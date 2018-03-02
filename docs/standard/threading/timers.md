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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 80b4cee03e934d3aec98ca323aac43f934c56455
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="timers"></a><span data-ttu-id="1db9a-102">Temporizadores</span><span class="sxs-lookup"><span data-stu-id="1db9a-102">Timers</span></span>
<span data-ttu-id="1db9a-103">Os temporizadores são objetos leves que permitem especificar um representante que será chamado em um horário especificado.</span><span class="sxs-lookup"><span data-stu-id="1db9a-103">Timers are lightweight objects that enable you to specify a delegate to be called at a specified time.</span></span> <span data-ttu-id="1db9a-104">Um thread no pool de threads executa a operação de espera.</span><span class="sxs-lookup"><span data-stu-id="1db9a-104">A thread in the thread pool performs the wait operation.</span></span>  
  
 <span data-ttu-id="1db9a-105">Com a classe <xref:System.Threading.Timer?displayProperty=nameWithType>, o processo é simples.</span><span class="sxs-lookup"><span data-stu-id="1db9a-105">Using the <xref:System.Threading.Timer?displayProperty=nameWithType> class is straightforward.</span></span> <span data-ttu-id="1db9a-106">Você cria um **Temporizador** passando um representante <xref:System.Threading.TimerCallback> para o método de retorno de chamada, um objeto que representa o estado que será passado para o retorno de chamada, um tempo de aumento inicial e um tempo que representa o período entre invocações do retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="1db9a-106">You create a **Timer**, passing a <xref:System.Threading.TimerCallback> delegate to the callback method, an object representing state that will be passed to the callback, an initial raise time, and a time representing the period between callback invocations.</span></span> <span data-ttu-id="1db9a-107">Para cancelar um temporizador pendente, chame a função **Timer.Dispose**.</span><span class="sxs-lookup"><span data-stu-id="1db9a-107">To cancel a pending timer, call the **Timer.Dispose** function.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1db9a-108">Há duas outras classes de temporizador.</span><span class="sxs-lookup"><span data-stu-id="1db9a-108">There are two other timer classes.</span></span> <span data-ttu-id="1db9a-109">A classe <xref:System.Windows.Forms.Timer?displayProperty=nameWithType> é um controle que funciona com designers visuais e deve ser usada em contextos de interface do usuário. Ela gera eventos no thread da interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="1db9a-109">The <xref:System.Windows.Forms.Timer?displayProperty=nameWithType> class is a control that works with visual designers and is meant to be used in user interface contexts; it raises events on the user interface thread.</span></span> <span data-ttu-id="1db9a-110">A classe <xref:System.Timers.Timer?displayProperty=nameWithType> é derivada de <xref:System.ComponentModel.Component>, portanto, pode ser usada com designers visuais. Ela também gera eventos, mas gera-os em um thread <xref:System.Threading.ThreadPool>.</span><span class="sxs-lookup"><span data-stu-id="1db9a-110">The <xref:System.Timers.Timer?displayProperty=nameWithType> class derives from <xref:System.ComponentModel.Component>, so it can be used with visual designers; it also raises events, but it raises them on a <xref:System.Threading.ThreadPool> thread.</span></span> <span data-ttu-id="1db9a-111">A classe <xref:System.Threading.Timer?displayProperty=nameWithType> faz retornos de chamada em um thread <xref:System.Threading.ThreadPool> e não usa o modelo de evento.</span><span class="sxs-lookup"><span data-stu-id="1db9a-111">The <xref:System.Threading.Timer?displayProperty=nameWithType> class makes callbacks on a <xref:System.Threading.ThreadPool> thread and does not use the event model at all.</span></span> <span data-ttu-id="1db9a-112">Ela também fornece um objeto de estado ao método de retorno de chamada que outros temporizadores não fornecem.</span><span class="sxs-lookup"><span data-stu-id="1db9a-112">It also provides a state object to the callback method, which the other timers do not.</span></span> <span data-ttu-id="1db9a-113">A classe é extremamente leve.</span><span class="sxs-lookup"><span data-stu-id="1db9a-113">It is extremely lightweight.</span></span>  
  
 <span data-ttu-id="1db9a-114">O exemplo de código a seguir inicia um temporizador que é iniciado após um segundo (1.000 milissegundos) e marca cada segundo até você pressionar a tecla **Enter**.</span><span class="sxs-lookup"><span data-stu-id="1db9a-114">The following code example starts a timer that starts after one second (1000 milliseconds) and ticks every second until you press the **Enter** key.</span></span> <span data-ttu-id="1db9a-115">A variável que contém a referência do temporizador é um campo de nível de classe para garantir que o temporizador não esteja sujeito à coleta de lixo enquanto ele ainda estiver em execução.</span><span class="sxs-lookup"><span data-stu-id="1db9a-115">The variable containing the reference to the timer is a class-level field, to ensure that the timer is not subject to garbage collection while it is still running.</span></span> <span data-ttu-id="1db9a-116">Para saber mais sobre a coleta de lixo agressiva, confira <xref:System.GC.KeepAlive%2A>.</span><span class="sxs-lookup"><span data-stu-id="1db9a-116">For more information on aggressive garbage collection, see <xref:System.GC.KeepAlive%2A>.</span></span>  
  
 [!code-cpp[System.Threading.Timer#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.Timer/CPP/source2.cpp#2)]
 [!code-csharp[System.Threading.Timer#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.Timer/CS/source2.cs#2)]
 [!code-vb[System.Threading.Timer#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.Timer/VB/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="1db9a-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1db9a-117">See Also</span></span>  
 <xref:System.Threading.Timer>  
 [<span data-ttu-id="1db9a-118">Objetos e recursos de threading</span><span class="sxs-lookup"><span data-stu-id="1db9a-118">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)
