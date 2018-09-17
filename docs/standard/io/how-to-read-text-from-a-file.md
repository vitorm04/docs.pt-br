---
title: Como ler texto de um arquivo
ms.date: 06/19/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- streams, reading text from files
- reading text files
- reading data, text files
- data streams, reading text from files
- I/O [.NET Framework], reading text from files
ms.assetid: ed180baa-dfc6-4c69-a725-46e87edafb27
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8f979f3d09079f36d12408d0a82ef58e603da859
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45645886"
---
# <a name="how-to-read-text-from-a-file"></a><span data-ttu-id="cd35d-102">Como ler texto de um arquivo</span><span class="sxs-lookup"><span data-stu-id="cd35d-102">How to: Read Text from a File</span></span>
<span data-ttu-id="cd35d-103">Os exemplos a seguir mostram como ler de forma síncrona e assíncrona o texto de um arquivo de texto usando o .NET para aplicativos de área de trabalho.</span><span class="sxs-lookup"><span data-stu-id="cd35d-103">The following examples show how to read text synchronously and asynchronously from a text file using .NET for desktop apps.</span></span> <span data-ttu-id="cd35d-104">Nos dois exemplos, ao criar uma instância da classe <xref:System.IO.StreamReader>, você fornece o caminho relativo ou absoluto para o arquivo.</span><span class="sxs-lookup"><span data-stu-id="cd35d-104">In both examples, when you create the instance of the <xref:System.IO.StreamReader> class, you provide the relative or absolute path to the file.</span></span> <span data-ttu-id="cd35d-105">Os exemplos a seguir supõem que o arquivo denominado TestFile.txt está na mesma pasta que o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="cd35d-105">The following examples assume that the file named TestFile.txt is in the same folder as the application.</span></span>  
  
 <span data-ttu-id="cd35d-106">Esses exemplos de código não se aplicam ao desenvolvimento para Aplicativos da Windows Store porque o Windows Runtime fornece tipos diferentes de fluxos para ler e gravar em arquivos.</span><span class="sxs-lookup"><span data-stu-id="cd35d-106">These code examples do not apply to developing for Windows Store Apps because the Windows Runtime provides different stream types for reading and writing to files.</span></span> <span data-ttu-id="cd35d-107">Para obter um exemplo que mostra como ler o texto de um arquivo em um aplicativo da Windows Store, veja [Início rápido: ler e gravar arquivos](https://docs.microsoft.com/previous-versions/windows/apps/hh758325(v=win.10)).</span><span class="sxs-lookup"><span data-stu-id="cd35d-107">For an example that shows how to read text from a file in a Windows Store app, see [Quickstart: Reading and writing files](https://docs.microsoft.com/previous-versions/windows/apps/hh758325(v=win.10)).</span></span> <span data-ttu-id="cd35d-108">Para obter exemplos que mostram como converter entre fluxos do .NET Framework e fluxos do Windows Runtime, veja [Como converter entre fluxos do .NET Framework e do Windows Runtime](../../../docs/standard/io/how-to-convert-between-dotnet-streams-and-winrt-streams.md).</span><span class="sxs-lookup"><span data-stu-id="cd35d-108">For examples that show how to convert between .NET Framework streams and Windows runtime streams, see [How to: Convert Between .NET Framework Streams and Windows Runtime Streams](../../../docs/standard/io/how-to-convert-between-dotnet-streams-and-winrt-streams.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="cd35d-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="cd35d-109">Example</span></span>  
 <span data-ttu-id="cd35d-110">O primeiro exemplo mostra uma operação de leitura síncrona em um aplicativo de console.</span><span class="sxs-lookup"><span data-stu-id="cd35d-110">The following example shows a synchronous read operation within a console application.</span></span> <span data-ttu-id="cd35d-111">Neste exemplo, o arquivo de texto é aberto usando um leitor de fluxo, o conteúdo é copiado para uma cadeia de caracteres e a cadeia de caracteres é enviada para o console.</span><span class="sxs-lookup"><span data-stu-id="cd35d-111">In this example, the text file is opened using a stream reader, the contents are copied to a string, and the string is output to the console.</span></span>  
  
 [!code-csharp[Conceptual.BasicIO.TextFiles#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source3.cs#3)]
 [!code-vb[Conceptual.BasicIO.TextFiles#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source3.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="cd35d-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="cd35d-112">Example</span></span>  
 <span data-ttu-id="cd35d-113">O exemplo a seguir mostra uma operação de leitura assíncrona em um aplicativo do WPF (Windows Presentation Foundation).</span><span class="sxs-lookup"><span data-stu-id="cd35d-113">The following example shows an asynchronous read operation in a Windows Presentation Foundation (WPF) application.</span></span>  
  
 [!code-csharp[Conceptual.BasicIO.TextFiles#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source6.cs#6)]
 [!code-vb[Conceptual.BasicIO.TextFiles#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source6.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="cd35d-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cd35d-114">See also</span></span>

- <xref:System.IO.StreamReader>  
- <xref:System.IO.File.OpenText%2A?displayProperty=nameWithType>  
- <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>  
- [<span data-ttu-id="cd35d-115">E/S de arquivo assíncrona</span><span class="sxs-lookup"><span data-stu-id="cd35d-115">Asynchronous File I/O</span></span>](../../../docs/standard/io/asynchronous-file-i-o.md)  
- [<span data-ttu-id="cd35d-116">NIB: Como criar uma listagem de diretório</span><span class="sxs-lookup"><span data-stu-id="cd35d-116">NIB: How to: Create a Directory Listing</span></span>](https://msdn.microsoft.com/library/4d2772b1-b991-4532-a8a6-6ef733277e69)  
- [<span data-ttu-id="cd35d-117">Início rápido: ler e gravar arquivos</span><span class="sxs-lookup"><span data-stu-id="cd35d-117">Quickstart: Reading and writing files</span></span>](https://msdn.microsoft.com/library/windows/apps/hh758325.aspx)  
- [<span data-ttu-id="cd35d-118">Como converter entre fluxos do .NET Framework e do Tempo de Execução do Windows</span><span class="sxs-lookup"><span data-stu-id="cd35d-118">How to: Convert Between .NET Framework Streams and Windows Runtime Streams</span></span>](../../../docs/standard/io/how-to-convert-between-dotnet-streams-and-winrt-streams.md)  
- [<span data-ttu-id="cd35d-119">Como ler e gravar em um arquivo de dados recém-criado</span><span class="sxs-lookup"><span data-stu-id="cd35d-119">How to: Read and Write to a Newly Created Data File</span></span>](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
- [<span data-ttu-id="cd35d-120">Como abrir e acrescentar a um arquivo de log</span><span class="sxs-lookup"><span data-stu-id="cd35d-120">How to: Open and Append to a Log File</span></span>](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
- [<span data-ttu-id="cd35d-121">Como gravar texto em um arquivo</span><span class="sxs-lookup"><span data-stu-id="cd35d-121">How to: Write Text to a File</span></span>](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
- [<span data-ttu-id="cd35d-122">Como ler caracteres de uma cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="cd35d-122">How to: Read Characters from a String</span></span>](../../../docs/standard/io/how-to-read-characters-from-a-string.md)  
- [<span data-ttu-id="cd35d-123">Como gravar caracteres em uma cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="cd35d-123">How to: Write Characters to a String</span></span>](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
- [<span data-ttu-id="cd35d-124">E/S de arquivo e de fluxo</span><span class="sxs-lookup"><span data-stu-id="cd35d-124">File and Stream I/O</span></span>](../../../docs/standard/io/index.md)
