---
title: 'Instruções passo a passo: gerando tipos F# com base em um arquivo de esquema EDMX (F#)'
description: 'Saiba como criar tipos F # para dados representados pela entidade de dados EDM (modelo) em F # 3.0, onde o esquema está especificado em um arquivo. edmx.'
keywords: visual f#, f#, programação funcional
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 81adb2eb-625f-4ad8-aeaa-8f672a6d79a2
ms.openlocfilehash: 901457dce358f768b4f4c980703e09f6c744918e
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/10/2018
---
# <a name="walkthrough-generating-f-types-from-an-edmx-schema-file"></a><span data-ttu-id="709c6-104">Instruções passo a passo: gerando tipos F# com base em um arquivo de esquema EDMX</span><span class="sxs-lookup"><span data-stu-id="709c6-104">Walkthrough: Generating F# Types from an EDMX Schema File</span></span>

> [!NOTE]
<span data-ttu-id="709c6-105">Este guia foi escrito para F # 3.0 e será atualizado.</span><span class="sxs-lookup"><span data-stu-id="709c6-105">This guide was written for F# 3.0 and will be updated.</span></span>  <span data-ttu-id="709c6-106">Consulte [FSharp.Data](https://fsharp.github.io/FSharp.Data/) para provedores de tipo de plataforma cruzada atualizados.</span><span class="sxs-lookup"><span data-stu-id="709c6-106">See [FSharp.Data](https://fsharp.github.io/FSharp.Data/) for up-to-date, cross-platform type providers.</span></span>

> [!NOTE]
<span data-ttu-id="709c6-107">Os links de referência de API levará você para o MSDN.</span><span class="sxs-lookup"><span data-stu-id="709c6-107">The API reference links will take you to MSDN.</span></span>  <span data-ttu-id="709c6-108">A referência da API docs.microsoft.com não está completa.</span><span class="sxs-lookup"><span data-stu-id="709c6-108">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="709c6-109">Este guia passo a passo para o F# 3.0 mostra como criar tipos para dados que são representados pelo EDM (Modelo de Dados de Entidade), o esquema para o qual é especificado em um arquivo .edmx.</span><span class="sxs-lookup"><span data-stu-id="709c6-109">This walkthrough for F# 3.0 shows you how to create types for data that is represented by the Entity Data Model (EDM), the schema for which is specified in an .edmx file.</span></span> <span data-ttu-id="709c6-110">Esse guia também mostra como usar o provedor de tipos EdmxFile.</span><span class="sxs-lookup"><span data-stu-id="709c6-110">This walkthrough also shows how to use the EdmxFile type provider.</span></span> <span data-ttu-id="709c6-111">Antes de começar, considere se um provedor de tipos SqlEntityConnection é uma opção mais apropriada de provedor de tipos.</span><span class="sxs-lookup"><span data-stu-id="709c6-111">Before you begin, consider whether a SqlEntityConnection type provider is a more appropriate type provider option.</span></span> <span data-ttu-id="709c6-112">O provedor de tipos SqlEntityConnection funciona melhor em cenários onde você tem um banco de dados dinâmico ao qual você pode se conectar durante a fase de desenvolvimento de seu projeto e você não se importa em especificar a cadeia de conexão em tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="709c6-112">The SqlEntityConnection type provider works best for scenarios where you have a live database that you can connect to during the development phase of your project, and you do not mind specifying the connection string at compile time.</span></span> <span data-ttu-id="709c6-113">No entanto, esse provedor de tipos também é limitado na medida que expõe tanta funcionalidade de banco de dados quanto o provedor de tipos EdmxFile.</span><span class="sxs-lookup"><span data-stu-id="709c6-113">However, this type provider is also limited in that it doesn't expose as much database functionality as the EdmxFile type provider.</span></span> <span data-ttu-id="709c6-114">Além de isso, se você não tiver uma conexão de banco de dados dinâmico para um projeto de banco de dados que use o Modelo de Dados de Entidade, será possível usar o arquivo .edmx para codificação em relação ao banco de dados.</span><span class="sxs-lookup"><span data-stu-id="709c6-114">Also, if you don't have a live database connection for a database project that uses the Entity Data Model, you can use the .edmx file to code against the database.</span></span> <span data-ttu-id="709c6-115">Quando você usa o provedor de tipos EdmxFile, o compilador F# executa EdmGen.exe para gerar os tipos que ele fornece.</span><span class="sxs-lookup"><span data-stu-id="709c6-115">When you use the EdmxFile type provider, the F# compiler runs EdmGen.exe to generate the types that it provides.</span></span>

<span data-ttu-id="709c6-116">Este guia passo a passo ilustra as seguintes tarefas que você deve executar nesta ordem para que as instruções sejam bem-sucedidas:</span><span class="sxs-lookup"><span data-stu-id="709c6-116">This walkthrough illustrates the following tasks, which you must perform in this order for the walkthrough to succeed:</span></span>


- <span data-ttu-id="709c6-117">Criando um arquivo EDMX</span><span class="sxs-lookup"><span data-stu-id="709c6-117">Creating an EDMX file</span></span>
<br />

- <span data-ttu-id="709c6-118">Criando o projeto</span><span class="sxs-lookup"><span data-stu-id="709c6-118">Creating the project</span></span>
<br />

- <span data-ttu-id="709c6-119">Localizando ou criando a cadeia de conexão do Modelo de Dados de Entidade</span><span class="sxs-lookup"><span data-stu-id="709c6-119">Finding or creating the entity data model connection string</span></span>
<br />

- <span data-ttu-id="709c6-120">Configurando o provedor de tipos</span><span class="sxs-lookup"><span data-stu-id="709c6-120">Configuring the type provider</span></span>
<br />

- <span data-ttu-id="709c6-121">Consultando os dados</span><span class="sxs-lookup"><span data-stu-id="709c6-121">Querying the data</span></span>
<br />

- <span data-ttu-id="709c6-122">Chamando um procedimento armazenado</span><span class="sxs-lookup"><span data-stu-id="709c6-122">Calling a stored procedure</span></span>
<br />


## <a name="prerequisites"></a><span data-ttu-id="709c6-123">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="709c6-123">Prerequisites</span></span>

## <a name="creating-an-edmx-file"></a><span data-ttu-id="709c6-124">Criando um arquivo EDMX</span><span class="sxs-lookup"><span data-stu-id="709c6-124">Creating an EDMX file</span></span>
<span data-ttu-id="709c6-125">Se você já tiver um arquivo EDMX, pule esta etapa.</span><span class="sxs-lookup"><span data-stu-id="709c6-125">If you already have an EDMX file, you can skip this step.</span></span>


#### <a name="to-create-an-edmx-file"></a><span data-ttu-id="709c6-126">Para criar um arquivo EDMX</span><span class="sxs-lookup"><span data-stu-id="709c6-126">To create an EDMX file</span></span>

- <span data-ttu-id="709c6-127">Se você ainda não tiver um arquivo EDMX, você pode seguir as instruções no final deste passo a passo na etapa [configurar o modelo de dados de entidade](generating-fsharp-types-from-edmx.md#configuring-the-entity-data-model).</span><span class="sxs-lookup"><span data-stu-id="709c6-127">If you don't already have an EDMX file, you can follow the instructions at the end of this walkthrough in the step [Configuring the Entity Data Model](generating-fsharp-types-from-edmx.md#configuring-the-entity-data-model).</span></span>
<br />

## <a name="creating-the-project"></a><span data-ttu-id="709c6-128">Criando o projeto</span><span class="sxs-lookup"><span data-stu-id="709c6-128">Creating the project</span></span>
<span data-ttu-id="709c6-129">Nesta etapa, você criará um projeto e adicionará referências apropriadas a ele para usar o provedor de tipos EDMX.</span><span class="sxs-lookup"><span data-stu-id="709c6-129">In this step, you create a project and add appropriate references to it to use the EDMX type provider.</span></span>


#### <a name="to-create-and-set-up-an-f-project"></a><span data-ttu-id="709c6-130">Para criar e configurar um projeto de F#</span><span class="sxs-lookup"><span data-stu-id="709c6-130">To create and set up an F# project</span></span>

1. <span data-ttu-id="709c6-131">Feche o projeto anterior, crie outro projeto e o chame SchoolEDM.</span><span class="sxs-lookup"><span data-stu-id="709c6-131">Close the previous project, create another project, and name it SchoolEDM.</span></span>
<br />

2. <span data-ttu-id="709c6-132">Em **Solution Explorer**, abra o menu de atalho para **referências**e, em seguida, escolha **adicionar referência**.</span><span class="sxs-lookup"><span data-stu-id="709c6-132">In **Solution Explorer**, open the shortcut menu for **References**, and then choose **Add Reference**.</span></span>
<br />

3. <span data-ttu-id="709c6-133">No **Assemblies** área, escolha o **Framework** nó.</span><span class="sxs-lookup"><span data-stu-id="709c6-133">In the **Assemblies** area, choose the **Framework** node.</span></span>
<br />

4. <span data-ttu-id="709c6-134">Na lista de assemblies disponíveis, escolha o **System.Data.Entity** e **System.Data.Linq** assemblies e, em seguida, escolha o **adicionar** botão para adicionar referências a eles assemblies ao seu projeto.</span><span class="sxs-lookup"><span data-stu-id="709c6-134">In the list of available assemblies, choose the **System.Data.Entity** and **System.Data.Linq** assemblies, and then choose the **Add** button to add references to these assemblies to your project.</span></span>
<br />

5. <span data-ttu-id="709c6-135">No **Assemblies** área, selecione o **extensões** nó.</span><span class="sxs-lookup"><span data-stu-id="709c6-135">In the **Assemblies** area, select the **Extensions** node.</span></span>
<br />

6. <span data-ttu-id="709c6-136">Na lista de extensões disponíveis, adicione uma referência ao assembly FSharp.Data.TypeProviders.</span><span class="sxs-lookup"><span data-stu-id="709c6-136">In the  list of available extensions, add a reference to the FSharp.Data.TypeProviders assembly.</span></span>
<br />

7. <span data-ttu-id="709c6-137">Adicione o código a seguir para abrir os namespaces apropriados.</span><span class="sxs-lookup"><span data-stu-id="709c6-137">Add the following code to open the appropriate namespaces.</span></span>
<br />

```fsharp
open System.Data.Linq
open System.Data.Entity
open Microsoft.FSharp.Data.TypeProviders
```

## <a name="finding-or-creating-the-connection-string-for-the-entity-data-model"></a><span data-ttu-id="709c6-138">Localizando ou criando a cadeia de conexão para o Modelo de Dados de Entidade</span><span class="sxs-lookup"><span data-stu-id="709c6-138">Finding or creating the connection string for the Entity Data Model</span></span>
<span data-ttu-id="709c6-139">A cadeia de conexão para o Modelo de Dados de Entidade (cadeia de conexão EDMX) inclui não somente a cadeia de conexão para o provedor de banco de dados, mas também informações adicionais.</span><span class="sxs-lookup"><span data-stu-id="709c6-139">The connection string for the Entity Data Model (EDMX connection string) includes not only the connection string for the database provider but also additional information.</span></span> <span data-ttu-id="709c6-140">Por exemplo, a cadeia de conexão EDMX para um banco de dados SQL Server simples lembra o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="709c6-140">For example, EDMX connection string for a simple SQL Server database resembles the following code.</span></span>

```fsharp
let edmConnectionString = "metadata=res://*/;provider=System.Data.SqlClient;Provider Connection String='Server=SERVER\Instance;Initial Catalog=DatabaseName;Integrated Security=SSPI;'"
```

<span data-ttu-id="709c6-141">Para obter mais informações sobre cadeias de caracteres de conexão EDMX, consulte [cadeias de caracteres de Conexão](../../../../docs/framework/data/adonet/connection-strings-and-configuration-files.md).</span><span class="sxs-lookup"><span data-stu-id="709c6-141">For more information about EDMX connection strings, see [Connection Strings](../../../../docs/framework/data/adonet/connection-strings-and-configuration-files.md).</span></span>


#### <a name="to-find-or-create-the-connection-string-for-the-entity-data-model"></a><span data-ttu-id="709c6-142">Para localizar ou criar a cadeia de conexão para o Modelo de Dados de Entidade</span><span class="sxs-lookup"><span data-stu-id="709c6-142">To find or create the connection string for the Entity Data Model</span></span>

1. <span data-ttu-id="709c6-143">A geração manual de cadeias de conexão EDMX pode ser difícil, portanto, é possível economizar tempo gerando-as via programação.</span><span class="sxs-lookup"><span data-stu-id="709c6-143">EDMX connection strings can be difficult to generate by hand, so you can save time by generating it programmatically.</span></span> <span data-ttu-id="709c6-144">Se você souber a sua cadeia de conexão EDMX, ignore esta etapa e simplesmente use essa cadeia na próxima etapa.</span><span class="sxs-lookup"><span data-stu-id="709c6-144">If you know your EDMX connection string, you can bypass this step and simply use that string in the next step.</span></span> <span data-ttu-id="709c6-145">Em caso negativo, use o código a seguir para gerar a cadeia de conexão EDMX de uma cadeia de conexão de banco de dados fornecida por você.</span><span class="sxs-lookup"><span data-stu-id="709c6-145">If not, use the following code to generate the EDMX connection string from a database connection string that you provide.</span></span>
<br />

```fsharp
open System
open System.Data
open System.Data.SqlClient
open System.Data.EntityClient
open System.Data.Metadata.Edm

let getEDMConnection(dbConnectionString) =
  let dbConnection = new SqlConnection(dbConnectionString)
  let resourceArray = [| "res://*/" |]
  let assemblyList = [| System.Reflection.Assembly.GetCallingAssembly() |]
  let metaData = MetadataWorkspace(resourceArray, assemblyList)
  new EntityConnection(metaData, dbConnection)
```

## <a name="configuring-the-type-provider"></a><span data-ttu-id="709c6-146">Configurando o provedor de tipos</span><span class="sxs-lookup"><span data-stu-id="709c6-146">Configuring the type provider</span></span>
<span data-ttu-id="709c6-147">Nesta etapa, você criará e configurará o provedor de tipos com a cadeia de conexão EDMX e você gerará tipos para o esquema definido no arquivo .edmx.</span><span class="sxs-lookup"><span data-stu-id="709c6-147">In this step, you create and configure the type provider with the EDMX connection string, and you generate types for the schema that's defined in the .edmx file.</span></span>


#### <a name="to-configure-the-type-provider-and-generate-types"></a><span data-ttu-id="709c6-148">Para configurar o provedor de tipos e gerar tipos</span><span class="sxs-lookup"><span data-stu-id="709c6-148">To configure the type provider and generate types</span></span>

1. <span data-ttu-id="709c6-149">Copie o arquivo .edmx que você gerou na primeira etapa deste guia passo a passo na pasta de seu projeto.</span><span class="sxs-lookup"><span data-stu-id="709c6-149">Copy the .edmx file that you generated in the first step of this walkthrough to your project folder.</span></span>
<br />

2. <span data-ttu-id="709c6-150">Abrir o menu de atalho para o nó de projeto em seu projeto de F #, escolher **Add Existing Item**e, em seguida, escolha o arquivo. edmx para adicioná-lo ao seu projeto.</span><span class="sxs-lookup"><span data-stu-id="709c6-150">Open the shortcut menu for the project node in your F# project, choose **Add Existing Item**, and then choose the .edmx file to add it to your project.</span></span>
<br />

3. <span data-ttu-id="709c6-151">Insira o código a seguir para ativar o provedor de tipos para o seu arquivo .edmx.</span><span class="sxs-lookup"><span data-stu-id="709c6-151">Enter the following code to activate the type provider for your .edmx file.</span></span> <span data-ttu-id="709c6-152">Substituir *servidor*\*instância * com o nome do servidor que está executando o SQL Server e o nome da sua instância e usar o nome do arquivo. edmx da primeira etapa neste passo a passo.</span><span class="sxs-lookup"><span data-stu-id="709c6-152">Replace *Server*\*Instance* with the name of your server that's running SQL Server and the name of your instance, and use the name of your .edmx file from the first step in this walkthrough.</span></span>
<br />

```fsharp
type edmx = EdmxFile<"Model1.edmx", ResolutionFolder = @"<path-tofolder-that-containsyour.edmx-file>">

use edmConnection =
  getEDMConnection("Data Source=SERVER\instance;Initial Catalog=School;Integrated Security=true;")
use context = new edmx.SchoolModel.SchoolEntities(edmConnection)
```

## <a name="querying-the-data"></a><span data-ttu-id="709c6-153">Consultando os dados</span><span class="sxs-lookup"><span data-stu-id="709c6-153">Querying the data</span></span>
<span data-ttu-id="709c6-154">Nesta etapa, você usa expressões de consulta do F# para consultar o banco de dados.</span><span class="sxs-lookup"><span data-stu-id="709c6-154">In this step, you use F# query expressions to query the database.</span></span>


#### <a name="to-query-the-data"></a><span data-ttu-id="709c6-155">Para consultar os dados</span><span class="sxs-lookup"><span data-stu-id="709c6-155">To query the data</span></span>

- <span data-ttu-id="709c6-156">Insira o código a seguir para consultar os dados no modelo de dados de entidade.</span><span class="sxs-lookup"><span data-stu-id="709c6-156">Enter the following code to query the data in the entity data model.</span></span>
<br />

```fsharp
query { 
  for course in context.Courses do
  select course 
} |> Seq.iter (fun course -> printfn "%s" course.Title)

query { 
  for person in context.Person do
  select person 
} |> Seq.iter (fun person -> printfn "%s %s" person.FirstName person.LastName)

// Add a where clause to filter results
query { 
  for course in context.Courses do
  where (course.DepartmentID = 1)
  select course
} |> Seq.iter (fun course -> printfn "%s" course.Title)

// Join two tables
query { 
  for course in context.Courses do
  join dept in context.Departments on (course.DepartmentID = dept.DepartmentID)
  select (course, dept.Name) 
} |> Seq.iter (fun (course, deptName) -> printfn "%s %s" course.Title deptName)
```

## <a name="calling-a-stored-procedure"></a><span data-ttu-id="709c6-157">Chamando um procedimento armazenado</span><span class="sxs-lookup"><span data-stu-id="709c6-157">Calling a stored procedure</span></span>
<span data-ttu-id="709c6-158">Você pode chamar procedimentos armazenados ao usar o provedor de tipos EDMX.</span><span class="sxs-lookup"><span data-stu-id="709c6-158">You can call stored procedures by using the EDMX type provider.</span></span> <span data-ttu-id="709c6-159">O procedimento a seguir, o banco de dados de escola contém um procedimento armazenado, **UpdatePerson**, que atualiza um registro, determinados novos valores para as colunas.</span><span class="sxs-lookup"><span data-stu-id="709c6-159">In the following procedure, the School database contains a stored procedure, **UpdatePerson**, which updates a record, given new values for the columns.</span></span> <span data-ttu-id="709c6-160">Você pode usar esse procedimento armazenado porque ele está exposto como um método no tipo DataContext.</span><span class="sxs-lookup"><span data-stu-id="709c6-160">You can use this stored procedure because it's exposed as a method on the DataContext type.</span></span>


#### <a name="to-call-a-stored-procedure"></a><span data-ttu-id="709c6-161">Para chamar um procedimento armazenado</span><span class="sxs-lookup"><span data-stu-id="709c6-161">To call a stored procedure</span></span>

- <span data-ttu-id="709c6-162">Adicione o código a seguir para atualizar registros.</span><span class="sxs-lookup"><span data-stu-id="709c6-162">Add the following code to update records.</span></span>
<br />

```fsharp
// Call a stored procedure.
let nullable value = new System.Nullable<_>(value)

// Assume now that you must correct someone's hire date.
// Throw an exception if more than one matching person is found.
let changeHireDate(lastName, firstName, hireDate) =

  query { 
    for person in context.People do
    where (person.LastName = lastName &&
           person.FirstName = firstName)
    exactlyOne 
  } |> (fun person ->
            context.UpdatePerson(nullable person.PersonID, person.LastName, person.FirstName, nullable hireDate, person.EnrollmentDate))

changeHireDate("Abercrombie", "Kim", DateTime.Parse("1/12/1998"))
|> printfn "Result: %d"
```

<span data-ttu-id="709c6-163">O resultado será 1 se houver êxito.</span><span class="sxs-lookup"><span data-stu-id="709c6-163">The result is 1 if you succeed.</span></span> <span data-ttu-id="709c6-164">Observe que **exactlyOne** é usado na expressão de consulta para garantir que apenas um resultado é retornado; caso contrário, uma exceção será lançada.</span><span class="sxs-lookup"><span data-stu-id="709c6-164">Notice that **exactlyOne** is used in the query expression to ensure that only one result is returned; otherwise, an exception is thrown.</span></span> <span data-ttu-id="709c6-165">Além disso, para trabalhar com valores anuláveis mais facilmente, você pode usar o simples **anulável** função que está definida nesse código para criar um valor nulo fora de um valor comum.</span><span class="sxs-lookup"><span data-stu-id="709c6-165">Also, to work with nullable values more easily, you can use the simple **nullable** function that's defined in this code to create a nullable value out of an ordinary value.</span></span>

<br />

## <a name="configuring-the-entity-data-model"></a><span data-ttu-id="709c6-166">Configurando o Modelo de Dados de Entidade</span><span class="sxs-lookup"><span data-stu-id="709c6-166">Configuring the Entity Data Model</span></span>
<span data-ttu-id="709c6-167">Você deve concluir este procedimento somente se você desejar saber como gerar um Modelo de Dados de Entidade completo de um banco de dados e não tiver um banco de dados com o qual testar.</span><span class="sxs-lookup"><span data-stu-id="709c6-167">You should complete this procedure only if you want to know how to generate a full Entity Data Model from a database and you don't have a database with which to test.</span></span>


#### <a name="to-configure-the-entity-data-model"></a><span data-ttu-id="709c6-168">Para configurar o Modelo de Dados de Entidade</span><span class="sxs-lookup"><span data-stu-id="709c6-168">To configure the Entity Data Model</span></span>

1. <span data-ttu-id="709c6-169">Na barra de menus, escolha **SQL**, **Editor Transact-SQL**, **nova consulta** para criar um banco de dados.</span><span class="sxs-lookup"><span data-stu-id="709c6-169">On the menu bar, choose **SQL**, **Transact-SQL Editor**, **New Query** to create a database.</span></span> <span data-ttu-id="709c6-170">Caso sejam solicitados, especifique o servidor e a instância de banco de dados.</span><span class="sxs-lookup"><span data-stu-id="709c6-170">If prompted, specify your database server and instance.</span></span>
<br />

2. <span data-ttu-id="709c6-171">Copie e cole o conteúdo do script de banco de dados que cria o banco de dados do aluno, conforme descrito no [documentação do Entity Framework](https://msdn.microsoft.com/data/JJ614587.aspx) no Centro de desenvolvedores de dados.</span><span class="sxs-lookup"><span data-stu-id="709c6-171">Copy and paste the contents of the database script that creates the Student database, as described in the [Entity Framework documentation](https://msdn.microsoft.com/data/JJ614587.aspx) in the Data Developer Center.</span></span>
<br />

3. <span data-ttu-id="709c6-172">Execute o script SQL escolhendo o botão de barra de ferramentas com o símbolo de triângulo ou escolhendo as teclas Ctrl + Q.</span><span class="sxs-lookup"><span data-stu-id="709c6-172">Run the SQL script by choosing the toolbar button with the triangle symbol or choosing the Ctrl+Q keys.</span></span>
<br />

4. <span data-ttu-id="709c6-173">Em **Server Explorer**, abra o menu de atalho para **conexões de dados**, escolha **Adicionar Conexão**e, em seguida, digite o nome do servidor de banco de dados, o nome da instância e o banco de dados de escola.</span><span class="sxs-lookup"><span data-stu-id="709c6-173">In **Server Explorer**, open the shortcut menu for **Data Connections**, choose **Add Connection**, and then enter the name of the database server, the name of the instance name, and the School database.</span></span>
<br />

5. <span data-ttu-id="709c6-174">Criar um projeto c# ou Visual Basic aplicativo de Console, abra o menu de atalho, escolha **Adicionar Novo Item**e, em seguida, escolha **modelo de dados de entidade ADO.NET**.</span><span class="sxs-lookup"><span data-stu-id="709c6-174">Create a C# or Visual Basic Console Application project, open its shortcut menu, choose **Add New Item**, and then choose **ADO.NET Entity Data Model**.</span></span>
<br />  <span data-ttu-id="709c6-175">O Assistente do Modelo de Dados de Entidade será aberto.</span><span class="sxs-lookup"><span data-stu-id="709c6-175">The Entity Data Model Wizard opens.</span></span> <span data-ttu-id="709c6-176">Ao usar este assistente, você poderá escolher como deseja criar o Modelo de Dados de Entidade.</span><span class="sxs-lookup"><span data-stu-id="709c6-176">By using this wizard, you can choose how you want to create the Entity Data Model.</span></span>
<br />

6. <span data-ttu-id="709c6-177">Em **escolher o modelo de conteúdo**, selecione o **gerar do banco de dados** caixa de seleção.</span><span class="sxs-lookup"><span data-stu-id="709c6-177">Under **Choose Model Contents**, select the **Generate from database** check box.</span></span>
<br />

7. <span data-ttu-id="709c6-178">Na próxima página, escolha o banco de dados escolar recém-criado como a conexão de dados.</span><span class="sxs-lookup"><span data-stu-id="709c6-178">On the next page, choose your newly created School database as the data connection.</span></span>
<br />  <span data-ttu-id="709c6-179">Deve ser semelhante a esta conexão  **&lt;servername&gt;.&lt; InstanceName&gt;. School.dbo**.</span><span class="sxs-lookup"><span data-stu-id="709c6-179">This connection should resemble **&lt;servername&gt;.&lt;instancename&gt;.School.dbo**.</span></span>
<br />

8. <span data-ttu-id="709c6-180">Copie sua cadeia de conexão de entidade para a Área de Transferência porque essa cadeia de caracteres pode ser importante posteriormente.</span><span class="sxs-lookup"><span data-stu-id="709c6-180">Copy your entity connection string to the Clipboard because that string might be important later.</span></span>
<br />

9. <span data-ttu-id="709c6-181">Verifique se a caixa de seleção para salvar a cadeia de caracteres de conexão de entidade para o **App. config** arquivo está selecionado e anote o valor de cadeia de caracteres na caixa de texto, que deve ajudá-lo a localizar a cadeia de caracteres de conexão mais tarde, se necessário.</span><span class="sxs-lookup"><span data-stu-id="709c6-181">Make sure the check box to save the entity connection string to the **App.Config** file is selected, and make note of the string value in the text box, which should help you locate the connection string later, if needed.</span></span>
<br />

10. <span data-ttu-id="709c6-182">Na próxima página, escolha **tabelas** e **procedimentos armazenados e funções**.</span><span class="sxs-lookup"><span data-stu-id="709c6-182">On the next page, choose **Tables** and **Stored Procedures and Functions**.</span></span>
<br />  <span data-ttu-id="709c6-183">Ao escolher esses nós de nível superior, você escolherá todas as tabelas, procedimentos armazenados e funções.</span><span class="sxs-lookup"><span data-stu-id="709c6-183">By choosing these top-level nodes, you choose all tables, stored procedures, and functions.</span></span> <span data-ttu-id="709c6-184">Você também pode escolhê-los individualmente se desejar.</span><span class="sxs-lookup"><span data-stu-id="709c6-184">You can also choose these individually, if you want.</span></span>
<br />

11. <span data-ttu-id="709c6-185">Certifique-se de que as caixas de seleção para as outras configurações estejam selecionadas.</span><span class="sxs-lookup"><span data-stu-id="709c6-185">Make sure that the check boxes for the other settings are selected.</span></span>
<br />  <span data-ttu-id="709c6-186">A primeira **Pluralizar ou singularizar nomes de objetos gerados** caixa de seleção indica se deve alterar as formas singulares para plural para corresponder as convenções de nomenclatura de objetos que representam as tabelas de banco de dados.</span><span class="sxs-lookup"><span data-stu-id="709c6-186">The first **Pluralize or singularize generated object names** check box indicates whether to change singular forms to plural to match conventions in naming objects that represent database tables.</span></span> <span data-ttu-id="709c6-187">O **incluir colunas de chave estrangeira no modelo** caixa de seleção determina se deve incluir campos para os quais o objetivo é unir a outros campos nos tipos de objeto que são gerados para o esquema de banco de dados.</span><span class="sxs-lookup"><span data-stu-id="709c6-187">The **Include foreign key columns in the model** check box determines whether to include fields for which the purpose is to join to other fields in the object types that are generated for the database schema.</span></span> <span data-ttu-id="709c6-188">A terceira caixa de seleção indica se procedimentos armazenados e funções devem ser incluídos no modelo.</span><span class="sxs-lookup"><span data-stu-id="709c6-188">The third check box indicates whether to include stored procedures and functions in the model.</span></span>
<br />

12. <span data-ttu-id="709c6-189">Selecione o **concluir** botão para gerar um arquivo. edmx que contém um modelo de dados de entidade com base no banco de dados School.</span><span class="sxs-lookup"><span data-stu-id="709c6-189">Select the **Finish** button to generate an .edmx file that contains an Entity Data Model that's based on the School database.</span></span>
<br />  <span data-ttu-id="709c6-190">Um arquivo **Model1.edmx**, é adicionado ao seu projeto, e um diagrama de banco de dados é exibida.</span><span class="sxs-lookup"><span data-stu-id="709c6-190">A file, **Model1.edmx**, is added to your project, and a database diagram appears.</span></span>
<br />

13. <span data-ttu-id="709c6-191">Na barra de menus, escolha **exibição**, **outras janelas**, **Entity Data Model Browser** para exibir todos os detalhes do modelo ou **mapeamento detalhes do modelo de dados de entidade**  para abrir uma janela que mostra como o modelo de objeto gerado mapeia colunas e tabelas de banco de dados.</span><span class="sxs-lookup"><span data-stu-id="709c6-191">On the menu bar, choose **View**, **Other Windows**, **Entity Data Model Browser** to view all the details of the model or **Entity Data Model Mapping Details** to open a window that shows how the generated object model maps onto database tables and columns.</span></span>
<br />


## <a name="next-steps"></a><span data-ttu-id="709c6-192">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="709c6-192">Next Steps</span></span>
<span data-ttu-id="709c6-193">Explore outras consultas, observando os operadores de consulta disponíveis conforme listado em [expressões de consulta](../../language-reference/query-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="709c6-193">Explore other queries by looking at the available query operators as listed in [Query Expressions](../../language-reference/query-expressions.md).</span></span>


## <a name="see-also"></a><span data-ttu-id="709c6-194">Consulte também</span><span class="sxs-lookup"><span data-stu-id="709c6-194">See Also</span></span>
[<span data-ttu-id="709c6-195">Provedores de Tipos</span><span class="sxs-lookup"><span data-stu-id="709c6-195">Type Providers</span></span>](index.md)

[<span data-ttu-id="709c6-196">Tipo EdmxFile</span><span class="sxs-lookup"><span data-stu-id="709c6-196">EdmxFile Type Provider</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/edmxfile-type-provider-%5bfsharp%5d)

[<span data-ttu-id="709c6-197">Instruções passo a passo: acessando um banco de dados SQL por meio de provedores de tipos e entidades</span><span class="sxs-lookup"><span data-stu-id="709c6-197">Walkthrough: Accessing a SQL Database by Using Type Providers and Entities</span></span>](accessing-a-sql-database-entities.md)

[<span data-ttu-id="709c6-198">Entity Framework</span><span class="sxs-lookup"><span data-stu-id="709c6-198">Entity Framework</span></span>](https://msdn.microsoft.com/data/ef)

[<span data-ttu-id="709c6-199">Visão geral do arquivo. edmx</span><span class="sxs-lookup"><span data-stu-id="709c6-199">.edmx File Overview</span></span>](https://msdn.microsoft.com/library/f4c8e7ce-1db6-417e-9759-15f8b55155d4)

[<span data-ttu-id="709c6-200">Gerador EDM &#40;EdmGen.exe&#41;</span><span class="sxs-lookup"><span data-stu-id="709c6-200">EDM Generator &#40;EdmGen.exe&#41;</span></span>](https://msdn.microsoft.com/library/bb387165)

