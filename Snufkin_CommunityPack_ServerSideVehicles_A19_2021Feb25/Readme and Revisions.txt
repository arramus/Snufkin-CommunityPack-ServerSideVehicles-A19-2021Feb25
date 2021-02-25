----------------------------------------------------------------------------------
Snufkin's Community Pack Server Side Vehicles (A19 - Stable) 25th of February 2021
----------------------------------------------------------------------------------

==========
BACKGROUND
==========
By utlizing in game assets without any need for external additions, Snufkin was able to create new vehicles by using an innovative approach of attaching prefabs and other effects to existing vehicles. In some cases you will recognise the base model, as with the Hell Beast motorcycle. However, other vehicles will only use a stock vehicle as base and appear totally unique in form and function, such as the parachute.

Other modders are heeding Snufkin's call for the community to exploit the xmls and create their own versions. This Community Pack compiles a variety of new creations as well as tweaks to the original existing code to ensure context and stability.

The current vehicle list, which can be produced on the workbench is as follows:

Armored Car - 4 seater (Snufkin)
Army Truck - 6 seater (Snufkin with stability and context edits by oakraven)
Raft - 4 seater (Snufkin)
Sled - 1 seater (Snufkin with additional comfort by oakraven)
Jet Pack - 1 seater (Snufkin)
Hell Beast - 2 seater motorcycle (Snufkin)
Parachute - 1 seater (Snufkin)
ATV - 2 seater motorcycle (Snufkin with functionality fix by oakraven)
Hell Hound 4x4 - 6 seater (oakraven)
Hell Fire - 2 seater motorcycle (oakraven)
Hell Spikey 4x4 - 6 seater (oakraven)
Hell Dog - 2 seater motorcycle (oakraven)
Shark Blimp - 2 seater (oakraven)
Whirligig - 3 seater 'chopper' (arramus, with 100% credit to Snufkin for the concept and supporting code as well as bdubyah for permission to use the settings for the MD-500 helicopter from Bdub's Vehicles - https://community.7daystodie.com/topic/11875-a19-bdubyahs-modlets/)
Magic Bus - 6 seater (oakraven)
Battle Bus - 6 seater (oakraven)
Hell Car - 4 seater (oakraven)
Bath Blimp - 1 seater (arramus)
Battle Bus Drone - 6 seater (oakraven with arramus assisting)
PeNa 1979 Express - 4 seater (oakraven) - Thank you to PeNa1979 for gameplay assistance.
Psyren Ride - 4 seater (oakraven)
Green Max - 4 seater (oakraven)
Red Max - 4 seater (oakraven)
Hell Piggy - 2 seater (oakraven)

-------------------------
Restoring the mod for A19
-------------------------
Issue 1
recipes.xml
meleeThrownSpearSteelParts

The dedicated server produces this warning:

2020-10-09T15:20:45 111.077 ERR XML loader: Loading and parsing 'recipes.xml' failed
2020-10-09T15:20:45 111.077 EXC No item/block/material with name 'meleeThrownSpearSteelParts' existing
Exception: No item/block/material with name 'meleeThrownSpearSteelParts' existing
  at RecipesFromXml+<LoadRecipies>d__1.MoveNext () [0x00499] in <9f04a0ee08f84f3794a7468a839f2bb0>:0 
  at ThreadManager+<CoroutineWrapperWithExceptionCallback>d__40.MoveNext () [0x00044] in <9f04a0ee08f84f3794a7468a839f2bb0>:0 
UnityEngine.DebugLogHandler:Internal_LogException(Exception, Object)
UnityEngine.DebugLogHandler:LogException(Exception, Object)
UnityEngine.Logger:LogException(Exception, Object)
UnityEngine.Debug:LogException(Exception)
Logger:masterLogException(Exception)
Logger:Exception(Exception)
Log:Exception(Exception)
<>c__DisplayClass50_0:<loadSingleXml>b__2(Exception)
<CoroutineWrapperWithExceptionCallback>d__40:MoveNext()
UnityEngine.SetupCoroutine:InvokeMoveNext(IEnumerator, IntPtr)
 
(Filename: <9f04a0ee08f84f3794a7468a839f2bb0> Line: 0)

As the 'meleeThrownSpearSteelParts' no longer exists, it is commented out and replaced with 'meleeToolAllSteelParts' in

recipes.xml
recipe name="HellBeast"

from

<!--ingredient name="meleeThrownSpearSteelParts" count="10"/--> to
<ingredient name="meleeToolAllSteelParts" count="10"/>
--------------------------------
Issue 2
recipes.xml
meleeToolWrench

As with Issue 1 and with the same resolution.
--------------------------------
Issue 3
recipes.xml
gunJunkTurretParts

As with Issue 1 and commented out and changed to:

<ingredient name="gunBotRoboticsParts" count="40"/>
--------------------------------
Issue 4
Xui warning about inventory for "CustonVehicles"

2020-10-09T15:20:55 121.098 WRN XML patch for "XUi/windows.xml" from mod "CustonVehicles" did not apply: <set xpath="/windows/window[@name='windowVehicleStorage']/grid[@name='inventory']/@rows" 
2020-10-09T15:20:55 121.098 WRN XML patch for "XUi/windows.xml" from mod "CustonVehicles" did not apply: <set xpath="/windows/window[@name='windowVehicleStorage']/grid[@name='inventory']/@cols" 

Deleted.
--------------------------------
Issue 5 (Reported by h0tr0d and fixed for functionality by oakraven)
Warning with collision for Army Truck

Non-convex MeshCollider with non-kinematic Rigidbody is no longer supported since Unity 5.
If you want to use a non-convex mesh either make the Rigidbody kinematic or remove the Rigidbody component. Scene hierarchy path "Entities/Cars/Army Truck_256087/Physics/Box1/tempPrefab_armyTruckPrefab/armyTruck", Mesh asset path "" Mesh name "army_truck_collider"

Changed:
items.xml
<property name="Meshfile" value="#Entities/Vehicles?Truck/armyTruckPrefab.prefab"/>
to
<property name="Meshfile" value="#Entities/Vehicles?jeep_Prefab.prefab"/>

While the warning persists until the collision in the model can be updated, it is now as easy to place as any other vehicle. This method can also be applied for additional vehicles added to the mod that present similar collision issues but can retain functionality such as the Magic Bus by oakraven.