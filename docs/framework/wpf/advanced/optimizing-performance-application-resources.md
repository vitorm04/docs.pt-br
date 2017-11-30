---
title: 'Otimizando desempenho: recursos do aplicativo'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application resources [WPF], performance
- resources [WPF], performance
- static resources [WPF]
- sharing resources [WPF]
- brushes [WPF], performance
- sharing brushes without copying [WPF]
ms.assetid: 62b88488-c08e-4804-b7de-a1c34fbe929c
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8ac462f3b49788fd909f9d9f4fc785db74704ff6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="optimizing-performance-application-resources"></a>Otimizando desempenho: recursos do aplicativo
O [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] permite compartilhar recursos do aplicativo para dar suporte a um comportamento ou a uma aparência consistente entre elementos de tipos semelhantes. Este tópico dá algumas recomendações nessa área que podem ajudar a melhorar o desempenho dos seus aplicativos.  
  
 Para obter mais informações sobre recursos, consulte [Recursos de XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md).  
  
## <a name="sharing-resources"></a>Compartilhando recursos  
 Se seu aplicativo usa controles personalizados e define os recursos em um <xref:System.Windows.ResourceDictionary> (ou nó de recursos XAML), é recomendável que você defina os recursos no <xref:System.Windows.Application> ou <xref:System.Windows.Window> nível de objeto ou defini-los no tema padrão para o controles personalizados. Definir recursos em um controle personalizado <xref:System.Windows.ResourceDictionary> impõe um impacto de desempenho para cada instância do controle. Por exemplo, se você tiver operações de pincel com uso intenso de desempenho definidas como parte da definição de recurso de um controle personalizado e muitas instâncias do controle personalizado, o conjunto de trabalho do aplicativo aumentará significativamente.  
  
 Para ilustrar esse ponto, considere o seguinte. Digamos que você esteja desenvolvendo um jogo de cartas usando [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Para a maioria dos jogos de cartas, você precisa de 52 cartas com 52 naipes diferentes. Você decide implementar um controle personalizado de carta e definir 52 pincéis (cada um representando um naipe de carta) nos recursos do seu controle personalizado de carta. No aplicativo principal, você inicialmente cria 52 instâncias desse controle personalizado de carta. Cada instância do controle personalizado cartão gera 52 instâncias de <xref:System.Windows.Media.Brush> objetos, o que resulta em um total de 52 * 52 <xref:System.Windows.Media.Brush> objetos em seu aplicativo. Movendo os pincéis sem os recursos de controle personalizado do cartão para o <xref:System.Windows.Application> ou <xref:System.Windows.Window> nível de objeto, ou definindo-os no tema padrão para o controle personalizado, você reduz o conjunto de trabalho do aplicativo, já que agora você está compartilhando os 52 pincéis entre as 52 instâncias do controle cartão.  
  
## <a name="sharing-a-brush-without-copying"></a>Compartilhando um pincel sem copiar  
 Se você tiver vários elementos usando o mesmo <xref:System.Windows.Media.Brush> do objeto, defina o brush como um recurso e fazer referência a ele, em vez de definir o brush inline no [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)]. Esse método cria uma instância e a reutiliza, enquanto definir pincéis embutidos no [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] cria uma nova instância para cada elemento.  
  
 O exemplo de marcação a seguir ilustra este ponto:  
  
 [!code-xaml[Performance#PerformanceSnippet7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/BrushResource.xaml#performancesnippet7)]  
  
## <a name="use-static-resources-when-possible"></a>Usar recursos estáticos quando possível  
 Um recurso estático fornece um valor para qualquer atributo de propriedade XAML pesquisando uma referência a um recurso já definido. O comportamento de pesquisa para esse recurso é análogo à pesquisa em tempo de compilação.  
  
 Um recurso dinâmico, por outro lado, criará uma expressão temporária durante a compilação inicial e, portanto, adiará a pesquisa por recursos até que o valor de recurso solicitado seja realmente necessário para construir um objeto. O comportamento de pesquisa para esse recurso é análogo à pesquisa de tempo de execução, que causa um impacto ao desempenho. Use recursos estáticos sempre que possível em seu aplicativo, usando recursos dinâmicos somente quando necessário.  
  
 O exemplo de marcação a seguir mostra o uso de ambos os tipos de recursos:  
  
 [!code-xaml[Performance#PerformanceSnippet8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/DynamicResource.xaml#performancesnippet8)]  
  
## <a name="see-also"></a>Consulte também  
 [Otimizando o desempenho do aplicativo WPF](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)  
 [Planejando para desempenho do aplicativo](../../../../docs/framework/wpf/advanced/planning-for-application-performance.md)  
 [Aproveitando o hardware](../../../../docs/framework/wpf/advanced/optimizing-performance-taking-advantage-of-hardware.md)  
 [Layout e design](../../../../docs/framework/wpf/advanced/optimizing-performance-layout-and-design.md)  
 [Elementos gráficos e geração de imagens 2D](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)  
 [Comportamento do objeto](../../../../docs/framework/wpf/advanced/optimizing-performance-object-behavior.md)  
 [Texto](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)  
 [Associação de dados](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)  
 [Outras recomendações de desempenho](../../../../docs/framework/wpf/advanced/optimizing-performance-other-recommendations.md)
