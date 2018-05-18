---
title: Como executar conversão cast com segurança usando operadores as e is (Guia de Programação em C#)
ms.date: 07/20/2015
helpviewer_keywords:
- cast operators [C#], as and is operators
- as operator [C#]
- is operator [C#]
ms.assetid: c1176cea-1426-4a44-8570-3eadafa58863
ms.openlocfilehash: 6e02675a2a895add245d3c2e40305a0417fdf429
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-safely-cast-by-using-as-and-is-operators-c-programming-guide"></a>Como executar conversão cast com segurança usando operadores as e is (Guia de Programação em C#)
Como os objetos são polimórficos, é possível que uma variável de tipo de classe base mantenha um tipo derivado. Para acessar o método de tipo derivado, é necessário converter o valor de volta no tipo derivado. No entanto, tentar uma conversão simples nesses casos, cria o risco de lançar uma <xref:System.InvalidCastException>. Isso ocorre porque o C# fornece os operadores [is](../../../csharp/language-reference/keywords/is.md) e [as](../../../csharp/language-reference/keywords/as.md). É possível usar esses operadores para testar se uma conversão será bem-sucedida sem fazer com que uma exceção seja lançada. Em geral, o operador `as` é mais eficiente, porque ele realmente retornará o valor de conversão se a conversão puder ser realizada com êxito. O operador `is` retorna apenas um valor booliano. Portanto, ele poderá ser usado quando você desejar determinar o tipo de um objeto, mas não será necessário convertê-lo realmente.  
  
## <a name="example"></a>Exemplo  
 Os exemplos a seguir mostram como usar os operadores `is` e `as` para converter de um tipo de referência em outro sem o risco de lançar uma exceção. O exemplo também mostra como usar o operador `as` com tipos de valores anuláveis.  
  
 [!code-csharp[csProgGuideTypes#40](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-safely-cast-by-using-as-and-is-operators_1.cs)]  
  
## <a name="see-also"></a>Consulte também  
 [Tipos](../../../csharp/programming-guide/types/index.md)  
 [Transmissões e conversões de tipo](../../../csharp/programming-guide/types/casting-and-type-conversions.md)  
 [Tipos que permitem valor nulo](../../../csharp/programming-guide/nullable-types/index.md)
