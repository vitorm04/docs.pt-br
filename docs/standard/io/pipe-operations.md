---
title: Operações de pipe no .NET Framework
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- pipes [.NET Framework]
- pipe operations [.NET Framework]
- interprocess communication [.NET Framework], pipes
- I/O [.NET Framework], pipes
ms.assetid: 7b964ebd-7a4f-4d28-8194-7841f9e4c702
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1e0d2747abbacf766ddeda6f41404d8701cbc273
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33574360"
---
# <a name="pipe-operations-in-the-net-framework"></a><span data-ttu-id="38a13-102">Operações de pipe no .NET Framework</span><span class="sxs-lookup"><span data-stu-id="38a13-102">Pipe Operations in the .NET Framework</span></span>
<span data-ttu-id="38a13-103">Os pipes fornecem um meio de comunicação entre processos.</span><span class="sxs-lookup"><span data-stu-id="38a13-103">Pipes provide a means for interprocess communication.</span></span> <span data-ttu-id="38a13-104">Existem dois tipos de pipes:</span><span class="sxs-lookup"><span data-stu-id="38a13-104">There are two types of pipes:</span></span>  
  
-   <span data-ttu-id="38a13-105">Pipes anônimos.</span><span class="sxs-lookup"><span data-stu-id="38a13-105">Anonymous pipes.</span></span>  
  
     <span data-ttu-id="38a13-106">Os pipes anônimos fornecem comunicação entre processos em um computador local.</span><span class="sxs-lookup"><span data-stu-id="38a13-106">Anonymous pipes provide interprocess communication on a local computer.</span></span> <span data-ttu-id="38a13-107">Os pipes anônimos exigem menos sobrecarga do que os pipes nomeados mas oferecem serviços limitados.</span><span class="sxs-lookup"><span data-stu-id="38a13-107">Anonymous pipes require less overhead than named pipes but offer limited services.</span></span> <span data-ttu-id="38a13-108">Os pipes anônimos são unidirecionais e não podem ser usados em uma rede.</span><span class="sxs-lookup"><span data-stu-id="38a13-108">Anonymous pipes are one-way and cannot be used over a network.</span></span> <span data-ttu-id="38a13-109">Eles oferecem suporte a apenas uma única instância de servidor.</span><span class="sxs-lookup"><span data-stu-id="38a13-109">They support only a single server instance.</span></span> <span data-ttu-id="38a13-110">Os pipes anônimos são úteis para a comunicação entre threads ou entre processos pai e filho em que os identificadores de pipe podem ser facilmente passados para o processo filho quando ele é criado.</span><span class="sxs-lookup"><span data-stu-id="38a13-110">Anonymous pipes are useful for communication between threads, or between parent and child processes where the pipe handles can be easily passed to the child process when it is created.</span></span>  
  
     <span data-ttu-id="38a13-111">No .NET Framework, você implementa pipes anônimos usando as classes <xref:System.IO.Pipes.AnonymousPipeServerStream> e <xref:System.IO.Pipes.AnonymousPipeClientStream>.</span><span class="sxs-lookup"><span data-stu-id="38a13-111">In the .NET Framework, you implement anonymous pipes by using the <xref:System.IO.Pipes.AnonymousPipeServerStream> and <xref:System.IO.Pipes.AnonymousPipeClientStream> classes.</span></span>  
  
     <span data-ttu-id="38a13-112">Veja [Como usar pipes anônimos para a comunicação entre processos locais](../../../docs/standard/io/how-to-use-anonymous-pipes-for-local-interprocess-communication.md).</span><span class="sxs-lookup"><span data-stu-id="38a13-112">See [How to: Use Anonymous Pipes for Local Interprocess Communication](../../../docs/standard/io/how-to-use-anonymous-pipes-for-local-interprocess-communication.md).</span></span>  
  
-   <span data-ttu-id="38a13-113">Pipes nomeados.</span><span class="sxs-lookup"><span data-stu-id="38a13-113">Named pipes.</span></span>  
  
     <span data-ttu-id="38a13-114">Os pipes nomeados fornecem a comunicação entre processos entre um servidor de pipe e um ou mais clientes pipe.</span><span class="sxs-lookup"><span data-stu-id="38a13-114">Named pipes provide interprocess communication between a pipe server and one or more pipe clients.</span></span> <span data-ttu-id="38a13-115">Os pipes nomeados podem ser unidirecionais ou bidirecionais.</span><span class="sxs-lookup"><span data-stu-id="38a13-115">Named pipes can be one-way or duplex.</span></span> <span data-ttu-id="38a13-116">Eles oferecem suporte à comunicação baseada em mensagens e permitem que vários clientes se conectem simultaneamente ao processo do servidor usando o mesmo nome de pipe.</span><span class="sxs-lookup"><span data-stu-id="38a13-116">They support message-based communication and allow multiple clients to connect simultaneously to the server process using the same pipe name.</span></span> <span data-ttu-id="38a13-117">Os pipes nomeados também oferecem suporte à representação, que permite aos processos de conexão usar suas próprias permissões em servidores remotos.</span><span class="sxs-lookup"><span data-stu-id="38a13-117">Named pipes also support impersonation, which enables connecting processes to use their own permissions on remote servers.</span></span>  
  
     <span data-ttu-id="38a13-118">No .NET Framework, você implementa pipes nomeados usando as classes <xref:System.IO.Pipes.NamedPipeServerStream> e <xref:System.IO.Pipes.NamedPipeClientStream>.</span><span class="sxs-lookup"><span data-stu-id="38a13-118">In the .NET Framework, you implement named pipes by using the <xref:System.IO.Pipes.NamedPipeServerStream> and <xref:System.IO.Pipes.NamedPipeClientStream> classes.</span></span>  
  
     <span data-ttu-id="38a13-119">Veja [Como usar pipes nomeados para comunicação entre processos na rede](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md).</span><span class="sxs-lookup"><span data-stu-id="38a13-119">See [How to: Use Named Pipes for Network Interprocess Communication](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38a13-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="38a13-120">See Also</span></span>  
 [<span data-ttu-id="38a13-121">E/S de arquivo e de fluxo</span><span class="sxs-lookup"><span data-stu-id="38a13-121">File and Stream I/O</span></span>](../../../docs/standard/io/index.md)  
 [<span data-ttu-id="38a13-122">Como usar pipes anônimos para comunicação entre processos locais</span><span class="sxs-lookup"><span data-stu-id="38a13-122">How to: Use Anonymous Pipes for Local Interprocess Communication</span></span>](../../../docs/standard/io/how-to-use-anonymous-pipes-for-local-interprocess-communication.md)  
 [<span data-ttu-id="38a13-123">Como usar pipes nomeados para comunicação entre processos na rede</span><span class="sxs-lookup"><span data-stu-id="38a13-123">How to: Use Named Pipes for Network Interprocess Communication</span></span>](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md)
