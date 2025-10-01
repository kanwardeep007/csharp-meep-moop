# meepMoop


<!-- Start SDK Example Usage [usage] -->
## SDK Example Usage

### Example

```csharp
using System.Collections.Generic;
using meepMoop;
using meepMoop.Models.Components;

var sdk = new Petstore(apiKey: "<YOUR_API_KEY_HERE>");

Models.Components.Pet req = new meepMoop.Models.Components.Pet() {
    Id = 10,
    Name = "doggie",
    Category = new Category() {
        Id = 1,
        Name = "Dogs",
    },
    PhotoUrls = new List<string>() {
        "<value 1>",
    },
};

var res = await sdk.Pet.UpdatePetAsync(req);

// handle response
```
<!-- End SDK Example Usage [usage] -->

<!-- Start Authentication [security] -->
## Authentication

### Per-Client Security Schemes

This SDK supports the following security scheme globally:

| Name     | Type   | Scheme  |
| -------- | ------ | ------- |
| `ApiKey` | apiKey | API key |

To authenticate with the API the `ApiKey` parameter must be set when initializing the SDK client instance. For example:
```csharp
using System.Collections.Generic;
using meepMoop;
using meepMoop.Models.Components;

var sdk = new Petstore(apiKey: "<YOUR_API_KEY_HERE>");

Models.Components.Pet req = new meepMoop.Models.Components.Pet() {
    Id = 10,
    Name = "doggie",
    Category = new Category() {
        Id = 1,
        Name = "Dogs",
    },
    PhotoUrls = new List<string>() {
        "<value 1>",
    },
};

var res = await sdk.Pet.UpdatePetAsync(req);

// handle response
```
<!-- End Authentication [security] -->

<!-- Start Error Handling [errors] -->
## Error Handling

[`PetstoreException`](./src/meepMoop/Models/Errors/PetstoreException.cs) is the base exception class for all HTTP error responses. It has the following properties:

| Property      | Type                  | Description           |
|---------------|-----------------------|-----------------------|
| `Message`     | *string*              | Error message         |
| `Request`     | *HttpRequestMessage*  | HTTP request object   |
| `Response`    | *HttpResponseMessage* | HTTP response object  |

Some exceptions in this SDK include an additional `Payload` field, which will contain deserialized custom error data when present. Possible exceptions are listed in the [Error Classes](#error-classes) section.

### Example

```csharp
using System.Collections.Generic;
using meepMoop;
using meepMoop.Models.Components;
using meepMoop.Models.Errors;

var sdk = new Petstore(apiKey: "<YOUR_API_KEY_HERE>");

try
{
    Models.Components.Pet req = new meepMoop.Models.Components.Pet() {
        Id = 10,
        Name = "doggie",
        Category = new Category() {
            Id = 1,
            Name = "Dogs",
        },
        PhotoUrls = new List<string>() {
            "<value 1>",
        },
    };

    var res = await sdk.Pet.UpdatePetAsync(req);

    // handle response
}
catch (PetstoreException ex)  // all SDK exceptions inherit from PetstoreException
{
    // ex.ToString() provides a detailed error message
    System.Console.WriteLine(ex);

    // Base exception fields
    HttpRequestMessage request = ex.Request;
    HttpResponseMessage response = ex.Response;
    var statusCode = (int)response.StatusCode;
    var responseBody = ex.Body;

    if (ex is ApiErrorInvalidInput) // different exceptions may be thrown depending on the method
    {
        // Check error data fields
        ApiErrorInvalidInputPayload payload = ex.Payload;
        int Status = payload.Status;
        string Error = payload.Error;
        // ...
    }

    // An underlying cause may be provided
    if (ex.InnerException != null)
    {
        Exception cause = ex.InnerException;
    }
}
catch (System.Net.Http.HttpRequestException ex)
{
    // Check ex.InnerException for Network connectivity errors
}
```

### Error Classes

**Primary exception:**
* [`PetstoreException`](./src/meepMoop/Models/Errors/PetstoreException.cs): The base class for HTTP error responses.

<details><summary>Less common exceptions (5)</summary>

* [`System.Net.Http.HttpRequestException`](https://learn.microsoft.com/en-us/dotnet/api/system.net.http.httprequestexception): Network connectivity error. For more details about the underlying cause, inspect the `ex.InnerException`.

* Inheriting from [`PetstoreException`](./src/meepMoop/Models/Errors/PetstoreException.cs):
  * [`ApiErrorUnauthorized`](./src/meepMoop/Models/Errors/ApiErrorUnauthorized.cs): Unauthorized error. Status code `401`. Applicable to 12 of 18 methods.*
  * [`ApiErrorNotFound`](./src/meepMoop/Models/Errors/ApiErrorNotFound.cs): Not Found error. Status code `404`. Applicable to 12 of 18 methods.*
  * [`ApiErrorInvalidInput`](./src/meepMoop/Models/Errors/ApiErrorInvalidInput.cs): Not Found error. Status code `400`. Applicable to 10 of 18 methods.*
  * [`ResponseValidationError`](./src/meepMoop/Models/Errors/ResponseValidationError.cs): Thrown when the response data could not be deserialized into the expected type.
</details>

\* Refer to the [relevant documentation](#available-resources-and-operations) to determine whether an exception applies to a specific operation.
<!-- End Error Handling [errors] -->

<!-- Start Server Selection [server] -->
## Server Selection

### Server Variables

The default server `https://{environment}.petstore.io` contains variables and is set to `https://prod.petstore.io` by default. To override default values, the following parameters are available when initializing the SDK client instance:

| Variable      | Parameter                                        | Supported Values                           | Default  | Description                                                   |
| ------------- | ------------------------------------------------ | ------------------------------------------ | -------- | ------------------------------------------------------------- |
| `environment` | `environment: meepMoop.Models.ServerEnvironment` | - `"prod"`<br/>- `"staging"`<br/>- `"dev"` | `"prod"` | The environment name. Defaults to the production environment. |

#### Example

```csharp
using System.Collections.Generic;
using meepMoop;
using meepMoop.Models.Components;

var sdk = new Petstore(
    environment: "dev",
    apiKey: "<YOUR_API_KEY_HERE>"
);

Models.Components.Pet req = new meepMoop.Models.Components.Pet() {
    Id = 10,
    Name = "doggie",
    Category = new Category() {
        Id = 1,
        Name = "Dogs",
    },
    PhotoUrls = new List<string>() {
        "<value 1>",
    },
};

var res = await sdk.Pet.UpdatePetAsync(req);

// handle response
```

### Override Server URL Per-Client

The default server can be overridden globally by passing a URL to the `serverUrl: string` optional parameter when initializing the SDK client instance. For example:
```csharp
using System.Collections.Generic;
using meepMoop;
using meepMoop.Models.Components;

var sdk = new Petstore(
    serverUrl: "https://prod.petstore.io",
    apiKey: "<YOUR_API_KEY_HERE>"
);

Models.Components.Pet req = new meepMoop.Models.Components.Pet() {
    Id = 10,
    Name = "doggie",
    Category = new Category() {
        Id = 1,
        Name = "Dogs",
    },
    PhotoUrls = new List<string>() {
        "<value 1>",
    },
};

var res = await sdk.Pet.UpdatePetAsync(req);

// handle response
```
<!-- End Server Selection [server] -->

<!-- Placeholder for Future Speakeasy SDK Sections -->