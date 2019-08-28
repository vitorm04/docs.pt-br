---
title: ForEach não genéricos
ms.date: 03/30/2017
ms.assetid: 576cd07a-d58d-4536-b514-77bad60bff38
ms.openlocfilehash: e467534ba2b233f1f3c279e89badf12846c6b7f7
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70038072"
---
# <a name="non-generic-foreach"></a>ForEach não genéricos
[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] envia na caixa de ferramentas um conjunto de atividades de fluxo de controle, incluindo <xref:System.Activities.Statements.ForEach%601>, que permita iterar através das coleções de <xref:System.Collections.Generic.IEnumerable%601> .  
  
 <xref:System.Activities.Statements.ForEach%601> requer sua propriedade de <xref:System.Activities.Statements.ForEach%601.Values%2A> ser do tipo <xref:System.Collections.Generic.IEnumerable%601>. Isso evita que usuários de iterar sobre as estruturas de dados que implementam a interface de <xref:System.Collections.Generic.IEnumerable%601> (por exemplo, <xref:System.Collections.ArrayList>). A versão não genérico de <xref:System.Activities.Statements.ForEach%601> supera esse requisito, custas de mais complexidade de tempo de execução para garantir a compatibilidade dos tipos de valores na coleção.  
  
 Este exemplo mostra como implementar uma atividade não genérico de <xref:System.Activities.Statements.ForEach%601> e seu designer. Esta atividade pode ser usada para percorrer <xref:System.Collections.ArrayList>.  
  
## <a name="foreach-activity"></a>Atividade ForEach  
 A declaração de C#/VB `foreach` enumera os elementos de uma coleção, executando uma instrução inserido para cada elemento da coleção. As atividades equivalentes de [!INCLUDE[wf1](../../../../includes/wf1-md.md)] de `foreach` são <xref:System.Activities.Statements.ForEach%601> e <xref:System.Activities.Statements.ParallelForEach%601>. A atividade de <xref:System.Activities.Statements.ForEach%601> contém uma lista de valores e um corpo. Em tempo de execução, a lista é iterada e o corpo é executado para cada valor na lista.  
  
 Para a maioria dos casos, a versão genérica de atividade deve ser a solução preferencial, porque ele aborda a maioria das situações em que ele deve ser usado, e fornece verificação de tipo em tempo de compilação. A versão não genérico pode ser usada iterando por tipos que implementam a interface não genérica de <xref:System.Collections.IEnumerable> .  
  
## <a name="class-definition"></a>Definição de classe  
 O exemplo de código a seguir mostra a definição de uma atividade não genérico de `ForEach` .  
  
```  
[ContentProperty("Body")]  
public class ForEach : NativeActivity  
{  
    [RequiredArgument]  
    [DefaultValue(null)]  
    InArgument<IEnumerable> Values { get; set; }  
  
    [DefaultValue(null)]  
    [DependsOn("Values")]  
    ActivityAction<object> Body { get; set; }   
}  
```  
  
 Corpo (opcional)  
 <xref:System.Activities.ActivityAction> de tipo <xref:System.Object>, que é executado para cada elemento na coleção. Cada elemento individual é passado no corpo através da propriedade de `Argument` .  
  
 Valores (opcional)  
 A coleção de elementos que são iterados sobre. Garantir que todos os elementos da coleção são de tipos compatíveis é feito em tempo de execução.  
  
## <a name="example-of-using-foreach"></a>Exemplo de usar ForEach  
 O código a seguir demonstra como usar a atividade ForEach em um aplicativo.  
  
```  
string[] names = { "bill", "steve", "ray" };  
  
DelegateInArgument<object> iterationVariable = new DelegateInArgument<object>() { Name = "iterationVariable" };  
  
Activity sampleUsage =  
    new ForEach  
    {  
       Values = new InArgument<IEnumerable>(c=> names),  
       Body = new ActivityAction<object>   
       {                          
           Argument = iterationVariable,  
           Handler = new WriteLine  
           {  
               Text = new InArgument<string>(env => string.Format("Hello {0}",                                                               iterationVariable.Get(env)))  
           }  
       }  
   };  
```  
  
|Condição|Mensagem|Severidade|Tipo de exceção|  
|---------------|-------------|--------------|--------------------|  
|Os valores são `null`|O valor para valores de um argumento necessário de atividade “não foi fornecido.|Erro|<xref:System.InvalidOperationException>|  
  
## <a name="foreach-designer"></a>Designer ForEach  
 O designer de atividade para o exemplo é semelhante a aparência ao designer fornecido para atividades interno de <xref:System.Activities.Statements.ForEach%601> . O designer aparece na caixa de ferramentas na categoria **exemplos**, **atividades não genéricas** . O designer é denominado **ForEachWithBodyFactory** na caixa de ferramentas, porque a atividade expõe <xref:System.Activities.Presentation.IActivityTemplateFactory> um na caixa de ferramentas, que cria a atividade com um <xref:System.Activities.ActivityAction>configurado corretamente.  
  
```  
public sealed class ForEachWithBodyFactory : IActivityTemplateFactory  
{  
    public Activity Create(DependencyObject target)  
    {  
        return new Microsoft.Samples.Activities.Statements.ForEach()  
        {  
            Body = new ActivityAction<object>()  
            {  
                Argument = new DelegateInArgument<object>()  
                {  
                    Name = "item"  
                }  
            }  
        };  
    }  
}  
```  
  
#### <a name="to-run-this-sample"></a>Para executar este exemplo  
  
1. Defina o projeto de sua escolha como o projeto inicialização de solução:  
  
    1. **CodeTestClient** mostra como usar a atividade usando código.  
  
    2. **DesignerTestClient** mostra como usar a atividade dentro do designer.  
  
2. Compile e execute o projeto.  
  
> [!IMPORTANT]
> Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) [!INCLUDE[wf1](../../../../includes/wf1-md.md)] e exemplos. Este exemplo está localizado no seguinte diretório.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\NonGenericForEach`
