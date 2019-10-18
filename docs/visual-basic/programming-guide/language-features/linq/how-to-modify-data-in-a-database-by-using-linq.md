---
title: Como modificar dados em um banco de dados usando LINQ (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- inserting rows [LINQ to SQL]
- deleting rows [LINQ to SQL]
- updating rows [LINQ to SQL]
- inserting data [Visual Basic]
- deleting data
- data [Visual Basic], updating
- updating data [LINQ]
- queries [LINQ in Visual Basic], data changes in database
- queries [LINQ in Visual Basic], how-to topics
ms.assetid: cf52635f-0c1b-46c3-aff1-bdf181cf19b1
ms.openlocfilehash: ebf0ed1be8d74b60b7e626db996e7cefb1c01131
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524518"
---
# <a name="how-to-modify-data-in-a-database-by-using-linq-visual-basic"></a>Como modificar dados em um banco de dados usando LINQ (Visual Basic)

As consultas de LINQ (consulta integrada à linguagem) facilitam o acesso a informações do banco de dados e a modificação de valores no banco de dados.

O exemplo a seguir mostra como criar um novo aplicativo que recupera e atualiza informações em um banco de dados SQL Server.

Os exemplos neste tópico usam o banco de dados de exemplo Northwind. Se você não tiver esse banco de dados no computador de desenvolvimento, poderá baixá-lo no centro de download da Microsoft. Para obter instruções, consulte [baixar bancos de dados de exemplo](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).

### <a name="to-create-a-connection-to-a-database"></a>Para criar uma conexão com um banco de dados

1. No Visual Studio, abra **Gerenciador de Servidores** /**Gerenciador de banco de dados** clicando no menu **Exibir** e, em seguida, selecione **Gerenciador de servidores** /**Gerenciador de banco de dados**.

2. Clique com o botão direito do mouse em **conexões de dados** no **Gerenciador de servidores** /**Gerenciador de banco de dados**e clique em **Adicionar conexão**.

3. Especifique uma conexão válida para o banco de dados de exemplo Northwind.

### <a name="to-add-a-project-with-a-linq-to-sql-file"></a>Para adicionar um projeto com um arquivo LINQ to SQL

1. No Visual Studio, no menu **Arquivo**, aponte para **Novo** e clique em **Projeto**. Selecione Visual Basic **aplicativo Windows Forms** como o tipo de projeto.

2. No menu **Projeto**, clique em **Adicionar Novo Item**. Selecione o modelo de item **classes de LINQ to SQL** .

3. Dê o nome `northwind.dbml` para o arquivo. Clique em **Adicionar**. O Object Relational Designer (O/R Designer) é aberto para o arquivo de `northwind.dbml`.

### <a name="to-add-tables-to-query-and-modify-to-the-designer"></a>Para adicionar tabelas à consulta e modificar para o designer

1. Em **Gerenciador de Servidores** /**Gerenciador de banco de dados**, expanda a conexão com o banco de dados Northwind. Expanda a pasta **tabelas** .

     Se você fechou o o/R Designer, você pode reabri-lo clicando duas vezes no arquivo `northwind.dbml` que você adicionou anteriormente.

2. Clique na tabela clientes e arraste-a para o painel esquerdo do designer.

     O designer cria um novo objeto de cliente para seu projeto.

3. Salve as alterações e feche o designer.

4. Salve seu projeto.

### <a name="to-add-code-to-modify-the-database-and-display-the-results"></a>Para adicionar código para modificar o banco de dados e exibir os resultados

1. Na **caixa de ferramentas**, arraste um controle de <xref:System.Windows.Forms.DataGridView> para o formulário padrão do Windows para seu projeto, Form1.

2. Quando você adicionou tabelas ao o/R Designer, o designer adicionou um objeto <xref:System.Data.Linq.DataContext> ao seu projeto. Este objeto contém código que você pode usar para acessar a tabela Customers. Ele também contém um código que define um objeto Customer local e uma coleção Customers para a tabela. O objeto <xref:System.Data.Linq.DataContext> para seu projeto é nomeado com base no nome do seu arquivo. dbml. Para este projeto, o objeto <xref:System.Data.Linq.DataContext> é nomeado `northwindDataContext`.

     Você pode criar uma instância do objeto <xref:System.Data.Linq.DataContext> em seu código e consultar e modificar a coleção Customers especificada pelo o/R Designer. As alterações feitas na coleção clientes não são refletidas no banco de dados até que você as envie chamando o método <xref:System.Data.Linq.DataContext.SubmitChanges%2A> do objeto <xref:System.Data.Linq.DataContext>.

     Clique duas vezes no Windows Form, Form1, para adicionar código ao evento <xref:System.Windows.Forms.Form.Load> para consultar a tabela Customers que é exposta como uma propriedade de sua <xref:System.Data.Linq.DataContext>. Adicione o seguinte código:

    ```vb
    Private db As northwindDataContext

    Private Sub Form1_Load(ByVal sender As System.Object,
                           ByVal e As System.EventArgs
                          ) Handles MyBase.Load
      db = New northwindDataContext()

      RefreshData()
    End Sub

    Private Sub RefreshData()
      Dim customers = From cust In db.Customers
                      Where cust.City(0) = "W"
                      Select cust

      DataGridView1.DataSource = customers
    End Sub
    ```

3. Na **caixa de ferramentas**, arraste três controles de <xref:System.Windows.Forms.Button> para o formulário. Selecione o primeiro controle de `Button`. Na janela **Propriedades** , defina a `Name` do controle de `Button` como `AddButton` e o `Text` como `Add`. Selecione o segundo botão e defina a propriedade `Name` como `UpdateButton` e a propriedade `Text` como `Update`. Selecione o terceiro botão e defina a propriedade `Name` como `DeleteButton` e a propriedade `Text` como `Delete`.

4. Clique duas vezes no botão **Adicionar** para adicionar código ao seu evento `Click`. Adicione o seguinte código:

    ```vb
    Private Sub AddButton_Click(ByVal sender As System.Object,
                                ByVal e As System.EventArgs
                               ) Handles AddButton.Click
      Dim cust As New Customer With {
        .City = "Wellington",
        .CompanyName = "Blue Yonder Airlines",
        .ContactName = "Jill Frank",
        .Country = "New Zealand",
        .CustomerID = "JILLF"}

      db.Customers.InsertOnSubmit(cust)

      Try
        db.SubmitChanges()
      Catch
        ' Handle exception.
      End Try

      RefreshData()
    End Sub
    ```

5. Clique duas vezes no botão **Atualizar** para adicionar código ao seu evento `Click`. Adicione o seguinte código:

    ```vb
    Private Sub UpdateButton_Click(ByVal sender As System.Object, _
                                   ByVal e As System.EventArgs
                                  ) Handles UpdateButton.Click
      Dim updateCust = (From cust In db.Customers
                        Where cust.CustomerID = "JILLF").ToList()(0)

      updateCust.ContactName = "Jill Shrader"
      updateCust.Country = "Wales"
      updateCust.CompanyName = "Red Yonder Airlines"
      updateCust.City = "Cardiff"

      Try
        db.SubmitChanges()
      Catch
        ' Handle exception.
      End Try

      RefreshData()
    End Sub
    ```

6. Clique duas vezes no botão **excluir** para adicionar código ao seu evento `Click`. Adicione o seguinte código:

    ```vb
    Private Sub DeleteButton_Click(ByVal sender As System.Object, _
                                   ByVal e As System.EventArgs
                                  ) Handles DeleteButton.Click
      Dim deleteCust = (From cust In db.Customers
                        Where cust.CustomerID = "JILLF").ToList()(0)

      db.Customers.DeleteOnSubmit(deleteCust)

      Try
        db.SubmitChanges()
      Catch
        ' Handle exception.
      End Try

      RefreshData()
    End Sub
    ```

7. Pressione F5 para executar o projeto. Clique em **Adicionar** para adicionar um novo registro. Clique em **Atualizar** para modificar o novo registro. Clique em **excluir** para excluir o novo registro.

## <a name="see-also"></a>Consulte também

- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [Consultas](../../../../visual-basic/language-reference/queries/index.md)
- [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)
- [Métodos DataContext (Designer Relacional de Objetos)](/visualstudio/data-tools/datacontext-methods-o-r-designer)
- [Como atribuir procedimentos armazenados para executar atualizações, inserções e exclusões (Designer Relacional de Objetos)](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)
