---
title: 'Como: ler caracteres de uma cadeia de caracteres'
description: Saiba como ler caracteres de uma cadeia de caracteres no .NET. Veja exemplos de leitura de caracteres de forma síncrona e assíncrona.
ms.date: 01/21/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- reading characters from strings
- data streams, reading characters from string
- I/O [.NET], reading characters from strings
- reading data, strings
- streams, reading characters from string
ms.assetid: 27ea5e52-6db8-42d8-980a-50bcfc7fd270
ms.openlocfilehash: c613f8170655601b72b87de4a20c295b1054bd1a
ms.sourcegitcommit: 7588b1f16b7608bc6833c05f91ae670c22ef56f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/02/2020
ms.locfileid: "93189336"
---
# <a name="how-to-read-characters-from-a-string"></a><span data-ttu-id="a5f49-104">Como: ler caracteres de uma cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="a5f49-104">How to: Read characters from a string</span></span>

<span data-ttu-id="a5f49-105">Os exemplos de código a seguir mostram como ler caracteres de forma síncrona ou assíncrona de uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="a5f49-105">The following code examples show how to read characters synchronously or asynchronously from a string.</span></span>  
  
## <a name="example-read-characters-synchronously"></a><span data-ttu-id="a5f49-106">Exemplo: ler caracteres de forma síncrona</span><span class="sxs-lookup"><span data-stu-id="a5f49-106">Example: Read characters synchronously</span></span>
 <span data-ttu-id="a5f49-107">Este exemplo lê 13 caracteres de forma síncrona de uma cadeia de caracteres, armazena-os em uma matriz e exibe-os.</span><span class="sxs-lookup"><span data-stu-id="a5f49-107">This example reads 13 characters synchronously from a string, stores them in an array, and displays them.</span></span> <span data-ttu-id="a5f49-108">Em seguida, o exemplo lê os caracteres restantes na cadeia de caracteres, armazena-os na matriz começando pelo sexto elemento e exibe o conteúdo da matriz.</span><span class="sxs-lookup"><span data-stu-id="a5f49-108">The example then reads the rest of the characters in the string, stores them in the array starting at the sixth element, and displays the contents of the array.</span></span>  
  
 [!code-csharp[Conceptual.StringReader#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.stringreader/cs/source.cs#1)]
 [!code-vb[Conceptual.StringReader#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.stringreader/vb/source.vb#1)]  
  
## <a name="example-read-characters-asynchronously"></a><span data-ttu-id="a5f49-109">Exemplo: ler caracteres de forma assíncrona</span><span class="sxs-lookup"><span data-stu-id="a5f49-109">Example: Read characters asynchronously</span></span>  
 <span data-ttu-id="a5f49-110">O próximo exemplo é o código por trás de um aplicativo WPF.</span><span class="sxs-lookup"><span data-stu-id="a5f49-110">The next example is the code behind a WPF app.</span></span> <span data-ttu-id="a5f49-111">Na carga de janela, o exemplo lê todos os caracteres de forma assíncrona de um controle <xref:System.Windows.Controls.TextBox> e os armazena em uma matriz.</span><span class="sxs-lookup"><span data-stu-id="a5f49-111">On window load, the example asynchronously reads all characters from a <xref:System.Windows.Controls.TextBox> control and stores them in an array.</span></span> <span data-ttu-id="a5f49-112">Em seguida, ele grava cada letra ou caractere de espaço em branco de forma assíncrona em uma linha separada de um controle <xref:System.Windows.Controls.TextBlock>.</span><span class="sxs-lookup"><span data-stu-id="a5f49-112">It then asynchronously writes each letter or white-space character to a separate line of a <xref:System.Windows.Controls.TextBlock> control.</span></span>  
  
 [!code-csharp[Conceptual.StringReader#2](../../../samples/snippets/csharp/VS_Snippets_Wpf/StringReaderWriter/MainWindow.xaml.cs)]
 [!code-vb[Conceptual.StringReader#2](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StringReaderWriter/MainWindow.xaml.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="a5f49-113">Confira também</span><span class="sxs-lookup"><span data-stu-id="a5f49-113">See also</span></span>

- <xref:System.IO.StringReader>  
- <xref:System.IO.StringReader.Read%2A?displayProperty=nameWithType>  
- [<span data-ttu-id="a5f49-114">E/S de arquivo assíncrona</span><span class="sxs-lookup"><span data-stu-id="a5f49-114">Asynchronous file I/O</span></span>](asynchronous-file-i-o.md)  
- <span data-ttu-id="a5f49-115">[Como: criar uma listagem de diretório](/previous-versions/dotnet/netframework-4.0/5cf8zcfh(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="a5f49-115">[How to: Create a directory listing](/previous-versions/dotnet/netframework-4.0/5cf8zcfh(v=vs.100))</span></span>  
- [<span data-ttu-id="a5f49-116">Como: ler e gravar em um arquivo de dados recém-criado</span><span class="sxs-lookup"><span data-stu-id="a5f49-116">How to: Read and write to a newly created data file</span></span>](how-to-read-and-write-to-a-newly-created-data-file.md)  
- [<span data-ttu-id="a5f49-117">Como: abrir e anexar a um arquivo de log</span><span class="sxs-lookup"><span data-stu-id="a5f49-117">How to: Open and append to a log file</span></span>](how-to-open-and-append-to-a-log-file.md)  
- [<span data-ttu-id="a5f49-118">Como: ler texto de um arquivo</span><span class="sxs-lookup"><span data-stu-id="a5f49-118">How to: Read text from a file</span></span>](how-to-read-text-from-a-file.md)  
- [<span data-ttu-id="a5f49-119">Como: gravar texto em um arquivo</span><span class="sxs-lookup"><span data-stu-id="a5f49-119">How to: Write text to a file</span></span>](how-to-write-text-to-a-file.md)  
- [<span data-ttu-id="a5f49-120">Como: gravar caracteres em uma cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="a5f49-120">How to: Write characters to a string</span></span>](how-to-write-characters-to-a-string.md)  
- [<span data-ttu-id="a5f49-121">E/S de arquivo e de fluxo</span><span class="sxs-lookup"><span data-stu-id="a5f49-121">File and stream I/O</span></span>](index.md)
