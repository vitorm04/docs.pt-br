---
title: 'Passo a passo: consultar entre relações (C#)'
ms.date: 03/30/2017
ms.assetid: 552abeb1-18f2-4e93-a9c6-ef7b2db30c32
ms.openlocfilehash: ebf96bc575ef68e1190c5b9be7111902c0f69fef
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780993"
---
# <a name="walkthrough-querying-across-relationships-c"></a><span data-ttu-id="d7b70-102">Passo a passo: consultar entre relações (C#)</span><span class="sxs-lookup"><span data-stu-id="d7b70-102">Walkthrough: Querying Across Relationships (C#)</span></span>
<span data-ttu-id="d7b70-103">Este tutorial demonstra o uso de [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] *associações* para representar relações de chave estrangeira no banco de dados.</span><span class="sxs-lookup"><span data-stu-id="d7b70-103">This walkthrough demonstrates the use of [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] *associations* to represent foreign-key relationships in the database.</span></span>  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 <span data-ttu-id="d7b70-104">Esse passo a passo foi escrito usando as configurações de desenvolvimento do Visual C#.</span><span class="sxs-lookup"><span data-stu-id="d7b70-104">This walkthrough was written by using Visual C# Development Settings.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="d7b70-105">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="d7b70-105">Prerequisites</span></span>  
 <span data-ttu-id="d7b70-106">Você deve ter concluído [o passo a passos: Modelo de objeto simples e consultaC#(](walkthrough-simple-object-model-and-query-csharp.md)).</span><span class="sxs-lookup"><span data-stu-id="d7b70-106">You must have completed [Walkthrough: Simple Object Model and Query (C#)](walkthrough-simple-object-model-and-query-csharp.md).</span></span> <span data-ttu-id="d7b70-107">Este passo a passo é baseado naquele, incluindo a presença do arquivo northwnd.mdf em c:\linqtest5.</span><span class="sxs-lookup"><span data-stu-id="d7b70-107">This walkthrough builds on that one, including the presence of the northwnd.mdf file in c:\linqtest5.</span></span>  
  
## <a name="overview"></a><span data-ttu-id="d7b70-108">Visão geral</span><span class="sxs-lookup"><span data-stu-id="d7b70-108">Overview</span></span>  
 <span data-ttu-id="d7b70-109">Este passo a passo consiste em três tarefas principais:</span><span class="sxs-lookup"><span data-stu-id="d7b70-109">This walkthrough consists of three main tasks:</span></span>  
  
- <span data-ttu-id="d7b70-110">Adicionando uma classe de entidade para representar a tabela Orders no banco de dados de exemplo Northwind.</span><span class="sxs-lookup"><span data-stu-id="d7b70-110">Adding an entity class to represent the Orders table in the sample Northwind database.</span></span>  
  
- <span data-ttu-id="d7b70-111">Suplementando anotações à classe `Customer` para aprimorar a relação entre as classes `Customer` e `Order`.</span><span class="sxs-lookup"><span data-stu-id="d7b70-111">Supplementing annotations to the `Customer` class to enhance the relationship between the `Customer` and `Order` classes.</span></span>  
  
- <span data-ttu-id="d7b70-112">Criando e executando uma consulta para testar a obtenção de informações de `Order` usando a classe `Customer`.</span><span class="sxs-lookup"><span data-stu-id="d7b70-112">Creating and running a query to test obtaining `Order` information by using the `Customer` class.</span></span>  
  
## <a name="mapping-relationships-across-tables"></a><span data-ttu-id="d7b70-113">Relações de mapeamento entre tabelas</span><span class="sxs-lookup"><span data-stu-id="d7b70-113">Mapping Relationships Across Tables</span></span>  
 <span data-ttu-id="d7b70-114">Depois de definir a classe `Customer`, crie a definição da classe de entidade `Order` que inclui o código a seguir, que indica que `Order.Customer` se relaciona como uma chave estrangeira a `Customer.CustomerID`.</span><span class="sxs-lookup"><span data-stu-id="d7b70-114">After the `Customer` class definition, create the `Order` entity class definition that includes the following code, which indicates that `Order.Customer` relates as a foreign key to `Customer.CustomerID`.</span></span>  
  
### <a name="to-add-the-order-entity-class"></a><span data-ttu-id="d7b70-115">Para adicionar a classe de entidade Order</span><span class="sxs-lookup"><span data-stu-id="d7b70-115">To add the Order entity class</span></span>  
  
- <span data-ttu-id="d7b70-116">Digite ou cole o código a seguir depois da classe `Customer`:</span><span class="sxs-lookup"><span data-stu-id="d7b70-116">Type or paste the following code after the `Customer` class:</span></span>  
  
     [!code-csharp[DLinqWalk2CS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk2CS/cs/Program.cs#1)]  
  
## <a name="annotating-the-customer-class"></a><span data-ttu-id="d7b70-117">Anotando a classe Customer</span><span class="sxs-lookup"><span data-stu-id="d7b70-117">Annotating the Customer Class</span></span>  
 <span data-ttu-id="d7b70-118">Nesta etapa, você anota a classe `Customer` para indicar sua relação com a classe `Order`.</span><span class="sxs-lookup"><span data-stu-id="d7b70-118">In this step, you annotate the `Customer` class to indicate its relationship to the `Order` class.</span></span> <span data-ttu-id="d7b70-119">Essa adição não é estritamente necessária, porque a definição da relação em qualquer direção é suficiente para criar o link.</span><span class="sxs-lookup"><span data-stu-id="d7b70-119">(This addition is not strictly necessary, because defining the relationship in either direction is sufficient to create the link.</span></span> <span data-ttu-id="d7b70-120">Mas a adição dessa anotação permite que você navegue objetos facilmente em qualquer direção.</span><span class="sxs-lookup"><span data-stu-id="d7b70-120">But adding this annotation does enable you to easily navigate objects in either direction.)</span></span>  
  
### <a name="to-annotate-the-customer-class"></a><span data-ttu-id="d7b70-121">Para anotar a classe Customer</span><span class="sxs-lookup"><span data-stu-id="d7b70-121">To annotate the Customer class</span></span>  
  
- <span data-ttu-id="d7b70-122">Digite ou cole o código a seguir na classe `Customer`:</span><span class="sxs-lookup"><span data-stu-id="d7b70-122">Type or paste the following code into the `Customer` class:</span></span>  
  
     [!code-csharp[DLinqWalk2CS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk2CS/cs/Program.cs#2)]  
  
## <a name="creating-and-running-a-query-across-the-customer-order-relationship"></a><span data-ttu-id="d7b70-123">Criando e executando uma consulta pela relação de Customer-Order</span><span class="sxs-lookup"><span data-stu-id="d7b70-123">Creating and Running a Query Across the Customer-Order Relationship</span></span>  
 <span data-ttu-id="d7b70-124">Agora você pode acessar objetos `Order` diretamente nos objetos `Customer` ou na ordem oposta.</span><span class="sxs-lookup"><span data-stu-id="d7b70-124">You can now access `Order` objects directly from the `Customer` objects, or in the opposite order.</span></span> <span data-ttu-id="d7b70-125">Você não precisa de uma *junção* explícita entre clientes e pedidos.</span><span class="sxs-lookup"><span data-stu-id="d7b70-125">You do not need an explicit *join* between customers and orders.</span></span>  
  
### <a name="to-access-order-objects-by-using-customer-objects"></a><span data-ttu-id="d7b70-126">Para acessar objetos Order usando objetos Customer</span><span class="sxs-lookup"><span data-stu-id="d7b70-126">To access Order objects by using Customer objects</span></span>  
  
1. <span data-ttu-id="d7b70-127">Modifique o método `Main` digitando ou colando o seguinte código no método:</span><span class="sxs-lookup"><span data-stu-id="d7b70-127">Modify the `Main` method by typing or pasting the following code into the method:</span></span>  
  
     [!code-csharp[DLinqWalk2CS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk2CS/cs/Program.cs#3)]  
  
2. <span data-ttu-id="d7b70-128">Pressione F5 para depurar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d7b70-128">Press F5 to debug your application.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="d7b70-129">Você pode eliminar o código SQL na janela do console comentando por `db.Log = Console.Out;`.</span><span class="sxs-lookup"><span data-stu-id="d7b70-129">You can eliminate the SQL code in the Console window by commenting out `db.Log = Console.Out;`.</span></span>  
  
3. <span data-ttu-id="d7b70-130">Pressione Enter na janela de Console para parar a depuração.</span><span class="sxs-lookup"><span data-stu-id="d7b70-130">Press Enter in the Console window to stop debugging.</span></span>  
  
## <a name="creating-a-strongly-typed-view-of-your-database"></a><span data-ttu-id="d7b70-131">Criando uma exibição fortemente tipada do seu banco de dados</span><span class="sxs-lookup"><span data-stu-id="d7b70-131">Creating a Strongly Typed View of Your Database</span></span>  
 <span data-ttu-id="d7b70-132">É muito mais fácil começar com uma exibição fortemente tipada do seu banco de dados.</span><span class="sxs-lookup"><span data-stu-id="d7b70-132">It is much easier to start with a strongly typed view of your database.</span></span> <span data-ttu-id="d7b70-133">Com o objeto <xref:System.Data.Linq.DataContext> fortemente tipado, você não precisa de chamadas para <xref:System.Data.Linq.DataContext.GetTable%2A>.</span><span class="sxs-lookup"><span data-stu-id="d7b70-133">By strongly typing the <xref:System.Data.Linq.DataContext> object, you do not need calls to <xref:System.Data.Linq.DataContext.GetTable%2A>.</span></span> <span data-ttu-id="d7b70-134">Você pode usar tabelas fortemente tipadas em todas as consultas quando usa o objeto <xref:System.Data.Linq.DataContext> fortemente tipado.</span><span class="sxs-lookup"><span data-stu-id="d7b70-134">You can use strongly typed tables in all your queries when you use the strongly typed <xref:System.Data.Linq.DataContext> object.</span></span>  
  
 <span data-ttu-id="d7b70-135">Nas etapas a seguir, você criará `Customers` como uma tabela fortemente tipada que mapeia para a tabela Customers no banco de dados.</span><span class="sxs-lookup"><span data-stu-id="d7b70-135">In the following steps, you will create `Customers` as a strongly typed table that maps to the Customers table in the database.</span></span>  
  
### <a name="to-strongly-type-the-datacontext-object"></a><span data-ttu-id="d7b70-136">Para tornar o objeto DataContext fortemente tipado</span><span class="sxs-lookup"><span data-stu-id="d7b70-136">To strongly type the DataContext object</span></span>  
  
1. <span data-ttu-id="d7b70-137">Adicione o código a seguir acima da declaração da classe `Customer`.</span><span class="sxs-lookup"><span data-stu-id="d7b70-137">Add the following code above the `Customer` class declaration.</span></span>  
  
     [!code-csharp[DLinqWalk2CS#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk2CS/cs/Program.cs#4)]  
  
2. <span data-ttu-id="d7b70-138">Modifique o método `Main` para usar o <xref:System.Data.Linq.DataContext> fortemente tipado da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="d7b70-138">Modify the `Main` method to use the strongly typed <xref:System.Data.Linq.DataContext> as follows:</span></span>  
  
     [!code-csharp[DLinqWalk2CS#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk2CS/cs/Program.cs#5)]  
  
3. <span data-ttu-id="d7b70-139">Pressione F5 para depurar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d7b70-139">Press F5 to debug your application.</span></span>  
  
     <span data-ttu-id="d7b70-140">A saída da janela Console é:</span><span class="sxs-lookup"><span data-stu-id="d7b70-140">The Console window output is:</span></span>  
  
     `ID=WHITC`  
  
4. <span data-ttu-id="d7b70-141">Pressione Enter na janela de Console para parar a depuração.</span><span class="sxs-lookup"><span data-stu-id="d7b70-141">Press Enter in the console window to stop debugging.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="d7b70-142">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="d7b70-142">Next Steps</span></span>  
 <span data-ttu-id="d7b70-143">O passo a seguir[(Walkthrough: A manipulação de dadosC#(](walkthrough-manipulating-data-csharp.md))) demonstra como manipular dados.</span><span class="sxs-lookup"><span data-stu-id="d7b70-143">The next walkthrough ([Walkthrough: Manipulating Data (C#)](walkthrough-manipulating-data-csharp.md)) demonstrates how to manipulate data.</span></span> <span data-ttu-id="d7b70-144">Esse passo a passo não requer que você salve os dois tutoriais passo a passo desta série que você já concluiu.</span><span class="sxs-lookup"><span data-stu-id="d7b70-144">That walkthrough does not require that you save the two walkthroughs in this series that you have already completed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7b70-145">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d7b70-145">See also</span></span>

- [<span data-ttu-id="d7b70-146">Aprendendo com explicações passo a passo</span><span class="sxs-lookup"><span data-stu-id="d7b70-146">Learning by Walkthroughs</span></span>](learning-by-walkthroughs.md)
