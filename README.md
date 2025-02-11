# rmmagent-script
Script for one-line installing and update of tacticalRMM agent

> Now x64, x86, arm64 and armv6 scripts are available but only x64 and i386 tested on Debian 11 and Debian 10 on baremetal, VM (Proxmox) and VPS(OVH)
> Tested on raspberry 2B+ with armv7l (chose armv6 on install)

Script for other platform will be available futher as I adapt script on other platform.
Feel free to adapt script and submit me !

# Usage
Download the script that match your configuration

### Tips

Download script with this url: `https://raw.githubusercontent.com/netvolt/LinuxRMM-Script/main/rmmagent-linux.sh`

## Install
To install agent launch the script with this arguement:

```bash
./rmmagent-linux.sh install 'System type' 'Mesh agent' 'API URL' 'Client ID' 'Site ID' 'Auth Key' 'Agent Type'
```
The compiling can be quite long, don't panic and wait few minutes... USE THE 'SINGLE QUOTES' IN ALL FIELDS!

The argument are:

2. System type

  Type of system. Can be 'amd64' 'x86' 'arm64' 'armv6'  

3. Mesh agent

  The url given by mesh for installing new agent.
  Go to mesh.fqdn.com > Add agent > Installation Executable Linux / BSD / macOS > **Select the good system type**
  Copy **ONLY** the URL with the quote.
  
4. API URL

  Your api URL for agent communication usually https://api.fqdn.com.
  
5. Client ID

  The ID of the client in wich agent will be added.
  Can be view by hovering the name of the client in the dashboard.
  
6. Site ID

  The ID of the site in wich agent will be added.
  Can be view by hovering the name of the site in the dashboard.
  
7. Auth Key

  Authentification key given by dashboard by going to dashboard > Agents > Install agent (Windows) > Select manual and show
  Copy **ONLY** the key after *--auth*.
  
8. Agent Type

  Can be *server* or *workstation* and define the type of agent.
  
### Example
```bash
./rmmagent-linux.sh install amd64 "https://mesh.fqdn.com/meshagents?id=XXXXX&installflags=X&meshinstall=X" "https://api.fqdn.com" 3 1 "XXXXX" server
```

## Update

Simply launch the script that match your system with *update* as argument.

```bash
./rmmagent-linux.sh update
```

## Uninstall
To uninstall agent launch the script with this arguement:

```bash
./rmmagent-linux.sh uninstall 'Mesh FQDN' 'Mesh ID'
```
Note: Single quotes must be around the Mesh ID for it to uninstall the mesh agent properly

The argument are:

2. Mesh FQDN

  Example of FQDN: mesh.fqdn.com 

3. Mesh ID

  The ID given by mesh for installing new agent.
  Go to mesh.fqdn.com > Add agent > Linux / BSD (Uninstall) > Copy **ONLY** the last value with the single quotes.
  You are looking for a 64 charaters long value of random letter case, numbers, and special characters.

### Example
```bash
./rmmagent-linux.sh uninstall mesh.fqdn.com 'XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX'
```

### WARNING
- You should **only** attempt this if the agent removal feaure on TacticalRMM is not working.
- Running uninstall will **not** remove the connections from the TacticalRMM and MeshCentral Dashboard. You will need to manually remove them. It only forcefully removes the agents from your linux box.
