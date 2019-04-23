---
title: Visão geral do componente de temporizador (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- Timer
helpviewer_keywords:
- Timer component [Windows Forms], about Timer components
- timers [Windows Forms], about timers
ms.assetid: e672c05b-a8b6-4b26-9e4d-9223aa9e3873
ms.openlocfilehash: 5bef0ba87d6a496acf7575965128be2b20b437ab
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59074203"
---
# <a name="timer-component-overview-windows-forms"></a><span data-ttu-id="19622-102">Visão geral do componente de temporizador (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="19622-102">Timer Component Overview (Windows Forms)</span></span>
<span data-ttu-id="19622-103">Os formulários do Windows <xref:System.Windows.Forms.Timer> é um componente que gera um evento em intervalos regulares.</span><span class="sxs-lookup"><span data-stu-id="19622-103">The Windows Forms <xref:System.Windows.Forms.Timer> is a component that raises an event at regular intervals.</span></span> <span data-ttu-id="19622-104">Esse componente foi projetado para um ambiente do Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="19622-104">This component is designed for a Windows Forms environment.</span></span> <span data-ttu-id="19622-105">Se você precisar de um temporizador que seja adequado para um ambiente de servidor, consulte [Introdução a temporizadores baseados em servidor](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="19622-105">If you need a timer that is suitable for a server environment, see [Introduction to Server-Based Timers](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).</span></span>  
  
## <a name="key-properties-methods-and-events"></a><span data-ttu-id="19622-106">Eventos, métodos e propriedades de chave</span><span class="sxs-lookup"><span data-stu-id="19622-106">Key Properties, Methods, and Events</span></span>  
 <span data-ttu-id="19622-107">O tamanho dos intervalos de é definido pelo <xref:System.Windows.Forms.Timer.Interval%2A> propriedade, cujo valor é em milissegundos.</span><span class="sxs-lookup"><span data-stu-id="19622-107">The length of the intervals is defined by the <xref:System.Windows.Forms.Timer.Interval%2A> property, whose value is in milliseconds.</span></span> <span data-ttu-id="19622-108">Quando o componente está habilitado, o <xref:System.Windows.Forms.Timer.Tick> é acionado cada intervalo.</span><span class="sxs-lookup"><span data-stu-id="19622-108">When the component is enabled, the <xref:System.Windows.Forms.Timer.Tick> event is raised every interval.</span></span> <span data-ttu-id="19622-109">Isso é onde você adicionaria o código a ser executado.</span><span class="sxs-lookup"><span data-stu-id="19622-109">This is where you would add code to be executed.</span></span> <span data-ttu-id="19622-110">Para obter mais informações, confira [Como: Executar procedimentos em intervalos definidos com o componente de temporizador do Windows Forms](run-procedures-at-set-intervals-with-wf-timer-component.md).</span><span class="sxs-lookup"><span data-stu-id="19622-110">For more information, see [How to: Run Procedures at Set Intervals with the Windows Forms Timer Component](run-procedures-at-set-intervals-with-wf-timer-component.md).</span></span> <span data-ttu-id="19622-111">Os métodos da chave de <xref:System.Windows.Forms.Timer> componente estão <xref:System.Windows.Forms.Timer.Start%2A> e <xref:System.Windows.Forms.Timer.Stop%2A>, qual ativar o temporizador e desativar.</span><span class="sxs-lookup"><span data-stu-id="19622-111">The key methods of the <xref:System.Windows.Forms.Timer> component are <xref:System.Windows.Forms.Timer.Start%2A> and <xref:System.Windows.Forms.Timer.Stop%2A>, which turn the timer on and off.</span></span> <span data-ttu-id="19622-112">Quando o temporizador é desligado, ele redefine; não é possível pausar um <xref:System.Windows.Forms.Timer> componente.</span><span class="sxs-lookup"><span data-stu-id="19622-112">When the timer is switched off, it resets; there is no way to pause a <xref:System.Windows.Forms.Timer> component.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19622-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="19622-113">See also</span></span>

- <xref:System.Windows.Forms.Timer>
- [<span data-ttu-id="19622-114">Componente Timer</span><span class="sxs-lookup"><span data-stu-id="19622-114">Timer Component</span></span>](timer-component-windows-forms.md)
- [<span data-ttu-id="19622-115">Limitações da propriedade de intervalo do componente temporizador dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="19622-115">Limitations of the Windows Forms Timer Component's Interval Property</span></span>](limitations-of-the-timer-component-interval-property.md)
