---
title: Visão geral de modelagem dos dados
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], templates
- binding data [WPF], templates
- templates [WPF], data
- data templates [WPF]
ms.assetid: 0f4d9f8c-0230-4013-bd7b-e8e7fed01b4a
ms.openlocfilehash: 98fff9ba84f386e93549fa94fe84f7b2b0fff5fd
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59097545"
---
# <a name="data-templating-overview"></a>Visão geral de modelagem dos dados
O modelo de modelagem de dados do WPF fornece grande flexibilidade para definir a apresentação dos dados. Os controles do WPF têm uma funcionalidade interna para dar suporte à personalização da apresentação de dados. Primeiro, este tópico demonstra como definir um <xref:System.Windows.DataTemplate> e, em seguida, apresenta outros recursos de modelagem de dados, como a seleção de modelos com base em lógica personalizada e o suporte para a exibição de dados hierárquicos.  
  
<a name="Prerequisites"></a>   
## <a name="prerequisites"></a>Pré-requisitos  
 Este tópico se concentra nos recursos de modelagem de dados e não é uma introdução dos conceitos de associação de dados. Para obter informações sobre conceitos de associação de dados, consulte [Visão geral de associação de dados](data-binding-overview.md).  
  
 <xref:System.Windows.DataTemplate> é sobre a apresentação de dados e é um dos muitos recursos fornecidos pelo modelo de estilo e modelagem do WPF. Para obter uma introdução do WPF estilo e modelagem de modelo, por exemplo, como usar um <xref:System.Windows.Style> para definir propriedades em controles, consulte a [Styling and Templating](../controls/styling-and-templating.md) tópico.  
  
 Além disso, é importante entender `Resources`, que são, essencialmente, o que permite que objetos como <xref:System.Windows.Style> e <xref:System.Windows.DataTemplate> a ser reutilizáveis. Para obter mais informações sobre recursos, consulte [Recursos de XAML](../advanced/xaml-resources.md).  
  
<a name="DataTemplating_Basic"></a>   
## <a name="data-templating-basics"></a>Noções básicas de modelagem de dados  
  
 Para demonstrar por que <xref:System.Windows.DataTemplate> é importante, vamos examinar um exemplo de associação de dados. Neste exemplo, temos uma <xref:System.Windows.Controls.ListBox> que está associado a uma lista de `Task` objetos. Cada objeto `Task` tem um `TaskName` (cadeia de caracteres), um `Description` (cadeia de caracteres), um `Priority` (int) e uma propriedade do tipo `TaskType`, que é um `Enum` com os valores `Home` e `Work`.  
  
 [!code-xaml[DataTemplatingIntro_snip#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#resources)]  
[!code-xaml[DataTemplatingIntro_snip#UI1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#ui1)]  
[!code-xaml[DataTemplatingIntro_snip#UI2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#ui2)]  
  
<a name="without_a_datatemplate"></a>   
### <a name="without-a-datatemplate"></a>Sem um DataTemplate  
 Sem um <xref:System.Windows.DataTemplate>, nossa <xref:System.Windows.Controls.ListBox> atualmente é semelhante a esta:  
  
 ![Captura de tela de exemplo dados templating](./media/datatemplatingintro-fig1.png "DataTemplatingIntro_fig1")  
  
 O que acontece é que, sem instruções específicas, o <xref:System.Windows.Controls.ListBox> por padrão chama `ToString` ao tentar exibir os objetos na coleção. Portanto, se o `Task` substituições do objeto de `ToString` método, então o <xref:System.Windows.Controls.ListBox> exibe a representação de cadeia de caracteres de cada objeto de origem na coleção subjacente.  
  
 Por exemplo, se a classe `Task` substituir o método `ToString` dessa maneira, em que `name` é o campo para a propriedade `TaskName`:  
  
 [!code-csharp[DataTemplatingIntro_snip#ToString](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Data.cs#tostring)]
 [!code-vb[DataTemplatingIntro_snip#ToString](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataTemplatingIntro_snip/visualbasic/data.vb#tostring)]  
  
 Em seguida, a <xref:System.Windows.Controls.ListBox> é semelhante ao seguinte:  
  
 ![Captura de tela de exemplo dados templating](./media/datatemplatingintro-fig2.png "DataTemplatingIntro_fig2")  
  
 No entanto, isso é inflexível e limitante. Além disso, se você estivesse associando a dados [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)], não poderia substituir `ToString`.  
  
<a name="defining_simple_datatemplate"></a>   
### <a name="defining-a-simple-datatemplate"></a>Definindo um DataTemplate simples  
 A solução é definir um <xref:System.Windows.DataTemplate>. Uma maneira de fazer isso é definir a <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> propriedade do <xref:System.Windows.Controls.ListBox> para um <xref:System.Windows.DataTemplate>. O que você especifica no seu <xref:System.Windows.DataTemplate> torna-se a estrutura visual do seu objeto de dados. O seguinte <xref:System.Windows.DataTemplate> é bastante simples. Estamos fornecendo instruções para que cada item seja exibido como três <xref:System.Windows.Controls.TextBlock> elementos dentro de um <xref:System.Windows.Controls.StackPanel>. Cada <xref:System.Windows.Controls.TextBlock> elemento está associado a uma propriedade do `Task` classe.  
  
 [!code-xaml[DataTemplatingIntro_snip#Inline](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#inline)]  
  
 Os dados subjacentes para os exemplos neste tópico são uma coleção de objetos [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]. Se você estiver associando a dados [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)], os conceitos fundamentais serão os mesmos, mas haverá uma pequena diferença sintática. Por exemplo, em vez de precisar `Path=TaskName`, você definiria <xref:System.Windows.Data.Binding.XPath%2A> à `@TaskName` (se `TaskName` é um atributo do seu [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] nó).  
  
 Agora nosso <xref:System.Windows.Controls.ListBox> é semelhante ao seguinte:  
  
 ![Captura de tela de exemplo dados templating](./media/datatemplatingintro-fig3.png "DataTemplatingIntro_fig3")  
  
<a name="defining_datatemplate_as_a_resource"></a>   
### <a name="creating-the-datatemplate-as-a-resource"></a>Criando o DataTemplate como um recurso  
 No exemplo acima, definimos o <xref:System.Windows.DataTemplate> embutido. É mais comum defini-lo na seção de recursos para que possa ser um objeto reutilizável, como no exemplo a seguir:  
  
 [!code-xaml[DataTemplatingIntro_snip#R1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r1)]  
[!code-xaml[DataTemplatingIntro_snip#AsResource](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#asresource)]  
[!code-xaml[DataTemplatingIntro_snip#R2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r2)]  
  
 Agora, é possível usar o `myTaskTemplate` como recurso, como no exemplo a seguir:  
  
 [!code-xaml[DataTemplatingIntro_snip#MyTaskTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#mytasktemplate)]  
  
 Porque `myTaskTemplate` é um recurso, agora você pode usá-lo em outros controles que têm uma propriedade que utiliza um <xref:System.Windows.DataTemplate> tipo. Conforme mostrado acima, para <xref:System.Windows.Controls.ItemsControl> objetos, como o <xref:System.Windows.Controls.ListBox>, é o <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> propriedade. Para <xref:System.Windows.Controls.ContentControl> objetos, é o <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> propriedade.  
  
<a name="Styling_DataType"></a>   
### <a name="the-datatype-property"></a>A propriedade DataType  
 O <xref:System.Windows.DataTemplate> classe tem um <xref:System.Windows.DataTemplate.DataType%2A> propriedade que é muito semelhante ao <xref:System.Windows.Style.TargetType%2A> propriedade do <xref:System.Windows.Style> classe. Portanto, em vez de especificar uma `x:Key` para o <xref:System.Windows.DataTemplate> no exemplo acima, você pode fazer o seguinte:  
  
 [!code-xaml[DataTemplatingIntro_snip#DataType](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#datatype)]  
  
 Isso <xref:System.Windows.DataTemplate> é aplicado automaticamente a todos os `Task` objetos. Observe que, nesse caso, o `x:Key` é definido implicitamente. Portanto, se você atribuir a esse <xref:System.Windows.DataTemplate> uma `x:Key` valor, você está substituindo implícito `x:Key` e o <xref:System.Windows.DataTemplate> não será aplicado automaticamente.  
  
 Se você estiver associando um <xref:System.Windows.Controls.ContentControl> a uma coleção de `Task` objetos, o <xref:System.Windows.Controls.ContentControl> não usa as opções acima <xref:System.Windows.DataTemplate> automaticamente. Isso ocorre porque a associação em um <xref:System.Windows.Controls.ContentControl> precisa de mais informações para distinguir se você deseja associar a uma coleção inteira ou os objetos individuais. Se sua <xref:System.Windows.Controls.ContentControl> está acompanhando a seleção de um <xref:System.Windows.Controls.ItemsControl> tipo, você pode definir o <xref:System.Windows.Data.Binding.Path%2A> propriedade do <xref:System.Windows.Controls.ContentControl> associando a "`/`" para indicar que você está interessado no item atual. Para ver um exemplo, consulte [Como associar a uma coleção e exibir informações com base na seleção](how-to-bind-to-a-collection-and-display-information-based-on-selection.md). Caso contrário, você precisará especificar o <xref:System.Windows.DataTemplate> explicitamente, definindo o <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> propriedade.  
  
 O <xref:System.Windows.DataTemplate.DataType%2A> propriedade é particularmente útil quando você tem um <xref:System.Windows.Data.CompositeCollection> de diferentes tipos de objetos de dados. Para ver um exemplo, consulte [Implementar um CompositeCollection](how-to-implement-a-compositecollection.md).  
  
<a name="adding_more_to_datatemplate"></a>   
## <a name="adding-more-to-the-datatemplate"></a>Adicionando mais ao DataTemplate  
 Os dados aparecem com as informações necessárias no momento, mas, sem dúvida, há espaço para melhoria. Vamos melhorar a apresentação adicionando um <xref:System.Windows.Controls.Border>, um <xref:System.Windows.Controls.Grid>e alguns <xref:System.Windows.Controls.TextBlock> elementos que descrevem os dados que está sendo exibidos.  
  
 [!code-xaml[DataTemplatingIntro#AddingMore](~/samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#addingmore)]  
[!code-xaml[DataTemplatingIntro#AddingMore2](~/samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#addingmore2)]  
  
 A captura de tela a seguir mostra a <xref:System.Windows.Controls.ListBox> com essa modificação <xref:System.Windows.DataTemplate>:  
  
 ![Captura de tela de exemplo dados templating](./media/datatemplatingintro-fig4.png "DataTemplatingIntro_fig4")  
  
 Podemos definir <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> ao <xref:System.Windows.HorizontalAlignment.Stretch> sobre o <xref:System.Windows.Controls.ListBox> para garantir que a largura dos itens ocupa todo o espaço:  
  
 [!code-xaml[DataTemplatingIntro_snip#Stretch](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#stretch)]  
  
 Com o <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> propriedade definida como <xref:System.Windows.HorizontalAlignment.Stretch>, o <xref:System.Windows.Controls.ListBox> agora se parece com isto:  
  
 ![Captura de tela de exemplo dados templating](./media/datatemplatingintro-fig5.png "DataTemplatingIntro_fig5")  
  
<a name="DataTrigger_to_Apply_Property_Values"></a>   
### <a name="use-datatriggers-to-apply-property-values"></a>Usar DataTriggers para aplicar valores da propriedade  
 A apresentação atual não nos informa se uma `Task` é uma tarefa de casa ou uma tarefa de escritório. Lembre-se de que o objeto `Task` tem uma propriedade `TaskType` do tipo `TaskType`, que é uma enumeração com os valores `Home` e `Work`.  
  
 No exemplo a seguir, o <xref:System.Windows.DataTrigger> define o <xref:System.Windows.Controls.Border.BorderBrush%2A> do elemento denominado `border` à `Yellow` se o `TaskType` é de propriedade `TaskType.Home`.  
  
 [!code-xaml[DataTemplatingIntro#DT](~/samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#dt)]  
[!code-xaml[DataTemplatingIntro#DataTrigger](~/samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#datatrigger)]  
[!code-xaml[DataTemplatingIntro#AddingMore2](~/samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#addingmore2)]  
  
 Agora, nosso aplicativo tem a seguinte aparência. As tarefas de casa são exibidas com uma borda amarela, enquanto as tarefas de escritório aparecem com uma borda verde-azulada:  
  
 ![Captura de tela de exemplo dados templating](./media/datatemplatingintro-fig6.png "DataTemplatingIntro_fig6")  
  
 Neste exemplo o <xref:System.Windows.DataTrigger> usa um <xref:System.Windows.Setter> para definir um valor de propriedade. As classes de gatilho também têm o <xref:System.Windows.TriggerBase.EnterActions%2A> e <xref:System.Windows.TriggerBase.ExitActions%2A> propriedades que permitem que você inicie um conjunto de ações como animações. Além disso, há também um <xref:System.Windows.MultiDataTrigger> classe que permite que você aplique as alterações com base em vários valores de propriedade de associação de dados.  
  
 Uma maneira alternativa de obter o mesmo efeito é associar o <xref:System.Windows.Controls.Border.BorderBrush%2A> propriedade para o `TaskType` propriedade e usar um conversor de valor para retornar a cor com base no `TaskType` valor. Criar o efeito acima usando um conversor é um pouco mais eficiente em termos de desempenho. Além disso, a criação do seu próprio conversor oferece mais flexibilidade, pois você fornecerá sua própria lógica. Por fim, a técnica escolhida depende do seu cenário e da sua preferência. Para obter informações sobre como escrever um conversor, consulte <xref:System.Windows.Data.IValueConverter>.  
  
<a name="what_belongs_in_datatemplate"></a>   
### <a name="what-belongs-in-a-datatemplate"></a>O que pertence a um DataTemplate?  

No exemplo anterior, colocamos o gatilho dentro do <xref:System.Windows.DataTemplate> usando o <xref:System.Windows.DataTemplate>.<xref:System.Windows.DataTemplate.Triggers%2A> propriedade. O <xref:System.Windows.Setter> do gatilho define o valor de uma propriedade de um elemento (o <xref:System.Windows.Controls.Border> elemento) que está dentro do <xref:System.Windows.DataTemplate>. No entanto, se as propriedades que seu `Setters` estão preocupados com não são propriedades de elementos que estão dentro do atual <xref:System.Windows.DataTemplate>, talvez seja mais adequado definir as propriedades usando uma <xref:System.Windows.Style> que é para o <xref:System.Windows.Controls.ListBoxItem> classe (se a Você está associando o controle é um <xref:System.Windows.Controls.ListBox>). Por exemplo, se você quiser que seu <xref:System.Windows.Trigger> animar o <xref:System.Windows.UIElement.Opacity%2A> valor do item quando um mouse aponta para um item, você pode definir gatilhos dentro de um <xref:System.Windows.Controls.ListBoxItem> estilo. Para ver um exemplo, consulte a [Amostra de introdução a estilo e modelagem](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).
  
 Em geral, tenha em mente que o <xref:System.Windows.DataTemplate> está sendo aplicada a cada um dos gerado <xref:System.Windows.Controls.ListBoxItem> (para obter mais informações sobre como e onde ele realmente é aplicado, consulte o <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> página.). Seu <xref:System.Windows.DataTemplate> se preocupa com apenas a apresentação e a aparência dos objetos de dados. Na maioria dos casos, todos os outros aspectos da apresentação, como a aparência de um item é semelhante quando ele é selecionado ou como o <xref:System.Windows.Controls.ListBox> dispõe os itens, não pertencem a definição de um <xref:System.Windows.DataTemplate>. Para ver um exemplo, consulte a seção [Estilo e modelagem de um ItemsControl](#DataTemplating_ItemsControl).  
  
<a name="Styling_StyleSelection"></a>   
## <a name="choosing-a-datatemplate-based-on-properties-of-the-data-object"></a>Escolhendo um DataTemplate com base nas propriedades do objeto de dados  
 Na seção [A propriedade DataType](#Styling_DataType), falamos que é possível definir diferentes modelos de dados para diferentes objetos de dados. Isso é especialmente útil quando você tem um <xref:System.Windows.Data.CompositeCollection> de diferentes tipos ou coleções com itens de diferentes tipos. No [Usar DataTriggers para aplicar valores da propriedade](#DataTrigger_to_Apply_Property_Values) seção, mostramos que se você tiver uma coleção do mesmo tipo de objetos de dados você pode criar um <xref:System.Windows.DataTemplate> e, em seguida, usar gatilhos para aplicar as alterações com base nos valores de propriedade cada objeto de dados. Contudo, os gatilhos permitem aplicar valores da propriedade ou iniciar animações, mas não proporcionam flexibilidade para reconstruir a estrutura dos seus objetos de dados. Alguns cenários podem exigir que você crie outro <xref:System.Windows.DataTemplate> para dados de objetos que são do mesmo tipo, mas têm propriedades diferentes.  
  
 Por exemplo, se um objeto `Task` tiver um valor `Priority` de `1`, talvez você queira lhe conferir uma aparência completamente diferente para funcionar como um alerta para si mesmo. Nesse caso, você cria um <xref:System.Windows.DataTemplate> para a exibição de alta prioridade `Task` objetos. Vamos adicionar o seguinte <xref:System.Windows.DataTemplate> à seção de recursos:  
  
 [!code-xaml[DataTemplatingIntro_snip#ImportantTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#importanttemplate)]  
  
 Observe que este exemplo usa o <xref:System.Windows.DataTemplate>.<xref:System.Windows.FrameworkTemplate.Resources%2A> propriedade. Os recursos definidos nessa seção são compartilhados pelos elementos dentro de <xref:System.Windows.DataTemplate>.  
  
 Para fornecer a lógica para escolher quais <xref:System.Windows.DataTemplate> usar com base em de `Priority` valor do objeto de dados, criar uma subclasse de <xref:System.Windows.Controls.DataTemplateSelector> e substitua o <xref:System.Windows.Controls.DataTemplateSelector.SelectTemplate%2A> método. No exemplo a seguir, o <xref:System.Windows.Controls.DataTemplateSelector.SelectTemplate%2A> método fornece lógica para retornar o modelo apropriado com base no valor da `Priority` propriedade. O modelo a ser retornado é encontrado nos recursos do envolvente <xref:System.Windows.Window> elemento.  
  
 [!code-csharp[DataTemplatingIntro_snip#DTSClass](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/TaskListDataTemplateSelector.cs#dtsclass)]
 [!code-vb[DataTemplatingIntro_snip#DTSClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataTemplatingIntro_snip/visualbasic/tasklistdatatemplateselector.vb#dtsclass)]  
  
 Em seguida, podemos declarar o `TaskListDataTemplateSelector` como um recurso:  
  
 [!code-xaml[DataTemplatingIntro_snip#R1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r1)]  
[!code-xaml[DataTemplatingIntro_snip#DTS](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#dts)]  
[!code-xaml[DataTemplatingIntro_snip#R2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r2)]  
  
 Para usar o recurso de seletor de modelo, atribua-o para o <xref:System.Windows.Controls.ItemsControl.ItemTemplateSelector%2A> propriedade do <xref:System.Windows.Controls.ListBox>. O <xref:System.Windows.Controls.ListBox> chamadas a <xref:System.Windows.Controls.DataTemplateSelector.SelectTemplate%2A> método o `TaskListDataTemplateSelector` para cada um dos itens na coleção subjacente. A chamada passa o objeto de dados como o parâmetro de item. O <xref:System.Windows.DataTemplate> que é retornado pelo método, em seguida, é aplicado a esse objeto de dados.  
  
 [!code-xaml[DataTemplatingIntro_snip#ItemTemplateSelector](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#itemtemplateselector)]  
  
 Com o seletor de modelo no lugar, o <xref:System.Windows.Controls.ListBox> agora aparece da seguinte maneira:  
  
 ![Captura de tela de exemplo dados templating](./media/datatemplatingintro-fig7.png "DataTemplatingIntro_fig7")  

Isso conclui nossa discussão sobre este exemplo. Para ver a amostra completa, consulte [Amostra da introdução à modelagem de dados](https://github.com/Microsoft/WPF-Samples/tree/master/Data%20Binding/DataTemplatingIntro).

<a name="DataTemplating_ItemsControl"></a>   
## <a name="styling-and-templating-an-itemscontrol"></a>Estilo e modelagem de um ItemsControl  
 Mesmo que o <xref:System.Windows.Controls.ItemsControl> não é o único tipo de controle que você pode usar um <xref:System.Windows.DataTemplate> com, é um cenário muito comum para associar um <xref:System.Windows.Controls.ItemsControl> a uma coleção. No [o que pertence a um DataTemplate](#what_belongs_in_datatemplate) seção, discutimos que a definição de seu <xref:System.Windows.DataTemplate> só deve se preocupar com a apresentação dos dados. Para saber quando não é adequado usar um <xref:System.Windows.DataTemplate> é importante entender as diferentes propriedades de estilo e modelo fornecidas pelo <xref:System.Windows.Controls.ItemsControl>. O exemplo a seguir foi desenvolvido para ilustrar a função de cada uma dessas propriedades. O <xref:System.Windows.Controls.ItemsControl> neste exemplo é associada à mesma `Tasks` coleção do exemplo anterior. Para fins de demonstração, os estilos e modelos deste exemplo são declarados como embutidos.  
  
 [!code-xaml[DataTemplatingIntro_snip#ItemsControlProperties](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#itemscontrolproperties)]  
  
 Segue uma captura de tela do exemplo quando é renderizado:  
  
 ![Captura de tela do exemplo de ItemsControl](./media/databinding-itemscontrolproperties.png "DataBinding_ItemsControlProperties")  
  
 Observe que, em vez de usar o <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>, você pode usar o <xref:System.Windows.Controls.ItemsControl.ItemTemplateSelector%2A>. Consulte a seção anterior para ver um exemplo. Da mesma forma, em vez de usar o <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>, você tem a opção de usar o <xref:System.Windows.Controls.ItemsControl.ItemContainerStyleSelector%2A>.  
  
 Duas outras propriedades relacionadas ao estilo do <xref:System.Windows.Controls.ItemsControl> que não são mostrados aqui estão <xref:System.Windows.Controls.ItemsControl.GroupStyle%2A> e <xref:System.Windows.Controls.ItemsControl.GroupStyleSelector%2A>.  
  
<a name="DataTemplating_HeirarchicalDataTemplate"></a>   
## <a name="support-for-hierarchical-data"></a>Suporte para dados hierárquicos  
 Até o momento, examinamos apenas como associar a uma única coleção e exibi-la. Às vezes, você tem uma coleção que contém outras coleções. O <xref:System.Windows.HierarchicalDataTemplate> classe é projetada para ser usado com <xref:System.Windows.Controls.HeaderedItemsControl> tipos para exibir tais dados. No exemplo a seguir, `ListLeagueList` é uma lista de objetos `League`. Cada objeto `League` tem um `Name` e uma coleção de objetos `Division`. Cada `Division` tem um `Name` e uma coleção de objetos `Team`; cada objeto `Team` tem um `Name`.  
  
 [!code-xaml[HierarchicalDataTemplateSnippet#HDT](~/samples/snippets/csharp/VS_Snippets_Wpf/HierarchicalDataTemplateSnippet/CS/window1.xaml#hdt)]  
  
 O exemplo mostra que, com o uso de <xref:System.Windows.HierarchicalDataTemplate>, você pode facilmente exibir dados de lista que contém outras listas. Segue uma captura de tela do exemplo.  
  
 ![Captura de tela de amostra de HierarchicalDataTemplate](./media/databinding-hierarchicaldatatemplate.png "DataBinding_HierarchicalDataTemplate")  
  
## <a name="see-also"></a>Consulte também

- [Associação de dados](../advanced/optimizing-performance-data-binding.md)
- [Localizar elementos gerados por DataTemplate](how-to-find-datatemplate-generated-elements.md)
- [Estilo e modelagem](../controls/styling-and-templating.md)
- [Visão geral da vinculação de dados](data-binding-overview.md)
- [Visão geral dos estilos e dos modelos de cabeçalho da coluna GridView](../controls/gridview-column-header-styles-and-templates-overview.md)
