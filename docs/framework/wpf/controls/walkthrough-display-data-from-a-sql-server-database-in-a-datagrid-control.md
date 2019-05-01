---
title: 'Passo a passo: exibir dados de um banco de dados do SQL Server em um controle DataGrid'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGrid [WPF], displaying data from SQL Server
- controls [WPF], DataGrid
ms.assetid: 6810b048-0a23-4f86-bfa5-97f92b3cfab4
ms.openlocfilehash: 274ec2e8ef16190da53061bb197bc3b1a1fadcf8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62024039"
---
# <a name="walkthrough-display-data-from-a-sql-server-database-in-a-datagrid-control"></a>Passo a passo: Exibir dados de um banco de dados do SQL Server em um controle DataGrid

Neste passo a passo, você pode recuperar dados de um banco de dados do SQL Server e exibi-los em um <xref:System.Windows.Controls.DataGrid> controle. O ADO.NET Entity Framework é usado para criar as classes de entidade que representam os dados e o LINQ é usado para gravar uma consulta que recupera os dados especificados de uma classe de entidade.

## <a name="prerequisites"></a>Pré-requisitos

Você precisa dos seguintes componentes para concluir esta instrução passo a passo:

- Visual Studio.

- Acesso a uma instância em execução do SQL Server ou SQL Server Express que tem o banco de dados de exemplo AdventureWorks anexado a ele. Você pode baixar o banco de dados AdventureWorks a [GitHub](https://github.com/Microsoft/sql-server-samples/releases).

## <a name="create-entity-classes"></a>Criar classes de entidade

1. Crie um novo projeto de Aplicativo do WPF no Visual Basic ou no C#, chamado `DataGridSQLExample`.

2. No Gerenciador de Soluções, clique com o botão direito do mouse no projeto, aponte para **Adicionar** e selecione **Novo Item**.

     A caixa de diálogo Adicionar Novo Item é exibida.

3. No painel modelos instalados, selecione **dados** e, na lista de modelos, selecione **modelo de dados de entidade ADO.NET**.

     ![Modelo de item de modelo de dados de entidade ADO.NET](../../wcf/feature-details/./media/ado-net-entity-data-model-item-template.png)

4. Nomeie o arquivo `AdventureWorksModel.edmx` e, em seguida, clique em **Adicionar**.

     O Assistente do Modelo de Dados de Entidade é aberto.

5. Na tela Escolher conteúdos modelo, selecione **EF Designer do banco de dados** e, em seguida, clique em **próxima**.

6. Na tela Escolher a Conexão de Dados, forneça a conexão ao banco de dados AdventureWorksLT2008. Para obter mais informações, consulte [Escolher uma Caixa de Diálogo de Conexão de Dados](https://go.microsoft.com/fwlink/?LinkId=160190).

    Certifique-se de que o nome é `AdventureWorksLT2008Entities` e que o **salvar configurações de conexão de entidade em App. config como** caixa de seleção está selecionada e, em seguida, clique em **próximo**.

7. Na tela Escolher Objetos de Banco de Dados, expanda o nó Tabelas e selecione as tabelas **Product** e **ProductCategory**.

     É possível gerar classes de entidade para todas as tabelas; no entanto, neste exemplo, somente os dados dessas duas tabelas serão recuperados.

     ![Selecione Product e ProductCategory nas tabelas](./media/datagrid-sql-ef-step4.png "DataGrid_SQL_EF_Step4")

8. Clique em **Finalizar**.

     As entidades Product e ProductCategory serão exibidas no Entity Designer.

     ![Modelos de entidade Product e ProductCategory](./media/datagrid-sql-ef-step5.png "DataGrid_SQL_EF_Step5")

## <a name="retrieve-and-present-the-data"></a>Recuperar e apresentar os dados

1. Abra o arquivo MainWindow.xaml.

2. Defina as <xref:System.Windows.FrameworkElement.Width%2A> propriedade no <xref:System.Windows.Window> para 450.

3. No editor de XAML, adicione o seguinte <xref:System.Windows.Controls.DataGrid> marcar entre o `<Grid>` e `</Grid>` marcas para adicionar um <xref:System.Windows.Controls.DataGrid> chamado `dataGrid1`.

     [!code-xaml[DataGrid_SQL_EF_Walkthrough#3](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/CS/MainWindow.xaml#3)]

     ![Janela com DataGrid](./media/datagrid-sql-ef-step6.png "DataGrid_SQL_EF_Step6")

4. Selecione o <xref:System.Windows.Window>.

5. Usando a janela Propriedades ou o editor XAML, crie um manipulador de eventos para o <xref:System.Windows.Window> nomeado `Window_Loaded` para o <xref:System.Windows.FrameworkElement.Loaded> eventos. Para obter mais informações, confira [Como: Crie um manipulador de eventos simples](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb675300(v=vs.100)).

     O exemplo a seguir mostra o XAML de MainWindow.xaml.

    > [!NOTE]
    > Se você estiver usando o Visual Basic, na primeira linha de MainWindow.xaml, substitua `x:Class="DataGridSQLExample.MainWindow"` por `x:Class="MainWindow"`.

     [!code-xaml[DataGrid_SQL_EF_Walkthrough#1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/CS/MainWindow.xaml#1)]

6. Abra o arquivo code-behind (. XAML. vb ou MainWindow.xaml.cs) para o <xref:System.Windows.Window>.

7. Adicione o seguinte código para recuperar valores específicos das tabelas unidas e defina as <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> propriedade do <xref:System.Windows.Controls.DataGrid> aos resultados da consulta.

     [!code-csharp[DataGrid_SQL_EF_Walkthrough#2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/CS/MainWindow.xaml.cs#2)]
     [!code-vb[DataGrid_SQL_EF_Walkthrough#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/VB/MainWindow.xaml.vb#2)]

8. Execute o exemplo.

     Você deve ver um <xref:System.Windows.Controls.DataGrid> que exibe dados.

     ![DataGrid com os dados de banco de dados SQL](./media/datagrid-sql-ef-step7.png "DataGrid_SQL_EF_Step7")

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Controls.DataGrid>
- [Como faço Introdução ao Entity Framework em aplicativos WPF?](https://go.microsoft.com/fwlink/?LinkId=159868)