# PiVault Documentation
If you have issues or questions not answered within this document, please join our [Discord-Community](https://discord.gg/MrNb9CQyYA).<br>

---
Please use the Table of contents below to navigate this document.
##  Table of Contents
1. General Interface
    <br>1.1. Advanced Settings
    <br>1.2. Hygiene Opening Settings
    <br>1.3. Unlock Settings
    <br>&nbsp;&nbsp;&nbsp;&nbsp;1.3.1 Timed Unlock
    <br>&nbsp;&nbsp;&nbsp;&nbsp;1.3.1 Unlock Now
    <br>&nbsp;&nbsp;&nbsp;&nbsp;1.3.1 Allow Unlock
---
## 1. General Interface
![PiVaultMainScreen](https://i.imgur.com/YevmxH0.png)
| Nr. | Name                         | Description                                                            |
|-----|------------------------------|------------------------------------------------------------------------|
| 1   | Add Button                   | Click to add a Lockbox / add a keyholder code                          |
| 2   | Own Lockbox Button           | Click to View the interface for your Lockbox                       |
| 3   | Shared Lockboxes             | Lockboxes you have a share code for will be listed below               |
| 4   | Hygiene Button               | Click to Access the Settings for Hygiene Opening                       |
| 5   | Unlock Button                | Click to Access the Unlock Options                                     |
| 6   | Time Control Button          | Click to Access the Time configuration                                 |
| 7   | "Locked Since" Timer         | Displays how Long the Lockbox has been locked                          |
| 8   | "Unlocks at" Timer           | Displays the date and time the Lockbox will unlock at                  |
| 9   | "Time Left" Timer            | Displays the time till the Lockbox will unlock                         |
| 10  | Last Opened                  | Displays the time since the Lockbox was last Opened                    |
| 11  | Last Closed                  | Displays the time since the Lockbox was last Closed                   |
| 12  | "Public Links" Button        | Click to Access the Public Link Interface                              |
| 13  | "Keyholder" Button           | Click to Access the Keyholder Settings                                 |
| 14  | "Additional Settings" Button | Click to Access the Additional Settings for the Lockbox                 |
| 15  | Lockbox Log                  | Lists all events reported by the lockbox (Open, Close, Emergency, etc) |
---
### 1.1 Advanced Settings
![PiVaultAdvancedSettings](https://i.imgur.com/VbA4k4w.png)
| Nr. | Name                    | Description                                                                      |
|-----|-------------------------|----------------------------------------------------------------------------------|
| 1   | Rename Button           | Click to change the Name of the Lockbox                                          |
| 2   | Wifi Settings Button    | Click to change the Wifi Settings                                                |
| 3   | Transfer Button         | Click to Unbind the PiVault from your Account and allow Ownership transfer to another User. **WARNING: This is only Intended for Transfering Ownership of the PiVault (eg. when selling it) *NOT* for giving another user control, to give another user control, see Keyholder codes / Public Links described further below**                                                              |
| 4   | Limits Button           | Click to Access the Limits Settings                                              |
| 5   | Emergency Unlock Toggle | Click to toggle between enabling and disabling the Emergency Unlock Function     |
| 6   | PiVault ID              | Your PiVault ID; Required for Certain API Applications as well as Troubleshooting |
---
### 1.2. Hygiene Opening Settings
![PiVaultHygieneOpeningSettings](https://i.imgur.com/5tVaWjx.png)
| Nr. | Name                                  | Description                                                      |
|-----|---------------------------------------|------------------------------------------------------------------|
| 1   | Enable Hygiene Opening Settings         | Click to Enable / Disable Hygiene Opening                         |
| 2   | Hygiene Opening day Configuration      | Click to set on which days Hygiene Opening will be allowed        |
| 3   | Hygiene Opening Time Configuration     | Click to set at which time Hygiene Opening will be allowed        |
| 4   | Hygiene Opening Duration Configuration | Click to set for which duration Hygiene Opening will be allowed   |
| 5   | Cancel Button                         | Click to cancel the changes to the Hygiene Opening Configuration  |
| 6   | Set Button                            | Click to confirm the changes to the Hygiene Opening Configuration |

**Please note that this configuration is based on the local timmezone of the PiVault**

---
### 1.3. Unlock Options
#### **1.3.1** Timed Unlock

![PiVaultUnlockTimed](https://i.imgur.com/LFpDSU7.png)

Timed unlock allows you to specify a Time window up to 60 Minutes in the future at which the PiVault will allow unlocking for 3 seconds by pressing the button on the device.

| Nr. | Name              | Description                                                                                                             |
|-----|-------------------|-------------------------------------------------------------------------------------------------------------------------|
| 1   | Enable Buzz       | Click to Enable / Disable Buzz when the PiVault is ready to unlock                                                      |
| 2   | No Reset          | Click to Enable Preserving the session. Unlocking with this option checked will Preserve the currently running session. |
| 3   | Time till unlock | Click to set the time in minutes until the PiVault will unlock for 3 seconds.                                          |
| 4   | Cancel Button     | Click to Cancel the Unlock                                                                                              |
| 5   | Confirm Button     | Click to Confirm the configuration and to start the timer.                                                                              |

#### **1.3.1** Unlock Now

![PiVaultUnlockNow](https://i.imgur.com/nNZk3cW.png)


| Nr. | Name              | Description                                                                                                             |
|-----|-------------------|-------------------------------------------------------------------------------------------------------------------------|
| 1   | Enable Buzz       | Click to Enable / Disable Buzzing from the PiVault to Signal that it is ready to unlock                                                  |
| 2   | No Reset          | Click to Enable Preserving the session. Unlocking with this option checked will Preserve the currently running session. |                                         |
| 3   | Cancel Button     | Click to Cancel the Unlock                                                                                              |
| 4   | Confirm Button     | Click to Confirm the configuration and to Unlock                                                                              |

#### **1.3.1** Allow Unlock

The "Allow Unlock" function allows the PiVault to be unlocked once at any point once it has been enabled. <br>
Using this allows Keyholder to give the sub the option to unlock themselfs at what ever time they choose. 

![PiVaultUnlockAllow](https://i.imgur.com/TC7DkN6.png)

| Nr. | Name              | Description                                                                                                             |
|-----|-------------------|-------------------------------------------------------------------------------------------------------------------------|
| 1   | Enable Buzz       | Click to Enable / Disable Buzzing from the PiVault to Signal that it is ready to unlock                                                  |
| 2   | No Reset          | Click to Enable Preserving the session. Unlocking with this option checked will Preserve the currently running session. |                                         |
| 3   | Cancel Button     | Click to Cancel the Unlock                                                                                              |
| 4   | Confirm Button     | Click to Confirm the configuration and to Unlock      
