-- =====================================================
-- KEY SYSTEM CONFIG
-- =====================================================

local KeySystemConfig = {
    Enabled = true,
    Keys = {
        -- KEYS NORMAIS
        "LKz34763548DFJ#@",
        "LKz92847563KLM$%",
        "LKz58394726NOP&*",
        "LKz74829563QRS^!",
        "LKz19384756TUV()_",
        "LKz83947562WXY+-=",
        "LKz45782936ABC[]{}",
        "LKz27394856DEF;:'",
        "LKz61847293GHI<>?,",
        "LKz38472918JKL|\\",
        "LKz92847361MNO`~",
        "LKz54739281PQR@#",
        "LKz81734629RST$%",
        "LKz39284756STU&*",
        "LKz74829361TUV()_",
        "LKz18394725UVW+-=",
        "LKz92837465VWX[]{}",
        "LKz47382916WXY;:'",
        "LKz63847291XYZ<>?,",
        "LKz84927361YZA|\\",
        "LKz25847193ZAB`~",
        "LKz39284617ABC@#",
        "LKz78349261BCD$%",
        "LKz52847369CDE&*",
        "LKz91847263DEF()_",
        "LKz37482916EFG+-=",
        "LKz64927381FGH[]{}",
        "LKz82374916GHI;:'",
        "LKz19384726HIJ<>?,",
        "LKz48392716IJK|\\",
        "LKz73482961JKL`~",
        "LKz29847361KLM@#",
        "LKz56384791LMN$%",
        "LKz84729361MNO&*",
        "LKz31847629NOP()_",
        "LKz67394281OPQ+-=",
        "LKz92847163PQR[]{}",
        "LKz38472916QRS;:'",
        "LKz74829163RST<>?,",
        "LKz45739281STU|\\",
        "LKz18294736TUV`~",
        "LKz62847391UVW@#",
        "LKz39284761VWX$%",
        "LKz81729463WXY&*",
        "LKz54829371XYZ()_",
        "LKz27394816YZA+-=",
        "LKz93847261ZAB[]{}",
        "LKz48372916ABC;:'",
        "LKz76284931BCD<>?,",
        "LKz12847365CDE|\\",

        -- KEYS PRINCIPAIS / VIP
        "KIEFER_KEY_REAlkz48537345",
        "ALMEIDA_KEY_REAlkz236452350987"
    },
    MaxAttempts = 3,
    BlockDuration = 30,
    DiscordLink = "https://discord.gg/NPhZqqCweX"
}

local keyAttempts = 0
local isBlocked = false
local blockedUntil = 0

-- =====================================================
-- KEY SYSTEM UI
-- =====================================================

local keySystemGui = Instance.new("ScreenGui")
keySystemGui.Name = "KeySystemGUI"
keySystemGui.ResetOnSpawn = false
keySystemGui.IgnoreGuiInset = true
keySystemGui.Parent = LocalPlayer:WaitForChild("PlayerGui")

local keyFrame = Instance.new("Frame")
keyFrame.AnchorPoint = Vector2.new(0.5, 0.5)
keyFrame.Position = UDim2.new(0.5, 0, 0.5, 0)
keyFrame.Size = UDim2.new(0, 400, 0, 260)
keyFrame.BackgroundColor3 = Color3.fromRGB(10, 10, 14)
keyFrame.BorderSizePixel = 0
keyFrame.ZIndex = 999
keyFrame.Parent = keySystemGui
Instance.new("UICorner", keyFrame).CornerRadius = UDim.new(0, 12)

local keyStroke = Instance.new("UIStroke")
keyStroke.Color = corPrincipal
keyStroke.Thickness = 1.6
keyStroke.Transparency = 0.35
keyStroke.ApplyStrokeMode = Enum.ApplyStrokeMode.Border
keyStroke.Parent = keyFrame

local keyTitle = Instance.new("TextLabel")
keyTitle.BackgroundTransparency = 1
keyTitle.Position = UDim2.new(0, 18, 0, 16)
keyTitle.Size = UDim2.new(1, -36, 0, 26)
keyTitle.Font = Enum.Font.GothamBold
keyTitle.Text = "Enhancer Internal - Arsenal"
keyTitle.TextColor3 = Color3.fromRGB(235, 235, 245)
keyTitle.TextSize = 20
keyTitle.TextXAlignment = Enum.TextXAlignment.Left
keyTitle.ZIndex = 1000
keyTitle.Parent = keyFrame

local keySubtitle = Instance.new("TextLabel")
keySubtitle.BackgroundTransparency = 1
keySubtitle.Position = UDim2.new(0, 18, 0, 46)
keySubtitle.Size = UDim2.new(1, -36, 0, 18)
keySubtitle.Font = Enum.Font.Gotham
keySubtitle.Text = "Faça seu login com sua chave de acesso particular"
keySubtitle.TextColor3 = Color3.fromRGB(150, 150, 160)
keySubtitle.TextSize = 13
keySubtitle.TextXAlignment = Enum.TextXAlignment.Left
keySubtitle.ZIndex = 1000
keySubtitle.Parent = keyFrame

local keyInput = Instance.new("TextBox")
keyInput.Name = "KeyInput"
keyInput.Position = UDim2.new(0, 20, 0, 80)
keyInput.Size = UDim2.new(1, -40, 0, 38)
keyInput.BackgroundColor3 = Color3.fromRGB(16, 16, 22)
keyInput.TextColor3 = Color3.fromRGB(220, 220, 230)
keyInput.Font = Enum.Font.GothamSemibold
keyInput.TextSize = 14
keyInput.PlaceholderText = "Cole sua key aqui..."
keyInput.PlaceholderColor3 = Color3.fromRGB(90, 90, 100)
keyInput.ClearTextOnFocus = false
keyInput.ZIndex = 1000
keyInput.Parent = keyFrame
Instance.new("UICorner", keyInput).CornerRadius = UDim.new(0, 8)

local keyInputStroke = Instance.new("UIStroke")
keyInputStroke.Color = corPrincipal
keyInputStroke.Thickness = 1.2
keyInputStroke.Transparency = 0.5
keyInputStroke.Parent = keyInput

local keyStatus = Instance.new("TextLabel")
keyStatus.BackgroundTransparency = 1
keyStatus.Position = UDim2.new(0, 20, 0, 124)
keyStatus.Size = UDim2.new(1, -40, 0, 18)
keyStatus.Font = Enum.Font.Gotham
keyStatus.Text = "Tentativas: 0/" .. KeySystemConfig.MaxAttempts
keyStatus.TextColor3 = Color3.fromRGB(150, 150, 160)
keyStatus.TextSize = 12
keyStatus.TextXAlignment = Enum.TextXAlignment.Left
keyStatus.ZIndex = 1000
keyStatus.Parent = keyFrame

local keySubmitBtn = Instance.new("TextButton")
keySubmitBtn.Position = UDim2.new(0, 20, 0, 155)
keySubmitBtn.Size = UDim2.new(1, -40, 0, 36)
keySubmitBtn.BackgroundColor3 = Color3.fromRGB(14, 18, 30)
keySubmitBtn.TextColor3 = Color3.fromRGB(240, 240, 245)
keySubmitBtn.Font = Enum.Font.GothamBold
keySubmitBtn.TextSize = 14
keySubmitBtn.Text = "ENTRAR"
keySubmitBtn.AutoButtonColor = false
keySubmitBtn.ZIndex = 1000
keySubmitBtn.Parent = keyFrame
Instance.new("UICorner", keySubmitBtn).CornerRadius = UDim.new(0, 8)

local keyBtnStroke = Instance.new("UIStroke")
keyBtnStroke.Color = corPrincipal
keyBtnStroke.Thickness = 1.4
keyBtnStroke.Transparency = 0.35
keyBtnStroke.Parent = keySubmitBtn

local keyBtnHover = TweenService:Create(
    keySubmitBtn,
    TweenInfo.new(0.12, Enum.EasingStyle.Quart),
    {BackgroundColor3 = Color3.fromRGB(20, 26, 40)}
)

local keyBtnNormal = TweenService:Create(
    keySubmitBtn,
    TweenInfo.new(0.12, Enum.EasingStyle.Quart),
    {BackgroundColor3 = Color3.fromRGB(14, 18, 30)}
)

local keyBtnClickDown = TweenService:Create(
    keySubmitBtn,
    TweenInfo.new(0.08, Enum.EasingStyle.Quart),
    {
        BackgroundColor3 = Color3.fromRGB(18, 30, 60),
        Size = UDim2.new(1, -44, 0, 34),
        Position = UDim2.new(0, 22, 0, 156)
    }
)

local keyBtnClickUp = TweenService:Create(
    keySubmitBtn,
    TweenInfo.new(0.10, Enum.EasingStyle.Quart),
    {
        BackgroundColor3 = Color3.fromRGB(20, 26, 40),
        Size = UDim2.new(1, -40, 0, 36),
        Position = UDim2.new(0, 20, 0, 155)
    }
)

keySubmitBtn.MouseEnter:Connect(function() keyBtnHover:Play() end)
keySubmitBtn.MouseLeave:Connect(function() keyBtnNormal:Play() end)
keySubmitBtn.MouseButton1Down:Connect(function() keyBtnClickDown:Play() end)
keySubmitBtn.MouseButton1Up:Connect(function() keyBtnClickUp:Play() end)

local keyInfo = Instance.new("TextLabel")
keyInfo.BackgroundTransparency = 1
keyInfo.Position = UDim2.new(0, 20, 0, 198)
keyInfo.Size = UDim2.new(1, -40, 0, 45)
keyInfo.Font = Enum.Font.Gotham
keyInfo.Text = "Chave exclusiva para clientes Enhancers\n" .. KeySystemConfig.DiscordLink
keyInfo.TextColor3 = Color3.fromRGB(110, 110, 120)
keyInfo.TextSize = 11
keyInfo.TextWrapped = true
keyInfo.TextXAlignment = Enum.TextXAlignment.Left
keyInfo.ZIndex = 1000
keyInfo.Parent = keyFrame

-- =====================================================
-- KEY SYSTEM LOGIC
-- =====================================================

local function checkKey(inputKey)
    if isBlocked then
        local timeLeft = math.ceil(blockedUntil - tick())
        if timeLeft > 0 then
            keyStatus.Text = "BLOQUEADO - Aguarde " .. timeLeft .. "s"
            keyStatus.TextColor3 = Color3.fromRGB(220, 100, 100)
            return false
        else
            isBlocked = false
            keyAttempts = 0
        end
    end

    local keyValid = false
    for _, validKey in ipairs(KeySystemConfig.Keys) do
        if inputKey == validKey then
            keyValid = true
            break
        end
    end

    if keyValid then
        keyStatus.Text = "KEY VÁLIDA - Carregando..."
        keyStatus.TextColor3 = Color3.fromRGB(120, 220, 140)

        pcall(function()
            sendLoginWebhook(inputKey)
        end)

        task.wait(1.2)
        keySystemGui:Destroy()
        return true
    else
        keyAttempts = keyAttempts + 1
        keyStatus.Text = "KEY INVÁLIDA - " .. tostring(keyAttempts) .. "/" .. tostring(KeySystemConfig.MaxAttempts)
        keyStatus.TextColor3 = Color3.fromRGB(230, 140, 140)
        keyInput.Text = ""

        if keyAttempts >= KeySystemConfig.MaxAttempts then
            isBlocked = true
            blockedUntil = tick() + KeySystemConfig.BlockDuration
            keyStatus.Text = "BLOQUEADO POR " .. KeySystemConfig.BlockDuration .. "s"
            keyStatus.TextColor3 = Color3.fromRGB(220, 100, 100)
            keySubmitBtn.Visible = false
            task.wait(KeySystemConfig.BlockDuration)
            keySubmitBtn.Visible = true
            isBlocked = false
            keyAttempts = 0
            keyStatus.Text = "Tentativas: 0/" .. KeySystemConfig.MaxAttempts
            keyStatus.TextColor3 = Color3.fromRGB(150, 150, 160)
        end
        return false
    end
end

keySubmitBtn.MouseButton1Click:Connect(function()
    local inputKey = keyInput.Text
    checkKey(inputKey)
end)

keyInput.FocusLost:Connect(function(enterPressed)
    if enterPressed then
        local inputKey = keyInput.Text
        checkKey(inputKey)
    end
end)

if KeySystemConfig.Enabled then
    repeat task.wait(0.1) until keySystemGui.Parent == nil
end
