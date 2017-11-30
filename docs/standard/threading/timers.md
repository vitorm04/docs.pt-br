---
title: Temporizadores
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
- threading [.NET Framework], timers
- timers, about timers
ms.assetid: 7091500d-be18-499b-a942-95366ce185e5
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: fca27cf5261e253c2bb3d3a10fa3db31f28a2415
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="timers"></a><span data-ttu-id="2a2e1-102">Temporizadores</span><span class="sxs-lookup"><span data-stu-id="2a2e1-102">Timers</span></span>
<span data-ttu-id="2a2e1-103">Temporizadores são objetos simples que permitem que você especifique um delegado a ser chamado em um horário especificado.</span><span class="sxs-lookup"><span data-stu-id="2a2e1-103">Timers are lightweight objects that enable you to specify a delegate to be called at a specified time.</span></span> <span data-ttu-id="2a2e1-104">Um thread no pool de threads executa a operação de espera.</span><span class="sxs-lookup"><span data-stu-id="2a2e1-104">A thread in the thread pool performs the wait operation.</span></span>  
  
 <span data-ttu-id="2a2e1-105">Usando o <xref:System.Threading.Timer?displayProperty=nameWithType> classe é simples.</span><span class="sxs-lookup"><span data-stu-id="2a2e1-105">Using the <xref:System.Threading.Timer?displayProperty=nameWithType> class is straightforward.</span></span> <span data-ttu-id="2a2e1-106">Você cria um **Timer**, passando um <xref:System.Threading.TimerCallback> delegado para o método de retorno de chamada, um objeto que representa o estado que será passado para o retorno de chamada e uma hora inicial acionar uma hora que representa o período entre as chamadas de retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="2a2e1-106">You create a **Timer**, passing a <xref:System.Threading.TimerCallback> delegate to the callback method, an object representing state that will be passed to the callback, an initial raise time, and a time representing the period between callback invocations.</span></span> <span data-ttu-id="2a2e1-107">Para cancelar um timer pendentes, chame o **Timer.Dispose** função.</span><span class="sxs-lookup"><span data-stu-id="2a2e1-107">To cancel a pending timer, call the **Timer.Dispose** function.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2a2e1-108">Há duas outras classes de temporizador.</span><span class="sxs-lookup"><span data-stu-id="2a2e1-108">There are two other timer classes.</span></span> <span data-ttu-id="2a2e1-109">O <xref:System.Windows.Forms.Timer?displayProperty=nameWithType> classe é um controle que funciona com designers visuais e se destina a ser usado em contextos de interface do usuário; ela gera eventos no thread de interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="2a2e1-109">The <xref:System.Windows.Forms.Timer?displayProperty=nameWithType> class is a control that works with visual designers and is meant to be used in user interface contexts; it raises events on the user interface thread.</span></span> <span data-ttu-id="2a2e1-110">O <xref:System.Timers.Timer?displayProperty=nameWithType> classe derivada de <xref:System.ComponentModel.Component>, portanto ele pode ser usado com designers visuais; ela também gera eventos, mas aumenta em um <xref:System.Threading.ThreadPool> thread.</span><span class="sxs-lookup"><span data-stu-id="2a2e1-110">The <xref:System.Timers.Timer?displayProperty=nameWithType> class derives from <xref:System.ComponentModel.Component>, so it can be used with visual designers; it also raises events, but it raises them on a <xref:System.Threading.ThreadPool> thread.</span></span> <span data-ttu-id="2a2e1-111">O <xref:System.Threading.Timer?displayProperty=nameWithType> classe torna retornos de chamada em um <xref:System.Threading.ThreadPool> de thread e não usa o modelo de evento.</span><span class="sxs-lookup"><span data-stu-id="2a2e1-111">The <xref:System.Threading.Timer?displayProperty=nameWithType> class makes callbacks on a <xref:System.Threading.ThreadPool> thread and does not use the event model at all.</span></span> <span data-ttu-id="2a2e1-112">Ele também fornece um objeto de estado para o método de retorno de chamada, que não os outros timers.</span><span class="sxs-lookup"><span data-stu-id="2a2e1-112">It also provides a state object to the callback method, which the other timers do not.</span></span> <span data-ttu-id="2a2e1-113">É extremamente leve.</span><span class="sxs-lookup"><span data-stu-id="2a2e1-113">It is extremely lightweight.</span></span>  
  
 <span data-ttu-id="2a2e1-114">O exemplo de código a seguir inicia um temporizador que é iniciado depois de um segundo (1000 milissegundos) e escalas cada segundo até que você pressiona o **Enter** chave.</span><span class="sxs-lookup"><span data-stu-id="2a2e1-114">The following code example starts a timer that starts after one second (1000 milliseconds) and ticks every second until you press the **Enter** key.</span></span> <span data-ttu-id="2a2e1-115">A variável que contém a referência para o timer é um campo de nível de classe, para garantir que o timer não está sujeita à coleta de lixo enquanto ele ainda está em execução.</span><span class="sxs-lookup"><span data-stu-id="2a2e1-115">The variable containing the reference to the timer is a class-level field, to ensure that the timer is not subject to garbage collection while it is still running.</span></span> <span data-ttu-id="2a2e1-116">Para obter mais informações sobre a coleta de lixo agressiva, consulte <xref:System.GC.KeepAlive%2A>.</span><span class="sxs-lookup"><span data-stu-id="2a2e1-116">For more information on aggressive garbage collection, see <xref:System.GC.KeepAlive%2A>.</span></span>  
  
 [!code-cpp[System.Threading.Timer#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.Timer/CPP/source2.cpp#2)]
 [!code-csharp[System.Threading.Timer#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.Timer/CS/source2.cs#2)]
 [!code-vb[System.Threading.Timer#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.Timer/VB/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="2a2e1-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2a2e1-117">See Also</span></span>  
 <xref:System.Threading.Timer>  
 [<span data-ttu-id="2a2e1-118">Objetos e recursos de threading</span><span class="sxs-lookup"><span data-stu-id="2a2e1-118">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)
