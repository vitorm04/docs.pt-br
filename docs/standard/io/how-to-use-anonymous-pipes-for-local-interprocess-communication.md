---
title: "Como usar pipes anônimos para comunicação entre processos locais"
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
- anonymous pipes [.NET Framework]
- parent-child communication [.NET Framework]
- pipes [.NET Framework]
- one-way communication [.NET Framework]
- local computer communication [.NET Framework], pipes
ms.assetid: e7773c77-c646-4a01-8a96-a003d59fc4c9
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: f457cc91e6fbfc118e5363d1b0a8e8c2ad800748
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-anonymous-pipes-for-local-interprocess-communication"></a>Como usar pipes anônimos para comunicação entre processos locais
Pipes anônimos fornecem comunicação entre processos em um computador local. Eles oferecem menos funcionalidade que pipes nomeados, mas também exigem menos sobrecarga. Você pode usar pipes anônimos para facilitar a comunicação entre processos em um computador local. Você não pode usar pipes anônimos para comunicação através de uma rede.  
  
 Para implementar pipes anônimos, use o <xref:System.IO.Pipes.AnonymousPipeServerStream> e <xref:System.IO.Pipes.AnonymousPipeClientStream> classes.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra uma maneira de enviar uma cadeia de caracteres de um processo pai para um processo filho usando pipes anônimos. Este exemplo cria um <xref:System.IO.Pipes.AnonymousPipeServerStream> objeto em um processo pai com um <xref:System.IO.Pipes.PipeDirection> valor <xref:System.IO.Pipes.PipeDirection.Out>. O processo pai, em seguida, cria um processo filho usando um identificador de cliente para criar um <xref:System.IO.Pipes.AnonymousPipeClientStream> objeto. O processo filho tem um <xref:System.IO.Pipes.PipeDirection> valor <xref:System.IO.Pipes.PipeDirection.In>.  
  
 O processo pai, em seguida, envia uma cadeia de caracteres fornecida pelo usuário para o processo filho. A cadeia de caracteres é exibida no console do processo filho.  
  
 O exemplo a seguir mostra o processo do servidor.  
  
 [!code-cpp[System.IO.Pipes.AnonymousPipeServerStream_Sample#01](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeServerStream_Sample/cpp/program.cpp#01)]
 [!code-csharp[System.IO.Pipes.AnonymousPipeServerStream_Sample#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeServerStream_Sample/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.AnonymousPipeServerStream_Sample#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeServerStream_Sample/vb/program.vb#01)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra o processo de cliente. O processo do servidor inicia o processo de cliente e oferece a esse processo um identificador de cliente. O executável resultante do código do cliente deve ser nomeado `pipeClient.exe` e ser copiado para o mesmo diretório que o servidor executável antes de executar o processo do servidor.  
  
 [!code-cpp[System.IO.Pipes.AnonymousPipeClientStream_Sample#01](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeClientStream_Sample/cpp/program.cpp#01)]
 [!code-csharp[System.IO.Pipes.AnonymousPipeClientStream_Sample#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeClientStream_Sample/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.AnonymousPipeClientStream_Sample#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeClientStream_Sample/vb/program.vb#01)]  
  
## <a name="see-also"></a>Consulte também  
 [Pipes](../../../docs/standard/io/pipe-operations.md)  
 [Como usar pipes nomeados para comunicação entre processos na rede](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md)
