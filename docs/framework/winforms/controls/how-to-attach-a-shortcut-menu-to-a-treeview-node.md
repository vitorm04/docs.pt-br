---
title: 'Como: Anexar um menu ShortCut a um nó TreeView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- shortcut menus [Windows Forms], adding to TreeView controls
- TreeView control [Windows Forms], adding shortcut menus
- tree nodes in TreeView control [Windows Forms], shortcut menus
ms.assetid: a23c6752-fd8f-44ad-b781-bab37962fc7c
ms.openlocfilehash: f818cccb3103866af993f1aff527a9c1a7c82109
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62053009"
---
# <a name="how-to-attach-a-shortcut-menu-to-a-treeview-node"></a>Como: Anexar um menu ShortCut a um nó TreeView
Os formulários do Windows <xref:System.Windows.Forms.TreeView> controle exibe uma hierarquia de nós, semelhantes aos arquivos e pastas exibidas no painel esquerdo do Windows Explorer. Definindo o <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> propriedade, você pode fornecer operações sensíveis ao contexto para o usuário quando eles com o botão direito do <xref:System.Windows.Forms.TreeView> controle. Associando um <xref:System.Windows.Forms.ContextMenuStrip> componente com indivíduo <xref:System.Windows.Forms.TreeNode> itens, você pode adicionar um nível personalizado de funcionalidade do menu de atalho para seu <xref:System.Windows.Forms.TreeView> controles.  
  
### <a name="to-associate-a-shortcut-menu-with-a-treenode-programmatically"></a>Para associar um menu de atalho a um TreeNode programaticamente  
  
1. Criar uma instância de um <xref:System.Windows.Forms.TreeView> controlar com as configurações de propriedade adequado, crie uma raiz <xref:System.Windows.Forms.TreeNode>e, em seguida, adicione subnós.  
  
2. Criar uma instância de um <xref:System.Windows.Forms.ContextMenuStrip> componente e, em seguida, adicione um <xref:System.Windows.Forms.ToolStripMenuItem> para cada operação que você deseja disponibilizar em tempo de execução.  
  
3. Defina as <xref:System.Windows.Forms.TreeNode.ContextMenuStrip%2A> propriedade do apropriado <xref:System.Windows.Forms.TreeNode> ao menu de atalho que você cria.  
  
4. Quando essa propriedade for definida, o menu de atalho será exibido quando você clicar no nó com o botão direito do mouse.  
  
 O exemplo de código a seguir cria um basic <xref:System.Windows.Forms.TreeView> e <xref:System.Windows.Forms.ContextMenuStrip> associados à raiz <xref:System.Windows.Forms.TreeNode> da <xref:System.Windows.Forms.TreeView>. Você precisará personalizar as opções de menu para que se ajustem a <xref:System.Windows.Forms.TreeView> você está desenvolvendo. Além disso, você vai querer escrever código para manipular o <xref:System.Windows.Forms.ToolStripItem.Click> eventos para esses itens de menu.  
  
 [!code-cpp[System.Windows.Forms.TreeNodeContextMenuStrip#1](~/samples/snippets/cpp/VS_Snippets_Winforms/system.windows.forms.TreeNodeContextMenuStrip/cpp/Form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.TreeNodeContextMenuStrip#1](~/samples/snippets/csharp/VS_Snippets_Winforms/system.windows.forms.TreeNodeContextMenuStrip/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.TreeNodeContextMenuStrip#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/system.windows.forms.TreeNodeContextMenuStrip/VB/Form1.vb#1)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.ContextMenuStrip>
- [Controle TreeView](treeview-control-windows-forms.md)
