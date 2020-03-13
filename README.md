# archive-files

Package for reading different archive files in a consistent way.

[![npm](https://img.shields.io/npm/v/@shockpkg/archive-files.svg)](https://npmjs.com/package/@shockpkg/archive-files)
[![node](https://img.shields.io/node/v/@shockpkg/archive-files.svg)](https://nodejs.org)

[![dependencies](https://david-dm.org/shockpkg/archive-files.svg)](https://david-dm.org/shockpkg/archive-files)
[![size](https://packagephobia.now.sh/badge?p=@shockpkg/archive-files)](https://packagephobia.now.sh/result?p=@shockpkg/archive-files)
[![downloads](https://img.shields.io/npm/dm/@shockpkg/archive-files.svg)](https://npmcharts.com/compare/@shockpkg/archive-files?minimal=true)

[![travis-ci](https://travis-ci.org/shockpkg/archive-files.svg?branch=master)](https://travis-ci.org/shockpkg/archive-files)


# Overview

A consistent set of archive extractors.

Mainly those features required to work with shockpkg packages are implemented.

Support for other archives or other features are likely considered out of scope for this project.

Some functionality, like disk image reading, resource forks, and file permissions, can only be fully supported on certain platforms.


# Usage

## Basic Usage

### Open a ZIP file

```js
import {ArchiveZip} from '@shockpkg/archive-files';

async function main() {
	const archive = new ArchiveZip('path/to/archive.zip');
	await archive.read(async entry => {
		console.log(entry.path);
		await entry.extract(`extracted/${entry.path}`);
	});
}
main().catch(err => {
	process.exitCode = 1;
	console.error(err);
});
```

### Open a file by file extension

```js
import {createArchiveByFileExtension} from '@shockpkg/archive-files';

async function main() {
	const archive = createArchiveByFileExtension('path/to/archive.zip');
	await archive.read(async entry => {
		console.log(entry.path);
		await entry.extract(`extracted/${entry.path}`);
	});
}
main().catch(err => {
	process.exitCode = 1;
	console.error(err);
});
```


# Bugs

If you find a bug or have compatibility issues, please open a ticket under issues section for this repository.


# License

Copyright (c) 2019-2020 JrMasterModelBuilder

Licensed under the Mozilla Public License, v. 2.0.

If this license does not work for you, feel free to contact me.
