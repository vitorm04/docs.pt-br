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
ms.openlocfilehash: a91b67df1071c79707bb20a68efb4d5e6f083ae0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59162131"
---
# <a name="textbox-control-overview-windows-forms"></a>Visão geral do controle TextBox (Windows Forms)
Caixas de texto dos Windows Forms são usadas para obter entradas do usuário ou para exibir texto. O controle <xref:System.Windows.Forms.TextBox> geralmente é usado para texto editável, embora também possa ser tornado somente leitura. Caixas de texto podem exibir várias linhas, quebrar o texto para o tamanho do controle e adicionar formatação básica. O <xref:System.Windows.Forms.TextBox> controle fornece um estilo de formato único para o texto exibido ou inserido no controle. Para exibir vários tipos de texto formatado, use o <xref:System.Windows.Forms.RichTextBox> controle. Para obter mais informações, consulte [Visão geral do controle RichTextBox](richtextbox-control-overview-windows-forms.md).  
  
## <a name="working-with-the-textbox-control"></a>Trabalhando com o controle TextBox  
 O texto exibido pelo controle está contido no <xref:System.Windows.Forms.TextBox.Text%2A> propriedade. Por padrão, você pode inserir até 2048 caracteres em uma caixa de texto. Se você definir a <xref:System.Windows.Forms.TextBox.Multiline%2A> propriedade para `true`, você pode inserir até 32 KB de texto. O <xref:System.Windows.Forms.TextBox.Text%2A> propriedade pode ser definida em tempo de design com a janela de propriedades em tempo de execução no código ou pela entrada do usuário em tempo de execução. O conteúdo atual de uma caixa de texto pode ser recuperado em tempo de execução lendo o <xref:System.Windows.Forms.TextBox.Text%2A> propriedade.  
  
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

- <xref:System.Windows.Forms.TextBox>
- [Como: Controlar o ponto de inserção em um controle TextBox do Windows Forms](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [Como: Criar uma caixa de texto de senha com o controle TextBox do Windows Forms](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [Como: Criar uma caixa de texto somente leitura](how-to-create-a-read-only-text-box-windows-forms.md)
- [Como: Inserir aspas em uma cadeia de caracteres](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [Como: Selecionar texto no controle TextBox do Windows Forms](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [Como: Exibir várias linhas no controle TextBox do Windows Forms](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [Controle TextBox](textbox-control-windows-forms.md)
