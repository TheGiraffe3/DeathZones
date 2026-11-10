# Death Zones

A BZFlag plugin that introduces the `DEATHZONE` map object. Any tank that enters this zone 
will be killed. 

## Requirements

- C++11
- BZFlag 2.4.14+

## Usage

### Loading the plug-in

This plug-in does not take any special configuration options at load time.

```
-loadplugin DeathZones
```

### Custom Map Objects

```text
# Rectangle
deathzone
  position <x> <y> <z>
  size <x> <y> <z>
  rotation <rot>
  team <team>
  privatemessage "Watch out for the death zones!"
  publicmessage "%player% just died!"
end
```

```text
# Cylinder
deathzone
  position <x> <y> <z>
  height <height>
  radius <radius>
  team <team>
  # Don't send a private message.
  privatemessage
  publicmessage "%player% just died!"
end
```

- `privatemessage` (optional) - A message to send to the player who died. If not provided, defaults to "You entered a death zone!"; if no second token is provided, sends no message.

- `publicmessage` (optional) - A message to send to all players. Blank by default. Any instances of `%player%` in the message will be replaced with the victim's username.

- `team` (optional) - This option restricts the deathzone to only affect tanks of a certain color.  If this option is left out, it'll apply to all teams. You may use this option multiple times to specify multiple teams. Supported values:
  - 0 - Rogue Team
  - 1 - Red Team
  - 2 - Green Team
  - 3 - Blue Team
  - 4 - Purple Team
  - 5 - Rabbit Team
  - 6 - Hunter Team