# F1-Analytics-AI
This is a SQL Agent AI tool built on langchain that can use natural language through an LLM to query a database and return relevant F1 race and qualifying statistics.

This project was written in Google Collab to take advantage of the free GPU resources but had to be refactored to use Gemini Pro

## The plan
F1 commentators keep coming up with fun F1 facts on the fly that are sometimes very specific. Most of the times they probably have a whole team on the side whose job is to provide these facts to the commentators but I wondered if I could write a tool that provided F1 data could answer similar questions for me.

By gathering publicly available (althought a bit out of date) F1 data from race and qualifying I am able to clean it up slightly and store this in a SQLite database.

Implementing RAG (Retrieval Augmented Generation) to generate SQL queries from natural language input using Langchain and a LLM model I am able to ask questions in natural language like:
`Which driver has won the most races?`

and have the LLM convert it into a valid SQL query that can be executed on the database:
`select driver, count(*) as race_wins from race where position = 1 group by driver order by race_wins desc limit 1;`

Execute it and return the answer in plain text like:
`Lewis Hamilton has won the most races.`

The responses of the AI are grounded on the data stored in the SQLite table, so you can be sure that the responses are correct if your data is correct.
