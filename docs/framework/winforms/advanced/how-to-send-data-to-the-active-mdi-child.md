---
title: Como enviar dados para o filhos MDI ativos
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- child forms
- MDI [Windows Forms], sending data to forms
- Clipboard [Windows Forms], pasting
- Clipboard [Windows Forms], getting data from
ms.assetid: 1047d2fe-1235-46db-aad9-563aea1d743b
ms.openlocfilehash: 563be8494cb84dc74b45985d3ba74e4b6a07eb8a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182489"
---
# <a name="how-to-send-data-to-the-active-mdi-child"></a>Como enviar dados para o filhos MDI ativos
Muitas vezes, dentro do contexto de [Aplicativos de Interface de Vários Documentos (MDI),](multiple-document-interface-mdi-applications.md)você precisará enviar dados para a janela ativa do filho, como quando o usuário cola dados da Área de Transferência em um aplicativo MDI.  
  
> [!NOTE]
> Para obter informações sobre como verificar qual janela filho tem foco e enviar seu conteúdo para a Área de Transferência, consulte [Determinando o MDI Active Child](how-to-determine-the-active-mdi-child.md).  
  
### <a name="to-send-data-to-the-active-mdi-child-window-from-the-clipboard"></a>Para enviar dados para a janela de criança MDI ativa da área de transferência  
  
1. Dentro de um método, copie o texto na Área de Transferência para o controle ativo da forma criança ativa.  
  
    > [!NOTE]
    > Este exemplo assume que há um`Form1`formulário pai MDI ( ) que <xref:System.Windows.Forms.RichTextBox> tem uma ou mais janelas de criançaS MDI contendo um controle. Para obter mais informações, consulte [Criando formulários pai MDI](how-to-create-mdi-parent-forms.md).  
  
    ```vb  
    Public Sub mniPaste_Click(ByVal sender As Object, _  
       ByVal e As System.EventArgs) Handles mniPaste.Click  
  
       ' Determine the active child form.  
       Dim activeChild As Form = Me.ParentForm.ActiveMDIChild  
  
       ' If there is an active child form, find the active control, which  
       ' in this example should be a RichTextBox.  
       If (Not activeChild Is Nothing) Then  
          Try  
             Dim theBox As RichTextBox = Ctype(activeChild.ActiveControl, RichTextBox)  
             If (Not theBox Is Nothing) Then  
                ' Create a new instance of the DataObject interface.  
                Dim data As IDataObject = Clipboard.GetDataObject()  
                ' If the data is text, then set the text of the
                ' RichTextBox to the text in the clipboard.  
                If (data.GetDataPresent(DataFormats.Text)) Then  
                   theBox.SelectedText = data.GetData(DataFormats.Text).ToString()  
                End If  
             End If  
          Catch  
             MessageBox.Show("You need to select a RichTextBox.")  
          End Try  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    protected void mniPaste_Click (object sender, System.EventArgs e)  
    {  
      // Determine the active child form.  
       Form activeChild = this.ParentForm.ActiveMdiChild;  
  
       // If there is an active child form, find the active control, which  
       // in this example should be a RichTextBox.  
       if (activeChild != null)  
       {  
          try
          {  
             RichTextBox theBox = (RichTextBox)activeChild.ActiveControl;  
             if (theBox != null)  
             {  
                // Create a new instance of the DataObject interface.  
                IDataObject data = Clipboard.GetDataObject();  
                // If the data is text, then set the text of the
                // RichTextBox to the text in the clipboard.  
                if (data.GetDataPresent(DataFormats.Text))  
                {  
                   theBox.SelectedText = data.GetData(DataFormats.Text).ToString();
                }  
             }  
          }  
          catch
          {  
             MessageBox.Show("You need to select a RichTextBox.");  
          }  
       }  
    }  
    ```  
  
## <a name="see-also"></a>Confira também

- [Aplicativos da interface MDI (Interface de Vários Documentos)](multiple-document-interface-mdi-applications.md)
- [Como criar formulários pai MDI](how-to-create-mdi-parent-forms.md)
- [Como criar formulários filho MDI](how-to-create-mdi-child-forms.md)
- [Como determinar o filho MDI ativo](how-to-determine-the-active-mdi-child.md)
- [Como Organizar Formulários Filho MDI](how-to-arrange-mdi-child-forms.md)
