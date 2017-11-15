import discord
from discord.ext import commands
import os
import sys

class Moderation:
    """Bot commands for moderation."""
    def __init__(self, bot):
        self.bot = bot
        print('Addon "{}" loaded'.format(self.__class__.__name__))  
    
    @commands.has_permissions(kick_members=True)    
    @commands.command(pass_context=True)
    async def kick(self, ctx, *, member):
        found_member = self.bot.server.get_member(member)
        if not found_member:
            found_member = self.bot.server.get_member_named(member)
        if not found_member:
            try:
                found_member = ctx.message.mentions[0]
            except IndexError:
                pass
        if not found_member:
            await self.bot.say("The user wasn't found. Fucking Retard.")
        else:
            await self.bot.kick(found_member)
            await self.bot.say("The faggot known as {0.name}#{0.discriminator} is now gone.".format(found_member))
    
    @commands.has_permissions(ban_members=True)    
    @commands.command(pass_context=True)
    async def ban(self, ctx, *, member):
        found_member = self.bot.server.get_member(member)
        if not found_member:
            found_member = self.bot.server.get_member_named(member)
        if not found_member:
            try:
                found_member = ctx.message.mentions[0]
            except IndexError:
                pass
        if not found_member:
            await self.bot.say("The user wasn't found. Fucking Retard.")
        else:
            await self.bot.ban(found_member)
            await self.bot.say("Successfully banned user {0.name}#{0.discriminator}!".format(found_member))
            
    @commands.has_permissions(ban_members=True)    
    @commands.command(pass_context=True)
    async def mute(self, ctx, *, member):
        found_member = self.bot.server.get_member(member)
        if not found_member:
            found_member = self.bot.server.get_member_named(member)
        if not found_member:
            try:
                found_member = ctx.message.mentions[0]
            except IndexError:
                pass
        if not found_member:
            await self.bot.say("The user wasn't found. Fucking Retard.")
        else:
            await self.bot.add_roles(found_member, self.bot.muted_role)
            await self.bot.say("Successfully muted user {0.name}#{0.discriminator}!".format(found_member))
            
    @commands.has_permissions(ban_members=True)    
    @commands.command(pass_context=True)
    async def unmute(self, ctx, *, member):
        found_member = self.bot.server.get_member(member)
        if not found_member:
            found_member = self.bot.server.get_member_named(member)
        if not found_member:
            try:
                found_member = ctx.message.mentions[0]
            except IndexError:
                pass
        if not found_member:
            await self.bot.say("The user wasn't found. Fucking Retard.")
        else:
            if "Muted" in [x.name for x in found_member.roles]:
                await self.bot.remove_roles(found_member, self.bot.muted_role)
                await self.bot.say("Successfully unmuted user {0.name}#{0.discriminator}!".format(found_member))
            else:
                await self.bot.say("That user isn't muted!")
        
def setup(bot):
    bot.add_cog(Moderation(bot))
