---
title: Visão geral da entrada
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- commands [WPF]
- input [WPF], overview
- keyboard focus [WPF]
- keyboard input [WPF]
- touch events [WPF]
- event routing [WPF]
- touch input [WPF]
- manipulation [WPF]
- logical focus [WPF]
- stylus input [WPF]
- text input [WPF]
- input events [WPF], handling
- WPF [WPF], input overview
- manipulation events [WPF]
- mouse input [WPF]
- mouse capture [WPF]
- focus [WPF]
- mouse position [WPF]
ms.assetid: ee5258b7-6567-415a-9b1c-c0cbe46e79ef
ms.openlocfilehash: 9553a66538297db9c2fa134e018f35ab9e2ddf37
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59320009"
---
# <a name="input-overview"></a>Visão geral da entrada
<a name="introduction"></a> O [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] subsistema fornece um poderoso [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] para obter a entrada de uma variedade de dispositivos, incluindo o mouse, teclado, toque e caneta. Este tópico descreve os serviços fornecidos pelo [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] e explica a arquitetura dos sistemas de entrada.

<a name="input_api"></a>
## <a name="input-api"></a>API de entrada
 A entrada principal [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] exposição é encontrada nas classes de elemento base: <xref:System.Windows.UIElement>, <xref:System.Windows.ContentElement>, <xref:System.Windows.FrameworkElement>, e <xref:System.Windows.FrameworkContentElement>.  Para obter mais informações sobre os elementos base, consulte [Visão geral de elementos base](base-elements-overview.md).  Essas classes fornecem funcionalidade para eventos de entrada relacionados a pressionamentos de tecla, botões do mouse, roda do mouse, movimento do mouse, gerenciamento de foco e captura do mouse, para citar alguns. Se em vez de tratar todos os elementos de entrada como um serviço você opta por colocar a entrada [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] nos elementos base, a arquitetura de entrada permite que os eventos de entrada sejam originados de um objeto específico na interface do usuário; além disso, permite que esses eventos deem suporte a um esquema de roteamento de eventos no qual mais de um elemento tem a oportunidade de manipular um evento de entrada. Muitos eventos de entrada têm um par de eventos associados a eles.  Por exemplo, o evento de pressionamento de tecla é associada com o <xref:System.Windows.Input.Keyboard.KeyDown> e <xref:System.Windows.Input.Keyboard.PreviewKeyDown> eventos.  A diferença nesses eventos está em como eles são roteados para o elemento de destino.  Eventos de visualização são roteados por túnel pela árvore de elementos, do elemento raiz ao elemento de destino.  Eventos por propagação propagam-se para cima, do elemento de destino até o elemento raiz.  O roteamento de eventos no [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] é discutido em mais detalhes posteriormente nesta visão geral e na [Visão geral de eventos roteados](routed-events-overview.md).

### <a name="keyboard-and-mouse-classes"></a>Classes de mouse e teclado
 Além de entrada [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] nas classes de elemento base, o <xref:System.Windows.Input.Keyboard> classe e <xref:System.Windows.Input.Mouse> classes fornecem adicionais [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] para trabalhar com entradas de mouse e teclado.

 Exemplos de entrada [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] sobre o <xref:System.Windows.Input.Keyboard> classe são o <xref:System.Windows.Input.Keyboard.Modifiers%2A> propriedade, que retorna o <xref:System.Windows.Input.ModifierKeys> pressionadas no momento e o <xref:System.Windows.Input.Keyboard.IsKeyDown%2A> método, que determina se uma chave especificada está pressionada.

 O exemplo a seguir usa o <xref:System.Windows.Input.Keyboard.GetKeyStates%2A> método para determinar se um <xref:System.Windows.Input.Key> está no estado inativo.

 [!code-csharp[keyargssnippetsample#KeyEventArgsKeyBoardGetKeyStates](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyArgsSnippetSample/CSharp/Window1.xaml.cs#keyeventargskeyboardgetkeystates)]
 [!code-vb[keyargssnippetsample#KeyEventArgsKeyBoardGetKeyStates](~/samples/snippets/visualbasic/VS_Snippets_Wpf/KeyArgsSnippetSample/visualbasic/window1.xaml.vb#keyeventargskeyboardgetkeystates)]

 Exemplos de entrada [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] sobre o <xref:System.Windows.Input.Mouse> classe são <xref:System.Windows.Input.Mouse.MiddleButton%2A>, que obtém o estado do botão do meio, e <xref:System.Windows.Input.Mouse.DirectlyOver%2A>, que obtém o elemento que o ponteiro do mouse está sobre.

 O exemplo a seguir determina se o <xref:System.Windows.Input.Mouse.LeftButton%2A> do mouse está no <xref:System.Windows.Input.MouseButtonState.Pressed> estado.

 [!code-csharp[mouserelatedsnippets#MouseRelatedSnippetsGetLeftButtonMouse](~/samples/snippets/csharp/VS_Snippets_Wpf/MouseRelatedSnippets/CSharp/Window1.xaml.cs#mouserelatedsnippetsgetleftbuttonmouse)]
 [!code-vb[mouserelatedsnippets#MouseRelatedSnippetsGetLeftButtonMouse](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MouseRelatedSnippets/visualbasic/window1.xaml.vb#mouserelatedsnippetsgetleftbuttonmouse)]

 O <xref:System.Windows.Input.Mouse> e <xref:System.Windows.Input.Keyboard> classes são abordadas em mais detalhes nesta visão geral.

### <a name="stylus-input"></a>Entrada de caneta
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tem suporte integrado para o <xref:System.Windows.Input.Stylus>.  O <xref:System.Windows.Input.Stylus> é uma entrada de caneta popularizada pelo [!INCLUDE[TLA#tla_tpc](../../../../includes/tlasharptla-tpc-md.md)].  Aplicativos [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] podem tratar a caneta como um mouse, usando a [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] do mouse, mas [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] também expõe uma abstração de dispositivo de caneta que usa um modelo semelhante ao teclado e ao mouse.  Todas as [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] relacionadas à caneta contêm a palavra "Caneta".

 Já que a caneta pode atuar como um mouse, aplicativos que dão suporte apenas à entrada de mouse ainda podem obter algum nível de suporte à caneta automaticamente. Quando a caneta é usada desse modo, o aplicativo tem a oportunidade de manipular o evento de caneta apropriado e, em seguida, manipular o evento de mouse correspondente. Além disso, os serviços de alto nível, por exemplo, a entrada de tinta, também estão disponíveis por meio da abstração do dispositivo de caneta.  Para obter mais informações sobre a tinta como entrada, consulte [Introdução à tinta](getting-started-with-ink.md).

<a name="event_routing"></a>
## <a name="event-routing"></a>Roteamento de eventos
 Um <xref:System.Windows.FrameworkElement> pode conter outros elementos como elementos filho em seu modelo de conteúdo, formando uma árvore de elementos.  Em [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], o elemento pai pode participar de uma entrada direcionada a seus elementos filho ou outros descendentes por meio da manipulação de eventos. Isso é especialmente útil para a criação de controles com base em controles menores, um processo conhecido como "composição de controle" ou "composição". Para obter mais informações sobre árvores de elementos e como árvores de elementos se relacionam a rotas de evento, consulte [Árvores no WPF](trees-in-wpf.md).

 Roteamento de eventos é o processo de encaminhamento de eventos para vários elementos para que um determinado objeto ou elemento ao longo da rota possa optar por oferecer uma resposta significativa (por meio de manipulação) a um evento que possa ter sido originado de um elemento diferente.  Eventos roteados usam um de três mecanismos de roteamento: direto, por propagação e por túnel.  No roteamento direto, o elemento de origem é o único elemento notificado e o evento não será roteado para nenhum outro elemento. No entanto, o evento roteado de modo direto ainda oferece alguns recursos adicionais que só estão presentes para eventos roteados, ao contrário do que acontece para eventos [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] padrão. O roteamento por propagação ocorre de baixo para cima na árvore de elementos, notificando primeiro o elemento que originou o evento, depois o elemento pai e assim por diante.  O roteamento por túnel começa na raiz da árvore de elementos prossegue de cima para baixo, terminando com o elemento de origem original.  Para obter mais informações sobre eventos roteados, consulte [Visão geral de eventos roteados](routed-events-overview.md).

 Eventos [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] de entrada geralmente vêm em pares que consistem em um evento por túnel e um evento por propagação.  Eventos por túnel são diferenciados dos eventos por propagação com o prefixo "Preview".  Por exemplo, <xref:System.Windows.Input.Mouse.PreviewMouseMove> é a versão de túnel de um evento de movimentação do mouse e <xref:System.Windows.Input.Mouse.MouseMove> é a versão por propagação desse evento. Esse emparelhamento de eventos é uma convenção que é implementada no nível de elemento e não é uma funcionalidade inerente ao sistema de eventos [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Para obter detalhes, consulte a seção Eventos WPF de entrada em [Visão geral de eventos roteados](routed-events-overview.md).

<a name="handling_input_events"></a>
## <a name="handling-input-events"></a>Manipulação de eventos de entrada
 Para receber a entrada em um elemento, um manipulador de eventos deve estar associado a esse evento específico.  Em [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] isso é fácil: você referencia o nome do evento como um atributo do elemento que escutará esse evento.  Em seguida, você deverá definir o valor do atributo para o nome do manipulador de eventos que você definir, com base em um delegado.  O manipulador de eventos deve ser escrito em código, como o c# e pode ser incluído em um arquivo code-behind.

 Eventos de teclado ocorrem quando o sistema operacional relata ações de tecla que ocorrem enquanto o foco do teclado está em um elemento. Tanto eventos de mouse quanto de caneta podem ser divididos em duas categorias: eventos relatam alterações na posição do ponteiro com relação ao elemento e eventos que relatam alterações no estado dos botões do dispositivo.

### <a name="keyboard-input-event-example"></a>Exemplo de evento de entrada do teclado
 O exemplo a seguir escuta um pressionamento de tecla de seta para a esquerda.  Um <xref:System.Windows.Controls.StackPanel> é criado que tem um <xref:System.Windows.Controls.Button>.  Um manipulador de eventos de escuta para o pressionamento de tecla de seta para a esquerda está anexado a <xref:System.Windows.Controls.Button> instância.

 A primeira seção do exemplo cria o <xref:System.Windows.Controls.StackPanel> e o <xref:System.Windows.Controls.Button> e anexa o manipulador de eventos para o <xref:System.Windows.UIElement.KeyDown>.

 [!code-xaml[InputOvw#Input_OvwKeyboardExampleXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml#input_ovwkeyboardexamplexaml)]

 [!code-csharp[InputOvw#Input_OvwKeyboardExampleUICodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml.cs#input_ovwkeyboardexampleuicodebehind)]
 [!code-vb[InputOvw#Input_OvwKeyboardExampleUICodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InputOvw/VisualBasic/Page1.xaml.vb#input_ovwkeyboardexampleuicodebehind)]

 A segunda seção é escrita em código e define o manipulador de eventos.  Quando a tecla de seta para a esquerda é pressionada e o <xref:System.Windows.Controls.Button> tem o foco do teclado, o manipulador é executado e o <xref:System.Windows.Controls.Control.Background%2A> cor do <xref:System.Windows.Controls.Button> é alterado.  Se a tecla é pressionada, mas não é a tecla de seta para a esquerda, o <xref:System.Windows.Controls.Control.Background%2A> cor do <xref:System.Windows.Controls.Button> é alterada de volta para sua cor inicial.

 [!code-csharp[InputOvw#Input_OvwKeyboardExampleHandlerCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml.cs#input_ovwkeyboardexamplehandlercodebehind)]
 [!code-vb[InputOvw#Input_OvwKeyboardExampleHandlerCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InputOvw/VisualBasic/Page1.xaml.vb#input_ovwkeyboardexamplehandlercodebehind)]

### <a name="mouse-input-event-example"></a>Exemplo de evento de entrada do mouse
 No exemplo a seguir, o <xref:System.Windows.Controls.Control.Background%2A> cor de um <xref:System.Windows.Controls.Button> é alterado quando o ponteiro do mouse entra o <xref:System.Windows.Controls.Button>.  O <xref:System.Windows.Controls.Control.Background%2A> cor é restaurada quando o mouse deixa o <xref:System.Windows.Controls.Button>.

 A primeira seção do exemplo cria o <xref:System.Windows.Controls.StackPanel> e o <xref:System.Windows.Controls.Button> controlar e anexa os manipuladores de eventos para o <xref:System.Windows.UIElement.MouseEnter> e <xref:System.Windows.UIElement.MouseLeave> eventos para o <xref:System.Windows.Controls.Button>.

 [!code-xaml[InputOvw#Input_OvwMouseExampleXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml#input_ovwmouseexamplexaml)]

 [!code-csharp[InputOvw#Input_OvwMouseExampleUICodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml.cs#input_ovwmouseexampleuicodebehind)]
 [!code-vb[InputOvw#Input_OvwMouseExampleUICodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InputOvw/VisualBasic/Page1.xaml.vb#input_ovwmouseexampleuicodebehind)]

 A segunda seção do exemplo é escrita em código e define os manipuladores de eventos.  Quando o mouse entra o <xref:System.Windows.Controls.Button>, o <xref:System.Windows.Controls.Control.Background%2A> cor do <xref:System.Windows.Controls.Button> é alterado para <xref:System.Windows.Media.Brushes.SlateGray%2A>.  Quando o mouse deixa o <xref:System.Windows.Controls.Button>, o <xref:System.Windows.Controls.Control.Background%2A> cor do <xref:System.Windows.Controls.Button> seja alterado para <xref:System.Windows.Media.Brushes.AliceBlue%2A>.

 [!code-csharp[InputOvw#Input_OvwMouseExampleEneterHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml.cs#input_ovwmouseexampleeneterhandler)]
 [!code-vb[InputOvw#Input_OvwMouseExampleEneterHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InputOvw/VisualBasic/Page1.xaml.vb#input_ovwmouseexampleeneterhandler)]

 [!code-csharp[InputOvw#Input_OvwMouseExampleLeaveHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml.cs#input_ovwmouseexampleleavehandler)]
 [!code-vb[InputOvw#Input_OvwMouseExampleLeaveHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InputOvw/VisualBasic/Page1.xaml.vb#input_ovwmouseexampleleavehandler)]

<a name="text_input"></a>
## <a name="text-input"></a>Entrada de Texto
 O <xref:System.Windows.ContentElement.TextInput> evento permite que você escute a entrada de texto de forma independente de dispositivo. O teclado é o método primário de entrada de texto; no entanto, fala, manuscrito e outros dispositivos de entrada também podem gerar entrada de texto.

 Para a entrada de teclado [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] primeiro envia apropriado <xref:System.Windows.ContentElement.KeyDown> / <xref:System.Windows.ContentElement.KeyUp> eventos. Se esses eventos não são processados e a chave é textual em vez de (uma chave de controle como as setas direcionais) ou teclas de função, em seguida, um <xref:System.Windows.ContentElement.TextInput> é gerado.  Nem sempre há um mapeamento um para um simples entre <xref:System.Windows.ContentElement.KeyDown> / <xref:System.Windows.ContentElement.KeyUp> e <xref:System.Windows.ContentElement.TextInput> eventos porque vários pressionamentos de tecla podem gerar um único caractere de entrada de texto e pressionamentos de tecla únicos podem gerar vários caracteres cadeias de caracteres.  Isso é especialmente verdadeiro para idiomas como chinês, japonês e coreano, que usam [!INCLUDE[TLA#tla_ime#plural](../../../../includes/tlasharptla-imesharpplural-md.md)] para gerar os milhares de caracteres possíveis em seus alfabetos correspondentes.

 Quando [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] envia um <xref:System.Windows.ContentElement.KeyUp> / <xref:System.Windows.ContentElement.KeyDown> evento <xref:System.Windows.Input.KeyEventArgs.Key%2A> é definido como <xref:System.Windows.Input.Key.System?displayProperty=nameWithType> se os pressionamentos de tecla pode se tornar parte de um <xref:System.Windows.ContentElement.TextInput> evento (se ALT + S é pressionada, por exemplo). Isso permite que o código em um <xref:System.Windows.ContentElement.KeyDown> manipulador de eventos para verificar se há <xref:System.Windows.Input.Key.System?displayProperty=nameWithType> e, se encontrado, deixe o processamento para o manipulador de acionado subsequentemente <xref:System.Windows.ContentElement.TextInput> eventos. Nesses casos, as várias propriedades do <xref:System.Windows.Input.TextCompositionEventArgs> argumento pode ser usado para determinar os pressionamentos de tecla originais. Da mesma forma, se um [!INCLUDE[TLA2#tla_ime](../../../../includes/tla2sharptla-ime-md.md)] estiver ativo, <xref:System.Windows.Input.Key> tem o valor de <xref:System.Windows.Input.Key.ImeProcessed?displayProperty=nameWithType>, e <xref:System.Windows.Input.KeyEventArgs.ImeProcessedKey%2A> fornece o pressionamento de tecla ou pressionamentos de tecla original.

 O exemplo a seguir define um manipulador para o <xref:System.Windows.Controls.Primitives.ButtonBase.Click> evento e um manipulador para o <xref:System.Windows.UIElement.KeyDown> eventos.

 O primeiro segmento de código ou marcação cria a interface do usuário.

 [!code-xaml[InputOvw#Input_OvwTextInputXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml#input_ovwtextinputxaml)]

 [!code-csharp[InputOvw#Input_OvwTextInputUICodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml.cs#input_ovwtextinputuicodebehind)]
 [!code-vb[InputOvw#Input_OvwTextInputUICodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InputOvw/VisualBasic/Page1.xaml.vb#input_ovwtextinputuicodebehind)]

 O segundo segmento de código contém os manipuladores de eventos.

 [!code-csharp[InputOvw#Input_OvwTextInputHandlersCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml.cs#input_ovwtextinputhandlerscodebehind)]
 [!code-vb[InputOvw#Input_OvwTextInputHandlersCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InputOvw/VisualBasic/Page1.xaml.vb#input_ovwtextinputhandlerscodebehind)]

 Porque a propagação de eventos de entrada na rota de evento, o <xref:System.Windows.Controls.StackPanel> recebe a entrada, independentemente de qual elemento tem o foco do teclado. O <xref:System.Windows.Controls.TextBox> controle é notificado pela primeira vez e o `OnTextInputKeyDown` manipulador é chamado apenas se o <xref:System.Windows.Controls.TextBox> não manipulou a entrada. Se o <xref:System.Windows.UIElement.PreviewKeyDown> evento é usado em vez do <xref:System.Windows.UIElement.KeyDown> evento, o `OnTextInputKeyDown` manipulador é chamado pela primeira vez.

 Neste exemplo, a lógica de tratamento é gravada duas vezes – uma vez para CTRL + O e novamente para o evento de clique do botão. Isso pode ser simplificado usando comandos em vez de manipular os eventos de entrada diretamente.  Comandos são discutidos nesta visão geral e na [Visão geral dos comandos](commanding-overview.md).

<a name="touch_and_manipulation"></a>
## <a name="touch-and-manipulation"></a>Toque e manipulação
 Novo hardware e a API no sistema operacional Windows 7 fornecem a aplicativos a capacidade de receber entradas de vários toques simultaneamente. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] permite que os aplicativos detectem e respondam ao toque de maneira semelhante à que respondem a outras entradas como o mouse ou teclado, acionando eventos quando o toque ocorre.

 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] expõe dois tipos de eventos quando o toque ocorre: eventos de toque e eventos de manipulação. Eventos de toque fornecem dados brutos sobre cada dedo e seu movimento em uma tela touch. Eventos de manipulação interpretam a entrada como determinadas ações. Ambos os tipos de eventos são discutidos nesta seção.

### <a name="prerequisites"></a>Pré-requisitos
 Você precisará dos componentes a seguir para desenvolver um aplicativo que responde ao toque.

-   Visual Studio 2010.

-   Windows 7.

-   Um dispositivo, como uma tela touch, que dê suporte a Windows Touch.

### <a name="terminology"></a>Terminologia
 Os termos a seguir são usados quando o toque é discutido.

-   **Toque** é um tipo de entrada do usuário que é reconhecida pelo Windows 7. Geralmente o toque é iniciado colocando-se os dedos em uma tela sensível ao toque. Observe que dispositivos como um touchpad, comuns em computadores laptop, não dão suporte ao toque se o dispositivo simplesmente converte a posição e movimentação do dedo como entrada de mouse.

-   **Multitoque** é toque que ocorre em mais de um ponto, simultaneamente. O Windows 7 e o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dão suporte a multitoque. Sempre que o toque é discutido na documentação do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], os conceitos se aplicam para multitoque.

-   Uma **manipulação** ocorre quando o toque é interpretado como uma ação física que é aplicada a um objeto. Em [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], eventos de manipulação interpretam a entrada como uma manipulação de translação, expansão ou rotação.

-   Um `touch device` representa um dispositivo que produz a entrada de toque, por exemplo, um único dedo em uma tela touch.

### <a name="controls-that-respond-to-touch"></a>Controles que respondem ao toque
 É possível rolar pelos controles a seguir arrastando um dedo pelo controle, caso ele tenha conteúdo que está fora da exibição.

-   <xref:System.Windows.Controls.ComboBox>

-   <xref:System.Windows.Controls.ContextMenu>

-   <xref:System.Windows.Controls.DataGrid>

-   <xref:System.Windows.Controls.ListBox>

-   <xref:System.Windows.Controls.ListView>

-   <xref:System.Windows.Controls.MenuItem>

-   <xref:System.Windows.Controls.TextBox>

-   <xref:System.Windows.Controls.ToolBar>

-   <xref:System.Windows.Controls.TreeView>

 O <xref:System.Windows.Controls.ScrollViewer> define o <xref:System.Windows.Controls.ScrollViewer.PanningMode%2A?displayProperty=nameWithType> anexado a propriedade que permite que você especifique se o movimento panorâmico por toque está habilitado na horizontal, vertical, ambos ou nenhum. O <xref:System.Windows.Controls.ScrollViewer.PanningDeceleration%2A?displayProperty=nameWithType> propriedade especifica a rapidez a rolagem diminui quando o usuário levanta o dedo da tela Touch. O <xref:System.Windows.Controls.ScrollViewer.PanningRatio%2A?displayProperty=nameWithType> propriedade anexada Especifica a proporção de deslocamento para traduzir o deslocamento de manipulação de rolagem.

### <a name="touch-events"></a>Eventos de Toque
 As classes base, <xref:System.Windows.UIElement>, <xref:System.Windows.UIElement3D>, e <xref:System.Windows.ContentElement>, definem os eventos que você pode se inscrever para que seu aplicativo responda ao toque. Eventos de toque são úteis quando seu aplicativo interpreta toque como algo diferente de manipular um objeto. Por exemplo, um aplicativo que permite que um usuário desenhe com um ou mais dedos assinaria eventos de toque.

 Todas as três classes definem os eventos a seguir, que se comportam da mesma forma independentemente da classe que os define.

-   <xref:System.Windows.UIElement.TouchDown>

-   <xref:System.Windows.UIElement.TouchMove>

-   <xref:System.Windows.UIElement.TouchUp>

-   <xref:System.Windows.UIElement.TouchEnter>

-   <xref:System.Windows.UIElement.TouchLeave>

-   <xref:System.Windows.UIElement.PreviewTouchDown>

-   <xref:System.Windows.UIElement.PreviewTouchMove>

-   <xref:System.Windows.UIElement.PreviewTouchUp>

-   <xref:System.Windows.UIElement.GotTouchCapture>

-   <xref:System.Windows.UIElement.LostTouchCapture>

 Assim como os eventos de teclado e mouse, os eventos de toque são eventos roteados. Os eventos que começam com `Preview` são eventos por túnel e os eventos que começam com `Touch` são eventos por propagação. Para obter mais informações sobre os eventos roteados, consulte [Visão geral de eventos roteados](routed-events-overview.md). Quando você lidar com esses eventos, você pode obter a posição da entrada, em relação a qualquer elemento, chamando o <xref:System.Windows.Input.TouchEventArgs.GetTouchPoint%2A> ou <xref:System.Windows.Input.TouchEventArgs.GetIntermediateTouchPoints%2A> método.

 Para compreender a interação entre os eventos de toque, considere o cenário em que um usuário coloca um dedo em um elemento, move o dedo pelo elemento e, em seguida, levanta o dedo do elemento. A ilustração a seguir mostra a execução dos eventos por propagação (os eventos por túnel são omitidos por questão de simplicidade).

 ![A sequência de eventos de toque. ](./media/ndp-touchevents.png "NDP_TouchEvents") eventos de toque

 A lista a seguir descreve a sequência de eventos na ilustração anterior.

1. O <xref:System.Windows.UIElement.TouchEnter> evento ocorre quando o usuário coloca um dedo no elemento de uma vez.

2. O <xref:System.Windows.UIElement.TouchDown> evento ocorre uma vez.

3. O <xref:System.Windows.UIElement.TouchMove> evento ocorre várias vezes conforme o usuário move o dedo dentro do elemento.

4. O <xref:System.Windows.UIElement.TouchUp> evento ocorre quando o usuário levanta o dedo do elemento de uma vez.

5. O <xref:System.Windows.UIElement.TouchLeave> evento ocorre uma vez.

 Quando mais de dois dedos são usados, os eventos ocorrem para cada dedo.

### <a name="manipulation-events"></a>Eventos de Manipulação
 Para casos em que um aplicativo permite que um usuário manipular um objeto, o <xref:System.Windows.UIElement> classe define os eventos de manipulação. Diferentemente de eventos de toque que simplesmente relatam a posição do toque, os eventos de manipulação relatam como a entrada pode ser interpretada. Há três tipos de manipulação: rotação, translação e expansão. A lista a seguir descreve como invocar os três tipos de manipulação.

-   Coloque um dedo em um objeto e mova o dedo na tela touch para invocar uma manipulação de translação. Geralmente, isso move o objeto.

-   Coloque dois dedos em um objeto e mova os dedos mais próximos ou mais distantes um do outro para invocar uma manipulação de expansão. Isso geralmente redimensiona o objeto.

-   Coloque dois dedos em um objeto e gire os dedos em torno um do outro para invocar uma manipulação de rotação. Isso geralmente gira o objeto.

 É possível que mais de um tipo de manipulação ocorram simultaneamente.

 Quando você faz com que objetos respondam a manipulações, você pode fazer com que o objeto pareça ter inércia. Isso pode fazer com que seus objetos simulem o mundo físico. Por exemplo, quando você empurra um livro por uma mesa, o livro continua a mover-se depois de você liberá-lo, caso você o empurre com força suficiente. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] permite simular esse comportamento, acionando eventos de manipulação após os dedos do usuário liberarem o objeto.

 Para obter informações sobre como criar um aplicativo que permite que o usuário mover, redimensionar e girar um objeto, consulte [passo a passo: Criando seu primeiro aplicativo do Touch](walkthrough-creating-your-first-touch-application.md).

 O <xref:System.Windows.UIElement> define os seguintes eventos de manipulação.

-   <xref:System.Windows.UIElement.ManipulationStarting>

-   <xref:System.Windows.UIElement.ManipulationStarted>

-   <xref:System.Windows.UIElement.ManipulationDelta>

-   <xref:System.Windows.UIElement.ManipulationInertiaStarting>

-   <xref:System.Windows.UIElement.ManipulationCompleted>

-   <xref:System.Windows.UIElement.ManipulationBoundaryFeedback>

 Por padrão, um <xref:System.Windows.UIElement> não recebe esses eventos manipulation. Para receber eventos de manipulação em um <xref:System.Windows.UIElement>, defina <xref:System.Windows.UIElement.IsManipulationEnabled%2A?displayProperty=nameWithType> para `true`.

#### <a name="the-execution-path-of-manipulation-events"></a>O caminho de execução de eventos de manipulação
 Considere um cenário em que um usuário "lança" um objeto. O usuário coloca um dedo no objeto, move o dedo pela tela touch por uma distância curta e, em seguida, levanta o dedo enquanto ele está se movendo. O resultado disso é que o objeto se moverá sob o dedo do usuário e continuará a mover-se depois que o usuário levantar o dedo.

 A ilustração a seguir mostra o caminho de execução de eventos de manipulação e informações importantes sobre cada evento.

 ![A sequência de eventos de manipulação. ](./media/ndp-manipulationevents.png "NDP_ManipulationEvents") eventos de manipulação

 A lista a seguir descreve a sequência de eventos na ilustração anterior.

1. O <xref:System.Windows.UIElement.ManipulationStarting> evento ocorre quando o usuário coloca um dedo no objeto. Entre outras coisas, este evento permite que você defina o <xref:System.Windows.Input.ManipulationStartingEventArgs.ManipulationContainer%2A> propriedade. Nos eventos subsequentes, a posição da manipulação será relativa ao <xref:System.Windows.Input.ManipulationStartingEventArgs.ManipulationContainer%2A>. Nos eventos diferente de <xref:System.Windows.UIElement.ManipulationStarting>, essa propriedade é somente leitura, portanto, o <xref:System.Windows.UIElement.ManipulationStarting> evento é a única vez que você pode definir essa propriedade.

2. O <xref:System.Windows.UIElement.ManipulationStarted> evento ocorre em seguida. Esse evento relata a origem da manipulação.

3. O <xref:System.Windows.UIElement.ManipulationDelta> evento ocorre várias vezes como a movimentação de dedos do usuário em uma tela sensível ao toque. O <xref:System.Windows.Input.ManipulationDeltaEventArgs.DeltaManipulation%2A> propriedade do <xref:System.Windows.Input.ManipulationDeltaEventArgs> classe relata se a manipulação é interpretada como movimentação, expansão ou conversão. É aqui que você realiza a maior parte do trabalho envolvido na manipulação de um objeto.

4. O <xref:System.Windows.UIElement.ManipulationInertiaStarting> evento ocorre quando os dedos do usuário perdem contato com o objeto. Esse evento permite que você especifique a desaceleração das manipulações durante a inércia. Isso é para que seu objeto possa emular espaços físicos ou atributos diferentes, se você assim escolher. Por exemplo, suponha que seu aplicativo tem dois objetos que representam itens no mundo físico e um deles é mais pesado que o outro. Você pode fazer com que o objeto mais pesado desacelere mais rápido do que o objeto mais leve.

5. O <xref:System.Windows.UIElement.ManipulationDelta> evento ocorre várias vezes conforme a ocorrência da inércia. Observe que este evento ocorre quando os dedos do usuário se movem pela tela touch e quando [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] simula inércia. Em outras palavras, <xref:System.Windows.UIElement.ManipulationDelta> ocorre antes e depois o <xref:System.Windows.UIElement.ManipulationInertiaStarting> eventos. O <xref:System.Windows.Input.ManipulationDeltaEventArgs.IsInertial%2A?displayProperty=nameWithType> relatórios de propriedade se o <xref:System.Windows.UIElement.ManipulationDelta> evento ocorre durante a inércia, portanto, você pode verificar essa propriedade e executar ações diferentes, dependendo de seu valor.

6. O <xref:System.Windows.UIElement.ManipulationCompleted> evento ocorre quando a manipulação e qualquer eventual inércia terminam. Isto é, afinal o <xref:System.Windows.UIElement.ManipulationDelta> eventos ocorrerem, o <xref:System.Windows.UIElement.ManipulationCompleted> evento ocorre para sinalizar que a manipulação foi concluída.

 O <xref:System.Windows.UIElement> também define o <xref:System.Windows.UIElement.ManipulationBoundaryFeedback> eventos. Esse evento ocorre quando o <xref:System.Windows.Input.ManipulationDeltaEventArgs.ReportBoundaryFeedback%2A> método é chamado no <xref:System.Windows.UIElement.ManipulationDelta> eventos. O <xref:System.Windows.UIElement.ManipulationBoundaryFeedback> evento permite que aplicativos ou componentes fornecer comentários visuais quando um objeto atinge um limite. Por exemplo, o <xref:System.Windows.Window> identificadores de classe a <xref:System.Windows.UIElement.ManipulationBoundaryFeedback> eventos para fazer com que a janela mova ligeiramente quando sua borda é encontrada.

 Você pode cancelar a manipulação chamando o <xref:System.Windows.Input.ManipulationStartingEventArgs.Cancel%2A> método nos argumentos de evento em qualquer evento de manipulação, exceto <xref:System.Windows.UIElement.ManipulationBoundaryFeedback> eventos. Quando você chama <xref:System.Windows.Input.ManipulationStartingEventArgs.Cancel%2A>, os eventos de manipulação não são acionados e eventos de mouse ocorrem para toques. A tabela a seguir descreve a relação entre a hora em que a manipulação é cancelada e os eventos de mouse que ocorrem.

|O evento no qual Cancel é chamado|Os eventos de mouse que ocorrem para entrada e que já ocorreram|
|----------------------------------------|-----------------------------------------------------------------|
|<xref:System.Windows.UIElement.ManipulationStarting> e <xref:System.Windows.UIElement.ManipulationStarted>|Eventos de pressionamento do mouse.|
|<xref:System.Windows.UIElement.ManipulationDelta>|Eventos de pressionamento do mouse e eventos de movimentação do mouse.|
|<xref:System.Windows.UIElement.ManipulationInertiaStarting> e <xref:System.Windows.UIElement.ManipulationCompleted>|Pressionamento do mouse, movimentação do mouse e liberação do mouse.|

 Observe que, se você chamar <xref:System.Windows.Input.ManipulationStartingEventArgs.Cancel%2A> quando a manipulação estiver em inércia, o método retorna `false` e a entrada não acionará eventos de mouse.

### <a name="the-relationship-between-touch-and-manipulation-events"></a>A relação entre eventos de toque e eventos de manipulação
 Um <xref:System.Windows.UIElement> sempre pode receber eventos de toque. Quando o <xref:System.Windows.UIElement.IsManipulationEnabled%2A> estiver definida como `true`, um <xref:System.Windows.UIElement> pode receber eventos de toque e manipulação.  Se o <xref:System.Windows.UIElement.TouchDown> evento não é manipulado (ou seja, o <xref:System.Windows.RoutedEventArgs.Handled%2A> é de propriedade `false`), a lógica de manipulação captura o toque para o elemento e gera os eventos de manipulação. Se o <xref:System.Windows.RoutedEventArgs.Handled%2A> estiver definida como `true` no <xref:System.Windows.UIElement.TouchDown> evento, a lógica de manipulação não gera eventos de manipulação. A ilustração a seguir mostra a relação entre os eventos de toque e os eventos de manipulação.

 ![Relação entre eventos de toque e manipulação](./media/ndp-touchmanipulateevents.png "NDP_TouchManipulateEvents") eventos de toque e manipulação

 A lista a seguir descreve a relação entre os eventos de toque e de manipulação que é mostrada na ilustração anterior.

-   Quando o primeiro dispositivo de toque gera uma <xref:System.Windows.UIElement.TouchDown> evento em um <xref:System.Windows.UIElement>, as chamadas de lógica de manipulação de <xref:System.Windows.UIElement.CaptureTouch%2A> método, que gera o <xref:System.Windows.UIElement.GotTouchCapture> eventos.

-   Quando o <xref:System.Windows.UIElement.GotTouchCapture> ocorrer, as chamadas de lógica de manipulação de <xref:System.Windows.Input.Manipulation.AddManipulator%2A?displayProperty=nameWithType> método, que gera o <xref:System.Windows.UIElement.ManipulationStarting> eventos.

-   Quando o <xref:System.Windows.UIElement.TouchMove> eventos ocorrem, a lógica de manipulação gera o <xref:System.Windows.UIElement.ManipulationDelta> eventos que ocorrem antes do <xref:System.Windows.UIElement.ManipulationInertiaStarting> eventos.

-   Quando o último dispositivo de toque elemento aciona o <xref:System.Windows.UIElement.TouchUp> evento, a lógica de manipulação gera o <xref:System.Windows.UIElement.ManipulationInertiaStarting> eventos.

<a name="focus"></a>
## <a name="focus"></a>Foco
 Há dois conceitos principais relativos ao foco em [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]: foco do teclado e foco lógico.

### <a name="keyboard-focus"></a>Foco do teclado
 O foco do teclado refere-se ao elemento que está recebendo entrada do teclado.  Em toda a área de trabalho, pode haver apenas um elemento que tem o foco do teclado.  Na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], o elemento que tem o foco do teclado terá <xref:System.Windows.IInputElement.IsKeyboardFocused%2A> definido como `true`.  Estático <xref:System.Windows.Input.Keyboard> método <xref:System.Windows.Input.Keyboard.FocusedElement%2A> retorna o elemento que tem o foco do teclado no momento.

 O foco do teclado pode ser obtido pressionando TAB até chegar a um elemento ou clicando o mouse sobre determinados elementos, como um <xref:System.Windows.Controls.TextBox>.  O foco do teclado também pode ser obtido programaticamente usando o <xref:System.Windows.Input.Keyboard.Focus%2A> método no <xref:System.Windows.Input.Keyboard> classe.  <xref:System.Windows.Input.Keyboard.Focus%2A> tenta dar o foco do teclado de elemento especificado.  O elemento retornado por <xref:System.Windows.Input.Keyboard.Focus%2A> é o elemento que tem o foco do teclado no momento.

 Para que um elemento Obtenha o foco do teclado a <xref:System.Windows.UIElement.Focusable%2A> propriedade e o <xref:System.Windows.UIElement.IsVisible%2A> propriedades devem ser definidas como **verdadeiro**.  Algumas classes, como <xref:System.Windows.Controls.Panel>, têm <xref:System.Windows.UIElement.Focusable%2A> definido como `false` por padrão; portanto, talvez você precise definir essa propriedade como `true` se você quiser que esse elemento seja capaz de obter o foco.

 O exemplo a seguir usa <xref:System.Windows.Input.Keyboard.Focus%2A> para definir o foco do teclado em um <xref:System.Windows.Controls.Button>.  O local recomendado para definir o foco inicial em um aplicativo está no <xref:System.Windows.FrameworkElement.Loaded> manipulador de eventos.

 [!code-csharp[focussample#FocusSampleSetFocus](~/samples/snippets/csharp/VS_Snippets_Wpf/FocusSample/CSharp/Window1.xaml.cs#focussamplesetfocus)]
 [!code-vb[focussample#FocusSampleSetFocus](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSample/visualbasic/window1.xaml.vb#focussamplesetfocus)]

 Para obter mais informações sobre o foco do teclado, consulte [Visão geral do foco](focus-overview.md).

### <a name="logical-focus"></a>Foco lógico
 Foco lógico refere-se ao <xref:System.Windows.Input.FocusManager.FocusedElement%2A?displayProperty=nameWithType> em um escopo de foco.  Pode haver vários elementos que têm foco lógico em um aplicativo, mas pode haver apenas um elemento com foco lógico em um escopo de foco específico.

 Um escopo de foco é um elemento de contêiner que controla o <xref:System.Windows.Input.FocusManager.FocusedElement%2A> dentro de seu escopo.  Quando o foco deixar um escopo de foco, o elemento com foco perderá o foco do teclado mas manterá o foco lógico.  Quando o foco retornar para o escopo de foco, o elemento com foco obterá o foco do teclado.  Isso permite que o foco do teclado seja alterado entre vários escopos de foco, mas assegura que o elemento com foco dentro do escopo de foco permanecerá sendo o elemento com foco quando o foco retornar.

 Um elemento pode ser ativado para um escopo de foco no [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] definindo o <xref:System.Windows.Input.FocusManager> propriedade anexada <xref:System.Windows.Input.FocusManager.IsFocusScope%2A> à `true`, ou no código, definindo a propriedade anexada usando o <xref:System.Windows.Input.FocusManager.SetIsFocusScope%2A> método.

 O exemplo a seguir faz uma <xref:System.Windows.Controls.StackPanel> em um escopo de foco, definindo o <xref:System.Windows.Input.FocusManager.IsFocusScope%2A> propriedade anexada.

 [!code-xaml[MarkupSnippets#MarkupIsFocusScopeXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/MarkupSnippets/CSharp/Window1.xaml#markupisfocusscopexaml)]

 [!code-csharp[FocusSnippets#FocusSetIsFocusScope](~/samples/snippets/csharp/VS_Snippets_Wpf/FocusSnippets/CSharp/Window1.xaml.cs#focussetisfocusscope)]
 [!code-vb[FocusSnippets#FocusSetIsFocusScope](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSnippets/visualbasic/window1.xaml.vb#focussetisfocusscope)]

 As classes [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] que são escopos de foco por padrão são <xref:System.Windows.Window>, <xref:System.Windows.Controls.Menu>, <xref:System.Windows.Controls.ToolBar>, e <xref:System.Windows.Controls.ContextMenu>.

 Um elemento que tem o foco do teclado também terá foco lógico para o escopo de foco que ele pertence; Portanto, definir o foco em um elemento com o <xref:System.Windows.Input.Keyboard.Focus%2A> método no <xref:System.Windows.Input.Keyboard> classe ou classes de elemento base tenta dar o foco do teclado ao elemento e foco lógico.

 Para determinar o elemento focalizado em um escopo de foco, use <xref:System.Windows.Input.FocusManager.GetFocusedElement%2A>. Para alterar o elemento focalizado atualmente para um escopo de foco, use <xref:System.Windows.Input.FocusManager.SetFocusedElement%2A>.

 Para obter mais informações sobre o foco lógico, consulte [Visão geral do foco](focus-overview.md).

<a name="mouse_position"></a>
## <a name="mouse-position"></a>Posição do mouse
 A [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] de entrada do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fornece informações úteis em relação a espaços de coordenadas.  Por exemplo, a coordenada `(0,0)` é a coordenada superior esquerda, mas trata-se do canto superior esquerdo de qual elemento na árvore? O elemento que é o destino de entrada? O elemento ao qual você anexou o manipulador de eventos? Ou alguma outra coisa? Para evitar confusão, a [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] de entrada do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] exige que você especifique o quadro de referência ao trabalhar com coordenadas obtidas por meio do mouse. O <xref:System.Windows.Input.Mouse.GetPosition%2A> método retorna a coordenada do ponteiro do mouse em relação ao elemento especificado.

<a name="mouse_capture"></a>
## <a name="mouse-capture"></a>Captura do mouse
 Dispositivos de mouse mantêm especificamente uma característica modal conhecida como captura do mouse. A captura do mouse é usada para manter um estado de entrada de transição quando uma operação do tipo "arrastar e soltar" é iniciada, de modo que outras operações que envolvem a posição nominal do ponteiro do mouse na tela não necessariamente ocorrem. Durante a ação de arrastar, o usuário não poderá clicar sem anular a ação do tipo "arrastar e soltar", o que torna a maioria das indicações mouseover inadequadas; enquanto isso, a captura do mouse é mantida pela origem da ação de arrastar. O sistema de entrada expõe [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)], que pode determinar o estado de captura do mouse, bem como [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)], que pode forçar a captura do mouse em um elemento específico ou limpar o estado de captura do mouse. Para obter mais informações sobre operações do tipo "arrastar e soltar", consulte [Visão geral de arrastar e soltar](drag-and-drop-overview.md).

<a name="commands"></a>
## <a name="commands"></a>Comandos
 Os comandos permitem a manipulação de entrada em um nível mais semântico que a entrada do dispositivo.  Os comandos são diretivas simples, como `Cut`, `Copy`, `Paste` ou `Open`.  Os comandos são úteis para centralizar sua lógica de comando.  O mesmo comando pode ser acessado de um <xref:System.Windows.Controls.Menu>, em um <xref:System.Windows.Controls.ToolBar>, ou por meio de um atalho de teclado. Os comandos também fornecem um mecanismo para desabilitar os controles quando o comando se torna não disponível.

 <xref:System.Windows.Input.RoutedCommand> é o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] implementação de <xref:System.Windows.Input.ICommand>.  Quando um <xref:System.Windows.Input.RoutedCommand> é executado, uma <xref:System.Windows.Input.CommandManager.PreviewExecuted> e um <xref:System.Windows.Input.CommandManager.Executed> eventos são gerados no destino do comando, quais túnel e por propagação pela árvore de elementos como uma outra entrada.  Se um destino do comando não for definido, o elemento com o foco do teclado será o destino do comando.  A lógica que executa o comando é anexada a um <xref:System.Windows.Input.CommandBinding>.  Quando um <xref:System.Windows.Input.CommandManager.Executed> evento atinge uma <xref:System.Windows.Input.CommandBinding> para esse comando específico, o <xref:System.Windows.Input.ExecutedRoutedEventHandler> no <xref:System.Windows.Input.CommandBinding> é chamado.  Esse manipulador executa a ação do comando.

 Para obter mais informações sobre comandos, consulte [Visão geral dos comandos](commanding-overview.md).

 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Fornece uma biblioteca de comandos comuns que consiste <xref:System.Windows.Input.ApplicationCommands>, <xref:System.Windows.Input.MediaCommands>, <xref:System.Windows.Input.ComponentCommands>, <xref:System.Windows.Input.NavigationCommands>, e <xref:System.Windows.Documents.EditingCommands>, ou você pode definir seus próprios.

 O exemplo a seguir mostra como configurar uma <xref:System.Windows.Controls.MenuItem> , de modo que quando ele for clicado, ele invoque o <xref:System.Windows.Input.ApplicationCommands.Paste%2A> comando as <xref:System.Windows.Controls.TextBox>, supondo que o <xref:System.Windows.Controls.TextBox> tem o foco do teclado.

 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewSimpleCommand](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewsimplecommand)]

 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcommandtargetcodebehind)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcommandtargetcodebehind)]

 Para obter mais informações sobre comandos em [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], consulte [Visão geral dos comandos](commanding-overview.md).

<a name="the_input_system_and_base_elements"></a>
## <a name="the-input-system-and-base-elements"></a>O sistema de entrada e elementos base
 Eventos de entrada como os eventos anexados definidos pela <xref:System.Windows.Input.Mouse>, <xref:System.Windows.Input.Keyboard>, e <xref:System.Windows.Input.Stylus> classes são geradas pelo sistema de entrada e injetadas em uma posição específica no modelo de objeto com base na árvore visual em tempo de execução de teste de clique.

 Cada um dos eventos que <xref:System.Windows.Input.Mouse>, <xref:System.Windows.Input.Keyboard>, e <xref:System.Windows.Input.Stylus> definir como um evento anexado é também exposto novamente pelas classes de elemento base <xref:System.Windows.UIElement> e <xref:System.Windows.ContentElement> como um novo evento roteado. Os eventos roteados de elemento base são gerados por classes que manipulam o evento anexado original e reutilizam os dados do evento.

 Quando o evento de entrada passa a ser associado a um elemento de origem específico por meio da implementação de evento de entrada do seu elemento base, ele pode ser roteado pelo restante de uma rota de evento baseada em uma combinação de objetos de árvore visual e lógicos e pode também ser manipulado pelo código do aplicativo.  Em geral, é mais conveniente lidar com esses eventos de entrada relacionados ao dispositivo usando os eventos roteados em <xref:System.Windows.UIElement> e <xref:System.Windows.ContentElement>, porque você pode usar o evento manipulador uma sintaxe mais intuitiva os dois em [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] e no código. Em vez disso, você poderia optar por manipular o evento anexado que iniciou o processo, no entanto, você enfrentaria diversos problemas: o evento anexado poderia ser marcado como manipulado pela manipulação de classe do elemento base e, em vez da verdadeira sintaxe de evento, você precisaria usar os métodos acessadores para anexar manipuladores para eventos anexados.

<a name="whats_next"></a>
## <a name="whats-next"></a>Novidades
 Agora você tem várias técnicas para manipular a entrada em [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  Você também deve ter uma compreensão melhor dos vários tipos de eventos de entrada e os mecanismos de evento roteado usados pelo [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].

 Há recursos adicionais disponíveis que explicam roteamento de eventos e elementos estruturais do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] em mais detalhes. Consulte as visões gerais a seguir para obter mais informações: [Visão geral de comandos](commanding-overview.md), [Visão geral do foco](focus-overview.md), [Visão geral de elementos base](base-elements-overview.md), [Árvores no WPF](trees-in-wpf.md) e [Visão geral de eventos roteados](routed-events-overview.md).

## <a name="see-also"></a>Consulte também

- [Visão geral do foco](focus-overview.md)
- [Visão geral de comandos](commanding-overview.md)
- [Visão geral de eventos roteados](routed-events-overview.md)
- [Visão geral de elementos base](base-elements-overview.md)
- [Propriedades](properties-wpf.md)
