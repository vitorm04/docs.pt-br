---
title: "Como chamar um procedimento armazenado usando LINQ (Visual Basic) | Microsoft Docs"
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
  - "consultas [LINQ no Visual Basic], tópicos explicativos"
  - "consultas [LINQ no Visual Basic], chamadas de procedimento armazenado"
  - "procedimentos armazenados [LINQ to SQL]"
  - "procedimentos armazenados de exemplo [Visual Basic]"
ms.assetid: 6436d384-d1e0-40aa-8afd-451007477260
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como chamar um procedimento armazenado usando LINQ (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

A Consulta Integrada à Linguagem \(LINQ\) facilita o acesso a informações do banco de dados, incluindo objetos de banco de dados como procedimentos armazenados.  
  
 O exemplo a seguir mostra como criar um aplicativo que chama uma procedimento armazenado em um banco de dados SQL Server.  O exemplo mostra como chamar dois procedimentos diferentes armazenados no banco de dados.  Cada procedimento retorna os resultados de uma consulta.  Um procedimento utiliza parâmetros de entrada, e o outro procedimento não aceita parâmetros.  
  
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
  
### Adicionar procedimentos armazenados ao Designer O\/R  
  
1.  Em **Gerenciador de Servidores**\/ **Gerenciador de Banco de dados** , expanda a conexão para o banco de dados Northwind.  Expanda a pasta  **Procedimentos Armazenados** .  
  
     Se você tiver fechado o O\/R Designer, você poderá reabri\-lo clicando duas vezes no arquivo northwind.dbml que você adicionou anteriormente.  
  
2.  Clique no procedimento armazenado  **Sales by Year** e arraste\-o para painel à direita do designer.  Clique no procedimento armazenado  **Ten Most Expensive Products** e arraste\-o para o painel à direita do designer.  
  
3.  Salve suas alterações e feche o designer.  
  
4.  Salve seu projeto.  
  
### Adicionar código para exibir os resultados dos procedimentos armazenados  
  
1.  Da **Caixa de Ferramentas**, arraste um controle <xref:System.Windows.Forms.DataGridView> para o Windows Form padrão para seu projeto, Form1.  
  
2.  Clique duas vezes em Form1 para adicionar código ao evento `Load`.  
  
3.  Quando você adicionou procedimentos armazenados ao O\/R Designer, o designer adicionará um objeto <xref:System.Data.Linq.DataContext> ao projeto.  Este objeto contém o código que você deve ter para acessar esses procedimentos.  O objeto <xref:System.Data.Linq.DataContext> para o projeto é nomeado com base no nome do arquivo .dbml.  Para este projeto, o objeto <xref:System.Data.Linq.DataContext> é denominado `northwindDataContext`.  
  
     Você pode criar uma instância de <xref:System.Data.Linq.DataContext> no seu código e chamar os métodos de procedimento armazenados especificados pelo O\/R Designer.  Para vincular ao objeto <xref:System.Windows.Forms.DataGridView>, talvez você precise forçar que a consulta execute imediatamente chamando o método <xref:System.Linq.Enumerable.ToList%2A> nos resultados do procedimento armazenado.  
  
     Adicione o seguinte código ao evento `Load` para chamar um dos procedimentos armazenados expostos como métodos para o contexto de dados.  
  
     [!code-vb[VbLINQtoSQLHowTos#1](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-call-a-stored-procedure-by-using-linq_1.vb)]  
    [!code-vb[VbLINQtoSQLHowTos#2](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-call-a-stored-procedure-by-using-linq_2.vb)]  
  
4.  Pressione F5 para executar seu projeto e exibir os resultados.  
  
## Consulte também  
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)   
 [Consultas](../../../../visual-basic/language-reference/queries/queries.md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)   
 [DataContext Methods \(O\/R Designer\)](/visual-studio/data-tools/datacontext-methods-o-r-designer)   
 [Como: atribuir procedimentos armazenados para executar atualizações, inserções e exclusões \(Object Relational Designer\)](../Topic/How%20to:%20Assign%20stored%20procedures%20to%20perform%20updates,%20inserts,%20and%20deletes%20\(O-R%20Designer\).md)   
 [Walkthrough: Creating LINQ to SQL Classes \(O\/R Designer\)](../Topic/Walkthrough:%20Creating%20LINQ%20to%20SQL%20Classes%20\(O-R%20Designer\).md)