# Flexbox


### Concepts ###

The flexible box layout module, usually referred to as flexbox, was designed as a one-dimensional layout model, 

and as a method that could offer space distribution between items in an interface and powerful alignment capabilities. 

When working with flexbox you need to think in terms of two axes — the **main axis** and the **cross axis.** 

The main axis is defined by the **flex-direction** property, and the cross axis runs perpendicular to it. 

Everything we do with flexbox refers back to these axes, so it is worth understanding how they work from the outset.

 - Elements sizing and ordering

 - Horizontal and vertical alignment

 - Empty space between elements

 - Positioning 


#### Container Properties ####

 - **flex-direction:**  row | row-reverse | column | column-reverse

 - **flex-wrap:** nowrap | warp | wrap-reverse
                  Whether flex items are forced onto one line(default) or can wrap onto multiple lines
			      Note: Top-bottom margins **do NOT collapsed** in flexbox.

 - **flex-flow:** This property is a shorthand for the following CSS properties: flex-direction and flex-wrap

 - **gap:**       0 | px | % | em | calc() 
                  Precise: column-gap | row-gap
                  Sets the gaps (gutters) between rows and columns 

 - **justify-content:**  flex-start | center | flex-end | space-between | space-around | space-evenly. 
                         Align items along the **main-axis.**

 - **align-items:**  stretch | center | start |  end. Align items along the **cross-axis.** 

 - **align-content:**  start | center | space-between | space-around 


#### Item Properties ####

 - align-self

 - flex-grow

 - flex-shrink

 - flex-basis

 - flex

 - order