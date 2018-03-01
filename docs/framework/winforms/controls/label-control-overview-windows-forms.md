---
title: "Visão geral do controle de rótulo (Windows Forms)"
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
- Label
helpviewer_keywords:
- images [Windows Forms], displaying in labels
- labels
- Label control [Windows Forms], about Label control
ms.assetid: dcad7f44-11b7-4c55-b0c0-d984ade43d7d
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f68642eb5f996722097976e042006afbf366ae39
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="label-control-overview-windows-forms"></a><span data-ttu-id="406e6-102">Visão geral do controle de rótulo (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="406e6-102">Label Control Overview (Windows Forms)</span></span>
<span data-ttu-id="406e6-103">Windows Forms <xref:System.Windows.Forms.Label> controles são usados para exibir texto ou imagens que não podem ser editadas pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="406e6-103">Windows Forms <xref:System.Windows.Forms.Label> controls are used to display text or images that cannot be edited by the user.</span></span> <span data-ttu-id="406e6-104">Eles são usados para identificar objetos em um formulário — fornecendo uma descrição do que acontecerá se um determinado controle for clicado, por exemplo ou exibindo informações em resposta a um evento em tempo de execução ou processo em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="406e6-104">They are used to identify objects on a form — to provide a description of what a certain control will do if clicked, for example, or to display information in response to a run-time event or process in your application.</span></span> <span data-ttu-id="406e6-105">Por exemplo, você pode usar rótulos para adicionar legendas descritivas em caixas de texto, caixas de listagem, caixas de combinação e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="406e6-105">For example, you can use labels to add descriptive captions to text boxes, list boxes, combo boxes, and so on.</span></span> <span data-ttu-id="406e6-106">Também é possível escrever código para alterar o texto exibido por um rótulo em resposta a eventos em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="406e6-106">You can also write code that changes the text displayed by a label in response to events at run time.</span></span> <span data-ttu-id="406e6-107">Por exemplo, se o aplicativo leva alguns minutos para processar uma alteração, é possível exibir uma mensagem de status de processamento em um rótulo.</span><span class="sxs-lookup"><span data-stu-id="406e6-107">For example, if your application takes a few minutes to process a change, you can display a processing-status message in a label.</span></span>  
  
## <a name="working-with-the-label-control"></a><span data-ttu-id="406e6-108">Trabalhando com o controle de rótulo</span><span class="sxs-lookup"><span data-stu-id="406e6-108">Working with the Label Control</span></span>  
 <span data-ttu-id="406e6-109">Porque o <xref:System.Windows.Forms.Label> controle não pode receber o foco, também pode ser usado para criar chaves de acesso para outros controles.</span><span class="sxs-lookup"><span data-stu-id="406e6-109">Because the <xref:System.Windows.Forms.Label> control cannot receive the focus, it can also be used to create access keys for other controls.</span></span> <span data-ttu-id="406e6-110">Uma tecla de acesso permite que o usuário selecione outro controle pressionando a tecla ALT com a tecla de acesso.</span><span class="sxs-lookup"><span data-stu-id="406e6-110">An access key allows a user to select the other control by pressing the ALT key with the access key.</span></span> <span data-ttu-id="406e6-111">Para obter mais informações, consulte [Criar teclas de acesso para controles dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md) e [Como criar teclas de acesso com controles de rótulo dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-create-access-keys-with-windows-forms-label-controls.md).</span><span class="sxs-lookup"><span data-stu-id="406e6-111">For more information, see [Creating Access Keys for Windows Forms Controls](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md) and [How to: Create Access Keys with Windows Forms Label Controls](../../../../docs/framework/winforms/controls/how-to-create-access-keys-with-windows-forms-label-controls.md).</span></span>  
  
 <span data-ttu-id="406e6-112">A legenda exibida no rótulo está contida no <xref:System.Windows.Forms.Label.Text%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="406e6-112">The caption displayed in the label is contained in the <xref:System.Windows.Forms.Label.Text%2A> property.</span></span> <span data-ttu-id="406e6-113">O <xref:System.Windows.Forms.Label.TextAlign%2A> propriedade permite que você defina o alinhamento do texto dentro do rótulo.</span><span class="sxs-lookup"><span data-stu-id="406e6-113">The <xref:System.Windows.Forms.Label.TextAlign%2A> property allows you to set the alignment of the text within the label.</span></span> <span data-ttu-id="406e6-114">Para obter mais informações, consulte [Como definir o texto exibido por um controle dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md).</span><span class="sxs-lookup"><span data-stu-id="406e6-114">For more information, see [How to: Set the Text Displayed by a Windows Forms Control](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="406e6-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="406e6-115">See Also</span></span>  
 <xref:System.Windows.Forms.Label>  
 [<span data-ttu-id="406e6-116">Como dimensionar um controle de rótulo dos Windows Forms para ajustar-se ao seu conteúdo</span><span class="sxs-lookup"><span data-stu-id="406e6-116">How to: Size a Windows Forms Label Control to Fit Its Contents</span></span>](../../../../docs/framework/winforms/controls/how-to-size-a-windows-forms-label-control-to-fit-its-contents.md)  
 [<span data-ttu-id="406e6-117">Como criar teclas de acesso com controles de rótulo dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="406e6-117">How to: Create Access Keys with Windows Forms Label Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-create-access-keys-with-windows-forms-label-controls.md)
