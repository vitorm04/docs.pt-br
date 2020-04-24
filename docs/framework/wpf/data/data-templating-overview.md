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
ms.openlocfilehash: b9e55eac1c72cd3deec21754373da4364a7cfed2
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646454"
---
# <a name="data-templating-overview"></a>Visão geral de modelagem dos dados
O modelo de modelagem de dados do WPF fornece grande flexibilidade para definir a apresentação dos dados. Os controles do WPF têm uma funcionalidade interna para dar suporte à personalização da apresentação de dados. Este tópico demonstra primeiro <xref:System.Windows.DataTemplate> como definir um e, em seguida, introduz outros recursos de templating de dados, como a seleção de modelos com base na lógica personalizada e o suporte para a exibição de dados hierárquicos.

<a name="Prerequisites"></a>
## <a name="prerequisites"></a>Pré-requisitos
 Este tópico se concentra nos recursos de modelagem de dados e não é uma introdução dos conceitos de associação de dados. Para obter informações sobre conceitos de associação de dados, consulte [Visão geral de associação de dados](../../../desktop-wpf/data/data-binding-overview.md).

 <xref:System.Windows.DataTemplate>é sobre a apresentação de dados e é uma das muitas características fornecidas pelo modelo de estilo e templating wpf. Para uma introdução do modelo de estilo e templating <xref:System.Windows.Style> wpf, como como usar um para definir propriedades nos controles, consulte o tópico [Estilo e Templating.](../../../desktop-wpf/fundamentals/styles-templates-overview.md)

 Além disso, é importante `Resources`entender , que são essencialmente o que permitem objetos como <xref:System.Windows.Style> e <xref:System.Windows.DataTemplate> para serem reutilizáveis. Para obter mais informações sobre recursos, consulte [Recursos de XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md).

<a name="DataTemplating_Basic"></a>
## <a name="data-templating-basics"></a>Noções básicas de modelagem de dados

 Para demonstrar <xref:System.Windows.DataTemplate> por que é importante, vamos passar por um exemplo de vinculação de dados. Neste exemplo, temos <xref:System.Windows.Controls.ListBox> um que está vinculado `Task` a uma lista de objetos. Cada objeto `Task` tem um `TaskName` (cadeia de caracteres), um `Description` (cadeia de caracteres), um `Priority` (int) e uma propriedade do tipo `TaskType`, que é um `Enum` com os valores `Home` e `Work`.

 [!code-xaml[DataTemplatingIntro_snip#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#resources)]
[!code-xaml[DataTemplatingIntro_snip#UI1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#ui1)]
[!code-xaml[DataTemplatingIntro_snip#UI2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#ui2)]

<a name="without_a_datatemplate"></a>
### <a name="without-a-datatemplate"></a>Sem um DataTemplate
 Sem <xref:System.Windows.DataTemplate>um <xref:System.Windows.Controls.ListBox> , nosso atualmente se parece com isso:

 ![Captura de tela de amostra de dados templating](./media/datatemplatingintro-fig1.png "DataTemplatingIntro_fig1")

 O que está acontecendo é que, <xref:System.Windows.Controls.ListBox> sem `ToString` instruções específicas, as chamadas por padrão ao tentar exibir os objetos na coleção. Portanto, se `Task` o objeto `ToString` se sobrepor <xref:System.Windows.Controls.ListBox> ao método, então o exibirá a representação de seqüência de cada objeto de origem na coleção subjacente.

 Por exemplo, se a classe `Task` substituir o método `ToString` dessa maneira, em que `name` é o campo para a propriedade `TaskName`:

 [!code-csharp[DataTemplatingIntro_snip#ToString](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Data.cs#tostring)]
 [!code-vb[DataTemplatingIntro_snip#ToString](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataTemplatingIntro_snip/visualbasic/data.vb#tostring)]

 Então <xref:System.Windows.Controls.ListBox> o parece o seguinte:

 ![Captura de tela de amostra de dados templating](./media/datatemplatingintro-fig2.png "DataTemplatingIntro_fig2")

 No entanto, isso é inflexível e limitante. Além disso, se você estiver vinculando aos dados XML, você não será capaz de substituir `ToString`.

<a name="defining_simple_datatemplate"></a>
### <a name="defining-a-simple-datatemplate"></a>Definindo um DataTemplate simples
 A solução é <xref:System.Windows.DataTemplate>definir um . Uma maneira de fazer isso <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> é <xref:System.Windows.Controls.ListBox> definir <xref:System.Windows.DataTemplate>a propriedade do a . O que você <xref:System.Windows.DataTemplate> especifica em seu torna-se a estrutura visual do seu objeto de dados. O <xref:System.Windows.DataTemplate> seguinte é bastante simples. Estamos dando instruções para que <xref:System.Windows.Controls.TextBlock> cada item apareça como três elementos dentro de um <xref:System.Windows.Controls.StackPanel>. Cada <xref:System.Windows.Controls.TextBlock> elemento está vinculado a `Task` uma propriedade da classe.

 [!code-xaml[DataTemplatingIntro_snip#Inline](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#inline)]

 Os dados subjacentes para os exemplos neste tópico são uma coleção de objetos CLR. Se você está vinculando aos dados XML, os conceitos fundamentais são os mesmos, mas há uma pequena diferença sintática. Por exemplo, em `Path=TaskName`vez de <xref:System.Windows.Data.Binding.XPath%2A> `@TaskName` ter, `TaskName` você definiria (se é um atributo do seu nó XML).

 Agora <xref:System.Windows.Controls.ListBox> nosso soa como o seguinte:

 ![Captura de tela de amostra de dados templating](./media/datatemplatingintro-fig3.png "DataTemplatingIntro_fig3")

<a name="defining_datatemplate_as_a_resource"></a>
### <a name="creating-the-datatemplate-as-a-resource"></a>Criando o DataTemplate como um recurso
 No exemplo acima, definimos a <xref:System.Windows.DataTemplate> linha. É mais comum defini-lo na seção de recursos para que possa ser um objeto reutilizável, como no exemplo a seguir:

 [!code-xaml[DataTemplatingIntro_snip#R1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r1)]
[!code-xaml[DataTemplatingIntro_snip#AsResource](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#asresource)]
[!code-xaml[DataTemplatingIntro_snip#R2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r2)]

 Agora, é possível usar o `myTaskTemplate` como recurso, como no exemplo a seguir:

 [!code-xaml[DataTemplatingIntro_snip#MyTaskTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#mytasktemplate)]

 Porque `myTaskTemplate` é um recurso, agora você pode usá-lo em <xref:System.Windows.DataTemplate> outros controles que têm uma propriedade que leva um tipo. Como mostrado acima, para <xref:System.Windows.Controls.ItemsControl> objetos, como o <xref:System.Windows.Controls.ListBox>, é a <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> propriedade. Para <xref:System.Windows.Controls.ContentControl> objetos, <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> é a propriedade.

<a name="Styling_DataType"></a>
### <a name="the-datatype-property"></a>A propriedade DataType
 A <xref:System.Windows.DataTemplate> classe <xref:System.Windows.DataTemplate.DataType%2A> tem uma propriedade que <xref:System.Windows.Style.TargetType%2A> é <xref:System.Windows.Style> muito semelhante à propriedade da classe. Portanto, em vez de `x:Key` especificar um para o <xref:System.Windows.DataTemplate> exemplo acima, você pode fazer o seguinte:

 [!code-xaml[DataTemplatingIntro_snip#DataType](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#datatype)]

 Isso <xref:System.Windows.DataTemplate> é aplicado automaticamente `Task` a todos os objetos. Observe que, nesse caso, o `x:Key` é definido implicitamente. Portanto, se você atribuir <xref:System.Windows.DataTemplate> `x:Key` isso um valor, você `x:Key` está <xref:System.Windows.DataTemplate> substituindo o implícito e o não seria aplicado automaticamente.

 Se você estiver <xref:System.Windows.Controls.ContentControl> vinculando `Task` a <xref:System.Windows.Controls.ContentControl> uma coleção de <xref:System.Windows.DataTemplate> objetos, o não usará o acima automaticamente. Isso porque a vinculação em um <xref:System.Windows.Controls.ContentControl> precisa de mais informações para distinguir se você deseja vincular a uma coleção inteira ou aos objetos individuais. Se <xref:System.Windows.Controls.ContentControl> você estiver rastreando a seleção <xref:System.Windows.Controls.ItemsControl> de um tipo, você pode definir a <xref:System.Windows.Data.Binding.Path%2A> propriedade da <xref:System.Windows.Controls.ContentControl> vinculação para "`/`para indicar que você está interessado no item atual. Para ver um exemplo, consulte [Como associar a uma coleção e exibir informações com base na seleção](how-to-bind-to-a-collection-and-display-information-based-on-selection.md). Caso contrário, você precisa <xref:System.Windows.DataTemplate> especificar o <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> explicitamente definindo a propriedade.

 A <xref:System.Windows.DataTemplate.DataType%2A> propriedade é particularmente útil <xref:System.Windows.Data.CompositeCollection> quando você tem um dos diferentes tipos de objetos de dados. Para ver um exemplo, consulte [Implementar um CompositeCollection](how-to-implement-a-compositecollection.md).

<a name="adding_more_to_datatemplate"></a>
## <a name="adding-more-to-the-datatemplate"></a>Adicionando mais ao DataTemplate
 Os dados aparecem com as informações necessárias no momento, mas, sem dúvida, há espaço para melhoria. Vamos melhorar a apresentação adicionando <xref:System.Windows.Controls.Border>a <xref:System.Windows.Controls.Grid>, <xref:System.Windows.Controls.TextBlock> a , e alguns elementos que descrevem os dados que estão sendo exibidos.

 [!code-xaml[DataTemplatingIntro#AddingMore](~/samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#addingmore)]
[!code-xaml[DataTemplatingIntro#AddingMore2](~/samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#addingmore2)]

 A captura de <xref:System.Windows.Controls.ListBox> tela <xref:System.Windows.DataTemplate>a seguir mostra o com esta modificada:

 ![Captura de tela de amostra de dados templating](./media/datatemplatingintro-fig4.png "DataTemplatingIntro_fig4")

 Podemos definir <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> <xref:System.Windows.HorizontalAlignment.Stretch> para <xref:System.Windows.Controls.ListBox> garantir que a largura dos itens odeie todo o espaço:

 [!code-xaml[DataTemplatingIntro_snip#Stretch](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#stretch)]

 Com <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> a propriedade <xref:System.Windows.HorizontalAlignment.Stretch>definida <xref:System.Windows.Controls.ListBox> para , o agora se parece com isso:

 ![Captura de tela de amostra de dados templating](./media/datatemplatingintro-fig5.png "DataTemplatingIntro_fig5")

<a name="DataTrigger_to_Apply_Property_Values"></a>
### <a name="use-datatriggers-to-apply-property-values"></a>Usar DataTriggers para aplicar valores da propriedade
 A apresentação atual não nos informa se uma `Task` é uma tarefa de casa ou uma tarefa de escritório. Lembre-se de que o objeto `Task` tem uma propriedade `TaskType` do tipo `TaskType`, que é uma enumeração com os valores `Home` e `Work`.

 No exemplo a <xref:System.Windows.DataTrigger> seguir, <xref:System.Windows.Controls.Border.BorderBrush%2A> os conjuntos `Yellow` do `TaskType` elemento `TaskType.Home`nomeado `border` para se a propriedade é .

 [!code-xaml[DataTemplatingIntro#DT](~/samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#dt)]
[!code-xaml[DataTemplatingIntro#DataTrigger](~/samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#datatrigger)]
[!code-xaml[DataTemplatingIntro#AddingMore2](~/samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#addingmore2)]

 Agora, nosso aplicativo tem a seguinte aparência. As tarefas de casa são exibidas com uma borda amarela, enquanto as tarefas de escritório aparecem com uma borda verde-azulada:

 ![Captura de tela de amostra de dados templating](./media/datatemplatingintro-fig6.png "DataTemplatingIntro_fig6")

 Neste exemplo, <xref:System.Windows.DataTrigger> o <xref:System.Windows.Setter> usa a para definir um valor de propriedade. As classes de <xref:System.Windows.TriggerBase.EnterActions%2A> gatilho <xref:System.Windows.TriggerBase.ExitActions%2A> também têm as propriedades que permitem iniciar um conjunto de ações, como animações. Além disso, há <xref:System.Windows.MultiDataTrigger> também uma classe que permite aplicar alterações com base em vários valores de propriedade vinculados a dados.

 Uma maneira alternativa de obter o <xref:System.Windows.Controls.Border.BorderBrush%2A> mesmo efeito `TaskType` é vincular a propriedade à propriedade `TaskType` e usar um conversor de valor para devolver a cor com base no valor. Criar o efeito acima usando um conversor é um pouco mais eficiente em termos de desempenho. Além disso, a criação do seu próprio conversor oferece mais flexibilidade, pois você fornecerá sua própria lógica. Por fim, a técnica escolhida depende do seu cenário e da sua preferência. Para obter informações sobre como <xref:System.Windows.Data.IValueConverter>escrever um conversor, consulte .

<a name="what_belongs_in_datatemplate"></a>
### <a name="what-belongs-in-a-datatemplate"></a>O que pertence a um DataTemplate?

No exemplo anterior, colocamos o <xref:System.Windows.DataTemplate> gatilho <xref:System.Windows.DataTemplate.Triggers%2A?displayProperty=nameWithType> dentro do uso da propriedade. O <xref:System.Windows.Setter> do gatilho define o valor de uma <xref:System.Windows.Controls.Border> propriedade de um <xref:System.Windows.DataTemplate>elemento (o elemento) que está dentro do . No entanto, se `Setters` as propriedades com as que você <xref:System.Windows.DataTemplate>está preocupado não são propriedades de <xref:System.Windows.Style> elementos que <xref:System.Windows.Controls.ListBoxItem> estão dentro da corrente, <xref:System.Windows.Controls.ListBox>pode ser mais adequado definir as propriedades usando um que é para a classe (se o controle que você está vinculando é um ). Por exemplo, se <xref:System.Windows.Trigger> você quiser <xref:System.Windows.UIElement.Opacity%2A> animar o valor do item quando um mouse aponta para <xref:System.Windows.Controls.ListBoxItem> um item, você define gatilhos dentro de um estilo. Para ver um exemplo, consulte a [Amostra de introdução a estilo e modelagem](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).

 Em geral, tenha em <xref:System.Windows.DataTemplate> mente que o está <xref:System.Windows.Controls.ListBoxItem> sendo aplicado a cada um dos gerados (para obter mais informações sobre como e onde é realmente aplicado, consulte a <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> página.). Você <xref:System.Windows.DataTemplate> está preocupado apenas com a apresentação e aparência dos objetos de dados. Na maioria dos casos, todos os outros aspectos da apresentação, como como <xref:System.Windows.Controls.ListBox> um item se parece quando é selecionado ou <xref:System.Windows.DataTemplate>como os itens são apresentados, não pertencem à definição de a . Para ver um exemplo, consulte a seção [Estilo e modelagem de um ItemsControl](#DataTemplating_ItemsControl).

<a name="Styling_StyleSelection"></a>
## <a name="choosing-a-datatemplate-based-on-properties-of-the-data-object"></a>Escolhendo um DataTemplate com base nas propriedades do objeto de dados
 Na seção [A propriedade DataType](#Styling_DataType), falamos que é possível definir diferentes modelos de dados para diferentes objetos de dados. Isso é especialmente útil quando <xref:System.Windows.Data.CompositeCollection> você tem um de diferentes tipos ou coleções com itens de diferentes tipos. Na seção [Usar DadosGatilhos para Aplicar Valores de Propriedade,](#DataTrigger_to_Apply_Property_Values) mostramos que se você <xref:System.Windows.DataTemplate> tiver uma coleção do mesmo tipo de objetos de dados, você pode criar um e, em seguida, usar gatilhos para aplicar alterações com base nos valores de propriedade de cada objeto de dados. Contudo, os gatilhos permitem aplicar valores da propriedade ou iniciar animações, mas não proporcionam flexibilidade para reconstruir a estrutura dos seus objetos de dados. Alguns cenários podem exigir <xref:System.Windows.DataTemplate> que você crie um diferente para objetos de dados que são do mesmo tipo, mas têm propriedades diferentes.

 Por exemplo, se um objeto `Task` tiver um valor `Priority` de `1`, talvez você queira lhe conferir uma aparência completamente diferente para funcionar como um alerta para si mesmo. Nesse caso, você <xref:System.Windows.DataTemplate> cria um para a `Task` exibição dos objetos de alta prioridade. Vamos adicionar o <xref:System.Windows.DataTemplate> seguinte à seção recursos:

 [!code-xaml[DataTemplatingIntro_snip#ImportantTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#importanttemplate)]

Este exemplo usa a propriedade [DataTemplate.Resources.](xref:System.Windows.FrameworkTemplate.Resources%2A) Os recursos definidos nessa seção são <xref:System.Windows.DataTemplate>compartilhados pelos elementos dentro do .

 Para fornecer lógica <xref:System.Windows.DataTemplate> para escolher qual `Priority` usar com base no valor <xref:System.Windows.Controls.DataTemplateSelector> do objeto <xref:System.Windows.Controls.DataTemplateSelector.SelectTemplate%2A> de dados, crie uma subclasse e anule o método. No exemplo a <xref:System.Windows.Controls.DataTemplateSelector.SelectTemplate%2A> seguir, o método fornece lógica para devolver `Priority` o modelo apropriado com base no valor da propriedade. O modelo de retorno é encontrado nos recursos <xref:System.Windows.Window> do elemento envolvente.

 [!code-csharp[DataTemplatingIntro_snip#DTSClass](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/TaskListDataTemplateSelector.cs#dtsclass)]
 [!code-vb[DataTemplatingIntro_snip#DTSClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataTemplatingIntro_snip/visualbasic/tasklistdatatemplateselector.vb#dtsclass)]

 Em seguida, podemos declarar o `TaskListDataTemplateSelector` como um recurso:

 [!code-xaml[DataTemplatingIntro_snip#R1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r1)]
[!code-xaml[DataTemplatingIntro_snip#DTS](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#dts)]
[!code-xaml[DataTemplatingIntro_snip#R2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r2)]

 Para usar o recurso do seletor de modelo, atribua-o à <xref:System.Windows.Controls.ItemsControl.ItemTemplateSelector%2A> propriedade do <xref:System.Windows.Controls.ListBox>. O <xref:System.Windows.Controls.ListBox> método <xref:System.Windows.Controls.DataTemplateSelector.SelectTemplate%2A> do `TaskListDataTemplateSelector` método para cada um dos itens da coleção subjacente. A chamada passa o objeto de dados como o parâmetro de item. O <xref:System.Windows.DataTemplate> que é devolvido pelo método é então aplicado a esse objeto de dados.

 [!code-xaml[DataTemplatingIntro_snip#ItemTemplateSelector](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#itemtemplateselector)]

 Com o seletor <xref:System.Windows.Controls.ListBox> de modelos no lugar, o agora aparece da seguinte forma:

 ![Captura de tela de amostra de dados templating](./media/datatemplatingintro-fig7.png "DataTemplatingIntro_fig7")

Isso conclui nossa discussão sobre este exemplo. Para ver a amostra completa, consulte [Amostra da introdução à modelagem de dados](https://github.com/Microsoft/WPF-Samples/tree/master/Data%20Binding/DataTemplatingIntro).

<a name="DataTemplating_ItemsControl"></a>
## <a name="styling-and-templating-an-itemscontrol"></a>Estilo e modelagem de um ItemsControl
 Mesmo que <xref:System.Windows.Controls.ItemsControl> o não seja o único <xref:System.Windows.DataTemplate> tipo de controle com o qual <xref:System.Windows.Controls.ItemsControl> você pode usar, é um cenário muito comum para vincular um a uma coleção. Na seção [O que pertence em um DataTemplate](#what_belongs_in_datatemplate) discutimos que a definição de você <xref:System.Windows.DataTemplate> só deve se preocupar com a apresentação de dados. Para saber quando não é adequado <xref:System.Windows.DataTemplate> usar um é importante entender as diferentes <xref:System.Windows.Controls.ItemsControl>propriedades de estilo e modelo fornecidas pelo . O exemplo a seguir foi desenvolvido para ilustrar a função de cada uma dessas propriedades. O <xref:System.Windows.Controls.ItemsControl> exemplo está vinculado à `Tasks` mesma coleção do exemplo anterior. Para fins de demonstração, os estilos e modelos deste exemplo são declarados como embutidos.

 [!code-xaml[DataTemplatingIntro_snip#ItemsControlProperties](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#itemscontrolproperties)]

 Segue uma captura de tela do exemplo quando é renderizado:

 ![ItensControle captura de tela de exemplo](./media/databinding-itemscontrolproperties.png "DataBinding_ItemsControlProperties")

 Note que, em <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>vez de <xref:System.Windows.Controls.ItemsControl.ItemTemplateSelector%2A>usar o , você pode usar o . Consulte a seção anterior para ver um exemplo. Da mesma forma, <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>em vez de usar <xref:System.Windows.Controls.ItemsControl.ItemContainerStyleSelector%2A>o , você tem a opção de usar o .

 Duas outras propriedades relacionadas ao estilo das <xref:System.Windows.Controls.ItemsControl> que não são mostradas aqui são <xref:System.Windows.Controls.ItemsControl.GroupStyle%2A> e <xref:System.Windows.Controls.ItemsControl.GroupStyleSelector%2A>.

<a name="DataTemplating_HeirarchicalDataTemplate"></a>
## <a name="support-for-hierarchical-data"></a>Suporte para dados hierárquicos
 Até o momento, examinamos apenas como associar a uma única coleção e exibi-la. Às vezes, você tem uma coleção que contém outras coleções. A <xref:System.Windows.HierarchicalDataTemplate> classe foi projetada <xref:System.Windows.Controls.HeaderedItemsControl> para ser usada com tipos para exibir tais dados. No exemplo a seguir, `ListLeagueList` é uma lista de objetos `League`. Cada objeto `League` tem um `Name` e uma coleção de objetos `Division`. Cada `Division` tem um `Name` e uma coleção de objetos `Team`; cada objeto `Team` tem um `Name`.

 [!code-xaml[HierarchicalDataTemplateSnippet#HDT](~/samples/snippets/csharp/VS_Snippets_Wpf/HierarchicalDataTemplateSnippet/CS/window1.xaml#hdt)]

 O exemplo mostra que, <xref:System.Windows.HierarchicalDataTemplate>com o uso de , você pode facilmente exibir dados de lista que contêm outras listas. Segue uma captura de tela do exemplo.

 ![Captura de tela de exemplo HierarchicalDataTemplate](./media/databinding-hierarchicaldatatemplate.png "DataBinding_HierarchicalDataTemplate")

## <a name="see-also"></a>Confira também

- [Vinculação de dados](../advanced/optimizing-performance-data-binding.md)
- [Encontrar elementos gerados por datatemplate](how-to-find-datatemplate-generated-elements.md)
- [Estilo e modelagem](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Visão geral da vinculação de dados](../../../desktop-wpf/data/data-binding-overview.md)
- [Visão geral dos estilos e dos modelos de cabeçalho da coluna GridView](../controls/gridview-column-header-styles-and-templates-overview.md)
