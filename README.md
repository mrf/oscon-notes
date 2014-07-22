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
