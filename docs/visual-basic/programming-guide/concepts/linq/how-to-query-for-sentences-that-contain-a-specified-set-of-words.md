---
title: Como consultar sentenças que contenham um conjunto especificado de palavras (LINQ)
ms.date: 07/20/2015
ms.assetid: a5ae8ced-61fe-4c10-bb8a-95630e50f603
ms.openlocfilehash: 4a068f4f5500da5fd26e3dea753ec9591b6c7f5f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347682"
---
# <a name="how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq-visual-basic"></a>How to: Query for Sentences that Contain a Specified Set of Words (LINQ) (Visual Basic)

Este exemplo mostra como localizar frases em um arquivo de texto que contenham correspondências para cada conjunto de palavras especificado. Embora a matriz de termos de pesquisa esteja embutida em código neste exemplo, ela também poderia ser populada dinamicamente em runtime. Neste exemplo, a consulta retorna as frases que contêm as palavras "Historically", "data" e "integrated".

## <a name="example"></a>Exemplo

```vb
Class FindSentences

    Shared Sub Main()
        Dim text As String = "Historically, the world of data and the world of objects " &
        "have not been well integrated. Programmers work in C# or Visual Basic " &
        "and also in SQL or XQuery. On the one side are concepts such as classes, " &
        "objects, fields, inheritance, and .NET Framework APIs. On the other side " &
        "are tables, columns, rows, nodes, and separate languages for dealing with " &
        "them. Data types often require translation between the two worlds; there are " &
        "different standard functions. Because the object world has no notion of query, a " &
        "query can only be represented as a string without compile-time type checking or " &
        "IntelliSense support in the IDE. Transferring data from SQL tables or XML trees to " &
        "objects in memory is often tedious and error-prone."

        ' Split the text block into an array of sentences.
        Dim sentences As String() = text.Split(New Char() {".", "?", "!"})

        ' Define the search terms. This list could also be dynamically populated at runtime
        Dim wordsToMatch As String() = {"Historically", "data", "integrated"}

        ' Find sentences that contain all the terms in the wordsToMatch array
        ' Note that the number of terms to match is not specified at compile time
        Dim sentenceQuery = From sentence In sentences
                            Let w = sentence.Split(New Char() {" ", ",", ".", ";", ":"},
                                                   StringSplitOptions.RemoveEmptyEntries)
                            Where w.Distinct().Intersect(wordsToMatch).Count = wordsToMatch.Count()
                            Select sentence

        ' Execute the query
        For Each str As String In sentenceQuery
            Console.WriteLine(str)
        Next

        ' Keep console window open in debug mode.
        Console.WriteLine("Press any key to exit.")
        Console.ReadKey()
    End Sub

End Class
' Output:
' Historically, the world of data and the world of objects have not been well integrated
```

A consulta funciona primeiro dividindo o texto em frases e, em seguida, dividindo as sentenças em uma matriz de cadeias de caracteres que contêm cada palavra. Para cada uma dessas matrizes, o método <xref:System.Linq.Enumerable.Distinct%2A> remove todas as palavras duplicadas e, em seguida, a consulta executa uma operação <xref:System.Linq.Enumerable.Intersect%2A> na matriz de palavras e na matriz `wordsToMatch`. Se a contagem da interseção for igual à contagem da matriz `wordsToMatch`, todas as palavras foram encontradas nas palavras e a frase original será retornada.

Na chamada para <xref:System.String.Split%2A>, as marcas de pontuação são usadas como separadores para removê-las da cadeia de caracteres. Se não fizer isso, por exemplo, você poderia ter uma cadeia de caracteres "Historically" que não corresponderia a "Historically" na matriz `wordsToMatch`. Talvez você precise usar separadores adicionais, dependendo dos tipos de pontuação encontrados no texto de origem.

## <a name="compiling-the-code"></a>Compilando o código

Create a VB.NET console application project, with an `Imports` statement for the System.Linq namespace.

## <a name="see-also"></a>Consulte também

- [LINQ and Strings (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)
