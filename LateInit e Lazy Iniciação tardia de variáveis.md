# LateInit e Lazy: Iniciação tardia de variáveis

Quando precisamos atrasar a inicialização de uma variável em um código em Kotlin, possuimos duas abordagens: LateInit e Lazy. Ambas possuem a mesma idéia e funcionabilidade, mas possuem usos diferentes e vamos dar uma olhada neles.

## LateInit:

Um exemplo de **lateinit** :

```kotlin
private lateinit var variavel: MinhaViewModel
```

Então você deve inicializar a variável em seu código.

```kotlin
variavel = MinhaViewModel()
```

*Caso contrário, você obterá UninitializedPropertyAccessException.*

## Lazy:

Um exemplo de **Lazy** :

```kotlin
private val variavel: MinhaClass by lazy { MinhaClass() } 
```

## 

## Por que temos duas ferramentas diferentes para fazer a mesma coisa? 

Fazendo uma comparação: Quando precisamos apertar e soltar parafusos, temos chaves de fenda e chaves Philips, de acordo com a cabeça do parafuso em questão. ( apesar de às vezes nos deparamos usando uma chave de fenda para apertar um parafuso Philips). 

E é bem assim :smiley: . O Kotlin fornece duas ferramentas e devemos usá-las nas situações apropriadas.

## Quando usar:

A regra básica é simples: 

Usamos **lateinit** com **var**, ou seja, quando precisamos alterar seu valor após sua inicialização. 

Já usamos do **lazy** quando precisamos do mesmo objeto ( sempre o mesmo valor ) toda vez que chamamos a variável. Portanto, **lazy** é usado com **val**.

### Mas não é só isso...  

Apesar de tardia, a inicialização por **lateinit** sempre irá ocorrer e, por menor que seja, há um consumo de recursos. Um uso comum ocorre em casos de fazer *injeção de dependências com Dagger*.

Já o **lazy**, usamos quando ***podemos ou não*** chamar uma variável durante seu fluxo em um programa. Principalmente se o objeto for "pesado", o que levaria tempo e consumo de recursos.

Portanto, devemos pensar com antecedência, o que é melhor para cada situação específica: gastar algum tempo no início ou algum tempo durante a execução.