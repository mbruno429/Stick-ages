# Stick Ages

A stick-figure fighting game in one file. Pick a fighter, pick a weapon, and climb 19 tiers from the Stone Age to the modern day. Every tier you clear hands over a new weapon, a new fighter, or both, and every tier's opponent is sharper and hits harder than the last.

There is no build step and nothing to install. `index.html` is the whole game: drawing, sound and saving are all done in code, so there are no image or audio files.

## Play it

**https://mbruno429.github.io/Stick-ages/**

The game is meant to be served by GitHub Pages straight from the root of the `main` branch. If that link shows a 404, Pages is switched off: open **Settings → Pages**, choose **Deploy from a branch**, pick `main` and `/ (root)`, and save. After that, pushing a new `index.html` to `main` updates the live game within a minute or two.

On the iPhone, open the link in Safari, then **Share → Add to Home Screen**. Launched from the home screen it runs full screen with no browser bars, which is how it is meant to be played. Hold the phone in landscape. If rotation lock is on, tap **Play sideways** and leave the lock alone.

## Controls

| | Phone | Keyboard | Controller |
|---|---|---|---|
| Move, jump, crouch | Left thumb stick | A D W S or arrows | Stick or d-pad |
| Attack (tap again to chain) | Weapon button | J | A |
| Kick, or sweep from a crouch | Kick | K | X |
| Guard (hold) | Guard | L | B |
| Dash | Dash | Shift | RB |
| Super, when the red meter is full | Super | Space | Y |
| Pause | Pause button | P or Esc | Start |

Things worth knowing: bullets and rockets fly at chest height, so a crouch or a forward dash slips under them. A guard only blocks from the front and breaks if it soaks up too much. A gun that is empty kicks until it has reloaded. Holding the attack button keeps a ranged weapon firing.

## What is in it

- **11 fighters.** Four from the start (Ash, Volt, Brick, Nyx). The six era bosses and the final boss become playable when you beat them. Each has different health, speed, power and jump, plus one perk.
- **19 weapons** across six eras: fists, bone club, flint spear, sling, bronze sword, longbow, war axe, crossbow, warhammer, katana, flintlock, cutlass, revolver, dynamite, shotgun, chainsaw, SMG, sniper rifle, rocket launcher.
- **19 tiers**, three per era with a boss on every third, then a final boss who changes weapon as his health drops. Seven arenas.
- **Ascension**, an endless run of harder fights that opens after the last tier.
- Best-of-three rounds, guard meter, super meter, combos, knockdowns, reloads.
- Progress saves in the browser on that device.

Losing to the same tier takes 5% off that opponent's health for each rematch, up to 25%, so nobody stays stuck for good. The defeat screen says so.

## Changing things

Everything is in `index.html`, in labelled sections. The ones you are most likely to touch:

- `data: eras, weapons, fighters, tiers` holds every number that matters. Weapon damage, speed and reach are in `WEAPONS` and `PROJ`. Fighter stats are in `FIGHTERS`. The tier list, who you fight and what each tier unlocks are in `TIERS` and the `tier:` field on each weapon and fighter. The difficulty slope is the `difficulty()` function.
- `DMG` near the top of the combat section scales all damage at once. Lower it for longer rounds.
- Add `?dev` to the address to unlock everything and show the frame rate.

## Not in yet

- **Music.** There are sound effects, all synthesized, but no soundtrack.
- **A real-phone pass.** It was built and tested in a desktop browser set to the iPhone 16's landscape size, with simulated touches. Thumb feel, frame rate and sound on an actual phone still need checking.
- **Hand-tuned balance.** Weapon strength and the difficulty slope were tuned by running thousands of computer-versus-computer rounds, not by people playing.
- **Two players.** It is single player only.
- **Cosmetic skins.** The unlockable looks are whole fighters with their own stats. There are no alternate colours or outfits for a fighter you already have.
- **Deeper move lists.** Each weapon has one attack string and one super. Kick, sweep and jump kick are shared. There are no throws.
- **Offline play and a proper app icon.** The home-screen icon is drawn at launch. A real icon file, a web manifest and a service worker would make it installable and playable with no connection.
- **Cloud saves.** Progress stays on the device and browser it was earned on. The home-screen copy and the Safari tab keep separate saves.
