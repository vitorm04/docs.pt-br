---
title: 'Como: ler texto de um arquivo'
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
ms.openlocfilehash: c46ccaf70d4d1aec030fb61bd8b2924d986e19d1
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291754"
---
# <a name="how-to-read-text-from-a-file"></a><span data-ttu-id="8e6e1-102">Como: ler texto de um arquivo</span><span class="sxs-lookup"><span data-stu-id="8e6e1-102">How to: Read text from a file</span></span>
<span data-ttu-id="8e6e1-103">Os exemplos a seguir mostram como ler de forma síncrona e assíncrona o texto de um arquivo de texto usando o .NET para aplicativos de área de trabalho.</span><span class="sxs-lookup"><span data-stu-id="8e6e1-103">The following examples show how to read text synchronously and asynchronously from a text file using .NET for desktop apps.</span></span> <span data-ttu-id="8e6e1-104">Nos dois exemplos, ao criar uma instância da classe <xref:System.IO.StreamReader>, você fornece o caminho relativo ou absoluto para o arquivo.</span><span class="sxs-lookup"><span data-stu-id="8e6e1-104">In both examples, when you create the instance of the <xref:System.IO.StreamReader> class, you provide the relative or absolute path to the file.</span></span>
  
> [!NOTE]
> <span data-ttu-id="8e6e1-105">Esses exemplos de código não se aplicam ao desenvolvimento para aplicativos UWP (Universal do Windows) porque o Windows Runtime fornece diferentes tipos de fluxos para leitura e gravação em arquivos.</span><span class="sxs-lookup"><span data-stu-id="8e6e1-105">These code examples do not apply to developing for Universal Windows (UWP) apps, because the Windows Runtime provides different stream types for reading and writing to files.</span></span> <span data-ttu-id="8e6e1-106">Para obter um exemplo que mostra como ler o texto de um arquivo em um aplicativo UWP, consulte [início rápido: lendo e gravando arquivos](https://docs.microsoft.com/previous-versions/windows/apps/hh758325(v=win.10)).</span><span class="sxs-lookup"><span data-stu-id="8e6e1-106">For an example that shows how to read text from a file in a UWP app, see [Quickstart: Reading and writing files](https://docs.microsoft.com/previous-versions/windows/apps/hh758325(v=win.10)).</span></span> <span data-ttu-id="8e6e1-107">Para obter exemplos que mostram como converter entre fluxos de .NET Framework e Windows Runtime fluxos, consulte [como converter entre fluxos de .NET Framework e fluxos de Windows Runtime](how-to-convert-between-dotnet-streams-and-winrt-streams.md).</span><span class="sxs-lookup"><span data-stu-id="8e6e1-107">For examples that show how to convert between .NET Framework streams and Windows Runtime streams, see [How to: Convert between .NET Framework streams and Windows Runtime streams](how-to-convert-between-dotnet-streams-and-winrt-streams.md).</span></span>  
  
## <a name="example-synchronous-read-in-a-console-app"></a><span data-ttu-id="8e6e1-108">Exemplo: leitura síncrona em um aplicativo de console</span><span class="sxs-lookup"><span data-stu-id="8e6e1-108">Example: Synchronous read in a console app</span></span>  
<span data-ttu-id="8e6e1-109">O exemplo a seguir mostra uma operação de leitura síncrona em um aplicativo de console.</span><span class="sxs-lookup"><span data-stu-id="8e6e1-109">The following example shows a synchronous read operation within a console app.</span></span> <span data-ttu-id="8e6e1-110">Esse exemplo abre o arquivo de texto usando um leitor de fluxo, copia o conteúdo para uma cadeia de caracteres e gera a cadeia de caracteres no console.</span><span class="sxs-lookup"><span data-stu-id="8e6e1-110">This example opens the text file using a stream reader, copies the contents to a string, and outputs the string to the console.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="8e6e1-111">O exemplo pressupõe que um arquivo chamado *TestFile.txt* já exista na mesma pasta do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8e6e1-111">The example assumes that a file named *TestFile.txt* already exists in the same folder as the app.</span></span>  

 [!code-csharp[Conceptual.BasicIO.TextFiles#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source3.cs#3)]
 [!code-vb[Conceptual.BasicIO.TextFiles#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source3.vb#3)]  
  
## <a name="example-asynchronous-read-in-a-wpf-app"></a><span data-ttu-id="8e6e1-112">Exemplo: leitura assíncrona em um aplicativo WPF</span><span class="sxs-lookup"><span data-stu-id="8e6e1-112">Example: Asynchronous read in a WPF app</span></span>
 <span data-ttu-id="8e6e1-113">O exemplo a seguir mostra uma operação de leitura assíncrona em um aplicativo WPF (Windows Presentation Foundation).</span><span class="sxs-lookup"><span data-stu-id="8e6e1-113">The following example shows an asynchronous read operation in a Windows Presentation Foundation (WPF) app.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="8e6e1-114">O exemplo pressupõe que um arquivo chamado *TestFile.txt* já exista na mesma pasta do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8e6e1-114">The example assumes that a file named *TestFile.txt* already exists in the same folder as the app.</span></span>  

 [!code-csharp[TextFiles](../../../samples/snippets/csharp/VS_Snippets_Wpf/TextFiles/MainWindow.xaml.cs)]
 [!code-vb[TextFiles](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextFiles/MainWindow.xaml.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="8e6e1-115">Veja também</span><span class="sxs-lookup"><span data-stu-id="8e6e1-115">See also</span></span>

- <xref:System.IO.StreamReader>  
- <xref:System.IO.File.OpenText%2A?displayProperty=nameWithType>  
- <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>  
- [<span data-ttu-id="8e6e1-116">E/S de arquivo assíncrona</span><span class="sxs-lookup"><span data-stu-id="8e6e1-116">Asynchronous file I/O</span></span>](asynchronous-file-i-o.md)  
- <span data-ttu-id="8e6e1-117">[Como: criar uma listagem de diretório](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5cf8zcfh(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="8e6e1-117">[How to: Create a directory listing](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5cf8zcfh(v=vs.100))</span></span>  
- [<span data-ttu-id="8e6e1-118">Início rápido: ler e gravar arquivos</span><span class="sxs-lookup"><span data-stu-id="8e6e1-118">Quickstart: Reading and writing files</span></span>](https://docs.microsoft.com/previous-versions/windows/apps/hh758325%28v=win.10%29)  
- [<span data-ttu-id="8e6e1-119">Como converter entre fluxos de .NET Framework e fluxos de Windows Runtime</span><span class="sxs-lookup"><span data-stu-id="8e6e1-119">How to: Convert between .NET Framework streams and Windows Runtime streams</span></span>](how-to-convert-between-dotnet-streams-and-winrt-streams.md)  
- [<span data-ttu-id="8e6e1-120">Como: ler e gravar em um arquivo de dados recém-criado</span><span class="sxs-lookup"><span data-stu-id="8e6e1-120">How to: Read and write to a newly created data file</span></span>](how-to-read-and-write-to-a-newly-created-data-file.md)  
- [<span data-ttu-id="8e6e1-121">Como: abrir e anexar a um arquivo de log</span><span class="sxs-lookup"><span data-stu-id="8e6e1-121">How to: Open and append to a log file</span></span>](how-to-open-and-append-to-a-log-file.md)  
- [<span data-ttu-id="8e6e1-122">Como: gravar texto em um arquivo</span><span class="sxs-lookup"><span data-stu-id="8e6e1-122">How to: Write text to a file</span></span>](how-to-write-text-to-a-file.md)  
- [<span data-ttu-id="8e6e1-123">Como: ler caracteres de uma cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="8e6e1-123">How to: Read characters from a string</span></span>](how-to-read-characters-from-a-string.md)  
- [<span data-ttu-id="8e6e1-124">Como: gravar caracteres em uma cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="8e6e1-124">How to: Write characters to a string</span></span>](how-to-write-characters-to-a-string.md)  
- [<span data-ttu-id="8e6e1-125">E/S de arquivo e de fluxo</span><span class="sxs-lookup"><span data-stu-id="8e6e1-125">File and stream I/O</span></span>](index.md)
