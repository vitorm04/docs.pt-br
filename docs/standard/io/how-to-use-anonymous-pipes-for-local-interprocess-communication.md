---
title: Como usar pipes anônimos para comunicação entre processos locais
ms.date: 03/30/2017
ms.technology: dotnet-standard
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 846d97871492b89026d50dd89b78a28263863cce
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33573164"
---
# <a name="how-to-use-anonymous-pipes-for-local-interprocess-communication"></a><span data-ttu-id="a8be8-102">Como usar pipes anônimos para comunicação entre processos locais</span><span class="sxs-lookup"><span data-stu-id="a8be8-102">How to: Use Anonymous Pipes for Local Interprocess Communication</span></span>
<span data-ttu-id="a8be8-103">Os pipes anônimos fornecem comunicação entre processos em um computador local.</span><span class="sxs-lookup"><span data-stu-id="a8be8-103">Anonymous pipes provide interprocess communication on a local computer.</span></span> <span data-ttu-id="a8be8-104">Eles oferecem menos funcionalidades que pipes nomeados, mas também exigem menos sobrecarga.</span><span class="sxs-lookup"><span data-stu-id="a8be8-104">They offer less functionality than named pipes, but also require less overhead.</span></span> <span data-ttu-id="a8be8-105">Você pode usar pipes anônimos para facilitar a comunicação entre processos em um computador local.</span><span class="sxs-lookup"><span data-stu-id="a8be8-105">You can use anonymous pipes to make interprocess communication on a local computer easier.</span></span> <span data-ttu-id="a8be8-106">Você não pode usar pipes anônimos para comunicações através de uma rede.</span><span class="sxs-lookup"><span data-stu-id="a8be8-106">You cannot use anonymous pipes for communication over a network.</span></span>  
  
 <span data-ttu-id="a8be8-107">Para implementar pipes anônimos, use as classes <xref:System.IO.Pipes.AnonymousPipeServerStream> e <xref:System.IO.Pipes.AnonymousPipeClientStream>.</span><span class="sxs-lookup"><span data-stu-id="a8be8-107">To implement anonymous pipes, use the <xref:System.IO.Pipes.AnonymousPipeServerStream> and <xref:System.IO.Pipes.AnonymousPipeClientStream> classes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a8be8-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a8be8-108">Example</span></span>  
 <span data-ttu-id="a8be8-109">O exemplo a seguir demonstra uma maneira de enviar uma cadeia de caracteres de um processo pai para um processo filho usando pipes anônimos.</span><span class="sxs-lookup"><span data-stu-id="a8be8-109">The following example demonstrates a way to send a string from a parent process to a child process using anonymous pipes.</span></span> <span data-ttu-id="a8be8-110">Este exemplo cria um objeto <xref:System.IO.Pipes.AnonymousPipeServerStream> em um processo pai com um valor <xref:System.IO.Pipes.PipeDirection> de <xref:System.IO.Pipes.PipeDirection.Out>.</span><span class="sxs-lookup"><span data-stu-id="a8be8-110">This example creates an <xref:System.IO.Pipes.AnonymousPipeServerStream> object in a parent process with a <xref:System.IO.Pipes.PipeDirection> value of <xref:System.IO.Pipes.PipeDirection.Out>.</span></span> <span data-ttu-id="a8be8-111">Em seguida, o processo pai cria um processo filho usando um identificador de cliente para criar um objeto <xref:System.IO.Pipes.AnonymousPipeClientStream>.</span><span class="sxs-lookup"><span data-stu-id="a8be8-111">The parent process then creates a child process by using a client handle to create an <xref:System.IO.Pipes.AnonymousPipeClientStream> object.</span></span> <span data-ttu-id="a8be8-112">O processo filho tem um valor <xref:System.IO.Pipes.PipeDirection> de <xref:System.IO.Pipes.PipeDirection.In>.</span><span class="sxs-lookup"><span data-stu-id="a8be8-112">The child process has a <xref:System.IO.Pipes.PipeDirection> value of <xref:System.IO.Pipes.PipeDirection.In>.</span></span>  
  
 <span data-ttu-id="a8be8-113">Em seguida, o processo pai envia uma cadeia de caracteres fornecida pelo usuário ao processo filho.</span><span class="sxs-lookup"><span data-stu-id="a8be8-113">The parent process then sends a user-supplied string to the child process.</span></span> <span data-ttu-id="a8be8-114">A cadeia de caracteres é exibida no console do processo filho.</span><span class="sxs-lookup"><span data-stu-id="a8be8-114">The string is displayed to the console in the child process.</span></span>  
  
 <span data-ttu-id="a8be8-115">O exemplo a seguir mostra o processo do servidor.</span><span class="sxs-lookup"><span data-stu-id="a8be8-115">The following example shows the server process.</span></span>  
  
 [!code-cpp[System.IO.Pipes.AnonymousPipeServerStream_Sample#01](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeServerStream_Sample/cpp/program.cpp#01)]
 [!code-csharp[System.IO.Pipes.AnonymousPipeServerStream_Sample#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeServerStream_Sample/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.AnonymousPipeServerStream_Sample#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeServerStream_Sample/vb/program.vb#01)]  
  
## <a name="example"></a><span data-ttu-id="a8be8-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a8be8-116">Example</span></span>  
 <span data-ttu-id="a8be8-117">O exemplo a seguir mostra o processo do cliente.</span><span class="sxs-lookup"><span data-stu-id="a8be8-117">The following example shows the client process.</span></span> <span data-ttu-id="a8be8-118">O processo do servidor inicia o processo do cliente e oferece a ele um identificador de cliente.</span><span class="sxs-lookup"><span data-stu-id="a8be8-118">The server process starts the client process and gives that process a client handle.</span></span> <span data-ttu-id="a8be8-119">O executável que resulta do código do cliente deve ser chamado de `pipeClient.exe` e copiado para o mesmo diretório que o executável do servidor antes que o processo do servidor seja executado.</span><span class="sxs-lookup"><span data-stu-id="a8be8-119">The resulting executable from the client code should be named `pipeClient.exe` and be copied to the same directory as the server executable before running the server process.</span></span>  
  
 [!code-cpp[System.IO.Pipes.AnonymousPipeClientStream_Sample#01](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeClientStream_Sample/cpp/program.cpp#01)]
 [!code-csharp[System.IO.Pipes.AnonymousPipeClientStream_Sample#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeClientStream_Sample/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.AnonymousPipeClientStream_Sample#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeClientStream_Sample/vb/program.vb#01)]  
  
## <a name="see-also"></a><span data-ttu-id="a8be8-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a8be8-120">See Also</span></span>  
 [<span data-ttu-id="a8be8-121">Pipes</span><span class="sxs-lookup"><span data-stu-id="a8be8-121">Pipes</span></span>](../../../docs/standard/io/pipe-operations.md)  
 [<span data-ttu-id="a8be8-122">Como usar pipes nomeados para comunicação entre processos na rede</span><span class="sxs-lookup"><span data-stu-id="a8be8-122">How to: Use Named Pipes for Network Interprocess Communication</span></span>](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md)
