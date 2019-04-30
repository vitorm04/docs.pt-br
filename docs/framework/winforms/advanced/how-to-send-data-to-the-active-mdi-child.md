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
ms.openlocfilehash: f4399d8548eff76aaa4effae6da7239cd3b0284b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61966889"
---
# <a name="how-to-send-data-to-the-active-mdi-child"></a><span data-ttu-id="2e0b4-102">Como: enviar dados para o filho MDI ativo</span><span class="sxs-lookup"><span data-stu-id="2e0b4-102">How to: Send Data to the Active MDI Child</span></span>
<span data-ttu-id="2e0b4-103">Muitas vezes, dentro do contexto de [aplicativos de Interface de documentos múltiplos (MDI)](multiple-document-interface-mdi-applications.md), você precisará enviar dados para a janela filho ativa, como quando o usuário cola dados da área de transferência em um aplicativo MDI.</span><span class="sxs-lookup"><span data-stu-id="2e0b4-103">Often, within the context of [Multiple-Document Interface (MDI) Applications](multiple-document-interface-mdi-applications.md), you will need to send data to the active child window, such as when the user pastes data from the Clipboard into an MDI application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2e0b4-104">Para obter informações sobre como verificar qual janela filho tem o foco e enviar seu conteúdo para a área de transferência, consulte [determinar o filho MDI ativo](how-to-determine-the-active-mdi-child.md).</span><span class="sxs-lookup"><span data-stu-id="2e0b4-104">For information about verifying which child window has focus and sending its contents to the Clipboard, see [Determining the Active MDI Child](how-to-determine-the-active-mdi-child.md).</span></span>  
  
### <a name="to-send-data-to-the-active-mdi-child-window-from-the-clipboard"></a><span data-ttu-id="2e0b4-105">Para enviar dados para a janela filho MDI ativo da área de transferência</span><span class="sxs-lookup"><span data-stu-id="2e0b4-105">To send data to the active MDI child window from the Clipboard</span></span>  
  
1. <span data-ttu-id="2e0b4-106">Dentro de um método, copie o texto na área de transferência para o controle ativo do formulário filho ativo.</span><span class="sxs-lookup"><span data-stu-id="2e0b4-106">Within a method, copy the text on the Clipboard to the active control of the active child form.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="2e0b4-107">Este exemplo assume que há um formulário MDI pai (`Form1`) que tem um ou mais janelas filho MDI que contém um <xref:System.Windows.Forms.RichTextBox> controle.</span><span class="sxs-lookup"><span data-stu-id="2e0b4-107">This example assumes there is an MDI parent form (`Form1`) that has one or more MDI child windows containing a <xref:System.Windows.Forms.RichTextBox> control.</span></span> <span data-ttu-id="2e0b4-108">Para obter mais informações, consulte [Criando formulários pai MDI](how-to-create-mdi-parent-forms.md).</span><span class="sxs-lookup"><span data-stu-id="2e0b4-108">For more information, see [Creating MDI Parent Forms](how-to-create-mdi-parent-forms.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2e0b4-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2e0b4-109">See also</span></span>

- [<span data-ttu-id="2e0b4-110">Aplicativos da interface MDI (Interface de Vários Documentos)</span><span class="sxs-lookup"><span data-stu-id="2e0b4-110">Multiple-Document Interface (MDI) Applications</span></span>](multiple-document-interface-mdi-applications.md)
- [<span data-ttu-id="2e0b4-111">Como: Criar formulários pai MDI</span><span class="sxs-lookup"><span data-stu-id="2e0b4-111">How to: Create MDI Parent Forms</span></span>](how-to-create-mdi-parent-forms.md)
- [<span data-ttu-id="2e0b4-112">Como: Criar formulários filho MDI</span><span class="sxs-lookup"><span data-stu-id="2e0b4-112">How to: Create MDI Child Forms</span></span>](how-to-create-mdi-child-forms.md)
- [<span data-ttu-id="2e0b4-113">Como: Determinar o filho MDI ativo</span><span class="sxs-lookup"><span data-stu-id="2e0b4-113">How to: Determine the Active MDI Child</span></span>](how-to-determine-the-active-mdi-child.md)
- [<span data-ttu-id="2e0b4-114">Como: Organizar formulários filho MDI</span><span class="sxs-lookup"><span data-stu-id="2e0b4-114">How to: Arrange MDI Child Forms</span></span>](how-to-arrange-mdi-child-forms.md)
