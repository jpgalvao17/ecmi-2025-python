import json
import requests
import pandas as pd

nome = input("digite o seu nome: ")
busca_deputado = input("Pelo que você deseja buscar? UF, Partido ou Nome? ").lower()
infomacao_deputados = input(f"Por qual {busca_deputado} você deseja buscar? ").lower()
retorno_api = requests.get("https://dadosabertos.camara.leg.br/api/v2/deputados")
base = retorno_api.json()
base_auxiliar = []



for deputado in base['dados']:
 base_auxiliar.append(deputado)
 pd.DataFrame(base_auxiliar)

deputados = pd.DataFrame(base_auxiliar)

deputados['nome'] = deputados['nome'].str.lower()
deputados['siglaPartido'] = deputados['siglaPartido'].str.lower()
deputados['siglaUf'] = deputados['siglaUf'].str.lower()


if busca_deputado =='nome':
  resultado=deputados[deputados['nome'] == infomacao_deputados]
  print(resultado)
elif busca_deputado == 'uf':
  resultado = deputados[deputados['siglaUf'] == infomacao_deputados]
  print(resultado)

elif busca_deputado == 'partido':
  resultado=deputados[deputados['siglaPartido'] == infomacao_deputados]
  print(resultado)

else:
  print("o que voce pesquisou nao se aplicar no modo de busca tente novamente /n pesquisa disponivel (nome . uf , partido ) ")

print(resultado)
