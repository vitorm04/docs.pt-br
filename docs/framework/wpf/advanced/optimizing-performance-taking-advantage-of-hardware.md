---
title: 'Otimizando desempenho: usufruindo hardware'
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], performance
- hardware rendering pipeline [WPF]
- rendering tiers [WPF]
- graphics rendering tiers [WPF]
- graphics [WPF], rendering tiers
- software rendering pipeline [WPF]
ms.assetid: bfb89bae-7aab-4cac-a26c-a956eda8fce2
ms.openlocfilehash: eb790da63b4636e3dd6c25ea118075304702acc0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="optimizing-performance-taking-advantage-of-hardware"></a>Otimizando desempenho: usufruindo hardware
A arquitetura interna do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tem dois pipelines de renderização, hardware e software. Este tópico apresenta informações sobre esses pipelines de renderização para ajudá-lo a tomar decisões sobre otimizações de desempenho de seus aplicativos.  
  
## <a name="hardware-rendering-pipeline"></a>Pipeline de renderização de hardware  
 Um dos fatores mais importantes para determinar o desempenho de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] é o limite de renderização: quanto mais pixels há para renderizar, maior o custo de desempenho. No entanto, quanto mais renderização pode ser descarregada para o [!INCLUDE[TLA#tla_gpu](../../../../includes/tlasharptla-gpu-md.md)], mais benefícios de desempenho você pode obter. O pipeline de renderização de hardware de aplicativo [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aproveita todos os recursos do [!INCLUDE[TLA#tla_dx](../../../../includes/tlasharptla-dx-md.md)] em hardware com suporte para pelo menos [!INCLUDE[TLA#tla_dx](../../../../includes/tlasharptla-dx-md.md)] versão 7.0. Otimizações adicionais podem ser obtidas pelo hardware que dá suporte a [!INCLUDE[TLA#tla_dx](../../../../includes/tlasharptla-dx-md.md)] versão 7.0 e recursos PixelShader 2.0 +.  
  
## <a name="software-rendering-pipeline"></a>Pipeline de renderização de software  
 O pipeline [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] de processamento de software é totalmente vinculado à CPU. O [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aproveita os conjuntos de instruções SSE e SSE2 na CPU para implementar um rasterizador otimizado de software com todos os recursos. Fazer fallback para o software é uma funcionalidade de aplicativo contínua disponível a qualquer momento e não pode ser renderizada usando o pipeline de renderização de hardware.  
  
 O maior problema de desempenho que você encontrará ao renderizar no modo de software está relacionado à taxa de preenchimento, que é definida como o número de pixels que você está renderizando. Se você estiver preocupado com o desempenho no modo de renderização de software, tente minimizar o número de vezes que um pixel é redesenhado. Por exemplo, se você tiver um aplicativo com uma tela de fundo azul, que então renderiza uma imagem levemente transparente sobre ela, você renderizará todos os pixels no aplicativo duas vezes. Como resultado, levará duas vezes mais tempo para renderizar o aplicativo com a imagem que se você tivesse apenas a tela de fundo azul.  
  
### <a name="graphics-rendering-tiers"></a>Camadas de renderização de gráficos  
 Pode ser muito difícil prever a configuração de hardware em que seu aplicativo será executado. No entanto, convém considerar um design que permita ao seu aplicativo mudar continuamente entre os recursos ao executar em hardware diferente para que possa se beneficiar totalmente de cada configuração de hardware diferente.  
  
 Para fazer isso, o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fornece funcionalidade para determinar a capacidade gráfica de um sistema em tempo de execução. A capacidade gráfica é determinada categorizando a placa de vídeo como uma das três camadas de capacidade de renderização. O [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] expõe um [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] que permite que um aplicativo consulte a camada da capacidade de renderização. Seu aplicativo então pode adotar diferentes caminhos de código no tempo de execução, dependendo da camada de renderização que tem suporte no hardware.  
  
 Os recursos do hardware gráfico que mais afetam os níveis de camada de renderização são:  
  
-   **RAM de Vídeo** A quantidade de memória de vídeo no hardware gráfico determina o tamanho e o número de buffers que podem ser usados para compor gráficos.  
  
-   **Sombreador de Pixel** Um sombreador de pixel é uma função de processamento gráfico que calcula efeitos por pixel. Dependendo da resolução dos gráficos exibidos, pode haver muitos milhões de pixels que precisam ser processados para cada quadro de vídeo.  
  
-   **Sombreador de Vértice** O sombreador de vértice é uma função de processamento gráfico que realiza operações matemáticas nos dados de vértice do objeto.  
  
-   **Suporte Multitextura** Suporte multitextura refere-se à capacidade de aplicar duas ou mais texturas distintas durante uma operação de mesclagem em um objeto gráfico 3D. O grau de suporte a multitextura é determinado pelo número de unidades de multitextura no hardware gráfico.  
  
 O sombreador de pixel, o sombreador de vértices e recursos multitextura são usados para definir níveis específicos de versão [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)], que, por sua vez, são usados para definir as diferentes camadas de renderização em [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 Os recursos do hardware gráfico determinam a capacidade de renderização de um aplicativo [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. O sistema [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] define três camadas de renderização:  
  
-   **Camada de Renderização 0** Sem aceleração de hardware gráfico. O nível de versão [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] é inferior à versão 7.0.  
  
-   **Camada de Renderização 1** Aceleração parcial de hardware gráfico. O nível de versão [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] é maior ou igual à versão 7.0 e **menor** que a versão 9.0.  
  
-   **Camada de Renderização 2** A maioria dos recursos gráficos usa aceleração de hardware gráfico. O nível de versão [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] é maior ou igual à versão 9.0.  
  
 Para obter mais informações sobre camadas de renderização [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], consulte [Níveis de renderização gráfica](../../../../docs/framework/wpf/advanced/graphics-rendering-tiers.md).  
  
## <a name="see-also"></a>Consulte também  
 [Otimizando o desempenho do aplicativo WPF](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)  
 [Planejando para desempenho do aplicativo](../../../../docs/framework/wpf/advanced/planning-for-application-performance.md)  
 [Layout e design](../../../../docs/framework/wpf/advanced/optimizing-performance-layout-and-design.md)  
 [Elementos gráficos e geração de imagens 2D](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)  
 [Comportamento do objeto](../../../../docs/framework/wpf/advanced/optimizing-performance-object-behavior.md)  
 [Recursos do aplicativo](../../../../docs/framework/wpf/advanced/optimizing-performance-application-resources.md)  
 [Texto](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)  
 [Associação de dados](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)  
 [Outras recomendações de desempenho](../../../../docs/framework/wpf/advanced/optimizing-performance-other-recommendations.md)
