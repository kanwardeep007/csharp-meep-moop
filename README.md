# meepMoop

Developer-friendly & type-safe Csharp SDK specifically catered to leverage *meepMoop* API.

<div align="left">
    <a href="https://www.speakeasy.com/?utm_source=meep-moop&utm_campaign=csharp"><img src="https://www.speakeasy.com/assets/badges/built-by-speakeasy.svg" /></a>
    <a href="https://opensource.org/licenses/MIT">
        <img src="https://img.shields.io/badge/License-MIT-blue.svg" style="width: 100px; height: 28px;" />
    </a>
</div>


<br /><br />
> [!IMPORTANT]
> This SDK is not yet ready for production use. To complete setup please follow the steps outlined in your [workspace](https://app.speakeasy.com/org/gdmtesting/petstore). Delete this section before > publishing to a package manager.

<!-- Start Summary [summary] -->
## Summary

Petstore - OpenAPI 3.1: This is a sample Pet Store Server based on the OpenAPI 3.1 specification.

Some useful links:
- [OpenAPI Reference](https://www.speakeasy.com/openapi)
- [The Pet Store repository](https://github.com/swagger-api/swagger-petstore)
- [The source API definition for the Pet Store](https://github.com/swagger-api/swagger-petstore/blob/master/src/main/resources/openapi.yaml)

For more information about the API: [Find out more about Swagger](http://swagger.io)
<!-- End Summary [summary] -->

<!-- Start Table of Contents [toc] -->
## Table of Contents
<!-- $toc-max-depth=2 -->
* [meepMoop](#meepmoop)
  * [SDK Installation](#sdk-installation)
  * [SDK Example Usage](#sdk-example-usage)
  * [Authentication](#authentication)
  * [Available Resources and Operations](#available-resources-and-operations)
  * [Error Handling](#error-handling)
  * [Server Selection](#server-selection)
* [Development](#development)
  * [Maturity](#maturity)
  * [Contributions](#contributions)

<!-- End Table of Contents [toc] -->

<!-- Start SDK Installation [installation] -->
## SDK Installation

To add a reference to a local instance of the SDK in a .NET project:
```bash
dotnet add reference src/meepMoop/meepMoop.csproj
```
<!-- End SDK Installation [installation] -->

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

<!-- Start Available Resources and Operations [operations] -->
## Available Resources and Operations

<details open>
<summary>Available methods</summary>

### [Pet](docs/sdks/pet/README.md)

* [UpdatePet](docs/sdks/pet/README.md#updatepet) - Update an existing pet
* [AddPet](docs/sdks/pet/README.md#addpet) - Add a new pet to the store
* [FindPetsByStatus](docs/sdks/pet/README.md#findpetsbystatus) - Finds Pets by status
* [FindPetsByTags](docs/sdks/pet/README.md#findpetsbytags) - Finds Pets by tags
* [GetPetById](docs/sdks/pet/README.md#getpetbyid) - Find pet by ID
* [DeletePet](docs/sdks/pet/README.md#deletepet) - Deletes a pet
* [UploadFile](docs/sdks/pet/README.md#uploadfile) - uploads an image


### [Store](docs/sdks/store/README.md)

* [GetInventory](docs/sdks/store/README.md#getinventory) - Returns pet inventories by status
* [PlaceOrder](docs/sdks/store/README.md#placeorder) - Place an order for a pet
* [GetOrderById](docs/sdks/store/README.md#getorderbyid) - Find purchase order by ID
* [DeleteOrder](docs/sdks/store/README.md#deleteorder) - Delete purchase order by ID

### [User](docs/sdks/user/README.md)

* [CreateUser](docs/sdks/user/README.md#createuser) - Create user
* [CreateUsersWithListInput](docs/sdks/user/README.md#createuserswithlistinput) - Creates list of users with given input array
* [LoginUser](docs/sdks/user/README.md#loginuser) - Logs user into the system
* [LogoutUser](docs/sdks/user/README.md#logoutuser) - Logs out current logged in user session
* [GetUserByName](docs/sdks/user/README.md#getuserbyname) - Get user by user name
* [UpdateUser](docs/sdks/user/README.md#updateuser) - Update user
* [DeleteUser](docs/sdks/user/README.md#deleteuser) - Delete user

</details>
<!-- End Available Resources and Operations [operations] -->

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

# Development

## Maturity

This SDK is in beta, and there may be breaking changes between versions without a major version update. Therefore, we recommend pinning usage
to a specific package version. This way, you can install the same version each time without breaking changes unless you are intentionally
looking for the latest version.

## Contributions

While we value open-source contributions to this SDK, this library is generated programmatically. Any manual changes added to internal files will be overwritten on the next generation. 
We look forward to hearing your feedback. Feel free to open a PR or an issue with a proof of concept and we'll do our best to include it in a future release. 

### SDK Created by [Speakeasy](https://www.speakeasy.com/?utm_source=meep-moop&utm_campaign=csharp)
