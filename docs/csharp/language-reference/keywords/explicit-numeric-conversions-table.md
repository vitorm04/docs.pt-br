---
title: Tabela de conversões numéricas explícitas (Referência de C#)
ms.date: 07/20/2015
helpviewer_keywords:
- conversions [C#], explicit numeric
- numeric conversions [C#], explicit
- explicit numeric conversion [C#]
- numeric data types [C#]
- types [C#], explicit numeric conversions
- type conversion [C#], explicit numeric
ms.assetid: f3bb9e76-6b92-4df7-bc36-f866c24e1dfd
ms.openlocfilehash: 7363df3e4b2449924222745de409fd68349b93de
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="explicit-numeric-conversions-table-c-reference"></a>Tabela de conversões numéricas explícitas (Referência de C#)
A conversão numérica explícita é usada para converter qualquer tipo numérico para outro tipo numérico para o qual não há conversão implícita, por meio de uma expressão de conversão. A tabela a seguir mostra essas conversões.  
  
 Para obter mais informações sobre conversões, consulte [Conversões e Conversões de Tipo](../../../csharp/programming-guide/types/casting-and-type-conversions.md).  
  
|De|Para|  
|----------|--------|  
|[sbyte](../../../csharp/language-reference/keywords/sbyte.md)|`byte`, `ushort`, `uint`, `ulong` ou `char`|  
|[byte](../../../csharp/language-reference/keywords/byte.md)|`Sbyte` ou `char`|  
|[short](../../../csharp/language-reference/keywords/short.md)|`sbyte`, `byte`, `ushort`, `uint`, `ulong` ou `char`|  
|[ushort](../../../csharp/language-reference/keywords/ushort.md)|`sbyte`, `byte`, `short` ou `char`|  
|[int](../../../csharp/language-reference/keywords/int.md)|`sbyte`, `byte`, `short`, `ushort`, `uint`, `ulong` ou `char`|  
|[uint](../../../csharp/language-reference/keywords/uint.md)|`sbyte`, `byte`, `short`, `ushort`, `int` ou `char`|  
|[long](../../../csharp/language-reference/keywords/long.md)|`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `ulong` ou `char`|  
|[ulong](../../../csharp/language-reference/keywords/ulong.md)|`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long` ou `char`|  
|[char](../../../csharp/language-reference/keywords/char.md)|`sbyte`, `byte` ou `short`|  
|[float](../../../csharp/language-reference/keywords/float.md)|`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char` ou `decimal`|  
|[double](../../../csharp/language-reference/keywords/double.md)|`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, `float` ou `decimal`|  
|[decimal](../../../csharp/language-reference/keywords/decimal.md)|`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, `float` ou `double`|  
  
## <a name="remarks"></a>Comentários  
  
-   A conversão numérica explícita pode causar perda de precisão ou resultados ao lançar exceções.  
  
-   Ao converter um valor `decimal` para um tipo integral, esse valor será arredondado para zero, para o valor integral mais próximo. Se o valor integral resultante estiver fora do intervalo do tipo de destino, uma <xref:System.OverflowException> será lançada.  
  
-   Ao converter de um valor `double` ou `float` para um tipo integral, o valore será truncado. Se o valor integral resultante estiver fora do intervalo do valor de destino, o resultado dependerá do contexto de verificação de estouro. Em um contexto verificado, uma `OverflowException` será lançada, ao passo que em um contexto não verificado, o resultado será um valor não especificado do tipo de destino.  
  
-   Ao converter `double` para `float`, o valor `double` será arredondado para o valor `float` mais próximo. Se o valor `double` for muito pequeno ou muito grande para caber no tipo de destino, o resultado será zero ou infinito.  
  
-   Ao converter `float` ou `double` para `decimal`, o valor de origem será convertido para uma representação `decimal` e arredondado para o número mais próximo após a 28ª casa decimal, se necessário. De acordo com o valor do valor de origem, um dos resultados a seguir podem ocorrer:  
  
    -   Se o valor de origem for muito pequeno para ser representado como um `decimal`, o resultado será zero.  
  
    -   Se o valor de origem for um NaN (não for um número), infinito ou muito grande para ser representado como um `decimal`, uma `OverflowException` será lançada.  
  
-   Ao converter `decimal` para `float` ou `double`, o valor `decimal` será arredondado para o valor `double` ou `float` mais próximo.  
  
 Para obter mais informações sobre conversões explícitas, consulte Explícito na Especificação da Linguagem C#. Para obter mais informações sobre como acessar a especificação, consulte [Especificação da Linguagem C#](../../../csharp/language-reference/language-specification/index.md).  
  
## <a name="see-also"></a>Consulte também  
 [Referência de C#](../../../csharp/language-reference/index.md)  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
 [Transmissões e conversões de tipo](../../../csharp/programming-guide/types/casting-and-type-conversions.md)  
 [Operador ()](../../../csharp/language-reference/operators/invocation-operator.md)  
 [Tabela de tipos integrais](../../../csharp/language-reference/keywords/integral-types-table.md)  
 [Tabela de tipos internos](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [Tabela de conversões numéricas implícitas](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)
