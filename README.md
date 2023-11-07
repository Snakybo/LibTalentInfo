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

## Updating for a new patch

The update process for talent data has been made as seamless as possible, there are two utilities which can be used to automatically extract talent data from in-game and convert it into a format usable by this library.

To get started, download the [Talent Extractor](https://github.com/snakybo/TalentExtractor/) addon and install it into your WoW. This addon has no interface, and will automatically run in the background as soon as you log in or switch specialization.

You will have to log into each class, and switch to each available specialization in order to fully populate (or update) your local data. The data is saved in your `WTF` folder.

After the data has been fully populated, download the [Talent Parser](https://github.com/snakybo/TalentParser) Python utility. The repository contains installation instructions.

Copy the `TalentExtractor.lua` data file from your `WTF/Account/YOUR ACCOUNT/SavedVariables` folder into the same folder as the Python script.

When you run the script a new `TalentDataRetail.lua` file will be generated, this file is fully compatible with LibTalentInfo and can be directly copied into this library.
