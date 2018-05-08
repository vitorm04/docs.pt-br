---
title: 'Otimizando desempenho: outras recomendações'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Terminal Services rendering [WPF]
- opacity [WPF]
- hit-test objects [WPF]
- ScrollBarVisibility enumeration [WPF]
- brushes [WPF], performance
ms.assetid: d028cc65-7e97-4a4f-9859-929734eaf40d
ms.openlocfilehash: 3ea776dcb1b8633922aafca31821d367a11260f5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="optimizing-performance-other-recommendations"></a>Otimizando desempenho: outras recomendações
<a name="introduction"></a> Este tópico apresenta recomendações de desempenho além daquelas abordadas pelos tópicos na seção [Otimizando o desempenho do aplicativo WPF](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md).  
  
 Esse tópico contém as seguintes seções:  
  
-   [Opacidade em pincéis versus opacidade em elementos](#Opacity)  
  
-   [Navegação para objeto](#Navigation_Objects)  
  
-   [Testes de clique em grandes superfícies 3D](#Hit_Testing)  
  
-   [Evento CompositionTarget.Rendering](#CompositionTarget_Rendering_Event)  
  
-   [Evite usar ScrollBarVisibility=Auto](#Avoid_Using_ScrollBarVisibility)  
  
-   [Configurar o serviço de cache de fonte para reduzir o tempo de inicialização](#FontCache)  
  
<a name="Opacity"></a>   
## <a name="opacity-on-brushes-versus-opacity-on-elements"></a>Opacidade em pincéis versus opacidade em elementos  
 Quando você usa um <xref:System.Windows.Media.Brush> para definir o <xref:System.Windows.Shapes.Shape.Fill%2A> ou <xref:System.Windows.Shapes.Shape.Stroke%2A> de um elemento, é melhor definir o <xref:System.Windows.Media.Brush.Opacity%2A?displayProperty=nameWithType> em vez da configuração do valor do elemento <xref:System.Windows.UIElement.Opacity%2A> propriedade. Modificando um elemento <xref:System.Windows.UIElement.Opacity%2A> pode fazer com que uma propriedade [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] para criar uma superfície temporária.  
  
<a name="Navigation_Objects"></a>   
## <a name="navigation-to-object"></a>Navegação para objeto  
 O <xref:System.Windows.Navigation.NavigationWindow> objeto derivado de <xref:System.Windows.Window> e estende com suporte de navegação de conteúdo, principalmente por agregar <xref:System.Windows.Navigation.NavigationService> e o diário. Você pode atualizar a área do cliente <xref:System.Windows.Navigation.NavigationWindow> especificando um [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] ou um objeto. O exemplo a seguir mostra os dois métodos:  
  
 [!code-csharp[Performance#PerformanceSnippet14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/TestNavigation.xaml.cs#performancesnippet14)]
 [!code-vb[Performance#PerformanceSnippet14](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/testnavigation.xaml.vb#performancesnippet14)]  
  
 Cada <xref:System.Windows.Navigation.NavigationWindow> objeto tem um diário que registra o histórico de navegação do usuário na janela. Uma das finalidades do diário é permitir aos usuários rastrear seus passos.  
  
 Quando você navega usando um [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)], o diário armazena apenas a referência [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]. Isso significa que sempre que você revisita a página, ela é dinamicamente reconstruída, o que pode ser demorado, dependendo da complexidade da página. Nesse caso, o custo de armazenamento do diário é baixo, mas o tempo para reconstituir a página é potencialmente alto.  
  
 Quando você navega usando um objeto, o diário armazena toda a árvore visual do objeto. Isso significa que sempre que você revisita a página, ela é renderizada imediatamente sem precisar ser reconstruída. Nesse caso, o custo de armazenamento do diário é alto, mas o tempo para reconstituir a página é baixo.  
  
 Quando você usa o <xref:System.Windows.Navigation.NavigationWindow> do objeto, você precisará ter em mente, como o suporte de diário impacta o desempenho do aplicativo. Para obter mais informações, consulte [Visão geral de navegação](../../../../docs/framework/wpf/app-development/navigation-overview.md).  
  
<a name="Hit_Testing"></a>   
## <a name="hit-testing-on-large-3d-surfaces"></a>Testes de clique em grandes superfícies 3D  
 Teste de clique em grandes superfícies 3D é uma operação com uso intenso de desempenho em termos de consumo de CPU. Isso é especialmente verdadeiro quando a superfície 3D é animada. Se você não precisar de teste de clique nessas superfícies, desabilite-o. Objetos que são derivados de <xref:System.Windows.UIElement> pode desabilitar o teste de hit definindo o <xref:System.Windows.UIElement.IsHitTestVisible%2A> propriedade `false`.  
  
<a name="CompositionTarget_Rendering_Event"></a>   
## <a name="compositiontargetrendering-event"></a>Evento CompositionTarget.Rendering  
 O <xref:System.Windows.Media.CompositionTarget.Rendering?displayProperty=nameWithType> faz com que o evento [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] anime continuamente. Se você usar esse evento, desanexe-o em cada oportunidade.  
  
<a name="Avoid_Using_ScrollBarVisibility"></a>   
## <a name="avoid-using-scrollbarvisibilityauto"></a>Evite usar ScrollBarVisibility=Auto  
 Sempre que possível, evite usar o <xref:System.Windows.Controls.ScrollBarVisibility.Auto?displayProperty=nameWithType> valor para o `HorizontalScrollBarVisibility` e `VerticalScrollBarVisibility` propriedades. Essas propriedades são definidas para <xref:System.Windows.Controls.RichTextBox>, <xref:System.Windows.Controls.ScrollViewer>, e <xref:System.Windows.Controls.TextBox> objetos e como uma propriedade anexada para o <xref:System.Windows.Controls.ListBox> objeto. Em vez disso, defina <xref:System.Windows.Controls.ScrollBarVisibility> para <xref:System.Windows.Controls.ScrollBarVisibility.Disabled>, <xref:System.Windows.Controls.ScrollBarVisibility.Hidden>, ou <xref:System.Windows.Controls.ScrollBarVisibility.Visible>.  
  
 O <xref:System.Windows.Controls.ScrollBarVisibility.Auto> valor destina-se de casos quando o espaço é limitado e barras de rolagem devem ser exibidas somente quando necessário. Por exemplo, pode ser útil para usar esse <xref:System.Windows.Controls.ScrollBarVisibility> valor com um <xref:System.Windows.Controls.ListBox> de 30 itens em oposição a um <xref:System.Windows.Controls.TextBox> com centenas de linhas de texto.  
  
<a name="FontCache"></a>   
## <a name="configure-font-cache-service-to-reduce-start-up-time"></a>Configurar o serviço de cache de fonte para reduzir o tempo de inicialização  
 O serviço de Cache de Fontes [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] compartilha dados de fontes entre aplicativos [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. O primeiro aplicativo [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] executado iniciará esse serviço se o serviço ainda não estiver em execução. Se você estiver usando [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)], você pode definir o serviço "Windows Presentation Foundation (WPF) Font Cache 3.0.0.0" de "Manual" (o padrão) para "Automático (início atrasado)" para reduzir o tempo de inicialização inicial de [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplicativos.  
  
## <a name="see-also"></a>Consulte também  
 [Planejando para desempenho do aplicativo](../../../../docs/framework/wpf/advanced/planning-for-application-performance.md)  
 [Aproveitando o hardware](../../../../docs/framework/wpf/advanced/optimizing-performance-taking-advantage-of-hardware.md)  
 [Layout e design](../../../../docs/framework/wpf/advanced/optimizing-performance-layout-and-design.md)  
 [Elementos gráficos e geração de imagens 2D](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)  
 [Comportamento do objeto](../../../../docs/framework/wpf/advanced/optimizing-performance-object-behavior.md)  
 [Recursos do aplicativo](../../../../docs/framework/wpf/advanced/optimizing-performance-application-resources.md)  
 [Texto](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)  
 [Associação de dados](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)  
 [Dicas e truques de animação](../../../../docs/framework/wpf/graphics-multimedia/animation-tips-and-tricks.md)
