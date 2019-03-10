---
title: Visão geral do controle TreeView (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- TreeView
helpviewer_keywords:
- TreeView control [Windows Forms], about TreeView control
ms.assetid: 0ece823a-9508-478a-bbdb-7d7c3bae51d5
ms.openlocfilehash: 046713745e7de18cefe5b4883af73034af2cfb31
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57711989"
---
# <a name="treeview-control-overview-windows-forms"></a>Visão geral do controle TreeView (Windows Forms)

Com os formulários do Windows <xref:System.Windows.Forms.TreeView> controle, você pode exibir uma hierarquia de nós para os usuários, como a forma como arquivos e pastas são exibidos no painel esquerdo do recurso Windows Explorer do sistema operacional Windows. Cada nó no modo de exibição de árvore pode conter outros nós, chamados *nós filho*. Você pode exibir nós pai ou nós que contêm nós filhos, como expandidos ou recolhidos. Você também pode exibir uma exibição de árvore com caixas de seleção ao lado de nós, definindo o modo de exibição de árvore <xref:System.Windows.Forms.TreeView.CheckBoxes%2A> propriedade para `true`. Você pode, em seguida, por meio de programação selecionados ou desmarcar os nós, definindo o nó <xref:System.Windows.Forms.TreeNode.Checked%2A> propriedade para `true` ou `false`.

## <a name="key-properties"></a>Propriedades da chave

As propriedades da chave de <xref:System.Windows.Forms.TreeView> controle estão <xref:System.Windows.Forms.TreeView.Nodes%2A> e <xref:System.Windows.Forms.TreeView.SelectedNode%2A>. O <xref:System.Windows.Forms.TreeView.Nodes%2A> propriedade contém a lista de nós de nível superior na exibição de árvore. O <xref:System.Windows.Forms.TreeView.SelectedNode%2A> propriedade define o nó atualmente selecionado. Você pode exibir ícones ao lado de nós. O controle usa imagens a partir de <xref:System.Windows.Forms.ImageList> nomeada na exibição de árvore <xref:System.Windows.Forms.TreeView.ImageList%2A> propriedade. O <xref:System.Windows.Forms.TreeView.ImageIndex%2A> propriedade define a imagem padrão para nós na exibição de árvore. Para obter mais informações sobre como exibir imagens, consulte [como: Definir ícones para o Windows Forms controle TreeView](how-to-set-icons-for-the-windows-forms-treeview-control.md). Se você estiver usando o Visual Studio 2005, você tem acesso a uma grande biblioteca de imagens padrão que você pode usar com o <xref:System.Windows.Forms.TreeView> controle.

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.TreeView>
- [Controle TreeView](treeview-control-windows-forms.md)
- [Como: Definir ícones para o controle TreeView dos Windows Forms](how-to-set-icons-for-the-windows-forms-treeview-control.md)
- [Como: Adicionar e remover nós com o controle TreeView dos Windows Forms](how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)
- [Como: Iterar em todos os nós de um controle TreeView dos Windows Forms](how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)
- [Como: Determinar qual nó TreeView foi clicado](how-to-determine-which-treeview-node-was-clicked-windows-forms.md)
- [Como: Adicionar informações personalizadas a um controle TreeView ou ListView (Windows Forms)](add-custom-information-to-a-treeview-or-listview-control-wf.md)