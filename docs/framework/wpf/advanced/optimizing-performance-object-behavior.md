---
title: 'Otimizando desempenho: comportamento do objeto'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- user interface virtualization [WPF]
- dependency properties [WPF], performance
- event handlers [WPF]
- object performance considerations [WPF]
- Freezable objects [WPF], performance
ms.assetid: 73aa2f47-1d73-439a-be1f-78dc4ba2b5bd
ms.openlocfilehash: 64e567cd28e9458b483b0963e0dedd924ad23bab
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2020
ms.locfileid: "77094482"
---
# <a name="optimizing-performance-object-behavior"></a>Otimizando desempenho: comportamento do objeto
O entendimento do comportamento intrínseco de objetos [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ajudará você a fazer o balanceamento correto entre desempenho e funcionalidade.  

<a name="Not_Removing_Event_Handlers"></a>   
## <a name="not-removing-event-handlers-on-objects-may-keep-objects-alive"></a>Não remover manipuladores de eventos em objetos poderá manter os objetos ativos  
 O delegado que um objeto passa para seu evento é, efetivamente, uma referência a esse objeto. Portanto, os manipuladores de eventos podem manter objetos ativos por mais tempo que o esperado. Ao realizar a limpeza de um objeto que tenha sido registrado para escutar um evento de objeto, é essencial remover esse delegado antes de liberar o objeto. Manter objetos desnecessários ativos aumenta o uso de memória do aplicativo. Isso é especialmente verdadeiro quando o objeto é a raiz de uma árvore lógica ou de uma árvore visual.  
  
 O [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] apresenta um padrão fraco de ouvinte de eventos para eventos que podem ser úteis em situações em que as relações de tempo de vida do objeto, entre a origem e o ouvinte, são difíceis de controlar. Alguns eventos do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] existentes usam esse padrão. Se estiver implementando objetos com eventos personalizados, esse padrão poderá ser útil para você. Para obter detalhes, consulte [Padrões de evento fracos](weak-event-patterns.md).  
  
 Há várias ferramentas, como o Criador de Perfil CLR e o Visualizador de Conjunto de Trabalho, que podem fornecer informações sobre o uso de memória de um processo especificado. O Criador de Perfil CLR inclui várias exibições muito úteis do perfil de alocação, incluindo um histograma de tipos alocados, grafos de alocação e de chamadas, uma linha do tempo mostrando coletas de lixo de várias gerações e o estado resultante do heap gerenciado após essas coletas, além de uma árvore de chamadas mostrando as cargas de assembly e alocações por método. Para obter mais informações, consulte [Desempenho](https://docs.microsoft.com/previous-versions/aa497289(v=msdn.10)).  
  
<a name="DPs_and_Objects"></a>   
## <a name="dependency-properties-and-objects"></a>Propriedades de dependência e objetos  
 Em geral, o acesso a uma propriedade de dependência de um <xref:System.Windows.DependencyObject> não é mais lento do que acessar uma propriedade CLR. Embora haja uma pequena sobrecarga de desempenho para definir um valor de propriedade, obter um valor é tão rápido quanto obter o valor de uma propriedade CLR. O fato de as propriedades de dependência darem suporte a recursos robustos, como vinculação de dados, animação, herança e estilos é a compensação pela pequena sobrecarga de desempenho. Para obter mais informações, consulte [Visão geral sobre propriedades de dependência](dependency-properties-overview.md).  
  
### <a name="dependencyproperty-optimizations"></a>Otimizações de DependencyProperty  
 Você deve definir as propriedades de dependência em seu aplicativo com muito cuidado. Se o <xref:System.Windows.DependencyProperty> afeta apenas as opções de metadados do tipo de renderização, em vez de outras opções de metadados, como <xref:System.Windows.FrameworkPropertyMetadata.AffectsMeasure%2A>, você deve marcá-lo como tal, substituindo seus metadados. Para obter mais informações sobre como substituir ou obter metadados de propriedades, consulte [Metadados de propriedades de dependência](dependency-property-metadata.md).  
  
 Talvez seja mais eficiente fazer com que um manipulador de alterações de propriedade invalide as passagens de medida, organização e renderização manualmente se nem todas as alterações de propriedade afetarem, na verdade, a medida, a organização e a renderização. Por exemplo, você pode decidir renderizar novamente uma tela de fundo apenas quando um valor for maior que um limite definido. Nesse caso, seu manipulador de alteração de propriedade só invalidaria a renderização quando o valor excedesse o limite definido.  
  
### <a name="making-a-dependencyproperty-inheritable-is-not-free"></a>Há consequências em tornar uma DependencyProperty herdável  
 Por padrão, as propriedades de dependência registradas são não herdáveis. No entanto, você pode explicitamente tornar qualquer propriedade herdável. Embora esse seja um recurso útil, converter uma propriedade para se tornar herdável afeta o desempenho, aumentando o período de tempo para a invalidação da propriedade.  
  
### <a name="use-registerclasshandler-carefully"></a>Usar o RegisterClassHandler com cuidado  
 Embora chamar <xref:System.Windows.EventManager.RegisterClassHandler%2A> permite que você salve o estado da instância, é importante estar ciente de que o manipulador é chamado em cada instância, o que pode causar problemas de desempenho. Use <xref:System.Windows.EventManager.RegisterClassHandler%2A> somente quando seu aplicativo exigir que você salve o estado da instância.  
  
### <a name="set-the-default-value-for-a-dependencyproperty-during-registration"></a>Definir o valor padrão para uma DependencyProperty durante o registro  
 Ao criar um <xref:System.Windows.DependencyProperty> que exija um valor padrão, defina o valor usando os metadados padrão passados como um parâmetro para o método <xref:System.Windows.DependencyProperty.Register%2A> da <xref:System.Windows.DependencyProperty>. Use esta técnica em vez de configurar o valor da propriedade em um construtor ou em cada instância de um elemento.  
  
### <a name="set-the-propertymetadata-value-using-register"></a>Definir o valor de PropertyMetadata usando o registro  
 Ao criar um <xref:System.Windows.DependencyProperty>, você tem a opção de definir o <xref:System.Windows.PropertyMetadata> usando os métodos <xref:System.Windows.DependencyProperty.Register%2A> ou <xref:System.Windows.DependencyProperty.OverrideMetadata%2A>. Embora seu objeto possa ter um construtor estático para chamar <xref:System.Windows.DependencyProperty.OverrideMetadata%2A>, essa não é a solução ideal e afetará o desempenho. Para obter o melhor desempenho, defina o <xref:System.Windows.PropertyMetadata> durante a chamada para <xref:System.Windows.DependencyProperty.Register%2A>.  
  
<a name="Freezable_Objects"></a>   
## <a name="freezable-objects"></a>Objetos congeláveis  
 Uma <xref:System.Windows.Freezable> é um tipo especial de objeto que tem dois Estados: descongelado e congelado. Congelar objetos sempre que possível melhora o desempenho do seu aplicativo e reduz seu conjunto de trabalho. Para obter mais informações, consulte a [Visão geral de objetos congeláveis](freezable-objects-overview.md).  
  
 Cada <xref:System.Windows.Freezable> tem um evento de <xref:System.Windows.Freezable.Changed> que é gerado sempre que ele é alterado. No entanto, as notificações de alteração são dispendiosas em termos de desempenho do aplicativo.  
  
 Considere o exemplo a seguir no qual cada <xref:System.Windows.Shapes.Rectangle> usa o mesmo objeto <xref:System.Windows.Media.Brush>:  
  
 [!code-csharp[Performance#PerformanceSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet2)]
 [!code-vb[Performance#PerformanceSnippet2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet2)]  
  
 Por padrão, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fornece um manipulador de eventos para o evento de <xref:System.Windows.Freezable.Changed> do objeto <xref:System.Windows.Media.SolidColorBrush> para invalidar a propriedade <xref:System.Windows.Shapes.Shape.Fill%2A> do objeto <xref:System.Windows.Shapes.Rectangle>. Nesse caso, sempre que o <xref:System.Windows.Media.SolidColorBrush> tiver que acionar seu evento de <xref:System.Windows.Freezable.Changed> é necessário invocar a função de retorno de chamada para cada <xref:System.Windows.Shapes.Rectangle>— o acúmulo dessas invocações de função de retorno de chamada impõe uma penalidade de desempenho significativa. Além disso, adicionar e remover manipuladores neste ponto exigiria muito do desempenho, já que o aplicativo teria que percorrer toda a lista para fazer isso. Se o cenário do aplicativo nunca alterar o <xref:System.Windows.Media.SolidColorBrush>, você estará pagando o custo de manter <xref:System.Windows.Freezable.Changed> manipuladores de eventos desnecessariamente.  
  
 Congelar um <xref:System.Windows.Freezable> pode melhorar seu desempenho, pois ele não precisa mais gastar recursos para manter notificações de alteração. A tabela a seguir mostra o tamanho de um <xref:System.Windows.Media.SolidColorBrush> simples quando sua propriedade <xref:System.Windows.Freezable.IsFrozen%2A> é definida como `true`, em comparação com quando não é. Isso pressupõe a aplicação de um pincel à propriedade <xref:System.Windows.Shapes.Shape.Fill%2A> de dez objetos <xref:System.Windows.Shapes.Rectangle>.  
  
|**State**|**Tamanho**|  
|---------------|--------------|  
|<xref:System.Windows.Media.SolidColorBrush> congelado|212 bytes|  
|<xref:System.Windows.Media.SolidColorBrush> não congeladas|972 bytes|  
  
 O exemplo de código a seguir demonstra esse conceito:  
  
 [!code-csharp[Performance#PerformanceSnippet3](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet3)]
 [!code-vb[Performance#PerformanceSnippet3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet3)]  
  
### <a name="changed-handlers-on-unfrozen-freezables-may-keep-objects-alive"></a>Manipuladores alterados em Congeláveis descongelados podem manter objetos ativos  
 O delegado que um objeto passa para um evento de <xref:System.Windows.Freezable.Changed> do objeto de <xref:System.Windows.Freezable> é efetivamente uma referência a esse objeto. Portanto, <xref:System.Windows.Freezable.Changed> manipuladores de eventos podem manter os objetos ativos por mais tempo do que o esperado. Ao executar a limpeza de um objeto que foi registrado para escutar um evento de <xref:System.Windows.Freezable.Changed> do objeto de <xref:System.Windows.Freezable>, é essencial remover esse delegado antes de liberar o objeto.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] também conecta <xref:System.Windows.Freezable.Changed> eventos internamente. Por exemplo, todas as propriedades de dependência que levam <xref:System.Windows.Freezable> como um valor escutarão <xref:System.Windows.Freezable.Changed> eventos automaticamente. A propriedade <xref:System.Windows.Shapes.Shape.Fill%2A>, que usa um <xref:System.Windows.Media.Brush>, ilustra esse conceito.  
  
 [!code-csharp[Performance#PerformanceSnippet4](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet4)]
 [!code-vb[Performance#PerformanceSnippet4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet4)]  
  
 Na atribuição de `myBrush` para `myRectangle.Fill`, um delegado apontando de volta para o objeto <xref:System.Windows.Shapes.Rectangle> será adicionado ao evento <xref:System.Windows.Freezable.Changed> do objeto <xref:System.Windows.Media.SolidColorBrush>. Isso significa que o código a seguir, na verdade, não torna o `myRect` qualificado para a coleta de lixo:  
  
 [!code-csharp[Performance#PerformanceSnippet5](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet5)]
 [!code-vb[Performance#PerformanceSnippet5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet5)]  
  
 Nesse caso, `myBrush` ainda está mantendo `myRectangle` Alive e chamará de volta para ele quando ele acionar seu evento de <xref:System.Windows.Freezable.Changed>. Observe que a atribuição de `myBrush` à propriedade <xref:System.Windows.Shapes.Shape.Fill%2A> de um novo <xref:System.Windows.Shapes.Rectangle> simplesmente adicionará outro manipulador de eventos a `myBrush`.  
  
 A maneira recomendada para limpar esses tipos de objetos é remover o <xref:System.Windows.Media.Brush> da propriedade <xref:System.Windows.Shapes.Shape.Fill%2A>, o que, por sua vez, removerá o manipulador de eventos <xref:System.Windows.Freezable.Changed>.  
  
 [!code-csharp[Performance#PerformanceSnippet6](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet6)]
 [!code-vb[Performance#PerformanceSnippet6](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet6)]  
  
<a name="User_Interface_Virtualization"></a>   
## <a name="user-interface-virtualization"></a>Virtualização da interface do usuário  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] também fornece uma variação do elemento <xref:System.Windows.Controls.StackPanel> que "virtualiza" automaticamente o conteúdo filho associado a dados. Nesse contexto, a palavra virtualizar refere-se a uma técnica pela qual um subconjunto dos objetos são gerados de um grande número de itens de dados com base em quais itens estão visíveis na tela. É intensivo, tanto em termos de memória quanto de processador, gerar um grande número de elementos de interface do usuário quando apenas alguns deles podem estar na tela em determinado momento. <xref:System.Windows.Controls.VirtualizingStackPanel> (por meio da funcionalidade fornecida pelo <xref:System.Windows.Controls.VirtualizingPanel>) calcula itens visíveis e trabalha com o <xref:System.Windows.Controls.ItemContainerGenerator> de um <xref:System.Windows.Controls.ItemsControl> (como <xref:System.Windows.Controls.ListBox> ou <xref:System.Windows.Controls.ListView>) para criar apenas elementos para itens visíveis.  
  
 Como uma otimização de desempenho, os objetos visuais para esses itens serão gerados ou mantidos ativos somente se estiverem visíveis na tela. Quando não estão mais na área visível do controle, os objetos visuais podem ser removidos. Isso não deve ser confundido com virtualização de dados, em que os objetos de dados não estão todos presentes na coleção local mas, em vez disso, são transmitidos conforme necessário.  
  
 A tabela a seguir mostra o tempo decorrido adicionando e renderizando 5000 elementos de <xref:System.Windows.Controls.TextBlock> a uma <xref:System.Windows.Controls.StackPanel> e uma <xref:System.Windows.Controls.VirtualizingStackPanel>. Nesse cenário, as medidas representam o tempo entre anexar uma cadeia de caracteres de texto à propriedade <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> de um objeto <xref:System.Windows.Controls.ItemsControl> até a hora em que os elementos do painel exibem a cadeia de texto.  
  
|**Painel de host**|**Tempo de renderização (ms)**|  
|--------------------|----------------------------|  
|<xref:System.Windows.Controls.StackPanel>|3210|  
|<xref:System.Windows.Controls.VirtualizingStackPanel>|46|  
  
## <a name="see-also"></a>Confira também

- [Otimizando o desempenho do aplicativo WPF](optimizing-wpf-application-performance.md)
- [Planejando para desempenho do aplicativo](planning-for-application-performance.md)
- [Aproveitando o hardware](optimizing-performance-taking-advantage-of-hardware.md)
- [Layout e design](optimizing-performance-layout-and-design.md)
- [Elementos gráficos e geração de imagens 2D](optimizing-performance-2d-graphics-and-imaging.md)
- [Recursos do aplicativo](optimizing-performance-application-resources.md)
- [Texto](optimizing-performance-text.md)
- [Associação de dados](optimizing-performance-data-binding.md)
- [Outras recomendações de desempenho](optimizing-performance-other-recommendations.md)
