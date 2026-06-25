from zipfile import ZipFile
import os

base="/mnt/data/chronux_store"
os.makedirs(base, exist_ok=True)

html="""<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>CHRONUX</title>
<link rel="stylesheet" href="style.css">
</head>
<body>
<header>
<h1>CHRONUX</h1>
<p>Premium Online Store</p>
<nav>
<a href="#products">Products</a>
<a href="#about">About</a>
<a href="#contact">Contact</a>
</nav>
</header>

<section class="hero">
<h2>Luxury Looks. Smart Prices.</h2>
<p>Watches • Footwear • Gadgets</p>
<button onclick="document.getElementById('products').scrollIntoView()">Shop Now</button>
</section>

<section id="products" class="grid">
<div class="card">
<h3>Premium Watches</h3>
<p>Starting ₹699</p>
<button>Order on WhatsApp</button>
</div>
<div class="card">
<h3>Footwear</h3>
<p>Latest Arrivals</p>
<button>Order on WhatsApp</button>
</div>
<div class="card">
<h3>Accessories</h3>
<p>More Coming Soon</p>
<button>View</button>
</div>
</section>

<footer id="contact">
<p>© 2026 CHRONUX</p>
<p>WhatsApp: Add your number</p>
</footer>
<script src="script.js"></script>
</body>
</html>"""

css="""*{margin:0;padding:0;box-sizing:border-box;font-family:Arial,sans-serif}
body{background:#0d0d0d;color:#fff}
header{padding:20px;text-align:center;background:#111;position:sticky;top:0}
nav a{color:#fff;text-decoration:none;margin:0 10px}
.hero{padding:80px 20px;text-align:center;background:linear-gradient(135deg,#111,#222)}
.hero h2{font-size:2.4rem}
button{margin-top:15px;padding:12px 20px;border:none;border-radius:8px;background:#d4af37;color:#000;font-weight:bold;cursor:pointer}
.grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(220px,1fr));gap:20px;padding:30px}
.card{background:#1b1b1b;padding:20px;border-radius:14px;border:1px solid #333;text-align:center}
footer{text-align:center;padding:30px;background:#111}
"""

js="""document.querySelectorAll('button').forEach(b=>b.addEventListener('click',()=>{
alert('Connect your WhatsApp link and products later.');
}));"""

readme="""# CHRONUX
Premium online store template.
Upload these files to GitHub and enable GitHub Pages.
"""

for name,content in [("index.html",html),("style.css",css),("script.js",js),("README.md",readme)]:
    with open(os.path.join(base,name),"w",encoding="utf-8") as f:
        f.write(content)

zip_path="/mnt/data/CHRONUX_Premium_Store_Template.zip"
with ZipFile(zip_path,"w") as z:
    for fn in os.listdir(base):
        z.write(os.path.join(base,fn),arcname=fn)

print(zip_path)

