---
title: Como posicionar um ToolTip
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolTip control [WPF], positioning
- positioning ToolTip controls [WPF]
ms.assetid: cddf3757-9e5f-4ce3-a6eb-44489cf3804a
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0e8345b74cf9269bca21e1e5698de974109c2aee
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-position-a-tooltip"></a><span data-ttu-id="e0fde-102">Como posicionar um ToolTip</span><span class="sxs-lookup"><span data-stu-id="e0fde-102">How to: Position a ToolTip</span></span>
<span data-ttu-id="e0fde-103">Este exemplo mostra como especificar a posição de uma dica de ferramenta na tela.</span><span class="sxs-lookup"><span data-stu-id="e0fde-103">This example shows how to specify the position of a tooltip on the screen.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e0fde-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e0fde-104">Example</span></span>  
 <span data-ttu-id="e0fde-105">Você pode posicionar um tooltip usando um conjunto de cinco propriedades que são definidas em ambas as <xref:System.Windows.Controls.ToolTip> e <xref:System.Windows.Controls.ToolTipService> classes.</span><span class="sxs-lookup"><span data-stu-id="e0fde-105">You can position a tooltip by using a set of five properties that are defined in both the <xref:System.Windows.Controls.ToolTip> and <xref:System.Windows.Controls.ToolTipService> classes.</span></span> <span data-ttu-id="e0fde-106">A tabela a seguir mostra esses dois conjuntos de cinco propriedades e fornece links para a documentação de referência de acordo com a classe.</span><span class="sxs-lookup"><span data-stu-id="e0fde-106">The following table shows these two sets of five properties and provides links to their reference documentation according to class.</span></span>  
  
### <a name="corresponding-tooltip-properties-according-to-class"></a><span data-ttu-id="e0fde-107">Propriedades de dica de ferramentas correspondentes de acordo com a classe</span><span class="sxs-lookup"><span data-stu-id="e0fde-107">Corresponding tooltip properties according to class</span></span>  
  
|<span data-ttu-id="e0fde-108"><xref:System.Windows.Controls.ToolTip?displayProperty=nameWithType>Propriedades de classe</span><span class="sxs-lookup"><span data-stu-id="e0fde-108"><xref:System.Windows.Controls.ToolTip?displayProperty=nameWithType> class properties</span></span>|<span data-ttu-id="e0fde-109"><xref:System.Windows.Controls.ToolTipService?displayProperty=nameWithType>Propriedades de classe</span><span class="sxs-lookup"><span data-stu-id="e0fde-109"><xref:System.Windows.Controls.ToolTipService?displayProperty=nameWithType> class properties</span></span>|  
|--------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Windows.Controls.ToolTip.Placement%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.Placement%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.PlacementTarget%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.PlacementTarget%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.PlacementRectangle%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.PlacementRectangle%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.HorizontalOffset%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.HorizontalOffset%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.VerticalOffset%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.VerticalOffset%2A?displayProperty=nameWithType>|  
  
 <span data-ttu-id="e0fde-110">Se você definir o conteúdo de uma dica de ferramenta usando um <xref:System.Windows.Controls.ToolTip> do objeto, você pode usar as propriedades de qualquer classe; no entanto, o <xref:System.Windows.Controls.ToolTipService> propriedades têm precedência.</span><span class="sxs-lookup"><span data-stu-id="e0fde-110">If you define the contents of a tooltip by using a <xref:System.Windows.Controls.ToolTip> object, you can use the properties of either class; however, the <xref:System.Windows.Controls.ToolTipService> properties take precedence.</span></span> <span data-ttu-id="e0fde-111">Use o <xref:System.Windows.Controls.ToolTipService> propriedades de dicas de ferramenta que não são definidas como <xref:System.Windows.Controls.ToolTip> objetos.</span><span class="sxs-lookup"><span data-stu-id="e0fde-111">Use the <xref:System.Windows.Controls.ToolTipService> properties for tooltips that are not defined as <xref:System.Windows.Controls.ToolTip> objects.</span></span>  
  
 <span data-ttu-id="e0fde-112">As ilustrações a seguir mostram como posicionar uma dica de ferramenta usando essas propriedades.</span><span class="sxs-lookup"><span data-stu-id="e0fde-112">The following illustrations show how to position a tooltip by using these properties.</span></span> <span data-ttu-id="e0fde-113">Embora, o [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] exemplos estas ilustrações mostram como definir as propriedades que são definidas pelo <xref:System.Windows.Controls.ToolTip> classe, as propriedades correspondentes do <xref:System.Windows.Controls.ToolTipService> classe seguem as mesmas regras de layout.</span><span class="sxs-lookup"><span data-stu-id="e0fde-113">Although, the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] examples in these illustrations show how to set the properties that are defined by the <xref:System.Windows.Controls.ToolTip> class, the corresponding properties of the <xref:System.Windows.Controls.ToolTipService> class follow the same layout rules.</span></span> <span data-ttu-id="e0fde-114">Para obter mais informações sobre os possíveis valores para a propriedade de Posicionamento, consulte [Comportamento de posicionamento de pop-up](../../../../docs/framework/wpf/controls/popup-placement-behavior.md).</span><span class="sxs-lookup"><span data-stu-id="e0fde-114">For more information about the possible values for the Placement property, see [Popup Placement Behavior](../../../../docs/framework/wpf/controls/popup-placement-behavior.md).</span></span>  
  
 <span data-ttu-id="e0fde-115">![Posicionamento de dica de ferramenta](../../../../docs/framework/wpf/controls/media/tooltipplacement.png "ToolTipPlacement")</span><span class="sxs-lookup"><span data-stu-id="e0fde-115">![ToolTip placement](../../../../docs/framework/wpf/controls/media/tooltipplacement.png "ToolTipPlacement")</span></span>  
<span data-ttu-id="e0fde-116">Posicionamento de ToolTip usando a propriedade de Posicionamento</span><span class="sxs-lookup"><span data-stu-id="e0fde-116">ToolTip placement by using the Placement property</span></span>  
  
 <span data-ttu-id="e0fde-117">![Colocando uma dica de ferramenta usando um retângulo de posicionamento](../../../../docs/framework/wpf/controls/media/tooltipplacementrectangle.png "ToolTipPlacementRectangle")</span><span class="sxs-lookup"><span data-stu-id="e0fde-117">![Placing a ToolTip by using a placement rectangle](../../../../docs/framework/wpf/controls/media/tooltipplacementrectangle.png "ToolTipPlacementRectangle")</span></span>  
<span data-ttu-id="e0fde-118">Posicionamento de ToolTip usando as propriedades Placement e PlacementRectangle</span><span class="sxs-lookup"><span data-stu-id="e0fde-118">ToolTip placement by using the Placement and PlacementRectangle properties</span></span>  
  
 <span data-ttu-id="e0fde-119">![Diagrama de posicionamento de dica de ferramenta](../../../../docs/framework/wpf/controls/media/tooltipplacementprhv.png "ToolTipPlacementPRHV")</span><span class="sxs-lookup"><span data-stu-id="e0fde-119">![ToolTip placement diagram](../../../../docs/framework/wpf/controls/media/tooltipplacementprhv.png "ToolTipPlacementPRHV")</span></span>  
<span data-ttu-id="e0fde-120">Posicionamento de ToolTip usando as propriedades Placement, PlacementRectangle e Offset</span><span class="sxs-lookup"><span data-stu-id="e0fde-120">ToolTip placement by using the Placement, PlacementRectangle, and Offset properties</span></span>  
  
 <span data-ttu-id="e0fde-121">O exemplo a seguir mostra como usar o <xref:System.Windows.Controls.ToolTip> propriedades para especificar a posição de um tooltip cujo conteúdo é um <xref:System.Windows.Controls.ToolTip> objeto.</span><span class="sxs-lookup"><span data-stu-id="e0fde-121">The following example shows how to use the <xref:System.Windows.Controls.ToolTip> properties to specify the position of a tooltip whose content is a <xref:System.Windows.Controls.ToolTip> object.</span></span>  
  
 [!code-xaml[ToolTipService#ToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#tooltip)]  
  
 [!code-csharp[ToolTipService#ToolTipCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml.cs#tooltipcode)]
 [!code-vb[ToolTipService#ToolTipCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ToolTipService/visualbasic/pane1.xaml.vb#tooltipcode)]  
  
 <span data-ttu-id="e0fde-122">O exemplo a seguir mostra como usar o <xref:System.Windows.Controls.ToolTipService> propriedades para especificar a posição de um tooltip cujo conteúdo não é um <xref:System.Windows.Controls.ToolTip> objeto.</span><span class="sxs-lookup"><span data-stu-id="e0fde-122">The following example shows how to use the <xref:System.Windows.Controls.ToolTipService> properties to specify the position of a tooltip whose content is not a <xref:System.Windows.Controls.ToolTip> object.</span></span>  
  
 [!code-xaml[ToolTipService#NoToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#notooltip)]  
  
 [!code-csharp[ToolTipService#NoToolTipCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml.cs#notooltipcode)]
 [!code-vb[ToolTipService#NoToolTipCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ToolTipService/visualbasic/pane1.xaml.vb#notooltipcode)]  
  
## <a name="see-also"></a><span data-ttu-id="e0fde-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e0fde-123">See Also</span></span>  
 <xref:System.Windows.Controls.ToolTip>  
 <xref:System.Windows.Controls.ToolTipService>  
 [<span data-ttu-id="e0fde-124">Tópicos explicativos</span><span class="sxs-lookup"><span data-stu-id="e0fde-124">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/tooltip-how-to-topics.md)  
 [<span data-ttu-id="e0fde-125">Visão geral de ToolTip</span><span class="sxs-lookup"><span data-stu-id="e0fde-125">ToolTip Overview</span></span>](../../../../docs/framework/wpf/controls/tooltip-overview.md)  
 [<span data-ttu-id="e0fde-126">Usar o ContextMenuService e o ToolTipService</span><span class="sxs-lookup"><span data-stu-id="e0fde-126">Use the ContextMenuService and ToolTipService</span></span>](http://msdn.microsoft.com/en-us/809b0e9c-d612-4cda-b8af-1a698c68f4d1)
