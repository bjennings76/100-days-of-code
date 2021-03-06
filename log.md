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


### Day 14: January 22, Sunday

#### Today's Progress
1. Updated control of the puppet
2. Made the kinematic puppet stick change to non-kinematic when certain points are selected
3. Created a 'skip unlock' component to let the arms and legs move without unlocking the stick

#### Thoughts
Work is going well. Still hard to find the time to work on this, especially with people around. Have to keep making sacrifices to the sleep god.

#### Link(s) to work
![Corrected Character Controls](Captures/Day%20014%20-%20Puppet%20Control%20Improvements.gif)


### Day 15: January 23, Monday

#### Today's Progress
1. Started work on a life-size puppet theatre.

#### Thoughts
Tried out a formal stage with a hidden camera and it seems like the right direction. Really grounds the player on where the camera/audience is.

#### Link(s) to work
[Puppet Theatre Stage WIP Commit](https://github.com/bjennings76/unity-vr-puppeteer/commit/b027d7bc4f5724362e01bdfc5d2cb59bfa75ced0)


### Day 16: January 24, Tuesday

#### Today's Progress
1. Finished theatre probuilder geo
2. Played with lighting
3. Created a moveable spotlight

#### Thoughts
It's looking pretty good, but I'm not sure about the audience 'mirror' anymore. It's strange interacting with the back of the puppets... but I'm not sure what would be better. Maybe have them face forward somehow?

I'll playtest it first before I make any more significant layout changes.

#### Link(s) to work
![Mood Lighting](Captures/Day%20016%20-%20Theatre%20Lighting.gif)


### Day 17: January 25, Wednesday

#### Today's Progress
1. Fixed issue that shrunk down characters
2. Improved lighting in the scene a bit
3. Added support for throwing puppets based on velocity

#### Thoughts
A bit distracted tonight, but I was able to figure out a few things. I think throwing vs sticking to thin air will work well. Exactly what velocity and what constraints that should be done in is yet to be seen, though. Need to remove the sticks when in throwable mode as they tend to burst the puppet's IK apart when it hits the ground.

#### Link(s) to work
[Throwing Support Commit](https://github.com/bjennings76/unity-vr-puppeteer/commit/8b09b642a8c2446d47380547beba5018d4da5450)


### Day 18: January 26, Thursday

#### Today's Progress
1. Updated puppets to turn off grab sticks when grabbed by their ragdoll points (chest and head)
2. When released above the throw velocity threshold, the grab sticks stay hidden
3. Simplified some underlying code that handled scale and the like.

#### Thoughts
Kinda went down a rabbit hole on exactly how to handle scaling. There's an issue with Unity's kinematic joints not scaling correctly when an object is instantiated and re-scaled in the same frame. Still need to do more work to get it to work properly in the dispenser.

#### Link(s) to work
![Tossable Puppets](Captures/Day%20018%20-%20Tossable%20Puppets.gif)


### Day 19: January 27, Friday

#### Today's Progress
1. Added an editor button to the Inspector GUI to test spawning objects
2. `BoxCollider` and `VRTK_InteractableObject` are now automatically added to props that don't have it when they are grabbed.

#### Thoughts
Wasn't able to do as much work as I would have liked today. Too tired. Should have more time durng the weekend.

#### Link(s) to work
[Auto Collision Commit](https://github.com/bjennings76/unity-vr-puppeteer/commit/4e0a3b42eebace129eca0028c3e1e377836dbfea)


### Day 20: January 28, Saturday

#### Today's Progress
1. Added visualization of spring joints as strings
2. Added head controls to puppet handle

#### Thoughts
It took a bit of experimenting, but recreating real-world interactions like the tried and true marrionette controls seems to be working well.

#### Link(s) to work
![Strings Attached](Captures/Day%20020%20-%20Strings%20Attached.gif)


### Day 21: January 29, Sunday

#### Today's Progress
1. Worked on improving interactions with the Prop Carousel.

#### Thoughts
Overriding the grab behaviour of VRTK has been difficult. I wasn't able to get very far today, but I have a good idea of something new to try tomorrow. Going to try just allowing the player to grab the preview object and not have the slot have any collision at all, but subscribe to the grab event of the object and resize to the desired size when they do. May even be able to give it a cool transition animation.

#### Link(s) to work
[Grabbing WIP Commit](https://github.com/bjennings76/unity-vr-puppeteer/commit/0c18ba0f1a1d01473948a820e2dfe7017911f4e2)


### Day 22: January 30, Monday

#### Today's Progress
1. Finally figured out how to support proper grabbing
2. Improved system for tracking interactions with Prop Carousel

#### Thoughts
After struggling to get objects to pull directly out of the Prop Carousel and finally realizing I should just use the actual props, it was great to see it all come together to quickly.

#### Link(s) to work
![Easy Grab](Captures/Day%20022%20-%20Easy%20Grab.gif)


### Day 23: January 31, Tuesday

#### Today's Progress
1. Started work on snapping objects into puppet hands.
2. Research VRTK's snap drop points.
3. Added a cycling 'interest attractor' object.
4. Some work on snapping.

#### Thoughts
Got a bit distracted imagining what would attract the player's attention. Got a good solution, but the actual snapping bit isn't working just yet.

#### Link(s) to work
![Attractor Test](Captures/Day%20023%20-%20Attractor%20Test.gif)


### Day 24: February 1, Wednesday

#### Today's Progress
1. Experimented more with object snapping

#### Thoughts
Pretty tired today and wasn't able to get very far. Still not sure why sometimes there is a preview prefab and sometimes there isn't. May be something to do with how things are specifically set up in the preview object. Will look in to it more tomorrow.

#### Link(s) to work
[Snapping Tests Commit](https://github.com/bjennings76/unity-vr-puppeteer/commit/220cf09ff6a8159c8f24a6d8c4d0fdbad7bc6b6c)


### Day 25: February 2, Thursday

#### Today's Progress
1. Figured out how to show interaction feedback
2. Set up puppet hands to hold equipment

#### Thoughts
There are smaller details that aren't exactly lining up yet, like how to get the drop points to use assigned handles when snapping on equipment. I may need to add a feature to VRTK to get that feature.

I must say, I do enjoy watching the ragdoll physics freak out when it tries to handle too much weirdness.

#### Link(s) to work
![Why Are You Hitting Yourself?](Captures/Day%20025%20-%20Violent%20Puppet.gif)


### Day 26: February 3, Friday

#### Today's Progress
1. Started work on a prop config format that will allow me to offset things like the handle location.

#### Thoughts
Not sure if this is the right system for the job, but it would be nice to tweak prefab from package that may update one day.

#### Link(s) to work
[Prop Detail Support Commit](https://github.com/bjennings76/unity-vr-puppeteer/commit/fcaba6f8fa51e9f7f1457d39ca0bfa0d689fb99b)


### Day 27: February 4, Saturday

#### Today's Progress
1. More work on supporting custom offsets for hand-snappable props.
2. Created a custom editor for the prop settings that are held within each prop type config.

#### Thoughts
The work seems to be dragging a bit, but hopefully it will get moving soon. Still need to figure out an easy way to lock in the offset position and rotation based on a manually placed object in the scene.

#### Link(s) to work
[Hand Snapping Commit (WIP)](https://github.com/bjennings76/unity-vr-puppeteer/commit/d8c2db1bb76af953285fce37efaf2e9c2eaf28cc)


### Day 28: February 5, Sunday

#### Today's Progress
1. Tweaked VRTK to allow a 'precision' snap on a drop zone, so weapons can be placed in arbitrary locations.

#### Thoughts
Still noodling on exactly how to let the player place weapons on a puppet's hands. Running out of steam, but I think I've got an idea that will work well and not require too much coding.

#### Link(s) to work
[VRTK Precision Snap Commit](https://github.com/bjennings76/unity-vr-puppeteer/commit/b6b6b0ea716d72adb3f0b21dd67c7dd652acc6a5)


### Day 29: February 6, Monday

#### Today's Progress
1. Fixed changing room geo on the prop spinner
2. Looked in to scaling issues with the puppets.

#### Thoughts
Didn't fully fix the scaling issues yet. Looks like I'll be doing more debugging tomorrow.

#### Link(s) to work
[Puppet Scaling Bug Work](https://github.com/bjennings76/unity-vr-puppeteer/commit/76fd23056590514f6b8458654c16f518dcb49578)


### Day 30: February 7, Tuesday

#### Today's Progress
1. Added Playfab Unity SDK
2. Added Asset Bundle Manager

#### Thoughts
Wanted to play around with the idea of removing all content and having it download as needed. Today I added some SDKs that should allow me to do that. Will play with them tomorrow.

#### Link(s) to work
[Playfab Commit](https://github.com/bjennings76/unity-vr-puppeteer/commit/a6f0f05308d8e82af45157ec56bbb92d9dde6fe1)


### Day 31: February 8, Wednesday

#### Today's Progress
1. Created a trash can for throwing away props

#### Thoughts
Was stuck for a while trying to figure out how to have one interactable object interact with another one when I realized I could just use a drop point like I was doing for the hands and have the drop point itself delete the new object. Worked like a charm! Even had some time to throw in some tweening.

#### Link(s) to work
![Taking Out the Trash](Captures/Day%20031%20-%20Taking%20Out%20the%20Trash.gif)


### Day 32: February 9, Thursday

#### Today's Progress
1. Created a JointScaler component that's supposed to properly scale a ragdoll character.

#### Thoughts
The attempt didn't really work out. It seems like the anchors scale in the wrong ways, possibly due to how the hierarchy is set up. I'll need to look in to it more.

#### Link(s) to work
[JointScaler Commit](https://github.com/bjennings76/unity-vr-puppeteer/commit/2d2659262e035aa7d64d53318115ea8cfe1ab9bd)


### Day 33: February 11, Saturday

#### Today's Progress
1. More work on the JointScaler

#### Thoughts
I found something that kinda works in terms of scaling stuff, but if you scale too menu, joints get disconnected and weird. Still not sure if I can do this properly. Probably going to have to come up with a solution that doesn't involve scaling when joints are involved.

#### Link(s) to work
![Scaling Issues](Captures/Day%20033%20-%20Scaling%20Issues.gif)


### Day 34: February 13, Monday

#### Today's Progress
1. Code cleanup
2. Fixed stand-alone build

#### Thoughts
Nothing too interesting today. Just cleaned up some code. I may be procrastinating a bit.

#### Link(s) to work
[Simplified Prop Type Config UI](https://github.com/bjennings76/unity-vr-puppeteer/commit/624e0d0f88ecc455be28ff804c48d2661626411c)


### Day 35: February 15, Wednesay

#### Today's Progress
1. Removed the hinge joint on the prop carousel
2. Modified the carousel spinner so it working in kinematic mode and can't be pushed around.
3. Created a 'JointToggler' and disabled string joints when in 'unlock' mode.

#### Thoughts
Had to skip a day due to moving houses and lack of internet connection. Still at it, though! This is really 2 days worth of work.

#### Link(s) to work
[Disabled Joints Commit](https://github.com/bjennings76/unity-vr-puppeteer/commit/94d257ffcde08afc7b13b9ab69347f85feb75b83)


### Day 36: February 16, Thursday

#### Today's Progress
1. Cleaned up the `JointToggler` some more.
2. Added support for actual size props on the prop carousel
3. Set up Character props to use actual size.

#### Thoughts
Well, I have life-sized props all right, but they collide with the wall and freak out when I spin the carousel. I'll need the props to ignore colliders or remove collision around the props somehow so it spins nicely once again. That'll be tomorrow, though.

#### Link(s) to work
![Puppet Collision Madness](Captures/Day%20036%20-%20Puppet%20Collision%20Madness.gif)


### Day 37: February 18, Saturday

#### Today's Progress
1. Fixed up carousel spin by removing collision
2. Fixed how puppets are handled when they are grabbed off the carousel
3. Puppets now have their controls enabled as you would expect.

#### Thoughts
Loosing motivation to get stuff done, but once I'm doing it, I do still enjoy it. Especially when it works! Still some problems with the carousel model swap, but I'm happy the characters are working well after all this time! It is too bad I wasn't able to get them to scale down as I would have liked.

#### Link(s) to work
![Working Puppets from Carousel](Captures/Day%20037%20-%20Working%20Puppet%20Carousel.gif)


### Day 38: February 19, Sunday

#### Today's Progress
1. Fixed up carousel's model swapping by repairing the Angle propertly

#### Thoughts
Looks like the angle broke after the refactor that removed the collision. I wasn't able to do much today due to a lot of unpacking and not much motivation, but I am happy that the experience is starting to become usable.

#### Link(s) to work
[Carousel Model Swap Fix Commit](https://github.com/bjennings76/unity-vr-puppeteer/commit/cc84e33e620f0f38a316af1fbb7818ecba0a70c9)


### Day 39: February 20, Monday

#### Today's Progress
1. Improved prop carousel spinning interaction

#### Thoughts
The stop-start of the prop carousel was really bothering me, so I dedicated some time to cleaning it up. It spins much more smoothly now. Aaaaah.

#### Link(s) to work
![Smooth Carousel Spin](Captures/Day%20039%20-%20Smoother%20Spinning.gif)


### Day 40: February 21, Tuesday

#### Today's Progress
1. Started work on a 'Puppet Possession' mode.

#### Thoughts
Wasn't sure exactly where to go next. Floundered a bit as I didn't originally have access to the VR equipment and didn't have an idea of what I could do without testing in VR. Once I did get access, I still wasn't sure exactly what to focus on. The backlog showed a cool idea of becoming the puppet with a button press, so I'm trying that out.

Perhaps the player can become one with the puppet by simply putting their face into the puppet?

#### Link(s) to work
[Puppet Possession Commit](https://github.com/bjennings76/unity-vr-puppeteer/commit/c1a3b53876f1cc14f38d9656498d6b99844d5983)


### Day 41: February 22, Wednesday

#### Today's Progress
1. Finished first pass on 'Puppet Possession' mode

#### Thoughts
It was a bit difficult to see how to properly interact with the controller. Luckily VRTK had a bunch of easy-access features for me to use to track down the controllers.

On the interaction itself, it's really interesting to change your scale. May need to explore that more. Ideally, you wouldn't see any of the head geometry, but I don't think there's a way to just hide the head of the puppet without scaling it down or something. I may have to hide the entire puppet from the player's perspective and only show it in the mirror. Wouldn't be as fun, alas.

#### Link(s) to work
![Taking Possession](Captures/Day%20041%20-%20Taking%20Possession.gif)


### Day 42: February 23, Thursday

#### Today's Progress
1. Fixed an issue with Possession Model position offset in fixed joints

#### Thoughts
Took me longer than I would care to admit to realize I needed to move one line of code down 2 lines, but I finally fixed the issue. Had to rotate first, THEN calculate the offset or visa versa. Can't do both calculations then both assignments or they'll get wonky.

Also, I'm under the weather, so I don't have much stamina for further work tonight.

#### Link(s) to work
[Fixed Offset Commit](https://github.com/bjennings76/unity-vr-puppeteer/commit/36ab8cdcc6a368862b136c160349f7b924802ebd)


### Day 43: February 25, Saturday

#### Today's Progress
1. Implemented backdrop swapping
2. Refactored the Prop class a bit to better handle special-case props like the backdrop.

#### Thoughts
I'm up way too late, especially since I still have a cold, but it was fun to work through the various changes necessary to allow the special cases of backdrops to work with the prop system. The additions have improved and actually simplified the system in some places which is a pleasant surprise.

#### Link(s) to work
![Background Swapping](Captures/Day%20043%20-%20Background%20Swapping.gif)


### Day 44: February 27, Monday

#### Today's Progress
1. Tried out backdrops with 3D assets - almost worked without changes!
2. Made changes to remove interaction from backdrops so I will no longer accidentally grab them after they are placed.

#### Thoughts
Man, that cold really knocked me out over the weekend, but I'm feeling much better now. Glad to be making some progress again. (I do wish I would start it a bit earlier though so I could get myself some more sleep.)

#### Link(s) to work
![3D Backdrops](Captures/Day%20044%20-%203D%20Backgrounds.gif)


### Day 45: February 28, Tuesday

#### Today's Progress
1. Refactored the Prop/PropSlot class relationships a bit so the Prop handles more of it's own stuff
2. Got the BackdropProp to tween itself into place nicely

#### Thoughts
It was nice to clean up the code a bit. PropSlot, BackdropProp, and Prop classes are all under 100 lines now and still read well, I think. There was some inheritence trickery I wasn't happy with regarding overriding a lower-level method so it wouldn't play a specific default transition. Not sure how to cleanly handle it, though. I'll need to noodle on that for a bit longer.

I did notice I sorta ruined the 2D background line-ups, though. I'll have to look at what's going on with that tomorrow.

#### Link(s) to work
[Backdrop Transitions Commit](https://github.com/bjennings76/unity-vr-puppeteer/commit/cda92b428057eb3f8055eaa3676b7c26a8c74863)


### Day 46: March 1, Wednesday

#### Today's Progress
1. Continued yesterday's work with cleaning up the background transisions

#### Thoughts
I think the transitions are in a good place! Tomorrow I'll look into better item attachement and interactions with the hands.

#### Link(s) to work
![Backdrop Transitions](Captures/Day%20046%20-%20Smooth%20Background%20Transitions.gif)


### Day 47: March 3, Friday

#### Today's Progress
1. Upgraded VRTK to v.3.1.0

#### Thoughts
Wasn't able to get too much done except a bit of house keeping.

#### Link(s) to work
[VRTK Upgrade Checkin](https://github.com/bjennings76/unity-vr-puppeteer/commit/5c2295f6d3d6fac4fdfc0f93c6b574d999e8f88b)


### Day 48: March 4, Saturday

#### Today's Progress
1. Implemented 'maintain offset' in VRTK scripts

#### Thoughts
I needed to re-implement my 'maintain offset' option into the new VRTK scripts. Did a much better job this time around. May submit it as an option to the VRTK repo when I get a chance.

#### Link(s) to work
[Maintain Offset in VRTK Snap Checkin](https://github.com/bjennings76/unity-vr-puppeteer/commit/8ecce4cbccea800a3d56a09bf53e3e5e6fd164ef)


### Day 49: March 6, Monday

#### Today's Progress
1. Some bug fixes in the main scene

#### Thoughts
Not much work today, alas. Was able to check in a fix for the scene, though.

#### Link(s) to work
[Main Scene Fixes Checkin](https://github.com/bjennings76/unity-vr-puppeteer/commit/8ecce4cbccea800a3d56a09bf53e3e5e6fd164ef)


### Day 50: March 7, Tuesday

#### Today's Progress
1. Added `UnlockOnThrow` component to allow simple props to lock in place or be thrown based on release velocity

#### Thoughts
The `UnlockOnThrow` component works fairly well, but it break the weapon props snapping into puppet hands. I'll need to figure that out next time.

#### Link(s) to work
[UnlockOnThrow Component Checkin](https://github.com/bjennings76/unity-vr-puppeteer/commit/eef7d39989d6078f2c06853605d88af436713c36)


### Day 51: March 20, Monday

#### Today's Progress
1. Upgraded VRTK to latest in github repo

#### Thoughts
Was on vacation for a week (plus a bit of Zelda time, truth be told). It made for a nice little mid-way break, but now I'm back and ready for action.

#### Link(s) to work
[VRTK Upgrade Checkin](https://github.com/bjennings76/unity-vr-puppeteer/commit/09c13000a6bf5236066107769f30f2ffdee0ed36)
