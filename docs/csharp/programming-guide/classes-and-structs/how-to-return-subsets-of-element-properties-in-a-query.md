---
title: 'Como: retornar subconjuntos de propriedades de elementos em uma consulta – Guia de Programação em C#'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- anonymous types [C#], for subsets of element properties
ms.assetid: fabdf349-f443-4e3f-8368-6c471be1dd7b
ms.openlocfilehash: da4ecb11c51f42c2297b6d40ed9a963590b3f441
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64599978"
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
  
- Para executar esse código, copie e cole a classe em um projeto de aplicativo de console do Visual C# que foi criado no Visual Studio. Por padrão, esse projeto é direcionado para a versão 3.5 do [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] e ele terá uma referência ao System.Core.dll e uma diretriz `using` para System.Linq. Se um ou mais desses requisitos estiverem ausentes no projeto, você poderá adicioná-los manualmente.   
  
## <a name="see-also"></a>Consulte também

- [Guia de Programação em C#](../../../csharp/programming-guide/index.md)
- [Tipos Anônimos](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)
- [Expressões de consulta LINQ](../../../csharp/programming-guide/linq-query-expressions/index.md)
