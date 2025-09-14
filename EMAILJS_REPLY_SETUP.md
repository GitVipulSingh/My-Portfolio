# EmailJS Reply-To Setup Guide

## 🎯 **Goal:** When you reply to received emails, they go directly to the customer's email

---

## 📧 **EmailJS Template Configuration:**

### **Step 1: Template Settings**
1. Go to EmailJS Dashboard → Email Templates
2. Create New Template or Edit existing one
3. **Template Name:** `Portfolio Contact Form`

### **Step 2: Email Configuration Fields**

#### **📌 To Email:**
```
{{to_email}}
```
*This will be your email: vipulsinghoffice@gmail.com*

#### **📌 From Name:**
```
{{from_name}} via Portfolio
```
*Shows who sent the message*

#### **📌 Reply To:**
```
{{reply_to}}
```
*This is the KEY - customer's email for direct replies*

#### **📌 Subject:**
```
New Portfolio Message - {{subject}}
```

#### **📌 Email Content:**
```
Hello {{to_name}},

You have received a new message from your portfolio contact form:

From: {{from_name}}
Email: {{from_email}}
Subject: {{subject}}

Message:
{{message}}

---
REPLY DIRECTLY to this email to respond to {{from_name}}.
Your reply will go to: {{from_email}}

Sent from your portfolio contact form.
```

---

## 🔧 **Advanced EmailJS Template Setup:**

### **In EmailJS Template Editor:**

```
┌─────────────────────────────────────────┐
│ Template Settings:                      │
├─────────────────────────────────────────┤
│ To Email: {{to_email}}                  │
│ From Name: {{from_name}} via Portfolio  │
│ Reply To: {{reply_to}}                  │ ← IMPORTANT!
│ Subject: New Portfolio Message - {{subject}} │
├─────────────────────────────────────────┤
│ Content:                                │
│                                         │
│ Hello {{to_name}},                      │
│                                         │
│ You have received a new message from    │
│ your portfolio contact form:            │
│                                         │
│ From: {{from_name}}                     │
│ Email: {{from_email}}                   │
│ Subject: {{subject}}                    │
│                                         │
│ Message:                                │
│ {{message}}                             │
│                                         │
│ ---                                     │
│ REPLY DIRECTLY to this email to respond │
│ to {{from_name}}.                       │
│ Your reply will go to: {{from_email}}   │
│                                         │
│ Sent from your portfolio contact form.  │
└─────────────────────────────────────────┘
```

---

## 🎯 **How It Works:**

### **When Customer Submits Form:**
1. **Customer fills form:** Name: "John Smith", Email: "john@company.com"
2. **EmailJS sends email to you** with:
   - **To:** vipulsinghoffice@gmail.com
   - **From:** john@company.com via Portfolio
   - **Reply-To:** john@company.com
   - **Subject:** New Portfolio Message - Project Inquiry

### **When You Reply:**
1. **You click "Reply" in Gmail**
2. **Gmail automatically uses Reply-To field**
3. **Your reply goes directly to:** john@company.com
4. **Customer receives your response**

---

## 📱 **What You'll See in Gmail:**

```
From: John Smith via Portfolio <vipulsinghoffice@gmail.com>
Reply-To: john@company.com
To: vipulsinghoffice@gmail.com
Subject: New Portfolio Message - Project Inquiry

Hello Vipul Singh,

You have received a new message from your portfolio contact form:

From: John Smith
Email: john@company.com
Subject: Project Inquiry

Message:
Hi, I'm interested in hiring you for a web development project...

---
REPLY DIRECTLY to this email to respond to John Smith.
Your reply will go to: john@company.com

Sent from your portfolio contact form.
```

**When you hit "Reply":**
- Gmail will automatically address it to: john@company.com
- Your response goes directly to the customer
- No need to copy/paste email addresses!

---

## ✅ **Testing the Setup:**

### **Step 1: Test Template**
1. In EmailJS dashboard, click "Test" on your template
2. Fill in test data:
   - `from_name`: "Test User"
   - `from_email`: "test@example.com"
   - `reply_to`: "test@example.com"
   - `to_email`: "vipulsinghoffice@gmail.com"
   - `to_name`: "Vipul Singh"

### **Step 2: Check Email**
1. Check your Gmail for the test email
2. Click "Reply"
3. Verify it's addressed to "test@example.com"

### **Step 3: Live Test**
1. Submit your own contact form
2. Use a different email address
3. Check that reply goes to that address

---

## 🔍 **Troubleshooting:**

**If replies don't go to customer:**
- ✅ Check "Reply-To" field is set to `{{reply_to}}`
- ✅ Verify JavaScript sends `reply_to: email`
- ✅ Test with EmailJS dashboard first

**If emails look wrong:**
- ✅ Check all template variables are correct
- ✅ Ensure no typos in variable names
- ✅ Test template with sample data

---

## 🎉 **Final Result:**

✅ **Customer submits form** → **You get email** → **You hit Reply** → **Customer gets your response**

**No copying email addresses, no manual setup - just natural email conversation!**