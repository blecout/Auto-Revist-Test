local player = game.Players.LocalPlayer
local frame = script.Parent
local activateButton = frame:WaitForChild("ActivateButton")
local deactivateButton = frame:WaitForChild("DeactivateButton")

local autoRevistarAtivo = false

local function ativarAutoRevistar()
    autoRevistarAtivo = true
    print("Auto-revistar ativado!")
end

local function desativarAutoRevistar()
    autoRevistarAtivo = false
    print("Auto-revistar desativado!")
end

activateButton.MouseButton1Click:Connect(ativarAutoRevistar)
deactivateButton.MouseButton1Click:Connect(desativarAutoRevistar)

while true do
    wait(1) -- Espera 1 segundo entre as verificações
    if autoRevistarAtivo then
        local character = player.Character
        if character then
            local items = {"Uzi", "AK47", "G3", "Parafal", "Glock 17", "Hi Power"}
            for _, itemName in pairs(items) do
                local item = workspace:FindFirstChild(itemName)
                if item and (item:IsA("Tool") or item:IsA("Weapon")) then
                    item.Parent = player.Backpack
                    print(itemName .. " coletado!")
                end
            end
        end
    end
end
