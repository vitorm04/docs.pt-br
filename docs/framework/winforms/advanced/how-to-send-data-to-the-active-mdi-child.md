---
title: 'Como: enviar dados para o filho MDI ativo'
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
ms.openlocfilehash: 0a7a2475891488d1fdd60f0db4a483c144a73f0d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947838"
---
# <a name="how-to-send-data-to-the-active-mdi-child"></a>Como: enviar dados para o filho MDI ativo
Muitas vezes, dentro do contexto de [aplicativos de interface de vários documentos (MDI)](multiple-document-interface-mdi-applications.md), você precisará enviar dados para a janela filho ativa, como quando o usuário cola dados da área de transferência em um aplicativo MDI.  
  
> [!NOTE]
> Para obter informações sobre como verificar qual janela filho tem foco e enviar seu conteúdo para a área de transferência, consulte [determinando o filho MDI ativo](how-to-determine-the-active-mdi-child.md).  
  
### <a name="to-send-data-to-the-active-mdi-child-window-from-the-clipboard"></a>Para enviar dados para a janela filho MDI ativa da área de transferência  
  
1. Dentro de um método, copie o texto na área de transferência para o controle ativo do formulário filho ativo.  
  
    > [!NOTE]
    > Este exemplo supõe que haja um formulário pai MDI (`Form1`) que tenha uma ou mais janelas filho MDI que contenham um <xref:System.Windows.Forms.RichTextBox> controle. Para obter mais informações, consulte [Criando formulários pai MDI](how-to-create-mdi-parent-forms.md).  
  
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
  
## <a name="see-also"></a>Consulte também

- [Aplicativos da interface MDI (Interface de Vários Documentos)](multiple-document-interface-mdi-applications.md)
- [Como: Criar formulários pai MDI](how-to-create-mdi-parent-forms.md)
- [Como: Criar formulários filho MDI](how-to-create-mdi-child-forms.md)
- [Como: Determinar o filho MDI ativo](how-to-determine-the-active-mdi-child.md)
- [Como: Organizar formulários filho MDI](how-to-arrange-mdi-child-forms.md)
