---
title: Visão geral da navegação estruturada
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- structured navigation [WPF]
ms.assetid: 025d30ef-fec5-436d-ad7a-5d5483331c26
ms.openlocfilehash: 8760c847d9e73fdff9f10f0dfa55a6c674021667
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/20/2019
ms.locfileid: "68364180"
---
# <a name="structured-navigation-overview"></a>Visão geral da navegação estruturada

O conteúdo que pode ser hospedado por [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)]um, <xref:System.Windows.Controls.Frame>um ou um <xref:System.Windows.Navigation.NavigationWindow> é composto por páginas que podem ser identificadas pelo [!INCLUDE[TLA#tla_uri#plural](../../../../includes/tlasharptla-urisharpplural-md.md)] pacote e navegadas por hiperlinks. A estrutura de páginas e as maneiras pelas quais elas podem ser navegadas, como definidas pelos hiperlinks, é conhecida como uma topologia de navegação. Uma topologia como esta serve a uma variedade de tipos de aplicativos, especialmente aqueles que navegam através de documentos. Para tais aplicativos, o usuário pode navegar de uma página à outra sem que as páginas precisem saber qualquer coisa sobre a outra.

No entanto, outros tipos de aplicativos têm páginas que precisam saber quando houve navegação entre elas. Por exemplo, considere um aplicativo de recursos humanos que tem uma página para listar todos os funcionários de uma organização, a página "Lista de funcionários". Esta página também pode permitir que os usuários adicionem um novo funcionário, clicando em um hiperlink. Ao clicar, a página navega para uma página "Adicionar um funcionário" para obter detalhes do novo empregado e retorná-los para a página "Lista de funcionários" para criar o novo funcionário e atualizar a lista. Este estilo de navegação é semelhante a chamar um método para fazer algum processamento e retornar um valor, que é conhecido como programação estruturada. Assim, este estilo de navegação é conhecido como *navegação estruturada*.

A <xref:System.Windows.Controls.Page> classe não implementa o suporte para navegação estruturada. Em vez disso <xref:System.Windows.Navigation.PageFunction%601> , a classe deriva <xref:System.Windows.Controls.Page> de e a estende com as construções básicas necessárias para a navegação estruturada. Este tópico mostra como estabelecer a navegação estruturada <xref:System.Windows.Navigation.PageFunction%601>usando o.

<a name="Structured_Navigation"></a>

## <a name="structured-navigation"></a>Navegação estruturada

Quando uma página chama outra página em uma navegação estruturada, alguns ou todos os seguintes comportamentos são necessários:

- A página chamadora navega até a página chamada, opcionalmente passando parâmetros exigidos pela página chamada.

- Quando um usuário tiver terminado de usar a página chamadora, a página chamada retorna especificamente para a página chamadora, de forma opcional:

  - Informações de estado de retorno que descrevem como a página chamadora foi concluída (por exemplo, se o usuário pressionou um botão OK ou um botão Cancelar).

  - Retornando os dados que foram coletados do usuário (por exemplo, detalhes do novo funcionário).

- Quando a página chamadora retorna para a página chamada, a página chamada é removida do histórico de navegação para isolar instâncias de páginas chamadas.

Esses comportamentos são ilustrados pela figura a seguir:

![Captura de tela mostra o fluxo entre a página de chamada e a página chamada.](./media/structured-navigation-overview/flow-between-calling-page-called-page.png)

Você pode implementar esses comportamentos usando um <xref:System.Windows.Navigation.PageFunction%601> como a página chamada.

<a name="Structured_Navigation_with_PageFunction"></a>

## <a name="structured-navigation-with-pagefunction"></a>Navegação estruturada com PageFunction

Este tópico mostra como implementar a mecânica básica de navegação estruturada que envolve um <xref:System.Windows.Navigation.PageFunction%601>único. Neste exemplo, um <xref:System.Windows.Controls.Page> chama um <xref:System.Windows.Navigation.PageFunction%601> para obter um <xref:System.String> valor do usuário e retorná-lo.

### <a name="creating-a-calling-page"></a>Criando uma página chamadora

A página que chama um <xref:System.Windows.Navigation.PageFunction%601> pode ser um <xref:System.Windows.Controls.Page> ou um <xref:System.Windows.Navigation.PageFunction%601>. Neste exemplo, é um <xref:System.Windows.Controls.Page>, conforme mostrado no código a seguir.

[!code-xaml[StructuredNavigationSample#CallingPageDefaultMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml#callingpagedefaultmarkup1)]
[!code-xaml[StructuredNavigationSample#CallingPageDefaultMARKUP2](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml#callingpagedefaultmarkup2)]

[!code-csharp[StructuredNavigationSample#CallingPageDefaultCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#callingpagedefaultcodebehind1)]
[!code-vb[StructuredNavigationSample#CallingPageDefaultCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#callingpagedefaultcodebehind1)]
[!code-csharp[StructuredNavigationSample#CallingPageDefaultCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#callingpagedefaultcodebehind2)]
[!code-vb[StructuredNavigationSample#CallingPageDefaultCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#callingpagedefaultcodebehind2)]
[!code-csharp[StructuredNavigationSample#CallingPageDefaultCODEBEHIND3](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#callingpagedefaultcodebehind3)]
[!code-vb[StructuredNavigationSample#CallingPageDefaultCODEBEHIND3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#callingpagedefaultcodebehind3)]

### <a name="creating-a-page-function-to-call"></a>Criando uma função de página para chamar

Como a página de chamada pode usar a página chamada para coletar e retornar dados do usuário, <xref:System.Windows.Navigation.PageFunction%601> é implementada como uma classe genérica cujo argumento de tipo especifica o tipo do valor que a página chamada retornará. O código a seguir mostra a implementação inicial da página chamada, usando um <xref:System.Windows.Navigation.PageFunction%601>, que retorna um <xref:System.String>.

[!code-xaml[StructuredNavigationSample#CalledPageFunctionMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml#calledpagefunctionmarkup)]

[!code-csharp[StructuredNavigationSample#CalledPageFunctionCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#calledpagefunctioncodebehind1)]
[!code-vb[StructuredNavigationSample#CalledPageFunctionCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#calledpagefunctioncodebehind1)]
[!code-csharp[StructuredNavigationSample#CalledPageFunctionCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#calledpagefunctioncodebehind2)]
[!code-vb[StructuredNavigationSample#CalledPageFunctionCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#calledpagefunctioncodebehind2)]

A declaração de um <xref:System.Windows.Navigation.PageFunction%601> é semelhante à declaração de um <xref:System.Windows.Controls.Page> com a adição dos argumentos de tipo. Como você pode ver no código de exemplo, os argumentos de tipo são especificados tanto na marcação [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], usando o atributo `x:TypeArguments` quanto no code-behind, usando a sintaxe padrão de argumento de tipo genérico.

Você não precisa usar apenas classes .NET Framework como argumentos de tipo. Um <xref:System.Windows.Navigation.PageFunction%601> pode ser chamado para coletar dados específicos de domínio que são abstratos como um tipo personalizado. O código a seguir mostra como usar um tipo personalizado como um argumento de tipo para <xref:System.Windows.Navigation.PageFunction%601>um.

[!code-csharp[CustomTypePageFunctionSnippets#CustomTypeCODE1](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/CSharp/CustomType.cs#customtypecode1)]
[!code-vb[CustomTypePageFunctionSnippets#CustomTypeCODE1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/VisualBasic/CustomType.vb#customtypecode1)]
[!code-csharp[CustomTypePageFunctionSnippets#CustomTypeCODE2](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/CSharp/CustomType.cs#customtypecode2)]
[!code-vb[CustomTypePageFunctionSnippets#CustomTypeCODE2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/VisualBasic/CustomType.vb#customtypecode2)]

[!code-xaml[CustomTypePageFunctionSnippets#CustomTypePageFunctionMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/CSharp/CustomTypePageFunction.xaml#customtypepagefunctionmarkup1)]
[!code-xaml[CustomTypePageFunctionSnippets#CustomTypePageFunctionMARKUP2](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/CSharp/CustomTypePageFunction.xaml#customtypepagefunctionmarkup2)]

[!code-csharp[CustomTypePageFunctionSnippets#CustomTypePageFunctionCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/CSharp/CustomTypePageFunction.xaml.cs#customtypepagefunctioncodebehind1)]
[!code-vb[CustomTypePageFunctionSnippets#CustomTypePageFunctionCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/VisualBasic/CustomTypePageFunction.xaml.vb#customtypepagefunctioncodebehind1)]
[!code-csharp[CustomTypePageFunctionSnippets#CustomTypePageFunctionCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/CSharp/CustomTypePageFunction.xaml.cs#customtypepagefunctioncodebehind2)]
[!code-vb[CustomTypePageFunctionSnippets#CustomTypePageFunctionCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/VisualBasic/CustomTypePageFunction.xaml.vb#customtypepagefunctioncodebehind2)]

Os argumentos de tipo para <xref:System.Windows.Navigation.PageFunction%601> o fornecem a base para a comunicação entre uma página de chamada e a página chamada, que são discutidas nas seções a seguir.

Como você verá, o tipo identificado com a declaração de um <xref:System.Windows.Navigation.PageFunction%601> desempenha um papel importante no retorno de dados de um <xref:System.Windows.Navigation.PageFunction%601> para a página de chamada.

### <a name="calling-a-pagefunction-and-passing-parameters"></a>Chamando uma PageFunction e passando parâmetros

Para chamar uma página, a página de chamada deve instanciar a página chamada e navegar para ela <xref:System.Windows.Navigation.NavigationService.Navigate%2A> usando o método. Isso permite que a página chamadora passe dados iniciais para a página chamada, como valores padrão para os dados que estão sendo coletados pela página chamada.

O código a seguir mostra a página chamada com um construtor sem parâmetros para aceitar parâmetros da página de chamada.

[!code-csharp[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#acceptsinitialdatacodebehind1)]
[!code-vb[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#acceptsinitialdatacodebehind1)]
[!code-csharp[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#acceptsinitialdatacodebehind2)]
[!code-vb[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#acceptsinitialdatacodebehind2)]
[!code-csharp[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND3](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#acceptsinitialdatacodebehind3)]
[!code-vb[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#acceptsinitialdatacodebehind3)]
[!code-csharp[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND4](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#acceptsinitialdatacodebehind4)]
[!code-vb[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#acceptsinitialdatacodebehind4)]

O código a seguir mostra a página <xref:System.Windows.Documents.Hyperlink.Click> <xref:System.Windows.Documents.Hyperlink> de chamada que manipula o evento do para instanciar a página chamada e passá-la para um valor de cadeia de caracteres inicial.

[!code-xaml[StructuredNavigationSample#PassingDataMARKUP2](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml#passingdatamarkup2)]
[!code-csharp[StructuredNavigationSample#PassingDataCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#passingdatacodebehind1)]
[!code-vb[StructuredNavigationSample#PassingDataCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#passingdatacodebehind1)]
[!code-csharp[StructuredNavigationSample#PassingDataCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#passingdatacodebehind2)]
[!code-vb[StructuredNavigationSample#PassingDataCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#passingdatacodebehind2)]
[!code-csharp[StructuredNavigationSample#PassingDataCODEBEHIND3](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#passingdatacodebehind3)]
[!code-vb[StructuredNavigationSample#PassingDataCODEBEHIND3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#passingdatacodebehind3)]

Não é necessário passar parâmetros para a página chamada. Em vez disso, você pode fazer o seguinte:

- Da página chamadora:

  1. Crie uma instância <xref:System.Windows.Navigation.PageFunction%601> do chamada usando o construtor sem parâmetros.

  2. Armazene os parâmetros <xref:System.Windows.Application.Properties%2A>em.

  3. Navegue até o chamado <xref:System.Windows.Navigation.PageFunction%601>.

- Do chamado <xref:System.Windows.Navigation.PageFunction%601>:

  - Recuperar e usar os parâmetros armazenados em <xref:System.Windows.Application.Properties%2A>.

Mas, como você verá em breve, você ainda precisará usar código para instanciar e navegar até a página chamada para coletar os dados retornados pela página chamada. Por esse motivo, o <xref:System.Windows.Navigation.PageFunction%601> precisa ser mantido ativo; caso contrário, na próxima vez que você navegar para <xref:System.Windows.Navigation.PageFunction%601>o [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] , o criará uma instância do <xref:System.Windows.Navigation.PageFunction%601> usando o construtor sem parâmetros.

No entanto, antes que a página chamada possa retornar, ela precisa retornar dados que podem ser recuperados pela página chamadora.

### <a name="returning-task-result-and-task-data-from-a-task-to-a-calling-page"></a>Retornando o resultado da tarefa e os dados de tarefa de uma tarefa para uma página chamadora

Quando o usuário tiver terminado de usar a página chamada, ao pressionar os botões OK ou Cancelar neste exemplo, a página chamada precisa retornar. Como a página chamadora usou a página chamada para coletar dados do usuário, a página chamadora necessita de dois tipos de informações:

1. Se o usuário cancelou a página chamada (pressionando o botão OK ou o botão Cancelar neste exemplo). Isso permite que a página chamadora determine se deve processar os dados que a página chamadora obteve do usuário.

2. Os dados que foram fornecidos pelo usuário.

Para retornar informações, <xref:System.Windows.Navigation.PageFunction%601> o implementa <xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A> o método. O código a seguir mostra como chamá-lo.

[!code-csharp[StructuredNavigationSample#ReturnCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#returncodebehind1)]
[!code-vb[StructuredNavigationSample#ReturnCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#returncodebehind1)]
[!code-csharp[StructuredNavigationSample#ReturnCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#returncodebehind2)]
[!code-vb[StructuredNavigationSample#ReturnCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#returncodebehind2)]

Neste exemplo, se um usuário pressiona o botão Cancelar, um valor de `null` é retornado para a página chamadora. Se, em vez disso, o botão OK for pressionado, será retornado o valor de cadeia de caracteres fornecido pelo usuário. <xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A>é um `protected virtual` método que você chama para retornar os dados para a página de chamada. Seus dados precisam ser empacotados em uma instância do tipo genérico <xref:System.Windows.Navigation.ReturnEventArgs%601> , cujo argumento de tipo especifica o tipo de valor que <xref:System.Windows.Navigation.ReturnEventArgs%601.Result%2A> retorna. Dessa forma, quando você declara um <xref:System.Windows.Navigation.PageFunction%601> com um argumento de tipo específico, está informando que um <xref:System.Windows.Navigation.PageFunction%601> retornará uma instância do tipo que é especificado pelo argumento de tipo. Neste exemplo, o argumento de tipo e, consequentemente, o valor de retorno é <xref:System.String>do tipo.

Quando <xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A> é chamado, a página de chamada precisa de alguma forma de receber o valor <xref:System.Windows.Navigation.PageFunction%601>de retorno do. Por esse motivo, <xref:System.Windows.Navigation.PageFunction%601> o implementa <xref:System.Windows.Navigation.PageFunction%601.Return> o evento para chamar páginas a serem manipuladas. Quando <xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A> é chamado, <xref:System.Windows.Navigation.PageFunction%601.Return> é gerado, portanto, a página de chamada pode <xref:System.Windows.Navigation.PageFunction%601.Return> se registrar no para receber a notificação.

[!code-csharp[StructuredNavigationSample#ProcessResultCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#processresultcodebehind1)]
[!code-vb[StructuredNavigationSample#ProcessResultCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#processresultcodebehind1)]
[!code-csharp[StructuredNavigationSample#ProcessResultCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#processresultcodebehind2)]
[!code-vb[StructuredNavigationSample#ProcessResultCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#processresultcodebehind2)]

### <a name="removing-task-pages-when-a-task-completes"></a>Removendo páginas de tarefa quando uma tarefa é concluída

Quando uma página chamada retorna, e o usuário não cancelou a página chamada, a página chamadora processará os dados fornecidos pelo usuário e também os retornados pela página chamada. A aquisição de dados dessa forma costuma ser uma atividade isolada. Quando a página chamada retorna, a página chamadora precisa criar e navegar até uma nova página chamadora para capturar mais dados.

No entanto, a menos que uma página chamada seja removida do diário, um usuário poderá navegar de volta para uma instância anterior da página chamadora. Se um <xref:System.Windows.Navigation.PageFunction%601> é retido no diário é determinado <xref:System.Windows.Navigation.PageFunctionBase.RemoveFromJournal%2A> pela propriedade. Por padrão, uma função Page é removida automaticamente <xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A> quando é chamado <xref:System.Windows.Navigation.PageFunctionBase.RemoveFromJournal%2A> porque é definido `true`como. Para manter uma função de página no histórico de <xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A> navegação depois que é <xref:System.Windows.Navigation.PageFunctionBase.RemoveFromJournal%2A> chamado `false`, defina como.

<a name="Other_Types_of_Structured_Navigation"></a>

## <a name="other-types-of-structured-navigation"></a>Outros tipos de navegação estruturada

Este tópico ilustra o uso mais básico de um <xref:System.Windows.Navigation.PageFunction%601> para dar suporte à navegação estruturada de chamada/retorno. Essa base fornece a capacidade para criar tipos mais complexos de navegação estruturada.

Por exemplo, algumas vezes várias páginas são exigidas pela página chamadora, para obter dados suficientes de um usuário ou para realizar uma tarefa. O uso de várias páginas é conhecido como um "assistente".

Em outros casos, os aplicativos podem ter topologias complexas de navegação que dependem da navegação estruturada para operar com eficiência. Para obter mais informações, consulte [Visão geral de topologias de navegação](navigation-topologies-overview.md).

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Navigation.PageFunction%601>
- <xref:System.Windows.Navigation.NavigationService>
- [Visão geral de topologias de navegação](navigation-topologies-overview.md)
