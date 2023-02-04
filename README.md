# apiutil
## What is does
This contains packages for common api utilities, based around golang echo servers. This includes
### Middleware
Yet to be implemented but want to add
- Rate limiting
- Auth + Cookie magic

### Router registering
Defines the interface RouteInterface so that anything that implements this can be used
in the function RegisterRoutes, which will run that method on the implemted struct,
this is useful for bulk registering controllers
```
type RouteInterface interface {
	Routes(g *echo.Group)
}

func RegisterRoutes(g *echo.Group, rr ...RouteInterface) { ... }
```

### Custom Error Handling
I've added a custom error handler, that uses `messages.GenericError`, this allows you to bubble 
errors of this type up to echo, which will then cast them to the relevant HTTP status code, and 
pass relevant conext. GenericError implements the Error interface, and errors should be raised
in this format in the lowest possible level of your application. This is still TBD if this approach
is nice or not. 

### Example usuage
This is used in my example API project over at [andyantrim/coreapi](https://github.com/andyantrim/coreapi)
