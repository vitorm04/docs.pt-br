---
title: Como remover um ToolStrip de um ToolStripContainer para um formulário
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStrip control [Windows Forms], parenting to forms
- Windows Forms, parenting ToolStrip controls
ms.assetid: a1c94a7f-6fc5-4e4c-84cf-ff11dc573d33
ms.openlocfilehash: a4b6e3bbc0750ba69607b5c0f96bdbb542aea1be
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43424087"
---
# <a name="how-to-move-a-toolstrip-out-of-a-toolstripcontainer-onto-a-form"></a>Como remover um ToolStrip de um ToolStripContainer para um formulário
Use o procedimento a seguir para mover uma <xref:System.Windows.Forms.ToolStrip> fora de um <xref:System.Windows.Forms.ToolStripContainer> para um formulário.  
  
> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-move-a-toolstrip-out-of-a-toolstripcontainer-onto-a-form"></a>Para mover um ToolStrip fora de um ToolStripContainer para um formulário  
  
1.  Selecione o <xref:System.Windows.Forms.ToolStrip>.  
  
2.  Recortar a <xref:System.Windows.Forms.ToolStrip> por pressionando CTRL + X ou clique com botão direito do <xref:System.Windows.Forms.ToolStrip> e escolha **Recortar** no menu de contexto.  
  
3.  Selecione o formulário.  
  
4.  Cole a <xref:System.Windows.Forms.ToolStrip> por pressionando CTRL + V ou escolha **colar** da **editar** menu.  
  
5.  Defina a <xref:System.Windows.Forms.ToolStrip.Dock%2A> propriedade do <xref:System.Windows.Forms.ToolStrip> para **superior**.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.ToolStripContainer>  
 [Visão geral do controle ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)
