---
title: Interoperação Win32 e WPF
ms.date: 03/30/2017
helpviewer_keywords:
- hosting WPF content in Win32 window [WPF]
- HWND interop [WPF]
- Win32 code [WPF], WPF interoperation
- interoperability [WPF], Win32
ms.assetid: 0ffbde0d-701d-45a3-a6fa-dd71f4d9772e
ms.openlocfilehash: d7e63c30040a90e29a9fb4acd0ecc897ca328c1f
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740198"
---
# <a name="wpf-and-win32-interoperation"></a>Interoperação Win32 e WPF

Este tópico fornece uma visão geral de como interoperar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] e código Win32. O [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fornece um ambiente avançado para a criação de aplicativos. No entanto, quando você tem um investimento substancial no código Win32, pode ser mais eficiente reutilizar parte desse código.

<a name="basics"></a>

## <a name="wpf-and-win32-interoperation-basics"></a>Noções básicas de interoperação entre o Win32 e o WPF

Há duas técnicas básicas para interoperação entre [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] e o código Win32.

- Hospede [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] conteúdo em uma janela do Win32. Com essa técnica, você pode usar os recursos gráficos avançados do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dentro da estrutura de uma janela e aplicativo padrão do Win32.

- Hospede uma janela do Win32 no conteúdo [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Com essa técnica, você pode usar um controle Win32 personalizado existente no contexto de outros [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] conteúdo e passar dados entre os limites.

Essas duas técnicas são apresentadas conceitualmente neste tópico. Para obter uma ilustração mais orientada a código de Hospedagem de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] no Win32, consulte [passo a passos: hospedando conteúdo do WPF no Win32](walkthrough-hosting-wpf-content-in-win32.md). Para obter uma ilustração mais orientada a código de hospedagem do Win32 no [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], consulte [passo a passos: hospedando um controle Win32 no WPF](walkthrough-hosting-a-win32-control-in-wpf.md).

<a name="projects"></a>

## <a name="wpf-interoperation-projects"></a>Projetos de interoperação do WPF

as APIs de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] são código gerenciado, mas a maioria dos programas Win32 existentes são escritas C++sem gerenciamento.  Você não pode chamar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] APIs de um programa verdadeiro não gerenciado. No entanto, usando a opção `/clr` com o compilador C++ Visual da Microsoft, você pode criar um programa misto gerenciado e não gerenciado, no qual você pode misturar diretamente chamadas de API gerenciadas e não gerenciadas.

Uma complicação no nível do projeto é que você não pode compilar [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] C++ arquivos em um projeto.  Há várias técnicas de divisão de projeto para compensar isso.

- Crie uma C# dll que contenha todas as suas páginas de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] como um assembly compilado e, C++ em seguida, faça com que o executável inclua essa dll como referência.

- Crie um C# executável para o conteúdo de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] e faça referência a uma C++ dll que contém o conteúdo do Win32.

- Use <xref:System.Windows.Markup.XamlReader.Load%2A> para carregar qualquer [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] em tempo de execução, em vez de compilar seu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].

- Não use [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] e grave todas as suas [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] no código, compilando a árvore de elementos do <xref:System.Windows.Application>.

Use a abordagem que funcionar melhor para você.

> [!NOTE]
> Se você não tiver usado C++o/CLI antes, poderá observar algumas palavras-chave "novas", como `gcnew` e `nullptr` nos exemplos de código de interoperação. Essas palavras-chave substituem a sintaxe mais antiga de sublinhado duplo (`__gc`) e fornecem uma sintaxe mais natural para código C++gerenciado no.  Para saber mais sobre os C++recursos gerenciados da/CLI, consulte [extensões de componente para plataformas de tempo de execução](/cpp/windows/component-extensions-for-runtime-platforms).

<a name="hwnds"></a>

## <a name="how-wpf-uses-hwnds"></a>Como o WPF usa Hwnds

Para aproveitar ao máximo a "Interoperabilidade de HWND" do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], você precisa entender como o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] usa HWNDs. Para qualquer HWND, você não pode misturar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] renderização com renderização do DirectX ou renderização GDI/GDI+. Isso tem várias implicações. Basicamente, para combinar esses modelos de renderização, você deve criar uma solução de interoperabilidade e usar segmentos de interoperação designados para cada modelo de renderização que optar usar. Além disso, o comportamento de renderização cria uma restrição de "espaço aéreo" para o que sua solução de interoperação pode realizar. O conceito de "espaço aéreo" é explicado com mais detalhes no tópico [Visão geral das regiões de tecnologia](technology-regions-overview.md).

Todos os elementos do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] na tela, por fim, contam com um HWND. Quando você cria um [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Window>, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] cria um HWND de nível superior e usa um <xref:System.Windows.Interop.HwndSource> para colocar o <xref:System.Windows.Window> e seu conteúdo de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dentro do HWND.  O restante do seu conteúdo do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] no aplicativo compartilha aquele único HWND. Uma exceção são menus, caixas de combinação suspensas e outros pop-ups. Esses elementos criam sua própria janela de nível superior, razão pela qual um menu do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pode passar da borda do HWND da janela que o contém. Quando você usa <xref:System.Windows.Interop.HwndHost> para colocar um HWND dentro de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] informa ao Win32 como posicionar o novo HWND filho em relação ao [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Window> HWND.

Um conceito relacionado a HWND é a transparência dentro e entre cada HWND. Isso também é discutido no tópico [Visão geral das regiões de tecnologia](technology-regions-overview.md).

<a name="hosting_a_wpf_page"></a>

## <a name="hosting-wpf-content-in-a-microsoft-win32-window"></a>Hospedando conteúdo do WPF em uma janela do Microsoft Win32

A chave para hospedar um [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] em uma janela do Win32 é a classe <xref:System.Windows.Interop.HwndSource>. Essa classe encapsula o conteúdo de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] em uma janela do Win32, para que o conteúdo de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] possa ser incorporado à sua [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] como uma janela filho. A abordagem a seguir combina o Win32 e o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] em um único aplicativo.

1. Implemente o conteúdo do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] (o elemento de conteúdo raiz) como uma classe gerenciada. Normalmente, a classe herda de uma das classes que podem conter vários elementos filho e/ou usada como um elemento raiz, como <xref:System.Windows.Controls.DockPanel> ou <xref:System.Windows.Controls.Page>. Nas próximas etapas, essa classe será mencionada como classe de conteúdo do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] e as instâncias da classe serão mencionadas como objetos de conteúdo do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].

2. Implementar um aplicativo do Windows C++com o/CLI. Se você estiver começando com um C++ aplicativo não gerenciado existente, geralmente poderá habilitá-lo para chamar código gerenciado alterando as configurações do projeto para incluir o sinalizador do compilador de `/clr` (o escopo completo do que pode ser necessário para dar suporte `/clr` compilação não está descrito neste tópico).

3. Defina o modelo de threading para STA (Single-Threaded Apartment). O [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] usa esse modelo de threading.

4. Identifique a notificação WM_CREATE no seu procedimento de janela.

5. Dentro do manipulador (ou de uma função que o manipulador chama), faça o seguinte:

    1. Crie um novo objeto <xref:System.Windows.Interop.HwndSource> com a janela pai HWND como seu parâmetro `parent`.

    2. Crie uma instância da sua classe de conteúdo do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].

    3. Atribua uma referência ao objeto de conteúdo [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] à propriedade <xref:System.Windows.Interop.HwndSource.RootVisual%2A> objeto de <xref:System.Windows.Interop.HwndSource>.

    4. O objeto de <xref:System.Windows.Interop.HwndSource> <xref:System.Windows.Interop.HwndSource.Handle%2A> propriedade contém o identificador de janela (HWND). Para obter um HWND que você possa usar na parte não gerenciada de seu aplicativo, transmita `Handle.ToPointer()` para um HWND.

6. Implemente uma classe gerenciada que contenha um campo estático contendo uma referência ao seu objeto de conteúdo do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Essa classe permite que você obtenha uma referência para o objeto de conteúdo de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] do seu código Win32, mas, mais importante, ele impede que o <xref:System.Windows.Interop.HwndSource> seja inadvertidamente coletado pelo lixo.

7. Receba notificações do objeto de conteúdo do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], anexando um manipulador a um ou mais eventos de objeto de conteúdo do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].

8. Comunique-se com o objeto de conteúdo do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] usando a referência que você armazenou no campo estático para definir propriedades, chamar métodos, etc.

> [!NOTE]
> Você pode fazer algumas ou todas as definições de classe de conteúdo do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] da Etapa Um em [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] usando a classe parcial padrão da classe de conteúdo, se você gerar um assembly separado e, em seguida, referenciá-lo. Embora você normalmente inclua um objeto <xref:System.Windows.Application> como parte da compilação do [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] em um assembly, você não acaba usando esse <xref:System.Windows.Application> como parte da interoperação, basta usar uma ou mais das classes raiz para [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] arquivos referenciados pelo aplicativo e fazer referência a suas classes parciais. O restante do procedimento é basicamente semelhante ao descrito acima.
>
> Cada uma dessas etapas é ilustrada por meio do código no tópico [Passo a passo: hospedando conteúdo do WPF no Win32](walkthrough-hosting-wpf-content-in-win32.md).

<a name="hosting_an_hwnd"></a>

## <a name="hosting-a-microsoft-win32-window-in-wpf"></a>Hospedando uma janela do Microsoft Win32 no WPF

A chave para hospedar uma janela Win32 dentro de outros [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] conteúdo é a classe <xref:System.Windows.Interop.HwndHost>. Essa classe encapsula a janela em um elemento do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] que pode ser adicionado a uma árvore de elementos do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. o <xref:System.Windows.Interop.HwndHost> também dá suporte a APIs que permitem realizar tarefas como processar mensagens para a janela hospedada. O procedimento básico é:

1. Crie uma árvore de elementos para um aplicativo [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] (pode ser por meio de código ou marcação). Localizar um ponto apropriado e permitido na árvore de elementos em que a implementação de <xref:System.Windows.Interop.HwndHost> pode ser adicionada como um elemento filho. No restante dessas etapas, esse elemento será referenciado como elemento de reserva.

2. Derive de <xref:System.Windows.Interop.HwndHost> para criar um objeto que contém seu conteúdo Win32.

3. Nessa classe de host, substitua o método <xref:System.Windows.Interop.HwndHost> <xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A>. Retorne o HWND da janela hospedada. Talvez convenha encapsular os controles reais como uma janela filha da janela retornada. Encapsular os controles em uma janela host fornece uma maneira simples para que o conteúdo do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] receba notificações dos controles. Essa técnica ajuda a corrigir alguns problemas do Win32 em relação à manipulação de mensagens no limite do controle hospedado.

4. Substitua os métodos de <xref:System.Windows.Interop.HwndHost> <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A> e <xref:System.Windows.Interop.HwndHost.WndProc%2A>. A intenção aqui é processar a limpeza e remover as referências ao conteúdo hospedado, principalmente se você tiver criado referências a objetos não gerenciados.

5. No seu arquivo code-behind, crie uma instância da classe que hospeda controles e torne-a filha do elemento de reserva. Normalmente, você usaria um manipulador de eventos, como <xref:System.Windows.FrameworkElement.Loaded>, ou usar o construtor de classe parcial. Mas você também pode adicionar o conteúdo de interoperação por meio de um comportamento de runtime.

6. Processe mensagens de janela selecionadas, como notificações de controle. Há duas abordagens. Ambos fornecem acesso idêntico ao fluxo de mensagens, portanto sua escolha é principalmente uma questão de conveniência de programação.

    - Implemente o processamento de mensagens para todas as mensagens (não apenas mensagens de desligamento) em sua substituição do método <xref:System.Windows.Interop.HwndHost> <xref:System.Windows.Interop.HwndHost.WndProc%2A>.

    - Faça com que o elemento de hospedagem [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] processe as mensagens manipulando o evento <xref:System.Windows.Interop.HwndHost.MessageHook>. Esse evento é gerado para cada mensagem que é enviada ao procedimento de janela principal da janela hospedada.

    - Você não pode processar mensagens do Windows que estão fora do processo usando o <xref:System.Windows.Interop.HwndHost.WndProc%2A>.

7. Comunique-se com a janela hospedada usando a invocação de plataforma para chamar função `SendMessage` não gerenciada.

Seguir essas cria um aplicativo que funciona com a entrada do mouse. Você pode adicionar suporte para tabulação para sua janela hospedada implementando a interface <xref:System.Windows.Interop.IKeyboardInputSink>.

Cada uma dessas etapas é ilustrada por meio do código no tópico [Passo a passo: hospedando um controle do Win32 no WPF](walkthrough-hosting-a-win32-control-in-wpf.md).

### <a name="hwnds-inside-wpf"></a>Hwnds dentro do WPF

Você pode considerar <xref:System.Windows.Interop.HwndHost> como um controle especial. (Tecnicamente, <xref:System.Windows.Interop.HwndHost> é uma classe derivada <xref:System.Windows.FrameworkElement>, não uma classe derivada <xref:System.Windows.Controls.Control>, mas pode ser considerada um controle para fins de interoperação.) <xref:System.Windows.Interop.HwndHost> abstrai a natureza subjacente do Win32 do conteúdo hospedado de modo que o restante da [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] considere o conteúdo hospedado para outro objeto semelhante ao controle, que deve renderizar e processar a entrada. <xref:System.Windows.Interop.HwndHost> geralmente se comporta como qualquer outro [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.FrameworkElement>, embora existam algumas diferenças importantes em relação à saída (desenho e elementos gráficos) e à entrada (mouse e teclado) com base nas limitações de como os HWNDs subjacentes podem dar suporte.

#### <a name="notable-differences-in-output-behavior"></a>Diferenças notáveis no comportamento de saída

- <xref:System.Windows.FrameworkElement>, que é a classe base <xref:System.Windows.Interop.HwndHost>, tem algumas propriedades que implicam alterações na interface do usuário. Isso inclui propriedades como <xref:System.Windows.FrameworkElement.FlowDirection%2A?displayProperty=nameWithType>, que altera o layout dos elementos dentro desse elemento como um pai. No entanto, a maioria dessas propriedades não é mapeada para possíveis equivalentes do Win32, mesmo que tais equivalentes possam existir. Muitas dessas propriedades e seus significados são tão específicas da tecnologia de processamento para mapeamentos que não são práticas. Portanto, definir propriedades como <xref:System.Windows.FrameworkElement.FlowDirection%2A> em <xref:System.Windows.Interop.HwndHost> não tem nenhum efeito.

- a <xref:System.Windows.Interop.HwndHost> não pode ser girada, dimensionada, distorcida ou afetada de outra forma por uma transformação.

- <xref:System.Windows.Interop.HwndHost> não oferece suporte à propriedade <xref:System.Windows.UIElement.Opacity%2A> (mistura alfa). Se o conteúdo dentro da <xref:System.Windows.Interop.HwndHost> executar <xref:System.Drawing> operações que incluem informações alfa, isso não é uma violação, mas o <xref:System.Windows.Interop.HwndHost> como um todo dá suporte apenas a Opacity = 1,0 (100%).

- <xref:System.Windows.Interop.HwndHost> aparecerá na parte superior de outros elementos de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] na mesma janela de nível superior. No entanto, um menu <xref:System.Windows.Controls.ToolTip> ou <xref:System.Windows.Controls.ContextMenu> gerado é uma janela de nível superior separada e, portanto, se comportará corretamente com <xref:System.Windows.Interop.HwndHost>.

- <xref:System.Windows.Interop.HwndHost> não respeita a região de recorte de seu <xref:System.Windows.UIElement>pai. Isso é potencialmente um problema se você tentar colocar uma classe de <xref:System.Windows.Interop.HwndHost> dentro de uma região de rolagem ou <xref:System.Windows.Controls.Canvas>.

#### <a name="notable-differences-in-input-behavior"></a>Diferenças notáveis no comportamento de entrada

- Em geral, embora os dispositivos de entrada sejam incluídos no escopo da região Win32 hospedada <xref:System.Windows.Interop.HwndHost>, os eventos de entrada vão diretamente para o Win32.

- Enquanto o mouse estiver sobre a <xref:System.Windows.Interop.HwndHost>, seu aplicativo não receberá [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] eventos de mouse e o valor da propriedade [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.UIElement.IsMouseOver%2A> será `false`.

- Enquanto o <xref:System.Windows.Interop.HwndHost> tem o foco do teclado, seu aplicativo não receberá [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] eventos de teclado e o valor da propriedade [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.UIElement.IsKeyboardFocusWithin%2A> será `false`.

- Quando o foco está dentro da <xref:System.Windows.Interop.HwndHost> e muda para outro controle dentro da <xref:System.Windows.Interop.HwndHost>, seu aplicativo não receberá os eventos de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.UIElement.GotFocus> ou <xref:System.Windows.UIElement.LostFocus>.

- As propriedades e os eventos relacionados à caneta são análogos e não relatam informações enquanto a caneta está sobre <xref:System.Windows.Interop.HwndHost>.

<a name="tabbing_mnemonics_accelerators"></a>

## <a name="tabbing-mnemonics-and-accelerators"></a>Uso da tecla TAB, mnemônicos e aceleradores

As interfaces <xref:System.Windows.Interop.IKeyboardInputSink> e <xref:System.Windows.Interop.IKeyboardInputSite> permitem que você crie uma experiência de teclado direta para aplicativos mistos [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] e Win32:

- Tabulação entre os componentes do Win32 e do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]

- Mnemônicos e aceleradores que funcionam quando o foco está em um componente do Win32 e quando está em um componente do WPF.

As classes <xref:System.Windows.Interop.HwndHost> e <xref:System.Windows.Interop.HwndSource> fornecem implementações de <xref:System.Windows.Interop.IKeyboardInputSink>, mas elas não podem lidar com todas as mensagens de entrada que você deseja para cenários mais avançados. Substitua os métodos apropriados para obter o comportamento de teclado desejado.

As interfaces fornecem suporte apenas para o que acontece na transição entre as regiões [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] e Win32. Na região Win32, o comportamento de tabulação é totalmente controlado pela lógica implementada pelo Win32 para tabulação, se houver.

## <a name="see-also"></a>Veja também

- <xref:System.Windows.Interop.HwndHost>
- <xref:System.Windows.Interop.HwndSource>
- <xref:System.Windows.Interop>
- [Passo a passo: hospedando um controle Win32 no WPF](walkthrough-hosting-a-win32-control-in-wpf.md)
- [Passo a passo: hospedando conteúdo do WPF no Win32](walkthrough-hosting-wpf-content-in-win32.md)
