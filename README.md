[Chat Bot TextEmbeddings-Gecko@001 Model]

Flask Application Endpoint to use the chatbot on the front end. It uses a csv file containing the questions, answers and its generated embeddings which can be used for similarity comparison 
between the user input. It also stores logs for user input in the static directory.
Chat Bot using Google's Gecko@001 Model to generate Text Embeddings and using cosine similarity, built a Chat Bot.
Evaluation mechanism for the chat bot by automatically generating test questions (variations of the original data) and giving the Chatbot's Response, Ground Truths and the accuracy score.
