---
title: "Como designar um botão dos Windows Forms como o botão Aceitar"
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
- buttons [Windows Forms], default on Windows Forms
- Accept button on Windows Forms
- Button control [Windows Forms], designating as default
- Windows Forms controls, default button on form
ms.assetid: 22cc9da6-b913-4e04-9554-dee443ac5c3a
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0bf5f8dbf8718cb6a30883395d54c5cbc6bafaff
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
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
