---
title: Atividades de acesso a base de dados
ms.date: 03/30/2017
ms.assetid: 174a381e-1343-46a8-a62c-7c2ae2c4f0b2
ms.openlocfilehash: efcdd25ee3e6b86d87d551623b166eab4fa76845
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/08/2018
ms.locfileid: "48850387"
---
# <a name="database-access-activities"></a><span data-ttu-id="9d32c-102">Atividades de acesso a base de dados</span><span class="sxs-lookup"><span data-stu-id="9d32c-102">Database Access Activities</span></span>
<span data-ttu-id="9d32c-103">As atividades de acesso a base de dados permitem que você acesse um base de dados em um fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="9d32c-103">Database access activities allow you to access a database within a workflow.</span></span> <span data-ttu-id="9d32c-104">Essas atividades permitem acessar bancos de dados para recuperar ou modificar as informações e usar [ADO.NET](https://go.microsoft.com/fwlink/?LinkId=166081) para acessar o banco de dados.</span><span class="sxs-lookup"><span data-stu-id="9d32c-104">These activities allow accessing databases to retrieve or modify information and use [ADO.NET](https://go.microsoft.com/fwlink/?LinkId=166081) to access the database.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="9d32c-105">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="9d32c-105">The samples may already be installed on your machine.</span></span> <span data-ttu-id="9d32c-106">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="9d32c-106">Check for the following (default) directory before continuing.</span></span>
>
>  `<InstallDrive>:\WF_WCF_Samples`
>
>  <span data-ttu-id="9d32c-107">Se este diretório não existir, vá para (página de download) Baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="9d32c-107">If this directory does not exist, go to (download page) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="9d32c-108">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="9d32c-108">This sample is located in the following directory.</span></span>
>
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\DbActivities`

## <a name="database-activities"></a><span data-ttu-id="9d32c-109">Atividades de base de dados</span><span class="sxs-lookup"><span data-stu-id="9d32c-109">Database Activities</span></span>
 <span data-ttu-id="9d32c-110">As seções a seguir detalham a lista de atividades incluídas neste exemplo.</span><span class="sxs-lookup"><span data-stu-id="9d32c-110">The following sections detail the list of activities included in this sample.</span></span>

## <a name="dbupdate"></a><span data-ttu-id="9d32c-111">DbUpdate</span><span class="sxs-lookup"><span data-stu-id="9d32c-111">DbUpdate</span></span>
 <span data-ttu-id="9d32c-112">Executa uma consulta SQL que gerencia uma alteração na base de dados (inserção, atualização, exclusão, e outras alterações).</span><span class="sxs-lookup"><span data-stu-id="9d32c-112">Executes a SQL query that produces a modification in the database (insert, update, delete, and other modifications).</span></span>

 <span data-ttu-id="9d32c-113">Essa classe executa seu trabalho de forma assíncrona (deriva de <xref:System.Activities.AsyncCodeActivity> e usa seus recursos assíncronas).</span><span class="sxs-lookup"><span data-stu-id="9d32c-113">This class performs its work asynchronously (it derives from <xref:System.Activities.AsyncCodeActivity> and uses its asynchronous capabilities).</span></span>

 <span data-ttu-id="9d32c-114">Informações de conexão pode ser configurado definindo um nome invariável do provedor (`ProviderName`) e a cadeia de conexão (`ConnectionString`) ou usando apenas um nome da cadeia de conexão (`ConfigFileSectionName`) do arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9d32c-114">The connection information can be configured by setting a provider invariant name (`ProviderName`) and the connection string (`ConnectionString`) or just using a connection string configuration name (`ConfigFileSectionName`) from the application configuration file.</span></span>

 <span data-ttu-id="9d32c-115">A consulta seja executada é configurado em sua propriedade de `Sql` e os parâmetros são passados através da coleção de `Parameters` .</span><span class="sxs-lookup"><span data-stu-id="9d32c-115">The query to be executed is configured in its `Sql` property and the parameters are passed through the `Parameters` collection.</span></span>

 <span data-ttu-id="9d32c-116">Após `DbUpdate` é executado, o número de registros afetados é retornado na propriedade de `AffectedRecords` .</span><span class="sxs-lookup"><span data-stu-id="9d32c-116">After `DbUpdate` is executed, the number of affected records is returned in the `AffectedRecords` property.</span></span>

```
Public class DbUpdate: AsyncCodeActivity
{
    [RequiredArgument]
    [OverloadGroup("ConnectionString")]
    [DefaultValue(null)]
    public InArgument<string> ProviderName { get; set; }

    [RequiredArgument]
    [OverloadGroup("ConnectionString")]
    [DependsOn("ProviderName")]
    [DefaultValue(null)]
    public InArgument<string> ConnectionString { get; set; }

    [RequiredArgument]
    [OverloadGroup("ConfigFileSectionName")]
    [DefaultValue(null)]
    public InArgument<string> ConfigName { get; set; }

    [DefaultValue(null)]
    public CommandType CommandType { get; set; }

    [RequiredArgument]
    public InArgument<string> Sql { get; set; }

    [DependsOn("Sql")]
    [DefaultValue(null)]
    public IDictionary<string, Argument> Parameters { get; }

    [DependsOn("Parameters")]
    public OutArgument<int> AffectedRecords { get; set; }
}
```

|<span data-ttu-id="9d32c-117">Argumento</span><span class="sxs-lookup"><span data-stu-id="9d32c-117">Argument</span></span>|<span data-ttu-id="9d32c-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="9d32c-118">Description</span></span>|
|-|-|
|<span data-ttu-id="9d32c-119">ProviderName</span><span class="sxs-lookup"><span data-stu-id="9d32c-119">ProviderName</span></span>|<span data-ttu-id="9d32c-120">Invariável nome do provedor ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="9d32c-120">ADO.NET provider invariant name.</span></span> <span data-ttu-id="9d32c-121">Se esse argumento é definido, então `ConnectionString` também deve ser definido.</span><span class="sxs-lookup"><span data-stu-id="9d32c-121">If this argument is set, then the `ConnectionString` must also be set.</span></span>|
|<span data-ttu-id="9d32c-122">ConnectionString</span><span class="sxs-lookup"><span data-stu-id="9d32c-122">ConnectionString</span></span>|<span data-ttu-id="9d32c-123">Cadeia de conexão para se conectar a base de dados.</span><span class="sxs-lookup"><span data-stu-id="9d32c-123">Connection string to connect to the database.</span></span> <span data-ttu-id="9d32c-124">Se esse argumento é definido, então `ProviderName` também deve ser definido.</span><span class="sxs-lookup"><span data-stu-id="9d32c-124">If this argument is set, then `ProviderName` must also be set.</span></span>|
|<span data-ttu-id="9d32c-125">ConfigName</span><span class="sxs-lookup"><span data-stu-id="9d32c-125">ConfigName</span></span>|<span data-ttu-id="9d32c-126">Nome da seção do arquivo de configuração onde as informações de conexão é armazenada.</span><span class="sxs-lookup"><span data-stu-id="9d32c-126">Name of the configuration file section where the connection information is stored.</span></span> <span data-ttu-id="9d32c-127">Quando esse argumento é ajustado `ProviderName` e `ConnectionString` não são necessários.</span><span class="sxs-lookup"><span data-stu-id="9d32c-127">When this argument is set `ProviderName` and `ConnectionString` are not required.</span></span>|
|<span data-ttu-id="9d32c-128">CommandType</span><span class="sxs-lookup"><span data-stu-id="9d32c-128">CommandType</span></span>|<span data-ttu-id="9d32c-129">Tipo de <xref:System.Data.Common.DbCommand> a ser executado.</span><span class="sxs-lookup"><span data-stu-id="9d32c-129">Type of the <xref:System.Data.Common.DbCommand> to be executed.</span></span>|
|<span data-ttu-id="9d32c-130">O SQL</span><span class="sxs-lookup"><span data-stu-id="9d32c-130">Sql</span></span>|<span data-ttu-id="9d32c-131">O comando SQL ser executado.</span><span class="sxs-lookup"><span data-stu-id="9d32c-131">The SQL command to be executed.</span></span>|
|<span data-ttu-id="9d32c-132">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9d32c-132">Parameters</span></span>|<span data-ttu-id="9d32c-133">Coleção de parâmetros de consulta SQL.</span><span class="sxs-lookup"><span data-stu-id="9d32c-133">Collection of the parameters of the SQL query.</span></span>|
|<span data-ttu-id="9d32c-134">AffectedRecords</span><span class="sxs-lookup"><span data-stu-id="9d32c-134">AffectedRecords</span></span>|<span data-ttu-id="9d32c-135">Número de registros afetados pela operação a mais recente.</span><span class="sxs-lookup"><span data-stu-id="9d32c-135">Number of records affected by the last operation.</span></span>|

## <a name="dbqueryscalar"></a><span data-ttu-id="9d32c-136">DbQueryScalar</span><span class="sxs-lookup"><span data-stu-id="9d32c-136">DbQueryScalar</span></span>
 <span data-ttu-id="9d32c-137">Executa uma consulta que recupera um único valor de base de dados.</span><span class="sxs-lookup"><span data-stu-id="9d32c-137">Executes a query that retrieves a single value from the database.</span></span>

 <span data-ttu-id="9d32c-138">Essa classe executa seu trabalho de forma assíncrona (deriva de <xref:System.Activities.AsyncCodeActivity%601> e usa seus recursos assíncronas).</span><span class="sxs-lookup"><span data-stu-id="9d32c-138">This class performs its work asynchronously (it derives from <xref:System.Activities.AsyncCodeActivity%601> and uses its asynchronous capabilities).</span></span>

 <span data-ttu-id="9d32c-139">Informações de conexão pode ser configurado definindo um nome invariável do provedor (`ProviderName`) e a cadeia de conexão (`ConnectionString`) ou usando apenas um nome da cadeia de conexão (`ConfigFileSectionName`) do arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9d32c-139">The connection information can be configured by setting a provider invariant name (`ProviderName`) and the connection string (`ConnectionString`) or just using a connection string configuration name (`ConfigFileSectionName`) from the application configuration file.</span></span>

 <span data-ttu-id="9d32c-140">A consulta seja executada é configurado em sua propriedade de `Sql` e os parâmetros são passados através da coleção de `Parameters` .</span><span class="sxs-lookup"><span data-stu-id="9d32c-140">The query to be executed is configured in its `Sql` property and the parameters are passed through the `Parameters` collection.</span></span>

 <span data-ttu-id="9d32c-141">Após `DbQueryScalar` é executado, o único é retornado na `Result``out` argumento (do tipo `TResult`, que é definido na classe base <xref:System.Activities.AsyncCodeActivity%601>).</span><span class="sxs-lookup"><span data-stu-id="9d32c-141">After `DbQueryScalar` is executed, the scalar is returned in the `Result``out` argument (of type `TResult`, that is defined in the base class <xref:System.Activities.AsyncCodeActivity%601>).</span></span>

```
public class DbQueryScalar<TResult> : AsyncCodeActivity<TResult>
{
    // public arguments
    [RequiredArgument]
    [OverloadGroup("ConnectionString")]
    [DefaultValue(null)]
    public InArgument<string> ProviderName { get; set; }

    [RequiredArgument]
    [OverloadGroup("ConnectionString")]
    [DependsOn("ProviderName")]
    [DefaultValue(null)]
    public InArgument<string> ConnectionString { get; set; }

    [RequiredArgument]
    [OverloadGroup("ConfigFileSectionName")]
    [DefaultValue(null)]
    public InArgument<string> ConfigName { get; set; }

    [DefaultValue(null)]
    public CommandType CommandType { get; set; }

    [RequiredArgument]
    public InArgument<string> Sql { get; set; }

    [DependsOn("Sql")]
    [DefaultValue(null)]
    public IDictionary<string, Argument> Parameters { get; }
}
```

|<span data-ttu-id="9d32c-142">Argumento</span><span class="sxs-lookup"><span data-stu-id="9d32c-142">Argument</span></span>|<span data-ttu-id="9d32c-143">Descrição</span><span class="sxs-lookup"><span data-stu-id="9d32c-143">Description</span></span>|
|-|-|
|<span data-ttu-id="9d32c-144">ProviderName</span><span class="sxs-lookup"><span data-stu-id="9d32c-144">ProviderName</span></span>|<span data-ttu-id="9d32c-145">Invariável nome do provedor ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="9d32c-145">ADO.NET provider invariant name.</span></span> <span data-ttu-id="9d32c-146">Se esse argumento é definido, então `ConnectionString` também deve ser definido.</span><span class="sxs-lookup"><span data-stu-id="9d32c-146">If this argument is set, then the `ConnectionString` must also be set.</span></span>|
|<span data-ttu-id="9d32c-147">ConnectionString</span><span class="sxs-lookup"><span data-stu-id="9d32c-147">ConnectionString</span></span>|<span data-ttu-id="9d32c-148">Cadeia de conexão para se conectar a base de dados.</span><span class="sxs-lookup"><span data-stu-id="9d32c-148">Connection string to connect to the database.</span></span> <span data-ttu-id="9d32c-149">Se esse argumento é definido, então `ProviderName` também deve ser definido.</span><span class="sxs-lookup"><span data-stu-id="9d32c-149">If this argument is set, then `ProviderName` must also be set.</span></span>|
|<span data-ttu-id="9d32c-150">ConfigName</span><span class="sxs-lookup"><span data-stu-id="9d32c-150">ConfigName</span></span>|<span data-ttu-id="9d32c-151">Nome da seção do arquivo de configuração onde as informações de conexão é armazenada.</span><span class="sxs-lookup"><span data-stu-id="9d32c-151">Name of the configuration file section where the connection information is stored.</span></span> <span data-ttu-id="9d32c-152">Quando esse argumento é ajustado `ProviderName` e `ConnectionString` não são necessários.</span><span class="sxs-lookup"><span data-stu-id="9d32c-152">When this argument is set `ProviderName` and `ConnectionString` are not required.</span></span>|
|<span data-ttu-id="9d32c-153">CommandType</span><span class="sxs-lookup"><span data-stu-id="9d32c-153">CommandType</span></span>|<span data-ttu-id="9d32c-154">Tipo de <xref:System.Data.Common.DbCommand> a ser executado.</span><span class="sxs-lookup"><span data-stu-id="9d32c-154">Type of the <xref:System.Data.Common.DbCommand> to be executed.</span></span>|
|<span data-ttu-id="9d32c-155">O SQL</span><span class="sxs-lookup"><span data-stu-id="9d32c-155">Sql</span></span>|<span data-ttu-id="9d32c-156">O comando SQL ser executado.</span><span class="sxs-lookup"><span data-stu-id="9d32c-156">The SQL command to be executed.</span></span>|
|<span data-ttu-id="9d32c-157">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9d32c-157">Parameters</span></span>|<span data-ttu-id="9d32c-158">Coleção de parâmetros de consulta SQL.</span><span class="sxs-lookup"><span data-stu-id="9d32c-158">Collection of the parameters of the SQL query.</span></span>|
|<span data-ttu-id="9d32c-159">Resultado</span><span class="sxs-lookup"><span data-stu-id="9d32c-159">Result</span></span>|<span data-ttu-id="9d32c-160">Escalar que é obtido depois que a consulta é executada.</span><span class="sxs-lookup"><span data-stu-id="9d32c-160">Scalar that is obtained after the query is executed.</span></span> <span data-ttu-id="9d32c-161">Esse argumento é do tipo `TResult`.</span><span class="sxs-lookup"><span data-stu-id="9d32c-161">This argument is of type `TResult`.</span></span>|

## <a name="dbquery"></a><span data-ttu-id="9d32c-162">DbQuery</span><span class="sxs-lookup"><span data-stu-id="9d32c-162">DbQuery</span></span>
 <span data-ttu-id="9d32c-163">Executa uma consulta que recupera uma lista de objetos.</span><span class="sxs-lookup"><span data-stu-id="9d32c-163">Executes a query that retrieves a list of objects.</span></span> <span data-ttu-id="9d32c-164">Depois que a consulta é executada, uma função de mapeamento é executada (pode ser <xref:System.Func%601> < `DbDataReader`, `TResult`> ou uma <xref:System.Activities.ActivityFunc%601> < `DbDataReader`, `TResult`>).</span><span class="sxs-lookup"><span data-stu-id="9d32c-164">After the query is executed, a mapping function is executed (it can be <xref:System.Func%601><`DbDataReader`, `TResult`> or an <xref:System.Activities.ActivityFunc%601><`DbDataReader`, `TResult`>).</span></span> <span data-ttu-id="9d32c-165">Essa função de mapeamento obtém um registro em `DbDataReader` e mapear-lo ao objeto a ser retornado.</span><span class="sxs-lookup"><span data-stu-id="9d32c-165">This mapping function gets a record in a `DbDataReader` and maps it to the object to be returned.</span></span>

 <span data-ttu-id="9d32c-166">Informações de conexão pode ser configurado definindo um nome invariável do provedor (`ProviderName`) e a cadeia de conexão (`ConnectionString`) ou usando apenas um nome da cadeia de conexão (`ConfigFileSectionName`) do arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9d32c-166">The connection information can be configured by setting a provider invariant name (`ProviderName`) and the connection string (`ConnectionString`) or just using a connection string configuration name (`ConfigFileSectionName`) from the application configuration file.</span></span>

 <span data-ttu-id="9d32c-167">A consulta seja executada é configurado em sua propriedade de `Sql` e os parâmetros são passados através da coleção de `Parameters` .</span><span class="sxs-lookup"><span data-stu-id="9d32c-167">The query to be executed is configured in its `Sql` property and the parameters are passed through the `Parameters` collection.</span></span>

 <span data-ttu-id="9d32c-168">Os resultados da consulta SQL são recuperados usando `DbDataReader`.</span><span class="sxs-lookup"><span data-stu-id="9d32c-168">The results of the SQL query are retrieved using a `DbDataReader`.</span></span> <span data-ttu-id="9d32c-169">A atividade itera com `DbDataReader` e mapeia as linhas em `DbDataReader` a uma instância de `TResult`.</span><span class="sxs-lookup"><span data-stu-id="9d32c-169">The activity iterates through the `DbDataReader` and maps the rows in the `DbDataReader` to an instance of `TResult`.</span></span> <span data-ttu-id="9d32c-170">O usuário do `DbQuery` tem que fornecer o código de mapeamento e isso podem ser feitos de duas maneiras: usando um <xref:System.Func%601> < `DbDataReader`, `TResult`> ou um <xref:System.Activities.ActivityFunc%601> < `DbDataReader`, `TResult`>.</span><span class="sxs-lookup"><span data-stu-id="9d32c-170">The user of `DbQuery` has to provide the mapping code and this can be done in two ways: using a <xref:System.Func%601><`DbDataReader`, `TResult`> or an <xref:System.Activities.ActivityFunc%601><`DbDataReader`, `TResult`>.</span></span> <span data-ttu-id="9d32c-171">No primeiro caso, o mapa é feito em um único pulso de execução.</span><span class="sxs-lookup"><span data-stu-id="9d32c-171">In the first case, the map is done in a single pulse of execution.</span></span> <span data-ttu-id="9d32c-172">Portanto, é mais rápido, mas isto não pode ser serializado em XAML.</span><span class="sxs-lookup"><span data-stu-id="9d32c-172">Therefore, it is faster, but this cannot be serialized to XAML.</span></span> <span data-ttu-id="9d32c-173">No último caso, o mapa é executado em vários pulsos.</span><span class="sxs-lookup"><span data-stu-id="9d32c-173">In the last case, the map is performed in multiple pulses.</span></span> <span data-ttu-id="9d32c-174">Portanto, pode ser mais lento mas pode ser serializada para XAML e ser criado declarativamente (quaisquer atividades existente pode participar no mapeamento).</span><span class="sxs-lookup"><span data-stu-id="9d32c-174">Therefore, it might be slower but can be serialized to XAML and authored declaratively (any existing activity can participate in the mapping).</span></span>

```
public class DbQuery<TResult> : AsyncCodeActivity<IList<TResult>> where TResult : class
{
    // public arguments
    [RequiredArgument]
    [OverloadGroup("ConnectionString")]
    [DefaultValue(null)]
    public InArgument<string> ProviderName { get; set; }

    [RequiredArgument]
    [OverloadGroup("ConnectionString")]
    [DependsOn("ProviderName")]
    [DefaultValue(null)]
    public InArgument<string> ConnectionString { get; set; }

    [RequiredArgument]
    [OverloadGroup("ConfigFileSectionName")]
    [DefaultValue(null)]
    public InArgument<string> ConfigName { get; set; }

    [DefaultValue(null)]
    public CommandType CommandType { get; set; }

    [RequiredArgument]
    public InArgument<string> Sql { get; set; }

    [DependsOn("Sql")]
    [DefaultValue(null)]
    public IDictionary<string, Argument> Parameters { get; }

    [OverloadGroup("DirectMapping")]
    [DefaultValue(null)]
    public Func<DbDataReader, TResult> Mapper { get; set; }

    [OverloadGroup("MultiplePulseMapping")]
    [DefaultValue(null)]
    public ActivityFunc<DbDataReader, TResult> MapperFunc { get; set; }
}
```

|<span data-ttu-id="9d32c-175">Argumento</span><span class="sxs-lookup"><span data-stu-id="9d32c-175">Argument</span></span>|<span data-ttu-id="9d32c-176">Descrição</span><span class="sxs-lookup"><span data-stu-id="9d32c-176">Description</span></span>|
|-|-|
|<span data-ttu-id="9d32c-177">ProviderName</span><span class="sxs-lookup"><span data-stu-id="9d32c-177">ProviderName</span></span>|<span data-ttu-id="9d32c-178">Invariável nome do provedor ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="9d32c-178">ADO.NET provider invariant name.</span></span> <span data-ttu-id="9d32c-179">Se esse argumento é definido, então `ConnectionString` também deve ser definido.</span><span class="sxs-lookup"><span data-stu-id="9d32c-179">If this argument is set, then the `ConnectionString` must also be set.</span></span>|
|<span data-ttu-id="9d32c-180">ConnectionString</span><span class="sxs-lookup"><span data-stu-id="9d32c-180">ConnectionString</span></span>|<span data-ttu-id="9d32c-181">Cadeia de conexão para se conectar a base de dados.</span><span class="sxs-lookup"><span data-stu-id="9d32c-181">Connection string to connect to the database.</span></span> <span data-ttu-id="9d32c-182">Se esse argumento é definido, então `ProviderName` também deve ser definido.</span><span class="sxs-lookup"><span data-stu-id="9d32c-182">If this argument is set, then `ProviderName` must also be set.</span></span>|
|<span data-ttu-id="9d32c-183">ConfigName</span><span class="sxs-lookup"><span data-stu-id="9d32c-183">ConfigName</span></span>|<span data-ttu-id="9d32c-184">Nome da seção do arquivo de configuração onde as informações de conexão é armazenada.</span><span class="sxs-lookup"><span data-stu-id="9d32c-184">Name of the configuration file section where the connection information is stored.</span></span> <span data-ttu-id="9d32c-185">Quando esse argumento é ajustado `ProviderName` e `ConnectionString` não são necessários.</span><span class="sxs-lookup"><span data-stu-id="9d32c-185">When this argument is set `ProviderName` and `ConnectionString` are not required.</span></span>|
|<span data-ttu-id="9d32c-186">CommandType</span><span class="sxs-lookup"><span data-stu-id="9d32c-186">CommandType</span></span>|<span data-ttu-id="9d32c-187">Tipo de <xref:System.Data.Common.DbCommand> a ser executado.</span><span class="sxs-lookup"><span data-stu-id="9d32c-187">Type of the <xref:System.Data.Common.DbCommand> to be executed.</span></span>|
|<span data-ttu-id="9d32c-188">O SQL</span><span class="sxs-lookup"><span data-stu-id="9d32c-188">Sql</span></span>|<span data-ttu-id="9d32c-189">O comando SQL ser executado.</span><span class="sxs-lookup"><span data-stu-id="9d32c-189">The SQL command to be executed.</span></span>|
|<span data-ttu-id="9d32c-190">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9d32c-190">Parameters</span></span>|<span data-ttu-id="9d32c-191">Coleção de parâmetros de consulta SQL.</span><span class="sxs-lookup"><span data-stu-id="9d32c-191">Collection of the parameters of the SQL query.</span></span>|
|<span data-ttu-id="9d32c-192">Mapeador</span><span class="sxs-lookup"><span data-stu-id="9d32c-192">Mapper</span></span>|<span data-ttu-id="9d32c-193">Função de mapeamento (<xref:System.Func%601><`DbDataReader`, `TResult`>) que utiliza um registro no `DataReader` obtidas como resultado da execução da consulta e retorna uma instância de um objeto do tipo `TResult` a ser adicionado para o `Result` coleção.</span><span class="sxs-lookup"><span data-stu-id="9d32c-193">Mapping function (<xref:System.Func%601><`DbDataReader`, `TResult`>) that takes a record in the `DataReader` obtained as result of executing the query and returns an instance of an object of type `TResult` to be added to the `Result` collection.</span></span><br /><br /> <span data-ttu-id="9d32c-194">Nesse caso, o mapeamento é feito em um único pulso de execução, mas não pode ser criado declarativamente usando o designer.</span><span class="sxs-lookup"><span data-stu-id="9d32c-194">In this case, mapping is done in a single pulse of execution, but it cannot be authored declaratively using the designer.</span></span>|
|<span data-ttu-id="9d32c-195">MapperFunc</span><span class="sxs-lookup"><span data-stu-id="9d32c-195">MapperFunc</span></span>|<span data-ttu-id="9d32c-196">Função de mapeamento (<xref:System.Activities.ActivityFunc%601><`DbDataReader`, `TResult`>) que utiliza um registro no `DataReader` obtidas como resultado da execução da consulta e retorna uma instância de um objeto do tipo `TResult` a ser adicionado para o `Result` coleção.</span><span class="sxs-lookup"><span data-stu-id="9d32c-196">Mapping function (<xref:System.Activities.ActivityFunc%601><`DbDataReader`, `TResult`>) that takes a record in the `DataReader` obtained as result of executing the query and returns an instance of an object of type `TResult` to be added to the `Result` collection.</span></span><br /><br /> <span data-ttu-id="9d32c-197">Nesse caso, o mapeamento é feito em vários pulsos de execução.</span><span class="sxs-lookup"><span data-stu-id="9d32c-197">In this case, the mapping is done in multiple pulses of execution.</span></span> <span data-ttu-id="9d32c-198">Essa função pode ser serializada para XAML e ser criado declarativamente (quaisquer atividades existente pode participar no mapeamento).</span><span class="sxs-lookup"><span data-stu-id="9d32c-198">This function can be serialized to XAML and authored declaratively (any existing activity can participate in the mapping).</span></span>|
|<span data-ttu-id="9d32c-199">Resultado</span><span class="sxs-lookup"><span data-stu-id="9d32c-199">Result</span></span>|<span data-ttu-id="9d32c-200">Lista de objetos obtidos como o resultado de executar a consulta e executar a função de mapeamento para cada registro em `DataReader`.</span><span class="sxs-lookup"><span data-stu-id="9d32c-200">List of objects obtained as result of executing the query and executing the mapping function for each record in the `DataReader`.</span></span>|

## <a name="dbquerydataset"></a><span data-ttu-id="9d32c-201">DbQueryDataSet</span><span class="sxs-lookup"><span data-stu-id="9d32c-201">DbQueryDataSet</span></span>
 <span data-ttu-id="9d32c-202">Executa uma consulta que retorna <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="9d32c-202">Executes a query that returns a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="9d32c-203">Essa classe executa seu trabalho de forma assíncrona.</span><span class="sxs-lookup"><span data-stu-id="9d32c-203">This class performs its work asynchronously.</span></span> <span data-ttu-id="9d32c-204">Ele deriva <xref:System.Activities.AsyncCodeActivity> < `TResult`> e usa seus recursos assíncronas.</span><span class="sxs-lookup"><span data-stu-id="9d32c-204">It derives from <xref:System.Activities.AsyncCodeActivity><`TResult`> and uses its asynchronous capabilities.</span></span>

 <span data-ttu-id="9d32c-205">Informações de conexão pode ser configurado definindo um nome invariável do provedor (`ProviderName`) e a cadeia de conexão (`ConnectionString`) ou usando apenas um nome da cadeia de conexão (`ConfigFileSectionName`) do arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9d32c-205">The connection information can be configured by setting a provider invariant name (`ProviderName`) and the connection string (`ConnectionString`) or just using a connection string configuration name (`ConfigFileSectionName`) from the application configuration file.</span></span>

 <span data-ttu-id="9d32c-206">A consulta seja executada é configurado em sua propriedade de `Sql` e os parâmetros são passados através da coleção de `Parameters` .</span><span class="sxs-lookup"><span data-stu-id="9d32c-206">The query to be executed is configured in its `Sql` property and the parameters are passed through the `Parameters` collection.</span></span>

 <span data-ttu-id="9d32c-207">Após o `DbQueryDataSet` é executado o `DataSet` é retornado na `Result``out` argumento (do tipo `TResult`, que é definido na classe base <xref:System.Activities.AsyncCodeActivity%601>).</span><span class="sxs-lookup"><span data-stu-id="9d32c-207">After the `DbQueryDataSet` is executed the `DataSet` is returned in the `Result``out` argument (of type `TResult`, that is defined in the base class <xref:System.Activities.AsyncCodeActivity%601>).</span></span>

```
public class DbQueryDataSet : AsyncCodeActivity<DataSet>
{
    // public arguments
    [RequiredArgument]
    [OverloadGroup("ConnectionString")]
    [DefaultValue(null)]
    public InArgument<string> ProviderName { get; set; }

    [RequiredArgument]
    [OverloadGroup("ConnectionString")]
    [DependsOn("ProviderName")]
    [DefaultValue(null)]
    public InArgument<string> ConnectionString { get; set; }

    [RequiredArgument]
    [OverloadGroup("ConfigFileSectionName")]
    [DefaultValue(null)]
    public InArgument<string> ConfigName { get; set; }

    [DefaultValue(null)]
    public CommandType CommandType { get; set; }

    [RequiredArgument]
    public InArgument<string> Sql { get; set; }

    [DependsOn("Sql")]
    [DefaultValue(null)]
    public IDictionary<string, Argument> Parameters { get; }
}
```

|<span data-ttu-id="9d32c-208">Argumento</span><span class="sxs-lookup"><span data-stu-id="9d32c-208">Argument</span></span>|<span data-ttu-id="9d32c-209">Descrição</span><span class="sxs-lookup"><span data-stu-id="9d32c-209">Description</span></span>|
|-|-|
|<span data-ttu-id="9d32c-210">ProviderName</span><span class="sxs-lookup"><span data-stu-id="9d32c-210">ProviderName</span></span>|<span data-ttu-id="9d32c-211">Invariável nome do provedor ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="9d32c-211">ADO.NET provider invariant name.</span></span> <span data-ttu-id="9d32c-212">Se esse argumento é definido, então `ConnectionString` também deve ser definido.</span><span class="sxs-lookup"><span data-stu-id="9d32c-212">If this argument is set, then the `ConnectionString` must also be set.</span></span>|
|<span data-ttu-id="9d32c-213">ConnectionString</span><span class="sxs-lookup"><span data-stu-id="9d32c-213">ConnectionString</span></span>|<span data-ttu-id="9d32c-214">Cadeia de conexão para se conectar a base de dados.</span><span class="sxs-lookup"><span data-stu-id="9d32c-214">Connection string to connect to the database.</span></span> <span data-ttu-id="9d32c-215">Se esse argumento é definido, então `ProviderName` também deve ser definido.</span><span class="sxs-lookup"><span data-stu-id="9d32c-215">If this argument is set, then `ProviderName` must also be set.</span></span>|
|<span data-ttu-id="9d32c-216">ConfigName</span><span class="sxs-lookup"><span data-stu-id="9d32c-216">ConfigName</span></span>|<span data-ttu-id="9d32c-217">Nome da seção do arquivo de configuração onde as informações de conexão é armazenada.</span><span class="sxs-lookup"><span data-stu-id="9d32c-217">Name of the configuration file section where the connection information is stored.</span></span> <span data-ttu-id="9d32c-218">Quando esse argumento é ajustado `ProviderName` e `ConnectionString` não são necessários.</span><span class="sxs-lookup"><span data-stu-id="9d32c-218">When this argument is set `ProviderName` and `ConnectionString` are not required.</span></span>|
|<span data-ttu-id="9d32c-219">CommandType</span><span class="sxs-lookup"><span data-stu-id="9d32c-219">CommandType</span></span>|<span data-ttu-id="9d32c-220">Tipo de <xref:System.Data.Common.DbCommand> a ser executado.</span><span class="sxs-lookup"><span data-stu-id="9d32c-220">Type of the <xref:System.Data.Common.DbCommand> to be executed.</span></span>|
|<span data-ttu-id="9d32c-221">O SQL</span><span class="sxs-lookup"><span data-stu-id="9d32c-221">Sql</span></span>|<span data-ttu-id="9d32c-222">O comando SQL ser executado.</span><span class="sxs-lookup"><span data-stu-id="9d32c-222">The SQL command to be executed.</span></span>|
|<span data-ttu-id="9d32c-223">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9d32c-223">Parameters</span></span>|<span data-ttu-id="9d32c-224">Coleção de parâmetros de consulta SQL.</span><span class="sxs-lookup"><span data-stu-id="9d32c-224">Collection of the parameters of the SQL query.</span></span>|
|<span data-ttu-id="9d32c-225">Resultado</span><span class="sxs-lookup"><span data-stu-id="9d32c-225">Result</span></span>|<span data-ttu-id="9d32c-226"><xref:System.Data.DataSet> que é obtido depois que a consulta é executada.</span><span class="sxs-lookup"><span data-stu-id="9d32c-226"><xref:System.Data.DataSet> that is obtained after the query is executed.</span></span>|

## <a name="configuring-connection-information"></a><span data-ttu-id="9d32c-227">Configurando as informações de conexão</span><span class="sxs-lookup"><span data-stu-id="9d32c-227">Configuring Connection Information</span></span>
 <span data-ttu-id="9d32c-228">Qualquer compartilhamento de DbActivities os mesmos parâmetros de configuração.</span><span class="sxs-lookup"><span data-stu-id="9d32c-228">All DbActivities share the same configuration parameters.</span></span> <span data-ttu-id="9d32c-229">Podem ser configurados em duas maneiras:</span><span class="sxs-lookup"><span data-stu-id="9d32c-229">They can be configured in two ways:</span></span>

-   <span data-ttu-id="9d32c-230">`ConnectionString + InvariantName`: Defina o nome e a cadeia de conexão invariável do provedor ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="9d32c-230">`ConnectionString + InvariantName`: Set the ADO.NET provider invariant name and connection string.</span></span>

    ```
    Activity dbSelectCount = new DbQueryScalar<DateTime>()
    {
        ProviderName = "System.Data.SqlClient",
        ConnectionString = @"Data Source=.\SQLExpress;
                             Initial Catalog=DbActivitiesSample;
                             Integrated Security=True",
        Sql = "SELECT GetDate()"
    };
    ```

-   <span data-ttu-id="9d32c-231">`ConfigName`: Defina o nome da seção de configuração que contém informações de conexão.</span><span class="sxs-lookup"><span data-stu-id="9d32c-231">`ConfigName`: Set the name of the configuration section that contains the connection information.</span></span>

    ```xml
    <connectionStrings>
        <add name="DbActivitiesSample"
             providerName="System.Data.SqlClient"
             connectionString="Data Source=.\SQLExpress;Initial Catalog=DbActivitiesSample;Integrated Security=true"/>
      </connectionStrings>
    ```

-   <span data-ttu-id="9d32c-232">Na atividade:</span><span class="sxs-lookup"><span data-stu-id="9d32c-232">In the activity:</span></span>

    ```
    Activity dbSelectCount = new DbQueryScalar<int>()
    {
        ConfigName = "DbActivitiesSample",
        Sql = "SELECT COUNT(*) FROM Roles"
    };
    ```

## <a name="running-this-sample"></a><span data-ttu-id="9d32c-233">Executando este exemplo</span><span class="sxs-lookup"><span data-stu-id="9d32c-233">Running this sample</span></span>

### <a name="setup-instructions"></a><span data-ttu-id="9d32c-234">Instruções de configuração</span><span class="sxs-lookup"><span data-stu-id="9d32c-234">Setup instructions</span></span>
 <span data-ttu-id="9d32c-235">Este exemplo usa uma base de dados.</span><span class="sxs-lookup"><span data-stu-id="9d32c-235">This sample uses a database.</span></span> <span data-ttu-id="9d32c-236">Um script de instalação e de carregamento (Setup.cmd) é fornecido com o exemplo.</span><span class="sxs-lookup"><span data-stu-id="9d32c-236">A set-up and load script (Setup.cmd) is provided with the sample.</span></span> <span data-ttu-id="9d32c-237">Você deve executar esse arquivo usando o prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="9d32c-237">You must execute that file using the command prompt.</span></span>

 <span data-ttu-id="9d32c-238">O script de Setup.cmd chama o arquivo de script CreateDb.sql, que contém os comandos SQL que façam o seguinte:</span><span class="sxs-lookup"><span data-stu-id="9d32c-238">The Setup.cmd script invokes the CreateDb.sql script file, which contains SQL commands that do the following:</span></span>

-   <span data-ttu-id="9d32c-239">Cria um base de dados chamado DbActivitiesSample.</span><span class="sxs-lookup"><span data-stu-id="9d32c-239">Creates a database called DbActivitiesSample.</span></span>

-   <span data-ttu-id="9d32c-240">Cria as funções da tabela.</span><span class="sxs-lookup"><span data-stu-id="9d32c-240">Creates the Roles table.</span></span>

-   <span data-ttu-id="9d32c-241">Cria a tabela employees.</span><span class="sxs-lookup"><span data-stu-id="9d32c-241">Creates Employees table.</span></span>

-   <span data-ttu-id="9d32c-242">Insere três registros nas funções da tabela.</span><span class="sxs-lookup"><span data-stu-id="9d32c-242">Inserts three records into the Roles table.</span></span>

-   <span data-ttu-id="9d32c-243">Insere doze registros na tabela employees.</span><span class="sxs-lookup"><span data-stu-id="9d32c-243">Inserts twelve records into the Employees table.</span></span>

##### <a name="to-run-setupcmd"></a><span data-ttu-id="9d32c-244">Para executar Setup.cmd</span><span class="sxs-lookup"><span data-stu-id="9d32c-244">To run Setup.cmd</span></span>

1.  <span data-ttu-id="9d32c-245">Abra um prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="9d32c-245">Open a command prompt.</span></span>

2.  <span data-ttu-id="9d32c-246">Vá para a pasta de DbActivities.</span><span class="sxs-lookup"><span data-stu-id="9d32c-246">Go to the DbActivities sample folder.</span></span>

3.  <span data-ttu-id="9d32c-247">Digite "Setup. cmd" e pressione ENTER.</span><span class="sxs-lookup"><span data-stu-id="9d32c-247">Type "setup.cmd" and press ENTER.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="9d32c-248">Setup.cmd tentar instalar o exemplo em sua instância de SqlExpress do computador local.</span><span class="sxs-lookup"><span data-stu-id="9d32c-248">Setup.cmd attempts to install the sample in your local machine SqlExpress instance.</span></span> <span data-ttu-id="9d32c-249">Se você deseja instalá-lo em outra instância do SQL server, a edição Setup.cmd com o novo nome da instância.</span><span class="sxs-lookup"><span data-stu-id="9d32c-249">If you want to install it in other SQL server instance, edit Setup.cmd with the new instance name.</span></span>

##### <a name="to-uninstall-the-sample-database"></a><span data-ttu-id="9d32c-250">Para desinstalar o base de dados de exemplo</span><span class="sxs-lookup"><span data-stu-id="9d32c-250">To uninstall the sample database</span></span>

1.  <span data-ttu-id="9d32c-251">Executar Cleanup.cmd da pasta de exemplo em um prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="9d32c-251">Run Cleanup.cmd from the sample folder in a command prompt.</span></span>

##### <a name="to-run-the-sample"></a><span data-ttu-id="9d32c-252">Para executar a amostra</span><span class="sxs-lookup"><span data-stu-id="9d32c-252">To run the sample</span></span>

1.  <span data-ttu-id="9d32c-253">Abra a solução no Visual Studio 2010</span><span class="sxs-lookup"><span data-stu-id="9d32c-253">Open the solution in Visual Studio 2010</span></span>

2.  <span data-ttu-id="9d32c-254">Para criar a solução, pressione CTRL+SHIFT+B.</span><span class="sxs-lookup"><span data-stu-id="9d32c-254">To compile the solution, press CTRL+SHIFT+B.</span></span>

3.  <span data-ttu-id="9d32c-255">Para executar o exemplo sem depuração, pressione CTRL+F5.</span><span class="sxs-lookup"><span data-stu-id="9d32c-255">To run the sample without debugging, press CTRL+F5.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="9d32c-256">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="9d32c-256">The samples may already be installed on your machine.</span></span> <span data-ttu-id="9d32c-257">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="9d32c-257">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="9d32c-258">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="9d32c-258">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="9d32c-259">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="9d32c-259">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\DbActivities`
