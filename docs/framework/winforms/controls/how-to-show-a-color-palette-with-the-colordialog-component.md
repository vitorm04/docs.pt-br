---
title: Como mostrar uma paleta de cores com o componente ColorDialog
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- palettes [Windows Forms], showing color
- color dialog box [Windows Forms], showing color palettes
- colors [Windows Forms], allowing users to select
- color palettes [Windows Forms], dialog box
- ColorDialog component [Windows Forms], showing color palettes
- color palettes [Windows Forms], showing in ColorDialog component
- colors [Windows Forms], showing palettes
ms.assetid: ee050f61-dbc8-4436-ba22-51360981ab48
ms.openlocfilehash: 0406ef7a32678bd149c0024348a7adf1f0b72926
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141777"
---
# <a name="how-to-show-a-color-palette-with-the-colordialog-component"></a>Como mostrar uma paleta de cores com o componente ColorDialog
O componente [ColorDialog](colordialog-component-windows-forms.md) exibe uma paleta de cores e retorna uma propriedade contendo a cor que o usuário selecionou.  
  
### <a name="to-choose-a-color-using-the-colordialog-component"></a>Para escolher uma cor usando o componente ColorDialog  
  
1. Exibir a caixa <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> de diálogo usando o método.  
  
2. Use <xref:System.Windows.Forms.DialogResult> a propriedade para determinar como a caixa de diálogo foi fechada.  
  
3. Use <xref:System.Windows.Forms.ColorDialog.Color%2A> a propriedade <xref:System.Windows.Forms.ColorDialog> do componente para definir a cor escolhida.  
  
     No exemplo abaixo, <xref:System.Windows.Forms.Button> o <xref:System.Windows.Forms.Control.Click> manipulador de <xref:System.Windows.Forms.ColorDialog> eventos do controle abre um componente. Quando uma cor é escolhida e o <xref:System.Windows.Forms.Button> usuário clica **em OK,** a cor de fundo do controle é definida como a cor escolhida. O exemplo pressupõe <xref:System.Windows.Forms.Button> que seu <xref:System.Windows.Forms.ColorDialog> formulário tenha um controle e um componente.  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, _  
    ByVal e As System.EventArgs) Handles Button1.Click  
       If ColorDialog1.ShowDialog() = DialogResult.OK Then  
          Button1.BackColor = ColorDialog1.Color  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       if(colorDialog1.ShowDialog() == DialogResult.OK)  
       {  
          button1.BackColor = colorDialog1.Color;  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       void button1_Click(System::Object ^ sender,
          System::EventArgs ^ e)  
       {  
          if(colorDialog1->ShowDialog() == DialogResult::OK)  
          {  
             button1->BackColor = colorDialog1->Color;  
          }  
       }  
    ```  
  
     (Visual C#, Visual C++) Coloque o seguinte código no construtor do formulário para registrar o manipulador de eventos.  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click +=
       gcnew System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.Forms.ColorDialog>
- [Componente ColorDialog](colordialog-component-windows-forms.md)
