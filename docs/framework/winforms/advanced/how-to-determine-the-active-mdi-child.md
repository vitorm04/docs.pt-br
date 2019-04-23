---
title: 'Como: determinar o filho MDI ativo'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Clipboard [Windows Forms], copying data to
- MDI [Windows Forms], child windows
- child forms
- MDI [Windows Forms], activating forms
- MDI [Windows Forms], locating focus
ms.assetid: 33880ec3-0207-4c2b-a616-ff140443cc0f
ms.openlocfilehash: 9b70824670b8f47a2346135cb31ad39bd55694d1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59300600"
---
# <a name="how-to-determine-the-active-mdi-child"></a>Como: determinar o filho MDI ativo
Ocasionalmente, pode ser útil fornecer um comando que opera o controle que tem o foco no formulário filho ativo no momento. Por exemplo, suponha que você deseja copiar o texto selecionado na caixa de texto do formulário filho para a área de transferência. Você criaria um procedimento que copia o texto selecionado para a área de transferência usando o <xref:System.Windows.Forms.Control.Click> evento o cópia do item de menu no menu Editar padrão.  
  
 Como um aplicativo MDI pode ter muitas instâncias do mesmo formulário filho, o procedimento precisa saber qual formulário usar. Para especificar a forma correta, use o <xref:System.Windows.Forms.Form.ActiveMdiChild%2A> propriedade, que retorna o formulário filho que tem o foco ou que estava ativo mais recentemente.  
  
 Se houver vários controles em um formulário, também será necessário especificar qual deles está ativo. Como o <xref:System.Windows.Forms.Form.ActiveMdiChild%2A> propriedade, o <xref:System.Windows.Forms.ContainerControl.ActiveControl%2A> propriedade retorna o controle com o foco no formulário filho ativo. O procedimento abaixo ilustra um procedimento de cópia que pode ser chamado de um menu de formulário filho, um menu no formulário MDI ou um botão de barra de ferramentas.  
  
### <a name="to-determine-the-active-mdi-child-to-copy-its-text-to-the-clipboard"></a>Determinar o filho MDI ativo (para copiar o texto para a área de transferência)  
  
1. Dentro de um método, copie o texto do controle ativo do formulário filho ativo para a área de transferência.  
  
    > [!NOTE]
    >  Este exemplo assume que há um formulário MDI pai (`Form1`) que tem um ou mais janelas filho MDI que contém um <xref:System.Windows.Forms.RichTextBox> controle. Para obter mais informações, consulte [Criando formulários pai MDI](how-to-create-mdi-parent-forms.md).  
  
    ```vb  
    Public Sub mniCopy_Click(ByVal sender As Object, _  
       ByVal e As System.EventArgs) Handles mniCopy.Click  
  
       ' Determine the active child form.  
       Dim activeChild As Form = Me.ActiveMDIChild  
  
       ' If there is an active child form, find the active control, which  
       ' in this example should be a RichTextBox.  
       If (Not activeChild Is Nothing) Then  
          Dim theBox As RichTextBox = _  
            TryCast(activeChild.ActiveControl, RichTextBox)  
  
          If (Not theBox Is Nothing) Then  
             'Put selected text on Clipboard.  
             Clipboard.SetDataObject(theBox.SelectedText)  
          Else  
             MessageBox.Show("You need to select a RichTextBox.")  
          End If  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    protected void mniCopy_Click (object sender, System.EventArgs e)  
    {  
       // Determine the active child form.  
       Form activeChild = this.ActiveMdiChild;  
  
       // If there is an active child form, find the active control, which  
       // in this example should be a RichTextBox.  
       if (activeChild != null)  
       {    
          try  
          {  
             RichTextBox theBox = (RichTextBox)activeChild.ActiveControl;  
             if (theBox != null)  
             {  
                // Put the selected text on the Clipboard.  
                Clipboard.SetDataObject(theBox.SelectedText);  
  
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
- [Como: Enviar dados para o filho MDI ativo](how-to-send-data-to-the-active-mdi-child.md)
- [Como: Organizar formulários filho MDI](how-to-arrange-mdi-child-forms.md)
