---
title: Designar um botão como o botão de cancelamento usando o designer
ms.date: 03/30/2017
helpviewer_keywords:
- buttons [Windows Forms], cancel buttons
- Button control [Windows Forms], designating as cancel button
ms.assetid: 30e77d9c-d565-4ab5-a84a-62c043af8822
ms.openlocfilehash: 95d1139b6e339055f944ad0b0967a6d91283d49e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746058"
---
# <a name="how-to-designate-a-windows-forms-button-as-the-cancel-button-using-the-designer"></a><span data-ttu-id="5eb6a-102">Como projetar um botão dos Windows Forms como o botão Cancelar usando o designer</span><span class="sxs-lookup"><span data-stu-id="5eb6a-102">How to: Designate a Windows Forms Button as the Cancel Button Using the Designer</span></span>
<span data-ttu-id="5eb6a-103">Em qualquer formulário do Windows, você pode designar um controle de <xref:System.Windows.Forms.Button> para ser o botão Cancelar.</span><span class="sxs-lookup"><span data-stu-id="5eb6a-103">On any Windows Form, you can designate a <xref:System.Windows.Forms.Button> control to be the cancel button.</span></span> <span data-ttu-id="5eb6a-104">Um botão Cancelar é clicado sempre que o usuário pressiona a tecla ESC, independentemente de qual outro controle no formulário tem o foco.</span><span class="sxs-lookup"><span data-stu-id="5eb6a-104">A cancel button is clicked whenever the user presses the ESC key, regardless of which other control on the form has the focus.</span></span> <span data-ttu-id="5eb6a-105">Esse botão geralmente é programado para permitir que o usuário saia rapidamente de uma operação sem confirmar qualquer ação.</span><span class="sxs-lookup"><span data-stu-id="5eb6a-105">Such a button is usually programmed to enable the user to quickly exit an operation without committing to any action.</span></span>

## <a name="to-designate-the-cancel-button"></a><span data-ttu-id="5eb6a-106">Para designar o botão Cancelar</span><span class="sxs-lookup"><span data-stu-id="5eb6a-106">To designate the cancel button</span></span>

1. <span data-ttu-id="5eb6a-107">Selecione o formulário no qual o botão reside.</span><span class="sxs-lookup"><span data-stu-id="5eb6a-107">Select the form on which the button resides.</span></span>

2. <span data-ttu-id="5eb6a-108">Na janela **Propriedades** , defina a propriedade <xref:System.Windows.Forms.Form.CancelButton%2A> do formulário como o nome do controle de <xref:System.Windows.Forms.Button>.</span><span class="sxs-lookup"><span data-stu-id="5eb6a-108">In the **Properties** window, set the form's <xref:System.Windows.Forms.Form.CancelButton%2A> property to the <xref:System.Windows.Forms.Button> control's name.</span></span>

## <a name="see-also"></a><span data-ttu-id="5eb6a-109">Veja também</span><span class="sxs-lookup"><span data-stu-id="5eb6a-109">See also</span></span>

- <xref:System.Windows.Forms.Form.CancelButton%2A>
- [<span data-ttu-id="5eb6a-110">Visão geral do controle de botão</span><span class="sxs-lookup"><span data-stu-id="5eb6a-110">Button Control Overview</span></span>](button-control-overview-windows-forms.md)
- [<span data-ttu-id="5eb6a-111">Formas de selecionar um controle de botão dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5eb6a-111">Ways to Select a Windows Forms Button Control</span></span>](ways-to-select-a-windows-forms-button-control.md)
- [<span data-ttu-id="5eb6a-112">Como responder a cliques no botão dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5eb6a-112">How to: Respond to Windows Forms Button Clicks</span></span>](how-to-respond-to-windows-forms-button-clicks.md)
- [<span data-ttu-id="5eb6a-113">Como designar um botão do Windows Forms como o botão Aceitar usando o Designer</span><span class="sxs-lookup"><span data-stu-id="5eb6a-113">How to: Designate a Windows Forms Button as the Accept Button Using the Designer</span></span>](designate-a-wf-button-as-the-accept-button-using-the-designer.md)
- [<span data-ttu-id="5eb6a-114">Controle de botão</span><span class="sxs-lookup"><span data-stu-id="5eb6a-114">Button Control</span></span>](button-control-windows-forms.md)
