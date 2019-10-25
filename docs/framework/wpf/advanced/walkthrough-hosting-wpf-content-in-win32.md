---
title: 'Instruções passo a passo: hospedando conteúdo do WPF em Win32'
ms.date: 03/30/2017
dev_langs:
- cpp
helpviewer_keywords:
- hosting WPF content in Win32 window [WPF]
ms.assetid: 38ce284a-4303-46dd-b699-c9365b22a7dc
ms.openlocfilehash: 5bc6e6d805d74bcf01044a16d94d6b3fc0ccf881
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/24/2019
ms.locfileid: "72846845"
---
# <a name="walkthrough-hosting-wpf-content-in-win32"></a>Instruções passo a passo: hospedando conteúdo do WPF em Win32
O [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fornece um ambiente sofisticado para criação de aplicativos. No entanto, quando você tem um investimento substancial em [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] código, pode ser mais eficiente adicionar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] funcionalidade ao seu aplicativo em vez de reescrever o código original. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fornece um mecanismo direto para hospedar conteúdo de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] em uma janela de [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)].  
  
 Este tutorial descreve como escrever um aplicativo de exemplo, [hospedando conteúdo do WPF em um exemplo de janela do Win32](https://go.microsoft.com/fwlink/?LinkID=160004), que hospeda [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] conteúdo em uma janela [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]. Você pode estender esse exemplo para hospedar qualquer janela de [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]. Como ele envolve a combinação de código gerenciado e não gerenciado, o aplicativo é escrito C++em/CLI.  

<a name="requirements"></a>   
## <a name="requirements"></a>Requisitos  
 Este tutorial pressupõe uma familiaridade básica com a programação [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] e [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]. Para obter uma introdução básica à programação de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], consulte [introdução](../getting-started/index.md). Para obter uma introdução à programação de [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)], você deve fazer referência a qualquer um dos vários livros sobre o assunto, em particular as *janelas de programação* de Charles Petzold.  
  
 Como o exemplo que acompanha este tutorial é implementado na C++/CLI, este tutorial pressupõe familiaridade com o uso do C++ para programar a API do Windows mais uma compreensão da programação de código gerenciado. A familiaridade C++com a/CLI é útil, mas não essencial.  
  
> [!NOTE]
> Este tutorial inclui vários exemplos de código da amostra associada. No entanto, para facilitar a leitura, não inclui o código de exemplo completo. Para obter o código de exemplo completo, consulte [hospedando conteúdo do WPF em um exemplo de janela do Win32](https://go.microsoft.com/fwlink/?LinkID=160004).  
  
<a name="basic_procedure"></a>   
## <a name="the-basic-procedure"></a>O procedimento básico  
 Esta seção descreve o procedimento básico usado para hospedar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] conteúdo em uma janela de [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]. As outras seções explicam os detalhes de cada etapa.  
  
 A chave para hospedar conteúdo de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] em uma janela de [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] é a classe <xref:System.Windows.Interop.HwndSource>. Essa classe encapsula o conteúdo de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] em uma janela de [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)], permitindo que ele seja incorporado ao seu [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] como uma janela filho. A abordagem a seguir combina o [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] e o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] em um único aplicativo.  
  
1. Implemente seu conteúdo de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] como uma classe gerenciada.  
  
2. Implementar um aplicativo do Windows C++com o/CLI. Se você estiver começando com um aplicativo existente e um C++ código não gerenciado, geralmente poderá habilitá-lo para chamar código gerenciado alterando as configurações do projeto para incluir o sinalizador do compilador`/clr`.  
  
3. Defina o modelo de threading como STA (Single-Threaded Apartment).  
  
4. Manipule a notificação [WM_CREATE](/windows/desktop/winmsg/wm-create)em seu procedimento de janela e faça o seguinte:  
  
    1. Crie um novo objeto <xref:System.Windows.Interop.HwndSource> com a janela pai como seu parâmetro `parent`.  
  
    2. Crie uma instância da sua classe de conteúdo do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
    3. Atribua uma referência ao objeto de conteúdo [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] à propriedade <xref:System.Windows.Interop.HwndSource.RootVisual%2A> da <xref:System.Windows.Interop.HwndSource>.  
  
    4. Obtenha o HWND do conteúdo. A propriedade <xref:System.Windows.Interop.HwndSource.Handle%2A> do objeto <xref:System.Windows.Interop.HwndSource> contém o identificador de janela (HWND). Para obter um HWND que você possa usar na parte não gerenciada de seu aplicativo, transmita `Handle.ToPointer()` para um HWND.  
  
5. Implemente uma classe gerenciada que contenha um campo estático para manter uma referência ao seu conteúdo de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Essa classe permite que você obtenha uma referência para o conteúdo de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] do seu código de [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)].  
  
6. Atribua o conteúdo de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ao campo estático.  
  
7. Receba notificações do conteúdo de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] anexando um manipulador a um ou mais dos eventos de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
8. Comunique-se com o conteúdo de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] usando a referência que você armazenou no campo estático para definir propriedades e assim por diante.  
  
> [!NOTE]
> Você também pode usar [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] para implementar seu conteúdo de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. No entanto, você precisará compilá-lo separadamente como uma DLL (biblioteca de vínculo dinâmico) e fazer referência a essa DLL do seu aplicativo [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]. O restante do procedimento é semelhante ao descrito acima.

<a name="implementing_the_application"></a>
## <a name="implementing-the-host-application"></a>Implementando o aplicativo host
 Esta seção descreve como hospedar conteúdo de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] em um aplicativo de [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] básico. O conteúdo em si é implementado C++em/CLI como uma classe gerenciada. Na maior parte, é simples [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] programação. Os principais aspectos da implementação de conteúdo são discutidos na [implementação do conteúdo do WPF](#implementing_the_wpf_page).

- [O aplicativo básico](#the_basic_application)

- [Hospedando o conteúdo do WPF](#hosting_the_wpf_page)

- [Mantendo uma referência ao conteúdo do WPF](#holding_a_reference)

- [Comunicando com o conteúdo do WPF](#communicating_with_the_page)

<a name="the_basic_application"></a>
### <a name="the-basic-application"></a>O aplicativo básico
 O ponto de partida para o aplicativo host era criar um modelo do Visual Studio 2005.

1. Abra o Visual Studio 2005 e selecione **novo projeto** no menu **arquivo** .

2. Selecione **Win32** na lista de tipos de C++ projeto Visual. Se o idioma padrão não C++for, você encontrará esses tipos de projeto em **outros idiomas**.

3. Selecione um modelo de **projeto do Win32** , atribua um nome ao projeto e clique em **OK** para iniciar o **Assistente de aplicativo Win32**.

4. Aceite as configurações padrão do assistente e clique em **concluir** para iniciar o projeto.

 O modelo cria um aplicativo [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] básico, incluindo:

- Um ponto de entrada do aplicativo.

- Uma janela, com um procedimento de janela associado (WndProc).

- Um menu com cabeçalhos de **arquivo** e de **ajuda** . O menu **arquivo** tem um item de **saída** que fecha o aplicativo. O menu **ajuda** tem um item **sobre** que inicia uma caixa de diálogo simples.

 Antes de começar a gravar o código para hospedar o conteúdo de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], você precisa fazer duas modificações no modelo básico.

 A primeira é compilar o projeto como um código gerenciado. Por padrão, o projeto é compilado como um código não gerenciado. No entanto, como [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] é implementado em código gerenciado, o projeto deve ser compilado de acordo.

1. Clique com o botão direito do mouse no nome do projeto em **Gerenciador de soluções** e selecione **Propriedades** no menu de contexto para iniciar a caixa de diálogo **páginas de propriedades** .

2. Selecione **Propriedades de configuração** no modo de exibição de árvore no painel esquerdo.

3. Selecione suporte a **Common Language Runtime** na lista **padrões do projeto** no painel direito.

4. Selecione **suporte a Common Language Runtime (/CLR)** na caixa de listagem suspensa.

> [!NOTE]
> Esse sinalizador de compilação permite que você use um código gerenciado no aplicativo, mas o código não gerenciado continuará sendo compilado como antes.

 O [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] usa o modelo de threading STA (Single-Threaded Apartment). Para funcionar corretamente com o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] código de conteúdo, você deve definir o modelo de Threading do aplicativo como STA aplicando um atributo ao ponto de entrada.

 [!code-cpp[Win32HostingWPFPage#WinMain](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#winmain)]

<a name="hosting_the_wpf_page"></a>
### <a name="hosting-the-wpf-content"></a>Hospedando o conteúdo do WPF
 O conteúdo de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] é um aplicativo de entrada de endereço simples. Ele consiste em vários controles de <xref:System.Windows.Controls.TextBox> para pegar o nome de usuário, o endereço e assim por diante. Também há dois controles de <xref:System.Windows.Controls.Button>, **OK** e **Cancelar**. Quando o usuário clica em **OK**, o manipulador de eventos de <xref:System.Windows.Controls.Primitives.ButtonBase.Click> do botão coleta os dados dos controles de <xref:System.Windows.Controls.TextBox>, atribui-os às propriedades correspondentes e gera um evento personalizado `OnButtonClicked`. Quando o usuário clica em **Cancelar**, o manipulador simplesmente gera `OnButtonClicked`. O objeto de argumento de evento para `OnButtonClicked` contém um campo booliano que indica qual botão foi clicado.

 O código para hospedar o conteúdo do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] é implementado em um manipulador para a notificação [WM_CREATE](/windows/desktop/winmsg/wm-create) na janela do host.

 [!code-cpp[Win32HostingWPFPage#WMCreate](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#wmcreate)]

 O método `GetHwnd` Obtém informações de tamanho e posição mais o identificador de janela pai e retorna o identificador de janela do conteúdo de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hospedado.

> [!NOTE]
> Você não pode usar uma diretiva `#using` para o namespace `System::Windows::Interop`. Isso cria uma colisão de nome entre a estrutura de <xref:System.Windows.Interop.MSG> nesse namespace e a estrutura MSG declarada em winuser. h. Em vez disso, use nomes totalmente qualificados para acessar o conteúdo desse namespace.

 [!code-cpp[Win32HostingWPFPage#GetHwnd](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#gethwnd)]

 Você não pode hospedar o conteúdo do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] diretamente na janela do aplicativo. Em vez disso, você primeiro cria um objeto <xref:System.Windows.Interop.HwndSource> para encapsular o conteúdo do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Esse objeto é basicamente uma janela projetada para hospedar um conteúdo de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Você hospeda o objeto <xref:System.Windows.Interop.HwndSource> na janela pai criando-o como um filho de uma janela [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] que faz parte do seu aplicativo. Os parâmetros do Construtor <xref:System.Windows.Interop.HwndSource> contêm muito as mesmas informações que você passaria para CreateWindow ao criar uma janela filho [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)].

 Em seguida, você cria uma instância do objeto de conteúdo de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Nesse caso, o conteúdo do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] é implementado como uma classe separada, `WPFPage`, usando C++/CLI. Você também pode implementar o conteúdo de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] com [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. No entanto, para fazer isso, você precisa configurar um projeto separado e criar o conteúdo de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] como uma DLL. Você pode adicionar uma referência a essa DLL ao seu projeto e usar essa referência para criar uma instância do conteúdo de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].

 Você exibe o conteúdo de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] em sua janela filho atribuindo uma referência ao conteúdo de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] à propriedade <xref:System.Windows.Interop.HwndSource.RootVisual%2A> do <xref:System.Windows.Interop.HwndSource>.

 A próxima linha de código anexa um manipulador de eventos, `WPFButtonClicked`, ao evento [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Content `OnButtonClicked`. Esse manipulador é chamado quando o usuário clica no botão **OK** ou **Cancelar** . Consulte [conteúdo do communicating_with_the_WPF](#communicating_with_the_page) para obter mais informações sobre esse manipulador de eventos.

 A linha final do código mostrado retorna o identificador de janela (HWND) associado ao objeto <xref:System.Windows.Interop.HwndSource>. Você pode usar esse identificador do seu código de [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] para enviar mensagens para a janela hospedada, embora o exemplo não faça isso. O objeto <xref:System.Windows.Interop.HwndSource> gera um evento toda vez que recebe uma mensagem. Para processar as mensagens, chame o método <xref:System.Windows.Interop.HwndSource.AddHook%2A> para anexar um manipulador de mensagens e, em seguida, processar as mensagens nesse manipulador.

<a name="holding_a_reference"></a>
### <a name="holding-a-reference-to-the-wpf-content"></a>Mantendo uma referência ao conteúdo do WPF
 Para muitos aplicativos, você desejará se comunicar com o conteúdo do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] mais tarde. Por exemplo, talvez você queira modificar as propriedades de conteúdo de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ou talvez o <xref:System.Windows.Interop.HwndSource> de objeto hospede [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] conteúdo diferente. Para fazer isso, você precisa de uma referência ao objeto <xref:System.Windows.Interop.HwndSource> ou ao conteúdo [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. O objeto <xref:System.Windows.Interop.HwndSource> e seu conteúdo [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] associado permanecem na memória até que você destrua o identificador de janela. No entanto, a variável que você atribui ao objeto <xref:System.Windows.Interop.HwndSource> será desativada assim que você retornar do procedimento de janela. A maneira personalizada de lidar com esse problema com [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] aplicativos é usar uma variável estática ou global. Infelizmente, não é possível atribuir um objeto gerenciado a esses tipos de variáveis. Você pode atribuir o identificador de janela associado a <xref:System.Windows.Interop.HwndSource> objeto a uma variável global ou estática, mas que não fornece acesso ao próprio objeto.

 A solução mais simples para esse problema é implementar uma classe gerenciada que contém um conjunto de campos estáticos para manter referências a todos os objetos gerenciados aos quais você precisa ter acesso. O exemplo usa a classe `WPFPageHost` para manter uma referência ao conteúdo de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], além dos valores iniciais de um número de suas propriedades que podem ser alteradas posteriormente pelo usuário. Isso é definido no cabeçalho.

 [!code-cpp[Win32HostingWPFPage#WPFPageHost](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.h#wpfpagehost)]

 A última parte da função `GetHwnd` atribui valores a esses campos para uso posterior enquanto `myPage` ainda está no escopo.

<a name="communicating_with_the_page"></a>
### <a name="communicating-with-the-wpf-content"></a>Comunicando com o conteúdo do WPF
 Há dois tipos de comunicação com o conteúdo de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. O aplicativo recebe informações do conteúdo de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] quando o usuário clica nos botões **OK** ou **Cancelar** . O aplicativo também tem um [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] que permite ao usuário alterar várias propriedades de conteúdo de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], como a cor do plano de fundo ou o tamanho da fonte padrão.

 Conforme mencionado acima, quando o usuário clica em um dos botões, o conteúdo do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] gera um evento de `OnButtonClicked`. O aplicativo anexa um manipulador a esse evento para receber essas notificações. Se o botão **OK** foi clicado, o manipulador obtém as informações do usuário do conteúdo [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] e a exibe em um conjunto de controles estáticos.

 [!code-cpp[Win32HostingWPFPage#WPFButtonClicked](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#wpfbuttonclicked)]

 O manipulador recebe um objeto de argumento de evento personalizado do conteúdo de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], `MyPageEventArgs`. A propriedade `IsOK` do objeto é definida como `true` se o botão **OK** foi clicado e `false` se o botão **Cancelar** foi clicado.

 Se o botão **OK** foi clicado, o manipulador obtém uma referência para o conteúdo de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] da classe de contêiner. Em seguida, ele coleta as informações do usuário mantidas pelas propriedades de conteúdo de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] associadas e usa os controles estáticos para exibir as informações na janela pai. Como os dados de conteúdo de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] estão na forma de uma cadeia de caracteres gerenciada, ele precisa ser empacotado para uso por um controle de [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]. Se o botão **Cancelar** tiver sido clicado, o manipulador limpará os dados dos controles estáticos.

 O [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] de aplicativos fornece um conjunto de botões de opção que permitem ao usuário modificar a cor do plano de fundo do conteúdo do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] e várias propriedades relacionadas à fonte. O exemplo a seguir é um trecho do procedimento de janela (WndProc) do aplicativo e sua manipulação de mensagens que define várias propriedades em diferentes mensagens, incluindo a cor da tela de fundo. As outras são semelhantes e não são mostradas. Consulte a amostra completa para obter detalhes e o contexto.

 [!code-cpp[Win32HostingWPFPage#WMCommandToBG](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#wmcommandtobg)]

 Para definir a cor do plano de fundo, obtenha uma referência para o conteúdo de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] (`hostedPage`) de `WPFPageHost` e defina a propriedade cor da fundo como a cor apropriada. A amostra usa três opções de cores: a cor original, verde-claro e salmão-claro. A cor original do plano de fundo é armazenada como um campo estático na classe `WPFPageHost`. Para definir os outros dois, você cria um novo objeto <xref:System.Windows.Media.SolidColorBrush> e passa o construtor de um valor de cores estáticas do objeto <xref:System.Windows.Media.Colors>.

<a name="implementing_the_wpf_page"></a>
## <a name="implementing-the-wpf-page"></a>Implementando a página do WPF
 Você pode hospedar e usar o conteúdo de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sem qualquer conhecimento da implementação real. Se o conteúdo de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tivesse sido empacotado em uma DLL separada, ele poderia ter sido compilado em qualquer linguagem de Common Language Runtime (CLR). Veja a seguir uma breve explicação da C++implementação da/CLI que é usada no exemplo. Esta seção contém as subseções a seguir.

- [Layout](#page_layout)

- [Retornando os dados à janela do host](#returning_data_to_window)

- [Definindo as propriedades do WPF](#set_page_properties)

<a name="page_layout"></a>
### <a name="layout"></a>Layout
 Os elementos de [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] no conteúdo de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] consistem em cinco controles de <xref:System.Windows.Controls.TextBox>, com controles <xref:System.Windows.Controls.Label> associados: nome, endereço, cidade, estado e CEP. Também há dois controles <xref:System.Windows.Controls.Button>, **OK** e **Cancelar**

 O conteúdo do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] é implementado na classe `WPFPage`. O layout é manipulado com um elemento de layout <xref:System.Windows.Controls.Grid>. A classe herda de <xref:System.Windows.Controls.Grid>, o que efetivamente o torna o elemento de raiz de conteúdo [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].

 O construtor de conteúdo de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Obtém a largura e a altura necessárias e dimensiona o <xref:System.Windows.Controls.Grid> de acordo. Em seguida, ele define o layout básico criando um conjunto de objetos <xref:System.Windows.Controls.ColumnDefinition> e <xref:System.Windows.Controls.RowDefinition> e adicionando-os à base do objeto <xref:System.Windows.Controls.Grid> <xref:System.Windows.Controls.Grid.ColumnDefinitions%2A> e às coleções de <xref:System.Windows.Controls.Grid.RowDefinitions%2A>, respectivamente. Isso define uma grade de cinco linhas e sete colunas, com as dimensões determinadas pelo conteúdo das células.

 [!code-cpp[Win32HostingWPFPage#WPFPageCtorToGridDef](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagectortogriddef)]

 Em seguida, o construtor adiciona os elementos de [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] ao <xref:System.Windows.Controls.Grid>. O primeiro elemento é o texto do título, que é um controle de <xref:System.Windows.Controls.Label> que é centralizado na primeira linha da grade.

 [!code-cpp[Win32HostingWPFPage#WPFPageCtorTitle](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagectortitle)]

 A próxima linha contém o nome <xref:System.Windows.Controls.Label> controle e seu controle de <xref:System.Windows.Controls.TextBox> associado. Como o mesmo código é usado para cada par rótulo/caixa de texto, ele é colocado em um par de métodos particulares e usado para todos os cinco pares de rótulo/caixa de texto. Os métodos criam o controle apropriado e chamam os métodos <xref:System.Windows.Controls.Grid.SetColumn%2A> estáticos de <xref:System.Windows.Controls.Grid> de classe e <xref:System.Windows.Controls.Grid.SetRow%2A> para posicionar os controles na célula apropriada. Depois que o controle é criado, o exemplo chama o método <xref:System.Windows.Controls.UIElementCollection.Add%2A> na propriedade <xref:System.Windows.Controls.Panel.Children%2A> do <xref:System.Windows.Controls.Grid> para adicionar o controle à grade. O código para adicionar os pares de rótulo/caixa de texto restantes é semelhante. Consulte o código de exemplo para obter detalhes.

 [!code-cpp[Win32HostingWPFPage#WPFPageCtorName](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagectorname)]

 A implementação dos dois métodos ocorre da seguinte forma:

 [!code-cpp[Win32HostingWPFPage#WPFPageCreateHelpers](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagecreatehelpers)]

 Por fim, o exemplo adiciona os botões **OK** e **Cancelar** e anexa um manipulador de eventos aos seus eventos de <xref:System.Windows.Controls.Primitives.ButtonBase.Click>.

 [!code-cpp[Win32HostingWPFPage#WPFPageCtorButtonsEvents](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagectorbuttonsevents)]

<a name="returning_data_to_window"></a>
### <a name="returning-the-data-to-the-host-window"></a>Retornando os dados à janela do host
 Quando um dos botões é clicado, seu evento de <xref:System.Windows.Controls.Primitives.ButtonBase.Click> é gerado. A janela do host pode simplesmente anexar manipuladores a esses eventos e obter os dados diretamente dos controles de <xref:System.Windows.Controls.TextBox>. O exemplo usa uma abordagem um pouco menos direta. Ele manipula o <xref:System.Windows.Controls.Primitives.ButtonBase.Click> dentro do conteúdo do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] e, em seguida, gera um evento personalizado `OnButtonClicked`para notificar o conteúdo do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Isso permite que o conteúdo do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] faça alguma validação de parâmetro antes de notificar o host. O manipulador obtém o texto dos controles de <xref:System.Windows.Controls.TextBox> e o atribui a propriedades públicas, das quais o host pode recuperar as informações.

 A declaração de evento, em WPFPage.h:

 [!code-cpp[Win32HostingWPFPage#WPFPageEventDecl](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.h#wpfpageeventdecl)]

 O manipulador de eventos <xref:System.Windows.Controls.Primitives.ButtonBase.Click>, em WPFPage. cpp:

 [!code-cpp[Win32HostingWPFPage#WPFPageButtonClicked](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagebuttonclicked)]

<a name="set_page_properties"></a>
### <a name="setting-the-wpf-properties"></a>Definindo as propriedades do WPF
 O host [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] permite que o usuário altere várias propriedades de conteúdo de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Do lado do [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)], é simplesmente uma questão de alterar as propriedades. A implementação na classe de conteúdo [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] é um pouco mais complicada, porque não há nenhuma propriedade global única que controle as fontes de todos os controles. Em vez disso, a propriedade apropriada de cada controle é alterada nos acessadores set das propriedades. O exemplo a seguir mostra o código para a propriedade `DefaultFontFamily`. A definição da propriedade chama um método privado que, por sua vez, define as propriedades <xref:System.Windows.Controls.Control.FontFamily%2A> para os vários controles.

 Em WPFPage.h:

 [!code-cpp[Win32HostingWPFPage#WPFPageFontFamilyProperty](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.h#wpfpagefontfamilyproperty)]

 Em WPFPage.cpp:

 [!code-cpp[Win32HostingWPFPage#WPFPageSetFontFamily](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagesetfontfamily)]

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Interop.HwndSource>
- [Interoperação Win32 e WPF](wpf-and-win32-interoperation.md)
