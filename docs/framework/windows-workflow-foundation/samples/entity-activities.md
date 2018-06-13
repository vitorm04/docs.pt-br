---
title: Atividades de entidade
ms.date: 03/30/2017
ms.assetid: c04f7413-7fb8-40c6-819e-dc92b145b62e
ms.openlocfilehash: 96301c15b849749299e744a435068c3ec9be2e3a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33519130"
---
# <a name="entity-activities"></a><span data-ttu-id="e53cb-102">Atividades de entidade</span><span class="sxs-lookup"><span data-stu-id="e53cb-102">Entity Activities</span></span>
<span data-ttu-id="e53cb-103">Este exemplo mostra como usar o ADO.NET Entity Framework com o Windows Workflow Foundation para simplificar o acesso a dados.</span><span class="sxs-lookup"><span data-stu-id="e53cb-103">This sample shows how to use the ADO.NET Entity Framework with Windows Workflow Foundation to simplify data access.</span></span>  
  
 <span data-ttu-id="e53cb-104">O ADO.NET Entity Framework permite aos desenvolvedores para trabalhar com dados na forma de objetos, propriedades e relações domínio específicos como clientes, pedidos, detalhes do pedido e relacionamentos entre essas entidades.</span><span class="sxs-lookup"><span data-stu-id="e53cb-104">The ADO.NET Entity Framework enables developers to work with data in the form of domain-specific objects, properties and relationships such as Customers, Orders, Order Details and the relationships between these entities.</span></span> <span data-ttu-id="e53cb-105">O ADO.NET Entity Framework faz isto fornecendo um nível de abstração que permite a programação em um modelo conceitual do aplicativo em vez de programação diretamente em um esquema relacional de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="e53cb-105">The ADO.NET Entity Framework does this by providing a level of abstraction that enables programming against a conceptual application model instead of programming directly against a relational storage schema.</span></span> <span data-ttu-id="e53cb-106">Para obter mais informações sobre, consulte o ADO.NET Entity Framework [ADO.NET Entity Framework](http://go.microsoft.com/fwlink/?LinkId=165549).</span><span class="sxs-lookup"><span data-stu-id="e53cb-106">For more information about the ADO.NET Entity Framework see [ADO.NET Entity Framework](http://go.microsoft.com/fwlink/?LinkId=165549).</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="e53cb-107">Detalhes de exemplo</span><span class="sxs-lookup"><span data-stu-id="e53cb-107">Sample details</span></span>  
 <span data-ttu-id="e53cb-108">Este exemplo usa o base de dados de `Northwind` e incluem scripts para criar e remova a base de dados de `Northwind` (Setup.cmd e Cleanup.cmd).</span><span class="sxs-lookup"><span data-stu-id="e53cb-108">This sample uses the `Northwind` database and includes scripts for creating and removing the `Northwind` database (Setup.cmd and Cleanup.cmd).</span></span> <span data-ttu-id="e53cb-109">Os projetos nesse exemplo incluem Modelo de Dados de Entidade baseado na base de dados de `Northwind` .</span><span class="sxs-lookup"><span data-stu-id="e53cb-109">The projects in this sample include an Entity Data Model based on the `Northwind` database.</span></span> <span data-ttu-id="e53cb-110">Você pode localizar o modelo abrindo o arquivo de `Northwind.edmx` que está incluído no projeto.</span><span class="sxs-lookup"><span data-stu-id="e53cb-110">You can find the model by opening the `Northwind.edmx` file that is included in the project.</span></span> <span data-ttu-id="e53cb-111">Esse é o modelo que define a forma de objetos que podem ser acessados usando ADO.NET Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="e53cb-111">This is the model that defines the shape of the objects that can be accessed using the ADO.NET Entity Framework.</span></span>  
  
 <span data-ttu-id="e53cb-112">As seguintes atividades são incluídas neste exemplo:</span><span class="sxs-lookup"><span data-stu-id="e53cb-112">The following activities are included in this sample:</span></span>  
  
-   <span data-ttu-id="e53cb-113">`EntitySQLQuery`: A atividade de `EntitySQLQuery` permite que você recupere objetos de base de dados com base em uma cadeia de caracteres Entity de consulta SQL.</span><span class="sxs-lookup"><span data-stu-id="e53cb-113">`EntitySQLQuery`: The `EntitySQLQuery` activity allows you to retrieve objects from the database based on an Entity SQL query string.</span></span> <span data-ttu-id="e53cb-114">Entity SQL é uma linguagem independente de armazenamento que é semelhante ao SQL e permite que você especifique consultas com base no modelo conceitual e as entidades que são uma parte do modelo ou domínio.</span><span class="sxs-lookup"><span data-stu-id="e53cb-114">Entity SQL is a store independent language that is similar to SQL and it allows you to specify queries based on the conceptual model and the entities that are a part of the model or domain.</span></span> <span data-ttu-id="e53cb-115">Para obter mais informações sobre linguagem Entity SQL, consulte [linguagem Entity SQL](http://go.microsoft.com/fwlink/?LinkId=165646).</span><span class="sxs-lookup"><span data-stu-id="e53cb-115">For more information about Entity SQL Language, see [Entity SQL Language](http://go.microsoft.com/fwlink/?LinkId=165646).</span></span>  
  
-   <span data-ttu-id="e53cb-116">`EntityLinqQuery`: Esta atividade permite que você recupere objetos de base de dados com base em uma consulta ou em um predicado LINQ.</span><span class="sxs-lookup"><span data-stu-id="e53cb-116">`EntityLinqQuery`: This activity allows you to retrieve objects from the database based on a LINQ query or predicate.</span></span>  
  
-   <span data-ttu-id="e53cb-117">`EntityAdd`: A atividade de `EntityAdd` permite que você adicione uma entidade ou uma coleção das entidades a base de dados.</span><span class="sxs-lookup"><span data-stu-id="e53cb-117">`EntityAdd`: The `EntityAdd` activity allows you to add an entity or a collection of entities to the database.</span></span>  
  
-   <span data-ttu-id="e53cb-118">`EntityDelete`: A atividade de `EntityDelete` permite que você exclua uma entidade ou uma coleção de entidades de base de dados.</span><span class="sxs-lookup"><span data-stu-id="e53cb-118">`EntityDelete`: The `EntityDelete` activity allows you to delete an entity or a collection of entities from the database.</span></span>  
  
-   <span data-ttu-id="e53cb-119">`ObjectContextScope`: As atividades mencionadas anteriormente só podem ser usadas em uma instância recipiente de atividade de `ObjectContextScope` .</span><span class="sxs-lookup"><span data-stu-id="e53cb-119">`ObjectContextScope`: The previously mentioned activities can only be used within a containing `ObjectContextScope` activity instance.</span></span> <span data-ttu-id="e53cb-120">A atividade de `ObjectContextScope` configura a conexão a base de dados.</span><span class="sxs-lookup"><span data-stu-id="e53cb-120">The `ObjectContextScope` activity sets up the connection to the database.</span></span> <span data-ttu-id="e53cb-121">Requer uma cadeia de conexão (que é passado ou recuperados usando uma configuração do arquivo de configuração).</span><span class="sxs-lookup"><span data-stu-id="e53cb-121">It requires a connection string (that is either passed in or retrieved using a configuration file setting).</span></span> <span data-ttu-id="e53cb-122">A atividade de `ObjectContextScope` facilita executar um grupo de operações relacionadas em entidades.</span><span class="sxs-lookup"><span data-stu-id="e53cb-122">The `ObjectContextScope` activity makes it easy to perform a group of related operations on entities.</span></span> <span data-ttu-id="e53cb-123">Porque esse escopo mantém uma conexão ativa, é um nenhum persistir o escopo.</span><span class="sxs-lookup"><span data-stu-id="e53cb-123">Because this scope maintains an active connection, it is a No Persist scope.</span></span> <span data-ttu-id="e53cb-124">Além disso, quando a atividade de `ObjectContextScope` sai, as alterações que são feitas em objetos recuperados usando atividades de entidade dentro do escopo automaticamente obtém persistido de volta a base de dados, e a ação não explícita ou subsequente são necessárias para salvar objetos de volta a base de dados.</span><span class="sxs-lookup"><span data-stu-id="e53cb-124">In addition, when the `ObjectContextScope` activity exits, any changes that are made to objects retrieved using Entity Activities within that scope automatically get persisted back to the database, and no explicit or subsequent action is required to save objects back to the database.</span></span>  
  
## <a name="using-the-entity-activities"></a><span data-ttu-id="e53cb-125">Usando as atividades de entidade</span><span class="sxs-lookup"><span data-stu-id="e53cb-125">Using the entity activities</span></span>  
 <span data-ttu-id="e53cb-126">Os seguintes trechos de código a seguir demonstram como usar as atividades de entidade apresentadas neste exemplo.</span><span class="sxs-lookup"><span data-stu-id="e53cb-126">The following code snippets demonstrate how to use the entity activities presented in this sample.</span></span>  
  
### <a name="entitysql"></a><span data-ttu-id="e53cb-127">EntitySql</span><span class="sxs-lookup"><span data-stu-id="e53cb-127">EntitySql</span></span>  
 <span data-ttu-id="e53cb-128">O trecho de código abaixo mostra como consultar todos os clientes de Londres classificado por nome e como iterar através da lista de clientes.</span><span class="sxs-lookup"><span data-stu-id="e53cb-128">The code snippet below shows how to query all customers in London sorted by name and how to iterate through the list of customers.</span></span>  
  
```  
Variable<IEnumerable<Customer>> londonCustomers = new Variable<IEnumerable<Customer>>();  
DelegateInArgument<Customer> iterationVariable = new DelegateInArgument<Customer>();  
  
// create and return the workflow  
return new ObjectContextScope  
{  
    ConnectionString = new InArgument<string>(connStr),  
    ContainerName = "NorthwindEntities",  
    Variables = { londonCustomers },  
    Body = new Sequence  
        {  
            Activities =   
                {               
                    new WriteLine { Text = "Executing query" },                            
                    // query for all customers that are in london   
                    new EntitySqlQuery<Customer>  
                    {  
                        EntitySql =  @"SELECT VALUE Customer   
                                        FROM NorthwindEntities.Customers AS Customer   
                                        WHERE Customer.City = 'London'   
                                        ORDER BY Customer.ContactName",  
                        Result = londonCustomers  
                    },  
  
                    // iterate through the list of customers and display them   
                    new ForEach<Customer>  
                    {                                      
                        Values = londonCustomers,  
                        Body = new ActivityAction<Customer>  
                        {  
                            Argument = iterationVariable,  
                            Handler = new WriteLine   
                            {   
                                  Text = new InArgument<String>(e =>    
                                              iterationVariable.Get(e).ContactName)   
                            }  
                        }  
                    }  
                }  
        }                 
};     
```  
  
### <a name="entitylinqquery"></a><span data-ttu-id="e53cb-129">EntityLinqQuery</span><span class="sxs-lookup"><span data-stu-id="e53cb-129">EntityLinqQuery</span></span>  
 <span data-ttu-id="e53cb-130">O trecho de código abaixo mostra como consultar todos os clientes em London e como iterar através da lista resultante de clientes.</span><span class="sxs-lookup"><span data-stu-id="e53cb-130">The code snippet below shows how to query all customers in London and how to iterate through the resulting list of customers.</span></span>  
  
```  
Variable<IEnumerable<Customer>> londonCustomers = new Variable<IEnumerable<Customer>>() { Name = "LondonCustomers" };  
DelegateInArgument<Customer> iterationVariable = new DelegateInArgument<Customer>() { Name = "iterationVariable" };  
  
return new ObjectContextScope  
{  
    ConnectionString = new InArgument<string>(connStr),  
    ContainerName = "NorthwindEntities",  
    Variables = { londonCustomers },  
    Body = new Sequence  
    {  
        Activities =   
        {               
            // return all the customers that match with the provided Linq predicate  
            new EntityLinqQuery<Customer>  
            {   
                Predicate = new LambdaValue<Func<Customer, bool>>(  
                          ctx => new Func<Customer, bool>(c => c.City.Equals("London"))),                              
                Result = londonCustomers  
            },  
  
            // iterate through the list of customers and display in the console  
            new ForEach<Customer>  
            {                                      
                Values = londonCustomers,  
                Body = new ActivityAction<Customer>  
                {  
                    Argument = iterationVariable,  
                    Handler = new WriteLine   
                    {   
                        Text = new InArgument<String>(e =>   
                                      iterationVariable.Get(e).ContactName)   
                    }  
                }  
            }  
        }  
    }  
};  
```  
  
### <a name="entityadd"></a><span data-ttu-id="e53cb-131">EntityAdd</span><span class="sxs-lookup"><span data-stu-id="e53cb-131">EntityAdd</span></span>  
 <span data-ttu-id="e53cb-132">O trecho de código abaixo mostra como adicionar um registro de OrderDetail para um ordem existente.</span><span class="sxs-lookup"><span data-stu-id="e53cb-132">The code snippet below shows how to add an OrderDetail record to an existing Order.</span></span>  
  
```  
Variable<IEnumerable<Order>> orders = new Variable<IEnumerable<Order>>();  
Variable<IEnumerable<OrderDetail>> orderDetails = new Variable<IEnumerable<OrderDetail>>();  
Variable<Order> order = new Variable<Order>();  
Variable<OrderDetail> orderDetail = new Variable<OrderDetail>();              
  
return new ObjectContextScope  
{  
    Variables = { order, orders, orderDetail, orderDetails },  
    ContainerName = "NorthwindEntities",  
    ConnectionString = new InArgument<string>(connStr),                  
    Body = new Sequence  
    {                      
        Activities =   
        {                            
           // get the order where we want to add the detail  
           new EntitySqlQuery<Order>  
           {  
               EntitySql =    
                    @"SELECT VALUE [Order]  
                      FROM NorthwindEntities.Orders as [Order]  
                      WHERE Order.OrderID == 10249",  
               Result = orders  
           },  
  
           // store the order in a variable  
           new Assign<Order>   
           {  
               To = new OutArgument<Order>(order),  
               Value = new InArgument<Order>(c => orders.Get(c).First<Order>())  
           },  
  
           // add the detail to the order  
           new EntityAdd<OrderDetail>  
           {  
               Entity = new InArgument<OrderDetail>(c =>   
                                         new OrderDetail {   
                                                  OrderID=10249, ProductID=11,   
                                                  Quantity=1, UnitPrice = 15,   
                                                  Discount = 0, Order = order.Get(c) })  
           }  
        }  
    }  
};  
```  
  
### <a name="entitydelete"></a><span data-ttu-id="e53cb-133">EntityDelete</span><span class="sxs-lookup"><span data-stu-id="e53cb-133">EntityDelete</span></span>  
 <span data-ttu-id="e53cb-134">O trecho de código abaixo mostra como excluir um registro existente de OrderDetail em uma ordem (se existir).</span><span class="sxs-lookup"><span data-stu-id="e53cb-134">The code snippet below shows how to delete an existing OrderDetail record in an Order (if it exists).</span></span>  
  
```  
Variable<IEnumerable<OrderDetail>> orderDetails = new Variable<IEnumerable<OrderDetail>>();              
  
return new ObjectContextScope  
{  
    Variables = { orderDetails },  
    ConnectionString = new InArgument<string>(connStr),  
    ContainerName = "NorthwindEntities",  
    Body = new Sequence  
    {  
        Activities =   
        {               
            // find the entitiy to be deleted (order detail for product 11 in order 10249)  
            new EntitySqlQuery<OrderDetail>  
            {  
                EntitySql = @"SELECT VALUE OrderDetail  
                                FROM NorthwindEntities.OrderDetails as OrderDetail  
                               WHERE OrderDetail.OrderID == 10249   
                                 AND OrderDetail.ProductID == 11",  
                Result = orderDetails  
            },  
  
            // if the order detail is found, delete it, otherwise, display a message  
            new If  
            {  
                Condition = new InArgument<bool>(c=>orderDetails.Get(c).Count() > 0),  
                Then = new Sequence  
                {   
                    Activities =   
                    {                                      
                        new EntityDelete<OrderDetail>  
                        {  
                            Entity = new InArgument<OrderDetail>(c =>   
                                              orderDetails.Get(c).First<OrderDetail>())  
                        },  
                    }  
                },                              
                Else = new WriteLine { Text = "Order Detail for Deleting not found" }                              
            }                                                  
        }  
    }  
};  
```  
  
## <a name="to-use-this-sample"></a><span data-ttu-id="e53cb-135">Para usar este exemplo</span><span class="sxs-lookup"><span data-stu-id="e53cb-135">To use this sample</span></span>  
 <span data-ttu-id="e53cb-136">Você deve criar o base de dados de `Northwind` em sua instância express SQL server local antes de executar este exemplo.</span><span class="sxs-lookup"><span data-stu-id="e53cb-136">You must create the `Northwind` database in your local SQL server Express instance before running this sample.</span></span>  
  
#### <a name="to-set-up-the-northwind-database"></a><span data-ttu-id="e53cb-137">Para configurar o base de dados Northwind</span><span class="sxs-lookup"><span data-stu-id="e53cb-137">To set up the Northwind database</span></span>  
  
1.  <span data-ttu-id="e53cb-138">Abra um prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="e53cb-138">Open a command prompt.</span></span>  
  
2.  <span data-ttu-id="e53cb-139">Na nova janela do prompt de comando, navegue para a pasta de EntityActivities \ CS.</span><span class="sxs-lookup"><span data-stu-id="e53cb-139">In the new command prompt window, navigate to the EntityActivities\CS folder.</span></span>  
  
3.  <span data-ttu-id="e53cb-140">Tipo `setup.cmd` e pressione ENTER.</span><span class="sxs-lookup"><span data-stu-id="e53cb-140">Type `setup.cmd` and press ENTER.</span></span>  
  
#### <a name="to-run-the-sample"></a><span data-ttu-id="e53cb-141">Para executar a amostra</span><span class="sxs-lookup"><span data-stu-id="e53cb-141">To run the sample</span></span>  
  
1.  <span data-ttu-id="e53cb-142">Usando [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], abra o arquivo de solução de EntityActivities.sln.</span><span class="sxs-lookup"><span data-stu-id="e53cb-142">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open the EntityActivities.sln solution file.</span></span>  
  
2.  <span data-ttu-id="e53cb-143">Para criar a solução, pressione CTRL+SHIFT+B.</span><span class="sxs-lookup"><span data-stu-id="e53cb-143">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="e53cb-144">Para executar a solução, pressione CTRL+F5.</span><span class="sxs-lookup"><span data-stu-id="e53cb-144">To run the solution, press CTRL+F5.</span></span>  
  
 <span data-ttu-id="e53cb-145">Depois de executar esse exemplo, você pode desejar remover o base de dados de `Northwind` .</span><span class="sxs-lookup"><span data-stu-id="e53cb-145">After running this sample, you may want to remove the `Northwind` database.</span></span>  
  
#### <a name="to-uninstall-the-northwind-database"></a><span data-ttu-id="e53cb-146">Para desinstalar o base de dados Northwind</span><span class="sxs-lookup"><span data-stu-id="e53cb-146">To uninstall the Northwind database</span></span>  
  
1.  <span data-ttu-id="e53cb-147">Abra um prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="e53cb-147">Open a command prompt.</span></span>  
  
2.  <span data-ttu-id="e53cb-148">Na nova janela do prompt de comando, navegue para a pasta de EntityActivities \ CS.</span><span class="sxs-lookup"><span data-stu-id="e53cb-148">In the new command prompt window, navigate to the EntityActivities\CS folder.</span></span>  
  
3.  <span data-ttu-id="e53cb-149">Tipo `cleanup.cmd` e pressione ENTER.</span><span class="sxs-lookup"><span data-stu-id="e53cb-149">Type `cleanup.cmd` and press ENTER.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e53cb-150">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="e53cb-150">The samples may already be installed on your machine.</span></span> <span data-ttu-id="e53cb-151">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="e53cb-151">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="e53cb-152">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="e53cb-152">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e53cb-153">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="e53cb-153">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\EntityActivities`