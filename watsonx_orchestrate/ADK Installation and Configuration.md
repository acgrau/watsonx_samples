# Installing and Configuring watsonx Orchestrate Agent Developer Kit

## Installation
The information provided is taken from the following reference documentation and assumes you are running on a mac: https://developer.watson-orchestrate.ibm.com/getting_started/installing

### Step1 - Set up your environment 
(ref: https://developer.watson-orchestrate.ibm.com/getting_started/installing#before-you-begin) 
#

Create a new project folder for your local development and `cd` into the folder.
ex:
```
mkdir wxo
cd wxo
```
Now create a local python 3.11 environment. 
(If you don't have pyenv installed then use `brew install pyenv`) <br>
```
pyenv install 3.11.14  
```
```
pyenv local 3.11.14
```
```
python -m venv .venv
```
You should now see a .venv folder in your project directory (`ls -al`). This will be your local python working environment.

Confirm you can activate the local environment <br>
```
source ./.venv/bin/activate
```

### Step 2: Install the watsonx Orchestrate ADK
```
pip install ibm-watsonx-orchestrate
```

You now have the orchestrate CLI install and ready to interact with running instances of watsonx Orchestrate.
```
(.venv) agrau@Alfonsos-MacBook-Pro wxo % orchestrate
                                                                                                                                                        
 Usage: orchestrate [OPTIONS] COMMAND [ARGS]...                                                                                                         
                                                                                                                                                        
╭─ Options ────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────╮
│ --version                     Show the installed version of the ADK and Developer Edition Tags                                                       │
│ --debug                       Enable debug mode                                                                                                      │
│ --install-completion          Install completion for the current shell.                                                                              │
│ --show-completion             Show completion for the current shell, to copy it or customize the installation.                                       │
│ --help                        Show this message and exit.                                                                                            │
╰──────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────╯
╭─ Commands ───────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────╮
│ env               Add, remove, or select the activate env other commands will interact with (either your local server or a production instance)      │
│ agents            Interact with the agents in your active env                                                                                        │
│ tools             Interact with the tools in your active env                                                                                         │
│ toolkits          Interact with the toolkits in your active env                                                                                      │
│ knowledge-bases   Upload knowledge your agents can search through to your active env                                                                 │
│ connections       Interact with the agents in your active env                                                                                        │
│ voice-configs     Configure voice providers to enable voice interaction with your agents                                                             │
│ server            Manipulate your local Orchestrate Developer Edition server [requires entitlement]                                                  │
│ chat              Launch the chat ui for your local Developer Edition server [requires entitlement]                                                  │
│ models            List the available large language models (llms) that can be used in your agent definitions                                         │
│ channels          Configure channels where your agent can exist on (such as embedded webchat)                                                        │
│ evaluations       Evaluate the performance of your agents in your active env                                                                         │
│ copilot           Access AI powered assistance to help refine your agents                                                                            │
│ settings          Configure the settings for your active env                                                                                         │
│ partners          Generate a well-structured, submission-ready agent artifact package for partner-built agents                                       │
╰──────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────╯
```

## Configure your target watsonx environments
You now need to define the target Orchestrate service you will be connecting to and for which you will be creating tools/agents. For this you will need to gather following information from you watsonx Orchestrate instance:
- watsonx orchestrate service url
- apikey for that service.

To access this information in your IBM Cloud watsonx Orchestrate instance, open your environment and then go to Settings on top right:

<img width="1548" height="991" alt="image" src="https://github.com/user-attachments/assets/8778703a-8dbf-4954-acfd-4dd3d2c017c7" />

<br></br>

Then click on API Details tab, generate an API key, and record the service instance URL. Be sure to copy your API Key value once its shown or you will not be able retrieve it after the fact. 
<img width="1546" height="536" alt="image" src="https://github.com/user-attachments/assets/a7c8ecbf-0265-4964-8a42-0c1a46a4f9e1" />

Here is sample page with apikey details for creation: 

<img width="600" height="461" alt="image" src="https://github.com/user-attachments/assets/ad281556-813e-4bb5-a097-1559f33e17e8" />

Click Create and then copy or download the key. 

<img width="500" height="212" alt="image" src="https://github.com/user-attachments/assets/eb893bcc-6965-4bf5-a6c0-99b589a2c902" />

<br/>

You are now ready to add the environment to local orchestrate CLI environment.
```
orchestrate env add -n <provide_a_logical_name_for_your_own_reference> -u <replace_with_your_service_url>
```
You can add multiple target environments to the CLI but only one can be active at a time. This allows you to control which instance of Orchestrate you would like to connect with.
Activate this new instance:
```
orchestrate env activate <logical_name_you_used_above> --api-key <APIKEY_recorded_above>
```
You can now see a list of available environments:
```
orchestrate env list
```
```
(.venv) agrau@Alfonsos-MacBook-Pro wxo % orchestrate env list
 grau-cloud  https://api.us-south.watson-orchestrate.cloud.ibm.com/instances/XXX  (active) 
(.venv) agrau@Alfonsos-MacBook-Pro wxo %
```

Test your connection:
```
orchestrate agents list
```
You should see a tabluar list of agents that exist in the active service you are working with.

For more information, please see the ADK Guide: https://developer.watson-orchestrate.ibm.com/getting_started/what_is
