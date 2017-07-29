---
title: "Operador &gt; (Referência de C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '>_CSharpKeyword'
dev_langs:
- CSharp
helpviewer_keywords:
- '> operator [C#]'
- greater than operator (>) [C#]
ms.assetid: 26d3cb69-9c0b-4cc5-858b-5be1abd6659d
caps.latest.revision: 16
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 5b4eb1f6fcca311fc772e4dbe0ce0391201af3de
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="gt-operator-c-reference"></a>Operador &gt; (Referência de C#)
Todos os tipos numéricos e de enumeração definem um operador relacional "maior que" (`>`) que retornará `true` se o primeiro operando for maior que o segundo, caso contrário, `false`.  
  
## <a name="remarks"></a>Comentários  
 Os tipos definidos pelo usuário podem sobrecarregar o operador `>` (consulte [operador](../../../csharp/language-reference/keywords/operator.md)). Se `>` estiver sobrecarregado, [<](../../../csharp/language-reference/operators/less-than-operator.md) também deverá estar sobrecarregado. Quando um operador binário está sobrecarregado, o operador de atribuição correspondente, se houver, também estará implicitamente sobrecarregado.  
  
## <a name="example"></a>Exemplo  
 [!code-cs[csRefOperators#29](../../../csharp/language-reference/operators/codesnippet/CSharp/greater-than-operator_1.cs)]  
  
## <a name="see-also"></a>Consulte também  
 [Referência de C#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Operadores do C#](../../../csharp/language-reference/operators/index.md)   
 [explicit](../../../csharp/language-reference/keywords/explicit.md)

