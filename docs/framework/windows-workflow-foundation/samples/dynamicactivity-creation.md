---
title: "Criação de DynamicActivity"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d8ebe82f-98c8-4452-aed7-2c60a512b097
caps.latest.revision: "14"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4a579606bd3ee9d3f11669d59c6e7c9767b6eaf4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="dynamicactivity-creation"></a>Criação de DynamicActivity
Este exemplo demonstra duas maneiras diferentes para criar uma atividade em tempo de execução usando a atividade de <xref:System.Activities.DynamicActivity> .  
  
 Nesse exemplo, uma atividade é criada em tempo de execução com um corpo que contém uma atividade de <xref:System.Activities.Statements.Sequence> que contém <xref:System.Activities.Statements.ForEach%601> e atividades de <xref:System.Activities.Statements.Assign%601> . Uma lista de entrada de inteiros é passada para a atividade e o conjunto como uma propriedade. A atividade de <xref:System.Activities.Statements.ForEach%601> em itera através da lista de valores e acumula-a. Na atividade de <xref:System.Activities.Statements.Assign%601> , o valor médio é calculado dividindo o acumulador pelo número de elementos na lista e atribuí-la a média.  
  
 O exemplo demonstra o uso de uma atividade de <xref:System.Activities.DynamicActivity> que flui em variáveis como argumentos de entrada e retornar valores como argumentos de saída. A atividade tem um `Numbers` chamado argumento conectado que é uma lista de inteiros. A atividade de <xref:System.Activities.Statements.ForEach%601> itera através da lista de valores e acumula-a. Na atividade de <xref:System.Activities.Statements.Assign%601> , o valor médio é calculado dividindo o acumulador pelo número de elementos na lista e atribuindo a média. A média é retornada como um argumento de saída chamado `Average`.  
  
 Quando a atividade dinâmico é criada por meio de programação, entrada e saída são declaradas como mostrado no exemplo de código.  
  
```csharp  
DynamicActivity act = new DynamicActivity()  
{  
    DisplayName = "Find average",  
    Properties =   
    {  
        // Input argument  
        new DynamicActivityProperty  
        {  
            Name = "Numbers",  
            Type = typeof(InArgument<List<int>>),  
            Value = numbers  
        },  
        // Output argument  
        new DynamicActivityProperty  
        {  
            Name = "Average",  
            Type = typeof(OutArgument<double>),  
            Value = average  
        }  
    },  
};  
```  
  
 O exemplo de código a seguir mostra a definição completa de `DynamicActivity` que calcula a média dos valores em uma lista.  
  
```  
DynamicActivity act = new DynamicActivity()  
{  
    DisplayName = "Find average",  
    Properties =   
    {  
        // Input argument  
        new DynamicActivityProperty  
        {  
            Name = "Numbers",  
            Type = typeof(InArgument<List<int>>),  
            Value = numbers  
        },  
        // Output argument  
        new DynamicActivityProperty  
        {  
            Name = "Average",  
            Type = typeof(OutArgument<double>),  
            Value = average  
        }  
    },  
    Implementation = () =>  
        new Sequence  
        {  
            Variables = { result, accumulator },  
            Activities =  
            {  
                new ForEach<int>  
                {  
                    Values =  new ArgumentValue<IEnumerable<int>> { ArgumentName = "Numbers" },                                  
                    Body = new ActivityAction<int>  
                    {  
                        Argument = iterationVariable,  
                        Handler = new Assign<int>  
                        {  
                            To = accumulator,  
                            Value = new InArgument<int>(env => iterationVariable.Get(env) +  accumulator.Get(env))  
                        }  
                    }  
                },  
  
                // Calculate the average and assign to the output argument.  
                new Assign<double>  
                {  
                    To = new ArgumentReference<double> { ArgumentName = "Average" },  
                    Value = new InArgument<double>(env => accumulator.Get(env) / numbers.Get(env).Count<int>())  
                },  
            }  
        }  
};  
```  
  
 Quando criada em XAML, entrada e saída são declaradas como mostrado no exemplo a seguir.  
  
```xml  
<Activity x:Class="Microsoft.Samples.DynamicActivityCreation.FindAverage"  
          xmlns="http://schemas.microsoft.com/netfx/2009/xaml/activities"  
          xmlns:scg="clr-namespace:System.Collections.Generic;assembly=mscorlib"  
          xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
  <x:Members>  
    <x:Property Name="Numbers" Type="InArgument(scg:List(x:Int32))" />  
    <x:Property Name="Average" Type="OutArgument(x:Double)" />  
  </x:Members>  
    ...  
    ...  
</Activity>  
```  
  
 O XAML pode ser criado usando [!INCLUDE[wfd1](../../../../includes/wfd1-md.md)]visualmente. Se estiver incluído em um projeto do Visual Studio, certifique-se de definir seu "Build Action" para "None" para impedir que está sendo compilada. O XAML pode então ser carregado dinamicamente usando a chamada a seguir.  
  
```  
Activity act2 = ActivityXamlServices.Load(@"FindAverage.xaml");  
```  
  
 A instância de <xref:System.Activities.DynamicActivity> criada ou carregar programaticamente com um fluxo de trabalho XAML pode ser usada como mostrado no exemplo de código. Observe que "atuar" passado para o `WorkflowInvoker.Invoke` é o ato de"" <xref:System.Activities.Activity> definido no primeiro exemplo de código.  
  
```  
IDictionary<string, object> results = WorkflowInvoker.Invoke(act, new Dictionary<string, object> { { "Numbers", numbers } });  
  
Console.WriteLine("The average calculated using the code activity is = " + results["Average"]);  
```  
  
#### <a name="to-use-this-sample"></a>Para usar este exemplo  
  
1.  Usando [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], abra o arquivo de solução de DynamicActivityCreation.sln.  
  
2.  Para criar a solução, pressione CTRL+SHIFT+B.  
  
3.  Para executar a solução, pressione CTRL+F5.  
  
## <a name="command-line-arguments"></a>Argumentos de linha de comando  
 Este exemplo aceita argumentos de linha de comando. Os usuários podem fornecer uma lista de números para que a atividade calcula a média. A lista de números a ser usado é passada como uma lista de números se ter separado por um espaço. Por exemplo, para calcular a média de 5, 10 e 32, chamam o exemplo usando a seguinte linha de comando.  
  
 **DynamicActivityCreation 5 10 32**  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\DynamicActivity\DynamicActivityCreation`  
  
## <a name="see-also"></a>Consulte também
