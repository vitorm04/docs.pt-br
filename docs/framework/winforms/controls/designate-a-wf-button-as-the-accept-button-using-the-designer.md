---
title: 'Como: Designar um botão do Windows Forms como o botão Aceitar usando o designer'
ms.date: 03/30/2017
helpviewer_keywords:
- buttons [Windows Forms], default on Windows Forms
- Accept button on Windows Forms
- Button control [Windows Forms], designating as default
- Windows Forms controls, default button on form
ms.assetid: a1da0590-755f-49f2-aca7-609fac6351bf
ms.openlocfilehash: 27ecb26c493232bcfb996d012f9760b7ef91e5b2
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039652"
---
# <a name="how-to-designate-a-windows-forms-button-as-the-accept-button-using-the-designer"></a><span data-ttu-id="7f0ad-102">Como: Designar um botão do Windows Forms como o botão Aceitar usando o designer</span><span class="sxs-lookup"><span data-stu-id="7f0ad-102">How to: Designate a Windows Forms Button as the Accept Button Using the Designer</span></span>
<span data-ttu-id="7f0ad-103">Em qualquer formulário do Windows, você pode designar <xref:System.Windows.Forms.Button> um controle para ser o botão aceitar, também conhecido como o botão padrão.</span><span class="sxs-lookup"><span data-stu-id="7f0ad-103">On any Windows Form, you can designate a <xref:System.Windows.Forms.Button> control to be the accept button, also known as the default button.</span></span> <span data-ttu-id="7f0ad-104">Sempre que o usuário pressiona a tecla ENTER, o botão padrão é clicado, independentemente de qual outro controle no formulário tenha o foco.</span><span class="sxs-lookup"><span data-stu-id="7f0ad-104">Whenever the user presses the ENTER key, the default button is clicked regardless of which other control on the form has the focus.</span></span> <span data-ttu-id="7f0ad-105">As exceções a isso são quando o controle com foco é outro botão — nesse caso, o botão com o foco será clicado — ou uma caixa de texto de várias linhas ou um controle personalizado que intercepta a tecla ENTER.</span><span class="sxs-lookup"><span data-stu-id="7f0ad-105">The exceptions to this are when the control with focus is another button — in that case, the button with the focus will be clicked — or a multiline text box, or a custom control that traps the ENTER key.</span></span>

## <a name="to-designate-the-accept-button"></a><span data-ttu-id="7f0ad-106">Para designar o botão aceitar</span><span class="sxs-lookup"><span data-stu-id="7f0ad-106">To designate the accept button</span></span>

1. <span data-ttu-id="7f0ad-107">Selecione o formulário no qual o botão reside.</span><span class="sxs-lookup"><span data-stu-id="7f0ad-107">Select the form on which the button resides.</span></span>

2. <span data-ttu-id="7f0ad-108">Na janela **Propriedades** , defina a propriedade do <xref:System.Windows.Forms.Form.AcceptButton%2A> formulário como o <xref:System.Windows.Forms.Button> nome do controle.</span><span class="sxs-lookup"><span data-stu-id="7f0ad-108">In the **Properties** window, set the form's <xref:System.Windows.Forms.Form.AcceptButton%2A> property to the <xref:System.Windows.Forms.Button> control's name.</span></span>

## <a name="see-also"></a><span data-ttu-id="7f0ad-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7f0ad-109">See also</span></span>

- <xref:System.Windows.Forms.Form.AcceptButton%2A>
- [<span data-ttu-id="7f0ad-110">Visão geral do controle de botão</span><span class="sxs-lookup"><span data-stu-id="7f0ad-110">Button Control Overview</span></span>](button-control-overview-windows-forms.md)
- [<span data-ttu-id="7f0ad-111">Formas de selecionar um controle de botão dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7f0ad-111">Ways to Select a Windows Forms Button Control</span></span>](ways-to-select-a-windows-forms-button-control.md)
- [<span data-ttu-id="7f0ad-112">Como: Responder a Windows Forms cliques de botão</span><span class="sxs-lookup"><span data-stu-id="7f0ad-112">How to: Respond to Windows Forms Button Clicks</span></span>](how-to-respond-to-windows-forms-button-clicks.md)
- [<span data-ttu-id="7f0ad-113">Como: Designar um botão de Windows Forms como o botão de cancelamento usando o designer</span><span class="sxs-lookup"><span data-stu-id="7f0ad-113">How to: Designate a Windows Forms Button as the Cancel Button Using the Designer</span></span>](designate-a-wf-button-as-the-cancel-button-using-the-designer.md)
- [<span data-ttu-id="7f0ad-114">Controle de botão</span><span class="sxs-lookup"><span data-stu-id="7f0ad-114">Button Control</span></span>](button-control-windows-forms.md)
