# **Onix Scripting Documentation**
### **local mcVersion = game.version**
-- The version of minecraft, example: "1.16.40"


### **local clientVersion = client.version**
-- The version of the client, example: "2.34"

### **client.execute("setcolor 0 #2020FF")**
-- Runs a client command, do not incldue the prefix

This exemple should set the fog color to a cool blueish color (if environement changer is enabled)

### **client.notification("Scripting on top")**
Sends a notification to the player

**Looks like this:**

![](https://raw.githubusercontent.com/Quoty0/OnixClient_Scripts/master/Commands/notification_example.png)


# **Settings**
-- The first parameter is the visual name

-- The second parameter is the variable name with the default value

-- Do that outside of any functions

### **client.settings.addAir(15)**
-- Adds a space in the ui at that place (15 is the height)

someText = "hi this is me"
### **client.settings.addInfo("someText")**
-- First parametter is name of text variable

-- The text of that variable can change and it will update

wanaDie = false
### **client.settings.addBool("Do you want to die?", "wanaDie")**
-- Will add a toggle option with default value of false

dieCount = 3
### **client.settings.addInt("Do you want to die?", "dieCount", 0, 250)**
-- Adds a slider with integer numbers

-- The last two parameters for int is minimum and maximum

textSize = 0.8
### **client.settings.addFloat("Do you want to die?", "textSize", 0.2, 3.5)**
-- Adds a slider with .00 at the end

-- The last two parameters for int is minimum and maximum

keybind = 0x45
### **client.settings.addKeybind("Suicide Key", "keybind")**
-- Adds a key setting with default value of A

-- See [Windows Virtual KeyCodes](https://docs.microsoft.com/en-us/windows/win32/inputdev/virtual-key-codes)

### **color = {255,0,0} --you can also specify the default opacity {255,0,0,255}**
### **client.settings.addColor("Text Color", "color")**
-- To access the color after addColor you must do color.r


-- Its now a table with {r g b a} defined

You can add a bool after the 2nd parameter if you want opacity to be visible or no

```
function funnyThingLmao()
	print("+1 Vbuck")
end
client.settings.addFunction("Click the button for free vbuck", "funnyThingLmao", "Click here!")
```

--first thing is the text before the button
--second thing is the name of the function
--third is the text inside of the button
--will be called when the user clicks on it

### **client.settings.send()**
--if you change a setting in the script (not for info ones) to apply it to the client you need to send them

### **client.settings.reload()**
--if you want to refresh your version of the settings you can do it too

### **local clipboardData = getClipboard()**
--gives you the content of the clipboard

### **setClipboard("text")**
--sets the clipboard to the text

### **ImportedLib = importLib("Thing")**
--will import the things from the Scripting/Libs/Thing.lua file
--"Thing.lua" would work too
--lets you have helper functions in a file that other scripts can use
--will return false if it could not find the file
--the functions in the file will be usable in this file basically


### **local gamemode = player.gamemode()**
--get player gamemode

### **local x,y,z = player.position()**
--returns xyz player position

### **local yaw, pitch = player.rotation()**
--returns camera rotation

### **local name = player.name()**
--returns the player's name

### **local x,y,z = player.selectedPos()**
--returns the selected block's position (the one u could break if u click)

### **local isFacingEntity = player.facingEntity()**
--if the player is looking at an entity

### **local isFacingEntity = player.facingBlock()**
--if the player is looking at a block

### **local x,y,z = player.lookingPos()**
--where the player looks in the world


### **local dimensionId = dimension.id()**
--get the numeric id of the current dimension

### **local dimensionName = dimension.name()**
---get the name of the current dimension

### **local time = dimension.time()**
--gets the current time of day, value from 0 to 1

### **local isRaining = dimension.isRaining()**
--if its raining in the current dimension

### **local blockBrightness, skyBrightness = dimension.getBrightness(x, y, z)**
-- gives you the brightness at a location
-- block brightness is for things like torch and stuff
-- sky is how much the sky will give its brightness

### **dimension.sound("random.fuse", 420, 69, 86)**
--plays the minecraft sound at the coordinates --can only be minecraft sounds


### **local connectedServerIp = server.ipConnected()**
--the ip you are currently trading packets with

### **local ip = server.ip()**
--the ip used to join the server

### **local port = server.port()**
--the port used to join the server

### **local worldName = server.worldName()**
--the name of the world (top right in pause)


### **local width = gui.width()**
--game ui width

### **local height = gui.height()**
--game ui height

### **local guiscale = gui.scale()**
--minecraft guiscale

### **local isMouseGrabbed = gui.mouseGrabbed()**
--if the mouse is captured or free

### **gui.setGrab(true)**
--lock/unlock the mouse

### **local showed = gui.showscreen("HudEditor")**
--shows a client ui, will tell you if it did

### **gui.clickSound()**
--plays the minecraft ui click sound

### **gui.sound("mob.wither.death")**
--plays the minecraft sound --can only be minecraft sounds




# **Effects**
### **local effects = player.effects()**
--returns a table of effect table, see effect table below.
--here is how to go trough the entire list:  for a, effect in pairs(effects) do

# **Effect Table**
### **local seconds = effect.duration**
--the duration of the effect in seconds (remaining time)

### **local amplifier = effect.level**
--like regeneration 2 or smth like that

### **local effectId = effect.id**
--the id of the potion, (the one that gfx.effect takes)

### **local effectTimeText = effect.time**
--will give you the time this potion will last for,  exemple: 6:32

### **local effectName = effect.name**
--will give you the name that /effect takes ex: night_vision

### **local visualEffectName = effect.vname**
--gives you the cool looking effect text, ex: Night Vision II




--Attributes
### **local attributeList = player.attributes()**
--gets the list of attributes

### **local attributeCount = attributeList.size**
--amount of attributes

### **local healthAttrib = attributeList.name("minecraft:health")**
--this exemple will return you the health attribute

### **local hungerAttrib = attributeList.id(2)**
--this exemple will give you the hunger attribute

### **local attributeHeight = attributeList.at(8)**
--will return whatever the attribute 8 in the list is


--these 3 functions all return an attribute table
--if you ask an invalid attribute, you will be given nil
--the content of this table goes as follow

### **local attribute_name = attributeHeight.name**
--the name (that you can pass in list.name())

### **local attribute_id = attributeHeight.id**
--its id, (the one that you can pass in list.id())

### **local attribute_value = attributeHeight.value --or attributeHeight.current**
--the current value of the attribute

### **local attribute_default = attributeHeight.default**
--the default value of the attribute

### **local attribute_minimum = attributeHeight.min**
--the minimum value of the attribute

### **local attribute_maximum = attributeHeight.max**
--the maximum value of the attribute




# --blocks
### **local block = dimension.getBlock(x,y,z)**
--gets a block table at these coordinates

--the block table:
### **local blockName = block.name**
--name of the block (the one to use in /setblock)

### **local blockData = block.data**
--data of the block (exemple: wool color)

### **local blockId = block.id**
--the id of the block




--biome
### **local biome = dimension.getBiome(x,y,z)**
--gets the biome table at the coordinates specified

--the block table:
### **local biomeName = biome.name**
--name of the biome  (text)

### **local  biomeId = biome.id**
--id of the biome  (number)

### **local temperature = biome.temperature**
-- temperature of the biome  (number)

### **local snowAccumulation = biome.snow**
-- the snow accumulation of the biome (number)

### **local canRain = biome.canRain**
--boolean indicating if the current biome can get rain




--inventory
### **local inventory = player.inventory()**
--gives you an inventory table

### **local inventorySize = inventory.size**
--gives you the size of the inventory

### **local selectedSlot = inventory.selected**
--the item in your hand basically

### **local armor = inventory.armor()**
--gives you the armor items (item table) (armor.helmet, armor.chestplate, armor.leggings, armor.boots)
--**if there is no items it will be nil**

### **local offhandItem = inventory.offhand()**
--gives you an item table for the 2nd hand, nil if no item

### **local firstInvSlot = inventory.at(1)**
--gives you an item table for the slot, dont go below one or above size
--will return nil if there is no item


--item
--make sure its not nil before accessing stuff in the table

### **local quantity = firstInvSlot.count --firstInvSlot.amount will work aswell**
--the amount of item in this stack

### **local itemLocation = firstInvSlot.location**
--you can use this to specify an item for stuff

### **local ItemId = firstInvSlot.id**
--the id of the item

### **local itemName = firstInvSlot.name**
--the name of the item (same as /give)

### **local maxStackCount = firstInvSlot.maxStack**
--like ender pearls are 16 and normal stuff is 64..

### **local maxDurability = firstInvSlot.maxData**
--items like sword have this to their max durability

### **local durability = firstInvSlot.data --or firstInvSlot.durability**
--will give you the Damage of the item or the block's data




--font
local font = gui.font()

--the font is a table with the following members

### **local isMcFont = font.isMinecrafttia**
--if its the mc font or the smooth one

### **local height = font.height**
--you can use that to make a rectangle around text with the font's height

### **local wrapHeight = font.wrap**
--what a line takes, so if you have a second line it will be at location + wrap

### **local textWidth = font.width("Hello World!")**
--will give you the width of the text you give.




--gfx
--DO NOT USE OUTSIDE OF RENDER()!!!!!
--otherwise the game will crash..

### **gfx.color(255,255,255, 255)**
--this will set the current drawing color to white, you can use rgb codes
--note, opacity is optional, no value will be 255.

### **gfx.rect(positionX, positionY, sizeX, sizeY)**
--will fill a rectangle on the screen

### **gfx.drawRect(positionX, positionY, sizeX, sizeY, width)**
--will draw a rectangle (just the outline) with the specified width

### **gfx.roundrect(positionX, positionY, sizeX, sizeY, radius, iterations)**
--same as rect but with rounded corners!
--radius is for the 4 corners and the number of iterations 
--(2 would be blocky and 10 would be smooth, play with it and see)
--its kinda like quality, dont put too much as it would be bad for performance

### **gfx.circle(positionX, positionY, height, iterations)**
--height is radius*2, basically if you had a square
--of 50 by 50 it will put a circle in the very center
--iterations again is kinda like the quality, dont put too little or too much!
--see how it look and adapt to put as little as you can for the desired result

### **gfx.triangle(point1X, point1Y, point2X, point2Y, point3X, point3Y)**
--fills the rectangle between those points

### **gfx.text(positionX, positionY, "Hello World", scale)**
--draws text, scale of 1 is normal, if you don't put a scale
--it will be 1, but its availible if you want to render bigger or smaller text

### **gfx.item(positionX, positionY, itemLocation, scale)**
--draws an item at the location
--scale is optional will be 1 if not specified
--do not guess item location as a wrong value would most likely crash the game!
--you get the location from the ItemTable.location

### **gfx.image(positionX, positionY, sizeX, sizeY, filePath)**
--will draw the image, you start from OnixClient/Scripts/Data

### **gfx.texture(positionX, positionY, sizeX, sizeY, "textures/items/bread", opacity)**
--will draw the texture, you start from the root of a texture pack, opacity is optional but goes from 0.0 to 1.0

### **gfx.effect(positionX, positionY, sizeX, sizeY, potionId, opacity)**
--will draw the potion icon for the id, opacity is optional but goes from 0.0 to 1.0
