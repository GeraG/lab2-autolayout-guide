# Creating AutoLayout Constraints for Lab 2 (a more detailed walkthrough) ##

If you got stuck during the AutoLayout portion of the lab, this guide will walk you through one way of adding constraints to complete this lab. Note that there are many different (and possibly better) ways to do this same job.

Remember, we need enough constraints so that the width, height, horizontal position, and vertical position of every UI element will be unambiguous at the runtime of our app (as mentioned in lecture, our goal is to create a set of linear equations (constraints) that will have a unique solution).

In this walkthrough, I'll first pin the bordering UI elements to the view, then create constraints between each of the buttons. At the end I'll create constraints for the label and segmented control. If you'd like to start from scratch with your constraints to follow this guide, click the `Resolve Auto Layout Issues` button at the bottom right of Interface Builder, then click `Clear Constraints` (see below). This will delete all of your existing constraints.

![alt text](/README-images/clear-constraints.png)

Also note that I've labeled the buttons in this tutorial with numbers to more easily refer to them, but you are not required to do the same.

## Part 1 - Pinning the top buttons to the top of the view ###

To make sure our top row buttons stay at the top of the screen, we'll add constraints for their vertical position.

First, add a **Vertical Position Constraint** between the top left button (Button 1) and the **Top Layout Guide**
![alt text](/README-images/autolayout1.png)

You can now edit this constraint in the Size Inspector. I set this constraint's constant value to 20 (this means that this button will remain 20 pixels below the top of the view), but feel free to use whatever value you see fit.
![alt text](/README-images/autolayout2.png)

We could do the same process for the other top row buttons, but to make potential future changes in margin size easier, **add a "Center Vertically" constraint from Button 2 to Button 1, and a "Center Vertically" constraint from Button 3 to Button 1** (Shown below).
![alt text](/README-images/autolayout3.png)

Now all of our top row buttons will remain at the top of the view!

## Part 2 - Pinning the first column of buttons to the left side of the screen ###

First, control-drag from button 1 to the left (leading) edge of the view. Then create a **Leading Space to Container Margin** Constraint. 

![alt text](/README-images/autolayout4.png)

Now, align the leading edges of Buttons 4 and 7 to Button 1 (Create two **Leading** constraints).

![alt text](/README-images/autolayout5.png)

## Part 3 - Pinning the Third Column of Buttons to the Right Edge of the Screen ###

Now create a **Trailing Space to Container Margin** constraint from Button 3 to the right (trailing) edge of the View. Make sure the constant value of this constraint is the same constant value for the **Leading Space** constraint made in Part 2 (we want our border sizes to be equal) by checking the constraints in the Size Inspector.

Then align the trailing edges of Buttons 6 and and 7 to Button 3 (create a **Trailing** constraint between Buttons 3 and 6 and another one Buttons 3 and 7.

## Part 4 - Adding Constraints Between Buttons ###

In order to ensure each button doesn't overlap with any others and that the spacing between each button is equal, we need to create constraints between each button and its adjacent neighbors. Wherever possible, we will align centers or edges of buttons, to avoid hardcoding in constant values.

Listed below is one way of creating constraints between the drum pad buttons in this app. 

1. Add a **Horizontal Spacing** constraint between Button 1 and Button 3. Click on Button 1 to view the constraint in the Size Inspector (it will show up as `Leading Space`) and set it's constant value to **Standard Value**.
2. Repeat Step 1 for Buttons 2 and 3
3. Add a **Vertical Spacing** constraint between Button 1 and Button 4. Click on Button 1 to view the constraint in the Size Inspector (it will show up as `Bottom Space`) and set it's constant value to **Standard Value**.
4. Add a **Center Vertically** constraint between Buttons 4 and 5 and Buttons 4 and 6 
5. Add a **Center Horizontally** constraint between Buttons 2 and 5 and Buttons 3 and 6 (we could add **Vertical Spacing** constraints instead, but this way we don't have to deal with setting constant values)
6. Add a **Vertical Spacing** constraint between Button 6 and Button 4 and set it's constant value to **Standard Value**.

Once you are at this point, the constraints for each button should look as follows:

![alt text](/README-images/autolayout6.png)

## Part 5 - Making all the buttons the same height ###

To make all of the buttons equal in height, we *could* control-drag from one button to every other button individually, adding an **Equal Width** constraint. To make our lives easier, instead we'll select all seven buttons, then open the "Add New Constraints" window found right above the debugger (see below), and create all of these constraints at the same time.

![alt text](/README-images/autolayout7.png)


Now each button's height will be the same as Button 1's height.

## Part 6 - Making the first 6 Buttons the same width ###

(Similar to Part 5) Now highlight the first 6 buttons (make sure not to include the last one!), then add an **Equal Height** Constraint between them using the "Add New Constraints" tool.

![alt text](/README-images/autolayout8.png)


If you want to make sure that you're on the right track at this point, add a temporary constraint from Button 7 to the bottom of the view (**Vertical Spacing to Bottom Layout Guide**). Run your simulator. The buttons should fill the screen and should resize and remain properly centered when the simulator is rotated. **With this added constraint, there should be no AutoLayout Issues**.

Here's what you should see in your simulator if you added this temporary constraint. 

![alt text](/README-images/autolayout9.png)

### Part 7 - Setting Constraints for the bottom UI Elements ###

First, delete the temporary constraint from part 6 if you haven't done so already.

Now we'll want to add the following constraints (again, there are many different ways to do this):

1. **Vertical Spacing to Bottom Layout Guide** constraint between the Label and the bottom of the View (pins the label to the bottom of the view)
2. **Leading Space to Container Margin** constraint between the Label and the left side of the View OR add a **Leading** constraint from the label to Button 1 (both pin the label to the left side of the view)
3. **Horizontal Spacing** constraint and a **Center Vertically** constraint between the Label and the Segmented Control
4. **Trailing Space to Container Margin** constraint between the Segmented Control and the right side of the View OR add a **Trailing** constraint from the label to Button 3 (both pin the segmented control to the right side of the view)

Now, to satisfy the requirement that the label and segmented control **should not** change in height or width, we need to create a constraints for their height and width.

To set the label's height constant, control drag from the label to itself, and set a reasonable value for the label's height constant in the Size Inspector. 

![alt text](/README-images/autolayout10.png)


Do the same process for the segmented control's width and height. 

Once your done with this part, your constraints should look similar to those pictured below.

![alt text](/README-images/autolayout11.png)


Now all we need to do is add a vertical spacing constraint from Button 7 to the bottom UI elements! One way to do this is by simply creating a `Vertical Spacing` constraint from Button 7 to the Label: 

![alt text](/README-images/autolayout12.png)


You may still have some warnings at this point, which we can resolve by "Updating Frames", which you can easily do by clicking this button:

![alt text](/README-images/autolayout13.png)


If you've followed this guide completely, you should have no AutoLayout warnings, and your app's UI should responsively update for any device size or orientation. Congrats!




