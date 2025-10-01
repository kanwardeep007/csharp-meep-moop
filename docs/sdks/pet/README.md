# Pet
(*Pet*)

## Overview

Everything about your Pets

Find out more
<http://swagger.io>

### Available Operations

* [UpdatePet](#updatepet) - Update an existing pet
* [AddPet](#addpet) - Add a new pet to the store
* [FindPetsByStatus](#findpetsbystatus) - Finds Pets by status
* [FindPetsByTags](#findpetsbytags) - Finds Pets by tags
* [GetPetById](#getpetbyid) - Find pet by ID
* [DeletePet](#deletepet) - Deletes a pet
* [UploadFile](#uploadfile) - uploads an image

## UpdatePet

Update an existing pet by Id

### Example Usage

<!-- UsageSnippet language="csharp" operationID="updatePet" method="put" path="/pet" -->
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

### Parameters

| Parameter                                               | Type                                                    | Required                                                | Description                                             |
| ------------------------------------------------------- | ------------------------------------------------------- | ------------------------------------------------------- | ------------------------------------------------------- |
| `request`                                               | [Models.Components.Pet](../../Models/Components/Pet.md) | :heavy_check_mark:                                      | The request object to use for the request.              |

### Response

**[UpdatePetResponse](../../Models/Requests/UpdatePetResponse.md)**

### Errors

| Error Type                                  | Status Code                                 | Content Type                                |
| ------------------------------------------- | ------------------------------------------- | ------------------------------------------- |
| meepMoop.Models.Errors.ApiErrorInvalidInput | 400                                         | application/json                            |
| meepMoop.Models.Errors.ApiErrorUnauthorized | 401                                         | application/json                            |
| meepMoop.Models.Errors.ApiErrorNotFound     | 404                                         | application/json                            |
| meepMoop.Models.Errors.APIException         | 4XX, 5XX                                    | \*/\*                                       |

## AddPet

Add a new pet to the store

### Example Usage

<!-- UsageSnippet language="csharp" operationID="addPet" method="post" path="/pet" -->
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
        "<value 2>",
        "<value 3>",
    },
};

var res = await sdk.Pet.AddPetAsync(req);

// handle response
```

### Parameters

| Parameter                                               | Type                                                    | Required                                                | Description                                             |
| ------------------------------------------------------- | ------------------------------------------------------- | ------------------------------------------------------- | ------------------------------------------------------- |
| `request`                                               | [Models.Components.Pet](../../Models/Components/Pet.md) | :heavy_check_mark:                                      | The request object to use for the request.              |

### Response

**[AddPetResponse](../../Models/Requests/AddPetResponse.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| meepMoop.Models.Errors.APIException | 4XX, 5XX                            | \*/\*                               |

## FindPetsByStatus

Multiple status values can be provided with comma separated strings

### Example Usage

<!-- UsageSnippet language="csharp" operationID="findPetsByStatus" method="get" path="/pet/findByStatus" -->
```csharp
using meepMoop;
using meepMoop.Models.Components;
using meepMoop.Models.Requests;

var sdk = new Petstore(apiKey: "<YOUR_API_KEY_HERE>");

var res = await sdk.Pet.FindPetsByStatusAsync(status: Status.Available);

// handle response
```

### Parameters

| Parameter                                           | Type                                                | Required                                            | Description                                         |
| --------------------------------------------------- | --------------------------------------------------- | --------------------------------------------------- | --------------------------------------------------- |
| `Status`                                            | [Status](../../Models/Requests/Status.md)           | :heavy_minus_sign:                                  | Status values that need to be considered for filter |

### Response

**[FindPetsByStatusResponse](../../Models/Requests/FindPetsByStatusResponse.md)**

### Errors

| Error Type                                  | Status Code                                 | Content Type                                |
| ------------------------------------------- | ------------------------------------------- | ------------------------------------------- |
| meepMoop.Models.Errors.ApiErrorInvalidInput | 400                                         | application/json                            |
| meepMoop.Models.Errors.ApiErrorUnauthorized | 401                                         | application/json                            |
| meepMoop.Models.Errors.ApiErrorNotFound     | 404                                         | application/json                            |
| meepMoop.Models.Errors.APIException         | 4XX, 5XX                                    | \*/\*                                       |

## FindPetsByTags

Multiple tags can be provided with comma separated strings. Use tag1, tag2, tag3 for testing.

### Example Usage

<!-- UsageSnippet language="csharp" operationID="findPetsByTags" method="get" path="/pet/findByTags" -->
```csharp
using meepMoop;
using meepMoop.Models.Components;

var sdk = new Petstore(apiKey: "<YOUR_API_KEY_HERE>");

var res = await sdk.Pet.FindPetsByTagsAsync();

// handle response
```

### Parameters

| Parameter          | Type               | Required           | Description        |
| ------------------ | ------------------ | ------------------ | ------------------ |
| `Tags`             | List<*string*>     | :heavy_minus_sign: | Tags to filter by  |

### Response

**[FindPetsByTagsResponse](../../Models/Requests/FindPetsByTagsResponse.md)**

### Errors

| Error Type                                  | Status Code                                 | Content Type                                |
| ------------------------------------------- | ------------------------------------------- | ------------------------------------------- |
| meepMoop.Models.Errors.ApiErrorInvalidInput | 400                                         | application/json                            |
| meepMoop.Models.Errors.ApiErrorUnauthorized | 401                                         | application/json                            |
| meepMoop.Models.Errors.ApiErrorNotFound     | 404                                         | application/json                            |
| meepMoop.Models.Errors.APIException         | 4XX, 5XX                                    | \*/\*                                       |

## GetPetById

Returns a single pet

### Example Usage

<!-- UsageSnippet language="csharp" operationID="getPetById" method="get" path="/pet/{petId}" -->
```csharp
using meepMoop;
using meepMoop.Models.Components;

var sdk = new Petstore(apiKey: "<YOUR_API_KEY_HERE>");

var res = await sdk.Pet.GetPetByIdAsync(petId: 311674);

// handle response
```

### Parameters

| Parameter           | Type                | Required            | Description         |
| ------------------- | ------------------- | ------------------- | ------------------- |
| `PetId`             | *long*              | :heavy_check_mark:  | ID of pet to return |

### Response

**[GetPetByIdResponse](../../Models/Requests/GetPetByIdResponse.md)**

### Errors

| Error Type                                  | Status Code                                 | Content Type                                |
| ------------------------------------------- | ------------------------------------------- | ------------------------------------------- |
| meepMoop.Models.Errors.ApiErrorInvalidInput | 400                                         | application/json                            |
| meepMoop.Models.Errors.ApiErrorUnauthorized | 401                                         | application/json                            |
| meepMoop.Models.Errors.ApiErrorNotFound     | 404                                         | application/json                            |
| meepMoop.Models.Errors.APIException         | 4XX, 5XX                                    | \*/\*                                       |

## DeletePet

Deletes a pet

### Example Usage

<!-- UsageSnippet language="csharp" operationID="deletePet" method="delete" path="/pet/{petId}" -->
```csharp
using meepMoop;
using meepMoop.Models.Components;

var sdk = new Petstore(apiKey: "<YOUR_API_KEY_HERE>");

var res = await sdk.Pet.DeletePetAsync(petId: 818965);

// handle response
```

### Parameters

| Parameter          | Type               | Required           | Description        |
| ------------------ | ------------------ | ------------------ | ------------------ |
| `PetId`            | *long*             | :heavy_check_mark: | Pet id to delete   |
| `ApiKey`           | *string*           | :heavy_minus_sign: | N/A                |

### Response

**[DeletePetResponse](../../Models/Requests/DeletePetResponse.md)**

### Errors

| Error Type                                  | Status Code                                 | Content Type                                |
| ------------------------------------------- | ------------------------------------------- | ------------------------------------------- |
| meepMoop.Models.Errors.ApiErrorInvalidInput | 400                                         | application/json                            |
| meepMoop.Models.Errors.ApiErrorUnauthorized | 401                                         | application/json                            |
| meepMoop.Models.Errors.ApiErrorNotFound     | 404                                         | application/json                            |
| meepMoop.Models.Errors.APIException         | 4XX, 5XX                                    | \*/\*                                       |

## UploadFile

uploads an image

### Example Usage

<!-- UsageSnippet language="csharp" operationID="uploadFile" method="post" path="/pet/{petId}/uploadImage" -->
```csharp
using meepMoop;
using meepMoop.Models.Components;

var sdk = new Petstore(apiKey: "<YOUR_API_KEY_HERE>");

var res = await sdk.Pet.UploadFileAsync(petId: 150516);

// handle response
```

### Parameters

| Parameter            | Type                 | Required             | Description          |
| -------------------- | -------------------- | -------------------- | -------------------- |
| `PetId`              | *long*               | :heavy_check_mark:   | ID of pet to update  |
| `AdditionalMetadata` | *string*             | :heavy_minus_sign:   | Additional Metadata  |
| `RequestBody`        | *byte[]*             | :heavy_minus_sign:   | N/A                  |

### Response

**[UploadFileResponse](../../Models/Requests/UploadFileResponse.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| meepMoop.Models.Errors.APIException | 4XX, 5XX                            | \*/\*                               |