# 🍽️ Kventures Restro AI

<div align="center">

![n8n](https://img.shields.io/badge/n8n-EA4B71?style=for-the-badge&logo=n8n&logoColor=white)
![WhatsApp](https://img.shields.io/badge/WhatsApp-25D366?style=for-the-badge&logo=whatsapp&logoColor=white)
![Google Gemini](https://img.shields.io/badge/Google_Gemini-4285F4?style=for-the-badge&logo=google&logoColor=white)
![Google Sheets](https://img.shields.io/badge/Google_Sheets-34A853?style=for-the-badge&logo=googlesheets&logoColor=white)

**🤖 AI-Powered WhatsApp restaurant chatbot that handles orders, queries & inventory automatically**

*Built with n8n • Powered by Google Gemini • Runs 24/7 for Free*

[Features](#-key-features) • [Architecture](#-how-it-works) • [Usage](#-how-to-use) • [Screenshots](#-workflow-screenshots)

---

</div>

## 🌟 About Kventures Restro AI

An intelligent n8n workflow that transforms WhatsApp into a complete restaurant management system. Your customers chat naturally, and AI handles everything - from answering questions to processing orders and checking inventory in real-time.

**Perfect for:**
- 🏪 Small & medium restaurants
- 🍕 Cloud kitchens & delivery-only businesses  
- 🍔 Food trucks & pop-up restaurants
- ☕ Cafes & quick service restaurants

---

## ✨ Key Features

| What It Does | How It Helps |
|--------------|--------------|
| 🤖 **AI Conversations** | Natural language chat powered by Google Gemini - understands customer intent |
| 💬 **WhatsApp Integration** | Customers order directly via WhatsApp (no app needed!) |
| 🧠 **Smart Memory** | Remembers conversation context, customer preferences & order history |
| 📊 **Live Inventory** | Checks real-time stock from Google Sheets before confirming orders |
| ❓ **Auto FAQ** | Instant answers to hours, delivery, menu, payment questions |
| 📦 **Order Processing** | Validates orders, calculates totals, saves to database automatically |
| 🆓 **100% Free** | Runs on free hosting (Oracle Cloud, Railway) - no recurring costs |

---

## ⚙️ Tech Stack

- **Automation Platform**: n8n (visual workflow builder)
- **AI Engine**: Google Gemini (gemini-1.5-pro)
- **Messaging**: WhatsApp Business API
- **Database**: Google Sheets (upgradable to PostgreSQL)
- **Hosting**: Oracle Cloud / Railway / Render
- **Languages**: JSON workflow (no coding required!)

---

## 🏗️ How It Works

```
Customer (WhatsApp)
        ↓
   WhatsApp Trigger ← Receives message
        ↓
   ┌─────────────────────┐
   │    AI Agent Core    │
   │  (Google Gemini)    │
   │                     │
   │  Memory + 3 Tools:  │
   │  • Get Inventory    │
   │  • Get FAQ          │
   │  • Post Order       │
   └──────────┬──────────┘
              ↓
      Google Sheets DB
      • Inventory Sheet
      • FAQ Sheet  
      • Orders Sheet
              ↓
        Send Message ← AI responds
              ↓
    Customer (WhatsApp)
```

### **Workflow Components:**

1. **WhatsApp Trigger** - Listens for incoming customer messages via webhook
2. **AI Agent** - Google Gemini brain with memory + 3 tools
3. **Simple Memory** - Stores conversation context
4. **Get Inventory Tool** - Reads menu items, prices, availability (Google Sheets)
5. **Get FAQ Tool** - Fetches answers to common questions (Google Sheets)
6. **Post Order Tool** - Saves customer orders with timestamp (Google Sheets)
7. **Send Message** - Replies to customer on WhatsApp

---

## 📁 Repository Structure

```
kventures-restro-ai/
├── 📂 workflows/
│   └── 📄 kventures-restro-ai-workflow.json  (Main n8n workflow)
├── 📂 screenshots/
│   ├── 01-complete-workflow.png
│   ├── 02-whatsapp-chat-demo.png
│   └── 03-google-sheets-structure.png
├── 📂 templates/
│   ├── inventory-template.csv
│   ├── faq-template.csv
│   └── orders-template.csv
├── 📄 README.md
├── 📄 .env.example
└── 📄 .gitignore
```

---

## 🔧 How to Use This Workflow

### **Prerequisites:**
- ✅ n8n instance (cloud or self-hosted)
- ✅ WhatsApp Business API account
- ✅ Google Gemini API key ([Get Free](https://makersuite.google.com/app/apikey))
- ✅ Google account (for Sheets)

### **Quick Setup (3 Steps):**

#### **1️⃣ Import Workflow**
```
• Open n8n
• Click "Import from File"
• Upload workflows/kventures-restro-ai-workflow.json
• Click "Import"
```

#### **2️⃣ Configure Credentials**
```
WhatsApp:
→ Get permanent token from Meta Business Suite
→ Add to WhatsApp Trigger node

Google Gemini:
→ Get API key from Google AI Studio
→ Add to Google Gemini Chat Model node

Google Sheets:
→ Authenticate with OAuth or Service Account
→ Connect to 3 tool nodes
```

#### **3️⃣ Create Google Sheets Database**

**Sheet 1: Inventory** (Template provided in `/templates/`)
```
Item Name | Category | Price | Stock | Available
Pizza     | Food     | 299   | 50    | Yes
Burger    | Food     | 199   | 30    | Yes
```

**Sheet 2: FAQ**
```
Question             | Answer
What are your hours? | We're open 11 AM - 11 PM daily!
Do you deliver?      | Yes! Within 5km. Delivery: ₹50
```

**Sheet 3: Orders** (Auto-populated)
```
Order ID | Customer | Phone | Items | Total | Timestamp
```

#### **🎉 Activate & Test!**
```
1. Activate workflow in n8n
2. Send WhatsApp: "Hi"
3. AI responds!
4. Test order: "I want 2 pizzas"
```

---

## 💬 Real Usage Example

```
Customer: Hi

Bot: Hello! 👋 Welcome to Kventures Restro!
     I can help you with:
     • 📋 View menu & order food
     • ❓ Answer questions
     • 📍 Check delivery areas
     
     What would you like today?

Customer: Show me pizza options

Bot: Great choice! 🍕 Here's our pizza menu:
     
     1. Margherita Pizza - ₹299 ✅
        Classic cheese & tomato
     
     2. Pepperoni Pizza - ₹349 ✅
        Loaded with pepperoni
     
     Which one would you like?

Customer: 2 margherita and 1 coke

Bot: Perfect! Let me confirm your order:
     
     🍕 Margherita Pizza x2 = ₹598
     🥤 Coke x1 = ₹49
     ──────────────────────────
     Total: ₹647
     
     Shall I proceed? (Yes/No)

Customer: Yes, delivery to MG Road

Bot: ✅ Order Confirmed! 
     
     📝 Order ID: #KV1247
     📍 Delivery: MG Road
     💰 Total: ₹697 (incl. ₹50 delivery)
     ⏰ ETA: 35-40 minutes
     
     Payment: Cash on Delivery
     
     Thank you for ordering! 😊
```

---

## 🖥️ Free 24/7 Hosting Options

| Platform | Free Resources | Best For | Setup Time |
|----------|---------------|----------|------------|
| **Oracle Cloud** 🏆 | 24GB RAM, 4 CPU cores | Production use | 15 min |
| **Railway.app** | 500 hrs/month | Quick testing | 5 min |
| **Render.com** | 750 hrs/month | Side projects | 5 min |

### **🏆 Recommended: Oracle Cloud (Always Free)**
```bash
1. Sign up: signup.oraclecloud.com
2. Create ARM instance (FREE: 4 cores, 24GB RAM)
3. Install: npm install -g n8n && pm2 start n8n
4. Done! Access at http://your-ip:5678
```

---

## 🧠 What's Special About This Workflow?

✅ **No Coding Required** - Visual n8n workflow, just click & configure  
✅ **Production Ready** - Handles errors, validates input, logs everything  
✅ **Easily Customizable** - Change AI personality, add new tools, modify responses  
✅ **Scalable** - Starts with Google Sheets, upgrades to PostgreSQL when needed  
✅ **Cost Effective** - Free hosting + Free AI API tier = $0/month  
✅ **Well Documented** - Every node explained, templates provided  

---

## 🎯 Use Cases

- 🍽️ **Restaurant Order Automation** - Primary use case
- 🏨 **Hotel Room Service** - Handle in-room orders
- ☕ **Cafe Ordering** - Coffee & snacks orders
- 🛒 **Grocery Delivery** - Local grocery orders via WhatsApp
- 🎂 **Bakery Pre-Orders** - Cake & pastry bookings
- 🍕 **Cloud Kitchen** - Multi-brand virtual restaurants

---

## 📊 Workflow Screenshots

### **Main Workflow Overview**
![Complete Workflow](<img width="1254" height="565" alt="Screenshot 2025-12-05 094332" src="https://github.com/user-attachments/assets/cb73c4a5-802f-4298-921a-9e3d0200c285" />


### **WhatsApp Chat Demo**
![Chat Example](screenshots/02-whatsapp-chat-demo.png)

### **Google Sheets Structure**
![Sheets Setup](screenshots/03-google-sheets-structure.png)

---

## 🔄 Updates & Maintenance

This workflow is **actively maintained** with:
- 🆕 New features based on user feedback
- 🐛 Bug fixes & performance improvements
- 📚 Better documentation & video tutorials
- 🔧 Compatibility updates for n8n/API changes

**Last Updated**: December 2024  
**Current Version**: v1.0  
**Next Update**: Payment integration, Multi-language support

---

## ⚠️ Important Notes

**Security:**
- ⚠️ Never commit API keys to GitHub
- ⚠️ Use `.env` for sensitive data
- ⚠️ Enable WhatsApp webhook signature verification
- ⚠️ Rotate tokens every 60 days (best practice)

**Data Privacy:**
- 📋 Minimal customer data stored
- 🗑️ Implement data retention policy
- 🔒 HTTPS only for production
- 🛡️ Comply with local data protection laws

**Limitations:**
- 📊 Google Sheets max: ~5000 rows (migrate to DB for scale)
- 🤖 Gemini free tier: 60 requests/minute
- 💬 WhatsApp: Rate limits apply per Meta policies

---

## 🤝 Contributing

Contributions are welcome! Here's how:

1. **Fork** this repository
2. **Create** a new branch: `git checkout -b feature-name`
3. **Make** your changes
4. **Test** thoroughly in n8n
5. **Submit** a pull request

**Ideas for contributions:**
- 🔌 New integrations (payment, delivery tracking)
- 🌐 Multi-language support
- 📱 Voice message handling
- 📊 Analytics dashboard
- 🎨 UI improvements

---

## 📬 Support & Contact

**Need help?**
- 🐛 [Open an Issue](https://github.com/YOUR_USERNAME/kventures-restro-ai/issues) for bugs
- 💡 [Start a Discussion](https://github.com/YOUR_USERNAME/kventures-restro-ai/discussions) for ideas
- 📧 Email: your-email@example.com
- 💼 LinkedIn: [Your Profile](https://linkedin.com/in/yourprofile)

**Business Inquiries:**
Want to deploy this for your restaurant? Custom features needed?  
Contact for commercial support & customization services.

---

## 📄 License

This project is licensed under the **MIT License** - feel free to use, modify, and distribute.

See [LICENSE](LICENSE) file for full details.

---

## ⭐ Show Your Support

If this workflow helped you, please:
- ⭐ **Star this repository**
- 🍴 **Fork and customize** for your needs
- 📢 **Share** with other restaurant owners
- 💬 **Provide feedback** via issues

---

<div align="center">

**Built with ❤️ for the restaurant community**

*Empowering businesses with AI automation • One workflow at a time*

**Kventures Restro AI** | Powered by n8n 🚀

</div>
