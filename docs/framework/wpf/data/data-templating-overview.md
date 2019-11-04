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
ms.openlocfilehash: d088342a08076c69b34f6c3d39dce076cb3890d4
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460039"
---
# <a name="data-templating-overview"></a>Visão geral de modelagem dos dados
O modelo de modelagem de dados do WPF fornece grande flexibilidade para definir a apresentação dos dados. Os controles do WPF têm uma funcionalidade interna para dar suporte à personalização da apresentação de dados. Este tópico primeiro demonstra como definir um <xref:System.Windows.DataTemplate> e, em seguida, apresenta outros recursos de modelagem de dados, como a seleção de modelos com base na lógica personalizada e o suporte para a exibição de dados hierárquicos.  
  
<a name="Prerequisites"></a>   
## <a name="prerequisites"></a>Prerequisites  
 Este tópico se concentra nos recursos de modelagem de dados e não é uma introdução dos conceitos de associação de dados. Para obter informações sobre conceitos de associação de dados, consulte [Visão geral de associação de dados](../../../desktop-wpf/data/data-binding-overview.md).  
  
 <xref:System.Windows.DataTemplate> é sobre a apresentação de dados e é um dos muitos recursos fornecidos pelo modelo de modelagem e estilo do WPF. Para obter uma introdução do modelo de modelagem e estilo do WPF, como usar um <xref:System.Windows.Style> para definir propriedades em controles, consulte o tópico [estilo e modelagem](../controls/styling-and-templating.md) .  
  
 Além disso, é importante entender `Resources`, que são essencialmente o que permite que objetos como <xref:System.Windows.Style> e <xref:System.Windows.DataTemplate> sejam reutilizáveis. Para obter mais informações sobre recursos, consulte [Recursos de XAML](../advanced/xaml-resources.md).  
  
<a name="DataTemplating_Basic"></a>   
## <a name="data-templating-basics"></a>Noções básicas de modelagem de dados  
  
 Para demonstrar por que <xref:System.Windows.DataTemplate> é importante, vamos examinar um exemplo de associação de dados. Neste exemplo, temos um <xref:System.Windows.Controls.ListBox> associado a uma lista de objetos `Task`. Cada objeto `Task` tem um `TaskName` (cadeia de caracteres), um `Description` (cadeia de caracteres), um `Priority` (int) e uma propriedade do tipo `TaskType`, que é um `Enum` com os valores `Home` e `Work`.  
  
 [!code-xaml[DataTemplatingIntro_snip#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#resources)]  
[!code-xaml[DataTemplatingIntro_snip#UI1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#ui1)]  
[!code-xaml[DataTemplatingIntro_snip#UI2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#ui2)]  
  
<a name="without_a_datatemplate"></a>   
### <a name="without-a-datatemplate"></a>Sem um DataTemplate  
 Sem um <xref:System.Windows.DataTemplate>, nosso <xref:System.Windows.Controls.ListBox> tem a seguinte aparência:  
  
 ![Captura de tela de exemplo de modelagem de dados](./media/datatemplatingintro-fig1.png "DataTemplatingIntro_fig1")  
  
 O que acontece é que, sem instruções específicas, o <xref:System.Windows.Controls.ListBox> por padrão chama `ToString` ao tentar exibir os objetos na coleção. Portanto, se o objeto `Task` substituir o método `ToString`, o <xref:System.Windows.Controls.ListBox> exibirá a representação de cadeia de caracteres de cada objeto de origem na coleção subjacente.  
  
 Por exemplo, se a classe `Task` substituir o método `ToString` dessa maneira, em que `name` é o campo para a propriedade `TaskName`:  
  
 [!code-csharp[DataTemplatingIntro_snip#ToString](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Data.cs#tostring)]
 [!code-vb[DataTemplatingIntro_snip#ToString](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataTemplatingIntro_snip/visualbasic/data.vb#tostring)]  
  
 Em seguida, o <xref:System.Windows.Controls.ListBox> é semelhante ao seguinte:  
  
 ![Captura de tela de exemplo de modelagem de dados](./media/datatemplatingintro-fig2.png "DataTemplatingIntro_fig2")  
  
 No entanto, isso é inflexível e limitante. Além disso, se você estivesse associando a dados [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)], não poderia substituir `ToString`.  
  
<a name="defining_simple_datatemplate"></a>   
### <a name="defining-a-simple-datatemplate"></a>Definindo um DataTemplate simples  
 A solução é definir um <xref:System.Windows.DataTemplate>. Uma maneira de fazer isso é definir a propriedade <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> do <xref:System.Windows.Controls.ListBox> como uma <xref:System.Windows.DataTemplate>. O que você especificar em seu <xref:System.Windows.DataTemplate> se tornará a estrutura visual do seu objeto de dados. A <xref:System.Windows.DataTemplate> a seguir é bem simples. Estamos dando instruções de que cada item aparece como três elementos <xref:System.Windows.Controls.TextBlock> dentro de um <xref:System.Windows.Controls.StackPanel>. Cada elemento <xref:System.Windows.Controls.TextBlock> é associado a uma propriedade da classe `Task`.  
  
 [!code-xaml[DataTemplatingIntro_snip#Inline](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#inline)]  
  
 Os dados subjacentes para os exemplos neste tópico são uma coleção de objetos CLR. Se você estiver associando a dados [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)], os conceitos fundamentais serão os mesmos, mas haverá uma pequena diferença sintática. Por exemplo, em vez de ter `Path=TaskName`, defina <xref:System.Windows.Data.Binding.XPath%2A> como `@TaskName` (se `TaskName` for um atributo de seu nó de [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]).  
  
 Agora, nosso <xref:System.Windows.Controls.ListBox> é semelhante ao seguinte:  
  
 ![Captura de tela de exemplo de modelagem de dados](./media/datatemplatingintro-fig3.png "DataTemplatingIntro_fig3")  
  
<a name="defining_datatemplate_as_a_resource"></a>   
### <a name="creating-the-datatemplate-as-a-resource"></a>Criando o DataTemplate como um recurso  
 No exemplo acima, definimos o <xref:System.Windows.DataTemplate> embutido. É mais comum defini-lo na seção de recursos para que possa ser um objeto reutilizável, como no exemplo a seguir:  
  
 [!code-xaml[DataTemplatingIntro_snip#R1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r1)]  
[!code-xaml[DataTemplatingIntro_snip#AsResource](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#asresource)]  
[!code-xaml[DataTemplatingIntro_snip#R2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r2)]  
  
 Agora, é possível usar o `myTaskTemplate` como recurso, como no exemplo a seguir:  
  
 [!code-xaml[DataTemplatingIntro_snip#MyTaskTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#mytasktemplate)]  
  
 Como `myTaskTemplate` é um recurso, agora você pode usá-lo em outros controles que têm uma propriedade que usa um tipo <xref:System.Windows.DataTemplate>. Como mostrado acima, para objetos <xref:System.Windows.Controls.ItemsControl>, como o <xref:System.Windows.Controls.ListBox>, é a propriedade <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>. Para objetos <xref:System.Windows.Controls.ContentControl>, é a propriedade <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A>.  
  
<a name="Styling_DataType"></a>   
### <a name="the-datatype-property"></a>A propriedade DataType  
 A classe <xref:System.Windows.DataTemplate> tem uma propriedade <xref:System.Windows.DataTemplate.DataType%2A> que é muito semelhante à propriedade <xref:System.Windows.Style.TargetType%2A> da classe <xref:System.Windows.Style>. Portanto, em vez de especificar um `x:Key` para o <xref:System.Windows.DataTemplate> no exemplo acima, você pode fazer o seguinte:  
  
 [!code-xaml[DataTemplatingIntro_snip#DataType](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#datatype)]  
  
 Essa <xref:System.Windows.DataTemplate> é aplicada automaticamente a todos os objetos de `Task`. Observe que, nesse caso, o `x:Key` é definido implicitamente. Portanto, se você atribuir esse <xref:System.Windows.DataTemplate> um valor de `x:Key`, você está substituindo o `x:Key` implícito e o <xref:System.Windows.DataTemplate> não seria aplicado automaticamente.  
  
 Se você estiver associando um <xref:System.Windows.Controls.ContentControl> a uma coleção de objetos `Task`, o <xref:System.Windows.Controls.ContentControl> não usará o <xref:System.Windows.DataTemplate> acima automaticamente. Isso ocorre porque a associação em uma <xref:System.Windows.Controls.ContentControl> precisa de mais informações para distinguir se você deseja associar a uma coleção inteira ou a objetos individuais. Se o <xref:System.Windows.Controls.ContentControl> estiver rastreando a seleção de um tipo de <xref:System.Windows.Controls.ItemsControl>, você poderá definir a propriedade <xref:System.Windows.Data.Binding.Path%2A> da Associação de <xref:System.Windows.Controls.ContentControl> como "`/`" para indicar que você está interessado no item atual. Para ver um exemplo, consulte [Como associar a uma coleção e exibir informações com base na seleção](how-to-bind-to-a-collection-and-display-information-based-on-selection.md). Caso contrário, você precisa especificar o <xref:System.Windows.DataTemplate> explicitamente definindo a propriedade <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A>.  
  
 A propriedade <xref:System.Windows.DataTemplate.DataType%2A> é particularmente útil quando você tem uma <xref:System.Windows.Data.CompositeCollection> de diferentes tipos de objetos de dados. Para ver um exemplo, consulte [Implementar um CompositeCollection](how-to-implement-a-compositecollection.md).  
  
<a name="adding_more_to_datatemplate"></a>   
## <a name="adding-more-to-the-datatemplate"></a>Adicionando mais ao DataTemplate  
 Os dados aparecem com as informações necessárias no momento, mas, sem dúvida, há espaço para melhoria. Vamos melhorar a apresentação adicionando um <xref:System.Windows.Controls.Border>, um <xref:System.Windows.Controls.Grid>e alguns elementos de <xref:System.Windows.Controls.TextBlock> que descrevem os dados que estão sendo exibidos.  
  
 [!code-xaml[DataTemplatingIntro#AddingMore](~/samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#addingmore)]  
[!code-xaml[DataTemplatingIntro#AddingMore2](~/samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#addingmore2)]  
  
 A captura de tela a seguir mostra a <xref:System.Windows.Controls.ListBox> com esse <xref:System.Windows.DataTemplate>modificado:  
  
 ![Captura de tela de exemplo de modelagem de dados](./media/datatemplatingintro-fig4.png "DataTemplatingIntro_fig4")  
  
 Podemos definir <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> como <xref:System.Windows.HorizontalAlignment.Stretch> no <xref:System.Windows.Controls.ListBox> para ter certeza de que a largura dos itens ocupará todo o espaço:  
  
 [!code-xaml[DataTemplatingIntro_snip#Stretch](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#stretch)]  
  
 Com a propriedade <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> definida como <xref:System.Windows.HorizontalAlignment.Stretch>, o <xref:System.Windows.Controls.ListBox> agora tem esta aparência:  
  
 ![Captura de tela de exemplo de modelagem de dados](./media/datatemplatingintro-fig5.png "DataTemplatingIntro_fig5")  
  
<a name="DataTrigger_to_Apply_Property_Values"></a>   
### <a name="use-datatriggers-to-apply-property-values"></a>Usar DataTriggers para aplicar valores da propriedade  
 A apresentação atual não nos informa se uma `Task` é uma tarefa de casa ou uma tarefa de escritório. Lembre-se de que o objeto `Task` tem uma propriedade `TaskType` do tipo `TaskType`, que é uma enumeração com os valores `Home` e `Work`.  
  
 No exemplo a seguir, o <xref:System.Windows.DataTrigger> define o <xref:System.Windows.Controls.Border.BorderBrush%2A> do elemento chamado `border` como `Yellow` se a propriedade `TaskType` for `TaskType.Home`.  
  
 [!code-xaml[DataTemplatingIntro#DT](~/samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#dt)]  
[!code-xaml[DataTemplatingIntro#DataTrigger](~/samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#datatrigger)]  
[!code-xaml[DataTemplatingIntro#AddingMore2](~/samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#addingmore2)]  
  
 Agora, nosso aplicativo tem a seguinte aparência. As tarefas de casa são exibidas com uma borda amarela, enquanto as tarefas de escritório aparecem com uma borda verde-azulada:  
  
 ![Captura de tela de exemplo de modelagem de dados](./media/datatemplatingintro-fig6.png "DataTemplatingIntro_fig6")  
  
 Neste exemplo, o <xref:System.Windows.DataTrigger> usa uma <xref:System.Windows.Setter> para definir um valor de propriedade. As classes de gatilho também têm as propriedades <xref:System.Windows.TriggerBase.EnterActions%2A> e <xref:System.Windows.TriggerBase.ExitActions%2A> que permitem que você inicie um conjunto de ações, como animações. Além disso, também há uma classe <xref:System.Windows.MultiDataTrigger> que permite aplicar alterações com base em vários valores de propriedade associados a dados.  
  
 Uma maneira alternativa de obter o mesmo efeito é associar a propriedade <xref:System.Windows.Controls.Border.BorderBrush%2A> à propriedade `TaskType` e usar um conversor de valor para retornar a cor com base no valor `TaskType`. Criar o efeito acima usando um conversor é um pouco mais eficiente em termos de desempenho. Além disso, a criação do seu próprio conversor oferece mais flexibilidade, pois você fornecerá sua própria lógica. Por fim, a técnica escolhida depende do seu cenário e da sua preferência. Para obter informações sobre como escrever um conversor, consulte <xref:System.Windows.Data.IValueConverter>.  
  
<a name="what_belongs_in_datatemplate"></a>   
### <a name="what-belongs-in-a-datatemplate"></a>O que pertence a um DataTemplate?  

No exemplo anterior, colocamos o gatilho dentro do <xref:System.Windows.DataTemplate> usando o <xref:System.Windows.DataTemplate>.<xref:System.Windows.DataTemplate.Triggers%2A> property. A <xref:System.Windows.Setter> do gatilho define o valor de uma propriedade de um elemento (o elemento <xref:System.Windows.Controls.Border>) que está dentro do <xref:System.Windows.DataTemplate>. No entanto, se as propriedades às quais seus `Setters` se preocupam não forem Propriedades de elementos que estão dentro do <xref:System.Windows.DataTemplate>atual, talvez seja mais adequado definir as propriedades usando uma <xref:System.Windows.Style> que seja para a classe <xref:System.Windows.Controls.ListBoxItem> (se o controle que você está associando for um <xref:System.Windows.Controls.ListBox>). Por exemplo, se você quiser que o <xref:System.Windows.Trigger> anime o valor de <xref:System.Windows.UIElement.Opacity%2A> do item quando um mouse apontar para um item, você definirá gatilhos dentro de um estilo de <xref:System.Windows.Controls.ListBoxItem>. Para ver um exemplo, consulte a [Amostra de introdução a estilo e modelagem](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).
  
 Em geral, tenha em mente que o <xref:System.Windows.DataTemplate> está sendo aplicado a cada um dos <xref:System.Windows.Controls.ListBoxItem> gerados (para obter mais informações sobre como e onde ele é realmente aplicado, consulte a página <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>). Seu <xref:System.Windows.DataTemplate> se preocupa apenas com a apresentação e a aparência dos objetos de dados. Na maioria dos casos, todos os outros aspectos da apresentação, como a aparência de um item quando ele é selecionado ou como o <xref:System.Windows.Controls.ListBox> apresenta os itens, não pertencem à definição de um <xref:System.Windows.DataTemplate>. Para ver um exemplo, consulte a seção [Estilo e modelagem de um ItemsControl](#DataTemplating_ItemsControl).  
  
<a name="Styling_StyleSelection"></a>   
## <a name="choosing-a-datatemplate-based-on-properties-of-the-data-object"></a>Escolhendo um DataTemplate com base nas propriedades do objeto de dados  
 Na seção [A propriedade DataType](#Styling_DataType), falamos que é possível definir diferentes modelos de dados para diferentes objetos de dados. Isso é especialmente útil quando você tem uma <xref:System.Windows.Data.CompositeCollection> de diferentes tipos ou coleções com itens de tipos diferentes. Na seção [usar gatilhos de dados para aplicar valores de propriedade](#DataTrigger_to_Apply_Property_Values) , mostramos que, se você tiver uma coleção do mesmo tipo de objeto de data, poderá criar um <xref:System.Windows.DataTemplate> e, em seguida, usar gatilhos para aplicar as alterações com base nos valores de propriedade de todos os objetos de dados. Contudo, os gatilhos permitem aplicar valores da propriedade ou iniciar animações, mas não proporcionam flexibilidade para reconstruir a estrutura dos seus objetos de dados. Alguns cenários podem exigir que você crie um <xref:System.Windows.DataTemplate> diferente para objetos de dados do mesmo tipo, mas que têm propriedades diferentes.  
  
 Por exemplo, se um objeto `Task` tiver um valor `Priority` de `1`, talvez você queira lhe conferir uma aparência completamente diferente para funcionar como um alerta para si mesmo. Nesse caso, você cria uma <xref:System.Windows.DataTemplate> para a exibição dos objetos `Task` de alta prioridade. Vamos adicionar o seguinte <xref:System.Windows.DataTemplate> à seção de recursos:  
  
 [!code-xaml[DataTemplatingIntro_snip#ImportantTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#importanttemplate)]  
  
 Observe que este exemplo usa o <xref:System.Windows.DataTemplate>.<xref:System.Windows.FrameworkTemplate.Resources%2A> property. Os recursos definidos nessa seção são compartilhados pelos elementos dentro do <xref:System.Windows.DataTemplate>.  
  
 Para fornecer a lógica para escolher qual <xref:System.Windows.DataTemplate> usar com base no valor `Priority` do objeto de dados, crie uma subclasse de <xref:System.Windows.Controls.DataTemplateSelector> e substitua o método <xref:System.Windows.Controls.DataTemplateSelector.SelectTemplate%2A>. No exemplo a seguir, o método <xref:System.Windows.Controls.DataTemplateSelector.SelectTemplate%2A> fornece a lógica para retornar o modelo apropriado com base no valor da propriedade `Priority`. O modelo a ser retornado é encontrado nos recursos do elemento de <xref:System.Windows.Window> enveloping.  
  
 [!code-csharp[DataTemplatingIntro_snip#DTSClass](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/TaskListDataTemplateSelector.cs#dtsclass)]
 [!code-vb[DataTemplatingIntro_snip#DTSClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataTemplatingIntro_snip/visualbasic/tasklistdatatemplateselector.vb#dtsclass)]  
  
 Em seguida, podemos declarar o `TaskListDataTemplateSelector` como um recurso:  
  
 [!code-xaml[DataTemplatingIntro_snip#R1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r1)]  
[!code-xaml[DataTemplatingIntro_snip#DTS](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#dts)]  
[!code-xaml[DataTemplatingIntro_snip#R2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r2)]  
  
 Para usar o recurso seletor de modelo, atribua-o à propriedade <xref:System.Windows.Controls.ItemsControl.ItemTemplateSelector%2A> da <xref:System.Windows.Controls.ListBox>. O <xref:System.Windows.Controls.ListBox> chama o método <xref:System.Windows.Controls.DataTemplateSelector.SelectTemplate%2A> do `TaskListDataTemplateSelector` para cada um dos itens na coleção subjacente. A chamada passa o objeto de dados como o parâmetro de item. O <xref:System.Windows.DataTemplate> retornado pelo método é aplicado a esse objeto de dados.  
  
 [!code-xaml[DataTemplatingIntro_snip#ItemTemplateSelector](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#itemtemplateselector)]  
  
 Com o seletor de modelo em vigor, o <xref:System.Windows.Controls.ListBox> agora aparece da seguinte maneira:  
  
 ![Captura de tela de exemplo de modelagem de dados](./media/datatemplatingintro-fig7.png "DataTemplatingIntro_fig7")  

Isso conclui nossa discussão sobre este exemplo. Para ver a amostra completa, consulte [Amostra da introdução à modelagem de dados](https://github.com/Microsoft/WPF-Samples/tree/master/Data%20Binding/DataTemplatingIntro).

<a name="DataTemplating_ItemsControl"></a>   
## <a name="styling-and-templating-an-itemscontrol"></a>Estilo e modelagem de um ItemsControl  
 Embora o <xref:System.Windows.Controls.ItemsControl> não seja o único tipo de controle com o qual você pode usar um <xref:System.Windows.DataTemplate>, é um cenário muito comum para associar um <xref:System.Windows.Controls.ItemsControl> a uma coleção. Na seção [o que pertence a um DataTemplate](#what_belongs_in_datatemplate) , discutimos que a definição de seu <xref:System.Windows.DataTemplate> só deve se preocupar com a apresentação dos dados. Para saber quando não é adequado usar um <xref:System.Windows.DataTemplate> é importante entender as diferentes propriedades de estilo e modelo fornecidas pelo <xref:System.Windows.Controls.ItemsControl>. O exemplo a seguir foi desenvolvido para ilustrar a função de cada uma dessas propriedades. O <xref:System.Windows.Controls.ItemsControl> neste exemplo está associado à mesma coleção de `Tasks` como no exemplo anterior. Para fins de demonstração, os estilos e modelos deste exemplo são declarados como embutidos.  
  
 [!code-xaml[DataTemplatingIntro_snip#ItemsControlProperties](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#itemscontrolproperties)]  
  
 Segue uma captura de tela do exemplo quando é renderizado:  
  
 ![Captura de tela de exemplo de ItemsControl](./media/databinding-itemscontrolproperties.png "DataBinding_ItemsControlProperties")  
  
 Observe que, em vez de usar o <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>, você pode usar o <xref:System.Windows.Controls.ItemsControl.ItemTemplateSelector%2A>. Consulte a seção anterior para ver um exemplo. Da mesma forma, em vez de usar o <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>, você tem a opção de usar o <xref:System.Windows.Controls.ItemsControl.ItemContainerStyleSelector%2A>.  
  
 Duas outras propriedades relacionadas a estilo dos <xref:System.Windows.Controls.ItemsControl> que não são mostradas aqui são <xref:System.Windows.Controls.ItemsControl.GroupStyle%2A> e <xref:System.Windows.Controls.ItemsControl.GroupStyleSelector%2A>.  
  
<a name="DataTemplating_HeirarchicalDataTemplate"></a>   
## <a name="support-for-hierarchical-data"></a>Suporte para dados hierárquicos  
 Até o momento, examinamos apenas como associar a uma única coleção e exibi-la. Às vezes, você tem uma coleção que contém outras coleções. A classe <xref:System.Windows.HierarchicalDataTemplate> foi projetada para ser usada com tipos de <xref:System.Windows.Controls.HeaderedItemsControl> para exibir esses dados. No exemplo a seguir, `ListLeagueList` é uma lista de objetos `League`. Cada objeto `League` tem um `Name` e uma coleção de objetos `Division`. Cada `Division` tem um `Name` e uma coleção de objetos `Team`; cada objeto `Team` tem um `Name`.  
  
 [!code-xaml[HierarchicalDataTemplateSnippet#HDT](~/samples/snippets/csharp/VS_Snippets_Wpf/HierarchicalDataTemplateSnippet/CS/window1.xaml#hdt)]  
  
 O exemplo mostra que, com o uso de <xref:System.Windows.HierarchicalDataTemplate>, você pode exibir facilmente os dados da lista que contêm outras listas. Segue uma captura de tela do exemplo.  
  
 ![Captura de tela de exemplo HierarchicalDataTemplate](./media/databinding-hierarchicaldatatemplate.png "DataBinding_HierarchicalDataTemplate")  
  
## <a name="see-also"></a>Consulte também

- [Associação de dados](../advanced/optimizing-performance-data-binding.md)
- [Localizar elementos gerados por DataTemplate](how-to-find-datatemplate-generated-elements.md)
- [Estilo e modelagem](../controls/styling-and-templating.md)
- [Visão geral da vinculação de dados](../../../desktop-wpf/data/data-binding-overview.md)
- [Visão geral dos estilos e dos modelos de cabeçalho da coluna GridView](../controls/gridview-column-header-styles-and-templates-overview.md)
