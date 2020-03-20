---
title: 'Como: Alterar o espaçamento e o alinhamento dos itens toolStrip'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStrip control [Windows Forms], aligning items
- examples [Windows Forms], toolbars
- toolbars [Windows Forms], aligning items
ms.assetid: cd483466-0f49-43df-addf-e2b5fcd64027
ms.openlocfilehash: 550ac1660a077e8d766a01bfa8d102c07f0fbfeb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182236"
---
# <a name="how-to-change-the-spacing-and-alignment-of-toolstrip-items-in-windows-forms"></a><span data-ttu-id="d2e51-102">Como alterar o espaçamento e o alinhamento de itens ToolStrip nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d2e51-102">How to: Change the Spacing and Alignment of ToolStrip Items in Windows Forms</span></span>
<span data-ttu-id="d2e51-103">O <xref:System.Windows.Forms.ToolStrip> controle suporta totalmente características de layout, como <xref:System.Windows.Forms.ToolStripItem> o dimensionamento, o espaçamento dos <xref:System.Windows.Forms.ToolStrip>controles em relação ao outro, <xref:System.Windows.Forms.ToolStrip>o arranjo de controles sobre o , e o espaçamento dos controles relativos ao .</span><span class="sxs-lookup"><span data-stu-id="d2e51-103">The <xref:System.Windows.Forms.ToolStrip> control fully supports layout features such as sizing, the spacing of <xref:System.Windows.Forms.ToolStripItem> controls relative to each other, the arrangement of controls on the <xref:System.Windows.Forms.ToolStrip>, and the spacing of controls relative to the <xref:System.Windows.Forms.ToolStrip>.</span></span>  
  
 <span data-ttu-id="d2e51-104">Como o valor <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> padrão `true`da propriedade é, os controles <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> são `false`dimensionados automaticamente, a menos que você defina a propriedade para .</span><span class="sxs-lookup"><span data-stu-id="d2e51-104">Because the default value of the <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> property is `true`, controls are sized automatically unless you set the <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> property to `false`.</span></span>  
  
### <a name="to-manually-size-a-toolstripitem"></a><span data-ttu-id="d2e51-105">Para dimensionar manualmente um ToolStripItem</span><span class="sxs-lookup"><span data-stu-id="d2e51-105">To manually size a ToolStripItem</span></span>  
  
1. <span data-ttu-id="d2e51-106">Defina <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> a `false` propriedade para o controle associado.</span><span class="sxs-lookup"><span data-stu-id="d2e51-106">Set the <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> property to `false` for the associated control.</span></span>  
  
    ```vb  
    ToolStripButton1.AutoSize = False  
    ```  
  
    ```csharp  
    toolStripButton1.AutoSize = false;  
    ```  
  
2. <span data-ttu-id="d2e51-107">Defina <xref:System.Windows.Forms.ToolStripItem.Size%2A> a propriedade da maneira <xref:System.Windows.Forms.ToolStripItem>que você quiser para o associado .</span><span class="sxs-lookup"><span data-stu-id="d2e51-107">Set the <xref:System.Windows.Forms.ToolStripItem.Size%2A> property the way you want for the associated <xref:System.Windows.Forms.ToolStripItem>.</span></span>  
  
### <a name="to-set-the-spacing-of-a-toolstripitem"></a><span data-ttu-id="d2e51-108">Para definir o espaçamento de um ToolStripItem</span><span class="sxs-lookup"><span data-stu-id="d2e51-108">To set the spacing of a ToolStripItem</span></span>  
  
1. <span data-ttu-id="d2e51-109">Insira os valores desejados, <xref:System.Windows.Forms.ToolStripItem.Margin%2A> em pixels, na propriedade do controle associado.</span><span class="sxs-lookup"><span data-stu-id="d2e51-109">Insert the desired values, in pixels, into the <xref:System.Windows.Forms.ToolStripItem.Margin%2A> property of the associated control.</span></span>  
  
     <span data-ttu-id="d2e51-110">Os valores <xref:System.Windows.Forms.ToolStripItem.Margin%2A> da propriedade especificam o espaçamento entre o item e os itens adjacentes nesta ordem: Esquerda, Superior, Direita e Inferior.</span><span class="sxs-lookup"><span data-stu-id="d2e51-110">The values of the <xref:System.Windows.Forms.ToolStripItem.Margin%2A> property specify the spacing between the item and adjacent items in this order: Left, Top, Right, and Bottom.</span></span>  
  
    ```vb  
    ToolStripTextBox1.Margin = New System.Windows.Forms.Padding _  
        (3, 0, 3, 0)  
    ```  
  
    ```csharp  
    toolStripTextBox1.Margin = new System.Windows.Forms.Padding
        (3, 0, 3, 0);  
    ```  
  
### <a name="to-align-a-toolstripitem-to-the-right-side-of-the-toolstrip"></a><span data-ttu-id="d2e51-111">Para alinhar um ToolStripItem à direita de ToolStrip</span><span class="sxs-lookup"><span data-stu-id="d2e51-111">To align a ToolStripItem to the right side of the ToolStrip</span></span>  
  
1. <span data-ttu-id="d2e51-112">Defina <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> a <xref:System.Windows.Forms.ToolStripItemAlignment.Right> propriedade para o controle associado.</span><span class="sxs-lookup"><span data-stu-id="d2e51-112">Set the <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> property to <xref:System.Windows.Forms.ToolStripItemAlignment.Right> for the associated control.</span></span> <span data-ttu-id="d2e51-113">Por padrão, <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> é <xref:System.Windows.Forms.ToolStripItemAlignment.Left>definido para , que alinha <xref:System.Windows.Forms.ToolStrip>os controles para o lado esquerdo do .</span><span class="sxs-lookup"><span data-stu-id="d2e51-113">By default, <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> is set to <xref:System.Windows.Forms.ToolStripItemAlignment.Left>, which aligns controls to the left side of the <xref:System.Windows.Forms.ToolStrip>.</span></span>  
  
    ```vb  
    ToolStripSplitButton1.Alignment = _  
        System.Windows.Forms.ToolStripItemAlignment.Right  
    ```  
  
    ```csharp  
    toolStripSplitButton1.Alignment =
        System.Windows.Forms.ToolStripItemAlignment.Right;  
    ```  
  
### <a name="to-arrange-toolstrip-items-on-the-toolstrip"></a><span data-ttu-id="d2e51-114">Para organizar itens de ToolStrip no ToolStrip</span><span class="sxs-lookup"><span data-stu-id="d2e51-114">To arrange ToolStrip items on the ToolStrip</span></span>  
  
- <span data-ttu-id="d2e51-115">Defina <xref:System.Windows.Forms.ToolStrip.LayoutStyle%2A> a propriedade <xref:System.Windows.Forms.ToolStripLayoutStyle> para o valor do que você deseja.</span><span class="sxs-lookup"><span data-stu-id="d2e51-115">Set the <xref:System.Windows.Forms.ToolStrip.LayoutStyle%2A> property to the value of <xref:System.Windows.Forms.ToolStripLayoutStyle> that you want.</span></span>  
  
    ```vb  
    ToolStripDropDown1.LayoutStyle = _  
        System.Windows.Forms.ToolStripLayoutStyle.Flow  
    ```  
  
    ```csharp  
    toolStripDropDown1.LayoutStyle =
        System.Windows.Forms.ToolStripLayoutStyle.Flow;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="d2e51-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="d2e51-116">See also</span></span>

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.Control.Layout>
- <xref:System.Windows.Forms.ToolStrip.LayoutCompleted>
- <xref:System.Windows.Forms.ToolStrip.LayoutSettings%2A>
- <xref:System.Windows.Forms.ToolStripItem.TextImageRelation%2A>
- <xref:System.Windows.Forms.ToolStripItem.Placement%2A>
- <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A>
- [<span data-ttu-id="d2e51-117">Visão geral do controle ToolStrip</span><span class="sxs-lookup"><span data-stu-id="d2e51-117">ToolStrip Control Overview</span></span>](toolstrip-control-overview-windows-forms.md)
- [<span data-ttu-id="d2e51-118">Arquitetura de controle ToolStrip</span><span class="sxs-lookup"><span data-stu-id="d2e51-118">ToolStrip Control Architecture</span></span>](toolstrip-control-architecture.md)
- [<span data-ttu-id="d2e51-119">Resumo da tecnologia de ToolStrip</span><span class="sxs-lookup"><span data-stu-id="d2e51-119">ToolStrip Technology Summary</span></span>](toolstrip-technology-summary.md)
