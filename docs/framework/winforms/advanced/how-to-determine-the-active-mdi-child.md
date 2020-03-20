---
title: Como determinar os filhos ativos MDI
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
ms.openlocfilehash: 57491faa10c182630d41565ba236d65e393929b3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182542"
---
# <a name="how-to-determine-the-active-mdi-child"></a>Como determinar os filhos ativos MDI
Ocasionalmente, pode ser útil fornecer um comando que opera o controle que tem o foco no formulário filho ativo no momento. Por exemplo, suponha que você deseja copiar o texto selecionado na caixa de texto do formulário filho para a área de transferência. Você criaria um procedimento que copia texto selecionado <xref:System.Windows.Forms.Control.Click> para a Área de Transferência usando o evento do item do menu Copiar no menu Editar padrão.  
  
 Como um aplicativo MDI pode ter muitas instâncias do mesmo formulário filho, o procedimento precisa saber qual formulário usar. Para especificar o formulário <xref:System.Windows.Forms.Form.ActiveMdiChild%2A> correto, use a propriedade, que retorna o formulário filho que tem o foco ou que estava mais recentemente ativo.  
  
 Se houver vários controles em um formulário, também será necessário especificar qual deles está ativo. Assim <xref:System.Windows.Forms.Form.ActiveMdiChild%2A> como a <xref:System.Windows.Forms.ContainerControl.ActiveControl%2A> propriedade, a propriedade retorna o controle com o foco na forma de criança ativa. O procedimento abaixo ilustra um procedimento de cópia que pode ser chamado de um menu de formulário filho, um menu no formulário MDI ou um botão de barra de ferramentas.  
  
### <a name="to-determine-the-active-mdi-child-to-copy-its-text-to-the-clipboard"></a>Determinar o filho MDI ativo (para copiar o texto para a área de transferência)  
  
1. Dentro de um método, copie o texto do controle ativo do formulário filho ativo para a área de transferência.  
  
    > [!NOTE]
    > Este exemplo assume que há um`Form1`formulário pai MDI ( ) que <xref:System.Windows.Forms.RichTextBox> tem uma ou mais janelas de criançaS MDI contendo um controle. Para obter mais informações, consulte [Criando formulários pai MDI](how-to-create-mdi-parent-forms.md).  
  
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
  
## <a name="see-also"></a>Confira também

- [Aplicativos da interface MDI (Interface de Vários Documentos)](multiple-document-interface-mdi-applications.md)
- [Como criar formulários pai MDI](how-to-create-mdi-parent-forms.md)
- [Como criar formulários filho MDI](how-to-create-mdi-child-forms.md)
- [Como enviar dados para o filhos MDI ativos](how-to-send-data-to-the-active-mdi-child.md)
- [Como Organizar Formulários Filho MDI](how-to-arrange-mdi-child-forms.md)
