---
title: 'Como: Alinhar um controle às bordas de formulários'
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
ms.openlocfilehash: beb8881dbd2aedaefe66510c2942ce6c082b9729
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59329967"
---
# <a name="how-to-align-a-control-to-the-edges-of-forms"></a><span data-ttu-id="62c72-102">Como: Alinhar um controle às bordas de formulários</span><span class="sxs-lookup"><span data-stu-id="62c72-102">How to: Align a Control to the Edges of Forms</span></span>
<span data-ttu-id="62c72-103">Você pode fazer com que o seu controle Alinhar à borda de seus formulários configurando o <xref:System.Windows.Forms.Control.Dock%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="62c72-103">You can make your control align to the edge of your forms by setting the <xref:System.Windows.Forms.Control.Dock%2A> property.</span></span> <span data-ttu-id="62c72-104">Essa propriedade determina onde reside o controle no formulário.</span><span class="sxs-lookup"><span data-stu-id="62c72-104">This property designates where your control resides in the form.</span></span> <span data-ttu-id="62c72-105">O <xref:System.Windows.Forms.Control.Dock%2A> propriedade pode ser definida com os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="62c72-105">The <xref:System.Windows.Forms.Control.Dock%2A> property can be set to the following values:</span></span>  
  
|<span data-ttu-id="62c72-106">Configuração</span><span class="sxs-lookup"><span data-stu-id="62c72-106">Setting</span></span>|<span data-ttu-id="62c72-107">Efeito no seu controle</span><span class="sxs-lookup"><span data-stu-id="62c72-107">Effect on your control</span></span>|  
|-------------|----------------------------|  
|<xref:System.Windows.Forms.DockStyle.Bottom>|<span data-ttu-id="62c72-108">Encaixa na parte inferior do formulário.</span><span class="sxs-lookup"><span data-stu-id="62c72-108">Docks to the bottom of the form.</span></span>|  
|<xref:System.Windows.Forms.DockStyle.Fill>|<span data-ttu-id="62c72-109">Preenche todo o espaço restante no formulário.</span><span class="sxs-lookup"><span data-stu-id="62c72-109">Fills all remaining space in the form.</span></span>|  
|<xref:System.Windows.Forms.DockStyle.Left>|<span data-ttu-id="62c72-110">Encaixa do lado esquerdo do formulário.</span><span class="sxs-lookup"><span data-stu-id="62c72-110">Docks to the left side of the form.</span></span>|  
|<xref:System.Windows.Forms.DockStyle.None>|<span data-ttu-id="62c72-111">Não se encaixa em qualquer lugar e aparece no local especificado pelo seu <xref:System.Windows.Forms.Control.Location%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="62c72-111">Does not dock anywhere, and it appears at the location specified by its <xref:System.Windows.Forms.Control.Location%2A> property.</span></span>|  
|<xref:System.Windows.Forms.DockStyle.Right>|<span data-ttu-id="62c72-112">Encaixa do lado direito do formulário.</span><span class="sxs-lookup"><span data-stu-id="62c72-112">Docks to the right side of the form.</span></span>|  
|<xref:System.Windows.Forms.DockStyle.Top>|<span data-ttu-id="62c72-113">Encaixa na parte superior do formulário.</span><span class="sxs-lookup"><span data-stu-id="62c72-113">Docks to the top of the form.</span></span>|  
  
 <span data-ttu-id="62c72-114">Não há suporte de tempo de design para esse recurso no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="62c72-114">There is design-time support for this feature in Visual Studio.</span></span>  
  
### <a name="to-set-the-dock-property-for-your-control-at-run-time"></a><span data-ttu-id="62c72-115">Para definir a propriedade Dock para o seu controle em tempo de execução</span><span class="sxs-lookup"><span data-stu-id="62c72-115">To set the Dock property for your control at run time</span></span>  
  
1. <span data-ttu-id="62c72-116">Defina o <xref:System.Windows.Forms.Control.Dock%2A> propriedade para o valor apropriado no código.</span><span class="sxs-lookup"><span data-stu-id="62c72-116">Set the <xref:System.Windows.Forms.Control.Dock%2A> property to the appropriate value in code.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="62c72-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="62c72-117">See also</span></span>

- <xref:System.Windows.Forms.Control.Dock%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.Anchor%2A?displayProperty=nameWithType>
- [<span data-ttu-id="62c72-118">Desenvolvendo controles dos Windows Forms personalizados com o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="62c72-118">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](developing-custom-windows-forms-controls.md)
- [<span data-ttu-id="62c72-119">Como: Ancorar e encaixar controles filho em um controle FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="62c72-119">How to: Anchor and Dock Child Controls in a FlowLayoutPanel Control</span></span>](how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control.md)
- [<span data-ttu-id="62c72-120">Como: Ancorar e encaixar controles filho em um controle TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="62c72-120">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>](how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [<span data-ttu-id="62c72-121">Visão geral da propriedade AutoSize</span><span class="sxs-lookup"><span data-stu-id="62c72-121">AutoSize Property Overview</span></span>](autosize-property-overview.md)
