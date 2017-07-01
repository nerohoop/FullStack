#Content

## Basics

### Read command-line arguments
You can access command-line arguments via the global process object. The  
process object has an argv property which is an array containing the  
complete command-line. i.e. process.argv.  

The first element of the process.argv array  
is always 'node', and the second element is always the path to your  
program.js file, so you need to start at the 3rd element (index 2), adding  
each item to the total until you reach the end of the array.

### File System
To perform a filesystem operation you are going to need the fs module from  
the Node core library. To load this kind of module, or any other "global"  
module, use the following incantation:  

   var fs = require('fs')  

Now you have the full fs module available in a variable named fs.  

Buffer objects are Node's way of efficiently representing arbitrary arrays  
of data, whether it be ascii, binary or some other format. Buffer objects  
can be converted to strings by simply calling the toString() method on  
them. e.g. var str = buf.toString().

## Managing Modules
Node uses two core modules for managing module dependencies:
* The 'require' module, which appears to be available on the global scope
* The 'module' module, which also appears to be available on the global scope

When Node invokes that require() function with a local file path as the function’s only argument, Node goes through the following sequence of steps:
* **Resolving**: To find the absolute path of the file.
* **Loading**: To determine the type of the file content.
* **Wrapping**: To give the file its private scope. This is what makes both the require and module objects local to every file we require.
* **Evaluating**: This is what the VM eventually does with the loaded code.
* **Caching**: So that when we require this file again, we don’t go over all the steps another time.

[Modules](https://medium.freecodecamp.com/requiring-modules-in-node-js-everything-you-need-to-know-e7fbd119be8)

## npm

Every published package on npm has a `dist-tags` entry on it which  
maps strings like "latest" to version numbers like "1.2.48".  

By default, the "latest" version is what gets installed.  When you  
publish, the version that you publish gets tagged as "latest".  This  
is generally great, because most of the time you publish things when  
you're ready for users to use them.  

However, if you need to publish something, and *not* make it the  
default version of a package (for example, if it's a security release  
for a legacy version, or something), then you can manually manage  
these distribution tags with the `dist-tag` function.  

`npm dist-tag add <pkg>@<version> [<tag>]` will add a new tag.  
To find out the name of your current package/version type `npm ls`.  
The first line of the output will be the package and version; e.g. pkg@1.0.1.  
To add a tag type in the name of the tag.  

  npm dist-tag add pkg@1.0.1 beta  

Run `npm help dist-tag` to learn more about it.  

Let's add a dist-tag on your package,  
and then `how-to-npm verify` to check it.  
