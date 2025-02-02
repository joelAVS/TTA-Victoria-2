# Gondor Flavor

[Workflow Graph](https://drive.google.com/file/d/1nMP0vgwSdBK1PY2o1YaHXS6ZTQbiMbjH/view?usp=sharing) - will want to open with diagrams.net

### Pops
	D�nedain represents the direct descendents of N�menor, those individuals with little-to-no blood of lesser men in their familial history
	Gondorian/Amrothian represents those who identify as Gondorians but are mixed blood of the Daen and N�menoreans
		Amrothian is it's own culture as Dol Amroth will have a path that allows them to secede from Gondor (and lose Gondorian as accepted)
	Dr�edain represents the Dr�edain in Gondor - most are in Dr�edan Forest or Dr�waith Iaur
	Dunir represents the Wild Men of Andrast and Anfalas who have not assimilated into Gondorian society
	Wildmen represents the other Wild Men in Gondor that have not assimilated into Gondorian society. They purposefully don't have a tag to promote assimilation
		Those around Ethir Anduin are the remnants of the Ethir Folk
		Those in the steppes of Harondor are the remnants of the D�nan
	Harnendan represents those who of a mixed blood between Gondorian and Haradrim, but are not the descendents of the followers of Castamir


### Possible Leaders
	Each leader has a flag stating if they are adults. Ecthelion II and Denethor II are alive at the start of the game
	Boromir II and Faramir II are born about 20 years into the game, and 16 years after their birth, become generals. At this point they are considered alive

	Generic Leader
	Ecthelion II (starting)
	Denethor II
	Boromir II
	Faramir I
	Aragorn Elessar II


### Substate Annexation
	Starts feudalized
	Decisions lead down centralization - the AI will not annex Dol Amroth if railroading is enabled
	
	If Tolfalas is denied, Dol Amroth will have the potential to revolt
		Decision da_independence_war kicks it off with event 50001
		Events 50002 and 50003 handle the end of the war
	
	If Gondor attempts to annex Dol Amroth via flavor, Dol Amroth will have the potential to rebel
		Event 50004 to Dol Amroth (to make decision)
		Event 50005 if they accept
		Event 50006 if they refuse
	
	Global Flags:
		no_tolfalas_for_da
			Gets set if Gondor annexes Tolfalas
			Allows Dol Amroth to declare independence
		
		da_independence_war
			Gets set if Dol Amroth attempts to declare independence, either by Tolfalas or refusing to be flavor-annexed
			Functions to ensure that DA can't spam the decision
			Also handles the end of the war
	
	Adds Generals:
		Forlong, Lord of Lossarnach (annex_lossarnach)
		Angbor, Lord of Lamedon (annex_lamedon)
		Duinhir, Lord of Blackroot Vale (annex_lamedon)
		Borhador, Lord of Ringl� Vale (annex_lamedon)
		Hirluin, Lord of Pinnath Gelin (annex_anfalas)
		Golasgil, Lord of Anfalas (annex_anfalas)
	
	Adds Admirals:
		Orodreth, Lord of Lebennin (annex_lebennin)


### Province Flavor
	Handles decisions related to specific provinces that don't fall nicely into other categories
	
	Minas Tirith (16): Houses of Healing, Collage of the Spoken Word
	Ithilduin (204): Restore/Destroy Crossroads of the Fallen King
	Dr�edain Forest (7): Share/Hide Stonewain Valley
	West Osgiliath (14): Rebuild Osgiliath, Rebuild Dome of Stars
	East Osgiliath (198): Rebuild Osgiliath
	
	Ithilien: Repopulate Ithilien
	
	Wool and Horse provinces: Expand the Mesta


### Military Build Up
	Handles Gondor dealing with low military recruitment
	
	Mainly there because Gondor would be unstoppable without starting debuffs
	
	Country Flags:
		low_military_recruitment
			Starts out with the flag
			Is paired with a modifier as modifier checks don't always work

### Expansion to the West
	Handles Gondor's flavor for expanding into Dr�waith Iaur and Andrast
	Gondor must have solved it's recruitment issues
	
	Andrast:
		Event 150000 starts the war(s)
	
	After Gondor annexes the region, if a Dr�edain majority province gets made enough that is a PUK core, Dr�waith Iaur can rebel
		Event 150002 sets it up to begin
		Event 150003 spawns in an army for PUK and starts the war
		If Gondor wins, it starts working on Gondorification, removing PUK cores and adding GON cores once complete
	
	Dr�adan Forest can rebel if still majority Dr�edain and militancy gets high enough
		Event 150007 sets it up to begin
		Event 150008 spawns an army for DRU and starts the war
		If Gondor wins, it starts working on Gondorification, removing DRU cores once complete
	
	Dr�waith Iaur:
		War to make PUK a puppet
		Also has other wars to free PUK land held by other realms
			Event 150009 starts these wars

	Global Flags:
		GON_andrast_war
			Functions as a stopgap to prevent the AI from spamming the decision
		
		GON_puppet_druwaith_iaur
			Functions as a stopgap to prevent the AI from spamming the decision
			
		annexed_druwaith_iaur
			Gets set when the flavor to annex Dr�waith Iaur fires
			Is one of the requirements for the Dr�edain Rebellion
			
		PUK_rebellion
			Gets set when PUK rebels
			Gets cleared after the war ends
		
		DRU_rebellion
			Gets set when DRU rebels
			Gets cleared after the war ends
	
	Country Flags:
		andrast_gondorification
			Gets set when Gondor attempts to increase colonial migration to the Andrast region
			Used to remove PUK cores when stating
			
		PUK_rebelling_from
			Used to target the former owner of PUK. Most likely will be Gondor
			Gets cleared after the war ends
		
		DRU_rebelling_from
			Used to target the former owner for DRU. Most likely will be Gondor
			Gets cleared after the war ends


### Expansion to the South
	Handles Gondor's flavor for expanding into Harondor
	Gondor must have solved it's recruitment issues
	
	Gondor's Harondor puppet starts in Benish Armon and Methir
		Harondor can start annexing adjacent empty provinces by event 50038
		Any Harondor core owned by Gondor will be given to Harondor by event 50039
	Gondor will get a free cb on any realm that holds Harondor provinces
		Event 150001 starts the wars
	
	When all HRD cores have been reclaims, Gondor can annex HRD
	When all HRD cores are states, Gondor can accept Harnendan
	When a tech level is reached, can improve farming output of the region
	
	Country Flags:
		south_gondor_gondorification
			Gets set when Gondor annexes HRD
			Used to remove cores when stating


### Reintigration of Rohan
	Happens when Rohan and Gondor have opposite alignments, or if Gondor turns evil
	
	Gondor gets cores on all Rohan cores, and can get a prestige and immigration boost when successful
	
	Country Flags:
		GON_reclaimed_calednardhon
			Gets set when Gondor claims the region
			Used to check if center of the realm can be used


### Generic Political Flavor
	Call the Council of Gondor:
		Once per leader
		Decreases militancy
	
	Declare the Steward King:
		Can only happen while a stewardship
		Turns the realm into a kingdom
		Will cause a second kin-strife
		
	Visit the Tomb of Elendil:
		Once per leader
		Decreases consciousness
	
	Restore the Huadh-in-Gwanur:
		Increases relations with Rohan
			
	Light the Beacons:
		Sends a request to Rohan to ally and join wars if alignments are not opposite
		Fires event 50020

	Country Flags:
		leader_visited_tomb_of_elendil
			Cleared when the next leader ascends
		
		lit_the_beacons
			Cleared when all current wars are done
			
	Global Flags:
		restored_the_haudh_in_gwanur


### Ecthelion II Flavor
	Flavor that happens that needs Ecthelion II as the realm leader
	
	Encourage Outside Military Recruitment:
		Boosts the military and helps to get rid of low military recruitment
		
	Fund Ithilien Rangers:
		Counters most of the effects of Orc raids in Ithilien

	Global Flags:
		gondor_prepared_coastal_defences
			Set when the decision is taken
			Never cleared

### Events
	50000 - Allows Gondor to decide what happens to Tolfalas
	50001 - Starts Dol Amroth's independence war if Gondor refuses to give them Tolfalas
	50002 - Finishing event if Dol Amroth wins
	50003 - Finishing event if Gondor wins
	50004 - Event asking Dol Amroth if they consent to being annexed
	50005 - Dol Amroth accepts
	50006 - Dol Amroth refuses
	50007 - Imrahil is born (Dol Amroth)
	50008 - Denethor marries Finduilas (Gondor)
	50009 - Denethor marries Finduilas (Dol Amroth)
	50010 - Boromir is born (will only happen after marriage)
	50011 - Faramir is born (will only happen after Boromir is born)
	50012 - The Service of Thorongil
		Will only happen if Gondor is encouraging outside military recruitment, and if Ecthelion II is leader
	50013 - Renaming of Dol Calemir to Lornost
		Dol Calemir needs a fort for this to happen
	50014 - Juggling School of Cabed Angren
	50015 - Ambush in Ithilien
		Needs to have funded the Ithilien rangers and that a neighboring country is evil
	50016 - Setup the second Kin-Strife to occur
	50017 - Starts the second Kin-Strife
	50018 - Citizens of Minas Tirith go gather flowers from Tumladen
	50019 - Diplomatic feast in the Merethrond
	50020 - The Beacons are lit! Asks Rohan for aid in their wars
	
	#### Switch from Ecthelion II to Denethor II
	 - Triggered by Ecthelion II's old age in the 2980s
	50021 - The Death of Ecthelion II
	50022 - Invite's allies and puppets to Ecthelion II's funeral and Denethor II's coronation
	50023 - The Coronation of Denethor II
	
	Country Flags:
		Sets knows_next_leader to ensure the system doesn't set the leader as generic_leader
			Also sets it for all substates with Ecthelion II as leader
			All get cleared when the leader has died event fires (3501)
		Sets leader_interim so that things that can be done once per leader cannot be done twice for Denethor II
			Also sets it for all substates with Ecthelion II as leader
			Gets cleared when Denethor II becomes the leader
	
	Global Flags:
		Clears ecthelion_ii_alive, marking him as dead
	
	#### The Death of the Lords of Gondor
	 - Triggered by their old age
	50024 - The death of Farlang and the New Lord of Lossarnach
	50025 - 50024 for the overlord (if existing)
	50026 - The Death of Asgon and the New Lord of Lamedon
	50027 - 50026 for the overlord (if existing)
	50028 - The Death of Borhador and the New Lord of the Ringl� Vale
	50029 - 50028 for the overlord (if existing)
	50030 - The Death of Duinmir and the New Lord of the Blackroot Vale
	50031 - 50030 for the overlord (if existing)
	50032 - The Death of Hirgon and the New Lord of Pinnath Gelin
	50033 - 50032 for the overlord (if existing)
	50034 - The Death of Gundor and the New Lord of Anfalas
	50035 - 50034 for the overlord (if existing)
	
	Global Flags:
		Sets forlong_lord_of_lossarnach
			To determine in annex_lossarnach which general to give Gondor
		Sets angbor_lord_of_lamedon
			To determine in annex_lamedon which general to give Gondor
		Sets dervorin_lord_of_the_ringlo_vale
			To determine in annex_lamedon which general to give Gondor
		Sets duinhir_lord_of_the_blackroot_vale
			To determine in annex_lebennin/annex_lamedon which general to give Lamedon/Gondor
		Sets hirluin_lord_of_pinnath_gelin
			To determine in annex_anfalas which general to give Gondor
		Sets golasgil_lord_of_anfalas
			To determine in annex_anfalas which general to give Gondor
	
	50036 - Noble Houses Fighting
	50037 - A Game of Dallok
	
	#### Expansion in Harondor
	50038 - Allows Harondor to claim a neighboring empty province
	50039 - Gives all Harondor cores owned by Gondor to HRD
	
	50040 - Emergence of the Mesta
	
	150000 - Starts the Andrast Wars
	150001 - Starts Gondor's wars liberating South Gondor's cores
	150002 - Setups PUK's rebellion
	150003 - Starts PUK's rebellion
	150007 - Setups DRU's rebellion
	150008 - Starts DRU's rebellion
	150009 - Starts the Dr�waith Wars
	
	Global Flags:
		birth_of_imrahil
		wedding_denethor_finduilas
		birth_of_boromir
		birth_of_faramir
		the_mesta_covers_anfalas
