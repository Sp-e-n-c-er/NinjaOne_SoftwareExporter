### What the Project Does
The **NinjaOne Software Inventory Exporter** is a PowerShell script with a WPF-based graphical user interface (GUI) that leverages the NinjaOne Public API to retrieve, filter, and export software inventories from specified organizations. The tool allows users to:
- Select organizations to query or process all organizations.
- Exclude predefined or custom software (e.g., Microsoft Office, .NET, Windows bloatware) via a dynamic exclusion list.
- Choose how software versions are displayed (hide, combine, or list separately).
- Export detailed software inventories to CSV files per organization or as a master list, including fields like software name, publisher, versions, device count, device names, install date, size, and last updated timestamp.
- Browse and export specific software details across devices in a dedicated "All Installed Software" tab, with double-click functionality to view granular details (e.g., per-device version and install date).

The script uses asynchronous API calls for efficient data retrieval.

### The Problem It Solves
Managing software inventories across multiple organizations in NinjaOne can be time-consuming and error-prone, especially for MSPs or IT teams overseeing diverse client environments. 
Key challenges include:
- **Manual Data Collection**: Retrieving software data for compliance, auditing, or licensing purposes requires navigating the NinjaOne portal or running multiple API queries manually.
- **Data Overload**: Default software lists include irrelevant bloatware (e.g., Windows Calculator) or common applications (e.g., Office, .NET), cluttering reports.
- **Report Customization**: Teams need flexible ways to format software data.
- **Scalability**: Exporting data for multiple organizations or specific software across devices is repetitive and slow without automation.

This tool automates the entire process, from data retrieval to customized CSV exports, saving hours of manual work and providing clear, actionable insights into software deployments.

### Who It Helps
- **MSP Technicians**: Quickly generate compliance reports or audit software installations for clients, filtering out irrelevant applications.
- **IT Administrators**: Monitor software usage across enterprise devices to ensure licensing compliance or identify outdated versions.
- **Compliance Teams**: Export detailed software inventories for regulatory audits, with customizable version reporting.
- **Service Desk Teams**: Investigate specific software deployments (e.g., which devices have a particular application) for troubleshooting or planning.

### Key API Endpoints Used
- **POST /ws/oauth/token**: Authenticates with the NinjaOne API to obtain an access token using client credentials.
- **GET /api/v2/organizations**: Retrieves the list of organizations for user selection.
- **GET /api/v2/queries/software**: Fetches software inventory data, filtered by organization ID (e.g., `queries/software?df=org={OrgID}`).
- **GET /api/v2/devices**: Retrieves device details (e.g., system names) to map device IDs to human-readable names in exports.

This is the main Screen After Connection, Icon Turns Green and Displays All Orgs.
Located on the left is a set of predefined software that will be excluded from the report, this is all Common MS software that is installed on all devices, you can add or remove them as you wish! 
![image](https://github.com/user-attachments/assets/f28da43b-c6c8-4d09-8efb-fe37ad2fe99e)

"All Software Screen"

This will display all software that is currently installed and pulled by Ninja, you can search and select individual software and the script will export all devices with that software installed.
![image](https://github.com/user-attachments/assets/f16a7a4a-581c-4812-a0d6-830d105469cc)

"Software Details Screen"

Need a quick look without needing to export? Double clicking on any software will also bring up a new UI, this will display useful information about the software to include

Device its Installed on,
Version,
Publisher,
Product Code,
Install Date,
Location (If Ninja reports it),
Size (If Ninja reports it),
Last Updated,
![image](https://github.com/user-attachments/assets/18d1a1ee-6d6d-454e-83e4-daa8acd23278)

"Running an Export"

Running an export for an org will export that orgs CSV and place them in the directory that you specified, if the org has no data to export, it will simply skip it.

As shown below, I have exported multiple orgs CSVs 
![image](https://github.com/user-attachments/assets/abf5ab59-75f7-4dc7-99f4-b23994fd3b1e)

"Custom Settings"

Exclude common apps that you might not want to see at the moment
Office Apps,
.Net,
C++ Redist,

Variable Version Output
Hide Versions (Will hide all software versions from the output, listing only the software),
Combine versions (Will combine all versions into a single line, with one column showing all versions installed),
List Each Version (Will list every application and each version that is installed and what device its installed on),
 
![image](https://github.com/user-attachments/assets/9e1d4b29-1490-4ef0-8ca9-294e0943efde)

Clicking "Save Config" will save your current settings in a JSON file, and upon running the script it will autoload that JSON so you easily retain custom settings you want! 
Also, its in DARK MODE!
