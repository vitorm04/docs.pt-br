---
title: 'Como: Ler texto de um arquivo'
ms.date: 01/03/2019
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
ms.openlocfilehash: 8676e5f0acd0646b4854df7dde060ec15548ec3e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78155718"
---
# <a name="how-to-read-text-from-a-file"></a><span data-ttu-id="71f84-102">Como: Ler texto de um arquivo</span><span class="sxs-lookup"><span data-stu-id="71f84-102">How to: Read text from a file</span></span>
<span data-ttu-id="71f84-103">Os exemplos a seguir mostram como ler de forma síncrona e assíncrona o texto de um arquivo de texto usando o .NET para aplicativos de área de trabalho.</span><span class="sxs-lookup"><span data-stu-id="71f84-103">The following examples show how to read text synchronously and asynchronously from a text file using .NET for desktop apps.</span></span> <span data-ttu-id="71f84-104">Nos dois exemplos, ao criar uma instância da classe <xref:System.IO.StreamReader>, você fornece o caminho relativo ou absoluto para o arquivo.</span><span class="sxs-lookup"><span data-stu-id="71f84-104">In both examples, when you create the instance of the <xref:System.IO.StreamReader> class, you provide the relative or absolute path to the file.</span></span>
  
> [!NOTE]
> <span data-ttu-id="71f84-105">Esses exemplos de código não se aplicam ao desenvolvimento para aplicativos UWP (Universal do Windows) porque o Windows Runtime fornece diferentes tipos de fluxos para leitura e gravação em arquivos.</span><span class="sxs-lookup"><span data-stu-id="71f84-105">These code examples do not apply to developing for Universal Windows (UWP) apps, because the Windows Runtime provides different stream types for reading and writing to files.</span></span> <span data-ttu-id="71f84-106">Para um exemplo que mostra como ler texto de um arquivo em um aplicativo UWP, consulte [Quickstart: Leitura e escrita de arquivos](https://docs.microsoft.com/previous-versions/windows/apps/hh758325(v=win.10)).</span><span class="sxs-lookup"><span data-stu-id="71f84-106">For an example that shows how to read text from a file in a UWP app, see [Quickstart: Reading and writing files](https://docs.microsoft.com/previous-versions/windows/apps/hh758325(v=win.10)).</span></span> <span data-ttu-id="71f84-107">Para exemplos que mostram como converter entre fluxos .NET Framework e fluxos de execução do Windows, consulte [Como: Converter entre fluxos .NET Framework e fluxos de execução do Windows](../../../docs/standard/io/how-to-convert-between-dotnet-streams-and-winrt-streams.md).</span><span class="sxs-lookup"><span data-stu-id="71f84-107">For examples that show how to convert between .NET Framework streams and Windows Runtime streams, see [How to: Convert between .NET Framework streams and Windows Runtime streams](../../../docs/standard/io/how-to-convert-between-dotnet-streams-and-winrt-streams.md).</span></span>  
  
## <a name="example-synchronous-read-in-a-console-app"></a><span data-ttu-id="71f84-108">Exemplo: Leitura síncrona em um aplicativo de console</span><span class="sxs-lookup"><span data-stu-id="71f84-108">Example: Synchronous read in a console app</span></span>  
<span data-ttu-id="71f84-109">O exemplo a seguir mostra uma operação de leitura síncrona em um aplicativo de console.</span><span class="sxs-lookup"><span data-stu-id="71f84-109">The following example shows a synchronous read operation within a console app.</span></span> <span data-ttu-id="71f84-110">Esse exemplo abre o arquivo de texto usando um leitor de fluxo, copia o conteúdo para uma cadeia de caracteres e gera a cadeia de caracteres no console.</span><span class="sxs-lookup"><span data-stu-id="71f84-110">This example opens the text file using a stream reader, copies the contents to a string, and outputs the string to the console.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="71f84-111">O exemplo pressupõe que um arquivo chamado *TestFile.txt* já exista na mesma pasta do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="71f84-111">The example assumes that a file named *TestFile.txt* already exists in the same folder as the app.</span></span>  

 [!code-csharp[Conceptual.BasicIO.TextFiles#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source3.cs#3)]
 [!code-vb[Conceptual.BasicIO.TextFiles#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source3.vb#3)]  
  
## <a name="example-asynchronous-read-in-a-wpf-app"></a><span data-ttu-id="71f84-112">Exemplo: Leitura assíncrona em um aplicativo WPF</span><span class="sxs-lookup"><span data-stu-id="71f84-112">Example: Asynchronous read in a WPF app</span></span>
 <span data-ttu-id="71f84-113">O exemplo a seguir mostra uma operação de leitura assíncrona em um aplicativo WPF (Windows Presentation Foundation).</span><span class="sxs-lookup"><span data-stu-id="71f84-113">The following example shows an asynchronous read operation in a Windows Presentation Foundation (WPF) app.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="71f84-114">O exemplo pressupõe que um arquivo chamado *TestFile.txt* já exista na mesma pasta do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="71f84-114">The example assumes that a file named *TestFile.txt* already exists in the same folder as the app.</span></span>  

 [!code-csharp[TextFiles](../../../samples/snippets/csharp/VS_Snippets_Wpf/TextFiles/MainWindow.xaml.cs)]
 [!code-vb[TextFiles](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextFiles/MainWindow.xaml.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="71f84-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="71f84-115">See also</span></span>

- <xref:System.IO.StreamReader>  
- <xref:System.IO.File.OpenText%2A?displayProperty=nameWithType>  
- <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>  
- [<span data-ttu-id="71f84-116">I/O do arquivo assíncrono</span><span class="sxs-lookup"><span data-stu-id="71f84-116">Asynchronous file I/O</span></span>](../../../docs/standard/io/asynchronous-file-i-o.md)  
- <span data-ttu-id="71f84-117">[Como: Criar uma listagem de diretórios](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5cf8zcfh(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="71f84-117">[How to: Create a directory listing](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5cf8zcfh(v=vs.100))</span></span>  
- [<span data-ttu-id="71f84-118">Início rápido: ler e gravar arquivos</span><span class="sxs-lookup"><span data-stu-id="71f84-118">Quickstart: Reading and writing files</span></span>](https://docs.microsoft.com/previous-versions/windows/apps/hh758325%28v=win.10%29)  
- [<span data-ttu-id="71f84-119">Como: Converter entre fluxos .NET Framework e fluxos de tempo de execução do Windows</span><span class="sxs-lookup"><span data-stu-id="71f84-119">How to: Convert between .NET Framework streams and Windows Runtime streams</span></span>](../../../docs/standard/io/how-to-convert-between-dotnet-streams-and-winrt-streams.md)  
- [<span data-ttu-id="71f84-120">Como: Ler e gravar em um arquivo de dados recém-criado</span><span class="sxs-lookup"><span data-stu-id="71f84-120">How to: Read and write to a newly created data file</span></span>](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
- [<span data-ttu-id="71f84-121">Como: Abrir e anexar a um arquivo de log</span><span class="sxs-lookup"><span data-stu-id="71f84-121">How to: Open and append to a log file</span></span>](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
- [<span data-ttu-id="71f84-122">Como: Escrever texto para um arquivo</span><span class="sxs-lookup"><span data-stu-id="71f84-122">How to: Write text to a file</span></span>](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
- [<span data-ttu-id="71f84-123">Como: Ler caracteres de uma seqüência</span><span class="sxs-lookup"><span data-stu-id="71f84-123">How to: Read characters from a string</span></span>](../../../docs/standard/io/how-to-read-characters-from-a-string.md)  
- [<span data-ttu-id="71f84-124">Como: Escrever caracteres em uma seqüência</span><span class="sxs-lookup"><span data-stu-id="71f84-124">How to: Write characters to a string</span></span>](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
- [<span data-ttu-id="71f84-125">E/S de arquivo e de fluxo</span><span class="sxs-lookup"><span data-stu-id="71f84-125">File and stream I/O</span></span>](../../../docs/standard/io/index.md)
