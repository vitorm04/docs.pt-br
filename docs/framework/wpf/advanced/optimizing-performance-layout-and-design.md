---
title: 'Otimizando desempenho: layout and design'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- layout [WPF], optimizing performance
- design considerations [WPF]
- layout pass [WPF]
ms.assetid: 005f4cda-a849-448b-916b-38d14d9a96fe
ms.openlocfilehash: 9c9921e664d69038480e73ee6779ca9e48b81c7a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="optimizing-performance-layout-and-design"></a>Otimizando desempenho: layout and design
O design de seu aplicativo [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pode afetar o desempenho criando sobrecarga desnecessária no cálculo de layout e validando referências de objetos. A construção de objetos, particularmente no tempo de execução, pode afetar as características de desempenho do seu aplicativo.  
  
 Este tópico apresenta recomendações de desempenho nessas áreas.  
  
## <a name="layout"></a>Layout  
 O termo "layout pass" descreve o processo de medir e organizar os membros de um <xref:System.Windows.Controls.Panel>-derivados do coleção objeto de filhos e, em seguida, na tela de desenho. O cálculo de layout é um processo matematicamente intensivo: quanto maior o número de filhos na coleção, maior será o número de cálculos necessários. Por exemplo, cada vez que um filho <xref:System.Windows.UIElement> sua posição alterações do objeto na coleção, ele tem o potencial de disparar uma nova passagem pelo sistema de layout. Devido ao forte relacionamento entre as características de objeto e comportamento de layout, é importante compreender os tipos de eventos que podem invocar o sistema de layout. Seu aplicativo terá um desempenho melhor reduzindo ao máximo as invocações desnecessárias do cálculo de layout.  
  
 O sistema de layout completa dois cálculos para cada membro filho em uma coleção: um cálculo de medição e um cálculo de organização. Cada objeto filho oferece sua própria implementação substituída do <xref:System.Windows.UIElement.Measure%2A> e <xref:System.Windows.UIElement.Arrange%2A> métodos para fornecer seu próprio comportamento específico de layout. Em sua forma mais simples, o layout é um sistema recursivo que leva a um elemento a ser dimensionado, posicionado e desenhado na tela.  
  
-   Um filho <xref:System.Windows.UIElement> objeto começa o processo de layout tendo suas propriedades principais medidas.  
  
-   O objeto <xref:System.Windows.FrameworkElement> propriedades que estão relacionadas a tamanho, tais como <xref:System.Windows.FrameworkElement.Width%2A>, <xref:System.Windows.FrameworkElement.Height%2A>, e <xref:System.Windows.FrameworkElement.Margin%2A>, são avaliadas.  
  
-   <xref:System.Windows.Controls.Panel>-lógica específica é aplicada, como o <xref:System.Windows.Controls.DockPanel.Dock%2A> propriedade do <xref:System.Windows.Controls.DockPanel>, ou o <xref:System.Windows.Controls.StackPanel.Orientation%2A> propriedade o <xref:System.Windows.Controls.StackPanel>.  
  
-   O conteúdo é organizado, ou posicionado, após a medição de todos os objetos filho.  
  
-   A coleção de objetos filho é desenhada na tela.  
  
 O processo de cálculo de layout será invocado novamente se qualquer uma das ações a seguir ocorrer:  
  
-   Um objeto filho é adicionado à coleção.  
  
-   Um <xref:System.Windows.FrameworkElement.LayoutTransform%2A> é aplicada ao objeto filho.  
  
-   O <xref:System.Windows.UIElement.UpdateLayout%2A> método é chamado para o objeto filho.  
  
-   Quando ocorre uma alteração ao valor da propriedade de dependência marcada com metadados que afetam a medida ou cálculos da organização.  
  
### <a name="use-the-most-efficient-panel-where-possible"></a>Usar o painel mais eficiente quando possível  
 A complexidade do processo de layout diretamente se baseia o comportamento de layout de <xref:System.Windows.Controls.Panel>-derivado elementos que você usar. Por exemplo, um <xref:System.Windows.Controls.Grid> ou <xref:System.Windows.Controls.StackPanel> controle oferece funcionalidade muito mais do que um <xref:System.Windows.Controls.Canvas> controle. O preço para esse aumento de funcionalidade é um aumento maior nos custos de desempenho. No entanto, se você não precisar da funcionalidade que uma <xref:System.Windows.Controls.Grid> fornece controle, você deve usar as alternativas mais baratos, como um <xref:System.Windows.Controls.Canvas> ou um painel personalizado.  
  
 Para obter mais informações, consulte [Visão geral dos painéis](../../../../docs/framework/wpf/controls/panels-overview.md).  
  
### <a name="update-rather-than-replace-a-rendertransform"></a>Atualizar, em vez de substituir, uma RenderTransform  
 Você poderá atualizar um <xref:System.Windows.Media.Transform> em vez de substituí-la como o valor de um <xref:System.Windows.UIElement.RenderTransform%2A> propriedade. Isso é especialmente verdadeiro em cenários que envolvem animação. Atualizando uma existente <xref:System.Windows.Media.Transform>, você evita iniciar um cálculo de layout desnecessário.  
  
### <a name="build-your-tree-top-down"></a>Compilar sua árvore de cima para baixo  
 Quando um nó é adicionado ou removido da árvore lógica, invalidações de propriedade são geradas no pai do nó e todos os seus filhos. Como resultado, um padrão de construção de cima para baixo deve sempre ser seguido para evitar o custo de invalidações desnecessárias em nós que já foram validados. A tabela a seguir mostra a diferença em tempo de execução entre construir uma árvore de cima para baixo em vez de baixo para cima, onde a árvore tem 150 níveis de profundidade com um único <xref:System.Windows.Controls.TextBlock> e <xref:System.Windows.Controls.DockPanel> em cada nível.  
  
|**Ação**|**Build da árvore (em ms)**|**Renderizar – inclui o build da árvore (em ms)**|  
|----------------|---------------------------------|-------------------------------------------------|  
|De baixo para cima|366|454|  
|De cima para baixo|11|96|  
  
 O exemplo de código a seguir demonstra como criar uma árvore de cima para baixo.  
  
 [!code-csharp[Performance#PerformanceSnippet1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet1)]
 [!code-vb[Performance#PerformanceSnippet1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet1)]  
  
 Para obter mais informações sobre a árvore lógica, consulte [Árvores no WPF](../../../../docs/framework/wpf/advanced/trees-in-wpf.md).  
  
## <a name="see-also"></a>Consulte também  
 [Otimizando o desempenho do aplicativo WPF](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)  
 [Planejando para desempenho do aplicativo](../../../../docs/framework/wpf/advanced/planning-for-application-performance.md)  
 [Aproveitando o hardware](../../../../docs/framework/wpf/advanced/optimizing-performance-taking-advantage-of-hardware.md)  
 [Elementos gráficos e geração de imagens 2D](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)  
 [Comportamento do objeto](../../../../docs/framework/wpf/advanced/optimizing-performance-object-behavior.md)  
 [Recursos do aplicativo](../../../../docs/framework/wpf/advanced/optimizing-performance-application-resources.md)  
 [Texto](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)  
 [Associação de dados](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)  
 [Outras recomendações de desempenho](../../../../docs/framework/wpf/advanced/optimizing-performance-other-recommendations.md)  
 [Layout](../../../../docs/framework/wpf/advanced/layout.md)
