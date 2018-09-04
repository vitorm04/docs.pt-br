---
title: Isolamento de instantâneo no SQL Server
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 43ae5dd3-50f5-43a8-8d01-e37a61664176
ms.openlocfilehash: 52c5dba1a21b0e8d8e5af1dc159941e5f4b4aa5f
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43562764"
---
# <a name="snapshot-isolation-in-sql-server"></a>Isolamento de instantâneo no SQL Server
O isolamento de instantâneo melhora a simultaneidade para aplicativos de OLTP.  
  
## <a name="understanding-snapshot-isolation-and-row-versioning"></a>Entendendo o isolamento de instantâneo e o controle de versão de linha  
 Depois que o isolamento de instantâneo é habilitado, as versões de linha atualizada para cada transação são mantidas no **tempdb**. Um número de sequência exclusivo de transação identifica cada transação, e esses números exclusivos são gravados para cada versão de linha. A transação funciona com as versões de linha mais recentes que têm um número de sequência antes do número de sequência da transação. Versões de linha mais recentes criadas após a transação ter iniciado são ignoradas pela transação.  
  
 O termo “instantâneo” reflete o fato de que todas as consultas na transação enxergam a mesma versão, ou o instantâneo, do banco de dados, com base no estado do banco de dados nesse ponto no tempo quando a transação começa. Nenhum bloqueio é adquirido nas linhas de dados subjacentes ou páginas de dados em uma transação de instantâneo, o que permite que outras transações sejam executadas sem serem bloqueadas por uma transação anterior não concluída. As transações que modificam dados não bloqueiam as transações que leem dados, e as transações que leem dados não bloqueiam as transações que gravam dados, como normalmente fariam no nível de isolamento READ COMMITTED padrão no SQL Server. Este comportamento de não bloqueio também reduz significativamente a probabilidade de deadlocks para transações complexas.  
  
 O isolamento de instantâneo usa um modelo otimista de simultaneidade. Se uma transação de instantâneo tentar confirmar as alterações nos dados que foram alterados desde que a transação iniciou, a transação será revertida e um erro será gerado. Você pode evitar isso usando dicas de UPDLOCK para instruções SELECT que acessam os dados a serem alterados. Consulte "Dicas de bloqueio" nos Manuais Online do SQL Server para obter mais informações.  
  
 O isolamento de instantâneo deve ser habilitado configurando-se a opção do banco de dados ALLOW_SNAPSHOT_ISOLATION ON antes de ser usada nas transações. Isso ativa o mecanismo para armazenar versões de linha no banco de dados temporário (**tempdb**). Você deve habilitar o isolamento de instantâneo em cada banco de dados que o usa com a instrução Transact-SQL ALTER DATABASE. Quanto a isso, o isolamento de instantâneo difere dos níveis de isolamento tradicionais de READ COMMITTED, REPEATABLE READ, SERIALIZABLE e READ UNCOMMITTED, que não exigem nenhuma configuração. As instruções a seguir ativam o isolamento de instantâneo e substituem o comportamento padrão de READ COMMITTED por SNAPSHOT:  
  
```  
ALTER DATABASE MyDatabase  
SET ALLOW_SNAPSHOT_ISOLATION ON  
  
ALTER DATABASE MyDatabase  
SET READ_COMMITTED_SNAPSHOT ON  
```  
  
 Definir a opção READ_COMMITTED_SNAPSHOT ON permite acessar as linhas com versão no nível de isolamento padrão READ COMMITTED. Se a opção READ_COMMITTED_SNAPSHOT estiver definida como OFF, você deverá definir explicitamente o nível de isolamento de instantâneo para cada sessão para acessar as linhas com versão.  
  
## <a name="managing-concurrency-with-isolation-levels"></a>Gerenciando simultaneidade com níveis de isolamento  
 O nível de isolamento no qual uma instrução Transact-SQL é executada determina o comportamento de bloqueio e controle de versão de linha. Um nível de isolamento tem escopo em toda a conexão, e assim que está definido para uma conexão com a instrução SET TRANSACTION ISOLATION LEVEL, permanece efetivo até que a conexão seja fechada ou outro nível de isolamento seja definido. Quando uma conexão é fechada e retornada para o pool, o nível de isolamento da última instrução SET TRANSACTION ISOLATION LEVEL é mantido. As conexões subsequentes que reutilizam uma conexão agrupada usam o nível de isolamento que estava em vigor no momento em que a conexão foi agrupada.  
  
 As consultas individuais emitidas dentro de uma conexão podem conter dicas de bloqueio que modificam o isolamento para uma única instrução ou transação, mas não afetam o nível de isolamento da conexão. Os níveis de isolamento ou dicas de bloqueio definidos em procedimentos armazenados ou funções não alteram o nível de isolamento de conexão que os chama e ficam em vigor somente para a duração do procedimento armazenado ou chamada de função.  
  
 Quatro níveis de isolamento definidos no padrão SQL-92 tinham suporte em versões anteriores do SQL Server:  
  
-   READ UNCOMMITTED é o nível de isolamento menos restritivo, porque ignora os bloqueios colocados por outras transações. As transações que são executadas com READ UNCOMMITTED podem ler os valores de dados modificados que ainda não foram confirmados por outras transações; eles são chamados de leituras “sujas”.  
  
-   READ COMMITTED é o nível de isolamento padrão para o SQL Server. Ele impede as leitura sujas especificando que as instruções não podem ler os valores de dados que foram modificados, mas ainda não foram confirmados por outras transações. Outras transações ainda podem modificar, inserir ou excluir dados entre execuções de instruções individuais dentro da transação atual, resultando em leituras não repetíveis, ou dados “fantasma”.  
  
-   REPEATABLE READ é um nível de isolamento mais restritivo do que READ COMMITTED. Ele abrange READ COMMITTED e especifica adicionalmente que nenhuma outra transação pode modificar ou excluir dados que foram lidos pela transação atual até a transação atual ser confirmada. A simultaneidade é menor do que para READ COMMITTED porque os bloqueios compartilhados em dados lidos são mantidos para a duração da transação em vez de serem lançados no final da cada instrução.  
  
-   SERIALIZABLE é o nível de isolamento mais restritivo, porque bloqueia intervalos inteiros de chaves e mantém os bloqueios até que a transação seja concluída. Ele abrange REPEATABLE READ e adiciona a restrição que outras transações não podem inserir novas linhas em intervalos que foram lidos pela transação até que a transação seja concluída.  
  
 Para obter mais informações, consulte “Níveis de isolamento” nos Manuais Online do SQL Server.  
  
### <a name="snapshot-isolation-level-extensions"></a>Extensões de nível de isolamento de instantâneo  
 O SQL Server introduziu extensões nos níveis de isolamento SQL-92 com a introdução do nível de isolamento do SNAPSHOT e uma implementação adicional de READ COMMITTED. O nível de isolamento READ_COMMITTED_SNAPSHOT pode substituir de modo transparente READ COMMITTED para todas as transações.  
  
-   O isolamento de SNAPSHOT especifica que os dados lidos dentro de uma transação nunca refletirá as alterações feitas por outras transações simultâneas. A transação usa as versões da linha de dados que existem quando a transação começa. Nenhum bloqueio é colocado nos dados quando são lidos. Portanto, as transações de SNAPSHOT não bloqueiam outras transações de gravar dados. As transações que gravam dados não bloqueiam as transações de instantâneo de ler dados. Você precisa habilitar o isolamento de instantâneo configurando a opção do banco de dados ALLOW_SNAPSHOT_ISOLATION para usá-lo.  
  
-   A opção de banco de dados READ_COMMITTED_SNAPSHOT determina o comportamento do nível de isolamento READ COMMITTED padrão quando o isolamento de instantâneo é habilitado em um banco de dados. Se você não especificar explicitamente READ_COMMITTED_SNAPSHOT ON, READ COMMITTED será aplicado a todas as transações implícitas. Isso gerará o mesmo comportamento que configurar READ_COMMITTED_SNAPSHOT OFF (o padrão). Quando READ_COMMITTED_SNAPSHOT OFF está em vigor, o mecanismo de banco de dados usa bloqueios compartilhados para impor o nível de isolamento padrão. Se você definir a opção de banco de dados READ_COMMITTED_SNAPSHOT como ON, o mecanismo de banco de dados usará o controle de versão de linhas e o isolamento de instantâneo como o padrão, em vez de usar bloqueios para proteger os dados.  
  
## <a name="how-snapshot-isolation-and-row-versioning-work"></a>Como funcionam o isolamento de instantâneo e o controle de versão de linha  
 Quando o nível de isolamento de instantâneo está habilitado, sempre que uma linha é atualizada, o mecanismo de banco de dados do SQL Server armazena uma cópia da linha original em **tempdb**e adiciona um número de sequência de transação à linha. Veja a seguir a sequência de eventos que ocorre:  
  
-   Uma nova transação é iniciada, e é atribuído um número de sequência de transação.  
  
-   O mecanismo de banco de dados lê uma linha dentro da transação e recupera a versão de linha de **tempdb** cujo número de sequência está próximo e menor do que o número de sequência da transação.  
  
-   O Mecanismo de Banco de Dados verifica se o número de sequência de transação não está na lista de números de sequência de transações não confirmadas como ativas quando a transação de instantâneo iniciou.  
  
-   A transação lê a versão da linha de **tempdb** que era atual a partir do início da transação. Ela não verá as novas linhas inseridas após a transação ter sido iniciada porque os valores do número de sequência serão superiores ao valor do número de sequência da transação.  
  
-   A transação atual verá linhas que foram excluídas depois que a transação iniciou, porque haverá uma versão de linha na **tempdb** com um valor de número de sequência mais baixo.  
  
 O efeito líquido do isolamento de instantâneo é que a transação vê todos os dados como existiam no início de transação, sem honrar ou colocar os bloqueios nas tabelas subjacentes. Isso pode resultar em melhorias de desempenho em situações onde há conflito.  
  
 Uma transação de instantâneo sempre usa o controle de simultaneidade otimista, mantendo todos os bloqueios que impedem que outras transações atualizem as linhas. Se uma transação de instantâneo tentar confirmar uma atualização em uma linha que foi alterada depois que a transação iniciou, a transação será revertida e um erro será gerado.  
  
## <a name="working-with-snapshot-isolation-in-adonet"></a>Trabalhando com isolamento de instantâneo no ADO.NET  
 O isolamento de instantâneo tem suporte no ADO.NET pela classe <xref:System.Data.SqlClient.SqlTransaction>. Se um banco de dados tiver sido habilitado para isolamento de instantâneo, mas não está configurado para READ_COMMITTED_SNAPSHOT ON, você deve iniciar um <xref:System.Data.SqlClient.SqlTransaction> usando o **IsolationLevel** valor de enumeração ao chamar o <xref:System.Data.SqlClient.SqlConnection.BeginTransaction%2A> método. Este fragmento de código presume que a conexão seja um objeto <xref:System.Data.SqlClient.SqlConnection> aberto.  
  
```vb  
Dim sqlTran As SqlTransaction = _  
  connection.BeginTransaction(IsolationLevel.Snapshot)  
```  
  
```csharp  
SqlTransaction sqlTran =   
  connection.BeginTransaction(IsolationLevel.Snapshot);  
```  
  
### <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra como os diferentes níveis de isolamento se comportam ao tentar acessar dados bloqueados e não se destina a ser usado no código de produção.  
  
 O código conecta-se para o **AdventureWorks** de exemplo do banco de dados no SQL Server e cria uma tabela denominada **TestSnapshot** e insere uma linha de dados. O código usa a instrução ALTER DATABASE Transact-SQL para ativar o isolamento de instantâneo para o banco de dados, mas não define a opção READ_COMMITTED_SNAPSHOT, deixando o comportamento padrão de nível de isolamento READ COMMITTED em vigor. O código, em seguida, executa as seguintes ações:  
  
-   Ele inicia, mas não for conclui o sqlTransaction1, que usa o nível de isolamento SERIALIZABLE para iniciar uma transação de atualização. Isso tem o efeito de bloquear a tabela.  
  
-   Abre uma segunda conexão e inicia uma segunda transação usando o nível de isolamento SNAPSHOT para ler os dados do **TestSnapshot** tabela. Como o isolamento de instantâneo está habilitado, esta transação pode ler os dados que existiam antes de sqlTransaction1 iniciar.  
  
-   Abre uma terceira conexão e inicia uma transação usando o nível de isolamento READ COMMITTED para tentar ler os dados na tabela. Nesse caso, o código não pode ler os dados porque não pode ler depois que os bloqueios são colocados na tabela na primeira transação e o tempo é esgotado. O mesmo resultado ocorreria se os níveis de isolamento REPEATABLE READ e SERIALIZABLE tivessem sido usados, porque esses níveis de isolamento também não podem ler depois que os bloqueios são colocados na primeira transação.  
  
-   Ele abre uma quarta conexão e inicia uma transação usando o nível de isolamento READ UNCOMMITTED, que executa uma leitura suja do valor não confirmado em sqlTransaction1. Esse valor poderá nunca realmente existir no banco de dados se a primeira transação não for confirmada.  
  
-   Ele reverte a transação primeiro e limpa excluindo a **TestSnapshot** tabela e desativando isolamento de instantâneo para o **AdventureWorks** banco de dados.  
  
> [!NOTE]
>  Os exemplos a seguir usam a mesma cadeia de conexão com o pool de conexões desativado. Se uma conexão estiver agrupada, redefinir seu nível de isolamento não redefine o nível de isolamento no servidor. Como resultado, conexões subsequentes que usam a mesma conexão interna agrupado iniciam com os níveis de isolamento definidos para a conexão agrupada. Uma alternativa para desativar o pool de conexões é definir explicitamente o nível de isolamento para cada conexão.  
  
 [!code-csharp[DataWorks SnapshotIsolation.Demo#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SnapshotIsolation.Demo/CS/source.cs#1)]
 [!code-vb[DataWorks SnapshotIsolation.Demo#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SnapshotIsolation.Demo/VB/source.vb#1)]  
  
### <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra o comportamento do isolamento de instantâneo quando os dados estão sendo modificados. O código executa as seguintes ações:  
  
-   Conecta-se ao **AdventureWorks** de exemplo do banco de dados e habilita o isolamento de instantâneo.  
  
-   Cria uma tabela denominada **TestSnapshotUpdate** e insere três linhas de dados de exemplo.  
  
-   Inicia, mas não conclui, sqlTransaction1 usando o isolamento de SNAPSHOT. Três linhas de dados são selecionadas na transação.  
  
-   Cria um segundo **SqlConnection** à **AdventureWorks** e cria uma segunda transação usando o nível de isolamento READ COMMITTED que atualiza um valor em uma das linhas selecionadas em sqlTransaction1.  
  
-   Confirma sqlTransaction2.  
  
-   Retorna para sqlTransaction1 e tenta atualizar a mesma linha que sqlTransaction1 já confirmou. O erro 3960 é gerado e sqlTransaction1 é revertido automaticamente. O **SqlException. Number** e **SqlException. Message** são exibidos na janela do Console.  
  
-   Executa o código de limpeza para desativar o isolamento de instantâneo no **AdventureWorks** e excluir os **TestSnapshotUpdate** tabela.  
  
 [!code-csharp[DataWorks SnapshotIsolation.DemoUpdate#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SnapshotIsolation.DemoUpdate/CS/source.cs#1)]
 [!code-vb[DataWorks SnapshotIsolation.DemoUpdate#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SnapshotIsolation.DemoUpdate/VB/source.vb#1)]  
  
### <a name="using-lock-hints-with-snapshot-isolation"></a>Usando dicas de bloqueio com isolamento de instantâneo  
 No exemplo anterior, a primeira transação seleciona dados, e uma segunda transação atualiza os dados antes que a primeira transação possa ser concluída, causando um conflito de atualização quando a primeira transação tentar atualizar a mesma linha. Você pode reduzir a possibilidade de conflitos de atualização em transações de instantâneo de execução longa fornecendo dicas de bloqueio no início de transação. A seguinte instrução SELECT usa a dica UPDLOCK para bloquear as linhas selecionadas:  
  
```  
SELECT * FROM TestSnapshotUpdate WITH (UPDLOCK)   
  WHERE PriKey BETWEEN 1 AND 3  
```  
  
 Usar a dica de bloqueio UPDLOCK bloqueia todas as linhas que tentam atualizar as linhas antes que a primeira transação seja concluída. Isso garante que as linhas selecionadas não tenham conflitos quando forem atualizadas posteriormente na transação. Consulte “Dicas de bloqueio” nos Manuais Online do SQL Server.  
  
 Se seu aplicativo tiver muitos conflitos, o isolamento de instantâneo poderá não ser a melhor opção. As dicas deverão ser usadas somente quando for realmente necessário. Seu aplicativo não deverá ser criado de modo que dependa constantemente de dicas de bloqueio para sua operação.  
  
## <a name="see-also"></a>Consulte também  
 [SQL Server and ADO.NET](../../../../../docs/framework/data/adonet/sql/index.md) (SQL Server e ADO.NET)  
 [ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
