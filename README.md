# Police K9 Scripts originally forked from hashisx https://github.com/hashisx/hashx_k9

# Use
Purchase a dog from the location specified in the Config, use Z to follow or attack (Must be pointing a weapon to attack).

Press K to show K9 Commands (Both of these are now keymaps so its a on user basis)

# Searching

 You must be facing your target (vehicle or player) when selecting the Search Action, except for Search Area.
 Sometimes the Search Person will pick up the dog. Best to have the dog behind you.

# K9 Ped
The k9 ped I use personally from this script is from here https://forum.cfx.re/t/how-to-german-shepherd-malinois-k9-dog-1-0-1/1065040

# You must add this to QB Inventory Server main.lua. 
```
    AddEventHandler("inventory:server:SearchLocalVehicleInventory", function(plate, list, cb)
    local TRUNK = Trunks[plate]
    local GLOVEBOX = Gloveboxes[plate]
    local RESULT = false

    if TRUNK ~= nil then
        for k, v in pairs(TRUNK.items) do
            local ITEM = TRUNK.items[k].name
            if HasItem(list, ITEM) then
                RESULT = true
            end
        end
    else
        TRUNK = GetOwnedVehicleItems(plate)

        for k, v in pairs(TRUNK) do

            local ITEM = TRUNK[k].name
            if HasItem(list, ITEM) then
                RESULT = true
            end
        end

    end

    if GLOVEBOX ~= nil then
        for k, v in pairs(GLOVEBOX.items) do

            local ITEM = GLOVEBOX.items[k].name
            if HasItem(list, ITEM) then
                RESULT = true
            end
        end
    else
        GLOVEBOX = GetOwnedVehicleGloveboxItems(plate)

        for k, v in pairs(GLOVEBOX) do
            local ITEM = GLOVEBOX[k].name
            if HasItem(list, ITEM) then
                RESULT = true
            end
        end
    end
    cb(RESULT)
    end)
   

    function HasItem(list, item)

        for i = 1, #list do

            if item == list[i] then
                return true
            end
        end

        return false
    end

```
