---
title: "Visão geral do controle FlowLayoutPanel"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- FlowLayoutPanel
helpviewer_keywords:
- forms [Windows Forms], dynamic layout
- layout [Windows Forms], dynamic
- Windows Forms, dynamic layout
- FlowLayoutPanel control [Windows Forms], about FlowLayoutPanel control
ms.assetid: 3883e024-f5a0-456d-9c27-b4dfa1cc9045
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7eafe31bec86a969a12661c9f5629b2d55e3e3d8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
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
