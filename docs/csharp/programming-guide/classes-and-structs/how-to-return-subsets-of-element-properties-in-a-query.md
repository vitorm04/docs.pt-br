---
title: 'Como: retornar subconjuntos de propriedades de elementos em uma consulta – Guia de Programação em C#'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- anonymous types [C#], for subsets of element properties
ms.assetid: fabdf349-f443-4e3f-8368-6c471be1dd7b
ms.openlocfilehash: acff804d87d67bf8758b97ad04805359bb3f2e32
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65586072"
---
# <a name="how-to-return-subsets-of-element-properties-in-a-query-c-programming-guide"></a>Como: retornar subconjuntos de propriedades de elementos em uma consulta (Guia de Programação em C#)
Use um tipo anônimo em uma expressão de consulta quando essas duas condições se aplicarem:  
  
- Você deseja retornar apenas algumas das propriedades de cada elemento de origem.  
  
- Você não precisa armazenar os resultados da consulta fora do escopo do método em que a consulta é executada.  
  
 Se você deseja retornar apenas uma propriedade ou campo de cada elemento de origem, use somente o operador de ponto na cláusula `select`. Por exemplo, para retornar somente a `ID` de cada `student`, escreva a cláusula `select` da seguinte maneira:  
  
```  
select student.ID;  
```  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar um tipo anônimo para retornar apenas um subconjunto das propriedades de cada elemento de origem que corresponda à condição especificada.  
  
 [!code-csharp[csProgGuideLINQ#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#31)]  
  
 Observe que o tipo anônimo usa nomes do elemento de origem para suas propriedades, se nenhum nome for especificado. Para fornecer novos nomes para as propriedades no tipo anônimo, escreva a instrução `select` da seguinte maneira:  
  
```  
select new { First = student.FirstName, Last = student.LastName };  
```  
  
 Se você tentar fazer isso no exemplo anterior, a instrução `Console.WriteLine` também deve ser alterada:  
  
```csharp  
Console.WriteLine(student.First + " " + student.Last);  
```  
  
## <a name="compiling-the-code"></a>Compilando o código  
  
Para executar esse código, copie e cole a classe em um aplicativo de console em C# com uma diretiva `using` para System.Linq.
  
## <a name="see-also"></a>Consulte também

- [Guia de Programação em C#](../../../csharp/programming-guide/index.md)
- [Tipos Anônimos](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)
- [Expressões de consulta LINQ](../../../csharp/programming-guide/linq-query-expressions/index.md)
