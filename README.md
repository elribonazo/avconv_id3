# avconv_id3

Read and write media file meta data (e.g., MP3 ID3 tags) using avconv's metadata framework.

# Usage

```js
var avconv = require("avconv_id3");
var fs = require("fs");

// Read song.mp3 metadata
avconv.read("song.mp3", function(err, data) {
	if (err) console.error("Error reading metadata, err");
	else console.log(data);
});

// Set the artist for song.mp3
var data = {
  artist: "Me",
};
avconv.write("song.mp3", data, function(err) {
	if (err) console.error("Error writing metadata");
	else console.log("Data written");
});

```
## Artwork

You can optionally include an array of files to be added to the source
file. This is a destructive action, it will overwrite any previous
streams on the file. For audio data, this is typically just one image.
For video, this is where you would write additional audio streams or
subtitle tracks.

```js
avconv.write("song.mp3", {}, ["cover.jpg"], function(err) {
	if (err) console.error("Error writing cover art");
	else console.log("Cover art added");
});
```
## Metadata

Avconv meta data (for songs) might include

 * `"artist"`: artist name
 * `"album"`: album name
 * `"title"`: song title
 * `"track"`: place in the album (e.g. `"5/8"`)
 * `"disc"`: for multidisc albums
 * `"label"`: record label
 * `"date"`: arbitrary, but usually year (e.g. `"2002"`)



```
npm install avconv
```
