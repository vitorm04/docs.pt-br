---
title: Designar um botão como o botão Cancelar
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- buttons [Windows Forms], cancel buttons
- Button control [Windows Forms], designating as cancel button
ms.assetid: 252f0834-e54b-44d9-96f7-ee5f50e94f2c
ms.openlocfilehash: 123b3e275065efadd24815320ea7d855808e60b9
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743254"
---
# <a name="how-to-designate-a-windows-forms-button-as-the-cancel-button"></a>Como designar um botão dos Windows Forms como o botão Cancelar
Em qualquer formulário do Windows, você pode designar um controle de <xref:System.Windows.Forms.Button> para ser o botão Cancelar. Um botão Cancelar é clicado sempre que o usuário pressiona a tecla ESC, independentemente de qual outro controle no formulário tem o foco. Esse botão geralmente é programado para permitir que o usuário saia rapidamente de uma operação sem confirmar qualquer ação.  
  
### <a name="to-designate-the-cancel-button"></a>Para designar o botão Cancelar  
  
1. Defina a propriedade <xref:System.Windows.Forms.Form.CancelButton%2A> do formulário como o controle de <xref:System.Windows.Forms.Button> apropriado.  
  
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
  
## <a name="see-also"></a>Veja também

- <xref:System.Windows.Forms.Form.CancelButton%2A>
- [Visão geral do controle de botão](button-control-overview-windows-forms.md)
- [Formas de selecionar um controle de botão dos Windows Forms](ways-to-select-a-windows-forms-button-control.md)
- [Como responder a cliques no botão dos Windows Forms](how-to-respond-to-windows-forms-button-clicks.md)
- [Como designar um botão dos Windows Forms como o botão Aceitar](how-to-designate-a-windows-forms-button-as-the-accept-button.md)
- [Controle de botão](button-control-windows-forms.md)
