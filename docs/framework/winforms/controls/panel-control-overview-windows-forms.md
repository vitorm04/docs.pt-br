---
title: "Visão geral do controle de painel (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: Panel
helpviewer_keywords:
- grouping controls [Windows Forms], Panel control
- Panel control [Windows Forms], about Panel control
ms.assetid: b6b83636-2c39-4dad-89d6-f0fa41049a74
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a8855c88a0ec60cd0d44d73046e44c9614347d90
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="panel-control-overview-windows-forms"></a>Visão geral do controle de painel (Windows Forms)
Windows Forms <xref:System.Windows.Forms.Panel> controles são usados para fornecer um agrupamento de identificação para outros controles. Normalmente, você usa painéis para subdividir um formulário por função. Por exemplo, você pode ter um formulário de pedido que especifica as opções de mala direta, como qual carrier noturna usar. Agrupar todas as opções em um painel fornece ao usuário uma indicação visual lógica. No design de tempo todos os controles podem ser movidos facilmente — quando você move o <xref:System.Windows.Forms.Panel> controlar, todos os seus controles contidos mover, muito. Os controles agrupados em um painel podem ser acessados por meio de seu <xref:System.Windows.Forms.Control.Controls%2A> propriedade. Essa propriedade retorna uma coleção de <xref:System.Windows.Forms.Control> instâncias, portanto, geralmente será necessário converter um controle recuperados dessa maneira ao seu tipo específico.  
  
## <a name="panel-versus-groupbox"></a>Painel Versus GroupBox  
 O <xref:System.Windows.Forms.Panel> controle é semelhante ao <xref:System.Windows.Forms.GroupBox> controlar; no entanto, somente o <xref:System.Windows.Forms.Panel> controle pode ter barras de rolagem e somente o <xref:System.Windows.Forms.GroupBox> controle exibe uma legenda.  
  
## <a name="key-properties"></a>Propriedades da chave  
 Para exibir as barras de rolagem, defina o <xref:System.Windows.Forms.ScrollableControl.AutoScroll%2A> propriedade `true`. Você também pode personalizar a aparência do painel, definindo o <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.BackgroundImage%2A>, e <xref:System.Windows.Forms.Panel.BorderStyle%2A> propriedades. Para obter mais informações sobre o <xref:System.Windows.Forms.Control.BackColor%2A> e <xref:System.Windows.Forms.Control.BackgroundImage%2A> propriedades, consulte [como: definir o plano de fundo de um painel](../../../../docs/framework/winforms/controls/how-to-set-the-background-of-a-windows-forms-panel.md). O <xref:System.Windows.Forms.Panel.BorderStyle%2A> propriedade determina se o painel é descrito com nenhuma borda visível (<xref:System.Windows.Forms.BorderStyle.None>), uma linha simples (<xref:System.Windows.Forms.BorderStyle.FixedSingle>), ou uma linha sombreada (<xref:System.Windows.Forms.BorderStyle.Fixed3D>).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.Panel>  
 [Controle GroupBox](../../../../docs/framework/winforms/controls/groupbox-control-windows-forms.md)  
 [Como agrupar controles com o controle de painel dos Windows Forms usando o Designer](../../../../docs/framework/winforms/controls/group-controls-with-wf-panel-control-using-the-designer.md)  
 [Como definir a tela de fundo de um painel dos Windows Forms usando o Designer](../../../../docs/framework/winforms/controls/how-to-set-the-background-of-a-windows-forms-panel-using-the-designer.md)
