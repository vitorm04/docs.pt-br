---
title: "Operador &gt;&gt; (Referência de C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: '>>_CSharpKeyword'
helpviewer_keywords:
- '>> operator [C#]'
- right shift operator (>>) [C#]
ms.assetid: a07f8679-d318-4ef8-b38b-65903efb8056
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 7c2eddf06d7b8417c9fcb0fed395b2bf51e07144
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="gtgt-operator-c-reference"></a>Operador &gt;&gt; (Referência de C#)
O operador de deslocamento para a direita (`>>`) desloca o primeiro operando à direita pelo número de bits especificado pelo seu segundo operando.  
  
## <a name="remarks"></a>Comentários  
 Se o primeiro operando for um [int](../../../csharp/language-reference/keywords/int.md) ou [uint](../../../csharp/language-reference/keywords/uint.md) (quantidade de 32 bits), a contagem de deslocamento será determinada pelos cinco bits de ordem inferior do segundo operando (segundo operando &0x1f).  
  
 Se o primeiro operando for um [long](../../../csharp/language-reference/keywords/long.md) ou [ulong](../../../csharp/language-reference/keywords/ulong.md) (quantidade de 64 bits), a contagem de deslocamento será determinada pelos seis bits de ordem inferior do segundo operando (segundo operando & 0x3f).  
  
 Se o primeiro operando for um [int](../../../csharp/language-reference/keywords/int.md) ou [long](../../../csharp/language-reference/keywords/long.md), o deslocamento para a direita será um deslocamento aritmético (bits vazios de ordem superior devem ser definidos como o bit de sinal). Se o primeiro operando for do tipo [uint](../../../csharp/language-reference/keywords/uint.md) ou [ulong](../../../csharp/language-reference/keywords/ulong.md), o deslocamento para a direita será um deslocamento lógico (bits de ordem superior são preenchidos com zero).  
  
 Tipos definidos pelo usuário podem sobrecarregar o operador `>>`; o tipo do primeiro operando deve ser o tipo definido pelo usuário e o tipo do segundo operando deve ser [int](../../../csharp/language-reference/keywords/int.md). Para obter mais informações, consulte [operador](../../../csharp/language-reference/keywords/operator.md). Quando um operador binário está sobrecarregado, o operador de atribuição correspondente, se houver, também estará implicitamente sobrecarregado.  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[csRefOperators#26](../../../csharp/language-reference/operators/codesnippet/CSharp/right-shift-operator_1.cs)]  
  
## <a name="see-also"></a>Consulte também  
 [Referência de C#](../../../csharp/language-reference/index.md)  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
 [Operadores do C#](../../../csharp/language-reference/operators/index.md)
