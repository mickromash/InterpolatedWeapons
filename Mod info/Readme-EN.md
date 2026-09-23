# Fluid Weapons (a.k.a. Interpolated Weapons)
UZDoom weapon mod with interpolated weapon animations, particle effects and more.


***
**Contents**
* [Requirements](#Mod-requirements)
* [Compatibility](#Compatibility)
* [Features](#Mod-features)
* [Mod settings (CVars) list](#Mod-settings-CVars)
   * [Main settings](#Settings----Configure-Interpolated-weapons)
     * [Main animations settings](#Settings----Configure-Interpolated-weapons----Animations-settings)
       * [General weapon settings](  #Settings----Configure-Interpolated-weapons----Animations-settings----General-weapon-settings)
       * [Weapons customization](#Settings----Configure-Interpolated-weapons----Animations-settings----Customize-weapons)
   * [Particles](#Settings----Configure-Interpolated-weapons----Particles-settings)
   * [Sound](#Settings----Configure-Interpolated-weapons----Sound-settings)
   * [UI](#Settings----Configure-Interpolated-weapons----UI-settings)
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


* В моде есть простая анимация смерти игрока, при которой он теряет оружие. Оружие сделано в качестве вижуал финкера и отображается только для погибшего игрока.
* Плавные анимации в меню

## Mod settings (CVars)

* Все КВары и комманды мода можно посмотреть в консоли введя `MRIntW` и нажав [TAB]
* Типы КВаров:
   * server - эти настройки влияют на всех игроков (пример: ускоренная стрельба пистолета работает для всех игроков)
   * user - персонализированные настройки для каждого игрока, но их влияние так же заметно для других игроков (пример: у каждого игрока свой цвет перчаток, но другие игроки будут видеть на вас перчатки именно вашего цвета)
   * nosave - эти настройки полностью персонализированы для каждого игрока, и никак не влияют на игру других. Также nosave КВары можно менять во время проигрывания демок (пример: включение эффектов на компьютере одного из игроков никак не сказывается на внешнем виде и производительности игры других игроков)

### Настройки --> Настроить интерполированное оружие
| Название | [тип квара] CVar | По умолчанию | Что делает |
| --- | --- | --- | --- |
| Исправить освещение оружия | [server] MRIntW_Lighting | Да | Исправляет динамическое освещение от оружия. По сути отключать не имеет смысла |
| Реалистичное привлечение внимания монстров | [server] MRintW_BetterAlert | Нет | Делает реагирование монстров на звуки игрока более логичным. Монстры не реагируют на удары кулаками по воздуху, и реагируют на работающую пилу |
| Визуальная отдача | [user] MRIntW_Recoil | Нет | Атаки оружия будут поднимать камеру игрока и автоматически её опускать |
| Сила отдачи | [user] MRIntW_RecoilAmount | 1 | Честно не помню |
| Компенсация отдачи | [user] MRIntW_RecoilRecover | 1 | Насколько быстро камера возвращается в исходное положение |
| Тряска экрана | [nosave] MRIntW_ScreenShake | Нет | Тряска экрана при выстрелах, взрывах и т.п. |
| Сила тряски экрана | [nosave] MRIntW_ScreenShakeAmount | 1 | Ну типа это то насколько сильно будет наклоняться экран при тряске воот |
| Убрать задержку перед выстрелом | [user] MRIntW_InstantFire | Да | Убирает задержку перед выстрелом (инпутлаг) для пистолета, дробовиков и ракетницы. Чтобы не изменять скорость стрельбы, задержка переносится на стейты после выстрела |
| Скорострельный пистолет | [server] MRIntW_FastPistol | Нет | Просто увеличивает скорострельность пистолета, делая его менее бесполезным. Надо бы добавить видос думкида в кредитсы |
| Комбинирование оружия | [server] MRIntW_QuickSwitch | Нет | Возможность сменить оружия во время анимаций перезарядки и им подобным (работает с дробовиком, двустволкой и плазмаганом) |
| Форсировать раскачивание при стрельбе | [nosave] MRIntW_ChangeFiringBob | Да | При заходе в игру настройке раскачивания оружия при стрельбе выдаётся значение 1. Настройка находится в Настройки --> Интерфейс |

### Настройки  --> Настроить интерполированное оружие --> Настройки анимаций
| Название | [тип квара] CVar | По умолчанию | Что делает |
| --- | --- | --- | --- |
| Цвет перчаток | [user] MRIntW_GlovesColor | Классический | Цвет перчаток игрока на спрайтах оружия |
| Тёмные участки | [user] MRIntW_GlovesColorShade | 2 2 2 | Если для цвета перчаток выбран пункт "Свой", цветом перчаток будет градиент из MRIntW_GlovesColorShade и MRIntW_GlovesColorLight. Рекомендую давать MRIntW_GlovesColorShade максимально тёмные значения |
| Светлые участки | [user] MRIntW_GlovesColorLight | EF EF EF | Главным образом на оттенок перчаток влияет именно этот цвет |
| Анимации подбора и перезарядки | [nosave] MRIntW_ReloadAnims | Только перезарядки | Если на оружии кончаются патроны, или при первом его подборе, будет проигрываться альтернативная анимация выбора |
| Отключить дульные вспышки | [nosave] MRIntW_NoMuzzleFlash | Нет | Отключает анимации дульных вспышек при стрельбе. Надо бы добавить Doom Retro в кредитсы... |
| Свечение от дульных вспышек | [nosave] MRIntW_FlashFlare | Нет | Ореолы вокруг дульных вспышек, типа блума |
| Рандомизировать кастомизацию на старте игры | [user] MRIntW_RandomStart | Нет | При старте новой игры, для отдельных элементов будут использоваться случанйые значения, вместо настроек игрока. Сохранённые настройки игрока в меню от этого не меняются |
| Без названия | [nosave] MRIntW_RandomDemo | Да | Применить рандомизацию предыдущей настройки к проигрываемым демо записям |

### Настройки --> Настроить интерполированное оружие --> Настройки анимаций --> Общие настройки оружия
| Название | [тип квара] CVar | По умолчанию | Что делает |
| --- | --- | --- | --- |
| Покачивание оружия | [nosave] MRIntW_BobStyle | Плавное | Стиль покачивания оружия в руках во время ходьбы |
| Радиус по горизонтали | [nosave] MRIntW_BobRangeX | 1 | Насколько сильно оружие будет раскачиваться по горизонтали |
| Радиус по вертикали | [nosave] MRIntW_BobRangeY | 1 | Насколько сильно оружие будет раскачиваться по вертикали |
| Радиус глубины | [nosave] MRIntW_BobRangeZ | 0 | Насколько сильно оружие будет раскачиваться вглубь (взад-вперёд). Вдохновленно Rise of The Triad. Не работает с пулемётом, плазмаганом и бфг из-за сложности реализации |
| Покачивание при стрельбе из оригинального (DOS) DOOM | [nosave] MRIntW_VanillaFireBob | Нет | Во время выстрела оружие будет замирать на месте, но не перемещаясь при этом в центр экрана |
| Анимации смены | [nosave] MRIntW_SwitchAnims | Случайные вариации | Анимации которые будут проигрываться при смене одного оружия на другое |
| Подпрыгивание оружия при приземлении | [nosave] MRIntW_Bounce | Обычное | Иммерсивное движение оружия в воздухе и при приземлении |
| Кнопка бега | [nosave] MRIntW_RunKey | Ничего не делает | Опускает оружие - при нажатии кнопки бега оружие будет опускаться вниз экрана; Поднимает оружие - оружие всегда находится внизу экрана и поднимается при нажатии кнопки бега |
| Инерция рук | [nosave] MRIntW_WeaponSway | Нет | Так называемый weapon sway - отставание оружия от камеры, и более правдоподобное его движение |
| Стиль инерции рук | [nosave] MRIntW_WeaponSwayStyle | Battlefront 2015 | Half Life 2 - оружие отстаёт от камеры, при остановке движения остаётся на месте, при стрельбе возвращается в центр экрана; Battlefront 2015 - в зависимости от типа и габаритов оружия, оно отстаёт или движется в направлении камеры и наклоняется. При остановке движения камеры, оружие возвращается в центр экрана с `wobble` эффектом |
| Анимации покоя | [nosave] MRIntW_IdleAnims | Да | Анимация дыхания, покачивания оружия и т.п. при бездействии. У отдельных видов оружия есть уникальные анимации покоя (также на кнопки альт. атаки и перезарядки оружия проигрывает более выраженные анимации) |
| Тряска рук при получении урона | [nosave] MRIntW_DamageShake | Да | Быстрая встряска рук при получении урона на подобии Doom (2016). Сила тряски зависит от количества полученного урона |
| Тряска рук при низком здоровье | [nosave] MRIntW_LowHealthShake | Нет | Если здоровье игрока опускается ниже 25, руки с оружием будут трястись (аналогично тряске при берсерке) |
| Положение оружия | [nosave] MRIntW_BaseOffset | Нет | Позволяет переместить оружие из центра экрана |
| По горизонтали | [nosave] MRIntW_BaseOffsetX | 0 | Положение оружия по оси X |
| По вертикали | [nosave] MRIntW_BaseOffsetY | 0 | Положение оружия по оси Y (инвертировано) |

### Настройки --> Настроить интерполированное оружие --> Настройки анимаций --> Настроить каждое оружие
**Кулаки**
| Название | [тип квара] CVar | По умолчанию | Что делает |
| --- | --- | --- | --- |
| Сменить основную руку | [user] MRIntW_RightPunch | Нет | Меняет руку с кастетом |
| Тряска рук при берсерке | [user] MRIntW_BersShake | Только без оружия | При подборе берсерка руки игрока будет трясти, а на экране добавится рука с кастетом. |
| Снимать перчатки | [user] MRIntW_BareHands | Да | Использовать спрайты без перчаток для анимаций кулаков. |
| Анимация снятия перчаток | [user] MRIntW_GlovesStrip | Да | При выборе кулаков будет проигрываться анимация снятия перчаток (если включена опция выше) |
| Всегда показывать второй кулак | [user] MRIntW_SecondFist | Нет | На экране всегда будет видна рука с кастетом без необходимости подбирать берсерк |
| Бьющая рука | [user] MRIntW_PunchingFist | Основная | Выбор каким кулаком будет бить игрок |
| Добивающий удар | [user] MRIntW_FinishPunch | Только с берсерком | Альтернативная анимация удара при убийстве цели |
| Анимация промаха | [user] MRIntW_MissPunch | Нет | Проигрывание анимации добивающего удара при промахе 
| Шанс добивающего удара | [user] MRIntW_FinishPunchChance | 0.7 | Вероятность проигрывания анимации добивающего удара |
| Отдача при ударе стены с берсерком | [user] MRIntW_SurfacePunchRecoil | Нет | При ударе геометрии уровня (стены/пол/потолок) после подбора берсерка, игрока будет отталкивать в противоположную сторону |
| Фиксировать кулак на ударенном монстре | [nosave] MRIntW_FistFixedOnTarget | Нет | При попадании по актору, спрайт кулака будет фиксироваться на нём, игнорируя поворот камеры игрока |

**Бензопила**
| Название | [тип квара] CVar | По умолчанию | Что делает |
| --- | --- | --- | --- |
| Анимация включения | [user] MRIntW_ChainsawStart | Нет | Альтернативная анимация выбора пилы |
| Улучшенная анимация распиливания | [user] MRIntW_ChainsawCutting | Да | При атаке пилой будут проигрываться процедурные анимации распиливания под разными углами и с разной скоростью |
| Тряска бензопилы при распиливании поверхностей | [user] MRIntW_ChainsawCuttingWall | Да | При распиливании геометрии уровня (стены/пол/потолок), бензопилу будет трясти |
| Дым от пилы | [nosave] MRIntW_ChainsawSmoke | Да | Таки да, в моде пила работает на бензине |
| Кровь на пиле | [nosave] MRIntW_ChainsawBlood | Нет | От распиливания врагов и жидкостей на пиле будет оставаться кровь (или жидкости) |
| Капающая кровь | [nosave] MRIntW_ChainsawBlood | Нет | Капли от крови и прочих жидкостей на пиле |
| Время до исчезновения (в секундах) | [nosave] MRIntW_ChainsawBloodLife | 60 | Через сколько секунд кровь на пиле начнёт пропадать |

**Пистолет**
| Название | [тип квара] CVar | По умолчанию | Что делает |
| --- | --- | --- | --- |
| Держать пистолет в левой руке | [user] MRIntW_LHand | Да | Каноничный думгай левша |
| Держать пистолет двумя руками | [user] MRIntW_PistolSHand | Если враг далеко | В зависимости от значения, при стрельбе в далеко стоящую цель игрок будет брать пистолет в две руки, убирать вторую руку при стрельбе на близкой дистанции, или всегда держать пистолет двумя руками |
| Заменить пистолет на винтовку | [user] MRIntW_Rifle | Нет | Визуальная замена пистолета на винтовку из ранних версий Doom |

**Дробовик**
| Название | [тип квара] CVar | По умолчанию | Что делает |
| --- | --- | --- | --- |
| Дым из патронника | [nosave] MRIntW_ShotgunSmoke | Да | Анимация дыма при передёргивании помпы |
| Искры при выстреле | [nosave] MRIntW_ShotgunSparks | Нет | Искры вылетающие из ствола при выстреле |
| Наклон во время перезарядки | [user] MRIntW_ShotgunPumpAngle | 0 | Наклон спрайта дробовика во время передёргивания помпы |
| Случайный наклон | [user] MRIntW_ShotgunPumpRandom | Нет | Выбирать случайный наклон спрайта для каждого передёргивания |
| Диапазон случайного наклона | [user] MRIntW_ShotgunPumpRandRotation | 1 | Максимальное число которое может быть добавлено к наклону спрайта |
| Сила анимации отдачи дробовиков | [nosave] MRIntW_ShotgunsRecoil | 1 | Насколько сильно спрайт дробовика и двустволки увеличивается и опускается при выстреле |

**Двустволка**
| Название | [тип квара] CVar | По умолчанию | Что делает |
| --- | --- | --- | --- |
| Держать цевьё во время перезарядки | [user] MRIntW_SSGHandless | Всегда | Более логичная анимация перезарядки при которой игрок убирает руку с цевья во время открытия двустволки, чтобы взять патроны |
| Дым из казённика | [nosave] MRIntW_SSGSmoke | Да | Дым из стволов после их открытия |
| Искры при выстреле | [nosave] MRIntW_SSGSparks | Нет | Искры вылетающие из ствола при выстреле |
| Сила анимации отдачи дробовиков | [nosave] MRIntW_ShotgunsRecoil | 1 | Насколько сильно спрайт дробовика и двустволки увеличивается и опускается при выстреле |

**Пулемёт**
| Название | [тип квара] CVar | По умолчанию | Что делает |
| --- | --- | --- | --- |
| Фиксированное положение стволов | [user] MRIntW_ChaingunFixed | Нет | По окончании стрельбы стволы будут возвращаться в исходное положение |
| Скорость вращения | [user] MRIntW_ChaingunSpeed | 1 | Не влияет на геймплей (как и почти все перечисленные опции) |
| Сила торможения | [user] MRIntW_ChaingunStopTime | .3 | Как быстро стволы перестают вращаться |
| Вращать стволы против часовой | [user] MRIntW_ChaingunCounterClock | Нет | Много кастомизации не бывает |
| Макс. дымящихся стволов | [nosave] MRIntW_ChaingunMaxSmokes | 3 | Попытка оптимизировать струящийся дым для пулемёта. Помимо этого, длина дыма для пулемёта делиться на количество дымящихся стволов |

**Ракетомёт**
| Название | [тип квара] CVar | По умолчанию | Что делает |
| --- | --- | --- | --- |
| Дым из дула | [nosave] MRIntW_RocketSmoke | 1 | Сила струящегося дыма для ракетомёта |

**Плазмаган**
| Название | [тип квара] CVar | По умолчанию | Что делает |
| --- | --- | --- | --- |
| Частицы при стрельбе | [nosave] MRIntW_PlasmaParticles | Только свечение | Красивое |
| Снаряды излучают динамический свет | [nosave] MRIntW_PlasmaLight | Да | Динамическое освещение для снарядов плазмагана |
| Только каждый второй снаряд излучает свет | [nosave] MRIntW_PlasmaSkipLight | Нет | При стрельбе очередями, каждый второй выстрел не будет излучать динамический свет |

**BFG**
| Название | [тип квара] CVar | По умолчанию | Что делает |
| --- | --- | --- | --- |
| Частицы при стрельбе | [nosave] MRIntW_BFGParticles | Да | Делает анимацию выстрела в разы интересней |


### Настройки --> Настроить интерполированное оружие --> Настройки частиц
| Название | [тип квара] CVar | По умолчанию | Что делает |
| --- | --- | --- | --- |
| Гильзы | [nosave] MRIntW_Casings | Только анимация | Включает гильзы для огнестрельного оружия |
| Макс. скорость гильз | [user] MRIntW_CasingsRandom | 1 | С какой силой гильзы экстрагируются из оружия |
| Громкость отскока гильз | [nosave] MRIntW_CasingsVolume | 1 | Забавный факт: звук сообщения о загрузке сохранения сделанного со старой версией мода, сделан из звуков отскока гильзы дробовика |
| Макс. количество гильз | [nosave] MRIntW_CasingsAmount | 300 | Если количество гильз превысит это значение, старые гильзы начнут пропадать |
| Оптимизировать скопления гильз | [nosave] MRIntW_CasingsClusteringReduce | Да | Предотвращает больше скопление гильз в одной куче |
| Низкая детализация гильз | [nosave] MRIntW_CasingsLowRes | Нет | Альтернативные спрайты для гильз в более низком разрешении (схожи с гильзами из Hideous Destructor) |
| Клубы дыма от выстрелов | [nosave] MRIntW_Smoke | Да | На текстуру этого дыма не влияет настройка текстуры обычного дыма на базе частиц |
| Струящийся дым | [nosave] MRIntW_FlowingSmoke | Нет | Дым от продолжительной стрельбы, на подобии того что был в играх серии Bioshock |
| Длина струящегося дыма | [nosave] MRIntW_FlowingSmokeLength | 0.6 | При значения ниже 0.6 могут появляться разрывы в струях дыма |
| Непрозрачность струящегося дыма | [nosave] MRIntW_FlowingSmokeAlpha | 0.2 | Насколько заметен дым |
| Макс. время дыма | [nosave] MRIntW_FlowingSmokeMaxTime | 1 | Насколько долго дым продолжает идти из ствола |
| Количество частиц в дыме | [nosave] MRIntW_FlowingSmokePrecision | 1 | Струи дыма сделаны из множества круглых (или не круглых, в зависимости от ваших настроек) частиц. Данная настройка регулирует плотность этих частиц. Более низкие значения улучшат производительность, но отдельные частицы станут более заметны |
| Экспериментальная текстура струящегося дыма | [nosave] MRIntW_FlowingSmokeBioTexture | Нет | Более детализированный струящийся дым, больше похожий на тот что был в Bioshock. Работает не идеально |
| Задымление помещений | [nosave] MRIntW_LongTermSmoke | Нет | Довольно экспериментальная функция. Включает постепенное появление большых облаков дыма при стрельбе в одном месте, которые после долго рассеиваются |
| Текстура частиц | [nosave] MRIntW_ParticleTexture | Такая же как у остальных частиц | Эффекты в моде, которые включаются ниже в данном меню, используют данную настройку для выбора внешнего вида частиц. "Такая же как у остальных частиц" означает что будет использоваться текстура частиц выбранная в настройках дисплея вашего сорс порта |
| Текстура частиц дыма | [nosave] MRIntW_ParticleSmokeTexture | Плавная | Данная настройка также распространяется только на эффекты ниже, но затрагивает только частицы дыма, на случай если текстура выбранная выше конкретно дыму может не подойти |
| Эффекты оружия игрока | [nosave] MRIntW_PlayerParticles | Нет | Включает эффекты для снарядов игрока, а также для всех буллет пафов (искры от попаданий по геометрии уровня).
| Качество эффектов оружия игрока | [nosave] MRIntW_PlayerParticlesAmount | 1 | Количество частиц в эффектах игрока. Я на GTX970 и Intel Core i7 3770 ставлю все настройки частиц кроме декораций на х2 |
| Выбранные эффекты оружия игрока | [nosave] MRIntW_PlayerWhichParticles | 134021019 | Все выбранные эффекты игрока хранятся в одном КВаре в формате флагов |
| Эффекты монстров | [nosave] MRIntW_MonsterParticles | Нет | Включает эффекты для снарядов монстров и для них самих |
| Качество эффектов монстров | [nosave] MRIntW_MonsterParticlesAmount | 1 | Количество частиц в эффектах монстров. На картах с большим количеством врагов может потребоваться снизить значение данной настройки |
| Выбранные эффекты монстров | [nosave] MRIntW_MonsterWhichParticles и [nosave] MRIntW_MonsterWhichParticles2 | -33 и -2147483617 | Аналогично эффектам игрока, эффекты монстров хранятся в виде флагов, но из-за их количества пришлось использовать две переменные |
| Применять эффекты к монстрам из модов | [nosave] MRIntW_MonsterParticlesCustom | Нет | Если данная опция не включена, эффекты из мода будут работать только с монстрами и снарядами из Doom |
| Мухи над трупами | [nosave] MRIntW_ParticleFlies | Нет | Мухи летающие над трупами в стиле Quake 2 |
| Громкость жужжания | [nosave] MRIntW_ParticleFliesVolume | 0.4 | Он точно будет кого-то бесить |
| Альт. визуализация молний | [nosave] MRIntW_AltLightnings | Нет | По умолчанию молнии в эффектах будут моментально появляться и медленно исчезать. С данной настройкой молнии будут "вырастать", а после пропадать с эффектом расщепления |
| Эффекты декораций | [nosave] MRIntW_DecorationParticles | Нет | Включает эффекты для декораций. Помимо прочего добавляет ореолы на подобии блума для светящихся объектов |
| Качество эффектов декораций | [nosave] MRIntW_DecorationParticlesAmount | 1 | Количество частиц в эффектах декораций |
| Выбранные эффекты декораций | [nosave] MRIntW_DecorationWhichParticles | 511 | То же самое что и с эффектами игрока и монстров |
| Эффект телепортации | [nosave] MRIntW_TeleportParticles | Нет | Включает эффекты на базе частиц для телепортации |
| Стиль телепортации | [nosave] MRIntW_TeleportParticlesStyle | Волна | Доступны варианты: 2 кольца, Взрыв, Испарение, Обратный взрыв, Двойное испарение, Странное облако, Волна |
| Стиль телепортации монстра | [nosave] MRIntW_TeleportParticlesStyleMonsters | Испарение | Тоже самое, но для телепортации монстров |
| Эффект возрождения предметов | [nosave] MRIntW_RespawnParticles | Нет | Эффект респавна предметов. |

### Настройки --> Настроить Интерполированное оружие --> Настройки звуков
| Название | [тип квара] CVar | По умолчанию | Что делает |
| --- | --- | --- | --- |
| Громкость отскока гильз | [nosave] MRIntW_CasingsVolume | 1 | Дубликат настройки громкости гильз из меню частиц |
| Громкость работы пилы | [nosave] MRIntW_ChainsawVolume | 1 | Кому-то он может надоедать |
| Рандомизация высоты звука пилы | [nosave] MRIntW_ChainsawRandomPitch | 0 | Добавляет вариативность звуку работы пилы |
| Громкость альт. атаки BFG | [nosave] MRIntW_BFGAltVolume | .6 | Громкость гудения BFG во время проигрывания анимации на ПКМ |
| Звуки оружия высокого качества | [nosave] MRIntW_HQSounds | Нет | Использовать не сжатые звуки для оружия |
| Звуки смены оружия | [nosave] MRIntW_SwitchSounds | Нет | Проигрывать звуки при доставании и убирании оружия |
| Звуки пулемёта из аддона | [nosave] MRIntW_ChaingunSound | Нет | Проигрывать кастомный звук стрельбы для пулемёта, вместо звука выстрела пистолета |

### Настройки --> Настроить интерполированное оружие --> Настройки интерфейса
| Название | [тип квара] CVar | По умолчанию | Что делает |
| --- | --- | --- | --- |
| Плавное меню | [nosave] MRIntW_SmoothUi | Да | Отключает ограничение на фпс в меню, сглаживает его прокрутку и отдельные элементы |
| Плавные переходы в меню | [nosave] MRIntW_SmoothUiTransitions | Везде | Добавляет анимацию перехода от одного меню к другому |
| Анимированный логотип | [nosave] MRIntW_SmoothUiLogo | Да | Добавляет анимации для лого в меню. |



## Кредитссс
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

## Для моддеров
Никому ничего не запрещаю, код можно смотреть, копировать и использовать в своих работах, как и ассеты мода (хотя я сомневаюсь, что это нечто кто-то будет использовать), но в кредитсах по возможности прошу указывать.  

При работе с модом обратите внимание на папку Mod info и на файл TexturexEditing!.txt, в последнем указаны все спрайты к которым нужно применение NoTrim - такой же список должен находится в основном файле
Textures.txt, который ничего кроме этого списка не должен в себе содержать, ибо при сохранении этого файла в режиме фоторедактора, все строки NoTrim из него удаляются.
***
## $\color{#FF0000}{Дай\ уже\ скачать\ мод\ долбаный\ задрот}$

На вот на вот https://github.com/mickromash/InterpolatedWeapons/archive/refs/heads/main.zip
