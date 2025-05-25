# Flask Web App

## Important: Update Script and Style Tags for Flask

When converting an HTML template to work with Flask, **you must update all `<script>`, `<link>`, and `<img>` tags** that reference static files (JavaScript, CSS, images, etc.) to use Flask’s `url_for` function. This allows Flask to correctly serve your static assets from the `/static` directory.

### How to Update

**Before (plain HTML):**
```html
<link rel="stylesheet" href="assets/css/style.css">
<script src="assets/js/main.js"></script>
<img src="assets/images/logo.png" alt="Logo">
```

**After (Flask/Jinja2):**
```html
<link rel="stylesheet" href="{{ url_for('static', filename='css/style.css') }}">
<script src="{{ url_for('static', filename='js/main.js') }}"></script>
<img src="{{ url_for('static', filename='images/logo.png') }}" alt="Logo">
```

- Make sure all your static files (CSS, JS, images) are located in the `static` folder at the root of your Flask project.
- Use this pattern for **every** static file reference in your HTML templates.

---

## Adding More Routes (Pages) in Flask

To display more pages (like `about.html`, `contact.html`, etc.), you need to:

1. **Create the HTML files** in the `templates` directory (e.g., `about.html`).
2. **Add a route** in your `app.py` for each page.

**Example:**

```python
from flask import Flask, render_template

app = Flask(__name__)

@app.route("/")
def index():
    return render_template("index.html")

@app.route("/about")
def about():
    return render_template("about.html")

@app.route("/contact")
def contact():
    return render_template("contact.html")

if __name__ == "__main__":
    app.run(debug=True)
```

Now,  
- Going to `/` will show `index.html`.
- Going to `/about` will show `about.html`.
- Going to `/contact` will show `contact.html`.

**Tip:**  
You can link to these routes from your templates using Flask’s `url_for`:

```html
<a href="{{ url_for('about') }}">About</a>
<a href="{{ url_for('contact') }}">Contact</a>
```

---