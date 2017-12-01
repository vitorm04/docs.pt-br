---
title: "Operações de pipe no .NET Framework"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pipes [.NET Framework]
- pipe operations [.NET Framework]
- interprocess communication [.NET Framework], pipes
- I/O [.NET Framework], pipes
ms.assetid: 7b964ebd-7a4f-4d28-8194-7841f9e4c702
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 879e5a73417f9347224bc22b397814b83972751c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="pipe-operations-in-the-net-framework"></a>Operações de pipe no .NET Framework
Pipes fornecem um meio de comunicação entre processos. Há dois tipos de pipes:  
  
-   Pipes anônimos.  
  
     Pipes anônimos fornecem comunicação entre processos em um computador local. Pipes anônimos exigem menos sobrecarga do que pipes nomeados mas oferecem serviços limitados. Pipes anônimos são unidirecionais e não podem ser usados em uma rede. Eles oferecem suporte a apenas uma única instância de servidor. Pipes anônimos são úteis para a comunicação entre threads ou processos pai e filho onde os identificadores do pipe podem ser facilmente passados para o processo filho quando ele é criado.  
  
     No .NET Framework, você implementa pipes anônimos usando o <xref:System.IO.Pipes.AnonymousPipeServerStream> e <xref:System.IO.Pipes.AnonymousPipeClientStream> classes.  
  
     Consulte [como: usar Pipes anônimos para comunicação entre processos locais](../../../docs/standard/io/how-to-use-anonymous-pipes-for-local-interprocess-communication.md).  
  
-   Pipes nomeados.  
  
     Pipes nomeados fornecem comunicação entre processos entre um servidor de pipe e um ou mais clientes pipe. Pipes nomeados podem ser unidirecionais ou bidirecionais. Eles oferecem suporte à comunicação baseada em mensagens e permitir que vários clientes para se conectar simultaneamente ao servidor de processo usando o mesmo nome de pipe. Pipes nomeados também oferecem suporte a representação, que permite que processos de conexão usar suas próprias permissões em servidores remotos.  
  
     No .NET Framework, você implementa pipes nomeados usando o <xref:System.IO.Pipes.NamedPipeServerStream> e <xref:System.IO.Pipes.NamedPipeClientStream> classes.  
  
     Consulte [como: usar Pipes nomeados para comunicação entre processos de rede](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md).  
  
## <a name="see-also"></a>Consulte também  
 [E/S de arquivo e de fluxo](../../../docs/standard/io/index.md)  
 [Como usar pipes anônimos para comunicação entre processos locais](../../../docs/standard/io/how-to-use-anonymous-pipes-for-local-interprocess-communication.md)  
 [Como usar pipes nomeados para comunicação entre processos na rede](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md)
