---
title: Diretiva avançada
ms.date: 03/30/2017
ms.assetid: 75a22c88-5e54-4ae8-84cb-fbb22a612f0a
ms.openlocfilehash: becdc28affd877239474d6f0f007a480297bccb8
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44083784"
---
# <a name="advanced-policy"></a><span data-ttu-id="d7dd6-102">Diretiva avançada</span><span class="sxs-lookup"><span data-stu-id="d7dd6-102">Advanced Policy</span></span>
<span data-ttu-id="d7dd6-103">Este exemplo amplia o exemplo simples de política.</span><span class="sxs-lookup"><span data-stu-id="d7dd6-103">This sample extends the Simple Policy sample.</span></span> <span data-ttu-id="d7dd6-104">Além das regras residenciais de desconto e de desconto de negócio de exemplo simples de política, várias regras novos foram adicionadas.</span><span class="sxs-lookup"><span data-stu-id="d7dd6-104">In addition to the residential discount and business discount rules from the Simple Policy example, several new rules have been added.</span></span>  
  
 <span data-ttu-id="d7dd6-105">Uma regra valioso é adicionada, que fornece desconto maior de pedidos importantes.</span><span class="sxs-lookup"><span data-stu-id="d7dd6-105">A high-value rule is added, which provides a bigger discount for high-value orders.</span></span> <span data-ttu-id="d7dd6-106">Recebe um valor de prioridade menor do que as duas regras anteriores de modo que substitui o campo de desconto e tem precedência sobre as regras residenciais e comerciais de desconto.</span><span class="sxs-lookup"><span data-stu-id="d7dd6-106">It is given a priority value less than the previous two rules so that it will overwrite the discount field and take precedence over both the residential and business discount rules.</span></span>  
  
 <span data-ttu-id="d7dd6-107">Uma regra do total de cálculo também é adicionada, que compute o total com base no nível de desconto.</span><span class="sxs-lookup"><span data-stu-id="d7dd6-107">A calculate total rule is also added, which computes the total based on the discount level.</span></span> <span data-ttu-id="d7dd6-108">Mostra como referenciar um método definido na atividade de fluxo de trabalho, bem como usar outras ações.</span><span class="sxs-lookup"><span data-stu-id="d7dd6-108">It shows how to reference a method defined on the workflow activity, as well as how to use else actions.</span></span> <span data-ttu-id="d7dd6-109">Essa regra também demonstra encadeamento o comportamento desde que será avaliado a qualquer momento as alterações do campo de desconto.</span><span class="sxs-lookup"><span data-stu-id="d7dd6-109">This rule also demonstrates chaining behavior since it will be evaluated anytime the discount field changes.</span></span> <span data-ttu-id="d7dd6-110">Além disso, a atribuição do método é mostrada com o RuleWriteAttribute no método de CalculateTotal.</span><span class="sxs-lookup"><span data-stu-id="d7dd6-110">Furthermore, method attributing is shown with the RuleWriteAttribute on the CalculateTotal method.</span></span> <span data-ttu-id="d7dd6-111">Isso faz com que as regras afetados (ErrorTotalRule) a ser reavaliadas sempre que o método é executado.</span><span class="sxs-lookup"><span data-stu-id="d7dd6-111">This causes impacted rules (ErrorTotalRule) to be re-evaluated whenever the method gets executed.</span></span>  
  
 <span data-ttu-id="d7dd6-112">A regra mais recente é adicionada uma que detecta erros (neste caso, total menor que 0).</span><span class="sxs-lookup"><span data-stu-id="d7dd6-112">The last rule added is one that detects errors (in this case, Total less than 0).</span></span> <span data-ttu-id="d7dd6-113">Se isso ocorre, a execução de política é interrompida.</span><span class="sxs-lookup"><span data-stu-id="d7dd6-113">If this occurs, the policy execution is halted.</span></span>  
  
 <span data-ttu-id="d7dd6-114">Finalmente, chamadas de `Console.Writeline` são adicionados como ações a cada regra fornecer mais visibilidade em execução de regra, para mostrar que também é possível acessar métodos estáticos em tipos referenciados.</span><span class="sxs-lookup"><span data-stu-id="d7dd6-114">Finally, `Console.Writeline` calls are added as actions to each rule to provide more visibility into rule execution, while also showing that it is possible to access static methods on referenced types.</span></span> <span data-ttu-id="d7dd6-115">Você também pode usar o rastreamento para obter a visibilidade nas regras que são executadas.</span><span class="sxs-lookup"><span data-stu-id="d7dd6-115">You could also use tracking to get visibility into the rules that are executed.</span></span>  
  
 <span data-ttu-id="d7dd6-116">Regras usadas nesse exemplo são:</span><span class="sxs-lookup"><span data-stu-id="d7dd6-116">The rules used in this sample are:</span></span>  
  
 <span data-ttu-id="d7dd6-117">**ResidentialDiscountRule:**</span><span class="sxs-lookup"><span data-stu-id="d7dd6-117">**ResidentialDiscountRule:**</span></span>  
  
 <span data-ttu-id="d7dd6-118">SE OrderValue > 500 E CustomerType = residencial</span><span class="sxs-lookup"><span data-stu-id="d7dd6-118">IF OrderValue > 500 AND CustomerType = Residential</span></span>  
  
 <span data-ttu-id="d7dd6-119">ENTÃO desconto = % 5</span><span class="sxs-lookup"><span data-stu-id="d7dd6-119">THEN Discount = 5%</span></span>  
  
 <span data-ttu-id="d7dd6-120">**BusinessDiscountRule:**</span><span class="sxs-lookup"><span data-stu-id="d7dd6-120">**BusinessDiscountRule:**</span></span>  
  
 <span data-ttu-id="d7dd6-121">SE OrderValue > 10000 E CustomerType = business</span><span class="sxs-lookup"><span data-stu-id="d7dd6-121">IF OrderValue > 10000 AND CustomerType = Business</span></span>  
  
 <span data-ttu-id="d7dd6-122">ENTÃO desconto = 10%</span><span class="sxs-lookup"><span data-stu-id="d7dd6-122">THEN Discount = 10%</span></span>  
  
 <span data-ttu-id="d7dd6-123">**HighValueDiscountRule:**</span><span class="sxs-lookup"><span data-stu-id="d7dd6-123">**HighValueDiscountRule:**</span></span>  
  
 <span data-ttu-id="d7dd6-124">SE OrderValue > 20000</span><span class="sxs-lookup"><span data-stu-id="d7dd6-124">IF OrderValue > 20000</span></span>  
  
 <span data-ttu-id="d7dd6-125">ENTÃO desconto = 15%</span><span class="sxs-lookup"><span data-stu-id="d7dd6-125">THEN Discount = 15%</span></span>  
  
 <span data-ttu-id="d7dd6-126">**TotalRule:**</span><span class="sxs-lookup"><span data-stu-id="d7dd6-126">**TotalRule:**</span></span>  
  
 <span data-ttu-id="d7dd6-127">SE desconto > 0</span><span class="sxs-lookup"><span data-stu-id="d7dd6-127">IF Discount > 0</span></span>  
  
 <span data-ttu-id="d7dd6-128">ENTÃO CalculateTotal (OrderValue, desconto)</span><span class="sxs-lookup"><span data-stu-id="d7dd6-128">THEN CalculateTotal(OrderValue, Discount)</span></span>  
  
 <span data-ttu-id="d7dd6-129">Total OUTRO = OrderValue</span><span class="sxs-lookup"><span data-stu-id="d7dd6-129">ELSE Total = OrderValue</span></span>  
  
 <span data-ttu-id="d7dd6-130">**ErrorTotalRule:**</span><span class="sxs-lookup"><span data-stu-id="d7dd6-130">**ErrorTotalRule:**</span></span>  
  
 <span data-ttu-id="d7dd6-131">Se Total \< 0</span><span class="sxs-lookup"><span data-stu-id="d7dd6-131">IF Total \< 0</span></span>  
  
 <span data-ttu-id="d7dd6-132">ENTÃO erro = “ErrorTotalRule acionado”; Stop</span><span class="sxs-lookup"><span data-stu-id="d7dd6-132">THEN Error = "Fired ErrorTotalRule"; Halt</span></span>  
  
 <span data-ttu-id="d7dd6-133">A avaliação e a execução da regra também podem ser consideradas com o rastreamento e o rastreamento.</span><span class="sxs-lookup"><span data-stu-id="d7dd6-133">Rule evaluation and execution can also be seen through tracing and tracking.</span></span>  
  
### <a name="to-build-the-sample"></a><span data-ttu-id="d7dd6-134">Para criar o exemplo</span><span class="sxs-lookup"><span data-stu-id="d7dd6-134">To build the sample</span></span>  
  
1.  <span data-ttu-id="d7dd6-135">Abra a solução em [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d7dd6-135">Open the solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="d7dd6-136">Crie a solução. CTRL+SHIFT+B pressionando.</span><span class="sxs-lookup"><span data-stu-id="d7dd6-136">Build the solution by pressing CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="d7dd6-137">Executar a solução sem depuração pressionando CTRL + f5.</span><span class="sxs-lookup"><span data-stu-id="d7dd6-137">Run the solution without debugging by pressing CTRL+F5.</span></span>  
  
### <a name="to-run-the-sample"></a><span data-ttu-id="d7dd6-138">Para executar a amostra</span><span class="sxs-lookup"><span data-stu-id="d7dd6-138">To run the sample</span></span>  
  
-   <span data-ttu-id="d7dd6-139">Na janela do prompt de comando SDK, execute o arquivo .exe no AdvancedPolicy \ bin \ debug (ou na pasta \ bin de AdvancedPolicy para a versão do Visual Basic de exemplo), que está localizado abaixo da pasta principal para o exemplo.</span><span class="sxs-lookup"><span data-stu-id="d7dd6-139">In the SDK Command Prompt window, run the .exe file in the AdvancedPolicy\bin\debug folder (or the AdvancedPolicy \bin folder for the Visual Basic version of the sample), which is located below the main folder for the sample.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d7dd6-140">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="d7dd6-140">The samples may already be installed on your computer.</span></span> <span data-ttu-id="d7dd6-141">Verificar o seguinte diretório (padrão) antes de continuar:</span><span class="sxs-lookup"><span data-stu-id="d7dd6-141">Check for the following (default) directory before continuing:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="d7dd6-142">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="d7dd6-142">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d7dd6-143">Este exemplo está no seguinte diretório:</span><span class="sxs-lookup"><span data-stu-id="d7dd6-143">This sample is located in the following directory:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Rules\Policy\AdvancedPolicy`  
  
## <a name="see-also"></a><span data-ttu-id="d7dd6-144">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d7dd6-144">See Also</span></span>  
 <xref:System.Workflow.Activities.Rules.RuleSet>  
 <xref:System.Workflow.Activities.PolicyActivity>  
 [<span data-ttu-id="d7dd6-145">Política simples</span><span class="sxs-lookup"><span data-stu-id="d7dd6-145">Simple Policy</span></span>](../../../../docs/framework/windows-workflow-foundation/samples/simple-policy.md)
