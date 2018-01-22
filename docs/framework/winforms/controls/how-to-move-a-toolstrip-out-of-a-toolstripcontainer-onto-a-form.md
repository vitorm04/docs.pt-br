---
title: "Como remover um ToolStrip de um ToolStripContainer para um formulário"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ToolStrip control [Windows Forms], parenting to forms
- Windows Forms, parenting ToolStrip controls
ms.assetid: a1c94a7f-6fc5-4e4c-84cf-ff11dc573d33
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 97d65abf38ee434218fa9bec0d8a9cade31fb687
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
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
