---
title: 'Como: Alterar o espaçamento e alinhamento de itens de ToolStrip nos Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStrip control [Windows Forms], aligning items
- examples [Windows Forms], toolbars
- toolbars [Windows Forms], aligning items
ms.assetid: cd483466-0f49-43df-addf-e2b5fcd64027
ms.openlocfilehash: 954087fa893baf3aa623c912efb081491304d3fb
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57719436"
---
# <a name="how-to-change-the-spacing-and-alignment-of-toolstrip-items-in-windows-forms"></a><span data-ttu-id="ce5e4-102">Como: Alterar o espaçamento e alinhamento de itens de ToolStrip nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ce5e4-102">How to: Change the Spacing and Alignment of ToolStrip Items in Windows Forms</span></span>
<span data-ttu-id="ce5e4-103">O <xref:System.Windows.Forms.ToolStrip> totalmente o controle dá suporte a recursos de layout como dimensionamento, espaçamento de <xref:System.Windows.Forms.ToolStripItem> controles relativos uns aos outros, a organização dos controles na <xref:System.Windows.Forms.ToolStrip>e o espaçamento dos controles relativo para o <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="ce5e4-103">The <xref:System.Windows.Forms.ToolStrip> control fully supports layout features such as sizing, the spacing of <xref:System.Windows.Forms.ToolStripItem> controls relative to each other, the arrangement of controls on the <xref:System.Windows.Forms.ToolStrip>, and the spacing of controls relative to the <xref:System.Windows.Forms.ToolStrip>.</span></span>  
  
 <span data-ttu-id="ce5e4-104">Porque o valor padrão do <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> é de propriedade `true`, controles são dimensionados automaticamente a menos que você defina o <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> propriedade `false`.</span><span class="sxs-lookup"><span data-stu-id="ce5e4-104">Because the default value of the <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> property is `true`, controls are sized automatically unless you set the <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> property to `false`.</span></span>  
  
### <a name="to-manually-size-a-toolstripitem"></a><span data-ttu-id="ce5e4-105">Para dimensionar manualmente um ToolStripItem</span><span class="sxs-lookup"><span data-stu-id="ce5e4-105">To manually size a ToolStripItem</span></span>  
  
1.  <span data-ttu-id="ce5e4-106">Defina as <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> propriedade para `false` para o controle associado.</span><span class="sxs-lookup"><span data-stu-id="ce5e4-106">Set the <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> property to `false` for the associated control.</span></span>  
  
    ```vb  
    ToolStripButton1.AutoSize = False  
    ```  
  
    ```csharp  
    toolStripButton1.AutoSize = false;  
    ```  
  
2.  <span data-ttu-id="ce5e4-107">Defina as <xref:System.Windows.Forms.ToolStripItem.Size%2A> propriedade da maneira desejada para associado <xref:System.Windows.Forms.ToolStripItem>.</span><span class="sxs-lookup"><span data-stu-id="ce5e4-107">Set the <xref:System.Windows.Forms.ToolStripItem.Size%2A> property the way you want for the associated <xref:System.Windows.Forms.ToolStripItem>.</span></span>  
  
### <a name="to-set-the-spacing-of-a-toolstripitem"></a><span data-ttu-id="ce5e4-108">Para definir o espaçamento de um ToolStripItem</span><span class="sxs-lookup"><span data-stu-id="ce5e4-108">To set the spacing of a ToolStripItem</span></span>  
  
1.  <span data-ttu-id="ce5e4-109">Insira os valores desejados, em pixels, o <xref:System.Windows.Forms.ToolStripItem.Margin%2A> propriedade do controle associado.</span><span class="sxs-lookup"><span data-stu-id="ce5e4-109">Insert the desired values, in pixels, into the <xref:System.Windows.Forms.ToolStripItem.Margin%2A> property of the associated control.</span></span>  
  
     <span data-ttu-id="ce5e4-110">Os valores da <xref:System.Windows.Forms.ToolStripItem.Margin%2A> propriedade especificam o espaçamento entre o item e itens adjacentes nesta ordem: À esquerda, superior, direita e inferior.</span><span class="sxs-lookup"><span data-stu-id="ce5e4-110">The values of the <xref:System.Windows.Forms.ToolStripItem.Margin%2A> property specify the spacing between the item and adjacent items in this order: Left, Top, Right, and Bottom.</span></span>  
  
    ```vb  
    ToolStripTextBox1.Margin = New System.Windows.Forms.Padding _  
        (3, 0, 3, 0)  
    ```  
  
    ```csharp  
    toolStripTextBox1.Margin = new System.Windows.Forms.Padding   
        (3, 0, 3, 0);  
    ```  
  
### <a name="to-align-a-toolstripitem-to-the-right-side-of-the-toolstrip"></a><span data-ttu-id="ce5e4-111">Para alinhar um ToolStripItem à direita de ToolStrip</span><span class="sxs-lookup"><span data-stu-id="ce5e4-111">To align a ToolStripItem to the right side of the ToolStrip</span></span>  
  
1.  <span data-ttu-id="ce5e4-112">Defina as <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> propriedade para <xref:System.Windows.Forms.ToolStripItemAlignment.Right> para o controle associado.</span><span class="sxs-lookup"><span data-stu-id="ce5e4-112">Set the <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> property to <xref:System.Windows.Forms.ToolStripItemAlignment.Right> for the associated control.</span></span> <span data-ttu-id="ce5e4-113">Por padrão, <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> é definido como <xref:System.Windows.Forms.ToolStripItemAlignment.Left>, que alinha os controles à esquerda do <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="ce5e4-113">By default, <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> is set to <xref:System.Windows.Forms.ToolStripItemAlignment.Left>, which aligns controls to the left side of the <xref:System.Windows.Forms.ToolStrip>.</span></span>  
  
    ```vb  
    ToolStripSplitButton1.Alignment = _  
        System.Windows.Forms.ToolStripItemAlignment.Right  
    ```  
  
    ```csharp  
    toolStripSplitButton1.Alignment =   
        System.Windows.Forms.ToolStripItemAlignment.Right;  
    ```  
  
### <a name="to-arrange-toolstrip-items-on-the-toolstrip"></a><span data-ttu-id="ce5e4-114">Para organizar itens de ToolStrip no ToolStrip</span><span class="sxs-lookup"><span data-stu-id="ce5e4-114">To arrange ToolStrip items on the ToolStrip</span></span>  
  
-   <span data-ttu-id="ce5e4-115">Defina as <xref:System.Windows.Forms.ToolStrip.LayoutStyle%2A> propriedade para o valor de <xref:System.Windows.Forms.ToolStripLayoutStyle> que você deseja.</span><span class="sxs-lookup"><span data-stu-id="ce5e4-115">Set the <xref:System.Windows.Forms.ToolStrip.LayoutStyle%2A> property to the value of <xref:System.Windows.Forms.ToolStripLayoutStyle> that you want.</span></span>  
  
    ```vb  
    ToolStripDropDown1.LayoutStyle = _  
        System.Windows.Forms.ToolStripLayoutStyle.Flow  
    ```  
  
    ```csharp  
    toolStripDropDown1.LayoutStyle =   
        System.Windows.Forms.ToolStripLayoutStyle.Flow;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="ce5e4-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ce5e4-116">See also</span></span>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.Control.Layout>
- <xref:System.Windows.Forms.ToolStrip.LayoutCompleted>
- <xref:System.Windows.Forms.ToolStrip.LayoutSettings%2A>
- <xref:System.Windows.Forms.ToolStripItem.TextImageRelation%2A>
- <xref:System.Windows.Forms.ToolStripItem.Placement%2A>
- <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A>
- [<span data-ttu-id="ce5e4-117">Visão geral do controle ToolStrip</span><span class="sxs-lookup"><span data-stu-id="ce5e4-117">ToolStrip Control Overview</span></span>](toolstrip-control-overview-windows-forms.md)
- [<span data-ttu-id="ce5e4-118">Arquitetura de controle do ToolStrip</span><span class="sxs-lookup"><span data-stu-id="ce5e4-118">ToolStrip Control Architecture</span></span>](toolstrip-control-architecture.md)
- [<span data-ttu-id="ce5e4-119">Resumo da tecnologia de ToolStrip</span><span class="sxs-lookup"><span data-stu-id="ce5e4-119">ToolStrip Technology Summary</span></span>](toolstrip-technology-summary.md)
