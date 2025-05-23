# 🧠 MCP Server for bunq API

This is an [MCP]([https://github.com/latentspace/mcp](https://docs.anthropic.com/en/docs/agents-and-tools/mcp)) (Model Context Protocol) server that connects to the [bunq](https://www.bunq.com) banking API. It exposes a wide range of tools to interact with bunq, including payments, invoices, cards, and more via a chat agent. 

You can use this with Claude Desktop or other MCP-compatible clients.

---
> ⚠️ **WARNING: Running in PRODUCTION**
>
> Be extremely cautious when setting `BUNQ_ENVIROMENT="PRODUCTION"` in your `.env` file.  
> This will connect the MCP server to your live bunq account.  
> Make sure you understand the implications, verify API permissions, and never expose your production API key publicly.
> We take no responsibility for any money lost



## 🚀 Quick Start

### 1. Clone the repository and install dependencies

```bash
git clone https://github.com/two-trick-pony-NL/bunq-model-context-protocol-server.git
cd bunq-MCP
pip install -r requirements.txt
```
2. Add a .env file
In the root of the project, create a .env file with the following content:

```
BUNQ_API_KEY="sandbox_your_key"
BUNQ_ENVIROMENT="SANDBOX"

```

Request a bunq sandbox API key here: 
```
curl --location --request POST 'https://public-api.sandbox.bunq.com/v1/sandbox-user-person' \
--header 'Content-Type: application/json' \
--header 'User-Agent: postman' \
--data ''

```
production keys can be fetched from your app

For production, set BUNQ_ENVIROMENT to PRODUCTION.

3. Run the server
```
python3 main.py
```
🧠 Using with Claude Desktop
Add the server to your Claude Desktop config.json:

```
{
  "mcpServers": {
    "bunq": {
      "command": "python3",
      "args": [
        "/Users/[path to the script]/main.py"
      ]
    }
  }
}
```


🔧 Tools Included
This server exposes the following tools via the MCP interface:

get_user_id

get_user_display_name

get_primary_monetary_account_id

get_list_monetary_accounts

list_user_invoices

get_subscription_contracts

send_payment

request_money

create_card

fetch_last_payments

schedule_payment

generate_bunq_me_link

These tools use the official bunq SDK and return structured Python objects.


📁 Project Structure
```
.
├── main.py         # MCP server for bunq
├── .env            # Your bunq API key and environment
├── README.md       # This file\
```

🧑‍💻 License
MIT — feel free to fork and modify.

