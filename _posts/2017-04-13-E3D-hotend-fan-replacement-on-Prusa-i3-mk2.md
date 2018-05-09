---
layout: post
title:  "E3D hotend fan replacement on Prusa i3 mk2"
date:   2017-04-13 18:29:00 +0200
categories: electronics 3D-printing
---
So my Prusa i3 MK2 is printing just fine and I get awesome results with PLA and nGen. But two things are missing to be an perfect printer which is living room compatible.

The y-axis in comparison to the x- and z-axis is really loud. A few days ago I read on the Prusa website about an upgrade kit which includes new rods and bearings to eliminate this issue. So I will keep this in mind until the lead time is acceptable.

Second thing is the fan from the E3D hotend. It is an 30x30 fan which runs in full turbine mode. After reading in the forum I stumbled about a post with other users which had the same problem. One critical point was getting the same airflow as the small fan, so the hotend doesn't clog during print. I found an nice 40x40x10 Noctua fan which fits my needs. It runs on 12V, creating an airflow of 8.2m³/h with an acoustical noise of 17.9dB(A).

For the adapter my co-worker printed an nice adapter in orange ABS (<a href="http://www.thingiverse.com/thing:1827477">http://www.thingiverse.com/thing:1827477</a>).
<h2>Upgrade</h2>
[caption id="attachment_477" align="alignnone" width="300"]<a href="https://cronj.de/2017/04/13/e3d-hotend-fan-replacement-on-prusa-i3-mk2/img_20170410_182444129/"><img class="wp-image-477 size-medium" src="https://cronj.de/wp-content/uploads/2017/04/IMG_20170410_182444129-300x225.jpg" alt="" width="300" height="225" /></a> fig. 1 - Removing the old fan[/caption]

[caption id="attachment_478" align="alignnone" width="300"]<a href="https://cronj.de/2017/04/13/e3d-hotend-fan-replacement-on-prusa-i3-mk2/img_20170410_182827316/" rel="attachment wp-att-478"><img class="wp-image-478 size-medium" src="https://cronj.de/wp-content/uploads/2017/04/IMG_20170410_182827316-300x225.jpg" alt="" width="300" height="225" /></a> fig. 2 - Mounting the adapter[/caption]

The old fan was unscrewed and removed. With three M3x18 screws I mounted the new fan adapter.

[caption id="attachment_479" align="alignnone" width="300"]<a href="https://cronj.de/2017/04/13/e3d-hotend-fan-replacement-on-prusa-i3-mk2/img_20170410_183255189/" rel="attachment wp-att-479"><img class="size-medium wp-image-479" src="https://cronj.de/wp-content/uploads/2017/04/IMG_20170410_183255189-300x225.jpg" alt="" width="300" height="225" /></a> fig. 3 - Mounting the new fan[/caption]

Now I attached the new fan to the adapter. Be careful with the length of your screws. If your screws are to long they will damage the other fan.

[caption id="attachment_480" align="alignnone" width="300"]<a href="https://cronj.de/2017/04/13/e3d-hotend-fan-replacement-on-prusa-i3-mk2/img_20170410_183741331/" rel="attachment wp-att-480"><img class="wp-image-480 size-medium" src="https://cronj.de/wp-content/uploads/2017/04/IMG_20170410_183741331-300x225.jpg" alt="" width="300" height="225" /></a> fig. 4 - Connecting the fan[/caption]

With my new fan came a short cable with a three pin connector. I removed the spiral wrap on the cables until I could get the fan cable plus the connector cable in there. The old fan wires where cut. Then I soldered the connector cable on the old wires and isolated the two wires from another.

[caption id="attachment_481" align="alignnone" width="300"]<a href="https://cronj.de/2017/04/13/e3d-hotend-fan-replacement-on-prusa-i3-mk2/img_20170410_183956791/" rel="attachment wp-att-481"><img class="wp-image-481 size-medium" src="https://cronj.de/wp-content/uploads/2017/04/IMG_20170410_183956791-300x225.jpg" alt="" width="300" height="225" /></a> fig. 5 - Spiral wrap attached again[/caption]

For the last step I reattached the spiral wrap on all the cables. Check that the cable doesn't touch the heated bed.
<h2>Noise level</h2>
Now that the fan noise is vanished the printer is really quiet. Only on the bed leveling procedure the y-axis makes noises. But now that the printer is so quiet I located a rattling noise which seems to come from the extruder. It only occurs some times during print and I couldn't locate it further. I reassembled all the screws on the extruder, because it sounds like a loose nut. But this doesn't help. I fastened the screws which mount the new fan which seems to fix it. But some times it occurs again.

But aside from that the printer now is quiet enough during print.
