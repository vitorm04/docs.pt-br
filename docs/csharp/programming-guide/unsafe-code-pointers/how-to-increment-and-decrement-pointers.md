---
title: Como incrementar e diminuir ponteiros – Guia de Programação em C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], increment and decrement
- pointer expressions [C#], increment and decrement
ms.assetid: 1b8b9281-44ee-485a-9045-3db38a4b4b89
ms.openlocfilehash: 040437bc8cbab4ba12f243434bdea7798711ce8a
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65635156"
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
  
 [!code-csharp[csProgGuidePointers#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers2.cs#3)]  
  
 [!code-csharp[csProgGuidePointers#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#13)]  
  
**Value:0 @ Address:12860272**
**Value:1 @ Address:12860276**
**Value:2 @ Address:12860280**
**Value:3 @ Address:12860284**
**Value:4 @ Address:12860288**

## <a name="see-also"></a>Consulte também

- [Guia de Programação em C#](../../../csharp/programming-guide/index.md)
- [Operadores do C#](../../../csharp/language-reference/operators/index.md)
- [Manipulando ponteiros](../../../csharp/programming-guide/unsafe-code-pointers/how-to-increment-and-decrement-pointers.md)
- [Tipos de ponteiro](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)
- [Tipos](../../../csharp/language-reference/keywords/types.md)
- [unsafe](../../../csharp/language-reference/keywords/unsafe.md)
- [Instrução fixed](../../../csharp/language-reference/keywords/fixed-statement.md)
- [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)
- [sizeof](../../../csharp/language-reference/keywords/sizeof.md)
