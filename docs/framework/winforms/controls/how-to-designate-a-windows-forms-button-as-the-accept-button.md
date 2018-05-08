---
title: Como designar um botão dos Windows Forms como o botão Aceitar
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
ms.openlocfilehash: a69964b83e9948a844483725616a150234a38c97
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-designate-a-windows-forms-button-as-the-accept-button"></a>Como designar um botão dos Windows Forms como o botão Aceitar
Em qualquer formulário do Windows, você pode designar um <xref:System.Windows.Forms.Button> controle botão aceitar, também conhecido como o botão padrão. Sempre que o usuário pressiona a tecla ENTER, o botão padrão é clicado, independentemente de qual outro controle no formulário tem o foco.  
  
> [!NOTE]
>  As exceções são quando o controle com foco é outro botão — nesse caso, o botão com o foco será clicado — ou uma caixa de texto de várias linhas, ou um controle personalizado que intercepta a tecla ENTER.  
  
### <a name="to-designate-the-accept-button"></a>Para designar o botão aceitar  
  
1.  Definir o formulário <xref:System.Windows.Forms.Form.AcceptButton%2A> propriedade apropriada <xref:System.Windows.Forms.Button> controle.  
  
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
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.Form.AcceptButton%2A>  
 [Visão geral do controle de botão](../../../../docs/framework/winforms/controls/button-control-overview-windows-forms.md)  
 [Formas de selecionar um controle de botão dos Windows Forms](../../../../docs/framework/winforms/controls/ways-to-select-a-windows-forms-button-control.md)  
 [Como responder a cliques no botão dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)  
 [Como designar um botão dos Windows Forms como o botão Cancelar](../../../../docs/framework/winforms/controls/how-to-designate-a-windows-forms-button-as-the-cancel-button.md)  
 [Controle de botão](../../../../docs/framework/winforms/controls/button-control-windows-forms.md)
