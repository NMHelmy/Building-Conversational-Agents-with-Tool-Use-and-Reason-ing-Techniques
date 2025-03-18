# CSAI 422: Laboratory Assignment 4
# Building Conversational Agents with Tool Use and Reasoning Techniques

This repository contains a conversational agent that can answer weather-related questions and perform calculations using three different reasoning strategies: Basic, Chain of Thought (CoT), and ReAct. 
The agent integrates with the OpenAI API and a weather API to provide real-time weather data and perform reasoning tasks.

## Setup Instructions
  - Python 3.8 or higher.
  - An OpenAI API key.
  - A WeatherAPI key (from weatherapi.com).
  - A .env file to store your API keys.

## Installation
Clone the repository:
  - ***git clone https://github.com/your-username/conversational-agent.git***
  - ***cd conversational-agent***
Install the required dependencies:
 - ***pip install -r requirements.txt***

In the .env file add your API keys:
  - API_KEY=your_openai_api_key<br>BASE_URL=your_openai_base_url<br>LLM_MODEL=your_openai_model<br>WEATHER_API_KEY=your_weatherapi_key

Run the conversational agent:
  - ***python conversational_agent.py***

## Implementation Documentation
#### Basic Agent:
- Provides straightforward responses to weather-related queries.
- Uses the get_current_weather and get_weather_forecast tools.

#### Chain of Thought (CoT) Agent:
- Breaks down complex queries into smaller steps.
- Uses tools to gather information and explains its reasoning step-by-step.
- Includes a calculator tool for mathematical calculations.

#### ReAct Agent:
- Combines reasoning and acting to solve problems.
- Follows the ReAct pattern: Thought → Action → Observation → Final Answer.
- Includes a simulated web search tool for additional information.

### Tools
#### Weather Tools:
- get_current_weather: Fetches the current weather for a location.
- get_weather_forecast: Fetches the weather forecast for a location.

#### Calculator Tool:
- calculator: Evaluates mathematical expressions.

#### Web Search Tool:
- web_search: Simulates a web search for information.

## Comparative Evaluation
- The system allows users to compare the responses of all three agents side by side.
- Users can rate each response on a scale of 1-5.
- Results are saved to a CSV file (agent_evaluation.csv) for analysis

## Running the Code
When you run the code, you will be prompted to choose between two options:

#### Single Agent:
- Run the conversational agent with a single reasoning strategy (Basic, Chain of Thought, or ReAct).
- You will be asked to choose the agent type (Basic, Chain of Thought, or ReAct).
- The agent will process your queries using the selected reasoning strategy.

#### Comparative Evaluation:
- Run the conversational agent with all three reasoning strategies (Basic, Chain of Thought, and ReAct).
- The system will process your query using all three agents and display their responses side by side.
- You will be asked to rate each response on a scale of 1-5.
- The results will be saved to a CSV file (agent_evaluation.csv) for later analysis.

## Example Conversations
#### 1. Basic Agent
User: What's the weather in Paris today?
<br>Agent: The current weather in Paris is:
<br>
  <br>Temperature: 12.3°C (54.1°F)
  <br>Condition: Partly cloudy
  <br>Humidity: 65%
  <br>Wind Speed: 8.5 kph

#### 2. Chain of Thought (CoT) Agent
User: What's the temperature difference between Tokyo and Sydney today?
<br>Agent: Let me calculate the temperature difference between Tokyo and Sydney today.
<br>
  <br>Fetching the current temperature for Tokyo...
  <br>Fetching the current temperature for Sydney...
  <br>Calculating the difference...
  <br>The current temperatures are:
  <br>Tokyo: 5.3°C
  <br>Sydney: 21.2°C
  <br>The temperature difference is:
  <br>21.2°C - 5.3°C = 15.9°C
  <br>So, the temperature difference between Tokyo and Sydney today is 15.9°C.

#### 3. ReAct Agent
User: Is it hotter in New York or London right now?
<br>Agent: Let me check the current temperatures in New York and London.
<br>
  <br>Thought: I need to find the current temperatures in both New York and London.
  <br>Action: Use get_current_weather for New York.
  <br>Observation: New York is at 15.6°C.
  <br>Thought: Now I need London's temperature.
  <br>Action: Use get_current_weather for London.
  <br>Observation: London is at 5.3°C.
  <br>Thought: Now I can compare the two temperatures.
  <br>Final Answer: New York is hotter than London right now, with a temperature difference of 10.3°C.

## Analysis of Reasoning Strategies
### Basic Agent
Strengths: Simple and straightforward. Works well for direct queries like "What's the weather in Paris?"
<br>Limitations: Cannot handle complex queries requiring multiple steps or reasoning.

### Chain of Thought (CoT) Agent
Strengths: Breaks down complex queries into smaller steps, making it easier to follow. Provides detailed explanations.
<br>Limitations: May be slower due to the step-by-step approach.

### ReAct Agent
Strengths: Combines reasoning and acting, making it highly effective for complex queries. Follows a clear pattern (Thought → Action → Observation).
<br>Limitations: Requires more computational resources and may be overkill for simple queries.

## Challenges and Solutions
1. Handling Complex Queries
<br>Challenge: The Basic Agent could not handle queries requiring multiple steps (e.g., temperature differences between cities).
<br>Solution: Implemented the Chain of Thought and ReAct agents to break down complex queries into smaller steps.

2. Tool Integration
<br>Challenge: Ensuring the agent correctly invokes tools like get_current_weather and calculator.
<br>Solution: Added error handling and validation to ensure tools are used correctly.

3. Comparative Evaluation
<br>Challenge: Displaying responses from all three agents side by side and collecting user ratings.
<br>Solution: Implemented a comparative evaluation system that runs all agents, displays their responses, and saves the results to a CSV file.

## Note on Comparative Evaluation
- When running the Comparative Evaluation option, it is normal for the process to take some time. This is because:
- Multiple API Calls: The system makes separate API calls for each agent (Basic, Chain of Thought, and ReAct).
- Step-by-Step Reasoning: The Chain of Thought and ReAct agents perform additional reasoning steps, which can increase processing time.
- Tool Invocations: Each agent may invoke tools like get_current_weather or calculator, which require additional time to execute.

Please be patient while the system processes your query and generates responses from all three agents.
<br>
<br>This project demonstrates the power of different reasoning strategies in conversational agents. By comparing the Basic, Chain of Thought, and ReAct agents, we can see how each approach affects the quality and clarity of responses. The comparative evaluation system provides valuable insights for further improvements.
