---
title: 'Como: Ler caracteres de uma cadeia de caracteres'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- reading characters from strings
- data streams, reading characters from string
- I/O [.NET Framework], reading characters from strings
- reading data, strings
- streams, reading characters from string
ms.assetid: 27ea5e52-6db8-42d8-980a-50bcfc7fd270
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cbf213c783d1688e9168265cedc27d2ac7a5a96d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54504802"
---
# <a name="how-to-read-characters-from-a-string"></a><span data-ttu-id="98187-102">Como: Ler caracteres de uma cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="98187-102">How to: Read Characters from a String</span></span>
<span data-ttu-id="98187-103">Os exemplos de código a seguir mostram como ler caracteres de forma síncrona e assíncrona de uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="98187-103">The following code examples show how to read characters synchronously and asynchronously from a string.</span></span>  
  
## <a name="example"></a><span data-ttu-id="98187-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="98187-104">Example</span></span>  
 <span data-ttu-id="98187-105">Este exemplo lê 13 caracteres de forma síncrona de uma cadeia de caracteres, armazena-os em uma matriz e exibe esses caracteres.</span><span class="sxs-lookup"><span data-stu-id="98187-105">This example reads 13 characters synchronously from a string, stores them in an array, and displays those characters.</span></span> <span data-ttu-id="98187-106">Em seguida, lê os caracteres restantes na cadeia de caracteres, armazena-os na matriz, começando pelo sexto elemento, e exibe o conteúdo da matriz.</span><span class="sxs-lookup"><span data-stu-id="98187-106">It then reads the remaining characters in the string, stores them in the array starting at the sixth element, and displays the contents of the array.</span></span>  
  
 [!code-cpp[Conceptual.StringReader#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.stringreader/cpp/source.cpp#1)]
 [!code-csharp[Conceptual.StringReader#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.stringreader/cs/source.cs#1)]
 [!code-vb[Conceptual.StringReader#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.stringreader/vb/source.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="98187-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="98187-107">Example</span></span>  
 <span data-ttu-id="98187-108">O próximo exemplo lê todos os caracteres de forma assíncrona de um controle <xref:System.Windows.Controls.TextBox> e os armazena em uma matriz.</span><span class="sxs-lookup"><span data-stu-id="98187-108">The next example reads all the characters asynchronously from a <xref:System.Windows.Controls.TextBox> control, and stores them in an array.</span></span> <span data-ttu-id="98187-109">Ele grava de maneira assíncrona cada caractere alfabético ou espaço em branco em uma linha separada, seguida de uma quebra de linha para um controle <xref:System.Windows.Controls.TextBlock>.</span><span class="sxs-lookup"><span data-stu-id="98187-109">It then asynchronously writes each letter or white space character on a separate line followed by a line break to a <xref:System.Windows.Controls.TextBlock> control.</span></span>  
  
 [!code-csharp[Conceptual.StringReader#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.stringreader/cs/source2.cs#2)]
 [!code-vb[Conceptual.StringReader#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.stringreader/vb/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="98187-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="98187-110">See also</span></span>

- <xref:System.IO.StringReader>
- <xref:System.IO.StringReader.Read%2A?displayProperty=nameWithType>
- [<span data-ttu-id="98187-111">E/S de arquivo assíncrona</span><span class="sxs-lookup"><span data-stu-id="98187-111">Asynchronous File I/O</span></span>](../../../docs/standard/io/asynchronous-file-i-o.md)
- [<span data-ttu-id="98187-112">NIB: Como: Criar uma listagem de diretório</span><span class="sxs-lookup"><span data-stu-id="98187-112">NIB: How to: Create a Directory Listing</span></span>](https://msdn.microsoft.com/library/4d2772b1-b991-4532-a8a6-6ef733277e69)
- [<span data-ttu-id="98187-113">Como: Ler e gravar em um arquivo de dados recém-criado</span><span class="sxs-lookup"><span data-stu-id="98187-113">How to: Read and Write to a Newly Created Data File</span></span>](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)
- [<span data-ttu-id="98187-114">Como: Abrir um arquivo de log e fazer acréscimos a ele</span><span class="sxs-lookup"><span data-stu-id="98187-114">How to: Open and Append to a Log File</span></span>](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)
- [<span data-ttu-id="98187-115">Como: Ler texto de um arquivo</span><span class="sxs-lookup"><span data-stu-id="98187-115">How to: Read Text from a File</span></span>](../../../docs/standard/io/how-to-read-text-from-a-file.md)
- [<span data-ttu-id="98187-116">Como: Gravar texto em um arquivo</span><span class="sxs-lookup"><span data-stu-id="98187-116">How to: Write Text to a File</span></span>](../../../docs/standard/io/how-to-write-text-to-a-file.md)
- [<span data-ttu-id="98187-117">Como: Gravar caracteres em uma cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="98187-117">How to: Write Characters to a String</span></span>](../../../docs/standard/io/how-to-write-characters-to-a-string.md)
- [<span data-ttu-id="98187-118">E/S de arquivo e de fluxo</span><span class="sxs-lookup"><span data-stu-id="98187-118">File and Stream I/O</span></span>](../../../docs/standard/io/index.md)
