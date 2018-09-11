---
title: Visão geral dos controles HScrollBar e VScrollBar (Windows Forms)
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
ms.openlocfilehash: 2c6436e77753322733580acba5a20d6bb220f29c
ms.sourcegitcommit: 67de6cb5dd66a19f2180ba7e4d7aecc697f8a963
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44342355"
---
# <a name="hscrollbar-and-vscrollbar-controls-overview-windows-forms"></a>Visão geral dos controles HScrollBar e VScrollBar (Windows Forms)
Windows Forms <xref:System.Windows.Forms.ScrollBar> controles são usados para fornecer uma navegação fácil por meio de uma longa lista de itens ou uma grande quantidade de informações ao rolar horizontal ou verticalmente dentro de um aplicativo ou controle. Barras de rolagem são um elemento comum da interface do Windows, portanto, o <xref:System.Windows.Forms.ScrollBar> controle é frequentemente usado com controles que não derivam de <xref:System.Windows.Forms.ScrollableControl> classe. Da mesma forma, muitos desenvolvedores optam por incorporar o <xref:System.Windows.Forms.ScrollBar> controlar ao criar seus próprios controles de usuário.  
  
 O <xref:System.Windows.Forms.HScrollBar> (horizontal) e <xref:System.Windows.Forms.VScrollBar> controles (verticais) operam independentemente de outros controles e ter seu próprio conjunto de eventos, propriedades e métodos. <xref:System.Windows.Forms.ScrollBar> controles não são o mesmo que as barras de rolagem internas anexadas para caixas de texto, caixas de listagem, caixas de combinação ou formulários MDI (o <xref:System.Windows.Forms.TextBox> controle tem um <xref:System.Windows.Forms.TextBox.ScrollBars%2A> propriedade para mostrar ou ocultar as barras de rolagem que estão anexadas ao controle).  
  
 O <xref:System.Windows.Forms.ScrollBar> controles usam o <xref:System.Windows.Forms.ScrollBar.Scroll> evento para monitorar a movimentação da caixa de rolagem (também conhecida como controle de posição) ao longo da barra de rolagem. Usando o <xref:System.Windows.Forms.ScrollBar.Scroll> evento fornece acesso para o valor da barra de rolagem como ele está sendo arrastado.  
  
## <a name="value-property"></a>Propriedade Value  
 O <xref:System.Windows.Forms.ScrollBar.Value%2A> propriedade (que, por padrão, é 0) é um `integer` valor correspondente para a posição da caixa de rolagem na barra de rolagem. Quando a posição da caixa de rolagem é o valor mínimo, ela se move para a posição mais à esquerda (para barras de rolagem horizontais) ou a posição superior (para barras de rolagem verticais). Quando a caixa de rolagem está no valor máximo, ela se move para a posição mais à direita ou para a posição inferior. Da mesma forma, um valor entre a parte inferior e superior do intervalo coloca a borda esquerda da caixa de rolagem no meio da barra de rolagem.  
  
 Além de usar cliques do mouse para alterar o valor da barra de rolagem, um usuário também pode arrastar a caixa de rolagem para qualquer ponto ao longo da barra. O valor resultante depende da posição da caixa de rolagem, mas é sempre dentro do intervalo da <xref:System.Windows.Forms.ScrollBar.Minimum%2A> para <xref:System.Windows.Forms.ScrollBar.Maximum%2A> propriedades definidas pelo usuário.  
  
## <a name="largechange-and-smallchange-properties"></a>Propriedades de SmallChange e LargeChange  
 Quando o usuário pressiona a tecla PAGE UP ou PAGE DOWN ou clica em que o faixa da barra de rolagem em ambos os lados da caixa de rolagem, o <xref:System.Windows.Forms.ScrollBar.Value%2A> as alterações de propriedade de acordo com o valor definido no <xref:System.Windows.Forms.ScrollBar.LargeChange%2A> propriedade.  
  
 Quando o usuário pressiona um da seta de teclas ou clica em um dos botões da barra de rolagem, o <xref:System.Windows.Forms.ScrollBar.Value%2A> as alterações de propriedade de acordo com o valor definido no <xref:System.Windows.Forms.ScrollBar.SmallChange%2A> propriedade.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.HScrollBar>  
 <xref:System.Windows.Forms.VScrollBar>  
 [Adições ao Windows Forms do .NET Framework 2.0](https://msdn.microsoft.com/library/c61a923d-3d6a-4c8c-820c-e94c83f3f9a8)  
 [Controles a serem usados nos Windows Forms](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
