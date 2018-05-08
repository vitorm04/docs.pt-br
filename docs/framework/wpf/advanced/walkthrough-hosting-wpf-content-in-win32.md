---
title: 'Instruções passo a passo: hospedando conteúdo do WPF em Win32'
ms.date: 03/30/2017
dev_langs:
- cpp
helpviewer_keywords:
- hosting WPF content in Win32 window [WPF]
ms.assetid: 38ce284a-4303-46dd-b699-c9365b22a7dc
ms.openlocfilehash: 429acf6e3b37f5532e031fdef999d252a3aae3cb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-hosting-wpf-content-in-win32"></a>Instruções passo a passo: hospedando conteúdo do WPF em Win32
O [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fornece um ambiente avançado para a criação de aplicativos. No entanto, quando você tem um investimento significativo em [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] código, talvez seja mais eficiente adicionar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] funcionalidade ao seu aplicativo em vez de reescrever o código original. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Fornece um mecanismo simples para hospedar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] conteúdo em um [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] janela.  
  
 Este tutorial descreve como escrever um aplicativo de exemplo, [hospedando conteúdo WPF em um exemplo de janela Win32](http://go.microsoft.com/fwlink/?LinkID=160004), que hospeda [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] conteúdo em um [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] janela. Você pode estender este exemplo para hospedar qualquer [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] janela. Porque envolve a mistura de código gerenciado e não gerenciado, o aplicativo é escrito em [!INCLUDE[TLA#tla_cppcli](../../../../includes/tlasharptla-cppcli-md.md)].  
  
 
  
<a name="requirements"></a>   
## <a name="requirements"></a>Requisitos  
 Este tutorial assume uma familiaridade básica com ambos [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] e [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] de programação. Para obter uma introdução básica [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] de programação, consulte [Introdução](../../../../docs/framework/wpf/getting-started/index.md). Para obter uma introdução ao [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] de programação, consulte qualquer dos numerosos livros no assunto, em particular *Programming Windows* por Charles Petzold.  
  
 Como o exemplo que acompanha este tutorial é implementado em [!INCLUDE[TLA#tla_cppcli](../../../../includes/tlasharptla-cppcli-md.md)], este tutorial assume familiaridade com o uso de [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] ao programa de [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] mais um conhecimento de programação de código gerenciado. Familiaridade com [!INCLUDE[TLA#tla_cppcli](../../../../includes/tlasharptla-cppcli-md.md)] é útil, mas não essenciais.  
  
> [!NOTE]
>  Este tutorial inclui vários exemplos de código da amostra associada. No entanto, para facilitar a leitura, não inclui o código de exemplo completo. Para o código de exemplo completo, consulte [hospedando conteúdo WPF em um exemplo de janela Win32](http://go.microsoft.com/fwlink/?LinkID=160004).  
  
<a name="basic_procedure"></a>   
## <a name="the-basic-procedure"></a>O procedimento básico  
 Esta seção descreve o procedimento básico para host [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] conteúdo em um [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] janela. As outras seções explicam os detalhes de cada etapa.  
  
 A chave para hospedar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] conteúdo em um [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] janela é a <xref:System.Windows.Interop.HwndSource> classe. Essa classe encapsula o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] conteúdo em um [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] janela, permitindo que ele seja incorporado a sua [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] como uma janela filho. A abordagem a seguir combina o [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] e o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] em um único aplicativo.  
  
1.  Implementar seu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] conteúdo como uma classe gerenciada.  
  
2.  Implementar um aplicativo [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] com [!INCLUDE[TLA#tla_cppcli](../../../../includes/tlasharptla-cppcli-md.md)]. Se você estiver iniciando com um aplicativo existente e não gerenciado [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] código, você normalmente poderá habilitá-lo para chamar código gerenciado alterando as configurações de projeto para incluir o `/clr` sinalizador do compilador.  
  
3.  Defina o modelo de threading como STA (Single-Threaded Apartment).  
  
4.  Manipular o [WM_CREATE](http://msdn.microsoft.com/library/ms632619.aspx)notificação em seu procedimento de janela e faça o seguinte:  
  
    1.  Criar um novo <xref:System.Windows.Interop.HwndSource> objeto com a janela pai como seu `parent` parâmetro.  
  
    2.  Crie uma instância da sua classe de conteúdo do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
    3.  Atribuir uma referência para o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] objeto do conteúdo para o <xref:System.Windows.Interop.HwndSource.RootVisual%2A> propriedade do <xref:System.Windows.Interop.HwndSource>.  
  
    4.  Obtenha o HWND do conteúdo. O <xref:System.Windows.Interop.HwndSource.Handle%2A> propriedade o <xref:System.Windows.Interop.HwndSource> objeto contém o identificador de janela (HWND). Para obter um HWND que você possa usar na parte não gerenciada de seu aplicativo, transmita `Handle.ToPointer()` para um HWND.  
  
5.  Implemente uma classe gerenciada que contenha um campo estático para manter uma referência ao seu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] conteúdo. Essa classe permite que você obtenha uma referência para o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] conteúdo de sua [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] código.  
  
6.  Atribuir o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] conteúdo para o campo estático.  
  
7.  Receber notificações do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] conteúdo anexando um manipulador para um ou mais do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] eventos.  
  
8.  Se comunicar com o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] conteúdo usando a referência que você armazenou no campo estático para definir propriedades e assim por diante.  
  
> [!NOTE]
>  Você também pode usar [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] para implementar seu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] conteúdo. No entanto, você precisa compilá-lo separadamente como um [!INCLUDE[TLA#tla_dll](../../../../includes/tlasharptla-dll-md.md)] e referência de [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] de seu [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] aplicativo. O restante do procedimento é semelhante ao descrito acima.  
  
<a name="implementing_the_application"></a>   
## <a name="implementing-the-host-application"></a>Implementando o aplicativo host  
 Esta seção descreve como hospedar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] conteúdo básico [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] aplicativo. O conteúdo em si é implementado em [!INCLUDE[TLA#tla_cppcli](../../../../includes/tlasharptla-cppcli-md.md)] como uma classe gerenciada. A maior parte do tempo, é fácil [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] de programação. Os principais aspectos da implementação do conteúdo são discutidos em [implementando conteúdo WPF](#implementing_the_wpf_page).  
  
<a name="autoNestedSectionsOUTLINE1"></a>   
-   [O aplicativo básico](#the_basic_application)  
  
-   [Hospedando o conteúdo do WPF](#hosting_the_wpf_page)  
  
-   [Mantendo uma referência ao conteúdo do WPF](#holding_a_reference)  
  
-   [Comunicando com o conteúdo do WPF](#communicating_with_the_page)  
  
<a name="the_basic_application"></a>   
### <a name="the-basic-application"></a>O aplicativo básico  
 O ponto de partida para o aplicativo host foi criar um [!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)] modelo.  
  
1.  Abra [!INCLUDE[TLA2#tla_visualstu2005](../../../../includes/tla2sharptla-visualstu2005-md.md)]e selecione **novo projeto** do **arquivo** menu.  
  
2.  Selecione **Win32** da lista de [!INCLUDE[TLA2#tla_visualcpp](../../../../includes/tla2sharptla-visualcpp-md.md)] tipos de projeto. Se o idioma padrão não for [!INCLUDE[TLA2#tla_cpp](../../../../includes/tla2sharptla-cpp-md.md)], você encontrará esses tipos de projeto em **outras linguagens**.  
  
3.  Selecione um **projeto Win32** modelo, atribua um nome para o projeto e clique em **Okey** para iniciar o **Assistente de aplicativo Win32**.  
  
4.  Aceite as configurações padrão do assistente e clique em **concluir** para iniciar o projeto.  
  
 O modelo cria um basic [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] aplicativo, incluindo:  
  
-   Um ponto de entrada do aplicativo.  
  
-   Uma janela, com um procedimento de janela associado (WndProc).  
  
-   Um menu com **arquivo** e **ajuda** títulos. O **arquivo** menu tem uma **Exit** item que fecha o aplicativo. O **ajuda** menu tem uma **sobre** item que inicia uma caixa de diálogo simples.  
  
 Antes de começar a escrever código para hospedar o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] conteúdo, você precisa fazer duas modificações no modelo básico.  
  
 A primeira é compilar o projeto como um código gerenciado. Por padrão, o projeto é compilado como um código não gerenciado. No entanto, porque [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] é implementado no código gerenciado, o projeto deve ser compilado adequadamente.  
  
1.  Clique no nome do projeto em **Solution Explorer** e selecione **propriedades** no menu de contexto para iniciar o **páginas de propriedade** caixa de diálogo.  
  
2.  Selecione **propriedades de configuração** da exibição em árvore no painel esquerdo.  
  
3.  Selecione **Common Language Runtime** dar suporte a **padrões do projeto** lista no painel direito.  
  
4.  Selecione **suporte a Common Language Runtime (/ clr)** na caixa de listagem suspensa.  
  
> [!NOTE]
>  Esse sinalizador de compilação permite que você use um código gerenciado no aplicativo, mas o código não gerenciado continuará sendo compilado como antes.  
  
 O [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] usa o modelo de threading STA (Single-Threaded Apartment). Para funcionar corretamente com o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] código de conteúdo, você deve definir o modelo de threading do aplicativo para STA aplicando um atributo para o ponto de entrada.  
  
 [!code-cpp[Win32HostingWPFPage#WinMain](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#winmain)]  
  
<a name="hosting_the_wpf_page"></a>   
### <a name="hosting-the-wpf-content"></a>Hospedando o conteúdo do WPF  
 O [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] conteúdo é um aplicativo de entrada simples de endereço. Ele consiste em vários <xref:System.Windows.Controls.TextBox> controla se o nome de usuário, endereço e assim por diante. Também há dois <xref:System.Windows.Controls.Button> controles, **Okey** e **Cancelar**. Quando o usuário clica **Okey**, o botão <xref:System.Windows.Controls.Primitives.ButtonBase.Click> manipulador de eventos coleta dados do <xref:System.Windows.Controls.TextBox> controla, atribui a propriedades correspondentes e gera um evento personalizado, `OnButtonClicked`. Quando o usuário clica **Cancelar**, simplesmente dispara o manipulador `OnButtonClicked`. O objeto de argumento do evento para `OnButtonClicked` contém um campo booleano que indica qual botão foi clicado.  
  
 O código para hospedar o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] conteúdo é implementado em um manipulador para o [WM_CREATE](http://msdn.microsoft.com/library/ms632619.aspx) notificação na janela do host.  
  
 [!code-cpp[Win32HostingWPFPage#WMCreate](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#wmcreate)]  
  
 O `GetHwnd` método recebe informações de tamanho e posição mais pai identificador de janela e retorna o identificador de janela de hospedado [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] conteúdo.  
  
> [!NOTE]
>  Não é possível usar um `#using` diretiva para o `System::Windows::Interop` namespace. Isso cria uma colisão de nomes entre o <xref:System.Windows.Interop.MSG> em que o namespace e a estrutura MSG declarada em winuser. Em vez disso, use nomes totalmente qualificados para acessar o conteúdo desse namespace.  
  
 [!code-cpp[Win32HostingWPFPage#GetHwnd](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#gethwnd)]  
  
 Você não pode hospedar o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] conteúdo diretamente na sua janela de aplicativo. Em vez disso, crie primeiro um <xref:System.Windows.Interop.HwndSource> objeto para encapsular o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] conteúdo. Este objeto é basicamente uma janela projetada para hospedar um [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] conteúdo. Hospedar o <xref:System.Windows.Interop.HwndSource> objeto na janela pai criando-o como um filho de um [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] janela que faz parte do seu aplicativo. O <xref:System.Windows.Interop.HwndSource> parâmetros do construtor contêm basicamente as mesmas informações que você passaria para CreateWindow ao criar um [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] janela filho.  
  
 Depois que você cria uma instância do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] objeto do conteúdo. Nesse caso, o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] conteúdo é implementado como uma classe separada, `WPFPage`usando [!INCLUDE[TLA#tla_cppcli](../../../../includes/tlasharptla-cppcli-md.md)]. Você também pode implementar o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] conteúdo com [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. No entanto, para isso você precisa configurar um projeto separado e construir o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] conteúdo como um [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)]. Você pode adicionar uma referência ao [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] no seu projeto e usá-la para criar uma instância do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] conteúdo.  
  
 Exibir o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] conteúdo na sua janela filho atribuindo uma referência para o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] conteúdo para o <xref:System.Windows.Interop.HwndSource.RootVisual%2A> propriedade do <xref:System.Windows.Interop.HwndSource>.  
  
 A próxima linha de código anexa um manipulador de eventos, `WPFButtonClicked`, para o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] conteúdo `OnButtonClicked` eventos. Esse manipulador é chamado quando o usuário clica o **Okey** ou **Cancelar** botão. Consulte [communicating_with_the_WPF content](#communicating_with_the_page) para mais informações sobre este manipulador de eventos.  
  
 A linha final do código mostrado retorna o identificador de janela (HWND) que está associado com o <xref:System.Windows.Interop.HwndSource> objeto. Você pode usar este identificador de seu [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] código para enviar mensagens para a janela hospedada, embora o exemplo não fazê-lo. O <xref:System.Windows.Interop.HwndSource> objeto gera um evento cada vez que recebe uma mensagem. Para processar as mensagens, chame o <xref:System.Windows.Interop.HwndSource.AddHook%2A> método para anexar um manipulador de mensagens e, em seguida, processar as mensagens nesse manipulador.  
  
<a name="holding_a_reference"></a>   
### <a name="holding-a-reference-to-the-wpf-content"></a>Mantendo uma referência ao conteúdo do WPF  
 Para muitos aplicativos, você desejará se comunicar com o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] de conteúdo mais tarde. Por exemplo, você talvez queira modificar o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] propriedades de conteúdo, ou talvez tenha o <xref:System.Windows.Interop.HwndSource> host de objeto diferente [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] conteúdo. Para fazer isso, você precisa de uma referência para o <xref:System.Windows.Interop.HwndSource> objeto ou o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] conteúdo. O <xref:System.Windows.Interop.HwndSource> objeto e seus associados [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] conteúdo permanecer na memória até que você destrua seu identificador de janela. No entanto, a variável que você atribui para a <xref:System.Windows.Interop.HwndSource> objeto irá fora do escopo, assim como retorno do procedimento da janela. O modo habitual para lidar com esse problema com [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] aplicativos é usar uma variável global ou estática. Infelizmente, não é possível atribuir um objeto gerenciado a esses tipos de variáveis. Você pode atribuir um identificador de janela associado <xref:System.Windows.Interop.HwndSource> do objeto a uma variável global ou estática, mas que isto não fornece acesso ao objeto em si.  
  
 A solução mais simples para esse problema é implementar uma classe gerenciada que contém um conjunto de campos estáticos para manter referências a todos os objetos gerenciados aos quais você precisa ter acesso. O exemplo usa o `WPFPageHost` classe para manter uma referência para o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] conteúdo, mais os valores iniciais de um número de propriedades que podem ser alteradas posteriormente pelo usuário. Isso é definido no cabeçalho.  
  
 [!code-cpp[Win32HostingWPFPage#WPFPageHost](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.h#wpfpagehost)]  
  
 A última parte do `GetHwnd` função atribui valores para esses campos para uso posterior ao `myPage` ainda está no escopo.  
  
<a name="communicating_with_the_page"></a>   
### <a name="communicating-with-the-wpf-content"></a>Comunicando com o conteúdo do WPF  
 Há dois tipos de comunicação com o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] conteúdo. O aplicativo recebe informações do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] de conteúdo quando o usuário clica o **Okey** ou **Cancelar** botões. O aplicativo também tem um [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] que permite ao usuário alterar várias [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] propriedades, como o tamanho de fonte de cor ou padrão de plano de fundo de conteúdo.  
  
 Conforme mencionado acima, quando o usuário clica o botão de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] conteúdo gera um `OnButtonClicked` eventos. O aplicativo anexa um manipulador a esse evento para receber essas notificações. Se o **Okey** botão foi clicado, o manipulador obtém as informações do usuário a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] de conteúdo e o exibe em um conjunto de controles estáticos.  
  
 [!code-cpp[Win32HostingWPFPage#WPFButtonClicked](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#wpfbuttonclicked)]  
  
 O manipulador recebe um objeto de argumento de evento personalizado do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] conteúdo, `MyPageEventArgs`. O objeto `IsOK` está definida como `true` se o **Okey** botão foi clicado, e `false` se o **Cancelar** botão foi clicado.  
  
 Se o **Okey** botão foi clicado, o manipulador obtém uma referência para o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] conteúdo da classe de contêiner. Depois que ele coleta as informações do usuário que são mantidas pelo associado [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] conteúdo propriedades e usa controles estáticos para exibir as informações sobre a janela pai. Porque o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dados de conteúdo na forma de uma cadeia de caracteres gerenciada, ele deve ser empacotado para uso por um [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] controle. Se o **Cancelar** botão foi clicado, o manipulador limpa os dados dos controles estáticos.  
  
 O aplicativo [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] fornece um conjunto de botões de opção que permitem ao usuário modificar a cor de fundo de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] conteúdo e várias propriedades relacionadas a fonte. O exemplo a seguir é um trecho do procedimento de janela (WndProc) do aplicativo e sua manipulação de mensagens que define várias propriedades em diferentes mensagens, incluindo a cor da tela de fundo. As outras são semelhantes e não são mostradas. Consulte a amostra completa para obter detalhes e o contexto.  
  
 [!code-cpp[Win32HostingWPFPage#WMCommandToBG](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#wmcommandtobg)]  
  
 Para definir a cor de plano de fundo, obtenha uma referência para o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] conteúdo (`hostedPage`) de `WPFPageHost` e defina a propriedade de cor do plano de fundo para a cor apropriada. A amostra usa três opções de cores: a cor original, verde-claro e salmão-claro. A cor de plano de fundo original é armazenada como um campo estático no `WPFPageHost` classe. Para ver as outras duas, crie um novo <xref:System.Windows.Media.SolidColorBrush> de objeto e passar o construtor de um valor de cor estática do <xref:System.Windows.Media.Colors> objeto.  
  
<a name="implementing_the_wpf_page"></a>   
## <a name="implementing-the-wpf-page"></a>Implementando a página do WPF  
 Você pode hospedar e usar o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] conteúdo sem nenhum conhecimento da implementação real. Se o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] conteúdo tiver sido empacotado em um separado [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)], ele pode ter sido construído em qualquer [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] idioma. A seguir está uma breve explicação do [!INCLUDE[TLA#tla_cppcli](../../../../includes/tlasharptla-cppcli-md.md)] implementação que é usada no exemplo. Esta seção contém as subseções a seguir.  
  
<a name="autoNestedSectionsOUTLINE2"></a>   
-   [Layout](#page_layout)  
  
-   [Retornando os dados à janela do host](#returning_data_to_window)  
  
-   [Definindo as propriedades do WPF](#set_page_properties)  
  
<a name="page_layout"></a>   
### <a name="layout"></a>Layout  
 O [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elementos o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] conteúdo consistem em cinco <xref:System.Windows.Controls.TextBox> controla, com associado <xref:System.Windows.Controls.Label> controles: nome, endereço, cidade, estado e CEP. Também há dois <xref:System.Windows.Controls.Button> controles, **Okey** e **Cancelar**  
  
 O [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] conteúdo é implementado no `WPFPage` classe. Layout é tratado com um <xref:System.Windows.Controls.Grid> elemento de layout. A classe herda de <xref:System.Windows.Controls.Grid>, que efetivamente o torna o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elemento raiz de conteúdo.  
  
 O [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] conteúdo construtor usa necessária largura e altura e tamanhos de <xref:System.Windows.Controls.Grid> adequadamente. Em seguida, define o layout básico criando um conjunto de <xref:System.Windows.Controls.ColumnDefinition> e <xref:System.Windows.Controls.RowDefinition> objetos e adicioná-los para o <xref:System.Windows.Controls.Grid> objeto base <xref:System.Windows.Controls.Grid.ColumnDefinitions%2A> e <xref:System.Windows.Controls.Grid.RowDefinitions%2A> coleções, respectivamente. Isso define uma grade de cinco linhas e sete colunas, com as dimensões determinadas pelo conteúdo das células.  
  
 [!code-cpp[Win32HostingWPFPage#WPFPageCtorToGridDef](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagectortogriddef)]  
  
 Em seguida, o construtor adiciona o [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elementos para o <xref:System.Windows.Controls.Grid>. O primeiro elemento é o texto do título, que é um <xref:System.Windows.Controls.Label> controle centralizado na primeira linha da grade.  
  
 [!code-cpp[Win32HostingWPFPage#WPFPageCtorTitle](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagectortitle)]  
  
 A próxima linha contém o nome <xref:System.Windows.Controls.Label> controle e seus associados <xref:System.Windows.Controls.TextBox> controle. Como o mesmo código é usado para cada par rótulo/caixa de texto, ele é colocado em um par de métodos particulares e usado para todos os cinco pares de rótulo/caixa de texto. Os métodos de criam o controle e, em seguida, chamar o <xref:System.Windows.Controls.Grid> classe estática <xref:System.Windows.Controls.Grid.SetColumn%2A> e <xref:System.Windows.Controls.Grid.SetRow%2A> métodos para colocar os controles na célula apropriada. Depois que o controle é criado, o exemplo chama o <xref:System.Windows.Controls.UIElementCollection.Add%2A> método no <xref:System.Windows.Controls.Panel.Children%2A> propriedade o <xref:System.Windows.Controls.Grid> para adicionar o controle à grade. O código para adicionar os pares de rótulo/caixa de texto restantes é semelhante. Consulte o código de exemplo para obter detalhes.  
  
 [!code-cpp[Win32HostingWPFPage#WPFPageCtorName](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagectorname)]  
  
 A implementação dos dois métodos ocorre da seguinte forma:  
  
 [!code-cpp[Win32HostingWPFPage#WPFPageCreateHelpers](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagecreatehelpers)]  
  
 Finalmente, o exemplo adiciona o **Okey** e **Cancelar** botões e anexa um manipulador de eventos para seus <xref:System.Windows.Controls.Primitives.ButtonBase.Click> eventos.  
  
 [!code-cpp[Win32HostingWPFPage#WPFPageCtorButtonsEvents](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagectorbuttonsevents)]  
  
<a name="returning_data_to_window"></a>   
### <a name="returning-the-data-to-the-host-window"></a>Retornando os dados à janela do host  
 Quando qualquer botão é clicado, seu <xref:System.Windows.Controls.Primitives.ButtonBase.Click> é gerado. A janela do host simplesmente pode anexar manipuladores para esses eventos e obter os dados diretamente a partir de <xref:System.Windows.Controls.TextBox> controles. O exemplo usa uma abordagem um pouco menos direta. Trata o <xref:System.Windows.Controls.Primitives.ButtonBase.Click> dentro de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] de conteúdo e, em seguida, gera um evento personalizado `OnButtonClicked`, para notificar o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] conteúdo. Isso permite que o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] conteúdo fazer alguma validação de parâmetro antes de notificar o host. O manipulador obtém o texto do <xref:System.Windows.Controls.TextBox> controla e atribui a propriedades públicas, do qual o host pode recuperar as informações.  
  
 A declaração de evento, em WPFPage.h:  
  
 [!code-cpp[Win32HostingWPFPage#WPFPageEventDecl](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.h#wpfpageeventdecl)]  
  
 O <xref:System.Windows.Controls.Primitives.ButtonBase.Click> manipulador de eventos, em WPFPage. cpp:  
  
 [!code-cpp[Win32HostingWPFPage#WPFPageButtonClicked](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagebuttonclicked)]  
  
<a name="set_page_properties"></a>   
### <a name="setting-the-wpf-properties"></a>Definindo as propriedades do WPF  
 O [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] host permite ao usuário alterar várias [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] propriedades de conteúdo. Do [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] lado, é simplesmente uma questão de alterar as propriedades. A implementação de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] classe conteúdo é um pouco mais complicado, porque não há nenhuma propriedade global único que controla as fontes para todos os controles. Em vez disso, a propriedade apropriada de cada controle é alterada nos acessadores set das propriedades. O exemplo a seguir mostra o código para o `DefaultFontFamily` propriedade. Definindo a propriedade chama um método privado ou de conjuntos de <xref:System.Windows.Controls.Control.FontFamily%2A> propriedades para os vários controles.  
  
 Em WPFPage.h:  
  
 [!code-cpp[Win32HostingWPFPage#WPFPageFontFamilyProperty](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.h#wpfpagefontfamilyproperty)]  
  
 Em WPFPage.cpp:  
  
 [!code-cpp[Win32HostingWPFPage#WPFPageSetFontFamily](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagesetfontfamily)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Interop.HwndSource>  
 [Interoperação do WPF e do Win32](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md)
