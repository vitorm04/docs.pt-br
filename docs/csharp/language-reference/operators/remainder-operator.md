---
title: Operador % (Referência de C#)
ms.date: 09/04/2018
f1_keywords:
- '%_CSharpKeyword'
helpviewer_keywords:
- remainder operator [C#]
- '% operator [C#]'
ms.assetid: 3b74f4f9-fd9c-45e7-84fa-c8d71a0dfad7
ms.openlocfilehash: 9cd2f7ad3856feb34667686979c942ecb21887c2
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/16/2018
ms.locfileid: "45645912"
---
# <a name="-operator-c-reference"></a>Operador % (Referência de C#)

O operador de resto `%` calcula o resto após dividir o primeiro operando pelo segundo. Tipos definidos pelo usuário podem [sobrecarregar](../keywords/operator.md) o operador `%`. Quando o `%` está sobrecarregado, o [operador de atribuição de resto](remainder-assignment-operator.md) `%=` também está implicitamente sobrecarregado.

Todos os tipos numéricos são compatíveis com o operador de resto.

## <a name="integer-remainder"></a>Resto inteiro
  
Para os operandos inteiros, o resultado de `a % b` é o valor produzido por `a - (a / b) * b`. O sinal do resto diferente de zero é o mesmo que o do primeiro operando, conforme mostra o seguinte exemplo:

[!code-csharp-interactive[integer remainder](~/samples/snippets/csharp/language-reference/operators/RemainderExamples.cs#1)]

## <a name="floating-point-remainder"></a>Resto de ponto flutuante

Para os operandos [float](../keywords/float.md) e [double](../keywords/double.md), o resultado de `x % y` para o `x` e `y` finitos é o valor `z` tal que

- o sinal de `z`, se diferente de zero, é o mesmo que o sinal de `x`;
- o valor absoluto de `z` é o valor produzido por `|x| - n * |y|` em que `n` é o maior inteiro possível que é menor ou igual a `|x| / |y|` e `|x|` e `|y|` são os valores absolutos de `x` e `y`, respectivamente.

Para obter informações sobre o comportamento do operador `%` no caso de operandos não finitos, consulte a seção [Operador de resto](/dotnet/csharp/language-reference/language-specification/expressions#remainder-operator) da [Especificação da linguagem C#](/dotnet/csharp/language-reference/language-specification/index).

> [!NOTE]
> Esse método de calcular o resto é semelhante ao usado para operandos inteiros, mas é diferente do IEEE 754. Se precisar da operação de resto em conformidade com o IEEE 754, use o método <xref:System.Math.IEEERemainder%2A?displayProperty=nameWithType>.

O exemplo a seguir demonstra o comportamento do operador de resto para os operandos `float` e `double`:

[!code-csharp-interactive[float and double remainder](~/samples/snippets/csharp/language-reference/operators/RemainderExamples.cs#2)]

Observe os erros de arredondamento que podem ser associados aos tipos de ponto flutuante.

Para os operandos [decimais](../keywords/decimal.md), o operador de resto `%` é equivalente ao [operador de resto](<xref:System.Decimal.op_Modulus(System.Decimal,System.Decimal)>) do tipo <xref:System.Decimal?displayProperty=nameWithType>.

## <a name="see-also"></a>Consulte também

- [Referência de C#](../index.md)
- [Guia de Programação em C#](../../programming-guide/index.md)
- [Operadores do C#](index.md)
- <xref:System.Math.IEEERemainder%2A?displayProperty=nameWithType>
- <xref:System.Math.DivRem%2A?displayProperty=nameWithType>
