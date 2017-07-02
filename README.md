# ConstellationSpotify
This Spotify package allows you to stream music from Spotify to any Debian based linux machine, provided you have a PREMIUM account. The package retrieves your favorite playlists to play it seamlessly. 
The package was designed to be integrated in a smart clock project.

## Installation
### Managing dependendies:
Python 2.7 has to be installed and running on your linux machine to enable ConstellationSpotify to run. To install it, simply run this command in your terminal: `sudo apt-get update` , `sudo apt-get install python python-dev`

Python libraries you need to install, simply run `sudo pip2 install <library>`
- pyalsaaudio
- pyspotify

How to install Constellation on your Debian based machine => https://developer.myconstellation.io/getting-started/installer-constellation/

### Constellation server-side:
Fetch the Spotify.zip file downloaded by cloning the github repository and drop it in the Package Repository / Upload Package section.
Once the package installed, click on Deploy Package on the desired Sentinel and follow the instructions, enter your spotify username and password, and you shouldn't change the other settings unless you know what you're doing.

### Warning :
When pushing a Spotify playlist to the package, check that it does not exceed 15~20 tracks, or you will be prompted a timeout error by pyspotify.
More info on pyspotify/libspotify => https://pyspotify.mopidy.com/en/latest/



## Package detail
### StateObjects
This package pushes 2 StateObjects to Constellation:
- Spotify_isPlaying, Boolean type: returns if Spotify is playong in the background, or not
- track_Title, String Type : returns the title of the song currently playing. 

### MessageCallbacks
 MusicControl is the MessageCallback used to push orders to Spotify via Constellation. It is a Python dictionnary `{"instruction":<instruction>, "uri":<uri>}`. 
 Here's the exhaustive list of instructions you can pass to the package:

|  Instruction  	|       URI      	|
|:-------------:	|:--------------:	|
|   PLAY_PAUSE  	|        /       	|
|   PLAY_TRACK  	|   <TRACK_URI>  	|
| PLAY_PLAYLIST 	| <PLAYLIST_URI> 	|
|   NEXT_SONG   	|        /       	|
| PREVIOUS_SONG 	|        /       	|
| TURNUP_VOLUME 	|        /       	|
|   TURNDOWN_VOLUME |        /       	|
