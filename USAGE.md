<!-- Start SDK Example Usage [usage] -->
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