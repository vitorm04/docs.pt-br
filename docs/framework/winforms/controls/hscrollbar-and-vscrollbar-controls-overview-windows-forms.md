---
title: "Visão geral dos controles HScrollBar e VScrollBar (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- HScrollBar
- VScrollBar
helpviewer_keywords:
- ScrollBar control [Windows Forms]
- HScrollBar control [Windows Forms], about HScrollBar
- VScrollBar control [Windows Forms], about VScrollBar control
- ScrollBar control [Windows Forms], about ScrollBar control
- scroll bars [Windows Forms], about scroll bars
ms.assetid: 8b307679-1cae-41d8-99aa-3d1efd207cd6
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8fbdb3778959d1691200cde49e485d8a63c6e645
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="hscrollbar-and-vscrollbar-controls-overview-windows-forms"></a>Visão geral dos controles HScrollBar e VScrollBar (Windows Forms)
Windows Forms <xref:System.Windows.Forms.ScrollBar> controles são usados para fornecer fácil navegação por uma longa lista de itens ou uma grande quantidade de informações por qualquer um de rolagem horizontal ou verticalmente dentro de um aplicativo ou controle. Barras de rolagem são um elemento comum da interface do Windows, portanto, o <xref:System.Windows.Forms.ScrollBar> controle é frequentemente usado com controles que não derivam o <xref:System.Windows.Forms.ScrollableControl> classe. Da mesma forma, muitos desenvolvedores escolhem incorporar o <xref:System.Windows.Forms.ScrollBar> controlar ao criar seus próprios controles de usuário.  
  
 O <xref:System.Windows.Forms.HScrollBar> (horizontal) e <xref:System.Windows.Forms.VScrollBar> (verticais) controles operar de forma independente de outros controles e ter seu próprio conjunto de eventos, propriedades e métodos. <xref:System.Windows.Forms.ScrollBar>controles não são o mesmo que as barras de rolagem internas que estão anexadas a caixas de texto, caixas de listagem, caixas de combinação ou formulários MDI (o <xref:System.Windows.Forms.TextBox> controle tem um <xref:System.Windows.Forms.TextBox.ScrollBars%2A> propriedade para mostrar ou ocultar as barras de rolagem que estão anexadas ao controle).  
  
 O <xref:System.Windows.Forms.ScrollBar> controla o uso de <xref:System.Windows.Forms.ScrollBar.Scroll> evento para monitorar a movimentação da caixa de rolagem (também conhecida como controle deslizante) ao longo da barra de rolagem. Usando o <xref:System.Windows.Forms.ScrollBar.Scroll> evento fornece acesso para o valor de barra de rolagem que está sendo arrastado.  
  
## <a name="value-property"></a>Propriedade Value  
 O <xref:System.Windows.Forms.ScrollBar.Value%2A> propriedade (que, por padrão, é 0) é um `integer` valor correspondente para a posição da caixa de rolagem na barra de rolagem. Quando a posição da caixa de rolagem é o valor mínimo, ela se move para a posição mais à esquerda (para barras de rolagem horizontais) ou a posição superior (para barras de rolagem verticais). Quando a caixa de rolagem está no valor máximo, ela se move para a posição mais à direita ou para a posição inferior. Da mesma forma, um valor entre a parte inferior e superior do intervalo coloca a borda esquerda da caixa de rolagem no meio da barra de rolagem.  
  
 Além de usar cliques do mouse para alterar o valor da barra de rolagem, um usuário também pode arrastar a caixa de rolagem para qualquer ponto ao longo da barra. O valor resultante depende da posição da caixa de rolagem, mas é sempre dentro do intervalo da <xref:System.Windows.Forms.ScrollBar.Minimum%2A> para <xref:System.Windows.Forms.ScrollBar.Maximum%2A> propriedades definidas pelo usuário.  
  
## <a name="largechange-and-smallchange-properties"></a>Propriedades de SmallChange e LargeChange  
 Quando o usuário pressiona a tecla PAGE UP ou PAGE DOWN ou clica na faixa de barra de rolagem em qualquer lado da caixa de rolagem, o <xref:System.Windows.Forms.ScrollBar.Value%2A> alterações de propriedade de acordo com o valor definido para o <xref:System.Windows.Forms.ScrollBar.LargeChange%2A> propriedade.  
  
 Quando o usuário pressiona uma seta de chaves ou clica em um dos botões da barra de rolagem, o <xref:System.Windows.Forms.ScrollBar.Value%2A> alterações de propriedade de acordo com o valor definido para o <xref:System.Windows.Forms.ScrollBar.SmallChange%2A> propriedade.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.HScrollBar>  
 <xref:System.Windows.Forms.VScrollBar>  
 [Adições para formulários do Windows para o .NET Framework 2.0](http://msdn.microsoft.com/library/c61a923d-3d6a-4c8c-820c-e94c83f3f9a8)  
 [Controles a serem usados nos Windows Forms](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
