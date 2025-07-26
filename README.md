# 📰 AI News Auto-Poster with Gemini API (PHP + MySQL)

## 👋 Hello and Welcome!

Hi there! 👋  
Thanks for visiting this project. I created this script to help automate the generation and publishing of fresh news articles into a database — powered by Google Gemini (Generative Language API). If you're building a news blog, want to explore AI-written journalism, or just looking for an efficient content automation tool, this is for you.

The script fetches AI-generated articles tailored for the Kenyan context across categories like Politics, Technology, Medicine, Business, Education, and Entertainment. It checks for duplicates, generates SEO-friendly slugs, and logs every run — ready for cron scheduling. Let’s get you started!

---

## 🚀 How It Works

1. PHP connects to Gemini via the official Generative Language API.
2. Prompts are sent for each category, asking Gemini to create 3 articles.
3. Articles are parsed (title + content) and checked for duplicates.
4. Only new articles are inserted into your MySQL `gonews` table.
5. Logs are saved to `cron_news.log` for every run.

---

## ⚙️ Configuration

1. Replace the placeholders in the script:
   - `DB_USERNAME`, `DB_PASSWORD`, `DB_NAME` – your MySQL credentials
   - `YOUR_GEMINI_API_KEY` – your API key from [Google AI Studio](https://makersuite.google.com/app)

2. Make sure your table is created as below:

```sql
CREATE TABLE `gonews` (
  `id` INT(11) NOT NULL AUTO_INCREMENT PRIMARY KEY,
  `category` VARCHAR(32) NOT NULL,
  `title` VARCHAR(255) NOT NULL,
  `slug` VARCHAR(255) NOT NULL,
  `content` TEXT NOT NULL,
  `author_id` INT(11) DEFAULT NULL,
  `featured_image` VARCHAR(255) DEFAULT NULL,
  `is_top` TINYINT(1) DEFAULT 0,
  `status` ENUM('draft','published','archived') DEFAULT 'draft',
  `created_at` DATETIME DEFAULT CURRENT_TIMESTAMP,
  `updated_at` DATETIME DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP
) ENGINE=InnoDB DEFAULT CHARSET=latin1;


Thank you so much for checking this out! I hope it brings value to your work, boosts your content pipeline, and inspires more AI integration into your projects. 
