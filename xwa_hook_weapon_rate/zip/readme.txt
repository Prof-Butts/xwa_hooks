xwa_hook_weapon_rate

This hook permits to define weapon decharge and recharge rates for any craft.


*** Requirements ***

This dll requires:
- Windows 7 or superior
- xwa_hook_main


*** Setup ***

Place hook_weapon_rate.dll next to xwingalliance.exe


*** Patch ***

The following modifications are applied at runtime to xwingalliance.exe:

# To call the hook that defines weapon decharge and recharge rates
At offset 090A51, replace A1C4337B008A54080484D2 with E8CA741100E98000000090.
At offset 08FCCE, replace 6683FA0574096683FA078D1436 with 52E84C8211005A0FAFD6EB0690.
At offset 090C66, replace A1FC0D910083FBFF with E8B5721100EB2990.


*** Usage ***

Suppose that the craft is "FlightModels\[Model].opt".

To define the decharge and recharge rates, create a file named "FlightModels\[Model]WeaponRate.txt" or create a section named "[WeaponRate]" in "FlightModels\[Model].ini".
The format is:
DechargeRate = decharge value
RechargeRate = recharge value
CooldownTimeFactor = cooldown time value

If the file does not exist, default values are used.

By default, the decharge rate is controlled as this:
if the ship category is Starfighter,
  if the craft is TieFighter or TieBomber, the decharge rate is 3,
  else the decharge rate is 4.
else
  if the weapon sequence is < 4, the decharge rate is 3,
  else there is no decharge.

By default, the recharge rate is controlled as this:
if the craft is TieFighter or TieBomber, the recharge rate is 3 * PresetLaser,
else the recharge rate is 2 * PresetLaser.

The default value for CooldownTimeFactor is 47.

See TieFighterWeaponRate.txt and TieBomberWeaponRate.txt.


*** Credits ***

- Jérémy Ansel (JeremyaFr)
