# What are objects?
An object is a single 16x16 tile that holds its own special properties to add functionality to the game. The most common objects are simple, such as walls, ledges, or signs, but some objects can be more complex, such as doors, wraps, or stairs.

A lot of objects are pre-built within the Mapbuilder already, making your job as a developer even easier! However, you may want to be familiar with creating your own objects in case you need to.

## Building Objects
The easiest place to start building is to make your own custom object(s)! An object is a single 16x16 tile that holds its own special properties to add functionality to the game. 

The most common objects are simple, such as; walls, ledges, or signs. Some objects can be more complicated such as doors, warps or stairs. A lot of objects are pre-built within Mapbuilder already, making your job as a developer even easier. 

However, you may want to be familiar with creating your own objects in case you need to.

To build your own object, you need to place an object block on the specific tile you want to work with. Many object blocks in the Mapbuilder editor have pre-existing code, so make sure the pre-existing code suits your situation. For example, the red solid object block code `solid()`, makes the entire tile solid. If you do not want the tile to be solid, do not use this block and use a normal object block instead.

To access the block editor, right click on the object when placed on the mapbuilder tilemap viewer, to open up the jCoad editor. We can now begin typing whatever code we want.

---

## Code Types
All objects may contain jCoad to specify their behavior. However, there are three ways that code can be added to an object.

### **Root code** 
A root code is a global code that is shared across all instances of that object placed on any map. Root code is great for code that must be repeated across multiple ties, such as walls or shorelines. Instead of writing the code in every object you place, you can write it just once and place that object everywhere you need that functionality.

```json title="Root Code"  
solid()
```

### **Instance code** 
Instance code is exclusive code to the single tile the object resides on. This code is written on a single object instance on a single map. Instance code is best for creating a unique event, such as NPC dialogue, that never needs to be repeated.

Objects can have both root code and instance code. Think of a sign. All signs are solid, but most signs hold a unique message. Therefore, a sign object would probably have the following jCoad:

```json title="Instance Code"
msg(I am a unique sign. Only I hold this message!)
```

### **Comment code**
Comment codes won’t be read as code within the coded block. This is useful to comment on how the code below or above the statement will function.

```json title="Comment Code"
//This code demonstrates how a comment works.
```

**All** the jCoad in this guide can be used in both root code and instance code formats.
