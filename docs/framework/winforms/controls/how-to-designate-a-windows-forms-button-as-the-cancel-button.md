---
title: 'Como: Designar um botão do Windows Forms como o botão Cancelar'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- buttons [Windows Forms], cancel buttons
- Button control [Windows Forms], designating as cancel button
ms.assetid: 252f0834-e54b-44d9-96f7-ee5f50e94f2c
ms.openlocfilehash: ad95a527ea72858cc106c87d8712110e018e97b2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59231429"
---
# <a name="how-to-designate-a-windows-forms-button-as-the-cancel-button"></a><span data-ttu-id="3d860-102">Como: Designar um botão do Windows Forms como o botão Cancelar</span><span class="sxs-lookup"><span data-stu-id="3d860-102">How to: Designate a Windows Forms Button as the Cancel Button</span></span>
<span data-ttu-id="3d860-103">Em qualquer formulário do Windows, você pode designar um <xref:System.Windows.Forms.Button> controle para ser o botão Cancelar.</span><span class="sxs-lookup"><span data-stu-id="3d860-103">On any Windows Form, you can designate a <xref:System.Windows.Forms.Button> control to be the cancel button.</span></span> <span data-ttu-id="3d860-104">Um botão Cancelar é clicado sempre que o usuário pressiona a tecla ESC, independentemente de qual outro controle no formulário tem o foco.</span><span class="sxs-lookup"><span data-stu-id="3d860-104">A cancel button is clicked whenever the user presses the ESC key, regardless of which other control on the form has the focus.</span></span> <span data-ttu-id="3d860-105">Geralmente, este botão é programado para permitir que o usuário sair rapidamente de uma operação sem se comprometer com qualquer ação.</span><span class="sxs-lookup"><span data-stu-id="3d860-105">Such a button is usually programmed to enable the user to quickly exit an operation without committing to any action.</span></span>  
  
### <a name="to-designate-the-cancel-button"></a><span data-ttu-id="3d860-106">Para designar um botão Cancelar</span><span class="sxs-lookup"><span data-stu-id="3d860-106">To designate the cancel button</span></span>  
  
1.  <span data-ttu-id="3d860-107">Definir o formulário <xref:System.Windows.Forms.Form.CancelButton%2A> propriedade para apropriado <xref:System.Windows.Forms.Button> controle.</span><span class="sxs-lookup"><span data-stu-id="3d860-107">Set the form's <xref:System.Windows.Forms.Form.CancelButton%2A> property to the appropriate <xref:System.Windows.Forms.Button> control.</span></span>  
  
    ```vb  
    Private Sub SetCancelButton(ByVal myCancelBtn As Button)  
       Me.CancelButton = myCancelBtn  
    End Sub  
    ```  
  
    ```csharp  
    private void SetCancelButton(Button myCancelBtn)  
    {  
       this.CancelButton = myCancelBtn;  
    }  
    ```  
  
    ```cpp  
    private:  
       void SetCancelButton(Button ^ myCancelBtn)  
       {  
          this->CancelButton = myCancelBtn;  
       }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="3d860-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3d860-108">See also</span></span>

- <xref:System.Windows.Forms.Form.CancelButton%2A>
- [<span data-ttu-id="3d860-109">Visão geral do controle de botão</span><span class="sxs-lookup"><span data-stu-id="3d860-109">Button Control Overview</span></span>](button-control-overview-windows-forms.md)
- [<span data-ttu-id="3d860-110">Forma de selecionar um controle de botão dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3d860-110">Ways to Select a Windows Forms Button Control</span></span>](ways-to-select-a-windows-forms-button-control.md)
- [<span data-ttu-id="3d860-111">Como: Responder a cliques no botão do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3d860-111">How to: Respond to Windows Forms Button Clicks</span></span>](how-to-respond-to-windows-forms-button-clicks.md)
- [<span data-ttu-id="3d860-112">Como: Designar um botão do Windows Forms como o botão Aceitar</span><span class="sxs-lookup"><span data-stu-id="3d860-112">How to: Designate a Windows Forms Button as the Accept Button</span></span>](how-to-designate-a-windows-forms-button-as-the-accept-button.md)
- [<span data-ttu-id="3d860-113">Controle de botão</span><span class="sxs-lookup"><span data-stu-id="3d860-113">Button Control</span></span>](button-control-windows-forms.md)
