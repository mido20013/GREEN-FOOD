import os
import zipfile

# Create folder structure
folder_path = "/mnt/data/veg_shop_site"
os.makedirs(folder_path, exist_ok=True)

# HTML content (from previous update, simplified into one HTML file)
html_content = """<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Fresh Vegetables Shop</title>
  <link href="https://cdn.jsdelivr.net/npm/tailwindcss@2.2.19/dist/tailwind.min.css" rel="stylesheet">
</head>
<body class="bg-green-50 font-sans">
  <header class="bg-green-600 text-white p-6 text-center text-3xl font-bold">
    Fresh Vegetables Shop
  </header>

  <section class="p-6 text-center">
    <h1 class="text-4xl font-bold mb-4">Welcome to Our Vegetable Shop</h1>
    <p class="text-lg">Fresh, organic, and healthy vegetables delivered to your door.</p>
  </section>

  <section class="grid grid-cols-1 md:grid-cols-3 gap-6 p-6">
    <div class="bg-white rounded-xl shadow p-4">
      <img src="https://images.unsplash.com/photo-1567306226416-28f0efdc88ce" alt="Tomatoes" class="rounded-lg mb-4">
      <h2 class="text-xl font-bold">Tomatoes</h2>
      <p class="text-gray-600">Fresh and juicy tomatoes.</p>
    </div>
    <div class="bg-white rounded-xl shadow p-4">
      <img src="https://images.unsplash.com/photo-1582515073490-dc84f6a05a13" alt="Carrots" class="rounded-lg mb-4">
      <h2 class="text-xl font-bold">Carrots</h2>
      <p class="text-gray-600">Organic crunchy carrots.</p>
    </div>
    <div class="bg-white rounded-xl shadow p-4">
      <img src="https://images.unsplash.com/photo-1601004890684-d8cbf643f5f2" alt="Broccoli" class="rounded-lg mb-4">
      <h2 class="text-xl font-bold">Broccoli</h2>
      <p class="text-gray-600">Healthy green broccoli.</p>
    </div>
  </section>

  <footer class="bg-green-600 text-white text-center p-4">
    © 2025 Fresh Vegetables Shop. All rights reserved.
  </footer>
</body>
</html>"""

# Save index.html
html_path = os.path.join(folder_path, "index.html")
with open(html_path, "w", encoding="utf-8") as f:
    f.write(html_content)

# Zip the folder for user to download
zip_path = "/mnt/data/veg_shop_site.zip"
with zipfile.ZipFile(zip_path, "w") as zipf:
    for root, dirs, files in os.walk(folder_path):
        for file in files:
            file_path = os.path.join(root, file)
            arcname = os.path.relpath(file_path, folder_path)
            zipf.write(file_path, arcname)

zip_path
