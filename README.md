# extrassclube.github.io
Site do Extrassclube
from zipfile import ZipFile
import os

site_files = {
    "index.html": """
<!DOCTYPE html>
<html lang="pt-br">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Extrassclube</title>
  <script src="https://cdn.tailwindcss.com"></script>
</head>
<body class="bg-white text-gray-800">
  <section class="bg-red-600 text-white py-20 px-4 text-center">
    <h1 class="text-5xl font-bold mb-4">Extrassclube</h1>
    <p class="text-xl">Transforme seus sonhos em realidade acadêmica.</p>
  </section>
  <section class="bg-white py-10 px-4 text-center">
    <div class="max-w-3xl mx-auto">
      <img src="assets/visionboard.jpg" alt="Vision Board" class="mx-auto mb-4 rounded shadow-lg">
      <p class="text-lg">Vision board é uma ótima forma de idealizar e visualizar seus sonhos.</p>
    </div>
  </section>
  <section class="bg-white py-10 px-4 text-center">
    <input type="text" placeholder="Busque por área, universidade ou prova..." class="border px-4 py-2 rounded w-full max-w-lg">
  </section>
  <section class="bg-white py-10 px-4" id="areas">
    <h2 class="text-3xl font-bold text-center mb-8">Áreas de Estudo</h2>
    <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
      <div class="border p-4 rounded shadow">
        <h3 class="font-bold text-xl mb-2">Engenharia Aeroespacial</h3>
        <p class="text-sm mb-2">10 atividades extracurriculares...</p>
        <p class="text-sm">Universidades: MIT, Stanford...</p>
      </div>
    </div>
  </section>
  <section class="bg-gray-100 py-10 px-4" id="universidades">
    <h2 class="text-3xl font-bold text-center mb-8">Universidades</h2>
    <div class="space-y-4 max-w-4xl mx-auto">
      <div class="p-4 bg-white rounded shadow">
        <h3 class="text-xl font-bold">Harvard University</h3>
        <p>Aprovação: ~4% - SAT/ACT, TOEFL/IELTS, entrevista...</p>
      </div>
    </div>
  </section>
  <section class="bg-red-600 text-white py-16 px-6 text-center" id="sobre">
    <h2 class="text-3xl font-bold mb-4">Sobre Mim</h2>
    <p class="text-lg max-w-2xl mx-auto leading-relaxed mb-4">
      Olá! Eu sou a <strong>Julia Bulla</strong> e estou aqui para te ajudar a encontrar as suas <strong>extracurriculares dos sonhos</strong>!
    </p>
    <p class="italic mb-4">“A educação transforma, e com as escolhas certas, você pode ir muito mais longe do que imagina.”</p>
    <a href="https://instagram.com/bulla_julia" target="_blank" class="underline">Instagram: @bulla_julia</a>
  </section>
  <section class="bg-white py-10 px-4 text-center" id="contato">
    <h2 class="text-2xl font-bold mb-4">Tem alguma dúvida? Nos pergunte!</h2>
    <form action="mailto:juliacaldart@gmail.com" method="POST" enctype="text/plain" class="max-w-md mx-auto space-y-4">
      <input type="text" name="name" placeholder="Seu nome" class="w-full border px-4 py-2 rounded">
      <textarea name="message" placeholder="Sua mensagem" class="w-full border px-4 py-2 rounded"></textarea>
      <button type="submit" class="bg-red-600 text-white px-6 py-2 rounded">Enviar</button>
    </form>
  </section>
</body>
</html>
""",
    "assets/visionboard.jpg": b"",  # Substitua com sua imagem depois
}

zip_name = "extrassclube_site.zip"
with ZipFile(zip_name, "w") as zipf:
    for filepath, content in site_files.items():
        os.makedirs(os.path.dirname(filepath), exist_ok=True)
        mode = "wb" if isinstance(content, bytes) else "w"
        with open(filepath, mode) as f:
            f.write(content)
        zipf.write(filepath)
        os.remove(filepath)

print(f"Arquivo {zip_name} gerado com sucesso!")
