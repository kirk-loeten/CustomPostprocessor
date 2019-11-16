# Adjustments of fanuc.cps

## change A axis to B axis

### line 13
description

### line 20
longDescription

### line 22
```
extension = "ngc"; //LinuxCNC
```
### line 23
fanuc neets numeric prognames, linuxCNC works with Names too

```
programNameIsInteger = false; //true;
```

### line 56
old: makeAAxisOtherWay: false, // make the A-axis rotate the opposite way
```
makeBAxisOtherWay: false, // make the B-axis rotate the opposite way ###
```

### line 83
old: makeAAxisOtherWay: {title:"Reverse A-axis", description:"Makes the A-axis rotate the opposite way.", type:"boolean"},
```
makeBAxisOtherWay: {title:"Reverse B-axis", description:"Makes the B-axis rotate the opposite way.", type:"boolean"},
```
### line 259 f
```
//var aAxis = createAxis({coordinate:0, table:true, axis:[(properties.makeAAxisOtherWay ? -1 : 1) * -1, 0, 0], cyclic:true, preference:1}); 
var bAxis = createAxis({coordinate:1, table:true, axis:[0, (properties.makeBAxisOtherWay ? -1 : 1) * -1, 0], cyclic:true, preference:1}); //1=b, axis:[a, b, c]
```
### line 289 to  322
uncommented

### line 323 to  326
```
//MyLinuxCNC
  if (programName) {
    writeComment(programName);
  }
```

### line 2507
```
if (arguments[i])  words.push("Z0");
```

### line 2508 to  2524
uncommented
