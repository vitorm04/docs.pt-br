---
title: Como incrementar e diminuir ponteiros – Guia de Programação em C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], increment and decrement
- pointer expressions [C#], increment and decrement
ms.assetid: 1b8b9281-44ee-485a-9045-3db38a4b4b89
ms.openlocfilehash: f28fc4f86e4ff01f90bfd49714f38eee7040f9d1
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53242277"
---
# <a name="how-to-increment-and-decrement-pointers-c-programming-guide"></a>Como incrementar e diminuir ponteiros (Guia de Programação em C#)

Utilize os operadores de incremento e de decremento, `++` e `--`, para alterar o local do ponteiro por `sizeof(pointer-type)` para um ponteiro do tipo `pointer-type*`. As expressões de incremento e de decremento têm o seguinte formato:  
  
```csharp
++p;  
p++;  
--p;  
p--;  
```  
  
 Os operadores de incremento e de decremento podem ser aplicados a ponteiros de qualquer tipo, exceto o tipo `void*`.  
  
 O efeito de aplicar o operador de incremento a um ponteiro do tipo `pointer-type*` é a adição de `sizeof(pointer-type)` ao endereço que está contido na variável do ponteiro.  
  
 O efeito de aplicar o operador de decremento a um ponteiro do tipo `pointer-type*` é a subtração de `sizeof(pointer-type)` do endereço que está contido na variável do ponteiro.  
  
 Nenhuma exceção é gerada quando a operação estoura o domínio do ponteiro e o resultado depende da implementação.  
  
## <a name="example"></a>Exemplo  
 Neste exemplo, você percorre cada etapa de uma matriz incrementando o ponteiro pelo tamanho de `int`. Em cada etapa, é possível exibir o endereço e o conteúdo do elemento da matriz.  
  
 [!code-csharp[csProgGuidePointers#3](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-increment-and-decrement-pointers_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#13](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-increment-and-decrement-pointers_2.cs)]  
  
**Value:0 @ Address:12860272**
**Value:1 @ Address:12860276**
**Value:2 @ Address:12860280**
**Value:3 @ Address:12860284**
**Value:4 @ Address:12860288**

## <a name="see-also"></a>Consulte também

- [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
- [Expressões de ponteiro](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
- [Operadores do C#](../../../csharp/language-reference/operators/index.md)  
- [Manipulando ponteiros](../../../csharp/programming-guide/unsafe-code-pointers/manipulating-pointers.md)  
- [Tipos de ponteiro](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
- [Tipos](../../../csharp/language-reference/keywords/types.md)  
- [unsafe](../../../csharp/language-reference/keywords/unsafe.md)  
- [Instrução fixed](../../../csharp/language-reference/keywords/fixed-statement.md)  
- [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)
- [sizeof](../../../csharp/language-reference/keywords/sizeof.md)
