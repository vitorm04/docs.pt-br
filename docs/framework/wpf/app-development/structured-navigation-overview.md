---
title: Visão geral da navegação estruturada
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- structured navigation [WPF]
ms.assetid: 025d30ef-fec5-436d-ad7a-5d5483331c26
ms.openlocfilehash: 2264686f34123e74bf7d24ce80877742d952f35d
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44133669"
---
# <a name="structured-navigation-overview"></a>Visão geral da navegação estruturada
Conteúdo que pode ser hospedado por um [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)], um <xref:System.Windows.Controls.Frame>, ou uma <xref:System.Windows.Navigation.NavigationWindow> é composto de páginas que podem ser identificadas pelo pacote [!INCLUDE[TLA#tla_uri#plural](../../../../includes/tlasharptla-urisharpplural-md.md)] e acessadas por hiperlinks. A estrutura de páginas e as maneiras pelas quais elas podem ser navegadas, como definidas pelos hiperlinks, é conhecida como uma topologia de navegação. Uma topologia como esta serve a uma variedade de tipos de aplicativos, especialmente aqueles que navegam através de documentos. Para tais aplicativos, o usuário pode navegar de uma página à outra sem que as páginas precisem saber qualquer coisa sobre a outra.  
  
 No entanto, outros tipos de aplicativos têm páginas que precisam saber quando houve navegação entre elas. Por exemplo, considere um aplicativo de recursos humanos que tem uma página para listar todos os funcionários de uma organização, a página "Lista de funcionários". Esta página também pode permitir que os usuários adicionem um novo funcionário, clicando em um hiperlink. Ao clicar, a página navega para uma página "Adicionar um funcionário" para obter detalhes do novo empregado e retorná-los para a página "Lista de funcionários" para criar o novo funcionário e atualizar a lista. Este estilo de navegação é semelhante a chamar um método para fazer algum processamento e retornar um valor, que é conhecido como programação estruturada. Assim, este estilo de navegação é conhecido como *navegação estruturada*.  
  
 O <xref:System.Windows.Controls.Page> classe não implementa o suporte à navegação estruturada. Em vez disso, o <xref:System.Windows.Navigation.PageFunction%601> deriva de classe <xref:System.Windows.Controls.Page> e a estende com as construções básicas necessárias para a navegação estruturada. Este tópico mostra como estabelecer a navegação estruturada usando <xref:System.Windows.Navigation.PageFunction%601>.  
  
 
  
<a name="Structured_Navigation"></a>   
## <a name="structured-navigation"></a>Navegação estruturada  
 Quando uma página chama outra página em uma navegação estruturada, alguns ou todos os seguintes comportamentos são necessários:  
  
-   A página chamadora navega até a página chamada, opcionalmente passando parâmetros exigidos pela página chamada.  
  
-   Quando um usuário tiver terminado de usar a página chamadora, a página chamada retorna especificamente para a página chamadora, de forma opcional:  
  
    -   Informações de estado de retorno que descrevem como a página chamadora foi concluída (por exemplo, se o usuário pressionou um botão OK ou um botão Cancelar).  
  
    -   Retornando os dados que foram coletados do usuário (por exemplo, detalhes do novo funcionário).  
  
-   Quando a página chamadora retorna para a página chamada, a página chamada é removida do histórico de navegação para isolar instâncias de páginas chamadas.  
  
 Esses comportamentos estão ilustrados na figura a seguir.  
  
 ![Fluxo entre a página chamadora e a página chamada](../../../../docs/framework/wpf/app-development/media/structurednavigationoverviewfigure1.png "StructuredNavigationOverviewFigure1")  
  
 Você pode implementar estes comportamentos usando um <xref:System.Windows.Navigation.PageFunction%601> como a página chamada.  
  
<a name="Structured_Navigation_with_PageFunction"></a>   
## <a name="structured-navigation-with-pagefunction"></a>Navegação estruturada com PageFunction  
 Este tópico mostra como implementar a mecânica básica da navegação estruturada envolvendo uma única <xref:System.Windows.Navigation.PageFunction%601>. Neste exemplo, uma <xref:System.Windows.Controls.Page> chamadas de um <xref:System.Windows.Navigation.PageFunction%601> para obter um <xref:System.String> de valor do usuário e retorná-lo.  
  
### <a name="creating-a-calling-page"></a>Criando uma página chamadora  
 A página que chama um <xref:System.Windows.Navigation.PageFunction%601> pode ser uma <xref:System.Windows.Controls.Page> ou um <xref:System.Windows.Navigation.PageFunction%601>. Neste exemplo, ele é um <xref:System.Windows.Controls.Page>, conforme mostrado no código a seguir.  
  
 [!code-xaml[StructuredNavigationSample#CallingPageDefaultMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml#callingpagedefaultmarkup1)]  
[!code-xaml[StructuredNavigationSample#CallingPageDefaultMARKUP2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml#callingpagedefaultmarkup2)]  
  
 [!code-csharp[StructuredNavigationSample#CallingPageDefaultCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#callingpagedefaultcodebehind1)]
 [!code-vb[StructuredNavigationSample#CallingPageDefaultCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#callingpagedefaultcodebehind1)]  
[!code-csharp[StructuredNavigationSample#CallingPageDefaultCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#callingpagedefaultcodebehind2)]
[!code-vb[StructuredNavigationSample#CallingPageDefaultCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#callingpagedefaultcodebehind2)]  
[!code-csharp[StructuredNavigationSample#CallingPageDefaultCODEBEHIND3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#callingpagedefaultcodebehind3)]
[!code-vb[StructuredNavigationSample#CallingPageDefaultCODEBEHIND3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#callingpagedefaultcodebehind3)]  
  
### <a name="creating-a-page-function-to-call"></a>Criando uma função de página para chamar  
 Porque a página chamadora pode usar a página chamada para coletar e retornar dados do usuário, <xref:System.Windows.Navigation.PageFunction%601> é implementado como uma classe genérica cujo argumento de tipo Especifica o tipo do valor que a página chamada retornará. O código a seguir mostra a implementação inicial da chamada de página, usando um <xref:System.Windows.Navigation.PageFunction%601>, que retorna um <xref:System.String>.  
  
 [!code-xaml[StructuredNavigationSample#CalledPageFunctionMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml#calledpagefunctionmarkup)]  
  
 [!code-csharp[StructuredNavigationSample#CalledPageFunctionCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#calledpagefunctioncodebehind1)]
 [!code-vb[StructuredNavigationSample#CalledPageFunctionCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#calledpagefunctioncodebehind1)]  
[!code-csharp[StructuredNavigationSample#CalledPageFunctionCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#calledpagefunctioncodebehind2)]
[!code-vb[StructuredNavigationSample#CalledPageFunctionCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#calledpagefunctioncodebehind2)]  
  
 A declaração de uma <xref:System.Windows.Navigation.PageFunction%601> é semelhante à declaração de um <xref:System.Windows.Controls.Page> com a adição dos argumentos de tipo. Como você pode ver no código de exemplo, os argumentos de tipo são especificados tanto na marcação [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], usando o atributo `x:TypeArguments` quanto no code-behind, usando a sintaxe padrão de argumento de tipo genérico.  
  
 Você não precisa usar somente classes [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] como argumentos de tipo. Um <xref:System.Windows.Navigation.PageFunction%601> poderia ser chamado para coletar dados específicos do domínio que são abstraídos como um tipo personalizado. O código a seguir mostra como usar um tipo personalizado como um argumento de tipo para um <xref:System.Windows.Navigation.PageFunction%601>.  
  
 [!code-csharp[CustomTypePageFunctionSnippets#CustomTypeCODE1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/CSharp/CustomType.cs#customtypecode1)]
 [!code-vb[CustomTypePageFunctionSnippets#CustomTypeCODE1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/VisualBasic/CustomType.vb#customtypecode1)]  
[!code-csharp[CustomTypePageFunctionSnippets#CustomTypeCODE2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/CSharp/CustomType.cs#customtypecode2)]
[!code-vb[CustomTypePageFunctionSnippets#CustomTypeCODE2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/VisualBasic/CustomType.vb#customtypecode2)]  
  
 [!code-xaml[CustomTypePageFunctionSnippets#CustomTypePageFunctionMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/CSharp/CustomTypePageFunction.xaml#customtypepagefunctionmarkup1)]  
[!code-xaml[CustomTypePageFunctionSnippets#CustomTypePageFunctionMARKUP2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/CSharp/CustomTypePageFunction.xaml#customtypepagefunctionmarkup2)]  
  
 [!code-csharp[CustomTypePageFunctionSnippets#CustomTypePageFunctionCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/CSharp/CustomTypePageFunction.xaml.cs#customtypepagefunctioncodebehind1)]
 [!code-vb[CustomTypePageFunctionSnippets#CustomTypePageFunctionCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/VisualBasic/CustomTypePageFunction.xaml.vb#customtypepagefunctioncodebehind1)]  
[!code-csharp[CustomTypePageFunctionSnippets#CustomTypePageFunctionCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/CSharp/CustomTypePageFunction.xaml.cs#customtypepagefunctioncodebehind2)]
[!code-vb[CustomTypePageFunctionSnippets#CustomTypePageFunctionCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/VisualBasic/CustomTypePageFunction.xaml.vb#customtypepagefunctioncodebehind2)]  
  
 Os argumentos de tipo para o <xref:System.Windows.Navigation.PageFunction%601> fornecem a base para a comunicação entre a página chamadora e a página chamada, que são discutidos nas seções a seguir.  
  
 Como você verá, o tipo que é identificado com a declaração de uma <xref:System.Windows.Navigation.PageFunction%601> desempenha um papel importante no retorno de dados de um <xref:System.Windows.Navigation.PageFunction%601> para a página chamadora.  
  
### <a name="calling-a-pagefunction-and-passing-parameters"></a>Chamando uma PageFunction e passando parâmetros  
 Para chamar uma página, a página chamadora precisa instanciar a página chamada e navegar para ele usando o <xref:System.Windows.Navigation.NavigationService.Navigate%2A> método. Isso permite que a página chamadora passe dados iniciais para a página chamada, como valores padrão para os dados que estão sendo coletados pela página chamada.  
  
 O código a seguir mostra a página chamada com um construtor não padrão para aceitar parâmetros da página chamadora.  
  
 [!code-csharp[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#acceptsinitialdatacodebehind1)]
 [!code-vb[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#acceptsinitialdatacodebehind1)]  
[!code-csharp[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#acceptsinitialdatacodebehind2)]
[!code-vb[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#acceptsinitialdatacodebehind2)]  
[!code-csharp[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#acceptsinitialdatacodebehind3)]
[!code-vb[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#acceptsinitialdatacodebehind3)]  
[!code-csharp[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#acceptsinitialdatacodebehind4)]
[!code-vb[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#acceptsinitialdatacodebehind4)]  
  
 O código a seguir mostra a página chamadora tratando o <xref:System.Windows.Documents.Hyperlink.Click> eventos do <xref:System.Windows.Documents.Hyperlink> para instanciar a página chamada e passar para ele um valor de cadeia de caracteres inicial.  
  
 [!code-xaml[StructuredNavigationSample#PassingDataMARKUP2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml#passingdatamarkup2)]  
[!code-csharp[StructuredNavigationSample#PassingDataCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#passingdatacodebehind1)]
[!code-vb[StructuredNavigationSample#PassingDataCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#passingdatacodebehind1)]  
[!code-csharp[StructuredNavigationSample#PassingDataCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#passingdatacodebehind2)]
[!code-vb[StructuredNavigationSample#PassingDataCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#passingdatacodebehind2)]  
[!code-csharp[StructuredNavigationSample#PassingDataCODEBEHIND3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#passingdatacodebehind3)]
[!code-vb[StructuredNavigationSample#PassingDataCODEBEHIND3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#passingdatacodebehind3)]  
  
 Não é necessário passar parâmetros para a página chamada. Em vez disso, você pode fazer o seguinte:  
  
-   Da página chamadora:  
  
    1.  Criar uma instância chamada <xref:System.Windows.Navigation.PageFunction%601> usando o construtor padrão.  
  
    2.  Store parâmetros no <xref:System.Windows.Application.Properties%2A>.  
  
    3.  Navegue até a chamada <xref:System.Windows.Navigation.PageFunction%601>.  
  
-   Na chamada <xref:System.Windows.Navigation.PageFunction%601>:  
  
    -   Recuperar e usar os parâmetros armazenados em <xref:System.Windows.Application.Properties%2A>.  
  
 Mas, como você verá em breve, você ainda precisará usar código para instanciar e navegar até a página chamada para coletar os dados retornados pela página chamada. Por esse motivo, o <xref:System.Windows.Navigation.PageFunction%601> precisa ser mantida ativa; caso contrário, na próxima vez que você navegue até a <xref:System.Windows.Navigation.PageFunction%601>, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] instancia o <xref:System.Windows.Navigation.PageFunction%601> usando o construtor padrão.  
  
 No entanto, antes que a página chamada possa retornar, ela precisa retornar dados que podem ser recuperados pela página chamadora.  
  
### <a name="returning-task-result-and-task-data-from-a-task-to-a-calling-page"></a>Retornando o resultado da tarefa e os dados de tarefa de uma tarefa para uma página chamadora  
 Quando o usuário tiver terminado de usar a página chamada, ao pressionar os botões OK ou Cancelar neste exemplo, a página chamada precisa retornar. Como a página chamadora usou a página chamada para coletar dados do usuário, a página chamadora necessita de dois tipos de informações:  
  
1.  Se o usuário cancelou a página chamada (pressionando o botão OK ou o botão Cancelar neste exemplo). Isso permite que a página chamadora determine se deve processar os dados que a página chamadora obteve do usuário.  
  
2.  Os dados que foram fornecidos pelo usuário.  
  
 Para retornar informações, <xref:System.Windows.Navigation.PageFunction%601> implementa o <xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A> método. O código a seguir mostra como chamá-lo.  
  
 [!code-csharp[StructuredNavigationSample#ReturnCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#returncodebehind1)]
 [!code-vb[StructuredNavigationSample#ReturnCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#returncodebehind1)]  
[!code-csharp[StructuredNavigationSample#ReturnCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#returncodebehind2)]
[!code-vb[StructuredNavigationSample#ReturnCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#returncodebehind2)]  
  
 Neste exemplo, se um usuário pressiona o botão Cancelar, um valor de `null` é retornado para a página chamadora. Se, em vez disso, o botão OK for pressionado, será retornado o valor de cadeia de caracteres fornecido pelo usuário. <xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A> é um `protected virtual` método que você pode chamar para retornar os dados para a página chamadora. Os dados precisam ser empacotados em uma instância do genérica <xref:System.Windows.Navigation.ReturnEventArgs%601> tipo, cujo argumento de tipo Especifica o tipo de valor que <xref:System.Windows.Navigation.ReturnEventArgs%601.Result%2A> retorna. Dessa forma, quando você declara uma <xref:System.Windows.Navigation.PageFunction%601> com um argumento de tipo específico, você está dizendo que um <xref:System.Windows.Navigation.PageFunction%601> retornará uma instância do tipo especificado pelo argumento de tipo. Neste exemplo, o argumento de tipo e, consequentemente, o valor retornado é do tipo <xref:System.String>.  
  
 Quando <xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A> é chamado, a página chamadora precisa alguma maneira de receber o valor de retorno de <xref:System.Windows.Navigation.PageFunction%601>. Por esse motivo, <xref:System.Windows.Navigation.PageFunction%601> implementa o <xref:System.Windows.Navigation.PageFunction%601.Return> eventos para chamar páginas para lidar com. Quando <xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A> é chamado, <xref:System.Windows.Navigation.PageFunction%601.Return> é gerado, portanto, a página chamadora pode registrar com <xref:System.Windows.Navigation.PageFunction%601.Return> para receber a notificação.  
  
 [!code-csharp[StructuredNavigationSample#ProcessResultCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#processresultcodebehind1)]
 [!code-vb[StructuredNavigationSample#ProcessResultCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#processresultcodebehind1)]  
[!code-csharp[StructuredNavigationSample#ProcessResultCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#processresultcodebehind2)]
[!code-vb[StructuredNavigationSample#ProcessResultCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#processresultcodebehind2)]  
  
### <a name="removing-task-pages-when-a-task-completes"></a>Removendo páginas de tarefa quando uma tarefa é concluída  
 Quando uma página chamada retorna, e o usuário não cancelou a página chamada, a página chamadora processará os dados fornecidos pelo usuário e também os retornados pela página chamada. A aquisição de dados dessa forma costuma ser uma atividade isolada. Quando a página chamada retorna, a página chamadora precisa criar e navegar até uma nova página chamadora para capturar mais dados.  
  
 No entanto, a menos que uma página chamada seja removida do diário, um usuário poderá navegar de volta para uma instância anterior da página chamadora. Se um <xref:System.Windows.Navigation.PageFunction%601> são mantidas no diário é determinado pelo <xref:System.Windows.Navigation.PageFunctionBase.RemoveFromJournal%2A> propriedade. Por padrão, uma função de página é automaticamente removido quando <xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A> é chamado porque <xref:System.Windows.Navigation.PageFunctionBase.RemoveFromJournal%2A> é definido como `true`. Para manter uma função de página no histórico de navegação após <xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A> é chamado, defina <xref:System.Windows.Navigation.PageFunctionBase.RemoveFromJournal%2A> para `false`.  
  
<a name="Other_Types_of_Structured_Navigation"></a>   
## <a name="other-types-of-structured-navigation"></a>Outros tipos de navegação estruturada  
 Este tópico ilustra o uso mais básico de um <xref:System.Windows.Navigation.PageFunction%601> dar suporte à chamada/retorno de navegação estruturada. Essa base fornece a capacidade para criar tipos mais complexos de navegação estruturada.  
  
 Por exemplo, algumas vezes várias páginas são exigidas pela página chamadora, para obter dados suficientes de um usuário ou para realizar uma tarefa. O uso de várias páginas é conhecido como um "assistente".  
  
 Em outros casos, os aplicativos podem ter topologias complexas de navegação que dependem da navegação estruturada para operar com eficiência. Para obter mais informações, consulte [Visão geral de topologias de navegação](../../../../docs/framework/wpf/app-development/navigation-topologies-overview.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Navigation.PageFunction%601>  
 <xref:System.Windows.Navigation.NavigationService>  
 [Visão geral de topologias de navegação](../../../../docs/framework/wpf/app-development/navigation-topologies-overview.md)
