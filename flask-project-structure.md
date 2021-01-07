# Flask Project Structure

> Part of [Flask Tutorial](https://github.com/app-generator/tutorial-flask): Learn how to structure your Flask project and compare the **pros** and **cons** between different options.

**Spot an issues or want to contribute?** - use the [Issues Tracker](https://github.com/app-generator/tutorial-flask/issues/) and tell us more. 

<br />

## Topics

- [Single File](#single-file)
- [Isolated `App` directory](#isolated-app-directory)
- [Blueprints with `app-factory` pattern](#blueprints)
- [Sample Apps](#sample-apps)

<br />

## Single File

:point_right: This structure is recommended for simple projects and DEMO's where we need to code simple apps fast.

<br />

```python
# Simple, one file Flask App 
from flask import Flask

app = Flask(__name__)

@app.route('/')
def hello():
    return f'Hello from Flask!'
```

The code will encapsulate routing, configuration, and assets management in the same place. To start the application, we need to export the `FLASK_APP` variable and invoke `flask run`. 

```bash
$ export FLASK_APP=run.py
$ flask run
```

Our simple app should be accessible in the browser: `localhost:5000`. By default Flask will start the application using the port **5000** but this can be changed using `--port` argument: 

```bash
$ # Flask app will start on 5001
$ flask run --port=5001
```

<br />

<p align="right"><a href="#topics"> :point_up_2: Return to top</a></p>

<br />

## Isolated app directory

:point_right: Once our project is getting bigger we might want to use a better codebase structure. The structure presented below it might be a good choice:

<br />

```bash
< PROJECT ROOT >
   |
   |-- app/
   |    |
   |    | -- config.py                     # App Configuration
   |    | -- models.py                     # Database Tables 
   |    | -- forms.py                      # App Forms: login, registration
   |    | -- util.py                       # Helpers to manipulate date, files  
   |    | -- views.py                      # App Routing
   |    | -- __init__.py                   # Bundle all above sections and expose the Flask APP 
   |    |
   |    |-- static/
   |    |    |-- <css, JS, images>         # CSS files, Javascripts files
   |    |
   |    |-- templates/
   |    |    |
   |    |    |-- includes/                 # Page chunks, components
   |    |    |    |
   |    |    |    |-- navigation.html      # Top bar
   |    |    |    |-- sidebar.html         # Left sidebar
   |    |    |    |-- scripts.html         # JS scripts common to all pages
   |    |    |    |-- footer.html          # The common footer
   |    |    |
   |    |    |-- layouts/                  # App Layouts (the master pages)
   |    |    |    |
   |    |    |    |-- base.html            # Used by common pages like index, UI
   |    |    |
   |    |    |-- accounts/                 # Auth Pages (login, register)
   |    |    |    |
   |    |    |    |-- login.html           # Use layout `base-fullscreen.html`
   |    |    |    |-- register.html        # Use layout `base-fullscreen.html`  
   |    |    |
   |    |  index.html                      # The default page
   |    |  page-404.html                   # Error 404 page (page not found)
   |    |  page-500.html                   # Error 500 page (server error)
   |    |    *.html                        # All other pages provided by the UI Kit
   |
   |-- requirements.txt                    # Application Dependencies
   |
   |-- run.py                              # Start the app in development and production
   |
   |-- ************************************************************************
```

<br />

> Relevant Files and folders

- `run.py` - is the entry point called to start the app
- `app/__init__.py` - bundle all app sections: configuration, forms, database connection
- App modules: `views` (routing), `config`, `forms`, `util`
- App static assets and template folders:
    - `static`: the place where JS,Images and CSS files are saved
    - `templates`: pages and components to be used 

<br />

> To visualize samples app that uses this structure please visit the [Sample Apps](#sample-apps) section.

<br />

<p align="right"><a href="#topics"> :point_up_2: Return to top</a></p>

<br />

## Blueprints

:point_right: ToDo

<br />

<p align="right"><a href="#topics"> :point_up_2: Return to top</a></p>

<br />

## Sample apps

:point_right: To visualize mentioned pattern in real-world Flask applications, here is a short-list:

- [Flask Swipe](https://github.com/app-generator/jinja-swipe-bootstrap-5) - uses the **[Isolated app directory](#isolated-app-directory)** pattern
- [Flask IraDesign](https://github.com/app-generator/flask-illustrations-iradesign) - uses the **[Isolated app directory](#isolated-app-directory)** pattern
- [Flask Datta Able](https://github.com/app-generator/flask-dashboard-dattaable) - uses the **[blueprints](#blueprints)** pattern

<br />

<p align="right"><a href="#topics"> :point_up_2: Return to top</a></p>

<br />

---
**Flask Project Structure** - [Flask Tutorial](https://github.com/app-generator/tutorial-flask) | by [AppSeed](https://appseed.us?ref=gh).
