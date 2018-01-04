---
title: "Como deixar o controle invisível em tempo de execução"
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
- controls [Windows Forms], making invisible at run time
- invisible controls
- user controls [Windows Forms], invisible
- custom controls [Windows Forms], invisible
- run time [Windows Forms], making controls invisible
ms.assetid: 69eb2e72-32f5-4f79-a157-c2c5f60c1628
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6e28a682c6f3bfc52a293daebeade960c1875bb5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-make-your-control-invisible-at-run-time"></a><span data-ttu-id="666f5-102">Como deixar o controle invisível em tempo de execução</span><span class="sxs-lookup"><span data-stu-id="666f5-102">How to: Make Your Control Invisible at Run Time</span></span>
<span data-ttu-id="666f5-103">Há vezes em que você quer criar um controle de usuário invisível em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="666f5-103">There are times when you might want to create a user control that is invisible at run time.</span></span> <span data-ttu-id="666f5-104">Por exemplo, um controle que é um relógio despertador pode ser invisível, exceto quando o alarme foi acionado.</span><span class="sxs-lookup"><span data-stu-id="666f5-104">For example, a control that is an alarm clock might be invisible except when the alarm was sounding.</span></span> <span data-ttu-id="666f5-105">Isso é feito facilmente configurando o <xref:System.Windows.Forms.Control.Visible%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="666f5-105">This is easily accomplished by setting the <xref:System.Windows.Forms.Control.Visible%2A> property.</span></span> <span data-ttu-id="666f5-106">Se o <xref:System.Windows.Forms.Control.Visible%2A> é de propriedade `true`, o controle será exibido como normal.</span><span class="sxs-lookup"><span data-stu-id="666f5-106">If the <xref:System.Windows.Forms.Control.Visible%2A> property is `true`, your control will appear as normal.</span></span> <span data-ttu-id="666f5-107">Se for `false`, o controle será ocultado.</span><span class="sxs-lookup"><span data-stu-id="666f5-107">If `false`, your control will be hidden.</span></span> <span data-ttu-id="666f5-108">Embora o código em seu controle ainda possa ser executado enquanto invisível, você não poderá interagir com o controle por meio da interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="666f5-108">Although code in your control may still run while invisible, you will not be able to interact with the control through the user interface.</span></span> <span data-ttu-id="666f5-109">Se quiser criar um controle invisível que ainda responde à entrada do usuário (por exemplo, cliques de mouse), você deverá criar um controle transparente.</span><span class="sxs-lookup"><span data-stu-id="666f5-109">If you want to create an invisible control that still responds to user input (for example, mouse clicks), you should create a transparent control.</span></span> <span data-ttu-id="666f5-110">Para obter mais informações, veja [Como dar ao controle de uma tela de fundo transparente](../../../../docs/framework/winforms/controls/how-to-give-your-control-a-transparent-background.md).</span><span class="sxs-lookup"><span data-stu-id="666f5-110">For more information, see [Giving Your Control a Transparent Background](../../../../docs/framework/winforms/controls/how-to-give-your-control-a-transparent-background.md).</span></span>  
  
### <a name="to-make-your-control-invisible-at-run-time"></a><span data-ttu-id="666f5-111">Para deixar o controle invisível em tempo de execução</span><span class="sxs-lookup"><span data-stu-id="666f5-111">To make your control invisible at run time</span></span>  
  
1.  <span data-ttu-id="666f5-112">Defina a propriedade <xref:System.Windows.Forms.Control.Visible%2A> como `false`.</span><span class="sxs-lookup"><span data-stu-id="666f5-112">Set the <xref:System.Windows.Forms.Control.Visible%2A> property to `false`.</span></span>  
  
    ```vb  
    ' To set the Visible property from within your object's own code.  
    Me.Visible = False  
    ' To set the Visible property from another object.  
    myControl1.Visible = False  
    ```  
  
    ```csharp  
    // To set the Visible property from within your object's own code.  
    this.Visible = false;  
    // To set the Visible property from another object.  
    myControl1.Visible = false;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="666f5-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="666f5-113">See Also</span></span>  
 <xref:System.Windows.Forms.Control.Visible%2A>  
 [<span data-ttu-id="666f5-114">Desenvolvendo controles dos Windows Forms personalizados com o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="666f5-114">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)  
 [<span data-ttu-id="666f5-115">Como dar ao controle uma tela de fundo transparente</span><span class="sxs-lookup"><span data-stu-id="666f5-115">How to: Give Your Control a Transparent Background</span></span>](../../../../docs/framework/winforms/controls/how-to-give-your-control-a-transparent-background.md)
