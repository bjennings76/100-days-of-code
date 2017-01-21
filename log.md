# 100 Days Of Code - Log


### Day 1: January 9, Monday 

#### Today's Progress
1. Forked [100-days-of-code](https://github.com/Kallaway/100-days-of-code)
2. Updated docs of fork with my own info
3. Copied previous progress over from [unity-vr-puppeteer repo](https://github.com/bjennings76/unity-vr-puppeteer)
4. Cleaned up [Favro Board](https://favro.com/organization/2857ca4e59648312669b3470/4f3ad4ae8deea00fd4a99356) and made it public

#### Thoughts
It's nice to be back from vacation and get back to sweet, sweet code. Mostly cleanup and preparation for this hour.

#### Link(s) to work
Steps: [Join the #100DaysOfCode](https://medium.freecodecamp.com/join-the-100daysofcode-556ddb4579e4#.962oiqjiq)


### Day 2: January 10, Tuesday

#### Today's Progress
1. Created a spinner script to turn the character selector
2. Cleaned up a lot of files
3. Upgraded to VRTK 3.0 and fixed issues created by upgrade

#### Thoughts
It was a rough start due to some VRTK upgrade issues, but once I got the table spinner working, things got fun. I threw together some puppets onto it to test it out. They turn well and throw their little limbs around with inertial forces making the turn table fun to play with. It definitely feels like the right way to for puppet selection.

Next up: Getting the puppets to cycle through all options as the spinner turns.

#### Link(s) to work
![Spinning Spinner](Captures/Day%20002%20-%20Spinner.gif)


### Day 3: January 11, Wednesday

#### Today's Progress
1. Fixed all Unity 5.5 obsolete call warnings from the build created by SteamVR and ProBuilder
2. Created a 'magic box' inside which items can get swapped out
3. Started work on creating a list of object creators.

#### Thoughts
Ran in to an interesting problem where I would like to have bespoke object prefabs that can be instanced along with a list of objects created dynamically from a single object through sub-object changes (swapping costumes on a single character, for instance). This forced me to think out exactly how to create a list of objects that don't yet exist. I'm exploring the idea of a list of item creators which would have a default creator for prefab version and customized create functions for the dynamic objects. Wasn't able to finish it up, but I should have a list of object creators to cycle through tomorrow.

#### Link(s) to work
![Changing Room Capture](Captures/Day%20003%20-%20Magic%20Changing%20Room.gif)


### Day 4: January 12, Thursday

#### Today's Progress
1. Puppets now are dynamically placed onto the spinner.
2. Discovered how `Math.Mod()` can be used to wrap an index into a valid index in a list. e.g. `index = index % count + count) % count;`

#### Thoughts
Most of the work is under the hood, but it'll be pretty slick to use going forward. I'm especially proud of keeping the item generation classes small and legible.


### Day 5: January 13, Friday

#### Today's Progress
1. Upgraded to SteamVR 1.2
2. Moved the project back into [unity-vr-puppeteer](https://github.com/bjennings76/unity-vr-puppeteer) so work shows up in GitHub contributions
3. Item Carousel now properly swaps out character models as they go through the changing room.

#### Thoughts
Nice to see some visible progress today and was happy to be able to capture the end result.

#### Link(s) to work
![Item Carousel swapping models](Captures/Day%20005%20-%20Puppet%20Carousel%20Swapping%20Models.gif)


### Day 6: January 14, Saturday

#### Today's Progress
1. Added label names to Item Spinner
2. Added dynamic slot count to Item Spinner

#### Thoughts
Got a bonus out of thinking about how to efficiently add labels to the item spinner. I need to create a template and noticed all the item slots were the same except 45 degree rotations which could easily be deduced by `360 / SlotCount`. Decided now that I had item slot templates, I could easily set them up to dynamically distribute themselves.

It's especially great having a decent util library built up. I was able to simply do `name.ToSpacedName()` and get file asset names to clean themselves up in no time. No lengthy regex research needed.

#### Link(s) to work
![Item Carousel with labels and dynamic slot placement](Captures/Day%20006%20-%20Puppet%20Carousel%20Labels%20and%20Placement.gif)


### Day 7: January 15, Sunday

#### Today's Progress
1. Stylized/increased resolution of the curtains
2. Fixed a few bugs and inconsistencies

#### Thoughts
Not much actual coding today. Mostly just asset upkeep, but the curtains are looking better.

#### Link(s) to work
![Curtain Cleanup](Captures/Day%20007%20-%20Curtians%20Cleanup.gif)


### Day 8: January 16, Monday

#### Today's Progress
1. Disabled collision for items spawned onto the item wheel
2. Started work on supporting object duplication on grab of an item on the wheel.

#### Thoughts
Did lots of research into the right way to grab an object. Thought about looking into the new SteamVR interaction scripts, but decided to stick with VRTK for now. Pulled some code out of the `VRTK_ObjectAutoGrab.cs` script. Not exactly working like I'd like it to, though. Will work on it more tomorrow.

#### Link(s) to work
[Grab Commit (WIP)](https://github.com/bjennings76/unity-vr-puppeteer/commit/f37af09e0ef644ac5bc51c404360876ed1791981)


### Day 9: January 17, Tuesday

#### Today's Progress
1. Fixed issues with spawning an item from an item slot
2. Some objects can now be optionally hidden in the item slot preview

#### Thoughts
Pretty good progress, but I wasn't able to get the Item Slot to push the new item directly onto the controller. Until I can figure out the problem, the new item simply spawns in the middle of the wheel.

#### Link(s) to work
![Curtain Cleanup](Captures/Day%20009%20-%20Spawned%20Item.gif)


### Day 10: January 18, Wednesday

#### Today's Progress
1. Added item type selection buttons to item carousel
2. Added editor script to auto-restart unity on compile
3. Added editor script to stop play mode with 'escape' key

#### Thoughts
Spent a lot of time thinking about exactly how to switch categories. Settled on using buttons on the spinner that rotate with the rest of the object. Not sure if it'll be confusing or not. Playtesting should be interesting.

#### Link(s) to work
![Item Type Selection Buttons](Captures/Day%20010%20-%20Item%20Type%20Selection.gif)


### Day 11: January 19, Thursday

#### Today's Progress
1. Set up buttons to swap out various item types
2. Created item type configs to use for changing item types on the spinner
3. Updated item type creation to work with the default scale of the SimpleFantasy assets

#### Thoughts
Pretty straight forward stuff. I'm digging the `ScriptableObject` stuff. I like how easy it is to create them now by simply adding `[CreateAssetMenu]`. It was also nice to off-load a lot of properties from `ItemDispensor` into the `ItemType` scriptable objects.

#### Link(s) to work
![Working Item Type Selection](Captures/Day%20011%20-%20Working%20Item%20Type%20Selection.gif)


### Day 12: January 20, Friday

#### Today's Progress
1. Updated prop spawn points to auto-scale objects to fit inside the box collider

#### Thoughts
I was able to get the objects to scale to the right size, but setting their positions based on the center of their bounding box didn't work quite right. Going to try and use the `OnDrawGizmos()` to determine exaclty where the math is wrong.

#### Link(s) to work
[Scale Prop Preview Commit](https://github.com/bjennings76/unity-vr-puppeteer/commit/45546d1f0dcfbfa0b2178e3ae618c6a34c7b6acb)


### Day 13: January 21, Saturday

#### Today's Progress
1. Spawned prop previews now properly place themselves onto the prop carousel
2. Added a tool to the PropType config files that allow me to auto-populate the prop list from a given folder of prefabs
3. Added a `TrimRegex` properly to the PropType config files that automaticaly trim out parts of the prop names that match the regex
4. Added all props in the Props folder to the Props config

#### Thoughts
I almost wasn't able to work on the project tonight, but at the last minute was able to clear out some time. Glad I was able to get in some tools that allow me to skip a lot of hand-editing of individual assets. Now I have tons of them from the SimpleFantasy pack without much work at all.

#### Link(s) to work
![Properly Placed Props](Captures/Day%20013%20-%20Properly%20Placed%20Props.gif)

<!-- Template


### Day 3: January 11, Wednesday

#### Today's Progress
1. 

#### Thoughts

#### Link(s) to work

-->
