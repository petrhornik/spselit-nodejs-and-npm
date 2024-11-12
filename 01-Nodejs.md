# Introduction

This document is introduction to **Node.js**.

## Contents

- Node.js introduction
- Installation
- Usage

## Node.js introduction

[**Node.js**](https://nodejs.org/en) is an open-source and cross-platform **JavaScript** runtime environment.

**Node.js** runs the **V8 JavaScript engine**, that is the same engine which powers **Chromium** based browsers. For example: Google Chrome, Microsoft Edge, Brave.

**Node.js** apps runs in single process without creating a new thread for every request (this is related to acting as server). Of course **Node.js** provides standard asynchronous operations like I/O or network communication and instead of blocking thread it will resume when response comes back.

**Node.js** implements **ECMAScript (ECMA-262)** standard and allows controlling which experimental features are available.
                            - definuje jak by měl script vypadat

## Installation

Installation of **Node.js** is possible via many methods and on all systems as it is really popular ecosystem. Possible options for you system can be found on [website](https://nodejs.org/en/download).

Easiest installation for Windows is by using pre-build binaries. Which is same way how it was installed on school computers.

### Multi version installation

When working on different projects it is sometimes required to use different version of **Node.js** for each. But unfortunately **Node.js** does not support multi version installation by itself.

Fortunately there are projects like [**nvm-windows**](https://github.com/coreybutler/nvm-windows) which adds this support to Windows. If you feel that you may need to have different versions I recommend to getting this tool now (as **Node.js** has to be installed through this tool).

## Usage

**Node.js** can be used from terminal/command line by passing Javascript file to it.

For example if we have file with name `server.js` then we will use command to run it:

    node server.js

Though normally this direct invocation is not used. As **Node.js** is mostly used via **NPM** or other package managers.
