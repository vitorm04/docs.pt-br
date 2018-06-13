---
title: Visão geral do controle TreeView (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- TreeView
helpviewer_keywords:
- TreeView control [Windows Forms], about TreeView control
ms.assetid: 0ece823a-9508-478a-bbdb-7d7c3bae51d5
ms.openlocfilehash: 6326f8976e20b5b72e1b6690ab323c8581411156
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33538620"
---
# <a name="treeview-control-overview-windows-forms"></a>Visão geral do controle TreeView (Windows Forms)
Com o Windows Forms <xref:System.Windows.Forms.TreeView> controle, você pode exibir uma hierarquia de nós para os usuários, como a forma como arquivos e pastas são exibidas no painel esquerdo do recurso Windows Explorer do sistema operacional Windows. Cada nó no modo de exibição de árvore pode conter outros nós, chamados *nós filho*. Você pode exibir nós pai ou nós que contêm nós filhos, como expandidos ou recolhidos. Você também pode exibir um modo de exibição de árvore com caixas de seleção ao lado de nós, definindo o modo de exibição de árvore <xref:System.Windows.Forms.TreeView.CheckBoxes%2A> propriedade `true`. Você pode, em seguida, por meio de programação marque ou desmarque nós definindo o nó <xref:System.Windows.Forms.TreeNode.Checked%2A> propriedade `true` ou `false`.  
  
## <a name="key-properties"></a>Propriedades da chave  
 Propriedades de chave do <xref:System.Windows.Forms.TreeView> controle são <xref:System.Windows.Forms.TreeView.Nodes%2A> e <xref:System.Windows.Forms.TreeView.SelectedNode%2A>. O <xref:System.Windows.Forms.TreeView.Nodes%2A> propriedade contém a lista de nós de nível superior na exibição de árvore. O <xref:System.Windows.Forms.TreeView.SelectedNode%2A> propriedade define o nó selecionado no momento. Você pode exibir ícones ao lado de nós. O controle usa imagens a partir de <xref:System.Windows.Forms.ImageList> nomeado na exibição de árvore <xref:System.Windows.Forms.TreeView.ImageList%2A> propriedade. O <xref:System.Windows.Forms.TreeView.ImageIndex%2A> propriedade define a imagem padrão para nós na exibição de árvore. Para obter mais informações sobre como exibir imagens, veja [Como definir ícones para o controle TreeView dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-set-icons-for-the-windows-forms-treeview-control.md). Se você estiver usando [!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)], você tem acesso a uma biblioteca grande de imagens padrão que você pode usar com o <xref:System.Windows.Forms.TreeView> controle.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.TreeView>  
 [Controle TreeView](../../../../docs/framework/winforms/controls/treeview-control-windows-forms.md)  
 [Como definir ícones para o controle TreeView dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-set-icons-for-the-windows-forms-treeview-control.md)  
 [Como adicionar e remover nós com o controle TreeView dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)  
 [Como iterar em todos os nós de um controle TreeView dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)  
 [Como determinar qual nó TreeView foi clicado](../../../../docs/framework/winforms/controls/how-to-determine-which-treeview-node-was-clicked-windows-forms.md)  
 [Como adicionar informações personalizadas a um controle TreeView ou ListView (Windows Forms)](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)
