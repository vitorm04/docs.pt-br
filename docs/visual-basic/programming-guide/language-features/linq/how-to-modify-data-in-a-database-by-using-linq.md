---
title: 'Como: modificar dados em um banco de dados usando LINQ (Visual Basic) | Documentos do Microsoft'
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
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
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 44ca3e44d8411a6329d176eb778677bfab2b365c
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-modify-data-in-a-database-by-using-linq-visual-basic"></a>Como modificar dados em um banco de dados usando LINQ (Visual Basic)
Consultas integradas à linguagem de consulta (LINQ) facilitam a acessar as informações do banco de dados e modifique os valores no banco de dados.  
  
 O exemplo a seguir mostra como criar um novo aplicativo que recupera e atualiza as informações em um banco de dados do SQL Server.  
  
 Os exemplos neste tópico usam o banco de dados de exemplo Northwind. Se você não tiver o banco de dados de exemplo Northwind no seu computador de desenvolvimento, você pode baixá-lo do [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=98088) site da Web. Para obter instruções, consulte [baixando bancos de dados de exemplo](https://msdn.microsoft.com/library/bb399411).  
  
### <a name="to-create-a-connection-to-a-database"></a>Para criar uma conexão para um banco de dados  
  
1.  No Visual Studio, abra **Server Explorer**/**Database Explorer** clicando o **exibição** menu e selecione **Server Explorer**/**Database Explorer**.  
  
2.  Clique com botão direito **conexões de dados** na **Server Explorer**/**Database Explorer**e clique em **Adicionar Conexão**.  
  
3.  Especifique uma conexão válida para o banco de dados de exemplo Northwind.  
  
### <a name="to-add-a-project-with-a-linq-to-sql-file"></a>Para adicionar um projeto com um LINQ para SQL file  
  
1.  No Visual Studio, no **arquivo** , aponte para **novo** e, em seguida, clique em **projeto**. Selecione Visual Basic **Windows Forms Application** como o tipo de projeto.  
  
2.  No menu **Projeto**, clique em **Adicionar Novo Item**. Selecione o **Classes LINQ to SQL** modelo de item.  
  
3.  Nomeie o arquivo `northwind.dbml`. Clique em **Adicionar**. O Object Relational Designer (Object Relational Designer) é aberto para o `northwind.dbml` arquivo.  
  
### <a name="to-add-tables-to-query-and-modify-to-the-designer"></a>Para adicionar tabelas para consultar e modificar para o designer  
  
1.  Em **Server Explorer**/**Database Explorer**, expanda a conexão ao banco de dados Northwind. Expanda o **tabelas** pasta.  
  
     Se você tiver fechado o Object Relational Designer, você poderá reabri-lo clicando duas vezes o `northwind.dbml` arquivo que você adicionou anteriormente.  
  
2.  Clique na tabela clientes e arraste-o para o painel esquerdo do designer.  
  
     O designer cria um novo objeto de cliente para o seu projeto.  
  
3.  Salve suas alterações e feche o designer.  
  
4.  Salve seu projeto.  
  
### <a name="to-add-code-to-modify-the-database-and-display-the-results"></a>Para adicionar código para modificar o banco de dados e exibir os resultados  
  
1.  Do **Toolbox**, arraste um <xref:System.Windows.Forms.DataGridView>controle para o Windows Form padrão para seu projeto, Form1.</xref:System.Windows.Forms.DataGridView>  
  
2.  Quando você adicionar tabelas ao / R Designer, o designer adicionará um <xref:System.Data.Linq.DataContext>objeto ao seu projeto.</xref:System.Data.Linq.DataContext> Este objeto contém o código que você pode usar para acessar a tabela de clientes. Ele também contém o código que define um objeto de cliente local e uma coleção de clientes para a tabela. O <xref:System.Data.Linq.DataContext>objeto para seu projeto é nomeado com base no nome do seu arquivo. dbml.</xref:System.Data.Linq.DataContext> Para este projeto, o <xref:System.Data.Linq.DataContext>objeto é denominado `northwindDataContext`.</xref:System.Data.Linq.DataContext>  
  
     Você pode criar uma instância do <xref:System.Data.Linq.DataContext>do objeto no seu código e consultar e modificar a coleção de clientes especificada por Object Relational Designer.</xref:System.Data.Linq.DataContext> As alterações feitas na coleção de clientes não serão refletidas no banco de dados enquanto você enviá-los ao chamar o <xref:System.Data.Linq.DataContext.SubmitChanges%2A>método de <xref:System.Data.Linq.DataContext>objeto.</xref:System.Data.Linq.DataContext> </xref:System.Data.Linq.DataContext.SubmitChanges%2A>  
  
     Clique duas vezes em Windows Form, Form1, para adicionar código ao <xref:System.Windows.Forms.Form.Load>evento para consultar a tabela de clientes que é exposta como uma propriedade de <xref:System.Data.Linq.DataContext>.</xref:System.Data.Linq.DataContext> </xref:System.Windows.Forms.Form.Load> Adicione o seguinte código:  
  
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
  
3.  Do **Toolbox**, arraste três <xref:System.Windows.Forms.Button>controles para o formulário.</xref:System.Windows.Forms.Button> Selecione o primeiro `Button` controle. No **propriedades** janela, defina a `Name` do `Button` controle `AddButton` e `Text` para `Add`. Selecione o segundo botão e defina o `Name` propriedade `UpdateButton` e `Text` propriedade `Update`. Selecione o terceiro botão e defina o `Name` propriedade `DeleteButton` e `Text` propriedade `Delete`.  
  
4.  Clique duas vezes o **adicionar** botão Adicionar código ao seu `Click` eventos. Adicione o seguinte código:  
  
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
  
5.  Clique duas vezes o **atualização** botão Adicionar código ao seu `Click` eventos. Adicione o seguinte código:  
  
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
  
6.  Clique duas vezes o **excluir** botão Adicionar código ao seu `Click` eventos. Adicione o seguinte código:  
  
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
 [Consultas](../../../../visual-basic/language-reference/queries/queries.md)   
 [LINQ to SQL](https://msdn.microsoft.com/library/bb386976)   
 [Métodos de DataContext (Object Relational Designer)](https://docs.microsoft.com/visualstudio/data-tools/datacontext-methods-o-r-designer)   
 [Como: atribuir procedimentos armazenados para executar atualizações, inserções e exclusões (Object Relational Designer)](http://msdn.microsoft.com/library/e88224ab-ff61-4a3a-b6b8-6f3694546cac)
