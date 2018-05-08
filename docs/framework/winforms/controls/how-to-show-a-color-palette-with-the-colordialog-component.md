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
ms.openlocfilehash: ea12fe19b6c8c7464f0820267face8a1d66de784
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-show-a-color-palette-with-the-colordialog-component"></a>Como mostrar uma paleta de cores com o componente ColorDialog
O [ColorDialog](../../../../docs/framework/winforms/controls/colordialog-component-windows-forms.md) componente exibe uma paleta de cores e retorna uma propriedade que contém a cor que o usuário selecionado.  
  
### <a name="to-choose-a-color-using-the-colordialog-component"></a>Para escolher uma cor usando o componente ColorDialog  
  
1.  Exibir a caixa de diálogo usando o <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> método.  
  
2.  Use o <xref:System.Windows.Forms.DialogResult> propriedade para determinar como a caixa de diálogo foi fechada.  
  
3.  Use o <xref:System.Windows.Forms.ColorDialog.Color%2A> propriedade o <xref:System.Windows.Forms.ColorDialog> componente para definir a cor escolhida.  
  
     No exemplo a seguir, o <xref:System.Windows.Forms.Button> do controle <xref:System.Windows.Forms.Control.Click> manipulador de eventos abre um <xref:System.Windows.Forms.ColorDialog> componente. Quando uma cor é escolhido e o usuário clica **Okey**, o <xref:System.Windows.Forms.Button> cor do plano de fundo do controle é definido como a cor escolhida. O exemplo supõe que o formulário tem uma <xref:System.Windows.Forms.Button> controle e um <xref:System.Windows.Forms.ColorDialog> componente.  
  
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
  
     (Visual c# [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) coloque o seguinte código no construtor do formulário para registrar o manipulador de eventos.  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click +=   
       gcnew System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.ColorDialog>  
 [Componente ColorDialog](../../../../docs/framework/winforms/controls/colordialog-component-windows-forms.md)
