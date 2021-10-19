Alura - Python 3 - Introdução a Orientação a Objetos
===============================

[ ] TODO - Preencher
----------

```python
# Sintaxe import método

from teste import cria_conta, deposita, saca, extrato

teste.py
def cria_conta(numero, titular, saldo, limite):
   conta = {"numero": numero, "titular": titular, "saldo": saldo, "limite": limite}
   return conta
```

```python
# Sintaxe classe e import
conta.py

# Uma classe é uma especificação de um tipo, definindo valores e comportamentos.
class Conta:

    pass

from conta import Conta

# Um objeto é uma instância de uma classe onde podemos definir valores para seus atributos.
conta = Conta()
conta
# <conta.Conta object at 0x10715f518> # Imprime endereço de memória
```

```python

conta.py

class Conta: # Classe, módulo, package, namespace

    def __init__(self, numero, titular, saldo, limite): # O valor do self é passado pelo Python, responsável pela criação final do objeto em memória
        print("Construindo objeto...{}".format(self))
        self.numero = numero # self é a variável de referência que sabe encontrar o objeto construído em memória.
        self.titular = titular # Em self.titular, o caractere "ponto" (.) é um comando de ida ao objeto e numero, titular, saldo e limite são atributos.
        self.saldo = saldo # características ou atributos da classe
        self.limite = limite

        # Métodos, ações, comportamentos, função
        def cria_conta(numero, titular, saldo, limite):
            conta = {"numero": numero, "titular": titular, "saldo": saldo, "limite": limite}

        def saca(conta,valor):
            conta["saldo"] -= valor

        def extrato(conta):
            print("Saldo é {}".format(conta["saldo"]))

from conta import Conta

# Um objeto é uma instância de uma classe onde podemos definir valores para seus atributos.
conta = Conta()
conta
# <conta.Conta object at 0x10715f518> # Imprime endereço de memória
```

```python
#  o responsável por jogar fora esses objetos em desuso é o coletor de lixo (garbage collector, em inglês) do Python.

# Desfaz o apontamento para uma referencia de objeto. A palavra None é equivalente a palavra-chave null nas linguagens C# ou Java.

# O Python não possui uma palavra-chave para tornar um atributo privado — como Java tem o modificador de visibilidade private. Porém, foi convencionada uma nomenclatura especial: os dois underscore (__). Quando _ é utilizado, o atributo é renomeado pelo Python. Por exemplo, __conta passou a se chamar automaticamente _Conta__saldo. Desta forma, explicitamos para o desenvolvedor que se trata de um atributo privado. 

# Principio da responsabilidade unica de uma classe. deve ter apenas uma responsabilidade (ou deve ter apenas uma razão para existir).ela não deve assumir responsabilidades que não são delas. Manter coesão.

# getter and setter

def set_limite(self, limite): 
    self.__limite = limite

def get_saldo(self):
    return self.__saldo

# Na linguagem Python, os métodos que dão acesso são nomeados como properties. Desta forma, indicaremos para o Python nossa intenção de ter acesso ao objeto. 

   @property
   def nome(self): 
       return self.__nome.title()

# Agora, quando digitarmos nos console cliente.nome, sem a adição dos parênteses, e conseguiremos que o método seja executado como antes. 

@nome.setter
def nome(self, nome):
    print("chamando setter nome()")
    self.__nome = nome

# Esse métodos que conseguimos chamar sem uma referência recebem o nome de estáticos, porque eles fazem parte da classe. Todas as linguagens orientadas a objeto trabalham com métodos estáticos, mas para que eles sejam utilizados, iremos configurar os métodos. Fica inapropriado usar property, porque ele sempre precisa do self. A configuração correta será @staticmethod.

@staticmethod
def codigo_banco():
    return "001"

>>> from conta import Conta
>>> Conta.codigo_banco()
'001'

# Atributo de classe

class Circulo:

    PI = 3.14

Circulo.PI
3.14

```
