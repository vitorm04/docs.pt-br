---
title: Como criar chaves de acesso para controles dos Windows Forms usando o designer
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [Windows Forms], access keys
- Button control [Windows Forms], access keys
- dialog box controls [Windows Forms], mnemonics
- access keys [Windows Forms], creating for controls
- mnemonics [Windows Forms], adding to dialog box controls
- ampersand character in shortcut key
- Windows Forms controls, access keys
- examples [Windows Forms], controls
- Text property [Windows Forms], specifying access keys for controls
- keyboard shortcuts [Windows Forms], creating for controls
- access keys [Windows Forms], Windows Forms
- ALT key
ms.assetid: 4c374c4c-4ca9-4a68-ac96-9dc3ab0f518a
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ed3bf2aa1e6081ca018f1b4dec98e6304a1aa95c
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-create-access-keys-for-windows-forms-controls-using-the-designer"></a><span data-ttu-id="8afbb-102">Como criar chaves de acesso para controles dos Windows Forms usando o designer</span><span class="sxs-lookup"><span data-stu-id="8afbb-102">How to: Create Access Keys for Windows Forms Controls Using the Designer</span></span>
<span data-ttu-id="8afbb-103">Uma *chave de acesso* é um caractere de sublinhado no texto de um menu, item de menu ou rótulo de um controle como um botão.</span><span class="sxs-lookup"><span data-stu-id="8afbb-103">An *access key* is an underlined character in the text of a menu, menu item, or the label of a control such as a button.</span></span> <span data-ttu-id="8afbb-104">Ela permite que o usuário "clique" em um botão pressionando a tecla ALT em combinação com a chave de acesso predefinida.</span><span class="sxs-lookup"><span data-stu-id="8afbb-104">It enables the user to "click" a button by pressing the ALT key in combination with the predefined access key.</span></span> <span data-ttu-id="8afbb-105">Por exemplo, se um botão executa um procedimento para imprimir um formulário e, portanto, sua propriedade `Text` estiver definida como "Print", adicionar um e comercial (&) antes da letra "P" faz com que a letra "P" seja sublinhada no texto do botão no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="8afbb-105">For example, if a button runs a procedure to print a form, and therefore its `Text` property is set to "Print," adding an ampersand (&) before the letter "P" causes the letter "P" to be underlined in the button text at run time.</span></span> <span data-ttu-id="8afbb-106">O usuário pode executar o comando associado ao botão pressionando ALT+P.</span><span class="sxs-lookup"><span data-stu-id="8afbb-106">The user can run the command associated with the button by pressing ALT+P.</span></span> <span data-ttu-id="8afbb-107">Não é possível ter uma chave de acesso para um controle que não possa receber foco.</span><span class="sxs-lookup"><span data-stu-id="8afbb-107">You cannot have an access key for a control that cannot receive focus.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8afbb-108">As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas.</span><span class="sxs-lookup"><span data-stu-id="8afbb-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="8afbb-109">Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="8afbb-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="8afbb-110">Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="8afbb-110">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-create-an-access-key-for-a-control"></a><span data-ttu-id="8afbb-111">Para criar uma chave de acesso para um controle</span><span class="sxs-lookup"><span data-stu-id="8afbb-111">To create an access key for a control</span></span>  
  
1.  <span data-ttu-id="8afbb-112">Na janela **Propriedades**, defina a propriedade `Text` como uma cadeia de caracteres que inclui um e comercial (&) antes da letra que será a chave de acesso.</span><span class="sxs-lookup"><span data-stu-id="8afbb-112">In the **Properties** window, set the `Text` property to a string that includes an ampersand (&) before the letter that will be the access key.</span></span> <span data-ttu-id="8afbb-113">Por exemplo, para definir a letra "P" como a chave de acesso, digite **&Print** na grade.</span><span class="sxs-lookup"><span data-stu-id="8afbb-113">For example, to set the letter "P" as the access key, type **&Print** into the grid.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8afbb-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8afbb-114">See Also</span></span>  
 <xref:System.Windows.Forms.Button>  
 [<span data-ttu-id="8afbb-115">Como responder a cliques no botão dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8afbb-115">How to: Respond to Windows Forms Button Clicks</span></span>](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)  
 [<span data-ttu-id="8afbb-116">Como definir o texto exibido por um controle dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8afbb-116">How to: Set the Text Displayed by a Windows Forms Control</span></span>](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md)  
 [<span data-ttu-id="8afbb-117">Rotulando controles individuais dos Windows Forms e fornecendo atalhos para eles</span><span class="sxs-lookup"><span data-stu-id="8afbb-117">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
