---
title: 'Como: Adicionar e remover nós com o componente TreeView do Windows Forms usando o designer'
ms.date: 03/30/2017
helpviewer_keywords:
- examples [Windows Forms], TreeView control
- TreeView control [Windows Forms], removing nodes
- tree nodes in TreeView control
- TreeView control [Windows Forms], adding nodes
ms.assetid: 35bf1750-045e-4ec5-97cb-b47b0dbdaa2c
ms.openlocfilehash: ecf0b758a9c45a0354a68b6cbfecdb1c49ab390f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61640360"
---
# <a name="how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control-using-the-designer"></a>Como: Adicionar e remover nós com o componente TreeView do Windows Forms usando o designer
Porque o Windows Forms <xref:System.Windows.Forms.TreeView> controle exibe nós de forma hierárquica, ao adicionar um nó que você deve prestar atenção a qual é seu nó pai.  
  
 O procedimento a seguir exige um **aplicativo do Windows** projeto com um formulário que contém um <xref:System.Windows.Forms.TreeView> controle. Para obter informações sobre como configurar um projeto desse tipo, consulte [como: Criar um projeto de aplicativo do Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) e [como: Adicionar controles ao Windows Forms](how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-add-or-remove-nodes-in-the-designer"></a>Para adicionar ou remover nós no designer  
  
1. Selecione o <xref:System.Windows.Forms.TreeView> controle.  
  
2. No **propriedades** janela, clique no **reticências** (![captura de tela de VisualStudioEllipsesButton](../media/vbellipsesbutton.png "vbEllipsesButton")) lado o <xref:System.Windows.Forms.TreeView.Nodes%2A> propriedade.  
  
     O **Editor TreeNode** é exibido.  
  
3. Para adicionar nós, deve existir um nó raiz; se não existir, primeiro adicione uma raiz clicando no botão **Adicionar Raiz**. Em seguida, adicione nós filho, selecionando a raiz ou qualquer outro nó e clicando no botão **Adicionar Filho**.  
  
4. Para excluir nós, selecione o nó a ser excluído e clique no botão **Excluir**.  
  
## <a name="see-also"></a>Consulte também

- [Controle TreeView](treeview-control-windows-forms.md)
- [Visão geral do controle TreeView](treeview-control-overview-windows-forms.md)
- [Como: Definir ícones para o controle TreeView dos Windows Forms](how-to-set-icons-for-the-windows-forms-treeview-control.md)
- [Como: Iterar em todos os nós de um controle TreeView dos Windows Forms](how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)
- [Como: Determinar qual nó TreeView foi clicado](how-to-determine-which-treeview-node-was-clicked-windows-forms.md)
- [Como: Adicionar informações personalizadas a um controle TreeView ou ListView (Windows Forms)](add-custom-information-to-a-treeview-or-listview-control-wf.md)
