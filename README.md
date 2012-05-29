#Hackathon@ReykjavikUNI 2012

###Videntify: Fast identification of movies and tv shows using advanced computer vision techniques

Have you ever needed an automatic way to identify your videos, or sort through your media collection?  You can do this by using Videntify, a command line client Videntifier has created for the Hackathon. Videntify isn’t simply a video hasher - we use unique visual fingerprints from the video content itself, a faster and more accurate technique.

###Download & Installation

Videntify comes both in Windows and 64-bit Linux versions (tested on debian based distros):

  https://files.videntifier.com/hackathon2012/Videntify-win32.zip  (Windows)

  https://files.videntifier.com/hackathon2012/Videntify-linux.zip  (Linux 64-bit)

Before using Videntify, you need to edit your hosts file. 

If you are on Windows, right click on notepad and select "Run as Administrator", then open the file

    C:\Windows\System32\drivers\etc\hosts

If you are on Linux this file is located in

    /etc/hosts

Add the following to the end of the file: 
    
    130.208.242.26 hnifur.videntifier.com

If you want to be able to call the Videntify binary from anywhere, make sure the directory it’s in is included in your PATH.

###Usage

Here is the full help that lists all the possible commands and parameters that Videntify supports, also available by running ```videntify --help``` on the command line.
We designed Videntify to be fast and easy to start using.  To identify a video or image, just pass it as an argument to the Videntify binary.

```
NAME
  videntify - Quickly matches a video or image file to a movie or a tv show using state of the art computer vision techniques

SYNOPSIS
  videntify [OPTIONS] SOURCE

DESCRIPTION
  Tries to match SOURCE to Videntifier's fingerprint database of movies and tv shows. A source can be video or images.

  -i, --image
      Always treat SOURCE as an image

  -v, --video
      Always treat SOURCE as a video

  -j, --json
      Output in json format

  -r, --reset-apikey
      Resets the api key, allowing you to use different credentials

  --verbose
      Verbose mode, prints additional output such as statistics

  --debug
      Debug mode, prints raw search results

  -h, --help
```
###Examples

Identifying a still image:

    $ time videntify Shrek_3_thumbnail.jpg
```
Movie   "Shrek the Third"       "http://www.imdb.com/title/tt0413267/"

real    0m0.755s
user    0m0.164s
sys     0m0.016s
```
Identifying a full length movie:

    $ time videntify nedivx-fclaus.avi
```
Movie   "Fred Claus"    "http://www.imdb.com/title/tt0486583/"

real    0m5.929s
user    0m1.712s
sys     0m0.056s
```
Identifying an HD (720p) tv show:

    $ time videntify south.park.s15e07.720p.hdtv.x264-immerse.mkv
```
Tv      "South Park"    S05E03  "http://thetvdb.com/?tab=series&id=75897&lid=7"

real    0m1.509s
user    0m0.404s
sys     0m0.036s
```

If you want the results in JSON format, just include the --json parameter:

    $ videntify south.park.s15e07.720p.hdtv.x264-immerse.mkv --json
```
{
"matches" : 
	[
		{
		"episode" : "S05E03",
		"tvshow" : "South Park",
		"type" : "Tv",
		"url" : "http://thetvdb.com/?tab=series&id=75897&lid=7"
		}
	]
}
```
###Troubleshooting

If you are on linux and cannot connect, try installing libssl-dev

###Notes

Videntify was designed with speed in mind. We downscale frames and reduce visual quality to further that goal. There are certain instances where it will not possess enough frames to identify a movie or show. If you find an interesting example of a clip or image that Videntify does not recognize, then please let us know.

While our media catalogue is relatively complete through 2011, it’s also possible some content isn’t in the Videntifier catalogue yet. Eventually Videntify will be able to identify content within days of public release.

If you are interested in viewing what movies and shows are in the database, you can browse them here:

  https://files.videntifier.com/hackathon2012/movies.txt

  https://files.videntifier.com/hackathon2012/tvshows.txt

For more about how videntify and our company visit:

http://www.videntifier.com/technology

We’re looking forward to seeing some cool, creative uses of our API.

Happy Hacking,

The Videntifier team

