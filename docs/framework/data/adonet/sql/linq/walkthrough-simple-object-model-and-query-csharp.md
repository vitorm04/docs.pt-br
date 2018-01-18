---
title: 'Passo a passo: modelo e consulta de objeto simples (C#)'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 419961cc-92d6-45f5-ae8a-d485bdde3a37
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 444692cb035d97b0fe57c1ea9ba7802491ca2160
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="walkthrough-simple-object-model-and-query-c"></a><span data-ttu-id="a8303-102">Passo a passo: modelo e consulta de objeto simples (C#)</span><span class="sxs-lookup"><span data-stu-id="a8303-102">Walkthrough: Simple Object Model and Query (C#)</span></span>
<span data-ttu-id="a8303-103">Este passo a passo fornece um cenário completo fundamental do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] com complexidades mínimas.</span><span class="sxs-lookup"><span data-stu-id="a8303-103">This walkthrough provides a fundamental end-to-end [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scenario with minimal complexities.</span></span> <span data-ttu-id="a8303-104">Você criará uma classe de entidade que modela a tabela Customers no banco de dados de exemplo Northwind.</span><span class="sxs-lookup"><span data-stu-id="a8303-104">You will create an entity class that models the Customers table in the sample Northwind database.</span></span> <span data-ttu-id="a8303-105">Em seguida, você criará uma consulta simples para os clientes de lista que estão localizados em Londres.</span><span class="sxs-lookup"><span data-stu-id="a8303-105">You will then create a simple query to list customers who are located in London.</span></span>  
  
 <span data-ttu-id="a8303-106">Este passo a passo é orientado a código por design para ajudar a mostrar os conceitos do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a8303-106">This walkthrough is code-oriented by design to help show [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] concepts.</span></span> <span data-ttu-id="a8303-107">Normalmente, você usa o [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] para criar seu modelo de objeto.</span><span class="sxs-lookup"><span data-stu-id="a8303-107">Normally speaking, you would use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to create your object model.</span></span>  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 <span data-ttu-id="a8303-108">Esse passo a passo foi escrito usando as configurações de desenvolvimento do Visual C#.</span><span class="sxs-lookup"><span data-stu-id="a8303-108">This walkthrough was written by using Visual C# Development Settings.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="a8303-109">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="a8303-109">Prerequisites</span></span>  
  
-   <span data-ttu-id="a8303-110">Este passo a passo usa uma pasta dedicada ("c:\linqtest5") para armazenar arquivos.</span><span class="sxs-lookup"><span data-stu-id="a8303-110">This walkthrough uses a dedicated folder ("c:\linqtest5") to hold files.</span></span> <span data-ttu-id="a8303-111">Crie essa pasta antes de iniciar o passo a passo.</span><span class="sxs-lookup"><span data-stu-id="a8303-111">Create this folder before you begin the walkthrough.</span></span>  
  
-   <span data-ttu-id="a8303-112">Este passo a passo requer o banco de dados de exemplo Northwind.</span><span class="sxs-lookup"><span data-stu-id="a8303-112">This walkthrough requires the Northwind sample database.</span></span> <span data-ttu-id="a8303-113">Se você não tiver esse banco de dados no seu computador de desenvolvimento, poderá baixá-lo no site de download da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="a8303-113">If you do not have this database on your development computer, you can download it from the Microsoft download site.</span></span> <span data-ttu-id="a8303-114">Para obter instruções, consulte [baixando bancos de dados de exemplo](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="a8303-114">For instructions, see [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span> <span data-ttu-id="a8303-115">Depois de baixar o banco de dados, copie o arquivo para a pasta c:\linqtest5.</span><span class="sxs-lookup"><span data-stu-id="a8303-115">After you have downloaded the database, copy the file to the c:\linqtest5 folder.</span></span>  
  
## <a name="overview"></a><span data-ttu-id="a8303-116">Visão geral</span><span class="sxs-lookup"><span data-stu-id="a8303-116">Overview</span></span>  
 <span data-ttu-id="a8303-117">Este passo a passo consiste em seis tarefas principais:</span><span class="sxs-lookup"><span data-stu-id="a8303-117">This walkthrough consists of six main tasks:</span></span>  
  
-   <span data-ttu-id="a8303-118">Criar uma solução [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] no [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a8303-118">Creating a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] solution in [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)].</span></span>  
  
-   <span data-ttu-id="a8303-119">Mapear uma classe para uma tabela do banco de dados.</span><span class="sxs-lookup"><span data-stu-id="a8303-119">Mapping a class to a database table.</span></span>  
  
-   <span data-ttu-id="a8303-120">Designar propriedades na classe para representar colunas do banco de dados.</span><span class="sxs-lookup"><span data-stu-id="a8303-120">Designating properties on the class to represent database columns.</span></span>  
  
-   <span data-ttu-id="a8303-121">Especificar a conexão ao banco de dados Northwind.</span><span class="sxs-lookup"><span data-stu-id="a8303-121">Specifying the connection to the Northwind database.</span></span>  
  
-   <span data-ttu-id="a8303-122">Criar uma consulta simples para execução no banco de dados.</span><span class="sxs-lookup"><span data-stu-id="a8303-122">Creating a simple query to run against the database.</span></span>  
  
-   <span data-ttu-id="a8303-123">Executar a consulta e observar os resultados.</span><span class="sxs-lookup"><span data-stu-id="a8303-123">Executing the query and observing the results.</span></span>  
  
## <a name="creating-a-linq-to-sql-solution"></a><span data-ttu-id="a8303-124">Criando uma solução LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="a8303-124">Creating a LINQ to SQL Solution</span></span>  
 <span data-ttu-id="a8303-125">Nesta primeira tarefa, você cria uma solução do [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] que contém as referências necessárias para criar e executar um projeto do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a8303-125">In this first task, you create a [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] solution that contains the necessary references to build and run a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] project.</span></span>  
  
#### <a name="to-create-a-linq-to-sql-solution"></a><span data-ttu-id="a8303-126">Para criar uma solução LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="a8303-126">To create a LINQ to SQL solution</span></span>  
  
1.  <span data-ttu-id="a8303-127">Sobre o [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] **arquivo** , aponte para **novo**e, em seguida, clique em **projeto**.</span><span class="sxs-lookup"><span data-stu-id="a8303-127">On the [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] **File** menu, point to **New**, and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="a8303-128">No **tipos de projeto** painel do **novo projeto** caixa de diálogo, clique em **Visual C#**.</span><span class="sxs-lookup"><span data-stu-id="a8303-128">In the **Project types** pane of the **New Project** dialog box, click **Visual C#**.</span></span>  
  
3.  <span data-ttu-id="a8303-129">No painel **Modelos**, clique em **Aplicativo de Console**.</span><span class="sxs-lookup"><span data-stu-id="a8303-129">In the **Templates** pane, click **Console Application**.</span></span>  
  
4.  <span data-ttu-id="a8303-130">No **nome** , digite **LinqConsoleApp**.</span><span class="sxs-lookup"><span data-stu-id="a8303-130">In the **Name** box, type **LinqConsoleApp**.</span></span>  
  
5.  <span data-ttu-id="a8303-131">No **local** , verifique se onde você deseja armazenar os arquivos de projeto.</span><span class="sxs-lookup"><span data-stu-id="a8303-131">In the **Location** box, verify where you want to store your project files.</span></span>  
  
6.  <span data-ttu-id="a8303-132">Clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="a8303-132">Click **OK**.</span></span>  
  
## <a name="adding-linq-references-and-directives"></a><span data-ttu-id="a8303-133">Adicionando referências e diretivas LINQ</span><span class="sxs-lookup"><span data-stu-id="a8303-133">Adding LINQ References and Directives</span></span>  
 <span data-ttu-id="a8303-134">Este passo a passo usa assemblies que não podem ser instalados por padrão em seu projeto.</span><span class="sxs-lookup"><span data-stu-id="a8303-134">This walkthrough uses assemblies that might not be installed by default in your project.</span></span> <span data-ttu-id="a8303-135">Se System.Data.Linq não estiver listada como uma referência em seu projeto (expanda o **referências** nó **Solution Explorer**), adicioná-lo, conforme explicado nas etapas a seguir.</span><span class="sxs-lookup"><span data-stu-id="a8303-135">If System.Data.Linq is not listed as a reference in your project (expand the **References** node in **Solution Explorer**), add it, as explained in the following steps.</span></span>  
  
#### <a name="to-add-systemdatalinq"></a><span data-ttu-id="a8303-136">Para adicionar System.Data.Linq</span><span class="sxs-lookup"><span data-stu-id="a8303-136">To add System.Data.Linq</span></span>  
  
1.  <span data-ttu-id="a8303-137">Em **Solution Explorer**, clique com botão direito **referências**e, em seguida, clique em **adicionar referência**.</span><span class="sxs-lookup"><span data-stu-id="a8303-137">In **Solution Explorer**, right-click **References**, and then click **Add Reference**.</span></span>  
  
2.  <span data-ttu-id="a8303-138">No **adicionar referência** caixa de diálogo, clique em **.NET**, clique em assembly System.Data.Linq e, em seguida, clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="a8303-138">In the **Add Reference** dialog box, click **.NET**, click the System.Data.Linq assembly, and then click **OK**.</span></span>  
  
     <span data-ttu-id="a8303-139">O assembly é adicionado ao projeto.</span><span class="sxs-lookup"><span data-stu-id="a8303-139">The assembly is added to the project.</span></span>  
  
3.  <span data-ttu-id="a8303-140">Adicione as seguintes diretivas na parte superior do **Program.cs**:</span><span class="sxs-lookup"><span data-stu-id="a8303-140">Add the following directives at the top of **Program.cs**:</span></span>  
  
     [!code-csharp[DLinqWalk1CS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1CS/cs/Program.cs#1)]  
  
## <a name="mapping-a-class-to-a-database-table"></a><span data-ttu-id="a8303-141">Mapeando uma classe para uma tabela do banco de dados</span><span class="sxs-lookup"><span data-stu-id="a8303-141">Mapping a Class to a Database Table</span></span>  
 <span data-ttu-id="a8303-142">Nesta etapa, você cria uma classe e a mapeia para uma tabela do banco de dados.</span><span class="sxs-lookup"><span data-stu-id="a8303-142">In this step, you create a class and map it to a database table.</span></span> <span data-ttu-id="a8303-143">Essa classe é chamado de um *classe da entidade*.</span><span class="sxs-lookup"><span data-stu-id="a8303-143">Such a class is termed an *entity class*.</span></span> <span data-ttu-id="a8303-144">Observe que o mapeamento é realizado simplesmente adicionando o atributo <xref:System.Data.Linq.Mapping.TableAttribute>.</span><span class="sxs-lookup"><span data-stu-id="a8303-144">Note that the mapping is accomplished by just adding the <xref:System.Data.Linq.Mapping.TableAttribute> attribute.</span></span> <span data-ttu-id="a8303-145">A propriedade <xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> especifica o nome da tabela no banco de dados.</span><span class="sxs-lookup"><span data-stu-id="a8303-145">The <xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> property specifies the name of the table in the database.</span></span>  
  
#### <a name="to-create-an-entity-class-and-map-it-to-a-database-table"></a><span data-ttu-id="a8303-146">Para criar uma classe de entidade e mapeá-la para uma tabela do banco de dados.</span><span class="sxs-lookup"><span data-stu-id="a8303-146">To create an entity class and map it to a database table</span></span>  
  
-   <span data-ttu-id="a8303-147">Digite ou cole o código a seguir em Program.cs imediatamente acima da declaração de classe `Program`:</span><span class="sxs-lookup"><span data-stu-id="a8303-147">Type or paste the following code into Program.cs immediately above the `Program` class declaration:</span></span>  
  
     [!code-csharp[DLinqWalk1CS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1CS/cs/Program.cs#2)]  
  
## <a name="designating-properties-on-the-class-to-represent-database-columns"></a><span data-ttu-id="a8303-148">Designando propriedades na classe para representar colunas do banco de dados</span><span class="sxs-lookup"><span data-stu-id="a8303-148">Designating Properties on the Class to Represent Database Columns</span></span>  
 <span data-ttu-id="a8303-149">Nesta etapa, você realiza várias tarefas.</span><span class="sxs-lookup"><span data-stu-id="a8303-149">In this step, you accomplish several tasks.</span></span>  
  
-   <span data-ttu-id="a8303-150">Você usa o atributo <xref:System.Data.Linq.Mapping.ColumnAttribute> para designar as propriedades `CustomerID` e `City` na classe de entidade como representação de colunas na tabela do banco de dados.</span><span class="sxs-lookup"><span data-stu-id="a8303-150">You use the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to designate `CustomerID` and `City` properties on the entity class as representing columns in the database table.</span></span>  
  
-   <span data-ttu-id="a8303-151">Você designa a propriedade `CustomerID` como a representação de uma coluna de chave primária no banco de dados.</span><span class="sxs-lookup"><span data-stu-id="a8303-151">You designate the `CustomerID` property as representing a primary key column in the database.</span></span>  
  
-   <span data-ttu-id="a8303-152">Você designa os campos `_CustomerID` e `_City` para armazenamento particular.</span><span class="sxs-lookup"><span data-stu-id="a8303-152">You designate `_CustomerID` and `_City` fields for private storage.</span></span> <span data-ttu-id="a8303-153">O [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] pode então armazenar e recuperar valores diretamente, em vez de usar acessadores públicos, que podem incluir lógica de negócios.</span><span class="sxs-lookup"><span data-stu-id="a8303-153">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] can then store and retrieve values directly, instead of using public accessors that might include business logic.</span></span>  
  
#### <a name="to-represent-characteristics-of-two-database-columns"></a><span data-ttu-id="a8303-154">Para representar características de duas colunas do banco de dados</span><span class="sxs-lookup"><span data-stu-id="a8303-154">To represent characteristics of two database columns</span></span>  
  
-   <span data-ttu-id="a8303-155">Digite ou cole o código a seguir em Program.cs dentro das chaves para a classe `Customer`.</span><span class="sxs-lookup"><span data-stu-id="a8303-155">Type or paste the following code into Program.cs inside the curly braces for the `Customer` class.</span></span>  
  
     [!code-csharp[DLinqWalk1CS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1CS/cs/Program.cs#3)]  
  
## <a name="specifying-the-connection-to-the-northwind-database"></a><span data-ttu-id="a8303-156">Especificando a conexão ao banco de dados Northwind</span><span class="sxs-lookup"><span data-stu-id="a8303-156">Specifying the Connection to the Northwind Database</span></span>  
 <span data-ttu-id="a8303-157">Nesta etapa você usa um objeto <xref:System.Data.Linq.DataContext> para estabelecer uma conexão entre as estruturas de dados baseadas em código e o próprio banco de dados.</span><span class="sxs-lookup"><span data-stu-id="a8303-157">In this step you use a <xref:System.Data.Linq.DataContext> object to establish a connection between your code-based data structures and the database itself.</span></span> <span data-ttu-id="a8303-158">O <xref:System.Data.Linq.DataContext> é o canal principal por meio do qual você recupera objetos do banco de dados e envia alterações.</span><span class="sxs-lookup"><span data-stu-id="a8303-158">The <xref:System.Data.Linq.DataContext> is the main channel through which you retrieve objects from the database and submit changes.</span></span>  
  
 <span data-ttu-id="a8303-159">Você também declara um `Table<Customer>` para atuar como a tabela lógica tipada para suas consultas na tabela Customers do banco de dados.</span><span class="sxs-lookup"><span data-stu-id="a8303-159">You also declare a `Table<Customer>` to act as the logical, typed table for your queries against the Customers table in the database.</span></span> <span data-ttu-id="a8303-160">Você criará e executará essas consultas em etapas posteriores.</span><span class="sxs-lookup"><span data-stu-id="a8303-160">You will create and execute these queries in later steps.</span></span>  
  
#### <a name="to-specify-the-database-connection"></a><span data-ttu-id="a8303-161">Para especificar a conexão do banco de dados</span><span class="sxs-lookup"><span data-stu-id="a8303-161">To specify the database connection</span></span>  
  
-   <span data-ttu-id="a8303-162">Digite ou cole o código a seguir no método `Main`:</span><span class="sxs-lookup"><span data-stu-id="a8303-162">Type or paste the following code into the `Main` method.</span></span>  
  
     <span data-ttu-id="a8303-163">Observe que supõe-se que o arquivo `northwnd.mdf` está na pasta linqtest5.</span><span class="sxs-lookup"><span data-stu-id="a8303-163">Note that the `northwnd.mdf` file is assumed to be in the linqtest5 folder.</span></span> <span data-ttu-id="a8303-164">Para obter mais informações, consulte a seção de pré-requisitos anteriormente neste passo a passo.</span><span class="sxs-lookup"><span data-stu-id="a8303-164">For more information, see the Prerequisites section earlier in this walkthrough.</span></span>  
  
     [!code-csharp[DLinqWalk1CS#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1CS/cs/Program.cs#4)]  
  
## <a name="creating-a-simple-query"></a><span data-ttu-id="a8303-165">Criando uma consulta simples</span><span class="sxs-lookup"><span data-stu-id="a8303-165">Creating a Simple Query</span></span>  
 <span data-ttu-id="a8303-166">Nesta etapa, você cria uma consulta para localizar quais clientes da tabela Customers do banco de dados estão localizados em Londres.</span><span class="sxs-lookup"><span data-stu-id="a8303-166">In this step, you create a query to find which customers in the database Customers table are located in London.</span></span> <span data-ttu-id="a8303-167">O código da consulta nesta etapa apenas descreve a consulta.</span><span class="sxs-lookup"><span data-stu-id="a8303-167">The query code in this step just describes the query.</span></span> <span data-ttu-id="a8303-168">Não a executa.</span><span class="sxs-lookup"><span data-stu-id="a8303-168">It does not execute it.</span></span> <span data-ttu-id="a8303-169">Essa abordagem é conhecida como *execução diferida*.</span><span class="sxs-lookup"><span data-stu-id="a8303-169">This approach is known as *deferred execution*.</span></span> <span data-ttu-id="a8303-170">Para obter mais informações, consulte [Introdução a Consultas de LINQ (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span><span class="sxs-lookup"><span data-stu-id="a8303-170">For more information, see [Introduction to LINQ Queries (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>  
  
 <span data-ttu-id="a8303-171">Você também gerará uma saída de log para mostrar os comandos SQL gerados pelo [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a8303-171">You will also produce a log output to show the SQL commands that [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generates.</span></span> <span data-ttu-id="a8303-172">Este recurso de log (que usa <xref:System.Data.Linq.DataContext.Log%2A>) é útil para depuração e para determinar se os comandos que estão sendo enviados ao banco de dados representam precisamente sua consulta.</span><span class="sxs-lookup"><span data-stu-id="a8303-172">This logging feature (which uses <xref:System.Data.Linq.DataContext.Log%2A>) is helpful in debugging, and in determining that the commands being sent to the database accurately represent your query.</span></span>  
  
#### <a name="to-create-a-simple-query"></a><span data-ttu-id="a8303-173">Para criar uma consulta simples</span><span class="sxs-lookup"><span data-stu-id="a8303-173">To create a simple query</span></span>  
  
-   <span data-ttu-id="a8303-174">Digite ou cole o código a seguir no método `Main` depois da declaração `Table<Customer>`.</span><span class="sxs-lookup"><span data-stu-id="a8303-174">Type or paste the following code into the `Main` method after the `Table<Customer>` declaration.</span></span>  
  
     [!code-csharp[DLinqWalk1ACS#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1ACS/cs/Program.cs#5)]  
  
## <a name="executing-the-query"></a><span data-ttu-id="a8303-175">Executando a consulta</span><span class="sxs-lookup"><span data-stu-id="a8303-175">Executing the Query</span></span>  
 <span data-ttu-id="a8303-176">Nesta etapa, você realmente executa a consulta.</span><span class="sxs-lookup"><span data-stu-id="a8303-176">In this step, you actually execute the query.</span></span> <span data-ttu-id="a8303-177">As expressões de consulta que você criou nas etapas anteriores não são avaliadas até que os resultados sejam necessários.</span><span class="sxs-lookup"><span data-stu-id="a8303-177">The query expressions you created in the previous steps are not evaluated until the results are needed.</span></span> <span data-ttu-id="a8303-178">Quando você começa a iteração `foreach`, um comando SQL é executado no banco de dados e os objetos são materializados.</span><span class="sxs-lookup"><span data-stu-id="a8303-178">When you begin the `foreach` iteration, a SQL command is executed against the database and objects are materialized.</span></span>  
  
#### <a name="to-execute-the-query"></a><span data-ttu-id="a8303-179">Para executar a consulta</span><span class="sxs-lookup"><span data-stu-id="a8303-179">To execute the query</span></span>  
  
1.  <span data-ttu-id="a8303-180">Digite ou cole o seguinte código ao final do método `Main` (após a descrição de consulta).</span><span class="sxs-lookup"><span data-stu-id="a8303-180">Type or paste the following code at the end of the `Main` method (after the query description).</span></span>  
  
     [!code-csharp[DLinqWalk1ACS#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1ACS/cs/Program.cs#6)]  
  
2.  <span data-ttu-id="a8303-181">Pressione F5 para depurar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a8303-181">Press F5 to debug the application.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a8303-182">Se o aplicativo gera um erro de tempo de execução, consulte a seção de solução de problemas de [aprendendo com explicações passo a passo](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md).</span><span class="sxs-lookup"><span data-stu-id="a8303-182">If your application generates a run-time error, see the Troubleshooting section of [Learning by Walkthroughs](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md).</span></span>  
  
     <span data-ttu-id="a8303-183">Os resultados da consulta na janela do console devem aparecer da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="a8303-183">The query results in the console window should appear as follows:</span></span>  
  
     `ID=AROUT, City=London`  
  
     `ID=BSBEV, City=London`  
  
     `ID=CONSH, City=London`  
  
     `ID=EASTC, City=London`  
  
     `ID=NORTS, City=London`  
  
     `ID=SEVES, City=London`  
  
3.  <span data-ttu-id="a8303-184">Pressione Enter na janela Console para fechar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a8303-184">Press Enter in the console window to close the application.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="a8303-185">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="a8303-185">Next Steps</span></span>  
 <span data-ttu-id="a8303-186">O [passo a passo: consultando em relações (c#)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-querying-across-relationships-csharp.md) tópico continua onde este passo a passo termina.</span><span class="sxs-lookup"><span data-stu-id="a8303-186">The [Walkthrough: Querying Across Relationships (C#)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-querying-across-relationships-csharp.md) topic continues where this walkthrough ends.</span></span> <span data-ttu-id="a8303-187">Consulta entre relações passo a passo demonstra como [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] pode consultar tabelas, semelhante ao *junções* em um banco de dados relacional.</span><span class="sxs-lookup"><span data-stu-id="a8303-187">The Query Across Relationships walkthrough demonstrates how [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] can query across tables, similar to *joins* in a relational database.</span></span>  
  
 <span data-ttu-id="a8303-188">Se você desejar realizar o passo a passo Consulta entre relações, salve a solução do passo a passo que você acabou de concluir, que é um pré-requisito.</span><span class="sxs-lookup"><span data-stu-id="a8303-188">If you want to do the Query Across Relationships walkthrough, make sure to save the solution for the walkthrough you have just completed, which is a prerequisite.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8303-189">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a8303-189">See Also</span></span>  
 [<span data-ttu-id="a8303-190">Aprendendo com explicações passo a passo</span><span class="sxs-lookup"><span data-stu-id="a8303-190">Learning by Walkthroughs</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
