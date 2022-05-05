# [dillinger](https://dillinger.io/)

## my *note* from dillinger markdown editors

[Bliss OS Install on Mac OS](https://docs.blissos.org/install-bliss-os/install-on-mac-os)

[Heroku Go]()
```
$ git clone https://github.com/heroku/go-getting-started.git
$ cd go-getting-started
```
* Deploy App
```
$ heroku create
Creating polar-inlet-4930... done, stack is heroku-18
https://polar-inlet-4930.herokuapp.com/ | https://git.heroku.com/polar-inlet-4930.git
Git remote heroku added
```
* Deploy code
```
$ git push heroku main
```
* Open
```
$ heroku open
```
* View log
```
$ heroku logs --tail
```
* Define  Procfile
```
web: bin/go-getting-started
```
 *bin/go-getting-started* is the compiled binary of the getting started app. The build process installs compiled binaries into the dyno’s *~/bin* directory.
 
### Scale the app
Right now, your app is running on a *single web dyno*. Think of a *dyno* as a lightweight container that runs the command specified in the *Procfile*.
```
$ heroku ps
=== web (Free): `go-getting-started`
web.1: up 2015/05/12 11:28:21 (~ 4m ago)
```
Scaling an application on Heroku is equivalent to changing the number of dynos that are running. Scale the number of web dynos to zero:
```
heroku ps:scale web=0
```
Scale it up again:
```
heroku ps:scale web=1
```
The demo app you deployed already has a go.mod file, and it looks something like this:
```
$ cat go.mod
module github.com/heroku/go-getting-started
```
When an app is deployed, Heroku reads this file, installs an appropriate Go version and compiles your code using ```go install ..```
### Run the app locally

Running apps locally in your own dev environment requires a little more effort. Go is a compiled language and you must first compile the application:
```
$ go build -o bin/go-getting-started -v .
```