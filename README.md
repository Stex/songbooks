# Songbooks

This gem will run a simply web server to format / display chord files.   
A chord file - at least here - is a text file with lyrics and chords for a certain song:
 
```
    Bm                    A        Bm
Our Hero, our Hero claims a warrior's heart
  Bm                     A         Bm
I tell you, I tell you the Dragonborn comes
       Bm                       A9         Bm
With a voice wielding power of the ancient Nord Art
  Bm                 A9         Bm
Believe, believe the Dragonborn comes
```
([Malukah](www.malukah.com/)'s version of Skyrim's "The Dragonborn comes")

It allows you to view all songs in a certain directory and generate PDF songbooks from them.

![Server](docs/server_screenshot.png)

## Installation

Simply install the gem using a ruby version >= 2.2:

    $ gem install songbooks

## Usage

To start a songbooks server in a certain directory, use the following command:

    $ sb_server start [DIRECTORY]
    
If you don't specify a directory, the server will use the directory you are currently in.
This means, the following commands are equivalent:

    $ sb_server start /path/to/chords
    $ cd /path/to/chords && sb_server start
    
Afterwards, open http://localhost:4567 in your browser and you're good to go.

## Annotations / Special Lines

The server automatically searches for certain patterns in the chord files: 
Song metadata and formatting information.

### Metadata
Currently, only song title and artist are available as metadata. You may specify them by adding 
the following lines to your chord files:

    @artist NAME
    @title SONG_TITLE
    
Name/Title don't have to be in the same line as the annotation, the following lines are totally 
valid as well:

```
@title
The Dragonborn comes

@artist
Skyrim OST (Cover by Malukah)
```

### Formatting

As seen in the above screenshot, it is possible to specify sections in your 
chord files. Each file starts with an initial unnamed section. To create a named section,
add a line in the following format to your file:

    ## SECTION NAME

## Planned features

- Chord transposing
- Better handling of chord files without annotations
- Better PDF formatting
- PDF generation from command line, e.g. `sb_server generate_songbook --out file.pdf [DIRECTORY]`

## Development

After checking out the repo, run `bin/setup` to install dependencies. 

The project contains a `Guardfile` to automatically generate css and javascript files from 
coffeescript and scss, so make sure you start guard before changing anything in `app/assets`:

    $ guard

To install this gem onto your local machine, run `bundle exec rake install`. 

## Contributing

Bug reports and pull requests are welcome on GitHub at https://github.com/stex/songbooks.

## License

The gem is available as open source under the terms of the [MIT License](http://opensource.org/licenses/MIT).

