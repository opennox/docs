---
title: "Migrate from original"
weight: 2
---

This guide will help migrate existing [NoxScript 3](https://noxtools.github.io/noxscript/)
maps to [NS3](https://pkg.go.dev/github.com/noxworld-dev/noxscript/ns/v3) in OpenNox.

In this guide we will refer to "NoxScript 3" as the original Nox script, while "NS3" as the new Go-based scripts for OpenNox.

## Why?

First logical question: *why bother*? OpenNox runs original NoxScript 3 just fine.

A few reasons to migrate to OpenNox scripts:
- NoxScript 3 is limited to what original Nox engine exposes. Which isn't a lot. There won't be *any* updates.
- NS3 in OpenNox is a **drop-in replacement**. Same functions are supported.
- We provide tooling to **migrate** 90% of your code **automatically**. Only minor tweaks are needed.
- NS4 (and beyond) will have more and **more features** going forward, including modding support.
- You *won't* need a separate script compiler. Scripts are run **directly from source**.
- More comprehensive **type system**: proper arrays, dictionaries (`map`), structures, classes.
- **Libraries** included: string manipulation, full UTF8 support, math, sorting, etc.
- Better **performance**: all libraries are compiled into OpenNox and run natively.
- Better **debugging**: if script crashes, there's a stack trace. Scripts can recover from it as well!
- Go language used in scripts is used in OpenNox itself. Maybe one day you'll decide to **contribute**?

It wouldn't be fair to not list *downsides*:
- It only works with OpenNox.
- You'll need to learn a new scripting language.
- Script may need to do more work when saving/loading.

If you heard about EUD script compiler by Panic and maybe considered it, see [this guide]({{% relref "noxscript/eud/migrate" %}}).

In general, we believe that OpenNox is the future of Nox modding, thus porting your map may give it an entirely new life!

## How?

There are two path currently: converting the compiled script from the map or converting the source.

### Converting the map script

You'll need a recent `noxtools` installed (assuming you have [Go 1.20+](https://go.dev/dl/) installed):

```
go install github.com/noxworld-dev/opennox-lib/cmd/noxtools@latest
```

From the map directory:
```
noxscript ns decomp <mapname>.map
```

It will print a decompiled source code converted to Go and NS3 runtime.

Because of the limitation of Nox script assembly:
- All variable names will be lost.
- Some control flow may be replaced with `goto`.

But after fixing these issues, you should be ready to go!

### Converting the source

**TODO:** Add a guide for using `cxgo` to automate it.

Currently, you'll have to manually convert the source.
Until we automate it as well, please consider converting the extracted map script, as shown above.

NoxScript 3 is similar to C, which has a lot in common with Go.
However, Go syntax is slightly different in regard to types.

Conversion steps will include:
- Swapping argument and variable names with types: `int a` -> `a int`.
- Adding either `var` or `const` to variable definitions: `int a` -> `var a int`.
- Moving function return type to the end: `int foo()` -> `func foo() int`.
- Moving `{` to the previous line. E.g. `func foo()\n{` -> `func foo() {`. Same for `if`, `else`, `for`.
- Adding `{ ... }` to `if` and `else` which do not have them: `if (1) foo()` -> `if (1) { foo() }`.
- Removing `void` from returns.
- Fixing variable types (Go doesn't allow implicit type conversion).

After this, add the following header to your file:

```go
package example

import (    
    . "github.com/noxworld-dev/noxscript/ns/v3"
)
```

Dot import should automatically resolve all references to NS3 functions.

## After conversion

### Limitations

There are some temporary limitations you should be aware of:
- Timers will stop each time the map is reloaded. You'll need to restart them from the script.
- All callbacks will reset when map is reloaded. You'll need to set them again from the script.

These issues will be resolved eventually.

### New: Syntax

We highly recommend checking our [Go tour](https://go.dev/tour/) to get familiar with the syntax, but we'll give a short recap here.

#### File structure

All files must start with `package <mapname>`:

```go
package example
```

It can be followed by one or more package imports:

```go
import "fmt"
import "strconv"
// it is typical to group them:
import (
	"fmt"
	"strconv"
)
```

Then global variables and/or functions follow. Order of declarations doesn't matter.

#### Variables and types

Most notable syntax distinction: in Go, the type name is on the right side, instead of on the left as in NoxScript 3:

{{< tabs >}}
{{% tab title="NS3 (Go)" %}}
```go
var x int
```
{{% /tab %}}
{{% tab title="NoxScript 3 (C)" %}}
```c
int x;
```
{{% /tab %}}
{{< /tabs >}}

Note that `;` is no longer needed, and variable declaration must start with `var` (or `const`).

There's a very good reason why types are on the right: it makes reading complex types more natural.
Just read them left to right!

For example, array: `var x [3][2]int` simply reads left to right as "array of 3 elements, each containing 2 `int` values".
Much better than a random order of `int x[2][3];`.

Same for pointers: `*[2]int` reads "pointer to an array of 2 `int`s". Compare it to `int* x[2];`.

#### Functions

Function declarations are also different:
- They *must* start with `func`.
- Types for arguments are on the *right*.
- Return type is *after* the arguments.
- Void return type *must* be omitted.
- The opening `{` *must* be on the same line as the function header.
- Arguments with the same types can be grouped.
- Multiple returns are supported.

{{< tabs >}}
{{% tab title="NS3 (Go)" %}}
```go
func foo(a int) {
}

func bar(x, y int, s string) int {
}
```
{{% /tab %}}
{{% tab title="NoxScript 3 (C)" %}}
```c
void foo(int a)
{
}

int bar(int x, int y, string s)
{
}
```
{{% /tab %}}
{{< /tabs >}}

#### Control flow

All control flow structures *require* the opening `{` to be on the same line, for example:

{{< tabs >}}
{{% tab title="NS3 (Go)" %}}
```go
if (x) { foo() }

if (y) {
    bar()
}
```
{{% /tab %}}
{{% tab title="NoxScript 3 (C)" %}}
```c
if (x) foo();

if (y)
{
    bar();
}
```
{{% /tab %}}
{{< /tabs >}}

The `()` in the condition is also optional:

{{< tabs >}}
{{% tab title="NS3 (Go)" %}}
```go
if x { foo() }

if y {
    bar()
}
```
{{% /tab %}}
{{% tab title="NoxScript 3 (C)" %}}
```c
if (x) foo();

if (y)
{
    bar();
}
```
{{% /tab %}}
{{< /tabs >}}

Same rules for `{` apply for `else`:

{{< tabs >}}
{{% tab title="NS3 (Go)" %}}
```go
if x {
    foo()
} else {
    bar()
}
```
{{% /tab %}}
{{% tab title="NoxScript 3 (C)" %}}
```c
if (x) foo()
else bar()
```
{{% /tab %}}
{{< /tabs >}}

#### Loops

Loops *must* not include `(` and have same rules in regard to `{`:

{{< tabs >}}
{{% tab title="NS3 (Go)" %}}
```go
var i int
for i = 0; i < 10; i++ {
}
```
{{% /tab %}}
{{% tab title="NoxScript 3 (C)" %}}
```c
int i;
for (i = 0; i < 10; i++)
{
}
```
{{% /tab %}}
{{< /tabs >}}

Loop that use `while` *must* use `for` keyword:

{{< tabs >}}
{{% tab title="NS3 (Go)" %}}
```go
for x {
}
```
{{% /tab %}}
{{% tab title="NoxScript 3 (C)" %}}
```c
while (x)
{
}
```
{{% /tab %}}
{{< /tabs >}}

### New: Core types

In original NoxScript 3, there were only a few types available: `int`, `float`, `string`, `object`.

In NS3 the list is much longer: `bool`, `int`, `uint`, `float32` (analog of `float`), `string`, `any`, etc.
The `object` type is replaced with more specific types from NS3 package:
[`ObjectID`](https://pkg.go.dev/github.com/noxworld-dev/noxscript/ns/v3#ObjectID),
[`ObjectGroupID`](https://pkg.go.dev/github.com/noxworld-dev/noxscript/ns/v3#ObjectGroupID),
[`WaypointID`](https://pkg.go.dev/github.com/noxworld-dev/noxscript/ns/v3#WaypointID), etc.

An important distinction is that Go doesn't allow implicit type conversion.
For example, in NoxScript it was okay to have an `int` variable and put an `object` there.
In NS3, this is requires an explicit type conversion: `int(x)`. But, of course, it's better to have correct types for your variables.

Another distinction of NS3 is the support of direct conversions between `int` and `float`.
It is done the same way: `int(x)` or `float32(x)`.

Converting between `int` and `string` is supported via [`IntToString`](https://pkg.go.dev/github.com/noxworld-dev/noxscript/ns/v3#IntToString),
but it's better to use Go's standard library instead: [`strconv.Itoa`](https://pkg.go.dev/strconv#Itoa).

It also supports conversion from `string` to `int` via Go's standard library: [`strconv.Atoi`](https://pkg.go.dev/strconv#Atoi).
Note, that this function may return an error, which you are free to ignore (with `_`):
```go
x, _ := strconv.Atoi("1")
```

### New: Strings

NoxScript 3 had a limitation that a frequent `+` operation on strings overflows a string table.

There's no such limitation in NS3: any number of strings can be created.

Printing to strings is also supported with Go's [`fmt.Sprintf`](https://pkg.go.dev/fmt#Sprintf):

```go
s := fmt.Sprintf("Hello player %d!", n)
```

There are quite a few more string functions available in [`strings`](https://pkg.go.dev/strings),
[`https://pkg.go.dev/strconv`](https://pkg.go.dev/strconv) and [`unicode`](https://pkg.go.dev/unicode) packages.

Even though strings can be created with `+` and individual bytes can be accessed with `s[i]`,
strings are *immutable* in Go! This means, once created, they cannot be edited, only new ones can be created.
If you need to change a few characters, consider converting to byte array, making changes, and converting back:

```go
s := "Gello"
b := []byte(s) // type: []byte
b[0] = 'H'
s = string(b) // "Hello"
```

### New: Variable type inference

NoxScript 3 requires a type for new variables to be set explicitly. NS3 allows automatic inference of variable type:

{{< tabs >}}
{{% tab title="NS3 (Go)" %}}
```go
a := 10 // int
b := false // bool
x := ns.Object("Bob") // ObjectID
```
{{% /tab %}}
{{% tab title="NoxScript 3 (C)" %}}
```c
int a = 10; // int
int b = 0; // bool 
int x = Object("Bob"); // object
```
{{% /tab %}}
{{< /tabs >}}

The `:=` operator does two things: defines a new variable (similar to `var`) and infers a type for it.

But note that using float values produces a `float64` type, not `float32`:

```go
x := 0.0 // float64!
y := float32(0.0) // float32
x = y // error!
```

However:

```go
const x = 0.0 // untyped float
var y float32 = x // no error
```

Constants are "untyped" and infer the type automatically from a variable they assigned to.

### New: Range loop

In NS3 a new type of loop is available: `for range`, which allows to loop over all values in an array.

{{< tabs >}}
{{% tab title="NS3 (Go)" %}}
```go
var arr [3]int
// writing: loop over indexes only
for i := range arr {
    arr[i] = i+1;
}
cnt := 0
// reading: loop over values
for _, v := range arr {
    cnt += v
}
```
{{% /tab %}}
{{% tab title="NoxScript 3 (C)" %}}
```c
int i;
int arr[3];
int cnt = 0;
for (i = 0; i < 3; i++) // writing
{
    arr[i] = i+1;
}
for (i = 0; i < 3; i++) // reading
{
    cnt += arr[i];
}
```
{{% /tab %}}
{{< /tabs >}}

### New: Dynamic arrays (slices)

In NoxScript 3, only fixed arrays are supported. NS3 has support for Go slices, which are arrays with dynamic length:

{{< tabs >}}
{{% tab title="NS3 (Go)" %}}
```go
var arr []int
for i := 0; i < 3; i++ {
    arr = append(arr, i+1) // adds elements to the end
}
// len(arr) == 3
```
{{% /tab %}}
{{% tab title="NoxScript 3 (C)" %}}
```c
int i;
int arr[3];
for (i = 0; i < 3; i++)
{
    arr[i] = i+1;
}
```
{{% /tab %}}
{{< /tabs >}}

### New: Structures

NS3 completely supports custom struct types. They are very similar to classes in other programming languages.

Let's say we want to build an RPG map, and we want to record a new character class for all player units:

```go
type MyUnit struct {
	ID ns.ObjectID // types on the right: field "ID" with type "ns.ObjectID"
	Class string
}

func init() {
    unit := ns.Object("Bob")
    // creates a new struct instance, takes pointer to it
    myUnit := &MyUnit{ID: unit, Class:"archer"}
    changeClass(myUnit, "shaman")
}

// changeClass accepts a pointer to struct be able to change fields.
// Removing the pointer will make a copy of the struct for this function!
func changeClass(unit *MyUnit, cl string) {
    unit.Class = cl
}
```

The `changeClass` function can also be rewritten as a method on `MyUnit` struct:

```go
type MyUnit struct {
	ID ns.ObjectID // types on the right: field "ID" with type "ns.ObjectID"
	Class string
}

// changeClass is a method on MyUnit struct pointer.
// Removing the pointer will make a copy of the struct for this function!
func (u *MyUnit) changeClass(cl string) {
    u.Class = cl
}

func init() {
    unit := ns.Object("Bob")
    myUnit := &MyUnit{ID: unit, Class:"archer"}
	// now changeClass is available as a method on the struct instance
    myUnit.changeClass("shaman")
}
```

For developer coming from C, new structs always have their fields initialized to zero vales.

### New: Dictionaries (maps)

NS3 support dictionaries/sets, which are unordered collections of values indexed by a key of any type.

For example, we made a `MyUnit` struct in the previous example. But how to quickly find `MyUnit` for `ns.ObjectID`?

```go
type MyUnit struct {
	ID ns.ObjectID // types on the right: field "ID" with type "ns.ObjectID"
	Class string
}

// mapUnits maps ns.ObjectID to *MyUnit.
// All maps must be created with make before use!
var mapUnits = make(map[ns.ObjectID]*MyUnit)

func init() {
	createMyUnits()
	findAndChangeClass()
}

func createMyUnits() {
    unit := ns.Object("Bob")
    myUnit := &MyUnit{ID: unit, Class:"archer"}
    // add new record to the map, index by ID
    mapUnits[unit] = myUnit
}

func findAndChangeClass() {
    unit := ns.Object("Bob")
	// find by ID
	myUnit := mapUnits[unit]
	if unit == nil {
	    return // not found	
    }
	myUnit.Class = "shaman"
}
```

Keys can also be deleted from the map:

```go
delete(mapUnits, unit) // delete by unit ID
```