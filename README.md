This is a sandbox mod about Manaka posting lewd photos of herself online.
She must build her fanbase to earn RP while hiding her identity.
It is inspired by Snapchat, Onlyfans, and other exhibition games :)

Requires CustomMissionsv2
https://f95zone.to/threads/secret-flasher-manaka-custom-missions-1-2-0-version-2-0-3.263276/
and Hunted
https://f95zone.to/threads/secret-flasher-manaka-custom-missions-1-2-0-version-2-0-3.263276/post-19194156

This mod not possible without the efforts of others developers. I have sometimes copied their code without permission, but here are their credits:
<details>
<summary>Credits:</summary>

  ```
FansChat v15, Nn312
    https://f95zone.to/threads/secret-flasher-manaka-custom-missions-1-2-0-version-2-0-3.263276/post-20060245

Hunted, TimeForAdventure
    developer : hacumefetitopikt.com
    https://f95zone.to/threads/secret-flasher-manaka-custom-missions-1-2-0-version-2-beta-0-5-5.263276/post-19194156

Custom Missions V2 examples
    developer : Crisp2002
    https://f95zone.to/threads/secret-flasher-manaka-custom-missions-1-2-0-version-2-beta-0-5-5.263276/
  ```
</details>

# General Gameplay

Open FansChat in Messenger. Click "Photo Now" to immediately post a photo using the current camera angle.
Or you can press V on keyboard to take photo instantly from current camera angle.
RP Score is awarded based on:
-How many lewd conditions are visible in the photo, and how visible they are
- How risky the photo is
- How many fans Manaka has

Manaka must conceal her identity while doing so! 
In v16, that means
- Either keeping her face out of view,
- Wearing masks, glasses or veils,
- Changing location each photo.

The presence and visibility of almost every generic exposure condition is checked, such as:
- Toys, eg vibrators
- Poses, eg Dogeza
- Cosplay sets, eg Tactical Maid set
- Situations, eg light/dark/near npc/busy area
- NPCs being in view, looking at Manaka, and/or between Manaka and the Cammera,
- Actions eg using vending machine, holding vibrator remote

# Mechanics
<details><summary>Conditions</summary>
  
The mod uses a large and complex table of conditions and their RP awards. You can view/modify this in ConditionRewards.code
The condition RP is loosely based on:
  
- How different conditions stack (eg coat-dropped vs exposed, watched vs showing off ),
- How rare/difficult some actions are.
- Photos taken at home cannot be scored.
- Some conditions reduce the RP score, such as being invisible
- Currently this system does not handle negative conditions eg "!Exposed_Front", so if you add these conditions, they may get scored incorrectly.
- If the condition does not include "Expose" or "Vis", then it assumes exposure is not a requirement, and visibility check is skipped (maximum visibility points are awarded)
  
</details>

<details><summary>Visibility</summary>
  
Conditions should only be scored if they are visible in the photo ... right?
Therefore a set of visibility checks occur to make sure each condition is viewable in the camera. Non-visible conditions are not scored.
  
- eg. before recording any Exposed_Hip conditions, the system checks if her hip is in frame, and if she is either facing the camera or crouched.
- Visibility also acts as a multiplier for the conditions' RP reward: Taking a photo of M's vibrators in center frame awards more points than if they are at the edge of the view.
- Zoom level also affects RP reward: Close ups increase the multiplier, but Long-shots show more conditions.
- Conditions that "protrude" from Manaka's silhouette get a visibility bonus, such as Tails or Futanari, making them easier to score.

The visibility is fundamentally flawed in some circumstances. This is partly due to limitations of the game, CustomMissionsv2, and my competance. For this reason some conditions pass visibility checks much too easily, while others seem impossible.
When those situations are identified, i have tried to make them More Visible.
</details>

<details><summary>Abstract Risk</summary>
  
This is an RP multiplier that is the average of Manakas Detection rating and RP multiplier.
High Detection = more RP.
High RP multipler = more RP.
If Manaka is wearing a low-detection Cosplay and not many mutator/modifier skills are used, the photo will score very low.
</details>

<details><summary>Anonymity and Hunters</summary>
  
If Manaka's identity OR location are exposed, she may attract Hunters.
This can either cause new hunters to spawn closeby, or attract distant hunters to the location.
Additionally all photos have a very small chance to attract hunters randomly, based on Manaka's face coverage/identity.
  
**Identity**

- Either keep Manaka's face out of view when taking photo, or
- wear masks, glasses, veils etc.
- The Anonymity gauge is shown when FanChat app is open, or when photo is taken.
- The level of required face cover is configurable in settings.
- In general, a higher anonymity means lower chance of attracting hunters.
  
**Location**

- When a photo is taken, a blue circle area is shown. A new circle is added every time a photo is taken.
- If you take another photo while inside or touching ANY circle, you will trigger a Hunter risk check.
- This will cause the circles to flash Magenta, and will stay visible until the next safe photo is taken.
- Blue circles will go invisible over time, but you can check them by opening FansChat.
- in v16, the only way to clear all the circles is to return Home.

**Hunter Chat**

- When Manaka has triggered a hunter spawn, they may send provocative messages.
- These are visible in the Stalker chat.
- A distinct notification sound plays when this occurs, and Manaka should run away quickly!

Hunter integration added by Nn312 in Fanschat v14
</details>

<details><summary>Fans</summary>
  
- RP reward for photos is increased based on the number of Fans.
- As Manaka posts photos, she will build Hype.
- When Hype reaches maximum, she is awarded with more Fans, and the Hype meter resets.
- Hype also resets when returning home.
- Hype gain is based on the single highest valued condition in the photo.
- Hype gain is opposed by 'fan boredom', an optional setting that penalises low-scoring photos.
- 
</details>

<details><summary>VIP Requests (by Nn312) </summary>
  
Every time Manaka takes a photo, there is a chance for VIP fans to make a special request.
Think of it like a bounty system: It is a special exposure mission with specific conditions required, and a high RP reward.
- VIP requests are shown as a mission in the top right corner of the screen.
- When Manaka is meeting the required conditions, a VIP Camera Focus meter appears.
- Use the VIP Camera Focus Meter to maximise your RP!
- The amount of conditions requested, and their risk, increases with Flasher Rank.
- Despite our best efforts, some impossible condition combinations still occur :(
- Some VIP Requests seem too difficult. Consider changing your active skills or Cosplay in order to complete them, but remember - Detection and RP Multiplier also apply to the VIP reward :)
- You can remove a VIP request by going to the FansChat app and clicking Deny Request. The penalty is 100 RP, and lose 10% of Fans.
- Experimental HARD MODE in settings enabled a specifically curated list of experimental conditions and cosplays. Some of them don't actually work, but when they do its very difficult!

</details>




### Developers
- there is now a mainLoop (and several other loops) at the bottom of mainThread, to centralize polling etc
- added some globals for useful parts of Fanschat. Sorry i haven't figured out Events yet. Some of them work like getters & setters, others are more read-only:
```
    FC.fans  # Manaka's current fandom
    FC.fans_hype  # Manaka's current hype. At (200+rank) she will gain a percentage of Hype added to Fans.
    FC.photoCool  # Manaka's camera's current Heat. This counts upward to _settings.photoCooldown, so 0 means a photo was taken this frame.
    FC.anonymity # Manaka's most recent Anonymity rating, updated 10 times per second.
    FC.viewCurrent  # List of Manaka's most recent view ratings for every body area, updated 10 times per second, at the same time as anonymity. The values are 0 or less if the part is not visible. See Visibility.Code.
    FC.scoreTable  # The big data object containing all of the conditions FanChat uses.
```
