---
title: 'Como: Desabilitar ToolStripMenuItems usando o designer'
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStripMenuItems [Windows Forms], disabling in designer
- MenuStrip control [Windows Forms], disabling menu items in designer
- menu items [Windows Forms], disabling
- menus [Windows Forms], disabling items
ms.assetid: 985e311e-7d67-4205-b5a3-d045b68a4a03
ms.openlocfilehash: fd80a6543c83ae957cd9c51b068d0702559f0925
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040264"
---
# <a name="how-to-disable-toolstripmenuitems-using-the-designer"></a>Como: Desabilitar ToolStripMenuItems usando o designer
Você pode limitar ou ampliar os comandos que um usuário pode fazer ao habilitar e desabilitar itens de menu em resposta a atividades do usuário. Os itens de menu são habilitados por padrão quando são criados, mas isso pode ser ajustado <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> por meio da propriedade. Você pode manipular essa propriedade em tempo de design na janela **Propriedades** ou programaticamente configurando ela no código. Para obter mais informações, confira [Como: Desabilite](how-to-disable-toolstripmenuitems.md)o ToolStripMenuItems.

## <a name="to-disable-a-menu-item-at-design-time"></a>Para desabilitar um item de menu em tempo de design

1. Com o item de menu selecionado no formulário, defina a <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> Propriedade como `false`.

    > [!TIP]
    >  Desabilitar o primeiro item de menu ou o de nível superior em um menu desabilita todos os itens de menu contidos no menu. Da mesma forma, desabilitar um item de menu que tenha itens de submenu desabilita os itens do submenu. Se todos os comandos em um determinado menu estiverem indisponíveis para o usuário, ocultar e desabilitar todo o menu será considerado uma boa prática de programação, pois isso apresenta uma interface do usuário mais enxuta. Você deve ocultar e desabilitar o menu, pois apenas ocultar não impede o acesso a um comando de menu por meio de uma tecla de atalho. Defina a <xref:System.Windows.Forms.ToolStripItem.Visible%2A> propriedade de um item de menu de nível superior `false` como para ocultar o menu inteiro.

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- [Como: Ocultar ToolStripMenuItems](how-to-hide-toolstripmenuitems.md)
- [Visão geral do controle MenuStrip](menustrip-control-overview-windows-forms.md)
