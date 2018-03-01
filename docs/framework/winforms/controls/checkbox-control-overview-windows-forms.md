---
title: "Visão geral do controle CheckBox (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CheckBox
helpviewer_keywords:
- CheckBox control [Windows Forms], about CheckBox control
- data binding [Windows Forms], checkbox controls
- check boxes [Windows Forms], about check boxes
ms.assetid: 085a4e0b-9046-473f-b141-d0edddfb2ebb
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 39645a02cd66d37d61df72028ab129677edb757e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="checkbox-control-overview-windows-forms"></a><span data-ttu-id="ee7ce-102">Visão geral do controle CheckBox (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="ee7ce-102">CheckBox Control Overview (Windows Forms)</span></span>
<span data-ttu-id="ee7ce-103">Windows Forms <xref:System.Windows.Forms.CheckBox> controle indica se uma determinada condição está ativado ou desativado.</span><span class="sxs-lookup"><span data-stu-id="ee7ce-103">The Windows Forms <xref:System.Windows.Forms.CheckBox> control indicates whether a particular condition is on or off.</span></span> <span data-ttu-id="ee7ce-104">É usado normalmente para apresentar uma seleção Sim/Não ou Verdadeiro/Falso ao usuário.</span><span class="sxs-lookup"><span data-stu-id="ee7ce-104">It is commonly used to present a Yes/No or True/False selection to the user.</span></span> <span data-ttu-id="ee7ce-105">Use os controles de caixa de seleção em grupos para exibir múltiplas opções entre as quais o usuário pode escolher uma ou mais.</span><span class="sxs-lookup"><span data-stu-id="ee7ce-105">You can use check box controls in groups to display multiple choices from which the user can select one or more.</span></span>  
  
 <span data-ttu-id="ee7ce-106">O controle de caixa de seleção é similar ao controle de botão de opção, ambos são usados para indicar uma seleção feita pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="ee7ce-106">The check box control is similar to the radio button control in that each is used to indicate a selection that is made by the user.</span></span> <span data-ttu-id="ee7ce-107">A diferença é que apenas um botão de opção em um grupo pode ser selecionado de cada vez.</span><span class="sxs-lookup"><span data-stu-id="ee7ce-107">They differ in that only one radio button in a group can be selected at a time.</span></span> <span data-ttu-id="ee7ce-108">Entretanto, com o controle de caixa de seleção é possível selecionar várias caixas de seleção.</span><span class="sxs-lookup"><span data-stu-id="ee7ce-108">With the check box control, however, any number of check boxes may be selected.</span></span>  
  
 <span data-ttu-id="ee7ce-109">Uma caixa de seleção pode se conectar aos elementos de um banco de dados usando associação de dados simples.</span><span class="sxs-lookup"><span data-stu-id="ee7ce-109">A check box may be connected to elements in a database using simple data binding.</span></span> <span data-ttu-id="ee7ce-110">Várias caixas de seleção podem ser agrupadas usando o <xref:System.Windows.Forms.GroupBox> controle.</span><span class="sxs-lookup"><span data-stu-id="ee7ce-110">Multiple check boxes may be grouped using the <xref:System.Windows.Forms.GroupBox> control.</span></span> <span data-ttu-id="ee7ce-111">Isso é útil para a aparência visual e também para o design de interface do usuário, uma vez que os controles agrupados podem ser movidos juntos no designer de formulários.</span><span class="sxs-lookup"><span data-stu-id="ee7ce-111">This is useful for visual appearance and also for user interface design, since grouped controls can be moved around together on the form designer.</span></span> <span data-ttu-id="ee7ce-112">Para mais informações, consulte [Associação de dados do Windows Forms](../../../../docs/framework/winforms/windows-forms-data-binding.md) e [Controle do GroupBox](../../../../docs/framework/winforms/controls/groupbox-control-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="ee7ce-112">For more information, see [Windows Forms Data Binding](../../../../docs/framework/winforms/windows-forms-data-binding.md) and [GroupBox Control](../../../../docs/framework/winforms/controls/groupbox-control-windows-forms.md).</span></span>  
  
 <span data-ttu-id="ee7ce-113">O <xref:System.Windows.Forms.CheckBox> controle tem duas propriedades importantes, <xref:System.Windows.Forms.CheckBox.Checked%2A> e <xref:System.Windows.Forms.CheckBox.CheckState%2A>.</span><span class="sxs-lookup"><span data-stu-id="ee7ce-113">The <xref:System.Windows.Forms.CheckBox> control has two important properties, <xref:System.Windows.Forms.CheckBox.Checked%2A> and <xref:System.Windows.Forms.CheckBox.CheckState%2A>.</span></span> <span data-ttu-id="ee7ce-114">O <xref:System.Windows.Forms.CheckBox.Checked%2A> propriedade retorna um `true` ou `false`.</span><span class="sxs-lookup"><span data-stu-id="ee7ce-114">The <xref:System.Windows.Forms.CheckBox.Checked%2A> property returns either `true` or `false`.</span></span> <span data-ttu-id="ee7ce-115">O <xref:System.Windows.Forms.CheckBox.CheckState%2A> propriedade retorna um <xref:System.Windows.Forms.CheckState.Checked> ou <xref:System.Windows.Forms.CheckState.Unchecked>; ou, se o <xref:System.Windows.Forms.CheckBox.ThreeState%2A> está definida como `true`, <xref:System.Windows.Forms.CheckBox.CheckState%2A> também podem retornar <xref:System.Windows.Forms.CheckState.Indeterminate>.</span><span class="sxs-lookup"><span data-stu-id="ee7ce-115">The <xref:System.Windows.Forms.CheckBox.CheckState%2A> property returns either <xref:System.Windows.Forms.CheckState.Checked> or <xref:System.Windows.Forms.CheckState.Unchecked>; or, if the <xref:System.Windows.Forms.CheckBox.ThreeState%2A> property is set to `true`, <xref:System.Windows.Forms.CheckBox.CheckState%2A> may also return <xref:System.Windows.Forms.CheckState.Indeterminate>.</span></span> <span data-ttu-id="ee7ce-116">No estado indeterminado, a caixa é mostrada com uma aparência esmaecida para indicar que a opção não está disponível.</span><span class="sxs-lookup"><span data-stu-id="ee7ce-116">In the indeterminate state, the box is displayed with a dimmed appearance to indicate the option is unavailable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee7ce-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ee7ce-117">See Also</span></span>  
 <xref:System.Windows.Forms.CheckBox>  
 [<span data-ttu-id="ee7ce-118">Como definir opções com os controles CheckBox dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ee7ce-118">How to: Set Options with Windows Forms CheckBox Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-set-options-with-windows-forms-checkbox-controls.md)  
 [<span data-ttu-id="ee7ce-119">Como responder a cliques em CheckBox dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ee7ce-119">How to: Respond to Windows Forms CheckBox Clicks</span></span>](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-checkbox-clicks.md)  
 [<span data-ttu-id="ee7ce-120">Controle CheckBox</span><span class="sxs-lookup"><span data-stu-id="ee7ce-120">CheckBox Control</span></span>](../../../../docs/framework/winforms/controls/checkbox-control-windows-forms.md)
