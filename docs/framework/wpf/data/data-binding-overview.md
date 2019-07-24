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
ms.openlocfilehash: e1fbb46c76fbc729818b6ff24b55c0d18f6b05df
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68400703"
---
# <a name="data-binding-overview"></a>Visão geral da vinculação de dados
A vinculação de dados do [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fornece aos aplicativos uma maneira simples e consistente para apresentar e interagir com os dados. Os elementos podem ser associados a dados de uma variedade de fontes de dados na forma de objetos Common Language Runtime (CLR) [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)]e. <xref:System.Windows.Controls.ContentControl>s como <xref:System.Windows.Controls.ItemsControl> <xref:System.Windows.Controls.ListBox>es como<xref:System.Windows.Controls.ListView> e têm funcionalidade interna para habilitar o estilo flexível de itens de dados individuais ou coleções de itens de dados. <xref:System.Windows.Controls.Button> É possível gerar exibições com classificação, filtragem e agrupamento dos dados.  
  
 A funcionalidade de vinculação de dados no [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tem várias vantagens sobre modelos tradicionais, incluindo uma ampla gama de propriedades que herdam suporte a vinculação de dados, representação de dados de [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] flexível e separação clara entre a lógica de negócios e a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
 Este tópico aborda primeiro os conceitos fundamentais para [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a vinculação de dados e, em seguida, entra <xref:System.Windows.Data.Binding> no uso da classe e de outros recursos de vinculação de dados.  

<a name="what_is_data_binding"></a>   
## <a name="what-is-data-binding"></a>O que é a vinculação de dados?  
 Vinculação de dados é o processo que estabelece uma conexão entre a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] e a lógica de negócios do aplicativo. Se a associação tiver as configurações corretas e os dados fornecerem notificações adequadas, os elementos associados aos dados refletirão automaticamente quaisquer alterações que venham a ocorrer no valor desses dados. A vinculação de dados também poderá significar que, se houver uma alteração de uma representação externa dos dados em um elemento, os dados subjacentes poderão ser atualizados automaticamente para refletir essa alteração. Por exemplo, se o usuário editar o valor em um <xref:System.Windows.Controls.TextBox> elemento, o valor dos dados subjacentes será atualizado automaticamente para refletir essa alteração.  
  
 Um uso típico da vinculação de dados é colocar dados de configuração local ou do servidor em formulários ou outros controles de [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. No [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], este conceito é expandido para incluir a associação de um amplo espectro de propriedades a uma variedade de fontes de dados. No [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], as propriedades de dependência de elementos podem ser associadas a objetos CLR (incluindo objetos ADO.net ou objetos associados a serviços Web e propriedades da [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] Web) e dados.  
  
 Para um exemplo de vinculação de dados, dê uma olhada na seguinte [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] de aplicativo do [Data Binding Demo](https://go.microsoft.com/fwlink/?LinkID=163703):  
  
 ![Captura de tela de exemplo de vinculação de dados](./media/databinding-databindingdemo.png "DataBinding_DataBindingDemo")  
  
 Acima, a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] de um aplicativo que exibe uma lista de itens de leilão. O aplicativo demonstra os seguintes recursos de vinculação de dados:  
  
- O conteúdo do <xref:System.Windows.Controls.ListBox> está associado a uma coleção de objetos *AuctionItem* . Um objeto *AuctionItem* tem propriedades como *Description*, *StartPrice*, *StartDate*, *Category*, *SpecialFeatures*, etc.  
  
- Os dados (objetos*AuctionItem* ) exibidos no <xref:System.Windows.Controls.ListBox> são modelados de forma que a descrição e o preço atual sejam mostrados para cada item. Isso é feito usando um <xref:System.Windows.DataTemplate>. Além disso, a aparência de cada item depende do valor de *SpecialFeatures* do *AuctionItem* sendo exibido. Se o valor *SpecialFeatures* do *AuctionItem* for *Color*, o item terá uma borda azul. Se o valor for *Highlight*, o item terá uma borda laranja e uma estrela. A seção [Modelos de dados](#data_templating) fornece informações sobre modelagem de dados.  
  
- O usuário pode agrupar, filtrar ou classificar os dados usando os <xref:System.Windows.Controls.CheckBox>es fornecidos. Na imagem acima, os es "Agrupar por categoria" e "classificar por categoria e data" <xref:System.Windows.Controls.CheckBox>são selecionados. Você talvez tenha observado que os dados estão agrupados com base na categoria do produto e que o nome da categoria está em ordem alfabética. É difícil perceber isto na imagem, mas os itens também são classificados por data de início dentro de cada categoria. Isso é feito usando uma *exibição de coleção*. A seção [Associar a coleções](#binding_to_collections) discute exibições de coleções.  
  
- Quando o usuário seleciona um item, <xref:System.Windows.Controls.ContentControl> exibe os detalhes do item selecionado. Isso é chamado de *cenário de Mestre/Detalhes*. A seção [cenário de Mestre/Detalhes](#master_detail_scenario) fornece informações sobre esse tipo de cenário de associação.  
  
- O tipo da propriedade *StartDate* é <xref:System.DateTime>, que retorna uma data que inclui a hora para o milissegundo. Neste aplicativo, um conversor personalizado foi utilizado para que uma cadeia de caracteres de data menor fosse exibida. A seção [Conversão de dados](#data_conversion) fornece informações sobre conversores.  
  
 Quando o usuário clica no botão *Adicionar produto*, o seguinte formulário aparece:  
  
 ![página Adicionar Listagem de Produtos](./media/databinding-demo-addproductlisting.png "DataBinding_Demo_AddProductListing")  
  
 O usuário pode editar os campos no formulário, visualizar a listagem de produtos usando a visualização rápida e os painéis de visualização mais detalhados e, em seguida, clicar em *enviar* para adicionar a nova listagem de produtos. Quaisquer funcionalidades de agrupamento, filtragem e classificação existentes serão aplicadas à nova entrada. Neste caso em particular, o item inserido na imagem acima será exibido como o segundo item dentro da categoria *Computador*.  
  
 Não mostrada nesta imagem é a lógica de validação fornecida na *Data* <xref:System.Windows.Controls.TextBox>de início. Se o usuário inserir uma data inválida (formatação inválida ou uma data anterior), o usuário será notificado <xref:System.Windows.Controls.ToolTip> com um e um ponto de exclamação vermelho ao <xref:System.Windows.Controls.TextBox>lado do. A seção [Validação de dados](#data_validation) discute como criar lógica de validação.  
  
 Antes de discutir em detalhes os diferentes recursos de vinculação de dados descritos acima, discutiremos na próxima seção os conceitos fundamentais que são críticos para o entendimento da vinculação de dados do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
## <a name="basic-data-binding-concepts"></a>Conceitos básicos de vinculação de dados  
  
 Independentemente de qual elemento você está associando e da natureza da fonte de dados, cada associação segue o modelo ilustrado pela figura a seguir:  
  
 ![Diagrama que mostra o modelo básico de ligação de dados.](./media/data-binding-overview/basic-data-binding-diagram.png)  
  
 Conforme ilustrado na figura anterior, vinculação de dados é essencialmente a ponte entre o destino da associação e a origem da associação. A figura demonstra os seguintes conceitos fundamentais de vinculação de dados do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]:  
  
- Normalmente, cada associação tem estes quatro componentes: um objeto de destino da associação, uma propriedade de destino, uma origem da associação e um caminho para o valor na origem da associação a utilizar. Por exemplo, se você quiser associar o conteúdo de <xref:System.Windows.Controls.TextBox> um à propriedade *Name* de um objeto *Employee* , o objeto de destino será o <xref:System.Windows.Controls.TextBox>, a Propriedade Target será a <xref:System.Windows.Controls.TextBox.Text%2A> Propriedade, o valor a ser usado será *Name*e o o objeto de origem é o objeto *Employee* .  
  
- A propriedade de destino deve ser uma propriedade de dependência. A <xref:System.Windows.UIElement> maioria das propriedades são propriedades de dependência e a maioria das propriedades de dependência, exceto somente leitura, dá suporte à associação de dados por padrão. (Somente <xref:System.Windows.DependencyObject> tipos podem definir propriedades de dependência e <xref:System.Windows.UIElement>todas as s <xref:System.Windows.DependencyObject>derivam de.)  
  
- Embora não seja especificado na figura, deve-se observar que o objeto de origem da associação não está restrito a ser um objeto CLR personalizado. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]a vinculação de dados dá suporte a dados na forma de [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]objetos CLR e. Para fornecer alguns exemplos, sua fonte de associação pode ser <xref:System.Windows.UIElement>um, qualquer objeto de lista, um objeto CLR associado a dados de ADO.net ou Web Services, ou um XmlNode que contém [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] seus dados. Para obter mais informações, consulte [Visão geral de origens da associação](binding-sources-overview.md).  
  
 Conforme você lê outros tópicos do [!INCLUDE[TLA#tla_sdk](../../../../includes/tlasharptla-sdk-md.md)], é importante lembrar que quando você está estabelecendo uma associação, você está associando um destino da associação *a* uma origem da associação. Por exemplo, se você estiver exibindo alguns [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] dados subjacentes <xref:System.Windows.Controls.ListBox> em um usando Associação de dados, você <xref:System.Windows.Controls.ListBox> [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] está ligando seus aos dados.  
  
 Para estabelecer uma associação, use o <xref:System.Windows.Data.Binding> objeto. O restante deste tópico aborda muitos dos conceitos associados a e algumas das propriedades e do uso do <xref:System.Windows.Data.Binding> objeto.  
  
<a name="direction_of_data_flow"></a>   
### <a name="direction-of-the-data-flow"></a>Direção do fluxo de dados  
 Conforme mencionado anteriormente e, conforme indicado pela seta na figura acima, o fluxo de dados de uma associação pode ir do destino de associação para a fonte de associação (por exemplo, o valor de origem é alterado quando um usuário edita o valor <xref:System.Windows.Controls.TextBox>de a) e/ou da origem da Associação para o destino de associação (por exemplo, <xref:System.Windows.Controls.TextBox> seu conteúdo é atualizado com alterações na fonte de associação) se a fonte de associação fornecer as notificações adequadas.  
  
 Convém que seu aplicativo permita aos usuários alterar os dados e propagá-los de volta para o objeto de origem. Ou talvez você não queira permitir que os usuários atualizem os dados de origem. Você pode controlar isso definindo a <xref:System.Windows.Data.Binding.Mode%2A> Propriedade do seu <xref:System.Windows.Data.Binding> objeto. A figura a seguir ilustra os diferentes tipos de fluxo de dados:  
  
 ![Fluxo de dados de vinculação de dados](./media/databinding-dataflow.png "DataBinding_DataFlow")  
  
- <xref:System.Windows.Data.BindingMode.OneWay>a associação faz com que as alterações na propriedade de origem atualizem automaticamente a propriedade de destino, mas as alterações na propriedade de destino não são propagadas de volta para a propriedade de origem. Esse tipo de associação será apropriado se o controle associado for somente leitura de forma implícita. Por exemplo, você pode associar a uma origem como uma cotação da bolsa ou talvez a propriedade de destino não tenha nenhuma interface de controle disponível para fazer alterações, como uma cor da tela de fundo associada a dados de uma tabela. Se não houver necessidade de monitorar as alterações da propriedade de destino, o uso do modo de associação <xref:System.Windows.Data.BindingMode.OneWay> evitará a sobrecarga do modo de associação <xref:System.Windows.Data.BindingMode.TwoWay>.  
  
- <xref:System.Windows.Data.BindingMode.TwoWay>a associação faz com que as alterações sejam feitas na propriedade Source ou na propriedade de destino para atualizar automaticamente a outra. Esse tipo de associação é apropriado para formulários editáveis ou outros cenários [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] totalmente interativos. A maioria das propriedades <xref:System.Windows.Data.BindingMode.OneWay> assume a associação como padrão, mas algumas propriedades de dependência (normalmente Propriedades de controles editáveis pelo <xref:System.Windows.Controls.TextBox> usuário, <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> como a <xref:System.Windows.Controls.CheckBox> <xref:System.Windows.Controls.TextBox.Text%2A> propriedade de e a propriedade de) são padrão para <xref:System.Windows.Data.BindingMode.TwoWay> associação. Uma maneira programática de determinar se uma propriedade de dependência é associada de forma unidirecional ou bidirecional por padrão é obter os metadados de propriedade da propriedade usando <xref:System.Windows.DependencyProperty.GetMetadata%2A> e verificar o valor booliano da propriedade <xref:System.Windows.FrameworkPropertyMetadata.BindsTwoWayByDefault%2A>.  
  
- <xref:System.Windows.Data.BindingMode.OneWayToSource>é o inverso <xref:System.Windows.Data.BindingMode.OneWay> da Associação; ele atualiza a propriedade Source quando a propriedade de destino é alterada. Um cenário exemplo é se você só precisa reavaliar o valor da origem da [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
- Não ilustrado na figura está <xref:System.Windows.Data.BindingMode.OneTime> a associação, que faz com que a propriedade Source inicialize a propriedade de destino, mas as alterações subsequentes não se propaguem. Isso significa que se o contexto de dados sofrer uma mudança ou o objeto no contexto de dados for alterado, a alteração não será refletida na propriedade de destino. Esse tipo de associação será apropriado se você estiver usando dados em que um instantâneo do estado atual é apropriado para uso ou os dados forem realmente estáticos. Esse tipo de associação também é útil se você deseja inicializar a propriedade de destino com um valor de uma propriedade de origem e o contexto de dados não é conhecido com antecedência. Este é basicamente uma forma mais simples de associação do <xref:System.Windows.Data.BindingMode.OneWay>, que fornece um melhor desempenho em casos em que o valor de origem não é alterado.  
  
 Observe que para detectar alterações de origem (aplicável <xref:System.Windows.Data.BindingMode.OneWay> às <xref:System.Windows.Data.BindingMode.TwoWay> associações e), a origem deve implementar um mecanismo de notificação de <xref:System.ComponentModel.INotifyPropertyChanged>alteração de propriedade adequado, como. Consulte [implementar notificação de alteração de propriedade](how-to-implement-property-change-notification.md) para obter um <xref:System.ComponentModel.INotifyPropertyChanged> exemplo de uma implementação.  
  
 A <xref:System.Windows.Data.Binding.Mode%2A> página de propriedades fornece mais informações sobre modos de associação e um exemplo de como especificar a direção de uma associação.  
  
<a name="what_triggers_source_updates"></a>   
### <a name="what-triggers-source-updates"></a>O que dispara atualizações de origem  
 Associações que são <xref:System.Windows.Data.BindingMode.TwoWay> ou <xref:System.Windows.Data.BindingMode.OneWayToSource> escutam alterações na propriedade de destino e as propagam de volta para a origem. Isso é conhecido como atualização da origem. Por exemplo, você pode editar o texto de uma caixa de texto para alterar o valor da origem subjacente. Conforme descrito na última seção, a direção do fluxo de dados é determinada pelo valor da <xref:System.Windows.Data.Binding.Mode%2A> propriedade da associação.  
  
 Mas o seu valor de origem é atualizado enquanto você está editando o texto ou após você terminar de editar o texto e apontar o mouse para fora da caixa de texto? A <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> propriedade da Associação determina o que dispara a atualização da origem. Os pontos das setas à direita na figura a seguir ilustram a função da <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> Propriedade:  
  
 ![Diagrama que mostra a função da propriedade UpdateSourceTrigger.](./media/data-binding-overview/data-binding-updatesource-trigger.png)  
  
 Se o <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> valor for <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>, o valor apontado <xref:System.Windows.Data.BindingMode.TwoWay> pela seta para a <xref:System.Windows.Data.BindingMode.OneWayToSource> direita ou pelas associações será atualizado assim que a propriedade de destino for alterada. No entanto, <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> se o <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus>valor for, esse valor só será atualizado com o novo valor quando a propriedade de destino perder o foco.  
  
 Semelhante à propriedade <xref:System.Windows.Data.Binding.Mode%2A> , diferentes propriedades de dependência têm valores padrão <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> diferentes. O valor padrão para a maioria das propriedades de dependência é <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>, enquanto a propriedade <xref:System.Windows.Controls.TextBox.Text%2A> tem um valor padrão de <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus>. Isso significa que as atualizações de origem geralmente ocorrem sempre que a propriedade de destino é alterada <xref:System.Windows.Controls.CheckBox>, o que é bom para es e outros controles simples. No entanto, para campos de texto, atualizar após cada pressionamento de tecla pode diminuir o desempenho e impede a oportunidade rotineira de voltar e corrigir erros de digitação antes de confirmar o novo valor. É por isso que <xref:System.Windows.Controls.TextBox.Text%2A> a propriedade tem um valor padrão <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus> de em <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>vez de.  
  
 Consulte a <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> página de propriedades para obter informações sobre como localizar o <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> valor padrão de uma propriedade de dependência.  
  
 A tabela a seguir fornece um cenário de exemplo <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> para cada valor <xref:System.Windows.Controls.TextBox> usando o como exemplo:  
  
|Valor de UpdateSourceTrigger|Quando o valor de origem é atualizado|Cenário de exemplo de caixa de texto|  
|-------------------------------|----------------------------------------|----------------------------------|  
|LostFocus (padrão para <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType>)|Quando o controle da caixa de texto perde o foco|Um <xref:System.Windows.Controls.TextBox> que está associado à lógica de validação (consulte a seção validação de dados)|  
|PropertyChanged|Conforme você digita no<xref:System.Windows.Controls.TextBox>|<xref:System.Windows.Controls.TextBox>controles em uma janela de sala de chat|  
|Explícito|Quando o aplicativo chama<xref:System.Windows.Data.BindingExpression.UpdateSource%2A>|<xref:System.Windows.Controls.TextBox>controles em um formulário editável (atualiza os valores de origem somente quando o usuário clica no botão enviar)|  
  
 Para obter um exemplo, consulte [Controlar quando o texto da caixa de texto atualiza a origem](how-to-control-when-the-textbox-text-updates-the-source.md).  
  
<a name="creating_a_binding"></a>   
## <a name="creating-a-binding"></a>Criar uma associação  
  
 Para recapitulate alguns dos conceitos discutidos nas seções anteriores, você estabelece uma associação usando o <xref:System.Windows.Data.Binding> objeto e cada associação geralmente tem quatro componentes: destino de associação, propriedade de destino, fonte de associação e um caminho para o valor de origem a ser usado. Esta seção discute como configurar uma associação.  
  
 Considere o exemplo a seguir, no qual o objeto de origem da associação é uma classe chamada *MyData* que é definida no namespace *SDKSample*. Para fins de demonstração, a classe *MyData* tem uma propriedade de cadeia de caracteres denominada *ColorName*, por meio da qual o valor é definido como "Red" (vermelho). Assim, esse exemplo gera um botão com uma tela de fundo vermelha.  
  
 [!code-xaml[BindNonTextProperty#1](~/samples/snippets/csharp/VS_Snippets_Wpf/BindNonTextProperty/CS/Page1.xaml#1)]  
  
 Para obter mais detalhes sobre a sintaxe de declaração de associação e para obter exemplos de como definir uma associação no código, consulte [Visão geral das declarações de associação](binding-declarations-overview.md).  
  
 Se nós aplicarmos esse exemplo a nosso diagrama básico, a figura resultante será semelhante à exibida a seguir. Essa é uma <xref:System.Windows.Data.BindingMode.OneWay> Associação porque a propriedade Background dá <xref:System.Windows.Data.BindingMode.OneWay> suporte à associação por padrão.  
  
 ![Diagrama que mostra a propriedade de plano de fundo de ligação de dados.](./media/data-binding-overview/data-binding-button-background-example.png)  
  
 Você pode imaginar por que isso funciona, embora  a propriedade colorname seja do tipo cadeia de <xref:System.Windows.Controls.Control.Background%2A> caracteres enquanto a propriedade <xref:System.Windows.Media.Brush>for do tipo. Trata-se da conversão de tipo padrão em operação, a qual é abordada na seção [Conversão de dados](#data_conversion).  
  
<a name="specifying_the_binding_source"></a>   
### <a name="specifying-the-binding-source"></a>Especificar a origem da associação  
 Observe que, no exemplo anterior, a origem da associação é especificada definindo a <xref:System.Windows.FrameworkElement.DataContext%2A> propriedade <xref:System.Windows.Controls.DockPanel> no elemento. Em <xref:System.Windows.Controls.Button> seguida, o <xref:System.Windows.FrameworkElement.DataContext%2A> herda o valor <xref:System.Windows.Controls.DockPanel>de, que é seu elemento pai. Para reiterar, o objeto de origem da associação é um dos quatro componentes necessários de uma associação. Portanto, sem o objeto de origem de associação que está sendo especificado, a associação não faria nada.  
  
 Há várias maneiras para especificar o objeto de origem de associação. O uso <xref:System.Windows.FrameworkElement.DataContext%2A> da propriedade em um elemento pai é útil quando você está associando várias propriedades à mesma fonte. No entanto, às vezes pode ser mais apropriado especificar a origem da associação em declarações de associação individuais. Para o exemplo anterior, em vez de usar <xref:System.Windows.FrameworkElement.DataContext%2A> a propriedade, você pode especificar a origem da Associação definindo <xref:System.Windows.Data.Binding.Source%2A> a propriedade diretamente na declaração de associação do botão, como no exemplo a seguir:  
  
 [!code-xaml[BindNonTextProperty#BackgroundBindingCompact](~/samples/snippets/csharp/VS_Snippets_Wpf/BindNonTextProperty/CS/Page2.xaml#backgroundbindingcompact)]  
  
 Além de definir a <xref:System.Windows.FrameworkElement.DataContext%2A> Propriedade em um elemento diretamente, herdando o <xref:System.Windows.FrameworkElement.DataContext%2A> valor de um ancestral (como o botão no primeiro exemplo) e especificando explicitamente a origem da associação, definindo a <xref:System.Windows.Data.Binding.Source%2A> Propriedade no <xref:System.Windows.Data.Binding> (como o botão o último exemplo), você também pode usar a <xref:System.Windows.Data.Binding.ElementName%2A> propriedade ou a <xref:System.Windows.Data.Binding.RelativeSource%2A> propriedade para especificar a origem da associação. A <xref:System.Windows.Data.Binding.ElementName%2A> propriedade é útil quando você está ligando a outros elementos em seu aplicativo, como quando você está usando um controle deslizante para ajustar a largura de um botão. A <xref:System.Windows.Data.Binding.RelativeSource%2A> propriedade é útil quando a associação é especificada em um <xref:System.Windows.Controls.ControlTemplate> ou um <xref:System.Windows.Style>. Para obter mais informações, consulte [Especificar a origem da associação](how-to-specify-the-binding-source.md).  
  
<a name="specifying_the_path_to_the_value"></a>   
### <a name="specifying-the-path-to-the-value"></a>Especificar o caminho para o valor  
 Se sua fonte de associação for um objeto, você usará a <xref:System.Windows.Data.Binding.Path%2A> propriedade para especificar o valor a ser usado para sua associação. Se você estiver ligando a [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] dados, use a <xref:System.Windows.Data.Binding.XPath%2A> propriedade para especificar o valor. Em alguns casos, pode ser aplicável usar a <xref:System.Windows.Data.Binding.Path%2A> Propriedade mesmo quando seus dados estiverem. [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] Por exemplo, se você quiser acessar a propriedade Name de um XMLNode retornado (como resultado de uma consulta XPath), deverá usar a <xref:System.Windows.Data.Binding.Path%2A> Propriedade além da <xref:System.Windows.Data.Binding.XPath%2A> propriedade.  
  
 Para obter informações de sintaxe e exemplos, <xref:System.Windows.Data.Binding.Path%2A> consulte <xref:System.Windows.Data.Binding.XPath%2A> as páginas de propriedades e.  
  
 Observe que, embora tenhamos enfatizado que o <xref:System.Windows.Data.Binding.Path%2A> para o valor a ser usado é um dos quatro componentes necessários de uma associação, nos cenários que você deseja associar a um objeto inteiro, o valor a ser usado seria o mesmo que o objeto de origem da associação. Nesses casos, é aplicável não especificar um <xref:System.Windows.Data.Binding.Path%2A>. Considere o exemplo a seguir:  
  
 [!code-xaml[MasterDetail#EmptyBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/MasterDetail/CSharp/Page1.xaml#emptybinding)]  
  
 O exemplo acima usa a sintaxe de associação vazia: {Binding}. Nesse caso, o <xref:System.Windows.Controls.ListBox> herda o DataContext de um elemento DockPanel pai (não mostrado neste exemplo). Quando o caminho não é especificado, o padrão é associar ao objeto inteiro. Em outras palavras, neste exemplo, o caminho saiu porque estamos associando a <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> Propriedade ao objeto inteiro. (Consulte a seção [Associar a coleções](#binding_to_collections) para uma discussão aprofundada.)  
  
 Além de ao associar a uma coleção, este cenário também é útil quando você deseja associar a um objeto inteiro em vez de apenas uma única propriedade de um objeto. Por exemplo, o objeto de origem é do tipo cadeia de caracteres e você quer simplesmente associar à própria cadeia de caracteres. Outro cenário comum é quando você deseja associar um elemento a um objeto com várias propriedades.  
  
 Observe que talvez seja necessário aplicar uma lógica personalizada para que os dados sejam significativos para a propriedade de destino associada. A lógica personalizada poderá ser na forma de um conversor personalizado (se a conversão de tipo padrão não existir). Para obter mais informações sobre conversores, consulte [Conversão de dados](#data_conversion).  
  
<a name="binding_bindingexpression"></a>   
### <a name="binding-and-bindingexpression"></a>Associação e BindingExpression  
 Antes de entrar em outros recursos e usos da vinculação de dados, seria útil introduzir a <xref:System.Windows.Data.BindingExpression> classe. Como você viu nas seções anteriores, a <xref:System.Windows.Data.Binding> classe é a classe de alto nível para a declaração de uma associação; a <xref:System.Windows.Data.Binding> classe fornece muitas propriedades que permitem que você especifique as características de uma associação. Uma classe relacionada, <xref:System.Windows.Data.BindingExpression>, é o objeto subjacente que mantém a conexão entre a origem e o destino. Uma associação contém todas as informações que podem ser compartilhadas entre várias expressões de associação. Um <xref:System.Windows.Data.BindingExpression> é uma expressão <xref:System.Windows.Data.Binding>de instância que não pode ser compartilhada e contém todas as informações de instância do.  
  
 Por exemplo, considere o seguinte, em  que myDataObject é uma instância da classe MyData, myBinding é <xref:System.Windows.Data.Binding> o objeto de origem e a classe MyData é uma classe definida que contém uma propriedade de cadeia de caracteres chamada    MyDataProperty. Este exemplo associa o conteúdo de texto de *MyText*, uma instância de <xref:System.Windows.Controls.TextBlock>, a MyDataProperty.  
  
 [!code-csharp[CodeOnlyBinding#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#1)]
 [!code-vb[CodeOnlyBinding#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#1)]  
  
 Você pode usar o mesmo objeto *myBinding* para criar outras associações. Por exemplo, você pode usar o objeto *myBinding* para associar o conteúdo de texto de uma caixa de seleção a *MyDataProperty*. Nesse cenário, haverá duas instâncias de <xref:System.Windows.Data.BindingExpression> compartilhamento do objeto myBinding.  
  
 Um <xref:System.Windows.Data.BindingExpression> objeto pode ser obtido por meio do valor de retorno <xref:System.Windows.Data.BindingOperations.GetBindingExpression%2A> de chamada em um objeto associado a dados. Os tópicos a seguir demonstram alguns dos usos da <xref:System.Windows.Data.BindingExpression> classe:  
  
- [Obter o objeto de associação de uma propriedade de destino associada](how-to-get-the-binding-object-from-a-bound-target-property.md)  
  
- [Controlar quando o texto da caixa de texto atualiza a origem](how-to-control-when-the-textbox-text-updates-the-source.md)  
  
<a name="data_conversion"></a>   
## <a name="data-conversion"></a>Conversão de dados  
 No exemplo anterior, o botão é vermelho porque sua <xref:System.Windows.Controls.Control.Background%2A> Propriedade está associada a uma propriedade de cadeia de caracteres com o valor "Red". Isso funciona porque um conversor de tipo está presente no <xref:System.Windows.Media.Brush> tipo para converter o valor da cadeia de <xref:System.Windows.Media.Brush>caracteres em um.  
  
 Para adicionar essas informações à figura na seção [Criando uma associação](#creating_a_binding), o diagrama é semelhante ao seguinte:  
  
 ![Diagrama que mostra a propriedade padrão de associação de dados.](./media/data-binding-overview/data-binding-button-default-conversion.png)  
  
 No entanto, e se, em vez de ter uma propriedade do tipo String, seu  objeto de origem de <xref:System.Windows.Media.Color>associação tiver uma Propriedade Color do tipo? Nesse caso, para que a ligação funcione, você precisaria primeiro transformar o valor da propriedade *Color* em algo que a <xref:System.Windows.Controls.Control.Background%2A> Propriedade aceite. Você precisaria criar um conversor personalizado implementando a <xref:System.Windows.Data.IValueConverter> interface, como no exemplo a seguir:  
  
 [!code-csharp[ColorPicker_snip#16](~/samples/snippets/csharp/VS_Snippets_Wpf/ColorPicker_snip/CSharp/ColorPickerLib/ColorPicker.cs#16)]
 [!code-vb[ColorPicker_snip#16](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ColorPicker_snip/visualbasic/colorpickerlib/colorpicker.vb#16)]  
  
 A <xref:System.Windows.Data.IValueConverter> página de referência fornece mais informações.  
  
 Agora o conversor personalizado é usado no lugar da conversão padrão e nosso diagrama fica assim:  
  
 ![Diagrama que mostra o conversor personalizado de vinculação de dados.](./media/data-binding-overview/data-binding-converter-color-example.png)  
  
 Para reiterar, conversões padrão podem estar disponíveis devido a conversores de tipo presentes no tipo para o qual a associação está sendo realizada. Esse comportamento dependerá de quais conversores de tipo estão disponíveis no destino. Em caso de dúvida, crie seu próprio conversor.  
  
 A seguir estão alguns cenários típicos em que faz sentido implementar um conversor de dados:  
  
- Os dados devem ser exibidos de forma diferente, dependendo da cultura. Por exemplo, você talvez queira implementar um conversor de moeda ou um conversor de data do calendário/hora com base nos valores ou padrões utilizados em uma cultura específica.  
  
- Os dados que está sendo usados não são necessariamente destinados a alterar o valor de texto de uma propriedade, mas sim destinados a alterar alguns outros valores como a origem de uma imagem ou então a cor ou o estilo do texto. Conversores podem ser usados nesta instância convertendo a associação de uma propriedade que pode não parecer apropriada, assim como a associação de um campo de texto à propriedade Background de uma célula de tabela.  
  
- Mais de um controle ou múltiplas propriedades de controles são vinculados aos mesmos dados. Nesse caso, a associação primária pode simplesmente exibir o texto, enquanto outras associações lidam com questões específicas de exibição, mas ainda usam a mesma associação como informações da origem.  
  
- Até agora, ainda não discutimos <xref:System.Windows.Data.MultiBinding>, em que uma propriedade de destino tem uma coleção de associações. No caso de um <xref:System.Windows.Data.MultiBinding>, você usa um personalizado <xref:System.Windows.Data.IMultiValueConverter> para produzir um valor final dos valores das associações. Por exemplo, a cor pode ser computada de valores vermelhos, azuis e verdes, que podem ser valores dos mesmos ou de diferentes objetos de origem da associação. Consulte a <xref:System.Windows.Data.MultiBinding> página de classe para obter exemplos e informações.  
  
<a name="binding_to_collections"></a>   
## <a name="binding-to-collections"></a>Associar a coleções  
  
 Um objeto de origem de associação pode ser tratado como um único objeto do qual as propriedades contêm dados ou como uma coleção de objetos polimórficos que são frequentemente agrupados juntos (como o resultado de uma consulta a um banco de dados). Até agora só discutimos a associação a objetos individuais, no entanto, a associação a uma coleção de dados é um cenário comum. Por exemplo, um cenário <xref:System.Windows.Controls.ItemsControl> comum é usar <xref:System.Windows.Controls.ListBox>um, <xref:System.Windows.Controls.ListView>ou <xref:System.Windows.Controls.TreeView> para exibir uma coleção de dados, como no aplicativo mostrado na seção [o que é a vinculação de dados?](#what_is_data_binding) .  
  
 Felizmente, nosso diagrama básico ainda se aplica. Se você estiver associando <xref:System.Windows.Controls.ItemsControl> um a uma coleção, o diagrama terá esta aparência:  
  
 ![Diagrama que mostra o objeto ItemsControl de vinculação de dados.](./media/data-binding-overview/data-binding-itemscontrol.png)  
  
 Conforme mostrado neste diagrama, para associar um <xref:System.Windows.Controls.ItemsControl> a um objeto de coleção, <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> a propriedade é a propriedade a ser usada. Você pode considerar <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> a propriedade como o conteúdo <xref:System.Windows.Controls.ItemsControl>do. Observe que a associação é <xref:System.Windows.Data.BindingMode.OneWay> porque a <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> Propriedade dá <xref:System.Windows.Data.BindingMode.OneWay> suporte à associação por padrão.  
  
<a name="how_to_implement_collections"></a>   
### <a name="how-to-implement-collections"></a>Como implementar coleções  
 Você pode enumerar em qualquer coleção que implemente a <xref:System.Collections.IEnumerable> interface. No entanto, para configurar associações dinâmicas para que as inserções ou exclusões na coleção atualizem [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] o automaticamente, a coleção deve implementar <xref:System.Collections.Specialized.INotifyCollectionChanged> a interface. Essa interface expõe um evento que deve ser acionado sempre que a coleção subjacente for alterada.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]fornece a <xref:System.Collections.ObjectModel.ObservableCollection%601> classe, que é uma implementação interna de uma coleção de dados que expõe a <xref:System.Collections.Specialized.INotifyCollectionChanged> interface. Observe que para oferecer suporte total à transferência de valores de dados de objetos de origem para destinos, cada objeto em sua coleção que dá suporte <xref:System.ComponentModel.INotifyPropertyChanged> a propriedades vinculáveis também deve implementar a interface. Para obter mais informações, consulte [Visão geral de origens da associação](binding-sources-overview.md).  
  
 Antes de implementar sua própria coleção, considere <xref:System.Collections.ObjectModel.ObservableCollection%601> usar ou uma das classes de coleção existentes, <xref:System.Collections.Generic.List%601>como <xref:System.Collections.ObjectModel.Collection%601>, e <xref:System.ComponentModel.BindingList%601>, entre muitas outras. Se você tiver um cenário avançado e quiser implementar sua própria coleção, considere usar <xref:System.Collections.IList>o, que fornece uma coleção não genérica de objetos que podem ser acessados individualmente pelo índice e, portanto, o melhor desempenho.  
  
<a name="collection_views"></a>   
### <a name="collection-views"></a>Exibições de coleção  
 Quando o <xref:System.Windows.Controls.ItemsControl> estiver associado a uma coleção de dados, talvez você queira classificar, filtrar ou agrupar os dados. Para fazer isso, você usa exibições de coleção, que são classes que <xref:System.ComponentModel.ICollectionView> implementam a interface.  

#### <a name="what-are-collection-views"></a>O que são exibições de coleção?  
 Uma exibição de coleção é uma camada sobre uma coleção de origem da associação que permite a você navegar e exibir a coleção de origem com base em consultas de classificação, filtragem e agrupamento, sem precisar alterar a coleção de origem subjacente. Uma exibição de coleção também mantém um ponteiro para o item atual na coleção. Se a coleção de origem implementar <xref:System.Collections.Specialized.INotifyCollectionChanged> a interface, as alterações geradas <xref:System.Collections.Specialized.INotifyCollectionChanged.CollectionChanged> pelo evento serão propagadas para as exibições.  
  
 Já que as exibições não alteram as coleções de origem subjacentes, cada coleção de origem pode ter várias exibições associadas a ela. Por exemplo, você pode ter uma coleção de objetos *Task*. Com o uso de exibições, você pode exibir esses mesmos dados de maneiras diferentes. Por exemplo, no lado esquerdo da página, talvez você queira mostrar as tarefas ordenadas por prioridade e, no lado direito, agrupadas por área.  
  
<a name="how_to_create_a_view"></a>   
#### <a name="how-to-create-a-view"></a>Como criar uma exibição  
 Uma maneira de criar e usar uma exibição é instanciar o objeto de exibição diretamente e então usá-lo como a origem da associação. Por exemplo, considere o aplicativo [Data Binding Demo](https://go.microsoft.com/fwlink/?LinkID=163703) mostrado na seção [O que é vinculação de dados?](#what_is_data_binding). O aplicativo é implementado de modo que <xref:System.Windows.Controls.ListBox> o seja associado a uma exibição sobre a coleta de dados em vez da coleta de dados diretamente. O exemplo a seguir é extraído do aplicativo [Data Binding Demo](https://go.microsoft.com/fwlink/?LinkID=163703). A <xref:System.Windows.Data.CollectionViewSource> classe é o [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] proxy de uma classe que herda de <xref:System.Windows.Data.CollectionView>. Neste exemplo específico, o <xref:System.Windows.Data.CollectionViewSource.Source%2A> da exibição está associado à coleção *AuctionItems* (do tipo <xref:System.Collections.ObjectModel.ObservableCollection%601>) do objeto de aplicativo atual.  
  
 [!code-xaml[DataBindingLab#WindowResources1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#windowresources1)]  
[!code-xaml[DataBindingLab#CollectionViewSource](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#collectionviewsource)]  
[!code-xaml[DataBindingLab#WindowResources2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#windowresources2)]  
  
 O recurso *listingDataView* , em seguida, serve como a fonte de associação para elementos no aplicativo, <xref:System.Windows.Controls.ListBox>como:  
  
 [!code-xaml[DataBindingLab#Master1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#master1)]  
[!code-xaml[DataBindingLab#Master2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#master2)]  
  
 Para criar outra exibição para a mesma coleção, você pode criar outra <xref:System.Windows.Data.CollectionViewSource> instância e dar a ela um `x:Key` nome diferente.  
  
 A tabela a seguir mostra quais tipos de dados de exibição são criados como a exibição de <xref:System.Windows.Data.CollectionViewSource> coleção padrão ou com base no tipo de coleção de origem.  
  
|Tipo de coleção de origem|Tipo de exibição de coleção|Observações|  
|----------------------------|--------------------------|-----------|  
|<xref:System.Collections.IEnumerable>|Um tipo interno baseado em<xref:System.Windows.Data.CollectionView>|Não é possível agrupar itens.|  
|<xref:System.Collections.IList>|<xref:System.Windows.Data.ListCollectionView>|Mais rápido.|  
|<xref:System.ComponentModel.IBindingList>|<xref:System.Windows.Data.BindingListCollectionView>||  
  
##### <a name="using-a-default-view"></a>Usando uma exibição padrão  
 Especificar uma exibição de coleção como uma origem da associação é uma maneira de criar e usar uma exibição de coleção. O WPF também cria uma exibição de coleção padrão para cada coleção usada como uma origem da associação. Se você associar diretamente a uma coleção, o WPF será associado à sua exibição padrão. Observe que essa exibição padrão é compartilhada por todas as associações à mesma coleção, de modo que uma alteração feita a uma exibição padrão por um código ou controle associado (por exemplo, uma classificação ou uma alteração do ponteiro atual do item, discutido posteriormente) será refletida em todas as demais associações à mesma coleção.  
  
 Para obter a exibição padrão, use o <xref:System.Windows.Data.CollectionViewSource.GetDefaultView%2A> método. Para obter um exemplo, consulte [Como obter a exibição padrão de uma coleção de dados](how-to-get-the-default-view-of-a-data-collection.md).  
  
##### <a name="collection-views-with-adonet-datatables"></a>Exibições de coleção com DataTables do ADO.NET  
 Para melhorar o desempenho, as exibições <xref:System.Data.DataTable> de <xref:System.Data.DataView> coleção para ADO.net ou objetos delegam <xref:System.Data.DataView>classificação e filtragem para o. Isso faz com que a classificação e filtragem sejam compartilhadas entre todas as exibições de coleção da fonte de dados. Para habilitar cada exibição de coleção para classificar e filtrar de forma independente, inicialize cada modo de <xref:System.Data.DataView> exibição de coleção com seu próprio objeto.  
  
#### <a name="sorting"></a>Classificação  
 Conforme mencionado anteriormente, as exibições podem aplicar uma ordem de classificação para uma coleção. Já que eles existem na coleção subjacente, seus dados podem ter ou não uma ordem inerente e relevante. A exibição da coleção permite impor uma ordem ou alterar a ordem padrão, com base em critérios de comparação fornecidos por você. Já que essa é uma exibição dos dados baseada no cliente, um cenário comum é que o usuário deseje classificar colunas de dados tabulares segundo o valor ao qual a coluna corresponde. Usando exibições, essa classificação controlada pelo usuário pode ser aplicada, novamente sem necessidade de alterações na coleção subjacente nem mesmo precisar repetir a consulta do conteúdo da coleção. Para obter um exemplo, consulte [Classificar uma coluna GridView quando um cabeçalho é clicado](../controls/how-to-sort-a-gridview-column-when-a-header-is-clicked.md).  
  
 O exemplo a seguir mostra a lógica de classificação de "classificar por categoria e data <xref:System.Windows.Controls.CheckBox> " do aplicativo [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] na seção [o que é Associação de dados?](#what_is_data_binding) :  
  
 [!code-csharp[DataBindingLab#8](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#8)]
 [!code-vb[DataBindingLab#8](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#8)]  
  
#### <a name="filtering"></a>Filtragem  
 Exibições também podem aplicar um filtro a uma coleção. Isso significa que, embora um item possa existir na coleção, essa exibição específica é destinada a mostrar somente um certo subconjunto da coleção inteira. Você pode filtrar por uma condição nos dados. Por exemplo, como é feito pelo aplicativo na seção [o que é a vinculação de dados?](#what_is_data_binding) , "mostrar apenas os itens" <xref:System.Windows.Controls.CheckBox> contém a lógica para filtrar o item que custa $25 ou mais. O código a seguir é executado para definir *ShowOnlyBargainsFilter* como <xref:System.Windows.Data.CollectionViewSource.Filter> o manipulador de <xref:System.Windows.Controls.CheckBox> eventos quando selecionado:  
  
 [!code-csharp[DataBindingLab#10](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#10)]
 [!code-vb[DataBindingLab#10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#10)]  
  
 O manipulador *ShowOnlyBargainsFilter* tem a seguinte implementação:  
  
 [!code-csharp[DataBindingLab#5](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#5)]
 [!code-vb[DataBindingLab#5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#5)]  
  
 Se você estiver usando uma das <xref:System.Windows.Data.CollectionView> classes diretamente em vez de <xref:System.Windows.Data.CollectionViewSource>, você usaria a <xref:System.Windows.Data.CollectionView.Filter%2A> propriedade para especificar um retorno de chamada. Para obter um exemplo, consulte [Filtrar dados em uma exibição](how-to-filter-data-in-a-view.md).  
  
#### <a name="grouping"></a>Agrupamento  
 Exceto para a classe interna que exibe uma <xref:System.Collections.IEnumerable> coleção, todas as exibições de coleção dão suporte à funcionalidade de agrupamento, o que permite ao usuário particionar a coleção no modo de exibição de coleção em grupos lógicos. Os grupos podem ser explícitos (caso em que o usuário fornece uma lista de grupos) ou então implícitos (caso em que os grupos são gerados dinamicamente, dependendo dos dados).  
  
 O exemplo a seguir mostra a lógica da "Agrupar por categoria" <xref:System.Windows.Controls.CheckBox>:  
  
 [!code-csharp[DataBindingLab#6](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#6)]
 [!code-vb[DataBindingLab#6](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#6)]  
  
 Para obter outro exemplo de agrupamento, consulte [Agrupar itens em uma ListView que implementa uma GridView](../controls/how-to-group-items-in-a-listview-that-implements-a-gridview.md).  
  
#### <a name="current-item-pointers"></a>Ponteiros de item atuais  
 As exibições também dão suporte à noção de um item atual. Você pode navegar pelos objetos em uma exibição de coleção. Enquanto você navega, você está movendo um ponteiro de item que permite que você recupere o objeto existente nesse local específico na coleção. Para obter um exemplo, consulte [Navegar pelos objetos em uma CollectionView de dados](how-to-navigate-through-the-objects-in-a-data-collectionview.md).  
  
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
 A noção de um item atual é útil não somente para navegação por itens em uma coleção, mas também para o cenário de associação mestre/detalhes. Considere a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] do aplicativo na seção [O que é vinculação de dados?](#what_is_data_binding) novamente. Nesse aplicativo, a seleção dentro de <xref:System.Windows.Controls.ListBox> determina o conteúdo mostrado <xref:System.Windows.Controls.ContentControl>no. Para colocá-lo de outra maneira, quando <xref:System.Windows.Controls.ListBox> um item é selecionado, <xref:System.Windows.Controls.ContentControl> o mostra os detalhes do item selecionado.  
  
 Você pode implementar o cenário mestre/detalhes simplesmente associando dois ou mais controles à mesma exibição. O exemplo a seguir da [demonstração de vinculação de dados](https://go.microsoft.com/fwlink/?LinkID=163703) mostra a marcação <xref:System.Windows.Controls.ListBox> do e <xref:System.Windows.Controls.ContentControl> o que você vê no [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] aplicativo na seção [o que é a vinculação de dados?](#what_is_data_binding) :  
  
 [!code-xaml[DataBindingLab#Master1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#master1)]  
[!code-xaml[DataBindingLab#Master2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#master2)]  
[!code-xaml[DataBindingLab#Detail](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#detail)]  
  
 Observe que ambos os controles são associados à mesma origem, o recurso estático *listingDataView* (consulte a definição desse recurso na [seção Como criar uma exibição](#how_to_create_a_view)). Isso funciona porque quando um objeto singleton ( <xref:System.Windows.Controls.ContentControl> neste caso) está associado a um modo <xref:System.Windows.Data.CollectionView.CurrentItem%2A> de exibição de coleção, ele automaticamente se vincula ao da exibição. Observe que <xref:System.Windows.Data.CollectionViewSource> os objetos sincronizam automaticamente a moeda e a seleção. Se o controle de lista não estiver associado a <xref:System.Windows.Data.CollectionViewSource> um objeto como neste exemplo, você precisará definir sua <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> Propriedade como `true` para que isso funcione.  
  
 Para obter outros exemplos, consulte [Associar a uma coleção e exibir informações com base na seleção](how-to-bind-to-a-collection-and-display-information-based-on-selection.md) e [Usar o padrão mestre/detalhes com os dados hierárquicos](how-to-use-the-master-detail-pattern-with-hierarchical-data.md).  
  
 Talvez você tenha observado que o exemplo anterior usa um modelo. Na verdade, os dados não seriam exibidos da maneira que desejamos sem o uso de modelos (aquele usado explicitamente pelo <xref:System.Windows.Controls.ContentControl> e aquele usado implicitamente <xref:System.Windows.Controls.ListBox>pelo). Agora, na próxima seção, nos ocuparemos da modelagem de dados.  
  
<a name="data_templating"></a>   
## <a name="data-templating"></a>Modelagem de dados  
 Sem o uso de modelos de dados, nossa [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] do aplicativo na seção [O que é vinculação de dados?](#what_is_data_binding) teria aparência semelhante à seguinte:  
  
 ![Demonstração de vinculação de dados sem modelos de dados](./media/data-binding-overview/data-binding-demo-templates.png)  
  
 Conforme mostrado no exemplo na seção anterior, o <xref:System.Windows.Controls.ListBox> controle e o <xref:System.Windows.Controls.ContentControl> são vinculados a todo o objeto da coleção (ou mais especificamente, a exibição sobre o objeto de coleção) de s *AuctionItem*. Sem instruções específicas de como exibir a coleta de dados, o <xref:System.Windows.Controls.ListBox> está exibindo uma representação de cadeia de caracteres de cada objeto na coleção <xref:System.Windows.Controls.ContentControl> subjacente e o está exibindo uma representação de cadeia de caracteres do objeto ao qual está associado.  
  
 Para resolver esse problema, o aplicativo define <xref:System.Windows.DataTemplate>s. Conforme mostrado no exemplo na seção anterior, o <xref:System.Windows.Controls.ContentControl> usa explicitamente o *detailsProductListingTemplate*<xref:System.Windows.DataTemplate>. O <xref:System.Windows.Controls.ListBox> controle usa implicitamente o seguinte <xref:System.Windows.DataTemplate> ao exibir os objetos *AuctionItem* na coleção:  
  
 [!code-xaml[DataBindingLab#AuctionItemDataTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DataBindingLabApp.xaml#auctionitemdatatemplate)]  
  
 Com o uso desses dois <xref:System.Windows.DataTemplate>s, a interface do usuário resultante é a mostrada na seção [o que é a vinculação de dados?](#what_is_data_binding) . Como você pode ver nessa captura de tela, além de permitir que você coloque dados em seus controles <xref:System.Windows.DataTemplate>, os s permitem que você defina visuais atraentes para seus dados. Por exemplo, <xref:System.Windows.DataTrigger>s são usados no acima <xref:System.Windows.DataTemplate> para que os s de *AuctionItem*com o valor *SpecialFeatures* de realce sejam exibidos com uma borda laranja e uma estrela.  
  
 Para obter mais informações sobre modelos de dados, consulte [Visão geral de modelagem de dados](data-templating-overview.md).  
  
<a name="data_validation"></a>   
## <a name="data-validation"></a>Validação de dados  
  
 A maioria dos aplicativos que usam a entrada do usuário precisam ter lógica de validação para garantir que o usuário tenha inserido as informações esperadas. As verificações de validação podem ser baseadas em tipo, intervalo, formato ou outros requisitos específicos de aplicativo. Esta seção discute como a validação de dados funciona no [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
### <a name="associating-validation-rules-with-a-binding"></a>Associar regras de validação com uma associação  
 O [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] modelo de associação de dados permite que <xref:System.Windows.Data.Binding.ValidationRules%2A> você associe <xref:System.Windows.Data.Binding> com o objeto. Por exemplo, o exemplo a seguir associa um <xref:System.Windows.Controls.TextBox> a uma propriedade chamada `StartPrice` e <xref:System.Windows.Data.Binding.ValidationRules%2A?displayProperty=nameWithType> adiciona um <xref:System.Windows.Controls.ExceptionValidationRule> objeto à propriedade.  
  
 [!code-xaml[DataBindingLab#DefaultValidation](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/AddProductWindow.xaml#defaultvalidation)]  
  
 Um <xref:System.Windows.Controls.ValidationRule> objeto verifica se o valor de uma propriedade é válido. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]o tem os dois tipos de <xref:System.Windows.Controls.ValidationRule> objetos internos a seguir:  
  
- Uma <xref:System.Windows.Controls.ExceptionValidationRule> verificação de exceções geradas durante a atualização da propriedade de origem da associação. No exemplo anterior, `StartPrice` é do tipo inteiro. Quando o usuário insere um valor que não pode ser convertido em um número inteiro, é gerada uma exceção que faz com que a associação seja marcada como inválida. Uma sintaxe alternativa para definir <xref:System.Windows.Controls.ExceptionValidationRule> explicitamente é definir a <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> Propriedade como `true` no seu <xref:System.Windows.Data.Binding> objeto or <xref:System.Windows.Data.MultiBinding> .  
  
- Um <xref:System.Windows.Controls.DataErrorValidationRule> objeto verifica se há erros que são gerados por objetos que implementam a <xref:System.ComponentModel.IDataErrorInfo> interface. Para obter um exemplo de como usar essa regra de <xref:System.Windows.Controls.DataErrorValidationRule>validação, consulte. Uma sintaxe alternativa para definir <xref:System.Windows.Controls.DataErrorValidationRule> explicitamente é definir a <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A> Propriedade como `true` no seu <xref:System.Windows.Data.Binding> objeto or <xref:System.Windows.Data.MultiBinding> .  
  
 Você também pode criar sua própria regra de validação derivando da <xref:System.Windows.Controls.ValidationRule> classe e implementando o <xref:System.Windows.Controls.ValidationRule.Validate%2A> método. O exemplo a seguir mostra a regra usada pela "data <xref:System.Windows.Controls.TextBox> de início" *Adicionar lista de produtos* na seção [o que é Associação de dados?](#what_is_data_binding) :  
  
 [!code-csharp[DataBindingLab#2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/FutureDateRule.cs#2)]
 [!code-vb[DataBindingLab#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/FutureDateRule.vb#2)]  
  
 O *StartDateEntryForm* <xref:System.Windows.Controls.TextBox> usa esse *FutureDateRule*, conforme mostrado no exemplo a seguir:  
  
 [!code-xaml[DataBindingLab#CustomValidation](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/AddProductWindow.xaml#customvalidation)]  
  
 Observe que, como <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> o valor <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>é, o mecanismo de associação atualiza o valor de origem em cada pressionamento de tecla, o que significa <xref:System.Windows.Data.Binding.ValidationRules%2A> que ele também verifica cada regra na coleção em cada pressionamento de tecla. Discutiremos isso de modo mais aprofundado na seção Processo de validação.  
  
<a name="invalidation_feedback"></a>   
### <a name="providing-visual-feedback"></a>Fornecer comentários visuais  
 Se o usuário inserir um valor inválido, talvez você queira fornecer comentários sobre o erro no aplicativo [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. Uma maneira de fornecer esses comentários é definir a <xref:System.Windows.Controls.Validation.ErrorTemplate%2A?displayProperty=nameWithType> Propriedade anexada como um personalizado. <xref:System.Windows.Controls.ControlTemplate> Conforme mostrado na subseção anterior, o *StartDateEntryForm* <xref:System.Windows.Controls.TextBox> usa um <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> chamado *validationTemplate*. O exemplo a seguir mostra a definição de *validationTemplate*:  
  
 [!code-xaml[DataBindingLab#1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/AddProductWindow.xaml#1)]  
  
 O <xref:System.Windows.Controls.AdornedElementPlaceholder> elemento especifica onde o controle que está sendo adornado deve ser colocado.  
  
 Além disso, você também pode usar um <xref:System.Windows.Controls.ToolTip> para exibir a mensagem de erro. O *StartDateEntryForm* e o *StartPriceEntryForm*<xref:System.Windows.Controls.TextBox>es usam o estilo *textStyleTextBox*, que cria um <xref:System.Windows.Controls.ToolTip> que exibe a mensagem de erro. O exemplo a seguir mostra a definição de *textStyleTextBox*. A propriedade <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> anexada `true` é quando uma ou mais das associações nas propriedades do elemento associado estão com erro.  
  
 [!code-xaml[DataBindingLab#14](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DataBindingLabApp.xaml#14)]  
  
 Com o personalizado <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> e o <xref:System.Windows.Controls.ToolTip>, o *StartDateEntryForm* <xref:System.Windows.Controls.TextBox> é semelhante ao seguinte quando há um erro de validação:  
  
 ![Erro de validação de vinculação de dados](./media/databindingdemo-validation.PNG "DataBindingDemo_Validation")  
  
 Se o <xref:System.Windows.Data.Binding> tiver regras de validação associadas, mas você não especificar <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> um no controle ligado, um padrão <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> será usado para notificar os usuários quando houver um erro de validação. O padrão <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> é um modelo de controle que define uma borda vermelha na camada de adorno. Com o padrão <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> e o <xref:System.Windows.Controls.ToolTip>, o [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] de *StartPriceEntryForm* <xref:System.Windows.Controls.TextBox> é semelhante ao seguinte quando há um erro de validação:  
  
 ![Erro de validação de vinculação de dados](./media/databindingdemo-validationdefault.PNG "DataBindingDemo_ValidationDefault")  
  
 Para obter um exemplo de como fornecer a lógica para validar todos os controles em uma caixa de diálogo, consulte a seção Caixas de diálogo personalizadas na [Visão geral das caixas de diálogo](../app-development/dialog-boxes-overview.md).  
  
### <a name="validation-process"></a>Processo de validação  
 Geralmente, a validação ocorre quando o valor de um destino é transferido para a propriedade de origem da associação. Isso ocorre em <xref:System.Windows.Data.BindingMode.TwoWay> associações <xref:System.Windows.Data.BindingMode.OneWayToSource> e. Para reiterar, o que causa uma atualização de origem depende do valor <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> da propriedade, conforme descrito na seção [o que dispara as atualizações de origem](#what_triggers_source_updates) .  
  
 O conteúdo a seguir descreve o processo de *validação*. Observe que, se ocorrer um erro de validação ou outro tipo de erro em qualquer momento durante este processo, o processo será interrompido.  
  
1. O mecanismo de associação verifica se há objetos personalizados <xref:System.Windows.Controls.ValidationRule> definidos cujo <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> conjunto está definido como <xref:System.Windows.Controls.ValidationStep.RawProposedValue> para isso <xref:System.Windows.Data.Binding>; nesse caso, ele chama o <xref:System.Windows.Controls.ValidationRule.Validate%2A> método em cada <xref:System.Windows.Controls.ValidationRule> um até que um deles seja executado em um erro ou até que todos eles passem.  
  
2. O mecanismo de associação então chamará o conversor, se houver.  
  
3. Se o conversor for executado com sucesso, o mecanismo de associação verificará se <xref:System.Windows.Controls.ValidationRule> há objetos personalizados <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> definidos, cujos <xref:System.Windows.Controls.ValidationStep.ConvertedProposedValue> são definidos <xref:System.Windows.Data.Binding>como para isso. nesse caso, <xref:System.Windows.Controls.ValidationRule.Validate%2A> ele chama o <xref:System.Windows.Controls.ValidationRule> método em cada um deles <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> defina como<xref:System.Windows.Controls.ValidationStep.ConvertedProposedValue> até que um deles execute um erro ou até que todos eles passem.  
  
4. O mecanismo de associação define a propriedade de origem.  
  
5. O mecanismo de associação verifica se há objetos personalizados <xref:System.Windows.Controls.ValidationRule> definidos cujo <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> conjunto está definido como <xref:System.Windows.Controls.ValidationStep.UpdatedValue> para isso <xref:System.Windows.Data.Binding>; nesse caso, ele chama o <xref:System.Windows.Controls.ValidationRule.Validate%2A> método em cada <xref:System.Windows.Controls.ValidationRule> um que <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> tenha definido como <xref:System.Windows.Controls.ValidationStep.UpdatedValue> até que um deles seja executado em um erro ou até que todos eles passem. Se um <xref:System.Windows.Controls.DataErrorValidationRule> estiver associado a uma associação e seu <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> estiver definido como o padrão, <xref:System.Windows.Controls.ValidationStep.UpdatedValue>o <xref:System.Windows.Controls.DataErrorValidationRule> será verificado neste ponto. Esse também é o ponto em que as associações que têm <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A> o conjunto `true` como estão marcadas.  
  
6. O mecanismo de associação verifica se há objetos personalizados <xref:System.Windows.Controls.ValidationRule> definidos cujo <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> conjunto está definido como <xref:System.Windows.Controls.ValidationStep.CommittedValue> para isso <xref:System.Windows.Data.Binding>; nesse caso, ele chama o <xref:System.Windows.Controls.ValidationRule.Validate%2A> método em cada <xref:System.Windows.Controls.ValidationRule> um que <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> tenha definido como <xref:System.Windows.Controls.ValidationStep.CommittedValue> até que um deles seja executado em um erro ou até que todos eles passem.  
  
 Se um <xref:System.Windows.Controls.ValidationRule> não passar algum tempo durante todo esse processo, o mecanismo de associação criará <xref:System.Windows.Controls.ValidationError> um objeto e o <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> adicionará à coleção do elemento associado. Antes que o mecanismo de associação <xref:System.Windows.Controls.ValidationRule> execute os objetos em qualquer etapa determinada, ele <xref:System.Windows.Controls.ValidationError> remove qualquer <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> que foi adicionado à propriedade anexada do elemento associado durante essa etapa. Por exemplo, se um <xref:System.Windows.Controls.ValidationRule> <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> deles estiver definido como <xref:System.Windows.Controls.ValidationStep.UpdatedValue> falha, na próxima vez que o processo de validação ocorrer, o mecanismo de <xref:System.Windows.Controls.ValidationError> Associação removerá isso imediatamente <xref:System.Windows.Controls.ValidationRule> antes de <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> chamar qualquer um que tenha sido definido como <xref:System.Windows.Controls.ValidationStep.UpdatedValue>.  
  
 Quando <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> não está vazio, a <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Propriedade anexada do elemento é definida como `true`. Além disso, se <xref:System.Windows.Data.Binding.NotifyOnValidationError%2A> a propriedade <xref:System.Windows.Data.Binding> de for definida como `true`, o mecanismo de associação gerará <xref:System.Windows.Controls.Validation.Error?displayProperty=nameWithType> o evento anexado no elemento.  
  
 Observe também que uma transferência de valor válida em qualquer direção (destino para origem ou origem para destino) limpa a <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> Propriedade anexada.  
  
 Se a associação tiver <xref:System.Windows.Controls.ExceptionValidationRule> um associado a ela ou <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> se a propriedade estiver definida como `true` e uma exceção for lançada quando o mecanismo de associação definir a origem, o mecanismo de associação verificará se há um <xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A>. Você tem a opção de usar o <xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A> retorno de chamada para fornecer um manipulador personalizado para lidar com exceções. Se um <xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A> não for especificado <xref:System.Windows.Data.Binding>no, o mecanismo de associação criará <xref:System.Windows.Controls.ValidationError> um com a exceção e o <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> adicionará à coleção do elemento associado.  
  
## <a name="debugging-mechanism"></a>Mecanismo de depuração  
 Você pode definir a propriedade <xref:System.Diagnostics.PresentationTraceSources.TraceLevel%2A?displayProperty=nameWithType> anexada em um objeto relacionado à associação para receber informações sobre o status de uma associação específica.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Controls.DataErrorValidationRule>
- [Novidades no WPF versão 4.5](../getting-started/whats-new.md)
- [Associar aos resultados de uma consulta LINQ](how-to-bind-to-the-results-of-a-linq-query.md)
- [Associação de dados](../advanced/optimizing-performance-data-binding.md)
- [Demonstração de vinculação de dados](https://go.microsoft.com/fwlink/?LinkID=163703)
- [Tópicos de instruções](data-binding-how-to-topics.md)
- [Associar a uma fonte de dados ADO.NET](how-to-bind-to-an-ado-net-data-source.md)
