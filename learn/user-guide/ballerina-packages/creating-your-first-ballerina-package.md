---
layout: ballerina-left-nav-pages-swanlake
title: Creating your first Ballerina Package
description: The below are basic steps you need to know about writing a Ballerina package. It also introduces the package-related commands in the `bal` command-line tool.
keywords: ballerina, programming language, ballerina packages, getting started
permalink: /learn/user-guide/ballerina-packages/creating-your-first-ballerina-package/
active: creating-your-first-ballerina-package
intro: The below are basic steps you need to know about writing a Ballerina packages. It also introduces the package-related commands in the `bal` command-line tool.
redirect_from:
- /learn/user-guide/ballerina-packages/creating-your-first-ballerina-package
---

## Creating a new package

The single source file program is a quick and easy way to get started with Ballerina. However, when your code grows, you need to create a Ballerina package to organize your code.

To create a new Ballerina package, we use the bal new command:

```bash
$ bal new hello_world
```

This will create a new Ballerina package with a main function. If we are creating a service instead of a main function, we pass the `-t service` option.
Let’s check what the `bal new` command generated:
```bash
$ cd hello_world
$ tree .
helloworld
  ├── Ballerina.toml
  └── main.bal
    
0 directories, 2 files
```

Let’s walk through each of these files:

**Ballerina.toml**

The [Ballerina.toml](/learn/user-guide/ballerina-packages/package-layout#ballerinatoml) file identifies a directory as a Ballerina package.

**.gitignore**

The `bal new` command also generates the .gitignore file by default with `target` added as an entry.

**main.bal**

This file generated by the `bal new` command will contain code for a hello world application as shown below.

```bal
import ballerina/io;  

public function main() { 
    io:println("Hello World!"); 
}

```

Let’s build the package and generate an executable jar file:

```bash
$ bal build
````

```bal
Compiling source
 	examples/helloworld:0.1.0 

Generating executable
    target/bin/helloworld.jar
```

Then, run it:

```bash
$ java -jar target/bin/helloworld.jar
Hello World!
```

We can also use `bal run` to compile and then run it in a single step:
```bash
$ bal run
Compiling source
    examples/helloworld:0.1.0

Running executable

Hello World!
```