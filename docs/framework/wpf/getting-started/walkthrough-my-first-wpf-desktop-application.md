---
title: Crie seu primeiro aplicativo WPF no Visual Studio 2019 - .NET Framework
titleSuffix: ''
ms.date: 09/06/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- getting started [WPF], WPF
- WPF [WPF], getting started
ms.assetid: b96bed40-8946-4285-8fe4-88045ab854ed
ms.topic: tutorial
ms.custom: mvc,vs-dotnet
ms.openlocfilehash: 9381873faa8cca1accf95d823f5183a218d28813
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646423"
---
# <a name="tutorial-create-your-first-wpf-application-in-visual-studio-2019"></a>Tutorial: Crie seu primeiro aplicativo WPF no Visual Studio 2019

Este artigo mostra como desenvolver um aplicativo de desktop do Windows Presentation Foundation (WPF) que inclui os elementos que são comuns à maioria dos aplicativos WPF: marcação XAML (Extensible Application Markup Language, xaml), code-behind, definições de aplicativos, controles, layout, vinculação de dados e estilos. Para desenvolver o aplicativo, você usará o Visual Studio.

Neste tutorial, você aprenderá como:
> [!div class="checklist"]
>
> - Crie um projeto WPF.
> - Use XAML para projetar a aparência da interface de usuário do aplicativo (UI).
> - Escreva código para construir o comportamento do aplicativo.
> - Crie uma definição de aplicativo para gerenciar o aplicativo.
> - Adicione controles e crie o layout para compor a interface do aplicativo.
> - Crie estilos para uma aparência consistente em toda a interface do ida do aplicativo.
> - Vincule a ui a dados, tanto para preencher a ui a partir de dados quanto para manter os dados e a UI sincronizados.

No final do tutorial, você terá construído um aplicativo autônomo do Windows que permite que os usuários visualizem relatórios de despesas para pessoas selecionadas. O aplicativo é composto por várias páginas WPF que estão hospedadas em uma janela no estilo navegador.

> [!TIP]
> O código de exemplo usado neste tutorial está disponível tanto para visual basic quanto c# no [Tutorial WPF App Sample Code](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/WalkthroughFirstWPFApp).
>
> Você pode alternar a linguagem de código do código de amostra entre C# e Visual Basic usando o seletor de idiomas no topo desta página.

## <a name="prerequisites"></a>Pré-requisitos

- [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) com a carga **de trabalho de desenvolvimento de desktop .NET** instalada.

   Para obter mais informações sobre a instalação da versão mais recente do Visual Studio, consulte [Install Visual Studio](/visualstudio/install/install-visual-studio).

## <a name="create-the-application-project"></a>Criar o projeto de aplicativo

O primeiro passo é criar a infra-estrutura do aplicativo, que inclui uma definição de aplicativo, duas páginas e uma imagem.

1. Crie um novo projeto de aplicativo WPF **`ExpenseIt`** no Visual Basic ou Visual C# chamado :

   1. Abra o Visual Studio e selecione **Crie um novo projeto** no menu **'Iniciar'.**

      O **Diálogo Criar um novo projeto** é aberto.

   2. Na estada **do idioma,** selecione **C#** ou **Visual Basic**.

   3. Selecione o modelo **WPF App (.NET Framework)** e selecione **Next**.

      ![Crie um novo diálogo de projeto](./media/walkthrough-my-first-wpf-desktop-application/create-new-project-dialog.png)

      **O Configure seu novo diálogo** de projeto é aberto.

   4. Digite o **`ExpenseIt`** nome do projeto e selecione **Criar**.

      ![Configure uma nova caixa de diálogo de projeto](./media/walkthrough-my-first-wpf-desktop-application/configure-new-project-dialog.png)

      O Visual Studio cria o projeto e abre o designer para a janela de aplicativo padrão chamada **MainWindow.xaml**.

2. Abra *o Application.xaml* (Visual Basic) ou *o App.xaml* (C#).

    Este arquivo XAML define um aplicativo WPF e quaisquer recursos de aplicação. Você também usa este arquivo para especificar a interface do u, neste caso *MainWindow.xaml*, que mostra automaticamente quando o aplicativo é iniciado.

    Seu XAML deve parecer o seguinte no Visual Basic:

    [!code-xaml[ExpenseIt#1_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/Application.xaml#1_a)]

    E como o seguinte em C#:

    [!code-xaml[ExpenseIt#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/App.xaml#1)]

3. Abra *MainWindow.xaml*.

    Este arquivo XAML é a janela principal do seu aplicativo e exibe o conteúdo criado nas páginas. A <xref:System.Windows.Window> classe define as propriedades de uma janela, como seu título, tamanho ou ícone, e lida com eventos, como fechar ou ocultar.

4. Altere <xref:System.Windows.Window> o <xref:System.Windows.Navigation.NavigationWindow>elemento para a, conforme mostrado no seguinte XAML:

   ```xaml
   <NavigationWindow x:Class="ExpenseIt.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        ...
   </NavigationWindow>
   ```

   Este aplicativo navega para diferentes conteúdos, dependendo da entrada do usuário. É por isso <xref:System.Windows.Window> que o principal <xref:System.Windows.Navigation.NavigationWindow>precisa ser alterado para um . <xref:System.Windows.Navigation.NavigationWindow>herda todas as <xref:System.Windows.Window>propriedades de . O <xref:System.Windows.Navigation.NavigationWindow> elemento no arquivo XAML cria <xref:System.Windows.Navigation.NavigationWindow> uma instância da classe. Para obter mais informações, consulte [Visão geral da navegação](../app-development/navigation-overview.md).

5. Remova <xref:System.Windows.Controls.Grid> os elementos <xref:System.Windows.Navigation.NavigationWindow> entre as etiquetas.

6. Alterar as seguintes propriedades no código <xref:System.Windows.Navigation.NavigationWindow> XAML para o elemento:

    - Defina <xref:System.Windows.Window.Title%2A> a`ExpenseIt`propriedade para ".

    - Defina <xref:System.Windows.FrameworkElement.Height%2A> a propriedade em 350 pixels.

    - Defina <xref:System.Windows.FrameworkElement.Width%2A> a propriedade para 500 pixels.

    Seu XAML deve parecer o seguinte para Visual Basic:

    [!code-xaml[ExpenseIt#2_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt/MainWindow.xaml#2_a)]

    E como o seguinte para C#:

    [!code-xaml[ExpenseIt#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/MainWindow.xaml#2)]

7. Abra *MainWindow.xaml.vb* ou *MainWindow.xaml.cs*.

    Este arquivo é um arquivo por trás do código que contém código para lidar com os eventos declarados em *MainWindow.xaml*. Esse arquivo contém uma classe parcial para a janela definida no XAML.

8. Se você estiver usando C#, mude `MainWindow` <xref:System.Windows.Navigation.NavigationWindow>a classe para derivar de . (No Visual Basic, isso acontece automaticamente quando você altera a janela em XAML.) Seu código C# agora deve ser assim:

   [!code-csharp[ExpenseIt#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/MainWindow.xaml.cs?highlight=21)]

## <a name="add-files-to-the-application"></a>Adicionar arquivos ao aplicativo

Nesta seção, você adicionará duas páginas e uma imagem ao aplicativo.

1. Adicione uma nova página ao projeto *`ExpenseItHome.xaml`* e nomeie-a:

   1. No **Solution Explorer,** clique **`ExpenseIt`** com o botão direito do mouse no nó do projeto e escolha **Adicionar** > **página**.

   1. Na caixa de diálogo **Adicionar novo item,** o modelo **Página (WPF)** já está selecionado. Digite **`ExpenseItHome`** o nome e selecione **Adicionar**.

    Esta página é a primeira página exibida quando o aplicativo é lançado. Ele mostrará uma lista de pessoas para selecionar, para mostrar um relatório de despesas para.

1. Abra. *`ExpenseItHome.xaml`*

1. Defina <xref:System.Windows.Controls.Page.Title%2A> o`ExpenseIt - Home`"" ".

1. Defina `DesignHeight` os 350 pixels e os `DesignWidth` 500 pixels.

    O XAML agora aparece da seguinte forma para Visual Basic:

    [!code-xaml[ExpenseIt#6_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml#6_a)]

    E como o seguinte para C#:

    [!code-xaml[ExpenseIt#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml#6)]

1. Abra *MainWindow.xaml*.

1. Adicione <xref:System.Windows.Navigation.NavigationWindow.Source%2A> uma propriedade <xref:System.Windows.Navigation.NavigationWindow> ao elemento e`ExpenseItHome.xaml`defina-a como " ".

    Esta *`ExpenseItHome.xaml`* define-se para ser a primeira página aberta quando o aplicativo é iniciado.

    Exemplo XAML no Visual Basic:

    [!code-xaml[ExpenseIt#7_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/MainWindow.xaml#7_a)]

    E em C#:

    [!code-xaml[ExpenseIt#7](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/MainWindow.xaml#7)]

   > [!TIP]
   > Você também pode definir a propriedade **Origem** na categoria **Diversas** da janela **Propriedades.**
   >
   > ![Propriedade de origem na janela Propriedades](./media/properties-source.png)

1. Adicione outra nova página do WPF ao projeto e nomeie-a *ExpenseReportPage.xaml*::

   1. No **Solution Explorer,** clique **`ExpenseIt`** com o botão direito do mouse no nó do projeto e escolha **Adicionar** > **página**.

   1. Na **caixa de diálogo Adicionar novo item,** selecione o modelo **Página (WPF).** Digite o nome **ExpenseReportPage**e, em seguida, **selecione Adicionar**.

    Esta página mostrará o relatório de despesas **`ExpenseItHome`** para a pessoa selecionada na página.

1. Open *ExpenseReportPage.xaml*.

1. Defina <xref:System.Windows.Controls.Page.Title%2A> o`ExpenseIt - View Expense`"" ".

1. Defina `DesignHeight` os 350 pixels e os `DesignWidth` 500 pixels.

    *ExpenseReportPage.xaml* agora parece o seguinte no Visual Basic:

    [!code-xaml[ExpenseIt#4_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml#4_a)]

    E como o seguinte em C#:

    [!code-xaml[ExpenseIt#4](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml#4)]

1. *Custo abertoItHome.xaml.vb* e *ExpenseReportPage.xaml.vb*, ou *ExpenseItHome.xaml.cs* e *ExpenseReportPage.xaml.cs*.

    Quando você cria um novo arquivo de página, o Visual Studio cria automaticamente seu arquivo *de código atrás.* Esses arquivos code-behind manipulam a lógica para responder à entrada do usuário.

    Seu código deve parecer **`ExpenseItHome`** o seguinte para:

    [!code-csharp[ExpenseIt#2_5](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml.cs#2_5)]

    [!code-vb[ExpenseIt#2_5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml.vb#2_5)]

    E como o seguinte para **ExpenseReportPage**:

    [!code-csharp[ExpenseIt#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml.cs#5)]

    [!code-vb[ExpenseIt#5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml.vb#5)]

1. Adicione uma imagem chamada *watermark.png* ao projeto. Você pode criar sua própria imagem, copiar o arquivo do código de amostra ou obtê-lo no repositório [GitHub da Microsoft/WPF-Samples.](https://raw.githubusercontent.com/microsoft/WPF-Samples/master/Getting%20Started/WalkthroughFirstWPFApp/csharp/watermark.png)

    1. Clique com o botão direito do mouse no nó do projeto e **selecione Adicionar** > **item existente**ou **pressione Shift**+**Alt**+**A**.

    2. Na **caixa de diálogo Adicionar item existente,** defina o filtro de arquivo para **todos os arquivos** ou arquivos de **imagem,** navegue até o arquivo de imagem que deseja usar e selecione **Adicionar**.

## <a name="build-and-run-the-application"></a>Compile e execute o aplicativo

1. Para criar e executar o aplicativo, pressione **F5** ou selecione **Iniciar depuração** no menu **Depuração.**

    A ilustração a seguir <xref:System.Windows.Navigation.NavigationWindow> mostra o aplicativo com os botões:

    ![Aplicativo depois de construí-lo e executá-lo.](./media/walkthrough-my-first-wpf-desktop-application/build-run-application.png)

2. Feche o aplicativo para retornar ao Visual Studio.

## <a name="create-the-layout"></a>Crie o layout

O layout fornece uma maneira ordenada de colocar elementos de ida e volta, e também gerencia o tamanho e a posição desses elementos quando uma iu é redimensionada. Normalmente, você cria um layout com um dos seguintes controles de layout:

- <xref:System.Windows.Controls.Canvas>- Define uma área dentro da qual você pode posicionar explicitamente elementos infantis usando coordenadas relativas à área do Canvas.
- <xref:System.Windows.Controls.DockPanel>- Define uma área onde você pode organizar elementos infantis horizontal ou verticalmente, em relação um ao outro.
- <xref:System.Windows.Controls.Grid>- Define uma área de grade flexível que consiste em colunas e linhas.
- <xref:System.Windows.Controls.StackPanel>- Organiza elementos infantis em uma única linha que pode ser orientada horizontal ou verticalmente.
- <xref:System.Windows.Controls.VirtualizingStackPanel>- Organiza e virtualiza o conteúdo em uma única linha orientada horizontal ou verticalmente.
- <xref:System.Windows.Controls.WrapPanel>- Posiciona os elementos da criança na posição seqüencial da esquerda para a direita, quebrando o conteúdo para a próxima linha na borda da caixa de contenção. A encomenda subseqüente acontece sequencialmente de cima para baixo ou da direita para a esquerda, dependendo do valor da propriedade Orientação.

Cada um desses controles de layout suporta um tipo específico de layout para seus elementos infantis. `ExpenseIt`páginas podem ser redimensionadas, e cada página tem elementos que são organizados horizontal e verticalmente ao lado de outros elementos. Neste exemplo, <xref:System.Windows.Controls.Grid> o é usado como elemento de layout para a aplicação.

> [!TIP]
> Para obter <xref:System.Windows.Controls.Panel> mais informações sobre elementos, consulte [Painéis de visão geral](../controls/panels-overview.md). Para obter mais informações sobre layout, consulte [Layout](../advanced/layout.md).

Nesta seção, você cria uma tabela de uma única coluna com três linhas e uma <xref:System.Windows.Controls.Grid> *`ExpenseItHome.xaml`* margem de 10 pixels adicionando definições de coluna e linha à entrada .

1. Em *`ExpenseItHome.xaml`*, <xref:System.Windows.FrameworkElement.Margin%2A> definir a <xref:System.Windows.Controls.Grid> propriedade no elemento como "10,0,10,10", que corresponde às margens esquerda, superior, direita e inferior:

   ```xaml
   <Grid Margin="10,0,10,10">
   ```

   > [!TIP]
   > Você também pode definir os valores **de Margem** na janela **Propriedades,** na categoria **Layout:**
   >
   > ![Valores de margem na janela Propriedades](./media/properties-margin.png)

2. Adicione o seguinte XAML entre as <xref:System.Windows.Controls.Grid> tags para criar as definições de linha e coluna:

    [!code-xaml[ExpenseIt#8](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#8)]

    A <xref:System.Windows.Controls.RowDefinition.Height%2A> de duas linhas <xref:System.Windows.GridLength.Auto%2A>é definida como , o que significa que as linhas são dimensionadas com base no conteúdo nas linhas. O <xref:System.Windows.Controls.RowDefinition.Height%2A> padrão <xref:System.Windows.GridUnitType.Star> é o dimensionamento, o que significa que a altura da linha é uma proporção ponderada do espaço disponível. Por exemplo, se duas <xref:System.Windows.Controls.RowDefinition.Height%2A> linhas cada uma tem um de "*", cada uma tem uma altura que é metade do espaço disponível.

    Agora <xref:System.Windows.Controls.Grid> você deve conter o seguinte XAML:

    [!code-xaml[ExpenseIt#9](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#9)]

## <a name="add-controls"></a>Adicionar controles

Nesta seção, você atualizará a ui da página inicial para mostrar uma lista de pessoas, onde você seleciona uma pessoa para exibir seu relatório de despesas. Os controles são objetos da interface do usuário que permitem aos usuários interagir com seu aplicativo. Para obter mais informações, consulte [Controles](../controls/index.md).

Para criar essa iu, você adicionará *`ExpenseItHome.xaml`* os seguintes elementos a:

- A <xref:System.Windows.Controls.ListBox> (para a lista de pessoas).
- A <xref:System.Windows.Controls.Label> (para o cabeçalho da lista).
- A <xref:System.Windows.Controls.Button> (clicar para visualizar o relatório de despesas para a pessoa selecionada na lista).

Cada controle é colocado em <xref:System.Windows.Controls.Grid> uma <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> linha do definindo a propriedade anexada. Para obter mais informações sobre propriedades anexadas, consulte [Visão geral de propriedades anexadas](../advanced/attached-properties-overview.md).

1. Em *`ExpenseItHome.xaml`*, adicione o seguinte XAML em algum lugar entre as <xref:System.Windows.Controls.Grid> tags:

   [!code-xaml[ExpenseIt#10](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt4/ExpenseItHome.xaml#10)]

   > [!TIP]
   > Você também pode criar os controles arrastando-os da janela **Toolbox** para a janela de design e, em seguida, definindo suas propriedades na janela **Propriedades.**

2. Criar e executar o aplicativo.

    A ilustração a seguir mostra os controles que você criou:

![DespesaA captura de tela de captura de tela de captura de tela exibindo uma lista de nomes](./media/walkthrough-my-first-wpf-desktop-application/add-application-controls.png)

## <a name="add-an-image-and-a-title"></a>Adicione uma imagem e um título

Nesta seção, você atualizará a ui da página inicial com uma imagem e um título de página.

1. Em *`ExpenseItHome.xaml`*, adicionar outra <xref:System.Windows.Controls.Grid.ColumnDefinitions%2A> coluna <xref:System.Windows.Controls.ColumnDefinition.Width%2A> ao com um fixo de 230 pixels:

    [!code-xaml[ExpenseIt#11](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseItHome.xaml?highlight=2#NewColumn)]

2. Adicione outra linha <xref:System.Windows.Controls.Grid.RowDefinitions%2A>ao , para um total de quatro linhas:

    [!code-xaml[ExpenseIt#11b](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseItHome.xaml?highlight=2#NewRows)]

3. Mova os controles para a segunda <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> coluna definindo a propriedade para 1 em cada um dos três controles (Border, ListBox e Button).

4. Mova cada controle para baixo <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> uma linha, aumentando seu valor em 1 para cada um dos três controles (Border, ListBox e Button) e para o elemento Borda.

   O XAML para os três controles agora parece o seguinte:

    [!code-xaml[ExpenseIt#12](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#12)]

5. Defina <xref:System.Windows.Controls.Panel.Background%2A?displayProperty=nameWithType> a propriedade no arquivo de imagem *watermark.png,* adicionando o seguinte XAML em qualquer lugar entre as `<Grid>` `</Grid>` tags:

    [!code-xaml[ExpenseIt#14](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#14)]

6. Antes <xref:System.Windows.Controls.Border> do elemento, <xref:System.Windows.Controls.Label> adicione a com o conteúdo "Exibir relatório de despesas". Este rótulo é o título da página.

    [!code-xaml[ExpenseIt#13](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#13)]

7. Criar e executar o aplicativo.

A ilustração a seguir mostra os resultados do que você acabou de adicionar:

![Captura de tela de exemplo expenseIt mostrando o novo plano de fundo da imagem e o título da página](./media/walkthrough-my-first-wpf-desktop-application/add-application-image-title.png)

## <a name="add-code-to-handle-events"></a>Adicionar código para lidar com eventos

1. Em *`ExpenseItHome.xaml`*, <xref:System.Windows.Controls.Primitives.ButtonBase.Click> adicionar um <xref:System.Windows.Controls.Button> manipulador de eventos ao elemento. Para obter mais informações, consulte [Como: Criar um simples manipulador de eventos](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb675300(v=vs.100)).

    [!code-xaml[ExpenseIt#15](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml#15)]

2. Abra *`ExpenseItHome.xaml.vb`* *`ExpenseItHome.xaml.cs`* ou.

3. Adicione o seguinte `ExpenseItHome` código à classe para adicionar um manipulador de eventos clique em botão. O manipulador de eventos abre a página **ExpenseReportPage.**

    [!code-csharp[ExpenseIt#16](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml.cs#16)]
    [!code-vb[ExpenseIt#16](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt6/ExpenseItHome.xaml.vb#16)]

## <a name="create-the-ui-for-expensereportpage"></a>Criar a ui para relatório de despesas

*ExpenseReportPage.xaml* exibe o relatório de despesas para **`ExpenseItHome`** a pessoa selecionada na página. Nesta seção, você criará a ui para **ExpenseReportPage**. Você também adicionará o plano de fundo e preencherá cores aos vários elementos de ia.

1. Open *ExpenseReportPage.xaml*.

2. Adicione o seguinte XAML entre as <xref:System.Windows.Controls.Grid> tags:

    [!code-xaml[ExpenseIt#17](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseReportPage.xaml#17)]

    Esta ui é *`ExpenseItHome.xaml`* semelhante, exceto que os <xref:System.Windows.Controls.DataGrid>dados do relatório são exibidos em um .

3. Criar e executar o aplicativo.

4. Selecione o botão **Exibir.**

    A página de relatório de despesas é exibida. Observe também que o botão de navegação de volta está ativado.

A ilustração a seguir mostra os elementos de IA adicionados ao *ExpenseReportPage.xaml*.

![Captura de tela de exemplo expenseIt mostrando a ui criada para o ExpenseReportPage.](./media/walkthrough-my-first-wpf-desktop-application/create-application-ui.png)

## <a name="style-controls"></a>Controles de estilo

O aparecimento de vários elementos é muitas vezes o mesmo para todos os elementos do mesmo tipo em uma ui. A ui usa [estilos](../../../desktop-wpf/fundamentals/styles-templates-overview.md) para tornar as aparências reutilizáveis em vários elementos. A reutilização dos estilos ajuda a simplificar a criação e o gerenciamento do XAML. Esta seção substitui os atributos por elemento que foram definidos nas etapas anteriores com estilos.

1. *Abra o Application.xaml* ou *app.xaml*.

2. Adicione o seguinte XAML entre as <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> tags:

    [!code-xaml[ExpenseIt#18](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/App.xaml#18)]

    Esse XAML adiciona os seguintes estilos:

    - `headerTextStyle`: para formatar o título da página <xref:System.Windows.Controls.Label>.

    - `labelStyle`: para formatar os controles <xref:System.Windows.Controls.Label>.

    - `columnHeaderStyle`: para formatar o <xref:System.Windows.Controls.Primitives.DataGridColumnHeader>.

    - `listHeaderStyle`: para formatar os controles <xref:System.Windows.Controls.Border> do cabeçalho da lista.

    - `listHeaderTextStyle`: Para formatar <xref:System.Windows.Controls.Label>o cabeçalho da lista .

    - `buttonStyle`: Para <xref:System.Windows.Controls.Button> formatar o on `ExpenseItHome.xaml`.

    Observe que os estilos são <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> recursos e filhos do elemento propriedade. Nesse local, os estilos são aplicados a todos os elementos em um aplicativo. Para um exemplo de uso de recursos em um aplicativo .NET, consulte [Use Application Resources](../advanced/how-to-use-application-resources.md).

3. Em *`ExpenseItHome.xaml`*, substituir <xref:System.Windows.Controls.Grid> tudo entre os elementos com o seguinte XAML:

    [!code-xaml[ExpenseIt#19](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseItHome.xaml#19)]

    As propriedades como <xref:System.Windows.VerticalAlignment> e <xref:System.Windows.Media.FontFamily> que definem a aparência de cada controle são removidas e substituídas ao aplicar os estilos. Por exemplo, `headerTextStyle` o é aplicado ao "Exibir relatório de despesas". <xref:System.Windows.Controls.Label>

4. Open *ExpenseReportPage.xaml*.

5. Substitua tudo <xref:System.Windows.Controls.Grid> entre os elementos pelo seguinte XAML:

    [!code-xaml[ExpenseIt#20](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseReportPage.xaml#20)]

    Este XAML adiciona <xref:System.Windows.Controls.Label> estilos <xref:System.Windows.Controls.Border> aos elementos.

6. Criar e executar o aplicativo. A aparência da janela é a mesma de antes.

    ![ExpenseIt captura de tela de captura de tela com a mesma aparência da última seção.](./media/walkthrough-my-first-wpf-desktop-application/create-application-ui.png)

7. Feche o aplicativo para retornar ao Visual Studio.

## <a name="bind-data-to-a-control"></a>Vincular dados a um controle

Nesta seção, você criará os dados XML que estão vinculados a vários controles.

1. Em *`ExpenseItHome.xaml`*, após <xref:System.Windows.Controls.Grid> o elemento de abertura, adicione <xref:System.Windows.Data.XmlDataProvider> o seguinte XAML para criar um que contenha os dados de cada pessoa:

    [!code-xaml[ExpenseIt#23](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml?range=13,16-40,49)]

    Os dados são criados como um <xref:System.Windows.Controls.Grid> recurso. Normalmente esses dados seriam carregados como um arquivo, mas para simplificar os dados são adicionados inline.

2. Dentro `<Grid.Resources>` do elemento, `<xref:System.Windows.DataTemplate>` adicione o seguinte elemento, que define <xref:System.Windows.Controls.ListBox>como `<XmlDataProvider>` exibir os dados no , após o elemento:

    [!code-xaml[ExpenseIt#24](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml?range=13,43-46,49)]

    Para obter mais informações sobre modelos de dados, consulte [Visão geral do templating de dados](../data/data-templating-overview.md).

3. Substitua o <xref:System.Windows.Controls.ListBox> existente pelo seguinte XAML:

    [!code-xaml[ExpenseIt#25](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#25)]

    Este XAML vincula <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> a <xref:System.Windows.Controls.ListBox> propriedade da fonte de dados e <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>aplica o modelo de dados como .

## <a name="connect-data-to-controls"></a>Conecte dados a controles

Em seguida, você adicionará código para recuperar o **`ExpenseItHome`** nome selecionado na página e passá-lo para o construtor de **ExpenseReportPage**. **ExpenseReportPage** define seu contexto de dados com o item passado, que é o que os controles definidos em *ExpenseReportPage.xaml* bind to.

1. *Open ExpenseReportPage.xaml.vb* ou *ExpenseReportPage.xaml.cs*.

2. Adicione um construtor que utiliza um objeto para passar os dados do relatório de despesas da pessoa selecionada.

    [!code-csharp[ExpenseIt#26](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseReportPage.xaml.cs#26)]
    [!code-vb[ExpenseIt#26](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseReportPage.xaml.vb#26)]

3. Abra *`ExpenseItHome.xaml.vb`* *`ExpenseItHome.xaml.cs`* ou.

4. Altere <xref:System.Windows.Controls.Primitives.ButtonBase.Click> o manipulador de eventos para chamar o novo construtor passando os dados do relatório de despesas da pessoa selecionada.

    [!code-csharp[ExpenseIt#27](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml.cs#27)]
    [!code-vb[ExpenseIt#27](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseItHome.xaml.vb#27)]

## <a name="style-data-with-data-templates"></a>Dados de estilo com modelos de dados

Nesta seção, você atualizará a ui para cada item nas listas vinculadas a dados usando modelos de dados.

1. Open *ExpenseReportPage.xaml*.

2. Vincule o conteúdo dos elementos <xref:System.Windows.Controls.Label> "Nome" e "Departamento" à propriedade de origem de dados apropriada. Para obter mais informações sobre vinculação de dados, consulte [Visão geral de vinculação de dados](../../../desktop-wpf/data/data-binding-overview.md).

    [!code-xaml[ExpenseIt#31](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#31)]

3. Após o <xref:System.Windows.Controls.Grid> elemento de abertura, adicione os seguintes modelos de dados, que definem como exibir os dados do relatório de despesas:

    [!code-xaml[ExpenseIt#30](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#30)]

4. Substitua <xref:System.Windows.Controls.DataGridTextColumn> os <xref:System.Windows.Controls.DataGridTemplateColumn> elementos por sob o <xref:System.Windows.Controls.DataGrid> elemento e aplique os modelos a eles.

    [!code-xaml[ExpenseIt#32](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#32)]

5. Criar e executar o aplicativo.

6. Selecione uma pessoa e selecione o botão **Exibir.**

A ilustração a `ExpenseIt` seguir mostra ambas as páginas do aplicativo com controles, layout, estilos, vinculação de dados e modelos de dados aplicados:

![Ambas as páginas do aplicativo mostrando a lista de nomes e um relatório de despesas.](./media/walkthrough-my-first-wpf-desktop-application/application-data-templates.png)

> [!NOTE]
> Esta amostra demonstra uma característica específica do WPF e não segue todas as práticas recomendadas para coisas como segurança, localização e acessibilidade. Para obter uma cobertura abrangente das práticas recomendadas de desenvolvimento de aplicativos .NET, consulte os seguintes tópicos:
>
> - [Acessibilidade](../../ui-automation/accessibility-best-practices.md)
> - [Segurança](../security-wpf.md)
> - [Globalização e localização do WPF](../advanced/wpf-globalization-and-localization-overview.md)
> - [Desempenho do WPF](../advanced/optimizing-wpf-application-performance.md)

## <a name="next-steps"></a>Próximas etapas

Neste passo a passo você aprendeu uma série de técnicas para criar uma UI usando o Windows Presentation Foundation (WPF). Agora você deve ter uma compreensão básica dos blocos de construção de um aplicativo .NET vinculado a dados. Para obter mais informações sobre os modelos de arquitetura e programação do WPF, consulte os seguintes tópicos:

- [Arquitetura WPF](../advanced/wpf-architecture.md)
- [Visão geral xaml (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [Visão geral das propriedades de dependência](../advanced/dependency-properties-overview.md)
- [Layout](../advanced/layout.md)

Para obter mais informações sobre como criar aplicativos, consulte os seguintes tópicos:

- [Desenvolvimento de aplicativo](../app-development/index.md)
- [Controles](../controls/index.md)
- [Visão geral de associação de dados](../../../desktop-wpf/data/data-binding-overview.md)
- [Gráficos e multimídia](../graphics-multimedia/index.md)
- [Documentos no WPF](../advanced/documents-in-wpf.md)

## <a name="see-also"></a>Confira também

- [Visão geral dos painéis](../controls/panels-overview.md)
- [Visão geral do templating de dados](../data/data-templating-overview.md)
- [Construa um aplicativo WPF](../app-development/building-a-wpf-application-wpf.md)
- [Estilos e modelos](../controls/styles-and-templates.md)
