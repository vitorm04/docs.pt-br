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
ms.openlocfilehash: 17b6fd604b5eca54d6323701dafdd38f9f6e7328
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59131008"
---
# <a name="creating-a-control-that-has-a-customizable-appearance"></a>Criando um controle que tenha uma aparência personalizável
<a name="introduction"></a>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fornece a capacidade de criar um controle cuja aparência pode ser personalizada. Por exemplo, você pode alterar a aparência de um <xref:System.Windows.Controls.CheckBox> além do qual configuração de propriedades fará, criando um novo <xref:System.Windows.Controls.ControlTemplate>. A ilustração a seguir mostra uma <xref:System.Windows.Controls.CheckBox> que usa um padrão <xref:System.Windows.Controls.ControlTemplate> e uma <xref:System.Windows.Controls.CheckBox> que usa um <xref:System.Windows.Controls.ControlTemplate>.  
  
 ![Uma caixa de seleção com o modelo de controle padrão. ](./media/ndp-checkboxdefault.png "NDP_CheckBoxDefault")  
Uma caixa de seleção que usa o modelo de controle padrão  
  
 ![Uma caixa de seleção com um modelo de controle personalizado. ](./media/ndp-checkboxcustom.png "NDP_CheckBoxCustom")  
Uma caixa de seleção que usa um modelo de controle personalizado  
  
 Se você seguir o modelo de partes e estados ao criar um controle, a aparência do controle será personalizável. Ferramentas de designer como o Microsoft Expression Blend dão suporte ao modelo de partes e estados; portanto, ao seguir esse modelo, o controle será personalizável nesses tipos de aplicativos.  Este tópico aborda o modelo de partes e estados e como segui-lo ao criar seu próprio controle. Este tópico usa um exemplo de um controle personalizado, `NumericUpDown`, para ilustrar a filosofia desse modelo.  O controle `NumericUpDown` exibe um valor numérico, que um usuário pode aumentar ou diminuir clicando nos botões do controle.  A ilustração a seguir mostra o controle `NumericUpDown` que é abordado neste tópico.  
  
 ![Controle NumericUpDown personalizado. ](./media/ndp-numericupdown.png "NDP_NumericUPDown")  
Um controle NumericUpDown personalizado  
  
 Esse tópico contém as seguintes seções:  
  
-   [Pré-requisitos](#prerequisites)  
  
-   [Modelo de partes e estados](#parts_and_states_model)  
  
-   [Definindo a estrutura e o comportamento visuais de um controle em um ControlTemplate](#defining_the_visual_structure_and_visual_behavior_of_a_control_in_a_controltemplate)  
  
-   [Usando partes do ControlTemplate no código](#using_parts_of_the_controltemplate_in_code)  
  
-   [Fornecendo o contrato de controle](#providing_the_control_contract)  
  
-   [Exemplo completo](#complete_example)  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Pré-requisitos  
 Este tópico pressupõe que você sabe como criar um novo <xref:System.Windows.Controls.ControlTemplate> de um controle existente, estão familiarizados com o que são os elementos em um contrato de controle e entender os conceitos discutidos [Personalizando a aparência de um controle existente por Criando um ControlTemplate](customizing-the-appearance-of-an-existing-control.md).  
  
> [!NOTE]
>  Para criar um controle que pode ter sua aparência personalizada, você deve criar um controle que herda de <xref:System.Windows.Controls.Control> classe ou uma de suas subclasses diferentes de <xref:System.Windows.Controls.UserControl>.  Um controle que herda de <xref:System.Windows.Controls.UserControl> é um controle que pode ser criado rapidamente, mas não usa um <xref:System.Windows.Controls.ControlTemplate> e você não pode personalizar sua aparência.  
  
<a name="parts_and_states_model"></a>   
## <a name="parts-and-states-model"></a>Modelo de partes e estados  
 O modelo de partes e estados especifica como definir a estrutura e o comportamento visuais de um controle. Para seguir o modelo de partes e estados, faça o seguinte:  
  
-   Definir a estrutura e o comportamento visuais no <xref:System.Windows.Controls.ControlTemplate> de um controle.  
  
-   Siga algumas melhores práticas quando a lógica do controle interagir com partes do modelo de controle.  
  
-   Fornecer um contrato de controle para especificar o que deve ser incluído no <xref:System.Windows.Controls.ControlTemplate>.  
  
 Quando você define a estrutura e o comportamento visuais nos <xref:System.Windows.Controls.ControlTemplate> de um controle, os autores do aplicativo podem alterar a estrutura e o comportamento visual do seu controle criando um novo <xref:System.Windows.Controls.ControlTemplate> em vez de escrever código.   Você deve fornecer um contrato de controle que informa ao aplicativo autores que <xref:System.Windows.FrameworkElement> objetos e os estados devem ser definidos na <xref:System.Windows.Controls.ControlTemplate>. Você deve seguir algumas práticas recomendadas quando você interage com as partes na <xref:System.Windows.Controls.ControlTemplate> para que o controle manipula adequadamente incompleto <xref:System.Windows.Controls.ControlTemplate>.  Se você seguir esses três princípios, os autores do aplicativo será capazes de criar uma <xref:System.Windows.Controls.ControlTemplate> para o seu controle apenas tão facilmente quanto eles pode para os controles que acompanham o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  A próxima seção explica cada uma dessas recomendações detalhadamente.  
  
<a name="defining_the_visual_structure_and_visual_behavior_of_a_control_in_a_controltemplate"></a>   
## <a name="defining-the-visual-structure-and-visual-behavior-of-a-control-in-a-controltemplate"></a>Definindo a estrutura e o comportamento visuais de um controle em um ControlTemplate  
 Quando você cria seu controle personalizado usando o modelo de partes e estados, você define a estrutura visual do controle e o comportamento visuais no seu <xref:System.Windows.Controls.ControlTemplate> em vez de em sua lógica.  A estrutura visual de um controle é uma composição de <xref:System.Windows.FrameworkElement> objetos que compõem o controle.  O comportamento visual é a aparência do controle quando ele está em determinado estado.   Para obter mais informações sobre como criar uma <xref:System.Windows.Controls.ControlTemplate> que especifica a estrutura visual e o comportamento visual de um controle, consulte [Personalizando a aparência de um controle existente criando um ControlTemplate](customizing-the-appearance-of-an-existing-control.md).  
  
 No exemplo do `NumericUpDown` controle, a estrutura visual inclui dois <xref:System.Windows.Controls.Primitives.RepeatButton> controles e um <xref:System.Windows.Controls.TextBlock>.  Se você adicionar esses controles ao código do controle `NumericUpDown` – no construtor, por exemplo –, as posições desses controles não serão alteráveis.  Em vez de definir a estrutura visual do controle e o comportamento visuais no seu código, você deve defini-lo no <xref:System.Windows.Controls.ControlTemplate>.  Em seguida, um desenvolvedor de aplicativos para personalizar a posição dos botões e <xref:System.Windows.Controls.TextBlock> e especificar qual comportamento ocorre quando `Value` for negativo porque o <xref:System.Windows.Controls.ControlTemplate> pode ser substituído.  
  
 O exemplo a seguir mostra a estrutura visual do `NumericUpDown` controle, que inclui um <xref:System.Windows.Controls.Primitives.RepeatButton> aumentar `Value`, uma <xref:System.Windows.Controls.Primitives.RepeatButton> diminuir `Value`e uma <xref:System.Windows.Controls.TextBlock> para exibir `Value`.  
  
 [!code-xaml[VSMCustomControl#VisualStructure](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/window1.xaml#visualstructure)]  
  
 Um comportamento visual do controle `NumericUpDown` é que o valor estará em uma fonte vermelha se for negativo.  Se você alterar o <xref:System.Windows.Controls.TextBlock.Foreground%2A> do <xref:System.Windows.Controls.TextBlock> no código quando o `Value` for negativo, o `NumericUpDown` sempre mostrará um valor negativo vermelho. Você especifica o comportamento visual do controle na <xref:System.Windows.Controls.ControlTemplate> adicionando <xref:System.Windows.VisualState> objetos para o <xref:System.Windows.Controls.ControlTemplate>.  A exemplo a seguir mostra a <xref:System.Windows.VisualState> objetos para o `Positive` e `Negative` estados.  `Positive` e `Negative` são mutuamente exclusivos (o controle sempre é exatamente em um dos dois), portanto, o exemplo coloca o <xref:System.Windows.VisualState> objetos em um único <xref:System.Windows.VisualStateGroup>.  Quando o controle passa para o `Negative` estado, o <xref:System.Windows.Controls.TextBlock.Foreground%2A> da <xref:System.Windows.Controls.TextBlock> fica vermelho.  Quando o controle está no `Positive` estado, o <xref:System.Windows.Controls.TextBlock.Foreground%2A> retorna ao seu valor original.  Definindo <xref:System.Windows.VisualState> objetos em um <xref:System.Windows.Controls.ControlTemplate> discutido em mais detalhes [Personalizando a aparência de um controle existente criando um ControlTemplate](customizing-the-appearance-of-an-existing-control.md).  
  
> [!NOTE]
>  Certifique-se de definir a <xref:System.Windows.VisualStateManager.VisualStateGroups%2A?displayProperty=nameWithType> anexados a propriedade na raiz <xref:System.Windows.FrameworkElement> da <xref:System.Windows.Controls.ControlTemplate>.  
  
 [!code-xaml[VSMCustomControl#ValueStates](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/window1.xaml#valuestates)]  
  
<a name="using_parts_of_the_controltemplate_in_code"></a>   
## <a name="using-parts-of-the-controltemplate-in-code"></a>Usando partes do ControlTemplate no código  
 Um <xref:System.Windows.Controls.ControlTemplate> autor pode omitir <xref:System.Windows.FrameworkElement> ou <xref:System.Windows.VisualState> objetos, intencionalmente ou por engano, mas a lógica do controle, talvez seja necessário essas partes funcionem corretamente. O modelo de partes e estados Especifica que o controle deve ser resiliente em relação a um <xref:System.Windows.Controls.ControlTemplate> que está faltando <xref:System.Windows.FrameworkElement> ou <xref:System.Windows.VisualState> objetos.  O controle não deve lançar uma exceção nem relatar um erro se um <xref:System.Windows.FrameworkElement>, <xref:System.Windows.VisualState>, ou <xref:System.Windows.VisualStateGroup> está ausente no <xref:System.Windows.Controls.ControlTemplate>. Esta seção descreve as práticas recomendadas para interagir com <xref:System.Windows.FrameworkElement> objetos e estados de gerenciamento.  
  
### <a name="anticipate-missing-frameworkelement-objects"></a>Prever objetos FrameworkElement ausentes  
 Quando você define <xref:System.Windows.FrameworkElement> objetos no <xref:System.Windows.Controls.ControlTemplate>, a lógica do controle pode precisar interagir com alguns deles.  Por exemplo, o `NumericUpDown` controle assina dos botões <xref:System.Windows.Controls.Primitives.ButtonBase.Click> eventos para aumentar ou diminuir `Value` e define o <xref:System.Windows.Controls.TextBlock.Text%2A> propriedade do <xref:System.Windows.Controls.TextBlock> para `Value`. Se um personalizado <xref:System.Windows.Controls.ControlTemplate> omite o <xref:System.Windows.Controls.TextBlock> ou botões, é aceitável que o controle perca algumas das suas funcionalidades, mas você deve certificar-se de que seu controle não causa um erro. Por exemplo, se um <xref:System.Windows.Controls.ControlTemplate> não contém os botões para alterar `Value`, o `NumericUpDown` perde essa funcionalidade, mas um aplicativo que usa o <xref:System.Windows.Controls.ControlTemplate> continuará a ser executado.  
  
 As seguintes práticas garantirão que o controle responda corretamente a ausentes <xref:System.Windows.FrameworkElement> objetos:  
  
1.  Defina as `x:Name` atributo para cada <xref:System.Windows.FrameworkElement> que você precisa referenciar no código.  
  
2.  Defina as propriedades particulares para cada <xref:System.Windows.FrameworkElement> que você precisa interagir com.  
  
3.  Assinar e cancelar a assinatura de todos os eventos que seu controle lida com o <xref:System.Windows.FrameworkElement> propriedade do acessador set.  
  
4.  Defina as <xref:System.Windows.FrameworkElement> propriedades que você definiu na etapa 2 <xref:System.Windows.FrameworkElement.OnApplyTemplate%2A> método. Isso é mais antigo que o <xref:System.Windows.FrameworkElement> no <xref:System.Windows.Controls.ControlTemplate> está disponível para o controle. Use o `x:Name` do <xref:System.Windows.FrameworkElement> para obtê-lo a <xref:System.Windows.Controls.ControlTemplate>.  
  
5.  Verifique se o <xref:System.Windows.FrameworkElement> não é `null` antes de acessar seus membros.  Se ele for `null`, não relate um erro.  
  
 Os exemplos a seguir mostram como o `NumericUpDown` controle interage com <xref:System.Windows.FrameworkElement> objetos de acordo com as recomendações na lista anterior.  
  
 No exemplo que define a estrutura visual do `NumericUpDown` no controlar a <xref:System.Windows.Controls.ControlTemplate>, o <xref:System.Windows.Controls.Primitives.RepeatButton> que aumenta `Value` tem seu `x:Name` atributo definido como `UpButton`.  O exemplo a seguir declara uma propriedade chamada `UpButtonElement` que representa o <xref:System.Windows.Controls.Primitives.RepeatButton> declarado no <xref:System.Windows.Controls.ControlTemplate>. O `set` acessador primeiro cancela a assinatura para o botão <xref:System.Windows.Controls.Primitives.ButtonBase.Click> evento se `UpDownElement` não é `null`, em seguida, ele define a propriedade e, em seguida, ele assina o <xref:System.Windows.Controls.Primitives.ButtonBase.Click> eventos. Também é uma propriedade definida, mas não mostrados aqui, por outro <xref:System.Windows.Controls.Primitives.RepeatButton>, chamado `DownButtonElement`.  
  
 [!code-csharp[VSMCustomControl#UpButtonProperty](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#upbuttonproperty)]
 [!code-vb[VSMCustomControl#UpButtonProperty](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#upbuttonproperty)]  
  
 A exemplo a seguir mostra a <xref:System.Windows.FrameworkElement.OnApplyTemplate%2A> para o `NumericUpDown` controle.  O exemplo usa o <xref:System.Windows.FrameworkElement.GetTemplateChild%2A> método para obter o <xref:System.Windows.FrameworkElement> objetos do <xref:System.Windows.Controls.ControlTemplate>.  Observe que o exemplo protege contra casos onde <xref:System.Windows.FrameworkElement.GetTemplateChild%2A> localiza um <xref:System.Windows.FrameworkElement> com o nome especificado que não é do tipo esperado. Também é uma melhor prática ignorar elementos que têm o `x:Name` especificado, mas que são do tipo incorreto.  
  
 [!code-csharp[VSMCustomControl#ApplyTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#applytemplate)]
 [!code-vb[VSMCustomControl#ApplyTemplate](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#applytemplate)]  
  
 Ao seguir as práticas que são mostradas nos exemplos anteriores, você certifique-se de que o controle continuará a ser executada quando o <xref:System.Windows.Controls.ControlTemplate> está faltando um <xref:System.Windows.FrameworkElement>.  
  
### <a name="use-the-visualstatemanager-to-manage-states"></a>Usar o VisualStateManager para gerenciar estados  
 O <xref:System.Windows.VisualStateManager> controla os estados de um controle e executa a lógica necessária para fazer a transição entre estados. Quando você adiciona <xref:System.Windows.VisualState> objetos para o <xref:System.Windows.Controls.ControlTemplate>, você adicioná-los para um <xref:System.Windows.VisualStateGroup> e adicione o <xref:System.Windows.VisualStateGroup> para o <xref:System.Windows.VisualStateManager.VisualStateGroups%2A?displayProperty=nameWithType> propriedade anexada, de modo que o <xref:System.Windows.VisualStateManager> tem acesso a eles.  
  
 O exemplo a seguir repete o exemplo anterior que mostra a <xref:System.Windows.VisualState> objetos que corresponde do `Positive` e `Negative` estados do controle. O <xref:System.Windows.Media.Animation.Storyboard> no `Negative`<xref:System.Windows.VisualState> transforma o <xref:System.Windows.Controls.TextBlock.Foreground%2A> da <xref:System.Windows.Controls.TextBlock> vermelho.   Quando o controle `NumericUpDown` está no estado `Negative`, o storyboard no estado `Negative` é iniciado.  Em seguida, a <xref:System.Windows.Media.Animation.Storyboard> no `Negative` paradas de estado quando o controle retorna para o `Positive` estado.  O `Positive`<xref:System.Windows.VisualState> não precisa conter um <xref:System.Windows.Media.Animation.Storyboard> porque quando o <xref:System.Windows.Media.Animation.Storyboard> para o `Negative` for interrompida, o <xref:System.Windows.Controls.TextBlock.Foreground%2A> retorna à sua cor original.  
  
 [!code-xaml[VSMCustomControl#ValueStates](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/window1.xaml#valuestates)]  
  
 Observe que o <xref:System.Windows.Controls.TextBlock> recebe um nome, mas o <xref:System.Windows.Controls.TextBlock> não está no contrato de controle de `NumericUpDown` porque a lógica do controle nunca referencia o <xref:System.Windows.Controls.TextBlock>.  Elementos que são referenciados na <xref:System.Windows.Controls.ControlTemplate> têm nomes, mas não precisa fazer parte do contrato de controle porque um novo <xref:System.Windows.Controls.ControlTemplate> para o controle talvez não precise fazer referência a esse elemento.  Por exemplo, alguém que cria um novo <xref:System.Windows.Controls.ControlTemplate> para `NumericUpDown` pode optar por não indicar que `Value` é negativo, alterando o <xref:System.Windows.Controls.Control.Foreground%2A>.  Nesse caso, nenhum código nem o <xref:System.Windows.Controls.ControlTemplate> referências a <xref:System.Windows.Controls.TextBlock> por nome.  
  
 A lógica do controle é responsável por alterar o estado do controle. O exemplo a seguir mostra que o `NumericUpDown` chamadas de controle o <xref:System.Windows.VisualStateManager.GoToState%2A> método para ir para o `Positive` estado quando `Value` é 0 ou maior e o `Negative` estado quando `Value` é menor que 0.  
  
 [!code-csharp[VSMCustomControl#ValueStateChange](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#valuestatechange)]
 [!code-vb[VSMCustomControl#ValueStateChange](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#valuestatechange)]  
  
 O <xref:System.Windows.VisualStateManager.GoToState%2A> método executa a lógica necessária para iniciar e interromper os storyboards corretamente. Quando um controle chama <xref:System.Windows.VisualStateManager.GoToState%2A> para alterar seu estado, o <xref:System.Windows.VisualStateManager> faz o seguinte:  
  
-   Se o <xref:System.Windows.VisualState> que o controle vai tiver um <xref:System.Windows.Media.Animation.Storyboard>, o storyboard será iniciado. Então, se o <xref:System.Windows.VisualState> que o controle vem tiver um <xref:System.Windows.Media.Animation.Storyboard>, o storyboard será encerrado.  
  
-   Se o controle já estiver no estado especificado, <xref:System.Windows.VisualStateManager.GoToState%2A> não executará nenhuma ação e retornará `true`.  
  
-   Se o estado especificado não existe na <xref:System.Windows.Controls.ControlTemplate> dos `control`, <xref:System.Windows.VisualStateManager.GoToState%2A> não executará nenhuma ação e retornará `false`.  
  
#### <a name="best-practices-for-working-with-the-visualstatemanager"></a>Melhores práticas para trabalhar com o VisualStateManager  
 É recomendável que você faça o seguinte para manter os estados do controle:  
  
-   Usar propriedades para controlar seu estado.  
  
-   Criar um método auxiliar para fazer a transição entre estados.  
  
 O controlar `NumericUpDown` usa sua propriedade `Value` para controlar se ele está no estado `Positive` ou `Negative`.  O `NumericUpDown` controle também define o `Focused` e `UnFocused` afirma, que rastreia o <xref:System.Windows.UIElement.IsFocused%2A> propriedade. Se você usar estados que naturalmente não correspondem a uma propriedade do controle, poderá definir uma propriedade particular para controlar o estado.  
  
 Um único método que atualiza todos os estados centraliza as chamadas para o <xref:System.Windows.VisualStateManager> e mantém o código gerenciável. O exemplo a seguir mostra o método auxiliar do controle `NumericUpDown`, `UpdateStates`. Quando `Value` é maior que ou igual a 0, o <xref:System.Windows.Controls.Control> está no `Positive` estado.  Quando `Value` é menor que 0, o controle está no estado `Negative`.  Quando <xref:System.Windows.UIElement.IsFocused%2A> está `true`, o controle está no `Focused` estado; caso contrário, ele está no `Unfocused` estado.  O controle pode chamar `UpdateStates` sempre que precisar alterar seu estado, independentemente de qual estado é alterado.  
  
 [!code-csharp[VSMCustomControl#UpdateStates](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#updatestates)]
 [!code-vb[VSMCustomControl#UpdateStates](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#updatestates)]  
  
 Se você passar um nome de estado para <xref:System.Windows.VisualStateManager.GoToState%2A> quando o controle já estiver nesse estado, <xref:System.Windows.VisualStateManager.GoToState%2A> não faz nada, portanto você não precisa verificar o estado do controle atual.  Por exemplo, se o `Value` for alterado de um número negativo para outro número negativo, o storyboard para o estado `Negative` não será interrompido e o usuário não verá uma alteração no controle.  
  
 O <xref:System.Windows.VisualStateManager> usa <xref:System.Windows.VisualStateGroup> objetos para determinar qual estado para sair quando você chama <xref:System.Windows.VisualStateManager.GoToState%2A>. O controle está sempre em um estado para cada <xref:System.Windows.VisualStateGroup> que é definido no seu <xref:System.Windows.Controls.ControlTemplate> e somente deixa um estado quando entra em outro estado da mesma <xref:System.Windows.VisualStateGroup>. Por exemplo, o <xref:System.Windows.Controls.ControlTemplate> do `NumericUpDown` controle define os `Positive` e `Negative`<xref:System.Windows.VisualState> objetos em um <xref:System.Windows.VisualStateGroup> e o `Focused` e `Unfocused`<xref:System.Windows.VisualState> objetos em outro. (Você pode ver o `Focused` e `Unfocused`<xref:System.Windows.VisualState> definidos na [exemplo completo](#complete_example) neste tópico quando o controle passa do `Positive` estado para o `Negative` estado, ou vice-versa, o controle permanece no tanto a `Focused` ou `Unfocused` estado.  
  
 Há três locais típicos em que o estado de um controle pode ser alterado:  
  
-   Quando o <xref:System.Windows.Controls.ControlTemplate> é aplicada para o <xref:System.Windows.Controls.Control>.  
  
-   Quando uma propriedade é alterada.  
  
-   Quando ocorre um evento.  
  
 Os exemplos a seguir demonstram a atualização do estado do controle `NumericUpDown` nesses casos.  
  
 Você deve atualizar o estado do controle na <xref:System.Windows.FrameworkElement.OnApplyTemplate%2A> método para que o controle seja exibido no item correto estado quando o <xref:System.Windows.Controls.ControlTemplate> é aplicado. A exemplo a seguir chama `UpdateStates` em <xref:System.Windows.FrameworkElement.OnApplyTemplate%2A> para garantir que o controle está nos estados apropriados.  Por exemplo, suponha que você crie uma `NumericUpDown` e, em seguida, defina sua <xref:System.Windows.Controls.Control.Foreground%2A> verde e `Value` como -5.  Se você não chamar `UpdateStates` quando o <xref:System.Windows.Controls.ControlTemplate> é aplicado para o `NumericUpDown` controle, o controle não está na `Negative` estado e o valor é verde, em vez de vermelho.  Você deve chamar `UpdateStates` para colocar o controle no estado `Negative`.  
  
 [!code-csharp[VSMCustomControl#ApplyTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#applytemplate)]
 [!code-vb[VSMCustomControl#ApplyTemplate](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#applytemplate)]  
  
 Geralmente, é necessário atualizar os estados de um controle quando uma propriedade é alterada. O exemplo a seguir mostra todo o método `ValueChangedCallback`. Como `ValueChangedCallback` é chamado quando o `Value` é alterado, o método `UpdateStates` chamará caso `Value` seja alterado de positivo para negativo ou vice-versa. É aceitável chamar `UpdateStates` quando o `Value` é alterado, mas permanece positivo ou negativo; nesse caso, o controle não mudará de estado.  
  
 [!code-csharp[VSMCustomControl#EntireValueChangedCallback](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#entirevaluechangedcallback)]
 [!code-vb[VSMCustomControl#EntireValueChangedCallback](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#entirevaluechangedcallback)]  
  
 Talvez você também precise atualizar os estados quando ocorrer um evento. O exemplo a seguir mostra que o `NumericUpDown` chamadas `UpdateStates` sobre o <xref:System.Windows.Controls.Control> para lidar com o <xref:System.Windows.UIElement.GotFocus> eventos.  
  
 [!code-csharp[VSMCustomControl#OnGotFocus](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#ongotfocus)]
 [!code-vb[VSMCustomControl#OnGotFocus](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#ongotfocus)]  
  
 O <xref:System.Windows.VisualStateManager> ajuda você a gerenciar os estados do controle. Usando o <xref:System.Windows.VisualStateManager>, verifique se que seu controle corretamente faz a transição entre estados.  Se você seguir as recomendações descritas nesta seção para trabalhar com o <xref:System.Windows.VisualStateManager>, código do seu controle permanecerá legível e sustentável.  
  
<a name="providing_the_control_contract"></a>   
## <a name="providing-the-control-contract"></a>Fornecendo o contrato de controle  
 Você fornece um contrato de controle, de modo que <xref:System.Windows.Controls.ControlTemplate> autores saberá o que colocar o modelo. Um contrato de controle contém três elementos:  
  
-   Os elementos visuais usados pela lógica do controle.  
  
-   Os estados do controle e o grupo ao qual cada estado pertence.  
  
-   As propriedades públicas que afetam o controle visualmente.  
  
 Alguém que cria um novo <xref:System.Windows.Controls.ControlTemplate> precisa saber o que <xref:System.Windows.FrameworkElement> objetos usa a lógica do controle, que tipo de cada objeto é e o nome deles. Um <xref:System.Windows.Controls.ControlTemplate> autor também precisa saber o nome de cada estado possível que o controle pode ser incluído e que <xref:System.Windows.VisualStateGroup> o estado é.  
  
 Retornando para o `NumericUpDown` espera de controle de exemplo, o <xref:System.Windows.Controls.ControlTemplate> ter o seguinte <xref:System.Windows.FrameworkElement> objetos:  
  
-   Um <xref:System.Windows.Controls.Primitives.RepeatButton> chamado `UpButton`.  
  
-   Um <xref:System.Windows.Controls.Primitives.RepeatButton> chamado `DownButton.`  
  
 O controle pode estar nos seguintes estados:  
  
-   No `ValueStates`<xref:System.Windows.VisualStateGroup>  
  
    -   `Positive`  
  
    -   `Negative`  
  
-   No `FocusStates`<xref:System.Windows.VisualStateGroup>  
  
    -   `Focused`  
  
    -   `Unfocused`  
  
 Para especificar quais <xref:System.Windows.FrameworkElement> objetos que o controle espera que, se você usar o <xref:System.Windows.TemplatePartAttribute>, que especifica o nome e tipo dos elementos esperados.  Para especificar os possíveis estados de um controle, você deve usar o <xref:System.Windows.TemplateVisualStateAttribute>, que especifica o nome do estado e que <xref:System.Windows.VisualStateGroup> pertence.  Colocar o <xref:System.Windows.TemplatePartAttribute> e <xref:System.Windows.TemplateVisualStateAttribute> na definição de classe do controle.  
  
 Qualquer propriedade pública que afeta a aparência do controle também é uma parte do contrato de controle.  
  
 O exemplo a seguir especifica o <xref:System.Windows.FrameworkElement> objeto e estados para o `NumericUpDown` controle.  
  
 [!code-csharp[VSMCustomControl#ControlContract](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#controlcontract)]
 [!code-vb[VSMCustomControl#ControlContract](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#controlcontract)]  
  
<a name="complete_example"></a>   
## <a name="complete-example"></a>Exemplo completo  
 O exemplo a seguir é todo o <xref:System.Windows.Controls.ControlTemplate> para o `NumericUpDown` controle.  
  
 [!code-xaml[VSMCustomControl#NUDTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/themes/generic.xaml#nudtemplate)]  
  
 O exemplo a seguir mostra a lógica do `NumericUpDown`.  
  
 [!code-csharp[VSMCustomControl#ControlLogic](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#controllogic)]
 [!code-vb[VSMCustomControl#ControlLogic](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#controllogic)]  
  
## <a name="see-also"></a>Consulte também

- [Personalizando a aparência de um controle existente criando um ControlTemplate](customizing-the-appearance-of-an-existing-control.md)
- [Personalização do controle](control-customization.md)
