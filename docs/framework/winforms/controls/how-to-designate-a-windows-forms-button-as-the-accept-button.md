---
title: 'Como: Designar um botão do Windows Forms como o botão Aceitar'
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
ms.openlocfilehash: 8e608bb2cb4635ef1d29fd7a0aff3ac95fcd9af5
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59309817"
---
# <a name="how-to-designate-a-windows-forms-button-as-the-accept-button"></a>Como: Designar um botão do Windows Forms como o botão Aceitar
Em qualquer formulário do Windows, você pode designar um <xref:System.Windows.Forms.Button> controle para ser o botão aceitar, também conhecido como botão padrão. Sempre que o usuário pressiona a tecla ENTER, o botão padrão é clicado, independentemente de qual outro controle no formulário tem o foco.  
  
> [!NOTE]
>  As exceções a isso são quando o controle com o foco é outro botão — nesse caso, o botão com o foco será ser clicado — ou uma caixa de texto de várias linhas, ou um controle personalizado que intercepte a tecla ENTER.  
  
### <a name="to-designate-the-accept-button"></a>Para designar o botão aceitar  
  
1. Definir o formulário <xref:System.Windows.Forms.Form.AcceptButton%2A> propriedade para apropriado <xref:System.Windows.Forms.Button> controle.  
  
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

- <xref:System.Windows.Forms.Form.AcceptButton%2A>
- [Visão geral do controle de botão](button-control-overview-windows-forms.md)
- [Forma de selecionar um controle de botão dos Windows Forms](ways-to-select-a-windows-forms-button-control.md)
- [Como: Responder a cliques no botão do Windows Forms](how-to-respond-to-windows-forms-button-clicks.md)
- [Como: Designar um botão do Windows Forms como o botão Cancelar](how-to-designate-a-windows-forms-button-as-the-cancel-button.md)
- [Controle de botão](button-control-windows-forms.md)
