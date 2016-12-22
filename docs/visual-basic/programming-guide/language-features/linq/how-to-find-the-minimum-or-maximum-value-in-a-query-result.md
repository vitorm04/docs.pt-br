---
title: "Como localizar o valor m&#237;nimo ou m&#225;ximo em um resultado de consulta usando LINQ (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "cláusula Aggregate"
  - "Operador aggregate [LINQ em Visual Basic]"
  - "consultas de agregação"
  - "Operador max [LINQ no Visual Basic]"
  - "propriedade Max"
  - "valores máximos [LINQ no Visual Basic]"
  - "Operador min [LINQ no Visual Basic]"
  - "valores mínimos [LINQ no Visual Basic]"
  - "consultas [LINQ no Visual Basic], consultas de agregação"
  - "consultas [LINQ no Visual Basic], tópicos explicativos"
  - "consultas [LINQ no Visual Basic], valores mínimo e máximo"
ms.assetid: 238b763b-7dcd-4b14-8050-b65500a4f71c
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como localizar o valor m&#237;nimo ou m&#225;ximo em um resultado de consulta usando LINQ (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Consulta Integrada à Linguagem \(LINQ, Language\-Integrated Query\) facilita o acesso a informações do banco de dados e a execução de consultas.  
  
 O exemplo a seguir mostra como criar um novo aplicativo que executa consultas em um banco de dados SQL Server.  O exemplo determina os valores mínimo e máximo para os resultados usando as cláusulas `Aggregate` e `Group By`.  Para obter mais informações, consulte [Cláusula Aggregate](../../../../visual-basic/language-reference/queries/aggregate-clause.md) e [Cláusula Group By](../../../../visual-basic/language-reference/queries/group-by-clause.md).  
  
 Os exemplos neste tópico usam o banco de dados de exemplo Northwind.  Se você não tiver o banco de dados de exemplo Northwind no seu computador de desenvolvimento, você poderá baixá\-lo do site da Web [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=98088).  Para obter instruções, consulte [Downloading Sample Databases](../Topic/Downloading%20Sample%20Databases.md).  
  
 [!INCLUDE[note_settings_general](../../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
### Para criar uma conexão com um banco de dados  
  
1.  No Visual Studio, abra **Gerenciador de Servidores**\/**Gerenciador de Banco de Dados** clicando em **Gerenciador de Servidores**\/**Gerenciador de Banco de Dados** no menu **Exibir** .  
  
2.  Clique com o botão direito do mouse em **Conexões de Dados** no  **Gerenciador de Servidores**\/**Gerenciador de Banco de Dados** e, em seguida, clique em **Adicionar Conexões**.  
  
3.  Especifique uma conexão válida ao banco de dados de exemplo Northwind.  
  
### Para adicionar um projeto que contém um arquivo LINQ to SQL  
  
1.  No Visual Studio, no menu **File**, aponte para **New** e em seguida clique em **Project**.  Selecione **Aplicativo Windows Forms** Visual Basic como o tipo de projeto.  
  
2.  No menu **Project**, clique em **Add New Item**.  Selecione o modelo de item **Classes LINQ to SQL** .  
  
3.  Nomeie o arquivo `northwind.dbml`.  Clique em **Adicionar**.  O Object Relational Designer \(O\/R Designer\) é aberto para o arquivo northwind.dbml.  
  
### Para adicionar tabelas de consulta para o criador O\/R  
  
1.  Em **Gerenciador de Servidores**\/ **Gerenciador de Banco de dados** , expanda a conexão para o banco de dados Northwind.  Expanda a pasta **Tabelas**.  
  
     Se você tiver fechado o O\/R Designer, você poderá reabri\-lo clicando duas vezes no arquivo northwind.dbml que você adicionou anteriormente.  
  
2.  Clique na tabela Clientes e arraste\-a para o painel esquerdo do designer.  Clique na tabela Ordens e arraste\-a para o painel esquerdo do designer.  
  
     O designer cria novos objetos `Customer` e `Order` para seu projeto.  Observe que o designer automaticamente detecta relacionamentos entre as tabelas e cria propriedades filhas para objetos relacionados.  Por exemplo, o IntelliSense mostrará que o objeto `Customer` tem uma propriedade `Orders` para todos os pedidos relacionados a esse cliente.  
  
3.  Salve suas alterações e feche o designer.  
  
4.  Salve seu projeto.  
  
### Para adicionar um código de consulta ao banco de dados e exibir os resultados  
  
1.  Da **Caixa de Ferramentas**, arraste um controle <xref:System.Windows.Forms.DataGridView> para o Windows Form padrão para seu projeto, Form1.  
  
2.  Clique duas vezes em Form1 para adicionar código ao evento `Load` do formulário.  
  
3.  Quando você adicionar tabelas ao O\/R Designer, o designer adicionará um objeto <xref:System.Data.Linq.DataContext> para o projeto.  Este objeto contém o código que você deve ter para acessar essas tabelas, adicionalmente para objetos individuais e coleções para cada tabela.  O objeto <xref:System.Data.Linq.DataContext> para seu projeto é nomeado com base no nome do arquivo .dbml.  Para este projeto, o objeto <xref:System.Data.Linq.DataContext> é denominado `northwindDataContext`.  
  
     Você pode criar uma instância de <xref:System.Data.Linq.DataContext> no seu código e consultar as tabelas especificadas pelo O\/R Designer.  
  
     Adicione o seguinte código para o evento `Load` .  Esse código consulta as tabelas que são expostas como propriedades de seu contexto de dados e determina os valores mínimo e máximo para os resultados.  O exemplo utiliza a cláusula `Aggregate` para consultar um único resultado e a cláusula `Group By` para mostrar uma média para resultados agrupados.  
  
     [!code-vb[VbLINQToSQLHowTos#14](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-find-the-minimum-or-maximum-value-in-a-query-result_1.vb)]  
  
4.  Pressione F5 para executar seu projeto e exibir os resultados.  
  
## Consulte também  
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)   
 [Consultas](../../../../visual-basic/language-reference/queries/queries.md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)   
 [DataContext Methods \(O\/R Designer\)](/visual-studio/data-tools/datacontext-methods-o-r-designer)   
 [Walkthrough: Creating LINQ to SQL Classes \(O\/R Designer\)](../Topic/Walkthrough:%20Creating%20LINQ%20to%20SQL%20Classes%20\(O-R%20Designer\).md)