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
    - Code functionality
  - Ops guy worries aobut outsides
    - Logging

- Docker Registry stores config "think Features server"
  - Download once, get changes from server
  - No need to move around the whole container once deployed

- Written in Go

- For OSX and Windows we hav Boot2Docker

- Architecture
  - Single client/server binary
    - recieves / sends Docker api requests
  - Docker hub registry
