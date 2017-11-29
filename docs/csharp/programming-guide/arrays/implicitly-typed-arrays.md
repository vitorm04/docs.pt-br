---
title: "Matrizes de tipo implícito (Guia de Programação em C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- arrays [C#], implicity-typed
- implicitly-typed arrays [C#]
- C# language, implicitly typed arrays
ms.assetid: e05be95c-6732-403d-ae42-b35f057cbbea
caps.latest.revision: "13"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f6e60ff600a04dab47e8b0ed52dda00441e17f25
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="implicitly-typed-arrays-c-programming-guide"></a>Matrizes de tipo implícito (Guia de Programação em C#)
É possível criar uma matriz de tipo implícito na qual o tipo da instância da matriz é inferido com base nos elementos especificados no inicializador de matriz. As regras para qualquer variável de tipo implícito também se aplicam a matrizes de tipo implícito. Para obter mais informações, consulte [Variáveis Locais de Tipo Implícito](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).  
  
 Geralmente, as matrizes de tipo implícito são usadas em expressões de consulta juntamente com objetos e tipos anônimos e inicializadores de coleção.  
  
 Os exemplos a seguir mostram como criar uma matriz de tipo implícito:  
  
 [!code-csharp[csProgGuideLINQ#37](../../../csharp/programming-guide/arrays/codesnippet/CSharp/implicitly-typed-arrays_1.cs)]  
  
 No exemplo anterior, observe que, com as matrizes de tipo implícito, não são usados colchetes do lado esquerdo da instrução de inicialização. Observe também que as matrizes denteadas são inicializadas usando `new []` assim como matrizes unidimensionais.  
  
## <a name="implicitly-typed-arrays-in-object-initializers"></a>Matrizes de tipo implícito em Inicializadores de objeto  
 Ao criar um tipo anônimo que contém uma matriz, ela deve ser de tipo implícito no inicializador de objeto do tipo. No exemplo a seguir, `contacts` é uma matriz de tipo implícito de tipos anônimos, cada um contém uma matriz denominada `PhoneNumbers`. Observe que a palavra-chave `var` não é usada dentro dos inicializadores de objeto.  
  
 [!code-csharp[csProgGuideLINQ#38](../../../csharp/programming-guide/arrays/codesnippet/CSharp/implicitly-typed-arrays_2.cs)]  
  
## <a name="see-also"></a>Consulte também  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
 [Variáveis Locais Tipadas Implicitamente](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md)  
 [Matrizes](../../../csharp/programming-guide/arrays/index.md)  
 [Tipos Anônimos](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)  
 [Inicializadores de objeto e coleção](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)  
 [var](../../../csharp/language-reference/keywords/var.md)  
 [Expressões de consulta LINQ](../../../csharp/programming-guide/linq-query-expressions/index.md)
