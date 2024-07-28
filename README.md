# Bot_de_discord
Dis_bot es un bot divertido para tu servidor de Discord. Usa los siguientes comandos:  $hello – Saluda. $bye – Despide. $sing [canción] – Canta canciones como "Twinkle Twinkle" o "Happy Birthday".  ¡Disfruta!
import discord
from discord.ext import commands

# Configuración de los intents para el bot
intents = discord.Intents.default()
intents.message_content = True

# Crear una instancia del bot con el prefijo de comandos
bot = commands.Bot(command_prefix='$', intents=intents)

@bot.event
async def on_ready():
    print(f'Bot ha iniciado sesión como {bot.user}')

@bot.command()
async def hello(ctx):
    await ctx.send("Hello there! How's it going?")

@bot.command()
async def bye(ctx):
    await ctx.send("Goodbye! See you next time!")

@bot.command()
async def sing(ctx, *, song: str):
    if song.lower() == 'twinkle twinkle':
        lyrics = """
        Twinkle, twinkle, little star,
        How I wonder what you are!
        Up above the world so high,
        Like a diamond in the sky.
        
        Twinkle, twinkle, little star,
        How I wonder what you are!
        """
        await ctx.send(lyrics)
    elif song.lower() == 'happy birthday':
        lyrics = """
        Happy birthday to you,
        Happy birthday to you,
        Happy birthday dear [Name],
        Happy birthday to you!
        """
        await ctx.send(lyrics)
    else:
        await ctx.send("Sorry, I don't know that song.")

@bot.event
async def on_message(message):
    if message.author == bot.user:
        return
    # Procesar los comandos del bot
    await bot.process_commands(message)

# Ejecutar el bot con el token (cambiar a tu token real)
bot.run("MTI2NDI2NjM0MzczMDExODY1Ng.Glvjlj.IkWyMvvq-zyWbm7RjdmOm2RLcV6PVPJ4W7toek")

