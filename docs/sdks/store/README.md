# Store
(*Store*)

## Overview

Access to Petstore orders

Find out more about our store
<http://swagger.io>

### Available Operations

* [GetInventory](#getinventory) - Returns pet inventories by status
* [PlaceOrder](#placeorder) - Place an order for a pet
* [GetOrderById](#getorderbyid) - Find purchase order by ID
* [DeleteOrder](#deleteorder) - Delete purchase order by ID

## GetInventory

Returns a map of status codes to quantities

### Example Usage

<!-- UsageSnippet language="csharp" operationID="getInventory" method="get" path="/store/inventory" -->
```csharp
using meepMoop;
using meepMoop.Models.Components;

var sdk = new Petstore(apiKey: "<YOUR_API_KEY_HERE>");

var res = await sdk.Store.GetInventoryAsync();

// handle response
```

### Response

**[GetInventoryResponse](../../Models/Requests/GetInventoryResponse.md)**

### Errors

| Error Type                                  | Status Code                                 | Content Type                                |
| ------------------------------------------- | ------------------------------------------- | ------------------------------------------- |
| meepMoop.Models.Errors.ApiErrorUnauthorized | 401                                         | application/json                            |
| meepMoop.Models.Errors.ApiErrorNotFound     | 404                                         | application/json                            |
| meepMoop.Models.Errors.APIException         | 4XX, 5XX                                    | \*/\*                                       |

## PlaceOrder

Place a new order in the store

### Example Usage

<!-- UsageSnippet language="csharp" operationID="placeOrder" method="post" path="/store/order" -->
```csharp
using meepMoop;
using meepMoop.Models.Components;

var sdk = new Petstore(apiKey: "<YOUR_API_KEY_HERE>");

Order req = new Order() {
    Id = 10,
    PetId = 198772,
    Quantity = 7,
    Status = OrderStatus.Approved,
};

var res = await sdk.Store.PlaceOrderAsync(req);

// handle response
```

### Parameters

| Parameter                                  | Type                                       | Required                                   | Description                                |
| ------------------------------------------ | ------------------------------------------ | ------------------------------------------ | ------------------------------------------ |
| `request`                                  | [Order](../../Models/Components/Order.md)  | :heavy_check_mark:                         | The request object to use for the request. |

### Response

**[PlaceOrderResponse](../../Models/Requests/PlaceOrderResponse.md)**

### Errors

| Error Type                                  | Status Code                                 | Content Type                                |
| ------------------------------------------- | ------------------------------------------- | ------------------------------------------- |
| meepMoop.Models.Errors.ApiErrorUnauthorized | 401                                         | application/json                            |
| meepMoop.Models.Errors.ApiErrorNotFound     | 404                                         | application/json                            |
| meepMoop.Models.Errors.APIException         | 4XX, 5XX                                    | \*/\*                                       |

## GetOrderById

For valid response try integer IDs with value <= 5 or > 10. Other values will generate exceptions.

### Example Usage

<!-- UsageSnippet language="csharp" operationID="getOrderById" method="get" path="/store/order/{orderId}" -->
```csharp
using meepMoop;
using meepMoop.Models.Components;

var sdk = new Petstore(apiKey: "<YOUR_API_KEY_HERE>");

var res = await sdk.Store.GetOrderByIdAsync(orderId: 728529);

// handle response
```

### Parameters

| Parameter                            | Type                                 | Required                             | Description                          |
| ------------------------------------ | ------------------------------------ | ------------------------------------ | ------------------------------------ |
| `OrderId`                            | *long*                               | :heavy_check_mark:                   | ID of order that needs to be fetched |

### Response

**[GetOrderByIdResponse](../../Models/Requests/GetOrderByIdResponse.md)**

### Errors

| Error Type                                  | Status Code                                 | Content Type                                |
| ------------------------------------------- | ------------------------------------------- | ------------------------------------------- |
| meepMoop.Models.Errors.ApiErrorInvalidInput | 400                                         | application/json                            |
| meepMoop.Models.Errors.ApiErrorUnauthorized | 401                                         | application/json                            |
| meepMoop.Models.Errors.ApiErrorNotFound     | 404                                         | application/json                            |
| meepMoop.Models.Errors.APIException         | 4XX, 5XX                                    | \*/\*                                       |

## DeleteOrder

For valid response try integer IDs with value < 1000. Anything above 1000 or nonintegers will generate API errors

### Example Usage

<!-- UsageSnippet language="csharp" operationID="deleteOrder" method="delete" path="/store/order/{orderId}" -->
```csharp
using meepMoop;
using meepMoop.Models.Components;

var sdk = new Petstore(apiKey: "<YOUR_API_KEY_HERE>");

var res = await sdk.Store.DeleteOrderAsync(orderId: 690575);

// handle response
```

### Parameters

| Parameter                                | Type                                     | Required                                 | Description                              |
| ---------------------------------------- | ---------------------------------------- | ---------------------------------------- | ---------------------------------------- |
| `OrderId`                                | *long*                                   | :heavy_check_mark:                       | ID of the order that needs to be deleted |

### Response

**[DeleteOrderResponse](../../Models/Requests/DeleteOrderResponse.md)**

### Errors

| Error Type                                  | Status Code                                 | Content Type                                |
| ------------------------------------------- | ------------------------------------------- | ------------------------------------------- |
| meepMoop.Models.Errors.ApiErrorInvalidInput | 400                                         | application/json                            |
| meepMoop.Models.Errors.ApiErrorUnauthorized | 401                                         | application/json                            |
| meepMoop.Models.Errors.ApiErrorNotFound     | 404                                         | application/json                            |
| meepMoop.Models.Errors.APIException         | 4XX, 5XX                                    | \*/\*                                       |