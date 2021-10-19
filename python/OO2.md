Alura - Python 3 - Avançando na Orientação a Objetos
===============================

[ ] TODO - Preencher
----------

```python

# Modelo - classes que representam o domínio do sistema.

# Sintaxe mínima para uma classe
class Livro
    pass # Permite que o código rode sem erro, apesar de incompleto.

dom_casmurro = Livro()
print(dom_casmurro) # imprime localização da instancia do objeto e mais nada.

# C:\Users\Alura\Appdata\Local\Progrms\Python\Python36-32\pythosn.exe\luan.silva
# <_mains_.Filme object at 0x050220F0>

# Process finished with code 0

```

```python

# Construtor

class Filme:
    def __init__(self, nome, ano, duracao):
        self._nome = nome
        self.ano = ano
        self.duracao = duracao
        self._likes = 0

    def dar_like(self):
        self.likes += 1

    @property #anotação que permite acessar um atributo privado.
    def likes(self):
         return self.__likes

    @property
    def nome(self):
        return self.__nome

    @nome.setter #anotação que permite alterar um atributo privado.
    def nome(self, novo_nome):
        self.__nome = novo_nome.title()

vingadores = Filme('vingadores - guerra infinita', 2018, 160)

vingadores.dar_like()

# Anotação de formatação - python 3.6+
print(f'Nome: {vingadores.nome} - Ano: {vingadores.ano} '
f'- Duração: {vingadores.duracao} - Likes: {vingadores.likes}')

```

```python
# Métodos String

<String>.capitalize() # Torna a primeira letra da String em maiúscula.

<String>.title() # Transforma cada primeira letra de cada palavra em maiúscula.
```

```python
# Os elementos que não necessitam de proteção, sem nenhuma lógica, ficarão públicos. Na linguagem Python, é raro deixarmos tudo como private, isto é mais recorrente em outras linguagens, que têm aspectos diferentes. No Python, o recomendável é mantermos nosso código simples para que ele seja de fácil compreensão e mais expressivo.
```

```python

# Atributo de Classe

class Pessoa:
    tamanho_cpf = 11

    def __init__(self, cpf, nome):
        self.cpf = cpf
        self.nome = nome

    def valida_cpf(self):
        return True if len(self.cpf) == __class__.tamanho_cpf else False # __class__ retorna os atributos de classe.

pe = Pessoa('00000000001', 'Ruby')
print(pe.valida_cpf())

pe = Pessoa('0000000000', 'Cristal')
print(pe.valida_cpf())

p = Pessoa()

print(p.tamanho_cpf) # Procura o atributo na instância, não encontrando procura na classe.

p.tamanho_cpf = 12 # Seta um novo atributo na instância que será diferente da classe.

print(p.tamanho_cpf) # Imprime o atributo da instânci.

print(Pessoa.tamanho_cpf) # Imprime o atrivuto da classe.

```

```python

# Herança - Generalização x Especialização - Relacionamento "É um"

# Justificativas para Herança
#   Interface, quando queremos resolver questões relativas a polimorfismo;
#   Reuso do código, ou remoção de duplicações.

class Programa:
    def __init__(self, nome, ano):
        self._nome = nome.title()
        self.ano = ano
        self._like = 0 #  _ (underscore) é uma convenção para criar a ideia de protegido, sem fazer o name mangling.

        @property
        def likes(self):
            return self._likes

        def dar_likes(self):
            self._likes += 1

        @property
        def nome(self):
            return self._nome

        @nome.setter
        def nome(self, novo_nome):
            self._nome = novo_nome.title()

class Filme(Programa):
    def __init__(self, nome, ano, duracao): # Sobreescrita do método.
        super().__init__(nome, ano) # Acessa a superclase
        self.duracao = duracao # Extensão do init da classe mãe

def __str__(self): # Dunder method que retorna um objeto em uma representção textual.
    return f'{self._nome} - {self.ano} - {self._likes} Likes'

class Serie(Programa):
    def __init__(self, nome, ano, temporadas):
        super().__init__(nome, ano)
        self.temporadas = temporadas

filmes_e_series = [vingadores, atlanta]

# Se aproveita da similaridade de um supertipo em comum para percorrer uma lista de tipos. Polimorfismo.
for programa in filmes_e_series:
    print(programa)

```

```python

# Métodos de classe

class Funcionario:
    prefixo = 'Instrutor'

    @classmethod
    def info(cls): # cls é a convenção equivalente a self usado em classes.
        return f'Esse é um {cls.prefixo}'

# Um método de classe pode ser acionado dentro dos métodos de uma instância através da palavra reserva __class__.

# Um método de classe, possibilita acesso aos atributos da classe.

# Métodos estáticos

class FolhaDePagamento:
    @staticmethod
    def log():
        return f'Isso é um log qualquer'

# Um método estático não recebe cls como argumento, e não acessa os atributos da classe. O método estático é acessível através da classe e suas instâncias.

# Alguns pythonistas não aconselham o uso do @staticmethod, já que poderia ser substituído por uma simples função no corpo do módulo. Outros mais puristas entendem que os métodos estáticos fazem sentido, sim, e que devem ser vistos como responsabilidade das classes.

# Quando vamos modelar classes e objetos, devemos levar em consideração suas responsabilidades. Portanto, o ideal seria que cada classe tivesse sua responsabilidade com clareza e, quando isto ocorre, é possível chamá-la de classe coesa, ou seja, quando ela sabe qual é sua responsabilidade e não faz mais do que aquilo a que se propõe a fazer.

```

```python
# Herança de uma classe built-in

class Playlist(list):
    def __init__(self, nome, programas):
        self.nome = nome
        super().__init__(programas)

# É um risco herdar uma classe não conhecida em sua totalidade.
```

```python
# Composição - Em vez de termos um relacionamento é um, teremos Playlist tem um list, assim sendo, ninguém precisa saber como a lista interna funciona, mesmo se quisermos fazer uma implementação de lista diferente da que está sendo usada. Isso porque a nossa interface é mais simples, e não precisamos expor todos os métodos de list.

class Playlist:
    def __init__(self, nome, programas):
        self.nome = nome
        self._programas = programas

    def __getitem__(self, item): # Torna a classe iterable
        return self._programas[item]

    @property
    def tamanho(self):
        return len(self._programas)

    def __len__(self): # Faz com que a classe se comporte como um sized, uma ideia de algo que possui tamanho
        return len(self._programas)

print(vingadores in playlist_fim_de_semana) # o método __getitem__() possibilita o uso das estruturas for in e in.

print(f'Tamanho do playlist: {len(playlist_fim_de_semana)}') # Aciona o método __len__()

print(playlist_fim_de_semana[0]) # Também permite o acesso de itens através de índexes.

# O nome desta característica da linguagem é Duck typing, termo famoso por causa de uma fala do Alex Martelli. Este termo remete à "tipagem de pato", dando a ideia de que não precisamos necessariamente identificar uma ave para saber se trata-se de um pato ou não, basta sabermos se ela emite o mesmo som que o pato, voa ou anda como ele.

# Não precisamos nos preocupar com isto, pois o próprio Python verificará se ele se comporta como tal. Então, se sabemos que ele se comporta como um iterável, não precisamos nos preocupar com a sua tipagem.

# Sendo assim, podemos fazer a nossa playlist se passar por outro tipo de objeto específico, sem precisarmos da herança; e não chamamos isso de polimorfismo, e sim de duck typing.

# No Python Data Model, todo objeto em Python pode se comportar de forma a ser compatível e mais próximo à linguagem, e de toda a ideia idiomática dela.

# Por exemplo, imaginem que queremos adicionar um item à playlist - neste caso, não poderíamos utilizar um append(), porque não o herdamos da estrutura de lista. No entanto, poderíamos definir que o operador + fará uma adição de um item na nossa lista interna. Para isto, é necessário implementarmos __add__(). Assim, conseguimos implementar o funcionamento dos operadores aritméticos com o objeto, ou com a forma como eles se interagem, o que é bem interessante. 

# Interface. No Python, é algo muito próximo a algumas linguagens do tipo Smalltalk, isto é, de protocolo. Isto quer dizer que nosso objeto precisa se comportar daquele modo específico, sendo necessária a implementação de métodos que comportem segundo um protocolo específico.

# Além disso, há uma grande vantagem: implementamos apenas o __getitem__() e, se tivéssemos uma interface como no Java, teríamos que implementar todos os métodos. Neste caso, com o __getitem__(), ele funcionará perfeitamente pois temos como fazer isso parcialmente.

# Então, o duck typing nos permite que sigamos o protocolo de forma parcial, o que acaba sendo bem interessante. 

# Composição significa menos acoplamento.
```

```python
# Contrato de interface no Python

# Existem algumas classes abstratas denominadas ABC, acrônimo para Abstract Base Classes.

# No Python, não é muito aconselhável criar nossas próprias classes abstratas, por ser um aspecto mais avançado da linguagem, já que lidaremos com metaprogramação, e afins. O Python recomenda que, caso queiramos criar uma classe que dependa de outra, precisamos checar se já não existe uma destas classes base prontas para uso.

# Se importarmos um pacote collections.abc, por exemplo, que contém diversas classes que podem ser utilizadas, inclusive o MutableSequence, uma sequência mutável cujos valores podem ser alterados:

from collections.abc import MutableSequence

class Playlist(MutableSequence):
    pass

filmes = Playlist()

# TypeError: Can't instantiate abstract class Playlist with abstract methods __delitem__, __getitem__, __len__, __setitem__, insert

# No caso de tentarmos implementar MutableSequence, seremos avisados das funções e métodos que também precisam ser implementados na nossa classe para que ela se comporte perfeitamente, como uma classe ABC.

# Este conceito surgiu para complementar a ideia do duck typing, pois existem algumas validações que precisamos fazer dependendo daquilo que estivermos criando em nosso sistema, que o duck typing ainda não nos garante.

# Pode até ser que tenhamos o comportamento do __getitem__(), por exemplo, mas pode ser que queiramos outros, e validar se aquele objeto realmente os possui. E se herdarmos diretamente, teremos os comportamentos, mas tampouco teremos a garantia do tipo específico do objeto de que estamos herdando, isto é, da superclasse.

# Neste caso, estamos reforçando a validação e inspecionando a classe de alguma maneira, por meio da abstract base class para saber se ela implementa tais métodos.

# Diferentemente do Java, no Python, pode ter uma implementação na classe que possui o método abstrato. Ou seja, se este for o caso, poderemos aproveitar esta implementação; seria um início para podermos cuidar de algo. Neste exemplo, uma parte de __getitem__() já está implementada, e podemos continuar implementando, ou modificá-la.

# No entanto, para isto é preciso consultar a documentação destas classes.

# Resumo vantagens: Tenho um erro que me diz, em tempo de instanciação, se eu esqueci de implementar algum método da superclasse. E também sou impedido de instanciar um objeto do tipo da superclasse, pra não ter problema com os métodos abstratos.Ainda posso aproveitar código dos meus métodos abstratos (que podem ter implementação na classe mãe)
 
```

```python
# No Python, não é preciso herdar de uma classe específica pra ter polimorfismo. O que é importante no Python é: se você quer um iterável, devo se preocupar com o que um iterável deve fazer.

# O nome dessa característica é duck typing.

# Com duck typing, você ganha muita flexibilidade ao não precisar ficar preso aos tipos dos objetos, só que em alguns momentos você pode querer ter restrições, como de uma garantia que uma classe implemente os métodos que você quer.
```

```python
# Criando uma classe abstrata

from abc import ABCMeta, abstractmethod 
class Programa(metaclass = ABCMeta): 
    @abstractmethod 
    def __str__(self): 
        pass
```

```python
# Herança Múltipla

# Conseguimos reaproveitar comportamentos de vários locais diferentes, podendo organizar melhor as responsabilidades das superclasses.

class Funcionario:
    def registra_horas(self, horas):
        print('Horas registradas...')

    def mostrar_tarefas(self):
        print('Fez muita coisa...')

class Caelum(Funcionario):
    def mostrar_tarefas(self):
        print('Fez muita coisa, Caelumer')

    def busca_cursos_do_mes(self, mes=None):
        print(f'Mostrando cursos - {mes}' if mes else 'Mostrando cursos desse mês')

class Alura(Funcionario):
    def mostrar_tarefas(self):
        print('Fez muita coisa, Alurete!')

    def busca_perguntas_sem_resposta(self):
        print('Mostrando perguntas não respondidas do fórum')

class Junior(Alura):
    pass

class Pleno(Alura, Caelum): # Prioridade das classes é lida da esquerda para direita.
    pass

jose = Junior()
jose.busca_perguntas_sem_resposta()

luan = Pleno()
luan.busca_perguntas_sem_resposta()
luan.busca_cursos_do_mes()

luan.mostrar_tarefas()

# Para a tomada de decisão sobre qual método deverá ser executado quando temos diversas superclasses que o possuem, internamente, a versão 3 do Python usa um algoritmo chamado MRO (Method Resolution Order), com um funcionamento que começa a busca pela classe atual, que é a própria classe.

# Por exemplo, em Pleno, a primeira classe que será buscada neste caso é o próprio Pleno. Em seguida, o acesso será em sua classe mãe. No caso, ela possui duas mães, Alura e Caelum, e é aí que ocorre a primeira distinção - a primeira classe mãe é Alura, portanto ela será consultada primeiro.

# Além disto, o cálculo do algoritmo acessará não apenas esta classe, mas todas as classes mães de Alura, e assim por diante, hierarquicamente:

# Pleno > Alura > Funcionario > Caelum > Funcionario

# Assim, é feita a verificação de qual método será chamado.

# Há duas etapas para a verificação do algoritmo MRO, que exige uma noção de que há uma repetição nesta lista, como no caso de Funcionario. Esta repetição precisa ser removida para que seja possível encontrar o local de onde acessaremos o método que está sendo implementado.

# No nosso caso, em vez de Funcionario, Caelum é que foi acessado, pois a parte da remoção da duplicidade verifica se Funcionario é "uma boa cabeça" (good head). Caso positivo, quer dizer que poderemos mantê-la. Como o primeiro Funcionario não é uma good head, iremos removê-la:

# Pleno > Alura > Caelum > Funcionario

# "Boa cabeça" indica que não há nenhuma outra classe que seja da mesma hierarquia, ou seja, que esteja abaixo de Funcionario (neste caso), e que possa ser utilizada. Já que Caelum também herda de Funcionario, podemos utilizá-la no lugar desta.

# Para tornar isso mais explícito, no Python 3, quando a duplicata é removida, é feita uma verificação da existência de alguma outra classe que herde desta. Por exemplo, será que tem alguma classe que herde de Funcionario na lista? Tem, Caelum. Assim, ela é removida, pois este não é seu lugar, já que existe uma classe em que ela pode caber melhor.

# A herança múltipla, e a forma como lidaremos com ela aqui será mais focada para o uso, para quando trabalhamos com uma classe que pode ser provida como herança, mas não criaremos muitas classes, pois normalmente estes recursos um pouco mais avançados são utilizados na criação de frameworks, ou de um conceito de aplicação a ser utilizada por muitas pessoas.



```

```python
    AttributeError: 'Junior' object has no attribute 'busca_cursos_do_mes'

# É indicado "erro de atributo" pois no Python tudo é atributo, inclusive métodos.
```

```python
# Chamamos estas classes pequenas, cujos objetos nem precisam ser instanciados, de Mixins. Elas são bastante utilizadas em Python no caso de precisarmos compartilhar algum comportamento que não é o mais importante desta classe.

# Neste caso, pode ser interessante utilizarmos este tipo de herança. Mas lembre-se de que o mixin envolve a ideia de não termos que instanciar um objeto desta classe.

# Os mixins são classes herdadas que não precisam ser instanciadas e contém preocupações comuns a diversas classes.
```
