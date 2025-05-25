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

### Notes

- Make sure all your static files (CSS, JS, images) are located in the `static` folder at the root of your Flask project.
- Use this pattern for **every** static file reference in your HTML templates.

---