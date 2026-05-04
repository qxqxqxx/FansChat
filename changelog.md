# Fanschat v16
## by eicosa
	General
	- SETTINGS including
	- LOCALIZATION v1! After changing language, please toggle the FansChat mod Off and On using the tickbox in the phone. Not everything is translated correctly, just some phone messages VIP request.
	- Text_CN.code is ai-translated from english, hopefully Nn312 or someone can fix
	- Flasher Rank-based progression, for newgames. Rank ranges from 0 to 7

	FansChat
	- Press V on keyboard to take photo immediately without opening phone. You can change the key in settings.code, where it says photoInput = CreateInput("<Keyboard>/v")
	- Camera flash and sound effect
	- Camera is on a cooldown
	- Flasher Rank now effects/scales many mechanics
	- Fans increase (Hype) is now based on the single highest scoring condition in the photo
	- Hype requires buildup to a threshold before it awards anything. This is a design choice to require some consistency with staying in an area and taking photos. 
	- Hype Amount required increases with Rank
	- RP scores revised and a limit is imposed based on Rank. Don't worry, this mod still makes the progression way faster in newgame+.

	VIP requests
	- Added more conditions requests, including a few Cosplay Sets.
	- VIP Condition requests are now gated by Flasher Rank, to reduce the chance you are asked to do something impossible.
	- Condition score now affected by risk (RP-factor and Detection-factor)
	- Condition validity and score now affected by Visibility
	- When the VIP request condition is valid, eg a special mission bar is displayed showing how 'in view' the required conditions are.
	- More filtering is done on conditions, but there is still some impossible combinations.
	- Reduced the default score from 300 to 100, added it to meta settings. 
	- Overall, VIP requests now have more variety and risk/reward. The highest RP i've earned from a single photo in this version of Fanschat was nearly 1000 RP, even with the score basis reduced.
	- Experimental "HARD MODE" toggle, which currently forces a small set of specifically risky conditions, as well as cosplay sets.
	- You can DENY Vip Requests in the phone. It costs 100 RP and you will lose 10% of your fans.

	Visibility
	- NPC Visibility!@! Due to technical limitations, an NPC can only be visible in photo if they are in frame, AND any of these are true:
		- They can see Manaka,
		- are between Manaka and the Camera,
		- are within 4 meters of Manaka.
	- Visibility calculations now include camera distance, with the resulting dynamic:
	- a zoomed out shot includes many body parts in one photo, but reduces score by 50%
	- a zoomed in shot excludes most body parts from the photo, but increases score by up to 50% (usually 20 to 30%)

	Hunter Integeration
	- New message notification sound for stalker messages, taken from SFM game files thanks Nn312.
	- Hunter spawn distance moved a bit further away, and it is no longer possible for 2 to spawn at once.
	- Instead, there is a 50% chance of existing hunters being immediately alerted to your location.
	
	Anonymity.
	- Anonymity Meter! Now displays anonymity when photo is taken or FansChat app is open.
	- Anonymity Zones! Taking photos twice in the same zone has a high chance of attracting/spawning Hunters. 
	- Zones are shown when you take a photo, or open the FansChat app, or have triggered hunters. 
	- Zones are blue if your last taken photo was outside of the zone, implying you are safe.
	- Zones are flashing magenta if your last taken photo inside the zone, potentially triggering hunters.
	- There is currently no particular way to wipe the Zones clear except changing map.
	- Anonymity rating no longer REQUIRES multiple faces items.
	- Anonymity rating now just adds up the highest of each face region. 

	Developers
	- there is now a mainLoop (and several other loops) in mainThread, to centralize polling etc
	- added some globals for useful parts of Fanschat. Some of them work like getters & setters, others are more read-only:
		FC.fans  # Manaka's current fandom
		FC.fans_hype  # Manaka's current hype. At (200+rank) she will gain a percentage of Hype added to Fans.
		FC.photoCool  # Manaka's camera's current Heat. This counts upward to _settings.photoCooldown, so 0 means a photo was taken this frame.
		FC.anonymity # Manaka's most recent Anonymity rating, updated 10 times per second.
		FC.viewCurrent  # List of Manaka's most recent view ratings for every body area, updated 10 times per second, at the same time as anonymity. The values are 0 or less if the part is not visible. See Visibility.Code.
		FC.scoreTable  # The big data object containing all of the conditions FanChat uses.

# Fanschat v14
## by Nn312
	First ever localization: Translated to CN

	Added VIP request system
	- when photo is scored, VIP might make a request
	- randomly picks up to 4 conditions from several categories
	- score depends on amount of conditions, and their severity

	Includes a suffix+prefix chat response system with localisation option via Text_EN.code

	Added Hunted mod integration with Anonymity, thanks to Hunted support from hacumefetitopikt
	- When Manaka shows her face, Hunters have chance to move to her location
	- Hunters will send provocative messages to "stalker" chat when your anonymity is compromised

# Fanschat v12
## by eicosa
	Initial public release
	- FansChat.code
	- original spaghetti logic, todo and wishlist comments

	ConditionRewards.code
	- included huge collection of conditions and subconditions, see MakeScoreTable, AppendScoreTable, DefaultScoreTable
	- included photo (snapshotdata) rp scoring logic in ScoreSnapshotData
	- included 'visibility' checking logic inside ConditionsToSnapshotData

	Anonymity.code
	- original logic for checking if Manaka's face is hidden by items
	- item coveraged rated independently across 3 regions - mouth, eyes, hair - and required at least two to be covered

