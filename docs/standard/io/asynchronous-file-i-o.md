---
title: E/S de arquivo assíncrona
description: Leia sobre e/s de arquivo assíncrono no .NET. Aprenda métodos assíncronos para simplificar operações assíncronas, como ReadAsync, WriteAsync e muito mais.
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
- I/O [.NET], asynchronous I/O
- Stream class, synchronous I/O
- data streams, asynchronous streams
- Stream class, asynchronous I/O
- multiple I/O requests
- data streams, synchronous streams
ms.assetid: dbdd55e7-d6b9-4f9e-8abb-ab0edd4457f7
ms.openlocfilehash: a148e6e13ec0ee4ee469a0630f150199c5a3af13
ms.sourcegitcommit: 7588b1f16b7608bc6833c05f91ae670c22ef56f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/02/2020
ms.locfileid: "93188595"
---
# <a name="asynchronous-file-io"></a><span data-ttu-id="89d83-104">E/S de arquivo assíncrona</span><span class="sxs-lookup"><span data-stu-id="89d83-104">Asynchronous File I/O</span></span>

<span data-ttu-id="89d83-105">Operações assíncronas permitem que você execute operações de E/S que consomem muitos recursos sem bloquear o thread principal.</span><span class="sxs-lookup"><span data-stu-id="89d83-105">Asynchronous operations enable you to perform resource-intensive I/O operations without blocking the main thread.</span></span> <span data-ttu-id="89d83-106">Essa consideração de desempenho é particularmente importante em um aplicativo de armazenamento do Windows 8. x ou aplicativo de área de trabalho em que uma operação de fluxo demorado pode bloquear o thread da interface do usuário e fazer seu aplicativo aparecer como se não estiver funcionando.</span><span class="sxs-lookup"><span data-stu-id="89d83-106">This performance consideration is particularly important in a Windows 8.x Store app or desktop app where a time-consuming stream operation can block the UI thread and make your app appear as if it is not working.</span></span>

<span data-ttu-id="89d83-107">A partir do .NET Framework 4,5, os tipos de e/s incluem métodos assíncronos para simplificar operações assíncronas.</span><span class="sxs-lookup"><span data-stu-id="89d83-107">Starting with .NET Framework 4.5, the I/O types include async methods to simplify asynchronous operations.</span></span> <span data-ttu-id="89d83-108">Um método assíncrono contém `Async` em seu nome, como <xref:System.IO.Stream.ReadAsync%2A>, <xref:System.IO.Stream.WriteAsync%2A>, <xref:System.IO.Stream.CopyToAsync%2A>, <xref:System.IO.Stream.FlushAsync%2A>, <xref:System.IO.TextReader.ReadLineAsync%2A> e <xref:System.IO.TextReader.ReadToEndAsync%2A>.</span><span class="sxs-lookup"><span data-stu-id="89d83-108">An async method contains `Async` in its name, such as <xref:System.IO.Stream.ReadAsync%2A>, <xref:System.IO.Stream.WriteAsync%2A>, <xref:System.IO.Stream.CopyToAsync%2A>, <xref:System.IO.Stream.FlushAsync%2A>, <xref:System.IO.TextReader.ReadLineAsync%2A>, and <xref:System.IO.TextReader.ReadToEndAsync%2A>.</span></span> <span data-ttu-id="89d83-109">Esses métodos assíncronos são implementados em classes de fluxo, como <xref:System.IO.Stream>, <xref:System.IO.FileStream> e <xref:System.IO.MemoryStream>, e nas classes que são usadas para leitura ou gravação em fluxos, como <xref:System.IO.TextReader> e <xref:System.IO.TextWriter>.</span><span class="sxs-lookup"><span data-stu-id="89d83-109">These async methods are implemented on stream classes, such as <xref:System.IO.Stream>, <xref:System.IO.FileStream>, and <xref:System.IO.MemoryStream>, and on classes that are used for reading from or writing to streams, such <xref:System.IO.TextReader> and <xref:System.IO.TextWriter>.</span></span>

<span data-ttu-id="89d83-110">No .NET Framework 4 e versões anteriores, você precisa usar métodos como <xref:System.IO.Stream.BeginRead%2A> e <xref:System.IO.Stream.EndRead%2A> para implementar operações de e/s assíncronas.</span><span class="sxs-lookup"><span data-stu-id="89d83-110">In .NET Framework 4 and earlier versions, you have to use methods such as <xref:System.IO.Stream.BeginRead%2A> and <xref:System.IO.Stream.EndRead%2A> to implement asynchronous I/O operations.</span></span> <span data-ttu-id="89d83-111">Esses métodos ainda estão disponíveis em versões atuais do .NET para oferecer suporte a código herdado; no entanto, os métodos assíncronos ajudam você a implementar operações de e/s assíncronas com mais facilidade.</span><span class="sxs-lookup"><span data-stu-id="89d83-111">These methods are still available in current .NET versions to support legacy code; however, the async methods help you implement asynchronous I/O operations more easily.</span></span>

<span data-ttu-id="89d83-112">C# e Visual Basic têm duas palavras-chave cada para a programação assíncrona:</span><span class="sxs-lookup"><span data-stu-id="89d83-112">C# and Visual Basic each have two keywords for asynchronous programming:</span></span>

- <span data-ttu-id="89d83-113">`Async` (Visual Basic) ou modificador `async` (C#), que é usado para marcar um método que contém uma operação assíncrona.</span><span class="sxs-lookup"><span data-stu-id="89d83-113">`Async` (Visual Basic) or `async` (C#) modifier, which is used to mark a method that contains an asynchronous operation.</span></span>

- <span data-ttu-id="89d83-114">`Await` (Visual Basic) ou operador `await` (C#), que é aplicado ao resultado de um método assíncrono.</span><span class="sxs-lookup"><span data-stu-id="89d83-114">`Await` (Visual Basic) or `await` (C#) operator, which is applied to the result of an async method.</span></span>

<span data-ttu-id="89d83-115">Para implementar operações de E/S assíncronas, use essas palavras-chave em conjunto com os métodos assíncronos, conforme mostrado nos exemplos a seguir.</span><span class="sxs-lookup"><span data-stu-id="89d83-115">To implement asynchronous I/O operations, use these keywords in conjunction with the async methods, as shown in the following examples.</span></span> <span data-ttu-id="89d83-116">Para obter mais informações, confira [Programação assíncrona com async e await (C#)](../../csharp/programming-guide/concepts/async/index.md) ou [Programação assíncrona com Async e Await (Visual Basic)](../../visual-basic/programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="89d83-116">For more information, see [Asynchronous programming with async and await (C#)](../../csharp/programming-guide/concepts/async/index.md) or [Asynchronous Programming with Async and Await (Visual Basic)](../../visual-basic/programming-guide/concepts/async/index.md).</span></span>

<span data-ttu-id="89d83-117">O exemplo a seguir demonstra como usar dois objetos <xref:System.IO.FileStream> para copiar arquivos de forma assíncrona de um diretório para outro.</span><span class="sxs-lookup"><span data-stu-id="89d83-117">The following example demonstrates how to use two <xref:System.IO.FileStream> objects to copy files asynchronously from one directory to another.</span></span> <span data-ttu-id="89d83-118">Observe que o manipulador de eventos <xref:System.Web.UI.WebControls.Button.Click> para o controle <xref:System.Windows.Controls.Button> está marcado com o modificador `async`, pois ele chama um método assíncrono.</span><span class="sxs-lookup"><span data-stu-id="89d83-118">Notice that the <xref:System.Web.UI.WebControls.Button.Click> event handler for the <xref:System.Windows.Controls.Button> control is marked with the `async` modifier because it calls an asynchronous method.</span></span>

[!code-csharp[Asynchronous_File_IO_async#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Asynchronous_File_IO_async/cs/example.cs#1)]
[!code-vb[Asynchronous_File_IO_async#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Asynchronous_File_IO_async/vb/example.vb#1)]

<span data-ttu-id="89d83-119">O exemplo a seguir é semelhante ao anterior, mas usa objetos <xref:System.IO.StreamReader> e <xref:System.IO.StreamWriter> para ler e gravar o conteúdo de um arquivo de texto de forma assíncrona.</span><span class="sxs-lookup"><span data-stu-id="89d83-119">The next example is similar to the previous one but uses <xref:System.IO.StreamReader> and <xref:System.IO.StreamWriter> objects to read and write the contents of a text file asynchronously.</span></span>

[!code-csharp[Asynchronous_File_IO_async#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Asynchronous_File_IO_async/cs/example2.cs#2)]
[!code-vb[Asynchronous_File_IO_async#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Asynchronous_File_IO_async/vb/example2.vb#2)]

<span data-ttu-id="89d83-120">O exemplo a seguir mostra o arquivo code-behind e o arquivo XAML que são usados para abrir um arquivo como um <xref:System.IO.Stream> em um aplicativo da loja do Windows 8. x e ler seu conteúdo usando uma instância da <xref:System.IO.StreamReader> classe.</span><span class="sxs-lookup"><span data-stu-id="89d83-120">The next example shows the code-behind file and the XAML file that are used to open a file as a <xref:System.IO.Stream> in a Windows 8.x Store app, and read its contents by using an instance of the <xref:System.IO.StreamReader> class.</span></span> <span data-ttu-id="89d83-121">Ele usa os métodos assíncronos para abrir o arquivo como um fluxo e ler seu conteúdo.</span><span class="sxs-lookup"><span data-stu-id="89d83-121">It uses asynchronous methods to open the file as a stream and to read its contents.</span></span>

[!code-csharp[System.IO.WindowsRuntimeStorageExtensions#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.windowsruntimestorageextensions/cs/blankpage.xaml.cs#2)]
[!code-vb[System.IO.WindowsRuntimeStorageExtensions#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.windowsruntimestorageextensions/vb/blankpage.xaml.vb#2)]

[!code-xaml[System.IO.WindowsRuntimeStorageExtensions#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.windowsruntimestorageextensions/cs/blankpage.xaml#1)]

## <a name="see-also"></a><span data-ttu-id="89d83-122">Confira também</span><span class="sxs-lookup"><span data-stu-id="89d83-122">See also</span></span>

- <xref:System.IO.Stream>
- [<span data-ttu-id="89d83-123">Arquivo e e/s de fluxo</span><span class="sxs-lookup"><span data-stu-id="89d83-123">File and Stream I/O</span></span>](index.md)
- [<span data-ttu-id="89d83-124">Programação assíncrona com async e await (C#)</span><span class="sxs-lookup"><span data-stu-id="89d83-124">Asynchronous programming with async and await (C#)</span></span>](../../csharp/programming-guide/concepts/async/index.md)
- [<span data-ttu-id="89d83-125">Programação assíncrona com Async e Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="89d83-125">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/async/index.md)
