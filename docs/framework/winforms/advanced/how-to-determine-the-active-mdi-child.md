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
# <a name="how-to-determine-the-active-mdi-child"></a><span data-ttu-id="8df1d-102">Como determinar os filhos ativos MDI</span><span class="sxs-lookup"><span data-stu-id="8df1d-102">How to: Determine the Active MDI Child</span></span>
<span data-ttu-id="8df1d-103">Ocasionalmente, pode ser útil fornecer um comando que opera o controle que tem o foco no formulário filho ativo no momento.</span><span class="sxs-lookup"><span data-stu-id="8df1d-103">On occasion, you will want to provide a command that operates on the control that has focus on the currently active child form.</span></span> <span data-ttu-id="8df1d-104">Por exemplo, suponha que você deseja copiar o texto selecionado na caixa de texto do formulário filho para a área de transferência.</span><span class="sxs-lookup"><span data-stu-id="8df1d-104">For example, suppose you want to copy selected text from the child form's text box to the Clipboard.</span></span> <span data-ttu-id="8df1d-105">Você criaria um procedimento que copia texto selecionado <xref:System.Windows.Forms.Control.Click> para a Área de Transferência usando o evento do item do menu Copiar no menu Editar padrão.</span><span class="sxs-lookup"><span data-stu-id="8df1d-105">You would create a procedure that copies selected text to the Clipboard using the <xref:System.Windows.Forms.Control.Click> event of the Copy menu item on the standard Edit menu.</span></span>  
  
 <span data-ttu-id="8df1d-106">Como um aplicativo MDI pode ter muitas instâncias do mesmo formulário filho, o procedimento precisa saber qual formulário usar.</span><span class="sxs-lookup"><span data-stu-id="8df1d-106">Because an MDI application can have many instances of the same child form, the procedure needs to know which form to use.</span></span> <span data-ttu-id="8df1d-107">Para especificar o formulário <xref:System.Windows.Forms.Form.ActiveMdiChild%2A> correto, use a propriedade, que retorna o formulário filho que tem o foco ou que estava mais recentemente ativo.</span><span class="sxs-lookup"><span data-stu-id="8df1d-107">To specify the correct form, use the <xref:System.Windows.Forms.Form.ActiveMdiChild%2A> property, which returns the child form that has the focus or that was most recently active.</span></span>  
  
 <span data-ttu-id="8df1d-108">Se houver vários controles em um formulário, também será necessário especificar qual deles está ativo.</span><span class="sxs-lookup"><span data-stu-id="8df1d-108">When you have several controls on a form, you also need to specify which control is active.</span></span> <span data-ttu-id="8df1d-109">Assim <xref:System.Windows.Forms.Form.ActiveMdiChild%2A> como a <xref:System.Windows.Forms.ContainerControl.ActiveControl%2A> propriedade, a propriedade retorna o controle com o foco na forma de criança ativa.</span><span class="sxs-lookup"><span data-stu-id="8df1d-109">Like the <xref:System.Windows.Forms.Form.ActiveMdiChild%2A> property, the <xref:System.Windows.Forms.ContainerControl.ActiveControl%2A> property returns the control with the focus on the active child form.</span></span> <span data-ttu-id="8df1d-110">O procedimento abaixo ilustra um procedimento de cópia que pode ser chamado de um menu de formulário filho, um menu no formulário MDI ou um botão de barra de ferramentas.</span><span class="sxs-lookup"><span data-stu-id="8df1d-110">The procedure below illustrates a copy procedure that can be called from a child form menu, a menu on the MDI form, or a toolbar button.</span></span>  
  
### <a name="to-determine-the-active-mdi-child-to-copy-its-text-to-the-clipboard"></a><span data-ttu-id="8df1d-111">Determinar o filho MDI ativo (para copiar o texto para a área de transferência)</span><span class="sxs-lookup"><span data-stu-id="8df1d-111">To determine the active MDI child (to copy its text to the Clipboard)</span></span>  
  
1. <span data-ttu-id="8df1d-112">Dentro de um método, copie o texto do controle ativo do formulário filho ativo para a área de transferência.</span><span class="sxs-lookup"><span data-stu-id="8df1d-112">Within a method, copy the text of the active control of the active child form to the Clipboard.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="8df1d-113">Este exemplo assume que há um`Form1`formulário pai MDI ( ) que <xref:System.Windows.Forms.RichTextBox> tem uma ou mais janelas de criançaS MDI contendo um controle.</span><span class="sxs-lookup"><span data-stu-id="8df1d-113">This example assumes there is an MDI parent form (`Form1`) that has one or more MDI child windows containing a <xref:System.Windows.Forms.RichTextBox> control.</span></span> <span data-ttu-id="8df1d-114">Para obter mais informações, consulte [Criando formulários pai MDI](how-to-create-mdi-parent-forms.md).</span><span class="sxs-lookup"><span data-stu-id="8df1d-114">For more information, see [Creating MDI Parent Forms](how-to-create-mdi-parent-forms.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8df1d-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="8df1d-115">See also</span></span>

- [<span data-ttu-id="8df1d-116">Aplicativos da interface MDI (Interface de Vários Documentos)</span><span class="sxs-lookup"><span data-stu-id="8df1d-116">Multiple-Document Interface (MDI) Applications</span></span>](multiple-document-interface-mdi-applications.md)
- [<span data-ttu-id="8df1d-117">Como criar formulários pai MDI</span><span class="sxs-lookup"><span data-stu-id="8df1d-117">How to: Create MDI Parent Forms</span></span>](how-to-create-mdi-parent-forms.md)
- [<span data-ttu-id="8df1d-118">Como criar formulários filho MDI</span><span class="sxs-lookup"><span data-stu-id="8df1d-118">How to: Create MDI Child Forms</span></span>](how-to-create-mdi-child-forms.md)
- [<span data-ttu-id="8df1d-119">Como enviar dados para o filhos MDI ativos</span><span class="sxs-lookup"><span data-stu-id="8df1d-119">How to: Send Data to the Active MDI Child</span></span>](how-to-send-data-to-the-active-mdi-child.md)
- [<span data-ttu-id="8df1d-120">Como Organizar Formulários Filho MDI</span><span class="sxs-lookup"><span data-stu-id="8df1d-120">How to: Arrange MDI Child Forms</span></span>](how-to-arrange-mdi-child-forms.md)
