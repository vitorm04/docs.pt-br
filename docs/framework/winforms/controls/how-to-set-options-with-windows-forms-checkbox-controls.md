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
ms.openlocfilehash: 00b467836d8e60aeee51a010a6384abf7dd73c56
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141842"
---
# <a name="how-to-set-options-with-windows-forms-checkbox-controls"></a>Como definir opções com controles CheckBox dos Windows Forms
Um controle <xref:System.Windows.Forms.CheckBox> do Windows Forms é usado para dar aos usuários opções True/False ou Yes/No. O controle exibe uma marca de seleção quando é selecionada.  
  
### <a name="to-set-options-with-checkbox-controls"></a>Para definir opções com controles do CheckBox  
  
1. Examine o valor <xref:System.Windows.Forms.CheckBox.Checked%2A> da propriedade para determinar seu estado e use esse valor para definir uma opção.  
  
     Na amostra de código <xref:System.Windows.Forms.CheckBox> abaixo, <xref:System.Windows.Forms.CheckBox.CheckedChanged> quando o evento do controle <xref:System.Windows.Forms.Control.AllowDrop%2A> é levantado, a propriedade do formulário é definida para `false` se a caixa de seleção for verificada. Isso é útil para situações em que você deseja restringir a interação do usuário.  
  
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
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.Forms.CheckBox>
- [Visão geral do controle CheckBox](checkbox-control-overview-windows-forms.md)
- [Como responder a cliques em CheckBox dos Windows Forms](how-to-respond-to-windows-forms-checkbox-clicks.md)
- [Controle da caixa de seleção](checkbox-control-windows-forms.md)
