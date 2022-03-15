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

### dot / prik

### cross / kryds

### intervalsolve

### grad

### vop

# Contribution

1. Download the package source code: [Mat1Tools.mw](Mat1Tools.mw)
2. Change/Add procedures
3. Create pull request
4. Wait for merge

You'll of cause be able to use your own modification right away by replacing the existing *Mat1Tools.mla* file in your Maple lib folder (See [Installation](#installation))
