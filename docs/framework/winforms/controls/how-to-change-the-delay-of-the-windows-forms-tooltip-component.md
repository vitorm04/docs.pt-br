---
title: 'Como: Alterar o atraso do componente ToolTip dos Windows Forms'
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
ms.openlocfilehash: 5f3be7467aad8b14aa67dc57b8c23e585a62fa25
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57704453"
---
# <a name="how-to-change-the-delay-of-the-windows-forms-tooltip-component"></a><span data-ttu-id="dd757-102">Como: Alterar o atraso do componente ToolTip dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="dd757-102">How to: Change the Delay of the Windows Forms ToolTip Component</span></span>
<span data-ttu-id="dd757-103">Há vários valores de atraso que podem ser definidas para um Windows Forms <xref:System.Windows.Forms.ToolTip> componente.</span><span class="sxs-lookup"><span data-stu-id="dd757-103">There are multiple delay values that you can set for a Windows Forms <xref:System.Windows.Forms.ToolTip> component.</span></span> <span data-ttu-id="dd757-104">A unidade de medida para todas essas propriedades é milissegundos.</span><span class="sxs-lookup"><span data-stu-id="dd757-104">The unit of measure for all these properties is milliseconds.</span></span> <span data-ttu-id="dd757-105">O <xref:System.Windows.Forms.ToolTip.InitialDelay%2A> propriedade determina quanto tempo o usuário deve apontar para o controle associado para a cadeia de caracteres de dica de ferramenta apareça.</span><span class="sxs-lookup"><span data-stu-id="dd757-105">The <xref:System.Windows.Forms.ToolTip.InitialDelay%2A> property determines how long the user must point at the associated control for the ToolTip string to appear.</span></span> <span data-ttu-id="dd757-106">O <xref:System.Windows.Forms.ToolTip.ReshowDelay%2A> propriedade define o número de milissegundos que leva para cadeias de caracteres de dica de ferramenta subsequentes sejam exibidas quando o mouse se move de um controle associado a dica de ferramenta para outra.</span><span class="sxs-lookup"><span data-stu-id="dd757-106">The <xref:System.Windows.Forms.ToolTip.ReshowDelay%2A> property sets the number of milliseconds it takes for subsequent ToolTip strings to appear as the mouse moves from one ToolTip-associated control to another.</span></span> <span data-ttu-id="dd757-107">O <xref:System.Windows.Forms.ToolTip.AutoPopDelay%2A> propriedade determina o período de tempo que a cadeia de caracteres de dica de ferramenta é mostrada.</span><span class="sxs-lookup"><span data-stu-id="dd757-107">The <xref:System.Windows.Forms.ToolTip.AutoPopDelay%2A> property determines the length of time the ToolTip string is shown.</span></span> <span data-ttu-id="dd757-108">Você pode definir esses valores individualmente ou definindo o valor da <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> propriedade; o outro atraso são definidas com base no valor atribuído para o <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="dd757-108">You can set these values individually, or by setting the value of the <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> property; the other delay properties are set based on the value assigned to the <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> property.</span></span> <span data-ttu-id="dd757-109">Por exemplo, quando <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> é definido como um valor de N, <xref:System.Windows.Forms.ToolTip.InitialDelay%2A> é definido como N, <xref:System.Windows.Forms.ToolTip.ReshowDelay%2A> é definido como o valor de <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> dividido por cinco (ou N/5), e <xref:System.Windows.Forms.ToolTip.AutoPopDelay%2A> é definido como um valor que é cinco vezes o valor da <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> propriedade (ou 5N).</span><span class="sxs-lookup"><span data-stu-id="dd757-109">For example, when <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> is set to a value N, <xref:System.Windows.Forms.ToolTip.InitialDelay%2A> is set to N, <xref:System.Windows.Forms.ToolTip.ReshowDelay%2A> is set to the value of <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> divided by five (or N/5), and <xref:System.Windows.Forms.ToolTip.AutoPopDelay%2A> is set to a value that is five times the value of the <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> property (or 5N).</span></span>  
  
### <a name="to-set-the-delay"></a><span data-ttu-id="dd757-110">Para definir o atraso</span><span class="sxs-lookup"><span data-stu-id="dd757-110">To set the delay</span></span>  
  
1.  <span data-ttu-id="dd757-111">Defina as seguintes propriedades conforme mostrado neste exemplo.</span><span class="sxs-lookup"><span data-stu-id="dd757-111">Set the following properties as shown in this example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="dd757-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dd757-112">See also</span></span>
- [<span data-ttu-id="dd757-113">Visão geral do componente ToolTip</span><span class="sxs-lookup"><span data-stu-id="dd757-113">ToolTip Component Overview</span></span>](tooltip-component-overview-windows-forms.md)
- [<span data-ttu-id="dd757-114">Como: Definir ToolTips para controles em um Windows Form no tempo de Design</span><span class="sxs-lookup"><span data-stu-id="dd757-114">How to: Set ToolTips for Controls on a Windows Form at Design Time</span></span>](how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time.md)
- [<span data-ttu-id="dd757-115">Componente ToolTip</span><span class="sxs-lookup"><span data-stu-id="dd757-115">ToolTip Component</span></span>](tooltip-component-windows-forms.md)
