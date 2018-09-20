---
title: Visão geral da vinculação de dados
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data conversion for binding [WPF]
- binding data [WPF], about data binding
- data binding [WPF], about data binding
- conversion for data binding [WPF]
ms.assetid: c707c95f-7811-401d-956e-2fffd019a211
ms.openlocfilehash: 1b34b3369e5a045f45251d3285f10bf74b6f0d33
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/18/2018
ms.locfileid: "45990070"
---
# <a name="data-binding-overview"></a>Visão geral da vinculação de dados
A vinculação de dados do [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fornece aos aplicativos uma maneira simples e consistente para apresentar e interagir com os dados. Os elementos podem ser associados aos dados de uma variedade de fontes de dados na forma de objetos [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] e [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)]. <xref:System.Windows.Controls.ContentControl>tais como <xref:System.Windows.Controls.Button> e <xref:System.Windows.Controls.ItemsControl>tais como <xref:System.Windows.Controls.ListBox> e <xref:System.Windows.Controls.ListView> tem uma funcionalidade interna para permitir a estilização flexível de um único item de dados ou coleções de itens de dados. É possível gerar exibições com classificação, filtragem e agrupamento dos dados.  
  
 A funcionalidade de vinculação de dados no [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tem várias vantagens sobre modelos tradicionais, incluindo uma ampla gama de propriedades que herdam suporte a vinculação de dados, representação de dados de [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] flexível e separação clara entre a lógica de negócios e a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
 Este tópico discute primeiramente conceitos fundamentais para [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vinculação de dados e então aborda o uso da <xref:System.Windows.Data.Binding> classe e outros recursos de vinculação de dados.  
  
  
<a name="what_is_data_binding"></a>   
## <a name="what-is-data-binding"></a>O que é a vinculação de dados?  
 Vinculação de dados é o processo que estabelece uma conexão entre a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] e a lógica de negócios do aplicativo. Se a associação tiver as configurações corretas e os dados fornecerem notificações adequadas, os elementos associados aos dados refletirão automaticamente quaisquer alterações que venham a ocorrer no valor desses dados. A vinculação de dados também poderá significar que, se houver uma alteração de uma representação externa dos dados em um elemento, os dados subjacentes poderão ser atualizados automaticamente para refletir essa alteração. Por exemplo, se o usuário edita o valor em uma <xref:System.Windows.Controls.TextBox> elemento, o valor de dados subjacente é atualizado automaticamente para refletir essa alteração.  
  
 Um uso típico da vinculação de dados é colocar dados de configuração local ou do servidor em formulários ou outros controles de [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. No [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], este conceito é expandido para incluir a associação de um amplo espectro de propriedades a uma variedade de fontes de dados. No [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], propriedades de dependência de elementos podem ser associadas a objetos [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] (incluindo objetos [!INCLUDE[TLA#tla_adonet](../../../../includes/tlasharptla-adonet-md.md)] ou objetos associados com serviços Web e propriedades da Web) e dados [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)].  
  
 Para um exemplo de vinculação de dados, dê uma olhada na seguinte [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] de aplicativo do [Data Binding Demo](https://go.microsoft.com/fwlink/?LinkID=163703):  
  
 ![Captura de tela de exemplo de vinculação de dados](../../../../docs/framework/wpf/data/media/databinding-databindingdemo.png "DataBinding_DataBindingDemo")  
  
 Acima, a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] de um aplicativo que exibe uma lista de itens de leilão. O aplicativo demonstra os seguintes recursos de vinculação de dados:  
  
-   O conteúdo a <xref:System.Windows.Controls.ListBox> está associado a uma coleção de *AuctionItem* objetos. Um objeto *AuctionItem* tem propriedades como *Description*, *StartPrice*, *StartDate*, *Category*, *SpecialFeatures*, etc.  
  
-   Os dados (*AuctionItem* objetos) exibido no <xref:System.Windows.Controls.ListBox> são modelados de forma que a descrição e o preço atual sejam mostrados para cada item. Isso é feito usando um <xref:System.Windows.DataTemplate>. Além disso, a aparência de cada item depende do valor de *SpecialFeatures* do *AuctionItem* sendo exibido. Se o valor *SpecialFeatures* do *AuctionItem* for *Color*, o item terá uma borda azul. Se o valor for *Highlight*, o item terá uma borda laranja e uma estrela. A seção [Modelos de dados](#data_templating) fornece informações sobre modelagem de dados.  
  
-   O usuário pode agrupar, filtrar ou classificar os dados usando o <xref:System.Windows.Controls.CheckBox>es fornecidas. Na imagem acima, "Agrupar por categoria" e "Ordenar por categoria e data" <xref:System.Windows.Controls.CheckBox>são selecionados. Você talvez tenha observado que os dados estão agrupados com base na categoria do produto e que o nome da categoria está em ordem alfabética. É difícil perceber isto na imagem, mas os itens também são classificados por data de início dentro de cada categoria. Isso é feito usando uma *exibição de coleção*. A seção [Associar a coleções](#binding_to_collections) discute exibições de coleções.  
  
-   Quando o usuário seleciona um item, o <xref:System.Windows.Controls.ContentControl> exibe os detalhes do item selecionado. Isso é chamado de *cenário de Mestre/Detalhes*. A seção [cenário de Mestre/Detalhes](#master_detail_scenario) fornece informações sobre esse tipo de cenário de associação.  
  
-   O tipo dos *StartDate* é de propriedade <xref:System.DateTime>, que retorna uma data que inclui o tempo em milissegundos. Neste aplicativo, um conversor personalizado foi utilizado para que uma cadeia de caracteres de data menor fosse exibida. A seção [Conversão de dados](#data_conversion) fornece informações sobre conversores.  
  
 Quando o usuário clica no botão *Adicionar produto*, o seguinte formulário aparece:  
  
 ![página Adicionar Listagem de Produtos](../../../../docs/framework/wpf/data/media/databinding-demo-addproductlisting.png "DataBinding_Demo_AddProductListing")  
  
 O usuário pode editar os campos no formulário, visualizar a listagem de produtos usando a visualização rápida e os painéis de visualização mais detalhados e, em seguida, clicar em *enviar* para adicionar a nova listagem de produtos. Quaisquer funcionalidades de agrupamento, filtragem e classificação existentes serão aplicadas à nova entrada. Neste caso em particular, o item inserido na imagem acima será exibido como o segundo item dentro da categoria *Computador*.  
  
 Não é mostrada nessa imagem é a lógica de validação fornecida na *data de início* <xref:System.Windows.Controls.TextBox>. Se o usuário insere um valor data (formato inválido ou data anterior), o usuário será notificado com uma <xref:System.Windows.Controls.ToolTip> e um ponto de exclamação vermelho ao lado de <xref:System.Windows.Controls.TextBox>. A seção [Validação de dados](#data_validation) discute como criar lógica de validação.  
  
 Antes de discutir em detalhes os diferentes recursos de vinculação de dados descritos acima, discutiremos na próxima seção os conceitos fundamentais que são críticos para o entendimento da vinculação de dados do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
## <a name="basic-data-binding-concepts"></a>Conceitos básicos de vinculação de dados  
  
 Independentemente de qual elemento você está associando e da natureza da fonte de dados, cada associação segue o modelo ilustrado pela figura a seguir:  
  
 ![Diagrama de vinculação de dados básica](../../../../docs/framework/wpf/data/media/databindingmostbasic.png "DataBindingMostBasic")  
  
 Conforme ilustrado na figura anterior, vinculação de dados é essencialmente a ponte entre o destino da associação e a origem da associação. A figura demonstra os seguintes conceitos fundamentais de vinculação de dados do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]:  
  
-   Normalmente, cada associação tem estes quatro componentes: um objeto de destino da associação, uma propriedade de destino, uma origem da associação e um caminho para o valor na origem da associação a utilizar. Por exemplo, se você deseja associar o conteúdo de um <xref:System.Windows.Controls.TextBox> para o *nome* propriedade de uma *funcionário* do objeto, seu objeto de destino é o <xref:System.Windows.Controls.TextBox>, a propriedade de destino é o <xref:System.Windows.Controls.TextBox.Text%2A> propriedade, o valor a ser usado é *nome*, e o objeto de origem é o *funcionário* objeto.  
  
-   A propriedade de destino deve ser uma propriedade de dependência. A maioria dos <xref:System.Windows.UIElement> propriedades são propriedades de dependência e a maioria das propriedades de dependência, exceto as somente leitura, dão suporte à vinculação de dados por padrão. (Somente <xref:System.Windows.DependencyObject> tipos podem definir as propriedades de dependência e todos os <xref:System.Windows.UIElement>s derivam de <xref:System.Windows.DependencyObject>.)  
  
-   Embora não especificado na figura, deve-se observar que o objeto de origem da associação não é restrito a ser um objeto [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] personalizado. A vinculação de dados do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dá suporte a dados na forma de objetos [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] e [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]. Para dar alguns exemplos, sua origem da associação pode ser um <xref:System.Windows.UIElement>, qualquer objeto de lista, uma [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] objeto está associado [!INCLUDE[TLA#tla_adonet](../../../../includes/tlasharptla-adonet-md.md)] dados ou serviços da Web ou um XmlNode que contém seu [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] dados. Para obter mais informações, consulte [Visão geral de origens da associação](../../../../docs/framework/wpf/data/binding-sources-overview.md).  
  
 Conforme você lê outros tópicos do [!INCLUDE[TLA#tla_sdk](../../../../includes/tlasharptla-sdk-md.md)], é importante lembrar que quando você está estabelecendo uma associação, você está associando um destino da associação *a* uma origem da associação. Por exemplo, se você estiver exibindo alguns subjacente [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] dados em um <xref:System.Windows.Controls.ListBox> usando a associação de dados, você está associando seu <xref:System.Windows.Controls.ListBox> para o [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] dados.  
  
 Para estabelecer uma associação, você usa o <xref:System.Windows.Data.Binding> objeto. O restante deste tópico discute muitos dos conceitos associados e algumas das propriedades e o uso do <xref:System.Windows.Data.Binding> objeto.  
  
<a name="direction_of_data_flow"></a>   
### <a name="direction-of-the-data-flow"></a>Direção do fluxo de dados  
 Conforme mencionado anteriormente e indicado pela seta na figura acima, o fluxo de dados de uma associação pode ir do destino da associação para a origem da associação (por exemplo, o valor de origem é alterado quando um usuário edita o valor de um <xref:System.Windows.Controls.TextBox>) e/ou da origem de associação para o destino da associação (por exemplo, seu <xref:System.Windows.Controls.TextBox> conteúdo é atualizado com alterações na origem da associação) se a origem da associação fornece notificações adequadas.  
  
 Convém que seu aplicativo permita aos usuários alterar os dados e propagá-los de volta para o objeto de origem. Ou talvez você não queira permitir que os usuários atualizem os dados de origem. Você pode controlar isso definindo a <xref:System.Windows.Data.Binding.Mode%2A> propriedade de seu <xref:System.Windows.Data.Binding> objeto. A figura a seguir ilustra os diferentes tipos de fluxo de dados:  
  
 ![Fluxo de dados de vinculação de dados](../../../../docs/framework/wpf/data/media/databinding-dataflow.png "DataBinding_DataFlow")  
  
-   <xref:System.Windows.Data.BindingMode.OneWay> associação faz com que as alterações para a propriedade de origem para atualizar automaticamente a propriedade de destino, mas as alterações à propriedade de destino não são propagadas de volta para a propriedade de origem. Esse tipo de associação será apropriado se o controle associado for somente leitura de forma implícita. Por exemplo, você pode associar a uma origem como uma cotação da bolsa ou talvez a propriedade de destino não tenha nenhuma interface de controle disponível para fazer alterações, como uma cor da tela de fundo associada a dados de uma tabela. Se não houver necessidade de monitorar as alterações da propriedade de destino, o uso do modo de associação <xref:System.Windows.Data.BindingMode.OneWay> evitará a sobrecarga do modo de associação <xref:System.Windows.Data.BindingMode.TwoWay>.  
  
-   <xref:System.Windows.Data.BindingMode.TwoWay> associação faz com que as alterações para a propriedade de origem ou a propriedade de destino para atualizar automaticamente o outro. Esse tipo de associação é apropriado para formulários editáveis ou outros cenários [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] totalmente interativos. A maioria das propriedades padrão para <xref:System.Windows.Data.BindingMode.OneWay> associação, mas algumas propriedades de dependência (normalmente propriedades de controles editáveis pelo usuário, como o <xref:System.Windows.Controls.TextBox.Text%2A> propriedade de <xref:System.Windows.Controls.TextBox> e o <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> propriedade do <xref:System.Windows.Controls.CheckBox>) padrão para <xref:System.Windows.Data.BindingMode.TwoWay> associação. Uma maneira programática de determinar se uma propriedade de dependência é associada de forma unidirecional ou bidirecional por padrão é obter os metadados de propriedade da propriedade usando <xref:System.Windows.DependencyProperty.GetMetadata%2A> e verificar o valor booliano da propriedade <xref:System.Windows.FrameworkPropertyMetadata.BindsTwoWayByDefault%2A>.  
  
-   <xref:System.Windows.Data.BindingMode.OneWayToSource> é o inverso da <xref:System.Windows.Data.BindingMode.OneWay> associação; ele atualiza a propriedade de origem quando a propriedade de destino é alterado. Um cenário exemplo é se você só precisa reavaliar o valor da origem da [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
-   Não é ilustrado na figura é <xref:System.Windows.Data.BindingMode.OneTime> de associação, que faz com que a propriedade de origem para inicializar a propriedade de destino, mas não se propagam as alterações subsequentes. Isso significa que se o contexto de dados sofrer uma mudança ou o objeto no contexto de dados for alterado, a alteração não será refletida na propriedade de destino. Esse tipo de associação será apropriado se você estiver usando dados em que um instantâneo do estado atual é apropriado para uso ou os dados forem realmente estáticos. Esse tipo de associação também é útil se você deseja inicializar a propriedade de destino com um valor de uma propriedade de origem e o contexto de dados não é conhecido com antecedência. Este é basicamente uma forma mais simples de associação do <xref:System.Windows.Data.BindingMode.OneWay>, que fornece um melhor desempenho em casos em que o valor de origem não é alterado.  
  
 Observe que, para detectar alterações na origem (aplicáveis ao <xref:System.Windows.Data.BindingMode.OneWay> e <xref:System.Windows.Data.BindingMode.TwoWay> associações), a origem deve implementar um mecanismo de notificação de alteração de propriedade adequado, como <xref:System.ComponentModel.INotifyPropertyChanged>. Ver [implementar notificação de alteração de propriedade](../../../../docs/framework/wpf/data/how-to-implement-property-change-notification.md) para obter um exemplo de um <xref:System.ComponentModel.INotifyPropertyChanged> implementação.  
  
 O <xref:System.Windows.Data.Binding.Mode%2A> página de propriedades fornece mais informações sobre modos de associação e um exemplo de como especificar a direção da associação.  
  
<a name="what_triggers_source_updates"></a>   
### <a name="what-triggers-source-updates"></a>O que dispara atualizações de origem  
 Associações que são <xref:System.Windows.Data.BindingMode.TwoWay> ou <xref:System.Windows.Data.BindingMode.OneWayToSource> escutam por alterações na propriedade de destino e propagá-las de volta para a fonte. Isso é conhecido como atualização da origem. Por exemplo, você pode editar o texto de uma caixa de texto para alterar o valor da origem subjacente. Conforme descrito na seção anterior, a direção do fluxo de dados é determinada pelo valor da <xref:System.Windows.Data.Binding.Mode%2A> propriedade da associação.  
  
 Mas o seu valor de origem é atualizado enquanto você está editando o texto ou após você terminar de editar o texto e apontar o mouse para fora da caixa de texto? O <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> propriedade da associação determina o que dispara a atualização da origem. Os pontos nas setas para direita na figura a seguir ilustra a função do <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> propriedade:  
  
 ![Diagrama de UpdateSourceTrigger](../../../../docs/framework/wpf/data/media/databindingupdatesourcetrigger.png "DataBindingUpdateSourceTrigger")  
  
 Se o <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> valor é <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>, em seguida, o valor apontado pela seta à direita do <xref:System.Windows.Data.BindingMode.TwoWay> ou o <xref:System.Windows.Data.BindingMode.OneWayToSource> associações é atualizado assim que as alterações de propriedade de destino. No entanto, se o <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> valor é <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus>, em seguida, esse valor só é atualizado com o novo valor quando a propriedade de destino perde o foco.  
  
 Semelhante do <xref:System.Windows.Data.Binding.Mode%2A> propriedade, propriedades de dependência diferentes têm diferente padrão <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> valores. O valor padrão para a maioria das propriedades de dependência é <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>, enquanto a propriedade <xref:System.Windows.Controls.TextBox.Text%2A> tem um valor padrão de <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus>. Isso significa que as atualizações de origem geralmente ocorrem sempre que as alterações de propriedade de destino, que é bom para <xref:System.Windows.Controls.CheckBox>es e outros controles simples. No entanto, para campos de texto, atualizar após cada pressionamento de tecla pode diminuir o desempenho e impede a oportunidade rotineira de voltar e corrigir erros de digitação antes de confirmar o novo valor. É por isso que o <xref:System.Windows.Controls.TextBox.Text%2A> propriedade tem um valor padrão de <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus> em vez de <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>.  
  
 Consulte a <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> página de propriedades para obter informações sobre como localizar o padrão <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> valor da propriedade de dependência.  
  
 A tabela a seguir fornece um cenário de exemplo para cada <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> valor usando o <xref:System.Windows.Controls.TextBox> como um exemplo:  
  
|Valor de UpdateSourceTrigger|Quando o valor de origem é atualizado|Cenário de exemplo de caixa de texto|  
|-------------------------------|----------------------------------------|----------------------------------|  
|LostFocus (padrão para <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType>)|Quando o controle da caixa de texto perde o foco|Um <xref:System.Windows.Controls.TextBox> que está associado com a lógica de validação (consulte a seção de validação de dados)|  
|PropertyChanged|Conforme você digita no <xref:System.Windows.Controls.TextBox>|<xref:System.Windows.Controls.TextBox> controles em uma janela de sala de bate-papo|  
|Explícito|Quando o aplicativo chama <xref:System.Windows.Data.BindingExpression.UpdateSource%2A>|<xref:System.Windows.Controls.TextBox> controles em um formulário editável (atualiza o valor de origem somente quando o usuário clica no botão Enviar)|  
  
 Para obter um exemplo, consulte [Controlar quando o texto da caixa de texto atualiza a origem](../../../../docs/framework/wpf/data/how-to-control-when-the-textbox-text-updates-the-source.md).  
  
<a name="creating_a_binding"></a>   
## <a name="creating-a-binding"></a>Criar uma associação  
  
 Para recapitular alguns conceitos discutidos nas seções anteriores, você estabelece uma associação usando o <xref:System.Windows.Data.Binding> objeto e cada associação normalmente tem quatro componentes: destino, propriedade de destino, origem da associação e um caminho de associação para o valor de origem a ser usado. Esta seção discute como configurar uma associação.  
  
 Considere o exemplo a seguir, no qual o objeto de origem da associação é uma classe chamada *MyData* que é definida no namespace *SDKSample*. Para fins de demonstração, a classe *MyData* tem uma propriedade de cadeia de caracteres denominada *ColorName*, por meio da qual o valor é definido como "Red" (vermelho). Assim, esse exemplo gera um botão com uma tela de fundo vermelha.  
  
 [!code-xaml[BindNonTextProperty#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindNonTextProperty/CS/Page1.xaml#1)]  
  
 Para obter mais detalhes sobre a sintaxe de declaração de associação e para obter exemplos de como definir uma associação no código, consulte [Visão geral das declarações de associação](../../../../docs/framework/wpf/data/binding-declarations-overview.md).  
  
 Se nós aplicarmos esse exemplo a nosso diagrama básico, a figura resultante será semelhante à exibida a seguir. Esse é um <xref:System.Windows.Data.BindingMode.OneWay> associação porque a propriedade Background dá suporte a <xref:System.Windows.Data.BindingMode.OneWay> associação por padrão.  
  
 ![Diagrama de vinculação de dados](../../../../docs/framework/wpf/data/media/databindingbuttonbackgroundexample.png "DataBindingButtonBackgroundExample")  
  
 Você deve estar imaginando por que isso funciona mesmo que o *ColorName* propriedade é do tipo cadeia de caracteres durante a <xref:System.Windows.Controls.Control.Background%2A> propriedade é do tipo <xref:System.Windows.Media.Brush>. Trata-se da conversão de tipo padrão em operação, a qual é abordada na seção [Conversão de dados](#data_conversion).  
  
<a name="specifying_the_binding_source"></a>   
### <a name="specifying-the-binding-source"></a>Especificar a origem da associação  
 Observe que no exemplo anterior, a origem da associação é especificada, definindo o <xref:System.Windows.FrameworkElement.DataContext%2A> propriedade no <xref:System.Windows.Controls.DockPanel> elemento. O <xref:System.Windows.Controls.Button> herda, em seguida, o <xref:System.Windows.FrameworkElement.DataContext%2A> o valor do <xref:System.Windows.Controls.DockPanel>, que é seu elemento pai. Para reiterar, o objeto de origem da associação é um dos quatro componentes necessários de uma associação. Portanto, sem o objeto de origem de associação que está sendo especificado, a associação não faria nada.  
  
 Há várias maneiras para especificar o objeto de origem de associação. Usando o <xref:System.Windows.FrameworkElement.DataContext%2A> propriedade em um elemento pai é útil quando você estiver associando várias propriedades à mesma fonte. No entanto, às vezes pode ser mais apropriado especificar a origem da associação em declarações de associação individuais. No exemplo anterior, em vez de usar o <xref:System.Windows.FrameworkElement.DataContext%2A> propriedade, você pode especificar a origem da associação, definindo o <xref:System.Windows.Data.Binding.Source%2A> propriedade diretamente na declaração da associação do botão, como no exemplo a seguir:  
  
 [!code-xaml[BindNonTextProperty#BackgroundBindingCompact](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindNonTextProperty/CS/Page2.xaml#backgroundbindingcompact)]  
  
 Diferente de definir a <xref:System.Windows.FrameworkElement.DataContext%2A> propriedade em um elemento diretamente, herdando o <xref:System.Windows.FrameworkElement.DataContext%2A> valor de um ancestral (como o botão no primeiro exemplo) e, em seguida, explicitamente especificando a origem da associação ao definir o <xref:System.Windows.Data.Binding.Source%2A> propriedade o <xref:System.Windows.Data.Binding> (por exemplo, o botão no último exemplo), você também pode usar o <xref:System.Windows.Data.Binding.ElementName%2A> propriedade ou o <xref:System.Windows.Data.Binding.RelativeSource%2A> propriedade para especificar a origem da associação. O <xref:System.Windows.Data.Binding.ElementName%2A> propriedade é útil quando você estiver associando a outros elementos no seu aplicativo, como quando você estiver usando um controle deslizante para ajustar a largura de um botão. O <xref:System.Windows.Data.Binding.RelativeSource%2A> propriedade é útil quando a associação é especificada em uma <xref:System.Windows.Controls.ControlTemplate> ou um <xref:System.Windows.Style>. Para obter mais informações, consulte [Especificar a origem da associação](../../../../docs/framework/wpf/data/how-to-specify-the-binding-source.md).  
  
<a name="specifying_the_path_to_the_value"></a>   
### <a name="specifying-the-path-to-the-value"></a>Especificar o caminho para o valor  
 Se a origem da associação for um objeto, use o <xref:System.Windows.Data.Binding.Path%2A> propriedade para especificar o valor a ser usado em sua associação. Se você estiver associando a [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] dados, use o <xref:System.Windows.Data.Binding.XPath%2A> propriedade para especificar o valor. Em alguns casos, pode ser aplicável usar a <xref:System.Windows.Data.Binding.Path%2A> mesmo quando seus dados são de propriedade [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]. Por exemplo, se você quiser acessar a propriedade de nome de um XmlNode retornado (como resultado de uma consulta XPath), você deve usar o <xref:System.Windows.Data.Binding.Path%2A> propriedade além de <xref:System.Windows.Data.Binding.XPath%2A> propriedade.  
  
 Para obter informações sobre a sintaxe e exemplos, consulte o <xref:System.Windows.Data.Binding.Path%2A> e <xref:System.Windows.Data.Binding.XPath%2A> páginas de propriedades.  
  
 Observe que, embora tenhamos enfatizado que o <xref:System.Windows.Data.Binding.Path%2A> para o valor a ser usado é um dos quatro componentes necessários de uma associação, nos cenários em que você deseja associar a um objeto inteiro, o valor a ser usado seria o mesmo que o objeto de origem da associação. Nesses casos, é aplicável não especificar um <xref:System.Windows.Data.Binding.Path%2A>. Considere o exemplo a seguir:  
  
 [!code-xaml[MasterDetail#EmptyBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MasterDetail/CSharp/Page1.xaml#emptybinding)]  
  
 O exemplo acima usa a sintaxe de associação vazia: {Binding}. Nesse caso, o <xref:System.Windows.Controls.ListBox> herda o DataContext de um elemento de DockPanel pai (não mostrado neste exemplo). Quando o caminho não é especificado, o padrão é associar ao objeto inteiro. Em outras palavras, neste exemplo, o caminho foi excluído porque estamos associando o <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> propriedade ao objeto inteiro. (Consulte a seção [Associar a coleções](#binding_to_collections) para uma discussão aprofundada.)  
  
 Além de ao associar a uma coleção, este cenário também é útil quando você deseja associar a um objeto inteiro em vez de apenas uma única propriedade de um objeto. Por exemplo, o objeto de origem é do tipo cadeia de caracteres e você quer simplesmente associar à própria cadeia de caracteres. Outro cenário comum é quando você deseja associar um elemento a um objeto com várias propriedades.  
  
 Observe que talvez seja necessário aplicar uma lógica personalizada para que os dados sejam significativos para a propriedade de destino associada. A lógica personalizada poderá ser na forma de um conversor personalizado (se a conversão de tipo padrão não existir). Para obter mais informações sobre conversores, consulte [Conversão de dados](#data_conversion).  
  
<a name="binding_bindingexpression"></a>   
### <a name="binding-and-bindingexpression"></a>Associação e BindingExpression  
 Antes de entrar em outros recursos e usos de associação de dados, seria útil apresentar a <xref:System.Windows.Data.BindingExpression> classe. Como você viu nas seções anteriores, o <xref:System.Windows.Data.Binding> é a classe de alto nível para a declaração de uma associação; o <xref:System.Windows.Data.Binding> classe fornece muitas propriedades que permitem que você especifique as características de uma associação. Uma classe relacionada, <xref:System.Windows.Data.BindingExpression>, é o objeto subjacente que mantém a conexão entre a origem e destino. Uma associação contém todas as informações que podem ser compartilhadas entre várias expressões de associação. Um <xref:System.Windows.Data.BindingExpression> é uma expressão de instância que não pode ser compartilhada e contém todas as informações de instância a <xref:System.Windows.Data.Binding>.  
  
 Por exemplo, considere o seguinte, onde *myDataObject* é uma instância de *MyData* classe *myBinding* é a origem <xref:System.Windows.Data.Binding> objeto e *MyData* classe é uma classe definida que contém uma propriedade de cadeia de caracteres denominada *MyDataProperty*. Este exemplo associa o conteúdo de texto *mytext*, uma instância do <xref:System.Windows.Controls.TextBlock>, para *MyDataProperty*.  
  
 [!code-csharp[CodeOnlyBinding#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#1)]
 [!code-vb[CodeOnlyBinding#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#1)]  
  
 Você pode usar o mesmo objeto *myBinding* para criar outras associações. Por exemplo, você pode usar o objeto *myBinding* para associar o conteúdo de texto de uma caixa de seleção a *MyDataProperty*. Nesse cenário, haverá duas instâncias de <xref:System.Windows.Data.BindingExpression> compartilhando a *myBinding* objeto.  
  
 Um <xref:System.Windows.Data.BindingExpression> objeto pode ser obtido por meio do valor de retorno de chamada <xref:System.Windows.Data.BindingOperations.GetBindingExpression%2A> em um objeto de associação de dados. Os tópicos a seguir demonstram alguns usos do <xref:System.Windows.Data.BindingExpression> classe:  
  
-   [Obter o objeto de associação de uma propriedade de destino associada](../../../../docs/framework/wpf/data/how-to-get-the-binding-object-from-a-bound-target-property.md)  
  
-   [Controlar quando o texto da caixa de texto atualiza a origem](../../../../docs/framework/wpf/data/how-to-control-when-the-textbox-text-updates-the-source.md)  
  
<a name="data_conversion"></a>   
## <a name="data-conversion"></a>Conversão de dados  
 No exemplo anterior, o botão é vermelho porque sua <xref:System.Windows.Controls.Control.Background%2A> propriedade está associada a uma propriedade de cadeia de caracteres com o valor "Red". Isso funciona como um conversor de tipo está presente na <xref:System.Windows.Media.Brush> tipo para converter o valor de cadeia de caracteres em um <xref:System.Windows.Media.Brush>.  
  
 Para adicionar essas informações à figura na seção [Criando uma associação](#creating_a_binding), o diagrama é semelhante ao seguinte:  
  
 ![Diagrama de vinculação de dados](../../../../docs/framework/wpf/data/media/databindingbuttondefaultconversion.png "DataBindingButtonDefaultConversion")  
  
 No entanto, se em vez de ter uma propriedade de cadeia de caracteres de tipo seu objeto de fonte de associação tem um *cor* propriedade do tipo <xref:System.Windows.Media.Color>? Nesse caso, para que a associação funcione você precisaria primeiro transformar o *cor* valor da propriedade em algo que o <xref:System.Windows.Controls.Control.Background%2A> propriedade aceita. Você precisaria criar um conversor personalizado implementando a <xref:System.Windows.Data.IValueConverter> interface, como no exemplo a seguir:  
  
 [!code-csharp[ColorPicker_snip#16](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ColorPicker_snip/CSharp/ColorPickerLib/ColorPicker.cs#16)]
 [!code-vb[ColorPicker_snip#16](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ColorPicker_snip/visualbasic/colorpickerlib/colorpicker.vb#16)]  
  
 O <xref:System.Windows.Data.IValueConverter> página de referência fornece mais informações.  
  
 Agora o conversor personalizado é usado no lugar da conversão padrão e nosso diagrama fica assim:  
  
 ![Diagrama de vinculação de dados](../../../../docs/framework/wpf/data/media/databindingconvertercolorexample.png "DataBindingConverterColorExample")  
  
 Para reiterar, conversões padrão podem estar disponíveis devido a conversores de tipo presentes no tipo para o qual a associação está sendo realizada. Esse comportamento dependerá de quais conversores de tipo estão disponíveis no destino. Em caso de dúvida, crie seu próprio conversor.  
  
 A seguir estão alguns cenários típicos em que faz sentido implementar um conversor de dados:  
  
-   Os dados devem ser exibidos de forma diferente, dependendo da cultura. Por exemplo, você talvez queira implementar um conversor de moeda ou um conversor de data do calendário/hora com base nos valores ou padrões utilizados em uma cultura específica.  
  
-   Os dados que está sendo usados não são necessariamente destinados a alterar o valor de texto de uma propriedade, mas sim destinados a alterar alguns outros valores como a origem de uma imagem ou então a cor ou o estilo do texto. Conversores podem ser usados nesta instância convertendo a associação de uma propriedade que pode não parecer apropriada, assim como a associação de um campo de texto à propriedade Background de uma célula de tabela.  
  
-   Mais de um controle ou múltiplas propriedades de controles são vinculados aos mesmos dados. Nesse caso, a associação primária pode simplesmente exibir o texto, enquanto outras associações lidam com questões específicas de exibição, mas ainda usam a mesma associação como informações da origem.  
  
-   Até agora não discutimos <xref:System.Windows.Data.MultiBinding>, e uma propriedade de destino tem uma coleção de associações. No caso de uma <xref:System.Windows.Data.MultiBinding>, você usa um personalizado <xref:System.Windows.Data.IMultiValueConverter> para produzir um valor final dos valores das associações. Por exemplo, a cor pode ser computada de valores vermelhos, azuis e verdes, que podem ser valores dos mesmos ou de diferentes objetos de origem da associação. Consulte o <xref:System.Windows.Data.MultiBinding> página de classe para informações e exemplos.  
  
<a name="binding_to_collections"></a>   
## <a name="binding-to-collections"></a>Associar a coleções  
  
 Um objeto de origem de associação pode ser tratado como um único objeto do qual as propriedades contêm dados ou como uma coleção de objetos polimórficos que são frequentemente agrupados juntos (como o resultado de uma consulta a um banco de dados). Até agora só discutimos a associação a objetos individuais, no entanto, a associação a uma coleção de dados é um cenário comum. Por exemplo, um cenário comum é usar um <xref:System.Windows.Controls.ItemsControl> como um <xref:System.Windows.Controls.ListBox>, <xref:System.Windows.Controls.ListView>, ou <xref:System.Windows.Controls.TreeView> para exibir um conjunto de dados, como no aplicativo mostrado na [o que é vinculação de dados?](#what_is_data_binding) seção.  
  
 Felizmente, nosso diagrama básico ainda se aplica. Se você estiver associando um <xref:System.Windows.Controls.ItemsControl> a uma coleção, o diagrama fica assim:  
  
 ![Diagrama de ItemsControl de vinculação de dados](../../../../docs/framework/wpf/data/media/databindingitemscontrol.png "DataBindingItemsControl")  
  
 Conforme mostrado neste diagrama, para associar uma <xref:System.Windows.Controls.ItemsControl> a um objeto de coleção, <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> é a propriedade a ser usado. Você pode pensar <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> propriedade como o conteúdo do <xref:System.Windows.Controls.ItemsControl>. Observe que a associação é <xref:System.Windows.Data.BindingMode.OneWay> porque o <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> dá suporte a propriedade <xref:System.Windows.Data.BindingMode.OneWay> associação por padrão.  
  
<a name="how_to_implement_collections"></a>   
### <a name="how-to-implement-collections"></a>Como implementar coleções  
 Você pode enumerar por qualquer coleção que implemente o <xref:System.Collections.IEnumerable> interface. No entanto, para definir associações dinâmicas para que inserções ou exclusões na coleção de atualizam o [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] automaticamente, a coleção deve implementar a <xref:System.Collections.Specialized.INotifyCollectionChanged> interface. Essa interface expõe um evento que deve ser acionado sempre que a coleção subjacente for alterada.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fornece o <xref:System.Collections.ObjectModel.ObservableCollection%601> classe, que é uma implementação embutida de uma coleção de dados que expõe o <xref:System.Collections.Specialized.INotifyCollectionChanged> interface. Observe que para dar total suporte transferência valores de dados dos objetos de origem para os destinos, cada objeto em sua coleção que dá suporte a propriedades associáveis também deve implementar o <xref:System.ComponentModel.INotifyPropertyChanged> interface. Para obter mais informações, consulte [Visão geral de origens da associação](../../../../docs/framework/wpf/data/binding-sources-overview.md).  
  
 Antes de implementar sua própria coleção, considere o uso de <xref:System.Collections.ObjectModel.ObservableCollection%601> ou um da coleção existente de classes, como <xref:System.Collections.Generic.List%601>, <xref:System.Collections.ObjectModel.Collection%601>, e <xref:System.ComponentModel.BindingList%601>, entre muitas outras. Se você tiver um cenário avançado e quiser implementar sua própria coleção, considere o uso de <xref:System.Collections.IList>, que fornece uma coleção não genérica de objetos que podem ser acessados individualmente pelo índice e, portanto, o melhor desempenho.  
  
<a name="collection_views"></a>   
### <a name="collection-views"></a>Exibições de coleção  
 Uma vez seu <xref:System.Windows.Controls.ItemsControl> está associado a uma coleção de dados, talvez você queira classificar, filtrar ou agrupar os dados. Para fazer isso, use as exibições de coleção, que são classes que implementam o <xref:System.ComponentModel.ICollectionView> interface.  
  
  
#### <a name="what-are-collection-views"></a>O que são exibições de coleção?  
 Uma exibição de coleção é uma camada sobre uma coleção de origem da associação que permite a você navegar e exibir a coleção de origem com base em consultas de classificação, filtragem e agrupamento, sem precisar alterar a coleção de origem subjacente. Uma exibição de coleção também mantém um ponteiro para o item atual na coleção. Se a coleção de origem implementa o <xref:System.Collections.Specialized.INotifyCollectionChanged> interface, as alterações geradas pelo <xref:System.Collections.Specialized.INotifyCollectionChanged.CollectionChanged> eventos são propagadas para os modos de exibição.  
  
 Já que as exibições não alteram as coleções de origem subjacentes, cada coleção de origem pode ter várias exibições associadas a ela. Por exemplo, você pode ter uma coleção de objetos *Task*. Com o uso de exibições, você pode exibir esses mesmos dados de maneiras diferentes. Por exemplo, no lado esquerdo da página, talvez você queira mostrar as tarefas ordenadas por prioridade e, no lado direito, agrupadas por área.  
  
<a name="how_to_create_a_view"></a>   
#### <a name="how-to-create-a-view"></a>Como criar uma exibição  
 Uma maneira de criar e usar uma exibição é instanciar o objeto de exibição diretamente e então usá-lo como a origem da associação. Por exemplo, considere o aplicativo [Data Binding Demo](https://go.microsoft.com/fwlink/?LinkID=163703) mostrado na seção [O que é vinculação de dados?](#what_is_data_binding). O aplicativo é implementado, de modo que o <xref:System.Windows.Controls.ListBox> associa a uma exibição sobre a coleta de dados, em vez da coleta de dados diretamente. O exemplo a seguir é extraído do aplicativo [Data Binding Demo](https://go.microsoft.com/fwlink/?LinkID=163703). O <xref:System.Windows.Data.CollectionViewSource> classe é o [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] proxy de uma classe que herda de <xref:System.Windows.Data.CollectionView>. Nesse exemplo específico, o <xref:System.Windows.Data.CollectionViewSource.Source%2A> da exibição está associado ao *AuctionItems* coleção (do tipo <xref:System.Collections.ObjectModel.ObservableCollection%601>) do objeto de aplicativo atual.  
  
 [!code-xaml[DataBindingLab#WindowResources1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#windowresources1)]  
[!code-xaml[DataBindingLab#CollectionViewSource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#collectionviewsource)]  
[!code-xaml[DataBindingLab#WindowResources2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#windowresources2)]  
  
 O recurso *listingDataView* serve como a origem da associação para elementos no aplicativo, como o <xref:System.Windows.Controls.ListBox>:  
  
 [!code-xaml[DataBindingLab#Master1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#master1)]  
[!code-xaml[DataBindingLab#Master2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#master2)]  
  
 Para criar outro modo de exibição da mesma coleção, você pode criar outra <xref:System.Windows.Data.CollectionViewSource> da instância e dê a ele um diferentes `x:Key` nome.  
  
 A tabela a seguir mostra quais tipos de dados de exibição são criados como a exibição de coleção padrão ou pelo <xref:System.Windows.Data.CollectionViewSource> com base no tipo de coleção de origem.  
  
|Tipo de coleção de origem|Tipo de exibição de coleção|Observações|  
|----------------------------|--------------------------|-----------|  
|<xref:System.Collections.IEnumerable>|Um tipo interno com base em <xref:System.Windows.Data.CollectionView>|Não é possível agrupar itens.|  
|<xref:System.Collections.IList>|<xref:System.Windows.Data.ListCollectionView>|Mais rápido.|  
|<xref:System.ComponentModel.IBindingList>|<xref:System.Windows.Data.BindingListCollectionView>||  
  
##### <a name="using-a-default-view"></a>Usando uma exibição padrão  
 Especificar uma exibição de coleção como uma origem da associação é uma maneira de criar e usar uma exibição de coleção. O WPF também cria uma exibição de coleção padrão para cada coleção usada como uma origem da associação. Se você associar diretamente a uma coleção, o WPF será associado à sua exibição padrão. Observe que essa exibição padrão é compartilhada por todas as associações à mesma coleção, de modo que uma alteração feita a uma exibição padrão por um código ou controle associado (por exemplo, uma classificação ou uma alteração do ponteiro atual do item, discutido posteriormente) será refletida em todas as demais associações à mesma coleção.  
  
 Para obter a exibição padrão, você deve usar o <xref:System.Windows.Data.CollectionViewSource.GetDefaultView%2A> método. Para obter um exemplo, consulte [Como obter a exibição padrão de uma coleção de dados](../../../../docs/framework/wpf/data/how-to-get-the-default-view-of-a-data-collection.md).  
  
##### <a name="collection-views-with-adonet-datatables"></a>Exibições de coleção com DataTables do ADO.NET  
 Para melhorar o desempenho, exibições de coleção para o ADO.NET <xref:System.Data.DataTable> ou <xref:System.Data.DataView> objetos delegam a classificação e filtragem para o <xref:System.Data.DataView>. Isso faz com que a classificação e filtragem sejam compartilhadas entre todas as exibições de coleção da fonte de dados. Para habilitar cada exibição de coleção a classificar e filtrar de modo independente, inicialize cada exibição de coleção com seu próprio <xref:System.Data.DataView> objeto.  
  
#### <a name="sorting"></a>Classificação  
 Conforme mencionado anteriormente, as exibições podem aplicar uma ordem de classificação para uma coleção. Já que eles existem na coleção subjacente, seus dados podem ter ou não uma ordem inerente e relevante. A exibição da coleção permite impor uma ordem ou alterar a ordem padrão, com base em critérios de comparação fornecidos por você. Já que essa é uma exibição dos dados baseada no cliente, um cenário comum é que o usuário deseje classificar colunas de dados tabulares segundo o valor ao qual a coluna corresponde. Usando exibições, essa classificação controlada pelo usuário pode ser aplicada, novamente sem necessidade de alterações na coleção subjacente nem mesmo precisar repetir a consulta do conteúdo da coleção. Para obter um exemplo, consulte [Classificar uma coluna GridView quando um cabeçalho é clicado](../../../../docs/framework/wpf/controls/how-to-sort-a-gridview-column-when-a-header-is-clicked.md).  
  
 O exemplo a seguir mostra a lógica de "Classificação por categoria e data" <xref:System.Windows.Controls.CheckBox> do aplicativo [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] na [o que é vinculação de dados?](#what_is_data_binding) seção:  
  
 [!code-csharp[DataBindingLab#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#8)]
 [!code-vb[DataBindingLab#8](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#8)]  
  
#### <a name="filtering"></a>Filtragem  
 Exibições também podem aplicar um filtro a uma coleção. Isso significa que, embora um item possa existir na coleção, essa exibição específica é destinada a mostrar somente um certo subconjunto da coleção inteira. Você pode filtrar por uma condição nos dados. Por exemplo, assim como é feito pelo aplicativo na [o que é vinculação de dados?](#what_is_data_binding) seção, "Mostrar apenas ofertas" <xref:System.Windows.Controls.CheckBox> contém a lógica para filtrar os itens que custam US $25 ou mais. O código a seguir é executado para definir *ShowOnlyBargainsFilter* como o <xref:System.Windows.Data.CollectionViewSource.Filter> manipulador de eventos quando que <xref:System.Windows.Controls.CheckBox> está selecionada:  
  
 [!code-csharp[DataBindingLab#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#10)]
 [!code-vb[DataBindingLab#10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#10)]  
  
 O manipulador *ShowOnlyBargainsFilter* tem a seguinte implementação:  
  
 [!code-csharp[DataBindingLab#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#5)]
 [!code-vb[DataBindingLab#5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#5)]  
  
 Se você estiver usando um dos <xref:System.Windows.Data.CollectionView> classes diretamente em vez de <xref:System.Windows.Data.CollectionViewSource>, você usaria o <xref:System.Windows.Data.CollectionView.Filter%2A> propriedade para especificar um retorno de chamada. Para obter um exemplo, consulte [Filtrar dados em uma exibição](../../../../docs/framework/wpf/data/how-to-filter-data-in-a-view.md).  
  
#### <a name="grouping"></a>Agrupamento  
 Exceto para a classe interna que exibe um <xref:System.Collections.IEnumerable> coleção, todas as exibições de coleção dá suporte à funcionalidade de agrupamento, o que permite ao usuário particionar a coleção na exibição de coleção em grupos lógicos. Os grupos podem ser explícitos (caso em que o usuário fornece uma lista de grupos) ou então implícitos (caso em que os grupos são gerados dinamicamente, dependendo dos dados).  
  
 O exemplo a seguir mostra a lógica de "Agrupar por categoria" <xref:System.Windows.Controls.CheckBox>:  
  
 [!code-csharp[DataBindingLab#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#6)]
 [!code-vb[DataBindingLab#6](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#6)]  
  
 Para obter outro exemplo de agrupamento, consulte [Agrupar itens em uma ListView que implementa uma GridView](../../../../docs/framework/wpf/controls/how-to-group-items-in-a-listview-that-implements-a-gridview.md).  
  
#### <a name="current-item-pointers"></a>Ponteiros de item atuais  
 As exibições também dão suporte à noção de um item atual. Você pode navegar pelos objetos em uma exibição de coleção. Enquanto você navega, você está movendo um ponteiro de item que permite que você recupere o objeto existente nesse local específico na coleção. Para obter um exemplo, consulte [Navegar pelos objetos em uma CollectionView de dados](../../../../docs/framework/wpf/data/how-to-navigate-through-the-objects-in-a-data-collectionview.md).  
  
 Já que o WPF associa a uma coleção usando uma exibição (uma exibição que você especificar ou uma exibição padrão da coleção), todas as associações a coleções têm um ponteiro de item atual. Ao associar a um modo de exibição, o caractere de barra ("/") em um valor `Path` atribui o item atual da exibição. No exemplo a seguir, o contexto de dados é uma exibição de coleção. A primeira linha é associada à coleção. A segunda linha é associada ao item atual na coleção. A terceira linha é associada à propriedade `Description` do item atual na coleção.  
  
```xaml  
<Button Content="{Binding }" />  
<Button Content="{Binding Path=/}" />  
<Button Content="{Binding Path=/Description}" />   
```  
  
 A sintaxe de barra e de propriedade também pode ser empilhada para transpor uma hierarquia de coleções. O exemplo a seguir associa o item atual de uma coleção chamada `Offices`, que é uma propriedade do item atual da coleção de origem.  
  
```xaml  
<Button Content="{Binding /Offices/}" />  
```  
  
 O ponteiro do item atual pode ser afetado por qualquer classificação ou filtragem aplicada à coleção. A classificação preserva o ponteiro do item atual no último item selecionado, mas a exibição de coleção está agora reestruturada em torno dele. (Talvez o item selecionado estivesse no início da lista antes, mas agora o item selecionado pode estar em algum lugar no meio.) Se essa seleção permanecer visível após a filtragem, a filtragem preservará o item selecionado. Caso contrário, o ponteiro do item atual será definido como o primeiro item da exibição de coleção filtrada.  
  
<a name="master_detail_scenario"></a>   
#### <a name="master-detail-binding-scenario"></a>Cenário de associação mestre/detalhes  
 A noção de um item atual é útil não somente para navegação por itens em uma coleção, mas também para o cenário de associação mestre/detalhes. Considere a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] do aplicativo na seção [O que é vinculação de dados?](#what_is_data_binding) novamente. Nesse aplicativo, a seleção dentro do <xref:System.Windows.Controls.ListBox> determina o conteúdo exibido no <xref:System.Windows.Controls.ContentControl>. Colocá-lo de outra forma, quando um <xref:System.Windows.Controls.ListBox> item é selecionado, o <xref:System.Windows.Controls.ContentControl> mostra os detalhes do item selecionado.  
  
 Você pode implementar o cenário mestre/detalhes simplesmente associando dois ou mais controles à mesma exibição. O exemplo a seguir da [Data Binding Demo](https://go.microsoft.com/fwlink/?LinkID=163703) mostra a marcação do <xref:System.Windows.Controls.ListBox> e o <xref:System.Windows.Controls.ContentControl> você vê na aplicação [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] no [o que é vinculação de dados?](#what_is_data_binding) seção:  
  
 [!code-xaml[DataBindingLab#Master1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#master1)]  
[!code-xaml[DataBindingLab#Master2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#master2)]  
[!code-xaml[DataBindingLab#Detail](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#detail)]  
  
 Observe que ambos os controles são associados à mesma origem, o recurso estático *listingDataView* (consulte a definição desse recurso na [seção Como criar uma exibição](#how_to_create_a_view)). Isso funciona porque quando um objeto singleton (o <xref:System.Windows.Controls.ContentControl> nesse caso) é associado a uma exibição de coleção, ele automaticamente associa ao <xref:System.Windows.Data.CollectionView.CurrentItem%2A> do modo de exibição. Observe que <xref:System.Windows.Data.CollectionViewSource> objetos automaticamente sincronizam moeda e seleção. Se o controle de lista não está associado a um <xref:System.Windows.Data.CollectionViewSource> objeto como neste exemplo, você precisa definir seu <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> propriedade para `true` para este trabalho.  
  
 Para obter outros exemplos, consulte [Associar a uma coleção e exibir informações com base na seleção](../../../../docs/framework/wpf/data/how-to-bind-to-a-collection-and-display-information-based-on-selection.md) e [Usar o padrão mestre/detalhes com os dados hierárquicos](../../../../docs/framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-data.md).  
  
 Talvez você tenha observado que o exemplo anterior usa um modelo. Na verdade, os dados não seriam exibidos de maneira que gostaríamos sem o uso de modelos (aquele usado explicitamente pelo <xref:System.Windows.Controls.ContentControl> e aquele usado implicitamente pelo <xref:System.Windows.Controls.ListBox>). Agora, na próxima seção, nos ocuparemos da modelagem de dados.  
  
<a name="data_templating"></a>   
## <a name="data-templating"></a>Modelagem de dados  
 Sem o uso de modelos de dados, nossa [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] do aplicativo na seção [O que é vinculação de dados?](#what_is_data_binding) teria aparência semelhante à seguinte:  
  
 ![Data Binding Demo sem modelos de dados](../../../../docs/framework/wpf/data/media/databindingdemotemplates.png "DataBindingDemoTemplates")  
  
 Conforme mostrado no exemplo na seção anterior, tanto a <xref:System.Windows.Controls.ListBox> controle e o <xref:System.Windows.Controls.ContentControl> são associados ao objeto da coleção inteira (ou mais especificamente, o modo de exibição sobre o objeto de coleção) de *AuctionItem*s. Sem instruções específicas de como exibir o conjunto de dados, o <xref:System.Windows.Controls.ListBox> está exibindo uma representação de cadeia de caracteres de cada objeto na coleção subjacente e o <xref:System.Windows.Controls.ContentControl> está exibindo uma representação de cadeia de caracteres do objeto está associado a.  
  
 Para resolver esse problema, o aplicativo define <xref:System.Windows.DataTemplate>s. Conforme mostrado no exemplo na seção anterior, o <xref:System.Windows.Controls.ContentControl> usa explicitamente o *detailsProductListingTemplate*<xref:System.Windows.DataTemplate>. O <xref:System.Windows.Controls.ListBox> controle usa implicitamente o seguinte <xref:System.Windows.DataTemplate> ao exibir o *AuctionItem* objetos na coleção:  
  
 [!code-xaml[DataBindingLab#AuctionItemDataTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DataBindingLabApp.xaml#auctionitemdatatemplate)]  
  
 Com o uso desses dois <xref:System.Windows.DataTemplate>s, a interface do usuário resultante é mostrada na [o que é vinculação de dados?](#what_is_data_binding) seção. Como você pode ver nessa captura de tela, além de permitindo que você coloque dados em seus controles, <xref:System.Windows.DataTemplate>s permitem que você defina visuais interessantes para seus dados. Por exemplo, <xref:System.Windows.DataTrigger>s são usados no acima <xref:System.Windows.DataTemplate> , de modo que *AuctionItem*s com *SpecialFeatures* valor de *realçar* seriam exibidos com um borda laranja e uma estrela.  
  
 Para obter mais informações sobre modelos de dados, consulte [Visão geral de modelagem de dados](../../../../docs/framework/wpf/data/data-templating-overview.md).  
  
<a name="data_validation"></a>   
## <a name="data-validation"></a>Validação de dados  
  
 A maioria dos aplicativos que usam a entrada do usuário precisam ter lógica de validação para garantir que o usuário tenha inserido as informações esperadas. As verificações de validação podem ser baseadas em tipo, intervalo, formato ou outros requisitos específicos de aplicativo. Esta seção discute como a validação de dados funciona no [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
### <a name="associating-validation-rules-with-a-binding"></a>Associar regras de validação com uma associação  
 O [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] modelo de associação de dados permite que você associe <xref:System.Windows.Data.Binding.ValidationRules%2A> com seu <xref:System.Windows.Data.Binding> objeto. Por exemplo, o exemplo a seguir associa um <xref:System.Windows.Controls.TextBox> a uma propriedade denominada `StartPrice` e adiciona uma <xref:System.Windows.Controls.ExceptionValidationRule> do objeto para o <xref:System.Windows.Data.Binding.ValidationRules%2A?displayProperty=nameWithType> propriedade.  
  
 [!code-xaml[DataBindingLab#DefaultValidation](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/AddProductWindow.xaml#defaultvalidation)]  
  
 Um <xref:System.Windows.Controls.ValidationRule> objeto verifica se o valor de uma propriedade é válido. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tem os seguintes dois tipos internos <xref:System.Windows.Controls.ValidationRule> objetos:  
  
-   Um <xref:System.Windows.Controls.ExceptionValidationRule> verifica exceções geradas durante a atualização da propriedade de origem de associação. No exemplo anterior, `StartPrice` é do tipo inteiro. Quando o usuário insere um valor que não pode ser convertido em um número inteiro, é gerada uma exceção que faz com que a associação seja marcada como inválida. Uma sintaxe alternativa para a configuração a <xref:System.Windows.Controls.ExceptionValidationRule> explicitamente é definir o <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> propriedade `true` em seu <xref:System.Windows.Data.Binding> ou <xref:System.Windows.Data.MultiBinding> objeto.  
  
-   Um <xref:System.Windows.Controls.DataErrorValidationRule> objeto verifica se há erros gerados por objetos que implementam o <xref:System.ComponentModel.IDataErrorInfo> interface. Para obter um exemplo de como usar essa regra de validação, consulte <xref:System.Windows.Controls.DataErrorValidationRule>. Uma sintaxe alternativa para a configuração a <xref:System.Windows.Controls.DataErrorValidationRule> explicitamente é definir o <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A> propriedade `true` em seu <xref:System.Windows.Data.Binding> ou <xref:System.Windows.Data.MultiBinding> objeto.  
  
 Você também pode criar sua própria regra de validação derivando de <xref:System.Windows.Controls.ValidationRule> classe e implementando o <xref:System.Windows.Controls.ValidationRule.Validate%2A> método. O exemplo a seguir mostra a regra usada pela *adicionar listagem de produtos* "Data de início" <xref:System.Windows.Controls.TextBox> da [o que é vinculação de dados?](#what_is_data_binding) seção:  
  
 [!code-csharp[DataBindingLab#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/FutureDateRule.cs#2)]
 [!code-vb[DataBindingLab#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/FutureDateRule.vb#2)]  
  
 O *StartDateEntryForm* <xref:System.Windows.Controls.TextBox> usa esse *FutureDateRule*, conforme mostrado no exemplo a seguir:  
  
 [!code-xaml[DataBindingLab#CustomValidation](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/AddProductWindow.xaml#customvalidation)]  
  
 Observe que, como o <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> valor é <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>, o mecanismo de associação atualiza o valor de origem em cada pressionamento de tecla, o que significa que também verifica cada regra no <xref:System.Windows.Data.Binding.ValidationRules%2A> coleção cada pressionamento de tecla. Discutiremos isso de modo mais aprofundado na seção Processo de validação.  
  
<a name="invalidation_feedback"></a>   
### <a name="providing-visual-feedback"></a>Fornecer comentários visuais  
 Se o usuário inserir um valor inválido, talvez você queira fornecer comentários sobre o erro no aplicativo [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. É uma maneira de fornecer esses comentários é definir a <xref:System.Windows.Controls.Validation.ErrorTemplate%2A?displayProperty=nameWithType> propriedade anexada a um personalizado <xref:System.Windows.Controls.ControlTemplate>. Conforme mostrado na seção anterior, o *StartDateEntryForm* <xref:System.Windows.Controls.TextBox> usa um <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> chamado *validationTemplate*. O exemplo a seguir mostra a definição de *validationTemplate*:  
  
 [!code-xaml[DataBindingLab#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/AddProductWindow.xaml#1)]  
  
 O <xref:System.Windows.Controls.AdornedElementPlaceholder> elemento Especifica onde o controle sendo adornado deve ser colocado.  
  
 Além disso, você também pode usar um <xref:System.Windows.Controls.ToolTip> para exibir a mensagem de erro. Os dois os *StartDateEntryForm* e o *StartPriceEntryForm*<xref:System.Windows.Controls.TextBox>es usam o estilo *textStyleTextBox*, que cria um <xref:System.Windows.Controls.ToolTip> que Exibe a mensagem de erro. O exemplo a seguir mostra a definição de *textStyleTextBox*. A propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `true` quando um ou mais das associações nas propriedades do elemento associado estiverem no erro.  
  
 [!code-xaml[DataBindingLab#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DataBindingLabApp.xaml#14)]  
  
 Com o personalizado <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> e o <xref:System.Windows.Controls.ToolTip>, o *StartDateEntryForm* <xref:System.Windows.Controls.TextBox> é semelhante ao seguinte quando há um erro de validação:  
  
 ![Erro de validação de vinculação de dados](../../../../docs/framework/wpf/data/media/databindingdemo-validation.PNG "DataBindingDemo_Validation")  
  
 Se sua <xref:System.Windows.Data.Binding> tem regras de validação associadas mas você não especificar um <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> no controle associado, um padrão <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> será usado para notificar os usuários quando há um erro de validação. O padrão <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> é um modelo de controle que define uma borda vermelha na camada de adorno. Com o padrão <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> e o <xref:System.Windows.Controls.ToolTip>, o [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] da *StartPriceEntryForm* <xref:System.Windows.Controls.TextBox> é semelhante ao seguinte quando há um erro de validação:  
  
 ![Erro de validação de vinculação de dados](../../../../docs/framework/wpf/data/media/databindingdemo-validationdefault.PNG "DataBindingDemo_ValidationDefault")  
  
 Para obter um exemplo de como fornecer a lógica para validar todos os controles em uma caixa de diálogo, consulte a seção Caixas de diálogo personalizadas na [Visão geral das caixas de diálogo](../../../../docs/framework/wpf/app-development/dialog-boxes-overview.md).  
  
### <a name="validation-process"></a>Processo de validação  
 Geralmente, a validação ocorre quando o valor de um destino é transferido para a propriedade de origem da associação. Isso ocorre em <xref:System.Windows.Data.BindingMode.TwoWay> e <xref:System.Windows.Data.BindingMode.OneWayToSource> associações. Para reiterar, o que faz com que uma atualização de origem depende do valor da <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> propriedade, conforme descrito em de [o que dispara atualizações de origem](#what_triggers_source_updates) seção.  
  
 O conteúdo a seguir descreve o processo de *validação*. Observe que, se ocorrer um erro de validação ou outro tipo de erro em qualquer momento durante este processo, o processo será interrompido.  
  
1.  O mecanismo de associação verifica se há qualquer personalizado <xref:System.Windows.Controls.ValidationRule> objetos definidos cuja <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> é definido como <xref:System.Windows.Controls.ValidationStep.RawProposedValue> para fazer isso <xref:System.Windows.Data.Binding>, caso em que ele chama o <xref:System.Windows.Controls.ValidationRule.Validate%2A> método em cada <xref:System.Windows.Controls.ValidationRule> até que um deles seja executado em um erro ou até que todos eles passem.  
  
2.  O mecanismo de associação então chamará o conversor, se houver.  
  
3.  Se o conversor for bem-sucedido, o mecanismo de associação verifica se há qualquer personalizado <xref:System.Windows.Controls.ValidationRule> objetos definidos cuja <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> é definido como <xref:System.Windows.Controls.ValidationStep.ConvertedProposedValue> para fazer isso <xref:System.Windows.Data.Binding>, caso em que ele chama o <xref:System.Windows.Controls.ValidationRule.Validate%2A> método em cada <xref:System.Windows.Controls.ValidationRule> que tem <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> definido como <xref:System.Windows.Controls.ValidationStep.ConvertedProposedValue> até que um deles seja executado em um erro ou até que todos eles passem.  
  
4.  O mecanismo de associação define a propriedade de origem.  
  
5.  O mecanismo de associação verifica se há qualquer personalizado <xref:System.Windows.Controls.ValidationRule> objetos definidos cuja <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> é definido como <xref:System.Windows.Controls.ValidationStep.UpdatedValue> para fazer isso <xref:System.Windows.Data.Binding>, caso em que ele chama o <xref:System.Windows.Controls.ValidationRule.Validate%2A> método em cada <xref:System.Windows.Controls.ValidationRule> que tem <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> definido como <xref:System.Windows.Controls.ValidationStep.UpdatedValue> até que um deles seja executado em um erro ou até que todos eles passem. Se um <xref:System.Windows.Controls.DataErrorValidationRule> está associado com uma associação e sua <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> é definido como o padrão <xref:System.Windows.Controls.ValidationStep.UpdatedValue>, o <xref:System.Windows.Controls.DataErrorValidationRule> é verificada neste momento. Isso também é o ponto quando associações que tenham o <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A> definido como `true` são verificadas.  
  
6.  O mecanismo de associação verifica se há qualquer personalizado <xref:System.Windows.Controls.ValidationRule> objetos definidos cuja <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> é definido como <xref:System.Windows.Controls.ValidationStep.CommittedValue> para fazer isso <xref:System.Windows.Data.Binding>, caso em que ele chama o <xref:System.Windows.Controls.ValidationRule.Validate%2A> método em cada <xref:System.Windows.Controls.ValidationRule> que tem <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> definido como <xref:System.Windows.Controls.ValidationStep.CommittedValue> até que um deles seja executado em um erro ou até que todos eles passem.  
  
 Se um <xref:System.Windows.Controls.ValidationRule> não passa a qualquer momento durante este processo, o mecanismo de associação cria um <xref:System.Windows.Controls.ValidationError> do objeto e adiciona-o para o <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> coleção do elemento associado. Antes da associação de mecanismo é executado o <xref:System.Windows.Controls.ValidationRule> objetos em qualquer determinada etapa, ele remove qualquer <xref:System.Windows.Controls.ValidationError> que foi adicionado para o <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> anexado a propriedade do elemento associado durante esta etapa. Por exemplo, se um <xref:System.Windows.Controls.ValidationRule> cujos <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> é definido como <xref:System.Windows.Controls.ValidationStep.UpdatedValue> falhou na próxima vez em que o processo de validação ocorre, o mecanismo de associação remove que <xref:System.Windows.Controls.ValidationError> imediatamente antes ele chama qualquer <xref:System.Windows.Controls.ValidationRule> que tem <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> definido como <xref:System.Windows.Controls.ValidationStep.UpdatedValue>.  
  
 Quando <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> não está vazio, o <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada do elemento é definida como `true`. Além disso, se o <xref:System.Windows.Data.Binding.NotifyOnValidationError%2A> propriedade do <xref:System.Windows.Data.Binding> é definido como `true`, em seguida, o mecanismo de associação aciona o <xref:System.Windows.Controls.Validation.Error?displayProperty=nameWithType> anexado a eventos no elemento.  
  
 Observe também que uma transferência de valor válida em qualquer direção (destino para origem ou destino) limpa o <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> propriedade anexada.  
  
 Se a associação tem um <xref:System.Windows.Controls.ExceptionValidationRule> associados a ele ou teve a <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> estiver definida como `true` e uma exceção é lançada quando o mecanismo de associação define a origem, o mecanismo de associação verifica para ver se há um <xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A>. Você tem a opção de usar o <xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A> retorno de chamada para fornecer um manipulador personalizado para lidar com exceções. Se um <xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A> não for especificado na <xref:System.Windows.Data.Binding>, o mecanismo de associação cria um <xref:System.Windows.Controls.ValidationError> com a exceção e adiciona-o para o <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> coleção do elemento associado.  
  
## <a name="debugging-mechanism"></a>Mecanismo de depuração  
 Você pode definir a propriedade anexada <xref:System.Diagnostics.PresentationTraceSources.TraceLevel%2A?displayProperty=nameWithType> em um objeto associativo para receber informações sobre o status de uma associação específica.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Controls.DataErrorValidationRule>  
 [Novidades no WPF versão 4.5](../../../../docs/framework/wpf/getting-started/whats-new.md)  
 [Associar aos resultados de uma consulta LINQ](../../../../docs/framework/wpf/data/how-to-bind-to-the-results-of-a-linq-query.md)  
 [Associação de dados](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)  
 [Demonstração de associação de dados](https://go.microsoft.com/fwlink/?LinkID=163703)  
 [Tópicos de instruções](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)  
 [Associar a uma fonte de dados ADO.NET](../../../../docs/framework/wpf/data/how-to-bind-to-an-ado-net-data-source.md)
