---
title: 'Como: Enumerar diretórios e arquivos'
ms.date: 12/27/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- I/O [.NET Framework], enumerating directories and files
ms.assetid: 86b69a08-3bfa-4e5f-b4e1-3b7cb8478215
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 863335cf080dbccd76b38c7222b74637b99ae2f0
ms.sourcegitcommit: 01ea420eaa4bf76d5fc47673294c8881379b3369
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/06/2019
ms.locfileid: "55758658"
---
# <a name="how-to-enumerate-directories-and-files"></a><span data-ttu-id="31b92-102">Como: Enumerar diretórios e arquivos</span><span class="sxs-lookup"><span data-stu-id="31b92-102">How to: Enumerate directories and files</span></span>
<span data-ttu-id="31b92-103">Coleções enumeráveis fornecem um desempenho melhor do que matrizes ao trabalhar com coleções grandes de arquivos e diretórios.</span><span class="sxs-lookup"><span data-stu-id="31b92-103">Enumerable collections provide better performance than arrays when you work with large collections of directories and files.</span></span> <span data-ttu-id="31b92-104">Para enumerar diretórios e arquivos, use métodos que retornam uma coleção enumerável de nomes de diretório ou arquivo ou seus objetos <xref:System.IO.DirectoryInfo>, <xref:System.IO.FileInfo> ou <xref:System.IO.FileSystemInfo>.</span><span class="sxs-lookup"><span data-stu-id="31b92-104">To enumerate directories and files, use methods that return an enumerable collection of directory or file names, or their <xref:System.IO.DirectoryInfo>, <xref:System.IO.FileInfo>, or <xref:System.IO.FileSystemInfo> objects.</span></span>  
  
<span data-ttu-id="31b92-105">Caso deseje pesquisar e retornar somente os nomes de diretórios ou arquivos, use os métodos de enumeração da classe <xref:System.IO.Directory>.</span><span class="sxs-lookup"><span data-stu-id="31b92-105">If you want to search and return only the names of directories or files, use the enumeration methods of the <xref:System.IO.Directory> class.</span></span> <span data-ttu-id="31b92-106">Caso deseje pesquisar e retornar outras propriedades de diretórios ou arquivos, use as classes <xref:System.IO.DirectoryInfo> e <xref:System.IO.FileSystemInfo>.</span><span class="sxs-lookup"><span data-stu-id="31b92-106">If you want to search and return other properties of directories or files, use the <xref:System.IO.DirectoryInfo> and <xref:System.IO.FileSystemInfo> classes.</span></span>  
  
<span data-ttu-id="31b92-107">Use coleções enumeráveis desses métodos como o parâmetro <xref:System.Collections.Generic.IEnumerable%601> para construtores de classes de coleção como <xref:System.Collections.Generic.List%601>.</span><span class="sxs-lookup"><span data-stu-id="31b92-107">You can use enumerable collections from these methods as the <xref:System.Collections.Generic.IEnumerable%601> parameter for constructors of collection classes like <xref:System.Collections.Generic.List%601>.</span></span>  
  
<span data-ttu-id="31b92-108">A seguinte tabela resume os métodos que retornam coleções enumeráveis de arquivos e diretórios:</span><span class="sxs-lookup"><span data-stu-id="31b92-108">The following table summarizes the methods that return enumerable collections of files and directories:</span></span>  
  
|<span data-ttu-id="31b92-109">Para pesquisar e retornar</span><span class="sxs-lookup"><span data-stu-id="31b92-109">To search and return</span></span>|<span data-ttu-id="31b92-110">Use o método</span><span class="sxs-lookup"><span data-stu-id="31b92-110">Use method</span></span>|  
|------------------|-------------------------------------|-------------------|  
|<span data-ttu-id="31b92-111">Nomes de diretório</span><span class="sxs-lookup"><span data-stu-id="31b92-111">Directory names</span></span>|<xref:System.IO.Directory.EnumerateDirectories%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="31b92-112">Informações de diretório (<xref:System.IO.DirectoryInfo>)</span><span class="sxs-lookup"><span data-stu-id="31b92-112">Directory information (<xref:System.IO.DirectoryInfo>)</span></span>|<xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="31b92-113">Nomes de arquivo</span><span class="sxs-lookup"><span data-stu-id="31b92-113">File names</span></span>|<xref:System.IO.Directory.EnumerateFiles%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="31b92-114">Informações do arquivo (<xref:System.IO.FileInfo>)</span><span class="sxs-lookup"><span data-stu-id="31b92-114">File information (<xref:System.IO.FileInfo>)</span></span>|<xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="31b92-115">Nomes de entrada do sistema de arquivos</span><span class="sxs-lookup"><span data-stu-id="31b92-115">File system entry names</span></span>|<xref:System.IO.Directory.EnumerateFileSystemEntries%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="31b92-116">Informações de entrada do sistema de arquivos (<xref:System.IO.FileSystemInfo>)</span><span class="sxs-lookup"><span data-stu-id="31b92-116">File system entry information (<xref:System.IO.FileSystemInfo>)</span></span>|<xref:System.IO.DirectoryInfo.EnumerateFileSystemInfos%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="31b92-117">Nomes de diretório e arquivo</span><span class="sxs-lookup"><span data-stu-id="31b92-117">Directory and file names</span></span> |<xref:System.IO.Directory.EnumerateFileSystemEntries%2A?displayProperty=nameWithType>|  

> [!NOTE]
> <span data-ttu-id="31b92-118">Embora você possa enumerar imediatamente todos os arquivos nos subdiretórios de um diretório pai usando a opção <xref:System.IO.SearchOption.AllDirectories> da enumeração <xref:System.IO.SearchOption> opcional, os erros <xref:System.UnauthorizedAccessException> podem tornar a enumeração incompleta.</span><span class="sxs-lookup"><span data-stu-id="31b92-118">Although you can immediately enumerate all the files in the subdirectories of a parent directory by using the <xref:System.IO.SearchOption.AllDirectories> option of the optional <xref:System.IO.SearchOption> enumeration, <xref:System.UnauthorizedAccessException> errors may make the enumeration incomplete.</span></span> <span data-ttu-id="31b92-119">Capture essas exceções enumerando primeiro os diretórios e, em seguida, os arquivos.</span><span class="sxs-lookup"><span data-stu-id="31b92-119">You can catch these exceptions by first enumerating directories and then enumerating files.</span></span>  
  
## <a name="examples-use-the-directory-class"></a><span data-ttu-id="31b92-120">Exemplos: Usar a classe Directory</span><span class="sxs-lookup"><span data-stu-id="31b92-120">Examples: Use the Directory class</span></span>  
  
<span data-ttu-id="31b92-121">O exemplo a seguir usa o método <xref:System.IO.Directory.EnumerateDirectories%28System.String%29?displayProperty=nameWithType> para obter uma lista dos nomes de diretório de nível superior em um caminho especificado.</span><span class="sxs-lookup"><span data-stu-id="31b92-121">The following example uses the <xref:System.IO.Directory.EnumerateDirectories%28System.String%29?displayProperty=nameWithType> method to get a list of the top-level directory names in a specified path.</span></span>  

[!code-csharp[System.IO.EnumDirs1#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.enumdirs1/cs/program.cs#1)]
[!code-vb[System.IO.EnumDirs1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.enumdirs1/vb/program.vb#1)]  

<span data-ttu-id="31b92-122">O exemplo a seguir usa o método <xref:System.IO.Directory.EnumerateFiles%28System.String%2CSystem.String%2CSystem.IO.SearchOption%29?displayProperty=nameWithType> para enumerar recursivamente todos os nomes de arquivo em um diretório e subdiretórios que correspondam a determinado padrão.</span><span class="sxs-lookup"><span data-stu-id="31b92-122">The following example uses the <xref:System.IO.Directory.EnumerateFiles%28System.String%2CSystem.String%2CSystem.IO.SearchOption%29?displayProperty=nameWithType> method to recursively enumerate all file names in a directory and subdirectories that match a certain pattern.</span></span> <span data-ttu-id="31b92-123">Em seguida, ele lê cada linha de cada arquivo e exibe as linhas que contêm uma cadeia de caracteres especificada, com seus nomes de arquivo e caminhos.</span><span class="sxs-lookup"><span data-stu-id="31b92-123">It then reads each line of each file and displays the lines that contain a specified string, with their filenames and paths.</span></span>

[!code-csharp[System.IO.Directory.EnumerateFiles#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directory.enumeratefiles/cs/program.cs#1)]
[!code-vb[System.IO.Directory.EnumerateFiles#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directory.enumeratefiles/vb/program.vb#1)]  
  
## <a name="examples-use-the-directoryinfo-class"></a><span data-ttu-id="31b92-124">Exemplos: Usar a classe DirectoryInfo</span><span class="sxs-lookup"><span data-stu-id="31b92-124">Examples: Use the DirectoryInfo class</span></span>  
  
<span data-ttu-id="31b92-125">O exemplo a seguir usa o método <xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=nameWithType> para listar uma coleção de diretórios de nível superior cuja <xref:System.IO.FileSystemInfo.CreationTimeUtc> é anterior a determinado valor <xref:System.DateTime>.</span><span class="sxs-lookup"><span data-stu-id="31b92-125">The following example uses the <xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=nameWithType> method to list a collection of top-level directories whose <xref:System.IO.FileSystemInfo.CreationTimeUtc> is earlier than a certain <xref:System.DateTime> value.</span></span>  

[!code-csharp[System.IO.DirectoryInfo.EnumDirs#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directoryinfo.enumdirs/cs/program.cs)]
[!code-vb[System.IO.DirectoryInfo.EnumDirs#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directoryinfo.enumdirs/vb/module1.vb)]  
  
<span data-ttu-id="31b92-126">O exemplo a seguir usa o método <xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=nameWithType> para listar todos os arquivos cujo <xref:System.IO.FileInfo.Length> excede 10 MB.</span><span class="sxs-lookup"><span data-stu-id="31b92-126">The following example uses the <xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=nameWithType> method to list all files whose <xref:System.IO.FileInfo.Length> exceeds 10MB.</span></span> <span data-ttu-id="31b92-127">Este exemplo enumera primeiro os diretórios de nível superior para capturar possíveis exceções de acesso não autorizado e, em seguida, enumera os arquivos.</span><span class="sxs-lookup"><span data-stu-id="31b92-127">This example first enumerates the top-level directories, to catch possible unauthorized access exceptions, and then enumerates the files.</span></span>  

[!code-csharp[System.IO.DirectoryInfo.EnumerateDirectories#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directoryinfo.enumeratedirectories/cs/program.cs#1)]
[!code-vb[System.IO.DirectoryInfo.EnumerateDirectories#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directoryinfo.enumeratedirectories/vb/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="31b92-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="31b92-128">See also</span></span>

- [<span data-ttu-id="31b92-129">E/S de arquivo e de fluxo</span><span class="sxs-lookup"><span data-stu-id="31b92-129">File and stream I/O</span></span>](../../../docs/standard/io/index.md)
