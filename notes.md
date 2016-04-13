Started playing around with it a couple of years ago as a side project, a nice change of pace, and could make a fun talk.

# What is Lua?

Quoting lua.org: "a powerful, fast, lightweight, embeddable scripting language."

Created in 1993 in the Computer Graphics Technology Group of the Pontifical Catholic University of Rio de Janeiro.

A little newer than Python (1991), a little over than JavaScript or Java (1995).

"Lua" is Portuguese for "moon."

Reminds me most of a bit more verbose JavaScript - apparently both JS and Lua took some inspiration from Scheme.

# Why should I care?

No shortage of languages available...
Lua's unique because it's _fast_ and _easy to embed_ (provides an easy API to work with, doesn't add a lot of weight)

## Embedded scripting environment for applications and servers

Adobe Photoshop Lightroom; ExtraPuTTY fork of the PuTTY SSH client; HAProxy (load balancer used by GitHub, StackOverflow, bunches of other guys); Lighty and Nginx web servers; MediaWiki, the engine that powers Wikipedia; MySQL Workbench; Nmap network scanner and Wireshark network sniffer; Redis (one of the most popular key-value stores and NoSQL databases); VLC media player

Could find a couple dozen more; these are just applications that I recognized or have used

## Example: Viruses

Darker note - Flame was a virus - maybe more of a cyberweapon or espionage tool - that, in 2012, infected hundreds of computers in Iran and elsewhere in the Middle East, suspected to be created by U.S. and Israeli intelligence agencies, was partially implemented in Lua.

## Example: CloudFlare

CloudFlare is a content delivery network.  You can put them in front of your web site, they'll offer caching, various optimizations, web application firewall, free SSL, denial-of-service protection...  Bunch of big-name customers.

Run on Nginx, I would have assumed that they do a lot of heavy C work to get all of those performance-critical network features running, but they've been switching to Lua, because it's a lot easier to work in and still lets them get extremely fast.  Now one of the sponsors of LuaJIT.

## Games

World of Warcraft is the best known - a good part of the UI is implemented in Lua, allowing players to create various UI add-ons and customizations

A *lot* of games over the last almost 20 years...  (Wikipedia lists over 150; probably several times that)

## Game engines

All of these have free options

Cocos 2d-x - a very popular multi-language, cross-platform framework, offers Lua as one of its options

Corona SDK - very popular for mobile development

CryEngine - AAA 3-D game engine

Defold - sponsored by King, the company that makes Candy Crush

LOVE (Love2d) - easy to pick up, popular at game jams and such

Lumberyard - Amazon's new free engine, which they're pushing to promote their AWS - based on CryEngine

Moai - I don't really know anything about this one, but it's also fairly popular.

T-Engine 4 - an example of a more niche engine, this is designed primarily for roguelikes

(I don't have nearly enough time to be an expert on all of these.  Some or all of what I just told you could be wrong.)

# How do I learn Lua?

_Programming in Lua_ available on Amazon, and an older edition available for free online.  That's a good resource.

The reference manual is online.  That's a good resource.

Lots of tutorials on the wiki.  Those are good resources.

I only have X minutes, so I'm ignoring all of those.

Instead, we're going to learn Lua in 15 minutes

Double - 53 bits, up to 9 trillion or so
Strings - double-brackets, Lua keeps the embedded newlines and whitespace and everything
More verbose than JS or other curly-brace languages

Metatables are _very flexible_:
That `__newindex` method?  Set a function there that throws an error, and you have a read-only table.
Lazy loading or memoizing?  Add a `__index` method that calculates or retrieves the value on demand.
Want to catch undefined variables?  You can set `_G`'s metatable, and set an `__index` and `__newindex` on it - very flexible stuff.

# Lua: the bad parts

Every language has its bad parts, right?

I feel like I can't use this photo much any more.

A bit more subjective.

So why talk about Lua's bad parts? It's worth being aware of them before you get into it, and, even if you never write in Lua, I find that looking at how other languages approach a problem helps broaden my horizons.

### 1-based indexing

Pretty horrifying. Different than every popular programming language of the last twenty years. I've seen people swear off Lua forever because of this.

Edsger Dijkstra essay, 1982, argued it's mathematically more elegant.
Nowhere near smart enough to argue with Dijkstra.

But...

No *normal* human starts counting at 1.  And off-by-one errors are a common source of problems.

Depending on who you ask, it's partially a historical accident that we programmers find it so natural.  BCPL chose 0-based, not because it made for more efficient run-time calculations of pointers and offsets, but to shave a bit of time off of compile cycles.  This was important, not just because efficiency was important in general, but because high-priority jobs could bump lower-priority jobs, and since IBM was so generous to MIT with computing hardware, if the president of IBM needed to calculate yacht race handicaps, that was an important job.

So maybe this isn't so bad.

### Limited standard library

Missing a bunch of functionality...

But...

My scripting language of choice is Python. Python's motto is batteries included.  It's incredibly featureful - can parse JSON, XML, email messages, has an HTTP client and server, has a SQL database engine (SQLite), a GUI toolkit.

Here's what my Python installation folder looks like. 57 MB of space for its standard library. For modern networks and disks, for a language that's installed systemwide, that's not bad at all.  But Lua's designed to be embeddable - add it to a utility like ExtraPuTTY, it's 20 times the entire utility.

Lua's popular, so you don't have to reinvent the wheel. Lua wiki has recipes, and there's a package manager, LuaRocks, that provides libraries.

Also, it's not all bad.  For example, printf-style string formatting, so it can left-pad out of the box, unlike other languages which shall remain nameless.

### Incompatible implementations

Lua 5.3 (and 5.2)

* Integers (handled transparently)
* Bitwise operators
* UTF-8 support (previously available in libraries)
* `goto` (Lua has no `continue` statement) (Yes, goto is considered harmful. Lua's philosophy is "mechanisms instead of policies" - just like providing metatables, so you can implement prototypical or classical or whatever. So, here, instead of building all that flow control into the language, they give you the tools to do continue, nested break, Python-style for/else, etc.)
* Finalizers

Bunch of other, smaller features.

LuaJIT

# Further information

Inspirations (from Wikipedia):

> Lua syntax for control structures was mostly borrowed from Modula (if, while, repeat/until), but also had taken influence from CLU (multiple assignments and multiple returns from function calls, as a simpler alternative to reference parameters or explicit pointers), C++ ("neat idea of allowing a local variable to be declared only where we need it"[4]), SNOBOL and AWK (associative arrays). In an article published in Dr. Dobb's Journal, Lua's creators also state that LISP and Scheme with their single, ubiquitous data structure mechanism (the list) were a major influence on their decision to develop the table as the primary data structure of Lua.[6]

