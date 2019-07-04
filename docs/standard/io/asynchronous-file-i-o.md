---
title: E/S de arquivo assíncrona
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- streams, synchronous streams
- asynchronous I/O
- synchronous I/O
- streams, asynchronous streams
- I/O [.NET Framework], asynchronous I/O
- Stream class, synchronous I/O
- data streams, asynchronous streams
- Stream class, asynchronous I/O
- multiple I/O requests
- data streams, synchronous streams
ms.assetid: dbdd55e7-d6b9-4f9e-8abb-ab0edd4457f7
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b045ad7e9a808b3e2b8d89750001ec9c4a33c005
ms.sourcegitcommit: a8d3504f0eae1a40bda2b06bd441ba01f1631ef0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/18/2019
ms.locfileid: "67170743"
---
# <a name="asynchronous-file-io"></a><span data-ttu-id="f6039-102">E/S de arquivo assíncrona</span><span class="sxs-lookup"><span data-stu-id="f6039-102">Asynchronous File I/O</span></span>

<span data-ttu-id="f6039-103">Operações assíncronas permitem que você execute operações de E/S que consomem muitos recursos sem bloquear o thread principal.</span><span class="sxs-lookup"><span data-stu-id="f6039-103">Asynchronous operations enable you to perform resource-intensive I/O operations without blocking the main thread.</span></span> <span data-ttu-id="f6039-104">Essa consideração sobre o desempenho é particularmente importante em um aplicativo [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] ou aplicativo de desktop em que uma operação demorada de fluxo pode bloquear o thread de interface do usuário e fazer seu aplicativo parecer como se não estivesse funcionando.</span><span class="sxs-lookup"><span data-stu-id="f6039-104">This performance consideration is particularly important in a [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] app or desktop app where a time-consuming stream operation can block the UI thread and make your app appear as if it is not working.</span></span>

<span data-ttu-id="f6039-105">Do .NET Framework 4.5 em diante, os tipos de E/S incluem métodos assíncronos para simplificar operações assíncronas.</span><span class="sxs-lookup"><span data-stu-id="f6039-105">Starting with the .NET Framework 4.5, the I/O types include async methods to simplify asynchronous operations.</span></span> <span data-ttu-id="f6039-106">Um método assíncrono contém `Async` em seu nome, como <xref:System.IO.Stream.ReadAsync%2A>, <xref:System.IO.Stream.WriteAsync%2A>, <xref:System.IO.Stream.CopyToAsync%2A>, <xref:System.IO.Stream.FlushAsync%2A>, <xref:System.IO.TextReader.ReadLineAsync%2A> e <xref:System.IO.TextReader.ReadToEndAsync%2A>.</span><span class="sxs-lookup"><span data-stu-id="f6039-106">An async method contains `Async` in its name, such as <xref:System.IO.Stream.ReadAsync%2A>, <xref:System.IO.Stream.WriteAsync%2A>, <xref:System.IO.Stream.CopyToAsync%2A>, <xref:System.IO.Stream.FlushAsync%2A>, <xref:System.IO.TextReader.ReadLineAsync%2A>, and <xref:System.IO.TextReader.ReadToEndAsync%2A>.</span></span> <span data-ttu-id="f6039-107">Esses métodos assíncronos são implementados em classes de fluxo, como <xref:System.IO.Stream>, <xref:System.IO.FileStream> e <xref:System.IO.MemoryStream>, e nas classes que são usadas para leitura ou gravação em fluxos, como <xref:System.IO.TextReader> e <xref:System.IO.TextWriter>.</span><span class="sxs-lookup"><span data-stu-id="f6039-107">These async methods are implemented on stream classes, such as <xref:System.IO.Stream>, <xref:System.IO.FileStream>, and <xref:System.IO.MemoryStream>, and on classes that are used for reading from or writing to streams, such <xref:System.IO.TextReader> and <xref:System.IO.TextWriter>.</span></span>

<span data-ttu-id="f6039-108">No .NET Framework 4, e em versões anteriores, você precisa usar métodos como <xref:System.IO.Stream.BeginRead%2A> e <xref:System.IO.Stream.EndRead%2A> para implementar operações de E/S assíncronas.</span><span class="sxs-lookup"><span data-stu-id="f6039-108">In the .NET Framework 4 and earlier versions, you have to use methods such as <xref:System.IO.Stream.BeginRead%2A> and <xref:System.IO.Stream.EndRead%2A> to implement asynchronous I/O operations.</span></span> <span data-ttu-id="f6039-109">Esses métodos ainda estão disponíveis no .NET Framework 4.5 para dar suporte ao código herdado; no entanto, os métodos assíncronos ajudarão você a implementar operações de E/S assíncronas com mais facilidade.</span><span class="sxs-lookup"><span data-stu-id="f6039-109">These methods are still available in the .NET Framework 4.5 to support legacy code; however, the async methods help you implement asynchronous I/O operations more easily.</span></span>

<span data-ttu-id="f6039-110">C# e Visual Basic têm duas palavras-chave cada para a programação assíncrona:</span><span class="sxs-lookup"><span data-stu-id="f6039-110">C# and Visual Basic each have two keywords for asynchronous programming:</span></span>

- <span data-ttu-id="f6039-111">`Async` (Visual Basic) ou modificador `async` (C#), que é usado para marcar um método que contém uma operação assíncrona.</span><span class="sxs-lookup"><span data-stu-id="f6039-111">`Async` (Visual Basic) or `async` (C#) modifier, which is used to mark a method that contains an asynchronous operation.</span></span>

- <span data-ttu-id="f6039-112">`Await` (Visual Basic) ou operador `await` (C#), que é aplicado ao resultado de um método assíncrono.</span><span class="sxs-lookup"><span data-stu-id="f6039-112">`Await` (Visual Basic) or `await` (C#) operator, which is applied to the result of an async method.</span></span>

<span data-ttu-id="f6039-113">Para implementar operações de E/S assíncronas, use essas palavras-chave em conjunto com os métodos assíncronos, conforme mostrado nos exemplos a seguir.</span><span class="sxs-lookup"><span data-stu-id="f6039-113">To implement asynchronous I/O operations, use these keywords in conjunction with the async methods, as shown in the following examples.</span></span> <span data-ttu-id="f6039-114">Para obter mais informações, confira [Programação assíncrona com async e await (C#)](../../csharp/programming-guide/concepts/async/index.md) ou [Programação assíncrona com Async e Await (Visual Basic)](../../visual-basic/programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="f6039-114">For more information, see [Asynchronous programming with async and await (C#)](../../csharp/programming-guide/concepts/async/index.md) or [Asynchronous Programming with Async and Await (Visual Basic)](../../visual-basic/programming-guide/concepts/async/index.md).</span></span>

<span data-ttu-id="f6039-115">O exemplo a seguir demonstra como usar dois objetos <xref:System.IO.FileStream> para copiar arquivos de forma assíncrona de um diretório para outro.</span><span class="sxs-lookup"><span data-stu-id="f6039-115">The following example demonstrates how to use two <xref:System.IO.FileStream> objects to copy files asynchronously from one directory to another.</span></span> <span data-ttu-id="f6039-116">Observe que o manipulador de eventos <xref:System.Web.UI.WebControls.Button.Click> para o controle <xref:System.Windows.Controls.Button> está marcado com o modificador `async`, pois ele chama um método assíncrono.</span><span class="sxs-lookup"><span data-stu-id="f6039-116">Notice that the <xref:System.Web.UI.WebControls.Button.Click> event handler for the <xref:System.Windows.Controls.Button> control is marked with the `async` modifier because it calls an asynchronous method.</span></span>

[!code-csharp[Asynchronous_File_IO_async#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Asynchronous_File_IO_async/cs/example.cs#1)]
[!code-vb[Asynchronous_File_IO_async#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Asynchronous_File_IO_async/vb/example.vb#1)]

<span data-ttu-id="f6039-117">O exemplo a seguir é semelhante ao anterior, mas usa objetos <xref:System.IO.StreamReader> e <xref:System.IO.StreamWriter> para ler e gravar o conteúdo de um arquivo de texto de forma assíncrona.</span><span class="sxs-lookup"><span data-stu-id="f6039-117">The next example is similar to the previous one but uses <xref:System.IO.StreamReader> and <xref:System.IO.StreamWriter> objects to read and write the contents of a text file asynchronously.</span></span>

[!code-csharp[Asynchronous_File_IO_async#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Asynchronous_File_IO_async/cs/example2.cs#2)]
[!code-vb[Asynchronous_File_IO_async#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Asynchronous_File_IO_async/vb/example2.vb#2)]

<span data-ttu-id="f6039-118">O exemplo a seguir mostra o arquivo code-behind e o arquivo XAML que são usados para abrir um arquivo como um <xref:System.IO.Stream> em um aplicativo [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)], e ler seu conteúdo usando uma instância da classe <xref:System.IO.StreamReader>.</span><span class="sxs-lookup"><span data-stu-id="f6039-118">The next example shows the code-behind file and the XAML file that are used to open a file as a <xref:System.IO.Stream> in a [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] app, and read its contents by using an instance of the <xref:System.IO.StreamReader> class.</span></span> <span data-ttu-id="f6039-119">Ele usa os métodos assíncronos para abrir o arquivo como um fluxo e ler seu conteúdo.</span><span class="sxs-lookup"><span data-stu-id="f6039-119">It uses asynchronous methods to open the file as a stream and to read its contents.</span></span>

[!code-csharp[System.IO.WindowsRuntimeStorageExtensions#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.windowsruntimestorageextensions/cs/blankpage.xaml.cs#2)]
[!code-vb[System.IO.WindowsRuntimeStorageExtensions#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.windowsruntimestorageextensions/vb/blankpage.xaml.vb#2)]

[!code-xaml[System.IO.WindowsRuntimeStorageExtensions#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.windowsruntimestorageextensions/cs/blankpage.xaml#1)]

## <a name="see-also"></a><span data-ttu-id="f6039-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f6039-120">See also</span></span>

- <xref:System.IO.Stream>
- [<span data-ttu-id="f6039-121">E/S de arquivo e de fluxo</span><span class="sxs-lookup"><span data-stu-id="f6039-121">File and Stream I/O</span></span>](index.md)
- [<span data-ttu-id="f6039-122">Programação assíncrona com async e await (C#)</span><span class="sxs-lookup"><span data-stu-id="f6039-122">Asynchronous programming with async and await (C#)</span></span>](../../csharp/programming-guide/concepts/async/index.md)
- [<span data-ttu-id="f6039-123">Programação assíncrona com Async e Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f6039-123">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/async/index.md)
