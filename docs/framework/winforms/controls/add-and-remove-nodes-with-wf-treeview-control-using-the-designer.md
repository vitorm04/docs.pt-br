---
title: Adicionar e remover nós com controle TreeView usando o designer
ms.date: 03/30/2017
helpviewer_keywords:
- examples [Windows Forms], TreeView control
- TreeView control [Windows Forms], removing nodes
- tree nodes in TreeView control
- TreeView control [Windows Forms], adding nodes
ms.assetid: 35bf1750-045e-4ec5-97cb-b47b0dbdaa2c
ms.openlocfilehash: 7edf09539719ec76fa3f650254c5c84ff0bc3af7
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76732246"
---
# <a name="how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control-using-the-designer"></a>Como adicionar e remover nós com o componente TreeView dos Windows Forms usando o designer

Como o controle de <xref:System.Windows.Forms.TreeView> de Windows Forms exibe nós de maneira hierárquica, ao adicionar um nó, você deve prestar atenção ao que é seu nó pai.

O procedimento a seguir requer um projeto de **aplicativo do Windows** com um formulário que contém um controle <xref:System.Windows.Forms.TreeView>. Para obter informações sobre como configurar esse projeto, consulte [como: criar um projeto de aplicativo Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) e [como adicionar controles ao Windows Forms](how-to-add-controls-to-windows-forms.md).

### <a name="to-add-or-remove-nodes-in-the-designer"></a>Para adicionar ou remover nós no designer

1. Selecione o controle <xref:System.Windows.Forms.TreeView>.

2. Na janela **Propriedades** , clique nas **reticências** (![botão de reticências (...) no botão janela Propriedades do Visual Studio.](./media/visual-studio-ellipsis-button.png)) ao lado da propriedade <xref:System.Windows.Forms.TreeView.Nodes%2A>.

     O **Editor TreeNode** é exibido.

3. Para adicionar nós, deve existir um nó raiz; se não existir, primeiro adicione uma raiz clicando no botão **Adicionar Raiz**. Em seguida, adicione nós filho, selecionando a raiz ou qualquer outro nó e clicando no botão **Adicionar Filho**.

4. Para excluir nós, selecione o nó a ser excluído e clique no botão **Excluir**.

## <a name="see-also"></a>Veja também

- [Controle TreeView](treeview-control-windows-forms.md)
- [Visão geral do controle TreeView](treeview-control-overview-windows-forms.md)
- [Como definir ícones para o controle TreeView dos Windows Forms](how-to-set-icons-for-the-windows-forms-treeview-control.md)
- [Como iterar em todos os nós de um controle TreeView dos Windows Forms](how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)
- [Como determinar qual nó TreeView foi clicado](how-to-determine-which-treeview-node-was-clicked-windows-forms.md)
- [Como adicionar informações personalizadas a um controle TreeView ou ListView (Windows Forms)](add-custom-information-to-a-treeview-or-listview-control-wf.md)
