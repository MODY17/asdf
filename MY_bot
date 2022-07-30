import telebot
from telebot import types
import requests,random
import redis
from redis import Redis

db = Redis(host='localhost',port="6379")
bot = telebot.TeleBot("5369185184:AAH88K0Wg_73fImt0623etRTCnmCrFqRkZA")
a = list()
@bot.message_handler(commands=['start'])
def st(message):
    key = types.InlineKeyboardMarkup()
    key.row_width = 2
    btn2 = types.InlineKeyboardButton(text="- فحص يوزرات رباعية .",callback_data="l4")
    btn3 = types.InlineKeyboardButton(text="- فحص يوزرات خماسية .",callback_data="l5")
    btn4 = types.InlineKeyboardButton(text="- المبرمج .",url="t.me/ttrakosz")
    key.add(btn2)
    key.add(btn3)
    key.add(btn4)

    bot.reply_to(message,f"- اهلا بك في بوت فحص يوزرات Tiki\n- يمكنك الاختيار طريقة الفحص من الاسفل .",reply_markup=key)
@bot.callback_query_handler(func=lambda call:True)
def quwery(call):
    if call.data ==  "l4":
        l3(call.message)
    if call.data == "l5":
        l5(call.message)
def l3(message):
    fall = 0
    true = 0

    for i in range(25):
        u = "abcdefghijklmonopqrxmjqieur123456789"
        usr = ("".join(random.choice(u) for i in range(4)))

        url = requests.get(f"https://tiki.video/@{usr}/?lang=en").status_code
        if url == 404:
            true+=1
            a.append(usr)
            bot.send_message(message.chat.id,f"<strong>تم صيد يوزر جديد : {usr}</strong>",parse_mode="html")
        else:
            fall+=1
            key2 = types.InlineKeyboardMarkup()
            key2.row_width = 1
            btn1 = types.InlineKeyboardButton(text=f"- عدد المتاح : {true}", callback_data="none")
            btn2 = types.InlineKeyboardButton(text=f"- عدد غير المتاح : {fall}", callback_data="none")
            btn3 = types.InlineKeyboardButton(text=f"- يتم فحص : {usr}", callback_data="none")
            key2.add(btn1, btn2, btn3)
            bot.edit_message_text(chat_id=message.chat.id,message_id=message.message_id,text=f"<strong>يتم الفحص الان ....</strong>",parse_mode="html",reply_markup=key2)
def l5(message):
    fall = 0
    true = 0

    for i in range(25):
        u = "abcdefghijklmonopqrxmjqieur123456789"
        usr = ("".join(random.choice(u) for i in range(5)))

        url = requests.get(f"https://tiki.video/@{usr}/?lang=en").status_code
        if url == 404:
            true+=1
            a.append(usr)
            bot.send_message(message.chat.id,f"<strong>تم صيد يوزر جديد : {usr}</strong>",parse_mode="html")
        else:
            fall+=1
            key2 = types.InlineKeyboardMarkup()
            key2.row_width = 1
            btn1 = types.InlineKeyboardButton(text=f"- عدد المتاح : {true}", callback_data="none")
            btn2 = types.InlineKeyboardButton(text=f"- عدد غير المتاح : {fall}", callback_data="none")
            btn3 = types.InlineKeyboardButton(text=f"- يتم فحص : {usr}", callback_data="none")
            key2.add(btn1, btn2, btn3)
            bot.edit_message_text(chat_id=message.chat.id,message_id=message.message_id,text=f"<strong>يتم الفحص الان ....</strong>",parse_mode="html",reply_markup=key2)

bot.infinity_polling()
