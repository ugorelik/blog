I want to start off by saying that I’ve never really looked at the actual design pattern before writing

this piece. I’ve used a couple of factories in my days (unknowingly) but I’ve never really bothered looking into how they actually work, what they’re for or when to actually use one. Again, I wrote this before knowing the “official” 
factory pattern. This is just what I came up with, and I’m sure it’s been done before so please don’t troll me.

<!--more-->

### The Problem

So I started making a game, I figured I’ll write this game in Java using some basic SWT stuff and then port it to OpenGL using LWJGL. Cool. My game has stuff in it and I like making nice polymorphic hierarchies. Naturally my first solution was to make an abstract class and then to sub class all of my desired items. Something like this:

`ReplaceableHorn < Item Brush < Item Food < Item`

Well that works pretty well and this is how we’ve done it both our games. I started writing an abstract class called item, got that finished pretty quickly, made some instanced variables and some methods. Bam, done. Then I went on to make my first item, the “replaceable horn.” It was then I realized that the only differences between an abstract Item class and something that was extending Item were different values for the variables. I literally just needed these objects to have different values but behave in the exact same way. I didn’t actually need polymorphism.

### The Solution: Make a Factory

As I’ve mentioned earlier, I’ve never actually used the factory pattern before but since first idea that popped into my head was, “Hmm I need some kinda item factory.” I figured I’d give it a shot.

### The Factory

I made a class called ItemFactory which would have static function and variables and the information about the all of the item variables.

### The Items

Next I made private nested class (within ItemFactory.java) called ItemTemplate (I’ll probably end up changing it to something more meaningful). Making a private class adds some security so that if someone else were to use my code they would never make their own item; they would have to go through the factory.

### The Interface

Using a private and nested class meant that I couldn’t really use this outside of ItemFactory.java. No big deal, we just need an interface. This is where Item.java comes in. Item is an interface that has all of the methods I need from ItemTemplate. Now ItemTemplate will implement Item and bam we have a pretty robust design from a software engineering perspective.

Here’s the verbose version of what it looks like:

```java
//ItemFactory.java
Public class ItemFactory {
    // Static stuff…
    // Variables
    public static Item createSpecificItem() {
        return createItem(ID_SPECIFIC_ITEM);
    }
    private static Item createItem(int id) {
        return new ItemTemplate(id, STAT1[id], STAT2[id], STAT3[id]);
    }
    // …
    private class ItemTemplate {
        // Variables
        Public ItemTemplate(int id, int stat1, int stat2, int stat3) {
        // …
    }
        Public void method1 { // … }
        Public void method2 { // … }
        // …
    }
}

// Item.java
Public interface Item {
    Public void method1();
    Public void method2();
    // ...
}
```
    
### Cleaning up the Factory

I decided to make arrays for the different items that I wanted. This makes accessing them a lot easier and cleaner. I also avoid an if-tree by simply using an “id.”