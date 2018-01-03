# Helsingborg Stad Coding Conventions

## Client side 
[CSS](client/css.md)

[HTML](client/html.md)

[JS](client/js.md)

## Server side

[PHP: Dictates how to write good backend implementations and how they should look like.](server/php.md)

## Ground principles

- The general mindset 
    + All functionality should be built in a manner that's flexible and general. The aim of each function should be to be re-usable in other components and implementations. 
- Replaceable
    + The platform is modular and benefits form staying that way. Code that you others write should be simple to replace or refactor. The main goal of this it not having to replace the would platform in the future. You may interpret this as a scheme of continuous updates.
- No hardcoding
    + Not a single line of code should be written that is specific to the target organization. All content and appearance should be flexible enough to be used by others. 
- Readable and simplistic before smart
    + Every bit of implementation must be readable. This requirement is more important than smart and innovative implementations.
 
