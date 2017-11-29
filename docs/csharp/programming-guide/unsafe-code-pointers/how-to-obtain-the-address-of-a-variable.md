---
title: "Como obter o endereço de uma variável (Guia de Programação em C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- variables [C#], address of
- pointers [C#], & operator
- pointer expressions [C#], address-of operator
ms.assetid: 44fe2cd9-a64f-4ef5-be2a-09ce807c0182
caps.latest.revision: "19"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 3d0969f7e62864c682660f08cd4198aa4032e0e2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-obtain-the-address-of-a-variable-c-programming-guide"></a>Como obter o endereço de uma variável (Guia de Programação em C#)
Para obter o endereço de uma expressão unária, que é avaliada como uma variável fixa, use o operador address-of:  
  
```  
int number;  
int* p = &number; //address-of operator &  
```  
  
 O operador address-of pode ser aplicado somente a uma variável. Se a variável for uma variável móvel, é possível usar a [instrução fixa](../../../csharp/language-reference/keywords/fixed-statement.md) para corrigir temporariamente a variável antes de obter seu endereço.  
  
 É sua responsabilidade assegurar que a variável seja inicializada. O compilador não emitirá uma mensagem de erro se a variável não for inicializada.  
  
 Não é possível obter o endereço de uma constante ou um valor.  
  
## <a name="example"></a>Exemplo  
 Neste exemplo, um ponteiro para `int`, `p`, é declarado e atribuído ao endereço de uma variável de inteiro, `number`. A variável `number` é inicializada como resultado da atribuição a *p. Se essa instrução de atribuição for transformada em um comentário, a inicialização da variável `number` será removida, mas nenhum erro em tempo de compilação será emitido. Observe o uso do operador [Acesso a Membro](../../../csharp/programming-guide/unsafe-code-pointers/how-to-access-a-member-with-a-pointer.md) `->` para obter e exibir o endereço armazenado no ponteiro.  
  
 [!code-csharp[csProgGuidePointers#7](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-obtain-the-address-of-a-variable_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#8](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-obtain-the-address-of-a-variable_2.cs)]  
  
## <a name="see-also"></a>Consulte também  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
 [Expressões de ponteiro](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
 [Tipos de ponteiro](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
 [Tipos](../../../csharp/language-reference/keywords/types.md)  
 [unsafe](../../../csharp/language-reference/keywords/unsafe.md)  
 [Instrução fixed](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)
