# ✉️ n8n — AI Cold Email Writer

AI দিয়ে স্বয়ংক্রিয়ভাবে Cold Email তৈরি ও পাঠানোর Workflow গাইড।  
OpenAI GPT দিয়ে Email Draft তৈরি হবে এবং Gmail দিয়ে সরাসরি পাঠানো হবে।

---

## 📋 ওভারভিউ

| বিষয় | বিবরণ |
|---|---|
| **টুল** | n8n Workflow Automation |
| **উদ্দেশ্য** | Form থেকে Input নিয়ে AI দিয়ে Cold Email Draft করে Gmail-এ পাঠানো |
| **AI Model** | OpenAI (GPT) |
| **ট্রিগার** | Webhook (HTTP POST) |
| **Output** | Gmail দিয়ে Email পাঠানো + Frontend-এ Response |

---

## 🔗 সম্পূর্ণ Workflow ফ্লো

```
Webhook (POST)
  (Frontend Form থেকে data আসবে)
       ↓
OpenAI — Message a Model
  (AI দিয়ে Cold Email Draft তৈরি)
       ↓
Code in JavaScript
  (AI Output প্রসেস / ফর্ম্যাট করা)
       ↓
Gmail — Send a Message
  (Email পাঠানো)
       ↓
Respond to Webhook
  (Frontend-এ সাফল্যের বার্তা পাঠানো)
```

---

## ⚙️ ধাপ ১ — OpenAI API Key তৈরি করা

> **উদ্দেশ্য:** OpenAI-এর GPT Model ব্যবহার করতে API Key দরকার।

**ধাপসমূহ:**

1. ব্রাউজারে যাও: [https://platform.openai.com](https://platform.openai.com)
2. Login করলে চলে যাবে: `https://platform.openai.com/home`
3. **Create API Keys** বাটনে ক্লিক করো।
4. একটি **নাম** দাও।
5. **Create secret key** বাটনে ক্লিক করো।
6. API Key **কপি** করো।
7. একটি ফাইলে আপাতত **paste করে রাখো** — পরে n8n-এ লাগবে।

```
⚠️ সতর্কতা: API Key একবারই দেখা যায়। উইন্ডো বন্ধ করলে আর দেখা যাবে না।
              তাই সাথে সাথে কোথাও সেভ করে রাখো।
```

---

## ⚙️ ধাপ ২ — Webhook সেটআপ

> **উদ্দেশ্য:** Frontend Form থেকে HTTP POST request গ্রহণ করা।

**ধাপসমূহ:**

1. **Add first step** বাটনে ক্লিক করো।
2. Search বক্সে টাইপ করো: `webhook` → **Webhook** ক্লিক করো।
3. নিচের মতো কনফিগার করো:

| ফিল্ড | মান |
|---|---|
| **HTTP Method** | `POST` |
| **Respond** | `Using 'Respond to Webhook' Node` *(শেষে আপডেট করতে হবে)* |

4. **Test URL** কপি করো।
5. `index.html` ফাইলের `try` block-এ URL টি **paste** করো।
6. **Listen for Test Event** বাটনে ক্লিক করো।
7. Browser-এ `index.html` খুলো → Form-এ value দাও → **EXECUTE DRAFT** বাটনে ক্লিক করো।

![Webhook Test](https://imgur.com/8OHFcUn.png)

---

## ⚙️ ধাপ ৩ — OpenAI "Message a Model" সেটআপ

> **উদ্দেশ্য:** Webhook থেকে পাওয়া Form Data দিয়ে AI-কে দিয়ে Cold Email Draft করানো।

**ধাপসমূহ:**

1. Webhook নোডের **`+`** চিহ্নে ক্লিক করো।
2. Search বক্সে টাইপ করো: `OpenAI` → **Message a Model** ক্লিক করো।
3. **Set up credential** বাটনে ক্লিক করো।
4. আগে কপি করা **API Key** paste করো।
5. **Save** বাটনে ক্লিক করো।
6. নিচের স্ক্রিনশট অনুযায়ী বাকি value সেট করো।
7. **Execute Step** বাটনে ক্লিক করো।

![OpenAI Message a Model](https://imgur.com/6Pcux93.png)

---

## ⚙️ ধাপ ৪ — Code in JavaScript

> **উদ্দেশ্য:** OpenAI-এর Output প্রসেস করা বা ফর্ম্যাট করা।

**ধাপসমূহ:**

1. Message a Model নোডের **`+`** চিহ্নে ক্লিক করো।
2. Search বক্সে টাইপ করো: `code` → **Code (JavaScript)** ক্লিক করো।
3. `codeNode.js` ফাইল থেকে সম্পূর্ণ code **কপি** করো।
4. Code নোডের ভেতরে **paste** করো।
5. **Execute Step** বাটনে ক্লিক করো।

![Code in JavaScript](https://imgur.com/x5BgheK.png)

```
📌 নোট: codeNode.js ফাইলটি প্রজেক্টের সাথে দেওয়া থাকবে।
         এই code AI-এর output থেকে Subject ও Body আলাদা করে বের করে।
```

---

## ⚙️ ধাপ ৫ — Gmail "Send a Message" সেটআপ

> **উদ্দেশ্য:** AI-এর তৈরি করা Email টি Gmail দিয়ে পাঠানো।

**ধাপসমূহ:**

1. Code নোডের **`+`** চিহ্নে ক্লিক করো।
2. Search বক্সে টাইপ করো: `gmail` → **Send a message** ক্লিক করো।
3. নিচের মতো ফিল্ডগুলো পূরণ করো:

| ফিল্ড | মান |
|---|---|
| **To** | পাশের প্যানেল থেকে recipient email field টেনে আনো |
| **Subject** | Code নোড থেকে subject field টেনে আনো |
| **Email Type** | `Text` |
| **Message** | Code নোড থেকে body field টেনে আনো |

---

## ⚙️ ধাপ ৬ — Respond to Webhook

> **উদ্দেশ্য:** Email পাঠানোর পরে Frontend-এ সফলতার বার্তা পাঠানো।

**ধাপসমূহ:**

1. Gmail নোডের **`+`** চিহ্নে ক্লিক করো।
2. Search বক্সে টাইপ করো: `Respond to Webhook` → ক্লিক করো।
3. নিচের স্ক্রিনশট অনুযায়ী value সেট করো:

![Respond to Webhook](https://imgur.com/Wcuy4cX.png)

---

## ⚙️ ধাপ ৭ — Webhook আপডেট ও Production URL সেট করা

> **উদ্দেশ্য:** Webhook-কে বলতে হবে Respond to Webhook নোড ব্যবহার করতে।  
> এবং Production URL দিয়ে `index.html` আপডেট করতে হবে।

**ধাপসমূহ:**

1. প্রথম **Webhook** নোডে ফিরে যাও।
2. **Respond** ফিল্ড পরিবর্তন করো:

| ফিল্ড | মান |
|---|---|
| **Respond** | `Using 'Respond to Webhook' Node` |

3. **Production URL** কপি করো।
4. `index.html` ফাইলের `try` block-এ **Test URL-এর জায়গায় Production URL paste** করো।

![Webhook Update & Production URL](https://imgur.com/a0lCKIC.png)

```
📌 নোট: Test URL শুধু n8n-এ "Listen for Test Event" চালু থাকলে কাজ করে।
         Production URL সবসময় কাজ করে — Live ব্যবহারের জন্য এটাই ব্যবহার করতে হবে।
```

---

## ✅ চেকলিস্ট

- [ ] OpenAI API Key তৈরি করা হয়েছে ও সেভ করা হয়েছে
- [ ] Webhook সেটআপ হয়েছে (HTTP Method: POST)
- [ ] Test URL `index.html`-এ paste করা হয়েছে
- [ ] Form থেকে Test Event পাঠানো হয়েছে
- [ ] OpenAI Credential সেট হয়েছে (API Key দিয়ে)
- [ ] "Message a Model" নোড কনফিগার ও Execute হয়েছে
- [ ] `codeNode.js` কোড paste হয়েছে ও Execute হয়েছে
- [ ] Gmail "Send a Message" নোড কনফিগার হয়েছে
- [ ] Respond to Webhook নোড যোগ হয়েছে
- [ ] Webhook → Respond আপডেট হয়েছে
- [ ] Production URL `index.html`-এ paste করা হয়েছে
- [ ] সম্পূর্ণ Workflow Live টেস্ট করা হয়েছে

---

## 🛠️ সম্ভাব্য সমস্যা ও সমাধান

| সমস্যা | সমাধান |
|---|---|
| OpenAI API Error | API Key সঠিক কিনা এবং OpenAI account-এ credit আছে কিনা চেক করো |
| Webhook response আসছে না | Webhook-এর Respond অপশন "Using Respond to Webhook Node" সেট হয়েছে কিনা দেখো |
| Gmail পাঠাচ্ছে না | Gmail Credential সঠিকভাবে connected কিনা এবং To/Subject/Message ফিল্ড ঠিকমতো সেট হয়েছে কিনা দেখো |
| Form submit হচ্ছে না | `index.html`-এর try block-এ সঠিক URL (Test বা Production) আছে কিনা দেখো |
| Code নোড Error দিচ্ছে | `codeNode.js` সম্পূর্ণ copy হয়েছে কিনা এবং OpenAI output format ঠিক আছে কিনা চেক করো |

---
