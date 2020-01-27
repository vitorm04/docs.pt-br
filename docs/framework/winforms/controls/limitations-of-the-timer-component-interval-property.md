---
title: Limitações da propriedade Interval do componente de timer
ms.date: 03/30/2017
helpviewer_keywords:
- timers [Windows Forms], event intervals
- Interval property [Windows Forms], limitations
- timers [Windows Forms], Windows-based
- Timer component [Windows Forms], limitations of Interval property
ms.assetid: 7e5fb513-77e7-4046-a8e8-aab94e61ca0f
ms.openlocfilehash: 15626a53f0541ff79e2098377d9dfdb4626ac155
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745237"
---
# <a name="limitations-of-the-windows-forms-timer-components-interval-property"></a><span data-ttu-id="4283e-102">Limitações da propriedade de intervalo do componente de temporizador dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4283e-102">Limitations of the Windows Forms Timer Component's Interval Property</span></span>
<span data-ttu-id="4283e-103">O componente Windows Forms <xref:System.Windows.Forms.Timer> tem uma propriedade <xref:System.Windows.Forms.Timer.Interval%2A> que especifica o número de milissegundos que passam entre um evento de temporizador e o próximo.</span><span class="sxs-lookup"><span data-stu-id="4283e-103">The Windows Forms <xref:System.Windows.Forms.Timer> component has an <xref:System.Windows.Forms.Timer.Interval%2A> property that specifies the number of milliseconds that pass between one timer event and the next.</span></span> <span data-ttu-id="4283e-104">A menos que o componente esteja desabilitado, um temporizador continua a receber o evento <xref:System.Windows.Forms.Timer.Tick> em intervalos de tempo aproximadamente iguais.</span><span class="sxs-lookup"><span data-stu-id="4283e-104">Unless the component is disabled, a timer continues to receive the <xref:System.Windows.Forms.Timer.Tick> event at roughly equal intervals of time.</span></span>  
  
 <span data-ttu-id="4283e-105">Esse componente foi criado para um ambiente dos Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="4283e-105">This component is designed for a Windows Forms environment.</span></span> <span data-ttu-id="4283e-106">Se você precisar de um temporizador que seja adequado para um ambiente de servidor, consulte [Introdução a temporizadores baseados em servidor](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="4283e-106">If you need a timer that is suitable for a server environment, see [Introduction to Server-Based Timers](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).</span></span>  
  
## <a name="the-interval-property"></a><span data-ttu-id="4283e-107">A propriedade Interval</span><span class="sxs-lookup"><span data-stu-id="4283e-107">The Interval Property</span></span>  
 <span data-ttu-id="4283e-108">A propriedade <xref:System.Windows.Forms.Timer.Interval%2A> tem algumas limitações a serem consideradas ao programar um componente de <xref:System.Windows.Forms.Timer>:</span><span class="sxs-lookup"><span data-stu-id="4283e-108">The <xref:System.Windows.Forms.Timer.Interval%2A> property has a few limitations to consider when you are programming a <xref:System.Windows.Forms.Timer> component:</span></span>  
  
- <span data-ttu-id="4283e-109">Se seu aplicativo ou outro aplicativo estiver tomando demandas pesadas no sistema — como loops longos, cálculos intensivos ou acesso a uma unidade, rede ou porta — seu aplicativo poderá não obter eventos de timer com tanta frequência como a propriedade <xref:System.Windows.Forms.Timer.Interval%2A> especifica.</span><span class="sxs-lookup"><span data-stu-id="4283e-109">If your application or another application is making heavy demands on the system — such as long loops, intensive calculations, or drive, network, or port access — your application may not get timer events as often as the <xref:System.Windows.Forms.Timer.Interval%2A> property specifies.</span></span>  
  
- <span data-ttu-id="4283e-110">Não há garantia de que o intervalo decorra exatamente na hora.</span><span class="sxs-lookup"><span data-stu-id="4283e-110">The interval is not guaranteed to elapse exactly on time.</span></span> <span data-ttu-id="4283e-111">Para garantir a precisão, o temporizador deve verificar o relógio do sistema conforme necessário, em vez de tentar manter o controle de tempo acumulado internamente.</span><span class="sxs-lookup"><span data-stu-id="4283e-111">To ensure accuracy, the timer should check the system clock as needed, rather than try to keep track of accumulated time internally.</span></span>  
  
- <span data-ttu-id="4283e-112">A precisão da propriedade <xref:System.Windows.Forms.Timer.Interval%2A> é em milissegundos.</span><span class="sxs-lookup"><span data-stu-id="4283e-112">The precision of the <xref:System.Windows.Forms.Timer.Interval%2A> property is in milliseconds.</span></span> <span data-ttu-id="4283e-113">Alguns computadores fornecem um contador de alta resolução que tem uma resolução maior do que milissegundos.</span><span class="sxs-lookup"><span data-stu-id="4283e-113">Some computers provide a high-resolution counter that has a resolution higher than milliseconds.</span></span> <span data-ttu-id="4283e-114">A disponibilidade desse contador depende do hardware do processador do computador.</span><span class="sxs-lookup"><span data-stu-id="4283e-114">The availability of such a counter depends on the processor hardware of your computer.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="4283e-115">Veja também</span><span class="sxs-lookup"><span data-stu-id="4283e-115">See also</span></span>

- <xref:System.Windows.Forms.Timer>
- [<span data-ttu-id="4283e-116">Componente Timer</span><span class="sxs-lookup"><span data-stu-id="4283e-116">Timer Component</span></span>](timer-component-windows-forms.md)
- [<span data-ttu-id="4283e-117">Visão geral do componente de temporizador</span><span class="sxs-lookup"><span data-stu-id="4283e-117">Timer Component Overview</span></span>](timer-component-overview-windows-forms.md)
