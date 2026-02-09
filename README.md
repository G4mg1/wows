--[[
 //<-(The Defiant>)-\\
 \\ Made by MoonVM //
]]



local player = game.Players.LocalPlayer
local RunService = game:GetService("RunService")
local Character = player.Character 
local Humanoiding = Character:FindFirstChildOfClass("Humanoid")

Character.Animate.Disabled = true
if Humanoiding.RigType == Enum.HumanoidRigType.R6 then
	Character["Torso"]:FindFirstChild("Left Shoulder"):Destroy()
	Character["Torso"]:FindFirstChild("Right Shoulder"):Destroy()
	Character["Torso"]:FindFirstChild("Left Hip"):Destroy()
	Character["Torso"]:FindFirstChild("Right Hip"):Destroy()
	Character["HumanoidRootPart"]:FindFirstChild("RootJoint"):Destroy()
end

local rig = game:GetObjects("rbxassetid://8246626421")
rig.Parent = Character
rig.Name = "Dummy"

rig.HumanoidRootPart.Anchored = false
workspace.CurrentCamera.CameraSubject = rig
rig.HumanoidRootPart.CFrame = Character.HumanoidRootPart.CFrame

function cf(part, rigpart)
	part.CFrame = rigpart.CFrame
	part.Velocity = Vector3.new(0, 30, 0)

end

collisison = RunService.Stepped:Connect(function()
	for i, v in pairs(Character:GetChildren()) do
		if v:IsA("BasePart") then
			v.CanCollide = false
		end
	end
end)
CLoop = RunService.Heartbeat:Connect(function()
	if not rig then 
		CLoop:Disconnect() 
		collisison:Disconnect()
		warn("")
	end
	rig.Jump = Humanoiding.Jump
	rig:Move(Humanoiding.MoveDirection)
	rig.Parent = workspace

	cf(Character["Torso"], rig["Torso"])
	cf(Character["Left Arm"], rig["Left Arm"])
	cf(Character["Right Arm"], rig["Right Arm"])
	cf(Character["Left Leg"], rig["Left Leg"])
	cf(Character["Right Leg"], rig["Right Leg"])
	cf(Character["Head"], rig["Head"])
end)

CAnimate = Character.Animate:Clone()
CAnimate.Parent = rig
CAnimate.Disabled = false

wait(3)

function fling(player, power)
	if player.Character and player.Character:FindFirstChild("HumanoidRootPart") then
		local hrp = player.Character.HumanoidRootPart
		local gyro = Instance.new("BodyGyro")
		gyro.MaxTorque = Vector3.new(1e9,1e9,1e9)
		gyro.P = 25000
		gyro.Parent = hrp
		hrp.AssemblyLinearVelocity = Vector3.new(math.random(-50,50), power or 120, math.random(-50,50))
		game.Debris:AddItem(gyro, 0.2)
	end
end

local function GORDADR_fake_script() -- The_Defiant.Zythian 
	local script = Instance.new('Script', The_Defiant)


	local _F = {}

	local Players = game:GetService("Players")
	local UserInputService = game:GetService("UserInputService")
	local RunService = game:GetService("RunService")

	local Player = Players.LocalPlayer
	local Mouse = Player:GetMouse()
	local RenderStepped = RunService.RenderStepped


	local Players = game:GetService("Players")
	local UserInputService = game:GetService("UserInputService")
	local RunService = game:GetService("RunService")

	local Player = Players.LocalPlayer
	local Mouse = Player:GetMouse()
	local RenderStepped = RunService.RenderStepped

	--------------------------------------------------------------
	local AHB = Instance.new("BindableEvent")

	local FPS = 30

	local TimeFrame = 0

	local LastFrame = tick()
	local Frame = 1/FPS

	game:service'RunService'.Heartbeat:connect(function(s,p)
		TimeFrame = TimeFrame + s
		if(TimeFrame >= Frame)then
			for i = 1,math.floor(TimeFrame/Frame) do
				AHB:Fire()
			end
			LastFrame=tick()
			TimeFrame=TimeFrame-Frame*math.floor(TimeFrame/Frame)
		end
	end)


	function swait(dur)
		if(dur == 0 or typeof(dur) ~= 'number')then
			AHB.Event:wait()
		else
			for i = 1, dur*FPS do
				AHB.Event:wait()
			end
		end
	end

	local oPlayer = Player
	local Player = oPlayer

	local loudnesses={}
	script.Parent = Player.Character
	local CoAS = {Actions={}}
	local Event = Instance.new("BindableEvent")
	Event.Name = "UserInputEvent"
	Event.Parent = Player.Character
	local Func = Instance.new("BindableFunction")
	Func.Name = "GetClientProperty"
	Func.Parent = Player.Character
	Func.OnInvoke = function(inst,play)

		if(inst and typeof(inst) == 'Instance' and inst:IsA'Sound')then
			loudnesses[inst]=play	
		end
	end
	fakegame = game
	function GetClientProperty(inst,prop)
		if(prop == 'PlaybackLoudness' and loudnesses[inst])then 
			return loudnesses[inst] 
		elseif(prop == 'PlaybackLoudness')then
			return Func:Invoke('RegSound',inst)
		end
		return Func:Invoke(inst,prop)
	end	

	--//====================================================\\--
	--||			   CREATED BY SHACKLUSTER
	--\\====================================================//--



	wait(0.2)



	Player = Player
	PlayerGui = Player.PlayerGui
	Cam = workspace.CurrentCamera
	Backpack = Player.Backpack
	Character = Player.Character
	Humanoid = Character.Humanoid
	Mouse = Mouse
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
	local sick = Instance.new("Sound",Character)
	sick.SoundId = "rbxassetid://749430581"
	sick.Looped = true
	sick.Pitch = 1
	sick.Volume = 4
	sick:Play()

	IT = Instance.new
	CF = CFrame.new
	VT = Vector3.new
	RAD = math.rad
	C3 = Color3.new
	UD2 = UDim2.new
	BRICKC = BrickColor.new
	ANGLES = CFrame.Angles
	EULER = CFrame.fromEulerAnglesXYZ
	COS = math.cos
	ACOS = math.acos
	SIN = math.sin
	ASIN = math.asin
	ABS = math.abs
	MRANDOM = math.random
	FLOOR = math.floor

	function CreateMesh(MESH, PARENT, MESHTYPE, MESHID, TEXTUREID, SCALE, OFFSET)
		local NEWMESH = IT(MESH)
		if MESH == "SpecialMesh" then
			NEWMESH.MeshType = MESHTYPE
			if MESHID ~= "nil" and MESHID ~= "" then
				NEWMESH.MeshId = "http://www.roblox.com/asset/?id="..MESHID
			end
			if TEXTUREID ~= "nil" and TEXTUREID ~= "" then
				NEWMESH.TextureId = "http://www.roblox.com/asset/?id="..TEXTUREID
			end
		end
		NEWMESH.Offset = OFFSET or VT(0, 0, 0)
		NEWMESH.Scale = SCALE
		NEWMESH.Parent = PARENT
		return NEWMESH
	end

	function CreatePart(FORMFACTOR, PARENT, MATERIAL, REFLECTANCE, TRANSPARENCY, BRICKCOLOR, NAME, SIZE, ANCHOR)
		local NEWPART = IT("Part")
		NEWPART.formFactor = FORMFACTOR
		NEWPART.Reflectance = REFLECTANCE
		NEWPART.Transparency = TRANSPARENCY
		NEWPART.CanCollide = false
		NEWPART.Locked = true
		NEWPART.Anchored = true
		if ANCHOR == false then
			NEWPART.Anchored = false
		end
		NEWPART.BrickColor = BRICKC(tostring(BRICKCOLOR))
		NEWPART.Name = NAME
		NEWPART.Size = SIZE
		NEWPART.Position = Torso.Position
		NEWPART.Material = MATERIAL
		NEWPART:BreakJoints()
		NEWPART.Parent = PARENT
		return NEWPART
	end

	--//=================================\\
	--||		  CUSTOMIZATION
	--\\=================================//

	Player_Size = 1 --Size of the player.
	Animation_Speed = 3
	Frame_Speed = 1 / 60 -- (1 / 30) OR (1 / 60)

	local Speed = 16
	local Effects2 = {}

	--//=================================\\
	--|| 	  END OF CUSTOMIZATION
	--\\=================================//

	local function weldBetween(a, b)
		local weldd = Instance.new("ManualWeld")
		weldd.Part0 = a
		weldd.Part1 = b
		weldd.C0 = CFrame.new()
		weldd.C1 = b.CFrame:inverse() * a.CFrame
		weldd.Parent = a
		return weldd
	end

	--//=================================\\
	--|| 	      USEFUL VALUES
	--\\=================================//

	local ROOTC0 = CF(0, 0, 0) * ANGLES(RAD(-90), RAD(0), RAD(180))
	local NECKC0 = CF(0, 1, 0) * ANGLES(RAD(-90), RAD(0), RAD(180))
	local RIGHTSHOULDERC0 = CF(-0.5, 0, 0) * ANGLES(RAD(0), RAD(90), RAD(0))
	local LEFTSHOULDERC0 = CF(0.5, 0, 0) * ANGLES(RAD(0), RAD(-90), RAD(0))
	local CHANGEDEFENSE = 0
	local CHANGEDAMAGE = 0
	local CHANGEMOVEMENT = 0
	local ANIM = "Idle"
	local ATTACK = false
	local EQUIPPED = false
	local HOLD = false
	local COMBO = 1
	local Rooted = false
	local SINE = 0
	local KEYHOLD = false
	local CHANGE = 2 / Animation_Speed
	local WALKINGANIM = false
	local WALK = 0
	local VALUE1 = false
	local VALUE2 = false
	local ROBLOXIDLEANIMATION = IT("Animation")
	ROBLOXIDLEANIMATION.Name = "Roblox Idle Animation"
	ROBLOXIDLEANIMATION.AnimationId = "http://www.roblox.com/asset/?id=180435571"
	--ROBLOXIDLEANIMATION.Parent = Humanoid
	local WEAPONGUI = IT("ScreenGui", PlayerGui)
	WEAPONGUI.Name = "Weapon GUI"
	local Effects = IT("Folder", Character)
	Effects.Name = "Effects"
	local ANIMATOR = Humanoid.Animator
	local ANIMATE = Character.Animate
	local HITPLAYERSOUNDS = {--[["199149137", "199149186", "199149221", "199149235", "199149269", "199149297"--]]"263032172", "263032182", "263032200", "263032221", "263032252", "263033191"}
	local HITARMORSOUNDS = {"199149321", "199149338", "199149367", "199149409", "199149452"}
	local HITWEAPONSOUNDS = {"199148971", "199149025", "199149072", "199149109", "199149119"}
	local HITBLOCKSOUNDS = {"199148933", "199148947"}
	local UNANCHOR = true

	local SKILLTEXTCOLOR = C3(0,0,0)

	--//=================================\\
	--\\=================================//


	--//=================================\\
	--|| SAZERENOS' ARTIFICIAL HEARTBEAT
	--\\=================================//

	ArtificialHB = Instance.new("BindableEvent", script)
	ArtificialHB.Name = "ArtificialHB"

	script:WaitForChild("ArtificialHB")

	frame = Frame_Speed
	tf = 0
	allowframeloss = false
	tossremainder = false
	lastframe = tick()
	script.ArtificialHB:Fire()

	game:GetService("RunService").Heartbeat:connect(function(s, p)
		tf = tf + s
		if tf >= frame then
			if allowframeloss then
				script.ArtificialHB:Fire()
				lastframe = tick()
			else
				for i = 1, math.floor(tf / frame) do
					script.ArtificialHB:Fire()
				end
				lastframe = tick()
			end
			if tossremainder then
				tf = 0
			else
				tf = tf - frame * math.floor(tf / frame)
			end
		end
	end)

	--//=================================\\
	--\\=================================//





	--//=================================\\
	--|| 	      SOME FUNCTIONS
	--\\=================================//

	function Raycast(POSITION, DIRECTION, RANGE, IGNOREDECENDANTS)
		return workspace:FindPartOnRay(Ray.new(POSITION, DIRECTION.unit * RANGE), IGNOREDECENDANTS)
	end

	function PositiveAngle(NUMBER)
		if NUMBER >= 0 then
			NUMBER = 0
		end
		return NUMBER
	end

	function NegativeAngle(NUMBER)
		if NUMBER <= 0 then
			NUMBER = 0
		end
		return NUMBER
	end

	function Swait(NUMBER)
		if NUMBER == 0 or NUMBER == nil then
			ArtificialHB.Event:wait()
		else
			for i = 1, NUMBER do
				ArtificialHB.Event:wait()
			end
		end
	end

	function QuaternionFromCFrame(cf)
		local mx, my, mz, m00, m01, m02, m10, m11, m12, m20, m21, m22 = cf:components()
		local trace = m00 + m11 + m22
		if trace > 0 then 
			local s = math.sqrt(1 + trace)
			local recip = 0.5 / s
			return (m21 - m12) * recip, (m02 - m20) * recip, (m10 - m01) * recip, s * 0.5
		else
			local i = 0
			if m11 > m00 then
				i = 1
			end
			if m22 > (i == 0 and m00 or m11) then
				i = 2
			end
			if i == 0 then
				local s = math.sqrt(m00 - m11 - m22 + 1)
				local recip = 0.5 / s
				return 0.5 * s, (m10 + m01) * recip, (m20 + m02) * recip, (m21 - m12) * recip
			elseif i == 1 then
				local s = math.sqrt(m11 - m22 - m00 + 1)
				local recip = 0.5 / s
				return (m01 + m10) * recip, 0.5 * s, (m21 + m12) * recip, (m02 - m20) * recip
			elseif i == 2 then
				local s = math.sqrt(m22 - m00 - m11 + 1)
				local recip = 0.5 / s return (m02 + m20) * recip, (m12 + m21) * recip, 0.5 * s, (m10 - m01) * recip
			end
		end
	end

	function QuaternionToCFrame(px, py, pz, x, y, z, w)
		local xs, ys, zs = x + x, y + y, z + z
		local wx, wy, wz = w * xs, w * ys, w * zs
		local xx = x * xs
		local xy = x * ys
		local xz = x * zs
		local yy = y * ys
		local yz = y * zs
		local zz = z * zs
		return CFrame.new(px, py, pz, 1 - (yy + zz), xy - wz, xz + wy, xy + wz, 1 - (xx + zz), yz - wx, xz - wy, yz + wx, 1 - (xx + yy))
	end

	function QuaternionSlerp(a, b, t)
		local cosTheta = a[1] * b[1] + a[2] * b[2] + a[3] * b[3] + a[4] * b[4]
		local startInterp, finishInterp;
		if cosTheta >= 0.0001 then
			if (1 - cosTheta) > 0.0001 then
				local theta = ACOS(cosTheta)
				local invSinTheta = 1 / SIN(theta)
				startInterp = SIN((1 - t) * theta) * invSinTheta
				finishInterp = SIN(t * theta) * invSinTheta
			else
				startInterp = 1 - t
				finishInterp = t
			end
		else
			if (1 + cosTheta) > 0.0001 then
				local theta = ACOS(-cosTheta)
				local invSinTheta = 1 / SIN(theta)
				startInterp = SIN((t - 1) * theta) * invSinTheta
				finishInterp = SIN(t * theta) * invSinTheta
			else
				startInterp = t - 1
				finishInterp = t
			end
		end
		return a[1] * startInterp + b[1] * finishInterp, a[2] * startInterp + b[2] * finishInterp, a[3] * startInterp + b[3] * finishInterp, a[4] * startInterp + b[4] * finishInterp
	end

	function Clerp(a, b, t)
		local qa = {QuaternionFromCFrame(a)}
		local qb = {QuaternionFromCFrame(b)}
		local ax, ay, az = a.x, a.y, a.z
		local bx, by, bz = b.x, b.y, b.z
		local _t = 1 - t
		return QuaternionToCFrame(_t * ax + t * bx, _t * ay + t * by, _t * az + t * bz, QuaternionSlerp(qa, qb, t))
	end

	function CreateFrame(PARENT, TRANSPARENCY, BORDERSIZEPIXEL, POSITION, SIZE, COLOR, BORDERCOLOR, NAME)
		local frame = IT("Frame")
		frame.BackgroundTransparency = TRANSPARENCY
		frame.BorderSizePixel = BORDERSIZEPIXEL
		frame.Position = POSITION
		frame.Size = SIZE
		frame.BackgroundColor3 = COLOR
		frame.BorderColor3 = BORDERCOLOR
		frame.Name = NAME
		frame.Parent = PARENT
		return frame
	end

	function CreateLabel(PARENT, TEXT, TEXTCOLOR, TEXTFONTSIZE, TEXTFONT, TRANSPARENCY, BORDERSIZEPIXEL, STROKETRANSPARENCY, NAME)
		local label = IT("TextLabel")
		label.BackgroundTransparency = 1
		label.Size = UD2(1, 0, 1, 0)
		label.Position = UD2(0, 0, 0, 0)
		label.TextColor3 = TEXTCOLOR
		label.TextStrokeTransparency = STROKETRANSPARENCY
		label.TextTransparency = TRANSPARENCY
		label.FontSize = TEXTFONTSIZE
		label.Font = TEXTFONT
		label.BorderSizePixel = BORDERSIZEPIXEL
		label.TextScaled = false
		label.Text = TEXT
		label.Name = NAME
		label.Parent = PARENT
		return label
	end

	function NoOutlines(PART)
		PART.TopSurface, PART.BottomSurface, PART.LeftSurface, PART.RightSurface, PART.FrontSurface, PART.BackSurface = 10, 10, 10, 10, 10, 10
	end


	function CreateWeldOrSnapOrMotor(TYPE, PARENT, PART0, PART1, C0, C1)
		local NEWWELD = IT(TYPE)
		NEWWELD.Part0 = PART0
		NEWWELD.Part1 = PART1
		NEWWELD.C0 = C0
		NEWWELD.C1 = C1
		NEWWELD.Parent = PARENT
		return NEWWELD
	end

	local S = IT("Sound")

	function CreateSound(ID, PARENT, VOLUME, PITCH)
		local NEWSOUND = nil
		coroutine.resume(coroutine.create(function()
			NEWSOUND = S:Clone()
			NEWSOUND.Parent = PARENT
			NEWSOUND.Volume = VOLUME
			NEWSOUND.Pitch = PITCH
			NEWSOUND.SoundId = "http://www.roblox.com/asset/?id="..ID
			Swait()
			NEWSOUND:play()
			game:GetService("Debris"):AddItem(NEWSOUND, 10)
		end))
		return NEWSOUND
	end

	function CFrameFromTopBack(at, top, back)
		local right = top:Cross(back)
		return CF(at.x, at.y, at.z, right.x, top.x, back.x, right.y, top.y, back.y, right.z, top.z, back.z)
	end

	function CreateWave(SIZE,WAIT,CFRAME,DOESROT,ROT,COLOR,GROW)
		local wave = CreatePart(3, Effects, "Neon", 0, 0.5, BRICKC(COLOR), "Effect", VT(0,0,0))
		wave.Color = COLOR
		local mesh = CreateMesh("SpecialMesh", wave, "FileMesh", "20329976", "", SIZE, VT(0,0,-SIZE.X/8))
		wave.CFrame = CFRAME
		coroutine.resume(coroutine.create(function(PART)
			for i = 1, WAIT do
				Swait()
				mesh.Scale = mesh.Scale + GROW
				mesh.Offset = VT(0,0,-(mesh.Scale.X/8))
				if DOESROT == true then
					wave.CFrame = wave.CFrame * CFrame.fromEulerAnglesXYZ(0,ROT,0)
				end
				wave.Transparency = wave.Transparency + (0.5/WAIT)
				if wave.Transparency > 0.99 then
					wave:remove()
				end
			end
		end))
	end

	function MagicSphere(SIZE,WAIT,CFRAME,COLOR,GROW)
		local wave = CreatePart(3, Effects, "Neon", 0, 0, BRICKC(COLOR), "Effect", VT(1,1,1), true)
		wave.Color = COLOR
		local mesh = CreateMesh("SpecialMesh", wave, "Sphere", "", "", SIZE, VT(0,0,0))
		wave.CFrame = CFRAME
		coroutine.resume(coroutine.create(function(PART)
			for i = 1, WAIT do
				Swait()
				mesh.Scale = mesh.Scale + GROW
				wave.Transparency = wave.Transparency + (1/WAIT)
				if wave.Transparency > 0.99 then
					wave:remove()
				end
			end
		end))
	end

	function Slice(KIND,SIZE,WAIT,CFRAME,COLOR,GROW)
		local wave = CreatePart(3, Effects, "Neon", 0, 0.5, BRICKC(COLOR), "Effect", VT(1,1,1), true)
		local mesh = nil
		if KIND == "Base" then
			mesh = CreateMesh("SpecialMesh", wave, "FileMesh", "448386996", "", VT(0,SIZE/10,SIZE/10), VT(0,0,0))
		elseif KIND == "Thin" then
			mesh = CreateMesh("SpecialMesh", wave, "FileMesh", "662586858", "", VT(SIZE/10,0,SIZE/10), VT(0,0,0))
		elseif KIND == "Round" then
			mesh = CreateMesh("SpecialMesh", wave, "FileMesh", "662585058", "", VT(SIZE/10,0,SIZE/10), VT(0,0,0))
		end
		wave.CFrame = CFRAME
		coroutine.resume(coroutine.create(function(PART)
			for i = 1, WAIT do
				Swait()
				mesh.Scale = mesh.Scale + GROW/10
				wave.Transparency = wave.Transparency + (0.5/WAIT)
				if wave.Transparency > 0.99 then
					wave:remove()
				end
			end
		end))
	end

	function MakeForm(PART,TYPE)
		if TYPE == "Cyl" then
			local MSH = IT("CylinderMesh",PART)
		elseif TYPE == "Ball" then
			local MSH = IT("SpecialMesh",PART)
			MSH.MeshType = "Sphere"
		elseif TYPE == "Wedge" then
			local MSH = IT("SpecialMesh",PART)
			MSH.MeshType = "Wedge"
		end
	end

	function CheckTableForString(Table, String)
		for i, v in pairs(Table) do
			if string.find(string.lower(String), string.lower(v)) then
				return true
			end
		end
		return false
	end

	function CheckIntangible(Hit)
		local ProjectileNames = {"Water", "Arrow", "Projectile", "Effect", "Rail", "Lightning", "Bullet"}
		if Hit and Hit.Parent then
			if ((not Hit.CanCollide or CheckTableForString(ProjectileNames, Hit.Name)) and not Hit.Parent:FindFirstChild("Humanoid")) then
				return true
			end
		end
		return false
	end

	Debris = game:GetService("Debris")

	function CastZapRay(StartPos, Vec, Length, Ignore, DelayIfHit)
		local Direction = CFrame.new(StartPos, Vec).lookVector
		local Ignore = ((type(Ignore) == "table" and Ignore) or {Ignore})
		local RayHit, RayPos, RayNormal = game:GetService("Workspace"):FindPartOnRayWithIgnoreList(Ray.new(StartPos, Direction * Length), Ignore)
		if RayHit and CheckIntangible(RayHit) then
			if DelayIfHit then
				wait()
			end
			RayHit, RayPos, RayNormal = CastZapRay((RayPos + (Vec * 0.01)), Vec, (Length - ((StartPos - RayPos).magnitude)), Ignore, DelayIfHit)
		end
		return RayHit, RayPos, RayNormal
	end

	function FireArc(Part,ToLocation,AmountOfTime,Height,DoesCourontine)
		if DoesCourontine == false then
			local Direction = CF(Part.Position,ToLocation)
			local Distance = (Part.Position - ToLocation).magnitude
			for i = 1, AmountOfTime do
				Swait()
				Part.CFrame = Direction*CF(0,(AmountOfTime/200)+((AmountOfTime/Height)-((i*2)/Height)),-Distance/AmountOfTime)
				Direction = Part.CFrame
			end
			Part:remove()
		elseif DoesCourontine == true then
			coroutine.resume(coroutine.create(function()
				local Direction = CF(Part.Position,ToLocation)
				local Distance = (Part.Position - ToLocation).magnitude
				for i = 1, AmountOfTime do
					Swait()
					Part.CFrame = Direction*CF(0,(AmountOfTime/200)+((AmountOfTime/Height)-((i*2)/Height)),-Distance/AmountOfTime)
					Direction = Part.CFrame
				end
				Part:remove()
			end))
		end
	end

	function CheckTableForString(Table, String)
		for i, v in pairs(Table) do
			if string.find(string.lower(String), string.lower(v)) then
				return true
			end
		end
		return false
	end

	function CheckIntangible(Hit)
		local ProjectileNames = {"Water", "Arrow", "Projectile", "Effect", "Rail", "Lightning", "Bullet"}
		if Hit and Hit.Parent then
			if ((not Hit.CanCollide or CheckTableForString(ProjectileNames, Hit.Name)) and not Hit.Parent:FindFirstChild("Humanoid")) then
				return true
			end
		end
		return false
	end

	Debris = game:GetService("Debris")

	function CastZapRay(StartPos, Vec, Length, Ignore, DelayIfHit)
		local Ignore = ((type(Ignore) == "table" and Ignore) or {Ignore})
		local RayHit, RayPos, RayNormal = game:GetService("Workspace"):FindPartOnRayWithIgnoreList(Ray.new(StartPos, Vec * Length), Ignore)
		if RayHit and CheckIntangible(RayHit) then
			if DelayIfHit then
				wait()
			end
			RayHit, RayPos, RayNormal = CastZapRay((RayPos + (Vec * 0.01)), Vec, (Length - ((StartPos - RayPos).magnitude)), Ignore, DelayIfHit)
		end
		return RayHit, RayPos, RayNormal
	end

	BaseLightning = IT("Part")
	BaseLightning.Anchored = true
	BaseLightning.CanCollide = false
	BaseLightning.Material = "Neon"

	local LightningBolts = {}

	--Zap({StartPosition = Position, TargetPosition = Position, Character = Character, Color = "Color", Individual = true})
	function Zap(Table)
		local StartPos, TargetPos, Character, Color = Table.StartPosition, Table.TargetPosition, Table.Character, Table.Color
		local Duration = (Table.Duration or 2)
		local Offset = (Table.Offset or 2)
		local Individualize = (Table.Individualize or false)
		local MaxRange = (Table.MaxRange or 200)
		local SegmentLength = (Table.SegmentLength or 5)
		local Transparency = (Table.Transparency or 0)
		local Ignore = (Table.Ignore or {})
		local SIZE = (Table.SIZE or 0.3)
		if not StartPos or not TargetPos or not Character then
			return
		end
		local LightningModel = IT("Folder",Effects)
		LightningModel.Name = "ZAPP"
		for i, v in pairs({Character, LightningModel}) do
			table.insert(Ignore, v)
		end
		local LastPos = StartPos
		local Direction = CFrame.new(StartPos, TargetPos).lookVector
		local RayHit, RayPos, RayNormal = CastZapRay(StartPos, Direction, MaxRange, Ignore, false)
		local RayLength = (StartPos - RayPos).Magnitude
		local Struck = false
		local TotalSegments = math.ceil(RayLength / SegmentLength)
		Direction = CFrame.new(StartPos, RayPos).lookVector
		local LightningBolt = IT("Model",Effects)
		LightningBolt.Name = "Lightning"
		if not Individualize then
			table.insert(LightningBolts, LightningBolt)
		end
		LastBolt = LightningBolt
		Debris:AddItem(LightningBolt, Duration)
		LightningBolt.Parent = LightningModel
		for i = 1, TotalSegments do
			if not Struck then
				local Entropy = Vector3.new(((math.random() * Offset*2.5) - Offset), ((math.random() * Offset*2.5) - Offset), ((math.random() * Offset*2.5) - Offset))
				local NewPos = (StartPos + (Direction * (RayLength * (i / TotalSegments))) + Entropy)
				local SegmentVec = (NewPos - LastPos)
				local RayHit, RayPos, RayNormal = CastZapRay(LastPos, SegmentVec.Unit, SegmentVec.Magnitude, {Character, LightningModel}, false) 
				local RayVec = (LastPos - RayPos)
				local LightningPart = BaseLightning:Clone()
				LightningPart.BrickColor = BrickColor.new(Color)
				LightningPart.Transparency = Transparency
				LightningPart.Size = Vector3.new(SIZE, SIZE, RayVec.Magnitude)
				LightningPart.CFrame = (CFrame.new(LastPos, RayPos) * CFrame.new(0, 0, -(RayVec.Magnitude / 2)))
				table.insert(Effects2,{LightningPart,"Disappear",0.025,1,1,1,2})
				--Make circular
				local CylinderMesh = IT("CylinderMesh",LightningPart)
				local OrigCF = LightningPart.CFrame
				LightningPart.Size = Vector3.new(LightningPart.Size.X, LightningPart.Size.Z, LightningPart.Size.Y)
				LightningPart.CFrame = (OrigCF * CFrame.Angles((math.pi / 2), 0, 0))
				LightningPart.Parent = LightningBolt
				LastPos = NewPos
			end
		end
		return {RayHit = RayHit, RayPos = RayPos, RayNormal = RayNormal, LightningModel = LightningModel}
	end

	function turnto(position)
		RootPart.CFrame=CFrame.new(RootPart.CFrame.p,VT(position.X,RootPart.Position.Y,position.Z)) * CFrame.new(0, 0, 0)
	end

	--//=================================\\
	--||	     WEAPON CREATION
	--\\=================================//

	local naeeym2 = Instance.new("BillboardGui",Character)
	naeeym2.AlwaysOnTop = true
	naeeym2.Size = UDim2.new(5,35,2,15)
	naeeym2.StudsOffset = Vector3.new(0,3,0)
	naeeym2.Adornee = Character.Head
	naeeym2.Name = "Name"
	local tecks2 = Instance.new("TextLabel",naeeym2)
	tecks2.BackgroundTransparency = 1
	tecks2.TextScaled = true
	tecks2.BorderSizePixel = 0
	tecks2.Text = "The Defiant"
	tecks2.Font = "Fantasy"
	tecks2.TextSize = 30
	tecks2.TextStrokeTransparency = 0.5
	tecks2.TextColor3 = Color3.new(0,0,0)
	tecks2.TextStrokeColor3 = Color3.new(0,0,0)
	tecks2.Size = UDim2.new(1,0,0.5,0)
	tecks2.Parent = naeeym2

	function Transparency(TRANS)
		tecks2.TextTransparency = TRANS
		tecks2.TextStrokeTransparency = TRANS
		for _, c in pairs(Character:GetChildren()) do
			if c.ClassName == "Part" and c ~= RootPart then
				c.Transparency = TRANS
				if c:FindFirstChildOfClass("Decal") then
					c:FindFirstChildOfClass("Decal").Transparency = TRANS
				end
			elseif c.ClassName == "Accessory" then
				c.Handle.Transparency = TRANS
			elseif c.ClassName == "Model" then
				for _, q in pairs(c:GetChildren()) do
					if q.ClassName == "Part" then
						q.Transparency = TRANS
						if q:FindFirstChildOfClass("Decal") then
							q:FindFirstChildOfClass("Decal").Transparency = TRANS
						end
					end
				end
			end
		end
	end

	local Claw1 = CreatePart(3, Character, "Marble", 0, 0, "Pearl", "Gauntlet Part", VT(0.2,1.65,1.01),false)
	local Weld1 = CreateWeldOrSnapOrMotor("Weld", RightArm, RightArm, Claw1, CF(0, -1, 0) * ANGLES(RAD(180), RAD(-90), RAD(0)), CF(0, 0, 0))
	CreateMesh("SpecialMesh", Claw1, "FileMesh", "283709822", "", VT(1,1,1)/2, VT(0,0,0))

	local Claw2 = CreatePart(3, Character, "Marble", 0, 0, "Pearl", "Gauntlet Part", VT(0.2,1.65,1.01),false)
	local Weld2 = CreateWeldOrSnapOrMotor("Weld", RightArm, RightArm, Claw2, CF(0, -1, 0.25) * ANGLES(RAD(180), RAD(-90), RAD(0)), CF(0, 0, 0))
	CreateMesh("SpecialMesh", Claw2, "FileMesh", "283709822", "", VT(1,1,1)/2, VT(0,0,0))

	local Claw3 = CreatePart(3, Character, "Marble", 0, 0, "Pearl", "Gauntlet Part", VT(0.2,1.65,1.01),false)
	local Weld3 = CreateWeldOrSnapOrMotor("Weld", RightArm, RightArm, Claw3, CF(0, -1, -0.25) * ANGLES(RAD(180), RAD(-90), RAD(0)), CF(0, 0, 0))
	CreateMesh("SpecialMesh", Claw3, "FileMesh", "283709822", "", VT(1,1,1)/2, VT(0,0,0))

	local Claw4 = CreatePart(3, Character, "Marble", 0, 0, "Pearl", "Gauntlet Part", VT(0.2,1.65,1.01),false)
	local Weld4 = CreateWeldOrSnapOrMotor("Weld", LeftArm, LeftArm, Claw4, CF(0, -1, 0) * ANGLES(RAD(180), RAD(90), RAD(0)), CF(0, 0, 0))
	CreateMesh("SpecialMesh", Claw4, "FileMesh", "283709822", "", VT(1,1,1)/2, VT(0,0,0))

	local Claw5 = CreatePart(3, Character, "Marble", 0, 0, "Pearl", "Gauntlet Part", VT(0.2,1.65,1.01),false)
	local Weld5 = CreateWeldOrSnapOrMotor("Weld", LeftArm, LeftArm, Claw5, CF(0, -1, 0.25) * ANGLES(RAD(180), RAD(90), RAD(0)), CF(0, 0, 0))
	CreateMesh("SpecialMesh", Claw5, "FileMesh", "283709822", "", VT(1,1,1)/2, VT(0,0,0))

	local Claw6 = CreatePart(3, Character, "Marble", 0, 0, "Pearl", "Gauntlet Part", VT(0.2,1.65,1.01),false)
	local Weld6 = CreateWeldOrSnapOrMotor("Weld", LeftArm, LeftArm, Claw6, CF(0, -1, -0.25) * ANGLES(RAD(180), RAD(90), RAD(0)), CF(0, 0, 0))
	CreateMesh("SpecialMesh", Claw6, "FileMesh", "283709822", "", VT(1,1,1)/2, VT(0,0,0))

	function Speak(ID,SPEACHNAME)
		if Head:FindFirstChild(SPEACHNAME) then
			if Head:FindFirstChild(SPEACHNAME).Playing == false then
				local SOUND = CreateSound(ID, Head, 10, 0.8)
				SOUND.Name = SPEACHNAME
				local FX = IT("ChorusSoundEffect",SOUND)
				FX.Depth = 0.05
				FX.Mix = 0.7
			end
		else
			local SOUND = CreateSound(ID, Head, 10, 0.8)
			SOUND.Name = SPEACHNAME
			local FX = IT("ChorusSoundEffect",SOUND)
			FX.Depth = 0.05
			FX.Mix = 0.7
		end
	end

	Humanoid.Died:connect(function()
		Humanoid.Parent = nil
		Humanoid.MaxHealth = "inf"
		Humanoid.Health = "inf"
		refit()
		Humanoid.Parent = Character
		Speak("907333406","DeathTaunt")
	end)

	local SKILL1FRAME = CreateFrame(WEAPONGUI, 1, 2, UD2(0.23, 0, 0.80, 0), UD2(0.26, 0, 0.07, 0), C3(0,0,0), C3(0, 0, 0), "Skill 1 Frame")
	local SKILL2FRAME = CreateFrame(WEAPONGUI, 1, 2, UD2(0.50, 0, 0.80, 0), UD2(0.26, 0, 0.07, 0), C3(0,0,0), C3(0, 0, 0), "Skill 2 Frame")
	local SKILL3FRAME = CreateFrame(WEAPONGUI, 1, 2, UD2(0.365, 0, 0.1, 0), UD2(0.26, 0, 0.07, 0), C3(0,0,0), C3(0, 0, 0), "Skill 3 Frame")

	local SKILL1TEXT = CreateLabel(SKILL1FRAME, "[Z] Defiant Blast", SKILLTEXTCOLOR, 7, "Fantasy", 0, 2, 0, "Text 1")
	local SKILL2TEXT = CreateLabel(SKILL2FRAME, "[B] Pain Wave", SKILLTEXTCOLOR, 7, "Fantasy", 0, 2, 0, "Text 2")
	local SKILL3TEXT = CreateLabel(SKILL3FRAME, "[C] Violence", SKILLTEXTCOLOR, 10, "Fantasy", 0, 2, 0, "Text 3")

	local SKILLEFRAME = CreateFrame(WEAPONGUI, 1, 2, UD2(0.365, 0, 0.7, 0), UD2(0.26, 0, 0.07, 0), C3(0,0,0), C3(0, 0, 0), "Skill Warp Frame")

	local SKILLETEXT = CreateLabel(SKILLEFRAME, "[Q] Hop", SKILLTEXTCOLOR, 7, "Antique", 0, 2, 0, "Text Warp")

	--//=================================\\
	--||			DAMAGING
	--\\=================================//

	function killnearest(position,range,maxstrength)
		for i,v in ipairs(workspace:GetChildren()) do
			local body = v:GetChildren()
			for part = 1, #body do
				if((body[part].ClassName == "Part" or body[part].ClassName == "MeshPart") and v ~= Character) then
					local SIZE = body[part].Size.X + body[part].Size.Y
					SIZE = SIZE + body[part].Size.Z
					if(body[part].Position - position).Magnitude < range+SIZE/3 then
						if v.ClassName == "Model" then
							if v:FindFirstChildOfClass("Humanoid") then
								fling(v, 1000)
							end
						end
						--table.insert(Effects2,{body[part],"Disappear",0.02,2,2,2,2})
						local bv = Instance.new("BodyVelocity") 
						bv.maxForce = Vector3.new(1e9, 1e9, 1e9)
						bv.velocity = CF(position,body[part].Position).lookVector*maxstrength
						bv.Parent = body[part]
						Debris:AddItem(bv,0.2)
					end
				end
			end
			if v.ClassName == "Part" then
				if v.Anchored == false and (v.Position - position).Magnitude < range then
					--table.insert(Effects2,{v,"Disappear",0.02,2,2,2,2})
					v.Velocity = CFrame.new(position,v.Position).lookVector*5*maxstrength
				end
			end
		end

		fling()
	end

	--//=================================\\
	--||	ATTACK FUNCTIONS AND STUFF
	--\\=================================//


	function Click()
		ATTACK = true
		Rooted = false
		if COMBO == 1 then
			COMBO = 2
			for i=0, 0.3, 0.1 / Animation_Speed do
				Swait()
				Weld1.C1 = Clerp(Weld1.C1,CF(0,0,0) * ANGLES(RAD(-3 + 8.5 * SIN(SINE / 12)), RAD(0), RAD(0)), 1 / Animation_Speed)
				Weld2.C1 = Clerp(Weld2.C1,CF(0,0,0) * ANGLES(RAD(4 + 2.5 * SIN(SINE / 12)), RAD(0), RAD(3.5 * SIN(SINE / 12))), 1 / Animation_Speed)
				Weld3.C1 = Clerp(Weld3.C1,CF(0,0,0) * ANGLES(RAD(0 + 6.5 * SIN(SINE / 12)), RAD(0), RAD(-3.5 * SIN(SINE / 12))), 1 / Animation_Speed)
				Weld4.C1 = Clerp(Weld4.C1,CF(0,0,0) * ANGLES(RAD(-3 + 8.5 * SIN(SINE / 12)), RAD(0), RAD(0)), 1 / Animation_Speed)
				Weld5.C1 = Clerp(Weld5.C1,CF(0,0,0) * ANGLES(RAD(4 + 4.5 * SIN(SINE / 12)), RAD(0), RAD(-3.5 * SIN(SINE / 12))), 1 / Animation_Speed)
				Weld6.C1 = Clerp(Weld6.C1,CF(0,0,0) * ANGLES(RAD(0 + 6.5 * SIN(SINE / 12)), RAD(0), RAD(3.5 * SIN(SINE / 12))), 1 / Animation_Speed)

				RootJoint.C0 = Clerp(RootJoint.C0,ROOTC0 * CF(0, 0, 0 + 0.25 * COS(SINE / 12)) * ANGLES(RAD(4 + 2.5 * SIN(SINE / 12)), RAD(0), RAD(-25 + 2.5 * SIN(SINE / 12))), 1 / Animation_Speed)
				Neck.C0 = Clerp(Neck.C0, NECKC0 * CF(0, 0, 0 + ((1) - 1)) * ANGLES(RAD(0 + 4.5 * SIN(SINE / 12)), RAD(0), RAD(25 - 2.5 * SIN(SINE / 12))), 1 / Animation_Speed)
				RightShoulder.C0 = Clerp(RightShoulder.C0, CF(1.5, 0.5 + 0.25 * COS(SINE / 12), 0) * ANGLES(RAD(130), RAD(45 - 2.5 * SIN(SINE / 12)), RAD(45 + 7.5 * SIN(SINE / 12))) * RIGHTSHOULDERC0, 1 / Animation_Speed)
				LeftShoulder.C0 = Clerp(LeftShoulder.C0, CF(-1.5, 0.5 + 0.25 * COS(SINE / 12), 0) * ANGLES(RAD(0), RAD(0 + 2.5 * SIN(SINE / 12)), RAD(-5 - 7.5 * SIN(SINE / 12))) * LEFTSHOULDERC0, 1 / Animation_Speed)
				RightHip.C0 = Clerp(RightHip.C0, CF(1, -1, -0.01) * ANGLES(RAD(-2.5 * SIN(SINE / 12)), RAD(75), RAD(0)) * ANGLES(RAD(-8 - 2.5 * SIN(SINE / 12)), RAD(0), RAD(0)), 1 / Animation_Speed)
				LeftHip.C0 = Clerp(LeftHip.C0, CF(-1, -0.5, -0.5) * ANGLES(RAD(-2.5 * SIN(SINE / 12)), RAD(-90), RAD(0)) * ANGLES(RAD(-8 - 2.5 * SIN(SINE / 12)), RAD(0), RAD(0)), 1 / Animation_Speed)
			end
			CreateSound("199150686", RightArm, 3, MRANDOM(8,12)/10)
			for i=0, 0.3, 0.1 / Animation_Speed do
				Swait()
				killnearest(RightArm.CFrame*CF(0,-1,0).p,2,15)
				Weld1.C1 = Clerp(Weld1.C1,CF(0,0,0) * ANGLES(RAD(-3 + 8.5 * SIN(SINE / 12)), RAD(0), RAD(0)), 1 / Animation_Speed)
				Weld2.C1 = Clerp(Weld2.C1,CF(0,0,0) * ANGLES(RAD(4 + 2.5 * SIN(SINE / 12)), RAD(0), RAD(3.5 * SIN(SINE / 12))), 1 / Animation_Speed)
				Weld3.C1 = Clerp(Weld3.C1,CF(0,0,0) * ANGLES(RAD(0 + 6.5 * SIN(SINE / 12)), RAD(0), RAD(-3.5 * SIN(SINE / 12))), 1 / Animation_Speed)
				Weld4.C1 = Clerp(Weld4.C1,CF(0,0,0) * ANGLES(RAD(-3 + 8.5 * SIN(SINE / 12)), RAD(0), RAD(0)), 1 / Animation_Speed)
				Weld5.C1 = Clerp(Weld5.C1,CF(0,0,0) * ANGLES(RAD(4 + 4.5 * SIN(SINE / 12)), RAD(0), RAD(-3.5 * SIN(SINE / 12))), 1 / Animation_Speed)
				Weld6.C1 = Clerp(Weld6.C1,CF(0,0,0) * ANGLES(RAD(0 + 6.5 * SIN(SINE / 12)), RAD(0), RAD(3.5 * SIN(SINE / 12))), 1 / Animation_Speed)

				RootJoint.C0 = Clerp(RootJoint.C0,ROOTC0 * CF(0, 0, 0 + 0.25 * COS(SINE / 12)) * ANGLES(RAD(4 + 2.5 * SIN(SINE / 12)), RAD(0), RAD(15 + 2.5 * SIN(SINE / 12))), 1 / Animation_Speed)
				Neck.C0 = Clerp(Neck.C0, NECKC0 * CF(0, 0, 0 + ((1) - 1)) * ANGLES(RAD(0 + 4.5 * SIN(SINE / 12)), RAD(0), RAD(-15 - 2.5 * SIN(SINE / 12))), 1 / Animation_Speed)
				RightShoulder.C0 = Clerp(RightShoulder.C0, CF(1, 0.5 + 0.25 * COS(SINE / 12), -1) * ANGLES(RAD(65), RAD(45 - 2.5 * SIN(SINE / 12)), RAD(-45 + 7.5 * SIN(SINE / 12))) * RIGHTSHOULDERC0, 1 / Animation_Speed)
				LeftShoulder.C0 = Clerp(LeftShoulder.C0, CF(-1.5, 0.5 + 0.25 * COS(SINE / 12), 0) * ANGLES(RAD(0), RAD(0 + 2.5 * SIN(SINE / 12)), RAD(-5 - 7.5 * SIN(SINE / 12))) * LEFTSHOULDERC0, 1 / Animation_Speed)
				RightHip.C0 = Clerp(RightHip.C0, CF(1, -1, -0.01) * ANGLES(RAD(-2.5 * SIN(SINE / 12)), RAD(75), RAD(0)) * ANGLES(RAD(-8 - 2.5 * SIN(SINE / 12)), RAD(0), RAD(0)), 1 / Animation_Speed)
				LeftHip.C0 = Clerp(LeftHip.C0, CF(-1, -0.5, -0.5) * ANGLES(RAD(-2.5 * SIN(SINE / 12)), RAD(-90), RAD(0)) * ANGLES(RAD(-8 - 2.5 * SIN(SINE / 12)), RAD(0), RAD(0)), 1 / Animation_Speed)
			end
		elseif COMBO == 2 then
			COMBO = 1
			for i=0, 0.3, 0.1 / Animation_Speed do
				Swait()
				Weld1.C1 = Clerp(Weld1.C1,CF(0,0,0) * ANGLES(RAD(-3 + 8.5 * SIN(SINE / 12)), RAD(0), RAD(0)), 1 / Animation_Speed)
				Weld2.C1 = Clerp(Weld2.C1,CF(0,0,0) * ANGLES(RAD(4 + 2.5 * SIN(SINE / 12)), RAD(0), RAD(3.5 * SIN(SINE / 12))), 1 / Animation_Speed)
				Weld3.C1 = Clerp(Weld3.C1,CF(0,0,0) * ANGLES(RAD(0 + 6.5 * SIN(SINE / 12)), RAD(0), RAD(-3.5 * SIN(SINE / 12))), 1 / Animation_Speed)
				Weld4.C1 = Clerp(Weld4.C1,CF(0,0,0) * ANGLES(RAD(-3 + 8.5 * SIN(SINE / 12)), RAD(0), RAD(0)), 1 / Animation_Speed)
				Weld5.C1 = Clerp(Weld5.C1,CF(0,0,0) * ANGLES(RAD(4 + 4.5 * SIN(SINE / 12)), RAD(0), RAD(-3.5 * SIN(SINE / 12))), 1 / Animation_Speed)
				Weld6.C1 = Clerp(Weld6.C1,CF(0,0,0) * ANGLES(RAD(0 + 6.5 * SIN(SINE / 12)), RAD(0), RAD(3.5 * SIN(SINE / 12))), 1 / Animation_Speed)

				RootJoint.C0 = Clerp(RootJoint.C0,ROOTC0 * CF(0, 0, 0 + 0.25 * COS(SINE / 12)) * ANGLES(RAD(4 + 2.5 * SIN(SINE / 12)), RAD(0), RAD(15 + 2.5 * SIN(SINE / 12))), 1 / Animation_Speed)
				Neck.C0 = Clerp(Neck.C0, NECKC0 * CF(0, 0, 0 + ((1) - 1)) * ANGLES(RAD(0 + 4.5 * SIN(SINE / 12)), RAD(0), RAD(-15 - 2.5 * SIN(SINE / 12))), 1 / Animation_Speed)
				RightShoulder.C0 = Clerp(RightShoulder.C0, CF(1.5, 0.5 + 0.25 * COS(SINE / 12), 0) * ANGLES(RAD(0), RAD(0 - 2.5 * SIN(SINE / 12)), RAD(5 + 7.5 * SIN(SINE / 12))) * RIGHTSHOULDERC0, 1 / Animation_Speed)
				LeftShoulder.C0 = Clerp(LeftShoulder.C0, CF(-1.5, 0.5 + 0.25 * COS(SINE / 12), 0) * ANGLES(RAD(0), RAD(0 + 2.5 * SIN(SINE / 12)), RAD(-90 - 7.5 * SIN(SINE / 12))) * ANGLES(RAD(0), RAD(90), RAD(0)) * LEFTSHOULDERC0, 1 / Animation_Speed)
				RightHip.C0 = Clerp(RightHip.C0, CF(1, -1, -0.01) * ANGLES(RAD(-2.5 * SIN(SINE / 12)), RAD(75), RAD(0)) * ANGLES(RAD(-8 - 2.5 * SIN(SINE / 12)), RAD(0), RAD(0)), 1 / Animation_Speed)
				LeftHip.C0 = Clerp(LeftHip.C0, CF(-1, -0.5, -0.5) * ANGLES(RAD(-2.5 * SIN(SINE / 12)), RAD(-90), RAD(0)) * ANGLES(RAD(-8 - 2.5 * SIN(SINE / 12)), RAD(0), RAD(0)), 1 / Animation_Speed)
			end
			CreateSound("199150686", LeftArm, 3, MRANDOM(8,12)/10)
			for i=0, 0.3, 0.1 / Animation_Speed do
				Swait()
				killnearest(LeftArm.CFrame*CF(0,-1,0).p,2,15)
				Weld1.C1 = Clerp(Weld1.C1,CF(0,0,0) * ANGLES(RAD(-3 + 8.5 * SIN(SINE / 12)), RAD(0), RAD(0)), 1 / Animation_Speed)
				Weld2.C1 = Clerp(Weld2.C1,CF(0,0,0) * ANGLES(RAD(4 + 2.5 * SIN(SINE / 12)), RAD(0), RAD(3.5 * SIN(SINE / 12))), 1 / Animation_Speed)
				Weld3.C1 = Clerp(Weld3.C1,CF(0,0,0) * ANGLES(RAD(0 + 6.5 * SIN(SINE / 12)), RAD(0), RAD(-3.5 * SIN(SINE / 12))), 1 / Animation_Speed)
				Weld4.C1 = Clerp(Weld4.C1,CF(0,0,0) * ANGLES(RAD(-3 + 8.5 * SIN(SINE / 12)), RAD(0), RAD(0)), 1 / Animation_Speed)
				Weld5.C1 = Clerp(Weld5.C1,CF(0,0,0) * ANGLES(RAD(4 + 4.5 * SIN(SINE / 12)), RAD(0), RAD(-3.5 * SIN(SINE / 12))), 1 / Animation_Speed)
				Weld6.C1 = Clerp(Weld6.C1,CF(0,0,0) * ANGLES(RAD(0 + 6.5 * SIN(SINE / 12)), RAD(0), RAD(3.5 * SIN(SINE / 12))), 1 / Animation_Speed)

				RootJoint.C0 = Clerp(RootJoint.C0,ROOTC0 * CF(0, 0, 0 + 0.25 * COS(SINE / 12)) * ANGLES(RAD(4 + 2.5 * SIN(SINE / 12)), RAD(0), RAD(-25 + 2.5 * SIN(SINE / 12))), 1 / Animation_Speed)
				Neck.C0 = Clerp(Neck.C0, NECKC0 * CF(0, 0, 0 + ((1) - 1)) * ANGLES(RAD(0 + 4.5 * SIN(SINE / 12)), RAD(0), RAD(25 - 2.5 * SIN(SINE / 12))), 1 / Animation_Speed)
				RightShoulder.C0 = Clerp(RightShoulder.C0, CF(1.5, 0.5 + 0.25 * COS(SINE / 12), 0) * ANGLES(RAD(0), RAD(0 - 2.5 * SIN(SINE / 12)), RAD(5 + 7.5 * SIN(SINE / 12))) * RIGHTSHOULDERC0, 1 / Animation_Speed)
				LeftShoulder.C0 = Clerp(LeftShoulder.C0, CF(-1, 0.5 + 0.25 * COS(SINE / 12), -1) * ANGLES(RAD(0), RAD(0 + 2.5 * SIN(SINE / 12)), RAD(90 - 7.5 * SIN(SINE / 12))) * ANGLES(RAD(0), RAD(-90), RAD(0)) * LEFTSHOULDERC0, 1 / Animation_Speed)
				RightHip.C0 = Clerp(RightHip.C0, CF(1, -1, -0.01) * ANGLES(RAD(-2.5 * SIN(SINE / 12)), RAD(75), RAD(0)) * ANGLES(RAD(-8 - 2.5 * SIN(SINE / 12)), RAD(0), RAD(0)), 1 / Animation_Speed)
				LeftHip.C0 = Clerp(LeftHip.C0, CF(-1, -0.5, -0.5) * ANGLES(RAD(-2.5 * SIN(SINE / 12)), RAD(-90), RAD(0)) * ANGLES(RAD(-8 - 2.5 * SIN(SINE / 12)), RAD(0), RAD(0)), 1 / Animation_Speed)
			end
		end
		ATTACK = false
		Rooted = false
	end

	function Defiant_Blast()
		local CENTER = CreatePart(3, Effects, "SmoothPlastic", 0, 1, SKILLTEXTCOLOR, "CenterPart", VT(0,0,0))
		local RAY = CreatePart(3, Effects, "Neon", 0, 1, C3(0,0,0), "Laser01", VT(25,25,25))
		RAY.Color = SKILLTEXTCOLOR
		MakeForm(RAY,"Ball")
		local RAY2 = CreatePart(3, Effects, "Neon", 0, 1, C3(0,0,0), "Laser01", VT(25,25,25))
		RAY2.Color = C3(1,0,0)
		MakeForm(RAY2,"Ball")
		local ECH = Mouse.Hit.p
		CENTER.CFrame = CF(Mouse.Hit.p)
		RAY.CFrame = CENTER.CFrame
		RAY2.CFrame = RAY.CFrame
		for i = 1, 120 do
			Swait()
			if MRANDOM(1,5) == 1 then
				CreateSound("168586586", CENTER, 1, MRANDOM(15,20)/10)
				local POS = ECH+VT(MRANDOM(-5,5),MRANDOM(-5,5),MRANDOM(-5,5))
				local ZAPTABLE = Zap({StartPosition = ECH, TargetPosition = POS, Character = workspace, Color = "Really red", Individual = true, MaxRange = 15,SegmentLength = 3, Offset = 3})
				Debris:AddItem(ZAPTABLE.LightningModel,0.1)
			end
			RAY.Size = RAY.Size * 0.99
			RAY.Transparency = RAY.Transparency - 1/60
			RAY2.Size = RAY.Size + VT(1,1,1)
			RAY2.Transparency = RAY2.Transparency - 1/150
		end
		killnearest(ECH,45,250)
		MagicSphere(VT(0,0,0),25,CF(ECH),C3(1,0,0),VT(2,2,2))
		MagicSphere(VT(0,0,0),75,CF(ECH),C3(0,0,0),VT(1.8,1.8,1.8))
		CreateSound("466493476", CENTER, 10, 1)
		Debris:AddItem(CENTER,5)
		RAY:remove()
		RAY2:remove()
	end

	function Pain_Wave()
		ATTACK = true
		Rooted = true
		local ENERGY = 0
		local GYRO = IT("BodyGyro",RootPart)
		GYRO.D = 100
		GYRO.P = 2000
		GYRO.MaxTorque = VT(0,4000000,0)
		GYRO.cframe = CF(RootPart.Position,Mouse.Hit.p)
		for i=0, 4, 0.1 / Animation_Speed do
			Swait()
			GYRO.cframe = CF(RootPart.Position,Mouse.Hit.p)
			if MRANDOM(1,5) == 1 then
				ENERGY = ENERGY + 1
				CreateSound("168586586", Torso, 1, MRANDOM(15,20)/10)
				local POS = RightArm.CFrame*CF(0,-1,0).p+VT(MRANDOM(-5,5),MRANDOM(-5,5),MRANDOM(-5,5))
				local ZAPTABLE = Zap({SIZE = 0.05,StartPosition = RightArm.CFrame*CF(0,-2,0).p, TargetPosition = RightArm.Position, Character = workspace, Color = "Really red", Individual = true, MaxRange = 3,SegmentLength = 0.5, Offset = 1})
				Debris:AddItem(ZAPTABLE.LightningModel,0.1)
			end
			if MRANDOM(1,5) == 1 then
				ENERGY = ENERGY + 1
				CreateSound("168586586", Torso, 1, MRANDOM(15,20)/10)
				local POS = LeftArm.CFrame*CF(0,-1,0).p+VT(MRANDOM(-5,5),MRANDOM(-5,5),MRANDOM(-5,5))
				local ZAPTABLE = Zap({SIZE = 0.05,StartPosition = LeftArm.CFrame*CF(0,-2,0).p, TargetPosition = LeftArm.Position, Character = workspace, Color = "Really red", Individual = true, MaxRange = 3,SegmentLength = 0.5, Offset = 1})
				Debris:AddItem(ZAPTABLE.LightningModel,0.1)
			end
			Weld1.C1 = Clerp(Weld1.C1,CF(0,0,0) * ANGLES(RAD(-3 + 8.5 * SIN(SINE / 12)), RAD(0), RAD(0)), 1 / Animation_Speed)
			Weld2.C1 = Clerp(Weld2.C1,CF(0,0,0) * ANGLES(RAD(4 + 2.5 * SIN(SINE / 12)), RAD(0), RAD(3.5 * SIN(SINE / 12))), 1 / Animation_Speed)
			Weld3.C1 = Clerp(Weld3.C1,CF(0,0,0) * ANGLES(RAD(0 + 6.5 * SIN(SINE / 12)), RAD(0), RAD(-3.5 * SIN(SINE / 12))), 1 / Animation_Speed)
			Weld4.C1 = Clerp(Weld4.C1,CF(0,0,0) * ANGLES(RAD(-3 + 8.5 * SIN(SINE / 12)), RAD(0), RAD(0)), 1 / Animation_Speed)
			Weld5.C1 = Clerp(Weld5.C1,CF(0,0,0) * ANGLES(RAD(4 + 4.5 * SIN(SINE / 12)), RAD(0), RAD(-3.5 * SIN(SINE / 12))), 1 / Animation_Speed)
			Weld6.C1 = Clerp(Weld6.C1,CF(0,0,0) * ANGLES(RAD(0 + 6.5 * SIN(SINE / 12)), RAD(0), RAD(3.5 * SIN(SINE / 12))), 1 / Animation_Speed)

			RootJoint.C0 = Clerp(RootJoint.C0,ROOTC0 * CF(0, 0, 0 + 0.25 * COS(SINE / 12)) * ANGLES(RAD(4 + 2.5 * SIN(SINE / 12)), RAD(0), RAD(5 + 2.5 * SIN(SINE / 12))), 1 / Animation_Speed)
			Neck.C0 = Clerp(Neck.C0, NECKC0 * CF(0, 0, 0 + ((1) - 1)) * ANGLES(RAD(-25 + 4.5 * SIN(SINE / 12)), RAD(0), RAD(-5 - 2.5 * SIN(SINE / 12))), 1 / Animation_Speed)
			RightShoulder.C0 = Clerp(RightShoulder.C0, CF(1.5, 0.5 + 0.25 * COS(SINE / 12), 0) * ANGLES(RAD(0), RAD(0 - 2.5 * SIN(SINE / 12)), RAD(75 + 7.5 * SIN(SINE / 12))) * RIGHTSHOULDERC0, 1 / Animation_Speed)
			LeftShoulder.C0 = Clerp(LeftShoulder.C0, CF(-1.5, 0.5 + 0.25 * COS(SINE / 12), 0) * ANGLES(RAD(0), RAD(0 + 2.5 * SIN(SINE / 12)), RAD(-75 - 7.5 * SIN(SINE / 12))) * LEFTSHOULDERC0, 1 / Animation_Speed)
			RightHip.C0 = Clerp(RightHip.C0, CF(1, -1, -0.01) * ANGLES(RAD(-2.5 * SIN(SINE / 12)), RAD(75), RAD(0)) * ANGLES(RAD(-8 - 2.5 * SIN(SINE / 12)), RAD(0), RAD(0)), 1 / Animation_Speed)
			LeftHip.C0 = Clerp(LeftHip.C0, CF(-1, -0.5, -0.5) * ANGLES(RAD(-2.5 * SIN(SINE / 12)), RAD(-90), RAD(0)) * ANGLES(RAD(-8 - 2.5 * SIN(SINE / 12)), RAD(0), RAD(0)), 1 / Animation_Speed)
		end
		GYRO:remove()
		local RATE = 45
		for i = 1, 3 do
			coroutine.resume(coroutine.create(function()
				local BOMB = CreatePart(3, Effects, "Neon", 0, 1, "Really red", "ORB", VT(4,4,4))
				CreateSound("215395388", BOMB, 10, MRANDOM(15,20)/10)
				BOMB.CFrame = RootPart.CFrame*ANGLES(RAD(0),RAD(RATE),RAD(0))
				local GUI = Instance.new("BillboardGui",BOMB)
				GUI.Size = UDim2.new(35,0,35,0)
				GUI.Adornee = BOMB
				local GUI2 = IT("ImageLabel",GUI)
				GUI2.BackgroundTransparency = 1
				GUI2.BorderSizePixel = 0
				GUI2.Size = UDim2.new(1,0,1,0)
				GUI2.SizeConstraint = "RelativeYY"
				GUI2.ImageColor3 = C3(1,0,0)
				GUI2.Image = "http://www.roblox.com/asset/?id=20254717"
				local AURA = CreatePart(3, BOMB, "Neon", 0, 1, "Really red", "ORB", VT(4.2,4.2,4.2))
				AURA.CFrame = BOMB.CFrame
				AURA.Color = C3(0,0,0)
				MakeForm(BOMB,"Ball")
				MakeForm(AURA,"Ball")
				for i = 1, 200 do
					Swait()
					killnearest(BOMB.CFrame*CF(0,0,-8).p,25,-25)
					--CreateWave(VT(7,0.3,7),25,BOMB.CFrame*CF(0,0,1)*ANGLES(RAD(90),RAD(0),RAD(0)),true,25,C3(1,0,0),-VT(0.1,0,0.1))
					--CreateWave(VT(15,0.3,15),10,BOMB.CFrame*CF(0,0,-8)*ANGLES(RAD(90),RAD(0),RAD(0)),true,25,C3(MRANDOM(0,10)/10,0,0),VT(3,0,3))
					BOMB.CFrame = BOMB.CFrame*CF(0,0,-1)
					AURA.CFrame = BOMB.CFrame
					for _, c in pairs(workspace:GetChildren()) do
						if c.ClassName == "Model" then
							if c ~= Character and c:FindFirstChildOfClass("Humanoid") and (c:FindFirstChild("Torso") or c:FindFirstChild("UpperTorso")) then
								local HUMANOID = c:FindFirstChildOfClass("Humanoid")
								if HUMANOID.Health > 0 then
									local TORSO = (c:FindFirstChild("Torso") or c:FindFirstChild("UpperTorso"))
									if (TORSO.Position - BOMB.Position).Magnitude < 65 then
										BOMB.CFrame = CF(BOMB.Position,TORSO.Position)
									end
								end
							end
						end
					end
					if i <= 10 then
						BOMB.Transparency = BOMB.Transparency - 0.1
						AURA.Transparency = AURA.Transparency - 0.05
					end
				end
				BOMB:remove()
			end))
			RATE = RATE - 45
		end
		ATTACK = false
		Rooted = false
	end

	game.StarterGui:SetCore("SendNotification", {
		Title = "The Defiant";
		Text = "Made by MoonVM!!!";
		Icon = "rbxassetid://579070527";
		Duration = 5; 
	})

	function Violence()
		local HITFLOOR,HITPOS,NORMAL = Raycast(RootPart.Position, (CF(RootPart.Position, RootPart.Position + VT(0, -1, 0))).lookVector, 7 * Player_Size, Character)
		if HITFLOOR ~= nil then
			local HITBODIES = {}
			ATTACK = true
			Rooted = true
			local ABSOLUTE = CreatePart(3, Effects, "Neon", 0, 1, "Really black", "SuperNova", VT(0,0,0))
			ABSOLUTE.Shape = "Ball"
			ABSOLUTE.Color = SKILLTEXTCOLOR
			MakeForm(ABSOLUTE,"Ball")
			CreateSound("469204826", ABSOLUTE, 10, 1)
			for i=0, 4, 0.1 / Animation_Speed do
				Swait()
				ABSOLUTE.Size = ABSOLUTE.Size + VT(0.2,0.2,0.2)
				ABSOLUTE.CFrame = RootPart.CFrame*CF(0,5+(ABSOLUTE.Size.Y/2),0)
				ABSOLUTE.Transparency = ABSOLUTE.Transparency - 0.01
				local CHARGE = CreatePart(3, Effects, "Neon", 0, 0, "Really red", "Star", VT(1,1,1)*MRANDOM(5,15)/10)
				MakeForm(CHARGE,"Ball")
				CHARGE.Color = C3(0,0,0)
				CHARGE.CFrame = CF(RootPart.Position) * CF(MRANDOM(-15,15),-6,MRANDOM(-15,15))
				local BONE = CreatePart(3, Effects, "Neon", 0, 0, "Salmon", "Bone", VT(1,1,1)*MRANDOM(5,35)/10)
				local MESHES = {"36869983","36780113","36780195","36780156","36780032","36780079"}
				BONE.CFrame = CF(RootPart.Position) * CF(MRANDOM(-15,15),-6,MRANDOM(-15,15))*ANGLES(RAD(MRANDOM(-180,180)),RAD(MRANDOM(-180,180)),RAD(MRANDOM(-180,180)))
				CreateMesh("SpecialMesh", BONE, "FileMesh", MESHES[MRANDOM(1,#MESHES)], "", VT(1,1,1), VT(0,0,0))
				FireArc(CHARGE,ABSOLUTE.Position,45,45,true)
				FireArc(BONE,ABSOLUTE.Position,45,45,true)
				RootJoint.C0 = Clerp(RootJoint.C0,ROOTC0 * CF(0, 0, 0 + 0.25 * COS(SINE / 12)) * ANGLES(RAD(4 + 2.5 * SIN(SINE / 12)), RAD(0), RAD(15 + 2.5 * SIN(SINE / 12))), 1 / Animation_Speed)
				Neck.C0 = Clerp(Neck.C0, NECKC0 * CF(0, 0, 0 + ((1) - 1)) * ANGLES(RAD(-25 + 4.5 * SIN(SINE / 12)), RAD(25), RAD(-15 - 2.5 * SIN(SINE / 12))), 1 / Animation_Speed)
				RightShoulder.C0 = Clerp(RightShoulder.C0, CF(1.25, 1.5 + 0.25 * COS(SINE / 12), 0) * ANGLES(RAD(170), RAD(0 - 7.5 * SIN(SINE / 12)), RAD(-12 + 7.5 * SIN(SINE / 12))) * RIGHTSHOULDERC0, 1 / Animation_Speed)
				LeftShoulder.C0 = Clerp(LeftShoulder.C0, CF(-1.5, 0.5 + 0.25 * COS(SINE / 12), 0) * ANGLES(RAD(0), RAD(0 + 7.5 * SIN(SINE / 12)), RAD(-12 - 7.5 * SIN(SINE / 12))) * LEFTSHOULDERC0, 1 / Animation_Speed)
				RightHip.C0 = Clerp(RightHip.C0, CF(1, -1, -0.01) * ANGLES(RAD(-7.5 * SIN(SINE / 12)), RAD(75), RAD(0)) * ANGLES(RAD(-8 - 2.5 * SIN(SINE / 12)), RAD(0), RAD(0)), 1 / Animation_Speed)
				LeftHip.C0 = Clerp(LeftHip.C0, CF(-1, -0.5, -0.5) * ANGLES(RAD(-7.5 * SIN(SINE / 12)), RAD(-90), RAD(0)) * ANGLES(RAD(-8 - 2.5 * SIN(SINE / 12)), RAD(0), RAD(0)), 1 / Animation_Speed)
			end
			local TAUNTS = {"907333406","907330103","907332856"}
			Speak(TAUNTS[MRANDOM(1,#TAUNTS)],"Taunt")
			for i=0, 2, 0.1 / Animation_Speed do
				Swait()
				RootJoint.C0 = Clerp(RootJoint.C0,ROOTC0 * CF(0, 0, 0 + 0.25 * COS(SINE / 12)) * ANGLES(RAD(4 + 2.5 * SIN(SINE / 12)), RAD(0), RAD(15 + 2.5 * SIN(SINE / 12))), 1 / Animation_Speed)
				Neck.C0 = Clerp(Neck.C0, NECKC0 * CF(0, 0, 0 + ((1) - 1)) * ANGLES(RAD(-25 + 4.5 * SIN(SINE / 12)), RAD(25), RAD(-15 - 2.5 * SIN(SINE / 12))), 1 / Animation_Speed)
				RightShoulder.C0 = Clerp(RightShoulder.C0, CF(1.25, 1.5 + 0.25 * COS(SINE / 12), 0) * ANGLES(RAD(170), RAD(0 - 7.5 * SIN(SINE / 12)), RAD(-12 + 7.5 * SIN(SINE / 12))) * RIGHTSHOULDERC0, 1 / Animation_Speed)
				LeftShoulder.C0 = Clerp(LeftShoulder.C0, CF(-1.5, 0.5 + 0.25 * COS(SINE / 12), 0) * ANGLES(RAD(0), RAD(0 + 7.5 * SIN(SINE / 12)), RAD(-12 - 7.5 * SIN(SINE / 12))) * LEFTSHOULDERC0, 1 / Animation_Speed)
				RightHip.C0 = Clerp(RightHip.C0, CF(1, -1, -0.01) * ANGLES(RAD(-7.5 * SIN(SINE / 12)), RAD(75), RAD(0)) * ANGLES(RAD(-8 - 2.5 * SIN(SINE / 12)), RAD(0), RAD(0)), 1 / Animation_Speed)
				LeftHip.C0 = Clerp(LeftHip.C0, CF(-1, -0.5, -0.5) * ANGLES(RAD(-7.5 * SIN(SINE / 12)), RAD(-90), RAD(0)) * ANGLES(RAD(-8 - 2.5 * SIN(SINE / 12)), RAD(0), RAD(0)), 1 / Animation_Speed)
			end
			coroutine.resume(coroutine.create(function()
				local sphere = ABSOLUTE
				local hit2 = sphere.Touched:connect(function(hit) 
					if hit.Parent ~= Character and hit.Parent.Parent ~= Character and hit.Parent ~= Effects and hit.Anchored == false and hit:FindFirstChild("Vanishing") == nil then
						local vanish = Instance.new("BoolValue",hit)
						vanish.Name = "Vanishing"
						hit.Anchored = true
						for i = 1, 30 do
							Swait()
							hit.Transparency = hit.Transparency + 1/30
						end
						hit:remove()
					end
				end)
				local childList = {}
				function checkObject(obj) -- This is basically a function that finds all unanchored parts and adds them to childList.
					if (obj ~= sphere) and (obj.className == "Part") then
						if (obj.Anchored == false) then
							table.insert(childList, 1, obj)
						end
					elseif (obj.className == "Model") or (obj.className == "Hat") or (obj.className == "Tool") or (obj == workspace) then
						local child = obj:GetChildren()
						for x = 1, #child do
							checkObject(child[x])
						end
						obj.ChildAdded:connect(checkObject)
					end
				end
				checkObject(workspace)
				local n = 0
				local count = 0
				for i = 1, 450 do
					Slice("Thin",ABSOLUTE.Size.X/15,15,ABSOLUTE.CFrame * ANGLES(RAD(MRANDOM(-180,180)),RAD(MRANDOM(-180,180)),RAD(MRANDOM(-180,180))),"Really black",VT(-0.01,0,-0.01))
					Slice("Round",ABSOLUTE.Size.X/18,15,ABSOLUTE.CFrame * ANGLES(RAD(MRANDOM(-180,180)),RAD(MRANDOM(-180,180)),RAD(MRANDOM(-180,180))),"Really black",VT(-0.01,0,-0.01))
					Swait()
					sphere.Size = sphere.Size + VT(0.3,0.3,0.3)
					count = count + 1
					if n < #childList then
						n = n + 1
						if n % 800 == 0 then
							Swait()
						end
					else
						n = 1
						Swait()
					end
					local child = childList[n]
					if (child ~= sphere) and (child.Parent ~= Character) and (child.className == "Part") and (child.Anchored == false) then
						local relPos = sphere.Position - child.Position
						local motivator = child:FindFirstChild("BlackHole Influence")
						if relPos.magnitude < 150 then
							--child.RotVelocity = cross(child.CFrame.lookVector, relPos) * 20 / relPos.magnitude
							--child:BreakJoints()
							if (relPos.magnitude < 200) and (child.Size.z + sphere.Size.x/2 >  relPos.magnitude * 2 - 4) then
								child:Remove()
								table.remove(childList, n)
								n = n - 1 -- This is the reason I need a counter of my own design
							else
								child.CanCollide = false -- I can assume that the child will not escape the black hole.
								if motivator == nil then
									motivator = Instance.new("BodyPosition")
									motivator.Parent = child
									motivator.Name = "BlackHole Influence"
								end
								motivator.position = sphere.Position
								motivator.maxForce = Vector3.new(1, 1, 1) * 80000000
								Debris:AddItem(motivator,0.5)
							end
						elseif motivator ~= nil then
							motivator:Remove()
						end
					end
				end
				for i = 1, 10 do
					Swait()
					sphere.Transparency = i/10
				end
				sphere:remove()
			end))
			ATTACK = false
			Rooted = false
		end
	end

	local Decal = IT("Decal")

	function Hop()
		ATTACK = true
		Rooted = false
		local O1 = CreatePart(3, Effects, "Neon", 0, 1, "Really red", "Warphole", VT(0,0,0))
		O1.CFrame = RootPart.CFrame*CF(0,0,-3)*ANGLES(RAD(90),RAD(0),RAD(0))
		local decal = Decal:Clone()
		decal.Parent = O1
		decal.Face = "Top"
		decal.Texture = "http://www.roblox.com/asset/?id=418573253"
		local decal2 = Decal:Clone()
		decal2.Parent = O1
		decal2.Face = "Bottom"
		decal2.Texture = "http://www.roblox.com/asset/?id=418573253"
		local O2 = CreatePart(3, Effects, "Neon", 0, 1, "Really red", "Warphole", VT(0,0,0))
		local POS = VT(RootPart.Position.X,Mouse.Hit.p.Y+6,RootPart.Position.Z)
		O2.CFrame = CF(Mouse.Hit.p+VT(0,6,0),POS)*ANGLES(RAD(90),RAD(0),RAD(0))
		local ROOT = CreatePart(3, Effects, "Neon", 0, 1, "Really red", "Warphole", VT(0,0,0))
		ROOT.CFrame = CF(O2.Position,RootPart.Position)
		local decal = Decal:Clone()
		decal.Parent = O2
		decal.Face = "Top"
		decal.Texture = "http://www.roblox.com/asset/?id=418573253"
		local decal2 = Decal:Clone()
		decal2.Parent = O2
		decal2.Face = "Bottom"
		decal2.Texture = "http://www.roblox.com/asset/?id=418573253"
		CreateSound("84005018", O1, 10, 0.7)
		CreateSound("84005018", O2, 10, 0.7)
		for i = 1, 75 do
			Swait()
			Weld1.C1 = Clerp(Weld1.C1,CF(0,0,0) * ANGLES(RAD(-3 + 8.5 * SIN(SINE / 12)), RAD(0), RAD(0)), 1 / Animation_Speed)
			Weld2.C1 = Clerp(Weld2.C1,CF(0,0,0) * ANGLES(RAD(4 + 2.5 * SIN(SINE / 12)), RAD(0), RAD(3.5 * SIN(SINE / 12))), 1 / Animation_Speed)
			Weld3.C1 = Clerp(Weld3.C1,CF(0,0,0) * ANGLES(RAD(0 + 6.5 * SIN(SINE / 12)), RAD(0), RAD(-3.5 * SIN(SINE / 12))), 1 / Animation_Speed)
			Weld4.C1 = Clerp(Weld4.C1,CF(0,0,0) * ANGLES(RAD(-3 + 8.5 * SIN(SINE / 12)), RAD(0), RAD(0)), 1 / Animation_Speed)
			Weld5.C1 = Clerp(Weld5.C1,CF(0,0,0) * ANGLES(RAD(4 + 4.5 * SIN(SINE / 12)), RAD(0), RAD(-3.5 * SIN(SINE / 12))), 1 / Animation_Speed)
			Weld6.C1 = Clerp(Weld6.C1,CF(0,0,0) * ANGLES(RAD(0 + 6.5 * SIN(SINE / 12)), RAD(0), RAD(3.5 * SIN(SINE / 12))), 1 / Animation_Speed)

			O1.Size = O1.Size + VT(0.1,0,0.1)
			O1.CFrame = RootPart.CFrame*CF(0,0,-3)*ANGLES(RAD(90),RAD(i),RAD(0))
			O2.Size = O2.Size + VT(0.1,0,0.1)
			O2.CFrame = O2.CFrame*ANGLES(RAD(0),RAD(i),RAD(0))
			RootJoint.C0 = Clerp(RootJoint.C0,ROOTC0 * CF(0, 0, 0 + 0.25 * COS(SINE / 12)) * ANGLES(RAD(4 + 2.5 * SIN(SINE / 12)), RAD(0), RAD(5 + 2.5 * SIN(SINE / 12))), 1 / Animation_Speed)
			Neck.C0 = Clerp(Neck.C0, NECKC0 * CF(0, 0, 0 + ((1) - 1)) * ANGLES(RAD(0 + 4.5 * SIN(SINE / 12)), RAD(0), RAD(-5 - 2.5 * SIN(SINE / 12))), 1 / Animation_Speed)
			RightShoulder.C0 = Clerp(RightShoulder.C0, CF(1.5, 0.5 + 0.25 * COS(SINE / 12), 0) * ANGLES(RAD(90), RAD(0 - 2.5 * SIN(SINE / 12)), RAD(5 + 7.5 * SIN(SINE / 12))) * RIGHTSHOULDERC0, 1 / Animation_Speed)
			LeftShoulder.C0 = Clerp(LeftShoulder.C0, CF(-1.5, 0.5 + 0.25 * COS(SINE / 12), 0) * ANGLES(RAD(90), RAD(0 + 2.5 * SIN(SINE / 12)), RAD(-5 - 7.5 * SIN(SINE / 12))) * LEFTSHOULDERC0, 1 / Animation_Speed)
			RightHip.C0 = Clerp(RightHip.C0, CF(1, -1, -0.01) * ANGLES(RAD(-2.5 * SIN(SINE / 12)), RAD(75), RAD(0)) * ANGLES(RAD(-8 - 2.5 * SIN(SINE / 12)), RAD(0), RAD(0)), 1 / Animation_Speed)
			LeftHip.C0 = Clerp(LeftHip.C0, CF(-1, -0.5, -0.5) * ANGLES(RAD(-2.5 * SIN(SINE / 12)), RAD(-90), RAD(0)) * ANGLES(RAD(-8 - 2.5 * SIN(SINE / 12)), RAD(0), RAD(0)), 1 / Animation_Speed)
		end
		Rooted = true
		UNANCHOR = false
		RootPart.Anchored = true
		VALUE1 = true
		for i = 1, 15 do
			Transparency(i/15)
			Swait()
			Weld1.C1 = Clerp(Weld1.C1,CF(0,0,0) * ANGLES(RAD(-3 + 8.5 * SIN(SINE / 12)), RAD(0), RAD(0)), 1 / Animation_Speed)
			Weld2.C1 = Clerp(Weld2.C1,CF(0,0,0) * ANGLES(RAD(4 + 2.5 * SIN(SINE / 12)), RAD(0), RAD(3.5 * SIN(SINE / 12))), 1 / Animation_Speed)
			Weld3.C1 = Clerp(Weld3.C1,CF(0,0,0) * ANGLES(RAD(0 + 6.5 * SIN(SINE / 12)), RAD(0), RAD(-3.5 * SIN(SINE / 12))), 1 / Animation_Speed)
			Weld4.C1 = Clerp(Weld4.C1,CF(0,0,0) * ANGLES(RAD(-3 + 8.5 * SIN(SINE / 12)), RAD(0), RAD(0)), 1 / Animation_Speed)
			Weld5.C1 = Clerp(Weld5.C1,CF(0,0,0) * ANGLES(RAD(4 + 4.5 * SIN(SINE / 12)), RAD(0), RAD(-3.5 * SIN(SINE / 12))), 1 / Animation_Speed)
			Weld6.C1 = Clerp(Weld6.C1,CF(0,0,0) * ANGLES(RAD(0 + 6.5 * SIN(SINE / 12)), RAD(0), RAD(3.5 * SIN(SINE / 12))), 1 / Animation_Speed)

			RootPart.CFrame = RootPart.CFrame*CF(0,0,-0.13)
			RootJoint.C0 = Clerp(RootJoint.C0,ROOTC0 * CF(0, 0, 0 + 0.25 * COS(SINE / 12)) * ANGLES(RAD(16 + 2.5 * SIN(SINE / 12)), RAD(0), RAD(5 + 2.5 * SIN(SINE / 12))), 1 / Animation_Speed)
			Neck.C0 = Clerp(Neck.C0, NECKC0 * CF(0, 0, 0 + ((1) - 1)) * ANGLES(RAD(-15 + 4.5 * SIN(SINE / 12)), RAD(0), RAD(-5 - 2.5 * SIN(SINE / 12))), 1 / Animation_Speed)
			RightShoulder.C0 = Clerp(RightShoulder.C0, CF(1.5, 0.5 + 0.25 * COS(SINE / 12), 0) * ANGLES(RAD(-15), RAD(0 - 2.5 * SIN(SINE / 12)), RAD(5 + 7.5 * SIN(SINE / 12))) * RIGHTSHOULDERC0, 1 / Animation_Speed)
			LeftShoulder.C0 = Clerp(LeftShoulder.C0, CF(-1.5, 0.5 + 0.25 * COS(SINE / 12), 0) * ANGLES(RAD(-15), RAD(0 + 2.5 * SIN(SINE / 12)), RAD(-5 - 7.5 * SIN(SINE / 12))) * LEFTSHOULDERC0, 1 / Animation_Speed)
			RightHip.C0 = Clerp(RightHip.C0, CF(1, -1, -0.01) * ANGLES(RAD(-2.5 * SIN(SINE / 12)), RAD(75), RAD(0)) * ANGLES(RAD(-8 - 2.5 * SIN(SINE / 12)), RAD(0), RAD(0)), 1 / Animation_Speed)
			LeftHip.C0 = Clerp(LeftHip.C0, CF(-1, -0.5, -0.5) * ANGLES(RAD(-2.5 * SIN(SINE / 12)), RAD(-90), RAD(0)) * ANGLES(RAD(-8 - 2.5 * SIN(SINE / 12)), RAD(0), RAD(0)), 1 / Animation_Speed)
		end
		RootPart.CFrame = ROOT.CFrame
		ROOT:remove()
		for i = 1, 15 do
			Transparency(1-(i/15))
			Swait()
			Weld1.C1 = Clerp(Weld1.C1,CF(0,0,0) * ANGLES(RAD(-3 + 8.5 * SIN(SINE / 12)), RAD(0), RAD(0)), 1 / Animation_Speed)
			Weld2.C1 = Clerp(Weld2.C1,CF(0,0,0) * ANGLES(RAD(4 + 2.5 * SIN(SINE / 12)), RAD(0), RAD(3.5 * SIN(SINE / 12))), 1 / Animation_Speed)
			Weld3.C1 = Clerp(Weld3.C1,CF(0,0,0) * ANGLES(RAD(0 + 6.5 * SIN(SINE / 12)), RAD(0), RAD(-3.5 * SIN(SINE / 12))), 1 / Animation_Speed)
			Weld4.C1 = Clerp(Weld4.C1,CF(0,0,0) * ANGLES(RAD(-3 + 8.5 * SIN(SINE / 12)), RAD(0), RAD(0)), 1 / Animation_Speed)
			Weld5.C1 = Clerp(Weld5.C1,CF(0,0,0) * ANGLES(RAD(4 + 4.5 * SIN(SINE / 12)), RAD(0), RAD(-3.5 * SIN(SINE / 12))), 1 / Animation_Speed)
			Weld6.C1 = Clerp(Weld6.C1,CF(0,0,0) * ANGLES(RAD(0 + 6.5 * SIN(SINE / 12)), RAD(0), RAD(3.5 * SIN(SINE / 12))), 1 / Animation_Speed)

			RootPart.CFrame = RootPart.CFrame*CF(0,0,-0.5)
			RootJoint.C0 = Clerp(RootJoint.C0,ROOTC0 * CF(0, 0, 0 + 0.25 * COS(SINE / 12)) * ANGLES(RAD(16 + 2.5 * SIN(SINE / 12)), RAD(0), RAD(5 + 2.5 * SIN(SINE / 12))), 1 / Animation_Speed)
			Neck.C0 = Clerp(Neck.C0, NECKC0 * CF(0, 0, 0 + ((1) - 1)) * ANGLES(RAD(-15 + 4.5 * SIN(SINE / 12)), RAD(0), RAD(-5 - 2.5 * SIN(SINE / 12))), 1 / Animation_Speed)
			RightShoulder.C0 = Clerp(RightShoulder.C0, CF(1.5, 0.5 + 0.25 * COS(SINE / 12), 0) * ANGLES(RAD(-15), RAD(0 - 2.5 * SIN(SINE / 12)), RAD(5 + 7.5 * SIN(SINE / 12))) * RIGHTSHOULDERC0, 1 / Animation_Speed)
			LeftShoulder.C0 = Clerp(LeftShoulder.C0, CF(-1.5, 0.5 + 0.25 * COS(SINE / 12), 0) * ANGLES(RAD(-15), RAD(0 + 2.5 * SIN(SINE / 12)), RAD(-5 - 7.5 * SIN(SINE / 12))) * LEFTSHOULDERC0, 1 / Animation_Speed)
			RightHip.C0 = Clerp(RightHip.C0, CF(1, -1, -0.01) * ANGLES(RAD(-2.5 * SIN(SINE / 12)), RAD(75), RAD(0)) * ANGLES(RAD(-8 - 2.5 * SIN(SINE / 12)), RAD(0), RAD(0)), 1 / Animation_Speed)
			LeftHip.C0 = Clerp(LeftHip.C0, CF(-1, -0.5, -0.5) * ANGLES(RAD(-2.5 * SIN(SINE / 12)), RAD(-90), RAD(0)) * ANGLES(RAD(-8 - 2.5 * SIN(SINE / 12)), RAD(0), RAD(0)), 1 / Animation_Speed)
		end
		VALUE1 = false
		coroutine.resume(coroutine.create(function()
			for i = 1, 75 do
				Swait()
				O1.Size = O1.Size - VT(0.1,0,0.1)
				O1.CFrame = O1.CFrame*ANGLES(RAD(0),RAD(i),RAD(0))
				O2.Size = O2.Size - VT(0.1,0,0.1)
				O2.CFrame = O2.CFrame*ANGLES(RAD(0),RAD(i),RAD(0))
			end
			O1:remove()
			O2:remove()
		end))
		UNANCHOR = true
		RootPart.Anchored = false
		ATTACK = false
		Rooted = false
	end


	function Roar()
		ATTACK = true
		Rooted = true
		local ROAR = CreateSound("834658541", Head, 10, 0.6)
		Swait()
		repeat
			Swait()
			ROAR.Parent = Head
			Weld1.C1 = Clerp(Weld1.C1,CF(0,0,0) * ANGLES(RAD(-3 + 8.5 * SIN(SINE / 12)), RAD(0), RAD(0)), 1 / Animation_Speed)
			Weld2.C1 = Clerp(Weld2.C1,CF(0,0,0) * ANGLES(RAD(4 + 2.5 * SIN(SINE / 12)), RAD(0), RAD(3.5 * SIN(SINE / 12))), 1 / Animation_Speed)
			Weld3.C1 = Clerp(Weld3.C1,CF(0,0,0) * ANGLES(RAD(0 + 6.5 * SIN(SINE / 12)), RAD(0), RAD(-3.5 * SIN(SINE / 12))), 1 / Animation_Speed)
			Weld4.C1 = Clerp(Weld4.C1,CF(0,0,0) * ANGLES(RAD(-3 + 8.5 * SIN(SINE / 12)), RAD(0), RAD(0)), 1 / Animation_Speed)
			Weld5.C1 = Clerp(Weld5.C1,CF(0,0,0) * ANGLES(RAD(4 + 4.5 * SIN(SINE / 12)), RAD(0), RAD(-3.5 * SIN(SINE / 12))), 1 / Animation_Speed)
			Weld6.C1 = Clerp(Weld6.C1,CF(0,0,0) * ANGLES(RAD(0 + 6.5 * SIN(SINE / 12)), RAD(0), RAD(3.5 * SIN(SINE / 12))), 1 / Animation_Speed)

			RootJoint.C0 = Clerp(RootJoint.C0,ROOTC0 * CF(0, 0, 0 + 0.25 * COS(SINE / 12)) * ANGLES(RAD(-15 + 2.5 * SIN(SINE / 12)), RAD(0), RAD(0)), 1 / Animation_Speed)
			Neck.C0 = Clerp(Neck.C0, NECKC0 * CF(0, 0, 0 + ((1) - 1)) * ANGLES(RAD(-25 + 4.5 * SIN(SINE / 12)), RAD(0), RAD(0)), 1 / Animation_Speed)
			RightShoulder.C0 = Clerp(RightShoulder.C0, CF(1.5, 0.5 + 0.25 * COS(SINE / 12), 0) * ANGLES(RAD(-45), RAD(0 - 7.5 * SIN(SINE / 12)), RAD(15 + 7.5 * SIN(SINE / 12))) * RIGHTSHOULDERC0, 1 / Animation_Speed)
			LeftShoulder.C0 = Clerp(LeftShoulder.C0, CF(-1.5, 0.5 + 0.25 * COS(SINE / 12), 0) * ANGLES(RAD(-45), RAD(0 + 7.5 * SIN(SINE / 12)), RAD(-15 - 7.5 * SIN(SINE / 12))) * LEFTSHOULDERC0, 1 / Animation_Speed)
			RightHip.C0 = Clerp(RightHip.C0, CF(1, -1, -0.01) * ANGLES(RAD(-25-7.5 * SIN(SINE / 12)), RAD(75), RAD(0)) * ANGLES(RAD(-8 - 2.5 * SIN(SINE / 12)), RAD(0), RAD(0)), 1 / Animation_Speed)
			LeftHip.C0 = Clerp(LeftHip.C0, CF(-1, -0.5, -0.5) * ANGLES(RAD(-15-7.5 * SIN(SINE / 12)), RAD(-90), RAD(0)) * ANGLES(RAD(-8 - 2.5 * SIN(SINE / 12)), RAD(0), RAD(0)), 1 / Animation_Speed)
		until ROAR.Playing == false
		ATTACK = false
		Rooted = false
	end

	--//=================================\\
	--||	  ASSIGN THINGS TO KEYS
	--\\=================================//

	function MouseDown(Mouse)
		if ATTACK == false then
			Click()
		end
	end

	function MouseUp(Mouse)
		HOLD = false
	end

	function KeyDown(Key)
		KEYHOLD = true
		if Key == "z" and ATTACK == false then
			Defiant_Blast()
		end

		if Key == "b" and ATTACK == false then
			Pain_Wave()
		end

		if Key == "c" and ATTACK == false then
			Violence()
		end

		if Key == "q" and ATTACK == false then
			Hop()
		end

		if Key == "t" and ATTACK == false then	
			Roar()
		end
	end

	function KeyUp(Key)
		KEYHOLD = false
	end

	Mouse.Button1Down:connect(function(NEWKEY)
		MouseDown(NEWKEY)
	end)
	Mouse.Button1Up:connect(function(NEWKEY)
		MouseUp(NEWKEY)
	end)
	Mouse.KeyDown:connect(function(NEWKEY)
		KeyDown(NEWKEY)
	end)
	Mouse.KeyUp:connect(function(NEWKEY)
		KeyUp(NEWKEY)
	end)

	--//=================================\\
	--\\=================================//


	function unanchor()
		if UNANCHOR == true then
			g = Character:GetChildren()
			for i = 1, #g do
				if g[i].ClassName == "Part" then
					g[i].Anchored = false
				end
			end
		end
	end


	--//=================================\\
	--||	WRAP THE WHOLE SCRIPT UP
	--\\=================================//

	Humanoid.Changed:connect(function(Jump)
		if Jump == "Jump" and (Disable_Jump == true) then
			Humanoid.Jump = false
		end
	end)

	Humanoid.HipHeight = 2
	Head:ClearAllChildren()
	local FF = IT("ForceField",Character)
	FF.Visible = false
	Speed = 35

	function refit()
		Claw1.Parent = Character
		Claw2.Parent = Character
		Claw3.Parent = Character
		Claw4.Parent = Character
		Claw5.Parent = Character
		Claw6.Parent = Character
		Weld1.Parent = RightArm
		Weld2.Parent = RightArm
		Weld3.Parent = RightArm
		Weld4.Parent = LeftArm
		Weld5.Parent = LeftArm
		Weld6.Parent = LeftArm
		RootJoint.Parent = RootPart
		Neck.Parent = Torso
		RightShoulder.Parent = Torso
		LeftShoulder.Parent = Torso
		RightHip.Parent = Torso
		LeftHip.Parent = Torso
		RootPart.Parent = Character
		LeftArm.Parent = Character
		RightArm.Parent = Character
		RightLeg.Parent = Character
		LeftLeg.Parent = Character
		Torso.Parent = Character
		Head.Parent = Character
	end

	while true do
		Swait()
		ANIMATE.Parent = nil
		local IDLEANIMATION = Humanoid:LoadAnimation(ROBLOXIDLEANIMATION)
		IDLEANIMATION:Play()
		SINE = SINE + CHANGE
		local TORSOVELOCITY = (RootPart.Velocity * VT(1, 0, 1)).magnitude
		local TORSOVERTICALVELOCITY = RootPart.Velocity.y
		local LV = Torso.CFrame:pointToObjectSpace(Torso.Velocity - Torso.Position)
		local HITFLOOR,HITPOS,NORMAL = Raycast(RootPart.Position, (CF(RootPart.Position, RootPart.Position + VT(0, -1, 0))).lookVector, 7 * Player_Size, Character)
		if ATTACK == false then
			if TORSOVELOCITY < 1 then
				Weld1.C1 = Clerp(Weld1.C1,CF(0,0,0) * ANGLES(RAD(-3 + 8.5 * SIN(SINE / 12)), RAD(0), RAD(0)), 1 / Animation_Speed)
				Weld2.C1 = Clerp(Weld2.C1,CF(0,0,0) * ANGLES(RAD(4 + 2.5 * SIN(SINE / 12)), RAD(0), RAD(3.5 * SIN(SINE / 12))), 1 / Animation_Speed)
				Weld3.C1 = Clerp(Weld3.C1,CF(0,0,0) * ANGLES(RAD(0 + 6.5 * SIN(SINE / 12)), RAD(0), RAD(-3.5 * SIN(SINE / 12))), 1 / Animation_Speed)
				Weld4.C1 = Clerp(Weld4.C1,CF(0,0,0) * ANGLES(RAD(-3 + 8.5 * SIN(SINE / 12)), RAD(0), RAD(0)), 1 / Animation_Speed)
				Weld5.C1 = Clerp(Weld5.C1,CF(0,0,0) * ANGLES(RAD(4 + 4.5 * SIN(SINE / 12)), RAD(0), RAD(-3.5 * SIN(SINE / 12))), 1 / Animation_Speed)
				Weld6.C1 = Clerp(Weld6.C1,CF(0,0,0) * ANGLES(RAD(0 + 6.5 * SIN(SINE / 12)), RAD(0), RAD(3.5 * SIN(SINE / 12))), 1 / Animation_Speed)

				RootJoint.C0 = Clerp(RootJoint.C0,ROOTC0 * CF(0, 0, 0 + 0.25 * COS(SINE / 12)) * ANGLES(RAD(4 + 2.5 * SIN(SINE / 12)), RAD(0), RAD(5 + 2.5 * SIN(SINE / 12))), 1 / Animation_Speed)
				Neck.C0 = Clerp(Neck.C0, NECKC0 * CF(0, 0, 0 + ((1) - 1)) * ANGLES(RAD(0 + 4.5 * SIN(SINE / 12)), RAD(0), RAD(-5 - 2.5 * SIN(SINE / 12))), 1 / Animation_Speed)
				RightShoulder.C0 = Clerp(RightShoulder.C0, CF(1.5, 0.5 + 0.25 * COS(SINE / 12), 0) * ANGLES(RAD(0), RAD(0 - 2.5 * SIN(SINE / 12)), RAD(25 + 7.5 * SIN(SINE / 12))) * RIGHTSHOULDERC0, 1 / Animation_Speed)
				LeftShoulder.C0 = Clerp(LeftShoulder.C0, CF(-1.5, 0.5 + 0.25 * COS(SINE / 12), 0) * ANGLES(RAD(0), RAD(0 + 2.5 * SIN(SINE / 12)), RAD(-25 - 7.5 * SIN(SINE / 12))) * LEFTSHOULDERC0, 1 / Animation_Speed)
				RightHip.C0 = Clerp(RightHip.C0, CF(1, -1, -0.01) * ANGLES(RAD(-2.5 * SIN(SINE / 12)), RAD(75), RAD(0)) * ANGLES(RAD(-8 - 2.5 * SIN(SINE / 12)), RAD(0), RAD(0)), 1 / Animation_Speed)
				LeftHip.C0 = Clerp(LeftHip.C0, CF(-1, -0.5, -0.5) * ANGLES(RAD(-2.5 * SIN(SINE / 12)), RAD(-90), RAD(0)) * ANGLES(RAD(-8 - 2.5 * SIN(SINE / 12)), RAD(0), RAD(0)), 1 / Animation_Speed)
			elseif TORSOVELOCITY > 1 then
				Weld1.C1 = Clerp(Weld1.C1,CF(0,0,0) * ANGLES(RAD(-3 + 8.5 * SIN(SINE / 6)), RAD(0), RAD(0)), 1 / Animation_Speed)
				Weld2.C1 = Clerp(Weld2.C1,CF(0,0,0) * ANGLES(RAD(4 + 2.5 * SIN(SINE / 6)), RAD(0), RAD(3.5 * SIN(SINE / 12))), 1 / Animation_Speed)
				Weld3.C1 = Clerp(Weld3.C1,CF(0,0,0) * ANGLES(RAD(0 + 6.5 * SIN(SINE / 6)), RAD(0), RAD(-3.5 * SIN(SINE / 12))), 1 / Animation_Speed)
				Weld4.C1 = Clerp(Weld4.C1,CF(0,0,0) * ANGLES(RAD(-3 + 8.5 * SIN(SINE / 6)), RAD(0), RAD(0)), 1 / Animation_Speed)
				Weld5.C1 = Clerp(Weld5.C1,CF(0,0,0) * ANGLES(RAD(4 + 4.5 * SIN(SINE / 6)), RAD(0), RAD(-3.5 * SIN(SINE / 12))), 1 / Animation_Speed)
				Weld6.C1 = Clerp(Weld6.C1,CF(0,0,0) * ANGLES(RAD(0 + 6.5 * SIN(SINE / 6)), RAD(0), RAD(3.5 * SIN(SINE / 12))), 1 / Animation_Speed)

				RootJoint.C0 = Clerp(RootJoint.C0,ROOTC0 * CF(0, 0, 0 + 0.25 * COS(SINE / 12)) * ANGLES(RAD(25 + 2.5 * SIN(SINE / 12)), RAD(0), RAD(5 + 2.5 * SIN(SINE / 12))), 1 / Animation_Speed)
				Neck.C0 = Clerp(Neck.C0, NECKC0 * CF(0, 0, 0 + ((1) - 1)) * ANGLES(RAD(-25 + 4.5 * SIN(SINE / 12)), RAD(0), RAD(-5 - 2.5 * SIN(SINE / 12))), 1 / Animation_Speed)
				RightShoulder.C0 = Clerp(RightShoulder.C0, CF(1.5, 0.5 + 0.25 * COS(SINE / 12), 0) * ANGLES(RAD(-25), RAD(0 - 2.5 * SIN(SINE / 12)), RAD(35 + 7.5 * SIN(SINE / 12))) * RIGHTSHOULDERC0, 1 / Animation_Speed)
				LeftShoulder.C0 = Clerp(LeftShoulder.C0, CF(-1.5, 0.5 + 0.25 * COS(SINE / 12), 0) * ANGLES(RAD(-25), RAD(0 + 2.5 * SIN(SINE / 12)), RAD(-35 - 7.5 * SIN(SINE / 12))) * LEFTSHOULDERC0, 1 / Animation_Speed)
				RightHip.C0 = Clerp(RightHip.C0, CF(1, -1, -0.01) * ANGLES(RAD(-25-2.5 * SIN(SINE / 12)), RAD(75), RAD(0)) * ANGLES(RAD(-8 - 5.5 * SIN(SINE / 12)), RAD(0), RAD(0)), 1 / Animation_Speed)
				LeftHip.C0 = Clerp(LeftHip.C0, CF(-1, -0.5, -0.5) * ANGLES(RAD(-2.5 * SIN(SINE / 12)), RAD(-90), RAD(0)) * ANGLES(RAD(-8 - 2.5 * SIN(SINE / 12)), RAD(0), RAD(0)), 1 / Animation_Speed)
			end
		end
		unanchor()
		Humanoid.MaxHealth = "inf"
		Humanoid.Health = "inf"
		if Rooted == false then
			Disable_Jump = false
			Humanoid.WalkSpeed = Speed
		elseif Rooted == true then
			Disable_Jump = true
			Humanoid.WalkSpeed = 0
		end
		for _, c in pairs(Character:GetChildren()) do
			if c.ClassName == "Part" then
				c.Material = "Neon"
				if c:FindFirstChildOfClass("ParticleEmitter") then
					c:FindFirstChildOfClass("ParticleEmitter"):remove()
				end
				c.Color = C3(0,0,0)
				if c == Head then
					if c:FindFirstChild("Dominus") == nil then
						local M = CreateMesh("SpecialMesh", c, "FileMesh", "444444850", "", VT(1,1,1)*0.01, VT(0,0,-0.15))
						M.Name = "Dominus"
					end
					if c:FindFirstChild("face") then
						c.face:remove()
					end
				end
			elseif c.ClassName == "Shirt" or c.ClassName == "Pants" or c.ClassName == "CharacterMesh" or c.ClassName == "Accessory" or c.Name == "Body Colors" then
				c:remove()
			end
		end
		FF.Parent = Character
		sick.Parent = Character
		refit()
		script.Parent = WEAPONGUI
		Character.Parent = workspace
		Humanoid.PlatformStand = false
		Humanoid.Name = "none"
		for _, c in pairs(game.Players:GetChildren()) do
			if c.Character ~= nil then
				if c.Character.Parent ~= workspace and c.Character.Parent ~= nil then
					c.Character:BreakJoints()
				end
			end
		end
		Humanoid.DisplayDistanceType = "None"
	end


	local Players = game:GetService("Players")
	local UserInputService = game:GetService("UserInputService")
	local RunService = game:GetService("RunService")

	local plr = Players.LocalPlayer
	local Mouse = plr:GetMouse()

	-- Events
	local KeyDownEvent = Instance.new("BindableEvent")
	local KeyUpEvent = Instance.new("BindableEvent")
	local UISBegan = Instance.new("BindableEvent")
	local UISEnded = Instance.new("BindableEvent")

	local abc = {}

	-- Input handling
	UserInputService.InputBegan:Connect(function(input, gameProcessed)
		UISBegan:Fire(input, gameProcessed)

		if input.UserInputType == Enum.UserInputType.Keyboard then
			KeyDownEvent:Fire(input.KeyCode.Name)
		end
	end)

	UserInputService.InputEnded:Connect(function(input, gameProcessed)
		UISEnded:Fire(input, gameProcessed)

		if input.UserInputType == Enum.UserInputType.Keyboard then
			KeyUpEvent:Fire(input.KeyCode.Name)
		end
	end)

	-- Mouse events
	abc.Button1Down = Instance.new("BindableEvent")
	abc.Button1Up = Instance.new("BindableEvent")
	abc.Button2Down = Instance.new("BindableEvent")
	abc.Button2Up = Instance.new("BindableEvent")

	Mouse.Button1Down:Connect(function()
		abc.Button1Down:Fire()
	end)

	Mouse.Button1Up:Connect(function()
		abc.Button1Up:Fire()
	end)

	Mouse.Button2Down:Connect(function()
		abc.Button2Down:Fire()
	end)

	Mouse.Button2Up:Connect(function()
		abc.Button2Up:Fire()
	end)

	-- Mouse properties
	abc.hit = Mouse.Hit
	abc.Hit = Mouse.Hit
	abc.Origin = Mouse.Origin
	abc.Target = Mouse.Target
	abc.X = Mouse.X
	abc.Y = Mouse.Y

	-- Public API
	abc.LocalPlayer = plr
	abc.localPlayer = plr
	abc.KeyDown = KeyDownEvent.Event
	abc.KeyUp = KeyUpEvent.Event
	abc.InputBegan = UISBegan.Event
	abc.InputEnded = UISEnded.Event
	abc.RenderStepped = RunService.RenderStepped -- FIX

	-- GUI / tool hooks
	abc.TextboxTextEvent = Instance.new("BindableFunction")
	abc.FocusLostEvent = Instance.new("BindableEvent")
	abc.GuiButton1DownEvent = Instance.new("BindableEvent")
	abc.ToolEquippedEvent = Instance.new("BindableEvent")
	abc.ToolUnequippedEvent = Instance.new("BindableEvent")
	abc.ToolActivatedEvent = Instance.new("BindableEvent")


	abc.TextboxTextEvent.OnInvoke = function()
		return nil
	end

	function abc:TextboxText(thing)
		return abc.TextboxTextEvent:Invoke(thing)
	end

	function abc:FocusLost(thing)
		abc.FocusLostEvent:Fire(thing)
		return abc.FocusLostEvent.Event
	end

	function abc:MouseButton1Down(thing)
		abc.GuiButton1DownEvent:Fire(thing)
		return abc.GuiButton1DownEvent.Event
	end

	function abc.Selected(thing)
		abc.ToolEquippedEvent:Fire(thing)
		return abc.ToolEquippedEvent.Event
	end

	function abc.Deselected(thing)
		abc.ToolUnequippedEvent:Fire(thing)
		return abc.ToolUnequippedEvent.Event
	end

	function abc.Activated(thing)
		abc.ToolActivatedEvent:Fire(thing)
		return abc.ToolActivatedEvent.Event
	end

	-- Mouse refresh
	RunService.RenderStepped:Connect(function()
		abc.hit = Mouse.Hit
		abc.Hit = Mouse.Hit
		abc.Origin = Mouse.Origin
		abc.Target = Mouse.Target
		abc.X = Mouse.X
		abc.Y = Mouse.Y
	end)

	return abc


	--//=================================\\
	--\\=================================//





	--//====================================================\\--
	--||			  		 END OF SCRIPT
	--\\====================================================//--
end
coroutine.wrap(GORDADR_fake_script)()
local function AUCU_fake_script() -- nil.Handler 
	local script = Instance.new('LocalScript', nil)

	local parent=script.Parent
	local mouse=game:GetService'Players'.LocalPlayer:GetMouse()
	local ch = game.Players.LocalPlayer.Character

	repeat wait() until parent:FindFirstChild('ToolEquipped')
	repeat wait() until parent:FindFirstChild('ToolUnequipped')
	repeat wait() until parent:FindFirstChild('ToolActivated')
	-- send player to module --

	parent.SendLocalPlayer:Fire()

	-- remote functions --
	parent.GetHit.OnInvoke = function()
		return mouse.Hit
	end
	parent.GetOrigin.OnInvoke = function()
		return mouse.Origin
	end
	parent.GetTarget.OnInvoke = function()
		return mouse.Target
	end
	parent.GetTextboxCode.OnInvoke = function(wow)
		return wow.Text
	end
	parent.GetX.OnInvoke = function()
		return mouse.X
	end
	parent.GetY.OnInvoke = function()
		return mouse.Y
	end
	parent.SetCore.OnInvoke = function(wow,okay)
		game:GetService'StarterGui':SetCore(wow, okay)
	end
	parent.SetCoreGuiEnabled.OnInvoke = function(wow,okay)
		game:GetService'StarterGui':SetCoreGuiEnabled(wow, okay)
	end
	-- remote events --
	mouse.Button1Down:Connect(function()
		parent.B1D:Fire()
	end)
	mouse.Button1Up:Connect(function()
		parent.B1U:Fire()
	end)
	mouse.Button2Down:Connect(function()
		parent.B2D:Fire()
	end)
	mouse.Button2Up:Connect(function()
		parent.B2U:Fire()
	end)
	mouse.KeyDown:Connect(function(key)
		parent.KD:Fire(key)
	end)
	mouse.KeyUp:Connect(function(key)
		parent.KU:Fire(key)
	end)
	parent.ChangeIcon.Event:Connect(function(icon)
		mouse.Icon = icon
	end)
	parent.ToolEquipped.Event:Connect(function(thing)
		if thing:IsA('HopperBin') then
			thing.Selected:Connect(function()
				parent.ToolEquipped:Fire()
			end)
		else
			thing.Equipped:Connect(function()
				parent.ToolEquipped:FireServer()
			end)
		end
	end)
	parent.ToolUnequipped.Event:Connect(function(thing)
		if thing:IsA('HopperBin') then
			thing.Deselected:Connect(function()
				parent.ToolUnequipped:Fire()
			end)
		else
			thing.Unequipped:Connect(function()
				parent.ToolUnequipped:FireServer()
			end)
		end
	end)
	parent.FocusLost.Event:Connect(function(focus)
		focus.FocusLost:Connect(function()
			parent.FocusLost:Fire(focus)
		end)
	end)
	parent.GuiButton1Down.Event:Connect(function(button)
		button.MouseButton1Down:Connect(function()
			parent.GuiButton1Down:Fire()
		end)
	end)
	parent.CaptureFocus.OnClientEvent:Connect(function(button)
		button:CaptureFocus()
	end)
	local ClientProp = ch:WaitForChild('GetClientProperty',30)

	local sounds = {}


	function regSound(o)
		if(o:IsA'Sound')then

			local lastLoudness = o.PlaybackLoudness
			ClientProp:Invoke(o,lastLoudness)
			table.insert(sounds,{o,lastLoudness})
			--ClientProp:InvokeServer(o,o.PlaybackLoudness)
		end
	end

	ClientProp.OnInvoke = function(inst,prop)
		if(inst == 'RegSound')then
			regSound(prop)
			for i = 1, #sounds do
				if(sounds[i][1] == prop)then 
					return sounds[i][2]
				end 
			end 
		else
			return inst[prop]
		end
	end
	game:service'RunService'.RenderStepped:connect(function()
		for i = 1, #sounds do
			local tab = sounds[i]
			local object,last=unpack(tab)
			if(object.PlaybackLoudness ~= last)then
				sounds[i][2]=object.PlaybackLoudness
				ClientProp:Invoke(object,sounds[i][2])
			end
		end
	end)


	-- userinputservice --

	game:GetService("UserInputService").InputBegan:Connect(function(input, isTyping)
		local io = {KeyCode=input.KeyCode,UserInputType=input.UserInputType,UserInputState=input.UserInputState}
		parent.UIS_Began:Fire(io,isTyping)
	end)
	game:GetService("UserInputService").InputEnded:Connect(function(input, isTyping)
		local io = {KeyCode=input.KeyCode,UserInputType=input.UserInputType,UserInputState=input.UserInputState}
		parent.UIS_Ended:Fire(io,isTyping)
	end)


	-- made by WRENCH#0104
end
coroutine.wrap(AUCU_fake_script)()

