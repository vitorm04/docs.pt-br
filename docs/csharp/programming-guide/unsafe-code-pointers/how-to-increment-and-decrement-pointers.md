---
title: Como incrementar e diminuir ponteiros (Guia de Programação em C#)
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], increment and decrement
- pointer expressions [C#], increment and decrement
ms.assetid: 1b8b9281-44ee-485a-9045-3db38a4b4b89
ms.openlocfilehash: e1c3ac12a126450781d0ce78e788f39c740b5279
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33324279"
---
# <a name="how-to-increment-and-decrement-pointers-c-programming-guide"></a>Como incrementar e diminuir ponteiros (Guia de Programação em C#)
Utilize os operadores de decremento e incremento, `++` e `--`, para alterar o local do ponteiro por [sizeof](../../../csharp/language-reference/keywords/sizeof.md) (`pointer-type`) para um ponteiro do tipo “tipo de ponteiro”*. As expressões de incremento e de decremento têm o seguinte formato:  
  
```  
++p;  
p++;  
--p;  
p--;  
```  
  
 Os operadores de incremento e de decremento podem ser aplicados a ponteiros de qualquer tipo, exceto o tipo `void*`.  
  
 O efeito de aplicar o operador de incremento a um ponteiro do tipo `pointer-type` é a adição de [sizeof](../../../csharp/language-reference/keywords/sizeof.md) (`pointer-type`) ao endereço que está contido na variável do ponteiro.  
  
 O efeito de aplicar o operador de decremento a um ponteiro do tipo `pointer-type` é a subtração de `sizeof` (`pointer-type`) do endereço que está contido na variável do ponteiro.  
  
 Nenhuma exceção é gerada quando a operação estoura o domínio do ponteiro e o resultado depende da implementação.  
  
## <a name="example"></a>Exemplo  
 Neste exemplo, você percorre cada etapa de uma matriz incrementando o ponteiro pelo tamanho de `int`. Em cada etapa, é possível exibir o endereço e o conteúdo do elemento da matriz.  
  
 [!code-csharp[csProgGuidePointers#3](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-increment-and-decrement-pointers_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#13](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-increment-and-decrement-pointers_2.cs)]  
  
 **Valor:0 @ Endereço:12860272**  
**Valor:1 @ Endereço:12860276**  
**Valor:2 @ Endereço:12860280**  
**Valor:3 @ Endereço:12860284**  
**Valor:4 @ Endereço:12860288**   
## <a name="see-also"></a>Consulte também  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
 [Expressões de ponteiro](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
 [Operadores do C#](../../../csharp/language-reference/operators/index.md)  
 [Manipulando ponteiros](../../../csharp/programming-guide/unsafe-code-pointers/manipulating-pointers.md)  
 [Tipos de ponteiro](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
 [Tipos](../../../csharp/language-reference/keywords/types.md)  
 [unsafe](../../../csharp/language-reference/keywords/unsafe.md)  
 [Instrução fixed](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)
