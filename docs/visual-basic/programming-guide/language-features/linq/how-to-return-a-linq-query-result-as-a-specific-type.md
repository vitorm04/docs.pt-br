---
title: "Como retornar um resultado de consulta LINQ como um tipo espec&#237;fico (Visual Basic) | Microsoft Docs"
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
  - "tipos anônimos [Visual Basic]"
  - "projeção [LINQ no Visual Basic]"
  - "consultas [LINQ no Visual Basic], tópicos explicativos"
  - "consultas [LINQ no Visual Basic], tipo específico retornado"
  - "exemplos de consulta [Visual Basic]"
  - "consultando bancos de dados [LINQ]"
ms.assetid: 621bb10a-e5d7-44fb-a025-317964b19d92
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como retornar um resultado de consulta LINQ como um tipo espec&#237;fico (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Consulta Integrada à Linguagem \(LINQ, Language\-Integrated Query\) facilita o acesso a informações do banco de dados e a execução de consultas.  Por padrão, consultas LINQ retornam uma lista de objetos com um tipo anônimo.  Você também pode especificar que uma consulta retorne uma lista de um tipo específico usando a cláusula `Select`.  
  
 O exemplo a seguir mostra como criar um novo aplicativo que executa consultas em um banco de dados SQL Server e projeta os resultados como um tipo específico.  Para obter mais informações, consulte [Tipos anônimos](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md) e [Cláusula Select](../../../../visual-basic/language-reference/queries/select-clause.md).  
  
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
  
2.  Clique na tabela Clientes e arraste\-a para o painel esquerdo do designer.  
  
     O designer cria um novo objeto `Customer` para o seu projeto.  Você pode projetar um resultado de consulta como o tipo `Customer` ou um tipo que você criar.  Este exemplo criará um novo tipo em um procedimento posterior e projetar um resultado de consulta como esse tipo.  
  
3.  Salve suas alterações e feche o designer.  
  
4.  Salve seu projeto.  
  
### Para adicionar um código de consulta ao banco de dados e exibir os resultados  
  
1.  Da **Caixa de Ferramentas**, arraste um controle <xref:System.Windows.Forms.DataGridView> para o Windows Form padrão para seu projeto, Form1.  
  
2.  Clique duas vezes em Form1 para modificar a classe Form1.  
  
3.  Após a instrução `End Class` da classe Form1, adicione o código seguinte para criar um tipo `CustomerInfo` para armazenar os resultados da consulta para esse exemplo.  
  
     [!code-vb[VbLINQToSQLHowTos#16](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-return-a-linq-query-result-as-a-specific-type_1.vb)]  
  
4.  Quando você adicionar tabelas ao O\/R Designer, o designer adicionará um objeto <xref:System.Data.Linq.DataContext> ao projeto.  Este objeto contém o código que você deve ter para acessar essas tabelas e para acessar objetos individuais e coleções para cada tabela.  O objeto <xref:System.Data.Linq.DataContext> para seu projeto é nomeado com base no nome do arquivo .dbml.  Para este projeto, o objeto <xref:System.Data.Linq.DataContext> é denominado `northwindDataContext`.  
  
     Você pode criar uma instância de <xref:System.Data.Linq.DataContext> no seu código e consultar as tabelas especificadas pelo O\/R Designer.  
  
     No evento `Load`, adicione o seguinte código para consultar as tabelas que estão expostas como propriedades de seu contexto de dados.  A cláusula `Select` da consulta irá criar um novo tipo `CustomerInfo` em vez de um tipo anônimo para cada item do resultado da consulta.  
  
     [!code-vb[VbLINQToSQLHowTos#15](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-return-a-linq-query-result-as-a-specific-type_2.vb)]  
  
5.  Pressione F5 para executar seu projeto e exibir os resultados.  
  
## Consulte também  
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)   
 [Consultas](../../../../visual-basic/language-reference/queries/queries.md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)   
 [DataContext Methods \(O\/R Designer\)](/visual-studio/data-tools/datacontext-methods-o-r-designer)   
 [Walkthrough: Creating LINQ to SQL Classes \(O\/R Designer\)](../Topic/Walkthrough:%20Creating%20LINQ%20to%20SQL%20Classes%20\(O-R%20Designer\).md)