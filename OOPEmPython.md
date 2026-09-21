# Herança em Python
## Continuação das aulas de Python orientadas a objeto(OOP)

Existem 4 pilares no conceito Programação Orientada a Objeto:  

1-Abstração  

2-Encapsulamento  

3-Herança  

4-Polimorfismo  

## **HERANÇA (Generalização)**
 É um relacionamento(**do tipo é UM**) entre itens gerais (ancestral/classe base/classe mãe) e tipos mais específicos (descendente/classe derivada/classe filha) desses itens, que herdam atributos e métodos dos níveis superiores. (de forma simples, os itens descendentes ou derivados vão "herdar" atributos e métodos dos itens ancestrais ou superiores, mas também pode criar atributos e métodos novos).Nos diagramas a herança é representada como uma seta para cima.

## Principais Vantagens  

- Reutilização de códigos (classes superiores podem ser utilizadas em outros códigos
- Organização hierárquica
- Facilidade de manutenção
- Extensibilidade (uma alteração em classe superior vai beneficiar as que estiverem inferiores)
- Suporte a polimorfismo

## Na imagem trás um exemplo prático de como seria uma organização de herança, com a parte de cima sendo generalizada e as de baixo sendo especializadas

<img width="1498" height="916" alt="image" src="https://github.com/user-attachments/assets/b47228a4-0939-4588-88c6-049ffe83dac2" />

Tradução da imagem para a linguagem Python:
```
from rich import print, inspect

class Pessoa:
    def __init__(self, nome="", idade=0):
        self.nome = nome
        self.idade = idade

    def fazer_aniversario(self):
        self.idade += 1


class Aluno(Pessoa):                    #aqui a classe "Pessoa" entre parênteses liga os atributos da classe mãe
    def __init__(self, nome, idade, curso, turma):
        super().__init__(nome, idade)           #comando para trazer os atributos solicidades da classe mãe
        self.curso = curso
        self.turma = turma

    def fazer_matricula(self):
        print(f"{self.nome} acabou de fazer matrícula")


class Professor(Pessoa):
    def __init__(self, nome, idade, especialidade, nivel):
        super().__init__(nome, idade)
        self.especialidade = especialidade
        self.nivel = nivel

    def dar_aula(self):
        print(f"Prof. {self.nome} começou a dar aula")


class Funcionario(Pessoa):
    def __init__(self, nome, idade, cargo, setor):
        super().__init__(nome, idade)
        self.cargo = cargo
        self.setor = setor

    def bater_ponto(self):
        print(f"{self.nome} acabou de bater ponto.")


a1 = Aluno("José", 17, "Informática", "T01")
a1.fazer_aniversario()
a1.fazer_matricula()
inspect(a1, methods=True)

p1 = Professor("Samuel", 37, "Biologa", "Mestrado")
p1.fazer_aniversario()
p1.dar_aula()
#inspect(p1, methods=True)

f1 = Funcionario("CLáudia", 27, "Secretária", "Secretaria")
f1.fazer_aniversario()
f1.bater_ponto()
#inspect(f1, methods=True)
```
*Esse exemplo foi usado como exercício (004)*

## **ABSTRAÇÃO**  

A prática de ignorar o irrelevante e se focar estritamente no essencial. Existe abstração de dados, que acontece quando ignoramos informações desnecessárias para o escopo do projeto. Existe abstração de processos, quando não precisamos saber como um método faz seu trabalho, apenas sabe que ele existe pela interface.

## Principais Vantagens  

- Maior legibilidade (é mais fácil entender um código que está mais objetivo)
- Padronização 
- Simplificação
- Segurança

> Classe Abstrata: funciona como uma base para as subclasses se transformarem em objetos(não serve para gerar objetos). Uma classe abstrata *nunca será instanciada*, já que ela será usada apenas como base para as subclasses. Uma classe abstrata pode ter métodos abstratos que deverão obrigatoriamente implementados nas subclasses, mas uma classe abstrata pode ter métodos concretos se eles funcionarem da mesma maneira para todos as subclasses(*DRY)


> Método Abstrato: estão dentro de classes abstratas, obriga a subclasse a ter um método, mas não descreve qual, ou seja, cada subclasse será obrigado a fazer o método, mas poderá ter características próprias. (não possuem linhas de programação). Deve ser escrito entre {} (ex: estudar () {abstract}. Quando criamos um conjunto de métodos abstratos, que estão dentro da classe abstrata, dizemos que estamos criando a interface pública da classe.

<img width="1825" height="901" alt="image" src="https://github.com/user-attachments/assets/41baad93-bf15-4847-8395-23084779c535" />


*DRY - Don't Repeat Yourself

** ABC (Abstract Base Classes) ***  

## ENCAPSULAMENTO ##  

Visa manter a integridade do sistema, protegendo o estado interno do objeto contra interferência externa não regulamentada. Envolvemos a "estrutura" em uma cápsula que deixa exposto apenas o que é necessário.  

## Principais Vantagens  

- Segurança e controle
- Facilidade de manutenção
- Flexibilidade e reutilização
- Redução de efeitos colaterais

Para conseguir realizar essa proteção, precisamos entender:  

1- Visibilidade dos atributos. Existem três tipos de visibilidade para atributos ou métodos na linguagem POO:
- Public >> +   (pode ser editado de qualquer forma)
- Protected >> #  (pode editar dentro da classe e das filhas) 
- Private >> -    (esse só pode ser visto e editado dentro da classe)

*Essa linguagem é utilizada pela programação orientada a objetos, e não é considerado no Python. No Python sobressai o uso do "Consenting Adults", ou seja liberdade com responsabilidade. No python se utiliza as seguinte estruturas:

- Public >> Não tem alteração
- Protected >> _ (adiciona o _ antes do atributo)
- Private >> __ (duplo _ antes do atributo)

<img width="217" height="220" alt="image" src="https://github.com/user-attachments/assets/288aab40-dcbc-47f2-ae0c-3460aa360aff" />

2- Acesso aos dados encapsulados/protegidos. Existem duas maneiras de permitir o acesso aos dados encapsulados:  

- Uso de getters e setter (métodos assessores) - Mais usado em linguagens clássicas
- Uso de decorador @property (cria atributo validável) - Utilizada em linguagens modernas como o Python

  visualização do @property
  
  <img width="329" height="287" alt="image" src="https://github.com/user-attachments/assets/b7974a74-ecff-410d-99a0-c2a99c88dc14" />


EXEMPLO DE USO DOS MÉTODOS ASSESSORES

```
class Avaliacao:

    def __init__(self, nome, disciplina, nota=0):
        self.nome = nome
        self.disciplina = disciplina
        self._nota = nota           #Atributo protegido

    #Métodos assessores
    def get_nota(self):     #Método Getter
        return self._nota

    def set_nota(self, valor):  #Método Setter
        if 0 <= valor <= 10:
            self._nota = valor
        else:
            print("Nota inválida")
```
CHAMADA NO MAIN:

```
from exercicio009 import Avaliacao
from rich import print, inspect

def main():
    av1 = Avaliacao("Pedro", "Matemática", 8.7)
    av1.set_nota(14.4)
    print(f"{av1.nome} tirou {av1.get_nota()} em {av1.disciplina}")
    #inspect(av1, private=True) #Esse comando vai mostrar os dados privados




if __name__ == '__main__':
    main()
```

**Esse exemplo está presente no "exercicio009".

EXEMPLO DE USO DO @PROPERTY

```
class Avaliacao:

    def __init__(self, nome, disciplina, nota=0):
        self.nome = nome
        self.disciplina = disciplina
        self._nota = nota           #Atributo protegido


    #Criando Atributo Validável
    @property
    def nota(self):     #getter
        return self._nota

    @nota.setter 
    def nota(self, valor):      #setter
        if 0 <= valor <= 10:
            self._nota = valor
        else:
            print("Nota inválida")


    @nota.deletter   #Usa uma validação para excluir    
    def nota(self):
        pass
```

CHAMADA DO MAIN

```
from ex_property import Avaliacao
from rich import print, inspect

def main():
    av1 = Avaliacao("Pedro", "Matemática")
    av1.nota = 3.5
    print(f"{av1.nome} tirou {av1.nota} em {av1.disciplina}")
    inspect(av1, private=True) #Esse comando vai mostrar os dados privados




if __name__ == '__main__':
    main()
```


## POLIMORFISMO ##
(O Python visa emitir o Polimorfismo sem a necessidade de Herança)

Propriedade ou estado daquilo que se apresenta e/ou se comporta de várias formas diferentes. "Único nome mas comportamentos diferentes".

##Function Overload

##Operator Overload

- Polimorfismo por Inclusão (Override/Subtyping): É quando um método subscreve um método da mãe(Herança).   -> Aceito pelo Python
- Polimorfismo por Sobrecarga (Ad-Hoc Overloading): Para finalidade de sobrecarga.                          -> Aceito pelo Python
Nesse caso pode ser utilizado para sobrecarga de métodos, onde os métodos possuem os mesmos nomes mas com assinaturas diferentes. 
- Polimorfismo de Coerção (Ad-Hoc Coercion)
- Polimorfismo Paramétrico(Template/Generic)

O Python utiliza os tipos Inclusão, Sobrecarga e "Duck Typing".

<img width="1228" height="692" alt="image" src="https://github.com/user-attachments/assets/e89b8d8b-f19b-41ce-82c6-fdf67689ef87" />
*Métodos mágicos para sobrecarga os operadores em Python.*

