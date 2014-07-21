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
