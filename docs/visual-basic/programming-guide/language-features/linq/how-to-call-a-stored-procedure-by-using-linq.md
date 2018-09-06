---
title: Como chamar um procedimento armazenado usando LINQ (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], stored procedure calls
- stored procedures sample [Visual Basic]
- stored procedures [LINQ to SQL]
- queries [LINQ in Visual Basic], how-to topics
ms.assetid: 6436d384-d1e0-40aa-8afd-451007477260
ms.openlocfilehash: 50a4dff90dc1ce02869978f1da147e530cefc3e1
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43779819"
---
# <a name="how-to-call-a-stored-procedure-by-using-linq-visual-basic"></a>Como chamar um procedimento armazenado usando LINQ (Visual Basic)
Consulta integrada à linguagem (LINQ) facilita o acesso a informações de banco de dados, incluindo o banco de dados objetos como procedimentos armazenados.  
  
 O exemplo a seguir mostra como criar um aplicativo que chama um procedimento armazenado em um banco de dados do SQL Server. O exemplo mostra como chamar dois diferentes procedimentos armazenados no banco de dados. Cada procedimento retorna os resultados de uma consulta. Um procedimento utiliza parâmetros de entrada e o outro procedimento não aceita parâmetros.  
  
 Os exemplos neste tópico usam o banco de dados de exemplo Northwind. Se você não tiver esse banco de dados no computador de desenvolvimento, você pode baixá-lo do Microsoft Download Center. Para obter instruções, consulte [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a>Para criar uma conexão para um banco de dados  
  
1.  No Visual Studio, abra **Gerenciador de servidores**/**Database Explorer** clicando **Server Explorer**/**banco de dados Explorer** sobre o **exibição** menu.  
  
2.  Clique com botão direito **conexões de dados** na **Gerenciador de servidores**/**Database Explorer** e, em seguida, clique em **Adicionar Conexão**.  
  
3.  Especifique uma conexão válida para o banco de dados de exemplo Northwind.  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a>Para adicionar um projeto que contém um arquivo LINQ to SQL  
  
1.  No Visual Studio, no menu **Arquivo**, aponte para **Novo** e clique em **Projeto**. Selecione Visual Basic **aplicativo do Windows Forms** como o tipo de projeto.  
  
2.  No menu **Projeto**, clique em **Adicionar Novo Item**. Selecione o **Classes LINQ to SQL** modelo de item.  
  
3.  Dê o nome `northwind.dbml` para o arquivo. Clique em **Adicionar**. O Object Relational Designer (O/R Designer) é aberto para o arquivo Northwind dbml.  
  
### <a name="to-add-stored-procedures-to-the-or-designer"></a>Para adicionar os procedimentos armazenados para o O/R Designer  
  
1.  Na **Gerenciador de servidores**/**Gerenciador de banco de dados**, expanda a conexão ao banco de dados Northwind. Expanda o **procedimentos armazenados** pasta.  
  
     Se você tiver fechado o O/R Designer, você poderá reabri-lo clicando duas vezes no arquivo dbml que você adicionou anteriormente.  
  
2.  Clique o **vendas por ano** procedimento armazenado e arraste-o para o painel à direita do designer. Clique o **dez produtos mais caros** procedimento armazenado arraste-o para o painel à direita do designer.  
  
3.  Salve suas alterações e feche o designer.  
  
4.  Salve seu projeto.  
  
### <a name="to-add-code-to-display-the-results-of-the-stored-procedures"></a>Para adicionar código para exibir os resultados dos procedimentos armazenados  
  
1.  Dos **caixa de ferramentas**, arraste um <xref:System.Windows.Forms.DataGridView> controle para o formulário do Windows padrão para seu projeto, Form1.  
  
2.  Clique duas vezes em Form1 para adicionar código ao seu `Load` eventos.  
  
3.  Quando você adicionou os procedimentos armazenados para o Designer relacional de objetos, o designer adicionará um <xref:System.Data.Linq.DataContext> objeto para o seu projeto. Este objeto contém o código que você deve ter para acessar esses procedimentos. O <xref:System.Data.Linq.DataContext> objeto para o projeto é nomeado com base no nome do arquivo. dbml. Para este projeto, o <xref:System.Data.Linq.DataContext> objeto é nomeado `northwindDataContext`.  
  
     Você pode criar uma instância da <xref:System.Data.Linq.DataContext> no seu código e chamar os métodos de procedimento armazenado especificado pelo Designer relacional de objetos. Para associar à <xref:System.Windows.Forms.DataGridView> do objeto, você pode ter que forçar a consulta seja executada imediatamente, chamando o <xref:System.Linq.Enumerable.ToList%2A> método nos resultados do procedimento armazenado.  
  
     Adicione o seguinte código para o `Load` eventos para chamar um dos procedimentos armazenados expostos como métodos para o contexto de dados.  
  
     [!code-vb[VbLINQtoSQLHowTos#1](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-call-a-stored-procedure-by-using-linq_1.vb)]  
    [!code-vb[VbLINQtoSQLHowTos#2](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-call-a-stored-procedure-by-using-linq_2.vb)]  
  
4.  Pressione F5 para executar seu projeto e exibir os resultados.  
  
## <a name="see-also"></a>Consulte também  
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [Consultas](../../../../visual-basic/language-reference/queries/index.md)  
 [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)  
 [Métodos DataContext (Designer Relacional de Objetos)](/visualstudio/data-tools/datacontext-methods-o-r-designer)  
 [Como atribuir procedimentos armazenados para executar atualizações, inserções e exclusões (Designer Relacional de Objetos)](https://msdn.microsoft.com/library/e88224ab-ff61-4a3a-b6b8-6f3694546cac)
