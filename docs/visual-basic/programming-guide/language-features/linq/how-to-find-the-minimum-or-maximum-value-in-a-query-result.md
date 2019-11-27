---
title: Como localizar o valor mínimo ou máximo em um resultado de consulta usando LINQ
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
ms.openlocfilehash: bddb90baa0b01fd9d724583b472af9f9fa7569e5
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344975"
---
# <a name="how-to-find-the-minimum-or-maximum-value-in-a-query-result-by-using-linq-visual-basic"></a>Como localizar o valor mínimo ou máximo em um resultado de consulta usando LINQ (Visual Basic)
A consulta integrada à linguagem (LINQ) facilita o acesso a informações do banco de dados e a execução de consultas.  
  
 O exemplo a seguir mostra como criar um novo aplicativo que executa consultas em um banco de dados SQL Server. O exemplo determina os valores mínimo e máximo para os resultados usando as cláusulas `Aggregate` e `Group By`. Para obter mais informações, consulte [cláusula Aggregate](../../../../visual-basic/language-reference/queries/aggregate-clause.md) e [cláusula Group by](../../../../visual-basic/language-reference/queries/group-by-clause.md).  
  
 Os exemplos neste tópico usam o banco de dados de exemplo Northwind. Caso não tenha esse banco de dados no seu computador de desenvolvimento, você poderá baixá-lo no Centro de Download da Microsoft. Para obter instruções, consulte [baixar bancos de dados de exemplo](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a>Para criar uma conexão com um banco de dados  
  
1. No Visual Studio, abra **Gerenciador de Servidores**/**Gerenciador de Banco de Dados** clicando em **Gerenciador de servidores**/**Gerenciador de banco de dados** no menu **Exibir** .  
  
2. Clique com o botão direito do mouse em **conexões de dados** no **Gerenciador de servidores**/**Gerenciador de banco de dados** e clique em **Adicionar conexão**.  
  
3. Especifique uma conexão válida para o banco de dados de exemplo Northwind.  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a>Para adicionar um projeto que contém um arquivo de LINQ to SQL  
  
1. No Visual Studio, no menu **Arquivo**, aponte para **Novo** e clique em **Projeto**. Selecione Visual Basic **aplicativo Windows Forms** como o tipo de projeto.  
  
2. No menu **Projeto**, clique em **Adicionar Novo Item**. Selecione o modelo de item **classes de LINQ to SQL** .  
  
3. Dê o nome `northwind.dbml` para o arquivo. Clique em **Adicionar**. O Object Relational Designer (O/R Designer) é aberto para o arquivo Northwind. dbml.  
  
### <a name="to-add-tables-to-query-to-the-or-designer"></a>Para adicionar tabelas para consulta ao o/R Designer  
  
1. Em **Gerenciador de Servidores**/**Gerenciador de banco de dados**, expanda a conexão com o banco de dados Northwind. Expanda a pasta **tabelas** .  
  
     Se você fechou o o/R Designer, você pode reabri-lo clicando duas vezes no arquivo Northwind. dbml que você adicionou anteriormente.  
  
2. Clique na tabela clientes e arraste-a para o painel esquerdo do designer. Clique na tabela Orders e arraste-a para o painel esquerdo do designer.  
  
     O designer cria novos objetos `Customer` e `Order` para seu projeto. Observe que o designer detecta automaticamente as relações entre as tabelas e cria propriedades filhas para objetos relacionados. Por exemplo, o IntelliSense mostrará que o objeto `Customer` tem uma propriedade `Orders` para todos os pedidos relacionados a esse cliente.  
  
3. Salve as alterações e feche o designer.  
  
4. Salve seu projeto.  
  
### <a name="to-add-code-to-query-the-database-and-display-the-results"></a>Para adicionar código para consultar o banco de dados e exibir os resultados  
  
1. Na **caixa de ferramentas**, arraste um controle de <xref:System.Windows.Forms.DataGridView> para o formulário padrão do Windows para seu projeto, Form1.  
  
2. Clique duas vezes em Form1 para adicionar código ao evento `Load` do formulário.  
  
3. Quando você adicionou tabelas ao o/R Designer, o designer adicionou um objeto <xref:System.Data.Linq.DataContext> para o seu projeto. Esse objeto contém o código que você deve ter para acessar essas tabelas, além de objetos individuais e coleções para cada tabela. O objeto <xref:System.Data.Linq.DataContext> para seu projeto é nomeado com base no nome do seu arquivo. dbml. Para este projeto, o objeto <xref:System.Data.Linq.DataContext> é nomeado `northwindDataContext`.  
  
     Você pode criar uma instância do <xref:System.Data.Linq.DataContext> em seu código e consultar as tabelas especificadas pelo o/R Designer.  
  
     Adicione o código a seguir ao evento `Load`. Esse código consulta as tabelas que são expostas como propriedades de seu contexto de dados e determina os valores mínimo e máximo para os resultados. O exemplo usa a cláusula `Aggregate` para consultar um único resultado e a cláusula `Group By` para mostrar uma média para resultados agrupados.  
  
     [!code-vb[VbLINQToSQLHowTos#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form7.vb#14)]  
  
4. Pressione F5 para executar o projeto e exibir os resultados.  
  
## <a name="see-also"></a>Consulte também

- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [Consultas](../../../../visual-basic/language-reference/queries/index.md)
- [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)
- [Métodos DataContext (Designer Relacional de Objetos)](/visualstudio/data-tools/datacontext-methods-o-r-designer)
