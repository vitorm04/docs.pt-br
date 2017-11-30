---
title: "Como designar um botão dos Windows Forms como o botão Cancelar"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- buttons [Windows Forms], cancel buttons
- Button control [Windows Forms], designating as cancel button
ms.assetid: 252f0834-e54b-44d9-96f7-ee5f50e94f2c
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3bbdf2ec4f2353662f1077b9d95966e0a2ebd316
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-designate-a-windows-forms-button-as-the-cancel-button"></a>Como designar um botão dos Windows Forms como o botão Cancelar
Em qualquer formulário do Windows, você pode designar um <xref:System.Windows.Forms.Button> controle botão de cancelamento. Um botão Cancelar é clicado sempre que o usuário pressiona a tecla ESC, independentemente de qual outro controle no formulário tem o foco. Geralmente, este botão é programado para permitir que o usuário sair rapidamente de uma operação sem confirmar qualquer ação.  
  
### <a name="to-designate-the-cancel-button"></a>Para designar o botão Cancelar  
  
1.  Definir o formulário <xref:System.Windows.Forms.Form.CancelButton%2A> propriedade apropriada <xref:System.Windows.Forms.Button> controle.  
  
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
 <xref:System.Windows.Forms.Form.CancelButton%2A>  
 [Visão geral do controle de botão](../../../../docs/framework/winforms/controls/button-control-overview-windows-forms.md)  
 [Formas de selecionar um controle de botão dos Windows Forms](../../../../docs/framework/winforms/controls/ways-to-select-a-windows-forms-button-control.md)  
 [Como responder a cliques no botão dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)  
 [Como designar um botão dos Windows Forms como o botão Aceitar](../../../../docs/framework/winforms/controls/how-to-designate-a-windows-forms-button-as-the-accept-button.md)  
 [Controle de botão](../../../../docs/framework/winforms/controls/button-control-windows-forms.md)
