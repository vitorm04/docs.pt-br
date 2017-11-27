---
title: IfElse com regras
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c4ad9bb2-9037-413a-8b14-59ed7b927a9e
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5cd0859db8071f9af130756fdc9b34726199be9a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ifelse-with-rules"></a><span data-ttu-id="ba96c-102">IfElse com regras</span><span class="sxs-lookup"><span data-stu-id="ba96c-102">IfElse With Rules</span></span>
<span data-ttu-id="ba96c-103">Este exemplo mostra o uso de uma condição de regra com uma atividade de <xref:System.Workflow.Activities.IfElseActivity> .</span><span class="sxs-lookup"><span data-stu-id="ba96c-103">This sample shows the use of a rule condition with an <xref:System.Workflow.Activities.IfElseActivity> activity.</span></span>  
  
 <span data-ttu-id="ba96c-104">O exemplo passa em um parâmetro de `OrderValue` host.</span><span class="sxs-lookup"><span data-stu-id="ba96c-104">The sample passes in an `OrderValue` parameter from the host.</span></span> <span data-ttu-id="ba96c-105">O valor do parâmetro é usado em uma condição de regra no primeiro ramificação de atividade de <xref:System.Workflow.Activities.IfElseActivity> .</span><span class="sxs-lookup"><span data-stu-id="ba96c-105">The value of the parameter is used in a rule condition on the first branch of the <xref:System.Workflow.Activities.IfElseActivity> activity.</span></span> <span data-ttu-id="ba96c-106">Se o valor for menor que 10.000, o primeiro branch que é executado e o <xref:System.Workflow.Activities.CodeActivity> atividade na ramificação primeiro imprime **obter aprovação do Gerenciador de** para o console.</span><span class="sxs-lookup"><span data-stu-id="ba96c-106">If the value is less than 10,000, the first branch executes, and the <xref:System.Workflow.Activities.CodeActivity> activity in the first branch prints **Get Manager Approval** to the console.</span></span> <span data-ttu-id="ba96c-107">Se o valor for maior que 10.000, o <xref:System.Workflow.Activities.CodeActivity> atividade na segunda ramificação executa e imprime **Obtenha vice-Presidente aprovação**.</span><span class="sxs-lookup"><span data-stu-id="ba96c-107">If the value is greater than 10,000, the <xref:System.Workflow.Activities.CodeActivity> activity in the second branch executes and prints **Get VP Approval**.</span></span>  
  
### <a name="to-build-the-sample"></a><span data-ttu-id="ba96c-108">Para criar o exemplo</span><span class="sxs-lookup"><span data-stu-id="ba96c-108">To build the sample</span></span>  
  
1.  <span data-ttu-id="ba96c-109">Abra a solução em [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ba96c-109">Open the solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="ba96c-110">Crie a solução. CTRL+SHIFT+B pressionando.</span><span class="sxs-lookup"><span data-stu-id="ba96c-110">Build the solution by pressing CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="ba96c-111">Executar a solução sem depuração pressionando CTRL + f5.</span><span class="sxs-lookup"><span data-stu-id="ba96c-111">Run the solution without debugging by pressing CTRL+F5.</span></span>  
  
### <a name="to-run-the-sample"></a><span data-ttu-id="ba96c-112">Para executar a amostra</span><span class="sxs-lookup"><span data-stu-id="ba96c-112">To run the sample</span></span>  
  
-   <span data-ttu-id="ba96c-113">Na janela do prompt de comando SDK, execute o arquivo .exe no IfElseWithRules \ bin \ debug (ou na pasta \ bin de IfElseWithRules para a versão do Visual Basic de exemplo), que está localizado abaixo da pasta principal para o exemplo.</span><span class="sxs-lookup"><span data-stu-id="ba96c-113">In the SDK Command Prompt window, run the .exe file in the IfElseWithRules\bin\debug folder (or the IfElseWithRules\bin folder for the Visual Basic version of the sample), which is located below the main folder for the sample.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ba96c-114">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="ba96c-114">The samples may already be installed on your computer.</span></span> <span data-ttu-id="ba96c-115">Verificar o seguinte diretório (padrão) antes de continuar:</span><span class="sxs-lookup"><span data-stu-id="ba96c-115">Check for the following (default) directory before continuing:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="ba96c-116">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="ba96c-116">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ba96c-117">Este exemplo está no seguinte diretório:</span><span class="sxs-lookup"><span data-stu-id="ba96c-117">This sample is located in the following directory:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Rules\IfElseWithRules`  
  
## <a name="see-also"></a><span data-ttu-id="ba96c-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ba96c-118">See Also</span></span>  
 <xref:System.Workflow.Activities.Rules>  
 <xref:System.Workflow.Activities.IfElseActivity>  
 <xref:System.Workflow.Activities.CodeActivity>  
 <xref:System.Workflow.Activities.Rules.RuleDefinitions>
