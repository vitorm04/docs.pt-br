---
title: Citações de código (F#)
description: 'Saiba mais sobre F # citações de código, um recurso de linguagem que permite que você gere e trabalhar programaticamente com expressões de código F #.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: cfa2e4b9a4ad1776315dfa8ea82fb8fc3f13a552
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2018
---
# <a name="code-quotations"></a>Citações de código

> [!NOTE]
O link de referência da API levará você até o MSDN.  A referência da API docs.microsoft.com não está completa.

Este tópico descreve *citações de código*, um recurso de linguagem que permite que você gere e trabalhar programaticamente com expressões de código F #. Esse recurso permite gerar uma árvore de sintaxe abstrata que representa o código F #. A árvore de sintaxe abstrata pode ser percorrida e processada de acordo com as necessidades do seu aplicativo. Por exemplo, você pode usar a árvore para gerar código F # ou gerar código em alguma outra linguagem.


## <a name="quoted-expressions"></a>Expressões entre aspas
Um *entre aspas expressão* é uma expressão que é delimitada, de forma que ele não é compilado como parte do seu programa, mas em vez disso, é compilado em um objeto que representa uma expressão de F # em seu código F #. Você pode marcar uma expressão entre aspas em uma das duas maneiras: com informações de tipo ou sem informações de tipo. Se você quiser incluir informações de tipo, você usar os símbolos `<@` e `@>` para delimitar a expressão entre aspas. Se você não precisar de informações de tipo, você usar os símbolos `<@@` e `@@>`. O código a seguir mostra tipadas e aspas.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet501.fs)]

Como percorrer uma árvore de expressão grande é mais rápido se você não incluir informações de tipo. O tipo resultante de uma expressão entre aspas com os símbolos digitados é `Expr<'T>`, e o parâmetro de tipo tem o tipo da expressão, conforme determinado pelo algoritmo de inferência de tipo do compilador F #. Quando você usa citações de código sem informações de tipo, o tipo da expressão entre aspas é o tipo não genérico [Expr](https://msdn.microsoft.com/library/ed6a2caf-69d4-45c2-ab97-e9b3be9bce65). Você pode chamar o [Raw](https://msdn.microsoft.com/library/47fb94f1-e77f-4c68-aabc-2b0ba40d59c2) propriedade tipado `Expr` classe para obter o não tipado `Expr` objeto.

Há uma variedade de métodos estáticos que permitem que você gerar F # objetos da expressão programaticamente o `Expr` classe sem o uso de expressões entre aspas.

Observe que uma cotação de código deve incluir uma expressão completa. Para um `let` de associação, por exemplo, você precisa a definição do nome do associado e uma expressão adicional que usa a associação. Na sintaxe estendida, esta é uma expressão que segue o `in` palavra-chave. No nível superior em um módulo, essa é a próxima expressão no módulo, mas uma cotação, é necessário explicitamente.

Portanto, a expressão a seguir não é válida.

```fsharp
// Not valid:
// <@ let f x = x + 1 @>
```

Mas as seguintes expressões são válidas.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet502.fs)]

Para usar citações de código, você deve adicionar uma declaração de importação (usando o `open` palavra-chave) que abre o [quotations](https://msdn.microsoft.com/library/e9ce8a3a-e00c-4190-bad5-cce52ee089b2) namespace.

O F # PowerPack fornece suporte para avaliar e execução de objetos de expressão do F #.


## <a name="expr-type"></a>Tipo expr
Uma instância das `Expr` tipo representa uma expressão de F #. Genérica e não genérica `Expr` tipos estão documentados na documentação da biblioteca F #. Para obter mais informações, consulte [quotations Namespace](https://msdn.microsoft.com/visualfsharpdocs/conceptual/microsoft.fsharp.quotations-namespace-%5bfsharp%5d) e [classe quotations. expr](https://msdn.microsoft.com/visualfsharpdocs/conceptual/quotations.expr-class-%5bfsharp%5d).


## <a name="splicing-operators"></a>Operadores de união
União permite que você combine citações de código literal com expressões que você criou por meio de programação ou de outra cotação de código. O `%` e `%%` operadores permitem que você adicionar um objeto de expressão do F # em uma cotação de código. Você usa o `%` operador para inserir um objeto do tipo de expressão em uma cotação digitada; você usar o `%%` operador para inserir um objeto de expressão não tipado em uma cotação não tipada. Ambos os operadores são os operadores unários prefixo. Portanto, se `expr` é uma expressão não tipada do tipo `Expr`, o código a seguir é válido.

```fsharp
<@@ 1 + %%expr @@>
```

E se `expr` é uma cotação digitada do tipo `Expr<int>`, o código a seguir é válido.

```fsharp
<@ 1 + %expr @>
```

## <a name="example"></a>Exemplo

### <a name="description"></a>Descrição
O exemplo a seguir ilustra o uso de aspas de código para colocar o código F # em um objeto de expressão e, em seguida, imprima o código F # que representa a expressão. Uma função `println` é definida que contém uma função recursiva `print` que exibe um objeto de expressão do F # (do tipo `Expr`) em um formato amigável. Há vários padrões ativos no [Microsoft.FSharp.Quotations.Patterns](https://msdn.microsoft.com/library/093944a9-c752-403a-8983-5fcd5dbf92a4) e [Microsoft.FSharp.Quotations.DerivedPatterns](https://msdn.microsoft.com/library/d2434a6e-ae7b-4f3d-b567-c162938bc9cd) módulos que podem ser usados para analisar objetos de expressão. Este exemplo não inclui todos os padrões possíveis que podem aparecer em uma expressão do F #. Qualquer não reconhecida padrão dispara uma correspondência de padrão de curinga (`_`) e é processado usando o `ToString` método, que, no `Expr` tipo permite que você saiba o padrão ativo para adicionar a sua expressão de correspondência.


### <a name="code"></a>Código
[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet601.fs)]
    
### <a name="output"></a>Saída

```fsharp
fun (x:System.Int32) -> x + 1
a + 1
let f = fun (x:System.Int32) -> x + 10 in f 10
```

## <a name="example"></a>Exemplo

### <a name="description"></a>Descrição
Você também pode usar os três padrões active no [módulo ExprShape](https://msdn.microsoft.com/library/7685150e-2432-4d39-9338-57292eff18de) atravessar árvores de expressão com menos padrões ativos. Esses padrões ativos podem ser útil quando você quiser atravessar uma árvore, mas você não precisa de todas as informações na maioria de nós. Quando você usa esses padrões, qualquer expressão F # corresponde a um dos seguintes padrões de três: `ShapeVar` se a expressão for uma variável, `ShapeLambda` se a expressão for uma expressão lambda, ou `ShapeCombination` se a expressão for diferente. Se você percorrer uma árvore de expressão usando os padrões ativos do exemplo de código anterior, você precisa usar vários padrões mais para lidar com todas as possíveis F # tipos de expressão e seu código será mais complexo. Para obter mais informações, consulte [ExprShape.ShapeVar&#124;ShapeLambda&#124;ativo Shapecombination](https://msdn.microsoft.com/visualfsharpdocs/conceptual/exprshape.shapevarhshapelambdahshapecombination-active-pattern-%5bfsharp%5d).

O exemplo de código a seguir pode ser usado como base para traversais mais complexas. Nesse código, uma árvore de expressão é criada para uma expressão que envolve uma chamada de função `add`. O [SpecificCall](https://msdn.microsoft.com/library/05a77b21-20fe-4b9a-8e07-aa999538198d) padrão ativo é usado para detectar qualquer chamada para `add` na árvore de expressão. Esse padrão ativo atribui os argumentos da chamada para o `exprList` valor. Nesse caso, há apenas dois, para que eles retirada e a função é chamada recursivamente sobre os argumentos. Os resultados são inseridos em uma cotação de código que representa uma chamada para `mul` usando o operador de união pré-fixo (`%%`). O `println` função do exemplo anterior é usada para exibir os resultados.

O código em outras ramificações de padrão ativo apenas gera novamente a mesma árvore de expressão, portanto, a única alteração na expressão resultante é a alteração do `add` para `mul`.


### <a name="code"></a>Código
[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet701.fs)]
    
### <a name="output"></a>Saída

```fsharp
1 + Module1.add(2,Module1.add(3,4))
1 + Module1.mul(2,Module1.mul(3,4))
```

## <a name="see-also"></a>Consulte também
[Referência da Linguagem F#](index.md)

