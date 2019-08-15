---
title: 'Como: Ocultar ToolStripMenuItems usando o designer'
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStripMenuItems [Windows Forms], hiding menu items in designer
- MenuStrip control [Windows Forms], hiding menu items in designer
- menu items [Windows Forms], hiding
ms.assetid: 8f1b057e-3d8a-4f11-88df-935f7b29a836
ms.openlocfilehash: 968d34a5f79d469ef62beaa8ac96742d73391b22
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039754"
---
# <a name="how-to-hide-toolstripmenuitems-using-the-designer"></a>Como: Ocultar ToolStripMenuItems usando o designer
Ocultar itens de menu é uma maneira de controlar a interface do usuário (IU) do seu aplicativo e restringir comandos do usuário. Geralmente, é recomendável ocultar um menu inteiro quando todos os itens de menu estão indisponíveis. Isso apresenta menos distrações para o usuário. Além disso, pode ser útil ocultar e desabilitar o menu ou item de menu, visto que apenas ocultar não impede que o usuário acesse um comando de menu usando uma tecla de atalho. Para obter mais informações sobre como desabilitar itens de menu [, consulte Como: Desabilite ToolStripMenuItems usando o](how-to-disable-toolstripmenuitems-using-the-designer.md)designer.

## <a name="to-hide-a-top-level-menu-and-its-submenu-items"></a>Ocultar um menu de nível superior e seus itens de submenu

1. Selecione o item de menu de nível superior e defina <xref:System.Windows.Forms.ToolStripItem.Visible%2A> sua <xref:System.Windows.Forms.ToolStripItem.Available%2A> propriedade ou `false`como.

     Quando você oculta o item de menu de nível superior, todos os itens de menu dentro desse menu também são ocultos. Se você clicar em algum lugar diferente de <xref:System.Windows.Forms.MenuStrip> na `false`configuração <xref:System.Windows.Forms.ToolStripItem.Visible%2A> após, o item de menu de nível superior inteiro e seus itens de submenu desaparecerão do formulário, mostrando assim o efeito de tempo de execução de sua ação. Para exibir o item de menu de nível superior oculto em tempo de design, clique <xref:System.Windows.Forms.MenuStrip> no na **bandeja de componentes**, em **estrutura de tópicos do documento**ou na parte superior da grade de propriedades.

> [!NOTE]
>  Você raramente ocultará um menu inteiro, exceto por menus filho MDI (interface de vários documentos) em um cenário de mesclagem.

## <a name="to-hide-a-submenu-item"></a>Ocultar um item de submenu

1. Selecione o item de submenu e defina <xref:System.Windows.Forms.ToolStripItem.Visible%2A> sua propriedade `false`como.

     Quando você oculta um item de submenu, ele permanece visível no formulário no tempo de design para que você pode selecioná-lo facilmente para continuar trabalhando nele. Ele será ocultado efetivamente no tempo de execução.

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.ToolStripItem.Visible%2A>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A>
- <xref:System.Windows.Forms.ToolStripItem.Available%2A>
- <xref:System.Windows.Forms.ToolStripMenuItem.Overflow%2A>
- [Visão geral do controle MenuStrip](menustrip-control-overview-windows-forms.md)
- [Como: Desabilitar ToolStripMenuItems usando o designer](how-to-disable-toolstripmenuitems-using-the-designer.md)
