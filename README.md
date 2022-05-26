# TagDebris
the most useless thing i've ever made
https://devforum.roblox.com/t/tagdebris-create-tags-with-duration-or-a-value/1811765

Documentation since there isn't much:

```lua
local TagDebris = require(game.ReplicatedStorage.TagDebris)
TagDebris:AddTag(Instance,Name,Duration) -- Will add a CollectionService tag for the duration specified, then it will be removed.
TagDebris:AddTagWithValue(Instance,TagName,Value,ConvertToBoolOrNumber) -- Will add a tag with a value, you can get values from this tag now.
TagDebris:GetTagWithValue(Instance,TagName) -- Will return the specified value that you set.

--[[
Use GetTagWithValue almost as CollectionService:HasTag()

example:

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
local value = TagDebris:GetTagWithValue(workspace.BasePart,"Age") -- returns 36, Will return the specified value that you set.
if value == 36 then -- returned tonumber()
    print("Value is 36!!!")
end

game:GetService("RunService").Heartbeat:Connect(function()
    if game:GetService("CollectionService"):HasTag(workspace.BasePart,"Deadly") then
        print("Part is deadly!!!")
    else
        print("awww its been 3 seconds... no deadly")
    end
end)
```
