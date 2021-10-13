# endpoint options
in addition to the convenient methods you can use in the constructor to define your endpoints (mentioned in previous pages), you can use the `Options()` method to customize aspects of endpoint registration like so:
```csharp
Options(b => b.RequireCors(x => x.AllowAnyOrigin())
              .RequireHost("https://somedomain.com")
              .ProducesProblem(404));
```

# endpoint properties
the following properties are available to all endpoint classes.

#### BaseURL (string)
the base url of the current request in the form of `https://hostname:port/` (includes trailing slash).

#### Config (IConfiguration)
gives access to current configuration of the web app

#### Env (IWebHostEnvironment)
gives access to the current web hosting environment

#### Files (IFormFileCollection)
exposes the uploaded file collection in case of `multipart/form-data` uploads.

#### Form (IFormCollection)
exposes the form data in case of `application/x-www-form-urlencoded` or `multipart/form-data` uploads.

#### HttpContext (HttpContext)
gives access to the current http context of the request.

#### HttpMethod (Http enum value)
the http method of the current request as an enum value.

#### Logger (ILogger)
the default logger for the current endpoint type

#### Response (TResponse)
exposes a blank response dto for the current endpoint before the endpoint handler is executed. or represents the populated response dto after a response has been sent to the client.

#### User (ClaimsPrincipal)
the current claims principal associated with the current request.

#### ValidationFailed (bool)
indicates the current validation status

#### ValidationFailures (List<ValidationFailure>)
the list of validation failures for the current execution context.

# send methods
the following response sending methods are available for use from within endpoint handlers:

#### SendAsync()
sends a given response dto or any object that can be serialized as json down to the requesting client.

#### SendOkAsync()
sends a 200 ok response without any body.

#### SendErrorsAsync()
sends a 400 error response with the current list of validation errors describing the validation failures.

#### SendNoContentAsync()
sends a 204 no content response

#### SendNotFoundAsync()
sends a 404 not found response

#### SendUnauthorizedAsync()
sends a 401 unauthorized response

#### SendForbiddenAsync()
sends a 403 unauthorized response