local script = [[
-- Define a function to create the GUI buttons
function CreateButtons()
    -- Create a ScreenGui object to hold the buttons
    local gui = Instance.new("ScreenGui")
    gui.Name = "Callux"
    gui.ResetOnSpawn = false
    gui.Parent = game:GetService("Players").LocalPlayer:WaitForChild("PlayerGui")

    -- Create a Frame object to hold the buttons
    local frame = Instance.new("Frame")
    frame.Size = UDim2.new(0, 200, 0, 100)
    frame.Position = UDim2.new(0.5, -100, 0.5, -50)
    frame.BackgroundColor3 = Color3.new(0, 0, 0)
    frame.BackgroundTransparency = 0.5
    frame.Parent = gui

    -- Create a TextButton object for the "Matar todos os Jogadores" button
    local killButton = Instance.new("TextButton")
    killButton.Text = "Matar todos os Jogadores"
    killButton.Size = UDim2.new(0, 180, 0, 40)
    killButton.Position = UDim2.new(0.5, -90, 0.25, -20)
    killButton.BackgroundColor3 = Color3.new(1, 0, 0)
    killButton.Parent = frame

    -- Create a TextButton object for the "Ver Jogadores" button
    local viewButton = Instance.new("TextButton")
    viewButton.Text = "Ver Jogadores"
    viewButton.Size = UDim2.new(0, 180, 0, 40)
    viewButton.Position = UDim2.new(0.5, -90, 0.75, -20)
    viewButton.BackgroundColor3 = Color3.new(1, 1, 1)
    viewButton.Parent = frame

    -- Connect the button events
    killButton.MouseButton1Click:Connect(function()
        -- Replace this with your own code to handle the button click
        for _, player in ipairs(game:GetService("Players"):GetPlayers()) do
            if player ~= game:GetService("Players").LocalPlayer then
                player.Character:BreakJoints()
            end
        end
    end)

    viewButton.MouseButton1Click:Connect(function()
        -- Replace this with your own code to handle the button click
        for _, player in ipairs(game:GetService("Players"):GetPlayers()) do
            if player ~= game:GetService("Players").LocalPlayer then
                local arrow = Instance.new("TextLabel")
                arrow.Text = "➤"
                arrow.TextColor3 = Color3.new(1, 1, 1)
                arrow.Position = UDim2.new(0.5, 0, 0.5, 0)
                arrow.AnchorPoint = Vector2.new(0.5, 0.5)
                arrow.Parent = player.Character.Head

                local name = Instance.new("TextLabel")
                name.Text = player.Name
                name.TextColor3 = Color3.new(1, 1, 1)
                name.Position = UDim2.new(0.5, 0, 0, -20)
                name.AnchorPoint = Vector2.new(0.5, 0.5)
                name.Parent = arrow

                local health = Instance.new("TextLabel")
                health.Text = "Health: " .. tostring(player.Character.Humanoid.Health)
                health.TextColor3 = Color3.new(1, 1, 1)
                health.Position = UDim2.new(0.5, 0, 0, 20)
                health.AnchorPoint = Vector2.new(0.5, 0.5)
                health.Parent = arrow

                local distance = Instance.new("TextLabel")
                distance.Text = "Distance: " .. tostring((player.Character.Head.Position - game:GetService("Players").LocalPlayer.Character.Head.Position).Magnitude)
                distance.TextColor3 = Color3.new(1, 1, 1)
                distance.Position = UDim2.new(0.5, 0, 0, 60)
                distance.AnchorPoint = Vector2.new(0.5, 0.5)
                distance.Parent = arrow
            end
        end
    end)
end

-- Call the CreateButtons function to create the GUI buttons
CreateButtons()
]]

loadstring(script)()
