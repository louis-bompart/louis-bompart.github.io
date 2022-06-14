# Integrate Moonlight with Steam Deck UI

## What is a Steam Deck?

> The Steam Deck is a handheld gaming computer developed by Valve [^1]

https://store.steampowered.com/steamdeck

## What is Moonlight?

> Moonlight (formerly Limelight) is an open source implementation of NVIDIA's GameStream protocol.

https://moonlight-stream.org/

In short: It allows a machine (in this instance, a Steam Deck) to stream game from another machine using Nvidia custom sauce.


## What is the goal here?

To have a seamless experience between launching a game through Moonlight and to stream a game with Steam Remote Play.

## But why?

- Non-Steam games, especially UWP (looking at you GamePass users) are a pain to setup with Steam Remote Play.
- Users on /r/SteamDeck and /r/Steam boast better perfs with Moonlight.

## End result

[!list]
_Games individually listed in the non-steam games section_

[!GamePage]
_Game images from SteamGridDB_

Press play and then... 

[!GameStart1]
_Moonlight starting automatically the game on the Host Machine..._

[!GameStart2]
_And the game, ready to play!_

## Prerequisites:
 - Have a Steam Deck
 - Have another computer, with a recent Nvidia graphic card (later refed as Host Machine)
 - Ensure your Host Machine is setup to GameStream. See [Moonlight Setup Guide](https://github.com/moonlight-stream/moonlight-docs/wiki/Setup-Guide#quick-setup-instructions)

## Setup steps

### Installing Moonlight

The Steam Deck ship with Flatpak as its package manager, you can use it directly, or use Discover.
If you use Discover, wait for Discover to find all the packages, it'll take a while. Then look for Moonlight from "Moonlight Game Streaming Team" and install it.

If you're used to use a package manager through the terminal, by all mean, do so. (won't hold your hands)

### Testing Moonlight

Before going throught the hoops to set it up with Steam, let's try it out.
With your Host Machine on and on the same network as your Steam Deck, start Moonlight.
You should see your Host Machine listed in. Take note of its name, you'll need it. If your Host Machine is not listed, refer to [Moonlight Troubleshooting Guide](https://github.com/moonlight-stream/moonlight-docs/wiki/Troubleshooting).

Click/Touch it, you should have a pairing code popup on your Host Machine and the said code on your Deck. You know what to do.

Now, try to launch a game.
Ensure that your control are pass thru properly, if not, back on the Moonlight, click the cog up right and check "Force gamepad #1 always connected".

All's working? Good, now, let's set up a 'moonlighted' game in Steam

### Setting up a Moonlighted game

#### Adding a Moonlight shortcut
Technical explanation:
We're about to set a steam app to launch moonlight cli with some arguments that will allow moonlight to start the game directly.


- From the desktop experience, start Steam and goto 'Add a non-steam game' (click Add a game and select the option).
- Select Browse
- Navigate to `/var/lib/flatpak/exports/bin/`
- Change "File type" to "All files"
- Select `com.moonlight stream.Moonlight`
- Click Open.
- Click on Add Select Programs.

From here, you can launch Moonlight from Steam. But that's not our end goal.

#### Parametrizing Moonlight Shortcut

- In your steam library, left click `com.moonlight stream.Moonlight` and select properties.
- In the launch options put: `stream $HOST_MACHINE_NAME "Game of your Name"`. So for example, if my host machine name is GLAD0S and I want to play Portal 2 I should put `stream GLAD0S "Portal 2"`
- Change the name from `com.moonlight stream.Moonlight` to the name of your game (I mean, I'd do that if I were you...)

From here, your game is playable directly from the Steam Deck experience. However, no picture nothing, pretty ugly innit.

#### Customizing Game Shortcut

To customize your new shortcut, we'll use [SteamGridDb](https://www.steamgriddb.com].

- Create an account
- Install [SGDBoop](https://www.steamgriddb.com/boop) (Flatpak is the option your looking for).
- Press dat boop button.
- Restart your Steam Deck, go back to the Desktop.
- Look for your game on SteamGridDb and pick the assets you want to use.
- For each asset type (grids, heroes, icons, logos) do the following step:
  - Hover it and click on the Boop button with a + icon "Apply with BOOP (non-steam)"
  - Chrome will prompt you with a pop-up, click on "Open xdg-open"
  - That will open an app on your Deck, select the Game you created, and click OK.
- Profit.

And that's all, your game is setup, you can go back to your deck. :tada:


[^1]: https://en.wikipedia.org/wiki/Steam_Deck
