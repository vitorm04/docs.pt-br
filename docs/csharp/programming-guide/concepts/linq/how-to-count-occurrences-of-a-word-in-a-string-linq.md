---
title: "Como: contar as ocorr&#234;ncias de uma palavra em uma cadeia de caracteres (LINQ) (c#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
ms.assetid: f8e6f546-7c14-4aa1-8a75-e8d09f3b8ccd
caps.latest.revision: 4
caps.handback.revision: 4
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Como: contar as ocorr&#234;ncias de uma palavra em uma cadeia de caracteres (LINQ) (c#)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Este exemplo mostra como usar uma consulta LINQ para contar as ocorrências de uma palavra em uma cadeia de caracteres especificada. Observe que para executar a contagem, primeiro o <xref:System.String.Split%2A> método é chamado para criar uma matriz de palavras. Há um custo de desempenho para o <xref:System.String.Split%2A> método. Se for a única operação na cadeia de caracteres contar as palavras, você deve considerar o uso de <xref:System.Text.RegularExpressions.Regex.Matches%2A> ou <xref:System.String.IndexOf%2A> métodos em vez disso. No entanto, se o desempenho não é um problema crítico ou dividir a sentença já a fim de executar outros tipos de consultas sobre ele, em seguida, faz sentido usar LINQ para contar as palavras ou frases bem.  
  
## Exemplo  
  
```c#  
class CountWords  
{  
    static void Main()  
    {  
        string text = @"Historically, the world of data and the world of objects" +  
          @" have not been well integrated. Programmers work in C# or Visual Basic" +  
          @" and also in SQL or XQuery. On the one side are concepts such as classes," +  
          @" objects, fields, inheritance, and .NET Framework APIs. On the other side" +  
          @" are tables, columns, rows, nodes, and separate languages for dealing with" +  
          @" them. Data types often require translation between the two worlds; there are" +  
          @" different standard functions. Because the object world has no notion of query, a" +  
          @" query can only be represented as a string without compile-time type checking or" +  
          @" IntelliSense support in the IDE. Transferring data from SQL tables or XML trees to" +  
          @" objects in memory is often tedious and error-prone.";  
  
        string searchTerm = "data";  
  
        //Convert the string into an array of words  
        string[] source = text.Split(new char[] { '.', '?', '!', ' ', ';', ':', ',' }, StringSplitOptions.RemoveEmptyEntries);  
  
        // Create the query.  Use ToLowerInvariant to match "data" and "Data"   
        var matchQuery = from word in source  
                         where word.ToLowerInvariant() == searchTerm.ToLowerInvariant()  
                         select word;  
  
        // Count the matches, which executes the query.  
        int wordCount = matchQuery.Count();  
        Console.WriteLine("{0} occurrences(s) of the search term \"{1}\" were found.", wordCount, searchTerm);  
  
        // Keep console window open in debug mode  
        Console.WriteLine("Press any key to exit");  
        Console.ReadKey();  
    }  
}  
/* Output:  
   3 occurrences(s) of the search term "data" were found.  
*/  
```  
  
## Compilando o código  
 Criar um projeto que tem como alvo o .NET Framework versão 3.5 ou posterior, com uma referência a System.Core.dll e `using` diretivas para os namespaces System. LINQ e System.IO.  
  
## Consulte também  
 [LINQ e cadeias de caracteres \(c\#\)](../../../../csharp/programming-guide/concepts/linq/linq-and-strings.md)