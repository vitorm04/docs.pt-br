---
title: "LINQ e diretórios de arquivos (Visual Basic) | Documentos do Microsoft"
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
ms.assetid: 159fd5c3-3926-4071-ae78-d8e423287eb7
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
ms.openlocfilehash: b9e814c9e9f8519522f288657d6940b07a0b3094
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="linq-and-file-directories-visual-basic"></a><span data-ttu-id="49735-102">LINQ e diretórios de arquivos (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="49735-102">LINQ and File Directories (Visual Basic)</span></span>
<span data-ttu-id="49735-103">Muitas operações de sistema de arquivos são essencialmente consultas e, portanto, são ideais para a abordagem do LINQ.</span><span class="sxs-lookup"><span data-stu-id="49735-103">Many file system operations are essentially queries and are therefore well-suited to the LINQ approach.</span></span>  
  
 <span data-ttu-id="49735-104">Observe que as consultas nesta seção são não-destrutiva.</span><span class="sxs-lookup"><span data-stu-id="49735-104">Note that the queries in this section are non-destructive.</span></span> <span data-ttu-id="49735-105">Eles não são usados para alterar o conteúdo dos arquivos originais ou pastas.</span><span class="sxs-lookup"><span data-stu-id="49735-105">They are not used to change the contents of the original files or folders.</span></span> <span data-ttu-id="49735-106">Isso segue a regra que consultas não devem causar efeitos colaterais.</span><span class="sxs-lookup"><span data-stu-id="49735-106">This follows the rule that queries should not cause any side-effects.</span></span> <span data-ttu-id="49735-107">Em geral, qualquer código (incluindo consultas que executam criarem / atualizam / excluir operadores) que modifica os dados de origem deve ser mantido separado do código que consulta apenas os dados.</span><span class="sxs-lookup"><span data-stu-id="49735-107">In general, any code (including queries that perform create / update / delete operators) that modifies source data should be kept separate from the code that just queries the data.</span></span>  
  
 <span data-ttu-id="49735-108">Esta seção contém os tópicos a seguir:</span><span class="sxs-lookup"><span data-stu-id="49735-108">This section contains the following topics:</span></span>  
  
 [<span data-ttu-id="49735-109">Como: consultar arquivos com um atributo especificado ou o nome (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="49735-109">How to: Query for Files with a Specified Attribute or Name (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-files-with-a-specified-attribute-or-name.md)  
 <span data-ttu-id="49735-110">Mostra como procurar arquivos examinando uma ou mais propriedades de seu <xref:System.IO.FileInfo>objeto.</xref:System.IO.FileInfo></span><span class="sxs-lookup"><span data-stu-id="49735-110">Shows how to search for files by examining one or more properties of its <xref:System.IO.FileInfo> object.</span></span>  
  
 [<span data-ttu-id="49735-111">Como: agrupar arquivos por extensão (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="49735-111">How to: Group Files by Extension (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-group-files-by-extension-linq.md)  
 <span data-ttu-id="49735-112">Mostra como retornar os grupos de <xref:System.IO.FileInfo>objeto com base em sua extensão de nome de arquivo.</xref:System.IO.FileInfo></span><span class="sxs-lookup"><span data-stu-id="49735-112">Shows how to return groups of <xref:System.IO.FileInfo> object based on their file name extension.</span></span>  
  
 [<span data-ttu-id="49735-113">Como: consultar o número Total de Bytes em um conjunto de pastas (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="49735-113">How to: Query for the Total Number of Bytes in a Set of Folders (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders.md)  
 <span data-ttu-id="49735-114">Mostra como retornar o número total de bytes em todos os arquivos em uma árvore de diretório especificado.</span><span class="sxs-lookup"><span data-stu-id="49735-114">Shows how to return the total number of bytes in all the files in a specified directory tree.</span></span>  
  
 <span data-ttu-id="49735-115">[Como: comparar o conteúdo de duas pastas (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-compare-the-contents-of-two-folders-linq.md)s</span><span class="sxs-lookup"><span data-stu-id="49735-115">[How to: Compare the Contents of Two Folders (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-compare-the-contents-of-two-folders-linq.md)s</span></span>  
 <span data-ttu-id="49735-116">Mostra como retornar todos os arquivos que estão presentes em duas pastas especificadas e também todos os arquivos que estão presentes em uma pasta, mas não o outro.</span><span class="sxs-lookup"><span data-stu-id="49735-116">Shows how to return all the files that are present in two specified folders, and also all the files that are present in one folder but not the other.</span></span>  
  
 [<span data-ttu-id="49735-117">Como: consultar o maior arquivo ou arquivos em uma árvore de diretório (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="49735-117">How to: Query for the Largest File or Files in a Directory Tree (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-the-largest-file-or-files-in-a-directory-tree.md)  
 <span data-ttu-id="49735-118">Mostra como retornar o arquivo maior ou menor, ou um número especificado de arquivos, em uma árvore de diretório.</span><span class="sxs-lookup"><span data-stu-id="49735-118">Shows how to return the largest or smallest file, or a specified number of files, in a directory tree.</span></span>  
  
 [<span data-ttu-id="49735-119">Como: consultar arquivos duplicados em uma árvore de diretório (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="49735-119">How to: Query for Duplicate Files in a Directory Tree (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-duplicate-files-in-a-directory-tree-linq.md)  
 <span data-ttu-id="49735-120">Mostra como agrupar todos os nomes de arquivo que ocorrem em mais de um local em uma árvore de diretório especificado.</span><span class="sxs-lookup"><span data-stu-id="49735-120">Shows how to group for all file names that occur in more than one location in a specified directory tree.</span></span> <span data-ttu-id="49735-121">Também mostra como executar comparações mais complexas com base em um comparador personalizado.</span><span class="sxs-lookup"><span data-stu-id="49735-121">Also shows how to perform more complex comparisons based on a custom comparer.</span></span>  
  
 [<span data-ttu-id="49735-122">Como: consultar o conteúdo de arquivos em uma pasta (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="49735-122">How to: Query the Contents of Files in a Folder (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-the-contents-of-files-in-a-folder-linq.md)  
 <span data-ttu-id="49735-123">Mostra como iterar através de pastas em uma árvore, abra cada arquivo e consultar o conteúdo do arquivo.</span><span class="sxs-lookup"><span data-stu-id="49735-123">Shows how to iterate through folders in a tree, open each file, and query the file's contents.</span></span>  
  
## <a name="comments"></a><span data-ttu-id="49735-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="49735-124">Comments</span></span>  
 <span data-ttu-id="49735-125">Há alguma complexidade envolvida na criação de uma fonte de dados que representa o conteúdo do sistema de arquivos com precisão e lida com exceções normalmente.</span><span class="sxs-lookup"><span data-stu-id="49735-125">There is some complexity involved in creating a data source that accurately represents the contents of the file system and handles exceptions gracefully.</span></span> <span data-ttu-id="49735-126">Os exemplos nesta seção criam uma coleção de instantâneo de <xref:System.IO.FileInfo>objetos que representa todos os arquivos em uma pasta raiz especificada e todas as suas subpastas.</xref:System.IO.FileInfo></span><span class="sxs-lookup"><span data-stu-id="49735-126">The examples in this section create a snapshot collection of <xref:System.IO.FileInfo> objects that represents all the files under a specified root folder and all its subfolders.</span></span> <span data-ttu-id="49735-127">O estado real de cada <xref:System.IO.FileInfo>pode ser alterado no tempo entre quando você começa e terminar a execução de uma consulta.</xref:System.IO.FileInfo></span><span class="sxs-lookup"><span data-stu-id="49735-127">The actual state of each <xref:System.IO.FileInfo> may change in the time between when you begin and end executing a query.</span></span> <span data-ttu-id="49735-128">Por exemplo, você pode criar uma lista de <xref:System.IO.FileInfo>objetos para usar como uma fonte de dados.</xref:System.IO.FileInfo></span><span class="sxs-lookup"><span data-stu-id="49735-128">For example, you can create a list of <xref:System.IO.FileInfo> objects to use as a data source.</span></span> <span data-ttu-id="49735-129">Se você tentar acessar o `Length` propriedade em uma consulta, o <xref:System.IO.FileInfo>objeto tentará acessar o sistema de arquivos para atualizar o valor de `Length`.</xref:System.IO.FileInfo></span><span class="sxs-lookup"><span data-stu-id="49735-129">If you try to access the `Length` property in a query, the <xref:System.IO.FileInfo> object will try to access the file system to update the value of `Length`.</span></span> <span data-ttu-id="49735-130">Se o arquivo não existir, você obterá uma <xref:System.IO.FileNotFoundException>em sua consulta, embora não consultar o sistema de arquivos diretamente.</xref:System.IO.FileNotFoundException></span><span class="sxs-lookup"><span data-stu-id="49735-130">If the file no longer exists, you will get a <xref:System.IO.FileNotFoundException> in your query, even though you are not querying the file system directly.</span></span> <span data-ttu-id="49735-131">Algumas consultas nesta seção usam um método separado que consome essas exceções específicas em determinados casos.</span><span class="sxs-lookup"><span data-stu-id="49735-131">Some queries in this section use a separate method that consumes these particular exceptions in certain cases.</span></span> <span data-ttu-id="49735-132">Outra opção é manter a fonte de dados atualizada dinamicamente usando <xref:System.IO.FileSystemWatcher>.</xref:System.IO.FileSystemWatcher></span><span class="sxs-lookup"><span data-stu-id="49735-132">Another option is to keep your data source updated dynamically by using the <xref:System.IO.FileSystemWatcher>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49735-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="49735-133">See Also</span></span>  
 [<span data-ttu-id="49735-134">LINQ to Objects (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="49735-134">LINQ to Objects (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
