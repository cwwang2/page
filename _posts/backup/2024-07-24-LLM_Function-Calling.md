# Function Calling with Open LLM
## What is function calling in Open LLM?
Function calling is OpenAI's way of allowing LLM to call a function that you predefined. LLM decide where, when to your function

## Available Function Calling directly from LLM with LangChain
- llama3-groq-tool-use 8B
- mistral-nemo 12B

## How to use function calling in Open LLM?
```python
from typing import List
from typing_extensions import TypedDict
from langchain_ollama import ChatOllama

def validate_user(user_id: int, addresses: list) -> bool:
    # Your code here
    return True

llm = ChatOllama(
    model = 'llama3-groq-tool-use:8b-q8_0',
    temperature = 0, 
).bind_tools([validate_user])
result = llm.invoke("Could you validate user 123? They previously lived at 123 Fake St in Boston MA and 234 Pretend Boulevard in Huston TX.")

print(result)
```

```bash
{'name': 'validate_user', 'args': {'addresses': ['123 Fake St, Boston MA', '234 Pretend Boulevard, Houston TX'], 'user_id': 123}, 'id': '75a95f61-8e4c-4813-ac67-8efb8f1abbc7', 'type': 'tool_call'}
```


## Agent


