---
title: Tabela de conversões numéricas explícitas – Referência de C#
ms.custom: seodec18
ms.date: 09/06/2018
helpviewer_keywords:
- conversions [C#], explicit numeric
- numeric conversions [C#], explicit
- explicit numeric conversion [C#]
- numeric data types [C#]
- types [C#], explicit numeric conversions
- type conversion [C#], explicit numeric
ms.assetid: f3bb9e76-6b92-4df7-bc36-f866c24e1dfd
ms.openlocfilehash: 22482a8f55cdb53f9826fbcc850992e20b7a8feb
ms.sourcegitcommit: a970268118ea61ce14207e0916e17243546a491f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/21/2019
ms.locfileid: "67306616"
---
# <a name="explicit-numeric-conversions-table-c-reference"></a>Tabela de conversões numéricas explícitas (Referência de C#)

A tabela a seguir mostra as conversões explícitas predefinidas entre os tipos numéricos do .NET para os quais não há nenhuma [conversão implícita](implicit-numeric-conversions-table.md).

|De|Para|  
|----------|--------|  
|[sbyte](sbyte.md)|`byte`, `ushort`, `uint`, `ulong` ou `char`|  
|[byte](byte.md)|`sbyte` ou `char`|  
|[short](short.md)|`sbyte`, `byte`, `ushort`, `uint`, `ulong` ou `char`|  
|[ushort](ushort.md)|`sbyte`, `byte`, `short` ou `char`|  
|[int](int.md)|`sbyte`, `byte`, `short`, `ushort`, `uint`, `ulong` ou `char`|  
|[uint](uint.md)|`sbyte`, `byte`, `short`, `ushort`, `int` ou `char`|  
|[long](long.md)|`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `ulong` ou `char`|  
|[ulong](ulong.md)|`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long` ou `char`|  
|[char](char.md)|`sbyte`, `byte` ou `short`|  
|[float](float.md)|`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char` ou `decimal`|  
|[double](double.md)|`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, `float` ou `decimal`|  
|[decimal](decimal.md)|`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, `float` ou `double`|  
  
## <a name="remarks"></a>Comentários  
  
- A conversão numérica explícita pode causar perda de precisão ou o lançamento de uma exceção, normalmente um <xref:System.OverflowException>.  

- Quando você converte um valor de um tipo integral em outro tipo integral, o resultado depende do [contexto de verificação](checked-and-unchecked.md) do estouro. Em um contexto verificado, a conversão terá êxito se o valor de origem estiver dentro do intervalo do tipo de destino. Caso contrário, um <xref:System.OverflowException> será gerado. Em um contexto não verificado, a conversão sempre terá êxito e procederá da seguinte maneira:

  - Se o tipo de origem for maior do que o tipo de destino, então o valor de origem será truncado descartando seus bits "extra" mais significativos. O resultado é então tratado como um valor do tipo de destino.

  - Se o tipo de origem for menor do que o tipo de destino, então o valor de origem será estendido por sinal ou por zero para que tenha o mesmo tamanho que o tipo de destino. A extensão por sinal será usada se o tipo de origem tiver sinal; a extensão por zero será usada se o tipo de origem não tiver sinal. O resultado é então tratado como um valor do tipo de destino.

  - Se o tipo de origem tiver o mesmo tamanho que o tipo de destino, então o valor de origem será tratado como um valor do tipo de destino.
  
- Ao converter um valor `decimal` para um tipo integral, esse valor será arredondado para zero, para o valor integral mais próximo. Se o valor integral resultante estiver fora do intervalo do tipo de destino, uma <xref:System.OverflowException> será lançada.  
  
- Ao converter um valor `double` ou `float` em um tipo integral, esse valor será arredondado em direção a zero para o valor integral mais próximo. Se o valor integral resultante estiver fora do intervalo do tipo de destino, o resultado dependerá do [contexto de verificação](checked-and-unchecked.md) de estouro. Em um contexto verificado, uma <xref:System.OverflowException> será lançada, ao passo que em um contexto não verificado, o resultado será um valor não especificado do tipo de destino.  
  
- Ao converter `double` para `float`, o valor `double` será arredondado para o valor `float` mais próximo. Se o valor `double` for muito pequeno ou muito grande para caber no tipo de destino, o resultado será zero ou infinito.  
  
- Ao converter `float` ou `double` para `decimal`, o valor de origem será convertido para uma representação `decimal` e arredondado para o número mais próximo após a 28ª casa decimal, se necessário. De acordo com o valor do valor de origem, um dos resultados a seguir podem ocorrer:  

  - Se o valor de origem for muito pequeno para ser representado como um `decimal`, o resultado será zero.  

  - Se o valor de origem for um NaN (não for um número), infinito ou muito grande para ser representado como um `decimal`, uma <xref:System.OverflowException> será lançada.  
  
- Ao converter `decimal` para `float` ou `double`, o valor `decimal` será arredondado para o valor `double` ou `float` mais próximo.  
  
 Para obter mais informações sobre conversões explícitas, consulte a seção [Conversões explícitas](~/_csharplang/spec/conversions.md#explicit-conversions) da [Especificação da linguagem C#](../language-specification/index.md).
  
## <a name="see-also"></a>Consulte também

- [Referência de C#](../index.md)
- [Conversão e conversões de tipo](../../programming-guide/types/casting-and-type-conversions.md)
- [Operador ()](../operators/type-testing-and-conversion-operators.md#cast-operator-)
- [Tabela de tipos integrais](integral-types-table.md)
- [Tabela de tipos de ponto flutuante](floating-point-types-table.md)
- [Tabela de tipos internos](built-in-types-table.md)
- [Tabela de conversões numéricas implícitas](implicit-numeric-conversions-table.md)
