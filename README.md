local library = loadstring(game:HttpGet(('https://pastebin.com/raw/FsJak6AT')))()
local w = library:CreateWindow("Naruto War Tycoon")
local b = w:CreateFolder("AutoFarm")
local f = w:CreateFolder("Mix")
local u = w:CreateFolder("Credits")

b:Toggle("AutoBuyButtons",function(bool)
    shared.toggle = bool
    AutoBuyButtons = bool
end)

f:Toggle("AntiAfk",function(bool)
    shared.toggle = bool
    AntiAfk = bool
end)

u:Button("maxgat5#8395",function()
    setclipboard("maxgat5#8395")
end)
 
u:Button("Discrod Server",function()
    setclipboard("https://discord.gg/K4txdRSVfq")
end)

if game:GetService("CoreGui"):FindFirstChild("PurchasePromptApp") then
    game:GetService("CoreGui").PurchasePromptApp:Destroy()
end

game:GetService('RunService').Stepped:connect(function()
    if AntiAfk == true then
        local bb=game:service'VirtualUser'
        bb:CaptureController()
        bb:ClickButton2(Vector2.new())
    end
end)

while wait() do
    if AutoBuyButtons == true then
        for i,v in pairs(game:GetService("Workspace").areas:GetChildren()) do
            if tostring(v.owner.Value) == tostring(game.Players.LocalPlayer.Name) then
                for i,v1 in pairs(v.unlockParts:GetDescendants()) do
                    if v1.ClassName == "ProximityPrompt" then
                        if v1.Parent.ClassName == "Part" then
                            if v1.Parent.BrickColor ~= BrickColor.new("New Yeller")  then
                                if AutoBuyButtons == true then
                                    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(v1.Parent.CFrame.Position + Vector3.new(0,0,0))
                                    wait(1)
                                    game:GetService("VirtualInputManager"):SendKeyEvent(true, "E", false, game)
                                    wait(1)
                                end
                            end
                        end
                    end
                end
            end
        end
    end
end
