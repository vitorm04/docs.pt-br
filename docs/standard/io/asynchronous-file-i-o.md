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
ms.openlocfilehash: b39373239d6aefaa671afebbb85dc2156866358f
ms.sourcegitcommit: 81ad1f09b93f3b3e6706a7f2e4ddf50ef229ea3d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/20/2019
ms.locfileid: "74204811"
---
# <a name="asynchronous-file-io"></a>E/S de arquivo assíncrona

Operações assíncronas permitem que você execute operações de E/S que consomem muitos recursos sem bloquear o thread principal. This performance consideration is particularly important in a Windows 8.x Store app or desktop app where a time-consuming stream operation can block the UI thread and make your app appear as if it is not working.

Do .NET Framework 4.5 em diante, os tipos de E/S incluem métodos assíncronos para simplificar operações assíncronas. Um método assíncrono contém `Async` em seu nome, como <xref:System.IO.Stream.ReadAsync%2A>, <xref:System.IO.Stream.WriteAsync%2A>, <xref:System.IO.Stream.CopyToAsync%2A>, <xref:System.IO.Stream.FlushAsync%2A>, <xref:System.IO.TextReader.ReadLineAsync%2A> e <xref:System.IO.TextReader.ReadToEndAsync%2A>. Esses métodos assíncronos são implementados em classes de fluxo, como <xref:System.IO.Stream>, <xref:System.IO.FileStream> e <xref:System.IO.MemoryStream>, e nas classes que são usadas para leitura ou gravação em fluxos, como <xref:System.IO.TextReader> e <xref:System.IO.TextWriter>.

No .NET Framework 4, e em versões anteriores, você precisa usar métodos como <xref:System.IO.Stream.BeginRead%2A> e <xref:System.IO.Stream.EndRead%2A> para implementar operações de E/S assíncronas. Esses métodos ainda estão disponíveis no .NET Framework 4.5 para dar suporte ao código herdado; no entanto, os métodos assíncronos ajudarão você a implementar operações de E/S assíncronas com mais facilidade.

C# e Visual Basic têm duas palavras-chave cada para a programação assíncrona:

- `Async` (Visual Basic) ou modificador `async` (C#), que é usado para marcar um método que contém uma operação assíncrona.

- `Await` (Visual Basic) ou operador `await` (C#), que é aplicado ao resultado de um método assíncrono.

Para implementar operações de E/S assíncronas, use essas palavras-chave em conjunto com os métodos assíncronos, conforme mostrado nos exemplos a seguir. Para obter mais informações, confira [Programação assíncrona com async e await (C#)](../../csharp/programming-guide/concepts/async/index.md) ou [Programação assíncrona com Async e Await (Visual Basic)](../../visual-basic/programming-guide/concepts/async/index.md).

O exemplo a seguir demonstra como usar dois objetos <xref:System.IO.FileStream> para copiar arquivos de forma assíncrona de um diretório para outro. Observe que o manipulador de eventos <xref:System.Web.UI.WebControls.Button.Click> para o controle <xref:System.Windows.Controls.Button> está marcado com o modificador `async`, pois ele chama um método assíncrono.

[!code-csharp[Asynchronous_File_IO_async#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Asynchronous_File_IO_async/cs/example.cs#1)]
[!code-vb[Asynchronous_File_IO_async#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Asynchronous_File_IO_async/vb/example.vb#1)]

O exemplo a seguir é semelhante ao anterior, mas usa objetos <xref:System.IO.StreamReader> e <xref:System.IO.StreamWriter> para ler e gravar o conteúdo de um arquivo de texto de forma assíncrona.

[!code-csharp[Asynchronous_File_IO_async#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Asynchronous_File_IO_async/cs/example2.cs#2)]
[!code-vb[Asynchronous_File_IO_async#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Asynchronous_File_IO_async/vb/example2.vb#2)]

The next example shows the code-behind file and the XAML file that are used to open a file as a <xref:System.IO.Stream> in a Windows 8.x Store app, and read its contents by using an instance of the <xref:System.IO.StreamReader> class. Ele usa os métodos assíncronos para abrir o arquivo como um fluxo e ler seu conteúdo.

[!code-csharp[System.IO.WindowsRuntimeStorageExtensions#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.windowsruntimestorageextensions/cs/blankpage.xaml.cs#2)]
[!code-vb[System.IO.WindowsRuntimeStorageExtensions#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.windowsruntimestorageextensions/vb/blankpage.xaml.vb#2)]

[!code-xaml[System.IO.WindowsRuntimeStorageExtensions#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.windowsruntimestorageextensions/cs/blankpage.xaml#1)]

## <a name="see-also"></a>Consulte também

- <xref:System.IO.Stream>
- [E/S de arquivo e de fluxo](index.md)
- [Programação assíncrona com async e await (C#)](../../csharp/programming-guide/concepts/async/index.md)
- [Programação assíncrona com Async e Await (Visual Basic)](../../visual-basic/programming-guide/concepts/async/index.md)
