# Security Policy

## Supported Versions

Use this section to tell people about which versions of your project are
currently being supported with security updates.

| Version | Supported          |
| ------- | ------------------ |
| 5.1.x   | :white_check_mark: |
| 5.0.x   | :x:                |
| 4.0.x   | :white_check_mark: |
| < 4.0   | :x:                |

## Reporting a Vulnerability

Use this section to tell people how to report a vulnerability.

Tell them where to go, how often they can expect to get an update on a
reported vulnerability, what to expect if the vulnerability is accepted or
declined, etc.

<div class="admin-login" id="adminLogin">
  <div class="login-card">
    <div class="shield">🛡️</div>
    <h2>SECURITY JFB</h2>
    <p>SUPER ADMIN PORTAL</p>

    <div class="owner">
      <strong>MD Jannatul Fardous</strong>
      <small>Owner · Super Admin</small>
    </div>

    <form id="loginForm">
      <label>Admin Username</label>
      <input id="username" autocomplete="username"
        placeholder="Enter username" required>

      <label>Password</label>
      <input id="password" type="password"
        autocomplete="current-password"
        placeholder="Enter password" required>

      <button type="submit">SECURE LOGIN</button>
      <p id="loginMessage"></p>
    </form>
  </div>
</div>

<style>
.admin-login {
  min-height:100vh;
  display:grid;
  place-items:center;
  background:#070d18;
  color:white;
  font-family:Arial,sans-serif;
  padding:20px;
}
.login-card {
  width:100%;
  max-width:380px;
  padding:28px;
  background:#111d30;
  border:1px solid #164c66;
  border-radius:20px;
  text-align:center;
}
.shield {font-size:55px}
.login-card h2 {color:#26d9ff}
.login-card p {color:#9aafc5}
.owner {
  margin:22px 0;
  padding:15px;
  background:#192b40;
  border-radius:12px;
}
.owner small {display:block;color:#26d9ff}
.login-card label {
  display:block;
  text-align:left;
  margin:12px 0 5px;
}
.login-card input {
  width:100%;
  padding:13px;
  border-radius:9px;
  border:1px solid #31516c;
  background:#081321;
  color:white;
}
.login-card button {
  width:100%;
  margin-top:20px;
  padding:14px;
  background:#13c9e9;
  border:0;
  border-radius:9px;
  font-weight:bold;
}
</style>

<script>
document.getElementById("loginForm").addEventListener(
  "submit", async function(e) {
    e.preventDefault();

    const message =
      document.getElementById("loginMessage");

    const username =
      document.getElementById("username").value;

    const password =
      document.getElementById("password").value;

    try {
      const response = await fetch("/api/admin/login", {
        method: "POST",
        headers: {"Content-Type":"application/json"},
        credentials: "same-origin",
        body: JSON.stringify({username,password})
      });

      if (!response.ok) throw new Error("Login failed");

      message.textContent = "Login successful!";
      location.href = "/admin/dashboard";
    } catch {
      message.textContent =
        "Login failed. Check your credentials.";
    }
  }
);
</script>
