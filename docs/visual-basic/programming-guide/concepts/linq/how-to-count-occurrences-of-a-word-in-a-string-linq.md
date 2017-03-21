---
title: "Como: contar as ocorrências de uma palavra em uma cadeia de caracteres (Visual Basic) (LINQ) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: bc367e46-f7cc-45f9-936f-754e661b7bb9
caps.latest.revision: 4
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 5ec6bb31fa095786f7c507a66e831a90fd1c6e92
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-count-occurrences-of-a-word-in-a-string-linq-visual-basic"></a>Como: contar as ocorrências de uma palavra em uma cadeia de caracteres (LINQ) (Visual Basic)
Este exemplo mostra como usar uma consulta LINQ para contar as ocorrências de uma palavra em uma cadeia de caracteres especificada. Observe que para executar a contagem, primeiro o <xref:System.String.Split%2A>método é chamado para criar uma matriz de palavras.</xref:System.String.Split%2A> Há um custo de desempenho para o <xref:System.String.Split%2A>método.</xref:System.String.Split%2A> Se for a única operação na cadeia de caracteres contar as palavras, você deve considerar o uso de <xref:System.Text.RegularExpressions.Regex.Matches%2A>ou <xref:System.String.IndexOf%2A>métodos em vez disso.</xref:System.String.IndexOf%2A> </xref:System.Text.RegularExpressions.Regex.Matches%2A> No entanto, se o desempenho não é um problema crítico ou dividir a sentença já a fim de executar outros tipos de consultas sobre ele, em seguida, faz sentido usar LINQ para contar as palavras ou frases bem.  
  
## <a name="example"></a>Exemplo  
  
```vb  
Class CountWords  
  
    Shared Sub Main()  
  
        Dim text As String = "Historically, the world of data and the world of objects" &   
                  " have not been well integrated. Programmers work in C# or Visual Basic" &   
                  " and also in SQL or XQuery. On the one side are concepts such as classes," &   
                  " objects, fields, inheritance, and .NET Framework APIs. On the other side" &   
                  " are tables, columns, rows, nodes, and separate languages for dealing with" &   
                  " them. Data types often require translation between the two worlds; there are" &   
                  " different standard functions. Because the object world has no notion of query, a" &   
                  " query can only be represented as a string without compile-time type checking or" &   
                  " IntelliSense support in the IDE. Transferring data from SQL tables or XML trees to" &   
                  " objects in memory is often tedious and error-prone."  
  
        Dim searchTerm As String = "data"  
  
        ' Convert the string into an array of words.  
        Dim dataSource As String() = text.Split(New Char() {" ", ",", ".", ";", ":"},   
                                                 StringSplitOptions.RemoveEmptyEntries)  
  
        ' Create and execute the query. It executes immediately   
        ' because a singleton value is produced.  
        ' Use ToLower to match "data" and "Data"   
        Dim matchQuery = From word In dataSource   
                      Where word.ToLowerInvariant() = searchTerm.ToLowerInvariant()   
                      Select word  
  
        ' Count the matches.  
        Dim count As Integer = matchQuery.Count()  
        Console.WriteLine(count & " occurrence(s) of the search term """ &   
                          searchTerm & """ were found.")  
  
        ' Keep console window open in debug mode.  
        Console.WriteLine("Press any key to exit.")  
        Console.ReadKey()  
    End Sub  
End Class  
' Output:  
' 3 occurrence(s) of the search term "data" were found.  
```  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Criar um projeto que tem como alvo o .NET Framework versão 3.5 ou superior com uma referência a System.Core.dll e uma `Imports` declaração para o namespace System. Linq.  
  
## <a name="see-also"></a>Consulte também  
 [LINQ e cadeias de caracteres (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)
