local ReplicatedStorage = game:GetService("ReplicatedStorage")
local SoundEvent = ReplicatedStorage:WaitForChild("SoundEvent")
local SpeedEvent = ReplicatedStorage:WaitForChild("SpeedEvent")
local JumpEvent = ReplicatedStorage:WaitForChild("JumpEvent")

-- Função para acionar o som
game:GetService("UserInputService").TouchStarted:Connect(function(input)
    local touchPosition = input.Position
    if touchPosition.X < game:GetService("Workspace").CurrentCamera.ViewportSize.X / 2 then
        -- Toque na parte esquerda da tela para tocar o som
        local soundId = "rbxassetid://YOUR_SOUND_ID"  -- Substitua pelo seu ID de som
        SoundEvent:FireServer(soundId)
    end
end)

-- Função para aumentar a velocidade
game:GetService("UserInputService").TouchStarted:Connect(function(input)
    local touchPosition = input.Position
    if touchPosition.X > game:GetService("Workspace").CurrentCamera.ViewportSize.X / 2 then
        -- Toque na parte direita da tela para aumentar a velocidade
        SpeedEvent:FireServer()
    end
end)

-- Função para aumentar o pulo
game:GetService("UserInputService").TouchStarted:Connect(function(input)
    local touchPosition = input.Position
    if touchPosition.Y < game:GetService("Workspace").CurrentCamera.ViewportSize.Y / 2 then
        -- Toque na parte inferior da tela para aumentar o pulo
        JumpEvent:FireServer()
    end
end)
