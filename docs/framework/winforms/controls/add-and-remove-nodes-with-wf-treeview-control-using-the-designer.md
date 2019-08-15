---
title: 'Como: Adicionar e remover nós com o componente TreeView do Windows Forms usando o designer'
ms.date: 03/30/2017
helpviewer_keywords:
- examples [Windows Forms], TreeView control
- TreeView control [Windows Forms], removing nodes
- tree nodes in TreeView control
- TreeView control [Windows Forms], adding nodes
ms.assetid: 35bf1750-045e-4ec5-97cb-b47b0dbdaa2c
ms.openlocfilehash: ef3a963b5621f0b972b02a007681f600fbdb1050
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040074"
---
# <a name="how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control-using-the-designer"></a>Como: Adicionar e remover nós com o componente TreeView do Windows Forms usando o designer

Como o controle <xref:System.Windows.Forms.TreeView> de Windows Forms exibe nós de maneira hierárquica, ao adicionar um nó, você deve prestar atenção ao que é seu nó pai.

O procedimento a seguir requer um projeto de **aplicativo do Windows** com um <xref:System.Windows.Forms.TreeView> formulário que contém um controle. Para obter informações sobre como configurar esse projeto, consulte [como: Crie um projeto](/visualstudio/ide/step-1-create-a-windows-forms-application-project) de aplicativo Windows Forms [e como: Adicione controles a Windows Forms](how-to-add-controls-to-windows-forms.md).

### <a name="to-add-or-remove-nodes-in-the-designer"></a>Para adicionar ou remover nós no designer

1. Selecione o <xref:System.Windows.Forms.TreeView> controle.

2. Na janela **Propriedades** , clique nas **reticências** (![o botão de reticências (...) no janela Propriedades do Visual Studio](./media/visual-studio-ellipsis-button.png).) botão ao lado <xref:System.Windows.Forms.TreeView.Nodes%2A> da propriedade.

     O **Editor TreeNode** é exibido.

3. Para adicionar nós, deve existir um nó raiz; se não existir, primeiro adicione uma raiz clicando no botão **Adicionar Raiz**. Em seguida, adicione nós filho, selecionando a raiz ou qualquer outro nó e clicando no botão **Adicionar Filho**.

4. Para excluir nós, selecione o nó a ser excluído e clique no botão **Excluir**.

## <a name="see-also"></a>Consulte também

- [Controle TreeView](treeview-control-windows-forms.md)
- [Visão geral do controle TreeView](treeview-control-overview-windows-forms.md)
- [Como: Definir ícones para o Windows Forms controle TreeView](how-to-set-icons-for-the-windows-forms-treeview-control.md)
- [Como: Iterar em todos os nós de um Windows Forms controle TreeView](how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)
- [Como: Determinar qual nó TreeView foi clicado](how-to-determine-which-treeview-node-was-clicked-windows-forms.md)
- [Como: Adicionar informações personalizadas a um controle TreeView ou ListView (Windows Forms)](add-custom-information-to-a-treeview-or-listview-control-wf.md)
