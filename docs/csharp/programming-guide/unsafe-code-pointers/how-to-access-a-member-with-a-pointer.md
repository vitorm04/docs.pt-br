---
title: "Como acessar um membro com um ponteiro (Guia de Programação em C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: pointers [C#], member access
ms.assetid: 1e998498-8c85-4a78-8ce2-4d8c20f08342
caps.latest.revision: "16"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 622d9910b09c9197b7f4ccd5e54e2675fbbbbccb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-access-a-member-with-a-pointer-c-programming-guide"></a>Como acessar um membro com um ponteiro (Guia de Programação em C#)
Para acessar um membro de um struct declarado em um contexto não seguro, é possível usar o operador de acesso de membro conforme mostrado no exemplo a seguir, no qual `p` é um ponteiro para um [struct](../../../csharp/language-reference/keywords/struct.md) que contém um membro `x`.  
  
```  
CoOrds* p = &home;  
p -> x = 25; //member access operator ->  
```  
  
## <a name="example"></a>Exemplo  
 Nesse exemplo, um [struct](../../../csharp/language-reference/keywords/struct.md), `CoOrds`, que contém as duas coordenadas `x` e `y` é declarado e instanciado. Usando o operador de acesso de membro `->` e um ponteiro para a instância `home`, `x` e `y` são valores atribuídos.  
  
> [!NOTE]
>  Observe que a expressão `p->x` é equivalente à expressão `(*p).x` e é possível obter o mesmo resultado usando qualquer uma das duas expressões.  
  
 [!code-csharp[csProgGuidePointers#9](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-access-a-member-with-a-pointer_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#10](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-access-a-member-with-a-pointer_2.cs)]  
  
## <a name="see-also"></a>Consulte também  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
 [Expressões de ponteiro](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
 [Tipos de ponteiro](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
 [Tipos](../../../csharp/language-reference/keywords/types.md)  
 [unsafe](../../../csharp/language-reference/keywords/unsafe.md)  
 [Instrução fixed](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)
