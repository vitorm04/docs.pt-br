---
title: 'Passo a passo: Consultando através de relações (Visual Basic)'
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: a7da43e3-769f-4e07-bcd6-552b8bde66f4
ms.openlocfilehash: aa98a823a5d97d86144ea2f76953e990cde8edec
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33355198"
---
# <a name="walkthrough-querying-across-relationships-visual-basic"></a><span data-ttu-id="1fee4-102">Passo a passo: Consultando através de relações (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1fee4-102">Walkthrough: Querying Across Relationships (Visual Basic)</span></span>
<span data-ttu-id="1fee4-103">Este passo a passo demonstra o uso de [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] *associações* para representar as relações de chave estrangeira no banco de dados.</span><span class="sxs-lookup"><span data-stu-id="1fee4-103">This walkthrough demonstrates the use of [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] *associations* to represent foreign-key relationships in the database.</span></span>  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 <span data-ttu-id="1fee4-104">Este passo a passo foi escrito usando as Configurações de Desenvolvimento do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="1fee4-104">This walkthrough was written by using Visual Basic Development Settings.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="1fee4-105">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="1fee4-105">Prerequisites</span></span>  
 <span data-ttu-id="1fee4-106">Você deve ter concluído [passo a passo: modelo de objeto simples e de consulta (Visual Basic)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-simple-object-model-and-query-visual-basic.md).</span><span class="sxs-lookup"><span data-stu-id="1fee4-106">You must have completed [Walkthrough: Simple Object Model and Query (Visual Basic)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-simple-object-model-and-query-visual-basic.md).</span></span> <span data-ttu-id="1fee4-107">Este passo a passo é baseado naquele, incluindo a presença do arquivo northwnd.mdf em c:\linqtest.</span><span class="sxs-lookup"><span data-stu-id="1fee4-107">This walkthrough builds on that one, including the presence of the northwnd.mdf file in c:\linqtest.</span></span>  
  
## <a name="overview"></a><span data-ttu-id="1fee4-108">Visão geral</span><span class="sxs-lookup"><span data-stu-id="1fee4-108">Overview</span></span>  
 <span data-ttu-id="1fee4-109">Este passo a passo consiste em três tarefas principais:</span><span class="sxs-lookup"><span data-stu-id="1fee4-109">This walkthrough consists of three main tasks:</span></span>  
  
-   <span data-ttu-id="1fee4-110">Adicionando uma classe de entidade para representar a tabela Orders no banco de dados de exemplo Northwind.</span><span class="sxs-lookup"><span data-stu-id="1fee4-110">Adding an entity class to represent the Orders table in the sample Northwind database.</span></span>  
  
-   <span data-ttu-id="1fee4-111">Suplementando anotações à classe `Customer` para aprimorar a relação entre as classes `Customer` e `Order`.</span><span class="sxs-lookup"><span data-stu-id="1fee4-111">Supplementing annotations to the `Customer` class to enhance the relationship between the `Customer` and `Order` classes.</span></span>  
  
-   <span data-ttu-id="1fee4-112">Criando e executando uma consulta para testar o processo de obtenção de informações de `Order` usando a classe `Customer`.</span><span class="sxs-lookup"><span data-stu-id="1fee4-112">Creating and running a query to test the process of obtaining `Order` information by using the `Customer` class.</span></span>  
  
## <a name="mapping-relationships-across-tables"></a><span data-ttu-id="1fee4-113">Relações de mapeamento entre tabelas</span><span class="sxs-lookup"><span data-stu-id="1fee4-113">Mapping Relationships across Tables</span></span>  
 <span data-ttu-id="1fee4-114">Depois de definir a classe `Customer`, crie a definição da classe de entidade `Order` que inclui o código a seguir, que indica que `Orders.Customer` se relaciona como uma chave estrangeira a `Customers.CustomerID`.</span><span class="sxs-lookup"><span data-stu-id="1fee4-114">After the `Customer` class definition, create the `Order` entity class definition that includes the following code, which indicates that `Orders.Customer` relates as a foreign key to `Customers.CustomerID`.</span></span>  
  
#### <a name="to-add-the-order-entity-class"></a><span data-ttu-id="1fee4-115">Para adicionar a classe de entidade Order</span><span class="sxs-lookup"><span data-stu-id="1fee4-115">To add the Order entity class</span></span>  
  
-   <span data-ttu-id="1fee4-116">Digite ou cole o código a seguir depois da classe `Customer`:</span><span class="sxs-lookup"><span data-stu-id="1fee4-116">Type or paste the following code after the `Customer` class:</span></span>  
  
     [!code-vb[DLinqWalk2VB#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#1)]  
  
## <a name="annotating-the-customer-class"></a><span data-ttu-id="1fee4-117">Anotando a classe Customer</span><span class="sxs-lookup"><span data-stu-id="1fee4-117">Annotating the Customer Class</span></span>  
 <span data-ttu-id="1fee4-118">Nesta etapa, você anota a classe `Customer` para indicar sua relação com a classe `Order`.</span><span class="sxs-lookup"><span data-stu-id="1fee4-118">In this step, you annotate the `Customer` class to indicate its relationship to the `Order` class.</span></span> <span data-ttu-id="1fee4-119">Essa adição não é estritamente necessária, porque a definição da relação em qualquer direção é suficiente para criar o link.</span><span class="sxs-lookup"><span data-stu-id="1fee4-119">(This addition is not strictly necessary, because defining the relationship in either direction is sufficient to create the link.</span></span> <span data-ttu-id="1fee4-120">Mas a adição dessa anotação permite que você navegue objetos facilmente em qualquer direção.</span><span class="sxs-lookup"><span data-stu-id="1fee4-120">But adding this annotation does enable you to easily navigate objects in either direction.)</span></span>  
  
#### <a name="to-annotate-the-customer-class"></a><span data-ttu-id="1fee4-121">Para anotar a classe Customer</span><span class="sxs-lookup"><span data-stu-id="1fee4-121">To annotate the Customer class</span></span>  
  
-   <span data-ttu-id="1fee4-122">Digite ou cole o código a seguir na classe `Customer`:</span><span class="sxs-lookup"><span data-stu-id="1fee4-122">Type or paste the following code into the `Customer` class:</span></span>  
  
     [!code-vb[DLinqWalk2VB#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#2)]  
  
## <a name="creating-and-running-a-query-across-the-customer-order-relationship"></a><span data-ttu-id="1fee4-123">Criando e executando uma consulta pela relação de Customer-Order</span><span class="sxs-lookup"><span data-stu-id="1fee4-123">Creating and Running a Query across the Customer-Order Relationship</span></span>  
 <span data-ttu-id="1fee4-124">Agora você pode acessar objetos `Order` diretamente nos objetos `Customer` ou na ordem oposta.</span><span class="sxs-lookup"><span data-stu-id="1fee4-124">You can now access `Order` objects directly from the `Customer` objects, or in the opposite order.</span></span> <span data-ttu-id="1fee4-125">Não é necessário um explícita *junção* entre clientes e pedidos.</span><span class="sxs-lookup"><span data-stu-id="1fee4-125">You do not need an explicit *join* between customers and orders.</span></span>  
  
#### <a name="to-access-order-objects-by-using-customer-objects"></a><span data-ttu-id="1fee4-126">Para acessar objetos Order usando objetos Customer</span><span class="sxs-lookup"><span data-stu-id="1fee4-126">To access Order objects by using Customer objects</span></span>  
  
1.  <span data-ttu-id="1fee4-127">Modifique o método `Sub Main` digitando ou colando o seguinte código no método:</span><span class="sxs-lookup"><span data-stu-id="1fee4-127">Modify the `Sub Main` method by typing or pasting the following code into the method:</span></span>  
  
     [!code-vb[DLinqWalk2VB#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#3)]  
  
2.  <span data-ttu-id="1fee4-128">Pressione F5 para depurar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1fee4-128">Press F5 to debug your application.</span></span>  
  
     <span data-ttu-id="1fee4-129">Dois nomes aparecem na caixa de mensagem, e a janela Console mostra o código SQL gerado.</span><span class="sxs-lookup"><span data-stu-id="1fee4-129">Two names appear in the message box, and the Console window shows the generated SQL code.</span></span>  
  
3.  <span data-ttu-id="1fee4-130">Feche a caixa de mensagem para interromper a depuração.</span><span class="sxs-lookup"><span data-stu-id="1fee4-130">Close the message box to stop debugging.</span></span>  
  
## <a name="creating-a-strongly-typed-view-of-your-database"></a><span data-ttu-id="1fee4-131">Criando uma exibição fortemente tipada do seu banco de dados</span><span class="sxs-lookup"><span data-stu-id="1fee4-131">Creating a Strongly Typed View of Your Database</span></span>  
 <span data-ttu-id="1fee4-132">É muito mais fácil começar com uma exibição fortemente tipada do seu banco de dados.</span><span class="sxs-lookup"><span data-stu-id="1fee4-132">It is much easier to start with a strongly typed view of your database.</span></span> <span data-ttu-id="1fee4-133">Com o objeto <xref:System.Data.Linq.DataContext> fortemente tipado, você não precisa de chamadas para <xref:System.Data.Linq.DataContext.GetTable%2A>.</span><span class="sxs-lookup"><span data-stu-id="1fee4-133">By strongly typing the <xref:System.Data.Linq.DataContext> object, you do not need calls to <xref:System.Data.Linq.DataContext.GetTable%2A>.</span></span> <span data-ttu-id="1fee4-134">Você pode usar tabelas fortemente tipadas em todas as consultas quando usa o objeto <xref:System.Data.Linq.DataContext> fortemente tipado.</span><span class="sxs-lookup"><span data-stu-id="1fee4-134">You can use strongly typed tables in all your queries when you use the strongly typed <xref:System.Data.Linq.DataContext> object.</span></span>  
  
 <span data-ttu-id="1fee4-135">Nas etapas a seguir, você criará `Customers` como uma tabela fortemente tipada que mapeia para a tabela Customers no banco de dados.</span><span class="sxs-lookup"><span data-stu-id="1fee4-135">In the following steps, you will create `Customers` as a strongly typed table that maps to the Customers table in the database.</span></span>  
  
#### <a name="to-strongly-type-the-datacontext-object"></a><span data-ttu-id="1fee4-136">Para tornar o objeto DataContext fortemente tipado</span><span class="sxs-lookup"><span data-stu-id="1fee4-136">To strongly type the DataContext object</span></span>  
  
1.  <span data-ttu-id="1fee4-137">Adicione o código a seguir acima da declaração da classe `Customer`.</span><span class="sxs-lookup"><span data-stu-id="1fee4-137">Add the following code above the `Customer` class declaration.</span></span>  
  
     [!code-vb[DLinqWalk2VB#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#4)]  
  
2.  <span data-ttu-id="1fee4-138">Modifique `Sub Main` para usar o <xref:System.Data.Linq.DataContext> fortemente tipado da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="1fee4-138">Modify `Sub Main` to use the strongly typed <xref:System.Data.Linq.DataContext> as follows:</span></span>  
  
     [!code-vb[DLinqWalk2VB#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#5)]  
  
3.  <span data-ttu-id="1fee4-139">Pressione F5 para depurar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1fee4-139">Press F5 to debug your application.</span></span>  
  
     <span data-ttu-id="1fee4-140">A saída da janela Console é:</span><span class="sxs-lookup"><span data-stu-id="1fee4-140">The Console window output is:</span></span>  
  
     `ID=WHITC`  
  
4.  <span data-ttu-id="1fee4-141">Pressione Enter na janela Console para fechar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1fee4-141">Press Enter in the Console window to close the application.</span></span>  
  
5.  <span data-ttu-id="1fee4-142">Sobre o **arquivo** menu, clique em **Salvar tudo** se você deseja salvar este aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1fee4-142">On the **File** menu, click **Save All** if you want to save this application.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="1fee4-143">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="1fee4-143">Next Steps</span></span>  
 <span data-ttu-id="1fee4-144">A próximo passo a passo ([passo a passo: manipulando dados (Visual Basic)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-manipulating-data-visual-basic.md)) demonstra como manipular dados.</span><span class="sxs-lookup"><span data-stu-id="1fee4-144">The next walkthrough ([Walkthrough: Manipulating Data (Visual Basic)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-manipulating-data-visual-basic.md)) demonstrates how to manipulate data.</span></span> <span data-ttu-id="1fee4-145">Esse passo a passo não requer que você salve os dois tutoriais passo a passo desta série que você já concluiu.</span><span class="sxs-lookup"><span data-stu-id="1fee4-145">That walkthrough does not require that you save the two walkthroughs in this series that you have already completed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1fee4-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1fee4-146">See Also</span></span>  
 [<span data-ttu-id="1fee4-147">Aprendendo com explicações passo a passo</span><span class="sxs-lookup"><span data-stu-id="1fee4-147">Learning by Walkthroughs</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
