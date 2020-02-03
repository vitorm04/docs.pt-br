---
title: Visão geral do controle TreeView
ms.date: 03/30/2017
f1_keywords:
- TreeView
helpviewer_keywords:
- TreeView control [Windows Forms], about TreeView control
ms.assetid: 0ece823a-9508-478a-bbdb-7d7c3bae51d5
ms.openlocfilehash: 44b5e27273d122f38ea00e009302d427305977a3
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743216"
---
# <a name="treeview-control-overview-windows-forms"></a>Visão geral do controle TreeView (Windows Forms)

Com o controle de <xref:System.Windows.Forms.TreeView> de Windows Forms, você pode exibir uma hierarquia de nós para os usuários, como a maneira como os arquivos e pastas são exibidos no painel esquerdo do recurso do Windows Explorer do sistema operacional Windows. Cada nó no modo de exibição de árvore pode conter outros nós, chamados *nós filho*. Você pode exibir nós pai ou nós que contêm nós filhos, como expandidos ou recolhidos. Você também pode exibir um modo de exibição de árvore com caixas de seleção ao lado dos nós definindo a propriedade <xref:System.Windows.Forms.TreeView.CheckBoxes%2A> da exibição de árvore como `true`. Em seguida, você pode selecionar ou limpar os nós programaticamente definindo a propriedade <xref:System.Windows.Forms.TreeNode.Checked%2A> do nó como `true` ou `false`.

## <a name="key-properties"></a>Propriedades da chave

As propriedades de chave do controle de <xref:System.Windows.Forms.TreeView> são <xref:System.Windows.Forms.TreeView.Nodes%2A> e <xref:System.Windows.Forms.TreeView.SelectedNode%2A>. A propriedade <xref:System.Windows.Forms.TreeView.Nodes%2A> contém a lista de nós de nível superior no modo de exibição de árvore. A propriedade <xref:System.Windows.Forms.TreeView.SelectedNode%2A> define o nó selecionado no momento. Você pode exibir ícones ao lado de nós. O controle usa imagens do <xref:System.Windows.Forms.ImageList> nomeados na propriedade <xref:System.Windows.Forms.TreeView.ImageList%2A> da exibição de árvore. A propriedade <xref:System.Windows.Forms.TreeView.ImageIndex%2A> define a imagem padrão para nós no modo de exibição de árvore. Para obter mais informações sobre como exibir imagens, veja [Como definir ícones para o controle TreeView dos Windows Forms](how-to-set-icons-for-the-windows-forms-treeview-control.md). Se você estiver usando o Visual Studio 2005, terá acesso a uma grande biblioteca de imagens padrão que você pode usar com o controle de <xref:System.Windows.Forms.TreeView>.

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.TreeView>
- [Controle TreeView](treeview-control-windows-forms.md)
- [Como definir ícones para o controle TreeView dos Windows Forms](how-to-set-icons-for-the-windows-forms-treeview-control.md)
- [Como adicionar e remover nós com o controle TreeView dos Windows Forms](how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)
- [Como iterar em todos os nós de um controle TreeView dos Windows Forms](how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)
- [Como determinar qual nó TreeView foi clicado](how-to-determine-which-treeview-node-was-clicked-windows-forms.md)
- [Como adicionar informações personalizadas a um controle TreeView ou ListView (Windows Forms)](add-custom-information-to-a-treeview-or-listview-control-wf.md)
