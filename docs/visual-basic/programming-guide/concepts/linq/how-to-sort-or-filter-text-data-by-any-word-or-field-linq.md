---
title: 'Como: classificar ou filtrar dados de texto por qualquer palavra ou campo (LINQ) (Visual Basic)'
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9df137fe-335b-46e0-aecf-ea8a9eddd4e3
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 19224bf51c95acdccbeb019631fdc884231610b4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-sort-or-filter-text-data-by-any-word-or-field-linq-visual-basic"></a><span data-ttu-id="0f361-102">Como: classificar ou filtrar dados de texto por qualquer palavra ou campo (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0f361-102">How to: Sort or Filter Text Data by Any Word or Field (LINQ) (Visual Basic)</span></span>
<span data-ttu-id="0f361-103">O exemplo a seguir mostra como classificar linhas de texto estruturado, como valores separados por vírgulas, por qualquer campo na linha.</span><span class="sxs-lookup"><span data-stu-id="0f361-103">The following example shows how to sort lines of structured text, such as comma-separated values, by any field in the line.</span></span> <span data-ttu-id="0f361-104">O campo pode ser especificado dinamicamente em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="0f361-104">The field may be dynamically specified at runtime.</span></span> <span data-ttu-id="0f361-105">Suponha que os campos em scores.csv representam o número de ID do aluno, seguido por uma série de quatro resultados de teste.</span><span class="sxs-lookup"><span data-stu-id="0f361-105">Assume that the fields in scores.csv represent a student's ID number, followed by a series of four test scores.</span></span>  
  
### <a name="to-create-a-file-that-contains-data"></a><span data-ttu-id="0f361-106">Para criar um arquivo que contém dados</span><span class="sxs-lookup"><span data-stu-id="0f361-106">To create a file that contains data</span></span>  
  
1.  <span data-ttu-id="0f361-107">Copiar os dados de scores.csv do tópico [como: unir conteúdo de arquivos diferentes (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-join-content-from-dissimilar-files-linq.md) e salvá-lo em sua pasta de solução.</span><span class="sxs-lookup"><span data-stu-id="0f361-107">Copy the scores.csv data from the topic [How to: Join Content from Dissimilar Files (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-join-content-from-dissimilar-files-linq.md) and save it to your solution folder.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0f361-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0f361-108">Example</span></span>  
  
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
  
 <span data-ttu-id="0f361-109">Este exemplo também demonstra como retornar uma variável de consulta de uma função.</span><span class="sxs-lookup"><span data-stu-id="0f361-109">This example also demonstrates how to return a query variable from a Function.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="0f361-110">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="0f361-110">Compiling the Code</span></span>  
 <span data-ttu-id="0f361-111">Crie um projeto que tenha como alvo o .NET Framework versão 3.5 ou posterior com uma referência a System.Core.dll e uma instrução `Imports` para o namespace System.Linq.</span><span class="sxs-lookup"><span data-stu-id="0f361-111">Create a project that targets the .NET Framework version 3.5 or higher with a reference to System.Core.dll and a `Imports` statement for the System.Linq namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f361-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0f361-112">See Also</span></span>  
 [<span data-ttu-id="0f361-113">LINQ e cadeias de caracteres (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0f361-113">LINQ and Strings (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)
