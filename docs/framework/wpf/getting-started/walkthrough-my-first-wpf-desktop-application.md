---
title: "Passo a passo: Meu aplicativo da área de trabalho primeiro do WPF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- getting started [WPF], WPF
- WPF [WPF], getting started
ms.assetid: b96bed40-8946-4285-8fe4-88045ab854ed
caps.latest.revision: "71"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3667d507f4c35174c1e888c9781b5f74ffd496a0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-my-first-wpf-desktop-application"></a>Passo a passo: Meu aplicativo da área de trabalho primeiro do WPF
Este passo a passo fornece uma introdução ao desenvolvimento de um [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] aplicativo que inclui os elementos que são comuns à maioria [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplicativos: [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] marcação, por trás do código, definições de aplicativo, controles, layout associação de dados e estilos. 
  
 Este passo a passo o orienta o desenvolvimento de um simples [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplicativo usando as etapas a seguir. 
  
-   Definindo [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] para criar a aparência do aplicativo [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. 
  
-   Gravando o código para criar o comportamento do aplicativo. 
  
-   Criando uma definição de aplicativo para gerenciar o aplicativo. 
  
-   Adicionando controles e criar o layout para compor o aplicativo [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. 
  
-   Criando estilos para criar uma aparência consistente em todo um aplicativo [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. 
  
-   Associação de [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] a dados para popular o [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] de dados e manter os dados e [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] sincronizados. 
  
 No final do passo a passo, você terá criado um autônomo [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] aplicativo que permite aos usuários exibir relatórios de despesa para pessoas selecionadas. O aplicativo será composto de vários [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] páginas que são hospedadas em uma janela com estilo de navegador. 
  
 O código de exemplo que é usado para este passo a passo de compilação está disponível para ambos [!INCLUDE[TLA#tla_visualb](../../../../includes/tlasharptla-visualb-md.md)] e [!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)] em [Introdução ao criar aplicativos do WPF](http://go.microsoft.com/fwlink/?LinkID=160008). 

## <a name="prerequisites"></a>Pré-requisitos  

- [!INCLUDE[vs_dev11_long](../../../../includes/vs-dev11-long-md.md)]ou posterior

Para obter mais informações sobre como instalar a versão mais recente do Visual Studio, consulte [instale o Visual Studio](/visualstudio/install/install-visual-studio).
  
## <a name="creating-the-application-project"></a>Criando o projeto de aplicativo  
 Nesta seção, você criará a infraestrutura do aplicativo, que inclui uma definição de aplicativo, duas páginas e uma imagem. 
  
1. Crie um novo projeto de aplicativo do WPF no Visual Basic ou no Visual C#, chamado `ExpenseIt`. Para obter mais informações, consulte [Como criar um novo projeto de aplicativo do WPF](http://msdn.microsoft.com/en-us/1f6aea7a-33e1-4d3f-8555-1daa42e95d82). 
  
    > [!NOTE]
    >  Este passo a passo usa o <xref:System.Windows.Controls.DataGrid> controle que está disponível no .NET Framework 4. Ser-se de que seu projeto se destina ao .NET Framework 4 ou posterior. Para obter mais informações, consulte[como: uma versão do .NET Framework de destino](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework). 
  
2. Abra o Application.xaml (Visual Basic) ou App.xaml (C#). 
  
     Isso [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] arquivo define uma [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplicativo e os recursos de aplicativo. Você também usar esse arquivo para especificar o [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] mostra que automaticamente quando o aplicativo é iniciado; nesse caso, MainWindow. XAML. 
  
     O [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] deve se parecer com no Visual Basic:  
  
    [!code-xaml[ExpenseIt#1_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/Application.xaml#1_a)]  
  
     Ou assim no C#:  
  
    [!code-xaml[ExpenseIt#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/App.xaml#1)]  
  
3. Abra MainWindow.xaml. 
  
     Isso [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] arquivo é a janela principal do seu aplicativo e exibe o conteúdo criado nas páginas. O <xref:System.Windows.Window> classe define as propriedades de uma janela, como título, tamanho ou no ícone e trata os eventos, como fechar ou ocultar. 
  
4. Alterar o <xref:System.Windows.Window> elemento para uma <xref:System.Windows.Navigation.NavigationWindow>. 
  
     Este aplicativo navegará para um conteúdo diferente dependendo da interação do usuário. Portanto, o principal <xref:System.Windows.Window> precisa ser alterado para um <xref:System.Windows.Navigation.NavigationWindow>. <xref:System.Windows.Navigation.NavigationWindow>herda todas as propriedades de <xref:System.Windows.Window>. O <xref:System.Windows.Navigation.NavigationWindow> elemento no arquivo XAML cria uma instância de <xref:System.Windows.Navigation.NavigationWindow> classe. Para obter mais informações, consulte [Visão geral de navegação](../../../../docs/framework/wpf/app-development/navigation-overview.md). 
  
5. Alterar as propriedades a seguir sobre o <xref:System.Windows.Navigation.NavigationWindow> elemento:  
  
    -   Definir o <xref:System.Windows.Window.Title%2A> propriedade como "ExpenseIt". 
  
    -   Definir o <xref:System.Windows.FrameworkElement.Width%2A> propriedade para 500 pixels. 
  
    -   Definir o <xref:System.Windows.FrameworkElement.Height%2A> propriedade 350 pixels. 
  
    -   Remover o <xref:System.Windows.Controls.Grid> elementos entre o <xref:System.Windows.Navigation.NavigationWindow> marcas. 
  
     O [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] deve se parecer com no Visual Basic:  
  
    [!code-xaml[ExpenseIt#2_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt/MainWindow.xaml#2_a)]  
  
     Ou assim no C#:  
  
    [!code-xaml[ExpenseIt#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/MainWindow.xaml#2)]  
  
6. Abra MainWindow.xaml.vb ou MainWindow.xaml.cs. 
  
     Esse é um arquivo code-behind que contém o código para manipular os eventos declarados no MainWindow.xaml. Esse arquivo contém uma classe parcial para a janela definida no XAML. 
  
7. Se você estiver usando c#, altere o `MainWindow` classe para derivar de <xref:System.Windows.Navigation.NavigationWindow>. 
  
     No Visual Basic, isso ocorre automaticamente quando você altera a janela no XAML. 
  
     Seu código deve ter esta aparência. 
  
    [!code-csharp[ExpenseIt#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/MainWindow.xaml.cs#3)]
    [!code-vb[ExpenseIt#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/MainWindow.xaml.vb#3)]  
  
## <a name="adding-files-to-the-application"></a>Adicionando arquivos ao aplicativo  
 Nesta seção, você adiciona duas páginas e uma imagem ao aplicativo. 
  
1. Adicione uma nova página (WPF) ao projeto nomeado `ExpenseItHome.xaml`. Para obter mais informações, consulte [como: adicionar novos itens a um projeto WPF](http://msdn.microsoft.com/en-us/17e6b238-fc32-4385-98ef-2f66ca09d9ad). 
  
     Esta página é a primeira página que será exibida quando o aplicativo for iniciado. Ela mostrará uma lista de pessoas na qual um usuário poderá selecionar uma delas para exibir um relatório de despesas. 
  
2. Abra ExpenseItHome.xaml. 
  
3. Definir o <xref:System.Windows.Controls.Page.Title%2A> para "ExpenseIt - Home". 
  
     O [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] deve se parecer com no Visual Basic:  
  
    [!code-xaml[ExpenseIt#6_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml#6_a)]  
  
     Ou em C#:  
  
    [!code-xaml[ExpenseIt#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml#6)]  
  
4. Abra MainWindow.xaml. 
  
5. Definir o <xref:System.Windows.Navigation.NavigationWindow.Source%2A> propriedade o <xref:System.Windows.Navigation.NavigationWindow> para "ExpenseItHome.xaml". 
  
     Isso define ExpenseItHome.xaml para ser a primeira página aberta quando o aplicativo é iniciado. O [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] deve se parecer com no Visual Basic:  
  
    [!code-xaml[ExpenseIt#7_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/MainWindow.xaml#7_a)]  
  
     Ou em C#:  
  
    [!code-xaml[ExpenseIt#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/MainWindow.xaml#7)]  
  
6. Adicione uma nova página (WPF) ao projeto nomeado `ExpenseReportPage.xaml`. 
  
     Esta página mostrará o relatório de despesas para a pessoa que está selecionada no ExpenseItHome.xaml. 
  
7. Abra ExpenseReportPage.xaml. 
  
8. Definir o <xref:System.Windows.Controls.Page.Title%2A> para "ExpenseIt - despesas de exibição". 
  
     O [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] deve se parecer com no Visual Basic:  
  
    [!code-xaml[ExpenseIt#4_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml#4_a)]  
  
     Ou em C#:  
  
    [!code-xaml[ExpenseIt#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml#4)]  
  
9. Abra ExpenseItHome.xaml.vb e ExpenseReportPage.xaml.vb ou ExpenseItHome.xaml.cs e ExpenseReportPage.xaml.cs. 
  
     Quando você cria um novo arquivo de paginação, o Visual Studio cria automaticamente um arquivo code-behind. Esses arquivos code-behind manipulam a lógica para responder à entrada do usuário. 
  
     Seu código deve ter esta aparência. 
  
    [!code-csharp[ExpenseIt#2_5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml.cs#2_5)]
    [!code-vb[ExpenseIt#2_5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml.vb#2_5)]  
  
    [!code-csharp[ExpenseIt#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml.cs#5)]
    [!code-vb[ExpenseIt#5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml.vb#5)]  
  
10. Adicione uma imagem chamada watermark.png ao projeto. Você pode criar sua própria imagem ou copiar o arquivo do código de exemplo. Para obter mais informações, consulte [NIB: como adicionar itens existentes a um projeto](http://msdn.microsoft.com/en-us/15f4cfb7-78ab-457f-9f14-099a25a6a2d3). 

## <a name="building-and-running-the-application"></a>Criar e executar o aplicativo  
 Nesta seção, você vai compilar e executar o aplicativo. 
  
1. Compilar e executar o aplicativo pressionando F5 ou selecione **iniciar depuração** do **depurar** menu. 
  
     A ilustração a seguir mostra o aplicativo com o <xref:System.Windows.Navigation.NavigationWindow> botões. 
  
     ![Captura de tela de exemplo de ExpenseIt](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure1.png "GettingStartedFigure1")  
  
2. Feche o aplicativo para retornar ao [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)]. 
  
## <a name="creating-the-layout"></a>Criando o layout  
 Layout oferece uma maneira ordenada para colocar [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elementos e também gerencia o tamanho e a posição desses elementos quando um [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] é redimensionado. Normalmente, você cria um layout com um dos seguintes controles de layout:  
  
-   <xref:System.Windows.Controls.Canvas>  
  
-   <xref:System.Windows.Controls.DockPanel>  
  
-   <xref:System.Windows.Controls.Grid>  
  
-   <xref:System.Windows.Controls.StackPanel>  
  
-   <xref:System.Windows.Controls.VirtualizingStackPanel>  
  
-   <xref:System.Windows.Controls.WrapPanel>  
  
 Cada um desses controles de layout dá suporte a um tipo especial de layout para seus elementos filhos. As páginas ExpenseIt podem ser redimensionadas e cada página tem elementos que são organizados horizontalmente e verticalmente juntamente com outros elementos. Consequentemente, o <xref:System.Windows.Controls.Grid> é o elemento de layout ideal para o aplicativo. 
  
> [!NOTE]
>  Para obter mais informações sobre <xref:System.Windows.Controls.Panel> elementos, consulte [visão geral de painéis](../../../../docs/framework/wpf/controls/panels-overview.md). Para obter mais informações sobre o layout, consulte [Layout](../../../../docs/framework/wpf/advanced/layout.md). 
  
 Na seção, você criar uma tabela de coluna única com três linhas e uma margem de 10 pixels adicionando definições de coluna e linha para o <xref:System.Windows.Controls.Grid> em ExpenseItHome.xaml. 
  
1. Abra ExpenseItHome.xaml. 
  
2. Definir o <xref:System.Windows.FrameworkElement.Margin%2A> propriedade o <xref:System.Windows.Controls.Grid> elemento para "10,0,10,10", que corresponde às margens esquerda, superior, direita e inferior. 
  
3. Adicione o seguinte [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] entre o <xref:System.Windows.Controls.Grid> marcas para criar as definições de linha e coluna. 
  
    [!code-xaml[ExpenseIt#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#8)]  
  
     O <xref:System.Windows.Controls.RowDefinition.Height%2A> de duas linhas é definido como <xref:System.Windows.GridLength.Auto%2A> que significa que as linhas serão dimensionadas de base no conteúdo de linhas. O padrão <xref:System.Windows.Controls.RowDefinition.Height%2A> é <xref:System.Windows.GridUnitType.Star> dimensionamento, o que significa que a linha será uma proporção ponderada do espaço disponível. Por exemplo, se duas linhas tiverem cada uma a altura de "*", eles terão uma altura que será a metade do espaço disponível.  
  
     Seu <xref:System.Windows.Controls.Grid> agora deve se parecer com o XAML a seguir:  
  
    [!code-xaml[ExpenseIt#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#9)]  
  
## <a name="adding-controls"></a>Adicionando controles  
 Nesta seção, a home page [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] é atualizada para mostrar uma lista de pessoas que os usuários podem selecionar para mostrar o relatório de despesas para uma pessoa. Os controles são objetos da interface do usuário que permitem aos usuários interagir com seu aplicativo. Para obter mais informações, consulte [Controles](../../../../docs/framework/wpf/controls/index.md). 
  
 Para criar esse [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], os seguintes elementos são adicionados ao ExpenseItHome.xaml:  
  
-   <xref:System.Windows.Controls.ListBox>(para obter a lista de pessoas). 
  
-   <xref:System.Windows.Controls.Label>(para o cabeçalho de lista). 
  
-   <xref:System.Windows.Controls.Button>(para clicar para exibir o relatório de despesas para a pessoa que está selecionada na lista). 
  
 Cada controle é colocado em uma linha do <xref:System.Windows.Controls.Grid> definindo o <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> propriedade anexada. Para obter mais informações sobre propriedades anexadas, consulte [visão geral de propriedades anexado](../../../../docs/framework/wpf/advanced/attached-properties-overview.md). 
  
1. Abra ExpenseItHome.xaml. 
  
2. Adicione o seguinte [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] entre o <xref:System.Windows.Controls.Grid> marcas. 
  
    [!code-xaml[ExpenseIt#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt4/ExpenseItHome.xaml#10)]  
  
3. Crie e execute o aplicativo. 
  
 A ilustração a seguir mostra os controles que são criados pelo XAML nesta seção. 
  
 ![Captura de tela de exemplo de ExpenseIt](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure2.png "GettingStartedFigure2")  
  
## <a name="adding-an-image-and-a-title"></a>Adicionar um título e uma imagem  
 Nesta seção, a home page [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] é atualizada com uma imagem e título da página. 
  
1. Abra ExpenseItHome.xaml. 
  
2. Adicione outra coluna para o <xref:System.Windows.Controls.Grid.ColumnDefinitions%2A> fixa <xref:System.Windows.Controls.ColumnDefinition.Width%2A> de 230 pixels. 
  
    [!code-xaml[ExpenseIt#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#11)]  
  
3. Adicionar outra linha para o <xref:System.Windows.Controls.Grid.RowDefinitions%2A>. 
  
    [!code-xaml[ExpenseIt#11b](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#11b)]  
  
4. Mover os controles para a segunda coluna, definindo <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> como 1. Mover cada controle para baixo de uma linha, aumentando a <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> em 1. 
  
    [!code-xaml[ExpenseIt#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#12)]  
  
5. Definir o <xref:System.Windows.Controls.Panel.Background%2A> do <xref:System.Windows.Controls.Grid> para ser o arquivo de imagem watermark. 
  
    [!code-xaml[ExpenseIt#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#14)]  
  
6. Antes do <xref:System.Windows.Controls.Border>, adicionar um <xref:System.Windows.Controls.Label> com o conteúdo "Exibir relatório de despesas" para ser o título da página. 
  
    [!code-xaml[ExpenseIt#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#13)]  
  
7. Crie e execute o aplicativo. 
  
 A ilustração a seguir mostra os resultados desta seção. 
  
 ![Captura de tela de exemplo de ExpenseIt](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure3.png "GettingStartedFigure3")  
  
## <a name="adding-code-to-handle-events"></a>Adicionando código para tratar eventos  
  
1. Abra ExpenseItHome.xaml. 
  
2. Adicionar um <xref:System.Windows.Controls.Primitives.ButtonBase.Click> manipulador de eventos para o <xref:System.Windows.Controls.Button> elemento. Para obter mais informações, consulte [Como Criar um Manipulador de Eventos Simples](http://msdn.microsoft.com/en-us/b1456e07-9dec-4354-99cf-18666b64f480). 
  
    [!code-xaml[ExpenseIt#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml#15)]  
  
3. Abra ExpenseItHome.xaml.vb ou ExpenseItHome.xaml.cs. 
  
4. Adicione o seguinte código para o <xref:System.Windows.Controls.Primitives.ButtonBase.Click> manipulador de eventos, que faz com que a janela navegar até o arquivo ExpenseReportPage. 
  
    [!code-csharp[ExpenseIt#16](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml.cs#16)]
    [!code-vb[ExpenseIt#16](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt6/ExpenseItHome.xaml.vb#16)]  
  
## <a name="creating-the-ui-for-expensereportpage"></a>Criando a interface do usuário para ExpenseReportPage  
 ExpenseReportPage.xaml exibe o relatório de despesas para a pessoa que foi selecionada no ExpenseItHome.xaml. Esta seção adiciona controles e cria o [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] para ExpenseReportPage. Esta seção também adiciona cores de plano de fundo e preenchimento para os vários [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elementos. 
  
1. Abra ExpenseReportPage.xaml. 
  
2. Adicionar o XAML a seguir entre a <xref:System.Windows.Controls.Grid> marcas. 
  
     Essa interface do usuário é semelhante para a interface do usuário criado em ExpenseItHome.xaml, exceto os dados de relatório são exibidos em um <xref:System.Windows.Controls.DataGrid>. 
  
    [!code-xaml[ExpenseIt#17](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseReportPage.xaml#17)]  
  
3. Crie e execute o aplicativo. 
  
    > [!NOTE]
    >  Se você receber um erro que o <xref:System.Windows.Controls.DataGrid> não foi encontrado ou não existir, certifique-se de que seu projeto direcionado ao .NET Framework 4 ou posterior. Para obter mais informações, consulte [Como definir uma versão do .NET Framework como destino](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework). 
  
4. Clique o **exibição** botão. 
  
     A página de relatório de despesas é exibida. 
  
 A ilustração a seguir mostra o [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elementos adicionados a ExpenseReportPage. Observe que o botão de navegação regressiva está habilitado. 
  
 ![Captura de tela de exemplo de ExpenseIt](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure4.png "GettingStartedFigure4")  
  
## <a name="styling-controls"></a>Controles de estilo  
 A aparência de vários elementos geralmente pode ser o mesmo para todos os elementos do mesmo tipo em um [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. A [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] usa estilos para fazer com que as aparências sejam reutilizáveis entre vários elementos. A capacidade de reutilização dos estilos ajuda a simplificar [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] criação e gerenciamento. Para obter mais informações sobre estilos, consulte [estilos e modelagem](../../../../docs/framework/wpf/controls/styling-and-templating.md). Esta seção substitui os atributos por elemento que foram definidos nas etapas anteriores com estilos. 
  
1. Abra Application.xaml ou App.xaml. 
  
2. Adicionar o XAML a seguir entre a <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> marcas:  
  
    [!code-xaml[ExpenseIt#18](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/App.xaml#18)]  
  
     Isso [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] adiciona os seguintes estilos:  
  
    -  `headerTextStyle`: para formatar o título da página <xref:System.Windows.Controls.Label>. 
  
    -  `labelStyle`: para formatar os controles <xref:System.Windows.Controls.Label>. 
  
    -  `columnHeaderStyle`: para formatar o <xref:System.Windows.Controls.Primitives.DataGridColumnHeader>. 
  
    -  `listHeaderStyle`: para formatar os controles <xref:System.Windows.Controls.Border> do cabeçalho da lista. 
  
    -  `listHeaderTextStyle`: Para formatar o cabeçalho da lista <xref:System.Windows.Controls.Label>. 
  
    -  `buttonStyle`: Para formatar o <xref:System.Windows.Controls.Button> em ExpenseItHome.xaml. 
  
     Observe que os estilos são recursos e seus filhos a <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> elemento property. Nesse local, os estilos são aplicados a todos os elementos em um aplicativo. Para obter um exemplo de uso de recursos em um [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] aplicativo, consulte [usar recursos de aplicativo](../../../../docs/framework/wpf/advanced/how-to-use-application-resources.md). 
  
3. Abra ExpenseItHome.xaml. 
  
4. Substituir tudo entre os <xref:System.Windows.Controls.Grid> elementos com o XAML a seguir. 
  
    [!code-xaml[ExpenseIt#19](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseItHome.xaml#19)]  
  
     As propriedades como <xref:System.Windows.VerticalAlignment> e <xref:System.Windows.Media.FontFamily> que definem a aparência de cada controle são removidas e substituídas ao aplicar os estilos. Por exemplo, o `headerTextStyle` é aplicado a "Exibir relatório de despesas" <xref:System.Windows.Controls.Label>. 
  
5. Abra ExpenseReportPage.xaml. 
  
6. Substituir tudo entre os <xref:System.Windows.Controls.Grid> elementos com o XAML a seguir. 
  
    [!code-xaml[ExpenseIt#20](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseReportPage.xaml#20)]  
  
     Isso adiciona estilos aos elementos <xref:System.Windows.Controls.Label> e <xref:System.Windows.Controls.Border>. 
  
7. Crie e execute o aplicativo. 
  
     Depois de adicionar o [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] nesta seção, o aplicativo tem a mesma aparência que tinha antes de ser atualizado com estilos. 
  
## <a name="binding-data-to-a-control"></a>Associando dados a um controle  
 Nesta seção, você cria o [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] dados que estão associados a vários controles. 
  
1. Abra ExpenseItHome.xaml. 
  
2. Após a abertura <xref:System.Windows.Controls.Grid> elemento, adicionar o XAML a seguir para criar um <xref:System.Windows.Data.XmlDataProvider> que contém os dados de cada pessoa. 
  
     Os dados são criados como um <xref:System.Windows.Controls.Grid> recursos. Normalmente, isso seria carregado como um arquivo, mas para simplificar, os dados são adicionados embutidos. 
  
    [!code-xaml[ExpenseIt#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#21)]  
    [!code-xaml[ExpenseIt#23](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#23)]  
    [!code-xaml[ExpenseIt#22](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#22)]  
  
3. No <xref:System.Windows.Controls.Grid> recursos, adicione o seguinte <xref:System.Windows.DataTemplate>, que define como exibir os dados de <xref:System.Windows.Controls.ListBox>. Para obter mais informações sobre modelos de dados, consulte [Visão geral de modelagem de dados](../../../../docs/framework/wpf/data/data-templating-overview.md). 
  
    [!code-xaml[ExpenseIt#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#21)]  
    [!code-xaml[ExpenseIt#24](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#24)]  
    [!code-xaml[ExpenseIt#22](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#22)]  
  
4. Substituir o <xref:System.Windows.Controls.ListBox> com o XAML a seguir. 
  
    [!code-xaml[ExpenseIt#25](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#25)]  
  
     Este XAML associa o <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> propriedade o <xref:System.Windows.Controls.ListBox> à fonte de dados e aplica o modelo de dados como o <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>. 
  
## <a name="connecting-data-to-controls"></a>Conectando a dados a controles  
 Nesta seção, você escreve o código que recupera o item atual que está selecionado na lista de pessoas na página ExpenseItHome.xaml e passa sua referência para o construtor de `ExpenseReportPage` durante a instanciação. `ExpenseReportPage` define seu contexto de dados com o item passado, ao qual os controles definidos em ExpenseReportPage.xaml serão associados. 
  
1. Abra ExpenseReportPage.xaml.vb ou ExpenseReportPage.xaml.cs. 
  
2. Adicione um construtor que utiliza um objeto para passar os dados do relatório de despesas da pessoa selecionada. 
  
    [!code-csharp[ExpenseIt#26](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseReportPage.xaml.cs#26)]
    [!code-vb[ExpenseIt#26](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseReportPage.xaml.vb#26)]  
  
3. Abra ExpenseItHome.xaml.vb ou ExpenseItHome.xaml.cs. 
  
4. Alterar o <xref:System.Windows.Controls.Primitives.ButtonBase.Click> manipulador de eventos para chamar o novo construtor passar os dados de relatório de despesas da pessoa que está selecionado. 
  
    [!code-csharp[ExpenseIt#27](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml.cs#27)]
    [!code-vb[ExpenseIt#27](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseItHome.xaml.vb#27)]  
  
## <a name="styling-data-with-data-templates"></a>Dados de estilo com modelos de dados  
 Nesta seção, você deve atualizar o [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] para cada item de dados associado ao listas usando modelos de dados. 
  
1. Abra ExpenseReportPage.xaml. 
  
2. Associar o conteúdo do "Nome" e "Departamento" <xref:System.Windows.Controls.Label> a propriedade de fonte de elementos para os dados apropriados. Para obter mais informações sobre vinculação de dados, veja [Noções básicas de vinculação de dados](../../../../docs/framework/wpf/data/data-binding-overview.md). 
  
    [!code-xaml[ExpenseIt#31](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#31)]  
  
3. Após a abertura <xref:System.Windows.Controls.Grid> elemento, adicione os seguintes modelos de dados, que definem como exibir os dados de relatório de despesas.  
    [!code-xaml[ExpenseIt#30](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#30)]  
  
4. Aplicar os modelos para o <xref:System.Windows.Controls.DataGrid> colunas que exibem a despesa de dados de relatório. 
  
    [!code-xaml[ExpenseIt#32](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#32)]  
  
5. Crie e execute o aplicativo. 
  
6. Selecione uma pessoa e clique no **exibição** botão. 
  
 A ilustração a seguir mostra as duas páginas do aplicativo ExpenseIt com controles, layout, estilos, vinculação de dados e modelos de dados aplicados. 
  
 ![Capturas de tela de exemplo de ExpenseIt](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure5.png "GettingStartedFigure5")  
  
## <a name="best-practices"></a>Práticas recomendadas  
 Este exemplo demonstra um recurso específico do WPF e, consequentemente, não segue as práticas recomendadas de desenvolvimento de aplicativos. Para uma cobertura abrangente do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] e [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] práticas recomendadas de desenvolvimento de aplicativo, consulte os tópicos a seguir, conforme apropriado:  
  
-   Acessibilidade – [Práticas recomendadas de acessibilidade](../../../../docs/framework/ui-automation/accessibility-best-practices.md)  
  
-   Segurança - [segurança](../../../../docs/framework/wpf/security-wpf.md)  
  
-   Localização – [Visão geral de globalização e localização do WPF](../../../../docs/framework/wpf/advanced/wpf-globalization-and-localization-overview.md)  
  
-   Desempenho – [Otimizando o desempenho do aplicativo WPF](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)  
  
## <a name="whats-next"></a>Próximas etapas  
 Agora você tem um número de técnicas à sua disposição para criar uma [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] usando [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. Agora você deve ter uma compreensão ampla dos blocos de construção básicos de uma associação de dados [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] aplicativo. Este tópico não é exaustivo, mas dará a você uma noção de algumas das possibilidades que você pode descobrir por conta própria, além das técnicas do tópico. 
  
 Para obter mais informações sobre os modelos de arquitetura e programação do WPF, consulte os seguintes tópicos:  
  
-   [Arquitetura do WPF](../../../../docs/framework/wpf/advanced/wpf-architecture.md)  
  
-   [Visão geral de XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
  
-   [Visão geral das propriedades da dependência](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
  
-   [Layout](../../../../docs/framework/wpf/advanced/layout.md)  
  
 Para obter mais informações sobre como criar aplicativos, consulte os seguintes tópicos:  
  
-   [Desenvolvimento de aplicativos](../../../../docs/framework/wpf/app-development/index.md)  
  
-   [Controles](../../../../docs/framework/wpf/controls/index.md)  
  
-   [Visão geral da vinculação de dados](../../../../docs/framework/wpf/data/data-binding-overview.md)  
  
-   [Elementos gráficos e multimídia](../../../../docs/framework/wpf/graphics-multimedia/index.md)  
  
-   [Documentos no WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral de painéis](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [Visão geral de modelagem dos dados](../../../../docs/framework/wpf/data/data-templating-overview.md)  
 [Compilar um aplicativo WPF](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md)  
 [Estilos e modelos](../../../../docs/framework/wpf/controls/styles-and-templates.md)
