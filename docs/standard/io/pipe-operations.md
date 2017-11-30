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
# <a name="pipe-operations-in-the-net-framework"></a><span data-ttu-id="617c7-102">Operações de pipe no .NET Framework</span><span class="sxs-lookup"><span data-stu-id="617c7-102">Pipe Operations in the .NET Framework</span></span>
<span data-ttu-id="617c7-103">Pipes fornecem um meio de comunicação entre processos.</span><span class="sxs-lookup"><span data-stu-id="617c7-103">Pipes provide a means for interprocess communication.</span></span> <span data-ttu-id="617c7-104">Há dois tipos de pipes:</span><span class="sxs-lookup"><span data-stu-id="617c7-104">There are two types of pipes:</span></span>  
  
-   <span data-ttu-id="617c7-105">Pipes anônimos.</span><span class="sxs-lookup"><span data-stu-id="617c7-105">Anonymous pipes.</span></span>  
  
     <span data-ttu-id="617c7-106">Pipes anônimos fornecem comunicação entre processos em um computador local.</span><span class="sxs-lookup"><span data-stu-id="617c7-106">Anonymous pipes provide interprocess communication on a local computer.</span></span> <span data-ttu-id="617c7-107">Pipes anônimos exigem menos sobrecarga do que pipes nomeados mas oferecem serviços limitados.</span><span class="sxs-lookup"><span data-stu-id="617c7-107">Anonymous pipes require less overhead than named pipes but offer limited services.</span></span> <span data-ttu-id="617c7-108">Pipes anônimos são unidirecionais e não podem ser usados em uma rede.</span><span class="sxs-lookup"><span data-stu-id="617c7-108">Anonymous pipes are one-way and cannot be used over a network.</span></span> <span data-ttu-id="617c7-109">Eles oferecem suporte a apenas uma única instância de servidor.</span><span class="sxs-lookup"><span data-stu-id="617c7-109">They support only a single server instance.</span></span> <span data-ttu-id="617c7-110">Pipes anônimos são úteis para a comunicação entre threads ou processos pai e filho onde os identificadores do pipe podem ser facilmente passados para o processo filho quando ele é criado.</span><span class="sxs-lookup"><span data-stu-id="617c7-110">Anonymous pipes are useful for communication between threads, or between parent and child processes where the pipe handles can be easily passed to the child process when it is created.</span></span>  
  
     <span data-ttu-id="617c7-111">No .NET Framework, você implementa pipes anônimos usando o <xref:System.IO.Pipes.AnonymousPipeServerStream> e <xref:System.IO.Pipes.AnonymousPipeClientStream> classes.</span><span class="sxs-lookup"><span data-stu-id="617c7-111">In the .NET Framework, you implement anonymous pipes by using the <xref:System.IO.Pipes.AnonymousPipeServerStream> and <xref:System.IO.Pipes.AnonymousPipeClientStream> classes.</span></span>  
  
     <span data-ttu-id="617c7-112">Consulte [como: usar Pipes anônimos para comunicação entre processos locais](../../../docs/standard/io/how-to-use-anonymous-pipes-for-local-interprocess-communication.md).</span><span class="sxs-lookup"><span data-stu-id="617c7-112">See [How to: Use Anonymous Pipes for Local Interprocess Communication](../../../docs/standard/io/how-to-use-anonymous-pipes-for-local-interprocess-communication.md).</span></span>  
  
-   <span data-ttu-id="617c7-113">Pipes nomeados.</span><span class="sxs-lookup"><span data-stu-id="617c7-113">Named pipes.</span></span>  
  
     <span data-ttu-id="617c7-114">Pipes nomeados fornecem comunicação entre processos entre um servidor de pipe e um ou mais clientes pipe.</span><span class="sxs-lookup"><span data-stu-id="617c7-114">Named pipes provide interprocess communication between a pipe server and one or more pipe clients.</span></span> <span data-ttu-id="617c7-115">Pipes nomeados podem ser unidirecionais ou bidirecionais.</span><span class="sxs-lookup"><span data-stu-id="617c7-115">Named pipes can be one-way or duplex.</span></span> <span data-ttu-id="617c7-116">Eles oferecem suporte à comunicação baseada em mensagens e permitir que vários clientes para se conectar simultaneamente ao servidor de processo usando o mesmo nome de pipe.</span><span class="sxs-lookup"><span data-stu-id="617c7-116">They support message-based communication and allow multiple clients to connect simultaneously to the server process using the same pipe name.</span></span> <span data-ttu-id="617c7-117">Pipes nomeados também oferecem suporte a representação, que permite que processos de conexão usar suas próprias permissões em servidores remotos.</span><span class="sxs-lookup"><span data-stu-id="617c7-117">Named pipes also support impersonation, which enables connecting processes to use their own permissions on remote servers.</span></span>  
  
     <span data-ttu-id="617c7-118">No .NET Framework, você implementa pipes nomeados usando o <xref:System.IO.Pipes.NamedPipeServerStream> e <xref:System.IO.Pipes.NamedPipeClientStream> classes.</span><span class="sxs-lookup"><span data-stu-id="617c7-118">In the .NET Framework, you implement named pipes by using the <xref:System.IO.Pipes.NamedPipeServerStream> and <xref:System.IO.Pipes.NamedPipeClientStream> classes.</span></span>  
  
     <span data-ttu-id="617c7-119">Consulte [como: usar Pipes nomeados para comunicação entre processos de rede](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md).</span><span class="sxs-lookup"><span data-stu-id="617c7-119">See [How to: Use Named Pipes for Network Interprocess Communication](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="617c7-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="617c7-120">See Also</span></span>  
 [<span data-ttu-id="617c7-121">E/S de arquivo e de fluxo</span><span class="sxs-lookup"><span data-stu-id="617c7-121">File and Stream I-O</span></span>](../../../docs/standard/io/index.md)  
 [<span data-ttu-id="617c7-122">Como usar pipes anônimos para comunicação entre processos locais</span><span class="sxs-lookup"><span data-stu-id="617c7-122">How to: Use Anonymous Pipes for Local Interprocess Communication</span></span>](../../../docs/standard/io/how-to-use-anonymous-pipes-for-local-interprocess-communication.md)  
 [<span data-ttu-id="617c7-123">Como usar pipes nomeados para comunicação entre processos na rede</span><span class="sxs-lookup"><span data-stu-id="617c7-123">How to: Use Named Pipes for Network Interprocess Communication</span></span>](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md)
