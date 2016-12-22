---
title: "Como retornar subconjuntos de propriedades de elementos em uma consulta (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "tipos anônimos [C#], para subconjuntos de propriedades de elemento"
ms.assetid: fabdf349-f443-4e3f-8368-6c471be1dd7b
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Como retornar subconjuntos de propriedades de elementos em uma consulta (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Use um tipo anônimo em uma expressão de consulta quando as duas condições se aplicam:  
  
-   Você deseja retornar apenas algumas das propriedades de cada elemento de origem.  
  
-   Não é necessário que armazenar os resultados da consulta fora do escopo do método no qual a consulta é executada.  
  
 Se você deseja apenas retornar uma propriedade ou campo de cada elemento de origem, você pode simplesmente usar o operador ponto no `select` cláusula.  Por exemplo, para retornar somente o `ID` de cada `student`, escrever o `select` cláusula da seguinte maneira:  
  
```  
select student.ID;  
```  
  
## Exemplo  
 O exemplo a seguir mostra como usar um tipo anônimo para retornar apenas um subconjunto das propriedades de cada elemento de origem que corresponda à condição especificada.  
  
 [!code-cs[csProgGuideLINQ#31](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-return-subsets-of-element-properties-in-a-query_1.cs)]  
  
 Observe que o tipo anônimo usa nomes do elemento de origem para suas propriedades, se nenhum nome for especificado.  Para fornecer novos nomes para as propriedades de tipo anônimo, escrever o `select` a instrução da seguinte maneira:  
  
```  
select new { First = student.FirstName, Last = student.LastName };  
```  
  
 Se você tentar fazer isso no exemplo anterior, em seguida, a `Console.WriteLine` também deve alterar a instrução:  
  
```  
Console.WriteLine(student.First + " " + student.Last);  
```  
  
## Compilando o código  
  
-   Para executar esse código, copiar e colar a classe em um Visual C\# projeto de aplicativo console que tenha sido criado em [!INCLUDE[vs_current_short](../../../csharp/programming-guide/classes-and-structs/includes/vs_current_short_md.md)].  Por padrão, esse projeto destina\-se a versão 3.5 da [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)], e ela terá uma referência a System.Core.dll e um `using` diretriz para System. LINQ.  Se um ou mais desses requisitos estão ausentes do projeto, você pode adicioná\-los manualmente.  Para obter mais informações, consulte [Como criar um projeto LINQ](../Topic/How%20to:%20Create%20a%20LINQ%20Project.md).  
  
## Consulte também  
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Tipos anônimos](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)   
 [Expressões de consulta LINQ](../../../csharp/programming-guide/linq-query-expressions/index.md)