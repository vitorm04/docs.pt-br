---
title: Visão geral do controle de painel
ms.date: 03/30/2017
f1_keywords:
- Panel
helpviewer_keywords:
- grouping controls [Windows Forms], Panel control
- Panel control [Windows Forms], about Panel control
ms.assetid: b6b83636-2c39-4dad-89d6-f0fa41049a74
ms.openlocfilehash: 3ea86e898e8a3e1ca90ba8e0a6240414702a1a73
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744311"
---
# <a name="panel-control-overview-windows-forms"></a>Visão geral do controle de painel (Windows Forms)
Windows Forms <xref:System.Windows.Forms.Panel> controles são usados para fornecer um agrupamento identificável para outros controles. Normalmente, você usa painéis para subdividir um formulário por função. Por exemplo, você pode ter um formulário de pedido que especifica as opções de mala direta, como qual carrier noturna usar. Agrupar todas as opções em um painel fornece ao usuário uma indicação visual lógica. Em tempo de design, todos os controles podem ser movidos facilmente — quando você move o controle de <xref:System.Windows.Forms.Panel>, todos os controles contidos também se movem. Os controles agrupados em um painel podem ser acessados por meio de sua propriedade <xref:System.Windows.Forms.Control.Controls%2A>. Essa propriedade retorna uma coleção de instâncias de <xref:System.Windows.Forms.Control>, portanto, normalmente, você precisará converter um controle recuperado dessa maneira para seu tipo específico.  
  
## <a name="panel-versus-groupbox"></a>Painel Versus GroupBox  
 O controle de <xref:System.Windows.Forms.Panel> é semelhante ao controle de <xref:System.Windows.Forms.GroupBox>; no entanto, somente o controle <xref:System.Windows.Forms.Panel> pode ter barras de rolagem e somente o controle <xref:System.Windows.Forms.GroupBox> exibe uma legenda.  
  
## <a name="key-properties"></a>Propriedades da chave  
 Para exibir barras de rolagem, defina a propriedade <xref:System.Windows.Forms.ScrollableControl.AutoScroll%2A> como `true`. Você também pode personalizar a aparência do painel definindo as propriedades <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.BackgroundImage%2A>e <xref:System.Windows.Forms.Panel.BorderStyle%2A>. Para obter mais informações sobre as propriedades <xref:System.Windows.Forms.Control.BackColor%2A> e <xref:System.Windows.Forms.Control.BackgroundImage%2A>, consulte [como: definir o plano de fundo de um painel](how-to-set-the-background-of-a-windows-forms-panel.md). A propriedade <xref:System.Windows.Forms.Panel.BorderStyle%2A> determina se o painel é descrito sem nenhuma borda visível (<xref:System.Windows.Forms.BorderStyle.None>), uma linha simples (<xref:System.Windows.Forms.BorderStyle.FixedSingle>) ou uma linha sombreada (<xref:System.Windows.Forms.BorderStyle.Fixed3D>).  
  
## <a name="see-also"></a>Veja também

- <xref:System.Windows.Forms.Panel>
- [Controle GroupBox](groupbox-control-windows-forms.md)
- [Como agrupar controles com o controle de painel dos Windows Forms usando o Designer](group-controls-with-wf-panel-control-using-the-designer.md)
- [Como definir a tela de fundo de um painel dos Windows Forms usando o Designer](how-to-set-the-background-of-a-windows-forms-panel-using-the-designer.md)
