---
title: 'Instruções passo a passo: acessando um banco de dados SQL por meio de provedores de tipos (F#)'
description: 'Saiba como usar o provedor de tipos SqlDataConnection (LINQ to SQL) em F # 3.0 para gerar tipos para um banco de dados SQL quando você tem uma conexão de banco de dados ao vivo.'
keywords: visual f#, f#, programação funcional
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 1c413eb0-16a5-4c1a-9a4e-ad6877e645d6
ms.openlocfilehash: dbc5d889fb7883b4327180fdf34accf45bf519e7
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/10/2018
---
# <a name="walkthrough-accessing-a-sql-database-by-using-type-providers"></a><span data-ttu-id="f923c-104">Instruções passo a passo: acessando um banco de dados SQL por meio de provedores de tipos</span><span class="sxs-lookup"><span data-stu-id="f923c-104">Walkthrough: Accessing a SQL Database by Using Type Providers</span></span>

> [!NOTE]
<span data-ttu-id="f923c-105">Este guia foi escrito para F # 3.0 e será atualizado.</span><span class="sxs-lookup"><span data-stu-id="f923c-105">This guide was written for F# 3.0 and will be updated.</span></span>  <span data-ttu-id="f923c-106">Consulte [FSharp.Data](https://fsharp.github.io/FSharp.Data/) para provedores de tipo de plataforma cruzada atualizados.</span><span class="sxs-lookup"><span data-stu-id="f923c-106">See [FSharp.Data](https://fsharp.github.io/FSharp.Data/) for up-to-date, cross-platform type providers.</span></span>

> [!NOTE]
<span data-ttu-id="f923c-107">Os links de referência de API levará você para o MSDN.</span><span class="sxs-lookup"><span data-stu-id="f923c-107">The API reference links will take you to MSDN.</span></span>  <span data-ttu-id="f923c-108">A referência da API docs.microsoft.com não está completa.</span><span class="sxs-lookup"><span data-stu-id="f923c-108">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="f923c-109">Este passo a passo explica como usar o provedor de tipos SqlDataConnection (LINQ to SQL) que está disponível em F # 3.0 para gerar tipos de dados em um banco de dados SQL quando você tem uma conexão ao vivo para um banco de dados.</span><span class="sxs-lookup"><span data-stu-id="f923c-109">This walkthrough explains how to use the SqlDataConnection (LINQ to SQL) type provider that is available in F# 3.0 to generate types for data in a SQL database when you have a live connection to a database.</span></span> <span data-ttu-id="f923c-110">Se você não tiver uma conexão ao vivo para um banco de dados, mas você tem um LINQ para SQL esquema (arquivo DBML), consulte [passo a passo: gerando tipos F # em um arquivo DBML](generating-fsharp-types-from-dbml.md).</span><span class="sxs-lookup"><span data-stu-id="f923c-110">If you do not have a live connection to a database, but you do have a LINQ to SQL schema file (DBML file), see [Walkthrough: Generating F# Types from a DBML File](generating-fsharp-types-from-dbml.md).</span></span>

<span data-ttu-id="f923c-111">Esta explicação passo a passo mostra as seguintes tarefas.</span><span class="sxs-lookup"><span data-stu-id="f923c-111">This walkthrough illustrates the following tasks.</span></span> <span data-ttu-id="f923c-112">Essas tarefas devem ser executadas nesta ordem para a passo a passo para ter êxito:</span><span class="sxs-lookup"><span data-stu-id="f923c-112">These tasks must be performed in this order for the walkthrough to succeed:</span></span>


- <span data-ttu-id="f923c-113">Preparar um banco de dados de teste</span><span class="sxs-lookup"><span data-stu-id="f923c-113">Preparing a test database</span></span>

- <span data-ttu-id="f923c-114">Criando o projeto</span><span class="sxs-lookup"><span data-stu-id="f923c-114">Creating the project</span></span>

- <span data-ttu-id="f923c-115">Configurando um provedor de tipos</span><span class="sxs-lookup"><span data-stu-id="f923c-115">Setting up a type provider</span></span>

- <span data-ttu-id="f923c-116">Consultando os dados</span><span class="sxs-lookup"><span data-stu-id="f923c-116">Querying the data</span></span>

- <span data-ttu-id="f923c-117">Trabalhando com campos anuláveis</span><span class="sxs-lookup"><span data-stu-id="f923c-117">Working with nullable fields</span></span>

- <span data-ttu-id="f923c-118">Chamando um procedimento armazenado</span><span class="sxs-lookup"><span data-stu-id="f923c-118">Calling a stored procedure</span></span>

- <span data-ttu-id="f923c-119">Atualizando o banco de dados</span><span class="sxs-lookup"><span data-stu-id="f923c-119">Updating the database</span></span>

- <span data-ttu-id="f923c-120">Execução de código Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="f923c-120">Executing Transact-SQL code</span></span>

- <span data-ttu-id="f923c-121">Usando o contexto de dados completo</span><span class="sxs-lookup"><span data-stu-id="f923c-121">Using the full data context</span></span>

- <span data-ttu-id="f923c-122">Excluindo dados</span><span class="sxs-lookup"><span data-stu-id="f923c-122">Deleting data</span></span>

- <span data-ttu-id="f923c-123">Criar um banco de dados de teste (conforme necessário)</span><span class="sxs-lookup"><span data-stu-id="f923c-123">Create a test database (as needed)</span></span>

## <a name="preparing-a-test-database"></a><span data-ttu-id="f923c-124">Preparar um banco de dados de teste</span><span class="sxs-lookup"><span data-stu-id="f923c-124">Preparing a Test Database</span></span>
<span data-ttu-id="f923c-125">Em um servidor que executa o SQL Server, crie um banco de dados para fins de teste.</span><span class="sxs-lookup"><span data-stu-id="f923c-125">On a server that's running SQL Server, create a database for testing purposes.</span></span> <span data-ttu-id="f923c-126">Você pode usar o banco de dados criar script na parte inferior desta página, na seção [criando um banco de dados de teste](#creating-a-test-database) para fazer isso.</span><span class="sxs-lookup"><span data-stu-id="f923c-126">You can use the database create script at the bottom of this page in the section [Creating a test database](#creating-a-test-database) to do this.</span></span>


#### <a name="to-prepare-a-test-database"></a><span data-ttu-id="f923c-127">Para preparar um banco de dados de teste</span><span class="sxs-lookup"><span data-stu-id="f923c-127">To prepare a test database</span></span>

<span data-ttu-id="f923c-128">Para executar o Script de criar MyDatabase, abra o **exibição** menu e, em seguida, escolha **Pesquisador de objetos do SQL Server** ou escolha Ctrl +\, teclas Ctrl + S.</span><span class="sxs-lookup"><span data-stu-id="f923c-128">To run the MyDatabase Create Script, open the **View** menu, and then choose **SQL Server Object Explorer** or choose the Ctrl+\, Ctrl+S keys.</span></span> <span data-ttu-id="f923c-129">Em **Pesquisador de objetos do SQL Server** janela, abra o menu de atalho para a instância apropriada, escolha **nova consulta**, copie o script na parte inferior desta página e, em seguida, cole o script no editor.</span><span class="sxs-lookup"><span data-stu-id="f923c-129">In **SQL Server Object Explorer** window, open the shortcut menu for the appropriate instance, choose **New Query**, copy the script at the bottom of this page, and then paste the script into the editor.</span></span> <span data-ttu-id="f923c-130">Para executar o script SQL, escolha o ícone da barra de ferramentas com o símbolo triangular ou escolha as teclas Ctrl + Q.</span><span class="sxs-lookup"><span data-stu-id="f923c-130">To run the SQL script, choose the toolbar icon with the triangular symbol, or choose the Ctrl+Q keys.</span></span> <span data-ttu-id="f923c-131">Para obter mais informações sobre **Pesquisador de objetos do SQL Server**, consulte [desenvolvimento de banco de dados conectado](https://msdn.microsoft.com/library/hh272679(VS.103).aspx).</span><span class="sxs-lookup"><span data-stu-id="f923c-131">For more information about **SQL Server Object Explorer**, see [Connected Database Development](https://msdn.microsoft.com/library/hh272679(VS.103).aspx).</span></span>


## <a name="creating-the-project"></a><span data-ttu-id="f923c-132">Criando o projeto</span><span class="sxs-lookup"><span data-stu-id="f923c-132">Creating the project</span></span>
<span data-ttu-id="f923c-133">Em seguida, você pode criar um projeto de aplicativo do F #.</span><span class="sxs-lookup"><span data-stu-id="f923c-133">Next, you create an F# application project.</span></span>


#### <a name="to-create-and-set-up-the-project"></a><span data-ttu-id="f923c-134">Criar e configurar o projeto</span><span class="sxs-lookup"><span data-stu-id="f923c-134">To create and set up the project</span></span>

1. <span data-ttu-id="f923c-135">Crie um novo projeto de aplicativo do F #.</span><span class="sxs-lookup"><span data-stu-id="f923c-135">Create a new F# Application project.</span></span>

2. <span data-ttu-id="f923c-136">Adicione referências a [FSharp.Data.TypeProviders](https://msdn.microsoft.com/library/a858f859-047a-44ab-945b-8731d7a0e6e3), bem como `System.Data`, e `System.Data.Linq`.</span><span class="sxs-lookup"><span data-stu-id="f923c-136">Add references to [FSharp.Data.TypeProviders](https://msdn.microsoft.com/library/a858f859-047a-44ab-945b-8731d7a0e6e3), as well as `System.Data`, and `System.Data.Linq`.</span></span>

3. <span data-ttu-id="f923c-137">Abra os namespaces apropriados, adicionando as seguintes linhas de código para a parte superior do seu arquivo de código F # Program.fs.</span><span class="sxs-lookup"><span data-stu-id="f923c-137">Open the appropriate namespaces by adding the following lines of code to the top of your F# code file Program.fs.</span></span>

  ```fsharp
open System
open System.Data
open System.Data.Linq
open Microsoft.FSharp.Data.TypeProviders
open Microsoft.FSharp.Linq
```

4. <span data-ttu-id="f923c-138">Assim como acontece com a maioria dos programas F #, você pode executar o código neste passo a passo como um programa compilado ou isso pode ser executado interativamente como um script.</span><span class="sxs-lookup"><span data-stu-id="f923c-138">As with most F# programs, you can execute the code in this walkthrough as a compiled program, or you can run it interactively as a script.</span></span> <span data-ttu-id="f923c-139">Se você preferir usar scripts, abra o menu de atalho para o nó do projeto, selecione **Adicionar Novo Item**, adicione um arquivo de script F # e adicione o código de cada etapa no script.</span><span class="sxs-lookup"><span data-stu-id="f923c-139">If you prefer to use scripts, open the shortcut menu for the project node, select **Add New Item**, add an F# script file, and add the code in each step to the script.</span></span> <span data-ttu-id="f923c-140">Você precisará adicionar as seguintes linhas na parte superior do arquivo para carregar as referências de assembly.</span><span class="sxs-lookup"><span data-stu-id="f923c-140">You will need to add the following lines at the top of the file to load the assembly references.</span></span>

  ```fsharp
#r "System.Data.dll"
#r "FSharp.Data.TypeProviders.dll"
#r "System.Data.Linq.dll"
```

  <span data-ttu-id="f923c-141">Você pode selecionar cada bloco de código e adicioná-lo e pressione Alt + Enter para executá-lo no F # interativo.</span><span class="sxs-lookup"><span data-stu-id="f923c-141">You can then select each block of code as you add it and press Alt+Enter to run it in F# Interactive.</span></span>

## <a name="setting-up-a-type-provider"></a><span data-ttu-id="f923c-142">Configurando um provedor de tipos</span><span class="sxs-lookup"><span data-stu-id="f923c-142">Setting up a type provider</span></span>
<span data-ttu-id="f923c-143">Nesta etapa, você pode criar um provedor de tipos para o esquema de banco de dados.</span><span class="sxs-lookup"><span data-stu-id="f923c-143">In this step, you create a type provider for your database schema.</span></span>


#### <a name="to-set-up-the-type-provider-from-a-direct-database-connection"></a><span data-ttu-id="f923c-144">Para configurar o provedor de tipo de uma conexão direta do banco de dados</span><span class="sxs-lookup"><span data-stu-id="f923c-144">To set up the type provider from a direct database connection</span></span>

<span data-ttu-id="f923c-145">Há duas linhas críticas de código que você precisa para criar os tipos que você pode usar para consultar um banco de dados SQL usando o provedor de tipo.</span><span class="sxs-lookup"><span data-stu-id="f923c-145">There are two critical lines of code that you need in order to create the types that you can use to query a SQL database using the type provider.</span></span> <span data-ttu-id="f923c-146">Primeiro, você pode instanciar o provedor de tipos.</span><span class="sxs-lookup"><span data-stu-id="f923c-146">First, you instantiate the type provider.</span></span> <span data-ttu-id="f923c-147">Para fazer isso, crie a aparência de uma abreviação de tipo de um `SqlDataConnection` com um parâmetro genérico estático.</span><span class="sxs-lookup"><span data-stu-id="f923c-147">To do this, create what looks like a type abbreviation for a `SqlDataConnection` with a static generic parameter.</span></span> <span data-ttu-id="f923c-148">`SqlDataConnection` é um provedor de tipo SQL e não deve ser confundido com `SqlConnection` tipo que é usado na programação do ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="f923c-148">`SqlDataConnection` is a SQL type provider, and should not be confused with `SqlConnection` type that is used in ADO.NET programming.</span></span> <span data-ttu-id="f923c-149">Se você tiver um banco de dados que você deseja se conectar e ter uma cadeia de caracteres de conexão, use o seguinte código para chamar o provedor de tipo.</span><span class="sxs-lookup"><span data-stu-id="f923c-149">If you have a database that you want to connect to, and have a connection string, use the following code to invoke the type provider.</span></span> <span data-ttu-id="f923c-150">Substitua por sua própria cadeia de caracteres de conexão para a cadeia de caracteres de exemplo fornecida.</span><span class="sxs-lookup"><span data-stu-id="f923c-150">Substitute your own connection string for the example string given.</span></span> <span data-ttu-id="f923c-151">Por exemplo, se seu servidor MYSERVER e a instância de banco de dados é a instância, o nome do banco de dados é MyDatabase, e você deseja usar a autenticação do Windows para acessar o banco de dados e, em seguida, a cadeia de caracteres de conexão seria como fornecido no código de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="f923c-151">For example, if your server is MYSERVER and the database instance is INSTANCE, the database name is MyDatabase, and you want to use Windows Authentication to access the database, then the connection string would be as given in the following example code.</span></span>

```fsharp
type dbSchema = SqlDataConnection<"Data Source=MYSERVER\INSTANCE;Initial Catalog=MyDatabase;Integrated Security=SSPI;">
let db = dbSchema.GetDataContext()

// Enable the logging of database activity to the console.
db.DataContext.Log <- System.Console.Out
```

<span data-ttu-id="f923c-152">Agora você tem um tipo, `dbSchema`, que é um tipo de pai que contém todos os tipos gerados que representam as tabelas de banco de dados.</span><span class="sxs-lookup"><span data-stu-id="f923c-152">Now you have a type, `dbSchema`, which is a parent type that contains all the generated types that represent database tables.</span></span> <span data-ttu-id="f923c-153">Você também tem um objeto `db`, que tenha como seus membros todas as tabelas no banco de dados.</span><span class="sxs-lookup"><span data-stu-id="f923c-153">You also have an object, `db`, which has as its members all the tables in the database.</span></span> <span data-ttu-id="f923c-154">Os nomes de tabela são propriedades e o tipo dessas propriedades é gerado pelo compilador F #.</span><span class="sxs-lookup"><span data-stu-id="f923c-154">The table names are properties, and the type of these properties is generated by the F# compiler.</span></span> <span data-ttu-id="f923c-155">Os tipos de si mesmos aparecem como tipos aninhados em `dbSchema.ServiceTypes`.</span><span class="sxs-lookup"><span data-stu-id="f923c-155">The types themselves appear as nested types under `dbSchema.ServiceTypes`.</span></span> <span data-ttu-id="f923c-156">Portanto, quaisquer dados recuperados para linhas dessas tabelas serão uma instância do tipo apropriado que foi gerado para aquela tabela.</span><span class="sxs-lookup"><span data-stu-id="f923c-156">Therefore, any data retrieved for rows of these tables is an instance of the appropriate type that was generated for that table.</span></span> <span data-ttu-id="f923c-157">É o nome do tipo `ServiceTypes.Table1`.</span><span class="sxs-lookup"><span data-stu-id="f923c-157">The name of the type is `ServiceTypes.Table1`.</span></span>

<span data-ttu-id="f923c-158">Para se familiarizar com como a linguagem F # interpreta consultas em consultas SQL, examine a linha que define o `Log` propriedade no contexto de dados.</span><span class="sxs-lookup"><span data-stu-id="f923c-158">To familiarize yourself with how the F# language interprets queries into SQL queries, review the line that sets the `Log` property on the data context.</span></span>

<span data-ttu-id="f923c-159">Para explorar os tipos criados pelo provedor de tipo, adicione o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="f923c-159">To further explore the types created by the type provider, add the following code.</span></span>

```fsharp
let table1 = db.Table1
```

<span data-ttu-id="f923c-160">Passe o mouse sobre `table1` para ver seu tipo.</span><span class="sxs-lookup"><span data-stu-id="f923c-160">Hover over `table1` to see its type.</span></span> <span data-ttu-id="f923c-161">Seu tipo é `System.Data.Linq.Table<dbSchema.ServiceTypes.Table1>` e o argumento genérico implica que o tipo de cada linha é o tipo gerado, `dbSchema.ServiceTypes.Table1`.</span><span class="sxs-lookup"><span data-stu-id="f923c-161">Its type is `System.Data.Linq.Table<dbSchema.ServiceTypes.Table1>` and the generic argument implies that the type of each row is the generated type, `dbSchema.ServiceTypes.Table1`.</span></span> <span data-ttu-id="f923c-162">O compilador cria um tipo semelhante para cada tabela no banco de dados.</span><span class="sxs-lookup"><span data-stu-id="f923c-162">The compiler creates a similar type for each table in the database.</span></span>

## <a name="querying-the-data"></a><span data-ttu-id="f923c-163">Consultando os dados</span><span class="sxs-lookup"><span data-stu-id="f923c-163">Querying the data</span></span>
<span data-ttu-id="f923c-164">Nesta etapa, você escreve uma consulta usando expressões de consulta do F #.</span><span class="sxs-lookup"><span data-stu-id="f923c-164">In this step, you write a query using F# query expressions.</span></span>


#### <a name="to-query-the-data"></a><span data-ttu-id="f923c-165">Para consultar os dados</span><span class="sxs-lookup"><span data-stu-id="f923c-165">To query the data</span></span>

1. <span data-ttu-id="f923c-166">Agora, crie uma consulta para essa tabela no banco de dados.</span><span class="sxs-lookup"><span data-stu-id="f923c-166">Now create a query for that table in the database.</span></span> <span data-ttu-id="f923c-167">Adicione o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="f923c-167">Add the following code.</span></span>

  ```fsharp
   let query1 =
     query {
       for row in db.Table1 do
       select row
     }
   query1 |> Seq.iter (fun row -> printfn "%s %d" row.Name row.TestData1)
```

  <span data-ttu-id="f923c-168">A aparência da palavra `query` indica que esta é uma expressão de consulta, um tipo de expressão de computação que gera um conjunto de resultados semelhantes de uma consulta de banco de dados típico.</span><span class="sxs-lookup"><span data-stu-id="f923c-168">The appearance of the word `query` indicates that this is a query expression, a type of computation expression that generates a collection of results similar of a typical database query.</span></span> <span data-ttu-id="f923c-169">Se você focaliza a consulta, você verá que ele é uma instância de [classe LINQ. querybuilder](https://msdn.microsoft.com/visualfsharpdocs/conceptual/linq.querybuilder-class-%5bfsharp%5d), um tipo que define a expressão de computação de consulta.</span><span class="sxs-lookup"><span data-stu-id="f923c-169">If you hover over query, you will see that it is an instance of [Linq.QueryBuilder Class](https://msdn.microsoft.com/visualfsharpdocs/conceptual/linq.querybuilder-class-%5bfsharp%5d), a type that defines the query computation expression.</span></span> <span data-ttu-id="f923c-170">Se você focalizar `query1`, você verá que ele é uma instância de `System.Linq.IQueryable`.</span><span class="sxs-lookup"><span data-stu-id="f923c-170">If you hover over `query1`, you will see that it is an instance of `System.Linq.IQueryable`.</span></span> <span data-ttu-id="f923c-171">Como o nome sugere, `System.Linq.IQueryable` representa os dados que podem ser consultados, não o resultado de uma consulta.</span><span class="sxs-lookup"><span data-stu-id="f923c-171">As the name suggests, `System.Linq.IQueryable` represents data that may be queried, not the result of a query.</span></span> <span data-ttu-id="f923c-172">Uma consulta está sujeita a avaliação lenta, o que significa que o banco de dados só é consultado quando a consulta é avaliada.</span><span class="sxs-lookup"><span data-stu-id="f923c-172">A query is subject to lazy evaluation, which means that the database is only queried when the query is evaluated.</span></span> <span data-ttu-id="f923c-173">A linha final passa a consulta por meio de `Seq.iter`.</span><span class="sxs-lookup"><span data-stu-id="f923c-173">The final line passes the query through `Seq.iter`.</span></span> <span data-ttu-id="f923c-174">As consultas são enumeráveis e podem ser iteradas como sequências.</span><span class="sxs-lookup"><span data-stu-id="f923c-174">Queries are enumerable and may be iterated like sequences.</span></span> <span data-ttu-id="f923c-175">Para obter mais informações, consulte [expressões de consulta](../../language-reference/query-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="f923c-175">For more information, see [Query Expressions](../../language-reference/query-expressions.md).</span></span>

2. <span data-ttu-id="f923c-176">Agora, adicione um operador de consulta à consulta.</span><span class="sxs-lookup"><span data-stu-id="f923c-176">Now add a query operator to the query.</span></span> <span data-ttu-id="f923c-177">Há um número de operadores de consulta disponíveis que você pode usar para construir consultas mais complexas.</span><span class="sxs-lookup"><span data-stu-id="f923c-177">There are a number of query operators available that you can use to construct more complex queries.</span></span> <span data-ttu-id="f923c-178">Este exemplo também mostra que você pode eliminar a variável de consulta e use um operador de pipeline em vez disso.</span><span class="sxs-lookup"><span data-stu-id="f923c-178">This example also shows that you can eliminate the query variable and use a pipeline operator instead.</span></span>

  ```fsharp
   query {
     for row in db.Table1 do
     where (row.TestData1 > 2)
     select row
   } |> Seq.iter (fun row -> printfn "%d %s" row.TestData1 row.Name)
```

3. <span data-ttu-id="f923c-179">Adicione uma consulta mais complexa com uma junção de duas tabelas.</span><span class="sxs-lookup"><span data-stu-id="f923c-179">Add a more complex query with a join of two tables.</span></span>

  ```fsharp
   query {
     for row1 in db.Table1 do
     join row2 in db.Table2 on (row1.Id = row2.Id)
     select (row1, row2)
   } |> Seq.iteri (fun index (row1, row2) ->
                   if (index = 0) then printfn "Table1.Id TestData1 TestData2 Name Table2.Id TestData1 TestData2 Name"
                   printfn "%d %d %f %s %d %d %f %s" row1.Id row1.TestData1 row1.TestData2 row1.Name
                     row2.Id (row2.TestData1.GetValueOrDefault()) (row2.TestData2.GetValueOrDefault()) row2.Name)
```

4. <span data-ttu-id="f923c-180">No código do mundo real, os parâmetros na consulta são geralmente valores ou variáveis, constantes de tempo de compilação não.</span><span class="sxs-lookup"><span data-stu-id="f923c-180">In real-world code, the parameters in your query are usually values or variables, not compile-time constants.</span></span> <span data-ttu-id="f923c-181">Adicione o seguinte código que encapsula uma consulta em uma função que aceita um parâmetro e, em seguida, chama a função com valor de 10.</span><span class="sxs-lookup"><span data-stu-id="f923c-181">Add the following code that wraps a query in a function that takes a parameter, and then calls that function with the value 10.</span></span>

  ```fsharp
   let findData param =
     query {
       for row in db.Table1 do
       where (row.TestData1 = param)
       select row
     }

   findData 10 |> Seq.iter (fun row -> printfn "Found row: %d %d %f %s" row.Id row.TestData1 row.TestData2 row.Name)
```

## <a name="working-with-nullable-fields"></a><span data-ttu-id="f923c-182">Trabalhando com campos anuláveis</span><span class="sxs-lookup"><span data-stu-id="f923c-182">Working with nullable fields</span></span>
<span data-ttu-id="f923c-183">Em bancos de dados, os campos geralmente permitem valores nulos.</span><span class="sxs-lookup"><span data-stu-id="f923c-183">In databases, fields often allow null values.</span></span> <span data-ttu-id="f923c-184">No sistema de tipo .NET, você não pode usar os tipos de dados numérico comum para dados que permite valores nulos porque esses tipos não têm nulo como um valor possível.</span><span class="sxs-lookup"><span data-stu-id="f923c-184">In the .NET type system, you cannot use the ordinary numerical data types for data that allows nulls because those types do not have null as a possible value.</span></span> <span data-ttu-id="f923c-185">Portanto, esses valores são representados por instâncias do `System.Nullable` tipo.</span><span class="sxs-lookup"><span data-stu-id="f923c-185">Therefore, these values are represented by instances of `System.Nullable` type.</span></span> <span data-ttu-id="f923c-186">Em vez de acessar o valor desses campos diretamente com o nome do campo, você precisa adicionar algumas etapas adicionais.</span><span class="sxs-lookup"><span data-stu-id="f923c-186">Instead of accessing the value of such fields directly with the name of the field, you need to add some extra steps.</span></span> <span data-ttu-id="f923c-187">Você pode usar o `System.Nullable.Value` propriedade para acessar o valor subjacente de um tipo anulável.</span><span class="sxs-lookup"><span data-stu-id="f923c-187">You can use the `System.Nullable.Value` property to access the underlying value of a nullable type.</span></span> <span data-ttu-id="f923c-188">O `System.Nullable.Value` propriedade gera uma exceção se o objeto é nulo em vez de um valor.</span><span class="sxs-lookup"><span data-stu-id="f923c-188">The `System.Nullable.Value` property throws an exception if the object is null rather than having a value.</span></span> <span data-ttu-id="f923c-189">Você pode usar o `System.Nullable.HasValue` método booliano para determinar se existe um valor ou use `System.Nullable.GetValueOrDefault()` para garantir que você tenha um valor real em todos os casos.</span><span class="sxs-lookup"><span data-stu-id="f923c-189">You can use the `System.Nullable.HasValue` Boolean method to determine if a value exists, or use `System.Nullable.GetValueOrDefault()` to ensure that you have an actual value in all cases.</span></span> <span data-ttu-id="f923c-190">Se você usar `System.Nullable.GetValueOrDefault()` e houver um valor nulo no banco de dados, ele será substituído com um valor como uma cadeia de caracteres vazia para tipos de cadeia de caracteres, 0 para tipos integrais 0,0 para flutuante ponto ou tipos.</span><span class="sxs-lookup"><span data-stu-id="f923c-190">If you use `System.Nullable.GetValueOrDefault()` and there is a null in the database, then it is replaced with a value such as an empty string for string types, 0 for integral types or 0.0 for floating point types.</span></span>

<span data-ttu-id="f923c-191">Quando você precisa executar testes de igualdade ou comparações em valores anuláveis em um `where` cláusula em uma consulta, você pode usar os operadores permitem valor nulos encontrados na [módulo LINQ. nullableoperators](https://msdn.microsoft.com/visualfsharpdocs/conceptual/linq.nullableoperators-module-%5bfsharp%5d).</span><span class="sxs-lookup"><span data-stu-id="f923c-191">When you need to perform equality tests or comparisons on nullable values in a `where` clause in a query, you can use the nullable operators found in the [Linq.NullableOperators Module](https://msdn.microsoft.com/visualfsharpdocs/conceptual/linq.nullableoperators-module-%5bfsharp%5d).</span></span> <span data-ttu-id="f923c-192">Esses são como os operadores de comparação regular `=`, `>`, `<=`e assim por diante, exceto que um ponto de interrogação é exibido à esquerda ou à direita do operador onde estão os valores nulos.</span><span class="sxs-lookup"><span data-stu-id="f923c-192">These are like the regular comparison operators `=`, `>`, `<=`, and so on, except that a question mark appears on the left or right of the operator where the nullable values are.</span></span> <span data-ttu-id="f923c-193">Por exemplo, o operador `>?` é maior-que o operador com um valor nulo à direita.</span><span class="sxs-lookup"><span data-stu-id="f923c-193">For example, the operator `>?` is a greater-than operator with a nullable value on the right.</span></span> <span data-ttu-id="f923c-194">A maneira como esses operadores trabalha é que, se ambos os lados da expressão for null, a expressão é avaliada como `false`.</span><span class="sxs-lookup"><span data-stu-id="f923c-194">The way these operators work is that if either side of the expression is null, the expression evaluates to `false`.</span></span> <span data-ttu-id="f923c-195">Em um `where` cláusula, isso geralmente significa que as linhas que contêm campos nulos não são selecionadas e não retornadas nos resultados da consulta.</span><span class="sxs-lookup"><span data-stu-id="f923c-195">In a `where` clause, this generally means that the rows that contain null fields are not selected and not returned in the query results.</span></span>


#### <a name="to-work-with-nullable-fields"></a><span data-ttu-id="f923c-196">Para trabalhar com campos anuláveis</span><span class="sxs-lookup"><span data-stu-id="f923c-196">To work with nullable fields</span></span>

<span data-ttu-id="f923c-197">O código a seguir mostra o trabalho com valores anuláveis. Suponha que **TestData1** é um campo de número inteiro que permite valores nulos.</span><span class="sxs-lookup"><span data-stu-id="f923c-197">The following code shows working with nullable values; assume that **TestData1** is an integer field that allows nulls.</span></span>

```fsharp
query {
  for row in db.Table2 do
  where (row.TestData1.HasValue && row.TestData1.Value > 2)
  select row
} |> Seq.iter (fun row -> printfn "%d %s" row.TestData1.Value row.Name)

query {
  for row in db.Table2 do
  // Use a nullable operator ?>
  where (row.TestData1 ?> 2)
  select row
} |> Seq.iter (fun row -> printfn "%d %s" (row.TestData1.GetValueOrDefault()) row.Name)
```

## <a name="calling-a-stored-procedure"></a><span data-ttu-id="f923c-198">Chamando um procedimento armazenado</span><span class="sxs-lookup"><span data-stu-id="f923c-198">Calling a stored procedure</span></span>
<span data-ttu-id="f923c-199">Todos os procedimentos armazenados no banco de dados podem ser chamados do F #.</span><span class="sxs-lookup"><span data-stu-id="f923c-199">Any stored procedures on the database can be called from F#.</span></span> <span data-ttu-id="f923c-200">Você deve definir o parâmetro static `StoredProcedures` para `true` em uma instância de provedor de tipo.</span><span class="sxs-lookup"><span data-stu-id="f923c-200">You must set the static parameter `StoredProcedures` to `true` in the type provider instantiation.</span></span> <span data-ttu-id="f923c-201">O provedor de tipo `SqlDataConnection` contém vários métodos estáticos que você pode usar para configurar os tipos que são gerados.</span><span class="sxs-lookup"><span data-stu-id="f923c-201">The type provider `SqlDataConnection` contains several static methods that you can use to configure the types that are generated.</span></span> <span data-ttu-id="f923c-202">Para obter uma descrição completa dessas, consulte [provedor de tipo SqlDataConnection](https://msdn.microsoft.com/visualfsharpdocs/conceptual/sqldataconnection-type-provider-%5bfsharp%5d).</span><span class="sxs-lookup"><span data-stu-id="f923c-202">For a complete description of these, see [SqlDataConnection Type Provider](https://msdn.microsoft.com/visualfsharpdocs/conceptual/sqldataconnection-type-provider-%5bfsharp%5d).</span></span> <span data-ttu-id="f923c-203">Um método no tipo de contexto de dados é gerado para cada procedimento armazenado.</span><span class="sxs-lookup"><span data-stu-id="f923c-203">A method on the data context type is generated for each stored procedure.</span></span>


#### <a name="to-call-a-stored-procedure"></a><span data-ttu-id="f923c-204">Para chamar um procedimento armazenado</span><span class="sxs-lookup"><span data-stu-id="f923c-204">To call a stored procedure</span></span>

<span data-ttu-id="f923c-205">Se os procedimentos armazenados usa parâmetros que permitem valor nulo, você precisa passar um apropriado `System.Nullable` valor.</span><span class="sxs-lookup"><span data-stu-id="f923c-205">If the stored procedures takes parameters that are nullable, you need to pass an appropriate `System.Nullable` value.</span></span> <span data-ttu-id="f923c-206">O valor de retorno de um método de procedimento armazenado que retorna um valor escalar ou uma tabela é `System.Data.Linq.ISingleResult`, que contém propriedades que permitem que você acesse os dados retornados.</span><span class="sxs-lookup"><span data-stu-id="f923c-206">The return value of a stored procedure method that returns a scalar or a table is `System.Data.Linq.ISingleResult`, which contains properties that enable you to access the returned data.</span></span> <span data-ttu-id="f923c-207">O argumento de tipo para `System.Data.Linq.ISingleResult` depende do procedimento específico e também é um dos tipos que gera o provedor de tipos.</span><span class="sxs-lookup"><span data-stu-id="f923c-207">The type argument for `System.Data.Linq.ISingleResult` depends on the specific procedure and is also one of the types that the type provider generates.</span></span> <span data-ttu-id="f923c-208">Para um procedimento armazenado denominado `Procedure1`, o tipo é `Procedure1Result`.</span><span class="sxs-lookup"><span data-stu-id="f923c-208">For a stored procedure named `Procedure1`, the type is `Procedure1Result`.</span></span> <span data-ttu-id="f923c-209">O tipo `Procedure1Result` contém os nomes das colunas em uma tabela retornada, ou, para um procedimento armazenado que retorna um valor escalar, ele representa o valor de retorno.</span><span class="sxs-lookup"><span data-stu-id="f923c-209">The type `Procedure1Result` contains the names of the columns in a returned table, or, for a stored procedure that returns a scalar value, it represents the return value.</span></span>

<span data-ttu-id="f923c-210">O código a seguir supõe que há um procedimento `Procedure1` no banco de dados que usa dois inteiros anuláveis como parâmetros, executa uma consulta que retorna uma coluna denominada `TestData1`e retorna um inteiro.</span><span class="sxs-lookup"><span data-stu-id="f923c-210">The following code assumes that there is a procedure `Procedure1` on the database that takes two nullable integers as parameters, runs a query that returns a column named `TestData1`, and returns an integer.</span></span>

```fsharp
type schema = SqlDataConnection<"Data Source=MYSERVER\INSTANCE;Initial Catalog=MyDatabase;Integrated Security=SSPI;", StoredProcedures = true>

let testdb = schema.GetDataContext()

let nullable value = new System.Nullable<_>(value)

let callProcedure1 a b =
  let results = testdb.Procedure1(nullable a, nullable b)
  for result in results do
    printfn "%d" (result.TestData1.GetValueOrDefault())
  results.ReturnValue :?> int

printfn "Return Value: %d" (callProcedure1 10 20)
```

## <a name="updating-the-database"></a><span data-ttu-id="f923c-211">Atualizando o banco de dados</span><span class="sxs-lookup"><span data-stu-id="f923c-211">Updating the database</span></span>
<span data-ttu-id="f923c-212">O tipo DataContext LINQ contém métodos que facilitam a executar atualizações transacionadas do banco de dados de maneira totalmente digitada com os tipos gerados.</span><span class="sxs-lookup"><span data-stu-id="f923c-212">The LINQ DataContext type contains methods that make it easier to perform transacted database updates in a fully typed fashion with the generated types.</span></span>


#### <a name="to-update-the-database"></a><span data-ttu-id="f923c-213">Para atualizar o banco de dados</span><span class="sxs-lookup"><span data-stu-id="f923c-213">To update the database</span></span>

1. <span data-ttu-id="f923c-214">No código a seguir, várias linhas são adicionadas ao banco de dados.</span><span class="sxs-lookup"><span data-stu-id="f923c-214">In the following code, several rows are added to the database.</span></span> <span data-ttu-id="f923c-215">Se você só estiver adicionando uma linha, você pode usar `System.Data.Linq.Table.InsertOnSubmit()` para especificar a nova linha para adicionar.</span><span class="sxs-lookup"><span data-stu-id="f923c-215">If you are only adding a row, you can use `System.Data.Linq.Table.InsertOnSubmit()` to specify the new row to add.</span></span> <span data-ttu-id="f923c-216">Se você estiver inserindo várias linhas, você deve colocá-los em uma coleção e chamada `System.Data.Linq.Table.InsertAllOnSubmit(System.Collections.Generic.IEnumerable)`.</span><span class="sxs-lookup"><span data-stu-id="f923c-216">If you are inserting multiple rows, you should put them into a collection and call `System.Data.Linq.Table.InsertAllOnSubmit(System.Collections.Generic.IEnumerable)`.</span></span> <span data-ttu-id="f923c-217">Quando você chamar qualquer um desses métodos, o banco de dados não é alterado imediatamente.</span><span class="sxs-lookup"><span data-stu-id="f923c-217">When you call either of these methods, the database is not immediately changed.</span></span> <span data-ttu-id="f923c-218">Você deve chamar `System.Data.Linq.DataContext.SubmitChanges` para confirmar as alterações.</span><span class="sxs-lookup"><span data-stu-id="f923c-218">You must call `System.Data.Linq.DataContext.SubmitChanges` to actually commit the changes.</span></span> <span data-ttu-id="f923c-219">Por padrão, tudo o que fazer antes de chamar `System.Data.Linq.DataContext.SubmitChanges` implicitamente faz parte da mesma transação.</span><span class="sxs-lookup"><span data-stu-id="f923c-219">By default, everything that you do before you call `System.Data.Linq.DataContext.SubmitChanges` is implicitly part of the same transaction.</span></span>

 ```fsharp
   let newRecord = new dbSchema.ServiceTypes.Table1(Id = 100,
                                                    TestData1 = 35, 
                                                    TestData2 = 2.0,
                                                    Name = "Testing123")

   let newValues =
     [ for i in [1 .. 10] ->
       new dbSchema.ServiceTypes.Table3(Id = 700 + i,
         Name = "Testing" + i.ToString(),
         Data = i) ]

   // Insert the new data into the database.
   db.Table1.InsertOnSubmit(newRecord)
   db.Table3.InsertAllOnSubmit(newValues)

   try
     db.DataContext.SubmitChanges()
     printfn "Successfully inserted new rows."
   with
   | exn -> printfn "Exception:\n%s" exn.Message
```

2. <span data-ttu-id="f923c-220">Limpe agora as linhas chamando uma operação de exclusão.</span><span class="sxs-lookup"><span data-stu-id="f923c-220">Now clean up the rows by calling a delete operation.</span></span>

  ```fsharp
   // Now delete what was added.
   db.Table1.DeleteOnSubmit(newRecord)
   db.Table3.DeleteAllOnSubmit(newValues)

   try
     db.DataContext.SubmitChanges()
     printfn "Successfully deleted all pending rows."
   with
   | exn -> printfn "Exception:\n%s" exn.Message
```

## <a name="executing-transact-sql-code"></a><span data-ttu-id="f923c-221">Execução de código Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="f923c-221">Executing Transact-SQL code</span></span>
<span data-ttu-id="f923c-222">Você também pode especificar o Transact-SQL diretamente usando o `System.Data.Linq.DataContext.ExecuteCommand(System.String,System.Object[])` método o `DataContext` classe.</span><span class="sxs-lookup"><span data-stu-id="f923c-222">You can also specify Transact-SQL directly by using the `System.Data.Linq.DataContext.ExecuteCommand(System.String,System.Object[])` method on the `DataContext` class.</span></span>


#### <a name="to-execute-custom-sql-commands"></a><span data-ttu-id="f923c-223">Para executar comandos SQL personalizados</span><span class="sxs-lookup"><span data-stu-id="f923c-223">To execute custom SQL commands</span></span>

<span data-ttu-id="f923c-224">O código a seguir mostra como enviar comandos SQL para inserir um registro em uma tabela e também para excluir um registro de uma tabela.</span><span class="sxs-lookup"><span data-stu-id="f923c-224">The following code shows how to send SQL commands to insert a record into a table and also to delete a record from a table.</span></span>

```fsharp
try
  db.DataContext.ExecuteCommand("INSERT INTO Table3 (Id, Name, Data) VALUES (102, 'Testing', 55)") |> ignore
with
| exn -> printfn "Exception:\n%s" exn.Message

try //AND Name = 'Testing' AND Data = 55
  db.DataContext.ExecuteCommand("DELETE FROM Table3 WHERE Id = 102 ") |> ignore
with
| exn -> printfn "Exception:\n%s" exn.Message
```

## <a name="using-the-full-data-context"></a><span data-ttu-id="f923c-225">Usando o contexto de dados completo</span><span class="sxs-lookup"><span data-stu-id="f923c-225">Using the full data context</span></span>
<span data-ttu-id="f923c-226">Nos exemplos anteriores, o `GetDataContext` método foi usado para obter o que é chamado de *o contexto de dados simplificado* para o esquema de banco de dados.</span><span class="sxs-lookup"><span data-stu-id="f923c-226">In the previous examples, the `GetDataContext` method was used to get what is called the *simplified data context* for the database schema.</span></span> <span data-ttu-id="f923c-227">O contexto de dados simplificado é mais fácil de usar ao construir consultas porque não há como muitos membros.</span><span class="sxs-lookup"><span data-stu-id="f923c-227">The simplified data context is easier to use when you are constructing queries because there are not as many members available.</span></span> <span data-ttu-id="f923c-228">Portanto, quando você procura as propriedades do IntelliSense, você pode se concentrar na estrutura de banco de dados, como as tabelas e procedimentos armazenados.</span><span class="sxs-lookup"><span data-stu-id="f923c-228">Therefore, when you browse the properties in IntelliSense, you can focus on the database structure, such as the tables and stored procedures.</span></span> <span data-ttu-id="f923c-229">No entanto, há um limite para que você pode fazer com o contexto de dados simplificado.</span><span class="sxs-lookup"><span data-stu-id="f923c-229">However, there is a limit to what you can do with the simplified data context.</span></span> <span data-ttu-id="f923c-230">Um contexto de dados completo que fornece a capacidade de executar outras ações.</span><span class="sxs-lookup"><span data-stu-id="f923c-230">A full data context that provides the ability to perform other actions.</span></span> <span data-ttu-id="f923c-231">também está disponível que ele está localizado no `ServiceTypes` e tem o nome do *DataContext* parâmetro estático se você forneceu a ele.</span><span class="sxs-lookup"><span data-stu-id="f923c-231">is also available This is located in the `ServiceTypes` and has the name of the *DataContext* static parameter if you provided it.</span></span> <span data-ttu-id="f923c-232">Se você não forneceu-lo, o nome do tipo de contexto de dados é gerado para você por SqlMetal.exe com base em outra entrada.</span><span class="sxs-lookup"><span data-stu-id="f923c-232">If you did not provide it, the name of the data context type is generated for you by SqlMetal.exe based on the other input.</span></span> <span data-ttu-id="f923c-233">Herda o contexto de dados completo de `System.Data.Linq.DataContext` e expõe os membros de sua classe base, incluindo as referências aos tipos de dados do ADO.NET, como o `Connection` objeto, métodos, como `System.Data.Linq.DataContext.ExecuteCommand(System.String,System.Object[])` e `System.Data.Linq.DataContext.ExecuteQuery(System.String,System.Object[])` que você pode usar para escrever consultas em SQL, e também um meio para funcionar com transações explicitamente.</span><span class="sxs-lookup"><span data-stu-id="f923c-233">The full data context inherits from `System.Data.Linq.DataContext` and exposes the members of its base class, including references to ADO.NET data types such as the `Connection` object, methods such as `System.Data.Linq.DataContext.ExecuteCommand(System.String,System.Object[])` and `System.Data.Linq.DataContext.ExecuteQuery(System.String,System.Object[])` that you can use to write queries in SQL, and also a means to work with transactions explicitly.</span></span>


#### <a name="to-use-the-full-data-context"></a><span data-ttu-id="f923c-234">Para usar o contexto de dados completo</span><span class="sxs-lookup"><span data-stu-id="f923c-234">To use the full data context</span></span>

<span data-ttu-id="f923c-235">O código a seguir demonstra a obtenção de um objeto de contexto de dados completo e usá-lo para executar comandos diretamente no banco de dados.</span><span class="sxs-lookup"><span data-stu-id="f923c-235">The following code demonstrates getting a full data context object and using it to execute commands directly against the database.</span></span> <span data-ttu-id="f923c-236">Nesse caso, os dois comandos são executados como parte da mesma transação.</span><span class="sxs-lookup"><span data-stu-id="f923c-236">In this case, two commands are executed as part of the same transaction.</span></span>

```fsharp
let dbConnection = testdb.Connection
let fullContext = new dbSchema.ServiceTypes.MyDatabase(dbConnection)

dbConnection.Open()

let transaction = dbConnection.BeginTransaction()
fullContext.Transaction <- transaction

try
  let result1 = fullContext.ExecuteCommand("INSERT INTO Table3 (Id, Name, Data) VALUES (102, 'A', 55)")
  printfn "ExecuteCommand Result: %d" result1
  let result2 = fullContext.ExecuteCommand("INSERT INTO Table3 (Id, Name, Data) VALUES (103, 'B', -2)")
  printfn "ExecuteCommand Result: %d" result2
  if (result1 <> 1 || result2 <> 1) then
    transaction.Rollback()
    printfn "Rolled back creation of two new rows."
  else
    transaction.Commit()
  printfn "Successfully committed two new rows."
with
| exn ->
  transaction.Rollback()
  printfn "Rolled back creation of two new rows due to exception:\n%s" exn.Message

dbConnection.Close()
```

## <a name="deleting-data"></a><span data-ttu-id="f923c-237">Excluindo dados</span><span class="sxs-lookup"><span data-stu-id="f923c-237">Deleting data</span></span>
<span data-ttu-id="f923c-238">Esta etapa mostra como excluir linhas de uma tabela de dados.</span><span class="sxs-lookup"><span data-stu-id="f923c-238">This step shows you how to delete rows from a data table.</span></span>


#### <a name="to-delete-rows-from-the-database"></a><span data-ttu-id="f923c-239">Para excluir linhas do banco de dados</span><span class="sxs-lookup"><span data-stu-id="f923c-239">To delete rows from the database</span></span>

<span data-ttu-id="f923c-240">Agora, limpar qualquer adicionadas linhas ao escrever uma função que exclui linhas de uma tabela especificada, uma instância do `System.Data.Linq.Table` classe.</span><span class="sxs-lookup"><span data-stu-id="f923c-240">Now, clean up any added rows by writing a function that deletes rows from a specified table, an instance of the `System.Data.Linq.Table` class.</span></span> <span data-ttu-id="f923c-241">Em seguida, escrever uma consulta para localizar todas as linhas que você deseja excluir e direcionar os resultados da consulta no `deleteRows` função.</span><span class="sxs-lookup"><span data-stu-id="f923c-241">Then write a query to find all the rows that you want to delete, and pipe the results of the query into the `deleteRows` function.</span></span> <span data-ttu-id="f923c-242">Esse código aproveita a capacidade de fornecer aplicativo parcial de argumentos de função.</span><span class="sxs-lookup"><span data-stu-id="f923c-242">This code takes advantage of the ability to provide partial application of function arguments.</span></span>

```fsharp
let deleteRowsFrom (table:Table<_>) rows =
  table.DeleteAllOnSubmit(rows)

query {
  for rows in db.Table3 do
  where (rows.Id > 10)
  select rows
} |> deleteRowsFrom db.Table3

db.DataContext.SubmitChanges()
printfn "Successfully deleted rows with Id greater than 10 in Table3."
```

## <a name="creating-a-test-database"></a><span data-ttu-id="f923c-243">Criando um banco de dados de teste</span><span class="sxs-lookup"><span data-stu-id="f923c-243">Creating a test database</span></span>
<span data-ttu-id="f923c-244">Esta seção mostra como configurar o banco de dados de teste para usar neste passo a passo.</span><span class="sxs-lookup"><span data-stu-id="f923c-244">This section shows you how to set up the test database to use in this walkthrough.</span></span>

<span data-ttu-id="f923c-245">Observe que, se você alterar o banco de dados de alguma forma, você precisará redefinir o provedor de tipos.</span><span class="sxs-lookup"><span data-stu-id="f923c-245">Note that if you alter the database in some way, you will have to reset the type provider.</span></span> <span data-ttu-id="f923c-246">Para redefinir o provedor de tipos, recriar ou limpe o projeto que contém o provedor de tipo.</span><span class="sxs-lookup"><span data-stu-id="f923c-246">To reset the type provider, rebuild or clean the project that contains the type provider.</span></span>


#### <a name="to-create-the-test-database"></a><span data-ttu-id="f923c-247">Para criar o banco de dados de teste</span><span class="sxs-lookup"><span data-stu-id="f923c-247">To create the test database</span></span>

1. <span data-ttu-id="f923c-248">Em **Server Explorer**, abra o menu de atalho para o **conexões de dados** nó e escolha **Adicionar Conexão**.</span><span class="sxs-lookup"><span data-stu-id="f923c-248">In **Server Explorer**, open the shortcut menu for the **Data Connections** node, and choose **Add Connection**.</span></span> <span data-ttu-id="f923c-249">O **Adicionar Conexão** caixa de diálogo é exibida.</span><span class="sxs-lookup"><span data-stu-id="f923c-249">The **Add Connection** dialog box appears.</span></span>

2. <span data-ttu-id="f923c-250">No **nome do servidor** caixa, especifique o nome de uma instância do SQL Server que têm acesso administrativo ao ou, se você não tiver acesso a um servidor, especifique (localdb\v11.0).</span><span class="sxs-lookup"><span data-stu-id="f923c-250">In the **Server name** box, specify the name of an instance of SQL Server that you have administrative access to, or if you do not have access to a server, specify (localdb\v11.0).</span></span> <span data-ttu-id="f923c-251">SQL Express LocalDB fornece um servidor de banco de dados leve para desenvolvimento e teste em seu computador.</span><span class="sxs-lookup"><span data-stu-id="f923c-251">SQL Express LocalDB provides a lightweight database server for development and testing on your machine.</span></span> <span data-ttu-id="f923c-252">É criado um novo nó no **Server Explorer** em **conexões de dados**.</span><span class="sxs-lookup"><span data-stu-id="f923c-252">A new node is created in **Server Explorer** under **Data Connections**.</span></span> <span data-ttu-id="f923c-253">Para obter mais informações sobre o LocalDB, consulte [passo a passo: Criando um arquivo de banco de dados Local no Visual Studio](https://msdn.microsoft.com/library/ms233763.aspx).</span><span class="sxs-lookup"><span data-stu-id="f923c-253">For more information about LocalDB, see [Walkthrough: Creating a Local Database File in Visual Studio](https://msdn.microsoft.com/library/ms233763.aspx).</span></span>

3. <span data-ttu-id="f923c-254">Abra o menu de atalho para o novo nó de conexão e selecione **nova consulta**.</span><span class="sxs-lookup"><span data-stu-id="f923c-254">Open the shortcut menu for the new connection node, and select **New Query**.</span></span>

4. <span data-ttu-id="f923c-255">Copie o seguinte script SQL, cole-o no editor de consultas e, em seguida, escolha o **Execute** botão na barra de ferramentas ou escolha as teclas Ctrl + Shift + E.</span><span class="sxs-lookup"><span data-stu-id="f923c-255">Copy the following SQL script, paste it into the query editor, and then choose the **Execute** button on the toolbar or choose the Ctrl+Shift+E keys.</span></span>

```sql
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO

USE [master];
GO

IF EXISTS (SELECT * FROM sys.databases WHERE name = 'MyDatabase')
  DROP DATABASE MyDatabase;
GO

-- Create the MyDatabase database.
CREATE DATABASE MyDatabase;
GO

-- Specify a simple recovery model 
-- to keep the log growth to a minimum.
ALTER DATABASE MyDatabase 
SET RECOVERY SIMPLE;
GO

USE MyDatabase;
GO

-- Create the Table1 table.
CREATE TABLE [dbo].[Table1] (
  [Id]        INT        NOT NULL,
  [TestData1] INT        NOT NULL,
  [TestData2] FLOAT (53) NOT NULL,
  [Name]      NTEXT      NOT NULL,
  PRIMARY KEY CLUSTERED ([Id] ASC)
);

-- Create the Table2 table.
CREATE TABLE [dbo].[Table2] (
  [Id]        INT        NOT NULL,
  [TestData1] INT        NULL,
  [TestData2] FLOAT (53) NULL,
  [Name]      NTEXT      NOT NULL,
  PRIMARY KEY CLUSTERED ([Id] ASC)
);


-- Create the Table3 table.
CREATE TABLE [dbo].[Table3] (
  [Id]   INT           NOT NULL,
  [Name] NVARCHAR (50) NOT NULL,
  [Data] INT           NOT NULL,
  PRIMARY KEY CLUSTERED ([Id] ASC)
  );
GO

CREATE PROCEDURE [dbo].[Procedure1]
  @param1 int = 0,
  @param2 int
AS
SELECT TestData1 FROM Table1
RETURN 0
GO

USE MyDatabase

-- Insert data into the Table1 table.
INSERT INTO Table1 (Id, TestData1, TestData2, Name)
  VALUES(1, 10, 5.5, 'Testing1');
INSERT INTO Table1 (Id, TestData1, TestData2, Name)
  VALUES(2, 20, -1.2, 'Testing2');

-- Insert data into the Table2 table.
INSERT INTO Table2 (Id, TestData1, TestData2, Name)
  VALUES(1, 10, 5.5, 'Testing1');
INSERT INTO Table2 (Id, TestData1, TestData2, Name)
  VALUES(2, 20, -1.2, 'Testing2');
INSERT INTO Table2 (Id, TestData1, TestData2, Name)
  VALUES(3, NULL, NULL, 'Testing3');

-- Insert data into the Table3 table.
INSERT INTO Table3 (Id, Name, Data)
  VALUES (1, 'Testing1', 10);
INSERT INTO Table3 (Id, Name, Data)
  VALUES (2, 'Testing2', 100);
```


## <a name="see-also"></a><span data-ttu-id="f923c-256">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f923c-256">See Also</span></span>
[<span data-ttu-id="f923c-257">Provedores de Tipos</span><span class="sxs-lookup"><span data-stu-id="f923c-257">Type Providers</span></span>](index.md)

[<span data-ttu-id="f923c-258">Tipo SqlDataConnection</span><span class="sxs-lookup"><span data-stu-id="f923c-258">SqlDataConnection Type Provider</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/sqldataconnection-type-provider-%5bfsharp%5d)

[<span data-ttu-id="f923c-259">Passo a passo: Gerando tipos F # em um arquivo DBML</span><span class="sxs-lookup"><span data-stu-id="f923c-259">Walkthrough: Generating F# Types from a DBML File</span></span>](generating-fsharp-types-from-dbml.md)

[<span data-ttu-id="f923c-260">Expressões de Consulta</span><span class="sxs-lookup"><span data-stu-id="f923c-260">Query Expressions</span></span>](../../language-reference/query-expressions.md)

[<span data-ttu-id="f923c-261">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="f923c-261">LINQ to SQL</span></span>](../../../../docs/framework/data/adonet/sql/linq/index.md)

[<span data-ttu-id="f923c-262">SqlMetal.exe &#40;ferramenta de geração de código&#41;</span><span class="sxs-lookup"><span data-stu-id="f923c-262">SqlMetal.exe &#40;Code Generation Tool&#41;</span></span>](https://msdn.microsoft.com/library/bb386987)
