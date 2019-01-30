---
title: 'Como: Usar pipes nomeados para comunicação entre processos na rede'
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
ms.openlocfilehash: 608991878b49bf0bafe9ebf90dbfc8eaec69e0e7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54698863"
---
# <a name="how-to-use-named-pipes-for-network-interprocess-communication"></a><span data-ttu-id="db9d7-102">Como: Usar pipes nomeados para comunicação entre processos na rede</span><span class="sxs-lookup"><span data-stu-id="db9d7-102">How to: Use Named Pipes for Network Interprocess Communication</span></span>
<span data-ttu-id="db9d7-103">Os pipes nomeados fornecem a comunicação entre processos entre um servidor de pipe e um ou mais clientes pipe.</span><span class="sxs-lookup"><span data-stu-id="db9d7-103">Named pipes provide interprocess communication between a pipe server and one or more pipe clients.</span></span> <span data-ttu-id="db9d7-104">Eles oferecem mais funcionalidades do que pipes anônimos, que fornecem comunicação entre processos em um computador local.</span><span class="sxs-lookup"><span data-stu-id="db9d7-104">They offer more functionality than anonymous pipes, which provide interprocess communication on a local computer.</span></span> <span data-ttu-id="db9d7-105">Pipes nomeados oferecem suporte à comunicação full-duplex em uma rede e em várias instâncias do servidor, comunicação por mensagens e representação do cliente, o que permite que processos de conexão usem seus próprios conjuntos de permissões em servidores remotos.</span><span class="sxs-lookup"><span data-stu-id="db9d7-105">Named pipes support full duplex communication over a network and multiple server instances, message-based communication, and client impersonation, which enables connecting processes to use their own set of permissions on remote servers.</span></span>  
  
 <span data-ttu-id="db9d7-106">Para implementar os pipes nomeados, use as classes <xref:System.IO.Pipes.NamedPipeServerStream> e <xref:System.IO.Pipes.NamedPipeClientStream>.</span><span class="sxs-lookup"><span data-stu-id="db9d7-106">To implement name pipes, use the <xref:System.IO.Pipes.NamedPipeServerStream> and <xref:System.IO.Pipes.NamedPipeClientStream> classes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="db9d7-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="db9d7-107">Example</span></span>  
 <span data-ttu-id="db9d7-108">O exemplo a seguir demonstra como criar um pipe nomeado usando a classe <xref:System.IO.Pipes.NamedPipeServerStream>.</span><span class="sxs-lookup"><span data-stu-id="db9d7-108">The following example demonstrates how to create a named pipe by using the <xref:System.IO.Pipes.NamedPipeServerStream> class.</span></span> <span data-ttu-id="db9d7-109">Neste exemplo, o processo do servidor cria quatro threads.</span><span class="sxs-lookup"><span data-stu-id="db9d7-109">In this example, the server process creates four threads.</span></span> <span data-ttu-id="db9d7-110">Cada thread pode aceitar uma conexão de cliente.</span><span class="sxs-lookup"><span data-stu-id="db9d7-110">Each thread can accept a client connection.</span></span> <span data-ttu-id="db9d7-111">O processo do cliente conectado, em seguida, fornece um nome de arquivo ao servidor.</span><span class="sxs-lookup"><span data-stu-id="db9d7-111">The connected client process then supplies the server with a file name.</span></span> <span data-ttu-id="db9d7-112">Se o cliente tiver permissões suficientes, o processo do servidor abrirá o arquivo e enviará seu conteúdo de volta ao cliente.</span><span class="sxs-lookup"><span data-stu-id="db9d7-112">If the client has sufficient permissions, the server process opens the file and sends its contents back to the client.</span></span>  
  
 [!code-cpp[System.IO.Pipes.NamedPipeServerStream_ImpersonationSample1#01](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.Pipes.NamedPipeServerStream_ImpersonationSample1/cpp/program.cpp#01)]
 [!code-csharp[System.IO.Pipes.NamedPipeServerStream_ImpersonationSample1#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.NamedPipeServerStream_ImpersonationSample1/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.NamedPipeServerStream_ImpersonationSample1#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.NamedPipeServerStream_ImpersonationSample1/vb/program.vb#01)]  
  
## <a name="example"></a><span data-ttu-id="db9d7-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="db9d7-113">Example</span></span>  
 <span data-ttu-id="db9d7-114">O exemplo a seguir mostra o processo do cliente, que usa a classe <xref:System.IO.Pipes.NamedPipeClientStream>.</span><span class="sxs-lookup"><span data-stu-id="db9d7-114">The following example shows the client process, which uses the <xref:System.IO.Pipes.NamedPipeClientStream> class.</span></span> <span data-ttu-id="db9d7-115">O cliente se conecta ao processo do servidor e envia um nome de arquivo para o servidor.</span><span class="sxs-lookup"><span data-stu-id="db9d7-115">The client connects to the server process and sends a file name to the server.</span></span> <span data-ttu-id="db9d7-116">O exemplo usa representação, de forma que a identidade que está executando o aplicativo do cliente deve ter permissão para acessar o arquivo.</span><span class="sxs-lookup"><span data-stu-id="db9d7-116">The example uses impersonation, so the identity that is running the client application must have permission to access the file.</span></span> <span data-ttu-id="db9d7-117">O servidor, então, envia o conteúdo do arquivo de volta ao cliente.</span><span class="sxs-lookup"><span data-stu-id="db9d7-117">The server then sends the contents of the file back to the client.</span></span> <span data-ttu-id="db9d7-118">O conteúdo do arquivo é exibido no console.</span><span class="sxs-lookup"><span data-stu-id="db9d7-118">The file contents are then displayed to the console.</span></span>  
  
 [!code-csharp[System.IO.Pipes.NamedPipeClientStream_ImpersonationSample1#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.NamedPipeClientStream_ImpersonationSample1/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.NamedPipeClientStream_ImpersonationSample1#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.NamedPipeClientStream_ImpersonationSample1/vb/program.vb#01)]  
  
## <a name="robust-programming"></a><span data-ttu-id="db9d7-119">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="db9d7-119">Robust Programming</span></span>  
 <span data-ttu-id="db9d7-120">Os processos de cliente e servidor neste exemplo devem ser executados no mesmo computador, para que o nome do servidor fornecido para o objeto <xref:System.IO.Pipes.NamedPipeClientStream> seja `"."`.</span><span class="sxs-lookup"><span data-stu-id="db9d7-120">The client and server processes in this example are intended to run on the same computer, so the server name provided to the <xref:System.IO.Pipes.NamedPipeClientStream> object is `"."`.</span></span> <span data-ttu-id="db9d7-121">Se os processos do cliente e do servidor fossem realizados em computadores separados, `"."` seria substituído pelo nome de rede do computador que executa o processo do servidor.</span><span class="sxs-lookup"><span data-stu-id="db9d7-121">If the client and server processes were on separate computers, `"."` would be replaced with the network name of the computer that runs the server process.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db9d7-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="db9d7-122">See also</span></span>

- <xref:System.Security.Principal.TokenImpersonationLevel>
- <xref:System.IO.Pipes.NamedPipeServerStream.GetImpersonationUserName%2A>
- [<span data-ttu-id="db9d7-123">Pipes</span><span class="sxs-lookup"><span data-stu-id="db9d7-123">Pipes</span></span>](../../../docs/standard/io/pipe-operations.md)
- [<span data-ttu-id="db9d7-124">Como: Usar pipes anônimos para comunicação entre processos locais</span><span class="sxs-lookup"><span data-stu-id="db9d7-124">How to: Use Anonymous Pipes for Local Interprocess Communication</span></span>](../../../docs/standard/io/how-to-use-anonymous-pipes-for-local-interprocess-communication.md)
