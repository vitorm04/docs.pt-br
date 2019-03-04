---
title: 'Como: implementar conversões definidas pelo usuário entre structs – Guia de Programação em C#'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- user-defined conversions [C#]
ms.assetid: 97839aef-8fbc-40d5-9769-6b569bc2710b
ms.openlocfilehash: bc792562b4849d402e03328e50dedac030520011
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/01/2019
ms.locfileid: "57201138"
---
# <a name="how-to-implement-user-defined-conversions-between-structs-c-programming-guide"></a>Como: implementar conversões definidas pelo usuário entre structs (Guia de Programação em C#)
Este exemplo define dois structs, `RomanNumeral` e `BinaryNumeral`, e demonstra conversões entre eles.  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[csProgGuideStatements#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#13)]  
  
## <a name="robust-programming"></a>Programação robusta  
  
-   No exemplo anterior, a instrução:  
  
     [!code-csharp[csProgGuideStatements#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#14)]  
  
     executa uma conversão de um `RomanNumeral` para um `BinaryNumeral`. Como não há nenhuma conversão direta de `RomanNumeral` para `BinaryNumeral`, uma conversão é usada para converter de um `RomanNumeral` para um `int` e outra conversão para converter de um `int` para um `BinaryNumeral`.  
  
-   Além disso, a instrução  
  
     [!code-csharp[csProgGuideStatements#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#15)]  
  
     executa uma conversão de um `BinaryNumeral` para um `RomanNumeral`. Como `RomanNumeral` define uma conversão implícita de `BinaryNumeral`, nenhuma conversão é necessária.  
  
## <a name="see-also"></a>Consulte também

- [Referência de C#](../../../csharp/language-reference/index.md)
- [Guia de Programação em C#](../../../csharp/programming-guide/index.md)
- [Operadores de conversão](../../../csharp/programming-guide/statements-expressions-operators/conversion-operators.md)
