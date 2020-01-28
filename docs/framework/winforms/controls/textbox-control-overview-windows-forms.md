---
title: Visão geral do controle TextBox
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
ms.openlocfilehash: 06ab460d720d17331881b5ba653263160eaf3cb3
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742797"
---
# <a name="textbox-control-overview-windows-forms"></a>Visão geral do controle TextBox (Windows Forms)
Caixas de texto dos Windows Forms são usadas para obter entradas do usuário ou para exibir texto. O controle <xref:System.Windows.Forms.TextBox> geralmente é usado para texto editável, embora também possa ser tornado somente leitura. Caixas de texto podem exibir várias linhas, quebrar o texto para o tamanho do controle e adicionar formatação básica. O controle <xref:System.Windows.Forms.TextBox> fornece um estilo de formato único para texto exibido ou inserido no controle. Para exibir vários tipos de texto formatado, use o controle <xref:System.Windows.Forms.RichTextBox>. Para obter mais informações, consulte [Visão geral do controle RichTextBox](richtextbox-control-overview-windows-forms.md).  
  
## <a name="working-with-the-textbox-control"></a>Trabalhando com o controle TextBox  
 O texto exibido pelo controle está contido na propriedade <xref:System.Windows.Forms.TextBox.Text%2A>. Por padrão, você pode inserir até 2048 caracteres em uma caixa de texto. Se você definir a propriedade <xref:System.Windows.Forms.TextBox.Multiline%2A> como `true`, poderá inserir até 32 KB de texto. A propriedade <xref:System.Windows.Forms.TextBox.Text%2A> pode ser definida em tempo de design com a janela Propriedades, em tempo de execução no código ou pela entrada do usuário em tempo de execução. O conteúdo atual de uma caixa de texto pode ser recuperado em tempo de execução, lendo a propriedade <xref:System.Windows.Forms.TextBox.Text%2A>.  
  
 O exemplo de código a seguir define o texto no controle no tempo de execução. O procedimento de `InitializeMyControl` não será executado automaticamente; Ele deve ser chamado.  
  
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
  
## <a name="see-also"></a>Veja também

- <xref:System.Windows.Forms.TextBox>
- [Como controlar o ponto de inserção em um controle TextBox dos Windows Forms](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [Como criar uma caixa de texto de senha com o controle TextBox dos Windows Forms](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [Como criar uma caixa de texto somente leitura](how-to-create-a-read-only-text-box-windows-forms.md)
- [Como inserir aspas em uma cadeia de caracteres](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [Como selecionar texto no controle TextBox dos Windows Forms](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [Como exibir várias linhas no controle TextBox dos Windows Forms](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [Controle TextBox](textbox-control-windows-forms.md)
