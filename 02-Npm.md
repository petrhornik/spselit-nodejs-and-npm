# Introduction

This document is introduction to **NPM**.

## Contents

- NPM introduction
- NPM possible usages
- NPM practically
- Package
- Project

## NPM introduction

**NPM** is ecosystem consisting of three parts: website, command line interface (CLI), registry.

**NPM** is the standard package manager for **Node.js**.

### NPM website

The [website](https://www.npmjs.com/) provides search for packages. And supports setting up profile or organization under which you can share your own packages.

### Command line interface (CLI)

**CLI** runs in terminal and is used to manipulate packages, from downloading them and installing them to creating new ones and uploading them back. Or it can be used to run them.

### Registry

Last part of system is **registry** itself. Which is just **database** which contains information about every package and **storage** where packages are stored.

There is more then 2 million of packages listed right now.

Default registry is **npm public registry** at https://registry.npmjs.org. It is possible to host own (private) registry or mirror/cache public one for example via Azure or Artifactory.

## NPM possible usages

NPM has many usages just to name some:

- add packages to own project
- download standalone tools
- run packages
- manage project dependencies
- share packages with team/world

## NPM practically

Here will be practical steps to use NPM.

### Executing tool

One time execution of command in package can be done via:

    npx <package name> <command + parameters>

For example:

    npx ascii-themes generate 'Hello world!'

This command has three parts: `npx` which defines that we will be running command from package, `ascii-themes` [package](https://www.npmjs.com/package/ascii-themes) from which command will run, `generate 'Hello world!'` [command](https://www.npmjs.com/package/ascii-themes#usage) and its parameters - in this case command to generate text as ASCII art.

This commands (if no path to package is provided like in example above) will work by looking at local project if requested package is available if not it will check npm cache folder if package is not there either it will offer to download it to cache. When package is found it will be run.

**Warning**: Downloading packages this way to cache folder does not work in school!

Not all packages can be used in this way.

### Creating project

Packages are mostly used as part of project. Well project here is not correct as technically we will be creating incomplete package (which we will not upload to **NPM** registry).

In project packages can be either **dependency** or **dev dependency** - the difference is if it leaves dev environment or not. Which means licensing...

Project (package) is created via command:

    npm init

Which will run interactive session in which `package.json` will be created.

Then you can install packages which will be used in project. This is done via command:

    npm install <package name>

Optional parameter `--save-dev` or `-D` can be used which will define that installed package will be saved as **dev dependency**.

Now that package is installed it can be used inside of the project folder by using `npx` command from above.

### Using existing project

To use existing project we first need to have it. We can get it for example by cloning git repository - this is standard practice in companies. Normally project dependencies are not stored in git as they may have hundreds MBs.

Before we can use the project we need to get all dependencies for it. That is done by command:

    npm install

Running `npm install` without any parameters inside of the project folder will took dependencies from `package-lock.json` (if exists) or from `package.json`.

## Package

Package is unit which is handled by **NPM**.

Every package needs to contain `package.json` which provides information about package. Javascript file which is **entry point** to package default is `index.js` - file which is executed and does something. Of course there could be more files which this entry point one is referencing.

Also package **should** contain readme file, license file.

### package.json

Is JSON file which contains information about package. And is defined by https://docs.npmjs.com/cli/v10/configuring-npm/package-json.

Required information are **name**, **version**. **Version** in **NPM** is always provided via [Semantic Versioning](https://semver.org/). Rest is optional and has some default value defined. Though you probably want to have **license** and **author** set.

## Project

Here is described how project looks and works. This project can be "build", "packaged" and published to **NPM** as a **package**. But in school setting we won't be creating packages which can be used by someone else but only a relatively simple website.

### Structure

Project of course same as package contains `package.json`, **readme**, **license**.

And `package-lock.json` here is description of which exact version and from where are installed in this project. This file includes all packages which are resolved - this means whole chains as dependencies which we are targeting may have it's own dependencies.

Another is `node_modules` folder where are resolved packages installed.

Additional file can be `.npmrc` which holds npm configuration.

And then of course files of project itself.

### package.json

This file has same job as in package and that is holding information about project/package.

In addition to it there is a section `scripts` which holds scripts which can be executed. That is done by running command:

    npm run <script name>

Scripts which can be run from here are either installed packages, npm commands, scripts files inside node or other command lines or even other applications.

Before running given script their **pre** script will run and after it's **post** script will run. Pre script is named `pre<script name>` and post script is named `post<script name>`. So if we have script with name `build` then NPM will run `prebuild` (if exists) then `build` then `postbuild` (if exists).
