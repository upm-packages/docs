---
layout: default
title: Publish packages
nav_order: 2
parent: English
permalink: /en/publish
---

# Publish packages

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Prepare

### Unregistered

User registration is performed from the command line.

```bash
npm adduser --registry https://upm-packages.dev
```

Authentication information is recorded in `~/.npmrc`.

### Registered

If you have already registered, log in from the command line.

```bash
npm login --registry https://upm-packages.dev
```

Authentication information is recorded in `~/.npmrc`.

## Publish packages

### 1. Develop the package as a regular Unity project

In principle, development with Unity 2019.1.0f2 or later is recommended.

There is no problem if the package you develop depends on other packages managed by Unofficial Unity Package Manager Registry.

### 2. Put `.npmrc`

Put `.npmrc` with the following contents in the root directory of the project.

```rc
registry=https://upm-packages.dev
```

### 3. Put `package.json`

Put `package.json` likes following content under the `Assets/` directory.

```json
{
    "name": "dev.monry.upm.sample-package",
    "displayName": "Sample Package",
    "version": "1.0.0",
    "unity": "2019.1",
    "description": "Sample Package for Unofficial Unity Package Manager Registry",
    "author": {
        "name": "Tetsuya Mori",
        "url": "https://github.com/monry"
    },
    "license": {
        "type": "MIT",
        "url": "https://monry.mit-license.org"
    },
    "keywords": ["sample"],
    "category": "",
    "dependencies": {
    },
    "repository": {
        "type": "git",
        "url": "https://github.com/monry/Sample-Package"
    }
}
```

The following fields are required.

* name
* displayName
* version

In principle [fields supported by package.json](https://docs.npmjs.com/files/package.json) are available.

Import `package.json` on Unity Editor so that `package.json.meta` is also generated to avoid errors when installed by Unity Package Manager.

### 4. Publish package

Publish package to Unofficial Unity Package Manager Registry using `npm` or `yarn` commands

#### `npm`

```bash
npm publish Assets
```

#### `yarn`

```bash
yarn publish Assets
```

Note: When updating a package, the value of the `"version"` field of `package.json` needs to be changed.
