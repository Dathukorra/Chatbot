# Chatbot
python using chatbot
import nltk
from nltk.chat.util import Chat, reflections
import tkinter as tk

# Download necessary nltk resources (only required once)
nltk.download('punkt')

# Define a set of pairs for the chatbot
chat_pairs = [
    (r"hi|hello|hey", ["Hello! How can I help you today?"]),
    (r"what is your name?", ["I'm a chatboot, created by Dathu !"]),
    (r"how are you?", ["I'm doing great, thank you! How can Dathu help you?"]),
    (r"what can you do?", ["Dathu can answer your questions and chat with you!"]),
    (r"(.*)", ["I'm sorry, I didn't understand that. Can you rephrase?"])
]


chatbot = Chat(chat_pairs, reflections)

# Define the function to handle chat interaction
def respond():
    user_input = entry.get()  # Get the input from the user
    response = chatbot.respond(user_input)  # Get the chatbot's response
    text_output.insert(tk.END, "Dathu: " + user_input + '\n')  # Display user's input
    text_output.insert(tk.END, "Chatbot: " + response + '\n\n')  # Display chatbot's response
    entry.delete(0, tk.END)  # Clear the input field after sending

# Create the GUI window
window = tk.Tk()
window.title("Chatbot")

# Create a scrollable text widget to display conversation
text_output = tk.Text(window, height=15, width=50)
text_output.pack(padx=10, pady=10)

# Create the input field for the user
entry = tk.Entry(window, width=40)
entry.pack(padx=10, pady=10)

# Create the send button
send_button = tk.Button(window, text="Send", command=respond)
send_button.pack(pady=10)

# Start the Tkinter event loop
window.mainloop()



