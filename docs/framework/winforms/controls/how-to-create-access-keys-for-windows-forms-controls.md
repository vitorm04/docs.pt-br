---
title: 'Como: Criar chaves de acesso para controles dos Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- controls [Windows Forms], access keys
- Button control [Windows Forms], access keys
- dialog box controls [Windows Forms], mnemonics
- access keys [Windows Forms], creating for controls
- mnemonics [Windows Forms], adding to dialog box controls
- mnemonics
- ampersand character in shortcut key
- Windows Forms controls, access keys
- examples [Windows Forms], controls
- Text property [Windows Forms], specifying access keys for controls
- keyboard shortcuts [Windows Forms], creating for controls
- access keys [Windows Forms], Windows Forms
- ALT key
ms.assetid: 4faa0991-28ec-4eca-91db-51dc2cd6a7ac
ms.openlocfilehash: 5713bc9fa02e6122cc42348160dbe9315e023bc4
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57707996"
---
# <a name="how-to-create-access-keys-for-windows-forms-controls"></a><span data-ttu-id="24621-102">Como: Criar chaves de acesso para controles dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="24621-102">How to: Create Access Keys for Windows Forms Controls</span></span>
<span data-ttu-id="24621-103">Uma *chave de acesso* é um caractere de sublinhado no texto de um menu, item de menu ou rótulo de um controle como um botão.</span><span class="sxs-lookup"><span data-stu-id="24621-103">An *access key* is an underlined character in the text of a menu, menu item, or the label of a control such as a button.</span></span> <span data-ttu-id="24621-104">Com uma chave de acesso, o usuário pode "clicar" um botão pressionando a tecla ALT em combinação com a chave de acesso predefinidas.</span><span class="sxs-lookup"><span data-stu-id="24621-104">With an access key, the user can "click" a button by pressing the ALT key in combination with the predefined access key.</span></span> <span data-ttu-id="24621-105">Por exemplo, se um botão executa um procedimento para imprimir um formulário e, portanto, seu `Text` estiver definida como "Print", adicionando um e comercial antes que a letra "P" faz com que a letra "P" seja sublinhada no texto do botão no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="24621-105">For example, if a button runs a procedure to print a form, and therefore its `Text` property is set to "Print," adding an ampersand before the letter "P" causes the letter "P" to be underlined in the button text at run time.</span></span> <span data-ttu-id="24621-106">O usuário pode executar o comando associado ao botão pressionando ALT+P.</span><span class="sxs-lookup"><span data-stu-id="24621-106">The user can run the command associated with the button by pressing ALT+P.</span></span> <span data-ttu-id="24621-107">Não é possível ter uma chave de acesso para um controle que não possa receber foco.</span><span class="sxs-lookup"><span data-stu-id="24621-107">You cannot have an access key for a control that cannot receive focus.</span></span>  
  
### <a name="to-create-an-access-key-for-a-control"></a><span data-ttu-id="24621-108">Para criar uma chave de acesso para um controle</span><span class="sxs-lookup"><span data-stu-id="24621-108">To create an access key for a control</span></span>  
  
1.  <span data-ttu-id="24621-109">Defina o `Text` propriedade como uma cadeia de caracteres que inclua um e comercial (&) antes da letra que será o atalho.</span><span class="sxs-lookup"><span data-stu-id="24621-109">Set the `Text` property to a string that includes an ampersand (&) before the letter that will be the shortcut.</span></span>  
  
    ```vb  
    ' Set the letter "P" as an access key.  
    Button1.Text = "&Print"  
    ```  
  
    ```csharp  
    // Set the letter "P" as an access key.  
    button1.Text = "&Print";  
    ```  
  
    ```cpp  
    // Set the letter "P" as an access key.  
    button1->Text = "&Print";  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="24621-110">Para incluir um e comercial em uma legenda sem criar uma chave de acesso, inclua duas "e" comercial (& &).</span><span class="sxs-lookup"><span data-stu-id="24621-110">To include an ampersand in a caption without creating an access key, include two ampersands (&&).</span></span> <span data-ttu-id="24621-111">Um único e comercial é exibido na legenda e caracteres não é sublinhado.</span><span class="sxs-lookup"><span data-stu-id="24621-111">A single ampersand is displayed in the caption and no characters are underlined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24621-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="24621-112">See also</span></span>
- <xref:System.Windows.Forms.Button>
- [<span data-ttu-id="24621-113">Como: Responder a cliques de botão do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="24621-113">How to: Respond to Windows Forms Button Clicks</span></span>](how-to-respond-to-windows-forms-button-clicks.md)
- [<span data-ttu-id="24621-114">Como: Definir o texto exibido pelo controle de um Windows Forms</span><span class="sxs-lookup"><span data-stu-id="24621-114">How to: Set the Text Displayed by a Windows Forms Control</span></span>](how-to-set-the-text-displayed-by-a-windows-forms-control.md)
- [<span data-ttu-id="24621-115">Rotulando controles individuais dos Windows Forms e fornecendo atalhos para eles</span><span class="sxs-lookup"><span data-stu-id="24621-115">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
