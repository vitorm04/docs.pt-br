---
title: Como projetar um botão dos Windows Forms como o botão Aceitar usando o designer
ms.date: 03/30/2017
helpviewer_keywords:
- buttons [Windows Forms], default on Windows Forms
- Accept button on Windows Forms
- Button control [Windows Forms], designating as default
- Windows Forms controls, default button on form
ms.assetid: a1da0590-755f-49f2-aca7-609fac6351bf
ms.openlocfilehash: ca049e86ab53fbd84cb24e81b0a850050ec2823f
ms.sourcegitcommit: dfb2a100cfb4d3902c042f17b3204f49bc7635e7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/20/2018
ms.locfileid: "46492364"
---
# <a name="how-to-designate-a-windows-forms-button-as-the-accept-button-using-the-designer"></a><span data-ttu-id="7c4d5-102">Como projetar um botão dos Windows Forms como o botão Aceitar usando o designer</span><span class="sxs-lookup"><span data-stu-id="7c4d5-102">How to: Designate a Windows Forms Button as the Accept Button Using the Designer</span></span>
<span data-ttu-id="7c4d5-103">Em qualquer formulário do Windows, você pode designar um <xref:System.Windows.Forms.Button> controle para ser o botão aceitar, também conhecido como botão padrão.</span><span class="sxs-lookup"><span data-stu-id="7c4d5-103">On any Windows Form, you can designate a <xref:System.Windows.Forms.Button> control to be the accept button, also known as the default button.</span></span> <span data-ttu-id="7c4d5-104">Sempre que o usuário pressiona a tecla ENTER, o botão padrão é clicado, independentemente de qual outro controle no formulário tem o foco.</span><span class="sxs-lookup"><span data-stu-id="7c4d5-104">Whenever the user presses the ENTER key, the default button is clicked regardless of which other control on the form has the focus.</span></span> <span data-ttu-id="7c4d5-105">As exceções a isso são quando o controle com o foco é outro botão — nesse caso, o botão com o foco será ser clicado — ou uma caixa de texto de várias linhas, ou um controle personalizado que intercepte a tecla ENTER.</span><span class="sxs-lookup"><span data-stu-id="7c4d5-105">The exceptions to this are when the control with focus is another button — in that case, the button with the focus will be clicked — or a multiline text box, or a custom control that traps the ENTER key.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7c4d5-106">As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas.</span><span class="sxs-lookup"><span data-stu-id="7c4d5-106">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="7c4d5-107">Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="7c4d5-107">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="7c4d5-108">Para obter mais informações, confira [Personalizar o IDE do Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="7c4d5-108">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-designate-the-accept-button"></a><span data-ttu-id="7c4d5-109">Para designar o botão aceitar</span><span class="sxs-lookup"><span data-stu-id="7c4d5-109">To designate the accept button</span></span>  
  
1.  <span data-ttu-id="7c4d5-110">Selecione o formulário no qual reside o botão.</span><span class="sxs-lookup"><span data-stu-id="7c4d5-110">Select the form on which the button resides.</span></span>  
  
2.  <span data-ttu-id="7c4d5-111">No **propriedades** janela, defina o formulário <xref:System.Windows.Forms.Form.AcceptButton%2A> propriedade para o <xref:System.Windows.Forms.Button> nome do controle.</span><span class="sxs-lookup"><span data-stu-id="7c4d5-111">In the **Properties** window, set the form's <xref:System.Windows.Forms.Form.AcceptButton%2A> property to the <xref:System.Windows.Forms.Button> control's name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c4d5-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7c4d5-112">See Also</span></span>  
 <xref:System.Windows.Forms.Form.AcceptButton%2A>  
 [<span data-ttu-id="7c4d5-113">Visão geral do controle de botão</span><span class="sxs-lookup"><span data-stu-id="7c4d5-113">Button Control Overview</span></span>](../../../../docs/framework/winforms/controls/button-control-overview-windows-forms.md)  
 [<span data-ttu-id="7c4d5-114">Formas de selecionar um controle de botão dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7c4d5-114">Ways to Select a Windows Forms Button Control</span></span>](../../../../docs/framework/winforms/controls/ways-to-select-a-windows-forms-button-control.md)  
 [<span data-ttu-id="7c4d5-115">Como responder a cliques no botão dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7c4d5-115">How to: Respond to Windows Forms Button Clicks</span></span>](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)  
 [<span data-ttu-id="7c4d5-116">Como projetar um botão do Windows Forms como o botão Cancelar usando o Designer</span><span class="sxs-lookup"><span data-stu-id="7c4d5-116">How to: Designate a Windows Forms Button as the Cancel Button Using the Designer</span></span>](../../../../docs/framework/winforms/controls/designate-a-wf-button-as-the-cancel-button-using-the-designer.md)  
 [<span data-ttu-id="7c4d5-117">Controle de botão</span><span class="sxs-lookup"><span data-stu-id="7c4d5-117">Button Control</span></span>](../../../../docs/framework/winforms/controls/button-control-windows-forms.md)
