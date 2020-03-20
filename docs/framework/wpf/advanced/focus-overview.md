---
title: Visão geral do foco
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- applications [WPF], focus
- focus in applications [WPF]
ms.assetid: 0230c4eb-0c8a-462b-ac4b-ae3e511659f4
ms.openlocfilehash: de788ec3f0628ff2f7c422c76c73ff7985424113
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186664"
---
# <a name="focus-overview"></a>Visão geral do foco
Em [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], há dois conceitos principais relativos ao foco: foco do teclado e foco lógico.  O foco do teclado refere-se ao elemento que recebe entrada do teclado e foco lógico refere-se ao elemento em um escopo de foco que tem foco.  Esses conceitos são discutidos em detalhes nesta visão geral.  Noções básicas sobre a diferença entre esses conceitos é importante para a criação de aplicativos complexos que têm várias regiões no qual o foco pode ser obtido.  
  
 As principais classes que participam <xref:System.Windows.Input.Keyboard> da <xref:System.Windows.Input.FocusManager> gestão focal são a classe, <xref:System.Windows.UIElement> <xref:System.Windows.ContentElement>a classe e as classes de elemento base, como e .  Para obter mais informações sobre os elementos base, consulte [Visão geral de elementos base](base-elements-overview.md).  
  
 A <xref:System.Windows.Input.Keyboard> classe está preocupada principalmente com <xref:System.Windows.Input.FocusManager> o foco do teclado e o está preocupado principalmente com o foco lógico, mas isso não é uma distinção absoluta.  Um elemento que tem o foco do teclado também terá foco lógico, mas não necessariamente um elemento que tenha foco lógico tem o foco do teclado.  Isso é evidente quando <xref:System.Windows.Input.Keyboard> você usa a classe para definir o elemento que tem foco no teclado, pois ele também define o foco lógico no elemento.  

<a name="Keyboard_Focus"></a>
## <a name="keyboard-focus"></a>Foco do teclado  
 O foco do teclado refere-se ao elemento que está recebendo atualmente entrada do teclado.  Em toda a área de trabalho, pode haver apenas um elemento que tem o foco do teclado.  Em [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], o elemento que <xref:System.Windows.IInputElement.IsKeyboardFocused%2A> tem `true`foco no teclado terá definido para .  A propriedade <xref:System.Windows.Input.Keyboard.FocusedElement%2A> estática na <xref:System.Windows.Input.Keyboard> classe obtém o elemento que atualmente tem foco no teclado.  
  
 Para que um elemento obtenha foco <xref:System.Windows.UIElement.Focusable%2A> no <xref:System.Windows.UIElement.IsVisible%2A> teclado, as propriedades dos `true`elementos base devem ser definidas como .  Algumas classes, como <xref:System.Windows.Controls.Panel> a classe <xref:System.Windows.UIElement.Focusable%2A> base, definiram `false` por padrão; portanto, você deve <xref:System.Windows.UIElement.Focusable%2A> `true` definir para se você quiser tal elemento para ser capaz de obter foco no teclado.  
  
 O foco do teclado pode ser obtido por meio de interação do usuário com o [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], como tabulações para um elemento ou clique do mouse sobre determinados elementos.  O foco do teclado também pode ser <xref:System.Windows.Input.Keyboard.Focus%2A> obtido <xref:System.Windows.Input.Keyboard> programáticamente usando o método na classe.  O <xref:System.Windows.Input.Keyboard.Focus%2A> método tenta dar ao elemento especificado foco no teclado.  O elemento retornado é o elemento que tem o foco do teclado, que pode ser um elemento diferente do solicitado se o velho ou o novo objeto de foco bloquear a solicitação.  
  
 O exemplo a <xref:System.Windows.Input.Keyboard.Focus%2A> seguir usa o <xref:System.Windows.Controls.Button>método para definir o foco do teclado em um .  
  
 [!code-csharp[focussample#FocusSampleSetFocus](~/samples/snippets/csharp/VS_Snippets_Wpf/FocusSample/CSharp/Window1.xaml.cs#focussamplesetfocus)]
 [!code-vb[focussample#FocusSampleSetFocus](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSample/visualbasic/window1.xaml.vb#focussamplesetfocus)]  
  
 A <xref:System.Windows.UIElement.IsKeyboardFocused%2A> propriedade nas classes de elemento base obtém um valor indicando se o elemento tem foco no teclado.  A <xref:System.Windows.UIElement.IsKeyboardFocusWithin%2A> propriedade nas classes de elemento base obtém um valor indicando se o elemento ou qualquer um de seus elementos visuais de criança tem foco no teclado.  
  
 Ao definir o foco inicial na inicialização do aplicativo, o elemento para receber o foco deve <xref:System.Windows.UIElement.Focusable%2A> estar <xref:System.Windows.UIElement.IsVisible%2A> na `true`árvore visual da janela inicial carregada pelo aplicativo, e o elemento deve ter e definir para .  O local recomendado para definir o <xref:System.Windows.FrameworkElement.Loaded> foco inicial é no manipulador de eventos.  Um <xref:System.Windows.Threading.Dispatcher> retorno de chamada também <xref:System.Windows.Threading.Dispatcher.Invoke%2A> <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A>pode ser usado ligando ou .  
  
<a name="Logical_Focus"></a>
## <a name="logical-focus"></a>Foco lógico  
 Foco lógico refere-se ao <xref:System.Windows.Input.FocusManager.FocusedElement%2A?displayProperty=nameWithType> escopo em foco.  Um escopo de foco é um <xref:System.Windows.Input.FocusManager.FocusedElement%2A> elemento que mantém o controle do dentro de seu escopo.  Quando o foco de teclado deixar um escopo de foco, o elemento com foco perderá o foco do teclado mas manterá o foco lógico.  Quando o foco de teclado retornar para o escopo de foco, o elemento com foco obterá o foco do teclado.  Isso permite que o foco do teclado seja alterado entre vários escopos de foco, mas assegura que o elemento focalizado no escopo de foco recupere o foco do teclado quando o foco retornar para o escopo de foco.  
  
 Pode haver vários elementos que têm foco lógico em um aplicativo, mas pode haver apenas um elemento com foco lógico em um escopo de foco específico.  
  
 Um elemento que tem o foco do teclado tem foco lógico para o escopo de foco a que pertence.  
  
 Um elemento pode ser transformado [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] em um <xref:System.Windows.Input.FocusManager> escopo <xref:System.Windows.Input.FocusManager.IsFocusScope%2A> de `true`foco definindo a propriedade anexada para .  Em código, um elemento pode ser transformado <xref:System.Windows.Input.FocusManager.SetIsFocusScope%2A>em um escopo de foco chamando .  
  
 O exemplo a <xref:System.Windows.Controls.StackPanel> seguir torna um <xref:System.Windows.Input.FocusManager.IsFocusScope%2A> escopo de foco definindo a propriedade anexada.  
  
 [!code-xaml[MarkupSnippets#MarkupIsFocusScopeXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/MarkupSnippets/CSharp/Window1.xaml#markupisfocusscopexaml)]  
  
 [!code-csharp[FocusSnippets#FocusSetIsFocusScope](~/samples/snippets/csharp/VS_Snippets_Wpf/FocusSnippets/CSharp/Window1.xaml.cs#focussetisfocusscope)]
 [!code-vb[FocusSnippets#FocusSetIsFocusScope](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSnippets/visualbasic/window1.xaml.vb#focussetisfocusscope)]  
  
 <xref:System.Windows.Input.FocusManager.GetFocusScope%2A>retorna o escopo de foco para o elemento especificado.  
  
 As [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] classes em que são <xref:System.Windows.Window>escopos <xref:System.Windows.Controls.ToolBar>de <xref:System.Windows.Controls.ContextMenu>foco por padrão são, <xref:System.Windows.Controls.MenuItem>e .  
  
 <xref:System.Windows.Input.FocusManager.GetFocusedElement%2A>obtém o elemento focalizado para o escopo de foco especificado.  <xref:System.Windows.Input.FocusManager.SetFocusedElement%2A>define o elemento focalizado no escopo de foco especificado.  <xref:System.Windows.Input.FocusManager.SetFocusedElement%2A>é tipicamente usado para definir o elemento focalizado inicial.  
  
 O exemplo a seguir define o elemento focalizado em um escopo de foco e obtém o elemento focalizado de um escopo de foco.  
  
 [!code-csharp[FocusSnippets#FocusGetSetFocusedElement](~/samples/snippets/csharp/VS_Snippets_Wpf/FocusSnippets/CSharp/Window1.xaml.cs#focusgetsetfocusedelement)]
 [!code-vb[FocusSnippets#FocusGetSetFocusedElement](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSnippets/visualbasic/window1.xaml.vb#focusgetsetfocusedelement)]  
  
<a name="Keyboard_Navigation"></a>
## <a name="keyboard-navigation"></a>Navegação por teclado  
 A <xref:System.Windows.Input.KeyboardNavigation> classe é responsável por implementar a navegação padrão de foco do teclado quando uma das teclas de navegação é pressionada.  As teclas de navegação são: TAB, SHIFT + TAB, CTRL + TAB, CTRL + SHIFT + TAB, setas para cima, para baixo, esquerda e direita.  
  
 O comportamento de navegação de um contêiner de <xref:System.Windows.Input.KeyboardNavigation> <xref:System.Windows.Input.KeyboardNavigation.TabNavigation%2A>navegação <xref:System.Windows.Input.KeyboardNavigation.ControlTabNavigation%2A>pode <xref:System.Windows.Input.KeyboardNavigation.DirectionalNavigation%2A>ser alterado definindo as propriedades anexadas e .  Essas propriedades são <xref:System.Windows.Input.KeyboardNavigationMode> de tipo <xref:System.Windows.Input.KeyboardNavigationMode.Continue>e <xref:System.Windows.Input.KeyboardNavigationMode.Local> <xref:System.Windows.Input.KeyboardNavigationMode.Contained>os <xref:System.Windows.Input.KeyboardNavigationMode.Cycle> <xref:System.Windows.Input.KeyboardNavigationMode.Once>valores <xref:System.Windows.Input.KeyboardNavigationMode.None>possíveis são, e .  O valor <xref:System.Windows.Input.KeyboardNavigationMode.Continue>padrão é , o que significa que o elemento não é um contêiner de navegação.  
  
 O exemplo a <xref:System.Windows.Controls.Menu> seguir cria <xref:System.Windows.Controls.MenuItem> um com um número de objetos.  A <xref:System.Windows.Input.KeyboardNavigation.TabNavigation%2A> propriedade anexada <xref:System.Windows.Input.KeyboardNavigationMode.Cycle> está <xref:System.Windows.Controls.Menu>definida para .  Quando o foco é alterado <xref:System.Windows.Controls.Menu>usando a tecla de guia dentro do , o foco se moverá de cada elemento e quando o último elemento for atingido o foco voltará ao primeiro elemento.  
  
 [!code-xaml[MarkupSnippets#MarkupKeyboardNavigationTabNavigationXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/MarkupSnippets/CSharp/Window1.xaml#markupkeyboardnavigationtabnavigationxaml)]  
  
 [!code-csharp[MarkupSnippets#MarkupKeyboardNavigationTabNavigationCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/MarkupSnippets/CSharp/Window1.xaml.cs#markupkeyboardnavigationtabnavigationcode)]
 [!code-vb[MarkupSnippets#MarkupKeyboardNavigationTabNavigationCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MarkupSnippets/visualbasic/window1.xaml.vb#markupkeyboardnavigationtabnavigationcode)]  
  
<a name="Manipulating_Focus_Programmatically"></a>
## <a name="navigating-focus-programmatically"></a>Foco de navegação por meio de programação  
 API adicional para trabalhar <xref:System.Windows.UIElement.MoveFocus%2A> <xref:System.Windows.UIElement.PredictFocus%2A>com foco são e .  
  
 <xref:System.Windows.FrameworkElement.MoveFocus%2A>muda o foco para o próximo elemento na aplicação.  A <xref:System.Windows.Input.TraversalRequest> é usado para especificar a direção.   O <xref:System.Windows.Input.FocusNavigationDirection> passe <xref:System.Windows.UIElement.MoveFocus%2A> para especificar as diferentes direções <xref:System.Windows.Input.FocusNavigationDirection.First> <xref:System.Windows.Input.FocusNavigationDirection.Last>de <xref:System.Windows.Input.FocusNavigationDirection.Up> <xref:System.Windows.Input.FocusNavigationDirection.Down>foco pode ser movido, tais como , e .  
  
 O exemplo <xref:System.Windows.FrameworkElement.MoveFocus%2A> a seguir é usa para alterar o elemento focalizado.  
  
 [!code-csharp[focussample#FocusSampleMoveFocus](~/samples/snippets/csharp/VS_Snippets_Wpf/FocusSample/CSharp/Window1.xaml.cs#focussamplemovefocus)]
 [!code-vb[focussample#FocusSampleMoveFocus](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSample/visualbasic/window1.xaml.vb#focussamplemovefocus)]  
  
 <xref:System.Windows.FrameworkElement.PredictFocus%2A>retorna o objeto que receberia foco se o foco fosse alterado.  Atualmente, <xref:System.Windows.Input.FocusNavigationDirection.Up>apenas <xref:System.Windows.Input.FocusNavigationDirection.Down> <xref:System.Windows.Input.FocusNavigationDirection.Left>, <xref:System.Windows.Input.FocusNavigationDirection.Right> e são <xref:System.Windows.FrameworkElement.PredictFocus%2A>apoiados por .  
  
<a name="Focus_Events"></a>
## <a name="focus-events"></a>Eventos de foco  
 Os eventos relacionados ao <xref:System.Windows.Input.Keyboard.PreviewGotKeyboardFocus> <xref:System.Windows.Input.Keyboard.GotKeyboardFocus> foco <xref:System.Windows.Input.Keyboard.PreviewLostKeyboardFocus> <xref:System.Windows.Input.Keyboard.LostKeyboardFocus>do teclado são, e , .  Os eventos são definidos como <xref:System.Windows.Input.Keyboard> eventos anexados na classe, mas são mais facilmente acessíveis como eventos roteados equivalentes nas classes de elementobase.  Para obter mais informações sobre os eventos, consulte a [Visão geral de eventos roteados](routed-events-overview.md).  
  
 <xref:System.Windows.Input.Keyboard.GotKeyboardFocus>é levantado quando o elemento obtém foco no teclado.  <xref:System.Windows.Input.Keyboard.LostKeyboardFocus>é levantado quando o elemento perde o foco do teclado.  Se <xref:System.Windows.Input.Keyboard.PreviewGotKeyboardFocus> o evento <xref:System.Windows.Input.Keyboard.PreviewLostKeyboardFocusEvent> ou o <xref:System.Windows.RoutedEventArgs.Handled%2A> evento for `true`tratado e for definido como , então o foco não mudará.  
  
 O exemplo a <xref:System.Windows.UIElement.GotKeyboardFocus> <xref:System.Windows.UIElement.LostKeyboardFocus> seguir anexa e <xref:System.Windows.Controls.TextBox>os manipuladores de eventos a a .  
  
 [!code-xaml[keyboardsample#KeyboardSampleXAMLHandlerHookup](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyboardSample/CSharp/Window1.xaml#keyboardsamplexamlhandlerhookup)]  
  
 Quando <xref:System.Windows.Controls.TextBox> o foco do <xref:System.Windows.Controls.Control.Background%2A> teclado obtém, a propriedade do <xref:System.Windows.Controls.TextBox> é alterada para <xref:System.Windows.Media.Brushes.LightBlue%2A>.  
  
 [!code-csharp[keyboardsample#KeyboardSampleGotFocus](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyboardSample/CSharp/Window1.xaml.cs#keyboardsamplegotfocus)]
 [!code-vb[keyboardsample#KeyboardSampleGotFocus](~/samples/snippets/visualbasic/VS_Snippets_Wpf/KeyboardSample/visualbasic/window1.xaml.vb#keyboardsamplegotfocus)]  
  
 Quando <xref:System.Windows.Controls.TextBox> o foco do <xref:System.Windows.Controls.Control.Background%2A> teclado <xref:System.Windows.Controls.TextBox> perde, a propriedade do é alterada de volta para branco.  
  
 [!code-csharp[keyboardsample#KeyboardSampleLostFocus](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyboardSample/CSharp/Window1.xaml.cs#keyboardsamplelostfocus)]
 [!code-vb[keyboardsample#KeyboardSampleLostFocus](~/samples/snippets/visualbasic/VS_Snippets_Wpf/KeyboardSample/visualbasic/window1.xaml.vb#keyboardsamplelostfocus)]  
  
 Os eventos relacionados ao <xref:System.Windows.UIElement.GotFocus> <xref:System.Windows.UIElement.LostFocus>foco lógico são e .  Esses eventos são <xref:System.Windows.Input.FocusManager> definidos como eventos <xref:System.Windows.Input.FocusManager> anexados, mas não expõem os invólucros de eventos CLR.  <xref:System.Windows.UIElement>e <xref:System.Windows.ContentElement> expor esses eventos de forma mais conveniente.  
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.Input.FocusManager>
- <xref:System.Windows.UIElement>
- <xref:System.Windows.ContentElement>
- [Visão geral da entrada](input-overview.md)
- [Visão geral de elementos base](base-elements-overview.md)
