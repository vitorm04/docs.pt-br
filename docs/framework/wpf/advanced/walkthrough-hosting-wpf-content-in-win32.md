---
title: Hospedar conteúdo WPF no Win32
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- cpp
helpviewer_keywords:
- hosting WPF content in Win32 window [WPF]
ms.assetid: 38ce284a-4303-46dd-b699-c9365b22a7dc
ms.openlocfilehash: 8a5d556abf49c9c1f49e7853e752ebc5248d1101
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186062"
---
# <a name="walkthrough-hosting-wpf-content-in-win32"></a>Instruções passo a passo: hospedando conteúdo do WPF em Win32
O [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fornece um ambiente avançado para a criação de aplicativos. No entanto, quando você tem um investimento substancial no código [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Win32, pode ser mais eficaz adicionar funcionalidade ao seu aplicativo em vez de reescrever seu código original. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]fornece um mecanismo [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] simples para hospedar conteúdo em uma janela Win32.  
  
 Este tutorial descreve como escrever um aplicativo de exemplo, [hospedando conteúdo WPF em uma amostra de janela Win32](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/Win32HostingWPFPage), que hospeda [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] conteúdo em uma janela Win32. Você pode estender esta amostra para hospedar qualquer janela Win32. Como envolve misturar código gerenciado e não gerenciado, o aplicativo é escrito em C++/CLI.  

<a name="requirements"></a>
## <a name="requirements"></a>Requisitos  
 Este tutorial assume uma familiaridade [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] básica com a programação do Win32. Para uma introdução básica à [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] programação, consulte Getting [Started](../getting-started/index.md). Para uma introdução à programação Win32, você deve referenciar qualquer um dos inúmeros livros sobre o assunto, em particular *O Windows de Programação* por Charles Petzold.  
  
 Como a amostra que acompanha este tutorial é implementada em C++/CLI, este tutorial assume familiaridade com o uso do C++ para programar a API do Windows, além de um entendimento da programação de código gerenciada. A familiaridade com c++/CLI é útil, mas não essencial.  
  
> [!NOTE]
> Este tutorial inclui vários exemplos de código da amostra associada. No entanto, para facilitar a leitura, não inclui o código de exemplo completo. Para obter o código de amostra completo, consulte [Hosting WPF Content em uma amostra de janela Win32](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/Win32HostingWPFPage).  
  
<a name="basic_procedure"></a>
## <a name="the-basic-procedure"></a>O procedimento básico  
 Esta seção descreve o procedimento [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] básico que você usa para hospedar conteúdo em uma janela Win32. As outras seções explicam os detalhes de cada etapa.  
  
 A chave [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] para hospedar conteúdo em uma <xref:System.Windows.Interop.HwndSource> janela Win32 é a classe. Esta classe envolve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] o conteúdo em uma janela Win32, [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] permitindo que ele seja incorporado em sua janela como criança. A abordagem a seguir combina [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] o Win32 e em um único aplicativo.  
  
1. Implemente [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] seu conteúdo como uma classe gerenciada.  
  
2. Implementar um aplicativo do Windows com C++/CLI. Se você estiver começando com um aplicativo existente e um código C++ não gerenciado, você geralmente pode `/clr` habilitá-lo para chamar código gerenciado alterando as configurações do projeto para incluir o sinalizador do compilador.  
  
3. Defina o modelo de threading como STA (Single-Threaded Apartment).  
  
4. Manuseie a notificação [WM_CREATE](/windows/desktop/winmsg/wm-create)no procedimento da janela e faça o seguinte:  
  
    1. Crie um <xref:System.Windows.Interop.HwndSource> novo objeto com `parent` a janela pai como parâmetro.  
  
    2. Crie uma instância da sua classe de conteúdo do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
    3. Atribuir uma referência [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ao objeto <xref:System.Windows.Interop.HwndSource.RootVisual%2A> de conteúdo <xref:System.Windows.Interop.HwndSource>à propriedade do .  
  
    4. Obtenha o HWND do conteúdo. A <xref:System.Windows.Interop.HwndSource.Handle%2A> propriedade <xref:System.Windows.Interop.HwndSource> do objeto contém a alça da janela (HWND). Para obter um HWND que você possa usar na parte não gerenciada de seu aplicativo, transmita `Handle.ToPointer()` para um HWND.  
  
5. Implemente uma classe gerenciada que contenha um [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] campo estático para manter uma referência ao seu conteúdo. Esta classe permite que você [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obtenha uma referência ao conteúdo do seu código Win32.  
  
6. Atribuir o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] conteúdo ao campo estático.  
  
7. Receba notificações [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] do conteúdo anexando um manipulador [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a um ou mais dos eventos.  
  
8. Comunique-se com o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] conteúdo usando a referência armazenada no campo estático para definir propriedades, e assim por diante.  
  
> [!NOTE]
> Você também [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] pode usar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] para implementar seu conteúdo. No entanto, você terá que compilá-lo separadamente como uma biblioteca de link dinâmico (DLL) e referenciar essa DLL do seu aplicativo Win32. O restante do procedimento é semelhante ao descrito acima.

<a name="implementing_the_application"></a>
## <a name="implementing-the-host-application"></a>Implementando o aplicativo host
 Esta seção descreve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] como hospedar conteúdo em um aplicativo Básico Win32. O conteúdo em si é implementado em C++/CLI como uma classe gerenciada. Na maioria das vezes, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] é uma programação simples. Os principais aspectos da implementação do conteúdo são discutidos na [implementação do conteúdo WPF](#implementing_the_wpf_page).

- [O aplicativo básico](#the_basic_application)

- [Hospedando o conteúdo do WPF](#hosting_the_wpf_page)

- [Mantendo uma referência ao conteúdo do WPF](#holding_a_reference)

- [Comunicando com o conteúdo do WPF](#communicating_with_the_page)

<a name="the_basic_application"></a>
### <a name="the-basic-application"></a>O aplicativo básico
 O ponto de partida para o aplicativo host foi criar um modelo Visual Studio 2005.

1. Abra o Visual Studio 2005 e selecione **Novo Projeto** no menu **Arquivo.**

2. Selecione **Win32** na lista de tipos de projeto Visual C++. Se o seu idioma padrão não for C++, você encontrará esses tipos de projeto em **Outras Línguas**.

3. Selecione um modelo **de projeto Win32,** atribua um nome ao projeto e clique em **OK** para iniciar o Assistente de **Aplicativo Win32**.

4. Aceite as configurações padrão do assistente e clique **em Concluir** para iniciar o projeto.

 O modelo cria um aplicativo básico do Win32, incluindo:

- Um ponto de entrada do aplicativo.

- Uma janela, com um procedimento de janela associado (WndProc).

- Um menu com os títulos **Arquivo** e **Ajuda.** O menu **Arquivo** tem um item **Sair** que fecha o aplicativo. O menu **Ajuda** tem um item **Sobre** que lança uma caixa de diálogo simples.

 Antes de começar a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] escrever código para hospedar o conteúdo, você precisa fazer duas modificações no modelo básico.

 A primeira é compilar o projeto como um código gerenciado. Por padrão, o projeto é compilado como um código não gerenciado. No entanto, como [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] é implementado em código gerenciado, o projeto deve ser compilado em conformidade.

1. Clique com o botão direito do mouse no nome do projeto no **Solution Explorer** e selecione **Propriedades** no menu de contexto para iniciar a caixa de diálogo **Páginas** de propriedade.

2. Selecione Propriedades de **configuração** na exibição da árvore no painel esquerdo.

3. Selecione o suporte **ao tempo de execução** do idioma comum na lista **'Padrão do projeto'** no painel direito.

4. Selecione **O suporte ao tempo de execução do idioma comum (/clr)** na caixa de lista baixa.

> [!NOTE]
> Esse sinalizador de compilação permite que você use um código gerenciado no aplicativo, mas o código não gerenciado continuará sendo compilado como antes.

 O [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] usa o modelo de threading STA (Single-Threaded Apartment). Para trabalhar corretamente [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] com o código de conteúdo, você deve definir o modelo de rosca do aplicativo como STA aplicando um atributo ao ponto de entrada.

 [!code-cpp[Win32HostingWPFPage#WinMain](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#winmain)]

<a name="hosting_the_wpf_page"></a>
### <a name="hosting-the-wpf-content"></a>Hospedando o conteúdo do WPF
 O [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] conteúdo é um simples aplicativo de entrada de endereço. Ele consiste em <xref:System.Windows.Controls.TextBox> vários controles para levar nome de usuário, endereço e assim por diante. Há também <xref:System.Windows.Controls.Button> dois controles, **OK** e **Cancel**. Quando o usuário clica em <xref:System.Windows.Controls.Primitives.ButtonBase.Click> **OK,** o manipulador de eventos do botão coleta os dados dos <xref:System.Windows.Controls.TextBox> controles, atribui-os às propriedades correspondentes e levanta um evento personalizado, `OnButtonClicked`. Quando o usuário **clica em Cancelar,** o manipulador simplesmente levanta `OnButtonClicked`. O objeto de `OnButtonClicked` argumento de evento para contém um campo booleano que indica qual botão foi clicado.

 O código para [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hospedar o conteúdo é implementado em um manipulador para a notificação [WM_CREATE](/windows/desktop/winmsg/wm-create) na janela host.

 [!code-cpp[Win32HostingWPFPage#WMCreate](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#wmcreate)]

 O `GetHwnd` método pega informações de tamanho e posição, além da [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] alça da janela pai e retorna a alça da janela do conteúdo hospedado.

> [!NOTE]
> Você não `#using` pode usar `System::Windows::Interop` uma diretiva para o namespace. Isso cria uma colisão <xref:System.Windows.Interop.MSG> de nome entre a estrutura nesse namespace e a estrutura MSG declarada em winuser.h. Em vez disso, use nomes totalmente qualificados para acessar o conteúdo desse namespace.

 [!code-cpp[Win32HostingWPFPage#GetHwnd](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#gethwnd)]

 Não é [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] possível hospedar o conteúdo diretamente na janela do aplicativo. Em vez disso, <xref:System.Windows.Interop.HwndSource> primeiro você [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] cria um objeto para embrulhar o conteúdo. Este objeto é basicamente uma janela [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] projetada para hospedar um conteúdo. Você hospeda o <xref:System.Windows.Interop.HwndSource> objeto na janela pai criando-o como filho de uma janela Win32 que faz parte do seu aplicativo. Os <xref:System.Windows.Interop.HwndSource> parâmetros do construtor contêm as mesmas informações que você passaria para criar janela quando você criar uma janela de filho Win32.

 Em seguida, você [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] cria uma instância do objeto de conteúdo. Neste caso, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] o conteúdo é implementado `WPFPage`como uma classe separada, usando C++/CLI. Você também pode [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] implementar [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]o conteúdo com . No entanto, para isso, você precisa configurar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] um projeto separado e construir o conteúdo como um DLL. Você pode adicionar uma referência a essa DLL ao seu projeto [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] e usar essa referência para criar uma instância do conteúdo.

 Você exibe [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] o conteúdo na janela do seu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] filho <xref:System.Windows.Interop.HwndSource.RootVisual%2A> atribuindo <xref:System.Windows.Interop.HwndSource>uma referência ao conteúdo à propriedade do .

 A próxima linha de código anexa `WPFButtonClicked`um [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] manipulador `OnButtonClicked` de eventos ao evento de conteúdo. Este manipulador é chamado quando o usuário clica no botão **OK** ou **Cancel.** Consulte [communicating_with_the_WPF conteúdo](#communicating_with_the_page) para mais discussão sobre este manipulador de eventos.

 A linha final de código mostrada retorna a alça da <xref:System.Windows.Interop.HwndSource> janela (HWND) associada ao objeto. Você pode usar este cabo a partir do seu código Win32 para enviar mensagens para a janela hospedada, embora a amostra não o faça. O <xref:System.Windows.Interop.HwndSource> objeto levanta um evento toda vez que recebe uma mensagem. Para processar as mensagens, ligue para o <xref:System.Windows.Interop.HwndSource.AddHook%2A> método para anexar um manipulador de mensagens e, em seguida, processe as mensagens nesse manipulador.

<a name="holding_a_reference"></a>
### <a name="holding-a-reference-to-the-wpf-content"></a>Mantendo uma referência ao conteúdo do WPF
 Para muitos aplicativos, você vai querer [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] se comunicar com o conteúdo mais tarde. Por exemplo, você pode [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] querer modificar as propriedades <xref:System.Windows.Interop.HwndSource> de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] conteúdo ou talvez ter o objeto hospedando conteúdo diferente. Para fazer isso, você precisa <xref:System.Windows.Interop.HwndSource> de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uma referência ao objeto ou ao conteúdo. O <xref:System.Windows.Interop.HwndSource> objeto e [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] seu conteúdo associado permanecem na memória até que você destrua a alça da janela. No entanto, a variável <xref:System.Windows.Interop.HwndSource> que você atribui ao objeto sairá do escopo assim que você retornar do procedimento da janela. A maneira usual de lidar com esse problema com aplicativos Win32 é usar uma variável estática ou global. Infelizmente, não é possível atribuir um objeto gerenciado a esses tipos de variáveis. Você pode atribuir a alça <xref:System.Windows.Interop.HwndSource> da janela associada ao objeto a uma variável global ou estática, mas essa doe não fornece acesso ao objeto em si.

 A solução mais simples para esse problema é implementar uma classe gerenciada que contém um conjunto de campos estáticos para manter referências a todos os objetos gerenciados aos quais você precisa ter acesso. A amostra `WPFPageHost` usa a classe para [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] manter uma referência ao conteúdo, além dos valores iniciais de uma série de suas propriedades que podem ser alteradas posteriormente pelo usuário. Isso é definido no cabeçalho.

 [!code-cpp[Win32HostingWPFPage#WPFPageHost](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.h#wpfpagehost)]

 A última parte `GetHwnd` da função atribui valores a `myPage` esses campos para uso posterior enquanto ainda está no escopo.

<a name="communicating_with_the_page"></a>
### <a name="communicating-with-the-wpf-content"></a>Comunicando com o conteúdo do WPF
 Existem dois tipos de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] comunicação com o conteúdo. O aplicativo recebe [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] informações do conteúdo quando o usuário clica nos botões **OK** ou **Cancel.** O aplicativo também [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] possui um que [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] permite ao usuário alterar várias propriedades de conteúdo, como a cor de fundo ou o tamanho padrão da fonte.

 Como mencionado acima, quando o usuário [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clica `OnButtonClicked` em qualquer botão o conteúdo levanta um evento. O aplicativo anexa um manipulador a esse evento para receber essas notificações. Se o botão **OK** foi clicado, o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] manipulador obtém as informações do usuário do conteúdo e as exibe em um conjunto de controles estáticos.

 [!code-cpp[Win32HostingWPFPage#WPFButtonClicked](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#wpfbuttonclicked)]

 O manipulador recebe um objeto [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] de `MyPageEventArgs`argumento de evento personalizado do conteúdo, . A propriedade `IsOK` do objeto `true` é definida para se o `false` botão **OK** foi clicado e se o botão **Cancelar** foi clicado.

 Se o botão **OK** foi clicado, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] o manipulador recebe uma referência ao conteúdo da classe de contêiner. Em seguida, coleta as informações do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] usuário que são mantidas pelas propriedades de conteúdo associadas e usa os controles estáticos para exibir as informações na janela pai. Como [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] os dados de conteúdo estão na forma de uma seqüência gerenciada, ele tem que ser empacotado para uso por um controle Win32. Se o botão **Cancelar** foi clicado, o manipulador limpará os dados dos controles estáticos.

 O [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] aplicativo fornece um conjunto de botões de rádio que [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] permitem ao usuário modificar a cor de fundo do conteúdo e várias propriedades relacionadas à fonte. O exemplo a seguir é um trecho do procedimento de janela (WndProc) do aplicativo e sua manipulação de mensagens que define várias propriedades em diferentes mensagens, incluindo a cor da tela de fundo. As outras são semelhantes e não são mostradas. Consulte a amostra completa para obter detalhes e o contexto.

 [!code-cpp[Win32HostingWPFPage#WMCommandToBG](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#wmcommandtobg)]

 Para definir a cor de fundo,`hostedPage`obtenha `WPFPageHost` uma referência ao [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] conteúdo ( ) e defina a propriedade de cor de fundo para a cor apropriada. A amostra usa três opções de cores: a cor original, verde-claro e salmão-claro. A cor de fundo original é `WPFPageHost` armazenada como um campo estático na classe. Para definir os outros dois, <xref:System.Windows.Media.SolidColorBrush> você cria um novo objeto e <xref:System.Windows.Media.Colors> passa ao construtor um valor de cores estáticas a partir do objeto.

<a name="implementing_the_wpf_page"></a>
## <a name="implementing-the-wpf-page"></a>Implementando a página do WPF
 Você pode hospedar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] e usar o conteúdo sem qualquer conhecimento da implementação real. Se [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] o conteúdo tivesse sido embalado em uma DLL separada, ele poderia ter sido construído em qualquer idioma de tempo de execução (CLR) comum. A seguir está um breve passo a passo da implementação C++/CLI que é usada na amostra. Esta seção contém as subseções a seguir.

- [Layout](#page_layout)

- [Retornando os dados à janela do host](#returning_data_to_window)

- [Definindo as propriedades do WPF](#set_page_properties)

<a name="page_layout"></a>
### <a name="layout"></a>Layout
 Os [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elementos [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] no conteúdo <xref:System.Windows.Controls.TextBox> consistem em <xref:System.Windows.Controls.Label> cinco controles, com controles associados: Nome, Endereço, Cidade, Estado e Zip. Há também <xref:System.Windows.Controls.Button> dois controles, **OK** e **Cancel**

 O [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] conteúdo é `WPFPage` implementado na classe. O layout é <xref:System.Windows.Controls.Grid> manuseado com um elemento de layout. A classe herda de <xref:System.Windows.Controls.Grid>, o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] que efetivamente faz dele o elemento raiz do conteúdo.

 O [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] construtor de conteúdo leva a largura e <xref:System.Windows.Controls.Grid> altura necessárias, e dimensiona o em conformidade. Em seguida, define o layout básico <xref:System.Windows.Controls.ColumnDefinition> <xref:System.Windows.Controls.RowDefinition> criando um conjunto <xref:System.Windows.Controls.Grid> de <xref:System.Windows.Controls.Grid.ColumnDefinitions%2A> objetos e adicionando-os à base de objetos e <xref:System.Windows.Controls.Grid.RowDefinitions%2A> coleções, respectivamente. Isso define uma grade de cinco linhas e sete colunas, com as dimensões determinadas pelo conteúdo das células.

 [!code-cpp[Win32HostingWPFPage#WPFPageCtorToGridDef](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagectortogriddef)]

 Em seguida, o [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] construtor adiciona <xref:System.Windows.Controls.Grid>os elementos ao . O primeiro elemento é o texto <xref:System.Windows.Controls.Label> do título, que é um controle centrado na primeira linha da grade.

 [!code-cpp[Win32HostingWPFPage#WPFPageCtorTitle](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagectortitle)]

 A próxima linha <xref:System.Windows.Controls.Label> contém o <xref:System.Windows.Controls.TextBox> controle Name e seu controle associado. Como o mesmo código é usado para cada par rótulo/caixa de texto, ele é colocado em um par de métodos particulares e usado para todos os cinco pares de rótulo/caixa de texto. Os métodos criam o controle <xref:System.Windows.Controls.Grid> apropriado <xref:System.Windows.Controls.Grid.SetColumn%2A> e <xref:System.Windows.Controls.Grid.SetRow%2A> chamam a classe de estática e métodos para colocar os controles na célula apropriada. Depois que o controle é criado, a amostra chama o <xref:System.Windows.Controls.UIElementCollection.Add%2A> método na <xref:System.Windows.Controls.Panel.Children%2A> propriedade do <xref:System.Windows.Controls.Grid> para adicionar o controle à grade. O código para adicionar os pares de rótulo/caixa de texto restantes é semelhante. Consulte o código de exemplo para obter detalhes.

 [!code-cpp[Win32HostingWPFPage#WPFPageCtorName](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagectorname)]

 A implementação dos dois métodos ocorre da seguinte forma:

 [!code-cpp[Win32HostingWPFPage#WPFPageCreateHelpers](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagecreatehelpers)]

 Finalmente, a amostra adiciona os botões **OK** e **Cancel** <xref:System.Windows.Controls.Primitives.ButtonBase.Click> e anexa um manipulador de eventos aos seus eventos.

 [!code-cpp[Win32HostingWPFPage#WPFPageCtorButtonsEvents](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagectorbuttonsevents)]

<a name="returning_data_to_window"></a>
### <a name="returning-the-data-to-the-host-window"></a>Retornando os dados à janela do host
 Quando um dos botões <xref:System.Windows.Controls.Primitives.ButtonBase.Click> é clicado, seu evento é levantado. A janela host pode simplesmente anexar manipuladores a esses <xref:System.Windows.Controls.TextBox> eventos e obter os dados diretamente dos controles. O exemplo usa uma abordagem um pouco menos direta. Ele lida <xref:System.Windows.Controls.Primitives.ButtonBase.Click> com [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] o conteúdo dentro do `OnButtonClicked`conteúdo e, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] em seguida, levanta um evento personalizado, para notificar o conteúdo. Isso permite [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] que o conteúdo faça alguma validação de parâmetroantes de notificar o host. O manipulador obtém <xref:System.Windows.Controls.TextBox> o texto dos controles e atribui-o a propriedades públicas, das quais o host pode recuperar as informações.

 A declaração de evento, em WPFPage.h:

 [!code-cpp[Win32HostingWPFPage#WPFPageEventDecl](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.h#wpfpageeventdecl)]

 O <xref:System.Windows.Controls.Primitives.ButtonBase.Click> manipulador de eventos, em WPFPage.cpp:

 [!code-cpp[Win32HostingWPFPage#WPFPageButtonClicked](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagebuttonclicked)]

<a name="set_page_properties"></a>
### <a name="setting-the-wpf-properties"></a>Definindo as propriedades do WPF
 O host Win32 permite que [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] o usuário altere várias propriedades de conteúdo. Do lado Win32, é simplesmente uma questão de mudar as propriedades. A implementação [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] na classe de conteúdo é um pouco mais complicada, pois não há uma única propriedade global que controle as fontes para todos os controles. Em vez disso, a propriedade apropriada de cada controle é alterada nos acessadores set das propriedades. O exemplo a seguir `DefaultFontFamily` mostra o código da propriedade. A configuração da propriedade chama um <xref:System.Windows.Controls.Control.FontFamily%2A> método privado que, por sua vez, define as propriedades para os vários controles.

 Em WPFPage.h:

 [!code-cpp[Win32HostingWPFPage#WPFPageFontFamilyProperty](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.h#wpfpagefontfamilyproperty)]

 Em WPFPage.cpp:

 [!code-cpp[Win32HostingWPFPage#WPFPageSetFontFamily](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagesetfontfamily)]

## <a name="see-also"></a>Confira também

- <xref:System.Windows.Interop.HwndSource>
- [Interoperação do WPF e do Win32](wpf-and-win32-interoperation.md)
