---
title: 'Como: Mover ToolStripMenuItems'
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStripMenuItems [Windows Forms], moving
- menus [Windows Forms], arranging items
- ToolStripMenuItems [Windows Forms], dragging and dropping
- menu items [Windows Forms], moving
- menu items [Windows Forms], cutting and pasting
- menu items [Windows Forms], dragging and dropping
- MenuStrip control [Windows Forms], arranging items
- ToolStripMenuItems [Windows Forms], cutting and pasting
ms.assetid: cab9e03e-4edd-4c25-b3e3-bd1edc602bd9
ms.openlocfilehash: 12554ee2225dbb186392b910ddfd7c2f69695e7e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54660210"
---
# <a name="how-to-move-toolstripmenuitems"></a>Como: Mover ToolStripMenuItems
Em tempo de design, você pode mover todos os menus de nível superior e seus itens de menu para um local diferente <xref:System.Windows.Forms.MenuStrip>. Você também pode mover itens de menu individuais entre menus de nível superior ou alterar a posição dos itens de menu dentro de um menu.  
  
> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-move-a-top-level-menu-and-its-menu-items-to-another-top-level-location"></a>Mover um menu de nível superior e seus itens de menu para outro local de nível superior  
  
1.  Clique e mantenha pressionado o botão esquerdo do mouse no menu que você deseja mover.  
  
2.  Arraste o ponto de inserção para o menu de nível superior que está antes do novo local desejado e solte o botão esquerdo do mouse.  
  
     O menu selecionado se move para a direita do ponto de inserção.  
  
### <a name="to-move-a-top-level-menu-and-its-menu-items-to-a-drop-down-location"></a>Mover um menu de nível superior e seus itens de menu para outro local suspenso  
  
1.  Clique com o botão esquerdo do mouse no menu que você deseja mover e pressione CTRL + X ou clique com o botão direito do mouse no menu e selecione **Recortar** no menu de atalho.  
  
2.  No menu de nível superior de destino, clique com o botão esquerdo do mouse no item de menu acima do novo local desejado e pressione CTRL + V, ou clique com o botão direito do mouse no item de menu acima do novo local desejado e selecione **Colar** no menu de atalho.  
  
     O menu que você recorta é inserido após o item de menu selecionado.  
  
### <a name="to-move-a-menu-item-within-a-menu-using-the-items-collection-editor"></a>Mover um item de menu de dentro de um menu usando o Editor de coleção de itens  
  
1.  Clique com o botão direito do mouse no menu que contém o item de menu que você deseja mover.  
  
2.  No menu de atalho, escolha **Editar DropDownItems**.  
  
3.  No **Editor de Coleção de Itens**, clique com o botão esquerdo do mouse no item de menu que você deseja mover.  
  
4.  Clique nas teclas de direção para cima e para baixo para mover o item de menu no menu.  
  
5.  Clique em **OK**.  
  
### <a name="to-move-a-menu-item-within-a-menu-using-the-keyboard"></a>Mover um item de menu de dentro de um menu usando o teclado  
  
1.  Pressione e mantenha a tecla ALT pressionada.  
  
2.  Clique e mantenha pressionado o botão esquerdo do mouse no item de menu que você deseja mover.  
  
3.  Arraste o item de menu para o novo local e solte o botão esquerdo do mouse.  
  
### <a name="to-move-a-menu-item-to-another-menu"></a>Mover um item de menu para outro menu  
  
1.  Clique com o botão esquerdo do mouse no item de menu que você deseja mover e pressione CTRL + X ou clique com o botão direito do mouse no item de menu e escolha **Recortar** no menu de atalho.  
  
2.  Clique com o botão esquerdo do mouse no menu que contém o item de menu que você recortou.  
  
3.  Clique com o botão esquerdo do mouse no item de menu anterior ao novo local desejado e pressione CTRL + V, ou clique com o botão direito do mouse no item de menu anterior ao novo local desejado e selecione **Colar** no menu de atalho.  
  
     O item de menu que você recortou é inserido após o item de menu selecionado.  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- [Visão geral do controle MenuStrip](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)
