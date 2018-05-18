---
title: Como usar pipes nomeados para comunicação entre processos em uma rede
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- message-based communication [.NET Framework], named pipes
- named pipes [.NET Framework]
- pipes [.NET Framework]
- multiple connections via named pipes
- network communications [.NET Framework], named pipes
- impersonation [.NET Framework], named pipes
- full duplex communcation [.NET Framework], named pipes
ms.assetid: 4e4d7e64-9f1b-4026-98f7-20488ac7b42b
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cb8da9ff6df910e1932c593c1f1b882dca12146a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-named-pipes-for-network-interprocess-communication"></a>Como usar pipes nomeados para comunicação entre processos em uma rede
Os pipes nomeados fornecem a comunicação entre processos entre um servidor de pipe e um ou mais clientes pipe. Eles oferecem mais funcionalidades do que pipes anônimos, que fornecem comunicação entre processos em um computador local. Pipes nomeados oferecem suporte à comunicação full-duplex em uma rede e em várias instâncias do servidor, comunicação por mensagens e representação do cliente, o que permite que processos de conexão usem seus próprios conjuntos de permissões em servidores remotos.  
  
 Para implementar os pipes nomeados, use as classes <xref:System.IO.Pipes.NamedPipeServerStream> e <xref:System.IO.Pipes.NamedPipeClientStream>.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra como criar um pipe nomeado usando a classe <xref:System.IO.Pipes.NamedPipeServerStream>. Neste exemplo, o processo do servidor cria quatro threads. Cada thread pode aceitar uma conexão de cliente. O processo do cliente conectado, em seguida, fornece um nome de arquivo ao servidor. Se o cliente tiver permissões suficientes, o processo do servidor abrirá o arquivo e enviará seu conteúdo de volta ao cliente.  
  
 [!code-cpp[System.IO.Pipes.NamedPipeServerStream_ImpersonationSample1#01](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.Pipes.NamedPipeServerStream_ImpersonationSample1/cpp/program.cpp#01)]
 [!code-csharp[System.IO.Pipes.NamedPipeServerStream_ImpersonationSample1#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.NamedPipeServerStream_ImpersonationSample1/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.NamedPipeServerStream_ImpersonationSample1#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.NamedPipeServerStream_ImpersonationSample1/vb/program.vb#01)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra o processo do cliente, que usa a classe <xref:System.IO.Pipes.NamedPipeClientStream>. O cliente se conecta ao processo do servidor e envia um nome de arquivo para o servidor. O exemplo usa representação, de forma que a identidade que está executando o aplicativo do cliente deve ter permissão para acessar o arquivo. O servidor, então, envia o conteúdo do arquivo de volta ao cliente. O conteúdo do arquivo é exibido no console.  
  
 [!code-csharp[System.IO.Pipes.NamedPipeClientStream_ImpersonationSample1#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.NamedPipeClientStream_ImpersonationSample1/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.NamedPipeClientStream_ImpersonationSample1#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.NamedPipeClientStream_ImpersonationSample1/vb/program.vb#01)]  
  
## <a name="robust-programming"></a>Programação robusta  
 Os processos de cliente e servidor neste exemplo devem ser executados no mesmo computador, para que o nome do servidor fornecido para o objeto <xref:System.IO.Pipes.NamedPipeClientStream> seja `"."`. Se os processos do cliente e do servidor fossem realizados em computadores separados, `"."` seria substituído pelo nome de rede do computador que executa o processo do servidor.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Security.Principal.TokenImpersonationLevel>  
 <xref:System.IO.Pipes.NamedPipeServerStream.GetImpersonationUserName%2A>  
 [Pipes](../../../docs/standard/io/pipe-operations.md)  
 [Como usar pipes anônimos para comunicação entre processos locais](../../../docs/standard/io/how-to-use-anonymous-pipes-for-local-interprocess-communication.md)
