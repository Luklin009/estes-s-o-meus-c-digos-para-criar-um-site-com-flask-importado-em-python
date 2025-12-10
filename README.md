# estes-s-o-meus-c-digos-para-criar-um-site-com-flask-importado-em-python


from flask import Flask, render_template, url_for


app = Flask(__name__)


@app.get("/")

def index():

    return render_template("index.html", titulo="Página inicial")


@app.get("/pagina-2")

def pagina2():

    return render_template("pagina2.html", titulo="Página 2")


@app.get("/pagina-3")

def pagina3():

    return render_template("pagina3.html", titulo="Página 3")


if __name__ == "__main__":

    app.run(debug=True)

    ARQUIVOS HTML
*BASE:

    <!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <title>{% block titulo %}Meu Site{% endblock %}</title>

    <!-- Arquivo CSS opcional -->
    <link rel="stylesheet" href="{{ url_for('static', filename='css/style.css') }}">
</head>

<body>
    <!-- Cabeçalho -->
    <header>
        <h1>Canvs</h1>

        <nav>
            <a href="{{ url_for('index') }}">Início</a>
            <a href="{{ url_for('pagina2') }}">Página 2</a>
            <a href="{{ url_for('pagina3') }}">Página 3</a>
        </nav>
        <hr>
    </header>

    <!-- Conteúdo de cada página -->
    <main>
        {% block conteudo %}{% endblock %}
    </main>

    <hr>
    <!-- Rodapé -->
    <footer>
        <p>&copy; 2025 - Meu Projeto you</p>
    </footer>
</body>
</html>

*INDEX:

{% extends "base.html" %}

{% block titulo %}Página Inicial{% endblock %}

{% block conteudo %}
<h2>Bem-vindo à página inicial!</h2>
<p>Este é o conteúdo da home.</p>
{% endblock %}

*PÁGINA 2:

{% extends "base.html" %}

{% block titulo %}Página 2{% endblock %}

{% block conteudo %}
<h2>Conteúdo da Página 2</h2>

<img src="{{ url_for('static', filename='img/minha_imagem.png') }}" 
     alt="https://i.ytimg.com/vi/-uKbF4mvVz8/maxresdefault.jpg"
     width="300">

<h2>Conteúdo da Página 2</h2>
<p>Alguma informação aqui...</p>
{% endblock %}

*PÁGINA 3:

{% extends "base.html" %}

{% block titulo %}Página 3{% endblock %}

{% block conteudo %}
<h2>Vídeo na Página 3</h2>

<video width="600" controls>
    <source src="{{ url_for('static', filename='video/video.mp4') }}" type="video/mp4">
    Seu navegador não suporta vídeos.
</video>https://www.youtube.com/watch?v=k8l7P7dEvTA
<h2>Conteúdo da Página 3</h2>
<p>Mais informações aqui...</p>
{% endblock %}
