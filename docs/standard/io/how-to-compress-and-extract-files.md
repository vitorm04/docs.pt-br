---
title: 'Como: Compactar e extrair arquivos'
ms.date: 06/06/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- I/O [.NET Framework], compression
- compression
- compress files
ms.assetid: e9876165-3c60-4c84-a272-513e47acf579
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c35bf549dc4dcd5e12e3580c2357b64dcc42905b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54650935"
---
# <a name="how-to-compress-and-extract-files"></a><span data-ttu-id="6ccc6-102">Como: Compactar e extrair arquivos</span><span class="sxs-lookup"><span data-stu-id="6ccc6-102">How to: Compress and extract files</span></span>

<span data-ttu-id="6ccc6-103">O namespace <xref:System.IO.Compression> contém os seguintes tipos para compactar e descompactar arquivos e fluxos.</span><span class="sxs-lookup"><span data-stu-id="6ccc6-103">The <xref:System.IO.Compression> namespace contains the following types for compressing and decompressing files and streams.</span></span> <span data-ttu-id="6ccc6-104">Você também pode usar esses tipos para ler e modificar o conteúdo de um arquivo compactado:</span><span class="sxs-lookup"><span data-stu-id="6ccc6-104">You can also use these types to read and modify the contents of a compressed file:</span></span>

- <xref:System.IO.Compression.ZipFile>

- <xref:System.IO.Compression.ZipArchive>

- <xref:System.IO.Compression.ZipArchiveEntry>

- <xref:System.IO.Compression.DeflateStream>

- <xref:System.IO.Compression.GZipStream>

<span data-ttu-id="6ccc6-105">Os exemplos a seguir mostram algumas das funções que você pode executar ao trabalhar com arquivos compactados.</span><span class="sxs-lookup"><span data-stu-id="6ccc6-105">The following examples show some of the functions you can perform when working with compressed files.</span></span>

## <a name="example-1---create-and-extract-a-zip-file"></a><span data-ttu-id="6ccc6-106">Exemplo 1 - Criar e extrair um arquivo .zip</span><span class="sxs-lookup"><span data-stu-id="6ccc6-106">Example 1 - Create and extract a .zip file</span></span>

<span data-ttu-id="6ccc6-107">O exemplo a seguir mostra como criar e extrair um arquivo compactado que tenha uma extensão de nome de arquivo .zip usando a classe <xref:System.IO.Compression.ZipFile>.</span><span class="sxs-lookup"><span data-stu-id="6ccc6-107">The following example shows how to create and extract a compressed file that has a .zip file name extension by using the <xref:System.IO.Compression.ZipFile> class.</span></span> <span data-ttu-id="6ccc6-108">Ele compacta o conteúdo de uma pasta em um novo arquivo .zip e extrai o conteúdo para uma nova pasta.</span><span class="sxs-lookup"><span data-stu-id="6ccc6-108">It compresses the contents of a folder into a new .zip file and then extracts that content to a new folder.</span></span> <span data-ttu-id="6ccc6-109">Para usar a classe <xref:System.IO.Compression.ZipFile>, você deve fazer referência ao assembly `System.IO.Compression.FileSystem` em seu projeto.</span><span class="sxs-lookup"><span data-stu-id="6ccc6-109">To use the <xref:System.IO.Compression.ZipFile> class, you must reference the `System.IO.Compression.FileSystem` assembly in your project.</span></span>

[!code-csharp[System.IO.Compression.ZipFile#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.zipfile/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipFile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.zipfile/vb/program1.vb#1)]

## <a name="example-2---extract-specific-file-extensions"></a><span data-ttu-id="6ccc6-110">Exemplo 2 - Extrair extensões de arquivo específicas</span><span class="sxs-lookup"><span data-stu-id="6ccc6-110">Example 2 - Extract specific file extensions</span></span>

<span data-ttu-id="6ccc6-111">O exemplo a seguir mostra como iterar pelo conteúdo de um arquivo .zip e extrair os arquivos que tenham uma extensão .txt.</span><span class="sxs-lookup"><span data-stu-id="6ccc6-111">The next example shows how to iterate through the contents of an existing .zip file and extract files that have a .txt extension.</span></span> <span data-ttu-id="6ccc6-112">Ele usa a classe <xref:System.IO.Compression.ZipArchive> para acessar um arquivo .zip existente, e a classe <xref:System.IO.Compression.ZipArchiveEntry> para inspecionar as entradas individuais no arquivo compactado.</span><span class="sxs-lookup"><span data-stu-id="6ccc6-112">It uses the <xref:System.IO.Compression.ZipArchive> class to access an existing .zip file, and the <xref:System.IO.Compression.ZipArchiveEntry> class to inspect the individual entries in the compressed file.</span></span> <span data-ttu-id="6ccc6-113">Ele usa um método de extensão (<xref:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A>) para o objeto <xref:System.IO.Compression.ZipArchiveEntry>.</span><span class="sxs-lookup"><span data-stu-id="6ccc6-113">It uses an extension method (<xref:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A>) for the <xref:System.IO.Compression.ZipArchiveEntry> object.</span></span> <span data-ttu-id="6ccc6-114">O método de extensão está disponível na classe <xref:System.IO.Compression.ZipFileExtensions?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6ccc6-114">The extension method is available in the <xref:System.IO.Compression.ZipFileExtensions?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="6ccc6-115">Para usar a classe <xref:System.IO.Compression.ZipFileExtensions>, você deve fazer referência ao assembly `System.IO.Compression.FileSystem` em seu projeto.</span><span class="sxs-lookup"><span data-stu-id="6ccc6-115">To use the <xref:System.IO.Compression.ZipFileExtensions> class, you must reference the `System.IO.Compression.FileSystem` assembly in your project.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6ccc6-116">Ao descompactar os arquivos, você deve procurar caminhos de arquivos maliciosos que possam escapar do diretório em que deseja descompactar.</span><span class="sxs-lookup"><span data-stu-id="6ccc6-116">When unzipping files, you must look for malicious file paths which can escape out of the directory where you want to unzip into.</span></span> <span data-ttu-id="6ccc6-117">Isso é conhecido como um ataque de passagem de caminho.</span><span class="sxs-lookup"><span data-stu-id="6ccc6-117">This is known as a path traversal attack.</span></span>

<span data-ttu-id="6ccc6-118">O exemplo a seguir demonstra como verificar caminhos de arquivos maliciosos e fornece uma maneira segura de descompactar:</span><span class="sxs-lookup"><span data-stu-id="6ccc6-118">The following example demonstrates how to check for malicious file paths and provides a safe way to unzip:</span></span>

[!code-csharp[System.IO.Compression.ZipArchive#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchive/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipArchive#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchive/vb/program1.vb#1)]

## <a name="example-3---add-a-new-file-to-an-existing-zip-file"></a><span data-ttu-id="6ccc6-119">Exemplo 3 - Adicionar um novo arquivo para um arquivo. zip existente</span><span class="sxs-lookup"><span data-stu-id="6ccc6-119">Example 3 - Add a new file to an existing .zip file</span></span>

<span data-ttu-id="6ccc6-120">O exemplo a seguir usa a classe <xref:System.IO.Compression.ZipArchive> para acessar um arquivo .zip existente, e adiciona um novo arquivo ao arquivo compactado.</span><span class="sxs-lookup"><span data-stu-id="6ccc6-120">The following example uses the <xref:System.IO.Compression.ZipArchive> class to access an existing .zip file, and adds a new file to the compressed file.</span></span> <span data-ttu-id="6ccc6-121">O novo arquivo é compactado quando você o adiciona ao arquivo .zip.</span><span class="sxs-lookup"><span data-stu-id="6ccc6-121">The new file gets compressed when you add it to the existing .zip file.</span></span>

[!code-csharp[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/vb/program1.vb#1)]

## <a name="example-4---compress-and-decompress-a-directory-of-gz-files"></a><span data-ttu-id="6ccc6-122">Exemplo 4 - Compactar e descompactar um diretório de arquivos .gz</span><span class="sxs-lookup"><span data-stu-id="6ccc6-122">Example 4 - Compress and decompress a directory of .gz files</span></span>

<span data-ttu-id="6ccc6-123">Você também pode usar as classes <xref:System.IO.Compression.GZipStream> e <xref:System.IO.Compression.DeflateStream> para compactar e descompactar dados.</span><span class="sxs-lookup"><span data-stu-id="6ccc6-123">You can also use the <xref:System.IO.Compression.GZipStream> and <xref:System.IO.Compression.DeflateStream> classes to compress and decompress data.</span></span> <span data-ttu-id="6ccc6-124">Elas usam o mesmo algoritmo de compactação.</span><span class="sxs-lookup"><span data-stu-id="6ccc6-124">They use the same compression algorithm.</span></span> <span data-ttu-id="6ccc6-125">Objetos <xref:System.IO.Compression.GZipStream> compactados que são gravados em um arquivo que tem uma extensão .gz podem ser descompactados usando várias ferramentas comuns, além dos métodos fornecidos por <xref:System.IO.Compression.GZipStream>.</span><span class="sxs-lookup"><span data-stu-id="6ccc6-125">Compressed <xref:System.IO.Compression.GZipStream> objects that are written to a file that has an extension of .gz can be decompressed by using many common tools in addition to the methods provided by <xref:System.IO.Compression.GZipStream>.</span></span> <span data-ttu-id="6ccc6-126">O exemplo a seguir mostra como compactar e descompactar um diretório de arquivos usando a classe <xref:System.IO.Compression.GZipStream>:</span><span class="sxs-lookup"><span data-stu-id="6ccc6-126">The following example shows how to compress and decompress a directory of files by using the <xref:System.IO.Compression.GZipStream> class:</span></span>

[!code-csharp[IO.Compression.GZip1#1](../../../samples/snippets/csharp/VS_Snippets_CLR/IO.Compression.GZip1/CS/gziptest.cs#1)]
[!code-vb[IO.Compression.GZip1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/IO.Compression.GZip1/VB/gziptest.vb#1)]

## <a name="see-also"></a><span data-ttu-id="6ccc6-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6ccc6-127">See also</span></span>

- <xref:System.IO.Compression.ZipArchive>
- <xref:System.IO.Compression.ZipFile>
- <xref:System.IO.Compression.ZipArchiveEntry>
- <xref:System.IO.Compression.DeflateStream>
- <xref:System.IO.Compression.GZipStream>
- [<span data-ttu-id="6ccc6-128">E/S de arquivo e de fluxo</span><span class="sxs-lookup"><span data-stu-id="6ccc6-128">File and Stream I/O</span></span>](../../../docs/standard/io/index.md)
