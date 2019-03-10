---
title: Visão geral do controle de painel (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- Panel
helpviewer_keywords:
- grouping controls [Windows Forms], Panel control
- Panel control [Windows Forms], about Panel control
ms.assetid: b6b83636-2c39-4dad-89d6-f0fa41049a74
ms.openlocfilehash: 2b70996f7944f3f5ef8ef8bc80015836956a9b00
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57715497"
---
# <a name="panel-control-overview-windows-forms"></a>Visão geral do controle de painel (Windows Forms)
Windows Forms <xref:System.Windows.Forms.Panel> controles são usados para fornecer um agrupamento identificável para outros controles. Normalmente, você usa painéis para subdividir um formulário por função. Por exemplo, você pode ter um formulário de pedido que especifica as opções de mala direta, como qual carrier noturna usar. Agrupar todas as opções em um painel fornece ao usuário uma indicação visual lógica. No tempo de design todos os controles podem ser movidos facilmente — quando você move o <xref:System.Windows.Forms.Panel> controlar todos os seus controles contidos se movem também. Os controles agrupados em um painel podem ser acessados por meio de seu <xref:System.Windows.Forms.Control.Controls%2A> propriedade. Essa propriedade retorna uma coleção de <xref:System.Windows.Forms.Control> instâncias, portanto, você geralmente precisará converter um controle recuperado dessa forma para seu tipo específico.  
  
## <a name="panel-versus-groupbox"></a>Painel Versus GroupBox  
 O <xref:System.Windows.Forms.Panel> controle é semelhante ao <xref:System.Windows.Forms.GroupBox> controle; no entanto, somente o <xref:System.Windows.Forms.Panel> controle pode ter barras de rolagem e apenas o <xref:System.Windows.Forms.GroupBox> controle exibe uma legenda.  
  
## <a name="key-properties"></a>Propriedades da chave  
 Para exibir as barras de rolagem, defina as <xref:System.Windows.Forms.ScrollableControl.AutoScroll%2A> propriedade para `true`. Você também pode personalizar a aparência do painel, definindo a <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.BackgroundImage%2A>, e <xref:System.Windows.Forms.Panel.BorderStyle%2A> propriedades. Para obter mais informações sobre o <xref:System.Windows.Forms.Control.BackColor%2A> e <xref:System.Windows.Forms.Control.BackgroundImage%2A> propriedades, consulte [como: Definir plano de fundo de um painel](how-to-set-the-background-of-a-windows-forms-panel.md). O <xref:System.Windows.Forms.Panel.BorderStyle%2A> propriedade determina se o painel é destacado com nenhuma borda visível (<xref:System.Windows.Forms.BorderStyle.None>), uma linha simples (<xref:System.Windows.Forms.BorderStyle.FixedSingle>), ou uma linha sombreada (<xref:System.Windows.Forms.BorderStyle.Fixed3D>).  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Windows.Forms.Panel>
- [Controle GroupBox](groupbox-control-windows-forms.md)
- [Como: Agrupar controles com o controle de painel do Windows Forms usando o Designer](group-controls-with-wf-panel-control-using-the-designer.md)
- [Como: Definir plano de fundo de um painel dos Windows Forms usando o Designer](how-to-set-the-background-of-a-windows-forms-panel-using-the-designer.md)
