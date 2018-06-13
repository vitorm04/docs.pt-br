---
title: Genéricos e matrizes (Guia de Programação em C#)
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], arrays
- arrays [C#], generics
ms.assetid: 7d956536-3851-41b5-94ad-3e7c0a5fe485
ms.openlocfilehash: 2e7ab9ff0dc4a73500c1a452df16af17c720d528
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33320658"
---
# <a name="generics-and-arrays-c-programming-guide"></a>Genéricos e matrizes (Guia de Programação em C#)
No C# 2.0 e versões posteriores, matrizes unidimensionais que têm um limite inferior a zero implementam <xref:System.Collections.Generic.IList%601> automaticamente. Isso permite a criação de métodos genéricos que podem usar o mesmo código para iterar por meio de matrizes e outros tipos de coleção. Essa técnica é útil principalmente para ler dados em coleções. A interface <xref:System.Collections.Generic.IList%601> não pode ser usada para adicionar ou remover elementos de uma matriz. Uma exceção será lançada se você tentar chamar um método <xref:System.Collections.Generic.IList%601> tal como <xref:System.Collections.Generic.IList%601.RemoveAt%2A> em uma matriz neste contexto.  
  
 O exemplo de código a seguir demonstra como um único método genérico que usa um parâmetro de entrada <xref:System.Collections.Generic.IList%601> pode iterar por meio de uma lista e uma matriz, nesse caso, uma matriz de inteiros.  
  
 [!code-csharp[csProgGuideGenerics#35](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-arrays_1.cs)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Collections.Generic>  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
 [Genéricos](../../../csharp/programming-guide/generics/index.md)  
 [Matrizes](../../../csharp/programming-guide/arrays/index.md)  
 [Genéricos](~/docs/standard/generics/index.md)
