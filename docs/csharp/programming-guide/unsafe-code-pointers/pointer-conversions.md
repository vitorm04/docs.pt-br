---
title: "Conversões de ponteiro (Guia de programação em C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- pointers [C#], conversions
ms.assetid: f0e87502-477a-4ede-a31f-7a3e262e46fb
caps.latest.revision: 17
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
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: b61f40a6ca04b608a32c0105d7731ec2cce9d071
ms.lasthandoff: 03/13/2017

---
# <a name="pointer-conversions-c-programming-guide"></a>Conversões de ponteiro (Guia de Programação em C#)
A tabela a seguir mostra as conversões de ponteiro implícitas predefinidas. As conversões implícitas podem ocorrer em diversas situações, incluindo instruções de atribuição e invocações de método.  
  
## <a name="implicit-pointer-conversions"></a>Conversões de ponteiro implícitas  
  
|De|Para|  
|----------|--------|  
|Qualquer tipo de ponteiro|void*|  
|nulo|Qualquer tipo de ponteiro|  
  
 A conversão explícita de ponteiro é usada para realizar conversões para as quais não há conversão implícita, usando uma expressão de conversão. A tabela a seguir mostra essas conversões.  
  
## <a name="explicit-pointer-conversions"></a>Conversões de ponteiro explícitas  
  
|De|Para|  
|----------|--------|  
|Qualquer tipo de ponteiro|Qualquer outro tipo de ponteiro|  
|sbyte, byte, short, ushort, int, uint, long ou ulong|Qualquer tipo de ponteiro|  
|Qualquer tipo de ponteiro|sbyte, byte, short, ushort, int, uint, long ou ulong|  
  
## <a name="example"></a>Exemplo  
 No exemplo a seguir, um ponteiro para `int` é convertido em um ponteiro para `byte`. Observe que o ponteiro aponta para o menor byte endereçado da variável. Quando você incrementar sucessivamente o resultado, até o tamanho de `int` (4 bytes), você poderá exibir os bytes restantes da variável.  
  
 [!code-cs[csProgGuidePointers#3](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/pointer-conversions_1.cs)]  
  
 [!code-cs[csProgGuidePointers#4](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/pointer-conversions_2.cs)]  
  
## <a name="see-also"></a>Consulte também  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Expressões de Ponteiro](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)   
 [Tipos de Ponteiro](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)   
 [Tipos](../../../csharp/language-reference/keywords/types.md)   
 [unsafe](../../../csharp/language-reference/keywords/unsafe.md)   
 [Instrução fixed](../../../csharp/language-reference/keywords/fixed-statement.md)   
 [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)
