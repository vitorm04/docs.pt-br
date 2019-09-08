---
title: Perguntas frequentes
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 252ed666-0679-4eea-b71b-2f14117ef443
ms.openlocfilehash: ed9149eb5b88d648c02863e0fb0101e5503e1c73
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782150"
---
# <a name="frequently-asked-questions"></a><span data-ttu-id="bdbec-102">Perguntas frequentes</span><span class="sxs-lookup"><span data-stu-id="bdbec-102">Frequently Asked Questions</span></span>

<span data-ttu-id="bdbec-103">As seções a seguir respondem a alguns problemas comuns que você pode encontrar ao implementar o [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bdbec-103">The following sections answer some common issues that you might encounter when you implement [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)].</span></span>

<span data-ttu-id="bdbec-104">Problemas adicionais são abordados na [solução de problemas](troubleshooting.md).</span><span class="sxs-lookup"><span data-stu-id="bdbec-104">Additional issues are addressed in [Troubleshooting](troubleshooting.md).</span></span>

## <a name="cannot-connect"></a><span data-ttu-id="bdbec-105">Não é possível conectar</span><span class="sxs-lookup"><span data-stu-id="bdbec-105">Cannot Connect</span></span>

<span data-ttu-id="bdbec-106">P.</span><span class="sxs-lookup"><span data-stu-id="bdbec-106">Q.</span></span> <span data-ttu-id="bdbec-107">Não consigo me conectar a meu banco de dados.</span><span class="sxs-lookup"><span data-stu-id="bdbec-107">I cannot connect to my database.</span></span>

<span data-ttu-id="bdbec-108">A.</span><span class="sxs-lookup"><span data-stu-id="bdbec-108">A.</span></span> <span data-ttu-id="bdbec-109">Verifique se a cadeia de conexão está correta e se sua instância de SQL Server está em execução.</span><span class="sxs-lookup"><span data-stu-id="bdbec-109">Make sure your connection string is correct and that your SQL Server instance is running.</span></span> <span data-ttu-id="bdbec-110">Observe também que o [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] exige que o protocolo de pipes nomeados esteja ativado.</span><span class="sxs-lookup"><span data-stu-id="bdbec-110">Note also that [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] requires the Named Pipes protocol to be enabled.</span></span> <span data-ttu-id="bdbec-111">Para obter mais informações, consulte [aprendendo por instruções](learning-by-walkthroughs.md).</span><span class="sxs-lookup"><span data-stu-id="bdbec-111">For more information, see [Learning by Walkthroughs](learning-by-walkthroughs.md).</span></span>

## <a name="changes-to-database-lost"></a><span data-ttu-id="bdbec-112">Alterações perdidas do banco de dados</span><span class="sxs-lookup"><span data-stu-id="bdbec-112">Changes to Database Lost</span></span>

<span data-ttu-id="bdbec-113">P.</span><span class="sxs-lookup"><span data-stu-id="bdbec-113">Q.</span></span> <span data-ttu-id="bdbec-114">Fiz uma alteração nos dados no banco de dados, mas, quando executei o aplicativo, a alteração não estava mais lá.</span><span class="sxs-lookup"><span data-stu-id="bdbec-114">I made a change to data in the database, but when I reran my application, the change was no longer there.</span></span>

<span data-ttu-id="bdbec-115">A.</span><span class="sxs-lookup"><span data-stu-id="bdbec-115">A.</span></span> <span data-ttu-id="bdbec-116">Verifique se você chamou <xref:System.Data.Linq.DataContext.SubmitChanges%2A> para salvar os resultados no banco de dados.</span><span class="sxs-lookup"><span data-stu-id="bdbec-116">Make sure that you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A> to save results to the database.</span></span>

## <a name="database-connection-open-how-long"></a><span data-ttu-id="bdbec-117">Conexão de banco de dados: Abrir por quanto tempo?</span><span class="sxs-lookup"><span data-stu-id="bdbec-117">Database Connection: Open How Long?</span></span>

<span data-ttu-id="bdbec-118">P.</span><span class="sxs-lookup"><span data-stu-id="bdbec-118">Q.</span></span> <span data-ttu-id="bdbec-119">Quanto tempo a conexão do banco de dados permanece aberta?</span><span class="sxs-lookup"><span data-stu-id="bdbec-119">How long does my database connection remain open?</span></span>

<span data-ttu-id="bdbec-120">A.</span><span class="sxs-lookup"><span data-stu-id="bdbec-120">A.</span></span> <span data-ttu-id="bdbec-121">Uma conexão geralmente permanece aberta até você consumir os resultados da consulta.</span><span class="sxs-lookup"><span data-stu-id="bdbec-121">A connection typically remains open until you consume the query results.</span></span> <span data-ttu-id="bdbec-122">Se você pretende processar todos os resultados e não se opõe a armazenar em cache os resultados, aplique <xref:System.Linq.Enumerable.ToList%2A> à consulta.</span><span class="sxs-lookup"><span data-stu-id="bdbec-122">If you expect to take time to process all the results and are not opposed to caching the results, apply <xref:System.Linq.Enumerable.ToList%2A> to the query.</span></span> <span data-ttu-id="bdbec-123">Em cenários comuns onde cada objeto é processado somente uma vez, o modelo de streaming é superior no `DataReader` e no [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bdbec-123">In common scenarios where each object is processed only one time, the streaming model is superior in both `DataReader` and [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>

<span data-ttu-id="bdbec-124">Os detalhes exatos do uso da conexão dependem do seguinte:</span><span class="sxs-lookup"><span data-stu-id="bdbec-124">The exact details of connection usage depend on the following:</span></span>

- <span data-ttu-id="bdbec-125">Status da conexão se <xref:System.Data.Linq.DataContext> for construído com um objeto de conexão.</span><span class="sxs-lookup"><span data-stu-id="bdbec-125">Connection status if the <xref:System.Data.Linq.DataContext> is constructed with a connection object.</span></span>

- <span data-ttu-id="bdbec-126">Configurações da cadeia de conexão (por exemplo, permitindo MARS, Multiple Active Result Sets).</span><span class="sxs-lookup"><span data-stu-id="bdbec-126">Connection string settings (for example, enabling Multiple Active Result Sets (MARS).</span></span> <span data-ttu-id="bdbec-127">Para obter mais informações, confira [MARS (Conjunto de Resultados Ativos Múltiplos)](../multiple-active-result-sets-mars.md).</span><span class="sxs-lookup"><span data-stu-id="bdbec-127">For more information, see [Multiple Active Result Sets (MARS)](../multiple-active-result-sets-mars.md).</span></span>

## <a name="updating-without-querying"></a><span data-ttu-id="bdbec-128">Atualizar sem consultar</span><span class="sxs-lookup"><span data-stu-id="bdbec-128">Updating Without Querying</span></span>

<span data-ttu-id="bdbec-129">P.</span><span class="sxs-lookup"><span data-stu-id="bdbec-129">Q.</span></span> <span data-ttu-id="bdbec-130">Posso atualizar os dados da tabela sem primeiro consultar o banco de dados?</span><span class="sxs-lookup"><span data-stu-id="bdbec-130">Can I update table data without first querying the database?</span></span>

<span data-ttu-id="bdbec-131">A.</span><span class="sxs-lookup"><span data-stu-id="bdbec-131">A.</span></span> <span data-ttu-id="bdbec-132">Embora o [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] não tenha comandos de atualização baseados em conjunto, você pode usar qualquer uma das seguintes técnicas para atualizar sem consultar primeiro:</span><span class="sxs-lookup"><span data-stu-id="bdbec-132">Although [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] does not have set-based update commands, you can use either of the following techniques to update without first querying:</span></span>

- <span data-ttu-id="bdbec-133">Use <xref:System.Data.Linq.DataContext.ExecuteCommand%2A> para enviar o código SQL.</span><span class="sxs-lookup"><span data-stu-id="bdbec-133">Use <xref:System.Data.Linq.DataContext.ExecuteCommand%2A> to send SQL code.</span></span>

- <span data-ttu-id="bdbec-134">Crie uma nova instância do objeto e inicialize todos os valores atuais (campos) que afetam a atualização.</span><span class="sxs-lookup"><span data-stu-id="bdbec-134">Create a new instance of the object and initialize all the current values (fields) that affect the update.</span></span> <span data-ttu-id="bdbec-135">Anexe o objeto ao <xref:System.Data.Linq.DataContext> usando <xref:System.Data.Linq.Table%601.Attach%2A> e modifique o campo que você deseja alterar.</span><span class="sxs-lookup"><span data-stu-id="bdbec-135">Then attach the object to the <xref:System.Data.Linq.DataContext> by using <xref:System.Data.Linq.Table%601.Attach%2A> and modify the field you want to change.</span></span>

## <a name="unexpected-query-results"></a><span data-ttu-id="bdbec-136">Resultados inesperados da consulta</span><span class="sxs-lookup"><span data-stu-id="bdbec-136">Unexpected Query Results</span></span>

<span data-ttu-id="bdbec-137">P.</span><span class="sxs-lookup"><span data-stu-id="bdbec-137">Q.</span></span> <span data-ttu-id="bdbec-138">Minha consulta está retornando resultados inesperados.</span><span class="sxs-lookup"><span data-stu-id="bdbec-138">My query is returning unexpected results.</span></span> <span data-ttu-id="bdbec-139">Como posso inspecionar o que está ocorrendo?</span><span class="sxs-lookup"><span data-stu-id="bdbec-139">How can I inspect what is occurring?</span></span>

<span data-ttu-id="bdbec-140">A.</span><span class="sxs-lookup"><span data-stu-id="bdbec-140">A.</span></span> <span data-ttu-id="bdbec-141">O [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] fornece várias ferramentas para inspecionar o código SQL que produz.</span><span class="sxs-lookup"><span data-stu-id="bdbec-141">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] provides several tools for inspecting the SQL code it generates.</span></span> <span data-ttu-id="bdbec-142">Um dos mais importantes é <xref:System.Data.Linq.DataContext.Log%2A>.</span><span class="sxs-lookup"><span data-stu-id="bdbec-142">One of the most important is <xref:System.Data.Linq.DataContext.Log%2A>.</span></span> <span data-ttu-id="bdbec-143">Para obter mais informações, consulte [depuração de suporte](debugging-support.md).</span><span class="sxs-lookup"><span data-stu-id="bdbec-143">For more information, see [Debugging Support](debugging-support.md).</span></span>

## <a name="unexpected-stored-procedure-results"></a><span data-ttu-id="bdbec-144">Resultados inesperados de procedimentos armazenados</span><span class="sxs-lookup"><span data-stu-id="bdbec-144">Unexpected Stored Procedure Results</span></span>

<span data-ttu-id="bdbec-145">P.</span><span class="sxs-lookup"><span data-stu-id="bdbec-145">Q.</span></span> <span data-ttu-id="bdbec-146">Tenho um procedimento armazenado cujo valor de retorno é calculado por `MAX()`.</span><span class="sxs-lookup"><span data-stu-id="bdbec-146">I have a stored procedure whose return value is calculated by `MAX()`.</span></span> <span data-ttu-id="bdbec-147">Quando arrasto o procedimento armazenado para a superfície o/R Designer, o valor de retorno não está correto.</span><span class="sxs-lookup"><span data-stu-id="bdbec-147">When I drag the stored procedure to the O/R Designer surface, the return value is not correct.</span></span>

<span data-ttu-id="bdbec-148">A.</span><span class="sxs-lookup"><span data-stu-id="bdbec-148">A.</span></span> <span data-ttu-id="bdbec-149">O [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] fornece duas maneiras de retornar valores gerados por banco de dados por meio de procedimentos armazenados:</span><span class="sxs-lookup"><span data-stu-id="bdbec-149">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] provides two ways to return database-generated values by way of stored procedures:</span></span>

- <span data-ttu-id="bdbec-150">Nomeando o resultado de saída.</span><span class="sxs-lookup"><span data-stu-id="bdbec-150">By naming the output result.</span></span>

- <span data-ttu-id="bdbec-151">Especificando explicitamente um parâmetro de saída.</span><span class="sxs-lookup"><span data-stu-id="bdbec-151">By explicitly specifying an output parameter.</span></span>

<span data-ttu-id="bdbec-152">O código a seguir é um exemplo de saída incorreta.</span><span class="sxs-lookup"><span data-stu-id="bdbec-152">The following is an example of incorrect output.</span></span> <span data-ttu-id="bdbec-153">Como o [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] não pode mapear os resultados, ele sempre retorna 0:</span><span class="sxs-lookup"><span data-stu-id="bdbec-153">Because [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] cannot map the results, it always returns 0:</span></span>

```sql
create procedure proc2

as

begin

select max(i) from t where name like 'hello'

end
```

<span data-ttu-id="bdbec-154">O código a seguir é um exemplo de saída correta usando um parâmetro de saída:</span><span class="sxs-lookup"><span data-stu-id="bdbec-154">The following is an example of correct output by using an output parameter:</span></span>

```sql
create procedure proc2

@result int OUTPUT

as

select @result = MAX(i) from t where name like 'hello'

go
```

<span data-ttu-id="bdbec-155">O código a seguir é um exemplo de saída correta nomeando o resultado de saída:</span><span class="sxs-lookup"><span data-stu-id="bdbec-155">The following is an example of correct output by naming the output result:</span></span>

```sql
create procedure proc2

as

begin

select nax(i) AS MaxResult from t where name like 'hello'

end
```

<span data-ttu-id="bdbec-156">Para obter mais informações, consulte [Personalizando operações usando procedimentos armazenados](customizing-operations-by-using-stored-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="bdbec-156">For more information, see [Customizing Operations By Using Stored Procedures](customizing-operations-by-using-stored-procedures.md).</span></span>

## <a name="serialization-errors"></a><span data-ttu-id="bdbec-157">Erros de serialização</span><span class="sxs-lookup"><span data-stu-id="bdbec-157">Serialization Errors</span></span>

<span data-ttu-id="bdbec-158">P.</span><span class="sxs-lookup"><span data-stu-id="bdbec-158">Q.</span></span> <span data-ttu-id="bdbec-159">Quando tento serializar, obtenho o seguinte erro: "Tipo ' System. Data. Linq. ChangeTracker + StandardChangeTracker '... Não está marcado como serializável. "</span><span class="sxs-lookup"><span data-stu-id="bdbec-159">When I try to serialize, I get the following error: "Type 'System.Data.Linq.ChangeTracker+StandardChangeTracker' ... is not marked as serializable."</span></span>

<span data-ttu-id="bdbec-160">A.</span><span class="sxs-lookup"><span data-stu-id="bdbec-160">A.</span></span> <span data-ttu-id="bdbec-161">A geração de código no [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dá suporte à serialização do <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="bdbec-161">Code generation in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] supports <xref:System.Runtime.Serialization.DataContractSerializer> serialization.</span></span> <span data-ttu-id="bdbec-162">Ela não dá suporte a <xref:System.Xml.Serialization.XmlSerializer> ou <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>.</span><span class="sxs-lookup"><span data-stu-id="bdbec-162">It does not support <xref:System.Xml.Serialization.XmlSerializer> or <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>.</span></span> <span data-ttu-id="bdbec-163">Para obter mais informações, consulte [Serialização](serialization.md).</span><span class="sxs-lookup"><span data-stu-id="bdbec-163">For more information, see [Serialization](serialization.md).</span></span>

## <a name="multiple-dbml-files"></a><span data-ttu-id="bdbec-164">Vários arquivos DBML</span><span class="sxs-lookup"><span data-stu-id="bdbec-164">Multiple DBML Files</span></span>

<span data-ttu-id="bdbec-165">P.</span><span class="sxs-lookup"><span data-stu-id="bdbec-165">Q.</span></span> <span data-ttu-id="bdbec-166">Quando eu tenho vários arquivos DBML que compartilham algumas tabelas em comum, eu obtenho um erro do compilador.</span><span class="sxs-lookup"><span data-stu-id="bdbec-166">When I have multiple DBML files that share some tables in common, I get a compiler error.</span></span>

<span data-ttu-id="bdbec-167">A.</span><span class="sxs-lookup"><span data-stu-id="bdbec-167">A.</span></span> <span data-ttu-id="bdbec-168">Defina o **namespace de contexto** e as propriedades de **namespace de entidade** do Object Relational Designer para um valor distinto para cada arquivo dbml.</span><span class="sxs-lookup"><span data-stu-id="bdbec-168">Set the **Context Namespace** and **Entity Namespace** properties from the Object Relational Designer to a distinct value for each DBML file.</span></span> <span data-ttu-id="bdbec-169">Essa abordagem elimina a colisão nome/namespace.</span><span class="sxs-lookup"><span data-stu-id="bdbec-169">This approach eliminates the name/namespace collision.</span></span>

## <a name="avoiding-explicit-setting-of-database-generated-values-on-insert-or-update"></a><span data-ttu-id="bdbec-170">Evitando a configuração explícita de valores gerados por banco de dados em Insert ou Update</span><span class="sxs-lookup"><span data-stu-id="bdbec-170">Avoiding Explicit Setting of Database-Generated Values on Insert or Update</span></span>

<span data-ttu-id="bdbec-171">P.</span><span class="sxs-lookup"><span data-stu-id="bdbec-171">Q.</span></span> <span data-ttu-id="bdbec-172">Tenho uma tabela de banco de dados com uma coluna `DateCreated` que usa como padrão o `Getdate()` do SQL.</span><span class="sxs-lookup"><span data-stu-id="bdbec-172">I have a database table with a `DateCreated` column that defaults to SQL `Getdate()`.</span></span> <span data-ttu-id="bdbec-173">Quando tento inserir um novo registro usando o [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], o valor é definido como `NULL`.</span><span class="sxs-lookup"><span data-stu-id="bdbec-173">When I try to insert a new record by using [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the value gets set to `NULL`.</span></span> <span data-ttu-id="bdbec-174">Eu gostaria que ele fosse definido como o padrão do banco de dados.</span><span class="sxs-lookup"><span data-stu-id="bdbec-174">I would expect it to be set to the database default.</span></span>

<span data-ttu-id="bdbec-175">A.</span><span class="sxs-lookup"><span data-stu-id="bdbec-175">A.</span></span> <span data-ttu-id="bdbec-176">O [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] trata essa situação automaticamente para colunas de identidade (incremento automático) e rowguidcol (GUID gerado por banco de dados) e carimbo de data/hora.</span><span class="sxs-lookup"><span data-stu-id="bdbec-176">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] handles this situation automatically for identity (auto-increment) and rowguidcol (database-generated GUID) and timestamp columns.</span></span> <span data-ttu-id="bdbec-177">Em <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> outros casos, você deve definir = <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A> = `true` e Propriedadesmanualmente<xref:System.Data.Linq.Mapping.AutoSync.Always> . / <xref:System.Data.Linq.Mapping.AutoSync.OnInsert> / <xref:System.Data.Linq.Mapping.AutoSync.OnUpdate></span><span class="sxs-lookup"><span data-stu-id="bdbec-177">In other cases, you should manually set <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>=`true` and <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A>=<xref:System.Data.Linq.Mapping.AutoSync.Always>/<xref:System.Data.Linq.Mapping.AutoSync.OnInsert>/<xref:System.Data.Linq.Mapping.AutoSync.OnUpdate> properties.</span></span>

## <a name="multiple-dataloadoptions"></a><span data-ttu-id="bdbec-178">Vários DataLoadOptions</span><span class="sxs-lookup"><span data-stu-id="bdbec-178">Multiple DataLoadOptions</span></span>

<span data-ttu-id="bdbec-179">P.</span><span class="sxs-lookup"><span data-stu-id="bdbec-179">Q.</span></span> <span data-ttu-id="bdbec-180">Posso especificar opções de carregamento adicionais sem substituir as primeiras?</span><span class="sxs-lookup"><span data-stu-id="bdbec-180">Can I specify additional load options without overwriting the first?</span></span>

<span data-ttu-id="bdbec-181">A.</span><span class="sxs-lookup"><span data-stu-id="bdbec-181">A.</span></span> <span data-ttu-id="bdbec-182">Sim.</span><span class="sxs-lookup"><span data-stu-id="bdbec-182">Yes.</span></span> <span data-ttu-id="bdbec-183">A primeira não é substituída, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="bdbec-183">The first is not overwritten, as in the following example:</span></span>

```vb
Dim dlo As New DataLoadOptions()
dlo.LoadWith(Of Order)(Function(o As Order) o.Customer)
dlo.LoadWith(Of Order)(Function(o As Order) o.OrderDetails)
```

```csharp
DataLoadOptions dlo = new DataLoadOptions();
dlo.LoadWith<Order>(o => o.Customer);
dlo.LoadWith<Order>(o => o.OrderDetails);
```

## <a name="errors-using-sql-compact-35"></a><span data-ttu-id="bdbec-184">Erros ao usar o SQL Compact 3.5</span><span class="sxs-lookup"><span data-stu-id="bdbec-184">Errors Using SQL Compact 3.5</span></span>

<span data-ttu-id="bdbec-185">P.</span><span class="sxs-lookup"><span data-stu-id="bdbec-185">Q.</span></span> <span data-ttu-id="bdbec-186">Recebo um erro quando arrasto tabelas de um banco de dados SQL Server Compact 3,5.</span><span class="sxs-lookup"><span data-stu-id="bdbec-186">I get an error when I drag tables out of a SQL Server Compact 3.5 database.</span></span>

<span data-ttu-id="bdbec-187">A.</span><span class="sxs-lookup"><span data-stu-id="bdbec-187">A.</span></span> <span data-ttu-id="bdbec-188">O Object Relational Designer não oferece suporte a SQL Server Compact 3,5, embora [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] o tempo de execução faça.</span><span class="sxs-lookup"><span data-stu-id="bdbec-188">The Object Relational Designer does not support SQL Server Compact 3.5, although the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] runtime does.</span></span> <span data-ttu-id="bdbec-189">Nesta situação, você deve criar suas próprias classes de entidade e adicionar os atributos apropriados.</span><span class="sxs-lookup"><span data-stu-id="bdbec-189">In this situation, you must create your own entity classes and add the appropriate attributes.</span></span>

## <a name="errors-in-inheritance-relationships"></a><span data-ttu-id="bdbec-190">Erros nas relações de herança</span><span class="sxs-lookup"><span data-stu-id="bdbec-190">Errors in Inheritance Relationships</span></span>

<span data-ttu-id="bdbec-191">P.</span><span class="sxs-lookup"><span data-stu-id="bdbec-191">Q.</span></span> <span data-ttu-id="bdbec-192">Usei a forma de herança da caixa de ferramentas no Object Relational Designer para conectar duas entidades, mas recebo erros.</span><span class="sxs-lookup"><span data-stu-id="bdbec-192">I used the toolbox inheritance shape in the Object Relational Designer to connect two entities, but I get errors.</span></span>

<span data-ttu-id="bdbec-193">A.</span><span class="sxs-lookup"><span data-stu-id="bdbec-193">A.</span></span> <span data-ttu-id="bdbec-194">Criar a relação não é suficiente.</span><span class="sxs-lookup"><span data-stu-id="bdbec-194">Creating the relationship is not enough.</span></span> <span data-ttu-id="bdbec-195">Você deve fornecer informações como a coluna do discriminador, o valor do discriminador da classe base e o valor do discriminador da classe derivada.</span><span class="sxs-lookup"><span data-stu-id="bdbec-195">You must provide information such as the discriminator column, base class discriminator value, and derived class discriminator value.</span></span>

## <a name="provider-model"></a><span data-ttu-id="bdbec-196">Modelo do provedor</span><span class="sxs-lookup"><span data-stu-id="bdbec-196">Provider Model</span></span>

<span data-ttu-id="bdbec-197">P.</span><span class="sxs-lookup"><span data-stu-id="bdbec-197">Q.</span></span> <span data-ttu-id="bdbec-198">Um modelo de provedor público está disponível?</span><span class="sxs-lookup"><span data-stu-id="bdbec-198">Is a public provider model available?</span></span>

<span data-ttu-id="bdbec-199">A.</span><span class="sxs-lookup"><span data-stu-id="bdbec-199">A.</span></span> <span data-ttu-id="bdbec-200">Nenhum modelo de provedor público está disponível.</span><span class="sxs-lookup"><span data-stu-id="bdbec-200">No public provider model is available.</span></span> <span data-ttu-id="bdbec-201">Neste momento, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] o oferece suporte apenas a SQL Server e SQL Server Compact 3,5.</span><span class="sxs-lookup"><span data-stu-id="bdbec-201">At this time, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] supports SQL Server and SQL Server Compact 3.5 only.</span></span>

## <a name="sql-injection-attacks"></a><span data-ttu-id="bdbec-202">Ataques de injeção de SQL</span><span class="sxs-lookup"><span data-stu-id="bdbec-202">SQL-Injection Attacks</span></span>

<span data-ttu-id="bdbec-203">P.</span><span class="sxs-lookup"><span data-stu-id="bdbec-203">Q.</span></span> <span data-ttu-id="bdbec-204">Como o [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] é protegido contra ataques de injeção de SQL?</span><span class="sxs-lookup"><span data-stu-id="bdbec-204">How is [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] protected from SQL-injection attacks?</span></span>

<span data-ttu-id="bdbec-205">A.</span><span class="sxs-lookup"><span data-stu-id="bdbec-205">A.</span></span> <span data-ttu-id="bdbec-206">A injeção de SQL tem sido um risco significativo para consultas tradicionais de SQL formadas por meio da concatenação da entrada do usuário.</span><span class="sxs-lookup"><span data-stu-id="bdbec-206">SQL injection has been a significant risk for traditional SQL queries formed by concatenating user input.</span></span> <span data-ttu-id="bdbec-207">O [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] evita essa injeção usando o <xref:System.Data.SqlClient.SqlParameter> em consultas.</span><span class="sxs-lookup"><span data-stu-id="bdbec-207">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] avoids such injection by using <xref:System.Data.SqlClient.SqlParameter> in queries.</span></span> <span data-ttu-id="bdbec-208">A entrada do usuário é transformada em valores de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="bdbec-208">User input is turned into parameter values.</span></span> <span data-ttu-id="bdbec-209">Essa abordagem impede que os comandos mal-intencionados sejam usados da entrada do cliente.</span><span class="sxs-lookup"><span data-stu-id="bdbec-209">This approach prevents malicious commands from being used from customer input.</span></span>

## <a name="changing-read-only-flag-in-dbml-files"></a><span data-ttu-id="bdbec-210">Alterando o sinalizador somente leitura em arquivos DBML</span><span class="sxs-lookup"><span data-stu-id="bdbec-210">Changing Read-only Flag in DBML Files</span></span>

<span data-ttu-id="bdbec-211">P.</span><span class="sxs-lookup"><span data-stu-id="bdbec-211">Q.</span></span> <span data-ttu-id="bdbec-212">Como posso eliminar configuradores de algumas propriedades quando crio um modelo de objeto de um arquivo DBML?</span><span class="sxs-lookup"><span data-stu-id="bdbec-212">How do I eliminate setters from some properties when I create an object model from a DBML file?</span></span>

<span data-ttu-id="bdbec-213">A.</span><span class="sxs-lookup"><span data-stu-id="bdbec-213">A.</span></span> <span data-ttu-id="bdbec-214">Siga as etapas a seguir para este cenário avançado:</span><span class="sxs-lookup"><span data-stu-id="bdbec-214">Take the following steps for this advanced scenario:</span></span>

1. <span data-ttu-id="bdbec-215">No arquivo .dbml, modifique a propriedade alterando o sinalizador do <xref:System.Data.Linq.ITable.IsReadOnly%2A> para `True`.</span><span class="sxs-lookup"><span data-stu-id="bdbec-215">In the .dbml file, modify the property by changing the <xref:System.Data.Linq.ITable.IsReadOnly%2A> flag to `True`.</span></span>

2. <span data-ttu-id="bdbec-216">Adicione uma classe parcial.</span><span class="sxs-lookup"><span data-stu-id="bdbec-216">Add a partial class.</span></span> <span data-ttu-id="bdbec-217">Crie um construtor com parâmetros para os membros somente leitura.</span><span class="sxs-lookup"><span data-stu-id="bdbec-217">Create a constructor with parameters for the read-only members.</span></span>

3. <span data-ttu-id="bdbec-218">Examine o valor padrão <xref:System.Data.Linq.Mapping.UpdateCheck> (<xref:System.Data.Linq.Mapping.UpdateCheck.Never>) para determinar se este é o valor correto para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="bdbec-218">Review the default <xref:System.Data.Linq.Mapping.UpdateCheck> value (<xref:System.Data.Linq.Mapping.UpdateCheck.Never>) to determine whether that is the correct value for your application.</span></span>

    > [!CAUTION]
    > <span data-ttu-id="bdbec-219">Se você estiver usando o Object Relational Designer no Visual Studio, suas alterações poderão ser substituídas.</span><span class="sxs-lookup"><span data-stu-id="bdbec-219">If you are using the Object Relational Designer in Visual Studio, your changes might be overwritten.</span></span>

## <a name="aptca"></a><span data-ttu-id="bdbec-220">APTCA</span><span class="sxs-lookup"><span data-stu-id="bdbec-220">APTCA</span></span>

<span data-ttu-id="bdbec-221">P.</span><span class="sxs-lookup"><span data-stu-id="bdbec-221">Q.</span></span> <span data-ttu-id="bdbec-222">O System.Data.Linq está marcado para ser usado pelo código parcialmente confiável?</span><span class="sxs-lookup"><span data-stu-id="bdbec-222">Is System.Data.Linq marked for use by partially trusted code?</span></span>

<span data-ttu-id="bdbec-223">A.</span><span class="sxs-lookup"><span data-stu-id="bdbec-223">A.</span></span> <span data-ttu-id="bdbec-224">Sim, o assembly System. Data. Linq. dll está entre aqueles .NET Framework assemblies marcados com o <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atributo.</span><span class="sxs-lookup"><span data-stu-id="bdbec-224">Yes, the System.Data.Linq.dll assembly is among those .NET Framework assemblies marked with the <xref:System.Security.AllowPartiallyTrustedCallersAttribute> attribute.</span></span> <span data-ttu-id="bdbec-225">Sem essa marcação, os assemblies no .NET Framework destinam-se ao uso somente por código totalmente confiável.</span><span class="sxs-lookup"><span data-stu-id="bdbec-225">Without this marking, assemblies in the .NET Framework are intended for use only by fully trusted code.</span></span>

<span data-ttu-id="bdbec-226">O cenário principal no [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] para permitir chamadores parcialmente confiáveis é habilitar o [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] assembly a ser acessado de aplicativos Web, onde a configuração de *confiança* é média.</span><span class="sxs-lookup"><span data-stu-id="bdbec-226">The principal scenario in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] for allowing partially trusted callers is to enable the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] assembly to be accessed from Web applications, where the *trust* configuration is Medium.</span></span>

## <a name="mapping-data-from-multiple-tables"></a><span data-ttu-id="bdbec-227">Dados de mapeamento de várias tabelas</span><span class="sxs-lookup"><span data-stu-id="bdbec-227">Mapping Data from Multiple Tables</span></span>

<span data-ttu-id="bdbec-228">P.</span><span class="sxs-lookup"><span data-stu-id="bdbec-228">Q.</span></span> <span data-ttu-id="bdbec-229">Os dados na minha entidade vêm de várias tabelas.</span><span class="sxs-lookup"><span data-stu-id="bdbec-229">The data in my entity comes from multiple tables.</span></span> <span data-ttu-id="bdbec-230">Como posso mapeá-los?</span><span class="sxs-lookup"><span data-stu-id="bdbec-230">How do I map it?</span></span>

<span data-ttu-id="bdbec-231">A.</span><span class="sxs-lookup"><span data-stu-id="bdbec-231">A.</span></span> <span data-ttu-id="bdbec-232">Você pode criar uma exibição em um banco de dados e mapear a entidade para a exibição.</span><span class="sxs-lookup"><span data-stu-id="bdbec-232">You can create a view in a database and map the entity to the view.</span></span> <span data-ttu-id="bdbec-233">O [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] gera o mesmo SQL para exibições da mesma forma que faz para tabelas.</span><span class="sxs-lookup"><span data-stu-id="bdbec-233">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generates the same SQL for views as it does for tables.</span></span>

> [!NOTE]
> <span data-ttu-id="bdbec-234">O uso de exibições nesse cenário tem limitações.</span><span class="sxs-lookup"><span data-stu-id="bdbec-234">The use of views in this scenario has limitations.</span></span> <span data-ttu-id="bdbec-235">Essa abordagem funciona com mais segurança quando as operações realizadas no <xref:System.Data.Linq.Table%601> têm suporte pela exibição subjacente.</span><span class="sxs-lookup"><span data-stu-id="bdbec-235">This approach works most safely when the operations performed on <xref:System.Data.Linq.Table%601> are supported by the underlying view.</span></span> <span data-ttu-id="bdbec-236">Somente você sabe quais operações são desejadas.</span><span class="sxs-lookup"><span data-stu-id="bdbec-236">Only you know which operations are intended.</span></span> <span data-ttu-id="bdbec-237">Por exemplo, a maioria dos aplicativos são somente leitura e outro número considerável executa `Create` / / `Update` `Delete` operações somente usando procedimentos armazenados em exibições.</span><span class="sxs-lookup"><span data-stu-id="bdbec-237">For example, most applications are read-only, and another sizeable number perform `Create`/`Update`/`Delete` operations only by using stored procedures against views.</span></span>

## <a name="connection-pooling"></a><span data-ttu-id="bdbec-238">Pool de conexões</span><span class="sxs-lookup"><span data-stu-id="bdbec-238">Connection Pooling</span></span>

<span data-ttu-id="bdbec-239">P.</span><span class="sxs-lookup"><span data-stu-id="bdbec-239">Q.</span></span> <span data-ttu-id="bdbec-240">Há uma construção que possa ajudar com o pool de <xref:System.Data.Linq.DataContext>?</span><span class="sxs-lookup"><span data-stu-id="bdbec-240">Is there a construct that can help with <xref:System.Data.Linq.DataContext> pooling?</span></span>

<span data-ttu-id="bdbec-241">A.</span><span class="sxs-lookup"><span data-stu-id="bdbec-241">A.</span></span> <span data-ttu-id="bdbec-242">Não tente reutilizar instâncias do <xref:System.Data.Linq.DataContext>.</span><span class="sxs-lookup"><span data-stu-id="bdbec-242">Do not try to reuse instances of <xref:System.Data.Linq.DataContext>.</span></span> <span data-ttu-id="bdbec-243">Cada <xref:System.Data.Linq.DataContext> mantém o estado (incluindo um cache de identidade) para uma determinada sessão de edição/consulta.</span><span class="sxs-lookup"><span data-stu-id="bdbec-243">Each <xref:System.Data.Linq.DataContext> maintains state (including an identity cache) for one particular edit/query session.</span></span> <span data-ttu-id="bdbec-244">Para obter as novas instâncias com base no estado atual do banco de dados, use um novo <xref:System.Data.Linq.DataContext>.</span><span class="sxs-lookup"><span data-stu-id="bdbec-244">To obtain new instances based on the current state of the database, use a new <xref:System.Data.Linq.DataContext>.</span></span>

<span data-ttu-id="bdbec-245">Você ainda pode usar o pool de conexões ADO.NET subjacente.</span><span class="sxs-lookup"><span data-stu-id="bdbec-245">You can still use underlying ADO.NET connection pooling.</span></span> <span data-ttu-id="bdbec-246">Para obter mais informações, confira [Pooling de conexão do SQL Server (ADO.NET)](../../sql-server-connection-pooling.md).</span><span class="sxs-lookup"><span data-stu-id="bdbec-246">For more information, see [SQL Server Connection Pooling (ADO.NET)](../../sql-server-connection-pooling.md).</span></span>

## <a name="second-datacontext-is-not-updated"></a><span data-ttu-id="bdbec-247">O segundo DataContext não é atualizado</span><span class="sxs-lookup"><span data-stu-id="bdbec-247">Second DataContext Is Not Updated</span></span>

<span data-ttu-id="bdbec-248">P.</span><span class="sxs-lookup"><span data-stu-id="bdbec-248">Q.</span></span> <span data-ttu-id="bdbec-249">Eu usei uma instância do <xref:System.Data.Linq.DataContext> para armazenar valores no banco de dados.</span><span class="sxs-lookup"><span data-stu-id="bdbec-249">I used one instance of <xref:System.Data.Linq.DataContext> to store values in the database.</span></span> <span data-ttu-id="bdbec-250">No entanto, um segundo <xref:System.Data.Linq.DataContext> no mesmo banco de dados não reflete os valores atualizados.</span><span class="sxs-lookup"><span data-stu-id="bdbec-250">However, a second <xref:System.Data.Linq.DataContext> on the same database does not reflect the updated values.</span></span> <span data-ttu-id="bdbec-251">A segunda instância do <xref:System.Data.Linq.DataContext> parece retornar os valores armazenados em cache.</span><span class="sxs-lookup"><span data-stu-id="bdbec-251">The second <xref:System.Data.Linq.DataContext> instance seems to return cached values.</span></span>

<span data-ttu-id="bdbec-252">A.</span><span class="sxs-lookup"><span data-stu-id="bdbec-252">A.</span></span> <span data-ttu-id="bdbec-253">Esse comportamento é padrão.</span><span class="sxs-lookup"><span data-stu-id="bdbec-253">This behavior is by design.</span></span> <span data-ttu-id="bdbec-254">O [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] continua a retornar as mesmas instâncias/valores que você viu na primeira instância.</span><span class="sxs-lookup"><span data-stu-id="bdbec-254">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] continues to return the same instances/values that you saw in the first instance.</span></span> <span data-ttu-id="bdbec-255">Quando você faz atualizações, usa a simultaneidade otimista.</span><span class="sxs-lookup"><span data-stu-id="bdbec-255">When you make updates, you use optimistic concurrency.</span></span> <span data-ttu-id="bdbec-256">Os dados originais são usados para verificar o estado atual do banco de dados e declarar que ainda estão de fato inalterados.</span><span class="sxs-lookup"><span data-stu-id="bdbec-256">The original data is used to check against the current database state to assert that it is in fact still unchanged.</span></span> <span data-ttu-id="bdbec-257">Se eles forem alterados, um conflito ocorre e seu aplicativo deve resolvê-lo.</span><span class="sxs-lookup"><span data-stu-id="bdbec-257">If it has changed, a conflict occurs and your application must resolve it.</span></span> <span data-ttu-id="bdbec-258">Uma opção do aplicativo é redefinir o estado original para o estado atual do banco de dados e tentar novamente a atualização.</span><span class="sxs-lookup"><span data-stu-id="bdbec-258">One option of your application is to reset the original state to the current database state and to try the update again.</span></span> <span data-ttu-id="bdbec-259">Para obter mais informações, confira [Como: Gerenciar conflitos](how-to-manage-change-conflicts.md)de alterações.</span><span class="sxs-lookup"><span data-stu-id="bdbec-259">For more information, see [How to: Manage Change Conflicts](how-to-manage-change-conflicts.md).</span></span>

<span data-ttu-id="bdbec-260">Você também pode definir o <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> como falso, o que desativa o cache e o controle de alterações.</span><span class="sxs-lookup"><span data-stu-id="bdbec-260">You can also set <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> to false, which turns off caching and change tracking.</span></span> <span data-ttu-id="bdbec-261">Você pode então recuperar os valores mais recentes toda vez que consultar.</span><span class="sxs-lookup"><span data-stu-id="bdbec-261">You can then retrieve the latest values every time that you query.</span></span>

## <a name="cannot-call-submitchanges-in-read-only-mode"></a><span data-ttu-id="bdbec-262">Não é possível chamar SubmitChanges no modo somente leitura</span><span class="sxs-lookup"><span data-stu-id="bdbec-262">Cannot Call SubmitChanges in Read-only Mode</span></span>

<span data-ttu-id="bdbec-263">P.</span><span class="sxs-lookup"><span data-stu-id="bdbec-263">Q.</span></span> <span data-ttu-id="bdbec-264">Quando eu tento chamar <xref:System.Data.Linq.DataContext.SubmitChanges%2A> no modo somente leitura, obtenho um erro.</span><span class="sxs-lookup"><span data-stu-id="bdbec-264">When I try to call <xref:System.Data.Linq.DataContext.SubmitChanges%2A> in read-only mode, I get an error.</span></span>

<span data-ttu-id="bdbec-265">A.</span><span class="sxs-lookup"><span data-stu-id="bdbec-265">A.</span></span> <span data-ttu-id="bdbec-266">O modo somente leitura desativa a capacidade de o contexto controlar as alterações.</span><span class="sxs-lookup"><span data-stu-id="bdbec-266">Read-only mode turns off the ability of the context to track changes.</span></span>

## <a name="see-also"></a><span data-ttu-id="bdbec-267">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bdbec-267">See also</span></span>

- [<span data-ttu-id="bdbec-268">Referência</span><span class="sxs-lookup"><span data-stu-id="bdbec-268">Reference</span></span>](reference.md)
- [<span data-ttu-id="bdbec-269">Solução de problemas</span><span class="sxs-lookup"><span data-stu-id="bdbec-269">Troubleshooting</span></span>](troubleshooting.md)
- [<span data-ttu-id="bdbec-270">Segurança em LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="bdbec-270">Security in LINQ to SQL</span></span>](security-in-linq-to-sql.md)
