# PiShock API
A JSON API for controlling shock collars (and soon other toys) with PiShock.

**PiShock can be purchased at [PiShock.com](https://www.pishock.com)**

> ## ⚠ DISCLAIMER
>
> PiShock is not responsible for any harm caused by misuse of the shock collar sold along with the PiShock device. We do not recommend putting any kind of electrical device near the heart or use if you have a heart condition. Shock collars are not meant for use on humans and can cause serious injury including cardiac events.
------------------
## Authenticating
To authenticate and select the shocker you must pass three variables: Username, Apikey, & Code.

Addtionally, all API queries must contain the Name variable, representing the script/person controlling the device.

| **Key**  | **Value Type** | **Example**                          | **Description**                                                                                                              |
|----------|----------------|--------------------------------------|------------------------------------------------------------------------------------------------------------------------------|
| Username | string         | puppy73                              | Username you use to log into [PiShock.com](https://www.pishock.com). Can be found in the **Account** section of the website. |
| Apikey   | string         | 5c678926-d19e-4f86-42ad-21f5a76126db | API Key generated on [PiShock.com](https://www.pishock.com) Can be found in the **Account** section of the website.          |
| Code     | string         | 17519CD8GAP                          | Sharecode generated on [PiShock.com](https://www.pishock.com). *Limitations can be set when generating the code*.            |
| Name     | string         | TG_Bot_Script                        | Name of what sent the commands. This will showup in the PiShock logs on the website.                                         |
------------------
## Shock Collar Control
### Operations
The shock collar included with PiShock has three operations: shock, vibrate, and beep. You specify the operation using the Op variable.
| **Key** | **Value** | **Operation** |
|---------|-----------|---------------|
| Op      | 0         | Shock         |
| Op      | 1         | Vibrate       |
| Op      | 2         | Beep          |



```
POST https://do.pishock.com/api/apioperate/
```

The headers of the request must specify JSON formatting:

```
Content-Type: application/json
```
------------------
#### Shock
This allows you to activate the shock function of the shock collar. It will shock the wearer with a specified *duration* and *intensity*.
> `POST` https://do.pishock.com/api/apioperate/

The following variables must be set to send a shock command.
| **Key**   | **Value Type**    | **Example** | **Description**                                                                              |
|-----------|-------------------|-------------|----------------------------------------------------------------------------------------------|
| Op        | integer           | 0           | Activate the shock function.                                                                 |
| Duration  | integer (1 - 15)  | 2           | An integer representing the number of seconds to shock the wearer. Must be between 1 and 15. |
| Intensity | integer (1 - 100) | 7           | An integer representing the intensity of shock. Must be between 1 and 100.                   |

Example:

```bash
curl -d '{"Username":"puppy73","Name":"TG_Bot_Script","Code":"17519CD8GAP","Intensity":"6","Duration":"1","Apikey":"5c678926-d19e-4f86-42ad-21f5a76126db","Op":"0"}' -H 'Content-Type: application/json' https://do.pishock.com/api/apioperate
```

------------------
#### Vibrate
This allows you to activate the vibration function of the shock collar. It will vibrate the shocker with a specified *duration* and *intensity*.
> `POST` https://do.pishock.com/api/apioperate/

The following variables must be set to send a vibrate command.
| Key       | Value Type        | Example | Description                                                                    |
|-----------|-------------------|---------|--------------------------------------------------------------------------------|
| Op        | integer           | 1       | Activate the vibrate function.                                                 |
| Duration  | integer           | 7       | An integer representing the number of seconds to vibrate the shocker.          |
| Intensity | integer (1 - 100) | 7       | An integer representing the intensity of vibration. Must be between 1 and 100. |

Example:

```bash
curl -d '{"Username":"puppy73","Name":"TG_Bot_Test","Code":"17519CD8GAP","Intensity":"50","Duration":"1","Apikey":"5c678926-d19e-4f86-42ad-21f5a76126db","Op":"1"}' -H 'Content-Type: application/json' https://do.pishock.com/api/apioperate
```

------------------
#### Beep
This allows you to activate the beep function of the shock collar. It will cause the shocker to beep with a specified duration and intensity.
> `POST` https://do.pishock.com/api/apioperate/

The following variables must be set to send a beep command.
| Key      | Value Type | Example | Description                                                             |
|----------|------------|---------|-------------------------------------------------------------------------|
| Op       | integer    | 2       | Activate the beep function.                                             |
| Duration | integer    | 3       | An integer representing the number of seconds to make the shocker beep. |

Example:

```bash
curl -d '{"Username":"puppy73","Name":"TG_Bot_Test","Code":"17519CD8GAP","Duration":"3","Apikey":"5c678926-d19e-4f86-42ad-21f5a76126db","Op":"2"}' -H 'Content-Type: application/json' https://do.pishock.com/api/apioperate
```


------------------
#### Shocker info
This allows you to get information about the shock collar.
The response is sent in JSON format and includes information such as the shock collar's client ID, name, maximum intensity, maximum duration, and online status.
> `POST` https://do.pishock.com/api/GetShockerInfo

This does not require any extra variables.

Example:

```bash
curl -d '{"Username":"puppy73","Code":"17519CD8GAP","Apikey":"5c678926-d19e-4f86-42ad-21f5a76126db"}' -H 'Content-Type: application/json' https://do.pishock.com/api/GetShockerInfo
```


------------------
### Responses
When a command is successfully received by the server, you will receive a response code of `200` with a message indicating the status of the command:

| **Response Message**                                          | **Meaning**                                                                                                               |
|---------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------|
| Operation Succeeded.                                          | The command was sent successfully.                                                                                        |
| This code doesn’t exist.                                      | The specified share code could not be found. Make sure you create and copy an active share code from the PiShock website. |
| Not Authorized.                                               | The specified username or apikey is not correct (or your account has not been activated).                                 |
| Shocker is Paused, unable to send command.                    | The shocker is paused (from the PiShock.com web panel).                                                                   |
| Device currently not connected.                               | The PiShock is offline.                                                                                                   |
| This share code has already been used by somebody else.       | Someone (or something) else is using the specified share code. Generate a new one.                                        |
| Unknown Op, use 0 for shock, 1 for vibrate and 2 for beep.    | Invalid Op code specified. Must be 0, 1, or 2.                                                                            |
| Intensity must be between 0 and {maxint}                      | The specified intensity was outside the permitted range.                                                                  |
| Duration must be between 1 and {maxdur}                       | The specified duration was outside the permitted range.                                                                   |

Headers:

```Content-Type: text/plain```

Body: 

```Operation Succeeded.```
