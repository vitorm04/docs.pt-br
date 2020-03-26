---
title: Como compactar e extrair arquivos
ms.date: 01/14/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- I/O [.NET Framework], compression
- compression
- compress files
ms.assetid: e9876165-3c60-4c84-a272-513e47acf579
ms.openlocfilehash: 10f990401830bc5f77176f4e586f15f7dd75ff14
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80248011"
---
# <a name="how-to-compress-and-extract-files"></a><span data-ttu-id="b9639-102">Como compactar e extrair arquivos</span><span class="sxs-lookup"><span data-stu-id="b9639-102">How to: Compress and extract files</span></span>

<span data-ttu-id="b9639-103">O namespace <xref:System.IO.Compression> contém os seguintes tipos para compactar e descompactar arquivos e fluxos.</span><span class="sxs-lookup"><span data-stu-id="b9639-103">The <xref:System.IO.Compression> namespace contains the following types for compressing and decompressing files and streams.</span></span> <span data-ttu-id="b9639-104">Use também esses tipos para ler e modificar o conteúdo de um arquivo compactado.</span><span class="sxs-lookup"><span data-stu-id="b9639-104">You can also use these types to read and modify the contents of a compressed file.</span></span>

- <xref:System.IO.Compression.ZipFile>
- <xref:System.IO.Compression.ZipArchive>
- <xref:System.IO.Compression.ZipArchiveEntry>
- <xref:System.IO.Compression.DeflateStream>
- <xref:System.IO.Compression.GZipStream>

<span data-ttu-id="b9639-105">Os exemplos a seguir mostram algumas das operações que você pode executar com arquivos compactados.</span><span class="sxs-lookup"><span data-stu-id="b9639-105">The following examples show some of the operations you can perform with compressed files.</span></span> <span data-ttu-id="b9639-106">Esses exemplos exigem que os seguintes pacotes NuGet sejam adicionados ao seu projeto:</span><span class="sxs-lookup"><span data-stu-id="b9639-106">These examples require the following NuGet packages to be added to your project:</span></span>

- [<span data-ttu-id="b9639-107">System.IO.Compression</span><span class="sxs-lookup"><span data-stu-id="b9639-107">System.IO.Compression</span></span>](https://www.nuget.org/packages/System.IO.Compression)
- [<span data-ttu-id="b9639-108">System.IO.Compression.ZipFile</span><span class="sxs-lookup"><span data-stu-id="b9639-108">System.IO.Compression.ZipFile</span></span>](https://www.nuget.org/packages/System.IO.Compression.ZipFile)

<span data-ttu-id="b9639-109">Se você estiver usando o .NET Framework, adicione referências a essas duas bibliotecas ao seu projeto:</span><span class="sxs-lookup"><span data-stu-id="b9639-109">If you're using .NET Framework, add references to these two libraries to your project:</span></span>

- `System.IO.Compression`
- `System.IO.Compression.FileSystem`

## <a name="example-1-create-and-extract-a-zip-file"></a><span data-ttu-id="b9639-110">Exemplo 1: Criar e extrair um arquivo .zip</span><span class="sxs-lookup"><span data-stu-id="b9639-110">Example 1: Create and extract a .zip file</span></span>

<span data-ttu-id="b9639-111">O exemplo a seguir mostra como criar e extrair um arquivo *.zip* compactado usando a classe <xref:System.IO.Compression.ZipFile>.</span><span class="sxs-lookup"><span data-stu-id="b9639-111">The following example shows how to create and extract a compressed *.zip* file by using the <xref:System.IO.Compression.ZipFile> class.</span></span> <span data-ttu-id="b9639-112">O exemplo compacta o conteúdo de uma pasta em um novo arquivo *.zip* e extrai o zip para uma nova pasta.</span><span class="sxs-lookup"><span data-stu-id="b9639-112">The example compresses the contents of a folder into a new *.zip* file, and then extracts the zip to a new folder.</span></span>

<span data-ttu-id="b9639-113">Para executar a amostra, crie uma pasta *Iniciar* na pasta do programa e popule-a com arquivos a serem zipados.</span><span class="sxs-lookup"><span data-stu-id="b9639-113">To run the sample, create a *start* folder in your program folder and populate it with files to zip.</span></span>

[!code-csharp[System.IO.Compression.ZipFile#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.zipfile/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipFile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.zipfile/vb/program1.vb#1)]

## <a name="example-2-extract-specific-file-extensions"></a><span data-ttu-id="b9639-114">Exemplo 2: Extrair extensões específicas de arquivos</span><span class="sxs-lookup"><span data-stu-id="b9639-114">Example 2: Extract specific file extensions</span></span>

<span data-ttu-id="b9639-115">O próximo exemplo itera pelo conteúdo de um arquivo *.zip* existente e extrai os arquivos que têm uma extensão *.txt*.</span><span class="sxs-lookup"><span data-stu-id="b9639-115">The next example iterates through the contents of an existing *.zip* file and extracts files that have a *.txt* extension.</span></span> <span data-ttu-id="b9639-116">Ele usa a classe <xref:System.IO.Compression.ZipArchive> para acessar o zip e a classe <xref:System.IO.Compression.ZipArchiveEntry> para inspecionar as entradas individuais.</span><span class="sxs-lookup"><span data-stu-id="b9639-116">It uses the <xref:System.IO.Compression.ZipArchive> class to access the zip, and the <xref:System.IO.Compression.ZipArchiveEntry> class to inspect the individual entries.</span></span> <span data-ttu-id="b9639-117">O método de extensão <xref:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A> para o objeto <xref:System.IO.Compression.ZipArchiveEntry> está disponível na classe <xref:System.IO.Compression.ZipFileExtensions?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b9639-117">The extension method <xref:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A> for the <xref:System.IO.Compression.ZipArchiveEntry> object is available in the <xref:System.IO.Compression.ZipFileExtensions?displayProperty=nameWithType> class.</span></span>

<span data-ttu-id="b9639-118">Para executar a amostra, coloque um arquivo *.zip* chamado *result.zip* na pasta do programa.</span><span class="sxs-lookup"><span data-stu-id="b9639-118">To run the sample, place a *.zip* file called *result.zip* in your program folder.</span></span> <span data-ttu-id="b9639-119">Quando solicitado, forneça um nome de pasta na qual extrair.</span><span class="sxs-lookup"><span data-stu-id="b9639-119">When prompted, provide a folder name to extract to.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b9639-120">Ao descompactar os arquivos, você precisa procurar caminhos de arquivos maliciosos que possam escapar do diretório no qual deseja descompactar.</span><span class="sxs-lookup"><span data-stu-id="b9639-120">When unzipping files, you must look for malicious file paths, which can escape out of the directory you unzip into.</span></span> <span data-ttu-id="b9639-121">Isso é conhecido como um ataque de passagem de caminho.</span><span class="sxs-lookup"><span data-stu-id="b9639-121">This is known as a path traversal attack.</span></span> <span data-ttu-id="b9639-122">O exemplo a seguir demonstra como verificar caminhos de arquivos maliciosos e fornece uma maneira segura de descompactação.</span><span class="sxs-lookup"><span data-stu-id="b9639-122">The following example demonstrates how to check for malicious file paths and provides a safe way to unzip.</span></span>

[!code-csharp[System.IO.Compression.ZipArchive#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchive/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipArchive#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchive/vb/program1.vb#1)]

## <a name="example-3-add-a-file-to-an-existing-zip"></a><span data-ttu-id="b9639-123">Exemplo 3: Adicione um arquivo a um zip existente</span><span class="sxs-lookup"><span data-stu-id="b9639-123">Example 3: Add a file to an existing zip</span></span>

<span data-ttu-id="b9639-124">O exemplo a seguir usa a classe <xref:System.IO.Compression.ZipArchive> para acessar um arquivo *.zip* existente e adiciona um arquivo a ele.</span><span class="sxs-lookup"><span data-stu-id="b9639-124">The following example uses the <xref:System.IO.Compression.ZipArchive> class to access an existing *.zip* file, and adds a file to it.</span></span> <span data-ttu-id="b9639-125">O novo arquivo é compactado quando você o adiciona ao zip existente.</span><span class="sxs-lookup"><span data-stu-id="b9639-125">The new file gets compressed when you add it to the existing zip.</span></span>

[!code-csharp[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/vb/program1.vb#1)]

## <a name="example-4-compress-and-decompress-gz-files"></a><span data-ttu-id="b9639-126">Exemplo 4: Compactar e descompactar arquivos .gz</span><span class="sxs-lookup"><span data-stu-id="b9639-126">Example 4: Compress and decompress .gz files</span></span>

<span data-ttu-id="b9639-127">Você também pode usar as classes <xref:System.IO.Compression.GZipStream> e <xref:System.IO.Compression.DeflateStream> para compactar e descompactar dados.</span><span class="sxs-lookup"><span data-stu-id="b9639-127">You can also use the <xref:System.IO.Compression.GZipStream> and <xref:System.IO.Compression.DeflateStream> classes to compress and decompress data.</span></span> <span data-ttu-id="b9639-128">Elas usam o mesmo algoritmo de compactação.</span><span class="sxs-lookup"><span data-stu-id="b9639-128">They use the same compression algorithm.</span></span> <span data-ttu-id="b9639-129">Você pode descompactar objetos <xref:System.IO.Compression.GZipStream> que são gravados em um arquivo *.gz* usando muitas ferramentas comuns.</span><span class="sxs-lookup"><span data-stu-id="b9639-129">You can decompress <xref:System.IO.Compression.GZipStream> objects that are written to a *.gz* file by using many common tools.</span></span> <span data-ttu-id="b9639-130">O exemplo a seguir mostra como compactar e descompactar um diretório de arquivos usando a classe <xref:System.IO.Compression.GZipStream>:</span><span class="sxs-lookup"><span data-stu-id="b9639-130">The following example shows how to compress and decompress a directory of files by using the <xref:System.IO.Compression.GZipStream> class:</span></span>

[!code-csharp[IO.Compression.GZip1#1](../../../samples/snippets/csharp/VS_Snippets_CLR/IO.Compression.GZip1/CS/gziptest.cs#1)]
[!code-vb[IO.Compression.GZip1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/IO.Compression.GZip1/VB/gziptest.vb#1)]

## <a name="see-also"></a><span data-ttu-id="b9639-131">Confira também</span><span class="sxs-lookup"><span data-stu-id="b9639-131">See also</span></span>

- <xref:System.IO.Compression.ZipArchive>  
- <xref:System.IO.Compression.ZipFile>  
- <xref:System.IO.Compression.ZipArchiveEntry>  
- <xref:System.IO.Compression.DeflateStream>  
- <xref:System.IO.Compression.GZipStream>  
- [<span data-ttu-id="b9639-132">E/S de arquivo e de fluxo</span><span class="sxs-lookup"><span data-stu-id="b9639-132">File and stream I/O</span></span>](../../../docs/standard/io/index.md)
