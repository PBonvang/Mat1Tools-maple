# Mat1Tools-maple
Mat1Tools is a [Maple](https://www.maplesoft.com/products/maple/) library consisting of procedures used throughout the [Advanced Engineering Mathematics (01005) DTU course](https://01005.compute.dtu.dk/).

Big thanks to [Jonathan Højlev](https://www.youtube.com/channel/UCJWO_AzFZuqXoBY14JEdDXg) for providing the foundation for this package through LaTex intro evenings and his [Template](assets/God%20skabelon.mw)

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
### paraplot
`paraplot(r, intervals, plotOpts)`  

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

### cross / kryds

### intervalsolve

### grad

### vop

### slhs
`slhs(X, type)`

**Parameters:**
- `X: List, vector, column matrix or similar`
- `type: The type of the returned element. Standard is the same type as X`

**Example:**
```
slhs(<x=0,y=10,z=15>)
```
For more examples see the [showcase](Procedure%20showcases/slhs.mw).

### srhs
`srhs(X, type)`

**Parameters:**
- `X: List, vector, column matrix or similar`
- `type: The type of the returned element. Standard is the same type as X`

**Example:**
```
srhs(<x=0,y=10,z=15>)
```
For more examples see the [showcase](Procedure%20showcases/srhs.mw).

### checkGradient

# Contribution

1. Download the package source code: [Mat1Tools.mw](Mat1Tools.mw)
2. Change/Add procedures
3. Add a show case to [Procedure showcases](Procedure%20showcases)
4. Create pull request
   1. Provide a proper description of the addition or modification, so that testers don't have to test everything (Wish Maple had unit tests).

You'll of cause be able to use your own modification right away by replacing the existing *Mat1Tools.mla* file in your Maple lib folder (See [Installation](#installation))
