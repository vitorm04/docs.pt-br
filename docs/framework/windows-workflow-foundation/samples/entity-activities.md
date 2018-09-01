---
title: Atividades de entidade
ms.date: 03/30/2017
ms.assetid: c04f7413-7fb8-40c6-819e-dc92b145b62e
ms.openlocfilehash: 03bd0e42c70f1226558d492bcb3b2cfa5c7010f2
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43385798"
---
# <a name="entity-activities"></a>Atividades de entidade
Este exemplo mostra como usar o ADO.NET Entity Framework com o Windows Workflow Foundation para simplificar o acesso a dados.  
  
 O ADO.NET Entity Framework permite aos desenvolvedores para trabalhar com dados na forma de objetos, propriedades e relações domínio específicos como clientes, pedidos, detalhes do pedido e relacionamentos entre essas entidades. O ADO.NET Entity Framework faz isto fornecendo um nível de abstração que permite a programação em um modelo conceitual do aplicativo em vez de programação diretamente em um esquema relacional de armazenamento. Para obter mais informações sobre o ADO.NET Entity Framework, consulte [ADO.NET Entity Framework](https://go.microsoft.com/fwlink/?LinkId=165549).  
  
## <a name="sample-details"></a>Detalhes de exemplo  
 Este exemplo usa o base de dados de `Northwind` e incluem scripts para criar e remova a base de dados de `Northwind` (Setup.cmd e Cleanup.cmd). Os projetos nesse exemplo incluem Modelo de Dados de Entidade baseado na base de dados de `Northwind` . Você pode localizar o modelo abrindo o arquivo de `Northwind.edmx` que está incluído no projeto. Esse é o modelo que define a forma de objetos que podem ser acessados usando ADO.NET Entity Framework.  
  
 As seguintes atividades são incluídas neste exemplo:  
  
-   `EntitySQLQuery`: A atividade de `EntitySQLQuery` permite que você recupere objetos de base de dados com base em uma cadeia de caracteres Entity de consulta SQL. Entity SQL é uma linguagem independente de armazenamento que é semelhante ao SQL e permite que você especifique consultas com base no modelo conceitual e as entidades que são uma parte do modelo ou domínio. Para obter mais informações sobre a linguagem Entity SQL, consulte [linguagem Entity SQL](https://go.microsoft.com/fwlink/?LinkId=165646).  
  
-   `EntityLinqQuery`: Esta atividade permite que você recupere objetos de base de dados com base em uma consulta ou em um predicado LINQ.  
  
-   `EntityAdd`: A atividade de `EntityAdd` permite que você adicione uma entidade ou uma coleção das entidades a base de dados.  
  
-   `EntityDelete`: A atividade de `EntityDelete` permite que você exclua uma entidade ou uma coleção de entidades de base de dados.  
  
-   `ObjectContextScope`: As atividades mencionadas anteriormente só podem ser usadas em uma instância recipiente de atividade de `ObjectContextScope` . A atividade de `ObjectContextScope` configura a conexão a base de dados. Requer uma cadeia de conexão (que é passado ou recuperados usando uma configuração do arquivo de configuração). A atividade de `ObjectContextScope` facilita executar um grupo de operações relacionadas em entidades. Porque esse escopo mantém uma conexão ativa, é um nenhum persistir o escopo. Além disso, quando a atividade de `ObjectContextScope` sai, as alterações que são feitas em objetos recuperados usando atividades de entidade dentro do escopo automaticamente obtém persistido de volta a base de dados, e a ação não explícita ou subsequente são necessárias para salvar objetos de volta a base de dados.  
  
## <a name="using-the-entity-activities"></a>Usando as atividades de entidade  
 Os seguintes trechos de código a seguir demonstram como usar as atividades de entidade apresentadas neste exemplo.  
  
### <a name="entitysql"></a>EntitySql  
 O trecho de código abaixo mostra como consultar todos os clientes de Londres classificado por nome e como iterar através da lista de clientes.  
  
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
  
### <a name="entitylinqquery"></a>EntityLinqQuery  
 O trecho de código abaixo mostra como consultar todos os clientes em London e como iterar através da lista resultante de clientes.  
  
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
  
### <a name="entityadd"></a>EntityAdd  
 O trecho de código abaixo mostra como adicionar um registro de OrderDetail para um ordem existente.  
  
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
  
### <a name="entitydelete"></a>EntityDelete  
 O trecho de código abaixo mostra como excluir um registro existente de OrderDetail em uma ordem (se existir).  
  
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
  
## <a name="to-use-this-sample"></a>Para usar este exemplo  
 Você deve criar o base de dados de `Northwind` em sua instância express SQL server local antes de executar este exemplo.  
  
#### <a name="to-set-up-the-northwind-database"></a>Para configurar o base de dados Northwind  
  
1.  Abra um prompt de comando.  
  
2.  Na nova janela do prompt de comando, navegue para a pasta de EntityActivities \ CS.  
  
3.  Tipo `setup.cmd` e pressione ENTER.  
  
#### <a name="to-run-the-sample"></a>Para executar a amostra  
  
1.  Usando [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], abra o arquivo de solução de EntityActivities.sln.  
  
2.  Para criar a solução, pressione CTRL+SHIFT+B.  
  
3.  Para executar a solução, pressione CTRL+F5.  
  
 Depois de executar esse exemplo, você pode desejar remover o base de dados de `Northwind` .  
  
#### <a name="to-uninstall-the-northwind-database"></a>Para desinstalar o base de dados Northwind  
  
1.  Abra um prompt de comando.  
  
2.  Na nova janela do prompt de comando, navegue para a pasta de EntityActivities \ CS.  
  
3.  Tipo `cleanup.cmd` e pressione ENTER.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\EntityActivities`