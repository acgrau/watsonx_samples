## Use the following steps as outlined in ADK documentation for the Empower Agent.

See https://developer.watson-orchestrate.ibm.com/tutorials/tutorial_2_arrows_internal_employees for details on this sample implementation.
#

### Clone this repo
```
git clone https://github.com/acgrau/watsonx_technical_assets.git
```

`cd` to the location of your watsonx orchestrate CLI and start the environment. See ADK Installation and Configuration Doc in this repo.
Now cd to the location of customer_care assets:
```
cd ./watsonx_technical_assets/watsonx_orchestrate/agent_examples
```
Configure this as a root directory for this effort:
```
WORK_DIR=$PWD/empower
```

### Configure needed connections:
Step 1: Make sure you are running the following commands from within the virtual environment. ie. from the defined folder where you installed the ADK you need to run 
```
. ./.venv/bin/activate
```
and you should see the (.venv) in the system prompt. ex:
```
(.venv) agrau@Alfonsos-MacBook-Pro wxo %
```

Step 2: ServiceNow requires a live connection so we need to create and configure a `connection` to a servicenow instance. 
```
orchestrate connections add -a service-now
orchestrate connections configure -a service-now --env draft --type team --kind basic --url <snow_instance_url>
orchestrate connections set-credentials -a service-now --env draft -u <servicenow_username> -p '<servicenow_password>'
```

Step 3: Publish (import) the customer_care and service_now tools to the server:
```
cd $WORK_DIR/tools/customer_care
```
```
orchestrate tools import -k python -f ./get_my_claims.py
orchestrate tools import -k python -f ./get_healthcare_benefits.py
```

```
cd $WORK_DIR/tools/servicenow
```
```
orchestrate tools import -k python -f ./create_service_now_incident.py  -a service-now
orchestrate tools import -k python -f ./get_my_service_now_incidents.py -a service-now
```

Step 4: Publish (Import) the customer care `agent` and the servicenow collaborator `agent`:
```
cd $WORK_DIR/agents
```
```
orchestrate agents import -f service_now_agent.yaml
orchestrate agents import -f customer_care_agent.yaml
```
#### You can now access yout watsonx Orchestrate service and view the local agents and tools. You will see the `customer_care_agent` available and configured with healthcare tools a collaborative service_now agent.
