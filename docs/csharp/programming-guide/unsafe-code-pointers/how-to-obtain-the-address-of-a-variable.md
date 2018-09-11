---
title: Como obter o endereço de uma variável (Guia de Programação em C#)
ms.date: 07/20/2015
helpviewer_keywords:
- variables [C#], address of
- pointers [C#], & operator
- pointer expressions [C#], address-of operator
ms.assetid: 44fe2cd9-a64f-4ef5-be2a-09ce807c0182
ms.openlocfilehash: 40a7ac34a4e68df7aa316adc3cbd1999d975eabe
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43741867"
---
# <a name="how-to-obtain-the-address-of-a-variable-c-programming-guide"></a>Como obter o endereço de uma variável (Guia de Programação em C#)
Para obter o endereço de uma expressão unária, que é avaliada como uma variável fixa, use o operador address-of `&`:  
  
```csharp  
int number;  
int* p = &number; //address-of operator &  
```  
  
 O operador address-of pode ser aplicado somente a uma variável. Se a variável for uma variável móvel, é possível usar a [instrução fixa](../../../csharp/language-reference/keywords/fixed-statement.md) para corrigir temporariamente a variável antes de obter seu endereço.  
  
 É sua responsabilidade assegurar que a variável seja inicializada. O compilador não emitirá uma mensagem de erro se a variável não for inicializada.  
  
 Não é possível obter o endereço de uma constante nem de um valor.  
  
## <a name="example"></a>Exemplo  
 Neste exemplo, um ponteiro para `int`, `p`, é declarado e atribuído ao endereço de uma variável de inteiro, `number`. A variável `number` é inicializada como resultado da atribuição a `*p`. Se você comentar esta instrução de atribuição, a inicialização da variável `number` será removida, mas não será emitido nenhum erro em tempo de compilação.  

> [!NOTE]
> Compile este exemplo com a opção do compilador [`-unsafe`](../../language-reference/compiler-options/unsafe-compiler-option.md).
  
 [!code-csharp[address-of-a-variable](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#8)]  
  
## <a name="see-also"></a>Consulte também

- [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
- [Expressões de ponteiro](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
- [Tipos de ponteiro](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
- [Tipos](../../../csharp/language-reference/keywords/types.md)  
- [unsafe](../../../csharp/language-reference/keywords/unsafe.md)  
- [Instrução fixed](../../../csharp/language-reference/keywords/fixed-statement.md)  
- [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)
