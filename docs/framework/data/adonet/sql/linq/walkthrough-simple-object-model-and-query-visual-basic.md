---
title: 'Passo a passo: modelo e consulta de objeto simples (Visual Basic)'
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: c878e457-f715-46e4-a136-ff14d6c86018
ms.openlocfilehash: ccbb979ae7cf67dd54eb80e1d30e74078960b43d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59169098"
---
# <a name="walkthrough-simple-object-model-and-query-visual-basic"></a><span data-ttu-id="acead-102">Passo a passo: modelo e consulta de objeto simples (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="acead-102">Walkthrough: Simple Object Model and Query (Visual Basic)</span></span>
<span data-ttu-id="acead-103">Este passo a passo fornece um cenário completo fundamental do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] com complexidades mínimas.</span><span class="sxs-lookup"><span data-stu-id="acead-103">This walkthrough provides a fundamental end-to-end [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scenario with minimal complexities.</span></span> <span data-ttu-id="acead-104">Você criará uma classe de entidade que modela a tabela Customers no banco de dados de exemplo Northwind.</span><span class="sxs-lookup"><span data-stu-id="acead-104">You will create an entity class that models the Customers table in the sample Northwind database.</span></span> <span data-ttu-id="acead-105">Em seguida, você irá criar uma consulta simples para listar os clientes que estão localizados em Londres.</span><span class="sxs-lookup"><span data-stu-id="acead-105">You will then create a simple query to list customers who are located in London.</span></span>  
  
 <span data-ttu-id="acead-106">Este passo a passo é orientado a código por design para ajudar a mostrar os conceitos do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="acead-106">This walkthrough is code-oriented by design to help show [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] concepts.</span></span> <span data-ttu-id="acead-107">Normalmente, você usa o [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] para criar seu modelo de objeto.</span><span class="sxs-lookup"><span data-stu-id="acead-107">Normally speaking, you would use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to create your object model.</span></span>  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 <span data-ttu-id="acead-108">Este passo a passo foi escrito usando as Configurações de Desenvolvimento do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="acead-108">This walkthrough was written by using Visual Basic Development Settings.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="acead-109">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="acead-109">Prerequisites</span></span>  
  
-   <span data-ttu-id="acead-110">Este passo a passo usa uma pasta dedicada ("c:\linqtest") para armazenar arquivos.</span><span class="sxs-lookup"><span data-stu-id="acead-110">This walkthrough uses a dedicated folder ("c:\linqtest") to hold files.</span></span> <span data-ttu-id="acead-111">Crie essa pasta antes de iniciar o passo a passo.</span><span class="sxs-lookup"><span data-stu-id="acead-111">Create this folder before you begin the walkthrough.</span></span>  
  
-   <span data-ttu-id="acead-112">Este passo a passo requer o banco de dados de exemplo Northwind.</span><span class="sxs-lookup"><span data-stu-id="acead-112">This walkthrough requires the Northwind sample database.</span></span> <span data-ttu-id="acead-113">Se você não tiver esse banco de dados no seu computador de desenvolvimento, poderá baixá-lo no site de download da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="acead-113">If you do not have this database on your development computer, you can download it from the Microsoft download site.</span></span> <span data-ttu-id="acead-114">Para obter instruções, consulte [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="acead-114">For instructions, see [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span> <span data-ttu-id="acead-115">Depois de baixar o banco de dados, copie o arquivo para a pasta c:\linqtest.</span><span class="sxs-lookup"><span data-stu-id="acead-115">After you have downloaded the database, copy the file to the c:\linqtest folder.</span></span>  
  
## <a name="overview"></a><span data-ttu-id="acead-116">Visão geral</span><span class="sxs-lookup"><span data-stu-id="acead-116">Overview</span></span>  
 <span data-ttu-id="acead-117">Este passo a passo consiste em seis tarefas principais:</span><span class="sxs-lookup"><span data-stu-id="acead-117">This walkthrough consists of six main tasks:</span></span>  
  
-   <span data-ttu-id="acead-118">Criando um [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] solução no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="acead-118">Creating a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] solution in Visual Studio.</span></span>  
  
-   <span data-ttu-id="acead-119">Mapear uma classe para uma tabela do banco de dados.</span><span class="sxs-lookup"><span data-stu-id="acead-119">Mapping a class to a database table.</span></span>  
  
-   <span data-ttu-id="acead-120">Designar propriedades na classe para representar colunas do banco de dados.</span><span class="sxs-lookup"><span data-stu-id="acead-120">Designating properties on the class to represent database columns.</span></span>  
  
-   <span data-ttu-id="acead-121">Especificar a conexão ao banco de dados Northwind.</span><span class="sxs-lookup"><span data-stu-id="acead-121">Specifying the connection to the Northwind database.</span></span>  
  
-   <span data-ttu-id="acead-122">Criar uma consulta simples para execução no banco de dados.</span><span class="sxs-lookup"><span data-stu-id="acead-122">Creating a simple query to run against the database.</span></span>  
  
-   <span data-ttu-id="acead-123">Executar a consulta e observar os resultados.</span><span class="sxs-lookup"><span data-stu-id="acead-123">Executing the query and observing the results.</span></span>  
  
## <a name="creating-a-linq-to-sql-solution"></a><span data-ttu-id="acead-124">Criando uma solução LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="acead-124">Creating a LINQ to SQL Solution</span></span>  
 <span data-ttu-id="acead-125">A primeira tarefa, você cria uma solução do Visual Studio que contém as referências necessárias para compilar e executar um [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projeto.</span><span class="sxs-lookup"><span data-stu-id="acead-125">In this first task, you create a Visual Studio solution that contains the necessary references to build and run a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] project.</span></span>  
  
#### <a name="to-create-a-linq-to-sql-solution"></a><span data-ttu-id="acead-126">Para criar uma solução LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="acead-126">To create a LINQ to SQL solution</span></span>  
  
1.  <span data-ttu-id="acead-127">No menu **Arquivo**, clique em **Novo Projeto**.</span><span class="sxs-lookup"><span data-stu-id="acead-127">On the **File** menu, click **New Project**.</span></span>  
  
2.  <span data-ttu-id="acead-128">No **tipos de projeto** painel da **novo projeto** caixa de diálogo, clique em **Visual Basic**.</span><span class="sxs-lookup"><span data-stu-id="acead-128">In the **Project types** pane of the **New Project** dialog box, click **Visual Basic**.</span></span>  
  
3.  <span data-ttu-id="acead-129">No painel **Modelos**, clique em **Aplicativo de Console**.</span><span class="sxs-lookup"><span data-stu-id="acead-129">In the **Templates** pane, click **Console Application**.</span></span>  
  
4.  <span data-ttu-id="acead-130">No **nome** , digite **LinqConsoleApp**.</span><span class="sxs-lookup"><span data-stu-id="acead-130">In the **Name** box, type **LinqConsoleApp**.</span></span>  
  
5.  <span data-ttu-id="acead-131">Clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="acead-131">Click **OK**.</span></span>  
  
## <a name="adding-linq-references-and-directives"></a><span data-ttu-id="acead-132">Adicionando referências e diretivas LINQ</span><span class="sxs-lookup"><span data-stu-id="acead-132">Adding LINQ References and Directives</span></span>  
 <span data-ttu-id="acead-133">Este passo a passo usa assemblies que não podem ser instalados por padrão em seu projeto.</span><span class="sxs-lookup"><span data-stu-id="acead-133">This walkthrough uses assemblies that might not be installed by default in your project.</span></span> <span data-ttu-id="acead-134">Se `System.Data.Linq` não estiver listado como uma referência em seu projeto (clique em **Show All Files** na **Gerenciador de soluções** e expanda o **referências** nó), adicioná-lo, conforme explicado em as etapas a seguir.</span><span class="sxs-lookup"><span data-stu-id="acead-134">If `System.Data.Linq` is not listed as a reference in your project (click **Show All Files** in **Solution Explorer** and expand the **References** node), add it, as explained in the following steps.</span></span>  
  
#### <a name="to-add-systemdatalinq"></a><span data-ttu-id="acead-135">Para adicionar System.Data.Linq</span><span class="sxs-lookup"><span data-stu-id="acead-135">To add System.Data.Linq</span></span>  
  
1.  <span data-ttu-id="acead-136">Na **Gerenciador de soluções**, clique com botão direito **referências**e, em seguida, clique em **Add Reference**.</span><span class="sxs-lookup"><span data-stu-id="acead-136">In **Solution Explorer**, right-click **References**, and then click **Add Reference**.</span></span>  
  
2.  <span data-ttu-id="acead-137">No **adicionar referência** caixa de diálogo, clique em **.NET**, clique no assembly System e, em seguida, clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="acead-137">In the **Add Reference** dialog box, click **.NET**, click the System.Data.Linq assembly, and then click **OK**.</span></span>  
  
     <span data-ttu-id="acead-138">O assembly é adicionado ao projeto.</span><span class="sxs-lookup"><span data-stu-id="acead-138">The assembly is added to the project.</span></span>  
  
3.  <span data-ttu-id="acead-139">Além disso, nos **adicionar referência** caixa de diálogo, clique em **.NET**, role para e clique em System e, em seguida, clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="acead-139">Also in the **Add Reference** dialog box, click **.NET**, scroll to and click System.Windows.Forms, and then click **OK**.</span></span>  
  
     <span data-ttu-id="acead-140">Este assembly, que oferece suporte à caixa de mensagem no passo a passo, é adicionado ao projeto.</span><span class="sxs-lookup"><span data-stu-id="acead-140">This assembly, which supports the message box in the walkthrough, is added to the project.</span></span>  
  
4.  <span data-ttu-id="acead-141">Adicione as seguintes diretivas acima de `Module1`:</span><span class="sxs-lookup"><span data-stu-id="acead-141">Add the following directives above `Module1`:</span></span>  
  
     [!code-vb[DLinqWalk1VB#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1VB/vb/Module1.vb#1)]  
  
## <a name="mapping-a-class-to-a-database-table"></a><span data-ttu-id="acead-142">Mapeando uma classe para uma tabela do banco de dados</span><span class="sxs-lookup"><span data-stu-id="acead-142">Mapping a Class to a Database Table</span></span>  
 <span data-ttu-id="acead-143">Nesta etapa, você cria uma classe e a mapeia para uma tabela do banco de dados.</span><span class="sxs-lookup"><span data-stu-id="acead-143">In this step, you create a class and map it to a database table.</span></span> <span data-ttu-id="acead-144">Essa classe é chamada de um *classe de entidade*.</span><span class="sxs-lookup"><span data-stu-id="acead-144">Such a class is termed an *entity class*.</span></span> <span data-ttu-id="acead-145">Observe que o mapeamento é realizado simplesmente adicionando o atributo <xref:System.Data.Linq.Mapping.TableAttribute>.</span><span class="sxs-lookup"><span data-stu-id="acead-145">Note that the mapping is accomplished by just adding the <xref:System.Data.Linq.Mapping.TableAttribute> attribute.</span></span> <span data-ttu-id="acead-146">A propriedade <xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> especifica o nome da tabela no banco de dados.</span><span class="sxs-lookup"><span data-stu-id="acead-146">The <xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> property specifies the name of the table in the database.</span></span>  
  
#### <a name="to-create-an-entity-class-and-map-it-to-a-database-table"></a><span data-ttu-id="acead-147">Para criar uma classe de entidade e mapeá-la para uma tabela do banco de dados.</span><span class="sxs-lookup"><span data-stu-id="acead-147">To create an entity class and map it to a database table</span></span>  
  
-   <span data-ttu-id="acead-148">Digite ou cole o seguinte código no Module1.vb imediatamente acima de `Sub Main`:</span><span class="sxs-lookup"><span data-stu-id="acead-148">Type or paste the following code into Module1.vb immediately above `Sub Main`:</span></span>  
  
     [!code-vb[DLinqWalk1VB#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1VB/vb/Module1.vb#2)]  
  
## <a name="designating-properties-on-the-class-to-represent-database-columns"></a><span data-ttu-id="acead-149">Designando propriedades na classe para representar colunas do banco de dados</span><span class="sxs-lookup"><span data-stu-id="acead-149">Designating Properties on the Class to Represent Database Columns</span></span>  
 <span data-ttu-id="acead-150">Nesta etapa, você realiza várias tarefas.</span><span class="sxs-lookup"><span data-stu-id="acead-150">In this step, you accomplish several tasks.</span></span>  
  
-   <span data-ttu-id="acead-151">Você usa o atributo <xref:System.Data.Linq.Mapping.ColumnAttribute> para designar as propriedades `CustomerID` e `City` na classe de entidade como representação de colunas na tabela do banco de dados.</span><span class="sxs-lookup"><span data-stu-id="acead-151">You use the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to designate `CustomerID` and `City` properties on the entity class as representing columns in the database table.</span></span>  
  
-   <span data-ttu-id="acead-152">Você designa a propriedade `CustomerID` como a representação de uma coluna de chave primária no banco de dados.</span><span class="sxs-lookup"><span data-stu-id="acead-152">You designate the `CustomerID` property as representing a primary key column in the database.</span></span>  
  
-   <span data-ttu-id="acead-153">Você designa os campos `_CustomerID` e `_City` para armazenamento particular.</span><span class="sxs-lookup"><span data-stu-id="acead-153">You designate `_CustomerID` and `_City` fields for private storage.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="acead-154">pode, em seguida, armazenar e recuperar valores diretamente, em vez de usar acessadores públicos, que podem incluir a lógica de negócios.</span><span class="sxs-lookup"><span data-stu-id="acead-154">can then store and retrieve values directly, instead of using public accessors that might include business logic.</span></span>  
  
#### <a name="to-represent-characteristics-of-two-database-columns"></a><span data-ttu-id="acead-155">Para representar características de duas colunas do banco de dados</span><span class="sxs-lookup"><span data-stu-id="acead-155">To represent characteristics of two database columns</span></span>  
  
-   <span data-ttu-id="acead-156">Digite ou cole o seguinte código no Module1.vb imediatamente antes de `End Class`:</span><span class="sxs-lookup"><span data-stu-id="acead-156">Type or paste the following code into Module1.vb just before `End Class`:</span></span>  
  
     [!code-vb[DLinqWalk1VB#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1VB/vb/Module1.vb#3)]  
  
## <a name="specifying-the-connection-to-the-northwind-database"></a><span data-ttu-id="acead-157">Especificando a conexão ao banco de dados Northwind</span><span class="sxs-lookup"><span data-stu-id="acead-157">Specifying the Connection to the Northwind Database</span></span>  
 <span data-ttu-id="acead-158">Nesta etapa você usa um objeto <xref:System.Data.Linq.DataContext> para estabelecer uma conexão entre as estruturas de dados baseadas em código e o próprio banco de dados.</span><span class="sxs-lookup"><span data-stu-id="acead-158">In this step you use a <xref:System.Data.Linq.DataContext> object to establish a connection between your code-based data structures and the database itself.</span></span> <span data-ttu-id="acead-159">O <xref:System.Data.Linq.DataContext> é o canal principal por meio do qual você recupera objetos do banco de dados e envia alterações.</span><span class="sxs-lookup"><span data-stu-id="acead-159">The <xref:System.Data.Linq.DataContext> is the main channel through which you retrieve objects from the database and submit changes.</span></span>  
  
 <span data-ttu-id="acead-160">Você também declara um `Table(Of Customer)` para atuar como a tabela lógica tipada para suas consultas na tabela Customers do banco de dados.</span><span class="sxs-lookup"><span data-stu-id="acead-160">You also declare a `Table(Of Customer)` to act as the logical, typed table for your queries against the Customers table in the database.</span></span> <span data-ttu-id="acead-161">Você criará e executará essas consultas em etapas posteriores.</span><span class="sxs-lookup"><span data-stu-id="acead-161">You will create and execute these queries in later steps.</span></span>  
  
#### <a name="to-specify-the-database-connection"></a><span data-ttu-id="acead-162">Para especificar a conexão do banco de dados</span><span class="sxs-lookup"><span data-stu-id="acead-162">To specify the database connection</span></span>  
  
-   <span data-ttu-id="acead-163">Digite ou cole o código a seguir no método `Sub Main`:</span><span class="sxs-lookup"><span data-stu-id="acead-163">Type or paste the following code into the `Sub Main` method.</span></span>  
  
     <span data-ttu-id="acead-164">Observe que supõe-se que o arquivo `northwnd.mdf` está na pasta linqtest.</span><span class="sxs-lookup"><span data-stu-id="acead-164">Note that the `northwnd.mdf` file is assumed to be in the linqtest folder.</span></span> <span data-ttu-id="acead-165">Para obter mais informações, consulte a seção de pré-requisitos anteriormente neste passo a passo.</span><span class="sxs-lookup"><span data-stu-id="acead-165">For more information, see the Prerequisites section earlier in this walkthrough.</span></span>  
  
     [!code-vb[DLinqWalk1VB#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1VB/vb/Module1.vb#4)]  
  
## <a name="creating-a-simple-query"></a><span data-ttu-id="acead-166">Criando uma consulta simples</span><span class="sxs-lookup"><span data-stu-id="acead-166">Creating a Simple Query</span></span>  
 <span data-ttu-id="acead-167">Nesta etapa, você cria uma consulta para localizar quais clientes da tabela Customers do banco de dados estão localizados em Londres.</span><span class="sxs-lookup"><span data-stu-id="acead-167">In this step, you create a query to find which customers in the database Customers table are located in London.</span></span> <span data-ttu-id="acead-168">O código da consulta nesta etapa apenas descreve a consulta.</span><span class="sxs-lookup"><span data-stu-id="acead-168">The query code in this step just describes the query.</span></span> <span data-ttu-id="acead-169">Não a executa.</span><span class="sxs-lookup"><span data-stu-id="acead-169">It does not execute it.</span></span> <span data-ttu-id="acead-170">Essa abordagem é conhecida como *execução adiada*.</span><span class="sxs-lookup"><span data-stu-id="acead-170">This approach is known as *deferred execution*.</span></span> <span data-ttu-id="acead-171">Para obter mais informações, consulte [Introdução a Consultas de LINQ (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span><span class="sxs-lookup"><span data-stu-id="acead-171">For more information, see [Introduction to LINQ Queries (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>  
  
 <span data-ttu-id="acead-172">Você também gerará uma saída de log para mostrar os comandos SQL gerados pelo [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="acead-172">You will also produce a log output to show the SQL commands that [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generates.</span></span> <span data-ttu-id="acead-173">Este recurso de log (que usa <xref:System.Data.Linq.DataContext.Log%2A>) é útil para depuração e para determinar se os comandos que estão sendo enviados ao banco de dados representam precisamente sua consulta.</span><span class="sxs-lookup"><span data-stu-id="acead-173">This logging feature (which uses <xref:System.Data.Linq.DataContext.Log%2A>) is helpful in debugging, and in determining that the commands being sent to the database accurately represent your query.</span></span>  
  
#### <a name="to-create-a-simple-query"></a><span data-ttu-id="acead-174">Para criar uma consulta simples</span><span class="sxs-lookup"><span data-stu-id="acead-174">To create a simple query</span></span>  
  
-   <span data-ttu-id="acead-175">Digite ou cole o código a seguir no método `Sub Main` depois da declaração `Table(Of Customer)`:</span><span class="sxs-lookup"><span data-stu-id="acead-175">Type or paste the following code into the `Sub Main` method after the `Table(Of Customer)` declaration:</span></span>  
  
     [!code-vb[DLinqWalk1AVB#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1AVB/vb/Module1.vb#5)]  
  
## <a name="executing-the-query"></a><span data-ttu-id="acead-176">Executando a consulta</span><span class="sxs-lookup"><span data-stu-id="acead-176">Executing the Query</span></span>  
 <span data-ttu-id="acead-177">Nesta etapa, você realmente executa a consulta.</span><span class="sxs-lookup"><span data-stu-id="acead-177">In this step, you actually execute the query.</span></span> <span data-ttu-id="acead-178">As expressões de consulta que você criou nas etapas anteriores não são avaliadas até que os resultados sejam necessários.</span><span class="sxs-lookup"><span data-stu-id="acead-178">The query expressions you created in the previous steps are not evaluated until the results are needed.</span></span> <span data-ttu-id="acead-179">Quando você começa a iteração `For Each`, um comando SQL é executado no banco de dados e os objetos são materializados.</span><span class="sxs-lookup"><span data-stu-id="acead-179">When you begin the `For Each` iteration, a SQL command is executed against the database and objects are materialized.</span></span>  
  
#### <a name="to-execute-the-query"></a><span data-ttu-id="acead-180">Para executar a consulta</span><span class="sxs-lookup"><span data-stu-id="acead-180">To execute the query</span></span>  
  
1.  <span data-ttu-id="acead-181">Digite ou cole o seguinte código ao final do método `Sub Main` (após a descrição de consulta):</span><span class="sxs-lookup"><span data-stu-id="acead-181">Type or paste the following code at the end of the `Sub Main` method (after the query description):</span></span>  
  
     [!code-vb[DLinqWalk1AVB#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1AVB/vb/Module1.vb#6)]  
  
2.  <span data-ttu-id="acead-182">Pressione F5 para depurar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="acead-182">Press F5 to debug the application.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="acead-183">Se seu aplicativo gera um erro de tempo de execução, consulte a seção solução de problemas [aprendendo com explicações passo a passo](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md).</span><span class="sxs-lookup"><span data-stu-id="acead-183">If your application generates a run-time error, see the Troubleshooting section of [Learning by Walkthroughs](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md).</span></span>  
  
     <span data-ttu-id="acead-184">A caixa de mensagem exibe uma lista de seis clientes.</span><span class="sxs-lookup"><span data-stu-id="acead-184">The message box displays a list of six customers.</span></span> <span data-ttu-id="acead-185">A janela Console exibe o código SQL gerado.</span><span class="sxs-lookup"><span data-stu-id="acead-185">The Console window displays the generated SQL code.</span></span>  
  
3.  <span data-ttu-id="acead-186">Clique em **OK** para descartar a caixa de mensagem.</span><span class="sxs-lookup"><span data-stu-id="acead-186">Click **OK** to dismiss the message box.</span></span>  
  
     <span data-ttu-id="acead-187">O aplicativo é fechado.</span><span class="sxs-lookup"><span data-stu-id="acead-187">The application closes.</span></span>  
  
4.  <span data-ttu-id="acead-188">No menu **Arquivo**, clique em **Salvar tudo**.</span><span class="sxs-lookup"><span data-stu-id="acead-188">On the **File** menu, click **Save All**.</span></span>  
  
     <span data-ttu-id="acead-189">Você precisará deste aplicativo para continuar com o próximo passo a passo.</span><span class="sxs-lookup"><span data-stu-id="acead-189">You will need this application if you continue with the next walkthrough.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="acead-190">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="acead-190">Next Steps</span></span>  
 <span data-ttu-id="acead-191">O [passo a passo: Consultando através de relações (Visual Basic)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-querying-across-relationships-visual-basic.md) tópico continua onde este passo a passo termina.</span><span class="sxs-lookup"><span data-stu-id="acead-191">The [Walkthrough: Querying Across Relationships (Visual Basic)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-querying-across-relationships-visual-basic.md) topic continues where this walkthrough ends.</span></span> <span data-ttu-id="acead-192">O passo a passo consultando através de relações demonstra como [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] pode consultar entre tabelas, semelhantes ao *junções* em um banco de dados relacional.</span><span class="sxs-lookup"><span data-stu-id="acead-192">The Querying Across Relationships walkthrough demonstrates how [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] can query across tables, similar to *joins* in a relational database.</span></span>  
  
 <span data-ttu-id="acead-193">Se você desejar realizar o passo a passo Consultando através de relações, salve a solução do passo a passo que você acabou de concluir, que é um pré-requisito.</span><span class="sxs-lookup"><span data-stu-id="acead-193">If you want to do the Querying Across Relationships walkthrough, make sure to save the solution for the walkthrough you have just completed, which is a prerequisite.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="acead-194">Consulte também</span><span class="sxs-lookup"><span data-stu-id="acead-194">See also</span></span>

- [<span data-ttu-id="acead-195">Aprendendo com explicações passo a passo</span><span class="sxs-lookup"><span data-stu-id="acead-195">Learning by Walkthroughs</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
