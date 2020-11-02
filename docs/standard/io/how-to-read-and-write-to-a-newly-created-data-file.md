---
title: 'Como: ler e gravar em um arquivo de dados recém-criado'
description: Saiba como ler e gravar em um arquivo de dados recém-criado no .NET usando as classes System. IO. BinaryReader e System. IO. BinaryWriter.
ms.date: 01/21/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- streams, reading and writing data
- BinaryReader class, examples
- I/O [.NET], reading data
- I/O [.NET], writing data
- BinaryWriter class, examples
ms.assetid: e209d949-31e8-44ea-8e38-87f9093f3093
ms.openlocfilehash: 236d50260efa66f21db6d0abba6cc5c258a74d8d
ms.sourcegitcommit: 7588b1f16b7608bc6833c05f91ae670c22ef56f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/02/2020
ms.locfileid: "93188725"
---
# <a name="how-to-read-and-write-to-a-newly-created-data-file"></a><span data-ttu-id="42816-103">Como: ler e gravar em um arquivo de dados recém-criado</span><span class="sxs-lookup"><span data-stu-id="42816-103">How to: Read and write to a newly created data file</span></span>

<span data-ttu-id="42816-104">As classes <xref:System.IO.BinaryWriter?displayProperty=nameWithType> e <xref:System.IO.BinaryReader?displayProperty=nameWithType> são usadas para gravar e ler dados que não sejam cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="42816-104">The <xref:System.IO.BinaryWriter?displayProperty=nameWithType> and <xref:System.IO.BinaryReader?displayProperty=nameWithType> classes are used for writing and reading data other than character strings.</span></span> <span data-ttu-id="42816-105">O exemplo a seguir mostra como criar um fluxo de arquivo vazio, gravar dados nele e ler dados dele.</span><span class="sxs-lookup"><span data-stu-id="42816-105">The following example shows how to create an empty file stream, write data to it, and read data from it.</span></span>

<span data-ttu-id="42816-106">O exemplo cria um arquivo de dados chamado *Test.data* no diretório atual, cria os objetos <xref:System.IO.BinaryWriter> e <xref:System.IO.BinaryReader> associados e usa o objeto <xref:System.IO.BinaryWriter> para gravar os inteiros de 0 a 10 em *Test.data* , o que deixa o ponteiro de arquivo no final do arquivo.</span><span class="sxs-lookup"><span data-stu-id="42816-106">The example creates a data file called *Test.data* in the current directory, creates the associated <xref:System.IO.BinaryWriter> and <xref:System.IO.BinaryReader> objects, and uses the <xref:System.IO.BinaryWriter> object to write the integers 0 through 10 to *Test.data* , which leaves the file pointer at the end of the file.</span></span> <span data-ttu-id="42816-107">Em seguida, o objeto <xref:System.IO.BinaryReader> define o ponteiro de arquivo novamente para a origem e lê o conteúdo especificado.</span><span class="sxs-lookup"><span data-stu-id="42816-107">The <xref:System.IO.BinaryReader> object then sets the file pointer back to the origin and reads out the specified content.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="42816-108">Se *Test.data* já existir no diretório atual, uma exceção <xref:System.IO.IOException> será gerada.</span><span class="sxs-lookup"><span data-stu-id="42816-108">If *Test.data* already exists in the current directory, an <xref:System.IO.IOException> exception is thrown.</span></span> <span data-ttu-id="42816-109">Use a opção de modo de arquivo <xref:System.IO.FileMode.Create?displayProperty=nameWithType> em vez de <xref:System.IO.FileMode.CreateNew?displayProperty=nameWithType> para sempre criar um arquivo sem gerar uma exceção.</span><span class="sxs-lookup"><span data-stu-id="42816-109">Use the file mode option <xref:System.IO.FileMode.Create?displayProperty=nameWithType> rather than <xref:System.IO.FileMode.CreateNew?displayProperty=nameWithType> to always create a new file without throwing an exception.</span></span>  
  
## <a name="example"></a><span data-ttu-id="42816-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="42816-110">Example</span></span>  
 [!code-csharp[System.IO.BinaryReaderWriter#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.BinaryReaderWriter/CS/source6.cs#7)]
 [!code-vb[System.IO.BinaryReaderWriter#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.BinaryReaderWriter/VB/source6.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="42816-111">Confira também</span><span class="sxs-lookup"><span data-stu-id="42816-111">See also</span></span>

- <xref:System.IO.BinaryReader>  
- <xref:System.IO.BinaryWriter>  
- <xref:System.IO.FileStream>  
- <xref:System.IO.FileStream.Seek%2A?displayProperty=nameWithType>  
- <xref:System.IO.SeekOrigin>  
- [<span data-ttu-id="42816-112">Como: enumerar diretórios e arquivos</span><span class="sxs-lookup"><span data-stu-id="42816-112">How to: Enumerate directories and files</span></span>](how-to-enumerate-directories-and-files.md)  
- [<span data-ttu-id="42816-113">Como: abrir e anexar a um arquivo de log</span><span class="sxs-lookup"><span data-stu-id="42816-113">How to: Open and append to a log file</span></span>](how-to-open-and-append-to-a-log-file.md)  
- [<span data-ttu-id="42816-114">Como: ler texto de um arquivo</span><span class="sxs-lookup"><span data-stu-id="42816-114">How to: Read text from a file</span></span>](how-to-read-text-from-a-file.md)  
- [<span data-ttu-id="42816-115">Como: gravar texto em um arquivo</span><span class="sxs-lookup"><span data-stu-id="42816-115">How to: Write text to a file</span></span>](how-to-write-text-to-a-file.md)  
- [<span data-ttu-id="42816-116">Como: ler caracteres de uma cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="42816-116">How to: Read characters from a string</span></span>](how-to-read-characters-from-a-string.md)  
- [<span data-ttu-id="42816-117">Como: gravar caracteres em uma cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="42816-117">How to: Write characters to a string</span></span>](how-to-write-characters-to-a-string.md)  
- [<span data-ttu-id="42816-118">E/S de arquivo e de fluxo</span><span class="sxs-lookup"><span data-stu-id="42816-118">File and stream I/O</span></span>](index.md)
