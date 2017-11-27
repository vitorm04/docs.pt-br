---
title: "Como: consulta para o número Total de Bytes em um conjunto de pastas (LINQ) (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bfe85ed2-44dc-4ef1-aac7-241622b80a69
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b200581f4876400727c63e86e3ccf4a44c67914b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders-linq-visual-basic"></a><span data-ttu-id="2b312-102">Como: consulta para o número Total de Bytes em um conjunto de pastas (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2b312-102">How to: Query for the Total Number of Bytes in a Set of Folders (LINQ) (Visual Basic)</span></span>
<span data-ttu-id="2b312-103">Este exemplo mostra como recuperar o número total de bytes usado por todos os arquivos em uma pasta especificada e todas as suas subpastas.</span><span class="sxs-lookup"><span data-stu-id="2b312-103">This example shows how to retrieve the total number of bytes used by all the files in a specified folder and all its subfolders.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2b312-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2b312-104">Example</span></span>  
 <span data-ttu-id="2b312-105">O método <xref:System.Linq.Enumerable.Sum%2A> adiciona os valores de todos os itens selecionados na cláusula `select`.</span><span class="sxs-lookup"><span data-stu-id="2b312-105">The <xref:System.Linq.Enumerable.Sum%2A> method adds the values of all the items selected in the `select` clause.</span></span> <span data-ttu-id="2b312-106">Você pode modificar essa consulta para recuperar o maior ou o menor arquivo na árvore de diretório especificada chamando o método <xref:System.Linq.Enumerable.Min%2A> ou <xref:System.Linq.Enumerable.Max%2A> em vez de <xref:System.Linq.Enumerable.Sum%2A>.</span><span class="sxs-lookup"><span data-stu-id="2b312-106">You can easily modify this query to retrieve the biggest or smallest file in the specified directory tree by calling the <xref:System.Linq.Enumerable.Min%2A> or <xref:System.Linq.Enumerable.Max%2A> method instead of <xref:System.Linq.Enumerable.Sum%2A>.</span></span>  
  
```vb  
Module QueryTotalBytes  
    Sub Main()  
  
        ' Change the drive\path if necessary.  
        Dim root As String = "C:\Program Files\Microsoft Visual Studio 9.0\VB"  
  
        'Take a snapshot of the folder contents.  
        ' This method assumes that the application has discovery permissions  
        ' for all folders under the specified path.  
        Dim fileList = My.Computer.FileSystem.GetFiles _  
                  (root, FileIO.SearchOption.SearchAllSubDirectories, "*.*")  
  
        Dim fileQuery = From file In fileList _  
                        Select GetFileLength(file)  
  
        ' Force execution and cache the results to avoid multiple trips to the file system.  
        Dim fileLengths = fileQuery.ToArray()  
  
        ' Find the largest file  
        Dim maxSize = Aggregate aFile In fileLengths Into Max()  
  
        ' Find the total number of bytes  
        Dim totalBytes = Aggregate aFile In fileLengths Into Sum()  
  
        Console.WriteLine("The largest file is " & maxSize & " bytes")  
        Console.WriteLine("There are " & totalBytes & " total bytes in " & _  
                          fileList.Count & " files under " & root)  
  
        ' Keep the console window open in debug mode  
        Console.WriteLine("Press any key to exit.")  
        Console.ReadKey()  
    End Sub  
  
    ' This method is used to catch the possible exception  
    ' that can be raised when accessing the FileInfo.Length property.  
    Function GetFileLength(ByVal filename As String) As Long  
        Dim retval As Long  
        Try  
            Dim fi As New System.IO.FileInfo(filename)  
            retval = fi.Length  
        Catch ex As System.IO.FileNotFoundException  
            ' If a file is no longer present,  
            ' just return zero bytes.   
            retval = 0  
        End Try  
  
        Return retval  
    End Function  
End Module  
```  
  
 <span data-ttu-id="2b312-107">Se precisar apenas contar o número de bytes em uma árvore de diretório especificada, você pode fazer isso com mais eficiência sem criar uma consulta LINQ, que gera a sobrecarga de criação da coleção de lista como uma fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="2b312-107">If you only have to count the number of bytes in a specified directory tree, you can do this more efficiently without creating a LINQ query, which incurs the overhead of creating the list collection as a data source.</span></span> <span data-ttu-id="2b312-108">A utilidade da abordagem da LINQ aumenta conforme a consulta se torna mais complexa ou quando você precisa executar várias consultas na mesma fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="2b312-108">The usefulness of the LINQ approach increases as the query becomes more complex, or when you have to run multiple queries against the same data source.</span></span>  
  
 <span data-ttu-id="2b312-109">A consulta chama um método separado para obter o tamanho de arquivo.</span><span class="sxs-lookup"><span data-stu-id="2b312-109">The query calls out to a separate method to obtain the file length.</span></span> <span data-ttu-id="2b312-110">Ela faz isso para consumir a possível exceção que será gerada se o arquivo tiver sido excluído em outro thread após o objeto <xref:System.IO.FileInfo> ter sido criado na chamada para `GetFiles`.</span><span class="sxs-lookup"><span data-stu-id="2b312-110">It does this in order to consume the possible exception that will be raised if the file was deleted on another thread after the <xref:System.IO.FileInfo> object was created in the call to `GetFiles`.</span></span> <span data-ttu-id="2b312-111">Embora o objeto <xref:System.IO.FileInfo> já tenha sido criado, a exceção poderá ocorrer porque um objeto <xref:System.IO.FileInfo> tentará atualizar sua propriedade <xref:System.IO.FileInfo.Length%2A> com o tamanho mais atual na primeira vez que a propriedade foi acessada.</span><span class="sxs-lookup"><span data-stu-id="2b312-111">Even though the <xref:System.IO.FileInfo> object has already been created, the exception can occur because a <xref:System.IO.FileInfo> object will try to refresh its <xref:System.IO.FileInfo.Length%2A> property with the most current length the first time the property is accessed.</span></span> <span data-ttu-id="2b312-112">Ao colocar essa operação em um bloco try-catch fora da consulta, o código segue a regra de evitar operações em consultas que podem causar efeitos colaterais.</span><span class="sxs-lookup"><span data-stu-id="2b312-112">By putting this operation in a try-catch block outside the query, the code follows the rule of avoiding operations in queries that can cause side-effects.</span></span> <span data-ttu-id="2b312-113">Em geral, deve-se ter muito cuidado ao consumir exceções para garantir que um aplicativo não seja deixado em um estado desconhecido.</span><span class="sxs-lookup"><span data-stu-id="2b312-113">In general, great care must be taken when you consume exceptions to make sure that an application is not left in an unknown state.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="2b312-114">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="2b312-114">Compiling the Code</span></span>  
 <span data-ttu-id="2b312-115">Criar um projeto que tem como alvo o .NET Framework versão 3.5 ou superior com uma referência a System.Core.dll e um `Imports` declaração para o namespace System. Linq.</span><span class="sxs-lookup"><span data-stu-id="2b312-115">Create a project that targets the .NET Framework version 3.5 or higher with a reference to System.Core.dll and a   `Imports` statement for the System.Linq namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b312-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2b312-116">See Also</span></span>  
 [<span data-ttu-id="2b312-117">LINQ to Objects (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2b312-117">LINQ to Objects (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)  
 [<span data-ttu-id="2b312-118">LINQ e diretórios de arquivos (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2b312-118">LINQ and File Directories (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)
