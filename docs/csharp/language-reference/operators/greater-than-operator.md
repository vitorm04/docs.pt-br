---
title: "Operador &gt; (Referência de C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: '>_CSharpKeyword'
helpviewer_keywords:
- '> operator [C#]'
- greater than operator (>) [C#]
ms.assetid: 26d3cb69-9c0b-4cc5-858b-5be1abd6659d
caps.latest.revision: "16"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: fc7c173ecc97bd3ca3b76a92ccbabc0f40062ac7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="gt-operator-c-reference"></a>Operador &gt; (Referência de C#)
Todos os tipos numéricos e de enumeração definem um operador relacional "maior que" (`>`) que retornará `true` se o primeiro operando for maior que o segundo, caso contrário, `false`.  
  
## <a name="remarks"></a>Comentários  
 Os tipos definidos pelo usuário podem sobrecarregar o operador `>` (consulte [operador](../../../csharp/language-reference/keywords/operator.md)). Se `>` estiver sobrecarregado, [<](../../../csharp/language-reference/operators/less-than-operator.md) também deverá estar sobrecarregado. Quando um operador binário está sobrecarregado, o operador de atribuição correspondente, se houver, também estará implicitamente sobrecarregado.  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[csRefOperators#29](../../../csharp/language-reference/operators/codesnippet/CSharp/greater-than-operator_1.cs)]  
  
## <a name="see-also"></a>Consulte também  
 [Referência de C#](../../../csharp/language-reference/index.md)  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
 [Operadores do C#](../../../csharp/language-reference/operators/index.md)  
 [explicit](../../../csharp/language-reference/keywords/explicit.md)
