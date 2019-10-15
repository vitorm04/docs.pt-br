---
title: 'Passo a passo: organizar controles do Windows Forms no WPF'
ms.date: 04/03/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hybrid applications [WPF interoperability]
- arranging controls [WPF]
ms.assetid: a1db8049-15c7-45d6-ae3d-36a6735cb848
ms.openlocfilehash: 3a94ef65be99b01a9511f37872cbcacd6ec12264
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/09/2019
ms.locfileid: "72179429"
---
# <a name="walkthrough-arranging-windows-forms-controls-in-wpf"></a>Passo a passo: organizar controles do Windows Forms no WPF

Este tutorial mostra como usar os recursos de layout [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] para organizar os controles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] em um aplicativo híbrido.

As tarefas ilustradas neste passo a passo incluem:

- Criar o projeto.
- Usando as configurações padrão de layout.
- Dimensionando o conteúdo.
- Usando o posicionamento absoluto.
- Especificando o tamanho explicitamente.
- Definindo propriedades de layout.
- Noções básicas sobre limitações da ordem z.
- Encaixe.
- Definindo a visibilidade.
- Hospedando um controle que não se alonga.
- Dimensionamento.
- Girando.
- Margens e preenchimento de configuração.
- Usando contêineres de layout dinâmico.

Para obter uma listagem de código completa das tarefas ilustradas neste passo a passos, consulte [organizando Windows Forms controles no WPF Sample](https://go.microsoft.com/fwlink/?LinkID=159971).

Quando tiver terminado, você terá uma compreensão dos recursos de layout [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] em aplicativos baseados em-1 @no__t.

## <a name="prerequisites"></a>Pré-requisitos

É necessário o Visual Studio para concluir este passo a passo.

## <a name="creating-the-project"></a>Criando o Projeto

Para criar e configurar o projeto, siga estas etapas:

1. Crie um projeto de aplicativo WPF chamado `WpfLayoutHostingWf`.

2. Em Gerenciador de Soluções, adicione referências aos seguintes assemblies:

    - WindowsFormsIntegration
    - System.Windows.Forms
    - System.Drawing

3. Clique duas vezes em *MainWindow. XAML* para abri-lo no modo de exibição XAML.

4. No elemento <xref:System.Windows.Window>, adicione o seguinte mapeamento de namespace [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].

    ```xaml
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"
    ```

5. No elemento <xref:System.Windows.Controls.Grid>, defina a propriedade <xref:System.Windows.Controls.Grid.ShowGridLines%2A> como `true` e defina cinco linhas e três colunas.

     [!code-xaml[WpfLayoutHostingWfWithXaml#2](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#2)]

## <a name="using-default-layout-settings"></a>Usando as configurações padrão de layout

Por padrão, o elemento <xref:System.Windows.Forms.Integration.WindowsFormsHost> manipula o layout do controle [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] hospedado.

Para usar as configurações de layout padrão, siga estas etapas:

1. Copie o XAML a seguir no elemento <xref:System.Windows.Controls.Grid>:

     [!code-xaml[WpfLayoutHostingWfWithXaml#3](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#3)]

2. Pressione <kbd>F5</kbd> para compilar e executar o aplicativo. O controle [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.Button?displayProperty=nameWithType> aparece no <xref:System.Windows.Controls.Canvas>. O controle hospedado é dimensionado com base em seu conteúdo e o elemento <xref:System.Windows.Forms.Integration.WindowsFormsHost> é dimensionado para acomodar o controle hospedado.

## <a name="sizing-to-content"></a>Dimensionando para o conteúdo

O elemento <xref:System.Windows.Forms.Integration.WindowsFormsHost> garante que o controle hospedado seja dimensionado para exibir seu conteúdo corretamente.

Para dimensionar para o conteúdo, siga estas etapas:

1. Copie o XAML a seguir no elemento <xref:System.Windows.Controls.Grid>:

     [!code-xaml[WpfLayoutHostingWfWithXaml#4](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#4)]

2. Pressione <kbd>F5</kbd> para compilar e executar o aplicativo. Os dois novos controles de botão são dimensionados para exibir a cadeia de texto mais longa e o tamanho de fonte maior corretamente, e os elementos <xref:System.Windows.Forms.Integration.WindowsFormsHost> são redimensionados para acomodar os controles hospedados.

## <a name="using-absolute-positioning"></a>Usando o posicionamento absoluto

Você pode usar o posicionamento absoluto para posicionar o elemento <xref:System.Windows.Forms.Integration.WindowsFormsHost> em qualquer lugar na interface do usuário.

Para usar o posicionamento absoluto, siga estas etapas:

1. Copie o XAML a seguir no elemento <xref:System.Windows.Controls.Grid>:

     [!code-xaml[WpfLayoutHostingWfWithXaml#5](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#5)]

2. Pressione <kbd>F5</kbd> para compilar e executar o aplicativo. O elemento <xref:System.Windows.Forms.Integration.WindowsFormsHost> é colocado em 20 pixels do lado superior da célula da grade e 20 pixels à esquerda.

## <a name="specifying-size-explicitly"></a>Especificando o tamanho explicitamente

Você pode especificar o tamanho do elemento <xref:System.Windows.Forms.Integration.WindowsFormsHost> usando as propriedades <xref:System.Windows.FrameworkElement.Width%2A> e <xref:System.Windows.FrameworkElement.Height%2A>.

Para especificar o tamanho explicitamente, siga estas etapas:

1. Copie o XAML a seguir no elemento <xref:System.Windows.Controls.Grid>:

     [!code-xaml[WpfLayoutHostingWfWithXaml#6](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#6)]

2. Pressione <kbd>F5</kbd> para compilar e executar o aplicativo. O elemento <xref:System.Windows.Forms.Integration.WindowsFormsHost> é definido com um tamanho de 50 pixels de largura por 70 pixels de altura, o que é menor do que as configurações de layout padrão. O conteúdo do controle [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] é reorganizado de acordo.

## <a name="setting-layout-properties"></a>Definindo propriedades de layout

Sempre defina propriedades relacionadas ao layout no controle hospedado usando as propriedades do elemento <xref:System.Windows.Forms.Integration.WindowsFormsHost>. Definindo propriedades de layout diretamente no controle hospedado produzirá resultados indesejados.

 Definir propriedades relacionadas a layout no controle hospedado no [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] não tem efeito.

Para ver os efeitos das propriedades de configuração no controle hospedado, siga estas etapas:

1. Copie o XAML a seguir no elemento <xref:System.Windows.Controls.Grid>:

     [!code-xaml[WpfLayoutHostingWfWithXaml#7](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#7)]

2. Em **Gerenciador de soluções**, clique duas vezes em *MainWindow. XAML. vb* ou *MainWindow.XAML.cs* para abri-lo no editor de códigos.

3. Copie o código a seguir na definição de classe `MainWindow`:

     [!code-csharp[WpfLayoutHostingWfWithXaml#101](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#101)]
     [!code-vb[WpfLayoutHostingWfWithXaml#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#101)]

4. Pressione <kbd>F5</kbd> para compilar e executar o aplicativo.

5. Clique no botão **clicar em mim** . O manipulador de eventos `button1_Click` define as propriedades <xref:System.Windows.Forms.Control.Top%2A> e <xref:System.Windows.Forms.Control.Left%2A> no controle hospedado. Isso faz com que o controle hospedado seja reposicionado dentro do elemento <xref:System.Windows.Forms.Integration.WindowsFormsHost>. O host mantém a mesma área da tela, mas o controle hospedado é cortado. Em vez disso, o controle hospedado sempre deve preencher o elemento <xref:System.Windows.Forms.Integration.WindowsFormsHost>.

## <a name="understanding-z-order-limitations"></a>Noções básicas sobre limitações da ordem z

Os elementos <xref:System.Windows.Forms.Integration.WindowsFormsHost> visíveis sempre são desenhados sobre outros elementos do WPF e não são afetados pela ordem z. Para ver esse comportamento de ordem z, faça o seguinte:

1. Copie o XAML a seguir no elemento <xref:System.Windows.Controls.Grid>:

     [!code-xaml[WpfLayoutHostingWfWithXaml#8](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#8)]

2. Pressione <kbd>F5</kbd> para compilar e executar o aplicativo. O elemento <xref:System.Windows.Forms.Integration.WindowsFormsHost> é pintado sobre o elemento Label.

## <a name="docking"></a>Encaixe

o elemento <xref:System.Windows.Forms.Integration.WindowsFormsHost> dá suporte ao encaixe [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Defina a propriedade anexada <xref:System.Windows.Controls.DockPanel.Dock%2A> para encaixar o controle hospedado em um elemento <xref:System.Windows.Controls.DockPanel>.

Para encaixar um controle hospedado, siga estas etapas:

1. Copie o XAML a seguir no elemento <xref:System.Windows.Controls.Grid>:

     [!code-xaml[WpfLayoutHostingWfWithXaml#9](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#9)]

2. Pressione <kbd>F5</kbd> para compilar e executar o aplicativo. O elemento <xref:System.Windows.Forms.Integration.WindowsFormsHost> é encaixado no lado direito do elemento <xref:System.Windows.Controls.DockPanel>.

## <a name="setting-visibility"></a>Definindo a visibilidade

Você pode tornar o controle [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] invisível ou recolhê-lo definindo a propriedade <xref:System.Windows.UIElement.Visibility%2A> no elemento <xref:System.Windows.Forms.Integration.WindowsFormsHost>. Quando um controle estiver invisível, ele não será exibido, mas ocupa espaço de layout. Quando um controle estiver recolhido, ele não será exibido, mas também não ocupa espaço de layout.

Para definir a visibilidade de um controle hospedado, siga estas etapas:

1. Copie o XAML a seguir no elemento <xref:System.Windows.Controls.Grid>:

     [!code-xaml[WpfLayoutHostingWfWithXaml#10](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#10)]

2. Em *MainWindow. XAML. vb* ou *MainWindow.XAML.cs*, copie o seguinte código para a definição de classe:

     [!code-csharp[WpfLayoutHostingWfWithXaml#102](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#102)]
     [!code-vb[WpfLayoutHostingWfWithXaml#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#102)]

3. Pressione <kbd>F5</kbd> para compilar e executar o aplicativo.

4. Clique no botão **clique para tornar invisível** para tornar o elemento <xref:System.Windows.Forms.Integration.WindowsFormsHost> invisível.

5. Clique no botão **clique para recolher** para ocultar totalmente o elemento <xref:System.Windows.Forms.Integration.WindowsFormsHost> do layout. Quando o controle [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] é recolhido, os elementos circundantes são reorganizados para ocupar seu espaço.

## <a name="hosting-a-control-that-does-not-stretch"></a>Hospedando um controle que não se alonga

Alguns controles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] têm um tamanho fixo e não se alongam para preencher o espaço disponível no layout. Por exemplo, o controle <xref:System.Windows.Forms.MonthCalendar> exibe um mês em um espaço fixo.

Para hospedar um controle que não se estende, siga estas etapas:

1. Copie o XAML a seguir no elemento <xref:System.Windows.Controls.Grid>:

     [!code-xaml[WpfLayoutHostingWfWithXaml#11](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#11)]

2. Pressione <kbd>F5</kbd> para compilar e executar o aplicativo. O elemento <xref:System.Windows.Forms.Integration.WindowsFormsHost> é centralizado na linha de grade, mas não é ampliado para preencher o espaço disponível. Se a janela for grande o suficiente, você poderá ver dois ou mais meses exibidos pelo controle <xref:System.Windows.Forms.MonthCalendar> hospedado, mas eles são centralizados na linha. O mecanismo de layout [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] centraliza os elementos que não podem ser dimensionados para preencher o espaço disponível.

## <a name="scaling"></a>Dimensionamento

Ao contrário dos elementos do WPF, a maioria dos controles de Windows Forms não são continuamente escalonáveis. Para fornecer o dimensionamento personalizado, você substitui o método <xref:System.Windows.Forms.Integration.WindowsFormsHost.ScaleChild%2A?displayProperty=nameWithType>.

Para dimensionar um controle hospedado usando o comportamento padrão, siga estas etapas:

1. Copie o XAML a seguir no elemento <xref:System.Windows.Controls.Grid>:

     [!code-xaml[WpfLayoutHostingWfWithXaml#12](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#12)]

2. Pressione <kbd>F5</kbd> para compilar e executar o aplicativo. O controle hospedado e seus elementos adjacentes são dimensionados por um fator de 0,5. No entanto, a fonte do controle hospedada não é redimensionada.

<!-- This could use an example of custom scaling. -->

## <a name="rotating"></a>Girando

Ao contrário dos elementos do WPF, os controles de Windows Forms não dão suporte à rotação. O elemento <xref:System.Windows.Forms.Integration.WindowsFormsHost> não gira com outros elementos do WPF quando uma transformação de rotação é aplicada. Qualquer valor de rotação diferente de 180 graus gera o evento <xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError>.

Para ver o efeito de rotação em um aplicativo híbrido, siga estas etapas:

1. Copie o XAML a seguir no elemento <xref:System.Windows.Controls.Grid>:

     [!code-xaml[WpfLayoutHostingWfWithXaml#13](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#13)]

2. Pressione <kbd>F5</kbd> para compilar e executar o aplicativo. O controle hospedado não é girado, mas seus elementos adjacentes são girados por um ângulo de 180 graus. Você terá que redimensionar a janela para ver os elementos.

## <a name="setting-padding-and-margins"></a>Margens e preenchimento de configuração

O preenchimento e as margens no layout [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] são semelhantes ao preenchimento e às margens em [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]. Basta definir as propriedades <xref:System.Windows.Controls.Control.Padding%2A> e <xref:System.Windows.FrameworkElement.Margin%2A> no elemento <xref:System.Windows.Forms.Integration.WindowsFormsHost>.

Para definir o preenchimento e as margens de um controle hospedado, siga estas etapas:

1. Copie o XAML a seguir no elemento <xref:System.Windows.Controls.Grid>:

     [!code-xaml[WpfLayoutHostingWfWithXaml#14](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#14)]
    [!code-xaml[WpfLayoutHostingWfWithXaml#15](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#15)]

2. Pressione <kbd>F5</kbd> para compilar e executar o aplicativo. As configurações de preenchimento e margem são aplicadas aos controles hospedados [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] da mesma maneira que seriam aplicadas em [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].

## <a name="using-dynamic-layout-containers"></a>Usando contêineres de layout dinâmico

[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] fornece dois contêineres de layout dinâmico, <xref:System.Windows.Forms.FlowLayoutPanel> e <xref:System.Windows.Forms.TableLayoutPanel>. Você também pode usar esses contêineres em layouts [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].

Para usar um contêiner de layout dinâmico, siga estas etapas:

1. Copie o XAML a seguir no elemento <xref:System.Windows.Controls.Grid>:

     [!code-xaml[WpfLayoutHostingWfWithXaml#16](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#16)]

2. Em *MainWindow. XAML. vb* ou *MainWindow.XAML.cs*, copie o seguinte código para a definição de classe:

     [!code-csharp[WpfLayoutHostingWfWithXaml#103](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#103)]
     [!code-vb[WpfLayoutHostingWfWithXaml#103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#103)]

3. Adicione uma chamada para o método `InitializeFlowLayoutPanel` no construtor:

     [!code-csharp[WpfLayoutHostingWfWithXaml#104](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#104)]
     [!code-vb[WpfLayoutHostingWfWithXaml#104](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#104)]

4. Pressione <kbd>F5</kbd> para compilar e executar o aplicativo. O elemento <xref:System.Windows.Forms.Integration.WindowsFormsHost> preenche o <xref:System.Windows.Controls.DockPanel> e <xref:System.Windows.Forms.FlowLayoutPanel> organiza seus controles filho no padrão <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A>.

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Criar o XAML no Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio)
- [Considerações sobre o layout do elemento WindowsFormsHost](layout-considerations-for-the-windowsformshost-element.md)
- [Organizando Windows Forms controles no WPF de exemplo](https://go.microsoft.com/fwlink/?LinkID=159971)
- [Passo a passo: Hospedando um controle composto Windows Forms no WPF @ no__t-0
- [Passo a passo: Hospedando um controle composto do WPF em Windows Forms @ no__t-0
