# talktocsv
The aim of this project is to let any user use natural language to analyse a given csv file. This app uses several technologies to make this possible:
  * The interface is implemented using [streamlit](https://streamlit.io/);
  * The processing and analysing of the CSV file is done by [ChatGPT](https://chat.openai.com);
  * [Langchain](https://python.langchain.com/) does the translation from natural language to chatGPT prompt.

The methods created in this project are :
  1. create_pandas_dataframe_agent: an agent is a component that can help to tap into a collection of tools, making decisions on which to use based on the users’ input. There are mainly 2         categories of agents: “Action Agents” and “Plan-and-Execute Agents”.</br>
     Action Agents determine a course of action and carry it out by order, one by one phase. Moreover, they can take out and manage data from various sources, such as databases, APIs, and in       this particular scenario, a CSV file.
  2. csv_tools : This function allows a path of a CSV file as its input and a return agent that can access and use a large language model (LLM). this function generates an OpenAI object,           reads the CSV file and then converts it into a Pandas DataFrame. Finally, it formulates a Pandas DataFrame agent which is then returned.
  3. ask_agent : The query_agent function is the powerhouse of this process. It accepts a pandas_dataframe_agent and a query as input, returning the agent’s response in string format. the          function generates a prompt for the agent, specifying the type of responses we’re seeking. The goal is to have the agent provide a string that can subsequently be converted into a             dictionary. Depending on what’s contained within this dictionary, the program will manifest a graph, table, or simple text response.
  4. decode_response : this function will change the agent’s response, a string, into a dictionary for easier use.
  5. write_answer : This function accepts a response dictionary and uses it to display output on the Streamlit app. This could include answers, bar graphs, line graphs, and tables.

To use this app :
1. Install python;
2. Install the required libraries:</br>
   ```pip install langchain==0.0.146 , python-dotenv==1.0.0 , streamlit==1.22.0 , openai==0.27.7 , tabulate==0.9.0```
3. Set a environment variable called OPENAI_API_KEY with your own API Key avalailable [here](https://elephas.app/blog/how-to-get-chatgpt-api-key-clh93ii2e1642073tpacu6w934j)
   ```set OPENAI_API_KEY=<YOUR_OWN_API_KEY>```
4. Execute the following command to launch streamlit :
   ```streamlit run Talk_with_csv.py```
5. Load a CSV file and ask questions in natural language
     The file used for the test is on [github](https://github.com/tarikkaoutar/Talk_with_CSV).
   Ex:
   * Which Products have the highest order?
   * Tabulate the first 5 Products Include the Products and Order columns only?
   * Create a line graph on the first 5 products. use the Products as the column and Orders as a data values
   * Create a bar graph on the first 5 products. use the Products as the column and Orders as a data values
  
     
</br>This project is based on the tutorial found at https://levelup.gitconnected.com/talk-to-your-csv-how-to-visualize-your-data-with-langchain-and-streamlit-5cb8a0db87e0

