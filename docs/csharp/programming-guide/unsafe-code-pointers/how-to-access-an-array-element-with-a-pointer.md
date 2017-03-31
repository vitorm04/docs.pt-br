---
title: "Como Acessar um Elemento de Matriz com um Ponteiro (Guia de Programação em C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- pointers [C#], array access
ms.assetid: 6c46f2af-a730-4855-8638-f136d9abaa12
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
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 7649adf36780666d5272486d8fce4e13ff052f0d
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-access-an-array-element-with-a-pointer-c-programming-guide"></a>Como acessar um elemento de matriz com um ponteiro (Guia de Programação em C#)
Em um contexto não seguro, é possível acessar um elemento na memória por meio do acesso de elemento de ponteiro, conforme mostrado no exemplo a seguir:  
  
```  
 char* charPointer = stackalloc char[123];  
for (int i = 65; i < 123; i++)  
{  
    charPointer[i] = (char)i; //access array elements  
}  
```  
  
 A expressão entre colchetes deve ser implicitamente conversível para `int`, `uint`, `long` ou `ulong`. A operação p[e] é equivalente a *(p+e). Assim como no C e no C++, o acesso de elemento de ponteiro não verifica erros fora dos limites.  
  
## <a name="example"></a>Exemplo  
 Neste exemplo, os locais de memória 123 são alocados para uma matriz de caracteres, `charPointer`. A matriz é usada para exibir as letras minúsculas e maiúsculas em dois loops [for](../../../csharp/language-reference/keywords/for.md).  
  
 Observe que a expressão `charPointer[i]` é equivalente à expressão `*(charPointer + i)` e é possível obter o mesmo resultado usando qualquer uma das duas expressões.  
  
 [!code-cs[csProgGuidePointers#11](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-access-an-array-element-with-a-pointer_1.cs)]  
  
 [!code-cs[csProgGuidePointers#12](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-access-an-array-element-with-a-pointer_2.cs)]  
  
 **Letras maiúsculas:**  
**ABCDEFGHIJKLMNOPQRSTUVWXYZ**  
**Letras minúsculas:**  
**abcdefghijklmnopqrstuvwxyz**   
## <a name="see-also"></a>Consulte também  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Expressões de Ponteiro](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)   
 [Tipos de Ponteiro](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)   
 [Tipos](../../../csharp/language-reference/keywords/types.md)   
 [unsafe](../../../csharp/language-reference/keywords/unsafe.md)   
 [Instrução fixed](../../../csharp/language-reference/keywords/fixed-statement.md)   
 [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)
