---
title: 'Tutorial: Criar seu primeiro aplicativo do WPF no Visual Studio 2019-.NET Framework'
ms.date: 09/06/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- getting started [WPF], WPF
- WPF [WPF], getting started
ms.assetid: b96bed40-8946-4285-8fe4-88045ab854ed
ms.topic: tutorial
ms.custom: vs-dotnet
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b2c8e36c1b8185f28a7ec20402e385f3a1ddf5ce
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991769"
---
# <a name="tutorial-create-your-first-wpf-application-in-visual-studio-2019"></a>Tutorial: Criar seu primeiro aplicativo do WPF no Visual Studio 2019

Este artigo mostra como desenvolver um aplicativo de área de trabalho Windows Presentation Foundation (WPF) que inclui os elementos comuns à maioria dos aplicativos WPF: Marcação de Extensible Application Markup Language (XAML), code-behind, definições de aplicativo, controles, layout, vinculação de dados e estilos. Para desenvolver o aplicativo, você usará o Visual Studio. 

Neste tutorial, você aprenderá como:
> [!div class="checklist"]
>
> - Crie um projeto do WPF.
> - Use o XAML para criar a aparência da interface do usuário do aplicativo.
> - Escreva o código para criar o comportamento do aplicativo.
> - Crie uma definição de aplicativo para gerenciar o aplicativo.
> - Adicione controles e crie o layout para compor a interface do usuário do aplicativo.
> - Crie estilos para uma aparência consistente em toda a interface do usuário do aplicativo.
> - Associe a interface do usuário aos dados para popular a interface do usuário de dados e manter os dados e a interface do usuário sincronizados.

Ao final do tutorial, você terá criado um aplicativo autônomo do Windows que permite aos usuários exibir relatórios de despesas para as pessoas selecionadas. O aplicativo é composto por várias páginas do WPF que são hospedadas em uma janela em estilo de navegador.

> [!TIP]
> O código de exemplo usado neste tutorial está disponível para o código de exemplo Visual Basic C# e no [tutorial do aplicativo WPF](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/WalkthroughFirstWPFApp).
>
> Você pode alternar o idioma de código do código de exemplo C# entre e Visual Basic usando o seletor de idioma na parte superior desta página.

## <a name="prerequisites"></a>Pré-requisitos

- [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) com a carga de **trabalho de desenvolvimento do .net desktop** instalada.

   Para obter mais informações sobre como instalar a versão mais recente do Visual Studio, consulte [instalar o Visual Studio](/visualstudio/install/install-visual-studio).

## <a name="create-the-application-project"></a>Criar o projeto de aplicativo

A primeira etapa é criar a infraestrutura do aplicativo, que inclui uma definição de aplicativo, duas páginas e uma imagem.

1. Crie um novo projeto de aplicativo WPF em Visual Basic ou C# Visual **`ExpenseIt`** chamado:

   1. Abra o Visual Studio e selecione **criar um novo projeto** no menu **introdução** .

      A caixa de diálogo **criar um novo projeto** é aberta.

   2. Na lista suspensa **idioma** , selecione um **C#** ou **Visual Basic**.
      
   3. Selecione o modelo **aplicativo do WPF (.NET Framework)** e, em seguida, selecione **Avançar**. 
     
      ![Caixa de diálogo criar um novo projeto](./media/walkthrough-my-first-wpf-desktop-application/create-new-project-dialog.png)
    
      A caixa de diálogo **configurar seu novo projeto** é aberta.

   4. Insira o nome **`ExpenseIt`** do projeto e, em seguida, selecione **criar**.

      ![Caixa de diálogo Configurar um novo projeto](./media/walkthrough-my-first-wpf-desktop-application/configure-new-project-dialog.png)

      O Visual Studio cria o projeto e abre o designer para a janela do aplicativo padrão chamada **MainWindow. XAML**.

2. Abra *Application. XAML* (Visual Basic) ou *app. XAML* (C#).

    Esse arquivo XAML define um aplicativo WPF e qualquer recurso de aplicativo. Você também usa esse arquivo para especificar a interface do usuário, nesse caso *MainWindow. XAML*, que mostra automaticamente quando o aplicativo é iniciado.

    O XAML deve ser semelhante ao seguinte no Visual Basic:

    [!code-xaml[ExpenseIt#1_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/Application.xaml#1_a)]

    E semelhante ao seguinte no C#:

    [!code-xaml[ExpenseIt#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/App.xaml#1)]

3. Abra *MainWindow. XAML*.

    Esse arquivo XAML é a janela principal do seu aplicativo e exibe o conteúdo criado em páginas. A <xref:System.Windows.Window> classe define as propriedades de uma janela, como seu título, tamanho ou ícone, e manipula eventos, como fechar ou ocultar.

4. Altere o <xref:System.Windows.Window> elemento <xref:System.Windows.Navigation.NavigationWindow>para a, conforme mostrado no XAML a seguir:

   ```xaml
   <NavigationWindow x:Class="ExpenseIt.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        ...
   </NavigationWindow>
   ```

   Esse aplicativo navega para um conteúdo diferente, dependendo da entrada do usuário. É por isso que a <xref:System.Windows.Window> principal precisa ser alterada para um <xref:System.Windows.Navigation.NavigationWindow>. <xref:System.Windows.Navigation.NavigationWindow>herda todas as propriedades de <xref:System.Windows.Window>. O <xref:System.Windows.Navigation.NavigationWindow> elemento no arquivo XAML cria uma instância <xref:System.Windows.Navigation.NavigationWindow> da classe. Para obter mais informações, consulte [visão geral de navegação](../app-development/navigation-overview.md).

5. Remova os <xref:System.Windows.Controls.Grid> elementos entre as <xref:System.Windows.Navigation.NavigationWindow> marcas.

6. Altere as seguintes propriedades no código XAML para o <xref:System.Windows.Navigation.NavigationWindow> elemento:

    - Defina a <xref:System.Windows.Window.Title%2A> Propriedade como "`ExpenseIt`".

    - Defina a <xref:System.Windows.FrameworkElement.Height%2A> Propriedade como 350 pixels.

    - Defina a <xref:System.Windows.FrameworkElement.Width%2A> Propriedade como 500 pixels.

    O XAML deve ser semelhante ao seguinte por Visual Basic:

    [!code-xaml[ExpenseIt#2_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt/MainWindow.xaml#2_a)]

    E semelhante ao seguinte para C#:

    [!code-xaml[ExpenseIt#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/MainWindow.xaml#2)]

7. Abra *MainWindow. XAML. vb* ou *MainWindow.XAML.cs*.

    Esse arquivo é um arquivo code-behind que contém o código para manipular os eventos declarados em *MainWindow. XAML*. Esse arquivo contém uma classe parcial para a janela definida no XAML.

8. Se você estiver usando C#o, altere `MainWindow` a classe da <xref:System.Windows.Navigation.NavigationWindow>qual derivar. (Em Visual Basic, isso ocorre automaticamente quando você altera a janela em XAML.) O C# código agora deve ser assim:

   [!code-csharp[ExpenseIt#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/MainWindow.xaml.cs?highlight=21)]

## <a name="add-files-to-the-application"></a>Adicionar arquivos ao aplicativo

Nesta seção, você adicionará duas páginas e uma imagem ao aplicativo.

1. Adicione uma nova página ao projeto e nomeie- *`ExpenseItHome.xaml`* a:

   1. Em **Gerenciador de soluções**, clique com o botão direito **`ExpenseIt`** do mouse no nó do projeto e escolha **Adicionar** > **página**.

   1. Na caixa de diálogo **Adicionar novo item** , o modelo **página (WPF)** já está selecionado. Insira o nome **`ExpenseItHome`** e, em seguida, selecione **Adicionar**.

    Esta página é a primeira página que é exibida quando o aplicativo é iniciado. Ele mostrará uma lista de pessoas a serem selecionadas, para mostrar um relatório de despesas para o.

1. Abra *`ExpenseItHome.xaml`* o.

1. Defina como "`ExpenseIt - Home`". <xref:System.Windows.Controls.Page.Title%2A>

1. Defina o `DesignHeight` para 350 pixels e o `DesignWidth` para 500 pixels.

    O XAML agora aparece da seguinte maneira para Visual Basic:

    [!code-xaml[ExpenseIt#6_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml#6_a)]

    E semelhante ao seguinte para C#:

    [!code-xaml[ExpenseIt#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml#6)]

1. Abra *MainWindow. XAML*.

1. Adicione uma <xref:System.Windows.Navigation.NavigationWindow.Source%2A> propriedade <xref:System.Windows.Navigation.NavigationWindow> ao elemento e defina-a como "`ExpenseItHome.xaml`".

    Isso define *`ExpenseItHome.xaml`* como a primeira página aberta quando o aplicativo é iniciado. 

    Exemplo de XAML no Visual Basic:

    [!code-xaml[ExpenseIt#7_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/MainWindow.xaml#7_a)]

    E, em C#:

    [!code-xaml[ExpenseIt#7](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/MainWindow.xaml#7)]

   > [!TIP]
   > Você também pode definir a propriedade **Source** na categoria **Miscellaneous** da janela **Propriedades** .
   >
   > ![Propriedade Source no janela Propriedades](./media/properties-source.png)

1. Adicione outra nova página do WPF ao projeto e nomeie-o como *ExpenseReportPage. XAML*::

   1. Em **Gerenciador de soluções**, clique com o botão direito **`ExpenseIt`** do mouse no nó do projeto e escolha **Adicionar** > **página**.

   1. Na caixa de diálogo **Adicionar novo item** , selecione o modelo **página (WPF)** . Insira o nome **ExpenseReportPage**e, em seguida, selecione **Adicionar**.

    Esta página mostrará o relatório de despesas para a pessoa que está selecionada na **`ExpenseItHome`** página.

1. Abra *ExpenseReportPage.xaml*.

1. Defina como "`ExpenseIt - View Expense`". <xref:System.Windows.Controls.Page.Title%2A>

1. Defina o `DesignHeight` para 350 pixels e o `DesignWidth` para 500 pixels. 

    *ExpenseReportPage. XAML* agora é semelhante ao seguinte no Visual Basic:

    [!code-xaml[ExpenseIt#4_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml#4_a)]

    E semelhante ao seguinte no C#:

    [!code-xaml[ExpenseIt#4](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml#4)]

1. Abra *ExpenseItHome. XAML. vb* e *ExpenseReportPage. XAML. vb*ou *ExpenseItHome.XAML.cs* e *ExpenseReportPage.XAML.cs*.

    Quando você cria um novo arquivo de paginação, o Visual Studio cria automaticamente seu arquivo *code-behind* . Esses arquivos code-behind manipulam a lógica para responder à entrada do usuário.

    Seu código deve ser semelhante ao seguinte para **`ExpenseItHome`** :

    [!code-csharp[ExpenseIt#2_5](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml.cs#2_5)]

    [!code-vb[ExpenseIt#2_5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml.vb#2_5)]

    E como o seguinte para **ExpenseReportPage**:

    [!code-csharp[ExpenseIt#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml.cs#5)]

    [!code-vb[ExpenseIt#5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml.vb#5)]

1. Adicione uma imagem chamada *watermark. png* ao projeto. Você pode criar sua própria imagem, copiar o arquivo do código de exemplo ou obtê-lo do repositório GitHub [Microsoft/WPF-Samples](https://raw.githubusercontent.com/microsoft/WPF-Samples/master/Getting%20Started/WalkthroughFirstWPFApp/csharp/watermark.png) .

    1. Clique com o botão direito do mouse no nó do projeto e selecione **Adicionar** > **Item existente**ou pressione **Shift**+**ALT**+**A**.

    2. Na caixa de diálogo **Adicionar item existente** , defina o filtro de arquivo como **todos os** arquivos ou **arquivos de imagem**, navegue até o arquivo de imagem que deseja usar e, em seguida, selecione **Adicionar**.

## <a name="build-and-run-the-application"></a>Compilar e executar o aplicativo

1. Para compilar e executar o aplicativo, pressione **F5** ou selecione **Iniciar Depuração** no menu **depurar** .

    A ilustração a seguir mostra o aplicativo com <xref:System.Windows.Navigation.NavigationWindow> os botões:

    ![Aplicativo depois de criá-lo e executá-lo.](./media/walkthrough-my-first-wpf-desktop-application/build-run-application.png)

2. Feche o aplicativo para retornar ao Visual Studio.

## <a name="create-the-layout"></a>Criar o layout

O layout fornece uma maneira ordenada de colocar elementos de interface do usuário e também gerencia o tamanho e a posição desses elementos quando uma interface do usuário é redimensionada. Normalmente, você cria um layout com um dos seguintes controles de layout:

- <xref:System.Windows.Controls.Canvas>-Define uma área na qual é possível posicionar explicitamente elementos filho usando coordenadas que são relativas à área da tela.
- <xref:System.Windows.Controls.DockPanel>-Define uma área em que é possível organizar elementos filho horizontal ou verticalmente em relação uns aos outros.
- <xref:System.Windows.Controls.Grid>-Define uma área de grade flexível que consiste em colunas e linhas.
- <xref:System.Windows.Controls.StackPanel>-Organiza os elementos filho em uma única linha que pode ser orientada horizontal ou verticalmente.
- <xref:System.Windows.Controls.VirtualizingStackPanel>-Organiza e virtualiza o conteúdo em uma única linha que é orientada horizontal ou verticalmente.
- <xref:System.Windows.Controls.WrapPanel>-Posiciona os elementos filho na posição sequencial da esquerda para a direita, quebrando o conteúdo para a próxima linha na borda da caixa que o contém. A ordenação subsequente ocorre sequencialmente de cima para baixo ou da direita para a esquerda, dependendo do valor da Propriedade Orientation.

Cada um desses controles de layout dá suporte a um tipo específico de layout para seus elementos filho. `ExpenseIt`as páginas podem ser redimensionadas e cada página tem elementos que são organizados horizontal e verticalmente junto com outros elementos. Neste exemplo, o <xref:System.Windows.Controls.Grid> é usado como elemento de layout para o aplicativo.

> [!TIP]
> Para obter mais informações <xref:System.Windows.Controls.Panel> sobre elementos, consulte [visão geral dos painéis](../controls/panels-overview.md). Para obter mais informações sobre layout, consulte [layout](../advanced/layout.md).

Nesta seção, você cria uma tabela de coluna única com três linhas e uma margem de 10 pixels adicionando definições de coluna e linha ao <xref:System.Windows.Controls.Grid> no. *`ExpenseItHome.xaml`*

1. No *`ExpenseItHome.xaml`* , defina a <xref:System.Windows.FrameworkElement.Margin%2A> Propriedade no <xref:System.Windows.Controls.Grid> elemento como "10, 0, 10, 10", que corresponde às margens esquerda, superior, direita e inferior:

   ```xaml
   <Grid Margin="10,0,10,10">
   ```

   > [!TIP]
   > Você também pode definir os valores de **margem** na janela **Propriedades** , na categoria **layout** :
   >
   > ![Valores de margem no janela Propriedades](./media/properties-margin.png)

2. Adicione o seguinte XAML entre as <xref:System.Windows.Controls.Grid> marcas para criar as definições de linha e coluna:

    [!code-xaml[ExpenseIt#8](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#8)]

    O <xref:System.Windows.Controls.RowDefinition.Height%2A> de duas linhas é definido como <xref:System.Windows.GridLength.Auto%2A>, o que significa que as linhas são dimensionadas com base no conteúdo das linhas. O padrão <xref:System.Windows.Controls.RowDefinition.Height%2A> é <xref:System.Windows.GridUnitType.Star> o dimensionamento, o que significa que a altura da linha é uma proporção ponderada do espaço disponível. Por exemplo, se duas linhas tiverem um <xref:System.Windows.Controls.RowDefinition.Height%2A> de "*", cada uma terá uma altura que é metade do espaço disponível.

    Agora <xref:System.Windows.Controls.Grid> , o deve conter o seguinte XAML:

    [!code-xaml[ExpenseIt#9](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#9)]

## <a name="add-controls"></a>Adicionar controles

Nesta seção, você atualizará a interface do usuário do home page para mostrar uma lista de pessoas, onde você seleciona uma pessoa para exibir seu relatório de despesas. Os controles são objetos da interface do usuário que permitem aos usuários interagir com seu aplicativo. Para obter mais informações, consulte [Controles](../controls/index.md).

Para criar essa interface do usuário, você adicionará os seguintes *`ExpenseItHome.xaml`* elementos a:

- A <xref:System.Windows.Controls.ListBox> (para a lista de pessoas).
- A <xref:System.Windows.Controls.Label> (para o cabeçalho da lista).
- A <xref:System.Windows.Controls.Button> (para clicar para exibir o relatório de despesas da pessoa que está selecionada na lista).

Cada controle é colocado em uma linha do <xref:System.Windows.Controls.Grid> definindo a <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> Propriedade anexada. Para obter mais informações sobre propriedades anexadas, consulte [visão geral de propriedades anexadas](../advanced/attached-properties-overview.md).

1. No *`ExpenseItHome.xaml`* , adicione o seguinte XAML em algum lugar <xref:System.Windows.Controls.Grid> entre as marcas:

   [!code-xaml[ExpenseIt#10](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt4/ExpenseItHome.xaml#10)]

   > [!TIP]
   > Você também pode criar os controles arrastando-os da janela **caixa de ferramentas** para a janela de design e, em seguida, definindo suas propriedades na janela **Propriedades** .

2. Crie e execute o aplicativo.

    A ilustração a seguir mostra os controles que você criou:

![Captura de tela de amostra ExpenseIt exibindo uma lista de nomes](./media/walkthrough-my-first-wpf-desktop-application/add-application-controls.png)

## <a name="add-an-image-and-a-title"></a>Adicionar uma imagem e um título

Nesta seção, você atualizará a interface do usuário do home page com uma imagem e um título de página.

1. No *`ExpenseItHome.xaml`* , adicione outra coluna <xref:System.Windows.Controls.Grid.ColumnDefinitions%2A> ao com um fixo <xref:System.Windows.Controls.ColumnDefinition.Width%2A> de 230 pixels:

    [!code-xaml[ExpenseIt#11](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseItHome.xaml?highlight=52-55)]

2. Adicione outra linha ao <xref:System.Windows.Controls.Grid.RowDefinitions%2A>, para um total de quatro linhas:

    [!code-xaml[ExpenseIt#11b](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseItHome.xaml?highlight=57-62)]

3. Mova os controles para a segunda coluna definindo a <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> Propriedade como 1 em cada um dos três controles (Border, ListBox e Button).

4. Mova cada controle para baixo em uma linha incrementando <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> seu valor em 1 para cada um dos três controles (Border, ListBox e Button) e para o elemento Border.

   O XAML para os três controles agora é semelhante ao seguinte:

    [!code-xaml[ExpenseIt#12](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#12)]

5. Defina a <xref:System.Windows.Controls.Panel.Background%2A?displayProperty=nameWithType> propriedade para o arquivo de imagem de *marca d' água. png* , adicionando o XAML a `<Grid>` seguir `</Grid>` em qualquer lugar entre as marcas e:

    [!code-xaml[ExpenseIt#14](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#14)]

6. Antes do <xref:System.Windows.Controls.Border> elemento, adicione um <xref:System.Windows.Controls.Label> com o conteúdo "Exibir relatório de despesas". Este rótulo é o título da página.

    [!code-xaml[ExpenseIt#13](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#13)]

7. Crie e execute o aplicativo.

A ilustração a seguir mostra os resultados do que você acabou de adicionar:

![Captura de tela de amostra ExpenseIt mostrando a nova tela de fundo e o título da página](./media/walkthrough-my-first-wpf-desktop-application/add-application-image-title.png)

## <a name="add-code-to-handle-events"></a>Adicionar código para manipular eventos

1. No *`ExpenseItHome.xaml`* , adicione um <xref:System.Windows.Controls.Primitives.ButtonBase.Click> manipulador de eventos ao <xref:System.Windows.Controls.Button> elemento. Para obter mais informações, confira [Como: Crie um manipulador](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb675300(v=vs.100))de eventos simples.

    [!code-xaml[ExpenseIt#15](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml#15)]

2. Abra *`ExpenseItHome.xaml.vb`* ou *`ExpenseItHome.xaml.cs`* .

3. Adicione o código a seguir à `ExpenseItHome` classe para adicionar um manipulador de eventos de clique de botão. O manipulador de eventos abre a página **ExpenseReportPage** .

    [!code-csharp[ExpenseIt#16](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml.cs#16)]
    [!code-vb[ExpenseIt#16](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt6/ExpenseItHome.xaml.vb#16)]

## <a name="create-the-ui-for-expensereportpage"></a>Criar a interface do usuário para ExpenseReportPage

*ExpenseReportPage. XAML* exibe o relatório de despesas da pessoa que está selecionada na **`ExpenseItHome`** página. Nesta seção, você criará a interface do usuário para **ExpenseReportPage**. Você também adicionará cores de plano de fundo e preenchimento aos vários elementos da interface do usuário.

1. Abra *ExpenseReportPage.xaml*.

2. Adicione o XAML a seguir entre <xref:System.Windows.Controls.Grid> as marcas:

    [!code-xaml[ExpenseIt#17](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseReportPage.xaml#17)]

    Essa interface do usuário é *`ExpenseItHome.xaml`* semelhante a, exceto que os dados do relatório <xref:System.Windows.Controls.DataGrid>são exibidos em um.

3. Crie e execute o aplicativo.

4. Selecione o botão **Exibir** .

    A página de relatório de despesas é exibida. Observe também que o botão de navegação voltar está habilitado.

A ilustração a seguir mostra os elementos de interface do usuário adicionados a *ExpenseReportPage. XAML*.

![Captura de tela de amostra ExpenseIt mostrando a interface do usuário recém-criada para o ExpenseReportPage.](./media/walkthrough-my-first-wpf-desktop-application/create-application-ui.png)

## <a name="style-controls"></a>Controles de estilo

A aparência de vários elementos é geralmente a mesma para todos os elementos do mesmo tipo em uma interface do usuário. A interface do usuário usa [estilos](../controls/styling-and-templating.md) para fazer com que as aparências sejam reutilizáveis em vários elementos. A reutilização de estilos ajuda a simplificar a criação e o gerenciamento de XAML. Esta seção substitui os atributos por elemento que foram definidos nas etapas anteriores com estilos.

1. Abra *Application. XAML* ou *app. XAML*.

2. Adicione o XAML a seguir entre <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> as marcas:

    [!code-xaml[ExpenseIt#18](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/App.xaml#18)]

    Esse XAML adiciona os seguintes estilos:

    - `headerTextStyle`: Para formatar o título <xref:System.Windows.Controls.Label>da página.

    - `labelStyle`: Para formatar os <xref:System.Windows.Controls.Label> controles.

    - `columnHeaderStyle`: Para formatar o <xref:System.Windows.Controls.Primitives.DataGridColumnHeader>.

    - `listHeaderStyle`: Para formatar os controles de <xref:System.Windows.Controls.Border> cabeçalho da lista.

    - `listHeaderTextStyle`: Para formatar o cabeçalho <xref:System.Windows.Controls.Label>da lista.

    - `buttonStyle`: Para formatar o <xref:System.Windows.Controls.Button> em `ExpenseItHome.xaml`.

    Observe que os estilos são recursos e filhos do <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> elemento Property. Nesse local, os estilos são aplicados a todos os elementos em um aplicativo. Para obter um exemplo de como usar recursos em um aplicativo .NET, consulte [usar recursos do aplicativo](../advanced/how-to-use-application-resources.md).

3. No *`ExpenseItHome.xaml`* , substitua tudo entre os <xref:System.Windows.Controls.Grid> elementos com o seguinte XAML:

    [!code-xaml[ExpenseIt#19](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseItHome.xaml#19)]

    As propriedades como <xref:System.Windows.VerticalAlignment> e <xref:System.Windows.Media.FontFamily> que definem a aparência de cada controle são removidas e substituídas ao aplicar os estilos. Por exemplo, o `headerTextStyle` é aplicado ao "Exibir relatório de despesas" <xref:System.Windows.Controls.Label>.

4. Abra *ExpenseReportPage.xaml*.

5. Substitua tudo entre os <xref:System.Windows.Controls.Grid> elementos com o seguinte XAML:

    [!code-xaml[ExpenseIt#20](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseReportPage.xaml#20)]

    Esse XAML adiciona estilos aos <xref:System.Windows.Controls.Label> elementos e. <xref:System.Windows.Controls.Border>

6. Crie e execute o aplicativo. A aparência da janela é a mesma que a anterior.

    ![Captura de tela de amostra ExpenseIt com a mesma aparência da última seção.](./media/walkthrough-my-first-wpf-desktop-application/create-application-ui.png)

7. Feche o aplicativo para retornar ao Visual Studio.

## <a name="bind-data-to-a-control"></a>Associar dados a um controle

Nesta seção, você criará os dados XML que estão associados a vários controles.

1. No *`ExpenseItHome.xaml`* , após o elemento <xref:System.Windows.Controls.Grid> de abertura, adicione o seguinte XAML para criar <xref:System.Windows.Data.XmlDataProvider> um que contenha os dados para cada pessoa:

    [!code-xaml[ExpenseIt#23](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml?range=13,16-40,49)]

    Os dados são criados como um <xref:System.Windows.Controls.Grid> recurso. Normalmente, esses dados seriam carregados como um arquivo, mas, para simplificar, os dados são adicionados embutidos.

2. Dentro do `<Grid.Resources>` elemento, adicione o seguinte `<xref:System.Windows.DataTemplate>` elemento, que define como <xref:System.Windows.Controls.ListBox>exibir os dados no, após o `<XmlDataProvider>` elemento:

    [!code-xaml[ExpenseIt#24](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml?range=13,43-46,49)]

    Para obter mais informações sobre modelos de dados, consulte [visão geral de modelagem de dados](../data/data-templating-overview.md).

3. Substitua o existente <xref:System.Windows.Controls.ListBox> pelo seguinte XAML:

    [!code-xaml[ExpenseIt#25](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#25)]

    Esse XAML associa a <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> propriedade <xref:System.Windows.Controls.ListBox> do à fonte de dados e aplica o modelo de dados como o <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>.

## <a name="connect-data-to-controls"></a>Conectar dados a controles

Em seguida, você adicionará o código para recuperar o nome selecionado na **`ExpenseItHome`** página e passá-lo para o construtor de **ExpenseReportPage**. **ExpenseReportPage** define seu contexto de dados com o item passado, que é o que os controles definidos no *ExpenseReportPage. XAML* se associam a.

1. Abra *ExpenseReportPage.xaml.vb* ou *ExpenseReportPage.xaml.cs*.

2. Adicione um construtor que utiliza um objeto para passar os dados do relatório de despesas da pessoa selecionada.

    [!code-csharp[ExpenseIt#26](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseReportPage.xaml.cs#26)]
    [!code-vb[ExpenseIt#26](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseReportPage.xaml.vb#26)]

3. Abra *`ExpenseItHome.xaml.vb`* ou *`ExpenseItHome.xaml.cs`* .

4. Altere o <xref:System.Windows.Controls.Primitives.ButtonBase.Click> manipulador de eventos para chamar o novo Construtor passando os dados do relatório de despesas da pessoa selecionada.

    [!code-csharp[ExpenseIt#27](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml.cs#27)]
    [!code-vb[ExpenseIt#27](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseItHome.xaml.vb#27)]

## <a name="style-data-with-data-templates"></a>Dados de estilo com modelos de dados

Nesta seção, você atualizará a interface do usuário para cada item nas listas vinculadas a dados usando modelos de dados.

1. Abra *ExpenseReportPage.xaml*.

2. Associe o conteúdo dos elementos "nome" e "departamento" <xref:System.Windows.Controls.Label> à propriedade de fonte de dados apropriada. Para obter mais informações sobre associação de dados, consulte [visão geral da ligação de dados](../data/data-binding-overview.md).

    [!code-xaml[ExpenseIt#31](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#31)]

3. Após o elemento <xref:System.Windows.Controls.Grid> de abertura, adicione os seguintes modelos de dados, que definem como exibir os dados do relatório de despesas:

    [!code-xaml[ExpenseIt#30](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#30)]

4. Substitua os <xref:System.Windows.Controls.DataGridTextColumn> elementos por <xref:System.Windows.Controls.DataGridTemplateColumn> sob o <xref:System.Windows.Controls.DataGrid> elemento e aplique os modelos a eles.

    [!code-xaml[ExpenseIt#32](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#32)]

5. Crie e execute o aplicativo.

6. Selecione uma pessoa e, em seguida, selecione o botão **Exibir** .

A ilustração a seguir mostra as páginas do `ExpenseIt` aplicativo com controles, layout, estilos, vinculação de dados e modelos de dados aplicados:

![Ambas as páginas do aplicativo mostrando a lista de nomes e um relatório de despesas.](./media/walkthrough-my-first-wpf-desktop-application/application-data-templates.png)

> [!NOTE]
> Este exemplo demonstra um recurso específico do WPF e não segue todas as práticas recomendadas para coisas como segurança, localização e acessibilidade. Para obter uma cobertura abrangente do WPF e as práticas recomendadas de desenvolvimento de aplicativos .NET, consulte os seguintes tópicos:
>
> - [Acessibilidade](../../ui-automation/accessibility-best-practices.md)
> - [Segurança](../security-wpf.md)
> - [Globalização e localização do WPF](../advanced/wpf-globalization-and-localization-overview.md)
> - [Desempenho do WPF](../advanced/optimizing-wpf-application-performance.md)

## <a name="next-steps"></a>Próximas etapas

Neste tutorial, você aprendeu várias técnicas para criar uma interface do usuário usando Windows Presentation Foundation (WPF). Agora você deve ter uma compreensão básica dos blocos de construção de um aplicativo .NET vinculado a dados. Para obter mais informações sobre os modelos de arquitetura e programação do WPF, consulte os seguintes tópicos:

- [Arquitetura do WPF](../advanced/wpf-architecture.md)
- [Visão geral do XAML (WPF)](../advanced/xaml-overview-wpf.md)
- [Visão geral das propriedades de dependência](../advanced/dependency-properties-overview.md)
- [Layout](../advanced/layout.md)

Para obter mais informações sobre como criar aplicativos, consulte os seguintes tópicos:

- [Desenvolvimento de aplicativos](../app-development/index.md)
- [Controles](../controls/index.md)
- [Visão geral da associação de dados](../data/data-binding-overview.md)
- [Gráficos e multimídia](../graphics-multimedia/index.md)
- [Documentos no WPF](../advanced/documents-in-wpf.md)

## <a name="see-also"></a>Consulte também

- [Visão geral dos painéis](../controls/panels-overview.md)
- [Visão geral de modelagem de dados](../data/data-templating-overview.md)
- [Compilar um aplicativo WPF](../app-development/building-a-wpf-application-wpf.md)
- [Estilos e modelos](../controls/styles-and-templates.md)
