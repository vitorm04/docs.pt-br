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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62010716"
---
# <a name="how-to-designate-a-windows-forms-button-as-the-cancel-button"></a>Como: Designar um botão do Windows Forms como o botão Cancelar
Em qualquer formulário do Windows, você pode designar um <xref:System.Windows.Forms.Button> controle para ser o botão Cancelar. Um botão Cancelar é clicado sempre que o usuário pressiona a tecla ESC, independentemente de qual outro controle no formulário tem o foco. Geralmente, este botão é programado para permitir que o usuário sair rapidamente de uma operação sem se comprometer com qualquer ação.  
  
### <a name="to-designate-the-cancel-button"></a>Para designar um botão Cancelar  
  
1. Definir o formulário <xref:System.Windows.Forms.Form.CancelButton%2A> propriedade para apropriado <xref:System.Windows.Forms.Button> controle.  
  
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
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.Form.CancelButton%2A>
- [Visão geral do controle de botão](button-control-overview-windows-forms.md)
- [Formas de selecionar um controle de botão dos Windows Forms](ways-to-select-a-windows-forms-button-control.md)
- [Como: Responder a cliques de botão do Windows Forms](how-to-respond-to-windows-forms-button-clicks.md)
- [Como: Designar um botão dos Windows Forms como botão aceitar](how-to-designate-a-windows-forms-button-as-the-accept-button.md)
- [Controle de botão](button-control-windows-forms.md)
