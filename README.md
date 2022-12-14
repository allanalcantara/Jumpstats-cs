# Unique Jumpstats plugin  ![GitHub build](https://img.shields.io/badge/build-compiled-brightgreen.svg) [![GitHub release](https://img.shields.io/github/release/michaelkheel/UQJumpstats.svg)](https://github.com/MichaelKheel/UQJumpstats/releases)
Initial version of the file **2.39**

Jumping statistics plugin for Goldsrc Engine (Counter-Strike 1.6) originally developed by Borjomi, but heavily modified by me.

Completely rewritten plugin uq_jumpstats_top.sma. The menu looks different. More correct distribution of items and more.

![Screenshot](screenshots/20180904174146_1.jpg)
![Screenshot](screenshots/20180904174155_1.jpg)
![Screenshot](screenshots/20180904174212_1.jpg)

### Supported Build
* ReHLDS 3.4.0.X
* Linux 5787 and higher
* Windows 5758 and higher

### AMXMODX Version
* 1.8.1+

### Required modules
* amxmodx
* amxmisc
* cstrike
* engine
* fakemeta
* hamsandwich
* mysql

### This plugin measures jump techniques:
* LongJump
* HighJump
* WeirdJump
* WeirdJump after Double Duck
* CountJump
* Double CountJump
* Multi CountJump
* Drop CountJump
* Drop Double CountJump
* Drop Multi CountJump
* BhopJump
* Drop BhopJump
* Standup BhopJump
* Ladder Bhop
* Real Ladder Bhop
* LadderJump
* Up BhopJump
* Up Standup BhopJump
* Up BhopJump in Duck
* BhopJump in Duck
* DuckBhopJump
* Standup CountJump
* Standup Double CountJump
* Standup Multi CountJump
* Drop Standup CountJump
* Drop Standup Double CountJump
* Drop Standup Multi CountJump
* MultiBhopJump

### The message about the jump in the chat is more detailed.
![Screenshot](screenshots/20180904172819_1.jpg)
![Screenshot](screenshots/20180904172829_1.jpg)
![Screenshot](screenshots/20180904172925_1.jpg)
![Screenshot](screenshots/20180904173542_1.jpg)

## Features:
### Jump Stats:
* Distance
* Maxspeed and Gain
* Prestrafe
* Strafes
* Sync
* Duck Count

### Strafe Stats:
* Gain speed each strafe
* Sync each strafe
* Loss on each strafe
* Air time on each strafe

### Jump Beam
* First type = simple beam
* Second type = beam with showing strafes

### Sounds:
* Impressive
* Perfect
* Holy Shit
* Wicked Sick
* Godlike
* Domination

### Turning On/Off Abilities:
* Current Speed
* Jump Prestrafe
* Speed after Ducks
* Jump Stats
* Strafe Stats
* Jump messages in chat
* Jump Beam
* Jump Sounds
* MultiBhop Prestrafe
* LJ Prestrafe
* Block Distance
* Edge Distances
* Edge Distances when

### Connecting to mysql
For security reasons, the connection to the database is made through the config file amxmodx/config/uqjumpstats.cfg

This avoids the appearance of database data in cvars.

```C#
// Mysql Connect
kz_uq_host = []
kz_uq_user = []
kz_uq_pass = []
kz_uq_db = []
```
### Commands
```
say /ljsmenu ??? open the configuration menu 
say /ljtop ??? open TOP10 menu

say /strafes ??? on/off statistics Strafes
say /showpre ???on/off display prestrafe
say /ducks ???on/off statistics ducks for multi cj
say /ljstats ???on/off the main statistics
say /beam ??? on/off showing the trajectory of the jump
say /colorchat ???on/off display of color in the chat messages from other players
say /bhopwarn -on/off show message when you bhop prestrafe is fail
say /multibhop - on/off show multi bhop pre
say /duckspre - on/off display prestrafe after each duck
say /ljpre - on/off display prestrafe for LJ
say /failedge - on/off display jumpoff wehn failed without bolock
say /edge - on/off display jumpoff,block,landing
say /height - on/off display height of jump 
say /mylj - on/off myljtop menu
say /jof - on/off showing jumpoff
say /joftr - on/off jumpof trainer
say /wpnlj - on/off weapon top menu
say /jheight - on/off jump height
```
### Config file 
```
// Mysql Connect
kz_uq_host = []
kz_uq_user = []
kz_uq_pass = []
kz_uq_db = []

// 0 = none
// a = colorchat
// b = stats
// c = speed
// d = showpre
// e = strafe stats
// f = beam
// g = duck stats for mcj
// h = shows message when your bhop prestrafe is failed
// i = show multibhop pre
// j = show prestrafe after duck
// k = show lj prestrafe
// l = show edge
// m = show edge when fail (without block)
// n = on/off sound's on players 
kz_uq_connect "abdeghijklmno"

// Min distance
kz_uq_min_dist 215

// Min distance (Ups bhop, MultiBhop, Real Ladder Bhop, Ducks Bhop, Ladder Jump)
kz_uq_min_dist_other 150

// Max distance
kz_uq_max_dist 290

// Allow sounds (1 = on, 0 = off)
kz_uq_sounds 1

// Allow check to legal settings (1 = on, 0 = off)
kz_uq_legal_settings 1
kz_uq_fps 1 - (1=more than 100 FPS jump does not count, 0=count)
kz_uq_bug_check 1
kz_uq_script_detection 1 - (beta)

// Allow InGame Strafe Stats (laggy feature)
kz_uq_istrafes 0

// How to set up a server by value sv_airaccelerate (0=10aa, 1=100aa)
kz_uq_airaccelerate 0

kz_uq_noslowdown 0

// Max strafes (if players strafes>Max, stats doesnt shows)
kz_uq_max_strafes 14

// Color Hud message statistics when you jump, in the RGB
kz_uq_stats_red 50
kz_uq_stats_green 189
kz_uq_stats_blue 100

// Color Hud messages Fail statistics when you jump, in the RGB
kz_uq_failstats_red 228
kz_uq_failstats_green 80
kz_uq_failstats_blue 80

// Color Hud messages prestrafe, in the RGB
kz_uq_prestrafe_red 30
kz_uq_prestrafe_green 255
kz_uq_prestrafe_blue 255

// Color of speed, in the RGB
kz_uq_speed_red 255
kz_uq_speed_green 255
kz_uq_speed_blue 255

//Coordinates Hud messages

//General stats jump
kz_uq_stats_x "-1.0"
kz_uq_stats_y "0.70"

//Strafes Stats
kz_uq_strafe_x "0.70"
kz_uq_strafe_y "0.35"

//Ducks Stats for Multi dd
kz_uq_duck_x "0.6"
kz_uq_duck_y "0.78"

//Speed
kz_uq_speed_x "-1.0"
kz_uq_speed_y "0.83"

//Prestrafe
kz_uq_prestrafe_x "-1.0"
kz_uq_prestrafe_y "0.65"

// Channel Hud messages of general stats jump
kz_uq_hud_stats 3

// Channel Hud messages of strafes Stats
kz_uq_hud_strafe 2

// Channel Hud messages of ducks Stats for Multi CountJump
kz_uq_hud_duck 1

// Channel Hud messages of speed
kz_uq_hud_speed 2

// Channel Hud messages of prestafe
kz_uq_hud_pre 1

// For what technique stats enable
kz_uq_lj 1
kz_uq_cj 1
kz_uq_bj 1
kz_uq_sbj 1
kz_uq_wj 1
kz_uq_dcj 1
kz_uq_mcj 1
kz_uq_drbj 1
kz_uq_drcj 1
kz_uq_ladder 1
kz_uq_ldbj 1

// Max,Min block to show in edge
kz_uq_max_block 290
kz_uq_min_block 200

// Minimum Prestrafe to show
kz_uq_min_pre 60

// For what Extra technique stats enable
kz_uq_scj 1
kz_uq_dscj 1
kz_uq_mscj 1
kz_uq_dropscj 1
kz_uq_dropdscj 1
kz_uq_dropmscj 1
kz_uq_duckbhop 0
kz_uq_bhopinduck 1
kz_uq_realldbhop 1
kz_uq_upbj 1
kz_uq_upsbj 1
kz_uq_upbhopinduck 1
kz_uq_multibhop 0
kz_uq_dropdcj 1
kz_uq_dropmcj 1

// Color for chat messages of jump distances (good = grey, pro = green, holy = blue, leet = red, god = red (with sound godlike for all players))
// LongJump/HighJump
kz_uq_good_lj 240
kz_uq_pro_lj 245
kz_uq_holy_lj 250
kz_uq_leet_lj 252
kz_uq_god_lj 254
kz_uq_dom_lj 255


// CountJump
kz_uq_good_cj 250
kz_uq_pro_cj 255
kz_uq_holy_cj 260
kz_uq_leet_cj 263
kz_uq_god_cj 265
kz_uq_dom_cj 267

// Double CountJump/Multi CountJump
kz_uq_good_dcj 250
kz_uq_pro_dcj 255
kz_uq_holy_dcj 260
kz_uq_leet_dcj 265
kz_uq_god_dcj 268
kz_uq_dom_dcj 270

// LadderJump
kz_uq_good_ladder 150
kz_uq_pro_ladder 160
kz_uq_holy_ladder 170
kz_uq_leet_ladder 180
kz_uq_god_ladder 185
kz_uq_dom_ladder 190

// BhopJump/StandUp BhopJump
kz_uq_good_bj 230
kz_uq_pro_bj 235
kz_uq_holy_bj 240
kz_uq_leet_bj 243
kz_uq_god_bj 245
kz_uq_dom_bj 247

// WeirdJump/Drop CountJump(double,multi)/Ladder BhopJump
kz_uq_good_wj 250
kz_uq_pro_wj 255
kz_uq_holy_wj 260
kz_uq_leet_wj 265
kz_uq_god_wj 268
kz_uq_dom_wj 270

// Drop BhopJump
kz_uq_good_dbj 240
kz_uq_pro_dbj 250
kz_uq_holy_dbj 260
kz_uq_leet_dbj 263
kz_uq_god_dbj 265
kz_uq_dom_dbj 267

// StandUp CountJump (Double or Multi StandUp CountJump=SCJ+10units)(if 100aa all cvar dist +10 units)
kz_uq_good_scj 245
kz_uq_pro_scj 250
kz_uq_holy_scj 255
kz_uq_leet_scj 257
kz_uq_god_scj 260
kz_uq_dom_scj 262

// Drop StandUp CountJump(double,multi)
kz_uq_good_dropscj 250
kz_uq_pro_dropscj 255
kz_uq_holy_dropscj 260
kz_uq_leet_dropscj 263
kz_uq_god_dropscj 265
kz_uq_dom_dropscj 267

// Up Bhop
kz_uq_good_upbj 225
kz_uq_pro_upbj 230
kz_uq_holy_upbj 235
kz_uq_leet_upbj 240
kz_uq_god_upbj 242
kz_uq_dom_upbj 245

// Up StandBhop
kz_uq_good_upsbj 225
kz_uq_pro_upsbj 230
kz_uq_holy_upsbj 235
kz_uq_leet_upsbj 240
kz_uq_god_upsbj 242
kz_uq_dom_upsbj 245

// Bhop In Duck(Up Bhop In Duck)
kz_uq_good_bhopinduck 205
kz_uq_pro_bhopinduck 210
kz_uq_holy_bhopinduck 212
kz_uq_leet_bhopinduck 215
kz_uq_god_bhopinduck 217
kz_uq_dom_bhopinduck 220

// Duck Bhop
kz_uq_good_duckbhop 120
kz_uq_pro_duckbhop 130
kz_uq_holy_duckbhop 140
kz_uq_leet_duckbhop 150
kz_uq_god_duckbhop 160
kz_uq_dom_duckbhop 162

// Real Ladder Bhop
kz_uq_good_realldbhop 240
kz_uq_pro_realldbhop 250
kz_uq_holy_realldbhop 255
kz_uq_leet_realldbhop 260
kz_uq_god_realldbhop 265
kz_uq_god_realldbhop 267
```
