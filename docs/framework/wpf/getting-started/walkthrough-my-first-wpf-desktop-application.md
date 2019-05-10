---
title: Criar um aplicativo WPF no Visual Studio
ms.date: 03/20/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- getting started [WPF], WPF
- WPF [WPF], getting started
ms.assetid: b96bed40-8946-4285-8fe4-88045ab854ed
author: mairaw
ms.author: mairaw
ms.custom: vs-dotnet
ms.openlocfilehash: 9d0abd18b2242ab21e8a915caac1ff9e3216acd0
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64617268"
---
# <a name="walkthrough-my-first-wpf-desktop-application"></a>Passo a passo: Meu primeiro aplicativo da área de trabalho do WPF

Este artigo mostra como desenvolver um aplicativo de desktop do Windows Presentation Foundation (WPF) que inclui os elementos que são comuns à maioria dos aplicativos do WPF: Extensible Application Markup Language (XAML) marcação, code-behind, definições de aplicativo, controles, layout, vinculação de dados e estilos. Para desenvolver o aplicativo, você usará o Visual Studio. 

Este passo a passo inclui as seguintes etapas:

- Use XAML para criar a aparência da interface do usuário do aplicativo (UI).

- Escreva código para criar o comportamento do aplicativo.

- Crie uma definição de aplicativo para gerenciar o aplicativo.

- Adicionar controles e criar o layout para compor o interface do usuário do aplicativo.

- Crie estilos para uma aparência consistente em toda a interface do usuário do aplicativo.

- Vincular a interface do usuário aos dados, tanto para preencher a interface do usuário de dados para manter os dados e interface do usuário sincronizado.

Ao final do passo a passo, você será criado um aplicativo do Windows que permite aos usuários exibir relatórios de despesas para pessoas selecionadas autônomo. O aplicativo é composto de várias páginas do WPF que são hospedadas em uma janela de estilo de navegador.

> [!TIP]
> O código de exemplo que é usado para criar este passo a passo está disponível para o Visual Basic e C# na [código de exemplo de aplicativo do passo a passo WPF](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/WalkthroughFirstWPFApp).
>
> Você pode alternar o idioma de código do código de exemplo entre o C# e Visual Basic usando o **\< />** lista suspensa no canto superior direito deste artigo.

## <a name="prerequisites"></a>Pré-requisitos

- Visual Studio 2017 ou posterior

   Para obter mais informações sobre como instalar a versão mais recente do Visual Studio, consulte [instalar o Visual Studio](/visualstudio/install/install-visual-studio). Este artigo usa o Visual Studio de 2019.

## <a name="create-the-application-project"></a>Criar o projeto de aplicativo

A primeira etapa é criar a infraestrutura de aplicativo, que inclui uma definição de aplicativo, duas páginas e uma imagem.

1. Criar um novo projeto de aplicativo do WPF no Visual Basic ou Visual c# denominado **`ExpenseIt`**:

   1. Abra o Visual Studio e selecione **arquivo** > **New** > **projeto**.

      O **criar um novo projeto** caixa de diálogo é aberta.

      ![Criar uma caixa de diálogo Novo projeto](./media/gettingstartedfigure0a.png)

   2. No **linguagem** lista suspensa, selecione **C#** ou **Visual Basic**.

   3. Selecione o **aplicativo WPF (.NET Framework)** modelo e selecione **próxima**. 
    
   4. Selecione **criar um novo projeto**.

      O **configurar um novo projeto** caixa de diálogo é aberta.

      ![Configurar uma caixa de diálogo Novo projeto](./media/gettingstartedfigure0c.png)

   5. Insira o nome do projeto **`ExpenseIt`** e, em seguida, selecione **criar**.

      Visual Studio cria o projeto e abre o designer para a janela do aplicativo padrão chamado **MainWindow. XAML**.

2. Abra *Application. XAML* (Visual Basic) ou *App. XAML* (c#).

    Esse arquivo XAML define um aplicativo WPF e quaisquer recursos do aplicativo. Você também usar esse arquivo para especificar a interface do usuário, nesse caso *MainWindow. XAML*, que mostra automaticamente quando o aplicativo é iniciado.

    O XAML deve ser semelhante ao seguinte no Visual Basic:

    [!code-xaml[ExpenseIt#1_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/Application.xaml#1_a)]

    E semelhante ao seguinte em C#:

    [!code-xaml[ExpenseIt#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/App.xaml#1)]

3. Abra *MainWindow. XAML*.

    Esse arquivo XAML é a janela principal do seu aplicativo e exibe o conteúdo criado em páginas. O <xref:System.Windows.Window> classe define as propriedades de uma janela, como seu título, tamanho ou ícone e manipula eventos, como fechar ou ocultar.

4. Alterar o <xref:System.Windows.Window> elemento para um <xref:System.Windows.Navigation.NavigationWindow>, como mostra o XAML a seguir:

   ```xaml
   <NavigationWindow x:Class="ExpenseIt.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        ...
   </NavigationWindow>
   ```

   Este aplicativo navega para um conteúdo diferente dependendo da entrada do usuário. É por isso que o principal <xref:System.Windows.Window> precisa ser alterado para um <xref:System.Windows.Navigation.NavigationWindow>. <xref:System.Windows.Navigation.NavigationWindow> herda todas as propriedades de <xref:System.Windows.Window>. O <xref:System.Windows.Navigation.NavigationWindow> elemento no arquivo XAML cria uma instância do <xref:System.Windows.Navigation.NavigationWindow> classe. Para obter mais informações, consulte [visão geral da navegação](../app-development/navigation-overview.md).

5. Remover o <xref:System.Windows.Controls.Grid> elementos entre o <xref:System.Windows.Navigation.NavigationWindow> marcas.

6. Alterar as propriedades a seguir no código XAML para o <xref:System.Windows.Navigation.NavigationWindow> elemento:

    - Defina as <xref:System.Windows.Window.Title%2A> propriedade para "`ExpenseIt`".

    - Defina o <xref:System.Windows.FrameworkElement.Height%2A> propriedade para 350 pixels.

    - Defina o <xref:System.Windows.FrameworkElement.Width%2A> propriedade para 500 pixels.

    O XAML deve ser semelhante ao seguinte para o Visual Basic:

    [!code-xaml[ExpenseIt#2_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt/MainWindow.xaml#2_a)]

    E com o seguinte para C#:

    [!code-xaml[ExpenseIt#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/MainWindow.xaml#2)]

7. Abra *. XAML. vb* ou *MainWindow.xaml.cs*.

    Esse arquivo é um arquivo code-behind que contém o código para manipular os eventos declarados em *MainWindow. XAML*. Esse arquivo contém uma classe parcial para a janela definida no XAML.

8. Se você estiver usando o C#, altere o `MainWindow` classe derivar <xref:System.Windows.Navigation.NavigationWindow>. (No Visual Basic, isso ocorre automaticamente quando você altera a janela no XAML.) O C# código agora deve ser assim:

   [!code-csharp[ExpenseIt#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/MainWindow.xaml.cs?highlight=21)]

## <a name="add-files-to-the-application"></a>Adicionar arquivos ao aplicativo

Nesta seção, você adicionará duas páginas e uma imagem ao aplicativo.

1. Adicione uma nova página ao projeto e denomine *`ExpenseItHome.xaml`*:

   1. Na **Gerenciador de soluções**, clique com botão direito no **`ExpenseIt`** nó do projeto e escolha **Add** > **página**.

   1. No **Adicionar Novo Item** caixa de diálogo, o **página (WPF)** modelo já está selecionado. Insira o nome **`ExpenseItHome`** e, em seguida, selecione **Add**.

    Esta página é a primeira página que é exibida quando o aplicativo é iniciado. Ela mostrará uma lista de pessoas para selecionar, para mostrar um relatório de despesas.

1. Abra *`ExpenseItHome.xaml`*.

1. Defina as <xref:System.Windows.Controls.Page.Title%2A> para "`ExpenseIt - Home`".

1. Defina as `DesignHeight` e `DesignWidth` valores de elemento para 300 pixels.

    O XAML agora aparece da seguinte maneira para o Visual Basic:

    [!code-xaml[ExpenseIt#6_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml#6_a)]

    E com o seguinte para C#:

    [!code-xaml[ExpenseIt#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml#6)]

1. Abra *MainWindow. XAML*.

1. Adicionar um <xref:System.Windows.Navigation.NavigationWindow.Source%2A> propriedade para o <xref:System.Windows.Navigation.NavigationWindow> elemento e defini-lo como "`ExpenseItHome.xaml`".

    Isso define *`ExpenseItHome.xaml`* ser a primeira página aberta quando o aplicativo é iniciado. 

    Exemplo de XAML no Visual Basic:

    [!code-xaml[ExpenseIt#7_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/MainWindow.xaml#7_a)]

    E, em C#:

    [!code-xaml[ExpenseIt#7](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/MainWindow.xaml#7)]

   > [!TIP]
   > Você também pode definir a **fonte** propriedade no **diversos** categoria da **propriedades** janela.
   >
   > ![Propriedade de origem na janela Propriedades](./media/properties-source.png)

1. Adicione outra nova página do WPF ao projeto e denomine *ExpenseReportPage*::

   1. Na **Gerenciador de soluções**, clique com botão direito no **`ExpenseIt`** nó do projeto e escolha **Add** > **página**.

   1. No **Adicionar Novo Item** caixa de diálogo, selecione o **página (WPF)** modelo. Insira o nome **ExpenseReportPage**e, em seguida, selecione **Add**.

    Essa página mostrará o relatório de despesas da pessoa que está selecionada na **`ExpenseItHome`** página.

1. Abra *ExpenseReportPage.xaml*.

1. Defina as <xref:System.Windows.Controls.Page.Title%2A> para "`ExpenseIt - View Expense`".

1. Defina as `DesignHeight` e `DesignWidth` valores de elemento para 300 pixels.

    *ExpenseReportPage. XAML* agora é semelhante ao seguinte no Visual Basic:

    [!code-xaml[ExpenseIt#4_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml#4_a)]

    E semelhante ao seguinte em C#:

    [!code-xaml[ExpenseIt#4](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml#4)]

1. Abra *Expenseithome* e *ExpenseReportPage*, ou *ExpenseItHome.xaml.cs* e *ExpenseReportPage.xaml.cs*.

    Quando você cria um novo arquivo de página, o Visual Studio cria automaticamente seus *de lógica* arquivo. Esses arquivos code-behind manipulam a lógica para responder à entrada do usuário.

    Seu código deve ser semelhante ao seguinte para **`ExpenseItHome`**:

    [!code-csharp[ExpenseIt#2_5](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml.cs#2_5)]

    [!code-vb[ExpenseIt#2_5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml.vb#2_5)]

    E com o seguinte para **ExpenseReportPage**:

    [!code-csharp[ExpenseIt#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml.cs#5)]

    [!code-vb[ExpenseIt#5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml.vb#5)]

1. Adicione uma imagem chamada *watermark* ao projeto. Você pode criar sua própria imagem, copie o arquivo de código de exemplo ou obtê-lo [aqui](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/WalkthroughFirstWPFApp).

    1. Clique com botão direito no nó do projeto e selecione **Add** > **Item existente**, ou pressione **Shift**+**Alt** + **Um**.

    2. No **Adicionar Item existente** caixa de diálogo, defina o filtro de arquivo como **todos os arquivos** ou **arquivos de imagem**, navegue até o arquivo de imagem que você deseja usar e, em seguida, selecione **adicionar** .

## <a name="build-and-run-the-application"></a>Compilar e executar o aplicativo

1. Para compilar e executar o aplicativo, pressione **F5** ou selecione **iniciar depuração** do **depurar** menu.

    A ilustração a seguir mostra o aplicativo com o <xref:System.Windows.Navigation.NavigationWindow> botões:

    ![Captura de tela de exemplo de ExpenseIt](./media/gettingstartedfigure1.png)

2. Feche o aplicativo para retornar ao Visual Studio.

## <a name="create-the-layout"></a>Criar o layout

Layout oferece uma maneira ordenada para posicionar os elementos de interface do usuário e também gerencia o tamanho e a posição desses elementos quando uma interface do usuário é redimensionado. Normalmente, você cria um layout com um dos seguintes controles de layout:

- <xref:System.Windows.Controls.Canvas> -Define uma área na qual você pode posicionar explicitamente elementos filho usando coordenadas são relativas à área da tela.
- <xref:System.Windows.Controls.DockPanel> -Define uma área onde você pode organizar elementos filho horizontal ou verticalmente, relativos uns aos outros.
- <xref:System.Windows.Controls.Grid> -Define uma área de grade flexível que consiste em linhas e colunas.
- <xref:System.Windows.Controls.StackPanel> -Organiza elementos filho em uma única linha que pode ser orientada horizontal ou verticalmente.
- <xref:System.Windows.Controls.VirtualizingStackPanel> -Organiza e virtualiza conteúdo em uma única linha que é orientada horizontal ou verticalmente.
- <xref:System.Windows.Controls.WrapPanel> -Coloca os elementos filho na posição sequencial da esquerda para a direita, quebrando o conteúdo para a próxima linha na borda da caixa delimitadora. A ordenação posterior ocorre sequencialmente de cima para baixo ou da direita para a esquerda, dependendo do valor da propriedade Orientation.

Cada um desses controles de layout dá suporte a um determinado tipo de layout para seus elementos filho. `ExpenseIt` as páginas podem ser redimensionadas e cada página tem elementos que são organizados horizontalmente e verticalmente juntamente com outros elementos. Neste exemplo, o <xref:System.Windows.Controls.Grid> é usado como o elemento de layout para o aplicativo.

> [!TIP]
> Para obter mais informações sobre <xref:System.Windows.Controls.Panel> elementos, consulte [visão geral de painéis](../controls/panels-overview.md). Para obter mais informações sobre layout, consulte [Layout](../advanced/layout.md).

Nesta seção, você cria uma tabela de coluna única com três linhas e uma margem de 10 pixels adicionando definições de linha e coluna para o <xref:System.Windows.Controls.Grid> na *`ExpenseItHome.xaml`*.

1. Na *`ExpenseItHome.xaml`*, defina as <xref:System.Windows.FrameworkElement.Margin%2A> propriedade no <xref:System.Windows.Controls.Grid> elemento a ser "10,0,10,10", que corresponde às margens esquerda, superior, direita e inferior:

   ```xaml
   <Grid Margin="10,0,10,10">
   ```

   > [!TIP]
   > Você também pode definir a **margem** os valores na **propriedades** janela, na **Layout** categoria:
   >
   > ![Valores de margem na janela Propriedades](./media/properties-margin.png)

2. Adicione o seguinte XAML entre o <xref:System.Windows.Controls.Grid> marcas para criar as definições de linha e coluna:

    [!code-xaml[ExpenseIt#8](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#8)]

    O <xref:System.Windows.Controls.RowDefinition.Height%2A> de duas linhas é definido como <xref:System.Windows.GridLength.Auto%2A>, o que significa que as linhas são dimensionadas com base no conteúdo de linhas. O padrão <xref:System.Windows.Controls.RowDefinition.Height%2A> é <xref:System.Windows.GridUnitType.Star> dimensionamento, o que significa que a altura da linha é uma proporção ponderada do espaço disponível. Por exemplo, se duas linhas tiverem uma <xref:System.Windows.Controls.RowDefinition.Height%2A> de "*", cada um deles tem uma altura que será a metade do espaço disponível.

    Seu <xref:System.Windows.Controls.Grid> agora deve conter o seguinte XAML:

    [!code-xaml[ExpenseIt#9](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#9)]

## <a name="add-controls"></a>Adicionar controles

Nesta seção, você atualizará a página inicial da interface do usuário para mostrar uma lista de pessoas, em que você selecione uma pessoa para exibir seus relatórios de despesas. Os controles são objetos da interface do usuário que permitem aos usuários interagir com seu aplicativo. Para obter mais informações, consulte [Controles](../controls/index.md).

Para criar essa interface do usuário, você adicionará os seguintes elementos para *`ExpenseItHome.xaml`*:

- Um <xref:System.Windows.Controls.ListBox> (para obter a lista de pessoas).
- Um <xref:System.Windows.Controls.Label> (para o cabeçalho da lista).
- Um <xref:System.Windows.Controls.Button> (para clicar para exibir o relatório de despesas para a pessoa que está selecionada na lista).

Cada controle é colocado em uma linha do <xref:System.Windows.Controls.Grid> definindo o <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> propriedade anexada. Para obter mais informações sobre propriedades anexadas, consulte [visão geral das propriedades anexadas](../advanced/attached-properties-overview.md).

1. Na *`ExpenseItHome.xaml`*, adicione o seguinte XAML em algum lugar entre o <xref:System.Windows.Controls.Grid> marcas:

   [!code-xaml[ExpenseIt#10](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt4/ExpenseItHome.xaml#10)]

   > [!TIP]
   > Você também pode criar os controles arrastando-os do **caixa de ferramentas** janela para a janela de design e, em seguida, definir suas propriedades na **propriedades** janela.

2. Crie e execute o aplicativo.

    A ilustração a seguir mostra os controles que você criou:

    ![Captura de tela de exemplo de ExpenseIt](./media/gettingstartedfigure2.png)

3. Feche o aplicativo para retornar ao Visual Studio.

## <a name="add-an-image-and-a-title"></a>Adicionar uma imagem e um título

Nesta seção, você vai atualizar a home page da interface do usuário com uma imagem e um título de página.

1. Na *`ExpenseItHome.xaml`*, adicione outra coluna para o <xref:System.Windows.Controls.Grid.ColumnDefinitions%2A> fixa <xref:System.Windows.Controls.ColumnDefinition.Width%2A> de 230 pixels:

    [!code-xaml[ExpenseIt#11](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseItHome.xaml?highlight=52-55)]

2. Adicionar outra linha para o <xref:System.Windows.Controls.Grid.RowDefinitions%2A>, para um total de quatro linhas:

    [!code-xaml[ExpenseIt#11b](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseItHome.xaml?highlight=57-62)]

3. Mova os controles para a segunda coluna, definindo o <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> propriedade como 1 em cada um dos três controles (da borda, ListBox e botão).

4. Mova cada controle uma linha para baixo ao incrementar sua <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> valor 1 para cada um dos três controles (da borda, ListBox e botão) e para o elemento Border.

   O XAML para os três controles agora é semelhante ao seguinte:

    [!code-xaml[ExpenseIt#12](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#12)]

5. Definir a <xref:System.Windows.Controls.Panel.Background%2A?displayProperty=nameWithType> propriedade para o *watermark* arquivo de imagem, adicionando o XAML a seguir em qualquer lugar entre os `<Grid>` e `</Grid>` marcas:

    [!code-xaml[ExpenseIt#14](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#14)]

6. Antes do <xref:System.Windows.Controls.Border> elemento, adicionar um <xref:System.Windows.Controls.Label> com o conteúdo "Exibir relatório de despesas". Esse rótulo é o título da página.

    [!code-xaml[ExpenseIt#13](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#13)]

7. Crie e execute o aplicativo.

A ilustração a seguir mostra os resultados de que você acabou de adicionar:

![Captura de tela de exemplo de ExpenseIt](./media/gettingstartedfigure3.png)

## <a name="add-code-to-handle-events"></a>Adicionar código para manipular eventos

1. Na *`ExpenseItHome.xaml`*, adicione uma <xref:System.Windows.Controls.Primitives.ButtonBase.Click> manipulador de eventos para o <xref:System.Windows.Controls.Button> elemento. Para obter mais informações, confira [Como: Crie um manipulador de eventos simples](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb675300(v=vs.100)).

    [!code-xaml[ExpenseIt#15](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml#15)]

2. Abra *`ExpenseItHome.xaml.vb`* ou *`ExpenseItHome.xaml.cs`*.

3. Adicione o seguinte código para o `ExpenseItHome` classe para adicionar um botão de manipulador de eventos de clique. O manipulador de eventos abre o **ExpenseReportPage** página.

    [!code-csharp[ExpenseIt#16](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml.cs#16)]
    [!code-vb[ExpenseIt#16](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt6/ExpenseItHome.xaml.vb#16)]

## <a name="create-the-ui-for-expensereportpage"></a>Criar a interface do usuário para ExpenseReportPage

*ExpenseReportPage. XAML* exibe o relatório de despesas para a pessoa que está selecionada na **`ExpenseItHome`** página. Nesta seção, você criará a interface do usuário para **ExpenseReportPage**. Você também adicionará o plano de fundo e cores de preenchimento para os vários elementos de interface do usuário.

1. Abra *ExpenseReportPage.xaml*.

2. Adicione o seguinte XAML entre o <xref:System.Windows.Controls.Grid> marcas:

    [!code-xaml[ExpenseIt#17](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseReportPage.xaml#17)]

    Essa interface do usuário é semelhante à *`ExpenseItHome.xaml`*, exceto os dados do relatório são exibidos em um <xref:System.Windows.Controls.DataGrid>.

3. Crie e execute o aplicativo.

4. Selecione o **exibição** botão.

    A página de relatório de despesas é exibida. Além disso, observe que o botão de navegação regressiva está habilitado.

A ilustração a seguir mostra os elementos de interface do usuário adicionados ao *ExpenseReportPage. XAML*.

![Captura de tela de exemplo de ExpenseIt](./media/gettingstartedfigure4.png)

## <a name="style-controls"></a>Controles de estilo

A aparência de vários elementos geralmente é o mesmo para todos os elementos do mesmo tipo em uma interface do usuário. Interface do usuário usa [estilos](../controls/styling-and-templating.md) para fazer com que as aparências reutilizáveis entre vários elementos. A capacidade de reutilização dos estilos ajuda a simplificar o gerenciamento e a criação de XAML. Esta seção substitui os atributos por elemento que foram definidos nas etapas anteriores com estilos.

1. Abra *Application. XAML* ou *App. XAML*.

2. Adicione o seguinte XAML entre o <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> marcas:

    [!code-xaml[ExpenseIt#18](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/App.xaml#18)]

    Esse XAML adiciona os seguintes estilos:

    - `headerTextStyle`: Para formatar o título da página <xref:System.Windows.Controls.Label>.

    - `labelStyle`: Para formatar o <xref:System.Windows.Controls.Label> controles.

    - `columnHeaderStyle`: Para formatar o <xref:System.Windows.Controls.Primitives.DataGridColumnHeader>.

    - `listHeaderStyle`: Para formatar o cabeçalho da lista <xref:System.Windows.Controls.Border> controles.

    - `listHeaderTextStyle`: Para formatar o cabeçalho da lista <xref:System.Windows.Controls.Label>.

    - `buttonStyle`: Para formatar a <xref:System.Windows.Controls.Button> em `ExpenseItHome.xaml`.

    Observe que os estilos são recursos e seus filhos a <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> elemento de propriedade. Nesse local, os estilos são aplicados a todos os elementos em um aplicativo. Para obter um exemplo do uso de recursos em um aplicativo .NET, consulte [usar recursos do aplicativo](../advanced/how-to-use-application-resources.md).

3. Na *`ExpenseItHome.xaml`*, substitua tudo entre os <xref:System.Windows.Controls.Grid> elementos com o XAML a seguir:

    [!code-xaml[ExpenseIt#19](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseItHome.xaml#19)]

    As propriedades como <xref:System.Windows.VerticalAlignment> e <xref:System.Windows.Media.FontFamily> que definem a aparência de cada controle são removidas e substituídas ao aplicar os estilos. Por exemplo, o `headerTextStyle` é aplicado a "Exibir relatório de despesas" <xref:System.Windows.Controls.Label>.

4. Abra *ExpenseReportPage.xaml*.

5. Substitua tudo entre os <xref:System.Windows.Controls.Grid> elementos com o XAML a seguir:

    [!code-xaml[ExpenseIt#20](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseReportPage.xaml#20)]

    Esse XAML adiciona estilos para o <xref:System.Windows.Controls.Label> e <xref:System.Windows.Controls.Border> elementos.

6. Crie e execute o aplicativo. A aparência da janela é o mesmo que anteriormente.

    ![Captura de tela de exemplo de ExpenseIt](./media/gettingstartedfigure4.png)

7. Feche o aplicativo para retornar ao Visual Studio.

## <a name="bind-data-to-a-control"></a>Associar dados a um controle

Nesta seção, você criará os dados XML que estão associados a vários controles.

1. Na *`ExpenseItHome.xaml`*, após a abertura <xref:System.Windows.Controls.Grid> elemento, adicione o XAML a seguir para criar um <xref:System.Windows.Data.XmlDataProvider> que contém os dados para cada pessoa:

    [!code-xaml[ExpenseIt#23](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml?range=13,16-40,49)]

    Os dados são criados como um <xref:System.Windows.Controls.Grid> recursos. Normalmente, esses dados seriam carregados como um arquivo, mas para simplificar os dados são adicionados embutidos.

2. Dentro de `<Grid.Resources>` elemento, adicione o seguinte `<xref:System.Windows.DataTemplate>` elemento, que define como exibir os dados no <xref:System.Windows.Controls.ListBox>, após o `<XmlDataProvider>` elemento:

    [!code-xaml[ExpenseIt#24](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml?range=13,43-46,49)]

    Para obter mais informações sobre modelos de dados, consulte [visão geral de modelagem de dados](../data/data-templating-overview.md).

3. Substitua a <xref:System.Windows.Controls.ListBox> com o XAML a seguir:

    [!code-xaml[ExpenseIt#25](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#25)]

    Esse XAML associa a <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> propriedade do <xref:System.Windows.Controls.ListBox> à fonte de dados e aplica o modelo de dados como o <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>.

## <a name="connect-data-to-controls"></a>Conectar dados aos controles

Em seguida, você adicionará código para recuperar o nome que está selecionado na **`ExpenseItHome`** da página e passá-lo para o construtor da **ExpenseReportPage**. **ExpenseReportPage** define seu contexto de dados com o item passado, que é o que os controles definidos no *ExpenseReportPage* associar a.

1. Abra *ExpenseReportPage.xaml.vb* ou *ExpenseReportPage.xaml.cs*.

2. Adicione um construtor que utiliza um objeto para passar os dados do relatório de despesas da pessoa selecionada.

    [!code-csharp[ExpenseIt#26](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseReportPage.xaml.cs#26)]
    [!code-vb[ExpenseIt#26](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseReportPage.xaml.vb#26)]

3. Abra *`ExpenseItHome.xaml.vb`* ou *`ExpenseItHome.xaml.cs`*.

4. Alterar o <xref:System.Windows.Controls.Primitives.ButtonBase.Click> manipulador de eventos para chamar o novo construtor passando os dados de relatório de despesas da pessoa selecionada.

    [!code-csharp[ExpenseIt#27](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml.cs#27)]
    [!code-vb[ExpenseIt#27](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseItHome.xaml.vb#27)]

## <a name="style-data-with-data-templates"></a>Dados de estilo com modelos de dados

Nesta seção, você atualizará a interface do usuário para cada item nas listas de associação de dados usando modelos de dados.

1. Abra *ExpenseReportPage.xaml*.

2. Associar o conteúdo do "Nome" e "Departamento" <xref:System.Windows.Controls.Label> propriedade da fonte de elementos para os dados apropriados. Para obter mais informações sobre associação de dados, consulte [visão geral da vinculação de dados](../data/data-binding-overview.md).

    [!code-xaml[ExpenseIt#31](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#31)]

3. Após a abertura <xref:System.Windows.Controls.Grid> elemento, adicione os seguintes modelos de dados, que definem como exibir os dados de relatório de despesas:

    [!code-xaml[ExpenseIt#30](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#30)]

4. Substitua os <xref:System.Windows.Controls.DataGridTextColumn> elementos com <xref:System.Windows.Controls.DataGridTemplateColumn> sob o <xref:System.Windows.Controls.DataGrid> elemento e aplicar os modelos a eles.

    [!code-xaml[ExpenseIt#32](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#32)]

5. Crie e execute o aplicativo.

6. Selecione uma pessoa e, em seguida, selecione a **exibição** botão.

A ilustração a seguir mostra as duas páginas do `ExpenseIt` aplicativo com controles, layout, estilos, vinculação de dados e modelos de dados aplicados:

![Capturas de tela de exemplo de ExpenseIt](./media/gettingstartedfigure5.png)

> [!NOTE]
> Este exemplo demonstra um recurso específico do WPF e não segue todas as práticas recomendadas para coisas como segurança, localização e acessibilidade. Para obter uma cobertura abrangente do WPF e as práticas recomendadas de desenvolvimento de aplicativo .NET, consulte os tópicos a seguir:
>
> - [Acessibilidade](../../ui-automation/accessibility-best-practices.md)
>
> - [Segurança](../security-wpf.md)
>
> - [Globalização e localização do WPF](../advanced/wpf-globalization-and-localization-overview.md)
>
> - [Desempenho do WPF](../advanced/optimizing-wpf-application-performance.md)

## <a name="next-steps"></a>Próximas etapas

Neste passo a passo, você aprendeu várias técnicas para a criação de uma interface do usuário usando o Windows Presentation Foundation (WPF). Agora você deve ter uma compreensão básica dos blocos de construção de um aplicativo .NET de associação de dados. Para obter mais informações sobre os modelos de arquitetura e programação do WPF, consulte os seguintes tópicos:

- [Arquitetura do WPF](../advanced/wpf-architecture.md)
- [Visão geral do XAML (WPF)](../advanced/xaml-overview-wpf.md)
- [Visão geral das propriedades de dependência](../advanced/dependency-properties-overview.md)
- [Layout](../advanced/layout.md)

Para obter mais informações sobre como criar aplicativos, consulte os seguintes tópicos:

- [Desenvolvimento de aplicativos](../app-development/index.md)
- [Controles](../controls/index.md)
- [Visão geral da associação de dados](../data/data-binding-overview.md)
- [Elementos gráficos e multimídia](../graphics-multimedia/index.md)
- [Documentos no WPF](../advanced/documents-in-wpf.md)

## <a name="see-also"></a>Consulte também

- [Visão geral de painéis](../controls/panels-overview.md)
- [Visão geral de modelagem de dados](../data/data-templating-overview.md)
- [Compilar um aplicativo WPF](../app-development/building-a-wpf-application-wpf.md)
- [Estilos e modelos](../controls/styles-and-templates.md)
