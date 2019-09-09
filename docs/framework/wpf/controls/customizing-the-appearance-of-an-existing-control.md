---
title: Personalizando a aparência de um controle existente criando um ControlTemplate
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- control contract [WPF]
- controls [WPF], visual structure changes
- ControlTemplate [WPF], customizing for existing controls
- skinning controls [WPF]
- controls [WPF], appearance specified by state
- templates [WPF], custom for existing controls
ms.assetid: 678dd116-43a2-4b8c-82b5-6b826f126e31
ms.openlocfilehash: 63a0b724b71c4a4901c2dedcf502045a75ec405c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933724"
---
# <a name="customizing-the-appearance-of-an-existing-control-by-creating-a-controltemplate"></a>Personalizando a aparência de um controle existente criando um ControlTemplate
<a name="introduction"></a>Um <xref:System.Windows.Controls.ControlTemplate> especifica a estrutura visual e o comportamento visual de um controle. Você pode personalizar a aparência de um controle dando a ele um novo <xref:System.Windows.Controls.ControlTemplate>. Quando você cria um <xref:System.Windows.Controls.ControlTemplate>, você substitui a aparência de um controle existente sem alterar sua funcionalidade. Por exemplo, você pode fazer com que os botões em seu aplicativo sejam arredondados em vez da forma quadrada padrão, mas <xref:System.Windows.Controls.Primitives.ButtonBase.Click> o botão ainda gerará o evento.  
  
 Este tópico explica as várias partes de um <xref:System.Windows.Controls.ControlTemplate>, demonstra como criar um <xref:System.Windows.Controls.ControlTemplate> simples para <xref:System.Windows.Controls.Button>um e explica como entender o contrato de controle de um controle para que você possa personalizar sua aparência. Como você cria um <xref:System.Windows.Controls.ControlTemplate> no [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], você pode alterar a aparência de um controle sem escrever nenhum código. Você também pode usar um designer, por exemplo, o Microsoft Expression Blend, para criar modelos de controle personalizado. Este tópico mostra exemplos no [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] que personalizam a aparência de um <xref:System.Windows.Controls.Button> e listam o exemplo completo no final do tópico. Para obter mais informações sobre como usar o Expression Blend, consulte [Definir o estilo de um controle que dá suporte a modelos](https://go.microsoft.com/fwlink/?LinkId=161153).  
  
 As ilustrações a seguir <xref:System.Windows.Controls.Button> mostram um que <xref:System.Windows.Controls.ControlTemplate> usa o que é criado neste tópico.  
  
 ![Um botão com um modelo de controle personalizado.](./media/ndp-buttonnormal.png "NDP_ButtonNormal")  
Um botão que usa um modelo de controle personalizado  
  
 ![Um botão com uma borda vermelha.](./media/ndp-buttonmouseover.png "NDP_ButtonMouseOver")  
Um botão que usa um modelo de controle personalizado e tem o ponteiro do mouse sobre ele  

<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Pré-requisitos  
 Este tópico presume que você entenda como criar e usar controles e estilos, conforme discutido em [Controles](index.md). Os conceitos abordados neste tópico se aplicam a elementos que herdam da <xref:System.Windows.Controls.Control> classe, exceto para o. <xref:System.Windows.Controls.UserControl> Você não pode aplicar <xref:System.Windows.Controls.ControlTemplate> um a <xref:System.Windows.Controls.UserControl>um.  
  
<a name="when_you_should_create_a_controltemplate"></a>   
## <a name="when-you-should-create-a-controltemplate"></a>Quando você criar um ControlTemplate  
 Os controles têm muitas propriedades, <xref:System.Windows.Controls.Border.Background%2A> <xref:System.Windows.Controls.Control.Foreground%2A>como, e <xref:System.Windows.Controls.Control.FontFamily%2A>, que você pode definir para especificar diferentes aspectos da aparência do controle, mas as alterações que você pode fazer definindo essas propriedades são limitadas. Por exemplo, você pode definir a <xref:System.Windows.Controls.Control.Foreground%2A> Propriedade como azul e <xref:System.Windows.Controls.Control.FontStyle%2A> itálico em um <xref:System.Windows.Controls.CheckBox>.  
  
 Sem a capacidade de criar um novo <xref:System.Windows.Controls.ControlTemplate> para controles, todos os controles em [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]cada aplicativo baseado em todos teriam a mesma aparência geral, o que limitaria a capacidade de criar um aplicativo com uma aparência personalizada. Por padrão, cada <xref:System.Windows.Controls.CheckBox> um tem características semelhantes. Por exemplo, o conteúdo do <xref:System.Windows.Controls.CheckBox> está sempre à direita do indicador de seleção e a marca de seleção é sempre usada para indicar que o <xref:System.Windows.Controls.CheckBox> está selecionado.  
  
 Você cria um <xref:System.Windows.Controls.ControlTemplate> quando deseja personalizar a aparência do controle além do que a definição das outras propriedades no controle fará. No exemplo do <xref:System.Windows.Controls.CheckBox>, suponha que você deseja que o conteúdo da caixa de seleção esteja acima do indicador de seleção e que um X indique que o <xref:System.Windows.Controls.CheckBox> está selecionado. Você especifica essas alterações no <xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Controls.CheckBox>do.  
  
 A ilustração a seguir mostra <xref:System.Windows.Controls.CheckBox> um que usa um <xref:System.Windows.Controls.ControlTemplate>padrão.  
  
 ![Uma caixa de seleção com o modelo de controle padrão.](./media/ndp-checkboxdefault.png "NDP_CheckBoxDefault")  
Uma caixa de seleção que usa o modelo de controle padrão  
  
 A ilustração a seguir mostra <xref:System.Windows.Controls.CheckBox> um que usa um <xref:System.Windows.Controls.ControlTemplate> personalizado para <xref:System.Windows.Controls.CheckBox> posicionar o conteúdo do indicador de seleção acima e exibe um X quando <xref:System.Windows.Controls.CheckBox> o é selecionado.  
  
 ![Uma caixa de seleção com um modelo de controle personalizado.](./media/ndp-checkboxcustom.png "NDP_CheckBoxCustom")  
Uma caixa de seleção que usa um modelo de controle personalizado  
  
 O <xref:System.Windows.Controls.ControlTemplate> para o <xref:System.Windows.Controls.CheckBox> neste exemplo é relativamente complexo, portanto, este tópico usa um exemplo mais simples <xref:System.Windows.Controls.Button>de criação de <xref:System.Windows.Controls.ControlTemplate> um para.  
  
<a name="changing_the_visual_structure_of_a_control"></a>   
## <a name="changing-the-visual-structure-of-a-control"></a>Alterar a estrutura visual de um controle  
 No [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], um controle é geralmente um objeto <xref:System.Windows.FrameworkElement> composto. Quando você cria um <xref:System.Windows.Controls.ControlTemplate>, você combina <xref:System.Windows.FrameworkElement> objetos para criar um único controle. Um <xref:System.Windows.Controls.ControlTemplate> deve ter apenas um <xref:System.Windows.FrameworkElement> como seu elemento raiz. O elemento raiz geralmente contém outros <xref:System.Windows.FrameworkElement> objetos. A combinação de objetos compõe a estrutura visual do controle.  
  
 O exemplo a seguir cria um <xref:System.Windows.Controls.ControlTemplate> personalizado para <xref:System.Windows.Controls.Button>o. O <xref:System.Windows.Controls.ControlTemplate> cria a estrutura visual <xref:System.Windows.Controls.Button>do. Este exemplo não altera a aparência do botão quando você move o ponteiro do mouse sobre ele ou clica nele. A alteração da aparência do botão quando ele está em um estado diferente é discutida posteriormente neste tópico.  
  
 Neste exemplo, a estrutura visual consiste das seguintes partes:  
  
- Um <xref:System.Windows.Controls.Border> <xref:System.Windows.FrameworkElement>nome `RootElement` que serve como a raiz do modelo.  
  
- Um <xref:System.Windows.Controls.Grid> que é um filho de `RootElement`.  
  
- Um <xref:System.Windows.Controls.ContentPresenter> que exibe o conteúdo do botão. O <xref:System.Windows.Controls.ContentPresenter> habilita qualquer tipo de objeto a ser exibido.  
  
 [!code-xaml[VSMButtonTemplate#BasicTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#basictemplate)]  
  
### <a name="preserving-the-functionality-of-a-controls-properties-by-using-templatebinding"></a>Preserva a funcionalidade das propriedades de um controle usando TemplateBinding  
 Quando você cria um novo <xref:System.Windows.Controls.ControlTemplate>, ainda convém usar as propriedades públicas para alterar a aparência do controle. A extensão de marcação [TemplateBinding](../advanced/templatebinding-markup-extension.md) associa uma propriedade de um elemento que está no <xref:System.Windows.Controls.ControlTemplate> a uma propriedade pública que é definida pelo controle. Quando você usa [TemplateBinding](../advanced/templatebinding-markup-extension.md), você habilita propriedades do controle para atuar como parâmetros para o modelo. Ou seja, quando uma propriedade em um controle é definida, esse valor é passado para o elemento que contém a [TemplateBinding](../advanced/templatebinding-markup-extension.md).  
  
 O exemplo a seguir repete a parte do exemplo anterior que usa a extensão de marcação [TemplateBinding](../advanced/templatebinding-markup-extension.md) para associar Propriedades de elementos que estão nas <xref:System.Windows.Controls.ControlTemplate> propriedades públicas que são definidas pelo botão.  
  
 [!code-xaml[VSMButtonTemplate#TemplateBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#templatebinding)]  
  
 Neste exemplo, o <xref:System.Windows.Controls.Grid> tem seu <xref:System.Windows.Controls.Panel.Background%2A?displayProperty=nameWithType> modelo de propriedade associado <xref:System.Windows.Controls.Control.Background%2A?displayProperty=nameWithType>. Como <xref:System.Windows.Controls.Panel.Background%2A?displayProperty=nameWithType> o modelo está associado, você pode criar vários botões que usam o <xref:System.Windows.Controls.ControlTemplate> mesmo e definir <xref:System.Windows.Controls.Control.Background%2A?displayProperty=nameWithType> o para valores diferentes em cada botão. Se <xref:System.Windows.Controls.Control.Background%2A?displayProperty=nameWithType> não houver um modelo associado a uma propriedade de um elemento <xref:System.Windows.Controls.ControlTemplate>no, a <xref:System.Windows.Controls.Control.Background%2A?displayProperty=nameWithType> definição do de um botão não teria nenhum impacto na aparência do botão.  
  
 Observe que os nomes das duas propriedades não precisam ser idênticos. No exemplo anterior, <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A?displayProperty=nameWithType> a propriedade <xref:System.Windows.Controls.Button> do modelo <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A?displayProperty=nameWithType> is está associada <xref:System.Windows.Controls.ContentPresenter>à propriedade do. Isso permite que o conteúdo do botão seja posicionado horizontalmente. <xref:System.Windows.Controls.ContentPresenter>Não tem uma propriedade chamada `HorizontalContentAlignment`, mas <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A?displayProperty=nameWithType> pode ser associada a <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A?displayProperty=nameWithType>. Quando você associar o modelo de uma propriedade, certifique-se de que as propriedades de origem e destino sejam do mesmo tipo.  
  
 A <xref:System.Windows.Controls.Control> classe define várias propriedades que devem ser usadas pelo modelo de controle para ter um efeito sobre o controle quando elas são definidas. Como o <xref:System.Windows.Controls.ControlTemplate> usa a propriedade depende da propriedade. O <xref:System.Windows.Controls.ControlTemplate> deve usar a propriedade de uma das seguintes maneiras:  
  
- Um elemento no <xref:System.Windows.Controls.ControlTemplate> modelo é associado à propriedade.  
  
- Um elemento em <xref:System.Windows.Controls.ControlTemplate> herda a propriedade de um pai <xref:System.Windows.FrameworkElement>.  
  
 A tabela a seguir lista as propriedades visuais herdadas por um controle <xref:System.Windows.Controls.Control> da classe. Ele também indica se o modelo de controle padrão de um controle usa o valor da propriedade herdada ou se ele deve teu seu modelo associado.  
  
|Propriedade|Método de uso|  
|--------------|------------------|  
|<xref:System.Windows.Controls.Control.Background%2A>|Associação de modelo|  
|<xref:System.Windows.Controls.Control.BorderThickness%2A>|Associação de modelo|  
|<xref:System.Windows.Controls.Control.BorderBrush%2A>|Associação de modelo|  
|<xref:System.Windows.Controls.Control.FontFamily%2A>|Herança de propriedade ou associação de modelo|  
|<xref:System.Windows.Controls.Control.FontSize%2A>|Herança de propriedade ou associação de modelo|  
|<xref:System.Windows.Controls.Control.FontStretch%2A>|Herança de propriedade ou associação de modelo|  
|<xref:System.Windows.Controls.Control.FontWeight%2A>|Herança de propriedade ou associação de modelo|  
|<xref:System.Windows.Controls.Control.Foreground%2A>|Herança de propriedade ou associação de modelo|  
|<xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A>|Associação de modelo|  
|<xref:System.Windows.Controls.Control.Padding%2A>|Associação de modelo|  
|<xref:System.Windows.Controls.Control.VerticalContentAlignment%2A>|Associação de modelo|  
  
 A tabela lista apenas as propriedades visuais herdadas da <xref:System.Windows.Controls.Control> classe. Além das propriedades listadas na tabela, um controle também pode herdar as <xref:System.Windows.FrameworkElement.DataContext%2A>propriedades <xref:System.Windows.FrameworkElement.Language%2A>, e <xref:System.Windows.Controls.TextBlock.TextDecorations%2A> do elemento pai Framework.  
  
 Além disso, se <xref:System.Windows.Controls.ContentPresenter> o estiver <xref:System.Windows.Controls.ControlTemplate> no de a <xref:System.Windows.Controls.ContentControl>, o <xref:System.Windows.Controls.ContentPresenter> será automaticamente associado às <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> Propriedades e <xref:System.Windows.Controls.ContentControl.Content%2A> . Da mesma forma <xref:System.Windows.Controls.ItemsPresenter> , um que está <xref:System.Windows.Controls.ControlTemplate> no de <xref:System.Windows.Controls.ItemsControl> um será automaticamente associado às <xref:System.Windows.Controls.ItemsControl.Items%2A> propriedades <xref:System.Windows.Controls.ItemsPresenter> e.  
  
 O exemplo a seguir cria dois botões que usam <xref:System.Windows.Controls.ControlTemplate> o definido no exemplo anterior. O exemplo define as <xref:System.Windows.Controls.Control.Background%2A>propriedades <xref:System.Windows.Controls.Control.Foreground%2A>, e <xref:System.Windows.Controls.Control.FontSize%2A> em cada botão. A definição <xref:System.Windows.Controls.Control.Background%2A> da propriedade tem um efeito porque ela está associada ao <xref:System.Windows.Controls.ControlTemplate>modelo no. Embora as propriedades <xref:System.Windows.Controls.Control.Foreground%2A> e <xref:System.Windows.Controls.Control.FontSize%2A> não estejam associadas ao modelo, configurá-las tem um efeito porque seus valores são herdados.  
  
 [!code-xaml[VSMButtonTemplate#ButtonDeclaration](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#buttondeclaration)]  
  
 O exemplo anterior produz um resultado semelhante ao mostrado na ilustração a seguir.  
  
 ![Dois botões, um azul e um roxo.](./media/ndp-buttontwo.png "NDP_ButtonTwo")  
Dois botões com cores da tela de fundo diferentes  
  
<a name="changing_the_appearance_of_a_control_depending_on_its_state"></a>   
## <a name="changing-the-appearance-of-a-control-depending-on-its-state"></a>Alterar a aparência de um controle dependendo do seu estado  
 A diferença entre um botão com sua aparência padrão e o botão no exemplo anterior é que o botão padrão sofre uma alteração sutil quando ele está em estados diferentes. Por exemplo, a aparência do botão padrão muda quando o botão é pressionado, ou quando o ponteiro do mouse está sobre o botão. Embora o <xref:System.Windows.Controls.ControlTemplate> não altere a funcionalidade de um controle, ele altera o comportamento visual do controle. Um comportamento visual descreve a aparência do controle quando ele está em um determinado estado. Para entender a diferença entre a funcionalidade e o comportamento visual de um controle, considere o exemplo de botão. A funcionalidade do botão é gerar o <xref:System.Windows.Controls.Primitives.ButtonBase.Click> evento quando ele é clicado, mas o comportamento visual do botão é alterar sua aparência quando ele é apontado ou pressionado.  
  
 Você usa <xref:System.Windows.VisualState> objetos para especificar a aparência de um controle quando ele está em um determinado estado. Um <xref:System.Windows.VisualState> contém um <xref:System.Windows.Media.Animation.Storyboard> que altera a aparência dos <xref:System.Windows.Controls.ControlTemplate>elementos que estão no. Você não precisa escrever nenhum código para fazer com que isso ocorra porque a lógica do controle muda de estado usando o <xref:System.Windows.VisualStateManager>. Quando o controle entra no estado especificado pela <xref:System.Windows.VisualState.Name%2A?displayProperty=nameWithType> propriedade <xref:System.Windows.Media.Animation.Storyboard> , começa. Quando o controle sai do estado, o <xref:System.Windows.Media.Animation.Storyboard> para.  
  
 O exemplo a seguir mostra <xref:System.Windows.VisualState> o que altera a aparência de <xref:System.Windows.Controls.Button> um quando o ponteiro do mouse está sobre ele. O <xref:System.Windows.Media.Animation.Storyboard> altera a cor da borda do botão alterando a cor `BorderBrush`do. Se você se referir <xref:System.Windows.Controls.ControlTemplate> ao exemplo no início deste tópico, será lembrado que `BorderBrush` <xref:System.Windows.Media.SolidColorBrush> é o nome do que está atribuído ao <xref:System.Windows.Controls.Border.Background%2A> do <xref:System.Windows.Controls.Border>.  
  
 [!code-xaml[VSMButtonTemplate#4](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#4)]  
  
 O controle é responsável por definir os estados como parte de seu contrato de controle, que é abordado em detalhes em [Personalizar outros controles pela compreensão do contrato de controle](#customizing_other_controls_by_understanding_the_control_contract), mais adiante neste tópico. A tabela a seguir lista os Estados especificados para o <xref:System.Windows.Controls.Button>.  
  
|Nome do VisualState|Nome do VisualStateGroup|Descrição|  
|----------------------|---------------------------|-----------------|  
|Normal|CommonStates|O estado padrão.|  
|MouseOver|CommonStates|O ponteiro do mouse é posicionado sobre o controle.|  
|Pressionado|CommonStates|O controle é pressionado.|  
|Desabilitado|CommonStates|O controle está desabilitado.|  
|Focalizado|FocusStates|O controle tem foco.|  
|Sem foco|FocusStates|O controle não tem foco.|  
  
 O <xref:System.Windows.Controls.Button> define dois grupos `Normal` `MouseOver` `CommonStates` deestado`Pressed`: o grupo contém os Estados,,e.`Disabled` O grupo `FocusStates` contém os estados `Focused` e `Unfocused`. Os estados no mesmo grupo de estados são mutuamente excludentes. O controle está sempre em exatamente um estado por grupo. Por exemplo, um <xref:System.Windows.Controls.Button> pode ter foco mesmo quando o ponteiro do mouse não está sobre ele, portanto <xref:System.Windows.Controls.Button> , um `Focused` no estado pode estar no `MouseOver`estado `Pressed`, ou `Normal` .  
  
 Você adiciona <xref:System.Windows.VisualState> objetos a <xref:System.Windows.VisualStateGroup> objetos. Você adiciona <xref:System.Windows.VisualStateGroup> objetos <xref:System.Windows.VisualStateManager.VisualStateGroups%2A?displayProperty=nameWithType> à propriedade anexada. O exemplo a seguir define <xref:System.Windows.VisualState> os objetos para `Normal`os `MouseOver`Estados, `Pressed` `CommonStates` e, que estão todos no grupo. O <xref:System.Windows.VisualState.Name%2A> de cada <xref:System.Windows.VisualState> um corresponde ao nome na tabela anterior. O estado `Disabled` e os estados no grupo `FocusStates` são omitidos para manter a brevidade do exemplo, mas eles estão incluídos no exemplo inteiro no final deste tópico.  
  
> [!NOTE]
> Certifique-se de definir <xref:System.Windows.VisualStateManager.VisualStateGroups%2A?displayProperty=nameWithType> a propriedade anexada na <xref:System.Windows.FrameworkElement> raiz do <xref:System.Windows.Controls.ControlTemplate>.  
  
 [!code-xaml[VSMButtonTemplate#VisualStates](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#visualstates)]  
  
 O exemplo anterior produz um resultado semelhante ao mostrado nas ilustrações a seguir.  
  
 ![Um botão com um modelo de controle personalizado.](./media/ndp-buttonnormal.png "NDP_ButtonNormal")  
Um botão que usa um modelo de controle personalizado no estado normal  
  
 ![Um botão com uma borda vermelha.](./media/ndp-buttonmouseover.png "NDP_ButtonMouseOver")  
Um botão que usa um modelo de controle personalizado no estado de passar o mouse  
  
 ![A borda é transparente em um botão pressionado.](./media/ndp-buttonpressed.png "NDP_ButtonPressed")  
Um botão que usa um modelo de controle personalizado no estado pressionado  
  
 Para localizar os estados visuais para controles incluídos no [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], consulte [Estilos e modelos de controle](control-styles-and-templates.md).  
  
<a name="specifying_the_behavior_of_a_control_when_it_transitions_between_states"></a>   
## <a name="specifying-the-behavior-of-a-control-when-it-transitions-between-states"></a>Especificar o comportamento de um controle quando ele faz a transição entre estados  
 No exemplo anterior, a aparência do botão também será alterada quando o usuário clicar nele; no entanto, se o usuário não pressionar o botão por um segundo completo, ele não verá o efeito. Por padrão, a animação dura um segundo. Como é provável que os usuários cliquem e liberem um botão em muito menos tempo, os comentários visuais não serão efetivos se <xref:System.Windows.Controls.ControlTemplate> você deixar o em seu estado padrão.  
  
 Você pode especificar a quantidade de tempo que uma animação leva para ocorrer para fazer a transição tranqüila de um controle de um estado para outro adicionando <xref:System.Windows.VisualTransition> objetos <xref:System.Windows.Controls.ControlTemplate>ao. Ao criar um <xref:System.Windows.VisualTransition>, você especifica um ou mais dos seguintes:  
  
- O tempo que leva para que uma transição entre estados ocorra.  
  
- Alterações adicionais na aparência do controle que ocorrem durante a transição.  
  
- Que indica se <xref:System.Windows.VisualTransition> o é aplicado ao.  
  
### <a name="specifying-the-duration-of-a-transition"></a>Especificar a duração de uma transição  
 Você pode especificar quanto tempo uma transição leva definindo a <xref:System.Windows.VisualTransition.GeneratedDuration%2A> propriedade. O exemplo anterior tem um <xref:System.Windows.VisualState> que especifica que a borda do botão se torna transparente quando o botão é pressionado, mas a animação leva muito tempo para ser perceptível se o botão é rapidamente pressionado e liberado. Você pode usar um <xref:System.Windows.VisualTransition> para especificar a quantidade de tempo que o controle leva para fazer a transição para o estado pressionado. O exemplo a seguir especifica que o controle utiliza um centésimo de segundo para ir para o estado pressionado.  
  
 [!code-xaml[VSMButtonTemplate#PressedTransition](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#pressedtransition)]  
  
### <a name="specifying-changes-to-the-controls-appearance-during-a-transition"></a>Especificar alterações à aparência do controle durante uma transição  
 O <xref:System.Windows.VisualTransition> contém um <xref:System.Windows.Media.Animation.Storyboard> que começa quando o controle faz a transição entre Estados. Por exemplo, você pode especificar que uma determinada animação ocorre quando o controle faz a transição do estado `MouseOver` para o estado `Normal`. O exemplo a seguir cria <xref:System.Windows.VisualTransition> um que especifica que quando o usuário move o ponteiro do mouse para longe do botão, a borda do botão muda para azul, depois para amarelo, em seguida para preto em 1,5 segundos.  
  
 [!code-xaml[VSMButtonTemplate#8](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#8)]  
  
### <a name="specifying-when-a-visualtransition-is-applied"></a>Especificar quando uma VisualTransition é aplicada  
 Um <xref:System.Windows.VisualTransition> pode ser restrito a ser aplicado a apenas determinados Estados ou pode ser aplicado sempre que o controle faz a transição entre os Estados. No exemplo anterior <xref:System.Windows.VisualTransition> , o é aplicado quando o controle passa `MouseOver` do estado para o `Normal` estado; no exemplo antes disso, o <xref:System.Windows.VisualTransition> é aplicado quando o controle entra `Pressed` no estado. Você restringe <xref:System.Windows.VisualTransition> quando um é aplicado definindo <xref:System.Windows.VisualTransition.To%2A> as <xref:System.Windows.VisualTransition.From%2A> Propriedades e. A tabela a seguir descreve os níveis de restrição do mais restritivo para o menos restritivo.  
  
|Tipo de restrição|Valor de de|Valor de para|  
|-------------------------|-------------------|-----------------|  
|De um estado especificado para outro estado especificado|O nome de um<xref:System.Windows.VisualState>|O nome de um<xref:System.Windows.VisualState>|  
|De qualquer estado para um estado especificado|Não definido|O nome de um<xref:System.Windows.VisualState>|  
|De um estado especificado para qualquer estado|O nome de um<xref:System.Windows.VisualState>|Não definido|  
|De qualquer Estado para qualquer outro Estado|Não definido|Não definido|  
  
 Você pode ter vários <xref:System.Windows.VisualTransition> objetos em um <xref:System.Windows.VisualStateGroup> que se referem ao mesmo estado, mas eles serão usados na ordem em que a tabela anterior especifica. No exemplo a seguir, há dois <xref:System.Windows.VisualTransition> objetos. Quando o controle faz a transição do `Pressed` estado para o `MouseOver` estado, o <xref:System.Windows.VisualTransition> que tem os <xref:System.Windows.VisualTransition.From%2A> dois <xref:System.Windows.VisualTransition.To%2A> e o conjunto é usado. Quando o controle faz a transição de um estado diferente de `Pressed` para o estado `MouseOver`, o outro estado é usado.  
  
 [!code-xaml[VSMButtonTemplate#7](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#7)]  
  
 O <xref:System.Windows.VisualStateGroup> tem uma <xref:System.Windows.VisualStateGroup.Transitions%2A> propriedade que contém os <xref:System.Windows.VisualTransition> objetosque<xref:System.Windows.VisualState> se aplicam aos objetos no. <xref:System.Windows.VisualStateGroup> Como autor, você tem a liberdade de incluir qualquer <xref:System.Windows.VisualTransition> um que desejar. <xref:System.Windows.Controls.ControlTemplate> No entanto, <xref:System.Windows.VisualTransition.To%2A> se <xref:System.Windows.VisualTransition.From%2A> as propriedades e estiverem definidas como nomes de estado <xref:System.Windows.VisualStateGroup>que não estão no <xref:System.Windows.VisualTransition> , o será ignorado.  
  
 O exemplo a seguir mostra <xref:System.Windows.VisualStateGroup> o para `CommonStates`o. O exemplo define um <xref:System.Windows.VisualTransition> para cada uma das transições a seguir do botão.  
  
- Para o estado `Pressed`.  
  
- Para o estado `MouseOver`.  
  
- Do estado `Pressed` para o estado `MouseOver`.  
  
- Do estado `MouseOver` para o estado `Normal`.  
  
 [!code-xaml[VSMButtonTemplate#VisualTransitions](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#visualtransitions)]  
  
<a name="customizing_other_controls_by_understanding_the_control_contract"></a>   
## <a name="customizing-other-controls-by-understanding-the-control-contract"></a>Personalizar de outros controles pela compreensão do contrato de controle  
 Um controle que usa um <xref:System.Windows.Controls.ControlTemplate> para especificar sua estrutura visual (usando <xref:System.Windows.FrameworkElement> objetos) e o comportamento visual (usando <xref:System.Windows.VisualState> objetos) usa o modelo de controle de partes. Muitos dos controles que estão incluídos no [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 4 usam esse modelo. As partes das quais <xref:System.Windows.Controls.ControlTemplate> um autor precisa estar atento são comunicadas por meio do contrato de controle. Quando você compreende as partes de um contrato de controle, você pode personalizar a aparência de qualquer controle que usa o modelo de controle de partes.  
  
 Um contrato de controle contém três elementos:  
  
- Os elementos visuais usados pela lógica do controle.  
  
- Os estados do controle e o grupo ao qual cada estado pertence.  
  
- As propriedades públicas que afetam o controle visualmente.  
  
### <a name="visual-elements-in-the-control-contract"></a>Elementos visuais no contrato de controle  
 Às vezes, a lógica de um controle interage <xref:System.Windows.FrameworkElement> com uma que está <xref:System.Windows.Controls.ControlTemplate>no. Por exemplo, o controle pode manipular um evento de um de seus elementos. Quando um controle espera encontrar um específico <xref:System.Windows.FrameworkElement> <xref:System.Windows.Controls.ControlTemplate>no, ele deve transmitir essas informações para o <xref:System.Windows.Controls.ControlTemplate> autor. O controle usa o <xref:System.Windows.TemplatePartAttribute> para transmitir o tipo de elemento esperado e qual deve ser o nome do elemento. O <xref:System.Windows.Controls.Button> não tem <xref:System.Windows.FrameworkElement> partes em seu contrato de controle, mas outros controles, como o <xref:System.Windows.Controls.ComboBox>, fazem.  
  
 O exemplo a seguir mostra <xref:System.Windows.TemplatePartAttribute> os objetos que são especificados <xref:System.Windows.Controls.ComboBox> na classe. A lógica de <xref:System.Windows.Controls.ComboBox> espera localizar um <xref:System.Windows.Controls.TextBox> nome `PART_EditableTextBox` e um <xref:System.Windows.Controls.Primitives.Popup> nomeado `PART_Popup` em seu <xref:System.Windows.Controls.ControlTemplate>.  
  
 [!code-csharp[VSMButtonTemplate#ComboBoxContract](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/controlcontracts.cs#comboboxcontract)]
 [!code-vb[VSMButtonTemplate#ComboBoxContract](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmbuttontemplate/visualbasic/window1.xaml.vb#comboboxcontract)]  
  
 O exemplo a seguir mostra um <xref:System.Windows.Controls.ControlTemplate> simplificado <xref:System.Windows.Controls.ComboBox> para o que inclui os elementos <xref:System.Windows.TemplatePartAttribute> que são especificados <xref:System.Windows.Controls.ComboBox> pelos objetos na classe.  
  
 [!code-xaml[VSMButtonTemplate#ComboBoxTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/window1.xaml#comboboxtemplate)]  
  
### <a name="states-in-the-control-contract"></a>Estados no contrato de controle  
 Os estados de um controle também são uma parte do contrato de controle. O exemplo de criação de <xref:System.Windows.Controls.ControlTemplate> um para <xref:System.Windows.Controls.Button> um mostra como especificar a aparência de um <xref:System.Windows.Controls.Button> dependendo de seus Estados. Você cria um <xref:System.Windows.VisualState> para cada estado especificado e coloca todos <xref:System.Windows.VisualState> os objetos que compartilham <xref:System.Windows.TemplateVisualStateAttribute.GroupName%2A> um em <xref:System.Windows.VisualStateGroup>um, conforme descrito em [alterando a aparência de um controle, dependendo do estado](#changing_the_appearance_of_a_control_depending_on_its_state) anterior neste tópico. Controles de terceiros devem especificar Estados usando o <xref:System.Windows.TemplateVisualStateAttribute>, que permite que as ferramentas de designer, como Expression Blend, exponham os Estados do controle para criar modelos de controle.  
  
 Para localizar o contrato de controle para controles incluídos no [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], consulte [Estilos e modelos de controle](control-styles-and-templates.md).  
  
### <a name="properties-in-the-control-contract"></a>Propriedades no contrato de controle  
 As propriedades públicas que afetam visualmente o controle também estão incluídas no contrato de controle. Você pode definir essas propriedades para alterar a aparência do controle sem criar um novo <xref:System.Windows.Controls.ControlTemplate>. Você também pode usar a extensão de marcação [TemplateBinding](../advanced/templatebinding-markup-extension.md) para associar Propriedades de elementos que estão <xref:System.Windows.Controls.ControlTemplate> nas propriedades públicas que <xref:System.Windows.Controls.Button>são definidas pelo.  
  
 O exemplo a seguir mostra o contrato de controle do botão.  
  
 [!code-csharp[VSMButtonTemplate#ButtonContract](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/controlcontracts.cs#buttoncontract)]
 [!code-vb[VSMButtonTemplate#ButtonContract](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmbuttontemplate/visualbasic/window1.xaml.vb#buttoncontract)]  
  
 Ao criar um <xref:System.Windows.Controls.ControlTemplate>, geralmente é mais fácil começar com um existente <xref:System.Windows.Controls.ControlTemplate> e fazer alterações nele. Você pode executar um dos seguintes procedimentos para alterar um existente <xref:System.Windows.Controls.ControlTemplate>:  
  
- Usar um designer como o Expression Blend, que fornece uma interface do usuário gráfica para criar modelos de controle. Para obter mais informações, consulte [Definir o estilo de um controle que dá suporte a modelos](https://go.microsoft.com/fwlink/?LinkId=161153).  
  
- Obtenha o padrão <xref:System.Windows.Controls.ControlTemplate> e edite-o. Para localizar os modelos de controle padrão que estão inclusos no [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], consulte [Temas padrão do WPF](https://go.microsoft.com/fwlink/?LinkID=158252).  
  
<a name="complete_example"></a>   
## <a name="complete-example"></a>Exemplo completo  
 O exemplo a seguir mostra a <xref:System.Windows.Controls.Button> conclusão <xref:System.Windows.Controls.ControlTemplate> que é abordada neste tópico.  
  
 [!code-xaml[VSMButtonTemplate#3](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#3)]  
  
## <a name="see-also"></a>Consulte também

- [Estilo e modelagem](styling-and-templating.md)
