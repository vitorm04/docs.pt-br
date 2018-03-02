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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 0679e09a52fab68d8da83863afde1568794ba561
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-use-anonymous-pipes-for-local-interprocess-communication"></a><span data-ttu-id="44ad7-102">Como usar pipes anônimos para comunicação entre processos locais</span><span class="sxs-lookup"><span data-stu-id="44ad7-102">How to: Use Anonymous Pipes for Local Interprocess Communication</span></span>
<span data-ttu-id="44ad7-103">Os pipes anônimos fornecem comunicação entre processos em um computador local.</span><span class="sxs-lookup"><span data-stu-id="44ad7-103">Anonymous pipes provide interprocess communication on a local computer.</span></span> <span data-ttu-id="44ad7-104">Eles oferecem menos funcionalidades que pipes nomeados, mas também exigem menos sobrecarga.</span><span class="sxs-lookup"><span data-stu-id="44ad7-104">They offer less functionality than named pipes, but also require less overhead.</span></span> <span data-ttu-id="44ad7-105">Você pode usar pipes anônimos para facilitar a comunicação entre processos em um computador local.</span><span class="sxs-lookup"><span data-stu-id="44ad7-105">You can use anonymous pipes to make interprocess communication on a local computer easier.</span></span> <span data-ttu-id="44ad7-106">Você não pode usar pipes anônimos para comunicações através de uma rede.</span><span class="sxs-lookup"><span data-stu-id="44ad7-106">You cannot use anonymous pipes for communication over a network.</span></span>  
  
 <span data-ttu-id="44ad7-107">Para implementar pipes anônimos, use as classes <xref:System.IO.Pipes.AnonymousPipeServerStream> e <xref:System.IO.Pipes.AnonymousPipeClientStream>.</span><span class="sxs-lookup"><span data-stu-id="44ad7-107">To implement anonymous pipes, use the <xref:System.IO.Pipes.AnonymousPipeServerStream> and <xref:System.IO.Pipes.AnonymousPipeClientStream> classes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="44ad7-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="44ad7-108">Example</span></span>  
 <span data-ttu-id="44ad7-109">O exemplo a seguir demonstra uma maneira de enviar uma cadeia de caracteres de um processo pai para um processo filho usando pipes anônimos.</span><span class="sxs-lookup"><span data-stu-id="44ad7-109">The following example demonstrates a way to send a string from a parent process to a child process using anonymous pipes.</span></span> <span data-ttu-id="44ad7-110">Este exemplo cria um objeto <xref:System.IO.Pipes.AnonymousPipeServerStream> em um processo pai com um valor <xref:System.IO.Pipes.PipeDirection> de <xref:System.IO.Pipes.PipeDirection.Out>.</span><span class="sxs-lookup"><span data-stu-id="44ad7-110">This example creates an <xref:System.IO.Pipes.AnonymousPipeServerStream> object in a parent process with a <xref:System.IO.Pipes.PipeDirection> value of <xref:System.IO.Pipes.PipeDirection.Out>.</span></span> <span data-ttu-id="44ad7-111">Em seguida, o processo pai cria um processo filho usando um identificador de cliente para criar um objeto <xref:System.IO.Pipes.AnonymousPipeClientStream>.</span><span class="sxs-lookup"><span data-stu-id="44ad7-111">The parent process then creates a child process by using a client handle to create an <xref:System.IO.Pipes.AnonymousPipeClientStream> object.</span></span> <span data-ttu-id="44ad7-112">O processo filho tem um valor <xref:System.IO.Pipes.PipeDirection> de <xref:System.IO.Pipes.PipeDirection.In>.</span><span class="sxs-lookup"><span data-stu-id="44ad7-112">The child process has a <xref:System.IO.Pipes.PipeDirection> value of <xref:System.IO.Pipes.PipeDirection.In>.</span></span>  
  
 <span data-ttu-id="44ad7-113">Em seguida, o processo pai envia uma cadeia de caracteres fornecida pelo usuário ao processo filho.</span><span class="sxs-lookup"><span data-stu-id="44ad7-113">The parent process then sends a user-supplied string to the child process.</span></span> <span data-ttu-id="44ad7-114">A cadeia de caracteres é exibida no console do processo filho.</span><span class="sxs-lookup"><span data-stu-id="44ad7-114">The string is displayed to the console in the child process.</span></span>  
  
 <span data-ttu-id="44ad7-115">O exemplo a seguir mostra o processo do servidor.</span><span class="sxs-lookup"><span data-stu-id="44ad7-115">The following example shows the server process.</span></span>  
  
 [!code-cpp[System.IO.Pipes.AnonymousPipeServerStream_Sample#01](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeServerStream_Sample/cpp/program.cpp#01)]
 [!code-csharp[System.IO.Pipes.AnonymousPipeServerStream_Sample#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeServerStream_Sample/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.AnonymousPipeServerStream_Sample#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeServerStream_Sample/vb/program.vb#01)]  
  
## <a name="example"></a><span data-ttu-id="44ad7-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="44ad7-116">Example</span></span>  
 <span data-ttu-id="44ad7-117">O exemplo a seguir mostra o processo do cliente.</span><span class="sxs-lookup"><span data-stu-id="44ad7-117">The following example shows the client process.</span></span> <span data-ttu-id="44ad7-118">O processo do servidor inicia o processo do cliente e oferece a ele um identificador de cliente.</span><span class="sxs-lookup"><span data-stu-id="44ad7-118">The server process starts the client process and gives that process a client handle.</span></span> <span data-ttu-id="44ad7-119">O executável que resulta do código do cliente deve ser chamado de `pipeClient.exe` e copiado para o mesmo diretório que o executável do servidor antes que o processo do servidor seja executado.</span><span class="sxs-lookup"><span data-stu-id="44ad7-119">The resulting executable from the client code should be named `pipeClient.exe` and be copied to the same directory as the server executable before running the server process.</span></span>  
  
 [!code-cpp[System.IO.Pipes.AnonymousPipeClientStream_Sample#01](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeClientStream_Sample/cpp/program.cpp#01)]
 [!code-csharp[System.IO.Pipes.AnonymousPipeClientStream_Sample#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeClientStream_Sample/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.AnonymousPipeClientStream_Sample#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeClientStream_Sample/vb/program.vb#01)]  
  
## <a name="see-also"></a><span data-ttu-id="44ad7-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="44ad7-120">See Also</span></span>  
 [<span data-ttu-id="44ad7-121">Pipes</span><span class="sxs-lookup"><span data-stu-id="44ad7-121">Pipes</span></span>](../../../docs/standard/io/pipe-operations.md)  
 [<span data-ttu-id="44ad7-122">Como usar pipes nomeados para comunicação entre processos na rede</span><span class="sxs-lookup"><span data-stu-id="44ad7-122">How to: Use Named Pipes for Network Interprocess Communication</span></span>](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md)
