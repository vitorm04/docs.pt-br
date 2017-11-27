---
title: "Limitações da propriedade de intervalo do componente de temporizador dos Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- timers [Windows Forms], event intervals
- Interval property [Windows Forms], limitations
- timers [Windows Forms], Windows-based
- Timer component [Windows Forms], limitations of Interval property
ms.assetid: 7e5fb513-77e7-4046-a8e8-aab94e61ca0f
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 72af16b7dcb7709dd132a3748a454eda57acc168
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="limitations-of-the-windows-forms-timer-component39s-interval-property"></a><span data-ttu-id="33d24-102">Limitações da propriedade de intervalo do componente de temporizador dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="33d24-102">Limitations of the Windows Forms Timer Component&#39;s Interval Property</span></span>
<span data-ttu-id="33d24-103">Windows Forms <xref:System.Windows.Forms.Timer> componente tem um <xref:System.Windows.Forms.Timer.Interval%2A> propriedade que especifica o número de milissegundos que passam entre o evento de um timer e a próxima.</span><span class="sxs-lookup"><span data-stu-id="33d24-103">The Windows Forms <xref:System.Windows.Forms.Timer> component has an <xref:System.Windows.Forms.Timer.Interval%2A> property that specifies the number of milliseconds that pass between one timer event and the next.</span></span> <span data-ttu-id="33d24-104">A menos que o componente está desativado, um temporizador continua a receber o <xref:System.Windows.Forms.Timer.Tick> evento aproximadamente igual intervalos de tempo.</span><span class="sxs-lookup"><span data-stu-id="33d24-104">Unless the component is disabled, a timer continues to receive the <xref:System.Windows.Forms.Timer.Tick> event at roughly equal intervals of time.</span></span>  
  
 <span data-ttu-id="33d24-105">Esse componente foi projetado para um ambiente do Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="33d24-105">This component is designed for a Windows Forms environment.</span></span> <span data-ttu-id="33d24-106">Se você precisar de um temporizador que seja adequado para um ambiente de servidor, consulte [Introdução a temporizadores baseados em servidor](http://msdn.microsoft.com/en-us/adc0bc0a-a519-4812-bafc-fb9d1a5801fc).</span><span class="sxs-lookup"><span data-stu-id="33d24-106">If you need a timer that is suitable for a server environment, see [Introduction to Server-Based Timers](http://msdn.microsoft.com/en-us/adc0bc0a-a519-4812-bafc-fb9d1a5801fc).</span></span>  
  
## <a name="the-interval-property"></a><span data-ttu-id="33d24-107">A propriedade Interval</span><span class="sxs-lookup"><span data-stu-id="33d24-107">The Interval Property</span></span>  
 <span data-ttu-id="33d24-108">O <xref:System.Windows.Forms.Timer.Interval%2A> propriedade tem algumas limitações a serem consideradas quando você estiver programando um <xref:System.Windows.Forms.Timer> componente:</span><span class="sxs-lookup"><span data-stu-id="33d24-108">The <xref:System.Windows.Forms.Timer.Interval%2A> property has a few limitations to consider when you are programming a <xref:System.Windows.Forms.Timer> component:</span></span>  
  
-   <span data-ttu-id="33d24-109">Se seu aplicativo ou outro aplicativo está fazendo exigem muito do sistema — como loops longo, cálculos intensivos, unidade, rede ou acesso de porta — seu aplicativo não pode obter eventos de timer sempre como o <xref:System.Windows.Forms.Timer.Interval%2A> propriedade especifica.</span><span class="sxs-lookup"><span data-stu-id="33d24-109">If your application or another application is making heavy demands on the system — such as long loops, intensive calculations, or drive, network, or port access — your application may not get timer events as often as the <xref:System.Windows.Forms.Timer.Interval%2A> property specifies.</span></span>  
  
-   <span data-ttu-id="33d24-110">Não há garantia de que o intervalo decorra exatamente na hora.</span><span class="sxs-lookup"><span data-stu-id="33d24-110">The interval is not guaranteed to elapse exactly on time.</span></span> <span data-ttu-id="33d24-111">Para garantir a precisão, o temporizador deve verificar o relógio do sistema conforme necessário, em vez de tentar manter o controle de tempo acumulado internamente.</span><span class="sxs-lookup"><span data-stu-id="33d24-111">To ensure accuracy, the timer should check the system clock as needed, rather than try to keep track of accumulated time internally.</span></span>  
  
-   <span data-ttu-id="33d24-112">A precisão de <xref:System.Windows.Forms.Timer.Interval%2A> propriedade é em milissegundos.</span><span class="sxs-lookup"><span data-stu-id="33d24-112">The precision of the <xref:System.Windows.Forms.Timer.Interval%2A> property is in milliseconds.</span></span> <span data-ttu-id="33d24-113">Alguns computadores fornecem um contador de alta resolução que tem uma resolução maior do que milissegundos.</span><span class="sxs-lookup"><span data-stu-id="33d24-113">Some computers provide a high-resolution counter that has a resolution higher than milliseconds.</span></span> <span data-ttu-id="33d24-114">A disponibilidade desse contador depende do hardware do processador do computador.</span><span class="sxs-lookup"><span data-stu-id="33d24-114">The availability of such a counter depends on the processor hardware of your computer.</span></span> <span data-ttu-id="33d24-115">Para obter mais informações, consulte o artigo 172338, "Como para usar QueryPerformanceCounter para o código de tempo" na Base de dados de Conhecimento Microsoft em http://support.microsoft.com.</span><span class="sxs-lookup"><span data-stu-id="33d24-115">For more information, see article 172338, "How To Use QueryPerformanceCounter to Time Code," in the Microsoft Knowledge Base at http://support.microsoft.com.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33d24-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="33d24-116">See Also</span></span>  
 <xref:System.Windows.Forms.Timer>  
 [<span data-ttu-id="33d24-117">Componente Timer</span><span class="sxs-lookup"><span data-stu-id="33d24-117">Timer Component</span></span>](../../../../docs/framework/winforms/controls/timer-component-windows-forms.md)  
 [<span data-ttu-id="33d24-118">Visão geral do componente de temporizador</span><span class="sxs-lookup"><span data-stu-id="33d24-118">Timer Component Overview</span></span>](../../../../docs/framework/winforms/controls/timer-component-overview-windows-forms.md)
