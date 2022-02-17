import discord

from discord.ext import commands


bot = commands.Bot(command_prefix='.')


@bot.event

async def on_ready():

    print("bot is ready")




    @bot.command()

    async def unban(ctx, *, member):

        banUsers = await ctx.guild.bans()

        memberString = member.split('#')[0]

        memberNumber = member.split('#')[1]


        for banned in banUsers:
            user = banned.user


            if user.name == memberString and user.discriminator == memberNumber:

                await ctx.guild.unban(user)

                await ctx.send(f"Unbanned '{member}'")
                return




bot.run("token")
