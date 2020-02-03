---
title: definir opções com controles de caixa de seleção
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- checked
helpviewer_keywords:
- CheckBox control [Windows Forms], checked state
- check boxes [Windows Forms], using to set options
- CheckBox control [Windows Forms], using to set options
ms.assetid: 2ac70498-7e3e-4e07-8901-ccabaeb5fd3e
ms.openlocfilehash: 84198eab42aa02b1bb37fa16a3c4247a37f58a10
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746772"
---
# <a name="how-to-set-options-with-windows-forms-checkbox-controls"></a>Como definir opções com controles CheckBox dos Windows Forms
Um controle de <xref:System.Windows.Forms.CheckBox> Windows Forms é usado para dar aos usuários opções verdadeiro/falso ou sim/não. O controle exibe uma marca de seleção quando ela está selecionada.  
  
### <a name="to-set-options-with-checkbox-controls"></a>Para definir opções com controles de caixa de seleção  
  
1. Examine o valor da propriedade <xref:System.Windows.Forms.CheckBox.Checked%2A> para determinar seu estado e use esse valor para definir uma opção.  
  
     No exemplo de código abaixo, quando o evento de <xref:System.Windows.Forms.CheckBox.CheckedChanged> do controle de <xref:System.Windows.Forms.CheckBox> é gerado, a propriedade <xref:System.Windows.Forms.Control.AllowDrop%2A> do formulário é definida como `false` se a caixa de seleção estiver marcada. Isso é útil para situações em que você deseja restringir a interação do usuário.  
  
    ```vb  
    Private Sub CheckBox1_CheckedChanged(ByVal sender As System.Object, _  
       ByVal e As System.EventArgs) Handles CheckBox1.CheckedChanged  
       ' Determine the CheckState of the check box.  
       If CheckBox1.CheckState = CheckState.Checked Then  
          ' If checked, do not allow items to be dragged onto the form.  
          Me.AllowDrop = False  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void checkBox1_CheckedChanged(object sender, System.EventArgs e)  
    {  
       // Determine the CheckState of the check box.  
       if (checkBox1.CheckState == CheckState.Checked)   
       {  
          // If checked, do not allow items to be dragged onto the form.  
          this.AllowDrop = false;  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       void checkBox1_CheckedChanged(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          // Determine the CheckState of the check box.  
          if (checkBox1->CheckState == CheckState::Checked)   
          {  
             // If checked, do not allow items to be dragged onto the form.  
             this->AllowDrop = false;  
          }  
       }  
    ```  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.CheckBox>
- [Visão geral do controle CheckBox](checkbox-control-overview-windows-forms.md)
- [Como responder a cliques em CheckBox dos Windows Forms](how-to-respond-to-windows-forms-checkbox-clicks.md)
- [Controle CheckBox](checkbox-control-windows-forms.md)
