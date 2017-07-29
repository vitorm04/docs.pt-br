---
title: "Como incrementar e diminuir ponteiros (Guia de Programação em C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- pointers [C#], increment and decrement
- pointer expressions [C#], increment and decrement
ms.assetid: 1b8b9281-44ee-485a-9045-3db38a4b4b89
caps.latest.revision: 20
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
ms.openlocfilehash: b474249ed9f7778e44981b292d51f29f46bc420d
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

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
  
 [!code-cs[csProgGuidePointers#3](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-increment-and-decrement-pointers_1.cs)]  
  
 [!code-cs[csProgGuidePointers#13](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-increment-and-decrement-pointers_2.cs)]  
  
 **Valor:0 @ Endereço:12860272**  
**Valor:1 @ Endereço:12860276**  
**Valor:2 @ Endereço:12860280**  
**Valor:3 @ Endereço:12860284**  
**Valor:4 @ Endereço:12860288**   
## <a name="see-also"></a>Consulte também  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Expressões de Ponteiro](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)   
 [Operadores do C#](../../../csharp/language-reference/operators/index.md)   
 [Manipulando Ponteiros](../../../csharp/programming-guide/unsafe-code-pointers/manipulating-pointers.md)   
 [Tipos de Ponteiro](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)   
 [Tipos](../../../csharp/language-reference/keywords/types.md)   
 [unsafe](../../../csharp/language-reference/keywords/unsafe.md)   
 [Instrução fixed](../../../csharp/language-reference/keywords/fixed-statement.md)   
 [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)

