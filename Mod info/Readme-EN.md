[![ru](https://img.shields.io/badge/%D0%A0%D1%83%D1%81%D1%81%D0%BA%D1%8F_%D0%B2%D0%B5%D1%80%D1%81%D0%B8%D1%8F_readme-green
)](https://github.com/mickromash/InterpolatedWeapons/blob/5.0%2B/Mod%20info/Readme-RU.md)
# Fluid Weapons (a.k.a. Interpolated Weapons)
UZDoom weapon mod with interpolated weapon animations, particle effects and more.


***
**Contents**
* [Requirements](#Mod-requirements)
* [Compatibility](#Compatibility)
* [Features](#Mod-features)
* [Mod settings (CVars) list](#Mod-settings-CVars)
   * [Main settings](#Options----Configure-Interpolated-weapons)
     * [Main animations settings](#Options----Configure-Interpolated-weapons----Animations-settings)
       * [General weapon settings](  #Options----Configure-Interpolated-weapons----Animations-settings----General-weapon-settings)
       * [Weapons customization](#Options----Configure-Interpolated-weapons----Animations-settings----Customize-weapons)
   * [Particles](#Options----Configure-Interpolated-weapons----Particles-settings)
   * [Sound](#Options----Configure-Interpolated-weapons----Sound-settings)
   * [UI](#Options----Configure-Interpolated-weapons----UI-settings)
* [Credits](#Credits)
* [For other modders](#For-other-modders)
* [Download mod](#ColorFF0000Give-me-the-damn-download-you-nerd)
***

## What's the difference between this and other weapon mods like Smooth Doom or Beautiful Doom?
The main reason of creation of this mod was to popularize the usage of interpolation in weapon mods.
With it, weapon animations aren't capped at 35 fps unlike animation in most of the weapon mods to date.
Interpolated animations look smooth if the game is running in 60 fps, 90 fps or 120 fps and more, or even if you slow time with
`i_timescale` command or with other mods.  
Besides that, there's no actor based visual effects in this mod, instead particles and visual thinkers are used, which makes the mod
lighter on the performance and makes all of the visual options to be client-sided.

## Mod requirements
* GZDoom (4.14.2), UZDoom, LZDoom (4.14.3 or newer), or any other source port that supports zscript 4.14.2 or newer.
* Any iwad (doom.wad, doom2.wad, plutonia.wad, freedoom.wad), but keep in mind that the mod was tested and designed for official DOOM wads,
and even though it's possible to run the mod with, let's say, freedom, its sprites won't magically change to fit the game.
* Wad Smoosh is also supported

## Compatibility
* Mod is supossed to work with most of the enemy randomizers or map packs, but I recommend to set it later in your mods loading order.
* Thanks to weapon giving algorythm used in the mod that doesn't involves changes in playerpawn class, the mod is compatible with mods like ZMovement.
* Since almost every graphics in the mod is made in DOOM .lmp format, the mod is compatible with mods that changes the game color palette  
however, only gloves with classic color will be changed by custom palette.
* In theory, the mod should work with other weapon mods, but in most cases you won't be able to use weapon of either of the mods.

## Mod features
* Fluid weapon animations with no framerate cap.
* Vanilla gameplay: mod doesn't affect weapon mechanics, including time of switching or firing, damage randomization or anything else.
Weapon states that affect gameplay were directly coppied from code files within UZDoom.pk3 and was edited for audio/visual purposes only.
However, there are some options in the mod settings that change gameplay, most of them are marked with "🌐" symbol. These options include
better monsters alerting, instant firing (this option remove delay after players presses firing button and before weapon actually fires, without changing weapon firing rate),
faster pistol firing, quick switching and berserk fists kickback.
* Customization: almost every part of the mod, like speciffic animations or effects, can be turned on and off.
* Client-side: most of mod visual or audio settings do not affect other players game in multiplayer. All server settings are marked with "🌐" symbol.
* Visual recoil and screen shake can be turned on and configured.
* Gloves color: you can choose classic tan, black, red, blue, green or any color you want for your gloves. There's even a speci
* Weapon bob and sway: you can choose different bob styles, configure bob amount on Z axis and even turn on firing bob login from DOS Doom. Besides that, there's an option for two weapon sway styles: Half Life 2 and SW Battlefront (2015).
* Various idle animations.
* Casings can be set to appear only as animations or as an actual object inside the game.
* There are 4 types of smoke in the mod:
	* Overlay: simple animations inside weapon states, like chainsaw smoke or smoke comming from shotgun's chamber.
	* Firing smoke: clouds of smoke made via visual thinkers that comes from the weapon on firing. The amount of this smokes depends on last shot damage.
	* Flowing smoke: you could've seen simillar concept in Bioshock games. Amount of the smoke is depends on how much you've been shooting.
	* Long-term smoke: clouds of smoke that cluster on the ceilling after a player was shooting for a long time in one place.
* A lot of different particle effects for projectiles, monsters and decorations, each can be turned on and off and combined with others. The amount of particles can be configured
* Presets feature: there are 2 build in presets, vanilla, and advanced. One makes the game look and play as close to vanilla doom as possible, and the other toggles as much options as possible.
* Simple dying animation with player dropping their weapon
* Smooth animations in menus

## Mod settings (CVars)

* All CVars and CCMDs can be seen by typing `MRIntW` in the game console and pressing [TAB]
* CVar types:
	* server - CVars of this type affect all players in the game. (example: fast pistol firing works for every player if it turned on by the host)
	* user - personalized settings which effects still can be seen by other players. (example: every player can set their own gloves color, but other players will be seeing gloves with the color set by you on your hands)
	* nosave - fully client-sided settings that do not affect other players game in any way. Their values also won't change after loading a saved game or a demo. (example: turning on or off particle effects won't make them appear for other players and won't affect their performance)
   
### Options --> Configure Interpolated weapons
| Setting name | [CVar type] CVar | Default | Description |
| --- | --- | --- | --- |
| Fix weapon dynamic lighting | [server] MRIntW_Lighting | Yes | Fixes weapons firing lighting. There's no point in turning this off |
| Better monster alerting | [server] MRintW_BetterAlert | No | Makes monsters react on player's sounds more naturally. Monsters won't react on player punching the air and will be alerted by a working chainsaw |
| Visual recoil | [user] MRIntW_Recoil | No | Weapon actions will raise player's camera and slowly return it back |
| Recoil amount | [user] MRIntW_RecoilAmount | 1 | Strength of the recoil or smth |
| Recoil compensation | [user] MRIntW_RecoilRecover | 1 | The speed of camera returning from being raised by recoil |
| Screen shake | [nosave] MRIntW_ScreenShake | No | Screen shaking by weapon actions or explosions |
| Screen shake amount | [nosave] MRIntW_ScreenShakeAmount | 1 | Strength of the screen shake |
| Instant firing | [user] MRIntW_InstantFire | Yes | Removes firing delay without changing the fire rate |
| Fast pistol | [server] MRIntW_FastPistol | No | Increases pistol firing rate making it a bit more useful |
| Quick switching | [server] MRIntW_QuickSwitch | No | Ability to switch weapon during reloading or similar animations |
| Legacy of Rust Weapons | [server] MRIntW_LoRWeaps | Yes | Enables Legacy of Rust weapons in regular Doom and adds animations for weapons in Legacy of Rust |

### Options --> Configure Interpolated weapons --> Animations settings
| Setting name | [CVar type] CVar | Default | Description |
| --- | --- | --- | --- |
| Gloves color | [user] MRIntW_GlovesColor | Classic | Player's gloves color on weapon sprites |
| Custom color shades | [user] MRIntW_GlovesColorShade | 2 2 2 | If gloves color is set to "Custom", gloves will be colored with gradient of MRIntW_GlovesColorShade and MRIntW_GlovesColorLight. I recomend you to set MRIntW_GlovesColorShade to the darkest value possible |
| Custom color lights | [user] MRIntW_GlovesColorLight | EF EF EF | Gloves hue mostly depends on this one |
| Pickup and reload animations | [nosave] MRIntW_ReloadAnims | Reload only | Если на оружии кончаются патроны, или при первом его подборе, будет проигрываться альтернативная анимация выбора |
| Disable muzzle flashes | [nosave] MRIntW_NoMuzzleFlash | No | Disables muzzle flashes for weapons like in Doom Retro source port |
| Muzzle flash flare | [nosave] MRIntW_FlashFlare | No | Bloom-like effect around muzzle flashes |
| Randomize customization | [user] MRIntW_RandomStart | No | On the start of the level for player and weapon customization will be used random values, instead of ones set in the settings. This won't changed values set in the settings. |
| Untitled | [nosave] MRIntW_RandomDemo | Yes | Apply setting above to demo playback |

### Options --> Configure Interpolated weapons --> Animations settings --> General weapon settings
| Setting name | [CVar type] CVar | Default | Description |
| --- | --- | --- | --- |
| Weapon bob style | [nosave] MRIntW_BobStyle | Smooth | The way weapon moves while walking |
| Bob X range | [nosave] MRIntW_BobRangeX | 1 | The horizontal range of weapon movement while walking |
| Bob Y range | [nosave] MRIntW_BobRangeY | 1 | The vertical range of weapon movement while walking |
| Bob Z range | [nosave] MRIntW_BobRangeZ | 0 | The inward range of weapon movement while walking. Similar to Rise of The Triad. Doesn't work with the chaingun, plasma rifle, BFG and calamity blade |
| Weapon bob when firing | [nosave] MRIntW_ChangeFiringBob | 1 | Amount of weapon bob during firing |
| Original (DOS) Doom firing bob | [nosave] MRIntW_VanillaFireBob | No | During firing weapon will stay in the same spot instead of continue bobbing or moving to the screen center |
| Switch animations | [nosave] MRIntW_SwitchAnims | Random variants | Animations that will play when switching weapons |
| Bounce on land | [nosave] MRIntW_Bounce | Regular | Realistic weapon movement in air and on landing |
| Run key | [nosave] MRIntW_RunKey | Does nothing | Lowers weapon - if the run key (Shift) is being holded, the weapon will go to the bottom of the screen; Raises weapon - the weapon is always at the bottom of the screen and is raised when the run key is being holded |
| Weapon sway | [nosave] MRIntW_WeaponSway | No | Realistic weapon reaction to player moving the camera |
| Weapon sway style | [nosave] MRIntW_WeaponSwayStyle | Battlefront 2015 | Half Life 2 - the weapon lags behind the camera movement, stays in place when it stops moving, resets its offset on firing; Battlefront 2015 - depending on the weapon, it lags behind or outstrips the camera movement and tilts. When the camera stops, the weapon resets its offset with wobble effect |
| Idle animations | [nosave] MRIntW_IdleAnims | Yes | Breathing, warmping-up etc while idling. Some weapons got unique idle animations (also when pressing alt fire or reloading key the weapon plays more expressed animations) |
| Shake hands on damage | [nosave] MRIntW_DamageShake | Yes | Quick weapon shaking when receiving damage, like in Doom (2016). Shaking amount depends on the damage |
| Low health hands shaking | [nosave] MRIntW_LowHealthShake | No | Small weapon shaking when the player's health is or lower than 25 |
| Weapon offset | [nosave] MRIntW_BaseOffset | No | Moves the weapon away from the screen center |
| Horizontal offset | [nosave] MRIntW_BaseOffsetX | 0 | Weapon offset on X axis |
| Vertical offset | [nosave] MRIntW_BaseOffsetY | 0 | Weapon offset on Y axis (inverted) |

### Options --> Configure Interpolated weapons --> Animations settings --> Customize weapons
**Brass Knuckles**
| Setting name | [CVar type] CVar | Default | Description |
| --- | --- | --- | --- |
| Switch main fist | [user] MRIntW_RightPunch | No | Switches the hand with the brass knuckles |
| Hands shaking on berserk | [user] MRIntW_BersShake | Only without weapon | After picking up berserk the player's hands will start shaking and the fist with brass knuckles will shown on the screen |
| Bare hands | [user] MRIntW_BareHands | Yes | Use gloveles sprite for fists |
| Gloves removal animation | [user] MRIntW_GlovesStrip | Yes | When selecting fists the gloves removal animation will play (if the option above is turned on) |
| Second fist always on screen | [user] MRIntW_SecondFist | No | The hand with brass knuckles will be always shown on the screen |
| Punching fist | [user] MRIntW_PunchingFist | Main | With which hand the player will be punching |
| Finishing punch | [user] MRIntW_FinishPunch | Only berserk | Play special animation when the target is killed |
| Miss animation | [user] MRIntW_MissPunch | No | Play special animation when nothing is hit |
| Finishing punch chance | [user] MRIntW_FinishPunchChance | 0.7 | Chance of playing the finishing animation |
| Kickback from punching surface with berserk | [user] MRIntW_SurfacePunchRecoil | No | When hitting the level geometry (walls/floor/ceilling) after picking up berserk, the player will be thrusted in the opposite direction |
| Fix fist on punched actor | [nosave] MRIntW_FistFixedOnTarget | No | If the actor is hit, the fist will be fixed on it, ignoring the camera angle |

**Chainsaw**
| Setting name | [CVar type] CVar | Default | Description |
| --- | --- | --- | --- |
| Starting animation | [user] MRIntW_ChainsawStart | No | Special chainsaw select animation |
| Improved chainsaw cutting animation | [user] MRIntW_ChainsawCutting | Yes | When cutting through actor, procedural animations with random angle and speed will be played |
| Chainsaw surface cutting shaking | [user] MRIntW_ChainsawCuttingWall | Yes | When cutting the level geometry (walls/floor/ceilling) hands with the chainsaw will be shaking |
| Chainsaw smoke | [nosave] MRIntW_ChainsawSmoke | Yes | Smoke coming from chainsaw |
| Blood on the chainsaw | [nosave] MRIntW_ChainsawBlood | No | When cutting monsters or liquids on the level the chainsaw will be getting dirty |
| Blood dripping | [nosave] MRIntW_ChainsawBlood | No | Liquids dripping from the chainsaw |
| Blood time (in seconds) | [nosave] MRIntW_ChainsawBloodLife | 60 | Time before chainsaw starts cleaning up |

**Pistol**
| Setting name | [CVar type] CVar | Default | Description |
| --- | --- | --- | --- |
| Hold pistol in the left hand | [user] MRIntW_LHand | Yes | Doomguy is left-handed in the original game |
| Hold pistol with two hands | [user] MRIntW_PistolSHand | If enemy is far away | Depending on this setting, player will use two hands when attacking a target standing far away, switch to one hand when attacking a close target or always hold the pistol with two hands |
| Replace pistol with rifle | [user] MRIntW_Rifle | No | Visually replace the pistol with the rifle from the early Doom versions |

**Shotgun**
| Setting name | [CVar type] CVar | Default | Description |
| --- | --- | --- | --- |
| Smoke from chamber | [nosave] MRIntW_ShotgunSmoke | Yes | Smoke coming from the chamber when pumping the shotgun |
| Buckshot sparks | [nosave] MRIntW_ShotgunSparks | No | Sparks coming from the muzzle when firing |
| Pumping angle | [user] MRIntW_ShotgunPumpAngle | 0 | Shotgun angle when pumping it |
| Randomize angle | [user] MRIntW_ShotgunPumpRandom | No | Random angle for each pumping |
| Random radius | [user] MRIntW_ShotgunPumpRandRotation | 1 | The maximum value that can be randomly added to the angle |
| Shotguns firing animation recoil | [nosave] MRIntW_ShotgunsRecoil | 1 | How much the SSG and shotgun sprite is affected by recoil |

**Super Shotgun**
| Setting name | [CVar type] CVar | Default | Description |
| --- | --- | --- | --- |
| Holding stock while reloading | [user] MRIntW_SSGHandless | Always | The animation makes a bit more sense when the player got time to lower the hand to grab shells before loading them |
| Smoke from barrels on reload | [nosave] MRIntW_SSGSmoke | Yes | Smoke coming from the barrels after openning them |
| Buckshot sparks | [nosave] MRIntW_SSGSparks | No | Sparks coming from the muzzle when firing |
| Shotguns firing animation recoil | [nosave] MRIntW_ShotgunsRecoil | 1 | How much the SSG and shotgun sprite is affected by recoil |

**Chaingun**
| Setting name | [CVar type] CVar | Default | Description |
| --- | --- | --- | --- |
| Fixed barrels position | [user] MRIntW_ChaingunFixed | No | When stop firing the barrels will reset their position |
| Rotation speed | [user] MRIntW_ChaingunSpeed | 1 | This setting doesn't affect gameplay (like almost every other setting in this section) |
| Stopping power | [user] MRIntW_ChaingunStopTime | .3 | How fast the barrels stop spinning |
| Counterclockwise rotation | [user] MRIntW_ChaingunCounterClock | No | The more customization the better |
| Max. smoking barrels | [nosave] MRIntW_ChaingunMaxSmokes | 3 | Might help with the pefromance on the weakier devices. Besides that, the length of the smoke is divided by barrels amount |

**Rocket Launcher**
| Setting name | [CVar type] CVar | Default | Description |
| --- | --- | --- | --- |
| Muzzle smoke | [nosave] MRIntW_RocketSmoke | 1 | The strength of the smoke coming from the barrel |

**Plasma Rifle**
| Setting name | [CVar type] CVar | Default | Description |
| --- | --- | --- | --- |
| Firing particles | [nosave] MRIntW_PlasmaParticles | Only muzzle flare | Fancy! |
| Enable dyn. lighting for projectiles | [nosave] MRIntW_PlasmaLight | Yes | Enable dynamic lighting for plasma |
| Disable dyn. lighting for every second projectile | [nosave] MRIntW_PlasmaSkipLight | No | During continues firing, only even projectiles will emit dynamic light |

**BFG 9000**
| Setting name | [CVar type] CVar | Default | Description |
| --- | --- | --- | --- |
| Firing particles | [nosave] MRIntW_BFGParticles | Yes | Makes the firing animation much more interesting |

**Incinerator**
| Setting name | [CVar type] CVar | Default | Description |
| --- | --- | --- | --- |
| Smoking | [nosave] MRIntW_InciniSmoke | Both | Smoke coming from the gun |

**Calamity Blade**
| Setting name | [CVar type] CVar | Default | Description |
| --- | --- | --- | --- |
| Charging particles | [nosave] MRIntW_CalamityParticles | Yes | Particles coming from the charging gun |


### Options --> Configure Interpolated weapons --> Particles settings
| Setting name | [CVar type] CVar | Default | Description |
| --- | --- | --- | --- |
| Casings | [nosave] MRIntW_Casings | Animation only | Turns on casings for firearms |
| Max. casings speed | [user] MRIntW_CasingsRandom | 1 | The force with which the casings extract from the weapon |
| Casings bounce sound volume | [nosave] MRIntW_CasingsVolume | 1 | Hello |
| Max. casings amount | [nosave] MRIntW_CasingsAmount | 300 | If the casings amount will reach this limit, the oldest casings will vanish |
| Reduce casings clustering | [nosave] MRIntW_CasingsClusteringReduce | Yes | Prevent a lot of casings cluster in one place |
| Lowres casings | [nosave] MRIntW_CasingsLowRes | No | Alternative lowres sprite for casing objects (similar to ones found in Hideous Destructor) |
| Firing smoke | [nosave] MRIntW_Smoke | Yes | Smoke coming from the weapon when firing |
| Flowing smoke | [nosave] MRIntW_FlowingSmoke | No | Smoke that starts coming from the weapon after long firing, similar to the one from Bioshock series |
| Flowing smoke length | [nosave] MRIntW_FlowingSmokeLength | 0.6 | If the values is lower than 0.6 the smoke flow might have breaks |
| Flowing smoke opacity | [nosave] MRIntW_FlowingSmokeAlpha | 0.2 | How visible the smoke is |
| Max. smoking time | [nosave] MRIntW_FlowingSmokeMaxTime | 1 | For how long the smoke will coming from the weapon |
| Flowing smoke particles amount | [nosave] MRIntW_FlowingSmokePrecision | 1 | Controls the density of the flowing smoke particles. Lower values will increase performance, but individual particles might became more visible |
| Flowing smoke experimental texture | [nosave] MRIntW_FlowingSmokeBioTexture | No | The more detailed smoke more similar to the smoke from Bioshock. Doesn't work perfectly |
| Long term smoke | [nosave] MRIntW_LongTermSmoke | No | A pretty much experimental feature. When firing for a long time in the same spot, the room will be clustered with clouds of smoke |
| Particles texture | [nosave] MRIntW_ParticleTexture | Same as UZDoom particles | Mod's effects which are turned on in this menu use this setting to determine particles appearance. If set to "Same as UZDoom particles", source port's particles texture will be used |
| Smoke particles texture | [nosave] MRIntW_ParticleSmokeTexture | Smooth | This setting also is used only by effects below, but it only changes smoke-like particles texture. Added for cases in which the texture above doesn't fit for smoke effects |
| Player's weapon particles | [nosave] MRIntW_PlayerParticles | No | Adds effects for player projectiles and all bullet puffs |
| Player weapon effects quality | [nosave] MRIntW_PlayerParticlesAmount | 1 | Amount of the particles used by player effects. My GTX970 and Core i7 3770 can handle x2 value |
| Selected player weapon effects | [nosave] MRIntW_PlayerWhichParticles | 134021019 | All selected player effects are contained in one CVar as flags |
| Monsters particles | [nosave] MRIntW_MonsterParticles | No | Adds effects for monsters and their projectiles |
| Monsters effects quality | [nosave] MRIntW_MonsterParticlesAmount | 1 | Amount of the particles used by monsters effects. Maps with the big amount of monsters might require lower this value |
| Selected monsters effects | [nosave] MRIntW_MonsterWhichParticles and [nosave] MRIntW_MonsterWhichParticles2 | -33 and -2147483617 | Same as the player effects, but because of the amount of effects I had to use two CVars to contain them |
| Apply effects to custom monsters | [nosave] MRIntW_MonsterParticlesCustom | No | If this setting is disabled, only vanilla Doom monsters and projectile will have particle effects |
| Particle flies | [nosave] MRIntW_ParticleFlies | No | Flies spawning on corpses like in Quake 2 |
| Flies buzz volume | [nosave] MRIntW_ParticleFliesVolume | 0.4 | I think not everyone will like this sound |
| Alternative lightnings | [nosave] MRIntW_AltLightnings | No | By default, lightnings will appear instantly and slowly fade out. If that setting is tuned on, lightnings will quikly grow and then decompose |
| Decorations particles | [nosave] MRIntW_DecorationParticles | No | Enables particle effects for decorations |
| Decorations effects quality | [nosave] MRIntW_DecorationParticlesAmount | 1 | Amount of particles used in decorations effects |
| Selected decorations effects | [nosave] MRIntW_DecorationWhichParticles | 511 | Same as with player and monsters effects |
| Teleportation particles | [nosave] MRIntW_TeleportParticles | No | Enables particle effects for teleportations |
| Teleport style | [nosave] MRIntW_TeleportParticlesStyle | Wave | The available variants are: 2 rings, Explosion, Vapor, Reverse explosion, Double vapor, Weird cloud, Wave |
| Monster teleport style | [nosave] MRIntW_TeleportParticlesStyleMonsters | Vapor | Same as the previous one, but for monsters |
| Items respawn particles | [nosave] MRIntW_RespawnParticles | No | The available variants are: Cloud, Wave, Dots (I prefer the last one) |

### Options --> Configure Interpolated weapons --> Sound settings
| Setting name | [CVar type] CVar | Default | Description |
| --- | --- | --- | --- |
| Casings bounce sound voulme | [nosave] MRIntW_CasingsVolume | 1 | The same setting as in particles menu |
| Chainsaw idle volume | [nosave] MRIntW_ChainsawVolume | 1 | Some people might think the sound is anoying |
| Chainsaw idle pitch randomness | [nosave] MRIntW_ChainsawRandomPitch | 0 | Makes the chainsaw noise more variable |
| BFG alt fire volume | [nosave] MRIntW_BFGAltVolume | .6 | Volume of the BFG working sound during altfire animation |
| High quality weapon sounds | [nosave] MRIntW_HQSounds | No | Use less compressed sounds |
| Weapon switch sound | [nosave] MRIntW_SwitchSounds | No | Play sounds during weapon switch animations |
| Chaingun custom firing sound | [nosave] MRIntW_ChaingunSound | No | Chaingun will use unique sound instead of pistol's |

### Настройки --> Configure Interpolated weapons --> Ui settings
| Setting name | [CVar type] CVar | Default | Description |
| --- | --- | --- | --- |
| Smooth menus | [nosave] MRIntW_SmoothUi | Yes | Uncaps framerate in menu, smooths scrolling and some elements |
| Smooth menu transitions | [nosave] MRIntW_SmoothUiTransitions | For all | Adds smooth transitions between menus |
| Animated logo | [nosave] MRIntW_SmoothUiLogo | Yes | Adds animations to M_Doom |
| Animated options | [nosave] MRIntW_SmoothUiOptions | Yes | Adds special animations for submenus |



## Credits
(Original credits.txt file can be found in Mod info folder)
* Sprites
	* Fist - id Software, Perkristian, some frames were taken from Charlie reskin pack for Hideous Destructor
	* Chainsaw - id Software, JoeyTD, Agent_Ash (chain animation, which was taken from Beautiful Doom)
	* Pistol - id Software, Perkristian (some frames were taken from ZScript version of Smooth Doom)
	* Shotgun - id Software, Perkristian
	* Super Shotgun - id Software, Perkristian
	* Chaingun - based on spirtes from Doom by id Software and Smooth Doom by Perkristian
	* Rocket Launcher - id Software, Perkristian
	* PlasmaGun (Plasma Rifle) - based on spirtes from Doom id Software and Smooth Doom by Perkristian
	* BFG 9000 - id Software
	* Rifle - id Software, DrPyspy
	* Casings - id Software
	* Lowres casings - based on sprites from Hideous Destructor
* Sounds
	* Fist whoosh sound - id Software
	* Gloves takin on/off - based on sounds from The Soldier Z mod
	* Fist hitting wall sound - based on sounds from Beautiful Doom mod
	* Weapon dropping - based on sounds from The Soldier Z mod
* Inspiration
	* Smooth Doom mod
	* Beautiful Doom mod
	* Hideous destructor mod
	* SmoothBlood mod
	* Doom Delta mod
	* Doom Deluxe mod
	* Bioshock
	* Bioshock Infinite
	* Doom 2016
	* Half Life 1-2
	* Power Slave
	* Quake 1, 2, 4
	* Unreal Tournament 3
	* Star Wars Battlefront 2015
	* Soldier of Fortune
	* Blood
	* Doom 3
	* Doom Retro
	* Black Lagoon anime series
	* Killer Bean Forever
	* C&Rsenal youtube channel (and C&Rsenal rus)
	* Импакт шутера - Kefir succerland на youtube
	* DOOM's pistol is kinda LAME... but it doesn't have to be! - Doomkid on youtube
	* Doom 2's Super Shotgun Graphics Are JANK - BeefGee on youtube
	* Squoosh app
* Special thanks
	* Patis
	* RastamanGames
	* JSO_X
	* El_Donte
	* Dingus
	* Shark Bite
	* Linok_Games
	* NomakhThunder and his community
	* Hideous Destructor community
	* Russian Doom Community on discord
	* Thanks to the people from these telegram chats for criticism and ideas for the mod:
		* Delta touch 2.0
		* ENDOOM Community

## For other modders
Feel free check this mod's files, use its assets or code. Although it will be great if you credit me or other authors.

If you want to work with this mod, or add something to it, check the Mod info folder and TexturexEditing!.txt file
***
## $\color{#FF0000}{Give\ me\ the\ damn\ download\ you\ nerd}$

[Version for GZDoom 4.14.2-UZDoom 4.14.3](https://github.com/mickromash/InterpolatedWeapons/archive/refs/heads/4.14.2.zip)

[Version for UZDoom 5.0+](https://github.com/mickromash/InterpolatedWeapons/archive/refs/heads/5.0+.zip)
