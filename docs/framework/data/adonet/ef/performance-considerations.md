---
title: Considerações sobre desempenho (Entity Framework)
ms.date: 03/30/2017
ms.assetid: 61913f3b-4f42-4d9b-810f-2a13c2388a4a
ms.openlocfilehash: 581f3bc81c689909164ed3fec246371cf83245ff
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32766807"
---
# <a name="performance-considerations-entity-framework"></a>Considerações sobre desempenho (Entity Framework)
Este tópico descreve as características de desempenho do ADO.NET Entity Framework e fornece algumas considerações para ajudar a melhorar o desempenho de aplicativos do Entity Framework.  
  
## <a name="stages-of-query-execution"></a>Fases da execução da consulta  
 Para compreender melhor o desempenho de consultas no Entity Framework, é útil entender as operações que ocorrem quando uma consulta é executada em um modelo conceitual e retorna dados como objetos. A tabela a seguir descreve esta série de operações.  
  
|Operação|Custo relativo|Frequência|Comentários|  
|---------------|-------------------|---------------|--------------|  
|Carregando metadados|Moderado|Uma vez em cada domínio de aplicativo.|Os metadados de modelo e de mapeamento usados pelo Entity Framework são carregados em uma <xref:System.Data.Metadata.Edm.MetadataWorkspace>. Esses metadados são armazenados em cache globalmente e estão disponíveis para outras instâncias do <xref:System.Data.Objects.ObjectContext> no mesmo domínio do aplicativo.|  
|Abrindo a conexão de banco de dados|Moderada<sup>1</sup>|Conforme o necessário.|Como uma conexão aberta ao banco de dados consome um recurso valioso, o [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] abre e fecha a conexão de banco de dados conforme necessário. Você também pode explicitamente abrir a conexão. Para obter mais informações, consulte [Gerenciando conexões e transações](http://msdn.microsoft.com/library/b6659d2a-9a45-4e98-acaa-d7a8029e5b99).|  
|Gerando exibições|Alta|Uma vez em cada domínio de aplicativo. (Pode ser pré-gerado.)|Antes que o Entity Framework possa executar uma consulta em um modelo conceitual ou salvar alterações na fonte de dados, ele deverá gerar um conjunto de exibições de consultas locais para acessar o banco de dados. Devido a custo alto de gerar essas exibições, você poderá pré-gerar as exibições e adicioná-las ao projeto em tempo de design. Para obter mais informações, consulte [como: Pre-Generate exibições para melhorar o desempenho da consulta](http://msdn.microsoft.com/library/b18a9d16-e10b-4043-ba91-b632f85a2579).|  
|Preparando a consulta|Moderada<sup>2</sup>|Uma vez para cada consulta exclusiva.|Inclui o custo para compor o comando de consulta, gerar uma árvore de comando com base em metadados de modelo e mapeamento, e definir o formato dos dados retornados. Como agora os comandos de consulta Entity SQL e as consultas LINQ são armazenados em cache, as execuções posteriores da mesma consulta são realizadas em menos tempo. Você ainda pode usar consultas LINQ para reduzir esse custo em execuções posteriores e consultas compiladas podem ser mais eficientes que consultas LINQ que são automaticamente armazenadas em cache. Para obter mais informações, consulte [consultas compiladas (LINQ to Entities)](../../../../../docs/framework/data/adonet/ef/language-reference/compiled-queries-linq-to-entities.md). Para obter informações gerais sobre a execução de consulta LINQ, consulte [LINQ to Entities](../../../../../docs/framework/data/adonet/ef/language-reference/linq-to-entities.md). **Observação:** consultas LINQ to Entities que se aplicam a `Enumerable.Contains` operador coleções na memória não estão em cache automaticamente. Além disso, não é permitido parametrizar coleções na memória em consultas LINQ compiladas.|  
|Executando a consulta|Baixo<sup>2</sup>|Uma vez para cada consulta.|O custo de executar o comando na fonte de dados usando o provedor de dados do ADO.NET. Como a maioria das fontes de dados armazenam em cache os planos de consulta, as executa posteriores da mesma consulta podem levar ainda menos tempo.|  
|Carregando e validando tipos|Baixo<sup>3</sup>|Uma vez para cada instância <xref:System.Data.Objects.ObjectContext>.|Os tipos são carregados e validados nos tipos que o modelo conceitual define.|  
|Acompanhamento|Baixo<sup>3</sup>|Uma vez para cada objeto que uma consulta retorna. <sup>4</sup>|Se uma consulta usa a opção de mesclagem <xref:System.Data.Objects.MergeOption.NoTracking>, essa fase não afetará o desempenho.<br /><br /> Se a consulta usa a opção de mesclagem <xref:System.Data.Objects.MergeOption.AppendOnly>, <xref:System.Data.Objects.MergeOption.PreserveChanges> ou <xref:System.Data.Objects.MergeOption.OverwriteChanges>, os resultados da consulta são controlados no <xref:System.Data.Objects.ObjectStateManager>. Um <xref:System.Data.EntityKey> é gerado para cada objeto controlado que a consulta retorna e é usado para criar <xref:System.Data.Objects.ObjectStateEntry> no <xref:System.Data.Objects.ObjectStateManager>. Se um <xref:System.Data.Objects.ObjectStateEntry> existente pode ser encontrado para o <xref:System.Data.EntityKey>, o objeto existente é retornado. Se a opção <xref:System.Data.Objects.MergeOption.PreserveChanges> ou <xref:System.Data.Objects.MergeOption.OverwriteChanges> for usada, o objeto será atualizado antes de ser retornado.<br /><br /> Para obter mais informações, consulte [resolução de identidade, gerenciamento de estado e controle de alterações](http://msdn.microsoft.com/library/3bd49311-0e72-4ea4-8355-38fe57036ba0).|  
|Materializando os objetos|Moderada<sup>3</sup>|Uma vez para cada objeto que uma consulta retorna. <sup>4</sup>|O processo de ler o objeto retornado <xref:System.Data.Common.DbDataReader>, criar objetos e definir valores de propriedades que são baseados nos valores em cada instância da classe <xref:System.Data.Common.DbDataRecord>. Se o objeto já existir no <xref:System.Data.Objects.ObjectContext> e a consulta usar as opções de mesclagem <xref:System.Data.Objects.MergeOption.AppendOnly> ou <xref:System.Data.Objects.MergeOption.PreserveChanges>, essa fase não afetará o desempenho. Para obter mais informações, consulte [resolução de identidade, gerenciamento de estado e controle de alterações](http://msdn.microsoft.com/library/3bd49311-0e72-4ea4-8355-38fe57036ba0).|  
  
 <sup>1</sup> quando um provedor de fonte de dados implementa o pooling de conexão, o custo de abrir uma conexão é distribuído entre o pool. O provedor do .NET para o SQL Server dá suporte ao pool de conexões.  
  
 <sup>2</sup> custo aumenta a complexidade da consulta maior.  
  
 <sup>3</sup> custo total aumenta proporcional ao número de objetos retornados pela consulta.  
  
 <sup>4</sup> essa sobrecarga não é necessária para consultas de EntityClient porque EntityClient consulta retornar um <xref:System.Data.EntityClient.EntityDataReader> em vez de objetos. Para obter mais informações, consulte [provedor EntityClient para Entity Framework](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md).  
  
## <a name="additional-considerations"></a>Considerações adicionais  
 Veja a seguir as outras considerações que podem afetar o desempenho de aplicativos do Entity Framework.  
  
### <a name="query-execution"></a>Execução da Consulta  
 Como as consultas podem consumir recursos intensivamente, considere em qual ponto no seu código e em qual computador a consulta será executada.  
  
#### <a name="deferred-versus-immediate-execution"></a>Execução adiada versus imediata  
 Quando você cria uma consulta <xref:System.Data.Objects.ObjectQuery%601> ou LINQ, a consulta pode não ser executada imediatamente. A execução da consulta é adiada até que os resultados sejam necessários, como durante uma enumeração `foreach` (C#) ou `For Each` (Visual Basic) ou quando ela é atribuída para preencher uma coleção de <xref:System.Collections.Generic.List%601>. A execução da consulta começa imediatamente quando você chama o método <xref:System.Data.Objects.ObjectQuery%601.Execute%2A> em um <xref:System.Data.Objects.ObjectQuery%601> ou quando você chama um método LINQ que retorna uma consulta singleton, como <xref:System.Linq.Enumerable.First%2A> ou <xref:System.Linq.Enumerable.Any%2A>. Para obter mais informações, consulte [objeto consultas](http://msdn.microsoft.com/library/0768033c-876f-471d-85d5-264884349276) e [a execução da consulta (LINQ to Entities)](../../../../../docs/framework/data/adonet/ef/language-reference/query-execution.md).  
  
#### <a name="client-side-execution-of-linq-queries"></a>Execução do lado do cliente de consultas LINQ  
 Embora a execução de uma consulta LINQ ocorra no computador que hospeda a fonte de dados, algumas partes de uma consulta LINQ podem ser avaliadas no computador cliente. Para obter mais informações, consulte a seção de execução do repositório de [a execução da consulta (LINQ to Entities)](../../../../../docs/framework/data/adonet/ef/language-reference/query-execution.md).  
  
### <a name="query-and-mapping-complexity"></a>Complexidade da consulta e de mapeamento  
 A complexidade de consultas individuais e de mapeamento no modelo de entidade terá um efeito significativo no desempenho da consulta.  
  
#### <a name="mapping-complexity"></a>Complexidade de mapeamento  
 Os modelos que são mais complexos do que um mapeamento de um-para-um simples entre entidades no modelo conceitual e as tabelas no modelo de armazenamento geram comandos mais complexos que modelos que têm um mapeamento um-para-um.  
  
#### <a name="query-complexity"></a>Complexidade da consulta  
 As consultas que exigem um grande número junções nos comandos que são executados na fonte de dados ou que retornam uma grande quantidade de dados podem afetar o desempenho das seguintes maneiras:  
  
-   As consulta em um modelo conceitual que parecem simples podem resultar na execução de consultas mais complexas na fonte de dados. Isso pode ocorrer porque o Entity Framework converte uma consulta em um modelo conceitual em uma consulta equivalente na fonte de dados. Quando um único conjunto de entidades no modelo conceitual mapeia para mais de uma tabela na fonte de dados, ou quando uma relação entre entidades é mapeada para uma tabela de junção, o comando de consulta executado na consulta da fonte de dados pode exigir um ou mais junções.  
  
    > [!NOTE]
    >  Use o método <xref:System.Data.Objects.ObjectQuery.ToTraceString%2A> das classes <xref:System.Data.Objects.ObjectQuery%601> ou <xref:System.Data.EntityClient.EntityCommand> para exibir os comandos que são executados na fonte de dados para uma determinada consulta. Para obter mais informações, consulte [como: exibir os comandos de armazenamento](http://msdn.microsoft.com/library/f9771c6e-3b62-4b24-a5d4-55d68e14fa79).  
  
-   As consultas aninhadas do Entity SQL podem criar junções no servidor e podem retornar um grande número de linhas.  
  
     Veja a seguir um exemplo de uma consulta aninhada em uma cláusula de projeção:  
  
    ```  
    SELECT c, (SELECT c, (SELECT c FROM AdventureWorksModel.Vendor AS c  ) As Inner2   
        FROM AdventureWorksModel.JobCandidate AS c  ) As Inner1   
        FROM AdventureWorksModel.EmployeeDepartmentHistory AS c  
    ```  
  
     Além disso, essas consultas fazem o pipeline de consulta gerar uma única consulta com duplicação de objetos nas consultas aninhadas. Devido a isso, uma única coluna pode ser duplicada várias vezes. Em alguns bancos de dados, incluindo o SQL Server, isso pode fazer a tabela TempDB aumentar muito, o que pode diminuir o desempenho do servidor. Tome cuidado ao executar consultas aninhadas.  
  
-   Todas as consultas que retornam uma grande quantidade de dados podem diminuir o desempenho se o cliente estiver executando operações que consomem recursos de uma maneira que seja proporcional ao tamanho do conjunto de resultados. Nesses casos, você deve limitar a quantidade de dados retornados pela consulta. Para obter mais informações, consulte [como: página por meio de resultados da consulta](http://msdn.microsoft.com/library/ffc0f920-e7de-42e0-9b12-ef356421d030).  
  
 Todos os comandos gerados automaticamente pelo Entity Framework podem ser mais complexos que os comandos semelhantes escritos explicitamente por um desenvolvedor de banco de dados. Se você precisar de um controle explícito sobre os comandos executados em sua fonte de dados, defina um mapeamento para uma função de valores de tabela ou procedimento armazenado.  
  
#### <a name="relationships"></a>Relações  
 Para obter um desempenho otimizado da consulta, você deverá definir relacionamentos entre as entidades como associações no modelo de entidade e como relacionamentos lógicos na fonte de dados.  
  
### <a name="query-paths"></a>Caminhos de consulta  
 Por padrão, quando você executa um <xref:System.Data.Objects.ObjectQuery%601>, os objetos relacionados não são retornados (embora os objetos que representam as próprias relações sejam). Você pode carregar os objetos relacionados de uma das três maneiras:  
  
1.  Defina o caminho de consulta antes que <xref:System.Data.Objects.ObjectQuery%601> seja executado.  
  
2.  Chame o método `Load` na propriedade de navegação que o objeto expõe.  
  
3.  Defina a opção <xref:System.Data.Objects.ObjectContextOptions.LazyLoadingEnabled%2A> no <xref:System.Data.Objects.ObjectContext> como `true`. Observe que isso é feito automaticamente quando você gera o código da camada de objeto com o [Entity Data Model Designer](http://msdn.microsoft.com/library/4ccd7ad6-b934-4f7c-82a0-cfd2d4a95faf). Para obter mais informações, consulte [visão geral de código gerado](http://msdn.microsoft.com/library/6a88ea38-6a90-4107-bc33-531b79ce5b6a).  
  
 Quando você considera qual opção usar, esteja ciente de que há uma escolha entre o número de solicitações no banco de dados e a quantidade de dados retornados em uma única consulta. Para obter mais informações, consulte [objetos relacionados ao carregar](http://msdn.microsoft.com/library/452347d2-7b3b-44cd-9001-231299a28cb1).  
  
#### <a name="using-query-paths"></a>Usando caminhos de consulta  
 Os caminhos de consulta definem o gráfico de objetos que uma consulta retorna. Quando você define um caminho de consulta, somente uma única solicitação no banco de dados é necessária para retornar todos os objetos que o caminho define. Usar caminhos de consulta pode fazer comandos complexos serem executados na fonte de dados de consultas de objetos aparentemente simples. Isso ocorre porque uma ou mais junções são necessárias para retornar objetos relacionados em uma única consulta. Esta complexidade é maior em consultas em um modelo complexo de entidade, como uma entidade com herança ou um caminho que inclui relações muitos-para-muitos.  
  
> [!NOTE]
>  Use o método <xref:System.Data.Objects.ObjectQuery.ToTraceString%2A> para ver o comando que será gerado por um <xref:System.Data.Objects.ObjectQuery%601>. Para obter mais informações, consulte [como: exibir os comandos de armazenamento](http://msdn.microsoft.com/library/f9771c6e-3b62-4b24-a5d4-55d68e14fa79).  
  
 Quando um caminho de consulta inclui muitos objetos relacionados ou os objetos contêm muitos dados de linha, a fonte de dados pode ser incapaz de concluir a consulta. Isso ocorre se a consulta exigir um armazenamento temporário intermediário que excede os recursos da fonte de dados. Quando isso ocorre, você pode reduzir a complexidade da consulta da fonte de dados explicitamente carregando objetos relacionados.  
  
#### <a name="explicitly-loading-related-objects"></a>Carregando objetos relacionados explicitamente  
 Você pode carregar objetos relacionados explicitamente chamando o método `Load` em uma propriedade de navegação que retorna um <xref:System.Data.Objects.DataClasses.EntityCollection%601> ou <xref:System.Data.Objects.DataClasses.EntityReference%601>. Carregar objetos explicitamente exige uma viagem de ida e volta ao banco de dados toda vez que `Load` é chamado.  
  
> [!NOTE]
>  Se você chamar `Load` enquanto está executando um loop em uma coleção de objetos retornados, como quando você usar a instrução `foreach` (`For Each` no Visual Basic), o provedor específico da fonte de dados deverá dar suporte a vários conjuntos de resultados ativos em uma única conexão. Para um banco de dados do SQL Server, você deverá especificar um valor `MultipleActiveResultSets = true` na cadeia de conexão do provedor.  
  
 Você também pode usar o método <xref:System.Data.Objects.ObjectContext.LoadProperty%2A> quando não há nenhuma propriedade <xref:System.Data.Objects.DataClasses.EntityCollection%601> ou <xref:System.Data.Objects.DataClasses.EntityReference%601> em entidades. Isso é útil quando você está usando as entidades de POCO.  
  
 Embora carregar objetos relacionados explicitamente reduza o número de junções e diminua a quantidade de dados redundantes, `Load` exige conexões repetidas ao banco de dados, o que podem se tornar caro ao carregar explicitamente um grande número de objetos.  
  
### <a name="saving-changes"></a>Salvando alterações  
 Quando você chama o método <xref:System.Data.Objects.ObjectContext.SaveChanges%2A> em um <xref:System.Data.Objects.ObjectContext>, um comando create, update ou delete é gerado para cada objeto adicionado, atualizado ou excluído no contexto. Esses comandos são executados na fonte de dados em uma única transação. Assim como ocorre com as consultas, o desempenho de operações create, update e delete dependem da complexidade do mapeamento no modelo conceitual.  
  
### <a name="distributed-transactions"></a>Transações distribuídas  
 As operações em uma transação explícita que exigem recursos que são gerenciados pelo coordenador de transações distribuídas (DTC) serão muito mais caras que uma operação semelhante que não exige DTC. A promoção para o DTC ocorrerá nas seguintes situações:  
  
-   Uma transação explícita com uma operação em um banco de dados do SQL Server 2000 ou outra fonte de dados que sempre promova transações explícitas para o DTC.  
  
-   Uma transação explícita com uma operação no SQL Server 2005 quando a conexão é gerenciada pelo [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]. Isso ocorre porque o SQL Server 2005 promove para um DTC sempre que uma conexão é fechada e reaberta dentro de uma única transação, que é o comportamento padrão do [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]. Esta promoção de DTC não ocorrer ao usar o SQL Server 2008. Para evitar esta promoção ao usar o SQL Server 2005, você deve explicitamente abrir e fechar a conexão na transação. Para obter mais informações, consulte [Gerenciando conexões e transações](http://msdn.microsoft.com/library/b6659d2a-9a45-4e98-acaa-d7a8029e5b99).  
  
 Uma transação explícita é usada quando uma ou mais operações são executadas dentro de uma transação <xref:System.Transactions>. Para obter mais informações, consulte [Gerenciando conexões e transações](http://msdn.microsoft.com/library/b6659d2a-9a45-4e98-acaa-d7a8029e5b99).  
  
## <a name="strategies-for-improving-performance"></a>Estratégias para melhorar o desempenho  
 Você pode melhorar o desempenho geral das consultas no Entity Framework usando as seguintes estratégias.  
  
#### <a name="pre-generate-views"></a>Pré-gerar exibições  
 Gerar exibições com base em um modelo de entidade é um custo significativo na primeira vez que um aplicativo executa uma consulta. Use o utilitário EdmGen.exe para pré-gerar exibições como um arquivo de código do Visual Basic ou C# que pode ser adicionado ao projeto durante o design. Você também pode usar o Kit de ferramentas de transformação do modelo de texto para gerar exibições pré-compiladas. Exibições pré-geradas são validadas em tempo de execução para garantir que sejam consistentes com a versão atual do modelo de entidade especificado. Para obter mais informações, consulte [como: Pre-Generate exibições para melhorar o desempenho da consulta](http://msdn.microsoft.com/library/b18a9d16-e10b-4043-ba91-b632f85a2579) e [isolamento de desempenho com pré-compilado/pré-generated exibições no Entity Framework 4](http://go.microsoft.com/fwlink/?LinkID=201337&clcid=0x409).  
  
 Ao trabalhar com modelos muito grandes, a consideração a seguir se aplica:  
  
 O formato de metadados do .NET limita o número de caracteres de uma cadeia de caracteres de usuário em um determinado binário a 16.777.215 (0xFFFFFF). Se você estiver gerando modos de exibição para um modelo muito grande e o arquivo de exibição atingir esse limite de tamanho, você obterá a "nenhum espaço lógico deixado para criar mais cadeias de caracteres do usuário." Erro de compilação. Essa limitação de tamanho aplica-se a todos os binários gerenciados. Para obter mais informações, consulte o [blog](http://go.microsoft.com/fwlink/?LinkId=201476) que demonstra como evitar o erro ao trabalhar com modelos grandes e complexos.  
  
#### <a name="consider-using-the-notracking-merge-option-for-queries"></a>Use a opção de mesclagem NoTracking para consultas  
 Há um custo necessário para controlar objetos retornados no contexto do objeto. Detectar alterações aos objetos e garantir que as várias solicitações para a mesma entidade lógica retorne a mesma instância de objeto exige que os objetos sejam anexados a uma instância <xref:System.Data.Objects.ObjectContext>. Se você não pretende fazer atualizações ou exclusões em objetos e não exige o gerenciamento de identidade, use as opções de mesclagem <xref:System.Data.Objects.MergeOption.NoTracking> ao executar consultas.  
  
#### <a name="return-the-correct-amount-of-data"></a>Retornar a quantidade correta de dados  
 Em alguns cenários, especificar um caminho de consulta usando o método <xref:System.Data.Objects.ObjectQuery%601.Include%2A> é muito mais rápido porque exige menos viagens de ida e volta para o banco de dados. No entanto, em outros cenários, as viagens de ida e volta adicionais ao banco de dados para carregar objetos relacionados podem ser mais rápidas porque as consultas mais simples com menos junções resultam em menos redundância de dados. Por causa disso, recomendamos que você testar o desempenho de várias maneiras para recuperar objetos relacionados. Para obter mais informações, consulte [objetos relacionados ao carregar](http://msdn.microsoft.com/library/452347d2-7b3b-44cd-9001-231299a28cb1).  
  
 Para evitar retornar dados demais em uma única consulta, pagine os resultados da consulta em grupos mais gerenciáveis. Para obter mais informações, consulte [como: página por meio de resultados da consulta](http://msdn.microsoft.com/library/ffc0f920-e7de-42e0-9b12-ef356421d030).  
  
#### <a name="limit-the-scope-of-the-objectcontext"></a>Limitar o escopo do ObjectContext  
 Na maioria dos casos, você deverá criar uma instância <xref:System.Data.Objects.ObjectContext> dentro de uma instrução `using` (`Using…End Using` no Visual Basic). Isso poderá aumentar o desempenho garantindo que os recursos associados com o contexto do objeto sejam descartados automaticamente quando o código sair do bloco de instruções. No entanto, quando os controles estão associados a objetos gerenciados pelo contexto do objeto, a instância <xref:System.Data.Objects.ObjectContext> deve ser mantida contanto que a associação seja necessária e descartada manualmente. Para obter mais informações, consulte [Gerenciando conexões e transações](http://msdn.microsoft.com/library/b6659d2a-9a45-4e98-acaa-d7a8029e5b99).  
  
#### <a name="consider-opening-the-database-connection-manually"></a>Abrir a conexão de banco de dados manualmente  
 Quando seu aplicativo executa uma série de consultas de objeto ou frequentemente chama <xref:System.Data.Objects.ObjectContext.SaveChanges%2A> para manter criar, atualizar e excluir operações para a fonte de dados, o [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] continuamente deve abrir e fechar a conexão à fonte de dados. Nessas situações, abra manualmente a conexão no início dessas operações e feche ou descarte a conexão quando as operações estiverem concluídas. Para obter mais informações, consulte [Gerenciando conexões e transações](http://msdn.microsoft.com/library/b6659d2a-9a45-4e98-acaa-d7a8029e5b99).  
  
## <a name="performance-data"></a>Dados de Desempenho  
 Alguns dados de desempenho para o Entity Framework são publicados no seguintes postagens no [blog da equipe do ADO.NET](http://go.microsoft.com/fwlink/?LinkId=91905):  
  
-   [Explorando o desempenho do ADO.NET Entity Framework - parte 1](http://go.microsoft.com/fwlink/?LinkId=123907)  
  
-   [Explorando o desempenho do ADO.NET Entity Framework – parte 2](http://go.microsoft.com/fwlink/?LinkId=123909)  
  
-   [Comparação de desempenho do ADO.NET Entity Framework](http://go.microsoft.com/fwlink/?LinkID=123913)  
  
## <a name="see-also"></a>Consulte também  
 [Considerações de desenvolvimento e implantação](../../../../../docs/framework/data/adonet/ef/development-and-deployment-considerations.md)
