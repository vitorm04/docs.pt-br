---
title: 'Como: Designar um botão do Windows Forms como o botão Cancelar usando o designer'
ms.date: 03/30/2017
helpviewer_keywords:
- buttons [Windows Forms], cancel buttons
- Button control [Windows Forms], designating as cancel button
ms.assetid: 30e77d9c-d565-4ab5-a84a-62c043af8822
ms.openlocfilehash: cc352f15fb1e8b531cd0f9b298b2db4ce649d3cf
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039643"
---
# <a name="how-to-designate-a-windows-forms-button-as-the-cancel-button-using-the-designer"></a><span data-ttu-id="775dd-102">Como: Designar um botão do Windows Forms como o botão Cancelar usando o designer</span><span class="sxs-lookup"><span data-stu-id="775dd-102">How to: Designate a Windows Forms Button as the Cancel Button Using the Designer</span></span>
<span data-ttu-id="775dd-103">Em qualquer formulário do Windows, você pode designar <xref:System.Windows.Forms.Button> um controle para ser o botão Cancelar.</span><span class="sxs-lookup"><span data-stu-id="775dd-103">On any Windows Form, you can designate a <xref:System.Windows.Forms.Button> control to be the cancel button.</span></span> <span data-ttu-id="775dd-104">Um botão Cancelar é clicado sempre que o usuário pressiona a tecla ESC, independentemente de qual outro controle no formulário tem o foco.</span><span class="sxs-lookup"><span data-stu-id="775dd-104">A cancel button is clicked whenever the user presses the ESC key, regardless of which other control on the form has the focus.</span></span> <span data-ttu-id="775dd-105">Esse botão geralmente é programado para permitir que o usuário saia rapidamente de uma operação sem confirmar qualquer ação.</span><span class="sxs-lookup"><span data-stu-id="775dd-105">Such a button is usually programmed to enable the user to quickly exit an operation without committing to any action.</span></span>

## <a name="to-designate-the-cancel-button"></a><span data-ttu-id="775dd-106">Para designar o botão Cancelar</span><span class="sxs-lookup"><span data-stu-id="775dd-106">To designate the cancel button</span></span>

1. <span data-ttu-id="775dd-107">Selecione o formulário no qual o botão reside.</span><span class="sxs-lookup"><span data-stu-id="775dd-107">Select the form on which the button resides.</span></span>

2. <span data-ttu-id="775dd-108">Na janela **Propriedades** , defina a propriedade do <xref:System.Windows.Forms.Form.CancelButton%2A> formulário como o <xref:System.Windows.Forms.Button> nome do controle.</span><span class="sxs-lookup"><span data-stu-id="775dd-108">In the **Properties** window, set the form's <xref:System.Windows.Forms.Form.CancelButton%2A> property to the <xref:System.Windows.Forms.Button> control's name.</span></span>

## <a name="see-also"></a><span data-ttu-id="775dd-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="775dd-109">See also</span></span>

- <xref:System.Windows.Forms.Form.CancelButton%2A>
- [<span data-ttu-id="775dd-110">Visão geral do controle de botão</span><span class="sxs-lookup"><span data-stu-id="775dd-110">Button Control Overview</span></span>](button-control-overview-windows-forms.md)
- [<span data-ttu-id="775dd-111">Formas de selecionar um controle de botão dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="775dd-111">Ways to Select a Windows Forms Button Control</span></span>](ways-to-select-a-windows-forms-button-control.md)
- [<span data-ttu-id="775dd-112">Como: Responder a Windows Forms cliques de botão</span><span class="sxs-lookup"><span data-stu-id="775dd-112">How to: Respond to Windows Forms Button Clicks</span></span>](how-to-respond-to-windows-forms-button-clicks.md)
- [<span data-ttu-id="775dd-113">Como: Designar um botão de Windows Forms como o botão aceitar usando o designer</span><span class="sxs-lookup"><span data-stu-id="775dd-113">How to: Designate a Windows Forms Button as the Accept Button Using the Designer</span></span>](designate-a-wf-button-as-the-accept-button-using-the-designer.md)
- [<span data-ttu-id="775dd-114">Controle de botão</span><span class="sxs-lookup"><span data-stu-id="775dd-114">Button Control</span></span>](button-control-windows-forms.md)
