---
title: "Como usar pipes nomeados para comunicação entre processos em uma rede"
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
caps.latest.revision: "16"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 952600e71311184c4a4f906734addbf335d0358a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-named-pipes-for-network-interprocess-communication"></a>Como usar pipes nomeados para comunicação entre processos em uma rede
Pipes nomeados fornecem comunicação entre processos entre um servidor de pipe e um ou mais clientes pipe. Eles oferecem mais funcionalidades do que pipes anônimos, que fornecem comunicação entre processos em um computador local. Pipes nomeados oferecem suporte à comunicação full-duplex em uma rede e várias instâncias do servidor, a comunicação baseada em mensagens e representação do cliente, que permite que processos de conexão usar seu próprio conjunto de permissões em servidores remotos.  
  
 Para implementar os pipes nomeados, use o <xref:System.IO.Pipes.NamedPipeServerStream> e <xref:System.IO.Pipes.NamedPipeClientStream> classes.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra como criar um pipe nomeado usando o <xref:System.IO.Pipes.NamedPipeServerStream> classe. Neste exemplo, o processo de servidor cria quatro threads. Cada thread pode aceitar uma conexão de cliente. O processo de cliente conectado, em seguida, fornece o servidor com um nome de arquivo. Se o cliente tiver permissões suficientes, o processo do servidor abre o arquivo e envia o conteúdo de volta ao cliente.  
  
 [!code-cpp[System.IO.Pipes.NamedPipeServerStream_ImpersonationSample1#01](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.Pipes.NamedPipeServerStream_ImpersonationSample1/cpp/program.cpp#01)]
 [!code-csharp[System.IO.Pipes.NamedPipeServerStream_ImpersonationSample1#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.NamedPipeServerStream_ImpersonationSample1/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.NamedPipeServerStream_ImpersonationSample1#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.NamedPipeServerStream_ImpersonationSample1/vb/program.vb#01)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra o processo de cliente, que usa o <xref:System.IO.Pipes.NamedPipeClientStream> classe. O cliente se conecta ao processo de servidor e envia um nome de arquivo para o servidor. O exemplo usa a representação, para que a identidade que está executando o aplicativo cliente deve ter permissão para acessar o arquivo. O servidor, em seguida, envia o conteúdo do arquivo de volta ao cliente. O conteúdo do arquivo é exibido no console.  
  
 [!code-csharp[System.IO.Pipes.NamedPipeClientStream_ImpersonationSample1#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.NamedPipeClientStream_ImpersonationSample1/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.NamedPipeClientStream_ImpersonationSample1#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.NamedPipeClientStream_ImpersonationSample1/vb/program.vb#01)]  
  
## <a name="robust-programming"></a>Programação robusta  
 Os processos de cliente e servidor neste exemplo devem ser executados no mesmo computador, para que o nome do servidor fornecido para o <xref:System.IO.Pipes.NamedPipeClientStream> objeto é `"."`. Se os processos de cliente e servidor fossem em computadores separados, `"."` deve ser substituído com o nome de rede do computador que executa o processo do servidor.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Security.Principal.TokenImpersonationLevel>  
 <xref:System.IO.Pipes.NamedPipeServerStream.GetImpersonationUserName%2A>  
 [Pipes](../../../docs/standard/io/pipe-operations.md)  
 [Como usar pipes anônimos para comunicação entre processos locais](../../../docs/standard/io/how-to-use-anonymous-pipes-for-local-interprocess-communication.md)
