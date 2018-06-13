---
title: Como remover um ToolStrip de um ToolStripContainer para um formulário
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStrip control [Windows Forms], parenting to forms
- Windows Forms, parenting ToolStrip controls
ms.assetid: a1c94a7f-6fc5-4e4c-84cf-ff11dc573d33
ms.openlocfilehash: 6cc54264033eca541ce845b75d608087fee8a542
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33532309"
---
# <a name="how-to-move-a-toolstrip-out-of-a-toolstripcontainer-onto-a-form"></a>Como remover um ToolStrip de um ToolStripContainer para um formulário
Use o procedimento a seguir para mover um <xref:System.Windows.Forms.ToolStrip> fora de um <xref:System.Windows.Forms.ToolStripContainer> em um formulário.  
  
> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-move-a-toolstrip-out-of-a-toolstripcontainer-onto-a-form"></a>Para mover um ToolStrip fora de um ToolStripContainer para um formulário  
  
1.  Selecione o <xref:System.Windows.Forms.ToolStrip>.  
  
2.  Recortar a <xref:System.Windows.Forms.ToolStrip> por pressionando CTRL + X ou com o botão direito do <xref:System.Windows.Forms.ToolStrip> e escolha **Recortar** no menu de contexto.  
  
3.  Selecione o formulário.  
  
4.  Colar o <xref:System.Windows.Forms.ToolStrip> por pressionando CTRL + V, ou escolha **colar** do **editar** menu.  
  
5.  Definir o <xref:System.Windows.Forms.ToolStrip.Dock%2A> propriedade o <xref:System.Windows.Forms.ToolStrip> para **superior**.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.ToolStripContainer>  
 [Visão geral do controle ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)
