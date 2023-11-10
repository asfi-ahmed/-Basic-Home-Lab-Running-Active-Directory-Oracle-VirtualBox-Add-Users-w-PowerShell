# -Basic-Home-Lab-Running-Active-Directory-Oracle-VirtualBox-Add-Users-w-PowerShell
This project on Oracle VirtualBox creates an Active Directory home lab. It employs PowerShell scripts for user creation and tests network functionalities. It provides hands-on learning in AD, scripting, and network setups.

# Introduction:
This project is designed to simulate a basic home lab environment using Oracle VirtualBox to set up an Active Directory. The environment represents a mini corporate network and aims to introduce users to the functionalities of Active Directory, the virtualization tool VirtualBox, PowerShell scripting, and network configuration.
The project involves the creation of a virtual corporate network using a domain controller and client machines within Oracle VirtualBox. Users will leverage PowerShell scripts to create user accounts in the Active Directory and gain a fundamental understanding of network infrastructure, user management, and domain setup.

# Objective:
<br><b>1. Setup and Configuration:</b> Establish an Active Directory environment in Oracle VirtualBox, configuring a domain controller and client machines to simulate a corporate network.</br>
<br><b>2. User Account Creation:</b> Employ PowerShell scripting to automate the creation of user accounts within the Active Directory.</br>
<br><b>3. Network Testing:</b> Validate network connectivity, including DHCP and DNS functionality, between the domain controller and client machines.</br>
<br><b>4. User Authentication:</b> Confirm successful user authentication by joining a client machine to the domain and logging in with created user credentials.</br>

## Outcomes:
<br><b>1.Understanding Active Directory:</b> Gain proficiency in configuring an Active Directory environment, setting up domain controllers, and managing user accounts within an Active Directory structure.</br>
<br><b>2. PowerShell Proficiency:</b> Acquire skills in PowerShell scripting for automating user creation and performing Active Directory tasks.</br>
<br><b>3. Networking and Domain Integration:</b> Experience setting up a domain environment and troubleshooting network configurations in a virtualized setting.</br>
<br><b>4. User Account Management:</b> Learn user account management within a corporate network, understanding domain authentication, and user privileges.</br>

# Steps
## Step 01: Set up an environment using VirtualBox
<br><b>1. VirtualBox Installation:</b> Download and install VirtualBox from the official website according to your operating system (Windows, macOS, or Linux). Run the setup file and follow the installation instructions.</br>
<br><b>2. Create a New Virtual Machine:</b> Open VirtualBox and click on "New." Enter a name for the Virtual Machine (VM) and select the appropriate OS type and version. Allocate memory, create a virtual hard disk, and choose its size and format.</br>
<br><b>3. Configure Network Settings:</b> Ensure the network settings are set to an Internal Network for the VM. This can be configured within the VirtualBox settings for the VM.</br>

## Step 2: Install Windows Server operating system on the VirtualBox environment
<br><b>1. ISO Image Download:</b> Download the ISO file for the Windows Server operating system. This can be done from the Microsoft website.</br>
<br><b>2. Create a New VM:</b> In VirtualBox, select the newly created VM and click "Start." It will prompt to select the Windows Server ISO file, which will begin the installation process.</br>
<br><b>3. Install Windows Server:</b> Follow the installation wizard. Choose language preferences, agree to terms, select the installation type, and configure the storage. Set the administrator password and perform the installation. The system will restart once the installation is complete.</br>

## Step 3: Configure the Domain Controller and the Active Directory
<br><b>1. Initial Setup:</b> After the OS installation, log in to the Windows Server. This will lead to the Server Manager Dashboard.</br>
<br><b>2. Add Roles and Features:</b> Open Server Manager, click on "Add roles and features," and choose the Active Directory Domain Services role.</br>
<br><b>3. Promote to Domain Controller:</b> Post-role installation, promote the server to a Domain Controller. Run the Active Directory Domain Services Configuration Wizard, select to add a new forest, enter the domain name ("mydomain.com"), set the Directory Services Restore Mode password, and proceed with the setup.</br>

## Step 4: Create an IP range (scope) and define settings, such as lease durations and exclusions
<br><b>1. Configure DHCP:</b> Open the Server Manager and select DHCP from the Tools menu. Add a new IPv4 scope. Define the IP address range, subnet mask, and default gateway.</br>
<br><b>2. Set Lease Duration:</b> Determine the lease duration for IP addresses (usually in hours) and set exclusions for specific IPs if necessary.</br>
<br><b>3. Activate the Scope:</b> Activate the scope to ensure the DHCP settings are saved and apply.</br>

## Step 5: Configure DHCP options (DNS, Gateway) for the connected clients
<br><b>1.Set DNS Server:</b> Under the IPv4 settings in DHCP, add DNS servers that clients should use for name resolution. Assign the IP address of the domain controller for DNS.</br>
<br><b>2. Set Default Gateway (Router):</b> Configure the DHCP server options and add the router option. Specify the IP address of the Domain Controller as the default gateway for the connected clients.</br>
<br><b>3. Finalize DHCP Configuration:</b> Save changes and ensure the DHCP settings are updated and applied correctly to provide the necessary IP configuration to the clients.</br>

## Step 6: Active Directory Configuration and PowerShell Scripting
<br><b>1.Domain Controller Setup:</b></br>
<br>>> Create a new VM in VirtualBox and install Windows Server operating system.</br>
<br>>> Configure Active Directory Domain Services (AD DS).</br>
<br>>> Set up DNS, DHCP, and other necessary services within the domain controller.</br>

<br><b>2. PowerShell Script for User Creation:</b></br>
<br>>> Write a PowerShell script to create users in Active Directory.</br>
<br>>> The script pulls user names from a text file and uses specific criteria (e.g., first and last names) to generate usernames, passwords, and other user attributes.</br>
<br>>> The script uses Active Directory commands to create and configure users, setting passwords, usernames, OU placement, etc.</br>

## Step 7: Executing the PowerShell Script
<br><b>1. Preparing Environment:</b></br>
<br>>> Navigate to the directory containing the PowerShell script and the text file with user names.</br>
<br>>> Ensure that the script can access and read the text file.</br>

<br><b>2. Running the Script:</b></br>
<br>>> Execute the PowerShell script to create users in Active Directory.</br>
<br>>> The script iterates through each name in the file, generates usernames, sets up user accounts, and configures relevant details.</br>

## Step 8: Visual Confirmation and Active Directory Check
<br><b>1. Checking Active Directory:</b></br>
<br>>> Access Active Directory to verify user creation.</br>
<br>>> Look for users created via the PowerShell script, ensuring proper attributes and placements.</br>

<br><b>2. Verification in Domain Controller:</b></br>
<br>>> Confirm user accounts within the Active Directory Users and Computers section.</br>
<br>>> Ensure the users are correctly placed in the defined OU (Organizational Unit).</br>

## Step 9: Client Virtual Machine Configuration
<br><b>1. Client Virtual Machine Setup:</b></br>
<br>>> Create a new VM in VirtualBox and install Windows 10 operating system.</br>
<br>>> Configure the network settings to connect to the internal network established by the domain controller.</br>

<br><b>2. Joining the Domain:</b></br>
<br>>> Join the Windows 10 VM to the Active Directory domain using domain credentials.</br>
<br>>> Authenticate and validate connectivity to the domain controller and the entire network infrastructure.</br>

## Step 10: Client Machine Verification
<br><b>1. DHCP Troubleshooting:</b></br>
<br>>> Resolve DHCP issues, if any, to ensure proper IP addressing, subnet mask, default gateway, and DNS settings.</br>
<br>>> Check for proper lease allocation from the DHCP server.</br>

<br><b>2. Network Verification:</b></br>
<br>>> Test network connectivity by pinging both local resources (e.g., domain controller) and external sites (e.g., Google) to confirm DNS and gateway functionality.</br>

## Step 11: Validating Domain and Active Directory Functionality
<br><b>1. Domain Membership Verification:</b></br>
<br>>> Confirm successful domain membership of the client machine by checking the domain name and associated user accounts.</br>
<br>>> Verify the proper user credentials necessary for domain access.</br>

<br><b>2. Active Directory Functionality Check:</b></br>
<br>>> Ensure the Active Directory service is functioning correctly.</br>
<br>>> Confirm user profiles and their association with the Active Directory.</br>
<br>>> Validate user login using domain credentials.</br>

## Step 12: PowerShell Script Process Overview
<br><b>1. Understanding the Script:</b></br>
<br>>> Review the PowerShell script that was executed to understand the logic and syntax used for user creation.</br>
<br>>> Analyze the variable assignments, loops, and specific Active Directory cmdlets employed in the script.</br>

<br><b>2. Troubleshooting and Script Modification:</b></br>
<br>>> Identify potential errors or issues in the script execution.</br>
<br>>> Modify the script to rectify any errors encountered during execution.</br>

## Step 13: DHCP and Default Gateway Configuration
<br><b>1. DHCP Server Options Review:</b></br>
<br>>> Access the DHCP Server Manager and navigate to the server options to verify or add necessary options, such as the default gateway, DNS servers, etc.</br>

<br><b>2. Address Renewal and Gateway Settings:</b></br>
<br>>> Ensure the DHCP server properly assigns the default gateway to client machines.</br>
<br>>> If there are issues in the default gateway assignment, review the DHCP server options and update the settings.</br>

## Step 14: Troubleshooting and Network Functionality
<br><b>1. Gateway Verification:</b></br>
<br>>> Execute ipconfig on the client machine to ensure it receives the proper default gateway after DHCP renewal.</br>
<br>>> Verify the IP address, subnet mask, and gateway details.</br>

<br><b>2. Connectivity Testing:</b></br>
<br>>> Use ping commands to test connectivity to local and external resources.</br>
<br>>> Confirm the ability to ping the default gateway, local servers, domain controller, and external websites to verify proper network functionality.</br>

## Step 15: Troubleshooting Network Configuration
<br><b>1. Activity:</b> Identified an issue in the network configuration.</br>

<br><b>2. Location:</b> Revisited DHCP server settings.</br>

<br><b>3. Procedure:</b> Reviewed server options, particularly the router (default gateway) entry.</br>

<br><b>4. Action:</b> Added the correct router entry to the DHCP server settings.</br>

<br><b>5. Resolution:</b> Restarted the DHCP server. Renewed the Windows 10 VM's IP configuration to rectify the missing default gateway issue.</br>

## Step 16: Network Testing
<br><b>1. Action:</b> Conducted network tests to ensure the success of the rectification.</br>

<br><b>2. Evaluation:</b> Pinged domains like "google.com" and "mydomain.com" from the Windows 10 VM.</br>

<br><b>3. Validation:</b> Checked for DNS resolution and ensured ping replies from external domains, validating network functionality.</br>

## Step 17: Reviewing Server and DHCP Logs
<br><b>1. Investigation:</b> Inspected DHCP logs and server configurations to understand the missing default gateway settings.</br>

<br><b>2. Documentation:</b> Vital for creating future references and troubleshooting if a similar issue arises.</br>

## Step 18: Verifying Windows 10 Connectivity and Joining the Domain
<br><b>1. Validation:</b> Ensured that the Windows 10 VM's network configurations were correctly updated with the default gateway settings.</br>

<br><b>2. Action:</b> Renamed the VM to "client one" and joined it to the domain "mydomain.com".</br>

<br><b>3. Confirmation:</b> Ensured successful domain membership of the Windows 10 VM.</br>

## Step 19: Checking Domain Membership and Logging In
<br><b>1. Review:</b> Revisited the domain controller to confirm the presence of the Windows 10 VM under the computer's container.</br>

<br><b>2. Authentication:</b> Accessed the Windows 10 VM using domain credentials to verify successful domain membership and user authentication.</br>

# Conclusion:
The project successfully achieved the objectives of setting up an Active Directory environment and user accounts in a simulated corporate network. Users gained an understanding of Active Directory, PowerShell scripting, and network configuration. It provides a foundation for further exploration into network infrastructure, user management, and virtualization.
Additionally, the project opened doors for possible expansions, including advanced Active Directory configurations, security enhancements, and larger-scale network simulations.
