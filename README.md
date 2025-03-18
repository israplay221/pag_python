﻿# pag_python
from flask import Flask, send_from_directory

import random
import os

app = Flask(__name__)

@app.route("/")
def hello_world():
    return """
    
    <h1>Hello, World!</h1>
        <ul>
        <li>
            <a href="/numeros">Dar click para ver numeros aleatorios</a>
        </li>
        <li>
        <a href="/datos">Dar click para ver datos aleatorios</a>
        </li>
    </ul>
    
    """

@app.route("/numeros")
def numeros():
    num = random.randint(1,100)
    return f"<h1> El numero es {num} </h1>"

@app.route("/datos")
def datos():
    datos = [
        "Jupiter es el planeta mas grande del sistema solar",
        "los ornitorrincos sudan leche 🙏",
        "El Sol es de color blanco ",
        "La capital de Colombia es Bogota",
        "El uniforme de Boca antes era blanco rayas negras, como era parecido al de otro equipo, decidieron en un partido quien se quedaria con el uniforme, el cual Boca perdio, entonces decidieron que el ultimo barco que llegara al puerto se quedaria con esos colores, el barco llevaba la bandera de Suecia y se quedaron con esos colores "
    ]
    return f"<h1> Aquí tienes un dato random: {random.choice(datos)} </h1>"

@app.route("/suma/<int:n1>/<int:n2>")
def suma(n1:int,n2:int):
    return f" <h1>La suma de {n1} con {n2} es {n1 + n2} </h1>"

@app.route("/meme")
def meme():
    return send_from_directory('static', 'meme.png')
    
if __name__ == '__main__':
    app.run(debug=True) 
