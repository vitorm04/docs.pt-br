---
title: Visão geral do controle TextBox (Windows Forms)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- TextBox
helpviewer_keywords:
- TextBox control [Windows Forms], about TextBox controls
- text boxes [Windows Forms], adding
ms.assetid: d1a9c7f5-fa53-480a-a75c-158f8649ea2f
ms.openlocfilehash: b15de762b166fb66ff926706e93cbac6d0c6ba9b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33539861"
---
# <a name="textbox-control-overview-windows-forms"></a>Visão geral do controle TextBox (Windows Forms)
Caixas de texto dos Windows Forms são usadas para obter entradas do usuário ou para exibir texto. O controle <xref:System.Windows.Forms.TextBox> geralmente é usado para texto editável, embora também possa ser tornado somente leitura. Caixas de texto podem exibir várias linhas, quebrar o texto para o tamanho do controle e adicionar formatação básica. O <xref:System.Windows.Forms.TextBox> controle fornece um estilo de formato único para o texto exibido ou inseridos no controle. Para exibir vários tipos de texto formatado, use o <xref:System.Windows.Forms.RichTextBox> controle. Para obter mais informações, consulte [Visão geral do controle RichTextBox](../../../../docs/framework/winforms/controls/richtextbox-control-overview-windows-forms.md).  
  
## <a name="working-with-the-textbox-control"></a>Trabalhando com o controle TextBox  
 O texto exibido pelo controle está contido no <xref:System.Windows.Forms.TextBox.Text%2A> propriedade. Por padrão, você pode inserir até 2048 caracteres em uma caixa de texto. Se você definir o <xref:System.Windows.Forms.TextBox.Multiline%2A> propriedade `true`, você pode inserir até 32 KB de texto. O <xref:System.Windows.Forms.TextBox.Text%2A> propriedade pode ser definida em tempo de design com a janela de propriedades em tempo de execução no código, ou pela entrada do usuário em tempo de execução. O conteúdo atual de uma caixa de texto pode ser recuperado em tempo de execução lendo o <xref:System.Windows.Forms.TextBox.Text%2A> propriedade.  
  
 O exemplo de código a seguir define o texto no controle no tempo de execução. O `InitializeMyControl` procedimento não será executado automaticamente; ele deve ser chamado.  
  
```vb  
Private Sub InitializeMyControl()  
   ' Put some text into the control first.  
   TextBox1.Text = "This is a TextBox control."  
End Sub  
```  
  
```csharp  
private void InitializeMyControl() {  
   // Put some text into the control first.  
   textBox1.Text = "This is a TextBox control.";  
}  
```  
  
```cpp  
private:  
   void InitializeMyControl()  
   {  
      // Put some text into the control first.  
      textBox1->Text = "This is a TextBox control.";  
   }  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.TextBox>  
 [Como controlar o ponto de inserção em um controle TextBox dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)  
 [Como criar uma caixa de texto de senha com o controle TextBox dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)  
 [Como criar uma caixa de texto somente leitura](../../../../docs/framework/winforms/controls/how-to-create-a-read-only-text-box-windows-forms.md)  
 [Como inserir aspas em uma cadeia de caracteres](../../../../docs/framework/winforms/controls/how-to-put-quotation-marks-in-a-string-windows-forms.md)  
 [Como selecionar texto no controle TextBox dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-select-text-in-the-windows-forms-textbox-control.md)  
 [Como exibir várias linhas no controle TextBox dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)  
 [Controle TextBox](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)
