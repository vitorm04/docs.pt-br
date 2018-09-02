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
ms.openlocfilehash: 02aaf2924c6230615d7d1cbcceac72265419b541
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43402890"
---
# <a name="how-to-modify-data-in-a-database-by-using-linq-visual-basic"></a>Como modificar dados em um banco de dados usando LINQ (Visual Basic)
Consultas integradas à linguagem de consulta (LINQ) tornam fácil acessar as informações de banco de dados e modificar valores no banco de dados.  
  
 O exemplo a seguir mostra como criar um novo aplicativo que recupera e atualiza as informações em um banco de dados do SQL Server.  
  
 Os exemplos neste tópico usam o banco de dados de exemplo Northwind. Se você não tiver esse banco de dados no computador de desenvolvimento, você pode baixá-lo do Microsoft Download Center. Para obter instruções, consulte [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).  
  
### <a name="to-create-a-connection-to-a-database"></a>Para criar uma conexão para um banco de dados  
  
1.  No Visual Studio, abra **Gerenciador de servidores**/**Database Explorer** clicando o **exibição** menu e, em seguida, selecione **Gerenciadordeservidores** / **Gerenciador de banco de dados**.  
  
2.  Clique com botão direito **conexões de dados** na **Gerenciador de servidores**/**Database Explorer**e clique em **Adicionar Conexão**.  
  
3.  Especifique uma conexão válida para o banco de dados de exemplo Northwind.  
  
### <a name="to-add-a-project-with-a-linq-to-sql-file"></a>Para adicionar um projeto com um LINQ para arquivo SQL  
  
1.  No Visual Studio, no menu **Arquivo**, aponte para **Novo** e clique em **Projeto**. Selecione Visual Basic **aplicativo do Windows Forms** como o tipo de projeto.  
  
2.  No menu **Projeto**, clique em **Adicionar Novo Item**. Selecione o **Classes LINQ to SQL** modelo de item.  
  
3.  Dê o nome `northwind.dbml` para o arquivo. Clique em **Adicionar**. O Object Relational Designer (O/R Designer) é aberto para o `northwind.dbml` arquivo.  
  
### <a name="to-add-tables-to-query-and-modify-to-the-designer"></a>Para adicionar tabelas para consultar e modificar para o designer  
  
1.  Na **Gerenciador de servidores**/**Gerenciador de banco de dados**, expanda a conexão ao banco de dados Northwind. Expanda o **tabelas** pasta.  
  
     Se você tiver fechado o O/R Designer, você poderá reabri-lo clicando duas vezes o `northwind.dbml` arquivo que você adicionou anteriormente.  
  
2.  Clique na tabela clientes e arraste-o no painel esquerdo do designer.  
  
     O designer cria um novo objeto de cliente para seu projeto.  
  
3.  Salve suas alterações e feche o designer.  
  
4.  Salve seu projeto.  
  
### <a name="to-add-code-to-modify-the-database-and-display-the-results"></a>Para adicionar código para modificar o banco de dados e exibir os resultados  
  
1.  Dos **caixa de ferramentas**, arraste um <xref:System.Windows.Forms.DataGridView> controle para o formulário do Windows padrão para seu projeto, Form1.  
  
2.  Quando você adicionar tabelas ao Designer relacional de objetos, o designer adicionará um <xref:System.Data.Linq.DataContext> objeto ao seu projeto. Este objeto contém código que você pode usar para acessar a tabela de clientes. Ele também contém código que define um objeto de cliente local e uma coleção de clientes para a tabela. O <xref:System.Data.Linq.DataContext> objeto para seu projeto é nomeado com base no nome do seu arquivo. dbml. Para este projeto, o <xref:System.Data.Linq.DataContext> objeto é nomeado `northwindDataContext`.  
  
     Você pode criar uma instância da <xref:System.Data.Linq.DataContext> do objeto no seu código e consultar e modificar a coleção de clientes especificada pelo Designer relacional de objetos. As alterações feitas à coleção de clientes não são refletidas no banco de dados até que você pode enviá-los por meio da chamada a <xref:System.Data.Linq.DataContext.SubmitChanges%2A> método da <xref:System.Data.Linq.DataContext> objeto.  
  
     Duas vezes no formulário do Windows Form1, para adicionar código para o <xref:System.Windows.Forms.Form.Load> eventos para consultar a tabela de clientes que é exposto como uma propriedade de seu <xref:System.Data.Linq.DataContext>. Adicione o seguinte código:  
  
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
  
3.  Dos **caixa de ferramentas**, arraste três <xref:System.Windows.Forms.Button> controles para o formulário. Selecione a primeira `Button` controle. No **propriedades** janela, defina as `Name` da `Button` o controle para `AddButton` e o `Text` para `Add`. Selecione o segundo botão e defina as `Name` propriedade para `UpdateButton` e o `Text` propriedade `Update`. Selecione o terceiro botão e defina as `Name` propriedade para `DeleteButton` e o `Text` propriedade `Delete`.  
  
4.  Clique duas vezes o **Add** botão para adicionar código para seu `Click` eventos. Adicione o seguinte código:  
  
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
  
5.  Clique duas vezes o **atualização** botão para adicionar código ao seu `Click` eventos. Adicione o seguinte código:  
  
    ```vb  
    Private Sub UpdateButton_Click(ByVal sender As System.Object, _  
                                   ByVal e As System.EventArgs  
                                  ) Handles UpdateButton.Click  
      Dim updateCust = (From cust In db.Customers   
                        Where cust.CustomerID = "JILLF").ToList()(0)  
  
      updateCust.ContactName = "Jill Shrader"  
  
      Try  
        db.SubmitChanges()  
      Catch  
        ' Handle exception.  
      End Try  
  
      RefreshData()  
    End Sub  
    ```  
  
6.  Clique duas vezes o **excluir** botão para adicionar código ao seu `Click` eventos. Adicione o seguinte código:  
  
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
  
7.  Pressione F5 para executar o projeto. Clique em **adicionar** para adicionar um novo registro. Clique em **atualização** para modificar o novo registro. Clique em **excluir** para excluir o novo registro.  
  
## <a name="see-also"></a>Consulte também  
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [Consultas](../../../../visual-basic/language-reference/queries/index.md)  
 [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)  
 [Métodos DataContext (Designer Relacional de Objetos)](/visualstudio/data-tools/datacontext-methods-o-r-designer)  
 [Como atribuir procedimentos armazenados para executar atualizações, inserções e exclusões (Designer Relacional de Objetos)](https://msdn.microsoft.com/library/e88224ab-ff61-4a3a-b6b8-6f3694546cac)
