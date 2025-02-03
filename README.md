# POO_Reto_6


### Soy Malcom Yamil Carrillo Quintero y pertenezco al grupo de "Fenomenoides", adelante se muestra nuestro logo
<details><summary>Preparense para ver el grandioso logo: </summary><p>
<div align='center'>
<figure> <img src="https://i.postimg.cc/NFbwf57S/logo-def.png" alt="Defensa Civil" width="400" height="auto"/></br>
<figcaption><b> "somos programadores, no diseñadores" </b></figcaption></figure>
</div>
</p></details><br>


## 1.
Crear una función que realice operaciones básicas (suma, resta, multiplicación, división) entre dos números, según la elección del usuario, la forma de entrada de la función será los dos operandos y el caracter usado para la operación. entrada: (1,2,"+"), salida (3).

```python
def main():
    print("Ingrese sus numeros y la operación que quiere aplicarles")
    a=int(input("Ingrese su primer entero"))
    b=int(input("Ingrese su segundo entero"))
    op=input("Ingrese la operación que quiere aplicar (símbolo: +, -, /, *)")
    match op:
        case "+":
            res=a+b
        case "-":
            res=a-b
        case "*":
            res=a*b
        case "/":
            res=a/b
        case _:
            print("No se ha ingresado una operación valida")
            main()
    return a, b, op, res
if __name__=="__main__":
    a, b, op, res=main()
    print(f"El resultado de {a} {op} {b} es {res}")

```
Para esta se toma una aproximación simple permitiendo la entrada de los numeros y la operación y realizando la operación a través de un match case de acuerdo al signo ingresado por el usuario. En caso de operar en una versión mas antigua de python que no cuente con el match case funcionaria igual pero con ifs y elifs
```python
def main():
    print("Ingrese sus numeros y la operación que quiere aplicarles")
    a=int(input("Ingrese su primer entero"))
    b=int(input("Ingrese su segundo entero"))
    op=input("Ingrese la operación que quiere aplicar (símbolo: +, -, /, *)")
    if op=="+":
        res=a+b
    elif op=="-":
        res=a-b
    elif op=="*":
        res=a*b
    elif op=="/":
        res=a/b
    else:
        print("No se ha ingresado una operación valida")
        main()
    return a, b, op, res
if __name__=="__main__":
    a, b, op, res=main()
    print(f"El resultado de {a} {op} {b} es {res}")
```
## 2.
Realice una función que permita validar si una palabra es un palíndromo. Condición: No se vale hacer slicing para invertir la palabra y verificar que sea igual a la original.

```python
def palindromo(palabra:int)->str:
    pal_char=list(palabra)
    inv_pal_char=[]
    for i in range(len(pal_char)):
        inv_pal_char.insert(0, pal_char[i])
    return pal_char==inv_pal_char

if __name__=="__main__":
    palabra=input()
    pal=palindromo(palabra)
    if pal:
        print(f"la palabra {palabra} es un palindromo")
    else:
        print(f"la palabra {palabra} NO es un palindromo")
```
Al convertir el string en una lista e insertar de manera contraria sus elementos en una lista, es posible tener 2 listas que al compararlas se pueda saber si la palabra original es un palindromo o no si las 2 listas son iguales

## 3.
Escribir una función que reciba una lista de números y devuelva solo aquellos que son primos. La función debe recibir una lista de enteros y retornar solo aquellos que sean primos.
```python
def primo(numero:int):
    limite=(int(numero/2)+1)
    for i in range(2, limite):
        if numero%i==0:
            return False
    return True

if __name__=="__main__":
    l_lista=int(input("De cuantos numeros quiere su lista: "))
    lista=[]
    for i in range(l_lista):
        lista.append(int(input(f"Ingrese el numero {i+1}: ")))
    primos=[]
    for i in lista:
        if primo(i):
            primos.append(i)
    print(f"Los numeros primos de la lista de numeros dados son: \n{primos}")
```
A partir de determinar si el modulo de entre 2 numeros es 0 se sabe si uno es divisor de otro. Para obtener los primos se descarta con este metodo los posibles divisores que se encuentran entre 2 y la mitad de cada numero, de esta manera se evalua si un numero es primo o no para separarlo en otra lista

## 4.
Escribir una función que reciba una lista de números enteros y retorne la mayor suma entre dos elementos consecutivos.
```python
def mayor_suma(numeros: list):
    mayor=0
    elementos=[0, 0]
    index=[0, 0]
    for i in range(len(numeros)-1):
        sum=numeros[i]+numeros[i+1]
        if sum>mayor:
            mayor=sum
            elementos[0], elementos[1]=numeros[i], numeros[i+1]
            index[0], index[1]=i+1, i+2
    return mayor, elementos, index

if __name__=="__main__":
    l_lista=int(input("De cuantos numeros quiere su lista: "))
    numeros=[]
    for i in range(l_lista):
        numeros.append(int(input(f"Ingrese el numero {i+1}: ")))
    mayor, elementos, index=mayor_suma(numeros)
    print(f"De la lista {numeros} 
          \nla mayor suma posible de consecutivos es: {mayor} 
           \nde los elementos{elementos} 
           \nen las posiciones {index}")
```
Las sumas se obtienen de recorrer la lista y sumar cada elemento con el elemento que le sigue, y comparando el resultado de esta suma con la que previamente se habia determinado como mayor en todos los casos se conserva la mayor suma al final con sus elementos e indices extraidos

## 5.
Escribir una función que reciba una lista de string y retorne unicamente aquellos elementos que tengan los mismos caracteres. e.g. entrada: ["amor", "roma", "perro"], salida ["amor", "roma"]

```python
def id_letras(palabras:list):
    palab=palabras.copy()
    for i in range(len(palab)):
        palab[i]=palab[i].lower()
        palab[i]=''.join(sorted(palab[i]))
    repet=[]
    unic=[]
    for i in range(len(palab)):
        if palab[i] in unic:
            unic.remove(palab[i])
            repet.append(palab[i])
        else:
            unic.append(palab[i])
    apar=[]
    for i in range(len(repet)):
        lista=[]
        while repet[i] in palab:
            ind=palab.index(repet[i])
            lista.append(palabras[ind])
            palab[ind]=" "
        if len(lista)>2:
            apar.append(lista)
    return apar

if __name__=="__main__":
    l_lista=int(input("De cuantas palabras quiere su lista: "))
    palabras=[]
    for i in range(l_lista):
        palabras.append(input(f"Ingrese la palabra {i+1}: "))
    apar=id_letras(palabras)
    for i in apar:
        print(i)
```
Para obtener las palabras con los mismos caracteres opté por encontrar una manera de que fuera mas facil encontrar cuales eran iguales, que en este caso es haciendo que las palabras se reorganicen de manera alfabetica en una copia de la lista que se va a utilizar para ubicar sus indices y extraerlos en listas aparte
