# Dark Horse converter [![Build Status](https://travis-ci.org/Metalnem/dark-horse-converter.svg?branch=master)](https://travis-ci.org/Metalnem/dark-horse-converter)
Converts digital Dark Horse comics into CBZ format. Comics are delivered to official iOS/Android clients as a tar archive that is not compatible with other comic book readers, so you have to convert them using this application before you can open them in the reader of your choice.

## Downloading comics

Easiest way to download Dark Horse comics is by using [Dark Horse downloader](https://chrome.google.com/webstore/detail/dark-horse-downloader/odciinkioeagogcogbpelccibomlenhl) Chrome extension.

If you don't want to install the extension, you can do it manually (following steps apply to Chrome web browser on Max OS X, but shouldn't be much different for any other OS/browser combination).

1) Open Chrome and go to [your library](https://digital.darkhorse.com/library/).

2) Click on the comic book you want to convert.

3) View page source by clicking View -> Developer -> View source.

4) Find and click the link containing string "manifest.jsonp".

5) When download is finished, open manifest.jsonp in any text editor.

6) Find the line line looking like this:

```
"book_uuid": "9f1bb1e5dd524127bbdd0bba39d022e2"
```

7) Construct the tar archive link for the comic by replacing {uuid} part of the following string with the book_uuid that you found:

```
https://digital.darkhorse.com/api/v6/book/{uuid}
```

In this example, final link would look like this:

```
https://digital.darkhorse.com/api/v6/book/9f1bb1e5dd524127bbdd0bba39d022e2
```

8) Visit constructed link in Chrome to download the tar archive.

## Installation

```
$ go get github.com/metalnem/dark-horse-converter
```

## Binaries (x64)

[Windows](https://github.com/Metalnem/dark-horse-converter/releases/download/v1.0.0/dark-horse-converter-win64-1.0.0.zip)  
[Mac OS X](https://github.com/Metalnem/dark-horse-converter/releases/download/v1.0.0/dark-horse-converter-darwin64-1.0.0.zip)

## Usage

```
$ ./dark-horse-converter
Usage of ./dark-horse-converter:
  -i string
    	Path of a comic book file in tar format to convert (required)
  -o string
    	Output directory (if not specified, result will be placed in the same directory as the input)
```

## Example

```
$ ./dark-horse-converter -i 'The Witcher Sampler.tar' -o ~/Comics
```
