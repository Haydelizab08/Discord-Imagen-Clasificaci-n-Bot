# Discord-Imagen-Clasificaci-n-Bot
Este proyecto se encarga de identificar razas de perros y dar características sobre ellos.

Este bot puede identificar 5 razas de perros las cuales son:
Chihuahua
Pitbull
Rottweiler
Bulldog
Perro salchicha

A continuacion les estare compartiendo imagenes sobre el proyecto.![Screenshot 2025-07-03 215935](https://github.com/user-attachments/assets/4f102b33-849f-4fb8-9f25-f2e963ec46e0)
![Screenshot 2025-07-03 220007](https://github.com/user-attachments/assets/9e98bcd8-3477-4f7c-8189-671e7476df3a)
![Screenshot 2025-07-03 220039](https://github.com/user-attachments/assets/1b6f8f34-189b-46b3-91af-64f22c14b3f9)
![Screenshot 2025-07-03 220106](https://github.com/user-attachments/assets/35b99ef8-ba09-42b2-a87b-84ac0692c78d)
![Screenshot 2025-07-03 220134](https://github.com/user-attachments/assets/23eb9c8a-cfd9-4201-981c-d2c3c437bb87)

Espero les guste el bot y sea de utilidad.

import discord
from discord.ext import commands
from clasificador import reconocedor

intents = discord.Intents.default()
intents.message_content = True

bot = commands.Bot(command_prefix='.', intents=intents)

@bot.event
async def on_ready():
    print(f'We have logged in as {bot.user}')

@bot.command()
async def hello(ctx):
    await ctx.send(f'Hi! I am a bot {bot.user}!')

@bot.command()
async def heh(ctx, count_heh = 5):
    await ctx.send("he" * count_heh)
@bot.command()
async def prueba(ctx): 
    if ctx.message.attachments:
        for image in ctx.message.attachments:
            image_nombre= image.filename
            image_url = image.url
            await image.save(f"./images/{image_nombre}")
            await ctx.send(reconocedor(f"./images/{image_nombre}"))
    else:
        await ctx.send("No ha enviado ninguna imagen")

bot.run("TOKEN") 
