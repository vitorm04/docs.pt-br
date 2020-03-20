---
title: Visão geral de ClearType
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], ClearType technology
- ClearType [WPF], technology
ms.assetid: 7e2392e0-75dc-463d-a716-908772782431
ms.openlocfilehash: b76c0cb04e5de498374cbf28c8813fe5c95d41ae
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186158"
---
# <a name="cleartype-overview"></a>Visão geral de ClearType
Este tópico fornece uma visão geral da tecnologia [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]Microsoft ClearType encontrada no .  

<a name="overview"></a>
## <a name="technology-overview"></a>Visão geral da tecnologia  
 ClearType é uma tecnologia de software desenvolvida pela Microsoft que melhora a legibilidade do texto em LCDs existentes (Liquid Crystal Displays), como telas de laptop, telas de Pocket PC e monitores de tela plana.  O ClearType funciona acessando os elementos de listras de cores verticais individuais em cada pixel de uma tela LCD. Antes do ClearType, o menor nível de detalhe que um computador poderia exibir era um único pixel, mas com o ClearType rodando em um monitor LCD, agora podemos exibir recursos de texto tão pequenos quanto uma fração de pixel de largura. A resolução extra aumenta a nitidez dos detalhes mínimos na exibição de texto, tornando a leitura por longos períodos muito mais fácil.  
  
 O ClearType [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] disponível é a última geração do ClearType, que tem várias melhorias em relação à versão encontrada no Microsoft Windows Graphics Device Interface (GDI).  
  
<a name="sub-pixel_positioning"></a>
## <a name="sub-pixel-positioning"></a>Posicionamento de subpixel  
 Uma melhoria significativa em relação à versão anterior do ClearType é o uso do posicionamento de subpixel. Ao contrário da implementação clearType encontrada no [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] GDI, o ClearType encontrado permite que os glifos comecem dentro do pixel e não apenas o limite inicial do pixel. Por causa dessa resolução extra ao posicionar os glifos, o espaçamento e as proporções dos glifos são mais precisos e consistentes.  
  
 Os dois exemplos a seguir mostram como os glifos podem começar em qualquer fronteira subpixel quando o posicionamento de subpixel é usado. O exemplo à esquerda é renderizado usando a versão anterior do renderizador ClearType, que não empregava posicionamento de subpixel. O exemplo à direita é renderizado usando a nova versão do renderizador ClearType, usando posicionamento de subpixel. Observe como cada **e** e **l** na imagem da direita é renderizado de modo ligeiramente diferente porque cada um começa em um subpixel diferente. Ao exibir o texto na tela em seu tamanho normal, essa diferença não é percebida por causa do alto contraste da imagem do glifo. Isso só é possível devido à filtragem de cores sofisticada que é incorporada no ClearType.  
  
 ![Texto exibido com duas versões do ClearType](./media/wcpsdk-mmgraphics-text-cleartype-overview-01.png "wcpsdk_mmgraphics_text_cleartype_overview_01")  
Texto exibido com versões anteriores e posteriores do ClearType  
  
 Os dois exemplos a seguir comparam a saída do renderizador ClearType anterior com a nova versão do renderizador ClearType. O posicionamento subpixel, exibido à direita, aumenta muito o espaçamento dos tipos na tela, especialmente em tamanhos pequenos, nos quais a diferença entre um subpixel e um pixel inteiro representa uma parte significativa da largura do glifo. Observe que o espaçamento entre as letras é mais uniforme na segunda imagem. O benefício cumulativo do posicionamento de subpixels para a aparência geral de uma tela de texto é muito aumentado, e representa uma evolução significativa na tecnologia ClearType.  
  
 ![Texto exibido com a versão anterior do ClearType](./media/wcpsdk-mmgraphics-text-cleartype-overview-02.png "wcpsdk_mmgraphics_text_cleartype_overview_02")  
Texto com versões anteriores e posteriores do ClearType  
  
<a name="y-direction_antialiasing"></a>
## <a name="y-direction-antialiasing"></a>Suavização da direção Y  
 Outra melhoria do [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] ClearType em é o anti-aliasing y-direction. O ClearType em GDI sem o anti-aliasing de direção y fornece melhor resolução no eixo x, mas não no eixo y. Nas partes superior e inferior das curvas rasas, as bordas irregulares prejudicam a sua legibilidade.  
  
 O exemplo a seguir mostra o efeito de não ter nenhuma suavização da direção y. Nesse caso, as bordas irregulares na parte superior e inferior da letra são aparentes.  
  
 ![Texto com bordas irregulares em curvas superficiais](./media/wcpsdk-mmgraphics-text-cleartype-overview-03.png "wcpsdk_mmgraphics_text_cleartype_overview_03")  
Texto com bordas irregulares em curvas superficiais  
  
 O ClearType in [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fornece antialiasing no nível de direção y para suavizar quaisquer bordas irregulares. Isso é particularmente importante para melhorar a legibilidade de idiomas do Leste da Ásia, nos quais os ideogramas têm uma quantidade praticamente igual de curvas superficiais horizontais e verticais.  
  
 O exemplo a seguir mostra o efeito da suavização da direção y. Nesse caso, as partes superior e inferior da letra mostram uma curva suave.  
  
 ![Texto com suavização da direção y do ClearType](./media/wcpsdk-mmgraphics-text-cleartype-overview-04.png "wcpsdk_mmgraphics_text_cleartype_overview_04")  
Texto com suavização da direção y do ClearType  
  
<a name="hardware_acceleration"></a>
## <a name="hardware-acceleration"></a>Aceleração de hardware  
 ClearType [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] in pode aproveitar a aceleração de hardware para um melhor desempenho e reduzir os requisitos de carga da CPU e memória do sistema. Usando os sombreadores de pixels e a memória de vídeo de uma placa gráfica, o ClearType fornece renderização mais rápida de texto, especialmente quando a animação é usada.  
  
 ClearType [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] in não modifica as configurações do ClearType em todo o sistema. Desativar o ClearType [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] no Windows define o antialiasing para o modo em escala de cinza. Além disso, clearType [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] in não modifica as configurações do [ClearType Tuner PowerToy](https://www.microsoft.com/typography/ClearTypePowerToy.mspx).  
  
 Uma das decisões de design arquitetônico do [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] é fazer com que o layout de resolução independente dê um suporte melhor para os monitores DPI de resolução mais alta, que estão se tornando mais difundidos. Como consequência, o [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] não dá suporte de renderização de texto com alias ou para bitmaps em algumas fontes do Leste da Ásia porque ambos são dependentes de resolução.  
  
<a name="further_information"></a>
## <a name="further-information"></a>Mais informações  
 [Informações sobre o ClearType](https://www.microsoft.com/typography/ClearTypeInfo.mspx)  
  
 [ClearType Tuner PowerToy](https://www.microsoft.com/typography/ClearTypePowerToy.mspx)  
  
## <a name="see-also"></a>Confira também

- [Configurações do Registro ClearType](cleartype-registry-settings.md)
