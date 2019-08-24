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
ms.openlocfilehash: 5d662489b7e31f391bbd508409e69c091a25592c
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015942"
---
# <a name="how-to-align-a-control-to-the-edges-of-forms"></a><span data-ttu-id="99427-102">Como: Alinhar um controle às bordas de formulários</span><span class="sxs-lookup"><span data-stu-id="99427-102">How to: Align a Control to the Edges of Forms</span></span>

<span data-ttu-id="99427-103">Você pode fazer com que seu controle fique alinhado à borda de seus formulários <xref:System.Windows.Forms.Control.Dock%2A> definindo a propriedade.</span><span class="sxs-lookup"><span data-stu-id="99427-103">You can make your control align to the edge of your forms by setting the <xref:System.Windows.Forms.Control.Dock%2A> property.</span></span> <span data-ttu-id="99427-104">Essa propriedade determina onde reside o controle no formulário.</span><span class="sxs-lookup"><span data-stu-id="99427-104">This property designates where your control resides in the form.</span></span> <span data-ttu-id="99427-105">A <xref:System.Windows.Forms.Control.Dock%2A> propriedade pode ser definida com os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="99427-105">The <xref:System.Windows.Forms.Control.Dock%2A> property can be set to the following values:</span></span>

|<span data-ttu-id="99427-106">Configuração</span><span class="sxs-lookup"><span data-stu-id="99427-106">Setting</span></span>|<span data-ttu-id="99427-107">Efeito no seu controle</span><span class="sxs-lookup"><span data-stu-id="99427-107">Effect on your control</span></span>|
|-------------|----------------------------|
|<xref:System.Windows.Forms.DockStyle.Bottom>|<span data-ttu-id="99427-108">Encaixa na parte inferior do formulário.</span><span class="sxs-lookup"><span data-stu-id="99427-108">Docks to the bottom of the form.</span></span>|
|<xref:System.Windows.Forms.DockStyle.Fill>|<span data-ttu-id="99427-109">Preenche todo o espaço restante no formulário.</span><span class="sxs-lookup"><span data-stu-id="99427-109">Fills all remaining space in the form.</span></span>|
|<xref:System.Windows.Forms.DockStyle.Left>|<span data-ttu-id="99427-110">Encaixa do lado esquerdo do formulário.</span><span class="sxs-lookup"><span data-stu-id="99427-110">Docks to the left side of the form.</span></span>|
|<xref:System.Windows.Forms.DockStyle.None>|<span data-ttu-id="99427-111">Não encaixa em nenhum lugar e aparece no local especificado por sua <xref:System.Windows.Forms.Control.Location%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="99427-111">Does not dock anywhere, and it appears at the location specified by its <xref:System.Windows.Forms.Control.Location%2A> property.</span></span>|
|<xref:System.Windows.Forms.DockStyle.Right>|<span data-ttu-id="99427-112">Encaixa do lado direito do formulário.</span><span class="sxs-lookup"><span data-stu-id="99427-112">Docks to the right side of the form.</span></span>|
|<xref:System.Windows.Forms.DockStyle.Top>|<span data-ttu-id="99427-113">Encaixa na parte superior do formulário.</span><span class="sxs-lookup"><span data-stu-id="99427-113">Docks to the top of the form.</span></span>|

<span data-ttu-id="99427-114">Há suporte para o tempo de design para esse recurso no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="99427-114">There is design-time support for this feature in Visual Studio.</span></span>

## <a name="set-the-dock-property-for-your-control-at-run-time"></a><span data-ttu-id="99427-115">Definir a propriedade Dock para seu controle em tempo de execução</span><span class="sxs-lookup"><span data-stu-id="99427-115">Set the Dock property for your control at run time</span></span>

<span data-ttu-id="99427-116">Defina a <xref:System.Windows.Forms.Control.Dock%2A> propriedade para o valor apropriado no código.</span><span class="sxs-lookup"><span data-stu-id="99427-116">Set the <xref:System.Windows.Forms.Control.Dock%2A> property to the appropriate value in code.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="99427-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="99427-117">See also</span></span>

- <xref:System.Windows.Forms.Control.Dock%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.Anchor%2A?displayProperty=nameWithType>
- [<span data-ttu-id="99427-118">Desenvolvendo controles dos Windows Forms personalizados com o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="99427-118">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](developing-custom-windows-forms-controls.md)
- [<span data-ttu-id="99427-119">Como: Ancorar e encaixar controles filho em um controle FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="99427-119">How to: Anchor and Dock Child Controls in a FlowLayoutPanel Control</span></span>](how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control.md)
- [<span data-ttu-id="99427-120">Como: Ancorar e encaixar controles filho em um controle TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="99427-120">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>](how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [<span data-ttu-id="99427-121">Visão geral da propriedade AutoSize</span><span class="sxs-lookup"><span data-stu-id="99427-121">AutoSize Property Overview</span></span>](autosize-property-overview.md)
