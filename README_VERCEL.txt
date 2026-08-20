DAUR AWAZ — Official Citizen Portal — VERCEL DEPLOY GUIDE
by DK Lashari

Step 1: GitHub par repo banao
- Is folder ko GitHub par push karo

Step 2: Vercel par deploy
- vercel.com -> New Project -> Import GitHub repo
- Framework: Other
- Deploy dabao - 1 min me live!

Step 3: Live link
- Aap ko milega: https://daur-awaz.vercel.app
- Public: /
- Track Complaint: /track
- Chairman Login: /login (default: admin / admin123 — pehli dafa login karke
  turant /admin/account se password change kar lein)

============================================================
LOCAL PAR (Windows/Mac/Linux) RUN KARNE KA TARIKA
============================================================
1. Is folder mein terminal/CMD kholein
2. pip install -r requirements.txt
3. python app.py   (Windows par: python app.py, Mac/Linux par: python3 app.py)
4. Browser mein: http://127.0.0.1:5000

Database khud-ba-khud app.py ke saath waali folder mein
"daur_awaz_final.db" ban jayega — Vercel par ye khud "/tmp" use kar
lega, kuch manually change karne ki zaroorat nahi.

============================================================
ADMIN LOGIN, PASSWORD CHANGE, AUR PA/STAFF ACCOUNTS
============================================================
Ab admin accounts database mein store hote hain (env vars sirf pehli
dafa ke liye seed karte hain). Dashboard se hi sab manage hota hai:

- Apna password change karna:
    Login karein -> "My Account" (top right) -> Change Password
    Current password confirm karke naya password set kar sakte hain.

- Apna display name change karna:
    "My Account" page par "Save Name" se.

- PA / staff ke liye naya account banana:
    Login karein -> "Manage Users" (top right) -> "Add a New Admin Account"
    Unko alag username + password dein (apna password kabhi share na
    karein). Role "Assistant" rakhein agar unhe limited staff account
    chahiye, ya "Chairman" agar unhe bhi full access dena hai.

- Kisi account ko remove karna:
    "Manage Users" page par uske saamne "Remove" — aap apna khud ka
    account ya aakhri baaqi account remove nahi kar sakte (portal
    lock-out se bachane ke liye).

Note: pehli dafa app run hone par agar koi admin account nahi hai to
ADMIN_USERNAME / ADMIN_PASSWORD environment variables (ya admin/admin123
default) se ek account khud-ba-khud ban jata hai. Uske baad ye env vars
kuch nahi karte — sab kuch database aur dashboard se control hota hai.

Vercel Environment Variables (Project Settings mein) sirf pehli dafa
ke liye zaroori hain:
  ADMIN_USERNAME, ADMIN_PASSWORD, SECRET_KEY, CHAIRMAN_NAME,
  CONTACT_PHONE, CONTACT_EMAIL, OFFICE_ADDRESS

============================================================
Is version mein kya hai
============================================================
- Official government-style branding: seal/emblem, green+gold color
  scheme, bilingual Urdu/English headings, "Government of Sindh" tag
- Photo upload kaam karta hai (complaint ke saath tasveer)
- Standalone "Track Complaint" page — citizen tracking ID se live
  status + Chairman ki official remarks dekh sakta hai
- Chairman Dashboard mein har complaint par "official remarks"
- Multi-admin system: apna password khud change karein, PA/staff ke
  liye alag accounts banayein, unhe remove karein
- Search dono public wall aur admin dashboard mein

============================================================
Note on data persistence
============================================================
Free Vercel par SQLite "/tmp" me rehta hai — cold-start/restart par
reset ho jayega (admin accounts bhi reset ho jayenge, wapas default
admin/admin123 ban jayega). Permanent storage ke liye Vercel Postgres
istemal karna hoga (batayein to help kar dunga).

Agar aap ke paas Daur city ka asal official logo/seal hai to bhej
dein — abhi generic seal hai (emblem() function, app.py mein), usay
replace kiya ja sakta hai.
