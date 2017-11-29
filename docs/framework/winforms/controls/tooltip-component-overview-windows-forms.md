---
title: "Visão geral do componente ToolTip (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: ToolTip
helpviewer_keywords:
- tooltips [Windows Forms], about tooltips
- ToolTip component [Windows Forms], about ToolTip component
ms.assetid: 3fbc6f08-c882-4acd-a960-a08efe3c7e6e
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ff2364b5c7223c265571257920a7c7e794b4921b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="tooltip-component-overview-windows-forms"></a><span data-ttu-id="f867d-102">Visão geral do componente ToolTip (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="f867d-102">ToolTip Component Overview (Windows Forms)</span></span>
<span data-ttu-id="f867d-103">Windows Forms <xref:System.Windows.Forms.ToolTip> componente exibe texto quando o usuário aponta para controles.</span><span class="sxs-lookup"><span data-stu-id="f867d-103">The Windows Forms <xref:System.Windows.Forms.ToolTip> component displays text when the user points at controls.</span></span> <span data-ttu-id="f867d-104">Uma dica de ferramenta pode ser associada a qualquer controle.</span><span class="sxs-lookup"><span data-stu-id="f867d-104">A ToolTip can be associated with any control.</span></span> <span data-ttu-id="f867d-105">Um exemplo de uso desse componente: para economizar espaço em um formulário, você pode exibir um pequeno ícone em um botão e usar uma dica de ferramenta para explicar a função do botão.</span><span class="sxs-lookup"><span data-stu-id="f867d-105">An example use of this component: to save space on a form, you can display a small icon on a button and use a ToolTip to explain the button's function.</span></span>  
  
## <a name="working-with-the-tooltip-component"></a><span data-ttu-id="f867d-106">Trabalhando com o componente ToolTip</span><span class="sxs-lookup"><span data-stu-id="f867d-106">Working with the ToolTip Component</span></span>  
 <span data-ttu-id="f867d-107">Um <xref:System.Windows.Forms.ToolTip> componente fornece um `ToolTip` propriedade para vários controles em um formulário do Windows ou outro contêiner.</span><span class="sxs-lookup"><span data-stu-id="f867d-107">A <xref:System.Windows.Forms.ToolTip> component provides a `ToolTip` property to multiple controls on a Windows Form or other container.</span></span> <span data-ttu-id="f867d-108">Por exemplo, se você colocar um <xref:System.Windows.Forms.ToolTip> componente em um formulário, você pode exibir "Digite seu nome aqui" para um <xref:System.Windows.Forms.TextBox> controlar e "Clique aqui para salvar as alterações" para um <xref:System.Windows.Forms.Button> controle.</span><span class="sxs-lookup"><span data-stu-id="f867d-108">For example, if you place one <xref:System.Windows.Forms.ToolTip> component on a form, you can display "Type your name here" for a <xref:System.Windows.Forms.TextBox> control and "Click here to save changes" for a <xref:System.Windows.Forms.Button> control.</span></span>  
  
 <span data-ttu-id="f867d-109">Os principais métodos do <xref:System.Windows.Forms.ToolTip> componente são <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> e <xref:System.Windows.Forms.ToolTip.GetToolTip%2A>.</span><span class="sxs-lookup"><span data-stu-id="f867d-109">The key methods of the <xref:System.Windows.Forms.ToolTip> component are <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> and <xref:System.Windows.Forms.ToolTip.GetToolTip%2A>.</span></span> <span data-ttu-id="f867d-110">Você pode usar o <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> método para definir as dicas de ferramenta exibidas para controles.</span><span class="sxs-lookup"><span data-stu-id="f867d-110">You can use the <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> method to set the ToolTips displayed for controls.</span></span> <span data-ttu-id="f867d-111">Para obter mais informações, consulte [Como definir ToolTips para controles em um Windows Form no tempo de design](../../../../docs/framework/winforms/controls/how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="f867d-111">For more information, see [How to: Set ToolTips for Controls on a Windows Form at Design Time](../../../../docs/framework/winforms/controls/how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time.md).</span></span> <span data-ttu-id="f867d-112">As propriedades de chave são <xref:System.Windows.Forms.ToolTip.Active%2A>, que deve ser definido como `true` para a dica de ferramenta, e <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A>, que define o período de tempo que a cadeia de caracteres de dica de ferramenta é exibida, quanto tempo o usuário deve apontar para o controle para a dica de ferramenta e como tempo leva para windows subsequente de dica de ferramenta apareça.</span><span class="sxs-lookup"><span data-stu-id="f867d-112">The key properties are <xref:System.Windows.Forms.ToolTip.Active%2A>, which must be set to `true` for the ToolTip to appear, and <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A>, which sets the length of time that the ToolTip string is shown, how long the user must point at the control for the ToolTip to appear, and how long it takes for subsequent ToolTip windows to appear.</span></span> <span data-ttu-id="f867d-113">Para obter mais informações, consulte [Como alterar o atraso do componente ToolTip dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-change-the-delay-of-the-windows-forms-tooltip-component.md).</span><span class="sxs-lookup"><span data-stu-id="f867d-113">For more information, see [How to: Change the Delay of the Windows Forms ToolTip Component](../../../../docs/framework/winforms/controls/how-to-change-the-delay-of-the-windows-forms-tooltip-component.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f867d-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f867d-114">See Also</span></span>  
 <xref:System.Windows.Forms.ToolTip>  
 [<span data-ttu-id="f867d-115">Como definir ToolTips para controles em um Windows Form no tempo de design</span><span class="sxs-lookup"><span data-stu-id="f867d-115">How to: Set ToolTips for Controls on a Windows Form at Design Time</span></span>](../../../../docs/framework/winforms/controls/how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time.md)  
 [<span data-ttu-id="f867d-116">Como alterar o atraso do componente ToolTip dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f867d-116">How to: Change the Delay of the Windows Forms ToolTip Component</span></span>](../../../../docs/framework/winforms/controls/how-to-change-the-delay-of-the-windows-forms-tooltip-component.md)
