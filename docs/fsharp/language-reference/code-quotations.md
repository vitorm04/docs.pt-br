---
title: Citações de código
description: Saiba mais F# sobre as cotações de código, um recurso de linguagem que permite gerar e trabalhar F# com expressões de código programaticamente.
ms.date: 05/16/2016
ms.openlocfilehash: c6ec0078c685a6452f49edd289b01491dd62e3db
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630423"
---
# <a name="code-quotations"></a>Citações de código

> [!NOTE]
> O link de referência da API levará você até o MSDN.  A referência da API docs.microsoft.com não está completa.

Este tópico descreve as *Cotações de código*, um recurso de linguagem que permite gerar e trabalhar com F# expressões de código programaticamente. Esse recurso permite gerar uma árvore de sintaxe abstrata que representa F# o código. A árvore de sintaxe abstrata pode ser atravessada e processada de acordo com as necessidades do seu aplicativo. Por exemplo, você pode usar a árvore para gerar F# código ou gerar código em alguma outra linguagem.

## <a name="quoted-expressions"></a>Expressões entre aspas

Uma *expressão entre aspas* é F# uma expressão em seu código delimitada de forma que ela não seja compilada como parte do seu programa, mas em vez disso, é compilada em um objeto que F# representa uma expressão. Você pode marcar uma expressão entre aspas de uma das duas maneiras: com informações de tipo ou sem informações de tipo. Se você quiser incluir informações de tipo, use os símbolos `<@` e `@>` para delimitar a expressão entre aspas. Se você não precisar de informações de tipo, use os símbolos `<@@` e `@@>`. O código a seguir mostra as cotações digitadas e não tipadas.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet501.fs)]

Percorrer uma árvore de expressão grande é mais rápido se você não incluir informações de tipo. O tipo resultante de uma expressão citada com os símbolos tipados é `Expr<'T>`, em que o parâmetro de tipo tem o tipo da expressão conforme determinado pelo algoritmo de inferência de tipo do F# compilador. Quando você usa Cotações de código sem informações de tipo, o tipo da expressão entre aspas é a [expr](https://msdn.microsoft.com/library/ed6a2caf-69d4-45c2-ab97-e9b3be9bce65)de tipo não genérico. Você pode chamar a propriedade [RAW](https://msdn.microsoft.com/library/47fb94f1-e77f-4c68-aabc-2b0ba40d59c2) na classe tipada `Expr` para obter `Expr` o objeto não tipado.

Há uma variedade de métodos estáticos que permitem gerar F# objetos de expressão programaticamente na `Expr` classe sem usar expressões entre aspas.

Observe que uma cotação de código deve incluir uma expressão completa. Para uma `let` associação, por exemplo, você precisa da definição do nome associado e de uma expressão adicional que usa a associação. Na sintaxe detalhada, essa é uma expressão que segue a `in` palavra-chave. No nível superior de um módulo, essa é apenas a próxima expressão no módulo, mas em uma cotação, ela é explicitamente necessária.

Portanto, a expressão a seguir não é válida.

```fsharp
// Not valid:
// <@ let f x = x + 1 @>
```

Mas as expressões a seguir são válidas.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet502.fs)]

Para avaliar F# as cotações, você deve usar o [ F# avaliador de aspas](https://github.com/fsprojects/FSharp.Quotations.Evaluator). Ele fornece suporte para avaliar e executar F# objetos de expressão.

## <a name="expr-type"></a>Tipo de expr

Uma instância do `Expr` tipo representa uma F# expressão. Os tipos genérico e não genérico `Expr` são documentados na documentação da F# biblioteca. Para obter mais informações, consulte a classe [Microsoft. FSharp. Requotas namespace](https://msdn.microsoft.com/visualfsharpdocs/conceptual/microsoft.fsharp.quotations-namespace-%5bfsharp%5d) e requotas [. expr](https://msdn.microsoft.com/visualfsharpdocs/conceptual/quotations.expr-class-%5bfsharp%5d).

## <a name="splicing-operators"></a>Operadores da União

O da União permite combinar Cotações de código literais com expressões que você criou programaticamente ou de outra cotação de código. Os `%` operadores `%%` e permitem que você adicione um F# objeto de expressão a uma cotação de código. Você usa o `%` operador para inserir um objeto de expressão com tipo em uma cotação tipada `%%` ; você usa o operador para inserir um objeto de expressão não tipado em uma cotação não tipada. Ambos os operadores são operadores de prefixo unários. Portanto, `expr` se for uma expressão não tipada do `Expr`tipo, o código a seguir será válido.

```fsharp
<@@ 1 + %%expr @@>
```

E se `expr` for uma citação tipada do `Expr<int>`tipo, o código a seguir será válido.

```fsharp
<@ 1 + %expr @>
```

## <a name="example"></a>Exemplo

### <a name="description"></a>Descrição

O exemplo a seguir ilustra o uso de aspas de código para F# colocar o código em um objeto de expressão e F# , em seguida, imprimir o código que representa a expressão. Uma função `println` é definida que contém uma função `print` recursiva que exibe um F# objeto de expressão (do `Expr`tipo) em um formato amigável. Há vários padrões ativos nos módulos [Microsoft. FSharp. Requotas. Patterns](https://msdn.microsoft.com/library/093944a9-c752-403a-8983-5fcd5dbf92a4) e [Microsoft. FSharp. requotars. DerivedPatterns](https://msdn.microsoft.com/library/d2434a6e-ae7b-4f3d-b567-c162938bc9cd) que podem ser usados para analisar objetos de expressão. Este exemplo não inclui todos os padrões possíveis que podem aparecer em uma F# expressão. Qualquer padrão não reconhecido dispara uma correspondência ao padrão curinga (`_`) e é renderizado usando o `ToString` método `Expr` , que, no tipo, permite que você saiba o padrão ativo a ser adicionado à expressão de correspondência.

### <a name="code"></a>Código

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet601.fs)]

### <a name="output"></a>Saída

```fsharp
fun (x:System.Int32) -> x + 1
a + 1
let f = fun (x:System.Int32) -> x + 10 in f 10
```

## <a name="example"></a>Exemplo

### <a name="description"></a>Descrição

Você também pode usar os três padrões ativos no [módulo ExprShape](https://msdn.microsoft.com/library/7685150e-2432-4d39-9338-57292eff18de) para atravessar árvores de expressão com menos padrões ativos. Esses padrões ativos podem ser úteis quando você deseja percorrer uma árvore, mas não precisa de todas as informações na maioria dos nós. Quando você usa esses padrões, qualquer F# expressão corresponde a um dos três padrões a seguir `ShapeVar` : se a expressão for uma variável `ShapeLambda` , se a expressão for uma expressão lambda ou `ShapeCombination` se a expressão for outra coisa. Se você percorrer uma árvore de expressão usando os padrões ativos como no exemplo de código anterior, precisará usar muitos outros padrões para lidar com todos os tipos F# de expressão possíveis e seu código será mais complexo. Para obter mais informações, consulte [ExprShape.&#124;ShapeVar&#124;ShapeLambda ShapeCombination active Pattern](https://msdn.microsoft.com/visualfsharpdocs/conceptual/exprshape.shapevarhshapelambdahshapecombination-active-pattern-%5bfsharp%5d).

O exemplo de código a seguir pode ser usado como base para passagens mais complexas. Nesse código, uma árvore de expressão é criada para uma expressão que envolve uma chamada de função `add`,. O padrão [SpecificCall](https://msdn.microsoft.com/library/05a77b21-20fe-4b9a-8e07-aa999538198d) ativo é usado para detectar qualquer chamada para `add` na árvore de expressão. Esse padrão ativo atribui os argumentos da chamada ao `exprList` valor. Nesse caso, há apenas dois, portanto, eles são retirados e a função é chamada recursivamente nos argumentos. Os resultados são inseridos em uma cotação de código que representa `mul` uma chamada para usando o operador de`%%`União (). A `println` função do exemplo anterior é usada para exibir os resultados.

O código em outras ramificações de padrão ativo apenas gera a mesma árvore de expressão, portanto, a única alteração na expressão resultante é a alteração de `add` para `mul`.

### <a name="code"></a>Código

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet701.fs)]

### <a name="output"></a>Saída

```fsharp
1 + Module1.add(2,Module1.add(3,4))
1 + Module1.mul(2,Module1.mul(3,4))
```

## <a name="see-also"></a>Consulte também

- [Referência da Linguagem F#](index.md)
