---
title: 'Como: Posicionar um ToolTip'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolTip control [WPF], positioning
- positioning ToolTip controls [WPF]
ms.assetid: cddf3757-9e5f-4ce3-a6eb-44489cf3804a
ms.openlocfilehash: 403b070e782a6f243fd5a420e569daa02044dbb1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54727697"
---
# <a name="how-to-position-a-tooltip"></a><span data-ttu-id="ff8c7-102">Como: Posicionar um ToolTip</span><span class="sxs-lookup"><span data-stu-id="ff8c7-102">How to: Position a ToolTip</span></span>
<span data-ttu-id="ff8c7-103">Este exemplo mostra como especificar a posição de uma dica de ferramenta na tela.</span><span class="sxs-lookup"><span data-stu-id="ff8c7-103">This example shows how to specify the position of a tooltip on the screen.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ff8c7-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ff8c7-104">Example</span></span>  
 <span data-ttu-id="ff8c7-105">Você pode posicionar um tooltip usando um conjunto de cinco propriedades que são definidas em ambas as <xref:System.Windows.Controls.ToolTip> e <xref:System.Windows.Controls.ToolTipService> classes.</span><span class="sxs-lookup"><span data-stu-id="ff8c7-105">You can position a tooltip by using a set of five properties that are defined in both the <xref:System.Windows.Controls.ToolTip> and <xref:System.Windows.Controls.ToolTipService> classes.</span></span> <span data-ttu-id="ff8c7-106">A tabela a seguir mostra esses dois conjuntos de cinco propriedades e fornece links para a documentação de referência de acordo com a classe.</span><span class="sxs-lookup"><span data-stu-id="ff8c7-106">The following table shows these two sets of five properties and provides links to their reference documentation according to class.</span></span>  
  
### <a name="corresponding-tooltip-properties-according-to-class"></a><span data-ttu-id="ff8c7-107">Propriedades de dica de ferramentas correspondentes de acordo com a classe</span><span class="sxs-lookup"><span data-stu-id="ff8c7-107">Corresponding tooltip properties according to class</span></span>  
  
|<span data-ttu-id="ff8c7-108"><xref:System.Windows.Controls.ToolTip?displayProperty=nameWithType> Propriedades de classe</span><span class="sxs-lookup"><span data-stu-id="ff8c7-108"><xref:System.Windows.Controls.ToolTip?displayProperty=nameWithType> class properties</span></span>|<span data-ttu-id="ff8c7-109"><xref:System.Windows.Controls.ToolTipService?displayProperty=nameWithType> Propriedades de classe</span><span class="sxs-lookup"><span data-stu-id="ff8c7-109"><xref:System.Windows.Controls.ToolTipService?displayProperty=nameWithType> class properties</span></span>|  
|--------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Windows.Controls.ToolTip.Placement%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.Placement%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.PlacementTarget%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.PlacementTarget%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.PlacementRectangle%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.PlacementRectangle%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.HorizontalOffset%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.HorizontalOffset%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.VerticalOffset%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.VerticalOffset%2A?displayProperty=nameWithType>|  
  
 <span data-ttu-id="ff8c7-110">Se você definir o conteúdo de uma dica de ferramenta usando um <xref:System.Windows.Controls.ToolTip> objeto, você pode usar as propriedades de qualquer classe; no entanto, o <xref:System.Windows.Controls.ToolTipService> propriedades têm precedência.</span><span class="sxs-lookup"><span data-stu-id="ff8c7-110">If you define the contents of a tooltip by using a <xref:System.Windows.Controls.ToolTip> object, you can use the properties of either class; however, the <xref:System.Windows.Controls.ToolTipService> properties take precedence.</span></span> <span data-ttu-id="ff8c7-111">Use o <xref:System.Windows.Controls.ToolTipService> propriedades de dicas de ferramenta que não são definidas como <xref:System.Windows.Controls.ToolTip> objetos.</span><span class="sxs-lookup"><span data-stu-id="ff8c7-111">Use the <xref:System.Windows.Controls.ToolTipService> properties for tooltips that are not defined as <xref:System.Windows.Controls.ToolTip> objects.</span></span>  
  
 <span data-ttu-id="ff8c7-112">As ilustrações a seguir mostram como posicionar uma dica de ferramenta usando essas propriedades.</span><span class="sxs-lookup"><span data-stu-id="ff8c7-112">The following illustrations show how to position a tooltip by using these properties.</span></span> <span data-ttu-id="ff8c7-113">Embora, a [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] exemplos nessas ilustrações mostram como definir as propriedades que são definidas pela <xref:System.Windows.Controls.ToolTip> classe, as propriedades correspondentes do <xref:System.Windows.Controls.ToolTipService> classe seguem as mesmas regras de layout.</span><span class="sxs-lookup"><span data-stu-id="ff8c7-113">Although, the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] examples in these illustrations show how to set the properties that are defined by the <xref:System.Windows.Controls.ToolTip> class, the corresponding properties of the <xref:System.Windows.Controls.ToolTipService> class follow the same layout rules.</span></span> <span data-ttu-id="ff8c7-114">Para obter mais informações sobre os possíveis valores para a propriedade de Posicionamento, consulte [Comportamento de posicionamento de pop-up](../../../../docs/framework/wpf/controls/popup-placement-behavior.md).</span><span class="sxs-lookup"><span data-stu-id="ff8c7-114">For more information about the possible values for the Placement property, see [Popup Placement Behavior](../../../../docs/framework/wpf/controls/popup-placement-behavior.md).</span></span>  
  
 <span data-ttu-id="ff8c7-115">![Posicionamento de ToolTip](../../../../docs/framework/wpf/controls/media/tooltipplacement.png "ToolTipPlacement")</span><span class="sxs-lookup"><span data-stu-id="ff8c7-115">![ToolTip placement](../../../../docs/framework/wpf/controls/media/tooltipplacement.png "ToolTipPlacement")</span></span>  
<span data-ttu-id="ff8c7-116">Posicionamento de ToolTip usando a propriedade de Posicionamento</span><span class="sxs-lookup"><span data-stu-id="ff8c7-116">ToolTip placement by using the Placement property</span></span>  
  
 <span data-ttu-id="ff8c7-117">![Colocando uma dica de ferramenta usando um retângulo de posicionamento](../../../../docs/framework/wpf/controls/media/tooltipplacementrectangle.png "ToolTipPlacementRectangle")</span><span class="sxs-lookup"><span data-stu-id="ff8c7-117">![Placing a ToolTip by using a placement rectangle](../../../../docs/framework/wpf/controls/media/tooltipplacementrectangle.png "ToolTipPlacementRectangle")</span></span>  
<span data-ttu-id="ff8c7-118">Posicionamento de ToolTip usando as propriedades Placement e PlacementRectangle</span><span class="sxs-lookup"><span data-stu-id="ff8c7-118">ToolTip placement by using the Placement and PlacementRectangle properties</span></span>  
  
 <span data-ttu-id="ff8c7-119">![Diagrama de posicionamento da dica de ferramenta](../../../../docs/framework/wpf/controls/media/tooltipplacementprhv.png "ToolTipPlacementPRHV")</span><span class="sxs-lookup"><span data-stu-id="ff8c7-119">![ToolTip placement diagram](../../../../docs/framework/wpf/controls/media/tooltipplacementprhv.png "ToolTipPlacementPRHV")</span></span>  
<span data-ttu-id="ff8c7-120">Posicionamento de ToolTip usando as propriedades Placement, PlacementRectangle e Offset</span><span class="sxs-lookup"><span data-stu-id="ff8c7-120">ToolTip placement by using the Placement, PlacementRectangle, and Offset properties</span></span>  
  
 <span data-ttu-id="ff8c7-121">O exemplo a seguir mostra como usar o <xref:System.Windows.Controls.ToolTip> propriedades para especificar a posição de uma dica de ferramenta cujo conteúdo é um <xref:System.Windows.Controls.ToolTip> objeto.</span><span class="sxs-lookup"><span data-stu-id="ff8c7-121">The following example shows how to use the <xref:System.Windows.Controls.ToolTip> properties to specify the position of a tooltip whose content is a <xref:System.Windows.Controls.ToolTip> object.</span></span>  
  
 [!code-xaml[ToolTipService#ToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#tooltip)]  
  
 [!code-csharp[ToolTipService#ToolTipCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml.cs#tooltipcode)]
 [!code-vb[ToolTipService#ToolTipCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ToolTipService/visualbasic/pane1.xaml.vb#tooltipcode)]  
  
 <span data-ttu-id="ff8c7-122">O exemplo a seguir mostra como usar o <xref:System.Windows.Controls.ToolTipService> propriedades para especificar a posição de uma dica de ferramenta cujo conteúdo não é um <xref:System.Windows.Controls.ToolTip> objeto.</span><span class="sxs-lookup"><span data-stu-id="ff8c7-122">The following example shows how to use the <xref:System.Windows.Controls.ToolTipService> properties to specify the position of a tooltip whose content is not a <xref:System.Windows.Controls.ToolTip> object.</span></span>  
  
 [!code-xaml[ToolTipService#NoToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#notooltip)]  
  
 [!code-csharp[ToolTipService#NoToolTipCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml.cs#notooltipcode)]
 [!code-vb[ToolTipService#NoToolTipCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ToolTipService/visualbasic/pane1.xaml.vb#notooltipcode)]  
  
## <a name="see-also"></a><span data-ttu-id="ff8c7-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ff8c7-123">See also</span></span>
- <xref:System.Windows.Controls.ToolTip>
- <xref:System.Windows.Controls.ToolTipService>
- [<span data-ttu-id="ff8c7-124">Tópicos de instruções</span><span class="sxs-lookup"><span data-stu-id="ff8c7-124">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/tooltip-how-to-topics.md)
- [<span data-ttu-id="ff8c7-125">Visão geral de ToolTip</span><span class="sxs-lookup"><span data-stu-id="ff8c7-125">ToolTip Overview</span></span>](../../../../docs/framework/wpf/controls/tooltip-overview.md)
- [<span data-ttu-id="ff8c7-126">Usar o ContextMenuService e o ToolTipService</span><span class="sxs-lookup"><span data-stu-id="ff8c7-126">Use the ContextMenuService and ToolTipService</span></span>](https://msdn.microsoft.com/library/809b0e9c-d612-4cda-b8af-1a698c68f4d1)
