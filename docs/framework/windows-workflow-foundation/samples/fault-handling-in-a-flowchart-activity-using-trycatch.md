---
title: Tratamento de falha em uma atividade do fluxograma usando TryCatch
ms.date: 03/30/2017
ms.assetid: 50922964-bfe0-4ba8-9422-0e7220d514fd
ms.openlocfilehash: df3d93087744ce0fba597f5c9f1d2da4b71a50dd
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48779849"
---
# <a name="fault-handling-in-a-flowchart-activity-using-trycatch"></a><span data-ttu-id="b0e86-102">Tratamento de falha em uma atividade do fluxograma usando TryCatch</span><span class="sxs-lookup"><span data-stu-id="b0e86-102">Fault Handling in a Flowchart Activity Using TryCatch</span></span>
<span data-ttu-id="b0e86-103">Este exemplo mostra como a atividade de <xref:System.Activities.Statements.TryCatch> pode ser usada dentro de uma atividade complexa de fluxo de controle.</span><span class="sxs-lookup"><span data-stu-id="b0e86-103">This sample shows how the <xref:System.Activities.Statements.TryCatch> activity can be used within a complex control flow activity.</span></span>

 <span data-ttu-id="b0e86-104">Nesse exemplo, um código da promoção e um número de filhos são passados como variáveis a uma atividade de <xref:System.Activities.Statements.Flowchart> que calcula desconto com base nas fórmulas que correspondem ao código da promoção.</span><span class="sxs-lookup"><span data-stu-id="b0e86-104">In this sample, a promotion code and number of children are passed as variables to a <xref:System.Activities.Statements.Flowchart> activity that calculates a discount based on formulae that correspond to the promotion code.</span></span> <span data-ttu-id="b0e86-105">O exemplo inclui versões imperativas do designer de código e de fluxo de trabalho de exemplo.</span><span class="sxs-lookup"><span data-stu-id="b0e86-105">The sample includes imperative code and workflow designer versions of the sample.</span></span>

 <span data-ttu-id="b0e86-106">A tabela a seguir detalha as variáveis para atividades de `CreateFlowchartWithFaults` .</span><span class="sxs-lookup"><span data-stu-id="b0e86-106">The following table details the variables for the `CreateFlowchartWithFaults` activity.</span></span>

|<span data-ttu-id="b0e86-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b0e86-107">Parameters</span></span>|<span data-ttu-id="b0e86-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="b0e86-108">Description</span></span>|
|----------------|-----------------|
|<span data-ttu-id="b0e86-109">promoCode</span><span class="sxs-lookup"><span data-stu-id="b0e86-109">promoCode</span></span>|<span data-ttu-id="b0e86-110">O código da promoção.</span><span class="sxs-lookup"><span data-stu-id="b0e86-110">The promotion code.</span></span> <span data-ttu-id="b0e86-111">Tipo: String</span><span class="sxs-lookup"><span data-stu-id="b0e86-111">Type: String</span></span><br /><br /> <span data-ttu-id="b0e86-112">Os valores possíveis com descrição entre parênteses:</span><span class="sxs-lookup"><span data-stu-id="b0e86-112">The possible values with description in parentheses:</span></span><br /><br /> <span data-ttu-id="b0e86-113">-Single (único)</span><span class="sxs-lookup"><span data-stu-id="b0e86-113">-   Single (Single)</span></span><br /><span data-ttu-id="b0e86-114">-MNK (casado sem crianças.)</span><span class="sxs-lookup"><span data-stu-id="b0e86-114">-   MNK (Married with no kids.)</span></span><br /><span data-ttu-id="b0e86-115">-MWK (casado com crianças.)</span><span class="sxs-lookup"><span data-stu-id="b0e86-115">-   MWK (Married with kids.)</span></span>|
|<span data-ttu-id="b0e86-116">numKids</span><span class="sxs-lookup"><span data-stu-id="b0e86-116">numKids</span></span>|<span data-ttu-id="b0e86-117">O número de filho.</span><span class="sxs-lookup"><span data-stu-id="b0e86-117">The number of children.</span></span> <span data-ttu-id="b0e86-118">Tipo: int</span><span class="sxs-lookup"><span data-stu-id="b0e86-118">Type: int</span></span>|

 <span data-ttu-id="b0e86-119">A atividade de `CreateFlowchartWithFaults` usa uma atividade de <xref:System.Activities.Statements.FlowSwitch%601> que alterna no argumento de `promoCode` e calculem o desconto usando a fórmula seguir.</span><span class="sxs-lookup"><span data-stu-id="b0e86-119">The `CreateFlowchartWithFaults` activity uses a <xref:System.Activities.Statements.FlowSwitch%601> activity that switches on the `promoCode` argument and calculates the discount using the following formula.</span></span>

|<span data-ttu-id="b0e86-120">Valor de `promoCode`</span><span class="sxs-lookup"><span data-stu-id="b0e86-120">Value of `promoCode`</span></span>|<span data-ttu-id="b0e86-121">Desconto (%)</span><span class="sxs-lookup"><span data-stu-id="b0e86-121">Discount (%)</span></span>|
|--------------------------|--------------------|
|<span data-ttu-id="b0e86-122">Simples</span><span class="sxs-lookup"><span data-stu-id="b0e86-122">Single</span></span>|<span data-ttu-id="b0e86-123">10</span><span class="sxs-lookup"><span data-stu-id="b0e86-123">10</span></span>|
|<span data-ttu-id="b0e86-124">MNK</span><span class="sxs-lookup"><span data-stu-id="b0e86-124">MNK</span></span>|<span data-ttu-id="b0e86-125">15</span><span class="sxs-lookup"><span data-stu-id="b0e86-125">15</span></span>|
|<span data-ttu-id="b0e86-126">MWK</span><span class="sxs-lookup"><span data-stu-id="b0e86-126">MWK</span></span>|<span data-ttu-id="b0e86-127">15 + (1 – 1 /`numberOfKids`)\*10 **Observação:** potencialmente, este cálculo pode lançar um <xref:System.DivideByZeroException>.</span><span class="sxs-lookup"><span data-stu-id="b0e86-127">15 + (1 – 1/`numberOfKids`)\*10 **Note:**  Potentially, this calculation can throw a <xref:System.DivideByZeroException>.</span></span> <span data-ttu-id="b0e86-128">Assim, o cálculo de desconto é empacotado em uma atividade de <xref:System.Activities.Statements.TryCatch> que captura a exceção de <xref:System.DivideByZeroException> e defina o desconto a zero.</span><span class="sxs-lookup"><span data-stu-id="b0e86-128">So, the discount calculation is wrapped in a <xref:System.Activities.Statements.TryCatch> activity that catches the <xref:System.DivideByZeroException> exception and sets the discount to zero.</span></span>|

#### <a name="to-use-this-sample"></a><span data-ttu-id="b0e86-129">Para usar este exemplo</span><span class="sxs-lookup"><span data-stu-id="b0e86-129">To use this sample</span></span>

1.  <span data-ttu-id="b0e86-130">Usando o Visual Studio 2010, abra o arquivo de solução de Flowchartwithfaulthandling.</span><span class="sxs-lookup"><span data-stu-id="b0e86-130">Using Visual Studio 2010, open the FlowchartWithFaultHandling.sln solution file.</span></span>

2.  <span data-ttu-id="b0e86-131">Para criar a solução, pressione CTRL+SHIFT+B.</span><span class="sxs-lookup"><span data-stu-id="b0e86-131">To build the solution, press CTRL+SHIFT+B.</span></span>

3.  <span data-ttu-id="b0e86-132">Para executar a solução, pressione F5.</span><span class="sxs-lookup"><span data-stu-id="b0e86-132">To run the solution, press F5.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="b0e86-133">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="b0e86-133">The samples may already be installed on your computer.</span></span> <span data-ttu-id="b0e86-134">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="b0e86-134">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="b0e86-135">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="b0e86-135">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b0e86-136">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="b0e86-136">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\FlowChartWithFaultHandling`  
  
## <a name="see-also"></a><span data-ttu-id="b0e86-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b0e86-137">See Also</span></span>  
 [<span data-ttu-id="b0e86-138">Fluxos de trabalho de fluxograma</span><span class="sxs-lookup"><span data-stu-id="b0e86-138">Flowchart Workflows</span></span>](../../../../docs/framework/windows-workflow-foundation/flowchart-workflows.md)  
 [<span data-ttu-id="b0e86-139">Exceções</span><span class="sxs-lookup"><span data-stu-id="b0e86-139">Exceptions</span></span>](../../../../docs/framework/windows-workflow-foundation/exceptions.md)
