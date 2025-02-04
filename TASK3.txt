import nltk
from nltk.chat.util import Chat, reflections

# Download necessary NLTK data
nltk.download('punkt')

# Define patterns and responses
patterns = [
    (r'hi|hello|hey', ['Hello!', 'Hi there!', 'Hey!']),
    (r'how are you?', ['I am good, thank you!', 'I am doing well, how about you?']),
    (r'what is your name?', ['I am a chatbot. You can call me ChatBot.']),
    (r'what can you do?', ['I can answer your questions, have a chat, and help you with basic information.']),
    (r'quit|bye|exit', ['Bye! Take care.', 'Goodbye!', 'It was nice talking to you.']),
    (r'(.*) your name?', ['I am a chatbot. You can call me ChatBot.']),
    (r'(.*) help (.*)', ['Sure, I can help you. What do you need help with?']),
    (r'(.*) (weather|temperature) (.*)', ['I am sorry, I cannot provide weather information.']),
    (r'(.*)', ['I am sorry, I do not understand. Can you please rephrase?']),
]

# Create the chatbot
chatbot = Chat(patterns, reflections)

def chat():
    print("Hello! I am a chatbot. Type 'quit' to exit.")
    while True:
        user_input = input("You: ")
        if user_input.lower() in ['quit', 'bye', 'exit']:
            print("ChatBot: Goodbye!")
            break
        response = chatbot.respond(user_input)
        print(f"ChatBot: {response}")

# Run the chatbot
if __name__ == "__main__":
    chat()