---
title: 'Como: Desabilitar ToolStripMenuItems'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- ToolStripMenuItems [Windows Forms], enabling
- ToolStripMenuItems [Windows Forms], disabling
- menu items [Windows Forms], disabling
- disabling menu items
- menu items [Windows Forms], enabling
- menus [Windows Forms], disabling menu items
ms.assetid: bcc1da84-50fd-41d2-8475-103b581d5654
ms.openlocfilehash: f86a2934e799e4604693491dacbecc517d44d810
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046219"
---
# <a name="how-to-disable-toolstripmenuitems"></a>Como: Desabilitar ToolStripMenuItems
Você pode limitar ou ampliar os comandos que um usuário pode fazer ao habilitar e desabilitar itens de menu em resposta a atividades do usuário. Os itens de menu são habilitados por padrão quando são criados, mas isso pode ser ajustado <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> por meio da propriedade. Você pode manipular essa propriedade em tempo de design na janela **Propriedades** ou programaticamente configurando ela no código.  
  
### <a name="to-disable-a-menu-item-programmatically"></a>Para desabilitar um item de menu programaticamente  
  
- Dentro do método em que você define as propriedades do item de menu, adicione o código para <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> definir a `false`Propriedade como.  
  
    ```vb  
    MenuItem1.Enabled = False  
    ```  
  
    ```csharp  
    menuItem1.Enabled = false;  
    ```  
  
    ```cpp  
    menuItem1->Enabled = false;  
    ```  
  
    > [!TIP]
    > Desabilitar o primeiro ou o item de menu de nível superior em um menu oculta todos os itens de menu contidos no menu, mas não os desabilita. Da mesma forma, desabilitar um item de menu que tem itens de submenu oculta os itens de submenu, mas não os desabilita. Se todos os comandos em um determinado menu estiverem indisponíveis para o usuário, ocultar e desabilitar todo o menu será considerado uma boa prática de programação, pois isso apresenta uma interface do usuário mais enxuta. Você deve ocultar e desabilitar o menu e desabilitar todos os itens de item e submenu no menu, pois a ocultação sozinha não impede o acesso a um comando de menu por meio de uma tecla de atalho. Defina a <xref:System.Windows.Forms.ToolStripItem.Visible%2A> propriedade de um item de menu de nível superior `false` como para ocultar o menu inteiro.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- [Como: Ocultar ToolStripMenuItems](how-to-hide-toolstripmenuitems.md)
- [Visão geral do controle MenuStrip](menustrip-control-overview-windows-forms.md)
