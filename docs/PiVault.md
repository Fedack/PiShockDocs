# PiVault Documentation
If you have issues or questions not answered within this document, please join our [Discord-Community](https://discord.gg/MrNb9CQyYA).<br>

---
Please use the Table of contents below to navigate this document.
##  Table of Contents
1. General Interface
    <br>1.1. Advanced Settings
    <br>&nbsp;&nbsp;&nbsp;&nbsp;1.1.1 Limits
    <br>1.2. Hygiene Opening Settings
    <br>1.3. Unlock Settings
    <br>&nbsp;&nbsp;&nbsp;&nbsp;1.3.1 Timed Unlock
    <br>&nbsp;&nbsp;&nbsp;&nbsp;1.3.1 Unlock Now
    <br>&nbsp;&nbsp;&nbsp;&nbsp;1.3.1 Allow Unlock
    <br>1.4. Time Settings & Starting a Session
    <br>&nbsp;&nbsp;&nbsp;&nbsp;1.4.1 No Keyholder Mode
    <br>&nbsp;&nbsp;&nbsp;&nbsp;1.4.2 Hidden Timer
    <br>1.5. Public Links
    <br>&nbsp;&nbsp;&nbsp;&nbsp;1.5.1 Create / Modify Public Links
    <br>1.6. API Keys
    <br>1.7. Keyholder Codes
---
## PiVault General Operation
The button on the PiVault can serve 3 purposes:
Press Once, it will check if it can unlock, like after the session time is elapsed or keyholder allowed unlock.
Hold for 5 seconds, until the light flash, it will mute or unmute the PiVault.
Hold for 15 seconds and you will request an emergency unlock (if still enabled).

Once unlocked, you just need to twist the PiVault lid counter clockwise and pull up. To lock, put the lid back on, aligning the notch on the side of the lid with the rightmost dent in the base.


---
## 1. General Interface
![PiVaultMainScreen](https://i.imgur.com/1cMOCUC.png)
| Nr. | Name                         | Description                                                            |
|-----|------------------------------|------------------------------------------------------------------------|
| 1   | Add Button                   | Click to add a PiVault / add a keyholder code                          |
| 2   | Own PiVault Button           | Click to View the interface for your PiVault                           |
| 3   | Shared PiVaults              | PiVaults you have a share code for will be listed below                |
| 4   | Hygiene Button               | Click to Access the Settings for Hygiene Opening                       |
| 5   | Unlock Button                | Click to Access the Unlock Options                                     |
| 6   | Time Control Button          | Click to Access the Time configuration                                 |
| 7   | Clear Button                 | Click to immediately end the current session                           |
| 8   | "Locked Since" Timer         | Displays how Long the PiVault has been locked                          |
| 9   | "Unlock at" Timer            | Displays the date and time the PiVault will unlock at                  |
| 10  | "Time Left" Timer            | Displays the time till the PiVault will unlock                         |
| 11  | Last Opened                  | Displays the time since the PiVault was last Opened                    |
| 12  | Last Closed                  | Displays the time since the PiVault was last Closed                    |
| 13  | "Public Links" Button        | Click to Access the Public Link Interface                              |
| 14  | "API Codes" Button           | Click to Access the API Codes Interface                                |
| 15  | "Keyholder" Button           | Click to Access the Keyholder Settings                                 |
| 16  | "Additional Settings" Button | Click to Access the Additional Settings for the PiVault                |
| 17  | PiVault Log                  | Lists all events reported by the PiVault (Open, Close, Emergency, etc) |
---
### 1.1 Advanced Settings
![PiVaultAdvancedSettings](https://i.imgur.com/VbA4k4w.png)
| Nr. | Name                    | Description                                                                      |
|-----|-------------------------|----------------------------------------------------------------------------------|
| 1   | Rename Button           | Click to change the Name of the PiVault                                          |
| 2   | Wifi Settings Button    | Click to change the Wifi Settings                                                |
| 3   | Transfer Button         | Click to Unbind the PiVault from your Account and allow Ownership transfer to another User. **WARNING: This is only Intended for Transfering Ownership of the PiVault (eg. when selling it) *NOT* for giving another user control, to give another user control, see Keyholder codes / Public Links described further below**                                                              |
| 4   | Limits Button           | Click to Access the Limits Settings                                              |
| 5   | Emergency Unlock Toggle | Click to toggle between enabling and disabling the Emergency Unlock Function (Not visible if there are Keyholders and Emergency Unlock has been disabled) |
| 6   | PiVault ID              | Your PiVault ID; Required for Certain API Applications as well as Troubleshooting |

#### **1.1.1** Limits
![PiVaultLimits](https://i.imgur.com/aWobraz.png)<br>
| Nr. | Name                              | Description                                                         |
|-----|-----------------------------------|---------------------------------------------------------------------|
| 1   | Chastity Session Maximum Duration | Click to set the Maximum duration for a Session flagged as Chastity |
| 2   | Bondage Session Maximum Duration  | Click to set the Maximum duration for a Session flagged as Bondage  |
| 3   | Unlocked By Default Toggle        | Toggle if the PiVault is unlocked by Default (Default off)          |
| 4   | Close Button                      | Click to close the Limits Dialog                                    |
| 5   | Confirm Button                    | Click to Confirm the settings to the Limit Settings                 |

**Note: "Unlocked By Default" can only be changed when no keyholder is present. Limits can only be changed when no session is active.**

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

**Please note that this configuration is based on the local Timezone of the PiVault**<br>
**Note that during the Hygiene Window, the PiVault can be opened at any time, for any number of times. It is recommended to make the window as small as possible.**

---
### 1.3. Unlock Options
#### **1.3.1** Timed Unlock

![PiVaultUnlockTimed](https://i.imgur.com/LFpDSU7.png)

Timed unlock allows you to specify a Time window up to 60 **Seconds** in the future at which the PiVault will allow unlocking for 3 seconds by pressing the button on the device.

| Nr. | Name              | Description                                                                                                             |
|-----|-------------------|-------------------------------------------------------------------------------------------------------------------------|
| 1   | Enable Buzz       | Click to Enable / Disable Buzz when the PiVault is ready to unlock                                                      |
| 2   | No Reset          | Click to Enable Preserving the session. Unlocking with this option checked will Preserve the currently running session. |
| 3   | Time till unlock | Click to set the time in minutes until the PiVault will unlock for 3 seconds.                                          |
| 4   | Cancel Button     | Click to Cancel the Unlock                                                                                              |
| 5   | Confirm Button     | Click to Confirm the configuration and to start the timer.                                                                              |

#### **1.3.2** Unlock Now

![PiVaultUnlockNow](https://i.imgur.com/nNZk3cW.png)


| Nr. | Name              | Description                                                                                                             |
|-----|-------------------|-------------------------------------------------------------------------------------------------------------------------|
| 1   | Enable Buzz       | Click to Enable / Disable Buzzing from the PiVault to Signal that it is ready to unlock                                                  |
| 2   | No Reset          | Click to Enable Preserving the session. Unlocking with this option checked will Preserve the currently running session. |                                         |
| 3   | Cancel Button     | Click to Cancel the Unlock                                                                                              |
| 4   | Confirm Button     | Click to Confirm the configuration and to Unlock                                                                              |

Unlock Now will unlock the PiVault as soon as it polls. It will stay unlocked for up to 15 seconds or until it is opened.

#### **1.3.3** Allow Unlock

The "Allow Unlock" function allows the PiVault to be unlocked once at any point once it has been enabled. <br>
Using this allows Keyholder to give the sub the option to unlock Themselves at what ever time they choose. 

![PiVaultUnlockAllow](https://i.imgur.com/TC7DkN6.png)

| Nr. | Name              | Description                                                                                                             |
|-----|-------------------|-------------------------------------------------------------------------------------------------------------------------|
| 1   | Enable Buzz       | Click to Enable / Disable Buzzing from the PiVault to Signal that it is ready to unlock                                                  |
| 2   | No Reset          | Click to Enable Preserving the session. Unlocking with this option checked will Preserve the currently running session. |                                         |
| 3   | Cancel Button     | Click to Cancel the Unlock                                                                                              |
| 4   | Confirm Button     | Click to Confirm the configuration and to Unlock      

**Note: It is currently possible that a server restart wipes the unlock allowance. This will be changed in the future but currently allow unlock will not work beyond 6 hours at the maximum.**

---
### 1.4. Time Settings & Starting a Session

![PiVaultSessionSettings](https://i.imgur.com/4ATbuk4.png)
| Nr. | Name               | Description                                                                                                                                                             |
|-----|--------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 1   | Date / Time Picker | Select the Date the PiVault will unlock at, then select the time it will Unlock at (Note: After Selecting the Date, the Date Picker gets replaced with the Time Picker) |
| 2   | No Keyholder Mode  | Click to Enable "No Keyholder Mode"                                                                                                                                     |
| 3   | Hidden Timer       | Click to Enable "Hidden Timer"                                                                                                                                          |
| 4   | Cancel Button      | Cancel Setting the Duration                                                                                                                                             |
| 5   | Confirm Button     | Confirm Setting the Duration                                                                                                                                            |

#### **1.4.1** No Keyholder Mode
No Keyholder mode locks down the PiVault in such a way to allow for a Solo Session. <br>
While in No Keyholder Mode:
- You will not be able to add keyholders
- You will not be able to create new public links with the option to subtract time enabled
- You will not be able to unlock the PiVault until the set time has elapsed (Emergency / Hygiene Unlock will function regardless, Note that Hygiene Unlocks have to be set up before Session start)
- You will not be able to set/alter Hygiene unlock settings

#### **1.4.2** Hidden Timer
The "Hidden Timer" can be used to prevent the lockee/wearer from knowing how much time is remaining in a session. This can be enabled with "No Keyholder Mode" and enabled in a session already in progress.
While Hidden Timer is enabled:
- The lockee will see "Who Knows" for both the "Unlock At" and "Time Left" values
- Any time changes will simply show as "added some time" or "removed some time" for the lockee
- The keyholder(s) will still see the "Unlock At" and "Time Left" values, as well as the values of any time added/removed

---
### 1.5. Public Links
![PiVaultPublicLinks](https://i.imgur.com/B3CrcMz.png)
| Nr. | Name                  | Description                        |
|-----|-----------------------|------------------------------------|
| 1   | Close Button          | Close the Public Link dialog       |
| 2   | Create Button         | Click to Create a new Public Link  |
| 3   | Public Link           | Existing Public link               |
| 4   | Copy Link Button      | Click to copy the Public Link URL  |
| 5   | Link Settings Button  | Click to change the Links Settings |
| 6   | Delete Link Button    | Click to Delete the Public Link    |

**Note: Links will persist between session! Make sure you manage them or you might find yourself with happy surprises on your count** ~

#### **1.5.1** Create / Modify Public Links
![PiVaultCreatePublicLinks](https://i.imgur.com/ZV8g2Rx.png)
| Nr. | Name                         | Description                                                                                                                             | Default  |
|-----|------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------|----------|
| 1   | Link Name                    | Click to change the Name of the Public Link                                                                                             | --       |
| 2   | Link Enable Toggle           | Click to enable / disable the link                                                                                                   | On       |
| 3   | Enable Vote Toggle           | Enables Voting options for the link (Note: If this is false, the link can only be used to see the current status as well as the logs)   | Off      |
| 4   | Require Login Toggle         | If true, only users with an Account can vote on the Link **Note: This can currently not be disabled, this might change in the future**  | On       |
| 5   | Cool Down Duration Select    | Click to change the Cooldown Duration until a user can vote again                                                                       | --       |
| 6   | Link Mode Select             | Click to change between Chastity or Bondage Mode, this influences the Max time setting below (Chastity: Max 7 days, Bondage: Max 1 Hour) | Chastity |
| 7   | Allow Reduction Toggle       | Enables Time Reduction via the link, if this is disabled you can only add time.                                                         | Off      |
| 8   | Max Time select              | Click to change the Maximum Voting Increment                                                                                            | --       |
| 9   | Link Expiration Date / Time  | Click to change the Links Expiration Date / Time                                                                                        | --       |
| 10  | Clear Expiration Date / Time | Click to reset the Links Expiration Date / Time, Links without an Expiration Date will not Expire automatically                          | --       |
| 11  | Cancel Button                | Click to cancel creating / modifying the Public Link                                                                                    | --       |
| 12  | Save Button                  | Click to Save the changes to / create the Public Link                                                                                   | --       |
---
### 1.6. API Keys
*Comming Soon, Feature in development*

---
### 1.7. Keyholder Codes
![PiVaultCreatePublicLinks](https://i.imgur.com/farHKHc.png)
| Nr. | Name                             | Description                                                                                         |
|-----|----------------------------------|-----------------------------------------------------------------------------------------------------|
| 1   | Keyholder Code                   | Existing Keyholder Code, with the Keyholders Name                                                   |
| 2   | Delete Keyholder Code Button     | Click to Delete the Keyholder Code and Revoke the Keyholders Access                                 |
| 3   | Close Button                     | Click to Close the Keyholder Code Dialog                                                            |
| 4   | Create a new Keyholder Code Button | Click to Create a new Keyholder Code, this will Generate a new Code you can share with your Partner |

Generating a Keyholder code will prevent you from doing the following:
- You can no longer create Links with Reduction.
- You can no longer adjust Hygiene.
- You can no longer unlock the box yourself except through Emergency Unlock
- You can no longer start a session.
- You can no longer enable or disable Emergency Unlock

Keyholders can:
- Create Links
- Adjust Hygiene Settings
- Delete Links
- See your logs
- Unlock
- Start a session
