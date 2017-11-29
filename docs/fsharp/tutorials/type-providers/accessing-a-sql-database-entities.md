---
title: "Instruções passo a passo: acessando um banco de dados SQL por meio de provedores de tipos e entidades (F#)"
description: 'Saiba como acessar dados de tipo para um banco de dados do SQL com base no modelo de dados de entidade ADO.NET em F # 3.0.'
keywords: "visual f#, f#, programação funcional"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: dc82a932-5401-4d19-9fb3-92c50d8db514
ms.openlocfilehash: 770d405921758eeb7e8d7ea98b95c29c99631475
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="walkthrough-accessing-a-sql-database-by-using-type-providers-and-entities"></a><span data-ttu-id="76a31-104">Instruções passo a passo: acessando um banco de dados SQL por meio de provedores de tipos e entidades</span><span class="sxs-lookup"><span data-stu-id="76a31-104">Walkthrough: Accessing a SQL Database by Using Type Providers and Entities</span></span>

> [!NOTE]
<span data-ttu-id="76a31-105">Este guia foi escrito para F # 3.0 e será atualizado.</span><span class="sxs-lookup"><span data-stu-id="76a31-105">This guide was written for F# 3.0 and will be updated.</span></span>  <span data-ttu-id="76a31-106">Consulte [FSharp.Data](http://fsharp.github.io/FSharp.Data/) para provedores de tipo de plataforma cruzada atualizados.</span><span class="sxs-lookup"><span data-stu-id="76a31-106">See [FSharp.Data](http://fsharp.github.io/FSharp.Data/) for up-to-date, cross-platform type providers.</span></span>

> [!NOTE]
<span data-ttu-id="76a31-107">Os links de referência de API levará você para o MSDN.</span><span class="sxs-lookup"><span data-stu-id="76a31-107">The API reference links will take you to MSDN.</span></span>  <span data-ttu-id="76a31-108">A referência da API docs.microsoft.com não está completa.</span><span class="sxs-lookup"><span data-stu-id="76a31-108">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="76a31-109">Esse guia passo a passo para o F# 3.0 mostra como acessar dados tipados para um banco de dados SQL baseado no Modelo de Dados de Entidade ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="76a31-109">This walkthrough for F# 3.0 shows you how to access typed data for a SQL database based on the ADO.NET Entity Data Model.</span></span> <span data-ttu-id="76a31-110">Esse guia passo a passo mostra como configurar o provedor de tipos `SqlEntityConnection` do F# para uso com um banco de dados SQL, como criar consultas para dados, como chamar procedimentos armazenados no banco de dados, bem como usar alguns métodos e tipos do ADO.NET Entity Framework para atualizar o banco de dados.</span><span class="sxs-lookup"><span data-stu-id="76a31-110">This walkthrough shows you how to set up the F# `SqlEntityConnection` type provider for use with a SQL database, how to write queries against the data, how to call stored procedures on the database, as well as how to use some of the ADO.NET Entity Framework types and methods to update the database.</span></span>

<span data-ttu-id="76a31-111">Esse guia passo a passo ilustra as seguintes tarefas que você deve executar nesta ordem para que as instruções sejam bem-sucedidas:</span><span class="sxs-lookup"><span data-stu-id="76a31-111">This walkthrough illustrates the following tasks, which you should perform in this order for the walkthrough to succeed:</span></span>


- <span data-ttu-id="76a31-112">Criar o banco de dados escolar</span><span class="sxs-lookup"><span data-stu-id="76a31-112">Create the School database</span></span>
<br />

- <span data-ttu-id="76a31-113">Criar e configurar um projeto F#</span><span class="sxs-lookup"><span data-stu-id="76a31-113">Create and configure an F# project</span></span>
<br />

- <span data-ttu-id="76a31-114">Configurar o provedor de tipos e conecte-se ao modelo de dados de entidade</span><span class="sxs-lookup"><span data-stu-id="76a31-114">Configure the type provider and connect to the Entity Data Model</span></span>
<br />

- <span data-ttu-id="76a31-115">Consulta o banco de dados</span><span class="sxs-lookup"><span data-stu-id="76a31-115">Query the database</span></span>
<br />

- <span data-ttu-id="76a31-116">Atualizando o banco de dados</span><span class="sxs-lookup"><span data-stu-id="76a31-116">Updating the database</span></span>
<br />


## <a name="prerequisites"></a><span data-ttu-id="76a31-117">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="76a31-117">Prerequisites</span></span>
<span data-ttu-id="76a31-118">Você deve ter acesso a um servidor que esteja executando um SQL Server onde você possa criar um banco de dados para concluir estas etapas.</span><span class="sxs-lookup"><span data-stu-id="76a31-118">You must have access to a server that's running SQL Server where you can create a database to complete these steps.</span></span>

## <a name="create-the-school-database"></a><span data-ttu-id="76a31-119">Criar o banco de dados escolar</span><span class="sxs-lookup"><span data-stu-id="76a31-119">Create the School database</span></span>
<span data-ttu-id="76a31-120">Você pode criar o banco de dados escolar em qualquer servidor que esteja executando um SQL Server ao qual você tenha acesso administrativo ou pode usar LocalDB.</span><span class="sxs-lookup"><span data-stu-id="76a31-120">You can create the School database on any server that's running SQL Server to which you have administrative access, or you can use LocalDB.</span></span>


#### <a name="to-create-the-school-database"></a><span data-ttu-id="76a31-121">Para criar o banco de dados escolar</span><span class="sxs-lookup"><span data-stu-id="76a31-121">To create the School database</span></span>

1. <span data-ttu-id="76a31-122">Em **Server Explorer**, abra o menu de atalho para o **conexões de dados** nó e, em seguida, escolha **Adicionar Conexão**.</span><span class="sxs-lookup"><span data-stu-id="76a31-122">In **Server Explorer**, open the shortcut menu for the **Data Connections** node, and then choose **Add Connection**.</span></span>
<br />  <span data-ttu-id="76a31-123">O **Adicionar Conexão** caixa de diálogo é exibida.</span><span class="sxs-lookup"><span data-stu-id="76a31-123">The **Add Connection** dialog box appears.</span></span>
<br />

2. <span data-ttu-id="76a31-124">No **nome do servidor** caixa, especifique o nome de uma instância do SQL Server ao qual você tem acesso administrativo ou especificar (localdb\v11.0) se você não tiver acesso a um servidor.</span><span class="sxs-lookup"><span data-stu-id="76a31-124">In the **Server name** box, specify the name of an instance of SQL Server to which you have administrative access, or specify (localdb\v11.0) if you don't have access to a server.</span></span>
<br />  <span data-ttu-id="76a31-125">O SQL Server Express LocalDB oferece um servidor de banco de dados leve para desenvolvimento e teste em seu computador.</span><span class="sxs-lookup"><span data-stu-id="76a31-125">SQL Server Express LocalDB provides a lightweight database server for development and testing on your machine.</span></span> <span data-ttu-id="76a31-126">Para obter mais informações sobre o LocalDB, consulte [passo a passo: Criando um arquivo de banco de dados Local no Visual Studio](https://msdn.microsoft.com/library/ms233763.aspx).</span><span class="sxs-lookup"><span data-stu-id="76a31-126">For more information about LocalDB, see [Walkthrough: Creating a Local Database File in Visual Studio](https://msdn.microsoft.com/library/ms233763.aspx).</span></span>
<br />  <span data-ttu-id="76a31-127">É criado um novo nó no **Server Explorer** em **conexões de dados**.</span><span class="sxs-lookup"><span data-stu-id="76a31-127">A new node is created in **Server Explorer** under **Data Connections**.</span></span>
<br />

3. <span data-ttu-id="76a31-128">Abra o menu de atalho para o novo nó de conexão e, em seguida, escolha **nova consulta**.</span><span class="sxs-lookup"><span data-stu-id="76a31-128">Open the shortcut menu for the new connection node, and then choose **New Query**.</span></span>
<br />

4. <span data-ttu-id="76a31-129">Abra [criando o banco de dados de exemplo School](http://go.microsoft.com/fwlink/?LinkID=237278) no site da Microsoft e, em seguida, copiar e colar o script de banco de dados que cria o banco de dados do aluno na janela do editor.</span><span class="sxs-lookup"><span data-stu-id="76a31-129">Open [Creating the School Sample Database](http://go.microsoft.com/fwlink/?LinkID=237278) on the Microsoft website, and then copy and paste the database script that creates the Student database into the editor window.</span></span>
<br />


## <span data-ttu-id="76a31-130"><a name="BKMK_CreateConfigFSProj"> </a></span><span class="sxs-lookup"><span data-stu-id="76a31-130"><a name="BKMK_CreateConfigFSProj"> </a></span></span>

## <a name="create-and-configure-an-f-project"></a><span data-ttu-id="76a31-131">Criar e configurar um projeto F#</span><span class="sxs-lookup"><span data-stu-id="76a31-131">Create and configure an F# project</span></span>
<span data-ttu-id="76a31-132">Nesta etapa, você criará um projeto e o configurará para usar um provedor de tipos.</span><span class="sxs-lookup"><span data-stu-id="76a31-132">In this step, you create a project and set it up to use a type provider.</span></span>


#### <a name="to-create-and-configure-an-f-project"></a><span data-ttu-id="76a31-133">Para criar e configurar um projeto F#</span><span class="sxs-lookup"><span data-stu-id="76a31-133">To create and configure an F# project</span></span>

1. <span data-ttu-id="76a31-134">Fechar o projeto anterior, crie outro projeto e nomeie-o **SchoolEDM**.</span><span class="sxs-lookup"><span data-stu-id="76a31-134">Close the previous project, create another project, and name it **SchoolEDM**.</span></span>
<br />

2. <span data-ttu-id="76a31-135">Em **Solution Explorer**, abra o menu de atalho para **referências**e, em seguida, escolha **adicionar referência**.</span><span class="sxs-lookup"><span data-stu-id="76a31-135">In **Solution Explorer**, open the shortcut menu for **References**, and then choose **Add Reference**.</span></span>
<br />

3. <span data-ttu-id="76a31-136">Escolha o **Framework** nó e, em seguida, no **Framework** , escolha **System. Data**, **System.Data.Entity**e **System.Data.Linq**.</span><span class="sxs-lookup"><span data-stu-id="76a31-136">Choose the **Framework** node, and then, in the **Framework** list, choose **System.Data**, **System.Data.Entity**,  and **System.Data.Linq**.</span></span>
<br />

4. <span data-ttu-id="76a31-137">Escolha o **extensões** nó, adicione uma referência para o [FSharp.Data.TypeProviders](https://msdn.microsoft.com/library/a858f859-047a-44ab-945b-8731d7a0e6e3) assembly e, em seguida, escolha o **Okey** botão para ignorar a caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="76a31-137">Choose the **Extensions** node, add a reference to the [FSharp.Data.TypeProviders](https://msdn.microsoft.com/library/a858f859-047a-44ab-945b-8731d7a0e6e3) assembly, and then choose the **OK** button to dismiss the dialog box.</span></span>
<br />

5. <span data-ttu-id="76a31-138">Adicione o código a seguir para definir um módulo interno e abrir namespaces apropriados.</span><span class="sxs-lookup"><span data-stu-id="76a31-138">Add the following code to define an internal module and open appropriate namespaces.</span></span> <span data-ttu-id="76a31-139">O provedor de tipos pode injetar tipos somente em um namespace particular ou interno.</span><span class="sxs-lookup"><span data-stu-id="76a31-139">The type provider can inject types only into a private or internal namespace.</span></span>
<br />

```fsharp
module internal SchoolEDM

open System.Data.Linq
open System.Data.Entity
open Microsoft.FSharp.Data.TypeProviders
```

6. <span data-ttu-id="76a31-140">Para executar o código neste passo a passo interativamente como um script em vez de como um programa compilado, abra o menu de atalho para o nó do projeto, escolha **Adicionar Novo Item**, adicione um arquivo de script F # e, em seguida, adicione o código de cada etapa no script.</span><span class="sxs-lookup"><span data-stu-id="76a31-140">To run the code in this walkthrough interactively as a script instead of as a compiled program, open the shortcut menu for the project node, choose **Add New Item**, add an F# script file, and then add the code in each step to the script.</span></span> <span data-ttu-id="76a31-141">Para carregar as referências de assembly, adicione as linhas a seguir.</span><span class="sxs-lookup"><span data-stu-id="76a31-141">To load the assembly references, add the following lines.</span></span>
<br />

```fsharp
#r "System.Data.Entity.dll"
#r "FSharp.Data.TypeProviders.dll"
#r "System.Data.Linq.dll"
```

7. <span data-ttu-id="76a31-142">Realce cada bloco de código conforme o adiciona e escolha as teclas Alt + Enter para executá-lo em F# Interativo.</span><span class="sxs-lookup"><span data-stu-id="76a31-142">Highlight each block of code as you add it, and choose the Alt + Enter keys to run it in F# Interactive.</span></span>
<br />

## <a name="configure-the-type-provider-and-connect-to-the-entity-data-model"></a><span data-ttu-id="76a31-143">Configurar o provedor de tipos e conectar ao Modelo de Dados de Entidade</span><span class="sxs-lookup"><span data-stu-id="76a31-143">Configure the type provider, and connect to the Entity Data Model</span></span>
<span data-ttu-id="76a31-144">Nesta etapa, você configura um provedor de tipos com uma conexão de dados e obtém um contexto de dados que permite trabalhar com dados.</span><span class="sxs-lookup"><span data-stu-id="76a31-144">In this step, you set up a type provider with a data connection and obtain a data context that allows you to work with data.</span></span>


#### <a name="to-configure-the-type-provider-and-connect-to-the-entity-data-model"></a><span data-ttu-id="76a31-145">Para configurar o provedor de tipos e conectar ao Modelo de Dados de Entidade</span><span class="sxs-lookup"><span data-stu-id="76a31-145">To configure the type provider, and connect to the Entity Data Model</span></span>

1. <span data-ttu-id="76a31-146">Insira o código a seguir para configurar o provedor de tipos `SqlEntityConnection` que gera tipos do F# com base no Modelo de Dados de Entidade que você criou anteriormente.</span><span class="sxs-lookup"><span data-stu-id="76a31-146">Enter the following code to configure the `SqlEntityConnection` type provider that generates F# types based on the Entity Data Model that you created previously.</span></span> <span data-ttu-id="76a31-147">Em vez da cadeia de conexão completa do EDMX, use apenas a cadeia de conexão SQL.</span><span class="sxs-lookup"><span data-stu-id="76a31-147">Instead of the full EDMX connection string, use only the SQL connection string.</span></span>
<br />

```fsharp
type private EntityConnection = SqlEntityConnection<ConnectionString="Server=SERVER\InstanceName;Initial Catalog=School;Integrated Security=SSPI;MultipleActiveResultSets=true",Pluralize = true>
```

  <span data-ttu-id="76a31-148">Esta ação configura um provedor de tipos com a conexão de banco de dados que você criou anteriormente.</span><span class="sxs-lookup"><span data-stu-id="76a31-148">This action sets up a type provider with the database connection that you created earlier.</span></span> <span data-ttu-id="76a31-149">A propriedade `MultipleActiveResultSets` é necessária quando você usa o ADO.NET Entity Framework porque essa propriedade permite que vários comandos sejam executados de modo assíncrono no banco de dados em uma conexão, isso pode ocorrer frequentemente no código do ADO.NET Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="76a31-149">The property `MultipleActiveResultSets` is needed when you use the ADO.NET Entity Framework because this property allows multiple commands to execute asynchronously on the database in one connection, which can occur frequently in ADO.NET Entity Framework code.</span></span> <span data-ttu-id="76a31-150">Para obter mais informações, consulte [vários conjuntos de MARS (resultados ativos)](/sql/relational-databases/native-client/features/using-multiple-active-result-sets-mars).</span><span class="sxs-lookup"><span data-stu-id="76a31-150">For more information, see [Multiple Active Result Sets (MARS)](/sql/relational-databases/native-client/features/using-multiple-active-result-sets-mars).</span></span>
<br />

2. <span data-ttu-id="76a31-151">Obtenha o contexto de dados que é um objeto com tabelas do banco de dados como propriedades e procedimentos armazenados e funções do banco de dados como métodos.</span><span class="sxs-lookup"><span data-stu-id="76a31-151">Get the data context, which is an object that contains the database tables as properties and the database stored procedures and functions as methods.</span></span>
<br />

```fsharp
let context = EntityConnection.GetDataContext()
```

## <a name="querying-the-database"></a><span data-ttu-id="76a31-152">Consultando o banco de dados</span><span class="sxs-lookup"><span data-stu-id="76a31-152">Querying the database</span></span>
<span data-ttu-id="76a31-153">Nesta etapa, você usará expressões de consulta F# para executar várias consultas no banco de dados.</span><span class="sxs-lookup"><span data-stu-id="76a31-153">In this step, you use F# query expressions to execute various queries on the database.</span></span>


#### <a name="to-query-the-data"></a><span data-ttu-id="76a31-154">Para consultar os dados</span><span class="sxs-lookup"><span data-stu-id="76a31-154">To query the data</span></span>

- <span data-ttu-id="76a31-155">Insira o código a seguir para consultar os dados do modelo de dados de entidade.</span><span class="sxs-lookup"><span data-stu-id="76a31-155">Enter the following code to query the data from the entity data model.</span></span> <span data-ttu-id="76a31-156">Observe o efeito de Pluralize = true que altera Course para Courses e Person para People na tabela de banco de dados.</span><span class="sxs-lookup"><span data-stu-id="76a31-156">Note the effect of Pluralize = true, which changes the database table Course to Courses and Person to People.</span></span>
<br />

```fsharp
query { 
  for course in context.Courses do
  select course
} |> Seq.iter (fun course -> printfn "%s" course.Title)

query { 
  for person in context.People do
  select person 
} |> Seq.iter (fun person -> printfn "%s %s" person.FirstName person.LastName)

// Add a where clause to filter results.
query {
  for course in context.Courses do
  where (course.DepartmentID = 1)
  select course
} |> Seq.iter (fun course -> printfn "%s" course.Title)

// Join two tables.
query { 
  for course in context.Courses do
  join dept in context.Departments on (course.DepartmentID = dept.DepartmentID)
  select (course, dept.Name) 
} |> Seq.iter (fun (course, deptName) -> printfn "%s %s" course.Title deptName)
```

## <a name="updating-the-database"></a><span data-ttu-id="76a31-157">Atualizando o banco de dados</span><span class="sxs-lookup"><span data-stu-id="76a31-157">Updating the database</span></span>
<span data-ttu-id="76a31-158">Para atualizar o banco de dados, use as classes e os métodos do Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="76a31-158">To update the database, you use the Entity Framework classes and methods.</span></span> <span data-ttu-id="76a31-159">Você pode usar dois tipos de contexto de dados com o provedor de tipos SQLEntityConnection.</span><span class="sxs-lookup"><span data-stu-id="76a31-159">You can use two types of data context with the SQLEntityConnection type provider.</span></span> <span data-ttu-id="76a31-160">Primeiro, `ServiceTypes.SimpleDataContextTypes.EntityContainer` é o contexto de dados simplificado que inclui somente as propriedades fornecidas que representam tabelas e colunas do banco de dados.</span><span class="sxs-lookup"><span data-stu-id="76a31-160">First, `ServiceTypes.SimpleDataContextTypes.EntityContainer` is the simplified data context, which includes only the provided properties that represent database tables and columns.</span></span> <span data-ttu-id="76a31-161">Segundo, o contexto de dados completo é uma instância da classe `System.Data.Objects.ObjectContext` do Entity Framework que contém o método `System.Data.Objects.ObjectContext.AddObject(System.String,System.Object)` para adicionar linhas ao banco de dados.</span><span class="sxs-lookup"><span data-stu-id="76a31-161">Second, the full data context is an instance of the Entity Framework class `System.Data.Objects.ObjectContext`, which contains the method `System.Data.Objects.ObjectContext.AddObject(System.String,System.Object)` to add rows to the database.</span></span> <span data-ttu-id="76a31-162">O Entity Framework reconhece as tabelas e os relacionamentos entre elas, assim, ele impõe consistência ao banco de dados.</span><span class="sxs-lookup"><span data-stu-id="76a31-162">The Entity Framework recognizes the tables and the relationships between them, so it enforces database consistency.</span></span>


#### <a name="to-update-the-database"></a><span data-ttu-id="76a31-163">Para atualizar o banco de dados</span><span class="sxs-lookup"><span data-stu-id="76a31-163">To update the database</span></span>

1. <span data-ttu-id="76a31-164">Adicione o código a seguir ao seu programa.</span><span class="sxs-lookup"><span data-stu-id="76a31-164">Add the following code to your program.</span></span> <span data-ttu-id="76a31-165">Neste exemplo, você adiciona dois objetos com um relacionamento entre eles e um instrutor e uma atribuição comercial.</span><span class="sxs-lookup"><span data-stu-id="76a31-165">In this example, you add two objects with a relationship between them, and you add an instructor and an office assignment.</span></span> <span data-ttu-id="76a31-166">A tabela `OfficeAssignments` contém a coluna `InstructorID` que faz referência à coluna `PersonID` na tabela `Person`.</span><span class="sxs-lookup"><span data-stu-id="76a31-166">The table `OfficeAssignments` contains the `InstructorID` column, which references the `PersonID` column in the `Person` table.</span></span>
<br />

```fsharp
// The full data context
let fullContext = context.DataContext

// A helper function.
let nullable value = new System.Nullable<_>(value)

let addInstructor(lastName, firstName, hireDate, office) =
  let hireDate = DateTime.Parse(hireDate)
  let newPerson = new EntityConnection.ServiceTypes.Person(LastName = lastName,
                                                           FirstName = firstName,
                                                           HireDate = nullable hireDate)
  fullContext.AddObject("People", newPerson)

  let newOffice = new EntityConnection.ServiceTypes.OfficeAssignment(Location = office)

  fullContext.AddObject("OfficeAssignments", newOffice)
  fullContext.CommandTimeout <- nullable 1000
  fullContext.SaveChanges() |> printfn "Saved changes: %d object(s) modified."

addInstructor("Parker", "Darren", "1/1/1998", "41/3720")
```

<span data-ttu-id="76a31-167">Nada será alterado no banco de dados até que você chame `System.Data.Objects.ObjectContext.SaveChanges`.</span><span class="sxs-lookup"><span data-stu-id="76a31-167">Nothing is changed in the database until you call `System.Data.Objects.ObjectContext.SaveChanges`.</span></span>
<br />

2. <span data-ttu-id="76a31-168">Agora, restaure o banco de dados ao seu estado anterior ao excluir os objetos que você adicionou.</span><span class="sxs-lookup"><span data-stu-id="76a31-168">Now restore the database to its earlier state by deleting the objects that you added.</span></span>
<br />

```fsharp
let deleteInstructor(lastName, firstName) =
  query {
    for person in context.People do
    where (person.FirstName = firstName &&
           person.LastName = lastName)
    select person
  } |> Seq.iter (fun person->
                    query {
                      for officeAssignment in context.OfficeAssignments do
                      where (officeAssignment.Person.PersonID = person.PersonID)
                      select officeAssignment
                    } |> Seq.iter (fun officeAssignment -> fullContext.DeleteObject(officeAssignment))

                    fullContext.DeleteObject(person))

  // The call to SaveChanges should be outside of any iteration on the queries.
  fullContext.SaveChanges() |> printfn "Saved changed: %d object(s) modified."

deleteInstructor("Parker", "Darren")
```

>[!WARNING] 
<span data-ttu-id="76a31-169">Ao usar uma expressão de consulta, lembre-se de que a consulta estará sujeita a avaliação lenta.</span><span class="sxs-lookup"><span data-stu-id="76a31-169">When you use a query expression, you must remember that the query is subject to lazy evaluation.</span></span> <span data-ttu-id="76a31-170">Portanto, o banco de dados ainda estará aberto para leitura durante quaisquer avaliações encadeadas como nos blocos de expressão lambda após cada expressão de consulta.</span><span class="sxs-lookup"><span data-stu-id="76a31-170">Therefore, the database is still open for reading during any chained evaluations, such as in the lambda expression blocks after each query expression.</span></span> <span data-ttu-id="76a31-171">Qualquer operação de banco de dados que usar explícita ou implicitamente uma transação deverá ocorrer depois que as operações de leitura forem concluídas.</span><span class="sxs-lookup"><span data-stu-id="76a31-171">Any database operation that explicitly or implicitly uses a transaction must occur after the read operations have completed.</span></span>


## <a name="next-steps"></a><span data-ttu-id="76a31-172">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="76a31-172">Next Steps</span></span>
<span data-ttu-id="76a31-173">Explore outras opções de consulta examinando os operadores de consulta disponíveis no [expressões de consulta](../../language-reference/query-expressions.md)e também Revise o [ADO.NET Entity Framework](https://msdn.microsoft.com/library/bb399572) entender qual funcionalidade está disponível para você quando você usar esse provedor de tipo.</span><span class="sxs-lookup"><span data-stu-id="76a31-173">Explore other query options by reviewing the query operators available in [Query Expressions](../../language-reference/query-expressions.md), and also review the [ADO.NET Entity Framework](https://msdn.microsoft.com/library/bb399572) to understand what functionality is available to you when you use this type provider.</span></span>


## <a name="see-also"></a><span data-ttu-id="76a31-174">Consulte também</span><span class="sxs-lookup"><span data-stu-id="76a31-174">See Also</span></span>
[<span data-ttu-id="76a31-175">Provedores de Tipos</span><span class="sxs-lookup"><span data-stu-id="76a31-175">Type Providers</span></span>](index.md)

[<span data-ttu-id="76a31-176">Tipo SqlEntityConnection</span><span class="sxs-lookup"><span data-stu-id="76a31-176">SqlEntityConnection Type Provider</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/sqlentityconnection-type-provider-%5bfsharp%5d)

[<span data-ttu-id="76a31-177">Passo a passo: Gerando tipos F # de um arquivo de esquema EDMX</span><span class="sxs-lookup"><span data-stu-id="76a31-177">Walkthrough: Generating F# Types from an EDMX Schema File</span></span>](generating-fsharp-types-from-edmx.md)

[<span data-ttu-id="76a31-178">ADO.NET Entity Framework</span><span class="sxs-lookup"><span data-stu-id="76a31-178">ADO.NET Entity Framework</span></span>](https://msdn.microsoft.com/library/bb399572)

[<span data-ttu-id="76a31-179">Visão geral do arquivo. edmx</span><span class="sxs-lookup"><span data-stu-id="76a31-179">.edmx File Overview</span></span>](https://msdn.microsoft.com/library/f4c8e7ce-1db6-417e-9759-15f8b55155d4)

[<span data-ttu-id="76a31-180">Gerador EDM &#40; EdmGen.exe &#41;</span><span class="sxs-lookup"><span data-stu-id="76a31-180">EDM Generator &#40;EdmGen.exe&#41;</span></span>](https://msdn.microsoft.com/library/bb387165)
