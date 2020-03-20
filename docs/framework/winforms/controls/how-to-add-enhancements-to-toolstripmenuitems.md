---
title: Como adicionar melhorias a ToolStripMenuItems
ms.date: 03/30/2017
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
ms.openlocfilehash: 61a79b9bbe101d7bf694240bdffdecee5187adf2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182328"
---
# <a name="how-to-add-enhancements-to-toolstripmenuitems"></a><span data-ttu-id="cc244-102">Como adicionar melhorias a ToolStripMenuItems</span><span class="sxs-lookup"><span data-stu-id="cc244-102">How to: Add Enhancements to ToolStripMenuItems</span></span>
<span data-ttu-id="cc244-103">Você pode melhorar a <xref:System.Windows.Forms.MenuStrip> <xref:System.Windows.Forms.ContextMenuStrip> usabilidade e os controles das seguintes maneiras:</span><span class="sxs-lookup"><span data-stu-id="cc244-103">You can enhance the usability of <xref:System.Windows.Forms.MenuStrip> and <xref:System.Windows.Forms.ContextMenuStrip> controls in the following ways:</span></span>  
  
- <span data-ttu-id="cc244-104">Adicione marcas de seleção para designar se um recurso está ativado ou desativado, como se uma régua é exibida ao longo da margem de um aplicativo de processamento de texto ou para indicar qual arquivo em uma lista de arquivos está sendo exibido, como em um menu **Janela**.</span><span class="sxs-lookup"><span data-stu-id="cc244-104">Add check marks to designate whether a feature is turned on or off, such as whether a ruler is displayed along the margin of a word-processing application, or to indicate which file in a list of files is being displayed, such as on a **Window** menu.</span></span>  
  
- <span data-ttu-id="cc244-105">Adicione imagens que representem visualmente os comandos de menu.</span><span class="sxs-lookup"><span data-stu-id="cc244-105">Add images that visually represent menu commands.</span></span>  
  
- <span data-ttu-id="cc244-106">Exiba teclas de atalho para oferecer uma alternativa de teclado ao mouse para executar comandos.</span><span class="sxs-lookup"><span data-stu-id="cc244-106">Display shortcut keys to provide a keyboard alternative to the mouse for performing commands.</span></span> <span data-ttu-id="cc244-107">Por exemplo, pressionar CTRL+C executa o comando **Copiar**.</span><span class="sxs-lookup"><span data-stu-id="cc244-107">For example, pressing CTRL+C performs the **Copy** command.</span></span>  
  
- <span data-ttu-id="cc244-108">Exiba chaves de acesso para oferecer uma alternativa de teclado ao mouse para navegação de menu.</span><span class="sxs-lookup"><span data-stu-id="cc244-108">Display access keys to provide a keyboard alternative to the mouse for menu navigation.</span></span> <span data-ttu-id="cc244-109">Por exemplo, pressionar ALT+F escolhe o menu **Arquivo**.</span><span class="sxs-lookup"><span data-stu-id="cc244-109">For example, pressing ALT+F chooses the **File** menu.</span></span>  
  
- <span data-ttu-id="cc244-110">Mostre barras de separação para agrupar comandos relacionados e tornar os menus mais legíveis.</span><span class="sxs-lookup"><span data-stu-id="cc244-110">Show separator bars to group related commands and make menus more readable.</span></span>  
  
### <a name="to-display-a-check-mark-on-a-menu-command"></a><span data-ttu-id="cc244-111">Para exibir uma marca de seleção em um comando de menu</span><span class="sxs-lookup"><span data-stu-id="cc244-111">To display a check mark on a menu command</span></span>  
  
- <span data-ttu-id="cc244-112">Defina <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> sua `true`propriedade para .</span><span class="sxs-lookup"><span data-stu-id="cc244-112">Set its <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> property to `true`.</span></span>  
  
     <span data-ttu-id="cc244-113">Isso também <xref:System.Windows.Forms.ToolStripMenuItem.CheckState%2A> define `true`a propriedade para .</span><span class="sxs-lookup"><span data-stu-id="cc244-113">This also sets the <xref:System.Windows.Forms.ToolStripMenuItem.CheckState%2A> property to `true`.</span></span> <span data-ttu-id="cc244-114">Use este procedimento somente se desejar que o comando de menu apareça como marcado por padrão, independentemente de estar selecionado.</span><span class="sxs-lookup"><span data-stu-id="cc244-114">Use this procedure only if you want the menu command to appear as checked by default, regardless of whether it is selected.</span></span>  
  
### <a name="to-display-a-check-mark-that-changes-state-with-each-click"></a><span data-ttu-id="cc244-115">Para exibir uma marca de seleção que altere o estado de cada clique</span><span class="sxs-lookup"><span data-stu-id="cc244-115">To display a check mark that changes state with each click</span></span>  
  
- <span data-ttu-id="cc244-116">Defina a propriedade <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> do `true`comando do menu para .</span><span class="sxs-lookup"><span data-stu-id="cc244-116">Set the menu command's <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> property to `true`.</span></span>  
  
### <a name="to-add-an-image-to-a-menu-command"></a><span data-ttu-id="cc244-117">Para adicionar uma imagem a um comando de menu</span><span class="sxs-lookup"><span data-stu-id="cc244-117">To add an image to a menu command</span></span>  
  
- <span data-ttu-id="cc244-118">Defina a propriedade <xref:System.Windows.Forms.ToolStripItem.Image%2A> do comando do menu para o nome da imagem.</span><span class="sxs-lookup"><span data-stu-id="cc244-118">Set the menu command's <xref:System.Windows.Forms.ToolStripItem.Image%2A> property to the name of the image.</span></span> <span data-ttu-id="cc244-119">Se <xref:System.Windows.Forms.ToolStripItemDisplayStyle> a propriedade deste comando <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> menu <xref:System.Windows.Forms.ToolStripItemDisplayStyle.None>estiver definida para ou , a imagem não poderá ser exibida.</span><span class="sxs-lookup"><span data-stu-id="cc244-119">If the <xref:System.Windows.Forms.ToolStripItemDisplayStyle> property of this menu command is set to <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> or <xref:System.Windows.Forms.ToolStripItemDisplayStyle.None>, the image cannot be displayed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cc244-120">A margem de imagem também poderá mostrar uma marca de seleção se você quiser.</span><span class="sxs-lookup"><span data-stu-id="cc244-120">The image margin can also show a check mark if you so choose.</span></span> <span data-ttu-id="cc244-121">Além disso, você <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> pode definir `true`a propriedade da imagem para , e a imagem aparecerá com uma borda eclodida em torno dela no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="cc244-121">Also, you can set the <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> property of the image to `true`, and the image will appear with a hatched border around it at run time.</span></span>  
  
### <a name="to-display-a-shortcut-key-for-a-menu-command"></a><span data-ttu-id="cc244-122">Para exibir uma tecla de atalho para um comando de menu</span><span class="sxs-lookup"><span data-stu-id="cc244-122">To display a shortcut key for a menu command</span></span>  
  
- <span data-ttu-id="cc244-123">Defina a propriedade <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys%2A> do comando de menu para a combinação de teclado desejada, como <xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A> CTRL+O para o comando **Open** menu e defina a propriedade como `true`.</span><span class="sxs-lookup"><span data-stu-id="cc244-123">Set the menu command's <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys%2A> property to the desired keyboard combination, such as CTRL+O for the **Open** menu command, and set the <xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A> property to `true`.</span></span>  
  
### <a name="to-display-custom-shortcut-keys-for-a-menu-command"></a><span data-ttu-id="cc244-124">Para exibir teclas de atalho personalizadas para um comando de menu</span><span class="sxs-lookup"><span data-stu-id="cc244-124">To display custom shortcut keys for a menu command</span></span>  
  
- <span data-ttu-id="cc244-125">Defina a propriedade <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeyDisplayString%2A> do comando de menu para a combinação de teclado desejada, como CTRL+SHIFT+O em vez de SHIFT+CTRL+O, e defina a <xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A> propriedade como `true`.</span><span class="sxs-lookup"><span data-stu-id="cc244-125">Set the menu command's <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeyDisplayString%2A> property to the desired keyboard combination, such as CTRL+SHIFT+O rather than SHIFT+CTRL+O, and set the <xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A> property to `true`.</span></span>  
  
### <a name="to-display-an-access-key-for-a-menu-command"></a><span data-ttu-id="cc244-126">Para exibir uma chave de acesso para um comando de menu</span><span class="sxs-lookup"><span data-stu-id="cc244-126">To display an access key for a menu command</span></span>  
  
- <span data-ttu-id="cc244-127">Ao definir <xref:System.Windows.Forms.ToolStripItem.Text%2A> a propriedade para o comando menu, digite uma ampersand (&) antes da letra que deseja ser sublinhada como a chave de acesso.</span><span class="sxs-lookup"><span data-stu-id="cc244-127">When you set the <xref:System.Windows.Forms.ToolStripItem.Text%2A> property for the menu command, enter an ampersand (&) before the letter you want to be underlined as the access key.</span></span> <span data-ttu-id="cc244-128">Por exemplo, `&Open` digitar <xref:System.Windows.Forms.ToolStripItem.Text%2A> como propriedade de um item do menu resultará em um comando de menu que aparece como <u>caneta O.</u></span><span class="sxs-lookup"><span data-stu-id="cc244-128">For example, typing `&Open` as the <xref:System.Windows.Forms.ToolStripItem.Text%2A> property of a menu item will result in a menu command that appears as <u>O</u>pen.</span></span>
  
     <span data-ttu-id="cc244-129">Para navegar até este comando de menu, <xref:System.Windows.Forms.MenuStrip>pressione ALT para dar foco ao e pressione a tecla de acesso do nome do menu.</span><span class="sxs-lookup"><span data-stu-id="cc244-129">To navigate to this menu command, press ALT to give focus to the <xref:System.Windows.Forms.MenuStrip>, and press the access key of the menu name.</span></span> <span data-ttu-id="cc244-130">Quando o menu é aberto e mostra os itens com chaves de acesso, basta pressionar a tecla de acesso para selecionar o comando de menu.</span><span class="sxs-lookup"><span data-stu-id="cc244-130">When the menu opens and shows items with access keys, you only need to press the access key to select the menu command.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cc244-131">Evite definir teclas de acesso duplicadas, como definir ALT+F duas vezes no mesmo sistema de menu.</span><span class="sxs-lookup"><span data-stu-id="cc244-131">Avoid defining duplicate access keys, such as defining ALT+F twice in the same menu system.</span></span> <span data-ttu-id="cc244-132">Não é possível garantir a ordem de seleção das teclas de acesso duplicadas.</span><span class="sxs-lookup"><span data-stu-id="cc244-132">The selection order of duplicate access keys cannot be guaranteed.</span></span>  
  
### <a name="to-display-a-separator-bar-between-menu-commands"></a><span data-ttu-id="cc244-133">Para exibir uma barra separadora entre os comandos de menu</span><span class="sxs-lookup"><span data-stu-id="cc244-133">To display a separator bar between menu commands</span></span>  
  
- <span data-ttu-id="cc244-134">Depois de <xref:System.Windows.Forms.MenuStrip> definir o seu e os itens <xref:System.Windows.Forms.ToolStripItemCollection.AddRange%2A> <xref:System.Windows.Forms.ToolStripItemCollection.Add%2A> que ele conterá, <xref:System.Windows.Forms.ToolStripSeparator> use o <xref:System.Windows.Forms.MenuStrip> método ou para adicionar os comandos e controles do menu à ordem desejada.</span><span class="sxs-lookup"><span data-stu-id="cc244-134">After you define your <xref:System.Windows.Forms.MenuStrip> and the items it will contain, use the <xref:System.Windows.Forms.ToolStripItemCollection.AddRange%2A> or <xref:System.Windows.Forms.ToolStripItemCollection.Add%2A> method to add the menu commands and <xref:System.Windows.Forms.ToolStripSeparator> controls to the <xref:System.Windows.Forms.MenuStrip> in the order you want.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="cc244-135">Confira também</span><span class="sxs-lookup"><span data-stu-id="cc244-135">See also</span></span>

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- [<span data-ttu-id="cc244-136">Visão geral do controle MenuStrip</span><span class="sxs-lookup"><span data-stu-id="cc244-136">MenuStrip Control Overview</span></span>](menustrip-control-overview-windows-forms.md)
