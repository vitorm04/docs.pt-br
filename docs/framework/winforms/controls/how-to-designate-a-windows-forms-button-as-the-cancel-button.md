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
ms.openlocfilehash: 8170190145e76a86f5343bc42b39be7fb9d61a0f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59344137"
---
# <a name="how-to-designate-a-windows-forms-button-as-the-cancel-button"></a><span data-ttu-id="0a31f-102">Como: Designar um botão do Windows Forms como o botão Cancelar</span><span class="sxs-lookup"><span data-stu-id="0a31f-102">How to: Designate a Windows Forms Button as the Cancel Button</span></span>
<span data-ttu-id="0a31f-103">Em qualquer formulário do Windows, você pode designar um <xref:System.Windows.Forms.Button> controle para ser o botão Cancelar.</span><span class="sxs-lookup"><span data-stu-id="0a31f-103">On any Windows Form, you can designate a <xref:System.Windows.Forms.Button> control to be the cancel button.</span></span> <span data-ttu-id="0a31f-104">Um botão Cancelar é clicado sempre que o usuário pressiona a tecla ESC, independentemente de qual outro controle no formulário tem o foco.</span><span class="sxs-lookup"><span data-stu-id="0a31f-104">A cancel button is clicked whenever the user presses the ESC key, regardless of which other control on the form has the focus.</span></span> <span data-ttu-id="0a31f-105">Geralmente, este botão é programado para permitir que o usuário sair rapidamente de uma operação sem se comprometer com qualquer ação.</span><span class="sxs-lookup"><span data-stu-id="0a31f-105">Such a button is usually programmed to enable the user to quickly exit an operation without committing to any action.</span></span>  
  
### <a name="to-designate-the-cancel-button"></a><span data-ttu-id="0a31f-106">Para designar um botão Cancelar</span><span class="sxs-lookup"><span data-stu-id="0a31f-106">To designate the cancel button</span></span>  
  
1. <span data-ttu-id="0a31f-107">Definir o formulário <xref:System.Windows.Forms.Form.CancelButton%2A> propriedade para apropriado <xref:System.Windows.Forms.Button> controle.</span><span class="sxs-lookup"><span data-stu-id="0a31f-107">Set the form's <xref:System.Windows.Forms.Form.CancelButton%2A> property to the appropriate <xref:System.Windows.Forms.Button> control.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0a31f-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0a31f-108">See also</span></span>

- <xref:System.Windows.Forms.Form.CancelButton%2A>
- [<span data-ttu-id="0a31f-109">Visão geral do controle de botão</span><span class="sxs-lookup"><span data-stu-id="0a31f-109">Button Control Overview</span></span>](button-control-overview-windows-forms.md)
- [<span data-ttu-id="0a31f-110">Formas de selecionar um controle de botão dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0a31f-110">Ways to Select a Windows Forms Button Control</span></span>](ways-to-select-a-windows-forms-button-control.md)
- [<span data-ttu-id="0a31f-111">Como: Responder a cliques de botão do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0a31f-111">How to: Respond to Windows Forms Button Clicks</span></span>](how-to-respond-to-windows-forms-button-clicks.md)
- [<span data-ttu-id="0a31f-112">Como: Designar um botão dos Windows Forms como botão aceitar</span><span class="sxs-lookup"><span data-stu-id="0a31f-112">How to: Designate a Windows Forms Button as the Accept Button</span></span>](how-to-designate-a-windows-forms-button-as-the-accept-button.md)
- [<span data-ttu-id="0a31f-113">Controle de botão</span><span class="sxs-lookup"><span data-stu-id="0a31f-113">Button Control</span></span>](button-control-windows-forms.md)
