---
title: Limitações da propriedade de intervalo do componente de temporizador dos Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- timers [Windows Forms], event intervals
- Interval property [Windows Forms], limitations
- timers [Windows Forms], Windows-based
- Timer component [Windows Forms], limitations of Interval property
ms.assetid: 7e5fb513-77e7-4046-a8e8-aab94e61ca0f
ms.openlocfilehash: 54782c4e0460ba1ba9b8a870b8f60f08a76340b3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62012835"
---
# <a name="limitations-of-the-windows-forms-timer-components-interval-property"></a><span data-ttu-id="4e9a8-102">Limitações da propriedade de intervalo do componente de temporizador dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4e9a8-102">Limitations of the Windows Forms Timer Component's Interval Property</span></span>
<span data-ttu-id="4e9a8-103">Os formulários do Windows <xref:System.Windows.Forms.Timer> componente tem um <xref:System.Windows.Forms.Timer.Interval%2A> propriedade que especifica o número de milissegundos que passam entre um evento de temporizador e o próximo.</span><span class="sxs-lookup"><span data-stu-id="4e9a8-103">The Windows Forms <xref:System.Windows.Forms.Timer> component has an <xref:System.Windows.Forms.Timer.Interval%2A> property that specifies the number of milliseconds that pass between one timer event and the next.</span></span> <span data-ttu-id="4e9a8-104">A menos que o componente está desativado, um temporizador continua recebendo o <xref:System.Windows.Forms.Timer.Tick> evento em intervalos aproximadamente iguais de tempo.</span><span class="sxs-lookup"><span data-stu-id="4e9a8-104">Unless the component is disabled, a timer continues to receive the <xref:System.Windows.Forms.Timer.Tick> event at roughly equal intervals of time.</span></span>  
  
 <span data-ttu-id="4e9a8-105">Esse componente foi projetado para um ambiente do Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="4e9a8-105">This component is designed for a Windows Forms environment.</span></span> <span data-ttu-id="4e9a8-106">Se você precisar de um temporizador que seja adequado para um ambiente de servidor, consulte [Introdução a temporizadores baseados em servidor](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="4e9a8-106">If you need a timer that is suitable for a server environment, see [Introduction to Server-Based Timers](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).</span></span>  
  
## <a name="the-interval-property"></a><span data-ttu-id="4e9a8-107">A propriedade Interval</span><span class="sxs-lookup"><span data-stu-id="4e9a8-107">The Interval Property</span></span>  
 <span data-ttu-id="4e9a8-108">O <xref:System.Windows.Forms.Timer.Interval%2A> propriedade tem algumas limitações a serem consideradas quando você está programando um <xref:System.Windows.Forms.Timer> componente:</span><span class="sxs-lookup"><span data-stu-id="4e9a8-108">The <xref:System.Windows.Forms.Timer.Interval%2A> property has a few limitations to consider when you are programming a <xref:System.Windows.Forms.Timer> component:</span></span>  
  
- <span data-ttu-id="4e9a8-109">Se seu aplicativo ou outro aplicativo estiver criando grandes demandas no sistema — como loops longos, cálculos intensivos, unidade, rede ou acesso à porta — seu aplicativo poderá não receber eventos com a frequência do temporizador como o <xref:System.Windows.Forms.Timer.Interval%2A> propriedade especifica.</span><span class="sxs-lookup"><span data-stu-id="4e9a8-109">If your application or another application is making heavy demands on the system — such as long loops, intensive calculations, or drive, network, or port access — your application may not get timer events as often as the <xref:System.Windows.Forms.Timer.Interval%2A> property specifies.</span></span>  
  
- <span data-ttu-id="4e9a8-110">Não há garantia de que o intervalo decorra exatamente na hora.</span><span class="sxs-lookup"><span data-stu-id="4e9a8-110">The interval is not guaranteed to elapse exactly on time.</span></span> <span data-ttu-id="4e9a8-111">Para garantir a precisão, o temporizador deve verificar o relógio do sistema conforme necessário, em vez de tentar manter o controle de tempo acumulado internamente.</span><span class="sxs-lookup"><span data-stu-id="4e9a8-111">To ensure accuracy, the timer should check the system clock as needed, rather than try to keep track of accumulated time internally.</span></span>  
  
- <span data-ttu-id="4e9a8-112">A precisão do <xref:System.Windows.Forms.Timer.Interval%2A> propriedade é em milissegundos.</span><span class="sxs-lookup"><span data-stu-id="4e9a8-112">The precision of the <xref:System.Windows.Forms.Timer.Interval%2A> property is in milliseconds.</span></span> <span data-ttu-id="4e9a8-113">Alguns computadores fornecem um contador de alta resolução que tem uma resolução maior do que milissegundos.</span><span class="sxs-lookup"><span data-stu-id="4e9a8-113">Some computers provide a high-resolution counter that has a resolution higher than milliseconds.</span></span> <span data-ttu-id="4e9a8-114">A disponibilidade desse contador depende do hardware do processador do computador.</span><span class="sxs-lookup"><span data-stu-id="4e9a8-114">The availability of such a counter depends on the processor hardware of your computer.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="4e9a8-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4e9a8-115">See also</span></span>

- <xref:System.Windows.Forms.Timer>
- [<span data-ttu-id="4e9a8-116">Componente Timer</span><span class="sxs-lookup"><span data-stu-id="4e9a8-116">Timer Component</span></span>](timer-component-windows-forms.md)
- [<span data-ttu-id="4e9a8-117">Visão geral do componente de temporizador</span><span class="sxs-lookup"><span data-stu-id="4e9a8-117">Timer Component Overview</span></span>](timer-component-overview-windows-forms.md)
