---
title: Como acessar um membro com um ponteiro – Guia de Programação em C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], member access
ms.assetid: 1e998498-8c85-4a78-8ce2-4d8c20f08342
ms.openlocfilehash: 9762b9e2487c30b81b7ef6ae22827b64e3cb02e2
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/01/2019
ms.locfileid: "57200345"
---
# <a name="how-to-access-a-member-with-a-pointer-c-programming-guide"></a>Como acessar um membro com um ponteiro (Guia de programação em C#)
Para acessar um membro de um struct declarado em um contexto não seguro, é possível usar o operador de acesso de membro conforme mostrado no exemplo a seguir, no qual `p` é um ponteiro para um [struct](../../../csharp/language-reference/keywords/struct.md) que contém um membro `x`.  
  
```  
CoOrds* p = &home;  
p -> x = 25; //member access operator ->  
```  
  
## <a name="example"></a>Exemplo  
 Nesse exemplo, um [struct](../../../csharp/language-reference/keywords/struct.md), `CoOrds`, que contém as duas coordenadas `x` e `y` é declarado e instanciado. Usando o operador de acesso de membro `->` e um ponteiro para a instância `home`, `x` e `y` são valores atribuídos.  
  
> [!NOTE]
>  Observe que a expressão `p->x` é equivalente à expressão `(*p).x` e é possível obter o mesmo resultado usando qualquer uma das duas expressões.  
  
 [!code-csharp[csProgGuidePointers#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers2.cs#9)]  
  
 [!code-csharp[csProgGuidePointers#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#10)]  
  
## <a name="see-also"></a>Consulte também

- [Guia de Programação em C#](../../../csharp/programming-guide/index.md)
- [Expressões de ponteiro](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)
- [Tipos de ponteiro](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)
- [Tipos](../../../csharp/language-reference/keywords/types.md)
- [unsafe](../../../csharp/language-reference/keywords/unsafe.md)
- [Instrução fixed](../../../csharp/language-reference/keywords/fixed-statement.md)
- [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)
