---
title: Grupo de atividade condicionado
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f76ef924-34ce-48ae-8c8d-48faf9697754
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e0df4ddc6f2cc5404c8153b30df66cda41487691
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="conditioned-activity-group"></a><span data-ttu-id="1a1c6-102">Grupo de atividade condicionado</span><span class="sxs-lookup"><span data-stu-id="1a1c6-102">Conditioned Activity Group</span></span>
<span data-ttu-id="1a1c6-103">O exemplo demonstra um aplicativo do registro do traço.</span><span class="sxs-lookup"><span data-stu-id="1a1c6-103">The sample demonstrates a travel booking application.</span></span> <span data-ttu-id="1a1c6-104"><xref:System.Workflow.Activities.ConditionedActivityGroup> (CAG) tem duas atividades de código a seguir: uma atividade do carro e uma atividade de linha sobrecarga.</span><span class="sxs-lookup"><span data-stu-id="1a1c6-104">The <xref:System.Workflow.Activities.ConditionedActivityGroup> (CAG) has two code activities: a Car activity and an Airline activity.</span></span> <span data-ttu-id="1a1c6-105">No construtor de `SimpleCAGWorkflow` , um objeto de ArrayList “travelNeedType” é preenchido com os tipos de registros de traço necessários.</span><span class="sxs-lookup"><span data-stu-id="1a1c6-105">In the `SimpleCAGWorkflow` constructor, a "travelNeedType" ArrayList object is populated with the types of travel bookings that are required.</span></span> <span data-ttu-id="1a1c6-106">Comentando por uma ou ambas as instruções de `travelNeeds.Add` , você altera o comportamento de CAG de acordo.</span><span class="sxs-lookup"><span data-stu-id="1a1c6-106">By commenting out one or both of the `travelNeeds.Add` statements, you modify the CAG behavior accordingly.</span></span> <span data-ttu-id="1a1c6-107">As atividades de carro e linha sobrecarga têm sua condição de <xref:System.Workflow.Activities.ConditionedActivityGroup.WhenConditionProperty> preenchida com <xref:System.Workflow.Activities.CodeCondition>.</span><span class="sxs-lookup"><span data-stu-id="1a1c6-107">Both the Car and Airline activities have their <xref:System.Workflow.Activities.ConditionedActivityGroup.WhenConditionProperty> condition populated with a <xref:System.Workflow.Activities.CodeCondition>.</span></span> <span data-ttu-id="1a1c6-108">Atividade de carro executa somente se a coleção de `travelNeeds` tem uma entrada de `TravelNeeds.Car` , e a atividade de linha sobrecarga executa somente se a coleção de `travelNeeds` tem uma entrada de `TravelNeeds.Airline` .</span><span class="sxs-lookup"><span data-stu-id="1a1c6-108">The Car activity executes only if the `travelNeeds` collection has a `TravelNeeds.Car` entry, and the Airline activity executes only if the `travelNeeds` collection has a `TravelNeeds.Airline` entry.</span></span>  
  
 <span data-ttu-id="1a1c6-109">A execução de cada atividade remove a entrada correspondente da coleção.</span><span class="sxs-lookup"><span data-stu-id="1a1c6-109">The execution of each activity removes the corresponding entry from the collection.</span></span> <span data-ttu-id="1a1c6-110">A condição de <xref:System.Workflow.Activities.ConditionedActivityGroup.UntilCondition%2A> de opção especifica que o CAG deve sair quando nenhum filho está executando ou está pronto para a execução (com base nas condições de <xref:System.Workflow.Activities.ConditionedActivityGroup.WhenConditionProperty> ).</span><span class="sxs-lookup"><span data-stu-id="1a1c6-110">The default <xref:System.Workflow.Activities.ConditionedActivityGroup.UntilCondition%2A> condition specifies that the CAG should exit when no children are executing or are ready for execution (based on their <xref:System.Workflow.Activities.ConditionedActivityGroup.WhenConditionProperty> conditions).</span></span> <span data-ttu-id="1a1c6-111">Nesse exemplo, isso significa que o CAG sai quando a coleção de `travelNeeds` está vazia.</span><span class="sxs-lookup"><span data-stu-id="1a1c6-111">In this sample, this means that the CAG exits when the `travelNeeds` collection is empty.</span></span>  
  
### <a name="to-build-the-sample"></a><span data-ttu-id="1a1c6-112">Para criar o exemplo</span><span class="sxs-lookup"><span data-stu-id="1a1c6-112">To build the sample</span></span>  
  
1.  <span data-ttu-id="1a1c6-113">Abra a solução em [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1a1c6-113">Open the solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="1a1c6-114">Crie a solução. CTRL+SHIFT+B pressionando.</span><span class="sxs-lookup"><span data-stu-id="1a1c6-114">Build the solution by pressing CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="1a1c6-115">Executar a solução sem depuração pressionando CTRL + f5.</span><span class="sxs-lookup"><span data-stu-id="1a1c6-115">Run the solution without debugging by pressing CTRL+F5.</span></span>  
  
### <a name="to-run-the-sample"></a><span data-ttu-id="1a1c6-116">Para executar a amostra</span><span class="sxs-lookup"><span data-stu-id="1a1c6-116">To run the sample</span></span>  
  
-   <span data-ttu-id="1a1c6-117">Na janela do prompt de comando SDK, execute o arquivo .exe no SimpleCAG \ bin \ debug (ou na pasta \ bin de SimpleCAG para a versão do Visual Basic de exemplo), que está localizado abaixo da pasta principal para o exemplo.</span><span class="sxs-lookup"><span data-stu-id="1a1c6-117">In the SDK Command Prompt window, run the .exe file in the SimpleCAG\bin\debug folder (or the SimpleCAG\bin folder for the Visual Basic version of the sample), which is located below the main folder for the sample.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="1a1c6-118">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="1a1c6-118">The samples may already be installed on your computer.</span></span> <span data-ttu-id="1a1c6-119">Verificar o seguinte diretório (padrão) antes de continuar:</span><span class="sxs-lookup"><span data-stu-id="1a1c6-119">Check for the following (default) directory before continuing:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="1a1c6-120">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="1a1c6-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="1a1c6-121">Este exemplo está no seguinte diretório:</span><span class="sxs-lookup"><span data-stu-id="1a1c6-121">This sample is located in the following directory:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Rules\SimpleCAG`  
  
## <a name="see-also"></a><span data-ttu-id="1a1c6-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1a1c6-122">See Also</span></span>  
 <xref:System.Workflow.Activities.ConditionedActivityGroup>  
 <xref:System.Workflow.Activities.ConditionedActivityGroup.WhenConditionProperty>  
 <xref:System.Workflow.Activities.CodeCondition>  
 <xref:System.Workflow.Activities.ConditionedActivityGroup.UntilCondition%2A>
