# Notes from OSCON 2014

## Just Enough Math
Paco Nathan

Move in late 90's defensibility -> predicatibility
- social sciences math -> physics math
- servers scale on commodity hardware (amazon, ebay, yahoo, google)
- data modeling -> algorithmic modeling
  - hundreds of predictive models (Netflix Prize)

Abstract Algebra
- can avoid bottlenecks by compilers computing algebra

Functional Programming
- less resources spent on sorting
- parralelism much easier

Probabilistic Data Structures
- "Hash, don't sample"

Singular Value Decomposition
- Recommendation Systems

Optimization
- Machine learning subset of optimization

Summary
- Data needs to be organized
- Math helps organize data


# Docker
  - As little operating system as possible
  - Small
  - Fast

- Containers are not new..
  - Only on radar of advanced sysadmin types

- Separation of concerns
  - Dev guy worries about insides
    - Code functionality etc.
  - Ops guy worries aobut outsides
    - Logging etc.

- Docker Registry stores config "think Features server"
  - Download once, get changes from server
  - No need to move around the whole container once deployed
  - Can run your own, seems way easier to user theirs.......

- Written in Go

- For OSX and Windows we hav Boot2Docker

- Architecture
  - Single client/server binary
    - recieves / sends Docker api requests
  - Docker hub registry

- Dockerfile
  - DSL similar to Bash
  - 'docker build'
  - super similar to Vagrant
  - every line if you change will change everywhere
  - executed in order
  - cached so never run multiple times

- Security
  - All ports closed by default
  - Linking one container talks to another on port

- 'docker run -t -i web /bin/bash'
  - open a shell within our container to debug whats going on inside

- docker inspect
  - find out about container
  - container ids are hashes don't need whole hash to reference
  - 'docker inspect $(docker ps -l -q)' inspects last container

- container networking
  - Assign ports, assign ips, get containers talking publicly or to eachother

- volumes
  - 'VOLUME /var/lib/postrgres' in DockerFile
  - 'docker -v /var/lib/postgres' at runtime
  - bypasses copy on write system (Drupal code goes here!)
  - share directory or single file
    - betwen containers
    - between host and container
  - Volumes container independent

- Connection containers
  - how do you break up components?
    - depends on your app... and you want to design
  - 

# Learning Go
  - http://spf13.com/presentation/first-go-app
  - How we got here
    - Blogger wanted fast static site generate to kill wordpress
    - wrote Hugo generates sites in milliseconds
    - 2nd most contributors of any Go project
  - Why go
    - software hard to write
    - compilation is fast - so fast it feels dynamic...
    - installation and environments are hard
    - concurrent
    - not theoretically exciting
  - Packages
    - not an object and not a class
    - all visibility at package level
  - Feels like "C the good parts"
  - Braces not spaces C-esque
  - Not many semicolons (inserted by compiler, coding standards compiler enforced)
  - GO FMT
    - reformats code
    - can be used for reformatting
    - FIX ALL THE THINGS
  - GO TEST
    - writing tests part of language
    - https://github.com/fatih/vim-go runs this automatijically on save
  - Has first class functions
    - functions passed to others
    - etc.
  - Easy pointers (hmm will have to see...)
  - Types
    - all the standard types are there
    - fixed not aliases
    - Slices vs Arrays
      - Slice
        - dynamically grows
        - core data structer for lists
      - Rarely use arrays except for fixed lengths
    - Two types of types
      - slices, maps, channels == reference types
  - new(T)
    - allocates zeroed value of type T
    - returns pointer to the new value ( \*T)
    - used for all non-reference types
  - make()
    - reference type, does not return pointer
  - composite literal
    - expression that creates a new value each time its evalueated
    - pseudo constructorish
      - go doesn't have constructors
  - goroutine
    - function executing concurrently with others in the same address space
    - not thread or process
  - Channels
    - lightweight
    - synchronize goroutines
    - sender / receiver
    - most Go unique part of language
  - for
    -for foreach and while all == for in go
  - Append
    - grows shrinks slices and moves in memory


# NODE.js Three Ways
  - @aaroncois, Tim
  - reactive vs. asynchronous
    - reactive: interaction paradigm / communication
    - asynchronous: programming paradigm 

  - package.json for storing dependencies
  - node_modules local by design
  - those two combined should be able to get you working
  - Express
    - Node MVC framework for frameworky stuff
    - Node not as impressive after learning Go all morning...
    - Having trouble getting excited about MVC in node
    - Much easier than Symfony to get serve a page for first time <- see positivity!
  - Socket.io
    - Ahh here we go this is more Nodey
  - Meteor
    - Single page
    - reactive
      - everything goes everywhere
    - security / performance
      - `meteor remove autopublish` 
      - now we have to decide what to publish
    - Uses Fibers (nodejs library)
      - makes iterative code into synchronous callbacks
    - Super rapid prototyping
 
# HHVM
  - HPHPC
    - quick dirty hack in 2010 - 2011
  - 2013
    - HHVM gets a dedicated team
    - Open Source
  - 2014
    - Lots of new shiny
    - devops and continuous integration
    - Hack programming language
  - Community
    - Baidu running on it!
  - Compile to machine code then run it
  - Production mode serves cached code
    - 10 -25% gain
  - Uses zend engine to compile to bytecode
    - optimize this bytecode
    - virtualized
    - then into machine code
    - slower to compile, faster to load <- important part
  - both faster and more requests per second
  - HACK
    - Both superset and subset of PHP
    - gradually typed language
      - no strict typing but strongly encouraged
    - public functions actually public
    - generics
    - arrays rebooted
    - async functions for batching framework
    - hh_server convert "The hackificator"
    - conversion at facebook
      - 10% - 90% over 1 year
    - No globals
    - no html embedded in your php
    - User attributes
      - user defined metadata
    - XHP
      - XSS filterer for markup output
      - Why did Drupal pick Twig instead of this? WHY!
      - componentizer for html
      - strongly staticly typed
    - HPHPd
      - interactive shell
      - gdb-like debugger
      - xdebug support getting built
    - Spec for php is "does it work" "its compliant"
      - Facebook has hired someone to write the PHP spec!
      - PHPng will need this
      - released next week
      - Take that eevee!
      - will be living doc curated by php community

# Microsoft Azure and Microsoft Open Source
  - Scott Hanselman
  - Hillarious!
  - Works on Azure
    - 20 -25% of azuer linux
    - run linux vms on it
  - Azure
    - Three tiers
      - A site (read pantheon)
      - A pseudo vm (read docker)
      - A full vm 
      - Azure manages os on first two
  - C# and .net compiler open sourced
  - Azure itself open sourced
  - on freaking github
  - "Microsoft not organized enough to be as evil as you think it is"
  - New Visual Studio looks freaking incredible
    - Node.js Express in VS weird, I need a shower
    - grunt and bower coming soon
  - Cross browser in browser editing with SignalRo
    - Signal similar to websockets for .net 
  - despite rumors asp.net not responsible for banking crisis 
  - Microsoft slogan contest
    - remember us?
    - halo didn't suck...
 
# Mongodb and Go
  - Steve Francia
  - Concurrent on both ends
    - better throughput without flooding db
  - GridFS
    - not really a file system

# PHP 5.6
  - Adam Harvey
  - close to 4k commits since 5.5
  - a lot of first time commiters
  - Should be out Augustish
  - Variatic Functions
    - function foo(...$params) {
      - Now we have a params array
    - replaces call_user_func_array
    - faster by 30%
  - Constant Scalar Expressions
  - use function, use const
  - PHPDBG
    - xdebug replacement built into php
    - command line debugger
    - won't really work with Drupal 7, 8 maybe...
  - new config value default_charset
  - SSL / TLS ciphers fixed, perfect forward enabled by default if server supports
  - json_decode now matches spec for TRUE vs true < this the good one
  - Deprecations
    - $HTTP_RAW_POST_DATA
    - serialize hack removed that allowed you to skip calling constuctor
  - The Future
    - no new major version yet
    - next version likely 6
    - new versions are scary
    - python 2->3 BIG rewrite
      - prepared users well
      - adoption slow and maintaining 2 for a LONG time 
    - Ruby 1.9->2
      - small changes, non-event
    - PERL 5->6
      - massive failure
    - PHP 4->5
      - significant OO changes
    - PHP 5->6 "the unicode release"
      - dead in water
    - How should you do this?
      - Breaking chnages have to be well justified
      - Breaking changes default to rejected
    - PHPNG
      - Rewrite of Zend Engine
      - Competitor to HipHop
      - Start of next new version
    - Uniform Variable Syntax
      - First backword compatibility break

# You Don't Know How Computers Work
  - Matthew Garret
    - security dude
  - Computers
    - Deterministic -> mostly
    - Simple -> Complicated
    - Predictable -> Utterly unpredictable
    - Safe -> Liable to explode if provoked
  - Parts
    - CPU -> More like multiple CPUs
    - RAM -> And some hidden RAM (more executable code)
    - Storage
    - -> Maybe an entire different computer
  - System Management Mode
    - Thermal management, stops execution
    - Has a mind of its own
    - frequently msec at a time
  - Network Cards
    - AMT
      - steals ports 16992 - 16995
  - Lessons to take time
    - nobody understands computers completely
    - its just going to get worse
  - Security is incremental
    - at least SOMETHING is fixed

# Weds Keynote
  - Don't want to talk about security
    - Scary
    - Really hard math (libraries for that now)
  - Governments
    - Want back doors 
  - Civilization Good
    - Fight agains those who want to take that away
  - HTTPS
    - Go to legal ask them if its ok if everyone listens in on traffic, see what they say
  - PGP
    - Libraries exist, use them
  - Some solutions political some technical: do both
  - Paypal
    - Danese
    - Intersourcing
    - All source available within the company, if not outside <- see Google
  - Simon Wardley
    - Favorite Lie: We have a strategy 
    - Why: Small and Vague
    - 67& have social big data and cloud
      - hmm we should have that too
    - 1984 62 companies you should copy (Kodak, Atari)
    - Generals don't respond "67% of generals bombard hills"
    - Cloud computing book - 48 years ago
  - Leslie Hawthorn
    - Community Manager ElasticSearch
    - Check Your Privilege
      - bandaids as a systemic problem
      - can't see the default when its designed for you
      - #HTHT Experiments
        - Beginner level: active listening
        - Intermediate: Change Your Speech
          - may be uncomfortable for you
        - Advanced: Speak Up for Others
          - ok to pass, but think about doing it
