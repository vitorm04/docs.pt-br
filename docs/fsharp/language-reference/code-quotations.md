---
title: Citações de código (F#)
description: Saiba mais sobre F# citações de código, um recurso de linguagem que permite que você gere e trabalhar com F# expressões de código por meio de programação.
ms.date: 05/16/2016
ms.openlocfilehash: 565fd2a07c617d156f1d43f94a7cb98fc22f1401
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53150766"
---
# <a name="code-quotations"></a>Citações de código

> [!NOTE]
> O link de referência da API levará você até o MSDN.  A referência da API docs.microsoft.com não está completa.

Este tópico descreve *citações de código*, um recurso de linguagem que permite que você gerar e trabalhar com o F# expressões de código por meio de programação. Esse recurso permite gerar uma árvore de sintaxe abstrata que representa F# código. A árvore de sintaxe abstrata pode ser percorrida e processada de acordo com as necessidades do seu aplicativo. Por exemplo, você pode usar a árvore para gerar F# de código ou gerar código em qualquer outra linguagem.

## <a name="quoted-expressions"></a>Expressões entre aspas

Um *entre aspas expressão* é um F# expressão do código que é delimitado, de forma que ele não é compilado como parte do seu programa, mas em vez disso, é compilado em um objeto que representa um F# expressão. Você pode marcar uma expressão entre aspas em uma das duas maneiras: com informações de tipo ou sem informações de tipo. Se você quiser incluir informações de tipo, você usar os símbolos `<@` e `@>` para delimitar a expressão entre aspas. Se você não precisar de informações de tipo, você usar os símbolos `<@@` e `@@>`. O código a seguir mostra as cotações com tipo e sem-tipo.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet501.fs)]

Como percorrer uma árvore de expressão grande é mais rápido se você não incluir informações de tipo. É o tipo resultante de uma expressão entre aspas com os símbolos tipados `Expr<'T>`, e o parâmetro de tipo tem o tipo da expressão, conforme determinado pelo F# algoritmo de inferência de tipo do compilador. Quando você usa citações de código sem informações de tipo, o tipo da expressão entre aspas é o tipo não genérico [Expr](https://msdn.microsoft.com/library/ed6a2caf-69d4-45c2-ab97-e9b3be9bce65). Você pode chamar o [Raw](https://msdn.microsoft.com/library/47fb94f1-e77f-4c68-aabc-2b0ba40d59c2) propriedade em tipado `Expr` classe para obter o sem-tipo `Expr` objeto.

Há uma variedade de métodos estáticos que permitem que você gerar F# expressão por meio de programação em objetos de `Expr` classe sem o uso de expressões entre aspas.

Observe que uma cotação de código deve incluir uma expressão completa. Para um `let` associando, por exemplo, você precisa tanto a definição do nome do associada e uma expressão adicional que usa a associação. Na sintaxe detalhada, isso é uma expressão que segue o `in` palavra-chave. No nível superior em um módulo, essa é a próxima expressão no módulo, mas em uma cotação, seja explicitamente obrigatório.

Portanto, a expressão a seguir não é válida.

```fsharp
// Not valid:
// <@ let f x = x + 1 @>
```

Mas as expressões a seguir são válidas.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet502.fs)]

Para usar citações de código, você deve adicionar uma declaração de importação (usando o `open` palavra-chave) que abre o [quotations](https://msdn.microsoft.com/library/e9ce8a3a-e00c-4190-bad5-cce52ee089b2) namespace.

O F# PowerPack fornece suporte para avaliar e executar F# objetos de expressão.

## <a name="expr-type"></a>Tipo expr

Uma instância das `Expr` tipo representa uma F# expressão. Genérica e não genérica `Expr` tipos estão documentados no F# documentação da biblioteca. Para obter mais informações, consulte [Namespace quotations](https://msdn.microsoft.com/visualfsharpdocs/conceptual/microsoft.fsharp.quotations-namespace-%5bfsharp%5d) e [classe quotations. expr](https://msdn.microsoft.com/visualfsharpdocs/conceptual/quotations.expr-class-%5bfsharp%5d).

## <a name="splicing-operators"></a>Operadores de união

Unindo permite que você combine citações de código literal com expressões que você criou por meio de programação ou de outro cotação de código. O `%` e `%%` operadores permitem que você adicionar um F# objeto de expressão em uma cotação de código. Você usa o `%` operador para inserir um objeto de expressão digitado em uma cotação tipada; use o `%%` operador para inserir um objeto de expressão não tipado em uma cotação não tipada. Ambos os operadores são operadores de prefixo unário. Portanto, se `expr` é uma expressão não tipada do tipo `Expr`, o código a seguir é válido.

```fsharp
<@@ 1 + %%expr @@>
```

E se `expr` é uma cotação tipada do tipo `Expr<int>`, o código a seguir é válido.

```fsharp
<@ 1 + %expr @>
```

## <a name="example"></a>Exemplo

### <a name="description"></a>Descrição

O exemplo a seguir ilustra o uso de citações de código para colocar F# em um objeto de expressão de código e, em seguida, imprima o F# que representa a expressão de código. Uma função `println` é definida que contém uma função recursiva `print` que exibe um F# objeto de expressão (do tipo `Expr`) em um formato amigável. Há vários padrões ativos na [Microsoft.FSharp.Quotations.Patterns](https://msdn.microsoft.com/library/093944a9-c752-403a-8983-5fcd5dbf92a4) e [Microsoft.FSharp.Quotations.DerivedPatterns](https://msdn.microsoft.com/library/d2434a6e-ae7b-4f3d-b567-c162938bc9cd) módulos que podem ser usados para analisar objetos de expressão. Este exemplo não inclui todos os padrões possíveis que podem aparecer em um F# expressão. Qualquer não reconhecida padrão dispara uma correspondência para o padrão de curinga (`_`) e será renderizado usando o `ToString` método, que, no `Expr` digitar, permite que você saiba que o Active Directory padrão para adicionar a sua expressão de correspondência.

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

Você também pode usar os três padrões-Active Directory na [módulo ExprShape](https://msdn.microsoft.com/library/7685150e-2432-4d39-9338-57292eff18de) para percorrer árvores de expressão com menos padrões ativos. Esses padrões ativos podem ser útil quando você deseja percorrer uma árvore, mas você não precisa todas as informações na maioria de nós. Quando você usa esses padrões, qualquer F# expressão corresponde a um dos três seguintes padrões: `ShapeVar` se a expressão for uma variável `ShapeLambda` se a expressão for uma expressão lambda, ou `ShapeCombination` se a expressão for outro número. Se você percorrer uma árvore de expressão usando os padrões de Active Directory como no exemplo de código anterior, você precisa usar vários padrões mais para lidar com todos os possíveis F# tipos de expressão e seu código será mais complexo. Para obter mais informações, consulte [ExprShape.ShapeVar&#124;ShapeLambda&#124;ativo Shapecombination](https://msdn.microsoft.com/visualfsharpdocs/conceptual/exprshape.shapevarhshapelambdahshapecombination-active-pattern-%5bfsharp%5d).

O exemplo de código a seguir pode ser usado como base para travessias mais complexas. Nesse código, uma árvore de expressão é criada para uma expressão que envolve uma chamada de função, `add`. O [SpecificCall](https://msdn.microsoft.com/library/05a77b21-20fe-4b9a-8e07-aa999538198d) padrão ativo é usado para detectar qualquer chamada para `add` na árvore de expressão. Esse padrão do Active Directory atribui os argumentos da chamada para o `exprList` valor. Nesse caso, há apenas dois, portanto, eles são extraídos e a função é chamada recursivamente nos argumentos. Os resultados são inseridos em uma cotação de código que representa uma chamada para `mul` usando o operador de junção (`%%`). O `println` função do exemplo anterior é usada para exibir os resultados.

O código em outras ramificações de padrão ativo apenas gera novamente a mesma árvore de expressão, portanto, a única alteração na expressão resultante é a alteração da `add` para `mul`.

### <a name="code"></a>Código

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet701.fs)]

### <a name="output"></a>Saída

```fsharp
1 + Module1.add(2,Module1.add(3,4))
1 + Module1.mul(2,Module1.mul(3,4))
```

## <a name="see-also"></a>Consulte também

- [Referência da Linguagem F#](index.md)
