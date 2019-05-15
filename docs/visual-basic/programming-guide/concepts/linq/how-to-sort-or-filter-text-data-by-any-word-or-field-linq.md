---
title: 'Como: Classificar ou filtrar dados de texto por qualquer palavra ou campo (LINQ) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 9df137fe-335b-46e0-aecf-ea8a9eddd4e3
ms.openlocfilehash: 5d6a8d26f28feafecfbddfb8d2b538adc22f1b90
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65592468"
---
# <a name="how-to-sort-or-filter-text-data-by-any-word-or-field-linq-visual-basic"></a>Como: Classificar ou filtrar dados de texto por qualquer palavra ou campo (LINQ) (Visual Basic)
O exemplo a seguir mostra como classificar linhas de texto estruturado, como valores separados por vírgulas, por qualquer campo na linha. O campo pode ser especificado dinamicamente em tempo de execução. Suponha que os campos em scores.csv representam o número de ID do aluno, seguido por uma série de quatro resultados de teste.  
  
### <a name="to-create-a-file-that-contains-data"></a>Para criar um arquivo que contém dados  
  
1. Copie os dados de scores.csv do tópico [Como: Unir conteúdo de arquivos diferentes (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-join-content-from-dissimilar-files-linq.md) e salvá-lo em sua pasta de solução.  
  
## <a name="example"></a>Exemplo  
  
```vb  
Class SortLines  
  
    Shared Sub Main()  
        Dim scores As String() = System.IO.File.ReadAllLines("../../../scores.csv")  
  
        ' Change this to any value from 0 to 4  
        Dim sortField As Integer = 1  
  
        Console.WriteLine("Sorted highest to lowest by field " & sortField)  
  
        ' Demonstrates how to return query from a method.  
        ' The query is executed here.  
        For Each str As String In SortQuery(scores, sortField)  
            Console.WriteLine(str)  
        Next  
  
        ' Keep console window open in debug mode.  
        Console.WriteLine("Press any key to exit.")  
        Console.ReadKey()  
  
    End Sub  
  
    Shared Function SortQuery(  
        ByVal source As IEnumerable(Of String),   
        ByVal num As Integer) As IEnumerable(Of String)  
  
        Dim scoreQuery = From line In source   
                         Let fields = line.Split(New Char() {","})   
                         Order By fields(num) Descending   
                         Select line  
  
        Return scoreQuery  
    End Function  
End Class  
' Output:  
' Sorted highest to lowest by field 1  
' 116, 99, 86, 90, 94  
' 120, 99, 82, 81, 79  
' 111, 97, 92, 81, 60  
' 114, 97, 89, 85, 82  
' 121, 96, 85, 91, 60  
' 122, 94, 92, 91, 91  
' 117, 93, 92, 80, 87  
' 118, 92, 90, 83, 78  
' 113, 88, 94, 65, 91  
' 112, 75, 84, 91, 39  
' 119, 68, 79, 88, 92  
' 115, 35, 72, 91, 70  
```  
  
 Este exemplo também demonstra como retornar uma variável de consulta de uma função.  
  
## <a name="compiling-the-code"></a>Compilando o código  
Criar um projeto de aplicativo do console do VB.NET, com um `Imports` instrução para o namespace System. Linq.
  
## <a name="see-also"></a>Consulte também

- [LINQ e cadeias de caracteres (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)
