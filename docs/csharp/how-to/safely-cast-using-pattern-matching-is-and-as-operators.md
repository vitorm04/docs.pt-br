---
title: Como lançar com segurança usando a correspondência de padrões e o é e como operadores
description: Aprenda a usar técnicas de correspondência de padrões para converter variáveis com segurança em um tipo diferente. É possível usar a correspondência de padrões, assim como os operadores is e as para converter tipos com segurança.
ms.date: 09/05/2018
helpviewer_keywords:
- cast operators [C#], as and is operators
- as operator [C#]
- is operator [C#]
ms.openlocfilehash: 60e69a8ef55484e3b04f1674c35a1c5dadfa3b7c
ms.sourcegitcommit: 43cbde34970f5f38f30c43cd63b9c7e2e83717ae
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/11/2020
ms.locfileid: "81121005"
---
# <a name="how-to-safely-cast-by-using-pattern-matching-and-the-is-and-as-operators"></a>Como lançar com segurança usando a correspondência de padrões e o é e como operadores

Como os objetos são polimórficos, é possível que uma variável de tipo de classe base tenha um [tipo](../programming-guide/types/index.md) derivado. Para acessar os métodos de instância do tipo derivado, é necessário [converter](../programming-guide/types/casting-and-type-conversions.md) o valor de volta no tipo derivado. No entanto, uma conversão cria o risco de lançar um <xref:System.InvalidCastException>. O C# fornece instruções de [correspondência de padrões](../pattern-matching.md) que executarão uma conversão condicionalmente somente quando ela tiver êxito. O C# também oferece os operadores [is](../language-reference/operators/type-testing-and-cast.md#is-operator) e [as](../language-reference/operators/type-testing-and-cast.md#as-operator) para testar se um valor é de um determinado tipo.

O exemplo a seguir mostra `is` como usar a declaração de correspondência de padrões:

[!code-csharp[Pattern matching is statement](../../../samples/snippets/csharp/how-to/safelycast/patternmatching/Program.cs#PatternMatchingIs)]

O exemplo anterior demonstra alguns recursos da sintaxe de correspondência de padrões. A `if (a is Mammal m)` declaração combina o teste com uma atribuição de inicialização. A atribuição ocorre apenas quando o teste é bem-sucedido. A variável `m` está somente no escopo na instrução `if` inserida em ela foi atribuída. Não é possível acessar `m` posteriormente no mesmo método. O exemplo anterior também mostra [ `as` ](../language-reference/operators/type-testing-and-cast.md#as-operator) como usar o operador para converter um objeto em um tipo especificado.

Você também pode usar a mesma sintaxe para testar se um [tipo de valor anulado](../language-reference/builtin-types/nullable-value-types.md) tiver um valor, como mostrado no exemplo a seguir:

[!code-csharp[Pattern matching with nullable types](../../../samples/snippets/csharp/how-to/safelycast/nullablepatternmatching/Program.cs#PatternMatchingNullable)]

O exemplo anterior demonstra outros recursos da correspondência de padrões a serem usados com conversões. É possível testar se uma variável tem padrão nulo verificando especificamente o valor `null`. Quando o valor de runtime da variável é `null`, uma instrução `is` que verifica um tipo retorna sempre `false`. A instrução `is` da correspondência de padrões não permite um tipo de valor anulável, como `int?` ou `Nullable<int>`, mas é possível testar qualquer outro tipo de valor. Os `is` padrões do exemplo anterior não se limitam aos tipos de valor anulados. Você também pode usar esses padrões para testar se uma variável `null`de um tipo de referência tem um valor ou é .

A amostra anterior também mostra como você `switch` usa o padrão de tipo em uma declaração onde a variável pode ser um dos muitos tipos diferentes.

Se você quiser testar se uma variável é um determinado tipo, mas não `is` atribuí-la a uma nova variável, você pode usar os operadores e `as` operadores para tipos de referência e tipos de valor anulados. O seguinte código mostra como usar as instruções `is` e `as` que faziam parte da linguagem C# antes que a correspondência de padrões fosse introduzida para testar se uma variável é de um determinado tipo:

[!code-csharp[testing variable types with the is and as statements](../../../samples/snippets/csharp/how-to/safelycast/asandis/Program.cs#IsAndAs)]

Como você pode ver na comparação desse código com o de correspondência de padrões, a sintaxe de correspondência de padrões oferece recursos mais robustos combinando o teste e a atribuição em uma única instrução. Use a sintaxe de correspondência de padrões sempre que possível.

Você pode experimentar essas amostras olhando para o código em nosso [repositório GitHub](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/how-to/safelycast). Ou então, você pode baixar os exemplos [como um arquivo zip](../../../samples/snippets/csharp/how-to/safelycast.zip).
