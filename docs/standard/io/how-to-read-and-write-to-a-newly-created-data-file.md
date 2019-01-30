---
title: 'Como: Ler e gravar em um arquivo de dados recém-criado'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- streams, reading and writing data
- BinaryReader class, examples
- I/O [.NET Framework], reading data
- I/O [.NET Framework], writing data
- BinaryWriter class, examples
ms.assetid: e209d949-31e8-44ea-8e38-87f9093f3093
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4f51042564158cfd7924164ce2b1a0fcc9d2658d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54562824"
---
# <a name="how-to-read-and-write-to-a-newly-created-data-file"></a><span data-ttu-id="eaf6c-102">Como: Ler e gravar em um arquivo de dados recém-criado</span><span class="sxs-lookup"><span data-stu-id="eaf6c-102">How to: Read and Write to a Newly Created Data File</span></span>
<span data-ttu-id="eaf6c-103">As classes <xref:System.IO.BinaryWriter> e <xref:System.IO.BinaryReader?displayProperty=nameWithType> são usadas para gravar e ler dados em vez de cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="eaf6c-103">The <xref:System.IO.BinaryWriter> and <xref:System.IO.BinaryReader?displayProperty=nameWithType> classes are used for writing and reading data rather than character strings.</span></span> <span data-ttu-id="eaf6c-104">O exemplo a seguir demonstra como gravar e ler dados de um fluxo de arquivo novo e vazio chamado `Test.data`.</span><span class="sxs-lookup"><span data-stu-id="eaf6c-104">The following example demonstrates how to write data to, and read data from, a new, empty file stream called `Test.data`.</span></span> <span data-ttu-id="eaf6c-105">Depois de criar o arquivo de dados no diretório atual, os objetos <xref:System.IO.BinaryWriter> e <xref:System.IO.BinaryReader> associados são criados e o objeto <xref:System.IO.BinaryWriter> é usado para gravar os inteiros de 0 a 10 para `Test.data`, que deixa o ponteiro de arquivo no final do arquivo.</span><span class="sxs-lookup"><span data-stu-id="eaf6c-105">After creating the data file in the current directory, the associated <xref:System.IO.BinaryWriter> and <xref:System.IO.BinaryReader> objects are created, and the <xref:System.IO.BinaryWriter> object is used to write the integers 0 through 10 to `Test.data`, which leaves the file pointer at the end of the file.</span></span> <span data-ttu-id="eaf6c-106">Depois de definir o ponteiro de arquivo de volta para a origem, o objeto <xref:System.IO.BinaryReader> lê o conteúdo especificado.</span><span class="sxs-lookup"><span data-stu-id="eaf6c-106">After setting the file pointer back to the origin, the <xref:System.IO.BinaryReader> object reads out the specified content.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eaf6c-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="eaf6c-107">Example</span></span>  
 [!code-cpp[System.IO.BinaryReaderWriter#7](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.BinaryReaderWriter/CPP/source6.cpp#7)]
 [!code-csharp[System.IO.BinaryReaderWriter#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.BinaryReaderWriter/CS/source6.cs#7)]
 [!code-vb[System.IO.BinaryReaderWriter#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.BinaryReaderWriter/VB/source6.vb#7)]  
  
## <a name="robust-programming"></a><span data-ttu-id="eaf6c-108">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="eaf6c-108">Robust Programming</span></span>  
 <span data-ttu-id="eaf6c-109">Se `Test.data` já existe no diretório atual, um exceção <xref:System.IO.IOException> será lançada.</span><span class="sxs-lookup"><span data-stu-id="eaf6c-109">If `Test.data` already exists in the current directory, an <xref:System.IO.IOException> exception is thrown.</span></span> <span data-ttu-id="eaf6c-110">Use a opção de modo de arquivo <xref:System.IO.FileMode.Create?displayProperty=nameWithType> quando você inicializar o fluxo de arquivos para sempre criar um novo arquivo sem lançar uma exceção.</span><span class="sxs-lookup"><span data-stu-id="eaf6c-110">Use the file mode option <xref:System.IO.FileMode.Create?displayProperty=nameWithType> when you initialize the file stream to always create a new file without throwing an  exception.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eaf6c-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="eaf6c-111">See also</span></span>

- <xref:System.IO.BinaryReader>
- <xref:System.IO.BinaryWriter>
- <xref:System.IO.FileStream>
- <xref:System.IO.FileStream.Seek%2A?displayProperty=nameWithType>
- <xref:System.IO.SeekOrigin>
- [<span data-ttu-id="eaf6c-112">Como: Enumerar diretórios e arquivos</span><span class="sxs-lookup"><span data-stu-id="eaf6c-112">How to: Enumerate Directories and Files</span></span>](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)
- [<span data-ttu-id="eaf6c-113">Como: Abrir um arquivo de log e fazer acréscimos a ele</span><span class="sxs-lookup"><span data-stu-id="eaf6c-113">How to: Open and Append to a Log File</span></span>](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)
- [<span data-ttu-id="eaf6c-114">Como: Ler texto de um arquivo</span><span class="sxs-lookup"><span data-stu-id="eaf6c-114">How to: Read Text from a File</span></span>](../../../docs/standard/io/how-to-read-text-from-a-file.md)
- [<span data-ttu-id="eaf6c-115">Como: Gravar texto em um arquivo</span><span class="sxs-lookup"><span data-stu-id="eaf6c-115">How to: Write Text to a File</span></span>](../../../docs/standard/io/how-to-write-text-to-a-file.md)
- [<span data-ttu-id="eaf6c-116">Como: Ler caracteres de uma cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="eaf6c-116">How to: Read Characters from a String</span></span>](../../../docs/standard/io/how-to-read-characters-from-a-string.md)
- [<span data-ttu-id="eaf6c-117">Como: Gravar caracteres em uma cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="eaf6c-117">How to: Write Characters to a String</span></span>](../../../docs/standard/io/how-to-write-characters-to-a-string.md)
- [<span data-ttu-id="eaf6c-118">E/S de arquivo e de fluxo</span><span class="sxs-lookup"><span data-stu-id="eaf6c-118">File and Stream I/O</span></span>](../../../docs/standard/io/index.md)
