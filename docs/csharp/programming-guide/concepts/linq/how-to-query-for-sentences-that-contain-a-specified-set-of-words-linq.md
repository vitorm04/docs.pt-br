---
title: "Como: consultar senten&#231;as que cont&#234;m um conjunto especificado de palavras (LINQ) (c#) | Microsoft Docs"
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
ms.assetid: 0724b429-4b87-4d26-a7b1-409358f3fc20
caps.latest.revision: 3
caps.handback.revision: 3
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Como: consultar senten&#231;as que cont&#234;m um conjunto especificado de palavras (LINQ) (c#)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Este exemplo mostra como localizar as frases em um arquivo de texto que contêm correspondências para cada um de um conjunto especificado de palavras. Embora a matriz de termos de pesquisa é embutida em código neste exemplo, ele poderia também ser preenchido dinamicamente em tempo de execução. Neste exemplo, a consulta retorna as sentenças que contêm as palavras "Historicamente", "dados" e "integrado".  
  
## Exemplo  
  
```c#  
class FindSentences  
{  
    static void Main()  
    {  
        string text = @"Historically, the world of data and the world of objects " +  
        @"have not been well integrated. Programmers work in C# or Visual Basic " +  
        @"and also in SQL or XQuery. On the one side are concepts such as classes, " +  
        @"objects, fields, inheritance, and .NET Framework APIs. On the other side " +  
        @"are tables, columns, rows, nodes, and separate languages for dealing with " +  
        @"them. Data types often require translation between the two worlds; there are " +  
        @"different standard functions. Because the object world has no notion of query, a " +  
        @"query can only be represented as a string without compile-time type checking or " +  
        @"IntelliSense support in the IDE. Transferring data from SQL tables or XML trees to " +  
        @"objects in memory is often tedious and error-prone.";  
  
        // Split the text block into an array of sentences.  
        string[] sentences = text.Split(new char[] { '.', '?', '!' });  
  
        // Define the search terms. This list could also be dynamically populated at runtime.  
        string[] wordsToMatch = { "Historically", "data", "integrated" };  
  
        // Find sentences that contain all the terms in the wordsToMatch array.  
        // Note that the number of terms to match is not specified at compile time.  
        var sentenceQuery = from sentence in sentences  
                            let w = sentence.Split(new char[] { '.', '?', '!', ' ', ';', ':', ',' },  
                                                    StringSplitOptions.RemoveEmptyEntries)  
                            where w.Distinct().Intersect(wordsToMatch).Count() == wordsToMatch.Count()  
                            select sentence;  
  
        // Execute the query. Note that you can explicitly type  
        // the iteration variable here even though sentenceQuery  
        // was implicitly typed.   
        foreach (string str in sentenceQuery)  
        {  
            Console.WriteLine(str);  
        }  
  
        // Keep the console window open in debug mode.  
        Console.WriteLine("Press any key to exit");  
        Console.ReadKey();  
    }  
}  
/* Output:  
Historically, the world of data and the world of objects have not been well integrated  
*/  
```  
  
 A consulta funciona primeiro dividindo o texto em sentenças, e, em seguida, dividindo as sentenças em uma matriz de cadeias de caracteres que contêm cada palavra. Para cada um desses conjuntos de <xref:System.Linq.Enumerable.Distinct%2A> método Remove todas as palavras duplicadas e, em seguida, executa a consulta um <xref:System.Linq.Enumerable.Intersect%2A> operação na matriz de word e o `wordsToMatch` matriz. Se a contagem de interseção é o mesmo que a contagem da `wordsToMatch` matriz, todas as palavras foram encontradas nas palavras e a frase original é retornada.  
  
 Na chamada para <xref:System.String.Split%2A>, as marcas de pontuação são usadas como separadores para removê\-los da cadeia de caracteres. Se você não fizer isso, por exemplo, você poderia ter uma cadeia de caracteres "Historicamente", que não corresponde a "Historicamente" no `wordsToMatch` matriz. Você talvez precise usar separadores adicionais, dependendo dos tipos de pontuação encontrado no texto de origem.  
  
## Compilando o código  
 Criar um projeto que tem como alvo o .NET Framework versão 3.5 ou posterior, com uma referência a System.Core.dll e `using` diretivas para os namespaces System. LINQ e System.IO.  
  
## Consulte também  
 [LINQ e cadeias de caracteres \(c\#\)](../../../../csharp/programming-guide/concepts/linq/linq-and-strings.md)