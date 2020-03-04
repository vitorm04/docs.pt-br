---
title: 'Como: ler e gravar em um arquivo de dados recém-criado'
ms.date: 01/21/2019
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
ms.openlocfilehash: 3772aeeb25d1251a13fde2a0e51a913e5e39eabc
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78155744"
---
# <a name="how-to-read-and-write-to-a-newly-created-data-file"></a><span data-ttu-id="6869a-102">Como: ler e gravar em um arquivo de dados recém-criado</span><span class="sxs-lookup"><span data-stu-id="6869a-102">How to: Read and write to a newly created data file</span></span>
<span data-ttu-id="6869a-103">As classes <xref:System.IO.BinaryWriter?displayProperty=nameWithType> e <xref:System.IO.BinaryReader?displayProperty=nameWithType> são usadas para gravar e ler dados que não sejam cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="6869a-103">The <xref:System.IO.BinaryWriter?displayProperty=nameWithType> and <xref:System.IO.BinaryReader?displayProperty=nameWithType> classes are used for writing and reading data other than character strings.</span></span> <span data-ttu-id="6869a-104">O exemplo a seguir mostra como criar um fluxo de arquivo vazio, gravar dados nele e ler dados dele.</span><span class="sxs-lookup"><span data-stu-id="6869a-104">The following example shows how to create an empty file stream, write data to it, and read data from it.</span></span>

<span data-ttu-id="6869a-105">O exemplo cria um arquivo de dados chamado *Test.data* no diretório atual, cria os objetos <xref:System.IO.BinaryWriter> e <xref:System.IO.BinaryReader> associados e usa o objeto <xref:System.IO.BinaryWriter> para gravar os inteiros de 0 a 10 em *Test.data*, o que deixa o ponteiro de arquivo no final do arquivo.</span><span class="sxs-lookup"><span data-stu-id="6869a-105">The example creates a data file called *Test.data* in the current directory, creates the associated <xref:System.IO.BinaryWriter> and <xref:System.IO.BinaryReader> objects, and uses the <xref:System.IO.BinaryWriter> object to write the integers 0 through 10 to *Test.data*, which leaves the file pointer at the end of the file.</span></span> <span data-ttu-id="6869a-106">Em seguida, o objeto <xref:System.IO.BinaryReader> define o ponteiro de arquivo novamente para a origem e lê o conteúdo especificado.</span><span class="sxs-lookup"><span data-stu-id="6869a-106">The <xref:System.IO.BinaryReader> object then sets the file pointer back to the origin and reads out the specified content.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6869a-107">Se *Test.data* já existir no diretório atual, uma exceção <xref:System.IO.IOException> será gerada.</span><span class="sxs-lookup"><span data-stu-id="6869a-107">If *Test.data* already exists in the current directory, an <xref:System.IO.IOException> exception is thrown.</span></span> <span data-ttu-id="6869a-108">Use a opção de modo de arquivo <xref:System.IO.FileMode.Create?displayProperty=nameWithType> em vez de <xref:System.IO.FileMode.CreateNew?displayProperty=nameWithType> para sempre criar um arquivo sem gerar uma exceção.</span><span class="sxs-lookup"><span data-stu-id="6869a-108">Use the file mode option <xref:System.IO.FileMode.Create?displayProperty=nameWithType> rather than <xref:System.IO.FileMode.CreateNew?displayProperty=nameWithType> to always create a new file without throwing an exception.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6869a-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6869a-109">Example</span></span>  
 [!code-csharp[System.IO.BinaryReaderWriter#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.BinaryReaderWriter/CS/source6.cs#7)]
 [!code-vb[System.IO.BinaryReaderWriter#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.BinaryReaderWriter/VB/source6.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="6869a-110">Confira também</span><span class="sxs-lookup"><span data-stu-id="6869a-110">See also</span></span>

- <xref:System.IO.BinaryReader>  
- <xref:System.IO.BinaryWriter>  
- <xref:System.IO.FileStream>  
- <xref:System.IO.FileStream.Seek%2A?displayProperty=nameWithType>  
- <xref:System.IO.SeekOrigin>  
- [<span data-ttu-id="6869a-111">Como: enumerar diretórios e arquivos</span><span class="sxs-lookup"><span data-stu-id="6869a-111">How to: Enumerate directories and files</span></span>](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)  
- [<span data-ttu-id="6869a-112">Como: abrir e anexar a um arquivo de log</span><span class="sxs-lookup"><span data-stu-id="6869a-112">How to: Open and append to a log file</span></span>](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
- [<span data-ttu-id="6869a-113">Como: ler texto de um arquivo</span><span class="sxs-lookup"><span data-stu-id="6869a-113">How to: Read text from a file</span></span>](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
- [<span data-ttu-id="6869a-114">Como: gravar texto em um arquivo</span><span class="sxs-lookup"><span data-stu-id="6869a-114">How to: Write text to a file</span></span>](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
- [<span data-ttu-id="6869a-115">Como: ler caracteres de uma cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="6869a-115">How to: Read characters from a string</span></span>](../../../docs/standard/io/how-to-read-characters-from-a-string.md)  
- [<span data-ttu-id="6869a-116">Como: gravar caracteres em uma cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="6869a-116">How to: Write characters to a string</span></span>](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
- [<span data-ttu-id="6869a-117">E/S de arquivo e de fluxo</span><span class="sxs-lookup"><span data-stu-id="6869a-117">File and stream I/O</span></span>](../../../docs/standard/io/index.md)
