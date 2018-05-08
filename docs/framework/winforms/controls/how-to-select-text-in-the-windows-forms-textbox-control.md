---
title: Como selecionar texto no controle TextBox dos Windows Forms
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- TextBox control [Windows Forms], selecting text programmatically
- text boxes [Windows Forms], selecting text programmatically
- text [Windows Forms], selecting in text boxes programmatically
ms.assetid: 8c591546-6a01-45c7-8e03-f78431f903b1
ms.openlocfilehash: 8fd1cfb0764d16b86cd639d8266d1cceff874932
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-select-text-in-the-windows-forms-textbox-control"></a>Como selecionar texto no controle TextBox dos Windows Forms
Você pode selecionar texto programaticamente no Windows Forms <xref:System.Windows.Forms.TextBox> controle. Por exemplo, se você criar uma função que pesquisa de texto de uma determinada cadeia de caracteres, poderá selecionar o texto para alertar visualmente o leitor da posição da cadeia de caracteres encontrada.  
  
### <a name="to-select-text-programmatically"></a>Selecionar texto com programação  
  
1.  Definir o <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> propriedade para o início do texto que você deseja selecionar.  
  
     O <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> é um número que indica o ponto de inserção na cadeia de caracteres de texto, com 0, sendo a posição mais à esquerda. Se o <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> propriedade é definida como um valor igual ou maior que o número de caracteres na caixa de texto, o ponto de inserção é posicionado após o último caractere.  
  
2.  Definir o <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> propriedade para o comprimento do texto que você deseja selecionar.  
  
     O <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> propriedade é um valor numérico que define a largura do ponto de inserção. Definindo o <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> para um número maior que 0 faz com que esse número de caracteres a ser selecionado, partindo do ponto de inserção atual.  
  
3.  (Opcional) O texto selecionado por meio de acesso a <xref:System.Windows.Forms.TextBoxBase.SelectedText%2A> propriedade.  
  
     O código a seguir seleciona o conteúdo de um texto da caixa quando o controle <xref:System.Windows.Forms.Control.Enter> evento ocorre. Este exemplo verifica se a caixa de texto tem um valor para o <xref:System.Windows.Forms.TextBox.Text%2A> propriedade que não é `null` ou uma cadeia de caracteres vazia. Quando a caixa de texto recebe o foco, o texto presente nela é selecionado. O manipulador de eventos `TextBox1_Enter` deve ser associado ao controle; para obter mais informações, consulte [Como criar manipuladores de eventos no tempo de execução para Windows Forms](../../../../docs/framework/winforms/how-to-create-event-handlers-at-run-time-for-windows-forms.md).  
  
     Para testar esse exemplo, pressione a tecla Tab até que a caixa de texto receber o foco. Se você clicar na caixa de texto, a seleção dele será cancelada.  
  
    ```vb  
    Private Sub TextBox1_Enter(ByVal sender As Object, ByVal e As System.EventArgs) Handles TextBox1.Enter  
       If (Not String.IsNullOrEmpty(TextBox1.Text)) Then  
          TextBox1.SelectionStart = 0  
          TextBox1.SelectionLength = TextBox1.Text.Length  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void textBox1_Enter(object sender, System.EventArgs e){  
       if (!String.IsNullOrEmpty(textBox1.Text))  
       {  
          textBox1.SelectionStart = 0;  
          textBox1.SelectionLength = textBox1.Text.Length;  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       void textBox1_Enter(System::Object ^ sender,  
          System::EventArgs ^ e) {  
       if (!System::String::IsNullOrEmpty(textBox1->Text))  
       {  
          textBox1->SelectionStart = 0;  
          textBox1->SelectionLength = textBox1->Text->Length;  
       }  
    }  
    ```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.TextBox>  
 [Visão geral do controle TextBox](../../../../docs/framework/winforms/controls/textbox-control-overview-windows-forms.md)  
 [Como controlar o ponto de inserção em um controle TextBox dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)  
 [Como criar uma caixa de texto de senha com o controle TextBox dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)  
 [Como criar uma caixa de texto somente leitura](../../../../docs/framework/winforms/controls/how-to-create-a-read-only-text-box-windows-forms.md)  
 [Como inserir aspas em uma cadeia de caracteres](../../../../docs/framework/winforms/controls/how-to-put-quotation-marks-in-a-string-windows-forms.md)  
 [Como exibir várias linhas no controle TextBox dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)  
 [Controle TextBox](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)
