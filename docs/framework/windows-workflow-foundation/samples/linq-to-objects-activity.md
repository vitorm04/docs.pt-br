---
title: LINQ a atividade de objetos
ms.date: 03/30/2017
ms.assetid: 403c82e8-7f2b-42f6-93cd-95c35bc76ead
ms.openlocfilehash: e2c2be52a88d8f9a886f0e59c027e1d6c737497c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="linq-to-objects-activity"></a>LINQ a atividade de objetos
Este exemplo demonstra como criar uma atividade para usar LINQ a objetos para os elementos de consulta em uma coleção.  
  
## <a name="activity-details-for-findincollection"></a>Detalhes de atividade para FindInCollection  
 Esta atividade permite que os usuários vejam os elementos das coleções na memória usando LINQ a objetos. Você deve fornecer um predicado LINQ na forma de uma expressão lambda para filtrar os resultados. Esta atividade pode ser usada em conjunto com atividades de <xref:System.Activities.Statements.AddToCollection%601> .  
  
 A tabela a seguir detalha a propriedade e valores de retorno para atividades.  
  
|Propriedade ou valor de retorno|Descrição|  
|------------------------------|-----------------|  
|Propriedade `Collection`|Uma propriedade necessário que especifica a coleção fonte.|  
|Propriedade `Predicate`|Uma propriedade necessário que especifica o filtro para a coleção na forma de uma expressão lambda.|  
|Valor de retorno|A coleção filtrada.|  
  
## <a name="code-sample-that-uses-the-custom-activity"></a>Exemplo de código que usa a atividade personalizado  
 O exemplo de código usa a atividade personalizado de `FindInCollection` para localizar todas as linhas em uma coleção de funcionários que têm uma propriedade de `Role` definida como `Manager` e a propriedade `Location` definida como `Redmond`.  
  
```csharp  
// Find all program managers in Redmond in the employees collection.  
  
Activity wf = new FindInCollection<Employee>  
{  
    Collections = new LambdaValue<IEnumerable<Employee>>(c => employees),                
    Predicate = new LambdaValue<Func<Employee, bool>>(c => new Func<Employee, bool>(e => e.Role.Equals("Manager") && e.Location.Equals("Redmond")))  
};  
```  
  
 O código a seguir mostra como criar um programa de fluxo de trabalho que usa a atividade personalizado de FindInCollection, <xref:System.Activities.Statements.AddToCollection%601>, e atividades de <xref:System.Activities.Statements.ForEach%601> para preencher uma coleção com funcionários, localiza os funcionários que têm funções do desenvolvedor e estão localizados em Redmond, e em seguida iterar-lo através da lista resultante.  
  
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
  
#### <a name="to-use-this-sample"></a>Para usar este exemplo  
  
1.  Usando [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], abra o arquivo de solução de LinqToObjects.sln.  
  
2.  Para criar a solução, pressione CTRL+SHIFT+B.  
  
3.  Para executar a solução, pressione F5.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\Linq\LinqToObjects`  
  
## <a name="see-also"></a>Consulte também  
 [Expressões lambda (guia de programação em c#)](http://go.microsoft.com/fwlink/?LinkId=150381)  
 [LINQ to Objects](http://go.microsoft.com/fwlink/?LinkID=150380)
