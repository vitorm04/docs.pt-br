---
title: 'Operador ?: (Referência de C#)'
ms.date: 07/20/2015
f1_keywords:
- ?:_CSharpKeyword
- ?_CSharpKeyword
- :_CSharpKeyword
helpviewer_keywords:
- '?: operator [C#]'
- conditional operator (?:) [C#]
ms.assetid: e83a17f1-7500-48ba-8bee-2fbc4c847af4
ms.openlocfilehash: 3e45ff6eaaefa5829c3ed9415abe1a12b7a1d069
ms.sourcegitcommit: 4bca8f7e172fd019ef437a4803bf5895c6bc4781
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2018
ms.locfileid: "50980616"
---
# <a name="-operator-c-reference"></a>Operador ?: (Referência de C#)

O operador condicional (`?:`), comumente conhecido como o operador condicional ternário, retorna um de dois valores dependendo do valor de uma expressão booliana. Esta é a sintaxe do operador condicional.  

```csharp
condition ? first_expression : second_expression;  
```

Começando com C# 7.2, `first_expression` e `second_expression` podem ser [expressões `ref`](https://github.com/dotnet/csharplang/blob/master/proposals/csharp-7.2/conditional-ref.md):

```csharp
ref condition ? ref first_expression : ref second_expression;  
```

O resultado pode ser atribuído a uma variável `ref` ou `ref readonly`, ou a uma variável sem nenhum modificador.

## <a name="remarks"></a>Comentários

A `condition` deve ser avaliada como `true` ou `false`. Se `condition` for `true`, `first_expression` será avaliada e se tornará o resultado. Se `condition` for `false`, `second_expression` será avaliada e se tornará o resultado. Somente uma das duas expressões será avaliada. Isso é particularmente importante para expressões nas quais o resultado é um `ref`, como o seguinte é válido:

```csharp
ref (storage != null) ? ref storage[3] : ref defaultValue;
```

A referência ao `storage` não será avaliada quando `storage` for nulo.

Quando o resultado for um valor, o tipo de `first_expression` e `second_expression` devem ser iguais ou, deve haver uma conversão implícita de um tipo para outro. Quando o resultado é um `ref`, o tipo de `first_expression` e `second_expression` devem ser iguais.

Você pode expressar cálculos que podem, de outra forma, exigir uma construção `if-else` mais concisamente ao usar o operador condicional. Por exemplo, o código a seguir usa primeiro uma instrução `if` e, em seguida, um operador condicional para classificar um inteiro como positivo ou negativo.

```csharp
int input = Convert.ToInt32(Console.ReadLine());  
string classify;  
  
// if-else construction.  
if (input > 0)  
    classify = "positive";  
else  
    classify = "negative";  
  
// ?: conditional operator.  
classify = (input > 0) ? "positive" : "negative";  
```

O operador condicional é associativo direito. A expressão `a ? b : c ? d : e` é avaliada como `a ? b : (c ? d : e)`, não como `(a ? b : c) ? d : e`.  
  
O operador condicional não pode ser sobrecarregado.
  
## <a name="example"></a>Exemplo

O exemplo a seguir mostra o operador condicional, cujo resultado é um valor:

[!code-csharp[csRefOperators?:](~/samples/snippets/csharp/language-reference/operators/ConditionalExamples.cs#ConditionalValue)]

A alternativa a seguir mostra o operador condicional, cujo resultado é uma referência:

[!code-csharp[csRefOperatorsRef?:](~/samples/snippets/csharp/language-reference/operators/ConditionalExamples.cs#ConditionalRef)]

## <a name="see-also"></a>Consulte também

- [Referência de C#](../../../csharp/language-reference/index.md)  
- [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
- [Operadores do C#](../../../csharp/language-reference/operators/index.md)  
- [if-else](../../../csharp/language-reference/keywords/if-else.md)  
- [Operadores ?. e ?[]](../../../csharp/language-reference/operators/null-conditional-operators.md)  
- [Operador ??](../../../csharp/language-reference/operators/null-coalescing-operator.md)
