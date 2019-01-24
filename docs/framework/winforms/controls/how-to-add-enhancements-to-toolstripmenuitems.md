---
title: 'Como: Adicionar melhorias a ToolStripMenuItems'
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
ms.openlocfilehash: 621b96805543abb92bc73f734f1a090d9cdb7319
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54685072"
---
# <a name="how-to-add-enhancements-to-toolstripmenuitems"></a>Como: Adicionar melhorias a ToolStripMenuItems
Você pode aprimorar a usabilidade dos <xref:System.Windows.Forms.MenuStrip> e <xref:System.Windows.Forms.ContextMenuStrip> controles das seguintes maneiras:  
  
-   Adicione marcas de seleção para designar se um recurso está ativado ou desativado, como se uma régua é exibida ao longo da margem de um aplicativo de processamento de texto ou para indicar qual arquivo em uma lista de arquivos está sendo exibido, como em um menu **Janela**.  
  
-   Adicione imagens que representem visualmente os comandos de menu.  
  
-   Exiba teclas de atalho para oferecer uma alternativa de teclado ao mouse para executar comandos. Por exemplo, pressionar CTRL+C executa o comando **Copiar**.  
  
-   Exiba chaves de acesso para oferecer uma alternativa de teclado ao mouse para navegação de menu. Por exemplo, pressionar ALT+F escolhe o menu **Arquivo**.  
  
-   Mostre barras de separação para agrupar comandos relacionados e tornar os menus mais legíveis.  
  
### <a name="to-display-a-check-mark-on-a-menu-command"></a>Para exibir uma marca de seleção em um comando de menu  
  
-   Defina suas <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> propriedade para `true`.  
  
     Isso também define o <xref:System.Windows.Forms.ToolStripMenuItem.CheckState%2A> propriedade para `true`. Use este procedimento somente se desejar que o comando de menu apareça como marcado por padrão, independentemente de estar selecionado.  
  
### <a name="to-display-a-check-mark-that-changes-state-with-each-click"></a>Para exibir uma marca de seleção que altere o estado de cada clique  
  
-   Definir o comando de menu <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> propriedade para `true`.  
  
### <a name="to-add-an-image-to-a-menu-command"></a>Para adicionar uma imagem a um comando de menu  
  
-   Definir o comando de menu <xref:System.Windows.Forms.ToolStripItem.Image%2A> propriedade para o nome da imagem. Se o <xref:System.Windows.Forms.ToolStripItemDisplayStyle> propriedade desse comando de menu é definida como <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> ou <xref:System.Windows.Forms.ToolStripItemDisplayStyle.None>, a imagem não pode ser exibida.  
  
> [!NOTE]
>  A margem de imagem também poderá mostrar uma marca de seleção se você quiser. Além disso, você pode definir as <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> propriedades da imagem a ser `true`, e a imagem será exibida com uma borda hachurada ao redor dele em tempo de execução.  
  
### <a name="to-display-a-shortcut-key-for-a-menu-command"></a>Para exibir uma tecla de atalho para um comando de menu  
  
-   Definir o comando de menu <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys%2A> propriedade para a combinação de teclado desejada, como CTRL + A para o **aberto** comando de menu e um conjunto a <xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A> propriedade para `true`.  
  
### <a name="to-display-custom-shortcut-keys-for-a-menu-command"></a>Para exibir teclas de atalho personalizadas para um comando de menu  
  
-   Definir o comando de menu <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeyDisplayString%2A> propriedade para a combinação de teclado desejada, como CTRL + SHIFT + O, em vez de CTRL + SHIFT + O e conjunto de <xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A> propriedade para `true`.  
  
### <a name="to-display-an-access-key-for-a-menu-command"></a>Para exibir uma chave de acesso para um comando de menu  
  
-   Quando você define o <xref:System.Windows.Forms.ToolStripItem.Text%2A> propriedade para o comando de menu, digite um e comercial (&) antes da letra que você deseja que a chave de acesso sublinhada. Por exemplo, digitar `&Open` como o <xref:System.Windows.Forms.ToolStripItem.Text%2A> propriedade de um item de menu resulta em um comando de menu que aparece como <u>s</u>caneta.
  
     Para navegar para esse comando de menu, pressione a tecla ALT para dar o foco para o <xref:System.Windows.Forms.MenuStrip>e pressione a tecla de acesso do nome do menu. Quando o menu é aberto e mostra os itens com chaves de acesso, basta pressionar a tecla de acesso para selecionar o comando de menu.  
  
> [!NOTE]
>  Evite definir teclas de acesso duplicadas, como definir ALT+F duas vezes no mesmo sistema de menu. Não é possível garantir a ordem de seleção das teclas de acesso duplicadas.  
  
### <a name="to-display-a-separator-bar-between-menu-commands"></a>Para exibir uma barra separadora entre os comandos de menu  
  
-   Depois de definir seu <xref:System.Windows.Forms.MenuStrip> e os itens que ele conterá, use o <xref:System.Windows.Forms.ToolStripItemCollection.AddRange%2A> ou <xref:System.Windows.Forms.ToolStripItemCollection.Add%2A> método para adicionar os comandos de menu e <xref:System.Windows.Forms.ToolStripSeparator> controles para o <xref:System.Windows.Forms.MenuStrip> na ordem desejada.  
  
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
  
## <a name="see-also"></a>Consulte também
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- [Visão geral do controle MenuStrip](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)
