---
title: 'Instruções passo a passo: associando a dados em aplicativos híbridos'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hybrid applications [WPF interoperability]
- data binding [WPF interoperability]
ms.assetid: 18997e71-745a-4425-9c69-2cbce1d8669e
ms.openlocfilehash: 99f0e621c7dd56c0a26b51b4725f9fb96ab3cbf9
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73197908"
---
# <a name="walkthrough-binding-to-data-in-hybrid-applications"></a>Instruções passo a passo: associando a dados em aplicativos híbridos

A associação de uma fonte de dados a um controle é essencial para fornecer aos usuários acesso aos dados subjacentes, independentemente de você estar usando [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ou [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Este tutorial mostra como você pode usar a associação de dados em aplicativos híbridos que incluem controles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] e [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].

As tarefas ilustradas neste passo a passo incluem:

- Criar o projeto.

- Definir o modelo de dados.

- Especificar o layout do formulário.

- Especificar associações de dados.

- Exibir dados usando interoperação.

- Adicionar a fonte de dados ao projeto.

- Criar uma associação à fonte de dados.

Para obter uma listagem de código completa das tarefas ilustradas neste passo a passos, consulte [exemplo de vinculação de dados em aplicativos híbridos](https://go.microsoft.com/fwlink/?LinkID=159983).

Quando tiver terminado, você terá um entendimento dos recursos de associação de dados em aplicativos híbridos.

## <a name="prerequisites"></a>Prerequisites

Você precisa dos seguintes componentes para concluir esta instrução passo a passo:

- Visual Studio.

- Acesso ao banco de dados de exemplo Northwind em execução no Microsoft SQL Server.

## <a name="creating-the-project"></a>Criando o Projeto

### <a name="to-create-and-set-up-the-project"></a>Criar e configurar o projeto

1. Crie um projeto de aplicativo WPF chamado `WPFWithWFAndDatabinding`.

2. No Gerenciador de Soluções, adicione referências aos assemblies a seguir.

    - WindowsFormsIntegration

    - System.Windows.Forms

3. Abra MainWindow.xaml no [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].

4. No elemento <xref:System.Windows.Window>, adicione o seguinte mapeamento de namespaces [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].

    ```xaml
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"
    ```

5. Nomeie o elemento <xref:System.Windows.Controls.Grid> padrão `mainGrid` atribuindo a propriedade <xref:System.Windows.FrameworkElement.Name%2A>.

     [!code-xaml[WPFWithWFAndDatabinding#8](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#8)]

## <a name="defining-the-data-template"></a>Definindo o modelo de dados

A lista mestra de clientes é exibida em um controle de <xref:System.Windows.Controls.ListBox>. O exemplo de código a seguir define um objeto <xref:System.Windows.DataTemplate> chamado `ListItemsTemplate` que controla a árvore visual do controle de <xref:System.Windows.Controls.ListBox>. Essa <xref:System.Windows.DataTemplate> é atribuída à propriedade <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> do controle de <xref:System.Windows.Controls.ListBox>.

### <a name="to-define-the-data-template"></a>Para definir o modelo de dados

- Copie o XAML a seguir na declaração do elemento <xref:System.Windows.Controls.Grid>.

     [!code-xaml[WPFWithWFAndDatabinding#3](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#3)]

## <a name="specifying-the-form-layout"></a>Especificando o layout do formulário

O layout do formulário é definido por uma grade com três linhas e três colunas. <xref:System.Windows.Controls.Label> controles são fornecidos para identificar cada coluna na tabela Customers.

### <a name="to-set-up-the-grid-layout"></a>Para configurar o layout de grade

- Copie o XAML a seguir na declaração do elemento <xref:System.Windows.Controls.Grid>.

     [!code-xaml[WPFWithWFAndDatabinding#4](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#4)]

### <a name="to-set-up-the-label-controls"></a>Para configurar os controles de Rótulo

- Copie o XAML a seguir na declaração do elemento <xref:System.Windows.Controls.Grid>.

     [!code-xaml[WPFWithWFAndDatabinding#5](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#5)]

## <a name="specifying-data-bindings"></a>Especificando associações de dados

A lista mestra de clientes é exibida em um controle de <xref:System.Windows.Controls.ListBox>. O `ListItemsTemplate` anexado associa um controle de <xref:System.Windows.Controls.TextBlock> ao campo `ContactName` do banco de dados.

Os detalhes de cada registro de cliente são exibidos em vários controles de <xref:System.Windows.Controls.TextBox>.

### <a name="to-specify-data-bindings"></a>Para especificar associações de dados

- Copie o XAML a seguir na declaração do elemento <xref:System.Windows.Controls.Grid>.

     A classe <xref:System.Windows.Data.Binding> associa os controles de <xref:System.Windows.Controls.TextBox> aos campos apropriados no banco de dados.

     [!code-xaml[WPFWithWFAndDatabinding#6](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#6)]

## <a name="displaying-data-by-using-interoperation"></a>Exibindo dados usando interoperação

Os pedidos correspondentes ao cliente selecionado são exibidos em um controle de <xref:System.Windows.Forms.DataGridView?displayProperty=nameWithType> chamado `dataGridView1`. O controle de `dataGridView1` está associado à fonte de dados no arquivo code-behind. Um controle de <xref:System.Windows.Forms.Integration.WindowsFormsHost> é o pai deste controle de [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].

### <a name="to-display-data-in-the-datagridview-control"></a>Para exibir dados no controle DataGridView

- Copie o XAML a seguir na declaração do elemento <xref:System.Windows.Controls.Grid>.

     [!code-xaml[WPFWithWFAndDatabinding#7](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#7)]

## <a name="adding-the-data-source-to-the-project"></a>Adicionando a fonte de dados ao projeto

Com o Visual Studio, você pode adicionar facilmente uma fonte de dados ao seu projeto. Este procedimento adiciona um conjunto de dados fortemente tipado ao seu projeto. Várias outras classes de suporte, como adaptadores de tabela para cada uma das tabelas escolhidas, também são adicionadas.

### <a name="to-add-the-data-source"></a>Para adicionar a fonte de dados

1. No menu **dados** , selecione **Adicionar nova fonte de dados**.

2. No **Assistente de configuração da fonte de dados**, crie uma conexão com o banco de dados Northwind usando um conjunto de dados. Para obter mais informações, consulte [How to: Connect to data in a Database](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/fxk9yw1t(v=vs.120)).

3. Quando solicitado pelo assistente de configuração da **fonte de dados**, salve a cadeia de conexão como `NorthwindConnectionString`.

4. Quando for solicitado que você escolha seus objetos de banco de dados, selecione as tabelas `Customers` e `Orders` e nomeie o conjunto de dados gerado `NorthwindDataSet`.

## <a name="binding-to-the-data-source"></a>Criando uma associação à fonte de dados

O componente <xref:System.Windows.Forms.BindingSource?displayProperty=nameWithType> fornece uma interface uniforme para a fonte de dados do aplicativo. Associação à fonte de dados é implementada no arquivo code-behind.

### <a name="to-bind-to-the-data-source"></a>Para associar à fonte de dados

1. Abra o arquivo code-behind, que se chama MainWindow.xaml.vb ou MainWindow.xaml.cs.

2. Copie o código a seguir para a definição de classe `MainWindow`.

     Esse código declara o componente <xref:System.Windows.Forms.BindingSource> e as classes auxiliares associadas que se conectam ao banco de dados.

     [!code-csharp[WPFWithWFAndDatabinding#11](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#11)]
     [!code-vb[WPFWithWFAndDatabinding#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#11)]

3. Copie o seguinte código para o construtor.

     Esse código cria e inicializa o componente <xref:System.Windows.Forms.BindingSource>.

     [!code-csharp[WPFWithWFAndDatabinding#12](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#12)]
     [!code-vb[WPFWithWFAndDatabinding#12](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#12)]

4. Abra MainWindow.xaml.

5. No modo de exibição modo de exibição de Design ou XAML, selecione o elemento <xref:System.Windows.Window>.

6. Na janela Propriedades, clique na guia **Eventos**.

7. Clique duas vezes no evento <xref:System.Windows.FrameworkElement.Loaded>.

8. Copie o código a seguir para o manipulador de eventos <xref:System.Windows.FrameworkElement.Loaded>.

     Esse código atribui o componente <xref:System.Windows.Forms.BindingSource> como o contexto de dados e popula os objetos `Customers` e `Orders` adaptador.

     [!code-csharp[WPFWithWFAndDatabinding#13](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#13)]
     [!code-vb[WPFWithWFAndDatabinding#13](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#13)]

9. Copie o código a seguir para a definição de classe `MainWindow`.

     Esse método manipula o evento <xref:System.Windows.Data.CollectionView.CurrentChanged> e atualiza o item atual da Associação de dados.

     [!code-csharp[WPFWithWFAndDatabinding#14](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#14)]
     [!code-vb[WPFWithWFAndDatabinding#14](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#14)]

10. Pressione F5 para compilar e executar o aplicativo.

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Criar o XAML no Visual Studio](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [Exemplo de associação de dados em aplicativos híbridos](https://go.microsoft.com/fwlink/?LinkID=159983)
- [Passo a passo: hospedando um controle composto do Windows Forms no WPF](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [Passo a passo: hospedando um controle composto do WPF no Windows Forms](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
