# Lead Form Setup Guide

The lead form on `index-v2.html` is now live with email and Telegram integration. Here's what you need to set up:

## Email Integration (Automatic)

The form uses **FormSubmit.co** which is completely free and requires no backend setup.

**First time only:**
1. When someone submits the form, they'll receive a confirmation email at nami@sakuralabs.io
2. Click the verification link in that email
3. After that, all submissions will go through automatically

**That's it.** The email sending is already configured and will work.

---

## Telegram Integration (Required Setup)

To receive lead notifications on Telegram, you need to:

### Step 1: Create a Telegram Bot
1. Open Telegram and search for **@BotFather**
2. Send `/start`
3. Send `/newbot`
4. Follow the prompts:
   - Choose a name (e.g., "Sakura Labs Bot")
   - Choose a username (e.g., "sakura_labs_bot")
5. **Copy the bot token** (looks like: `123456:ABC-DEF1234ghIkl-zyx57W2v1u123ew11`)

### Step 2: Get Your Chat ID
1. Open Telegram and search for **@userinfobot**
2. Send `/start`
3. The bot will show your User ID (e.g., `123456789`)
4. **Copy this number**

### Step 3: Update the Form
1. Open `/Users/nami/.openclaw/workspace/sakura-labs/index-v2.html`
2. Find this line (around line 400):
```javascript
const telegramBotToken = 'YOUR_TELEGRAM_BOT_TOKEN';
const telegramChatId = 'YOUR_TELEGRAM_CHAT_ID';
```

3. Replace:
   - `YOUR_TELEGRAM_BOT_TOKEN` → Your bot token from Step 1
   - `YOUR_TELEGRAM_CHAT_ID` → Your User ID from Step 2

Example:
```javascript
const telegramBotToken = '123456:ABC-DEF1234ghIkl-zyx57W2v1u123ew11';
const telegramChatId = '123456789';
```

### Step 4: Test
1. Go to the website
2. Fill out the lead form and submit
3. You should receive a Telegram message within a few seconds

---

## Form Fields

**Collected:**
- Name (required)
- Company (required)
- Team Size (required) - 1-5, 6-10, 11-20, 20+
- Email (required)
- Pain Points (required, multiple choice):
  - Scheduling chaos & manual coordination
  - Too much admin time (5-15 hours/week wasted)
  - No-shows & revenue loss
  - Invoicing, billing & payment issues
  - Data scattered across 5+ systems
  - Can't see what's actually happening in the business
  - Too much money spent on fragmented software

**Delivery:**
- Email goes to: `nami@sakuralabs.io`
- Telegram notification sent to your Telegram account
- User sees: "We'll Be In Touch Soon" message on the form

---

## Form Submission Flow

```
User fills form
    ↓
Submit button clicked
    ↓
Data sent to nami@sakuralabs.io (via FormSubmit.co)
    ↓
Telegram notification sent to Ben
    ↓
Success message displayed: "We'll Be In Touch Soon"
```

---

## Troubleshooting

**Email not arriving?**
- Check spam folder
- Verify the nami@sakuralabs.io address in FormSubmit.co (first submission may need verification link)

**Telegram not working?**
- Make sure bot token is correct (no spaces)
- Make sure chat ID is correct (just the number)
- Check that the bot is started (send /start to the bot in Telegram)
- The form will still submit to email even if Telegram fails

**Form not submitting?**
- Check browser console (F12 → Console tab) for errors
- Make sure all required fields are filled
- Make sure at least one pain point is selected
