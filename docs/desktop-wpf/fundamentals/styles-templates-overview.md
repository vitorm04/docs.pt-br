---
title: Estilos e modelos
description: Saiba mais sobre os recursos XAML no Windows Presentation Foundation (WPF) para .NET Core. Entenda os tipos de recursos XAML relacionados a estilos e temas.
author: thraka
ms.author: adegeo
ms.date: 09/09/2019
dev_langs:
- csharp
- vb
ms.openlocfilehash: f845e739ec3cae502d1e4fd6631f987c5364a42e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "82071881"
---
# <a name="styles-and-templates-in-wpf"></a>Estilos e modelos em WPF

O estilo e o templating do Windows Presentation Foundation (WPF) referem-se a um conjunto de recursos que permitem que desenvolvedores e designers criem efeitos visualmente atraentes e uma aparência consistente para seu produto. Ao personalizar a aparência de um aplicativo, você quer um modelo de estilo forte e templating que permita a manutenção e o compartilhamento da aparência dentro e entre os aplicativos. O WPF fornece esse modelo.

Outra característica do modelo de estilo WPF é a separação de apresentação e lógica. Os designers podem trabalhar na aparência de um aplicativo usando apenas XAML ao mesmo tempo em que os desenvolvedores trabalham na lógica de programação usando C# ou Visual Basic.

Essa visão geral se concentra nos aspectos de estilo e templating do aplicativo e não discute conceitos de vinculação de dados. Para obter informações sobre associação de dados, consulte [Visão geral de vinculação de dados](../data/data-binding-overview.md).

É importante entender os recursos, que são o que permitem que estilos e modelos sejam reutilizados. Para obter mais informações sobre recursos, consulte [Recursos de XAML](xaml-resources-define.md).

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

## <a name="sample"></a>Amostra

O código de exemplo fornecido nesta visão geral é baseado em um [simples aplicativo de navegação](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating) por foto mostrado na ilustração a seguir.

![Lista estilizadaVer](./media/styles-and-templates-overview/stylingintro-triggers.png "StylingIntro_triggers")

Essa amostra de foto simples usa estilo e modelagem para criar uma experiência de usuário visualmente atraente. A amostra <xref:System.Windows.Controls.TextBlock> tem dois <xref:System.Windows.Controls.ListBox> elementos e um controle que está vinculado a uma lista de imagens.

Para ver a amostra completa, consulte [Introdução à amostra de estilo e modelagem](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).

## <a name="styles"></a>Estilos

Você pode pensar <xref:System.Windows.Style> em uma maneira conveniente de aplicar um conjunto de valores de propriedade a vários elementos. Você pode usar um estilo em <xref:System.Windows.FrameworkElement> qualquer <xref:System.Windows.FrameworkContentElement> elemento <xref:System.Windows.Window> que <xref:System.Windows.Controls.Button>deriva ou como um ou um .

A maneira mais comum de declarar um `Resources` estilo é como um recurso na seção em um arquivo XAML. Como estilos são recursos, eles obedecem às mesmas regras de escopo que se aplicam a todos os recursos. Simplificando, onde você declara que um estilo afeta onde o estilo pode ser aplicado. Por exemplo, se você declarar o estilo no elemento raiz do arquivo XAML da definição do aplicativo, o estilo pode ser usado em qualquer lugar do seu aplicativo.

Por exemplo, o seguinte código XAML `TextBlock`declara dois estilos para `TextBlock` um , um aplicado automaticamente a todos os elementos, e outro que deve ser explicitamente referenciado.

[!code-xaml[SnippetDefaultTextBlockStyleBasedOn](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window2.xaml#SnippetDefaultTextBlockStyleBasedOn)]

Aqui está um exemplo dos estilos declarados acima sendo usados.

[!code-xaml[SnippetTextBlocksExplicit](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window2.xaml#SnippetTextBlocksExplicit)]

![Blocos de texto estilizados](./media/styles-and-templates-overview/stylingintro-textblocks.png)

Para obter mais informações, consulte [Criar um estilo para um controle](styles-templates-create-apply-style.md).

## <a name="controltemplates"></a>ControlTemplates

No WPF, <xref:System.Windows.Controls.ControlTemplate> o de um controle define a aparência do controle. Você pode alterar a estrutura e a <xref:System.Windows.Controls.ControlTemplate> aparência de um controle definindo um novo e atribuindo-o a um controle. Em muitos casos, os modelos lhe dão flexibilidade suficiente para que você não tenha que escrever seus próprios controles personalizados.

Cada controle tem um modelo padrão atribuído à propriedade [Control.Template.](xref:System.Windows.Controls.Control.Template) O modelo conecta a apresentação visual do controle com as capacidades do controle. Como você define um modelo em XAML, você pode alterar a aparência do controle sem escrever nenhum código. Cada modelo é projetado para um <xref:System.Windows.Controls.Button>controle específico, como um .

Geralmente você declara um modelo como `Resources` um recurso na seção de um arquivo XAML. Como em todos os recursos, as regras de escopo se aplicam.

Modelos de controle são muito mais envolvidos do que um estilo. Isso porque o modelo de controle reescreve a aparência visual de todo o controle, enquanto um estilo simplesmente aplica alterações de propriedade ao controle existente. No entanto, uma vez que o modelo de um controle é aplicado definindo a propriedade [Control.Template,](xref:System.Windows.Controls.Control.Template) você pode usar um estilo para definir ou definir um modelo.

Os designers geralmente permitem que você crie uma cópia de um modelo existente e modifique-o. Por exemplo, no designer Do Visual `CheckBox` Studio WPF, selecione um controle e, em seguida, clique com o botão direito do mouse e selecione **Editar modelo** > **Criar uma cópia**. Este comando gera um *estilo que define um modelo*.

```xaml
<Style x:Key="CheckBoxStyle1" TargetType="{x:Type CheckBox}">
    <Setter Property="FocusVisualStyle" Value="{StaticResource FocusVisual1}"/>
    <Setter Property="Background" Value="{StaticResource OptionMark.Static.Background1}"/>
    <Setter Property="BorderBrush" Value="{StaticResource OptionMark.Static.Border1}"/>
    <Setter Property="Foreground" Value="{DynamicResource {x:Static SystemColors.ControlTextBrushKey}}"/>
    <Setter Property="BorderThickness" Value="1"/>
    <Setter Property="Template">
        <Setter.Value>
            <ControlTemplate TargetType="{x:Type CheckBox}">
                <Grid x:Name="templateRoot" Background="Transparent" SnapsToDevicePixels="True">
                    <Grid.ColumnDefinitions>
                        <ColumnDefinition Width="Auto"/>
                        <ColumnDefinition Width="*"/>
                    </Grid.ColumnDefinitions>
                    <Border x:Name="checkBoxBorder" Background="{TemplateBinding Background}" BorderThickness="{TemplateBinding BorderThickness}" BorderBrush="{TemplateBinding BorderBrush}" HorizontalAlignment="{TemplateBinding HorizontalContentAlignment}" Margin="1" VerticalAlignment="{TemplateBinding VerticalContentAlignment}">
                        <Grid x:Name="markGrid">
                            <Path x:Name="optionMark" Data="F1 M 9.97498,1.22334L 4.6983,9.09834L 4.52164,9.09834L 0,5.19331L 1.27664,3.52165L 4.255,6.08833L 8.33331,1.52588e-005L 9.97498,1.22334 Z " Fill="{StaticResource OptionMark.Static.Glyph1}" Margin="1" Opacity="0" Stretch="None"/>
                            <Rectangle x:Name="indeterminateMark" Fill="{StaticResource OptionMark.Static.Glyph1}" Margin="2" Opacity="0"/>
                        </Grid>
                    </Border>
                    <ContentPresenter x:Name="contentPresenter" Grid.Column="1" Focusable="False" HorizontalAlignment="{TemplateBinding HorizontalContentAlignment}" Margin="{TemplateBinding Padding}" RecognizesAccessKey="True" SnapsToDevicePixels="{TemplateBinding SnapsToDevicePixels}" VerticalAlignment="{TemplateBinding VerticalContentAlignment}"/>
                </Grid>
                <ControlTemplate.Triggers>
                    <Trigger Property="HasContent" Value="true">
                        <Setter Property="FocusVisualStyle" Value="{StaticResource OptionMarkFocusVisual1}"/>
                        <Setter Property="Padding" Value="4,-1,0,0"/>

... content removed to save space ...
```

Editar uma cópia de um modelo é uma ótima maneira de aprender como os modelos funcionam. Em vez de criar um novo modelo em branco, é mais fácil editar uma cópia e alterar alguns aspectos da apresentação visual.

Por exemplo, consulte [Criar um modelo para um controle](../themes/how-to-create-apply-template.md).

### <a name="templatebinding"></a>TemplateBinding

Você deve ter notado que o recurso de modelo definido na seção anterior usa a [extensão de marcação de vinculação de modelos](../../framework/wpf/advanced/templatebinding-markup-extension.md). A `TemplateBinding` é uma forma otimizada de uma vinculação para cenários `{Binding RelativeSource={RelativeSource TemplatedParent}}`de modelo, análoga a uma vinculação construída com . `TemplateBinding`é útil para vincular partes do modelo às propriedades do controle. Por exemplo, cada <xref:System.Windows.Controls.Control.BorderThickness> controle tem uma propriedade. Use `TemplateBinding` a para gerenciar qual elemento no modelo é afetado por essa configuração de controle.

### <a name="contentcontrol-and-itemscontrol"></a>Controle de conteúdo e itensControle

Se <xref:System.Windows.Controls.ContentPresenter> um for declarado <xref:System.Windows.Controls.ControlTemplate> no <xref:System.Windows.Controls.ContentControl>de <xref:System.Windows.Controls.ContentPresenter> a, a <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> vontade <xref:System.Windows.Controls.ContentControl.Content%2A> automaticamente se ligará às propriedades. Da mesma <xref:System.Windows.Controls.ItemsPresenter> forma, um <xref:System.Windows.Controls.ControlTemplate> que <xref:System.Windows.Controls.ItemsControl> está no de <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> <xref:System.Windows.Controls.ItemsControl.Items%2A> um irá automaticamente ligar-se ao e propriedades.

## <a name="datatemplates"></a>Datatemplates

Neste aplicativo de exemplo, <xref:System.Windows.Controls.ListBox> há um controle que está vinculado a uma lista de fotos.

[!code-xaml[ListBox](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window3.xaml#SnippetListBox)]

Este <xref:System.Windows.Controls.ListBox> atualmente se parece com o seguinte.

![ListBox antes de aplicar o modelo](./media/styles-and-templates-overview/stylingintro-listboxbefore.png "StylingIntro_ListBoxBefore")

A maioria dos controles tem algum tipo de conteúdo, que, frequentemente, vem dos dados aos quais você está se associando. Neste exemplo, os dados estão na lista de fotos. No WPF, você <xref:System.Windows.DataTemplate> usa um para definir a representação visual dos dados. Basicamente, o que <xref:System.Windows.DataTemplate> você coloca em um determina como os dados se parecem no aplicativo renderizado.

Em nosso aplicativo de `Photo` exemplo, `Source` cada objeto personalizado tem uma propriedade de string de tipo que especifica o caminho do arquivo da imagem. Atualmente, os objetos de fotos aparecem como caminhos de arquivo.

[!code-csharp[PhotoClass](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Photo.cs#PhotoClass)]
[!code-vb[PhotoClass](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/vb/Photo.vb#PhotoClass)]

Para que as fotos apareçam <xref:System.Windows.DataTemplate> como imagens, você cria um recurso.

[!code-xaml[DataTemplate](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window4.xaml#SnippetDataTemplate)]

Observe que <xref:System.Windows.DataTemplate.DataType%2A> a propriedade <xref:System.Windows.Style.TargetType%2A> é semelhante <xref:System.Windows.Style>à propriedade do . Se <xref:System.Windows.DataTemplate> o seu estiver na seção <xref:System.Windows.DataTemplate.DataType%2A> recursos, quando você especificar a propriedade para um tipo e omitir um `x:Key`, o <xref:System.Windows.DataTemplate> é aplicado sempre que esse tipo aparecer. Você sempre tem a opção <xref:System.Windows.DataTemplate> de `x:Key` atribuir o com `StaticResource` um e, em seguida, defini-lo como um para propriedades que tomam <xref:System.Windows.DataTemplate> tipos, como o <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> imóvel ou o <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> imóvel.

Essencialmente, <xref:System.Windows.DataTemplate> o exemplo acima define que sempre `Photo` que há um <xref:System.Windows.Controls.Image> objeto, <xref:System.Windows.Controls.Border>ele deve aparecer como um dentro de um . Com <xref:System.Windows.DataTemplate>isso, nosso aplicativo agora se parece com isso.

![Imagem de foto](./media/styles-and-templates-overview/stylingintro-photosasimages.png "StylingIntro_PhotosAsImages")

O modelo de modelagem de dados fornece outros recursos. Por exemplo, se você estiver exibindo dados de <xref:System.Windows.Controls.HeaderedItemsControl> coleta que <xref:System.Windows.Controls.Menu> contenham <xref:System.Windows.Controls.TreeView>outras <xref:System.Windows.HierarchicalDataTemplate>coleções usando um tipo como a ou a, há o . Outro recurso de templating de dados é o <xref:System.Windows.Controls.DataTemplateSelector>, que permite que você escolha um <xref:System.Windows.DataTemplate> para usar com base na lógica personalizada. Para obter mais informações, consulte [Visão geral de modelagem dos dados](../../framework/wpf/data/data-templating-overview.md), que oferece uma discussão mais detalhada sobre os diferentes recursos de modelagem de dados.

## <a name="triggers"></a>Gatilhos

Um gatilho define propriedades ou inicia ações, como uma animação, quando um valor da propriedade for alterado ou quando um evento for gerado. <xref:System.Windows.Style>, <xref:System.Windows.Controls.ControlTemplate>e <xref:System.Windows.DataTemplate> todos `Triggers` possuem uma propriedade que pode conter um conjunto de gatilhos. Existem vários tipos de gatilhos.

### <a name="propertytriggers"></a>Gatilhos de propriedade

Um <xref:System.Windows.Trigger> que define valores de propriedade ou inicia ações com base no valor de um imóvel é chamado de gatilho de propriedade.

Para demonstrar como usar gatilhos de <xref:System.Windows.Controls.ListBoxItem> propriedade, você pode tornar cada um parcialmente transparente, a menos que seja selecionado. O estilo a <xref:System.Windows.UIElement.Opacity%2A> seguir <xref:System.Windows.Controls.ListBoxItem> define `0.5`o valor de a . Quando <xref:System.Windows.Controls.ListBoxItem.IsSelected%2A> a `true`propriedade é <xref:System.Windows.UIElement.Opacity%2A> , no `1.0`entanto, o é definido para .

[!code-xaml[PropertyTrigger](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window5.xaml#SnippetPropertyTrigger)]

Este exemplo <xref:System.Windows.Trigger> usa um para definir um <xref:System.Windows.Trigger> valor de <xref:System.Windows.TriggerBase.EnterActions%2A> propriedade, mas observe que a classe também tem as propriedades que <xref:System.Windows.TriggerBase.ExitActions%2A> permitem que um gatilho execute ações.

Observe que <xref:System.Windows.FrameworkElement.MaxHeight%2A> a <xref:System.Windows.Controls.ListBoxItem> propriedade do `75`está definida como . Na ilustração a seguir, o terceiro item é o item selecionado.

![Lista estilizadaVer](./media/styles-and-templates-overview/stylingintro-triggers.png "StylingIntro_triggers")

### <a name="eventtriggers-and-storyboards"></a>EventTriggers e storyboards

Outro tipo de <xref:System.Windows.EventTrigger>gatilho é o , que inicia um conjunto de ações com base na ocorrência de um evento. Por exemplo, <xref:System.Windows.EventTrigger> os seguintes objetos especificam <xref:System.Windows.FrameworkElement.MaxHeight%2A> que quando o ponteiro `90` do `0.2` mouse entra no <xref:System.Windows.Controls.ListBoxItem>, a propriedade anima a um valor de mais de um segundo período. Quando o mouse se afasta do item, a propriedade retorna para o valor original durante um período de `1` segundos. Observe como não é necessário <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> especificar <xref:System.Windows.ContentElement.MouseLeave> um valor para a animação. Isso ocorre porque a animação é capaz de controlar o valor original.

[!code-xaml[StyleEventTriggers](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window6.xaml#SnippetStyleEventTriggers)]

Para obter mais informações, consulte a visão geral do [Storyboards](../../framework/wpf/graphics-multimedia/storyboards-overview.md).

Na ilustração a seguir, o mouse está apontando para o terceiro item.

![Captura de tela de amostra de estilo](./media/styles-and-templates-overview/stylingintro-eventtriggers.png "StylingIntro_EventTriggers")

### <a name="multitriggers-datatriggers-and-multidatatriggers"></a>MultiTriggers, DataTriggers e MultiDataTriggers

Além <xref:System.Windows.Trigger> disso, <xref:System.Windows.EventTrigger>existem outros tipos de gatilhos. <xref:System.Windows.MultiTrigger>permite definir valores de propriedade com base em múltiplas condições. Você <xref:System.Windows.DataTrigger> usa <xref:System.Windows.MultiDataTrigger> e quando a propriedade de sua condição está vinculada a dados.

## <a name="visual-states"></a>Estados Visuais

Os controles estão sempre em um **estado**específico. Por exemplo, quando o mouse se move sobre a superfície de um `MouseOver`controle, o controle é considerado em um estado comum de . Um controle sem um estado específico `Normal` é considerado no estado comum. Os Estados são divididos em grupos, e os estados `CommonStates`mencionados anteriormente fazem parte do grupo estatal. A maioria dos controles `CommonStates` tem `FocusStates`dois grupos estaduais: e . De cada grupo de Estado aplicado a um controle, um controle `CommonStates.MouseOver` está `FocusStates.Unfocused`sempre em um estado de cada grupo, como e . No entanto, um controle não pode estar em dois `CommonStates.Normal` `CommonStates.Disabled`estados diferentes dentro do mesmo grupo, como e . Aqui está uma tabela de estados que a maioria dos controles reconhece e usa.

| Nome do VisualState | Nome do VisualStateGroup | Descrição |
| ---------------- | --------------------- | ----------- |
| Normal           | CommonStates          | O estado padrão. |
| MouseOver        | CommonStates          | O ponteiro do mouse é posicionado sobre o controle. |
| Pressionado          | CommonStates          | O controle é pressionado. |
| Desabilitado         | CommonStates          | O controle está desabilitado. |
| Focalizado          | FocusStates           | O controle tem foco. |
| Sem foco        | FocusStates           | O controle não tem foco. |

Ao definir <xref:System.Windows.VisualStateManager?displayProperty=fullName> um no elemento raiz de um modelo de controle, você pode acionar animações quando um controle entra em um estado específico. O `VisualStateManager` declara quais combinações <xref:System.Windows.VisualState> e <xref:System.Windows.VisualStateGroup> assistir. Quando o controle entra em um estado `VisaulStateManager` assistido, a animação definida pelo é iniciada.

Por exemplo, o código XAML a seguir observa o `CommonStates.MouseOver` estado `backgroundElement`para animar a cor de preenchimento do elemento nomeado . Quando o controle `CommonStates.Normal` retorna ao estado, a `backgroundElement` cor de preenchimento do elemento nomeado é restaurada.

```xaml
<ControlTemplate x:Key="roundbutton" TargetType="Button">
    <Grid>
        <VisualStateManager.VisualStateGroups>
            <VisualStateGroup Name="CommonStates">
                <VisualState Name="Normal">
                    <ColorAnimation Storyboard.TargetName="backgroundElement"
                                    Storyboard.TargetProperty="(Shape.Fill).(SolidColorBrush.Color)"
                                    To="{TemplateBinding Background}"
                                    Duration="0:0:0.3"/>
                </VisualState>
                <VisualState Name="MouseOver">
                    <ColorAnimation Storyboard.TargetName="backgroundElement"
                                    Storyboard.TargetProperty="(Shape.Fill).(SolidColorBrush.Color)"
                                    To="Yellow"
                                    Duration="0:0:0.3"/>
                </VisualState>
            </VisualStateGroup>
        </VisualStateManager.VisualStateGroups>

        ...
```

Para obter mais informações sobre storyboards, consulte [Storyboards Overview](../../framework/wpf/graphics-multimedia/storyboards-overview.md).

## <a name="shared-resources-and-themes"></a>Recursos e temas compartilhados

Um aplicativo Típico WPF pode ter vários recursos de IU que são aplicados em todo o aplicativo. Coletivamente, esse conjunto de recursos pode ser considerado o tema do aplicativo. O WPF fornece suporte para a embalagem de recursos de UI <xref:System.Windows.ResourceDictionary> como tema usando um dicionário de recursos encapsulado como classe.

Os temas wpf são definidos usando o mecanismo de estilo e templating que o WPF expõe para personalizar o visual de qualquer elemento.

Os recursos temáticos do WPF são armazenados em dicionários de recursos incorporados. Esses dicionários de recursos devem ser inseridos em um assembly assinado; podem ser inseridos no mesmo assembly, como o próprio código, ou em um assembly lado a lado. Para PresentationFramework.dll, o conjunto que contém controles WPF, os recursos temáticos estão em uma série de conjuntos lado a lado.

O tema torna-se o último local para procurar o estilo de um elemento. Normalmente, a pesquisa começará subindo a árvore de elementos em busca de um recurso apropriado, depois procure na coleção de recursos do aplicativo e, finalmente, consultará o sistema. Isso dá aos desenvolvedores de aplicativos a chance de redefinir o estilo para qualquer objeto no nível da árvore ou aplicativo antes de chegar ao tema.

Você pode definir dicionários de recursos como arquivos individuais que permitem reutilizar um tema em vários aplicativos. Você também pode criar temas permutáveis definindo vários dicionários de recursos que fornecem os mesmos tipos de recursos, mas com valores diferentes. Redefinir esses estilos ou outros recursos no nível do aplicativo é a abordagem recomendada para esfolar um aplicativo.

Para compartilhar um conjunto de recursos, incluindo estilos e modelos, entre aplicativos, <xref:System.Windows.ResourceDictionary> você pode criar `shared.xaml` um arquivo XAML e definir um que inclua referência a um arquivo.

```xaml
<ResourceDictionary.MergedDictionaries>
  <ResourceDictionary Source="Shared.xaml" />
</ResourceDictionary.MergedDictionaries>
```

É o compartilhamento `shared.xaml`de , que <xref:System.Windows.ResourceDictionary> por si só define um que contém um conjunto de recursos de estilo e pincel, que permite que os controles em um aplicativo tenham um olhar consistente.

Para obter mais informações, consulte [dicionários de recursos mesclados](../../framework/wpf/advanced/merged-resource-dictionaries.md).

Se você estiver criando um tema para o seu controle personalizado, consulte os **recursos definidores na** seção de nível temático da [visão geral](../../framework/wpf/controls/control-authoring-overview.md#defining-resources-at-the-theme-level)de autoria do Controle .

## <a name="see-also"></a>Confira também

- [URIs "pack://" no WPF](../../framework/wpf/app-development/pack-uris-in-wpf.md)
- [Como localizar elementos gerados por ControlTemplate](../../framework/wpf/controls/how-to-find-controltemplate-generated-elements.md)
- [Encontrar elementos gerados por datatemplate](../../framework/wpf/data/how-to-find-datatemplate-generated-elements.md)
