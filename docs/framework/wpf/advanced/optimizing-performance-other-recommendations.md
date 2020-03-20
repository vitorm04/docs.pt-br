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
ms.openlocfilehash: 727331adb41251460209f157d1804ff455bcf473
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186298"
---
# <a name="optimizing-performance-other-recommendations"></a>Otimizando desempenho: outras recomendações
<a name="introduction"></a> Este tópico apresenta recomendações de desempenho além daquelas abordadas pelos tópicos na seção [Otimizando o desempenho do aplicativo WPF](optimizing-wpf-application-performance.md).  
  
 Este tópico contém as seguintes seções:  
  
- [Opacidade em pincéis versus opacidade em elementos](#Opacity)  
  
- [Navegação para objeto](#Navigation_Objects)  
  
- [Testes de clique em grandes superfícies 3D](#Hit_Testing)  
  
- [Evento CompositionTarget.Rendering](#CompositionTarget_Rendering_Event)  
  
- [Evite usar ScrollBarVisibility=Auto](#Avoid_Using_ScrollBarVisibility)  
  
- [Configurar o serviço de cache de fonte para reduzir o tempo de inicialização](#FontCache)  
  
<a name="Opacity"></a>
## <a name="opacity-on-brushes-versus-opacity-on-elements"></a>Opacidade em pincéis versus opacidade em elementos  
 Quando você <xref:System.Windows.Media.Brush> usa um <xref:System.Windows.Shapes.Shape.Fill%2A> <xref:System.Windows.Shapes.Shape.Stroke%2A> para definir o ou de <xref:System.Windows.Media.Brush.Opacity%2A?displayProperty=nameWithType> um elemento, é melhor <xref:System.Windows.UIElement.Opacity%2A> definir o valor em vez de definir a propriedade do elemento. Modificar a propriedade <xref:System.Windows.UIElement.Opacity%2A> de um [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elemento pode causar a criação de uma superfície temporária.  
  
<a name="Navigation_Objects"></a>
## <a name="navigation-to-object"></a>Navegação para objeto  
 O <xref:System.Windows.Navigation.NavigationWindow> objeto deriva <xref:System.Windows.Window> e o estende com suporte de navegação <xref:System.Windows.Navigation.NavigationService> de conteúdo, principalmente pela agregação e pelo diário. Você pode atualizar a <xref:System.Windows.Navigation.NavigationWindow> área do cliente especificando um uri (identificador de recursos uniforme) ou um objeto. O exemplo a seguir mostra os dois métodos:  
  
 [!code-csharp[Performance#PerformanceSnippet14](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/TestNavigation.xaml.cs#performancesnippet14)]
 [!code-vb[Performance#PerformanceSnippet14](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/testnavigation.xaml.vb#performancesnippet14)]  
  
 Cada <xref:System.Windows.Navigation.NavigationWindow> objeto tem um diário que registra o histórico de navegação do usuário nessa janela. Uma das finalidades do diário é permitir aos usuários rastrear seus passos.  
  
 Quando você navega usando um uri identificador de recursos uniforme , o diário armazena apenas a referência uri (uniform resource identifier). Isso significa que sempre que você revisita a página, ela é dinamicamente reconstruída, o que pode ser demorado, dependendo da complexidade da página. Nesse caso, o custo de armazenamento do diário é baixo, mas o tempo para reconstituir a página é potencialmente alto.  
  
 Quando você navega usando um objeto, o diário armazena toda a árvore visual do objeto. Isso significa que sempre que você revisita a página, ela é renderizada imediatamente sem precisar ser reconstruída. Nesse caso, o custo de armazenamento do diário é alto, mas o tempo para reconstituir a página é baixo.  
  
 Ao usar <xref:System.Windows.Navigation.NavigationWindow> o objeto, você precisará ter em mente como o suporte de diário impacta o desempenho do aplicativo. Para obter mais informações, consulte [Visão geral da navegação](../app-development/navigation-overview.md).  
  
<a name="Hit_Testing"></a>
## <a name="hit-testing-on-large-3d-surfaces"></a>Testes de clique em grandes superfícies 3D  
 Teste de clique em grandes superfícies 3D é uma operação com uso intenso de desempenho em termos de consumo de CPU. Isso é especialmente verdadeiro quando a superfície 3D é animada. Se você não precisar de teste de clique nessas superfícies, desabilite-o. Objetos derivados <xref:System.Windows.UIElement> podem desativar o teste de <xref:System.Windows.UIElement.IsHitTestVisible%2A> hit `false`definindo a propriedade para .  
  
<a name="CompositionTarget_Rendering_Event"></a>
## <a name="compositiontargetrendering-event"></a>Evento CompositionTarget.Rendering  
 O <xref:System.Windows.Media.CompositionTarget.Rendering?displayProperty=nameWithType> evento [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] faz com que se anime continuamente. Se você usar esse evento, desanexe-o em cada oportunidade.  
  
<a name="Avoid_Using_ScrollBarVisibility"></a>
## <a name="avoid-using-scrollbarvisibilityauto"></a>Evite usar ScrollBarVisibility=Auto  
 Sempre que possível, <xref:System.Windows.Controls.ScrollBarVisibility.Auto?displayProperty=nameWithType> evite `HorizontalScrollBarVisibility` usar `VerticalScrollBarVisibility` o valor para as propriedades. Essas propriedades são <xref:System.Windows.Controls.RichTextBox> <xref:System.Windows.Controls.ScrollViewer>definidas <xref:System.Windows.Controls.TextBox> para , e objetos, <xref:System.Windows.Controls.ListBox> e como uma propriedade anexada para o objeto. Em vez <xref:System.Windows.Controls.ScrollBarVisibility> <xref:System.Windows.Controls.ScrollBarVisibility.Disabled>disso, definir para , <xref:System.Windows.Controls.ScrollBarVisibility.Hidden>ou <xref:System.Windows.Controls.ScrollBarVisibility.Visible>.  
  
 O <xref:System.Windows.Controls.ScrollBarVisibility.Auto> valor destina-se a casos em que o espaço é limitado e as barras de rolagem só devem ser exibidas quando necessário. Por exemplo, pode ser útil <xref:System.Windows.Controls.ScrollBarVisibility> usar <xref:System.Windows.Controls.ListBox> esse valor com um de <xref:System.Windows.Controls.TextBox> 30 itens em oposição a um com centenas de linhas de texto.  
  
<a name="FontCache"></a>
## <a name="configure-font-cache-service-to-reduce-start-up-time"></a>Configurar o serviço de cache de fonte para reduzir o tempo de inicialização  
 O serviço WPF Font Cache compartilha dados de fonte entre aplicativos WPF. O primeiro aplicativo WPF executado inicia este serviço se o serviço ainda não estiver em execução. Se você estiver usando o Windows Vista, você pode definir o serviço "Windows Presentation Foundation (WPF) Font Cache 3.0.0.0" de "Manual" (o padrão) para "Início automático (Início atrasado)" para reduzir o tempo inicial de inicialização dos aplicativos WPF.  
  
## <a name="see-also"></a>Confira também

- [Planejando o desempenho do aplicativo](planning-for-application-performance.md)
- [Aproveitar o hardware](optimizing-performance-taking-advantage-of-hardware.md)
- [Layout e design](optimizing-performance-layout-and-design.md)
- [Elementos gráficos e geração de imagens 2D](optimizing-performance-2d-graphics-and-imaging.md)
- [Comportamento do objeto](optimizing-performance-object-behavior.md)
- [Recursos de aplicação](optimizing-performance-application-resources.md)
- [Texto](optimizing-performance-text.md)
- [Associação de dados](optimizing-performance-data-binding.md)
- [Dicas e truques de animação](../graphics-multimedia/animation-tips-and-tricks.md)
