---
title: 'Otimizando desempenho: Layout e design'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- layout [WPF], optimizing performance
- design considerations [WPF]
- layout pass [WPF]
ms.assetid: 005f4cda-a849-448b-916b-38d14d9a96fe
ms.openlocfilehash: 8a76dd5de9f374d77345eeab3d259624546fed7c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59107062"
---
# <a name="optimizing-performance-layout-and-design"></a>Otimizando desempenho: Layout e design
O design de seu aplicativo [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pode afetar o desempenho criando sobrecarga desnecessária no cálculo de layout e validando referências de objetos. A construção de objetos, particularmente no tempo de execução, pode afetar as características de desempenho do seu aplicativo.  
  
 Este tópico apresenta recomendações de desempenho nessas áreas.  
  
## <a name="layout"></a>Layout  
 O termo "cálculo de layout" descreve o processo de medir e organizar os membros de um <xref:System.Windows.Controls.Panel>-derivados do coleção objeto de filhos e então desenhá-los na tela. O cálculo de layout é um processo matematicamente intensivo: quanto maior o número de filhos na coleção, maior será o número de cálculos necessários. Por exemplo, cada vez que um filho <xref:System.Windows.UIElement> objeto na coleção muda de posição, ele tem o potencial de disparar uma nova passagem pelo sistema de layout. Devido ao forte relacionamento entre as características de objeto e comportamento de layout, é importante compreender os tipos de eventos que podem invocar o sistema de layout. Seu aplicativo terá um desempenho melhor reduzindo ao máximo as invocações desnecessárias do cálculo de layout.  
  
 O sistema de layout completa dois cálculos para cada membro filho em uma coleção: um cálculo de medição e um cálculo de organização. Cada objeto filho oferece sua própria implementação substituída do <xref:System.Windows.UIElement.Measure%2A> e <xref:System.Windows.UIElement.Arrange%2A> métodos para fornecer seu próprio comportamento específico de layout. Em sua forma mais simples, o layout é um sistema recursivo que leva a um elemento a ser dimensionado, posicionado e desenhado na tela.  
  
-   Um filho <xref:System.Windows.UIElement> objeto começa o processo de layout primeiro tendo suas propriedades principais medidas.  
  
-   O objeto <xref:System.Windows.FrameworkElement> as propriedades relacionadas ao tamanho, como <xref:System.Windows.FrameworkElement.Width%2A>, <xref:System.Windows.FrameworkElement.Height%2A>, e <xref:System.Windows.FrameworkElement.Margin%2A>, são avaliadas.  
  
-   <xref:System.Windows.Controls.Panel>-lógica específica é aplicada, como o <xref:System.Windows.Controls.DockPanel.Dock%2A> propriedade do <xref:System.Windows.Controls.DockPanel>, ou o <xref:System.Windows.Controls.StackPanel.Orientation%2A> propriedade do <xref:System.Windows.Controls.StackPanel>.  
  
-   O conteúdo é organizado, ou posicionado, após a medição de todos os objetos filho.  
  
-   A coleção de objetos filho é desenhada na tela.  
  
 O processo de cálculo de layout será invocado novamente se qualquer uma das ações a seguir ocorrer:  
  
-   Um objeto filho é adicionado à coleção.  
  
-   Um <xref:System.Windows.FrameworkElement.LayoutTransform%2A> é aplicada ao objeto filho.  
  
-   O <xref:System.Windows.UIElement.UpdateLayout%2A> método é chamado para o objeto filho.  
  
-   Quando ocorre uma alteração ao valor da propriedade de dependência marcada com metadados que afetam a medida ou cálculos da organização.  
  
### <a name="use-the-most-efficient-panel-where-possible"></a>Usar o painel mais eficiente quando possível  
 A complexidade do processo de layout é baseada diretamente no comportamento de layout do <xref:System.Windows.Controls.Panel>-derivados de elementos que você usar. Por exemplo, uma <xref:System.Windows.Controls.Grid> ou <xref:System.Windows.Controls.StackPanel> controle fornece muito mais funcionalidade do que um <xref:System.Windows.Controls.Canvas> controle. O preço para esse aumento de funcionalidade é um aumento maior nos custos de desempenho. No entanto, se você não precisar da funcionalidade que um <xref:System.Windows.Controls.Grid> fornece controle, você deve usar as alternativas menos dispendiosas, como um <xref:System.Windows.Controls.Canvas> ou um painel personalizado.  
  
 Para obter mais informações, consulte [Visão geral dos painéis](../controls/panels-overview.md).  
  
### <a name="update-rather-than-replace-a-rendertransform"></a>Atualizar, em vez de substituir, uma RenderTransform  
 Você poderá atualizar uma <xref:System.Windows.Media.Transform> em vez de substituí-la como o valor de um <xref:System.Windows.UIElement.RenderTransform%2A> propriedade. Isso é especialmente verdadeiro em cenários que envolvem animação. Atualizando uma existente <xref:System.Windows.Media.Transform>, você evita iniciar um cálculo de layout desnecessário.  
  
### <a name="build-your-tree-top-down"></a>Compilar sua árvore de cima para baixo  
 Quando um nó é adicionado ou removido da árvore lógica, invalidações de propriedade são geradas no pai do nó e todos os seus filhos. Como resultado, um padrão de construção de cima para baixo deve sempre ser seguido para evitar o custo de invalidações desnecessárias em nós que já foram validados. A tabela a seguir mostra a diferença no tempo de execução entre compilar uma árvore de cima para baixo versus de baixo para cima, onde a árvore tem 150 níveis de profundidade com um único <xref:System.Windows.Controls.TextBlock> e <xref:System.Windows.Controls.DockPanel> em cada nível.  
  
|**Ação**|**Build da árvore (em ms)**|**Renderizar – inclui o build da árvore (em ms)**|  
|----------------|---------------------------------|-------------------------------------------------|  
|De baixo para cima|366|454|  
|De cima para baixo|11|96|  
  
 O exemplo de código a seguir demonstra como criar uma árvore de cima para baixo.  
  
 [!code-csharp[Performance#PerformanceSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet1)]
 [!code-vb[Performance#PerformanceSnippet1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet1)]  
  
 Para obter mais informações sobre a árvore lógica, consulte [Árvores no WPF](trees-in-wpf.md).  
  
## <a name="see-also"></a>Consulte também

- [Otimizando o desempenho do aplicativo WPF](optimizing-wpf-application-performance.md)
- [Planejando para desempenho do aplicativo](planning-for-application-performance.md)
- [Aproveitando o hardware](optimizing-performance-taking-advantage-of-hardware.md)
- [Elementos gráficos e geração de imagens 2D](optimizing-performance-2d-graphics-and-imaging.md)
- [Comportamento do objeto](optimizing-performance-object-behavior.md)
- [Recursos do aplicativo](optimizing-performance-application-resources.md)
- [Texto](optimizing-performance-text.md)
- [Associação de dados](optimizing-performance-data-binding.md)
- [Outras recomendações de desempenho](optimizing-performance-other-recommendations.md)
- [Layout](layout.md)
