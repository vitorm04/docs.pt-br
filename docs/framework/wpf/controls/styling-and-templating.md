---
title: Estilo e modelagem
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- triggers [WPF]
- styles [WPF], referencing
- event triggers [WPF]
- styles [WPF], prerequisites
- styles [WPF], declaring
- styles [WPF], overview
- styles [WPF], extending
- styles [WPF], triggers
- styles [WPF], event triggers
ms.assetid: 481765e5-5467-4a75-9f7b-e10e2ac410d9
ms.openlocfilehash: 8bd806d6b0d53d09cfca875f9f8fa844eb73ffdc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54549711"
---
# <a name="styling-and-templating"></a>Estilo e modelagem
O estilo e a modelagem do [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] se refere a um conjunto de recursos (estilos, modelos, gatilhos e storyboards) que permitem que os desenvolvedores e designers criem efeitos visualmente atraentes, além de uma aparência consistente para o produto. Embora os desenvolvedores e/ou designers possam personalizar a aparência de forma ampla conforme o aplicativo, é necessário um forte modelo de estilo e modelagem para permitir a manutenção e o compartilhamento da aparência dentro dos aplicativos e entre eles. O [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fornece esse modelo.  
  
 Outro recurso do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] modelo de estilo é a separação da apresentação e lógica. Isso significa que os designers podem trabalhar na aparência de um aplicativo usando apenas o [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], ao mesmo tempo que os desenvolvedores trabalham na lógica de programação usando C# ou Visual Basic.  
  
 Esta visão geral enfoca os aspectos de estilo e modelagem do aplicativo e não aborda conceitos de vinculação de dados. Para obter informações sobre associação de dados, consulte [Visão geral de vinculação de dados](../../../../docs/framework/wpf/data/data-binding-overview.md).  
  
 Além disso, é importante compreender os recursos, que são o que permite a reutilização dos estilos e modelos. Para obter mais informações sobre recursos, consulte [Recursos de XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md).

<a name="styling_and_templating_sample"></a>   
## <a name="styling-and-templating-sample"></a>Amostra de estilo e modelagem  
 Os exemplos de código usados nesta visão geral baseiam-se em uma amostra de foto simples, mostrada na ilustração a seguir:  
  
 ![ListView estilizada](../../../../docs/framework/wpf/controls/media/stylingintro-triggers.png "StylingIntro_triggers")  
  
 Essa amostra de foto simples usa estilo e modelagem para criar uma experiência de usuário visualmente atraente. O exemplo tem dois <xref:System.Windows.Controls.TextBlock> elementos e um <xref:System.Windows.Controls.ListBox> controle que está associado a uma lista de imagens. Para ver a amostra completa, consulte [Introdução à amostra de estilo e modelagem](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).  
  
<a name="styling_basics"></a>   
## <a name="style-basics"></a>Noções básicas de estilo  
 Você pode pensar uma <xref:System.Windows.Style> como uma maneira conveniente de aplicar um conjunto de valores de propriedade a mais de um elemento. Por exemplo, considere o seguinte <xref:System.Windows.Controls.TextBlock> elementos e sua aparência padrão:  
  
 [!code-xaml[StylingIntroSample_snippet#TextBlocks](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSample_snippet/CSharp/Window1.xaml#textblocks)]  
  
 ![Captura de tela da amostra de estilo](../../../../docs/framework/wpf/controls/media/stylingintro-textblocksbefore.PNG "StylingIntro_TextBlocksBefore")  
  
 Você pode alterar a aparência padrão definindo propriedades, como <xref:System.Windows.Controls.Control.FontSize%2A> e <xref:System.Windows.Controls.Control.FontFamily%2A>, em cada <xref:System.Windows.Controls.TextBlock> elemento diretamente. No entanto, se você quiser que seu <xref:System.Windows.Controls.TextBlock> elementos compartilhem algumas propriedades, você pode criar um <xref:System.Windows.Style> na `Resources` seção do seu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] de arquivo, como mostrado aqui:  
  
 [!code-xaml[StylingIntroSnippet#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#resources)]  
[!code-xaml[StylingIntroSnippet#tb1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#tb1)]  
[!code-xaml[StylingIntroSnippet#Resources2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#resources2)]  
  
 Quando você define o <xref:System.Windows.Style.TargetType%2A> do seu estilo para o <xref:System.Windows.Controls.TextBlock> tipo, o estilo é aplicado a todos o <xref:System.Windows.Controls.TextBlock> elementos na janela.  
  
 Agora o <xref:System.Windows.Controls.TextBlock> elementos aparecem da seguinte maneira:  
  
 ![Captura de tela da amostra de estilo](../../../../docs/framework/wpf/controls/media/stylingintro-textblocksbasestyle.PNG "StylingIntro_TextBlocksBaseStyle")  
  
### <a name="extending-styles"></a>Estendendo estilos  
 Talvez você queira que seus dois <xref:System.Windows.Controls.TextBlock> elementos compartilhem alguns valores de propriedade, como o <xref:System.Windows.Controls.Control.FontFamily%2A> e o centralizado <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>, mas você também deseja que o texto "Minhas imagens" tenha algumas propriedades adicionais. Para fazer isso, você pode criar um novo estilo baseado no primeiro estilo, como mostrado aqui:  
  
 [!code-xaml[StylingIntroSnippet#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#resources)]  
[!code-xaml[StylingIntroSnippet#tb2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#tb2)]  
[!code-xaml[StylingIntroSnippet#Resources2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#resources2)]  
  
 Observe que o estilo anterior recebe um `x:Key`. Para aplicar o estilo, você define o <xref:System.Windows.FrameworkElement.Style%2A> propriedade em seu <xref:System.Windows.Controls.TextBlock> para o `x:Key` valor, conforme mostrado aqui:  
  
 [!code-xaml[StylingIntroSnippet#UIText](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#uitext)]  
  
 Isso <xref:System.Windows.Controls.TextBlock> estilo agora tem um <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> valor de <xref:System.Windows.HorizontalAlignment.Center>, um <xref:System.Windows.Controls.TextBlock.FontFamily%2A> valor de `Comic Sans MS`, um <xref:System.Windows.Controls.TextBlock.FontSize%2A> valor de 26 e um <xref:System.Windows.Controls.TextBlock.Foreground%2A> valor definido como o <xref:System.Windows.Media.LinearGradientBrush> mostrado no exemplo a. Observe que ele substitui o <xref:System.Windows.Controls.Control.FontSize%2A> valor do estilo base. Se houver mais de um <xref:System.Windows.Setter> Configurando a mesma propriedade em um <xref:System.Windows.Style>, o <xref:System.Windows.Setter> que é declarado último terá precedência.  
  
 A seguir mostra o que o <xref:System.Windows.Controls.TextBlock> elementos a seguinte aparência:  
  
 ![TextBlocks estilizados](../../../../docs/framework/wpf/controls/media/stylingintro-textblocks.png "StylingIntro_TextBlocks")  
  
 Isso `TitleText` estilo amplia o estilo que foi criado para o <xref:System.Windows.Controls.TextBlock> tipo. Também é possível ampliar um estilo que possui um `x:Key` usando o valor `x:Key`. Para obter um exemplo, consulte o exemplo fornecido para o <xref:System.Windows.Style.BasedOn%2A> propriedade.  
  
### <a name="relationship-of-the-targettype-property-and-the-xkey-attribute"></a>Relação da propriedade TargetType com o atributo x:Key  
 Conforme mostrado no primeiro exemplo, definindo a <xref:System.Windows.Style.TargetType%2A> propriedade para `TextBlock` sem atribuir o estilo de um `x:Key` faz com que o estilo seja aplicado a todos os <xref:System.Windows.Controls.TextBlock> elementos. Nesse caso, o `x:Key` é definido implicitamente como `{x:Type TextBlock}`. Isso significa que, se você definir explicitamente o `x:Key` valor para qualquer coisa diferente de `{x:Type TextBlock}`, o <xref:System.Windows.Style> não é aplicada a todos os <xref:System.Windows.Controls.TextBlock> elementos automaticamente. Em vez disso, você deve aplicar o estilo (usando o `x:Key` valor) para o <xref:System.Windows.Controls.TextBlock> elementos explicitamente. Se o seu estilo estiver na seção de recursos e você não definir a <xref:System.Windows.Style.TargetType%2A> propriedade no seu estilo, você deve fornecer um `x:Key`.  
  
 Além de fornecer um valor padrão para o `x:Key`, o <xref:System.Windows.Style.TargetType%2A> propriedade especifica o tipo ao qual aplicam as propriedades de setter. Se você não especificar uma <xref:System.Windows.Style.TargetType%2A>, você deve qualificar as propriedades na sua <xref:System.Windows.Setter> objetos com um nome de classe usando a sintaxe `Property="ClassName.Property"`. Por exemplo, em vez de definir `Property="FontSize"`, você deve definir <xref:System.Windows.Setter.Property%2A> à `"TextBlock.FontSize"` ou `"Control.FontSize"`.  
  
 Observe, além disso, que muitos controles do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] consistem em uma combinação de outros controles do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Caso você crie um estilo que se aplica a todos os controles de um tipo, pode obter resultados inesperados. Por exemplo, se você criar um estilo que se destina a <xref:System.Windows.Controls.TextBlock> digite um <xref:System.Windows.Window>, o estilo é aplicado a todos os <xref:System.Windows.Controls.TextBlock> controles na janela, mesmo se o <xref:System.Windows.Controls.TextBlock> faz parte de outro controle, como um <xref:System.Windows.Controls.ListBox>.  
  
### <a name="styles-and-resources"></a>Estilos e recursos  
 Você pode usar um estilo em qualquer elemento que é derivada de <xref:System.Windows.FrameworkElement> ou <xref:System.Windows.FrameworkContentElement>. A maneira mais comum de declarar um estilo é como recurso na seção `Resources` de um arquivo [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], como mostrado nos exemplos anteriores. Por serem recursos, os estilos obedecem às mesmas regras de escopo que se aplicam a todos os recursos; o local onde um estilo é declarado afeta o local onde ele pode ser aplicado. Por exemplo, se você declarar o estilo no elemento raiz do arquivo [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] de definição de aplicativo, ele poderá ser utilizado em qualquer lugar do aplicativo. Se você criar um aplicativo de navegação e declarar o estilo em dos arquivos [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] do aplicativo, esse estilo poderá ser usado somente em tal arquivo [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Para obter mais informações sobre regras de escopo para recursos, consulte [Recursos de XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md).  
  
 Além disso, é possível encontrar mais informações sobre estilos e recursos em [Recursos e temas compartilhados](#styling_themes) posteriormente, nesta visão geral.  
  
### <a name="setting-styles-programmatically"></a>Definindo estilos programaticamente  
 Para atribuir um estilo nomeado para um elemento programaticamente, obtenha o estilo da coleção de recursos e atribuí-lo para o elemento <xref:System.Windows.FrameworkElement.Style%2A> propriedade. Observe que os itens em uma coleção de recursos são do tipo <xref:System.Object>. Portanto, você deve converter o estilo recuperado em uma <xref:System.Windows.Style> antes de atribuí-lo para o <xref:System.Windows.FrameworkElement.Style%2A> propriedade. Por exemplo, para definir o prefixo `TitleText` de estilo em uma <xref:System.Windows.Controls.TextBlock> denominado `textblock1`, faça o seguinte:  
  
 [!code-csharp[StylingIntroSample_snippet#Code](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSample_snippet/CSharp/Window1.xaml.cs#code)]
 [!code-vb[StylingIntroSample_snippet#Code](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StylingIntroSample_snippet/visualbasic/window1.xaml.vb#code)]  
  
 Observe que, depois de aplicado, um estilo é lacrado e não pode ser alterado. Se você quiser alterar dinamicamente um estilo que já foi aplicado, deve criar um novo estilo para substituir o existente. Para obter mais informações, consulte a propriedade <xref:System.Windows.Style.IsSealed%2A>.  
  
 É possível criar um objeto que escolhe um estilo para aplicar com base na lógica personalizada. Para obter um exemplo, consulte o exemplo fornecido para o <xref:System.Windows.Controls.StyleSelector> classe.  
  
<a name="styling_binding_dynamicresource"></a>   
### <a name="bindings-dynamic-resources-and-event-handlers"></a>Associações, recursos dinâmicos e manipuladores de eventos  
 Observe que a propriedade `Setter.Value` pode ser usada para especificar uma [Extensão de marcação de associação](../../../../docs/framework/wpf/advanced/binding-markup-extension.md) ou uma [Extensão de marcação DynamicResource](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md). Para obter mais informações, consulte os exemplos fornecidos para o <xref:System.Windows.Setter.Value%2A?displayProperty=nameWithType> propriedade.  
  
 Até o momento, esta visão geral aborda somente o uso de setters para definir o valor da propriedade. Você também pode especificar os manipuladores de eventos em um estilo. Para obter mais informações, consulte <xref:System.Windows.EventSetter>.  
  
<a name="styling_datatemplates"></a>   
## <a name="data-templates"></a>Modelos de dados  
 Neste aplicativo de exemplo, há um <xref:System.Windows.Controls.ListBox> controle que está associado a uma lista de fotos:  
  
 [!code-xaml[StylingIntroSnippet#UIListBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#uilistbox)]  
  
 Isso <xref:System.Windows.Controls.ListBox> atualmente é semelhante ao seguinte:  
  
 ![ListBox antes da aplicação do modelo](../../../../docs/framework/wpf/controls/media/stylingintro-listboxbefore.png "StylingIntro_ListBoxBefore")  
  
 A maioria dos controles tem algum tipo de conteúdo, que, frequentemente, vem dos dados aos quais você está se associando. Neste exemplo, os dados estão na lista de fotos. Na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], você usa um <xref:System.Windows.DataTemplate> para definir a representação visual dos dados. Basicamente, o que você coloca em um <xref:System.Windows.DataTemplate> determina a aparência dos dados no aplicativo renderizado.  
  
 No aplicativo de exemplo, cada objeto `Photo` personalizado tem uma propriedade `Source` de cadeia de caracteres de tipo que especifica o caminho do arquivo da imagem. Atualmente, os objetos de fotos aparecem como caminhos de arquivo.  
  
 Para que as fotos serem exibidas como imagens, você cria um <xref:System.Windows.DataTemplate> como um recurso:  
  
 [!code-xaml[StylingIntroSnippet#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#resources)]  
[!code-xaml[StylingIntroSnippet#DataTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#datatemplate)]  
[!code-xaml[StylingIntroSnippet#Resources2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#resources2)]  
  
 Observe que o <xref:System.Windows.DataTemplate.DataType%2A> propriedade é muito semelhante de <xref:System.Windows.Style.TargetType%2A> propriedade do <xref:System.Windows.Style>. Se sua <xref:System.Windows.DataTemplate> está na seção de recursos, quando você especifica a <xref:System.Windows.DataTemplate.DataType%2A> propriedade em um tipo e o atribui um `x:Key`, o <xref:System.Windows.DataTemplate> será aplicado sempre que esse tipo será exibido. Você sempre tem a opção de atribuir o <xref:System.Windows.DataTemplate> com um `x:Key` e, em seguida, defina-o como um `StaticResource` para as propriedades que usam <xref:System.Windows.DataTemplate> tipos, como o <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> propriedade ou o <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> propriedade.  
  
 Essencialmente, o <xref:System.Windows.DataTemplate> no exemplo acima define que sempre que houver uma `Photo` do objeto, ele deve aparecer como uma <xref:System.Windows.Controls.Image> dentro de um <xref:System.Windows.Controls.Border>. Com isso <xref:System.Windows.DataTemplate>, nosso aplicativo agora tem esta aparência:  
  
 ![Imagem de foto](../../../../docs/framework/wpf/controls/media/stylingintro-photosasimages.png "StylingIntro_PhotosAsImages")  
  
 O modelo de modelagem de dados fornece outros recursos. Por exemplo, se você estiver exibindo dados de coleção que contém outras coleções usando um <xref:System.Windows.Controls.HeaderedItemsControl> digite como uma <xref:System.Windows.Controls.Menu> ou um <xref:System.Windows.Controls.TreeView>, há o <xref:System.Windows.HierarchicalDataTemplate>. Outro recurso de modelagem de dados é o <xref:System.Windows.Controls.DataTemplateSelector>, que permite que você escolha um <xref:System.Windows.DataTemplate> para usar com base em lógica personalizada. Para obter mais informações, consulte [Visão geral de modelagem dos dados](../../../../docs/framework/wpf/data/data-templating-overview.md), que oferece uma discussão mais detalhada sobre os diferentes recursos de modelagem de dados.  
  
<a name="styling_controltemplates"></a>   
## <a name="control-templates"></a>Modelos de controle  
 Na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], o <xref:System.Windows.Controls.ControlTemplate> de um controle define a aparência do controle. Você pode alterar a estrutura e a aparência de um controle definindo um novo <xref:System.Windows.Controls.ControlTemplate> para o controle. Em muitos casos, isso lhe oferece flexibilidade suficiente para que você não precise gravar seus próprios controles personalizados. Para obter mais informações, consulte [Personalizando a aparência de um controle existente criando um ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).  
  
<a name="styling_triggers"></a>   
## <a name="triggers"></a>Gatilhos  
 Um gatilho define propriedades ou inicia ações, como uma animação, quando um valor da propriedade for alterado ou quando um evento for gerado. <xref:System.Windows.Style>, <xref:System.Windows.Controls.ControlTemplate>, e <xref:System.Windows.DataTemplate> todas têm um `Triggers` propriedade que pode conter um conjunto de disparadores. Existem vários tipos de gatilhos.  
  
### <a name="property-triggers"></a>Gatilhos de propriedade  
 Um <xref:System.Windows.Trigger> que a propriedade de conjuntos de valores ou inicia ações com base no valor de uma propriedade é chamado um gatilho de propriedade.  
  
 Para demonstrar como usar gatilhos de propriedade, você pode fazer cada <xref:System.Windows.Controls.ListBoxItem> parcialmente transparente, a menos que ele está selecionado. O estilo a seguir define o <xref:System.Windows.UIElement.Opacity%2A> valor de uma <xref:System.Windows.Controls.ListBoxItem> para `0.5`. Quando o <xref:System.Windows.Controls.ListBoxItem.IsSelected%2A> é de propriedade `true`, no entanto, o <xref:System.Windows.UIElement.Opacity%2A> é definido como `1.0`:  
  
 [!code-xaml[StylingIntroSample_snippet#Triggers](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSample_snippet/CSharp/Window1.xaml#triggers)]  
[!code-xaml[StylingIntroSample_snippet#EndTriggers](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSample_snippet/CSharp/Window1.xaml#endtriggers)]  
  
 Este exemplo usa uma <xref:System.Windows.Trigger> para definir um valor de propriedade, mas observe que o <xref:System.Windows.Trigger> classe também tem a <xref:System.Windows.TriggerBase.EnterActions%2A> e <xref:System.Windows.TriggerBase.ExitActions%2A> propriedades que permitem que um gatilho executar ações.  
  
 Observe que o <xref:System.Windows.FrameworkElement.MaxHeight%2A> propriedade do <xref:System.Windows.Controls.ListBoxItem> é definido como `75`. Na ilustração a seguir, o terceiro item é o item selecionado:  
  
 ![ListView estilizada](../../../../docs/framework/wpf/controls/media/stylingintro-triggers.png "StylingIntro_triggers")  
  
### <a name="eventtriggers-and-storyboards"></a>EventTriggers e storyboards  
 Outro tipo de disparador é o <xref:System.Windows.EventTrigger>, que inicia um conjunto de ações com base na ocorrência de um evento. Por exemplo, a seguinte <xref:System.Windows.EventTrigger> objetos especificam que, quando o ponteiro do mouse entra o <xref:System.Windows.Controls.ListBoxItem>, o <xref:System.Windows.FrameworkElement.MaxHeight%2A> propriedade anima a um valor de `90` sobre um `0.2` segundo período. Quando o mouse se afasta do item, a propriedade retorna para o valor original durante um período de `1` segundos. Observe como não é necessário especificar uma <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> de valor para o <xref:System.Windows.ContentElement.MouseLeave> animação. Isso ocorre porque a animação é capaz de controlar o valor original.  
  
 [!code-xaml[StylingIntroSample_snippet#EventTriggers](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSample_snippet/CSharp/Window1.xaml#eventtriggers)]  
  
 Para obter mais informações, consulte a [Visão geral de storyboards](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md).  
  
 Na ilustração a seguir, o mouse está apontando para o terceiro item:  
  
 ![Captura de tela da amostra de estilo](../../../../docs/framework/wpf/controls/media/stylingintro-eventtriggers.png "StylingIntro_EventTriggers")  
  
### <a name="multitriggers-datatriggers-and-multidatatriggers"></a>MultiTriggers, DataTriggers e MultiDataTriggers  
 Além <xref:System.Windows.Trigger> e <xref:System.Windows.EventTrigger>, há outros tipos de gatilhos. <xref:System.Windows.MultiTrigger> permite que você defina valores de propriedade com base em várias condições. Você usa <xref:System.Windows.DataTrigger> e <xref:System.Windows.MultiDataTrigger> quando a propriedade de sua condição é associado a dados.  
  
<a name="styling_themes"></a>   
## <a name="shared-resources-and-themes"></a>Recursos e temas compartilhados  
 Um aplicativo típico do Windows Presentation Foundation (WPF) pode ter vários recursos de interface do usuário do usuário que são aplicados em todo o aplicativo. Coletivamente, esse conjunto de recursos pode ser considerado o tema do aplicativo. Windows Presentation Foundation (WPF) oferece suporte para o empacotamento recursos de interface do usuário como um tema usando um dicionário de recursos que é encapsulado como o <xref:System.Windows.ResourceDictionary> classe.  
  
 Temas do Windows Presentation Foundation (WPF) são definidos usando o estilo e o mecanismo de modelagem que Windows Presentation Foundation (WPF) expõe para personalizar a aparência de qualquer elemento.  
  
 Recursos de tema do Windows Presentation Foundation (WPF) são armazenados em dicionários de recurso inserido. Esses dicionários de recursos devem ser inseridos em um assembly assinado; podem ser inseridos no mesmo assembly, como o próprio código, ou em um assembly lado a lado. No caso do PresentationFramework. dll, o assembly que contém controles do Windows Presentation Foundation (WPF), os recursos de tema ficam em uma série de assemblies lado a lado.  
  
 O tema torna-se o último local para procurar o estilo de um elemento. Normalmente, a pesquisa começará percorrendo a árvore de elementos à procura de um recurso apropriado; em seguida, examinará a coleção de recursos do aplicativo e, por fim, consultará o sistema. Assim, os desenvolvedores de aplicativos têm uma chance de redefinir o estilo de qualquer objeto no nível da árvore ou do aplicativo antes de alcançar o tema.  
  
 É possível definir os dicionários de recursos como arquivos individuais que permitem reutilizar um tema em vários aplicativos. Você também pode criar temas permutáveis definindo vários dicionários de recursos que fornecem os mesmos tipos de recursos, mas com valores diferentes. Redefinir esses estilos ou outros recursos no nível do aplicativo é a abordagem recomendada para aplicar capa em um aplicativo.  
  
 Para compartilhar um conjunto de recursos, incluindo estilos e modelos, entre aplicativos, você pode criar uma [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] do arquivo e definir um <xref:System.Windows.ResourceDictionary>. Por exemplo, dê uma olhada na ilustração a seguir que mostra parte da [Amostra de estilo com ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating):

![Exemplos de ControlTemplate](../../../../docs/framework/wpf/controls/media/stylingintro-controltemplateexamples.png "StylingIntro_ControlTemplateExamples")  
  
 Se você examinar os arquivos [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] na amostra, perceberá que todos têm o seguinte:  
  
 [!code-xaml[ControlTemplateExamples#MergedDictionaries](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/button.xaml#mergeddictionaries)]  
  
 É o compartilhamento de `shared.xaml`, que define um <xref:System.Windows.ResourceDictionary> que contém um conjunto de recursos de pincel e estilo que permite que os controles na amostra tenham uma aparência consistente.  
  
 Para obter mais informações, consulte [Dicionários de recursos mesclados](../../../../docs/framework/wpf/advanced/merged-resource-dictionaries.md).  
  
 Caso esteja criando um tema para o controle personalizado, consulte a seção Biblioteca de controle externo da [Visão geral da criação de controle](../../../../docs/framework/wpf/controls/control-authoring-overview.md).  
  
## <a name="see-also"></a>Consulte também
- [URIs "pack://" no WPF](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md)
- [Como: Localizar elementos gerados por ControlTemplate](../../../../docs/framework/wpf/controls/how-to-find-controltemplate-generated-elements.md)
- [Localizar elementos gerados por DataTemplate](../../../../docs/framework/wpf/data/how-to-find-datatemplate-generated-elements.md)
