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
ms.openlocfilehash: a480cd29eef1a79a69f702eed7cd02c28d7ea3de
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61954214"
---
# <a name="how-to-disable-toolstripmenuitems"></a>Como: Desabilitar ToolStripMenuItems
Você pode limitar ou ampliar os comandos que um usuário pode fazer ao habilitar e desabilitar itens de menu em resposta a atividades do usuário. Itens de menu são habilitados por padrão, quando eles são criados, mas isso pode ser ajustado por meio de <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> propriedade. Você pode manipular essa propriedade em tempo de design na janela **Propriedades** ou programaticamente configurando ela no código.  
  
### <a name="to-disable-a-menu-item-programmatically"></a>Para desabilitar um item de menu por meio de programação  
  
- Dentro do método em que você definir as propriedades do item de menu, adicionar código para definir a <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> propriedade para `false`.  
  
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
    >  Desabilitar o item de menu de nível superior ou primeiro em um menu oculta todos os itens de menu contidos no menu, mas não desabilitá-los. Da mesma forma, desabilitar um item de menu que tem itens de submenu oculta os itens de submenu, mas não desabilitá-los. Se todos os comandos em um determinado menu estiverem indisponíveis para o usuário, ocultar e desabilitar todo o menu será considerado uma boa prática de programação, pois isso apresenta uma interface do usuário mais enxuta. Você deve ocultar e desabilitar o menu e desabilitar cada item e o item de submenu no menu, pois ocultando sozinho não impede o acesso a um comando de menu por meio de uma tecla de atalho. Defina as <xref:System.Windows.Forms.ToolStripItem.Visible%2A> propriedade de um item de menu de nível superior para `false` para ocultar o menu inteiro.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- [Como: Ocultar ToolStripMenuItems](how-to-hide-toolstripmenuitems.md)
- [Visão geral do controle MenuStrip](menustrip-control-overview-windows-forms.md)
