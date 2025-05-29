# Flask Auth0 App

This is a Flask-based web application integrated with Auth0 to demonstrate secure login, logout, and access-controlled routes. This lab project was built for CST8919 - Lab 1.

## 🎯 Objectives

- Implement user login and logout functionality using Auth0.
- Protect specific routes so they are accessible only to authenticated users.
- Demonstrate Auth0 integration in a Python Flask web app.

---

## 🚀 Setup Instructions

### 1. Clone the Repository

```bash
git clone https://github.com/praj0080/flask-auth0-app.git
cd flask-auth0-app
```

### 2. Create a Virtual Environment

```bash
python -m venv venv
venv\Scripts\activate   # For Windows
# OR
source venv/bin/activate  # For macOS/Linux
```

### 3. Install Dependencies

```bash
pip install -r requirements.txt
```

If you don’t have a `requirements.txt`, run:

```bash
pip install flask authlib python-dotenv
```

### 4. Setup `.env` File

Create a `.env` file in the root folder with your Auth0 credentials:

```ini
AUTH0_CLIENT_ID=1iJfZId8CsZgUtcTdBCKk14BMiS40dSg
AUTH0_CLIENT_SECRET=F3HYVzCMMhA5Vzd_QxvJAATPPnYBOJDQJcsAlkFUAHkJ06SDuqi3LvQePS2plFcJ
AUTH0_DOMAIN=dev-65yuhxtq0n6jvmfd.ca.auth0.com
AUTH0_CALLBACK_URL=http://localhost:3000/callback
APP_SECRET_KEY=1a80923a3f098aed4256347ab4595d2d220fd549e34a4348327838344d2808d8


```

Generate a secure secret key for `APP_SECRET_KEY` using:

```bash
python -c "import secrets; print(secrets.token_hex(32))"

```

---

## 🔧 Running the App

```bash
python server.py
```

Then open your browser and go to:

```
http://localhost:3000
```

You should be able to:

- Log in using Auth0
- View a protected page after login
- Log out securely

---

## 🔒 Protected Route

- `/protected`: Only accessible when logged in
- If a non-authenticated user tries to access it, they are redirected to `/login`
### 🔸 `/dashboard`

- Accessible only to authenticated users.
- Displays a personalized welcome message and user info.


---

## 📺 Demo Video

👉 [Watch 5-Minute Demo on YouTube](https://youtube.com/your-demo-video-link)

In this video:

- I demonstrate login, logout, and protected route access.
- Briefly explain the code setup.
- Share what I learned from integrating Auth0 with Flask.

---
## Additional Custom Routes

### `/protected` Route
This route serves a "Protected Page" which is only accessible to authenticated users. If a user is not logged in, they will be redirected to the login page.

```python
@app.route("/protected")
def protected():
    if not session.get("user"):
        return redirect(url_for("login"))
    return render_template("protected.html")
```

### `/dashboard` Route
This route can be used to show a dashboard after the user logs in successfully.

```python
@app.route("/dashboard")
def dashboard():
    if not session.get("user"):
        return redirect(url_for("login"))
    return render_template("dashboard.html", user=session["user"])
```
## 📂 Project Structure

```
flask-auth0-app/
├── templates/
│   ├── home.html
│   ├── dashboard.html
│   └── protected.html
├── .env
├── server.py
├── README.md
└── venv/
```

---

## 🙌 What I Learned

- How to securely integrate Auth0 with Flask
- Working with environment variables
- Creating protected routes
- Using OAuth2 and OpenID Connect standards

---


 
