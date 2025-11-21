# Installing and Configuring watsonx Orchestrate Agent Developer Kit

## Installation
The information provided is taken from the following reference documentation and assumes you are running on a mac: https://developer.watson-orchestrate.ibm.com/getting_started/installing

### Step1 - Set up your environment (ref: https://developer.watson-orchestrate.ibm.com/getting_started/installing#before-you-begin) <br>
Make sure you have python 3.11 installed. If not install using: 
```
brew install python@3.11
```
Create a new project folder for your local development and `cd` into the folder.
ex:
```
mkdir wxo
cd wxo
```
Now create a local python environment. 
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

### Step 2: Install the local install of watsonx Orchestrate 
```
pip install ibm-watsonx-orchestrate
```

You now have the orchestrate CLI install and ready to interact with running instances of watsonx Orchestrate.
```
(.venv) agrau@Alfonsos-MacBook-Pro temp % orchestrate
                                                                                                                                                        
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

## Configure your target watsonx services
You now need to define the target service you will be connecting to and for which you will be creating tools/agents. For this you will need to gather:
- watsonx orchestrate service url
- apikey for that service.





## 


