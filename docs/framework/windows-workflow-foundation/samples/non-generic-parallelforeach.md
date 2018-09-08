---
title: ParallelForEach não genéricos
ms.date: 03/30/2017
ms.assetid: de17e7a2-257b-48b3-91a1-860e2e9bf6e6
ms.openlocfilehash: 70d5de587dda3cb61205a8d77f2173df9b93498b
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44210579"
---
# <a name="non-generic-parallelforeach"></a>ParallelForEach não genéricos
[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] é fornecido na caixa de ferramentas, um conjunto de atividades de fluxo de controle, incluindo <xref:System.Activities.Statements.ParallelForEach%601>, que permite iterar <!--zz <xref:System.Collections.IEnumerable%601> --> `System.Collections.IEnumerable` coleções.  
  
 <xref:System.Activities.Statements.ParallelForEach%601> requer seu <xref:System.Activities.Statements.ParallelForEach%601.Values%2A> propriedade para ser do tipo <!--zz <xref:System.Collections.IEnumerable%601> --> `System.Collections.IEnumerable`. Isso evita que usuários de iterar sobre estruturas de dados que implementam <!--zz <xref:System.Collections.IEnumerable%601> --> `System.Collections.IEnumerable` interface (por exemplo, <xref:System.Collections.ArrayList>). A versão não genérico de <xref:System.Activities.Statements.ParallelForEach%601> supera esse requisito, custas de mais complexidade de tempo de execução para garantir a compatibilidade dos tipos de valores na coleção.  
  
 Este exemplo mostra como implementar uma atividade não genérico de <xref:System.Activities.Statements.ParallelForEach%601> e seu designer. Esta atividade pode ser usada para percorrer <xref:System.Collections.ArrayList>.  
  
## <a name="parallelforeach-activity"></a>Atividade de ParallelForEach  
 A declaração de C#/VB `foreach` enumera os elementos de uma coleção, executando uma instrução inserido para cada elemento da coleção. As atividades equivalentes de [!INCLUDE[wf1](../../../../includes/wf1-md.md)] são <xref:System.Activities.Statements.ForEach%601> e <xref:System.Activities.Statements.ParallelForEach%601>. A atividade de <xref:System.Activities.Statements.ForEach%601> contém uma lista de valores e um corpo. Em tempo de execução, a lista é iterada e o corpo é executado para cada valor na lista.  
  
 <xref:System.Activities.Statements.ParallelForEach%601> tem <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A>, de modo que a atividade de <xref:System.Activities.Statements.ParallelForEach%601> pode concluir no início se a avaliação de <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> retorna `true`. <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> é avaliado após cada iteração é concluída.  
  
 Para a maioria dos casos, a versão genérica de atividade deve ser a solução preferencial, porque ele aborda a maioria das situações em que é usada e fornece verificação de tipo em tempo de compilação. A versão não genérico pode ser usada iterando por tipos que implementam a interface não genérica de <xref:System.Collections.IEnumerable> .  
  
## <a name="class-definition"></a>Definição de classe  
 O exemplo de código a seguir mostra a definição de uma atividade não genérico de `ParallelForEach` é.  
  
```  
[ContentProperty("Body")]  
public class ParallelForEach : NativeActivity  
{  
    [RequiredArgument]  
    [DefaultValue(null)]  
    InArgument<IEnumerable> Values { get; set; }  
  
    [DefaultValue(null)]  
    [DependsOn("Values")]  
    public Activity<bool> CompletionCondition  
    [DefaultValue(null)]  
    [DependsOn("CompletionCondition")]  
    ActivityAction<object> Body { get; set; }   
}  
```  
  
 Corpo (opcional)  
 <xref:System.Activities.ActivityAction> de tipo <xref:System.Object>, que é executado para cada elemento na coleção. Cada elemento individual é passado no corpo através da propriedade do argumento.  
  
 Valores (opcional)  
 A coleção de elementos que são iterados sobre. Garantir que todos os elementos da coleção são de tipos compatíveis é feito em tempo de execução.  
  
 CompletionCondition (opcional)  
 A propriedade de <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> é avaliada após qualquer iteração completa. Se for avaliada como `true`, então o agendada durante iterações é cancelado. Se esta propriedade não for definida, todas as atividades na coleção de ramificações executam até a conclusão.  
  
## <a name="example-of-using-parallelforeach"></a>Exemplo de usar ParallelForEach  
 O código a seguir demonstra como usar a atividade de ParallelForEach em um aplicativo.  
  
```  
string[] names = { "bill", "steve", "ray" };  
  
DelegateInArgument<object> iterationVariable = new DelegateInArgument<object>() { Name = "iterationVariable" };  
  
Activity sampleUsage =  
    new ParallelForEach  
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
  
## <a name="parallelforeach-designer"></a>Designer de ParallelForEach  
 O designer de atividade para o exemplo é semelhante a aparência ao designer fornecido para atividades interno de <xref:System.Activities.Statements.ParallelForEach%601> . O designer aparece na caixa de ferramentas do **amostras**, **atividades não genéricas** categoria. O designer é chamado **ParallelForEachWithBodyFactory** na caixa de ferramentas, porque a atividade expõe uma <xref:System.Activities.Presentation.IActivityTemplateFactory> na caixa de ferramentas que cria a atividade com configurada adequadamente <xref:System.Activities.ActivityAction>.  
  
```  
public sealed class ParallelForEachWithBodyFactory : IActivityTemplateFactory  
{  
    public Activity Create(DependencyObject target)  
    {  
        return new Microsoft.Samples.Activities.Statements.ParallelForEach()  
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
  
#### <a name="to-run-the-sample"></a>Para executar a amostra  
  
1.  Defina o projeto de sua escolha como o projeto de inicialização de solução.  
  
    1.  **CodeTestClient** mostra como usar a atividade usando código.  
  
    2.  **DesignerTestClient** mostra como usar a atividade dentro do designer.  
  
2.  Compile e execute o projeto.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\NonGenericParallelForEach`
