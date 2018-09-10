---
title: Matrizes unidimensionais (Guia de Programação em C#)
ms.date: 07/20/2015
helpviewer_keywords:
- single-dimensional arrays [C#]
- arrays [C#], single-dimensional
ms.assetid: 2cec1196-1de0-49d2-baf2-c607c33310e8
ms.openlocfilehash: c2f26fd74a596ada21eef578e58c9cd8e0305d6c
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44128544"
---
# <a name="single-dimensional-arrays-c-programming-guide"></a>Matrizes unidimensionais (Guia de Programação em C#)

É possível declarar uma matriz unidimensional de cinco inteiros, conforme mostrado no exemplo a seguir:  
  
 [!code-csharp[csProgGuideArrays#4](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_1.cs)]  
  
 Essa matriz contém os elementos de `array[0]` a `array[4]`. O operador [new](../../../csharp/language-reference/keywords/new.md) é usado para criar a matriz e inicializar os elementos da matriz para seus valores padrão. Neste exemplo, todos os elementos da matriz são inicializados em zero.  
  
 Uma matriz que armazena os elementos da cadeia de caracteres pode ser declarada da mesma maneira. Por exemplo:  
  
 [!code-csharp[csProgGuideArrays#5](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_2.cs)]  
  
## <a name="array-initialization"></a>Inicialização de Matriz

 É possível inicializar uma matriz na declaração. Nesse caso, o especificador de classificação não é necessário, porque ele já é fornecido pelo número de elementos na lista de inicialização. Por exemplo:  
  
 [!code-csharp[csProgGuideArrays#6](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_3.cs)]  
  
 Uma matriz de cadeia de caracteres pode ser inicializada da mesma maneira. A seguir, há uma declaração de uma matriz de cadeia de caracteres em que cada elemento da matriz é inicializado por um nome de um dia:  
  
 [!code-csharp[csProgGuideArrays#7](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_4.cs)]  
  
 Quando você inicializa uma matriz na declaração, é possível usar os seguintes atalhos:  
  
 [!code-csharp[csProgGuideArrays#8](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_5.cs)]  
  
 É possível declarar uma variável de matriz sem inicialização, mas é necessário usar o operador `new` quando você atribui uma matriz a essa variável. Por exemplo:  
  
 [!code-csharp[csProgGuideArrays#9](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_6.cs)]  
  
 O C# 3.0 introduz matrizes de tipo implícito. Para obter mais informações, consulte [Matrizes de tipo implícito](../../../csharp/programming-guide/arrays/implicitly-typed-arrays.md).  
  
## <a name="value-type-and-reference-type-arrays"></a>Matrizes de tipo de valor e de tipo de referência

 Considere a seguinte declaração de matriz:  
  
 [!code-csharp[csProgGuideArrays#10](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_7.cs)]  
  
 O resultado dessa instrução depende se `SomeType` é um tipo de valor ou um tipo de referência. Se for um tipo de valor, a instrução criará uma matriz de 10 elementos, cada um deles tem o tipo `SomeType`. Se `SomeType` for um tipo de referência, a instrução criará uma matriz de 10 elementos, cada um deles é inicializado com uma referência nula.  
  
 Para obter mais informações sobre tipos de valor e de referência, consulte [Tipos](../../../csharp/language-reference/keywords/types.md).  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Array>  
- [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
- [Matrizes](../../../csharp/programming-guide/arrays/index.md)  
- [Matrizes multidimensionais](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)  
- [Matrizes denteadas](../../../csharp/programming-guide/arrays/jagged-arrays.md)
