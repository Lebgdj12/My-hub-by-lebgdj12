local ThunderScreen = Instance.new("ScreenGui")
local ThunderToggleUI = Instance.new("TextButton")
local ThunderCornerUI = Instance.new("UICorner")
local ThunderImageUI = Instance.new("ImageLabel")

        ThunderScreen.Name = "ThunderScreen"
        ThunderScreen.Parent = game.CoreGui
        ThunderScreen.ZIndexBehavior = Enum.ZIndexBehavior.Sibling

        ThunderToggleUI.Name = "ThunderToggleUI"
        ThunderToggleUI.Parent = ThunderScreen
        ThunderToggleUI.BackgroundColor3 = Color3.fromRGB(31,31,31)
        ThunderToggleUI.BorderSizePixel = 0
        ThunderToggleUI.Position = UDim2.new(0.120833337, 0, 0.0952890813, 0)
        ThunderToggleUI.Size = UDim2.new(0, 50, 0, 50)
        ThunderToggleUI.Font = Enum.Font.SourceSans
        ThunderToggleUI.Text = ""
        ThunderToggleUI.TextColor3 = Color3.fromRGB(0, 0, 0)
        ThunderToggleUI.TextSize = 14.000
        ThunderToggleUI.Draggable = true
        ThunderToggleUI.MouseButton1Click:Connect(function()
        game:GetService("VirtualInputManager"):SendKeyEvent(true,305,false,game)
        game:GetService("VirtualInputManager"):SendKeyEvent(false,305,false,game)
        end)

        ThunderCornerUI.Name = "ThunderCornerUI"
        ThunderCornerUI.Parent = ThunderToggleUI

        ThunderImageUI.Name = "MODILEMAGE"
        ThunderImageUI.Parent = ThunderToggleUI
        ThunderImageUI.BackgroundColor3 = Color3.fromRGB(192,192,192)
        ThunderImageUI.BackgroundTransparency = 1.000
        ThunderImageUI.BorderSizePixel = 0
        ThunderImageUI.Position = UDim2.new(0.0, 0, 0.0, 0)
        ThunderImageUI.Size = UDim2.new(0, 50, 0, 50)
        ThunderImageUI.Image = "http://www.roblox.com/asset/?id=12511245920"

local SOMEXHUB = {}
local UserInputService = game:GetService("UserInputService")
local TweenService = game:GetService("TweenService")
local RunService = game:GetService("RunService")
local LocalPlayer = game:GetService("Players").LocalPlayer
local Mouse = LocalPlayer:GetMouse()
local HttpService = game:GetService("HttpService")
local pfp
local user
local tag
local userinfo = {}

_G.Key = ""
_G.Discord = ""

if game.CoreGui:FindFirstChild(_G.Key .."," .. _G.Discord) then
   game.CoreGui:FindFirstChild(_G.Key .."," .. _G.Discord):Destroy()
end

pcall(function()
   userinfo = HttpService:JSONDecode(readfile(""));
end)

pfp = userinfo["pfp"] or "https://www.roblox.com/headshot-thumbnail/image?userId=".. game.Players.LocalPlayer.UserId .."&width=420&height=420&format=png"
user =  userinfo["user"] or game.Players.LocalPlayer.Name
tag = userinfo["tag"] or tostring(math.random(1,10))

local function SaveInfo()
   userinfo["pfp"] = pfp
   userinfo["user"] = user
   userinfo["tag"] = tag
   writefile("", HttpService:JSONEncode(userinfo));
end

local function MakeDraggable(topbarobject, object)
   local Dragging = nil
   local DragInput = nil
   local DragStart = nil
   local StartPosition = nil

   local function Update(input)
      local Delta = input.Position - DragStart
      local pos =
         UDim2.new(StartPosition.X.Scale,StartPosition.X.Offset + Delta.X,StartPosition.Y.Scale,StartPosition.Y.Offset + Delta.Y)
      local Tween = TweenService:Create(object, TweenInfo.new(0.2), {Position = pos})
      Tween:Play()
   end

   topbarobject.InputBegan:Connect(
      function(input)
         if input.UserInputType == Enum.UserInputType.MouseButton1 or input.UserInputType == Enum.UserInputType.Touch then
            Dragging = true
            DragStart = input.Position
            StartPosition = object.Position

            input.Changed:Connect(function()
               if input.UserInputState == Enum.UserInputState.End then
                  Dragging = false
               end
            end)
         end
      end)

   topbarobject.InputChanged:Connect(
      function(input)
         if
            input.UserInputType == Enum.UserInputType.MouseMovement or
               input.UserInputType == Enum.UserInputType.Touch
         then
            DragInput = input
         end
      end)

   UserInputService.InputChanged:Connect(
      function(input)
         if input == DragInput and Dragging then
            Update(input)
         end
      end)
end

local Update = {}
local pfp = "https://www.roblox.com/headshot-thumbnail/image?userId=".. game.Players.LocalPlayer.UserId .."&width=420&height=420&format=png"

function Update:Window(text,logo,keybind)
	local uihide = false
	local abc = false
	local logo = logo or 12511245920
	local currentpage = ""
	local keybind = keybind or Enum.KeyCode.RightControl
	local yoo = string.gsub(tostring(keybind),"Enum.KeyCode.","")
	
	local PADOXHUB = Instance.new("ScreenGui")
	PADOXHUB.Name = "ZEN HUB By King's Hub"
	PADOXHUB.Parent = game.CoreGui
	PADOXHUB.ZIndexBehavior = Enum.ZIndexBehavior.Sibling

	local Main = Instance.new("Frame")
	Main.Name = "Main"
	Main.Parent = PADOXHUB
	Main.ClipsDescendants = true
	Main.AnchorPoint = Vector2.new(0.5,0.5)
	Main.BackgroundColor3 = Color3.fromRGB(15, 15, 15)
	Main.Position = UDim2.new(0.5, 0, 0.5, 0)
	Main.Size = UDim2.new(0, 0, 0, 0)
	
	Main:TweenSize(UDim2.new(0, 530, 0, 330),"Out","Quad",0.4,true)

	local MCNR = Instance.new("UICorner")
	MCNR.Name = "MCNR"
	MCNR.Parent = Main

	local Top = Instance.new("Frame")
	Top.Name = "Top"
	Top.Parent = Main
	Top.BackgroundColor3 = Color3.fromRGB(20,20,20)
	Top.Size = UDim2.new(0, 530, 0, 63)

	local TCNR = Instance.new("UICorner")
	TCNR.Name = "TCNR"
	TCNR.Parent = Top

	local Logo = Instance.new("ImageLabel")
 Logo.Name = "Logo"
 Logo.Parent = Top
 Logo.BackgroundColor3 = Color3.fromRGB(224,224,224)
 Logo.BackgroundTransparency = 1.000
 Logo.Position = UDim2.new(-0.01, 0,-0.170, 0)
 Logo.Size = UDim2.new(0, 55,0, 45)
Logo.Image = "rbxassetid://12511245920"

	local Name = Instance.new("TextLabel")
	Name.Name = "Name"
	Name.Parent = Top
	Name.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
	Name.BackgroundTransparency = 1.000
	Name.Position = UDim2.new(0.0909756112, 0, 0, 0)
	Name.Size = UDim2.new(0, 61, 0, 27)
	Name.Font = Enum.Font.GothamSemibold
	Name.Text = text
	Name.TextColor3 = Color3.fromRGB(225, 225, 225)
	Name.TextSize = 17.000
	
	local Hub = Instance.new("TextLabel")
	Hub.Name = "Hub"
	Hub.Parent = Top
	Hub.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
	Hub.BackgroundTransparency = 1.000
	Hub.Position = UDim2.new(0, 150, 0, 0)
	Hub.Size = UDim2.new(0, 81, 0, 27)
	Hub.Font = Enum.Font.GothamSemibold
	Hub.Text = " Blox Fruit Update 18"
	Hub.TextColor3 = Color3.fromRGB(255, 255, 255)
	Hub.TextSize = 14.000
	Hub.TextXAlignment = Enum.TextXAlignment.Left

        spawn(function()
            while wait() do
                pcall(function()
                    wait(0.1) 
                    game:GetService('TweenService'):Create(
                        Name,TweenInfo.new(1,Enum.EasingStyle.Linear,Enum.EasingDirection.InOut),
                        {TextColor3 = Color3.fromRGB(255, 255, 255)}
                    ):Play() 
                    wait(.5)            
                    game:GetService('TweenService'):Create(
                        Name,TweenInfo.new(1,Enum.EasingStyle.Linear,Enum.EasingDirection.InOut),
                        {TextColor3 = Color3.fromRGB(224, 224, 224)}
                    ):Play() 
                    wait(.5)            
                    game:GetService('TweenService'):Create(
                        Name,TweenInfo.new(1,Enum.EasingStyle.Linear,Enum.EasingDirection.InOut),
                        {TextColor3 = Color3.fromRGB(192, 192, 192)}
                    ):Play() 
                    wait(.5)            
                    game:GetService('TweenService'):Create(
                        Name,TweenInfo.new(1,Enum.EasingStyle.Linear,Enum.EasingDirection.InOut),
                        {TextColor3 = Color3.fromRGB(160, 160, 160)}
                    ):Play() 
                    wait(.5)            
                    game:GetService('TweenService'):Create(
                        Name,TweenInfo.new(1,Enum.EasingStyle.Linear,Enum.EasingDirection.InOut),
                        {TextColor3 = Color3.fromRGB(128, 128, 128)}
                    ):Play() 
                    wait(.5)            
                    game:GetService('TweenService'):Create(
                        Name,TweenInfo.new(1,Enum.EasingStyle.Linear,Enum.EasingDirection.InOut),
                        {TextColor3 = Color3.fromRGB(96, 96, 96)}
                    ):Play() 
                    wait(.5)            
                    game:GetService('TweenService'):Create(
                        Name,TweenInfo.new(1,Enum.EasingStyle.Linear,Enum.EasingDirection.InOut),
                        {TextColor3 = Color3.fromRGB(64, 64, 64)}
                    ):Play() 
                    wait(.5)            
                    game:GetService('TweenService'):Create(
                        Name,TweenInfo.new(1,Enum.EasingStyle.Linear,Enum.EasingDirection.InOut),
                        {TextColor3 = Color3.fromRGB(32, 32, 32)}
                    ):Play() 
                    wait(.5)
                end)
            end
        end)

	local ver1 = Instance.new("TextLabel")
	ver1.Name = "ver"
	ver1.Parent = Top
	ver1.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
	ver1.BackgroundTransparency = 1.000
	ver1.Position = UDim2.new(0.640, 0, 0, 0)
	ver1.Size = UDim2.new(0, 80, 0, 27)
	ver1.Font = Enum.Font.GothamSemibold
	ver1.Text = "N/A"
	ver1.TextColor3 = Color3.fromRGB(255,255,255)
	ver1.TextSize = 13.000
	ver1.TextXAlignment = Enum.TextXAlignment.Left
    task.spawn(function()
	  while wait() do
	   ver1.Text = "[Time] : "..os.date("%H")..":"..os.date("%M")..":"..os.date("%S")
	end
end)

	local Ping = Instance.new("TextLabel")
	Ping.Name = "Ping"
	Ping.Parent = Top
	Ping.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
	Ping.BackgroundTransparency = 1.000
	Ping.Position = UDim2.new(0, 350,0, 30)
	Ping.Size = UDim2.new(0, 130, 0.01, 25)
	Ping.Font = Enum.Font.GothamSemibold
	Ping.Text = "N/A"
	Ping.TextColor3 = Color3.fromRGB(255,255,255)
	Ping.TextSize = 13.000
	Ping.TextXAlignment = Enum.TextXAlignment.Left

	local Fps = Instance.new("TextLabel")
	Fps.Name = "Fps"
	Fps.Parent = Top
	Fps.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
	Fps.BackgroundTransparency = 1.000
	Fps.Position = UDim2.new(0.850, 0,0, 0)
	Fps.Size = UDim2.new(0, 81, 0, 27)
	Fps.Font = Enum.Font.GothamSemibold
	Fps.Text = "N/A"
	Fps.TextColor3 = Color3.fromRGB(255,255,255)
	Fps.TextSize = 13.000
	Fps.TextXAlignment = Enum.TextXAlignment.Left

local Fps = Instance.new('LocalScript', Fps)
local RunService = game:GetService("RunService")
RunService.RenderStepped:Connect(function(frame)
Fps.Parent.Text = ("[FPS] : "..math.round(1/frame)) 
end)

local Ping = Instance.new('LocalScript', Ping)
local RunService = game:GetService("RunService")
RunService.RenderStepped:Connect(function(ping) 
Ping.Parent.Text = ("[Ping] : " ..game:GetService("Stats").Network.ServerStatsItem["Data Ping"]:GetValueString(math.round(2/ping)))
end)
    local User = Instance.new("Frame")
    User.Name = "User"
    User.Parent = Top
    User.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
    User.BackgroundTransparency = 1.000
    User.Position = UDim2.new(0, 0,0, 25)
    User.Size = UDim2.new(0, 125, 0, 40)
    
    local UserText = Instance.new("TextLabel")
    UserText.Name = "UserText"
    UserText.Parent = User
    UserText.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
    UserText.BackgroundTransparency = 1.000
    UserText.Position = UDim2.new(0.4, 0,0, 10)
	UserText.TextColor3 = Color3.fromRGB(255, 255, 255)
    UserText.Size = UDim2.new(0, 80, 0, 20)
    UserText.Font = Enum.Font.GothamSemibold
    UserText.Text = tostring(game.Players.LocalPlayer.Name)
    UserText.TextScaled = true
    UserText.TextSize = 17.000
    UserText.TextWrapped = true
    UserText.TextXAlignment = Enum.TextXAlignment.Left
    
    local UITextSizeConstraint = Instance.new("UITextSizeConstraint")
    UITextSizeConstraint.Parent = UserText
    UITextSizeConstraint.MaxTextSize = 17
    
    local UserImage = Instance.new("ImageLabel")
    UserImage.Name = "UserImage"
    UserImage.Parent = User
    UserImage.BackgroundTransparency = 0
    UserImage.BackgroundColor3 = Color3.fromRGB(225, 225, 225)
    UserImage.Position = UDim2.new(0, 10, 0, 9)
    UserImage.Size = UDim2.new(0, 25, 0, 25)
    UserImage.Image = "https://www.roblox.com/headshot-thumbnail/image?userId="..game.Players.LocalPlayer.UserId.."&width=420&height=420&format=png"
    local UserImageCorner = Instance.new("UICorner")
   UserImageCorner.CornerRadius = UDim.new(0, 100)
    UserImageCorner.Name = "UserImageCorner"
    UserImageCorner.Parent = UserImage
    
	local timecock = Instance.new("TextButton")
	timecock.Parent = Top
	timecock.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
	timecock.BackgroundTransparency = 1
	timecock.BorderSizePixel = 0
	timecock.Position = UDim2.new(0, 240,0, 44)
	timecock.AnchorPoint = Vector2.new(0.5, 0.5)
	timecock.Size = UDim2.new(0, 130, 0.01, 25)
	timecock.Font = Enum.Font.GothamSemibold
	timecock.Text = "N/Q"
	timecock.TextColor3 = Color3.fromRGB(255, 255, 255)
	timecock.TextSize = 13.000

    function setTime()
        local GameTime = math.floor(workspace.DistributedGameTime+0.5)
        local Hour = math.floor(GameTime/(60^2))%24
        local Minute = math.floor(GameTime/(60^1))%60
        local Second = math.floor(GameTime/(60^0))%60
        timecock.Text = ("Hr(s) : "..Hour.." Min(s) : "..Minute.." Sec(s) : "..Second)
    end
    
    spawn(function()
        while task.wait() do
            pcall(function()
                setTime()
            end)
        end
    end)
    
 local Tab = Instance.new("Frame")
 Tab.Name = "Tab"
 Tab.Parent = Main
 Tab.BackgroundColor3 = Color3.fromRGB(35, 35, 35)
 Tab.Position = UDim2.new(0, 5, 0, 60)
 --Tab.CornerRadius = UDim.new(0,5)
 Tab.Size = UDim2.new(0, 0, 0, 0)
 --Tab.Size = UDim2.new(0, 150, 0, 365)
 
 --local TabCorner = Instance.new("UICorner")
 local TabCorner = Instance.new("UIListLayout")
 TabCorner.Name = "TabCorner"
 TabCorner.Parent = Tab
 TabCorner.SortOrder = Enum.SortOrder.LayoutOrder
 TabCorner.Padding = UDim.new(0, 15)
 
 local TCNR = Instance.new("UICorner")
 TCNR.Name = "TCNR"
 TCNR.Parent = Tab
 
 local ScrollTab = Instance.new("ScrollingFrame")
 ScrollTab.Name = "ScrollTab"
 ScrollTab.Parent = Tab
 ScrollTab.Active = true
 ScrollTab.BackgroundColor3 = Color3.fromRGB(224,224,224)
 ScrollTab.BackgroundTransparency = 1.000
 ScrollTab.Size = UDim2.new(0, 133, 0, 250)
 ScrollTab.CanvasSize = UDim2.new(0, 0, 0, 0)
 ScrollTab.ScrollBarThickness = 0
 
 local PLL = Instance.new("UIListLayout")
 PLL.Name = "PLL"
 PLL.Parent = ScrollTab
 PLL.SortOrder = Enum.SortOrder.LayoutOrder
 PLL.Padding = UDim.new(0, 15)
 
 local PPD = Instance.new("UIPadding")
 PPD.Name = "PPD"
 PPD.Parent = ScrollTab
 PPD.PaddingLeft = UDim.new(0, 10)
 PPD.PaddingTop = UDim.new(0, 10)
 
 local Page = Instance.new("Frame")
 Page.Name = "Page"
 Page.Parent = Main
 Page.BackgroundColor3 = Color3.fromRGB(35,35,35)
 Page.Position = UDim2.new(0.26, 0, 0.211050003, 0)
 Page.BackgroundTransparency = 1
 Page.Size = UDim2.new(0, 388, 0, 248)
 
 local PCNR = Instance.new("UICorner")
 PCNR.Name = "PCNR"
 PCNR.Parent = Page
 
 local MainPage = Instance.new("Frame")
 MainPage.Name = "MainPage"
 MainPage.Parent = Page
 MainPage.ClipsDescendants = true
 MainPage.BackgroundColor3 = Color3.fromRGB(224,224,224)
 MainPage.BackgroundTransparency = 1.000
 MainPage.Size = UDim2.new(0, 400, 0, 316)
 
 local PageList = Instance.new("Folder")
 PageList.Name = "PageList"
 PageList.Parent = MainPage
 
 local UIPageLayout = Instance.new("UIPageLayout")
 
 UIPageLayout.Parent = PageList
 UIPageLayout.SortOrder = Enum.SortOrder.LayoutOrder
 UIPageLayout.EasingDirection = Enum.EasingDirection.InOut
 UIPageLayout.EasingStyle = Enum.EasingStyle.Quad
 UIPageLayout.FillDirection = Enum.FillDirection.Vertical
 UIPageLayout.Padding = UDim.new(0, 15)
 UIPageLayout.TweenTime = 0.400
 UIPageLayout.GamepadInputEnabled = false
 UIPageLayout.ScrollWheelInputEnabled = false
 UIPageLayout.TouchInputEnabled = false
 
 MakeDraggable(Top,Main)
 
 UserInputService.InputBegan:Connect(function(input)
  if input.KeyCode == Enum.KeyCode[yoo] then
  if uihide == false then
  uihide = true
  Main:TweenSize(UDim2.new(0, 0, 0, 0),"In","Quad",0.4,true)
  else
   uihide = false
  Main:TweenSize(UDim2.new(0, 530, 0, 330),"Out","Quad",0.5,true)
  end
  end
  end)
 local uitab = {}
 
 function uitab:Tab(text,icon)
 local TabButton = Instance.new("TextButton")
 local TabImage = Instance.new("ImageLabel")
 TabButton.Parent = ScrollTab
 TabButton.Name = text.."Server"
 TabButton.Text = text
 TabButton.BackgroundColor3 = Color3.fromRGB(224,224,224)
 TabButton.BackgroundTransparency = 1.000
 TabButton.Size = UDim2.new(0, 125, 0, 23)
 TabButton.Font = Enum.Font.GothamSemibold
 TabButton.TextColor3 = Color3.fromRGB(225, 225, 225)
 TabButton.TextSize = 11.000
 TabButton.TextTransparency = 0.100
 
 local TabFrame = Instance.new("Frame")
 local UICornerFrame = Instance.new("UICorner")
 TabFrame.Name = "TabFrame"
 TabFrame.Parent = TabButton
 TabFrame.ClipsDescendants = true
 --TabFrame.Position = UDim2.new(0, 1, 0.1, 2)
 TabFrame.BackgroundColor3 = Color3.fromRGB(31, 31, 31)
 TabFrame.BackgroundTransparency = 0.500
 TabFrame.Size = UDim2.new(0, 118, 0.1, 23)
 UICornerFrame.CornerRadius = UDim.new(0,0)
 
local postog = Instance.new("UIStroke")
 
 postog.Name = "postog"
 postog.Parent = TabFrame
 postog.ApplyStrokeMode = Enum.ApplyStrokeMode.Border
 postog.Color = Color3.fromRGB(255,255,255)
 postog.LineJoinMode = Enum.LineJoinMode.Round
 postog.Thickness = 1
 postog.Transparency = 0.8
 postog.Enabled = true
 postog.Archivable = true
 
 UICornerFrame.Parent = TabFrame
 
 TabImage.Name = text or "TabImage"
 TabImage.Parent = TabFrame
 TabImage.BackgroundColor3 = Color3.fromRGB(225, 225, 225)
 TabImage.BackgroundTransparency = 1.000
 TabImage.Position = UDim2.new(0, 0, 0, 0)
 TabImage.Size = UDim2.new(0, 20, 0, 20)
 TabImage.Image = "rbxassetid://"..tostring(icon)
 TabImage.ImageColor3 = Color3.fromRGB(225, 225, 225)
 
 local MainFramePage = Instance.new("ScrollingFrame")
 MainFramePage.Name = text.."_Page"
 MainFramePage.Parent = PageList
 MainFramePage.Active = true
 MainFramePage.BackgroundColor3 = Color3.fromRGB(224,224,224)
 MainFramePage.BackgroundTransparency = 1.000
 MainFramePage.BorderSizePixel = 0
 MainFramePage.Size = UDim2.new(0, 400, 0, 245)
 MainFramePage.CanvasSize = UDim2.new(0, 0, 0, 0)
 MainFramePage.ScrollBarThickness = 4
 
 local UIPadding = Instance.new("UIPadding")
 local UIListLayout = Instance.new("UIListLayout")
 
 UIPadding.Parent = MainFramePage
 UIPadding.PaddingLeft = UDim.new(0, 10)
 UIPadding.PaddingTop = UDim.new(0, 10)
 
 UIListLayout.Padding = UDim.new(0,15)
 UIListLayout.Parent = MainFramePage
 UIListLayout.SortOrder = Enum.SortOrder.LayoutOrder
 
  spawn(function()

        while wait() do

            pcall(function()

                wait(0.1) 

                game:GetService('TweenService'):Create(

                    postog,TweenInfo.new(1,Enum.EasingStyle.Linear,Enum.EasingDirection.InOut),

                    {Color = Color3.fromRGB(255, 0, 0)}

                ):Play() 

                wait(.5)            

                game:GetService('TweenService'):Create(

                    postog,TweenInfo.new(1,Enum.EasingStyle.Linear,Enum.EasingDirection.InOut),

                    {Color = Color3.fromRGB(255, 155, 0)}

                ):Play() 

                wait(.5)            

                game:GetService('TweenService'):Create(

                    postog,TweenInfo.new(1,Enum.EasingStyle.Linear,Enum.EasingDirection.InOut),

                    {Color = Color3.fromRGB(255, 255, 0)}

                ):Play() 

                wait(.5)            

                game:GetService('TweenService'):Create(

                    postog,TweenInfo.new(1,Enum.EasingStyle.Linear,Enum.EasingDirection.InOut),

                    {Color = Color3.fromRGB(0, 255, 0)}

                ):Play() 

                wait(.5)            

                game:GetService('TweenService'):Create(

                    postog,TweenInfo.new(1,Enum.EasingStyle.Linear,Enum.EasingDirection.InOut),

                    {Color = Color3.fromRGB(0, 255, 255)}

                ):Play() 

                wait(.5)            

                game:GetService('TweenService'):Create(

                    postog,TweenInfo.new(1,Enum.EasingStyle.Linear,Enum.EasingDirection.InOut),

                    {Color = Color3.fromRGB(0, 155, 255)}

                ):Play() 

                wait(.5)            

                game:GetService('TweenService'):Create(

                    postog,TweenInfo.new(1,Enum.EasingStyle.Linear,Enum.EasingDirection.InOut),

                    {Color = Color3.fromRGB(255, 0, 255)}

                ):Play() 

                wait(.5)            

                game:GetService('TweenService'):Create(

                    postog,TweenInfo.new(1,Enum.EasingStyle.Linear,Enum.EasingDirection.InOut),

                    {Color = Color3.fromRGB(255, 0, 155)}

                ):Play() 

                wait(.5)
                
            end)

        end

    end)
 
 TabButton.MouseButton1Click:Connect(function()
  for i,v in next, ScrollTab:GetChildren() do
  if v:IsA("TextButton") then
  TweenService:Create(
   v,
   TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
   {
    TextTransparency = 0.5
   }
  ):Play()
  end
  TweenService:Create(
   TabButton,
   TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
   {
    TextTransparency = 0
   }
  ):Play()
  end
  for i,v in next, PageList:GetChildren() do
  currentpage = string.gsub(TabButton.Name,"Server","").."_Page"
  if v.Name == currentpage then
  UIPageLayout:JumpTo(v)
  end
  end
  end)
 
 if abc == false then
 for i,v in next, ScrollTab:GetChildren() do
 if v:IsA("TextButton") then
 TweenService:Create(
  v,
  TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
  {
   TextTransparency = 0.5
  }
 ):Play()
 end
 TweenService:Create(
  TabButton,
  TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
  {
   TextTransparency = 0
  }
 ):Play()
 end
 UIPageLayout:JumpToIndex(1)
 abc = true
 end
 
 game:GetService("RunService").Stepped:Connect(function()
  pcall(function()
   MainFramePage.CanvasSize = UDim2.new(0,0,0,UIListLayout.AbsoluteContentSize.Y + 20)
   ScrollTab.CanvasSize = UDim2.new(0,0,0,PLL.AbsoluteContentSize.Y + 20)
   end)
 end)

local main = {}
 function main:Button(text,callback)
 local Button = Instance.new("Frame")
 local UICorner = Instance.new("UICorner")
 local TextBtn = Instance.new("TextButton")
 local UICorner_2 = Instance.new("UICorner")
 local Black = Instance.new("Frame")
 local UICorner_3 = Instance.new("UICorner")
 
 Button.Name = "Button"
 Button.Parent = MainFramePage
 Button.BackgroundColor3 = Color3.fromRGB(225, 225, 225)
 Button.BackgroundTransparency = 1
 Button.Size = UDim2.new(0, 370, 0, 31)
 
 UICorner.CornerRadius = UDim.new(0, 5)
 UICorner.Parent = Button
 
 TextBtn.Name = "TextBtn"
 TextBtn.Parent = Button
 TextBtn.BackgroundColor3 = Color3.fromRGB(244,244,244)
 TextBtn.BackgroundTransparency = 0.500
 TextBtn.Position = UDim2.new(0, 1, 0, 1)
 TextBtn.Size = UDim2.new(0, 368, 0, 29)
 TextBtn.AutoButtonColor = false
 TextBtn.Font = Enum.Font.GothamSemibold
 TextBtn.Text = text
 TextBtn.TextColor3 = Color3.fromRGB(0, 0, 0)
 TextBtn.TextSize = 12.000
 
 UICorner_2.CornerRadius = UDim.new(0, 5)
 UICorner_2.Parent = TextBtn
 
 Black.Name = "Black"
 Black.Parent = Button
 Black.BackgroundColor3 = Color3.fromRGB(0, 0, 0)
 Black.BackgroundTransparency = 1.000
 Black.BorderSizePixel = 0
 Black.Position = UDim2.new(0, 1, 0, 1)
 Black.Size = UDim2.new(0, 370, 0, 29)
 
 UICorner_3.CornerRadius = UDim.new(0, 5)
 UICorner_3.Parent = Black
 
 
 
 TextBtn.MouseEnter:Connect(function()
  TweenService:Create(
   Black,
   TweenInfo.new(0.4,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
   {
    BackgroundTransparency = 0.7
   }
  ):Play()
  end)
 TextBtn.MouseLeave:Connect(function()
  TweenService:Create(
   Black,
   TweenInfo.new(0.4,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
   {
    BackgroundTransparency = 1
   }
  ):Play()
  end)
 TextBtn.MouseButton1Click:Connect(function()
  TextBtn.TextSize = 0
  TweenService:Create(
   TextBtn,
   TweenInfo.new(0.4,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
   {
    TextSize = 12
   }
  ):Play()
  callback()
  end)
 end
 function main:Toggle(TogInfo,default,callback)
 local toggle = false
 local CheckFrame = Instance.new("Frame")
 local CheckFrame2 = Instance.new("Frame")
 local UIListLayout = Instance.new("UIListLayout")
 local UICorner = Instance.new("UICorner")
 local ImageLabel = Instance.new("ImageLabel")
 local Space = Instance.new("TextLabel")
 local Title = Instance.new("TextLabel")
 local ImageButton = Instance.new("ImageButton")
 
 -- Prop --
 CheckFrame.Name = TogInfo or "CheckFrame"
 CheckFrame.Parent = MainFramePage
 CheckFrame.BackgroundColor3 = Color3.fromRGB(150, 150, 150)
 CheckFrame.BackgroundTransparency = 1.000
 CheckFrame.BorderSizePixel = 0
 CheckFrame.Size = UDim2.new(0, 38, 0, 30)
 
 CheckFrame2.Name = "CheckFrame2"
 CheckFrame2.Parent = CheckFrame
 CheckFrame2.BackgroundColor3 = Color3.fromRGB(30,30,30)
 CheckFrame2.BackgroundTransparency = 1
 CheckFrame2.BorderSizePixel = 0
 CheckFrame2.Position = UDim2.new(0, 3, 0, 0)
 CheckFrame2.Size = UDim2.new(0, 370, 0, 30)

local postog12 = Instance.new("UIStroke")
 
 postog12.Name = "UIStroke"
 postog12.Parent = CheckFrame2
 postog12.ApplyStrokeMode = Enum.ApplyStrokeMode.Border
 postog12.Color = Color3.fromRGB(255,255,255)
 postog12.LineJoinMode = Enum.LineJoinMode.Round
 postog12.Thickness = 1
 postog12.Transparency = 0.8
 postog12.Enabled = true
 postog12.Archivable = true
 
 
 UICorner.Parent = CheckFrame2
 UICorner.CornerRadius = UDim.new(0, 0)
 
 ImageLabel.Name = "ImageLabel"
 ImageLabel.Parent = CheckFrame2
 ImageLabel.BackgroundColor3 = Color3.fromRGB(150, 150, 150)
 ImageLabel.BackgroundTransparency = 1.000
 ImageLabel.BorderSizePixel = 0
 ImageLabel.Position = UDim2.new(-0.018, 0,-0.252, 0)
 ImageLabel.Size = UDim2.new(0, 45,0, 45)
 ImageLabel.Image = "rbxassetid://12511245920"
 ImageLabel.ImageColor3 = Color3.fromRGB(224,224,224)
 
 Space.Name = "Space"
 Space.Parent = CheckFrame2
 Space.BackgroundColor3 = Color3.fromRGB(150, 150, 150)
 Space.BackgroundTransparency = 1.000
 Space.Position = UDim2.new(0, 30, 0, 0)
 Space.Size = UDim2.new(0, 15, 0, 30)
 Space.Font = Enum.Font.GothamSemibold
 Space.Text = "|"
 Space.TextSize = 12.000
 Space.TextColor3 = Color3.fromRGB(255,225,225)
 Space.TextXAlignment = Enum.TextXAlignment.Center
 
 Title.Name = "Title"
 Title.Parent = CheckFrame2
 Title.BackgroundColor3 = Color3.fromRGB(150, 150, 150)
 Title.BackgroundTransparency = 1.000
 Title.Position = UDim2.new(0, 50, 0, 0)
 Title.Size = UDim2.new(0, 280, 0, 30)
 Title.Font = Enum.Font.GothamSemibold
 Title.Text = TogInfo or "checkBox Title"
 Title.TextColor3 = Color3.fromRGB(224,224,224)
 Title.TextSize = 12.000
 Title.TextXAlignment = Enum.TextXAlignment.Left
 
 ImageButton.Name = "ImageButton"
 ImageButton.Parent = CheckFrame2
 ImageButton.BackgroundColor3 = Color3.fromRGB(224,224,224)
 ImageButton.BackgroundTransparency = 1.000
 ImageButton.Position = UDim2.new(0, 340, 0, 4)
 ImageButton.Size = UDim2.new(0, 23, 0, 23)
 ImageButton.ZIndex = 2
 ImageButton.Image = "rbxassetid://3926311105"
 ImageButton.ImageColor3 = Color3.fromRGB(224,224,224)
 ImageButton.ImageRectOffset = Vector2.new(940, 784)
 ImageButton.ImageRectSize = Vector2.new(48, 48)
 
 -- Toggle Script --
 
 if default == true then
 ImageButton.ImageRectOffset = Vector2.new(4, 836)
 game.TweenService:Create(ImageButton, TweenInfo.new(0.08, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut),
  {
   ImageColor3 = Color3.fromRGB(255,225,225)}
 ):Play()
 toggle = not toggle
 pcall(callback, toggle)
 end
 
 ImageButton.MouseButton1Click:Connect(function()
  if toggle == false then
  game.TweenService:Create(ImageButton, TweenInfo.new(0.08, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut),
   {
    ImageColor3 = Color3.fromRGB(255,225,225)}
  ):Play()
  ImageButton.ImageRectOffset = Vector2.new(4, 836)
  else
   game.TweenService:Create(ImageButton, TweenInfo.new(0.08, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut),
   {
    ImageColor3 = Color3.fromRGB(224,224,224)}
  ):Play()
  ImageButton.ImageRectOffset = Vector2.new(940, 784)
  end
  toggle = not toggle
  pcall(callback, toggle)
  end)
 end

 
function main:Dropdown(text,option,callback)
 local isdropping = false
 local Dropdown = Instance.new("Frame")
 local UICorner = Instance.new("UICorner")
 local DropTitle = Instance.new("TextLabel")
 local DropScroll = Instance.new("ScrollingFrame")
 local UIListLayout = Instance.new("UIListLayout")
 local UIPadding = Instance.new("UIPadding")
 local DropButton = Instance.new("TextButton")
 local DropImage = Instance.new("ImageLabel")
 local posto1 = Instance.new("UIStroke")
 
 Dropdown.Name = "Dropdown"
 Dropdown.Parent = MainFramePage
 Dropdown.BackgroundColor3 = Color3.fromRGB(28,28,28)
 Dropdown.BackgroundTransparency = 1
 Dropdown.ClipsDescendants = true
 Dropdown.Size = UDim2.new(0, 370, 0, 31)
 
 posto1.Name = "posto"
 posto1.Parent = Dropdown
 posto1.ApplyStrokeMode = Enum.ApplyStrokeMode.Border
 posto1.Color = Color3.fromRGB(255,255,255)
 posto1.LineJoinMode = Enum.LineJoinMode.Round
 posto1.Thickness = 1
 posto1.Transparency = 0.8
 posto1.Enabled = true
 posto1.Archivable = true
 
 UICorner.CornerRadius = UDim.new(0, 0)
 UICorner.Parent = Dropdown
 
 DropTitle.Name = "DropTitle"
 DropTitle.Parent = Dropdown
 DropTitle.BackgroundColor3 = Color3.fromRGB(224,224,224)
 DropTitle.BackgroundTransparency = 1.000
 DropTitle.Size = UDim2.new(0, 370, 0, 31)
 DropTitle.Font = Enum.Font.GothamSemibold
 DropTitle.Text = text.. " : "
 DropTitle.TextColor3 = Color3.fromRGB(225, 225, 225)
 DropTitle.TextSize = 12.000
 
 DropScroll.Name = "DropScroll"
 DropScroll.Parent = DropTitle
 DropScroll.Active = true
 DropScroll.BackgroundColor3 = Color3.fromRGB(224,224,224)
 DropScroll.BackgroundTransparency = 1.000
 DropScroll.BorderSizePixel = 0
 DropScroll.Position = UDim2.new(0, 0, 0, 31)
 DropScroll.Size = UDim2.new(0, 370, 0, 100)
 DropScroll.CanvasSize = UDim2.new(0, 0, 0, 0)
 DropScroll.ScrollBarThickness = 3
 
 UIListLayout.Parent = DropScroll
 UIListLayout.SortOrder = Enum.SortOrder.LayoutOrder
 UIListLayout.Padding = UDim.new(0, 5)
 
 UIPadding.Parent = DropScroll
 UIPadding.PaddingLeft = UDim.new(0, 5)
 UIPadding.PaddingTop = UDim.new(0, 5)
 
 DropImage.Name = "DropImage"
 DropImage.Parent = Dropdown
 DropImage.BackgroundColor3 = Color3.fromRGB(224,224,224)
 DropImage.BackgroundTransparency = 1.000
 DropImage.Position = UDim2.new(0, 320, 0, 6)
 DropImage.Rotation = 180.000
 DropImage.Size = UDim2.new(0, 20, 0, 20)
 DropImage.Image = "rbxassetid://6031090990"
 
 DropButton.Name = "DropButton"
 DropButton.Parent = Dropdown
 DropButton.BackgroundColor3 = Color3.fromRGB(224,224,224)
 DropButton.BackgroundTransparency = 1.000
 DropButton.Size = UDim2.new(0, 370, 0, 31)
 DropButton.Font = Enum.Font.SourceSans
 DropButton.Text = ""
 DropButton.TextColor3 = Color3.fromRGB(0, 0, 0)
 DropButton.TextSize = 14.000
 
 for i,v in next,option do
 local Item = Instance.new("TextButton")
 
 Item.Name = "Item"
 Item.Parent = DropScroll
 Item.BackgroundColor3 = Color3.fromRGB(224,224,224)
 Item.BackgroundTransparency = 1.000
 Item.Size = UDim2.new(0, 370, 0, 26)
 Item.Font = Enum.Font.GothamSemibold
 Item.Text = tostring(v)
 Item.TextColor3 = Color3.fromRGB(225, 225, 225)
 Item.TextSize = 13.000
 Item.TextTransparency = 0.500
 
 Item.MouseEnter:Connect(function()
  TweenService:Create(
   Item,
   TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
   {
    TextTransparency = 0
   }
  ):Play()
  end)
 
 Item.MouseLeave:Connect(function()
  TweenService:Create(
   Item,
   TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
   {
    TextTransparency = 0.5
   }
  ):Play()
  end)
 
 Item.MouseButton1Click:Connect(function()
  isdropping = false
  Dropdown:TweenSize(UDim2.new(0,370,0,31),"Out","Quad",0.3,true)
  TweenService:Create(
   DropImage,
   TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
   {
    Rotation = 180
   }
  ):Play()
  callback(Item.Text)
  DropTitle.Text = text.." : "..Item.Text
  end)
 end
 
 DropScroll.CanvasSize = UDim2.new(0,0,0,UIListLayout.AbsoluteContentSize.Y + 10)
 
 DropButton.MouseButton1Click:Connect(function()
  if isdropping == false then
  isdropping = true
  Dropdown:TweenSize(UDim2.new(0,370,0,131),"Out","Quad",0.3,true)
  TweenService:Create(
   DropImage,
   TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
   {
    Rotation = 0
   }
  ):Play()
  else
   isdropping = false
  Dropdown:TweenSize(UDim2.new(0,370,0,31),"Out","Quad",0.3,true)
  TweenService:Create(
   DropImage,
   TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
   {
    Rotation = 180
   }
  ):Play()
  end
  end)
 
 local dropfunc = {}
 function dropfunc:Add(t)
 local Item = Instance.new("TextButton")
 Item.Name = "Item"
 Item.Parent = DropScroll
 Item.BackgroundColor3 = Color3.fromRGB(224,224,224)
 Item.BackgroundTransparency = 1.000
 Item.Size = UDim2.new(0, 370, 0, 26)
 Item.Font = Enum.Font.GothamSemibold
 Item.Text = tostring(t)
 Item.TextColor3 = Color3.fromRGB(225, 225, 225)
 Item.TextSize = 13.000
 Item.TextTransparency = 0.500
 
 Item.MouseEnter:Connect(function()
  TweenService:Create(
   Item,
   TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
   {
    TextTransparency = 0
   }
  ):Play()
  end)
 
 Item.MouseLeave:Connect(function()
  TweenService:Create(
   Item,
   TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
   {
    TextTransparency = 0.5
   }
  ):Play()
  end)
 
 Item.MouseButton1Click:Connect(function()
  isdropping = false
  Dropdown:TweenSize(UDim2.new(0,370,0,31),"Out","Quad",0.3,true)
  TweenService:Create(
   DropImage,
   TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
   {
    Rotation = 180
   }
  ):Play()
  callback(Item.Text)
  DropTitle.Text = text.." : "..Item.Text
  end)
 end
 function dropfunc:Clear()
 DropTitle.Text = tostring(text).." : "
 isdropping = false
 Dropdown:TweenSize(UDim2.new(0,370,0,31),"Out","Quad",0.3,true)
 TweenService:Create(
  DropImage,
  TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
  {
   Rotation = 180
  }
 ):Play()
 for i,v in next, DropScroll:GetChildren() do
 if v:IsA("TextButton") then
 v:Destroy()
 end
 end
 end
 return dropfunc
 end
 
function main:Slider1(slidertitle, min, max, start, callback)
local slider1func = {}
local SliderFrame = Instance.new("Frame")
local SliderFrame_2 = Instance.new("Frame")
local UIStroke = Instance.new("UIStroke")
local UICorner = Instance.new("UICorner")
local ImageLabel = Instance.new("ImageLabel")
local Space = Instance.new("TextLabel")
local Title = Instance.new("TextLabel")
local SliderInput = Instance.new("Frame")
local SliderButton = Instance.new("Frame")
local SliderCount = Instance.new("Frame")
local SliderCorner = Instance.new("UICorner")
local SliderCorner2 = Instance.new("UICorner")
local BoxFrame = Instance.new("Frame")
local SliderBox = Instance.new("TextBox")
local SliderStroke = Instance.new("UIStroke")
local Title_2 = Instance.new("TextButton")
local UICorner_2 = Instance.new("UICorner")
local UICorner_3 = Instance.new("UICorner")

-- Prop --
SliderFrame.Name = slidertitle or "SliderFrame"
SliderFrame.Parent = MainFramePage
SliderFrame.BackgroundColor3 = Color3.fromRGB(28,28,28)
SliderFrame.BackgroundTransparency = 1.000
SliderFrame.BorderSizePixel = 0
SliderFrame.Size = UDim2.new(0, 355, 0, 55)

SliderFrame_2.Name = "SliderFrame_2"
SliderFrame_2.Parent = SliderFrame
SliderFrame_2.BackgroundColor3 = Color3.fromRGB(28,28,28)
SliderFrame_2.BackgroundTransparency = 1
SliderFrame_2.BorderSizePixel = 0
SliderFrame_2.Position = UDim2.new(0, 3, 0, 0)
SliderFrame_2.Size = UDim2.new(0, 370, 0, 55)

UIStroke.Name = "UIStroke"
UIStroke.Parent = SliderFrame_2
UIStroke.ApplyStrokeMode = Enum.ApplyStrokeMode.Border
UIStroke.Color = Color3.fromRGB(255,255,255)
UIStroke.LineJoinMode = Enum.LineJoinMode.Round
UIStroke.Thickness = 1
UIStroke.Transparency = 0.8
UIStroke.Enabled = true
UIStroke.Archivable = true

UICorner.Parent = SliderFrame_2
UICorner.CornerRadius = UDim.new(0, 0)

ImageLabel.Name = "ImageLabel"
ImageLabel.Parent = SliderFrame_2
ImageLabel.BackgroundColor3 = Color3.fromRGB(150, 150, 150)
ImageLabel.BackgroundTransparency = 1.000
ImageLabel.BorderSizePixel = 0
ImageLabel.Position = UDim2.new(0, -5, 0, -5)
ImageLabel.Size = UDim2.new(0, 45, 0, 45)
ImageLabel.Image = "rbxassetid://12511245920"
ImageLabel.ImageColor3 = Color3.fromRGB(224,224,224)

Space.Name = "Space"
Space.Parent = SliderFrame_2
Space.BackgroundColor3 = Color3.fromRGB(150, 150, 150)
Space.BackgroundTransparency = 1.000
Space.Position = UDim2.new(0, 30, 0, 0)
Space.Size = UDim2.new(0, 15, 0, 30)
Space.Font = Enum.Font.GothamSemibold
Space.Text = "|"
Space.TextSize = 15.000
Space.TextColor3 = Color3.fromRGB(224,224,224)
Space.TextXAlignment = Enum.TextXAlignment.Center

Title.Name = "Title"
Title.Parent = SliderFrame_2
Title.BackgroundColor3 = Color3.fromRGB(150, 150, 150)
Title.BackgroundTransparency = 1.000
Title.Position = UDim2.new(0, 50, 0, 0)
Title.Size = UDim2.new(0, 280, 0, 30)
Title.Font = Enum.Font.GothamSemibold
Title.Text = slidertitle or "Slider Title"
Title.TextColor3 = Color3.fromRGB(224,224,224)
Title.TextSize = 12.000
Title.TextXAlignment = Enum.TextXAlignment.Left

SliderInput.Name = "SliderInput"
SliderInput.Parent = SliderFrame_2
SliderInput.BackgroundColor3 = Color3.fromRGB(224,224,224)
SliderInput.BackgroundTransparency = 0.7
SliderInput.BorderSizePixel = 0
SliderInput.Position = UDim2.new(0, 8, 0, 37)
SliderInput.Size = UDim2.new(0, 355, 0, 4)

SliderCorner2.CornerRadius = UDim.new(0, 100000)
SliderCorner2.Parent = SliderInput

SliderButton.Name = "SliderButton"
SliderButton.Parent = SliderInput
SliderButton.BackgroundColor3 = Color3.fromRGB(150, 150, 150)
SliderButton.BackgroundTransparency = 1.000
SliderButton.BorderSizePixel = 0
SliderButton.Position = UDim2.new(0, 0, 0, -7)
SliderButton.Size = UDim2.new(0, 355, 0, 25)

SliderCount.Name = "SliderCount"
SliderCount.Parent = SliderButton
SliderCount.BackgroundColor3 = Color3.fromRGB(224,224,224)
SliderCount.BackgroundTransparency = 0.3
SliderCount.BorderSizePixel = 0
SliderCount.Position = UDim2.new(0,start,0,0)
SliderCount.Size = UDim2.new(0, 18, 0, 18)

Title_2.Name = "Title_2"
Title_2.Parent = SliderButton
Title_2.AnchorPoint = Vector2.new(0, 0)
Title_2.BackgroundColor3 = Color3.fromRGB(224,224,224)
Title_2.AutoButtonColor = false
Title_2.BackgroundTransparency = 1.000
Title_2.Position = UDim2.new(0,start,0,0)
Title_2.Size = UDim2.new(0, 18, 0, 18)
Title_2.Font = Enum.Font.GothamSemibold
Title_2.Text = tostring(start and math.floor((start / max) * (max - min) + min) or 0)
Title_2.TextColor3 = Color3.fromRGB(224,224,224)
Title_2.TextSize = 8.000
Title_2.TextXAlignment = Enum.TextXAlignment.Center

UICorner_2.Parent = Title_2
UICorner_2.CornerRadius = UDim.new(0, 100000)

SliderCorner.CornerRadius = UDim.new(0, 100000)
SliderCorner.Parent = SliderCount

SliderStroke.Name = "SliderStroke"
SliderStroke.Parent = BoxFrame
SliderStroke.ApplyStrokeMode = Enum.ApplyStrokeMode.Border
SliderStroke.Color = Color3.fromRGB(255,255,255)
SliderStroke.LineJoinMode = Enum.LineJoinMode.Round
SliderStroke.Thickness = 1
SliderStroke.Transparency = 0.8
SliderStroke.Enabled = true
SliderStroke.Archivable = true

BoxFrame.Name = "BoxFrame"
BoxFrame.Parent = SliderFrame_2
BoxFrame.BackgroundColor3 = Color3.fromRGB(20, 20, 20)
BoxFrame.BackgroundTransparency = 1.000
BoxFrame.Size = UDim2.new(0, 50, 0, 15)
BoxFrame.Position = UDim2.new(0, 300, 0, 8)

SliderBox.Name = "SliderBox"
SliderBox.Parent = BoxFrame
SliderBox.BackgroundColor3 = Color3.fromRGB(200, 0, 0)
SliderBox.BackgroundTransparency = 1.000
SliderBox.Position = UDim2.new(0, 0, 0, 1.65)
SliderBox.Size = UDim2.new(0, 50, 0, 15)
SliderBox.ClearTextOnFocus = false
SliderBox.Font = Enum.Font.GothamSemibold
SliderBox.Text = tostring(start and math.floor((start / max) * (max - min) + min) or 0)
SliderBox.TextColor3 = Color3.fromRGB(224,224,224)
SliderBox.TextSize = 9.000
SliderBox.TextTransparency = 0
SliderBox.TextXAlignment = Enum.TextXAlignment.Center
SliderBox.TextEditable = true

UICorner_3.Parent = BoxFrame
UICorner_3.CornerRadius = UDim.new(0, 2)

-- Slider Script --
local dragging
local SliderButtonStart
local SliderButtonInput
local slide = SliderButton

local function slide(input)
local slidein = UDim2.new(math.clamp((input.Position.X - SliderButton.AbsolutePosition.X) / SliderButton.AbsoluteSize.X, 0, 1), 0, 0, 0)
SliderCount:TweenPosition(slidein, Enum.EasingDirection.InOut, Enum.EasingStyle.Linear, 0.08, true)
Title_2:TweenPosition(slidein, Enum.EasingDirection.InOut, Enum.EasingStyle.Linear, 0.12, true)
local Value = math.floor(((slidein.X.Scale * max) / max) * (max - min) + min)
SliderBox.Text = tostring(Value)
Title_2.Text = tostring(Value)
pcall(callback, Value, slidein)
end

SliderButton.InputBegan:Connect(function(input)
 if input.UserInputType == Enum.UserInputType.MouseButton1 or input.UserInputType == Enum.UserInputType.Touch then
 dragging = true
 SliderButtonInput = input
 SliderButtonStart = input.Position.X
 slidein = SliderButton.AbsolutePosition.X
 game.TweenService:Create(SliderCount, TweenInfo.new(0.08, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut), {
  BackgroundTransparency = 0, Size = UDim2.new(0, 14, 0, 14)}):Play()
 game.TweenService:Create(Title_2, TweenInfo.new(0.12, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut), {
  AnchorPoint = Vector2.new(0.22, 0.8), TextSize = 13.000, BackgroundTransparency = 0, Size = UDim2.new(0, 25, 0, 25)}):Play()
 game.TweenService:Create(SliderBox, TweenInfo.new(0.08, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut), {
  TextTransparency = 0
 }):Play()
 game.TweenService:Create(SliderInput, TweenInfo.new(0.08, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut), {
  BackgroundTransparency = 0.5
 }):Play()
 game.TweenService:Create(SliderStroke, TweenInfo.new(0.08, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut), {
  Transparency = 0
 }):Play()
 end
 input.Changed:Connect(function(input)
  if input.UserInputType == Enum.UserInputState.End then
  dragging = false

  end
  end)
 end)
SliderButton.InputEnded:Connect(function(input)
 if input.UserInputType == Enum.UserInputType.MouseMovement or input.UserInputType == Enum.UserInputType.Touch then
 dragging = false
 SliderButtonInput = input
 game.TweenService:Create(SliderCount, TweenInfo.new(0.08, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut), {
  BackgroundTransparency = 0.3, Size = UDim2.new(0, 18, 0, 18)}):Play()
 game.TweenService:Create(Title_2, TweenInfo.new(0.12, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut), {
  AnchorPoint = Vector2.new(0, 0), TextSize = 8.000, BackgroundTransparency = 1.000, Size = UDim2.new(0, 18, 0, 18)}):Play()
 game.TweenService:Create(SliderBox, TweenInfo.new(0.08, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut), {
  TextTransparency = 0.5
 }):Play()
 game.TweenService:Create(SliderInput, TweenInfo.new(0.08, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut), {
  BackgroundTransparency = 0.7
 }):Play()
 game.TweenService:Create(SliderStroke, TweenInfo.new(0.08, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut), {
  Transparency = 0.5
 }):Play()
 end
 end)
UserInputService.InputChanged:Connect(function(input)
 if input == SliderButtonInput and dragging then
 slide(input)
 end
 end)

function set(property)
if property == "Text" then
if tonumber(SliderBox.Text) then
if tonumber(SliderBox.Text) <= max then
Value = SliderBox.Text
Title_2.Text = SliderBox.Text
SliderCount:TweenPosition(UDim2.new(((tonumber(SliderBox.Text) or min) - min) / (max - min), 0, 0, 0), "InOut", "Linear", 0.08, true)
Title_2:TweenPosition(UDim2.new(((tonumber(SliderBox.Text) or min) - min) / (max - min), 0, 0, 0), "InOut", "Linear", 0.12, true)
pcall(function()
 callback(Value)
 end)
end
if tonumber(SliderBox.Text) > max then
SliderBox.Text = max
Title_2.Text = max
Value = max
SliderCount:TweenPosition(UDim2.new(((max or min) - min) / (max - min), 0, 0, 0), "InOut", "Linear", 0.08, true)
Title_2:TweenPosition(UDim2.new(((max or min) - min) / (max - min), 0, 0, 0), "InOut", "Linear", 0.12, true)
pcall(function()
 callback(Value)
 end)
end
if tonumber(SliderBox.Text) >= min then
Value = SliderBox.Text
Title_2.Text = SliderBox.Text
SliderCount:TweenPosition(UDim2.new(((tonumber(SliderBox.Text) or min) - min) / (max - min), 0, 0, 0), "InOut", "Linear", 0.08, true)
Title_2:TweenPosition(UDim2.new(((tonumber(SliderBox.Text) or min) - min) / (max - min), 0, 0, 0), "InOut", "Linear", 0.12, true)
pcall(function()
 callback(Value)
 end)
end
if tonumber(SliderBox.Text) < min then
Value = min
Title_2 = min
SliderCount.Position = UDim2.new(((min or min) - min) / (max - min), 0, 0, 0)
Title_2.Position = UDim2.new(((min or min) - min) / (max - min), 0, 0, 0)
pcall(function()
 callback(Value)
 end)
end
else
 SliderBox.Text = "" or Value
Title_2.Text = Value
end
end
end

SliderBox.Focused:Connect(function()
 SliderBox.Changed:Connect(set)
 end)

SliderBox.FocusLost:Connect(function(enterP)
 if not enterP then
 if SliderBox.Text == "" then
 SliderBox.Text = min
 Title_2.Text = min
 Value = min
 SliderCount:TweenPosition(UDim2.new(((min) - min) / (max - min), 0, 0, 0), "InOut", "Linear", 0.08, true)
 Title_2:TweenPosition(UDim2.new(((min) - min) / (max - min), 0, 0, 0), "InOut", "Linear", 0.12, true)
 pcall(function()
  callback(Value)
  end)
 end
 if tonumber(SliderBox.Text) > tonumber(max) then
 Value = max
 SliderBox.Text = max
 Title_2.Text = max
 SliderCount:TweenPosition(UDim2.new(((max or min) - min) / (max - min), 0, 0, 0), "InOut", "Linear", 0.08, true)
 Title_2:TweenPosition(UDim2.new(((max or min) - min) / (max - min), 0, 0, 0), "InOut", "Linear", 0.12, true)
 pcall(function()
  callback(Value)
  end)
 else
  Value = tonumber(SliderBox.Text)
 end
 if tonumber(SliderBox.Text) < min then
 SliderBox.Text = min
 Title_2.Text = min
 Value = min
 SliderCount:TweenPosition(UDim2.new(((min) - min) / (max - min), 0, 0, 0), "InOut", "Linear", 0.08, true)
 Title_2:TweenPosition(UDim2.new(((min) - min) / (max - min), 0, 0, 0), "InOut", "Linear", 0.12, true)
 pcall(function()
  callback(Value)
  end)
 else
  Value = tonumber(SliderBox.Text)
 end
 end
 if tonumber(SliderBox.Text) > max then
 SliderBox.Text = max
 Title_2.Text = max
 Value = max
 SliderCount:TweenPosition(UDim2.new(((max or min) - min) / (max - min), 0, 0, 0), "InOut", "Linear", 0.08, true)
 Title_2:TweenPosition(UDim2.new(((max or min) - min) / (max - min), 0, 0, 0), "InOut", "Linear", 0.12, true)
 pcall(function()
  callback(Value)
  end)
 else
  Value = tonumber(SliderBox.Text)
 end
 if tonumber(SliderBox.Text) < min then
 SliderBox.Text = min
 Title_2.Text = min
 Value = min
 SliderCount.Position = UDim2.new(((min) - min) / (max - min), 0, 0, 0)
 Title_2.Position = UDim2.new(((min) - min) / (max - min), 0, 0, 0)
 pcall(function()
  callback(Value)
  end)
 else
  Value = tonumber(SliderBox.Text)
 end
 if SliderBox.Text == "" then
 SliderBox.Text = min
 Title_2.Text = min
 Value = min
 SliderCount:TweenPosition(UDim2.new(((min) - min) / (max - min), 0, 0, 0), "InOut", "Linear", 0.08, true)
 Title_2:TweenPosition(UDim2.new(((min) - min) / (max - min), 0, 0, 0), "InOut", "Linear", 0.12, true)
 pcall(function()
  callback(Value)
  end)
 end
 end)
return sliderfunc
end

 _G.BGColor_1 = Color3.fromRGB(30,30,30)
 _G.BGColor_2 = Color3.fromRGB(20, 20, 20)
 _G.WindowBackgroundColor = Color3.fromRGB(12,12,12)
 _G.BackgroundItemColor = Color3.fromRGB(20, 20, 20)
 _G.TabWindowColor = Color3.fromRGB(30, 30, 30)
 _G.ContainerColor = Color3.fromRGB(30, 30, 30)
 _G.TitleTextColor = Color3.fromRGB(150, 150, 150)
 _G.ImageColor = Color3.fromRGB(150, 150, 150)
 _G.LineThemeColor = Color3.fromRGB(150, 150, 150)
 _G.TabTextColor = Color3.fromRGB(150, 150, 150)
 _G.TabImageColor = Color3.fromRGB(150, 150, 150)
 _G.TabThemeColor = Color3.fromRGB(250, 0, 0)
 _G.SectionColor = Color3.fromRGB(150, 150, 150)
 _G.SectionImageColor = Color3.fromRGB(150, 150, 150)
 _G.SectionTextColor = Color3.fromRGB(150, 150, 150)
 _G.SectionOn = Color3.fromRGB(0, 250, 0)
 
 function main:Slider(text,min,max,set,callback)
 local Slider = Instance.new("Frame")
 local slidercorner = Instance.new("UICorner")
 local sliderr = Instance.new("Frame")
 local sliderrcorner = Instance.new("UICorner")
 local SliderLabel = Instance.new("TextLabel")
 local HAHA = Instance.new("Frame")
 local AHEHE = Instance.new("TextButton")
 local bar = Instance.new("Frame")
 local bar1 = Instance.new("Frame")
 local bar1corner = Instance.new("UICorner")
 local barcorner = Instance.new("UICorner")
 local circlebar = Instance.new("Frame")
 local UICorner = Instance.new("UICorner")
 local slidervalue = Instance.new("Frame")
 local valuecorner = Instance.new("UICorner")
 local TextBox = Instance.new("TextBox")
 local UICorner_2 = Instance.new("UICorner")
 local posto = Instance.new("UIStroke")
 
 Slider.Name = "Slider"
 Slider.Parent = MainFramePage
 Slider.BackgroundColor3 = Color3.fromRGB(255,255,255)
 Slider.BackgroundTransparency = 0.8
 Slider.Size = UDim2.new(0, 370, 0, 51)
 
 slidercorner.CornerRadius = UDim.new(0, 5)
 slidercorner.Name = "slidercorner"
 slidercorner.Parent = Slider
 
 sliderr.Name = "sliderr"
 sliderr.Parent = Slider
 sliderr.BackgroundTransparency = 0
 sliderr.BackgroundColor3 = Color3.fromRGB(30,30,30)
 sliderr.Position = UDim2.new(0, 1, 0, 1)
 sliderr.Size = UDim2.new(0, 368, 0, 49)
 
 sliderrcorner.CornerRadius = UDim.new(0, 5)
 sliderrcorner.Name = "sliderrcorner"
 sliderrcorner.Parent = sliderr
 
 SliderLabel.Name = "SliderLabel"
 SliderLabel.Parent = sliderr
 SliderLabel.BackgroundColor3 = Color3.fromRGB(224,224,224)
 SliderLabel.BackgroundTransparency = 1.000
 SliderLabel.Position = UDim2.new(0, 15, 0, 0)
 SliderLabel.Size = UDim2.new(0, 180, 0, 26)
 SliderLabel.Font = Enum.Font.GothamSemibold
 SliderLabel.Text = text
 SliderLabel.TextColor3 = Color3.fromRGB(224,224,224)
 SliderLabel.TextSize = 12.000
 SliderLabel.TextTransparency = 0
 SliderLabel.TextXAlignment = Enum.TextXAlignment.Left
 
 HAHA.Name = "HAHA"
 HAHA.Parent = sliderr
 HAHA.BackgroundColor3 = Color3.fromRGB(224,224,224)
 HAHA.BackgroundTransparency = 1.000
 HAHA.Size = UDim2.new(0, 355, 0, 29)
 
 AHEHE.Name = "AHEHE"
 AHEHE.Parent = sliderr
 AHEHE.BackgroundColor3 = Color3.fromRGB(224,224,224)
 AHEHE.BackgroundTransparency = 1.000
 AHEHE.Position = UDim2.new(0, 10, 0, 35)
 AHEHE.Size = UDim2.new(0, 355, 0, 5)
 AHEHE.Font = Enum.Font.SourceSans
 AHEHE.Text = ""
 AHEHE.TextColor3 = Color3.fromRGB(0, 0, 0)
 AHEHE.TextSize = 14.000
 
 bar.Name = "bar"
 bar.Parent = AHEHE
 bar.BackgroundColor3 = _G.BGColor_2
 bar.Size = UDim2.new(0, 355, 0, 5)
 
 bar1.Name = "bar1"
 bar1.Parent = bar
 bar1.BackgroundColor3 = Color3.fromRGB(225, 225, 225)
 bar1.BackgroundTransparency = 0
 bar1.Size = UDim2.new(set/max, 0, 0, 5)
 
 bar1corner.CornerRadius = UDim.new(0, 5)
 bar1corner.Name = "bar1corner"
 bar1corner.Parent = bar1
 
 barcorner.CornerRadius = UDim.new(0, 5)
 barcorner.Name = "barcorner"
 barcorner.Parent = bar
 
 circlebar.Name = "circlebar"
 circlebar.Parent = bar1
 circlebar.BackgroundColor3 = Color3.fromRGB(224,224,224)
 circlebar.Position = UDim2.new(1, -2, 0, -3)
 circlebar.Size = UDim2.new(0, 10, 0, 10)
 
 UICorner.CornerRadius = UDim.new(0, 100)
 UICorner.Parent = circlebar
 
 slidervalue.Name = "slidervalue"
 slidervalue.Parent = sliderr
 slidervalue.BackgroundColor3 = Color3.fromRGB(225, 225, 225)
 slidervalue.BackgroundTransparency = 1
 slidervalue.Position = UDim2.new(0, 300, 0, 5)
 slidervalue.Size = UDim2.new(0, 65, 0, 18)
 
 valuecorner.CornerRadius = UDim.new(0, 5)
 valuecorner.Name = "valuecorner"
 valuecorner.Parent = slidervalue
 
 TextBox.Parent = slidervalue
 TextBox.BackgroundColor3 = _G.BGColor_2
 TextBox.Position = UDim2.new(0, 0, 0, 0)
 TextBox.Size = UDim2.new(0, 60, 0, 20)
 TextBox.Font = Enum.Font.GothamSemibold
 TextBox.TextColor3 = Color3.fromRGB(224,224,224)
 TextBox.TextSize = 9.000
 TextBox.Text = set
 TextBox.TextTransparency = 0
 
 posto.Name = "posto"
 posto.Parent = TextBox
 posto.ApplyStrokeMode = Enum.ApplyStrokeMode.Border
 posto.Color = Color3.fromRGB(224,224,224)
 posto.LineJoinMode = Enum.LineJoinMode.Round
 posto.Thickness = 1
 posto.Transparency = 0
 posto.Enabled = true
 posto.Archivable = true
 
 UICorner_2.CornerRadius = UDim.new(0, 5)
 UICorner_2.Parent = TextBox
 
 local mouse = game.Players.LocalPlayer:GetMouse()
 local uis = game:GetService("UserInputService")
 
 if Value == nil then
 Value = set
 pcall(function()
  callback(Value)
  end)
 end
 
 AHEHE.MouseButton1Down:Connect(function()
  Value = math.floor((((tonumber(max) - tonumber(min)) / 320) * bar1.AbsoluteSize.X) + tonumber(min)) or 0
  pcall(function()
   callback(Value)
   end)
  bar1.Size = UDim2.new(0, math.clamp(mouse.X - bar1.AbsolutePosition.X, 0, 320), 0, 5)
  circlebar.Position = UDim2.new(0, math.clamp(mouse.X - bar1.AbsolutePosition.X - 2, 0, 355), 0, -3)
  moveconnection = mouse.Move:Connect(function()
   TextBox.Text = Value
   Value = math.floor((((tonumber(max) - tonumber(min)) / 320) * bar1.AbsoluteSize.X) + tonumber(min))
   pcall(function()
    callback(Value)
    end)
   bar1.Size = UDim2.new(0, math.clamp(mouse.X - bar1.AbsolutePosition.X, 0, 320), 0, 5)
   circlebar.Position = UDim2.new(0, math.clamp(mouse.X - bar1.AbsolutePosition.X - 2, 0, 355), 0, -3)
   end)
  releaseconnection = uis.InputEnded:Connect(function(Mouse)
   if Mouse.UserInputType == Enum.UserInputType.MouseButton1 then
   Value = math.floor((((tonumber(max) - tonumber(min)) / 320) * bar1.AbsoluteSize.X) + tonumber(min))
   pcall(function()
    callback(Value)
    end)
   bar1.Size = UDim2.new(0, math.clamp(mouse.X - bar1.AbsolutePosition.X, 0, 320), 0, 5)
   circlebar.Position = UDim2.new(0, math.clamp(mouse.X - bar1.AbsolutePosition.X - 2, 0, 355), 0, -3)
   moveconnection:Disconnect()
   releaseconnection:Disconnect()
   end
   end)
  end)
 releaseconnection = uis.InputEnded:Connect(function(Mouse)
  if Mouse.UserInputType == Enum.UserInputType.MouseButton1 then
  Value = math.floor((((tonumber(max) - tonumber(min)) / 320) * bar1.AbsoluteSize.X) + tonumber(min))
  TextBox.Text = Value
  end
  end)
 
 TextBox.FocusLost:Connect(function()
  if tonumber(TextBox.Text) > max then
  TextBox.Text = max
  end
  bar1.Size = UDim2.new((TextBox.Text or 0) / max, 0, 0, 5)
  circlebar.Position = UDim2.new(1, -2, 0, -3)
  TextBox.Text = tostring(TextBox.Text and math.floor((TextBox.Text / max) * (max - min) + min))
  pcall(callback, TextBox.Text)
  end)
 end
 function main:Textbox(text,disappear,callback)
 local Textbox = Instance.new("Frame")
 local TextboxCorner = Instance.new("UICorner")
 local Textboxx = Instance.new("Frame")
 local TextboxxCorner = Instance.new("UICorner")
 local TextboxLabel = Instance.new("TextLabel")
 local txtbtn = Instance.new("TextButton")
 local RealTextbox = Instance.new("TextBox")
 local UICorner = Instance.new("UICorner")
 
 Textbox.Name = "Textbox"
 Textbox.Parent = MainFramePage
 Textbox.BackgroundColor3 = Color3.fromRGB(255,255,255)
 Textbox.BackgroundTransparency = 0.8
 Textbox.Size = UDim2.new(0, 370, 0, 31)
 
 TextboxCorner.CornerRadius = UDim.new(0, 0)
 TextboxCorner.Name = "TextboxCorner"
 TextboxCorner.Parent = Textbox
 
 Textboxx.Name = "Textboxx"
 Textboxx.Parent = Textbox
 Textboxx.BackgroundColor3 = Color3.fromRGB(30,30,30)
 Textboxx.Position = UDim2.new(0, 1, 0, 1)
 Textboxx.Size = UDim2.new(0, 368, 0, 29)
 
 TextboxxCorner.CornerRadius = UDim.new(0, 5)
 TextboxxCorner.Name = "TextboxxCorner"
 TextboxxCorner.Parent = Textboxx
 
 TextboxLabel.Name = "TextboxLabel"
 TextboxLabel.Parent = Textbox
 TextboxLabel.BackgroundColor3 = Color3.fromRGB(224,224,224)
 TextboxLabel.BackgroundTransparency = 1.000
 TextboxLabel.Position = UDim2.new(0, 15, 0, 0)
 TextboxLabel.Text = text
 TextboxLabel.Size = UDim2.new(0, 145, 0, 31)
 TextboxLabel.Font = Enum.Font.GothamSemibold
 TextboxLabel.TextColor3 = Color3.fromRGB(225, 225, 225)
 TextboxLabel.TextSize = 16.000
 TextboxLabel.TextTransparency = 0
 TextboxLabel.TextXAlignment = Enum.TextXAlignment.Left
 
 txtbtn.Name = "txtbtn"
 txtbtn.Parent = Textbox
 txtbtn.BackgroundColor3 = Color3.fromRGB(224,224,224)
 txtbtn.BackgroundTransparency = 1.000
 txtbtn.Position = UDim2.new(0, 1, 0, 1)
 txtbtn.Size = UDim2.new(0, 370, 0, 29)
 txtbtn.Font = Enum.Font.SourceSans
 txtbtn.Text = ""
 txtbtn.TextColor3 = Color3.fromRGB(0, 0, 0)
 txtbtn.TextSize = 14.000
 
 RealTextbox.Name = "RealTextbox"
 RealTextbox.Parent = Textbox
 RealTextbox.BackgroundColor3 = Color3.fromRGB(35, 35, 35)
 RealTextbox.BackgroundTransparency = 0
 RealTextbox.Position = UDim2.new(0, 260, 0, 4)
 RealTextbox.Size = UDim2.new(0, 100, 0, 24)
 RealTextbox.Font = Enum.Font.GothamSemibold
 RealTextbox.Text = ""
 RealTextbox.TextColor3 = Color3.fromRGB(225, 225, 225)
 RealTextbox.TextSize = 11.000
 RealTextbox.TextTransparency = 0
 
 RealTextbox.FocusLost:Connect(function()
  callback(RealTextbox.Text)
  if disappear then
  RealTextbox.Text = ""
  end
  end)
 
 UICorner.CornerRadius = UDim.new(0, 5)
 UICorner.Parent = RealTextbox
 end
 function main:Label(text)
 local Label = Instance.new("TextLabel")
 local PaddingLabel = Instance.new("UIPadding")
 local labelfunc = {}
 
 Label.Name = "Label"
 Label.Parent = MainFramePage
 Label.BackgroundColor3 = Color3.fromRGB(224,224,224)
 Label.BackgroundTransparency = 1.000
 Label.Size = UDim2.new(0, 325, 0, 20)
 Label.Font = Enum.Font.GothamSemibold
 Label.TextColor3 = Color3.fromRGB(225, 225, 225)
 Label.TextSize = 12.000
 Label.Text = text
 Label.TextXAlignment = Enum.TextXAlignment.Left
 
 PaddingLabel.PaddingLeft = UDim.new(0,15)
 PaddingLabel.Parent = Label
 PaddingLabel.Name = "PaddingLabel"
 
 function labelfunc:Set(newtext)
 Label.Text = newtext
 end
 return labelfunc
 end
 
 function main:Label1(text)
 local Label1 = Instance.new("TextLabel")
 local PaddingLabel1 = Instance.new("UIPadding")
 local Label1func = {}
 
 Label1.Name = "Label1"
 Label1.Parent = MainFramePage
 Label1.BackgroundColor3 = Color3.fromRGB(224,224,224)
 Label1.BackgroundTransparency = 1.000
 Label1.Size = UDim2.new(0, 325, 0, 20)
 Label1.Font = Enum.Font.GothamSemibold
 Label1.TextColor3 = Color3.fromRGB(225, 225, 225)
 Label1.TextSize = 12.000
 Label1.Text = text
 Label1.TextXAlignment = Enum.TextXAlignment.Left
 
 PaddingLabel1.PaddingLeft = UDim.new(0,15)
 PaddingLabel1.Parent = Label1
 PaddingLabel1.Name = "PaddingLabel1"
 function Label1func:Refresh(tochange)
 Label1.Text = tochange
 end
 
 return Label1func
 end
 
function main:Seperator(text)
 local Seperator = Instance.new("Frame")
 local Sep1 = Instance.new("Frame")
 local Sep2 = Instance.new("TextLabel")
 local Sep3 = Instance.new("Frame")
 
 Seperator.Name = "Seperator"
 Seperator.Parent = MainFramePage
 Seperator.BackgroundColor3 = Color3.fromRGB(224,224,224)
 Seperator.BackgroundTransparency = 1.000
 Seperator.Size = UDim2.new(0, 320, 0, 20)
 
 Sep1.Name = "Sep1"
 Sep1.Parent = Seperator
 Sep1.BackgroundColor3 = Color3.fromRGB(255,255,255)
 Sep1.BorderSizePixel = 0
 Sep1.Position = UDim2.new(0, 0, 0, 10)
 Sep1.Size = UDim2.new(0, 120, 0, 1)
 
 Sep2.Name = "Sep2"
 Sep2.Parent = Seperator
 Sep2.BackgroundColor3 = Color3.fromRGB(224,224,224)
 Sep2.BackgroundTransparency = 1.000
 Sep2.Position = UDim2.new(0, 130, 0, 0)
 Sep2.Size = UDim2.new(0, 100, 0, 20)
 Sep2.Font = Enum.Font.GothamSemibold
 Sep2.Text = text
 Sep2.TextColor3 = Color3.fromRGB(224,224,224)
 Sep2.TextSize = 10.000
 
 Sep3.Name = "Sep3"
 Sep3.Parent = Seperator
 Sep3.BackgroundColor3 = Color3.fromRGB(255,255,255)
 Sep3.BorderSizePixel = 0
 Sep3.Position = UDim2.new(0, 240, 0, 10)
 Sep3.Size = UDim2.new(0, 120, 0, 1)
 end
 
 
 function main:Line()
 local Linee = Instance.new("Frame")
 local Line = Instance.new("Frame")
 
 Linee.Name = "Linee"
 Linee.Parent = MainFramePage
 Linee.BackgroundColor3 = Color3.fromRGB(224,224,224)
 Linee.BackgroundTransparency = 1.000
 Linee.Position = UDim2.new(0, 0, 0.119999997, 0)
 Linee.Size = UDim2.new(0, 530, 0, 20)
 
 Line.Name = "Line"
 Line.Parent = Linee
 Line.BackgroundColor3 = Color3.fromRGB(255,255,255)
 Line.BorderSizePixel = 0
 Line.Position = UDim2.new(0, 0, 0, 10)
 Line.Size = UDim2.new(0, 530, 0, 1)
 end
 return main
 end
 return uitab
end

if game.PlaceId == 2753915549 then
	World1 = true
elseif game.PlaceId == 4442272183 then
	World2 = true
elseif game.PlaceId == 7449423635 then
	World3 = true
end
 




function AutoHaki()
	if not game:GetService("Players").LocalPlayer.Character:FindFirstChild("HasBuso") then
		game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("Buso")
	end
end
 
function Equipgui(ToolSe)
	if not _G.NotAutoEquip then
		if game.Players.LocalPlayer.Backpack:FindFirstChild(ToolSe) then
			Tool = game.Players.LocalPlayer.Backpack:FindFirstChild(ToolSe)
			wait(.1)
			game.Players.LocalPlayer.Character.Humanoid:EquipTool(Tool)
		end
	end
end

 function topos(Pos)
        Distance = (Pos.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude
        if game.Players.LocalPlayer.Character.Humanoid.Sit == true then game.Players.LocalPlayer.Character.Humanoid.Sit = false end
        pcall(function() tween = game:GetService("TweenService"):Create(game.Players.LocalPlayer.Character.HumanoidRootPart,TweenInfo.new(Distance/210, Enum.EasingStyle.Linear),{CFrame = Pos}) end)
        tween:Play()
        if Distance <= 250 then
            tween:Cancel()
            game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = Pos
        end
        if _G.StopTween == true then
            tween:Cancel()
            _G.Clip = false
        end
    end
    
    function GetDistance(target)
        return math.floor((target.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude)
    end


function StopTween(target)
	if not target then
		_G.StopTween = true
		wait()
		topos(game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame)
		wait()
		if game:GetService("Players").LocalPlayer.Character.HumanoidRootPart:FindFirstChild("BodyClip") then
			game:GetService("Players").LocalPlayer.Character.HumanoidRootPart:FindFirstChild("BodyClip"):Destroy()
		end
		_G.StopTween = false
		_G.Clip = false
	end
end

function UseCode(Text)
	game:GetService("ReplicatedStorage").Remotes.Redeem:InvokeServer(Text)
end

function hop()
    local PlaceID = game.PlaceId
    local AllIDs = {}
    local foundAnything = ""
    local actualHour = os.date("!*t").hour
    local Deleted = false
    function TPReturner()
        local Site;
        if foundAnything == "" then
            Site = game.HttpService:JSONDecode(game:HttpGet('https://games.roblox.com/v1/games/' .. PlaceID .. '/servers/Public?sortOrder=Asc&limit=100'))
        else
            Site = game.HttpService:JSONDecode(game:HttpGet('https://games.roblox.com/v1/games/' .. PlaceID .. '/servers/Public?sortOrder=Asc&limit=100&cursor=' .. foundAnything))
        end
        local ID = ""
        if Site.nextPageCursor and Site.nextPageCursor ~= "null" and Site.nextPageCursor ~= nil then
            foundAnything = Site.nextPageCursor
        end
        local num = 0;
        for i,v in pairs(Site.data) do
            local Possible = true
            ID = tostring(v.id)
            if tonumber(v.maxPlayers) > tonumber(v.playing) then
                for _,Existing in pairs(AllIDs) do
                    if num ~= 0 then
                        if ID == tostring(Existing) then
                            Possible = false
                        end
                    else
                        if tonumber(actualHour) ~= tonumber(Existing) then
                            local delFile = pcall(function()
                                -- delfile("NotSameServers.json")
                                AllIDs = {}
                                table.insert(AllIDs, actualHour)
                            end)
                        end
                    end
                    num = num + 1
                end
                if Possible == true then
                    table.insert(AllIDs, ID)
                    wait()
                    pcall(function()
                        -- writefile("NotSameServers.json", game:GetService('HttpService'):JSONEncode(AllIDs))
                        wait()
                        game:GetService("TeleportService"):TeleportToPlaceInstance(PlaceID, ID, game.Players.LocalPlayer)
                    end)
                    wait(4)
                end
            end
        end
    end
    function Teleport()
        while wait() do
            pcall(function()
                TPReturner()
                if foundAnything ~= "" then
                    TPReturner()
                end
            end)
        end
    end
    Teleport()
end

	local PlaceID = game.PlaceId
	local AllIDs = {}
	local foundAnything = ""
	local actualHour = os.date("!*t").hour
	local Deleted = false
	local File = pcall(function()
		AllIDs = game:GetService('HttpService'):JSONDecode(readfile("NotSameServers.json"))
	end)
	if not File then
		table.insert(AllIDs, actualHour)
		writefile("NotSameServers.json", game:GetService('HttpService'):JSONEncode(AllIDs))
	end
	function TPReturner()
		local Site;
		if foundAnything == "" then
			Site = game.HttpService:JSONDecode(game:HttpGet('https://games.roblox.com/v1/games/' .. PlaceID .. '/servers/Public?sortOrder=Asc&limit=100'))
		else
			Site = game.HttpService:JSONDecode(game:HttpGet('https://games.roblox.com/v1/games/' .. PlaceID .. '/servers/Public?sortOrder=Asc&limit=100&cursor=' .. foundAnything))
		end
		local ID = ""
		if Site.nextPageCursor and Site.nextPageCursor ~= "null" and Site.nextPageCursor ~= nil then
			foundAnything = Site.nextPageCursor
		end
		local num = 0;
		for i,v in pairs(Site.data) do
			local Possible = true
			ID = t
				SaveSetting()ostring(v.id)
			if tonumber(v.maxPlayers) > tonumber(v.playing) then
				for _,Existing in pairs(AllIDs) do
					if num ~= 0 then
						if ID == tostring(Existing) then
							Possible = false
						end
					else
						if tonumber(actualHour) ~= tonumber(Existing) then
							local delFile = pcall(function()
								delfile("NotSameServers.json")
								AllIDs = {}
								table.insert(AllIDs, actualHour)
							end)
						end
					end
					num = num + 1
				end
				if Possible == true then
					table.insert(AllIDs, ID)
					wait()
					pcall(function()
						writefile("NotSameServers.json", game:GetService('HttpService'):JSONEncode(AllIDs))
						wait()
						game:GetService("TeleportService"):TeleportToPlaceInstance(PlaceID, ID, game.Players.LocalPlayer)
					end)
					wait(1)
				end
			end
		end
	end

	function Teleport()
		while wait() do
			pcall(function()
				TPReturner()
				if foundAnything ~= "" then
					TPReturner()
				end
			end)
		end
	end

    function InfAb()
        if InfAbility then
            if not game:GetService("Players").LocalPlayer.Character.HumanoidRootPart:FindFirstChild("Agility") then
                local inf = Instance.new("ParticleEmitter")
                inf.Acceleration = Vector3.new(0,0,0)
                inf.Archivable = true
                inf.Drag = 20
                inf.EmissionDirection = Enum.NormalId.Top
                inf.Enabled = true
                inf.Lifetime = NumberRange.new(0,0)
                inf.LightInfluence = 0
                inf.LockedToPart = true
                inf.Name = "Agility"
                inf.Rate = 500
                local numberKeypoints2 = {
                    NumberSequenceKeypoint.new(0, 0);
                    NumberSequenceKeypoint.new(1, 4); 
                }
                inf.Size = NumberSequence.new(numberKeypoints2)
                inf.RotSpeed = NumberRange.new(9999, 99999)
                inf.Rotation = NumberRange.new(0, 0)
                inf.Speed = NumberRange.new(30, 30)
                inf.SpreadAngle = Vector2.new(0,0,0,0)
                inf.Texture = "rbxassetid://243098098"
                inf.VelocityInheritance = 0
                inf.ZOffset = 2
                inf.Transparency = NumberSequence.new(0)
                inf.Color = ColorSequence.new(Color3.fromRGB(0,0,0),Color3.fromRGB(0,0,0))
                inf.Parent = game:GetService("Players").LocalPlayer.Character.HumanoidRootPart
            end
        else
            if game:GetService("Players").LocalPlayer.Character.HumanoidRootPart:FindFirstChild("Agility") then
                game:GetService("Players").LocalPlayer.Character.HumanoidRootPart:FindFirstChild("Agility"):Destroy()
            end
        end
    end


---------------------------------------------------------------

spawn(function()
	pcall(function()
		game:GetService("RunService").Stepped:Connect(function()
		  	if _G.Auto_Farm_Level or _G.Auto_New_World or _G.AutoFarmFruitMastery or _G.AutoFarmGunMastery or _G.Auto_Third_World or _G.Auto_Farm_Chest or _G.TeleportIsland or _G.Auto_Farm_Boss or _G.Autotushita or _G.Auto_Elite_Hunter or _G.Auto_Cake_Prince or _G.Auto_Farm_All_Boss or _G.Auto_Saber or _G.Auto_Pole or _G.Auto_Farm_Scrap_and_Leather or _G.Auto_Farm_Angel_Wing or _G.Auto_Factory_Farm or _G.Auto_Farm_Ectoplasm or _G.Auto_Bartilo_Quest or _G.Auto_Rengoku or _G.Auto_Farm_Radioactive or _G.Auto_Farm_Vampire_Fang or _G.Auto_Farm_Mystic_Droplet or _G.Auto_Farm_GunPowder or _G.Auto_Farm_Dragon_Scales or _G.Auto_Evo_Race_V2 or _G.Auto_Swan_Glasses or _G.Auto_Dragon_Trident or _G.Auto_Soul_Reaper or _G.Auto_Farm_Fish_Tail or _G.Auto_Farm_Mini_Tusk or _G.Auto_Farm_Magma_Ore or _G.Auto_Farm_Bone or _G.Auto_Farm_Conjured_Cocoa or _G.Auto_Open_Dough_Dungeon or _G.Auto_Rainbow_Haki or _G.Auto_Musketeer_Hat or _G.Auto_Holy_Torch or _G.Auto_Canvander or _G.d or _G.Auto_Twin_Hook or _G.Auto_Serpent_Bow or _G.AutoFarmMaterial or _G.Auto_Fully_Death_Step or _G.Auto_Fully_SharkMan_Karate or _G.Teleport_to_Player or _G.Auto_Kill_Player_Melee or _G.Auto_Kill_Player_Gun or _G.Start_Tween_Island or _G.Auto_Next_Island or _G.autoraid or AutoNextIsland or _G.Auto_Farm_Sword or _G.MeleeFarm or _G.AutoFarmSelectMonster or _G.AutoFarmKenHakivor or _G.AutoObservationHakiV2 or _G.GunMastery or _G.AutoFactory or _G.Mastery or _G.Auto_Kill_Law then
			 	if not game.Players.LocalPlayer.Character.HumanoidRootPart:FindFirstChild("BodyClip") then
					local Noclip = Instance.new("BodyVelocity")
					Noclip.Name = "BodyClip"
					Noclip.Parent = game.Players.LocalPlayer.Character.HumanoidRootPart
					Noclip.MaxForce = Vector3.new(100000,100000,100000)
					Noclip.Velocity = Vector3.new(0,0,0)
			 	end
		  	else	
			 	if game.Players.LocalPlayer.Character.HumanoidRootPart:FindFirstChild("BodyClip") then
					game.Players.LocalPlayer.Character.HumanoidRootPart:FindFirstChild("BodyClip"):Destroy()
			 	end
		  	end
		end)
	end)
end)
 
spawn(function()
	pcall(function()
		game:GetService("RunService").Stepped:Connect(function()
			if _G.Auto_Farm_Level or _G.Auto_New_World or _G.TeleportIsland or _G.Auto_Third_World or _G.Auto_Farm_Chest or _G.Auto_Farm_Boss or _G.GunMastery or _G.Mastery or _G.AutoFarmFruitMastery or _G.AutoFarmGunMastery or _G.Auto_Elite_Hunter or _G.AutoFarmKenHaki or _G.AutoFactory or _G.AutoFarmSelectMonster or _G.Auto_Cake_Prince or _G.Auto_Farm_All_Boss or _G.Auto_Saber or _G.Auto_Pole or _G.Auto_Farm_Scrap_and_Leather or _G.Auto_Farm_Angel_Wing or _G.Auto_Factory_Farm or _G.Auto_Farm_Ectoplasm or _G.Auto_Bartilo_Quest or _G.d or _G.Auto_Rengoku or _G.Autotushita or _G.Auto_Farm_Radioactive or _G.Auto_Farm_Vampire_Fang or _G.Auto_Farm_Mystic_Droplet or _G.Auto_Farm_GunPowder or _G.Auto_Farm_Dragon_Scales or _G.Auto_Evo_Race_V2 or _G.Auto_Swan_Glasses or _G.Auto_Dragon_Trident or _G.Auto_Soul_Reaper or _G.Auto_Farm_Fish_Tail or _G.Auto_Farm_Mini_Tusk or _G.Auto_Farm_Magma_Ore or _G.Auto_Farm_Bone or _G.Auto_Farm_Conjured_Cocoa or _G.Auto_Open_Dough_Dungeon or _G.Auto_Rainbow_Haki or _G.Auto_Musketeer_Hat or _G.Auto_Holy_Torch or _G.Auto_Canvander or _G.AutoFarmMaterial or _G.autoraid or _G.Auto_Twin_Hook or AutoNextIsland or _G.Auto_Serpent_Bow or _G.Auto_Fully_Death_Step or _G.Auto_Fully_SharkMan_Karate or _G.Teleport_to_Player or _G.Auto_Kill_Player_Melee or _G.Auto_Kill_Player_Gun or _G.Start_Tween_Island or _G.AutoObservationHakiV2 or _G.d or _G.Auto_Next_Island or _G.Auto_Farm_Sword or _G.MeleeFarm or _G.Auto_Kill_Law then
				for _, v in pairs(game.Players.LocalPlayer.Character:GetDescendants()) do
					if v:IsA("BasePart") then
						v.CanCollide = false    
					end
				end
			end
		end)
	end)
end)


spawn(function()
	while wait() do
		for i,v in pairs(game.Players.LocalPlayer.Backpack:GetChildren()) do  
			if v:IsA("Tool") then
				if v:FindFirstChild("RemoteFunctionShoot") then 
					SelectToolguiGun = v.Name
				end
			end
		end
		for i,v in pairs(game.Players.LocalPlayer.Character:GetChildren()) do  
			if v:IsA("Tool") then
				if v:FindFirstChild("RemoteFunctionShoot") then 
					SelectToolguiGun = v.Name
				end
			end
		end
	end
end)

spawn(function()
	local gg = getrawmetatable(game)
	local old = gg.__namecall
	setreadonly(gg,false)
	gg.__namecall = newcclosure(function(...)
		local method = getnamecallmethod()
		local args = {...}
		if tostring(method) == "FireServer" then
			if tostring(args[1]) == "RemoteEvent" then
				if tostring(args[2]) ~= "true" and tostring(args[2]) ~= "false" then
					if UseSkillMasteryDevilFruit then
						args[2] = PositionSkillMasteryDevilFruit
						return old(unpack(args))
					elseif AimSkillNearest then
						args[2] = AimBotSkillPosition
						return old(unpack(args))
					end
				end
			end
		end
		return old(...)
	end)
end)

spawn(function()
	game:GetService("RunService").RenderStepped:Connect(function()
        if UseGun then
			pcall(function()
                for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                    if v.Name == Ms then
						local args = {
							[1] = "TAP",
							[2] = v.HumanoidRootPart.Position
						}
						
						game:GetService("Players").LocalPlayer.Character.Humanoid:FindFirstChild("Soul Guitar"):InvokeServer(unpack(args))
                        local args = {
                            [1] = v.HumanoidRootPart.Position,
                            [2] = v.HumanoidRootPart
                        }
                        game:GetService("Players").LocalPlayer.Character[SelectToolguiGun].RemoteFunctionShoot:InvokeServer(unpack(args))
                    end
                end
            end)
        end
    end)
end)

spawn(function()
	game:GetService("RunService").RenderStepped:Connect(function()
        if UseGunKillPlayer then
			pcall(function()
                for i,v in pairs(game:GetService("Workspace").Characters:GetChildren()) do
                    if v.Name == _G.Select_Player then
                        local args = {
                            [1] = v.HumanoidRootPart.Position,
                            [2] = v.HumanoidRootPart
                        }
                        game:GetService("Players").LocalPlayer.Character[SelectToolguiGun].RemoteFunctionShoot:InvokeServer(unpack(args))
                    end
                end
            end)
        end
    end)
end)

local lp = game:GetService('Players').LocalPlayer
local mouse = lp:GetMouse()
spawn(function()
	while wait() do
		if _G.Aimbot_Skill_Fov then
			pcall(function()
				local MaxDist, Closest = math.huge
				for i,v in pairs(game:GetService("Players"):GetChildren()) do 
					local Head = v.Character:FindFirstChild("HumanoidRootPart")
					local Pos, Vis = game.Workspace.CurrentCamera.WorldToScreenPoint(game.Workspace.CurrentCamera, Head.Position)
					local MousePos, TheirPos = Vector2.new(mouse.X, mouse.Y), Vector2.new(Pos.X, Pos.Y)
					local Dist = (TheirPos - MousePos).Magnitude
					if Dist < MaxDist and Dist <= _G.Select_Size_Fov and v.Name ~= game.Players.LocalPlayer.Name then
						MaxDist = Dist
						_G.Aim_Players = v
					end
				end
			end)
		end
	end
end)

spawn(function()
	local gg = getrawmetatable(game)
	local old = gg.__namecall
	setreadonly(gg,false)
	gg.__namecall = newcclosure(function(...)
		local method = getnamecallmethod()
		local args = {...}
		if tostring(method) == "FireServer" then
			if tostring(args[1]) == "RemoteEvent" then
				if tostring(args[2]) ~= "true" and tostring(args[2]) ~= "false" then
					if _G.Aimbot_Skill_Fov then
						args[2] = _G.Aim_Players.Character.HumanoidRootPart.Position
						return old(unpack(args))
					end
				end
			end
		end
		return old(...)
	end)
end)

 
--------------------------------------------------------------------
local Library = Update:Window("t7gfy-YT ","")
------------------------------------------

spawn(function()
 game:GetService("RunService").Heartbeat:Connect(function()
  pcall(function()
   for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
   if _G.Auto_Farm_Ectoplasm and StartMagnetEctoplasm and string.find(v.Name, "Ship") and (v.HumanoidRootPart.Position - PosMonEctoplasm.Position).magnitude <= 350 then
   v.HumanoidRootPart.CFrame = PosMonEctoplasm
   v.HumanoidRootPart.CanCollide = false
   v.HumanoidRootPart.Size = Vector3.new(50,50,50)
   if v.Humanoid:FindFirstChild("Animator") then
   v.Humanoid.Animator:Destroy()
   end
   sethiddenproperty(game.Players.LocalPlayer, "SimulationRadius", math.huge)
   end
   end
   end)
  end)
 end)

spawn(function()
 while wait() do
 if _G.Auto_Farm_Ectoplasm then
 pcall(function()
  if game:GetService("Workspace").Enemies:FindFirstChild("Ship Deckhand [Lv. 1250]") or game:GetService("Workspace").Enemies:FindFirstChild("Ship Engineer [Lv. 1275]") or game:GetService("Workspace").Enemies:FindFirstChild("Ship Steward [Lv. 1300]") or game:GetService("Workspace").Enemies:FindFirstChild("Ship Officer [Lv. 1325]") then
  for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
  if string.find(v.Name, "Ship") then
  repeat wait()
  AutoHaki()
  Equipgui(_G.Select_gui)
  PosMonEctoplasm = v.HumanoidRootPart.CFrame
  v.HumanoidRootPart.CanCollide = false
  v.HumanoidRootPart.Size = Vector3.new(50,50,50)
  topos(v.HumanoidRootPart.CFrame * MethodFarm)
  StartMagnetEctoplasm = true
  game:GetService'VirtualUser':CaptureController()
  game:GetService'VirtualUser':Button1Down(Vector2.new(1280, 672))
  until _G.Auto_Farm_Ectoplasm == false or not v.Parent or v.Humanoid.Health <= 0
  StartMagnetEctoplasm = false
  else
   StartMagnetEctoplasm = false
  topos(CFrame.new(904.4072265625, 181.05767822266, 33341.38671875))
  end
  end
  else
   StartMagnetEctoplasm = false
  local Distance = (Vector3.new(904.4072265625, 181.05767822266, 33341.38671875) - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude
  if Distance > 20000 then
  game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(923.21252441406, 126.9760055542, 32852.83203125))
  end
  topos(CFrame.new(904.4072265625, 181.05767822266, 33341.38671875))
  end
  end)
 end
 end
 end)

spawn(function()
 game:GetService("RunService").Heartbeat:Connect(function()
  pcall(function()
   for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
   if _G.Auto_Farm_Bone and StartMagnetBoneMon and (v.Name == "Reborn Skeleton [Lv. 1975]" or v.Name == "Living Zombie [Lv. 2000]" or v.Name == "Demonic Soul [Lv. 2025]" or v.Name == "Posessed Mummy [Lv. 2050]") and (v.HumanoidRootPart.Position - PosMonBone.Position).magnitude <= 350 then
   v.HumanoidRootPart.CFrame = PosMonBone
   v.HumanoidRootPart.CanCollide = false
   v.HumanoidRootPart.Size = Vector3.new(50,50,50)
   if v.Humanoid:FindFirstChild("Animator") then
   v.Humanoid.Animator:Destroy()
   end
   sethiddenproperty(game.Players.LocalPlayer, "SimulationRadius", math.huge)
   end
   end
   end)
  end)
 end)

spawn(function()
 while wait() do
 if _G.Auto_Farm_Bone and World3 then
 pcall(function()
  if game:GetService("Workspace").Enemies:FindFirstChild("Reborn Skeleton [Lv. 1975]") or game:GetService("Workspace").Enemies:FindFirstChild("Living Zombie [Lv. 2000]") or game:GetService("Workspace").Enemies:FindFirstChild("Domenic Soul [Lv. 2025]") or game:GetService("Workspace").Enemies:FindFirstChild("Posessed Mummy [Lv. 2050]") then
  for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
  if v.Name == "Reborn Skeleton [Lv. 1975]" or v.Name == "Living Zombie [Lv. 2000]" or v.Name == "Demonic Soul [Lv. 2025]" or v.Name == "Posessed Mummy [Lv. 2050]" then
  if v.Humanoid.Health > 0 then
  repeat wait()
  AutoHaki()
  Equipgui(_G.Select_gui)
  StartMagnetBoneMon = true
  v.HumanoidRootPart.CanCollide = false
  v.HumanoidRootPart.Size = Vector3.new(60, 60, 60)
  PosMonBone = v.HumanoidRootPart.CFrame
  topos(v.HumanoidRootPart.CFrame * MethodFarm)
  game:GetService'VirtualUser':CaptureController()
  game:GetService'VirtualUser':Button1Down(Vector2.new(1280, 672))
  until _G.Auto_Farm_Bone == false or not v.Parent or v.Humanoid.Health <= 0
  end
  end
  end
  else
   StartMagnetBoneMon = false
  for i,v in pairs(game:GetService("ReplicatedStorage"):GetChildren()) do
  if v.Name == "Reborn Skeleton [Lv. 1975]" then
  topos(v.HumanoidRootPart.CFrame * MethodFarm)
  elseif v.Name == "Living Zombie [Lv. 2000]" then
  topos(v.HumanoidRootPart.CFrame * MethodFarm)
  elseif v.Name == "Demonic Soul [Lv. 2025]" then
  topos(v.HumanoidRootPart.CFrame * MethodFarm)
  elseif v.Name == "Posessed Mummy [Lv. 2050]" then
  topos(v.HumanoidRootPart.CFrame * MethodFarm)
  end
  end
  topos(CFrame.new(-9466.72949, 171.162918, 6132.01514))
  end
  end)
 end
 end
 end)

spawn(function()
    game:GetService("RunService").Heartbeat:Connect(function() CheckQuest()
		pcall(function()
			for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
				if _G.Auto_Farm_Level and MasteryBFStartMagnetActive and v.Name == Ms and (v.HumanoidRootPart.Position - PosMonMasteryFruit.Position).magnitude <= 350 then
					v.HumanoidRootPart.CFrame = PosMonMasteryFruit
					v.HumanoidRootPart.CanCollide = false
					v.HumanoidRootPart.Size = Vector3.new(50,50,50)
					if v.Humanoid:FindFirstChild("Animator") then
						v.Humanoid.Animator:Destroy()
					end
					sethiddenproperty(game.Players.LocalPlayer, "SimulationRadius",  math.huge)
				end
			end
		end)
    end)
end)

spawn(function()
    game:GetService("RunService").Heartbeat:Connect(function() CheckQuest()
		pcall(function()
			for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
				if _G.Auto_Farm_Level and MasteryGunStartMagnetActive and v.Name == Ms and (v.HumanoidRootPart.Position - PosMonMasteryGun.Position).magnitude <= 350 then
					v.HumanoidRootPart.CFrame = PosMonMasteryGun
					v.HumanoidRootPart.CanCollide = false
					v.HumanoidRootPart.Size = Vector3.new(50,50,50)
					if v.Humanoid:FindFirstChild("Animator") then
						v.Humanoid.Animator:Destroy()
					end
					sethiddenproperty(game.Players.LocalPlayer, "SimulationRadius",  math.huge)
				end
			end
		end)
    end)
end)

spawn(function()
    while wait() do
        if _G.Auto_Farm_Level then
			if _G.Select_Mode_Farm == "Level Farm" then
				pcall(function()
					if not string.find(game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Container.QuestTitle.Title.Text, NameMon) then
						StartMagnet = false
						game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("AbandonQuest")
					end
					if game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == false then
						StartMagnet = false
						CheckQuest()
						repeat wait() topos(CFrameQuest) until (CFrameQuest.Position - game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 3 or not _G.Auto_Farm_Level
						if (CFrameQuest.Position - game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 3 then
							wait(1.2)
							game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("StartQuest",NameQuest,LevelQuest)
							wait(0.5)
						end
					elseif game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == true then
						CheckQuest()
						if game:GetService("Workspace").Enemies:FindFirstChild(Ms) then
							for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
								if v:FindFirstChild("HumanoidRootPart") and v:FindFirstChild("Humanoid") and v.Humanoid.Health > 0 then
									if v.Name == Ms then
										repeat wait()
											if string.find(game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Container.QuestTitle.Title.Text, NameMon) then
												Equipgui(_G.Select_gui)
												AutoHaki()
												PosMon = v.HumanoidRootPart.CFrame
												v.HumanoidRootPart.CanCollide = false
												v.Humanoid.WalkSpeed = 0
												v.Head.CanCollide = false
												v.HumanoidRootPart.Size = Vector3.new(50,50,50)
												StartMagnet = true
												topos(v.HumanoidRootPart.CFrame * MethodFarm)
												game:GetService'VirtualUser':CaptureController()
												game:GetService'VirtualUser':Button1Down(Vector2.new(1280, 672))
											else
												StartMagnet = false
												game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("AbandonQuest")
											end
										until not _G.Auto_Farm_Level or v.Humanoid.Health <= 0 or not v.Parent or game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == false
									end
								end
							end
						else
							StartMagnet = false
							if game:GetService("ReplicatedStorage"):FindFirstChild(Ms) then
								topos(game:GetService("ReplicatedStorage"):FindFirstChild(Ms).HumanoidRootPart.CFrame * CFrame.new(0,20,0))
							else	
								topos(CFrameMon)
							end
						end
					end
				end)
			elseif _G.Select_Mode_Farm == "Fast Mode" then
				pcall(function()
					if game:GetService("Players").LocalPlayer.Data.SpawnPoint.Value == SPAWNPOINT then
						if not string.find(game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Container.QuestTitle.Title.Text, NameMon) then
							StartMagnet = false
							game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("AbandonQuest")
						end
						if game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == false then
							StartMagnet = false
							CheckQuest()
							game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("StartQuest",NameQuest,LevelQuest)
						elseif game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == true then
							CheckQuest()
							if game:GetService("Workspace").Enemies:FindFirstChild(Ms) then
								for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
									if v:FindFirstChild("HumanoidRootPart") and v:FindFirstChild("Humanoid") and v.Humanoid.Health > 0 then
										if v.Name == Ms then
											repeat wait()
												if string.find(game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Container.QuestTitle.Title.Text, NameMon) then
													Equipgui(_G.Select_gui)
													AutoHaki()
													PosMon = v.HumanoidRootPart.CFrame
													v.HumanoidRootPart.CanCollide = false
													v.Humanoid.WalkSpeed = 0
													v.Head.CanCollide = false
													v.HumanoidRootPart.Size = Vector3.new(50,50,50)
													StartMagnet = true
													topos(v.HumanoidRootPart.CFrame * MethodFarm)
													game:GetService'VirtualUser':CaptureController()
													game:GetService'VirtualUser':Button1Down(Vector2.new(1280, 672))
												else
													StartMagnet = false
													game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("AbandonQuest")
												end
											until not _G.Auto_Farm_Level or v.Humanoid.Health <= 0 or not v.Parent or game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == false
										end
									end
								end
							else
								StartMagnet = false
								if game:GetService("ReplicatedStorage"):FindFirstChild(Ms) then
									topos(game:GetService("ReplicatedStorage"):FindFirstChild(Ms).HumanoidRootPart.CFrame * CFrame.new(0,20,0))
								else	
									topos(CFrameMon)
								end
							end
						end
					else
						repeat task.wait()
							game.Players.LocalPlayer.Character.Head:Destroy()
							wait(0.5)
							game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrameQuest
							game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("SetSpawnPoint")
						until game:GetService("Players").LocalPlayer.Data.SpawnPoint.Value == SPAWNPOINT 
					end
                end)
            elseif _G.Select_Mode_Farm == "No Quest" then
				pcall(function()
                	CheckQuest()
					if game:GetService("Workspace").Enemies:FindFirstChild(Ms) then
						for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
							if v:FindFirstChild("HumanoidRootPart") and v:FindFirstChild("Humanoid") and v.Humanoid.Health > 0 then
								if v.Name == Ms then
									if v.Humanoid.Health > 0 then
										repeat wait()
											Equipgui(_G.Select_gui)
											AutoHaki()
											PosMon = v.HumanoidRootPart.CFrame
											v.HumanoidRootPart.CanCollide = false
											v.Humanoid.WalkSpeed = 0
											v.Head.CanCollide = false
											v.HumanoidRootPart.Size = Vector3.new(50,50,50)
											StartMagnet = true
											topos(v.HumanoidRootPart.CFrame * MethodFarm)
											game:GetService'VirtualUser':CaptureController()
											game:GetService'VirtualUser':Button1Down(Vector2.new(1280, 672))
										until not _G.Auto_Farm_Level or v.Humanoid.Health <= 0 or not v.Parent
									end
								end
							end
						end
					else
						StartMagnet = false
						if game:GetService("ReplicatedStorage"):FindFirstChild(Ms) then
							topos(game:GetService("ReplicatedStorage"):FindFirstChild(Ms).HumanoidRootPart.CFrame * CFrame.new(0,20,0))
						else	
							topos(CFrameMon)
						end
					end
				end)
elseif _G.Select_Mode_Farm == "Near Farm Mode" then
  for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
  if v.Name and v:FindFirstChild("Humanoid") then
  if v.Humanoid.Health > 0 then
  repeat game:GetService("RunService").Heartbeat:wait()
  Equipgui(_G.Select_gui)
  if not game.Players.LocalPlayer.Character:FindFirstChild("HasBuso") then
  local args = {
   [1] = "Buso"
  }
  game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
  end
  PosMon = v.HumanoidRootPart.CFrame
 v.HumanoidRootPart.CanCollide = false
 v.Humanoid.WalkSpeed = 0
 v.Head.CanCollide = false
 v.HumanoidRootPart.Size = Vector3.new(60,60,60)
 StartMagnet = false
 topos(v.HumanoidRootPart.CFrame * MethodFarm)
 game:GetService'VirtualUser':CaptureController()
 game:GetService'VirtualUser':Button1Down(Vector2.new(1280, 672))
  StartMagnet = true
  PosMon = v.HumanoidRootPart.CFrame
  until not _G.Auto_Farm_Level or not v.Parent or v.Humanoid.Health == 0 or not game.Workspace.Enemies:FindFirstChild(v.Name)
  end
		end
    end
end
end
end
end)

spawn(function()
 while wait() do
 if _G.Auto_New_World then
 pcall(function()
  if game.Players.LocalPlayer.Data.Level.Value >= 700 and World1 then
  _G.Auto_Farm_Level = false
  if game.Workspace.Map.Ice.Door.CanCollide == true and game.Workspace.Map.Ice.Door.Transparency == 0 then
  repeat wait() topos(CFrame.new(4851.8720703125, 5.6514348983765, 718.47094726563)) until (CFrame.new(4851.8720703125, 5.6514348983765, 718.47094726563).Position - game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 3 or not _G.Auto_New_World
  wait(1)
  game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("DressrosaQuestProgress","Detective")
  Equipgui("Key")
  local pos2 = CFrame.new(1347.7124, 37.3751602, -1325.6488)
  repeat wait() topos(pos2) until (pos2.Position - game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 3 or not _G.Auto_New_World
  wait(3)
  elseif game.Workspace.Map.Ice.Door.CanCollide == false and game.Workspace.Map.Ice.Door.Transparency == 1 then
  if game:GetService("Workspace").Enemies:FindFirstChild("Ice Admiral [Lv. 700] [Boss]") then
  for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
  if v.Name == "Ice Admiral [Lv. 700] [Boss]" and v.Humanoid.Health > 0 then
  repeat wait()
  AutoHaki()
  Equipgui(_G.Select_gui)
  v.HumanoidRootPart.CanCollide = false
  v.HumanoidRootPart.Size = Vector3.new(60,60,60)
  v.HumanoidRootPart.Transparency = 1
  topos(v.HumanoidRootPart.CFrame * MethodFarm)
  game:GetService("VirtualUser"):CaptureController()
  game:GetService("VirtualUser"):Button1Down(Vector2.new(1280, 870),workspace.CurrentCamera.CFrame)
  until v.Humanoid.Health <= 0 or not v.Parent or not _G.Auto_New_World
  game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("TravelDressrosa")
  end
  end
  else
   topos(CFrame.new(1347.7124, 37.3751602, -1325.6488))
  end
  else
   game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("TravelDressrosa")
  end
  end
  end)
 end
 end
 end)

spawn(function()
 while wait() do
 if _G.Auto_Third_World then
 pcall(function()
  if game:GetService("Players").LocalPlayer.Data.Level.Value >= 1500 and World2 then
  _G.Auto_Farm_Level = false
  if game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("QuestProgress","Check") == 0 then
  topos(CFrame.new(-1926.3221435547, 12.819851875305, 1738.3092041016))
  if (CFrame.new(-1926.3221435547, 12.819851875305, 1738.3092041016).Position - game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 10 then
  wait(1.5)
  game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("QuestProgress","Begin")
  end
  wait(1.8)
  if game:GetService("Workspace").Enemies:FindFirstChild("rip_indra [Lv. 1500] [Boss]") then
  for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
  if v.Name == "rip_indra [Lv. 1500] [Boss]" then
  OldCFrameThird = v.HumanoidRootPart.CFrame
  repeat wait()
  AutoHaki()
  Equipgui(_G.Select_gui)
  v.HumanoidRootPart.CFrame = OldCFrameThird
  v.HumanoidRootPart.Size = Vector3.new(50,50,50)
  v.HumanoidRootPart.CanCollide = false
  v.Humanoid.WalkSpeed = 0
  topos(v.HumanoidRootPart.CFrame * MethodFarm)
  game:GetService'VirtualUser':CaptureController()
  game:GetService'VirtualUser':Button1Down(Vector2.new(1280, 672))
  game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("TravelZou")
  sethiddenproperty(game:GetService("Players").LocalPlayer,"SimulationRadius",math.huge)
  until _G.Auto_Third_World == false or v.Humanoid.Health <= 0 or not v.Parent
  end
  end
  elseif not game:GetService("Workspace").Enemies:FindFirstChild("rip_indra [Lv. 1500] [Boss]") and (CFrame.new(-26880.93359375, 22.848554611206, 473.18951416016).Position - game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 1000 then
  topos(CFrame.new(-26880.93359375, 22.848554611206, 473.18951416016))
  end
  end
  end
  end)
 end
 end
end)

--------------------------
local Main = Library:Tab("Main","rbxassetid://11446825283")
local Setting = Library:Tab("Settings","rbxassetid://11446835336")
local gui = Library:Tab("guis","rbxassetid://11446859498")
local Race = Library:Tab("Race V4","rbxassetid://11446900930")
local Stats = Library:Tab("Stats","rbxassetid://11447069304")
local P = Library:Tab("Player","rbxassetid://11446900930")
local Teleport = Library:Tab("Teleport","rbxassetid://11446920523")
local Dungeon = Library:Tab("Dungeon","rbxassetid://11446957539")
local DevilFruit = Library:Tab("Fruit+Esp","rbxassetid://11446965348")
local Shop = Library:Tab("Shop","rbxassetid://6031265976")
local Misc = Library:Tab("Misc","rbxassetid://11447063791")
local Op = Library:Tab("Status", "rbxassetid://7040410130")
--------------------------------------------------------------------

Setting:Label("get free premeum!!!")

Setting:Line()

Setting:Button(" lebgdj ",function()
 
 setclipboard("https://www.youtube.com/@tlebgdj12")
 end)

Setting:Seperator(" Setting ")
Setting:Toggle("Auto Set Spawn Points",true,function(value)
 _G.AutoSetSpawn = value
 end)

spawn(function()
 pcall(function()
  while wait() do
  if _G.AutoSetSpawn then
  if game:GetService("Players").LocalPlayer.Character.Humanoid.Health > 0 then
  game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("SetSpawnPoint")
  end
  end
  end
  end)
 end)

Setting:Toggle("Anti AFK",true,function(value)
 _G.AFK = value
 end)

if not game:GetService("UserInputService").TouchEnabled and not game:GetService("UserInputService").KeyboardEnabled == false then
_G.DistanceMob = 20
Setting:Slider("Farm Distance",1,100,20,function(value)
 _G.DistanceMob = value
 end)
else
 _G.DistanceMob = 20
Setting:Slider1("Farm Distance",1,100,20,function(value)
 _G.DistanceMob = value
 end)
end

Setting:Dropdown("Select Farm Method", {
 "Behind","Below","Upper"
},function(value)
 _G.Method = value
end)


Setting:Toggle("White Screen [ Booster FPS ]",_G.WhiteScreen,function(value)
 _G.WhiteScreen = value

 if _G.WhiteScreen == true then
 game:GetService("RunService"):Set3dRenderingEnabled(false)
 elseif _G.WhiteScreen == false then
 game:GetService("RunService"):Set3dRenderingEnabled(true)
 end
end)


    Setting:Button("FPS Boost",function()
        pcall(function()
            game:GetService("Lighting").FantasySky:Destroy()
            local g = game
            local w = g.Workspace
            local l = g.Lighting
            local t = w.Terrain
            t.WaterWaveSize = 0
            t.WaterWaveSpeed = 0
            t.WaterReflectance = 0
            t.WaterTransparency = 0
            l.GlobalShadows = false
            l.FogEnd = 9e9
            l.Brightness = 0
            settings().Rendering.QualityLevel = "Level01"
            for i, v in pairs(g:GetDescendants()) do
                if v:IsA("Part") or v:IsA("Union") or v:IsA("CornerWedgePart") or v:IsA("TrussPart") then 
                    v.Material = "Plastic"
                    v.Reflectance = 0
                elseif v:IsA("Decal") or v:IsA("Texture") then
                    v.Transparency = 1
                elseif v:IsA("ParticleEmitter") or v:IsA("Trail") then
                    v.Lifetime = NumberRange.new(0)
                elseif v:IsA("Explosion") then
                    v.BlastPressure = 1
                    v.BlastRadius = 1
                elseif v:IsA("Fire") or v:IsA("SpotLight") or v:IsA("Smoke") or v:IsA("Sparkles") then
                    v.Enabled = false
                elseif v:IsA("MeshPart") then
                    v.Material = "Plastic"
                    v.Reflectance = 0
                    v.TextureID = 10385902758728957
                end
            end
            for i, e in pairs(l:GetChildren()) do
                if e:IsA("BlurEffect") or e:IsA("SunRaysEffect") or e:IsA("ColorCorrectionEffect") or e:IsA("BloomEffect") or e:IsA("DepthOfFieldEffect") then
                    e.Enabled = false
                end
            end
            for i, v in pairs(game:GetService("Workspace").Camera:GetDescendants()) do
                if v.Name == ("Water;") then
                    v.Transparency = 1
                    v.Material = "Plastic"
                end
            end
        end)
    end)


Setting:Seperator(" Settings Mastery ")

if not game:GetService("UserInputService").TouchEnabled and not game:GetService("UserInputService").KeyboardEnabled == false then
_G.Kill_At = 25
Setting:Slider("Kill Health [For Mastery]",1,100,25,function(value)
 _G.Kill_At = value
end)
else
_G.Kill_At = 25
Setting:Slider1("Kill Health [For Mastery]",1,100,25,function(value)
 _G.Kill_At = value
end)
end

Setting:Toggle("Skill Z",true,function(a)
		_G.SkillZ = a
	end)
	Setting:Toggle("Skill X",true,function(a)
		_G.SkillX = a
	end)
	Setting:Toggle("Skill C",true,function(a)
		_G.SkillC = a
	end)
	Setting:Toggle("Skill V",true,function(a)
		_G.SkillV = a
	end)

Main:Seperator(" Server ")

Time = Main:Label("Executer Time")

function UpdateTime()
local GameTime = math.floor(workspace.DistributedGameTime+0.5)
local Hour = math.floor(GameTime/(60^2))%24
local Minute = math.floor(GameTime/(60^1))%60
local Second = math.floor(GameTime/(60^0))%60
Time:Set("[GameTime] : Hours : "..Hour.." Minutes : "..Minute.." Seconds : "..Second)
end

spawn(function()
 while task.wait() do
 pcall(function()
  UpdateTime()
  end)
 end
 end)

Client = Main:Label1("Client")

function UpdateClient()
local Fps = workspace:GetRealPhysicsFPS()
Client:Refresh("[Fps] : "..Fps)
end

spawn(function()
 while true do wait(.1)
 UpdateClient()
 end
 end)

Client1 = Main:Label1("Client")

function UpdateClient1()
local Ping = game:GetService("Stats").Network.ServerStatsItem["Data Ping"]:GetValueString()
Client1:Refresh("[Ping] : "..Ping)
end

spawn(function()
 while true do wait(.1)
 UpdateClient1()
 end
 end)


Main:Line()

function Equipgui(ToolSe)
if not _G.NotAutoEquip then
if game.Players.LocalPlayer.Backpack:FindFirstChild(ToolSe) then
Tool = game.Players.LocalPlayer.Backpack:FindFirstChild(ToolSe)
wait(.1)
game.Players.LocalPlayer.Character.Humanoid:EquipTool(Tool)
end
end
end

if _G.Select_gui == nil then
for i,v in pairs(game:GetService("Players").LocalPlayer.Backpack:GetChildren()) do
if v.ToolTip == "Melee" then
if game.Players.LocalPlayer.Backpack:FindFirstChild(tostring(v.Name)) then
_G.Select_gui = tostring(v.Name)
end
end
end
end

guiList = {}

for i,v in pairs(game:GetService("Players").LocalPlayer.Backpack:GetChildren()) do
if v:IsA("Tool") then
table.insert(guiList ,v.Name)
end
end
local Selectguia = Main:Dropdown("Select gui",guiList,function(value)
 _G.Select_gui = value
 end)

Main:Button("Refresh gui",function()
 Selectguia:Clear()
 for i,v in pairs(game:GetService("Players").LocalPlayer.Backpack:GetChildren()) do
 Selectguia:Add(v.Name)
 end
end)

spawn(function()
    game:GetService("RunService").RenderStepped:Connect(function()
        if _G.click then
             pcall(function()
                game:GetService'VirtualUser':CaptureController()
			    game:GetService'VirtualUser':Button1Down(Vector2.new(0,1,0,1))
            end)
        end
    end)
end)

Main:Button("Stop Teleport",function()
  topos(game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame)
  _G.Clip = false
  end)

Main:Seperator(" Main ")

Main:Dropdown("Select Mode Farm", {
 "Level Farm","Fast Mode","No Quest","Near Farm Mode"
},function(value)
 _G.Select_Mode_Farm = value
end)

Main:Toggle("Start Auto Farm",_G.Auto_Farm_Level,function(value)
 _G.Auto_Farm_Level = value
 StopTween(_G.Auto_Farm_Level)
end)


function EquipguiSword()
pcall(function()
	for i,v in pairs(game.Players.LocalPlayer.Backpack:GetChildren()) do
		if v.ToolTip == "Sword" and v:IsA('Tool') then
			local ToolHumanoid = game.Players.LocalPlayer.Backpack:FindFirstChild(v.Name) 
			game.Players.LocalPlayer.Character.Humanoid:EquipTool(ToolHumanoid) 
		end
	end
end)
end

function EquipguiMelee()
pcall(function()
	for i,v in pairs(game.Players.LocalPlayer.Backpack:GetChildren()) do
		if v.ToolTip == "Melee" and v:IsA('Tool') then
			local ToolHumanoid = game.Players.LocalPlayer.Backpack:FindFirstChild(v.Name) 
			game.Players.LocalPlayer.Character.Humanoid:EquipTool(ToolHumanoid) 
		end
	end
end)
end

		

if World2 then

Main:Seperator("Auto New Sea")

Main:Toggle("Auto Third Sea",_G.Auto_Third_World,function(value)
 _G.Auto_Third_World = value
 StopTween(_G.Auto_Third_World)
 end)

Main:Seperator("Ectoplasm")

Main:Toggle("Auto Farm Ectoplasm",_G.Auto_Farm_Ectoplasm,function(value)
 _G.Auto_Farm_Ectoplasm = value
 StopTween(_G.Auto_Farm_Ectoplasm)
 end)

Main:Seperator("Factory")

Main:Toggle("Auto Farm Factory",_G.AutoFactory,function(value)
 _G.AutoFactory = value
 StopTween(_G.AutoFactory)
 end)

spawn(function()
 while wait() do
 pcall(function()
  if _G.AutoFactory then
  if game:GetService("Workspace").Enemies:FindFirstChild("Core") then
  for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
  if v.Name == "Core" and v.Humanoid.Health > 0 then
  repeat task.wait()
  AutoHaki()
  Equipgui(_G.Select_gui)
  topos(CFrame.new(448.46756, 199.356781, -441.389252))
  game:GetService("VirtualUser"):CaptureController()
  game:GetService("VirtualUser"):Button1Down(Vector2.new(1280,672))
  until v.Humanoid.Health <= 0 or _G.AutoFactory == false
  end
  end
  else
   topos(CFrame.new(448.46756, 199.356781, -441.389252))
  end
  end
  end)
 end
 end)
end

if World1 then

Main:Seperator("Auto New Sea")

Main:Toggle("Auto Second Sea",_G.Auto_New_World,function(value)
 _G.Auto_New_World = value
 StopTween(_G.Auto_New_World)
 end)
end

-- Farm_Monster
if World1 then
tableMon = {
 "Bandit [Lv. 5]","Monkey [Lv. 14]","Gorilla [Lv. 20]","Pirate [Lv. 35]","Brute [Lv. 45]","Desert Bandit [Lv. 60]","Desert Officer [Lv. 70]","Snow Bandit [Lv. 90]","Snowman [Lv. 100]","Chief Petty Officer [Lv. 120]","Sky Bandit [Lv. 150]","Dark Master [Lv. 175]","Prisoner [Lv. 190]", "Dangerous Prisoner [Lv. 210]","Toga Warrior [Lv. 250]","Gladiator [Lv. 275]","Military Soldier [Lv. 300]","Military Spy [Lv. 325]","Fishman Warrior [Lv. 375]","Fishman Commando [Lv. 400]","God's Guard [Lv. 450]","Shanda [Lv. 475]","Royal Squad [Lv. 525]","Royal Soldier [Lv. 550]","Galley Pirate [Lv. 625]","Galley Captain [Lv. 650]"
} elseif World2 then
tableMon = {
 "Raider [Lv. 700]","Mercenary [Lv. 725]","Swan Pirate [Lv. 775]","Factory Staff [Lv. 800]","Marine Lieutenant [Lv. 875]","Marine Captain [Lv. 900]","Zombie [Lv. 950]","Vampire [Lv. 975]","Snow Trooper [Lv. 1000]","Winter Warrior [Lv. 1050]","Lab Subordinate [Lv. 1100]","Horned Warrior [Lv. 1125]","Magma Ninja [Lv. 1175]","Lava Pirate [Lv. 1200]","Ship Deckhand [Lv. 1250]","Ship Engineer [Lv. 1275]","Ship Steward [Lv. 1300]","Ship Officer [Lv. 1325]","Arctic Warrior [Lv. 1350]","Snow Lurker [Lv. 1375]","Sea Soldier [Lv. 1425]","Water Fighter [Lv. 1450]"
} elseif World3 then
tableMon = {
 "Pirate Millionaire [Lv. 1500]","Dragon Crew Warrior [Lv. 1575]","Dragon Crew Archer [Lv. 1600]","Female Islander [Lv. 1625]","Giant Islander [Lv. 1650]","Marine Commodore [Lv. 1700]","Marine Rear Admiral [Lv. 1725]","Fishman Raider [Lv. 1775]","Fishman Captain [Lv. 1800]","Forest Pirate [Lv. 1825]","Mythological Pirate [Lv. 1850]","Jungle Pirate [Lv. 1900]","Musketeer Pirate [Lv. 1925]","Reborn Skeleton [Lv. 1975]","Living Zombie [Lv. 2000]","Demonic Soul [Lv. 2025]","Posessed Mummy [Lv. 2050]", "Peanut Scout [Lv. 2075]", "Peanut President [Lv. 2100]", "Ice Cream Chef [Lv. 2125]", "Ice Cream Commander [Lv. 2150]", "Cookie Crafter [Lv. 2200]", "Cake Guard [Lv. 2225]", "Baking Staff [Lv. 2250]", "Head Baker [Lv. 2275]", "Cocoa Warrior [Lv. 2300]", "Chocolate Bar Battler [Lv. 2325]", "Sweet Thief [Lv. 2350]", "Candy Rebel [Lv. 2375]", "Candy Pirate [Lv. 2400]", "Snow Demon [Lv. 2425]"
}
end

Main:Seperator(" Other ")

Main:Dropdown("Select Monster", tableMon, function(vu)
 SelectMonster = vu
 end)

Main:Toggle("Farm Selected Monster",_G.AutoFarmSelectMonster,function(vu)
 _G.AutoFarmSelectMonster = vu
end)

spawn(function()
 while wait(.1) do
 if _G.AutoFarmSelectMonster then
 pcall(function()
  checkselect(SelectMonster)
  if game:GetService("Workspace").Enemies:FindFirstChild(SelectMonster) then
  for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
  if v.Name == SelectMonster then
  if v:FindFirstChild("Humanoid") then
  if v.Humanoid.Health > 0 then
  repeat game:GetService("RunService").Heartbeat:wait()
  Equipgui(_G.Select_gui)
  if not game.Players.LocalPlayer.Character:FindFirstChild("HasBuso") then
  local args = {
   [1] = "Buso"
  }
  game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
  end
  topos(v.HumanoidRootPart.CFrame * CFrame.new(0,30,0))
  v.HumanoidRootPart.CanCollide = false
  v.HumanoidRootPart.Size = Vector3.new(60, 60, 60)
  game:GetService("VirtualUser"):CaptureController()
  game:GetService("VirtualUser"):Button1Down(Vector2.new(1280, 672), game.Workspace.CurrentCamera.CFrame)
  PosMonSelectMonster = v.HumanoidRootPart.CFrame
  SelectMonsterMagnet = true
  until not _G.AutoFarmSelectMonster or not v.Parent or v.Humanoid.Health == 0 or not game:GetService("Workspace").Enemies:FindFirstChild(v.Name)
  end
  end
  end
  end
  else
   checkselect(SelectMonster)
  SelectMonsterMagnet = false
  topos(CFrameMon)
  end
  end)
 end
 end
end)

Main:Seperator(" Mastery ")
 
Main:Toggle("Auto BF Mastery",_G.AutoFarmFruitMastery,function(value)
  _G.AutoFarmFruitMastery = value
  StopTween(_G.AutoFarmFruitMastery)
  if _G.AutoFarmFruitMastery == false then
  UseSkill = false
  end
  end)
 
 spawn(function()
  while wait() do
  if _G.AutoFarmFruitMastery then
  pcall(function()
   local QuestTitle = game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Container.QuestTitle.Title.Text
   if not string.find(QuestTitle, NameMon) then
   StartMagnet = false
   UseSkill = false
   game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("AbandonQuest")
   end
   if game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == false then
   StartMasteryFruitStartMagnet = false
   UseSkill = false
   CheckQuest()
   repeat wait()
   topos(CFrameQuest)
   until (CFrameQuest.Position - game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 3 or not _G.AutoFarmFruitMastery
   if (CFrameQuest.Position - game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 3 then
   wait(1.2)
   game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("StartQuest",NameQuest,LevelQuest)
   wait(0.5)
   end
   elseif game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == true then
   CheckQuest()
   if game:GetService("Workspace").Enemies:FindFirstChild(Ms) then
   for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
   if v:FindFirstChild("HumanoidRootPart") and v:FindFirstChild("Humanoid") and v.Humanoid.Health > 0 then
   if v.Name == Ms then
   if string.find(game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Container.QuestTitle.Title.Text, NameMon) then
   HealthMs = v.Humanoid.MaxHealth * _G.Kill_At/100
   repeat task.wait()
   if v.Humanoid.Health <= HealthMs then
   AutoHaki()
   Equipgui(game:GetService("Players").LocalPlayer.Data.DevilFruit.Value)
   topos(v.HumanoidRootPart.CFrame * MethodFarm)
   v.HumanoidRootPart.CanCollide = false
   PosMonMasteryFruit = v.HumanoidRootPart.CFrame
   v.Humanoid.WalkSpeed = 0
   v.Head.CanCollide = false
   UseSkill = true
   else
    UseSkill = false
   AutoHaki()
   Equipgui(_G.Select_gui)
   topos(v.HumanoidRootPart.CFrame * MethodFarm)
   v.HumanoidRootPart.CanCollide = false
   v.HumanoidRootPart.Size = Vector3.new(50,50,50)
   PosMonMasteryFruit = v.HumanoidRootPart.CFrame
   v.Humanoid.WalkSpeed = 0
   v.Head.CanCollide = false
   end
   StartMasteryFruitStartMagnet = true
   game:GetService'VirtualUser':CaptureController()
   game:GetService'VirtualUser':Button1Down(Vector2.new(1280, 672))
   until not _G.AutoFarmFruitMastery or v.Humanoid.Health <= 0 or not v.Parent or game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == false
   else
    UseSkill = false
   StartMasteryFruitStartMagnet = false
   game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("AbandonQuest")
   end
   end
   end
   end
   else
    StartMasteryFruitStartMagnet = false
   UseSkill = false
   local Mob = game:GetService("ReplicatedStorage"):FindFirstChild(Ms)
   if Mob then
   topos(Mob.HumanoidRootPart.CFrame * MethodFarm)
   else
    if game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame.Y <= 1 then
   game:GetService("Players").LocalPlayer.Character.Humanoid.Jump = true
   task.wait()
   game:GetService("Players").LocalPlayer.Character.Humanoid.Jump = false
   end
   end
   end
   end
   end)
  end
  end
  end)
 
 spawn(function()
  while wait() do
  if UseSkill then
  pcall(function()
   CheckQuest()
   for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
   if game:GetService("Players").LocalPlayer.Character:FindFirstChild(game:GetService("Players").LocalPlayer.Data.DevilFruit.Value) then
   MasBF = game:GetService("Players").LocalPlayer.Character[game:GetService("Players").LocalPlayer.Data.DevilFruit.Value].Level.Value
   elseif game:GetService("Players").LocalPlayer.Backpack:FindFirstChild(game:GetService("Players").LocalPlayer.Data.DevilFruit.Value) then
   MasBF = game:GetService("Players").LocalPlayer.Backpack[game:GetService("Players").LocalPlayer.Data.DevilFruit.Value].Level.Value
   end
   if game:GetService("Players").LocalPlayer.Character:FindFirstChild("Dragon-Dragon") then
   if _G.SkillZ then
   local args = {
    [1] = PosMonMasteryFruit.Position
   }
   game:GetService("Players").LocalPlayer.Character[game:GetService("Players").LocalPlayer.Character:FindFirstChildOfClass("Tool").Name].RemoteEvent:FireServer(unpack(args))
   game:GetService("VirtualInputManager"):SendKeyEvent(true,"Z",false,game)
   game:GetService("VirtualInputManager"):SendKeyEvent(false,"Z",false,game)
   end
   if _G.SkillX then
   local args = {
    [1] = PosMonMasteryFruit.Position
   }
   game:GetService("Players").LocalPlayer.Character[game:GetService("Players").LocalPlayer.Character:FindFirstChildOfClass("Tool").Name].RemoteEvent:FireServer(unpack(args))
   game:GetService("VirtualInputManager"):SendKeyEvent(true,"X",false,game)
   game:GetService("VirtualInputManager"):SendKeyEvent(false,"X",false,game)
   end
   if _G.SkillC then
   local args = {
    [1] = PosMonMasteryFruit.Position
   }
   game:GetService("Players").LocalPlayer.Character[game:GetService("Players").LocalPlayer.Character:FindFirstChildOfClass("Tool").Name].RemoteEvent:FireServer(unpack(args))
   game:GetService("VirtualInputManager"):SendKeyEvent(true,"C",false,game)
   wait(2)
   game:GetService("VirtualInputManager"):SendKeyEvent(false,"C",false,game)
   end
   elseif game:GetService("Players").LocalPlayer.Character:FindFirstChild("Venom-Venom") then
   if _G.SkillZ then
   local args = {
    [1] = PosMonMasteryFruit.Position
   }
   game:GetService("Players").LocalPlayer.Character[game:GetService("Players").LocalPlayer.Character:FindFirstChildOfClass("Tool").Name].RemoteEvent:FireServer(unpack(args))
   game:GetService("VirtualInputManager"):SendKeyEvent(true,"Z",false,game)
   game:GetService("VirtualInputManager"):SendKeyEvent(false,"Z",false,game)
   end
   if _G.SkillX then
   local args = {
    [1] = PosMonMasteryFruit.Position
   }
   game:GetService("Players").LocalPlayer.Character[game:GetService("Players").LocalPlayer.Character:FindFirstChildOfClass("Tool").Name].RemoteEvent:FireServer(unpack(args))
   game:GetService("VirtualInputManager"):SendKeyEvent(true,"X",false,game)
   game:GetService("VirtualInputManager"):SendKeyEvent(false,"X",false,game)
   end
   if _G.SkillC then
   local args = {
    [1] = PosMonMasteryFruit.Position
   }
   game:GetService("Players").LocalPlayer.Character[game:GetService("Players").LocalPlayer.Character:FindFirstChildOfClass("Tool").Name].RemoteEvent:FireServer(unpack(args))
   game:GetService("VirtualInputManager"):SendKeyEvent(true,"C",false,game)
   wait(2)
   game:GetService("VirtualInputManager"):SendKeyEvent(false,"C",false,game)
   end
   elseif game:GetService("Players").LocalPlayer.Character:FindFirstChild("Human-Human: Buddha") then
   if _G.SkillZ and game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Size == Vector3.new(2, 2.0199999809265, 1) then
   local args = {
    [1] = PosMonMasteryFruit.Position
   }
   game:GetService("Players").LocalPlayer.Character[game:GetService("Players").LocalPlayer.Character:FindFirstChildOfClass("Tool").Name].RemoteEvent:FireServer(unpack(args))
   game:GetService("VirtualInputManager"):SendKeyEvent(true,"Z",false,game)
   game:GetService("VirtualInputManager"):SendKeyEvent(false,"Z",false,game)
   end
   if _G.SkillX then
   local args = {
    [1] = PosMonMasteryFruit.Position
   }
   game:GetService("Players").LocalPlayer.Character[game:GetService("Players").LocalPlayer.Character:FindFirstChildOfClass("Tool").Name].RemoteEvent:FireServer(unpack(args))
   game:GetService("VirtualInputManager"):SendKeyEvent(true,"X",false,game)
   game:GetService("VirtualInputManager"):SendKeyEvent(false,"X",false,game)
   end
   if _G.SkillC then
   local args = {
    [1] = PosMonMasteryFruit.Position
   }
   game:GetService("Players").LocalPlayer.Character[game:GetService("Players").LocalPlayer.Character:FindFirstChildOfClass("Tool").Name].RemoteEvent:FireServer(unpack(args))
   game:GetService("VirtualInputManager"):SendKeyEvent(true,"C",false,game)
   game:GetService("VirtualInputManager"):SendKeyEvent(false,"C",false,game)
   end
   if _G.SkillV then
   local args = {
    [1] = PosMonMasteryFruit.Position
   }
   game:GetService("Players").LocalPlayer.Character[game:GetService("Players").LocalPlayer.Character:FindFirstChildOfClass("Tool").Name].RemoteEvent:FireServer(unpack(args))
   game:GetService("VirtualInputManager"):SendKeyEvent(true,"V",false,game)
   game:GetService("VirtualInputManager"):SendKeyEvent(false,"V",false,game)
   end
   elseif game:GetService("Players").LocalPlayer.Character:FindFirstChild(game:GetService("Players").LocalPlayer.Data.DevilFruit.Value) then
   if _G.SkillZ then
   local args = {
    [1] = PosMonMasteryFruit.Position
   }
   game:GetService("Players").LocalPlayer.Character[game:GetService("Players").LocalPlayer.Character:FindFirstChildOfClass("Tool").Name].RemoteEvent:FireServer(unpack(args))
   game:GetService("VirtualInputManager"):SendKeyEvent(true,"Z",false,game)
   game:GetService("VirtualInputManager"):SendKeyEvent(false,"Z",false,game)
   end
   if _G.SkillX then
   local args = {
    [1] = PosMonMasteryFruit.Position
   }
   game:GetService("Players").LocalPlayer.Character[game:GetService("Players").LocalPlayer.Character:FindFirstChildOfClass("Tool").Name].RemoteEvent:FireServer(unpack(args))
   game:GetService("VirtualInputManager"):SendKeyEvent(true,"X",false,game)
   game:GetService("VirtualInputManager"):SendKeyEvent(false,"X",false,game)
   end
   if _G.SkillC then
   local args = {
    [1] = PosMonMasteryFruit.Position
   }
   game:GetService("Players").LocalPlayer.Character[game:GetService("Players").LocalPlayer.Character:FindFirstChildOfClass("Tool").Name].RemoteEvent:FireServer(unpack(args))
   game:GetService("VirtualInputManager"):SendKeyEvent(true,"C",false,game)
   game:GetService("VirtualInputManager"):SendKeyEvent(false,"C",false,game)
   end
   if _G.SkillV then
   local args = {
    [1] = PosMonMasteryFruit.Position
   }
   game:GetService("Players").LocalPlayer.Character[game:GetService("Players").LocalPlayer.Character:FindFirstChildOfClass("Tool").Name].RemoteEvent:FireServer(unpack(args))
   game:GetService("VirtualInputManager"):SendKeyEvent(true,"V",false,game)
   game:GetService("VirtualInputManager"):SendKeyEvent(false,"V",false,game)
   end
   end
   end
   end)
  end
  end
  end)
 
 spawn(function()
  game:GetService("RunService").RenderStepped:Connect(function()
   pcall(function()
    if UseSkill then
    for i,v in pairs(game:GetService("Players").LocalPlayer.PlayerGui.Notifications:GetChildren()) do
    if v.Name == "NotificationTemplate" then
    if string.find(v.Text,"Skill locked!") then
    v:Destroy()
    end
    end
    end
    end
    end)
   end)
  end)
 
 spawn(function()
  pcall(function()
   game:GetService("RunService").RenderStepped:Connect(function()
    if UseSkill then
    local args = {
     [1] = PosMonMasteryFruit.Position
    }
    game:GetService("Players").LocalPlayer.Character[game:GetService("Players").LocalPlayer.Data.DevilFruit.Value].RemoteEvent:FireServer(unpack(args))
    end
    end)
   end)
  end)
 
 Main:Toggle("Auto Gun Mastery",_G.AutoFarmGunMastery,function(value)
  _G.AutoFarmGunMastery = value
  StopTween(_G.AutoFarmGunMastery)
  end)
 
 spawn(function()
  pcall(function()
   while wait() do
   if _G.AutoFarmGunMastery then
   local QuestTitle = game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Container.QuestTitle.Title.Text
   if not string.find(QuestTitle, NameMon) then
   StartMagnet = false
   game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("AbandonQuest")
   end
   if game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == false then
   StartMasteryGunStartMagnet = false
   CheckQuest()
   topos(CFrameQuest)
   if (CFrameQuest.Position - game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 10 then
   wait(1.2)
   game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("StartQuest", NameQuest, LevelQuest)
   end
   elseif game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == true then
   CheckQuest()
   if game:GetService("Workspace").Enemies:FindFirstChild(Ms) then
   pcall(function()
    for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
    if v.Name == Ms then
    repeat task.wait()
    if string.find(game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Container.QuestTitle.Title.Text, NameMon) then
    HealthMs = v.Humanoid.MaxHealth * _G.Kill_At/100
    if v.Humanoid.Health <= HealthMs then
    Equipgui(SelectguiGun)
    topos(v.HumanoidRootPart.CFrame * MethodFarm)
    v.Humanoid.WalkSpeed = 0
    v.HumanoidRootPart.CanCollide = false
    v.HumanoidRootPart.Size = Vector3.new(2,2,1)
    v.Head.CanCollide = false
    local args = {
     [1] = v.HumanoidRootPart.Position,
     [2] = v.HumanoidRootPart
    }
    game:GetService("Players").LocalPlayer.Character[SelectguiGun].RemoteFunctionShoot:InvokeServer(unpack(args))
    else
     AutoHaki()
    Equipgui(_G.Select_gui)
    v.Humanoid.WalkSpeed = 0
    v.HumanoidRootPart.CanCollide = false
    v.Head.CanCollide = false
    v.HumanoidRootPart.Size = Vector3.new(50,50,50)
    topos(v.HumanoidRootPart.CFrame * MethodFarm)
    game:GetService'VirtualUser':CaptureController()
    game:GetService'VirtualUser':Button1Down(Vector2.new(1280, 672))
    end
    StartMasteryGunStartMagnet = true
    PosMonMasteryGun = v.HumanoidRootPart.CFrame
    else
     StartMasteryGunStartMagnet = false
    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("AbandonQuest")
    end
    until v.Humanoid.Health <= 0 or _G.AutoFarmGunMastery == false or game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == false
    StartMasteryGunStartMagnet = false
    end
    end
    end)
   else
    StartMasteryGunStartMagnet = false
   local Mob = game:GetService("ReplicatedStorage"):FindFirstChild(Ms)
   if Mob then
   topos(Mob.HumanoidRootPart.CFrame * MethodFarm)
   else
    if game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame.Y <= 1 then
   game:GetService("Players").LocalPlayer.Character.Humanoid.Jump = true
   task.wait()
   game:GetService("Players").LocalPlayer.Character.Humanoid.Jump = false
   end
   end
   end
   end
   end
   end
   end)
 end)

 
Main:Seperator(" Bosses ")

local Boss = {}
    
    for i, v in pairs(game:GetService("ReplicatedStorage"):GetChildren()) do
        if string.find(v.Name, "Boss") then
            if v.Name == "Ice Admiral [Lv. 700] [Boss]" then
                else
                table.insert(Boss, v.Name)
            end
        end
    end
    
    local BossName = Main:Dropdown("Select Boss",Boss,function(value)
       _G.Select_Boss = value
    end)
    
    Main:Button("Refresh Boss",function()
        BossName:Clear()
            for i, v in pairs(game:GetService("ReplicatedStorage"):GetChildren()) do
            if string.find(v.Name, "Boss") then
                BossName:Add(v.Name) 
            end
        end
    end)

Main:Toggle("Auto Farm Boss",_G.Auto_Farm_Boss,function(value)
 _G.Auto_Farm_Boss = value
 end)

Main:Toggle("Auto Quest Boss",true,function(value)
 _G.Auto_Quest_Boss = value
end)

spawn(function()
	while wait() do
		if _G.Auto_Farm_Boss then
			pcall(function()
				CheckBossQuest()
				if MsBoss == "Soul Reaper [Lv. 2100] [Raid Boss]" or MsBoss == "Longma [Lv. 2000] [Boss]" or MsBoss == "Don Swan [Lv. 1000] [Boss]" or MsBoss == "Cursed Captain [Lv. 1325] [Raid Boss]" or MsBoss == "Order [Lv. 1250] [Raid Boss]" or MsBoss == "rip_indra True Form [Lv. 5000] [Raid Boss]" then
					if game:GetService("Workspace").Enemies:FindFirstChild(MsBoss) then
						for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
							if v.Name == MsBoss then
								repeat wait()
									Equipgui(_G.Select_gui)
									AutoHaki()
									topos(v.HumanoidRootPart.CFrame * MethodFarm)
									v.HumanoidRootPart.CanCollide = false
									v.HumanoidRootPart.Size = Vector3.new(60, 60, 60)
									game:GetService'VirtualUser':CaptureController()
									game:GetService'VirtualUser':Button1Down(Vector2.new(1280, 672))
								until _G.Auto_Farm_Boss == false or not v.Parent or v.Humanoid.Health <= 0
							end
						end
					else
						topos(CFrameBoss)
					end
				else
					if _G.Auto_Quest_Boss then
						CheckBossQuest()
						if not string.find(game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Container.QuestTitle.Title.Text, NameBoss) then
                            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("AbandonQuest")
                        end
						if game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == false then
							repeat wait() topos(CFrameQuestBoss) until (CFrameQuestBoss.Position - game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 3 or not _G.Auto_Farm_Boss
							if (CFrameQuestBoss.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 4 then
								wait(1.1)
								game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("StartQuest", NameQuestBoss, LevelQuestBoss)
							end
						elseif game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == true then
							if game:GetService("Workspace").Enemies:FindFirstChild(MsBoss) then
								for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
									if v.Name == MsBoss then
										repeat wait()
											if string.find(game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Container.QuestTitle.Title.Text, NameBoss) then
												Equipgui(_G.Select_gui)
												AutoHaki()
												topos(v.HumanoidRootPart.CFrame * MethodFarm)
												v.HumanoidRootPart.CanCollide = false
												v.HumanoidRootPart.Size = Vector3.new(60, 60, 60)
												game:GetService'VirtualUser':CaptureController()
												game:GetService'VirtualUser':Button1Down(Vector2.new(1280, 672))									
											else
												game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("AbandonQuest")
											end
										until _G.Auto_Farm_Boss == false or not v.Parent or v.Humanoid.Health <= 0
									end
								end
							else
								topos(CFrameBoss)
							end
						end
					else
						if game:GetService("Workspace").Enemies:FindFirstChild(MsBoss) then
							for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
								if v.Name == MsBoss then
									repeat wait()
										Equipgui(_G.Select_gui)
										AutoHaki()
										topos(v.HumanoidRootPart.CFrame * MethodFarm)
										v.HumanoidRootPart.CanCollide = false
										v.HumanoidRootPart.Size = Vector3.new(60, 60, 60)
										game:GetService'VirtualUser':CaptureController()
                                        game:GetService'VirtualUser':Button1Down(Vector2.new(1280, 672))										
									until _G.Auto_Farm_Boss == false or not v.Parent or v.Humanoid.Health <= 0
								end
							end
						else
							topos(CFrameBoss)
						end
					end
				end
			end)
		end
	end
end)

Main:Toggle("Auto Farm All Boss",_G.Auto_Farm_All_Boss,function(value)
 _G.Auto_Farm_All_Boss = value
StopTween(_G.Auto_Farm_All_Boss)
end)

spawn(function()
	while wait() do
		if _G.Auto_Farm_All_Boss then
			pcall(function()
				for i,v in pairs(game.ReplicatedStorage:GetChildren()) do
					if string.find(v.Name,"Boss") then
						repeat task.wait()
							if v:FindFirstChild("HumanoidRootPart") and v:FindFirstChild("Humanoid") and (v.HumanoidRootPart.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).magnitude > 350 then
								topos(v.HumanoidRootPart.CFrame)
							elseif v:FindFirstChild("HumanoidRootPart") and v:FindFirstChild("Humanoid") and (v.HumanoidRootPart.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).magnitude <= 350 then
								AutoHaki()
								Equipgui(_G.Select_gui)
								v.Humanoid.WalkSpeed = 0
								v.HumanoidRootPart.CanCollide = false
								v.Head.CanCollide = false
								v.HumanoidRootPart.Size = Vector3.new(80,80,80)
								topos(v.HumanoidRootPart.CFrame * MethodFarm)
								game:GetService'VirtualUser':CaptureController()
								game:GetService'VirtualUser':Button1Down(Vector2.new(1280, 672))
								sethiddenproperty(game.Players.LocalPlayer,"SimulationRadius",math.huge)
							end
						until v.Humanoid.Health <= 0 or _G.Auto_Farm_All_Boss == false or not v.Parent
					end
				end
			end)
		end
	end
end)

function MaterialMon()
			if _G.SelectMaterial == "Radioactive Material" then
				MMon = "Factory Staff [Lv. 800]"
				MPos = CFrame.new(-507.7895202636719, 72.99479675292969, -126.45632934570312)
				SP = "Bar"
			elseif _G.SelectMaterial == "Mystic Droplet" then
				MMon = "Water Fighter [Lv. 1450]"
				MPos = CFrame.new(-3214.218017578125, 298.69952392578125, -10543.685546875)
				SP = "ForgottenIsland"
			elseif _G.SelectMaterial == "Magma Ore" then
				if game.PlaceId == 2753915549 then
					MMon = "Military Spy [Lv. 325]"
					MPos = CFrame.new(-5850.2802734375, 77.28675079345703, 8848.6748046875)
					SP = "Magma"
				elseif game.PlaceId == 4442272183 then
					MMon = "Lava Pirate [Lv. 1200]"
					MPos = CFrame.new(-5234.60595703125, 51.953372955322266, -4732.27880859375)
					SP = "CircleIslandFire"
				end
			elseif _G.SelectMaterial == "Angel Wings" then
				MMon = "Royal Soldier [Lv. 550]"
				MPos = CFrame.new(-7827.15625, 5606.912109375, -1705.5833740234375)
				SP = "Sky2"
			elseif _G.SelectMaterial == "Leather" then
				if game.PlaceId == 2753915549 then
					MMon = "Pirate [Lv. 36]"
					MPos = CFrame.new(-1211.8792724609375, 4.787090301513672, 3916.83056640625)
					SP = "Pirate"
				elseif game.PlaceId == 4442272183 then
					MMon = "Marine Captain [Lv. 900]"
					MPos = CFrame.new(-2010.5059814453125, 73.00115966796875, -3326.620849609375)
					SP = "Greenb"
				elseif game.PlaceId == 7449423635 then
					MMon = "Jungle Pirate [Lv. 1900]"
					MPos = CFrame.new(-11975.78515625, 331.7734069824219, -10620.0302734375)
					SP = "PineappleTown"
				end
			elseif _G.SelectMaterial == "Scrap Metal" then
				if game.PlaceId == 2753915549 then
					MMon = "Brute [Lv. 45]"
					MPos = CFrame.new(-1132.4202880859375, 14.844913482666016, 4293.30517578125)
					SP = "Pirate"
				elseif game.PlaceId == 4442272183 then
					MMon = "Mercenary [Lv. 725]"
					MPos = CFrame.new(-972.307373046875, 73.04473876953125, 1419.2901611328125)
					SP = "DressTown"
				elseif game.PlaceId == 7449423635 then
					MMon = "Pirate Millionaire [Lv. 1500]"
					MPos = CFrame.new(-289.6311950683594, 43.8282470703125, 5583.66357421875)
					SP = "Default"
				end
			elseif _G.SelectMaterial == "Demonic Wisp" then
				MMon = "Demonic Soul [Lv. 2025]"
				MPos = CFrame.new(-9503.388671875, 172.139892578125, 6143.0634765625)
				SP = "HauntedCastle"
			elseif _G.SelectMaterial == "Vampire Fang" then
				MMon = "Vampire [Lv. 975]"
				MPos = CFrame.new(-5999.20458984375, 6.437741279602051, -1290.059326171875)
				SP = "Graveyard"
			elseif _G.SelectMaterial == "Conjured Cocoa" then
				MMon = "Chocolate Bar Battler [Lv. 2325]"
				MPos = CFrame.new(744.7930908203125, 24.76934242248535, -12637.7255859375)
				SP = "Chocolate"
			elseif _G.SelectMaterial == "Dragon Scale" then
				MMon = "Dragon Crew Warrior [Lv. 1575]"
				MPos = CFrame.new(5824.06982421875, 51.38640213012695, -1106.694580078125)
				SP = "Hydra1"
			elseif _G.SelectMaterial == "Gunpowder" then
				MMon = "Pistol Billionaire [Lv. 1525]"
				MPos = CFrame.new(-379.6134338378906, 73.84449768066406, 5928.5263671875)
				SP = "Default"
			elseif _G.SelectMaterial == "Fish Tail" then
				MMon = "Fishman Captain [Lv. 1800]"
				MPos = CFrame.new(-10961.0126953125, 331.7977600097656, -8914.29296875)
				SP = "PineappleTown"
			elseif _G.SelectMaterial == "Mini Tusk" then
				MMon = "Mythological Pirate [Lv. 1850]"
				MPos = CFrame.new(-13516.0458984375, 469.8182373046875, -6899.16064453125)
				SP = "BigMansion"
			end
		end

local MaterialMethod
if World1 then
	MaterialMethod = {
 "Magma Ore",
 "Angel Wings",
 "Leather",
 "Scrap Metal",
 "Radioactive Material",
 }
elseif World2 then
MaterialMethod = {
 "Mystic Droplet",
 "Magma Ore",
 "Leather",
 "Scrap Metal",
 "Demonic Wisp",
 "Vampire Fang",
 "Radioactive Material",
 }
 elseif World3 then
MaterialMethod = {
 "Leather",
 "Scrap Metal",
 "Vampire Fang",
 "Conjured Cocoa",
 "Dragon Scale",
 "Gunpowder",
 "Fish Tail",
 "Mini Tusk",
 "Radioactive Material",
 }
 end
 
Main:Seperator(" Materials ")
 
 local SelectMaterial = Main:Dropdown("Select Material",MaterialMethod,function(value)
 _G.SelectMaterial = value
end)

Main:Toggle("Farm Selected Material",_G.AutoFarmMaterial,function(t)
			_G.AutoFarmMaterial = t
			StopTween(_G.AutoFarmMaterial)
end)
		
spawn(function()
			while task.wait() do
				pcall(function()
					if _G.AutoFarmMaterial and _G.SelectMaterial then
						MaterialMon()
						if game.Workspace.Enemies:FindFirstChild(MMon) then
							for i,v in pairs(game.Workspace.Enemies:GetChildren()) do
								if v.Name == MMon then
									if v:FindFirstChild("HumanoidRootPart") then
										repeat task.wait()
											AutoHaki()
											Equipgui(_G.Select_gui)
												PosMon = v.HumanoidRootPart.CFrame
												v.HumanoidRootPart.CanCollide = false
												v.Humanoid.WalkSpeed = 0
												v.Head.CanCollide = false
												v.HumanoidRootPart.Size = Vector3.new(50,50,50)
												StartMagnet = true
												topos(v.HumanoidRootPart.CFrame * MethodFarm)
												game:GetService'VirtualUser':CaptureController()
												game:GetService'VirtualUser':Button1Down(Vector2.new(1280, 672))
											MatMon = v.Name
											MatPos = v.HumanoidRootPart.CFrame
										until not _G.AutoFarmMaterial or not v.Parent or v.Humanoid.Health <= 0
									end
								end
							end
						else
							topos(MPos)
						end
					end
				end)
			end
end)

spawn(function()
			while task.wait() do
				if _G.BringNormal and _G.AutoFarmMaterial then
					pcall(function()
						for i,v in pairs(game.Workspace.Enemies:GetChildren()) do
							if v.Name == MatMon and (v.HumanoidRootPart.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 400 then
								v.Humanoid.WalkSpeed = 0
								v.HumanoidRootPart.Size = Vector3.new(60,60,60)
								--v.Humanoid:ChangeState(14)
								v.HumanoidRootPart.CanCollide = false
								v.Head.CanCollide = false
								v.HumanoidRootPart.CFrame = MatPos
								if v.Humanoid:FindFirstChild("Animator") then
									v.Humanoid.Animator:Destroy()
								end
								v.Humanoid:ChangeState(11)
								v.Humanoid:ChangeState(14)
								sethiddenproperty(game.Players.LocalPlayer,"SimulationRadius",math.huge)
							end
						end
					end)
				end
			end
end)

spawn(function()
			while task.wait() do
				if _G.BringNormal and _G.Select_Mode_Farm == "Near Farm Mode" then
					pcall(function()
						for i,v in pairs(game.Workspace.Enemies:GetChildren()) do
							if v.Name == Mon and (v.HumanoidRootPart.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 400 then
								v.Humanoid.WalkSpeed = 0
								v.HumanoidRootPart.Size = Vector3.new(60,60,60)
								--v.Humanoid:ChangeState(14)
								v.HumanoidRootPart.CanCollide = false
								v.Head.CanCollide = false
								v.HumanoidRootPart.CFrame = PosMon
								if v.Humanoid:FindFirstChild("Animator") then
									v.Humanoid.Animator:Destroy()
								end
								v.Humanoid:ChangeState(11)
								v.Humanoid:ChangeState(14)
								sethiddenproperty(game.Players.LocalPlayer,"SimulationRadius",math.huge)
							end
						end
					end)
				end
			end
end)

spawn(function()
			while task.wait() do
				if _G.AutoFarmSelectMonster then
					pcall(function()
						for i,v in pairs(game.Workspace.Enemies:GetChildren()) do
							if v.Name == Mon and (v.HumanoidRootPart.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 400 then
								v.Humanoid.WalkSpeed = 0
								v.HumanoidRootPart.Size = Vector3.new(60,60,60)
								--v.Humanoid:ChangeState(14)
								v.HumanoidRootPart.CanCollide = false
								v.Head.CanCollide = false
								v.HumanoidRootPart.CFrame = PosMon
								if v.Humanoid:FindFirstChild("Animator") then
									v.Humanoid.Animator:Destroy()
								end
								v.Humanoid:ChangeState(11)
								v.Humanoid:ChangeState(14)
								sethiddenproperty(game.Players.LocalPlayer,"SimulationRadius",math.huge)
							end
						end
					end)
				end
			end
end)

spawn(function()
			while task.wait() do
				if _G.AutoFarmSelectMonster then
					pcall(function()
						for i,v in pairs(game.Workspace.Enemies:GetChildren()) do
							if v.Name == Ms and (v.HumanoidRootPart.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 400 then
								v.Humanoid.WalkSpeed = 0
								v.HumanoidRootPart.Size = Vector3.new(60,60,60)
								--v.Humanoid:ChangeState(14)
								v.HumanoidRootPart.CanCollide = false
								v.Head.CanCollide = false
								v.HumanoidRootPart.CFrame = PosMon
								if v.Humanoid:FindFirstChild("Animator") then
									v.Humanoid.Animator:Destroy()
								end
								v.Humanoid:ChangeState(11)
								v.Humanoid:ChangeState(14)
								sethiddenproperty(game.Players.LocalPlayer,"SimulationRadius",math.huge)
							end
						end
					end)
				end
			end
end)

Main:Seperator(" Mirage Island ")

Main:Toggle("Auto Mirage Island",false,function(value)
 if game:GetService("Workspace").Map:FindFirstChild("MysticIsland") then
                           topos(game:GetService("Workspace").Map:FindFirstChild("MysticIsland").HumanoidRootPart.CFrame * CFrame.new(0,500,-100))
                    else
if _G.Mystichop then
hop()
end
end
end)

Main:Toggle("Auto Mirage Island Hop",false,function(value)
 _G.Mystichop = value
end)

Main:Seperator(" Chest ")

Main:Toggle("Auto Chest Fast",false,function(vu)
	_G.ChestBypass = vu
end)

spawn(function()
while wait() do
if _G.ChestBypass then
pcall(function()
for i,v in pairs(game:GetService("Workspace"):GetChildren()) do
      if string.find(v.Name, "Chest") then
          print(v.Name)
          game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = v.CFrame
          wait(.15)
      end
  end
  game.Players.LocalPlayer.Character.Head:Destroy()
  for _,v in pairs(game:GetService("Workspace"):GetDescendants()) do
   if string.find(v.Name, "Chest") and v:IsA("TouchTransmitter") then
   firetouchinterest(game.Players.LocalPlayer.Character.HumanoidRootPart, v.Parent, 0) --0 is touch
   wait()
   firetouchinterest(game.Players.LocalPlayer.Character.HumanoidRootPart, v.Parent, 1) -- 1 is untouch
   end
   end
  end)
    end
  end
end)

spawn(function()
while task.wait() do
if _G.ChestBypass then
        local ohString1 = "SetTeam"
        local ohString2 = "Pirates"
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(ohString1, ohString2)
     end
end
end)

Main:Toggle("Auto Chest Tween",_G.Grab_Chest,function(vu)
	Grab_Chest = vu
    StopTween(Grab_Chest)
	_G.Grab_Chest = vu
end)

Main:Button("Instant Tp Chest (Risk)",function()
 loadstring(game:HttpGet("https://raw.githubusercontent.com/scriptpastebin/raw/main/Chest_onoff"))()
 end)

if World3 then
Main:Seperator(" Bones ")

Main:Toggle("Auto Farm Bone",_G.Auto_Farm_Bone,function(value)
 _G.Auto_Farm_Bone = value
 StopTween(_G.Auto_Farm_Bone)
 end)

Main:Toggle("Auto Trade Bone",_G.Auto_Trade_Bone,function(value)
 _G.Auto_Trade_Bone = value
 end)

spawn(function()
 while wait(.1) do
 if _G.Auto_Trade_Bone then
 local args = {
  [1] = "Bones",
  [2] = "Buy",
  [3] = 1,
  [4] = 1
 }

 game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
 end
 end
 end)

Main:Button("Check Bone", function()
 game.StarterGui:SetCore("SendNotification", {
  Title = "Checking Bone",
  Text = ("Your Bone : "..(game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("Bones","Check")))
 })
 wait(1)
end)
end

Main:Seperator(" Observation ")
	
local ObservationLevel = Main:Label("")

spawn(function()
	while game:GetService("RunService").Heartbeat:wait() do
		if game.Players.LocalPlayer.VisionRadius.Value == 3000 then
			value = "Max"
		else
			value = math.round(game.Players.LocalPlayer.VisionRadius.value)
		end
		ObservationLevel:Set("Observation Haki Level : "..tostring(value))
	end
end)
    
       Main:Toggle("Auto Farm Observation",_G.AutoObservation,function(value)
        _G.AutoObservation = value
        StopTween(_G.AutoObservation)
    end)
    
    spawn(function()
        while wait() do
            pcall(function()
                if _G.AutoObservation then
                    repeat task.wait()
                        if not game:GetService("Players").LocalPlayer.PlayerGui.ScreenGui:FindFirstChild("ImageLabel") then
                            game:GetService('VirtualUser'):CaptureController()
                            game:GetService('VirtualUser'):SetKeyDown('0x65')
                            wait(2)
                            game:GetService('VirtualUser'):SetKeyUp('0x65')
                        end
                    until game:GetService("Players").LocalPlayer.PlayerGui.ScreenGui:FindFirstChild("ImageLabel") or not _G.AutoObservation
                end
            end)
        end
    end)
    
    Main:Toggle("Auto Farm Observation Hop",_G.AutoObservation_Hop,function(value)
        _G.AutoObservation_Hop = value
    end)
    
    spawn(function()
        pcall(function()
            while wait() do
                if _G.AutoObservation then
                    if game:GetService("Players").LocalPlayer.VisionRadius.Value >= 3000 then
local NotificationHolder = loadstring(game:HttpGet("https://raw.githubusercontent.com/BocusLuke/UI/main/STX/Module.Lua"))()
local Notification = loadstring(game:HttpGet("https://raw.githubusercontent.com/BocusLuke/UI/main/STX/Client.Lua"))()
wait(1)
Notification:Notify(
   {Title = "t7gfy hub ", Description = "You Have Max Observation"},
   {OutlineColor = Color3.fromRGB(80, 80, 80),Time = 5, Type = "option"},
   {Image = "http://www.roblox.com/asset/?id=6023426923", ImageColor = Color3.fromRGB(255, 84, 84), Callback = function(State) print(tostring(State)) end}
)
                    else
                        if World2 then
                            if game:GetService("Workspace").Enemies:FindFirstChild("Water Fighter [Lv. 1450]") then
                                if game:GetService("Players").LocalPlayer.PlayerGui.ScreenGui:FindFirstChild("ImageLabel") then
                                    repeat task.wait()
                                        game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame = game:GetService("Workspace").Enemies:FindFirstChild("Water Fighter [Lv. 1450]").HumanoidRootPart.CFrame * CFrame.new(3,0,0)
                                    until _G.AutoObservation == false or not game:GetService("Players").LocalPlayer.PlayerGui.ScreenGui:FindFirstChild("ImageLabel")
                                else
                                    repeat task.wait()
                                        game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame = game:GetService("Workspace").Enemies:FindFirstChild("Water Fighter [Lv. 1450]").HumanoidRootPart.CFrame * CFrame.new(0,50,0)+
                                            wait(1)
                                        if not game:GetService("Players").LocalPlayer.PlayerGui.ScreenGui:FindFirstChild("ImageLabel") and _G.AutoObservation_Hop == true then
                                           game:GetService("TeleportService"):Teleport(game.PlaceId, game:GetService("Players").LocalPlayer)
                                        end
                                    until _G.AutoObservation == false or game:GetService("Players").LocalPlayer.PlayerGui.ScreenGui:FindFirstChild("ImageLabel")
                                end
                            else
                                topos(CFrame.new(-3184.662353515625, 58.35300064086914, -9662.85546875))
                            end
                        elseif World1 then
                            if game:GetService("Workspace").Enemies:FindFirstChild("Galley Captain [Lv. 650]") then
                                if game:GetService("Players").LocalPlayer.PlayerGui.ScreenGui:FindFirstChild("ImageLabel") then
                                    repeat task.wait()
                                        game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame = game:GetService("Workspace").Enemies:FindFirstChild("Galley Captain [Lv. 650]").HumanoidRootPart.CFrame * CFrame.new(3,0,0)
                                    until _G.AutoObservation == false or not game:GetService("Players").LocalPlayer.PlayerGui.ScreenGui:FindFirstChild("ImageLabel")
                                else
                                    repeat task.wait()
                                        game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame = game:GetService("Workspace").Enemies:FindFirstChild("Galley Captain [Lv. 650]").HumanoidRootPart.CFrame * CFrame.new(0,50,0)
                                        wait(1)
                                        if not game:GetService("Players").LocalPlayer.PlayerGui.ScreenGui:FindFirstChild("ImageLabel") and _G.AutoObservation_Hop == true then
                                            game:GetService("TeleportService"):Teleport(game.PlaceId,game:GetService("Players").LocalPlayer)
                                        end
                                    until _G.AutoObservation == false or game:GetService("Players").LocalPlayer.PlayerGui.ScreenGui:FindFirstChild("ImageLabel")
                                end
                            else
                                topos(CFrame.new(5533.29785, 88.1079102, 4852.3916))
                            end
                        elseif World3 then
                            if game:GetService("Workspace").Enemies:FindFirstChild("Giant Islander [Lv. 1650]") then
                                if game:GetService("Players").LocalPlayer.PlayerGui.ScreenGui:FindFirstChild("ImageLabel") then
                                    repeat task.wait()
                                        game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame = game:GetService("Workspace").Enemies:FindFirstChild("Giant Islander [Lv. 1650]").HumanoidRootPart.CFrame * CFrame.new(3,0,0)
                                    until _G.AutoObservation == false or not game:GetService("Players").LocalPlayer.PlayerGui.ScreenGui:FindFirstChild("ImageLabel")
                                else
                                    repeat task.wait()
                                        game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame = game:GetService("Workspace").Enemies:FindFirstChild("Giant Islander [Lv. 1650]").HumanoidRootPart.CFrame * CFrame.new(0,50,0)
                                        wait(1)
                                        if not game:GetService("Players").LocalPlayer.PlayerGui.ScreenGui:FindFirstChild("ImageLabel") and _G.AutoObservation_Hop == true then
                                            game:GetService("TeleportService"):Teleport(game.PlaceId,game:GetService("Players").LocalPlayer)
                                        end
                                    until _G.AutoObservation == false or game:GetService("Players").LocalPlayer.PlayerGui.ScreenGui:FindFirstChild("ImageLabel")
                                end
                            else
                                topos(CFrame.new(4530.3540039063, 656.75695800781, -131.60952758789))
                            end
                        end
                    end
                end
            end
        end)
    end)

Main:Seperator(" Fake Race V4 ")


Main:Button("Mink Fake Transform",function()
 require(game:GetService("ReplicatedStorage").Notification).new("Mink V4!"):Display();
 wait()
 setthreadcontext(5)

 local ReplicatedStorage = game:GetService("ReplicatedStorage")

 local Player = game:GetService("Players").LocalPlayer

 local ArgsTransform = {
  Character = game.Players.LocalPlayer.Character,
  CFrame = game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame,
  Color1 = Color3.fromRGB(102, 255, 153),
  Color2 = Color3.fromRGB(102, 255, 153),
  Color3 = Color3.fromRGB(102, 255, 153),
 }

 Player.Character.Humanoid:LoadAnimation(ReplicatedStorage.Util.Anims.Storage["2"].RaceTransform):Play()

 delay(1, function()
  pcall(function() require(ReplicatedStorage.Effect.Container.RaceTransformation.Main)(ArgsTransform) end)
  end)

 end)
Main:Button("Fishman Fake Transform",function()
 require(game:GetService("ReplicatedStorage").Notification).new("Fishman V4!"):Display();
 wait()
 setthreadcontext(5)

 local ReplicatedStorage = game:GetService("ReplicatedStorage")

 local Player = game:GetService("Players").LocalPlayer

 local ArgsTransform = {
  Character = game.Players.LocalPlayer.Character,
  CFrame = game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame,
  Color1 = Color3.fromRGB(5, 115, 166),
  Color2 = Color3.fromRGB(5, 115, 166),
  Color3 = Color3.fromRGB(5, 115, 166),
 }

 Player.Character.Humanoid:LoadAnimation(ReplicatedStorage.Util.Anims.Storage["2"].RaceTransform):Play()

 delay(1, function()
  pcall(function() require(ReplicatedStorage.Effect.Container.RaceTransformation.Main)(ArgsTransform) end)
  end)

 end)
Main:Button("Skypeian Fake Transform",function()
 require(game:GetService("ReplicatedStorage").Notification).new("Skypeian V4!"):Display();
 wait()
 setthreadcontext(5)

 local ReplicatedStorage = game:GetService("ReplicatedStorage")

 local Player = game:GetService("Players").LocalPlayer

 local ArgsTransform = {
  Character = game.Players.LocalPlayer.Character,
  CFrame = game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame,
  Color1 = Color3.fromRGB(222, 222, 0),
  Color2 = Color3.fromRGB(222, 222, 0),
  Color3 = Color3.fromRGB(222, 222, 0),
 }

 Player.Character.Humanoid:LoadAnimation(ReplicatedStorage.Util.Anims.Storage["2"].RaceTransform):Play()

 delay(1, function()
  pcall(function() require(ReplicatedStorage.Effect.Container.RaceTransformation.Main)(ArgsTransform) end)
  end)

 end)
Main:Button("Ghoul Fake Transform",function()
 require(game:GetService("ReplicatedStorage").Notification).new("Ghoul V4!"):Display();
 wait()
 setthreadcontext(5)

 local ReplicatedStorage = game:GetService("ReplicatedStorage")

 local Player = game:GetService("Players").LocalPlayer

 local ArgsTransform = {
  Character = game.Players.LocalPlayer.Character,
  CFrame = game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame,
  Color1 = Color3.fromRGB(155, 155, 155),
  Color2 = Color3.fromRGB(0, 0, 0),
  Color3 = Color3.fromRGB(155, 155, 155),
 }

 Player.Character.Humanoid:LoadAnimation(ReplicatedStorage.Util.Anims.Storage["2"].RaceTransform):Play()

 delay(1, function()
  pcall(function() require(ReplicatedStorage.Effect.Container.RaceTransformation.Main)(ArgsTransform) end)
  end)


 end)
Main:Button("Cyborg Fake Transform",function()
 require(game:GetService("ReplicatedStorage").Notification).new("Cyborg V4!"):Display();
 wait()
 setthreadcontext(5)

 local ReplicatedStorage = game:GetService("ReplicatedStorage")

 local Player = game:GetService("Players").LocalPlayer

 local ArgsTransform = {
  Character = game.Players.LocalPlayer.Character,
  CFrame = game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame,
  Color1 = Color3.fromRGB(166, 0, 111),
  Color2 = Color3.fromRGB(166, 0, 111),
  Color3 = Color3.fromRGB(166, 0, 111),
 }

 Player.Character.Humanoid:LoadAnimation(ReplicatedStorage.Util.Anims.Storage["2"].RaceTransform):Play()

 delay(1, function()
  pcall(function() require(ReplicatedStorage.Effect.Container.RaceTransformation.Main)(ArgsTransform) end)
  end)

 end)
Main:Button("Human Fake Transform",function()
 require(game:GetService("ReplicatedStorage").Notification).new("Human V4!"):Display();
 wait()
 setthreadcontext(5)

 local ReplicatedStorage = game:GetService("ReplicatedStorage")

 local Player = game:GetService("Players").LocalPlayer

 local ArgsTransform = {
  Character = game.Players.LocalPlayer.Character,
  CFrame = game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame,
  Color1 = Color3.fromRGB(166, 0, 0),
  Color2 = Color3.fromRGB(166, 0, 0),
  Color3 = Color3.fromRGB(166, 0, 0),
 }

 Player.Character.Humanoid:LoadAnimation(ReplicatedStorage.Util.Anims.Storage["2"].RaceTransform):Play()

 delay(1, function()
  pcall(function() require(ReplicatedStorage.Effect.Container.RaceTransformation.Main)(ArgsTransform) end)
  end)

 end)

Main:Button("Fake Mink Dash Animation",function()
 local ReplicatedStorage = game:GetService("ReplicatedStorage")

 local Player = game:GetService("Players").LocalPlayer

 local ArgsDash = {
  Character = Player.Character,
  Duration = .25,
  CFrame = Player.Character.HumanoidRootPart.CFrame,
 }

 local old; old = hookmetamethod(game, "__namecall", newcclosure(function(self, ...)
  if self.Name == "CommE" then
  local args = {
   ...
  }

  if args[1] == "Dodge" then
  coroutine.wrap(function() require(ReplicatedStorage.Effect.Container.Shared.Lightningtopos)(ArgsDash) end)()
  end
  end

  return old(self, ...)
  end))
end)
 
 if World3 then

gui:Seperator(" Item & Quest ")

local Total_Elite_Hunter = gui:Label("Elite Hunter")

local Elite_Hunter_Status = gui:Label("Status")


	spawn(function()
		while wait() do
			pcall(function()
				if game:GetService("ReplicatedStorage"):FindFirstChild("Diablo [Lv. 1750]") or game:GetService("ReplicatedStorage"):FindFirstChild("Deandre [Lv. 1750]") or game:GetService("ReplicatedStorage"):FindFirstChild("Urban [Lv. 1750]") or game:GetService("Workspace").Enemies:FindFirstChild("Diablo [Lv. 1750]") or game:GetService("Workspace").Enemies:FindFirstChild("Deandre [Lv. 1750]") or game:GetService("Workspace").Enemies:FindFirstChild("Urban [Lv. 1750]") then
					Elite_Hunter_Status:Set("Status : Elite Spawn!")	
				else
					Elite_Hunter_Status:Set("Status : Elite Not Spawn")	
				end
			end)
		end
	end)

	spawn(function()
		while wait() do
			Total_Elite_Hunter:Set("Total Elite Hunter : "..game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("EliteHunter","Progress"))
		end
	end)
	
	gui:Toggle("Auto Elite Hunter",_G.Auto_Elite_Hunter,function(value)
 _G.Auto_Elite_Hunter = value
StopTween(_G.Auto_Elite_Hunter)
end)

	
	gui:Toggle("Auto Elite Hunter Hop",_G.Auto_Elite_Hunter_Hop,function(value)
 _G.Auto_Elite_Hunter_Hop = value
end)

	spawn(function()
		while wait() do
			if _G.Auto_Elite_Hunter and World3 then
				pcall(function()
					if game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == true then
						if string.find(game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Container.QuestTitle.Title.Text,"Diablo") or string.find(game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Container.QuestTitle.Title.Text,"Deandre") or string.find(game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Container.QuestTitle.Title.Text,"Urban") then
							if game:GetService("Workspace").Enemies:FindFirstChild("Diablo [Lv. 1750]") or game:GetService("Workspace").Enemies:FindFirstChild("Deandre [Lv. 1750]") or game:GetService("Workspace").Enemies:FindFirstChild("Urban [Lv. 1750]") then
								for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
									if v.Name == "Diablo [Lv. 1750]" or v.Name == "Deandre [Lv. 1750]" or v.Name == "Urban [Lv. 1750]" then
										if v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
											repeat wait()
												AutoHaki()
												Equipgui(_G.Select_gui)
												v.HumanoidRootPart.CanCollide = false
												v.Humanoid.WalkSpeed = 0
												v.HumanoidRootPart.Size = Vector3.new(50,50,50)
												topos(v.HumanoidRootPart.CFrame * MethodFarm)
												game:GetService("VirtualUser"):CaptureController()
												game:GetService("VirtualUser"):Button1Down(Vector2.new(1280,672))
												sethiddenproperty(game:GetService("Players").LocalPlayer,"SimulationRadius",math.huge)
											until _G.Auto_Elite_Hunter == false or v.Humanoid.Health <= 0 or not v.Parent
										end
									end
								end
							else
								if game:GetService("ReplicatedStorage"):FindFirstChild("Diablo [Lv. 1750]") then
									topos(game:GetService("ReplicatedStorage"):FindFirstChild("Diablo [Lv. 1750]").HumanoidRootPart.CFrame * MethodFarm)
								elseif game:GetService("ReplicatedStorage"):FindFirstChild("Deandre [Lv. 1750]") then
									topos(game:GetService("ReplicatedStorage"):FindFirstChild("Deandre [Lv. 1750]").HumanoidRootPart.CFrame * MethodFarm)
								elseif game:GetService("ReplicatedStorage"):FindFirstChild("Urban [Lv. 1750]") then
									topos(game:GetService("ReplicatedStorage"):FindFirstChild("Urban [Lv. 1750]").HumanoidRootPart.CFrame * MethodFarm)
								end
							end                    
						end
					else
						if _G.Auto_Elite_Hunter_Hop and game:GetService("ReplicatedStorage").Remotes["CommF_"]:InvokeServer("EliteHunter") == "I don't have anything for you right now. Come back later." then
							hop()
						else
							game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("EliteHunter")
						end
					end
				end)
			end
		end
	end)
	
	gui:Seperator(" Dough Boss ")

local Mob_Kill_Cake_Prince = gui:Label("Total")

	spawn(function()
		while wait() do
			pcall(function()
				if string.len(game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("CakePrinceSpawner")) == 88 then
					Mob_Kill_Cake_Prince:Set("Killed : "..string.sub(game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("CakePrinceSpawner"),39,41).." : Kill More")
				elseif string.len(game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("CakePrinceSpawner")) == 87 then
					Mob_Kill_Cake_Prince:Set("Kill : "..string.sub(game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("CakePrinceSpawner"),39,40).." : Kill More")
				elseif string.len(game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("CakePrinceSpawner")) == 86 then
					Mob_Kill_Cake_Prince:Set("Kill : "..string.sub(game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("CakePrinceSpawner"),39,39).." : More")
				else
					Mob_Kill_Cake_Prince:Set("Boss Is Spawned")
				end
			end)
		end
	end)

gui:Toggle("Auto Cake Prince",_G.Auto_Cake_Prince,function(value)
 _G.Auto_Cake_Prince = value
StopTween(_G.Auto_Cake_Prince)
end)
	
	
	
	gui:Toggle("Auto Open Dough Dungeon",_G.Auto_Open_Dough_Dungeon,function(value)
 _G.Auto_Open_Dough_Dungeon = value
StopTween(_G.Auto_Open_Dough_Dungeon)
end)
	
	spawn(function()
		game:GetService("RunService").Heartbeat:Connect(function()
			pcall(function()
				for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
					if _G.Auto_Open_Dough_Dungeon and StartCakeStartMagnet and (v.Name == "Cookie Crafter [Lv. 2200]" or v.Name == "Cake Guard [Lv. 2225]" or v.Name == "Baking Staff [Lv. 2250]" or v.Name == "Head Baker [Lv. 2275]") and (v.HumanoidRootPart.Position - POSCAKE.Position).magnitude <= 350 then
						v.HumanoidRootPart.CFrame = POSCAKE
						v.HumanoidRootPart.CanCollide = false
						v.HumanoidRootPart.Size = Vector3.new(50,50,50)
						if v.Humanoid:FindFirstChild("Animator") then
							v.Humanoid.Animator:Destroy()
						end
						sethiddenproperty(game.Players.LocalPlayer, "SimulationRadius",  math.huge)
					end
				end
			end)
		end)
	end) 

	spawn(function()
		game:GetService("RunService").Heartbeat:Connect(function()
			pcall(function()
				for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
					if _G.Auto_Cake_Prince and StartCakeStartMagnet and (v.Name == "Cookie Crafter [Lv. 2200]" or v.Name == "Cake Guard [Lv. 2225]" or v.Name == "Baking Staff [Lv. 2250]" or v.Name == "Head Baker [Lv. 2275]") and (v.HumanoidRootPart.Position - POSCAKE.Position).magnitude <= 350 then
						v.HumanoidRootPart.CFrame = POSCAKE
						v.HumanoidRootPart.CanCollide = false
						v.HumanoidRootPart.Size = Vector3.new(50,50,50)
						if v.Humanoid:FindFirstChild("Animator") then
							v.Humanoid.Animator:Destroy()
						end
						sethiddenproperty(game.Players.LocalPlayer, "SimulationRadius",  math.huge)
					end
				end
			end)
		end)
	end)

	spawn(function()
		while wait() do
			if _G.Auto_Cake_Prince then
				pcall(function()
					if game.ReplicatedStorage:FindFirstChild("Cake Prince [Lv. 2300] [Raid Boss]") or game:GetService("Workspace").Enemies:FindFirstChild("Cake Prince [Lv. 2300] [Raid Boss]") then   
						if game:GetService("Workspace").Enemies:FindFirstChild("Cake Prince [Lv. 2300] [Raid Boss]") then
							for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do 
								if v.Name == "Cake Prince [Lv. 2300] [Raid Boss]" then
									repeat wait()
										AutoHaki()
										Equipgui(_G.Select_gui)
										v.HumanoidRootPart.Size = Vector3.new(60, 60, 60)
										v.HumanoidRootPart.CanCollide = false
										topos(v.HumanoidRootPart.CFrame * MethodFarm)
										game:GetService'VirtualUser':CaptureController()
										game:GetService'VirtualUser':Button1Down(Vector2.new(1280, 672))
									until _G.Auto_Cake_Prince == false or not v.Parent or v.Humanoid.Health <= 0
								end    
							end    
						else
							topos(CFrame.new(-2009.2802734375, 4532.97216796875, -14937.3076171875)) 
						end
					else
						if game.Workspace.Enemies:FindFirstChild("Baking Staff [Lv. 2250]") or game.Workspace.Enemies:FindFirstChild("Head Baker [Lv. 2275]") or game.Workspace.Enemies:FindFirstChild("Cake Guard [Lv. 2225]") or game.Workspace.Enemies:FindFirstChild("Cookie Crafter [Lv. 2200]")  then
							for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do  
								if (v.Name == "Baking Staff [Lv. 2250]" or v.Name == "Head Baker [Lv. 2275]" or v.Name == "Cake Guard [Lv. 2225]" or v.Name == "Cookie Crafter [Lv. 2200]") and v.Humanoid.Health > 0 then
									repeat wait()
										AutoHaki()
										Equipgui(_G.Select_gui)
										StartCakeStartMagnet = true
										v.HumanoidRootPart.Size = Vector3.new(60, 60, 60)  
										POSCAKE = v.HumanoidRootPart.CFrame
										topos(v.HumanoidRootPart.CFrame * MethodFarm)
										game:GetService'VirtualUser':CaptureController()
										game:GetService'VirtualUser':Button1Down(Vector2.new(1280, 672))
									until _G.Auto_Cake_Prince == false or game:GetService("ReplicatedStorage"):FindFirstChild("Cake Prince [Lv. 2300] [Raid Boss]") or not v.Parent or v.Humanoid.Health <= 0
								end
							end
						else
							StartCakeStartMagnet = false
							topos(CFrame.new(-1820.0634765625, 210.74781799316406, -12297.49609375))
						end
					end
				end)
			end
		end
	end)

gui:Seperator(" Soul Guitar ")

gui:Toggle("Auto Soul Guitar",_G.AutoNevaSoulGuitar,function(value)
  _G.AutoNevaSoulGuitar = value    
 			StopTween(_G.AutoNevaSoulGuitar)
 end)

spawn(function()
		while wait() do
			pcall(function()
				if _G.AutoNevaSoulGuitar then
					if GetguiInventory("Soul Guitar") == false then
						if (CFrame.new(-9681.458984375, 6.139880657196045, 6341.3720703125).Position - game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 5000 then
							if game:GetService("Workspace").NPCs:FindFirstChild("Skeleton Machine") then
								game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("soulGuitarBuy",true)
							else
								if game:GetService("Workspace").Map["Haunted Castle"].Candle1.Transparency == 0 then
									if game:GetService("Workspace").Map["Haunted Castle"].Placard1.Left.Part.Transparency == 0 then
										Quest2 = true
										repeat wait() topos(CFrame.new(-8762.69140625, 176.84783935546875, 6171.3076171875)) until (CFrame.new(-8762.69140625, 176.84783935546875, 6171.3076171875).Position - game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 3 or not _G.AutoNevaSoulGuitar
										wait(1)
										fireclickdetector(game:GetService("Workspace").Map["Haunted Castle"].Placard7.Left.ClickDetector)
										wait(1)
										fireclickdetector(game:GetService("Workspace").Map["Haunted Castle"].Placard6.Left.ClickDetector)
										wait(1)
										fireclickdetector(game:GetService("Workspace").Map["Haunted Castle"].Placard5.Left.ClickDetector)
										wait(1)
										fireclickdetector(game:GetService("Workspace").Map["Haunted Castle"].Placard4.Right.ClickDetector)
										wait(1)
										fireclickdetector(game:GetService("Workspace").Map["Haunted Castle"].Placard3.Left.ClickDetector)
										wait(1)
										fireclickdetector(game:GetService("Workspace").Map["Haunted Castle"].Placard2.Right.ClickDetector)
										wait(1)
										fireclickdetector(game:GetService("Workspace").Map["Haunted Castle"].Placard1.Right.ClickDetector)
										wait(1)
									elseif game:GetService("Workspace").Map["Haunted Castle"].Tablet.Segment1:FindFirstChild("ClickDetector") then
										if game:GetService("Workspace").Map["Haunted Castle"]["Lab Puzzle"].ColorFloor.Model.Part1:FindFirstChild("ClickDetector") then
											Quest4 = true
											repeat wait() topos(CFrame.new(-9553.5986328125, 65.62338256835938, 6041.58837890625)) until (CFrame.new(-9553.5986328125, 65.62338256835938, 6041.58837890625).Position - game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 3 or not _G.AutoNevaSoulGuitar
											wait(1)
											topos(game:GetService("Workspace").Map["Haunted Castle"]["Lab Puzzle"].ColorFloor.Model.Part3.CFrame)
											wait(1)
											fireclickdetector(game:GetService("Workspace").Map["Haunted Castle"]["Lab Puzzle"].ColorFloor.Model.Part3.ClickDetector)
											wait(1)
											topos(game:GetService("Workspace").Map["Haunted Castle"]["Lab Puzzle"].ColorFloor.Model.Part4.CFrame)
											wait(1)
											fireclickdetector(game:GetService("Workspace").Map["Haunted Castle"]["Lab Puzzle"].ColorFloor.Model.Part4.ClickDetector)
											wait(1)
											fireclickdetector(game:GetService("Workspace").Map["Haunted Castle"]["Lab Puzzle"].ColorFloor.Model.Part4.ClickDetector)
											wait(1)
											fireclickdetector(game:GetService("Workspace").Map["Haunted Castle"]["Lab Puzzle"].ColorFloor.Model.Part4.ClickDetector)
											wait(1)
											topos(game:GetService("Workspace").Map["Haunted Castle"]["Lab Puzzle"].ColorFloor.Model.Part6.CFrame)
											wait(1)
											fireclickdetector(game:GetService("Workspace").Map["Haunted Castle"]["Lab Puzzle"].ColorFloor.Model.Part6.ClickDetector)
											wait(1)
											fireclickdetector(game:GetService("Workspace").Map["Haunted Castle"]["Lab Puzzle"].ColorFloor.Model.Part6.ClickDetector)
											wait(1)
											topos(game:GetService("Workspace").Map["Haunted Castle"]["Lab Puzzle"].ColorFloor.Model.Part8.CFrame)
											wait(1)
											fireclickdetector(game:GetService("Workspace").Map["Haunted Castle"]["Lab Puzzle"].ColorFloor.Model.Part8.ClickDetector)
											wait(1)
											topos(game:GetService("Workspace").Map["Haunted Castle"]["Lab Puzzle"].ColorFloor.Model.Part10.CFrame)
											wait(1)
											fireclickdetector(game:GetService("Workspace").Map["Haunted Castle"]["Lab Puzzle"].ColorFloor.Model.Part10.ClickDetector)
											wait(1)
											fireclickdetector(game:GetService("Workspace").Map["Haunted Castle"]["Lab Puzzle"].ColorFloor.Model.Part10.ClickDetector)
											wait(1)
											fireclickdetector(game:GetService("Workspace").Map["Haunted Castle"]["Lab Puzzle"].ColorFloor.Model.Part10.ClickDetector)
										else
											Quest3 = true
											--Not Work Yet
										end
									else
										if game:GetService("Workspace").NPCs:FindFirstChild("Ghost") then
											local args = {
												[1] = "GuitarPuzzleProgress",
												[2] = "Ghost"
											}

											game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
										end
										if game.Workspace.Enemies:FindFirstChild("Living Zombie [Lv. 2000]") then
											for i,v in pairs(game.Workspace.Enemies:GetChildren()) do
												if v:FindFirstChild("HumanoidRootPart") and v:FindFirstChild("Humanoid") and v.Humanoid.Health > 0 then
													if v.Name == "Living Zombie [Lv. 2000]" then
														Equipgui(_G.Select_gui)
														v.HumanoidRootPart.Size = Vector3.new(60,60,60)
														v.HumanoidRootPart.Transparency = 1
														v.Humanoid.JumpPower = 0
														v.Humanoid.WalkSpeed = 0
														v.HumanoidRootPart.CanCollide = false
														v.HumanoidRootPart.CFrame = game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame * CFrame.new(0,20,0)
														topos(CFrame.new(-10160.787109375, 138.6616973876953, 5955.03076171875))
														game:GetService'VirtualUser':CaptureController()
														game:GetService'VirtualUser':Button1Down(Vector2.new(1280, 672))
													end
												end
											end
										else
											topos(CFrame.new(-10160.787109375, 138.6616973876953, 5955.03076171875))
										end
									end
								else    
									if string.find(game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("gravestoneEvent",2), "Error") then
										print("Go to Grave")
										topos(CFrame.new(-8653.2060546875, 140.98487854003906, 6160.033203125))
									elseif string.find(game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("gravestoneEvent",2), "Nothing") then
										print("Wait Next Night")
									else
										game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("gravestoneEvent",2,true)
									end
								end
							end
						else
							topos(CFrame.new(-9681.458984375, 6.139880657196045, 6341.3720703125))
	end
	else
if _G.soulGuitarhop then
hop()
end
						end
					end
			end)
		end
end)

gui:Toggle("Auto Soul Guitar + Hop",false,function(value)
  _G.soulGuitarhop = value    
 end)

gui:Seperator(" Dual Curse Katana ")

gui:Toggle("Auto CDK Quest(Not Working)",_G.AutoCdk,function(value)
 _G.AutoCdk = value
end)

spawn(function()
		while wait() do
			pcall(function()
				if _G.AutoCdk then
					if GetMaterial("Alucard Fragment") == 0 then
						Auto_Quest_Yama_1 = true
						Auto_Quest_Yama_2 = false
						Auto_Quest_Yama_3 = false
						Auto_Quest_Tushita_1 = false
						Auto_Quest_Tushita_2 = false
						Auto_Quest_Tushita_3 = false
						game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("CDKQuest","Progress","Evil")
						game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("CDKQuest","StartTrial","Evil")
					elseif GetMaterial("Alucard Fragment") == 1 then
						Auto_Quest_Yama_1 = false
						Auto_Quest_Yama_2 = true
						Auto_Quest_Yama_3 = false
						Auto_Quest_Tushita_1 = false
						Auto_Quest_Tushita_2 = false
						Auto_Quest_Tushita_3 = false
						game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("CDKQuest","Progress","Evil")
						game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("CDKQuest","StartTrial","Evil")
					elseif GetMaterial("Alucard Fragment") == 2 then
						Auto_Quest_Yama_1 = false
						Auto_Quest_Yama_2 = false
						Auto_Quest_Yama_3 = true
						Auto_Quest_Tushita_1 = false
						Auto_Quest_Tushita_2 = false
						Auto_Quest_Tushita_3 = false
						game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("CDKQuest","Progress","Evil")
						game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("CDKQuest","StartTrial","Evil")
					elseif GetMaterial("Alucard Fragment") == 3 then
						Auto_Quest_Yama_1 = false
						Auto_Quest_Yama_2 = false
						Auto_Quest_Yama_3 = false
						Auto_Quest_Tushita_1 = true
						Auto_Quest_Tushita_2 = false
						Auto_Quest_Tushita_3 = false
						game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("CDKQuest","Progress","Good")
						game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("CDKQuest","StartTrial","Good")
					elseif GetMaterial("Alucard Fragment") == 4 then
						Auto_Quest_Yama_1 = false
						Auto_Quest_Yama_2 = false
						Auto_Quest_Yama_3 = false
						Auto_Quest_Tushita_1 = false
						Auto_Quest_Tushita_2 = true
						Auto_Quest_Tushita_3 = false
						game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("CDKQuest","Progress","Good")
						game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("CDKQuest","StartTrial","Good")
					elseif GetMaterial("Alucard Fragment") == 5 then
						Auto_Quest_Yama_1 = false
						Auto_Quest_Yama_2 = false
						Auto_Quest_Yama_3 = false
						Auto_Quest_Tushita_1 = false
						Auto_Quest_Tushita_2 = false
						Auto_Quest_Tushita_3 = true
						game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("CDKQuest","Progress","Good")
						game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("CDKQuest","StartTrial","Good")
					elseif GetMaterial("Alucard Fragment") == 6 then
						if game:GetService("Workspace").Enemies:FindFirstChild("Cursed Skeleton Boss [Lv. 2025] [Boss]") or game:GetService("Workspace").ReplicatedStorage:FindFirstChild("Cursed Skeleton Boss [Lv. 2025] [Boss]") then
							Auto_Quest_Yama_1 = false
							Auto_Quest_Yama_2 = false
							Auto_Quest_Yama_3 = false
							Auto_Quest_Tushita_1 = false
							Auto_Quest_Tushita_2 = false
							Auto_Quest_Tushita_3 = false
							if game:GetService("Workspace").Enemies:FindFirstChild("Cursed Skeleton Boss [Lv. 2025] [Boss]") or game:GetService("Workspace").Enemies:FindFirstChild("Cursed Skeleton [Lv. 2200]") then
								for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
									if v.Name == "Cursed Skeleton Boss [Lv. 2025] [Boss]" or v.Name == "Cursed Skeleton [Lv. 2200]" then
										if v.Humanoid.Health > 0 then
											v.HumanoidRootPart.CanCollide = false
											v.HumanoidRootPart.Size = Vector3.new(60, 60, 60)
											topos(v.HumanoidRootPart.CFrame * CFrame.new(0,50,0))
											game:GetService'VirtualUser':CaptureController()
											game:GetService'VirtualUser':Button1Down(Vector2.new(1280, 672))
										end
									end
								end
							end
						else
							if (CFrame.new(-12361.7060546875, 603.3547973632812, -6550.5341796875).Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 100 then
								game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("CDKQuest","Progress","Good")
								wait(1)
								game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("CDKQuest","Progress","Evil")
								wait(1)
								topos(CFrame.new(-12361.7060546875, 603.3547973632812, -6550.5341796875))
								wait(1.5)
								game:GetService("VirtualInputManager"):SendKeyEvent(true, "E", false, game)
								wait(1.5)
								topos(CFrame.new(-12253.5419921875, 598.8999633789062, -6546.8388671875))
							else
								topos(CFrame.new(-12361.7060546875, 603.3547973632812, -6550.5341796875))
							end   
						end
					end
				end
			end)
		end
	end)

	spawn(function()
		while wait() do
			if Auto_Quest_Yama_1 then
				pcall(function()
					if game:GetService("Workspace").Enemies:FindFirstChild("Mythological Pirate [Lv. 1850]") then
						for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
							if v.Name == "Mythological Pirate [Lv. 1850]" then
								repeat wait()
									topos(v.HumanoidRootPart.CFrame * CFrame.new(0,0,-2))
								until _G.AutoCdk == false or Auto_Cursed_Dual_Katana == false or Auto_Quest_Yama_1 == false
								game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("CDKQuest","StartTrial","Evil")
							end
						end
					else
						topos(CFrame.new(-13451.46484375, 543.712890625, -6961.0029296875))
					end
				end)
			end
		end
	end)

	spawn(function()
		while wait() do
			pcall(function()
				if Auto_Quest_Yama_2 then
					for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
						if v:FindFirstChild("HazeESP") then
							v.HazeESP.Size = UDim2.new(50,50,50,50)
							v.HazeESP.MaxDistance = "inf"
						end
					end
					for i,v in pairs(game:GetService("ReplicatedStorage"):GetChildren()) do
						if v:FindFirstChild("HazeESP") then
							v.HazeESP.Size = UDim2.new(50,50,50,50)
							v.HazeESP.MaxDistance = "inf"
						end
					end
				end
			end)
		end
	end)

	spawn(function()
		while wait() do
			pcall(function()
				for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
					if Auto_Quest_Yama_2 and v:FindFirstChild("HazeESP") and (v.HumanoidRootPart.Position - PosMonsEsp.Position).magnitude <= 300 then
						v.HumanoidRootPart.CFrame = PosMonsEsp
						v.HumanoidRootPart.CanCollide = false
						v.HumanoidRootPart.Size = Vector3.new(50,50,50)
						if not v.HumanoidRootPart:FindFirstChild("BodyVelocity") then
							local vc = Instance.new("BodyVelocity", v.HumanoidRootPart)
							vc.MaxForce = Vector3.new(1, 1, 1) * math.huge
							vc.Velocity = Vector3.new(0, 0, 0)
						end
					end
				end
			end)
		end
	end)

	spawn(function()
		while wait() do
			if Auto_Quest_Yama_2 then 
				pcall(function() 
					for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
						if v:FindFirstChild("HazeESP") then
							repeat wait()
								if (v.HumanoidRootPart.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 2000 then
									topos(y.HumanoidRootPart.CFrameMon * CFrame.new(0,20,0))
								else
									StartMagnet = true
									FastAttack = true
									if Auto_Buso then
										if not game.Players.LocalPlayer.Character:FindFirstChild("HasBuso") then
											game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("Buso")
										end
									end
									if not game.Players.LocalPlayer.Character:FindFirstChild(_G.Select_gui) then
										wait()
										Equipgui(_G.Select_gui)
									end
									PosMonsEsp = v.HumanoidRootPart.CFrame
									if not FastAttack then
										game:GetService'VirtualUser':CaptureController()
										game:GetService'VirtualUser':Button1Down(Vector2.new(1280, 672))
									end
									v.HumanoidRootPart.Size = Vector3.new(60,60,60)
									if _G.Configs["Show Hitbox"] then
										v.HumanoidRootPart.Transparency = _G.Hitbox_LocalTransparency
									else
										v.HumanoidRootPart.Transparency = 1
									end
									v.Humanoid.JumpPower = 0
									v.Humanoid.WalkSpeed = 0
									v.HumanoidRootPart.CanCollide = false
									v.Humanoid:ChangeState(11)
									topos(v.HumanoidRootPart.CFrame * CFrame.new(0,20,0))								
								end      
							until Auto_Cursed_Dual_Katana == false or Auto_Quest_Yama_2 == false or not v.Parent or v.Humanoid.Health <= 0 or not v:FindFirstChild("HazeESP")
						else
							for x,y in pairs(game:GetService("ReplicatedStorage"):GetChildren()) do
								if y:FindFirstChild("HazeESP") then
									if (y.HumanoidRootPart.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 2000 then
										topos(y.HumanoidRootPart.CFrameMon* CFrame.new(0,20,0))
									else
										topos(y.HumanoidRootPart.CFrame * CFrame.new(0,20,0))
									end
								end
							end
						end
					end
				end)
			end
		end
	end)

	spawn(function()
		while wait() do
			if Auto_Quest_Yama_3 then
				pcall(function()
					if game.Players.LocalPlayer.Backpack:FindFirstChild("Hallow Essence") then         
						_G.Main["Auto Farm Bone"] = false           
						topos(game:GetService("Workspace").Map["Haunted Castle"].Summoner.Detection.CFrame)
					elseif game:GetService("Workspace").Map:FindFirstChild("HellDimension") then
						repeat wait()
							if game:GetService("Workspace").Enemies:FindFirstChild("Cursed Skeleton [Lv. 2200]") or game:GetService("Workspace").Enemies:FindFirstChild("Cursed Skeleton [Lv. 2200] [Boss]") or game:GetService("Workspace").Enemies:FindFirstChild("Hell's Messenger [Lv. 2200] [Boss]") then
								for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
									if v.Name == "Cursed Skeleton [Lv. 2200]" or v.Name == "Cursed Skeleton [Lv. 2200] [Boss]" or v.Name == "Hell's Messenger [Lv. 2200] [Boss]" then
										if v.Humanoid.Health > 0 then
											repeat wait()
												StartMagnet = true
												FastAttack = true
												if Auto_Buso then
													if not game.Players.LocalPlayer.Character:FindFirstChild("HasBuso") then
														game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("Buso")
													end
												end
												if not game.Players.LocalPlayer.Character:FindFirstChild(_G.Select_gui) then
													wait()
													Equipgui(_G.Select_gui)
												end
												PosMonsEsp = v.HumanoidRootPart.CFrame
												if not FastAttack then
													game:GetService'VirtualUser':CaptureController()
													game:GetService'VirtualUser':Button1Down(Vector2.new(1280, 672))
												end
												v.HumanoidRootPart.Size = Vector3.new(60,60,60)
												if _G.Configs["Show Hitbox"] then
													v.HumanoidRootPart.Transparency = _G.Hitbox_LocalTransparency
												else
													v.HumanoidRootPart.Transparency = 1
												end
												v.Humanoid.JumpPower = 0
												v.Humanoid.WalkSpeed = 0
												v.HumanoidRootPart.CanCollide = false
												v.Humanoid:ChangeState(11)
												topos(v.HumanoidRootPart.CFrame * CFrame.new(0,50,0))
											until v.Humanoid.Health <= 0 or not v.Parent or Auto_Quest_Yama_3 == false
										end
									end
								end
							else
								wait(5)
								topos(game:GetService("Workspace").Map.HellDimension.Torch1.CFrame)
								wait(1.5)
								game:GetService("VirtualInputManager"):SendKeyEvent(true, "E", false, game)
								wait(1.5)        
								topos(game:GetService("Workspace").Map.HellDimension.Torch2.CFrame)
								wait(1.5)
								game:GetService("VirtualInputManager"):SendKeyEvent(true, "E", false, game)
								wait(1.5)     
								topos(game:GetService("Workspace").Map.HellDimension.Torch3.CFrame)
								wait(1.5)
								game:GetService("VirtualInputManager"):SendKeyEvent(true, "E", false, game)
								wait(1.5)     
								topos(game:GetService("Workspace").Map.HellDimension.Exit.CFrame)
							end
						until Auto_Cursed_Dual_Katana == false or Auto_Quest_Yama_3 == false or GetMaterial("Alucard Fragment") == 3
					else
						if game:GetService("Workspace").Enemies:FindFirstChild("Soul Reaper [Lv. 2100] [Raid Boss]") or game.ReplicatedStorage:FindFirstChild("Soul Reaper [Lv. 2100] [Raid Boss]") then
							if game:GetService("Workspace").Enemies:FindFirstChild("Soul Reaper [Lv. 2100] [Raid Boss]") then
								for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
									if v.Name == "Soul Reaper [Lv. 2100] [Raid Boss]" then
										if v.Humanoid.Health > 0 then
											repeat wait()
												topos(v.HumanoidRootPart.CFrame * CFrame.new(0,0,-2))
											until Auto_Cursed_Dual_Katana == false or Auto_Quest_Yama_3 == false or game:GetService("Workspace").Map:FindFirstChild("HellDimension")
										end
									end
								end
							else
								topos(CFrame.new(-9570.033203125, 315.9346923828125, 6726.89306640625))
							end
						else
							_G.Main["Auto Farm Bone"] = true
							game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("Bones","Buy",1,1)
						end
					end
				end)
			end
		end
	end)

	spawn(function() 
		while wait() do
			if Auto_Quest_Tushita_1 then
				game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("CDKQuest","BoatQuest",workspace.NPCs:FindFirstChild("Luxury Boat Dealer"))
			end
		end
	end)

	spawn(function()
		while wait() do
			if Auto_Quest_Tushita_1 then
				topos(CFrame.new(-9546.990234375, 21.139892578125, 4686.1142578125))
				wait(5)
				topos(CFrame.new(-6120.0576171875, 16.455780029296875, -2250.697265625))
				wait(5)
				topos(CFrame.new(-9533.2392578125, 7.254445552825928, -8372.69921875))    
			end
		end
	end)

	spawn(function()
		while wait() do
			if Auto_Quest_Tushita_2 then
				pcall(function()
					if (CFrame.new(-5539.3115234375, 313.800537109375, -2972.372314453125).Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 500 then
						for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
							if Auto_Quest_Tushita_2 and v:FindFirstChild("HumanoidRootPart") and v:FindFirstChild("Humanoid") and v.Humanoid.Health > 0 then
								if (v.HumanoidRootPart.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude < 2000 then
									repeat wait()
										v.HumanoidRootPart.CanCollide = false
										v.HumanoidRootPart.Size = Vector3.new(60, 60, 60)
										topos(v.HumanoidRootPart.CFrame * CFrame.new(0,50,0))
										game:GetService'VirtualUser':CaptureController()
										game:GetService'VirtualUser':Button1Down(Vector2.new(1280, 672))
									until v.Humanoid.Health <= 0 or not v.Parent or Auto_Quest_Tushita_2 == false
								end
							end
						end
					else
						topos(CFrame.new(-5545.1240234375, 313.800537109375, -2976.616455078125))
					end
				end)
			end
		end
	end)

	spawn(function()
		while wait() do
			if Auto_Quest_Tushita_3 then
				pcall(function()
					if game:GetService("Workspace").Enemies:FindFirstChild("Cake Queen [Lv. 2175] [Boss]") or game.ReplicatedStorage:FindFirstChild("Cake Queen [Lv. 2175] [Boss]") then
						if game:GetService("Workspace").Enemies:FindFirstChild("Cake Queen [Lv. 2175] [Boss]") then
							for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
								if v.Name == "Cake Queen [Lv. 2175] [Boss]" then
									if v.Humanoid.Health > 0 then
										repeat wait()
											if Auto_Buso then
												if not game.Players.LocalPlayer.Character:FindFirstChild("HasBuso") then
													game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("Buso")
												end
											end
											if not game.Players.LocalPlayer.Character:FindFirstChild(_G.Select_gui) then
												wait()
												Equipgui(_G.Select_gui)
											end
											if not FastAttack then
												game:GetService'VirtualUser':CaptureController()
												game:GetService'VirtualUser':Button1Down(Vector2.new(1280, 672))
											end
											v.HumanoidRootPart.Size = Vector3.new(60,60,60)
											if _G.Configs["Show Hitbox"] then
												v.HumanoidRootPart.Transparency = _G.Hitbox_LocalTransparency
											else
												v.HumanoidRootPart.Transparency = 1
											end
											v.Humanoid.JumpPower = 0
											v.Humanoid.WalkSpeed = 0
											v.HumanoidRootPart.CanCollide = false
											v.Humanoid:ChangeState(11)
											topos(v.HumanoidRootPart.CFrame * CFrame.new(0,50,0))
										until Auto_Cursed_Dual_Katana == false or Auto_Quest_Tushita_3 == false or game:GetService("Workspace").Map:FindFirstChild("HeavenlyDimension")
									end
								end
							end
						else
							topos(CFrame.new(-709.3132934570312, 381.6005859375, -11011.396484375))
						end
					elseif game:GetService("Workspace").Map:FindFirstChild("HeavenlyDimension") then
						repeat wait()
							if game:GetService("Workspace").Enemies:FindFirstChild("Cursed Skeleton [Lv. 2200]") or game:GetService("Workspace").Enemies:FindFirstChild("Cursed Skeleton [Lv. 2200] [Boss]") or game:GetService("Workspace").Enemies:FindFirstChild("Heaven's Guardian [Lv. 2200] [Boss]") then
								for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
									if v.Name == "Cursed Skeleton [Lv. 2200]" or v.Name == "Cursed Skeleton [Lv. 2200] [Boss]" or v.Name == "Heaven's Guardian [Lv. 2200] [Boss]" then
										if v.Humanoid.Health > 0 then
											repeat wait()
												if Auto_Buso then
													if not game.Players.LocalPlayer.Character:FindFirstChild("HasBuso") then
														game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("Buso")
													end
												end
												if not game.Players.LocalPlayer.Character:FindFirstChild(_G.Select_gui) then
													wait()
													Equipgui(_G.Select_gui)
												end
												if not FastAttack then
													game:GetService'VirtualUser':CaptureController()
													game:GetService'VirtualUser':Button1Down(Vector2.new(1280, 672))
												end
												v.HumanoidRootPart.Size = Vector3.new(60,60,60)
												if _G.Configs["Show Hitbox"] then
													v.HumanoidRootPart.Transparency = _G.Hitbox_LocalTransparency
												else
													v.HumanoidRootPart.Transparency = 1
												end
												v.Humanoid.JumpPower = 0
												v.Humanoid.WalkSpeed = 0
												v.HumanoidRootPart.CanCollide = false
												v.Humanoid:ChangeState(11)
											until v.Humanoid.Health <= 0 or not v.Parent or Auto_Quest_Tushita_3 == false
										end
									end
								end
							else
								wait(5)
								topos(game:GetService("Workspace").Map.HeavenlyDimension.Torch1.CFrame)
								wait(1.5)
								game:GetService("VirtualInputManager"):SendKeyEvent(true, "E", false, game)
								wait(1.5)        
								topos(game:GetService("Workspace").Map.HeavenlyDimension.Torch2.CFrame)
								wait(1.5)
								game:GetService("VirtualInputManager"):SendKeyEvent(true, "E", false, game)
								wait(1.5)     
								topos(game:GetService("Workspace").Map.HeavenlyDimension.Torch3.CFrame)
								wait(1.5)
								game:GetService("VirtualInputManager"):SendKeyEvent(true, "E", false, game)
								wait(1.5)     
								topos(game:GetService("Workspace").Map.HeavenlyDimension.Exit.CFrame)
							end
						until Auto_Cursed_Dual_Katana == false or Auto_Quest_Tushita_3 == false or GetMaterial("Alucard Fragment") == 6
					else
						hop()
					end
				end)
			end
		end
	end)
end

if World1 then

gui:Seperator(" Auto Saber ")

gui:Toggle("Auto Saber",_G.AutoSaber,function(value)
				_G.AutoSaber = value
			end)
			
			gui:Toggle("Auto Saber Hop",_G.AutoSaberHop,function(value)
				_G.AutoSaberHop = value
			end)
			
 spawn(function()
            while wait() do
                if _G.AutoSaber then
                    if game.Players.localPlayer.Data.Level.Value < 200 then
                    else
                        if game.Workspace.Map.Jungle.Final.Part.CanCollide == false then
                            if _G.AutoSaber and game.ReplicatedStorage:FindFirstChild("Saber Expert [Lv. 200] [Boss]") or game.Workspace.Enemies:FindFirstChild("Saber Expert [Lv. 200] [Boss]") then
                                if game.Workspace.Enemies:FindFirstChild("Saber Expert [Lv. 200] [Boss]") then
                                    for i,v in pairs(game.Workspace.Enemies:GetChildren()) do
                                        if v.Name == "Saber Expert [Lv. 200] [Boss]" and v:FindFirstChild("HumanoidRootPart") and v:FindFirstChild("Humanoid") and v.Humanoid.Health > 0 then
                                            repeat wait()
                                                if (v.HumanoidRootPart.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).magnitude > 300 then
                                                    Farmtween = topos(v.HumanoidRootPart.Position,v.HumanoidRootPart.CFrame)
                                                elseif (v.HumanoidRootPart.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).magnitude <= 300 then
                                                    if Farmtween then
                                                        Farmtween:Stop()
                                                    end
                                                    AutoHaki()
                                                    Equipgui(_G.Selectgui)
                                                    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = v.HumanoidRootPart.CFrame * CFrame.new(0, 30, 0)
                                                    game:GetService'VirtualUser':CaptureController()
                                                    game:GetService'VirtualUser':Button1Down(Vector2.new(1280, 672))
                                                end
                                            until not _G.Auto_Saber or not v.Parent or v.Humanoid.Health <= 0
                                        end
                                    end
                                else
                                    Questtween = topos(CFrame.new(-1405.41956, 29.8519993, 5.62435055).Position,CFrame.new(-1405.41956, 29.8519993, 5.62435055))
                                    if (CFrame.new(-1405.41956, 29.8519993, 5.62435055).Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).magnitude <= 300 then
                                        if Questtween then
                                            Questtween:Stop()
                                        end
                                        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-1405.41956, 29.8519993, 5.62435055, 0.885240912, 3.52892613e-08, 0.465132833, -6.60881128e-09, 1, -6.32913171e-08, -0.465132833, 5.29540891e-08, 0.885240912)
                                    end
                                end
                            else
                                if _G.AutoSaberHop then
                                    Hop()
                                end
                            end
                        elseif game.Players.LocalPlayer.Backpack:FindFirstChild("Relic") or game.Players.LocalPlayer.Character:FindFirstChild("Relic") and game.Players.localPlayer.Data.Level.Value >= 200 then
                            Equipgui("Relic")
                            wait(0.5)
                            Questtween = topos(CFrame.new(-1405.41956, 29.8519993, 5.62435055).Position,CFrame.new(-1405.41956, 29.8519993, 5.62435055))
                            if (CFrame.new(-1405.41956, 29.8519993, 5.62435055).Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).magnitude <= 300 then
                                if Questtween then
                                    Questtween:Stop()
                                end
                                game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-1405.41956, 29.8519993, 5.62435055, 0.885240912, 3.52892613e-08, 0.465132833, -6.60881128e-09, 1, -6.32913171e-08, -0.465132833, 5.29540891e-08, 0.885240912)
                            end
                        else
                            if Workspace.Map.Jungle.QuestPlates.Door.CanCollide == false then
                                if game.Workspace.Map.Desert.Burn.Part.CanCollide == false then
                                    if game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("ProQuestProgress","SickMan") == 0 then
                                        if game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("ProQuestProgress","RichSon") == 0 then
                                            if game.Workspace.Enemies:FindFirstChild("Mob Leader [Lv. 120] [Boss]") then
                                                for i,v in pairs(game.Workspace.Enemies:GetChildren()) do
                                                    if _G.AutoSaber and v:IsA("Model") and v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 and v.Name == "Mob Leader [Lv. 120] [Boss]" then
                                                        repeat
                                                            pcall(function() wait() 
                                                                if (v.HumanoidRootPart.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).magnitude > 300 then
                                                                    Farmtween = topos(v.HumanoidRootPart.Position,v.HumanoidRootPart.CFrame)
                                                                elseif (v.HumanoidRootPart.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).magnitude <= 300 then
                                                                    if Farmtween then
                                                                        Farmtween:Stop()
                                                                    end
                                                                    AutoHaki()
                                                                    Equipgui(_G.Selectgui)
                                                                    if not game.Players.LocalPlayer.Character:FindFirstChild("HasBuso") then
                                                                        local args = {
                                                                            [1] = "Buso"
                                                                        }
                                                                        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
                                                                    end
                                                                    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = v.HumanoidRootPart.CFrame * CFrame.new(0, 30, 0)
                                                                    game:GetService'VirtualUser':CaptureController()
                                                                    game:GetService'VirtualUser':Button1Down(Vector2.new(1280, 672))
                                                                end
                                                            end)
                                                        until not _G.AutoSaber or not v.Parent or v.Humanoid.Health <= 0
                                                    end
                                                end
                                            else
                                                Questtween = topos(CFrame.new(-2848.59399, 7.4272871, 5342.44043).Position,CFrame.new(-2848.59399, 7.4272871, 5342.44043))
                                                if (CFrame.new(-2848.59399, 7.4272871, 5342.44043).Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).magnitude <= 300 then
                                                    if Questtween then
                                                        Questtween:Stop()
                                                    end
                                                    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-2848.59399, 7.4272871, 5342.44043, -0.928248107, -8.7248246e-08, 0.371961564, -7.61816636e-08, 1, 4.44474857e-08, -0.371961564, 1.29216433e-08, -0.928248107)
                                                end
                                            end
                                        elseif game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("ProQuestProgress","RichSon") == 1 then
                                            if game.Players.LocalPlayer.Backpack:FindFirstChild("Relic") or game.Players.LocalPlayer.Character:FindFirstChild("Relic") then
                                                Equipgui("Relic")
                                                wait(0.5)
                                                Questtween = topos(CFrame.new(-1405.41956, 29.8519993, 5.62435055).Position,CFrame.new(-1405.41956, 29.8519993, 5.62435055))
                                                if (CFrame.new(-1405.41956, 29.8519993, 5.62435055).Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).magnitude <= 300 then
                                                    if Questtween then
                                                        Questtween:Stop()
                                                    end
                                                    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-1405.41956, 29.8519993, 5.62435055)
                                                end
                                            else
                                                Questtween = topos(CFrame.new(-910.979736, 13.7520342, 4078.14624).Position,CFrame.new(-910.979736, 13.7520342, 4078.14624))
                                                if (CFrame.new(-910.979736, 13.7520342, 4078.14624).Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).magnitude <= 300 then
                                                    if Questtween then
                                                        Questtween:Stop()
                                                    end
                                                    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-910.979736, 13.7520342, 4078.14624, 0.00685182028, -1.53155766e-09, -0.999976516, 9.15205245e-09, 1, -1.46888401e-09, 0.999976516, -9.14177267e-09, 0.00685182028)
                                                    wait(.5)
                                                    local args = {
                                                        [1] = "ProQuestProgress",
                                                        [2] = "RichSon"
                                                    }
                                                    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
                                                end
                                            end
                                        else
                                            Questtween = topos(CFrame.new(-910.979736, 13.7520342, 4078.14624).Position,CFrame.new(-910.979736, 13.7520342, 4078.14624))
                                            if (CFrame.new(-910.979736, 13.7520342, 4078.14624).Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).magnitude <= 300 then
                                                if Questtween then
                                                    Questtween:Stop()
                                                end
                                                game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-910.979736, 13.7520342, 4078.14624)
                                                local args = {
                                                    [1] = "ProQuestProgress",
                                                    [2] = "RichSon"
                                                }
                                                game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
                                            end
                                        end
                                    else
                                        if game.Players.LocalPlayer.Backpack:FindFirstChild("Cup") or game.Players.LocalPlayer.Character:FindFirstChild("Cup") then
                                            Equipgui("Cup")
                                            if game.Players.LocalPlayer.Character.Cup.Handle:FindFirstChild("TouchInterest") then
                                                Questtween = topos(CFrame.new(1397.229, 37.3480148, -1320.85217).Position,CFrame.new(1397.229, 37.3480148, -1320.85217))
                                                if (CFrame.new(1397.229, 37.3480148, -1320.85217).Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).magnitude <= 300 then
                                                    if Questtween then
                                                        Questtween:Stop()
                                                    end
                                                    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(1397.229, 37.3480148, -1320.85217, -0.11285457, 2.01368788e-08, 0.993611455, 1.91641178e-07, 1, 1.50028845e-09, -0.993611455, 1.90586206e-07, -0.11285457)
                                                end
                                            else
                                                wait(0.5)
                                                if game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("ProQuestProgress","SickMan") ~= 0 then
                                                    local args = {
                                                        [1] = "ProQuestProgress",
                                                        [2] = "SickMan"
                                                    }
                                                    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
                                                end
                                            end
                                        else
                                            Questtween = topos(game.Workspace.Map.Desert.Cup.Position,game.Workspace.Map.Desert.Cup.CFrame)
                                            if (game.Workspace.Map.Desert.Cup.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).magnitude <= 300 then
                                                if Questtween then
                                                    Questtween:Stop()
                                                end
                                                game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = game.Workspace.Map.Desert.Cup.CFrame
                                            end
                                            firetouchinterest(game.Workspace.Map.Desert.Cup.TouchInterest,game.Players.LocalPlayer.Character.Head, 1)
                                        end
                                    end
                                else
                                    if game.Players.LocalPlayer.Backpack:FindFirstChild("Torch") or game.Players.LocalPlayer.Character:FindFirstChild("Torch") then
                                        Equipgui("Torch")
                                        Questtween = topos(CFrame.new(1114.87708, 4.9214654, 4349.8501).Position,CFrame.new(1114.87708, 4.9214654, 4349.8501))
                                        if (CFrame.new(1114.87708, 4.9214654, 4349.8501).Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).magnitude <= 300 then
                                            if Questtween then
                                                Questtween:Stop()
                                            end
                                            game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(1114.87708, 4.9214654, 4349.8501, -0.612586915, -9.68697833e-08, 0.790403247, -1.2634203e-07, 1, 2.4638446e-08, -0.790403247, -8.47679615e-08, -0.612586915)
                                        end
                                    else
                                        Questtween = topos(CFrame.new(-1610.00757, 11.5049858, 164.001587).Position,CFrame.new(-1610.00757, 11.5049858, 164.001587))
                                        if (CFrame.new(-1610.00757, 11.5049858, 164.001587).Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).magnitude <= 300 then
                                            if Questtween then
                                                Questtween:Stop()
                                            end
                                            game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-1610.00757, 11.5049858, 164.001587, 0.984807551, -0.167722285, -0.0449818149, 0.17364943, 0.951244235, 0.254912198, 3.42372805e-05, -0.258850515, 0.965917408)
                                        end
                                    end
                                end
                            else
                                for i,v in pairs(Workspace.Map.Jungle.QuestPlates:GetChildren()) do
                                    if v:IsA("Model") then wait()
                                        if v.Button.BrickColor ~= BrickColor.new("Camo") then
                                            repeat wait()
                                                Questtween = topos(v.Button.Position,v.Button.CFrame)
                                                if (v.Button.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).magnitude <= 150 then
                                                    if Questtween then
                                                        Questtween:Stop()
                                                    end
                                                    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = v.Button.CFrame
                                                end
                                            until not _G.AutoSaber or v.Button.BrickColor == BrickColor.new("Camo")
                                        end
                                    end
                                end    
                            end
                        end
                    end 
                end
            end
        end)
	
	gui:Seperator(" Pole ")
	
	gui:Toggle("Auto Pole V.1",_G.AutoPole,function(value)
        _G.AutoPole = value
        StopTween(_G.AutoPole)
    end)
    
    gui:Toggle("Auto Pole V.1 Hop",_G.AutoPoleHop,function(value)
        _G.AutoPoleHop = value
    end)
    
    spawn(function()
        while wait() do
            if _G.AutoPole then
                pcall(function()
                    if game:GetService("Workspace").Enemies:FindFirstChild("Thunder God [Lv. 575] [Boss]") then
                        for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                            if v.Name == "Thunder God [Lv. 575] [Boss]" then
                                if v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
                                    repeat task.wait()
                                        AutoHaki()
                                        Equipgui(_G.Selectgui)
                                        v.HumanoidRootPart.CanCollide = false
                                        v.Humanoid.WalkSpeed = 0
                                        v.HumanoidRootPart.Size = Vector3.new(50,50,50)
                                        topos(v.HumanoidRootPart.CFrame * MethodFarm)                         
                                        game:GetService("VirtualUser"):CaptureController()
                                        game:GetService("VirtualUser"):Button1Down(Vector2.new(1280,672))
                                        sethiddenproperty(game.Players.LocalPlayer,"SimulationRadius",math.huge)
                                    until not _G.AutoPole or not v.Parent or v.Humanoid.Health <= 0
                                end
                            end
                        end
                    else
                        if game:GetService("ReplicatedStorage"):FindFirstChild("Thunder God [Lv. 575] [Boss]") then
                            topos(game:GetService("ReplicatedStorage"):FindFirstChild("Thunder God [Lv. 575] [Boss]").HumanoidRootPart.CFrame * CFrame.new(5,10,7))
                        else
                            if _G.AutoPoleHop then
                                Hop()
                            end
                        end
                    end
                end)
            end
        end
    end)

elseif World2 then

gui:Seperator(" Bartilo Quest ")

gui:Toggle("Auto Bartilo Quest",_G.Auto_Bartilo_Quest,function(value)
 _G.Auto_Bartilo_Quest = value
StopTween(_G.Auto_Bartilo_Quest)
end)

gui:Seperator(" Race V2 ")

gui:Toggle("Auto Evo Race [V2]",_G.Auto_Evo_Race_V2,function(value)
 _G.Auto_Evo_Race_V2 = value
StopTween(_G.Auto_Evo_Race_V2)
end)
	

	spawn(function()
		game:GetService("RunService").Heartbeat:Connect(function()
			pcall(function()
				for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
					if _G.Auto_Evo_Race_V2 and StartEvoStartMagnet and v.Name == "Swan Pirate [Lv. 775]" and (v.HumanoidRootPart.Position - PosMonEvo.Position).magnitude <= 350 then
						v.HumanoidRootPart.CFrame = PosMonEvo
						v.HumanoidRootPart.CanCollide = false
						v.HumanoidRootPart.Size = Vector3.new(50,50,50)
						if v.Humanoid:FindFirstChild("Animator") then
							v.Humanoid.Animator:Destroy()
						end
						sethiddenproperty(game.Players.LocalPlayer, "SimulationRadius",  math.huge)
					end
				end
			end)
		end)
	end)

	spawn(function()
		pcall(function()
			while wait() do
				if _G.Auto_Evo_Race_V2 then
					if not game:GetService("Players").LocalPlayer.Data.Race:FindFirstChild("Evolved") then
						if game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("Alchemist","1") == 0 then
							topos(CFrame.new(-2779.83521, 72.9661407, -3574.02002, -0.730484903, 6.39014104e-08, -0.68292886, 3.59963224e-08, 1, 5.50667032e-08, 0.68292886, 1.56424669e-08, -0.730484903))
							if (Vector3.new(-2779.83521, 72.9661407, -3574.02002) - game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 4 then
								wait(1.3)
								game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("Alchemist","2")
							end
						elseif game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("Alchemist","1") == 1 then
							pcall(function()
								if not game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Flower 1") and not game:GetService("Players").LocalPlayer.Character:FindFirstChild("Flower 1") then
									topos(game:GetService("Workspace").Flower1.CFrame)
								elseif not game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Flower 2") and not game:GetService("Players").LocalPlayer.Character:FindFirstChild("Flower 2") then
									topos(game:GetService("Workspace").Flower2.CFrame)
								elseif not game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Flower 3") and not game:GetService("Players").LocalPlayer.Character:FindFirstChild("Flower 3") then
									if game:GetService("Workspace").Enemies:FindFirstChild("Swan Pirate [Lv. 775]") then
										for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
											if v.Name == "Swan Pirate [Lv. 775]" then
												repeat wait()
													AutoHaki()
													Equipgui(_G.Select_gui)
													topos(v.HumanoidRootPart.CFrame * MethodFarm)
													v.HumanoidRootPart.CanCollide = false
													v.HumanoidRootPart.Size = Vector3.new(50,50,50)
													game:GetService'VirtualUser':CaptureController()
													game:GetService'VirtualUser':Button1Down(Vector2.new(1280, 672))
													PosMonEvo = v.HumanoidRootPart.CFrame
													StartEvoStartMagnet = true
												until game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Flower 3") or not v.Parent or v.Humanoid.Health <= 0 or _G.Auto_Evo_Race_V2 == false
												StartEvoStartMagnet = false
											end
										end
									else
										StartEvoStartMagnet = false
										topos(CFrame.new(980.0985107421875, 121.331298828125, 1287.2093505859375))
									end
								end
							end)
						elseif game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("Alchemist","1") == 2 then
							game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("Alchemist","3")
						end
					end
				end
			end
		end)
	end)

gui:Seperator(" Legendary Sword ")

gui:Toggle("Auto Buy Legendary Sword",_G.AutoBuyLegendarySword,function(Value)
			_G.AutoBuyLegendarySword = Value
		end)
		spawn(function()
            while wait() do
                if _G.AutoBuyLegendarySword then
                    pcall(function()
                        local args = {
                            [1] = "LegendarySwordDealer",
                            [2] = "1"
                        }
                        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
                        local args = {
                            [1] = "LegendarySwordDealer",
                            [2] = "2"
                        }
                        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
                        local args = {
                            [1] = "LegendarySwordDealer",
                            [2] = "3"
                        }
                        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
                        if _G.AutoBuyLegendarySword_Hop and _G.AutoBuyLegendarySword and World2 then
                            wait(10)
                            Hop()
                        end
                    end)
                end 
            end
		end)

		gui:Toggle("Auto Buy Legendary Sword Hop",_G.AutoBuySwordHop,function(Value)
			_G.AutoBuyLegendarySword_Hop = Value
		end)
		spawn(function()
			while _G.AutoBuyLegendarySword_Hop do wait()
				if _G.AutoBuyLegendarySword_Hop then
					hop()
				end 
			end
		end)

	spawn(function()
		while wait(7) do
			if _G.AutoBuySwordHop or _G.HakiColorHop then
				local PlaceID = game.PlaceId
				local AllIDs = {}
				local foundAnything = ""
				local actualHour = os.date("!*t").hour
				local Deleted = false
				function TPReturner()
					local Site;
					if foundAnything == "" then
						Site = game.HttpService:JSONDecode(game:HttpGet('https://games.roblox.com/v1/games/' .. PlaceID .. '/servers/Public?sortOrder=Asc&limit=100'))
					else
						Site = game.HttpService:JSONDecode(game:HttpGet('https://games.roblox.com/v1/games/' .. PlaceID .. '/servers/Public?sortOrder=Asc&limit=100&cursor=' .. foundAnything))
					end
					local ID = ""
					if Site.nextPageCursor and Site.nextPageCursor ~= "null" and Site.nextPageCursor ~= nil then
						foundAnything = Site.nextPageCursor
					end
					local num = 0;
					for i,v in pairs(Site.data) do
						local Possible = true
						ID = tostring(v.id)
						if tonumber(v.maxPlayers) > tonumber(v.playing) then
							for _,Existing in pairs(AllIDs) do
								if num ~= 0 then
									if ID == tostring(Existing) then
										Possible = false
									end
								else
									if tonumber(actualHour) ~= tonumber(Existing) then
										local delFile = pcall(function()
											-- delfile("NotSameServers.json")
											AllIDs = {}
											table.insert(AllIDs, actualHour)
										end)
									end
								end
								num = num + 1
							end
							if Possible == true then
								table.insert(AllIDs, ID)
								wait()
								pcall(function()
									-- writefile("NotSameServers.json", game:GetService('HttpService'):JSONEncode(AllIDs))
									wait()
									game:GetService("TeleportService"):TeleportToPlaceInstance(PlaceID, ID, game.Players.LocalPlayer)
								end)
								wait(4)
							end
						end
					end
				end
				function Teleport() 
					while wait() do
						pcall(function()
							TPReturner()
							if foundAnything ~= "" then
								TPReturner()
							end
						end)
					end
				end
				Teleport()
			end
		end
	end)

gui:Seperator(" Haki Color Enhancement ")

	gui:Toggle("Auto Buy Enchancement",_G.Auto_Buy_Enchancement,function(value)
 _G.Auto_Buy_Enchancement = value
StopTween(_G.Auto_Buy_Enchancement)
end)
	
	
	spawn(function()
		while wait() do
			if _G.Auto_Buy_Enchancement then
				local args = {
					[1] = "ColorsDealer",
					[2] = "2"
				}
				game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
			end 
		end
	end)

		gui:Seperator(" Rengoku ")

	gui:Toggle("Auto Rengoku",_G.Auto_Rengoku,function(value)
 _G.Auto_Rengoku = value
StopTween(_G.Auto_Rengoku)
end)


	spawn(function()
		game:GetService("RunService").Heartbeat:Connect(function()
			pcall(function()
				for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
					if _G.Auto_Rengoku and StartRengokuStartMagnet and (v.Name == "Snow Lurker [Lv. 1375]" or v.Name == "Arctic Warrior [Lv. 1350]") and (v.HumanoidRootPart.Position - RengokuMon.Position).magnitude <= 350 then
						v.HumanoidRootPart.CFrame = RengokuMon
						v.HumanoidRootPart.CanCollide = false
						v.HumanoidRootPart.Size = Vector3.new(50,50,50)
						if v.Humanoid:FindFirstChild("Animator") then
							v.Humanoid.Animator:Destroy()
						end
						sethiddenproperty(game.Players.LocalPlayer, "SimulationRadius",  math.huge)
					end
				end
			end)
		end)
	end)

	spawn(function()
		while wait() do
			if _G.Auto_Rengoku then
				pcall(function()
					if game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Hidden Key") or game:GetService("Players").LocalPlayer.Character:FindFirstChild("Hidden Key") then
						Equipgui("Hidden Key")
						topos(CFrame.new(6571.1201171875, 299.23028564453, -6967.841796875))
					elseif game:GetService("Workspace").Enemies:FindFirstChild("Snow Lurker [Lv. 1375]") or game:GetService("Workspace").Enemies:FindFirstChild("Arctic Warrior [Lv. 1350]") then
						for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
							if (v.Name == "Snow Lurker [Lv. 1375]" or v.Name == "Arctic Warrior [Lv. 1350]") and v.Humanoid.Health > 0 then
								repeat wait()
									AutoHaki()
									Equipgui(_G.Select_gui)
									v.HumanoidRootPart.CanCollide = false
									v.HumanoidRootPart.Size = Vector3.new(50,50,50)
									RengokuMon = v.HumanoidRootPart.CFrame
									topos(v.HumanoidRootPart.CFrame * MethodFarm)
									game:GetService'VirtualUser':CaptureController()
									game:GetService'VirtualUser':Button1Down(Vector2.new(1280, 672))
									StartRengokuStartMagnet = true
								until game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Hidden Key") or _G.Auto_Rengoku == false or not v.Parent or v.Humanoid.Health <= 0
								StartRengokuStartMagnet = false
							end
						end
					else
						StartRengokuStartMagnet = false
						topos(CFrame.new(5439.716796875, 84.420944213867, -6715.1635742188))
					end
				end)
			end
		end
	end)
	
		gui:Seperator(" Swan Glasses ")

gui:Toggle("Auto Swan Glasses",_G.Auto_Swan_Glasses,function(value)
 _G.Auto_Swan_Glasses = value
StopTween(_G.Auto_Swan_Glasses)
end)


	gui:Toggle("Auto Swan Glasses Hop",_G.Auto_Swan_Glasses_Hop,function(value)
 _G.Auto_Swan_Glasses_Hop = value
end)

	spawn(function()
		while wait() do
			pcall(function()
				if _G.Auto_Swan_Glasses and game.ReplicatedStorage:FindFirstChild("Don Swan [Lv. 1000] [Boss]") or game.Workspace.Enemies:FindFirstChild("Don Swan [Lv. 1000] [Boss]") then
					if game.Workspace.Enemies:FindFirstChild("Don Swan [Lv. 1000] [Boss]") then
						for i,v in pairs(game.Workspace.Enemies:GetChildren()) do
							if _G.Auto_Swan_Glasses and v.Name == "Don Swan [Lv. 1000] [Boss]" and v:FindFirstChild("HumanoidRootPart") and v:FindFirstChild("Humanoid") and v.Humanoid.Health > 0 then
								repeat wait()  
									Equipgui(_G.Select_gui)
									AutoHaki()
									topos(v.HumanoidRootPart.CFrame * MethodFarm)
									game:GetService'VirtualUser':CaptureController()
									game:GetService'VirtualUser':Button1Down(Vector2.new(1280, 672))
								until not _G.Auto_Swan_Glasses or v.Humanoid.Health <= 0 or not v.Parent
							end
						end
					else
						topos(CFrame.new(2289.47900390625, 15.152046203613281, 739.512939453125))
					end
				else
					if _G.Auto_Swan_Glasses_Hop then
						hop()
					end
				end
			end)
		end
	end)
	
		gui:Seperator(" Trident ")
	
	gui:Toggle("Auto Dragon Trident",_G.Auto_Dragon_Trident,function(value)
 _G.Auto_Dragon_Trident = value
StopTween(_G.Auto_Dragon_Trident)
end)

	
	gui:Toggle("Auto Dragon Trident Hop",_G.Auto_Dragon_Trident_Hop,function(value)
_G.Auto_Dragon_Trident_Hop = value
end)
	
	

	spawn(function()
		while wait() do
			if _G.Auto_Dragon_Trident then
				pcall(function()
					if _G.Auto_Dragon_Trident and game.ReplicatedStorage:FindFirstChild("Tide Keeper [Lv. 1475] [Boss]") or game.Workspace.Enemies:FindFirstChild("Tide Keeper [Lv. 1475] [Boss]") then
						if game.Workspace.Enemies:FindFirstChild("Tide Keeper [Lv. 1475] [Boss]") then
							for i,v in pairs(game.Workspace.Enemies:GetChildren()) do
								if v.Name == "Tide Keeper [Lv. 1475] [Boss]" and v:FindFirstChild("HumanoidRootPart") and v:FindFirstChild("Humanoid") and v.Humanoid.Health > 0 then
									repeat wait()
										Equipgui(_G.Select_gui)
										AutoHaki()
										topos(v.HumanoidRootPart.CFrame * MethodFarm)
										game:GetService'VirtualUser':CaptureController()
										game:GetService'VirtualUser':Button1Down(Vector2.new(1280, 672))
									until _G.Auto_Dragon_Trident or v.Humanoid.Health <= 0 or not v.Parent
								end
							end
						else
							topos(CFrame.new(-3914.830322265625, 123.29389190673828, -11516.8642578125))
						end
					else
						if _G.Auto_Dragon_Trident_Hop then
							hop()
						end
					end
				end)
			end
		end
	end)

	

elseif World3 then

	gui:Seperator(" Soul Reaper ")

gui:Toggle("Auto Soul Reaper",_G.Auto_Soul_Reaper,function(value)
 _G.Auto_Soul_Reaper = value
StopTween(_G.Auto_Soul_Reaper)
end)


gui:Toggle("Auto Soul Reaper Hop",_G.Auto_Soul_Reaper_Hop,function(value)
 _G.Auto_Soul_Reaper_Hop = value
StopTween(_G.Auto_Soul_Reaper_Hop)
end)


	spawn(function()
		while wait() do
			if _G.Auto_Soul_Reaper then
				pcall(function()
					if game.Players.LocalPlayer.Backpack:FindFirstChild("Hallow Essence") then                    
						topos(CFrame.new(-8932.83789, 144.098709, 6059.34229, -0.999290943, 7.95623478e-09, -0.0376505218, 4.4684243e-09, 1, 9.27205832e-08, 0.0376505218, 9.24866086e-08, -0.999290943))  
					elseif game:GetService("Workspace").Enemies:FindFirstChild("Soul Reaper [Lv. 2100] [Raid Boss]") or game.ReplicatedStorage:FindFirstChild("Soul Reaper [Lv. 2100] [Raid Boss]") then
						if game.Workspace.Enemies:FindFirstChild ("Soul Reaper [Lv. 2100] [Raid Boss]") then    
							for i, v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
								if v.Name == "Soul Reaper [Lv. 2100] [Raid Boss]"  then
									if _G.Auto_Soul_Reaper and v.Name == "Soul Reaper [Lv. 2100] [Raid Boss]" and v:FindFirstChild("HumanoidRootPart") and v:FindFirstChild("Humanoid") and v.Humanoid.Health > 0 then
										repeat wait()
											AutoHaki()
											Equipgui(_G.Select_gui)
											v.HumanoidRootPart.CanCollide = false
											v.HumanoidRootPart.Size = Vector3.new(50,50,50)
											topos(v.HumanoidRootPart.CFrame * MethodFarm)
											game:GetService'VirtualUser':CaptureController()
											game:GetService'VirtualUser':Button1Down(Vector2.new(1280, 672))
										until not _G.Auto_Soul_Reaper or not v.Parent or v.Humanoid.Health <= 0
									end
								end
							end
						end
					else
						if _G.Auto_Soul_Reaper_Hop then
							hop()
						else
							local args = {
								[1] = "Bones",
								[2] = "Buy",
								[3] = 1,
								[4] = 1
							}
							game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
						end
					end
				end)
			end
		end
	end)

	spawn(function()
		while wait() do
			if _G.Auto_Open_Dough_Dungeon then
				pcall(function()
					if game.Players.LocalPlayer.Backpack:FindFirstChild("God's Chalice") or game.Players.LocalPlayer.Character:FindFirstChild("God's Chalice") then
						if string.find(game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("SweetChaliceNpc"),"Where") then
							game.StarterGui:SetCore("SendNotification", {
								Title = "Notification", 
								Text = "Not Have Enough Material" ,
								Icon = "http://www.roblox.com/asset/?id=",
								Duration = 2.5
							})
						else
							game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("SweetChaliceNpc")
						end
					elseif game.Players.LocalPlayer.Backpack:FindFirstChild("Sweet Chalice") or game.Players.LocalPlayer.Character:FindFirstChild("Sweet Chalice") then
						if string.find(game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("CakePrinceSpawner"),"Do you want to open the portal now?") then
							game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("CakePrinceSpawner")
						else
							if game.Workspace.Enemies:FindFirstChild("Baking Staff [Lv. 2250]") or game.Workspace.Enemies:FindFirstChild("Head Baker [Lv. 2275]") or game.Workspace.Enemies:FindFirstChild("Cake Guard [Lv. 2225]") or game.Workspace.Enemies:FindFirstChild("Cookie Crafter [Lv. 2200]")  then
								for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do  
									if (v.Name == "Baking Staff [Lv. 2250]" or v.Name == "Head Baker [Lv. 2275]" or v.Name == "Cake Guard [Lv. 2225]" or v.Name == "Cookie Crafter [Lv. 2200]") and v.Humanoid.Health > 0 then
										repeat wait()
											AutoHaki()
											Equipgui(_G.Select_gui)
											StartCakeStartMagnet = true
											v.HumanoidRootPart.Size = Vector3.new(60, 60, 60)  
											POSCAKE = v.HumanoidRootPart.CFrame
											topos(v.HumanoidRootPart.CFrame * MethodFarm)
											game:GetService'VirtualUser':CaptureController()
											game:GetService'VirtualUser':Button1Down(Vector2.new(1280, 672))
										until _G.Auto_Open_Dough_Dungeon == false or game:GetService("ReplicatedStorage"):FindFirstChild("Cake Prince [Lv. 2300] [Raid Boss]") or not v.Parent or v.Humanoid.Health <= 0
									end
								end
							else
								StartCakeStartMagnet = false
								topos(CFrame.new(-1820.0634765625, 210.74781799316406, -12297.49609375))
							end
						end						
					elseif game.ReplicatedStorage:FindFirstChild("Dough King [Lv. 2300] [Raid Boss]") or game:GetService("Workspace").Enemies:FindFirstChild("Dough King [Lv. 2300] [Raid Boss]") then
						if game:GetService("Workspace").Enemies:FindFirstChild("Dough King [Lv. 2300] [Raid Boss]") then
							for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do 
								if v.Name == "Dough King [Lv. 2300] [Raid Boss]" then
									repeat wait()
										AutoHaki()
										Equipgui(_G.Select_gui)
										v.HumanoidRootPart.Size = Vector3.new(60, 60, 60)
										v.HumanoidRootPart.CanCollide = false
										topos(v.HumanoidRootPart.CFrame * MethodFarm)
										game:GetService'VirtualUser':CaptureController()
										game:GetService'VirtualUser':Button1Down(Vector2.new(1280, 672))
									until _G.Auto_Open_Dough_Dungeon == false or not v.Parent or v.Humanoid.Health <= 0
								end    
							end    
						else
							topos(CFrame.new(-2009.2802734375, 4532.97216796875, -14937.3076171875)) 
						end
					elseif game.Players.LocalPlayer.Backpack:FindFirstChild("Red Key") or game.Players.LocalPlayer.Character:FindFirstChild("Red Key") then
						local args = {
							[1] = "CakeScientist",
							[2] = "Check"
						}

						game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
					else
						if game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == true then
							if string.find(game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Container.QuestTitle.Title.Text,"Diablo") or string.find(game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Container.QuestTitle.Title.Text,"Deandre") or string.find(game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Container.QuestTitle.Title.Text,"Urban") then
								if game:GetService("Workspace").Enemies:FindFirstChild("Diablo [Lv. 1750]") or game:GetService("Workspace").Enemies:FindFirstChild("Deandre [Lv. 1750]") or game:GetService("Workspace").Enemies:FindFirstChild("Urban [Lv. 1750]") then
									for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
										if v.Name == "Diablo [Lv. 1750]" or v.Name == "Deandre [Lv. 1750]" or v.Name == "Urban [Lv. 1750]" then
											if v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
												repeat wait()
													AutoHaki()
													Equipgui(_G.Select_gui)
													v.HumanoidRootPart.CanCollide = false
													v.Humanoid.WalkSpeed = 0
													v.HumanoidRootPart.Size = Vector3.new(50,50,50)
													topos(v.HumanoidRootPart.CFrame * MethodFarm)
													game:GetService("VirtualUser"):CaptureController()
													game:GetService("VirtualUser"):Button1Down(Vector2.new(1280,672))
													sethiddenproperty(game:GetService("Players").LocalPlayer,"SimulationRadius",math.huge)
												until _G.Auto_Open_Dough_Dungeon == false or v.Humanoid.Health <= 0 or not v.Parent or game.Players.LocalPlayer.Backpack:FindFirstChild("God's Chalice") or game.Players.LocalPlayer.Character:FindFirstChild("God's Chalice")
											end
										end
									end
								else
									if game:GetService("ReplicatedStorage"):FindFirstChild("Diablo [Lv. 1750]") then
										topos(game:GetService("ReplicatedStorage"):FindFirstChild("Diablo [Lv. 1750]").HumanoidRootPart.CFrame * MethodFarm)
									elseif game:GetService("ReplicatedStorage"):FindFirstChild("Deandre [Lv. 1750]") then
										topos(game:GetService("ReplicatedStorage"):FindFirstChild("Deandre [Lv. 1750]").HumanoidRootPart.CFrame * MethodFarm)
									elseif game:GetService("ReplicatedStorage"):FindFirstChild("Urban [Lv. 1750]") then
										topos(game:GetService("ReplicatedStorage"):FindFirstChild("Urban [Lv. 1750]").HumanoidRootPart.CFrame * MethodFarm)
									end
								end                    
							end
						else
							wait(0.5)
							game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("EliteHunter")
						end
					end
				end)
			end
		end
	end)
	
		gui:Seperator(" Yama ")
	
	gui:Toggle("Auto Yama",_G.Auto_Yama,function(value)
	 _G.Auto_Yama = value
 	StopTween(_G.Auto_Yama)
end)


	spawn(function()
		while wait() do
			if _G.Auto_Yama then
				pcall(function()
					if game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("EliteHunter","Progress") >= 30 then
						fireclickdetector(game:GetService("Workspace").Map.Waterfall.SealedKatana.Handle.ClickDetector)
					end
				end)
			end
		end
	end)
	
		gui:Seperator(" Rainbow Haki ")
	
	gui:Toggle("Auto Rainbow Haki",_G.Auto_Rainbow_Haki,function(value)
 _G.Auto_Rainbow_Haki = value
StopTween(_G.Auto_Rainbow_Haki)
end)

	
	gui:Toggle("Auto Rainbow Haki Hop",_G.Auto_Rainbow_Haki_Hop,function(value)
 _G.Auto_Rainbow_Haki_Hop = value
StopTween(_G.Auto_Rainbow_Haki_Hop)
end)


	spawn(function()
		pcall(function()
			while wait() do
				if _G.Auto_Rainbow_Haki then
					if game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == false then
						game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("HornedMan","Bet")
					elseif game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == true and string.find(game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Container.QuestTitle.Title.Text, "Stone") then
						if _G.Auto_Rainbow_Haki and game.ReplicatedStorage:FindFirstChild("Stone [Lv. 1550] [Boss]") or game.Workspace.Enemies:FindFirstChild("Stone [Lv. 1550] [Boss]") then
							if game:GetService("Workspace").Enemies:FindFirstChild("Stone [Lv. 1550] [Boss]") then
								for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
									if v.Name == "Stone [Lv. 1550] [Boss]" then
										OldCFrameRainbow = v.HumanoidRootPart.CFrame
										repeat wait()
											AutoHaki()
											Equipgui(_G.Select_gui)
											topos(v.HumanoidRootPart.CFrame * MethodFarm)
											v.HumanoidRootPart.CanCollide = false
											v.HumanoidRootPart.CFrame = OldCFrameRainbow
											v.HumanoidRootPart.Size = Vector3.new(50,50,50)
											game:GetService'VirtualUser':CaptureController()
											game:GetService'VirtualUser':Button1Down(Vector2.new(1280, 672))
											sethiddenproperty(game:GetService("Players").LocalPlayer,"SimulationRadius",math.huge)
										until _G.Auto_Rainbow_Haki == false or v.Humanoid.Health <= 0 or not v.Parent or game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == false
									end
								end
							else
								topos(CFrame.new(-1086.11621, 38.8425903, 6768.71436, 0.0231462717, -0.592676699, 0.805107772, 2.03251839e-05, 0.805323839, 0.592835128, -0.999732077, -0.0137055516, 0.0186523199))
							end
						else
							if _G.Auto_Rainbow_Haki_Hop then
								hop()
							end
						end
					elseif game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == true and string.find(game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Container.QuestTitle.Title.Text, "Island Empress") then
						if _G.Auto_Rainbow_Haki and game.ReplicatedStorage:FindFirstChild("Island Empress [Lv. 1675] [Boss]") or game.Workspace.Enemies:FindFirstChild("Island Empress [Lv. 1675] [Boss]") then
							if game:GetService("Workspace").Enemies:FindFirstChild("Island Empress [Lv. 1675] [Boss]") then
								for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
									if v.Name == "Island Empress [Lv. 1675] [Boss]" then
										OldCFrameRainbow = v.HumanoidRootPart.CFrame
										repeat wait()
											AutoHaki()
											Equipgui(_G.Select_gui)
											topos(v.HumanoidRootPart.CFrame * MethodFarm)
											v.HumanoidRootPart.CanCollide = false
											v.HumanoidRootPart.CFrame = OldCFrameRainbow
											v.HumanoidRootPart.Size = Vector3.new(50,50,50)
											game:GetService'VirtualUser':CaptureController()
											game:GetService'VirtualUser':Button1Down(Vector2.new(1280, 672))
											sethiddenproperty(game:GetService("Players").LocalPlayer,"SimulationRadius",math.huge)
										until _G.Auto_Rainbow_Haki == false or v.Humanoid.Health <= 0 or not v.Parent or game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == false
									end
								end
							else
								topos(CFrame.new(5713.98877, 601.922974, 202.751251, -0.101080291, -0, -0.994878292, -0, 1, -0, 0.994878292, 0, -0.101080291))
							end
						else
							if _G.Auto_Rainbow_Haki_Hop then
								hop()
							end
						end
					elseif string.find(game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Container.QuestTitle.Title.Text, "Kilo Admiral") then
						if _G.Auto_Rainbow_Haki and game.ReplicatedStorage:FindFirstChild("Kilo Admiral [Lv. 1750] [Boss]") or game.Workspace.Enemies:FindFirstChild("Kilo Admiral [Lv. 1750] [Boss]") then
							if game:GetService("Workspace").Enemies:FindFirstChild("Kilo Admiral [Lv. 1750] [Boss]") then
								for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
									if v.Name == "Kilo Admiral [Lv. 1750] [Boss]" then
										OldCFrameRainbow = v.HumanoidRootPart.CFrame
										repeat wait()
											AutoHaki()
											Equipgui(_G.Select_gui)
											topos(v.HumanoidRootPart.CFrame * MethodFarm)
											v.HumanoidRootPart.CanCollide = false
											v.HumanoidRootPart.Size = Vector3.new(50,50,50)
											v.HumanoidRootPart.CFrame = OldCFrameRainbow
											game:GetService'VirtualUser':CaptureController()
											game:GetService'VirtualUser':Button1Down(Vector2.new(1280, 672))
											sethiddenproperty(game:GetService("Players").LocalPlayer,"SimulationRadius",math.huge)
										until _G.Auto_Rainbow_Haki == false or v.Humanoid.Health <= 0 or not v.Parent or game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == false
									end
								end
							else
								topos(CFrame.new(2877.61743, 423.558685, -7207.31006, -0.989591599, -0, -0.143904909, -0, 1.00000012, -0, 0.143904924, 0, -0.989591479))
							end
						else
							if _G.Auto_Rainbow_Haki_Hop then
								hop()
							end
						end
					elseif string.find(game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Container.QuestTitle.Title.Text, "Captain Elephant") then
						if _G.Auto_Rainbow_Haki and game.ReplicatedStorage:FindFirstChild("Captain Elephant [Lv. 1875] [Boss]") or game.Workspace.Enemies:FindFirstChild("Captain Elephant [Lv. 1875] [Boss]") then
							if game:GetService("Workspace").Enemies:FindFirstChild("Captain Elephant [Lv. 1875] [Boss]") then
								for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
									if v.Name == "Captain Elephant [Lv. 1875] [Boss]" then
										OldCFrameRainbow = v.HumanoidRootPart.CFrame
										repeat wait()
											AutoHaki()
											Equipgui(_G.Select_gui)
											topos(v.HumanoidRootPart.CFrame * MethodFarm)
											v.HumanoidRootPart.CanCollide = false
											v.HumanoidRootPart.Size = Vector3.new(50,50,50)
											v.HumanoidRootPart.CFrame = OldCFrameRainbow
											game:GetService'VirtualUser':CaptureController()
											game:GetService'VirtualUser':Button1Down(Vector2.new(1280, 672))
											sethiddenproperty(game:GetService("Players").LocalPlayer,"SimulationRadius",math.huge)
										until _G.Auto_Rainbow_Haki == false or v.Humanoid.Health <= 0 or not v.Parent or game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == false
									end
								end
							else
								topos(CFrame.new(-13485.0283, 331.709259, -8012.4873, 0.714521289, 7.98849911e-08, 0.69961375, -1.02065748e-07, 1, -9.94383065e-09, -0.69961375, -6.43015241e-08, 0.714521289))
							end
						else 
							if _G.Auto_Rainbow_Haki_Hop then
								hop()
							end
						end
					elseif string.find(game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Container.QuestTitle.Title.Text, "Beautiful Pirate") then
						if _G.Auto_Rainbow_Haki and game.ReplicatedStorage:FindFirstChild("Beautiful Pirate [Lv. 1950] [Boss]") or game.Workspace.Enemies:FindFirstChild("Beautiful Pirate [Lv. 1950] [Boss]") then
							if game:GetService("Workspace").Enemies:FindFirstChild("Beautiful Pirate [Lv. 1950] [Boss]") then
								for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
									if v.Name == "Beautiful Pirate [Lv. 1950] [Boss]" then
										OldCFrameRainbow = v.HumanoidRootPart.CFrame
										repeat wait()
											AutoHaki()
											Equipgui(_G.Select_gui)
											topos(v.HumanoidRootPart.CFrame * MethodFarm)
											v.HumanoidRootPart.CanCollide = false
											v.HumanoidRootPart.Size = Vector3.new(50,50,50)
											v.HumanoidRootPart.CFrame = OldCFrameRainbow
											game:GetService'VirtualUser':CaptureController()
											game:GetService'VirtualUser':Button1Down(Vector2.new(1280, 672))
											sethiddenproperty(game:GetService("Players").LocalPlayer,"SimulationRadius",math.huge)
										until _G.Auto_Rainbow_Haki == false or v.Humanoid.Health <= 0 or not v.Parent or game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == false
									end
								end
							else
								topos(CFrame.new(5312.3598632813, 20.141201019287, -10.158538818359))
							end
						else 
							if _G.Auto_Rainbow_Haki_Hop then
								hop()
							end
						end
					else
						game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("HornedMan","Bet")
					end
				end
			end
		end)
	end)
	
		gui:Seperator(" Canvander ")

	gui:Toggle("Auto Canvander",_G.Auto_Canvander,function(value)
 _G.Auto_Canvander = value
StopTween(_G.Auto_Canvander)
end)

	
	gui:Toggle("Auto Canvander Hop",_G.Auto_Canvander_Hop,function(value)
 _G.Auto_Canvander_Hop = value
StopTween(_G.Auto_Canvander_Hop)
end)


	spawn(function()
		while wait() do
			if _G.Auto_Canvander then
				pcall(function()
					if _G.Auto_Canvander and game.ReplicatedStorage:FindFirstChild("Beautiful Pirate [Lv. 1950] [Boss]") or game.Workspace.Enemies:FindFirstChild("Beautiful Pirate [Lv. 1950] [Boss]") then
						if game.Workspace.Enemies:FindFirstChild("Beautiful Pirate [Lv. 1950] [Boss]") then
							for i,v in pairs(game.Workspace.Enemies:GetChildren()) do
								if v.Name == "Beautiful Pirate [Lv. 1950] [Boss]" and v:FindFirstChild("HumanoidRootPart") and v:FindFirstChild("Humanoid") and v.Humanoid.Health > 0 then
									repeat wait()
										AutoHaki()
										Equipgui(_G.Select_gui)
										topos(v.HumanoidRootPart.CFrame * MethodFarm)
										game:GetService'VirtualUser':CaptureController()
										game:GetService'VirtualUser':Button1Down(Vector2.new(1280, 672))
									until _G.Auto_Canvander or v.Humanoid.Health <= 0 or not v.Parent
								end
							end
						else
							topos(CFrame.new(5240.40869140625, 22.536449432373047, 17.463970184326172))
						end
					else
						if _G.Auto_Canvander_Hop then
							hop()
						end
					end
				end)
			end
		end
	end)
	
		gui:Seperator(" Twin Hook ")
	
	gui:Toggle("Auto Twin Hook",_G.Auto_Twin_Hook,function(value)
 _G.Auto_Twin_Hook = value
StopTween(_G.Auto_Twin_Hook)
end)

	
	gui:Toggle("Auto Twin Hook Hop",_G.Auto_Twin_Hook_Hop,function(value)
 _G.Auto_Twin_Hook_Hop = value
StopTween(_G.Auto_Twin_Hook_Hop)
end)


	spawn(function()
		while wait() do
			if _G.Auto_Twin_Hook then
				pcall(function()
					if _G.Auto_Twin_Hook and game.ReplicatedStorage:FindFirstChild("Captain Elephant [Lv. 1875] [Boss]") or game.Workspace.Enemies:FindFirstChild("Captain Elephant [Lv. 1875] [Boss]") then
						if game.Workspace.Enemies:FindFirstChild("Captain Elephant [Lv. 1875] [Boss]") then
							for i,v in pairs(game.Workspace.Enemies:GetChildren()) do
								if v.Name == "Captain Elephant [Lv. 1875] [Boss]" and v:FindFirstChild("HumanoidRootPart") and v:FindFirstChild("Humanoid") and v.Humanoid.Health > 0 then
									repeat wait()
										AutoHaki()
										Equipgui(_G.Select_gui)
										topos(v.HumanoidRootPart.CFrame * MethodFarm)
										game:GetService'VirtualUser':CaptureController()
										game:GetService'VirtualUser':Button1Down(Vector2.new(1280, 672))
									until _G.Auto_Twin_Hook or v.Humanoid.Health <= 0 or not v.Parent
								end
							end
						else
							topos(CFrame.new(-13348.0654296875, 405.8904113769531, -8570.62890625))
						end
					else
						if _G.Auto_Twin_Hook_Hop then
							hop()
						end
					end
				end)
			end
		end
	end)
	
		gui:Seperator(" Serpent Bow ")

gui:Toggle("Auto Serpent Bow",_G.Auto_Serpent_Bow,function(value)
 _G.Auto_Serpent_Bow = value
StopTween(_G.Auto_Serpent_Bow)
end)

	
	gui:Toggle("Auto Serpent Bow Hop",_G.Auto_Serpent_Bow_Hop,function(value)
 _G.Auto_Serpent_Bow_Hop = value
StopTween(_G.Auto_Serpent_Bow_Hop)
end)


	spawn(function()
		while wait() do
			if _G.Auto_Serpent_Bow then
				pcall(function()
					if _G.Auto_Serpent_Bow and game.ReplicatedStorage:FindFirstChild("Island Empress [Lv. 1675] [Boss]") or game.Workspace.Enemies:FindFirstChild("Island Empress [Lv. 1675] [Boss]") then
						if game.Workspace.Enemies:FindFirstChild("Island Empress [Lv. 1675] [Boss]") then
							for i,v in pairs(game.Workspace.Enemies:GetChildren()) do
								if v.Name == "Island Empress [Lv. 1675] [Boss]" and v:FindFirstChild("HumanoidRootPart") and v:FindFirstChild("Humanoid") and v.Humanoid.Health > 0 then
									repeat wait()
										AutoHaki()
										Equipgui(_G.Select_gui)
										topos(v.HumanoidRootPart.CFrame * MethodFarm)
										game:GetService'VirtualUser':CaptureController()
										game:GetService'VirtualUser':Button1Down(Vector2.new(1280, 672))
									until _G.Auto_Serpent_Bow or v.Humanoid.Health <= 0 or not v.Parent
								end
							end
						else
							topos(CFrame.new(5764.1826171875, 700.425537109375, 141.11996459960938))
						end
					else
						if _G.Auto_Serpent_Bow_Hop then
							hop()
						end
					end
				end)
			end
		end
	end)

gui:Seperator(" Tushita ")

gui:Toggle("Auto Tushita Sword",_G.Autotushita,function(value)
 _G.Autotushita = value
	end)
	
	
spawn(function()
		while wait() do
					if _G.Autotushita then
						if game:GetService("Workspace").Enemies:FindFirstChild("Longma [Lv. 2000] [Boss]") then
							for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
								if v.Name == ("Longma [Lv. 2000] [Boss]" or v.Name == "Longma [Lv. 2000] [Boss]") and v.Humanoid.Health > 0 and v:IsA("Model") and v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") then
									repeat wait()
										StartMagnet = true
										AutoHaki()
										if not game.Players.LocalPlayer.Character:FindFirstChild(_G.Select_gui) then
											wait()
											Equipgui(_G.Select_gui)
										end
										PosMon = v.HumanoidRootPart.CFrame
											game:GetService'VirtualUser':CaptureController()
											game:GetService'VirtualUser':Button1Down(Vector2.new(1280, 672))
										v.HumanoidRootPart.Size = Vector3.new(60,60,60)
										v.Humanoid.JumpPower = 0
										v.Humanoid.WalkSpeed = 0
										v.HumanoidRootPart.CanCollide = false
										v.Humanoid:ChangeState(11)
										topos(v.HumanoidRootPart.CFrame * MethodFarm)
									until not _G.Autotushita or not v.Parent or v.Humanoid.Health <= 0
									StartMagnet = false
								end
							end
						else
							topos(CFrame.new(-10238.875976563, 389.7912902832, -9549.7939453125))
						end
					end
				end
		end)

gui:Toggle("Auto Holy Torch",_G.Auto_Holy_Torch,function(value)
 _G.Auto_Holy_Torch = value
StopTween(_G.Auto_Holy_Torch)
end)
end

if World3 then

gui:Seperator(" Observation Haki V2 ")

gui:Toggle("Auto Observation Haki V2",_G.AutoObservationHakiV2,function(x)
		_G.AutoObservationHakiV2 = x
	end)

	spawn(function()
		while wait() do
			if _G.AutoObservationHakiV2 then
				if game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == false then
					repeat 
						topos(CFrame.new(-12444.78515625, 332.40396118164, -7673.1806640625)) 
						wait() 
					until _G.StopTween == true or not _G.AutoObservationHakiV2 or (game.Players.LocalPlayer.Character.HumanoidRootPart.Position-Vector3.new(-12444.78515625, 332.40396118164, -7673.1806640625)).Magnitude <= 10
					wait(.5)
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("CitizenQuestProgress","Citizen")
					wait(1)
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("StartQuest","CitizenQuest",1)
				else
					if string.find(game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Container.QuestTitle.Title.Text,"Defeat 50 Forest Pirates") then
						if game:GetService("Workspace").Enemies:FindFirstChild("Forest Pirate [Lv. 1825]") then
							for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
								if v.Name == "Forest Pirate [Lv. 1825]" then
									repeat wait()
										if not game.Players.LocalPlayer.Character:FindFirstChild("HasBuso") then
											game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("Buso")
										end
										Equipgui(_G.Select_gui)
										topos(v.HumanoidRootPart.CFrame * CFrame.new(1,20,1))
										PosHee =  v.HumanoidRootPart.CFrame
										if sethiddenproperty then
											sethiddenproperty(game.Players.LocalPlayer, "SimulationRadius", math.huge)
										end
										v.HumanoidRootPart.CFrame = v.HumanoidRootPart.CFrame
										v.HumanoidRootPart.CanCollide = false
										v.HumanoidRootPart.Size = Vector3.new(50,50,50)
										game:GetService'VirtualUser':CaptureController()
										game:GetService'VirtualUser':Button1Down(Vector2.new(1280, 672))
										StatrMagnet = true
									until _G.AutoObservationHakiV2 == false or v.Humanoid.Health <= 0
									StatrMagnet = false
								end
							end
						else
							repeat 
								topos(CFrame.new(-13277.568359375, 370.34185791016, -7821.1572265625)) 
								wait() 
							until _G.StopTween == true or not _G.AutoObservationHakiV2 or (game.Players.LocalPlayer.Character.HumanoidRootPart.Position-Vector3.new(-13277.568359375, 370.34185791016, -7821.1572265625)).Magnitude <= 10
						end
					elseif game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Container.QuestTitle.Title.Text ==  "Defeat  Captain Elephant (0/1)" then 
						if game:GetService("Workspace").Enemies:FindFirstChild("Captain Elephant [Lv. 1875] [Boss]") then
							for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
								if v.Name == "Captain Elephant [Lv. 1875] [Boss]" then
									repeat wait()
										if not game.Players.LocalPlayer.Character:FindFirstChild("HasBuso") then
											game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("Buso")
										end
										Equipgui(_G.Select_gui)
										topos(v.HumanoidRootPart.CFrame * CFrame.new(1,20,1))										
										if sethiddenproperty then
											sethiddenproperty(game.Players.LocalPlayer, "SimulationRadius", math.huge)
										end
										v.HumanoidRootPart.CFrame = v.HumanoidRootPart.CFrame
										v.HumanoidRootPart.CanCollide = false
										v.HumanoidRootPart.Size = Vector3.new(50,50,50)
										game:GetService'VirtualUser':CaptureController()
										game:GetService'VirtualUser':Button1Down(Vector2.new(1280, 672))
									until _G.AutoObservationHakiV2 == false or v.Humanoid.Health <= 0
								end
							end
						else
							repeat 
								topos(CFrame.new(-13493.12890625, 318.89553833008, -8373.7919921875)) 
								wait() 
							until _G.StopTween == true or not _G.AutoObservationHakiV2 or (game.Players.LocalPlayer.Character.HumanoidRootPart.Position-Vector3.new(-13493.12890625, 318.89553833008, -8373.7919921875)).Magnitude <= 10
						end        
					end
				end
				if game.Players.LocalPlayer.Backpack:FindFirstChild("Banana") and  game.Players.LocalPlayer.Backpack:FindFirstChild("Apple") and game.Players.LocalPlayer.Backpack:FindFirstChild("Pineapple") then
					repeat 
						topos(CFrame.new(-12444.78515625, 332.40396118164, -7673.1806640625)) 
						wait() 
					until _G.StopTween == true or not _G.AutoObservationHakiV2 or (game.Players.LocalPlayer.Character.HumanoidRootPart.Position-Vector3.new(-12444.78515625, 332.40396118164, -7673.1806640625)).Magnitude <= 10
					wait(.5)
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("CitizenQuestProgress","Citizen")
				elseif game.Players.LocalPlayer.Backpack:FindFirstChild("Fruit Bowl") or game.Players.LocalPlayer.Character:FindFirstChild("Fruit Bowl") then
					repeat 
						topos(CFrame.new(-10920.125, 624.20275878906, -10266.995117188)) 
						wait() 
					until _G.StopTween == true or not _G.AutoObservationHakiV2 or (game.Players.LocalPlayer.Character.HumanoidRootPart.Position-Vector3.new(-10920.125, 624.20275878906, -10266.995117188)).Magnitude <= 10
					wait(.5)
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("KenTalk2","Start")
					wait(1)
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("KenTalk2","Buy")
				else
					for i,v in pairs(game.Workspace:GetDescendants()) do
						if v.Name == "Apple" or v.Name == "Banana" or v.Name == "Pineapple" then
							v.Handle.CFrame = game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame * CFrame.new(0,1,10)
							wait()
							firetouchinterest(game.Players.LocalPlayer.Character.HumanoidRootPart,v.Handle,0)    
							wait()
						end
					end   
				end
			end
		end
	end)

	spawn(function()
		while wait() do
			pcall(function()
				if _G.AutoObservationHakiV2 then
					if sethiddenproperty then
						sethiddenproperty(game.Players.LocalPlayer, "SimulationRadius", math.huge)
					end
				end
			end)
			game:GetService("RunService").Heartbeat:Wait()
		end
	end)

	spawn(function()
		game:GetService("RunService").Heartbeat:connect(function()
			pcall(function()
				if _G.AutoObservationHakiV2 then
					if game:GetService("Players").LocalPlayer.Character:FindFirstChild("Humanoid") then
						game:GetService("Players").LocalPlayer.Character.Humanoid:ChangeState(11)
					end
				end
			end)
		end)
	end)

	spawn(function()
		pcall(function()
			game:GetService("RunService").Heartbeat:Connect(function()
				game:GetService("RunService").Heartbeat:Wait()
				if _G.AutoObservationHakiV2 and StatrMagnet then
					for i,v in pairs(game.Workspace.Enemies:GetChildren()) do
						if v.Name == "Forest Pirate [Lv. 1825]" and v:FindFirstChild("Humanoid") and v.Humanoid.Health > 0 then
							if v.Name == "Forest Pirate [Lv. 1825]" then
								v.HumanoidRootPart.CanCollide = false
								v.HumanoidRootPart.Size = Vector3.new(50, 50, 50)
								v.HumanoidRootPart.CFrame = PosHee
							end
						end
					end
				end
			end)
		end)
	end)

	spawn(function()
		game:GetService("RunService").Heartbeat:connect(function()
			game:GetService("RunService").Heartbeat:Wait()
			pcall(function()
				if _G.AutoObservationHakiV2 and StatrMagnet then
					CheckQuest()
					for i,v in pairs(game.Workspace.Enemies:GetChildren()) do
						if v.Name == Ms then
							v.Humanoid:ChangeState(11)
						end
					end
				end
			end)
			game:GetService("RunService").Heartbeat:Wait()
		end)
	end)

	spawn(function()
		while wait() do
			pcall(function()
				if _G.AutoObservationHakiV2 and StatrMagnet then
					for i,v in pairs(game.Workspace.Enemies:GetChildren()) do
						if v.Name == Ms and v:FindFirstChild("HumanoidRootPart") then
							if not v.HumanoidRootPart:FindFirstChild("BringEE") then
								local bv = Instance.new("BodyVelocity")
								bv.Parent = v.HumanoidRootPart
								bv.Name = "BringEE"
								bv.MaxForce = Vector3.new(100000,100000,100000)
								bv.Velocity = Vector3.new(0,0,0)
							end
						end
					end
				end
			end)
			wait()
		end
	end)
	end

	spawn(function()
		game:GetService("RunService").Heartbeat:Connect(function()
			pcall(function()
				for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
					if _G.Auto_Bartilo_Quest and AutoBartiloBring and v.Name == "Swan Pirate [Lv. 775]" and (v.HumanoidRootPart.Position - PosMonBarto.Position).magnitude <= 350 then
						v.HumanoidRootPart.CFrame = PosMonBarto
						v.HumanoidRootPart.CanCollide = false
						v.HumanoidRootPart.Size = Vector3.new(50,50,50)
						if v.Humanoid:FindFirstChild("Animator") then
							v.Humanoid.Animator:Destroy()
						end
						sethiddenproperty(game.Players.LocalPlayer, "SimulationRadius",  math.huge)
					end
				end
			end)
		end)
	end)

	spawn(function()
		pcall(function()
			while wait() do
				if _G.Auto_Bartilo_Quest then
					if game:GetService("Players").LocalPlayer.Data.Level.Value >= 800 and game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BartiloQuestProgress","Bartilo") == 0 then
						if string.find(game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Container.QuestTitle.Title.Text, "Swan Pirates") and string.find(game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Container.QuestTitle.Title.Text, "50") and game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == true then 
							if game:GetService("Workspace").Enemies:FindFirstChild("Swan Pirate [Lv. 775]") then
								for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
									if v.Name == "Swan Pirate [Lv. 775]" then
										pcall(function()
											repeat wait()
												AutoHaki()
												Equipgui(_G.Select_gui)
												v.HumanoidRootPart.Transparency = 1
												v.HumanoidRootPart.CanCollide = false
												v.HumanoidRootPart.Size = Vector3.new(50,50,50)
												topos(v.HumanoidRootPart.CFrame * MethodFarm)													
												PosMonBarto =  v.HumanoidRootPart.CFrame
												game:GetService'VirtualUser':CaptureController()
												game:GetService'VirtualUser':Button1Down(Vector2.new(1280, 672))
												AutoBartiloBring = true
											until not v.Parent or v.Humanoid.Health <= 0 or _G.Auto_Bartilo_Quest == false or game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == false
											AutoBartiloBring = false
										end)
									end
								end
							else
								repeat topos(CFrame.new(932.624451, 156.106079, 1180.27466, -0.973085582, 4.55137119e-08, -0.230443969, 2.67024713e-08, 1, 8.47491108e-08, 0.230443969, 7.63147128e-08, -0.973085582)) wait() until not _G.Auto_Bartilo_Quest or (game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position-Vector3.new(932.624451, 156.106079, 1180.27466, -0.973085582, 4.55137119e-08, -0.230443969, 2.67024713e-08, 1, 8.47491108e-08, 0.230443969, 7.63147128e-08, -0.973085582)).Magnitude <= 10
							end
						else
							repeat topos(CFrame.new(-456.28952, 73.0200958, 299.895966)) wait() until not _G.Auto_Bartilo_Quest or (game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position-Vector3.new(-456.28952, 73.0200958, 299.895966)).Magnitude <= 10
							wait(1.1)
							game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("StartQuest","BartiloQuest",1)
						end 
					elseif game:GetService("Players").LocalPlayer.Data.Level.Value >= 800 and game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BartiloQuestProgress","Bartilo") == 1 then
						if game:GetService("Workspace").Enemies:FindFirstChild("Jeremy [Lv. 850] [Boss]") then
							for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
								if v.Name == "Jeremy [Lv. 850] [Boss]" then
									OldCFrameBartlio = v.HumanoidRootPart.CFrame
									repeat wait()
										sethiddenproperty(game:GetService("Players").LocalPlayer, "SimulationRadius", math.huge)
										AutoHaki()
										Equipgui(_G.Select_gui)
										v.HumanoidRootPart.Transparency = 1
										v.HumanoidRootPart.CanCollide = false
										v.HumanoidRootPart.Size = Vector3.new(50,50,50)
										v.HumanoidRootPart.CFrame = OldCFrameBartlio
										topos(v.HumanoidRootPart.CFrame * MethodFarm)
										game:GetService'VirtualUser':CaptureController()
										game:GetService'VirtualUser':Button1Down(Vector2.new(1280, 672))
										sethiddenproperty(game:GetService("Players").LocalPlayer,"SimulationRadius",math.huge)
									until not v.Parent or v.Humanoid.Health <= 0 or _G.Auto_Bartilo_Quest == false
								end
							end
						elseif game:GetService("ReplicatedStorage"):FindFirstChild("Jeremy [Lv. 850] [Boss]") then
							repeat topos(CFrame.new(-456.28952, 73.0200958, 299.895966)) wait() until not _G.Auto_Bartilo_Quest or (game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position-Vector3.new(-456.28952, 73.0200958, 299.895966)).Magnitude <= 10
							wait(1.1)
							game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BartiloQuestProgress","Bartilo")
							wait(1)
							repeat topos(CFrame.new(2099.88159, 448.931, 648.997375)) wait() until not _G.Auto_Bartilo_Quest or (game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position-Vector3.new(2099.88159, 448.931, 648.997375)).Magnitude <= 10
							wait(2)
						else
							repeat topos(CFrame.new(2099.88159, 448.931, 648.997375)) wait() until not _G.Auto_Bartilo_Quest or (game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position-Vector3.new(2099.88159, 448.931, 648.997375)).Magnitude <= 10
						end
					elseif game:GetService("Players").LocalPlayer.Data.Level.Value >= 800 and game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BartiloQuestProgress","Bartilo") == 2 then
						repeat topos(CFrame.new(-1850.49329, 13.1789551, 1750.89685)) wait() until not _G.Auto_Bartilo_Quest or (game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position-Vector3.new(-1850.49329, 13.1789551, 1750.89685)).Magnitude <= 10
						wait(1)
						repeat topos(CFrame.new(-1858.87305, 19.3777466, 1712.01807)) wait() until not _G.Auto_Bartilo_Quest or (game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position-Vector3.new(-1858.87305, 19.3777466, 1712.01807)).Magnitude <= 10
						wait(1)
						repeat topos(CFrame.new(-1803.94324, 16.5789185, 1750.89685)) wait() until not _G.Auto_Bartilo_Quest or (game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position-Vector3.new(-1803.94324, 16.5789185, 1750.89685)).Magnitude <= 10
						wait(1)
						repeat topos(CFrame.new(-1858.55835, 16.8604317, 1724.79541)) wait() until not _G.Auto_Bartilo_Quest or (game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position-Vector3.new(-1858.55835, 16.8604317, 1724.79541)).Magnitude <= 10
						wait(1)
						repeat topos(CFrame.new(-1869.54224, 15.987854, 1681.00659)) wait() until not _G.Auto_Bartilo_Quest or (game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position-Vector3.new(-1869.54224, 15.987854, 1681.00659)).Magnitude <= 10
						wait(1)
						repeat topos(CFrame.new(-1800.0979, 16.4978027, 1684.52368)) wait() until not _G.Auto_Bartilo_Quest or (game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position-Vector3.new(-1800.0979, 16.4978027, 1684.52368)).Magnitude <= 10
						wait(1)
						repeat topos(CFrame.new(-1819.26343, 14.795166, 1717.90625)) wait() until not _G.Auto_Bartilo_Quest or (game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position-Vector3.new(-1819.26343, 14.795166, 1717.90625)).Magnitude <= 10
						wait(1)
						repeat topos(CFrame.new(-1813.51843, 14.8604736, 1724.79541)) wait() until not _G.Auto_Bartilo_Quest or (game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position-Vector3.new(-1813.51843, 14.8604736, 1724.79541)).Magnitude <= 10
					end
				end 
			end
		end)
	end)

if World3 then

gui:Seperator(" Musketeer Hat ")

gui:Toggle("Auto Musketeer Hat",_G.Auto_Musketeer_Hat,function(value)
 _G.Auto_Musketeer_Hat = value
StopTween(_G.Auto_Musketeer_Hat)
end)
	

	spawn(function()
		game:GetService("RunService").Heartbeat:Connect(function()
			pcall(function()
				for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
					if _G.Auto_Musketeer_Hat and StartMagnetMusketeerhat and v.Name == "Forest Pirate [Lv. 1825]" and (v.HumanoidRootPart.Position - MusketeerHatMon.Position).magnitude <= 350 then
						v.HumanoidRootPart.CFrame = MusketeerHatMon
						v.HumanoidRootPart.CanCollide = false
						v.HumanoidRootPart.Size = Vector3.new(50,50,50)
						if v.Humanoid:FindFirstChild("Animator") then
							v.Humanoid.Animator:Destroy()
						end
						sethiddenproperty(game.Players.LocalPlayer, "SimulationRadius",  math.huge)
					end
				end
			end)
		end)
	end)

	spawn(function()
		pcall(function()
			while wait() do
				if _G.Auto_Musketeer_Hat then
					if game:GetService("Players").LocalPlayer.Data.Level.Value >= 1800 and game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("CitizenQuestProgress").KilledBandits == false then
						if string.find(game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Container.QuestTitle.Title.Text, "Forest Pirate") and string.find(game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Container.QuestTitle.Title.Text, "50") and game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == true then
							if game:GetService("Workspace").Enemies:FindFirstChild("Forest Pirate [Lv. 1825]") then
								for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
									if v.Name == "Forest Pirate [Lv. 1825]" then
										repeat wait()
											pcall(function()
												AutoHaki()
												Equipgui(_G.Select_gui)
												v.HumanoidRootPart.Size = Vector3.new(50,50,50)
												topos(v.HumanoidRootPart.CFrame * MethodFarm)
												v.HumanoidRootPart.CanCollide = false
												game:GetService'VirtualUser':CaptureController()
												game:GetService'VirtualUser':Button1Down(Vector2.new(1280, 672))
												MusketeerHatMon = v.HumanoidRootPart.CFrame
												StartMagnetMusketeerhat = true
											end)
										until _G.Auto_Musketeer_Hat == false or not v.Parent or v.Humanoid.Health <= 0 or game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == false
										StartMagnetMusketeerhat = false
									end
								end
							else
								StartMagnetMusketeerhat = false
								topos(CFrame.new(-13206.452148438, 425.89199829102, -7964.5537109375))
							end
						else
							topos(CFrame.new(-12443.8671875, 332.40396118164, -7675.4892578125))
							if (Vector3.new(-12443.8671875, 332.40396118164, -7675.4892578125) - game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 30 then
								wait(1.5)
								game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("StartQuest","CitizenQuest",1)
							end
						end
					elseif game:GetService("Players").LocalPlayer.Data.Level.Value >= 1800 and game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("CitizenQuestProgress").KilledBoss == false then
						if game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible and string.find(game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Container.QuestTitle.Title.Text, "Captain Elephant") and game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == true then
							if game:GetService("Workspace").Enemies:FindFirstChild("Captain Elephant [Lv. 1875] [Boss]") then
								for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
									if v.Name == "Captain Elephant [Lv. 1875] [Boss]" then
										OldCFrameElephant = v.HumanoidRootPart.CFrame
										repeat wait()
											pcall(function()
												AutoHaki()
												Equipgui(_G.Select_gui)
												v.HumanoidRootPart.CanCollide = false
												v.HumanoidRootPart.Size = Vector3.new(50,50,50)
												topos(v.HumanoidRootPart.CFrame * MethodFarm)
												v.HumanoidRootPart.CanCollide = false
												v.HumanoidRootPart.CFrame = OldCFrameElephant
												game:GetService'VirtualUser':CaptureController()
												game:GetService'VirtualUser':Button1Down(Vector2.new(1280, 672))
												sethiddenproperty(game:GetService("Players").LocalPlayer,"SimulationRadius",math.huge)
											end)
										until _G.Auto_Musketeer_Hat == false or v.Humanoid.Health <= 0 or not v.Parent or game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == false
									end
								end
							else
								topos(CFrame.new(-13374.889648438, 421.27752685547, -8225.208984375))
							end
						else
							topos(CFrame.new(-12443.8671875, 332.40396118164, -7675.4892578125))
							if (CFrame.new(-12443.8671875, 332.40396118164, -7675.4892578125).Position - game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 4 then
								wait(1.5)
								game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("CitizenQuestProgress","Citizen")
							end
						end
					elseif game:GetService("Players").LocalPlayer.Data.Level.Value >= 1800 and game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("CitizenQuestProgress","Citizen") == 2 then
						topos(CFrame.new(-12512.138671875, 340.39279174805, -9872.8203125))
					end
				end
			end
		end)
	end)


	spawn(function()
		while wait() do
			if _G.Auto_Holy_Torch then
				pcall(function()
					wait(1)
					repeat topos(CFrame.new(-10752, 417, -9366)) wait() until not _G.Auto_Holy_Torch or (game.Players.LocalPlayer.Character.HumanoidRootPart.Position-Vector3.new(-10752, 417, -9366)).Magnitude <= 10
					wait(1)
					repeat topos(CFrame.new(-11672, 334, -9474)) wait() until not _G.Auto_Holy_Torch or (game.Players.LocalPlayer.Character.HumanoidRootPart.Position-Vector3.new(-11672, 334, -9474)).Magnitude <= 10
					wait(1)
					repeat topos(CFrame.new(-12132, 521, -10655)) wait() until not _G.Auto_Holy_Torch or (game.Players.LocalPlayer.Character.HumanoidRootPart.Position-Vector3.new(-12132, 521, -10655)).Magnitude <= 10
					wait(1)
					repeat topos(CFrame.new(-13336, 486, -6985)) wait() until not _G.Auto_Holy_Torch or (game.Players.LocalPlayer.Character.HumanoidRootPart.Position-Vector3.new(-13336, 486, -6985)).Magnitude <= 10
					wait(1)
					repeat topos(CFrame.new(-13489, 332, -7925)) wait() until not _G.Auto_Holy_Torch or (game.Players.LocalPlayer.Character.HumanoidRootPart.Position-Vector3.new(-13489, 332, -7925)).Magnitude <= 10
				end)
			end
		end
	end)
end

if World2 then

	gui:Seperator(" Superhuman ")
	
gui:Toggle("Auto Superhuman",_G.Auto_Superhuman,function(value)
 _G.Auto_Superhuman = value
end)


gui:Toggle("Auto Fully Superhuman",_G.Auto_Fully_Superhuman,function(value)
 _G.Auto_Fully_Superhuman = value
end)


spawn(function()
    while wait(.25) do
        if _G.Auto_Superhuman or _G.Auto_Fully_Superhuman and game.Players.LocalPlayer:FindFirstChild("guiAssetCache") then 
			pcall(function()
				if game:GetService("Players").LocalPlayer.Data.Beli.Value >= 500000 and (game.Players.LocalPlayer.Character:FindFirstChild("Combat") or game.Players.LocalPlayer.Backpack:FindFirstChild("Combat")) then
					_G.Select_gui = "Combat"
					local args = {
						[1] = "BuyElectro"
					}
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
				end   
				if game.Players.LocalPlayer.Character:FindFirstChild("Superhuman") or game.Players.LocalPlayer.Backpack:FindFirstChild("Superhuman") then
					_G.Select_gui = "Superhuman"
				end  
				if game.Players.LocalPlayer.Backpack:FindFirstChild("Black Leg") and game.Players.LocalPlayer.Backpack:FindFirstChild("Black Leg").Level.Value <= 299  then
					_G.Select_gui = "Black Leg"
				end
				if game.Players.LocalPlayer.Backpack:FindFirstChild("Electro") and game.Players.LocalPlayer.Backpack:FindFirstChild("Electro").Level.Value <= 299  then
					_G.Select_gui = "Electro"
				end
				if game.Players.LocalPlayer.Backpack:FindFirstChild("Fishman Karate") and game.Players.LocalPlayer.Backpack:FindFirstChild("Fishman Karate").Level.Value <= 299  then
					_G.Select_gui = "Fishman Karate"
				end
				if game.Players.LocalPlayer.Backpack:FindFirstChild("Dragon Claw") and game.Players.LocalPlayer.Backpack:FindFirstChild("Dragon Claw").Level.Value <= 299  then
					_G.Select_gui = "Dragon Claw"
				end
				if game.Players.LocalPlayer.Backpack:FindFirstChild("Black Leg") and game.Players.LocalPlayer.Backpack:FindFirstChild("Black Leg").Level.Value >= 300  then
					local args = {
						[1] = "BuyFishmanKarate"
					}
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
				end
				if game.Players.LocalPlayer.Character:FindFirstChild("Black Leg") and game.Players.LocalPlayer.Character:FindFirstChild("Black Leg").Level.Value >= 300  then
					local args = {
						[1] = "BuyFishmanKarate"
					}
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
				end
				if game.Players.LocalPlayer.Character:FindFirstChild("Electro") and game.Players.LocalPlayer.Character:FindFirstChild("Electro").Level.Value >= 300  then
					local args = {
						[1] = "BuyBlackLeg"
					}
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
				end
				if game.Players.LocalPlayer.Backpack:FindFirstChild("Fishman Karate") and game.Players.LocalPlayer.Backpack:FindFirstChild("Fishman Karate").Level.Value >= 300  then
					if _G.Auto_Fully_Superhuman and game.Players.LocalPlayer.Data.Fragments.Value < 1500 then
						if game.Players.LocalPlayer.Data.Level.Value > 1100 then
							_G.Select_Dungeon = "Flame"
							_G.Auto_Buy_Chips_Dungeon = true
							_G.Auto_Start_Dungeon = true
							_G.Auto_Next_Island = true
							_G.Kill_Aura = true
						end
					else
						_G.Auto_Buy_Chips_Dungeon = false
						_G.Auto_Start_Dungeon = false
						_G.Auto_Next_Island = false
						_G.Kill_Aura = false
						local args = {
							[1] = "BlackbeardReward",
							[2] = "DragonClaw",
							[3] = "2"
						}
						game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
					end
				end
				if game.Players.LocalPlayer.Character:FindFirstChild("Fishman Karate") and game.Players.LocalPlayer.Character:FindFirstChild("Fishman Karate").Level.Value >= 300  then
					if _G.Auto_Fully_Superhuman and game.Players.LocalPlayer.Data.Fragments.Value < 1500 then
						if game.Players.LocalPlayer.Data.Level.Value > 1100 then
							_G.Select_Dungeon = "Flame"
							_G.Auto_Buy_Chips_Dungeon = true
							_G.Auto_Start_Dungeon = true
							_G.Auto_Next_Island = true
							_G.Kill_Aura = true
						end
					else
						_G.Auto_Buy_Chips_Dungeon = false
						_G.Auto_Start_Dungeon = false
						_G.Auto_Next_Island = false
						_G.Kill_Aura = false
						local args = {
							[1] = "BlackbeardReward",
							[2] = "DragonClaw",
							[3] = "2"
						}
						game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
					end
				end
				if game.Players.LocalPlayer.Backpack:FindFirstChild("Dragon Claw") and game.Players.LocalPlayer.Backpack:FindFirstChild("Dragon Claw").Level.Value >= 300  then
					local args = {
						[1] = "BuySuperhuman"
					}
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
				end
				if game.Players.LocalPlayer.Character:FindFirstChild("Dragon Claw") and game.Players.LocalPlayer.Character:FindFirstChild("Dragon Claw").Level.Value >= 300  then
					local args = {
						[1] = "BuySuperhuman"
					}
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
				end 
			end)
        end
    end
end)

gui:Seperator(" Death Step ")

gui:Toggle("Auto Death Step",_G.Auto_Death_Step,function(value)
 _G.Auto_Death_Step = value
StopTween(_G.Auto_Death_Step)
end)


spawn(function()
	while wait() do
		if _G.Auto_Death_Step then
			if game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Black Leg") or game:GetService("Players").LocalPlayer.Character:FindFirstChild("Black Leg") or game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Death Step") or game:GetService("Players").LocalPlayer.Character:FindFirstChild("Death Step") then
				if game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Black Leg") and game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Black Leg").Level.Value >= 450 then
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyDeathStep")
					_G.Select_gui = "Death Step"
				end  
				if game:GetService("Players").LocalPlayer.Character:FindFirstChild("Black Leg") and game:GetService("Players").LocalPlayer.Character:FindFirstChild("Black Leg").Level.Value >= 450 then
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyDeathStep")
					_G.Select_gui = "Death Step"
				end  
				if game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Black Leg") and game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Black Leg").Level.Value <= 449 then
					_G.Select_gui = "Black Leg"
				end 
			else 
				game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyBlackLeg")
			end
		end
	end
end)

gui:Toggle("Auto Fully Death Step",_G.Auto_Fully_Death_Step,function(value)
 _G.Auto_Fully_Death_Step = value
end)


spawn(function()
	while wait() do
		if _G.Auto_Fully_Death_Step then
			pcall(function()
				if not game.Players.LocalPlayer.Backpack:FindFirstChild("Black Leg") or not game.Players.LocalPlayer.Character:FindFirstChild("Black Leg") or not game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Death Step") or not game:GetService("Players").LocalPlayer.Character:FindFirstChild("Death Step") then
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyBlackLeg")
				end				
				if game:GetService("Workspace").Map.IceCastle.Hall.LibraryDoor.PhoeyuDoor.Transparency == 0 then  
					if game:GetService("Players").LocalPlayer.Character:FindFirstChild("Library Key") or game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Library Key") then
						Equipgui("Library Key")
						repeat wait() topos(CFrame.new(6371.2001953125, 296.63433837890625, -6841.18115234375)) until (CFrame.new(6371.2001953125, 296.63433837890625, -6841.18115234375).Position - game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 3 or not _G.Auto_Fully_Death_Step
						if (CFrame.new(6371.2001953125, 296.63433837890625, -6841.18115234375).Position - game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 3 then
							wait(1.2)
							game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyDeathStep",true)
							game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyDeathStep")
							wait(0.5)
						end
					elseif game.Players.LocalPlayer.Backpack:FindFirstChild("Black Leg") and game.Players.LocalPlayer.Backpack:FindFirstChild("Black Leg").Level.Value >= 450 or game.Players.LocalPlayer.Character:FindFirstChild("Black Leg") and game.Players.LocalPlayer.Character:FindFirstChild("Black Leg").Level.Value >= 450 then   
						if game:GetService("ReplicatedStorage"):FindFirstChild("Awakened Ice Admiral [Lv. 1400] [Boss]") or game:GetService("Workspace").Enemies:FindFirstChild("Awakened Ice Admiral [Lv. 1400] [Boss]") then
							if game:GetService("Workspace").Enemies:FindFirstChild("Awakened Ice Admiral [Lv. 1400] [Boss]") then 	
								for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
									if v.Name == "Awakened Ice Admiral [Lv. 1400] [Boss]" then    
										repeat wait()
											AutoHaki()
											Equipgui(_G.Select_gui)
											v.Head.CanCollide = false
											v.Humanoid.WalkSpeed = 0
											v.HumanoidRootPart.CanCollide = false
											v.HumanoidRootPart.Size = Vector3.new(50,50,50)
											topos(v.HumanoidRootPart.CFrame * MethodFarm)
											game:GetService'VirtualUser':CaptureController()
											game:GetService'VirtualUser':Button1Down(Vector2.new(1280, 672))
											sethiddenproperty(game:GetService("Players").LocalPlayer,"SimulationRadius",math.huge)
										until not v.Parent or v.Humanoid.Health <= 0 or _G.Auto_Fully_Death_Step == false or game:GetService("Players").LocalPlayer.Character:FindFirstChild("Library Key") or game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Library Key")
									end
								end
							else
								repeat wait() topos(game:GetService("ReplicatedStorage"):FindFirstChild("Awakened Ice Admiral [Lv. 1400] [Boss]").HumanoidRootPart.CFrame) until game:GetService("Workspace").Enemies:FindFirstChild("Awakened Ice Admiral [Lv. 1400] [Boss]")
							end
						else 
							hop()
						end
					end
				else 
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyDeathStep")
				end
			end)
		end
	end
end)

gui:Seperator(" Sharkman Karate ")

gui:Toggle("Auto Sharkman Karate",_G.Auto_SharkMan_Karate,function(value)
 _G.Auto_SharkMan_Karate = value
StopTween(_G.Auto_SharkMan_Karate)
end)


spawn(function()
	while wait() do
		if _G.Auto_SharkMan_Karate then
			if game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Fishman Karate") or game:GetService("Players").LocalPlayer.Character:FindFirstChild("Fishman Karate") or game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Sharkman Karate") or game:GetService("Players").LocalPlayer.Character:FindFirstChild("Sharkman Karate") then
				if game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Fishman Karate") and game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Fishman Karate").Level.Value >= 400 then
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuySharkmanKarate")
					_G.Select_gui = "Sharkman Karate"
				end  
				if game:GetService("Players").LocalPlayer.Character:FindFirstChild("Fishman Karate") and game:GetService("Players").LocalPlayer.Character:FindFirstChild("Fishman Karate").Level.Value >= 400 then
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuySharkmanKarate")
					_G.Select_gui = "Sharkman Karate"
				end  
				if game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Fishman Karate") and game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Fishman Karate").Level.Value <= 400 then
					_G.Select_gui = "Fishman Karate"
				end 
			else 
				game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyFishmanKarate")
			end
		end
	end
end)

gui:Toggle("Auto Fully Sharkman Karate",_G.Auto_Fully_SharkMan_Karate,function(value)
 _G.Auto_Fully_SharkMan_Karate = value
end)


spawn(function()
	while wait() do
		if _G.Auto_Fully_SharkMan_Karate then
			pcall(function()
				if not game.Players.LocalPlayer.Backpack:FindFirstChild("Fishman Karate") or not game.Players.LocalPlayer.Character:FindFirstChild("Fishman Karate") then
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyFishmanKarate")
				end		
				if string.find(game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuySharkmanKarate"), "keys") then  
					if game:GetService("Players").LocalPlayer.Character:FindFirstChild("Water Key") or game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Water Key") then
						repeat wait() topos(-2604.6958, 239.432526, -10315.1982, 0.0425701365, 0, -0.999093413, 0, 1, 0, 0.999093413, 0, 0.0425701365) until (CFrame.new(-2604.6958, 239.432526, -10315.1982, 0.0425701365, 0, -0.999093413, 0, 1, 0, 0.999093413, 0, 0.0425701365).Position - game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 3 or not _G.Auto_Fully_SharkMan_Karate
						if (CFrame.new(-2604.6958, 239.432526, -10315.1982, 0.0425701365, 0, -0.999093413, 0, 1, 0, 0.999093413, 0, 0.0425701365).Position - game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 3 then
							wait(1.2)
							game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuySharkmanKarate",true)
							game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuySharkmanKarate")
							wait(0.5)
						end
					elseif game.Players.LocalPlayer.Backpack:FindFirstChild("Fishman Karate") and game.Players.LocalPlayer.Backpack:FindFirstChild("Fishman Karate").Level.Value >= 400 or game.Players.LocalPlayer.Backpack:FindFirstChild("Fishman Karate") and game.Players.LocalPlayer.Backpack:FindFirstChild("Fishman Karate").Level.Value >= 400 then   
						if game:GetService("ReplicatedStorage"):FindFirstChild("Tide Keeper [Lv. 1475] [Boss]") or game:GetService("Workspace").Enemies:FindFirstChild("Tide Keeper [Lv. 1475] [Boss]") then
							if game:GetService("Workspace").Enemies:FindFirstChild("Tide Keeper [Lv. 1475] [Boss]") then 	
								for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
									if v.Name == "Tide Keeper [Lv. 1475] [Boss]" then    
										repeat wait()
											AutoHaki()
											Equipgui(_G.Select_gui)
											v.Head.CanCollide = false
											v.Humanoid.WalkSpeed = 0
											v.HumanoidRootPart.CanCollide = false
											v.HumanoidRootPart.Size = Vector3.new(50,50,50)
											topos(v.HumanoidRootPart.CFrame * MethodFarm)
											game:GetService'VirtualUser':CaptureController()
											game:GetService'VirtualUser':Button1Down(Vector2.new(1280, 672))
											sethiddenproperty(game:GetService("Players").LocalPlayer,"SimulationRadius",math.huge)
										until not v.Parent or v.Humanoid.Health <= 0 or _G.Auto_Fully_SharkMan_Karate == false or game:GetService("Players").LocalPlayer.Character:FindFirstChild("Water Key") or game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Water Key")
									end
								end
							else
								repeat wait() topos(game:GetService("ReplicatedStorage"):FindFirstChild("Tide Keeper [Lv. 1475] [Boss]").HumanoidRootPart.CFrame) until game:GetService("Workspace").Enemies:FindFirstChild("Tide Keeper [Lv. 1475] [Boss]")
							end
						else
							hop()
						end
					end
				else 
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuySharkmanKarate")
				end
			end)
		end
	end
end)
end

if World3 then

gui:Seperator(" Electric Claw ")

gui:Toggle("Auto Electric Claw",_G.Auto_Electric_Claw,function(value)
 _G.Auto_Electric_Claw = value
end)


spawn(function()
	while wait() do 
		if _G.Auto_Electric_Claw then
			if game.Players.LocalPlayer.Backpack:FindFirstChild("Electro") or game.Players.LocalPlayer.Character:FindFirstChild("Electro") or game.Players.LocalPlayer.Backpack:FindFirstChild("Electric Claw") or game.Players.LocalPlayer.Character:FindFirstChild("Electric Claw") then
				if game.Players.LocalPlayer.Backpack:FindFirstChild("Electro") and game.Players.LocalPlayer.Backpack:FindFirstChild("Electro").Level.Value >= 400 then
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyElectricClaw")
					_G.Select_gui = "Electric Claw"
				end  
				if game.Players.LocalPlayer.Character:FindFirstChild("Electro") and game.Players.LocalPlayer.Character:FindFirstChild("Electro").Level.Value >= 400 then
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyElectricClaw")
					_G.Select_gui = "Electric Claw"
				end  
				if game.Players.LocalPlayer.Backpack:FindFirstChild("Electro") and game.Players.LocalPlayer.Backpack:FindFirstChild("Electro").Level.Value <= 399 then
					_G.Select_gui = "Electro"
				end 
			else
				game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyElectro")
			end
		end
	end
end)

gui:Seperator(" Dragon Talon ")

gui:Toggle("Auto Dragon Talon",_G.Auto_Dragon_Talon,function(value)
 _G.Auto_Dragon_Talon = value
end)


spawn(function()
	while wait() do
		if _G.Auto_Dragon_Talon then
			if game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Dragon Claw") or game:GetService("Players").LocalPlayer.Character:FindFirstChild("Dragon Claw") or game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Dragon Talon") or game:GetService("Players").LocalPlayer.Character:FindFirstChild("Dragon Talon") then
				if game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Dragon Claw") and game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Dragon Claw").Level.Value >= 400 then
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyDragonTalon")
					_G.Select_gui = "Dragon Talon"
				end  
				if game:GetService("Players").LocalPlayer.Character:FindFirstChild("Dragon Claw") and game:GetService("Players").LocalPlayer.Character:FindFirstChild("Dragon Claw").Level.Value >= 400 then
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyDragonTalon")
					_G.Select_gui = "Dragon Talon"
				end  
				if game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Dragon Claw") and game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Dragon Claw").Level.Value <= 399 then
					_G.Select_gui = "Dragon Claw"
				end 
			else 
				game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BlackbeardReward","DragonClaw","2")
			end
		end
	end
end)

gui:Seperator(" God Human ")

gui:Toggle("Auto_God_Human",_G.Auto_God_Human,function(value)
 _G.Auto_God_Human = value
end)
end

spawn(function()
    while task.wait() do
		if _G.Auto_God_Human then
			pcall(function()
				if game.Players.LocalPlayer.Character:FindFirstChild("Superhuman") or game.Players.LocalPlayer.Backpack:FindFirstChild("Superhuman") or game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Black Leg") or game:GetService("Players").LocalPlayer.Character:FindFirstChild("Black Leg") or game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Death Step") or game:GetService("Players").LocalPlayer.Character:FindFirstChild("Death Step") or game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Fishman Karate") or game:GetService("Players").LocalPlayer.Character:FindFirstChild("Fishman Karate") or game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Sharkman Karate") or game:GetService("Players").LocalPlayer.Character:FindFirstChild("Sharkman Karate") or game.Players.LocalPlayer.Backpack:FindFirstChild("Electro") or game.Players.LocalPlayer.Character:FindFirstChild("Electro") or game.Players.LocalPlayer.Backpack:FindFirstChild("Electric Claw") or game.Players.LocalPlayer.Character:FindFirstChild("Electric Claw") or game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Dragon Claw") or game:GetService("Players").LocalPlayer.Character:FindFirstChild("Dragon Claw") or game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Dragon Talon") or game:GetService("Players").LocalPlayer.Character:FindFirstChild("Dragon Talon") or game.Players.LocalPlayer.Character:FindFirstChild("Godhuman") or game.Players.LocalPlayer.Backpack:FindFirstChild("Godhuman") then
					if game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuySuperhuman",true) == 1 then
						if game.Players.LocalPlayer.Backpack:FindFirstChild("Superhuman") and game.Players.LocalPlayer.Backpack:FindFirstChild("Superhuman").Level.Value >= 400 or game.Players.LocalPlayer.Character:FindFirstChild("Superhuman") and game.Players.LocalPlayer.Character:FindFirstChild("Superhuman").Level.Value >= 400 then
							game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyDeathStep")
						end
					else
						game.StarterGui:SetCore("SendNotification", {
							Title = "Notification", 
							Text = "Not Have Superhuman" ,
							Icon = "http://www.roblox.com/asset/?id=",
							Duration = 2.5
						})
					end
					if game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyDeathStep",true) == 1 then
						if game.Players.LocalPlayer.Backpack:FindFirstChild("Death Step") and game.Players.LocalPlayer.Backpack:FindFirstChild("Death Step").Level.Value >= 400 or game.Players.LocalPlayer.Character:FindFirstChild("Death Step") and game.Players.LocalPlayer.Character:FindFirstChild("Death Step").Level.Value >= 400 then
							game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuySharkmanKarate")
						end
					else
						game.StarterGui:SetCore("SendNotification", {
							Title = "Notification", 
							Text = "Not Have Death Step" ,
							Icon = "http://www.roblox.com/asset/?id=",
							Duration = 2.5
						})
					end
					if game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuySharkmanKarate",true) == 1 then
						if game.Players.LocalPlayer.Backpack:FindFirstChild("Sharkman Karate") and game.Players.LocalPlayer.Backpack:FindFirstChild("Sharkman Karate").Level.Value >= 400 or game.Players.LocalPlayer.Character:FindFirstChild("Sharkman Karate") and game.Players.LocalPlayer.Character:FindFirstChild("Sharkman Karate").Level.Value >= 400 then
							game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyElectricClaw")
						end
					else
						game.StarterGui:SetCore("SendNotification", {
							Title = "Notification", 
							Text = "Not Have SharkMan Karate" ,
							Icon = "http://www.roblox.com/asset/?id=",
							Duration = 2.5
						})
					end
					if game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyElectricClaw",true) == 1 then
						if game.Players.LocalPlayer.Backpack:FindFirstChild("Electric Claw") and game.Players.LocalPlayer.Backpack:FindFirstChild("Electric Claw").Level.Value >= 400 or game.Players.LocalPlayer.Character:FindFirstChild("Electric Claw") and game.Players.LocalPlayer.Character:FindFirstChild("Electric Claw").Level.Value >= 400 then
							game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyDragonTalon")
						end
					else
						game.StarterGui:SetCore("SendNotification", {
							Title = "Notification", 
							Text = "Not Have Electric Claw" ,
							Icon = "http://www.roblox.com/asset/?id=",
							Duration = 2.5
						})
					end
					if game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyDragonTalon",true) == 1 then
						if game.Players.LocalPlayer.Backpack:FindFirstChild("Dragon Talon") and game.Players.LocalPlayer.Backpack:FindFirstChild("Dragon Talon").Level.Value >= 400 or game.Players.LocalPlayer.Character:FindFirstChild("Dragon Talon") and game.Players.LocalPlayer.Character:FindFirstChild("Dragon Talon").Level.Value >= 400 then
							if string.find(game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyGodhuman",true), "Bring") then
								game.StarterGui:SetCore("SendNotification", {
									Title = "Notification", 
									Text = "Not Have Enough Material" ,
									Icon = "http://www.roblox.com/asset/?id=",
									Duration = 2.5
								})
							else
								game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyGodhuman")
							end
						end
					else
						game.StarterGui:SetCore("SendNotification", {
							Title = "Notification", 
							Text = "Not Have Dragon Talon" ,
							Icon = "http://www.roblox.com/asset/?id=",
							Duration = 2.5
						})
					end
				else
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuySuperhuman")
				end
			end)
		end
	end
end)

if World1 or World2 then
    Race:Label("Only Available At Sea 3")
end

if World3 then
Race:Seperator("Race V4")
    
    Race:Button("Teleport To Timple Of Time",function()
  Game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(28286.35546875, 14895.3017578125, 102.62469482421875)
    end)
    
Race:Button("Teleport To Lever Pull",function()
  topos(CFrame.new(28575.181640625, 14936.6279296875, 72.31636810302734))
end)

Race:Button("Teleport To Acient One (Must Be in Temple Of Time!)",function()
  topos(CFrame.new(28981.552734375, 14888.4267578125, -120.245849609375))
end)
   
   Race:Button("Unlock Lever.", function()
venyx:Notify("Unlocked")
if game:GetService("Workspace").Map["Temple of Time"].Lever.Prompt:FindFirstChild("ProximityPrompt") then
    game:GetService("Workspace").Map["Temple of Time"].Lever.Prompt:FindFirstChild("ProximityPrompt"):Remove()
else
--[[]]
end
wait(0.1)
local ProximityPrompt = Instance.new("ProximityPrompt")
ProximityPrompt.Parent = game:GetService("Workspace").Map["Temple of Time"].Lever.Prompt
ProximityPrompt.MaxActivationDistance = 10
ProximityPrompt.ActionText = "Secrets Beholds Inside"
ProximityPrompt.ObjectText = "An unknown lever of time"

function onProximity()
local part = game:GetService("Workspace").Map["Temple of Time"].MainDoor1
local TweenService = game:GetService("TweenService")

local startPosition = part.Position
local endPosition = startPosition + Vector3.new(0, -50, 0)

local tweenInfo = TweenInfo.new(10, Enum.EasingStyle.Linear, Enum.EasingDirection.Out)
local tween = TweenService:Create(part, tweenInfo, {Position = endPosition})

tween:Play()

local partnew = game:GetService("Workspace").Map["Temple of Time"].MainDoor2
local TweenService = game:GetService("TweenService")

local startPosition = partnew.Position
local endPosition = startPosition + Vector3.new(0, -50, 0)

local tweenInfo = TweenInfo.new(10, Enum.EasingStyle.Linear, Enum.EasingDirection.Out)
local tween = TweenService:Create(partnew, tweenInfo, {Position = endPosition})

tween:Play()

local SoundSFX = Instance.new("Sound")
SoundSFX.Parent = workspace
SoundSFX.SoundId = "rbxassetid://1904813041"
SoundSFX:Play()
SoundSFX.Name = "POwfpxzxzfFfFF"
game:GetService("Workspace").Map["Temple of Time"].Lever.Prompt:FindFirstChild("ProximityPrompt"):Remove()
wait(5)
workspace:FindFirstChild("POwfpxzxzfFfFF"):Remove()
game:GetService("Workspace").Map["Temple of Time"].NoGlitching:Remove()
game:GetService("Workspace").Map["Temple of Time"].NoGlitching:Remove()
game:GetService("Workspace").Map["Temple of Time"].NoGlitching:Remove()
end

ProximityPrompt.Triggered:Connect(onProximity)
end)

Race:Button("Clock Acces.", function()
    game:GetService("Workspace").Map["Temple of Time"].DoNotEnter:Remove()
    game:GetService("Workspace").Map["Temple of Time"].ClockRoomExit:Remove()
end)

Race:Toggle("Disabled Inf Stairs", nil, function(value)
	game.Players.LocalPlayer.Character.InfiniteStairs.Disabled = value
end)
   Race:Line()
 
  Race:Button("Teleport Cyborg Door (Must Be in Temple Of Time!)",function()
  topos(CFrame.new(28492.4140625, 14894.4267578125, -422.1100158691406))
  end)
  
  Race:Button("Teleport Fish Door (Must Be in Temple Of Time!)",function()
  topos(CFrame.new(28224.056640625, 14889.4267578125, -210.5872039794922))
  end)
  
  Race:Button("Teleport Ghoul Door (Must Be in Temple Of Time!)",function()
  topos(CFrame.new(28672.720703125, 14889.1279296875, 454.5961608886719))
  end)
  
  Race:Button("Teleport Human Door (Must Be in Temple Of Time!)",function()
  topos(CFrame.new(29237.294921875, 14889.4267578125, -206.94955444335938))
  end)
  
  Race:Button("Teleport Mink Door (Must Be in Temple Of Time!)",function()
  topos(CFrame.new(29020.66015625, 14889.4267578125, -379.2682800292969))
  end)
  
  Race:Button("Teleport Sky Door (Must Be in Temple Of Time!)",function()
  topos(CFrame.new(28967.408203125, 14918.0751953125, 234.31198120117188))
  end)
  
  Race:Line()
  
  Race:Button("Teleport To Safe Zone When Pvp (Must Be in Temple Of Time!)",function()
  topos(CFrame.new(28273.0859375, 14896.5078125, 157.42063903808594))
  end)
  
  Race:Button("Teleport Pvp Zone (Must Be in Temple Of Time!)",function()
  topos(CFrame.new(28766.681640625, 14967.1455078125, -164.13290405273438))
  end)
  end

Stats:Seperator(" Auto Stats ")

Stats:Toggle("Auto Stats Melee",_G.Auto_Stats_Melee,function(value)
 _G.Auto_Stats_Melee = value
end)


spawn(function()
	while wait() do
		if _G.Auto_Stats_Melee then
			local args = {
				[1] = "AddPoint",
				[2] = "Melee",
				[3] = _G.Point
			}
						
			game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
		end
	end
end)

Stats:Toggle("Auto Stats Defense",_G.Auto_Stats_Defense,function(value)
 _G.Auto_Stats_Defense = value
end)


spawn(function()
	while wait() do
		if _G.Auto_Stats_Defense then
			local args = {
				[1] = "AddPoint",
				[2] = "Defense",
				[3] = _G.Point
			}
						
			game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
		end
	end
end)

Stats:Toggle("Auto Stats Sword",_G.Auto_Stats_Sword,function(value)
 _G.Auto_Stats_Sword = value
end)


spawn(function()
	while wait() do
		if _G.Auto_Stats_Sword then
			local args = {
				[1] = "AddPoint",
				[2] = "Sword",
				[3] = _G.Point
			}
						
			game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
		end
	end
end)

Stats:Toggle("Auto Stats Gun",_G.Auto_Stats_Gun,function(value)
 _G.Auto_Stats_Gun = value
end)

spawn(function()
	while wait() do
		if _G.Auto_Stats_Gun then
			local args = {
				[1] = "AddPoint",
				[2] = "Gun",
				[3] = _G.Point
			}
						
			game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
		end
	end
end)

Stats:Toggle("Auto Stats Devil Fruit",_G.Auto_Stats_Devil_Fruit,function(value)
 _G.Auto_Stats_Devil_Fruit = value
end)


spawn(function()
	while wait() do
		if _G.Auto_Stats_Devil_Fruit then
			local args = {
				[1] = "AddPoint",
				[2] = "Demon Fruit",
				[3] = _G.Point
			}
						
			game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
		end
	end
end)

Stats:Button("Stat Refund",function()
  game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("Bones","Buy",1,2)
  end)

Stats:Slider("Select Point",1,100,1,function(value)
_G.Point = value
return "Point : " .. tostring(value)
end)

P:Seperator(" Combats ")

P:Slider("Select Size Fov",1,1000,200,function(value)
_G.Select_Size_Fov = value
return "Size Fov : " .. tostring(value)
end)

P:Toggle("Show Fov",_G.Show_Fov,function(value)
 _G.Show_Fov = value
end)

P:Toggle("Aimbot Skill Fov",_G.Aimbot_Skill_Fov,function(value)
 _G.Aimbot_Skill_Fov = value
end)

P:Seperator(" Kill Player ")


Playerslist = {}
    
    for i,v in pairs(game:GetService("Players"):GetChildren()) do
        table.insert(Playerslist,v.Name)
    end
    
    local SelectedPly = P:Dropdown("Select Players",Playerslist,function(value)
        _G.Select_Player = value
    end)
    
    P:Button("Refresh Player",function()
        Playerslist = {}
        SelectedPly:Clear()
        for i,v in pairs(game:GetService("Players"):GetChildren()) do  
            SelectedPly:Add(v.Name)
        end
    end)

P:Toggle("Spectate Player",_G.Spectate_Player,function(value)
 _G.Spectate_Player = value
end)


spawn(function()
	while wait() do
		if _G.Spectate_Player then
			pcall(function()
				if game.Players:FindFirstChild(_G.Select_Player) then
					game.Workspace.Camera.CameraSubject = game.Players:FindFirstChild(_G.Select_Player).Character.Humanoid
				end
			end)
		else
			game.Workspace.Camera.CameraSubject = game.Players.LocalPlayer.Character.Humanoid
		end
	end
end)

P:Toggle("Teleport to Player",_G.Teleport_to_Player,function(value)
 _G.Teleport_to_Player = value
StopTween(_G.Teleport_to_Player)
end)


spawn(function()
	while wait() do
		if _G.Teleport_to_Player then
			pcall(function()
				if game.Players:FindFirstChild(_G.Select_Player) then
					topos(game.Players[_G.Select_Player].Character.HumanoidRootPart.CFrame)
				end
			end)
		end
	end
end)

P:Toggle("Auto Kill Player [Melee]",_G.Auto_Kill_Player_Melee,function(value)
 _G.Auto_Kill_Player_Melee = value
StopTween(_G.Auto_Kill_Player_Melee)
end)


spawn(function()
	while wait() do 
		pcall(function()
			if _G.Auto_Kill_Player_Melee then
				if game.Players:FindFirstChild(_G.Select_Player) then
					for i,v in pairs(game:GetService("Workspace").Characters:GetChildren()) do
						if v.Name == _G.Select_Player and v.Humanoid.Health > 0 then
							repeat wait()
								if (v.HumanoidRootPart.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).magnitude > 300 then
									topos(v.HumanoidRootPart.CFrame * CFrame.new(0,5,0))
								elseif (v.HumanoidRootPart.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).magnitude <= 300 then
									AutoHaki()
									Equipgui(_G.Select_gui_Kill_Player_Melee)
									topos(v.HumanoidRootPart.CFrame * CFrame.new(0,5,0))
									game:GetService'VirtualUser':CaptureController()
									game:GetService'VirtualUser':Button1Down(Vector2.new(1280, 672))
								end
							until game.Players:FindFirstChild(_G.Select_Player).Character.Humanoid.Health <= 0 or not _G.Auto_Kill_Player_Melee or not game.Players:FindFirstChild(_G.Select_Player)
						end
					end
				end
			end
		end)
	end
end)

P:Toggle("Auto Kill Player [Gun]",_G.Auto_Kill_Player_Gun,function(value)
 _G.Auto_Kill_Player_Gun = value
StopTween(_G.Auto_Kill_Player_Gun)
end)


spawn(function()
	while wait() do 
		pcall(function()
			if _G.Auto_Kill_Player_Gun then
				if game.Players:FindFirstChild(_G.Select_Player) then
					for i,v in pairs(game:GetService("Workspace").Characters:GetChildren()) do
						if v.Name == _G.Select_Player and v.Humanoid.Health > 0 then
							repeat wait()
								if (v.HumanoidRootPart.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).magnitude > 300 then
									topos(v.HumanoidRootPart.CFrame)
								elseif (v.HumanoidRootPart.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).magnitude <= 300 then
									AutoHaki()
									Equipgui(SelectToolguiGun)
									UseGunKillPlayer = true
									game:GetService("Players").LocalPlayer.Character[SelectToolguiGun].Cooldown.Value = 0
									v.HumanoidRootPart.Size = Vector3.new(60,60,60)
									v.HumanoidRootPart.Transparency = 0.7
									topos(v.HumanoidRootPart.CFrame * CFrame.new(0,50,-10))
									game:GetService'VirtualUser':CaptureController()
									game:GetService'VirtualUser':Button1Down(Vector2.new(1280, 672))
								end
							until game.Players:FindFirstChild(_G.Select_Player).Character.Humanoid.Health <= 0 or not _G.Auto_Kill_Player_Gun or not game.Players:FindFirstChild(_G.Select_Player)
						end
					end
				end
			else
				UseGunKillPlayer = false
			end
		end)
	end
end)

Teleport:Seperator(" WORLD ")
 
 Teleport:Button("Teleport To Old World",function()
  game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("TravelMain")
  end)
 
 Teleport:Button("Teleport To Second Sea",function()
  game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("TravelDressrosa")
 end)

 
 Teleport:Button("Teleport To Third Sea",function()
  game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("TravelZou")
  end)
 
 Teleport:Button("Teleport to Seabeast",function()
  for i,v in pairs(game:GetService("Workspace").SeaBeasts:GetChildren()) do
  if v:FindFirstChild("HumanoidRootPart") then
  topos(v.HumanoidRootPart.CFrame*CFrame.new(0,100,0))
  end
  end
 end)
 
 Teleport:Seperator(" Island ")
 
 if World1 then
 Teleport:Dropdown("Select Island", {
  "WindMill",
  "Marine",
  "Middle Town",
  "Jungle",
  "Pirate Village",
  "Desert",
  "Snow Island",
  "MarineFord",
  "Colosseum",
  "Sky Island 1",
  "Sky Island 2",
  "Sky Island 3",
  "Prison",
  "Magma Village",
  "Under Water Island",
  "Fountain City",
  "Shank Room",
  "Mob Island"
 },function(value)
  _G.SelectIsland = value
  end)
 end
 
 if World2 then
 Teleport:Dropdown("Select Island", {
  "The Cafe",
  "Frist Spot",
  "Dark Area",
  "Flamingo Mansion",
  "Flamingo Room",
  "Green Zone",
  "Factory",
  "Colossuim",
  "Zombie Island",
  "Two Snow Mountain",
  "Punk Hazard",
  "Cursed Ship",
  "Ice Castle",
  "Forgotten Island",
  "Ussop Island",
  "Mini Sky Island"
 },function(value)
  _G.SelectIsland = value
  end)
 end
 
 if World3 then
 Teleport:Dropdown("Select Island", {
  "Mansion",
  "Port Town",
  "Great Tree",
  "Castle On The Sea",
  "MiniSky",
  "Hydra Island",
  "Floating Turtle",
  "Haunted Castle",
  "Ice Cream Island",
  "Peanut Island",
  "Cake Island",
  "Noname Island(New)"
 },function(value)
  _G.SelectIsland = value
  end)
 end
 
 Teleport:Toggle("Teleport",false,function(value)
  _G.TeleportIsland = value
  if _G.TeleportIsland == true then
  repeat wait()
  if _G.SelectIsland == "WindMill" then
  topos(CFrame.new(979.79895019531, 16.516613006592, 1429.0466308594))
  elseif _G.SelectIsland == "Marine" then
  topos(CFrame.new(-2566.4296875, 6.8556680679321, 2045.2561035156))
  elseif _G.SelectIsland == "Middle Town" then
  topos(CFrame.new(-690.33081054688, 15.09425163269, 1582.2380371094))
  elseif _G.SelectIsland == "Jungle" then
  topos(CFrame.new(-1612.7957763672, 36.852081298828, 149.12843322754))
  elseif _G.SelectIsland == "Pirate Village" then
  topos(CFrame.new(-1181.3093261719, 4.7514905929565, 3803.5456542969))
  elseif _G.SelectIsland == "Desert" then
  topos(CFrame.new(944.15789794922, 20.919729232788, 4373.3002929688))
  elseif _G.SelectIsland == "Snow Island" then
  topos(CFrame.new(1347.8067626953, 104.66806030273, -1319.7370605469))
  elseif _G.SelectIsland == "MarineFord" then
  topos(CFrame.new(-4914.8212890625, 50.963626861572, 4281.0278320313))
  elseif _G.SelectIsland == "Colosseum" then
  topos(CFrame.new(-1427.6203613281, 7.2881078720093, -2792.7722167969))
  elseif _G.SelectIsland == "Sky Island 1" then
  topos(CFrame.new(-4869.1025390625, 733.46051025391, -2667.0180664063))
  elseif _G.SelectIsland == "Sky Island 2" then
  game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(-4607.82275, 872.54248, -1667.55688))
  elseif _G.SelectIsland == "Sky Island 3" then
  game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(-7894.6176757813, 5547.1416015625, -380.29119873047))
  elseif _G.SelectIsland == "Prison" then
  topos(CFrame.new(4875.330078125, 5.6519818305969, 734.85021972656))
  elseif _G.SelectIsland == "Magma Village" then
  topos(CFrame.new(-5247.7163085938, 12.883934020996, 8504.96875))
  elseif _G.SelectIsland == "Under Water Island" then
  game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(61163.8515625, 11.6796875, 1819.7841796875))
  elseif _G.SelectIsland == "Fountain City" then
  topos(CFrame.new(5127.1284179688, 59.501365661621, 4105.4458007813))
  elseif _G.SelectIsland == "Shank Room" then
  topos(CFrame.new(-1442.16553, 29.8788261, -28.3547478))
  elseif _G.SelectIsland == "Mob Island" then
  topos(CFrame.new(-2850.20068, 7.39224768, 5354.99268))
  elseif _G.SelectIsland == "The Cafe" then
  topos(CFrame.new(-380.47927856445, 77.220390319824, 255.82550048828))
  elseif _G.SelectIsland == "Frist Spot" then
  topos(CFrame.new(-11.311455726624, 29.276733398438, 2771.5224609375))
  elseif _G.SelectIsland == "Dark Area" then
  topos(CFrame.new(3780.0302734375, 22.652164459229, -3498.5859375))
  elseif _G.SelectIsland == "Flamingo Mansion" then
  topos(CFrame.new(-483.73370361328, 332.0383605957, 595.32708740234))
  elseif _G.SelectIsland == "Flamingo Room" then
  topos(CFrame.new(2284.4140625, 15.152037620544, 875.72534179688))
  elseif _G.SelectIsland == "Green Zone" then
  topos(CFrame.new(-2448.5300292969, 73.016105651855, -3210.6306152344))
  elseif _G.SelectIsland == "Factory" then
  topos(CFrame.new(424.12698364258, 211.16171264648, -427.54049682617))
  elseif _G.SelectIsland == "Colossuim" then
  topos(CFrame.new(-1503.6224365234, 219.7956237793, 1369.3101806641))
  elseif _G.SelectIsland == "Zombie Island" then
  topos(CFrame.new(-5622.033203125, 492.19604492188, -781.78552246094))
  elseif _G.SelectIsland == "Two Snow Mountain" then
  topos(CFrame.new(753.14288330078, 408.23559570313, -5274.6147460938))
  elseif _G.SelectIsland == "Punk Hazard" then
  topos(CFrame.new(-6127.654296875, 15.951762199402, -5040.2861328125))
  elseif _G.SelectIsland == "Cursed Ship" then
  topos(CFrame.new(923.40197753906, 125.05712890625, 32885.875))
  elseif _G.SelectIsland == "Ice Castle" then
  topos(CFrame.new(6148.4116210938, 294.38687133789, -6741.1166992188))
  elseif _G.SelectIsland == "Forgotten Island" then
  topos(CFrame.new(-3032.7641601563, 317.89672851563, -10075.373046875))
  elseif _G.SelectIsland == "Ussop Island" then
  topos(CFrame.new(4816.8618164063, 8.4599885940552, 2863.8195800781))
  elseif _G.SelectIsland == "Mini Sky Island" then
  topos(CFrame.new(-288.74060058594, 49326.31640625, -35248.59375))
  elseif _G.SelectIsland == "Great Tree" then
  topos(CFrame.new(2681.2736816406, 1682.8092041016, -7190.9853515625))
  elseif _G.SelectIsland == "Castle On The Sea" then
  topos(CFrame.new(-5074.45556640625, 314.5155334472656, -2991.054443359375))
  elseif _G.SelectIsland == "MiniSky" then
  topos(CFrame.new(-260.65557861328, 49325.8046875, -35253.5703125))
  elseif _G.SelectIsland == "Port Town" then
  topos(CFrame.new(-290.7376708984375, 6.729952812194824, 5343.5537109375))
  elseif _G.SelectIsland == "Hydra Island" then
  topos(CFrame.new(5228.8842773438, 604.23400878906, 345.0400390625))
  elseif _G.SelectIsland == "Floating Turtle" then
  topos(CFrame.new(-13274.528320313, 531.82073974609, -7579.22265625))
  elseif _G.SelectIsland == "Mansion" then
  game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(-12471.169921875, 374.94024658203, -7551.677734375))
  elseif _G.SelectIsland == "Haunted Castle" then
  topos(CFrame.new(-9515.3720703125, 164.00624084473, 5786.0610351562))
  elseif _G.SelectIsland == "Ice Cream Island" then
  topos(CFrame.new(-902.56817626953, 79.93204498291, -10988.84765625))
  elseif _G.SelectIsland == "Peanut Island" then
  topos(CFrame.new(-2062.7475585938, 50.473892211914, -10232.568359375))
  elseif _G.SelectIsland == "Cake Island" then
  topos(CFrame.new(-1884.7747802734375, 19.327526092529297, -11666.8974609375))
  elseif _G.SelectIsland == "Noname Island(New)" then
  topos(CFrame.new(231.742981, 25.3354111, -12199.0537, 0.998278677, -5.16006757e-08, 0.0586484075, 4.79685092e-08, 1, 6.33390442e-08, -0.0586484075, -6.04167383e-08, 0.998278677))
  end
  until not _G.TeleportIsland
  end
  StopTween(_G.TeleportIsland)
 end)
 
 Teleport:Button("Instant Teleport",function()
		 _G.Instant = true
        if _G.Instant == true then
	     if _G.SelectIsland == "Port Town" then 
	     repeat task.wait()
         game.Players.LocalPlayer.Character.Head:Destroy()
         wait(0.5)
         game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-290.7376708984375, 6.729952812194824, 5343.5537109375)
         game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("SetSpawnPoint")
         until game:GetService("Players").LocalPlayer.Data.SpawnPoint.Value == SPAWNPOINT 
	    elseif _G.SelectIsland == "Great Tree" then
	    repeat task.wait()
        game.Players.LocalPlayer.Character.Head:Destroy()
        wait(0.5)
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(2681.2736816406, 1682.8092041016, -7190.9853515625)
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("SetSpawnPoint")
        until game:GetService("Players").LocalPlayer.Data.SpawnPoint.Value == SPAWNPOINT 
        elseif _G.SelectIsland == "Castle On The Sea" then
	    repeat task.wait()
        game.Players.LocalPlayer.Character.Head:Destroy()
        wait(0.5)
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-5074.45556640625, 314.5155334472656, -2991.054443359375)
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("SetSpawnPoint")
        until game:GetService("Players").LocalPlayer.Data.SpawnPoint.Value == SPAWNPOINT 
        elseif _G.SelectIsland == "MiniSky" then
	    repeat task.wait()
        game.Players.LocalPlayer.Character.Head:Destroy()
        wait(0.5)
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-260.65557861328, 49325.8046875, -35253.5703125)
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("SetSpawnPoint")
        until game:GetService("Players").LocalPlayer.Data.SpawnPoint.Value == SPAWNPOINT 
        elseif _G.SelectIsland == "Hydra Island" then
	    repeat task.wait()
        game.Players.LocalPlayer.Character.Head:Destroy()
        wait(0.5)
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(5228.8842773438, 604.23400878906, 345.0400390625)
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("SetSpawnPoint")
        until game:GetService("Players").LocalPlayer.Data.SpawnPoint.Value == SPAWNPOINT 
        elseif _G.SelectIsland == "Floating Turtle" then
	    repeat task.wait()
        game.Players.LocalPlayer.Character.Head:Destroy()
        wait(0.5)
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-13274.528320313, 531.82073974609, -7579.22265625)
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("SetSpawnPoint")
        until game:GetService("Players").LocalPlayer.Data.SpawnPoint.Value == SPAWNPOINT 
        elseif _G.SelectIsland == "Haunted Castle" then
	    repeat task.wait()
        game.Players.LocalPlayer.Character.Head:Destroy()
        wait(0.5)
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-9515.3720703125, 164.00624084473, 5786.0610351562)
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("SetSpawnPoint")
        until game:GetService("Players").LocalPlayer.Data.SpawnPoint.Value == SPAWNPOINT 
        elseif _G.SelectIsland == "Ice Cream Island" then
	    repeat task.wait()
        game.Players.LocalPlayer.Character.Head:Destroy()
        wait(0.5)
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-902.56817626953, 79.93204498291, -10988.84765625)
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("SetSpawnPoint")
        until game:GetService("Players").LocalPlayer.Data.SpawnPoint.Value == SPAWNPOINT 
        elseif _G.SelectIsland == "Peanut Island" then
	    repeat task.wait()
        game.Players.LocalPlayer.Character.Head:Destroy()
        wait(0.5)
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-2062.7475585938, 50.473892211914, -10232.568359375)
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("SetSpawnPoint")
        until game:GetService("Players").LocalPlayer.Data.SpawnPoint.Value == SPAWNPOINT 
        elseif _G.SelectIsland == "Cake Island" then
	    repeat task.wait()
        game.Players.LocalPlayer.Character.Head:Destroy()
        wait(0.5)
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-1884.7747802734375, 19.327526092529297, -11666.8974609375)
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("SetSpawnPoint")
        until game:GetService("Players").LocalPlayer.Data.SpawnPoint.Value == SPAWNPOINT 
        ----------------------------------------------------------------------------------------------------
        elseif _G.SelectIsland == "The Cafe" then
	    repeat task.wait()
        game.Players.LocalPlayer.Character.Head:Destroy()
        wait(0.5)
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-380.47927856445, 77.220390319824, 255.82550048828)
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("SetSpawnPoint")
        until game:GetService("Players").LocalPlayer.Data.SpawnPoint.Value == SPAWNPOINT 
        elseif _G.SelectIsland == "Frist Spot" then
	    repeat task.wait()
        game.Players.LocalPlayer.Character.Head:Destroy()
        wait(0.5)
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-11.311455726624, 29.276733398438, 2771.5224609375)
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("SetSpawnPoint")
        until game:GetService("Players").LocalPlayer.Data.SpawnPoint.Value == SPAWNPOINT 
        elseif _G.SelectIsland == "Dark Area" then
	    repeat task.wait()
        game.Players.LocalPlayer.Character.Head:Destroy()
        wait(0.5)
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(3780.0302734375, 22.652164459229, -3498.5859375)
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("SetSpawnPoint")
        until game:GetService("Players").LocalPlayer.Data.SpawnPoint.Value == SPAWNPOINT 
        elseif _G.SelectIsland == "Flamingo Mansion" then
	    repeat task.wait()
        game.Players.LocalPlayer.Character.Head:Destroy()
        wait(0.5)
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-483.73370361328, 332.0383605957, 595.32708740234)
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("SetSpawnPoint")
        until game:GetService("Players").LocalPlayer.Data.SpawnPoint.Value == SPAWNPOINT 
        elseif _G.SelectIsland == "Flamingo Room" then
	    repeat task.wait()
        game.Players.LocalPlayer.Character.Head:Destroy()
        wait(0.5)
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(2284.4140625, 15.152037620544, 875.72534179688)
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("SetSpawnPoint")
        until game:GetService("Players").LocalPlayer.Data.SpawnPoint.Value == SPAWNPOINT 
        elseif _G.SelectIsland == "Green Zone" then
	    repeat task.wait()
        game.Players.LocalPlayer.Character.Head:Destroy()
        wait(0.5)
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-2448.5300292969, 73.016105651855, -3210.6306152344)
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("SetSpawnPoint")
        until game:GetService("Players").LocalPlayer.Data.SpawnPoint.Value == SPAWNPOINT 
        elseif _G.SelectIsland == "Factory" then
	    repeat task.wait()
        game.Players.LocalPlayer.Character.Head:Destroy()
        wait(0.5)
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(424.12698364258, 211.16171264648, -427.54049682617)
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("SetSpawnPoint")
        until game:GetService("Players").LocalPlayer.Data.SpawnPoint.Value == SPAWNPOINT 
        elseif _G.SelectIsland == "Colossuim" then
	    repeat task.wait()
        game.Players.LocalPlayer.Character.Head:Destroy()
        wait(0.5)
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-1503.6224365234, 219.7956237793, 1369.3101806641)
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("SetSpawnPoint")
        until game:GetService("Players").LocalPlayer.Data.SpawnPoint.Value == SPAWNPOINT 
        elseif _G.SelectIsland == "Zombie Island" then
	    repeat task.wait()
        game.Players.LocalPlayer.Character.Head:Destroy()
        wait(0.5)
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-5622.033203125, 492.19604492188, -781.78552246094)
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("SetSpawnPoint")
        until game:GetService("Players").LocalPlayer.Data.SpawnPoint.Value == SPAWNPOINT 
        elseif _G.SelectIsland == "Two Snow Mountain" then
	    repeat task.wait()
        game.Players.LocalPlayer.Character.Head:Destroy()
        wait(0.5)
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(753.14288330078, 408.23559570313, -5274.6147460938)
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("SetSpawnPoint")
        until game:GetService("Players").LocalPlayer.Data.SpawnPoint.Value == SPAWNPOINT 
        elseif _G.SelectIsland == "Punk Hazard" then
	    repeat task.wait()
        game.Players.LocalPlayer.Character.Head:Destroy()
        wait(0.5)
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-6127.654296875, 15.951762199402, -5040.2861328125)
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("SetSpawnPoint")
        until game:GetService("Players").LocalPlayer.Data.SpawnPoint.Value == SPAWNPOINT 
        elseif _G.SelectIsland == "Cursed Ship" then
	    repeat task.wait()
        game.Players.LocalPlayer.Character.Head:Destroy()
        wait(0.5)
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(923.40197753906, 125.05712890625, 32885.875)
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("SetSpawnPoint")
        until game:GetService("Players").LocalPlayer.Data.SpawnPoint.Value == SPAWNPOINT 
        elseif _G.SelectIsland == "Ice Castle" then
	    repeat task.wait()
        game.Players.LocalPlayer.Character.Head:Destroy()
        wait(0.5)
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(6148.4116210938, 294.38687133789, -6741.1166992188)
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("SetSpawnPoint")
        until game:GetService("Players").LocalPlayer.Data.SpawnPoint.Value == SPAWNPOINT 
        elseif _G.SelectIsland == "Forgotten Island" then
	    repeat task.wait()
        game.Players.LocalPlayer.Character.Head:Destroy()
        wait(0.5)
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-3032.7641601563, 317.89672851563, -10075.373046875)
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("SetSpawnPoint")
        until game:GetService("Players").LocalPlayer.Data.SpawnPoint.Value == SPAWNPOINT 
        elseif _G.SelectIsland == "Ussop Island" then
	    repeat task.wait()
        game.Players.LocalPlayer.Character.Head:Destroy()
        wait(0.5)
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(4816.8618164063, 8.4599885940552, 2863.8195800781)
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("SetSpawnPoint")
        until game:GetService("Players").LocalPlayer.Data.SpawnPoint.Value == SPAWNPOINT 
        elseif _G.SelectIsland == "Mini Sky Island" then
	    repeat task.wait()
        game.Players.LocalPlayer.Character.Head:Destroy()
        wait(0.5)
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-288.74060058594, 49326.31640625, -35248.59375)
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("SetSpawnPoint")
        until game:GetService("Players").LocalPlayer.Data.SpawnPoint.Value == SPAWNPOINT 
        elseif _G.SelectIsland == "WindMill" then
	    repeat task.wait()
        game.Players.LocalPlayer.Character.Head:Destroy()
        wait(0.5)
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(979.79895019531, 16.516613006592, 1429.0466308594)
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("SetSpawnPoint")
        until game:GetService("Players").LocalPlayer.Data.SpawnPoint.Value == SPAWNPOINT 
        elseif _G.SelectIsland == "Marine" then
	    repeat task.wait()
        game.Players.LocalPlayer.Character.Head:Destroy()
        wait(0.5)
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-2566.4296875, 6.8556680679321, 2045.2561035156)
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("SetSpawnPoint")
        until game:GetService("Players").LocalPlayer.Data.SpawnPoint.Value == SPAWNPOINT
        elseif _G.SelectIsland == "Middle Town" then
	    repeat task.wait()
        game.Players.LocalPlayer.Character.Head:Destroy()
        wait(0.5)
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-690.33081054688, 15.09425163269, 1582.2380371094)
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("SetSpawnPoint")
        until game:GetService("Players").LocalPlayer.Data.SpawnPoint.Value == SPAWNPOINT
        elseif _G.SelectIsland == "Jungle" then
	    repeat task.wait()
        game.Players.LocalPlayer.Character.Head:Destroy()
        wait(0.5)
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-1612.7957763672, 36.852081298828, 149.12843322754)
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("SetSpawnPoint")
        until game:GetService("Players").LocalPlayer.Data.SpawnPoint.Value == SPAWNPOINT
        elseif _G.SelectIsland == "Pirate Village" then
	    repeat task.wait()
        game.Players.LocalPlayer.Character.Head:Destroy()
        wait(0.5)
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-1181.3093261719, 4.7514905929565, 3803.5456542969)
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("SetSpawnPoint")
        until game:GetService("Players").LocalPlayer.Data.SpawnPoint.Value == SPAWNPOINT
        elseif _G.SelectIsland == "Desert" then
	    repeat task.wait()
        game.Players.LocalPlayer.Character.Head:Destroy()
        wait(0.5)
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(944.15789794922, 20.919729232788, 4373.3002929688)
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("SetSpawnPoint")
        until game:GetService("Players").LocalPlayer.Data.SpawnPoint.Value == SPAWNPOINT
        elseif _G.SelectIsland == "Snow Island" then
	    repeat task.wait()
        game.Players.LocalPlayer.Character.Head:Destroy()
        wait(0.5)
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(1347.8067626953, 104.66806030273, -1319.7370605469)
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("SetSpawnPoint")
        until game:GetService("Players").LocalPlayer.Data.SpawnPoint.Value == SPAWNPOINT
        elseif _G.SelectIsland == "MarineFord" then
	    repeat task.wait()
        game.Players.LocalPlayer.Character.Head:Destroy()
        wait(0.5)
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-4914.8212890625, 50.963626861572, 4281.0278320313)
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("SetSpawnPoint")
        until game:GetService("Players").LocalPlayer.Data.SpawnPoint.Value == SPAWNPOINT
        elseif _G.SelectIsland == "Colosseum" then
	    repeat task.wait()
        game.Players.LocalPlayer.Character.Head:Destroy()
        wait(0.5)
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-1427.6203613281, 7.2881078720093, -2792.7722167969)
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("SetSpawnPoint")
        until game:GetService("Players").LocalPlayer.Data.SpawnPoint.Value == SPAWNPOINT
        elseif _G.SelectIsland == "Sky Island 1" then
	    repeat task.wait()
        game.Players.LocalPlayer.Character.Head:Destroy()
        wait(0.5)
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-4869.1025390625, 733.46051025391, -2667.0180664063)
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("SetSpawnPoint")
        until game:GetService("Players").LocalPlayer.Data.SpawnPoint.Value == SPAWNPOINT
        elseif _G.SelectIsland == "Prison" then
	    repeat task.wait()
        game.Players.LocalPlayer.Character.Head:Destroy()
        wait(0.5)
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(4875.330078125, 5.6519818305969, 734.85021972656)
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("SetSpawnPoint")
        until game:GetService("Players").LocalPlayer.Data.SpawnPoint.Value == SPAWNPOINT
        elseif _G.SelectIsland == "Magma Village" then
	    repeat task.wait()
        game.Players.LocalPlayer.Character.Head:Destroy()
        wait(0.5)
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-5247.7163085938, 12.883934020996, 8504.96875)
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("SetSpawnPoint")
        until game:GetService("Players").LocalPlayer.Data.SpawnPoint.Value == SPAWNPOINT
        elseif _G.SelectIsland == "Fountain City" then
	    repeat task.wait()
        game.Players.LocalPlayer.Character.Head:Destroy()
        wait(0.5)
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(127.1284179688, 59.501365661621, 4105.4458007813)
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("SetSpawnPoint")
        until game:GetService("Players").LocalPlayer.Data.SpawnPoint.Value == SPAWNPOINT
        elseif _G.SelectIsland == "Shank Room" then
	    repeat task.wait()
        game.Players.LocalPlayer.Character.Head:Destroy()
        wait(0.5)
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-1442.16553, 29.8788261, -28.3547478)
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("SetSpawnPoint")
        until game:GetService("Players").LocalPlayer.Data.SpawnPoint.Value == SPAWNPOINT
        elseif _G.SelectIsland == "Mob Island" then
	    repeat task.wait()
        game.Players.LocalPlayer.Character.Head:Destroy()
        wait(0.5)
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-2850.20068, 7.39224768, 5354.99268)
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("SetSpawnPoint")
        until game:GetService("Players").LocalPlayer.Data.SpawnPoint.Value == SPAWNPOINT
        end
     end
end)

if World1 then
    Dungeon:Label("Dungeon Raid Only Available At Sea 2 and 3")
end

if World2 or World3 then
Dungeon:Seperator("Use in Dungeon Only!")

chip = {
	"Flame", 
	"Ice", 
	"Quake", 
	"Light",
	"Dark",
	"String",
	"Rumble",
	"Magma",
	"Human: Buddha",
	"Sand",
	"Bird: Phoenix"
}

Dungeon:Dropdown("Select Dungeon",chip,function(value)
 _G.Select_Dungeon = value
end)

Dungeon:Toggle("Auto Buy Chip Dungeon",_G.Auto_Buy_Chips_Dungeon,function(value)
 _G.Auto_Buy_Chips_Dungeon = value
end)


spawn(function()
    while wait() do
		if _G.Auto_Buy_Chips_Dungeon then
			pcall(function()
				local args = {
					[1] = "RaidsNpc",
					[2] = "Select",
					[3] = _G.Select_Dungeon
				}
				
				game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
			end)
		end
    end
end)


Dungeon:Toggle("Auto Start Dungeon",_G.Auto_StartRaid,function(value)
 _G.Auto_StartRaid = value
end)

spawn(function()
    while wait(.1) do
        pcall(function()
            if _G.Auto_StartRaid then
                if game:GetService("Players")["LocalPlayer"].PlayerGui.Main.Timer.Visible == false then
                    if not game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 1") and game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Special Microchip") or game:GetService("Players").LocalPlayer.Character:FindFirstChild("Special Microchip") then
                        if World2 then
                            fireclickdetector(game:GetService("Workspace").Map.CircleIsland.RaidSummon2.Button.Main.ClickDetector)
                        elseif World3 then
                            fireclickdetector(game:GetService("Workspace").Map["Boat Castle"].RaidSummon2.Button.Main.ClickDetector)
                        end
                    end
                end
            end
        end)
    end
    end)

Dungeon:Toggle("Auto Next Island",_G.Auto_Next_Island,function(value)
 _G.Auto_Next_Island = value
end)

spawn(function()
    while wait() do
        if _G.Auto_Next_Island then
			if not game.Players.LocalPlayer.PlayerGui.Main.Timer.Visible == false then
				if game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 5") then
					topos(game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 5").CFrame * CFrame.new(0,70,100))
				elseif game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 4") then
					topos(game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 4").CFrame * CFrame.new(0,70,100))
				elseif game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 3") then
					topos(game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 3").CFrame * CFrame.new(0,70,100))
				elseif game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 2") then
					topos(game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 2").CFrame * CFrame.new(0,70,100))
				elseif game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 1") then
					topos(game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 1").CFrame * CFrame.new(0,70,100))
				end
			end
        end
    end
end)

Dungeon:Toggle("Kill Aura",_G.Kill_Aura,function(value)
 _G.Kill_Aura = value  
end)

spawn(function()
    while wait() do
        if _G.Kill_Aura then
            for i,v in pairs(game.Workspace.Enemies:GetDescendants()) do
                if v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
                    pcall(function()
                        repeat wait(.1)
                            v.Humanoid.Health = 0
                            v.HumanoidRootPart.CanCollide = false
							sethiddenproperty(game.Players.LocalPlayer, "SimulationRadius", math.huge)
                        until not _G.Kill_Aura  or not v.Parent or v.Humanoid.Health <= 0
                    end)
                end
            end
        end
    end
end)

Dungeon:Toggle("Auto Awake",_G.Auto_Awake,function(value)
 _G.Auto_Awake = value 
end)


spawn(function()
	while wait(.1) do
		if _G.Auto_Awake then
			pcall(function()
				local args = {
					[1] = "Awakener",
					[2] = "Check"
				}
				
				game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
				local args = {
					[1] = "Awakener",
					[2] = "Awaken"
				}
				game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
			end)
		end
	end
end)

  
  Dungeon:Button("Next Island",function()
   pcall(function()
    if game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 5") then
    topos(game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 5").CFrame*CFrame.new(0,70,100))
    elseif game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 4") then
    topos(game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 4").CFrame*CFrame.new(0,70,100))
    elseif game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 3") then
    topos(game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 3").CFrame*CFrame.new(0,70,100))
    elseif game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 2") then
    topos(game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 2").CFrame*CFrame.new(0,70,100))
    elseif game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 1") then
    topos(game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 1").CFrame*CFrame.new(0,70,100))
    end
    end)
  end)
  
local function toTarget(...)
	local RealtargetPos = {...}
	local targetPos = RealtargetPos[1]
	local RealTarget
	if type(targetPos) == "vector" then
		RealTarget = CFrame.new(targetPos)
	elseif type(targetPos) == "userdata" then
		RealTarget = targetPos
	elseif type(targetPos) == "number" then
		RealTarget = CFrame.new(unpack(RealtargetPos))
	end

	if game.Players.LocalPlayer.Character:WaitForChild("Humanoid").Health == 0 then if tween then tween:Cancel() end repeat wait() until game.Players.LocalPlayer.Character:WaitForChild("Humanoid").Health > 0; wait(0.2) end

	local tweenfunc = {}
	local Distance = (RealTarget.Position - game:GetService("Players").LocalPlayer.Character:WaitForChild("HumanoidRootPart").Position).Magnitude
	if Distance < 1000 then
		Speed = 315
	elseif Distance >= 1000 then
		Speed = 300
	end

function topos(Pos)
            Distance = (Pos.Position - game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).Magnitude
            if Distance < 250 then
                Speed = 600
            elseif Distance >= 1000 then
                Speed = 200
            end
            game:GetService("TweenService"):Create(
                game:GetService("Players").LocalPlayer.Character.HumanoidRootPart,
                TweenInfo.new(Distance/Speed, Enum.EasingStyle.Linear),
                {CFrame = Pos}
            ):Play()
            _G.Clip = true
            wait(Distance/Speed)
            _G.Clip = false
end
end

Dungeon:Seperator("\\\\\  Law Dungeon  //")

Dungeon:Toggle("Auto Buy Law Chip",_G.Auto_Buy_Law_Chip,function(value)
 _G.Auto_Buy_Law_Chip = value
end)

spawn(function()
	while wait() do
		if _G.Auto_Buy_Law_Chip then
			pcall(function()
				if game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Microchip") or game:GetService("Players").LocalPlayer.Character:FindFirstChild("Microchip") or game:GetService("Workspace").Enemies:FindFirstChild("Order [Lv. 1250] [Raid Boss]") or game:GetService("ReplicatedStorage"):FindFirstChild("Order [Lv. 1250] [Raid Boss]") then
				
				else
					local args = {
						[1] = "BlackbeardReward",
						[2] = "Microchip",
						[3] = "2"
					}
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
				end
			end)
		end
	end
end)

Dungeon:Toggle("Auto Start Law Dungeon",_G.Auto_Start_Law_Dungeon,function(value)
 _G.Auto_Start_Law_Dungeon = value
end)


spawn(function()
	while wait() do
		if _G.Auto_Start_Law_Dungeon then
			pcall(function()
				if game:GetService("Players").LocalPlayer.Character:FindFirstChild("Microchip") or game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Microchip") then
					fireclickdetector(game:GetService("Workspace").Map.CircleIsland.RaidSummon.Button.Main.ClickDetector)
				end
			end)
		end
	end
end)

Dungeon:Toggle("Auto Kill Law",_G.Auto_Kill_Law,function(value)
_G.Auto_Kill_Law = value
end)

spawn(function()
	while wait() do
		if _G.Auto_Kill_Law then
			pcall(function()
				if game:GetService("ReplicatedStorage"):FindFirstChild("Order [Lv. 1250] [Raid Boss]") or game:GetService("Workspace").Enemies:FindFirstChild("Order [Lv. 1250] [Raid Boss]") then
					for i,v in pairs(game.Workspace.Enemies:GetChildren()) do
						if _G.Auto_Kill_Law and v.Name == "Order [Lv. 1250] [Raid Boss]" and v:FindFirstChild("HumanoidRootPart") and v:FindFirstChild("Humanoid") and v.Humanoid.Health > 0 then
							repeat task.wait()
								AutoHaki()
								Equipgui(_G.Select_gui)
								v.HumanoidRootPart.CanCollide = false
								v.HumanoidRootPart.Size = Vector3.new(50,50,50)
								topos(v.HumanoidRootPart.CFrame * CFrame.new(0,30,0))
								game:GetService'VirtualUser':CaptureController()
								game:GetService'VirtualUser':Button1Down(Vector2.new(1280, 672))
							until not _G.Auto_Kill_Law or v.Humanoid.Health <= 0 or not v.Parent
						end
					end
				end 
			end)
		end
	end
end)
end
 
 DevilFruit:Seperator(" Sniper ")
 
 FruitList = {
  "Bomb-Bomb",
  "Spike-Spike",
  "Chop-Chop",
  "Spring-Spring",
  "Kilo-Kilo",
  "Spin-Spin",
  "Bird: Falcon",
  "Smoke-Smoke",
  "Flame-Flame",
  "Ice-Ice",
  "Sand-Sand",
  "Dark-Dark",
  "Revive-Revive",
  "Diamond-Diamond",
  "Light-Light",
  "Love-Love",
  "Rubber-Rubber",
  "Barrier-Barrier",
  "Magma-Magma",
  "Door-Door",
  "Quake-Quake",
  "Human-Human: Buddha",
  "String-String",
  "Bird-Bird: Phoenix",
  "Rumble-Rumble",
  "Paw-Paw",
  "Gravity-Gravity",
  "Dough-Dough",
  "Venom-Venom",
  "Shadow-Shadow",
  "Control-Control",
  "Soul-Soul",
  "Dragon-Dragon"
 }
 
 _G.SelectFruit = ""
 DevilFruit:Dropdown("Select Fruits Sniper",FruitList,function(value)
  _G.SelectFruit = value
  end)
 
 DevilFruit:Toggle("Auto Buy Fruit Sniper",_G.AutoBuyFruitSniper,function(value)
  _G.AutoBuyFruitSniper = value
  end)
 
 DevilFruit:Seperator(" Others ")
 
 DevilFruit:Dropdown("Select Fruits Eat",FruitList,function(value)
  _G.SelectFruitEat = value
  end)
 
 DevilFruit:Toggle("Auto Eat Fruit",_G.AutoEatFruit,function(value)
  _G.AutoEatFruit = value
  end)
 
 spawn(function()
  pcall(function()
   while wait(.1) do
   if _G.AutoEatFruit then
   game:GetService("Players").LocalPlayer.Character:FindFirstChild(_G.SelectFruitEat).EatRemote:InvokeServer()
   end
   end
   end)
 end)

 
 spawn(function()
  pcall(function()
   while wait(.1) do
   if _G.AutoBuyFruitSniper then
   game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("GetFruits")
   game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("PurchaseRawFruit",_G.SelectFruit)
   end
   end
   end)
  end)
 
 DevilFruit:Toggle("Auto Random Fruit",_G.Random_Auto,function(value)
  _G.Random_Auto = value
  end)
 
 spawn(function()
  pcall(function()
   while wait(.1) do
   if _G.Random_Auto then
   game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("Cousin","Buy")
   end
   end
   end)
  end)
 
 DevilFruit:Button("Random Fruit",function()
  game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("Cousin","Buy")
  end)
 
 
 DevilFruit:Toggle("Auto Drop Fruit",_G.DropFruit,function(value)
  _G.DropFruit = value
  end)
 
 spawn(function()
  while wait() do
  if _G.DropFruit then
  pcall(function()
   for i,v in pairs(game:GetService("Players").LocalPlayer.Backpack:GetChildren()) do
   if string.find(v.Name, "Fruit") then
   Equipgui(v.Name)
   wait(.1)
   if game:GetService("Players").LocalPlayer.PlayerGui.Main.Dialogue.Visible == true then
   game:GetService("Players").LocalPlayer.PlayerGui.Main.Dialogue.Visible = false
   end
   Equipgui(v.Name)
   game:GetService("Players").LocalPlayer.Character:FindFirstChild(SelectFruit).EatRemote:InvokeServer("Drop")
   end
   end
   for i,v in pairs(game:GetService("Players").LocalPlayer.Character:GetChildren()) do
   if string.find(v.Name, "Fruit") then
   Equipgui(v.Name)
   wait(.1)
   if game:GetService("Players").LocalPlayer.PlayerGui.Main.Dialogue.Visible == true then
   game:GetService("Players").LocalPlayer.PlayerGui.Main.Dialogue.Visible = false
   end
   Equipgui(v.Name)
   game:GetService("Players").LocalPlayer.Character:FindFirstChild(SelectFruit).EatRemote:InvokeServer("Drop")
   end
   end
   end)
  end
  end
  end)
 
 DevilFruit:Toggle("Auto Store Fruit",_G.AutoStoreFruit,function(value)
  _G.AutoStoreFruit = value
  end)
 
 		spawn(function()
			while task.wait() do
				if _G.AutoStoreFruit then
					pcall(function()
						for i,v in pairs(Fruit) do
						for x,y in pairs(game.Players.LocalPlayer.Backpack:GetChildren()) do
							if string.find(y.Name,"Fruit") then
								game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("StoreFruit",v,game.Players.LocalPlayer.Backpack[y.Name])
							end
						end
						end
					end)
				end
			end
		end)
 
 
 DevilFruit:Toggle("Grab Fruit",_G.BringFruit,function(value)
  _G.BringFruit = value
  pcall(function()
   while _G.BringFruit do wait(.1)
   for i,v in pairs(game:GetService("Workspace"):GetChildren()) do
   if v:IsA("Tool") then
   local OldCFrame = game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame
   game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame = v.Handle.CFrame * CFrame.new(0,0,8)
   v.Handle.CFrame = game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame
   wait(.1)
   game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame = OldCFrame
   end
   end
   end
   end)
 end)
 
 DevilFruit:Toggle("Teleport To Spawn Fruit",false,function(value)
 _G.Grabfruit = value
end)

spawn(function()
			while wait(.1) do
				if _G.Grabfruit then
					for i,v in pairs(game.Workspace:GetChildren()) do
						if string.find(v.Name, "Fruit") then
							game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = v.Handle.CFrame
						end
					end
				end
end
end)
 DevilFruit:Toggle("Bring All Fruit 75% Kick System",_G.BringFruitBF,function(value)
  _G.BringFruitBF = value
  end)
 
 spawn(function()
  while wait() do
  if _G.BringFruitBF then
  pcall(function()
   for i,v in pairs(game.Workspace:GetChildren()) do
   if v:IsA("Tool") then
   v.Handle.CFrame = game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame
   end
   end
   end)
  end
  end
 end)
 
 function isnil(thing)
 return (thing == nil)
 end
 local function round(n)
 return math.floor(tonumber(n) + 0.5)
 end
 Number = math.random(1, 1000000)
 function UpdateEspPlayer()
 for i,v in pairs(game:GetService'Players':GetChildren()) do
 pcall(function()
  if not isnil(v.Character) then
  if ESPPlayer then
  if not isnil(v.Character.Head) and not v.Character.Head:FindFirstChild('NameEsp'..Number) then
  local bill = Instance.new('BillboardGui',v.Character.Head)
  bill.Name = 'NameEsp'..Number
  bill.ExtentsOffset = Vector3.new(0, 1, 0)
  bill.Size = UDim2.new(1,200,1,30)
  bill.Adornee = v.Character.Head
  bill.AlwaysOnTop = true
  local name = Instance.new('TextLabel',bill)
  name.Font = "Code"
  name.FontSize = "Size14"
  name.TextWrapped = true
  name.Text = (v.Name ..' \n'.. round((game:GetService('Players').LocalPlayer.Character.Head.Position - v.Character.Head.Position).Magnitude/3) ..' M')
  name.Size = UDim2.new(1,0,1,0)
  name.TextYAlignment = 'Top'
  name.BackgroundTransparency = 1
  name.TextStrokeTransparency = 0.5
  if v.Team == game.Players.LocalPlayer.Team then
  name.TextColor3 = Color3.new(0,255,0)
  else
   name.TextColor3 = Color3.new(255,0,0)
  end
  else
   v.Character.Head['NameEsp'..Number].TextLabel.Text = (v.Name ..'  '.. round((game:GetService('Players').LocalPlayer.Character.Head.Position - v.Character.Head.Position).Magnitude/3) ..' M\nHealth : ' .. round(v.Character.Humanoid.Health*100/v.Character.Humanoid.MaxHealth) .. '%')
  end
  else
   if v.Character.Head:FindFirstChild('NameEsp'..Number) then
  v.Character.Head:FindFirstChild('NameEsp'..Number):Destroy()
  end
  end
  end
  end)
 end
 end

function UpdateIslandESP()
 for i,v in pairs(game:GetService("Workspace")["_WorldOrigin"].Locations:GetChildren()) do
 pcall(function()
  if IslandESP then
  if v.Name ~= "Sea" then
  if not v:FindFirstChild('NameEsp') then
  local bill = Instance.new('BillboardGui',v)
  bill.Name = 'NameEsp'
  bill.ExtentsOffset = Vector3.new(0, 1, 0)
  bill.Size = UDim2.new(1,200,1,30)
  bill.Adornee = v
  bill.AlwaysOnTop = true
  local name = Instance.new('TextLabel',bill)
  name.Font = "Code"
  name.FontSize = "Size14"
  name.TextWrapped = true
  name.Size = UDim2.new(1,0,1,0)
  name.TextYAlignment = 'Top'
  name.BackgroundTransparency = 1
  name.TextStrokeTransparency = 0.5
  name.TextColor3 = Color3.fromRGB(80, 245, 245)
  else
   v['NameEsp'].TextLabel.Text = (v.Name ..'   \n'.. round((game:GetService('Players').LocalPlayer.Character.Head.Position - v.Position).Magnitude/3) ..' M')
  end
  end
  else
   if v:FindFirstChild('NameEsp') then
  v:FindFirstChild('NameEsp'):Destroy()
  end
  end
  end)
 end
 end
 
 function UpdateChestEsp()
 for i,v in pairs(game.Workspace:GetChildren()) do
 pcall(function()
  if v.Name == "Chest1" or v.Name == "Chest2" or v.Name == "Chest3" then
  if ChestESP then
  if (v.Name == "Chest1" or v.Name == "Chest2" or v.Name == "Chest3") and (v.Position - game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 60000 then
  if not v:FindFirstChild("ChestESP"..Number) then
  local Bb = Instance.new("BillboardGui", v)
  Bb.Name = "ChestESP"..Number
  Bb.ExtentsOffset = Vector3.new(0, 1, 0)
  Bb.Size = UDim2.new(1, 200, 1, 30)
  Bb.Adornee = v
  Bb.AlwaysOnTop = true
  local Textlb = Instance.new("TextLabel", Bb)
  Textlb.Font = "Code"
  Textlb.FontSize = "Size14"
  Textlb.Size = UDim2.new(1,0,1,0)
  Textlb.BackgroundTransparency = 1
  Textlb.TextStrokeTransparency = 0.5
  if v.Name == "Chest1" then
  Textlb.TextColor3 = Color3.fromRGB(174, 123, 47)
  Textlb.Text = "Bronze Chest".."\n"..math.round((v.Position - game:GetService('Players').LocalPlayer.Character.HumanoidRootPart.Position).Magnitude/3).." m."
  end
  if v.Name == "Chest2" then
  Textlb.TextColor3 = Color3.fromRGB(255, 255, 127)
  Textlb.Text = "Gold Chest".."\n"..math.round((v.Position - game:GetService('Players').LocalPlayer.Character.HumanoidRootPart.Position).Magnitude/3).." m."
  end
  if v.Name == "Chest3" then
  Textlb.Text = "Diamond Chest".."\n"..math.round((v.Position - game:GetService('Players').LocalPlayer.Character.HumanoidRootPart.Position).Magnitude/3).." m."
  Textlb.TextColor3 = Color3.fromRGB(5, 243, 255)
  end
  else
   v["ChestESP"..Number].TextLabel.Text = v.Name.."\n"..math.round((v.Position - game:GetService('Players').LocalPlayer.Character.HumanoidRootPart.Position).Magnitude/3).." m."
  end
  end
  else
   if v:FindFirstChild("ChestESP"..Number) then
  v:FindFirstChild("ChestESP"..Number):Destroy()
  end
  end
  end
  end)
 end
 end
 
 function UpdateBfEsp()
 for i,v in pairs(game:GetService("Workspace"):GetChildren()) do
 pcall(function()
  if DevilFruitESP then
  if string.find(v.Name, "Fruit") then
  if not v.Handle:FindFirstChild('NameEsp'..Number) then
  local bill = Instance.new('BillboardGui',v.Handle)
  bill.Name = 'NameEsp'..Number
  bill.ExtentsOffset = Vector3.new(0, 1, 0)
  bill.Size = UDim2.new(1,200,1,30)
  bill.Adornee = v.Handle
  bill.AlwaysOnTop = true
  local name = Instance.new('TextLabel',bill)
  name.Font = "Code"
  name.FontSize = "Size14"
  name.TextWrapped = true
  name.Size = UDim2.new(1,0,1,0)
  name.TextYAlignment = 'Top'
  name.BackgroundTransparency = 1
  name.TextStrokeTransparency = 0.5
  name.TextColor3 = Color3.fromRGB(255, 0, 0)
  name.Text = (v.Name ..' \n'.. round((game:GetService('Players').LocalPlayer.Character.Head.Position - v.Handle.Position).Magnitude/3) ..' M')
  else
   v.Handle['NameEsp'..Number].TextLabel.Text = (v.Name ..'   \n'.. round((game:GetService('Players').LocalPlayer.Character.Head.Position - v.Handle.Position).Magnitude/3) ..' M')
  end
  end
  else
   if v.Handle:FindFirstChild('NameEsp'..Number) then
  v.Handle:FindFirstChild('NameEsp'..Number):Destroy()
  end
  end
  end)
 end
 end
 
 function UpdateFlowerEsp()
 for i,v in pairs(game:GetService("Workspace"):GetChildren()) do
 pcall(function()
  if v.Name == "Flower2" or v.Name == "Flower1" then
  if FlowerESP then
  if not v:FindFirstChild('NameEsp'..Number) then
  local bill = Instance.new('BillboardGui',v)
  bill.Name = 'NameEsp'..Number
  bill.ExtentsOffset = Vector3.new(0, 1, 0)
  bill.Size = UDim2.new(1,200,1,30)
  bill.Adornee = v
  bill.AlwaysOnTop = true
  local name = Instance.new('TextLabel',bill)
  name.Font = "Code"
  name.FontSize = "Size14"
  name.TextWrapped = true
  name.Size = UDim2.new(1,0,1,0)
  name.TextYAlignment = 'Top'
  name.BackgroundTransparency = 1
  name.TextStrokeTransparency = 0.5
  name.TextColor3 = Color3.fromRGB(255, 0, 0)
  if v.Name == "Flower1" then
  name.Text = ("Blue Flower" ..' \n'.. round((game:GetService('Players').LocalPlayer.Character.Head.Position - v.Position).Magnitude/3) ..' M')
  name.TextColor3 = Color3.fromRGB(255, 0, 0)
  end
  if v.Name == "Flower2" then
  name.Text = ("Red Flower" ..' \n'.. round((game:GetService('Players').LocalPlayer.Character.Head.Position - v.Position).Magnitude/3) ..' M')
  name.TextColor3 = Color3.fromRGB(255, 0, 0)
  end
  else
   v['NameEsp'..Number].TextLabel.Text = (v.Name ..'   \n'.. round((game:GetService('Players').LocalPlayer.Character.Head.Position - v.Position).Magnitude/3) ..' M')
  end
  else
   if v:FindFirstChild('NameEsp'..Number) then
  v:FindFirstChild('NameEsp'..Number):Destroy()
  end
  end
  end
  end)
 end
 end
 
 DevilFruit:Seperator(" ESP ")
  
if World2 then
		DevilFruit:Button("TP Flower Red",function()
			for i,v in pairs(game.Workspace:GetDescendants()) do
				if v.Name == "Flower2" then
				    topos(v.CFrame)
				end
			end
		end)

		DevilFruit:Button("TP Flower Blue",function()
			for i,v in pairs(game.Workspace:GetDescendants()) do
				if v.Name == "Flower1" then
					topos(v.CFrame)
				end
			end
		end)
	end

	function isnil(thing)
		return (thing == nil)
	end
	local function round(n)
		return math.floor(tonumber(n) + 0.5)
	end
	Number = math.random(1, 1000000)
	function UpdatePlayerChams()
		for i,v in pairs(game:GetService'Players':GetChildren()) do
			pcall(function()
				if not isnil(v.Character) then
					if ESPPlayer then
						if not isnil(v.Character.Head) and not v.Character.Head:FindFirstChild('NameEsp'..Number) then
							local bill = Instance.new('BillboardGui',v.Character.Head)
							bill.Name = 'NameEsp'..Number
							bill.ExtentsOffset = Vector3.new(0, 1, 0)
							bill.Size = UDim2.new(1,200,1,30)
							bill.Adornee = v.Character.Head
							bill.AlwaysOnTop = true
							local name = Instance.new('TextLabel',bill)
							name.Font = "GothamBold"
							name.FontSize = "Size14"
							name.TextWrapped = true
							name.Text = (v.Name ..' \n'.. round((game:GetService('Players').LocalPlayer.Character.Head.Position - v.Character.Head.Position).Magnitude/3) ..' M')
							name.Size = UDim2.new(1,0,1,0)
							name.TextYAlignment = 'Top'
							name.BackgroundTransparency = 1
							name.TextStrokeTransparency = 0.5
							if v.Team == game.Players.LocalPlayer.Team then
								name.TextColor3 = Color3.new(0,255,0)
							else
								name.TextColor3 = Color3.new(255,0,0)
							end
						else
							v.Character.Head['NameEsp'..Number].TextLabel.Text = (v.Name ..'   \n'.. round((game:GetService('Players').LocalPlayer.Character.Head.Position - v.Character.Head.Position).Magnitude/3) ..' M')
						end
					else
						if v.Character.Head:FindFirstChild('NameEsp'..Number) then
							v.Character.Head:FindFirstChild('NameEsp'..Number):Destroy()
						end
					end
				end
			end)
		end
	end
	function UpdateChestChams() 
		for i,v in pairs(game.Workspace:GetChildren()) do
			pcall(function()
				if string.find(v.Name,"Chest") then
					if ChestESP then
						if string.find(v.Name,"Chest") then
							if not v:FindFirstChild('NameEsp'..Number) then
								local bill = Instance.new('BillboardGui',v)
								bill.Name = 'NameEsp'..Number
								bill.ExtentsOffset = Vector3.new(0, 1, 0)
								bill.Size = UDim2.new(1,200,1,30)
								bill.Adornee = v
								bill.AlwaysOnTop = true
								local name = Instance.new('TextLabel',bill)
								name.Font = "GothamBold"
								name.FontSize = "Size14"
								name.TextWrapped = true
								name.Size = UDim2.new(1,0,1,0)
								name.TextYAlignment = 'Top'
								name.BackgroundTransparency = 1
								name.TextStrokeTransparency = 0.5
								if v.Name == "Chest1" then
									name.TextColor3 = Color3.fromRGB(10, 224, 153)
									name.Text = ("Chest 1" ..' \n'.. round((game:GetService('Players').LocalPlayer.Character.Head.Position - v.Position).Magnitude/3) ..' M')
								end
								if v.Name == "Chest2" then
									name.TextColor3 = Color3.fromRGB(10, 224, 153)
									name.Text = ("Chest 2" ..' \n'.. round((game:GetService('Players').LocalPlayer.Character.Head.Position - v.Position).Magnitude/3) ..' M')
								end
								if v.Name == "Chest3" then
									name.TextColor3 = Color3.fromRGB(10, 224, 153)
									name.Text = ("Chest 3" ..' \n'.. round((game:GetService('Players').LocalPlayer.Character.Head.Position - v.Position).Magnitude/3) ..' M')
								end
							else
								v['NameEsp'..Number].TextLabel.Text = (v.Name ..'   \n'.. round((game:GetService('Players').LocalPlayer.Character.Head.Position - v.Position).Magnitude/3) ..' M')
							end
						end
					else
						if v:FindFirstChild('NameEsp'..Number) then
							v:FindFirstChild('NameEsp'..Number):Destroy()
						end
					end
				end
			end)
		end
	end
	function UpdateDevilChams() 
		for i,v in pairs(game.Workspace:GetChildren()) do
			pcall(function()
				if DevilFruitESP then
					if string.find(v.Name, "Fruit") then   
						if not v.Handle:FindFirstChild('NameEsp'..Number) then
							local bill = Instance.new('BillboardGui',v.Handle)
							bill.Name = 'NameEsp'..Number
							bill.ExtentsOffset = Vector3.new(0, 1, 0)
							bill.Size = UDim2.new(1,200,1,30)
							bill.Adornee = v.Handle
							bill.AlwaysOnTop = true
							local name = Instance.new('TextLabel',bill)
							name.Font = "GothamBold"
							name.FontSize = "Size14"
							name.TextWrapped = true
							name.Size = UDim2.new(1,0,1,0)
							name.TextYAlignment = 'Top'
							name.BackgroundTransparency = 1
							name.TextStrokeTransparency = 0.5
							name.TextColor3 = Color3.fromRGB(10, 224, 153)
							name.Text = (v.Name ..' \n'.. round((game:GetService('Players').LocalPlayer.Character.Head.Position - v.Handle.Position).Magnitude/3) ..' M')
						else
							v.Handle['NameEsp'..Number].TextLabel.Text = (v.Name ..'   \n'.. round((game:GetService('Players').LocalPlayer.Character.Head.Position - v.Handle.Position).Magnitude/3) ..' M')
						end
					end
				else
					if v.Handle:FindFirstChild('NameEsp'..Number) then
						v.Handle:FindFirstChild('NameEsp'..Number):Destroy()
					end
				end
			end)
		end
	end
	function UpdateFlowerChams() 
		for i,v in pairs(game.Workspace:GetChildren()) do
			pcall(function()
				if v.Name == "Flower2" or v.Name == "Flower1" then
					if FlowerESP then 
						if not v:FindFirstChild('NameEsp'..Number) then
							local bill = Instance.new('BillboardGui',v)
							bill.Name = 'NameEsp'..Number
							bill.ExtentsOffset = Vector3.new(0, 1, 0)
							bill.Size = UDim2.new(1,200,1,30)
							bill.Adornee = v
							bill.AlwaysOnTop = true
							local name = Instance.new('TextLabel',bill)
							name.Font = "GothamBold"
							name.FontSize = "Size14"
							name.TextWrapped = true
							name.Size = UDim2.new(1,0,1,0)
							name.TextYAlignment = 'Top'
							name.BackgroundTransparency = 1
							name.TextStrokeTransparency = 0.5
							name.TextColor3 = Color3.fromRGB(10, 224, 153)
							if v.Name == "Flower1" then 
								name.Text = ("Blue Flower" ..' \n'.. round((game:GetService('Players').LocalPlayer.Character.Head.Position - v.Position).Magnitude/3) ..' M')
								name.TextColor3 = Color3.fromRGB(10, 224, 153)
							end
							if v.Name == "Flower2" then
								name.Text = ("Red Flower" ..' \n'.. round((game:GetService('Players').LocalPlayer.Character.Head.Position - v.Position).Magnitude/3) ..' M')
								name.TextColor3 = Color3.fromRGB(10, 224, 153)
							end
						else
							v['NameEsp'..Number].TextLabel.Text = (v.Name ..'   \n'.. round((game:GetService('Players').LocalPlayer.Character.Head.Position - v.Position).Magnitude/3) ..' M')
						end
					else
						if v:FindFirstChild('NameEsp'..Number) then
							v:FindFirstChild('NameEsp'..Number):Destroy()
						end
					end
				end   
			end)
		end
	end
	DevilFruit:Toggle("ESP Player",false,function(a)
		ESPPlayer = a
		while ESPPlayer do wait()
			UpdatePlayerChams()
		end
	end)
	DevilFruit:Toggle("ESP Chest",false,function(a)
		ChestESP = a
		while ChestESP do wait()
			UpdateChestChams() 
		end
	end)
	DevilFruit:Toggle("ESP Devil Fruit",false,function(a)
		DevilFruitESP = a
		while DevilFruitESP do wait()
			UpdateDevilChams() 
		end
	end)
	DevilFruit:Toggle("ESP Flower",false,function(a)
		FlowerESP = a
		while FlowerESP do wait()
			UpdateFlowerChams() 
		end
	end)
	
 
 Shop:Seperator(" Abilities ")
 
 Shop:Button("Buy Geppo",function()
  game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyHaki","Geppo")
  end)
 
 Shop:Button("Buy Buso Haki",function()
  game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyHaki","Buso")
  end)
 
 Shop:Button("Buy Soru",function()
  game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyHaki","Soru")
  end)
 
 Shop:Button("Buy Observation(Ken) Haki",function()
  game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("KenTalk","Buy")
  end)
 
 Shop:Seperator(" Fighting Style ")
 
 Shop:Button("Buy Black Leg",function()
  game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyBlackLeg")
  end)
 
 Shop:Button("Buy Electro",function()
  game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyElectro")
  end)
 
 Shop:Button("Buy Fishman Karate",function()
  game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyFishmanKarate")
  end)
 
 Shop:Button("Buy Dragon Claw",function()
  game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BlackbeardReward","DragonClaw","1")
  game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BlackbeardReward","DragonClaw","2")
  end)
 
 Shop:Button("Buy Superhuman",function()
  game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuySuperhuman")
  end)
 
 Shop:Button("Buy Death Step",function()
  game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyDeathStep")
  end)
 
 Shop:Button("Buy Sharkman Karate",function()
  game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuySharkmanKarate",true)
  game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuySharkmanKarate")
  end)
 
 Shop:Button("Buy Electric Claw",function()
  game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyElectricClaw")
  end)
 
 Shop:Button("Buy Dragon Talon",function()
  game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyDragonTalon")
  end)
 Shop:Button("Buy GodHuman",function()
  game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyGodhuman")
  end)
 -----Shop----------------
 Shop:Seperator(" Accessory ")
 
 Shop:Button("Tomoe Ring",function()
  game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyItem","Tomoe Ring")
  end)
 
 Shop:Button("Black Cape",function()
  game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyItem","Black Cape")
  end)
 
 Shop:Button("Swordsman Hat",function()
  game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyItem","Swordsman Hat")
  end)
 
 Shop:Seperator(" Sword ")
 
 Shop:Button("Cutlass",function()
  game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyItem","Cutlass")
  end)
 
 Shop:Button("Katana",function()
  game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyItem","Katana")
  end)
 
 Shop:Button("Iron Mace",function()
  game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyItem","Iron Mace")
  end)
 
 Shop:Button("Duel Katana",function()
  game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyItem","Duel Katana")
  end)
 
 Shop:Button("Triple Katana", function()
  game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyItem","Triple Katana")
  end)
 
 Shop:Button("Pipe",function()
  game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyItem","Pipe")
  end)
 
 Shop:Button("Dual Headed Blade",function()
  game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyItem","Dual-Headed Blade")
  end)
 
 Shop:Button("Bisento",function()
  game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyItem","Bisento")
  end)
 
 Shop:Button("Soul Cane",function()
  game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyItem","Soul Cane")
  end)
 
 Shop:Seperator(" Gun ")
 
 Shop:Button("Slingshot",function()
  game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyItem","Slingshot")
  end)
 
 Shop:Button("Musket",function()
  game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyItem","Musket")
  end)
 
 Shop:Button("Flintlock",function()
  game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyItem","Flintlock")
  end)
 
 Shop:Button("Refined Flintlock",function()
  game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyItem","Refined Flintlock")
  end)
 
 Shop:Button("Cannon",function()
  game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyItem","Cannon")
  end)
 
 Shop:Button("Kabucha",function()
  game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BlackbeardReward","Slingshot","1")
  game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BlackbeardReward","Slingshot","2")
 end)
 
 Shop:Button("Race Reroll",function()
  game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("Bones","Buy",1,3)
 end)
 
 Misc:Seperator(" Joins ")
 
 Misc:Button("Join Pirates Team",function()
 		local args = {
			[1] = "SetTeam",
			[2] = "Pirates"
		}
		game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args)) 
		local args = {
			[1] = "BartiloQuestProgress"
		}
		game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
end)
 

Misc:Button("Join Marines Team",function()
 local args = {
			[1] = "SetTeam",
			[2] = "Marines"
		}
		game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
		local args = {
			[1] = "BartiloQuestProgress"
		}
		game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
end)


Misc:Button("Rejoin",function()
 local ts = game:GetService("TeleportService")
		local p = game:GetService("Players").LocalPlayer
		ts:Teleport(game.PlaceId, p)
end)

Misc:Button("Sever Hop",function()
 hop()
end)
    Misc:Button("Hop To Lower Player",function()
        local maxplayers, gamelink, goodserver, data_table = math.huge, "https://games.roblox.com/v1/games/" .. game.PlaceId .. "/servers/Public?sortOrder=Asc&limit=100"
		if not _G.FailedServerID then _G.FailedServerID = {} end

		local function serversearch()
			data_table = game:GetService"HttpService":JSONDecode(game:HttpGetAsync(gamelink))
			for _, v in pairs(data_table.data) do
				pcall(function()
					if type(v) == "table" and v.id and v.playing and tonumber(maxplayers) > tonumber(v.playing) and not table.find(_G.FailedServerID, v.id) then
						maxplayers = v.playing
						goodserver = v.id
					end
				end)
			end
		end

		function getservers()
			pcall(serversearch)
			for i, v in pairs(data_table) do
				if i == "nextPageCursor" then
					if gamelink:find"&cursor=" then
						local a = gamelink:find"&cursor="
						local b = gamelink:sub(a)
						gamelink = gamelink:gsub(b, "")
					end
					gamelink = gamelink .. "&cursor=" .. v
					pcall(getservers)
				end
			end
		end

		pcall(getservers)
		wait()
		if goodserver == game.JobId or maxplayers == #game:GetService"Players":GetChildren() - 1 then
		end
		table.insert(_G.FailedServerID, goodserver)
		game:GetService"TeleportService":TeleportToPlaceInstance(game.PlaceId, goodserver)
    end)

Misc:Seperator(" Open Menu ")

Misc:Button("Inventory",function()
 game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("getInventoryguis")
		game.Players.localPlayer.PlayerGui.Main.Inventory.Visible = true
end)

Misc:Button("Devil Fruit Shop",function()
 local args = {
			[1] = "GetFruits"
		}
		game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
		game.Players.localPlayer.PlayerGui.Main.FruitShop.Visible = true
end)


Misc:Button("Title Name",function()
 local args = {
			[1] = "getTitles"
		}
		game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
		game.Players.localPlayer.PlayerGui.Main.Titles.Visible = true
end)


Misc:Button("Color Haki",function()
 game.Players.localPlayer.PlayerGui.Main.Colors.Visible = true
end)

Misc:Seperator(" Codes ")
    
    
local x2Code = {
 "EXP_5B",
 "CONTROL",
 "UPDATE11",
 "XMASEXP",
 "1BILLION",
 "ShutDownFix2",
 "UPD14",
 "STRAWHATMAINE",
 "TantaiGaming",
 "Colosseum",
 "Axiore",
 "Sub2Daigrock",
 "Sky Island 3",
 "Sub2OfficialNoobie",
 "SUB2NOOBMASTER123",
 "THEGREATACE",
 "Fountain City",
 "BIGNEWS",
 "FUDD10",
 "SUB2GAMERROBOT_EXP1",
 "UPD15",
 "2BILLION",
 "UPD16",
 "3BVISITS",
 "fudd10_v2",
 "Starcodeheo",
 "Magicbus",
 "JCWK",
 "Bluxxy",
 "Sub2Fer999",
 "Enyu_is_Pro"
}
    
    Misc:Button("Redeem All Codes",function()
        function RedeemCode(value)
            game:GetService("ReplicatedStorage").Remotes.Redeem:InvokeServer(value)
        end
        for i,v in pairs(x2Code) do
            RedeemCode(v)
        end
    end)
    
    Misc:Dropdown("Selected Codes",{"1MLIKES_RESET","THIRDSEA","SUB2GAMERROBOT_RESET1","SUB2UNCLEKIZARU"},function(value)
        _G.CodeSelect = value
    end)
    
    Misc:Button("Redeem Code",function()
        game:GetService("ReplicatedStorage").Remotes.Redeem:InvokeServer(_G.CodeSelect)
    end)


Misc:Seperator(" Player Misc ")
    
    
    Misc:Dropdown("Select Haki State",{"State 0","State 1","State 2","State 3","State 4","State 5"},function(value)
        _G.SelectStateHaki = value
    end)
    
    Misc:Button("Change Buso Haki State",function()
        if _G.SelectStateHaki == "State 0" then
            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("ChangeBusoStage",0)
        elseif _G.SelectStateHaki == "State 1" then
            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("ChangeBusoStage",1)
        elseif _G.SelectStateHaki == "State 2" then
            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("ChangeBusoStage",2)
        elseif _G.SelectStateHaki == "State 3" then
            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("ChangeBusoStage",3)
        elseif _G.SelectStateHaki == "State 4" then
            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("ChangeBusoStage",4)
        elseif _G.SelectStateHaki == "State 5" then
            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("ChangeBusoStage",5)
        end
    end)

Misc:Toggle("No Clip",_G.No_clip,function(value)
 _G.No_clip = value
end)


spawn(function()
    pcall(function()
        game:GetService("RunService").Stepped:Connect(function()
            if _G.No_clip then
                for _, v in pairs(game.Players.LocalPlayer.Character:GetDescendants()) do
                    if v:IsA("BasePart") then
                        v.CanCollide = false    
                    end
                end
            end
        end)
    end)
end)

  function NoDodgeCool()
        if nododgecool then
            for i,v in next, getgc() do
                if game:GetService("Players").LocalPlayer.Character.Dodge then
                    if typeof(v) == "function" and getfenv(v).script == game:GetService("Players").LocalPlayer.Character.Dodge then
                        for i2,v2 in next, getupvalues(v) do
                            if tostring(v2) == "0.1" then
                            repeat wait(.1)
                                setupvalue(v,i2,0)
                            until not nododgecool
                            end
                        end
                    end
                end
            end
        end
  end
   
    
    local LocalPlayer = game:GetService'Players'.LocalPlayer
    local originalstam = LocalPlayer.Character.Energy.Value
    function infinitestam()
        LocalPlayer.Character.Energy.Changed:connect(function()
            if InfiniteEnergy then
                LocalPlayer.Character.Energy.Value = originalstam
            end 
        end)
    end
    
    spawn(function()
        pcall(function()
            while wait(.1) do
                if InfiniteEnergy then
                    wait(0.1)
                    originalstam = LocalPlayer.Character.Energy.Value
                    infinitestam()
                end
            end
        end)
    end)

Misc:Toggle("Dodge No Cooldown",false,function(value)
        nododgecool = value
        NoDodgeCool()
    end)
    
    Misc:Toggle("Auto Active Race",_G.AutoAgility,function(value)
        _G.AutoAgility = value
    end)
    
    spawn(function()
        pcall(function()
            while wait() do
                if _G.AutoAgility then
                    game:GetService("ReplicatedStorage").Remotes.CommE:FireServer("ActivateAbility")
                end
            end
        end)
    end)
    
    Misc:Toggle("Infinite Ability",false,function(value)
        InfAbility = value
        if value == false then
            game:GetService("Players").LocalPlayer.Character.HumanoidRootPart:FindFirstChild("Agility"):Destroy()
        end
    end)
    
    spawn(function()
        while wait() do
            if InfAbility then
                InfAb()
            end
        end
    end)
    
    Misc:Toggle("Infinite Obversation Range",getgenv().InfiniteObRange,function(value)
        getgenv().InfiniteObRange = value
        local VS = game:GetService("Players").LocalPlayer.VisionRadius.Value
        while getgenv().InfiniteObRange do
            wait()
            local player = game:GetService("Players").LocalPlayer
            local char = player.Character
            local VisionRadius = player.VisionRadius
            if player then
                if char.Humanoid.Health <= 0 then 
                    wait(5) 
                end
                VisionRadius.Value = math.huge
            elseif getgenv().InfiniteObRange == false and player then
                VisionRadius.Value = VS
            end
        end
    end)
    
    Misc:Toggle("Infinite Geppo",getgenv().InfGeppo,function(value)
        getgenv().InfGeppo = value
    end)
    
    spawn(function()
        while wait() do
            pcall(function()
                if getgenv().InfGeppo then
                    for i,v in next, getgc() do
                        if game:GetService("Players").LocalPlayer.Character.Geppo then
                            if typeof(v) == "function" and getfenv(v).script == game:GetService("Players").LocalPlayer.Character.Geppo then
                                for i2,v2 in next, getupvalues(v) do
                                    if tostring(i2) == "9" then
                                        repeat wait(.1)
                                            setupvalue(v,i2,0)
                                        until not getgenv().InfGeppo or game:GetService("Players").LocalPlayer.Character.Humanoid.Health <= 0 
                                    end
                                end
                            end
                        end
                    end
                end
            end)
        end
    end)
    
    Misc:Toggle("Infinite Soru",getgenv().InfSoru,function(value)
        getgenv().InfSoru = value
    end)
    
    spawn(function()
        while wait() do
            pcall(function()
                if getgenv().InfSoru and game:GetService("Players").LocalPlayer.Character:FindFirstChild("HumanoidRootPart") ~= nil  then
                    for i,v in next, getgc() do
                        if game:GetService("Players").LocalPlayer.Character.Soru then
                            if typeof(v) == "function" and getfenv(v).script == game:GetService("Players").LocalPlayer.Character.Soru then
                                for i2,v2 in next, getupvalues(v) do
                                    if typeof(v2) == "table" then
                                        repeat wait(.1)
                                            v2.LastUse = 0
                                        until not getgenv().InfSoru or game:GetService("Players").LocalPlayer.Character.Humanoid.Health <= 0
                                    end
                                end
                            end
                        end
                    end
                end
            end)
        end
    end)
    
    Misc:Toggle("Walk on Water",true,function(value)
        _G.WalkWater = value
    end)
    
    if World2 then
		Misc:Button("Remove Lava",function()
			for i,v in pairs(game.Workspace:GetDescendants()) do
				if v.Name == "Lava" then   
					v:Destroy()
				end
			end
			for i,v in pairs(game.ReplicatedStorage:GetDescendants()) do
				if v.Name == "Lava" then   
					v:Destroy()
				end
			end
		end)
		end
    
spawn(function()
			while task.wait() do
				pcall(function()
					if _G.WalkWater then
						game:GetService("Workspace").Map["WaterBase-Plane"].Size = Vector3.new(1000,112,1000)
					else
						game:GetService("Workspace").Map["WaterBase-Plane"].Size = Vector3.new(1000,80,1000)
					end
				end)
			end
		end)
    Misc:Toggle("Fly",false,function(value)
        Fly = value
    end)
    
    spawn(function()
        while wait() do
            pcall(function()
                if Fly then
                    fly()
                end
            end)
        end
    end)
    
        
    Misc:Button("Unlock FPS",function()
        setfpscap(100)
    end)
Misc:Button("Invisible",function()
        game:GetService("Players").LocalPlayer.Character.LowerTorso:Destroy()
    end)


Op:Label("Name : "..game.Players.LocalPlayer.Name)



if W then
Op:Label("World : 1")
end

if W2 then
Op:Label("World : 2")
end

if W3 then
Op:Label("World : 3")
end

Op:Label("Race : "..game:GetService("Players").LocalPlayer.Data.Race.Value)

Op:Label("Fruit : "..game.Players.LocalPlayer.Data.DevilFruit.Value)

Op:Label("Level : "..game.Players.localPlayer.Data.Level.Value)

Op:Label("Bounty : "..game:GetService("Players").LocalPlayer.leaderstats["Bounty/Honor"].Value)

Op:Seperator("\\\\\  Sword  //")

local Saber = Op:Label("❌: Saber")
local Rengoku = Op:Label("❌: Rengoku")
local Midnight_Blade = Op:Label("❌: Midnight Blade")
local Dragon_Trident = Op:Label("❌: Dragon Trident")
local Yama = Op:Label("❌: Yama")
local Buddy_Sword = Op:Label("❌: Buddy Sword")
local Canvander = Op:Label("❌: Canvander")
local Twin_Hooks = Op:Label("❌: Twin Hooks")
local Spikey_Trident = Op:Label("❌: Spikey Trident")
local Hallow_Scythe = Op:Label("❌: Hallow Scythe")
local Dark_Dagger = Op:Label("❌: Dark Dagger")
local Tushita = Op:Label("❌: Tushita")

spawn(function()
    while task.wait() do
        pcall(function()
            for i,v in pairs(game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("getInventoryguis")) do
                if v.Name == "Saber" then
                    Saber:Set("✅: Saber")
                end
                if v.Name == "Rengoku" then
                    Rengoku:Set("✅: Rengoku")
                end
                if v.Name == "Midnight Blade" then
                    Midnight_Blade:Set("✅: Midnight Blade")
                end
                if v.Name == "Dragon Trident" then
                    Dragon_Trident:Set("✅: Dragon Trident")
                end
                if v.Name == "Yama" then
                    Yama:Set("✅: Yama")
                end
                if v.Name == "Buddy Sword" then
                    Buddy_Sword:Set("✅: Buddy Sword")
                end
                if v.Name == "Canvander" then
                    Canvander:Set("✅: Canvander")
                end
                if v.Name == "Twin Hooks" then
                    Twin_Hooks:Set("✅: Twin Hooks")
                end
                if v.Name == "Spikey Trident" then
                    Spikey_Trident:Set("✅: Spikey Trident")
                end
                if v.Name == "Hallow Scythe" then
                    Hallow_Scythe:Set("✅: Hallow Scythe")
                end
                if v.Name == "Dark Dagger" then
                    Dark_Dagger:Set("✅: Dark Dagger")
                end
                if v.Name == "Tushita" then
                    Tushita:Set("✅: Tushita")
                 end
            end
        end)
    end
end)

Op:Seperator("\\\\\  Quest  //")

local Bartilo_Quest = Op:Label("❌: Bartilo Quest")
local Don_Swan_Quest = Op:Label("❌: Don Swan Quest")
local Kill_Don_Swan = Op:Label("❌: Kill Don Swan")

spawn(function()
    while task.wait() do
        if game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BartiloQuestProgress","Bartilo") == 3 then
            Bartilo_Quest:Set("✅: Bartilo Quest")
        end

        if game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("GetUnlockables").FlamingoAccess == nil then
            --Nothing
        else
            Don_Swan_Quest:Set("✅: Don Swan Quest")
        end

        if game:GetService("ReplicatedStorage").Remotes["CommF_"]:InvokeServer("ZQuestProgress", "Check") == 1 then
            Kill_Don_Swan:Set("✅: Kill Don Swan")
        end
    end
end)

Op:Seperator("\\\\\  Sword Legendary  //")

local Shisui = Op:Label("❌: Shisui")
local Saddi = Op:Label("❌: Saddi")
local Wando = Op:Label("❌: Wando")
local True_Triple_Katana = Op:Label("❌: True Triple Katana")

spawn(function()
    while task.wait() do
        pcall(function()
            for i,v in pairs(game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("getInventoryguis")) do
                if v.Name == "Shisui" then
                    Shisui:Set("✅: Shisui")
                end
                if v.Name == "Saddi" then
                    Saddi:Set("✅: Saddi")
                end
                if v.Name == "Wando" then
                    Wando:Set("✅: Wando")
                end
                if v.Name == "True Triple Katana" then
                    True_Triple_Katana:Set("✅: True Triple Katana")
                end
            end
        end)
    end
end)

Op:Seperator("\\\\\  Melee  //")

local Superhuman = Op:Label("❌: Superhuman")
local Death_Step = Op:Label("❌: Death Step")
local Sharkman_Karate = Op:Label("❌: Sharkman Karate")
local Electric_Claw = Op:Label("❌: Electric Claw")
local Dragon_Talon = Op:Label("❌: Dragon Talon")
local God_Human = Op:Label("❌: God Human")

spawn(function()
    while task.wait() do
        if game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuySuperhuman",true) == 1 then
            Superhuman:Set("✅: Superhuman")
        end
        if game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyDeathStep",true) == 1 then
            Death_Step:Set("✅: Death Step")
        end
        if game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuySharkmanKarate",true) == 1 then
            Sharkman_Karate:Set("✅: Sharkman Karate")
        end
        if game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyElectricClaw",true) == 1 then
            Electric_Claw:Set("✅: Electric Claw")
        end
        if game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyDragonTalon",true) == 1 then
            Dragon_Talon:Set("✅: Dragon Talon")
        end
    end
end)

Op:Seperator("\\\\\  Gun  //")

local Kabu_cha = Op:Label("❌: Kabucha")
local Acidum_Rifle = Op:Label("❌: Acidum Rifle")
local Bizarre_Rifle = Op:Label("❌: Bizarre Rifle")

spawn(function()
    while task.wait() do
        pcall(function()
            for i,v in pairs(game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("getInventoryguis")) do
                if v.Name == "Kabucha" then
                    Kabu_cha:Set("✅: Kabucha")
                end
                if v.Name == "Acidum Rifle" then
                    Acidum_Rifle:Set("✅: Acidum Rifle")
                end
                if v.Name == "Bizarre Rifle" then
                    Bizarre_Rifle:Set("✅: Bizarre Rifle")
                end
            end
        end)
    end
end)



Op:Seperator("\\\\\  Accessory  //")

local Dark_Coat = Op:Label("❌: Dark Coat")
local Ghoul_Mask = Op:Label("❌: Ghoul Mask")
local Swan_Glass = Op:Label("❌: Swan Glass")
local Pale_Scarf = Op:Label("❌: Pale Scarf")
local Valkyrie_Helm = Op:Label("❌: Valkyrie Helm")


spawn(function()
    while task.wait() do
        pcall(function()
            for i,v in pairs(game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("getInventoryguis")) do
                if v.Name == "Saber" then
                    Dark_Coat:Set("✅: Dark Coat")
                end
                if v.Name == "Ghoul Mask" then
                    Ghoul_Mask:Set("✅: Ghoul Mask")
                end
                if v.Name == "Swan Glasses" then
                    Swan_Glass:Set("✅: Swan Glass")
                end
                if v.Name == "Pale Scarf" then
                    Pale_Scarf:Set("✅: Pale Scarf")
                end
                if v.Name == "Valkyrie Helmet" then
                    Valkyrie_Helm:Set("✅: Valkyrie Helmet")
                end
            end
        end)
    end
end)
