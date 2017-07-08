# RaspberryJuice

A Bukkit plugin which implements the Minecraft Pi Socket API.

Hardcoded Settings:
- Weather is off
- Hunger is off
- Permanent Night Vision

## Commands

### Commands supported

<details>
  <summary>
mc.setBlock(x, y, z, block_id, [block_data])
  </summary>

> Set the block at coordinates X/Y/Z to block_id

```python

from mcpi import minecraft

#Connect to minecraft server 127.0.0.1 as player 'steve'
mc = minecraft.Minecraft.create(address="127.0.0.1", name="steve")

#Get current player's position
pos = mc.player.getPos()

#This is the minecraft block ID of the glass block.
#To see what other block IDs are available, go here in your browser: http://minecraft-ids.grahamedgecombe.com/
glass_block_id = 20

#Set the block underneath the player to be glass
mc.setBlock(pos.x, pos.y-1, pos.z, glass_block_id)

#Set the block to the side of player to be wood of a specific subtype
wood_block_id = 5
wood_data = 1 #subtype
mc.setBlock(pos.x+1, pos.y, pos.z, wood_block_id, wood_data)

```

</details>

<details>
  <summary>
mc.getBlock(x, y, z)
  </summary>

> Get the block at coordinates X/Y/Z, returning its block ID

```python

from mcpi import minecraft

# Connect to minecraft server 127.0.0.1 as player 'steve'
mc = minecraft.Minecraft.create(address="127.0.0.1", name="steve")

# Get current player's position
pos = mc.player.getPos()

# Get the block underneath the player
block_id_under_player = mc.getBlock(pos.x, pos.y-1, pos.z)
grass_block_id = 2

if block_id_under_player == grass_block_id:
    print "Player is standing on grass"

```

</details>



<details>
  <summary>
mc.getBlockWithData(x, y, z)
  </summary>

> Get the block at coordinates X/Y/Z, returning its block ID & data field (e.g. for wool color)

```python

from mcpi import minecraft

# Connect to minecraft server 127.0.0.1 as player 'steve'
mc = minecraft.Minecraft.create(address="127.0.0.1", name="steve")

# Get current player's position
pos = mc.player.getPos()

# Get the block underneath the player
block_under_player = mc.getBlockWithData(pos.x, pos.y-1, pos.z)
print "block id", block_under_player.id
print "block data", block_under_player.data

```

</details>


<details>
  <summary>
mc.setBlocks(x1, y1, z1, x2, y2, z2, block_id, [block_data])
  </summary>

> Set a cuboid of blocks between two opposite corners (x1/y1/z1 and x2/y2/z2)

```python

from mcpi import minecraft

#Connect to minecraft server 127.0.0.1 as player 'steve'
mc = minecraft.Minecraft.create(address="127.0.0.1", name="steve")

#Get current player's position
pos = mc.player.getPos()

#This is the minecraft block ID of the glass block.
#To see what other block IDs are available, go here in your browser: http://minecraft-ids.grahamedgecombe.com/
glass_block_id = 20

#Build a glass cube next to the player
mc.setBlocks(pos.x+3, pos.y, pos.z, pos.x+8, pos.y+5, pos.z+5, glass_block_id)

#Build a wood cube of a specific subtype next to the player, then make it hollow by building a smaller cube of air inside
wood_block_id = 5
wood_data = 1 #subtype
mc.setBlocks(pos.x-3, pos.y, pos.z, pos.x-8, pos.y+5, pos.z-5, wood_block_id, wood_data)

air_block_id = 0
mc.setBlocks(pos.x-2, pos.y+1, pos.z-1, pos.x-7, pos.y+4, pos.z-4, air_block_id)

```

</details>


<details>
  <summary>
mc.getBlocks(x1, y1, z1, x2, y2, z2)
  </summary>

> Get a cuboid of blocks between two opposite corners (x1/y1/z1 and x2/y2/z2)

```python

from mcpi import minecraft

#Connect to minecraft server 127.0.0.1 as player 'steve'
mc = minecraft.Minecraft.create(address="127.0.0.1", name="steve")

#Get current player's position
pos = mc.player.getPos()

blocks = mc.getBlocks(pos.x+3, pos.y, pos.z, pos.x+8, pos.y+5, pos.z+5)
for block_id in blocks:
    print block_id


```

</details>


<details>
  <summary>
mc.player.getPos()
  </summary>

> Get current player's position exactly (decimals)

```python

from mcpi import minecraft

#Connect to minecraft server 127.0.0.1 as player 'steve'
mc = minecraft.Minecraft.create(address="127.0.0.1", name="bob")

#Get current player's position
pos = mc.player.getPos()

# Returns Vec3(18.3814903971,6.0,25.6063951368)
# Can be accessed as pos.x, pos.y, and pos.z
print pos.x, pos.y, pos.z

```

</details>


<details>
  <summary>
mc.player.setPos()
  </summary>

> Set current player's position exactly (supports decimals)

```python

from mcpi import minecraft

#Connect to minecraft server 127.0.0.1 as player 'steve'
mc = minecraft.Minecraft.create(address="127.0.0.1", name="bob")

#Get current player's position
pos = mc.player.getPos()

#Set current player's position 100 blocks in the air
mc.player.setPos(pos.x, pos.y+100, pos.z)

```

</details>

<details>
  <summary>
mc.player.getPos()
  </summary>

> Get current player's position exactly (decimals)

```python

from mcpi import minecraft

#Connect to minecraft server 127.0.0.1 as player 'steve'
mc = minecraft.Minecraft.create(address="127.0.0.1", name="bob")

#Get current player's position
pos = mc.player.getPos()

# Returns Vec3(18.3814903971,6.0,25.6063951368)
# Can be accessed as pos.x, pos.y, and pos.z
print pos.x, pos.y, pos.z

```

</details>


<details>
  <summary>
mc.player.setPos()
  </summary>

> Set current player's position exactly (supports decimals)

```python

from mcpi import minecraft

#Connect to minecraft server 127.0.0.1 as player 'steve'
mc = minecraft.Minecraft.create(address="127.0.0.1", name="bob")

#Get current player's position
pos = mc.player.getPos()

#Set current player's position 100 blocks in the air
mc.player.setPos(pos.x, pos.y+100, pos.z)

```

</details>

 - chat.post
 - events.clear
 - events.block.hits
 - player.getTile
 - player.setTile
 - player.getPos
 - player.setPos
 - world.getHeight
 - entity.getTile
 - entity.setTile

Features that can't be supported:
 - Camera angles

Extra features(**):
 - getBlocks(x1,y1,z1,x2,y2,z2) has been implemented
 - getDirection, getRotation, getPitch functions - get the 'direction' players and entities are facing
 - getPlayerId(playerName) - get the entity of a player by name
 - pollChatPosts() - get events back for posts to the chat
 - multiplayer support
   - name added as an option parameter to player calls
   - modded minecraft.py in python api library so player "name" can be passed on Minecraft.create(ip, port, name)
   - this change does not stop standard python api library being used
 - the default tcp port can be changed in config.yml

** to use the extra features an modded version of the java and python libraries that were originally supplied by Mojang with the Pi is required, https://github.com/zhuowei/RaspberryJuice/tree/master/src/main/resources/mcpi.  You only need the modded libraries to use the extra features, the original libraries still work, you just wont be able to use the extra features

** please note extra features are NOT guaranteed to be maintained in future releases, particularly if updates are made to the original Pi API which replace the functionality


Version history:
 - 1.1 - Initial release
 - 1.1.1 - block hit events
 - 1.2 - added world.getBlockWithData
 - 1.3 - getHeight, multiplayer, getBlocks
 - 1.4 - bug fixes, port specified in config.yml
 - 1.4.2 - bug fixes
 - 1.5 - entity functions
 - 1.6 - added getPlayerId(playerName), getDirection, getRotation, getPitch
 - 1.7 - added pollChatPosts() & block update performance improvements
 - 1.8 - minecraft version 1.9.2 compatibility
 - 1.8tc - Teachcraft version, added polling projectiles and focused on Multiplayer support

 https://hub.spigotmc.org/javadocs/spigot/index.html?org/bukkit/event/entity/FoodLevelChangeEvent.html
 /Users/emeth/Downloads/apache-maven-3.5.0/bin/mvn  package