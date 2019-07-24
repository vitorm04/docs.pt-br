---
title: 'Otimizando o desempenho: Comportamento do objeto'
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
ms.openlocfilehash: 025c8691eb1aaf9483a222530a5590670ede486b
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68400471"
---
# <a name="optimizing-performance-object-behavior"></a>Otimizando o desempenho: Comportamento do objeto
O entendimento do comportamento intrínseco de objetos [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ajudará você a fazer o balanceamento correto entre desempenho e funcionalidade.  

<a name="Not_Removing_Event_Handlers"></a>   
## <a name="not-removing-event-handlers-on-objects-may-keep-objects-alive"></a>Não remover manipuladores de eventos em objetos poderá manter os objetos ativos  
 O delegado que um objeto passa para seu evento é, efetivamente, uma referência a esse objeto. Portanto, os manipuladores de eventos podem manter objetos ativos por mais tempo que o esperado. Ao realizar a limpeza de um objeto que tenha sido registrado para escutar um evento de objeto, é essencial remover esse delegado antes de liberar o objeto. Manter objetos desnecessários ativos aumenta o uso de memória do aplicativo. Isso é especialmente verdadeiro quando o objeto é a raiz de uma árvore lógica ou de uma árvore visual.  
  
 O [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] apresenta um padrão fraco de ouvinte de eventos para eventos que podem ser úteis em situações em que as relações de tempo de vida do objeto, entre a origem e o ouvinte, são difíceis de controlar. Alguns eventos do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] existentes usam esse padrão. Se estiver implementando objetos com eventos personalizados, esse padrão poderá ser útil para você. Para obter detalhes, consulte [Padrões de evento fracos](weak-event-patterns.md).  
  
 Há várias ferramentas, como o Criador de Perfil CLR e o Visualizador de Conjunto de Trabalho, que podem fornecer informações sobre o uso de memória de um processo especificado. O Criador de Perfil CLR inclui várias exibições muito úteis do perfil de alocação, incluindo um histograma de tipos alocados, grafos de alocação e de chamadas, uma linha do tempo mostrando coletas de lixo de várias gerações e o estado resultante do heap gerenciado após essas coletas, além de uma árvore de chamadas mostrando as cargas de assembly e alocações por método. Para obter mais informações, consulte [Centro de desenvolvedores do .NET Framework](https://go.microsoft.com/fwlink/?LinkId=117435).  
  
<a name="DPs_and_Objects"></a>   
## <a name="dependency-properties-and-objects"></a>Propriedades de dependência e objetos  
 Em geral, o acesso a uma propriedade de <xref:System.Windows.DependencyObject> dependência de um não é mais lento do que acessar uma propriedade CLR. Embora haja uma pequena sobrecarga de desempenho para definir um valor de propriedade, obter um valor é tão rápido quanto obter o valor de uma propriedade CLR. O fato de as propriedades de dependência darem suporte a recursos robustos, como vinculação de dados, animação, herança e estilos é a compensação pela pequena sobrecarga de desempenho. Para obter mais informações, consulte [Visão geral sobre propriedades de dependência](dependency-properties-overview.md).  
  
### <a name="dependencyproperty-optimizations"></a>Otimizações de DependencyProperty  
 Você deve definir as propriedades de dependência em seu aplicativo com muito cuidado. Se o <xref:System.Windows.DependencyProperty> afetar apenas as opções de metadados do tipo de renderização, em vez de <xref:System.Windows.FrameworkPropertyMetadata.AffectsMeasure%2A>outras opções de metadados, como, você deve marcá-lo como tal, substituindo seus metadados. Para obter mais informações sobre como substituir ou obter metadados de propriedades, consulte [Metadados de propriedades de dependência](dependency-property-metadata.md).  
  
 Talvez seja mais eficiente fazer com que um manipulador de alterações de propriedade invalide as passagens de medida, organização e renderização manualmente se nem todas as alterações de propriedade afetarem, na verdade, a medida, a organização e a renderização. Por exemplo, você pode decidir renderizar novamente uma tela de fundo apenas quando um valor for maior que um limite definido. Nesse caso, seu manipulador de alteração de propriedade só invalidaria a renderização quando o valor excedesse o limite definido.  
  
### <a name="making-a-dependencyproperty-inheritable-is-not-free"></a>Há consequências em tornar uma DependencyProperty herdável  
 Por padrão, as propriedades de dependência registradas são não herdáveis. No entanto, você pode explicitamente tornar qualquer propriedade herdável. Embora esse seja um recurso útil, converter uma propriedade para se tornar herdável afeta o desempenho, aumentando o período de tempo para a invalidação da propriedade.  
  
### <a name="use-registerclasshandler-carefully"></a>Usar o RegisterClassHandler com cuidado  
 Embora a <xref:System.Windows.EventManager.RegisterClassHandler%2A> chamada permita que você salve o estado da instância, é importante estar ciente de que o manipulador é chamado em cada instância, o que pode causar problemas de desempenho. Use <xref:System.Windows.EventManager.RegisterClassHandler%2A> somente quando seu aplicativo exigir que você salve o estado da instância.  
  
### <a name="set-the-default-value-for-a-dependencyproperty-during-registration"></a>Definir o valor padrão para uma DependencyProperty durante o registro  
 Ao criar um <xref:System.Windows.DependencyProperty> que exija um valor padrão, defina o valor usando os metadados padrão passados como um parâmetro para o <xref:System.Windows.DependencyProperty.Register%2A> método do <xref:System.Windows.DependencyProperty>. Use esta técnica em vez de configurar o valor da propriedade em um construtor ou em cada instância de um elemento.  
  
### <a name="set-the-propertymetadata-value-using-register"></a>Definir o valor de PropertyMetadata usando o registro  
 Ao criar um <xref:System.Windows.DependencyProperty>, você tem a opção de definir o <xref:System.Windows.PropertyMetadata> usando os <xref:System.Windows.DependencyProperty.Register%2A> métodos ou <xref:System.Windows.DependencyProperty.OverrideMetadata%2A> . Embora seu objeto possa ter um construtor estático para chamar <xref:System.Windows.DependencyProperty.OverrideMetadata%2A>, essa não é a solução ideal e afetará o desempenho. Para obter o melhor desempenho, <xref:System.Windows.PropertyMetadata> defina o durante a <xref:System.Windows.DependencyProperty.Register%2A>chamada para.  
  
<a name="Freezable_Objects"></a>   
## <a name="freezable-objects"></a>Objetos congeláveis  
 Um <xref:System.Windows.Freezable> é um tipo especial de objeto que tem dois Estados: descongelado e congelado. Congelar objetos sempre que possível melhora o desempenho do seu aplicativo e reduz seu conjunto de trabalho. Para obter mais informações, consulte a [Visão geral de objetos congeláveis](freezable-objects-overview.md).  
  
 Cada <xref:System.Windows.Freezable> um tem <xref:System.Windows.Freezable.Changed> um evento que é gerado sempre que é alterado. No entanto, as notificações de alteração são dispendiosas em termos de desempenho do aplicativo.  
  
 Considere o exemplo a seguir no qual <xref:System.Windows.Shapes.Rectangle> cada um usa <xref:System.Windows.Media.Brush> o mesmo objeto:  
  
 [!code-csharp[Performance#PerformanceSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet2)]
 [!code-vb[Performance#PerformanceSnippet2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet2)]  
  
 Por padrão, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] o fornece um manipulador de eventos <xref:System.Windows.Media.SolidColorBrush> para o <xref:System.Windows.Freezable.Changed> evento do objeto a fim de invalidar <xref:System.Windows.Shapes.Rectangle> a propriedade <xref:System.Windows.Shapes.Shape.Fill%2A> do objeto. Nesse caso, cada vez que o <xref:System.Windows.Media.SolidColorBrush> tem que disparar seu <xref:System.Windows.Freezable.Changed> evento, é necessário invocar a função de retorno de <xref:System.Windows.Shapes.Rectangle>chamada para cada um — o acúmulo dessas invocações de função de retorno de chamada impõe uma penalidade de desempenho significativa. Além disso, adicionar e remover manipuladores neste ponto exigiria muito do desempenho, já que o aplicativo teria que percorrer toda a lista para fazer isso. Se o cenário do aplicativo nunca alterar <xref:System.Windows.Media.SolidColorBrush>o, você pagará o custo de manter <xref:System.Windows.Freezable.Changed> os manipuladores de eventos desnecessariamente.  
  
 Congelar um <xref:System.Windows.Freezable> pode melhorar seu desempenho, pois ele não precisa mais gastar recursos para manter notificações de alteração. A tabela a seguir mostra o tamanho de um <xref:System.Windows.Media.SolidColorBrush> simples quando <xref:System.Windows.Freezable.IsFrozen%2A> sua propriedade é definida `true`como, em comparação com quando não é. Isso pressupõe a aplicação de um pincel <xref:System.Windows.Shapes.Shape.Fill%2A> à propriedade de <xref:System.Windows.Shapes.Rectangle> dez objetos.  
  
|**Estado**|**Size**|  
|---------------|--------------|  
|Daquela<xref:System.Windows.Media.SolidColorBrush>|212 bytes|  
|Não congelado<xref:System.Windows.Media.SolidColorBrush>|972 bytes|  
  
 O exemplo de código a seguir demonstra esse conceito:  
  
 [!code-csharp[Performance#PerformanceSnippet3](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet3)]
 [!code-vb[Performance#PerformanceSnippet3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet3)]  
  
### <a name="changed-handlers-on-unfrozen-freezables-may-keep-objects-alive"></a>Manipuladores alterados em Congeláveis descongelados podem manter objetos ativos  
 O delegado que um objeto passa para o <xref:System.Windows.Freezable> evento de <xref:System.Windows.Freezable.Changed> um objeto é efetivamente uma referência a esse objeto. Portanto, <xref:System.Windows.Freezable.Changed> os manipuladores de eventos podem manter os objetos ativos por mais tempo do que o esperado. Ao executar a limpeza de um objeto que foi registrado para escutar o <xref:System.Windows.Freezable> <xref:System.Windows.Freezable.Changed> evento de um objeto, é essencial remover esse delegado antes de liberar o objeto.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]também conecta <xref:System.Windows.Freezable.Changed> eventos internamente. Por exemplo, todas as propriedades de dependência <xref:System.Windows.Freezable> que assumem como um valor <xref:System.Windows.Freezable.Changed> escutarão eventos automaticamente. A <xref:System.Windows.Shapes.Shape.Fill%2A> Propriedade, que usa um <xref:System.Windows.Media.Brush>, ilustra esse conceito.  
  
 [!code-csharp[Performance#PerformanceSnippet4](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet4)]
 [!code-vb[Performance#PerformanceSnippet4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet4)]  
  
 Na `myBrush` atribuição de <xref:System.Windows.Freezable.Changed> para `myRectangle.Fill`, um delegado apontando de volta para o <xref:System.Windows.Shapes.Rectangle> objeto será adicionado ao <xref:System.Windows.Media.SolidColorBrush> evento do objeto. Isso significa que o código a seguir, na verdade, não torna o `myRect` qualificado para a coleta de lixo:  
  
 [!code-csharp[Performance#PerformanceSnippet5](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet5)]
 [!code-vb[Performance#PerformanceSnippet5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet5)]  
  
 Nesse caso `myBrush` , ainda está se `myRectangle` mantendo ativa e irá chamá-la de volta quando ele <xref:System.Windows.Freezable.Changed> acionar seu evento. `myBrush` Observe que a atribuição <xref:System.Windows.Shapes.Shape.Fill%2A> à propriedade de um novo <xref:System.Windows.Shapes.Rectangle> irá simplesmente adicionar outro manipulador de eventos a `myBrush`.  
  
 A maneira recomendada para limpar esses tipos de objetos é remover o <xref:System.Windows.Media.Brush> <xref:System.Windows.Shapes.Shape.Fill%2A> da propriedade, o que, por sua vez, removerá <xref:System.Windows.Freezable.Changed> o manipulador de eventos.  
  
 [!code-csharp[Performance#PerformanceSnippet6](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet6)]
 [!code-vb[Performance#PerformanceSnippet6](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet6)]  
  
<a name="User_Interface_Virtualization"></a>   
## <a name="user-interface-virtualization"></a>Virtualização da interface do usuário  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]também fornece uma variação do elemento <xref:System.Windows.Controls.StackPanel> que "virtualiza" automaticamente o conteúdo filho associado a dados. Nesse contexto, a palavra virtualizar refere-se a uma técnica pela qual um subconjunto dos objetos são gerados de um grande número de itens de dados com base em quais itens estão visíveis na tela. É intensivo, tanto em termos de memória quanto de processador, gerar um grande número de elementos de interface do usuário quando apenas alguns podem estar na tela em um determinado momento. <xref:System.Windows.Controls.VirtualizingStackPanel>(por meio da <xref:System.Windows.Controls.VirtualizingPanel> <xref:System.Windows.Controls.ItemsControl> <xref:System.Windows.Controls.ListView> <xref:System.Windows.Controls.ItemContainerGenerator> funcionalidadefornecidapor)calculaositensvisíveisetrabalhacomodeum(comoou)paracriarapenaselementosparaitensvisíveis.<xref:System.Windows.Controls.ListBox>  
  
 Como uma otimização de desempenho, os objetos visuais para esses itens serão gerados ou mantidos ativos somente se estiverem visíveis na tela. Quando não estão mais na área visível do controle, os objetos visuais podem ser removidos. Isso não deve ser confundido com virtualização de dados, em que os objetos de dados não estão todos presentes na coleção local mas, em vez disso, são transmitidos conforme necessário.  
  
 A tabela a seguir mostra o tempo decorrido adicionando e renderizando 5000 <xref:System.Windows.Controls.TextBlock> elementos <xref:System.Windows.Controls.StackPanel> a a e a. <xref:System.Windows.Controls.VirtualizingStackPanel> Nesse cenário, as medidas representam o tempo entre anexar uma cadeia de caracteres de texto <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> à propriedade de <xref:System.Windows.Controls.ItemsControl> um objeto até a hora em que os elementos do painel exibem a cadeia de texto.  
  
|**Painel de host**|**Tempo de renderização (ms)**|  
|--------------------|----------------------------|  
|<xref:System.Windows.Controls.StackPanel>|3210|  
|<xref:System.Windows.Controls.VirtualizingStackPanel>|46|  
  
## <a name="see-also"></a>Consulte também

- [Otimizando o desempenho do aplicativo WPF](optimizing-wpf-application-performance.md)
- [Planejando para desempenho do aplicativo](planning-for-application-performance.md)
- [Aproveitando o hardware](optimizing-performance-taking-advantage-of-hardware.md)
- [Layout e design](optimizing-performance-layout-and-design.md)
- [Elementos gráficos e geração de imagens 2D](optimizing-performance-2d-graphics-and-imaging.md)
- [Recursos do aplicativo](optimizing-performance-application-resources.md)
- [Texto](optimizing-performance-text.md)
- [Associação de dados](optimizing-performance-data-binding.md)
- [Outras recomendações de desempenho](optimizing-performance-other-recommendations.md)
