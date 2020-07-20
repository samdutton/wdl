# Download YouTube video captions

Before building an app to enable search and readable transcripts for YouTube 
videos, you will need to download automatic and/or manual video captions and 
save a caption (transcript) file for each video.

Other video hosting services provide similar APIs.

## YouTube Data APIs

YouTube provides APIs to get playlist video IDs and caption tracks: see 
[developers.google.com/youtube/v3/docs/captions](https://developers.google.com/youtube/v3/docs/captions). 

[youtube-data-api](https://github.com/samdutton/youtube-data-api) demonstrates 
how to use these APIs to get video transcripts for one or more playlists.

Accessing these APIs requires authorisation and incurs quota cost. YouTube 
provides more information, examples and API Explorer functionality:

• [Captions:list](https://developers.google.com/youtube/v3/docs/captions/list)

• [Captions:download](https://developers.google.com/youtube/v3/docs/captions/download)

## youtube-dl

[youtube-dl](https://github.com/ytdl-org/youtube-dl/blob/master/README.md#readme) 
is a Node command-line program for downloading videos and video data from YouTube. 
This can be used to retrieve captions via a list of video IDs, a playlist ID, or 
other mechanisms. You will need to clean up the caption files after download.

###1. Get the captions
```
youtube-dl -o 'src/srt/%(id)s' --batch-file src/youtube-urls --no-check-certificate --skip-download --write-auto-sub --youtube-skip-dash-manifest --ignore-errors
```

###2. Fix subtitle durations
See [FFmpeg Advanced Subtitle options](https://ffmpeg.org/ffmpeg.html#Advanced-Subtitle-options) 
for more information.

```
for i in ./*.vtt ; do ffmpeg -fix_sub_duration -i "$i" "$( echo "$i"|sed 's/\.srt.en.vtt//g' ).srt"  &&  rm -f "$i"  ; done
```

###3. Fix subtitle overlaps
See [documentation](https://github.com/bleggett/subtitle-overlap-fixer) for more 
information.

```
for i in ./*.srt ; do subtitle-overlap-fixer "$i"; done;
```

###4. Clean up files
```
rm ./*.bak
```

If necessary rename *\*.en.vtt.srt* to *\*.srt*.

You can do this from the command line or (on Mac) in Finder select all relevant 
files then right-click and select **Rename**.

