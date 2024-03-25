# Default Matrix Config
{id="matrix_boards_default_config" title="Matrix Boards Default Config"}

Below is the default `config_matrixboards.lua` file.

> Usually you do not need to touch this file unless you are adding a custom-made matrix board.
> 
{style="note" title="Note"}

```text
-- Ignore this file if you don't know what you're doing.

local function DefaultSettingsDialogFunc(currentSettings)
    local uiSettings = currentSettings.UISettings
    local visible = currentSettings.Visible
    return {
        {
            label = 'Text 1',
            type = 'input',
            description = 'Text to display on the matrix board',
            required = true,
            default = uiSettings.Text and uiSettings.Text[1],
            max = 50
        },
        {
            label = 'Text 2',
            type = 'input',
            description = 'Text to display on the matrix board',
            required = false,
            default = uiSettings.Text and uiSettings.Text[2],
            max = 50
        },
        {
            label = 'Text 3',
            type = 'input',
            description = 'Text to display on the matrix board',
            required = false,
            default = uiSettings.Text and uiSettings.Text[3],
            max = 50
        },
        {
            label = 'Text 4',
            type = 'input',
            description = 'Text to display on the matrix board',
            required = false,
            default = uiSettings.Text and uiSettings.Text[4],
            max = 50
        },
        {
            label = 'Text 5',
            type = 'input',
            description = 'Text to display on the matrix board',
            required = false,
            default = uiSettings.Text and uiSettings.Text[5],
            max = 50
        },
        {
            label = 'Color',
            type = 'color',
            description = 'Color of the text',
            default = uiSettings.Color or '#FF8A00',
        },
        {
            label = 'Delay (ms)',
            type = 'number',
            description = 'Delay between text changes',
            step = 250,
            min = 250,
            max = 10000,
            default = uiSettings.Delay or 1000,
        },
        {
            label = 'Scroll Speed',
            type = 'number',
            description = 'Any text over 8 characters will automatically scroll, this is the speed of the scroll',
            step = 1,
            min = 1,
            max = 8,
            default = uiSettings.Speed or 3,
        },
        {
            label = 'Visible',
            type = 'checkbox',
            description = 'Show this matrix board',
            checked = visible,
        }
    }
end

local function DefaultParseSettingsFunc(dialogResult)
    if (not dialogResult) then return end

    local texts = {}
    for i = 1, 5 do
        local text = dialogResult[i]
        if (text and text ~= '') then
            table.insert(texts, text)
        end
    end

    local matrixSettings = {
        Text = texts,
        Color = dialogResult[6],
        Delay = dialogResult[7],
        Speed = dialogResult[8],
    }

    local visible = dialogResult[9]

    return {
        UISettings = matrixSettings,
        Visible = visible
    }
end


Config.MatrixBoards = {
    [`D3s_Matrix`] = {              -- Model of the matrix board
        TextureDict = 'D3s_Matrix', -- Texture dictionary of the matrix board
        ExtraToTextureName = {      -- Don't change this unless you know what you're doing.
            [1] = 'Sign_1',
            [2] = 'Sign_2',
            [3] = 'Sign_3',
            [4] = 'Sign_4',
            [5] = 'Sign_5',
            [6] = 'Sign_6',
            [7] = 'Sign_7',
            [8] = 'Sign_8',
            [9] = 'Sign_9',
            [10] = 'Sign_10',
        },
        Url = string.format("nui://%s/html/D3s_Matrix/index.html", GetCurrentResourceName()), -- Don't change this unless you know what you're doing.
        Height = 140,                                                                         -- Height of the matrix board (UI)
        Width = 860,                                                                          -- Width of the matrix board (UI)
        DefaultUISettings = {                                                                 -- Default settings for the matrix board
            Text = { 'POLICE' },
            Color = '#FF8A00',
            Delay = 1000,
            Speed = 3,
        },
        SettingsDialogFunc = DefaultSettingsDialogFunc,
        ParseSettingsFunc = DefaultParseSettingsFunc
    }
}
```
{collapsible="true" default-state="expanded" collapsed-title="config_matrixboards.lua"}
