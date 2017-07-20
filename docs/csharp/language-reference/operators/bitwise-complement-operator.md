---
title: "Operador ~ (Referência de C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- ~_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- tilde (~) one's complement operator [C#]
- ~ operator [C#]
- ~ [C#], bitwise complement operator
- bitwise complement operator [C#]
ms.assetid: 11bc078a-50e2-4d7e-9896-67ef669dc602
caps.latest.revision: 18
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
ms.sourcegitcommit: a5ed524a1b17f7be8903f998cbd732594faab831
ms.openlocfilehash: c7245700f78ff52a98c499d895c7eb2f95efe5b6
ms.contentlocale: pt-br
ms.lasthandoff: 05/15/2017

---
# <a name="-operator-c-reference"></a>Operador ~ (Referência de C#)
O operador `~` executa uma operação de complemento bit a bit em seu operando, que tem o efeito de reverter cada bit. Operadores de complemento bit a bit são predefinidos para [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md) e [ulong](../../../csharp/language-reference/keywords/ulong.md).  
  
> [!NOTE]
>  O símbolo `~` também é usado para declarar finalizadores. Para mais informações, consulte [Finalizadores](../../../csharp/programming-guide/classes-and-structs/destructors.md).  
  
## <a name="remarks"></a>Comentários  
 Os tipos definidos pelo usuário podem sobrecarregar o operador `~`. Para obter mais informações, consulte [operador](../../../csharp/language-reference/keywords/operator.md). As operações em tipos integrais geralmente são permitidas na enumeração.  
  
## <a name="example"></a>Exemplo  
 [!code-cs[csRefOperators#25](../../../csharp/language-reference/operators/codesnippet/CSharp/bitwise-complement-operator_1.cs)]  
  
## <a name="see-also"></a>Consulte também  
 [Referência de C#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Operadores do C#](../../../csharp/language-reference/operators/index.md)   
 [Finalizadores](../../../csharp/programming-guide/classes-and-structs/destructors.md)
