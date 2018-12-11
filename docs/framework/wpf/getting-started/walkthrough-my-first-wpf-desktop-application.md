---
title: Criar um aplicativo WPF no Visual Studio
ms.date: 10/26/2018
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
ms.openlocfilehash: 6ea5997906c0bf34de67a6a125552d2b2c4e1a43
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53150739"
---
# <a name="walkthrough-my-first-wpf-desktop-application"></a>Passo a passo: Meu primeiro aplicativo da área de trabalho do WPF

Este artigo mostra como desenvolver um aplicativo simples do Windows Presentation Foundation (WPF) que inclui os elementos que são comuns à maioria dos aplicativos do WPF: Extensible Application Markup Language (XAML) marcação, code-behind, definições de aplicativo, controles, layout, vinculação de dados e estilos.

Este passo a passo inclui as seguintes etapas:

- Use XAML para criar a aparência da interface do usuário do aplicativo (UI).

- Escreva código para criar o comportamento do aplicativo.

- Crie uma definição de aplicativo para gerenciar o aplicativo.

- Adicionar controles e criar o layout para compor o interface do usuário do aplicativo.

- Crie estilos para uma aparência consistente em toda a interface de usuário do aplicativo.

- Associe a interface do usuário a dados popular a IU de dados e manter os dados e a interface do usuário sincronizado.

Ao final do passo a passo, você será criado um aplicativo do Windows que permite aos usuários exibir relatórios de despesas para pessoas selecionadas autônomo. O aplicativo é composto de várias páginas do WPF que são hospedadas em uma janela de estilo de navegador.

> [!TIP]
> O código de exemplo que é usado para criar este passo a passo está disponível para o Visual Basic e c# na [Introdução à criação de aplicativos WPF](https://go.microsoft.com/fwlink/?LinkID=160008).

## <a name="prerequisites"></a>Pré-requisitos

- Visual Studio 2017 ou posterior

   Para obter mais informações sobre como instalar a versão mais recente do Visual Studio, consulte [instalar o Visual Studio](/visualstudio/install/install-visual-studio).

## <a name="create-the-application-project"></a>Criar o projeto de aplicativo

A primeira etapa é criar a infraestrutura de aplicativo, que inclui uma definição de aplicativo, duas páginas e uma imagem.

1. Criar um novo projeto de aplicativo do WPF no Visual Basic ou Visual c# denominado **`ExpenseIt`**:

   1. Abra o Visual Studio e selecione **arquivo** > **New** > **projeto**.

      O **novo projeto** caixa de diálogo é aberta.

   2. Sob o **instalados** categoria, expanda o **Visual C#**  ou **Visual Basic** nó e, em seguida, selecione **área de trabalho do Windows**.

   3. Selecione o **aplicativo WPF (.NET Framework)** modelo. Insira o nome **`ExpenseIt`** e, em seguida, selecione **Okey**.

      ![Caixa de diálogo Nova projeto com o aplicativo do WPF selecionado](media/new-project-dialog.png)

      Visual Studio cria o projeto e abre o designer para a janela do aplicativo padrão chamado **MainWindow. XAML**.

   > [!NOTE]
   > Este passo a passo usa o <xref:System.Windows.Controls.DataGrid> controle que está disponível no .NET Framework 4 e posterior. Ser-se de que seu projeto tem como alvo o .NET Framework 4 ou posterior. Para obter mais informações, consulte [como: Uma versão do .NET Framework de destino](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework).

2. Abra *Application. XAML* (Visual Basic) ou *App. XAML* (c#).

    Esse arquivo XAML define um aplicativo WPF e quaisquer recursos do aplicativo. Você também usar esse arquivo para especificar a interface do usuário que mostra automaticamente quando o aplicativo é iniciado; Nesse caso, *MainWindow. XAML*.

    O XAML deve ter esta aparência no Visual Basic:

    [!code-xaml[ExpenseIt#1_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/Application.xaml#1_a)]

    Ou assim no C#:

    [!code-xaml[ExpenseIt#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/App.xaml#1)]

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

   Este aplicativo navega para um conteúdo diferente dependendo da entrada do usuário. É por isso que o principal <xref:System.Windows.Window> precisa ser alterado para um <xref:System.Windows.Navigation.NavigationWindow>. <xref:System.Windows.Navigation.NavigationWindow> herda todas as propriedades de <xref:System.Windows.Window>. O <xref:System.Windows.Navigation.NavigationWindow> elemento no arquivo XAML cria uma instância do <xref:System.Windows.Navigation.NavigationWindow> classe. Para obter mais informações, consulte [visão geral da navegação](../../../../docs/framework/wpf/app-development/navigation-overview.md).

5. Alterar as propriedades a seguir sobre o <xref:System.Windows.Navigation.NavigationWindow> elemento:

    - Defina as <xref:System.Windows.Window.Title%2A> propriedade para "`ExpenseIt`".

    - Defina o <xref:System.Windows.FrameworkElement.Width%2A> propriedade para 500 pixels.

    - Defina o <xref:System.Windows.FrameworkElement.Height%2A> propriedade para 350 pixels.

    - Remover o <xref:System.Windows.Controls.Grid> elementos entre o <xref:System.Windows.Navigation.NavigationWindow> marcas.

    O XAML deve ter esta aparência no Visual Basic:

    [!code-xaml[ExpenseIt#2_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt/MainWindow.xaml#2_a)]

    Ou assim no C#:

    [!code-xaml[ExpenseIt#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/MainWindow.xaml#2)]

6. Abra *. XAML. vb* ou *MainWindow.xaml.cs*.

    Esse arquivo é um arquivo code-behind que contém o código para manipular os eventos declarados em *MainWindow. XAML*. Esse arquivo contém uma classe parcial para a janela definida no XAML.

7. Se você estiver usando c#, altere o `MainWindow` classe para derivar de <xref:System.Windows.Navigation.NavigationWindow>. (No Visual Basic, isso ocorre automaticamente quando você altera a janela no XAML.)

   Seu código deve ter esta aparência:

   [!code-csharp[ExpenseIt#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/MainWindow.xaml.cs#3)]
   [!code-vb[ExpenseIt#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/MainWindow.xaml.vb#3)]

   > [!TIP]
   > Você pode alternar o idioma de código do código de exemplo entre c# e Visual Basic na **linguagem** lista suspensa no canto superior direito deste artigo.

## <a name="add-files-to-the-application"></a>Adicionar arquivos ao aplicativo

Nesta seção, você adicionará duas páginas e uma imagem ao aplicativo.

1. Adicione uma nova página do WPF ao projeto e denomine *`ExpenseItHome.xaml`*:

   1. Na **Gerenciador de soluções**, clique com botão direito no **`ExpenseIt`** nó do projeto e escolha **Add** > **página**.

   1. No **Adicionar Novo Item** caixa de diálogo, o **página (WPF)** modelo já está selecionado. Insira o nome **`ExpenseItHome`** e, em seguida, selecione **Add**.

    Esta página é a primeira página que é exibida quando o aplicativo é iniciado. Ela mostrará uma lista de pessoas para selecionar, para mostrar um relatório de despesas.

2. Abra *`ExpenseItHome.xaml`*.

3. Defina as <xref:System.Windows.Controls.Page.Title%2A> para "`ExpenseIt - Home`".

    O XAML deve ter esta aparência no Visual Basic:

    [!code-xaml[ExpenseIt#6_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml#6_a)]

    Ou em C#:

    [!code-xaml[ExpenseIt#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml#6)]

4. Abra *MainWindow. XAML*.

5. Defina as <xref:System.Windows.Navigation.NavigationWindow.Source%2A> propriedade no <xref:System.Windows.Navigation.NavigationWindow> para "`ExpenseItHome.xaml`".

    Isso define *`ExpenseItHome.xaml`* ser a primeira página aberta quando o aplicativo é iniciado. O XAML deve ter esta aparência no Visual Basic:

    [!code-xaml[ExpenseIt#7_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/MainWindow.xaml#7_a)]

    Ou em C#:

    [!code-xaml[ExpenseIt#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/MainWindow.xaml#7)]

   > [!TIP]
   > Você também pode definir a **fonte** propriedade no **diversos** categoria da **propriedades** janela.
   >
   > ![Propriedade de origem na janela Propriedades](media/properties-source.png)

6. Adicione outra nova página do WPF ao projeto e denomine *ExpenseReportPage*::

   1. Na **Gerenciador de soluções**, clique com botão direito no **`ExpenseIt`** nó do projeto e escolha **Add** > **página**.

   1. No **Adicionar Novo Item** caixa de diálogo, o **página (WPF)** modelo já está selecionado. Insira o nome **ExpenseReportPage**e, em seguida, selecione **Add**.

    Essa página mostrará o relatório de despesas da pessoa que está selecionada na **`ExpenseItHome`** página.

7. Abra *ExpenseReportPage.xaml*.

8. Defina as <xref:System.Windows.Controls.Page.Title%2A> para "`ExpenseIt - View Expense`".

    O XAML deve ter esta aparência no Visual Basic:

    [!code-xaml[ExpenseIt#4_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml#4_a)]

    Ou em C#:

    [!code-xaml[ExpenseIt#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml#4)]

9. Abra *Expenseithome* e *ExpenseReportPage*, ou *ExpenseItHome.xaml.cs* e *ExpenseReportPage.xaml.cs*.

    Quando você cria um novo arquivo de página, o Visual Studio cria automaticamente um *de lógica* arquivo. Esses arquivos code-behind manipulam a lógica para responder à entrada do usuário.

    Seu código deve parecer com isso para **`ExpenseItHome`**:

    [!code-csharp[ExpenseIt#2_5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml.cs#2_5)]
    [!code-vb[ExpenseIt#2_5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml.vb#2_5)]

    E como este para **ExpenseReportPage**:

    [!code-csharp[ExpenseIt#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml.cs#5)]
    [!code-vb[ExpenseIt#5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml.vb#5)]

10. Adicione uma imagem chamada *watermark* ao projeto. Você pode criar sua própria imagem, copie o arquivo de código de exemplo ou obtê-lo [aqui](https://github.com/dotnet/docs/blob/master/docs/framework/wpf/getting-started/media/watermark.png).

   1. Clique com botão direito no nó do projeto e selecione **Add** > **Item existente**, ou pressione **Shift**+**Alt** + **Um**.

   2. No **Adicionar Item existente** caixa de diálogo, navegue até o arquivo de imagem que você deseja usar e, em seguida, selecione **Add**.

## <a name="build-and-run-the-application"></a>Compilar e executar o aplicativo

1. Para compilar e executar o aplicativo, pressione **F5** ou selecione **iniciar depuração** do **depurar** menu.

    A ilustração a seguir mostra o aplicativo com o <xref:System.Windows.Navigation.NavigationWindow> botões:

    ![Captura de tela de exemplo de ExpenseIt](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure1.png)

2. Feche o aplicativo para retornar ao Visual Studio.

## <a name="create-the-layout"></a>Criar o layout

Layout oferece uma maneira ordenada para posicionar os elementos de interface do usuário e também gerencia o tamanho e a posição desses elementos quando uma interface do usuário é redimensionado. Normalmente, você cria um layout com um dos seguintes controles de layout:

- <xref:System.Windows.Controls.Canvas>
- <xref:System.Windows.Controls.DockPanel>
- <xref:System.Windows.Controls.Grid>
- <xref:System.Windows.Controls.StackPanel>
- <xref:System.Windows.Controls.VirtualizingStackPanel>
- <xref:System.Windows.Controls.WrapPanel>

Cada um desses controles de layout dá suporte a um tipo especial de layout para seus elementos filhos. `ExpenseIt` as páginas podem ser redimensionadas e cada página tem elementos que são organizados horizontalmente e verticalmente juntamente com outros elementos. Consequentemente, o <xref:System.Windows.Controls.Grid> é o elemento de layout ideal para o aplicativo.

> [!TIP]
> Para obter mais informações sobre <xref:System.Windows.Controls.Panel> elementos, consulte [visão geral de painéis](../../../../docs/framework/wpf/controls/panels-overview.md). Para obter mais informações sobre layout, consulte [Layout](../../../../docs/framework/wpf/advanced/layout.md).

Na seção, você criar uma tabela de coluna única com três linhas e uma margem de 10 pixels adicionando definições de linha e coluna para o <xref:System.Windows.Controls.Grid> na *`ExpenseItHome.xaml`*.

1. Abra *`ExpenseItHome.xaml`*.

2. Defina a <xref:System.Windows.FrameworkElement.Margin%2A> propriedade no <xref:System.Windows.Controls.Grid> elemento a ser "10,0,10,10", que corresponde às margens esquerda, superior, direita e inferior:

   ```xaml
   <Grid Margin="10,0,10,10">
   ```

   > [!TIP]
   > Você também pode definir a **margem** os valores na **propriedades** janela, na **Layout** categoria:
   >
   > ![Valores de margem na janela Propriedades](media/properties-margin.png)

3. Adicione o seguinte XAML entre o <xref:System.Windows.Controls.Grid> marcas para criar as definições de linha e coluna:

    [!code-xaml[ExpenseIt#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#8)]

    O <xref:System.Windows.Controls.RowDefinition.Height%2A> de duas linhas é definido como <xref:System.Windows.GridLength.Auto%2A>, o que significa que as linhas são dimensionadas com base no conteúdo de linhas. O padrão <xref:System.Windows.Controls.RowDefinition.Height%2A> é <xref:System.Windows.GridUnitType.Star> dimensionamento, o que significa que a altura da linha é uma proporção ponderada do espaço disponível. Por exemplo, se duas linhas tiverem uma <xref:System.Windows.Controls.RowDefinition.Height%2A> de "*", cada um deles tem uma altura que será a metade do espaço disponível.

    Seu <xref:System.Windows.Controls.Grid> deve agora parecer como o XAML a seguir:

    [!code-xaml[ExpenseIt#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#9)]

## <a name="add-controls"></a>Adicionar controles

Nesta seção, você atualizará a página inicial da interface do usuário para mostrar uma lista das pessoas que um usuário pode selecionar para mostrar o relatório de despesas. Os controles são objetos da interface do usuário que permitem aos usuários interagir com seu aplicativo. Para obter mais informações, consulte [Controles](../../../../docs/framework/wpf/controls/index.md).

Para criar essa interface do usuário, você adicionará os seguintes elementos para *`ExpenseItHome.xaml`*:

- <xref:System.Windows.Controls.ListBox> (para a lista de pessoas).
- <xref:System.Windows.Controls.Label> (para o cabeçalho da lista).
- <xref:System.Windows.Controls.Button> (para clicar para exibir o relatório de despesas para a pessoa que está selecionada na lista).

Cada controle é colocado em uma linha do <xref:System.Windows.Controls.Grid> definindo o <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> propriedade anexada. Para obter mais informações sobre propriedades anexadas, consulte [visão geral das propriedades anexadas](../../../../docs/framework/wpf/advanced/attached-properties-overview.md).

1. Abra *`ExpenseItHome.xaml`*.

2. Adicione o seguinte XAML em algum lugar entre o <xref:System.Windows.Controls.Grid> marcas:

   [!code-xaml[ExpenseIt#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt4/ExpenseItHome.xaml#10)]

   > [!TIP]
   > Você também pode criar os controles arrastando-os do **caixa de ferramentas** janela para a janela de design e, em seguida, definir suas propriedades na **propriedades** janela.

3. Crie e execute o aplicativo.

A ilustração a seguir mostra os controles que você acabou de criar:

![Captura de tela de exemplo de ExpenseIt](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure2.png)

## <a name="add-an-image-and-a-title"></a>Adicionar uma imagem e um título

Nesta seção, você vai atualizar a home page da interface do usuário com uma imagem e um título de página.

1. Abra *`ExpenseItHome.xaml`*.

2. Adicione outra coluna para o <xref:System.Windows.Controls.Grid.ColumnDefinitions%2A> fixa <xref:System.Windows.Controls.ColumnDefinition.Width%2A> de 230 pixels:

    [!code-xaml[ExpenseIt#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#11)]

3. Adicionar outra linha para o <xref:System.Windows.Controls.Grid.RowDefinitions%2A>, para um total de quatro linhas:

    [!code-xaml[ExpenseIt#11b](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#11b)]

4. Mova os controles para a segunda coluna, definindo o <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> propriedade como 1 em cada um dos três controles (da borda, ListBox e botão).

5. Mova cada controle para baixo uma linha, aumentando seu <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> valor por 1.

   O XAML para os três controles agora aparece desta forma:

    [!code-xaml[ExpenseIt#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#12)]

6. Definir a <xref:System.Windows.Controls.Panel.Background%2A> do <xref:System.Windows.Controls.Grid> seja a *watermark* arquivo de imagem, adicionando o seguinte XAML em algum lugar entre o `<Grid>` e `</Grid>` marcas:

    [!code-xaml[ExpenseIt#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#14)]

7. Antes do <xref:System.Windows.Controls.Border> elemento, adicionar um <xref:System.Windows.Controls.Label> com o conteúdo "Exibir relatório de despesas". Este é o título da página.

    [!code-xaml[ExpenseIt#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#13)]

8. Crie e execute o aplicativo.

A ilustração a seguir mostra os resultados de que você acabou de adicionar:

![Captura de tela de exemplo de ExpenseIt](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure3.png)

## <a name="add-code-to-handle-events"></a>Adicionar código para manipular eventos

1. Abra *`ExpenseItHome.xaml`*.

2. Adicionar um <xref:System.Windows.Controls.Primitives.ButtonBase.Click> manipulador de eventos para o <xref:System.Windows.Controls.Button> elemento. Para obter mais informações, consulte [como: Crie um manipulador de eventos simples](https://msdn.microsoft.com/library/b1456e07-9dec-4354-99cf-18666b64f480).

    [!code-xaml[ExpenseIt#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml#15)]

3. Abra *`ExpenseItHome.xaml.vb`* ou *`ExpenseItHome.xaml.cs`*.

4. Adicione o seguinte código para o `ExpenseItHome` classe para adicionar um botão de manipulador de eventos de clique. O manipulador de eventos abre o **ExpenseReportPage** página.

    [!code-csharp[ExpenseIt#16](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml.cs#16)]
    [!code-vb[ExpenseIt#16](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt6/ExpenseItHome.xaml.vb#16)]

## <a name="create-the-ui-for-expensereportpage"></a>Criar a interface do usuário para ExpenseReportPage

*ExpenseReportPage. XAML* exibe o relatório de despesas para a pessoa que está selecionada na **`ExpenseItHome`** página. Nesta seção, você criará a interface do usuário para **ExpenseReportPage**. Você também adicionará o plano de fundo e cores de preenchimento para os vários elementos de interface do usuário.

1. Abra *ExpenseReportPage.xaml*.

2. Adicione o seguinte XAML entre o <xref:System.Windows.Controls.Grid> marcas:

    [!code-xaml[ExpenseIt#17](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseReportPage.xaml#17)]

    Essa interface do usuário é semelhante à *`ExpenseItHome.xaml`*, exceto os dados do relatório são exibidos em um <xref:System.Windows.Controls.DataGrid>.

3. Crie e execute o aplicativo.

    > [!NOTE]
    > Se você receber um erro que o <xref:System.Windows.Controls.DataGrid> não foi encontrado ou não existir, certifique-se de que seu projeto direcionado ao .NET Framework 4 ou posterior. Para obter mais informações, consulte [como: Uma versão do .NET Framework de destino](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework).

4. Selecione o **exibição** botão.

    A página de relatório de despesas é exibida. Além disso, observe que o botão de navegação regressiva está habilitado.

A ilustração a seguir mostra os elementos de interface do usuário adicionados ao *ExpenseReportPage. XAML*.

![Captura de tela de exemplo de ExpenseIt](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure4.png)

## <a name="style-controls"></a>Controles de estilo

A aparência de vários elementos geralmente é o mesmo para todos os elementos do mesmo tipo em uma interface do usuário. Interface do usuário usa [estilos](../../../../docs/framework/wpf/controls/styling-and-templating.md) para fazer com que as aparências reutilizáveis entre vários elementos. A capacidade de reutilização dos estilos ajuda a simplificar o gerenciamento e a criação de XAML. Esta seção substitui os atributos por elemento que foram definidos nas etapas anteriores com estilos.

1. Abra *Application. XAML* ou *App. XAML*.

2. Adicione o seguinte XAML entre o <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> marcas:

    [!code-xaml[ExpenseIt#18](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/App.xaml#18)]

    Esse XAML adiciona os seguintes estilos:

    - `headerTextStyle`: Para formatar o título da página <xref:System.Windows.Controls.Label>.

    - `labelStyle`: Para formatar o <xref:System.Windows.Controls.Label> controles.

    - `columnHeaderStyle`: Para formatar o <xref:System.Windows.Controls.Primitives.DataGridColumnHeader>.

    - `listHeaderStyle`: Para formatar o cabeçalho da lista <xref:System.Windows.Controls.Border> controles.

    - `listHeaderTextStyle`: Para formatar o cabeçalho da lista <xref:System.Windows.Controls.Label>.

    - `buttonStyle`: Para formatar a <xref:System.Windows.Controls.Button> em `ExpenseItHome.xaml`.

    Observe que os estilos são recursos e seus filhos a <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> elemento de propriedade. Nesse local, os estilos são aplicados a todos os elementos em um aplicativo. Para obter um exemplo do uso de recursos em um aplicativo .NET Framework, consulte [usar recursos do aplicativo](../../../../docs/framework/wpf/advanced/how-to-use-application-resources.md).

3. Abra *`ExpenseItHome.xaml`*.

4. Substitua tudo entre os <xref:System.Windows.Controls.Grid> elementos com o XAML a seguir:

    [!code-xaml[ExpenseIt#19](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseItHome.xaml#19)]

    As propriedades como <xref:System.Windows.VerticalAlignment> e <xref:System.Windows.Media.FontFamily> que definem a aparência de cada controle são removidas e substituídas ao aplicar os estilos. Por exemplo, o `headerTextStyle` é aplicado a "Exibir relatório de despesas" <xref:System.Windows.Controls.Label>.

5. Abra *ExpenseReportPage.xaml*.

6. Substitua tudo entre os <xref:System.Windows.Controls.Grid> elementos com o XAML a seguir:

    [!code-xaml[ExpenseIt#20](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseReportPage.xaml#20)]

    Isso adiciona estilos aos elementos <xref:System.Windows.Controls.Label> e <xref:System.Windows.Controls.Border>.

## <a name="bind-data-to-a-control"></a>Associar dados a um controle

Nesta seção, você criará os dados XML que estão associados a vários controles.

1. Abra *`ExpenseItHome.xaml`*.

2. Após a abertura <xref:System.Windows.Controls.Grid> elemento, adicione o XAML a seguir para criar um <xref:System.Windows.Data.XmlDataProvider> que contém os dados para cada pessoa:

    [!code-xaml[ExpenseIt#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#21)]
    [!code-xaml[ExpenseIt#23](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#23)]
    [!code-xaml[ExpenseIt#22](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#22)]

    Os dados são criados como um <xref:System.Windows.Controls.Grid> recursos. Normalmente, isso seria carregado como um arquivo, mas para simplificar, os dados são adicionados embutidos.

3. Dentro de `<Grid.Resources>` elemento, adicione o seguinte <xref:System.Windows.DataTemplate>, que define como exibir os dados no <xref:System.Windows.Controls.ListBox>:

    [!code-xaml[ExpenseIt#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#21)]
    [!code-xaml[ExpenseIt#24](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#24)]
    [!code-xaml[ExpenseIt#22](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#22)]

    Para obter mais informações sobre modelos de dados, consulte [visão geral de modelagem de dados](../../../../docs/framework/wpf/data/data-templating-overview.md).

4. Substitua a <xref:System.Windows.Controls.ListBox> com o XAML a seguir:

    [!code-xaml[ExpenseIt#25](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#25)]

    Esse XAML associa a <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> propriedade do <xref:System.Windows.Controls.ListBox> à fonte de dados e aplica o modelo de dados como o <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>.

## <a name="connect-data-to-controls"></a>Conectar dados aos controles

Em seguida, você adicionará código para recuperar o nome que está selecionado na **`ExpenseItHome`** da página e passá-lo para o construtor da **ExpenseReportPage**. **ExpenseReportPage** define seu contexto de dados com o item passado, que é o que os controles definidos no *ExpenseReportPage* associar a.

1. Abra *ExpenseReportPage.xaml.vb* ou *ExpenseReportPage.xaml.cs*.

2. Adicione um construtor que utiliza um objeto para passar os dados do relatório de despesas da pessoa selecionada.

    [!code-csharp[ExpenseIt#26](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseReportPage.xaml.cs#26)]
    [!code-vb[ExpenseIt#26](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseReportPage.xaml.vb#26)]

3. Abra *`ExpenseItHome.xaml.vb`* ou *`ExpenseItHome.xaml.cs`*.

4. Alterar o <xref:System.Windows.Controls.Primitives.ButtonBase.Click> manipulador de eventos para chamar o novo construtor passando os dados de relatório de despesas da pessoa selecionada.

    [!code-csharp[ExpenseIt#27](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml.cs#27)]
    [!code-vb[ExpenseIt#27](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseItHome.xaml.vb#27)]

## <a name="style-data-with-data-templates"></a>Dados de estilo com modelos de dados

Nesta seção, você atualizará a interface do usuário para cada item nas listas de associação de dados usando modelos de dados.

1. Abra *ExpenseReportPage.xaml*.

2. Associar o conteúdo do "Nome" e "Departamento" <xref:System.Windows.Controls.Label> propriedade da fonte de elementos para os dados apropriados. Para obter mais informações sobre associação de dados, consulte [visão geral da vinculação de dados](../../../../docs/framework/wpf/data/data-binding-overview.md).

    [!code-xaml[ExpenseIt#31](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#31)]

3. Após a abertura <xref:System.Windows.Controls.Grid> elemento, adicione os seguintes modelos de dados, que definem como exibir os dados de relatório de despesas:

    [!code-xaml[ExpenseIt#30](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#30)]

4. Substitua os <xref:System.Windows.Controls.DataGridTextColumn> elementos com <xref:System.Windows.Controls.DataGridTemplateColumn> sob o <xref:System.Windows.Controls.DataGrid> elemento e aplicar os modelos a eles.

    [!code-xaml[ExpenseIt#32](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#32)]

5. Crie e execute o aplicativo.

6. Selecione uma pessoa e, em seguida, selecione a **exibição** botão.

A ilustração a seguir mostra as duas páginas do `ExpenseIt` aplicativo com controles, layout, estilos, vinculação de dados e modelos de dados aplicados:

![Capturas de tela de exemplo de ExpenseIt](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure5.png)

> [!NOTE]
> Este exemplo demonstra um recurso específico do WPF e não segue todas as práticas recomendadas para coisas como segurança, localização e acessibilidade. Para obter uma cobertura abrangente do WPF e as práticas recomendadas de desenvolvimento de aplicativo do .NET Framework, consulte os tópicos a seguir:
>
> - [Acessibilidade](../../../../docs/framework/ui-automation/accessibility-best-practices.md)
>
> - [Segurança](../../../../docs/framework/wpf/security-wpf.md)
>
> - [Globalização e localização do WPF](../../../../docs/framework/wpf/advanced/wpf-globalization-and-localization-overview.md)
>
> - [Desempenho do WPF](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)

## <a name="next-steps"></a>Próximas etapas

Neste passo a passo, você aprendeu várias técnicas para a criação de uma interface do usuário usando o Windows Presentation Foundation (WPF). Agora você deve ter uma compreensão básica dos blocos de construção de um aplicativo do .NET Framework de associação de dados. Para obter mais informações sobre os modelos de arquitetura e programação do WPF, consulte os seguintes tópicos:

- [Arquitetura do WPF](../../../../docs/framework/wpf/advanced/wpf-architecture.md)
- [Visão geral do XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
- [Visão geral das propriedades de dependência](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)
- [Layout](../../../../docs/framework/wpf/advanced/layout.md)

Para obter mais informações sobre como criar aplicativos, consulte os seguintes tópicos:

- [Desenvolvimento de aplicativos](../../../../docs/framework/wpf/app-development/index.md)
- [Controles](../../../../docs/framework/wpf/controls/index.md)
- [Visão geral da associação de dados](../../../../docs/framework/wpf/data/data-binding-overview.md)
- [Elementos gráficos e multimídia](../../../../docs/framework/wpf/graphics-multimedia/index.md)
- [Documentos no WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)

## <a name="see-also"></a>Consulte também

- [Visão geral de painéis](../../../../docs/framework/wpf/controls/panels-overview.md)
- [Visão geral de modelagem de dados](../../../../docs/framework/wpf/data/data-templating-overview.md)
- [Compilar um aplicativo WPF](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md)
- [Estilos e modelos](../../../../docs/framework/wpf/controls/styles-and-templates.md)
