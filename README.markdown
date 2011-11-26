# Spotify PHP API #

## About ##

A simple PHP wrapper for Spotify's Metadata API.  
Your feedback is always welcome.

## Requirements ##

- PHP 5.2.x or higher
- cURL

## Get started ##

### Setup class and search for an Artist ###

    <?php
        require_once 'spotify.class.php';
        
        $spotify = new Spotify();
        
        // Search for an artist by its name
        $artist = $spotify->searchArtist('Maroon 5');
        
        // Take a look at the response
        echo '<pre>';
        print_r($artist);
        echo '<pre>';
    ?>

### URI Lookup ###

    <?php
        // Look up for an artist by its Spotify URI
        $spotify->lookUp('spotify:artist:58lV9VcRSjABbAbfWS6skp', 'album');
    ?>

### Generate Spotify URI ###

    <?php
        // Search for a track
        $track = $spotify->searchTrack('Narcotic');
        
        // Receive the Spotify URI for the first track
        $uri = $spotify->getUri($track); // spotify:track:6MSPmHR15vgpa0A5L205Xv
        
        // Display Spotify link (opens Spotify player)
        echo "<a href="/{$uri}"/>Play Song with Spotify</a>";
    ?>

## Available methods ##

### Search methods ###

- `searchArtist($name, <$page>)`
- `searchAlbum($title, <$page>)`
- `searchTrack($title, <$page>)`

All `<$page>` parameters are optional. If the page number is undefined, the first one will be returned *(default)*.

> [Sample responses of the Search Endpoints.]()

### Lookup method ###

- `lookUp($uri, <$detail>)`
  - `$uri` is a valid Spotify URI like: `spotify:artist:58lV9VcRSjABbAbfWS6skp`, `spotify:track:4I4BS0OeI7VZdo5WeEQHFP`
    - the URI type will be automatically detected
  - `$detail` defines the detail level in the response:
    - Artist: `album`, `albumdetail`
    - Album: `track`, `trackdetail`
    - Track: `no detail level available`
- `getUri($obj, <$count>)`
  - `$obj` is a JSON object returned by one of the search methods
  - `$count` *[optional]* number of result (first result = 0 *[default]*)

> [Sample responses of the Lookup Endpoints.]()

If you need additional informations, take a look at [Spotify's API docs](http://developer.spotify.com/en/metadata-api/overview/).

## History ##

**Instagram 0.8 - 27/11/2011**

- `release` First official released version
- `update` Detailed documentation

**Instagram 0.5 - 26/11/2011**

- `release` Beta version
- `update` Small documentation

## Credits ##

Copyright (c) 2011 - Programmed by Christian Metz  
Released under the [BSD License](http://www.opensource.org/licenses/bsd-license.php).