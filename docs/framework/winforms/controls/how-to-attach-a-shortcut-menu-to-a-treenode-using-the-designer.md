---
title: Como anexar um menu de atalho a um TreeNode usando o designer
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- shortcut menus [Windows Forms], attaching to TreeNodes
- TreeNode [Windows Forms], attaching a shortcut menu using Designer
ms.assetid: 8e45e184-1313-4f8f-90ff-2cd5789b2268
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3acc1a731fa584a17c8a96f8a02986a504cd302d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-attach-a-shortcut-menu-to-a-treenode-using-the-designer"></a>Como anexar um menu de atalho a um TreeNode usando o designer
Windows Forms <xref:System.Windows.Forms.TreeView> controle exibe uma hierarquia de nós, semelhantes aos arquivos e pastas exibidas no painel esquerdo do recurso Windows Explorer em sistemas operacionais Windows. Definindo o <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> propriedade, você pode fornecer operações sensíveis ao contexto para o usuário quando eles com o botão direito do <xref:System.Windows.Forms.TreeView> controle. Associando um <xref:System.Windows.Forms.ContextMenuStrip> componente com individuais <xref:System.Windows.Forms.TreeNode> itens, você pode adicionar um nível personalizado de funcionalidade do menu de atalho para o <xref:System.Windows.Forms.TreeView> controles.  
  
> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-associate-a-shortcut-menu-with-a-treenode-at-design-time"></a>Para associar um menu de atalho a um TreeNode em tempo de design  
  
1.  Adicionar um <xref:System.Windows.Forms.TreeView> o controle para o formulário e, em seguida, adicionar nós a <xref:System.Windows.Forms.TreeView> conforme necessário. Para obter mais informações, veja [Como adicionar e remover nós com o controle TreeView dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md).  
  
2.  Adicionar uma <xref:System.Windows.Forms.ContextMenuStrip> ao formulário, o componente e, em seguida, adicionar itens de menu ao menu de atalho que representam as operações de nível de nó que você deseja disponibilizar em tempo de execução. Para obter mais informações, veja [Como adicionar itens de menu a um ContextMenuStrip](../../../../docs/framework/winforms/controls/how-to-add-menu-items-to-a-contextmenustrip.md).  
  
3.  Reabra o **TreeNodeEditor** caixa de diálogo para o <xref:System.Windows.Forms.TreeView> de controle, selecione o nó para editar e definir seu <xref:System.Windows.Forms.ContextMenuStrip> propriedade para o menu de atalho que você adicionou.  
  
4.  Quando essa propriedade for definida, o menu de atalho será exibido quando você clicar no nó com o botão direito do mouse.  
  
     Além disso, você deve escrever código para manipular o <xref:System.Windows.Forms.ToolStripItem.Click> eventos para esses itens de menu.  
  
## <a name="see-also"></a>Consulte também  
 [Controle TreeView](../../../../docs/framework/winforms/controls/treeview-control-windows-forms.md)  
 [Visão geral do controle TreeView](../../../../docs/framework/winforms/controls/treeview-control-overview-windows-forms.md)  
 [Controle ContextMenuStrip](../../../../docs/framework/winforms/controls/contextmenustrip-control.md)
