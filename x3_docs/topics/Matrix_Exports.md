# Exports

You are provided a few exports so you can customize this script to your liking, whether implementing your own system to
install the matrix boards onto the vehicles to using an item to open the menu, etc.

| Server/Client | Export                          | Description                                                                          | Parameters                                | Return Type    |
|---------------|---------------------------------|--------------------------------------------------------------------------------------|-------------------------------------------|----------------|
| Client        | CanOpenMatrixMenu               | Returns true/false whether the menu can be opened by the player                      | N/A                                       | Boolean        |
| Client        | GetVehicleConfig                | Gets the vehicle config for the given hash. If nil, no config exists for given model | Model                                     | VehicleConfig? |
| Client        | InstallMatrixOnVehicle          | Installs the matrix boards onto the given vehicle. True if successful                | Vehicle Handle                            | Boolean        |
| Client        | UninstallMatrixBoardFromVehicle | Uninstalls the matrix board from the given vehicle. True if successful               | Vehicle Handle                            | Boolean        |
| Client        | SendMatrixBoardMessage          | Sends matrix board UI message to the given vehicle                                   | Vehicle Handle, MatrixUIData, boardIndex? | nil            |
| Client        | OpenMenu                        | Opens the matrix menu for the current vehicle                                        | N/A                                       | nil            |

## Types

### VehicleConfig

```text
{
    Distance = 75.0,                           -- Distance from the vehicle to start rendering in the matrix boards
    MatrixBoards = {                           -- List of all matrix board positions
        {
            Model = `D3s_Matrix`,              -- Model of the matrix board (see config_matrixboards.lua)
            Name = 'Rear',                     -- Name of the matrix board as it appears in the menu
            Offset = vector3(0.0, -2.1, 0.85), -- Position of the matrix board offset from the center of the vehicle
            Rotation = vector3(0.0, 0.0, 0.0), -- Rotation of the matrix board
            VisibleByDefault = true,           -- If the matrix board is visible by default
        },
    }
```

### MatrixUIData

```text
{
    Text: ['POLICE', 'SCROLLING TEXT'], -- Array of text
    Delay: 1000, -- Delay between the texts
    Speed: 5.0, -- Speed of scrolling texts
    Color: 'orange' -- Color of the text
}
```