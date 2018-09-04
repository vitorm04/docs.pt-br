---
title: Interoperação Win32 e WPF
ms.date: 03/30/2017
helpviewer_keywords:
- hosting WPF content in Win32 window [WPF]
- HWND interop [WPF]
- Win32 code [WPF], WPF interoperation
- interoperability [WPF], Win32
ms.assetid: 0ffbde0d-701d-45a3-a6fa-dd71f4d9772e
ms.openlocfilehash: 733a4d4ee7296d96a18e8ba4763dfa12e218c028
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43526511"
---
# <a name="wpf-and-win32-interoperation"></a>Interoperação Win32 e WPF
Este tópico fornece uma visão geral de como interoperar o código do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] e do [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]. O [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fornece um ambiente sofisticado para criação de aplicativos. No entanto, quando você tem um investimento significativo em código do [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)], pode ser mais eficiente reutilizar parte desse código.  
  

  
<a name="basics"></a>   
## <a name="wpf-and-win32-interoperation-basics"></a>Noções básicas de interoperação entre o Win32 e o WPF  
 Há duas técnicas básicas de interoperação entre o código do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] e do [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)].  
  
-   Hospedar conteúdo do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] em uma janela do [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]. Com essa técnica, você pode usar as capacidades gráficas avançadas do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dentro da estrutura de uma janela e de um aplicativo padrão do [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)].  
  
-   Hospedar uma janela do [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] no conteúdo do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Com essa técnica, você pode usar um controle do [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] personalizado no contexto de outro conteúdo do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] e passar dados entre os limites.  
  
 Essas duas técnicas são apresentadas conceitualmente neste tópico. Para obter uma ilustração mais orientada a código da hospedagem do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] no [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)], consulte [Passo a passo: hospedando conteúdo do WPF no Win32](../../../../docs/framework/wpf/advanced/walkthrough-hosting-wpf-content-in-win32.md). Para obter uma ilustração mais orientada a código da hospedagem do [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] no [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], consulte [Passo a passo: hospedando um controle do Win32 no WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-win32-control-in-wpf.md).  
  
<a name="projects"></a>   
## <a name="wpf-interoperation-projects"></a>Projetos de interoperação do WPF  
 As [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] são códigos gerenciados, mas a maioria dos programas do [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] existentes são gravados em [!INCLUDE[TLA2#tla_cpp](../../../../includes/tla2sharptla-cpp-md.md)] não gerenciado.  Não é possível chamar [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] de um programa realmente não gerenciado. No entanto, usando a opção `/clr` com o compilador [!INCLUDE[TLA#tla_visualcpp](../../../../includes/tlasharptla-visualcpp-md.md)], você pode criar um programa misto gerenciado e não gerenciado no qual pode misturar perfeitamente chamadas de [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] gerenciadas e não gerenciadas.  
  
 Uma complicação no nível do projeto é que você não pode compilar arquivos [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] em um projeto [!INCLUDE[TLA2#tla_cpp](../../../../includes/tla2sharptla-cpp-md.md)].  Há várias técnicas de divisão de projeto para compensar isso.  
  
-   Criar uma DLL do c# que contém todos os seus [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] páginas como um assembly compilado e, em seguida, ter seu [!INCLUDE[TLA2#tla_cpp](../../../../includes/tla2sharptla-cpp-md.md)] executável incluem que [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] como uma referência.  
  
-   Criar um c# executável para o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] de conteúdo e a fazer referência a um [!INCLUDE[TLA2#tla_cpp](../../../../includes/tla2sharptla-cpp-md.md)] [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] que contém o [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] conteúdo.  
  
-   Use <xref:System.Windows.Markup.XamlReader.Load%2A> para carregar qualquer [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] em tempo de execução, em vez de compilar seu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
-   Não use [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] e gravar todos os seus [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] no código, construindo a árvore de elementos de <xref:System.Windows.Application>.  
  
 Use a abordagem que funcionar melhor para você.  
  
> [!NOTE]
>  Se você nunca usou [!INCLUDE[TLA#tla_cppcli](../../../../includes/tlasharptla-cppcli-md.md)], poderá notar algumas palavras-chave "novas", como `gcnew` e `nullptr` nos exemplos de código de interoperação. Essas palavras-chave substituem a antiga sintaxe com sublinhado duplo (`__gc`) e fornecem uma sintaxe mais natural para o código gerenciado em [!INCLUDE[TLA2#tla_cpp](../../../../includes/tla2sharptla-cpp-md.md)].  Para saber mais sobre as funcionalidades gerenciadas [!INCLUDE[TLA#tla_cppcli](../../../../includes/tlasharptla-cppcli-md.md)], consulte [Component Extensions for Runtime Platforms](/cpp/windows/component-extensions-for-runtime-platforms) (Extensões de componente para plataformas de tempo de execução) e [Hello, C++/CLI](https://go.microsoft.com/fwlink/?LinkId=98739) (Olá, C++/CLI).  
  
<a name="hwnds"></a>   
## <a name="how-wpf-uses-hwnds"></a>Como o WPF usa Hwnds  
 Para aproveitar ao máximo a "Interoperabilidade de HWND" do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], você precisa entender como o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] usa HWNDs. Para qualquer HWND, você não pode combinar a renderização do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] com a renderização do [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] ou a renderização do [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] / [!INCLUDE[TLA2#tla_gdiplus](../../../../includes/tla2sharptla-gdiplus-md.md)]. Isso tem várias implicações. Basicamente, para combinar esses modelos de renderização, você deve criar uma solução de interoperabilidade e usar segmentos de interoperação designados para cada modelo de renderização que optar usar. Além disso, o comportamento de renderização cria uma restrição de "espaço aéreo" para o que sua solução de interoperação pode realizar. O conceito de "espaço aéreo" é explicado com mais detalhes no tópico [Visão geral das regiões de tecnologia](../../../../docs/framework/wpf/advanced/technology-regions-overview.md).  
  
 Todos os elementos do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] na tela, por fim, contam com um HWND. Quando você cria um [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Window>, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] cria um HWND de alto nível e usa um <xref:System.Windows.Interop.HwndSource> colocar o <xref:System.Windows.Window> e sua [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] conteúdo dentro do HWND.  O restante do seu conteúdo do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] no aplicativo compartilha aquele único HWND. Uma exceção são menus, caixas de combinação suspensas e outros pop-ups. Esses elementos criam sua própria janela de nível superior, razão pela qual um menu do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pode passar da borda do HWND da janela que o contém. Quando você usa <xref:System.Windows.Interop.HwndHost> para colocar um HWND dentro [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] informa [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] como posicionar o novo HWND filho em relação para o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Window> HWND.  
  
 Um conceito relacionado a HWND é a transparência dentro e entre cada HWND. Isso também é discutido no tópico [Visão geral das regiões de tecnologia](../../../../docs/framework/wpf/advanced/technology-regions-overview.md).  
  
<a name="hosting_a_wpf_page"></a>   
## <a name="hosting-wpf-content-in-a-microsoft-win32-window"></a>Hospedando conteúdo do WPF em uma janela do Microsoft Win32  
 A chave para hospedar uma [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] em um [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] janela é o <xref:System.Windows.Interop.HwndSource> classe. Essa classe encapsula o conteúdo do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] em uma janela do [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)], para que o conteúdo do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] possa ser incorporado na [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] como uma janela filho. A abordagem a seguir combina o [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] e o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] em um único aplicativo.  
  
1.  Implemente o conteúdo do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] (o elemento de conteúdo raiz) como uma classe gerenciada. Normalmente, a classe herda de uma das classes que podem conter vários elementos filho e/ou usado como um elemento raiz, como <xref:System.Windows.Controls.DockPanel> ou <xref:System.Windows.Controls.Page>. Nas próximas etapas, essa classe será mencionada como classe de conteúdo do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] e as instâncias da classe serão mencionadas como objetos de conteúdo do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
2.  Implementar um aplicativo [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] com [!INCLUDE[TLA2#tla_cppcli](../../../../includes/tla2sharptla-cppcli-md.md)]. Se você está começando com um aplicativo [!INCLUDE[TLA2#tla_cpp](../../../../includes/tla2sharptla-cpp-md.md)] não gerenciado existente, normalmente, é possível habilitá-lo para chamar o código gerenciado alterando as configurações do projeto para incluir o sinalizador do compilador `/clr` (o escopo completo do que pode ser necessário para dar suporte à compilação `/clr` não está descrita neste tópico).  
  
3.  Defina o modelo de threading para STA (Single-Threaded Apartment). O [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] usa esse modelo de threading.  
  
4.  Identifique a notificação WM_CREATE no seu procedimento de janela.  
  
5.  Dentro do manipulador (ou de uma função que o manipulador chama), faça o seguinte:  
  
    1.  Criar um novo <xref:System.Windows.Interop.HwndSource> objeto com o HWND da janela pai como seu `parent` parâmetro.  
  
    2.  Crie uma instância da sua classe de conteúdo do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
    3.  Atribua uma referência para o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] o objeto de conteúdo para o <xref:System.Windows.Interop.HwndSource> objeto <xref:System.Windows.Interop.HwndSource.RootVisual%2A> propriedade.  
  
    4.  O <xref:System.Windows.Interop.HwndSource> objeto <xref:System.Windows.Interop.HwndSource.Handle%2A> propriedade contém o identificador de janela (HWND). Para obter um HWND que você possa usar na parte não gerenciada de seu aplicativo, transmita `Handle.ToPointer()` para um HWND.  
  
6.  Implemente uma classe gerenciada que contenha um campo estático contendo uma referência ao seu objeto de conteúdo do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Essa classe permite que você obtenha uma referência para o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] objeto de conteúdo do seu [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] código, mas mais importante, impede que seu <xref:System.Windows.Interop.HwndSource> sejam inadvertidamente coletados pelo lixo.  
  
7.  Receba notificações do objeto de conteúdo do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], anexando um manipulador a um ou mais eventos de objeto de conteúdo do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
8.  Comunique-se com o objeto de conteúdo do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] usando a referência que você armazenou no campo estático para definir propriedades, chamar métodos, etc.  
  
> [!NOTE]
>  Você pode fazer algumas ou todas as definições de classe de conteúdo do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] da Etapa Um em [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] usando a classe parcial padrão da classe de conteúdo, se você gerar um assembly separado e, em seguida, referenciá-lo. Embora você normalmente inclua um <xref:System.Windows.Application> objeto como parte da compilação a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] em um assembly, você acaba não usando essa <xref:System.Windows.Application> como parte da interoperação, você apenas use um ou mais das classes raiz para [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] arquivos conhecidos para o aplicativo e referencia suas classes parciais. O restante do procedimento é basicamente semelhante ao descrito acima.  
>   
>  Cada uma dessas etapas é ilustrada por meio do código no tópico [Passo a passo: hospedando conteúdo do WPF no Win32](../../../../docs/framework/wpf/advanced/walkthrough-hosting-wpf-content-in-win32.md).  
  
<a name="hosting_an_hwnd"></a>   
## <a name="hosting-a-microsoft-win32-window-in-wpf"></a>Hospedando uma janela do Microsoft Win32 no WPF  
 A chave para hospedar uma [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] janela dentro de outras [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] conteúdo é o <xref:System.Windows.Interop.HwndHost> classe. Essa classe encapsula a janela em um elemento do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] que pode ser adicionado a uma árvore de elementos do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. <xref:System.Windows.Interop.HwndHost> também dá suporte a [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] que permitem executar tarefas, como processar as mensagens para a janela hospedada. O procedimento básico é:  
  
1.  Crie uma árvore de elementos para um aplicativo [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] (pode ser por meio de código ou marcação). Localize um ponto adequado e permitido na árvore de elementos em que o <xref:System.Windows.Interop.HwndHost> implementação pode ser adicionada como um elemento filho. No restante dessas etapas, esse elemento será referenciado como elemento de reserva.  
  
2.  Derivam <xref:System.Windows.Interop.HwndHost> para criar um objeto que contém seu [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] conteúdo.  
  
3.  Na classe host, substituir os <xref:System.Windows.Interop.HwndHost> método <xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A>. Retorne o HWND da janela hospedada. Talvez convenha encapsular os controles reais como uma janela filha da janela retornada. Encapsular os controles em uma janela host fornece uma maneira simples para que o conteúdo do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] receba notificações dos controles. Essa técnica ajuda a corrigir alguns problemas do [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] em relação à manipulação de mensagens no limite do controle hospedado.  
  
4.  Substituir a <xref:System.Windows.Interop.HwndHost> métodos <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A> e <xref:System.Windows.Interop.HwndHost.WndProc%2A>. A intenção aqui é processar a limpeza e remover as referências ao conteúdo hospedado, principalmente se você tiver criado referências a objetos não gerenciados.  
  
5.  No seu arquivo code-behind, crie uma instância da classe que hospeda controles e torne-a filha do elemento de reserva. Normalmente você usaria um manipulador de eventos, como <xref:System.Windows.FrameworkElement.Loaded>, ou usar o construtor de classe parcial. Mas você também pode adicionar o conteúdo de interoperação por meio de um comportamento de tempo de execução.  
  
6.  Processe mensagens de janela selecionadas, como notificações de controle. Há duas abordagens. Ambos fornecem acesso idêntico ao fluxo de mensagens, portanto sua escolha é principalmente uma questão de conveniência de programação.  
  
    -   Processamento de todas as mensagens (não apenas mensagens de desligamento) em seu substituto de mensagens de implementar o <xref:System.Windows.Interop.HwndHost> método <xref:System.Windows.Interop.HwndHost.WndProc%2A>.  
  
    -   Ter a hospedagem [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elemento processar as mensagens manipulando o <xref:System.Windows.Interop.HwndHost.MessageHook> eventos. Esse evento é gerado para cada mensagem que é enviada ao procedimento de janela principal da janela hospedada.  
  
    -   Você não pode processar as mensagens de janelas que estão fora do processo usando <xref:System.Windows.Interop.HwndHost.WndProc%2A>.  
  
7.  Comunique-se com a janela hospedada usando a invocação de plataforma para chamar função `SendMessage` não gerenciada.  
  
 Seguir essas cria um aplicativo que funciona com a entrada do mouse. Você pode adicionar suporte a TAB para sua janela hospedada Implementando a <xref:System.Windows.Interop.IKeyboardInputSink> interface.  
  
 Cada uma dessas etapas é ilustrada por meio do código no tópico [Passo a passo: hospedando um controle do Win32 no WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-win32-control-in-wpf.md).  
  
### <a name="hwnds-inside-wpf"></a>Hwnds dentro do WPF  
 Você pode pensar <xref:System.Windows.Interop.HwndHost> como um controle especial. (Tecnicamente, <xref:System.Windows.Interop.HwndHost> é um <xref:System.Windows.FrameworkElement> derivado de classe, não um <xref:System.Windows.Controls.Control> classe derivada, mas ele pode ser considerado um controle para fins de interoperação.) <xref:System.Windows.Interop.HwndHost> abstrai a [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] natureza do conteúdo hospedado, de modo que o restante do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] considera o conteúdo hospedado como outro objeto do tipo controle, que deve renderizar e processar a entrada. <xref:System.Windows.Interop.HwndHost> geralmente se comporta como qualquer outro [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.FrameworkElement>, embora há algumas diferenças importantes em torno de saída (desenho e gráficos) e pode dar suporte a entrada (mouse e teclado) com base nas limitações de que os HWNDs subjacentes.  
  
#### <a name="notable-differences-in-output-behavior"></a>Diferenças notáveis no comportamento de saída  
  
-   <xref:System.Windows.FrameworkElement>, que é o <xref:System.Windows.Interop.HwndHost> classe base, tem muito poucas propriedades que implicam alterações na interface do usuário. Estas incluem propriedades como <xref:System.Windows.FrameworkElement.FlowDirection%2A?displayProperty=nameWithType>, que altera o layout dos elementos dentro desse elemento como um pai. No entanto, a maioria dessas propriedades não é mapeada para possíveis equivalentes do [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)], mesmo que tais equivalentes possam existir. Muitas dessas propriedades e seus significados são tão específicas da tecnologia de processamento para mapeamentos que não são práticas. Portanto, definir propriedades como <xref:System.Windows.FrameworkElement.FlowDirection%2A> em <xref:System.Windows.Interop.HwndHost> não tem nenhum efeito.  
  
-   <xref:System.Windows.Interop.HwndHost> não pode ser girada, dimensionada, distorcida ou caso contrário, afetadas por uma transformação.  
  
-   <xref:System.Windows.Interop.HwndHost> não oferece suporte a <xref:System.Windows.UIElement.Opacity%2A> propriedade (a combinação alfa). Se o conteúdo dentro do <xref:System.Windows.Interop.HwndHost> executa <xref:System.Drawing> operações que incluem informações de alfa, que em si não é uma violação, mas o <xref:System.Windows.Interop.HwndHost> como um todo somente dá suporte à opacidade = 1.0 (100%).  
  
-   <xref:System.Windows.Interop.HwndHost> aparecerá acima dos outros [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elementos na mesma janela de nível superior. No entanto, uma <xref:System.Windows.Controls.ToolTip> ou <xref:System.Windows.Controls.ContextMenu> menu gerado é uma janela de nível superior separada e então se comportará corretamente com <xref:System.Windows.Interop.HwndHost>.  
  
-   <xref:System.Windows.Interop.HwndHost> não respeita a região de recorte de seu pai <xref:System.Windows.UIElement>. É possível que haja um problema se você tentar colocar uma <xref:System.Windows.Interop.HwndHost> classe dentro de uma região de rolagem ou <xref:System.Windows.Controls.Canvas>.  
  
#### <a name="notable-differences-in-input-behavior"></a>Diferenças notáveis no comportamento de entrada  
  
-   Em geral, enquanto os dispositivos de entrada tem escopo dentro de <xref:System.Windows.Interop.HwndHost> hospedados [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] região, eventos de entrada vão diretamente para [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)].  
  
-   Enquanto o mouse está sobre o <xref:System.Windows.Interop.HwndHost>, seu aplicativo não receberá [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] eventos de mouse e o valor da [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] propriedade <xref:System.Windows.UIElement.IsMouseOver%2A> será `false`.  
  
-   Enquanto o <xref:System.Windows.Interop.HwndHost> tem o foco do teclado, seu aplicativo não receberá [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] eventos e o valor de teclado a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] propriedade <xref:System.Windows.UIElement.IsKeyboardFocusWithin%2A> será `false`.  
  
-   Quando o foco estiver dentro a <xref:System.Windows.Interop.HwndHost> e as alterações para outro controle dentro a <xref:System.Windows.Interop.HwndHost>, seu aplicativo não receberá a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] eventos <xref:System.Windows.UIElement.GotFocus> ou <xref:System.Windows.UIElement.LostFocus>.  
  
-   Caneta propriedades e eventos são análogos e não relatam informações enquanto a caneta está sobre relacionados <xref:System.Windows.Interop.HwndHost>.  
  
<a name="tabbing_mnemonics_accelerators"></a>   
## <a name="tabbing-mnemonics-and-accelerators"></a>Uso da tecla TAB, mnemônicos e aceleradores  
 O <xref:System.Windows.Interop.IKeyboardInputSink> e <xref:System.Windows.Interop.IKeyboardInputSite> interfaces permitem que você crie uma experiência de teclado perfeita para misto [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] e [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] aplicativos:  
  
-   Uso da tecla TAB entre componentes do [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] e do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]  
  
-   Mnemônicos e aceleradores que funcionam quando o foco está em um componente do Win32 e quando está em um componente do WPF.  
  
 O <xref:System.Windows.Interop.HwndHost> e <xref:System.Windows.Interop.HwndSource> classes fornecem implementações de <xref:System.Windows.Interop.IKeyboardInputSink>, mas elas não podem tratar todas as mensagens de entrada que você deseja para cenários mais avançados. Substitua os métodos apropriados para obter o comportamento de teclado desejado.  
  
 As interfaces somente dão suporte para o que acontece na transição entre as regiões do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] e do [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]. Dentro da região do [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)], o comportamento de uso da tecla TAB é totalmente controlado pela lógica implementada do [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)], caso haja alguma.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Interop.HwndHost>  
 <xref:System.Windows.Interop.HwndSource>  
 <xref:System.Windows.Interop>  
 [Passo a passo: hospedando um controle Win32 no WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-win32-control-in-wpf.md)  
 [Passo a passo: hospedando conteúdo do WPF em Win32](../../../../docs/framework/wpf/advanced/walkthrough-hosting-wpf-content-in-win32.md)
