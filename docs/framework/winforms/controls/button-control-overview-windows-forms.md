---
title: "Visão geral do controle Button (Windows Forms)"
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
- Button
helpviewer_keywords:
- Button control [Windows Forms], about Button control
- buttons [Windows Forms], about buttons
ms.assetid: 255b291b-51a9-4a92-a1a4-2400cd82443f
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e04b99c9d85ae92ad4d013abc01c5b16914fe1c3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="button-control-overview-windows-forms"></a><span data-ttu-id="03423-102">Visão geral do controle Button (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="03423-102">Button Control Overview (Windows Forms)</span></span>
<span data-ttu-id="03423-103">O controle <xref:System.Windows.Forms.Button> dos Windows Forms permite que o usuário clique nele para realizar uma ação.</span><span class="sxs-lookup"><span data-stu-id="03423-103">The Windows Forms <xref:System.Windows.Forms.Button> control allows the user to click it to perform an action.</span></span> <span data-ttu-id="03423-104">Quando o botão é clicado, ele se parece como se estivesse sendo empurrado e solto.</span><span class="sxs-lookup"><span data-stu-id="03423-104">When the button is clicked, it looks as if it is being pushed in and released.</span></span> <span data-ttu-id="03423-105">Sempre que o usuário clica em um botão, o <xref:System.Windows.Forms.Control.Click> manipulador de eventos é chamado.</span><span class="sxs-lookup"><span data-stu-id="03423-105">Whenever the user clicks a button, the <xref:System.Windows.Forms.Control.Click> event handler is invoked.</span></span> <span data-ttu-id="03423-106">Coloque o código de <xref:System.Windows.Forms.Control.Click> manipulador de eventos para realizar qualquer ação que você escolher.</span><span class="sxs-lookup"><span data-stu-id="03423-106">You place code in the <xref:System.Windows.Forms.Control.Click> event handler to perform any action you choose.</span></span>  
  
 <span data-ttu-id="03423-107">O texto exibido no botão está contido no <xref:System.Windows.Forms.Control.Text%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="03423-107">The text displayed on the button is contained in the <xref:System.Windows.Forms.Control.Text%2A> property.</span></span> <span data-ttu-id="03423-108">Se o texto exceder a largura do botão, ele será encapsulado para a próxima linha.</span><span class="sxs-lookup"><span data-stu-id="03423-108">If your text exceeds the width of the button, it will wrap to the next line.</span></span> <span data-ttu-id="03423-109">No entanto, ele será recortado se o controle não puder acomodar sua altura geral.</span><span class="sxs-lookup"><span data-stu-id="03423-109">However, it will be clipped if the control cannot accommodate its overall height.</span></span> <span data-ttu-id="03423-110">Para obter mais informações, consulte [Como definir o texto exibido por um controle dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md).</span><span class="sxs-lookup"><span data-stu-id="03423-110">For more information, see [How to: Set the Text Displayed by a Windows Forms Control](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md).</span></span> <span data-ttu-id="03423-111">O <xref:System.Windows.Forms.Control.Text%2A> propriedade pode conter uma chave de acesso, que permite que um usuário "clique" do controle pressionando a tecla ALT com a chave de acesso.</span><span class="sxs-lookup"><span data-stu-id="03423-111">The <xref:System.Windows.Forms.Control.Text%2A> property can contain an access key, which allows a user to "click" the control by pressing the ALT key with the access key.</span></span> <span data-ttu-id="03423-112">Para obter mais detalhes, consulte [Como criar chaves de acesso para controles dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md).</span><span class="sxs-lookup"><span data-stu-id="03423-112">For details, see [How to: Create Access Keys for Windows Forms Controls](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md).</span></span> <span data-ttu-id="03423-113">A aparência do texto é controlada pelo <xref:System.Windows.Forms.Control.Font%2A> propriedade e o <xref:System.Windows.Forms.ButtonBase.TextAlign%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="03423-113">The appearance of the text is controlled by the <xref:System.Windows.Forms.Control.Font%2A> property and the <xref:System.Windows.Forms.ButtonBase.TextAlign%2A> property.</span></span>  
  
 <span data-ttu-id="03423-114">O <xref:System.Windows.Forms.Button> controle também pode exibir imagens usando o <xref:System.Windows.Forms.ButtonBase.Image%2A> e <xref:System.Windows.Forms.ButtonBase.ImageList%2A> propriedades.</span><span class="sxs-lookup"><span data-stu-id="03423-114">The <xref:System.Windows.Forms.Button> control can also display images using the <xref:System.Windows.Forms.ButtonBase.Image%2A> and <xref:System.Windows.Forms.ButtonBase.ImageList%2A> properties.</span></span> <span data-ttu-id="03423-115">Para obter mais informações, consulte [Como definir a imagem exibida por um controle dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-set-the-image-displayed-by-a-windows-forms-control.md).</span><span class="sxs-lookup"><span data-stu-id="03423-115">For more information, see [How to: Set the Image Displayed by a Windows Forms Control](../../../../docs/framework/winforms/controls/how-to-set-the-image-displayed-by-a-windows-forms-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03423-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="03423-116">See Also</span></span>  
 <xref:System.Windows.Forms.Button>  
 [<span data-ttu-id="03423-117">Como responder a cliques no botão dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="03423-117">How to: Respond to Windows Forms Button Clicks</span></span>](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)  
 [<span data-ttu-id="03423-118">Formas de selecionar um controle de botão dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="03423-118">Ways to Select a Windows Forms Button Control</span></span>](../../../../docs/framework/winforms/controls/ways-to-select-a-windows-forms-button-control.md)  
 [<span data-ttu-id="03423-119">Como designar um botão dos Windows Forms como o botão Aceitar usando o Designer</span><span class="sxs-lookup"><span data-stu-id="03423-119">How to: Designate a Windows Forms Button as the Accept Button Using the Designer</span></span>](../../../../docs/framework/winforms/controls/designate-a-wf-button-as-the-accept-button-using-the-designer.md)  
 [<span data-ttu-id="03423-120">Como projetar um botão do Windows Forms como o botão Cancelar usando o Designer</span><span class="sxs-lookup"><span data-stu-id="03423-120">How to: Designate a Windows Forms Button as the Cancel Button Using the Designer</span></span>](../../../../docs/framework/winforms/controls/designate-a-wf-button-as-the-cancel-button-using-the-designer.md)  
 [<span data-ttu-id="03423-121">Controle de botão</span><span class="sxs-lookup"><span data-stu-id="03423-121">Button Control</span></span>](../../../../docs/framework/winforms/controls/button-control-windows-forms.md)
