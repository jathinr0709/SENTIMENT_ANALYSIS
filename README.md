# 📰 India News & Sports Aggregator

A beginner-friendly, responsive web app built with **Flask**. It aggregates the latest news (via [NewsAPI.org](https://newsapi.org/)), scrapes India sports headlines (from[Cricbuzz](https://www.cricbuzz.com/)), and tracks your "read" articles history in a MySQL database.

## ✨ Features

- 🔄 **Automatic, real-time aggregation** of India news & sports updates  
- 📝 **"Read History" tracking:** Every time you click a headline, it's saved
- 👀 **Clean, accessible UI** with large fonts & simple navigation (suitable for adults & seniors)
- 💾 **MySQL backend** for persistent storage

## 📸 Screenshots
Homepage
<img width="1439" height="779" alt="Screenshot 2025-07-24 at 3 46 22 PM" src="https://github.com/user-attachments/assets/a309d796-dcde-48dc-aadc-7d720c7e7c6d" />
History
<img width="1433" height="742" alt="Screenshot 2025-07-24 at 3 46 38 PM" src="https://github.com/user-attachments/assets/116dd298-2c68-418e-bc78-5a18720fc208" />



### 1. **Clone the repository**

```bash
git clone https://github.com/YOUR-USERNAME/your-news-aggregator.git
cd your-news-aggregator
```

### 2. **Install dependencies**

```bash
python3 -m venv venv
source venv/bin/activate            # Windows: venv\Scripts\activate
pip install -r requirements.txt
```


Sample requirements.txt:

```
flask
requests
beautifulsoup4
mysql-connector-python
```


### 3. **Set up MySQL database**

Start MySQL and enter in the MySQL shell:
```sql
CREATE DATABASE news_db;
USE news_db;
CREATE TABLE read_history (
    id INT AUTO_INCREMENT PRIMARY KEY,
    title VARCHAR(512),
    url TEXT,
    read_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```
> For very long URLs, `TEXT` is recommended for `url`.

### 4. **Get a NewsAPI API Key**

- Register for a free key at [https://newsapi.org/](https://newsapi.org/)
- Replace `NEWS_API_KEY` in `app.py` accordingly

### 5. **Configure your database credentials**

Edit your `app.py`:
```python
db_config = {
    'user': 'root',
    'password': 'YOUR_MYSQL_PASSWORD',
    'host': 'localhost',
    'database': 'news_db'
}
```

### 6. **Run the application**

```bash
python app.py
```
Now open [http://127.0.0.1:5000/](http://127.0.0.1:5000/) in your browser.

## 🛠️ Tech Stack

- **Backend:** Flask (Python)
- **Frontend:** Jinja2 Templates, Responsive inlined CSS
- **Database:** MySQL (persistent read history)
- **APIs/Scraping:** [NewsAPI.org](https://newsapi.org/) for news, [Cricbuzz](https://www.cricbuzz.com/) (for India sports)
- **Python Libraries:** `requests`, `mysql-connector-python`, `beautifulsoup4`

## 👀 Usage

- **Click any news or sports headline:**  
  Opens the article and instantly logs it to your read history.

- **View your read articles:**  
  Click **"View Read History"** on the homepage to see all you've read (title, URL, date/time).

## 📂 Project Structure

```
.
├── app.py
├── requirements.txt
├── templates/
│   ├── index.html
│   └── history.html
└── static/    # optional, for external CSS/images
```

## 🎨 Customization

- **Change news source:** Modify `NEWS_URL` in `app.py` (`country=in`, or `everything?q=india`, etc.)
- **Change sports source:** Update the URL and selectors in the `get_sports` function.
- **Styling:** Edit embedded CSS in templates, or add your own at `static/style.css`.
- **Database:** Use MySQL Workbench or CLI to view/delete history as needed.

## ⚠️ Known Issues

- ESPN’s homepage layout may change; update scraping selectors or use Cricbuzz if headlines break.
- NewsAPI free keys may have limitations (daily requests, empty for some countries).
- For multi-user/production: Add authentication, use environment variables, deploy securely.

## 📄 License

This project is for educational and portfolio purposes.  
Do not use it for commercial purposes or in violation of any website’s terms.

## ✨ Credits

- [NewsAPI.org](https://newsapi.org/)
- [Cricbuzz](https://www.cricbuzz.com/)
- UI inspired by accessible news platforms.

## 🙌 Feel free to fork and improve!
For issues, open a GitHub Issue or contact me.
