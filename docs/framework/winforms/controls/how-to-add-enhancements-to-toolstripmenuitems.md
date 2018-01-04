---
title: Como adicionar melhorias a ToolStripMenuItems
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
- commands [Windows Forms], grouping on menus
- check marks [Windows Forms], adding to menus
- ToolStripMenuItems [Windows Forms], displaying access keys
- menus [Windows Forms], grouping commands
- menu items [Windows Forms], displaying shortcut keys
- ToolStripMenuItems
- separators [Windows Forms], displaying on menus
- menu items [Windows Forms], showing separators
- menu items [Windows Forms], adding check marks
- ToolStripMenuItems [Windows Forms], adding check marks
- menu items [Windows Forms], adding images
- ToolStripSeparators [Windows Forms], displaying on MenuStrips
- menu items [Windows Forms], displaying access keys
- ToolStripMenuItems [Windows Forms], displaying shortcut keys
- ToolStripMenuItems [Windows Forms], adding images
- keyboard shortcuts [Windows Forms], displaying on menus
- images [Windows Forms], adding to menus
- ToolStripMenuItems [Windows Forms], showing separator bars
ms.assetid: aa5f19bb-b545-4378-bfa6-36ba592f0d7c
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 075370b56ab9e73434394e15a25cd5ce6cd043bf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-enhancements-to-toolstripmenuitems"></a><span data-ttu-id="ab46b-102">Como adicionar melhorias a ToolStripMenuItems</span><span class="sxs-lookup"><span data-stu-id="ab46b-102">How to: Add Enhancements to ToolStripMenuItems</span></span>
<span data-ttu-id="ab46b-103">Você pode aprimorar a usabilidade de <xref:System.Windows.Forms.MenuStrip> e <xref:System.Windows.Forms.ContextMenuStrip> controles das seguintes maneiras:</span><span class="sxs-lookup"><span data-stu-id="ab46b-103">You can enhance the usability of <xref:System.Windows.Forms.MenuStrip> and <xref:System.Windows.Forms.ContextMenuStrip> controls in the following ways:</span></span>  
  
-   <span data-ttu-id="ab46b-104">Adicione marcas de seleção para designar se um recurso está ativado ou desativado, como se uma régua é exibida ao longo da margem de um aplicativo de processamento de texto ou para indicar qual arquivo em uma lista de arquivos está sendo exibido, como em um menu **Janela**.</span><span class="sxs-lookup"><span data-stu-id="ab46b-104">Add check marks to designate whether a feature is turned on or off, such as whether a ruler is displayed along the margin of a word-processing application, or to indicate which file in a list of files is being displayed, such as on a **Window** menu.</span></span>  
  
-   <span data-ttu-id="ab46b-105">Adicione imagens que representem visualmente os comandos de menu.</span><span class="sxs-lookup"><span data-stu-id="ab46b-105">Add images that visually represent menu commands.</span></span>  
  
-   <span data-ttu-id="ab46b-106">Exiba teclas de atalho para oferecer uma alternativa de teclado ao mouse para executar comandos.</span><span class="sxs-lookup"><span data-stu-id="ab46b-106">Display shortcut keys to provide a keyboard alternative to the mouse for performing commands.</span></span> <span data-ttu-id="ab46b-107">Por exemplo, pressionar CTRL+C executa o comando **Copiar**.</span><span class="sxs-lookup"><span data-stu-id="ab46b-107">For example, pressing CTRL+C performs the **Copy** command.</span></span>  
  
-   <span data-ttu-id="ab46b-108">Exiba chaves de acesso para oferecer uma alternativa de teclado ao mouse para navegação de menu.</span><span class="sxs-lookup"><span data-stu-id="ab46b-108">Display access keys to provide a keyboard alternative to the mouse for menu navigation.</span></span> <span data-ttu-id="ab46b-109">Por exemplo, pressionar ALT+F escolhe o menu **Arquivo**.</span><span class="sxs-lookup"><span data-stu-id="ab46b-109">For example, pressing ALT+F chooses the **File** menu.</span></span>  
  
-   <span data-ttu-id="ab46b-110">Mostre barras de separação para agrupar comandos relacionados e tornar os menus mais legíveis.</span><span class="sxs-lookup"><span data-stu-id="ab46b-110">Show separator bars to group related commands and make menus more readable.</span></span>  
  
### <a name="to-display-a-check-mark-on-a-menu-command"></a><span data-ttu-id="ab46b-111">Para exibir uma marca de seleção em um comando de menu</span><span class="sxs-lookup"><span data-stu-id="ab46b-111">To display a check mark on a menu command</span></span>  
  
-   <span data-ttu-id="ab46b-112">Definir seu <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> propriedade `true`.</span><span class="sxs-lookup"><span data-stu-id="ab46b-112">Set its <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> property to `true`.</span></span>  
  
     <span data-ttu-id="ab46b-113">Isso também define o <xref:System.Windows.Forms.ToolStripMenuItem.CheckState%2A> propriedade `true`.</span><span class="sxs-lookup"><span data-stu-id="ab46b-113">This also sets the <xref:System.Windows.Forms.ToolStripMenuItem.CheckState%2A> property to `true`.</span></span> <span data-ttu-id="ab46b-114">Use este procedimento somente se desejar que o comando de menu apareça como marcado por padrão, independentemente de estar selecionado.</span><span class="sxs-lookup"><span data-stu-id="ab46b-114">Use this procedure only if you want the menu command to appear as checked by default, regardless of whether it is selected.</span></span>  
  
### <a name="to-display-a-check-mark-that-changes-state-with-each-click"></a><span data-ttu-id="ab46b-115">Para exibir uma marca de seleção que altere o estado de cada clique</span><span class="sxs-lookup"><span data-stu-id="ab46b-115">To display a check mark that changes state with each click</span></span>  
  
-   <span data-ttu-id="ab46b-116">Defina o comando de menu <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> propriedade `true`.</span><span class="sxs-lookup"><span data-stu-id="ab46b-116">Set the menu command's <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> property to `true`.</span></span>  
  
### <a name="to-add-an-image-to-a-menu-command"></a><span data-ttu-id="ab46b-117">Para adicionar uma imagem a um comando de menu</span><span class="sxs-lookup"><span data-stu-id="ab46b-117">To add an image to a menu command</span></span>  
  
-   <span data-ttu-id="ab46b-118">Defina o comando de menu <xref:System.Windows.Forms.ToolStripItem.Image%2A> propriedade para o nome da imagem.</span><span class="sxs-lookup"><span data-stu-id="ab46b-118">Set the menu command's <xref:System.Windows.Forms.ToolStripItem.Image%2A> property to the name of the image.</span></span> <span data-ttu-id="ab46b-119">Se o <xref:System.Windows.Forms.ToolStripItemDisplayStyle> propriedade deste comando de menu é definida como <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> ou <xref:System.Windows.Forms.ToolStripItemDisplayStyle.None>, a imagem não pode ser exibida.</span><span class="sxs-lookup"><span data-stu-id="ab46b-119">If the <xref:System.Windows.Forms.ToolStripItemDisplayStyle> property of this menu command is set to <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> or <xref:System.Windows.Forms.ToolStripItemDisplayStyle.None>, the image cannot be displayed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ab46b-120">A margem de imagem também poderá mostrar uma marca de seleção se você quiser.</span><span class="sxs-lookup"><span data-stu-id="ab46b-120">The image margin can also show a check mark if you so choose.</span></span> <span data-ttu-id="ab46b-121">Além disso, você pode definir o <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> propriedades da imagem para `true`, e a imagem será exibida com uma borda tracejada ao redor dele em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="ab46b-121">Also, you can set the <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> property of the image to `true`, and the image will appear with a hatched border around it at run time.</span></span>  
  
### <a name="to-display-a-shortcut-key-for-a-menu-command"></a><span data-ttu-id="ab46b-122">Para exibir uma tecla de atalho para um comando de menu</span><span class="sxs-lookup"><span data-stu-id="ab46b-122">To display a shortcut key for a menu command</span></span>  
  
-   <span data-ttu-id="ab46b-123">Defina o comando de menu <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys%2A> propriedade para a combinação de teclado desejado, como CTRL + A para o **abrir** comando de menu e defina o <xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A> propriedade para `true`.</span><span class="sxs-lookup"><span data-stu-id="ab46b-123">Set the menu command's <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys%2A> property to the desired keyboard combination, such as CTRL+O for the **Open** menu command, and set the <xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A> property to `true`.</span></span>  
  
### <a name="to-display-custom-shortcut-keys-for-a-menu-command"></a><span data-ttu-id="ab46b-124">Para exibir teclas de atalho personalizadas para um comando de menu</span><span class="sxs-lookup"><span data-stu-id="ab46b-124">To display custom shortcut keys for a menu command</span></span>  
  
-   <span data-ttu-id="ab46b-125">Definir o comando de menu <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeyDisplayString%2A> propriedade para a combinação de teclado desejado, como CTRL + SHIFT + O, em vez de SHIFT + CTRL + O e conjunto de <xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A> propriedade para `true`.</span><span class="sxs-lookup"><span data-stu-id="ab46b-125">Set the menu command's <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeyDisplayString%2A> property to the desired keyboard combination, such as CTRL+SHIFT+O rather than SHIFT+CTRL+O, and set the <xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A> property to `true`.</span></span>  
  
### <a name="to-display-an-access-key-for-a-menu-command"></a><span data-ttu-id="ab46b-126">Para exibir uma chave de acesso para um comando de menu</span><span class="sxs-lookup"><span data-stu-id="ab46b-126">To display an access key for a menu command</span></span>  
  
-   <span data-ttu-id="ab46b-127">Quando você define o <xref:System.Windows.Forms.ToolStripItem.Text%2A> propriedade para o comando de menu, digite um e comercial (&) antes da letra que você deseja ser sublinhadas como a chave de acesso.</span><span class="sxs-lookup"><span data-stu-id="ab46b-127">When you set the <xref:System.Windows.Forms.ToolStripItem.Text%2A> property for the menu command, enter an ampersand (&) before the letter you want to be underlined as the access key.</span></span> <span data-ttu-id="ab46b-128">Por exemplo, digitando `&Open` como o <xref:System.Windows.Forms.ToolStripItem.Text%2A> propriedade de um item de menu resultará em um comando de menu que aparece como **O**caneta.</span><span class="sxs-lookup"><span data-stu-id="ab46b-128">For example, typing `&Open` as the <xref:System.Windows.Forms.ToolStripItem.Text%2A> property of a menu item will result in a menu command that appears as **O**pen.</span></span>  
  
     <span data-ttu-id="ab46b-129">Para navegar para este comando de menu, pressione ALT para dar o foco para o <xref:System.Windows.Forms.MenuStrip>e pressione a tecla de acesso do nome do menu.</span><span class="sxs-lookup"><span data-stu-id="ab46b-129">To navigate to this menu command, press ALT to give focus to the <xref:System.Windows.Forms.MenuStrip>, and press the access key of the menu name.</span></span> <span data-ttu-id="ab46b-130">Quando o menu é aberto e mostra os itens com chaves de acesso, basta pressionar a tecla de acesso para selecionar o comando de menu.</span><span class="sxs-lookup"><span data-stu-id="ab46b-130">When the menu opens and shows items with access keys, you only need to press the access key to select the menu command.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ab46b-131">Evite definir teclas de acesso duplicadas, como definir ALT+F duas vezes no mesmo sistema de menu.</span><span class="sxs-lookup"><span data-stu-id="ab46b-131">Avoid defining duplicate access keys, such as defining ALT+F twice in the same menu system.</span></span> <span data-ttu-id="ab46b-132">Não é possível garantir a ordem de seleção das teclas de acesso duplicadas.</span><span class="sxs-lookup"><span data-stu-id="ab46b-132">The selection order of duplicate access keys cannot be guaranteed.</span></span>  
  
### <a name="to-display-a-separator-bar-between-menu-commands"></a><span data-ttu-id="ab46b-133">Para exibir uma barra separadora entre os comandos de menu</span><span class="sxs-lookup"><span data-stu-id="ab46b-133">To display a separator bar between menu commands</span></span>  
  
-   <span data-ttu-id="ab46b-134">Depois de definir seu <xref:System.Windows.Forms.MenuStrip> e os itens que ele contém, use o <xref:System.Windows.Forms.ToolStripItemCollection.AddRange%2A> ou <xref:System.Windows.Forms.ToolStripItemCollection.Add%2A> para adicionar os comandos de menu e <xref:System.Windows.Forms.ToolStripSeparator> controles para o <xref:System.Windows.Forms.MenuStrip> na ordem desejada.</span><span class="sxs-lookup"><span data-stu-id="ab46b-134">After you define your <xref:System.Windows.Forms.MenuStrip> and the items it will contain, use the <xref:System.Windows.Forms.ToolStripItemCollection.AddRange%2A> or <xref:System.Windows.Forms.ToolStripItemCollection.Add%2A> method to add the menu commands and <xref:System.Windows.Forms.ToolStripSeparator> controls to the <xref:System.Windows.Forms.MenuStrip> in the order you want.</span></span>  
  
    ```vb  
    ' This code adds a top-level File menu to the MenuStrip.  
    Me.menuStrip1.Items.Add(New ToolStripMenuItem() _  
    {Me.fileToolStripMenuItem})  
  
    ' This code adds the New and Open menu commands, a separator bar,   
    ' and the Save and Exit menu commands to the top-level File menu,   
    ' in that order.  
    Me.fileToolStripMenuItem.DropDownItems.AddRange(New _  
    ToolStripMenuItem() {Me.newToolStripMenuItem, _  
    Me.openToolStripMenuItem, Me.toolStripSeparator1, _  
    Me.saveToolStripMenuItem, Me.exitToolStripMenuItem})  
    ```  
  
    ```csharp  
    // This code adds a top-level File menu to the MenuStrip.  
    this.menuStrip1.Items.Add(new ToolStripItem[]_  
    {this.fileToolStripMenuItem});  
  
    // This code adds the New and Open menu commands, a separator bar,   
    // and the Save and Exit menu commands to the top-level File menu,   
    // in that order.  
    this.fileToolStripMenuItem.DropDownItems.AddRange(new _  
    ToolStripItem[] {  
    this.newToolStripMenuItem,  
    this.openToolStripMenuItem,  
    this.toolStripSeparator1,  
    this.saveToolStripMenuItem,  
    this.exitToolStripMenuItem});  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="ab46b-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ab46b-135">See Also</span></span>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStripMenuItem>  
 [<span data-ttu-id="ab46b-136">Visão geral do controle MenuStrip</span><span class="sxs-lookup"><span data-stu-id="ab46b-136">MenuStrip Control Overview</span></span>](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)
