# User
(*User*)

## Overview

Operations about user

### Available Operations

* [CreateUser](#createuser) - Create user
* [CreateUsersWithListInput](#createuserswithlistinput) - Creates list of users with given input array
* [LogoutUser](#logoutuser) - Logs out current logged in user session
* [GetUserByName](#getuserbyname) - Get user by user name
* [UpdateUser](#updateuser) - Update user
* [DeleteUser](#deleteuser) - Delete user

## CreateUser

This can only be done by the logged in user.

### Example Usage

<!-- UsageSnippet language="csharp" operationID="createUser" method="post" path="/user" -->
```csharp
using meepMoop;
using meepMoop.Models.Components;

var sdk = new Petstore(apiKey: "<YOUR_API_KEY_HERE>");

Models.Components.User req = new meepMoop.Models.Components.User() {
    Id = 10,
    Username = "theUser",
    FirstName = "John",
    LastName = "James",
    Email = "john@email.com",
    Password = "12345",
    Phone = "12345",
    UserStatus = 1,
};

var res = await sdk.User.CreateUserAsync(req);

// handle response
```

### Parameters

| Parameter                                                 | Type                                                      | Required                                                  | Description                                               |
| --------------------------------------------------------- | --------------------------------------------------------- | --------------------------------------------------------- | --------------------------------------------------------- |
| `request`                                                 | [Models.Components.User](../../Models/Components/User.md) | :heavy_check_mark:                                        | The request object to use for the request.                |

### Response

**[CreateUserResponse](../../Models/Requests/CreateUserResponse.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| meepMoop.Models.Errors.APIException | 4XX, 5XX                            | \*/\*                               |

## CreateUsersWithListInput

Creates list of users with given input array

### Example Usage

<!-- UsageSnippet language="csharp" operationID="createUsersWithListInput" method="post" path="/user/createWithList" -->
```csharp
using System.Collections.Generic;
using meepMoop;
using meepMoop.Models.Components;

var sdk = new Petstore(apiKey: "<YOUR_API_KEY_HERE>");

List<Models.Components.User> req = new List<meepMoop.Models.Components.User>() {
    new meepMoop.Models.Components.User() {
        Id = 10,
        Username = "theUser",
        FirstName = "John",
        LastName = "James",
        Email = "john@email.com",
        Password = "12345",
        Phone = "12345",
        UserStatus = 1,
    },
};

var res = await sdk.User.CreateUsersWithListInputAsync(req);

// handle response
```

### Parameters

| Parameter                                                       | Type                                                            | Required                                                        | Description                                                     |
| --------------------------------------------------------------- | --------------------------------------------------------------- | --------------------------------------------------------------- | --------------------------------------------------------------- |
| `request`                                                       | List<[Models.Components.User](../../Models/Components/User.md)> | :heavy_check_mark:                                              | The request object to use for the request.                      |

### Response

**[CreateUsersWithListInputResponse](../../Models/Requests/CreateUsersWithListInputResponse.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| meepMoop.Models.Errors.APIException | 4XX, 5XX                            | \*/\*                               |

## LogoutUser

Logs out current logged in user session

### Example Usage

<!-- UsageSnippet language="csharp" operationID="logoutUser" method="get" path="/user/logout" -->
```csharp
using meepMoop;
using meepMoop.Models.Components;

var sdk = new Petstore(apiKey: "<YOUR_API_KEY_HERE>");

var res = await sdk.User.LogoutUserAsync();

// handle response
```

### Response

**[LogoutUserResponse](../../Models/Requests/LogoutUserResponse.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| meepMoop.Models.Errors.APIException | 4XX, 5XX                            | \*/\*                               |

## GetUserByName

Get user by user name

### Example Usage

<!-- UsageSnippet language="csharp" operationID="getUserByName" method="get" path="/user/{username}" -->
```csharp
using meepMoop;
using meepMoop.Models.Components;

var sdk = new Petstore(apiKey: "<YOUR_API_KEY_HERE>");

var res = await sdk.User.GetUserByNameAsync(username: "Edyth10");

// handle response
```

### Parameters

| Parameter                                                  | Type                                                       | Required                                                   | Description                                                |
| ---------------------------------------------------------- | ---------------------------------------------------------- | ---------------------------------------------------------- | ---------------------------------------------------------- |
| `Username`                                                 | *string*                                                   | :heavy_check_mark:                                         | The name that needs to be fetched. Use user1 for testing.  |

### Response

**[GetUserByNameResponse](../../Models/Requests/GetUserByNameResponse.md)**

### Errors

| Error Type                                  | Status Code                                 | Content Type                                |
| ------------------------------------------- | ------------------------------------------- | ------------------------------------------- |
| meepMoop.Models.Errors.ApiErrorInvalidInput | 400                                         | application/json                            |
| meepMoop.Models.Errors.ApiErrorUnauthorized | 401                                         | application/json                            |
| meepMoop.Models.Errors.ApiErrorNotFound     | 404                                         | application/json                            |
| meepMoop.Models.Errors.APIException         | 4XX, 5XX                                    | \*/\*                                       |

## UpdateUser

This can only be done by the logged in user.

### Example Usage

<!-- UsageSnippet language="csharp" operationID="updateUser" method="put" path="/user/{username}" -->
```csharp
using meepMoop;
using meepMoop.Models.Components;

var sdk = new Petstore(apiKey: "<YOUR_API_KEY_HERE>");

var res = await sdk.User.UpdateUserAsync(
    username: "Alison.Cassin",
    user: new meepMoop.Models.Components.User() {
        Id = 10,
        Username = "theUser",
        FirstName = "John",
        LastName = "James",
        Email = "john@email.com",
        Password = "12345",
        Phone = "12345",
        UserStatus = 1,
    }
);

// handle response
```

### Parameters

| Parameter                                                 | Type                                                      | Required                                                  | Description                                               |
| --------------------------------------------------------- | --------------------------------------------------------- | --------------------------------------------------------- | --------------------------------------------------------- |
| `Username`                                                | *string*                                                  | :heavy_check_mark:                                        | name that needs to be updated                             |
| `User`                                                    | [Models.Components.User](../../Models/Components/User.md) | :heavy_minus_sign:                                        | Update an existent user in the store                      |

### Response

**[UpdateUserResponse](../../Models/Requests/UpdateUserResponse.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| meepMoop.Models.Errors.APIException | 4XX, 5XX                            | \*/\*                               |

## DeleteUser

This can only be done by the logged in user.

### Example Usage

<!-- UsageSnippet language="csharp" operationID="deleteUser" method="delete" path="/user/{username}" -->
```csharp
using meepMoop;
using meepMoop.Models.Components;

var sdk = new Petstore(apiKey: "<YOUR_API_KEY_HERE>");

var res = await sdk.User.DeleteUserAsync(username: "Rita_Schuppe");

// handle response
```

### Parameters

| Parameter                         | Type                              | Required                          | Description                       |
| --------------------------------- | --------------------------------- | --------------------------------- | --------------------------------- |
| `Username`                        | *string*                          | :heavy_check_mark:                | The name that needs to be deleted |

### Response

**[DeleteUserResponse](../../Models/Requests/DeleteUserResponse.md)**

### Errors

| Error Type                                  | Status Code                                 | Content Type                                |
| ------------------------------------------- | ------------------------------------------- | ------------------------------------------- |
| meepMoop.Models.Errors.ApiErrorInvalidInput | 400                                         | application/json                            |
| meepMoop.Models.Errors.ApiErrorUnauthorized | 401                                         | application/json                            |
| meepMoop.Models.Errors.ApiErrorNotFound     | 404                                         | application/json                            |
| meepMoop.Models.Errors.APIException         | 4XX, 5XX                                    | \*/\*                                       |