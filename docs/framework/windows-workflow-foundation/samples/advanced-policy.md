---
title: "Diretiva avançada"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 75a22c88-5e54-4ae8-84cb-fbb22a612f0a
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c83f4167ce1947b10f97e0cab5b5ddd2f8e00c76
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="advanced-policy"></a><span data-ttu-id="81038-102">Diretiva avançada</span><span class="sxs-lookup"><span data-stu-id="81038-102">Advanced Policy</span></span>
<span data-ttu-id="81038-103">Este exemplo amplia o exemplo simples de política.</span><span class="sxs-lookup"><span data-stu-id="81038-103">This sample extends the Simple Policy sample.</span></span> <span data-ttu-id="81038-104">Além das regras residenciais de desconto e de desconto de negócio de exemplo simples de política, várias regras novos foram adicionadas.</span><span class="sxs-lookup"><span data-stu-id="81038-104">In addition to the residential discount and business discount rules from the Simple Policy example, several new rules have been added.</span></span>  
  
 <span data-ttu-id="81038-105">Uma regra valioso é adicionada, que fornece desconto maior de pedidos importantes.</span><span class="sxs-lookup"><span data-stu-id="81038-105">A high-value rule is added, which provides a bigger discount for high-value orders.</span></span> <span data-ttu-id="81038-106">Recebe um valor de prioridade menor do que as duas regras anteriores de modo que substitui o campo de desconto e tem precedência sobre as regras residenciais e comerciais de desconto.</span><span class="sxs-lookup"><span data-stu-id="81038-106">It is given a priority value less than the previous two rules so that it will overwrite the discount field and take precedence over both the residential and business discount rules.</span></span>  
  
 <span data-ttu-id="81038-107">Uma regra do total de cálculo também é adicionada, que compute o total com base no nível de desconto.</span><span class="sxs-lookup"><span data-stu-id="81038-107">A calculate total rule is also added, which computes the total based on the discount level.</span></span> <span data-ttu-id="81038-108">Mostra como referenciar um método definido na atividade de fluxo de trabalho, bem como usar outras ações.</span><span class="sxs-lookup"><span data-stu-id="81038-108">It shows how to reference a method defined on the workflow activity, as well as how to use else actions.</span></span> <span data-ttu-id="81038-109">Essa regra também demonstra encadeamento o comportamento desde que será avaliado a qualquer momento as alterações do campo de desconto.</span><span class="sxs-lookup"><span data-stu-id="81038-109">This rule also demonstrates chaining behavior since it will be evaluated anytime the discount field changes.</span></span> <span data-ttu-id="81038-110">Além disso, a atribuição do método é mostrada com o RuleWriteAttribute no método de CalculateTotal.</span><span class="sxs-lookup"><span data-stu-id="81038-110">Furthermore, method attributing is shown with the RuleWriteAttribute on the CalculateTotal method.</span></span> <span data-ttu-id="81038-111">Isso faz com que as regras afetados (ErrorTotalRule) a ser reavaliadas sempre que o método é executado.</span><span class="sxs-lookup"><span data-stu-id="81038-111">This causes impacted rules (ErrorTotalRule) to be re-evaluated whenever the method gets executed.</span></span>  
  
 <span data-ttu-id="81038-112">A regra mais recente é adicionada uma que detecta erros (neste caso, total menor que 0).</span><span class="sxs-lookup"><span data-stu-id="81038-112">The last rule added is one that detects errors (in this case, Total less than 0).</span></span> <span data-ttu-id="81038-113">Se isso ocorre, a execução de política é interrompida.</span><span class="sxs-lookup"><span data-stu-id="81038-113">If this occurs, the policy execution is halted.</span></span>  
  
 <span data-ttu-id="81038-114">Finalmente, chamadas de `Console.Writeline` são adicionados como ações a cada regra fornecer mais visibilidade em execução de regra, para mostrar que também é possível acessar métodos estáticos em tipos referenciados.</span><span class="sxs-lookup"><span data-stu-id="81038-114">Finally, `Console.Writeline` calls are added as actions to each rule to provide more visibility into rule execution, while also showing that it is possible to access static methods on referenced types.</span></span> <span data-ttu-id="81038-115">Você também pode usar o rastreamento para obter a visibilidade nas regras que são executadas.</span><span class="sxs-lookup"><span data-stu-id="81038-115">You could also use tracking to get visibility into the rules that are executed.</span></span>  
  
 <span data-ttu-id="81038-116">Regras usadas nesse exemplo são:</span><span class="sxs-lookup"><span data-stu-id="81038-116">The rules used in this sample are:</span></span>  
  
 <span data-ttu-id="81038-117">**ResidentialDiscountRule:**</span><span class="sxs-lookup"><span data-stu-id="81038-117">**ResidentialDiscountRule:**</span></span>  
  
 <span data-ttu-id="81038-118">SE OrderValue > 500 E CustomerType = residencial</span><span class="sxs-lookup"><span data-stu-id="81038-118">IF OrderValue > 500 AND CustomerType = Residential</span></span>  
  
 <span data-ttu-id="81038-119">Em seguida, desconto = % 5</span><span class="sxs-lookup"><span data-stu-id="81038-119">THEN Discount = 5%</span></span>  
  
 <span data-ttu-id="81038-120">**BusinessDiscountRule:**</span><span class="sxs-lookup"><span data-stu-id="81038-120">**BusinessDiscountRule:**</span></span>  
  
 <span data-ttu-id="81038-121">SE OrderValue > 10000 E CustomerType = business</span><span class="sxs-lookup"><span data-stu-id="81038-121">IF OrderValue > 10000 AND CustomerType = Business</span></span>  
  
 <span data-ttu-id="81038-122">Em seguida, desconto = 10%</span><span class="sxs-lookup"><span data-stu-id="81038-122">THEN Discount = 10%</span></span>  
  
 <span data-ttu-id="81038-123">**HighValueDiscountRule:**</span><span class="sxs-lookup"><span data-stu-id="81038-123">**HighValueDiscountRule:**</span></span>  
  
 <span data-ttu-id="81038-124">SE OrderValue > 20000</span><span class="sxs-lookup"><span data-stu-id="81038-124">IF OrderValue > 20000</span></span>  
  
 <span data-ttu-id="81038-125">ENTÃO desconto = 15%</span><span class="sxs-lookup"><span data-stu-id="81038-125">THEN Discount = 15%</span></span>  
  
 <span data-ttu-id="81038-126">**TotalRule:**</span><span class="sxs-lookup"><span data-stu-id="81038-126">**TotalRule:**</span></span>  
  
 <span data-ttu-id="81038-127">SE desconto > 0</span><span class="sxs-lookup"><span data-stu-id="81038-127">IF Discount > 0</span></span>  
  
 <span data-ttu-id="81038-128">ENTÃO CalculateTotal (OrderValue, desconto)</span><span class="sxs-lookup"><span data-stu-id="81038-128">THEN CalculateTotal(OrderValue, Discount)</span></span>  
  
 <span data-ttu-id="81038-129">Total OUTRO = OrderValue</span><span class="sxs-lookup"><span data-stu-id="81038-129">ELSE Total = OrderValue</span></span>  
  
 <span data-ttu-id="81038-130">**ErrorTotalRule:**</span><span class="sxs-lookup"><span data-stu-id="81038-130">**ErrorTotalRule:**</span></span>  
  
 <span data-ttu-id="81038-131">Se Total \< 0</span><span class="sxs-lookup"><span data-stu-id="81038-131">IF Total \< 0</span></span>  
  
 <span data-ttu-id="81038-132">ENTÃO erro = “ErrorTotalRule acionado”; Stop</span><span class="sxs-lookup"><span data-stu-id="81038-132">THEN Error = "Fired ErrorTotalRule"; Halt</span></span>  
  
 <span data-ttu-id="81038-133">A avaliação e a execução da regra também podem ser consideradas com o rastreamento e o rastreamento.</span><span class="sxs-lookup"><span data-stu-id="81038-133">Rule evaluation and execution can also be seen through tracing and tracking.</span></span>  
  
### <a name="to-build-the-sample"></a><span data-ttu-id="81038-134">Para criar o exemplo</span><span class="sxs-lookup"><span data-stu-id="81038-134">To build the sample</span></span>  
  
1.  <span data-ttu-id="81038-135">Abra a solução em [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="81038-135">Open the solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="81038-136">Crie a solução. CTRL+SHIFT+B pressionando.</span><span class="sxs-lookup"><span data-stu-id="81038-136">Build the solution by pressing CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="81038-137">Executar a solução sem depuração pressionando CTRL + f5.</span><span class="sxs-lookup"><span data-stu-id="81038-137">Run the solution without debugging by pressing CTRL+F5.</span></span>  
  
### <a name="to-run-the-sample"></a><span data-ttu-id="81038-138">Para executar a amostra</span><span class="sxs-lookup"><span data-stu-id="81038-138">To run the sample</span></span>  
  
-   <span data-ttu-id="81038-139">Na janela do prompt de comando SDK, execute o arquivo .exe no AdvancedPolicy \ bin \ debug (ou na pasta \ bin de AdvancedPolicy para a versão do Visual Basic de exemplo), que está localizado abaixo da pasta principal para o exemplo.</span><span class="sxs-lookup"><span data-stu-id="81038-139">In the SDK Command Prompt window, run the .exe file in the AdvancedPolicy\bin\debug folder (or the AdvancedPolicy \bin folder for the Visual Basic version of the sample), which is located below the main folder for the sample.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="81038-140">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="81038-140">The samples may already be installed on your computer.</span></span> <span data-ttu-id="81038-141">Verificar o seguinte diretório (padrão) antes de continuar:</span><span class="sxs-lookup"><span data-stu-id="81038-141">Check for the following (default) directory before continuing:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="81038-142">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="81038-142">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="81038-143">Este exemplo está no seguinte diretório:</span><span class="sxs-lookup"><span data-stu-id="81038-143">This sample is located in the following directory:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Rules\Policy\AdvancedPolicy`  
  
## <a name="see-also"></a><span data-ttu-id="81038-144">Consulte também</span><span class="sxs-lookup"><span data-stu-id="81038-144">See Also</span></span>  
 <xref:System.Workflow.Activities.Rules.RuleSet>  
 <xref:System.Workflow.Activities.PolicyActivity>  
 [<span data-ttu-id="81038-145">Política simples</span><span class="sxs-lookup"><span data-stu-id="81038-145">Simple Policy</span></span>](../../../../docs/framework/windows-workflow-foundation/samples/simple-policy.md)
