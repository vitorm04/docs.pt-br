---
title: Alterar o atraso do componente de dica de ferramenta
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- ToolTip component [Windows Forms], delay values
- tooltips [Windows Forms], delay values
- examples [Windows Forms], tooltips
ms.assetid: 08979ba7-dd84-477b-ab17-8d06e759be99
ms.openlocfilehash: 8ab0b0760e8c82d752eaada19f14cae57fa63fdc
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746580"
---
# <a name="how-to-change-the-delay-of-the-windows-forms-tooltip-component"></a><span data-ttu-id="b8a3a-102">Como alterar o atraso do componente ToolTip dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b8a3a-102">How to: Change the Delay of the Windows Forms ToolTip Component</span></span>
<span data-ttu-id="b8a3a-103">Há vários valores de atraso que podem ser definidos para um componente Windows Forms <xref:System.Windows.Forms.ToolTip>.</span><span class="sxs-lookup"><span data-stu-id="b8a3a-103">There are multiple delay values that you can set for a Windows Forms <xref:System.Windows.Forms.ToolTip> component.</span></span> <span data-ttu-id="b8a3a-104">A unidade de medida para todas essas propriedades é milissegundos.</span><span class="sxs-lookup"><span data-stu-id="b8a3a-104">The unit of measure for all these properties is milliseconds.</span></span> <span data-ttu-id="b8a3a-105">A propriedade <xref:System.Windows.Forms.ToolTip.InitialDelay%2A> determina por quanto tempo o usuário deve apontar para o controle associado para que a cadeia de dica de ferramenta apareça.</span><span class="sxs-lookup"><span data-stu-id="b8a3a-105">The <xref:System.Windows.Forms.ToolTip.InitialDelay%2A> property determines how long the user must point at the associated control for the ToolTip string to appear.</span></span> <span data-ttu-id="b8a3a-106">A propriedade <xref:System.Windows.Forms.ToolTip.ReshowDelay%2A> define o número de milissegundos que leva para que as cadeias de caracteres de dica de ferramenta subsequentes sejam exibidas à medida que o mouse se move de um controle associado à dica de ferramenta para outro.</span><span class="sxs-lookup"><span data-stu-id="b8a3a-106">The <xref:System.Windows.Forms.ToolTip.ReshowDelay%2A> property sets the number of milliseconds it takes for subsequent ToolTip strings to appear as the mouse moves from one ToolTip-associated control to another.</span></span> <span data-ttu-id="b8a3a-107">A propriedade <xref:System.Windows.Forms.ToolTip.AutoPopDelay%2A> determina o período de tempo em que a cadeia de dica de ferramenta é mostrada.</span><span class="sxs-lookup"><span data-stu-id="b8a3a-107">The <xref:System.Windows.Forms.ToolTip.AutoPopDelay%2A> property determines the length of time the ToolTip string is shown.</span></span> <span data-ttu-id="b8a3a-108">Você pode definir esses valores individualmente ou definindo o valor da propriedade <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A>; as outras propriedades de atraso são definidas com base no valor atribuído à propriedade <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A>.</span><span class="sxs-lookup"><span data-stu-id="b8a3a-108">You can set these values individually, or by setting the value of the <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> property; the other delay properties are set based on the value assigned to the <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> property.</span></span> <span data-ttu-id="b8a3a-109">Por exemplo, quando <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> é definido como um valor N, <xref:System.Windows.Forms.ToolTip.InitialDelay%2A> é definido como N, <xref:System.Windows.Forms.ToolTip.ReshowDelay%2A> é definido como o valor de <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> dividido por cinco (ou N/5) e <xref:System.Windows.Forms.ToolTip.AutoPopDelay%2A> é definido como um valor que é cinco vezes o valor da propriedade <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> (ou 5N).</span><span class="sxs-lookup"><span data-stu-id="b8a3a-109">For example, when <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> is set to a value N, <xref:System.Windows.Forms.ToolTip.InitialDelay%2A> is set to N, <xref:System.Windows.Forms.ToolTip.ReshowDelay%2A> is set to the value of <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> divided by five (or N/5), and <xref:System.Windows.Forms.ToolTip.AutoPopDelay%2A> is set to a value that is five times the value of the <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> property (or 5N).</span></span>  
  
### <a name="to-set-the-delay"></a><span data-ttu-id="b8a3a-110">Para definir o atraso</span><span class="sxs-lookup"><span data-stu-id="b8a3a-110">To set the delay</span></span>  
  
1. <span data-ttu-id="b8a3a-111">Defina as seguintes propriedades conforme mostrado neste exemplo.</span><span class="sxs-lookup"><span data-stu-id="b8a3a-111">Set the following properties as shown in this example.</span></span>  
  
    ```vb  
    ToolTip1.InitialDelay = 500  
    ToolTip1.ReshowDelay = 100  
    ToolTip1.AutoPopDelay = 5000  
    ```  
  
    ```csharp  
    ToolTip1.InitialDelay = 500;  
    ToolTip1.ReshowDelay = 100;  
    ToolTip1.AutoPopDelay = 5000;  
    ```  
  
    ```cpp  
    toolTip1->InitialDelay = 500;  
    toolTip1->ReshowDelay = 100;  
    toolTip1->AutoPopDelay = 5000;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="b8a3a-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b8a3a-112">See also</span></span>

- [<span data-ttu-id="b8a3a-113">Visão geral do componente ToolTip</span><span class="sxs-lookup"><span data-stu-id="b8a3a-113">ToolTip Component Overview</span></span>](tooltip-component-overview-windows-forms.md)
- [<span data-ttu-id="b8a3a-114">Como definir ToolTips para controles em um Windows Form no tempo de design</span><span class="sxs-lookup"><span data-stu-id="b8a3a-114">How to: Set ToolTips for Controls on a Windows Form at Design Time</span></span>](how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time.md)
- [<span data-ttu-id="b8a3a-115">Componente ToolTip</span><span class="sxs-lookup"><span data-stu-id="b8a3a-115">ToolTip Component</span></span>](tooltip-component-windows-forms.md)
