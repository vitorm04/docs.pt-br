---
title: Como converter com segurança usando a correspondência de padrões e os operadores is e as
description: Aprenda a usar técnicas de correspondência de padrões para converter variáveis com segurança em um tipo diferente. É possível usar a correspondência de padrões, assim como os operadores is e as para converter tipos com segurança.
ms.date: 09/05/2018
helpviewer_keywords:
- cast operators [C#], as and is operators
- as operator [C#]
- is operator [C#]
ms.openlocfilehash: 8d090df1338c535b11a7fd3ec32f6d1cb00b338f
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73739690"
---
# <a name="how-to-safely-cast-by-using-pattern-matching-and-the-is-and-as-operators"></a>Como converter com segurança usando a correspondência de padrões e os operadores is e as

Como os objetos são polimórficos, é possível que uma variável de tipo de classe base tenha um [tipo](../programming-guide/types/index.md) derivado. Para acessar os métodos de instância do tipo derivado, é necessário [converter](../programming-guide/types/casting-and-type-conversions.md) o valor de volta no tipo derivado. No entanto, uma conversão cria o risco de lançar um <xref:System.InvalidCastException>. O C# fornece instruções de [correspondência de padrões](../pattern-matching.md) que executarão uma conversão condicionalmente somente quando ela tiver êxito. O C# também oferece os operadores [is](../language-reference/operators/type-testing-and-cast.md#is-operator) e [as](../language-reference/operators/type-testing-and-cast.md#as-operator) para testar se um valor é de um determinado tipo.

O código a seguir demonstra a instrução `is` da correspondência de padrões. Ele contém métodos que testam um argumento de método para determinar se ele é um argumento de um possível conjunto de tipos derivados:

[!code-csharp[Pattern matching is statement](../../../samples/snippets/csharp/how-to/safelycast/patternmatching/Program.cs#PatternMatchingIs)]

O exemplo anterior demonstra alguns recursos da sintaxe de correspondência de padrões. As instruções `if (a is Mammal m)` e `if (o is Mammal m)` combinam o teste com uma atribuição de inicialização. A atribuição ocorre apenas quando o teste é bem-sucedido. A variável `m` está somente no escopo na instrução `if` inserida em ela foi atribuída. Não é possível acessar `m` posteriormente no mesmo método. Experimente isso na janela interativa.

Você também pode usar a mesma sintaxe para testar se um [tipo de valor anulável](../language-reference/builtin-types/nullable-value-types.md) tem um valor, conforme mostrado no código de exemplo a seguir:

[!code-csharp[Pattern matching with nullable types](../../../samples/snippets/csharp/how-to/safelycast/nullablepatternmatching/Program.cs#PatternMatchingNullable)]

O exemplo anterior demonstra outros recursos da correspondência de padrões a serem usados com conversões. É possível testar se uma variável tem padrão nulo verificando especificamente o valor `null`. Quando o valor de runtime da variável é `null`, uma instrução `is` que verifica um tipo retorna sempre `false`. A instrução `is` da correspondência de padrões não permite um tipo de valor anulável, como `int?` ou `Nullable<int>`, mas é possível testar qualquer outro tipo de valor. Os padrões de `is` do exemplo anterior não estão limitados aos tipos de valor anulável. Você também pode usar esses padrões para testar se uma variável de um tipo de referência tem um valor ou é `null`.

O exemplo anterior também mostra como você usa a expressão `is` de correspondência de padrões em uma instrução `switch` em que a variável pode ser um dos muitos tipos diferentes.

Se desejar testar se uma variável é um determinado tipo, mas não a atribuir à nova variável, será possível usar os operadores `is` e `as` para tipos de referência e tipos que permitem valor nulo. O seguinte código mostra como usar as instruções `is` e `as` que faziam parte da linguagem C# antes que a correspondência de padrões fosse introduzida para testar se uma variável é de um determinado tipo:

[!code-csharp[testing variable types with the is and as statements](../../../samples/snippets/csharp/how-to/safelycast/asandis/Program.cs#IsAndAs)]

Como você pode ver na comparação desse código com o de correspondência de padrões, a sintaxe de correspondência de padrões oferece recursos mais robustos combinando o teste e a atribuição em uma única instrução. Use a sintaxe de correspondência de padrões sempre que possível.

Você pode experimentar estes exemplos examinando o código em nosso [repositório GitHub](https://github.com/dotnet/samples/tree/master/snippets/csharp/how-to/safelycast). Ou então, você pode baixar os exemplos [como um arquivo zip](https://github.com/dotnet/samples/raw/master/snippets/csharp/how-to/safelycast.zip).
