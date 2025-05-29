# Understanding Definitions

This guide will focus on several definitions for using jCoad functions, properties and triggers.
Anything in parenthesis (represented by ``( ) ``) is a **parameter.** Parameters are separated by commas with no spaces between them.

Any parameter that is then enclosed in brackets (`[,example]`) is an **optional parameter**. These are not required and may not be needed when you are using the object code.

Any sets of brackets may be removed and your jCoad will still work properly, but you must be careful to remove the correct set of brackets and optional parameters.

Take the following jCoad as an example on how to identify which optional parameters can be taken out at once.

animation(image[,depth[,x,y,width,height[,frames[,speed[,loop]]]]])

This piece of jCoad can be used in any of the following ways depending on what you may or may not need to include.

```json title="Example with Optional Parameter Signifier" 
animation(image)
animation(image[,depth])
animation(image[,depth[,x,y,width,height]])
animation(image[,depth[,x,y,width,height[,frames]]]) 
animation(image[,depth[,x,y,width,height[,frames[,speed]]]]) 
animation(image[,depth[,x,y,width,height[,frames[,speed[,loop]]]]])
```

Now, we only need to remove the brackets to show what we would type into Mapbuilder.

```json title="Example"  
animation(image)
animation(image,depth)
animation(image,depth,x,y,width,height)
animation(image,depth,x,y,width,height,frames)
animation(image,depth,x,y,width,height,frames,speed)
animation(image,depth,x,y,width,height,frames,speed,loop)
```

The parameter names are only used for documentation. These names will be replaced with **arguments** that you swap in. Arguments may be a string of characters, a number, a boolean value, or some other format. All data types are documented alongside the parameter lists later in this guide.