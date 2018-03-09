# Infrastructure
Our infrastrucure of code is simple, but not a common "go-to" solution. We do not stive to limit the number of reposorys and making large plugins. A new plugin shuld be created when there is a clear purpose. 

## Live enviroment
All sites are located in 'mnt/persist/www/'. The are named by a logical structure docroot_[sitename]. The beta & test enviroment are suffixed with _test and _beta. For example, our live version of helsingborg.se resides in 'mnt/persist/www/docroot_helsingborg' and the test equivalent resides in 'mnt/persist/www/docroot_helsingborg_test'. 

##Code

### The container
All websites should be packaged in its own repository. It should include relevant configurations, required plugin index (as a composer file) and other assets. This repository may include the full theme, if it's not being used in multiple containers (sites). 

### Plugin
A plugin should not be tied to the container. The ability to "live" on its own in any enviroment guarantees that the plugin can be reused in the future. All vendor packages should be included in the package (eaven if you use composer to aquire them in the first place). This requirement is due to the fact that it should be able to run, in enviroments where composer isen't implemented.

__This could also be implemented for themes__, if they live in their own repository. 

### Package
A package is like a plugin, it can contian vendor packages from other sources that should be handled in the same manner. Packages are smaller and dosen'r construct by default. Commonly used for Helper classes that is frequentlu used by many plugins, conatiners or themes. 

## Git
We host our code in a seperate enviroment and for simplicity we have activly cosen not to implement a traditional deploy procedure. The fact that we have pushed code to our "master" branch of the container repo or a plugin repo dosent mean that it has been taken in production. The following steps is required to take the code into production. 

- __For containers:__ A sepatate push to production using git should be done directoly to the target production server. All production machines do host a bare repository of it's own for all containers. Our vagrant enviroment automatically setup these origin remotes for you, named "production". Most of uor sites implements 3 separate branches. 
    + master - The production site
    + beta - A version of the site created for the single purpose of testing new code (only for developers).
    + test - A test version of the site that should contain __production ready__ code that editrs can use to test their hypothesis. 
    
- __For Plugins, themes and packages:__ Use a terminal tool to ssh into the production machine. 
    + CD to the relevant docroot directory. 
    + Run composer update [you may define a specific package]



