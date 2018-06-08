---
title: Como localizar o valor mínimo ou máximo em um resultado de consulta usando LINQ (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- max operator [LINQ in Visual Basic]
- aggregate operator [LINQ in Visual Basic]
- aggregate queries
- minimum values [LINQ in Visual Basic]
- min operator [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], minimum and maximum values
- Max property
- maximum values [LINQ in Visual Basic]
- Aggregate clause [Visual Basic]
- queries [LINQ in Visual Basic], aggregate queries
- queries [LINQ in Visual Basic], how-to topics
ms.assetid: 238b763b-7dcd-4b14-8050-b65500a4f71c
ms.openlocfilehash: f1b997272bc65a3702353f1f7db02fa330a19c21
ms.sourcegitcommit: d955cb4c681d68cf301d410925d83f25172ece86
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/07/2018
ms.locfileid: "34826884"
---
# <a name="how-to-find-the-minimum-or-maximum-value-in-a-query-result-by-using-linq-visual-basic"></a>Como localizar o valor mínimo ou máximo em um resultado de consulta usando LINQ (Visual Basic)
Consulta integrada à linguagem (LINQ) facilita o acesso a informações de banco de dados e executar consultas.  
  
 O exemplo a seguir mostra como criar um novo aplicativo que executa consultas em um banco de dados do SQL Server. O exemplo determina os valores mínimos e máximo para os resultados usando o `Aggregate` e `Group By` cláusulas. Para obter mais informações, consulte [cláusula Aggregate](../../../../visual-basic/language-reference/queries/aggregate-clause.md) e [grupo pela cláusula](../../../../visual-basic/language-reference/queries/group-by-clause.md).  
  
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
  
     Adicione o seguinte código para o `Load` evento. Esse código consulta as tabelas que são expostas como propriedades de seu contexto de dados e determina os valores mínimos e máximo para os resultados. O exemplo utiliza `Aggregate` cláusula para consultar um único resultado e o `Group By` cláusula para mostrar uma média para resultados de agrupados.  
  
     [!code-vb[VbLINQToSQLHowTos#14](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-find-the-minimum-or-maximum-value-in-a-query-result_1.vb)]  
  
4.  Pressione F5 para executar seu projeto e exibir os resultados.  
  
## <a name="see-also"></a>Consulte também  
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [Consultas](../../../../visual-basic/language-reference/queries/queries.md)  
 [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)  
 [Métodos de DataContext (Object Relational Designer)](/visualstudio/data-tools/datacontext-methods-o-r-designer)
