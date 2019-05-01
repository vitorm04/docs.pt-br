---
title: 'Como: Consultar arquivos com um atributo especificado ou o nome (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: b26026a3-3f43-448f-a582-259997af6be0
ms.openlocfilehash: 0c6875a0e4b8224010b20ca17ab6318387490aca
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62021356"
---
# <a name="how-to-query-for-files-with-a-specified-attribute-or-name-visual-basic"></a><span data-ttu-id="758a7-102">Como: Consultar arquivos com um atributo especificado ou o nome (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="758a7-102">How to: Query for Files with a Specified Attribute or Name (Visual Basic)</span></span>
<span data-ttu-id="758a7-103">Este exemplo mostra como localizar todos os arquivos que têm uma extensão de nome de arquivo especificada (por exemplo ".txt") em uma árvore de diretório especificada.</span><span class="sxs-lookup"><span data-stu-id="758a7-103">This example shows how to find all files that have a specified file name extension (for example ".txt") in a specified directory tree.</span></span> <span data-ttu-id="758a7-104">Ele também mostra como retornar tanto os arquivos mais recentes como os mais antigo na árvore com base na hora de criação.</span><span class="sxs-lookup"><span data-stu-id="758a7-104">It also shows how to return either the newest or oldest file in the tree based on the creation time.</span></span>  
  
## <a name="example"></a><span data-ttu-id="758a7-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="758a7-105">Example</span></span>  
  
```vb  
Module FindFileByExtension  
    Sub Main()  
  
        ' Change the drive\path if necessary  
        Dim root As String = "C:\Program Files\Microsoft Visual Studio 9.0"  
  
        'Take a snapshot of the folder contents  
        Dim dir As New System.IO.DirectoryInfo(root)  
  
        Dim fileList = dir.GetFiles("*.*", System.IO.SearchOption.AllDirectories)  
  
        ' This query will produce the full path for all .txt files  
        ' under the specified folder including subfolders.  
        ' It orders the list according to the file name.  
        Dim fileQuery = From file In fileList _  
                        Where file.Extension = ".txt" _  
                        Order By file.Name _  
                        Select file  
  
        For Each file In fileQuery  
            Console.WriteLine(file.FullName)  
        Next  
  
        ' Create and execute a new query by using  
        ' the previous query as a starting point.  
        ' fileQuery is not executed again until the  
        ' call to Last  
        Dim fileQuery2 = From file In fileQuery _  
                         Order By file.CreationTime _  
                         Select file.Name, file.CreationTime  
  
        ' Execute the query  
        Dim newestFile = fileQuery2.Last  
  
        Console.WriteLine("\r\nThe newest .txt file is {0}. Creation time: {1}", _  
                newestFile.Name, newestFile.CreationTime)  
  
        ' Keep the console window open in debug mode  
        Console.WriteLine("Press any key to exit.")  
        Console.ReadKey()  
  
    End Sub  
End Module  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="758a7-106">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="758a7-106">Compiling the Code</span></span>  
 <span data-ttu-id="758a7-107">Criar um projeto que tem como alvo o .NET Framework versão 3.5 ou posterior com uma referência à dll e um `Imports` instrução para o namespace System. Linq.</span><span class="sxs-lookup"><span data-stu-id="758a7-107">Create a project that targets the .NET Framework version 3.5 or higher with a reference to System.Core.dll and a   `Imports` statement for the System.Linq namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="758a7-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="758a7-108">See also</span></span>

- [<span data-ttu-id="758a7-109">LINQ to Objects (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="758a7-109">LINQ to Objects (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
- [<span data-ttu-id="758a7-110">LINQ e diretórios de arquivos (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="758a7-110">LINQ and File Directories (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)
