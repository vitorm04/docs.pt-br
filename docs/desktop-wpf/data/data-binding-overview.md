---
title: Visão geral de associação de dados
description: Conheça as diferentes fontes de dados que você pode adicionar ao seu projeto no Windows Presentation Foundation for .NET Core. Fontes de dados podem ser vinculadas a elementos XAML para criar aplicativos dinâmicos.
author: thraka
ms.date: 09/19/2019
ms.author: adegeo
dev_langs:
- csharp
- vb
ms.openlocfilehash: 7f17ff094a35c04ba880c87c6966d7d249817516
ms.sourcegitcommit: b75a45f0cfe012b71b45dd9bf723adf32369d40c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/24/2020
ms.locfileid: "82072007"
---
# <a name="data-binding-overview-in-wpf"></a>Visão geral da vinculação de dados no WPF

A vinculação de dados no Windows Presentation Foundation (WPF) fornece uma maneira simples e consistente de os aplicativos apresentarem e interagirem com os dados. Os elementos podem ser vinculados a dados de uma variedade de fontes de dados na forma de objetos .NET e XML. Qualquer <xref:System.Windows.Controls.ContentControl> como <xref:System.Windows.Controls.Button> e <xref:System.Windows.Controls.ItemsControl>qualquer <xref:System.Windows.Controls.ListBox> , <xref:System.Windows.Controls.ListView>como e , têm funcionalidade incorporada para permitir o estilo flexível de itens de dados únicos ou coletas de itens de dados. É possível gerar exibições com classificação, filtragem e agrupamento dos dados.

A funcionalidade de vinculação de dados no WPF tem várias vantagens em relação aos modelos tradicionais, incluindo suporte inerente à vinculação de dados por uma ampla gama de propriedades, representação flexível de iu de dados e separação limpa da lógica de negócios da UI.

Este artigo discute primeiro conceitos fundamentais para a vinculação <xref:System.Windows.Data.Binding> de dados do WPF e, em seguida, abrange o uso da classe e outras características da vinculação de dados.

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

## <a name="what-is-data-binding"></a>O que é a associação de dados?

Vinculação de dados é o processo que estabelece uma conexão entre a ui do aplicativo e os dados que ele exibe. Se a associação possui configurações corretas e os dados fornecem notificações adequadas, quando os dados mudam de valor, os elementos que são associados a dados refletem as mudanças automaticamente. A vinculação de dados também poderá significar que, se houver uma alteração de uma representação externa dos dados em um elemento, os dados subjacentes poderão ser atualizados automaticamente para refletir essa alteração. Por exemplo, se o usuário emite o valor em um `TextBox` elemento, o valor de dados subjacente é automaticamente atualizado para refletir essa alteração.

Um uso típico da vinculação de dados é colocar dados de configuração de servidor ou local em formulários ou outros controles de ida e posição. No WPF, esse conceito é expandido para incluir a vinculação de uma ampla gama de propriedades a uma variedade de fontes de dados. No WPF, as propriedades de dependência dos elementos podem ser vinculadas a objetos .NET (incluindo objetos de ADO.NET ou objetos associados a Serviços Web e propriedades web) e dados XML.

Para um exemplo de vinculação de dados, dê uma olhada na ui do aplicativo a seguir da [Demonstração de Vinculação de Dados][data-binding-demo], que exibe uma lista de itens de leilão.

![Captura de tela de amostra de vinculação de dados](./media/data-binding-overview/demo.png "DataBinding_DataBindingDemo")

O aplicativo demonstra os seguintes recursos de vinculação de dados:

- O conteúdo do ListBox está vinculado a uma coleção de objetos *AuctionItem.* Um objeto *AuctionItem* tem propriedades como *Descrição,* *Preço inicial,* *Data de início,* *categoria,* *Características Especiais,* e assim por diante.

- Os dados (objetos*AuctionItem)* exibidos no `ListBox` é modelado para que a descrição e o preço atual sejam mostrados para cada item. O modelo é criado <xref:System.Windows.DataTemplate>usando um . Além disso, a aparência de cada item depende do valor de *SpecialFeatures* do *AuctionItem* sendo exibido. Se o valor *SpecialFeatures* do *AuctionItem* for *Color*, o item terá uma borda azul. Se o valor for *Highlight*, o item terá uma borda laranja e uma estrela. A seção [Modelos de dados](#data-templating) fornece informações sobre modelagem de dados.

- O usuário pode agrupar, filtrar `CheckBoxes` ou classificar os dados usando o fornecido. Na imagem acima, o **Grupo por categoria** e Classificar por categoria e **data** `CheckBoxes` são selecionados. Você talvez tenha observado que os dados estão agrupados com base na categoria do produto e que o nome da categoria está em ordem alfabética. É difícil perceber isto na imagem, mas os itens também são classificados por data de início dentro de cada categoria. A classificação é feita usando uma *exibição de coleção.* A seção [Vinculação às coleções](#binding-to-collections) discute as vistas da coleção.

- Quando o usuário seleciona um <xref:System.Windows.Controls.ContentControl> item, exibe os detalhes do item selecionado. Essa experiência é chamada *de cenário de detalhemestre.* A seção [de cenário de detalhes mestres](#master-detail-binding-scenario) fornece informações sobre esse tipo de vinculação.

- O tipo de propriedade <xref:System.DateTime> *StartDate* é , que retorna uma data que inclui a hora para o milissegundo. Neste aplicativo, um conversor personalizado foi usado para que uma seqüência de datas mais curta seja exibida. A seção [de conversão de dados](#data-conversion) fornece informações sobre conversores.

Quando o usuário seleciona o botão *Adicionar produto,* o formulário a seguir é criado.

![Adicionar página de listagem de produtos](./media/data-binding-overview/demo-addproductlisting.png "DataBinding_Demo_AddProductListing")

O usuário pode editar os campos no formulário, visualizar a listagem do `Submit` produto usando os painéis de visualização curtos ou detalhados e selecionar para adicionar a nova listagem de produtos. Quaisquer configurações de agrupamento, filtragem e classificação existentes serão aplicadas à nova entrada. Neste caso em particular, o item inserido na imagem acima será exibido como o segundo item dentro da categoria *Computador*.

Não mostrado nesta imagem é a lógica de validação fornecida na *Data de Início* <xref:System.Windows.Controls.TextBox>. Se o usuário inserir uma data inválida (formatação inválida ou uma <xref:System.Windows.Controls.ToolTip> data passada), o usuário <xref:System.Windows.Controls.TextBox>será notificado com um ponto de exclamação vermelho ao lado do . A seção [Validação de dados](#data-validation) discute como criar lógica de validação.

Antes de entrar nas diferentes características da vinculação de dados descritaacima, discutiremos primeiro os conceitos fundamentais que são fundamentais para entender a vinculação de dados do WPF.

## <a name="basic-data-binding-concepts"></a>Conceitos básicos de vinculação de dados

Independentemente do elemento que você está vinculando e da natureza de sua fonte de dados, cada vinculação sempre segue o modelo ilustrado pela figura a seguir.

![Diagrama que mostra o modelo básico de vinculação de dados.](./media/data-binding-overview/basic-data-binding-diagram.png)

Como a figura mostra, a vinculação de dados é essencialmente a ponte entre seu alvo de ligação e sua fonte de ligação. A figura demonstra os seguintes conceitos fundamentais de vinculação de dados do WPF:

- Normalmente, cada ligação tem quatro componentes:

  - Um objeto alvo de ligação.
  - Uma propriedade alvo.
  - Uma origem de associação.
  - Um caminho para o valor na fonte de ligação a ser usada.
  
  > Por exemplo, se você quiser vincular `TextBox` o `Employee.Name` conteúdo de a `TextBox`à propriedade, seu <xref:System.Windows.Controls.TextBox.Text%2A> objeto de destino é, a propriedade de destino é a propriedade, o valor a ser usado é *Nome,* e o objeto de origem é o objeto *Funcionário.*

- A propriedade de destino deve ser uma propriedade de dependência. A <xref:System.Windows.UIElement> maioria das propriedades são propriedades de dependência, e a maioria das propriedades de dependência, exceto as somente leitura, suportam a vinculação de dados por padrão. (Somente tipos derivados podem definir propriedades <xref:System.Windows.DependencyObject> <xref:System.Windows.UIElement> de dependência; e todos os tipos derivam de `DependencyObject`.)

- Embora não seja mostrado na figura, deve-se notar que o objeto de origem de vinculação não está restrito a ser um objeto .NET personalizado. A vinculação de dados WPF suporta dados na forma de objetos .NET e XML. Para fornecer alguns exemplos, sua <xref:System.Windows.UIElement>fonte de vinculação pode ser um objeto de lista, um objeto de ADO.NET ou Serviços Web ou um XmlNode que contenha seus dados XML. Para obter mais informações, consulte [A visão geral das fontes vinculantes](../../framework/wpf/data/binding-sources-overview.md).

É importante lembrar que quando você está estabelecendo uma vinculação, você está vinculando um alvo vinculativo *a* uma fonte vinculante. Por exemplo, se você estiver exibindo alguns <xref:System.Windows.Controls.ListBox> dados XML subjacentes `ListBox` em uma vinculação de dados usando, você está vinculando o seu aos dados XML.

Para estabelecer uma vinculação, você usa o <xref:System.Windows.Data.Binding> objeto. O resto deste artigo discute muitos dos conceitos associados e algumas `Binding` das propriedades e uso do objeto.

### <a name="direction-of-the-data-flow"></a>Direção do fluxo de dados

Como indicado pela seta na figura anterior, o fluxo de dados de uma vinculação pode ir da meta vinculante para a `TextBox`fonte de vinculação (por exemplo, o valor `TextBox` de origem muda quando um usuário emite o valor de a ) e/ou da fonte vinculante para o destino vinculante (por exemplo, seu conteúdo é atualizado com alterações na fonte vinculante) se a fonte vinculante fornecer as notificações adequadas.

Você pode querer que seu aplicativo habilite os usuários a alterar os dados e propagar-os de volta para o objeto de origem. Ou talvez você não queira permitir que os usuários atualizem os dados de origem. Você pode controlar o fluxo <xref:System.Windows.Data.Binding.Mode?displayProperty=nameWithType>de dados definindo o .

Esta figura ilustra os diferentes tipos de fluxo de dados:

![Fluxo de dados de vinculação de dados](./media/data-binding-overview/databinding-dataflow.png "DataBinding_DataFlow")

- <xref:System.Windows.Data.BindingMode.OneWay>a vinculação faz com que alterações na propriedade de origem atualizem automaticamente a propriedade de destino, mas as alterações na propriedade de destino não são propagadas de volta à propriedade de origem. Esse tipo de associação será apropriado se o controle associado for somente leitura de forma implícita. Por exemplo, você pode vincular a uma fonte, como um ticker de estoque, ou talvez sua propriedade de destino não tenha nenhuma interface de controle fornecida para fazer alterações, como uma cor de fundo vinculada a dados de uma tabela. Se não houver necessidade de monitorar as alterações da propriedade de destino, o uso do modo de associação <xref:System.Windows.Data.BindingMode.OneWay> evitará a sobrecarga do modo de associação <xref:System.Windows.Data.BindingMode.TwoWay>.

- <xref:System.Windows.Data.BindingMode.TwoWay>a vinculação causa alterações na propriedade de origem ou na propriedade de destino para atualizar automaticamente a outra. Este tipo de vinculação é apropriado para formas editáveis ou outros cenários de IA totalmente interativos. A maioria <xref:System.Windows.Data.BindingMode.OneWay> das propriedades é padrão para vinculação, mas algumas propriedades de <xref:System.Windows.Controls.TextBox.Text?displayProperty=nameWithType> dependência (normalmente propriedades <xref:System.Windows.Data.BindingMode.TwoWay> de controles editáveis pelo usuário, como o e o [CheckBox.IsChecked](xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked) padrão à vinculação. Uma maneira programática de determinar se uma propriedade de dependência se liga de uma ou <xref:System.Windows.DependencyProperty.GetMetadata%2A?displayProperty=nameWithType> duas vias por padrão <xref:System.Windows.FrameworkPropertyMetadata.BindsTwoWayByDefault%2A?displayProperty=nameWithType> é obter os metadados da propriedade e, em seguida, verificar o valor booleano da propriedade.

- <xref:System.Windows.Data.BindingMode.OneWayToSource>é o <xref:System.Windows.Data.BindingMode.OneWay> inverso da vinculação; ele atualiza a propriedade de origem quando a propriedade de destino muda. Um exemplo de cenário é se você só precisa reavaliar o valor de origem da ui.

- Não ilustrado na <xref:System.Windows.Data.BindingMode.OneTime> figura é vinculante, o que faz com que a propriedade de origem inicialize a propriedade alvo, mas não propague alterações subseqüentes. Se o contexto de dados mudar ou o objeto no contexto de dados mudar, a alteração *não* será refletida na propriedade de destino. Este tipo de vinculação é apropriado se um instantâneo do estado atual for apropriado ou os dados forem verdadeiramente estáticos. Esse tipo de associação também é útil se você deseja inicializar a propriedade de destino com um valor de uma propriedade de origem e o contexto de dados não é conhecido com antecedência. Este modo é essencialmente <xref:System.Windows.Data.BindingMode.OneWay> uma forma mais simples de vinculação que proporciona melhor desempenho nos casos em que o valor de origem não muda.

Para detectar alterações de <xref:System.Windows.Data.BindingMode.OneWay> <xref:System.Windows.Data.BindingMode.TwoWay> origem (aplicáveis e vinculações), a fonte <xref:System.ComponentModel.INotifyPropertyChanged>deve implementar um mecanismo adequado de notificação de alteração de propriedade, como . [Veja Como: Implementar a notificação](../../framework/wpf/data/how-to-implement-property-change-notification.md) de <xref:System.ComponentModel.INotifyPropertyChanged> alteração de propriedade para um exemplo de implementação.

A <xref:System.Windows.Data.Binding.Mode?displayProperty=nameWithType> propriedade fornece mais informações sobre os modos de vinculação e um exemplo de como especificar a direção de uma vinculação.

### <a name="what-triggers-source-updates"></a>O que desencadeia atualizações de origem

Vinculações que <xref:System.Windows.Data.BindingMode.TwoWay> <xref:System.Windows.Data.BindingMode.OneWayToSource> são ou ouvem alterações na propriedade de destino e as propagam de volta para a fonte, conhecida como atualização da fonte. Por exemplo, você pode editar o texto de uma caixa de texto para alterar o valor da origem subjacente.

No entanto, seu valor de origem é atualizado enquanto você está editando o texto ou depois de terminar de editar o texto e o controle perde o foco? A <xref:System.Windows.Data.Binding.UpdateSourceTrigger?displayProperty=nameWithType> propriedade determina o que desencadeia a atualização da fonte. Os apontates das setas certas na figura a <xref:System.Windows.Data.Binding.UpdateSourceTrigger?displayProperty=nameWithType> seguir ilustram o papel da propriedade.

![Diagrama que mostra a função da propriedade UpdateSourceTrigger.](./media/data-binding-overview/data-binding-updatesource-trigger.png)

Se `UpdateSourceTrigger` o <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged?displayProperty=nameWithType>valor for, então o valor <xref:System.Windows.Data.BindingMode.TwoWay> apontado <xref:System.Windows.Data.BindingMode.OneWayToSource> pela seta direita ou pelas vinculações é atualizado assim que a propriedade-alvo for mudada. No entanto, se o `UpdateSourceTrigger` valor for, <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus>então esse valor só é atualizado com o novo valor quando o imóvel-alvo perde o foco.

Semelhante à <xref:System.Windows.Data.Binding.Mode%2A> propriedade, diferentes propriedades <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> de dependência têm valores padrão diferentes. O valor padrão para a maioria das propriedades de dependência é <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>, enquanto a propriedade `TextBox.Text` tem um valor padrão de <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus>. `PropertyChanged`significa que as atualizações de origem geralmente acontecem sempre que a propriedade de destino muda. Alterações instantâneas são boas para Caixas de Seleção e outros controles simples. No entanto, para campos de texto, a atualização após cada tecla pode diminuir o desempenho e nega ao usuário a oportunidade usual de fazer backspace e corrigir erros de digitação antes de se comprometer com o novo valor.

Consulte <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> a página de propriedade para obter informações sobre como encontrar o valor padrão de uma propriedade de dependência.

A tabela a seguir fornece <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> um <xref:System.Windows.Controls.TextBox> cenário de exemplo para cada valor usando o exemplo.

| Valor de UpdateSourceTrigger | Quando o valor de origem é atualizado | Exemplo de cenário para TextBox |
| ------------------------- | ---------------------------------- | ---------------------------- |
| `LostFocus`(padrão <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType>para) | Quando o controle TextBox perde o foco. | Uma TextBox associada à lógica de validação (consulte [Validação de dados](#data-validation) abaixo). |
| `PropertyChanged` | À medida que <xref:System.Windows.Controls.TextBox>você digita no . | Controles textbox em uma janela de sala de bate-papo. |
| `Explicit` | Quando o <xref:System.Windows.Data.BindingExpression.UpdateSource%2A>aplicativo chama . | O TextBox controla de forma editável (atualiza os valores de origem somente quando o usuário clica no botão enviar). |

Por exemplo, [veja Como: Controlar quando o texto do TextBox atualizar a origem](../../framework/wpf/data/how-to-control-when-the-textbox-text-updates-the-source.md).

## <a name="creating-a-binding"></a>Criando uma vinculação

Para reafirmar alguns dos conceitos discutidos nas seções anteriores, você estabelece uma vinculação usando o <xref:System.Windows.Data.Binding> objeto, e cada vinculação geralmente tem quatro componentes: um alvo vinculativo, uma propriedade de destino, uma fonte de vinculação e um caminho para o valor de origem a ser usado. Esta seção discute como configurar uma associação.

Considere o exemplo a seguir, no qual o objeto de origem da associação é uma classe chamada *MyData* que é definida no namespace *SDKSample*. Para fins de demonstração, *o MyData* tem uma propriedade de string chamada *ColorName* cujo valor é definido como "Vermelho". Assim, esse exemplo gera um botão com uma tela de fundo vermelha.

[!code-xaml[BindNonTextProperty](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/AutoConvertPropertyToColor.xaml#BindAutoConvertColor)]

Para obter mais informações sobre a sintaxe da declaração vinculante e exemplos de como configurar uma vinculação no código, consulte [Visão geral das Declarações Vinculantes](../../framework/wpf/data/binding-declarations-overview.md).

Se nós aplicarmos esse exemplo a nosso diagrama básico, a figura resultante será semelhante à exibida a seguir. Essa figura descreve <xref:System.Windows.Data.BindingMode.OneWay> uma vinculação porque <xref:System.Windows.Data.BindingMode.OneWay> a propriedade Background suporta vinculação por padrão.

![Diagrama que mostra a propriedade de fundo de vinculação de dados.](./media/data-binding-overview/data-binding-button-background-example.png)

Você pode se perguntar por que essa vinculação funciona <xref:System.Windows.Controls.Control.Background%2A> mesmo que <xref:System.Windows.Media.Brush>a propriedade *ColorName* seja de cadeia de tipo enquanto a propriedade é do tipo . Essa vinculação usa conversão de tipo padrão, que é discutida na seção [conversão de dados.](#data-conversion)

### <a name="specifying-the-binding-source"></a>Especificando a fonte de vinculação

Observe que, no exemplo anterior, a fonte de vinculação é especificada definindo a propriedade [DockPanel.DataContext.](xref:System.Windows.FrameworkElement.DataContext) O <xref:System.Windows.Controls.Button> então herda <xref:System.Windows.FrameworkElement.DataContext%2A> o <xref:System.Windows.Controls.DockPanel>valor do , que é o seu elemento pai. Para reiterar, o objeto de origem da associação é um dos quatro componentes necessários de uma associação. Portanto, sem o objeto de origem de associação que está sendo especificado, a associação não faria nada.

Há várias maneiras para especificar o objeto de origem de associação. O <xref:System.Windows.FrameworkElement.DataContext%2A> uso da propriedade em um elemento pai é útil quando você está vinculando várias propriedades à mesma fonte. No entanto, às vezes pode ser mais apropriado especificar a origem da associação em declarações de associação individuais. No exemplo anterior, em <xref:System.Windows.FrameworkElement.DataContext%2A> vez de usar a propriedade, <xref:System.Windows.Data.Binding.Source%2A?displayProperty=nameWithType> você pode especificar a fonte de vinculação definindo a propriedade diretamente na declaração vinculante do botão, como no exemplo a seguir.

[!code-xaml[BindNonTextPropertyCompactBinding](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/AutoConvertPropertyToColor.xaml#BindAutoConvertColorCompactBinding)]

Além de <xref:System.Windows.FrameworkElement.DataContext%2A> definir a propriedade em um <xref:System.Windows.FrameworkElement.DataContext%2A> elemento diretamente, herdar o valor de um ancestral (como o botão no <xref:System.Windows.Data.Binding.Source%2A?displayProperty=nameWithType> primeiro exemplo) e especificar explicitamente a fonte de <xref:System.Windows.Data.Binding.ElementName?displayProperty=nameWithType> vinculação <xref:System.Windows.Data.Binding.RelativeSource?displayProperty=nameWithType> definindo a propriedade na vinculação (como o botão do último exemplo), você também pode usar a propriedade ou a propriedade para especificar a fonte de vinculação. A <xref:System.Windows.Data.Binding.ElementName%2A> propriedade é útil quando você está vinculando a outros elementos em seu aplicativo, como quando você está usando um controle deslizante para ajustar a largura de um botão. A <xref:System.Windows.Data.Binding.RelativeSource%2A> propriedade é útil quando a <xref:System.Windows.Controls.ControlTemplate> vinculação <xref:System.Windows.Style>é especificada em a ou a . Para obter mais informações, consulte [Como: Especificar a fonte de vinculação](../../framework/wpf/data/how-to-specify-the-binding-source.md).

### <a name="specifying-the-path-to-the-value"></a>Especificando o caminho para o valor

Se sua fonte de vinculação <xref:System.Windows.Data.Binding.Path?displayProperty=nameWithType> for um objeto, você usará a propriedade para especificar o valor a ser usado para sua vinculação. Se você estiver vinculando aos <xref:System.Windows.Data.Binding.XPath?displayProperty=nameWithType> dados XML, use a propriedade para especificar o valor. Em alguns casos, pode ser <xref:System.Windows.Data.Binding.Path%2A> aplicável usar a propriedade mesmo quando seus dados são XML. Por exemplo, se você quiser acessar a propriedade Name de um XmlNode retornado (como <xref:System.Windows.Data.Binding.Path%2A> resultado de uma <xref:System.Windows.Data.Binding.XPath%2A> consulta XPath), você deve usar a propriedade além da propriedade.

Para obter mais <xref:System.Windows.Data.Binding.Path%2A> informações, consulte as propriedades e. <xref:System.Windows.Data.Binding.XPath%2A>

Embora tenhamos enfatizado <xref:System.Windows.Data.Binding.Path%2A> que o valor a ser usado é um dos quatro componentes necessários de uma vinculação, nos cenários que você deseja vincular a um objeto inteiro, o valor a ser usado seria o mesmo que o objeto de origem vinculante. Nesses casos, é aplicável não especificar um <xref:System.Windows.Data.Binding.Path%2A>. Considere o exemplo a seguir.

[!code-xaml[EmptyBinding](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/EmptyBinding.xaml#EmptyBinding)]

O exemplo acima usa a sintaxe de associação vazia: {Binding}. Neste caso, <xref:System.Windows.Controls.ListBox> o herda o DataContext a partir de um elemento dockPanel pai (não mostrado neste exemplo). Quando o caminho não é especificado, o padrão é associar ao objeto inteiro. Em outras palavras, neste exemplo, o caminho foi <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> deixado de fora porque estamos vinculando a propriedade a todo o objeto. (Consulte a seção [Vinculação às coleções](#binding-to-collections) para uma discussão aprofundada.)

Além de ao associar a uma coleção, este cenário também é útil quando você deseja associar a um objeto inteiro em vez de apenas uma única propriedade de um objeto. Por exemplo, se o objeto <xref:System.String>de origem for de tipo, você pode simplesmente querer se ligar à própria string. Outro cenário comum é quando você deseja associar um elemento a um objeto com várias propriedades.

Você pode precisar aplicar uma lógica personalizada para que os dados sejam significativos para sua propriedade de destino vinculada. A lógica personalizada pode estar na forma de um conversor personalizado se a conversão de tipo padrão não existir. Consulte [a conversão de dados](#data-conversion) para obter informações sobre conversores.

### <a name="binding-and-bindingexpression"></a>Associação e BindingExpression

Antes de entrar em outros recursos e usos de <xref:System.Windows.Data.BindingExpression> vinculação de dados, é útil introduzir a classe. Como você viu em seções <xref:System.Windows.Data.Binding> anteriores, a classe é a classe de alto nível para a declaração de uma vinculação; ele fornece muitas propriedades que permitem especificar as características de uma vinculação. Uma classe <xref:System.Windows.Data.BindingExpression>relacionada é o objeto subjacente que mantém a conexão entre a fonte e o alvo. Uma associação contém todas as informações que podem ser compartilhadas entre várias expressões de associação. A <xref:System.Windows.Data.BindingExpression> é uma expressão de instância que não pode <xref:System.Windows.Data.Binding>ser compartilhada e contém todas as informações de instância do .

Considere o exemplo `myDataObject` a seguir, `MyData` onde `myBinding` é uma <xref:System.Windows.Data.Binding> instância `MyData` da classe, é o objeto `MyDataProperty`de origem e é uma classe definida que contém uma propriedade de string chamada . Este exemplo vincula o `myText`conteúdo do <xref:System.Windows.Controls.TextBlock>texto `MyDataProperty`de , uma instância de , a .

[!code-csharp[CodeOnlyBinding](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/ManualBinding.cs#CodeOnlyBinding)]
[!code-vb[CodeOnlyBinding](~/samples/snippets/desktop-guide/wpf/data-binding-overview/vb/ManualBinding.vb#CodeOnlyBinding)]

Você pode usar o mesmo objeto *myBinding* para criar outras associações. Por exemplo, você pode usar o objeto *myBinding* para vincular o conteúdo de texto de uma caixa de seleção ao *MyDataProperty*. Nesse cenário, haverá duas instâncias de compartilhamento do <xref:System.Windows.Data.BindingExpression> objeto *myBinding.*

Um <xref:System.Windows.Data.BindingExpression> objeto é devolvido <xref:System.Windows.Data.BindingOperations.GetBindingExpression%2A> chamando um objeto vinculado a dados. Os seguintes artigos demonstram alguns <xref:System.Windows.Data.BindingExpression> dos usos da classe:

- [Obter o objeto de associação de uma propriedade de destino associada](../../framework/wpf/data/how-to-get-the-binding-object-from-a-bound-target-property.md)

- [Controle Quando o texto textBox atualiza a fonte](../../framework/wpf/data/how-to-control-when-the-textbox-text-updates-the-source.md)

## <a name="data-conversion"></a>Conversão de dados

Na [seção Criar uma vinculação,](#creating-a-binding) <xref:System.Windows.Controls.Control.Background%2A> o botão é vermelho porque sua propriedade está vinculada a uma propriedade de string com o valor "Vermelho". Esse valor de seqüência funciona <xref:System.Windows.Media.Brush> porque um conversor de <xref:System.Windows.Media.Brush>tipo está presente no tipo para converter o valor da seqüência em um .

Adicionar essas informações à figura da [seção Criar uma vinculação](#creating-a-binding) se parece com isso.

![Diagrama que mostra a vinculação de dados Propriedade Padrão.](./media/data-binding-overview/data-binding-button-default-conversion.png)

No entanto, e se em vez de ter *Color* uma propriedade <xref:System.Windows.Media.Color>de string tipo seu objeto de origem de vinculação tiver uma propriedade Cor do tipo? Nesse caso, para que a vinculação funcione, *Color* você precisaria primeiro transformar <xref:System.Windows.Controls.Control.Background%2A> o valor da propriedade Color em algo que a propriedade aceita. Você precisaria criar um conversor personalizado <xref:System.Windows.Data.IValueConverter> implementando a interface, como no exemplo a seguir.

[!code-csharp[CodeOnlyBinding](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/ColorBrushConverter.cs#ColorBrushConverter)]
[!code-vb[CodeOnlyBinding](~/samples/snippets/desktop-guide/wpf/data-binding-overview/vb/ColorBrushConverter.vb#ColorBrushConverter)]

Consulte <xref:System.Windows.Data.IValueConverter> para obter mais informações.

Agora, o conversor personalizado é usado em vez de conversão padrão, e nosso diagrama se parece com isso.

![Diagrama que mostra o conversor personalizado de vinculação de dados.](./media/data-binding-overview/data-binding-converter-color-example.png)

Para reiterar, conversões padrão podem estar disponíveis devido a conversores de tipo presentes no tipo para o qual a associação está sendo realizada. Esse comportamento dependerá de quais conversores de tipo estão disponíveis no destino. Em caso de dúvida, crie seu próprio conversor.

A seguir estão alguns cenários típicos onde faz sentido implementar um conversor de dados:

- Os dados devem ser exibidos de forma diferente, dependendo da cultura. Por exemplo, você pode querer implementar um conversor de moedas ou um conversor de data/hora de calendário com base nas convenções usadas em uma cultura específica.

- Os dados que está sendo usados não são necessariamente destinados a alterar o valor de texto de uma propriedade, mas sim destinados a alterar alguns outros valores como a origem de uma imagem ou então a cor ou o estilo do texto. Conversores podem ser usados nesta instância convertendo a associação de uma propriedade que pode não parecer apropriada, assim como a associação de um campo de texto à propriedade Background de uma célula de tabela.

- Mais de um controle ou múltiplas propriedades de controles estão vinculados aos mesmos dados. Nesse caso, a associação primária pode simplesmente exibir o texto, enquanto outras associações lidam com questões específicas de exibição, mas ainda usam a mesma associação como informações da origem.

- Uma propriedade-alvo tem uma coleção de <xref:System.Windows.Data.MultiBinding>vinculações, que é denominada . Para <xref:System.Windows.Data.MultiBinding>, você <xref:System.Windows.Data.IMultiValueConverter> usa um costume para produzir um valor final a partir dos valores das vinculações. Por exemplo, a cor pode ser computada de valores vermelhos, azuis e verdes, que podem ser valores dos mesmos ou de diferentes objetos de origem da associação. Consulte <xref:System.Windows.Data.MultiBinding> exemplos e informações.

## <a name="binding-to-collections"></a>Vinculação às coleções

Um objeto de origem vinculante pode ser tratado como um único objeto cujas propriedades contêm dados ou como uma coleta de dados de objetos polimórficos que são frequentemente agrupados (como o resultado de uma consulta a um banco de dados). Até agora, só discutimos a vinculação a objetos únicos. No entanto, vincular-se a uma coleta de dados é um cenário comum. Por exemplo, um cenário comum é <xref:System.Windows.Controls.ListBox> <xref:System.Windows.Controls.ListView>usar <xref:System.Windows.Controls.TreeView> uma <xref:System.Windows.Controls.ItemsControl> tal como a , ou exibir uma coleta de dados, como no aplicativo mostrado na seção [O que é vinculação de dados.](#what-is-data-binding)

Felizmente, nosso diagrama básico ainda se aplica. Se você está <xref:System.Windows.Controls.ItemsControl> vinculando um a uma coleção, o diagrama se parece com isso.

![Diagrama que mostra o objeto ItemsControl vinculação de dados.](./media/data-binding-overview/data-binding-itemscontrol.png)

Como mostrado neste diagrama, <xref:System.Windows.Controls.ItemsControl> para vincular <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A?displayProperty=nameWithType> um a um objeto de coleta, a propriedade é a propriedade a ser usada. Você pode `ItemsSource` pensar como o <xref:System.Windows.Controls.ItemsControl>conteúdo do . A vinculação <xref:System.Windows.Data.BindingMode.OneWay> `ItemsSource` é porque `OneWay` a propriedade suporta vinculação por padrão.

### <a name="how-to-implement-collections"></a>Como implementar coleções

Você pode enumerar qualquer coleção <xref:System.Collections.IEnumerable> que implemente a interface. No entanto, para configurar vinculações dinâmicas para que as inserções ou exclusões <xref:System.Collections.Specialized.INotifyCollectionChanged> na atualização de cobrança atualizem automaticamente a interface, a coleção deve implementar a interface. Essa interface expõe um evento que deve ser acionado sempre que a coleção subjacente for alterada.

O WPF <xref:System.Collections.ObjectModel.ObservableCollection%601> fornece a classe, que é uma implementação <xref:System.Collections.Specialized.INotifyCollectionChanged> incorporada de uma coleta de dados que expõe a interface. Para suportar totalmente a transferência de valores de dados de objetos de origem <xref:System.ComponentModel.INotifyPropertyChanged> para alvos, cada objeto em sua coleção que suporte propriedades vinculáveis também deve implementar a interface. Para obter mais informações, consulte [A visão geral das fontes vinculantes](../../framework/wpf/data/binding-sources-overview.md).

Antes de implementar sua própria <xref:System.Collections.ObjectModel.ObservableCollection%601> coleção, considere usar ou uma <xref:System.Collections.Generic.List%601> <xref:System.Collections.ObjectModel.Collection%601>das <xref:System.ComponentModel.BindingList%601>classes de coleta existentes, como , e , entre muitas outras. Se você tem um cenário avançado e deseja <xref:System.Collections.IList>implementar sua própria coleção, considere usar , que fornece uma coleção não genérica de objetos que podem ser acessados individualmente pelo índice, e assim proporciona o melhor desempenho.

### <a name="collection-views"></a>Exibições de coleção

Uma <xref:System.Windows.Controls.ItemsControl> vez que o seu está vinculado a uma coleta de dados, você pode querer classificar, filtrar ou agrupar os dados. Para fazer isso, você usa visualizações de <xref:System.ComponentModel.ICollectionView> coleção, que são classes que implementam a interface.

#### <a name="what-are-collection-views"></a>O que são vistas de coleção?

Uma exibição de coleção é uma camada sobre uma coleção de origem da associação que permite a você navegar e exibir a coleção de origem com base em consultas de classificação, filtragem e agrupamento, sem precisar alterar a coleção de origem subjacente. Uma exibição de coleção também mantém um ponteiro para o item atual na coleção. Se a coleta de <xref:System.Collections.Specialized.INotifyCollectionChanged> origem implementar a interface, as alterações levantadas pelo <xref:System.Collections.Specialized.INotifyCollectionChanged.CollectionChanged> evento serão propagadas para as visualizações.

Já que as exibições não alteram as coleções de origem subjacentes, cada coleção de origem pode ter várias exibições associadas a ela. Por exemplo, você pode ter uma coleção de objetos *Task*. Com o uso de exibições, você pode exibir esses mesmos dados de maneiras diferentes. Por exemplo, no lado esquerdo da página, talvez você queira mostrar as tarefas ordenadas por prioridade e, no lado direito, agrupadas por área.

#### <a name="how-to-create-a-view"></a>Como criar uma exibição

Uma maneira de criar e usar uma exibição é instanciar o objeto de exibição diretamente e então usá-lo como a origem da associação. Por exemplo, considere o aplicativo [de demonstração de vinculação de dados][data-binding-demo] mostrado na seção O que é [vinculação de dados.](#what-is-data-binding) O aplicativo é implementado <xref:System.Windows.Controls.ListBox> de tal forma que o binds a uma exibição sobre a coleta de dados em vez da coleta de dados diretamente. O exemplo a seguir é extraído do aplicativo [de demonstração de vinculação de dados.][data-binding-demo] A <xref:System.Windows.Data.CollectionViewSource> classe é o proxy XAML de <xref:System.Windows.Data.CollectionView>uma classe que herda de . Neste exemplo em <xref:System.Windows.Data.CollectionViewSource.Source%2A> particular, a exibição está vinculada à coleção <xref:System.Collections.ObjectModel.ObservableCollection%601> *AuctionItems* (de tipo) do objeto do aplicativo atual.

[!code-xaml[CollectionView](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/CollectionView.xaml#CollectionView)]

A listagem de *recursosDataView* serve então como a fonte <xref:System.Windows.Controls.ListBox>de vinculação para elementos no aplicativo, como o .

[!code-xaml[ListBoxCollectionView](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/CollectionView.xaml#ListBoxCollectionView)]

Para criar outra visualização para a <xref:System.Windows.Data.CollectionViewSource> mesma coleção, você `x:Key` pode criar outra instância e dar-lhe um nome diferente.

A tabela a seguir mostra quais tipos de dados <xref:System.Windows.Data.CollectionViewSource> de exibição são criados como a exibição de coleta padrão ou com base no tipo de coleta de origem.

| Tipo de coleção de origem                    | Tipo de exibição de coleção | Observações |
| ----------------------------------------- | -------------------- | ----- |
| <xref:System.Collections.IEnumerable>     | Um tipo interno baseado em<xref:System.Windows.Data.CollectionView> | Não é possível agrupar itens. |
| <xref:System.Collections.IList>           | <xref:System.Windows.Data.ListCollectionView> | Mais rápido. |
| <xref:System.ComponentModel.IBindingList> | <xref:System.Windows.Data.BindingListCollectionView> | |

#### <a name="using-a-default-view"></a>Usando uma exibição padrão

Especificar uma exibição de coleção como uma origem da associação é uma maneira de criar e usar uma exibição de coleção. O WPF também cria uma exibição de coleção padrão para cada coleção usada como uma origem da associação. Se você associar diretamente a uma coleção, o WPF será associado à sua exibição padrão. Essa exibição padrão é compartilhada por todas as vinculações à mesma coleção, de modo que uma alteração feita para uma exibição padrão por um controle ou código vinculado (como classificação ou alteração no ponteiro do item atual, discutido posteriormente) é refletida em todas as outras vinculações à mesma coleção.

Para obter a exibição <xref:System.Windows.Data.CollectionViewSource.GetDefaultView%2A> padrão, você usa o método. Por exemplo, consulte [Obter a exibição padrão de uma coleta de dados](../../framework/wpf/data/how-to-get-the-default-view-of-a-data-collection.md).

#### <a name="collection-views-with-adonet-datatables"></a>Visualizações de coleta com ADO.NET DataTables

Para melhorar o desempenho, <xref:System.Data.DataTable> <xref:System.Data.DataView> as visualizações de coleta <xref:System.Data.DataView>para ADO.NET ou objetos delegam classificação e filtragem para o , o que faz com que a classificação e filtragem sejam compartilhadas em todas as visualizações de coleta da fonte de dados. Para permitir que cada visualização de coleção classifique e <xref:System.Data.DataView> filtre de forma independente, inicialize cada exibição de coleção com seu próprio objeto.

#### <a name="sorting"></a>Classificação

Conforme mencionado anteriormente, as exibições podem aplicar uma ordem de classificação para uma coleção. Já que eles existem na coleção subjacente, seus dados podem ter ou não uma ordem inerente e relevante. A exibição da coleção permite impor uma ordem ou alterar a ordem padrão, com base em critérios de comparação fornecidos por você. Já que essa é uma exibição dos dados baseada no cliente, um cenário comum é que o usuário deseje classificar colunas de dados tabulares segundo o valor ao qual a coluna corresponde. Usando exibições, essa classificação controlada pelo usuário pode ser aplicada, novamente sem necessidade de alterações na coleção subjacente nem mesmo precisar repetir a consulta do conteúdo da coleção. Por exemplo, consulte [Classificar uma coluna GridView quando um cabeçalho é clicado](../../framework/wpf/controls/how-to-sort-a-gridview-column-when-a-header-is-clicked.md).

O exemplo a seguir mostra a lógica de classificação da "Classificar por categoria e data" <xref:System.Windows.Controls.CheckBox> da iu do aplicativo na seção O que é [vinculação de dados.](#what-is-data-binding)

[!code-csharp[AddSortChecked](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/CollectionView.xaml.cs#AddSortChecked)]
[!code-vb[AddSortChecked](~/samples/snippets/desktop-guide/wpf/data-binding-overview/vb/CollectionView.xaml.vb#AddSortChecked)]

#### <a name="filtering"></a>Filtragem

As visualizações também podem aplicar um filtro a uma coleção, de modo que a exibição mostre apenas um certo subconjunto da coleção completa. Você pode filtrar por uma condição nos dados. Por exemplo, como é feito pelo aplicativo na seção O que <xref:System.Windows.Controls.CheckBox> é [vinculação de dados,](#what-is-data-binding) o "Mostrar apenas barganhas" contém lógica para filtrar itens que custam US$ 25 ou mais. O código a seguir é executado para definir <xref:System.Windows.Data.CollectionViewSource.Filter> *ShowOnlyBargainsFilter* como o manipulador de eventos quando for <xref:System.Windows.Controls.CheckBox> selecionado.

[!code-csharp[ListingViewFilter](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/CollectionView.xaml.cs#ListingViewFilter)]
[!code-vb[ListingViewFilter](~/samples/snippets/desktop-guide/wpf/data-binding-overview/vb/CollectionView.xaml.vb#ListingViewFilter)]

O manipulador de eventos *ShowOnlyBargainsFilter* tem a seguinte implementação.

[!code-csharp[FilterEvent](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/CollectionView.xaml.cs#FilterEvent)]
[!code-vb[FilterEvent](~/samples/snippets/desktop-guide/wpf/data-binding-overview/vb/CollectionView.xaml.vb#FilterEvent)]

Se você estiver usando <xref:System.Windows.Data.CollectionView> uma das <xref:System.Windows.Data.CollectionViewSource>classes diretamente <xref:System.Windows.Data.CollectionView.Filter%2A> em vez de, você usaria a propriedade para especificar um retorno de chamada. Para obter um exemplo, consulte [Filtrar dados em uma exibição](../../framework/wpf/data/how-to-filter-data-in-a-view.md).

#### <a name="grouping"></a>Agrupamento

Com exceção da classe <xref:System.Collections.IEnumerable> interna que visualiza uma coleção, todas as visualizações de coleção suportam o *agrupamento,* o que permite ao usuário dividir a coleção na exibição de coleção em grupos lógicos. Os grupos podem ser explícitos (caso em que o usuário fornece uma lista de grupos) ou então implícitos (caso em que os grupos são gerados dinamicamente, dependendo dos dados).

O exemplo a seguir mostra a lógica <xref:System.Windows.Controls.CheckBox>do "Grupo por categoria".

[!code-csharp[ListingGroupCheck](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/CollectionView.xaml.cs#ListingGroupCheck)]
[!code-vb[ListingGroupCheck](~/samples/snippets/desktop-guide/wpf/data-binding-overview/vb/CollectionView.xaml.vb#ListingGroupCheck)]

Para obter outro exemplo de agrupamento, consulte [Agrupar itens em uma ListView que implementa uma GridView](../../framework/wpf/controls/how-to-group-items-in-a-listview-that-implements-a-gridview.md).

#### <a name="current-item-pointers"></a>Ponteiros de itens atuais

As exibições também dão suporte à noção de um item atual. Você pode navegar pelos objetos em uma exibição de coleção. Enquanto você navega, você está movendo um ponteiro de item que permite que você recupere o objeto existente nesse local específico na coleção. Por exemplo, consulte [Navegar através dos objetos em uma coleção de dadosView](../../framework/wpf/data/how-to-navigate-through-the-objects-in-a-data-collectionview.md).

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

O ponteiro do item atual pode ser afetado por qualquer classificação ou filtragem aplicada à coleção. A classificação preserva o ponteiro do item atual no último item selecionado, mas a exibição de coleção está agora reestruturada em torno dele. (Talvez o item selecionado estivesse no início da lista antes, mas agora o item selecionado pode estar em algum lugar no meio.) A filtragem preserva o item selecionado se essa seleção permanecer à vista após a filtragem. Caso contrário, o ponteiro do item atual será definido como o primeiro item da exibição de coleção filtrada.

#### <a name="master-detail-binding-scenario"></a>Cenário de vinculação de detalhes mestres

A noção de um item atual é útil não somente para navegação por itens em uma coleção, mas também para o cenário de associação mestre/detalhes. Considere a ui do aplicativo na seção [O que é vinculação de dados](#what-is-data-binding) novamente. Nesse aplicativo, a seleção dentro do <xref:System.Windows.Controls.ListBox> <xref:System.Windows.Controls.ContentControl>determina o conteúdo mostrado no . Para colocá-lo de outra <xref:System.Windows.Controls.ListBox> forma, quando <xref:System.Windows.Controls.ContentControl> um item é selecionado, mostra os detalhes do item selecionado.

Você pode implementar o cenário mestre/detalhes simplesmente associando dois ou mais controles à mesma exibição. O exemplo a seguir da [demonstração][data-binding-demo] de <xref:System.Windows.Controls.ListBox> vinculação <xref:System.Windows.Controls.ContentControl> de dados mostra a marcação do e o que você vê na ui do aplicativo na seção [O que é vinculação de dados.](#what-is-data-binding)

[!code-xaml[ListBoxContentControl](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/CollectionView.xaml#ListBoxContentControl)]

Observe que ambos os controles estão vinculados à mesma fonte, o recurso estático *listingDataView* (veja a definição desse recurso na [seção Como criar uma seção de exibição](#how-to-create-a-view)). Essa vinculação funciona porque quando <xref:System.Windows.Controls.ContentControl> um objeto singleton (o neste caso) está vinculado <xref:System.Windows.Data.CollectionView.CurrentItem%2A> a uma exibição de coleção, ele se liga automaticamente à exibição. Os <xref:System.Windows.Data.CollectionViewSource> objetos sincronizam automaticamente moeda e seleção. Se o controle de sua <xref:System.Windows.Data.CollectionViewSource> lista não estiver vinculado a um <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> objeto `true` como neste exemplo, então você precisará definir sua propriedade para que isso funcione.

Para outros exemplos, consulte [Vincular a uma coleção e exibir informações com base na seleção](../../framework/wpf/data/how-to-bind-to-a-collection-and-display-information-based-on-selection.md) e [usar o padrão de detalhemestre com dados hierárquicos](../../framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-data.md).

Talvez você tenha observado que o exemplo anterior usa um modelo. Na verdade, os dados não seriam exibidos da maneira que desejamos sem <xref:System.Windows.Controls.ContentControl> o uso de modelos <xref:System.Windows.Controls.ListBox>(aquele explicitamente usado pelo e o usado implicitamente pelo ). Agora, na próxima seção, nos ocuparemos da modelagem de dados.

## <a name="data-templating"></a>Modelagem de dados

Sem o uso de modelos de dados, nossa iu de ida de dados na seção [O que é vinculação de dados](#what-is-data-binding) se pareceria com a seguinte.

![Demonstração de vinculação de dados sem modelos de dados](./media/data-binding-overview/demo-no-template.png)

Como mostrado no exemplo na seção <xref:System.Windows.Controls.ListBox> anterior, <xref:System.Windows.Controls.ContentControl> tanto o controle quanto o estão vinculados a todo o objeto de coleção (ou, mais especificamente, à exibição sobre o objeto de cobrança) do *AuctionItem*s. Sem instruções específicas de como <xref:System.Windows.Controls.ListBox> exibir a coleta de dados, o exibe <xref:System.Windows.Controls.ContentControl> a representação de string de cada objeto na coleção subjacente e exibe a representação de string do objeto ao qual está vinculado.

Para resolver esse problema, <xref:System.Windows.DataTemplate?text=DataTemplates>o aplicativo define . Como mostrado no exemplo na seção anterior, o <xref:System.Windows.Controls.ContentControl> uso explicitamente do modelo de dados *ProductListingTemplate detalhes.* O <xref:System.Windows.Controls.ListBox> controle usa implicitamente o seguinte modelo de dados ao exibir os objetos *AuctionItem* na coleção.

[!code-xaml[AuctionItemDataTemplate](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/CollectionView.xaml#AuctionItemDataTemplate)]

Com o uso desses dois DataTemplates, a ui resultante é a mostrada na seção [O que é vinculação de dados.](#what-is-data-binding) Como você pode ver a partir dessa captura de tela, além de permitir que você coloque dados em seus controles, os DataTemplates permitem que você defina visuais atraentes para seus dados. <xref:System.Windows.DataTrigger>Por exemplo, s são <xref:System.Windows.DataTemplate> usados no acima para que *AuctionItem*s com *EspecialFeatures* valor de *HighLight* seria exibido com uma borda laranja e uma estrela.

Para obter mais informações sobre modelos de dados, consulte a [visão geral do templating de dados](../../framework/wpf/data/data-templating-overview.md).

## <a name="data-validation"></a>Validação de dados

A maioria dos aplicativos que tomam a entrada do usuário precisa ter lógica de validação para garantir que o usuário tenha inserido as informações esperadas. As verificações de validação podem ser baseadas em tipo, intervalo, formato ou outros requisitos específicos do aplicativo. Esta seção discute como a validação de dados funciona no WPF.

### <a name="associating-validation-rules-with-a-binding"></a>Associar regras de validação com uma vinculação

O modelo de vinculação de <xref:System.Windows.Data.Binding.ValidationRules%2A> dados <xref:System.Windows.Data.Binding> WPF permite que você se associe ao seu objeto. Por exemplo, o exemplo <xref:System.Windows.Controls.TextBox> a seguir `StartPrice` vincula <xref:System.Windows.Controls.ExceptionValidationRule> a um <xref:System.Windows.Data.Binding.ValidationRules%2A?displayProperty=nameWithType> imóvel nomeado e adiciona um objeto à propriedade.

[!code-xaml[TextboxStartPrice](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/DataValidation.xaml#TextboxStartPrice)]

Um <xref:System.Windows.Controls.ValidationRule> objeto verifica se o valor de uma propriedade é válido. O WPF tem dois <xref:System.Windows.Controls.ValidationRule> tipos de objetos incorporados:

- Uma <xref:System.Windows.Controls.ExceptionValidationRule> verificação de exceções lançadas durante a atualização da propriedade de origem vinculante. No exemplo anterior, `StartPrice` é do tipo inteiro. Quando o usuário insere um valor que não pode ser convertido em um número inteiro, é gerada uma exceção que faz com que a associação seja marcada como inválida. Uma sintaxe alternativa <xref:System.Windows.Controls.ExceptionValidationRule> para definir o <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> explicitamente `true` é <xref:System.Windows.Data.Binding> <xref:System.Windows.Data.MultiBinding> definir a propriedade em seu objeto ou objeto.

- Um <xref:System.Windows.Controls.DataErrorValidationRule> objeto verifica se há erros levantados <xref:System.ComponentModel.IDataErrorInfo> por objetos que implementam a interface. Para um exemplo de uso <xref:System.Windows.Controls.DataErrorValidationRule>desta regra de validação, consulte . Uma sintaxe alternativa <xref:System.Windows.Controls.DataErrorValidationRule> para definir o <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A> explicitamente `true` é <xref:System.Windows.Data.Binding> <xref:System.Windows.Data.MultiBinding> definir a propriedade em seu objeto ou objeto.

Você também pode criar sua própria regra <xref:System.Windows.Controls.ValidationRule> de validação, <xref:System.Windows.Controls.ValidationRule.Validate%2A> derivando da classe e implementando o método. O exemplo a seguir mostra a regra usada <xref:System.Windows.Controls.TextBox> pela *"Data* de início" da listagem de produtos adicionados da seção [O que é vinculação de dados.](#what-is-data-binding)

[!code-csharp[FutureDateRule](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/FutureDateRule.cs#FutureDateRule)]
[!code-vb[FutureDateRule](~/samples/snippets/desktop-guide/wpf/data-binding-overview/vb/FutureDateRule.vb#FutureDateRule)]

O *StartDateEntryForm* <xref:System.Windows.Controls.TextBox> usa esta *Regra de Data de Futuro,* como mostrado no exemplo a seguir.

[!code-xaml[TextboxStartDate](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/DataValidation.xaml#TextboxStartDate)]

Como <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> o <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>valor é , o mecanismo de ligação atualiza o valor de origem <xref:System.Windows.Data.Binding.ValidationRules%2A> em cada tecla, o que significa que ele também verifica todas as regras da coleção em cada tecla. Discutiremos isso de modo mais aprofundado na seção Processo de validação.

### <a name="providing-visual-feedback"></a>Fornecendo feedback visual

Se o usuário inserir um valor inválido, você pode querer fornecer algum feedback sobre o erro na ia do aplicativo. Uma maneira de fornecer esse <xref:System.Windows.Controls.Validation.ErrorTemplate%2A?displayProperty=nameWithType> feedback é definir <xref:System.Windows.Controls.ControlTemplate>a propriedade anexada como um costume . Como mostrado na subseção anterior, o <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> *StartDateEntryForm* <xref:System.Windows.Controls.TextBox> usa um chamado *validApartir*. O exemplo a seguir mostra a definição de *validationTemplate*.

[!code-xaml[ControlTemplate](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/DataValidation.xaml#ControlTemplate)]

O <xref:System.Windows.Controls.AdornedElementPlaceholder> elemento especifica onde o controle que está sendo adornado deve ser colocado.

Além disso, você também <xref:System.Windows.Controls.ToolTip> pode usar um para exibir a mensagem de erro. Tanto o *StartDateEntryForm* quanto o *StartPriceEntryForm*<xref:System.Windows.Controls.TextBox>es usam o <xref:System.Windows.Controls.ToolTip> estilo *textStyleTextBox*, que cria um que exibe a mensagem de erro. O exemplo a seguir mostra a definição de *textStyleTextBox*. A propriedade <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> anexada é `true` quando uma ou mais das vinculações nas propriedades do elemento vinculado estão em erro.

[!code-xaml[TextBoxStyle](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/DataValidation.xaml#TextBoxStyle)]

Com o <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> personalizado <xref:System.Windows.Controls.ToolTip>e o , o *StartDateEntryForm* <xref:System.Windows.Controls.TextBox> parece o seguinte quando há um erro de validação.

![Erro de validação de vinculação de dados](./media/data-binding-overview/demo-validation-date.png "DataBindingDemo_Validation")

Se <xref:System.Windows.Data.Binding> o seu tiver regras de <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> validação associadas, mas <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> você não especificar um no controle vinculado, um padrão será usado para notificar os usuários quando houver um erro de validação. O <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> padrão é um modelo de controle que define uma borda vermelha na camada do adorno. Com o <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> padrão <xref:System.Windows.Controls.ToolTip>e o , a ui do *StartPriceEntryForm* <xref:System.Windows.Controls.TextBox> parece o seguinte quando há um erro de validação.

![Erro de validação de vinculação de dados](./media/data-binding-overview/demo-validation-price.png "DataBindingDemo_ValidationDefault")

Para obter um exemplo de como fornecer lógica para validar todos os controles em uma caixa de diálogo, consulte a seção Caixas de diálogo personalizadas na [visão geral das caixas de diálogo](../../framework/wpf/app-development/dialog-boxes-overview.md).

### <a name="validation-process"></a>Processo de validação

Geralmente, a validação ocorre quando o valor de um destino é transferido para a propriedade de origem da associação. Essa transferência <xref:System.Windows.Data.BindingMode.TwoWay> ocorre <xref:System.Windows.Data.BindingMode.OneWayToSource> em e vinculações. Para reiterar, o que causa uma atualização <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> de origem depende do valor da propriedade, conforme descrito na seção [O que desencadeia atualizações de origem.](#what-triggers-source-updates)

Os itens a seguir descrevem o processo *de validação.* Se ocorrer um erro de validação ou outro tipo de erro a qualquer momento durante esse processo, o processo será interrompido:

1. O mecanismo de ligação verifica <xref:System.Windows.Controls.ValidationRule> se <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> há algum <xref:System.Windows.Controls.ValidationStep.RawProposedValue> objeto <xref:System.Windows.Data.Binding>personalizado definido para <xref:System.Windows.Controls.ValidationRule.Validate%2A> isso, <xref:System.Windows.Controls.ValidationRule> nesse caso, ele chama o método em cada um deles até que um deles se esgote em um erro ou até que todos eles passem.

2. O mecanismo de associação então chamará o conversor, se houver.

3. Se o conversor for bem sucedido, o <xref:System.Windows.Controls.ValidationRule> mecanismo <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> de ligação <xref:System.Windows.Controls.ValidationStep.ConvertedProposedValue> verifica <xref:System.Windows.Data.Binding>se há algum <xref:System.Windows.Controls.ValidationRule.Validate%2A> objeto personalizado <xref:System.Windows.Controls.ValidationRule> definido <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> para <xref:System.Windows.Controls.ValidationStep.ConvertedProposedValue> isso, nesse caso ele chama o método em cada um que foi definido até que um deles se esgote em um erro ou até que todos eles passem.

4. O mecanismo de associação define a propriedade de origem.

5. O mecanismo de ligação verifica <xref:System.Windows.Controls.ValidationRule> se <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> há algum <xref:System.Windows.Controls.ValidationStep.UpdatedValue> objeto <xref:System.Windows.Data.Binding>personalizado definido para <xref:System.Windows.Controls.ValidationRule.Validate%2A> isso, <xref:System.Windows.Controls.ValidationRule> nesse <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> caso, <xref:System.Windows.Controls.ValidationStep.UpdatedValue> ele chama o método em cada um que foi definido até que um deles se esgote em um erro ou até que todos eles passem. Se <xref:System.Windows.Controls.DataErrorValidationRule> um estiver associado a <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> uma vinculação <xref:System.Windows.Controls.ValidationStep.UpdatedValue>e <xref:System.Windows.Controls.DataErrorValidationRule> for definido como padrão, o é verificado neste momento. Neste ponto, qualquer vinculação que tenha o <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A> conjunto para `true` é verificada.

6. O mecanismo de ligação verifica <xref:System.Windows.Controls.ValidationRule> se <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> há algum <xref:System.Windows.Controls.ValidationStep.CommittedValue> objeto <xref:System.Windows.Data.Binding>personalizado definido para <xref:System.Windows.Controls.ValidationRule.Validate%2A> isso, <xref:System.Windows.Controls.ValidationRule> nesse <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> caso, <xref:System.Windows.Controls.ValidationStep.CommittedValue> ele chama o método em cada um que foi definido até que um deles se esgote em um erro ou até que todos eles passem.

Se <xref:System.Windows.Controls.ValidationRule> um não passar em nenhum momento durante todo <xref:System.Windows.Controls.ValidationError> esse processo, <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> o mecanismo de ligação cria um objeto e o adiciona à coleção do elemento vinculado. Antes que o <xref:System.Windows.Controls.ValidationRule> motor de ligação execute os <xref:System.Windows.Controls.ValidationError> objetos em <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> qualquer etapa, ele remove qualquer um que foi adicionado à propriedade anexada do elemento vinculado durante essa etapa. Por exemplo, <xref:System.Windows.Controls.ValidationRule> se <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> um <xref:System.Windows.Controls.ValidationStep.UpdatedValue> cujo está definido como falhado, na próxima <xref:System.Windows.Controls.ValidationError> vez que o <xref:System.Windows.Controls.ValidationRule> processo <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> de <xref:System.Windows.Controls.ValidationStep.UpdatedValue>validação ocorrer, o mecanismo de vinculação removerá imediatamente antes de chamar qualquer um que tenha sido definido como .

Quando <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> não estiver <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> vazio, a propriedade anexada `true`do elemento é definida como . Além disso, <xref:System.Windows.Data.Binding.NotifyOnValidationError%2A> se <xref:System.Windows.Data.Binding> a propriedade `true`do for definido <xref:System.Windows.Controls.Validation.Error?displayProperty=nameWithType> como , então o mecanismo de ligação aumenta o evento anexado no elemento.

Observe também que uma transferência de valor válida em qualquer direção <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> (destino à origem ou fonte para destino) limpa a propriedade anexada.

Se a vinculação <xref:System.Windows.Controls.ExceptionValidationRule> tiver um associado <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> a ela, `true` ou se a propriedade estiver definida e uma exceção for lançada <xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A>quando o mecanismo de ligação definir a origem, o mecanismo de ligação verifica se há um . Você tem a opção <xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A> de usar o retorno de chamada para fornecer um manipulador personalizado para lidar com exceções. Se <xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A> um não for <xref:System.Windows.Data.Binding>especificado no , <xref:System.Windows.Controls.ValidationError> o mecanismo de ligação <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> cria um com exceção e adiciona-o à coleção do elemento vinculado.

## <a name="debugging-mechanism"></a>Mecanismo de depuração

Você pode definir a <xref:System.Diagnostics.PresentationTraceSources.TraceLevel%2A?displayProperty=nameWithType> propriedade anexada em um objeto relacionado à vinculação para receber informações sobre o status de uma vinculação específica.

## <a name="see-also"></a>Confira também

- <xref:System.Windows.Controls.DataErrorValidationRule>
- [Vincular-se aos resultados de uma consulta LINQ](../../framework/wpf/data/how-to-bind-to-the-results-of-a-linq-query.md)
- [Associação de dados](../../framework/wpf/advanced/optimizing-performance-data-binding.md)
- [Demonstração de vinculação de dados][data-binding-demo]
- [Artigos de como fazer](../../framework/wpf/data/data-binding-how-to-topics.md)
- [Associar a uma fonte de dados ADO.NET](../../framework/wpf/data/how-to-bind-to-an-ado-net-data-source.md)

[data-binding-demo]: https://github.com/microsoft/WPF-Samples/tree/master/Sample%20Applications/DataBindingDemo "aplicativo de demonstração de vinculação de dados"
