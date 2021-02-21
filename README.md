# V2-work
PLEASE DO READ ALL THOUGHT THESE ARE CODE

# How many blocks should be placed per
 second. (1-20)
speed: 2

# The max height blocks can gen at.
height-limit: 256

# How many blocks UPWARDS/ANY gens travel vertically.
vertical-travel: 256

# How many blocks HORIZONTAL/ANY gen travel horizontally.
horizontal-travel: 32

# How many chunks HORIZONTAL_BY_CHUNK/ANY_BY_CHUNK gens travel horizontally.
chunk-travel: 1

# Whether to drop items if a players inventory is full when doing the /gba give command. (false means it will show an error message instead)
give-drop-item-if-full: true

# Whether to drop items if a players inventory is full when buying from the shop. (false means it will show an error message instead)
shop-drop-item-if-full: false

# Make infinite genbuckets disappear when dropped. This is for convenience.
infinite-buckets-disappear: true

# Check for nearby players in this radius. Set to 0 to disable. Also compares faction relationships if applicable.
player-check-radius: 0.0

# Check for sponges in this radius and stop the genbucket if they are found. Set to 0 to disable.
sponge-check-radius: 0.0

# Allows you to punch/break a fake wool block at the base of the genbucket to cancel it.
enable-cancelling: true

# Should a block be added under gravity blocks to allow it to generate downwards smoothly?
add-block-under-gravity-blocks: true

# The block used for the above confition.
gravity-block: COBBLESTONE

# Define your genbuckets here. This part may get a bit confusing with all the indents, its best to copy one of the examples
# and then just edit it to your liking. Feel free to double check your formatting 
items:
  any_direction_cobble: # The name of the bucket, can be anything. No spaces! This will be used to get the item ingame.
    item:
      name: '&7Any Direction Cobble Bucket' # The item name when in the player's inventory.
      material: 'COBBLESTONE'  # The item material when in the player's inventory. Feel free to use data/damage values.
      lore:
        - '&7This magical block creates cobblestone' # The item lore when in the player's inventory.
        - '&7in any direction when placed!'
      glow: true # Whether the item in the player's inventory should glow.
    block:
      material: 'COBBLESTONE' # The block that will gen when this bucket is placed.
      # The direction of this bucket, can be one of these 4:
      # 'UPWARDS' - Will gen up from the block it's placed on
      # 'DOWNWARDS' - Will gen down from the block it's placed on. (TIP: Do not use for blocks with gravity like sand/gravel)
      # 'HORIZONTAL' - Will gen sideways from the block it's placed on. The direction depends on what the bucket was placed against.
      # 'ANY' - Can gen upwards, downwards, or horizontally. The direction depends on what the bucket was placed against.
      direction: 'ANY'
      count-by-chunk: false # This means it will count chunks instead of blocks while generating.
      patch: false # Whether this is a patch bucket- meaning it can go through blocks of its same type to patch holes.
      delete: false # Whether this bucket will bypass the "ignored-blocks-list" and just place over every block in its path.
    gui:
      name: '&7Any Direction Cobble Bucket (BUY)' # The item name shown in the shop gui.
      material: 'COBBLESTONE' # The material name shown in the shop gui.
      lore:
      - '&7Buy a magical block that creates cobblestone' # The item lore shown in the shop gui.
      - '&7from the ground to the sky when placed!'
      - '&7COST: &e$200'
      - '&eShift-click&7 to buy 16! (&e$3200)'
      glow: true # Whether the item in the gui should glow.
      slot: 11 # The slot this item will appear in the shop GUI. To count the slot number, count from left-right-up-down, and subtract 1.
    buy-price: 200 # The cost of this item to buy this item from the GUI.
    infinite: false # Whether the gen has unlimited places, but will instead charge to place. (also known as printer mode genbuckets)
    place-price: 0 # How much to charge the player per placement if infinite (above) is set to true.
  horizontal_obby: # Bucket two, follows the same format as above. Feel free to copy and paste the example bucket and just change the values.
    item:
      name: '&7Horizontal Obsidian Bucket'
      material: 'OBSIDIAN'
      lore:
        - '&7This magical block creates obsidian'
        - '&7sideways when placed!'
      glow: true
    block:
      material: 'OBSIDIAN'
      direction: 'HORIZONTAL'
      count-by-chunk: false
      patch: false
      delete: false
    gui:
      name: '&7Horizontal Cobble Bucket (BUY)'
      material: 'OBSIDIAN'
      lore:
        - '&7Buy a magical block that creates obsidian'
        - '&7sideways when placed!'
        - '&7COST: &e$1000'
        - '&eShift-click&7 to buy 16! (&e$16000)'
      glow: true
      slot: 14
    buy-price: 1000
    infinite: false
    place-price: 0

# All the settings for the shop GUI.
gui:
  enabled: true # Whether the GUI shop is enabled. You can disable this for example if you'd like to make your own shop in ShopGUI with commands.
  title: '&7GENBUCKET SHOP' # The title of the shop GUI inventory.
  rows: 3 # How big the inventory will be (in rows).
  bulk-buy-amount: 16 # How many buckets will a player be able to buy when they shift and click? (bulk buy)
  exit: # Customize the exit button in the shop GUI.
    item: 'BARRIER'
    name: '&cExit the shop!'
    lore: []
    slots: # What slots the exit button will appear on.
      - 26
    glow: true
  fill: # This will automatically fill all the empty slots in the GUI.
    item: 'STAINED_GLASS_PANE:7'
    name: ''
    lore:
      - ''
    glow: false

# Which blocks will be ignored by the genbucket.
ignored-blocks:
  - 'AIR' # If you remove AIR, gen buckets will probably not work.
  - 'DOUBLE_PLANT'
  - 'RED_ROSE'
  - 'SNOW'
  - 'LONG_GRASS'
  - 'YELLOW_FLOWER'
  - 'DEAD_BUSH'
#  - 'LAVA'
#  - 'WATER'
#  - 'STATIONARY_LAVA'
#  - 'STATIONARY_WATER'

# Which blocks will be ignored by delete buckets.
delete-blacklist:
  - 'BEDROCK' # Delete buckets will not delete bedrock.

# Define custom recipes for your buckets here. Read the comments carefully to learn how they work.
recipes:
  any_direction_cobble: # Specify the bucket name here.
    symbols: # Specify symbols to represent items (makes your life easier). The symbol can be any single-letter character. Don't list symbols that you don't use in recipe:.
      O: 'OBSIDIAN'
      B: 'BARRIER'
    recipe: # Shape your recipe here, look at it like a crafting table.
      - 'OBO' # The 3 slots on the first line are the 3 slots on the top of a crafting table
      - '   ' # These are the slots in the middle.
      - '   ' # These are the slots at the end. To craft this bucket, you need obsidian, barrier, obsidian on the top row of the crafting table.
    outcome-amount: 1
  horizontal_obby:
    symbols:
      R: 'BEDROCK'
    recipe:
      - 'R  '
      - 'R  '
      - 'R  '
    outcome-amount: 1

# Hook into other plugins for checks when genning blocks.
hooks:
  factions: true # Check each block's territory
  worldguard: true # Check for 'block-break: deny' flag for each block
  worldborder: true # Will make sure blocks cannot be placed past the border of this plugin (minecraft worldborder will check regardless of this setting)
  coreprotect: false # Will log every single block placed to allow rollbacks.

# Settings for factions if the hook is enabled.
factions:
  requires-faction: true # Whether you need a faction or not to place a gen bucket.
  can-place-wilderness: true # If you can place gen buckets in wilderness.

# Customize messages sent to the player. Set to '' for no message.
messages:
  give: '&aYou gave {player} {amount} {bucket} genbuckets(s).' # Message to the person who executed /gba give.
  receive: '&aYou have received {amount} {BUCK CBA TO RIGHT BUT HERE IS MY 3
HOURS OF WRIITING PLEASE ENJOY 
