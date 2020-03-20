---
title: responder a cliques em caixa de seleção
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Click event [Windows Forms], CheckBox control
- CheckBox control [Windows Forms], Click events
- events [Windows Forms], Click events
- double-clicks
- check boxes [Windows Forms], responding to events
ms.assetid: c39f901e-8899-43b6-aa31-939cbf7089fb
ms.openlocfilehash: 6ff20c443519446d3804b325924cb3c5cbedea97
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141920"
---
# <a name="how-to-respond-to-windows-forms-checkbox-clicks"></a>Como responder a cliques CheckBox dos Windows Forms
Sempre que um usuário <xref:System.Windows.Forms.CheckBox> clica <xref:System.Windows.Forms.Control.Click> em um controle do Windows Forms, o evento ocorre. Você pode programar seu aplicativo para realizar alguma ação dependendo do estado da caixa de seleção.  
  
### <a name="to-respond-to-checkbox-clicks"></a>Para responder a cliques na caixa de seleção  
  
1. No <xref:System.Windows.Forms.Control.Click> manipulador de eventos, use a <xref:System.Windows.Forms.CheckBox.Checked%2A> propriedade para determinar o estado do controle e realize qualquer ação necessária.  
  
    ```vb  
    Private Sub CheckBox1_Click(ByVal sender As Object, ByVal e As System.EventArgs) Handles CheckBox1.Click  
       ' The CheckBox control's Text property is changed each time the
       ' control is clicked, indicating a checked or unchecked state.  
       If CheckBox1.Checked = True Then  
          CheckBox1.Text = "Checked"  
       Else  
          CheckBox1.Text = "Unchecked"  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void checkBox1_Click(object sender, System.EventArgs e)  
    {  
       // The CheckBox control's Text property is changed each time the
       // control is clicked, indicating a checked or unchecked state.  
       if (checkBox1.Checked)  
       {  
          checkBox1.Text = "Checked";  
       }  
       else  
       {  
          checkBox1.Text = "Unchecked";  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       void checkBox1_CheckedChanged(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          if (checkBox1->Checked)  
          {  
             checkBox1->Text = "Checked";  
          }  
          else  
          {  
             checkBox1->Text = "Unchecked";  
          }  
       }  
    ```  
  
    > [!NOTE]
    > Se o usuário tentar clicar <xref:System.Windows.Forms.CheckBox> duas vezes no controle, cada clique será processado separadamente; ou seja, <xref:System.Windows.Forms.CheckBox> o controle não suporta o evento de duplo clique.  
  
    > [!NOTE]
    > Quando <xref:System.Windows.Forms.CheckBox.AutoCheck%2A> a `true` propriedade é (o padrão), a <xref:System.Windows.Forms.CheckBox> é automaticamente selecionada ou limpa quando é clicada. Caso contrário, você deve <xref:System.Windows.Forms.CheckBox.Checked%2A> definir manualmente a propriedade quando o <xref:System.Windows.Forms.Control.Click> evento ocorrer.  
  
     Você também pode <xref:System.Windows.Forms.CheckBox> usar o controle para determinar um curso de ação.  
  
### <a name="to-determine-a-course-of-action-when-a-check-box-is-clicked"></a>Para determinar um curso de ação quando uma caixa de seleção é clicada  
  
1. Use uma declaração de caso <xref:System.Windows.Forms.CheckBox.CheckState%2A> para consultar o valor da propriedade para determinar um curso de ação. Quando <xref:System.Windows.Forms.CheckBox.ThreeState%2A> a propriedade `true`é <xref:System.Windows.Forms.CheckBox.CheckState%2A> definida para , a propriedade pode retornar três valores possíveis, que representam a caixa sendo verificada, a caixa sendo desmarcada ou um terceiro estado indeterminado em que a caixa é exibida com uma aparência escurecida para indicar que a opção está indisponível.  
  
    ```vb  
    Private Sub CheckBox1_Click(ByVal sender As Object, ByVal e As System.EventArgs) Handles CheckBox1.Click  
       Select Case CheckBox1.CheckState  
          Case CheckState.Checked  
             ' Code for checked state.  
          Case CheckState.Unchecked  
             ' Code for unchecked state.  
          Case CheckState.Indeterminate  
             ' Code for indeterminate state.  
       End Select
    End Sub  
    ```  
  
    ```csharp  
    private void checkBox1_Click(object sender, System.EventArgs e)  
    {  
       switch(checkBox1.CheckState)  
       {  
          case CheckState.Checked:  
             // Code for checked state.  
             break;  
          case CheckState.Unchecked:  
             // Code for unchecked state.  
             break;  
          case CheckState.Indeterminate:  
             // Code for indeterminate state.  
             break;  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       void checkBox1_CheckedChanged(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          switch(checkBox1->CheckState) {  
             case CheckState::Checked:  
                // Code for checked state.  
                break;  
             case CheckState::Unchecked:  
                // Code for unchecked state.  
                break;  
             case CheckState::Indeterminate:  
                // Code for indeterminate state.  
                break;  
          }  
       }  
    ```  
  
    > [!NOTE]
    > Quando <xref:System.Windows.Forms.CheckBox.ThreeState%2A> a propriedade `true`é <xref:System.Windows.Forms.CheckBox.Checked%2A> definida `true` para <xref:System.Windows.Forms.CheckState.Checked> , <xref:System.Windows.Forms.CheckState.Indeterminate>a propriedade retorna para ambos e .  
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.Forms.CheckBox>
- [Visão geral do controle CheckBox](checkbox-control-overview-windows-forms.md)
- [Como definir opções com controles CheckBox dos Windows Forms](how-to-set-options-with-windows-forms-checkbox-controls.md)
- [Controle da caixa de seleção](checkbox-control-windows-forms.md)
