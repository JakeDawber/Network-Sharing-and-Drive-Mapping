<h1>Network Sharing and Drive Mapping</h1>

<b>1. Creating the Shared Folder and Configuring Permissions</b>

Created a shared folder named SHARED on the domain controller and configured its network sharing permissions. The Domain Users group was granted Read access, allowing domain users to access shared resources without granting unnecessary modification or administrative privileges.


<img src="Screenshots/Share Permissions.png"/>


<b>2. Configuring the Network Share</b>

Verified that the folder was shared successfully and that its UNC network path was \\JH-DC01\shared. This path allows domain-connected workstations to access the shared folder across the network.

<img src="Screenshots/Share Network path.png"/>


<b>3. Creating a Drive Mapping GPO Preference</b>

Created a Group Policy Object named Drive Mapping and configured a Drive Maps preference under User Configuration → Preferences → Windows Settings → Drive Maps. The mapping uses the UNC path \\JH-DC01\shared and assigns it the drive letter S: with the label SHARED.


<img src="Screenshots/Drive Mapping path.png"/>


<b>4. Applying the Drive Mapping</b>

Configured the drive mapping action as Update, allowing the preference to create or update the network drive mapping when the user Group Policy refreshes. This provides users with consistent access to shared resources without requiring them to map the drive manually.

<img src="Screenshots/Share Drive Properties.png"/>


<b>5. Verifying Access as John Smith</b>

Signed in to the Windows 11 workstation as JAKEHOMELAB\johnsmith and confirmed that the SHARED (S:) network drive appeared under This PC. The whoami command verified the logged-in domain account, demonstrating that the drive mapping was applied successfully in the user's session.

<img src="Screenshots/Network share conformation.png"/>


<b>GPO Policies vs GPO Preferences</b>

<b>Group Policy Policies:</b> Enforce or restrict system and user settings, such as disabling Control Panel access, preventing registry editing, or enforcing security requirements. Users generally cannot override enforced settings while the policy applies.

<b>Group Policy Preferences:</b> Configure or customise the user and computer environment, such as mapping network drives, creating shortcuts, or configuring files and folders. Preferences are generally not enforced in the same way, and users may be able to change the resulting settings.

In this project, the network drive was configured using a GPO Preference because the objective was to automatically map a shared network resource for the domain user rather than enforce a restrictive security setting.

<b>Skills Demonstrated</b>

- Active Directory administration: Working with domain users and groups to manage access to network resources.

- File sharing and permissions: Creating shared folders and configuring share-level permissions.

- UNC paths: Configuring and troubleshooting network paths to access shared resources.

- Group Policy Management: Creating and configuring GPOs to automate workstation and user settings.

- Group Policy Preferences: Using Drive Maps to automatically assign network drives to domain users.

- User account verification: Using whoami to confirm the currently authenticated domain account.

- Windows 11 administration: Verifying network drive mappings through File Explorer.

- Access control and least privilege: Applying read-only permissions to limit unnecessary access.

- Troubleshooting and validation: Confirming that the drive mapping is present and available in the intended user's session.
