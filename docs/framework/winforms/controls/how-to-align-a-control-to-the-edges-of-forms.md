---
title: Como alinhar um controle às bordas de formulários
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Dock property [Windows Forms], aligning controls (using code)
- forms [Windows Forms], aligning controls
- controls [Windows Forms], aligning on forms
- custom controls [Windows Forms], docking using code
ms.assetid: 5994cb59-242b-4e75-bd0e-62879c34d702
ms.openlocfilehash: a8571f668de2714511a8732772443a8897043cf2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-align-a-control-to-the-edges-of-forms"></a><span data-ttu-id="bb8aa-102">Como alinhar um controle às bordas de formulários</span><span class="sxs-lookup"><span data-stu-id="bb8aa-102">How to: Align a Control to the Edges of Forms</span></span>
<span data-ttu-id="bb8aa-103">Você pode fazer com que o seu controle alinhe a borda de formulários, definindo o <xref:System.Windows.Forms.Control.Dock%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="bb8aa-103">You can make your control align to the edge of your forms by setting the <xref:System.Windows.Forms.Control.Dock%2A> property.</span></span> <span data-ttu-id="bb8aa-104">Essa propriedade determina onde reside o controle no formulário.</span><span class="sxs-lookup"><span data-stu-id="bb8aa-104">This property designates where your control resides in the form.</span></span> <span data-ttu-id="bb8aa-105">O <xref:System.Windows.Forms.Control.Dock%2A> propriedade pode ser definida com os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="bb8aa-105">The <xref:System.Windows.Forms.Control.Dock%2A> property can be set to the following values:</span></span>  
  
|<span data-ttu-id="bb8aa-106">Configuração</span><span class="sxs-lookup"><span data-stu-id="bb8aa-106">Setting</span></span>|<span data-ttu-id="bb8aa-107">Efeito no seu controle</span><span class="sxs-lookup"><span data-stu-id="bb8aa-107">Effect on your control</span></span>|  
|-------------|----------------------------|  
|<xref:System.Windows.Forms.DockStyle.Bottom>|<span data-ttu-id="bb8aa-108">Encaixa na parte inferior do formulário.</span><span class="sxs-lookup"><span data-stu-id="bb8aa-108">Docks to the bottom of the form.</span></span>|  
|<xref:System.Windows.Forms.DockStyle.Fill>|<span data-ttu-id="bb8aa-109">Preenche todo o espaço restante no formulário.</span><span class="sxs-lookup"><span data-stu-id="bb8aa-109">Fills all remaining space in the form.</span></span>|  
|<xref:System.Windows.Forms.DockStyle.Left>|<span data-ttu-id="bb8aa-110">Encaixa do lado esquerdo do formulário.</span><span class="sxs-lookup"><span data-stu-id="bb8aa-110">Docks to the left side of the form.</span></span>|  
|<xref:System.Windows.Forms.DockStyle.None>|<span data-ttu-id="bb8aa-111">Faz não encaixe em qualquer local e ele aparece no local especificado por seu <xref:System.Windows.Forms.Control.Location%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="bb8aa-111">Does not dock anywhere, and it appears at the location specified by its <xref:System.Windows.Forms.Control.Location%2A> property.</span></span>|  
|<xref:System.Windows.Forms.DockStyle.Right>|<span data-ttu-id="bb8aa-112">Encaixa do lado direito do formulário.</span><span class="sxs-lookup"><span data-stu-id="bb8aa-112">Docks to the right side of the form.</span></span>|  
|<xref:System.Windows.Forms.DockStyle.Top>|<span data-ttu-id="bb8aa-113">Encaixa na parte superior do formulário.</span><span class="sxs-lookup"><span data-stu-id="bb8aa-113">Docks to the top of the form.</span></span>|  
  
 <span data-ttu-id="bb8aa-114">Não há suporte de tempo de design para esse recurso no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="bb8aa-114">There is design-time support for this feature in Visual Studio.</span></span>  
  
### <a name="to-set-the-dock-property-for-your-control-at-run-time"></a><span data-ttu-id="bb8aa-115">Para definir a propriedade Dock de controle de tempo de execução</span><span class="sxs-lookup"><span data-stu-id="bb8aa-115">To set the Dock property for your control at run time</span></span>  
  
1.  <span data-ttu-id="bb8aa-116">Definir o <xref:System.Windows.Forms.Control.Dock%2A> propriedade para o valor apropriado no código.</span><span class="sxs-lookup"><span data-stu-id="bb8aa-116">Set the <xref:System.Windows.Forms.Control.Dock%2A> property to the appropriate value in code.</span></span>  
  
    ```vb  
    ' To set the Dock property internally.  
    Me.Dock = DockStyle.Top  
    ' To set the Dock property from another object.  
    UserControl1.Dock = DockStyle.Top  
    ```  
  
    ```csharp  
    // To set the Dock property internally.  
    this.Dock = DockStyle.Top;  
    // To set the Dock property from another object.  
    UserControl1.Dock = DockStyle.Top;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="bb8aa-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bb8aa-117">See Also</span></span>  
 <xref:System.Windows.Forms.Control.Dock%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.Control.Anchor%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="bb8aa-118">Desenvolvendo controles dos Windows Forms personalizados com o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="bb8aa-118">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)  
 [<span data-ttu-id="bb8aa-119">Como ancorar e encaixar controles filho em um controle FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="bb8aa-119">How to: Anchor and Dock Child Controls in a FlowLayoutPanel Control</span></span>](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control.md)  
 [<span data-ttu-id="bb8aa-120">Como ancorar e encaixar controles filho em um controle TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="bb8aa-120">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)  
 [<span data-ttu-id="bb8aa-121">Visão geral da propriedade AutoSize</span><span class="sxs-lookup"><span data-stu-id="bb8aa-121">AutoSize Property Overview</span></span>](../../../../docs/framework/winforms/controls/autosize-property-overview.md)
