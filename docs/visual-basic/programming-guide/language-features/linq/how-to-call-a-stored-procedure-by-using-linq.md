---
title: 'Como: chamar um procedimento armazenado usando LINQ (Visual Basic) | Documentos do Microsoft'
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
- queries [LINQ in Visual Basic], stored procedure calls
- stored procedures sample [Visual Basic]
- stored procedures [LINQ to SQL]
- queries [LINQ in Visual Basic], how-to topics
ms.assetid: 6436d384-d1e0-40aa-8afd-451007477260
caps.latest.revision: 12
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: abc3970fc5ab6f4a2f4b67b5efa2b19afb07337b
ms.contentlocale: pt-br
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-call-a-stored-procedure-by-using-linq-visual-basic"></a>Como chamar um procedimento armazenado usando LINQ (Visual Basic)
Consulta integrada à linguagem (LINQ) facilita o acesso a informações do banco de dados, incluindo o banco de dados objetos como procedimentos armazenados.  
  
 O exemplo a seguir mostra como criar um aplicativo que chama um procedimento armazenado em um banco de dados do SQL Server. O exemplo mostra como chamar dois procedimentos diferentes armazenados no banco de dados. Cada procedimento retorna os resultados de uma consulta. Um procedimento utiliza parâmetros de entrada e o outro procedimento não aceita parâmetros.  
  
 Os exemplos neste tópico usam o banco de dados de exemplo Northwind. Se você não tiver o banco de dados de exemplo Northwind no seu computador de desenvolvimento, você pode baixá-lo do [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=98088) site da Web. Para obter instruções, consulte [baixando bancos de dados de exemplo](https://msdn.microsoft.com/library/bb399411).  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a>Para criar uma conexão para um banco de dados  
  
1.  No Visual Studio, abra **Server Explorer**/**Database Explorer** clicando **Server Explorer**/**Database Explorer** sobre o **exibição** menu.  
  
2.  Clique com botão direito **conexões de dados** na **Server Explorer**/**Database Explorer** e, em seguida, clique em **Adicionar Conexão**.  
  
3.  Especifique uma conexão válida para o banco de dados de exemplo Northwind.  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a>Para adicionar um projeto que contém um arquivo LINQ to SQL  
  
1.  No Visual Studio, no **arquivo** , aponte para **novo** e, em seguida, clique em **projeto**. Selecione Visual Basic **Windows Forms Application** como o tipo de projeto.  
  
2.  No menu **Projeto**, clique em **Adicionar Novo Item**. Selecione o **Classes LINQ to SQL** modelo de item.  
  
3.  Nomeie o arquivo `northwind.dbml`. Clique em **Adicionar**. O Object Relational Designer (Object Relational Designer) é aberto para o arquivo Northwind dbml.  
  
### <a name="to-add-stored-procedures-to-the-or-designer"></a>Adicionar procedimentos armazenados para o Object Relational Designer  
  
1.  Em **Server Explorer**/**Database Explorer**, expanda a conexão ao banco de dados Northwind. Expanda o **procedimentos armazenados** pasta.  
  
     Se você tiver fechado o Object Relational Designer, você poderá reabri-lo clicando no arquivo dbml que você adicionou anteriormente.  
  
2.  Clique o **Sales by Year** procedimento armazenado e arraste-o para o painel à direita do designer. Clique o **dez produtos mais caros** procedimento armazenado arraste-o para o painel à direita do designer.  
  
3.  Salve suas alterações e feche o designer.  
  
4.  Salve seu projeto.  
  
### <a name="to-add-code-to-display-the-results-of-the-stored-procedures"></a>Para adicionar código para exibir os resultados dos procedimentos armazenados  
  
1.  Do **Toolbox**, arraste um <xref:System.Windows.Forms.DataGridView>controle para o Windows Form padrão para seu projeto, Form1.</xref:System.Windows.Forms.DataGridView>  
  
2.  Clique duas vezes em Form1 para adicionar código ao seu `Load` eventos.  
  
3.  Quando você adicionou procedimentos armazenados ao / R Designer, o designer adicionará um <xref:System.Data.Linq.DataContext>objeto para o seu projeto.</xref:System.Data.Linq.DataContext> Este objeto contém o código que você deve ter para acessar esses procedimentos. O <xref:System.Data.Linq.DataContext>objeto para o projeto é nomeado com base no nome do arquivo. dbml.</xref:System.Data.Linq.DataContext> Para este projeto, o <xref:System.Data.Linq.DataContext>objeto é denominado `northwindDataContext`.</xref:System.Data.Linq.DataContext>  
  
     Você pode criar uma instância do <xref:System.Data.Linq.DataContext>em seu código e chamar os métodos de procedimento armazenado especificado por Object Relational Designer.</xref:System.Data.Linq.DataContext> Ligar para o <xref:System.Windows.Forms.DataGridView>do objeto, talvez você precise forçar a consulta seja executada imediatamente chamando o <xref:System.Linq.Enumerable.ToList%2A>método nos resultados do procedimento armazenado.</xref:System.Linq.Enumerable.ToList%2A> </xref:System.Windows.Forms.DataGridView>  
  
     Adicione o seguinte código para o `Load` eventos para chamar um dos procedimentos armazenados expostos como métodos para o contexto de dados.  
  
     [!code-vb[VbLINQtoSQLHowTos n º&1;](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-call-a-stored-procedure-by-using-linq_1.vb)]  
    [!code-vb[VbLINQtoSQLHowTos n º&2;](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-call-a-stored-procedure-by-using-linq_2.vb)]  
  
4.  Pressione F5 para executar seu projeto e exibir os resultados.  
  
## <a name="see-also"></a>Consulte também  
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)   
 [Consultas](../../../../visual-basic/language-reference/queries/queries.md)   
 [LINQ to SQL](https://msdn.microsoft.com/library/bb386976)   
 [Métodos de DataContext (Object Relational Designer)](https://docs.microsoft.com/visualstudio/data-tools/datacontext-methods-o-r-designer)   
 [Como: atribuir procedimentos armazenados para executar atualizações, inserções e exclusões (Object Relational Designer)](http://msdn.microsoft.com/library/e88224ab-ff61-4a3a-b6b8-6f3694546cac)

