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
ms.openlocfilehash: 435789e0d1bc601a9eb51488254407fefd334e05
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44185909"
---
# <a name="customizing-the-appearance-of-an-existing-control-by-creating-a-controltemplate"></a>Personalizando a aparência de um controle existente criando um ControlTemplate
<a name="introduction"></a> Um <xref:System.Windows.Controls.ControlTemplate> Especifica a estrutura visual e o comportamento visual de um controle. Você pode personalizar a aparência de um controle, fornecendo uma nova <xref:System.Windows.Controls.ControlTemplate>. Quando você cria um <xref:System.Windows.Controls.ControlTemplate>, substitua a aparência de um controle existente sem alterar sua funcionalidade. Por exemplo, você pode tornar os botões em seu aplicativo redondos em vez da forma quadrada padrão, mas o botão ainda gerará o <xref:System.Windows.Controls.Primitives.ButtonBase.Click> eventos.  
  
 Este tópico explica as várias partes de um <xref:System.Windows.Controls.ControlTemplate>, demonstra como criar um simples <xref:System.Windows.Controls.ControlTemplate> para um <xref:System.Windows.Controls.Button>e explica como compreender o contrato de controle de um controle para que você possa personalizar sua aparência. Como você criar uma <xref:System.Windows.Controls.ControlTemplate> em [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], você pode alterar a aparência de um controle sem escrever nenhum código. Você também pode usar um designer, por exemplo, o Microsoft Expression Blend, para criar modelos de controle personalizado. Este tópico mostra exemplos de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] que personalizam a aparência de um <xref:System.Windows.Controls.Button> e lista o exemplo completo no final do tópico. Para obter mais informações sobre como usar o Expression Blend, consulte [Definir o estilo de um controle que dá suporte a modelos](https://go.microsoft.com/fwlink/?LinkId=161153).  
  
 As ilustrações mostram uma <xref:System.Windows.Controls.Button> que usa o <xref:System.Windows.Controls.ControlTemplate> que é criado neste tópico.  
  
 ![Um botão com um modelo de controle personalizado. ](../../../../docs/framework/wpf/controls/media/ndp-buttonnormal.png "NDP_ButtonNormal")  
Um botão que usa um modelo de controle personalizado  
  
 ![Um botão com uma borda vermelha. ](../../../../docs/framework/wpf/controls/media/ndp-buttonmouseover.png "NDP_ButtonMouseOver")  
Um botão que usa um modelo de controle personalizado e tem o ponteiro do mouse sobre ele  
  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Pré-requisitos  
 Este tópico presume que você entenda como criar e usar controles e estilos, conforme discutido em [Controles](../../../../docs/framework/wpf/controls/index.md). Os conceitos discutidos neste tópico se aplicam aos elementos que herdam de <xref:System.Windows.Controls.Control> classe, exceto para o <xref:System.Windows.Controls.UserControl>. Não é possível aplicar uma <xref:System.Windows.Controls.ControlTemplate> para um <xref:System.Windows.Controls.UserControl>.  
  
<a name="when_you_should_create_a_controltemplate"></a>   
## <a name="when-you-should-create-a-controltemplate"></a>Quando você criar um ControlTemplate  
 Controles têm várias propriedades, tais como <xref:System.Windows.Controls.Border.Background%2A>, <xref:System.Windows.Controls.Control.Foreground%2A>, e <xref:System.Windows.Controls.Control.FontFamily%2A>, que você pode definir para especificar diferentes aspectos da aparência do controle, mas as alterações que você pode fazer ao definir essas propriedades são limitadas. Por exemplo, você pode definir as <xref:System.Windows.Controls.Control.Foreground%2A> propriedade para azul e <xref:System.Windows.Controls.Control.FontStyle%2A> para itálico em uma <xref:System.Windows.Controls.CheckBox>.  
  
 Sem a capacidade de criar um novo <xref:System.Windows.Controls.ControlTemplate> para controles, todos os controles em cada [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-aplicativo com base teria a mesma aparência geral, o que limitaria a capacidade de criar um aplicativo com uma aparência personalizada. Por padrão, cada <xref:System.Windows.Controls.CheckBox> tem características semelhantes. Por exemplo, o conteúdo do <xref:System.Windows.Controls.CheckBox> sempre está à direita do indicador de seleção, e a marca de seleção é sempre usada para indicar que o <xref:System.Windows.Controls.CheckBox> está selecionado.  
  
 Você cria um <xref:System.Windows.Controls.ControlTemplate> quando você deseja personalizar a aparência do controle além do que as outras propriedades de configuração no controle fará. No exemplo do <xref:System.Windows.Controls.CheckBox>, suponha que você deseja que o conteúdo da caixa de seleção acima do indicador de seleção e você deseja que um X para indicar que o <xref:System.Windows.Controls.CheckBox> está selecionado. Especificar essas alterações na <xref:System.Windows.Controls.ControlTemplate> do <xref:System.Windows.Controls.CheckBox>.  
  
 A ilustração a seguir mostra uma <xref:System.Windows.Controls.CheckBox> que usa um padrão <xref:System.Windows.Controls.ControlTemplate>.  
  
 ![Uma caixa de seleção com o modelo de controle padrão. ](../../../../docs/framework/wpf/controls/media/ndp-checkboxdefault.png "NDP_CheckBoxDefault")  
Uma caixa de seleção que usa o modelo de controle padrão  
  
 A ilustração a seguir mostra uma <xref:System.Windows.Controls.CheckBox> que usa um personalizado <xref:System.Windows.Controls.ControlTemplate> para colocar o conteúdo da <xref:System.Windows.Controls.CheckBox> acima do indicador de seleção e exibe um X quando o <xref:System.Windows.Controls.CheckBox> está selecionado.  
  
 ![Uma caixa de seleção com um modelo de controle personalizado. ](../../../../docs/framework/wpf/controls/media/ndp-checkboxcustom.png "NDP_CheckBoxCustom")  
Uma caixa de seleção que usa um modelo de controle personalizado  
  
 O <xref:System.Windows.Controls.ControlTemplate> para o <xref:System.Windows.Controls.CheckBox> neste exemplo é relativamente complexa, portanto, este tópico usa um exemplo mais simples de criar um <xref:System.Windows.Controls.ControlTemplate> para um <xref:System.Windows.Controls.Button>.  
  
<a name="changing_the_visual_structure_of_a_control"></a>   
## <a name="changing-the-visual-structure-of-a-control"></a>Alterar a estrutura visual de um controle  
 Na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], um controle é muitas vezes uma composição <xref:System.Windows.FrameworkElement> objetos. Quando você cria um <xref:System.Windows.Controls.ControlTemplate>, você combina <xref:System.Windows.FrameworkElement> objetos para criar um único controle. Um <xref:System.Windows.Controls.ControlTemplate> deve ter apenas um <xref:System.Windows.FrameworkElement> como seu elemento raiz. O elemento raiz normalmente contém outros <xref:System.Windows.FrameworkElement> objetos. A combinação de objetos compõe a estrutura visual do controle.  
  
 O exemplo a seguir cria um personalizado <xref:System.Windows.Controls.ControlTemplate> para o <xref:System.Windows.Controls.Button>. O <xref:System.Windows.Controls.ControlTemplate> cria a estrutura visual do <xref:System.Windows.Controls.Button>. Este exemplo não altera a aparência do botão quando você move o ponteiro do mouse sobre ele ou clica nele. A alteração da aparência do botão quando ele está em um estado diferente é discutida posteriormente neste tópico.  
  
 Neste exemplo, a estrutura visual consiste das seguintes partes:  
  
-   Um <xref:System.Windows.Controls.Border> nomeado `RootElement` que serve como a raiz do modelo <xref:System.Windows.FrameworkElement>.  
  
-   Um <xref:System.Windows.Controls.Grid> que é um filho de `RootElement`.  
  
-   Um <xref:System.Windows.Controls.ContentPresenter> que exibe o conteúdo do botão. O <xref:System.Windows.Controls.ContentPresenter> permite que qualquer tipo de objeto a ser exibido.  
  
 [!code-xaml[VSMButtonTemplate#BasicTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#basictemplate)]  
  
### <a name="preserving-the-functionality-of-a-controls-properties-by-using-templatebinding"></a>Preserva a funcionalidade das propriedades de um controle usando TemplateBinding  
 Quando você cria um novo <xref:System.Windows.Controls.ControlTemplate>, você ainda poderá usar as propriedades públicas para alterar a aparência do controle. O [TemplateBinding](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md) extensão de marcação é associado a uma propriedade de um elemento que está no <xref:System.Windows.Controls.ControlTemplate> a uma propriedade pública que é definida pelo controle. Quando você usa [TemplateBinding](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md), você habilita propriedades do controle para atuar como parâmetros para o modelo. Ou seja, quando uma propriedade em um controle é definida, esse valor é passado para o elemento que contém a [TemplateBinding](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md).  
  
 O exemplo a seguir repete a parte do exemplo anterior que usa o [TemplateBinding](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md) extensão de marcação para associar as propriedades dos elementos que estão na <xref:System.Windows.Controls.ControlTemplate> a propriedades públicas que são definidas pelo botão.  
  
 [!code-xaml[VSMButtonTemplate#TemplateBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#templatebinding)]  
  
 Neste exemplo, o <xref:System.Windows.Controls.Grid> tem sua <xref:System.Windows.Controls.Panel.Background%2A?displayProperty=nameWithType> modelo de propriedade associado ao <xref:System.Windows.Controls.Control.Background%2A?displayProperty=nameWithType>. Porque <xref:System.Windows.Controls.Panel.Background%2A?displayProperty=nameWithType> é o modelo associado, você pode criar vários botões que usam o mesmo <xref:System.Windows.Controls.ControlTemplate> e defina o <xref:System.Windows.Controls.Control.Background%2A?displayProperty=nameWithType> como valores diferentes em cada botão. Se <xref:System.Windows.Controls.Control.Background%2A?displayProperty=nameWithType> era o modelo não associado a uma propriedade de um elemento em de <xref:System.Windows.Controls.ControlTemplate>, definindo o <xref:System.Windows.Controls.Control.Background%2A?displayProperty=nameWithType> de um botão não tem nenhum impacto sobre a aparência do botão.  
  
 Observe que os nomes das duas propriedades não precisam ser idênticos. No exemplo anterior, o <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A?displayProperty=nameWithType> propriedade do <xref:System.Windows.Controls.Button> é o modelo associado à <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A?displayProperty=nameWithType> propriedade do <xref:System.Windows.Controls.ContentPresenter>. Isso permite que o conteúdo do botão seja posicionado horizontalmente. <xref:System.Windows.Controls.ContentPresenter> não tem uma propriedade chamada `HorizontalContentAlignment`, mas <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A?displayProperty=nameWithType> pode ser associado a <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A?displayProperty=nameWithType>. Quando você associar o modelo de uma propriedade, certifique-se de que as propriedades de origem e destino sejam do mesmo tipo.  
  
 O <xref:System.Windows.Controls.Control> classe define várias propriedades que devem ser usadas pelo modelo de controle para ter um efeito no controle quando eles são definidos. Como o <xref:System.Windows.Controls.ControlTemplate> usa a propriedade depende da propriedade. O <xref:System.Windows.Controls.ControlTemplate> deve usar a propriedade em uma das seguintes maneiras:  
  
-   Um elemento no <xref:System.Windows.Controls.ControlTemplate> modelo associado à propriedade.  
  
-   Um elemento de <xref:System.Windows.Controls.ControlTemplate> herda a propriedade de um pai <xref:System.Windows.FrameworkElement>.  
  
 A tabela a seguir lista as propriedades visuais herdadas por um controle a partir de <xref:System.Windows.Controls.Control> classe. Ele também indica se o modelo de controle padrão de um controle usa o valor da propriedade herdada ou se ele deve teu seu modelo associado.  
  
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
  
 A tabela lista apenas as propriedades visuais herdadas do <xref:System.Windows.Controls.Control> classe. Além das propriedades listadas na tabela, um controle também pode herdar de <xref:System.Windows.FrameworkElement.DataContext%2A>, <xref:System.Windows.FrameworkElement.Language%2A>, e <xref:System.Windows.Controls.TextBlock.TextDecorations%2A> propriedades de elemento framework pai.  
  
 Além disso, se o <xref:System.Windows.Controls.ContentPresenter> está no <xref:System.Windows.Controls.ControlTemplate> de uma <xref:System.Windows.Controls.ContentControl>, o <xref:System.Windows.Controls.ContentPresenter> se associará automaticamente para o <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> e <xref:System.Windows.Controls.ContentControl.Content%2A> propriedades. Da mesma forma, uma <xref:System.Windows.Controls.ItemsPresenter> que está no <xref:System.Windows.Controls.ControlTemplate> de uma <xref:System.Windows.Controls.ItemsControl> se associará automaticamente para o <xref:System.Windows.Controls.ItemsControl.Items%2A> e <xref:System.Windows.Controls.ItemsPresenter> propriedades.  
  
 O exemplo a seguir cria dois botões que usam o <xref:System.Windows.Controls.ControlTemplate> definido no exemplo anterior. O exemplo define o <xref:System.Windows.Controls.Control.Background%2A>, <xref:System.Windows.Controls.Control.Foreground%2A>, e <xref:System.Windows.Controls.Control.FontSize%2A> propriedades em cada botão. Definindo o <xref:System.Windows.Controls.Control.Background%2A> propriedade tem um efeito porque ele é o modelo associado a <xref:System.Windows.Controls.ControlTemplate>. Mesmo que o <xref:System.Windows.Controls.Control.Foreground%2A> e <xref:System.Windows.Controls.Control.FontSize%2A> propriedades não são de modelo associado, defini-las tem um efeito porque seus valores são herdados.  
  
 [!code-xaml[VSMButtonTemplate#ButtonDeclaration](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#buttondeclaration)]  
  
 O exemplo anterior produz um resultado semelhante ao mostrado na ilustração a seguir.  
  
 ![Dois botões, um azul e um roxo. ](../../../../docs/framework/wpf/controls/media/ndp-buttontwo.png "NDP_ButtonTwo")  
Dois botões com cores da tela de fundo diferentes  
  
<a name="changing_the_appearance_of_a_control_depending_on_its_state"></a>   
## <a name="changing-the-appearance-of-a-control-depending-on-its-state"></a>Alterar a aparência de um controle dependendo do seu estado  
 A diferença entre um botão com sua aparência padrão e o botão no exemplo anterior é que o botão padrão sofre uma alteração sutil quando ele está em estados diferentes. Por exemplo, a aparência do botão padrão muda quando o botão é pressionado, ou quando o ponteiro do mouse está sobre o botão. Embora o <xref:System.Windows.Controls.ControlTemplate> não altera a funcionalidade de um controle, ele altera o comportamento visual do controle. Um comportamento visual descreve a aparência do controle quando ele está em um determinado estado. Para entender a diferença entre a funcionalidade e o comportamento visual de um controle, considere o exemplo de botão. A funcionalidade do botão é acionar o <xref:System.Windows.Controls.Primitives.ButtonBase.Click> evento quando ele for clicado, mas o comportamento visual do botão é alterar sua aparência quando ele é apontado ou pressionado.  
  
 Você usa <xref:System.Windows.VisualState> objetos para especificar a aparência de um controle quando ele está em um determinado estado. Um <xref:System.Windows.VisualState> contém uma <xref:System.Windows.Media.Animation.Storyboard> que altera a aparência dos elementos que estão no <xref:System.Windows.Controls.ControlTemplate>. Você não precisa escrever nenhum código para que isso ocorra porque a lógica do controle muda de estado usando o <xref:System.Windows.VisualStateManager>. Quando o controle entra no estado especificado pelo <xref:System.Windows.VisualState.Name%2A?displayProperty=nameWithType> propriedade, o <xref:System.Windows.Media.Animation.Storyboard> começa. Quando o controle sai do estado, o <xref:System.Windows.Media.Animation.Storyboard> para.  
  
 A exemplo a seguir mostra a <xref:System.Windows.VisualState> que altera a aparência de um <xref:System.Windows.Controls.Button> quando o ponteiro do mouse está sobre ele. O <xref:System.Windows.Media.Animation.Storyboard> altera a cor da borda do botão alterando a cor do `BorderBrush`. Se você consultar a <xref:System.Windows.Controls.ControlTemplate> exemplo no início deste tópico, você deve se lembrar que `BorderBrush` é o nome da <xref:System.Windows.Media.SolidColorBrush> que é atribuído ao <xref:System.Windows.Controls.Border.Background%2A> do <xref:System.Windows.Controls.Border>.  
  
 [!code-xaml[VSMButtonTemplate#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#4)]  
  
 O controle é responsável por definir os estados como parte de seu contrato de controle, que é abordado em detalhes em [Personalizar outros controles pela compreensão do contrato de controle](#customizing_other_controls_by_understanding_the_control_contract), mais adiante neste tópico. A tabela a seguir lista os estados que são especificados para o <xref:System.Windows.Controls.Button>.  
  
|Nome do VisualState|Nome do VisualStateGroup|Descrição|  
|----------------------|---------------------------|-----------------|  
|Normal|CommonStates|O estado padrão.|  
|MouseOver|CommonStates|O ponteiro do mouse é posicionado sobre o controle.|  
|Pressionado|CommonStates|O controle é pressionado.|  
|Disabled|CommonStates|O controle está desabilitado.|  
|Focalizado|FocusStates|O controle tem foco.|  
|Sem foco|FocusStates|O controle não tem foco.|  
  
 O <xref:System.Windows.Controls.Button> define dois grupos de estado: o `CommonStates` grupo contém o `Normal`, `MouseOver`, `Pressed`, e `Disabled` estados. O grupo `FocusStates` contém os estados `Focused` e `Unfocused`. Os estados no mesmo grupo de estados são mutuamente excludentes. O controle está sempre em exatamente um estado por grupo. Por exemplo, uma <xref:System.Windows.Controls.Button> pode ter o foco mesmo quando o ponteiro do mouse não está sobre ele, portanto, uma <xref:System.Windows.Controls.Button> na `Focused` estado pode estar no `MouseOver`, `Pressed`, ou `Normal` estado.  
  
 Você adiciona <xref:System.Windows.VisualState> objetos à <xref:System.Windows.VisualStateGroup> objetos. Você adiciona <xref:System.Windows.VisualStateGroup> objetos para o <xref:System.Windows.VisualStateManager.VisualStateGroups%2A?displayProperty=nameWithType> propriedade anexada. O exemplo a seguir define o <xref:System.Windows.VisualState> objetos para o `Normal`, `MouseOver`, e `Pressed` estados, que estão todos no `CommonStates` grupo. O <xref:System.Windows.VisualState.Name%2A> de cada <xref:System.Windows.VisualState> corresponde ao nome na tabela anterior. O estado `Disabled` e os estados no grupo `FocusStates` são omitidos para manter a brevidade do exemplo, mas eles estão incluídos no exemplo inteiro no final deste tópico.  
  
> [!NOTE]
>  Certifique-se de definir a <xref:System.Windows.VisualStateManager.VisualStateGroups%2A?displayProperty=nameWithType> anexados a propriedade na raiz <xref:System.Windows.FrameworkElement> da <xref:System.Windows.Controls.ControlTemplate>.  
  
 [!code-xaml[VSMButtonTemplate#VisualStates](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#visualstates)]  
  
 O exemplo anterior produz um resultado semelhante ao mostrado nas ilustrações a seguir.  
  
 ![Um botão com um modelo de controle personalizado. ](../../../../docs/framework/wpf/controls/media/ndp-buttonnormal.png "NDP_ButtonNormal")  
Um botão que usa um modelo de controle personalizado no estado normal  
  
 ![Um botão com uma borda vermelha. ](../../../../docs/framework/wpf/controls/media/ndp-buttonmouseover.png "NDP_ButtonMouseOver")  
Um botão que usa um modelo de controle personalizado no estado de passar o mouse  
  
 ![A borda é transparente em um botão pressionado. ](../../../../docs/framework/wpf/controls/media/ndp-buttonpressed.png "NDP_ButtonPressed")  
Um botão que usa um modelo de controle personalizado no estado pressionado  
  
 Para localizar os estados visuais para controles incluídos no [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], consulte [Estilos e modelos de controle](../../../../docs/framework/wpf/controls/control-styles-and-templates.md).  
  
<a name="specifying_the_behavior_of_a_control_when_it_transitions_between_states"></a>   
## <a name="specifying-the-behavior-of-a-control-when-it-transitions-between-states"></a>Especificar o comportamento de um controle quando ele faz a transição entre estados  
 No exemplo anterior, a aparência do botão também será alterada quando o usuário clicar nele; no entanto, se o usuário não pressionar o botão por um segundo completo, ele não verá o efeito. Por padrão, a animação dura um segundo. Como os usuários têm probabilidade cliquem e liberem um botão em muito menos tempo, os comentários visuais não serão eficazes se você deixar o <xref:System.Windows.Controls.ControlTemplate> em seu estado padrão.  
  
 Você pode especificar a quantidade de tempo que leva para ocorrer para uma transição suave de um controle de um estado para outro, adicionando uma animação <xref:System.Windows.VisualTransition> objetos para o <xref:System.Windows.Controls.ControlTemplate>. Quando você cria um <xref:System.Windows.VisualTransition>, especifique um ou mais das seguintes opções:  
  
-   O tempo que leva para que uma transição entre estados ocorra.  
  
-   Alterações adicionais na aparência do controle que ocorrem durante a transição.  
  
-   Quais estados as <xref:System.Windows.VisualTransition> é aplicado a.  
  
### <a name="specifying-the-duration-of-a-transition"></a>Especificar a duração de uma transição  
 Você pode especificar quanto tempo uma transição dura definindo a <xref:System.Windows.VisualTransition.GeneratedDuration%2A> propriedade. O exemplo anterior tem um <xref:System.Windows.VisualState> que especifica que a borda do botão se torna transparente quando o botão é pressionado, mas a animação leva muito tempo para ser perceptível caso o botão é pressionado e liberado de rapidamente. Você pode usar um <xref:System.Windows.VisualTransition> para especificar a quantidade de tempo ele leva o controle para fazer a transição para o estado pressionado. O exemplo a seguir especifica que o controle utiliza um centésimo de segundo para ir para o estado pressionado.  
  
 [!code-xaml[VSMButtonTemplate#PressedTransition](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#pressedtransition)]  
  
### <a name="specifying-changes-to-the-controls-appearance-during-a-transition"></a>Especificar alterações à aparência do controle durante uma transição  
 O <xref:System.Windows.VisualTransition> contém um <xref:System.Windows.Media.Animation.Storyboard> que começa quando o controle faz a transição entre estados. Por exemplo, você pode especificar que uma determinada animação ocorre quando o controle faz a transição do estado `MouseOver` para o estado `Normal`. O exemplo a seguir cria um <xref:System.Windows.VisualTransition> que especifica que quando o usuário move o ponteiro do mouse para longe do botão, a borda do botão muda para azul, em seguida, amarelo e, então, preto em 1,5 segundos.  
  
 [!code-xaml[VSMButtonTemplate#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#8)]  
  
### <a name="specifying-when-a-visualtransition-is-applied"></a>Especificar quando uma VisualTransition é aplicada  
 Um <xref:System.Windows.VisualTransition> pode ser restrito a ser aplicado somente em determinados estados, ou ele pode ser aplicado sempre que o controle fizer a transição entre estados. No exemplo anterior, o <xref:System.Windows.VisualTransition> é aplicada quando o controle passa do `MouseOver` estado para o `Normal` estado; no exemplo antes disso, o <xref:System.Windows.VisualTransition> é aplicado quando o controle passa para o `Pressed` estado. Você restringe quando uma <xref:System.Windows.VisualTransition> é aplicada definindo o <xref:System.Windows.VisualTransition.To%2A> e <xref:System.Windows.VisualTransition.From%2A> propriedades. A tabela a seguir descreve os níveis de restrição do mais restritivo para o menos restritivo.  
  
|Tipo de restrição|Valor de partir|Valor de|  
|-------------------------|-------------------|-----------------|  
|De um estado especificado para outro estado especificado|O nome de um <xref:System.Windows.VisualState>|O nome de um <xref:System.Windows.VisualState>|  
|De qualquer estado para um estado especificado|Não definido|O nome de um <xref:System.Windows.VisualState>|  
|De um estado especificado para qualquer estado|O nome de um <xref:System.Windows.VisualState>|Não definido|  
|De qualquer estado para qualquer outro estado|Não definido|Não definido|  
  
 Você pode ter vários <xref:System.Windows.VisualTransition> objetos em um <xref:System.Windows.VisualStateGroup> que se referem ao mesmo estado, mas eles serão usados na ordem em que especifica a tabela anterior. O exemplo a seguir, há dois <xref:System.Windows.VisualTransition> objetos. Quando o controle faz a transição do `Pressed` estado para o `MouseOver` estado, o <xref:System.Windows.VisualTransition> que tem ambos <xref:System.Windows.VisualTransition.From%2A> e <xref:System.Windows.VisualTransition.To%2A> conjunto é usado. Quando o controle faz a transição de um estado diferente de `Pressed` para o estado `MouseOver`, o outro estado é usado.  
  
 [!code-xaml[VSMButtonTemplate#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#7)]  
  
 O <xref:System.Windows.VisualStateGroup> tem uma <xref:System.Windows.VisualStateGroup.Transitions%2A> propriedade que contém o <xref:System.Windows.VisualTransition> objetos que se aplicam ao <xref:System.Windows.VisualState> objetos no <xref:System.Windows.VisualStateGroup>. Como o <xref:System.Windows.Controls.ControlTemplate> autor, você é livre para incluir quaisquer <xref:System.Windows.VisualTransition> desejado. No entanto, se o <xref:System.Windows.VisualTransition.To%2A> e <xref:System.Windows.VisualTransition.From%2A> são definidas como nomes de estado que não estão na <xref:System.Windows.VisualStateGroup>, o <xref:System.Windows.VisualTransition> será ignorado.  
  
 A exemplo a seguir mostra a <xref:System.Windows.VisualStateGroup> para o `CommonStates`. O exemplo define um <xref:System.Windows.VisualTransition> para cada uma das seguintes do botão faz a transição.  
  
-   Para o estado `Pressed`.  
  
-   Para o estado `MouseOver`.  
  
-   Do estado `Pressed` para o estado `MouseOver`.  
  
-   Do estado `MouseOver` para o estado `Normal`.  
  
 [!code-xaml[VSMButtonTemplate#VisualTransitions](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#visualtransitions)]  
  
<a name="customizing_other_controls_by_understanding_the_control_contract"></a>   
## <a name="customizing-other-controls-by-understanding-the-control-contract"></a>Personalizar de outros controles pela compreensão do contrato de controle  
 Um controle que usa um <xref:System.Windows.Controls.ControlTemplate> para especificar sua estrutura visual (usando <xref:System.Windows.FrameworkElement> objetos) e o comportamento visual (usando <xref:System.Windows.VisualState> objetos) usa o modelo de controle de partes. Muitos dos controles que estão incluídos no [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 4 usam esse modelo. As partes que um <xref:System.Windows.Controls.ControlTemplate> autor precisa estar atento é comunicada por meio do contrato de controle. Quando você compreende as partes de um contrato de controle, você pode personalizar a aparência de qualquer controle que usa o modelo de controle de partes.  
  
 Um contrato de controle contém três elementos:  
  
-   Os elementos visuais usados pela lógica do controle.  
  
-   Os estados do controle e o grupo ao qual cada estado pertence.  
  
-   As propriedades públicas que afetam o controle visualmente.  
  
### <a name="visual-elements-in-the-control-contract"></a>Elementos visuais no contrato de controle  
 Às vezes, a lógica do controle interage com um <xref:System.Windows.FrameworkElement> que é o <xref:System.Windows.Controls.ControlTemplate>. Por exemplo, o controle pode manipular um evento de um de seus elementos. Quando um controle espera encontrar um determinado <xref:System.Windows.FrameworkElement> no <xref:System.Windows.Controls.ControlTemplate>, ele deve transmitir essas informações para o <xref:System.Windows.Controls.ControlTemplate> autor. O controle usa o <xref:System.Windows.TemplatePartAttribute> para transmitir o tipo de elemento que é esperado e qual deve ser o nome do elemento. O <xref:System.Windows.Controls.Button> não tem <xref:System.Windows.FrameworkElement> partes em seu contrato de controle, mas outros controles, como o <xref:System.Windows.Controls.ComboBox>, fazer.  
  
 A exemplo a seguir mostra a <xref:System.Windows.TemplatePartAttribute> objetos que são especificados no <xref:System.Windows.Controls.ComboBox> classe. A lógica de <xref:System.Windows.Controls.ComboBox> espera encontrar uma <xref:System.Windows.Controls.TextBox> denominado `PART_EditableTextBox` e uma <xref:System.Windows.Controls.Primitives.Popup> denominada `PART_Popup` no seu <xref:System.Windows.Controls.ControlTemplate>.  
  
 [!code-csharp[VSMButtonTemplate#ComboBoxContract](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/controlcontracts.cs#comboboxcontract)]
 [!code-vb[VSMButtonTemplate#ComboBoxContract](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/vsmbuttontemplate/visualbasic/window1.xaml.vb#comboboxcontract)]  
  
 O exemplo a seguir mostra um simplificada <xref:System.Windows.Controls.ControlTemplate> para o <xref:System.Windows.Controls.ComboBox> que inclui os elementos que são especificados pelo <xref:System.Windows.TemplatePartAttribute> objetos no <xref:System.Windows.Controls.ComboBox> classe.  
  
 [!code-xaml[VSMButtonTemplate#ComboBoxTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/window1.xaml#comboboxtemplate)]  
  
### <a name="states-in-the-control-contract"></a>Estados no contrato de controle  
 Os estados de um controle também são uma parte do contrato de controle. O exemplo de como criar uma <xref:System.Windows.Controls.ControlTemplate> para um <xref:System.Windows.Controls.Button> mostra como especificar a aparência de um <xref:System.Windows.Controls.Button> dependendo de seus estados. Você cria um <xref:System.Windows.VisualState> para cada estado especificado e coloca todos os <xref:System.Windows.VisualState> objetos que compartilham um <xref:System.Windows.TemplateVisualStateAttribute.GroupName%2A> em um <xref:System.Windows.VisualStateGroup>, conforme descrito na [alterando a aparência de um controle dependendo do seu estado](#changing_the_appearance_of_a_control_depending_on_its_state) anteriores desta tópico. Controles de terceiros devem especificar estados usando o <xref:System.Windows.TemplateVisualStateAttribute>, que permite que ferramentas de designer, como o Expression Blend, exponham os estados do controle para a criação de modelos de controle.  
  
 Para localizar o contrato de controle para controles incluídos no [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], consulte [Estilos e modelos de controle](../../../../docs/framework/wpf/controls/control-styles-and-templates.md).  
  
### <a name="properties-in-the-control-contract"></a>Propriedades no contrato de controle  
 As propriedades públicas que afetam visualmente o controle também estão incluídas no contrato de controle. Você pode definir essas propriedades para alterar a aparência do controle sem criar um novo <xref:System.Windows.Controls.ControlTemplate>. Você também pode usar o [TemplateBinding](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md) extensão de marcação para associar as propriedades dos elementos que estão na <xref:System.Windows.Controls.ControlTemplate> a propriedades públicas que são definidas pelo <xref:System.Windows.Controls.Button>.  
  
 O exemplo a seguir mostra o contrato de controle do botão.  
  
 [!code-csharp[VSMButtonTemplate#ButtonContract](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/controlcontracts.cs#buttoncontract)]
 [!code-vb[VSMButtonTemplate#ButtonContract](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/vsmbuttontemplate/visualbasic/window1.xaml.vb#buttoncontract)]  
  
 Ao criar uma <xref:System.Windows.Controls.ControlTemplate>, geralmente é mais fácil começar com um <xref:System.Windows.Controls.ControlTemplate> e fazer alterações nele. Você pode fazer uma das opções a seguir para alterar um existente <xref:System.Windows.Controls.ControlTemplate>:  
  
-   Usar um designer como o Expression Blend, que fornece uma interface do usuário gráfica para criar modelos de controle. Para obter mais informações, consulte [Definir o estilo de um controle que dá suporte a modelos](https://go.microsoft.com/fwlink/?LinkId=161153).  
  
-   Obter o padrão <xref:System.Windows.Controls.ControlTemplate> e editá-lo. Para localizar os modelos de controle padrão que estão inclusos no [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], consulte [Temas padrão do WPF](https://go.microsoft.com/fwlink/?LinkID=158252).  
  
<a name="complete_example"></a>   
## <a name="complete-example"></a>Exemplo completo  
 O exemplo a seguir mostra todo <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.ControlTemplate> que é discutido neste tópico.  
  
 [!code-xaml[VSMButtonTemplate#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#3)]  
  
## <a name="see-also"></a>Consulte também  
 [Estilo e modelagem](../../../../docs/framework/wpf/controls/styling-and-templating.md)
