---
layout: page

category: "Examples"
category_lead:  "XML File Examples"
title:  "Race for Victory 3"

---

[<i class="fa fa-share right-ref-link"></i>](/modules/main)
Specify the XML file version and then open the main map module and specify the maps name, version and objective.

    <?xml version="1.0"?>
    <map proto="{{site.current_proto}}">
    <name>Race for Victory 3</name>
    <version>1.2.9</version>
    <objective>Take the enemy's wool located to either side of the enemy's base and place it in your victory monument.</objective>

<br/>
Specify the maps authors and contributors. Each author and contributors `contribution=""` attribute is set to their specific contribution to the map.

    <authors>
        <author uuid="3c7db14d-ac4b-4e35-b2c6-3b2237f382be" contribution="map design and master gardener"/> <!--  MonsieurApple  -->
        <author uuid="ef4ea031-998f-4ec9-b7b6-1bdd428bcef8" contribution="map design and code memorization"/> <!--  Plastix  -->
        <author uuid="82c796a5-c033-43be-af30-fa06496995f9" contribution="map design and beautification"/> <!--  IM_A_H0B0  -->
    </authors>
    <contributors>
        <contributor uuid="25961a08-c90c-4abd-b136-dad90e89c2eb" contribution="item management and shenanigan manager"/> <!--  Anxuiz  -->
        <contributor uuid="3a549b18-08ed-4756-a78c-b34d29a4fd87" contribution="portals and various aesthetics"/> <!--  Torn_Ares  -->
        <contributor uuid="4a0780d3-d9c4-41c4-a816-e077a36f27c9" contribution="words"/> <!--  KasiCrafter  -->
    </contributors>

<br/>
[<i class="fa fa-share right-ref-link"></i>](/modules/tutorial)
Setup the tutorial module by including its default settings from the `tutorial.xml`, and then specify each of the points of interest on the map.

    <include src="tutorial.xml"/>
    <tutorial>
        <stage title="Capture the Wool">
            <message>
                <line>`rThis map is a `a`lCapture the Wool `r(CTW) map</line>
                <line>The objective is to grab the wool on the other team's side and return it to your base.</line>
            </message>
            <teleport>
                <point yaw="90" pitch="50">44,60,0</point>
            </teleport>
        </stage>
        <stage title="Blue Team Base">
            <message>
                <line>`rThis is the `9Blue Team `rbase. You spawn with gear ready to go into battle!</line>
                <line>You can use the water portals on either side to quickly exit the base.</line>
                <line>The chests contain extra supplies to help you build defenses or bridge to the enemy side.</line>
            </message>
            <teleport>
                <point yaw="180">0.5,2,102</point>
            </teleport>
        </stage>
        <stage title="Iron Supplies">
            <message>
                <line>Here is the iron supply for `9Blue Team`r. Note that `cRed Team `rhas the same thing on their side.</line>
                <line>You can craft iron armor to prepare yourself for battle.</line>
            </message>
            <teleport>
                <point yaw="35" pitch="30">14,25,63</point>
            </teleport>
        </stage>
        <stage title="Red Wool Rooms">
            <message>
                <line>These are `cRed Team`r's wool rooms housing `alime`r, `dpink`r, and `6orange`r.</line>
                <line>`9Blue Team `rhas `5purple`r, `eyellow`r, and `3cyan `rwools.</line>
                <line>`cRed Team`r should defend these rooms against `9Blue Team`r invaders who are trying to steal the wool and make it back alive.</line>
                <line>There are special goodies inside that will help you fight your way out.</line>
            </message>
            <teleport>
                <point yaw="-107" pitch="10">-115,22,-95</point>
            </teleport>
        </stage>
        <stage title="Victory Monument">
            <message>
                <line>This is one of three of `9Blue Team`r's victory monuments.</line>
                <line>The three colored wools from the `cRed Team`r's wool rooms must be placed in the victory monuments for the match to end.</line>
                <line>Note that `cRed Team`r has three identical victory monuments for their respective wools.</line>
            </message>
            <teleport>
                <point yaw="0">0.5,15,137</point>
            </teleport>
        </stage>
    </tutorial>

<br/>
[<i class="fa fa-share right-ref-link"></i>](/modules/teams)
Define two teams, their [colors](/reference/formatting#chatColors) and names.

    <teams>
        <team id="blue-team" color="blue" max="50">Blue Team</team>
        <team id="red-team" color="dark red" max="50">Red Team</team>
    </teams>

<br/>
[<i class="fa fa-share right-ref-link"></i>](/modules/spawns)
Specify spawns for the two teams.

    <spawns>
        <spawns kit="spawn">
            <spawn team="blue-team" yaw="180"><cylinder base="0.5,2,91.5" radius="5" height="0"/></spawn>
            <spawn team="red-team" yaw="0"><cylinder base="0.5,2,-90.5" radius="5" height="0"/></spawn>
        </spawns>
        <default yaw="270"><cylinder base="44.5,8,0.5" radius="4" height="0"/></default>
    </spawns>

<br/>
[<i class="fa fa-share right-ref-link"></i>](/modules/kits)
Team spawn kits, both teams get the same kit.

    <kits>
        <kit id="spawn">
            <item slot="0" material="iron sword"/>
            <item slot="1" enchantment="arrow infinite:1" material="bow"/>
            <item slot="28" material="arrow"/>
            <item slot="2" enchantment="durability:3;dig speed:1" material="iron pickaxe"/>
            <item slot="3" material="iron axe"/>
            <item slot="4" amount="64" damage="1" material="log"/>
            <item slot="5" amount="64" material="glass"/>
            <item slot="6" material="bucket"/>
            <item slot="7" material="golden apple"/>
            <item slot="8" amount="64" material="cooked fish"/>
        </kit>
    </kits>

<br/>
[<i class="fa fa-share right-ref-link"></i>](/modules/filters)
Create several filters including a no-void filter.

    <filters>
        <deny id="no-void"><void/></deny>

        <team id="only-red">red-team</team>
        <team id="only-blue">blue-team</team>

        <not id="only-red-usage">
            <all>
                <any>
                    <material>chest</material>
                    <material>workbench</material>
                    <material>trap door</material>
                </any>
                <team>blue</team>
            </all>
        </not>
        <not id="only-blue-usage">
            <all>
                <any>
                    <material>chest</material>
                    <material>workbench</material>
                    <material>trap door</material>
                </any>
                <team>red</team>
            </all>
        </not>
    </filters>

<br/>
[<i class="fa fa-share right-ref-link"></i>](/modules/regions)
Define all the regions, since the playing area of this map is pretty complex there are lots of regions and combinations of regions.

    <regions>
        <union id="portals">
            <circle center="-48.5,-90.5" radius="8"/>
            <circle center="49.5,-90.5" radius="8"/>
            <circle center="0.5,-139.5" radius="8"/>
            <circle center="49.5,91.5" radius="8"/>
            <circle center="-48.5,91.5" radius="8"/>
            <circle center="0.5,140.5" radius="8"/>
        </union>

        <!-- void protection -->
        <apply block="no-void" message="You may not edit the void area">
            <region>
                <negative>
                    <rectangle min="-14,-12" max="15,13"/>
                    <region id="portals"/>
                </negative>
            </region>
        </apply>

        <!-- portal protections -->
        <apply block="never" region="portals"/>
        <apply block="never" message="You may not modify your supply room">
            <region>
                <complement id="blue-supplies">
                    <circle center="0.5,91.5" radius="22"/> <!-- circle encompassing the entire base -->
                    <cylinder base="0.5,7,91.5" radius="19" height="8"/> <!-- defines the area where iron can be gotten -->
                </complement>
                <complement id="red-supplies">
                    <circle center="0.5,-90.5" radius="22"/> <!-- circle encompassing the entire base -->
                    <cylinder base="0.5,7,-90.5" radius="19" height="8"/> <!-- defines the area where iron can be gotten -->
                </complement>
            </region>
        </apply>

        <!-- the wools red has to get -->
        <union id="red-wool-rooms">
            <circle id="yellow-island" center="-83.5,91.5" radius="11"/>
            <circle id="purple-island" center="84.5,91.5" radius="11"/>
            <circle id="cyan-island" center="0.5,175.5" radius="11"/>
        </union>

        <!-- the wools blue has to get -->
        <union id="blue-wool-rooms">
            <circle id="orange-island" center="84.5,-90.5" radius="11"/>
            <circle id="lime-island" center="-83.5,-90.5" radius="11"/>
            <circle id="pink-island" center="0.5,-174.5" radius="11"/>
        </union>

        <!-- the blocks outside of blue's wool rooms -->
        <complement id="outside-yellow">
            <circle center="-83.5,91.5" radius="14.9"/>
            <region id="yellow-island"/>
        </complement>
        <complement id="outside-purple">
            <circle center="84.5,91.5" radius="14.9"/>
            <region id="purple-island"/>
        </complement>
        <complement id="outside-cyan">
            <circle center="0.5,175.5" radius="14.9"/>
            <region id="cyan-island"/>
        </complement>

        <!-- the blocks outside of red's wool rooms -->
        <complement id="outside-orange">
            <circle center="84.5,-90.5" radius="14.9"/>
            <region id="orange-island"/>
        </complement>
        <complement id="outside-lime">
            <circle center="-83.5,-90.5" radius="14.9"/>
            <region id="lime-island"/>
        </complement>
        <complement id="outside-pink">
            <circle center="0.5,-174.5" radius="14.9"/>
            <region id="pink-island"/>
        </complement>

        <!-- wool room rules -->
        <apply block="only-blue" use="only-blue-usage" region="blue-wool-rooms"/>
        <apply enter="only-blue" region="blue-wool-rooms" message="You may not enter your own wool room."/>
        <apply block="only-red" region="red-wool-rooms" use="only-red-usage"/>
        <apply enter="only-red" region="red-wool-rooms" message="You may not enter your own wool room."/>

        <!-- spawn rules -->
        <apply enter="only-blue" message="You may not enter the enemy spawn.">
            <region>
                <circle center="0.5,91.5" radius="22"/> <!-- circle encompassing the entire base -->
            </region>
        </apply>
        <apply enter="only-red" message="You may not enter the enemy spawn.">
            <region>
                <circle center="0.5,-90.5" radius="22"/> <!-- circle encompassing the entire base -->
            </region>
        </apply>

        <!-- no block placement outside wool rooms -->
        <apply block="never">
            <region>
                <region id="outside-yellow"/>
                <region id="outside-purple"/>
                <region id="outside-cyan"/>
                <region id="outside-orange"/>
                <region id="outside-lime"/>
                <region id="outside-pink"/>
            </region>
        </apply>
    </regions>

<br/>
[<i class="fa fa-share right-ref-link"></i>](/modules/portals)
Specify the team base portals and where they link from. There are two portals out of each team base and one back inside.

    <portals>
        <!-- portals in red base -->
        <portal x="-33" y="7">
            <cuboid min="-12,2,-92" max="-11,5,-89"/>
        </portal>
        <portal x="33" y="7">
            <cuboid min="12,2,-92" max="13,5,-89"/>
        </portal>

        <!-- portals in blue base -->
        <portal x="33" y="7">
            <cuboid min="12,2,90" max="13,5,93"/>
        </portal>
        <portal x="-33" y="7">
            <cuboid min="-12,2,90" max="-11,5,93"/>
        </portal>

        <!-- portal back to blue base -->
        <portal filter="only-blue" z="-33" y="-13">
            <cuboid min="-1,15,134" max="2,18,135"/>
        </portal>

        <!-- portal back to red base -->
        <portal filter="only-red" z="34" y="-13">
            <cuboid min="-1,15,-134" max="2,18,-133"/>
        </portal>
    </portals>

<br/>
[<i class="fa fa-share right-ref-link"></i>](/modules/repair_remove_keep)
Specify that iron swords, diamond pickaxes, iron axes, and bows get repaired when dropped or when the player picks one up. Since the player only needs one arrow because the bows are enchanted with `infinite:1` arrows are also specified here. This prevents players from collecting huge stacks of arrows and spewing them all over on death. Repairing arrows instead of removing them also has the advantage of the player being able to accidental drop a arrow and not lose it.

    <toolrepair>
        <tool>iron sword</tool>
        <tool>iron pickaxe</tool>
        <tool>iron axe</tool>
        <tool>bow</tool>
        <tool>arrow</tool>
    </toolrepair>

<br/>
[<i class="fa fa-share right-ref-link"></i>](/modules/repair_remove_keep)
Remove specific items when they get dropped to prevent the map from getting cluttered.

    <itemremove>
        <item>log</item>
        <item>wood</item>
        <item>bucket</item>
        <item>cooked fish</item>
        <item>golden apple</item>
        <item>glass</item>
        <item>seeds</item>
        <item>sugar cane</item>
        <item>string</item>
        <item>glowstone dust</item>
    </itemremove>

<br/>
[<i class="fa fa-share right-ref-link"></i>](/modules/other_settings)
The maps max build height in blocks.

    <maxbuildheight>40</maxbuildheight>

<br/>
[<i class="fa fa-share right-ref-link"></i>](/modules/gamemode_ctw)
Specify a Capture the Wool type game, and the locations where the wools have to be placed by each team.

    <wools>
        <wool team="red-team" color="purple">
            <block location="-49,10,-91"/>
        </wool>
        <wool team="red-team" color="yellow">
            <block location="49,10,-91"/>
        </wool>
        <wool team="red-team" color="cyan">
            <block location="0,16,-140"/>
        </wool>
        <wool team="blue-team" color="lime">
            <block location="49,10,91"/>
        </wool>
        <wool team="blue-team" color="orange">
            <block location="-49,10,91"/>
        </wool>
        <wool team="blue-team" color="pink">
            <block location="0,16,140"/>
        </wool>
    </wools>

<br/>
Close the main `<map>` module.

    </map>
