---
title: "Como: consultar o maior arquivo ou arquivos em uma árvore de diretório (LINQ) (Visual Basic) | Documentos do Microsoft"
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
ms.assetid: 8c1c9f0c-95dd-4222-9be2-9ec026a13e81
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 95c5197b2cb66745201ceac89b78fe67b95ecb75
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq-visual-basic"></a><span data-ttu-id="665ce-102">Como: consultar o maior arquivo ou arquivos em uma árvore de diretório (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="665ce-102">How to: Query for the Largest File or Files in a Directory Tree (LINQ) (Visual Basic)</span></span>
<span data-ttu-id="665ce-103">Este exemplo mostra cinco consultas relacionadas ao tamanho do arquivo em bytes:</span><span class="sxs-lookup"><span data-stu-id="665ce-103">This example shows five queries related to file size in bytes:</span></span>  
  
-   <span data-ttu-id="665ce-104">Como recuperar o tamanho em bytes do arquivo maior.</span><span class="sxs-lookup"><span data-stu-id="665ce-104">How to retrieve the size in bytes of the largest file.</span></span>  
  
-   <span data-ttu-id="665ce-105">Como recuperar o tamanho em bytes do arquivo menor.</span><span class="sxs-lookup"><span data-stu-id="665ce-105">How to retrieve the size in bytes of the smallest file.</span></span>  
  
-   <span data-ttu-id="665ce-106">Como recuperar o <xref:System.IO.FileInfo>arquivo maior ou menor de objetos de uma ou mais pastas em uma pasta raiz especificada.</xref:System.IO.FileInfo></span><span class="sxs-lookup"><span data-stu-id="665ce-106">How to retrieve the <xref:System.IO.FileInfo> object largest or smallest file from one or more folders under a specified root folder.</span></span>  
  
-   <span data-ttu-id="665ce-107">Como recuperar uma sequência, como os 10 maiores arquivos.</span><span class="sxs-lookup"><span data-stu-id="665ce-107">How to retrieve a sequence such as the 10 largest files.</span></span>  
  
-   <span data-ttu-id="665ce-108">Como ordenar os arquivos em grupos com base em seu tamanho de arquivo em bytes, ignorando arquivos que são menores do que um tamanho especificado.</span><span class="sxs-lookup"><span data-stu-id="665ce-108">How to order files into groups based on their file size in bytes, ignoring files that are less than a specified size.</span></span>  
  
## <a name="example"></a><span data-ttu-id="665ce-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="665ce-109">Example</span></span>  
 <span data-ttu-id="665ce-110">O exemplo a seguir contém cinco consultas separadas que mostram como consultar e arquivos de grupo, dependendo do tamanho do arquivo em bytes.</span><span class="sxs-lookup"><span data-stu-id="665ce-110">The following example contains five separate queries that show how to query and group files, depending on their file size in bytes.</span></span> <span data-ttu-id="665ce-111">Você pode facilmente modificar esses exemplos para basear a consulta em outra propriedade do <xref:System.IO.FileInfo>objeto.</xref:System.IO.FileInfo></span><span class="sxs-lookup"><span data-stu-id="665ce-111">You can easily modify these examples to base the query on some other property of the <xref:System.IO.FileInfo> object.</span></span>  
  
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
  
 <span data-ttu-id="665ce-112">Para retornar a concluir uma ou mais <xref:System.IO.FileInfo>objetos, a consulta primeiro deve examinar cada um dos dados de origem e, em seguida, classificá-los pelo valor de sua propriedade Length.</xref:System.IO.FileInfo></span><span class="sxs-lookup"><span data-stu-id="665ce-112">To return one or more complete <xref:System.IO.FileInfo> objects, the query first must examine each one in the data source, and then sort them by the value of their Length property.</span></span> <span data-ttu-id="665ce-113">Em seguida, ele pode retornar uma única ou a sequência com os maiores tamanhos.</span><span class="sxs-lookup"><span data-stu-id="665ce-113">Then it can return the single one or the sequence with the greatest lengths.</span></span> <span data-ttu-id="665ce-114">Use <xref:System.Linq.Enumerable.First%2A>para retornar o primeiro elemento em uma lista.</xref:System.Linq.Enumerable.First%2A></span><span class="sxs-lookup"><span data-stu-id="665ce-114">Use <xref:System.Linq.Enumerable.First%2A> to return the first element in a list.</span></span> <span data-ttu-id="665ce-115">Use <xref:System.Linq.Enumerable.Take%2A>para retornar o primeiro número de n elementos.</xref:System.Linq.Enumerable.Take%2A></span><span class="sxs-lookup"><span data-stu-id="665ce-115">Use <xref:System.Linq.Enumerable.Take%2A> to return the first n number of elements.</span></span> <span data-ttu-id="665ce-116">Especifica uma ordem de classificação decrescente para colocar os elementos menor no início da lista.</span><span class="sxs-lookup"><span data-stu-id="665ce-116">Specify a descending sort order to put the smallest elements at the start of the list.</span></span>  
  
 <span data-ttu-id="665ce-117">A consulta chama um método separado para obter o tamanho do arquivo em bytes para consumir a possível exceção ocorrerá no caso em que um arquivo foi excluído em outro thread no período de tempo desde o <xref:System.IO.FileInfo>objeto foi criado na chamada para `GetFiles`.</xref:System.IO.FileInfo></span><span class="sxs-lookup"><span data-stu-id="665ce-117">The query calls out to a separate method to obtain the file size in bytes in order to consume the possible exception that will be raised in the case where a file was deleted on another thread in the time period since the <xref:System.IO.FileInfo> object was created in the call to `GetFiles`.</span></span> <span data-ttu-id="665ce-118">Embora o <xref:System.IO.FileInfo>objeto já foi criado, a exceção pode ocorrer porque um <xref:System.IO.FileInfo>objeto tentará atualizar seu <xref:System.IO.FileInfo.Length%2A>propriedade usando o tamanho máximo atual em bytes na primeira vez em que a propriedade é acessada.</xref:System.IO.FileInfo.Length%2A> </xref:System.IO.FileInfo> </xref:System.IO.FileInfo></span><span class="sxs-lookup"><span data-stu-id="665ce-118">Even through the <xref:System.IO.FileInfo> object has already been created, the exception can occur because a <xref:System.IO.FileInfo> object will try to refresh its <xref:System.IO.FileInfo.Length%2A> property by using the most current size in bytes the first time the property is accessed.</span></span> <span data-ttu-id="665ce-119">Ao colocar essa operação em um bloco try-catch fora da consulta, podemos seguir a regra de evitar operações em consultas que podem causar efeitos colaterais.</span><span class="sxs-lookup"><span data-stu-id="665ce-119">By putting this operation in a try-catch block outside the query, we follow the rule of avoiding operations in queries that can cause side-effects.</span></span> <span data-ttu-id="665ce-120">Em geral, ótimo deve ter cuidado ao consumir exceções, para certificar-se de que um aplicativo não seja deixado em um estado desconhecido.</span><span class="sxs-lookup"><span data-stu-id="665ce-120">In general, great care must be taken when consuming exceptions, to make sure that an application is not left in an unknown state.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="665ce-121">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="665ce-121">Compiling the Code</span></span>  
 <span data-ttu-id="665ce-122">Criar um projeto que tem como alvo o .NET Framework versão 3.5 ou superior com uma referência a System.Core.dll e uma `Imports` declaração para o namespace System. Linq.</span><span class="sxs-lookup"><span data-stu-id="665ce-122">Create a project that targets the .NET Framework version 3.5 or higher with a reference to System.Core.dll and a `Imports` statement for the System.Linq namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="665ce-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="665ce-123">See Also</span></span>  
 <span data-ttu-id="665ce-124">[LINQ to Objects (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md) </span><span class="sxs-lookup"><span data-stu-id="665ce-124">[LINQ to Objects (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md) </span></span>  
<span data-ttu-id="665ce-125"> [LINQ e diretórios de arquivos (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)</span><span class="sxs-lookup"><span data-stu-id="665ce-125"> [LINQ and File Directories (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)</span></span>
