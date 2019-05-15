---
title: 'Como: Consulta para o maior arquivo ou arquivos em uma árvore de diretório (LINQ) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 8c1c9f0c-95dd-4222-9be2-9ec026a13e81
ms.openlocfilehash: 91cfba02bade5811dbc5f45a5106731ff637efcf
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65593285"
---
# <a name="how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq-visual-basic"></a><span data-ttu-id="e7025-102">Como: Consulta para o maior arquivo ou arquivos em uma árvore de diretório (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e7025-102">How to: Query for the Largest File or Files in a Directory Tree (LINQ) (Visual Basic)</span></span>
<span data-ttu-id="e7025-103">Este exemplo mostra cinco consultas relacionadas ao tamanho do arquivo em bytes:</span><span class="sxs-lookup"><span data-stu-id="e7025-103">This example shows five queries related to file size in bytes:</span></span>  
  
- <span data-ttu-id="e7025-104">Como recuperar o tamanho em bytes do maior arquivo.</span><span class="sxs-lookup"><span data-stu-id="e7025-104">How to retrieve the size in bytes of the largest file.</span></span>  
  
- <span data-ttu-id="e7025-105">Como recuperar o tamanho em bytes do menor arquivo.</span><span class="sxs-lookup"><span data-stu-id="e7025-105">How to retrieve the size in bytes of the smallest file.</span></span>  
  
- <span data-ttu-id="e7025-106">Como recuperar o maior ou menor arquivo do objeto <xref:System.IO.FileInfo> de uma ou mais pastas em uma pasta raiz especificada.</span><span class="sxs-lookup"><span data-stu-id="e7025-106">How to retrieve the <xref:System.IO.FileInfo> object largest or smallest file from one or more folders under a specified root folder.</span></span>  
  
- <span data-ttu-id="e7025-107">Como recuperar uma sequência, como os 10 maiores arquivos.</span><span class="sxs-lookup"><span data-stu-id="e7025-107">How to retrieve a sequence such as the 10 largest files.</span></span>  
  
- <span data-ttu-id="e7025-108">Como ordenar os arquivos em grupos com base no tamanho do arquivo em bytes, ignorando arquivos menores do que um tamanho especificado.</span><span class="sxs-lookup"><span data-stu-id="e7025-108">How to order files into groups based on their file size in bytes, ignoring files that are less than a specified size.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e7025-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e7025-109">Example</span></span>  
 <span data-ttu-id="e7025-110">O exemplo a seguir contém cinco consultas separadas que mostram como consultar e agrupar arquivos, dependendo do tamanho do arquivo em bytes.</span><span class="sxs-lookup"><span data-stu-id="e7025-110">The following example contains five separate queries that show how to query and group files, depending on their file size in bytes.</span></span> <span data-ttu-id="e7025-111">Você pode modificar facilmente esses exemplos para basear a consulta em outra propriedade do objeto <xref:System.IO.FileInfo>.</span><span class="sxs-lookup"><span data-stu-id="e7025-111">You can easily modify these examples to base the query on some other property of the <xref:System.IO.FileInfo> object.</span></span>  
  
```vb  
Module QueryBySize  
    Sub Main()  
  
        ' Change the drive\path if necessary  
        Dim root As String = "C:\Program Files\Microsoft Visual Studio 9.0"  
  
        'Take a snapshot of the folder contents  
        Dim dir As New System.IO.DirectoryInfo(root)  
        Dim fileList = dir.GetFiles("*.*", System.IO.SearchOption.AllDirectories)  
  
        ' Return the size of the largest file  
        Dim maxSize = Aggregate aFile In fileList Into Max(GetFileLength(aFile))  
  
        'Dim maxSize = fileLengths.Max  
        Console.WriteLine("The length of the largest file under {0} is {1}", _  
                          root, maxSize)  
  
        ' Return the FileInfo object of the largest file  
        ' by sorting and selecting from the beginning of the list  
        Dim filesByLengDesc = From file In fileList _  
                              Let filelength = GetFileLength(file) _  
                              Where filelength > 0 _  
                              Order By filelength Descending _  
                              Select file  
  
        Dim longestFile = filesByLengDesc.First  
  
        Console.WriteLine("The largest file under {0} is {1} with a length of {2} bytes", _  
                          root, longestFile.FullName, longestFile.Length)  
  
        Dim smallestFile = filesByLengDesc.Last  
  
        Console.WriteLine("The smallest file under {0} is {1} with a length of {2} bytes", _  
                                root, smallestFile.FullName, smallestFile.Length)  
  
        ' Return the FileInfos for the 10 largest files  
        ' Based on a previous query, but nothing is executed  
        ' until the For Each statement below.  
        Dim tenLargest = From file In filesByLengDesc Take 10  
  
        Console.WriteLine("The 10 largest files under {0} are:", root)  
  
        For Each fi As System.IO.FileInfo In tenLargest  
            Console.WriteLine("{0}: {1} bytes", fi.FullName, fi.Length)  
        Next  
  
        ' Group files according to their size,  
        ' leaving out the ones under 200K  
        Dim sizeGroups = From file As System.IO.FileInfo In fileList _  
                         Where file.Length > 0 _  
                         Let groupLength = file.Length / 100000 _  
                         Group file By groupLength Into fileGroup = Group _  
                         Where groupLength >= 2 _  
                         Order By groupLength Descending  
  
        For Each group In sizeGroups  
            Console.WriteLine(group.groupLength + "00000")  
  
            For Each item As System.IO.FileInfo In group.fileGroup  
                Console.WriteLine("   {0}: {1}", item.Name, item.Length)  
            Next  
        Next  
  
        ' Keep the console window open in debug mode  
        Console.WriteLine("Press any key to exit.")  
        Console.ReadKey()  
  
    End Sub  
  
    ' This method is used to catch the possible exception  
    ' that can be raised when accessing the FileInfo.Length property.  
    ' In this particular case, it is safe to ignore the exception.  
    Function GetFileLength(ByVal fi As System.IO.FileInfo) As Long  
        Dim retval As Long  
        Try  
            retval = fi.Length  
        Catch ex As FileNotFoundException  
            ' If a file is no longer present,  
            ' just return zero bytes.   
            retval = 0  
        End Try  
  
        Return retval  
    End Function  
End Module  
```  
  
 <span data-ttu-id="e7025-112">Para retornar um ou mais objetos <xref:System.IO.FileInfo> completos, a consulta deve primeiro examinar cada um dos objetos na fonte de dados e, em seguida, classificá-los segundo o valor de sua propriedade Length.</span><span class="sxs-lookup"><span data-stu-id="e7025-112">To return one or more complete <xref:System.IO.FileInfo> objects, the query first must examine each one in the data source, and then sort them by the value of their Length property.</span></span> <span data-ttu-id="e7025-113">Em seguida, ela pode retornar um único elemento ou a sequência com os maiores tamanhos.</span><span class="sxs-lookup"><span data-stu-id="e7025-113">Then it can return the single one or the sequence with the greatest lengths.</span></span> <span data-ttu-id="e7025-114">Use <xref:System.Linq.Enumerable.First%2A> para retornar o primeiro elemento em uma lista.</span><span class="sxs-lookup"><span data-stu-id="e7025-114">Use <xref:System.Linq.Enumerable.First%2A> to return the first element in a list.</span></span> <span data-ttu-id="e7025-115">Use <xref:System.Linq.Enumerable.Take%2A> para retornar o primeiro número n de elementos.</span><span class="sxs-lookup"><span data-stu-id="e7025-115">Use <xref:System.Linq.Enumerable.Take%2A> to return the first n number of elements.</span></span> <span data-ttu-id="e7025-116">Especifique uma ordem de classificação decrescente para colocar os menores elementos no início da lista.</span><span class="sxs-lookup"><span data-stu-id="e7025-116">Specify a descending sort order to put the smallest elements at the start of the list.</span></span>  
  
 <span data-ttu-id="e7025-117">A consulta chama um método separado para obter o tamanho do arquivo em bytes para consumir a exceção possível que ocorrerá caso um arquivo tenha sido excluído em outro thread no período desde que o objeto <xref:System.IO.FileInfo> foi criado na chamada para `GetFiles`.</span><span class="sxs-lookup"><span data-stu-id="e7025-117">The query calls out to a separate method to obtain the file size in bytes in order to consume the possible exception that will be raised in the case where a file was deleted on another thread in the time period since the <xref:System.IO.FileInfo> object was created in the call to `GetFiles`.</span></span> <span data-ttu-id="e7025-118">Embora o objeto <xref:System.IO.FileInfo> já tenha sido criado, a exceção poderá ocorrer porque um objeto <xref:System.IO.FileInfo> tentará atualizar sua propriedade <xref:System.IO.FileInfo.Length%2A> usando o tamanho mais atual em bytes na primeira vez que a propriedade foi acessada.</span><span class="sxs-lookup"><span data-stu-id="e7025-118">Even through the <xref:System.IO.FileInfo> object has already been created, the exception can occur because a <xref:System.IO.FileInfo> object will try to refresh its <xref:System.IO.FileInfo.Length%2A> property by using the most current size in bytes the first time the property is accessed.</span></span> <span data-ttu-id="e7025-119">Ao colocar essa operação em um bloco try-catch fora da consulta, nós seguimos a regra de evitar operações em consultas que podem causar efeitos colaterais.</span><span class="sxs-lookup"><span data-stu-id="e7025-119">By putting this operation in a try-catch block outside the query, we follow the rule of avoiding operations in queries that can cause side-effects.</span></span> <span data-ttu-id="e7025-120">Em geral, deve-se ter muito cuidado ao consumir exceções para garantir que um aplicativo não seja deixado em um estado desconhecido.</span><span class="sxs-lookup"><span data-stu-id="e7025-120">In general, great care must be taken when consuming exceptions, to make sure that an application is not left in an unknown state.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e7025-121">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="e7025-121">Compiling the Code</span></span>  
<span data-ttu-id="e7025-122">Criar um projeto de aplicativo do console do VB.NET, com um `Imports` instrução para o namespace System. Linq.</span><span class="sxs-lookup"><span data-stu-id="e7025-122">Create a VB.NET console application project, with an `Imports` statement for the System.Linq namespace.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="e7025-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e7025-123">See also</span></span>

- [<span data-ttu-id="e7025-124">LINQ to Objects (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e7025-124">LINQ to Objects (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
- [<span data-ttu-id="e7025-125">LINQ e diretórios de arquivos (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e7025-125">LINQ and File Directories (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)
