# LibTalentInfo-1.0

A library that can retrieve PvP talent info for any specialization.

## Examples

### Get PvP talent info for a spec

```lua
local LibTalentInfo = LibStub("LibTalentInfo-1.0")

local specs = LibTalentInfo:GetClassSpecIDs("WARRIOR")

for i = 1, #specs do
	local specID = specs[i]
	local numTalents = LibTalentInfo:GetNumPvPTalentsForSpec(specID, 1)

	for j = 1, numTalents do
		local _, name = LibTalentInfo:GetPvPTalentInfo(specID, 1, j)

		print(specID .. ": " .. name)
	end
end
```
