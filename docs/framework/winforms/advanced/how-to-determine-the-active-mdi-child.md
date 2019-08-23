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
ms.openlocfilehash: 91100b37e4cae9041479b209e40034efe376df5b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69946214"
---
# <a name="how-to-determine-the-active-mdi-child"></a><span data-ttu-id="ae7b1-102">Como: determinar o filho MDI ativo</span><span class="sxs-lookup"><span data-stu-id="ae7b1-102">How to: Determine the Active MDI Child</span></span>
<span data-ttu-id="ae7b1-103">Ocasionalmente, pode ser útil fornecer um comando que opera o controle que tem o foco no formulário filho ativo no momento.</span><span class="sxs-lookup"><span data-stu-id="ae7b1-103">On occasion, you will want to provide a command that operates on the control that has focus on the currently active child form.</span></span> <span data-ttu-id="ae7b1-104">Por exemplo, suponha que você deseja copiar o texto selecionado na caixa de texto do formulário filho para a área de transferência.</span><span class="sxs-lookup"><span data-stu-id="ae7b1-104">For example, suppose you want to copy selected text from the child form's text box to the Clipboard.</span></span> <span data-ttu-id="ae7b1-105">Você criaria um procedimento que copia o texto selecionado para a área de <xref:System.Windows.Forms.Control.Click> transferência usando o evento do item de menu Copiar no menu Editar padrão.</span><span class="sxs-lookup"><span data-stu-id="ae7b1-105">You would create a procedure that copies selected text to the Clipboard using the <xref:System.Windows.Forms.Control.Click> event of the Copy menu item on the standard Edit menu.</span></span>  
  
 <span data-ttu-id="ae7b1-106">Como um aplicativo MDI pode ter muitas instâncias do mesmo formulário filho, o procedimento precisa saber qual formulário usar.</span><span class="sxs-lookup"><span data-stu-id="ae7b1-106">Because an MDI application can have many instances of the same child form, the procedure needs to know which form to use.</span></span> <span data-ttu-id="ae7b1-107">Para especificar o formato correto, use a <xref:System.Windows.Forms.Form.ActiveMdiChild%2A> Propriedade, que retorna o formulário filho que tem o foco ou que estava ativo mais recentemente.</span><span class="sxs-lookup"><span data-stu-id="ae7b1-107">To specify the correct form, use the <xref:System.Windows.Forms.Form.ActiveMdiChild%2A> property, which returns the child form that has the focus or that was most recently active.</span></span>  
  
 <span data-ttu-id="ae7b1-108">Se houver vários controles em um formulário, também será necessário especificar qual deles está ativo.</span><span class="sxs-lookup"><span data-stu-id="ae7b1-108">When you have several controls on a form, you also need to specify which control is active.</span></span> <span data-ttu-id="ae7b1-109">Assim como <xref:System.Windows.Forms.Form.ActiveMdiChild%2A> a propriedade, <xref:System.Windows.Forms.ContainerControl.ActiveControl%2A> a propriedade retorna o controle com o foco no formulário filho ativo.</span><span class="sxs-lookup"><span data-stu-id="ae7b1-109">Like the <xref:System.Windows.Forms.Form.ActiveMdiChild%2A> property, the <xref:System.Windows.Forms.ContainerControl.ActiveControl%2A> property returns the control with the focus on the active child form.</span></span> <span data-ttu-id="ae7b1-110">O procedimento abaixo ilustra um procedimento de cópia que pode ser chamado de um menu de formulário filho, um menu no formulário MDI ou um botão de barra de ferramentas.</span><span class="sxs-lookup"><span data-stu-id="ae7b1-110">The procedure below illustrates a copy procedure that can be called from a child form menu, a menu on the MDI form, or a toolbar button.</span></span>  
  
### <a name="to-determine-the-active-mdi-child-to-copy-its-text-to-the-clipboard"></a><span data-ttu-id="ae7b1-111">Determinar o filho MDI ativo (para copiar o texto para a área de transferência)</span><span class="sxs-lookup"><span data-stu-id="ae7b1-111">To determine the active MDI child (to copy its text to the Clipboard)</span></span>  
  
1. <span data-ttu-id="ae7b1-112">Dentro de um método, copie o texto do controle ativo do formulário filho ativo para a área de transferência.</span><span class="sxs-lookup"><span data-stu-id="ae7b1-112">Within a method, copy the text of the active control of the active child form to the Clipboard.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="ae7b1-113">Este exemplo supõe que haja um formulário pai MDI (`Form1`) que tenha uma ou mais janelas filho MDI que contenham um <xref:System.Windows.Forms.RichTextBox> controle.</span><span class="sxs-lookup"><span data-stu-id="ae7b1-113">This example assumes there is an MDI parent form (`Form1`) that has one or more MDI child windows containing a <xref:System.Windows.Forms.RichTextBox> control.</span></span> <span data-ttu-id="ae7b1-114">Para obter mais informações, consulte [Criando formulários pai MDI](how-to-create-mdi-parent-forms.md).</span><span class="sxs-lookup"><span data-stu-id="ae7b1-114">For more information, see [Creating MDI Parent Forms](how-to-create-mdi-parent-forms.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ae7b1-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ae7b1-115">See also</span></span>

- [<span data-ttu-id="ae7b1-116">Aplicativos da interface MDI (Interface de Vários Documentos)</span><span class="sxs-lookup"><span data-stu-id="ae7b1-116">Multiple-Document Interface (MDI) Applications</span></span>](multiple-document-interface-mdi-applications.md)
- [<span data-ttu-id="ae7b1-117">Como: Criar formulários pai MDI</span><span class="sxs-lookup"><span data-stu-id="ae7b1-117">How to: Create MDI Parent Forms</span></span>](how-to-create-mdi-parent-forms.md)
- [<span data-ttu-id="ae7b1-118">Como: Criar formulários filho MDI</span><span class="sxs-lookup"><span data-stu-id="ae7b1-118">How to: Create MDI Child Forms</span></span>](how-to-create-mdi-child-forms.md)
- [<span data-ttu-id="ae7b1-119">Como: Enviar dados para o filho MDI ativo</span><span class="sxs-lookup"><span data-stu-id="ae7b1-119">How to: Send Data to the Active MDI Child</span></span>](how-to-send-data-to-the-active-mdi-child.md)
- [<span data-ttu-id="ae7b1-120">Como: Organizar formulários filho MDI</span><span class="sxs-lookup"><span data-stu-id="ae7b1-120">How to: Arrange MDI Child Forms</span></span>](how-to-arrange-mdi-child-forms.md)
