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
# <a name="how-to-use-anonymous-pipes-for-local-interprocess-communication"></a><span data-ttu-id="47d5a-102">Como usar pipes anônimos para comunicação entre processos locais</span><span class="sxs-lookup"><span data-stu-id="47d5a-102">How to: Use Anonymous Pipes for Local Interprocess Communication</span></span>
<span data-ttu-id="47d5a-103">Pipes anônimos fornecem comunicação entre processos em um computador local.</span><span class="sxs-lookup"><span data-stu-id="47d5a-103">Anonymous pipes provide interprocess communication on a local computer.</span></span> <span data-ttu-id="47d5a-104">Eles oferecem menos funcionalidade que pipes nomeados, mas também exigem menos sobrecarga.</span><span class="sxs-lookup"><span data-stu-id="47d5a-104">They offer less functionality than named pipes, but also require less overhead.</span></span> <span data-ttu-id="47d5a-105">Você pode usar pipes anônimos para facilitar a comunicação entre processos em um computador local.</span><span class="sxs-lookup"><span data-stu-id="47d5a-105">You can use anonymous pipes to make interprocess communication on a local computer easier.</span></span> <span data-ttu-id="47d5a-106">Você não pode usar pipes anônimos para comunicação através de uma rede.</span><span class="sxs-lookup"><span data-stu-id="47d5a-106">You cannot use anonymous pipes for communication over a network.</span></span>  
  
 <span data-ttu-id="47d5a-107">Para implementar pipes anônimos, use o <xref:System.IO.Pipes.AnonymousPipeServerStream> e <xref:System.IO.Pipes.AnonymousPipeClientStream> classes.</span><span class="sxs-lookup"><span data-stu-id="47d5a-107">To implement anonymous pipes, use the <xref:System.IO.Pipes.AnonymousPipeServerStream> and <xref:System.IO.Pipes.AnonymousPipeClientStream> classes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="47d5a-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="47d5a-108">Example</span></span>  
 <span data-ttu-id="47d5a-109">O exemplo a seguir demonstra uma maneira de enviar uma cadeia de caracteres de um processo pai para um processo filho usando pipes anônimos.</span><span class="sxs-lookup"><span data-stu-id="47d5a-109">The following example demonstrates a way to send a string from a parent process to a child process using anonymous pipes.</span></span> <span data-ttu-id="47d5a-110">Este exemplo cria um <xref:System.IO.Pipes.AnonymousPipeServerStream> objeto em um processo pai com um <xref:System.IO.Pipes.PipeDirection> valor <xref:System.IO.Pipes.PipeDirection.Out>.</span><span class="sxs-lookup"><span data-stu-id="47d5a-110">This example creates an <xref:System.IO.Pipes.AnonymousPipeServerStream> object in a parent process with a <xref:System.IO.Pipes.PipeDirection> value of <xref:System.IO.Pipes.PipeDirection.Out>.</span></span> <span data-ttu-id="47d5a-111">O processo pai, em seguida, cria um processo filho usando um identificador de cliente para criar um <xref:System.IO.Pipes.AnonymousPipeClientStream> objeto.</span><span class="sxs-lookup"><span data-stu-id="47d5a-111">The parent process then creates a child process by using a client handle to create an <xref:System.IO.Pipes.AnonymousPipeClientStream> object.</span></span> <span data-ttu-id="47d5a-112">O processo filho tem um <xref:System.IO.Pipes.PipeDirection> valor <xref:System.IO.Pipes.PipeDirection.In>.</span><span class="sxs-lookup"><span data-stu-id="47d5a-112">The child process has a <xref:System.IO.Pipes.PipeDirection> value of <xref:System.IO.Pipes.PipeDirection.In>.</span></span>  
  
 <span data-ttu-id="47d5a-113">O processo pai, em seguida, envia uma cadeia de caracteres fornecida pelo usuário para o processo filho.</span><span class="sxs-lookup"><span data-stu-id="47d5a-113">The parent process then sends a user-supplied string to the child process.</span></span> <span data-ttu-id="47d5a-114">A cadeia de caracteres é exibida no console do processo filho.</span><span class="sxs-lookup"><span data-stu-id="47d5a-114">The string is displayed to the console in the child process.</span></span>  
  
 <span data-ttu-id="47d5a-115">O exemplo a seguir mostra o processo do servidor.</span><span class="sxs-lookup"><span data-stu-id="47d5a-115">The following example shows the server process.</span></span>  
  
 [!code-cpp[System.IO.Pipes.AnonymousPipeServerStream_Sample#01](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeServerStream_Sample/cpp/program.cpp#01)]
 [!code-csharp[System.IO.Pipes.AnonymousPipeServerStream_Sample#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeServerStream_Sample/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.AnonymousPipeServerStream_Sample#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeServerStream_Sample/vb/program.vb#01)]  
  
## <a name="example"></a><span data-ttu-id="47d5a-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="47d5a-116">Example</span></span>  
 <span data-ttu-id="47d5a-117">O exemplo a seguir mostra o processo de cliente.</span><span class="sxs-lookup"><span data-stu-id="47d5a-117">The following example shows the client process.</span></span> <span data-ttu-id="47d5a-118">O processo do servidor inicia o processo de cliente e oferece a esse processo um identificador de cliente.</span><span class="sxs-lookup"><span data-stu-id="47d5a-118">The server process starts the client process and gives that process a client handle.</span></span> <span data-ttu-id="47d5a-119">O executável resultante do código do cliente deve ser nomeado `pipeClient.exe` e ser copiado para o mesmo diretório que o servidor executável antes de executar o processo do servidor.</span><span class="sxs-lookup"><span data-stu-id="47d5a-119">The resulting executable from the client code should be named `pipeClient.exe` and be copied to the same directory as the server executable before running the server process.</span></span>  
  
 [!code-cpp[System.IO.Pipes.AnonymousPipeClientStream_Sample#01](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeClientStream_Sample/cpp/program.cpp#01)]
 [!code-csharp[System.IO.Pipes.AnonymousPipeClientStream_Sample#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeClientStream_Sample/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.AnonymousPipeClientStream_Sample#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeClientStream_Sample/vb/program.vb#01)]  
  
## <a name="see-also"></a><span data-ttu-id="47d5a-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="47d5a-120">See Also</span></span>  
 [<span data-ttu-id="47d5a-121">Pipes</span><span class="sxs-lookup"><span data-stu-id="47d5a-121">Pipes</span></span>](../../../docs/standard/io/pipe-operations.md)  
 [<span data-ttu-id="47d5a-122">Como usar pipes nomeados para comunicação entre processos na rede</span><span class="sxs-lookup"><span data-stu-id="47d5a-122">How to: Use Named Pipes for Network Interprocess Communication</span></span>](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md)
