---
title: Como inserir um MenuStrip um menu suspenso MDI
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MenuStrip control [Windows Forms], inserting
- MenuStrip control [Windows Forms], merging
- MDI [Windows Forms], merging menu items
ms.assetid: 0fad444e-26d9-49af-8860-044d9c10d608
ms.openlocfilehash: 6e189dd159c48b5779679d0563fab85e9b848992
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736407"
---
# <a name="how-to-insert-a-menustrip-into-an-mdi-drop-down-menu-windows-forms"></a><span data-ttu-id="c1748-102">Como inserir um MenuStrip um menu suspenso MDI (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="c1748-102">How to: Insert a MenuStrip into an MDI Drop-Down Menu (Windows Forms)</span></span>
<span data-ttu-id="c1748-103">Em alguns aplicativos, o tipo de uma janela filho MDI (interface de vários documentos) pode ser diferente da janela MDI pai.</span><span class="sxs-lookup"><span data-stu-id="c1748-103">In some applications, the kind of a multiple-document interface (MDI) child window can be different from the MDI parent window.</span></span> <span data-ttu-id="c1748-104">Por exemplo, a MDI pai pode ser uma planilha e a MDI filho pode ser um gráfico.</span><span class="sxs-lookup"><span data-stu-id="c1748-104">For example, the MDI parent might be a spreadsheet, and the MDI child might be a chart.</span></span> <span data-ttu-id="c1748-105">Nesse caso, é recomendável atualizar o conteúdo do menu do MDI pai com o conteúdo do menu do MDI filho, visto que janelas MDI filho de tipos diferentes são ativadas.</span><span class="sxs-lookup"><span data-stu-id="c1748-105">In that case, you want to update the contents of the MDI parent's menu with the contents of the MDI child's menu as MDI child windows of different kinds are activated.</span></span>  
  
 <span data-ttu-id="c1748-106">O procedimento a seguir usa as propriedades <xref:System.Windows.Forms.Form.IsMdiContainer%2A>, <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A>, <xref:System.Windows.Forms.MergeAction>e <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> para inserir um grupo de itens de menu do menu filho MDI na parte suspensa do menu pai MDI.</span><span class="sxs-lookup"><span data-stu-id="c1748-106">The following procedure uses the <xref:System.Windows.Forms.Form.IsMdiContainer%2A>, <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A>, <xref:System.Windows.Forms.MergeAction>, and <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> properties to insert a group of menu items from the MDI child menu into the drop-down part of the MDI parent menu.</span></span> <span data-ttu-id="c1748-107">Fechar a janela MDI filho remove os itens de menu inseridos do MDI pai.</span><span class="sxs-lookup"><span data-stu-id="c1748-107">Closing the MDI child window removes the inserted menu items from the MDI parent.</span></span>  
  
### <a name="to-insert-a-menustrip-into-an-mdi-drop-down-menu"></a><span data-ttu-id="c1748-108">Como inserir um MenuStrip em um menu suspenso MDI</span><span class="sxs-lookup"><span data-stu-id="c1748-108">To insert a MenuStrip into an MDI drop-down menu</span></span>  
  
1. <span data-ttu-id="c1748-109">Crie um formulário e defina sua propriedade <xref:System.Windows.Forms.Form.IsMdiContainer%2A> como `true`.</span><span class="sxs-lookup"><span data-stu-id="c1748-109">Create a form and set its <xref:System.Windows.Forms.Form.IsMdiContainer%2A> property to `true`.</span></span>  
  
2. <span data-ttu-id="c1748-110">Adicione um <xref:System.Windows.Forms.MenuStrip> a `Form1` e defina a propriedade <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> do <xref:System.Windows.Forms.MenuStrip> como `true`.</span><span class="sxs-lookup"><span data-stu-id="c1748-110">Add a <xref:System.Windows.Forms.MenuStrip> to `Form1` and set the <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> property of the <xref:System.Windows.Forms.MenuStrip> to `true`.</span></span>  
  
3. <span data-ttu-id="c1748-111">Adicione um item de menu de nível superior ao `Form1`<xref:System.Windows.Forms.MenuStrip> e defina sua propriedade <xref:System.Windows.Forms.Control.Text%2A> como `&File`.</span><span class="sxs-lookup"><span data-stu-id="c1748-111">Add a top-level menu item to the `Form1`<xref:System.Windows.Forms.MenuStrip> and set its <xref:System.Windows.Forms.Control.Text%2A> property to `&File`.</span></span>  
  
4. <span data-ttu-id="c1748-112">Adicione três itens de submenu ao item de menu `&File` e defina suas propriedades <xref:System.Windows.Forms.ToolStripItem.Text%2A> como `&Open`, `&Import from`e `E&xit`.</span><span class="sxs-lookup"><span data-stu-id="c1748-112">Add three submenu items to the `&File` menu item and set their <xref:System.Windows.Forms.ToolStripItem.Text%2A> properties to `&Open`, `&Import from`, and `E&xit`.</span></span>  
  
5. <span data-ttu-id="c1748-113">Adicione dois itens de submenu ao item de submenu `&Import from` e defina suas propriedades <xref:System.Windows.Forms.ToolStripItem.Text%2A> como `&Word` e `&Excel`.</span><span class="sxs-lookup"><span data-stu-id="c1748-113">Add two submenu items to the `&Import from` submenu item and set their <xref:System.Windows.Forms.ToolStripItem.Text%2A> properties to `&Word` and `&Excel`.</span></span>  
  
6. <span data-ttu-id="c1748-114">Adicione um formulário ao projeto, adicione um <xref:System.Windows.Forms.MenuStrip> ao formulário e defina a propriedade <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> do `Form2`<xref:System.Windows.Forms.MenuStrip> como `true`.</span><span class="sxs-lookup"><span data-stu-id="c1748-114">Add a form to the project, add a <xref:System.Windows.Forms.MenuStrip> to the form, and set the <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> property of the `Form2`<xref:System.Windows.Forms.MenuStrip> to `true`.</span></span>  
  
7. <span data-ttu-id="c1748-115">Adicione um item de menu de nível superior ao `Form2`<xref:System.Windows.Forms.MenuStrip> e defina sua propriedade <xref:System.Windows.Forms.ToolStripItem.Text%2A> como `&File`.</span><span class="sxs-lookup"><span data-stu-id="c1748-115">Add a top-level menu item to the `Form2`<xref:System.Windows.Forms.MenuStrip> and set its <xref:System.Windows.Forms.ToolStripItem.Text%2A> property to `&File`.</span></span>  
  
8. <span data-ttu-id="c1748-116">Adicione itens de submenu ao menu de `&File` de `Form2` na seguinte ordem: uma <xref:System.Windows.Forms.ToolStripSeparator>, `&Save`, `Save and &Close`e outra <xref:System.Windows.Forms.ToolStripSeparator>.</span><span class="sxs-lookup"><span data-stu-id="c1748-116">Add submenu items to the `&File` menu of `Form2` in the following order: a <xref:System.Windows.Forms.ToolStripSeparator>, `&Save`, `Save and &Close`, and another <xref:System.Windows.Forms.ToolStripSeparator>.</span></span>  
  
9. <span data-ttu-id="c1748-117">Defina as propriedades <xref:System.Windows.Forms.MergeAction> e <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> dos itens de menu `Form2`, conforme mostrado na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="c1748-117">Set the <xref:System.Windows.Forms.MergeAction> and <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> properties of the `Form2` menu items as shown in the following table.</span></span>  
  
    |<span data-ttu-id="c1748-118">Item de menu Form2</span><span class="sxs-lookup"><span data-stu-id="c1748-118">Form2 menu item</span></span>|<span data-ttu-id="c1748-119">Valor de MergeAction</span><span class="sxs-lookup"><span data-stu-id="c1748-119">MergeAction value</span></span>|<span data-ttu-id="c1748-120">Valor de MergeIndex</span><span class="sxs-lookup"><span data-stu-id="c1748-120">MergeIndex value</span></span>|  
    |---------------------|-----------------------|----------------------|  
    |<span data-ttu-id="c1748-121">File</span><span class="sxs-lookup"><span data-stu-id="c1748-121">File</span></span>|<span data-ttu-id="c1748-122">MatchOnly</span><span class="sxs-lookup"><span data-stu-id="c1748-122">MatchOnly</span></span>|<span data-ttu-id="c1748-123">-1</span><span class="sxs-lookup"><span data-stu-id="c1748-123">-1</span></span>|  
    |<span data-ttu-id="c1748-124">Separador</span><span class="sxs-lookup"><span data-stu-id="c1748-124">Separator</span></span>|<span data-ttu-id="c1748-125">Inserir</span><span class="sxs-lookup"><span data-stu-id="c1748-125">Insert</span></span>|<span data-ttu-id="c1748-126">2</span><span class="sxs-lookup"><span data-stu-id="c1748-126">2</span></span>|  
    |<span data-ttu-id="c1748-127">Salvar</span><span class="sxs-lookup"><span data-stu-id="c1748-127">Save</span></span>|<span data-ttu-id="c1748-128">Inserir</span><span class="sxs-lookup"><span data-stu-id="c1748-128">Insert</span></span>|<span data-ttu-id="c1748-129">3</span><span class="sxs-lookup"><span data-stu-id="c1748-129">3</span></span>|  
    |<span data-ttu-id="c1748-130">Salvar e Fechar</span><span class="sxs-lookup"><span data-stu-id="c1748-130">Save and Close</span></span>|<span data-ttu-id="c1748-131">Inserir</span><span class="sxs-lookup"><span data-stu-id="c1748-131">Insert</span></span>|<span data-ttu-id="c1748-132">4</span><span class="sxs-lookup"><span data-stu-id="c1748-132">4</span></span>|  
    |<span data-ttu-id="c1748-133">Separador</span><span class="sxs-lookup"><span data-stu-id="c1748-133">Separator</span></span>|<span data-ttu-id="c1748-134">Inserir</span><span class="sxs-lookup"><span data-stu-id="c1748-134">Insert</span></span>|<span data-ttu-id="c1748-135">5</span><span class="sxs-lookup"><span data-stu-id="c1748-135">5</span></span>|  
  
10. <span data-ttu-id="c1748-136">Crie um manipulador de eventos para o evento <xref:System.Windows.Forms.Control.Click> do <xref:System.Windows.Forms.ToolStripMenuItem>de `&Open`.</span><span class="sxs-lookup"><span data-stu-id="c1748-136">Create an event handler for the <xref:System.Windows.Forms.Control.Click> event of the `&Open`<xref:System.Windows.Forms.ToolStripMenuItem>.</span></span>  
  
11. <span data-ttu-id="c1748-137">No manipulador de eventos, insira um código semelhante ao exemplo de código a seguir para criar e exibir novas instâncias de `Form2` como filhos MDI de `Form1`.</span><span class="sxs-lookup"><span data-stu-id="c1748-137">Within the event handler, insert code similar to the following code example to create and display new instances of `Form2` as MDI children of `Form1`.</span></span>  
  
    ```vb  
    Private Sub openToolStripMenuItem_Click(ByVal sender As System.Object, _  
    ByVal e As System.EventArgs) Handles openToolStripMenuItem.Click  
        Dim NewMDIChild As New Form2()  
        'Set the parent form of the child window.  
            NewMDIChild.MdiParent = Me  
        'Display the new form.  
            NewMDIChild.Show()  
    End Sub  
    ```  
  
    ```csharp  
    private void openToolStripMenuItem_Click(object sender, EventArgs e)  
    {  
        Form2 newMDIChild = new Form2();  
        // Set the parent form of the child window.  
            newMDIChild.MdiParent = this;  
        // Display the new form.  
            newMDIChild.Show();  
    }  
    ```  
  
12. <span data-ttu-id="c1748-138">Coloque um código semelhante ao exemplo de código a seguir no `&Open`<xref:System.Windows.Forms.ToolStripMenuItem> para registrar o manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="c1748-138">Place code similar to the following code example in the `&Open`<xref:System.Windows.Forms.ToolStripMenuItem> to register the event handler.</span></span>  
  
    ```vb  
    Private Sub openToolStripMenuItem_Click(sender As Object, e As _  
    EventArgs) Handles openToolStripMenuItem.Click  
    ```  
  
    ```csharp  
    this.openToolStripMenuItem.Click += new System.EventHandler(this.openToolStripMenuItem_Click);  
    ```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c1748-139">Compilando o Código</span><span class="sxs-lookup"><span data-stu-id="c1748-139">Compiling the Code</span></span>  
 <span data-ttu-id="c1748-140">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="c1748-140">This example requires:</span></span>  
  
- <span data-ttu-id="c1748-141">Dois controles de <xref:System.Windows.Forms.Form> chamados `Form1` e `Form2`.</span><span class="sxs-lookup"><span data-stu-id="c1748-141">Two <xref:System.Windows.Forms.Form> controls named `Form1` and `Form2`.</span></span>  
  
- <span data-ttu-id="c1748-142">Um controle <xref:System.Windows.Forms.MenuStrip> em `Form1` chamado `menuStrip1`e um controle <xref:System.Windows.Forms.MenuStrip> em `Form2` chamado `menuStrip2`.</span><span class="sxs-lookup"><span data-stu-id="c1748-142">A <xref:System.Windows.Forms.MenuStrip> control on `Form1` named `menuStrip1`, and a <xref:System.Windows.Forms.MenuStrip> control on `Form2` named `menuStrip2`.</span></span>  
  
- <span data-ttu-id="c1748-143">Referências aos assemblies <xref:System?displayProperty=nameWithType> e <xref:System.Windows.Forms?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c1748-143">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1748-144">Veja também</span><span class="sxs-lookup"><span data-stu-id="c1748-144">See also</span></span>

- [<span data-ttu-id="c1748-145">Como criar formulários pai MDI</span><span class="sxs-lookup"><span data-stu-id="c1748-145">How to: Create MDI Parent Forms</span></span>](../advanced/how-to-create-mdi-parent-forms.md)
- [<span data-ttu-id="c1748-146">Como criar formulários filho MDI</span><span class="sxs-lookup"><span data-stu-id="c1748-146">How to: Create MDI Child Forms</span></span>](../advanced/how-to-create-mdi-child-forms.md)
- [<span data-ttu-id="c1748-147">Visão geral do controle MenuStrip</span><span class="sxs-lookup"><span data-stu-id="c1748-147">MenuStrip Control Overview</span></span>](menustrip-control-overview-windows-forms.md)
