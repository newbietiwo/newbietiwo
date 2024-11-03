local Players = game:GetService("Players")
local player = Players.LocalPlayer

-- Key system setup
local validKeys = {
    "key1",
}

local function isValidKey(inputKey)
    for _, key in ipairs(validKeys) do
        if inputKey == key then
            return true
        end
    end
    return false
end

local function createUI()
    -- Simple UI creation
    local ScreenGui = Instance.new("ScreenGui", player:WaitForChild("PlayerGui"))
    local Frame = Instance.new("Frame", ScreenGui)
    Frame.Size = UDim2.new(0, 300, 0, 300)
    Frame.Position = UDim2.new(0.5, -150, 0.5, -150)
    Frame.BackgroundColor3 = Color3.fromRGB(50, 50, 50)

    local Title = Instance.new("TextLabel", Frame)
    Title.Size = UDim2.new(1, 0, 0, 50)
    Title.Text = "Enter Key"
    Title.TextColor3 = Color3.fromRGB(255, 255, 255)
    Title.BackgroundColor3 = Color3.fromRGB(0, 0, 0)

    local InputBox = Instance.new("TextBox", Frame)
    InputBox.Size = UDim2.new(0.8, 0, 0, 50)
    InputBox.Position = UDim2.new(0.1, 0, 0.25, 0)
    InputBox.PlaceholderText = "Enter your key"

    local SubmitButton = Instance.new("TextButton", Frame)
    SubmitButton.Size = UDim2.new(0.3, 0, 0, 50)
    SubmitButton.Position = UDim2.new(0.35, 0, 0.6, 0)
    SubmitButton.Text = "Submit"
    SubmitButton.BackgroundColor3 = Color3.fromRGB(0, 150, 0)

    local GetKeyButton = Instance.new("TextButton", Frame)
    GetKeyButton.Size = UDim2.new(0.3, 0, 0, 50)
    GetKeyButton.Position = UDim2.new(0.35, 0, 0.75, 0)
    GetKeyButton.Text = "Get Key"
    GetKeyButton.BackgroundColor3 = Color3.fromRGB(0, 100, 255)

    local CopyMessage = Instance.new("TextLabel", Frame)
    CopyMessage.Size = UDim2.new(1, 0, 0, 50)
    CopyMessage.Position = UDim2.new(0, 0, 0.85, 0)
    CopyMessage.Text = ""
    CopyMessage.TextColor3 = Color3.fromRGB(255, 255, 255)
    CopyMessage.BackgroundColor3 = Color3.fromRGB(50, 50, 50)

    SubmitButton.MouseButton1Click:Connect(function()
        local inputKey = InputBox.Text
        if isValidKey(inputKey) then
            print("Access granted!")
            -- Load additional features or functions here
            ScreenGui:Destroy() -- Remove UI after successful key entry
        else
            print("Invalid key!")
        end
    end)

    GetKeyButton.MouseButton1Click:Connect(function()
        local url = "https://www.youtube.com/watch?v=ToyPnBDNapg&t=353s"
        setclipboard(url) -- Copies the link to clipboard
        CopyMessage.Text = "Link copied to clipboard!" -- Display confirmation message
        wait(2) -- Optional: hide the message after 2 seconds
        CopyMessage.Text = "" -- Clear the message
    end)
end

-- Start the UI
createUI() 
