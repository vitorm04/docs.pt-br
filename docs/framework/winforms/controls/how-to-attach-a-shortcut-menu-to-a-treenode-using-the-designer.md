---
title: 'Como: Anexar um menu de atalho a um TreeNode usando o designer'
ms.date: 03/30/2017
helpviewer_keywords:
- shortcut menus [Windows Forms], attaching to TreeNodes
- TreeNode [Windows Forms], attaching a shortcut menu using Designer
ms.assetid: 8e45e184-1313-4f8f-90ff-2cd5789b2268
ms.openlocfilehash: eb3240d35309e03aa8ce949b9c5000f8581d2c2f
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040454"
---
# <a name="how-to-attach-a-shortcut-menu-to-a-treenode-using-the-designer"></a>Como: Anexar um menu de atalho a um TreeNode usando o designer
O controle <xref:System.Windows.Forms.TreeView> Windows Forms exibe uma hierarquia de nós, semelhante aos arquivos e pastas exibidos no painel esquerdo do recurso Windows Explorer em sistemas operacionais Windows. Ao definir a <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> Propriedade, você pode fornecer operações sensíveis ao contexto ao usuário ao clicar com o botão direito do <xref:System.Windows.Forms.TreeView> mouse no controle. Ao associar um <xref:System.Windows.Forms.ContextMenuStrip> componente a itens individuais <xref:System.Windows.Forms.TreeNode> , você pode adicionar um nível personalizado de funcionalidade de menu de atalho para <xref:System.Windows.Forms.TreeView> seus controles.

## <a name="to-associate-a-shortcut-menu-with-a-treenode-at-design-time"></a>Para associar um menu de atalho a um TreeNode em tempo de design

1. Adicione um <xref:System.Windows.Forms.TreeView> controle ao seu formulário e, em seguida, adicione nós <xref:System.Windows.Forms.TreeView> ao conforme necessário. Para obter mais informações, confira [Como: Adicione e remova nós com o Windows Forms controle](how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)TreeView.

2. Adicione um <xref:System.Windows.Forms.ContextMenuStrip> componente ao formulário e, em seguida, adicione itens de menu ao menu de atalho que representam operações em nível de nó que você deseja disponibilizar em tempo de execução. Para obter mais informações, confira [Como: Adicione itens de menu a um](how-to-add-menu-items-to-a-contextmenustrip.md)ContextMenuStrip.

3. Reabra a caixa de diálogo **TreeNodeEditor** para <xref:System.Windows.Forms.TreeView> o controle, selecione o nó a ser editado e <xref:System.Windows.Forms.ContextMenuStrip> defina sua propriedade para o menu de atalho que você adicionou.

4. Quando essa propriedade for definida, o menu de atalho será exibido quando você clicar no nó com o botão direito do mouse.

     Além disso, você desejará escrever código para manipular <xref:System.Windows.Forms.ToolStripItem.Click> os eventos para esses itens de menu.

## <a name="see-also"></a>Consulte também

- [Controle TreeView](treeview-control-windows-forms.md)
- [Visão geral do controle TreeView](treeview-control-overview-windows-forms.md)
- [Controle ContextMenuStrip](contextmenustrip-control.md)
