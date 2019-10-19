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
ms.openlocfilehash: cf621ab5f423e2465999b26f32489af1132bece0
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582447"
---
# <a name="optimizing-performance-other-recommendations"></a>Otimizando desempenho: outras recomendações
<a name="introduction"></a> Este tópico apresenta recomendações de desempenho além daquelas abordadas pelos tópicos na seção [Otimizando o desempenho do aplicativo WPF](optimizing-wpf-application-performance.md).  
  
 Esse tópico contém as seguintes seções:  
  
- [Opacidade em pincéis versus opacidade em elementos](#Opacity)  
  
- [Navegação para objeto](#Navigation_Objects)  
  
- [Testes de clique em grandes superfícies 3D](#Hit_Testing)  
  
- [Evento CompositionTarget.Rendering](#CompositionTarget_Rendering_Event)  
  
- [Evite usar ScrollBarVisibility=Auto](#Avoid_Using_ScrollBarVisibility)  
  
- [Configurar o serviço de cache de fonte para reduzir o tempo de inicialização](#FontCache)  
  
<a name="Opacity"></a>   
## <a name="opacity-on-brushes-versus-opacity-on-elements"></a>Opacidade em pincéis versus opacidade em elementos  
 Quando você usa um <xref:System.Windows.Media.Brush> para definir o <xref:System.Windows.Shapes.Shape.Fill%2A> ou <xref:System.Windows.Shapes.Shape.Stroke%2A> de um elemento, é melhor definir o valor <xref:System.Windows.Media.Brush.Opacity%2A?displayProperty=nameWithType> em vez da configuração da propriedade <xref:System.Windows.UIElement.Opacity%2A> do elemento. Modificar a propriedade de <xref:System.Windows.UIElement.Opacity%2A> de um elemento pode fazer com que [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] crie uma superfície temporária.  
  
<a name="Navigation_Objects"></a>   
## <a name="navigation-to-object"></a>Navegação para objeto  
 O objeto <xref:System.Windows.Navigation.NavigationWindow> deriva de <xref:System.Windows.Window> e o estende com suporte à navegação de conteúdo, principalmente pela agregação de <xref:System.Windows.Navigation.NavigationService> e o diário. Você pode atualizar a área do cliente de <xref:System.Windows.Navigation.NavigationWindow> especificando um URI (Uniform Resource Identifier) ou um objeto. O exemplo a seguir mostra os dois métodos:  
  
 [!code-csharp[Performance#PerformanceSnippet14](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/TestNavigation.xaml.cs#performancesnippet14)]
 [!code-vb[Performance#PerformanceSnippet14](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/testnavigation.xaml.vb#performancesnippet14)]  
  
 Cada objeto de <xref:System.Windows.Navigation.NavigationWindow> tem um diário que registra o histórico de navegação do usuário nessa janela. Uma das finalidades do diário é permitir aos usuários rastrear seus passos.  
  
 Quando você navega usando um URI (Uniform Resource Identifier), o diário armazena apenas a referência do URI (Uniform Resource Identifier). Isso significa que sempre que você revisita a página, ela é dinamicamente reconstruída, o que pode ser demorado, dependendo da complexidade da página. Nesse caso, o custo de armazenamento do diário é baixo, mas o tempo para reconstituir a página é potencialmente alto.  
  
 Quando você navega usando um objeto, o diário armazena toda a árvore visual do objeto. Isso significa que sempre que você revisita a página, ela é renderizada imediatamente sem precisar ser reconstruída. Nesse caso, o custo de armazenamento do diário é alto, mas o tempo para reconstituir a página é baixo.  
  
 Ao usar o objeto <xref:System.Windows.Navigation.NavigationWindow>, você precisará ter em mente como o suporte ao diário afeta o desempenho do aplicativo. Para obter mais informações, consulte [Visão geral de navegação](../app-development/navigation-overview.md).  
  
<a name="Hit_Testing"></a>   
## <a name="hit-testing-on-large-3d-surfaces"></a>Testes de clique em grandes superfícies 3D  
 Teste de clique em grandes superfícies 3D é uma operação com uso intenso de desempenho em termos de consumo de CPU. Isso é especialmente verdadeiro quando a superfície 3D é animada. Se você não precisar de teste de clique nessas superfícies, desabilite-o. Os objetos derivados de <xref:System.Windows.UIElement> podem desabilitar o teste de clique definindo a propriedade <xref:System.Windows.UIElement.IsHitTestVisible%2A> como `false`.  
  
<a name="CompositionTarget_Rendering_Event"></a>   
## <a name="compositiontargetrendering-event"></a>Evento CompositionTarget.Rendering  
 O evento <xref:System.Windows.Media.CompositionTarget.Rendering?displayProperty=nameWithType> faz com que [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] anime continuamente. Se você usar esse evento, desanexe-o em cada oportunidade.  
  
<a name="Avoid_Using_ScrollBarVisibility"></a>   
## <a name="avoid-using-scrollbarvisibilityauto"></a>Evite usar ScrollBarVisibility=Auto  
 Sempre que possível, evite usar o valor <xref:System.Windows.Controls.ScrollBarVisibility.Auto?displayProperty=nameWithType> para as propriedades `HorizontalScrollBarVisibility` e `VerticalScrollBarVisibility`. Essas propriedades são definidas para objetos <xref:System.Windows.Controls.RichTextBox>, <xref:System.Windows.Controls.ScrollViewer> e <xref:System.Windows.Controls.TextBox> e como uma propriedade anexada para o objeto <xref:System.Windows.Controls.ListBox>. Em vez disso, defina <xref:System.Windows.Controls.ScrollBarVisibility> como <xref:System.Windows.Controls.ScrollBarVisibility.Disabled>, <xref:System.Windows.Controls.ScrollBarVisibility.Hidden> ou <xref:System.Windows.Controls.ScrollBarVisibility.Visible>.  
  
 O valor <xref:System.Windows.Controls.ScrollBarVisibility.Auto> se destina a casos em que o espaço é limitado e barras de rolagem só devem ser exibidas quando necessário. Por exemplo, pode ser útil usar esse <xref:System.Windows.Controls.ScrollBarVisibility> valor com um <xref:System.Windows.Controls.ListBox> de 30 itens em oposição a um <xref:System.Windows.Controls.TextBox> com centenas de linhas de texto.  
  
<a name="FontCache"></a>   
## <a name="configure-font-cache-service-to-reduce-start-up-time"></a>Configurar o serviço de cache de fonte para reduzir o tempo de inicialização  
 O serviço de Cache de Fontes [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] compartilha dados de fontes entre aplicativos [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. O primeiro aplicativo [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] executado iniciará esse serviço se o serviço ainda não estiver em execução. Se você estiver usando [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)], poderá definir o serviço "Windows Presentation Foundation (WPF) 3.0.0.0 do cache de fonte" de "manual" (o padrão) como "automático (início atrasado)" para reduzir o tempo de inicialização inicial dos aplicativos [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].  
  
## <a name="see-also"></a>Consulte também

- [Planejando para desempenho do aplicativo](planning-for-application-performance.md)
- [Aproveitando o hardware](optimizing-performance-taking-advantage-of-hardware.md)
- [Layout e design](optimizing-performance-layout-and-design.md)
- [Elementos gráficos e geração de imagens 2D](optimizing-performance-2d-graphics-and-imaging.md)
- [Comportamento do objeto](optimizing-performance-object-behavior.md)
- [Recursos do aplicativo](optimizing-performance-application-resources.md)
- [Texto](optimizing-performance-text.md)
- [Associação de dados](optimizing-performance-data-binding.md)
- [Dicas e truques de animação](../graphics-multimedia/animation-tips-and-tricks.md)
