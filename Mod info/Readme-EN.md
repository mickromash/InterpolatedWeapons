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
* [Download mod](#ColorFF0000Give-me-the-damn-donwload-you-nerd)
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
| Weapon bob when firing | [nosave] MRIntW_ChangeFiringBob | 1 | Amount of weapon bob during firing. |

### Options  --> Configure Interpolated weapons --> Animations settings
| Setting name | [CVar type] CVar | Default | Description |
| --- | --- | --- | --- |
| Цвет перчаток | [user] MRIntW_GlovesColor | Классический | Цвет перчаток игрока на спрайтах оружия |
| Тёмные участки | [user] MRIntW_GlovesColorShade | 2 2 2 | Если для цвета перчаток выбран пункт "Свой", цветом перчаток будет градиент из MRIntW_GlovesColorShade и MRIntW_GlovesColorLight. Рекомендую давать MRIntW_GlovesColorShade максимально тёмные значения |
| Светлые участки | [user] MRIntW_GlovesColorLight | EF EF EF | Главным образом на оттенок перчаток влияет именно этот цвет |
| Анимации подбора и перезарядки | [nosave] MRIntW_ReloadAnims | Только перезарядки | Если на оружии кончаются патроны, или при первом его подборе, будет проигрываться альтернативная анимация выбора |
| Отключить дульные вспышки | [nosave] MRIntW_NoMuzzleFlash | No | Отключает анимации дульных вспышек при стрельбе. Надо бы добавить Doom Retro в кредитсы... |
| Свечение от дульных вспышек | [nosave] MRIntW_FlashFlare | No | Ореолы вокруг дульных вспышек, типа блума |
| Рандомизировать кастомизацию на старте игры | [user] MRIntW_RandomStart | No | При старте новой игры, для отдельных элементов будут использоваться случанйые значения, вместо настроек игрока. Сохранённые настройки игрока в меню от этого не меняются |
| Без названия | [nosave] MRIntW_RandomDemo | Yes | Применить рандомизацию предыдущей настройки к проигрываемым демо записям |

### Options --> Configure Interpolated weapons --> Настройки анимаций --> Общие настройки оружия
| Setting name | [CVar type] CVar | Default | Description |
| --- | --- | --- | --- |
| Покачивание оружия | [nosave] MRIntW_BobStyle | Плавное | Стиль покачивания оружия в руках во время ходьбы |
| Радиус по горизонтали | [nosave] MRIntW_BobRangeX | 1 | Насколько сильно оружие будет раскачиваться по горизонтали |
| Радиус по вертикали | [nosave] MRIntW_BobRangeY | 1 | Насколько сильно оружие будет раскачиваться по вертикали |
| Радиус глубины | [nosave] MRIntW_BobRangeZ | 0 | Насколько сильно оружие будет раскачиваться вглубь (взад-вперёд). Вдохновленно Rise of The Triad. Не работает с пулемётом, плазмаганом и бфг из-за сложности реализации |
| Покачивание при стрельбе из оригинального (DOS) DOOM | [nosave] MRIntW_VanillaFireBob | No | Во время выстрела оружие будет замирать на месте, но не перемещаясь при этом в центр экрана |
| Анимации смены | [nosave] MRIntW_SwitchAnims | Случайные вариации | Анимации которые будут проигрываться при смене одного оружия на другое |
| Подпрыгивание оружия при приземлении | [nosave] MRIntW_Bounce | Обычное | Иммерсивное движение оружия в воздухе и при приземлении |
| Кнопка бега | [nosave] MRIntW_RunKey | Ничего не делает | Опускает оружие - при нажатии кнопки бега оружие будет опускаться вниз экрана; Поднимает оружие - оружие всегда находится внизу экрана и поднимается при нажатии кнопки бега |
| Инерция рук | [nosave] MRIntW_WeaponSway | No | Так называемый weapon sway - отставание оружия от камеры, и более правдоподобное его движение |
| Стиль инерции рук | [nosave] MRIntW_WeaponSwayStyle | Battlefront 2015 | Half Life 2 - оружие отстаёт от камеры, при остановке движения остаётся на месте, при стрельбе возвращается в центр экрана; Battlefront 2015 - в зависимости от типа и габаритов оружия, оно отстаёт или движется в направлении камеры и наклоняется. При остановке движения камеры, оружие возвращается в центр экрана с `wobble` эффектом |
| Анимации покоя | [nosave] MRIntW_IdleAnims | Yes | Анимация дыхания, покачивания оружия и т.п. при бездействии. У отдельных видов оружия есть уникальные анимации покоя (также на кнопки альт. атаки и перезарядки оружия проигрывает более выраженные анимации) |
| Тряска рук при получении урона | [nosave] MRIntW_DamageShake | Yes | Быстрая встряска рук при получении урона на подобии Doom (2016). Сила тряски зависит от количества полученного урона |
| Тряска рук при низком здоровье | [nosave] MRIntW_LowHealthShake | No | Если здоровье игрока опускается ниже 25, руки с оружием будут трястись (аналогично тряске при берсерке) |
| Положение оружия | [nosave] MRIntW_BaseOffset | No | Позволяет переместить оружие из центра экрана |
| По горизонтали | [nosave] MRIntW_BaseOffsetX | 0 | Положение оружия по оси X |
| По вертикали | [nosave] MRIntW_BaseOffsetY | 0 | Положение оружия по оси Y (инвертировано) |

### Options --> Configure Interpolated weapons --> Настройки анимаций --> Настроить каждое оружие
**Кулаки**
| Setting name | [CVar type] CVar | Default | Description |
| --- | --- | --- | --- |
| Сменить основную руку | [user] MRIntW_RightPunch | No | Меняет руку с кастетом |
| Тряска рук при берсерке | [user] MRIntW_BersShake | Только без оружия | При подборе берсерка руки игрока будет трясти, а на экране добавится рука с кастетом. |
| Снимать перчатки | [user] MRIntW_BareHands | Yes | Использовать спрайты без перчаток для анимаций кулаков. |
| Анимация снятия перчаток | [user] MRIntW_GlovesStrip | Yes | При выборе кулаков будет проигрываться анимация снятия перчаток (если включена опция выше) |
| Всегда показывать второй кулак | [user] MRIntW_SecondFist | No | На экране всегда будет видна рука с кастетом без необходимости подбирать берсерк |
| Бьющая рука | [user] MRIntW_PunchingFist | Основная | Выбор каким кулаком будет бить игрок |
| Добивающий удар | [user] MRIntW_FinishPunch | Только с берсерком | Альтернативная анимация удара при убийстве цели |
| Анимация промаха | [user] MRIntW_MissPunch | No | Проигрывание анимации добивающего удара при промахе 
| Шанс добивающего удара | [user] MRIntW_FinishPunchChance | 0.7 | Вероятность проигрывания анимации добивающего удара |
| Отдача при ударе стены с берсерком | [user] MRIntW_SurfacePunchRecoil | No | При ударе геометрии уровня (стены/пол/потолок) после подбора берсерка, игрока будет отталкивать в противоположную сторону |
| Фиксировать кулак на ударенном монстре | [nosave] MRIntW_FistFixedOnTarget | No | При попадании по актору, спрайт кулака будет фиксироваться на нём, игнорируя поворот камеры игрока |

**Бензопила**
| Setting name | [CVar type] CVar | Default | Description |
| --- | --- | --- | --- |
| Анимация включения | [user] MRIntW_ChainsawStart | No | Альтернативная анимация выбора пилы |
| Улучшенная анимация распиливания | [user] MRIntW_ChainsawCutting | Yes | При атаке пилой будут проигрываться процедурные анимации распиливания под разными углами и с разной скоростью |
| Тряска бензопилы при распиливании поверхностей | [user] MRIntW_ChainsawCuttingWall | Yes | При распиливании геометрии уровня (стены/пол/потолок), бензопилу будет трясти |
| Дым от пилы | [nosave] MRIntW_ChainsawSmoke | Yes | Таки да, в моде пила работает на бензине |
| Кровь на пиле | [nosave] MRIntW_ChainsawBlood | No | От распиливания врагов и жидкостей на пиле будет оставаться кровь (или жидкости) |
| Капающая кровь | [nosave] MRIntW_ChainsawBlood | No | Капли от крови и прочих жидкостей на пиле |
| Время до исчезновения (в секундах) | [nosave] MRIntW_ChainsawBloodLife | 60 | Через сколько секунд кровь на пиле начнёт пропадать |

**Пистолет**
| Setting name | [CVar type] CVar | Default | Description |
| --- | --- | --- | --- |
| Держать пистолет в левой руке | [user] MRIntW_LHand | Yes | Каноничный думгай левша |
| Держать пистолет двумя руками | [user] MRIntW_PistolSHand | Если враг далеко | В зависимости от значения, при стрельбе в далеко стоящую цель игрок будет брать пистолет в две руки, убирать вторую руку при стрельбе на близкой дистанции, или всегда держать пистолет двумя руками |
| Заменить пистолет на винтовку | [user] MRIntW_Rifle | No | Визуальная замена пистолета на винтовку из ранних версий Doom |

**Дробовик**
| Setting name | [CVar type] CVar | Default | Description |
| --- | --- | --- | --- |
| Дым из патронника | [nosave] MRIntW_ShotgunSmoke | Yes | Анимация дыма при передёргивании помпы |
| Искры при выстреле | [nosave] MRIntW_ShotgunSparks | No | Искры вылетающие из ствола при выстреле |
| Наклон во время перезарядки | [user] MRIntW_ShotgunPumpAngle | 0 | Наклон спрайта дробовика во время передёргивания помпы |
| Случайный наклон | [user] MRIntW_ShotgunPumpRandom | No | Выбирать случайный наклон спрайта для каждого передёргивания |
| Диапазон случайного наклона | [user] MRIntW_ShotgunPumpRandRotation | 1 | Максимальное число которое может быть добавлено к наклону спрайта |
| Сила анимации отдачи дробовиков | [nosave] MRIntW_ShotgunsRecoil | 1 | Насколько сильно спрайт дробовика и двустволки увеличивается и опускается при выстреле |

**Двустволка**
| Setting name | [CVar type] CVar | Default | Description |
| --- | --- | --- | --- |
| Держать цевьё во время перезарядки | [user] MRIntW_SSGHandless | Всегда | Более логичная анимация перезарядки при которой игрок убирает руку с цевья во время открытия двустволки, чтобы взять патроны |
| Дым из казённика | [nosave] MRIntW_SSGSmoke | Yes | Дым из стволов после их открытия |
| Искры при выстреле | [nosave] MRIntW_SSGSparks | No | Искры вылетающие из ствола при выстреле |
| Сила анимации отдачи дробовиков | [nosave] MRIntW_ShotgunsRecoil | 1 | Насколько сильно спрайт дробовика и двустволки увеличивается и опускается при выстреле |

**Пулемёт**
| Setting name | [CVar type] CVar | Default | Description |
| --- | --- | --- | --- |
| Фиксированное положение стволов | [user] MRIntW_ChaingunFixed | No | По окончании стрельбы стволы будут возвращаться в исходное положение |
| Скорость вращения | [user] MRIntW_ChaingunSpeed | 1 | Не влияет на геймплей (как и почти все перечисленные опции) |
| Сила торможения | [user] MRIntW_ChaingunStopTime | .3 | Как быстро стволы перестают вращаться |
| Вращать стволы против часовой | [user] MRIntW_ChaingunCounterClock | No | Много кастомизации не бывает |
| Макс. дымящихся стволов | [nosave] MRIntW_ChaingunMaxSmokes | 3 | Попытка оптимизировать струящийся дым для пулемёта. Помимо этого, длина дыма для пулемёта делиться на количество дымящихся стволов |

**Ракетомёт**
| Setting name | [CVar type] CVar | Default | Description |
| --- | --- | --- | --- |
| Дым из дула | [nosave] MRIntW_RocketSmoke | 1 | Сила струящегося дыма для ракетомёта |

**Плазмаган**
| Setting name | [CVar type] CVar | Default | Description |
| --- | --- | --- | --- |
| Частицы при стрельбе | [nosave] MRIntW_PlasmaParticles | Только свечение | Красивое |
| Снаряды излучают динамический свет | [nosave] MRIntW_PlasmaLight | Yes | Динамическое освещение для снарядов плазмагана |
| Только каждый второй снаряд излучает свет | [nosave] MRIntW_PlasmaSkipLight | No | При стрельбе очередями, каждый второй выстрел не будет излучать динамический свет |

**BFG**
| Setting name | [CVar type] CVar | Default | Description |
| --- | --- | --- | --- |
| Частицы при стрельбе | [nosave] MRIntW_BFGParticles | Yes | Делает анимацию выстрела в разы интересней |


### Options --> Configure Interpolated weapons --> Настройки частиц
| Setting name | [CVar type] CVar | Default | Description |
| --- | --- | --- | --- |
| Гильзы | [nosave] MRIntW_Casings | Только анимация | Включает гильзы для огнестрельного оружия |
| Макс. скорость гильз | [user] MRIntW_CasingsRandom | 1 | С какой силой гильзы экстрагируются из оружия |
| Громкость отскока гильз | [nosave] MRIntW_CasingsVolume | 1 | Забавный факт: звук сообщения о загрузке сохранения сделанного со старой версией мода, сделан из звуков отскока гильзы дробовика |
| Макс. количество гильз | [nosave] MRIntW_CasingsAmount | 300 | Если количество гильз превысит это значение, старые гильзы начнут пропадать |
| Оптимизировать скопления гильз | [nosave] MRIntW_CasingsClusteringReduce | Yes | Предотвращает больше скопление гильз в одной куче |
| Низкая детализация гильз | [nosave] MRIntW_CasingsLowRes | No | Альтернативные спрайты для гильз в более низком разрешении (схожи с гильзами из Hideous Destructor) |
| Клубы дыма от выстрелов | [nosave] MRIntW_Smoke | Yes | На текстуру этого дыма не влияет настройка текстуры обычного дыма на базе частиц |
| Струящийся дым | [nosave] MRIntW_FlowingSmoke | No | Дым от продолжительной стрельбы, на подобии того что был в играх серии Bioshock |
| Длина струящегося дыма | [nosave] MRIntW_FlowingSmokeLength | 0.6 | При значения ниже 0.6 могут появляться разрывы в струях дыма |
| Непрозрачность струящегося дыма | [nosave] MRIntW_FlowingSmokeAlpha | 0.2 | Насколько заметен дым |
| Макс. время дыма | [nosave] MRIntW_FlowingSmokeMaxTime | 1 | Насколько долго дым продолжает идти из ствола |
| Количество частиц в дыме | [nosave] MRIntW_FlowingSmokePrecision | 1 | Струи дыма сделаны из множества круглых (или не круглых, в зависимости от ваших настроек) частиц. Данная настройка регулирует плотность этих частиц. Более низкие значения улучшат производительность, но отдельные частицы станут более заметны |
| Экспериментальная текстура струящегося дыма | [nosave] MRIntW_FlowingSmokeBioTexture | No | Более детализированный струящийся дым, больше похожий на тот что был в Bioshock. Работает не идеально |
| Задымление помещений | [nosave] MRIntW_LongTermSmoke | No | Довольно экспериментальная функция. Включает постепенное появление большых облаков дыма при стрельбе в одном месте, которые после долго рассеиваются |
| Текстура частиц | [nosave] MRIntW_ParticleTexture | Такая же как у остальных частиц | Эффекты в моде, которые включаются ниже в данном меню, используют данную настройку для выбора внешнего вида частиц. "Такая же как у остальных частиц" означает что будет использоваться текстура частиц выбранная в настройках дисплея вашего сорс порта |
| Текстура частиц дыма | [nosave] MRIntW_ParticleSmokeTexture | Плавная | Данная настройка также распространяется только на эффекты ниже, но затрагивает только частицы дыма, на случай если текстура выбранная выше конкретно дыму может не подойти |
| Эффекты оружия игрока | [nosave] MRIntW_PlayerParticles | No | Включает эффекты для снарядов игрока, а также для всех буллет пафов (искры от попаданий по геометрии уровня).
| Качество эффектов оружия игрока | [nosave] MRIntW_PlayerParticlesAmount | 1 | Количество частиц в эффектах игрока. Я на GTX970 и Intel Core i7 3770 ставлю все настройки частиц кроме декораций на х2 |
| Выбранные эффекты оружия игрока | [nosave] MRIntW_PlayerWhichParticles | 134021019 | Все выбранные эффекты игрока хранятся в одном КВаре в формате флагов |
| Эффекты монстров | [nosave] MRIntW_MonsterParticles | No | Включает эффекты для снарядов монстров и для них самих |
| Качество эффектов монстров | [nosave] MRIntW_MonsterParticlesAmount | 1 | Количество частиц в эффектах монстров. На картах с большим количеством врагов может потребоваться снизить значение данной настройки |
| Выбранные эффекты монстров | [nosave] MRIntW_MonsterWhichParticles и [nosave] MRIntW_MonsterWhichParticles2 | -33 и -2147483617 | Аналогично эффектам игрока, эффекты монстров хранятся в виде флагов, но из-за их количества пришлось использовать две переменные |
| Применять эффекты к монстрам из модов | [nosave] MRIntW_MonsterParticlesCustom | No | Если данная опция не включена, эффекты из мода будут работать только с монстрами и снарядами из Doom |
| Мухи над трупами | [nosave] MRIntW_ParticleFlies | No | Мухи летающие над трупами в стиле Quake 2 |
| Громкость жужжания | [nosave] MRIntW_ParticleFliesVolume | 0.4 | Он точно будет кого-то бесить |
| Альт. визуализация молний | [nosave] MRIntW_AltLightnings | No | По умолчанию молнии в эффектах будут моментально появляться и медленно исчезать. С данной настройкой молнии будут "вырастать", а после пропадать с эффектом расщепления |
| Эффекты декораций | [nosave] MRIntW_DecorationParticles | No | Включает эффекты для декораций. Помимо прочего добавляет ореолы на подобии блума для светящихся объектов |
| Качество эффектов декораций | [nosave] MRIntW_DecorationParticlesAmount | 1 | Количество частиц в эффектах декораций |
| Выбранные эффекты декораций | [nosave] MRIntW_DecorationWhichParticles | 511 | То же самое что и с эффектами игрока и монстров |
| Эффект телепортации | [nosave] MRIntW_TeleportParticles | No | Включает эффекты на базе частиц для телепортации |
| Стиль телепортации | [nosave] MRIntW_TeleportParticlesStyle | Волна | Доступны варианты: 2 кольца, Взрыв, Испарение, Обратный взрыв, Двойное испарение, Странное облако, Волна |
| Стиль телепортации монстра | [nosave] MRIntW_TeleportParticlesStyleMonsters | Испарение | Тоже самое, но для телепортации монстров |
| Эффект возрождения предметов | [nosave] MRIntW_RespawnParticles | No | Эффект респавна предметов. |

### Options --> Configure Interpolated weapons --> Настройки звуков
| Setting name | [CVar type] CVar | Default | Description |
| --- | --- | --- | --- |
| Громкость отскока гильз | [nosave] MRIntW_CasingsVolume | 1 | Дубликат настройки громкости гильз из меню частиц |
| Громкость работы пилы | [nosave] MRIntW_ChainsawVolume | 1 | Кому-то он может надоедать |
| Рандомизация высоты звука пилы | [nosave] MRIntW_ChainsawRandomPitch | 0 | Добавляет вариативность звуку работы пилы |
| Громкость альт. атаки BFG | [nosave] MRIntW_BFGAltVolume | .6 | Громкость гудения BFG во время проигрывания анимации на ПКМ |
| Звуки оружия высокого качества | [nosave] MRIntW_HQSounds | No | Использовать не сжатые звуки для оружия |
| Звуки смены оружия | [nosave] MRIntW_SwitchSounds | No | Проигрывать звуки при доставании и убирании оружия |
| Звуки пулемёта из аддона | [nosave] MRIntW_ChaingunSound | No | Проигрывать кастомный звук стрельбы для пулемёта, вместо звука выстрела пистолета |

### Настройки --> Настроить интерполированное оружие --> Настройки интерфейса
| Setting name | [CVar type] CVar | Default | Description |
| --- | --- | --- | --- |
| Плавное меню | [nosave] MRIntW_SmoothUi | Yes | Отключает ограничение на фпс в меню, сглаживает его прокрутку и отдельные элементы |
| Плавные переходы в меню | [nosave] MRIntW_SmoothUiTransitions | Везде | Добавляет анимацию перехода от одного меню к другому |
| Анимированный логотип | [nosave] MRIntW_SmoothUiLogo | Yes | Добавляет анимации для лого в меню. |



## Credits
(Оригинальный файл credits.txt с указанием всех чужих работ есть в папке Mod info)
* Спрайты
     * Кулаки - id Software, Perkristian, отдельные кадры были взяты из Charlie reskin pack для Hideous Destructor
     * Бензопила - id Software, JoeyTD, Agent_Ash (анимация цепи была взята из его Beautiful Doom)
     * Пистолет - id Software, Perkristian (отдельные кадры были взяты из Smooth Doom ZScript Edition)
     * Дробовик - id Software, Perkristian
     * Супердробовик - id Software, Perkristian
     * Пулемёт - основаны на спрайтах из Doom от id Software и Smooth Doom от Perkristian
     * Ракетница - id Software, Perkristian
     * Плазмаган - основан на спрайтах из Doom от id Software и Smooth Doom от Perkristian
     * BFG 9000 - id Software
     * Винтовка - id Software, DrPyspy
     * Гильзы - id Software
     * Пиксельные гильзы - основаны на спрайтах из Hideous Destructor
* Звуки
     * Звук взмаха кулаком - id Software
     * Звуки снятия/надевания перчаток основаны на звуках из The Soldier Z
     * Звуки удара оружия об пол основаны на звуках из The Soldier Z
* Мод вдохновлён
     * Smooth Doom
     * Beautiful Doom
     * Hideous destructor
     * SmoothBlood
     * Doom Delta
     * Doom Deluxe
     * Bioshock
     * Bioshock Infinite
     * Doom 2016
     * Half Life 1-2
     * Power Slave
     * Quake 1, 2, 4
     * Unreal Tournament 3
     * Star Wars Battlefront 2015
     * Soldier of Fortune
     * Doom 3
     * Doom Retro
     * Аниме Black Lagoon
     * Killer Bean Forever
     * Видео с youtube канала C&Rsenal (а точнее переводами с канала C&Rsenal rus)
     * Импакт шутера - Kefir succerland на youtube
     * DOOM's pistol is kinda LAME... but it doesn't have to be! - Doomkid на youtube
     * Doom 2's Super Shotgun Graphics Are JANK - BeefGee на youtube
* Отдельная благодарность
     * Patis
     * RastamanGames
     * JSO_X
     * El_Donte
     * Dingus
     * Shark Bite
     * Linok_Games
     * NomakhThunder и его подписчикам
     * Сообществу Hideous Destructor
     * Russian Doom Community в discord
     * Спасибо людям из этих тг чатов за критику и идеи для мода:
        * Delta touch 2.0
        * ENDOOM Community

## For other modders
Никому ничего не запрещаю, код можно смотреть, копировать и использовать в своих работах, как и ассеты мода (хотя я сомневаюсь, что это нечто кто-то будет использовать), но в кредитсах по возможности прошу указывать.  

При работе с модом обратите внимание на папку Mod info и на файл TexturexEditing!.txt, в последнем указаны все спрайты к которым нужно применение NoTrim - такой же список должен находится в основном файле
Textures.txt, который ничего кроме этого списка не должен в себе содержать, ибо при сохранении этого файла в режиме фоторедактора, все строки NoTrim из него удаляются.
***
## $\color{#FF0000}{Дай\ уже\ скачать\ мод\ долбаный\ задрот}$

На вот на вот https://github.com/mickromash/InterpolatedWeapons/archive/refs/heads/main.zip
