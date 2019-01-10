---
title: 'Como: obter o valor de uma variável de ponteiro – Guia de Programação em C#'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- pointer expressions [C#], indirection
- pointers [C#], indirection
- variables [C#], pointers
- pointers [C#], * operator
ms.assetid: 460a813a-4995-44c1-9de2-213b91dc7668
ms.openlocfilehash: b20642344b34b5426512ef64bde2ab33d55136b9
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53236629"
---
# <a name="how-to-obtain-the-value-of-a-pointer-variable-c-programming-guide"></a>Como: obter o valor de uma variável de ponteiro (Guia de Programação em C#)
Use o operador de indireção de ponteiro para obter a variável no local apontado por um ponteiro. A expressão usa o seguinte formato, em que `p` é um tipo de ponteiro:  
  
```  
*p;  
```  
  
 Não é possível utilizar o operador de indireção unário em uma expressão de qualquer tipo diferente do tipo de ponteiro. Além disso, não é possível aplicá-lo a um ponteiro [void](../../../csharp/language-reference/keywords/void.md).  
  
 Ao aplicar o operador de indireção a um ponteiro [nulo](../../../csharp/language-reference/keywords/null.md), o resultado dependerá da implementação.  
  
## <a name="example"></a>Exemplo  
 No exemplo a seguir, uma variável do tipo `char` é acessada usando ponteiros de tipos diferentes. Observe que o endereço do `theChar` variará de execução em execução, pois o endereço físico alocado a uma variável pode ser alterado.  
  
 [!code-csharp[csProgGuidePointers#5](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-obtain-the-value-of-a-pointer-variable_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#6](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-obtain-the-value-of-a-pointer-variable_2.cs)]  
  
**Valor de theChar = Z**
**Endereço de theChar = 12F718**
**Valor de pChar = Z**
**Valor de pInt = 90**

## <a name="see-also"></a>Consulte também

- [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
- [Expressões de ponteiro](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
- [Tipos de ponteiro](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
- [Tipos](../../../csharp/language-reference/keywords/types.md)  
- [unsafe](../../../csharp/language-reference/keywords/unsafe.md)  
- [Instrução fixed](../../../csharp/language-reference/keywords/fixed-statement.md)  
- [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)
