---
title: Visão geral do controle TrackBar
ms.date: 03/30/2017
f1_keywords:
- TrackBar
helpviewer_keywords:
- sliders [Windows Forms], about sliders
- TrackBar control [Windows Forms], about TrackBar control
- slider controls [Windows Forms], about slider controls
ms.assetid: 95910ecb-8a4c-4776-89fa-206c89ed6973
ms.openlocfilehash: 6901405100df4633c84850757f55b756bc9a0199
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741460"
---
# <a name="trackbar-control-overview-windows-forms"></a>Visão geral do controle TrackBar (Windows Forms)
O controle de <xref:System.Windows.Forms.TrackBar> de Windows Forms (também chamado de controle "slider") é usado para navegar por uma grande quantidade de informações ou para ajustar visualmente uma configuração numérica. O controle de <xref:System.Windows.Forms.TrackBar> tem duas partes: o Thumb, também conhecido como um controle deslizante e as marcas de escala. O elevador é parte que pode ser ajustada. Sua posição corresponde à propriedade <xref:System.Windows.Forms.TrackBar.Value%2A>. As marcas de escala são indicadores visuais espaçados em intervalos regulares. A trackbar se move em incrementos especificados e pode ser alinhada horizontalmente ou verticalmente. Por exemplo, é possível usar a trackbar para controlar a taxa de intermitência do cursor ou a velocidade do mouse em um sistema.  
  
## <a name="key-properties"></a>Propriedades da chave  
 As propriedades de chave do controle de <xref:System.Windows.Forms.TrackBar> são <xref:System.Windows.Forms.TrackBar.Value%2A>, <xref:System.Windows.Forms.TrackBar.TickFrequency%2A>, <xref:System.Windows.Forms.TrackBar.Minimum%2A>e <xref:System.Windows.Forms.TrackBar.Maximum%2A>. <xref:System.Windows.Forms.TrackBar.TickFrequency%2A> é o espaçamento das tiques. <xref:System.Windows.Forms.TrackBar.Minimum%2A> e <xref:System.Windows.Forms.TrackBar.Maximum%2A> são os menores e maiores valores que podem ser representados na barra de controle.  
  
 Duas outras propriedades importantes são <xref:System.Windows.Forms.TrackBar.SmallChange%2A> e <xref:System.Windows.Forms.TrackBar.LargeChange%2A>. O valor da propriedade <xref:System.Windows.Forms.TrackBar.SmallChange%2A> é o número de posições que o Thumb move em resposta a ter a tecla de seta para a esquerda ou para a direita pressionada. O valor da propriedade <xref:System.Windows.Forms.TrackBar.LargeChange%2A> é o número de posições que o Thumb move em resposta a ter a tecla PAGE UP ou PAGE DOWN pressionada ou em resposta a cliques do mouse na barra de controle em qualquer lado do polegar.  
  
## <a name="see-also"></a>Veja também

- <xref:System.Windows.Forms.TrackBar>
- [Controle TrackBar](trackbar-control-windows-forms.md)
