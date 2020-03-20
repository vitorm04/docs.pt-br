---
title: Designe um botão como o botão aceitar
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- buttons [Windows Forms], default on Windows Forms
- Accept button on Windows Forms
- Button control [Windows Forms], designating as default
- Windows Forms controls, default button on form
ms.assetid: 22cc9da6-b913-4e04-9554-dee443ac5c3a
ms.openlocfilehash: ca5f691fb26db5c4adcb48405c9600b54827104c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142141"
---
# <a name="how-to-designate-a-windows-forms-button-as-the-accept-button"></a>Como designar um botão dos Windows Forms como o botão Aceitar
Em qualquer formulário do Windows, você pode designar um <xref:System.Windows.Forms.Button> controle para ser o botão de aceitação, também conhecido como botão padrão. Sempre que o usuário pressiona a tecla ENTER, o botão padrão é clicado independentemente de qual outro controle no formulário tenha o foco.  
  
> [!NOTE]
> As exceções para isso são quando o controle com foco é outro botão — nesse caso, o botão com o foco será clicado — ou uma caixa de texto multilinha, ou um controle personalizado que prende a tecla ENTER.  
  
### <a name="to-designate-the-accept-button"></a>Para designar o botão aceitar  
  
1. Defina a <xref:System.Windows.Forms.Form.AcceptButton%2A> propriedade do <xref:System.Windows.Forms.Button> formulário para o controle apropriado.  
  
    ```vb  
    Private Sub SetDefault(ByVal myDefaultBtn As Button)  
      Me.AcceptButton = myDefaultBtn
    End Sub  
    ```  
  
    ```csharp  
    private void SetDefault(Button myDefaultBtn)  
    {  
       this.AcceptButton = myDefaultBtn;  
    }  
    ```  
  
    ```cpp  
    private:  
       void SetDefault(Button ^ myDefaultBtn)  
       {  
          this->AcceptButton = myDefaultBtn;  
       }  
    ```  
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.Forms.Form.AcceptButton%2A>
- [Visão geral do controle Button](button-control-overview-windows-forms.md)
- [Forma de selecionar um controle de botão dos Windows Forms](ways-to-select-a-windows-forms-button-control.md)
- [Como responder a cliques no botão dos Windows Forms](how-to-respond-to-windows-forms-button-clicks.md)
- [Como designar um botão dos Windows Forms como o botão Cancelar](how-to-designate-a-windows-forms-button-as-the-cancel-button.md)
- [Controle de botão](button-control-windows-forms.md)
