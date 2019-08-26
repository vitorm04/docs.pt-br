---
title: Matrizes unidimensionais – Guia de Programação em C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- single-dimensional arrays [C#]
- arrays [C#], single-dimensional
ms.assetid: 2cec1196-1de0-49d2-baf2-c607c33310e8
ms.openlocfilehash: 17c384ec327d4a80ed614dce6254baa5bfb2e960
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69597301"
---
# <a name="single-dimensional-arrays-c-programming-guide"></a>Matrizes unidimensionais (Guia de Programação em C#)

É possível declarar uma matriz unidimensional de cinco inteiros, conforme mostrado no exemplo a seguir:  
  
 [!code-csharp[csProgGuideArrays#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#4)]  
  
 Essa matriz contém os elementos de `array[0]` a `array[4]`. O operador [new](../../language-reference/operators/new-operator.md) é usado para criar a matriz e inicializar os elementos da matriz para seus valores padrão. Neste exemplo, todos os elementos da matriz são inicializados em zero.  
  
 Uma matriz que armazena os elementos da cadeia de caracteres pode ser declarada da mesma maneira. Por exemplo:  
  
 [!code-csharp[csProgGuideArrays#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#5)]  
  
## <a name="array-initialization"></a>Inicialização de Matriz

 É possível inicializar uma matriz na declaração. Nesse caso, o especificador de comprimento não é necessário porque ele já é fornecido pelo número de elementos na lista de inicialização. Por exemplo:  
  
 [!code-csharp[csProgGuideArrays#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#6)]  
  
 Uma matriz de cadeia de caracteres pode ser inicializada da mesma maneira. A seguir, há uma declaração de uma matriz de cadeia de caracteres em que cada elemento da matriz é inicializado por um nome de um dia:  
 
 ```csharp
 string[] weekDays = new string[] { "Sun", "Mon", "Tue", "Wed", "Thu", "Fri", "Sat" };
 ```
  
 Quando você inicializa uma matriz na declaração, é possível usar os seguintes atalhos:  
  
 [!code-csharp[csProgGuideArrays#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#8)]  
  
 É possível declarar uma variável de matriz sem inicialização, mas é necessário usar o operador `new` quando você atribui uma matriz a essa variável. Por exemplo:  
  
 [!code-csharp[csProgGuideArrays#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#9)]  
  
 O C# 3.0 introduz matrizes de tipo implícito. Para obter mais informações, consulte [Matrizes de tipo implícito](./implicitly-typed-arrays.md).  
  
## <a name="value-type-and-reference-type-arrays"></a>Matrizes de tipo de valor e de tipo de referência

 Considere a seguinte declaração de matriz:  
  
 [!code-csharp[csProgGuideArrays#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#10)]  
  
 O resultado dessa instrução depende se `SomeType` é um tipo de valor ou um tipo de referência. Se for um tipo de valor, a instrução criará uma matriz de 10 elementos, cada um deles tem o tipo `SomeType`. Se `SomeType` for um tipo de referência, a instrução criará uma matriz de 10 elementos, cada um deles é inicializado com uma referência nula.  
  
 Para obter mais informações sobre tipos de valor e de referência, consulte [Tipos](../../language-reference/keywords/types.md).  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Array>
- [Guia de Programação em C#](../index.md)
- [Matrizes](./index.md)
- [Matrizes multidimensionais](./multidimensional-arrays.md)
- [Matrizes denteadas](./jagged-arrays.md)
