# Minecraft: Discord Messenger

Hello, Minecraft community,

I present to your attention a script written in Skript for sending messages to Discord via a webhook URL.

You can generate messages in JSON format and send them to the webhook of the URL Discord channel. 

___

## Script functions
1. **Function to format message in JSON format**
> **Function:** prepareDiscordMessage
> 
> **Parameters:**
> - avatarUrl: Avatar for Discord bot
> - botUsername: Username for Discord bot
> - embedTitle: Embed title
> - embedDescription: Embed description
> - embedFooter: Footer text
> - embedColor: Embed color
> 
> **Usage example:**
>
> An example of the result of formatting a message for further sending as a message to the Discord channel.
> 
> ```
> set {_discordMessage} to prepareDiscordMessage(BotAvatar(), BotUsername(), "%event-player% has joined the server", "The player **%event-player%** has joined the server.", FooterText(), GreenColor())
> ```
>
> **Result:**
>
> ```
> '{ ""embeds"": [{ ""title"": ""CHYZHOV has joined the server"", ""description"": ""The player **CHYZHOV** has joined the server."", ""color"": 3066993, ""footer"": { ""text"": ""Date of action execution: 02.11.2024, 02:49"" } }], ""username"": ""System alert"", ""avatar_url"": ""https://cdn.discordapp.com/attachments/1014147200701435965/1294052865836318791/star-fall-svgrepo-com.png?ex=6714d0e5&is=67137f65&hm=aecc0259e4c8eda035b42ac9b414ea87c6d1d7e82a23fa21a3519273ef64ded3&"" }'
> ```

2. **Function for sending messages to the Discord channel**
> **Function:** sendDiscordMessage
> 
> **Parameters:**
>   - message: Message in JSON format
>   - channel: Channel webhook URL
> 
> **Usage example:**
>
> When a player joins a server, a message will be sent to the Discord channel about it.
> 
> ```
> on join:
>   set {_discordMessage} to prepareDiscordMessage(BotAvatar(), BotUsername(), "%event-player% has joined the server", "The player **%event-player%** has joined the server.", FooterText(), GreenColor())
>   sendDiscordMessage({_discordMessage}, Channel())
> ```
>
> **Result:**
> 
> ![зображення](https://github.com/user-attachments/assets/09cc89fe-87d4-4547-b309-cd5a54e3b0d1)

___

## Configuration:
To use the script, you need to configure it.

1. **Bot avatar**
> Specify a link to the bot's avatar, which will be displayed in the discord message.
>
> ```
> function BotAvatar() :: string:
>   return "https://cdn.discordapp.com/attachments/1014147200701435965/1294052865836318791/star-fall-svgrepo-com.png?ex=6714d0e5&is=67137f65&hm=aecc0259e4c8eda035b42ac9b414ea87c6d1d7e82a23fa21a3519273ef64ded3&"
> ```

2. **Bot username**
> The name of the bot will be displayed in the discord message.
> 
> ```
> function BotUsername() :: string:
>   return "System alert"
> ```

3. **Footer text**
> The text will be displayed in the footer of the Discord message.
> 
> ```
> function FooterText() :: string:
>   return "Date of action execution: %now%"
> ```

4. **Red color**
> The color code variant for the embed in the Discord message.
> 
> ```
> function RedColor() :: integer:
>   return 13458524
> ```

5. **Yellow color**
> The color code variant for the embed in the Discord message.
> 
> ```
> function YellowColor() :: integer:
>   return 15844367
> ```

6. **Green color**
> The color code variant for the embed in the Discord message.
> 
> ```
> function GreenColor() :: integer:
>   return 3066993
> ```

7. **Channel**
> Link to the webhook of the URL channel to which the message will be sent.
> 
> ```
> function Channel() :: string:
>   return "https://discord.com/api/webhooks/your_webhook"
> ```

___

## Requirements:
* Skript 2.9.0+
* skript-reflect 2.5.1+
