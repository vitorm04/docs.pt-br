---
title: "Tabela de conversões numéricas implícitas (Referência de C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- conversions [C#], implicit numeric
- implicit numeric conversions [C#]
- numeric conversions [C#], implicit
- types [C#], implicit numeric conversions
ms.assetid: 72eb5a94-0491-48bf-8032-d7ebfdfeb8d8
caps.latest.revision: 12
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: e4a0eca529b7c66cca527cfef3078a2c5bd24555
ms.contentlocale: pt-br
ms.lasthandoff: 03/13/2017

---
# <a name="implicit-numeric-conversions-table-c-reference"></a>Tabela de conversões numéricas implícitas (Referência de C#)
A tabela a seguir mostra as conversões numéricas implícitas predefinidas. As conversões implícitas podem ocorrer em diversas situações, incluindo instruções de atribuição e invocações de método.  
  
|De|Para|  
|----------|--------|  
|[sbyte](../../../csharp/language-reference/keywords/sbyte.md)|`short`, `int`, `long`, `float`, `double` ou `decimal`|  
|[byte](../../../csharp/language-reference/keywords/byte.md)|`short`, `ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double` ou `decimal`|  
|[short](../../../csharp/language-reference/keywords/short.md)|`int`, `long`, `float`, `double` ou `decimal`|  
|[ushort](../../../csharp/language-reference/keywords/ushort.md)|`int`, `uint`, `long`, `ulong`, `float`, `double` ou `decimal`|  
|[int](../../../csharp/language-reference/keywords/int.md)|`long`, `float`, `double` ou `decimal`|  
|[uint](../../../csharp/language-reference/keywords/uint.md)|`long`, `ulong`, `float`, `double` ou `decimal`|  
|[long](../../../csharp/language-reference/keywords/long.md)|`float`, `double` ou `decimal`|  
|[char](../../../csharp/language-reference/keywords/char.md)|`ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double` ou `decimal`|  
|[float](../../../csharp/language-reference/keywords/float.md)|`double`|  
|[ulong](../../../csharp/language-reference/keywords/ulong.md)|`float`, `double` ou `decimal`|  
  
## <a name="remarks"></a>Comentários  
  
-   A precisão, mas não a magnitude, poderá ser perdida em conversões de `int`, `uint`, `long` ou `ulong` para `float` e de `long` ou `ulong` para `double`.  
  
-   Não há conversões implícitas para o tipo `char`.  
  
-   Não há conversões implícitas entre tipos de ponto flutuante e o tipo `decimal`.  
  
-   Uma expressão constante do tipo `int` pode ser convertida em `sbyte`, `byte`, `short`, `ushort`, `uint` ou `ulong`, desde que o valor da expressão constante esteja dentro do intervalo do tipo de destino.  
  
## <a name="c-language-specification"></a>Especificação da Linguagem C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Referência de C#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Tabela de Tipos Integrais](../../../csharp/language-reference/keywords/integral-types-table.md)   
 [Tabela de Tipos Internos](../../../csharp/language-reference/keywords/built-in-types-table.md)   
 [Tabela de conversões numéricas explícitas](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)   
 [Transmissões e conversões de tipo](../../../csharp/programming-guide/types/casting-and-type-conversions.md)
