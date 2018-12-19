---
title: 'Como: implementar conversões definidas pelo usuário entre structs – Guia de Programação em C#'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- user-defined conversions [C#]
ms.assetid: 97839aef-8fbc-40d5-9769-6b569bc2710b
ms.openlocfilehash: 85345203982679c0ab8dc9a6ae899312204c3230
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53241568"
---
# <a name="how-to-implement-user-defined-conversions-between-structs-c-programming-guide"></a>Como: implementar conversões definidas pelo usuário entre structs (Guia de Programação em C#)
Este exemplo define dois structs, `RomanNumeral` e `BinaryNumeral`, e demonstra conversões entre eles.  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[csProgGuideStatements#13](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-implement-user-defined-conversions-between-structs_1.cs)]  
  
## <a name="robust-programming"></a>Programação robusta  
  
-   No exemplo anterior, a instrução:  
  
     [!code-csharp[csProgGuideStatements#14](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-implement-user-defined-conversions-between-structs_2.cs)]  
  
     executa uma conversão de um `RomanNumeral` para um `BinaryNumeral`. Como não há nenhuma conversão direta de `RomanNumeral` para `BinaryNumeral`, uma conversão é usada para converter de um `RomanNumeral` para um `int` e outra conversão para converter de um `int` para um `BinaryNumeral`.  
  
-   Além disso, a instrução  
  
     [!code-csharp[csProgGuideStatements#15](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-implement-user-defined-conversions-between-structs_3.cs)]  
  
     executa uma conversão de um `BinaryNumeral` para um `RomanNumeral`. Como `RomanNumeral` define uma conversão implícita de `BinaryNumeral`, nenhuma conversão é necessária.  
  
## <a name="see-also"></a>Consulte também

- [Referência de C#](../../../csharp/language-reference/index.md)  
- [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
- [Operadores de conversão](../../../csharp/programming-guide/statements-expressions-operators/conversion-operators.md)
