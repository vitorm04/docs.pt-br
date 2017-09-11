---
title: "Como: exibir cabeçalhos de Item em um controle DataRepeater (Visual Studio) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- DataRepeater, item headers
- DataRepeater, selection indicators
ms.assetid: 37321447-0ffa-43e1-bdc9-0480e392b90f
caps.latest.revision: 7
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 090296adbdc291a65e70dee64ab8b207575ca69d
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-display-item-headers-in-a-datarepeater-control-visual-studio"></a><span data-ttu-id="1dee3-102">Como exibir cabeçalhos de item em um controle DataRepeater (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="1dee3-102">How to: Display Item Headers in a DataRepeater Control (Visual Studio)</span></span>
<span data-ttu-id="1dee3-103">Cabeçalho do item em uma <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>controle fornece um indicador visual quando um <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>é selecionado.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></span><span class="sxs-lookup"><span data-stu-id="1dee3-103">The item header in a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control provides a visual indicator when a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> is selected.</span></span> <span data-ttu-id="1dee3-104">Quando o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A>estiver definida como <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles>(o padrão), o cabeçalho do item é exibido à esquerda de cada item.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A></span><span class="sxs-lookup"><span data-stu-id="1dee3-104">When the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> property is set to <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles> (the default), the item header is displayed to the left of each item.</span></span> <span data-ttu-id="1dee3-105">Quando o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A>estiver definida como <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles>, o cabeçalho do item é exibido na parte superior de cada item.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A></span><span class="sxs-lookup"><span data-stu-id="1dee3-105">When the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> property is set to <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles>, the item header is displayed at the top of each item.</span></span>  
  
 <span data-ttu-id="1dee3-106">Quando o primeiro é selecionada, o cabeçalho do item é exibido na cor que é especificada pelo <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A>propriedade e um ícone de seta branca é exibida.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A></span><span class="sxs-lookup"><span data-stu-id="1dee3-106">When it is first selected, the item header is displayed in the color that is specified by the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> property, and a white arrow icon is displayed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1dee3-107">Se você definir o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A>para <xref:System.Drawing.Color.White%2A>, o símbolo de seleção não ficará visível quando o item for selecionado pela primeira vez.</xref:System.Drawing.Color.White%2A> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A></span><span class="sxs-lookup"><span data-stu-id="1dee3-107">If you set the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> to <xref:System.Drawing.Color.White%2A>, the selection symbol will not be visible when the item is first selected.</span></span>  
  
 <span data-ttu-id="1dee3-108">Quando um campo o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>tem o foco, a cor da cabeçalho de alterações de item para o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A>plano de fundo de cor e as alterações do ícone de seta para preto.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem></span><span class="sxs-lookup"><span data-stu-id="1dee3-108">When a field in the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> has focus, the color of the item header changes to the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> background color and the arrow icon changes to black.</span></span> <span data-ttu-id="1dee3-109">Se os dados são alterados, um símbolo de lápis é exibido no cabeçalho de item.</span><span class="sxs-lookup"><span data-stu-id="1dee3-109">If data is changed, a pencil symbol is displayed in the item header.</span></span>  
  
 <span data-ttu-id="1dee3-110">A largura padrão (ou altura quando o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A>estiver definida como <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles>) do item de cabeçalho é 15 pixels.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A></span><span class="sxs-lookup"><span data-stu-id="1dee3-110">The default width (or height when the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> property is set to <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles>) of the item header is 15 pixels.</span></span> <span data-ttu-id="1dee3-111">Você pode alterar a largura, definindo o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A>propriedade.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A></span><span class="sxs-lookup"><span data-stu-id="1dee3-111">You can change the width by setting the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A> property.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1dee3-112">Se o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A>propriedade é definida como um valor que seja menor do que 11, os símbolos de indicador no cabeçalho do item não serão exibidos.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A></span><span class="sxs-lookup"><span data-stu-id="1dee3-112">If the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A> property is set to a value that is less than 11, the indicator symbols in the item header will not be displayed.</span></span>  
  
 <span data-ttu-id="1dee3-113">Você pode ocultar os cabeçalhos de item, definindo a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderVisible%2A>propriedade **False**.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderVisible%2A></span><span class="sxs-lookup"><span data-stu-id="1dee3-113">You can hide the item headers by setting the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderVisible%2A> property to **False**.</span></span> <span data-ttu-id="1dee3-114">Quando <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderVisible%2A>é definido como **False**, a única indicação de que um item é selecionado é uma linha pontilhada em torno do perímetro de <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderVisible%2A></span><span class="sxs-lookup"><span data-stu-id="1dee3-114">When <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderVisible%2A> is set to **False**, the only indication that an item is selected is a dotted line around the perimeter of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1dee3-115">Você também pode fornecer seu próprio indicador de seleção monitorando o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem.IsCurrent%2A>propriedade do <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>no <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem>eventos do <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>controle.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem.IsCurrent%2A></span><span class="sxs-lookup"><span data-stu-id="1dee3-115">You can also provide your own selection indicator by monitoring the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem.IsCurrent%2A> property of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> in the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> event of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span> <span data-ttu-id="1dee3-116">Para obter mais informações, consulte <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem.IsCurrent%2A>.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem.IsCurrent%2A></span><span class="sxs-lookup"><span data-stu-id="1dee3-116">For more information, see <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem.IsCurrent%2A>.</span></span>  
  
### <a name="to-change-the-appearance-of-item-headers"></a><span data-ttu-id="1dee3-117">Para alterar a aparência de cabeçalhos de item</span><span class="sxs-lookup"><span data-stu-id="1dee3-117">To change the appearance of item headers</span></span>  
  
1.  <span data-ttu-id="1dee3-118">No Windows Forms Designer, selecione a região inferior do <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>controle.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></span><span class="sxs-lookup"><span data-stu-id="1dee3-118">In the Windows Forms Designer, select the lower region of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="1dee3-119">Você deve selecionar a região inferior do controle.</span><span class="sxs-lookup"><span data-stu-id="1dee3-119">You must select the lower region of the control.</span></span> <span data-ttu-id="1dee3-120">Se você selecionar a seção de modelos de item, um conjunto diferente de propriedades será exibida na janela Propriedades.</span><span class="sxs-lookup"><span data-stu-id="1dee3-120">If you select the item template section, a different set of properties will appear in the Properties window.</span></span>  
  
2.  <span data-ttu-id="1dee3-121">Na janela Propriedades, use o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A>propriedade para alterar a cor dos cabeçalhos de item.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A></span><span class="sxs-lookup"><span data-stu-id="1dee3-121">In the Properties window, use the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> property to change the color of the item headers.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="1dee3-122">Se você definir o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A>para <xref:System.Drawing.Color.White%2A>, o símbolo de seleção não ficará visível quando o item for selecionado pela primeira vez.</xref:System.Drawing.Color.White%2A> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A></span><span class="sxs-lookup"><span data-stu-id="1dee3-122">If you set the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> to <xref:System.Drawing.Color.White%2A>, the selection symbol will not be visible when the item is first selected.</span></span>  
  
3.  <span data-ttu-id="1dee3-123">Use o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A>propriedade para alterar a largura (ou altura) dos cabeçalhos de item.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A></span><span class="sxs-lookup"><span data-stu-id="1dee3-123">Use the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A> property to change the width (or height) of the item headers.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="1dee3-124">Se o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A>propriedade é definida como um valor que seja menor do que 11, os símbolos de indicador no cabeçalho do item não serão exibidos.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A></span><span class="sxs-lookup"><span data-stu-id="1dee3-124">If the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A> property is set to a value that is less than 11, the indicator symbols in the item header will not be displayed.</span></span>  
  
### <a name="to-hide-item-headers"></a><span data-ttu-id="1dee3-125">Para ocultar cabeçalhos de item</span><span class="sxs-lookup"><span data-stu-id="1dee3-125">To hide item headers</span></span>  
  
1.  <span data-ttu-id="1dee3-126">No Windows Forms Designer, selecione a região inferior do <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>controle.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></span><span class="sxs-lookup"><span data-stu-id="1dee3-126">In the Windows Forms Designer, select the lower region of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="1dee3-127">Você deve selecionar a região inferior do controle.</span><span class="sxs-lookup"><span data-stu-id="1dee3-127">You must select the lower region of the control.</span></span> <span data-ttu-id="1dee3-128">Se você selecionar a seção de modelos de item, um conjunto diferente de propriedades será exibida na janela Propriedades.</span><span class="sxs-lookup"><span data-stu-id="1dee3-128">If you select the item template section, a different set of properties will appear in the Properties window.</span></span>  
  
2.  <span data-ttu-id="1dee3-129">Na janela Propriedades, defina o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderVisible%2A>propriedade **False**.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderVisible%2A></span><span class="sxs-lookup"><span data-stu-id="1dee3-129">In the Properties window, set the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderVisible%2A> property to **False**.</span></span>  
  
     <span data-ttu-id="1dee3-130">Quando um item de <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>é selecionada, a única indicação será uma linha pontilhada em torno do perímetro de <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></span><span class="sxs-lookup"><span data-stu-id="1dee3-130">When an item in the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> is selected, the only indication will be a dotted line around the perimeter of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1dee3-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1dee3-131">See Also</span></span>  
 <span data-ttu-id="1dee3-132"><xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></span><span class="sxs-lookup"><span data-stu-id="1dee3-132"><xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></span></span>   
<span data-ttu-id="1dee3-133"> [Introdução ao controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md) </span><span class="sxs-lookup"><span data-stu-id="1dee3-133"> [Introduction to the DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md) </span></span>  
<span data-ttu-id="1dee3-134"> [Como: alterar a aparência de um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md) </span><span class="sxs-lookup"><span data-stu-id="1dee3-134"> [How to: Change the Appearance of a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md) </span></span>  
<span data-ttu-id="1dee3-135"> [Como: alterar o Layout de um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-layout-of-a-datarepeater-control-visual-studio.md) </span><span class="sxs-lookup"><span data-stu-id="1dee3-135"> [How to: Change the Layout of a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-layout-of-a-datarepeater-control-visual-studio.md) </span></span>  
<span data-ttu-id="1dee3-136"> [Solução de problemas do controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)</span><span class="sxs-lookup"><span data-stu-id="1dee3-136"> [Troubleshooting the DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)</span></span>
