---
title: "Como modificar dados em um banco de dados usando LINQ (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "dados [Visual Basic], atualizando"
  - "excluindo dados"
  - "excluindo linhas [LINQ to SQL]"
  - "inserindo dados [Visual Basic]"
  - "inserindo linhas [LINQ to SQL]"
  - "consultas [LINQ no Visual Basic], alterações de dados no banco de dados"
  - "consultas [LINQ no Visual Basic], tópicos explicativos"
  - "atualizando dados [LINQ]"
  - "atualizando linhas [LINQ to SQL]"
ms.assetid: cf52635f-0c1b-46c3-aff1-bdf181cf19b1
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como modificar dados em um banco de dados usando LINQ (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Consultas do LINQ \(consulta\) integrada à linguagem facilitam acessar as informações do banco de dados e modificar valores no banco de dados.  
  
 O exemplo a seguir mostra como criar um novo aplicativo que recupera e atualiza as informações em um banco de dados SQL Server.  
  
 Os exemplos neste tópico usam o banco de dados de exemplo Northwind.  Se você não tiver o banco de dados de exemplo Northwind no seu computador de desenvolvimento, você poderá baixá\-lo do site da Web [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=98088).  Para obter instruções, consulte [Downloading Sample Databases](../Topic/Downloading%20Sample%20Databases.md).  
  
### Para criar uma conexão com um banco de dados  
  
1.  No Visual Studio, abra  **Server Explorer**\/**Database Explorer** clicando o  **Exibir** menu e, em seguida, selecione  **Server Explorer**\/**Database Explorer**.  
  
2.  Com o botão direito  **Conexões de dados** na  **Server Explorer**\/**Database Explorer**e clique em  **Add Connection**.  
  
3.  Especifique uma conexão válida ao banco de dados de exemplo Northwind.  
  
### Para adicionar um projeto com um LINQ to SQL de arquivo  
  
1.  No Visual Studio, no menu **File**, aponte para **New** e em seguida clique em **Project**.  Selecione **Aplicativo Windows Forms** Visual Basic como o tipo de projeto.  
  
2.  No menu **Project**, clique em **Add New Item**.  Selecione o modelo de item **Classes LINQ to SQL** .  
  
3.  Nomeie o arquivo `northwind.dbml`.  Clique em **Adicionar**.  O Object Relational Designer \(O\/R Designer\) é aberto para o  `northwind.dbml` arquivo.  
  
### Para adicionar tabelas para consultar e modificar para o designer  
  
1.  Em **Gerenciador de Servidores**\/ **Gerenciador de Banco de dados** , expanda a conexão para o banco de dados Northwind.  Expanda a pasta **Tabelas**.  
  
     Se você tiver fechado o O\/R Designer, você poderá reabri\-lo clicando duas vezes o  `northwind.dbml` o arquivo que você adicionou anteriormente.  
  
2.  Clique na tabela Clientes e arraste\-a para o painel esquerdo do designer.  
  
     O designer cria um novo objeto de cliente para o seu projeto.  
  
3.  Salve suas alterações e feche o designer.  
  
4.  Salve seu projeto.  
  
### Para adicionar código para modificar o banco de dados e exibir os resultados  
  
1.  Da **Caixa de Ferramentas**, arraste um controle <xref:System.Windows.Forms.DataGridView> para o Windows Form padrão para seu projeto, Form1.  
  
2.  Quando você adicionar tabelas ao O\/R Designer, o designer adicionará um objeto <xref:System.Data.Linq.DataContext> ao projeto.  Este objeto contém código que você pode usar para acessar a tabela de clientes.  Ele também contém código que define um objeto local do cliente e uma coleção de clientes para a tabela.  O objeto <xref:System.Data.Linq.DataContext> para seu projeto é nomeado com base no nome do arquivo .dbml.  Para este projeto, o objeto <xref:System.Data.Linq.DataContext> é denominado `northwindDataContext`.  
  
     Você pode criar uma instância da <xref:System.Data.Linq.DataContext> de objeto em seu código e a consulta e modificar a coleção de clientes especificada pelo \/ R Designer.  As alterações feitas para a coleção de clientes não são refletidas no banco de dados até que você enviá\-los, chamando o <xref:System.Data.Linq.DataContext.SubmitChanges%2A> método da <xref:System.Data.Linq.DataContext> objeto.  
  
     Clique duas vezes no formulário do Windows, Form1, para adicionar código para o <xref:System.Windows.Forms.Form.Load> evento para consulta, os clientes da tabela que é exposto como uma propriedade de seu <xref:System.Data.Linq.DataContext>.  Adicione o seguinte código:  
  
    ```vb#  
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
  
3.  Do  **caixa de ferramentas**, arraste três <xref:System.Windows.Forms.Button> controles para o formulário.  Selecione o primeiro `Button` controle.  No  **Propriedades** janela, defina a `Name` da `Button` o controle para  `AddButton` e o `Text` para  `Add`.  Selecione o segundo botão e defina a `Name` propriedade para  `UpdateButton` e o `Text` propriedade para  `atualização`.  Selecione o terceiro botão e defina a `Name` propriedade para  `DeleteButton` e o `Text` propriedade para  `Excluir`.  
  
4.  Clique duas vezes o  **Add** o botão para adicionar código para seu `Click` evento.  Adicione o seguinte código:  
  
    ```vb#  
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
  
5.  Clique duas vezes o  **atualização** o botão para adicionar código para seu `Click` evento.  Adicione o seguinte código:  
  
    ```vb#  
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
  
6.  Clique duas vezes o  **Excluir** o botão para adicionar código para seu `Click` evento.  Adicione o seguinte código:  
  
    ```vb#  
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
  
7.  Pressione F5 para executar o projeto.  Clique em  **Add** para adicionar um novo registro.  Clique em  **atualização** para modificar o novo registro.  Clique em  **Excluir** para excluir o novo registro.  
  
## Consulte também  
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)   
 [Consultas](../../../../visual-basic/language-reference/queries/queries.md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)   
 [DataContext Methods \(O\/R Designer\)](/visual-studio/data-tools/datacontext-methods-o-r-designer)   
 [Como: atribuir procedimentos armazenados para executar atualizações, inserções e exclusões \(Object Relational Designer\)](../Topic/How%20to:%20Assign%20stored%20procedures%20to%20perform%20updates,%20inserts,%20and%20deletes%20\(O-R%20Designer\).md)   
 [Walkthrough: Creating LINQ to SQL Classes \(O\/R Designer\)](../Topic/Walkthrough:%20Creating%20LINQ%20to%20SQL%20Classes%20\(O-R%20Designer\).md)