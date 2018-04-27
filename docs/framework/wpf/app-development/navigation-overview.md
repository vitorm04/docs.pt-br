---
title: Visão geral de navegação
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- loose XAML files [WPF]
- windows [WPF]
- Start page [WPF]
- HTML files [WPF]
- structured navigation [WPF]
- fragment navigation [WPF]
- URIs (Uniform Resource Identifiers)
- custom objects [WPF]
- Uniform Resource Identifiers (URIs)
- pages [WPF]
- frames [WPF]
- navigation hosts [WPF]
- journals [WPF]
- lifetimes [WPF]
- retaining content state [WPF]
- content state [WPF]
- programmatic navigation [WPF]
- hyperlinks [WPF]
ms.assetid: 86ad2143-606a-4e34-bf7e-51a2594248b8
caps.latest.revision: 69
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 07609671d061851e6ede2f2bd90e4bee38e43159
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="navigation-overview"></a>Visão geral de navegação
[!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] dá suporte à navegação de estilo de navegador que pode ser usada em dois tipos de aplicativos: aplicativos autônomos e [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)]. Para conteúdo do pacote para navegação, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] fornece o <xref:System.Windows.Controls.Page> classe. Você pode navegar de um <xref:System.Windows.Controls.Page> para outra declarativamente, usando um <xref:System.Windows.Documents.Hyperlink>, ou programaticamente, usando o <xref:System.Windows.Navigation.NavigationService>. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] usa o diário para lembrar as páginas que foram navegadas e navegar de volta para elas.  
  
 <xref:System.Windows.Controls.Page>, <xref:System.Windows.Documents.Hyperlink>, <xref:System.Windows.Navigation.NavigationService>, e o diário de formam o núcleo do suporte a navegação oferecido por [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. Esta visão geral explora esses recursos detalhadamente antes de abranger suporte a navegação avançada que inclui a navegação perder [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] arquivos, [!INCLUDE[TLA#tla_html](../../../../includes/tlasharptla-html-md.md)] arquivos e objetos.  
  
> [!NOTE]
>  Neste tópico, o termo "browser" refere-se somente aos navegadores que podem hospedar [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplicativos, que atualmente inclui [!INCLUDE[TLA#tla_ie](../../../../includes/tlasharptla-ie-md.md)] e Firefox. Onde específico [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] recursos têm suporte apenas por um navegador em particular, a versão do navegador é chamada.  
   
     
## <a name="navigation-in-wpf-applications"></a>Navegação em aplicativos WPF  
 Este tópico fornece uma visão geral dos recursos de navegação principais no [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. Esses recursos estão disponíveis para os dois aplicativos autônomos e [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)], embora este tópico apresenta dentro do contexto de um [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)].  
  
> [!NOTE]
>  Este tópico não aborda como criar e implantar [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]. Para obter mais informações sobre [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)], consulte [visão geral sobre aplicativos de navegador XAML WPF](../../../../docs/framework/wpf/app-development/wpf-xaml-browser-applications-overview.md).  
  
 Esta seção explica e demonstra os seguintes aspectos da navegação:  
  
-   [Implementar uma página](#CreatingAXAMLPage)  
  
-   [Configurar uma página inicial](#Configuring_a_Start_Page)  
  
-   [Configurar o título, largura e altura da janela do host](#ConfiguringAXAMLPage)  
  
-   [Navegação de hiperlink](#NavigatingBetweenXAMLPages)  
  
-   [Navegação de fragmento](#FragmentNavigation)  
  
-   [Serviço de navegação](#NavigationService)  
  
-   [Navegação programática com o serviço de navegação](#Programmatic_Navigation_with_the_Navigation_Service)  
  
-   [Tempo de vida de navegação](#Navigation_Lifetime)  
  
-   [Memorizar a navegação com o diário](#NavigationHistory)  
  
-   [Tempo de vida da página e o diário](#PageLifetime)  
  
-   [Reter o estado de conteúdo com o histórico de navegação](#RetainingContentStateWithNavigationHistory)  
  
-   [Cookies](#Cookies)  
  
-   [Navegação estruturada](#Structured_Navigation)  
  
<a name="CreatingAXAMLPage"></a>   
### <a name="implementing-a-page"></a>Implementar uma página  
 Em [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], você pode navegar para vários tipos de conteúdo que incluem [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] objetos, objetos personalizados, valores de enumeração, controles de usuário, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] arquivos, e [!INCLUDE[TLA#tla_html](../../../../includes/tlasharptla-html-md.md)] arquivos. No entanto, você descobrirá que a forma mais comum e conveniente de conteúdo do pacote é usando <xref:System.Windows.Controls.Page>. Além disso, <xref:System.Windows.Controls.Page> implementa recursos específicos de navegação para aprimorar sua aparência e simplificar o desenvolvimento.  
  
 Usando <xref:System.Windows.Controls.Page>, declarativamente, você pode implementar uma página navegável de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] conteúdo usando marcação semelhante ao seguinte.  
  
 [!code-xaml[NavigationOverviewSnippets#Page1XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/Page1.xaml#page1xaml)]  
  
 Um <xref:System.Windows.Controls.Page> que é implementada no [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] marcação tem `Page` como seu elemento raiz e requer o [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] declaração de namespace. O `Page` elemento contém o conteúdo que você deseja navegar e exibir. Adicionar conteúdo definindo o `Page.Content` elemento de propriedade, conforme mostrado na seguinte marcação.  
  
 [!code-xaml[NavigationOverviewSnippets#Page2XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/Page2.xaml#page2xaml)]  
  
 `Page.Content` só pode conter um elemento filho; no exemplo anterior, o conteúdo é uma única cadeia de caracteres, "Hello, Page!" Na prática, você normalmente usará um controle de layout como o elemento filho (consulte [Layout](../../../../docs/framework/wpf/advanced/layout.md)) para conter e redigir o conteúdo.  
  
 Os elementos filho de um `Page` elemento são considerados como o conteúdo de um <xref:System.Windows.Controls.Page> e, consequentemente, você não precisa usar explícita `Page.Content` declaração. A marcação a seguir é o equivalente declarativo da amostra anterior.  
  
 [!code-xaml[NavigationOverviewSnippets#Page3XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/Page3.xaml#page3xaml)]  
  
 Nesse caso, `Page.Content` é definido automaticamente com os elementos filho do `Page` elemento. Para obter mais informações, consulte [Modelo de conteúdo do WPF](../../../../docs/framework/wpf/controls/wpf-content-model.md).  
  
 Uma marcação somente <xref:System.Windows.Controls.Page> é útil para exibir o conteúdo. No entanto, um <xref:System.Windows.Controls.Page> também pode exibir os controles que permitem aos usuários interagir com a página, e ele pode responder à interação do usuário manipulando eventos e chamando a lógica do aplicativo. Interativo <xref:System.Windows.Controls.Page> é implementada usando uma combinação de marcação e code-behind, conforme mostrado no exemplo a seguir.  
  
 [!code-xaml[XBAPAppDefSnippets#HomePageMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppDefSnippets/CSharp/HomePage.xaml#homepagemarkup)]  
  
 [!code-csharp[XBAPAppDefSnippets#HomePageCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppDefSnippets/CSharp/HomePage.xaml.cs#homepagecodebehind)]
 [!code-vb[XBAPAppDefSnippets#HomePageCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/XBAPAppDefSnippets/VisualBasic/HomePage.xaml.vb#homepagecodebehind)]  
  
 Para permitir que um arquivo de marcação e o arquivo code-behind funcionem juntos, a seguinte configuração é necessária:  
  
-   Na marcação, o `Page` elemento deve incluir o `x:Class` atributo. Quando o aplicativo é construído, a existência de `x:Class` na marcação arquivo faz com que [!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)] para criar um `partial` classe que deriva de <xref:System.Windows.Controls.Page> e tem o nome especificado pelo `x:Class` atributo. Isso requer a adição de um [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] declaração de namespace para o [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] esquema ( `xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"` ). Gerado `partial` classe implementa `InitializeComponent`, que é chamado para registrar os eventos e definir as propriedades que são implementadas na marcação.  
  
-   No code-behind, a classe deve ser um `partial` classe com o mesmo nome que é especificado pelo `x:Class` atributo na marcação e deve ser derivado de <xref:System.Windows.Controls.Page>. Isso permite que o arquivo de code-behind deve ser associado a `partial` classe gerada para o arquivo de marcação quando o aplicativo é compilado (consulte [criando um aplicativo WPF](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md)).  
  
-   No code-behind, o <xref:System.Windows.Controls.Page> classe deve implementar um construtor que chama o `InitializeComponent` método. `InitializeComponent` é implementado pela marcação gerada do arquivo `partial` classe para registrar eventos e definir propriedades que são definidas na marcação.  
  
> [!NOTE]
>  Quando você adiciona um novo <xref:System.Windows.Controls.Page> ao seu projeto usando [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], o <xref:System.Windows.Controls.Page> é implementada usando marcação e lógica, e inclui a configuração necessária para criar a associação entre os arquivos de marcação e code-behind como descritos aqui.  
  
 Depois que você tiver um <xref:System.Windows.Controls.Page>, você pode navegar para ela. Para especificar o primeiro <xref:System.Windows.Controls.Page> que um aplicativo navega, você precisa configurar o início <xref:System.Windows.Controls.Page>.  
  
<a name="Configuring_a_Start_Page"></a>   
### <a name="configuring-a-start-page"></a>Configurar uma página inicial  
 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] exige que uma certa quantidade de infraestrutura de aplicativos sejam hospedados em um navegador. Em [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], o <xref:System.Windows.Application> classe faz parte de uma definição de aplicativo que estabelece a infra-estrutura de aplicativo necessário (consulte [visão geral do gerenciamento de aplicativo](../../../../docs/framework/wpf/app-development/application-management-overview.md)).  
  
 Uma definição de aplicativo normalmente é implementada usando marcação e o code-behind com o arquivo de marcação configurado como um [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `ApplicationDefinition` item. A seguir está uma definição de aplicativo para um [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)].  
  
 [!code-xaml[XBAPAppDefSnippets#XBAPApplicationDefinitionMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppDefSnippets/CSharp/App.xaml#xbapapplicationdefinitionmarkup)]  
  
 [!code-csharp[XBAPAppDefSnippets#XBAPApplicationDefinitionCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppDefSnippets/CSharp/App.xaml.cs#xbapapplicationdefinitioncodebehind)]
 [!code-vb[XBAPAppDefSnippets#XBAPApplicationDefinitionCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/XBAPAppDefSnippets/VisualBasic/Application.xaml.vb#xbapapplicationdefinitioncodebehind)]  
  
 Um [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] pode usar sua definição de aplicativo para especificar um início <xref:System.Windows.Controls.Page>, que é o <xref:System.Windows.Controls.Page> que é carregado automaticamente quando o [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] é iniciado. Você pode fazer isso definindo o <xref:System.Windows.Application.StartupUri%2A> propriedade com o [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] para desejado <xref:System.Windows.Controls.Page>.  
  
> [!NOTE]
>  Na maioria dos casos, o <xref:System.Windows.Controls.Page> é compilado ou implantado em um aplicativo. Nesses casos, o [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] que identifica um <xref:System.Windows.Controls.Page> é um pacote de [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)], que é um [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] que está em conformidade com a *pacote* esquema. Pacote de [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] são discutidas mais [URIs de pacote no WPF](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md). Você também pode navegar para o conteúdo usando o esquema http, que é discutido abaixo.  
  
 Você pode definir <xref:System.Windows.Application.StartupUri%2A> declarativamente na marcação, como mostrado no exemplo a seguir.  
  
 [!code-xaml[NavigationOverviewSnippets#XBAPApplicationDefinitionMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/App.xaml#xbapapplicationdefinitionmarkup)]  
  
 Neste exemplo, o `StartupUri` atributo é definido com um pacote relativo [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] que identifica HomePage. Quando o [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] é iniciado, HomePage é direcionada e exibidos automaticamente. Isso é demonstrado pela figura a seguir, que mostra um [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] que foi iniciado de um servidor Web.  
  
 ![Página XBAP](../../../../docs/framework/wpf/app-development/media/navigationoverviewfigure9.png "NavigationOverviewFigure9")  
  
> [!NOTE]
>  Para obter mais informações sobre o desenvolvimento e implantação de [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)], consulte [visão geral sobre aplicativos de navegador XAML WPF](../../../../docs/framework/wpf/app-development/wpf-xaml-browser-applications-overview.md) e [Implantando um aplicativo do WPF](../../../../docs/framework/wpf/app-development/deploying-a-wpf-application-wpf.md).  
  
<a name="ConfiguringAXAMLPage"></a>   
### <a name="configuring-the-host-windows-title-width-and-height"></a>Configurar o título, largura e altura da janela do host  
 Uma coisa que você pode ter observado da figura anterior é que o título do navegador e o painel Guia de [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] para o [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]. Além de ser longo, o título não é atraente nem informativo. Por esse motivo, <xref:System.Windows.Controls.Page> oferece uma maneira de alterar o título, definindo o <xref:System.Windows.Controls.Page.WindowTitle%2A> propriedade. Além disso, você pode configurar a largura e altura da janela do navegador definindo <xref:System.Windows.Controls.Page.WindowWidth%2A> e <xref:System.Windows.Controls.Page.WindowHeight%2A>, respectivamente.  
  
 <xref:System.Windows.Controls.Page.WindowTitle%2A>, <xref:System.Windows.Controls.Page.WindowWidth%2A>, e <xref:System.Windows.Controls.Page.WindowHeight%2A> pode ser definida declarativamente na marcação, como mostrado no exemplo a seguir.  
  
 [!code-xaml[NavigationOverviewSnippets#HomePageMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/HomePage.xaml#homepagemarkup)]  
  
 O resultado é mostrado na figura a seguir.  
  
 ![Título, altura e largura da janela](../../../../docs/framework/wpf/app-development/media/navigationoverviewfigure2.png "NavigationOverviewFigure2")  
  
<a name="NavigatingBetweenXAMLPages"></a>   
### <a name="hyperlink-navigation"></a>Navegação de hiperlink  
 Um típico [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] consiste em várias páginas. A maneira mais simples para navegar de uma página para outra é usar um <xref:System.Windows.Documents.Hyperlink>. Você pode adicionar declarativamente uma <xref:System.Windows.Documents.Hyperlink> para um <xref:System.Windows.Controls.Page> usando o `Hyperlink` elemento, que é mostrado na seguinte marcação.  
  
 [!code-xaml[NavigationOverviewSnippets#HyperlinkXAML1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml1)]  
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml2)]  
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml3)]  
  
 Um `Hyperlink` elemento requer o seguinte:  
  
-   O pacote de [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] do <xref:System.Windows.Controls.Page> para navegar, conforme especificado pelo `NavigateUri` atributo.  
  
-   Conteúdo que um usuário pode clicar para iniciar a navegação, como texto e imagens (para o conteúdo que o `Hyperlink` elemento pode conter, consulte <xref:System.Windows.Documents.Hyperlink>).  
  
 A figura a seguir mostra um [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] com um <xref:System.Windows.Controls.Page> que tem um <xref:System.Windows.Documents.Hyperlink>.  
  
 ![Página com hiperlink](../../../../docs/framework/wpf/app-development/media/navigationoverviewfigure3.png "NavigationOverviewFigure3")  
  
 Como você esperaria, clicar no <xref:System.Windows.Documents.Hyperlink> faz com que o [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] para navegar até o <xref:System.Windows.Controls.Page> que é identificado pelo `NavigateUri` atributo. Além disso, o [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] adiciona uma entrada para o anterior <xref:System.Windows.Controls.Page> à lista de páginas recentes na [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)]. Isso será mostrado na figura a seguir.  
  
 ![Botões Voltar e Avançar](../../../../docs/framework/wpf/app-development/media/navigationoverviewfigure4.png "NavigationOverviewFigure4")  
  
 Bem como suporte de navegação de um <xref:System.Windows.Controls.Page> para outra, <xref:System.Windows.Documents.Hyperlink> também dá suporte à navegação de fragmento.  
  
<a name="FragmentNavigation"></a>   
### <a name="fragment-navigation"></a>Navegação de fragmento  
 *Navegação de fragmento* é a navegação para um fragmento de conteúdo no atual <xref:System.Windows.Controls.Page> ou outro <xref:System.Windows.Controls.Page>. Em [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], um fragmento de conteúdo é o conteúdo que está contido por um elemento nomeado. Um elemento nomeado é um elemento que tem seu `Name` conjunto de atributos. A marcação a seguir mostra um conjunto nomeado `TextBlock` elemento que contém um fragmento de conteúdo.  
  
 [!code-xaml[NavigationOverviewSnippets#PageWithContentFragmentsMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithFragments.xaml#pagewithcontentfragmentsmarkup1)]  
[!code-xaml[NavigationOverviewSnippets#PageWithContentFragmentsMARKUP2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithFragments.xaml#pagewithcontentfragmentsmarkup2)]  
[!code-xaml[NavigationOverviewSnippets#PageWithContentFragmentsMARKUP3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithFragments.xaml#pagewithcontentfragmentsmarkup3)]  
  
 Para uma <xref:System.Windows.Documents.Hyperlink> para navegar até um fragmento de conteúdo, o `NavigateUri` atributo deve incluir o seguinte:  
  
-   O [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] do <xref:System.Windows.Controls.Page> com o fragmento de conteúdo para navegar até.  
  
-   Um caractere "#".  
  
-   O nome do elemento no <xref:System.Windows.Controls.Page> que contém o fragmento de conteúdo.  
  
 Um fragmento [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] tem o seguinte formato.  
  
 *PageURI* `#` *ElementName*  
  
 A seguir mostra um exemplo de uma `Hyperlink` que está configurado para navegar até um fragmento de conteúdo.  
  
 [!code-xaml[NavigationOverviewSnippets#PageThatNavigatesXAML1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageThatNavigatesToFragment.xaml#pagethatnavigatesxaml1)]  
[!code-xaml[NavigationOverviewSnippets#PageThatNavigatesXAML2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageThatNavigatesToFragment.xaml#pagethatnavigatesxaml2)]  
[!code-xaml[NavigationOverviewSnippets#PageThatNavigatesXAML3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageThatNavigatesToFragment.xaml#pagethatnavigatesxaml3)]  
  
> [!NOTE]
>  Esta seção descreve a implementação padrão de navegação de fragmento no [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] também permite que você implemente seu próprio esquema de navegação de fragmento que, em parte, requer manipulação de <xref:System.Windows.Navigation.NavigationService.FragmentNavigation?displayProperty=nameWithType> eventos.  
  
> [!IMPORTANT]
>  Você pode navegar para fragmentos em perder [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] páginas (somente marcação [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] arquivos com `Page` como elemento raiz) somente se as páginas podem ser navegadas por meio de [!INCLUDE[TLA2#tla_http](../../../../includes/tla2sharptla-http-md.md)].  
>   
>  No entanto, um flexível [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] página pode navegar para seus próprios fragmentos.  
  
<a name="NavigationService"></a>   
### <a name="navigation-service"></a>Serviço de navegação  
 Enquanto <xref:System.Windows.Documents.Hyperlink> permite que um usuário iniciar a navegação para uma determinada <xref:System.Windows.Controls.Page>, o trabalho de localizar e baixar a página é executado a <xref:System.Windows.Navigation.NavigationService> classe. Essencialmente, <xref:System.Windows.Navigation.NavigationService> fornece a capacidade de processar uma solicitação de navegação em nome de código do cliente, como o <xref:System.Windows.Documents.Hyperlink>. Além disso, <xref:System.Windows.Navigation.NavigationService> implementa o suporte de alto nível para controlar e influenciar uma solicitação de navegação.  
  
 Quando um <xref:System.Windows.Documents.Hyperlink> é clicado, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] chamadas <xref:System.Windows.Navigation.NavigationService.Navigate%2A?displayProperty=nameWithType> para localizar e baixar o <xref:System.Windows.Controls.Page> no pacote especificado [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]. Baixado <xref:System.Windows.Controls.Page> é convertido em uma árvore de objetos cujo objeto raiz é uma instância do baixado <xref:System.Windows.Controls.Page>. Uma referência para a raiz <xref:System.Windows.Controls.Page> objeto é armazenado no <xref:System.Windows.Navigation.NavigationService.Content%2A?displayProperty=nameWithType> propriedade. O pacote de [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] para o conteúdo que foi direcionado é armazenado no <xref:System.Windows.Navigation.NavigationService.Source%2A?displayProperty=nameWithType> propriedade, enquanto o <xref:System.Windows.Navigation.NavigationService.CurrentSource%2A?displayProperty=nameWithType> armazena o pacote de [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] para a última página foi direcionada.  
  
> [!NOTE]
>  É possível que um [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplicativo tenha mais de um ativo no momento <xref:System.Windows.Navigation.NavigationService>. Para obter mais informações, consulte [Hosts de navegação](#Navigation_Hosts) mais adiante neste tópico.  
  
<a name="Programmatic_Navigation_with_the_Navigation_Service"></a>   
### <a name="programmatic-navigation-with-the-navigation-service"></a>Navegação programática com o serviço de navegação  
 Você não precisa saber sobre <xref:System.Windows.Navigation.NavigationService> se a navegação for implementada declarativamente na marcação usando <xref:System.Windows.Documents.Hyperlink>, pois <xref:System.Windows.Documents.Hyperlink> usa o <xref:System.Windows.Navigation.NavigationService> em seu nome. Isso significa que, desde que o pai direto ou indireto de um <xref:System.Windows.Documents.Hyperlink> é um host de navegação (consulte [Hosts de navegação](#Navigation_Hosts)), <xref:System.Windows.Documents.Hyperlink> será capaz de localizar e usar o serviço de navegação do host de navegação para processar um solicitação de navegação.  
  
 No entanto, há situações quando você precisa usar <xref:System.Windows.Navigation.NavigationService> diretamente, incluindo o seguinte:  
  
-   Quando você precisa criar uma instância de um <xref:System.Windows.Controls.Page> usando um construtor não padrão.  
  
-   Quando você precisa definir propriedades no <xref:System.Windows.Controls.Page> antes de navegar até ele.  
  
-   Quando o <xref:System.Windows.Controls.Page> que precisam ser navegados só pode ser determinado em tempo de execução.  
  
 Nessas situações, você precisa escrever código para iniciar navegação por programação chamando o <xref:System.Windows.Navigation.NavigationService.Navigate%2A> método o <xref:System.Windows.Navigation.NavigationService> objeto. Que requer a obtenção de uma referência a um <xref:System.Windows.Navigation.NavigationService>.  
  
#### <a name="getting-a-reference-to-the-navigationservice"></a>Obter uma referência para o NavigationService  
 Por razões que são abordados a [Hosts de navegação](#Navigation_Hosts) seção, uma [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplicativo pode ter mais de um <xref:System.Windows.Navigation.NavigationService>. Isso significa que seu código precisa de uma maneira de localizar um <xref:System.Windows.Navigation.NavigationService>, que é geralmente o <xref:System.Windows.Navigation.NavigationService> que navegou para atual <xref:System.Windows.Controls.Page>. Você pode obter uma referência a um <xref:System.Windows.Navigation.NavigationService> chamando o `static` <xref:System.Windows.Navigation.NavigationService.GetNavigationService%2A?displayProperty=nameWithType> método. Para obter o <xref:System.Windows.Navigation.NavigationService> que navegou para uma determinada <xref:System.Windows.Controls.Page>, você passar uma referência para o <xref:System.Windows.Controls.Page> como o argumento do <xref:System.Windows.Navigation.NavigationService.GetNavigationService%2A> método. O código a seguir mostra como obter o <xref:System.Windows.Navigation.NavigationService> atual <xref:System.Windows.Controls.Page>.  
  
 [!code-csharp[NavigationOverviewSnippets#GetNSCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/GetNSPage.xaml.cs#getnscodebehind1)]  
[!code-csharp[NavigationOverviewSnippets#GetNSCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/GetNSPage.xaml.cs#getnscodebehind2)]
[!code-vb[NavigationOverviewSnippets#GetNSCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/GetNSPage.xaml.vb#getnscodebehind2)]  
  
 Como um atalho para localizar o <xref:System.Windows.Navigation.NavigationService> para um <xref:System.Windows.Controls.Page>, <xref:System.Windows.Controls.Page> implementa o <xref:System.Windows.Controls.Page.NavigationService%2A> propriedade. Isso é mostrado no exemplo a seguir.  
  
 [!code-csharp[NavigationOverviewSnippets#GetNSShortcutCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/GetNSPageShortCut.xaml.cs#getnsshortcutcodebehind1)]  
[!code-csharp[NavigationOverviewSnippets#GetNSShortcutCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/GetNSPageShortCut.xaml.cs#getnsshortcutcodebehind2)]
[!code-vb[NavigationOverviewSnippets#GetNSShortcutCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/GetNSPageShortCut.xaml.vb#getnsshortcutcodebehind2)]  
  
> [!NOTE]
>  Um <xref:System.Windows.Controls.Page> só pode obter uma referência a seu <xref:System.Windows.Navigation.NavigationService> quando <xref:System.Windows.Controls.Page> gera o <xref:System.Windows.FrameworkElement.Loaded> evento.  
  
#### <a name="programmatic-navigation-to-a-page-object"></a>Navegação programática para um objeto de página  
 O exemplo a seguir mostra como usar o <xref:System.Windows.Navigation.NavigationService> para navegar por meio de programação para um <xref:System.Windows.Controls.Page>. Navegação através de programação é necessária porque o <xref:System.Windows.Controls.Page> que é sendo navegado só pode ser instanciado usando um único construtor não padrão. O <xref:System.Windows.Controls.Page> com o construtor padrão não é mostrado na seguinte marcação e código.  
  
 [!code-xaml[NavigationOverviewSnippets#PageWithNonDefaultConstructorXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithNonDefaultConstructor.xaml#pagewithnondefaultconstructorxaml)]  
  
 [!code-csharp[NavigationOverviewSnippets#PageWithNonDefaultConstructorCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithNonDefaultConstructor.xaml.cs#pagewithnondefaultconstructorcodebehind)]
 [!code-vb[NavigationOverviewSnippets#PageWithNonDefaultConstructorCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/PageWithNonDefaultConstructor.xaml.vb#pagewithnondefaultconstructorcodebehind)]  
  
 O <xref:System.Windows.Controls.Page> que navega para o <xref:System.Windows.Controls.Page> com o construtor padrão não é mostrado na seguinte marcação e código.  
  
 [!code-xaml[NavigationOverviewSnippets#NSNavigationPageXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSNavigationPage.xaml#nsnavigationpagexaml)]  
  
 [!code-csharp[NavigationOverviewSnippets#NSNavigationPageCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSNavigationPage.xaml.cs#nsnavigationpagecodebehind)]
 [!code-vb[NavigationOverviewSnippets#NSNavigationPageCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/NSNavigationPage.xaml.vb#nsnavigationpagecodebehind)]  
  
 Quando o <xref:System.Windows.Documents.Hyperlink> neste <xref:System.Windows.Controls.Page> é clicado, a navegação é iniciada criando uma instância de <xref:System.Windows.Controls.Page> para navegar usando o construtor não padrão e chamar o <xref:System.Windows.Navigation.NavigationService.Navigate%2A?displayProperty=nameWithType> método. <xref:System.Windows.Navigation.NavigationService.Navigate%2A> aceita uma referência ao objeto que o <xref:System.Windows.Navigation.NavigationService> navegará, em vez de um pacote de [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].  
  
#### <a name="programmatic-navigation-with-a-pack-uri"></a>Navegação programática com um URI "pack://"  
 Se você precisar criar um pacote de [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] programaticamente (quando você somente pode determinar o pacote [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] em tempo de execução, por exemplo), você pode usar o <xref:System.Windows.Navigation.NavigationService.Navigate%2A?displayProperty=nameWithType> método. Isso é mostrado no exemplo a seguir.  
  
 [!code-xaml[NavigationOverviewSnippets#NSUriNavigationPageXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSUriNavigationPage.xaml#nsurinavigationpagexaml)]  
  
 [!code-csharp[NavigationOverviewSnippets#NSUriNavigationPageCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSUriNavigationPage.xaml.cs#nsurinavigationpagecodebehind)]
 [!code-vb[NavigationOverviewSnippets#NSUriNavigationPageCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/NSUriNavigationPage.xaml.vb#nsurinavigationpagecodebehind)]  
  
#### <a name="refreshing-the-current-page"></a>Atualizar a página atual  
 Um <xref:System.Windows.Controls.Page> não é baixado, se ele tem o mesmo pacote [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] como o pacote de [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] que é armazenado no <xref:System.Windows.Navigation.NavigationService.Source%2A?displayProperty=nameWithType> propriedade. Para forçar [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] para baixar a página atual novamente, você pode chamar o <xref:System.Windows.Navigation.NavigationService.Refresh%2A?displayProperty=nameWithType> método, conforme mostrado no exemplo a seguir.  
  
 [!code-xaml[NavigationOverviewSnippets#NSRefreshNavigationPageXAML1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSRefreshNavigationPage.xaml#nsrefreshnavigationpagexaml1)]  
  
 [!code-csharp[NavigationOverviewSnippets#NSRefreshNavigationPageCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSRefreshNavigationPage.xaml.cs#nsrefreshnavigationpagecodebehind1)]
 [!code-vb[NavigationOverviewSnippets#NSRefreshNavigationPageCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/NSRefreshNavigationPage.xaml.vb#nsrefreshnavigationpagecodebehind1)]  
[!code-csharp[NavigationOverviewSnippets#NSRefreshNavigationPageCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSRefreshNavigationPage.xaml.cs#nsrefreshnavigationpagecodebehind2)]
[!code-vb[NavigationOverviewSnippets#NSRefreshNavigationPageCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/NSRefreshNavigationPage.xaml.vb#nsrefreshnavigationpagecodebehind2)]  
  
<a name="Navigation_Lifetime"></a>   
### <a name="navigation-lifetime"></a>Tempo de vida de navegação  
 Como você viu, há várias maneiras de iniciar a navegação. Quando a navegação é iniciada, e enquanto a navegação está em andamento, você pode controlar e influenciar a navegação usando os seguintes eventos são implementados pelo <xref:System.Windows.Navigation.NavigationService>:  
  
-   <xref:System.Windows.Navigation.NavigationService.Navigating>. Ocorre quando uma nova navegação é solicitada. Pode ser usado para cancelar a navegação.  
  
-   <xref:System.Windows.Navigation.NavigationService.NavigationProgress>. Ocorre periodicamente durante um download para fornecer informações sobre o andamento da navegação.  
  
-   <xref:System.Windows.Navigation.NavigationService.Navigated>. Ocorre quando a página foi localizada e baixada.  
  
-   <xref:System.Windows.Navigation.NavigationService.NavigationStopped>. Ocorre quando a navegação é interrompida (chamando <xref:System.Windows.Navigation.NavigationService.StopLoading%2A>), ou quando é solicitada uma nova navegação enquanto uma navegação atual está em andamento.  
  
-   <xref:System.Windows.Navigation.NavigationService.NavigationFailed>. Ocorre quando um erro é gerado ao negar para o conteúdo solicitado.  
  
-   <xref:System.Windows.Navigation.NavigationService.LoadCompleted>. Ocorre após carregar, analisar o conteúdo para o qual se navegou e iniciar sua renderização.  
  
-   <xref:System.Windows.Navigation.NavigationService.FragmentNavigation>. Ocorre quando a navegação para um fragmento de conteúdo começa, o que ocorre:  
  
    -   Imediatamente, se o fragmento desejado estiver no conteúdo atual.  
  
    -   Depois que o conteúdo de origem tiver sido carregado, se o fragmento desejado estiver em outro conteúdo.  
  
 Os eventos de navegação são acionados na ordem em que são ilustrados pela figura a seguir.  
  
 ![Fluxograma de navegação de página](../../../../docs/framework/wpf/app-development/media/navigationoverviewfigure11.png "NavigationOverviewFigure11")  
  
 Em geral, um <xref:System.Windows.Controls.Page> não se preocupa com esses eventos. É mais provável que um aplicativo esteja relacionado a eles e, por esse motivo, esses eventos são também gerados pelo <xref:System.Windows.Application> classe:  
  
-   <xref:System.Windows.Application.Navigating?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Application.NavigationProgress?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Application.Navigated?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Application.NavigationFailed?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Application.NavigationStopped?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Application.LoadCompleted?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Application.FragmentNavigation?displayProperty=nameWithType>  
  
 Sempre <xref:System.Windows.Navigation.NavigationService> gera um evento, o <xref:System.Windows.Application> classe gera o evento correspondente. <xref:System.Windows.Controls.Frame> e <xref:System.Windows.Navigation.NavigationWindow> oferecem os mesmos eventos para detectar navegação em seus respectivos escopos.  
  
 Em alguns casos, um <xref:System.Windows.Controls.Page> podem se interessar por esses eventos. Por exemplo, um <xref:System.Windows.Controls.Page> pode tratar o <xref:System.Windows.Navigation.NavigationService.Navigating?displayProperty=nameWithType> evento para determinar se deve ou não cancelar a navegação para fora dela. Isso é mostrado no exemplo a seguir.  
  
 [!code-xaml[NavigationOverviewSnippets#CancelNavigationPageXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/CancelNavigationPage.xaml#cancelnavigationpagexaml)]  
  
 [!code-csharp[NavigationOverviewSnippets#CancelNavigationPageCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/CancelNavigationPage.xaml.cs#cancelnavigationpagecodebehind)]
 [!code-vb[NavigationOverviewSnippets#CancelNavigationPageCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/CancelNavigationPage.xaml.vb#cancelnavigationpagecodebehind)]  
  
 Se você registrar um manipulador com um evento de navegação de um <xref:System.Windows.Controls.Page>, assim como no exemplo anterior, você deve também cancelar o registro do manipulador de eventos. Se você não fizer isso, pode haver efeitos colaterais em relação a como [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] navegação lembra <xref:System.Windows.Controls.Page> usando o diário de navegação.  
  
<a name="NavigationHistory"></a>   
### <a name="remembering-navigation-with-the-journal"></a>Memorizar a navegação com o diário  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] usa duas pilhas para memorizar as páginas pelas quais você navegou: uma pilha voltar e uma pilha avançar. Quando você navegar da atual <xref:System.Windows.Controls.Page> para um novo <xref:System.Windows.Controls.Page> frente a um existente ou <xref:System.Windows.Controls.Page>, atual <xref:System.Windows.Controls.Page> é adicionada para o *pilha voltar*. Quando você navegar da atual <xref:System.Windows.Controls.Page> para a versão anterior <xref:System.Windows.Controls.Page>, atual <xref:System.Windows.Controls.Page> é adicionada para o *pilha Avançar*. Nos referimos ao conjunto composto pela pilha voltar, a pilha avançar e a funcionalidade para gerenciá-las como o diário. Cada item na pilha de volta e a pilha de avanço é uma instância do <xref:System.Windows.Navigation.JournalEntry> classe e é conhecido como um *entrada do diário*.  
  
#### <a name="navigating-the-journal-from-internet-explorer"></a>Navegando pelo diário no Internet Explorer  
 Conceitualmente, o diário funciona da mesma forma que o **novamente** e **Forward** botões [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)] fazer. Eles serão mostrados na figura a seguir.  
  
 ![Botões Voltar e Avançar](../../../../docs/framework/wpf/app-development/media/navigationoverviewfigure4.png "NavigationOverviewFigure4")  
  
 Para [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] que são hospedadas por [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)], [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] integra o diário de navegação [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] de [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)]. Isso permite aos usuários navegar pelas páginas em um [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] usando o **novamente**, **Forward**, e **páginas recentes** botões [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)]. O diário não está integrado ao [!INCLUDE[TLA2#tla_ie6](../../../../includes/tla2sharptla-ie6-md.md)] da mesma maneira para [!INCLUDE[TLA2#tla_ie7](../../../../includes/tla2sharptla-ie7-md.md)] ou Internet Explorer 8. Em vez disso, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] renderiza uma navegação substituto [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
> [!IMPORTANT]
>  Em [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)], quando um usuário navega de e para um [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)], somente as entradas de diário para páginas que não foram mantidas ativas são mantidas no diário. Para discussão sobre como manter páginas ativas, consulte [tempo de vida da página e o diário de](#PageLifetime) mais adiante neste tópico.  
  
 Por padrão, o texto para cada <xref:System.Windows.Controls.Page> que aparece no **páginas recentes** lista de [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)] é o [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] para o <xref:System.Windows.Controls.Page>. Em muitos casos, isso não é especialmente significativo para o usuário. Felizmente, você pode alterar o texto usando uma das seguintes opções:  
  
1.  O anexo `JournalEntry.Name` valor do atributo.  
  
2.  O `Page.Title` valor do atributo.  
  
3.  O `Page.WindowTitle` valor de atributo e o [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] atual <xref:System.Windows.Controls.Page>.  
  
4.  O [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] atual <xref:System.Windows.Controls.Page>. (Padrão)  
  
 A ordem na qual as opções estão listadas coincide com a ordem de precedência para localizar o texto. Por exemplo, se `JournalEntry.Name` estiver definido, os outros valores são ignorados.  
  
 O exemplo a seguir usa o `Page.Title` atributo para alterar o texto que aparece para uma entrada de diário.  
  
 [!code-xaml[NavigationOverviewSnippets#PageTitleMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithTitle.xaml#pagetitlemarkup1)]  
[!code-xaml[NavigationOverviewSnippets#PageTitleMARKUP2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithTitle.xaml#pagetitlemarkup2)]  
  
 [!code-csharp[NavigationOverviewSnippets#PageTitleCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithTitle.xaml.cs#pagetitlecodebehind1)]
 [!code-vb[NavigationOverviewSnippets#PageTitleCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/PageWithTitle.xaml.vb#pagetitlecodebehind1)]  
[!code-csharp[NavigationOverviewSnippets#PageTitleCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithTitle.xaml.cs#pagetitlecodebehind2)]
[!code-vb[NavigationOverviewSnippets#PageTitleCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/PageWithTitle.xaml.vb#pagetitlecodebehind2)]  
  
#### <a name="navigating-the-journal-using-wpf"></a>Navegando pelo diário usando WPF  
 Embora um usuário possa navegar diário usando o **novamente**, **Forward**, e **páginas recentes** em [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)], você também pode navegar o diário usando mecanismos de programáticos e declarativos fornecidos pelo [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. Um motivo para fazer isso é fornecer navegação personalizada [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] nas suas páginas.  
  
 Você pode adicionar declarativamente diário navegação suporte usando os comandos de navegação expostos pelo <xref:System.Windows.Input.NavigationCommands>. O exemplo a seguir demonstra como usar o `BrowseBack` comando de navegação.  
  
 [!code-xaml[NavigationOverviewSnippets#NavigationCommandsPageXAML1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NavigationCommandsPage.xaml#navigationcommandspagexaml1)]  
[!code-xaml[NavigationOverviewSnippets#NavigationCommandsPageXAML2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NavigationCommandsPage.xaml#navigationcommandspagexaml2)]  
[!code-xaml[NavigationOverviewSnippets#NavigationCommandsPageXAML3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NavigationCommandsPage.xaml#navigationcommandspagexaml3)]  
[!code-xaml[NavigationOverviewSnippets#NavigationCommandsPageXAML4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NavigationCommandsPage.xaml#navigationcommandspagexaml4)]  
  
 Você pode navegar por meio de programação diário usando um dos seguintes membros de <xref:System.Windows.Navigation.NavigationService> classe:  
  
-   <xref:System.Windows.Navigation.NavigationService.GoBack%2A>  
  
-   <xref:System.Windows.Navigation.NavigationService.GoForward%2A>  
  
-   <xref:System.Windows.Navigation.NavigationService.CanGoBack%2A>  
  
-   <xref:System.Windows.Navigation.NavigationService.CanGoForward%2A>  
  
 O diário também pode ser manipulado programaticamente, conforme discutido em [retendo estado de conteúdo com histórico de navegação](#RetainingContentStateWithNavigationHistory) mais adiante neste tópico.  
  
<a name="PageLifetime"></a>   
### <a name="page-lifetime-and-the-journal"></a>Tempo de vida da página e o diário  
 Considere um [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] com várias páginas que contêm conteúdo rico, incluindo gráficos, animações e mídia. O volume de memória de páginas como essas poderá ser muito grande, especialmente se mídia de áudio e vídeo for usada. Considerando que o diário de "lembra" páginas que foram navegada, como um [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] rapidamente pode consumir uma quantidade grande e perceptível de memória.  
  
 Por esse motivo, o comportamento padrão do diário é armazenar <xref:System.Windows.Controls.Page> metadados em cada entrada de diário em vez de uma referência a um <xref:System.Windows.Controls.Page> objeto. Quando uma entrada de diário é direcionada, seu <xref:System.Windows.Controls.Page> metadados são usados para criar uma nova instância do <xref:System.Windows.Controls.Page>. Como consequência, cada <xref:System.Windows.Controls.Page> que é navegada tem a vida útil é ilustrada pela figura a seguir.  
  
 ![Tempo de vida da página](../../../../docs/framework/wpf/app-development/media/navigationoverviewfigure10.PNG "NavigationOverviewFigure10")  
  
 Embora usar o comportamento de registro em log padrão pode economizar consumo de memória, o desempenho de processamento por página poderá ser reduzido; reinstanciar uma <xref:System.Windows.Controls.Page> pode ser demorada, especialmente se ela tiver muito conteúdo. Se você precisar manter um <xref:System.Windows.Controls.Page> instância no diário, você pode usar duas técnicas para fazer isso. Primeiro, você pode navegar para programaticamente um <xref:System.Windows.Controls.Page> objeto chamando o <xref:System.Windows.Navigation.NavigationService.Navigate%2A?displayProperty=nameWithType> método.  
  
 Em segundo lugar, você pode especificar que [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] mantém uma instância de um <xref:System.Windows.Controls.Page> no diário, definindo o <xref:System.Windows.Controls.Page.KeepAlive%2A> propriedade `true` (o padrão é `false`). Conforme mostrado no exemplo a seguir, você pode definir <xref:System.Windows.Controls.Page.KeepAlive%2A> declarativamente na marcação.  
  
 [!code-xaml[NavigationOverviewSnippets#KeepAlivePageXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/KeepAlivePage.xaml#keepalivepagexaml)]  
  
 O tempo de vida de um <xref:System.Windows.Controls.Page> que é mantida ativa é ligeiramente diferente de uma que não é. Na primeira vez que um <xref:System.Windows.Controls.Page> que é mantida ativa é direcionada, ele é instanciado como um <xref:System.Windows.Controls.Page> que não é mantida ativa. No entanto, como uma instância do <xref:System.Windows.Controls.Page> é mantido no diário, ele é nunca instanciado novamente, desde que ela permaneça no diário. Consequentemente, se um <xref:System.Windows.Controls.Page> tem lógica de inicialização que precisa ser chamado sempre que o <xref:System.Windows.Controls.Page> navega, você deverá movê-la a partir do construtor para um manipulador para o <xref:System.Windows.FrameworkElement.Loaded> evento. Conforme mostrado na figura a seguir, o <xref:System.Windows.FrameworkElement.Loaded> e <xref:System.Windows.FrameworkElement.Unloaded> eventos ainda são gerados sempre que uma <xref:System.Windows.Controls.Page> navega de e para, respectivamente.  
  
 ![Quando os eventos Loaded e Unloaded são acionados](../../../../docs/framework/wpf/app-development/media/navigationoverviewfigure17.png "NavigationOverviewFigure17")  
  
 Quando um <xref:System.Windows.Controls.Page> não é mantida ativa, você não deve fazer o seguinte:  
  
-   Armazenar uma referência nela ou qualquer parte dela.  
  
-   Registrar manipuladores de eventos com eventos que não são implementados por ela.  
  
 Fazer um deles criará referências que forçam a <xref:System.Windows.Controls.Page> a ser mantido na memória, mesmo depois que ele tiver sido removido do diário.  
  
 Em geral, você deve preferir o padrão <xref:System.Windows.Controls.Page> comportamento de não manter um <xref:System.Windows.Controls.Page> ativo. No entanto, isso tem implicações de estado que são discutidas na próxima seção.  
  
<a name="RetainingContentStateWithNavigationHistory"></a>   
### <a name="retaining-content-state-with-navigation-history"></a>Reter o estado de conteúdo com o histórico de navegação  
 Se um <xref:System.Windows.Controls.Page> não é mantida ativa, e ela tem controles que coletam dados de usuário, o que acontece com os dados se um usuário navega de e para o <xref:System.Windows.Controls.Page>? De uma perspectiva de experiência do usuário, o usuário deve ter a expectativa de ver os dados que inseriu anteriormente. Infelizmente, porque uma nova instância do <xref:System.Windows.Controls.Page> é criada com cada navegação, os controles que coletados os dados são instanciadas novamente e os dados serão perdidos.  
  
 Felizmente, o journal oferece suporte para memorizar dados entre <xref:System.Windows.Controls.Page> navegações, incluindo dados de controle. Especificamente, a entrada de diário para cada <xref:System.Windows.Controls.Page> atua como um contêiner temporário associado <xref:System.Windows.Controls.Page> estado. As etapas a seguir descrevem como esse suporte é usado quando um <xref:System.Windows.Controls.Page> é navegado:  
  
1.  Uma entrada atual <xref:System.Windows.Controls.Page> é adicionada para o diário.  
  
2.  O estado do <xref:System.Windows.Controls.Page> é armazenado com a entrada do diário para essa página, que é adicionada à pilha de volta.  
  
3.  O novo <xref:System.Windows.Controls.Page> para onde navegar.  
  
 Quando a página <xref:System.Windows.Controls.Page> é direcionada, usando o diário, as etapas a seguir ocorrem:  
  
1.  O <xref:System.Windows.Controls.Page> (a entrada do diário superior na pilha voltar) é instanciada.  
  
2.  O <xref:System.Windows.Controls.Page> é atualizada com o estado que foi armazenado com a entrada de diário para o <xref:System.Windows.Controls.Page>.  
  
3.  O <xref:System.Windows.Controls.Page> novamente para onde navegar.  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] automaticamente usa esse suporte quando os controles a seguir são usados em um <xref:System.Windows.Controls.Page>:  
  
-   <xref:System.Windows.Controls.CheckBox>  
  
-   <xref:System.Windows.Controls.ComboBox>  
  
-   <xref:System.Windows.Controls.Expander>  
  
-   <xref:System.Windows.Controls.Frame>  
  
-   <xref:System.Windows.Controls.ListBox>  
  
-   <xref:System.Windows.Controls.ListBoxItem>  
  
-   <xref:System.Windows.Controls.MenuItem>  
  
-   <xref:System.Windows.Controls.ProgressBar>  
  
-   <xref:System.Windows.Controls.RadioButton>  
  
-   <xref:System.Windows.Controls.Slider>  
  
-   <xref:System.Windows.Controls.TabControl>  
  
-   <xref:System.Windows.Controls.TabItem>  
  
-   <xref:System.Windows.Controls.TextBox>  
  
 Se um <xref:System.Windows.Controls.Page> usa esses controles, os dados inseridos neles são memorizados entre <xref:System.Windows.Controls.Page> navegações, conforme demonstrado a **cor favorita** <xref:System.Windows.Controls.ListBox> na figura a seguir.  
  
 ![Página com controles que memorizam o estado](../../../../docs/framework/wpf/app-development/media/navigationoverviewfigure13.png "NavigationOverviewFigure13")  
  
 Quando um <xref:System.Windows.Controls.Page> tem controles que não sejam aqueles na lista anterior, ou quando o estado é armazenado em objetos personalizados, você precisa para escrever código para fazer com que o diário lembrar o estado em <xref:System.Windows.Controls.Page> navegações.  
  
 Se você precisa memorizar pequenos pedaços de estado entre <xref:System.Windows.Controls.Page> navegações, você pode usar propriedades de dependência (consulte <xref:System.Windows.DependencyProperty>) que são configurados com o <xref:System.Windows.FrameworkPropertyMetadata.Journal%2A?displayProperty=nameWithType> sinalizador de metadados.  
  
 Se o estado que sua <xref:System.Windows.Controls.Page> precisa memorizar entre navegações compreende várias partes de dados, talvez seja menos código intensiva encapsular seu estado em uma única classe e implementar o <xref:System.Windows.Navigation.IProvideCustomContentState> interface.  
  
 Se você precisa navegar pelos diversos estados de uma única <xref:System.Windows.Controls.Page>, sem navegar do <xref:System.Windows.Controls.Page> em si, você pode usar <xref:System.Windows.Navigation.IProvideCustomContentState> e <xref:System.Windows.Navigation.NavigationService.AddBackEntry%2A?displayProperty=nameWithType>.  
  
<a name="Cookies"></a>   
### <a name="cookies"></a>Cookies  
 Outra forma que [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplicativos podem armazenar dados é com cookies, que são criados, atualizadas e excluídas usando o <xref:System.Windows.Application.SetCookie%2A> e <xref:System.Windows.Application.GetCookie%2A> métodos. Os cookies que você pode criar no [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] são os mesmos cookies que outros tipos de aplicativos Web usam; cookies são pedaços arbitrários de dados que são armazenados por um aplicativo em um computador cliente durante ou nas sessões do aplicativo. Os dados do cookie normalmente assumem a forma de um par nome/valor no formato a seguir.  
  
 *Nome* `=` *Valor*  
  
 Quando os dados são passados para <xref:System.Windows.Application.SetCookie%2A>, juntamente com o <xref:System.Uri> do local para o qual o cookie deve ser definido, um cookie é criado na memória e só está disponível para a duração da sessão atual do aplicativo. Esse tipo de cookie é conhecido como um *cookie de sessão*.  
  
 Para armazenar um cookie entre sessões de aplicativo, uma data de validade deve ser adicionada ao cookie, usando o formato a seguir.  
  
 *NOME* `=` *VALOR* `; expires=DAY, DD-MMM-YYYY HH:MM:SS GMT`  
  
 Um cookie com uma data de expiração é armazenado no atual [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] pasta de arquivos temporários da Internet da instalação até que o cookie expira. Um cookie é conhecido como um *cookie persistente* porque ele persiste nas sessões do aplicativo.  
  
 Recuperar de sessão e cookies persistentes chamando o <xref:System.Windows.Application.GetCookie%2A> método, passando o <xref:System.Uri> do local onde o cookie foi definido com o <xref:System.Windows.Application.SetCookie%2A> método.  
  
 A seguir estão algumas das maneiras como os cookies são suportados em [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]:  
  
-   [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplicativos autônomos e [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] pode criar e gerenciar cookies.  
  
-   Cookies que são criados por um [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] pode ser acessado a partir do navegador.  
  
-   [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] do mesmo domínio podem criar e compartilhar cookies.  
  
-   [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] e [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] páginas do mesmo domínio podem criar e compartilhar cookies.  
  
-   Cookies são distribuídos quando [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] e flexível [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] páginas fazem solicitações da Web.  
  
-   Nível superior ambos [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] e [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] hospedados em IFRAMES podem acessar cookies.  
  
-   Suporte a cookie em [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] é o mesmo para todos os navegadores com suporte.  
  
-   Em [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)], política P3P relacionada aos cookies é aceita por [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], especialmente em relação à primários e de terceiros [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)].  
  
<a name="Structured_Navigation"></a>   
### <a name="structured-navigation"></a>Navegação estruturada  
 Se você precisar passar dados de uma <xref:System.Windows.Controls.Page> para outra, você pode passar os dados como argumentos para um construtor não padrão da <xref:System.Windows.Controls.Page>. Observe que se você usar essa técnica, você deve manter o <xref:System.Windows.Controls.Page> alive; se não, na próxima vez que você navegar para o <xref:System.Windows.Controls.Page>, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] reinstancia o <xref:System.Windows.Controls.Page> usando o construtor padrão.  
  
 Como alternativa, o <xref:System.Windows.Controls.Page> pode implementar propriedades que são definidas com os dados que precisam ser passadas. As coisas ficam complicadas, no entanto, quando um <xref:System.Windows.Controls.Page> precisam passar dados de volta para o <xref:System.Windows.Controls.Page> que navegou até ele. O problema é que navegação não oferece suporte a mecanismos para garantir que um <xref:System.Windows.Controls.Page> será retornado para depois que ele é navegado. Essencialmente, a navegação não dá suporte à semântica de chamada/retorno. Para resolver esse problema, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] fornece o <xref:System.Windows.Navigation.PageFunction%601> classe que você pode usar para garantir que um <xref:System.Windows.Controls.Page> é retornado de maneira previsível e estruturada. Para obter mais informações, consulte [visão geral de navegação estruturada](../../../../docs/framework/wpf/app-development/structured-navigation-overview.md).  
  
<a name="The_NavigationWindow_Class"></a>   
## <a name="the-navigationwindow-class"></a>A classe NavigationWindow  
 Neste ponto, você viu a gama de serviços de navegação que você provavelmente utilizará para criar aplicativos com conteúdo navegável. Esses serviços foram discutidos no contexto de [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)], embora eles não estão limitados a [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]. Os sistemas operacionais modernos e aplicativos do Windows tirar proveito da experiência de navegador dos usuários modernos para incorporar navegação no estilo de navegador em aplicativos autônomos. Exemplos comuns incluem:  
  
-   **Dicionário de sinônimos de palavras**: navegue por opções de palavras.  
  
-   **Explorador de Arquivos**: navegar por arquivos e pastas.  
  
-   **Assistentes**: dividir uma tarefa complexa em várias páginas entre as quais se pode navegar. Um exemplo é o Assistente de componentes do Windows que manipula adição e remoção de recursos do Windows.  
  
 Para incorporar navegação no estilo de navegador em seus aplicativos autônomos, você pode usar o <xref:System.Windows.Navigation.NavigationWindow> classe. <xref:System.Windows.Navigation.NavigationWindow> deriva <xref:System.Windows.Window> e estende com o mesmo suporte de navegação que [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] fornecer. Você pode usar <xref:System.Windows.Navigation.NavigationWindow> como a janela principal do seu aplicativo autônomo ou como uma janela secundária, como uma caixa de diálogo.  
  
 Para implementar um <xref:System.Windows.Navigation.NavigationWindow>, assim como acontece com a maioria das classes de nível superior em [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] (<xref:System.Windows.Window>, <xref:System.Windows.Controls.Page>e assim por diante), você usa uma combinação de marcação e code-behind. Isso é mostrado no exemplo a seguir.  
  
 [!code-xaml[IntroToNavNavigationWindowSnippets#NavigationWindowMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/MainWindow.xaml#navigationwindowmarkup)]  
  
 [!code-csharp[IntroToNavNavigationWindowSnippets#NavigationWindowCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/MainWindow.xaml.cs#navigationwindowcodebehind)]
 [!code-vb[IntroToNavNavigationWindowSnippets#NavigationWindowCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/VisualBasic/MainWindow.xaml.vb#navigationwindowcodebehind)]  
  
 Esse código cria um <xref:System.Windows.Navigation.NavigationWindow> automaticamente que navega para um <xref:System.Windows.Controls.Page> (HomePage) quando o <xref:System.Windows.Navigation.NavigationWindow> é aberto. Se o <xref:System.Windows.Navigation.NavigationWindow> é a janela principal do aplicativo, você pode usar o `StartupUri` atributo para iniciá-lo. Isso é mostrado na marcação a seguir.  
  
 [!code-xaml[IntroToNavNavigationWindowSnippets#AppLaunchNavWindow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/App.xaml#applaunchnavwindow)]  
  
 A figura a seguir mostra o <xref:System.Windows.Navigation.NavigationWindow> como a janela principal de um aplicativo autônomo.  
  
 ![Uma janela principal](../../../../docs/framework/wpf/app-development/media/navigationoverviewfigure18.png "NavigationOverviewFigure18")  
  
 A figura, você pode ver que o <xref:System.Windows.Navigation.NavigationWindow> tem um título, mesmo que ele não foi definido no <xref:System.Windows.Navigation.NavigationWindow> código de implementação do exemplo anterior. Em vez disso, o título é definido usando o <xref:System.Windows.Controls.Page.WindowTitle%2A> propriedade, que é mostrada no código a seguir.  
  
 [!code-xaml[IntroToNavNavigationWindowSnippets#HomePageMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/HomePage.xaml#homepagemarkup1)]  
[!code-xaml[IntroToNavNavigationWindowSnippets#HomePageMARKUP2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/HomePage.xaml#homepagemarkup2)]  
  
 Definindo o <xref:System.Windows.Controls.Page.WindowWidth%2A> e <xref:System.Windows.Controls.Page.WindowHeight%2A> propriedades também afeta o <xref:System.Windows.Navigation.NavigationWindow>.  
  
 Geralmente, você implementa seu próprio <xref:System.Windows.Navigation.NavigationWindow> quando você precisa personalizar seu comportamento ou aparência. Se nada disso é necessário, você pode usar um atalho. Se você especificar o pacote [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] de um <xref:System.Windows.Controls.Page> como o <xref:System.Windows.Application.StartupUri%2A> em um aplicativo autônomo, <xref:System.Windows.Application> cria automaticamente um <xref:System.Windows.Navigation.NavigationWindow> para hospedar o <xref:System.Windows.Controls.Page>. A marcação a seguir mostra como habilitar isso.  
  
 [!code-xaml[IntroToNavNavigationWindowSnippets#AppLaunchPage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/AnotherApp.xaml#applaunchpage)]  
  
 Se você quiser uma janela do aplicativo secundário como uma caixa de diálogo para ser um <xref:System.Windows.Navigation.NavigationWindow>, você pode usar o código no exemplo a seguir para abri-lo.  
  
 [!code-csharp[IntroToNavNavigationWindowSnippets#CreateNWDialogBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/DialogOwnerWindow.xaml.cs#createnwdialogbox)]
 [!code-vb[IntroToNavNavigationWindowSnippets#CreateNWDialogBox](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/VisualBasic/DialogOwnerWindow.xaml.vb#createnwdialogbox)]  
  
 A figura a seguir mostra o resultado.  
  
 ![Uma caixa de diálogo](../../../../docs/framework/wpf/app-development/media/navigationoverviewfigure19.png "NavigationOverviewFigure19")  
  
 Como você pode ver, <xref:System.Windows.Navigation.NavigationWindow> exibe [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)]-estilo **novamente** e **Forward** botões que permitem aos usuários navegar o diário. Esses botões fornecem a mesma experiência do usuário, conforme mostrado na figura a seguir.  
  
 ![Botões Voltar e Avançar em NavigationWindow](../../../../docs/framework/wpf/app-development/media/navigationoverviewfigure20.png "NavigationOverviewFigure20")  
  
 Se suas páginas fornecem seus próprios suporte de navegação do journal e interface do usuário, você pode ocultar o **novamente** e **Forward** botões exibidos pela <xref:System.Windows.Navigation.NavigationWindow> , definindo o valor da <xref:System.Windows.Navigation.NavigationWindow.ShowsNavigationUI%2A> propriedade `false`.  
  
 Como alternativa, você pode usar o suporte a personalização em [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] para substituir o [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] do <xref:System.Windows.Navigation.NavigationWindow> em si.  
  
<a name="Frame_in_Standalone_Applications"></a>   
## <a name="the-frame-class"></a>A classe Frame  
 O navegador e <xref:System.Windows.Navigation.NavigationWindow> são janelas que hospedam conteúdo navegável. Em alguns casos, os aplicativos têm conteúdo que não precisa ser hospedado por uma janela inteira. Em vez disso, esse tipo de conteúdo pode ser hospedado dentro de outro conteúdo. Você pode inserir conteúdo navegável em outro conteúdo usando o <xref:System.Windows.Controls.Frame> classe. <xref:System.Windows.Controls.Frame> fornece o mesmo suporte como <xref:System.Windows.Navigation.NavigationWindow> e [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)].  
  
 O exemplo a seguir mostra como adicionar um <xref:System.Windows.Controls.Frame> para um <xref:System.Windows.Controls.Page> declarativamente usando o `Frame` elemento.  
  
 [!code-xaml[NavigationOverviewSnippets#FrameHostPageXAML1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPage.xaml#framehostpagexaml1)]  
[!code-xaml[NavigationOverviewSnippets#FrameHostPageXAML2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPage.xaml#framehostpagexaml2)]  
[!code-xaml[NavigationOverviewSnippets#FrameHostPageXAML3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPage.xaml#framehostpagexaml3)]  
  
 Essa marcação define o `Source` atributo do `Frame` elemento com um pacote de [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] para o <xref:System.Windows.Controls.Page> que o <xref:System.Windows.Controls.Frame> inicialmente deve navegar. A figura a seguir mostra um [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] com um <xref:System.Windows.Controls.Page> que tem um <xref:System.Windows.Controls.Frame> que navegou entre várias páginas.  
  
 ![Um quadro que navegou entre várias páginas](../../../../docs/framework/wpf/app-development/media/navigationoverviewfigure5.png "NavigationOverviewFigure5")  
  
 Você não precisa usar apenas <xref:System.Windows.Controls.Frame> dentro do conteúdo de um <xref:System.Windows.Controls.Page>. Também é comum para hospedar um <xref:System.Windows.Controls.Frame> dentro do conteúdo de um <xref:System.Windows.Window>.  
  
 Por padrão, <xref:System.Windows.Controls.Frame> usa apenas seu próprio diário na ausência de outro diário. Se um <xref:System.Windows.Controls.Frame> faz parte do conteúdo que está hospedado dentro de um <xref:System.Windows.Navigation.NavigationWindow> ou um [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)], <xref:System.Windows.Controls.Frame> usa o diário que pertence a <xref:System.Windows.Navigation.NavigationWindow> ou [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]. Às vezes, no entanto, um <xref:System.Windows.Controls.Frame> talvez precise ser responsável por seu próprio diário. Um motivo para isso é permitir a navegação de diário dentro das páginas que são hospedados por um <xref:System.Windows.Controls.Frame>. Isso é ilustrado pela figura a seguir.  
  
 ![Diagrama de páginas e quadro](../../../../docs/framework/wpf/app-development/media/navigationoverviewfigure7.png "NavigationOverviewFigure7")  
  
 Nesse caso, você pode configurar o <xref:System.Windows.Controls.Frame> para usar seu próprio diário, definindo o <xref:System.Windows.Controls.Frame.JournalOwnership%2A> propriedade o <xref:System.Windows.Controls.Frame> para <xref:System.Windows.Navigation.JournalOwnership.OwnsJournal>. Isso é mostrado na marcação a seguir.  
  
 [!code-xaml[NavigationOverviewSnippets#FrameHostPageOwnJournalXAML1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnJournal.xaml#framehostpageownjournalxaml1)]  
[!code-xaml[NavigationOverviewSnippets#FrameHostPageOwnJournalXAML2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnJournal.xaml#framehostpageownjournalxaml2)]  
[!code-xaml[NavigationOverviewSnippets#FrameHostPageOwnJournalXAML3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnJournal.xaml#framehostpageownjournalxaml3)]  
  
 A figura a seguir ilustra o efeito de navegar em um <xref:System.Windows.Controls.Frame> que usa seu próprio diário.  
  
 ![Um quadro que usa seu próprio diário](../../../../docs/framework/wpf/app-development/media/navigationoverviewfigure8.png "NavigationOverviewFigure8")  
  
 Observe que as entradas de diário são mostradas pelo painel de navegação [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] no <xref:System.Windows.Controls.Frame>, em vez de [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)].  
  
> [!NOTE]
>  Se um <xref:System.Windows.Controls.Frame> faz parte do conteúdo que está hospedado em um <xref:System.Windows.Window>, <xref:System.Windows.Controls.Frame> usa seu próprio diário e, consequentemente, exibe sua própria navegação [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
 Se a sua experiência de usuário requer um <xref:System.Windows.Controls.Frame> para fornecer seu próprio journal sem mostrar a navegação [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], você pode ocultar o painel de navegação [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] definindo o <xref:System.Windows.Controls.Frame.NavigationUIVisibility%2A> para <xref:System.Windows.Visibility.Hidden>. Isso é mostrado na marcação a seguir.  
  
 [!code-xaml[NavigationOverviewSnippets#FrameHostPageHidesUIXAML1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnHiddenJournal.xaml#framehostpagehidesuixaml1)]  
[!code-xaml[NavigationOverviewSnippets#FrameHostPageHidesUIXAML2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnHiddenJournal.xaml#framehostpagehidesuixaml2)]  
[!code-xaml[NavigationOverviewSnippets#FrameHostPageHidesUIXAML3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnHiddenJournal.xaml#framehostpagehidesuixaml3)]  
  
<a name="Navigation_Hosts"></a>   
## <a name="navigation-hosts"></a>Hosts de navegação  
 <xref:System.Windows.Controls.Frame> e <xref:System.Windows.Navigation.NavigationWindow> são classes que são conhecidas como hosts de navegação. Um *host navegação* é uma classe que pode navegar e exibir o conteúdo. Para fazer isso, cada host de navegação usa seus próprios <xref:System.Windows.Navigation.NavigationService> e diário. A construção básica de um host de navegação é mostrada na figura a seguir.  
  
 ![Diagramas do navegador](../../../../docs/framework/wpf/app-development/media/navigationoverviewfigure15.png "NavigationOverviewFigure15")  
  
 Essencialmente, isso permite <xref:System.Windows.Navigation.NavigationWindow> e <xref:System.Windows.Controls.Frame> para fornecer o mesmo suporte navegação que um [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] fornece quando hospedado no navegador.  
  
 Além de usar <xref:System.Windows.Navigation.NavigationService> e um diário, hosts de navegação implementam os mesmos membros que <xref:System.Windows.Navigation.NavigationService> implementa. Isso é ilustrado pela figura a seguir.  
  
 ![Um diário em um quadro e em uma NavigationWindow](../../../../docs/framework/wpf/app-development/media/naivgationoverviewfigure24.png "NaivgationOverviewFigure24")  
  
 Isso permite que você programe suporte a navegação diretamente em relação a eles. Você pode considerar isso se você precisa fornecer uma navegação personalizada [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] para um <xref:System.Windows.Controls.Frame> que é hospedado em um <xref:System.Windows.Window>. Além disso, os dois tipos implementam membros adicionais, relacionados a navegação, incluindo `BackStack` (<xref:System.Windows.Navigation.NavigationWindow.BackStack%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.Frame.BackStack%2A?displayProperty=nameWithType>) e `ForwardStack` (<xref:System.Windows.Navigation.NavigationWindow.ForwardStack%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.Frame.ForwardStack%2A?displayProperty=nameWithType>), que permitem enumerar as entradas de diário na parte traseira a pilha e a pilha de avanço, respectivamente.  
  
 Conforme mencionado anteriormente, mais de um diário pode existir dentro de um aplicativo. A figura a seguir fornece um exemplo de quando isso pode acontecer.  
  
 ![Vários diários dentro de um aplicativo](../../../../docs/framework/wpf/app-development/media/naivgationoverviewfigure25.png "NaivgationOverviewFigure25")  
  
<a name="Navigating_to_Content_Other_than_Pages"></a>   
## <a name="navigating-to-content-other-than-xaml-pages"></a>Navegar para conteúdo que não seja páginas XAML  
 Ao longo deste tópico, <xref:System.Windows.Controls.Page> e pacote [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] ter sido usado para demonstrar os vários recursos de navegação de [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. No entanto, um <xref:System.Windows.Controls.Page> que é compilado em um aplicativo não é o único tipo de conteúdo que pode ser acessado e pacote [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] não são a única maneira de identificar o conteúdo.  
  
 Como esta seção demonstra, você também pode navegar para perder [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] arquivos, [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] arquivos e objetos.  
  
<a name="Navigating_to_Loose_XAML_Files"></a>   
### <a name="navigating-to-loose-xaml-files"></a>Navegar para arquivos XAML flexíveis  
 Um flexível [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] é um arquivo com as seguintes características:  
  
-   Contém apenas [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] (ou seja, sem código).  
  
-   Tem uma declaração de namespace apropriada.  
  
-   Tem a extensão de nome de arquivo .xaml.  
  
 Por exemplo, considere o seguinte conteúdo que é armazenado como um flexível [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] arquivo Person.  
  
 [!code-xaml[NavigationOverviewSnippets#LooseXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/Person.xaml#loosexaml)]  
  
 Quando você clica duas vezes no arquivo, o navegador é aberto e então navega para o conteúdo e o exibe. Isso será mostrado na figura a seguir.  
  
 ![Exibição do conteúdo no arquivo Person.XAML](../../../../docs/framework/wpf/app-development/media/navigationoverviewfigure21.png "NavigationOverviewFigure21")  
  
 Você pode exibir um flexível [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] arquivo a partir do seguinte:  
  
-   Um site da Web no computador local, a intranet ou a Internet.  
  
-   Um [!INCLUDE[TLA#tla_unc](../../../../includes/tlasharptla-unc-md.md)] compartilhamento de arquivos.  
  
-   O disco local.  
  
 Um flexível [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] arquivo pode ser adicionado aos Favoritos do navegador, ou ser home page do navegador.  
  
> [!NOTE]
>  Para obter mais informações sobre a publicação e iniciando perder [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] páginas, consulte [Implantando um aplicativo do WPF](../../../../docs/framework/wpf/app-development/deploying-a-wpf-application-wpf.md).  
  
 Uma limitação em relação ao perder [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] é que você só pode hospedar conteúdo que é seguro para ser executado em confiança parcial. Por exemplo, `Window` não pode ser o elemento raiz de um flexível [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] arquivo. Para obter mais informações, consulte [Segurança parcialmente confiável do WPF](../../../../docs/framework/wpf/wpf-partial-trust-security.md).  
  
<a name="Navigating_to_HTML_Files_Using_Frame"></a>   
### <a name="navigating-to-html-files-by-using-frame"></a>Navegar para arquivos HTML usando o quadro  
 Como esperado, você também pode navegar para [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)]. Você só precisa fornecer um [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] que usa o esquema http. Por exemplo, a seguinte [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] mostra um <xref:System.Windows.Controls.Frame> que navega para um [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] página.  
  
 [!code-xaml[NavigationOverviewSnippets#FrameHtmlNavMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHTMLNavPage.xaml#framehtmlnavmarkup)]  
  
 Navegando até [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] requer permissões especiais. Por exemplo, você não pode navegar de um [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] que está sendo executado no modo de segurança da zona de confiança parcial da Internet. Para obter mais informações, consulte [Segurança parcialmente confiável do WPF](../../../../docs/framework/wpf/wpf-partial-trust-security.md).  
  
<a name="Navigating_to_HTML_Files_Using_WebBrowser"></a>   
### <a name="navigating-to-html-files-by-using-the-webbrowser-control"></a>Navegar para arquivos HTML usando o controle WebBrowser  
 O <xref:System.Windows.Controls.WebBrowser> controle oferece suporte a [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] interoperabilidade de código de hospedagem de documento, navegação e script/gerenciado. Para obter informações detalhadas sobre o <xref:System.Windows.Controls.WebBrowser> , consulte <xref:System.Windows.Controls.WebBrowser>.  
  
 Como <xref:System.Windows.Controls.Frame>, navegando para [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] usando <xref:System.Windows.Controls.WebBrowser> requer permissões especiais. Por exemplo, de um aplicativo de confiança parcial, você pode navegar somente a [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] localizado no site de origem. Para obter mais informações, consulte [Segurança parcialmente confiável do WPF](../../../../docs/framework/wpf/wpf-partial-trust-security.md).  
  
<a name="Navigating_to_Objects"></a>   
### <a name="navigating-to-custom-objects"></a>Navegar para objetos personalizados  
 Se você tiver dados que são armazenados como objetos personalizados, uma maneira de exibir os dados é criar um <xref:System.Windows.Controls.Page> com conteúdo que está associado a esses objetos (consulte [visão geral de associação de dados](../../../../docs/framework/wpf/data/data-binding-overview.md)). Se você não precisar da sobrecarga resultante da criação de uma página inteira apenas para exibir os objetos, você poderá navegar diretamente para eles em vez disso.  
  
 Considere o `Person` classe que é implementado no código a seguir.  
  
 [!code-csharp[NavigateToObjectSnippets#PersonClassCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/Person.cs#personclasscode)]
 [!code-vb[NavigateToObjectSnippets#PersonClassCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/NavigateToObjectSnippets/VisualBasic/Person.vb#personclasscode)]  
  
 Para navegar até ele, você deve chamar o <xref:System.Windows.Navigation.NavigationWindow.Navigate%2A?displayProperty=nameWithType> método, conforme demonstrado pelo código a seguir.  
  
 [!code-xaml[NavigateToObjectSnippets#PageThatNavsToObject1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/HomePage.xaml#pagethatnavstoobject1)]  
[!code-xaml[NavigateToObjectSnippets#PageThatNavsToObject2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/HomePage.xaml#pagethatnavstoobject2)]  
[!code-xaml[NavigateToObjectSnippets#PageThatNavsToObject3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/HomePage.xaml#pagethatnavstoobject3)]  
  
 [!code-csharp[NavigateToObjectSnippets#PageThatNavsToObjectCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/HomePage.xaml.cs#pagethatnavstoobjectcodebehind)]
 [!code-vb[NavigateToObjectSnippets#PageThatNavsToObjectCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/NavigateToObjectSnippets/VisualBasic/HomePage.xaml.vb#pagethatnavstoobjectcodebehind)]  
  
 A figura a seguir mostra o resultado.  
  
 ![Uma página que navega para uma classe](../../../../docs/framework/wpf/app-development/media/navigationoverviewfigure22.png "NavigationOverviewFigure22")  
  
 Nessa figura, você pode ver que nada útil é exibido. Na verdade, o valor exibido é o valor de retorno de `ToString` método para o **pessoa** objeto; por padrão, esse é o único valor que [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] pode usar para representar seu objeto. Você pode substituir o `ToString` método para retornar informações mais significativas, apesar de ele ainda apenas ser um valor de cadeia de caracteres. Uma técnica pode usar que aproveita os recursos de apresentação [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] é usar um modelo de dados. Você pode implementar um modelo de dados que [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] pode associar a um objeto de um tipo específico. O código a seguir mostra um modelo de dados para o `Person` objeto.  
  
 [!code-xaml[NavigateToObjectSnippets#DataTemplateMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/App.xaml#datatemplatemarkup)]  
  
 Aqui, o modelo de dados está associado a `Person` tipo usando o `x:Type` extensão de marcação no `DataType` atributo. O modelo de dados, em seguida, associa `TextBlock` elementos (consulte <xref:System.Windows.Controls.TextBlock>) para as propriedades da `Person` classe. A figura a seguir mostra a aparência atualizada do `Person` objeto.  
  
 ![Navegar para uma classe que tem um modelo de dados](../../../../docs/framework/wpf/app-development/media/navigationoverviewfigure23.png "NavigationOverviewFigure23")  
  
 Uma vantagem dessa técnica é a consistência você obtém sendo capaz de reutilizar o modelo de dados para exibir os objetos de forma consistente em qualquer lugar no aplicativo.  
  
 Para obter mais informações sobre modelos de dados, consulte [visão geral de modelagem de dados](../../../../docs/framework/wpf/data/data-templating-overview.md).  
  
<a name="Security"></a>   
## <a name="security"></a>Segurança  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] permite o suporte à navegação [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] navegar pela Internet e permite que os aplicativos para hospedar conteúdo de terceiros. Para proteger os aplicativos e usuários contra comportamento prejudicial, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] fornece uma variedade de recursos de segurança que são discutidos em [segurança](../../../../docs/framework/wpf/security-wpf.md) e [WPF Partial Trust Security](../../../../docs/framework/wpf/wpf-partial-trust-security.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Application.SetCookie%2A>  
 <xref:System.Windows.Application.GetCookie%2A>  
 [Visão geral do gerenciamento de aplicativos](../../../../docs/framework/wpf/app-development/application-management-overview.md)  
 [URIs "pack://" no WPF](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md)  
 [Visão geral da navegação estruturada](../../../../docs/framework/wpf/app-development/structured-navigation-overview.md)  
 [Visão geral de topologias de navegação](../../../../docs/framework/wpf/app-development/navigation-topologies-overview.md)  
 [Tópicos de instruções](../../../../docs/framework/wpf/app-development/navigation-how-to-topics.md)  
 [Implantando um aplicativo WPF](../../../../docs/framework/wpf/app-development/deploying-a-wpf-application-wpf.md)
