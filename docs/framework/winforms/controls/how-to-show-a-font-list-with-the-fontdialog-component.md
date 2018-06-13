---
title: Como mostrar uma lista de fontes ao componente FontDialog
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- fonts [Windows Forms], showing list
- FontDialog component [Windows Forms]
- fonts [Windows Forms], attributes
- Font property [Windows Forms], setting with FontDialog component
- Font dialog box [Windows Forms], displaying
- fonts [Windows Forms], selecting
ms.assetid: 35692c1b-0937-4b7a-9207-1ae6bdc244a0
ms.openlocfilehash: fe291df1648da5002ce3173a68208bbad659705d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33536492"
---
# <a name="how-to-show-a-font-list-with-the-fontdialog-component"></a>Como mostrar uma lista de fontes ao componente FontDialog
O componente [FontDialog](../../../../docs/framework/winforms/controls/fontdialog-component-windows-forms.md) permite aos usuários selecionar uma fonte, bem como alterar seus aspectos de exibição, como peso e tamanho.  
  
 A fonte selecionada na caixa de diálogo é retornada no <xref:System.Windows.Forms.FontDialog.Font%2A> propriedade. Assim, tirar proveito da fonte selecionada pelo usuário é tão fácil quanto ler uma propriedade.  
  
### <a name="to-select-font-properties-using-the-fontdialog-component"></a>Para selecionar as propriedades de fonte usando o componente FontDialog  
  
1.  Exibir a caixa de diálogo usando o <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> método.  
  
2.  Use o <xref:System.Windows.Forms.DialogResult> propriedade para determinar como a caixa de diálogo foi fechada.  
  
3.  Use o <xref:System.Windows.Forms.FontDialog.Font%2A> propriedade para definir a fonte desejada.  
  
     No exemplo a seguir, o <xref:System.Windows.Forms.Button> do controle <xref:System.Windows.Forms.Control.Click> manipulador de eventos abre um <xref:System.Windows.Forms.FontDialog> componente. Quando uma fonte é escolhido e o usuário clica **Okey**, o <xref:System.Windows.Forms.FontDialog.Font%2A> propriedade de um <xref:System.Windows.Forms.TextBox> controle no formulário é definido como a fonte escolhida. O exemplo supõe que o formulário tem uma <xref:System.Windows.Forms.Button> controle, uma <xref:System.Windows.Forms.TextBox> controle e um <xref:System.Windows.Forms.FontDialog> componente.  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, _  
       ByVal e As System.EventArgs) Handles Button1.Click  
       If FontDialog1.ShowDialog() = DialogResult.OK Then  
          TextBox1.Font = FontDialog1.Font  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       if(fontDialog1.ShowDialog() == DialogResult.OK)  
       {  
          textBox1.Font = fontDialog1.Font;  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       void button1_Click(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          if(fontDialog1->ShowDialog() == DialogResult::OK)  
          {  
             textBox1->Font = fontDialog1->Font;  
          }  
       }  
    ```  
  
     (Visual c# e [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) coloque o seguinte código no construtor do formulário para registrar o manipulador de eventos.  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    button1->Click += gcnew System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.FontDialog>  
 [Componente FontDialog](../../../../docs/framework/winforms/controls/fontdialog-component-windows-forms.md)
