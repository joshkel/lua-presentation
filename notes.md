# What is Lua?

Quoting lua.org: "a powerful, fast, lightweight, embeddable scripting language."

Created in 1993 in the Computer Graphics Technology Group of the Pontifical Catholic University of Rio de Janeiro.

A little newer than Python (1991), a little over than JavaScript or Java (1995).

"Lua" is Portuguese for "moon."

Reminds me most of a bit more verbose JavaScript - apparently not a coincidence, since JS and Lua took some inspiration from Scheme.

# Why should I care?

No shortage of languages available...
Lua's unique because it's _fast_ and _easy to embed_.

## Application scripting

Adobe Photoshop Lightroom; ExtraPuTTY fork of the PuTTY SSH client; Lighty and Nginx web servers; MediaWiki, the engine that powers Wikipedia; MySQL Workbench; Nmap network scanner and Wireshark network sniffer; VLC media player

Could find a couple dozen more; these are just applications that I recognized or have used

Darker note - Flame virus that, in 2012, infected Iran and elsewhere in the Middle East, suspected to be created by U.S. and Israeli intelligence agencies, was partially implemented in Lua.

## Games

World of Warcraft is the best known - a good part of the UI is implemented in Lua, allowing players to create various UI add-ons and customizations

A *lot* of games over the last almost 20 years...

## Game engines

All of these have free options

Cocos 2d-x - a very popular multi-language, cross-platform framework, offers Lua as one of its options

Corona SDK - very popular for mobile development

CryEngine - AAA 3-D game engine, now included in Amazon's free Lumberyard game engine

Defold - sponsored by King, the company that makes Candy Crush

LOVE - popular beginner/hobbyist choice

T-Engine 4 - an example of a more niche engine, this is designed primarily for roguelikes

Lumberyard - Amazon's new free engine

# Lua: the bad parts

### 1-based indexing

Edsger Dijkstra essay, 1982, argued it's mathematically more elegant.
Nowhere near smart enough to argue with Dijkstra.
But...
*No* normal humans count at 1.

### Incompatible implementations

Lua 5.3

* Integers (handled transparently)
* Bitwise operators
* UTF-8 support (previously available in libraries)

Lua 5.2

* `goto` (Lua has no `continue` statement) (Yes, goto is evil. Lua's philosophy is "mechanisms instead of policies" - just like providing metatables, so you can implement prototypical or classical or whatever)
* Finalizers

LuaJIT

# Further information

Inspirations (from Wikipedia):

> Lua syntax for control structures was mostly borrowed from Modula (if, while, repeat/until), but also had taken influence from CLU (multiple assignments and multiple returns from function calls, as a simpler alternative to reference parameters or explicit pointers), C++ ("neat idea of allowing a local variable to be declared only where we need it"[4]), SNOBOL and AWK (associative arrays). In an article published in Dr. Dobb's Journal, Lua's creators also state that LISP and Scheme with their single, ubiquitous data structure mechanism (the list) were a major influence on their decision to develop the table as the primary data structure of Lua.[6]

