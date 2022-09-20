# PiVault Lockbox API
A JSON API for controlling the PiVault Lockbox by PiShock

**PiVault can be purchased at [PiShock.com](https://pishock.com/#/?product=pivault)**

> ## ⚠ DISCLAIMER
>
> PiShock is not responsible for any harm caused by the misuse of the PiVault Lockbox. We always recommend leaving the emergency unlock function enabled, or having an alternative means of emergency release.
------------
## Authenticating
All API requests require a PiShock username and API key to be submitted as HTTP Basic Auth. Your username and API key can be obtained from [the account page on pishock.com](https://pishock.com/#/account).

Additionally, all API calls except for TestAuthorization requires a lockbox API key (lockboxapikey) as a parameter. This is an API key specific to the lockbox, and one can be generated on [the PiVault control panel](https://pishock.com/#/lockbox).

Once a lockbox API key is used, it becomes bound to the account that used it. This is to prevent multiple accounts from using the same lockbox API key, to prevent cheating on lock sessions.

| **Key**       | **Value Type** | **Usage**       | **Example**                          | **Description**                                                                          |
|---------------|----------------|-----------------|--------------------------------------|------------------------------------------------------------------------------------------|
| Username      | String         | HTTP Basic Auth | DemoUser                             | PiShock.com username for the account that will be interacting with the API.              |
| Password      | String (UUID)  | HTTP Basic Auth | 30f1e957-6287-4bd3-8125-51429a5b4572 | PiShock.com API key for the account that will be interacting with the API.               |
| LockboxApiKey | String (UUID)  | Parameter       | c643a21a-7897-4965-b912-c7e32c1f743b | API key for a specific lockbox. Becomes bound to the PiShock.com account on first usage. |
------------
## Lockbox Status (GET)
This gets the current status of the lockbox.
> `GET` https://do.pishock.com/pivaultapi/getpivaultinfo?lockboxapikey=LOCKBOXAPIKEY

### Results
| **Value**        | **Value Type** | **Description**                                                                                                          |
|------------------|----------------|--------------------------------------------------------------------------------------------------------------------------|
| id               | Integer        | The ID of the PiVault Lockbox.                                                                                           |
| online           | Boolean        | Indicates if the lockbox is online or not.                                                                               |
| lastPolled       | DateTime       | Last time that the lockbox polled the server.                                                                            |
| lastUnlocked     | DateTime       | Last time that the lockbox was unlocked.                                                                                 |
| name             | String         | Name of the lockbox.                                                                                                     |
| keyholdersCount  | Integer        | Number of keyholders who have control over the lockbox.                                                                  |
| userName         | String         | Username of the account that owns the lockbox.                                                                           |
| timesForced      | Integer        | Number of times the emergency unlock function was used.                                                                  |
| selfLocking      | Boolean        | Indiciates if the current session is in self-locking ("no keyholder") mode.                                              |
| maxMinutes       | Integer        | Maximum time (in minutes) that can be added overall to a chastity session.                                               |
| maxMinutesSB     | Integer        | Maximum time (in minutes) that can be added overall to a self-bondage session.                                           |
| normallyUnlocked | Boolean        | Indicates if the lockbox has "normally unlocked" enabled, allowing it to be opened anytime a session is not in progress. |
| timezone         | String         | Time zone that the device is located in.                                                                                 |
| hygieneActive    | Boolean        | Indicates if hygiene openings are permitted or not.                                                                      |
| lockedSince      | DateTime       | Time that a lock session has begun.                                                                                      |
| lockedUntil      | DateTime       | Current end time of a lock session.                                                                                      |
| canUnlock        | Boolean        | Indicates if the lockbox will currently permit opening with the button on the back.                                      |
| hygieneSettings  | Array          | Provides information about hygiene openings, including frequency, time, and days permitted.                              |
| lastOpened       | DateTime       | The date and time the lockbox was last opened.                                                                           |
| lastClosed       | DateTime       | the date and time the lockbox was last closed.                                                                           |

### Examples
Curl:
```bash
curl https://do.pishock.com/pivaultapi/getpivaultinfo?lockboxapikey=c643a21a-7897-4965-b912-c7e32c1f743b -u DemoUser:30f1e957-6287-4bd3-8125-51429a5b4572
```

Python:
```python
import requests
from requests.auth import HTTPBasicAuth
res = requests.get("https://do.pishock.com/pivaultapi/getpivaultinfo?lockboxapikey=c643a21a-7897-4965-b912-c7e32c1f743b", verify=False, auth=HTTPBasicAuth("DemoUser", "30f1e957-6287-4bd3-8125-51429a5b4572"))
print(res.json())
```
------------
## API Key Permissions (GET)
This shows the permissions for a lockbox API key. This can be used by a script or app to ensure that the API gives all necessary permissions to work successfully.
> `GET` https://do.pishock.com/pivaultapi/apikeypermissions?lockboxapikey=LOCKBOXAPIKEY

### Results
| **Value**    | **Value Type** | **Description**                                                                 |
|--------------|----------------|---------------------------------------------------------------------------------|
| change       | Boolean        | Indicates if the API key can be used to change the time remaining.              |
| reduction    | Boolean        | Indicates if the API key can reduce the time left on a session.                 |
| sessionStart | Boolean        | Indicates if the API key can start a session if one is not already in progress. |
| unlock       | Boolean        | Indicates if the API key can send an unlock command.                            |

### Examples
Curl:
```bash
curl https://do.pishock.com/pivaultapi/apikeypermissions?lockboxapikey=c643a21a-7897-4965-b912-c7e32c1f743b -u DemoUser:30f1e957-6287-4bd3-8125-51429a5b4572
```

Python:
```python
import requests
from requests.auth import HTTPBasicAuth
res = requests.get("https://do.pishock.com/pivaultapi/apikeypermissions?lockboxapikey=c643a21a-7897-4965-b912-c7e32c1f743b", verify=False, auth=HTTPBasicAuth("DemoUser", "30f1e957-6287-4bd3-8125-51429a5b4572"))
print(res.json())
```
------------
## Set Unlock Time (POST)
This allows you to set the unlock time for a lockbox. If a session is not in progress and the API key has the "sessionStart" permission set to true, this will start a new session. If a session is in progress, this will change the unlock time. Reducing the unlock time to an earlier value requires the "reduction" permission to be set to true.
> `POST` https://do.pishock.com/pivaultapi/setunlocktime

### Properties
| **Key**       | **Value Type** | **Example**                          | **Description**                                     |
|---------------|----------------|--------------------------------------|-----------------------------------------------------|
| LockboxApiKey | String (UUID)  | c643a21a-7897-4965-b912-c7e32c1f743b | The API key for the lockbox.                        |
| DateTime      | DateTime       | 2022-08-20T18:00:00                  | The desired unlock time.                            |
| UseLocal      | Boolean        | True                                 | Uses the lockbox's time zone if true, UTC if false. |

### Results
| **Response Code** | **Meaning**                                                                                          |
|-------------------|------------------------------------------------------------------------------------------------------|
| 200               | Successful.                                                                                          |
| 400               | Bad request. This may indicate that you are trying to set a time beyond the session's allowed limit. |
| 403               | Forbidden. This may indicate your API key is invalid or does not have the necessary permissions.     |

### Examples
Curl:
```bash
curl -d '{"LockboxApiKey":"c643a21a-7897-4965-b912-c7e32c1f743b","UseLocal":"False","DateTime":"2022-08-20T18:00:00Z"}' -u DemoUser:30f1e957-6287-4bd3-8125-51429a5b4572 -H 'Content-Type: application/json' https://do.pishock.com/pivaultapi/setunlocktime
```

Python:
```python
import requests
import json
from requests.auth import HTTPBasicAuth

user_name = "DemoUser"
user_key = "30f1e957-6287-4bd3-8125-51429a5b4572"
box_key = "c643a21a-7897-4965-b912-c7e32c1f743b"

api_data = {
    "LockboxApiKey" : box_key,
    "DateTime" : "2022-08-20T18:00:00Z",
    "UseLocal" : "False"
}

api_headers = {
    "Content-type" : "application/json"
}

res = requests.post("https://do.pishock.com/pivaultapi/setunlocktime", data=json.dumps(api_data), auth=HTTPBasicAuth(user_name, user_key), headers=api_headers)
print(res)
```

------------
## Clear (POST)
This clears (stops) the current session. This requires the "reduction" and "allowChange" permissions to both be set to true.
> `POST` https://do.pishock.com/pivaultapi/clear

### Properties
| **Key**       | **Value Type** | **Example**                          | **Description**              |
|---------------|----------------|--------------------------------------|------------------------------|
| LockboxApiKey | String (UUID)  | c643a21a-7897-4965-b912-c7e32c1f743b | The API key for the lockbox. |

### Results
| **Response Code** | **Meaning**                                                                                      |
|-------------------|--------------------------------------------------------------------------------------------------|
| 200               | Successful.                                                                                      |
| 400               | Bad request. This may indicate that no session is currently in progress.                         |
| 403               | Forbidden. This may indicate your API key is invalid or does not have the necessary permissions. |

### Examples
Curl:
```bash
curl -d '{"LockboxApiKey":"c643a21a-7897-4965-b912-c7e32c1f743b"}' -u DemoUser:30f1e957-6287-4bd3-8125-51429a5b4572 -H 'Content-Type: application/json' https://do.pishock.com/pivaultapi/clear
```

Python:
```python
import requests
import json
from requests.auth import HTTPBasicAuth

user_name = "DemoUser"
user_key = "30f1e957-6287-4bd3-8125-51429a5b4572"
box_key = "c643a21a-7897-4965-b912-c7e32c1f743b"

api_data = {
    "LockboxApiKey" : box_key,
}

api_headers = {
    "Content-type" : "application/json"
}

res = requests.post("https://do.pishock.com/pivaultapi/clear", data=json.dumps(api_data), auth=HTTPBasicAuth(user_name, user_key), headers=api_headers)
print(res)
```

------------
## Unlock (POST)
This either unlocks the lockbox (if "Mode" is 0 or 2) or allows the lockbox to be manually unlocked with the button (if "Mode" is 1). This requires the "unlock" permission to be set to true.
> `POST` https://do.pishock.com/pivaultapi/unlock

### Properties
| **Key**       | **Value Type** | **Example**                          | **Description**                                                                                               |
|---------------|----------------|--------------------------------------|---------------------------------------------------------------------------------------------------------------|
| LockboxApiKey | String (UUID)  | c643a21a-7897-4965-b912-c7e32c1f743b | The API key for the lockbox.                                                                                  |
| Mode          | Integer (0-2)  | 1                                    | The unlock mode. 0 unlocks on next poll, 1 allows manual unlock with the button, and 2 unlocks after a delay. |
| Seconds       | Integer        | 15                                   | Number of seconds to delay prior to unlocking. Only used if "Mode" is set to 2.                               |
| Buzz          | Boolean        | True                                 | Plays a sound when unlocking.                                                                                 |
| IgnoreTimer   | Boolean        | False                                | If false, the session will end when unlocked. If true, the session will not end when unlocked.                |

### Results
| **Response Code** | **Meaning**                                                                                      |
|-------------------|--------------------------------------------------------------------------------------------------|
| 200               | Successful.                                                                                      |
| 400               | Bad request. This may indicate that no session is currently in progress.                         |
| 403               | Forbidden. This may indicate your API key is invalid or does not have the necessary permissions. |

### Examples
Curl:
```bash
curl -d '{"LockboxApiKey":"c643a21a-7897-4965-b912-c7e32c1f743b","Mode":"2","Seconds":"15","Buzz":"True","IgnoreTimer":"False"}' -u DemoUser:30f1e957-6287-4bd3-8125-51429a5b4572 -H 'Content-Type: application/json' https://do.pishock.com/pivaultapi/unlock
```

Python:
```python
import requests
import json
from requests.auth import HTTPBasicAuth

user_name = "DemoUser"
user_key = "30f1e957-6287-4bd3-8125-51429a5b4572"
box_key = "c643a21a-7897-4965-b912-c7e32c1f743b"

api_data = {
    "LockboxApiKey" : box_key,
    "Mode": "2",
    "Seconds" : "15",
    "Buzz" : "True",
    "IgnoreTimer" : "False"
}

api_headers = {
    "Content-type" : "application/json"
}

res = requests.post("https://do.pishock.com/pivaultapi/unlock", data=json.dumps(api_data), auth=HTTPBasicAuth(user_name, user_key), headers=api_headers)
print(res)
```