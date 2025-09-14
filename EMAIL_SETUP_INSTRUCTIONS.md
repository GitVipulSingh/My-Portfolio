# Email Setup Instructions for Portfolio Contact Form

## Option 1: EmailJS (Recommended for Static Sites) - FREE

EmailJS allows you to send emails directly from your frontend without a backend server.

### Setup Steps:

1. **Create EmailJS Account**
   - Go to https://www.emailjs.com/
   - Sign up for a free account (1000 emails/month free)

2. **Create Email Service**
   - Go to Email Services
   - Click "Add New Service"
   - Choose Gmail (recommended)
   - Connect your Gmail account (vipulsinghoffice@gmail.com)
   - Note down the Service ID

3. **Create Email Template**
   - Go to Email Templates
   - Click "Create New Template"
   - Use this template:
   ```
   Subject: New Contact Form Message - {{subject}}
   
   From: {{from_name}} ({{from_email}})
   Subject: {{subject}}
   
   Message:
   {{message}}
   
   ---
   This message was sent from your portfolio contact form.
   ```
   - Note down the Template ID

4. **Get Public Key**
   - Go to Account > General
   - Copy your Public Key

5. **Update JavaScript**
   - Open script.js
   - Replace these values:
     - `service_vipul_portfolio` with your Service ID
     - `template_contact_form` with your Template ID  
     - `YOUR_PUBLIC_KEY` with your Public Key

### Benefits:
- ✅ Completely free (1000 emails/month)
- ✅ No backend server needed
- ✅ Works with static hosting (GitHub Pages, Netlify, etc.)
- ✅ Reliable delivery
- ✅ Easy setup

---

## Option 2: Node.js Backend with Nodemailer

If you prefer a backend solution, here's a complete Node.js setup:

### Files to Create:

#### package.json
```json
{
  "name": "portfolio-backend",
  "version": "1.0.0",
  "description": "Backend for portfolio contact form",
  "main": "server.js",
  "scripts": {
    "start": "node server.js",
    "dev": "nodemon server.js"
  },
  "dependencies": {
    "express": "^4.18.2",
    "nodemailer": "^6.9.7",
    "cors": "^2.8.5",
    "dotenv": "^16.3.1",
    "express-rate-limit": "^7.1.5"
  }
}
```

#### server.js
```javascript
const express = require('express');
const nodemailer = require('nodemailer');
const cors = require('cors');
const rateLimit = require('express-rate-limit');
require('dotenv').config();

const app = express();
const PORT = process.env.PORT || 3000;

// Middleware
app.use(cors());
app.use(express.json());

// Rate limiting
const limiter = rateLimit({
  windowMs: 15 * 60 * 1000, // 15 minutes
  max: 5, // limit each IP to 5 requests per windowMs
  message: 'Too many requests from this IP, please try again later.'
});

app.use('/api/send-email', limiter);

// Email configuration
const transporter = nodemailer.createTransporter({
  service: 'gmail',
  auth: {
    user: process.env.EMAIL_USER, // vipulsinghoffice@gmail.com
    pass: process.env.EMAIL_PASS  // Your Gmail app password
  }
});

// Send email endpoint
app.post('/api/send-email', async (req, res) => {
  try {
    const { name, email, subject, message } = req.body;

    // Validation
    if (!name || !email || !subject || !message) {
      return res.status(400).json({ message: 'All fields are required' });
    }

    // Email options
    const mailOptions = {
      from: process.env.EMAIL_USER,
      to: 'vipulsinghoffice@gmail.com',
      subject: `Portfolio Contact: ${subject}`,
      html: `
        <h3>New Contact Form Message</h3>
        <p><strong>Name:</strong> ${name}</p>
        <p><strong>Email:</strong> ${email}</p>
        <p><strong>Subject:</strong> ${subject}</p>
        <p><strong>Message:</strong></p>
        <p>${message.replace(/\n/g, '<br>')}</p>
      `
    };

    // Send email
    await transporter.sendMail(mailOptions);
    
    res.status(200).json({ message: 'Email sent successfully' });
  } catch (error) {
    console.error('Error sending email:', error);
    res.status(500).json({ message: 'Failed to send email' });
  }
});

app.listen(PORT, () => {
  console.log(`Server running on port ${PORT}`);
});
```

#### .env
```
EMAIL_USER=vipulsinghoffice@gmail.com
EMAIL_PASS=your_gmail_app_password
PORT=3000
```

### Setup Steps:

1. **Install Dependencies**
   ```bash
   npm install
   ```

2. **Setup Gmail App Password**
   - Go to Google Account settings
   - Enable 2-factor authentication
   - Generate an App Password for "Mail"
   - Use this password in .env file

3. **Run Server**
   ```bash
   npm start
   ```

4. **Update Frontend**
   - Change the fetch URL in script.js to your server URL
   - For local development: `http://localhost:3000/api/send-email`
   - For production: `https://your-domain.com/api/send-email`

---

## Recommendation

**Use EmailJS (Option 1)** because:
- No server maintenance required
- Free tier is generous (1000 emails/month)
- Works with any static hosting
- Easier to deploy and maintain
- Perfect for portfolio contact forms

The Node.js option is better if you need more control or plan to add other backend features later.