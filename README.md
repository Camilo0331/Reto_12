# Reto_12

Procesar el archivo y extraer:

Cantidad de vocales
Cantidad de consonantes
Listado de las 50 palabras que más se repiten
Listado de destinatarios con cantidad de mensajes recibidos
Cantidad de mensajes enviados por cada día

```
def contarVoca(texto:str):
    listaVo = ['A','E','I','O','U','a','e','i','o','u']
    o = 0
    for i in texto:
        if i in listaVo:
            o += 1
    return o

def contarConso(texto:str)-> int:
    listaVo = ['A','E','I','O','U','a','e','i','o','u']
    o = 0
    for i in texto:
        if i.isalpha and i not in listaVo:
            o +=1
    return o

def palabrasRep(texto:str): 
    u = texto.split() #Se crea una lista con lo que 
    for i in range(len(u)):
        if not u[i].isalpha():
            o = u[i].strip(".,<>()[]:;/-_")
            u.pop(i)
            u.insert(i, o)
    for n in u:
        if not n.isalpha():
            u.remove(n)
    diccionario = {}
    for m in u:
        if m in diccionario:
            diccionario[m] +=1
        else:
            diccionario[m] =1
    lista2 = list(diccionario.items())
    lista3 = []
    for k in range(len(lista2)):
        p = lista2[k][::-1]
        lista3.append(p)
        lista3.sort(reverse=True)
        b = 0
        while b < 50 and b < len(lista3):
            print(lista3[b])
            b +=1

def contarDesti(texto:str):
    lista = texto.split()
    dic = {}
    for i in range(len(lista)):
        if (lista[i]== "by" or lista[i]=="BY") and lista[i-1]:
            if lista[i+1] in dic:
               dic[lista[i+1]] +=1
            else:
                dic[lista[i+1]] =1
    return dic

def cantidadDias(texto:str):
    texto2 = texto.split()
    lista1 = []
    for i in range(len(texto2)):
        lista2 = []
        while texto2[i] != "-0500" and texto2[i] != "(GMT)":
            lista2.append(texto2[i])
            i +=1
        lista1.append(lista2)
    dias = {}
    for i in range(len(lista1)):
        k = lista1[i].index("Jan")
        dia = (lista1[i][k-1])
        if dia in dias:
            dias[dia] +=1
        else: 
            dias[dia] =1
    return dias
        


if __name__=="__main__":
    with open("C:/Users/MSI 1/Downloads/py/hola.txt", "r")  as text:
        texto = text.read()
    voca = contarVoca(texto)
    print("la cantidad de vocales en el texto son "+str(voca))
    conso = contarConso(texto)
    print("la cantidad de consonantes en el texto son "+str(conso))
    palabrasRep(texto)
    desti = contarDesti(texto)
    print(desti)
    dias = cantidadDias(texto)
    print(dias)

```

### ¡Gracias por veer el repo!
