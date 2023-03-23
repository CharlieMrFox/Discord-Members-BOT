import discord
from cachetools import TTLCache
import asyncio

# Define all intents
intents = discord.Intents.default()
intents.members = True

# Initialize the client object with all intents parameter
client = discord.Client(intents=intents)


member_cache = TTLCache(maxsize=1, ttl=300)  #This is a cache for 5 minutes to work with Discord's cache behaviour

TOKEN = "your_bot_token_here"

@client.event
async def on_ready():
    guild = client.get_guild(00000000000000000000) # This is servers's ID (Rigth click on the server picture > Copy ID).
    if guild is None:
        print("Unable to find guild.")
        return

    if 'members' not in member_cache:
        members = []
        async for member in guild.fetch_members(limit=None):
            members.append(member)
        member_cache['members'] = members


    for member in member_cache['members']:
        print(member.name)

client.run('TOKEN')
