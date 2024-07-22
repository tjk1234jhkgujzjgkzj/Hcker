Let's update the bot code to include the user's specific channel and group.

updated_bot_code = """
from telegram import Update
from telegram.ext import Updater, CommandHandler, CallbackContext

# List of channels and groups
CHANNELS = ["@hacker_TJKE", "-1002022717222"]  # Added both channel and group

def start(update: Update, context: CallbackContext) -> None:
    user_id = update.message.from_user.id
    for channel in CHANNELS:
        member = context.bot.get_chat_member(chat_id=channel, user_id=user_id)
        if member.status not in ["member", "administrator", "creator"]:
            update.message.reply_text(f"Шумо бояд аввал ба {channel} обуна шавед.")
            return
    update.message.reply_text("Хуш омадед! Шумо ба ҳамаи каналҳо ва гурӯҳҳо обуна шудаед.")

def main() -> None:
    # Replace with the user's bot token
    updater = Updater("7067582224:AAGVjEEeoWOpppn4NBvaB7i8Yda3ACc8FkY", use_context=True)
    dispatcher = updater.dispatcher

    dispatcher.add_handler(CommandHandler("start", start))

    updater.start_polling()
    updater.idle()

if __name__ == '__main__':
    main()
"""

# Save the updated code to a file
updated_file_path = "/mnt/data/bot_updated.py"
with open(updated_file_path, "w") as file:
    file.write(updated_bot_code)

updated_file_path
