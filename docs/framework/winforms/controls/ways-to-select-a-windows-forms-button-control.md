---
title: Maneiras de selecionar um controle de botão
ms.date: 03/30/2017
helpviewer_keywords:
- Button control [Windows Forms], selecting
ms.assetid: fe2fc058-5118-4f70-b264-6147d64a7a8d
ms.openlocfilehash: 145166d182f1ec51068ab3e0c23c12b471b69231
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740008"
---
# <a name="ways-to-select-a-windows-forms-button-control"></a><span data-ttu-id="175a8-102">Forma de selecionar um controle de botão dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="175a8-102">Ways to Select a Windows Forms Button Control</span></span>
<span data-ttu-id="175a8-103">Um botão dos Windows Forms pode ser selecionado das seguintes maneiras:</span><span class="sxs-lookup"><span data-stu-id="175a8-103">A Windows Forms button can be selected in the following ways:</span></span>  
  
- <span data-ttu-id="175a8-104">Use um mouse para clicar no botão.</span><span class="sxs-lookup"><span data-stu-id="175a8-104">Use a mouse to click the button.</span></span>  
  
- <span data-ttu-id="175a8-105">Invocar o evento <xref:System.Windows.Forms.Control.Click> do botão no código.</span><span class="sxs-lookup"><span data-stu-id="175a8-105">Invoke the button's <xref:System.Windows.Forms.Control.Click> event in code.</span></span>  
  
- <span data-ttu-id="175a8-106">Mova o foco para o botão pressionando a tecla TAB e, em seguida, escolha o botão pressionando a barra de espaços ou ENTER.</span><span class="sxs-lookup"><span data-stu-id="175a8-106">Move the focus to the button by pressing the TAB key, and then choose the button by pressing the SPACEBAR or ENTER.</span></span>  
  
- <span data-ttu-id="175a8-107">Pressione a tecla de acesso (ALT + a letra sublinhada) para o botão.</span><span class="sxs-lookup"><span data-stu-id="175a8-107">Press the access key (ALT + the underlined letter) for the button.</span></span> <span data-ttu-id="175a8-108">Para obter mais informações sobre chaves de acesso, consulte [Como criar chaves de acesso para controles dos Windows Forms](how-to-create-access-keys-for-windows-forms-controls.md).</span><span class="sxs-lookup"><span data-stu-id="175a8-108">For more information about access keys, see [How to: Create Access Keys for Windows Forms Controls](how-to-create-access-keys-for-windows-forms-controls.md).</span></span>  
  
- <span data-ttu-id="175a8-109">Se o botão for o botão "Aceitar" do formulário, pressionar ENTER seleciona o botão, mesmo se outro controle tiver o foco — exceto se o outro controle for outro botão, uma caixa de texto de várias linhas ou um controle personalizado que intercepte a tecla enter.</span><span class="sxs-lookup"><span data-stu-id="175a8-109">If the button is the "accept" button of the form, pressing ENTER chooses the button, even if another control has the focus — except if that other control is another button, a multi-line text box, or a custom control that traps the enter key.</span></span>  
  
- <span data-ttu-id="175a8-110">Se o botão for o botão "Cancelar" do formulário, pressionar ESC seleciona o botão, mesmo se outro controle tiver o foco.</span><span class="sxs-lookup"><span data-stu-id="175a8-110">If the button is the "cancel" button of the form, pressing ESC chooses the button, even if another control has the focus.</span></span>  
  
- <span data-ttu-id="175a8-111">Chame o método <xref:System.Windows.Forms.Button.PerformClick%2A> para selecionar o botão programaticamente.</span><span class="sxs-lookup"><span data-stu-id="175a8-111">Call the <xref:System.Windows.Forms.Button.PerformClick%2A> method to select the button programmatically.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="175a8-112">Veja também</span><span class="sxs-lookup"><span data-stu-id="175a8-112">See also</span></span>

- [<span data-ttu-id="175a8-113">Visão geral do controle de botão</span><span class="sxs-lookup"><span data-stu-id="175a8-113">Button Control Overview</span></span>](button-control-overview-windows-forms.md)
- [<span data-ttu-id="175a8-114">Como responder a cliques no botão dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="175a8-114">How to: Respond to Windows Forms Button Clicks</span></span>](how-to-respond-to-windows-forms-button-clicks.md)
- [<span data-ttu-id="175a8-115">Controle de botão</span><span class="sxs-lookup"><span data-stu-id="175a8-115">Button Control</span></span>](button-control-windows-forms.md)
