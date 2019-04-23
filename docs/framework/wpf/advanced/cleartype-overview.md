---
title: Visão geral de ClearType
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], ClearType technology
- ClearType [WPF], technology
ms.assetid: 7e2392e0-75dc-463d-a716-908772782431
ms.openlocfilehash: 0127ee4112c4b42a7a55b9233217ea1e02604042
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59085188"
---
# <a name="cleartype-overview"></a>Visão geral de ClearType
Este tópico fornece uma visão geral da tecnologia [!INCLUDE[TLA#tla_ct](../../../../includes/tlasharptla-ct-md.md)] encontrada no [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  

<a name="overview"></a>   
## <a name="technology-overview"></a>Visão geral da tecnologia  
 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] é uma tecnologia de software desenvolvida por [!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)], que melhora a legibilidade do texto em monitores LCD existentes, como telas de laptop, telas de Pocket PC e monitores de tela plana.  [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] funciona ao acessar os elementos individuais da listra de cores vertical em cada pixel de uma tela LCD. Antes de [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)], o menor nível de detalhe que um computador poderia exibir era um único pixel, mas com [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] em execução em um monitor LCD, podemos agora exibir recursos de texto tão pequenos quanto uma fração de um pixel de largura. A resolução extra aumenta a nitidez dos detalhes mínimos na exibição de texto, tornando a leitura por longos períodos muito mais fácil.  
  
 O [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] disponível em [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] é a última geração de [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)], que tem diversas melhorias em relação à versão encontrada em [!INCLUDE[TLA#tla_gdi](../../../../includes/tlasharptla-gdi-md.md)].  
  
<a name="sub-pixel_positioning"></a>   
## <a name="sub-pixel-positioning"></a>Posicionamento de subpixel  
 Uma melhoria significativa sobre a versão anterior do [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] é o uso do posicionamento de subpixel. Ao contrário da implementação [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] encontrada no [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)], o [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] encontrado no [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] permite que os glifos comecem dentro do pixel e não apenas na fronteira inicial do pixel. Por causa dessa resolução extra ao posicionar os glifos, o espaçamento e as proporções dos glifos são mais precisos e consistentes.  
  
 Os dois exemplos a seguir mostram como os glifos podem começar em qualquer fronteira subpixel quando o posicionamento de subpixel é usado. O exemplo à esquerda é renderizado utilizando a versão anterior do renderizador [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)], que não utilizava o posicionamento de subpixel. O exemplo à direita é renderizado utilizando a nova versão do renderizador [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)], que usa o posicionamento de subpixel. Observe como cada **e** e **l** na imagem da direita é renderizado de modo ligeiramente diferente porque cada um começa em um subpixel diferente. Ao exibir o texto na tela em seu tamanho normal, essa diferença não é percebida por causa do alto contraste da imagem do glifo. Isso só é possível por causa de filtros de cor sofisticados que são incorporados na [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)].  
  
 ![Texto exibido com duas versões do ClearType](./media/wcpsdk-mmgraphics-text-cleartype-overview-01.png "wcpsdk_mmgraphics_text_cleartype_overview_01")  
Texto exibido com versões anteriores e posteriores do ClearType  
  
 Os dois exemplos a seguir comparam a saída do renderizador [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] anterior com a nova versão do renderizador [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)]. O posicionamento subpixel, exibido à direita, aumenta muito o espaçamento dos tipos na tela, especialmente em tamanhos pequenos, nos quais a diferença entre um subpixel e um pixel inteiro representa uma parte significativa da largura do glifo. Observe que o espaçamento entre as letras é mais uniforme na segunda imagem. O benefício cumulativo do posicionamento de subpixel na aparência geral de uma tela de texto é muito maior e representa uma evolução significativa na tecnologia [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)].  
  
 ![Texto exibido com a versão anterior do ClearType](./media/wcpsdk-mmgraphics-text-cleartype-overview-02.png "wcpsdk_mmgraphics_text_cleartype_overview_02")  
Texto com versões anteriores e posteriores do ClearType  
  
<a name="y-direction_antialiasing"></a>   
## <a name="y-direction-antialiasing"></a>Suavização da direção Y  
 Outra melhoria de [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] em [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] é a suavização da direção y. O [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] em [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] sem a suavização da direção y fornece uma resolução melhor no eixo x, mas não no eixo y. Nas partes superior e inferior das curvas rasas, as bordas irregulares prejudicam a sua legibilidade.  
  
 O exemplo a seguir mostra o efeito de não ter nenhuma suavização da direção y. Nesse caso, as bordas irregulares na parte superior e inferior da letra são aparentes.  
  
 ![Texto com bordas irregulares em curvas superficiais](./media/wcpsdk-mmgraphics-text-cleartype-overview-03.png "wcpsdk_mmgraphics_text_cleartype_overview_03")  
Texto com bordas irregulares em curvas superficiais  
  
 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] em [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fornece suavização no nível da direção y para atenuar qualquer borda irregular. Isso é particularmente importante para melhorar a legibilidade de idiomas do Leste Asiático, nos quais os ideogramas têm uma quantidade praticamente igual de curvas superficiais horizontais e verticais.  
  
 O exemplo a seguir mostra o efeito da suavização da direção y. Nesse caso, as partes superior e inferior da letra mostram uma curva suave.  
  
 ![Texto com y do ClearType&#45;direção&#45;alias](./media/wcpsdk-mmgraphics-text-cleartype-overview-04.png "wcpsdk_mmgraphics_text_cleartype_overview_04")  
Texto com suavização da direção y do ClearType  
  
<a name="hardware_acceleration"></a>   
## <a name="hardware-acceleration"></a>Aceleração de hardware  
 O [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] no [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] pode aproveitar a aceleração de hardware para melhorar o desempenho e reduzir os requisitos de carga de CPU e memória do sistema. Usando os sombreadores de pixel e a memória de vídeo de um cartão gráfico, o [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] fornece renderização mais rápida de texto, em particular quando a animação é usada.  
  
 O [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] no [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] não modifica as configurações do [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] em todo o sistema. Desabilitar o [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] no [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] define a suavização do [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] para o modo escala de cinza. Além disso, o [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] no [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] não modifica as configurações do [ClearType Tuner PowerToy](https://www.microsoft.com/typography/ClearTypePowerToy.mspx).  
  
 Uma das decisões de design arquitetônico do [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] é fazer com que o layout de resolução independente dê um suporte melhor para os monitores DPI de resolução mais alta, que estão se tornando mais difundidos. Como consequência, o [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] não dá suporte de renderização de texto com alias ou para bitmaps em algumas fontes da Ásia Oriental porque ambos são dependentes de resolução.  
  
<a name="further_information"></a>   
## <a name="further-information"></a>Mais informações  
 [Informações sobre o ClearType](https://www.microsoft.com/typography/ClearTypeInfo.mspx)  
  
 [ClearType Tuner PowerToy](https://www.microsoft.com/typography/ClearTypePowerToy.mspx)  
  
## <a name="see-also"></a>Consulte também

- [Configurações do Registro ClearType](cleartype-registry-settings.md)
