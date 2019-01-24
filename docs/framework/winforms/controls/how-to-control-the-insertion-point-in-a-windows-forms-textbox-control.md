---
title: 'Como: Controlar o ponto de inserção em um controle TextBox dos Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- TextBox control [Windows Forms], insertion point
- insertion points [Windows Forms], TextBox controls
- text boxes [Windows Forms], controlling insertion point
ms.assetid: 5bee7d34-5121-429e-ab1f-d8ff67bc74c1
ms.openlocfilehash: 6ed49cac8341551dd0900a8468990e314a16e7b6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54660184"
---
# <a name="how-to-control-the-insertion-point-in-a-windows-forms-textbox-control"></a>Como: Controlar o ponto de inserção em um controle TextBox dos Windows Forms
Quando um Windows Forms <xref:System.Windows.Forms.TextBox> controle primeiro recebe o foco, a inserção padrão na caixa de texto está à esquerda do texto existente. O usuário pode mover o ponto de inserção com o teclado ou o mouse. Se a caixa de texto perder e recuperar o foco, o ponto de inserção será sempre o ponto em que o usuário o colocou por último.  
  
 Em alguns casos, esse comportamento pode ser desconcertante para o usuário. Em um aplicativo de processamento de texto, o usuário pode esperar que novos caracteres apareçam após o texto existente. Em um aplicativo de entrada de dados, o usuário pode esperar que novos caracteres substituam a entrada existente. O <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> e <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> propriedades permitem que você modificar o comportamento de acordo com sua finalidade.  
  
### <a name="to-control-the-insertion-point-in-a-textbox-control"></a>Controlar o ponto de inserção em um controle TextBox  
  
1.  Defina o <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> propriedade para um valor apropriado. Zero coloca o ponto de inserção imediatamente à esquerda do primeiro caractere.  
  
2.  (Opcional) Defina o <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> propriedade para o comprimento do texto que você deseja selecionar.  
  
     O código abaixo sempre retorna o ponto de inserção para 0. O manipulador de eventos `TextBox1_Enter` deve ser associado ao controle; para obter mais informações, consulte [Criando manipuladores de eventos no Windows Forms](../../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md).  
  
    ```vb  
    Private Sub TextBox1_Enter(ByVal sender As Object, ByVal e As System.EventArgs) Handles TextBox1.Enter  
       TextBox1.SelectionStart = 0  
       TextBox1.SelectionLength = 0  
    End Sub  
    ```  
  
    ```csharp  
    private void textBox1_Enter(Object sender, System.EventArgs e) {  
       textBox1.SelectionStart = 0;  
       textBox1.SelectionLength = 0;  
    }  
    ```  
  
    ```cpp  
    private:  
       void textBox1_Enter(System::Object ^  sender,  
          System::EventArgs ^  e)  
       {  
          textBox1->SelectionStart = 0;  
          textBox1->SelectionLength = 0;  
       }  
    ```  
  
## <a name="making-the-insertion-point-visible-by-default"></a>Tornando o ponto de inserção visível por padrão  
 O <xref:System.Windows.Forms.TextBox> ponto de inserção é visível por padrão em um novo formulário apenas se o <xref:System.Windows.Forms.TextBox> controle é o primeiro na ordem de tabulação. Caso contrário, o ponto de inserção aparecerá apenas se você conceder a <xref:System.Windows.Forms.TextBox> o foco do teclado ou mouse.  
  
#### <a name="to-make-the-text-box-insertion-point-visible-by-default-on-a-new-form"></a>Tornar a o ponto de inserção da caixa de texto visível por padrão em um novo formulário  
  
-   Defina as <xref:System.Windows.Forms.TextBox> do controle <xref:System.Windows.Forms.Control.TabIndex%2A> propriedade `0`.  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Windows.Forms.TextBox>
- [Visão geral do controle TextBox](../../../../docs/framework/winforms/controls/textbox-control-overview-windows-forms.md)
- [Como: Criar uma caixa de texto de senha com o controle TextBox dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [Como: Criar uma caixa de texto somente leitura](../../../../docs/framework/winforms/controls/how-to-create-a-read-only-text-box-windows-forms.md)
- [Como: Inserir aspas em uma cadeia de caracteres](../../../../docs/framework/winforms/controls/how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [Como: Selecione o texto no controle TextBox de formulários do Windows](../../../../docs/framework/winforms/controls/how-to-select-text-in-the-windows-forms-textbox-control.md)
- [Como: Exibir várias linhas no controle TextBox de formulários do Windows](../../../../docs/framework/winforms/controls/how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [Controle TextBox](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)
