# 📰 n8n Daily News Bot

Flujo de **n8n** que cada mañana lee las noticias de tecnología, las resume con **IA (OpenAI)** y te las envía por **Telegram**.

▶️ **Video paso a paso:** [n8n desde cero: crea un bot de noticias con IA y Telegram](https://youtu.be/VuJmM_N0J8k)

---

## 🧩 Cómo funciona

```
Schedule Trigger → RSS Read → Limit → Aggregate → OpenAI → Telegram
   (7:00 a. m.)    (Hacker News)  (5)   (todo junto)  (resumen)  (mensaje)
```

| Nodo | Qué hace |
| --- | --- |
| Schedule Trigger | Ejecuta el flujo todos los días a las 7:00. |
| RSS Read | Lee el feed `https://hnrss.org/frontpage`. |
| Limit | Se queda con las 5 primeras noticias. |
| Aggregate | Junta las 5 en un solo elemento para la IA. |
| OpenAI (Message a Model) | Resume las noticias en español, una por línea, con emoji y enlace. |
| Telegram | Envía el resumen a tu chat. |

## ✅ Requisitos

- n8n (Docker o n8n Cloud).
- Una API key de OpenAI: [platform.openai.com](https://platform.openai.com).
- Un bot de Telegram creado con **@BotFather** y tu **chat ID** (puedes obtenerlo con **@userinfobot**).

## 🚀 Uso

1. Descarga `daily-news-bot.workflow.json`.
2. En n8n: **Create workflow → ⋯ → Import from File**.
3. En el nodo **OpenAI**, crea la credencial con tu API key.
4. En el nodo **Telegram**, crea la credencial con el token de tu bot y reemplaza `TU_CHAT_ID` por tu chat ID.
5. En **⋯ → Settings → Timezone**, elige tu zona horaria (viene en UTC).
6. Prueba con **Execute workflow** y luego pulsa **Publish** para que se ejecute solo.

> 🔐 Las credenciales se guardan en el gestor de credenciales de n8n. Nunca las pegues dentro de los nodos ni las subas al repositorio.

## 📄 Licencia

[MIT](LICENSE) · Hecho con 💙 por [AguiCode](https://www.youtube.com/channel/UCOwIey0vGlYkZBgF29ASn3A)
