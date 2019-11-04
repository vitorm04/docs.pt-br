---
title: 'Otimizando desempenho: recursos do aplicativo'
ms.date: 03/30/2017
helpviewer_keywords:
- application resources [WPF], performance
- resources [WPF], performance
- static resources [WPF]
- sharing resources [WPF]
- brushes [WPF], performance
- sharing brushes without copying [WPF]
ms.assetid: 62b88488-c08e-4804-b7de-a1c34fbe929c
ms.openlocfilehash: 59b124c28ade0a6c5119b651ff935d460bf4516d
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458565"
---
# <a name="optimizing-performance-application-resources"></a>Otimizando desempenho: recursos do aplicativo
O [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] permite compartilhar recursos do aplicativo para dar suporte a um comportamento ou a uma aparência consistente entre elementos de tipos semelhantes. Este tópico dá algumas recomendações nessa área que podem ajudar a melhorar o desempenho dos seus aplicativos.  
  
 Para obter mais informações sobre recursos, consulte [Recursos de XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md).  
  
## <a name="sharing-resources"></a>Compartilhando recursos  
 Se seu aplicativo usar controles personalizados e definir recursos em um <xref:System.Windows.ResourceDictionary> (ou nó de recursos XAML), é recomendável que você defina os recursos no nível de <xref:System.Windows.Application> ou <xref:System.Windows.Window> objeto ou defina-os no tema padrão para os controles personalizados. Definir recursos no <xref:System.Windows.ResourceDictionary> de um controle personalizado impõe um impacto no desempenho de cada instância desse controle. Por exemplo, se você tiver operações de pincel com uso intenso de desempenho definidas como parte da definição de recurso de um controle personalizado e muitas instâncias do controle personalizado, o conjunto de trabalho do aplicativo aumentará significativamente.  
  
 Para ilustrar esse ponto, considere o seguinte. Digamos que você esteja desenvolvendo um jogo de cartas usando [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Para a maioria dos jogos de cartas, você precisa de 52 cartas com 52 naipes diferentes. Você decide implementar um controle personalizado de carta e definir 52 pincéis (cada um representando um naipe de carta) nos recursos do seu controle personalizado de carta. No aplicativo principal, você inicialmente cria 52 instâncias desse controle personalizado de carta. Cada instância do controle personalizado de cartão gera 52 instâncias de objetos <xref:System.Windows.Media.Brush>, o que oferece um total de 52 * 52 <xref:System.Windows.Media.Brush> objetos em seu aplicativo. Ao mover os pincéis para fora dos recursos de controle personalizado do cartão para o nível de objeto <xref:System.Windows.Application> ou <xref:System.Windows.Window> ou defini-los no tema padrão para o controle personalizado, você reduz o conjunto de trabalho do aplicativo, já que agora você está compartilhando os pincéis 52 entre 52 instâncias do controle de cartão.  
  
## <a name="sharing-a-brush-without-copying"></a>Compartilhando um pincel sem copiar  
 Se você tiver vários elementos usando o mesmo objeto <xref:System.Windows.Media.Brush>, defina o pincel como um recurso e faça referência a ele, em vez de definir o pincel embutido em XAML. Esse método criará uma instância e a reutilizará, enquanto a definição de pincéis embutidos em XAML cria uma nova instância para cada elemento.  
  
 O exemplo de marcação a seguir ilustra este ponto:  
  
 [!code-xaml[Performance#PerformanceSnippet7](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/BrushResource.xaml#performancesnippet7)]  
  
## <a name="use-static-resources-when-possible"></a>Usar recursos estáticos quando possível  
 Um recurso estático fornece um valor para qualquer atributo de propriedade XAML pesquisando uma referência a um recurso já definido. O comportamento de pesquisa para esse recurso é análogo à pesquisa em tempo de compilação.  
  
 Um recurso dinâmico, por outro lado, criará uma expressão temporária durante a compilação inicial e, portanto, adiará a pesquisa por recursos até que o valor de recurso solicitado seja realmente necessário para construir um objeto. O comportamento de pesquisa para esse recurso é análogo à pesquisa de tempo de execução, que causa um impacto ao desempenho. Use recursos estáticos sempre que possível em seu aplicativo, usando recursos dinâmicos somente quando necessário.  
  
 O exemplo de marcação a seguir mostra o uso de ambos os tipos de recursos:  
  
 [!code-xaml[Performance#PerformanceSnippet8](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/DynamicResource.xaml#performancesnippet8)]  
  
## <a name="see-also"></a>Consulte também

- [Otimizando o desempenho do aplicativo WPF](optimizing-wpf-application-performance.md)
- [Planejando para desempenho do aplicativo](planning-for-application-performance.md)
- [Aproveitando o hardware](optimizing-performance-taking-advantage-of-hardware.md)
- [Layout e design](optimizing-performance-layout-and-design.md)
- [Elementos gráficos e geração de imagens 2D](optimizing-performance-2d-graphics-and-imaging.md)
- [Comportamento do objeto](optimizing-performance-object-behavior.md)
- [Texto](optimizing-performance-text.md)
- [Associação de dados](optimizing-performance-data-binding.md)
- [Outras recomendações de desempenho](optimizing-performance-other-recommendations.md)
