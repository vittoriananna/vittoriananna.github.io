+++
date = '2026-08-18'
draft = false
title = "How to Change Corner Radius in PowerPoint"
tags = ["tricks","powerpoint"]
+++

Preparing a poster for an upcoming conference, I found myself wanting to standardize the roundness of the rounded-rectagle boxes across my slides. Dragging the little yellow dot that appears in PowerPoint surely isn't the most efficient way to get consistent results. I wanted every box to have *exactly* the same corner radius.
Surprinsingly, there is no way to do this in the native Powerpoint interface. 
A solution is to use VBA, the Visual Basic for Applications engine. 

## 1. Create a reference shape
Draw a shape and manually adjust the yellow handle until it looks as you want it. This shape becomes your reference and every other box will be matched to it. 

## 2. Open VBA 
To open the VBA window, click <kbd>Alt</kbd> + <kbd>F11</kbd>. Ensure that your shape is selected in the slide. 
In the VBA editor, open the Immediate window, if not already visible (**View -> Immediate Window**) and type: 
```vbnet
? Activewindow.Selection.ShapeRange(1).Adjustments(1)
```
Press <kbd>Enter<kbd> and VBA will display the value of the adjustment on the next line. 

## 3. Apply the setting to the next shape 
Next, select another shapes that you want to match to the first, go back to the Immediate Window and type:
```vbnet
Activewindow.Selection.ShapeRange(1).Adjustments(1)=[value from step 2]
```
Press Enter, and the shape snaps to the exact same roundness as your reference. Repeat for each shape.

I have a feeling VBA will become my new favorite way to productively procrastinate work. But then — slides *do* need to be perfect.