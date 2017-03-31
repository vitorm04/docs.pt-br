---
title: "Passando matrizes como argumentos (Guia de Programação em C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- arrays [C#], passing as arguments
ms.assetid: f3a0971e-c87c-4a1f-8262-bc0a3b712772
caps.latest.revision: 21
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
ms.openlocfilehash: f6dcaf5fa5e32cdd47292ba2a687da9cd24d87d7
ms.lasthandoff: 03/13/2017

---
# <a name="passing-arrays-as-arguments-c-programming-guide"></a>Passando matrizes como argumentos (Guia de Programação em C#)
As matrizes podem ser passadas como argumentos para parâmetros de método. Como matrizes são tipos de referência, o método pode alterar o valor dos elementos.  
  
## <a name="passing-single-dimensional-arrays-as-arguments"></a>Passando matrizes unidimensionais como argumentos  
 É possível passar uma matriz unidimensional inicializada para um método. Por exemplo, a instrução a seguir envia uma matriz a um método de impressão.  
  
 [!code-cs[csProgGuideArrays#34](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_1.cs)]  
  
 O código a seguir mostra uma implementação parcial do método de impressão.  
  
 [!code-cs[csProgGuideArrays#33](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_2.cs)]  
  
 É possível inicializar e passar uma nova matriz em uma etapa, conforme mostrado no exemplo a seguir.  
  
 [!code-cs[CsProgGuideArrays#35](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_3.cs)]  
  
## <a name="example"></a>Exemplo  
  
### <a name="description"></a>Descrição  
 No exemplo a seguir, uma matriz de cadeia de caracteres é inicializada e passada como um argumento para um método `PrintArray` para cadeias de caracteres. O método exibe os elementos da matriz. Em seguida, os métodos `ChangeArray` e `ChangeArrayElement` são chamados para demonstrar que o envio de um argumento de matriz por valor não impede alterações nos elementos de matriz.  
  
### <a name="code"></a>Código  
 [!code-cs[csProgGuideArrays#30](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_4.cs)]  
  
## <a name="passing-multidimensional-arrays-as-arguments"></a>Passando matrizes multidimensionais como argumentos  
 Você passa uma matriz multidimensional inicializada para um método da mesma forma que você passa uma matriz unidimensional.  
  
 [!code-cs[csProgGuideArrays#41](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_5.cs)]  
  
 O código a seguir mostra uma declaração parcial de um método de impressão que aceita uma matriz bidimensional como seu argumento.  
  
 [!code-cs[csProgGuideArrays#36](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_6.cs)]  
  
 É possível inicializar e passar uma nova matriz em uma etapa, conforme mostrado no exemplo a seguir.  
  
 [!code-cs[csProgGuideArrays#32](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_7.cs)]  
  
## <a name="example"></a>Exemplo  
  
### <a name="description"></a>Descrição  
 No exemplo a seguir, uma matriz bidimensional de inteiros é inicializada e passada para o método `Print2DArray`. O método exibe os elementos da matriz.  
  
### <a name="code"></a>Código  
 [!code-cs[csProgGuideArrays#31](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_8.cs)]  
  
## <a name="see-also"></a>Consulte também  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Matrizes](../../../csharp/programming-guide/arrays/index.md)   
 [Matrizes Unidimensionais](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)   
 [Matrizes Multidimensionais](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)   
 [Matrizes denteadas](../../../csharp/programming-guide/arrays/jagged-arrays.md)
