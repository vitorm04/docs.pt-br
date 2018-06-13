---
title: Emulação quebrando em um tempo a atividade
ms.date: 03/30/2017
ms.assetid: ddff715d-d623-4b54-b841-60bacbc3ca21
ms.openlocfilehash: 37c64c2b8dc03d58f9c2802edef644fe4888e87d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33514707"
---
# <a name="emulating-breaking-in-a-while-activity"></a><span data-ttu-id="06a3e-102">Emulação quebrando em um tempo a atividade</span><span class="sxs-lookup"><span data-stu-id="06a3e-102">Emulating breaking in a While activity</span></span>
<span data-ttu-id="06a3e-103">Este exemplo demonstra como dividir o mecanismo de loop das seguintes atividades: <xref:System.Activities.Statements.DoWhile>, <xref:System.Activities.Statements.ForEach%601>, <xref:System.Activities.Statements.While>, e <xref:System.Activities.Statements.ParallelForEach%601>.</span><span class="sxs-lookup"><span data-stu-id="06a3e-103">This sample demonstrates how to break the looping mechanism of the following activities: <xref:System.Activities.Statements.DoWhile>, <xref:System.Activities.Statements.ForEach%601>, <xref:System.Activities.Statements.While>, and <xref:System.Activities.Statements.ParallelForEach%601>.</span></span>  
  
 <span data-ttu-id="06a3e-104">Isso é útil porque o Windows Workflow Foundation (WF) não inclui nenhuma atividade para interromper a execução desses loops.</span><span class="sxs-lookup"><span data-stu-id="06a3e-104">This is useful because Windows Workflow Foundation (WF) does not include any activity to break the execution of these loops.</span></span>  
  
## <a name="scenario"></a><span data-ttu-id="06a3e-105">Cenário</span><span class="sxs-lookup"><span data-stu-id="06a3e-105">Scenario</span></span>  
 <span data-ttu-id="06a3e-106">O exemplo localiza o primeiro fornecedor confiável de uma lista de fornecedores (instâncias da classe `Vendor` ).</span><span class="sxs-lookup"><span data-stu-id="06a3e-106">The sample finds the first reliable vendor from a list of vendors (instances of the `Vendor` class).</span></span> <span data-ttu-id="06a3e-107">Cada fornecedor tem `ID`, `Name` e um valor numérico de confiabilidade que determina como o fornecedor é seguro.</span><span class="sxs-lookup"><span data-stu-id="06a3e-107">Each vendor has an `ID`, a `Name` and a numeric reliability value that determines how dependable the vendor is.</span></span> <span data-ttu-id="06a3e-108">O exemplo cria uma atividade personalizado chamada `FindReliableVendor` que recebe dois parâmetros de entrada (uma lista de fornecedores e um valor mínimo de confiabilidade) e retorna o primeiro fornecedor de lista que corresponde aos critérios fornecidos.</span><span class="sxs-lookup"><span data-stu-id="06a3e-108">The sample creates a custom activity called `FindReliableVendor` that receives two input parameters (a list of vendors and a minimum reliability value) and returns the first vendor of the list that matches the supplied criteria.</span></span>  
  
## <a name="breaking-a-loop"></a><span data-ttu-id="06a3e-109">Quebrando um loop</span><span class="sxs-lookup"><span data-stu-id="06a3e-109">Breaking a Loop</span></span>  
 <span data-ttu-id="06a3e-110">Windows Workflow Foundation (WF) não inclui uma atividade para interromper um loop.</span><span class="sxs-lookup"><span data-stu-id="06a3e-110">Windows Workflow Foundation (WF) does not include an activity to break a loop.</span></span> <span data-ttu-id="06a3e-111">O exemplo de código a seguir realiza quebrar um loop usando uma atividade de <xref:System.Activities.Statements.If> e diversas variáveis.</span><span class="sxs-lookup"><span data-stu-id="06a3e-111">The code sample accomplishes breaking a loop by using an <xref:System.Activities.Statements.If> activity and several variables.</span></span> <span data-ttu-id="06a3e-112">No exemplo, a atividade de <xref:System.Activities.Statements.While> é interrompida uma vez que a variável de `reliableVendor` é atribuído um valor diferente `null`.</span><span class="sxs-lookup"><span data-stu-id="06a3e-112">In the sample, the <xref:System.Activities.Statements.While> activity is broken once the `reliableVendor` variable is assigned a value other than `null`.</span></span>  
  
 <span data-ttu-id="06a3e-113">O exemplo de código a seguir demonstra como dividir o exemplo um loop de quando.</span><span class="sxs-lookup"><span data-stu-id="06a3e-113">The following code example demonstrates how the sample breaks a while loop.</span></span>  
  
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
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="06a3e-114">Para usar este exemplo</span><span class="sxs-lookup"><span data-stu-id="06a3e-114">To use this sample</span></span>  
  
1.  <span data-ttu-id="06a3e-115">Usando [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], abra o arquivo de solução de EmulatingBreakInWhile.sln.</span><span class="sxs-lookup"><span data-stu-id="06a3e-115">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the EmulatingBreakInWhile.sln solution file.</span></span>  
  
2.  <span data-ttu-id="06a3e-116">Para criar a solução, pressione CTRL+SHIFT+B.</span><span class="sxs-lookup"><span data-stu-id="06a3e-116">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="06a3e-117">Para executar a solução, pressione CTRL+F5.</span><span class="sxs-lookup"><span data-stu-id="06a3e-117">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="06a3e-118">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="06a3e-118">The samples may already be installed on your machine.</span></span> <span data-ttu-id="06a3e-119">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="06a3e-119">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="06a3e-120">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="06a3e-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="06a3e-121">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="06a3e-121">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\EmulatingBreakInWhile`