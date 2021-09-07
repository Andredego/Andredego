- 👋 Hi, I’m @Andredego
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...

<!---
Andredego/Andredego is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
const botgram = require("botgram")
const bot = botgram("<auth token>")

bot.command("start", "help", (msg, reply) =>
  reply.text("To schedule an alert, do: /alert <seconds> <text>"))

bot.command("alert", (msg, reply, next) => {
  var [ seconds, text ] = msg.args(2)
  if (!seconds.match(/^\d+$/) || !text) return next()

  setTimeout(() => reply.text(text), Number(seconds) * 1000)
})

bot.command((msg, reply) =>
  reply.text("Invalid command."))
