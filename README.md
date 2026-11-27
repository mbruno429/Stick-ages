# Stick Ages

A stick-figure fighting game in one file. Pick a fighter, pick a weapon, and climb 19 tiers from the Stone Age to the modern day. Every tier you clear hands over a new weapon, a new fighter, or both, and every tier's opponent is sharper and hits harder than the last.

There is no build step and nothing to install. `index.html` is the whole game: drawing, sound and saving are all done in code, so there are no image or audio files.

## Play it

**https://mbruno429.github.io/Stick-ages/**

GitHub Pages serves the game straight from the root of the `main` branch, so a new `index.html` on `main` updates the live game within a minute or two.

On the iPhone, open the link in Safari, then **Share → Add to Home Screen**. Launched from the home screen it runs full screen with no browser bars, which is how it is meant to be played. Hold the phone in landscape. If rotation lock is on, tap **Play sideways** and leave the lock alone.

## Controls

On the phone the whole screen is the controller: tap, swipe and hold anywhere, with as many fingers as you like. The only buttons are the three meter buttons in the bottom-left corner.

| | Phone | Keyboard | Controller |
|---|---|---|---|
| Attack (keep tapping to chain) | Tap | J | A |
| Rush in and strike | Swipe toward them | Shift | RB |
| Back flip out of reach | Swipe away | Shift + away | RB + away |
| Leap at them | Swipe up | Shift + W | RB + up |
| Slide under and trip them | Swipe down | Shift + S | RB + down |
| Guard | Hold a finger still | L | B or LT |
| Keep running, backing off or staying low | Leave the finger down after a swipe | Hold the direction | Hold the direction |
| Special 1 (one bar of meter) | 1 | U | Y |
| Special 2 (two bars) | 2 | I | LB |
| Super (all three bars) | Bolt | O or Space | RT |
| Move, jump, crouch, kick | | A D, W, S, K | Stick, X |
| Pause | Pause button | P or Esc | Start |

If you would rather have a thumb stick and buttons, switch **Options → Touch controls** to **Buttons**.

### Combos

Once a hit lands:

- **Tap** for the next hit of your weapon's string.
- **Swipe up** to launch them. Keep tapping while they are in the air, or swipe up again to leap after them and spike them into the floor.
- **Swipe toward them** to knock them across the arena. Near the edge they bounce off the wall, and you get one more hit.
- **Swipe down** to sweep them off their feet.
- **Tap 1 or 2** to cancel straight into a special.

A rush that connects flows into all of these too. The pause menu has a **Moves** list for whatever you are holding.

Things worth knowing: bullets and rockets fly at chest height, so a slide or the first steps of a rush go under them. Getting shot while running in staggers you. A guard only blocks from the front and breaks if it soaks up too much. Axes and hammers shrug off one light hit per swing, and a revving chainsaw ignores bullets. With a gun, a swipe cuts the pause after a shot short, so you can fire and flip away. An empty gun kicks until it has reloaded.

## What is in it

- **11 fighters.** Four from the start (Ash, Volt, Brick, Nyx). The six era bosses and the final boss become playable when you beat them. Each has different health, speed, power and jump, plus one perk.
- **19 weapons** across six eras: fists, bone club, flint spear, sling, bronze sword, longbow, war axe, crossbow, warhammer, katana, flintlock, cutlass, revolver, dynamite, shotgun, chainsaw, SMG, sniper rifle, rocket launcher.
- **Two specials and a super for every weapon,** 57 in all, on a three-bar meter that fills as you deal and take hits: thrown spears and clubs, blades of air, shockwaves along the floor, arrow rain, grenades, guard-piercing rounds, rocket barrages. The weapon screen demonstrates each one.
- **19 tiers**, three per era with a boss on every third, then a final boss who changes weapon as his health drops. Seven arenas.
- **Ascension**, an endless run of harder fights that opens after the last tier.
- Opponents that use the same moves you do, and use more of them, more cleverly, at each tier.
- Coaching in your first fights that teaches the gestures one at a time.
- Best-of-three rounds, guard breaks, juggles, wall and floor bounces, knockdowns, reloads.
- Progress saves in the browser on that device.

Losing to the same tier takes 5% off that opponent's health for each rematch, up to 25%, so nobody stays stuck for good. The defeat screen says so.

## Changing things

Everything is in `index.html`, in labelled sections. The ones you are most likely to touch:

- `data: eras, weapons, fighters, tiers` holds every number that matters. Weapon damage, speed and reach are in `WEAPONS` and `PROJ`. Each weapon's rush strike, launcher, knock-away, leap, specials and super are built in `buildMoves`, which is also where the specials' names and descriptions live. Fighter stats are in `FIGHTERS`. The tier list, who you fight and what each tier unlocks are in `TIERS` and the `tier:` field on each weapon and fighter. The difficulty slope is the `difficulty()` function.
- `DMG` near the top of the combat section scales all damage at once. Lower it for longer rounds. `METER_MAX` and `JUG_MAX` beside it set the meter size and how long a juggle can last.
- The swipe feel is set by `SW_MIN` (how far a finger travels before it counts as a swipe), `HOLD_MS` (how long a still finger takes to become a guard) and `TAP_MS` at the top of the input section.
- Add `?dev` to the address to unlock everything and show the frame rate.

## Not in yet

- **Music.** There are sound effects, all synthesized, but no soundtrack.
- **A real-phone pass.** It was built and tested in a desktop browser set to the iPhone 16's landscape size, with simulated touches and swipes. Thumb feel, the swipe and hold thresholds, frame rate and sound on an actual phone still need checking.
- **Hand-tuned balance.** Weapon strength, the specials and the difficulty slope were tuned by running thousands of computer-versus-computer rounds, not by people playing.
- **Two players.** It is single player only.
- **Cosmetic skins.** The unlockable looks are whole fighters with their own stats. There are no alternate colours or outfits for a fighter you already have.
- **Fighter-specific moves and throws.** Specials belong to weapons, so two fighters holding the same weapon share a move list. There are no grabs.
- **Offline play and a proper app icon.** The home-screen icon is drawn at launch. A real icon file, a web manifest and a service worker would make it installable and playable with no connection.
- **Cloud saves.** Progress stays on the device and browser it was earned on. The home-screen copy and the Safari tab keep separate saves.
