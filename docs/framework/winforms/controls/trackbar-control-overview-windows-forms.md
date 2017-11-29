---
title: "Visão geral do controle TrackBar (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: TrackBar
helpviewer_keywords:
- sliders [Windows Forms], about sliders
- TrackBar control [Windows Forms], about TrackBar control
- slider controls [Windows Forms], about slider controls
ms.assetid: 95910ecb-8a4c-4776-89fa-206c89ed6973
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ccea982c45ab22a4b2ab81bc80c16dd472144bbe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="trackbar-control-overview-windows-forms"></a><span data-ttu-id="16cf7-102">Visão geral do controle TrackBar (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="16cf7-102">TrackBar Control Overview (Windows Forms)</span></span>
<span data-ttu-id="16cf7-103">Windows Forms <xref:System.Windows.Forms.TrackBar> controle (também chamado de controle "deslizante") é usado para navegar por uma grande quantidade de informações ou para ajustar visualmente uma configuração numérica.</span><span class="sxs-lookup"><span data-stu-id="16cf7-103">The Windows Forms <xref:System.Windows.Forms.TrackBar> control (also sometimes called a "slider" control) is used for navigating through a large amount of information or for visually adjusting a numeric setting.</span></span> <span data-ttu-id="16cf7-104">O <xref:System.Windows.Forms.TrackBar> controle tem duas partes: o thumb, também conhecido como um controle deslizante e as marcas de escala.</span><span class="sxs-lookup"><span data-stu-id="16cf7-104">The <xref:System.Windows.Forms.TrackBar> control has two parts: the thumb, also known as a slider, and the tick marks.</span></span> <span data-ttu-id="16cf7-105">O elevador é parte que pode ser ajustada.</span><span class="sxs-lookup"><span data-stu-id="16cf7-105">The thumb is the part that can be adjusted.</span></span> <span data-ttu-id="16cf7-106">Sua posição corresponde do <xref:System.Windows.Forms.TrackBar.Value%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="16cf7-106">Its position corresponds to the <xref:System.Windows.Forms.TrackBar.Value%2A> property.</span></span> <span data-ttu-id="16cf7-107">As marcas de escala são indicadores visuais espaçados em intervalos regulares.</span><span class="sxs-lookup"><span data-stu-id="16cf7-107">The tick marks are visual indicators that are spaced at regular intervals.</span></span> <span data-ttu-id="16cf7-108">A trackbar se move em incrementos especificados e pode ser alinhada horizontalmente ou verticalmente.</span><span class="sxs-lookup"><span data-stu-id="16cf7-108">The trackbar moves in increments that you specify and can be aligned horizontally or vertically.</span></span> <span data-ttu-id="16cf7-109">Por exemplo, é possível usar a trackbar para controlar a taxa de intermitência do cursor ou a velocidade do mouse em um sistema.</span><span class="sxs-lookup"><span data-stu-id="16cf7-109">For example, you might use the track bar to control the cursor blink rate or mouse speed for a system.</span></span>  
  
## <a name="key-properties"></a><span data-ttu-id="16cf7-110">Propriedades da chave</span><span class="sxs-lookup"><span data-stu-id="16cf7-110">Key Properties</span></span>  
 <span data-ttu-id="16cf7-111">Propriedades de chave do <xref:System.Windows.Forms.TrackBar> controle são <xref:System.Windows.Forms.TrackBar.Value%2A>, <xref:System.Windows.Forms.TrackBar.TickFrequency%2A>, <xref:System.Windows.Forms.TrackBar.Minimum%2A>, e <xref:System.Windows.Forms.TrackBar.Maximum%2A>.</span><span class="sxs-lookup"><span data-stu-id="16cf7-111">The key properties of the <xref:System.Windows.Forms.TrackBar> control are <xref:System.Windows.Forms.TrackBar.Value%2A>, <xref:System.Windows.Forms.TrackBar.TickFrequency%2A>, <xref:System.Windows.Forms.TrackBar.Minimum%2A>, and <xref:System.Windows.Forms.TrackBar.Maximum%2A>.</span></span> <span data-ttu-id="16cf7-112"><xref:System.Windows.Forms.TrackBar.TickFrequency%2A>é o espaçamento de tiques.</span><span class="sxs-lookup"><span data-stu-id="16cf7-112"><xref:System.Windows.Forms.TrackBar.TickFrequency%2A> is the spacing of the ticks.</span></span> <span data-ttu-id="16cf7-113"><xref:System.Windows.Forms.TrackBar.Minimum%2A>e <xref:System.Windows.Forms.TrackBar.Maximum%2A> são os valores menores e maiores que podem ser representados na barra de controle.</span><span class="sxs-lookup"><span data-stu-id="16cf7-113"><xref:System.Windows.Forms.TrackBar.Minimum%2A> and <xref:System.Windows.Forms.TrackBar.Maximum%2A> are the smallest and largest values that can be represented on the track bar.</span></span>  
  
 <span data-ttu-id="16cf7-114">Duas outras propriedades importantes forem <xref:System.Windows.Forms.TrackBar.SmallChange%2A> e <xref:System.Windows.Forms.TrackBar.LargeChange%2A>.</span><span class="sxs-lookup"><span data-stu-id="16cf7-114">Two other important properties are <xref:System.Windows.Forms.TrackBar.SmallChange%2A> and <xref:System.Windows.Forms.TrackBar.LargeChange%2A>.</span></span> <span data-ttu-id="16cf7-115">O valor de <xref:System.Windows.Forms.TrackBar.SmallChange%2A> propriedade é o número de posições de controle deslizante se move em resposta a ter a chave esquerda ou para a direita pressionada.</span><span class="sxs-lookup"><span data-stu-id="16cf7-115">The value of the <xref:System.Windows.Forms.TrackBar.SmallChange%2A> property is the number of positions the thumb moves in response to having the LEFT or RIGHT ARROW key pressed.</span></span> <span data-ttu-id="16cf7-116">O valor de <xref:System.Windows.Forms.TrackBar.LargeChange%2A> propriedade é o número de posições que o controle deslizante se move em resposta a ter a tecla PAGE UP ou PAGE DOWN pressionada ou em resposta a mouse clica na barra de controle em ambos os lados do controle deslizante.</span><span class="sxs-lookup"><span data-stu-id="16cf7-116">The value of the <xref:System.Windows.Forms.TrackBar.LargeChange%2A> property is the number of positions the thumb moves in response to having the PAGE UP or PAGE DOWN key pressed, or in response to mouse clicks on the track bar on either side of the thumb.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16cf7-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="16cf7-117">See Also</span></span>  
 <xref:System.Windows.Forms.TrackBar>  
 [<span data-ttu-id="16cf7-118">Controle TrackBar</span><span class="sxs-lookup"><span data-stu-id="16cf7-118">TrackBar Control</span></span>](../../../../docs/framework/winforms/controls/trackbar-control-windows-forms.md)
