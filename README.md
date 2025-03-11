# python-password-generator
import random
import string

def generate_password(length=12, use_digits=True, use_special=True):
    characters = string.ascii_letters
    if use_digits:
        characters += string.digits
    if use_special:
        characters += string.punctuation

    password = ''.join(random.choice(characters) for _ in range(length))
    return password

print("Generated Password:", generate_password(16))


import pyshorteners

def shorten_url(url):
    shortener = pyshorteners.Shortener()
    return shortener.tinyurl.short(url)

url = input("Enter the URL: ")
print("Shortened URL:", shorten_url(url))

import qrcode

data = input("Enter text or URL: ")
qr = qrcode.make(data)
qr.save("qrcode.png")
print("QR Code saved as 'qrcode.png'")
import requests

API_KEY = "your_api_key_here"
city = input("Enter city name: ")
url = f"http://api.openweathermap.org/data/2.5/weather?q={city}&appid={API_KEY}&units=metric"

response = requests.get(url)
weather = response.json()
print(f"Weather in {city}: {weather['weather'][0]['description']}, {weather['main']['temp']}°C")


tasks = []

def add_task(task):
    tasks.append(task)
    print(f"Added: {task}")

def view_tasks():
    print("\nYour To-Do List:")
    for idx, task in enumerate(tasks, 1):
        print(f"{idx}. {task}")

while True:
    choice = input("\n1. Add Task\n2. View Tasks\n3. Exit\nChoose: ")
    if choice == '1':
        task = input("Enter task: ")
        add_task(task)
    elif choice == '2':
        view_tasks()
    elif choice == '3':
        break


import csv

def add_expense(amount, category):
    with open("expenses.csv", "a", newline='') as file:
        writer = csv.writer(file)
        writer.writerow([amount, category])
    print("Expense added!")

def view_expenses():
    with open("expenses.csv", "r") as file:
        reader = csv.reader(file)
        total = sum(float(row[0]) for row in reader)
        print(f"Total Expenses: ${total}")

while True:
    choice = input("\n1. Add Expense\n2. View Expenses\n3. Exit\nChoose: ")
    if choice == '1':
        amount = input("Enter amount: ")
        category = input("Enter category: ")
        add_expense(amount, category)
    elif choice == '2':
        view_expenses()
    elif choice == '3':
        break


import random

choices = ["rock", "paper", "scissors"]
user_choice = input("Choose rock, paper, or scissors: ").lower()
computer_choice = random.choice(choices)

print(f"Computer chose: {computer_choice}")

if user_choice == computer_choice:
    print("It's a tie!")
elif (user_choice == "rock" and computer_choice == "scissors") or \
     (user_choice == "scissors" and computer_choice == "paper") or \
     (user_choice == "paper" and computer_choice == "rock"):
    print("You win!")
else:
    print("You lose!")



responses = {
    "hello": "Hi there! How can I help you?",
    "how are you": "I'm just a bot, but I'm doing great!",
    "bye": "Goodbye! Have a nice day!"
}

while True:
    user_input = input("You: ").lower()
    if user_input in responses:
        print("Bot:", responses[user_input])
    else:
        print("Bot: Sorry, I don't understand.")
    if user_input == "bye":
        break
