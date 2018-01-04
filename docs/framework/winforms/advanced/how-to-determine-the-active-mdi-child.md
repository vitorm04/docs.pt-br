---
title: Como determinar os filhos ativos MDI
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c026df631c2ac033594ea86887bb8440a6aa240a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-determine-the-active-mdi-child"></a>Como determinar os filhos ativos MDI
Ocasionalmente, pode ser útil fornecer um comando que opera o controle que tem o foco no formulário filho ativo no momento. Por exemplo, suponha que você deseja copiar o texto selecionado na caixa de texto do formulário filho para a área de transferência. Você deve criar um procedimento que copia o texto selecionado para a área de transferência usando o <xref:System.Windows.Forms.Control.Click> evento o cópia do item de menu no menu Editar padrão.  
  
 Como um aplicativo MDI pode ter muitas instâncias do mesmo formulário filho, o procedimento precisa saber qual formulário usar. Para especificar o formato correto, use o <xref:System.Windows.Forms.Form.ActiveMdiChild%2A> propriedade, que retorna o formulário filho que tem o foco ou que estava ativo mais recentemente.  
  
 Se houver vários controles em um formulário, também será necessário especificar qual deles está ativo. Como o <xref:System.Windows.Forms.Form.ActiveMdiChild%2A> propriedade, o <xref:System.Windows.Forms.ContainerControl.ActiveControl%2A> propriedade retorna o controle com o foco no formulário filho ativo. O procedimento abaixo ilustra um procedimento de cópia que pode ser chamado de um menu de formulário filho, um menu no formulário MDI ou um botão de barra de ferramentas.  
  
### <a name="to-determine-the-active-mdi-child-to-copy-its-text-to-the-clipboard"></a>Determinar o filho MDI ativo (para copiar o texto para a área de transferência)  
  
1.  Dentro de um método, copie o texto do controle ativo do formulário filho ativo para a área de transferência.  
  
    > [!NOTE]
    >  Este exemplo assume que há um formulário pai MDI (`Form1`) que tem um ou mais janelas filho MDI que contém um <xref:System.Windows.Forms.RichTextBox> controle. Para obter mais informações, consulte [Criando formulários pai MDI](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md).  
  
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
 [Aplicativos da interface MDI (Interface de Vários Documentos)](../../../../docs/framework/winforms/advanced/multiple-document-interface-mdi-applications.md)  
 [Como criar formulários pai MDI](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)  
 [Como criar formulários filho MDI](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md)  
 [Como Enviar Dados para o Filho MDI Ativo](../../../../docs/framework/winforms/advanced/how-to-send-data-to-the-active-mdi-child.md)  
 [Como Organizar Formulários Filho MDI](../../../../docs/framework/winforms/advanced/how-to-arrange-mdi-child-forms.md)
