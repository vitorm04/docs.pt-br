---
title: Como filtrar resultados de consulta usando LINQ (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- filtering [Visual Basic]
- filtering data [LINQ in Visual Basic]
- filtering [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], filtering results
- querying databases [LINQ]
- queries [LINQ in Visual Basic], how-to topics
- query samples [Visual Basic]
- filtering data [Visual Basic]
ms.assetid: ef103092-9bed-4134-97f4-2db696e83c12
ms.openlocfilehash: 8e051d583cdaeb04190e4499834a052fa41d1c48
ms.sourcegitcommit: d955cb4c681d68cf301d410925d83f25172ece86
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/07/2018
ms.locfileid: "34827203"
---
# <a name="how-to-filter-query-results-by-using-linq-visual-basic"></a>Como filtrar resultados de consulta usando LINQ (Visual Basic)
Consulta integrada à linguagem (LINQ) facilita o acesso a informações de banco de dados e executar consultas.  
  
 O exemplo a seguir mostra como criar um novo aplicativo que executa consultas em um banco de dados do SQL Server e filtra os resultados por um valor específico usando o `Where` cláusula. Para obter mais informações, consulte [cláusula Where](../../../../visual-basic/language-reference/queries/where-clause.md).  
  
 Os exemplos neste tópico usam o banco de dados de exemplo Northwind. Se você não tiver esse banco de dados no computador de desenvolvimento, você pode baixá-lo do Microsoft Download Center. Para obter instruções, consulte [baixando bancos de dados de exemplo](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a>Para criar uma conexão para um banco de dados  
  
1.  No Visual Studio, abra **Server Explorer**/**Pesquisador de objetos de banco de dados** clicando **Server Explorer**/**banco de dados Gerenciador de** no **exibição** menu.  
  
2.  Clique com botão direito **conexões de dados** na **Server Explorer**/**Pesquisador de objetos de banco de dados** e, em seguida, clique em **Adicionar Conexão**.  
  
3.  Especifique uma conexão válida para o banco de dados de exemplo Northwind.  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a>Para adicionar um projeto que contém um arquivo LINQ to SQL  
  
1.  No Visual Studio, no menu **Arquivo**, aponte para **Novo** e clique em **Projeto**. Selecione Visual Basic **aplicativo do Windows Forms** como o tipo de projeto.  
  
2.  No menu **Projeto**, clique em **Adicionar Novo Item**. Selecione o **Classes LINQ to SQL** modelo de item.  
  
3.  Dê o nome `northwind.dbml` para o arquivo. Clique em **Adicionar**. O Object Relational Designer (O/R Designer) é aberto para o arquivo dbml.  
  
### <a name="to-add-tables-to-query-to-the-or-designer"></a>Para adicionar tabelas de consulta para o O/R Designer  
  
1.  Em **Server Explorer**/**Pesquisador de objetos de banco de dados**, expanda a conexão ao banco de dados Northwind. Expanda o **tabelas** pasta.  
  
     Se você fechou o Object Relational Designer, você poderá reabri-lo clicando no arquivo dbml que você adicionou anteriormente.  
  
2.  Clique na tabela clientes e arraste-o no painel esquerdo do designer. Clique na tabela Orders e arraste-o no painel esquerdo do designer.  
  
     O designer cria novos `Customer` e `Order` objetos para o seu projeto. Observe que o designer automaticamente detecta as relações entre as tabelas e cria propriedades filhas para objetos relacionados. Por exemplo, o IntelliSense mostrará que o `Customer` objeto tem um `Orders` propriedade para todos os pedidos relacionados a esse cliente.  
  
3.  Salve suas alterações e fechar o designer.  
  
4.  Salve seu projeto.  
  
### <a name="to-add-code-to-query-the-database-and-display-the-results"></a>Para adicionar código para consultar o banco de dados e exibir os resultados  
  
1.  Do **caixa de ferramentas**, arraste um <xref:System.Windows.Forms.DataGridView> controle para o Windows Form padrão para seu projeto, Form1.  
  
2.  Clique duas vezes em Form1 para adicionar código para o `Load` evento do formulário.  
  
3.  Quando você adicionar tabelas ao / R Designer, o designer adicionará um <xref:System.Data.Linq.DataContext> objeto para o seu projeto. Este objeto contém o código que você deve ter para acessar essas tabelas, além de objetos individuais e coleções para cada tabela. O <xref:System.Data.Linq.DataContext> objeto para seu projeto é nomeado com base no nome do seu arquivo dbml. Para este projeto, o <xref:System.Data.Linq.DataContext> objeto é nomeado `northwindDataContext`.  
  
     Você pode criar uma instância do <xref:System.Data.Linq.DataContext> no seu código e consultar as tabelas especificadas pelo / R Designer.  
  
     Adicione o seguinte código para o `Load` evento para consultar as tabelas que são expostas como propriedades de seu contexto de dados. A consulta filtra os resultados e retorna somente os clientes que estão localizados em `London`.  
  
     [!code-vb[VbLINQToSQLHowTos#11](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-filter-query-results-by-using-linq_1.vb)]  
  
4.  Pressione F5 para executar seu projeto e exibir os resultados.  
  
5.  A seguir estão alguns outros filtros que você pode tentar.  
  
     [!code-vb[VbLINQToSQLHowTos#12](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-filter-query-results-by-using-linq_2.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [Consultas](../../../../visual-basic/language-reference/queries/queries.md)  
 [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)  
 [Métodos de DataContext (Object Relational Designer)](/visualstudio/data-tools/datacontext-methods-o-r-designer)
