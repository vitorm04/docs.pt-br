---
title: Visão geral do controle FlowLayoutPanel
ms.date: 03/30/2017
f1_keywords:
- FlowLayoutPanel
helpviewer_keywords:
- forms [Windows Forms], dynamic layout
- layout [Windows Forms], dynamic
- Windows Forms, dynamic layout
- FlowLayoutPanel control [Windows Forms], about FlowLayoutPanel control
ms.assetid: 3883e024-f5a0-456d-9c27-b4dfa1cc9045
ms.openlocfilehash: 58d95c2238687b4822155916177172a34c3abb87
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33526719"
---
# <a name="flowlayoutpanel-control-overview"></a>Visão geral do controle FlowLayoutPanel
O <xref:System.Windows.Forms.FlowLayoutPanel> controle organiza seu conteúdo em uma direção de fluxo horizontal ou vertical. Você pode encapsular o conteúdo do controle de uma linha para outra ou de uma coluna para a próxima. Como alternativa, você pode recortar, em vez de encapsular seu conteúdo.  
  
 Você pode especificar a direção de fluxo, definindo o valor da <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> propriedade. O <xref:System.Windows.Forms.FlowLayoutPanel> controle corretamente inverte a direção de fluxo em layouts da direita para esquerda (RTL). Você também pode especificar se o <xref:System.Windows.Forms.FlowLayoutPanel> conteúdo do controle é encapsulado ou recortado, definindo o valor da <xref:System.Windows.Forms.FlowLayoutPanel.WrapContents%2A> propriedade.  
  
 O <xref:System.Windows.Forms.FlowLayoutPanel> controlar tamanhos para seu conteúdo automaticamente, quando você define o <xref:System.Windows.Forms.Control.AutoSize%2A> propriedade `true`. Ele também fornece uma propriedade **FlowBreak** para seus controles filho. Definir o valor da propriedade FlowBreak para `true` faz com que o <xref:System.Windows.Forms.FlowLayoutPanel> controle parar dispor controles no contorno para a próxima linha ou coluna e direção do fluxo atual.  
  
 Qualquer controle de formulários do Windows pode ser um filho de <xref:System.Windows.Forms.FlowLayoutPanel> controle, inclusive de outras instâncias de <xref:System.Windows.Forms.FlowLayoutPanel>. Com esse capacidade, você pode criar layouts sofisticados que se adaptam às dimensões do formulário em tempo de execução.  
  
 Consulte também [Explicação passo a passo: organizando controles nos Windows Forms utilizando um FlowLayoutPanel](http://msdn.microsoft.com/library/z9w7ek2f\(v=vs.110\)).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A>  
 <xref:System.Windows.Forms.TableLayoutPanel>  
 [Controle FlowLayoutPanel](../../../../docs/framework/winforms/controls/flowlayoutpanel-control-windows-forms.md)
