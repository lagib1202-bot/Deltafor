local Players = game:GetService("Players")
local player = Players.LocalPlayer

local Saves = {}
local slotCount = 0

local gui = Instance.new("ScreenGui")
gui.Name = "SaveTeleportGUI"
gui.ResetOnSpawn = false
gui.Parent = player:WaitForChild("PlayerGui")

local frame = Instance.new("Frame")
frame.Size = UDim2.new(0,260,0,300)
frame.Position = UDim2.new(0.05,0,0.2,0)
frame.BackgroundColor3 = Color3.fromRGB(35,35,35)
frame.Active = true
frame.Draggable = true
frame.Parent = gui

local title = Instance.new("TextLabel")
title.Size = UDim2.new(1,-60,0,30)
title.BackgroundTransparency = 1
title.Text = "Save Teleport"
title.TextColor3 = Color3.new(1,1,1)
title.TextScaled = true
title.Parent = frame

local hide = Instance.new("TextButton")
hide.Size = UDim2.new(0,25,0,25)
hide.Position = UDim2.new(1,-30,0,3)
hide.Text = "-"
hide.Parent = frame

local open = Instance.new("TextButton")
open.Size = UDim2.new(0,60,0,30)
open.Position = UDim2.new(0,10,0.5,0)
open.Text = "Open"
open.Visible = false
open.Parent = gui

hide.MouseButton1Click:Connect(function()
	frame.Visible = false
	open.Visible = true
end)

open.MouseButton1Click:Connect(function()
	frame.Visible = true
	open.Visible = false
end)

local add = Instance.new("TextButton")
add.Size = UDim2.new(1,-10,0,30)
add.Position = UDim2.new(0,5,0,35)
add.Text = "+ Add Slot"
add.Parent = frame

local scroll = Instance.new("ScrollingFrame")
scroll.Size = UDim2.new(1,-10,1,-70)
scroll.Position = UDim2.new(0,5,0,65)
scroll.CanvasSize = UDim2.new()
scroll.ScrollBarThickness = 6
scroll.Parent = frame

local function updateCanvas()
	scroll.CanvasSize = UDim2.new(0,0,0,slotCount*40)
end

local function createSlot()
end

add.MouseButton1Click:Connect(createSlot)

createSlot()
