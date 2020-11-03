---
title: 'Como: Usar pipes anônimos para comunicação entre processos locais'
description: Saiba como usar pipes anônimos para comunicação entre processos locais em um computador local no .NET. Os pipes anônimos exigem menos sobrecarga do que os pipes nomeados.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- anonymous pipes [.NET]
- parent-child communication [.NET]
- pipes [.NET]
- one-way communication [.NET]
- local computer communication [.NET], pipes
ms.assetid: e7773c77-c646-4a01-8a96-a003d59fc4c9
ms.openlocfilehash: c9d223d975dc7ab251717a66de0bc845845dc9d7
ms.sourcegitcommit: 7588b1f16b7608bc6833c05f91ae670c22ef56f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/02/2020
ms.locfileid: "93189349"
---
# <a name="how-to-use-anonymous-pipes-for-local-interprocess-communication"></a><span data-ttu-id="2e500-104">Como: Usar pipes anônimos para comunicação entre processos locais</span><span class="sxs-lookup"><span data-stu-id="2e500-104">How to: Use Anonymous Pipes for Local Interprocess Communication</span></span>

<span data-ttu-id="2e500-105">Os pipes anônimos fornecem comunicação entre processos em um computador local.</span><span class="sxs-lookup"><span data-stu-id="2e500-105">Anonymous pipes provide interprocess communication on a local computer.</span></span> <span data-ttu-id="2e500-106">Eles oferecem menos funcionalidades que pipes nomeados, mas também exigem menos sobrecarga.</span><span class="sxs-lookup"><span data-stu-id="2e500-106">They offer less functionality than named pipes, but also require less overhead.</span></span> <span data-ttu-id="2e500-107">Você pode usar pipes anônimos para facilitar a comunicação entre processos em um computador local.</span><span class="sxs-lookup"><span data-stu-id="2e500-107">You can use anonymous pipes to make interprocess communication on a local computer easier.</span></span> <span data-ttu-id="2e500-108">Você não pode usar pipes anônimos para comunicações através de uma rede.</span><span class="sxs-lookup"><span data-stu-id="2e500-108">You cannot use anonymous pipes for communication over a network.</span></span>  
  
 <span data-ttu-id="2e500-109">Para implementar pipes anônimos, use as classes <xref:System.IO.Pipes.AnonymousPipeServerStream> e <xref:System.IO.Pipes.AnonymousPipeClientStream>.</span><span class="sxs-lookup"><span data-stu-id="2e500-109">To implement anonymous pipes, use the <xref:System.IO.Pipes.AnonymousPipeServerStream> and <xref:System.IO.Pipes.AnonymousPipeClientStream> classes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2e500-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2e500-110">Example</span></span>  
 <span data-ttu-id="2e500-111">O exemplo a seguir demonstra uma maneira de enviar uma cadeia de caracteres de um processo pai para um processo filho usando pipes anônimos.</span><span class="sxs-lookup"><span data-stu-id="2e500-111">The following example demonstrates a way to send a string from a parent process to a child process using anonymous pipes.</span></span> <span data-ttu-id="2e500-112">Este exemplo cria um objeto <xref:System.IO.Pipes.AnonymousPipeServerStream> em um processo pai com um valor <xref:System.IO.Pipes.PipeDirection> de <xref:System.IO.Pipes.PipeDirection.Out>.</span><span class="sxs-lookup"><span data-stu-id="2e500-112">This example creates an <xref:System.IO.Pipes.AnonymousPipeServerStream> object in a parent process with a <xref:System.IO.Pipes.PipeDirection> value of <xref:System.IO.Pipes.PipeDirection.Out>.</span></span> <span data-ttu-id="2e500-113">Em seguida, o processo pai cria um processo filho usando um identificador de cliente para criar um objeto <xref:System.IO.Pipes.AnonymousPipeClientStream>.</span><span class="sxs-lookup"><span data-stu-id="2e500-113">The parent process then creates a child process by using a client handle to create an <xref:System.IO.Pipes.AnonymousPipeClientStream> object.</span></span> <span data-ttu-id="2e500-114">O processo filho tem um valor <xref:System.IO.Pipes.PipeDirection> de <xref:System.IO.Pipes.PipeDirection.In>.</span><span class="sxs-lookup"><span data-stu-id="2e500-114">The child process has a <xref:System.IO.Pipes.PipeDirection> value of <xref:System.IO.Pipes.PipeDirection.In>.</span></span>  
  
 <span data-ttu-id="2e500-115">Em seguida, o processo pai envia uma cadeia de caracteres fornecida pelo usuário ao processo filho.</span><span class="sxs-lookup"><span data-stu-id="2e500-115">The parent process then sends a user-supplied string to the child process.</span></span> <span data-ttu-id="2e500-116">A cadeia de caracteres é exibida no console do processo filho.</span><span class="sxs-lookup"><span data-stu-id="2e500-116">The string is displayed to the console in the child process.</span></span>  
  
 <span data-ttu-id="2e500-117">O exemplo a seguir mostra o processo do servidor.</span><span class="sxs-lookup"><span data-stu-id="2e500-117">The following example shows the server process.</span></span>  
  
 [!code-cpp[System.IO.Pipes.AnonymousPipeServerStream_Sample#01](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeServerStream_Sample/cpp/program.cpp#01)]
 [!code-csharp[System.IO.Pipes.AnonymousPipeServerStream_Sample#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeServerStream_Sample/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.AnonymousPipeServerStream_Sample#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeServerStream_Sample/vb/program.vb#01)]  

[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]
  
## <a name="example"></a><span data-ttu-id="2e500-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2e500-118">Example</span></span>  
 <span data-ttu-id="2e500-119">O exemplo a seguir mostra o processo do cliente.</span><span class="sxs-lookup"><span data-stu-id="2e500-119">The following example shows the client process.</span></span> <span data-ttu-id="2e500-120">O processo do servidor inicia o processo do cliente e oferece a ele um identificador de cliente.</span><span class="sxs-lookup"><span data-stu-id="2e500-120">The server process starts the client process and gives that process a client handle.</span></span> <span data-ttu-id="2e500-121">O executável que resulta do código do cliente deve ser chamado de `pipeClient.exe` e copiado para o mesmo diretório que o executável do servidor antes que o processo do servidor seja executado.</span><span class="sxs-lookup"><span data-stu-id="2e500-121">The resulting executable from the client code should be named `pipeClient.exe` and be copied to the same directory as the server executable before running the server process.</span></span>  
  
 [!code-cpp[System.IO.Pipes.AnonymousPipeClientStream_Sample#01](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeClientStream_Sample/cpp/program.cpp#01)]
 [!code-csharp[System.IO.Pipes.AnonymousPipeClientStream_Sample#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeClientStream_Sample/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.AnonymousPipeClientStream_Sample#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeClientStream_Sample/vb/program.vb#01)]  
  
## <a name="see-also"></a><span data-ttu-id="2e500-122">Confira também</span><span class="sxs-lookup"><span data-stu-id="2e500-122">See also</span></span>

- [<span data-ttu-id="2e500-123">Pipes</span><span class="sxs-lookup"><span data-stu-id="2e500-123">Pipes</span></span>](pipe-operations.md)
- [<span data-ttu-id="2e500-124">Como: Usar pipes nomeados para comunicação entre processos na rede</span><span class="sxs-lookup"><span data-stu-id="2e500-124">How to: Use Named Pipes for Network Interprocess Communication</span></span>](how-to-use-named-pipes-for-network-interprocess-communication.md)
