# pdify

> Generate PDF files from a directory of images

[![Build Status](https://travis-ci.org/0xazure/pdify-go.svg)](https://travis-ci.org/0xazure/pdify-go)
[![Coverage Status](https://coveralls.io/repos/0xazure/pdify-go/badge.svg?branch=master&service=github)](https://coveralls.io/github/0xazure/pdify-go?branch=master)
[![Go Report Card](https://goreportcard.com/badge/0xazure/pdify-go)](https://goreportcard.com/report/0xazure/pdify-go)

## Install

```
$ go get github.com/0xazure/pdify-go
```

## Usage

Specify a relative or absolute directory path as the argument.

```
$ pdify <directory>
```

### Options

##### `-o`, `--output <filename>`

Specify the output file. Requires a `.pdf` extension.

### Examples

```
# Basic usage
$ pdify archive # Produces archive.pdf

# Specify output file
$ pdify archive --output image_archive.pdf # Produces image_archive.pdf
```

Given a directory structure:

```
archive
├── vol00
│   ├── 00.jpg
│   ├── 01.jpg
│   ├── 02.jpg
│   └── 03.jpg
├── vol01
│   ├── aa.jpg
│   ├── ab.jpg
│   ├── ac.jpg
│   └── ad.jpg
└── vol02
    ├── xx.jpg
    ├── xy.jpg
    ├── xz.jpg
    └── xq.jpg

3 directories, 12 files
```

`pdify` traverses the directory structure in a depth-first manner, and
appends image files to the resultant PDF in lexicographical (alpha)
order.  Given the directory structure above, `pdify archive` would produce the
following internal PDF structure:

```
archive.pdf
├── vol00/00.jpg
├── vol00/01.jpg
├── vol00/02.jpg
├── vol00/03.jpg
├── vol01/aa.jpg
├── vol01/ab.jpg
├── vol01/ac.jpg
├── vol01/ad.jpg
├── vol02/xx.jpg
├── vol02/xy.jpg
├── vol02/xz.jpg
└── vol02/xq.jpg
```

## License

MIT © Stuart "0xazure" Crust
