#Criação da FASTAPI usando Python
#Localhost: http://127.0.0.1:8000

from fastapi import FastAPI

from pydantic import BaseModel


app = FastAPI()

#Rota Raiz
@app.get("/")
def raiz():
    return {"Planetas Star Wars"}

#Criar model
class Planeta(BaseModel):
    id: int
    name: str
    climate: str
    terrain: str
    films: int

#Criar Base de dados

base_de_dados = [
    Planeta(id=1, name="Tatooine", climate="arid", terrain="desert", films=5),
    Planeta(id=2, name="Alderaan", climate="temperate", terrain="grasslands, mountains", films=2),
    Planeta(id=3, name="Yavin IV", climate="temperate, tropical", terrain="jungle, rainforests", films=1),
    Planeta(id=4, name="Hoth", climate="frozen", terrain="tundra, ice caves, mountain ranges", films=1),
    Planeta(id=5, name="Dagobah", climate="murky", terrain="swamp, jungles", films=3),
    Planeta(id=6, name="Bespin", climate="temperate", terrain="gas giant", films=1),
    Planeta(id=7, name="Endor", climate="temperate", terrain="forests, mountains, lakes", films=1),
    Planeta(id=8, name="Naboo", climate="temperate", terrain="grassy hills, swamps, forests, mountains", films=4),
    Planeta(id=9, name="Coruscant", climate="temperate", terrain="cityscape, mountains", films=4),
    Planeta(id=10, name="Kamino", climate="temperate", terrain="ocean", films=1)
]

#Rota Get ALL
@app.get("/planetas")
def get_todos_os_planetas():
    return base_de_dados

#Rota Get Id
@app.get("/planetas/{id_planeta}")
def get_planeta_id(id_planeta: int):
    for planeta in base_de_dados:
        if(planeta.id == id_planeta):
            return planeta

    return {"Status": 404, "Mensagem": "Planeta não encontrado"}

# Rota Get name
@app.get("/planetas/name/{name_planeta}")
def get_planeta_name(name_planeta: str):
    for planeta in base_de_dados:
        if (planeta.name == name_planeta):
            return planeta

    return {"Status": 404, "Mensagem": "Planeta não encontrado"}

#Rota Post
@app.post("/planetas")
def insere_planeta(planeta: Planeta):
    base_de_dados.append(planeta)
    return planeta

#Rota Delete
@app.delete("/delete/{name_planeta}")
def delete_planeta(name_planeta: str):
    for planeta in base_de_dados:
        if (planeta.name == name_planeta):
            return planeta

