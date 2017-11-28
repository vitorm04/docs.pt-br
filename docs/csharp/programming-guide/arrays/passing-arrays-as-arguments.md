---
title: "Passando matrizes como argumentos (Guia de Programação em C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: arrays [C#], passing as arguments
ms.assetid: f3a0971e-c87c-4a1f-8262-bc0a3b712772
caps.latest.revision: "21"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f152173b747a171052ab99f261ed91ced9465fdc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="passing-arrays-as-arguments-c-programming-guide"></a>Passando matrizes como argumentos (Guia de Programação em C#)
As matrizes podem ser passadas como argumentos para parâmetros de método. Como matrizes são tipos de referência, o método pode alterar o valor dos elementos.  
  
## <a name="passing-single-dimensional-arrays-as-arguments"></a>Passando matrizes unidimensionais como argumentos  
 É possível passar uma matriz unidimensional inicializada para um método. Por exemplo, a instrução a seguir envia uma matriz a um método de impressão.  
  
 [!code-csharp[csProgGuideArrays#34](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_1.cs)]  
  
 O código a seguir mostra uma implementação parcial do método de impressão.  
  
 [!code-csharp[csProgGuideArrays#33](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_2.cs)]  
  
 É possível inicializar e passar uma nova matriz em uma etapa, conforme mostrado no exemplo a seguir.  
  
 [!code-csharp[CsProgGuideArrays#35](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_3.cs)]  
  
## <a name="example"></a>Exemplo  
  
### <a name="description"></a>Descrição  
 No exemplo a seguir, uma matriz de cadeia de caracteres é inicializada e passada como um argumento para um método `PrintArray` para cadeias de caracteres. O método exibe os elementos da matriz. Em seguida, os métodos `ChangeArray` e `ChangeArrayElement` são chamados para demonstrar que o envio de um argumento de matriz por valor não impede alterações nos elementos de matriz.  
  
### <a name="code"></a>Código  
 [!code-csharp[csProgGuideArrays#30](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_4.cs)]  
  
## <a name="passing-multidimensional-arrays-as-arguments"></a>Passando matrizes multidimensionais como argumentos  
 Você passa uma matriz multidimensional inicializada para um método da mesma forma que você passa uma matriz unidimensional.  
  
 [!code-csharp[csProgGuideArrays#41](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_5.cs)]  
  
 O código a seguir mostra uma declaração parcial de um método de impressão que aceita uma matriz bidimensional como seu argumento.  
  
 [!code-csharp[csProgGuideArrays#36](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_6.cs)]  
  
 É possível inicializar e passar uma nova matriz em uma etapa, conforme mostrado no exemplo a seguir.  
  
 [!code-csharp[csProgGuideArrays#32](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_7.cs)]  
  
## <a name="example"></a>Exemplo  
  
### <a name="description"></a>Descrição  
 No exemplo a seguir, uma matriz bidimensional de inteiros é inicializada e passada para o método `Print2DArray`. O método exibe os elementos da matriz.  
  
### <a name="code"></a>Código  
 [!code-csharp[csProgGuideArrays#31](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_8.cs)]  
  
## <a name="see-also"></a>Consulte também  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
 [Matrizes](../../../csharp/programming-guide/arrays/index.md)  
 [Matrizes unidimensionais](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)  
 [Matrizes multidimensionais](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)  
 [Matrizes denteadas](../../../csharp/programming-guide/arrays/jagged-arrays.md)
