---
title: 'Como: Definir opções com controles CheckBox do Windows Forms'
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
ms.openlocfilehash: 881996563acef36a1981ca6236c155b8fc56ef0a
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59307295"
---
# <a name="how-to-set-options-with-windows-forms-checkbox-controls"></a>Como: Definir opções com controles CheckBox do Windows Forms
Um Windows Forms <xref:System.Windows.Forms.CheckBox> controle é usado para dar aos usuários True/False ou opções de Sim/não. O controle exibe uma marca de seleção quando ele é selecionado.  
  
### <a name="to-set-options-with-checkbox-controls"></a>Para definir opções com controles CheckBox  
  
1. Examinar o valor da <xref:System.Windows.Forms.CheckBox.Checked%2A> propriedade para determinar seu estado e usar esse valor para definir uma opção.  
  
     No exemplo de código abaixo, quando o <xref:System.Windows.Forms.CheckBox> do controle <xref:System.Windows.Forms.CheckBox.CheckedChanged> é gerado, o formulário <xref:System.Windows.Forms.Control.AllowDrop%2A> estiver definida como `false` se a caixa de seleção estiver marcada. Isso é útil para situações em que você deseja restringir a interação do usuário.  
  
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
- [Como: Responder a cliques CheckBox do Windows Forms](how-to-respond-to-windows-forms-checkbox-clicks.md)
- [Controle de CheckBox](checkbox-control-windows-forms.md)
