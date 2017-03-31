---
title: "Como retornar subconjuntos de propriedades de elementos em uma consulta (Guia de programação em C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- anonymous types [C#], for subsets of element properties
ms.assetid: fabdf349-f443-4e3f-8368-6c471be1dd7b
caps.latest.revision: 11
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 3849d26506278fede6642530c60b6ec418f39464
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-return-subsets-of-element-properties-in-a-query-c-programming-guide"></a>Como retornar subconjuntos de propriedades de elementos em uma consulta (Guia de Programação em C#)
Use um tipo anônimo em uma expressão de consulta quando essas duas condições se aplicarem:  
  
-   Você deseja retornar apenas algumas das propriedades de cada elemento de origem.  
  
-   Você não precisa armazenar os resultados da consulta fora do escopo do método em que a consulta é executada.  
  
 Se você deseja retornar apenas uma propriedade ou campo de cada elemento de origem, use somente o operador de ponto na cláusula `select`. Por exemplo, para retornar somente a `ID` de cada `student`, escreva a cláusula `select` da seguinte maneira:  
  
```  
select student.ID;  
```  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar um tipo anônimo para retornar apenas um subconjunto das propriedades de cada elemento de origem que corresponda à condição especificada.  
  
 [!code-cs[csProgGuideLINQ#31](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-return-subsets-of-element-properties-in-a-query_1.cs)]  
  
 Observe que o tipo anônimo usa nomes do elemento de origem para suas propriedades, se nenhum nome for especificado. Para fornecer novos nomes para as propriedades no tipo anônimo, escreva a instrução `select` da seguinte maneira:  
  
```  
select new { First = student.FirstName, Last = student.LastName };  
```  
  
 Se você tentar fazer isso no exemplo anterior, a instrução `Console.WriteLine` também deve ser alterada:  
  
```  
Console.WriteLine(student.First + " " + student.Last);  
```  
  
## <a name="compiling-the-code"></a>Compilando o código  
  
-   Para executar esse código, copie e cole a classe em um projeto de aplicativo de console do Visual C# que foi criado no [!INCLUDE[vs_current_short](../../../csharp/programming-guide/classes-and-structs/includes/vs_current_short_md.md)]. Por padrão, esse projeto é direcionado para a versão 3.5 do [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] e ele terá uma referência ao System.Core.dll e uma diretriz `using` para System.Linq. Se um ou mais desses requisitos estiverem ausentes no projeto, você poderá adicioná-los manualmente.   
  
## <a name="see-also"></a>Consulte também  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Tipos Anônimos](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)   
 [Expressões de consulta LINQ](../../../csharp/programming-guide/linq-query-expressions/index.md)
