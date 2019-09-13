---
title: 'Passo a passo: hospedar conteúdo do WPF no Win32'
ms.date: 03/30/2017
dev_langs:
- cpp
helpviewer_keywords:
- hosting WPF content in Win32 window [WPF]
ms.assetid: 38ce284a-4303-46dd-b699-c9365b22a7dc
ms.openlocfilehash: 3433819761c19b616a7c9c19fe52e250b0f028dc
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70929186"
---
# <a name="walkthrough-hosting-wpf-content-in-win32"></a>Passo a passo: hospedar conteúdo do WPF no Win32
O [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fornece um ambiente avançado para a criação de aplicativos. No entanto, quando você tem um investimento [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] substancial em código, pode ser mais eficiente adicionar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] funcionalidade ao seu aplicativo em vez de reescrever o código original. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]fornece um mecanismo direto para hospedar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] conteúdo em uma [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] janela.  
  
 Este tutorial descreve como escrever um aplicativo de exemplo, [hospedando conteúdo do WPF em um exemplo de janela do Win32](https://go.microsoft.com/fwlink/?LinkID=160004), que [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] hospeda [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] o conteúdo em uma janela. Você pode estender esse exemplo para hospedar qualquer [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] janela. Como ele envolve a combinação de código gerenciado e não gerenciado, o aplicativo é escrito C++em/CLI.  

<a name="requirements"></a>   
## <a name="requirements"></a>Requisitos  
 Este tutorial pressupõe uma familiaridade básica com ambos [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] e [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] programação. Para obter uma introdução básica [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] à programação, consulte [introdução](../getting-started/index.md). Para obter uma introdução [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] à programação, você deve fazer referência a qualquer um dos vários livros sobre o assunto, em particular as *janelas de programação* de Charles Petzold.  
  
 Como o exemplo que acompanha este tutorial é implementado na C++/CLI, este tutorial pressupõe familiaridade com o uso do C++ para programar a API do Windows mais uma compreensão da programação de código gerenciado. A familiaridade C++com a/CLI é útil, mas não essencial.  
  
> [!NOTE]
> Este tutorial inclui vários exemplos de código da amostra associada. No entanto, para facilitar a leitura, não inclui o código de exemplo completo. Para obter o código de exemplo completo, consulte [hospedando conteúdo do WPF em um exemplo de janela do Win32](https://go.microsoft.com/fwlink/?LinkID=160004).  
  
<a name="basic_procedure"></a>   
## <a name="the-basic-procedure"></a>O procedimento básico  
 Esta seção descreve o procedimento básico que você usa para hospedar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] conteúdo em uma [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] janela. As outras seções explicam os detalhes de cada etapa.  
  
 A chave para hospedar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] o conteúdo em [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] uma janela é <xref:System.Windows.Interop.HwndSource> a classe. Essa classe encapsula o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] conteúdo em uma [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] janela, permitindo que ele seja incorporado à sua [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] janela como filho. A abordagem a seguir combina o [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] e o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] em um único aplicativo.  
  
1. Implemente [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] seu conteúdo como uma classe gerenciada.  
  
2. Implementar um aplicativo do Windows C++com o/CLI. Se você estiver começando com um aplicativo existente e um C++ código não gerenciado, você geralmente pode habilitá-lo para chamar código gerenciado alterando as configurações do projeto `/clr` para incluir o sinalizador do compilador.  
  
3. Defina o modelo de threading como STA (Single-Threaded Apartment).  
  
4. Manipule a notificação [WM_CREATE](/windows/desktop/winmsg/wm-create)em seu procedimento de janela e faça o seguinte:  
  
    1. Crie um novo <xref:System.Windows.Interop.HwndSource> objeto com a janela pai como seu `parent` parâmetro.  
  
    2. Crie uma instância da sua classe de conteúdo do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
    3. Atribua uma referência ao [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] objeto de conteúdo <xref:System.Windows.Interop.HwndSource.RootVisual%2A> à propriedade do <xref:System.Windows.Interop.HwndSource>.  
  
    4. Obtenha o HWND do conteúdo. A <xref:System.Windows.Interop.HwndSource.Handle%2A> propriedade<xref:System.Windows.Interop.HwndSource> do objeto contém o identificador de janela (HWND). Para obter um HWND que você possa usar na parte não gerenciada de seu aplicativo, transmita `Handle.ToPointer()` para um HWND.  
  
5. Implemente uma classe gerenciada que contenha um campo estático para manter uma [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] referência ao seu conteúdo. Essa classe permite que você obtenha uma referência ao [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] conteúdo do seu [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] código.  
  
6. Atribua o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] conteúdo ao campo estático.  
  
7. Receba notificações do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] conteúdo anexando um manipulador a um ou mais [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dos eventos.  
  
8. Comunique-se [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] com o conteúdo usando a referência que você armazenou no campo estático para definir propriedades e assim por diante.  
  
> [!NOTE]
> Você também pode usar [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] o para implementar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] seu conteúdo. No entanto, você precisará compilá-lo separadamente como uma dll (biblioteca de vínculo dinâmico) e fazer referência a [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] essa DLL do seu aplicativo. O restante do procedimento é semelhante ao descrito acima.

<a name="implementing_the_application"></a>
## <a name="implementing-the-host-application"></a>Implementando o aplicativo host
 Esta seção descreve como hospedar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] conteúdo em um aplicativo básico. [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] O conteúdo em si é implementado C++em/CLI como uma classe gerenciada. Na maior parte, é uma programação direta [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] . Os principais aspectos da implementação de conteúdo são discutidos na [implementação do conteúdo do WPF](#implementing_the_wpf_page).

- [O aplicativo básico](#the_basic_application)

- [Hospedando o conteúdo do WPF](#hosting_the_wpf_page)

- [Mantendo uma referência ao conteúdo do WPF](#holding_a_reference)

- [Comunicando com o conteúdo do WPF](#communicating_with_the_page)

<a name="the_basic_application"></a>
### <a name="the-basic-application"></a>O aplicativo básico
 O ponto de partida para o aplicativo host era criar um modelo do Visual Studio 2005.

1. Abra o Visual Studio 2005 e selecione **novo projeto** no menu **arquivo** .

2. Selecione **Win32** na lista de tipos [!INCLUDE[TLA2#tla_visualcpp](../../../../includes/tla2sharptla-visualcpp-md.md)] de projeto. Se o idioma padrão não C++for, você encontrará esses tipos de projeto em **outros idiomas**.

3. Selecione um modelo de **projeto do Win32** , atribua um nome ao projeto e clique em **OK** para iniciar o **Assistente de aplicativo Win32**.

4. Aceite as configurações padrão do assistente e clique em **concluir** para iniciar o projeto.

 O modelo cria um aplicativo [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] básico, incluindo:

- Um ponto de entrada do aplicativo.

- Uma janela, com um procedimento de janela associado (WndProc).

- Um menu com cabeçalhos de **arquivo** e de **ajuda** . O menu **arquivo** tem um item de **saída** que fecha o aplicativo. O menu **ajuda** tem um item **sobre** que inicia uma caixa de diálogo simples.

 Antes de começar a gravar o código para [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hospedar o conteúdo, você precisa fazer duas modificações no modelo básico.

 A primeira é compilar o projeto como um código gerenciado. Por padrão, o projeto é compilado como um código não gerenciado. No entanto [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] , como o é implementado em código gerenciado, o projeto deve ser compilado de acordo.

1. Clique com o botão direito do mouse no nome do projeto em **Gerenciador de soluções** e selecione **Propriedades** no menu de contexto para iniciar a caixa de diálogo **páginas de propriedades** .

2. Selecione **Propriedades de configuração** no modo de exibição de árvore no painel esquerdo.

3. Selecione suporte a **Common Language Runtime** na lista **padrões do projeto** no painel direito.

4. Selecione **suporte a Common Language Runtime (/CLR)** na caixa de listagem suspensa.

> [!NOTE]
> Esse sinalizador de compilação permite que você use um código gerenciado no aplicativo, mas o código não gerenciado continuará sendo compilado como antes.

 O [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] usa o modelo de threading STA (Single-Threaded Apartment). Para funcionar corretamente com o código de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] conteúdo, você deve definir o modelo de Threading do aplicativo como STA aplicando um atributo ao ponto de entrada.

 [!code-cpp[Win32HostingWPFPage#WinMain](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#winmain)]

<a name="hosting_the_wpf_page"></a>
### <a name="hosting-the-wpf-content"></a>Hospedando o conteúdo do WPF
 O [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] conteúdo é um aplicativo de entrada de endereço simples. Ele consiste em vários <xref:System.Windows.Controls.TextBox> controles para pegar o nome de usuário, o endereço e assim por diante. Há também dois <xref:System.Windows.Controls.Button> controles, **OK** e **Cancelar**. Quando o usuário clica em **OK**, o manipulador <xref:System.Windows.Controls.Primitives.ButtonBase.Click> de eventos do botão coleta <xref:System.Windows.Controls.TextBox> os dados dos controles, atribui-os às propriedades correspondentes e gera um evento personalizado, `OnButtonClicked`. Quando o usuário clica em **Cancelar**, o manipulador simplesmente `OnButtonClicked`gera. O objeto de argumento de `OnButtonClicked` evento para contém um campo booliano que indica qual botão foi clicado.

 O código para hospedar o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] conteúdo é implementado em um manipulador para a notificação [WM_CREATE](/windows/desktop/winmsg/wm-create) na janela do host.

 [!code-cpp[Win32HostingWPFPage#WMCreate](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#wmcreate)]

 O `GetHwnd` método usa informações de tamanho e de posição mais o identificador de janela pai e retorna o identificador de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] janela do conteúdo hospedado.

> [!NOTE]
> Você não pode usar `#using` uma diretiva para `System::Windows::Interop` o namespace. Isso cria uma colisão de nome entre a <xref:System.Windows.Interop.MSG> estrutura nesse namespace e a estrutura de MSG declarada em winuser. h. Em vez disso, use nomes totalmente qualificados para acessar o conteúdo desse namespace.

 [!code-cpp[Win32HostingWPFPage#GetHwnd](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#gethwnd)]

 Você não pode hospedar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] o conteúdo diretamente na janela do aplicativo. Em vez disso, você primeiro <xref:System.Windows.Interop.HwndSource> cria um objeto para [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] encapsular o conteúdo. Esse objeto é basicamente uma janela projetada para hospedar um [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] conteúdo. Você hospeda o <xref:System.Windows.Interop.HwndSource> objeto na janela pai criando-o como um filho de uma [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] janela que faz parte do seu aplicativo. Os <xref:System.Windows.Interop.HwndSource> parâmetros do Construtor contêm muito as mesmas informações que você passaria para CreateWindow ao criar uma [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] janela filho.

 Em seguida, você cria uma instância [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] do objeto de conteúdo. Nesse caso, o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] conteúdo é implementado como uma classe separada, `WPFPage`usando/CLI. C++ Você também pode implementar o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] conteúdo com [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. No entanto, para fazer isso, você precisa configurar um projeto separado e criar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] o conteúdo como uma dll. Você pode adicionar uma referência a essa dll ao seu projeto e usar essa referência para criar uma instância do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] conteúdo.

 Você exibe o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] conteúdo em sua janela filho atribuindo uma referência [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ao conteúdo <xref:System.Windows.Interop.HwndSource>para a <xref:System.Windows.Interop.HwndSource.RootVisual%2A> Propriedade do.

 A próxima linha de código anexa um manipulador de eventos, `WPFButtonClicked`ao evento de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] conteúdo `OnButtonClicked` . Esse manipulador é chamado quando o usuário clica no botão **OK** ou **Cancelar** . Consulte [conteúdo do communicating_with_the_WPF](#communicating_with_the_page) para obter mais informações sobre esse manipulador de eventos.

 A linha final do código mostrado retorna o identificador de janela (HWND) associado <xref:System.Windows.Interop.HwndSource> ao objeto. Você pode usar esse identificador do seu [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] código para enviar mensagens para a janela hospedada, embora o exemplo não faça isso. O <xref:System.Windows.Interop.HwndSource> objeto gera um evento toda vez que recebe uma mensagem. Para processar as mensagens, chame o <xref:System.Windows.Interop.HwndSource.AddHook%2A> método para anexar um manipulador de mensagens e, em seguida, processe as mensagens nesse manipulador.

<a name="holding_a_reference"></a>
### <a name="holding-a-reference-to-the-wpf-content"></a>Mantendo uma referência ao conteúdo do WPF
 Para muitos aplicativos, você deverá se comunicar com o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] conteúdo posteriormente. Por exemplo, talvez você queira modificar as propriedades [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] de conteúdo ou talvez o <xref:System.Windows.Interop.HwndSource> objeto hospede conteúdo diferente [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] . Para fazer isso, você precisa de uma referência ao <xref:System.Windows.Interop.HwndSource> objeto ou ao [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] conteúdo. O <xref:System.Windows.Interop.HwndSource> objeto e seu conteúdo [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] associado permanecem na memória até que você destrua o identificador de janela. No entanto, a variável que você <xref:System.Windows.Interop.HwndSource> atribui ao objeto sai do escopo assim que você retorna do procedimento de janela. A maneira personalizada de lidar com esse problema com [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] os aplicativos é usar uma variável estática ou global. Infelizmente, não é possível atribuir um objeto gerenciado a esses tipos de variáveis. Você pode atribuir o identificador de janela associado <xref:System.Windows.Interop.HwndSource> ao objeto a uma variável global ou estática, mas que não fornece acesso ao próprio objeto.

 A solução mais simples para esse problema é implementar uma classe gerenciada que contém um conjunto de campos estáticos para manter referências a todos os objetos gerenciados aos quais você precisa ter acesso. O exemplo usa a `WPFPageHost` classe para manter uma referência [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ao conteúdo, além dos valores iniciais de um número de suas propriedades que podem ser alteradas posteriormente pelo usuário. Isso é definido no cabeçalho.

 [!code-cpp[Win32HostingWPFPage#WPFPageHost](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.h#wpfpagehost)]

 A última parte da `GetHwnd` função atribui valores a esses campos para uso posterior enquanto `myPage` ainda está no escopo.

<a name="communicating_with_the_page"></a>
### <a name="communicating-with-the-wpf-content"></a>Comunicando com o conteúdo do WPF
 Há dois tipos de comunicação com o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] conteúdo. O aplicativo recebe informações do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] conteúdo quando o usuário clica nos botões **OK** ou **Cancelar** . O aplicativo também tem um [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] que permite ao usuário alterar várias [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Propriedades de conteúdo, como a cor do plano de fundo ou o tamanho da fonte padrão.

 Conforme mencionado acima, quando o usuário clica em um dos [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] botões, o `OnButtonClicked` conteúdo gera um evento. O aplicativo anexa um manipulador a esse evento para receber essas notificações. Se o botão **OK** tiver sido clicado, o manipulador obterá as informações [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] do usuário do conteúdo e as exibirá em um conjunto de controles estáticos.

 [!code-cpp[Win32HostingWPFPage#WPFButtonClicked](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#wpfbuttonclicked)]

 O manipulador recebe um objeto de argumento de evento personalizado [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] do conteúdo `MyPageEventArgs`,. A propriedade do `IsOK` objeto é definida como `true` se o botão **OK** fosse clicado e `false` se o botão **Cancelar** foi clicado.

 Se o botão **OK** foi clicado, o manipulador obtém uma referência ao [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] conteúdo da classe de contêiner. Em seguida, ele coleta as informações do usuário mantidas pelas propriedades [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] de conteúdo associadas e usa os controles estáticos para exibir as informações na janela pai. Como os [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dados de conteúdo estão na forma de uma cadeia de caracteres gerenciada, ele precisa ser empacotado para uso [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] por um controle. Se o botão **Cancelar** tiver sido clicado, o manipulador limpará os dados dos controles estáticos.

 O aplicativo [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] fornece um conjunto de botões de opção que permitem ao usuário modificar a cor [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] do plano de fundo do conteúdo e várias propriedades relacionadas à fonte. O exemplo a seguir é um trecho do procedimento de janela (WndProc) do aplicativo e sua manipulação de mensagens que define várias propriedades em diferentes mensagens, incluindo a cor da tela de fundo. As outras são semelhantes e não são mostradas. Consulte a amostra completa para obter detalhes e o contexto.

 [!code-cpp[Win32HostingWPFPage#WMCommandToBG](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#wmcommandtobg)]

 Para definir a cor do plano de fundo, obtenha uma [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] referência ao`hostedPage`conteúdo ( `WPFPageHost` ) de e defina a propriedade cor da fundo como a cor apropriada. A amostra usa três opções de cores: a cor original, verde-claro e salmão-claro. A cor original do plano de fundo é armazenada como um `WPFPageHost` campo estático na classe. Para definir os outros dois, você cria um novo <xref:System.Windows.Media.SolidColorBrush> objeto e passa o construtor de um valor <xref:System.Windows.Media.Colors> de cores estáticos do objeto.

<a name="implementing_the_wpf_page"></a>
## <a name="implementing-the-wpf-page"></a>Implementando a página do WPF
 Você pode hospedar e usar o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] conteúdo sem qualquer conhecimento da implementação real. Se o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] conteúdo tiver sido empacotado em uma DLL separada, ele poderia ter sido compilado em qualquer linguagem de Common Language Runtime (CLR). Veja a seguir uma breve explicação da C++implementação da/CLI que é usada no exemplo. Esta seção contém as subseções a seguir.

- [Layout](#page_layout)

- [Retornando os dados à janela do host](#returning_data_to_window)

- [Definindo as propriedades do WPF](#set_page_properties)

<a name="page_layout"></a>
### <a name="layout"></a>Layout
 Os [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elementos <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.Label> no conteúdo consistem em cinco controles, com controles associados: [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Nome, endereço, cidade, estado e CEP. Há também dois <xref:System.Windows.Controls.Button> controles, **OK** e **Cancelar**

 O [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] conteúdo é implementado `WPFPage` na classe. O layout é manipulado <xref:System.Windows.Controls.Grid> com um elemento layout. A classe é herdada de <xref:System.Windows.Controls.Grid>, o que efetivamente a transforma no elemento raiz de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] conteúdo.

 O [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Construtor de conteúdo Obtém a largura e a altura necessárias e dimensiona <xref:System.Windows.Controls.Grid> o de acordo. Em seguida, ele define o layout básico criando um conjunto <xref:System.Windows.Controls.ColumnDefinition> de <xref:System.Windows.Controls.RowDefinition> objetos e e adicionando-os <xref:System.Windows.Controls.Grid> à base <xref:System.Windows.Controls.Grid.ColumnDefinitions%2A> do <xref:System.Windows.Controls.Grid.RowDefinitions%2A> objeto e às coleções, respectivamente. Isso define uma grade de cinco linhas e sete colunas, com as dimensões determinadas pelo conteúdo das células.

 [!code-cpp[Win32HostingWPFPage#WPFPageCtorToGridDef](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagectortogriddef)]

 Em seguida, o construtor adiciona [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] os elementos <xref:System.Windows.Controls.Grid>ao. O primeiro elemento é o texto do título, que é <xref:System.Windows.Controls.Label> um controle que é centralizado na primeira linha da grade.

 [!code-cpp[Win32HostingWPFPage#WPFPageCtorTitle](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagectortitle)]

 A próxima linha contém o controle <xref:System.Windows.Controls.Label> de nome e seu <xref:System.Windows.Controls.TextBox> controle associado. Como o mesmo código é usado para cada par rótulo/caixa de texto, ele é colocado em um par de métodos particulares e usado para todos os cinco pares de rótulo/caixa de texto. Os métodos criam o controle apropriado e chamam a classe <xref:System.Windows.Controls.Grid> static <xref:System.Windows.Controls.Grid.SetColumn%2A> e <xref:System.Windows.Controls.Grid.SetRow%2A> os métodos para posicionar os controles na célula apropriada. Depois que o controle é criado, o exemplo chama <xref:System.Windows.Controls.UIElementCollection.Add%2A> o método <xref:System.Windows.Controls.Panel.Children%2A> na Propriedade do <xref:System.Windows.Controls.Grid> para adicionar o controle à grade. O código para adicionar os pares de rótulo/caixa de texto restantes é semelhante. Consulte o código de exemplo para obter detalhes.

 [!code-cpp[Win32HostingWPFPage#WPFPageCtorName](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagectorname)]

 A implementação dos dois métodos ocorre da seguinte forma:

 [!code-cpp[Win32HostingWPFPage#WPFPageCreateHelpers](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagecreatehelpers)]

 Por fim, o exemplo adiciona os botões **OK** e **Cancelar** e anexa um manipulador de eventos aos <xref:System.Windows.Controls.Primitives.ButtonBase.Click> seus eventos.

 [!code-cpp[Win32HostingWPFPage#WPFPageCtorButtonsEvents](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagectorbuttonsevents)]

<a name="returning_data_to_window"></a>
### <a name="returning-the-data-to-the-host-window"></a>Retornando os dados à janela do host
 Quando um dos botões é clicado <xref:System.Windows.Controls.Primitives.ButtonBase.Click> , seu evento é gerado. A janela do host pode simplesmente anexar manipuladores a esses eventos e obter os dados diretamente dos <xref:System.Windows.Controls.TextBox> controles. O exemplo usa uma abordagem um pouco menos direta. Ele manipula o <xref:System.Windows.Controls.Primitives.ButtonBase.Click> dentro do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] conteúdo e, em seguida, gera um `OnButtonClicked`evento personalizado para notificar o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] conteúdo. Isso permite que [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] o conteúdo faça alguma validação de parâmetro antes de notificar o host. O manipulador obtém o texto dos <xref:System.Windows.Controls.TextBox> controles e o atribui a propriedades públicas, das quais o host pode recuperar as informações.

 A declaração de evento, em WPFPage.h:

 [!code-cpp[Win32HostingWPFPage#WPFPageEventDecl](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.h#wpfpageeventdecl)]

 O <xref:System.Windows.Controls.Primitives.ButtonBase.Click> manipulador de eventos, em WPFPage. cpp:

 [!code-cpp[Win32HostingWPFPage#WPFPageButtonClicked](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagebuttonclicked)]

<a name="set_page_properties"></a>
### <a name="setting-the-wpf-properties"></a>Definindo as propriedades do WPF
 O [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] host permite que o usuário altere várias [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Propriedades de conteúdo. [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] Do lado, é simplesmente uma questão de alterar as propriedades. A implementação na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] classe Content é um pouco mais complicada, porque não há nenhuma propriedade global única que controle as fontes de todos os controles. Em vez disso, a propriedade apropriada de cada controle é alterada nos acessadores set das propriedades. O exemplo a seguir mostra o código para `DefaultFontFamily` a propriedade. A definição da propriedade chama um método privado que, por sua <xref:System.Windows.Controls.Control.FontFamily%2A> vez, define as propriedades para os vários controles.

 Em WPFPage.h:

 [!code-cpp[Win32HostingWPFPage#WPFPageFontFamilyProperty](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.h#wpfpagefontfamilyproperty)]

 Em WPFPage.cpp:

 [!code-cpp[Win32HostingWPFPage#WPFPageSetFontFamily](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagesetfontfamily)]

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Interop.HwndSource>
- [Interoperação do WPF e do Win32](wpf-and-win32-interoperation.md)
