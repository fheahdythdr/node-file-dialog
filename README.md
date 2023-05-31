# node-file-dialog

A NodeJS library that lets you open file dialogs

## Current support

Only supports Windows until I can figure out how to package for Linux aswell using PyInstaller.

## Getting started
### Installation
```
npm install @fheahdythdr/node-file-dialog
```

### Usage
The configuration has 6 properties, 1 being required.
Optional properties are:
```
ext: default file extension
types: Object<string, string> (available file extensions you can pick from/save as)
startdir: start directory for file explorer
startfile: file selected when file explorer opens (also default filename in save as dialog)
title: title of explorer window
```

Required property is:
```
dialogtype: type of dialog to open, directory, save-file, open-file or open-files
```

### Documentation

This package exports a function, known internally as dialog.
To use it, you do

```js
const { dialog } = require('@fheahdythdr/node-file-dialog');
const config = {
    dialogtype: 'open-file', // the rest of these are optional, dialog only needs dialogtype.
    ext: "mp4 files", // the default extension, use the name of it and not which extensions it uses
    types: [ // the extensions you can pick from
        {
            display: "mp4 files", extensions: "*.mp4"   
        }
    ],
    startdir: "C:\\", // starting directory
    title: "open file" // tkinter window's title
    // additionally: startfile, the file that is selected by default
}
dialog(config).then(res => {
    // res is an array, loop through it if you need to perform an action on each selected file
    console.log(res); // logs an array with whatever file(s) the user selected.
}).catch(err => {
    // throws an error if the user doesn't pick anything, so let's catch that
    console.error(err);
})
```

### Examples

##### NodeJS

```js
const { dialog } = require('@fheahdythdr/node-file-dialog')
const config = {
    dialogtype: 'open-file'
};
const result = dialog(config).then((result) => {
    console.log(result);
}).catch(err => {
    console.error(err);
});
```

##### Typescript

```ts
import { dialog, Config } from '@fheahdythdr/node-file-dialog';

const config: Config = {
    dialogtype: 'open-file'
}

dialog(config).then((result) => {
    console.log(result);
}).catch((err: Error) => {
    console.error(err.message);
});
```

### Extra info

Unpacked size is 21.9 MB due to pre-packing Python311 with PyInstaller so the user doesn't need Python to use the python file.

### Changelog

Update README.md to include info about file size
