# Service-Bot
class Chatbot:
    def __init__(self):
        self.queries = []  # List to store queries asked by users
        self.solutions = {}  # Dictionary to store solutions provided by the merchant

    def ask_question(self, user, question):
        """A user asks a question."""
        print(f"{user.name} asks: {question}")
        # Add the question to the list
        self.queries.append(question)
        # Check if solution already exists
        if question in self.solutions:
            return self.solutions[question]
        else:
            return "I'm not sure about that. Let me check with the merchant."

    def provide_solution(self, merchant, question, solution):
        """Merchant provides a solution to a question."""
        print(f"{merchant.name} provides solution: {solution}")
        # Store the solution for future queries
        self.solutions[question] = solution

    def train_chatbot(self):
        """Train the chatbot using accumulated queries and solutions."""
        print("\nTraining the chatbot with accumulated queries and solutions...")
        for question, solution in self.solutions.items():
            print(f"Training with: Question: '{question}' -> Solution: '{solution}'")
        print("Chatbot trained successfully!")


class User:
    def __init__(self, name):
        self.name = name

class Merchant:
    def __init__(self, name):
        self.name = name

# Simulation of the system
if __name__ == "__main__":
    # Create the Chatbot
    chatbot = Chatbot()

    # Create user and merchant accounts
    user1 = User("Alice")
    merchant1 = Merchant("Bob")

    # User asking a question
    response = chatbot.ask_question(user1, "What is the warranty period of this product?")
    print("Chatbot responds:", response)

    # Merchant providing a solution
    chatbot.provide_solution(merchant1, "What is the warranty period of this product?", "The warranty period is 2 years.")

    # User asking the same question again
    response = chatbot.ask_question(user1, "What is the warranty period of this product?")
    print("Chatbot responds:", response)

    # Train the chatbot based on previous queries and solutions
    chatbot.train_chatbot()
