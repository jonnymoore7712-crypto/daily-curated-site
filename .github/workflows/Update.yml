import json
import urllib.request
from datetime import datetime

def fetch_content():
    # Example: Fetching public data (using a public API endpoint)
    # You can swap this URL later for any niche data source you prefer.
    url = "https://official-joke-api.appspot.com/random_ten"
    
    try:
        req = urllib.request.Request(url, headers={'User-Agent': 'Mozilla/5.0'})
        with urllib.request.urlopen(req) as response:
            data = json.loads(response.read().decode())
            return data
    except Exception as e:
        print(f"Error fetching data: {e}")
        return []

def generate_html(items):
    current_date = datetime.now().strftime("%B %d, %Y")
    
    # Build the HTML content structure
    html_content = f"""<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Daily Curated Insights</title>
    <style>
        body {{ font-family: Arial, sans-serif; max-width: 800px; margin: 40px auto; padding: 0 20px; line-height: 1.6; color: #333; background: #f9f9f9; }}
        header {{ text-align: center; margin-bottom: 40px; }}
        .card {{ background: #fff; padding: 20px; margin-bottom: 20px; border-radius: 8px; box-shadow: 0 2px 4px rgba(0,0,0,0.05); }}
        .setup {{ font-weight: bold; color: #0066cc; }}
        .punchline {{ margin-top: 10px; color: #555; }}
        footer {{ text-align: center; margin-top: 40px; font-size: 0.9em; color: #777; }}
    </style>
</head>
<body>
    <header>
        <h1>Daily Curated Feed</h1>
        <p>Last updated automatically on: <strong>{current_date}</strong></p>
    </header>
    
    <main>
"""

    if items:
        for item in items:
            setup = item.get('setup', 'Insight item')
            punchline = item.get('punchline', '')
            html_content += f"""
        <div class="card">
            <div class="setup">{setup}</div>
            <div class="punchline">{punchline}</div>
        </div>
"""
    else:
        html_content += """
        <div class="card">
            <p>Content updating soon. Check back tomorrow!</p>
        </div>
"""

    html_content += """
    </main>

    <!-- Ad Space Placeholder: Paste your approved AdSense or ad network tag here -->
    <div style="text-align: center; margin: 40px 0; padding: 20px; background: #eee; border-radius: 8px;">
        <p style="color: #666; font-size: 0.85em;">Advertisement</p>
        <!-- Insert Ad Tag Here -->
    </div>

    <footer>
        <p>&copy; 2026 Autonomous Web Project. All rights reserved.</p>
    </footer>
</body>
</html>
"""

    # Save to index.html
    with open("index.html", "w", encoding="utf-8") as f:
        f.write(html_content)
    print("index.html successfully updated!")

if __name__ == "__main__":
    content = fetch_content()
    generate_html(content)
