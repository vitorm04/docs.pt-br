---
title: Como gerenciar o estouro de ToolStrip nos Windows Forms
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStrip control [Windows Forms], managing overflow
- toolbars [Windows Forms], managing overflow
- examples [Windows Forms], toolbars
- CanOverflow property
ms.assetid: fa10e0ad-4cbf-4c0d-9082-359c2f855d4e
ms.openlocfilehash: 32bbc06320f0dc7f096a4b9021bebfbefedaf8f7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33534886"
---
# <a name="how-to-manage-toolstrip-overflow-in-windows-forms"></a><span data-ttu-id="8a8fc-102">Como gerenciar o estouro de ToolStrip nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8a8fc-102">How to: Manage ToolStrip Overflow in Windows Forms</span></span>
<span data-ttu-id="8a8fc-103">Quando todos os itens em uma <xref:System.Windows.Forms.ToolStrip> controle não se ajustarem no espaço reservado, você pode habilitar a funcionalidade de estouro no <xref:System.Windows.Forms.ToolStrip> e determinar o comportamento de estouro de específicos <xref:System.Windows.Forms.ToolStripItem>s.</span><span class="sxs-lookup"><span data-stu-id="8a8fc-103">When all the items on a <xref:System.Windows.Forms.ToolStrip> control do not fit in the allotted space, you can enable overflow functionality on the <xref:System.Windows.Forms.ToolStrip> and determine the overflow behavior of specific <xref:System.Windows.Forms.ToolStripItem>s.</span></span>  
  
 <span data-ttu-id="8a8fc-104">Quando você adiciona <xref:System.Windows.Forms.ToolStripItem>que exigem mais espaço do que está alocado para o <xref:System.Windows.Forms.ToolStrip> dado o tamanho atual do formulário, uma <xref:System.Windows.Forms.ToolStripOverflowButton> aparece automaticamente na <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="8a8fc-104">When you add <xref:System.Windows.Forms.ToolStripItem>s that require more space than is allotted to the <xref:System.Windows.Forms.ToolStrip> given the form's current size, a <xref:System.Windows.Forms.ToolStripOverflowButton> automatically appears on the <xref:System.Windows.Forms.ToolStrip>.</span></span> <span data-ttu-id="8a8fc-105">O <xref:System.Windows.Forms.ToolStripOverflowButton> for exibida, e os itens com overflow ativado são movidos para o menu suspenso de excedentes.</span><span class="sxs-lookup"><span data-stu-id="8a8fc-105">The <xref:System.Windows.Forms.ToolStripOverflowButton> appears, and overflow-enabled items are moved into the drop-down overflow menu.</span></span> <span data-ttu-id="8a8fc-106">Isso permite que você personalize e priorizar como seu <xref:System.Windows.Forms.ToolStrip> itens ajustam adequadamente para tamanhos de forma diferente.</span><span class="sxs-lookup"><span data-stu-id="8a8fc-106">This allows you to customize and prioritize how your <xref:System.Windows.Forms.ToolStrip> items properly adjust to different form sizes.</span></span> <span data-ttu-id="8a8fc-107">Você também pode alterar a aparência de seus itens quando eles se encaixam o estouro usando o <xref:System.Windows.Forms.ToolStripItem.Placement%2A> e <xref:System.Windows.Forms.ToolStripOverflow.DisplayedItems%2A?displayProperty=nameWithType> propriedades e o <xref:System.Windows.Forms.ToolStrip.LayoutCompleted> evento.</span><span class="sxs-lookup"><span data-stu-id="8a8fc-107">You can also change the appearance of your items when they fall into the overflow by using the <xref:System.Windows.Forms.ToolStripItem.Placement%2A> and <xref:System.Windows.Forms.ToolStripOverflow.DisplayedItems%2A?displayProperty=nameWithType> properties and the <xref:System.Windows.Forms.ToolStrip.LayoutCompleted> event.</span></span> <span data-ttu-id="8a8fc-108">Se você aumentar o formulário no tempo de design ou em tempo de execução mais <xref:System.Windows.Forms.ToolStripItem>s podem ser exibidos no principal <xref:System.Windows.Forms.ToolStrip> e <xref:System.Windows.Forms.ToolStripOverflowButton> pode até mesmo desaparecer até que você diminuir o tamanho do formulário.</span><span class="sxs-lookup"><span data-stu-id="8a8fc-108">If you enlarge the form at either design time or run time, more <xref:System.Windows.Forms.ToolStripItem>s can be displayed on the main <xref:System.Windows.Forms.ToolStrip> and the <xref:System.Windows.Forms.ToolStripOverflowButton> might even disappear until you decrease the size of the form.</span></span>  
  
### <a name="to-enable-overflow-on-a-toolstrip-control"></a><span data-ttu-id="8a8fc-109">Para habilitar o estouro em um controle ToolStrip</span><span class="sxs-lookup"><span data-stu-id="8a8fc-109">To enable overflow on a ToolStrip control</span></span>  
  
-   <span data-ttu-id="8a8fc-110">Certifique-se de que o <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A> propriedade não está definida como `false` para o <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="8a8fc-110">Ensure that the <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A> property is not set to `false` for the <xref:System.Windows.Forms.ToolStrip>.</span></span> <span data-ttu-id="8a8fc-111">O padrão é `True`.</span><span class="sxs-lookup"><span data-stu-id="8a8fc-111">The default is `True`.</span></span>  
  
     <span data-ttu-id="8a8fc-112">Quando <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A> é `True` (o padrão), um <xref:System.Windows.Forms.ToolStripItem> é enviada para o menu suspenso estouro quando o conteúdo do <xref:System.Windows.Forms.ToolStripItem> excede a largura de uma horizontal <xref:System.Windows.Forms.ToolStrip> ou a altura de um vertical <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="8a8fc-112">When <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A> is `True` (the default), a <xref:System.Windows.Forms.ToolStripItem> is sent to the drop-down overflow menu when the content of the <xref:System.Windows.Forms.ToolStripItem> exceeds the width of a horizontal <xref:System.Windows.Forms.ToolStrip> or the height of a vertical <xref:System.Windows.Forms.ToolStrip>.</span></span>  
  
### <a name="to-specify-overflow-behavior-of-a-specific-toolstripitem"></a><span data-ttu-id="8a8fc-113">Especificar comportamento de estouro de um item ToolStripItem específico</span><span class="sxs-lookup"><span data-stu-id="8a8fc-113">To specify overflow behavior of a specific ToolStripItem</span></span>  
  
-   <span data-ttu-id="8a8fc-114">Definir o <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> propriedade o <xref:System.Windows.Forms.ToolStripItem> para o valor desejado.</span><span class="sxs-lookup"><span data-stu-id="8a8fc-114">Set the <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> property of the <xref:System.Windows.Forms.ToolStripItem> to the desired value.</span></span> <span data-ttu-id="8a8fc-115">As possibilidades são `Always`, `Never` e `AsNeeded`.</span><span class="sxs-lookup"><span data-stu-id="8a8fc-115">The possibilities are `Always`, `Never`, and `AsNeeded`.</span></span> <span data-ttu-id="8a8fc-116">O padrão é `AsNeeded`.</span><span class="sxs-lookup"><span data-stu-id="8a8fc-116">The defaultis `AsNeeded`.</span></span>  
  
    ```vb  
    toolStripTextBox1.Overflow = _  
    System.Windows.Forms.ToolStripItemOverflow.Never  
    ```  
  
    ```csharp  
    toolStripTextBox1.Overflow = _  
    System.Windows.Forms.ToolStripItemOverflow.Never;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="8a8fc-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8a8fc-117">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.ToolStripOverflowButton>  
 <xref:System.Windows.Forms.ToolStripItem.Overflow%2A>  
 <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A>  
 [<span data-ttu-id="8a8fc-118">Visão geral do controle ToolStrip</span><span class="sxs-lookup"><span data-stu-id="8a8fc-118">ToolStrip Control Overview</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)  
 [<span data-ttu-id="8a8fc-119">Arquitetura de controle do ToolStrip</span><span class="sxs-lookup"><span data-stu-id="8a8fc-119">ToolStrip Control Architecture</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md)  
 [<span data-ttu-id="8a8fc-120">Resumo da tecnologia de ToolStrip</span><span class="sxs-lookup"><span data-stu-id="8a8fc-120">ToolStrip Technology Summary</span></span>](../../../../docs/framework/winforms/controls/toolstrip-technology-summary.md)
