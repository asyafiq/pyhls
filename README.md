# pyhls

[![Build Status](https://travis-ci.org/billyshambrook/pyhls.svg?branch=develop)](https://travis-ci.org/billyshambrook/pyhls)
[![Build status](https://ci.appveyor.com/api/projects/status/n3h3cge0j7ap0yd2/branch/develop?svg=true)](https://ci.appveyor.com/project/billyshambrook/pyhls/branch/develop)
[![Code Health](https://landscape.io/github/billyshambrook/pyhls/project-setup/landscape.svg?style=flat)](https://landscape.io/github/billyshambrook/pyhls/develop)
[![codecov.io](http://codecov.io/github/billyshambrook/pyhls/coverage.svg?branch=develop)](http://codecov.io/github/billyshambrook/pyhls?branch=develop)
[![Documentation Status](https://readthedocs.org/projects/pyhls/badge/?version=latest)](https://readthedocs.org/projects/pyhls/?badge=latest)

A HTTP Live Streaming (HLS) python library

Apple provides a number of tools to work with HLS however these are only
usable on OS X. This library aims to include the functionality of these tools,
plus more, and offer this across multiple platforms.

- [Support](#support)
- [API](#api)
    - [Create](#create)
    - [Parse](#parse)
    - [Validate](#validate)
    - [Edit](#edit)
- [Roadmap](#roadmap)

## Support

To ensure full support of a version during initial development of this library, version support
will be iterated from the first to the latest. **We do** plan on supporting all versions before
the first release.

`pyhls` currently supports Version 1 of the HTTP Live Streaming specification
as defined in the [Pantos specification][pantos]


## API


### Create

To create a manifest:

    >>> import pyhls

    >>> manifest = pyhls.create('master.m3u8')
    >>> manifest.add_stream(media='1.ts', playlist='1.m3u8')

This will create a master and media playlist for the media file '1.ts'.

Once you have finished setting up the manifest, you can write out the manifest
and all it's dependencies to a folder.

    >>> manifest.out(destination='/mymanifests')
    ('master.m3u8', '1.m3u8', '1.ts')


### Parse

To parse a manifest, simply do:

    manifest.parse('master.m3u8')


### Validate

To validate a manifest:

    warnings, errors = pyhls.validate('master.m3u8')

This will return you a list of warnings and errors, each with a description and line
number.


### Edit

To edit a manifest:

    manifest = pyhls.parse('master'.m3u8)
    manifest.add_stream(media='2.ts', playlist='2.m3u8')

When you parse a manifest, you can then edit it just like you would when
creating.


## Roadmap

Overview on how things currently stand:

* Build out the structure of the package.
* Add full create, parse, validate and edit support for version 1.
* Iterate on support for all other versions.
* Add validation for video/audio/subtitle media files.
* Add support for creating media files.
* Add support for encryption of media files.


[pantos]: https://tools.ietf.org/html/draft-pantos-http-live-streaming "Pantos"
