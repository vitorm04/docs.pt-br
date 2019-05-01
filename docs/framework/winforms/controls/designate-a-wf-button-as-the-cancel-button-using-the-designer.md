---
title: 'Como: Designar um botão do Windows Forms como o botão Cancelar usando o designer'
ms.date: 03/30/2017
helpviewer_keywords:
- buttons [Windows Forms], cancel buttons
- Button control [Windows Forms], designating as cancel button
ms.assetid: 30e77d9c-d565-4ab5-a84a-62c043af8822
ms.openlocfilehash: f127a1a74643c975aea73b24896c098b365aa327
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61972296"
---
# <a name="how-to-designate-a-windows-forms-button-as-the-cancel-button-using-the-designer"></a><span data-ttu-id="0c5a5-102">Como: Designar um botão do Windows Forms como o botão Cancelar usando o designer</span><span class="sxs-lookup"><span data-stu-id="0c5a5-102">How to: Designate a Windows Forms Button as the Cancel Button Using the Designer</span></span>
<span data-ttu-id="0c5a5-103">Em qualquer formulário do Windows, você pode designar um <xref:System.Windows.Forms.Button> controle para ser o botão Cancelar.</span><span class="sxs-lookup"><span data-stu-id="0c5a5-103">On any Windows Form, you can designate a <xref:System.Windows.Forms.Button> control to be the cancel button.</span></span> <span data-ttu-id="0c5a5-104">Um botão Cancelar é clicado sempre que o usuário pressiona a tecla ESC, independentemente de qual outro controle no formulário tem o foco.</span><span class="sxs-lookup"><span data-stu-id="0c5a5-104">A cancel button is clicked whenever the user presses the ESC key, regardless of which other control on the form has the focus.</span></span> <span data-ttu-id="0c5a5-105">Geralmente, este botão é programado para permitir que o usuário sair rapidamente de uma operação sem se comprometer com qualquer ação.</span><span class="sxs-lookup"><span data-stu-id="0c5a5-105">Such a button is usually programmed to enable the user to quickly exit an operation without committing to any action.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0c5a5-106">As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas.</span><span class="sxs-lookup"><span data-stu-id="0c5a5-106">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="0c5a5-107">Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="0c5a5-107">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="0c5a5-108">Para obter mais informações, confira [Personalizar o IDE do Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="0c5a5-108">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-designate-the-cancel-button"></a><span data-ttu-id="0c5a5-109">Para designar um botão Cancelar</span><span class="sxs-lookup"><span data-stu-id="0c5a5-109">To designate the cancel button</span></span>  
  
1. <span data-ttu-id="0c5a5-110">Selecione o formulário no qual reside o botão.</span><span class="sxs-lookup"><span data-stu-id="0c5a5-110">Select the form on which the button resides.</span></span>  
  
2. <span data-ttu-id="0c5a5-111">No **propriedades** janela, defina o formulário <xref:System.Windows.Forms.Form.CancelButton%2A> propriedade para o <xref:System.Windows.Forms.Button> nome do controle.</span><span class="sxs-lookup"><span data-stu-id="0c5a5-111">In the **Properties** window, set the form's <xref:System.Windows.Forms.Form.CancelButton%2A> property to the <xref:System.Windows.Forms.Button> control's name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c5a5-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0c5a5-112">See also</span></span>

- <xref:System.Windows.Forms.Form.CancelButton%2A>
- [<span data-ttu-id="0c5a5-113">Visão geral do controle de botão</span><span class="sxs-lookup"><span data-stu-id="0c5a5-113">Button Control Overview</span></span>](button-control-overview-windows-forms.md)
- [<span data-ttu-id="0c5a5-114">Formas de selecionar um controle de botão dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0c5a5-114">Ways to Select a Windows Forms Button Control</span></span>](ways-to-select-a-windows-forms-button-control.md)
- [<span data-ttu-id="0c5a5-115">Como: Responder a cliques de botão do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0c5a5-115">How to: Respond to Windows Forms Button Clicks</span></span>](how-to-respond-to-windows-forms-button-clicks.md)
- [<span data-ttu-id="0c5a5-116">Como: Designar um botão dos Windows Forms como botão aceitar usando o Designer</span><span class="sxs-lookup"><span data-stu-id="0c5a5-116">How to: Designate a Windows Forms Button as the Accept Button Using the Designer</span></span>](designate-a-wf-button-as-the-accept-button-using-the-designer.md)
- [<span data-ttu-id="0c5a5-117">Controle de botão</span><span class="sxs-lookup"><span data-stu-id="0c5a5-117">Button Control</span></span>](button-control-windows-forms.md)
