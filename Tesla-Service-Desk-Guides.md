# Tesla service desk guides

October 2026. Desk reference only. Not a repair procedure. Menus change with software. Toolbox for that VIN wins.

On an iPhone: open this page in Safari, tap Share, then Print, then pinch out and save as PDF.

---

# 1. Isolation faults

How the car finds a leak, which codes matter, and what to write on the ticket.

## Say it this simply

The strong electricity that moves the car has to stay inside its own path, like juice in a straw. Isolation means that juice does not touch the metal body. If the wall between them gets a hole — water, a cracked cable, a wet plug — the car stops charging or driving so nobody gets a shock. It is being careful, not stubborn.

## How the car finds it

A tester inside the battery computer sends a very small signal from the high-voltage wires toward the body. It is not the driving current. If almost nothing leaks across, the car is fine. If some of that signal sneaks through, the car measures how bad the leak is, remembers whether it is the plus side or the minus side, and sets a warning. It may refuse to drive or charge.

**Open contactors or closed.** The pack contactors are the big switches between the battery and the rest of the car.

- Open: only the battery is in the test. If the leak is still there, the hole is inside the pack.
- Closed: motors, charger, heater, compressor, and orange cables are included. Fine when open and bad when closed means the hole is outside the battery.

**How a technician finishes the hunt.** They read the resistance, which side, and whether the pack alone is guilty. Then they disconnect high-voltage parts one at a time and test again: rear drive unit, front drive unit, heater, A/C compressor, charge port. The moment the leak disappears, the last part unplugged is the failed part. If the leak is inside the pack, they look for water, old coolant, corrosion, or damaged insulation. Eyes matter too: cracked orange cable, a soggy charge port, chewed wires, green crust on a connector.

You do not unplug orange connectors, run an insulation tester, or clear isolation counters to get the car out the door. High voltage can kill. Your job is the exact code, the story, and the right bay: pack, external high voltage, or drive unit.

## Read the code before you say battery

The same number with w, a, or f is one family at different severity, not a different part. w may still drive. a limits the car. f has already shut something down. Do not tell a w customer they are fine.

**BMS_a123 / w123 / f123 — SW_Internal_Isolation.** Contactors open. Leak is in the circuit with the rest of the car disconnected. Treat it as the HV battery until a tech proves otherwise. Often "Unable to charge." Do not quote a cable or a compressor.

**BMS_a035 / w035 / f035 — SW_Isolation.** Contactors closed. Below the hard limit. Tesla’s own text says external or internal. A BMS code is not a battery verdict. Screen: "Vehicle may not restart." Need an open-contactor reading before anyone picks a part.

**BMS_a151 / w151 / f151 — SW_external_isolation.** Contactors closed. Pointed outside the pack: compressor, PTC or coolant heater, charge port, charger / DC-DC, drive unit, orange harness. Screen: "Vehicle may not restart." Book external HV, not a pack quote.

**BMS_a142 — SW_Isolation_Degradation.** Contactors just closed. Under the warning line, still above the stop-the-car line. The quiet early leak. Often stamped at the end of a Supercharge. One hit can fade. A repeat is real. Usually no message. Ask for the kΩ number and whether every DC session does it.

**BMS_a027 / w027 / f027 — Repeated isolation failure in drive.** Many drive cycles. This is the escalation, not the first blip. Capture a companion BMS_a170. Do not guess that code. Screen: "Power limited — OK to drive" and "may not restart after this drive." Same day. Tow if it already will not restart.

**BMS_w172 — SW_Drive_Iso_Warning, often with BMS_u008.** A drive-unit leak wearing a battery code. On 2012–2020 S/X the usual cause is coolant past the rear large-drive-unit rotor seal. Ask about coolant top-offs. Write "rule out rear LDU before the pack."

**BMS_a037 — SW_Flood_Port_Open.** The pack drain is open. Not the ohms reading itself. It is the door the water used. More common on 3/Y and 2021+ S/X. Older S/X 85 packs leak through breather valves and show up as the a035 family instead. Ask flood, deep water, underbody wash, and the date.

Clearing counters is not a repair. The car retests at power-up.

## Traps

- a035 does not mean "external only," and it does not mean "battery." Open-versus-closed decides.
- a123 with the contactors open is the pack until someone proves it is not.
- w172 is a motor. Classic S/X, rear large drive unit, coolant loss with no puddle under the car.
- a142 is the quiet one. No screen message. Ignore the repeats and it grows into a027.
- a027 means it already failed a lot. "It still drives" is not an all-clear.
- A dead 12-volt beside an isolation alert is usually the victim. Note both. Do not replace the 12-volt and release the car.
- "We cleared it" is not a fix.

**These are not isolation**

- BMS_a066, then a064, then a079: cell imbalance. Range cut, sometimes near half.
- BMS_a017: a brick went over-voltage.
- BMS_a166, or older BMS_w152 / w153: welded contactor.
- BMS_f038 / w026: stuck contactor, mostly older S/X.
- BMS_w107 / f107: voltage-sense harness tabs.

## What their sentence is telling you

- "May not restart" — a035, a151, or a027. Are they still driving, or is it already parked?
- "Will not charge, still drives" — a123, or water in the charge port. Home AC, Supercharger, or both?
- "Only when I unplug a Supercharger" — a142. Screenshot of the kΩ, and does every DC session do it?
- "Only with heat or A/C on" — PTC heater on older cars, or the compressor. Does it start during precondition?
- "Only after rain or a car wash" — charge port or a harness. Does the charge-port door latch?
- "Old S/X, coolant goes down, power reduced" — w172 / rear LDU. Sweet smell, top-offs, isolation alert yet?
- "Flood, deep puddle, wet carpet" — a037 plus an isolation code. What date?

## Put this on the ticket

Exact alert names, letter included, plus anything cleared in the last 30 days. Isolation resistance with contactors open and closed, and the timestamp. When it sets: key-on, after a drive, end of DC charge, HVAC on, rain. AC, DC, or both. Coolant loss, sweet smell, underbody wash, flood, body shop, or a replaced orange cable. Model and year. On 2012–2020 S/X the first line is "rule out the rear LDU before the pack." The customer’s words.

Healthy isolation is usually several thousand kΩ. A degradation warning is often under about 1,000 kΩ. A hard fault is lower. A legacy Model S bulletin treated open-contactor isolation under about 1,800 kΩ as a pack problem. Those are the scale techs see, not a spec. PTC heaters and compressors are insulation-tested much lower than a charge port. "Megger everything at 1,000 V" can destroy a good compressor.

**Priority.** a123, f035, f151, or an a027 that already will not restart: tow. Do not ask them to try charging again. a035 or a151 "may not restart": same day, and tell them the next Park may stick. A single a142 with no message after one Supercharge: note it and watch. Do not scare them into a pack quote.

---

# 2. Legacy Model S and X (about 2012–2020)

Phone card for older owners. Say it in short sentences.

Ask this before you name a part: year, whether the screen computer says NVIDIA Tegra or Intel Atom (Controls, then Software, then Additional vehicle information), the words on the screen, and whether it still drives.

## The screen is slow, frozen, or black

On a Tegra car, built before about March 2018, the memory chip behind the screen wears out. That was recall 21V-035. The free repair replaces the chip. It does not turn the car into a newer computer. A paid Intel upgrade is a different job. That upgrade is what adds a usable phone key, Sentry, and a faster screen.

The car can usually still drive. They lose the backup camera, the defrost controls, and the click of the turn signal. Tell them not to install a software update if the screen is already dying. To reboot and get home: foot on the brake, hold both scroll wheels until the screen goes black, then let go. If it is black again the next morning, it needs the computer, not another reboot. A screen that still paints a picture but will not answer a finger is often the touch layer, not the memory chip.

## Keys

These cars use a fob, not a card. A Tegra car cannot use a phone as the key. An Intel car can. To add a fob they must already have one working key. On the screen: Controls, then Locks, then the key list, then add, then press a button on the new fob when it asks. A cheap fob from the internet often will not pair. If every fob is lost, only Tesla can pair a new one, and they will want proof of ownership.

A fob that works only when held against the door pillar needs a new coin cell, usually a CR2032. If the car suddenly wants a PIN, someone turned on PIN to Drive. A forgotten PIN is not a broken key. Service can clear it with proof they own the car. Do not have them guess.

## The small 12-volt battery

This is not the big battery that moves the car. It is often why the screens reboot, the handles stay in, the charge door will not open, and the frunk will not pop. Plan on a few years of life, not ten. If the frunk is shut and the 12-volt is dead, do not send an older owner into the wheel well to hunt for a cable. Send roadside. After a 12-volt replacement on a Model X, the falcon doors often need a calibration. Warn them before the repair.

## Model S door handles

Each handle has its own little motor. One dead handle is not a dead car. Use another door. In ice, do not pull on a handle that will not come out. A handle that keeps cycling can run the 12-volt flat. That one is a tow or a mobile visit, not "keep trying it."

## Model X falcon doors

Most "my door is possessed" calls are a block, a low 12-volt, or a lost calibration. Hats, garage rails, and items in the door pocket count as obstacles. Recalibrate from Controls, then Service. If a door stops halfway and will not move, leave it and call. Do not let them hang on the door.

## Air suspension

- One corner down after it sits: leak in that air spring. Do not drive it far on the bump stop. Note which corner and how fast it drops.
- Sinks overnight, all four: compressor, a line, or the dryer. A short drive is fine if it will still raise.
- Warning, stuck high: height sensor, a line, or the compressor. It will feel stiff. Come in slow.
- Unhappy only in a steep driveway: often normal. Give it a minute.
- Compressor runs for minutes: it is chasing a leak. Do not keep raising and lowering it to test.

The control module is not a swap-and-go part. It has to be programmed, and the ride height has to be calibrated.

## Coolant loss, a whine, then an isolation alert

On these years the rear motor can pull coolant in through a seal. The puddle is inside the motor, so they may never see one. The whine follows road speed. This is the BMS_w172 path. Say "the rear motor is the first suspect," not "you need a battery." Do not keep driving it if the coolant is low or the car has already said it may not restart.

## Charge door, heat, noises, range

Charge door will not open: dead 12-volt first, ice second, the latch third. There is a manual release in the trunk liner. If they are unsteady, roadside is safer. "Charging is slow" on a cold morning is often not a broken port.

No heat: these cars use an electric cabin heater, not a heat pump. The fan can blow and the air can still be cold. Weak cool air is often a cabin filter that has never been changed, or the compressor.

A click on takeoff, once per wheel turn, is often a half shaft. A clunk over bumps can be a lower link or ball joint. A creak from the glass roof in the sun is usually annoying, not dangerous. These cars wear the inner edge of the tires when alignment is off. A headlight that turns yellow on one side is a known aging item, not the big battery.

Some range loss after years is normal. A "battery needs service" message, a charge limit stuck near half, or a sudden fall of about 30 miles is not. BMS_a066, a064, and a079 are cell imbalance, not a leak to the body.

## The app and the map look dead

Many of these cars shipped with a 3G modem. That network is gone. Remote lock, live location, and streaming maps need the LTE upgrade. The car still drives. Bluetooth music still works.

## Autopilot and FSD

You are still the driver. If the car says take over, you take over. Dirty glass, low sun, and heavy rain will hand the car back. Wipe the camera at the top of the windshield before a visit.

- One camera, Mobileye, mostly 2014 through late 2016: this car cannot run today’s FSD. No software update changes that.
- Later camera cars can be fitted with the HW3 Autopilot computer if the owner bought FSD. A Tegra screen computer is not the computer FSD runs on. Current software wants the Intel screen computer.
- As of October 2026, HW3 cars with Intel screens are starting to get a lighter FSD, v14.3 Lite. It still will not start from Park, will not reverse itself, and does not get the arrival choices the newest cars get.
- HW3 will not do unsupervised driving. Tesla has said people who paid for FSD should get a future computer. Do not give a date.
- A yellow border or bubbles in the screen is the display aging. Separate from Autopilot.

**Normal, so do not book it.** A slight whine that rises with speed. A click as the brakes settle. The suspension adjusting in a steep driveway. Regen that feels weaker when the battery is full or very cold.

**Stop and tow.** Smoke. A sharp sweet smell. A battery or isolation warning. The car says it may not restart. A wheel tucked into the arch. A falcon door stuck in traffic. Steering that suddenly goes heavy.

**Ticket line.** Their words, plus Tegra or Intel, which door or which corner, coolant loss yes or no, home charge or Supercharger, and the exact sentence on the screen.

---

# 3. Newer cars

Model 3, Model Y, and Model S / X from 2021 on. The banner "Service is required" is useless without the alert name under the bell.

## No heat, no A/C, climate needs service

Model Y has had a heat pump from the start. Model 3 from about late 2020. A 2018 or 2019 Model 3 still has the older electric heater. Do not call that one a heat pump. On a heat-pump car the usual story is no heat in the cold, a loud compressor, a chemical smell, or the defrost giving up. Some 2021–2022 cars were in software recall 22V-063, a valve that stuck and killed the heat. Later failures are sensors, the valve block, or the compressor. They are not a dirty filter.

Ask whether they lost heat, A/C, or both, and whether it died while the cabin was preheating. A musty smell with the A/C still cold is usually the cabin filter and the evaporator. The fan can run and the air can still be dead.

## Clunk or squeak in a parking lot

Worse when cold, especially over a bump with the wheel turned: front upper control arm or its mount. This is the most common Model 3 and Model Y complaint. It can be noisy before it is loose. Do not call it "just the sound of an electric car." Note left or right, cold only or always, and whether the car wanders. Inner-edge tire wear means an alignment at the same visit.

A 2025–2026 Model Y clunk over small bumps has its own service bulletins. Some 2026 Model Ys were recalled for front suspension fasteners, 26V558. Check the VIN before you call a noise ordinary wear.

## Keys, pins, and stalkless cars

Newer cars use a phone and a card, not a fob. When the phone stops working, a phone update or a Bluetooth permission is more common than a broken car. Have them stand at the pillar, toggle Bluetooth, and try the card on the pillar. The card lives in the wallet, not in the car. A forgotten PIN to Drive or glovebox PIN can be cleared with proof of ownership. Do not guess.

A stalkless Highland or Juniper, and the refreshed S/X yoke, make people think the car will not start. The shifter is on the screen. The turn signals are on the wheel. Walk them through that before you book a dead car.

## The small battery

Early Model 3s used a normal 12-volt lead-acid battery. From about 2022, and on refreshed S/X, it is a lithium low-voltage battery. Do not send them to a parts store. Jump only from the posts in the manual, under the tow cover in the front bumper on a 3 or Y. The frunk will not open once that battery is flat.

## Charging

Often not a failure: regen is weaker when the battery is full or cold. Supercharging slows as the battery fills. A cold battery charges slowly until it warms. Scheduled charging sits there until the time they set. A third-party charger or a loose adapter causes more "it will not charge" calls than a bad port.

A handle that is hot, a charge that fails on every stall, or an isolation warning during a charge is real. Note AC, DC, or both.

## Cameras and FSD

You are still the driver. "Take over immediately" means take over. Sunglasses, a hat, or a tag over the cabin camera will nag them or shut assistance off. Clean the glass before a visit.

- HW3, mostly before early 2023: they get the lighter FSD, v14 Lite, not the full new stack. The computer can run warm. If Autopilot drops out until the car sits, note the temperature. Unsupervised driving is not coming to this computer. Do not give a date for a replacement.
- HW4 / AI4: full current FSD. Still supervised. A windshield replacement needs a camera calibration. Put the glass date on the ticket.
- No ultrasonic sensors, roughly late 2022 on: it will not beep like an older car. The picture on the screen is the parking aid. Do not book "backup sensors dead" on a car that never had them.

## Water, smells, and the little stuff

- Model 3 trunk wet after rain: a known seal and lamp path. Note which side.
- Fog inside a headlamp that clears is condensation. A pool of water in the lamp is a leak.
- Sentry overnight, not plugged in, can use several percent. That is not a failing big battery.
- A phone that cooks on the wireless pad: take it off the pad.
- Seatbelt chime with an empty seat: the occupancy mat.
- Wipers on a dry windshield, or silent in the rain: show them the manual speed before you replace hardware.

## A software update that will not finish

The small battery has to be healthy, the car in Park, and Wi-Fi is better than cell. Leave it on the cord overnight and stop tapping retry. If it has been stuck for days, or the screen boot-loops, then it is a ticket.

## Refreshed S and X air suspension

Same owner words as the old cars, different parts. One corner down after sitting is still a leak. A replacement control module still has to be programmed, and the height still has to be calibrated. A yoke and a tilting screen are not suspension problems.

## They scraped the bottom

If the car drives normally, with no smell and no new warning, it can be inspected. If they smell coolant, see fluid, or get an isolation or battery warning, they stop. Write the speed, and whether it was a speed bump, a curb, or debris.

**Stop and tow.** Smoke or a chemical smell from the heater. An isolation or battery warning. A wheel that looks out of place. Steering that suddenly goes heavy. A charge handle that is melting or too hot to hold.

**Ticket line.** Model and year. Heat pump or not. HW3 or HW4. The exact alert under the bell. Left or right. Cold or always. AC or Supercharger. Whether a windshield was replaced recently.
