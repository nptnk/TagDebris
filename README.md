# TagDebris
the most useless thing i've ever made
https://devforum.roblox.com/t/tagdebris-create-tags-with-duration-or-a-value/1811765

Documentation since there isn't much:

```lua
local TagDebris = require(game.ReplicatedStorage.TagDebris)

--[[ Debris Tags]]--
TagDebris:AddTag(Instance,Name,Duration) -- Will add a CollectionService tag for the duration specified, then it will be removed.
TagDebris:GetDurationLeft(Instance,TagName) -- Will return the duration of tag
TagDebris:DestroyTag(Instance,TagName) -- Will destroy the tag early
TagDebris:UpdateDuration(Instance,TagName,Duration) -- Will update the duration of the tags lifetime, and return success

--[[ Value Tags ]]--
TagDebris:AddTagWithValue(Instance,TagName,Value,ConvertToBoolOrNumber) -- Will add a tag with a value, you can get values from this tag now.
TagDebris:GetTagWithValue(Instance,TagName) -- Will return the specified value that you set.
TagDebris:RemoveTagWithValue(Instance,TagName)
--[[
Use GetTagWithValue almost as CollectionService:HasTag()

if CollectionService:HasTag() then
----------------------------------
if GetTagWithValue() then
--]]
```

```lua
-- example
local TagDebris = require(game.ReplicatedStorage.TagDebris)
TagDebris:AddTag(workspace.BasePart,"Deadly",3) -- Will add a CollectionService tag for the duration specified, then it will be removed, returns nil.
TagDebris:AddTagWithValue(workspace.BasePart,"Age","36",true) -- Will add a tag with a value, you can get values from this tag now.
local duration = TagDebris:UpdateDuration(workspace.BasePart,"Deadly",5) -- > 5
local value = TagDebris:GetTagWithValue(workspace.BasePart,"Age") -- Will return the specified value that you set, returns the value [36].
if value == 36 then -- returned tonumber()
    print("Value is 36!!!")
    local success = TagDebris:RemoveTagWithValue(workspace.BasePart,"Age")
end

local startTick = tick()
game:GetService("RunService").Heartbeat:Connect(function()
    if game:GetService("CollectionService"):HasTag(workspace.BasePart,"Deadly") then
        print(string.format("Part is deadly!!! and its got %ss left!!!!",))
    else
        print(string.format("awww its been %s seconds... no deadly",duration))
    end
end)
```
