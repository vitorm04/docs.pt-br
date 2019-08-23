---
title: Interoperação Win32 e WPF
ms.date: 03/30/2017
helpviewer_keywords:
- hosting WPF content in Win32 window [WPF]
- HWND interop [WPF]
- Win32 code [WPF], WPF interoperation
- interoperability [WPF], Win32
ms.assetid: 0ffbde0d-701d-45a3-a6fa-dd71f4d9772e
ms.openlocfilehash: d13f4ce37dba45dc99f0481043d80640e73d833d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917482"
---
# <a name="wpf-and-win32-interoperation"></a>Interoperação Win32 e WPF
Este tópico fornece uma visão geral de como interoperar o código do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] e do [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]. O [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fornece um ambiente sofisticado para criação de aplicativos. No entanto, quando você tem um investimento significativo em código do [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)], pode ser mais eficiente reutilizar parte desse código.  

<a name="basics"></a>   
## <a name="wpf-and-win32-interoperation-basics"></a>Noções básicas de interoperação entre o Win32 e o WPF  
 Há duas técnicas básicas de interoperação entre o código do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] e do [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)].  
  
- Hospedar conteúdo do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] em uma janela do [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]. Com essa técnica, você pode usar as capacidades gráficas avançadas do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dentro da estrutura de uma janela e de um aplicativo padrão do [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)].  
  
- Hospedar uma janela do [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] no conteúdo do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Com essa técnica, você pode usar um controle do [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] personalizado no contexto de outro conteúdo do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] e passar dados entre os limites.  
  
 Essas duas técnicas são apresentadas conceitualmente neste tópico. Para obter uma ilustração mais orientada a código [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] de [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]hospedagem no [, consulte Passo a passos: Hospedando conteúdo do WPF](walkthrough-hosting-wpf-content-in-win32.md)no Win32. Para obter uma ilustração mais orientada a código [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]hospedagem no [, consulte Passo a passos: Hospedando um controle Win32 no](walkthrough-hosting-a-win32-control-in-wpf.md)WPF.  
  
<a name="projects"></a>   
## <a name="wpf-interoperation-projects"></a>Projetos de interoperação do WPF  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]APIs são código gerenciado, mas a maioria [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] dos programas existentes são escritas sem gerenciamento C++.  Você não pode [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] chamar APIs de um programa verdadeiro não gerenciado. No entanto, usando `/clr` a opção com [!INCLUDE[TLA#tla_visualcpp](../../../../includes/tlasharptla-visualcpp-md.md)] o compilador, você pode criar um programa misto gerenciado e não gerenciado, no qual você pode misturar diretamente chamadas de API gerenciadas e não gerenciadas.  
  
 Uma complicação no nível do projeto é que você [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] não pode compilar C++ arquivos em um projeto.  Há várias técnicas de divisão de projeto para compensar isso.  
  
- Crie uma C# dll que contenha todas [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] as suas páginas como um assembly compilado e, em C++ seguida, faça com que o executável inclua essa dll como referência.  
  
- Crie um C# executável para o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] conteúdo e faça com que ele faça C++ referência a uma dll [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] que contém o conteúdo.  
  
- Use <xref:System.Windows.Markup.XamlReader.Load%2A> para carregar qualquer [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] em tempo de execução, em vez de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]compilar seu.  
  
- Não use [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] todos, e escreva todos os seus [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] códigos no código, compilando a árvore de elementos <xref:System.Windows.Application>do.  
  
 Use a abordagem que funcionar melhor para você.  
  
> [!NOTE]
> Se você não tiver usado C++o/CLI antes, poderá observar algumas palavras-chave "novas", `gcnew` como e `nullptr` nos exemplos de código de interoperação. Essas palavras-chave substituem a sintaxe mais antiga de sublinhado`__gc`duplo () e fornecem uma sintaxe mais natural para código C++gerenciado no.  Para saber mais sobre os C++recursos gerenciados da/CLI, consulte [extensões de componente para plataformas de tempo de execução](/cpp/windows/component-extensions-for-runtime-platforms) e [Olá, C++/CLI](https://go.microsoft.com/fwlink/?LinkId=98739).  
  
<a name="hwnds"></a>   
## <a name="how-wpf-uses-hwnds"></a>Como o WPF usa Hwnds  
 Para aproveitar ao máximo a "Interoperabilidade de HWND" do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], você precisa entender como o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] usa HWNDs. Para qualquer HWND, você não pode [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] misturar renderização com renderização DirectX ou renderização GDI/GDI+. Isso tem várias implicações. Basicamente, para combinar esses modelos de renderização, você deve criar uma solução de interoperabilidade e usar segmentos de interoperação designados para cada modelo de renderização que optar usar. Além disso, o comportamento de renderização cria uma restrição de "espaço aéreo" para o que sua solução de interoperação pode realizar. O conceito de "espaço aéreo" é explicado com mais detalhes no tópico [Visão geral das regiões de tecnologia](technology-regions-overview.md).  
  
 Todos os elementos do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] na tela, por fim, contam com um HWND. Quando você cria um [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Window>, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] o cria um HWND de nível superior e usa um <xref:System.Windows.Interop.HwndSource> para colocar o <xref:System.Windows.Window> e seu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] conteúdo dentro do HWND.  O restante do seu conteúdo do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] no aplicativo compartilha aquele único HWND. Uma exceção são menus, caixas de combinação suspensas e outros pop-ups. Esses elementos criam sua própria janela de nível superior, razão pela qual um menu do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pode passar da borda do HWND da janela que o contém. Quando você usa <xref:System.Windows.Interop.HwndHost> para colocar um HWND dentro [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] o informa como posicionar o novo HWND filho em relação ao [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Window> HWND.  
  
 Um conceito relacionado a HWND é a transparência dentro e entre cada HWND. Isso também é discutido no tópico [Visão geral das regiões de tecnologia](technology-regions-overview.md).  
  
<a name="hosting_a_wpf_page"></a>   
## <a name="hosting-wpf-content-in-a-microsoft-win32-window"></a>Hospedando conteúdo do WPF em uma janela do Microsoft Win32  
 A chave para hospedar um [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] em uma [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] janela é a <xref:System.Windows.Interop.HwndSource> classe. Essa classe encapsula o conteúdo do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] em uma janela do [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)], para que o conteúdo do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] possa ser incorporado na [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] como uma janela filho. A abordagem a seguir combina o [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] e o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] em um único aplicativo.  
  
1. Implemente o conteúdo do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] (o elemento de conteúdo raiz) como uma classe gerenciada. Normalmente, a classe herda de uma das classes que podem conter vários elementos filho e/ou usada como um elemento raiz, <xref:System.Windows.Controls.DockPanel> como ou. <xref:System.Windows.Controls.Page> Nas próximas etapas, essa classe será mencionada como classe de conteúdo do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] e as instâncias da classe serão mencionadas como objetos de conteúdo do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
2. Implementar um aplicativo do Windows C++com o/CLI. Se você estiver começando com um C++ aplicativo não gerenciado existente, geralmente poderá habilitá-lo para chamar código gerenciado alterando as configurações do projeto para incluir `/clr` o sinalizador do compilador (o escopo completo do que pode ser necessário `/clr` para dar suporte a compilação não está descrita neste tópico).  
  
3. Defina o modelo de threading para STA (Single-Threaded Apartment). O [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] usa esse modelo de threading.  
  
4. Identifique a notificação WM_CREATE no seu procedimento de janela.  
  
5. Dentro do manipulador (ou de uma função que o manipulador chama), faça o seguinte:  
  
    1. Crie um novo <xref:System.Windows.Interop.HwndSource> objeto com a janela pai HWND como seu `parent` parâmetro.  
  
    2. Crie uma instância da sua classe de conteúdo do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
    3. Atribua uma referência ao [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] objeto de conteúdo <xref:System.Windows.Interop.HwndSource> à propriedade Object <xref:System.Windows.Interop.HwndSource.RootVisual%2A> .  
  
    4. A <xref:System.Windows.Interop.HwndSource> propriedade <xref:System.Windows.Interop.HwndSource.Handle%2A> Object contém o identificador de janela (HWND). Para obter um HWND que você possa usar na parte não gerenciada de seu aplicativo, transmita `Handle.ToPointer()` para um HWND.  
  
6. Implemente uma classe gerenciada que contenha um campo estático contendo uma referência ao seu objeto de conteúdo do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Essa classe permite que você obtenha uma referência ao [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] objeto de conteúdo do seu [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] código, mas, mais importante, ele impede que o <xref:System.Windows.Interop.HwndSource> lixo inadvertidamente seja coletado.  
  
7. Receba notificações do objeto de conteúdo do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], anexando um manipulador a um ou mais eventos de objeto de conteúdo do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
8. Comunique-se com o objeto de conteúdo do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] usando a referência que você armazenou no campo estático para definir propriedades, chamar métodos, etc.  
  
> [!NOTE]
> Você pode fazer algumas ou todas as definições de classe de conteúdo do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] da Etapa Um em [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] usando a classe parcial padrão da classe de conteúdo, se você gerar um assembly separado e, em seguida, referenciá-lo. Embora você normalmente inclua um <xref:System.Windows.Application> objeto como parte da compilação do [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] em um assembly, você não acaba usando isso <xref:System.Windows.Application> como parte da interoperação, basta usar uma ou mais das classes raiz para [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] os arquivos referenciados para o aplicativo e referenciar suas classes parciais. O restante do procedimento é basicamente semelhante ao descrito acima.  
>   
>  Cada uma dessas etapas é ilustrada por meio do código [no tópico Walkthrough: Hospedando conteúdo do WPF](walkthrough-hosting-wpf-content-in-win32.md)no Win32.  
  
<a name="hosting_an_hwnd"></a>   
## <a name="hosting-a-microsoft-win32-window-in-wpf"></a>Hospedando uma janela do Microsoft Win32 no WPF  
 A chave para hospedar uma [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] janela dentro de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] outro conteúdo é <xref:System.Windows.Interop.HwndHost> a classe. Essa classe encapsula a janela em um elemento do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] que pode ser adicionado a uma árvore de elementos do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. <xref:System.Windows.Interop.HwndHost>também dá suporte a APIs que permitem realizar tarefas como processar mensagens para a janela hospedada. O procedimento básico é:  
  
1. Crie uma árvore de elementos para um aplicativo [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] (pode ser por meio de código ou marcação). Localizar um ponto apropriado e permitido na árvore de elementos, em <xref:System.Windows.Interop.HwndHost> que a implementação pode ser adicionada como um elemento filho. No restante dessas etapas, esse elemento será referenciado como elemento de reserva.  
  
2. Derive <xref:System.Windows.Interop.HwndHost> de para criar um objeto que contém [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] seu conteúdo.  
  
3. Nessa classe de host, substitua o <xref:System.Windows.Interop.HwndHost> método <xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A>. Retorne o HWND da janela hospedada. Talvez convenha encapsular os controles reais como uma janela filha da janela retornada. Encapsular os controles em uma janela host fornece uma maneira simples para que o conteúdo do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] receba notificações dos controles. Essa técnica ajuda a corrigir alguns problemas do [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] em relação à manipulação de mensagens no limite do controle hospedado.  
  
4. Substitua os <xref:System.Windows.Interop.HwndHost> métodos <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A> e <xref:System.Windows.Interop.HwndHost.WndProc%2A>. A intenção aqui é processar a limpeza e remover as referências ao conteúdo hospedado, principalmente se você tiver criado referências a objetos não gerenciados.  
  
5. No seu arquivo code-behind, crie uma instância da classe que hospeda controles e torne-a filha do elemento de reserva. Normalmente <xref:System.Windows.FrameworkElement.Loaded>, você usaria um manipulador de eventos como, ou usaria o construtor de classe parcial. Mas você também pode adicionar o conteúdo de interoperação por meio de um comportamento de tempo de execução.  
  
6. Processe mensagens de janela selecionadas, como notificações de controle. Há duas abordagens. Ambos fornecem acesso idêntico ao fluxo de mensagens, portanto sua escolha é principalmente uma questão de conveniência de programação.  
  
    - Implemente o <xref:System.Windows.Interop.HwndHost> processamento de mensagens para todas as mensagens (não apenas mensagens de desligamento <xref:System.Windows.Interop.HwndHost.WndProc%2A>) em sua substituição do método.  
  
    - Faça com que [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] o elemento de hospedagem processe as mensagens <xref:System.Windows.Interop.HwndHost.MessageHook> manipulando o evento. Esse evento é gerado para cada mensagem que é enviada ao procedimento de janela principal da janela hospedada.  
  
    - Você não pode processar mensagens do Windows que estão fora do processo <xref:System.Windows.Interop.HwndHost.WndProc%2A>usando o.  
  
7. Comunique-se com a janela hospedada usando a invocação de plataforma para chamar função `SendMessage` não gerenciada.  
  
 Seguir essas cria um aplicativo que funciona com a entrada do mouse. Você pode adicionar suporte para tabulação para sua janela hospedada implementando a <xref:System.Windows.Interop.IKeyboardInputSink> interface.  
  
 Cada uma dessas etapas é ilustrada por meio do código [no tópico Walkthrough: Hospedando um controle Win32 no](walkthrough-hosting-a-win32-control-in-wpf.md)WPF.  
  
### <a name="hwnds-inside-wpf"></a>Hwnds dentro do WPF  
 Você pode considerar <xref:System.Windows.Interop.HwndHost> como um controle especial. (Tecnicamente, <xref:System.Windows.Interop.HwndHost> é uma <xref:System.Windows.FrameworkElement> classe derivada, não uma <xref:System.Windows.Controls.Control> classe derivada, mas pode ser considerada um controle para fins de interoperação.) abstrai a natureza subjacente [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] do conteúdo hospedado, de modo que o restante de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] considera o conteúdo hospedado como outro objeto semelhante ao controle, que deve renderizar e processar a entrada. <xref:System.Windows.Interop.HwndHost> <xref:System.Windows.Interop.HwndHost>geralmente se comporta como qualquer outro [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.FrameworkElement>, embora haja algumas diferenças importantes em relação à saída (desenho e elementos gráficos) e à entrada (mouse e teclado) com base nas limitações do que os HWNDs subjacentes podem dar suporte.  
  
#### <a name="notable-differences-in-output-behavior"></a>Diferenças notáveis no comportamento de saída  
  
- <xref:System.Windows.FrameworkElement>, que é a <xref:System.Windows.Interop.HwndHost> classe base, tem algumas propriedades que implicam alterações na interface do usuário. Elas incluem propriedades como <xref:System.Windows.FrameworkElement.FlowDirection%2A?displayProperty=nameWithType>, que alteram o layout dos elementos dentro desse elemento como um pai. No entanto, a maioria dessas propriedades não é mapeada para possíveis equivalentes do [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)], mesmo que tais equivalentes possam existir. Muitas dessas propriedades e seus significados são tão específicas da tecnologia de processamento para mapeamentos que não são práticas. Portanto, a <xref:System.Windows.FrameworkElement.FlowDirection%2A> definição de propriedades como <xref:System.Windows.Interop.HwndHost> on não tem nenhum efeito.  
  
- <xref:System.Windows.Interop.HwndHost>Não pode ser girado, dimensionado, inclinado ou, de outra forma, afetado por uma transformação.  
  
- <xref:System.Windows.Interop.HwndHost>não oferece suporte à <xref:System.Windows.UIElement.Opacity%2A> Propriedade (mistura alfa). Se o conteúdo dentro <xref:System.Windows.Interop.HwndHost> do <xref:System.Drawing> executar operações que incluem informações alfa, isso não é uma violação, mas o <xref:System.Windows.Interop.HwndHost> como um todo dá suporte apenas a Opacity = 1,0 (100%).  
  
- <xref:System.Windows.Interop.HwndHost>aparecerá na parte superior de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] outros elementos na mesma janela de nível superior. No entanto <xref:System.Windows.Controls.ToolTip> , <xref:System.Windows.Controls.ContextMenu> um menu ou gerado é uma janela de nível superior separada e, portanto, se <xref:System.Windows.Interop.HwndHost>comportará corretamente com o.  
  
- <xref:System.Windows.Interop.HwndHost>Não respeita a região de recorte de seu pai <xref:System.Windows.UIElement>. Isso é potencialmente um problema se você tentar colocar uma <xref:System.Windows.Interop.HwndHost> classe dentro de uma região de rolagem ou. <xref:System.Windows.Controls.Canvas>  
  
#### <a name="notable-differences-in-input-behavior"></a>Diferenças notáveis no comportamento de entrada  
  
- Em geral, enquanto os dispositivos de entrada têm o <xref:System.Windows.Interop.HwndHost> escopo definido na região hospedada [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] , os eventos [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]de entrada vão diretamente para.  
  
- Enquanto o mouse estiver sobre o <xref:System.Windows.Interop.HwndHost>, seu aplicativo não receberá [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] eventos `false`de mouse [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] e o valor da propriedade <xref:System.Windows.UIElement.IsMouseOver%2A> será.  
  
- Enquanto o <xref:System.Windows.Interop.HwndHost> teclado tem o foco, seu aplicativo não receberá [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] eventos `false`de teclado [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] e o valor da <xref:System.Windows.UIElement.IsKeyboardFocusWithin%2A> propriedade será.  
  
- Quando o foco está dentro <xref:System.Windows.Interop.HwndHost> do e muda para outro controle dentro <xref:System.Windows.Interop.HwndHost>do, seu aplicativo não receberá [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] os <xref:System.Windows.UIElement.GotFocus> eventos <xref:System.Windows.UIElement.LostFocus>ou.  
  
- Eventos e propriedades de caneta relacionadas são análogos e não relatam informações enquanto a caneta terminar <xref:System.Windows.Interop.HwndHost>.  
  
<a name="tabbing_mnemonics_accelerators"></a>   
## <a name="tabbing-mnemonics-and-accelerators"></a>Uso da tecla TAB, mnemônicos e aceleradores  
 As <xref:System.Windows.Interop.IKeyboardInputSink> interfaces <xref:System.Windows.Interop.IKeyboardInputSite> e permitem que você crie uma experiência de [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] teclado direta para [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplicativos mistos:  
  
- Uso da tecla TAB entre componentes do [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] e do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]  
  
- Mnemônicos e aceleradores que funcionam quando o foco está em um componente do Win32 e quando está em um componente do WPF.  
  
 As <xref:System.Windows.Interop.HwndHost> classes <xref:System.Windows.Interop.HwndSource> e fornecem implementações do <xref:System.Windows.Interop.IKeyboardInputSink>, mas elas não podem lidar com todas as mensagens de entrada que você deseja para cenários mais avançados. Substitua os métodos apropriados para obter o comportamento de teclado desejado.  
  
 As interfaces somente dão suporte para o que acontece na transição entre as regiões do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] e do [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]. Dentro da região do [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)], o comportamento de uso da tecla TAB é totalmente controlado pela lógica implementada do [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)], caso haja alguma.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Interop.HwndHost>
- <xref:System.Windows.Interop.HwndSource>
- <xref:System.Windows.Interop>
- [Passo a passo: Hospedando um controle Win32 no WPF](walkthrough-hosting-a-win32-control-in-wpf.md)
- [Passo a passo: Hospedando conteúdo do WPF no Win32](walkthrough-hosting-wpf-content-in-win32.md)
