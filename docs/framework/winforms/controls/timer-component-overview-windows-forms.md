---
title: Visão geral do componente de temporizador
ms.date: 03/30/2017
f1_keywords:
- Timer
helpviewer_keywords:
- Timer component [Windows Forms], about Timer components
- timers [Windows Forms], about timers
ms.assetid: e672c05b-a8b6-4b26-9e4d-9223aa9e3873
ms.openlocfilehash: 83b52d395cdc3e3357bcf83517eab258a5c8ae08
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742772"
---
# <a name="timer-component-overview-windows-forms"></a><span data-ttu-id="63ad1-102">Visão geral do componente de temporizador (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="63ad1-102">Timer Component Overview (Windows Forms)</span></span>
<span data-ttu-id="63ad1-103">O <xref:System.Windows.Forms.Timer> de Windows Forms é um componente que gera um evento em intervalos regulares.</span><span class="sxs-lookup"><span data-stu-id="63ad1-103">The Windows Forms <xref:System.Windows.Forms.Timer> is a component that raises an event at regular intervals.</span></span> <span data-ttu-id="63ad1-104">Esse componente foi criado para um ambiente dos Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="63ad1-104">This component is designed for a Windows Forms environment.</span></span> <span data-ttu-id="63ad1-105">Se você precisar de um temporizador que seja adequado para um ambiente de servidor, consulte [Introdução a temporizadores baseados em servidor](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="63ad1-105">If you need a timer that is suitable for a server environment, see [Introduction to Server-Based Timers](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).</span></span>  
  
## <a name="key-properties-methods-and-events"></a><span data-ttu-id="63ad1-106">Propriedades, métodos e eventos de chave</span><span class="sxs-lookup"><span data-stu-id="63ad1-106">Key Properties, Methods, and Events</span></span>  
 <span data-ttu-id="63ad1-107">O comprimento dos intervalos é definido pela propriedade <xref:System.Windows.Forms.Timer.Interval%2A>, cujo valor é em milissegundos.</span><span class="sxs-lookup"><span data-stu-id="63ad1-107">The length of the intervals is defined by the <xref:System.Windows.Forms.Timer.Interval%2A> property, whose value is in milliseconds.</span></span> <span data-ttu-id="63ad1-108">Quando o componente é habilitado, o evento <xref:System.Windows.Forms.Timer.Tick> é gerado a cada intervalo.</span><span class="sxs-lookup"><span data-stu-id="63ad1-108">When the component is enabled, the <xref:System.Windows.Forms.Timer.Tick> event is raised every interval.</span></span> <span data-ttu-id="63ad1-109">É aí que você adicionaria o código a ser executado.</span><span class="sxs-lookup"><span data-stu-id="63ad1-109">This is where you would add code to be executed.</span></span> <span data-ttu-id="63ad1-110">Para obter mais informações, consulte [como: executar procedimentos em intervalos definidos com o componente de Timer Windows Forms](run-procedures-at-set-intervals-with-wf-timer-component.md).</span><span class="sxs-lookup"><span data-stu-id="63ad1-110">For more information, see [How to: Run Procedures at Set Intervals with the Windows Forms Timer Component](run-procedures-at-set-intervals-with-wf-timer-component.md).</span></span> <span data-ttu-id="63ad1-111">Os principais métodos do componente <xref:System.Windows.Forms.Timer> são <xref:System.Windows.Forms.Timer.Start%2A> e <xref:System.Windows.Forms.Timer.Stop%2A>, o que ativa e desativa o temporizador.</span><span class="sxs-lookup"><span data-stu-id="63ad1-111">The key methods of the <xref:System.Windows.Forms.Timer> component are <xref:System.Windows.Forms.Timer.Start%2A> and <xref:System.Windows.Forms.Timer.Stop%2A>, which turn the timer on and off.</span></span> <span data-ttu-id="63ad1-112">Quando o temporizador é desligado, ele é redefinido; Não é possível pausar um componente <xref:System.Windows.Forms.Timer>.</span><span class="sxs-lookup"><span data-stu-id="63ad1-112">When the timer is switched off, it resets; there is no way to pause a <xref:System.Windows.Forms.Timer> component.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63ad1-113">Veja também</span><span class="sxs-lookup"><span data-stu-id="63ad1-113">See also</span></span>

- <xref:System.Windows.Forms.Timer>
- [<span data-ttu-id="63ad1-114">Componente Timer</span><span class="sxs-lookup"><span data-stu-id="63ad1-114">Timer Component</span></span>](timer-component-windows-forms.md)
- [<span data-ttu-id="63ad1-115">Limitações da propriedade de intervalo do componente temporizador dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="63ad1-115">Limitations of the Windows Forms Timer Component's Interval Property</span></span>](limitations-of-the-timer-component-interval-property.md)
