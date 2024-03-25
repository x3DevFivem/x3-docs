# Default Config

Below is the default `config.lua` file.

```text
Config = {
    LoggingLevel = 2,
    TxdName = 'x3_matrixboard', -- No need to change this.
    TxNamePrefix = 'matrix_',   -- No need to change this.
    Commands = {
        MatrixMenu = {
            Name = 'matrixmenu',   -- Name of the command
            Enabled = true,        -- If the command is enabled, disable this if you prefer to implement your own system using provided exports
            ShowInstallMenu = true -- If the command should show the install menu when its not installed
        }
    },
    Menu = {
        Id = 'matrix_board_menu', -- ID of the menu
        Title = 'Matrix Board',   -- Title of the menu
        Position = 'top-right'
    }
}

Config.Vehicles = {
    [`polexplorer`] = {                            -- Vehicle model name
        Distance = 75.0,                           -- Distance from the vehicle to start rendering in the matrix boards
        MatrixBoards = {                           -- List of all matrix board positions
            {
                Model = `D3s_Matrix`,              -- Model of the matrix board (see config_matrixboards.lua)
                Name = 'Rear',                     -- Name of the matrix board as it appears in the menu
                Offset = vector3(0.0, -2.1, 0.85), -- Position of the matrix board offset from the center of the vehicle
                Rotation = vector3(0.0, 0.0, 0.0), -- Rotation of the matrix board
                Togglable = true,                  -- If the matrix board can be toggled on/off
                VisibleByDefault = true,           -- If the matrix board is visible by default
            },
        }
    }
}
```
{collapsible="true" default-state="expanded" collapsed-title="config.lua"}
