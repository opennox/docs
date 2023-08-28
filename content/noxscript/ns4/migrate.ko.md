---
title: "Migrate from NS3"
weight: 2
---

NS4 provides the same functionality as NS3, but uses object-oriented approach.
It also supports a few unique features which are not available in NS3.

## Changes

### Objects

The `ns3.ObjectID` is replaced with [`ns4.Obj`](https://pkg.go.dev/github.com/noxworld-dev/noxscript/ns/v4#Obj) type.
The main difference is that `ns4.Obj` is opaque and can no longer be used or stored as an integer.

It is possible to convert `ns4.Obj` to/from `ns3.ObjectID` using the following code:

{{< tabs >}}
{{% tab title="NS3 to NS4" %}}
```go
ns4.AsObj(obj)
```
{{% /tab %}}
{{% tab title="NS4 to NS3" %}}
```go
ns3.ObjectID(obj.ObjScriptID())
```
{{% /tab %}}
{{< /tabs >}}

Similar functions are available for `ns4.ObjGroup` and `ns3.ObjectGroupID`:

{{< tabs >}}
{{% tab title="NS3 to NS4" %}}
```go
ns4.AsObjGroup(group)
```
{{% /tab %}}
{{% tab title="NS4 to NS3" %}}
```go
ns3.ObjectGroupID(group.ObjGroupScriptID())
```
{{% /tab %}}
{{< /tabs >}}

Most object-specific functions are now available on the object itself, instead of a top-level library function:

{{< tabs >}}
{{% tab title="NS4" %}}
```go
obj.Enable(false)
obj.Delete()
```
{{% /tab %}}
{{% tab title="NS3" %}}
```go
ns3.ObjectOff(obj)
ns3.Delete(obj)
```
{{% /tab %}}
{{< /tabs >}}

Object position is now available as a point type, instead of separate X and Y coordinates:

{{< tabs >}}
{{% tab title="NS4" %}}
```go
pos := obj.Pos()
x, y := pos.X, pos.Y
```
{{% /tab %}}
{{% tab title="NS3" %}}
```go
x, y := ns3.GetObjectX(obj), ns3.GetObjectY(obj)
```
{{% /tab %}}
{{< /tabs >}}

Most functions can now accept this new position type instead of a coordinate pair:

{{< tabs >}}
{{% tab title="NS4" %}}
```go
pos := obj.Pos()
obj2.HitMelee(pos)
```
{{% /tab %}}
{{% tab title="NS3" %}}
```go
x, y := ns3.GetObjectX(obj), ns3.GetObjectY(obj)
ns3.HitLocation(obj2, x, y)
```
{{% /tab %}}
{{< /tabs >}}

Position can also be constructed from X and Y values:

{{< tabs >}}
{{% tab title="NS4" %}}
```go
obj.HitMelee(ns4.Ptf(10, 20))
```
{{% /tab %}}
{{% tab title="NS3" %}}
```go
ns3.HitLocation(obj, 10, 20)
```
{{% /tab %}}
{{< /tabs >}}

### Waypoints

Similar to objects, waypoints are also represented with opaque `ns4.WaypointObj` type.

Conversion to/from `ns3.WaypointID` is still available:

{{< tabs >}}
{{% tab title="NS3 to NS4" %}}
```go
ns4.AsWaypoint(wp)
```
{{% /tab %}}
{{% tab title="NS4 to NS3" %}}
```go
ns3.WaypointID(wp.WaypointScriptID())
```
{{% /tab %}}
{{< /tabs >}}

Waypoints now also have methods instead of top-level library functions:

{{< tabs >}}
{{% tab title="NS4" %}}
```go
wp.Enable(false)
```
{{% /tab %}}
{{% tab title="NS3" %}}
```go
ns3.WaypointOff(wp)
```
{{% /tab %}}
{{< /tabs >}}

Position is also returned as a point data type:

{{< tabs >}}
{{% tab title="NS4" %}}
```go
pos := wp.Pos()
x, y := pos.X, pos.Y
```
{{% /tab %}}
{{% tab title="NS3" %}}
```go
x, y := ns3.GetWaypointX(obj), ns3.GetWaypointY(obj)
```
{{% /tab %}}
{{< /tabs >}}

This, in turn, allows using any type that has `Pos()` method (also known as `ns4.Positioner`) in places where position is expected:

{{< tabs >}}
{{% tab title="NS4" %}}
```go
ns4.CreateObject("Beholder", ns4.Ptf(10, 20))
ns4.CreateObject("Beholder", ns4.GetHost())
ns4.CreateObject("Beholder", ns4.Waypoint("Spot"))
```
{{% /tab %}}
{{% tab title="NS3" %}}
```go
ns3.CreateObject("Beholder", ns3.Waypoint("Spot"))
```
{{% /tab %}}
{{< /tabs >}}