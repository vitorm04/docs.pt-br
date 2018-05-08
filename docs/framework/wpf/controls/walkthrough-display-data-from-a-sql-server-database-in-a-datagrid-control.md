---
title: 'Instruções passo a passo: exibir dados a partir de um banco de dados do SQL Server em um controle DataGrid'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGrid [WPF], displaying data from SQL Server
- controls [WPF], DataGrid
ms.assetid: 6810b048-0a23-4f86-bfa5-97f92b3cfab4
ms.openlocfilehash: 230d2c6843f9ae80126d9d0a2c949982aae24c76
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-display-data-from-a-sql-server-database-in-a-datagrid-control"></a>Instruções passo a passo: exibir dados a partir de um banco de dados do SQL Server em um controle DataGrid
Neste passo a passo, você pode recuperar dados de um banco de dados do SQL Server e exibir os dados em um <xref:System.Windows.Controls.DataGrid> controle. O ADO.NET Entity Framework é usado para criar as classes de entidade que representam os dados e o LINQ é usado para gravar uma consulta que recupera os dados especificados de uma classe de entidade.  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Você precisa dos seguintes componentes para concluir esta instrução passo a passo:  
  
-   [!INCLUDE[vs_dev11_long](../../../../includes/vs-dev11-long-md.md)].  
  
-   Acesso a uma instância em execução do SQL Server ou SQL Server Express que tem o banco de dados de exemplo AdventureWorks anexado a ele. Você pode baixar o banco de dados AdventureWorks de [GitHub](https://github.com/Microsoft/sql-server-samples/releases).  
  
### <a name="to-create-entity-classes"></a>Criar classes de entidade  
  
1.  Crie um novo projeto de Aplicativo do WPF no Visual Basic ou no C#, chamado `DataGridSQLExample`.  
  
2.  No Gerenciador de Soluções, clique com o botão direito do mouse no projeto, aponte para **Adicionar** e selecione **Novo Item**.  
  
     A caixa de diálogo Adicionar Novo Item é exibida.  
  
3.  No painel Modelos Instalados, selecione **Dados** e na lista de modelos, selecione **Modelo de Dados de Entidade ADO.NET**.  
  
     ![Selecione o Modelo de Dados de Entidade ADO.NET](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step1.png "DataGrid_SQL_EF_Step1")  
  
4.  Nomeie o arquivo `AdventureWorksModel.edmx` e, em seguida, clique em **Adicionar**.  
  
     O Assistente do Modelo de Dados de Entidade é aberto.  
  
5.  Na tela Escolher Conteúdos Modelo, selecione **Gerar do banco de dados** e, em seguida, clique em **Próximo**.  
  
     ![Selecione a opção Gerar do banco de dados](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step2.png "DataGrid_SQL_EF_Step2")  
  
6.  Na tela Escolher a Conexão de Dados, forneça a conexão ao banco de dados AdventureWorksLT2008. Para obter mais informações, consulte [Escolher uma Caixa de Diálogo de Conexão de Dados](http://go.microsoft.com/fwlink/?LinkId=160190).  
  
     ![Fornecer a conexão ao banco de dados](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step3.png "DataGrid_SQL_EF_Step3")  
  
7.  Certifique-se de que o nome é `AdventureWorksLT2008Entities` e que o **salvar configurações de conexão de entidade no App. config como** caixa de seleção está selecionada e, em seguida, clique em **próximo**.  
  
8.  Na tela Escolher Objetos de Banco de Dados, expanda o nó Tabelas e selecione as tabelas **Product** e **ProductCategory**.  
  
     É possível gerar classes de entidade para todas as tabelas; no entanto, neste exemplo, somente os dados dessas duas tabelas serão recuperados.  
  
     ![Selecione Product e ProductCategory nas tabelas](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step4.png "DataGrid_SQL_EF_Step4")  
  
9. Clique em **Finalizar**.  
  
     As entidades Product e ProductCategory serão exibidas no Entity Designer.  
  
     ![Modelos de entidade Product e ProductCategory](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step5.png "DataGrid_SQL_EF_Step5")  
  
### <a name="to-retrieve-and-present-the-data"></a>Recuperar e apresentar os dados  
  
1.  Abra o arquivo MainWindow.xaml.  
  
2.  Definir o <xref:System.Windows.FrameworkElement.Width%2A> propriedade o <xref:System.Windows.Window> para 450.  
  
3.  No editor XAML, adicione o seguinte <xref:System.Windows.Controls.DataGrid> marca entre o `<Grid>` e `</Grid>` marcas para adicionar um <xref:System.Windows.Controls.DataGrid> chamado `dataGrid1`.  
  
     [!code-xaml[DataGrid_SQL_EF_Walkthrough#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/CS/MainWindow.xaml#3)]  
  
     ![Janela com DataGrid](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step6.png "DataGrid_SQL_EF_Step6")  
  
4.  Selecione o <xref:System.Windows.Window>.  
  
5.  Usando a janela Propriedades ou o editor XAML, crie um manipulador de eventos para o <xref:System.Windows.Window> chamado `Window_Loaded` para o <xref:System.Windows.FrameworkElement.Loaded> evento. Para obter mais informações, consulte [Como Criar um Manipulador de Eventos Simples](http://msdn.microsoft.com/library/b1456e07-9dec-4354-99cf-18666b64f480).  
  
     O exemplo a seguir mostra o XAML de MainWindow.xaml.  
  
    > [!NOTE]
    >  Se você estiver usando o Visual Basic, na primeira linha de MainWindow.xaml, substitua `x:Class="DataGridSQLExample.MainWindow"` por `x:Class="MainWindow"`.  
  
     [!code-xaml[DataGrid_SQL_EF_Walkthrough#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/CS/MainWindow.xaml#1)]  
  
6.  Abra o arquivo code-behind (MainWindow.xaml.vb ou MainWindow.xaml.cs) para o <xref:System.Windows.Window>.  
  
7.  Adicione o seguinte código para recuperar apenas os valores específicos de tabelas unidas e definir o <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> propriedade o <xref:System.Windows.Controls.DataGrid> para os resultados da consulta.  
  
     [!code-csharp[DataGrid_SQL_EF_Walkthrough#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/CS/MainWindow.xaml.cs#2)]
     [!code-vb[DataGrid_SQL_EF_Walkthrough#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/VB/MainWindow.xaml.vb#2)]  
  
8.  Execute o exemplo.  
  
     Você deve ver uma <xref:System.Windows.Controls.DataGrid> que exibe os dados.  
  
     ![DataGrid com os dados de banco de dados SQL](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step7.png "DataGrid_SQL_EF_Step7")  
  
## <a name="next-steps"></a>Próximas etapas  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Controls.DataGrid>  
 [Como se Familiarizar com o Entity Framework em Aplicativos WPF?](http://go.microsoft.com/fwlink/?LinkId=159868)
