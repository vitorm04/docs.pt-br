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
ms.openlocfilehash: 473cf67f01db8735eb3b32a7549296f827e66ef6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-determine-the-active-mdi-child"></a><span data-ttu-id="88a12-102">Como determinar os filhos ativos MDI</span><span class="sxs-lookup"><span data-stu-id="88a12-102">How to: Determine the Active MDI Child</span></span>
<span data-ttu-id="88a12-103">Ocasionalmente, pode ser útil fornecer um comando que opera o controle que tem o foco no formulário filho ativo no momento.</span><span class="sxs-lookup"><span data-stu-id="88a12-103">On occasion, you will want to provide a command that operates on the control that has focus on the currently active child form.</span></span> <span data-ttu-id="88a12-104">Por exemplo, suponha que você deseja copiar o texto selecionado na caixa de texto do formulário filho para a área de transferência.</span><span class="sxs-lookup"><span data-stu-id="88a12-104">For example, suppose you want to copy selected text from the child form's text box to the Clipboard.</span></span> <span data-ttu-id="88a12-105">Você deve criar um procedimento que copia o texto selecionado para a área de transferência usando o <xref:System.Windows.Forms.Control.Click> evento o cópia do item de menu no menu Editar padrão.</span><span class="sxs-lookup"><span data-stu-id="88a12-105">You would create a procedure that copies selected text to the Clipboard using the <xref:System.Windows.Forms.Control.Click> event of the Copy menu item on the standard Edit menu.</span></span>  
  
 <span data-ttu-id="88a12-106">Como um aplicativo MDI pode ter muitas instâncias do mesmo formulário filho, o procedimento precisa saber qual formulário usar.</span><span class="sxs-lookup"><span data-stu-id="88a12-106">Because an MDI application can have many instances of the same child form, the procedure needs to know which form to use.</span></span> <span data-ttu-id="88a12-107">Para especificar o formato correto, use o <xref:System.Windows.Forms.Form.ActiveMdiChild%2A> propriedade, que retorna o formulário filho que tem o foco ou que estava ativo mais recentemente.</span><span class="sxs-lookup"><span data-stu-id="88a12-107">To specify the correct form, use the <xref:System.Windows.Forms.Form.ActiveMdiChild%2A> property, which returns the child form that has the focus or that was most recently active.</span></span>  
  
 <span data-ttu-id="88a12-108">Se houver vários controles em um formulário, também será necessário especificar qual deles está ativo.</span><span class="sxs-lookup"><span data-stu-id="88a12-108">When you have several controls on a form, you also need to specify which control is active.</span></span> <span data-ttu-id="88a12-109">Como o <xref:System.Windows.Forms.Form.ActiveMdiChild%2A> propriedade, o <xref:System.Windows.Forms.ContainerControl.ActiveControl%2A> propriedade retorna o controle com o foco no formulário filho ativo.</span><span class="sxs-lookup"><span data-stu-id="88a12-109">Like the <xref:System.Windows.Forms.Form.ActiveMdiChild%2A> property, the <xref:System.Windows.Forms.ContainerControl.ActiveControl%2A> property returns the control with the focus on the active child form.</span></span> <span data-ttu-id="88a12-110">O procedimento abaixo ilustra um procedimento de cópia que pode ser chamado de um menu de formulário filho, um menu no formulário MDI ou um botão de barra de ferramentas.</span><span class="sxs-lookup"><span data-stu-id="88a12-110">The procedure below illustrates a copy procedure that can be called from a child form menu, a menu on the MDI form, or a toolbar button.</span></span>  
  
### <a name="to-determine-the-active-mdi-child-to-copy-its-text-to-the-clipboard"></a><span data-ttu-id="88a12-111">Determinar o filho MDI ativo (para copiar o texto para a área de transferência)</span><span class="sxs-lookup"><span data-stu-id="88a12-111">To determine the active MDI child (to copy its text to the Clipboard)</span></span>  
  
1.  <span data-ttu-id="88a12-112">Dentro de um método, copie o texto do controle ativo do formulário filho ativo para a área de transferência.</span><span class="sxs-lookup"><span data-stu-id="88a12-112">Within a method, copy the text of the active control of the active child form to the Clipboard.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="88a12-113">Este exemplo assume que há um formulário pai MDI (`Form1`) que tem um ou mais janelas filho MDI que contém um <xref:System.Windows.Forms.RichTextBox> controle.</span><span class="sxs-lookup"><span data-stu-id="88a12-113">This example assumes there is an MDI parent form (`Form1`) that has one or more MDI child windows containing a <xref:System.Windows.Forms.RichTextBox> control.</span></span> <span data-ttu-id="88a12-114">Para obter mais informações, consulte [Criando formulários pai MDI](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md).</span><span class="sxs-lookup"><span data-stu-id="88a12-114">For more information, see [Creating MDI Parent Forms](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="88a12-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="88a12-115">See Also</span></span>  
 [<span data-ttu-id="88a12-116">Aplicativos da interface MDI (Interface de Vários Documentos)</span><span class="sxs-lookup"><span data-stu-id="88a12-116">Multiple-Document Interface (MDI) Applications</span></span>](../../../../docs/framework/winforms/advanced/multiple-document-interface-mdi-applications.md)  
 [<span data-ttu-id="88a12-117">Como criar formulários pai MDI</span><span class="sxs-lookup"><span data-stu-id="88a12-117">How to: Create MDI Parent Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)  
 [<span data-ttu-id="88a12-118">Como criar formulários filho MDI</span><span class="sxs-lookup"><span data-stu-id="88a12-118">How to: Create MDI Child Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md)  
 [<span data-ttu-id="88a12-119">Como Enviar Dados para o Filho MDI Ativo</span><span class="sxs-lookup"><span data-stu-id="88a12-119">How to: Send Data to the Active MDI Child</span></span>](../../../../docs/framework/winforms/advanced/how-to-send-data-to-the-active-mdi-child.md)  
 [<span data-ttu-id="88a12-120">Como Organizar Formulários Filho MDI</span><span class="sxs-lookup"><span data-stu-id="88a12-120">How to: Arrange MDI Child Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-arrange-mdi-child-forms.md)
