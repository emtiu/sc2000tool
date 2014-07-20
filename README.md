sc2000tool [![Flattr this repository](http://api.flattr.com/button/flattr-badge-large.png)](https://flattr.com/submit/auto?user_id=mtu&url=http://github.com/emtiu/sc2000tool/&title=sc2000tool&language=de&tags=github&category=software)
==========

A command line utility for analysis and certain modifications of Sim City 2000 savegames (*.SC2). Main features:

* universal money cheat
* change city and mayor name
* read city details from file (money, year founded, current game date, …)
* verify file integrity and structure

## Use cases and example

Sim City 2000 offers no convenient way of changing the name of a city (which is chosen upon starting a new game) or the mayor's name (which is determined at game installation). If you play an existing savegame and/or an abandonware version of the game, you're probably stuck with names that others have chosen. *(This is what got me started on this project in the first place.)*

Also, most money cheats are clumsy. Available tools (usually DOS or Windows binaries)  will usually just give you the maximum possible amount of money ($2,147,483,647), which is uselessly close to where the variable overflows. Other cheats require you to jump through hoops in-game or get down and dirty with a hex editor.

This is where **sc2000tool** comes in. See this simple example and its effect on the game:

```
$ sc2000tool -M 50000 -N Awesomeville -Y "Jimbob Johnson" NEWCITY.SC2 -O MYCITY.SC2
```

![Screenshot comparison illustrating in-game effects](docs/screenshots.png?raw=true)

You can also analyze files on the command line, like so:

```
$ sc2000tool --city MYCITY.SC2
City name: Awesomeville
Mayor name: Jimbob Johnson
Year founded: 2000
Current Date: May 23, 3576
Money: $50,000
```

Other options enable you to examine the file structure and contents down to the byte level.

## Requirements and compatibility

A stock Python 2.7 should be all that's needed for sc2000tool to run. If you replaced `optparse` with `argparse`, you could probably get this requirement down to Python 2.3, but I haven't tried that.

So far, sc2000tool has only been tested on one setup:
* **Known working**
  * **Platform:** Linux 64-bit with Python 2.7.3
  * **Sim City 2000:** MS-DOS, rev. 1.01
  * **… running in:** DOSBox 0.74

I'd love to see that list grow, especially for Sim City 2000 on other platforms like Mac or Windows. Any report of success or failure is greatly appreciated!

## Documentation

All of sc2000tool's features are listed in its built-in help. Simply call it without any arguments, or explicity with `sc2000tool -h` or `sc2000tool --help`.

When in doubt, take a peek at the code. It's scarcely commmented, but hey, at least it's not Perl ;)

## Feedback

I'm immensely interested in whether anybody besides myself will want use this, so I'll be glad to take your questions or comments here, on Twitter or by email.

## Credit

Most of us wouldn't be able to enjoy all these wonderful old games without the tireless work of the abandonware community. Here, I'd like to thank [XTCabandonware](http://www.xtcabandonware.com/game/832/simcity-2000) especially.

This project would never have gotten off the ground without the work of **David Moews**, who in 1995 published [an in-depth analysis of the .SC2 savegame file structure](http://djm.cc/simcity-2000-info.txt). Written over 18 years ago, it probably still constitutes the sum of all public knowledge about .SC2 files.
