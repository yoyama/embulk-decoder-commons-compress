# Commons Compress decoder plugin for Embulk

This decoder plugin for Embulk supports various archive formats using [Apache Commons Compress](http://commons.apache.org/proper/commons-compress/) library.

## Overview

* **Plugin type**: decoder
* **Load all or nothing**: yes
* **Resume supported**: no

## Configuration

- **format**: An archive format like tar, zip, and so on. (string, optional, default: "")
  - The format type is one of supported formats by by [Apache Commons Compress](http://commons.apache.org/proper/commons-compress/).
  - Auto detect is used when there is no configuration. This can use for a single format. If a file format is solid compression like tar.gz, please set format config explicitly.
  - Some listing formats in [Apache Commons Compress](http://commons.apache.org/proper/commons-compress/) may not work in your environment. I could confirm the following formats work well. Your environment may be able to use other formats listed in the site.

## Formats

- **archive format**: ar, cpio, jar, tar, zip
  - These formats are archive formats. All files in an archive are processed by embulk.
- **compress format**: bzip2, deflate, gzip
  - These formats are compress formats. Uncompressed file is processed by embulk.
- **solid compression format**: Need to set *format* config parameter explicitly.
  - tgz, tar.gz
  - tbz, tbz2, tb2, tar.bz2
  - taz, tz, tar.Z

## Example

- Use auto detection. This can use for 1 format like tar and zip. If you would like to use a solid compression format like tar.gz, please set the format to your configuration file.

```yaml
in:
  type: any input plugin type
  decoders:
    - type: commons-compress
```

- Set a file format like tar explicit.

```yaml
in:
  type: any input plugin type
  decoders:
    - type: commons-compress
      format: tar
```

- Set a solid compression format.

```yaml
in:
  type: any input plugin type
  decoders:
    - type: commons-compress
      format: tgz
```

## Build

```
$ ./gradlew gem
```

## Reference

- [Apache Commons Compress](http://commons.apache.org/proper/commons-compress/)


