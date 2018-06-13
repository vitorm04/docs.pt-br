---
title: Como desabilitar ToolStripMenuItems usando o designer
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStripMenuItems [Windows Forms], disabling in designer
- MenuStrip control [Windows Forms], disabling menu items in designer
- menu items [Windows Forms], disabling
- menus [Windows Forms], disabling items
ms.assetid: 985e311e-7d67-4205-b5a3-d045b68a4a03
ms.openlocfilehash: 3ce18d40910145a076cc7084e2fba8ee0229c21f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33531548"
---
# <a name="how-to-disable-toolstripmenuitems-using-the-designer"></a>Como desabilitar ToolStripMenuItems usando o designer
Você pode limitar ou ampliar os comandos que um usuário pode fazer ao habilitar e desabilitar itens de menu em resposta a atividades do usuário. Itens de menu são habilitados por padrão, quando eles são criados, mas isso pode ser ajustado por meio de <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> propriedade. Você pode manipular essa propriedade em tempo de design na janela **Propriedades** ou programaticamente configurando ela no código. Para obter mais informações, consulte [Como desabilitar ToolStripMenuItems](../../../../docs/framework/winforms/controls/how-to-disable-toolstripmenuitems.md).  
  
> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-disable-a-menu-item-at-design-time"></a>Para desabilitar um item de menu em tempo de design  
  
1.  Com o item de menu selecionado no formulário, defina o <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> propriedade `false`.  
  
    > [!TIP]
    >  Desabilitar o primeiro item de menu ou o de nível superior em um menu desabilita todos os itens de menu contidos no menu. Da mesma forma, desabilitar um item de menu que tenha itens de submenu desabilita os itens do submenu. Se todos os comandos em um determinado menu estiverem indisponíveis para o usuário, ocultar e desabilitar todo o menu será considerado uma boa prática de programação, pois isso apresenta uma interface do usuário mais enxuta. Você deve ocultar e desabilitar o menu, pois apenas ocultar não impede o acesso a um comando de menu por meio de uma tecla de atalho. Definir o <xref:System.Windows.Forms.ToolStripItem.Visible%2A> propriedade de um item de menu de nível superior para `false` para ocultar o menu inteiro.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStripMenuItem>  
 [Como ocultar ToolStripMenuItems](../../../../docs/framework/winforms/controls/how-to-hide-toolstripmenuitems.md)  
 [Visão geral do controle MenuStrip](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)
