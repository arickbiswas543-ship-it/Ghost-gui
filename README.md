loadstring([[
local P = game:GetService("Players").LocalPlayer
local G = P:WaitForChild("PlayerGui")
local KEY = "(/*userroblox(key)+gui-(key)*)/enter*)/"
local KEYLINK = "https://youtube.com/@lnt_ght?si=7dEJHBFjE0brggld"
local SCRIPTS_URL = "https://raw.githubusercontent.com/YourUsername/ghost-gui/main/scripts.lua"
local ADD_SCRIPT_URL = "https://github.com/YourUsername/ghost-gui/issues/new"

local K = Instance.new("ScreenGui", G)
local F = Instance.new("Frame", K)
F.Size = UDim2.new(0, 360, 0, 190)
F.Position = UDim2.new(0.5, -180, 0.5, -95)
F.BackgroundColor3 = Color3.fromRGB(18, 18, 18)
F.Active = true
F.Draggable = true
Instance.new("UICorner", F)

local T = Instance.new("TextLabel", F)
T.Size = UDim2.new(1, 0, 0, 40)
T.BackgroundTransparency = 1
T.Text = "Ghost GUI"
T.TextColor3 = Color3.new(1,1,1)
T.Font = Enum.Font.GothamBold
T.TextSize = 22

local C = Instance.new("TextButton", F)
C.Size = UDim2.new(1, -20, 0, 30)
C.Position = UDim2.new(0,10,0,50)
C.Text = "Copy Key"
C.BackgroundColor3 = Color3.fromRGB(255,255,255)
C.TextColor3 = Color3.new(0,0,0)
Instance.new("UICorner", C)
C.MouseButton1Click:Connect(function() setclipboard(KEYLINK) end)

local B = Instance.new("TextBox", F)
B.Size = UDim2.new(1, -20, 0, 30)
B.Position = UDim2.new(0,10,0,90)
B.PlaceholderText = "Enter Key"
B.TextColor3 = Color3.new(1,1,1)
B.BackgroundColor3 = Color3.fromRGB(30,30,30)
Instance.new("UICorner", B)

local S = Instance.new("TextButton", F)
S.Size = UDim2.new(1, -20, 0, 30)
S.Position = UDim2.new(0,10,0,130)
S.Text = "Submit"
S.BackgroundColor3 = Color3.fromRGB(70,120,255)
S.TextColor3 = Color3.new(1,1,1)
Instance.new("UICorner", S)

local function OPEN()
    K:Destroy()
    local GUI = Instance.new("ScreenGui", G)
    GUI.ResetOnSpawn = false

    local M = Instance.new("Frame", GUI)
    M.Size = UDim2.new(0,600,0,350)
    M.Position = UDim2.new(0.5,-300,0.5,-175)
    M.BackgroundColor3 = Color3.fromRGB(18,18,18)
    M.Active = true
    M.Draggable = true
    Instance.new("UICorner", M)

    local TOGGLE = Instance.new("TextButton", GUI)
    TOGGLE.Size = UDim2.new(0,90,0,30)
    TOGGLE.Position = UDim2.new(0,10,0,10)
    TOGGLE.Text = "Hide"
    TOGGLE.BackgroundColor3 = Color3.fromRGB(30,30,30)
    TOGGLE.TextColor3 = Color3.new(1,1,1)
    Instance.new("UICorner", TOGGLE)
    TOGGLE.MouseButton1Click:Connect(function()
        M.Visible = not M.Visible
        TOGGLE.Text = M.Visible and "Hide" or "Show"
    end)

    local TT = Instance.new("TextLabel", M)
    TT.Size = UDim2.new(1,0,0,40)
    TT.BackgroundTransparency = 1
    TT.Text = "👻 Ghost GUI"
    TT.TextColor3 = Color3.new(1,1,1)
    TT.Font = Enum.Font.GothamBold
    TT.TextSize = 22

    local SEARCH = Instance.new("TextBox", M)
    SEARCH.Size = UDim2.new(1,-20,0,30)
    SEARCH.Position = UDim2.new(0,10,0,50)
    SEARCH.PlaceholderText = "Search Script"
    SEARCH.BackgroundColor3 = Color3.fromRGB(30,30,30)
    SEARCH.TextColor3 = Color3.new(1,1,1)
    Instance.new("UICorner", SEARCH)

    local ADD = Instance.new("TextButton", M)
    ADD.Size = UDim2.new(1,-20,0,30)
    ADD.Position = UDim2.new(0,10,1,-40)
    ADD.Text = "Add Script"
    ADD.BackgroundColor3 = Color3.fromRGB(70,120,255)
    ADD.TextColor3 = Color3.new(1,1,1)
    Instance.new("UICorner", ADD)
    ADD.MouseButton1Click:Connect(function() setclipboard(ADD_SCRIPT_URL) end)

    local SC = Instance.new("ScrollingFrame", M)
    SC.Size = UDim2.new(1,-20,1,-140)
    SC.Position = UDim2.new(0,10,0,90)
    SC.CanvasSize = UDim2.new(0,0,0,0)
    SC.ScrollBarThickness = 6
    SC.BackgroundColor3 = Color3.fromRGB(25,25,25)
    Instance.new("UICorner", SC)

    local L = Instance.new("UIListLayout", SC)
    L.Padding = UDim.new(0,8)

    local success, list = pcall(function()
        return loadstring(game:HttpGet(SCRIPTS_URL))()
    end)
    if success and type(list) == "table" then
        for _,v in pairs(list) do
            local b = Instance.new("TextButton", SC)
            b.Size = UDim2.new(1,-10,0,40)
            b.Text = v.Title
            b.Font = Enum.Font.Gotham
            b.TextSize = 16
            b.TextColor3 = Color3.new(1,1,1)
            b.BackgroundColor3 = Color3.fromRGB(40,40,40)
            Instance.new("UICorner", b)
            b.MouseButton1Click:Connect(function()
                loadstring(game:HttpGet(v.URL))()
            end)
        end
        SC.CanvasSize = UDim2.new(0,0,0,L.AbsoluteContentSize.Y+10)
    end
end

S.MouseButton1Click:Connect(function()
    if B.Text == KEY then
        OPEN()
    end
end)
]] )()
