# Python

import discord
from discord.ext import commands
from mantik import *
import random

#ayrıcakları tanımlıyoruz.
ayricaliklar = discord.Intents.default()
#Mesaj içeriklerine ulaşım sağlamamı sağlar.
ayricaliklar.message_content = True

# prefix parametresine odaklayın - bu, komutları tanımlamamızı sağlayan bir tanımlayıcıdır!
bot = commands.Bot(command_prefix='$', intents=ayricaliklar)


@bot.event
async def on_ready():
    print(f'{bot.user} olarak giriş yaptık')


#bot komutlarını işleyen komutu yazmak.
@bot.command
async def hello(ctx):
    await ctx.send(f'Merhaba {bot.user}! Ben bir botum!')

@bot.command()
async def pasw(ctx):
    await ctx.send(sifre_olusturucu(10))

bot.run("")

# bot_logic in original




def sifre_olusturucu(sifre_uzunlugu):
    ogeler = "+-/*!&$#?=@<>"
    sifre = ""

    for i in range(sifre_uzunlugu):
        sifre += random.choice(ogeler)

    return sifre


def emoji_olusturucu():
    emoji = ["\U0001f600", "\U0001f642", "\U0001F606", "\U0001F923"]
    return random.choice(emoji)


def yazi_tura():
    para = random.randint(0, 2)
    if para == 0:
        return "YAZI"
    else:
        return "TURA"
