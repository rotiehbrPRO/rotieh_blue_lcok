-- Blue Lock Roblox Script Generator
-- Generated for player: YourPlayerName
-- No key required, all features enabled!

local Player = game:GetService("Players").LocalPlayer
local Character = Player.Character or Player.CharacterAdded:Wait()
local Humanoid = Character:WaitForChild("Humanoid")
local PlayerGui = Player:WaitForChild("PlayerGui")

-- Load necessary services
local RunService = game:GetService("RunService")
local ReplicatedStorage = game:GetService("ReplicatedStorage")
local UserInputService = game:GetService("UserInputService")

-- Initialize script
print("Blue Lock Script loaded successfully!")

-- Auto Goal feature
RunService.Heartbeat:Connect(function()
    local ball = workspace:FindFirstChild("SoccerBall")
    if ball and Character then
        local goalPosition = workspace.GoalPosts.OpponentGoal.Center.Position
        
        -- When player is near the ball, teleport to the goal and kick
        if (Character.HumanoidRootPart.Position - ball.Position).Magnitude < 10 then
            -- Teleport the ball to the player first
            ball.Position = Character.HumanoidRootPart.Position
            
            -- Then teleport player near the goal
            local teleportPosition = goalPosition - Vector3.new(5, 0, 0)  -- Position slightly in front of goal
            Character.HumanoidRootPart.CFrame = CFrame.new(teleportPosition)
            
            -- Kick ball into goal
            local direction = (goalPosition - Character.HumanoidRootPart.Position).Unit
            ReplicatedStorage.Events.KickBall:FireServer(direction * 150, ball)
            print("Auto Goal activated - teleported to goal!")
        end
    end
end)

-- Script execution completed
print("All selected features have been activated!")
print("Enjoy your enhanced Blue Lock experience!")
