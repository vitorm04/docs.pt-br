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
ms.openlocfilehash: ef5f218cdcc7275f616486110825ad0b9df11cc3
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112356"
---
# <a name="how-to-find-the-minimum-or-maximum-value-in-a-query-result-by-using-linq-visual-basic"></a>Como localizar o valor mínimo ou máximo em um resultado de consulta usando LINQ (Visual Basic)
A Consulta Integrada ao Idioma (LINQ) facilita o acesso às informações do banco de dados e a execução de consultas.  
  
 O exemplo a seguir mostra como criar um novo aplicativo que executa consultas em um banco de dados do SQL Server. A amostra determina os valores mínimos e `Aggregate` `Group By` máximos para os resultados usando as cláusulas. Para obter mais informações, consulte [Cláusula Agregada](../../../../visual-basic/language-reference/queries/aggregate-clause.md) e [Grupo por Cláusula](../../../../visual-basic/language-reference/queries/group-by-clause.md).  
  
 Os exemplos neste tópico usam o banco de dados de amostras northwind. Caso não tenha esse banco de dados no seu computador de desenvolvimento, você poderá baixá-lo no Centro de Download da Microsoft. Para obter instruções, consulte [Baixar bancos de dados de amostras](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="create-a-connection-to-a-database"></a>Crie uma conexão com um banco de dados  
  
1. No Visual Studio, abra **o Server Explorer**/**Database Explorer** clicando no Server **Explorer**/**Database Explorer** no menu **Exibir.**  
  
2. Clique com o botão direito do **mouse conexões de dados** no Server **Explorer**/**Database Explorer Explorer** e clique em **Adicionar conexão**.  
  
3. Especifique uma conexão válida com o banco de dados de amostras do Northwind.  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a>Para adicionar um projeto que contém um arquivo LINQ ao SQL  
  
1. No Visual Studio, no menu **Arquivo,** aponte para **Novo** e clique em **Projeto**. Selecione visual basic **windows forms application** como o tipo de projeto.  
  
2. No menu **Projeto** , clique em **Adicionar Novo Item**. Selecione o modelo de item **LINQ para SQL Classes.**  
  
3. Nomeie o arquivo `northwind.dbml`. Clique em **Adicionar**. O Object Relational Designer (O/R Designer) é aberto para o arquivo northwind.dbml.  
  
## <a name="add-tables-to-query-to-the-or-designer"></a>Adicionar tabelas à consulta ao Designer O/R  
  
1. No **Server Explorer**/**Database Explorer,** expanda a conexão para o banco de dados Northwind. Expanda a pasta **Tabelas** .  
  
     Se você tiver fechado o O/R Designer, você pode reabri-lo clicando duas vezes no arquivo northwind.dbml que você adicionou anteriormente.  
  
2. Clique na tabela Clientes e arraste-a para o painel esquerdo do designer. Clique na tabela Pedidos e arraste-a para o painel esquerdo do designer.  
  
     O designer `Customer` cria `Order` novos e objetos para o seu projeto. Observe que o designer detecta automaticamente relações entre as tabelas e cria propriedades de criança para objetos relacionados. Por exemplo, o IntelliSense `Customer` mostrará `Orders` que o objeto possui uma propriedade para todos os pedidos relacionados a esse cliente.  
  
3. Guarde suas mudanças e feche o designer.  
  
4. Salve seu projeto.  
  
## <a name="add-code-to-query-the-database-and-display-the-results"></a>Adicionar código para consultar o banco de dados e exibir os resultados  
  
1. Na **caixa de ferramentas,** arraste um <xref:System.Windows.Forms.DataGridView> controle para o formulário padrão do Windows para o seu projeto, Form1.  
  
2. Clique duas vezes em Formulário1 `Load` para adicionar código ao evento do formulário.  
  
3. Quando você adicionou tabelas ao O/R <xref:System.Data.Linq.DataContext> Designer, o designer adicionou um objeto para o seu projeto. Este objeto contém o código que você deve ter para acessar essas tabelas, além de objetos individuais e coleções para cada tabela. O <xref:System.Data.Linq.DataContext> objeto para o seu projeto é nomeado com base no nome do seu arquivo .dbml. Para este projeto, <xref:System.Data.Linq.DataContext> o `northwindDataContext`objeto é chamado .  
  
     Você pode criar uma <xref:System.Data.Linq.DataContext> instância do em seu código e consultar as tabelas especificadas pelo Designer O/R.  
  
     Adicione o seguinte `Load` código ao evento. Este código consulta as tabelas que são expostas como propriedades do seu contexto de dados e determina os valores mínimos e máximos para os resultados. A amostra `Aggregate` usa a cláusula para consultar um `Group By` único resultado, e a cláusula para mostrar uma média de resultados agrupados.  
  
     [!code-vb[VbLINQToSQLHowTos#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form7.vb#14)]  
  
4. Pressione **F5** para executar seu projeto e visualizar os resultados.  
  
## <a name="see-also"></a>Confira também

- [Linq](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [Consultas](../../../../visual-basic/language-reference/queries/index.md)
- [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)
- [Métodos de DataContext (Designer O/R)](/visualstudio/data-tools/datacontext-methods-o-r-designer)
