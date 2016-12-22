---
title: "Tabela de convers&#245;es num&#233;ricas expl&#237;citas (Refer&#234;ncia de C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "conversões [C#], numéricas explícitas"
  - "conversão numérica explícita [C#]"
  - "conversões numéricas [C#], explicit"
  - "tipos de dados numéricos [C#]"
  - "conversão de tipo [C#], numéricas explícitas"
  - "tipos [C#], conversões numéricas explícitas"
ms.assetid: f3bb9e76-6b92-4df7-bc36-f866c24e1dfd
caps.latest.revision: 14
caps.handback.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Tabela de convers&#245;es num&#233;ricas expl&#237;citas (Refer&#234;ncia de C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Conversão numérica explícita é usado para converter qualquer tipo numérico para qualquer outro tipo numérico, para o qual não há nenhuma conversão implícita, usando uma expressão de conversão.  A tabela a seguir mostra essas conversões.  
  
 Para obter mais informações sobre conversões, consulte [Conversões cast e conversões de tipo](../../../csharp/programming-guide/types/casting-and-type-conversions.md).  
  
|From|Para|  
|----------|----------|  
|[sbyte](../../../csharp/language-reference/keywords/sbyte.md)|`byte`, `ushort`, `uint`, `ulong`, ou `char`|  
|[Byte](../../../csharp/language-reference/keywords/byte.md)|`Sbyte`ou`char`|  
|[short](../../../csharp/language-reference/keywords/short.md)|`sbyte`, `byte`, `ushort`, `uint`, `ulong`, or `char`|  
|[ushort](../../../csharp/language-reference/keywords/ushort.md)|`sbyte`, `byte`, `short`, or `char`|  
|[int](../../../csharp/language-reference/keywords/int.md)|`sbyte`, `byte`, `short`, `ushort`, `uint`, `ulong`,or `char`|  
|[uint](../../../csharp/language-reference/keywords/uint.md)|`sbyte`, `byte`, `short`, `ushort`, `int`, or `char`|  
|[long](../../../csharp/language-reference/keywords/long.md)|`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `ulong`, or `char`|  
|[ulong](../../../csharp/language-reference/keywords/ulong.md)|`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, or `char`|  
|[char](../../../csharp/language-reference/keywords/char.md)|`sbyte`, `byte`, or `short`|  
|[float](../../../csharp/language-reference/keywords/float.md)|`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`,or `decimal`|  
|[double](../../../csharp/language-reference/keywords/double.md)|`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, `float`,or `decimal`|  
|[decimal](../../../csharp/language-reference/keywords/decimal.md)|`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, `float`, or `double`|  
  
## Comentários  
  
-   A conversão numérica explícita pode causar perda de precisão ou resultado throwing exceções.  
  
-   Quando você converter uma `decimal` valor de tipo integral, esse valor é arredondado em direção a zero para o valor inteiro mais próximo.  Se o valor integral resultante está fora do intervalo do tipo de destino, um <xref:System.OverflowException> é lançada.  
  
-   Quando você converter de um `double` ou `float` valor para um tipo integral, o valor é truncado.  Se o valor integral resultante está fora do intervalo do valor de destino, o resultado depende o estouro de verificação de contexto.  Em um contexto marcada, um `OverflowException` é lançada, embora em um contexto desmarcado, o resultado é um valor não especificado no tipo de destino.  
  
-   Quando você converter `double` para `float`, o `double` valor é arredondado para o mais próximo `float` valor.  Se o `double` valor é muito pequeno ou muito grande para caber no tipo de destino, o resultado será zero ou infinito.  
  
-   Quando você converter `float` ou `double` para `decimal`, o valor de origem é convertido em `decimal` representação e arredondado para o próximo número após a casa decimal 28, se necessário.  Dependendo do valor do valor de origem, pode ocorrer um dos seguintes resultados:  
  
    -   Se o valor de origem é muito pequeno para ser representado como uma `decimal`, o resultado se torna zero.  
  
    -   Se o valor de origem for NaN \(não um número\), infinito, ou muito grande para ser representado como uma `decimal`, um `OverflowException` é lançada.  
  
-   Quando você converter `decimal` para `float` ou `double`, o `decimal` valor é arredondado para o mais próximo `double` ou `float` valor.  
  
 Para obter mais informações sobre conversão explícita, consulte Explicit na especificação de linguagem C\#.  Para obter mais informações sobre como acessar a especificação, consulte [Especificação da linguagem C\#](../../../visual-basic/reference/language-specification.md).  
  
## Consulte também  
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Conversões cast e conversões de tipo](../../../csharp/programming-guide/types/casting-and-type-conversions.md)   
 [Operador \(\)](../../../csharp/language-reference/operators/invocation-operator.md)   
 [Tabela de tipos integrais](../../../csharp/language-reference/keywords/integral-types-table.md)   
 [Tabela de tipos internos](../../../csharp/language-reference/keywords/built-in-types-table.md)   
 [Tabela de conversões numéricas implícitas](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)