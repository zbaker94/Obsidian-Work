- User-facing chat interface (chat gpt for JOTS)
	*Provides help resources, basic application support, and data analysis via a chat-like interface embedded on JOTS*
	- 

- Command API that uses AI to call a sequence of events (direct accusal command -> appropriate api calls)
	*Tool has access to a list of endpoints (using the openapi spec) that describe their purpose, inputs, and outputs. The front end provides arbitrary commands to the AI which then calls the necessary endpoints in the proper order.*
	- 

- Internal tool that looks at sql diff between environments and generates patch script for CI/CD
	*API endpoint that generates 2 SQL files (or series therein) and prompts the AI with them. The AI responds with a single SQL script that will resolve the diff. Possible that we want to do a dry run of the script?*
	- 

- AI Suggested Charge Boilerplate
	*Custom trained model trained on existing boilerplate correlated with charges. Accepts input of charge and generates some number of new boilerplate texts based on the charge info*
	- 






