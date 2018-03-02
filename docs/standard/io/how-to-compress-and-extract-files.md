---
title: Como compactar e extrair arquivos
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- I/O [.NET Framework], compression
- compression
- compress files
ms.assetid: e9876165-3c60-4c84-a272-513e47acf579
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 33c9249692998aea8c22ddbf75a5a9b7bdf28708
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-compress-and-extract-files"></a><span data-ttu-id="183ad-102">Como compactar e extrair arquivos</span><span class="sxs-lookup"><span data-stu-id="183ad-102">How to: Compress and Extract Files</span></span>
<span data-ttu-id="183ad-103">O namespace <xref:System.IO.Compression> contém os seguintes tipos para compactar e descompactar arquivos e fluxos.</span><span class="sxs-lookup"><span data-stu-id="183ad-103">The <xref:System.IO.Compression> namespace contains the following types for compressing and decompressing files and streams.</span></span> <span data-ttu-id="183ad-104">Você também pode usar esses tipos para ler e modificar o conteúdo de um arquivo compactado:</span><span class="sxs-lookup"><span data-stu-id="183ad-104">You can also use these types to read and modify the contents of a compressed file:</span></span>  
  
-   <xref:System.IO.Compression.ZipFile>  
  
-   <xref:System.IO.Compression.ZipArchive>  
  
-   <xref:System.IO.Compression.ZipArchiveEntry>  
  
-   <xref:System.IO.Compression.DeflateStream>  
  
-   <xref:System.IO.Compression.GZipStream>  
  
 <span data-ttu-id="183ad-105">Os exemplos a seguir mostram algumas das funções que você pode executar ao trabalhar com arquivos compactados.</span><span class="sxs-lookup"><span data-stu-id="183ad-105">The following examples show some of the functions you can perform when working with compressed files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="183ad-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="183ad-106">Example</span></span>  
 <span data-ttu-id="183ad-107">Este exemplo mostra como criar e extrair um arquivo compactado que tenha uma extensão de nome de arquivo .zip usando a classe <xref:System.IO.Compression.ZipFile>.</span><span class="sxs-lookup"><span data-stu-id="183ad-107">This example shows how to create and extract a compressed file that has a .zip file name extension by using the <xref:System.IO.Compression.ZipFile> class.</span></span> <span data-ttu-id="183ad-108">Ele compacta o conteúdo de uma pasta em um novo arquivo .zip e extrai o conteúdo para uma nova pasta.</span><span class="sxs-lookup"><span data-stu-id="183ad-108">It compresses the contents of a folder into a new .zip file and then extracts that content to a new folder.</span></span> <span data-ttu-id="183ad-109">Para usar a classe <xref:System.IO.Compression.ZipFile>, você deve fazer referência ao assembly `System.IO.Compression.FileSystem` em seu projeto.</span><span class="sxs-lookup"><span data-stu-id="183ad-109">To use the <xref:System.IO.Compression.ZipFile> class, you must reference the `System.IO.Compression.FileSystem` assembly in your project.</span></span>  
  
 [!code-csharp[System.IO.Compression.ZipFile#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.zipfile/cs/program1.cs#1)]
 [!code-vb[System.IO.Compression.ZipFile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.zipfile/vb/program1.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="183ad-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="183ad-110">Example</span></span>  
 <span data-ttu-id="183ad-111">O exemplo a seguir mostra como iterar pelo conteúdo de um arquivo .zip e extrair os arquivos que tenham uma extensão .txt.</span><span class="sxs-lookup"><span data-stu-id="183ad-111">The next example shows how to iterate through the contents of an existing .zip file and extract files that have a .txt extension.</span></span> <span data-ttu-id="183ad-112">Ele usa a classe <xref:System.IO.Compression.ZipArchive> para acessar um arquivo .zip existente, e a classe <xref:System.IO.Compression.ZipArchiveEntry> para inspecionar as entradas individuais no arquivo compactado.</span><span class="sxs-lookup"><span data-stu-id="183ad-112">It uses the <xref:System.IO.Compression.ZipArchive> class to access an existing .zip file, and the <xref:System.IO.Compression.ZipArchiveEntry> class to inspect the individual entries in the compressed file.</span></span> <span data-ttu-id="183ad-113">Ele usa um método de extensão (<xref:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A>) para o objeto <xref:System.IO.Compression.ZipArchiveEntry>.</span><span class="sxs-lookup"><span data-stu-id="183ad-113">It uses an extension method (<xref:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A>) for the <xref:System.IO.Compression.ZipArchiveEntry> object.</span></span> <span data-ttu-id="183ad-114">O método de extensão está disponível na classe <xref:System.IO.Compression.ZipFileExtensions?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="183ad-114">The extension method is available in the <xref:System.IO.Compression.ZipFileExtensions?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="183ad-115">Para usar a classe <xref:System.IO.Compression.ZipFileExtensions>, você deve fazer referência ao assembly `System.IO.Compression.FileSystem` em seu projeto.</span><span class="sxs-lookup"><span data-stu-id="183ad-115">To use the <xref:System.IO.Compression.ZipFileExtensions> class, you must reference the `System.IO.Compression.FileSystem` assembly in your project.</span></span>  
  
 [!code-csharp[System.IO.Compression.ZipArchive#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchive/cs/program1.cs#1)]
 [!code-vb[System.IO.Compression.ZipArchive#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchive/vb/program1.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="183ad-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="183ad-116">Example</span></span>  
 <span data-ttu-id="183ad-117">O exemplo a seguir usa a classe <xref:System.IO.Compression.ZipArchive> para acessar um arquivo .zip existente, e adiciona um novo arquivo ao arquivo compactado.</span><span class="sxs-lookup"><span data-stu-id="183ad-117">The next example uses the <xref:System.IO.Compression.ZipArchive> class to access an existing .zip file, and adds a new file to the compressed file.</span></span> <span data-ttu-id="183ad-118">O novo arquivo é compactado quando você o adiciona ao arquivo .zip.</span><span class="sxs-lookup"><span data-stu-id="183ad-118">The new file gets compressed when you add it to the existing .zip file.</span></span>  
  
 [!code-csharp[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/cs/program1.cs#1)]
 [!code-vb[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/vb/program1.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="183ad-119">Exemplo</span><span class="sxs-lookup"><span data-stu-id="183ad-119">Example</span></span>  
 <span data-ttu-id="183ad-120">Você também pode usar as classes <xref:System.IO.Compression.GZipStream> e <xref:System.IO.Compression.DeflateStream> para compactar e descompactar dados.</span><span class="sxs-lookup"><span data-stu-id="183ad-120">You can also use the <xref:System.IO.Compression.GZipStream> and <xref:System.IO.Compression.DeflateStream> classes to compress and decompress data.</span></span> <span data-ttu-id="183ad-121">Elas usam o mesmo algoritmo de compactação.</span><span class="sxs-lookup"><span data-stu-id="183ad-121">They use the same compression algorithm.</span></span> <span data-ttu-id="183ad-122">Objetos <xref:System.IO.Compression.GZipStream> compactados que são gravados em um arquivo que tem uma extensão .gz podem ser descompactados usando várias ferramentas comuns, além dos métodos fornecidos por <xref:System.IO.Compression.GZipStream>.</span><span class="sxs-lookup"><span data-stu-id="183ad-122">Compressed <xref:System.IO.Compression.GZipStream> objects that are written to a file that has an extension of .gz can be decompressed by using many common tools in addition to the methods provided by <xref:System.IO.Compression.GZipStream>.</span></span> <span data-ttu-id="183ad-123">Este exemplo mostra como compactar e descompactar um diretório de arquivos usando a classe <xref:System.IO.Compression.GZipStream>.</span><span class="sxs-lookup"><span data-stu-id="183ad-123">This example shows how to compress and decompress a directory of files by using the <xref:System.IO.Compression.GZipStream> class.</span></span>  
  
 [!code-csharp[IO.Compression.GZip1#1](../../../samples/snippets/csharp/VS_Snippets_CLR/IO.Compression.GZip1/CS/gziptest.cs#1)]
 [!code-vb[IO.Compression.GZip1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/IO.Compression.GZip1/VB/gziptest.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="183ad-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="183ad-124">See Also</span></span>  
 <xref:System.IO.Compression.ZipArchive>  
 <xref:System.IO.Compression.ZipFile>  
 <xref:System.IO.Compression.ZipArchiveEntry>  
 <xref:System.IO.Compression.DeflateStream>  
 <xref:System.IO.Compression.GZipStream>  
 [<span data-ttu-id="183ad-125">E/S de arquivo e de fluxo</span><span class="sxs-lookup"><span data-stu-id="183ad-125">File and Stream I-O</span></span>](../../../docs/standard/io/index.md)
