---
title: 'Como: Localizar a diferença definida entre as duas listas (LINQ) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: b5b25474-10a8-4df6-aab5-75621bb6b68e
ms.openlocfilehash: 3757a588ed37805d6dd2569e1d25b07bd166c2d5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59324052"
---
# <a name="how-to-find-the-set-difference-between-two-lists-linq-visual-basic"></a>Como: Localizar a diferença definida entre as duas listas (LINQ) (Visual Basic)
Este exemplo mostra como usar o LINQ para comparar duas listas de cadeias de caracteres e retornar as linhas que estão no names1.txt, mas não no names2.txt.  
  
### <a name="to-create-the-data-files"></a>Para criar os arquivos de dados  
  
1. Copie names1.txt e names2.txt para a pasta da solução, conforme mostrado em [Como: Combinar e comparar coleções de cadeia de caracteres (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-combine-and-compare-string-collections-linq.md).  
  
## <a name="example"></a>Exemplo  
  
```vb  
Class CompareLists  
  
    Shared Sub Main()  
  
        ' Create the IEnumerable data sources.  
        Dim names1 As String() = System.IO.File.ReadAllLines("../../../names1.txt")  
        Dim names2 As String() = System.IO.File.ReadAllLines("../../../names2.txt")  
  
        ' Create the query. Note that method syntax must be used here.  
        Dim differenceQuery = names1.Except(names2)  
        Console.WriteLine("The following lines are in names1.txt but not names2.txt")  
  
        ' Execute the query.  
        For Each name As String In differenceQuery  
            Console.WriteLine(name)  
        Next  
  
        ' Keep console window open in debug mode.  
        Console.WriteLine("Press any key to exit.")  
        Console.ReadKey()  
    End Sub  
End Class  
' Output:  
' The following lines are in names1.txt but not names2.txt  
' Potra, Cristina  
' Noriega, Fabricio  
' Aw, Kam Foo  
' Toyoshima, Tim  
' Guy, Wey Yuan  
' Garcia, Debra  
```  
  
 Alguns tipos de operações de consulta em Visual Basic, como <xref:System.Linq.Enumerable.Except%2A>, <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Union%2A>, e <xref:System.Linq.Enumerable.Concat%2A>, só podem ser expressas na sintaxe baseada em método.  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Crie um projeto que tenha como alvo o .NET Framework versão 3.5 ou posterior com uma referência a System.Core.dll e uma instrução `Imports` para o namespace System.Linq.  
  
## <a name="see-also"></a>Consulte também

- [LINQ e cadeias de caracteres (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)
