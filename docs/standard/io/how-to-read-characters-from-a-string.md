---
title: 'Como: Ler caracteres de uma cadeia de caracteres'
ms.date: 01/21/2019
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
ms.openlocfilehash: e890e4172e645e9919ea88ec5835aaed7432c0c6
ms.sourcegitcommit: bd28ff1e312eaba9718c4f7ea272c2d4781a7cac
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/26/2019
ms.locfileid: "56835194"
---
# <a name="how-to-read-characters-from-a-string"></a><span data-ttu-id="2a34d-102">Como: Ler caracteres de uma cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="2a34d-102">How to: Read characters from a string</span></span>
<span data-ttu-id="2a34d-103">Os exemplos de código a seguir mostram como ler caracteres de forma síncrona ou assíncrona de uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="2a34d-103">The following code examples show how to read characters synchronously or asynchronously from a string.</span></span>  
  
## <a name="example-read-characters-synchronously"></a><span data-ttu-id="2a34d-104">Exemplo: Ler caracteres de forma síncrona</span><span class="sxs-lookup"><span data-stu-id="2a34d-104">Example: Read characters synchronously</span></span> 
 <span data-ttu-id="2a34d-105">Este exemplo lê 13 caracteres de forma síncrona de uma cadeia de caracteres, armazena-os em uma matriz e exibe-os.</span><span class="sxs-lookup"><span data-stu-id="2a34d-105">This example reads 13 characters synchronously from a string, stores them in an array, and displays them.</span></span> <span data-ttu-id="2a34d-106">Em seguida, o exemplo lê os caracteres restantes na cadeia de caracteres, armazena-os na matriz começando pelo sexto elemento e exibe o conteúdo da matriz.</span><span class="sxs-lookup"><span data-stu-id="2a34d-106">The example then reads the rest of the characters in the string, stores them in the array starting at the sixth element, and displays the contents of the array.</span></span>  
  
 [!code-csharp[Conceptual.StringReader#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.stringreader/cs/source.cs#1)]
 [!code-vb[Conceptual.StringReader#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.stringreader/vb/source.vb#1)]  
  
## <a name="example-read-characters-asynchronously"></a><span data-ttu-id="2a34d-107">Exemplo: Ler caracteres de forma assíncrona</span><span class="sxs-lookup"><span data-stu-id="2a34d-107">Example: Read characters asynchronously</span></span>  
 <span data-ttu-id="2a34d-108">O próximo exemplo é o código por trás de um aplicativo WPF.</span><span class="sxs-lookup"><span data-stu-id="2a34d-108">The next example is the code behind a WPF app.</span></span> <span data-ttu-id="2a34d-109">Na carga de janela, o exemplo lê todos os caracteres de forma assíncrona de um controle <xref:System.Windows.Controls.TextBox> e os armazena em uma matriz.</span><span class="sxs-lookup"><span data-stu-id="2a34d-109">On window load, the example asynchronously reads all characters from a <xref:System.Windows.Controls.TextBox> control and stores them in an array.</span></span> <span data-ttu-id="2a34d-110">Em seguida, ele grava cada letra ou caractere de espaço em branco de forma assíncrona em uma linha separada de um controle <xref:System.Windows.Controls.TextBlock>.</span><span class="sxs-lookup"><span data-stu-id="2a34d-110">It then asynchronously writes each letter or white-space character to a separate line of a <xref:System.Windows.Controls.TextBlock> control.</span></span>  
  
 [!code-csharp[Conceptual.StringReader#2](../../../samples/snippets/csharp/VS_Snippets_Wpf/StringReaderWriter/MainWindow.xaml.cs)]
 [!code-vb[Conceptual.StringReader#2](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StringReaderWriter/MainWindow.xaml.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="2a34d-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2a34d-111">See also</span></span>

- <xref:System.IO.StringReader>  
- <xref:System.IO.StringReader.Read%2A?displayProperty=nameWithType>  
- [<span data-ttu-id="2a34d-112">E/S assíncrona de arquivo</span><span class="sxs-lookup"><span data-stu-id="2a34d-112">Asynchronous file I/O</span></span>](../../../docs/standard/io/asynchronous-file-i-o.md)  
- <span data-ttu-id="2a34d-113">[Como: Criar uma listagem de diretório](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5cf8zcfh(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="2a34d-113">[How to: Create a directory listing](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5cf8zcfh(v=vs.100))</span></span>  
- [<span data-ttu-id="2a34d-114">Como: Ler e gravar em um arquivo de dados recém-criado</span><span class="sxs-lookup"><span data-stu-id="2a34d-114">How to: Read and write to a newly created data file</span></span>](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
- [<span data-ttu-id="2a34d-115">Como: Abrir um arquivo de log e fazer acréscimos a ele</span><span class="sxs-lookup"><span data-stu-id="2a34d-115">How to: Open and append to a log file</span></span>](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
- [<span data-ttu-id="2a34d-116">Como: Ler texto de um arquivo</span><span class="sxs-lookup"><span data-stu-id="2a34d-116">How to: Read text from a file</span></span>](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
- [<span data-ttu-id="2a34d-117">Como: Gravar texto em um arquivo</span><span class="sxs-lookup"><span data-stu-id="2a34d-117">How to: Write text to a file</span></span>](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
- [<span data-ttu-id="2a34d-118">Como: Gravar caracteres em uma cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="2a34d-118">How to: Write characters to a string</span></span>](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
- [<span data-ttu-id="2a34d-119">E/S de arquivo e de fluxo</span><span class="sxs-lookup"><span data-stu-id="2a34d-119">File and stream I/O</span></span>](../../../docs/standard/io/index.md)
