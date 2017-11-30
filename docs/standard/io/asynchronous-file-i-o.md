---
title: "Arquivo assíncrono e-S"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "23"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: d8a461d79ecdcadc3f880f6a813918cf891abd45
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="asynchronous-file-io"></a>E/S de arquivo assíncrona
Operações assíncronas permitem executar operações de e/s de uso intensivo de recursos sem bloquear o thread principal. A consideração de desempenho é particularmente importante em uma [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplicativo ou [!INCLUDE[desktop_appname](../../../includes/desktop-appname-md.md)] aplicativo em que uma operação demorada fluxo pode bloquear o thread de interface do usuário e tornar seu aplicativo aparecem como se ele não está funcionando.  
  
 Começando com o [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], os tipos de e/s incluem os métodos assíncronos para simplificar as operações assíncronas. Contém um método assíncrono `Async` em seu nome, como <xref:System.IO.Stream.ReadAsync%2A>, <xref:System.IO.Stream.WriteAsync%2A>, <xref:System.IO.Stream.CopyToAsync%2A>, <xref:System.IO.Stream.FlushAsync%2A>, <xref:System.IO.TextReader.ReadLineAsync%2A>, e <xref:System.IO.TextReader.ReadToEndAsync%2A>. Esses métodos assíncronos são implementados em classes de fluxo, como <xref:System.IO.Stream>, <xref:System.IO.FileStream>, e <xref:System.IO.MemoryStream>e nas classes que são usadas para leitura ou gravação em fluxos, tais <xref:System.IO.TextReader> e <xref:System.IO.TextWriter>.  
  
 O .NET Framework 4 e versões anteriores, você precisa usar métodos como <xref:System.IO.Stream.BeginRead%2A> e <xref:System.IO.Stream.EndRead%2A> para implementar operações de e/s assíncronas. Esses métodos ainda estão disponíveis no [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] para dar suporte a código herdado; no entanto, os métodos assíncronos ajudarão-lo a implementar operações de e/s assíncronas mais facilmente.  
  
 Começando com [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], o Visual Studio fornece duas palavras-chave para a programação assíncrona:  
  
 `Async`(Visual Basic) ou `async` modificador (c#), que é usado para marcar um método que contém uma operação assíncrona.  
  
 `Await`(Visual Basic) ou `await` (c#) operador, que é aplicada ao resultado de um método assíncrono.  
  
 Para implementar operações de e/s assíncronas, use essas palavras-chave em conjunto com os métodos assíncronos, conforme mostrado nos exemplos a seguir. Para obter mais informações, consulte [programação assíncrona com Async e Await](http://msdn.microsoft.com/library/db854f91-ccef-4035-ae4d-0911fde808c7).  
  
 O exemplo a seguir demonstra como usar duas <xref:System.IO.FileStream> objetos para copiar arquivos de forma assíncrona de um diretório para outro. Observe que o <xref:System.Web.UI.WebControls.Button.Click> manipulador de eventos para o <xref:System.Windows.Controls.Button> controle está marcado com o `async` modificador porque chama um método assíncrono.  
  
 [!code-csharp[Asynchronous_File_IO_async#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Asynchronous_File_IO_async/cs/example.cs#1)]
 [!code-vb[Asynchronous_File_IO_async#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Asynchronous_File_IO_async/vb/example.vb#1)]  
  
 O exemplo a seguir é semelhante à anterior, mas usa <xref:System.IO.StreamReader> e <xref:System.IO.StreamWriter> objetos para ler e gravar o conteúdo de um arquivo de texto de forma assíncrona.  
  
 [!code-csharp[Asynchronous_File_IO_async#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Asynchronous_File_IO_async/cs/example2.cs#2)]
 [!code-vb[Asynchronous_File_IO_async#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Asynchronous_File_IO_async/vb/example2.vb#2)]  
  
 O exemplo a seguir mostra o arquivo code-behind e o arquivo XAML que são usados para abrir um arquivo como um <xref:System.IO.Stream> em uma [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplicativo, e ler seu conteúdo usando uma instância do <xref:System.IO.StreamReader> classe. Ele usa os métodos assíncronos para abrir o arquivo como um fluxo e ler seu conteúdo.  
  
 [!code-csharp[System.IO.WindowsRuntimeStorageExtensions#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.windowsruntimestorageextensions/cs/blankpage.xaml.cs#2)]
 [!code-vb[System.IO.WindowsRuntimeStorageExtensions#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.windowsruntimestorageextensions/vb/blankpage.xaml.vb#2)]  
  
 [!code-xaml[System.IO.WindowsRuntimeStorageExtensions#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.windowsruntimestorageextensions/cs/blankpage.xaml#1)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.IO.Stream>  
 [E/S de arquivo e de fluxo](../../../docs/standard/io/index.md)  
 [Programação assíncrona com Async e Await](http://msdn.microsoft.com/library/db854f91-ccef-4035-ae4d-0911fde808c7)
