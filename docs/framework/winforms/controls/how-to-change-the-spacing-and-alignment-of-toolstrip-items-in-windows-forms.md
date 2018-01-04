---
title: "Como alterar o espaçamento e o alinhamento de itens ToolStrip nos Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStrip control [Windows Forms], aligning items
- examples [Windows Forms], toolbars
- toolbars [Windows Forms], aligning items
ms.assetid: cd483466-0f49-43df-addf-e2b5fcd64027
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 58cad83b7253b71363f9ccf7fbda74e03803f381
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-change-the-spacing-and-alignment-of-toolstrip-items-in-windows-forms"></a><span data-ttu-id="76ad6-102">Como alterar o espaçamento e o alinhamento de itens ToolStrip nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="76ad6-102">How to: Change the Spacing and Alignment of ToolStrip Items in Windows Forms</span></span>
<span data-ttu-id="76ad6-103">O <xref:System.Windows.Forms.ToolStrip> totalmente o controle oferece suporte para recursos de layout, como dimensionamento, o espaçamento de <xref:System.Windows.Forms.ToolStripItem> controles relativos uns aos outros, a organização dos controles no <xref:System.Windows.Forms.ToolStrip>e o espaçamento de controles relativo a <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="76ad6-103">The <xref:System.Windows.Forms.ToolStrip> control fully supports layout features such as sizing, the spacing of <xref:System.Windows.Forms.ToolStripItem> controls relative to each other, the arrangement of controls on the <xref:System.Windows.Forms.ToolStrip>, and the spacing of controls relative to the <xref:System.Windows.Forms.ToolStrip>.</span></span>  
  
 <span data-ttu-id="76ad6-104">Porque o valor padrão a <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> é de propriedade `true`, controles são dimensionados automaticamente a menos que você defina o <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> propriedade `false`.</span><span class="sxs-lookup"><span data-stu-id="76ad6-104">Because the default value of the <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> property is `true`, controls are sized automatically unless you set the <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> property to `false`.</span></span>  
  
### <a name="to-manually-size-a-toolstripitem"></a><span data-ttu-id="76ad6-105">Para dimensionar manualmente um ToolStripItem</span><span class="sxs-lookup"><span data-stu-id="76ad6-105">To manually size a ToolStripItem</span></span>  
  
1.  <span data-ttu-id="76ad6-106">Definir o <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> propriedade `false` para o controle associado.</span><span class="sxs-lookup"><span data-stu-id="76ad6-106">Set the <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> property to `false` for the associated control.</span></span>  
  
    ```vb  
    ToolStripButton1.AutoSize = False  
    ```  
  
    ```csharp  
    toolStripButton1.AutoSize = false;  
    ```  
  
2.  <span data-ttu-id="76ad6-107">Definir o <xref:System.Windows.Forms.ToolStripItem.Size%2A> da maneira desejada para o associado de propriedade <xref:System.Windows.Forms.ToolStripItem>.</span><span class="sxs-lookup"><span data-stu-id="76ad6-107">Set the <xref:System.Windows.Forms.ToolStripItem.Size%2A> property the way you want for the associated <xref:System.Windows.Forms.ToolStripItem>.</span></span>  
  
### <a name="to-set-the-spacing-of-a-toolstripitem"></a><span data-ttu-id="76ad6-108">Para definir o espaçamento de um ToolStripItem</span><span class="sxs-lookup"><span data-stu-id="76ad6-108">To set the spacing of a ToolStripItem</span></span>  
  
1.  <span data-ttu-id="76ad6-109">Insira os valores desejados, em pixels, do <xref:System.Windows.Forms.ToolStripItem.Margin%2A> propriedade do controle associado.</span><span class="sxs-lookup"><span data-stu-id="76ad6-109">Insert the desired values, in pixels, into the <xref:System.Windows.Forms.ToolStripItem.Margin%2A> property of the associated control.</span></span>  
  
     <span data-ttu-id="76ad6-110">Os valores de <xref:System.Windows.Forms.ToolStripItem.Margin%2A> propriedade especifica o espaçamento entre o item e itens adjacentes nesta ordem: esquerda, superior, direita e inferior.</span><span class="sxs-lookup"><span data-stu-id="76ad6-110">The values of the <xref:System.Windows.Forms.ToolStripItem.Margin%2A> property specify the spacing between the item and adjacent items in this order: Left, Top, Right, and Bottom.</span></span>  
  
    ```vb  
    ToolStripTextBox1.Margin = New System.Windows.Forms.Padding _  
        (3, 0, 3, 0)  
    ```  
  
    ```csharp  
    toolStripTextBox1.Margin = new System.Windows.Forms.Padding   
        (3, 0, 3, 0);  
    ```  
  
### <a name="to-align-a-toolstripitem-to-the-right-side-of-the-toolstrip"></a><span data-ttu-id="76ad6-111">Para alinhar um ToolStripItem à direita de ToolStrip</span><span class="sxs-lookup"><span data-stu-id="76ad6-111">To align a ToolStripItem to the right side of the ToolStrip</span></span>  
  
1.  <span data-ttu-id="76ad6-112">Definir o <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> propriedade <xref:System.Windows.Forms.ToolStripItemAlignment.Right> para o controle associado.</span><span class="sxs-lookup"><span data-stu-id="76ad6-112">Set the <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> property to <xref:System.Windows.Forms.ToolStripItemAlignment.Right> for the associated control.</span></span> <span data-ttu-id="76ad6-113">Por padrão, <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> é definido como <xref:System.Windows.Forms.ToolStripItemAlignment.Left>, que alinha os controles para o lado esquerdo do <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="76ad6-113">By default, <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> is set to <xref:System.Windows.Forms.ToolStripItemAlignment.Left>, which aligns controls to the left side of the <xref:System.Windows.Forms.ToolStrip>.</span></span>  
  
    ```vb  
    ToolStripSplitButton1.Alignment = _  
        System.Windows.Forms.ToolStripItemAlignment.Right  
    ```  
  
    ```csharp  
    toolStripSplitButton1.Alignment =   
        System.Windows.Forms.ToolStripItemAlignment.Right;  
    ```  
  
### <a name="to-arrange-toolstrip-items-on-the-toolstrip"></a><span data-ttu-id="76ad6-114">Para organizar itens de ToolStrip no ToolStrip</span><span class="sxs-lookup"><span data-stu-id="76ad6-114">To arrange ToolStrip items on the ToolStrip</span></span>  
  
-   <span data-ttu-id="76ad6-115">Definir o <xref:System.Windows.Forms.ToolStrip.LayoutStyle%2A> o valor da propriedade <xref:System.Windows.Forms.ToolStripLayoutStyle> que você deseja.</span><span class="sxs-lookup"><span data-stu-id="76ad6-115">Set the <xref:System.Windows.Forms.ToolStrip.LayoutStyle%2A> property to the value of <xref:System.Windows.Forms.ToolStripLayoutStyle> that you want.</span></span>  
  
    ```vb  
    ToolStripDropDown1.LayoutStyle = _  
        System.Windows.Forms.ToolStripLayoutStyle.Flow  
    ```  
  
    ```csharp  
    toolStripDropDown1.LayoutStyle =   
        System.Windows.Forms.ToolStripLayoutStyle.Flow;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="76ad6-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="76ad6-116">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.Control.Layout>  
 <xref:System.Windows.Forms.ToolStrip.LayoutCompleted>  
 <xref:System.Windows.Forms.ToolStrip.LayoutSettings%2A>  
 <xref:System.Windows.Forms.ToolStripItem.TextImageRelation%2A>  
 <xref:System.Windows.Forms.ToolStripItem.Placement%2A>  
 <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A>  
 [<span data-ttu-id="76ad6-117">Visão geral do controle ToolStrip</span><span class="sxs-lookup"><span data-stu-id="76ad6-117">ToolStrip Control Overview</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)  
 [<span data-ttu-id="76ad6-118">Arquitetura de controle do ToolStrip</span><span class="sxs-lookup"><span data-stu-id="76ad6-118">ToolStrip Control Architecture</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md)  
 [<span data-ttu-id="76ad6-119">Resumo da tecnologia de ToolStrip</span><span class="sxs-lookup"><span data-stu-id="76ad6-119">ToolStrip Technology Summary</span></span>](../../../../docs/framework/winforms/controls/toolstrip-technology-summary.md)
