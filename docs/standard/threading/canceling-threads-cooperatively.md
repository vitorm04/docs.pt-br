---
title: Cancelando threads de forma cooperativa
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- threads, cancellation
ms.assetid: d2d6d5fd-e263-4fa0-847b-2fc3e0d82337
ms.openlocfilehash: 1d1433ecf39974bf9e68fe07b9d0818ac16fb544
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73138121"
---
# <a name="canceling-threads-cooperatively"></a><span data-ttu-id="bfbf1-102">Cancelando threads de forma cooperativa</span><span class="sxs-lookup"><span data-stu-id="bfbf1-102">Canceling threads cooperatively</span></span>

<span data-ttu-id="bfbf1-103">Antes do .NET Framework 4, o .NET Framework não fornecia uma maneira integrada de cancelar um thread de forma cooperativa após ele ter sido iniciado.</span><span class="sxs-lookup"><span data-stu-id="bfbf1-103">Prior to the .NET Framework 4, the .NET Framework provided no built-in way to cancel a thread cooperatively after it was started.</span></span> <span data-ttu-id="bfbf1-104">No entanto, a partir do .NET Framework 4, é possível usar um <xref:System.Threading.CancellationToken?displayProperty=nameWithType> para cancelar threads, assim como você pode usá-los para cancelar consultas PLINQ ou objetos <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="bfbf1-104">However, starting with the .NET Framework 4, you can use a <xref:System.Threading.CancellationToken?displayProperty=nameWithType> to cancel threads, just as you can use them to cancel <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> objects or PLINQ queries.</span></span> <span data-ttu-id="bfbf1-105">Embora a classe <xref:System.Threading.Thread?displayProperty=nameWithType> não ofereça suporte interno para tokens de cancelamento, você pode passar um token para um procedimento de thread usando o constructo <xref:System.Threading.Thread> que usa um representante <xref:System.Threading.ParameterizedThreadStart>.</span><span class="sxs-lookup"><span data-stu-id="bfbf1-105">Although the <xref:System.Threading.Thread?displayProperty=nameWithType> class does not offer built-in support for cancellation tokens, you can pass a token to a thread procedure by using the <xref:System.Threading.Thread> constructor that takes a <xref:System.Threading.ParameterizedThreadStart> delegate.</span></span> <span data-ttu-id="bfbf1-106">O exemplo a seguir demonstra como fazer isso.</span><span class="sxs-lookup"><span data-stu-id="bfbf1-106">The following example demonstrates how to do this.</span></span>  
  
 [!code-csharp[Cancellation#14](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/CooperativeThreads.cs#14)]
 [!code-vb[Cancellation#14](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/CooperativeThreads.vb#14)]  
  
## <a name="see-also"></a><span data-ttu-id="bfbf1-107">Confira também</span><span class="sxs-lookup"><span data-stu-id="bfbf1-107">See also</span></span>

- [<span data-ttu-id="bfbf1-108">Usando threads e threading</span><span class="sxs-lookup"><span data-stu-id="bfbf1-108">Using Threads and Threading</span></span>](using-threads-and-threading.md)
