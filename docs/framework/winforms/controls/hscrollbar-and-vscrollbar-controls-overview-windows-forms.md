---
title: Visão geral de controles HScrollBar e VScrollBar
ms.date: 03/30/2017
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
ms.openlocfilehash: abe0c8da9723f17cb80715454f6ab7297724a21f
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728167"
---
# <a name="hscrollbar-and-vscrollbar-controls-overview-windows-forms"></a>Visão geral dos controles HScrollBar e VScrollBar (Windows Forms)
Windows Forms <xref:System.Windows.Forms.ScrollBar> controles são usados para fornecer navegação fácil por meio de uma longa lista de itens ou uma grande quantidade de informações, rolando horizontalmente ou verticalmente dentro de um aplicativo ou controle. As barras de rolagem são um elemento comum da interface do Windows, de modo que o controle de <xref:System.Windows.Forms.ScrollBar> geralmente é usado com controles que não derivam da classe <xref:System.Windows.Forms.ScrollableControl>. Da mesma forma, muitos desenvolvedores optam por incorporar o controle de <xref:System.Windows.Forms.ScrollBar> ao criar seus próprios controles de usuário.  
  
 Os controles <xref:System.Windows.Forms.HScrollBar> (horizontal) e <xref:System.Windows.Forms.VScrollBar> (vertical) operam independentemente de outros controles e têm seu próprio conjunto de eventos, propriedades e métodos. os controles de <xref:System.Windows.Forms.ScrollBar> não são iguais às barras de rolagem internas que são anexadas a caixas de texto, caixas de listagem, caixas de combinação ou formulários MDI (o controle <xref:System.Windows.Forms.TextBox> tem uma propriedade <xref:System.Windows.Forms.TextBox.ScrollBars%2A> para mostrar ou ocultar as barras de rolagem que são anexadas ao controle).  
  
 Os controles de <xref:System.Windows.Forms.ScrollBar> usam o evento <xref:System.Windows.Forms.ScrollBar.Scroll> para monitorar a movimentação da caixa de rolagem (às vezes chamada de Thumb) ao longo da barra de rolagem. O uso do evento <xref:System.Windows.Forms.ScrollBar.Scroll> fornece acesso ao valor da barra de rolagem à medida que é arrastado.  
  
## <a name="value-property"></a>Propriedade Value  
 A propriedade <xref:System.Windows.Forms.ScrollBar.Value%2A> (que, por padrão, é 0) é um valor `integer` correspondente à posição da caixa de rolagem na barra de rolagem. Quando a posição da caixa de rolagem é o valor mínimo, ela se move para a posição mais à esquerda (para barras de rolagem horizontais) ou a posição superior (para barras de rolagem verticais). Quando a caixa de rolagem está no valor máximo, ela se move para a posição mais à direita ou para a posição inferior. Da mesma forma, um valor entre a parte inferior e superior do intervalo coloca a borda esquerda da caixa de rolagem no meio da barra de rolagem.  
  
 Além de usar cliques do mouse para alterar o valor da barra de rolagem, um usuário também pode arrastar a caixa de rolagem para qualquer ponto ao longo da barra. O valor resultante depende da posição da caixa de rolagem, mas está sempre dentro do intervalo da <xref:System.Windows.Forms.ScrollBar.Minimum%2A> para <xref:System.Windows.Forms.ScrollBar.Maximum%2A> propriedades definidas pelo usuário.  
  
## <a name="largechange-and-smallchange-properties"></a>Propriedades de SmallChange e LargeChange  
 Quando o usuário pressiona a tecla PAGE UP ou PAGE DOWN ou clica na faixa da barra de rolagem em qualquer lado da caixa de rolagem, a propriedade <xref:System.Windows.Forms.ScrollBar.Value%2A> muda de acordo com o valor definido na propriedade <xref:System.Windows.Forms.ScrollBar.LargeChange%2A>.  
  
 Quando o usuário pressiona uma das teclas de direção ou clica em um dos botões da barra de rolagem, a propriedade <xref:System.Windows.Forms.ScrollBar.Value%2A> muda de acordo com o valor definido na propriedade <xref:System.Windows.Forms.ScrollBar.SmallChange%2A>.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.HScrollBar>
- <xref:System.Windows.Forms.VScrollBar>
- [Controles a serem usados no Windows Forms](controls-to-use-on-windows-forms.md)
