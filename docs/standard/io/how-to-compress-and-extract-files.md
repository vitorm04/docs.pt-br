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
caps.latest.revision: "19"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 22a95ce18b602d4e329499c5d36557213e08a8b5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-compress-and-extract-files"></a><span data-ttu-id="bc7cf-102">Como compactar e extrair arquivos</span><span class="sxs-lookup"><span data-stu-id="bc7cf-102">How to: Compress and Extract Files</span></span>
<span data-ttu-id="bc7cf-103">O <xref:System.IO.Compression> namespace contém os tipos a seguir para compactar e descompactar os arquivos e fluxos.</span><span class="sxs-lookup"><span data-stu-id="bc7cf-103">The <xref:System.IO.Compression> namespace contains the following types for compressing and decompressing files and streams.</span></span> <span data-ttu-id="bc7cf-104">Você também pode usar esses tipos para ler e modificar o conteúdo de um arquivo compactado:</span><span class="sxs-lookup"><span data-stu-id="bc7cf-104">You can also use these types to read and modify the contents of a compressed file:</span></span>  
  
-   <xref:System.IO.Compression.ZipFile>  
  
-   <xref:System.IO.Compression.ZipArchive>  
  
-   <xref:System.IO.Compression.ZipArchiveEntry>  
  
-   <xref:System.IO.Compression.DeflateStream>  
  
-   <xref:System.IO.Compression.GZipStream>  
  
 <span data-ttu-id="bc7cf-105">Os exemplos a seguir mostram algumas das funções que você pode executar ao trabalhar com arquivos compactados.</span><span class="sxs-lookup"><span data-stu-id="bc7cf-105">The following examples show some of the functions you can perform when working with compressed files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bc7cf-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bc7cf-106">Example</span></span>  
 <span data-ttu-id="bc7cf-107">Este exemplo mostra como criar e extrair um arquivo compactado com uma extensão de nome de arquivo. zip usando o <xref:System.IO.Compression.ZipFile> classe.</span><span class="sxs-lookup"><span data-stu-id="bc7cf-107">This example shows how to create and extract a compressed file that has a .zip file name extension by using the <xref:System.IO.Compression.ZipFile> class.</span></span> <span data-ttu-id="bc7cf-108">Compacta o conteúdo de uma pasta em um novo arquivo. zip e extrai o conteúdo para uma nova pasta.</span><span class="sxs-lookup"><span data-stu-id="bc7cf-108">It compresses the contents of a folder into a new .zip file and then extracts that content to a new folder.</span></span> <span data-ttu-id="bc7cf-109">Para usar o <xref:System.IO.Compression.ZipFile> classe, você deve fazer referência a `System.IO.Compression.FileSystem` assembly em seu projeto.</span><span class="sxs-lookup"><span data-stu-id="bc7cf-109">To use the <xref:System.IO.Compression.ZipFile> class, you must reference the `System.IO.Compression.FileSystem` assembly in your project.</span></span>  
  
 [!code-csharp[System.IO.Compression.ZipFile#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.zipfile/cs/program1.cs#1)]
 [!code-vb[System.IO.Compression.ZipFile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.zipfile/vb/program1.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="bc7cf-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bc7cf-110">Example</span></span>  
 <span data-ttu-id="bc7cf-111">O exemplo a seguir mostra como percorrer o conteúdo de um arquivo. zip e extraia os arquivos que têm uma extensão. txt.</span><span class="sxs-lookup"><span data-stu-id="bc7cf-111">The next example shows how to iterate through the contents of an existing .zip file and extract files that have a .txt extension.</span></span> <span data-ttu-id="bc7cf-112">Ele usa o <xref:System.IO.Compression.ZipArchive> classe para acessar um arquivo. zip existente e o <xref:System.IO.Compression.ZipArchiveEntry> classe para inspecionar as entradas individuais no arquivo compactado.</span><span class="sxs-lookup"><span data-stu-id="bc7cf-112">It uses the <xref:System.IO.Compression.ZipArchive> class to access an existing .zip file, and the <xref:System.IO.Compression.ZipArchiveEntry> class to inspect the individual entries in the compressed file.</span></span> <span data-ttu-id="bc7cf-113">Ele usa um método de extensão (<xref:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A>) para o <xref:System.IO.Compression.ZipArchiveEntry> objeto.</span><span class="sxs-lookup"><span data-stu-id="bc7cf-113">It uses an extension method (<xref:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A>) for the <xref:System.IO.Compression.ZipArchiveEntry> object.</span></span> <span data-ttu-id="bc7cf-114">O método de extensão está disponível na <xref:System.IO.Compression.ZipFileExtensions?displayProperty=nameWithType> classe.</span><span class="sxs-lookup"><span data-stu-id="bc7cf-114">The extension method is available in the <xref:System.IO.Compression.ZipFileExtensions?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="bc7cf-115">Para usar o <xref:System.IO.Compression.ZipFileExtensions> classe, você deve fazer referência a `System.IO.Compression.FileSystem` assembly em seu projeto.</span><span class="sxs-lookup"><span data-stu-id="bc7cf-115">To use the <xref:System.IO.Compression.ZipFileExtensions> class, you must reference the `System.IO.Compression.FileSystem` assembly in your project.</span></span>  
  
 [!code-csharp[System.IO.Compression.ZipArchive#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchive/cs/program1.cs#1)]
 [!code-vb[System.IO.Compression.ZipArchive#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchive/vb/program1.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="bc7cf-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bc7cf-116">Example</span></span>  
 <span data-ttu-id="bc7cf-117">O exemplo a seguir usa o <xref:System.IO.Compression.ZipArchive> de classe para acessar um arquivo. zip existente e adiciona um novo arquivo para o arquivo compactado.</span><span class="sxs-lookup"><span data-stu-id="bc7cf-117">The next example uses the <xref:System.IO.Compression.ZipArchive> class to access an existing .zip file, and adds a new file to the compressed file.</span></span> <span data-ttu-id="bc7cf-118">O novo arquivo obtém compactado quando você adicioná-lo para o arquivo. zip.</span><span class="sxs-lookup"><span data-stu-id="bc7cf-118">The new file gets compressed when you add it to the existing .zip file.</span></span>  
  
 [!code-csharp[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/cs/program1.cs#1)]
 [!code-vb[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/vb/program1.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="bc7cf-119">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bc7cf-119">Example</span></span>  
 <span data-ttu-id="bc7cf-120">Você também pode usar o <xref:System.IO.Compression.GZipStream> e <xref:System.IO.Compression.DeflateStream> classes para compactar e descompactar dados.</span><span class="sxs-lookup"><span data-stu-id="bc7cf-120">You can also use the <xref:System.IO.Compression.GZipStream> and <xref:System.IO.Compression.DeflateStream> classes to compress and decompress data.</span></span> <span data-ttu-id="bc7cf-121">Eles usam o mesmo algoritmo de compactação.</span><span class="sxs-lookup"><span data-stu-id="bc7cf-121">They use the same compression algorithm.</span></span> <span data-ttu-id="bc7cf-122">Compactado <xref:System.IO.Compression.GZipStream> objetos que são gravados em um arquivo que tem uma extensão de .gz podem ser descompactados usando várias ferramentas comuns, além dos métodos fornecidos pelo <xref:System.IO.Compression.GZipStream>.</span><span class="sxs-lookup"><span data-stu-id="bc7cf-122">Compressed <xref:System.IO.Compression.GZipStream> objects that are written to a file that has an extension of .gz can be decompressed by using many common tools in addition to the methods provided by <xref:System.IO.Compression.GZipStream>.</span></span> <span data-ttu-id="bc7cf-123">Este exemplo mostra como compactar e descompactar um diretório de arquivos usando o <xref:System.IO.Compression.GZipStream> classe.</span><span class="sxs-lookup"><span data-stu-id="bc7cf-123">This example shows how to compress and decompress a directory of files by using the <xref:System.IO.Compression.GZipStream> class.</span></span>  
  
 [!code-csharp[IO.Compression.GZip1#1](../../../samples/snippets/csharp/VS_Snippets_CLR/IO.Compression.GZip1/CS/gziptest.cs#1)]
 [!code-vb[IO.Compression.GZip1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/IO.Compression.GZip1/VB/gziptest.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="bc7cf-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bc7cf-124">See Also</span></span>  
 <xref:System.IO.Compression.ZipArchive>  
 <xref:System.IO.Compression.ZipFile>  
 <xref:System.IO.Compression.ZipArchiveEntry>  
 <xref:System.IO.Compression.DeflateStream>  
 <xref:System.IO.Compression.GZipStream>  
 [<span data-ttu-id="bc7cf-125">E/S de arquivo e de fluxo</span><span class="sxs-lookup"><span data-stu-id="bc7cf-125">File and Stream I-O</span></span>](../../../docs/standard/io/index.md)
