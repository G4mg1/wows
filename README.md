for i,v in pairs(game.Players.LocalPlayer.Character:GetChildren()) do
	if v:IsA("Accessory") then
		v:Destroy()
	end
end
wait(2)
game:GetService("TextChatService").TextChannels.RBXGeneral:SendAsync("-gh 71961850752564")

Duration = 90;

local lp = game:FindService("Players").LocalPlayer

local function gplr(String)
	local Found = {}
	local strl = String:lower()
	if strl == "all" then
		for i,v in pairs(game:FindService("Players"):GetPlayers()) do
			table.insert(Found,v)
		end
	elseif strl == "others" then
		for i,v in pairs(game:FindService("Players"):GetPlayers()) do
			if v.Name ~= lp.Name then
				table.insert(Found,v)
			end
		end 
	elseif strl == "me" then
		for i,v in pairs(game:FindService("Players"):GetPlayers()) do
			if v.Name == lp.Name then
				table.insert(Found,v)
			end
		end 
	else
		for i,v in pairs(game:FindService("Players"):GetPlayers()) do
			if v.Name:lower():sub(1, #String) == String:lower() then
				table.insert(Found,v)
			end
		end 
	end
	return Found 
end


function ScatterEff(part)
	local eff1 = Instance.new("ParticleEmitter",part)
	eff1.Size = NumberSequence.new(.1)
	eff1.Transparency = NumberSequence.new({NumberSequenceKeypoint.new(0,0),NumberSequenceKeypoint.new(.9,0),NumberSequenceKeypoint.new(1,1)})
	eff1.LightEmission = 1
	eff1.Lifetime = NumberRange.new(1)
	eff1.Speed = NumberRange.new(1)
	eff1.Rate = 100
	eff1.VelocitySpread = 10000
	eff1.Texture = "rbxassetid://347504241"
	eff1.Color = ColorSequence.new(Color3.new(1,0,0))
	local eff2 = Instance.new("ParticleEmitter",part)
	eff2.Size = NumberSequence.new(.1)
	eff2.Transparency = NumberSequence.new({NumberSequenceKeypoint.new(0,0),NumberSequenceKeypoint.new(.9,0),NumberSequenceKeypoint.new(1,1)})
	eff2.LightEmission = 1
	eff2.Lifetime = NumberRange.new(1)
	eff2.Speed = NumberRange.new(1)
	eff2.Rate = 100
	eff2.VelocitySpread = 10000
	eff2.Texture = "rbxassetid://347504259"
	eff2.Color = ColorSequence.new(Color3.new(1,0,0))
end


OP = game.Players
OPlayer = OP.LocalPlayer
Character = OPlayer["Character"]
Humanoid = Character["Humanoid"]
RootPart = Character["HumanoidRootPart"]
Torso = Character["Torso"]
Head = Character["Head"]
RightArm = Character["Right Arm"]
LeftArm = Character["Left Arm"]
RightLeg = Character["Right Leg"]
LeftLeg = Character["Left Leg"]
RootJoint = RootPart["RootJoint"]
Neck = Torso["Neck"]
RightShoulder = Torso["Right Shoulder"]
LeftShoulder = Torso["Left Shoulder"]
RightHip = Torso["Right Hip"]
LeftHip = Torso["Left Hip"]
HitBox = RightArm

New = function(Object, Parent, Name, Data)
	local Object = Instance.new(Object)
	for Index, Value in pairs(Data or {}) do
		Object[Index] = Value
	end
	Object.Parent = Parent
	Object.Name = Name
	return Object
end


slashsnd = New("Sound",Character.Torso,"Slash",{SoundId = "rbxassetid://28144425",PlaybackSpeed = .7,Volume = 5})
hitsnd = New("Sound",Character.Torso,"Hit",{SoundId = "rbxassetid://429400881",PlaybackSpeed = .7,Volume = 5})
telesnd = New("Sound",Character.Torso,"Tele",{SoundId = "rbxassetid://2767090",PlaybackSpeed = .7,Volume = 5})
burnsnd = New("Sound",Character.Torso,"Burn",{SoundId = "rbxassetid://32791565",PlaybackSpeed = .7,Volume = 5})
music1 = New("Sound",Character.Torso,"Music1",{SoundId = "rbxassetid://151038517",PlaybackSpeed = .5,Volume = 10,Looped = true})
music2 = New("Sound",Character.Torso,"Music2",{SoundId = "rbxassetid://11984351",PlaybackSpeed = .2,Volume = 5,Looped = true})
deathmus = New("Sound",Character.Torso,"DeathMus",{SoundId = "rbxassetid://19094700",PlaybackSpeed = .5,Volume = 5,Looped = true})
deathex = New("Sound",Character.Torso,"DeathEx",{SoundId = "rbxassetid://11984351",PlaybackSpeed = 1,Volume = 5})
music1:Play()
music2:Play()




function RemoveALLCLOTHS()
	for i,v in pairs(Character:GetDescendants()) do
		if v:IsA("Shirt") or v:IsA("ShirtGraphic") or v:IsA("Pants") then
			v:Destroy()
		end
	end
end

function AddColor()
	LeftArm.Color = Color3.new(1, 0.92549, 0.545098)
	RightArm.Color = Color3.new(1, 0.92549, 0.545098)
	Torso.Color = Color3.new(1, 0.843137, 0.376471)
	LeftLeg.Color = Color3.new(0.168627, 0.74902, 1)
	RightLeg.Color = Color3.new(0.168627, 0.74902, 1)
	Head.Color = Color3.new(1, 0.92549, 0.545098)
end

RemoveALLCLOTHS()
AddColor()

function Adjust()
	RightArm.Transparency = 1
	RightArm.CanCollide = false
end
Adjust()

local naeeym = Instance.new("BillboardGui",Character)
naeeym.Size = UDim2.new(0,100,0,40)
naeeym.StudsOffset = Vector3.new(0,2,0)
naeeym.Adornee = Head
local tecks = Instance.new("TextLabel",naeeym)
tecks.BackgroundTransparency = 1
tecks.BorderSizePixel = 0
tecks.Text = "John Doe"
tecks.Font = "Fantasy"
tecks.FontSize = "Size24"
tecks.TextStrokeTransparency = 0
tecks.TextStrokeColor3 = Color3.new(0,0,0)
tecks.TextColor3 = Color3.new(0,0,0)
tecks.Size = UDim2.new(1,0,0.5,0)



function SoulSteal(pos)
	local soulst = coroutine.wrap(function()
		local soul = Instance.new("Part",Character)
		soul.Size = Vector3.new(0,0,0)
		soul.CanCollide = false
		soul.Anchored = false
		soul.Position = pos
		soul.CFrame = CFrame.new(pos.X,pos.Y,pos.Z)
		soul.Transparency = 1
		local ptc = Instance.new("ParticleEmitter",soul)
		ptc.Texture = "http://www.roblox.com/asset/?id=413366101"
		ptc.Size = NumberSequence.new(.5)
		ptc.LockedToPart = true
		ptc.Speed = NumberRange.new(0)
		ptc.Lifetime = NumberRange.new(9999)
		local bodpos = Instance.new("BodyPosition",soul)
		bodpos.Position = pos
		wait(2)
		soul.Touched:connect(function(hit)
			if hit.Parent == Character then
				soul:Destroy()
			end
		end)
		while soul do
			wait(.1)
			bodpos.Position = Character.Torso.Position
		end
	end)
	soulst()
end


function KillMortal(hitdude)
	local torsy = nil
	if hitdude:FindFirstChild("Torso")~=nil then
		torsy = hitdude.Torso	
	elseif hitdude:FindFirstChild("UpperTorso")~=nil then
		torsy = hitdude.UpperTorso
	end
	local val = Instance.new("ObjectValue",hitdude)
	val.Name = "HasBeenHit"
	hitdude:BreakJoints()
	hitdude.Humanoid:Destroy()
	SoulSteal(torsy.Position)
	local chi = hitdude:GetChildren()
	for i = 1, #chi do
		if chi[i].ClassName == "Part" or chi[i].ClassName == "MeshPart" then
			local bodpos = Instance.new("BodyPosition",chi[i])
			bodpos.Position = chi[i].Position + Vector3.new(math.random(-5,5),math.random(-5,5),math.random(-5,5))
			ScatterEff(chi[i])
			chi[i].BrickColor = BrickColor.new("Really black")
		end
	end
	for i = 1, 4 do
		for i = 1, #chi do
			if chi[i].ClassName == "Part" or chi[i].ClassName == "MeshPart" then
				chi[i].Transparency = chi[i].Transparency + .25
				wait(.01)
			end
		end
	end
	for i = 1, #chi do
		if chi[i].ClassName == "Part" or chi[i].ClassName == "MeshPart" then
			chi[i]:Destroy()
		end
	end
end


swinganim = Character.Humanoid:LoadAnimation(New("Animation",Character,"Swing",{AnimationId = "rbxassetid://186934658"}))


bladeactive = false
HitBox.Touched:connect(function(hit)
	if bladeactive == true then
		if hit.Parent:FindFirstChild("Humanoid")~= nil and hit.Parent:FindFirstChild("HasBeenHit")== nil and hit.Parent ~= chara then
			hitsnd:Play()
			KillMortal(hit.Parent)
		end
	end
end)

function Teleport(pos)
	telesnd:Play()
	local ch = Character:GetChildren()
	for i = 1, #ch do
		if ch[i].ClassName == "Part" and ch[i].Name ~= "HumanoidRootPart" then
			local trace = Instance.new("Part",game.Workspace)
			trace.Size = ch[i].Size
			trace.Material = "Neon"
			trace.BrickColor = BrickColor.new("Really black")
			trace.Transparency = .3
			trace.CanCollide = false
			trace.Anchored = true
			trace.CFrame = ch[i].CFrame
			if ch[i].Name == "Head" then
				mehs = Instance.new("CylinderMesh",trace)
				mehs.Scale = Vector3.new(1.25,1.25,1.25)
			end
			tracedisappear = coroutine.wrap(function()
				wait(1)
				for i = 1, 7 do
					wait(.1)
					trace.Transparency = trace.Transparency + .1
				end
				trace:Destroy()
			end)
			tracedisappear()
		end
	end
	chara.Torso.CFrame = CFrame.new(pos.X,pos.Y,pos.Z)
end


function Grab(mouse)
	local hit = mouse.Target
	if hit ~= nil then
		if hit.Parent:FindFirstChild("Humanoid")~=nil then
			local torsy = nil
			if hit.Parent:FindFirstChild("Torso")~=nil then
				torsy = hit.Parent.Torso
			elseif hit.Parent:FindFirstChild("UpperTorso")~=nil then
				torsy = hit.Parent.UpperTorso
			end
			local bodpos = Instance.new("BodyPosition",torsy)
			bodpos.Position = torsy.Position
			wait(1)
			burnsnd:Play()
			hit.Parent.Humanoid.MaxHealth = 100
			bodpos.Position = bodpos.Position + Vector3.new(0,4,0)
			for i = 1, 10 do
				wait(.1)
				BurningEff(torsy)
				hit.Parent.Humanoid.Health = hit.Parent.Humanoid.Health - 10
			end
			KillMortal(hit.Parent)
		end
	else end
end


dell = false
function onButton1Down()
	if dell == false then
		dell = true
		swinganim:Play()
		bladeactive = true
		slashsnd:Play()
		wait(.7)
		bladeactive = false
		dell = false
		swinganim:Stop()
	end
end


function onKeyDown(key)
	if key == "z" then
		Teleport(Mouse.Hit.p + Vector3.new(0,2,0))
	elseif key == "x" then
		Grab(Mouse)
	end
end


Mouse = OPlayer:GetMouse()
if Mouse then
	Mouse.Button1Down:connect(onButton1Down)
	Mouse.KeyDown:connect(onKeyDown)
end

Character.Humanoid.Died:connect(function()
	local pat = Instance.new("Part",game.Workspace)
	pat.Transparency = 1
	pat.Anchored = true
	pat.CFrame = Character.Torso.CFrame
	naeeym.Parent = pat
	naeeym.Adornee = pat
	skybox.Parent = game.Workspace
	tecks.Text = "BAD CHOICE"
	tecks.FontSize = "Size48"
	tecks.TextColor3 = Color3.new(1,0,0)
	music1:Stop()
	music2:Stop()
	deathmus.Parent = game.Workspace
	deathex.Parent = game.Workspace
	deathmus:Play()
	deathex:Play()
	game.Lighting.OutdoorAmbient = Color3.new(0,0,0)
	game.Lighting.TimeOfDay = "00:00:00"
	game.Lighting.FogColor = Color3.new(0,0,0)
	game.Lighting.FogEnd = 1000
	local ex = Instance.new("Explosion",game.Workspace)
	ex.Position = Character.Torso.Position
	ex.Visible = false
	ex.BlastRadius = 999999999999999999999999
	ex.BlastPressure = 9999999999999999999999999
end)
