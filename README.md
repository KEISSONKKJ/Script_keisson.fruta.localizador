# Script_keisson.fruta.localizador

git remote add origin https://github.com/Script_keisson.fruta.localizador.git

-- Script ESP para Blox Fruits
-- Nome: Keisson

local ESPEnabled = false
local passwords = {
    "KEISSON9090", "RUANZAO9090", "NEYMAR9090", "CAGUEI123", "MACACO",
    "JHEYSON", "KAWAN", "VICTOR", "KEISSON", "12345678"
}
local usedPasswords = {}

-- Função para desenhar ESP
local function DESP()
    if not ESPEnabled then return end

    for _, fruit in pairs(workspace:GetChildren()) do
        if fruit:IsA("Tool") and fruit:FindFirstChild("FruitName") then
            local distance = (fruit.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).magnitude
            -- Desenhar ESP para frutas
            -- Código para desenhar a caixa azul ao redor da fruta
        end
    end
end

-- Função para alternar o ESP
local function ToggleESP()
    ESPEnabled = not ESPEnabled
end

-- Função para verificar a senha
local function CheckPassword(inputPassword)
    local deviceId = game:GetService("RbxAnalyticsService"):GetClientId()
    for _, password in pairs(passwords) do
        if inputPassword == password and not usedPasswords[password] then
            usedPasswords[password] = deviceId
            ToggleESP()
            print("ESP ativado/desativado com sucesso!")
            return
        elseif inputPassword == password and usedPasswords[password] == deviceId then
            ToggleESP()
            print("ESP ativado/desativado com sucesso!")
            return
        end
    end
    print("Senha incorreta ou já usada em outro dispositivo!")
end

-- Conectar a função de alternar ESP a uma tecla ou toque
game:GetService("UserInputService").InputBegan:Connect(function(input)
    if input.KeyCode == Enum.KeyCode.E or input.UserInputType == Enum.UserInputType.Touch then
        local userInput = game:GetService("Players").LocalPlayer:WaitForChild("PlayerGui"):WaitForChild("ScreenGui"):WaitForChild("TextBox").Text
        CheckPassword(userInput)
    end
end)

-- Loop para atualizar o ESP
while true do
    DESP()
    wait(0.1)
end
