# EmailJS Setup Guide - Step by Step

## 🚀 Yes, EmailJS works in real-time and it's perfect for your portfolio!

### ✅ Benefits of EmailJS:
- **Real-time delivery** - Emails arrive instantly
- **1000 emails/month FREE** - More than enough for portfolio
- **No backend needed** - Works with static hosting
- **Professional** - Reliable email delivery
- **Easy setup** - Just 5 minutes

---

## 📧 Step-by-Step Setup:

### **Step 1: Create EmailJS Account**
1. Go to https://www.emailjs.com/
2. Click "Sign Up" 
3. Use your email: `vipulsinghoffice@gmail.com`
4. Verify your email

### **Step 2: Add Email Service**
1. In EmailJS dashboard, click "Email Services"
2. Click "Add New Service"
3. Choose "Gmail"
4. Click "Connect Account" 
5. Sign in with your Gmail (`vipulsinghoffice@gmail.com`)
6. Allow EmailJS permissions
7. **Copy the Service ID** (looks like: `service_abc123`)

### **Step 3: Create Email Template**
1. Click "Email Templates"
2. Click "Create New Template"
3. **Template Name:** `Portfolio Contact Form`
4. **Template Content:**
   ```
   Subject: New Portfolio Message - {{subject}}
   
   Hello Vipul,
   
   You have received a new message from your portfolio contact form:
   
   From: {{from_name}}
   Email: {{from_email}}
   Subject: {{subject}}
   
   Message:
   {{message}}
   
   ---
   Reply directly to this email to respond to {{from_name}}.
   
   Sent from your portfolio at vipulsingh.dev
   ```
5. **Variables to add:**
   - `{{from_name}}`
   - `{{from_email}}`
   - `{{subject}}`
   - `{{message}}`
6. **Copy the Template ID** (looks like: `template_xyz789`)

### **Step 4: Get Public Key**
1. Click on your profile (top right)
2. Go to "General" tab
3. **Copy the Public Key** (looks like: `user_abcdefghijk`)

### **Step 5: Update Your Code**
Replace these values in `script.js` (around line 127-129):

```javascript
const serviceID = 'service_abc123';        // Your actual Service ID
const templateID = 'template_xyz789';      // Your actual Template ID  
const publicKey = 'user_abcdefghijk';      // Your actual Public Key
```

---

## 🔧 Example Configuration:

If your EmailJS gives you:
- Service ID: `service_portfolio_2024`
- Template ID: `template_contact_vipul`
- Public Key: `user_vipul_portfolio_key`

Update script.js:
```javascript
const serviceID = 'service_portfolio_2024';
const templateID = 'template_contact_vipul';
const publicKey = 'user_vipul_portfolio_key';
```

---

## 🧪 Testing Your Setup:

1. **Save your files** after updating the credentials
2. **Open your portfolio** in browser
3. **Fill out the contact form** with test data
4. **Submit the form**
5. **Check your Gmail** (`vipulsinghoffice@gmail.com`)
6. **Email should arrive within seconds!**

---

## 🎯 What Happens After Setup:

1. **User fills form** → **JavaScript validates** → **EmailJS sends** → **You get email**
2. **Real-time delivery** - Usually arrives in 5-10 seconds
3. **Professional format** - Clean, formatted emails
4. **Reply capability** - You can reply directly to the sender

---

## 🔍 Troubleshooting:

**If you get errors:**
- ✅ **Double-check IDs** - Make sure Service ID, Template ID, and Public Key are correct
- ✅ **Check Gmail connection** - Ensure Gmail service is properly connected
- ✅ **Test template** - Send a test email from EmailJS dashboard
- ✅ **Browser console** - Check for any JavaScript errors

**Common Issues:**
- **"Public Key invalid"** → Copy the correct public key from Account settings
- **"Service not found"** → Use the exact Service ID from Email Services
- **"Template not found"** → Use the exact Template ID from Email Templates

---

## 💡 Pro Tips:

1. **Test first** - Send yourself a test email from EmailJS dashboard
2. **Check spam** - First emails might go to spam folder
3. **Customize template** - Make the email template match your branding
4. **Monitor usage** - Check your EmailJS dashboard for email statistics

---

## 🎉 Final Result:

Once set up, your contact form will:
- ✅ Send emails **instantly** to vipulsinghoffice@gmail.com
- ✅ Show **professional success/error messages**
- ✅ Work on **any hosting platform** (GitHub Pages, Netlify, etc.)
- ✅ Handle **1000 emails/month for FREE**

**Ready to set it up? Follow the steps above and your contact form will be live in 5 minutes!**