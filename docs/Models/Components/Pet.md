# Pet


## Fields

| Field                                             | Type                                              | Required                                          | Description                                       | Example                                           |
| ------------------------------------------------- | ------------------------------------------------- | ------------------------------------------------- | ------------------------------------------------- | ------------------------------------------------- |
| `Id`                                              | *long*                                            | :heavy_minus_sign:                                | N/A                                               | 10                                                |
| `Name`                                            | *string*                                          | :heavy_check_mark:                                | N/A                                               | doggie                                            |
| `Category`                                        | [Category](../../Models/Components/Category.md)   | :heavy_minus_sign:                                | N/A                                               |                                                   |
| `PhotoUrls`                                       | List<*string*>                                    | :heavy_check_mark:                                | N/A                                               |                                                   |
| `Tags`                                            | List<[Tag](../../Models/Components/Tag.md)>       | :heavy_minus_sign:                                | N/A                                               |                                                   |
| `Status`                                          | [PetStatus](../../Models/Components/PetStatus.md) | :heavy_minus_sign:                                | pet status in the store                           |                                                   |