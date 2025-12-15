
local Players = game:GetService("Players")
local Workspace = game:GetService("Workspace")
local UserInputService = game:GetService("UserInputService")
local RunService = game:GetService("RunService")
local TweenService = game:GetService("TweenService")
local HttpService = game:GetService("HttpService")
local CoreGui = game:GetService("CoreGui")
local TeleportService = game:GetService("TeleportService")

-- Variáveis Globais
local player = Players.LocalPlayer
local mouse = player:GetMouse()
local camera = Workspace.CurrentCamera
local character = player.Character or player.CharacterAdded:Wait()
local humanoid = character:WaitForChild("Humanoid")
local rootPart = character:WaitForChild("HumanoidRootPart")

-- Variáveis de Controle
local aimbotEnabled = false
local aimbotTarget = nil
local espEnabled = false
local tpEnabled = false
local tpTarget = nil
local autoFarmEnabled = false
local noclipEnabled = false
local flyEnabled = false
local flySpeed = 50
local invisibilityEnabled = false

-- Funções de Utilidade
local function createGUI()
    local ScreenGui = Instance.new("ScreenGui")
    ScreenGui.Name = "BloxFruitsGUI"
    ScreenGui.Parent = CoreGui
    ScreenGui.ZIndexBehavior = Enum.ZIndexBehavior.Sibling

    local MainFrame = Instance.new("Frame")
    MainFrame.Name = "MainFrame"
    MainFrame.Parent = ScreenGui
    MainFrame.BackgroundColor3 = Color3.fromRGB(35, 35, 35)
    MainFrame.BorderSizePixel = 0
    MainFrame.Position = UDim2.new(0.5, -200, 0.5, -150)
    MainFrame.Size = UDim2.new(0, 400, 0, 300)
    MainFrame.Draggable = true

    local TitleLabel = Instance.new("TextLabel")
    TitleLabel.Name = "TitleLabel"
    TitleLabel.Parent = MainFrame
    TitleLabel.BackgroundColor3 = Color3.fromRGB(255, 85, 0)
    TitleLabel.BorderSizePixel = 0
    TitleLabel.Position = UDim2.new(0, 0, 0, 0)
    TitleLabel.Size = UDim2.new(1, 0, 0, 30)
    TitleLabel.Font = Enum.Font.SourceSansBold
    TitleLabel.Text = "Blox Fruits Script v1.0"
    TitleLabel.TextColor3 = Color3.fromRGB(255, 255, 255)
    TitleLabel.TextSize = 18

    local TabFrame = Instance.new("Frame")
    TabFrame.Name = "TabFrame"
    TabFrame.Parent = MainFrame
    TabFrame.BackgroundColor3 = Color3.fromRGB(45, 45, 45)
    TabFrame.BorderSizePixel = 0
    TabFrame.Position = UDim2.new(0, 0, 0, 30)
    TabFrame.Size = UDim2.new(0, 100, 1, -30)

    local ContentFrame = Instance.new("Frame")
    ContentFrame.Name = "ContentFrame"
    ContentFrame.Parent = MainFrame
    ContentFrame.BackgroundColor3 = Color3.fromRGB(55, 55, 55)
    ContentFrame.BorderSizePixel = 0
    ContentFrame.Position = UDim2.new(0, 100, 0, 30)
    ContentFrame.Size = UDim2.new(1, -100, 1, -30)

    -- Abas
    local CombatTab = Instance.new("TextButton")
    CombatTab.Name = "CombatTab"
    CombatTab.Parent = TabFrame
    CombatTab.BackgroundColor3 = Color3.fromRGB(65, 65, 65)
    CombatTab.BorderSizePixel = 0
    CombatTab.Position = UDim2.new(0, 0, 0, 10)
    CombatTab.Size = UDim2.new(1, 0, 0, 30)
    CombatTab.Font = Enum.Font.SourceSans
    CombatTab.Text = "Combate"
    CombatTab.TextColor3 = Color3.fromRGB(255, 255, 255)
    CombatTab.TextSize = 14

    local VisualTab = Instance.new("TextButton")
    VisualTab.Name = "VisualTab"
    VisualTab.Parent = TabFrame
    VisualTab.BackgroundColor3 = Color3.fromRGB(65, 65, 65)
    VisualTab.BorderSizePixel = 0
    VisualTab.Position = UDim2.new(0, 0, 0, 50)
    VisualTab.Size = UDim2.new(1, 0, 0, 30)
    VisualTab.Font = Enum.Font.SourceSans
    VisualTab.Text = "Visual"
    VisualTab.TextColor3 = Color3.fromRGB(255, 255, 255)
    VisualTab.TextSize = 14

    local TeleportTab = Instance.new("TextButton")
    TeleportTab.Name = "TeleportTab"
    TeleportTab.Parent = TabFrame
    Teleport
