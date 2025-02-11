revmgo
======
mgo module for revel framework

This is a **mantained** fork of https://github.com/jgraham909/revmgo.

### Installation
``` bash
    go get github.com/AidenHowell/revmgo
```
### Test
``` bash
    revel test github.com/AidenHowell/revmgo/testapp dev
```
### Configuration
In app.conf:
- **revmgo.dial** = [mgo.Session.Dial()](http://godoc.org/gopkg.in/mgo.v2#Dial)
- **revmgo.method** = One of 'clone', 'copy', 'new'. See [mgo.Session.New()](http://godoc.org/gopkg.in/mgo.v2#Session.New)

### Initialization
- In app.init() in `app/init.go` add:
``` go
    revel.OnAppStart(revmgo.AppInit)
```

- In controllers.init() in `app/controllers/init.go` add
``` go
    revmgo.ControllerInit()
```
So a minimal controller's init() would be:

``` go
    package controllers

    import "github.com/AidenHowell/revmgo"

    func init() {
        revmgo.ControllerInit()
    }
```

### Usage
Embed the MongoController on your custom controller;
``` go
    package controllers

    import (
        "github.com/AidenHowell/revmgo"
        "github.com/revel/revel"
    )

    type App struct {
        *revel.Controller
        revmgo.MongoController
  		// ...
  	}
```
The controller will now have a MongoSession variable of type `*mgo.Session`. Use this to query your mongo datastore.

### See Also

*  https://godoc.org/gopkg.in/mgo.v2 for documentation on the mgo driver


