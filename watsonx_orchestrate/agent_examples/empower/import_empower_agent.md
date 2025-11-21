## Use the following steps as outlined in ADK documentation for the Empower Agent.
https://developer.watson-orchestrate.ibm.com/tutorials/tutorial_2_arrows_internal_employees


`cd` to the location of your watsonx orchestrate CLI and start the environment. See ADK Installation and Configuration Doc in this repo.
Now cd to the location of customer_care assets:
```
cd ./watsonx_technical_assets/watsonx_orchestrate/agent_examples/customer_care
```
Configure this as a root directory for this effort:
```
WORK_DIR=$PWD
```

## Configure customer care connections:
ServiceNow requires a live connection so we need to provide access to a servicenow instance

```
orchestrate connections add -a service-now
orchestrate connections configure -a service-now --env draft --type team --kind basic --url <the instance url>
orchestrate connections set-credentials -a service-now --env draft -u admin -p '<servicenow_password>'
```

Now publish (import) the customer_care tools to the server:
```
cd $WORK_DIR/tools/customer_care
```
```
orchestrate tools import -k python -f ./get_my_claims.py
orchestrate tools import -k python -f ./get_healthcare_benefits.py
```

Now publish (import) the service_now tools to the server:
```
cd $WORK_DIR/tools/service_now
```
```
orchestrate tools import -k python -f ./create_service_now_incident.py  -a service-now
orchestrate tools import -k python -f ./get_my_service_now_incidents.py -a service-now
```

Import Agents for both:
```
cd $WORK_DIR/agents
```
```
orchestrate agents import -f service_now_agent.yaml
orchestrate agents import -f customer_care_agent.yaml
```
