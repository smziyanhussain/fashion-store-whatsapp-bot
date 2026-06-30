# 🛍️ Fashion Store WhatsApp Bot

An AI-powered WhatsApp customer support bot for a fashion store, built with **n8n**, **OpenAI**, **Twilio**, and **Google Sheets**.

---

## 🤖 What It Does

- Automatically responds to customer WhatsApp messages
- Helps customers place new orders
- Checks order status in real-time
- Saves orders to Google Sheets
- Sends email confirmations to customers

---

## 🧱 Tech Stack

| Tool | Purpose |
|------|---------|
| [n8n](https://n8n.io) | Workflow automation |
| [Twilio](https://twilio.com) | WhatsApp messaging |
| [OpenAI GPT-4o-mini](https://openai.com) | AI brain |
| [Google Sheets](https://sheets.google.com) | Order database |
| [Gmail](https://gmail.com) | Email confirmations |

---

## 🗺️ Workflow Architecture

```
WhatsApp Message
      ↓
  Twilio Webhook
      ↓
 Extract Message
      ↓
   AI Agent  ───────────────────────────┐
      ↓                                 │
  ┌───┴────────────────┐           Tools Used:
  │                    │         - Google Sheets (Read)
Send WhatsApp     Respond to    - Google Sheets (Append)
   Reply            Webhook     - Gmail (Send Email)
```

---

## ⚙️ Setup Guide

### 1. Prerequisites
- [n8n Cloud](https://n8n.io) account or self-hosted n8n
- [Twilio](https://twilio.com) account (free trial available)
- [OpenAI](https://platform.openai.com) API key
- Google account (for Sheets + Gmail)

---

### 2. Twilio Setup

1. Create a Twilio account at [twilio.com](https://twilio.com)
2. Go to **Messaging → Try it out → Send a WhatsApp message**
3. Connect your WhatsApp by sending `join label-done` to `+1 415 523 8886`
4. Go to **Sandbox Settings** and set webhook URL:
   ```
   https://YOUR-N8N-URL/webhook/bot
   ```

---

### 3. Google Sheets Setup

Create a new Google Sheet named **"Store Bot"** with these columns:

| Order ID | Customer Name | Phone | Product | Size | Color | Status | Date |
|----------|--------------|-------|---------|------|-------|--------|------|

---

### 4. Import Workflow to n8n

1. Download the `workflow.json` file from this repo
2. Open n8n
3. Click **"Add workflow"** → **"Import from file"**
4. Select `workflow.json`

---

### 5. Configure Credentials in n8n

Add these credentials in n8n:

- **Twilio** → Account SID + Auth Token
- **OpenAI** → API Key
- **Google Sheets** → OAuth2 (Sign in with Google)
- **Gmail** → OAuth2 (Sign in with Google)

---

### 6. Activate Workflow

1. Click **"Publish"** in top right
2. Send a WhatsApp message to test!

---

## 💬 Example Conversations

**Placing an Order:**
```
User: Hi, I want to order a blue shirt size M
Bot:  Sure! Could you please provide your name and email 
      for order confirmation?
User: Ali Khan, ali@email.com
Bot:  Your order has been placed! Order confirmation 
      sent to ali@email.com ✅
```

**Checking Order Status:**
```
User: What is my order status?
Bot:  Your order for Blue Shirt (Size M) is currently 
      Pending. We will update you soon!
```

---

## 📁 Project Structure

```
fashion-store-whatsapp-bot/
│
├── workflow.json       # n8n workflow file
└── README.md          # Project documentation
```

---

## 🚀 Future Improvements

- [ ] Add product catalog with images
- [ ] Payment integration
- [ ] Multi-language support (Urdu/English)
- [ ] Order tracking notifications
- [ ] Admin dashboard

---

## 👨‍💻 Author

**Ziyan**  
Built with ❤️ using n8n and AI

---

## 📄 License

MIT License — feel free to use and modify!
