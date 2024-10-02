
-- Auto Farm
local plr = game.Players.LocalPlayer
local CFrame = plr.Character.HumanoidRootPart.CFrame

while true do
    wait()
    local enemies = game:GetService("Workspace").Enemies:GetChildren()
    for i, v in pairs(enemies) do
        if v:FindFirstChild("Humanoid") and v.Humanoid.Health > 0 then
            plr.Character.HumanoidRootPart.CFrame = v.HumanoidRootPart.CFrame * CFrame.new(0, 0, 3)
            game:GetService("VirtualInputManager"):SendKeyEvent(true, "X", false, game)
            wait(0.1)
            game:GetService("VirtualInputManager"):SendKeyEvent(false, "X", false, game)
        end
    end
end

-- Auto Bone
local args = {
    [1] = "ActivateAbility"
}

game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))

-- Teleporte de Frutas
local fruitSpawns = game:GetService("Workspace").Enemies:GetDescendants("FruitSpawner")
for i, v in pairs(fruitSpawns) do
    plr.Character.HumanoidRootPart.CFrame = v.CFrame
end

-- Auto Store Fruits
local args = {
    [1] = "StoreFruit"
}

game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))

-- Rastreador de Frutas
local fruits = game:GetService("Workspace").Enemies:GetDescendants("FruitSpawner")
for i, v in pairs(fruits) do
    plr.Character.HumanoidRootPart.CFrame = v.CFrame
end

-- Auto Sea Events
local seaEvents = game:GetService("Workspace").Enemies:GetDescendants("SeaEventSpawner")
for i, v in pairs(seaEvents) do
    plr.Character.HumanoidRootPart.CFrame = v.CFrame
end
