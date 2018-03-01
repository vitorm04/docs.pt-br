---
title: "Instruções passo a passo: gerando tipos F# com base em um arquivo DBML (F#)"
description: "Saiba como criar tipos F # para dados de um banco de dados em F # 3.0 quando você tiver informações de esquema codificadas em um arquivo dbml."
keywords: "visual f#, f#, programação funcional"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 6fbb6ccc-248f-4226-95e9-f6f99541dbe4
ms.openlocfilehash: 3cd8df9becac0d1a8842eb22e2f772eee6307acf
ms.sourcegitcommit: 655fd4f78741967f80c409cef98347fdcf77857d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2018
---
# <a name="walkthrough-generating-f-types-from-a-dbml-file"></a><span data-ttu-id="f3b12-104">Instruções passo a passo: gerando tipos F# com base em um arquivo DBML</span><span class="sxs-lookup"><span data-stu-id="f3b12-104">Walkthrough: Generating F# Types from a DBML File</span></span>

> [!NOTE]
<span data-ttu-id="f3b12-105">Este guia foi escrito para F # 3.0 e será atualizado.</span><span class="sxs-lookup"><span data-stu-id="f3b12-105">This guide was written for F# 3.0 and will be updated.</span></span>  <span data-ttu-id="f3b12-106">Consulte [FSharp.Data](https://fsharp.github.io/FSharp.Data/) para provedores de tipo de plataforma cruzada atualizados.</span><span class="sxs-lookup"><span data-stu-id="f3b12-106">See [FSharp.Data](https://fsharp.github.io/FSharp.Data/) for up-to-date, cross-platform type providers.</span></span>

> [!NOTE]
<span data-ttu-id="f3b12-107">Os links de referência de API levará você para o MSDN.</span><span class="sxs-lookup"><span data-stu-id="f3b12-107">The API reference links will take you to MSDN.</span></span>  <span data-ttu-id="f3b12-108">A referência da API docs.microsoft.com não está completa.</span><span class="sxs-lookup"><span data-stu-id="f3b12-108">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="f3b12-109">Este passo a passo para F # 3.0 descreve como criar tipos de dados de um banco de dados quando você tiver informações de esquema codificadas em um arquivo dbml.</span><span class="sxs-lookup"><span data-stu-id="f3b12-109">This walkthrough for F# 3.0 describes how to create types for data from a database when you have schema information encoded in a .dbml file.</span></span> <span data-ttu-id="f3b12-110">O LINQ to SQL usa esse formato de arquivo para representar o esquema de banco de dados.</span><span class="sxs-lookup"><span data-stu-id="f3b12-110">LINQ to SQL uses this file format to represent database schema.</span></span> <span data-ttu-id="f3b12-111">Você pode gerar um arquivo LINQ to SQL esquema no Visual Studio usando o Designer relacional de objeto (Object Relational).</span><span class="sxs-lookup"><span data-stu-id="f3b12-111">You can generate a LINQ to SQL schema file in Visual Studio by using the Object Relational (O/R) Designer.</span></span> <span data-ttu-id="f3b12-112">Para obter mais informações, consulte [Object Relational Designer Overview](https://msdn.microsoft.com/library/bb384511.aspx) e [geração de código em LINQ to SQL](../../../../docs/framework/data/adonet/sql/linq/index.md).</span><span class="sxs-lookup"><span data-stu-id="f3b12-112">For more information, see [O/R Designer Overview](https://msdn.microsoft.com/library/bb384511.aspx) and [Code Generation in LINQ to SQL](../../../../docs/framework/data/adonet/sql/linq/index.md).</span></span>

<span data-ttu-id="f3b12-113">O provedor de tipo de linguagem de marcação de banco de dados (DBML) permite que você escreva código que usa tipos com base em um esquema de banco de dados sem a necessidade de especificar uma cadeia de caracteres de conexão estática em tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="f3b12-113">The Database Markup Language (DBML) type provider allows you to write code that uses types based on a database schema without requiring you to specify a static connection string at compile time.</span></span> <span data-ttu-id="f3b12-114">Isso pode ser útil se você precisar permitir a possibilidade de que o aplicativo final usará um banco de dados diferente, credenciais diferentes ou uma cadeia de caracteres de conexão diferentes que você pode usar para desenvolver o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f3b12-114">That can be useful if you need to allow for the possibility that the final application will use a different database, different credentials, or a different connection string than the one you use to develop the application.</span></span> <span data-ttu-id="f3b12-115">Se você tiver uma conexão direta do banco de dados que você pode usar em tempo de compilação e esse é o mesmo banco de dados e as credenciais que você ainda usará em seu aplicativo compilado, você também pode usar o provedor de tipos SQLDataConnection.</span><span class="sxs-lookup"><span data-stu-id="f3b12-115">If you have a direct database connection that you can use at compile time and this is the same database and credentials that you will eventually use in your built application, you can also use the SQLDataConnection type provider.</span></span> <span data-ttu-id="f3b12-116">Para obter mais informações, consulte [passo a passo: acessando um banco de dados SQL usando provedores de tipos](accessing-a-sql-database.md).</span><span class="sxs-lookup"><span data-stu-id="f3b12-116">For more information, see [Walkthrough: Accessing a SQL Database by Using Type Providers](accessing-a-sql-database.md).</span></span>

<span data-ttu-id="f3b12-117">Esta explicação passo a passo mostra as seguintes tarefas.</span><span class="sxs-lookup"><span data-stu-id="f3b12-117">This walkthrough illustrates the following tasks.</span></span> <span data-ttu-id="f3b12-118">Que devem ser concluídas na ordem para a passo a passo para ter êxito:</span><span class="sxs-lookup"><span data-stu-id="f3b12-118">They should be completed in this order for the walkthrough to succeed:</span></span>


- <span data-ttu-id="f3b12-119">Criando um arquivo dbml</span><span class="sxs-lookup"><span data-stu-id="f3b12-119">Creating a .dbml file</span></span>
<br />

- <span data-ttu-id="f3b12-120">Criando e configurando um projeto F #</span><span class="sxs-lookup"><span data-stu-id="f3b12-120">Creating and setting up an F# project</span></span>
<br />

- <span data-ttu-id="f3b12-121">Configurar o provedor de tipos e gerar os tipos de</span><span class="sxs-lookup"><span data-stu-id="f3b12-121">Configuring the type provider and generating the types</span></span>
<br />

- <span data-ttu-id="f3b12-122">Consultando o banco de dados</span><span class="sxs-lookup"><span data-stu-id="f3b12-122">Querying the database</span></span>
<br />


## <a name="prerequisites"></a><span data-ttu-id="f3b12-123">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="f3b12-123">Prerequisites</span></span>

## <a name="creating-a-dbml-file"></a><span data-ttu-id="f3b12-124">Criando um arquivo dbml</span><span class="sxs-lookup"><span data-stu-id="f3b12-124">Creating a .dbml file</span></span>
<span data-ttu-id="f3b12-125">Se você não tiver um banco de dados de teste em, crie um seguindo as instruções na parte inferior da [passo a passo: acessando um banco de dados SQL usando provedores de tipos](accessing-a-sql-database.md).</span><span class="sxs-lookup"><span data-stu-id="f3b12-125">If you do not have a database to test on, create one by following the instructions at the bottom of [Walkthrough: Accessing a SQL Database by Using Type Providers](accessing-a-sql-database.md).</span></span> <span data-ttu-id="f3b12-126">Se você seguir estas instruções, você criará um banco de dados chamado MyDatabase que contém algumas tabelas simples e procedimentos armazenados no SQL Server.</span><span class="sxs-lookup"><span data-stu-id="f3b12-126">If you follow these instructions, you will create a database called MyDatabase that contains a few simple tables and stored procedures on your SQL Server.</span></span>

<span data-ttu-id="f3b12-127">Se você já tiver um arquivo dbml, você pode ignorar a seção **criar e definir a um projeto F #**.</span><span class="sxs-lookup"><span data-stu-id="f3b12-127">If you already have a .dbml file, you can skip to the section, **Create and Set Up an F# Project**.</span></span> <span data-ttu-id="f3b12-128">Caso contrário, você pode criar um arquivo dbml fornecido a um banco de dados SQL e usando a linha de comando ferramenta SqlMetal.exe.</span><span class="sxs-lookup"><span data-stu-id="f3b12-128">Otherwise, you can create a .dbml file given an existing SQL database and by using the command-line tool SqlMetal.exe.</span></span>


#### <a name="to-create-a-dbml-file-by-using-sqlmetalexe"></a><span data-ttu-id="f3b12-129">Para criar um arquivo dbml usando SqlMetal.exe</span><span class="sxs-lookup"><span data-stu-id="f3b12-129">To create a .dbml file by using SqlMetal.exe</span></span>

1. <span data-ttu-id="f3b12-130">Abra um **Prompt de comando do desenvolvedor**.</span><span class="sxs-lookup"><span data-stu-id="f3b12-130">Open a **Developer Command Prompt**.</span></span>
<br />

2. <span data-ttu-id="f3b12-131">Verifique se você tem acesso ao SqlMetal.exe digitando `SqlMetal.exe /?` no prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="f3b12-131">Ensure that you have access to SqlMetal.exe by entering `SqlMetal.exe /?` at the command prompt.</span></span> <span data-ttu-id="f3b12-132">SqlMetal.exe é normalmente instalado no **SDKs do Microsoft** pasta **arquivos de programa** ou **arquivos de programa (x86)**.</span><span class="sxs-lookup"><span data-stu-id="f3b12-132">SqlMetal.exe is typically installed under the **Microsoft SDKs** folder in **Program Files** or **Program Files (x86)**.</span></span>
<br />

3. <span data-ttu-id="f3b12-133">Execute SqlMetal.exe com as seguintes opções de linha de comando.</span><span class="sxs-lookup"><span data-stu-id="f3b12-133">Run SqlMetal.exe with the following command-line options.</span></span> <span data-ttu-id="f3b12-134">Substituir por um caminho correto no lugar de `c:\destpath` para criar o arquivo dbml e inserir os valores apropriados para o servidor de banco de dados, nome da instância e o nome de banco de dados.</span><span class="sxs-lookup"><span data-stu-id="f3b12-134">Substitute an appropriate path in place of `c:\destpath` to create the .dbml file, and insert appropriate values for the database server, instance name, and database name.</span></span>
<br />

```
  SqlMetal.exe /sprocs /dbml:C:\destpath\MyDatabase.dbml /server:SERVER\INSTANCE /database:MyDatabase
```

>[!NOTE]
<span data-ttu-id="f3b12-135">Se SqlMetal.exe tiver problemas para criar o arquivo devido a problemas de permissões, altere o diretório atual para uma pasta que você tem acesso de gravação.</span><span class="sxs-lookup"><span data-stu-id="f3b12-135">If SqlMetal.exe has trouble creating the file due to permissions issues, change the current directory to a folder that you have write access to.</span></span>


4. <span data-ttu-id="f3b12-136">Você também pode examinar as outras opções de linha de comando disponíveis.</span><span class="sxs-lookup"><span data-stu-id="f3b12-136">You can also look at the other available command-line options.</span></span> <span data-ttu-id="f3b12-137">Por exemplo, há opções que você pode usar se desejar exibições e funções SQL incluídas entre os tipos gerados.</span><span class="sxs-lookup"><span data-stu-id="f3b12-137">For example, there are options you can use if you want views and SQL functions included in the generated types.</span></span> <span data-ttu-id="f3b12-138">Para obter mais informações, consulte [SqlMetal.exe &#40; Ferramenta de geração de código &#41; ](https://msdn.microsoft.com/library/bb386987).</span><span class="sxs-lookup"><span data-stu-id="f3b12-138">For more information, see [SqlMetal.exe &#40;Code Generation Tool&#41;](https://msdn.microsoft.com/library/bb386987).</span></span>
<br />


## <a name="creating-and-setting-up-an-f-project"></a><span data-ttu-id="f3b12-139">Criando e configurando um projeto F #</span><span class="sxs-lookup"><span data-stu-id="f3b12-139">Creating and setting up an F# project</span></span>
<span data-ttu-id="f3b12-140">Nesta etapa, você pode cria um projeto e adicionar referências apropriadas para usar o provedor de tipo DBML.</span><span class="sxs-lookup"><span data-stu-id="f3b12-140">In this step, you create a project and add appropriate references to use the DBML type provider.</span></span>


#### <a name="to-create-and-set-up-an-f-project"></a><span data-ttu-id="f3b12-141">Para criar e configurar um projeto de F#</span><span class="sxs-lookup"><span data-stu-id="f3b12-141">To create and set up an F# project</span></span>

1. <span data-ttu-id="f3b12-142">Adicione um novo projeto de aplicativo de Console em F # para sua solução.</span><span class="sxs-lookup"><span data-stu-id="f3b12-142">Add a new F# Console Application project to your solution.</span></span>
<br />

2. <span data-ttu-id="f3b12-143">Em **Solution Explorer**, abra o menu de atalho para **referências**e, em seguida, escolha **adicionar referência**.</span><span class="sxs-lookup"><span data-stu-id="f3b12-143">In **Solution Explorer**, open the shortcut menu for **References**, and then choose **Add Reference**.</span></span>
<br />

3. <span data-ttu-id="f3b12-144">No **Assemblies** área, escolha o **Framework** nó e, em seguida, na lista de assemblies disponíveis, escolha o **System. Data** e **System.Data.Linq**  assemblies.</span><span class="sxs-lookup"><span data-stu-id="f3b12-144">In the **Assemblies** area, choose the **Framework** node, and then, in the list of available assemblies, choose the **System.Data** and **System.Data.Linq** assemblies.</span></span>
<br />

4. <span data-ttu-id="f3b12-145">No **Assemblies** área, escolha **extensões**e, em seguida, na lista de assemblies disponíveis, escolha **FSharp.Data.TypeProviders**.</span><span class="sxs-lookup"><span data-stu-id="f3b12-145">In the **Assemblies** area, choose **Extensions**, and then, in the list of available assemblies, choose **FSharp.Data.TypeProviders**.</span></span>
<br />

5. <span data-ttu-id="f3b12-146">Escolha o **Okey** botão para adicionar referências a esses assemblies ao seu projeto.</span><span class="sxs-lookup"><span data-stu-id="f3b12-146">Choose the **OK** button to add references to these assemblies to your project.</span></span>
<br />

6. <span data-ttu-id="f3b12-147">(Opcional).</span><span class="sxs-lookup"><span data-stu-id="f3b12-147">(Optional).</span></span> <span data-ttu-id="f3b12-148">Copie o arquivo dbml que você criou na etapa anterior e, em seguida, cole o arquivo na pasta principal para o seu projeto.</span><span class="sxs-lookup"><span data-stu-id="f3b12-148">Copy the .dbml file that you created in the previous step, and paste the file in the main folder for your project.</span></span> <span data-ttu-id="f3b12-149">Esta pasta contém o arquivo de projeto (fsproj) e arquivos de código.</span><span class="sxs-lookup"><span data-stu-id="f3b12-149">This folder contains the project file (.fsproj) and code files.</span></span> <span data-ttu-id="f3b12-150">Na barra de menus, escolha **projeto**, **Add Existing Item**e, em seguida, especifique o arquivo dbml para adicioná-lo ao seu projeto.</span><span class="sxs-lookup"><span data-stu-id="f3b12-150">On the menu bar, choose **Project**, **Add Existing Item**, and then specify the .dbml file to add it to your project.</span></span> <span data-ttu-id="f3b12-151">Se você concluir essas etapas, você pode omitir o parâmetro static ResolutionFolder na próxima etapa.</span><span class="sxs-lookup"><span data-stu-id="f3b12-151">If you complete these steps, you can omit the ResolutionFolder static parameter in the next step.</span></span>
<br />

## <a name="configuring-the-type-provider"></a><span data-ttu-id="f3b12-152">Configurando o provedor de tipos</span><span class="sxs-lookup"><span data-stu-id="f3b12-152">Configuring the type provider</span></span>
<span data-ttu-id="f3b12-153">Nesta seção, você cria um provedor de tipos e gerar tipos de esquema que é descrito no arquivo dbml.</span><span class="sxs-lookup"><span data-stu-id="f3b12-153">In this section, you create a type provider and generate types from the schema that’s described in the .dbml file.</span></span>


#### <a name="to-configure-the-type-provider-and-generate-the-types"></a><span data-ttu-id="f3b12-154">Para configurar o provedor de tipos e gerar os tipos</span><span class="sxs-lookup"><span data-stu-id="f3b12-154">To configure the type provider and generate the types</span></span>

- <span data-ttu-id="f3b12-155">Adicione o código que abre o **TypeProviders** namespace e instancia o provedor de tipos para o arquivo dbml que você deseja usar.</span><span class="sxs-lookup"><span data-stu-id="f3b12-155">Add code that opens the **TypeProviders** namespace and instantiates the type provider for the .dbml file that you want to use.</span></span> <span data-ttu-id="f3b12-156">Se você adicionou o arquivo dbml ao seu projeto, você pode omitir o parâmetro estático ResolutionFolder.</span><span class="sxs-lookup"><span data-stu-id="f3b12-156">If you added the .dbml file to your project, you can omit the ResolutionFolder static parameter.</span></span>
<br />

```fsharp
open Microsoft.FSharp.Data.TypeProviders


type dbml = DbmlFile<"MyDatabase.dbml", ResolutionFolder = @"<path-to-folder-that-contains-.dbml-file>">

// This connection string can be specified at run time.
let connectionString = "Data Source=MYSERVER\INSTANCE;Initial Catalog=MyDatabase;Integrated Security=SSPI;"
let dataContext = new dbml.Mydatabase(connectionString)
```

<span data-ttu-id="f3b12-157">O tipo DataContext fornece acesso a todos os tipos gerados e herda do `System.Data.Linq.DataContext`.</span><span class="sxs-lookup"><span data-stu-id="f3b12-157">The DataContext type provides access to all the generated types and inherits from `System.Data.Linq.DataContext`.</span></span> <span data-ttu-id="f3b12-158">O provedor de tipos DbmlFile tem vários parâmetros estáticos que podem ser definidas.</span><span class="sxs-lookup"><span data-stu-id="f3b12-158">The DbmlFile type provider has various static parameters that you can set.</span></span> <span data-ttu-id="f3b12-159">Por exemplo, você pode usar um nome diferente para o tipo DataContext especificando `DataContext=MyDataContext`.</span><span class="sxs-lookup"><span data-stu-id="f3b12-159">For example, you can use a different name for the DataContext type by specifying `DataContext=MyDataContext`.</span></span> <span data-ttu-id="f3b12-160">Nesse caso, seu código semelhante ao exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="f3b12-160">In that case, your code resembles the following example:</span></span>
<br />

```fsharp
open Microsoft.FSharp.Data.TypeProviders


type dbml = DbmlFile<"MyDatabase.dbml", ContextTypeName = "MyDataContext">

// This connection string can be specified at run time.
let connectionString = "Data Source=MYSERVER\INSTANCE;Initial Catalog=MyDatabase;Integrated Security=SSPI;"
let db = new dbml.MyDataContext(connectionString)
```

## <a name="querying-the-database"></a><span data-ttu-id="f3b12-161">Consultando o banco de dados</span><span class="sxs-lookup"><span data-stu-id="f3b12-161">Querying the database</span></span>
<span data-ttu-id="f3b12-162">Nesta seção, você pode usar expressões de consulta do F # para consultar o banco de dados.</span><span class="sxs-lookup"><span data-stu-id="f3b12-162">In this section, you use F# query expressions to query the database.</span></span>


#### <a name="to-query-the-data"></a><span data-ttu-id="f3b12-163">Para consultar os dados</span><span class="sxs-lookup"><span data-stu-id="f3b12-163">To query the data</span></span>

- <span data-ttu-id="f3b12-164">Adicione código para consultar o banco de dados.</span><span class="sxs-lookup"><span data-stu-id="f3b12-164">Add code to query the database.</span></span>
<br />

```fsharp
  query {
    for row in db.Table1 do
    where (row.TestData1 > 2)
    select row
  } |> Seq.iter (fun row -> printfn "%d %s" row.TestData1 row.Name)
```

## <a name="next-steps"></a><span data-ttu-id="f3b12-165">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="f3b12-165">Next Steps</span></span>
<span data-ttu-id="f3b12-166">Você pode continuar a usar outras expressões de consulta, ou obter uma conexão de banco de dados do contexto de dados e executar operações normais de dados ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="f3b12-166">You can proceed to use other query expressions, or get a database connection from the data context and perform normal ADO.NET data operations.</span></span> <span data-ttu-id="f3b12-167">Para obter as etapas adicionais, consulte as seções depois de "Consulta os dados" em [passo a passo: acessando um banco de dados SQL usando provedores de tipos](accessing-a-sql-database.md).</span><span class="sxs-lookup"><span data-stu-id="f3b12-167">For additional steps, see the sections after "Query the Data" in [Walkthrough: Accessing a SQL Database by Using Type Providers](accessing-a-sql-database.md).</span></span>


## <a name="see-also"></a><span data-ttu-id="f3b12-168">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f3b12-168">See Also</span></span>
[<span data-ttu-id="f3b12-169">Tipo DbmlFile</span><span class="sxs-lookup"><span data-stu-id="f3b12-169">DbmlFile Type Provider</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/dbmlfile-type-provider-%5bfsharp%5d)

[<span data-ttu-id="f3b12-170">Provedores de Tipos</span><span class="sxs-lookup"><span data-stu-id="f3b12-170">Type Providers</span></span>](index.md)

[<span data-ttu-id="f3b12-171">Instruções passo a passo: acessando um banco de dados SQL por meio de provedores de tipos</span><span class="sxs-lookup"><span data-stu-id="f3b12-171">Walkthrough: Accessing a SQL Database by Using Type Providers</span></span>](accessing-a-sql-database.md)

[<span data-ttu-id="f3b12-172">SqlMetal.exe &#40; Ferramenta de geração de código &#41;</span><span class="sxs-lookup"><span data-stu-id="f3b12-172">SqlMetal.exe &#40;Code Generation Tool&#41;</span></span>](https://msdn.microsoft.com/library/bb386987)

[<span data-ttu-id="f3b12-173">Expressões de Consulta</span><span class="sxs-lookup"><span data-stu-id="f3b12-173">Query Expressions</span></span>](../../language-reference/query-expressions.md)
