# dice_bot
telegram bot to roll dice
/////////////////////////////


import telebot
import random

API_KEY = '6182784711:AAEHZQjGkfURzEv26T-4qaM5YycbG2Z_zwc'
bot = telebot.TeleBot(API_KEY)

# Roll two dice and return the result
def roll_dice():
    dice1 = random.randint(1, 6)
    dice2 = random.randint(1, 6)
    return (dice1, dice2)

@bot.message_handler(commands=['roll'])
def roll(message):
    dice = roll_dice()
    result = f"🎲 You rolled {dice[0]} and {dice[1]} 🎲"
    bot.send_message(message.chat.id, result)

bot.infinity_polling()
