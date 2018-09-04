---
title: Emulação quebrando em um tempo a atividade
ms.date: 03/30/2017
ms.assetid: ddff715d-d623-4b54-b841-60bacbc3ca21
ms.openlocfilehash: 4938e07364609520f6528688877bce112be26d3f
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43560419"
---
# <a name="emulating-breaking-in-a-while-activity"></a>Emulação quebrando em um tempo a atividade
Este exemplo demonstra como dividir o mecanismo de loop das seguintes atividades: <xref:System.Activities.Statements.DoWhile>, <xref:System.Activities.Statements.ForEach%601>, <xref:System.Activities.Statements.While>, e <xref:System.Activities.Statements.ParallelForEach%601>.  
  
 Isso é útil porque o Windows Workflow Foundation (WF) não inclui nenhum atividade para interromper a execução desses loop.  
  
## <a name="scenario"></a>Cenário  
 O exemplo localiza o primeiro fornecedor confiável de uma lista de fornecedores (instâncias da classe `Vendor` ). Cada fornecedor tem `ID`, `Name` e um valor numérico de confiabilidade que determina como o fornecedor é seguro. O exemplo cria uma atividade personalizado chamada `FindReliableVendor` que recebe dois parâmetros de entrada (uma lista de fornecedores e um valor mínimo de confiabilidade) e retorna o primeiro fornecedor de lista que corresponde aos critérios fornecidos.  
  
## <a name="breaking-a-loop"></a>Quebrando um loop  
 Windows Workflow Foundation (WF) não inclui uma atividade para interromper um loop. O exemplo de código a seguir realiza quebrar um loop usando uma atividade de <xref:System.Activities.Statements.If> e diversas variáveis. No exemplo, a atividade de <xref:System.Activities.Statements.While> é interrompida uma vez que a variável de `reliableVendor` é atribuído um valor diferente `null`.  
  
 O exemplo de código a seguir demonstra como dividir o exemplo um loop de quando.  
  
```csharp  
// Iterates while the "i" variable is lower than the size of the list   
// and any reliable Vendor is found.        
new While(env => i.Get(env) < this.Vendors.Get(env).Count && reliableVendor.Get(env) == null)  
{  
    DisplayName = "Main loop. Breaks when a reliable vendor is found",  
    Body = new Sequence  
    {                              
        Activities =  
        {  
            // This is the if used for setting the value of the break value…  
            new If  
            {  
                DisplayName = "Check for a reliable vendor",  
  
                //  If a vendor satisfies the reliability level…  
                Condition = new InArgument<bool>(env =>   
                           this.Vendors.Get(env)[i.Get(env)].Reliability >   
                           this.MinimumReliability.Get(env)),  
  
                // then assign that vendor to the reliable vendor variable and   
                // the while condition becomes false (exit the loop).  
                Then = new Assign<Vendor>  
                {  
                    To = reliableVendor,  
                    Value = new InArgument<Vendor>(env =>   
                                  this.Vendors.Get(env)[i.Get(env)])  
                }  
            },  
  
            // Increment the iteration variable.   
            new Assign<int>  
            {  
                DisplayName = "Increment iteration variable",  
                To = i,  
                Value = new InArgument<int>(env => i.Get(env) + 1)  
            }   
        }  
    }  
}  
```  
  
#### <a name="to-use-this-sample"></a>Para usar este exemplo  
  
1.  Usando [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], abra o arquivo de solução de EmulatingBreakInWhile.sln.  
  
2.  Para criar a solução, pressione CTRL+SHIFT+B.  
  
3.  Para executar a solução, pressione CTRL+F5.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\EmulatingBreakInWhile`