---
title: Criando um controle que tenha uma aparência personalizável
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], customizing
- VisualStateManager [WPF], managing the state of a control
- ControlTemplate [WPF], customizing appearance
- controls [WPF], defining the visual structure and behavior of
- customizing appearance [WPF], ControlTemplate
- managing control states [WPF], VisualStateManager
- VisualStateManager [WPF], best practice
ms.assetid: 9e356d3d-a3d0-4b01-a25f-2d43e4d53fe5
ms.openlocfilehash: c98035ef0b4ea1add22b09fb9927bcd49c00cd9b
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920035"
---
# <a name="creating-a-control-that-has-a-customizable-appearance"></a>Criando um controle que tenha uma aparência personalizável

<a name="introduction"></a>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] oferece a capacidade de criar um controle cuja aparência possa ser personalizada. Por exemplo, você pode alterar a aparência de um <xref:System.Windows.Controls.CheckBox> além do que as propriedades de configuração farão, criando um novo <xref:System.Windows.Controls.ControlTemplate>. A ilustração a seguir mostra um <xref:System.Windows.Controls.CheckBox> que usa um <xref:System.Windows.Controls.ControlTemplate> padrão e uma <xref:System.Windows.Controls.CheckBox> que usa um <xref:System.Windows.Controls.ControlTemplate>personalizado.

![Uma caixa de seleção com o modelo de controle padrão.](./media/ndp-checkboxdefault.png "NDP_CheckBoxDefault")
Uma caixa de seleção que usa o modelo de controle padrão

![Uma caixa de seleção com um modelo de controle personalizado.](./media/ndp-checkboxcustom.png "NDP_CheckBoxCustom")
Uma caixa de seleção que usa um modelo de controle personalizado

Se você seguir o modelo de partes e estados ao criar um controle, a aparência do controle será personalizável. Ferramentas de designer como Blend para Visual Studio dão suporte ao modelo de partes e Estados, portanto, quando você seguir esse modelo, seu controle será personalizável nesses tipos de aplicativos.  Este tópico aborda o modelo de partes e estados e como segui-lo ao criar seu próprio controle. Este tópico usa um exemplo de um controle personalizado, `NumericUpDown`, para ilustrar a filosofia desse modelo.  O controle `NumericUpDown` exibe um valor numérico, que um usuário pode aumentar ou diminuir clicando nos botões do controle.  A ilustração a seguir mostra o controle `NumericUpDown` que é abordado neste tópico.

![Controle NumericUpDown personalizado.](./media/ndp-numericupdown.png "NDP_NumericUPDown")
Um controle NumericUpDown personalizado

Esse tópico contém as seguintes seções:

- [Pré-requisitos](#prerequisites)

- [Modelo de partes e estados](#parts_and_states_model)

- [Definindo a estrutura e o comportamento visuais de um controle em um ControlTemplate](#defining_the_visual_structure_and_visual_behavior_of_a_control_in_a_controltemplate)

- [Usando partes do ControlTemplate no código](#using_parts_of_the_controltemplate_in_code)

- [Fornecendo o contrato de controle](#providing_the_control_contract)

- [Exemplo completo](#complete_example)

<a name="prerequisites"></a>

## <a name="prerequisites"></a>Prerequisites

Este tópico pressupõe que você saiba como criar um novo <xref:System.Windows.Controls.ControlTemplate> para um controle existente, esteja familiarizado com o que são os elementos em um contrato de controle e entenda os conceitos discutidos na [personalização da aparência de um controle existente criando um ControlTemplate](customizing-the-appearance-of-an-existing-control.md).

> [!NOTE]
> Para criar um controle que pode ter sua aparência personalizada, você deve criar um controle que herda da classe <xref:System.Windows.Controls.Control> ou de uma de suas subclasses que não seja <xref:System.Windows.Controls.UserControl>.  Um controle que herda de <xref:System.Windows.Controls.UserControl> é um controle que pode ser criado rapidamente, mas não usa um <xref:System.Windows.Controls.ControlTemplate> e você não pode personalizar sua aparência.

<a name="parts_and_states_model"></a>

## <a name="parts-and-states-model"></a>Modelo de partes e estados

O modelo de partes e estados especifica como definir a estrutura e o comportamento visuais de um controle. Para seguir o modelo de partes e estados, faça o seguinte:

- Defina a estrutura visual e o comportamento visual no <xref:System.Windows.Controls.ControlTemplate> de um controle.

- Siga algumas melhores práticas quando a lógica do controle interagir com partes do modelo de controle.

- Forneça um contrato de controle para especificar o que deve ser incluído no <xref:System.Windows.Controls.ControlTemplate>.

Quando você define a estrutura visual e o comportamento visual no <xref:System.Windows.Controls.ControlTemplate> de um controle, os autores de aplicativos podem alterar a estrutura visual e o comportamento visual do seu controle criando uma nova <xref:System.Windows.Controls.ControlTemplate> em vez de escrever código.   Você deve fornecer um contrato de controle que indique aos autores do aplicativo que <xref:System.Windows.FrameworkElement> objetos e Estados devem ser definidos no <xref:System.Windows.Controls.ControlTemplate>. Você deve seguir algumas práticas recomendadas ao interagir com as partes no <xref:System.Windows.Controls.ControlTemplate> para que o controle manipule corretamente um <xref:System.Windows.Controls.ControlTemplate>incompleto.  Se você seguir esses três princípios, os autores de aplicativos poderão criar um <xref:System.Windows.Controls.ControlTemplate> para seu controle tão facilmente quanto eles puderem para os controles fornecidos com [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  A próxima seção explica cada uma dessas recomendações detalhadamente.

<a name="defining_the_visual_structure_and_visual_behavior_of_a_control_in_a_controltemplate"></a>

## <a name="defining-the-visual-structure-and-visual-behavior-of-a-control-in-a-controltemplate"></a>Definindo a estrutura e o comportamento visuais de um controle em um ControlTemplate

Quando você cria seu controle personalizado usando o modelo de partes e Estados, você define a estrutura visual do controle e o comportamento visual em seu <xref:System.Windows.Controls.ControlTemplate> em vez de em sua lógica.  A estrutura visual de um controle é a composição de <xref:System.Windows.FrameworkElement> objetos que compõem o controle.  O comportamento visual é a aparência do controle quando ele está em determinado estado.   Para obter mais informações sobre como criar um <xref:System.Windows.Controls.ControlTemplate> que especifica a estrutura visual e o comportamento visual de um controle, consulte [Personalizando a aparência de um controle existente criando um ControlTemplate](customizing-the-appearance-of-an-existing-control.md).

No exemplo do controle de `NumericUpDown`, a estrutura visual inclui dois controles <xref:System.Windows.Controls.Primitives.RepeatButton> e uma <xref:System.Windows.Controls.TextBlock>.  Se você adicionar esses controles ao código do controle `NumericUpDown` – no construtor, por exemplo –, as posições desses controles não serão alteráveis.  Em vez de definir a estrutura visual do controle e o comportamento do Visual em seu código, você deve defini-lo no <xref:System.Windows.Controls.ControlTemplate>.  Em seguida, um desenvolvedor de aplicativos para personalizar a posição dos botões e <xref:System.Windows.Controls.TextBlock> e especificar qual comportamento ocorre quando `Value` é negativo, pois o <xref:System.Windows.Controls.ControlTemplate> pode ser substituído.

O exemplo a seguir mostra a estrutura visual do controle de `NumericUpDown`, que inclui uma <xref:System.Windows.Controls.Primitives.RepeatButton> para aumentar `Value`, uma <xref:System.Windows.Controls.Primitives.RepeatButton> para diminuir `Value`e uma <xref:System.Windows.Controls.TextBlock> para exibir `Value`.

[!code-xaml[VSMCustomControl#VisualStructure](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/window1.xaml#visualstructure)]

Um comportamento visual do controle `NumericUpDown` é que o valor estará em uma fonte vermelha se for negativo.  Se você alterar o <xref:System.Windows.Controls.TextBlock.Foreground%2A> do <xref:System.Windows.Controls.TextBlock> no código quando o `Value` for negativo, o `NumericUpDown` sempre mostrará um valor negativo vermelho. Você especifica o comportamento visual do controle na <xref:System.Windows.Controls.ControlTemplate> adicionando objetos <xref:System.Windows.VisualState> ao <xref:System.Windows.Controls.ControlTemplate>.  O exemplo a seguir mostra os objetos <xref:System.Windows.VisualState> para os Estados `Positive` e `Negative`.  `Positive` e `Negative` são mutuamente exclusivos (o controle está sempre em um dos dois), portanto, o exemplo coloca os objetos <xref:System.Windows.VisualState> em um único <xref:System.Windows.VisualStateGroup>.  Quando o controle entra no estado de `Negative`, a <xref:System.Windows.Controls.TextBlock.Foreground%2A> do <xref:System.Windows.Controls.TextBlock> fica vermelha.  Quando o controle está no estado `Positive`, o <xref:System.Windows.Controls.TextBlock.Foreground%2A> retorna ao seu valor original.  Definir <xref:System.Windows.VisualState> objetos em um <xref:System.Windows.Controls.ControlTemplate> é discutido mais detalhadamente na [personalização da aparência de um controle existente por meio da criação de um ControlTemplate](customizing-the-appearance-of-an-existing-control.md).

> [!NOTE]
> Certifique-se de definir a propriedade <xref:System.Windows.VisualStateManager.VisualStateGroups%2A?displayProperty=nameWithType> anexada no <xref:System.Windows.FrameworkElement> raiz do <xref:System.Windows.Controls.ControlTemplate>.

[!code-xaml[VSMCustomControl#ValueStates](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/window1.xaml#valuestates)]

<a name="using_parts_of_the_controltemplate_in_code"></a>

## <a name="using-parts-of-the-controltemplate-in-code"></a>Usando partes do ControlTemplate no código

Um autor de <xref:System.Windows.Controls.ControlTemplate> pode omitir <xref:System.Windows.FrameworkElement> ou <xref:System.Windows.VisualState> objetos, intencionalmente ou por engano, mas a lógica do seu controle pode precisar que essas partes funcionem corretamente. O modelo de partes e Estados especifica que seu controle deve ser resiliente a um <xref:System.Windows.Controls.ControlTemplate> que está faltando <xref:System.Windows.FrameworkElement> ou <xref:System.Windows.VisualState> objetos.  Seu controle não deve gerar uma exceção ou relatar um erro se um <xref:System.Windows.FrameworkElement>, <xref:System.Windows.VisualState>ou <xref:System.Windows.VisualStateGroup> estiver faltando no <xref:System.Windows.Controls.ControlTemplate>. Esta seção descreve as práticas recomendadas para interagir com <xref:System.Windows.FrameworkElement> objetos e gerenciar Estados.

### <a name="anticipate-missing-frameworkelement-objects"></a>Prever objetos FrameworkElement ausentes

Quando você define <xref:System.Windows.FrameworkElement> objetos no <xref:System.Windows.Controls.ControlTemplate>, a lógica do controle pode precisar interagir com alguns deles.  Por exemplo, o controle de `NumericUpDown` assina o evento de <xref:System.Windows.Controls.Primitives.ButtonBase.Click> de botões para aumentar ou diminuir `Value` e define a propriedade <xref:System.Windows.Controls.TextBlock.Text%2A> do <xref:System.Windows.Controls.TextBlock> como `Value`. Se um <xref:System.Windows.Controls.ControlTemplate> personalizado omitir o <xref:System.Windows.Controls.TextBlock> ou os botões, é aceitável que o controle perca algumas de suas funcionalidades, mas você deve ter certeza de que seu controle não causa um erro. Por exemplo, se uma <xref:System.Windows.Controls.ControlTemplate> não contiver os botões a serem alterados `Value`, a `NumericUpDown` perderá essa funcionalidade, mas um aplicativo que usa o <xref:System.Windows.Controls.ControlTemplate> continuará a ser executado.

As seguintes práticas garantirão que seu controle responda corretamente a objetos <xref:System.Windows.FrameworkElement> ausentes:

1. Defina o atributo `x:Name` para cada <xref:System.Windows.FrameworkElement> que você precisa referenciar no código.

2. Defina propriedades privadas para cada <xref:System.Windows.FrameworkElement> com o qual você precisa interagir.

3. Assine e cancele a assinatura de quaisquer eventos que seu controle manipula no acessador set da propriedade <xref:System.Windows.FrameworkElement>.

4. Defina as propriedades de <xref:System.Windows.FrameworkElement> que você definiu na etapa 2 no método <xref:System.Windows.FrameworkElement.OnApplyTemplate%2A>. Esse é o primeiro que o <xref:System.Windows.FrameworkElement> no <xref:System.Windows.Controls.ControlTemplate> está disponível para o controle. Use o `x:Name` do <xref:System.Windows.FrameworkElement> para obtê-lo da <xref:System.Windows.Controls.ControlTemplate>.

5. Verifique se o <xref:System.Windows.FrameworkElement> não é `null` antes de acessar seus membros.  Se ele for `null`, não relate um erro.

Os exemplos a seguir mostram como o controle de `NumericUpDown` interage com <xref:System.Windows.FrameworkElement> objetos de acordo com as recomendações na lista anterior.

No exemplo que define a estrutura visual do controle de `NumericUpDown` no <xref:System.Windows.Controls.ControlTemplate>, a <xref:System.Windows.Controls.Primitives.RepeatButton> que aumenta `Value` tem seu atributo `x:Name` definido como `UpButton`.  O exemplo a seguir declara uma propriedade chamada `UpButtonElement` que representa a <xref:System.Windows.Controls.Primitives.RepeatButton> declarada no <xref:System.Windows.Controls.ControlTemplate>. O acessador de `set` primeiro cancela a assinatura do evento <xref:System.Windows.Controls.Primitives.ButtonBase.Click> do botão se `UpDownElement` não é `null`, então ele define a propriedade e, em seguida, assina o evento <xref:System.Windows.Controls.Primitives.ButtonBase.Click>. Há também uma propriedade definida, mas não mostrada aqui, para as outras <xref:System.Windows.Controls.Primitives.RepeatButton>, chamada `DownButtonElement`.

[!code-csharp[VSMCustomControl#UpButtonProperty](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#upbuttonproperty)]
[!code-vb[VSMCustomControl#UpButtonProperty](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#upbuttonproperty)]

O exemplo a seguir mostra a <xref:System.Windows.FrameworkElement.OnApplyTemplate%2A> para o controle de `NumericUpDown`.  O exemplo usa o método <xref:System.Windows.FrameworkElement.GetTemplateChild%2A> para obter os objetos de <xref:System.Windows.FrameworkElement> do <xref:System.Windows.Controls.ControlTemplate>.  Observe que o exemplo protege contra casos em que <xref:System.Windows.FrameworkElement.GetTemplateChild%2A> encontra um <xref:System.Windows.FrameworkElement> com o nome especificado que não é do tipo esperado. Também é uma melhor prática ignorar elementos que têm o `x:Name` especificado, mas que são do tipo incorreto.

[!code-csharp[VSMCustomControl#ApplyTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#applytemplate)]
[!code-vb[VSMCustomControl#ApplyTemplate](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#applytemplate)]

Seguindo as práticas que são mostradas nos exemplos anteriores, você garante que o controle continuará a ser executado quando o <xref:System.Windows.Controls.ControlTemplate> estiver faltando um <xref:System.Windows.FrameworkElement>.

### <a name="use-the-visualstatemanager-to-manage-states"></a>Usar o VisualStateManager para gerenciar estados

O <xref:System.Windows.VisualStateManager> controla os Estados de um controle e executa a lógica necessária para fazer a transição entre os Estados. Ao adicionar <xref:System.Windows.VisualState> objetos ao <xref:System.Windows.Controls.ControlTemplate>, você os adiciona a um <xref:System.Windows.VisualStateGroup> e adiciona o <xref:System.Windows.VisualStateGroup> à propriedade <xref:System.Windows.VisualStateManager.VisualStateGroups%2A?displayProperty=nameWithType> anexada para que o <xref:System.Windows.VisualStateManager> tenha acesso a eles.

O exemplo a seguir repete o exemplo anterior que mostra os objetos <xref:System.Windows.VisualState> que correspondem aos Estados `Positive` e `Negative` do controle. A <xref:System.Windows.Media.Animation.Storyboard> no `Negative`<xref:System.Windows.VisualState> transforma a <xref:System.Windows.Controls.TextBlock.Foreground%2A> do <xref:System.Windows.Controls.TextBlock> vermelho.   Quando o controle `NumericUpDown` está no estado `Negative`, o storyboard no estado `Negative` é iniciado.  Em seguida, o <xref:System.Windows.Media.Animation.Storyboard> no estado de `Negative` para quando o controle retornar ao estado de `Positive`.  O<xref:System.Windows.VisualState> de `Positive`não precisa conter uma <xref:System.Windows.Media.Animation.Storyboard> porque quando o <xref:System.Windows.Media.Animation.Storyboard> para o `Negative` é interrompido, o <xref:System.Windows.Controls.TextBlock.Foreground%2A> retorna à sua cor original.

[!code-xaml[VSMCustomControl#ValueStates](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/window1.xaml#valuestates)]

Observe que o <xref:System.Windows.Controls.TextBlock> recebe um nome, mas o <xref:System.Windows.Controls.TextBlock> não está no contrato de controle para `NumericUpDown` porque a lógica do controle nunca faz referência à <xref:System.Windows.Controls.TextBlock>.  Os elementos que são referenciados no <xref:System.Windows.Controls.ControlTemplate> têm nomes, mas não precisam fazer parte do contrato de controle porque um novo <xref:System.Windows.Controls.ControlTemplate> para o controle pode não precisar fazer referência a esse elemento.  Por exemplo, alguém que cria um novo <xref:System.Windows.Controls.ControlTemplate> para `NumericUpDown` pode decidir não indicar que `Value` é negativo alterando o <xref:System.Windows.Controls.Control.Foreground%2A>.  Nesse caso, nem o código nem o <xref:System.Windows.Controls.ControlTemplate> referencia o <xref:System.Windows.Controls.TextBlock> por nome.

A lógica do controle é responsável por alterar o estado do controle. O exemplo a seguir mostra que o controle de `NumericUpDown` chama o método <xref:System.Windows.VisualStateManager.GoToState%2A> para entrar no estado `Positive` quando `Value` é 0 ou maior e o estado `Negative` quando `Value` é menor que 0.

[!code-csharp[VSMCustomControl#ValueStateChange](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#valuestatechange)]
[!code-vb[VSMCustomControl#ValueStateChange](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#valuestatechange)]

O método <xref:System.Windows.VisualStateManager.GoToState%2A> executa a lógica necessária para iniciar e parar os storyboards adequadamente. Quando um controle chama <xref:System.Windows.VisualStateManager.GoToState%2A> para alterar seu estado, o <xref:System.Windows.VisualStateManager> faz o seguinte:

- Se a <xref:System.Windows.VisualState> que o controle terá um <xref:System.Windows.Media.Animation.Storyboard>, o storyboard começará. Em seguida, se o <xref:System.Windows.VisualState> do qual o controle está vindo tiver um <xref:System.Windows.Media.Animation.Storyboard>, o storyboard terminará.

- Se o controle já estiver no estado especificado, <xref:System.Windows.VisualStateManager.GoToState%2A> não executará nenhuma ação e retornará `true`.

- Se o estado especificado não existir no <xref:System.Windows.Controls.ControlTemplate> de `control`, <xref:System.Windows.VisualStateManager.GoToState%2A> não executará nenhuma ação e retornará `false`.

#### <a name="best-practices-for-working-with-the-visualstatemanager"></a>Melhores práticas para trabalhar com o VisualStateManager

É recomendável que você faça o seguinte para manter os estados do controle:

- Usar propriedades para controlar seu estado.

- Criar um método auxiliar para fazer a transição entre estados.

O controlar `NumericUpDown` usa sua propriedade `Value` para controlar se ele está no estado `Positive` ou `Negative`.  O controle `NumericUpDown` também define os Estados `Focused` e `UnFocused`, que controlam a propriedade <xref:System.Windows.UIElement.IsFocused%2A>. Se você usar estados que naturalmente não correspondem a uma propriedade do controle, poderá definir uma propriedade particular para controlar o estado.

Um único método que atualiza todos os Estados centraliza chamadas para o <xref:System.Windows.VisualStateManager> e mantém seu código gerenciável. O exemplo a seguir mostra o método auxiliar do controle `NumericUpDown`, `UpdateStates`. Quando `Value` é maior ou igual a 0, o <xref:System.Windows.Controls.Control> está no estado de `Positive`.  Quando `Value` é menor que 0, o controle está no estado `Negative`.  Quando <xref:System.Windows.UIElement.IsFocused%2A> é `true`, o controle está no estado de `Focused`; caso contrário, ele estará no estado de `Unfocused`.  O controle pode chamar `UpdateStates` sempre que precisar alterar seu estado, independentemente de qual estado é alterado.

[!code-csharp[VSMCustomControl#UpdateStates](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#updatestates)]
[!code-vb[VSMCustomControl#UpdateStates](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#updatestates)]

Se você passar um nome de estado para <xref:System.Windows.VisualStateManager.GoToState%2A> quando o controle já estiver nesse estado, <xref:System.Windows.VisualStateManager.GoToState%2A> não fará nada, portanto, você não precisará verificar o estado atual do controle.  Por exemplo, se o `Value` for alterado de um número negativo para outro número negativo, o storyboard para o estado `Negative` não será interrompido e o usuário não verá uma alteração no controle.

O <xref:System.Windows.VisualStateManager> usa objetos <xref:System.Windows.VisualStateGroup> para determinar qual estado deve ser encerrado quando você chama <xref:System.Windows.VisualStateManager.GoToState%2A>. O controle sempre está em um estado para cada <xref:System.Windows.VisualStateGroup> definido em seu <xref:System.Windows.Controls.ControlTemplate> e deixa apenas um estado quando ele entra em outro Estado na mesma <xref:System.Windows.VisualStateGroup>. Por exemplo, a <xref:System.Windows.Controls.ControlTemplate> do controle de `NumericUpDown` define os objetos `Positive` e `Negative`<xref:System.Windows.VisualState> em um <xref:System.Windows.VisualStateGroup> e os objetos `Focused` e `Unfocused`<xref:System.Windows.VisualState> em outro. (Você pode ver o `Focused` e `Unfocused`<xref:System.Windows.VisualState> definidos na seção de [exemplo completo](#complete_example) neste tópico quando o controle passa do estado de `Positive` para o estado `Negative`, ou vice-versa, o controle permanece no `Focused` ou `Unfocused` status.

Há três locais típicos em que o estado de um controle pode ser alterado:

- Quando a <xref:System.Windows.Controls.ControlTemplate> é aplicada à <xref:System.Windows.Controls.Control>.

- Quando uma propriedade é alterada.

- Quando ocorre um evento.

Os exemplos a seguir demonstram a atualização do estado do controle `NumericUpDown` nesses casos.

Você deve atualizar o estado do controle no método <xref:System.Windows.FrameworkElement.OnApplyTemplate%2A> para que o controle seja exibido no estado correto quando o <xref:System.Windows.Controls.ControlTemplate> for aplicado. O exemplo a seguir chama `UpdateStates` em <xref:System.Windows.FrameworkElement.OnApplyTemplate%2A> para garantir que o controle esteja nos Estados apropriados.  Por exemplo, suponha que você crie um controle de `NumericUpDown` e, em seguida, defina seu <xref:System.Windows.Controls.Control.Foreground%2A> como verde e `Value` como-5.  Se você não chamar `UpdateStates` quando a <xref:System.Windows.Controls.ControlTemplate> for aplicada ao controle de `NumericUpDown`, o controle não estará no estado de `Negative` e o valor será verde em vez de vermelho.  Você deve chamar `UpdateStates` para colocar o controle no estado `Negative`.

[!code-csharp[VSMCustomControl#ApplyTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#applytemplate)]
[!code-vb[VSMCustomControl#ApplyTemplate](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#applytemplate)]

Geralmente, é necessário atualizar os estados de um controle quando uma propriedade é alterada. O exemplo a seguir mostra todo o método `ValueChangedCallback`. Como `ValueChangedCallback` é chamado quando o `Value` é alterado, o método `UpdateStates` chamará caso `Value` seja alterado de positivo para negativo ou vice-versa. É aceitável chamar `UpdateStates` quando o `Value` é alterado, mas permanece positivo ou negativo; nesse caso, o controle não mudará de estado.

[!code-csharp[VSMCustomControl#EntireValueChangedCallback](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#entirevaluechangedcallback)]
[!code-vb[VSMCustomControl#EntireValueChangedCallback](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#entirevaluechangedcallback)]

Talvez você também precise atualizar os estados quando ocorrer um evento. O exemplo a seguir mostra que o `NumericUpDown` chama `UpdateStates` no <xref:System.Windows.Controls.Control> para manipular o evento de <xref:System.Windows.UIElement.GotFocus>.

[!code-csharp[VSMCustomControl#OnGotFocus](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#ongotfocus)]
[!code-vb[VSMCustomControl#OnGotFocus](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#ongotfocus)]

O <xref:System.Windows.VisualStateManager> ajuda a gerenciar os Estados do seu controle. Usando o <xref:System.Windows.VisualStateManager>, você garante que o controle faz a transição corretamente entre os Estados.  Se você seguir as recomendações descritas nesta seção para trabalhar com o <xref:System.Windows.VisualStateManager>, o código do controle permanecerá legível e passível de manutenção.

<a name="providing_the_control_contract"></a>

## <a name="providing-the-control-contract"></a>Fornecendo o contrato de controle

Você fornece um contrato de controle para que <xref:System.Windows.Controls.ControlTemplate> autores saibam o que colocar no modelo. Um contrato de controle contém três elementos:

- Os elementos visuais usados pela lógica do controle.

- Os estados do controle e o grupo ao qual cada estado pertence.

- As propriedades públicas que afetam o controle visualmente.

Alguém que cria um novo <xref:System.Windows.Controls.ControlTemplate> precisa saber o que <xref:System.Windows.FrameworkElement> objetos que a lógica do controle usa, o tipo de cada objeto e o nome dele. Um autor de <xref:System.Windows.Controls.ControlTemplate> também precisa saber o nome de cada Estado possível em que o controle pode estar e qual <xref:System.Windows.VisualStateGroup> estado.

Retornando ao exemplo de `NumericUpDown`, o controle espera que o <xref:System.Windows.Controls.ControlTemplate> tenha os seguintes objetos de <xref:System.Windows.FrameworkElement>:

- Um <xref:System.Windows.Controls.Primitives.RepeatButton> chamado `UpButton`.

- Um <xref:System.Windows.Controls.Primitives.RepeatButton> chamado `DownButton.`

 O controle pode estar nos seguintes estados:

- No `ValueStates`<xref:System.Windows.VisualStateGroup>

  - `Positive`

  - `Negative`

- No `FocusStates`<xref:System.Windows.VisualStateGroup>

  - `Focused`

  - `Unfocused`

Para especificar o que <xref:System.Windows.FrameworkElement> objetos esperados pelo controle, use o <xref:System.Windows.TemplatePartAttribute>, que especifica o nome e o tipo dos elementos esperados.  Para especificar os possíveis estados de um controle, use o <xref:System.Windows.TemplateVisualStateAttribute>, que especifica o nome do estado e a qual <xref:System.Windows.VisualStateGroup> ele pertence.  Coloque o <xref:System.Windows.TemplatePartAttribute> e <xref:System.Windows.TemplateVisualStateAttribute> na definição de classe do controle.

Qualquer propriedade pública que afeta a aparência do controle também é uma parte do contrato de controle.

O exemplo a seguir especifica o objeto <xref:System.Windows.FrameworkElement> e os Estados para o controle `NumericUpDown`.

[!code-csharp[VSMCustomControl#ControlContract](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#controlcontract)]
[!code-vb[VSMCustomControl#ControlContract](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#controlcontract)]

<a name="complete_example"></a>

## <a name="complete-example"></a>Exemplo completo

O exemplo a seguir é o <xref:System.Windows.Controls.ControlTemplate> inteiro para o controle de `NumericUpDown`.

[!code-xaml[VSMCustomControl#NUDTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/themes/generic.xaml#nudtemplate)]

O exemplo a seguir mostra a lógica do `NumericUpDown`.

[!code-csharp[VSMCustomControl#ControlLogic](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#controllogic)]
[!code-vb[VSMCustomControl#ControlLogic](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#controllogic)]

## <a name="see-also"></a>Consulte também

- [Personalizando a aparência de um controle existente criando um ControlTemplate](customizing-the-appearance-of-an-existing-control.md)
- [Personalização do controle](control-customization.md)
