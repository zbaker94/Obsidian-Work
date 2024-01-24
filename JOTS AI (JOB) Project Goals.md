- User-facing chat interface (chat gpt for JOTS)
	*Provides help resources, basic application support, and data analysis via a chat-like interface embedded on JOTS*
	- Uses text or vector search to inspect provided resources 
		- database
			- Proxy access via an api
			- AI captures search terms or IDs and calls corresponding endpoint(s)
		- help docs
			- Provides help steps 
			- Feature documentation
	- Service then sends data back to AI
		- transforms into digest-able, interactive text
	- Send alert to slack / email if user still needs help

- Command API that uses AI to call a sequence of events
	*Tool has access to a list of endpoints (using the openapi spec) that describe their purpose, inputs, and outputs. The front end provides arbitrary commands to the AI which then calls the necessary endpoints in the proper order.*
	- AI takes in a command
	- Determines which endpoint(s) to call with which parameters
	- API then calls proper endpoints in proper order
	- The AI may then format the returned data as needed

- Internal tool that looks at sql diff between environments and generates patch script for CI/CD
	*API endpoint that takes in 2 SQL files (or series therein) and prompts the AI with them. The AI responds with a single SQL script that will resolve the diff.*
	- 

- AI Suggested Charge Boilerplate
	*Custom model trained on existing boilerplate correlated with charges. Accepts input of charge and generates some number of new boilerplate texts based on the charge info*
	- 






