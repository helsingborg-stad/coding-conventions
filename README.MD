# Helsingborg Stad Coding Conventions

## Client side 
[CSS](client/css.md)

[HTML](client/html.md)

[JS](client/js.md)

## Server side

[PHP: Dictates how to write good backend implementations and how they should look like.](server/php.md)

[Infrastucture: Deployments & severs](server/infrastructure.md)

## Versioning
We are using semantic versioning for all of our plugins, themes and platform overall. Refer to semver 2.0 when unsure: https://semver.org/. 

## Ground principles

- __The general mindset__ 
    + All functionality should be built in a manner that's flexible and general. The aim of each function should be to be re-usable in other components and implementations. 
- __Replaceable__
    + The platform is modular and benefits form staying that way. Code that you others write should be simple to replace or refactor. The main goal of this it not having to replace the would platform in the future. You may interpret this as a scheme of continuous updates.
- __No hardcoding__
    + Not a single line of code should be written that is specific to the target organization. All content and appearance should be flexible enough to be used by others. 
- __Readable and simplistic before smart__
    + Every bit of implementation must be readable. This requirement is more important than smart and innovative implementations.
 
