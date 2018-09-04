---
title: LINQ a atividade de objetos
ms.date: 03/30/2017
ms.assetid: 403c82e8-7f2b-42f6-93cd-95c35bc76ead
ms.openlocfilehash: fca4a94a951c9713a61914de6ef33e0cbb74f75e
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43552762"
---
# <a name="linq-to-objects-activity"></a><span data-ttu-id="b76ee-102">LINQ a atividade de objetos</span><span class="sxs-lookup"><span data-stu-id="b76ee-102">LINQ to Objects Activity</span></span>
<span data-ttu-id="b76ee-103">Este exemplo demonstra como criar uma atividade para usar LINQ a objetos para os elementos de consulta em uma coleção.</span><span class="sxs-lookup"><span data-stu-id="b76ee-103">This sample demonstrates how to create an activity to use LINQ to Objects to query elements in a collection.</span></span>  
  
## <a name="activity-details-for-findincollection"></a><span data-ttu-id="b76ee-104">Detalhes de atividade para FindInCollection</span><span class="sxs-lookup"><span data-stu-id="b76ee-104">Activity Details for FindInCollection</span></span>  
 <span data-ttu-id="b76ee-105">Esta atividade permite que os usuários vejam os elementos das coleções na memória usando LINQ a objetos.</span><span class="sxs-lookup"><span data-stu-id="b76ee-105">This activity allows users to query elements from collections in memory using LINQ to Objects.</span></span> <span data-ttu-id="b76ee-106">Você deve fornecer um predicado LINQ na forma de uma expressão lambda para filtrar os resultados.</span><span class="sxs-lookup"><span data-stu-id="b76ee-106">You must provide a LINQ predicate in the form of a lambda expression to filter the results.</span></span> <span data-ttu-id="b76ee-107">Esta atividade pode ser usada em conjunto com atividades de <xref:System.Activities.Statements.AddToCollection%601> .</span><span class="sxs-lookup"><span data-stu-id="b76ee-107">This activity can be used in conjunction with <xref:System.Activities.Statements.AddToCollection%601> activities.</span></span>  
  
 <span data-ttu-id="b76ee-108">A tabela a seguir detalha a propriedade e valores de retorno para atividades.</span><span class="sxs-lookup"><span data-stu-id="b76ee-108">The following table details the property and return values for the activity.</span></span>  
  
|<span data-ttu-id="b76ee-109">Propriedade ou valor de retorno</span><span class="sxs-lookup"><span data-stu-id="b76ee-109">Property or Return Value</span></span>|<span data-ttu-id="b76ee-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="b76ee-110">Description</span></span>|  
|------------------------------|-----------------|  
|<span data-ttu-id="b76ee-111">Propriedade `Collection`</span><span class="sxs-lookup"><span data-stu-id="b76ee-111">`Collection` property</span></span>|<span data-ttu-id="b76ee-112">Uma propriedade necessário que especifica a coleção fonte.</span><span class="sxs-lookup"><span data-stu-id="b76ee-112">A required property that specifies the source collection.</span></span>|  
|<span data-ttu-id="b76ee-113">Propriedade `Predicate`</span><span class="sxs-lookup"><span data-stu-id="b76ee-113">`Predicate` property</span></span>|<span data-ttu-id="b76ee-114">Uma propriedade necessário que especifica o filtro para a coleção na forma de uma expressão lambda.</span><span class="sxs-lookup"><span data-stu-id="b76ee-114">A required property that specifies the filter for the collection in the form of a lambda expression.</span></span>|  
|<span data-ttu-id="b76ee-115">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="b76ee-115">Return Value</span></span>|<span data-ttu-id="b76ee-116">A coleção filtrada.</span><span class="sxs-lookup"><span data-stu-id="b76ee-116">The filtered collection.</span></span>|  
  
## <a name="code-sample-that-uses-the-custom-activity"></a><span data-ttu-id="b76ee-117">Exemplo de código que usa a atividade personalizado</span><span class="sxs-lookup"><span data-stu-id="b76ee-117">Code Sample that uses the Custom Activity</span></span>  
 <span data-ttu-id="b76ee-118">O exemplo de código usa a atividade personalizado de `FindInCollection` para localizar todas as linhas em uma coleção de funcionários que têm uma propriedade de `Role` definida como `Manager` e a propriedade `Location` definida como `Redmond`.</span><span class="sxs-lookup"><span data-stu-id="b76ee-118">The following code example uses the `FindInCollection` custom activity to find all rows in a collection of employees that have a `Role` property set to `Manager` and the `Location` property set to `Redmond`.</span></span>  
  
```csharp  
// Find all program managers in Redmond in the employees collection.  
  
Activity wf = new FindInCollection<Employee>  
{  
    Collections = new LambdaValue<IEnumerable<Employee>>(c => employees),                
    Predicate = new LambdaValue<Func<Employee, bool>>(c => new Func<Employee, bool>(e => e.Role.Equals("Manager") && e.Location.Equals("Redmond")))  
};  
```  
  
 <span data-ttu-id="b76ee-119">O código a seguir mostra como criar um programa de fluxo de trabalho que usa a atividade personalizado de FindInCollection, <xref:System.Activities.Statements.AddToCollection%601>, e atividades de <xref:System.Activities.Statements.ForEach%601> para preencher uma coleção com funcionários, localiza os funcionários que têm funções do desenvolvedor e estão localizados em Redmond, e em seguida iterar-lo através da lista resultante.</span><span class="sxs-lookup"><span data-stu-id="b76ee-119">The following code shows how to create a workflow program that uses the custom FindInCollection activity, <xref:System.Activities.Statements.AddToCollection%601>, and <xref:System.Activities.Statements.ForEach%601> activities to populate a collection with employees, find all the employees that have developer roles and are located in Redmond, and then iterate through the resulting list.</span></span>  
  
```csharp  
// Create the Linq predicate for the find expression  
  
Func<Employee, bool> predicate = e => e.Role == "DEV" && e.Location.Equals("Redmond");  
  
// Create workflow program  
Activity sampleWorkflow = new Sequence  
{  
    Variables = { employees, devsFromRedmond },  
    Activities =  
    {  
        new Assign<IList<Employee>>  
        {  
            To = employees,  
            Value = new LambdaValue<IList<Employee>>(c => new List<Employee>())  
        },  
        new AddToCollection<Employee>  
        {  
            Collection = new InArgument<ICollection<Employee>>(employees),  
            Item =  new LambdaValue<Employee>(c => new Employee(1, "Employee 1", "DEV", "Redmond"))  
        },  
        new AddToCollection<Employee>  
        {  
            Collection = new InArgument<ICollection<Employee>>(employees),  
            Item =  new LambdaValue<Employee>(c => new Employee(2, "Employee 2", "DEV", "Redmond"))  
        },  
        new AddToCollection<Employee>  
        {  
            Collection = new InArgument<ICollection<Employee>>(employees),  
            Item =  new LambdaValue<Employee>(c => new Employee(3, "Employee 3", "PM", "Redmond"))  
        },  
        new AddToCollection<Employee>  
        {  
            Collection = new InArgument<ICollection<Employee>>(employees),  
            Item =  new LambdaValue<Employee>(c => new Employee(4, "Employee 4", "PM", "China"))  
        },  
        new FindInCollection<Employee>  
        {  
            Collections = new InArgument<IEnumerable<Employee>>(employees),  
            Predicate = new LambdaValue<Func<Employee, bool>>(c => predicate),  
            Result = new OutArgument<IList<Employee>>(devsFromRedmond)  
        },  
        new ForEach<Employee>  
        {  
            Values = new InArgument<IEnumerable<Employee>>(devsFromRedmond),  
            Body = new ActivityAction<Employee>  
            {  
                Argument = iterationVariable,  
                Handler = new WriteLine  
                {  
                    Text = new InArgument<string>(env => iterationVariable.Get(env).ToString())  
                }  
            }  
        }  
    }  
};  
```  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="b76ee-120">Para usar este exemplo</span><span class="sxs-lookup"><span data-stu-id="b76ee-120">To use this sample</span></span>  
  
1.  <span data-ttu-id="b76ee-121">Usando [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], abra o arquivo de solução de LinqToObjects.sln.</span><span class="sxs-lookup"><span data-stu-id="b76ee-121">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the LinqToObjects.sln solution file.</span></span>  
  
2.  <span data-ttu-id="b76ee-122">Para criar a solução, pressione CTRL+SHIFT+B.</span><span class="sxs-lookup"><span data-stu-id="b76ee-122">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="b76ee-123">Para executar a solução, pressione F5.</span><span class="sxs-lookup"><span data-stu-id="b76ee-123">To run the solution, press F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b76ee-124">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="b76ee-124">The samples may already be installed on your machine.</span></span> <span data-ttu-id="b76ee-125">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="b76ee-125">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="b76ee-126">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="b76ee-126">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b76ee-127">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="b76ee-127">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\Linq\LinqToObjects`  
  
## <a name="see-also"></a><span data-ttu-id="b76ee-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b76ee-128">See Also</span></span>  
 [<span data-ttu-id="b76ee-129">Expressões lambda (guia de programação em c#)</span><span class="sxs-lookup"><span data-stu-id="b76ee-129">Lambda Expressions (C# Programming Guide)</span></span>](https://go.microsoft.com/fwlink/?LinkId=150381)  
 [<span data-ttu-id="b76ee-130">LINQ to Objects</span><span class="sxs-lookup"><span data-stu-id="b76ee-130">LINQ to Objects</span></span>](https://go.microsoft.com/fwlink/?LinkID=150380)
