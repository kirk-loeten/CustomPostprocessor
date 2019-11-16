# Adjustments of linuxcnc.cps

Add:

| option | description | link |
|---------|------------|------|
| lengthOffset | limit to 99999 | http://linuxcnc.org/docs/html/gcode/tool-compensation.html#sec:tool-table |
| G64 P0.002 | Path Blending | http://www.linuxcnc.org/docs/2.6/html/gcode/gcode.html#sec:G64 |
| no G43 | exclude option |  |

## maximal toolnumber 99999
In the post processor is 99 the maximal tool number. The tool-table is allowed until 99999

### line 657, 782
change 99 to 99999
```
if (tool.number > 99999) {
if (lengthOffset > 99999) {
```

## noG43 after toolchange

### line 52
one comma at the end of line 51
```
noG43_after_TC: true // turn G43 Off
```

### line 60
copy line 59 -> paste in line 60, change name, title, description
```
noG43_after_TC: {title:"No G43 after TC", description:"After toolchange don't load the toolLengthOffset for tooltable", type:"boolean"},
```

### line 790
if block form line 790 to 815

```
if (!properties.noG43_after_TC) {
...
}
```
