---
title: "Quickstart"
weight: 1
---

This guide will show how to create your first map script using OpenNox map script API in Go language.

## First steps

{{% notice note %}}
Make sure you have **OpenNox** installed. Vanilla Nox, Reloaded or other version won't work!
{{% /notice %}}

To create your first map script, copy one of the existing map folders, or create your own in the editor.
If you copied the map, make sure to rename files inside the folder accordingly.

Then, make the following files in you map folder:

`script.go` (any name like `*.go` will work):
```go
package <mapname>
	
func init() {
	println("hello!")
}
```

`go.mod`:
```
module <mapname>

go 1.22
```

For example, original map:
```
maps/
  estate/
    estate.map
    estate.nxz
```

Copied, and with new files:
```
maps/
  example/
    example.map
    example.nxz
    script.go
    go.mod
```

In `script.go`:
```go
package example

func init() {
	println("hello!")
}
```

In `go.mod`:
```
module example

go 1.22
```

Done! Now start the map in OpenNox, open game console, and you should see `hello!` message there.

{{% notice info %}}
You don't need Go or any other compiler to write map scripts for OpenNox.

Having said that, proper Go language setup will enable IDE support, type checking, autocompletion, etc.
Thus, it's highly advised.
{{% /notice %}}


## Full setup

For proper setup you will need:

1. [Go 1.20+](https://go.dev/dl/) (for type checking, dependencies)
2. [Git](https://git-scm.com/) (for [Windows](https://gitforwindows.org))
3. [GoPls](https://github.com/golang/tools/blob/master/gopls/README.md) (for integration with VSCode)
4. [VSCode](https://code.visualstudio.com/) (IDE itself)
5. [Go extension](https://code.visualstudio.com/docs/languages/go) for VSCode (includes docs about `gopls`)

Once done, we can make a new project:

1. Copy existing map or create a new one in the map editor.
2. Open map folder in VSCode.
3. Open terminal (`Terminal -> New Terminal` in top menu in VSCode).
4. `go mod init <mapname>` (e.g. `go mod init example`). This will create `go.mod`.
5. Create a new Go file, e.g. `script.go` with `package <mapname>` (e.g. `package example`).
6. Add some code to it, e.g. `func init() { println("hello!") }`.
7. Save everything, start OpenNox and test the map.

## Script runtimes

There are multiple versions of the script runtimes available (full list [here]({{% relref "noxscript" %}})), for example:

- [NoxScript 3 (aka NS3)]({{% relref "noxscript/ns3" %}}) - compatible with original [NoxScript 3](https://noxtools.github.io/noxscript/)
- [EUD v171]({{% relref "noxscript/eud" %}}) - compatible with Panic's [EUD project](https://gitlab.com/happysoft3/eud-maps-project/-/tree/master/eud_project/libs)
- [NoxScript 4 (aka NS4)]({{% relref "noxscript/ns4" %}}) - our new script runtime (**recommended**)

The way these runtime works is that usually one of them is the main runtime (**NS4** in this case),
which provides all functionality available in OpenNox. Other runtimes are only a compatibility layer on top of it.
But an important one! They provide an already familiar interface for map developers (e.g. NS3 or EUD).

Because of this, it is safe to mix and match the runtimes. If you are experienced in NS3 - start from it.
If you are new to Nox scripting - pick the latest NS runtime (NS4).

Links above will link to Go language documentation for each runtime - this is the main source of documentation
for the functions and classes available in each runtime. This guide will only provide basic knowledge about the setup.

## Using runtimes

Now, how to enable these runtimes?

In case you skipped the full setup, it's only a matter of adding an `import` in a Go file and using it:

```go
package example

import (
    "fmt"
    
    "github.com/noxworld-dev/noxscript/ns/v4"
)

func OnFrame() {
	fmt.Println("players:", len(ns.Players()))
}
```

Couple a things to note here:
- We imported standard Go package `fmt` used for printing to console. You can freely use other Go standard packages as well.
- We imported NS as `github.com/.../ns/v4`, but we reference it as `ns.*` (e.g. in `ns.Players`). The `v4` suffix is a *package version*.
- `OnFrame` function will be called by OpenNox each game frame (aka "server tick"). So we should see a lot of messages in console!

That's all what's needed to use one of the runtimes. But what if we want to use both NS3 and NS4, for example?

Importing both packages directly won't work - they have the same name. So we assign an *alias* to each version:

```go
package example

import (
    "fmt"
    
    ns3 "github.com/noxworld-dev/noxscript/ns/v3"
    ns4 "github.com/noxworld-dev/noxscript/ns/v4"
)

func OnFrame() {
	fmt.Println("players:", len(ns4.Players()))
	fmt.Println("talking:", ns3.IsTalking())
}
```

If you got used to NoxScript 3, and you don't want to write `ns.` or `ns3.` everywhere, you can also specify dot as an alias:

```go
package example

import (
    "fmt"
    
    . "github.com/noxworld-dev/noxscript/ns/v3"
    ns4 "github.com/noxworld-dev/noxscript/ns/v4"
)

func OnFrame() {
	fmt.Println("players:", len(ns4.Players()))
	fmt.Println("talking:", IsTalking())
}
```

Notice how we are calling `IsTalking` without the `ns3` prefix.
This is, however, not typical to Go, since it's not clear if `IsTalking` is defined in your code or in the other package.

Now, going back to the full IDE setup, you may have noticed that it doesn't recognize the imports.
This is because we need to update project dependencies in `go.mod`. We can do it with either of two ways:

- `go mod tidy` from the terminal (requires Git).
- Or hover over the unrecognized import name, select `Quick fix...`, and `go get ...` there.

In both cases it should download the dependency (which is the NS runtime you selected) and will add it to `go.mod`.

Now you should see autocomplete working properly on these runtime packages.

## Updating runtimes

Script runtimes are updated periodically in OpenNox to expose new functionality or fix bugs.

This is done automatically, new OpenNox releases will enable new runtimes without any actions needed from the map developer.

However, the IDE will not see new functions in the new runtime version, unless it is updated in the map project.

The easiest way to update is to open `go.mod` file in the map folder and find the line with the runtime you want to update:
```
require (
    github.com/noxworld-dev/noxscript/ns/v4 v4.3.0
    // ... other lines
)
```

Just update the version there, and run `go mod tidy`.
The full list of version is available by clicking on the version in the [script package documentation](https://pkg.go.dev/github.com/noxworld-dev/noxscript/ns/v4?tab=versions)
and on the [GitHub](https://github.com/noxworld-dev/noxscript/tags).

## Packages

Now we know how to import runtimes and run scripts. How should we structure the code, though?

In Go, a unit of distribution is a "package": a directory with one or more Go files.
Names of Go files do not matter, the only requirement is that all files in a directory must have the same
`package` directive at the top. OpenNox enforces additional limitation: `package` should match the map name.

Apart from that, the code organization is up to you. All functions and variables defined in one file will be
available for all other files in the same directory.

## Ho do I ...

This guide barely scratches the surface, and only show a few first steps.

If you are already familiar with original NoxScript 3, check the [NS3 migration guide]({{% relref "noxscript/ns3/migrate" %}}).

You may probably want to get a bit more familiar with Go. The language is very simple, so it should be straightforward.
An interactive [Go tour](https://go.dev/tour/) is a great place to start.

Some of your questions may be answered already in [Q&A](./questions-and-answers.md).
There are [examples]({{% relref "noxscript/examples" %}}) available as well.

If your question is not covered, please send a question [here](https://github.com/noxworld-dev/noxscript/discussions/new?category=q-a)
or in our [Discord](https://discord.gg/HgDUeXhAyW).
