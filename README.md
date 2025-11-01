-- 🛡 HUB ARRÁSTAVEL, MINIMIZÁVEL E RESTRITO POR NICK
-- Apenas mendes24135 e davizinho221111 podem usar
-- Coloque este script como LocalScript em StarterGui

local Players = game:GetService("Players")
local LocalPlayer = Players.LocalPlayer
local PlayerGui = LocalPlayer:WaitForChild("PlayerGui")

-- Lista de nicks autorizados (em minúsculas)
local allowed = {
    ["mendes24135"] = true,
    ["davizinho221111"] = true,
}

-- Checagem de permissão
if not allowed[string.lower(LocalPlayer.Name or "")] then
    -- Kick imediato com mensagem se não for autorizado
    LocalPlayer:Kick("Você não está autorizado")
    return
end

-- ====================================
-- GUI do Hub
-- ====================================

-- Criar ScreenGui
local ScreenGui = Instance.new("ScreenGui")
ScreenGui.Name = "DraggableHub"
ScreenGui.Parent = PlayerGui
ScreenGui.ResetOnSpawn = false

-- Frame principal
local MainFrame = Instance.new("Frame")
MainFrame.Size = UDim2.new(0, 250, 0, 330)
MainFrame.Position = UDim2.new(0.35, 0, 0.3, 0)
MainFrame.BackgroundColor3 = Color3.fromRGB(25, 25, 25)
MainFrame.BorderSizePixel = 0
MainFrame.Active = true
MainFrame.Draggable = true
MainFrame.Parent = ScreenGui

-- Título
local TitleBar = Instance.new("TextLabel")
TitleBar.Text = "📦 HUB MENU"
TitleBar.Size = UDim2.new(1, 0, 0, 30)
TitleBar.BackgroundColor3 = Color3.fromRGB(35, 35, 35)
TitleBar.TextColor3 = Color3.fromRGB(255, 255, 255)
TitleBar.Font = Enum.Font.SourceSansBold
TitleBar.TextSize = 18
TitleBar.Parent = MainFrame

-- Botão Minimizar
local MinimizeButton = Instance.new("TextButton")
MinimizeButton.Text = "-"
MinimizeButton.Size = UDim2.new(0, 30, 0, 30)
MinimizeButton.Position = UDim2.new(1, -35, 0, 0)
MinimizeButton.BackgroundColor3 = Color3.fromRGB(50, 50, 50)
MinimizeButton.TextColor3 = Color3.fromRGB(255, 255, 255)
MinimizeButton.Font = Enum.Font.SourceSansBold
MinimizeButton.TextSize = 20
MinimizeButton.Parent = MainFrame

-- Corpo
local Body = Instance.new("Frame")
Body.Size = UDim2.new(1, 0, 1, -30)
Body.Position = UDim2.new(0, 0, 0, 30)
Body.BackgroundColor3 = Color3.fromRGB(40, 40, 40)
Body.BorderSizePixel = 0
Body.Parent = MainFrame

-- Função criar botão
local function criarBotao(texto, ordem, callback)
    local botao = Instance.new("TextButton")
    botao.Size = UDim2.new(0, 200, 0, 30)
    botao.Position = UDim2.new(0.5, -100, 0, (ordem - 1) * 35 + 10)
    botao.Text = texto
    botao.BackgroundColor3 = Color3.fromRGB(70, 70, 70)
    botao.TextColor3 = Color3.fromRGB(255, 255, 255)
    botao.Font = Enum.Font.SourceSansBold
    botao.TextSize = 16
    botao.Parent = Body
    
    botao.MouseEnter:Connect(function()
        botao.BackgroundColor3 = Color3.fromRGB(90, 90, 90)
    end)
    botao.MouseLeave:Connect(function()
        botao.BackgroundColor3 = Color3.fromRGB(70, 70, 70)
    end)

    botao.MouseButton1Click:Connect(callback)
end

-- ================================
-- Botões com loadstrings
-- ================================

criarBotao("Nameless Hub 💜", 1, function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/ily123950/Vulkan/refs/heads/main/Tr"))()
end)

criarBotao("Lumora Fps Destroyer 👹", 2, function()
    loadstring(game:HttpGet("https://api.luarmor.net/files/v3/loaders/c62563366e7ba3208d704a4e2d7e6789.lua"))()
end)

criarBotao("Lennon Hub 🐊", 3, function()
    loadstring(game:HttpGet("https://pastefy.app/RusmcE3c/raw"))()
end)

criarBotao("Chilli Hub", 4, function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/tienkhanh1/spicy/main/Chilli.lua"))()
end)

criarBotao("Kurd Hub 👨‍💻", 5, function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/Ninja10908/S4/refs/heads/main/Kurdhub"))()
end)

criarBotao("Miranda Hub ♦️", 6, function()
    loadstring(game:HttpGet("https://pastefy.app/ZvovS3bh/raw"))()
end)

criarBotao("Lipe Tools", 7, function()
    loadstring(game:HttpGet("https://pastebin.com/raw/ke146qjn"))()
end)

-- Minimizar / Restaurar
local minimizado = false
MinimizeButton.MouseButton1Click:Connect(function()
    minimizado = not minimizado
    if minimizado then
        Body.Visible = false
        MainFrame.Size = UDim2.new(0, 250, 0, 30)
        MinimizeButton.Text = "+"
    else
        Body.Visible = true
        MainFrame.Size = UDim2.new(0, 250, 0, 330)
        MinimizeButton.Text = "-"
    end
end)
