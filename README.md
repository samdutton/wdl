# Build search and readable transcripts for conference videos

This is a Node application that processes caption files from conference videos to enable search and create readable transcripts.

The code could easily be adapted to work with caption files from other playlists.

<!--- Try it out at [samdutton.github.io/wdl](https://samdutton.github.io/wdl). --->

---

## Installation and usage

1. Clone or download the code.
2. Add your SRT caption files to the [_input_](src/srt) directory.
3. From a terminal `cd` to the `src` directory and run `node index.js -s`,
optionally setting flags (see below). This creates HTML for readable transcripts (in the [docs](docs) folder) and builds the search index if the `-s` flag is set.
4. Progress updates and errors are logged to the console.
5. When conversion is complete, view the results from
[index.html](docs/index.html) in the [_app_](docs) directory, the directory
used for GitHub Pages. This directory includes a [CSS file](docs/css/main.css)
and a [JavaScript file](docs/js/main.js) to style the transcripts and
enable interaction.

### SRT and app directories

* When you clone the repo, the directories for the [_SRT_](src/srt) caption
files and the [_app_](docs) contain sample files.
* You can customize _srt_ and _app_ directories — see flags below.

## Error handling

Check for errors in _error-log.txt_.

## Command line options

```
-a, --append      Append output to existing files in output directory
-h, --help        Show help
-i, --input       Input directory, default is [_input_](src/input)
-l, --validate    Validate HTML output, default is false
-o, --output      Output directory, default is [_output_](src/docs)
-s, --search      Create search index
-t, --transcript  Create transcript HTML files, default is false
-u, --upload      Upload records to search service, default is false
```

## Feedback, feature requests and bug reports

- Please [file an issue](https://github.com/samdutton/wdl/issues/new)
including input files where relevant.
- See the [TODO](TODO) file for work in progress.

## Known issues

### Google Translate widget

This widget is [no longer supported](https://translate.google.com/intl/en/about/website)
and the language selection popup is not laid out responsively.

Probably best to remove unless the layout can be fixed (others have tried!)

---

<!--- Please note that this is not an official Google product.  --->
