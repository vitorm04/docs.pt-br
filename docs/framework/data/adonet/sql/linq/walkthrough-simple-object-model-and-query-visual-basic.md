---
title: 'Passo a passo: modelo e consulta de objeto simples (Visual Basic)'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: vb
ms.assetid: c878e457-f715-46e4-a136-ff14d6c86018
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: ed6436dcac1791d735132c295943519af36e307d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="walkthrough-simple-object-model-and-query-visual-basic"></a>Passo a passo: modelo e consulta de objeto simples (Visual Basic)
Este passo a passo fornece um cenário completo fundamental do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] com complexidades mínimas. Você criará uma classe de entidade que modela a tabela Customers no banco de dados de exemplo Northwind. Em seguida, você criará uma consulta simples para os clientes de lista que estão localizados em Londres.  
  
 Este passo a passo é orientado a código por design para ajudar a mostrar os conceitos do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. Normalmente, você usa o [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] para criar seu modelo de objeto.  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 Este passo a passo foi escrito usando as Configurações de Desenvolvimento do Visual Basic.  
  
## <a name="prerequisites"></a>Pré-requisitos  
  
-   Este passo a passo usa uma pasta dedicada ("c:\linqtest") para armazenar arquivos. Crie essa pasta antes de iniciar o passo a passo.  
  
-   Este passo a passo requer o banco de dados de exemplo Northwind. Se você não tiver esse banco de dados no seu computador de desenvolvimento, poderá baixá-lo no site de download da Microsoft. Para obter instruções, consulte [baixando bancos de dados de exemplo](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md). Depois de baixar o banco de dados, copie o arquivo para a pasta c:\linqtest.  
  
## <a name="overview"></a>Visão Geral  
 Este passo a passo consiste em seis tarefas principais:  
  
-   Criar uma solução [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] no [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)].  
  
-   Mapear uma classe para uma tabela do banco de dados.  
  
-   Designar propriedades na classe para representar colunas do banco de dados.  
  
-   Especificar a conexão ao banco de dados Northwind.  
  
-   Criar uma consulta simples para execução no banco de dados.  
  
-   Executar a consulta e observar os resultados.  
  
## <a name="creating-a-linq-to-sql-solution"></a>Criando uma solução LINQ to SQL  
 Nesta primeira tarefa, você cria uma solução do [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] que contém as referências necessárias para criar e executar um projeto do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
#### <a name="to-create-a-linq-to-sql-solution"></a>Para criar uma solução LINQ to SQL  
  
1.  No menu **Arquivo**, clique em **Novo Projeto**.  
  
2.  No **tipos de projeto** painel do **novo projeto** caixa de diálogo, clique em **Visual Basic**.  
  
3.  No painel **Modelos**, clique em **Aplicativo de Console**.  
  
4.  No **nome** , digite **LinqConsoleApp**.  
  
5.  Clique em **OK**.  
  
## <a name="adding-linq-references-and-directives"></a>Adicionando referências e diretivas LINQ  
 Este passo a passo usa assemblies que não podem ser instalados por padrão em seu projeto. Se `System.Data.Linq` não está listado como uma referência em seu projeto (clique **Mostrar todos os arquivos** na **Gerenciador de soluções** e expanda o **referências** nó), adicioná-lo, conforme explicado em as etapas a seguir.  
  
#### <a name="to-add-systemdatalinq"></a>Para adicionar System.Data.Linq  
  
1.  Em **Solution Explorer**, clique com botão direito **referências**e, em seguida, clique em **adicionar referência**.  
  
2.  No **adicionar referência** caixa de diálogo, clique em **.NET**, clique em assembly System.Data.Linq e, em seguida, clique em **Okey**.  
  
     O assembly é adicionado ao projeto.  
  
3.  Também no **adicionar referência** caixa de diálogo, clique em **.NET**, vá para e clique em System e, em seguida, clique em **Okey**.  
  
     Este assembly, que oferece suporte à caixa de mensagem no passo a passo, é adicionado ao projeto.  
  
4.  Adicione as seguintes diretivas acima de `Module1`:  
  
     [!code-vb[DLinqWalk1VB#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1VB/vb/Module1.vb#1)]  
  
## <a name="mapping-a-class-to-a-database-table"></a>Mapeando uma classe para uma tabela do banco de dados  
 Nesta etapa, você cria uma classe e a mapeia para uma tabela do banco de dados. Essa classe é chamado de um *classe da entidade*. Observe que o mapeamento é realizado simplesmente adicionando o atributo <xref:System.Data.Linq.Mapping.TableAttribute>. A propriedade <xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> especifica o nome da tabela no banco de dados.  
  
#### <a name="to-create-an-entity-class-and-map-it-to-a-database-table"></a>Para criar uma classe de entidade e mapeá-la para uma tabela do banco de dados.  
  
-   Digite ou cole o seguinte código no Module1.vb imediatamente acima de `Sub Main`:  
  
     [!code-vb[DLinqWalk1VB#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1VB/vb/Module1.vb#2)]  
  
## <a name="designating-properties-on-the-class-to-represent-database-columns"></a>Designando propriedades na classe para representar colunas do banco de dados  
 Nesta etapa, você realiza várias tarefas.  
  
-   Você usa o atributo <xref:System.Data.Linq.Mapping.ColumnAttribute> para designar as propriedades `CustomerID` e `City` na classe de entidade como representação de colunas na tabela do banco de dados.  
  
-   Você designa a propriedade `CustomerID` como a representação de uma coluna de chave primária no banco de dados.  
  
-   Você designa os campos `_CustomerID` e `_City` para armazenamento particular. O [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] pode então armazenar e recuperar valores diretamente, em vez de usar acessadores públicos, que podem incluir lógica de negócios.  
  
#### <a name="to-represent-characteristics-of-two-database-columns"></a>Para representar características de duas colunas do banco de dados  
  
-   Digite ou cole o seguinte código no Module1.vb imediatamente antes de `End Class`:  
  
     [!code-vb[DLinqWalk1VB#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1VB/vb/Module1.vb#3)]  
  
## <a name="specifying-the-connection-to-the-northwind-database"></a>Especificando a conexão ao banco de dados Northwind  
 Nesta etapa você usa um objeto <xref:System.Data.Linq.DataContext> para estabelecer uma conexão entre as estruturas de dados baseadas em código e o próprio banco de dados. O <xref:System.Data.Linq.DataContext> é o canal principal por meio do qual você recupera objetos do banco de dados e envia alterações.  
  
 Você também declara um `Table(Of Customer)` para atuar como a tabela lógica tipada para suas consultas na tabela Customers do banco de dados. Você criará e executará essas consultas em etapas posteriores.  
  
#### <a name="to-specify-the-database-connection"></a>Para especificar a conexão do banco de dados  
  
-   Digite ou cole o código a seguir no método `Sub Main`:  
  
     Observe que supõe-se que o arquivo `northwnd.mdf` está na pasta linqtest. Para obter mais informações, consulte a seção de pré-requisitos anteriormente neste passo a passo.  
  
     [!code-vb[DLinqWalk1VB#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1VB/vb/Module1.vb#4)]  
  
## <a name="creating-a-simple-query"></a>Criando uma consulta simples  
 Nesta etapa, você cria uma consulta para localizar quais clientes da tabela Customers do banco de dados estão localizados em Londres. O código da consulta nesta etapa apenas descreve a consulta. Não a executa. Essa abordagem é conhecida como *execução diferida*. Para obter mais informações, consulte [Introdução a Consultas de LINQ (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).  
  
 Você também gerará uma saída de log para mostrar os comandos SQL gerados pelo [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. Este recurso de log (que usa <xref:System.Data.Linq.DataContext.Log%2A>) é útil para depuração e para determinar se os comandos que estão sendo enviados ao banco de dados representam precisamente sua consulta.  
  
#### <a name="to-create-a-simple-query"></a>Para criar uma consulta simples  
  
-   Digite ou cole o código a seguir no método `Sub Main` depois da declaração `Table(Of Customer)`:  
  
     [!code-vb[DLinqWalk1AVB#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1AVB/vb/Module1.vb#5)]  
  
## <a name="executing-the-query"></a>Executando a consulta  
 Nesta etapa, você realmente executa a consulta. As expressões de consulta que você criou nas etapas anteriores não são avaliadas até que os resultados sejam necessários. Quando você começa a iteração `For Each`, um comando SQL é executado no banco de dados e os objetos são materializados.  
  
#### <a name="to-execute-the-query"></a>Para executar a consulta  
  
1.  Digite ou cole o seguinte código ao final do método `Sub Main` (após a descrição de consulta):  
  
     [!code-vb[DLinqWalk1AVB#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1AVB/vb/Module1.vb#6)]  
  
2.  Pressione F5 para depurar o aplicativo.  
  
    > [!NOTE]
    >  Se o aplicativo gera um erro de tempo de execução, consulte a seção de solução de problemas de [aprendendo com explicações passo a passo](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md).  
  
     A caixa de mensagem exibe uma lista de seis clientes. A janela Console exibe o código SQL gerado.  
  
3.  Clique em **Okey** para fechar a caixa de mensagem.  
  
     O aplicativo é fechado.  
  
4.  Sobre o **arquivo** menu, clique em **Salvar tudo**.  
  
     Você precisará deste aplicativo para continuar com o próximo passo a passo.  
  
## <a name="next-steps"></a>Próximas etapas  
 O [passo a passo: consultando em relações (Visual Basic)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-querying-across-relationships-visual-basic.md) tópico continua onde este passo a passo termina. Consulta entre relações passo a passo demonstra como [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] pode consultar tabelas, semelhante ao *junções* em um banco de dados relacional.  
  
 Se você desejar realizar o passo a passo Consultando através de relações, salve a solução do passo a passo que você acabou de concluir, que é um pré-requisito.  
  
## <a name="see-also"></a>Consulte também  
 [Aprendendo com explicações passo a passo](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
