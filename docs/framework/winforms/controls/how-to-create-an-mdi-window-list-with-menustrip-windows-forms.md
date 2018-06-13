---
title: Como criar uma lista de janelas MDI com MenuStrip (Windows Forms)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MDI [Windows Forms], creating window lists
- MenuStrip control [Windows Forms], creating window lists
ms.assetid: 04fb414b-811f-4a83-aab6-b4a24646dec5
ms.openlocfilehash: c87ffadaef2842f10d40f6fd84eb1c70c6dfe37e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33530816"
---
# <a name="how-to-create-an-mdi-window-list-with-menustrip-windows-forms"></a><span data-ttu-id="2d225-102">Como criar uma lista de janelas MDI com MenuStrip (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="2d225-102">How to: Create an MDI Window List with MenuStrip (Windows Forms)</span></span>
<span data-ttu-id="2d225-103">Use a interface MDI para criar aplicativos que podem abrir vários documentos no mesmo momento e copie e cole o conteúdo de um documento para outro.</span><span class="sxs-lookup"><span data-stu-id="2d225-103">Use the multiple-document interface (MDI) to create applications that can open several documents at the same time and copy and paste content from one document to the other.</span></span>  
  
 <span data-ttu-id="2d225-104">Este procedimento mostra como criar uma lista de todos os formulários filho ativos no menu Janela do pai.</span><span class="sxs-lookup"><span data-stu-id="2d225-104">This procedure shows you how to create a list of all the active child forms on the parent's Window menu.</span></span>  
  
### <a name="to-create-an-mdi-window-list-on-a-menustrip"></a><span data-ttu-id="2d225-105">Para criar uma lista de janelas MDI em um MenuStrip</span><span class="sxs-lookup"><span data-stu-id="2d225-105">To create an MDI Window list on a MenuStrip</span></span>  
  
1.  <span data-ttu-id="2d225-106">Criar um formulário e defina seu <xref:System.Windows.Forms.Form.IsMdiContainer%2A> propriedade `true`.</span><span class="sxs-lookup"><span data-stu-id="2d225-106">Create a form and set its <xref:System.Windows.Forms.Form.IsMdiContainer%2A> property to `true`.</span></span>  
  
2.  <span data-ttu-id="2d225-107">Adicionar uma <xref:System.Windows.Forms.MenuStrip> ao formulário.</span><span class="sxs-lookup"><span data-stu-id="2d225-107">Add a <xref:System.Windows.Forms.MenuStrip> to the form.</span></span>  
  
3.  <span data-ttu-id="2d225-108">Adicionar dois itens de menu de nível superior para o <xref:System.Windows.Forms.MenuStrip> e defina seus <xref:System.Windows.Forms.Control.Text%2A> propriedades `&File` e `&Window`.</span><span class="sxs-lookup"><span data-stu-id="2d225-108">Add two top-level menu items to the <xref:System.Windows.Forms.MenuStrip> and set their <xref:System.Windows.Forms.Control.Text%2A> properties to `&File` and `&Window`.</span></span>  
  
4.  <span data-ttu-id="2d225-109">Adicionar um item de submenu a `&File` item de menu e defina seu <xref:System.Windows.Forms.ToolStripItem.Text%2A> propriedade `&Open`.</span><span class="sxs-lookup"><span data-stu-id="2d225-109">Add a submenu item to the `&File` menu item and set its <xref:System.Windows.Forms.ToolStripItem.Text%2A> property to `&Open`.</span></span>  
  
5.  <span data-ttu-id="2d225-110">Definir o <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> propriedade o <xref:System.Windows.Forms.MenuStrip> para o `&Window` <xref:System.Windows.Forms.ToolStripMenuItem>.</span><span class="sxs-lookup"><span data-stu-id="2d225-110">Set the <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> property of the <xref:System.Windows.Forms.MenuStrip> to the `&Window`<xref:System.Windows.Forms.ToolStripMenuItem>.</span></span>  
  
6.  <span data-ttu-id="2d225-111">Adicione um formulário para o projeto e adicione o controle que você deseja a ele, como outro <xref:System.Windows.Forms.MenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="2d225-111">Add a form to the project and add the control you want to it, such as another <xref:System.Windows.Forms.MenuStrip>.</span></span>  
  
7.  <span data-ttu-id="2d225-112">Criar um manipulador de eventos para o <xref:System.Windows.Forms.Control.Click> evento o `&New` <xref:System.Windows.Forms.ToolStripMenuItem>.</span><span class="sxs-lookup"><span data-stu-id="2d225-112">Create an event handler for the <xref:System.Windows.Forms.Control.Click> event of the `&New`<xref:System.Windows.Forms.ToolStripMenuItem>.</span></span>  
  
8.  <span data-ttu-id="2d225-113">No manipulador de eventos, insira um código semelhante ao seguinte para criar e exibir novas instâncias de `Form2` como filhos MDI de `Form1`.</span><span class="sxs-lookup"><span data-stu-id="2d225-113">Within the event handler, insert code similar to the following to create and display new instances of `Form2` as MDI children of `Form1`.</span></span>  
  
    ```vb  
    Private Sub openToolStripMenuItem_Click(ByVal sender As _  
    System.Object, ByVal e As System.EventArgs) Handles _  
    openToolStripMenuItem.Click  
        Dim NewMDIChild As New Form2()  
        'Set the parent form of the child window.  
            NewMDIChild.MdiParent = Me  
        'Display the new form.  
            NewMDIChild.Show()  
    End Sub  
    ```  
  
    ```csharp  
    private void newToolStripMenuItem_Click(object sender, EventArgs e)  
    {  
        Form2 newMDIChild = new Form2();  
        // Set the parent form of the child window.  
            newMDIChild.MdiParent = this;  
        // Display the new form.  
            newMDIChild.Show();  
    }  
    ```  
  
9. <span data-ttu-id="2d225-114">Coloque o código como o seguinte o `&New` <xref:System.Windows.Forms.ToolStripMenuItem> para registrar o manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="2d225-114">Place code like the following in the `&New`<xref:System.Windows.Forms.ToolStripMenuItem> to register the event handler.</span></span>  
  
    ```vb  
    Private Sub newToolStripMenuItem_Click(sender As Object, e As _  
    EventArgs) Handles newToolStripMenuItem.Click  
    ```  
  
    ```csharp  
    this.newToolStripMenuItem.Click += new System.EventHandler(this.newToolStripMenuItem_Click);  
    ```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="2d225-115">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="2d225-115">Compiling the Code</span></span>  
 <span data-ttu-id="2d225-116">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="2d225-116">This example requires:</span></span>  
  
-   <span data-ttu-id="2d225-117">Dois <xref:System.Windows.Forms.Form> controles denominados `Form1` e `Form2`.</span><span class="sxs-lookup"><span data-stu-id="2d225-117">Two <xref:System.Windows.Forms.Form> controls named `Form1` and `Form2`.</span></span>  
  
-   <span data-ttu-id="2d225-118">Um <xref:System.Windows.Forms.MenuStrip> control em `Form1` chamado `menuStrip1`e um <xref:System.Windows.Forms.MenuStrip> control em `Form2` chamado `menuStrip2`.</span><span class="sxs-lookup"><span data-stu-id="2d225-118">A <xref:System.Windows.Forms.MenuStrip> control on `Form1` named `menuStrip1`, and a <xref:System.Windows.Forms.MenuStrip> control on `Form2` named `menuStrip2`.</span></span>  
  
-   <span data-ttu-id="2d225-119">Referências aos assemblies <xref:System?displayProperty=nameWithType> e <xref:System.Windows.Forms?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="2d225-119">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d225-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2d225-120">See Also</span></span>  
 [<span data-ttu-id="2d225-121">Como criar formulários pai MDI</span><span class="sxs-lookup"><span data-stu-id="2d225-121">How to: Create MDI Parent Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)  
 [<span data-ttu-id="2d225-122">Como criar formulários filho MDI</span><span class="sxs-lookup"><span data-stu-id="2d225-122">How to: Create MDI Child Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md)  
 [<span data-ttu-id="2d225-123">Controle MenuStrip</span><span class="sxs-lookup"><span data-stu-id="2d225-123">MenuStrip Control</span></span>](../../../../docs/framework/winforms/controls/menustrip-control-windows-forms.md)
