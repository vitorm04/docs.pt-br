---
title: Introdução à programação funcional em F#
description: Conheça os conceitos básicos da programação funcional em F#.
ms.date: 10/29/2018
ms.openlocfilehash: 84022e58c0f17b9e9875402c653c31e494e940da
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61772782"
---
# <a name="introduction-to-functional-programming-in-f"></a>Introdução à programação funcional em F\#

Programação funcional é um estilo de programação que enfatiza o uso de funções e dados imutáveis. Programação funcional tipada é quando a programação funcional é combinada com tipos estáticos, como com F#. Em geral, os conceitos a seguir são enfatizados na programação funcional:

* Funções como as principais construções em que você usar
* Expressões em vez de instruções
* Valores imutáveis sobre as variáveis
* Programação declarativa sobre programação imperativa

Em toda esta série, você irá explorar os conceitos e padrões na programação funcional usando F#. Ao longo do caminho, você aprenderá sobre alguns F# muito.

## <a name="terminology"></a>Terminologia

Programação funcional, como outras paradigmas de programação, vem com um vocabulário que, eventualmente, você precisará aprender. Aqui estão alguns termos comuns que você verá que o tempo todo:

* **Função** -uma função é uma construção que produzirá uma saída quando recebe uma entrada. Mais formalmente, ele _mapeia_ um item de um conjunto para outro conjunto. Essa formalidade é elevada na concretas de várias maneiras, especialmente ao usar funções que operam em coleções de dados. Ele é o conceito mais básico (e importante) na programação funcional. 
* **Expressão** -uma expressão é uma construção de código que produz um valor. No F#, esse valor deve ser associado ou explicitamente ignorado. Uma expressão pode ser facilmente substituída por uma chamada de função.
* **Pureza** -pureza é uma propriedade de uma função de modo que seu valor de retorno é sempre o mesmo para os mesmos argumentos, e que sua avaliação não tem efeitos colaterais. Uma função pura depende inteiramente em seus argumentos.
* **Transparência referencial** -transparência referencial é uma propriedade de expressões, de modo que eles podem ser substituídos por suas saídas sem afetar o comportamento do programa.
* **Imutabilidade** -significa que a imutabilidade que um valor não pode ser alterada no local. Isso é diferente das variáveis, que podem ser alterado em vigor.

## <a name="examples"></a>Exemplos

Os exemplos a seguir demonstram esses conceitos básicos.

### <a name="functions"></a>Funções

Construção mais fundamental e comuns na programação funcional é a função. Aqui está uma função simples que adiciona 1 em um inteiro:

```fsharp
let addOne x = x + 1
```

Sua assinatura do tipo é da seguinte maneira:

```fsharp
val addOne: x:int -> int
```

A assinatura pode ser lido como, "`addOne` aceita um `int` denominado `x` e produzirá um `int`". Mais formalmente, `addOne` está _mapeamento_ um valor do conjunto de números inteiros para o conjunto de números inteiros. O `->` token significa que esse mapeamento. No F#, você pode examinar a assinatura de função para ter uma ideia para o que ele faz normalmente.

Então, por que é a assinatura importante? Na programação funcional tipada, a implementação de uma função geralmente é menos importante do que a assinatura de tipo real! O fato de que `addOne` adiciona o valor 1 para um número inteiro é interessante em tempo de execução, mas quando você estiver construindo um programa, o fato de que ele aceita e retorna um `int` é o que informa como você realmente usar essa função. Além disso, depois que você usa essa função corretamente (com respeito à sua assinatura do tipo), diagnóstico de problemas pode ser feito somente dentro do corpo do `addOne` função. Esse é o motivo por trás da programação funcional tipada.

### <a name="expressions"></a>Expressões

As expressões são construções que avaliam um valor. Em contraste com as instruções que executam uma ação, expressões podem ser consideradas executando uma ação que devolve um valor. Expressões quase sempre são usadas em favor de instruções na programação funcional.

Considere a função anterior, `addOne`. O corpo da `addOne` é uma expressão:

```fsharp
// 'x + 1' is an expression!
let addOne x = x + 1
```

É o resultado dessa expressão que define o tipo de resultado de `addOne` função. Por exemplo, a expressão que compõe essa função pode ser alterada para ser um tipo diferente, como um `string`:

```fsharp
let addOne x = x.ToString() + "1"
```

A assinatura da função é agora:

```fsharp
val addOne: x:'a -> string
```

Desde qualquer tipo em F# pode ter `ToString()` chamado nela, o tipo de `x` foi feita genérico (chamados [generalização automática](../language-reference/generics/automatic-generalization.md)), e o tipo resultante é um `string`.

Expressões não são apenas os corpos de funções. Você pode ter expressões que produzem um valor que você pode usar em outro lugar. Um comum que um é `if`:

```fsharp
// Checks if 'x' is odd by using the mod operator
let isOdd x = x % 2 <> 0

let addOneIfOdd input =
    let result =
        if isOdd input then
            input + 1
        else
            input

    result
```

O `if` expressão produzir um valor chamado `result`. Observe que você poderia omitir `result` totalmente, tornando o `if` o corpo da expressão do `addOneIfOdd` função. O mais importante lembrar sobre expressões é que eles produzem um valor.

Há um tipo especial, `unit`, que é usado quando não há nada para retornar. Por exemplo, considere essa função simples:

```fsharp
let printString (str: string) =
    printfn "String is: %s" str
```

A assinatura tem esta aparência:

```fsharp
val printString: str:string -> unit
```

O `unit` tipo indica que não há nenhum valor real que está sendo retornado. Isso é útil quando você tem uma rotina que deve "trabalho" Apesar de não ter nenhum valor a ser retornado como resultado desse trabalho.

Isso é um nítido contraste com programação imperativa, em que o equivalente `if` construção é uma instrução e produzir valores geralmente é feito com a mutação de variáveis. Por exemplo, em C#, o código pode ser escrito da seguinte forma:

```csharp
bool IsOdd(int x) => x % 2 != 0;

int AddOneIfOdd(int input)
{
    var result = input;

    if (IsOdd(input))
    {
        result = input + 1;
    }

    return result;
}
```

Vale a pena observar que C# e outras linguagens de estilo C têm suporte para o [expressão ternária](../../csharp/language-reference/operators/conditional-operator.md), que permite a programação condicional baseada em expressão.

Na programação funcional, é raro para modificar os valores com instruções. Embora algumas linguagens funcionais ofereçam suporte a instruções e a mutação, não é comum usar esses conceitos em programação funcional.

### <a name="pure-functions"></a>Funções puras

Como mencionadas anteriormente, puras funções são funções que:

* Sempre avalie para o mesmo valor para a mesma entrada.
* Não têm efeitos colaterais.

É útil pensar em funções matemáticas neste contexto. Em matemática, funções dependem apenas em seus argumentos e não tem nenhum efeito colateral. Na função matemática `f(x) = x + 1`, o valor da `f(x)` depende apenas do valor de `x`. Funções puras na programação funcional são da mesma maneira.

Ao escrever uma função pura, a função deve depender apenas de seus argumentos e não realiza qualquer ação que resulta em um efeito colateral.

Aqui está um exemplo de uma função não pura porque ele depende do estado mutável, global:

```fsharp
let mutable value = 1

let addOneToValue x = x + value
```

O `addOneToValue` função é claramente impuras, porque `value` poderia ser alterado a qualquer momento para ter um valor diferente de 1. Esse padrão de acordo com um valor global é a serem evitados na programação funcional.

Aqui está outro exemplo de uma função não pura, pois ele executa um efeito colateral:

```fsharp
let addOneToValue x = 
    printfn "x is %d" x
    x + 1
```

Embora essa função não depende de um valor global, ele grava o valor de `x` para a saída do programa. Embora não haja nada errado com isso, isso significa que a função não é pura. Se outra parte do seu programa depende de algo externo ao programa, como o buffer de saída, em seguida, chamar essa função pode afetar essa outra parte do seu programa.

Removendo o `printfn` instrução faz com que a função pura:

```fsharp
let addOneToValue x = x + 1
```

Embora essa função não é inerentemente _melhor_ que a versão anterior com o `printfn` instrução, ele garante que tudo o que essa função faz é retornar um valor. Chamar essa função a qualquer número de vezes que produz o mesmo resultado: ele produz apenas um valor. A capacidade de previsão fornecida por pureza é algo que muitos programadores funcionais se esforçam para.

### <a name="immutability"></a>Imutabilidade

Por fim, um dos conceitos fundamentais da programação funcional tipada é imutabilidade. No F#, todos os valores são imutáveis por padrão. Isso significa que eles não podem ser mudados para a posição, a menos que você explicitamente marcá-los como mutáveis.

Na prática, trabalhar com valores imutáveis significa que você alterar sua abordagem à programação de "Preciso alterar algo", para "preciso gerar um novo valor".

Por exemplo, adicionando 1 como um valor significa que a produzir um novo valor, não a mutação existente:

```fsharp
let value = 1
let secondValue = value + 1
```

No F#, o código a seguir faz **não** modifica o `value` função; em vez disso, ele executa uma verificação de igualdade:

```fsharp
let value = 1
value = value + 1 // Produces a 'bool' value!
```

Algumas linguagens de programação funcionais não suportam mutação. No F#, há suporte, mas não é o comportamento padrão para valores.

Estende esse conceito ainda mais para estruturas de dados. Na programação funcional, estruturas de dados imutáveis, como conjuntos (e muito mais) têm uma implementação diferente que você pode inicialmente esperam. Conceitualmente, algo assim que adicionar um item a um conjunto não altera o conjunto, ele produz um _novo_ definido com o valor agregado. Nos bastidores, isso geralmente é feito por uma estrutura de dados diferentes que permite que um valor de controle com eficiência para que a representação apropriada dos dados pode ser fornecida como resultado.

Esse estilo de trabalhar com valores e estruturas de dados é crítico, pois isso força você a tratar de qualquer operação que modifique algo como se ele cria uma nova versão dessa coisa. Isso permite coisas como comparação e igualdade para ser consistente em seus programas.

## <a name="next-steps"></a>Próximas etapas

A próxima seção abordará minuciosamente funções, explorando maneiras diferentes, você pode usá-los na programação funcional.

[Funções de primeira classe](first-class-functions.md) explora funções profundamente, mostrando como você pode usá-los em vários contextos.

## <a name="further-reading"></a>Leitura adicional

O [pensar funcionalmente](https://fsharpforfunandprofit.com/posts/thinking-functionally-intro/) série é outro excelente recurso para saber mais sobre programação funcional com F#. Ele abrange conceitos básicos da programação funcional de forma pragmática e fácil de ler, usando F# recursos para ilustrar os conceitos.
