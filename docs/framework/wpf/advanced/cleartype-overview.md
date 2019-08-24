---
title: Visão geral de ClearType
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], ClearType technology
- ClearType [WPF], technology
ms.assetid: 7e2392e0-75dc-463d-a716-908772782431
ms.openlocfilehash: dbef816a995d9f4909a887f017da29bab6fc3702
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015650"
---
# <a name="cleartype-overview"></a>Visão geral de ClearType
Este tópico fornece uma visão geral da tecnologia Microsoft ClearType encontrada no [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  

<a name="overview"></a>   
## <a name="technology-overview"></a>Visão geral da tecnologia  
 O ClearType é uma tecnologia de software desenvolvida pela Microsoft que melhora a legibilidade do texto em LCDs existentes (monitores Liquid Crystal), como telas de laptops, telas de Pocket PC e monitores de tela plana.  O ClearType funciona acessando os elementos da faixa de cor vertical individual em cada pixel de uma tela de LCD. Antes do ClearType, o menor nível de detalhe que um computador poderia exibir era um único pixel, mas com o ClearType em execução em um monitor de LCD, agora podemos exibir recursos de texto tão pequenos quanto uma fração de um pixel de largura. A resolução extra aumenta a nitidez dos detalhes mínimos na exibição de texto, tornando a leitura por longos períodos muito mais fácil.  
  
 O ClearType disponível no [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] é a última geração de ClearType, que tem várias melhorias em relação à versão encontrada no Microsoft Windows Graphics Device Interface (GDI).  
  
<a name="sub-pixel_positioning"></a>   
## <a name="sub-pixel-positioning"></a>Posicionamento de subpixel  
 Uma melhoria significativa em relação à versão anterior do ClearType é o uso de posicionamento de subpixel. Ao contrário da implementação de ClearType encontrada em GDI, o ClearType [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] encontrado no permite que os glifos comecem dentro do pixel e não apenas o limite inicial do pixel. Por causa dessa resolução extra ao posicionar os glifos, o espaçamento e as proporções dos glifos são mais precisos e consistentes.  
  
 Os dois exemplos a seguir mostram como os glifos podem começar em qualquer fronteira subpixel quando o posicionamento de subpixel é usado. O exemplo à esquerda é renderizado usando a versão anterior do renderizador ClearType, que não emprega o posicionamento de sub-pixel. O exemplo à direita é renderizado usando a nova versão do renderizador ClearType, usando o posicionamento de sub-pixel. Observe como cada **e** e **l** na imagem da direita é renderizado de modo ligeiramente diferente porque cada um começa em um subpixel diferente. Ao exibir o texto na tela em seu tamanho normal, essa diferença não é percebida por causa do alto contraste da imagem do glifo. Isso só é possível devido à sofisticada filtragem de cores incorporada no ClearType.  
  
 ![Texto exibido com duas versões do ClearType](./media/wcpsdk-mmgraphics-text-cleartype-overview-01.png "wcpsdk_mmgraphics_text_cleartype_overview_01")  
Texto exibido com versões anteriores e posteriores do ClearType  
  
 Os dois exemplos a seguir comparam a saída do renderizador ClearType anterior com a nova versão do renderizador ClearType. O posicionamento subpixel, exibido à direita, aumenta muito o espaçamento dos tipos na tela, especialmente em tamanhos pequenos, nos quais a diferença entre um subpixel e um pixel inteiro representa uma parte significativa da largura do glifo. Observe que o espaçamento entre as letras é mais uniforme na segunda imagem. O benefício cumulativo do posicionamento de subpixel para a aparência geral de uma tela de texto é muito maior e representa uma evolução significativa na tecnologia ClearType.  
  
 ![Texto exibido com a versão anterior do ClearType](./media/wcpsdk-mmgraphics-text-cleartype-overview-02.png "wcpsdk_mmgraphics_text_cleartype_overview_02")  
Texto com versões anteriores e posteriores do ClearType  
  
<a name="y-direction_antialiasing"></a>   
## <a name="y-direction-antialiasing"></a>Suavização da direção Y  
 Outra melhoria do ClearType no [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] é a suavização de serrilhado de direção y. O ClearType no GDI sem suavização de direção y fornece uma resolução melhor no eixo x, mas não no eixo y. Nas partes superior e inferior das curvas rasas, as bordas irregulares prejudicam a sua legibilidade.  
  
 O exemplo a seguir mostra o efeito de não ter nenhuma suavização da direção y. Nesse caso, as bordas irregulares na parte superior e inferior da letra são aparentes.  
  
 ![Texto com bordas denteadas em curvas superficiais](./media/wcpsdk-mmgraphics-text-cleartype-overview-03.png "wcpsdk_mmgraphics_text_cleartype_overview_03")  
Texto com bordas irregulares em curvas superficiais  
  
 O ClearType [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] no fornece anti-aliasing no nível de direção y para suavizar as bordas denteadas. Isso é particularmente importante para melhorar a legibilidade de idiomas do Leste Asiático, nos quais os ideogramas têm uma quantidade praticamente igual de curvas superficiais horizontais e verticais.  
  
 O exemplo a seguir mostra o efeito da suavização da direção y. Nesse caso, as partes superior e inferior da letra mostram uma curva suave.  
  
 ![Texto com anti&#45;-&#45;alias de direção y ClearType](./media/wcpsdk-mmgraphics-text-cleartype-overview-04.png "wcpsdk_mmgraphics_text_cleartype_overview_04")  
Texto com suavização da direção y do ClearType  
  
<a name="hardware_acceleration"></a>   
## <a name="hardware-acceleration"></a>Aceleração de hardware  
 O ClearType [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] no pode aproveitar a aceleração de hardware para melhorar o desempenho e reduzir os requisitos de carga de CPU e de memória do sistema. Usando os sombreadores de pixel e a memória de vídeo de uma placa gráfica, o ClearType fornece renderização mais rápida de texto, especialmente quando a animação é usada.  
  
 ClearType no [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] não modifica as configurações de ClearType em todo o sistema. Desabilitar o ClearType no Windows define [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] a anti-aliasing para o modo tons de cinza. Além disso, o ClearType [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] no não modifica as configurações do [PowerToy do sintonizador ClearType](https://www.microsoft.com/typography/ClearTypePowerToy.mspx).  
  
 Uma das decisões de design arquitetônico do [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] é fazer com que o layout de resolução independente dê um suporte melhor para os monitores DPI de resolução mais alta, que estão se tornando mais difundidos. Como consequência, o [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] não dá suporte de renderização de texto com alias ou para bitmaps em algumas fontes da Ásia Oriental porque ambos são dependentes de resolução.  
  
<a name="further_information"></a>   
## <a name="further-information"></a>Mais informações  
 [Informações sobre o ClearType](https://www.microsoft.com/typography/ClearTypeInfo.mspx)  
  
 [ClearType Tuner PowerToy](https://www.microsoft.com/typography/ClearTypePowerToy.mspx)  
  
## <a name="see-also"></a>Consulte também

- [Configurações do Registro ClearType](cleartype-registry-settings.md)
