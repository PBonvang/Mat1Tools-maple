# Mat1Tools-maple
Mat1Tools is a [Maple](https://www.maplesoft.com/products/maple/) library consisting of procedures used throughout the [Advanced Engineering Mathematics 1 (01005) DTU course](https://01005.compute.dtu.dk/).

Big thanks to [Jonathan Højlev](https://www.youtube.com/channel/UCJWO_AzFZuqXoBY14JEdDXg) for providing the foundation for this package through Maple intro evenings and his [Template](assets/God%20skabelon.mw)

# Prerequisites
- [Integrator8](https://steen-toft.dk/mat/maple/int8.htm)

# Installation
1. Ensure you have the [Prerequisites](#prerequisites) installed
2. Download the package: [Mat1Tools.mla](Mat1Tools.mla)
3. Place the package in Maples lib folder
   1. The folder can be found by running the following command in Maple: `FileTools:-JoinPath(["lib"],base=mapledir);`
   2. This might require elevated privilege (Admin)
4. Restart Maple

# Use
To import the package into a document or worksheet simply write: `with(Mat1Tools)`  
and the [Procedures](#procedures) will be available to you.
## Procedures

**Index:**
 - [paraplot](#paraplot)
 - [dot / prik](#dot--prik)
 - [cross / kryds](#cross--kryds)
 - [intervalsolve](#intervalsolve)
 - [grad](#grad)
 - [vop](#vop)
 - [slhs](#slhs)
 - [srhs](#srhs)
 - [condgf](#condgf)
 - [vlen](#vlen)
 - [div](#div)
 - [jacobi](#jacobi)
 - [curl / rot](#curl)
 - [pint](#pint)
 - [flux](#flux)
 - [vsolve](#vsolve)
### paraplot
`paraplot(r, intervals, plotOpts)`  

**Description:** Plots parametric equations.

**Parameters:**
- `r: function / parametric equation`
- `intervals: list of ranges`
- `plotOpts: plot options`
  - 2D list: https://www.maplesoft.com/support/help/Maple/view.aspx?path=plot%2foptions
  - 3D list: https://www.maplesoft.com/support/help/Maple/view.aspx?path=plot3d%2foption

**Example:**
```
r:=(u,v) -> <u,exp(-u/3)*sin(u)*v>;
intervals := [0..2*Pi,0..1];
paraplot(r,intervals,color="#FF0004")
```

For more examples see the [showcase](Procedure%20showcases/paraplot.mw).

### dot / prik
`dot(x, y) / prik(x, y)`

**Parameters:**
- `x: Vector`
- `y: Vector`

**Example:**
```
x := <a,b,c>;
y := <d,e,f>;

dot(x,y)
> ad + be + cf
```

For more examples see the [showcase](Procedure%20showcases/dot.mw).

### cross / kryds
`cross(x, y) / kryds(x, y)`

**Parameters:**
- `x: 3D Vector`
- `y: 3D Vector`

**Example:**
```
x := <a,b,c>;
y := <d,e,f>;

cross(x,y);
> <b*f - c*e,
   -a*f + c*d,
   a*e - b*d>
```

For more examples see the [showcase](Procedure%20showcases/cross.mw).

### intervalsolve
`intervalsolve(equation, variable_range)`

**Description:** Solves for solutions to the provided equation in the provided variable range.

**Parameters:**
- `equation: Equation`
- `variable_range: Named range`

**Example:**
```
lign := sin(x)= 1;

intervalsolve(lign,x=0..4*Pi);
> [Pi/2, (5*Pi)/2]
```

For more examples see the [showcase](Procedure%20showcases/intervalsolve.mw).

### grad
`grad(f, vars)`

**Description:** Computes the gradient of a function regarding the list of variables passed.

**Parameters:**
- `f: Procedure`
- `vars: List of variable names`

**Example:**
```
f := (x,y) -> x^2 + y^2;

grad(f,[x,y]);
> <1,1>
```

For more examples see the [showcase](Procedure%20showcases/grad.mw).

### vop
`vop(v)`

**Description:** Vector operands (vop) extracts the elements of a vector.

**Parameter:**
- `v: Vector`

**Example:**
```
v := <a,b,c>;

vop(v);
> a,b,c
```

For more examples see the [showcase](Procedure%20showcases/vop.mw).

### slhs
`slhs(X, type)`

**Description:** Sequential left hand side (slhs) takes a list, vector, column matrix, or similar containing only equations and returns the left-hand side of the equations.

**Parameters:**
- `X: List, vector, column matrix, or similar`
- `type: The type of the returned element. Standard is the same type as X`

**Example:**
```
slhs(<x=0,y=10,z=15>)
> <x, y, z>
```
For more examples see the [showcase](Procedure%20showcases/slhs.mw).

### srhs
`srhs(X, type)`

**Description:** Sequential right hand side (srhs) takes a list, vector, column matrix, or similar containing only equations and returns the right-hand side of the equations.

**Parameters:**
- `X: List, vector, column matrix, or similar`
- `type: The type of the returned element. Standard is the same type as X`

**Example:**
```
srhs(<x=0,y=10,z=15>)
> <0, 10, 15>
```
For more examples see the [showcase](Procedure%20showcases/srhs.mw).

### condgf
`condgf(V)`

**Description:** Takes a vector field in 2 or 3 dimensions as a list, vector, or similar and checks if it lives up to the mandatory criteria for being a gradient field.

**Parameters:**
- `V: List, vector, or similar`

**Example:**
```
condgf(<x, y>)
> "Condition satisfied."
```

For more examples see the [showcase](Procedure%20showcases/condgf.mw).

### vlen
`vlen(v)`

**Description:** Vector length (vlen) computes the length of the passed vector.

**Parameters:**
- `v: Vector`

**Example:**
```
v := <x,y>:
vlen(v);
> sqrt(x^2 + y^2)
```

For more examples see the [showcase](Procedure%20showcases/vlen.mw).

### div
`div(V)`

**Description:** Creates a procedure/function for the divergence of the passed vector field.

**Parameter:**
- `V: Vector field procedure`

**Example:**
```
V := unapply(<z*x,y,y^2>,[x,y,z]):

div(V);
> (x,y,z) -> z + 1
```

For more examples see the [showcase](Procedure%20showcases/div.mw).

### jacobi
`jacobi(r)`

**Description:** Computes the jacobi function of a parametric equation variable of up to 3 variables.

**Parameter:**
- `r: parametric equation (Procedure/Function)`

**Example:**
```
r := unapply(<6*cos(u),6*sin(u),u>,u):
r(u);

jacobi(r);
> sqrt(37)
```

For more examples see the [showcase](Procedure%20showcases/jacobi.mw).

### curl
`curl(V) / rot(V)`

**Description:** Creates a rotation procedure/function for the given vector field.

**Parameter:**
- `V: Vector field (Procedure/Function)`

**Example:**
```
V := unapply(<z*x,y,y^2>,[x,y,z]):

curl(V);
> (x,y,z) -> <2*y, x, 0>
```

For more examples see the [showcase](Procedure%20showcases/curl.mw).

### pint
`pint(r,intervals,f=1)`

**Description:** Parametric equation integration (`pint`) integrates the parametric equation given in the given intervals, optionally with the provided weight function.

**Parameters:**
- `r: Parametric equation (Procedure/Function)`
- `intervals: List of ranges`
- `f: Weight function (Procedure/Function). Default = 1`

**Example:**
```
r := unapply(<u*cos(v),u*sin(v),u^2>,[u,v]):
r(u,v);
intervals := [0..2,0..Pi/2];

pint(r,intervals);
> (17*Pi*sqrt(17))/24 - Pi/24

# With weight function
f:=(x,y,z)->z^2;

pint(r,intervals,f);
> (7769*Pi*sqrt(17))/1680 - Pi/1680
```

For more examples see the [showcase](Procedure%20showcases/pint.mw).

### flux
`flux(V, r, intervals)`

**Description:** Computes the flux of the provided **3D** vector field throughout the provided 2 variable parametric equation in the given intervals.

**Parameters:**
- `V: Vector field (Procedure/Function)`
- `r: Parametric equation (Procedure/Function)`
- `intervals: List of ranges`

**Example:**
```
V := unapply(<z*x,y,y^2>,[x,y,z]):
V(x,y,z);

r := unapply(<u*cos(v),u*sin(v),u^2>,[u,v]):
r(u,v);
intervals := [0..2,0..Pi/2];

flux(V,r,intervals);
> -(19*Pi)/3
```

For more examples see the [showcase](Procedure%20showcases/flux.mw).

### vsolve
`vsolve(veq, vars)`

**Description:** Vector solve solves vector equations, where each side of the operand is a vector, for the specified variables

**Parameters:**
- `veq: Vector equation`
- `vars: A list/set of variable names`

**Example:**
```
veq := <a+b, a - b> = <4, 10>;

vsolve(veq,{a,b});
> {a = 7, b = -3}
```

For more examples see the [showcase](Procedure%20showcases/vsolve.mw).
# Contribution

1. Download the package source code: [Mat1Tools.mw](Mat1Tools.mw)
2. Change/Add procedures
3. Add a show case to [Procedure showcases](Procedure%20showcases)
4. Create pull request
   1. Provide a proper description of the addition or modification, so that testers don't have to test everything (Unit tests pending).

You'll of cause be able to use your own modification right away by replacing the existing *Mat1Tools.mla* file in your Maple lib folder (See [Installation](#installation))
