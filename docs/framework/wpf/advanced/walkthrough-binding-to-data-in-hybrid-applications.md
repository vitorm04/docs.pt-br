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
ms.openlocfilehash: fe8826a390abd370361b84f99540b8dacbdedc5e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-binding-to-data-in-hybrid-applications"></a>Instruções passo a passo: associando a dados em aplicativos híbridos
Associando uma fonte de dados a um controle é essencial para fornecer aos usuários acesso aos dados subjacentes, se você estiver usando [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ou [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Este passo a passo mostra como você pode usar a associação de dados em aplicativos híbridos que incluem ambas [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] e [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] controles.  
  
 As tarefas ilustradas neste passo a passo incluem:  
  
-   Criar o projeto.  
  
-   Definir o modelo de dados.  
  
-   Especificar o layout do formulário.  
  
-   Especificar associações de dados.  
  
-   Exibir dados usando interoperação.  
  
-   Adicionar a fonte de dados ao projeto.  
  
-   Criar uma associação à fonte de dados.  
  
 Para uma listagem de código completa das tarefas ilustradas neste passo a passo, consulte [associação de dados no exemplo de aplicativos híbridos](http://go.microsoft.com/fwlink/?LinkID=159983).  
  
 Quando tiver terminado, você terá um entendimento dos recursos de associação de dados em aplicativos híbridos.  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Você precisa dos seguintes componentes para concluir esta instrução passo a passo:  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)].  
  
-   Acesso ao banco de dados de exemplo e em execução no Microsoft SQL Server.  
  
## <a name="creating-the-project"></a>Criando o Projeto  
  
#### <a name="to-create-and-set-up-the-project"></a>Criar e configurar o projeto  
  
1.  Crie um projeto de aplicativo WPF chamado `WPFWithWFAndDatabinding`.  
  
2.  No Gerenciador de Soluções, adicione referências aos assemblies a seguir.  
  
    -   WindowsFormsIntegration  
  
    -   System.Windows.Forms  
  
3.  Abra MainWindow.xaml no [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].  
  
4.  No <xref:System.Windows.Window> elemento, adicione o seguinte [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] mapeamento de namespaces.  
  
    ```xaml  
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"  
    ```  
  
5.  Nomeie o padrão <xref:System.Windows.Controls.Grid> elemento `mainGrid` atribuindo o <xref:System.Windows.FrameworkElement.Name%2A> propriedade.  
  
     [!code-xaml[WPFWithWFAndDatabinding#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#8)]  
  
## <a name="defining-the-data-template"></a>Definindo o modelo de dados  
 A lista mestra de clientes é exibida em um <xref:System.Windows.Controls.ListBox> controle. O exemplo de código a seguir define uma <xref:System.Windows.DataTemplate> objeto chamado `ListItemsTemplate` que controla a árvore visual do <xref:System.Windows.Controls.ListBox> controle. Isso <xref:System.Windows.DataTemplate> é atribuído para o <xref:System.Windows.Controls.ListBox> do controle <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> propriedade.  
  
#### <a name="to-define-the-data-template"></a>Para definir o modelo de dados  
  
-   Copie o XAML a seguir para o <xref:System.Windows.Controls.Grid> declaração do elemento.  
  
     [!code-xaml[WPFWithWFAndDatabinding#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#3)]  
  
## <a name="specifying-the-form-layout"></a>Especificando o layout do formulário  
 O layout do formulário é definido por uma grade com três linhas e três colunas. <xref:System.Windows.Controls.Label> controles são fornecidos para identificar cada coluna na tabela Customers.  
  
#### <a name="to-set-up-the-grid-layout"></a>Para configurar o layout de grade  
  
-   Copie o XAML a seguir para o <xref:System.Windows.Controls.Grid> declaração do elemento.  
  
     [!code-xaml[WPFWithWFAndDatabinding#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#4)]  
  
#### <a name="to-set-up-the-label-controls"></a>Para configurar os controles de Rótulo  
  
-   Copie o XAML a seguir para o <xref:System.Windows.Controls.Grid> declaração do elemento.  
  
     [!code-xaml[WPFWithWFAndDatabinding#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#5)]  
  
## <a name="specifying-data-bindings"></a>Especificando associações de dados  
 A lista mestra de clientes é exibida em um <xref:System.Windows.Controls.ListBox> controle. O anexo `ListItemsTemplate` associa um <xref:System.Windows.Controls.TextBlock> o controle para o `ContactName` campo do banco de dados.  
  
 Os detalhes de cada registro de cliente são exibidos em vários <xref:System.Windows.Controls.TextBox> controles.  
  
#### <a name="to-specify-data-bindings"></a>Para especificar associações de dados  
  
-   Copie o XAML a seguir para o <xref:System.Windows.Controls.Grid> declaração do elemento.  
  
     O <xref:System.Windows.Data.Binding> classe associa o <xref:System.Windows.Controls.TextBox> controles para os campos apropriados no banco de dados.  
  
     [!code-xaml[WPFWithWFAndDatabinding#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#6)]  
  
## <a name="displaying-data-by-using-interoperation"></a>Exibindo dados usando interoperação  
 Os pedidos correspondentes ao cliente selecionado são exibidos em uma <xref:System.Windows.Forms.DataGridView?displayProperty=nameWithType> controle chamado `dataGridView1`. O `dataGridView1` controle está associado à fonte de dados no arquivo code-behind. Um <xref:System.Windows.Forms.Integration.WindowsFormsHost> controle é o pai desta [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controle.  
  
#### <a name="to-display-data-in-the-datagridview-control"></a>Para exibir dados no controle DataGridView  
  
-   Copie o XAML a seguir para o <xref:System.Windows.Controls.Grid> declaração do elemento.  
  
     [!code-xaml[WPFWithWFAndDatabinding#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#7)]  
  
## <a name="adding-the-data-source-to-the-project"></a>Adicionando a fonte de dados ao projeto  
 Com o Visual Studio, você pode facilmente adicionar uma fonte de dados ao seu projeto. Este procedimento adiciona um conjunto de dados fortemente tipado ao seu projeto. Várias outras classes de suporte, como adaptadores de tabela para cada uma das tabelas escolhidas, também são adicionadas.  
  
#### <a name="to-add-the-data-source"></a>Para adicionar a fonte de dados  
  
1.  Do **dados** menu, selecione **adicionar nova fonte de dados**.  
  
2.  No **Assistente de configuração de fonte de dados**, crie uma conexão ao banco de dados Northwind usando um conjunto de dados. Para obter mais informações, consulte [como: conectar a dados em um banco de dados](http://msdn.microsoft.com/library/6c56e54e-8834-4297-85aa-cc1a443ba556).  
  
3.  Quando for solicitado pelo **Assistente de configuração de fonte de dados**, salvar a cadeia de conexão como `NorthwindConnectionString`.  
  
4.  Quando você for solicitado a escolher seus objetos de banco de dados, selecione o `Customers` e `Orders` tabelas e o nome do conjunto de dados gerado `NorthwindDataSet`.  
  
## <a name="binding-to-the-data-source"></a>Criando uma associação à fonte de dados  
 O <xref:System.Windows.Forms.BindingSource?displayProperty=nameWithType> componente fornece uma interface uniforme para a fonte de dados do aplicativo. Associação à fonte de dados é implementada no arquivo code-behind.  
  
#### <a name="to-bind-to-the-data-source"></a>Para associar à fonte de dados  
  
1.  Abra o arquivo code-behind, que se chama MainWindow.xaml.vb ou MainWindow.xaml.cs.  
  
2.  Copie o seguinte código para o `MainWindow` definição da classe.  
  
     Esse código declara o <xref:System.Windows.Forms.BindingSource> componente e classes auxiliares associadas que se conectam ao banco de dados.  
  
     [!code-csharp[WPFWithWFAndDatabinding#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#11)]
     [!code-vb[WPFWithWFAndDatabinding#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#11)]  
  
3.  Copie o seguinte código para o construtor.  
  
     Esse código cria e inicializa o <xref:System.Windows.Forms.BindingSource> componente.  
  
     [!code-csharp[WPFWithWFAndDatabinding#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#12)]
     [!code-vb[WPFWithWFAndDatabinding#12](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#12)]  
  
4.  Abra MainWindow.xaml.  
  
5.  No modo de Design ou modo de exibição XAML, selecione o <xref:System.Windows.Window> elemento.  
  
6.  Na janela Propriedades, clique na guia **Eventos**.  
  
7.  Clique duas vezes o <xref:System.Windows.FrameworkElement.Loaded> evento.  
  
8.  Copie o seguinte código para o <xref:System.Windows.FrameworkElement.Loaded> manipulador de eventos.  
  
     Esse código atribui o <xref:System.Windows.Forms.BindingSource> componente como o contexto de dados e preenche o `Customers` e `Orders` objetos de adaptador.  
  
     [!code-csharp[WPFWithWFAndDatabinding#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#13)]
     [!code-vb[WPFWithWFAndDatabinding#13](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#13)]  
  
9. Copie o seguinte código para o `MainWindow` definição da classe.  
  
     Este método trata o <xref:System.Windows.Data.CollectionView.CurrentChanged> eventos e atualiza o item atual da associação de dados.  
  
     [!code-csharp[WPFWithWFAndDatabinding#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#14)]
     [!code-vb[WPFWithWFAndDatabinding#14](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#14)]  
  
10. Pressione F5 para compilar e executar o aplicativo.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [Designer do WPF](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26)  
 [Associação de dados em um exemplo de aplicativos híbridos](http://go.microsoft.com/fwlink/?LinkID=159983)  
 [Passo a passo: hospedando um controle composto do Windows Forms no WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)  
 [Instruções passo a passo: hospedando um controle de composição do WPF nos Windows Forms](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
