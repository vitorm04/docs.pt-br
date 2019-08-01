---
title: 'Otimizando o desempenho: Aproveitar o hardware'
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], performance
- hardware rendering pipeline [WPF]
- rendering tiers [WPF]
- graphics rendering tiers [WPF]
- graphics [WPF], rendering tiers
- software rendering pipeline [WPF]
ms.assetid: bfb89bae-7aab-4cac-a26c-a956eda8fce2
ms.openlocfilehash: a47a4aae785d817904c30fe7c865a1c033eb3cca
ms.sourcegitcommit: eb9ff6f364cde6f11322e03800d8f5ce302f3c73
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/01/2019
ms.locfileid: "68709217"
---
# <a name="optimizing-performance-taking-advantage-of-hardware"></a>Otimizando o desempenho: Aproveitar o hardware
A arquitetura interna do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tem dois pipelines de renderização, hardware e software. Este tópico apresenta informações sobre esses pipelines de renderização para ajudá-lo a tomar decisões sobre otimizações de desempenho de seus aplicativos.  
  
## <a name="hardware-rendering-pipeline"></a>Pipeline de renderização de hardware  
 Um dos fatores mais importantes para determinar o desempenho de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] é o limite de renderização: quanto mais pixels há para renderizar, maior o custo de desempenho. No entanto, quanto mais renderização puder ser descarregada na GPU (unidade de processamento gráfico), mais benefícios de desempenho você poderá obter. O [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pipeline de processamento de hardware do aplicativo aproveita totalmente os recursos do Microsoft DirectX em hardware que oferece suporte a um mínimo de Microsoft DirectX versão 7,0. Otimizações adicionais podem ser obtidas por hardware que dá suporte ao Microsoft DirectX versão 7,0 e aos recursos do PixelShader 2.0 +.  
  
## <a name="software-rendering-pipeline"></a>Pipeline de renderização de software  
 O pipeline [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] de processamento de software é totalmente vinculado à CPU. O [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aproveita os conjuntos de instruções SSE e SSE2 na CPU para implementar um rasterizador otimizado de software com todos os recursos. Fazer fallback para o software é uma funcionalidade de aplicativo contínua disponível a qualquer momento e não pode ser renderizada usando o pipeline de renderização de hardware.  
  
 O maior problema de desempenho que você encontrará ao renderizar no modo de software está relacionado à taxa de preenchimento, que é definida como o número de pixels que você está renderizando. Se você estiver preocupado com o desempenho no modo de renderização de software, tente minimizar o número de vezes que um pixel é redesenhado. Por exemplo, se você tiver um aplicativo com uma tela de fundo azul, que então renderiza uma imagem levemente transparente sobre ela, você renderizará todos os pixels no aplicativo duas vezes. Como resultado, levará duas vezes mais tempo para renderizar o aplicativo com a imagem que se você tivesse apenas a tela de fundo azul.  
  
### <a name="graphics-rendering-tiers"></a>Camadas de renderização de gráficos  
 Pode ser muito difícil prever a configuração de hardware em que seu aplicativo será executado. No entanto, convém considerar um design que permita ao seu aplicativo mudar continuamente entre os recursos ao executar em hardware diferente para que possa se beneficiar totalmente de cada configuração de hardware diferente.  
  
 Para fazer isso, o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fornece funcionalidade para determinar a capacidade gráfica de um sistema em tempo de execução. A capacidade gráfica é determinada categorizando a placa de vídeo como uma das três camadas de capacidade de renderização. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]expõe uma API que permite que um aplicativo consulte a camada de capacidade de renderização. Seu aplicativo então pode adotar diferentes caminhos de código no tempo de execução, dependendo da camada de renderização que tem suporte no hardware.  
  
 Os recursos do hardware gráfico que mais afetam os níveis de camada de renderização são:  
  
- **RAM de Vídeo** A quantidade de memória de vídeo no hardware gráfico determina o tamanho e o número de buffers que podem ser usados para compor gráficos.  
  
- **Sombreador de Pixel** Um sombreador de pixel é uma função de processamento gráfico que calcula efeitos por pixel. Dependendo da resolução dos gráficos exibidos, pode haver muitos milhões de pixels que precisam ser processados para cada quadro de vídeo.  
  
- **Sombreador de Vértice** O sombreador de vértice é uma função de processamento gráfico que realiza operações matemáticas nos dados de vértice do objeto.  
  
- **Suporte Multitextura** Suporte multitextura refere-se à capacidade de aplicar duas ou mais texturas distintas durante uma operação de mesclagem em um objeto gráfico 3D. O grau de suporte a multitextura é determinado pelo número de unidades de multitextura no hardware gráfico.  
  
 O sombreador de pixel, o sombreador de vértice e os recursos de multitextura são usados para definir níveis de versão específicos do DirectX, que, por sua vez, são [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]usados para definir as diferentes camadas de renderização no.  
  
 Os recursos do hardware gráfico determinam a capacidade de renderização de um aplicativo [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. O sistema [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] define três camadas de renderização:  
  
- **Camada de Renderização 0** Sem aceleração de hardware gráfico. O nível de versão do DirectX é menor que a versão 7,0.  
  
- **Camada de Renderização 1** Aceleração parcial de hardware gráfico. O nível de versão do DirectX é maior ou igual à versão 7,0 e **menor** que a versão 9,0.  
  
- **Camada de Renderização 2** A maioria dos recursos gráficos usa aceleração de hardware gráfico. O nível de versão do DirectX é maior ou igual à versão 9,0.  
  
 Para obter mais informações sobre camadas de renderização [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], consulte [Níveis de renderização gráfica](graphics-rendering-tiers.md).  
  
## <a name="see-also"></a>Consulte também

- [Otimizando o desempenho do aplicativo WPF](optimizing-wpf-application-performance.md)
- [Planejando para desempenho do aplicativo](planning-for-application-performance.md)
- [Layout e design](optimizing-performance-layout-and-design.md)
- [Elementos gráficos e geração de imagens 2D](optimizing-performance-2d-graphics-and-imaging.md)
- [Comportamento do objeto](optimizing-performance-object-behavior.md)
- [Recursos do aplicativo](optimizing-performance-application-resources.md)
- [Texto](optimizing-performance-text.md)
- [Associação de dados](optimizing-performance-data-binding.md)
- [Outras recomendações de desempenho](optimizing-performance-other-recommendations.md)
