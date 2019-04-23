---
title: 'Como: Anexar um menu de atalho a um TreeNode usando o designer'
ms.date: 03/30/2017
helpviewer_keywords:
- shortcut menus [Windows Forms], attaching to TreeNodes
- TreeNode [Windows Forms], attaching a shortcut menu using Designer
ms.assetid: 8e45e184-1313-4f8f-90ff-2cd5789b2268
ms.openlocfilehash: 9be633d14429bc2ceda1f0db2ff09252d55d5dd5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59337442"
---
# <a name="how-to-attach-a-shortcut-menu-to-a-treenode-using-the-designer"></a>Como: Anexar um menu de atalho a um TreeNode usando o designer
Os formulários do Windows <xref:System.Windows.Forms.TreeView> controle exibe uma hierarquia de nós, semelhantes aos arquivos e pastas exibidas no painel esquerdo do recurso Windows Explorer em sistemas de operacionais do Windows. Definindo o <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> propriedade, você pode fornecer operações sensíveis ao contexto para o usuário quando eles com o botão direito do <xref:System.Windows.Forms.TreeView> controle. Associando um <xref:System.Windows.Forms.ContextMenuStrip> componente com indivíduo <xref:System.Windows.Forms.TreeNode> itens, você pode adicionar um nível personalizado de funcionalidade do menu de atalho para seu <xref:System.Windows.Forms.TreeView> controles.  
  
> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-associate-a-shortcut-menu-with-a-treenode-at-design-time"></a>Para associar um menu de atalho a um TreeNode em tempo de design  
  
1. Adicionar um <xref:System.Windows.Forms.TreeView> controlar ao seu formulário e, em seguida, adicionar nós a <xref:System.Windows.Forms.TreeView> conforme necessário. Para obter mais informações, confira [Como: Adicionar e remover nós com o Windows Forms controle TreeView](how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md).  
  
2. Adicionar um <xref:System.Windows.Forms.ContextMenuStrip> ao seu formulário e, em seguida, adicionar itens de menu ao menu de atalho que representam as operações de nível de nó que você deseja disponibilizar em tempo de execução. Para obter mais informações, confira [Como: Adicionar itens de Menu a um ContextMenuStrip](how-to-add-menu-items-to-a-contextmenustrip.md).  
  
3. Reabra o **TreeNodeEditor** caixa de diálogo para o <xref:System.Windows.Forms.TreeView> de controle, selecione o nó para editar e defina seu <xref:System.Windows.Forms.ContextMenuStrip> propriedade para o menu de atalho que você adicionou.  
  
4. Quando essa propriedade for definida, o menu de atalho será exibido quando você clicar no nó com o botão direito do mouse.  
  
     Além disso, você vai querer escrever código para manipular o <xref:System.Windows.Forms.ToolStripItem.Click> eventos para esses itens de menu.  
  
## <a name="see-also"></a>Consulte também

- [Controle TreeView](treeview-control-windows-forms.md)
- [Visão geral do controle TreeView](treeview-control-overview-windows-forms.md)
- [Controle ContextMenuStrip](contextmenustrip-control.md)
