---
title: "Determinando a duração da execução de fluxo de trabalho usando rastreamento"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f04ad0fd-edc7-4cbc-8979-356f2a1131c4
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f2687d045db28974e99b2f2b6a3222924a520720
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="determining-workflow-execution-duration-using-tracing"></a><span data-ttu-id="11ac5-102">Determinando a duração da execução de fluxo de trabalho usando rastreamento</span><span class="sxs-lookup"><span data-stu-id="11ac5-102">Determining Workflow Execution Duration Using Tracing</span></span>
<span data-ttu-id="11ac5-103">Este tópico demonstra como determinar o tempo necessário para que um fluxo de trabalho com êxito concluído, são hospedado é executado usando o rastreamento de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="11ac5-103">This topic demonstrates how to determine the time it takes for a successfully completed, self-hosted workflow to execute by using workflow tracing.</span></span>  
  
### <a name="to-determine-workflow-application-execution-duration-by-using-workflow-tracing"></a><span data-ttu-id="11ac5-104">Para determinar a duração de execução do aplicativo de fluxo de trabalho usando o rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="11ac5-104">To determine workflow application execution duration by using workflow tracing</span></span>  
  
1.  <span data-ttu-id="11ac5-105">Abra [!INCLUDE[vs2010](../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="11ac5-105">Open [!INCLUDE[vs2010](../../../includes/vs2010-md.md)].</span></span>  <span data-ttu-id="11ac5-106">Selecione **arquivo**, **novo**, **projeto**.</span><span class="sxs-lookup"><span data-stu-id="11ac5-106">Select **File**, **New**, **Project**.</span></span>  <span data-ttu-id="11ac5-107">Em **c#**, selecione o **fluxo de trabalho** nó.</span><span class="sxs-lookup"><span data-stu-id="11ac5-107">Under **C#**, select the **Workflow** node.</span></span>  <span data-ttu-id="11ac5-108">Selecione **aplicativo de Console do fluxo de trabalho** da lista de modelos.</span><span class="sxs-lookup"><span data-stu-id="11ac5-108">Select **Workflow Console Application** from the list of templates.</span></span>  <span data-ttu-id="11ac5-109">Nomeie o novo projeto `WorkflowDurationTracing` e clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="11ac5-109">Name the new project `WorkflowDurationTracing` and click **OK**.</span></span>  
  
2.  <span data-ttu-id="11ac5-110">Abra Workflow1.xaml.</span><span class="sxs-lookup"><span data-stu-id="11ac5-110">Open Workflow1.xaml.</span></span>  <span data-ttu-id="11ac5-111">Arraste uma atividade de <xref:System.Activities.Statements.Delay> na superfície de designer.</span><span class="sxs-lookup"><span data-stu-id="11ac5-111">Drag a <xref:System.Activities.Statements.Delay> activity onto the designer surface.</span></span> <span data-ttu-id="11ac5-112">Atribua o valor de 00:00: (dez 10 segundos) para a propriedade duração da atividade.</span><span class="sxs-lookup"><span data-stu-id="11ac5-112">Assign the value 00:00:10 (ten seconds) to the Duration property of the activity.</span></span>  
  
3.  <span data-ttu-id="11ac5-113">Abra o Visualizador de eventos clicando **iniciar**, **executar**e digitando `eventvwr.exe`.</span><span class="sxs-lookup"><span data-stu-id="11ac5-113">Open Event Viewer by clicking **Start**, **Run**, and entering `eventvwr.exe`.</span></span>  
  
4.  <span data-ttu-id="11ac5-114">Se você ainda não ativou o rastreamento de fluxo de trabalho, expanda **Applications and Services Logs**, **Microsoft**, **Windows**, **aplicativos de servidor de aplicativo** .</span><span class="sxs-lookup"><span data-stu-id="11ac5-114">If you haven’t enabled workflow tracing, expand **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.</span></span> <span data-ttu-id="11ac5-115">Selecione **exibição**, **Mostrar analítica e Logs de depuração**.</span><span class="sxs-lookup"><span data-stu-id="11ac5-115">Select **View**, **Show Analytic and Debug Logs**.</span></span> <span data-ttu-id="11ac5-116">Clique com botão direito **depurar** e selecione **Habilitar Log**.</span><span class="sxs-lookup"><span data-stu-id="11ac5-116">Right-click **Debug** and select **Enable Log**.</span></span> <span data-ttu-id="11ac5-117">Deixe o visualizador de eventos aberto de modo que os rastreamentos podem ser exibidos após o fluxo de trabalho é executado.</span><span class="sxs-lookup"><span data-stu-id="11ac5-117">Leave Event Viewer open so that traces can be viewed after the workflow is run.</span></span>  
  
5.  <span data-ttu-id="11ac5-118">Execute o aplicativo de fluxo de trabalho pressionando CTRL+SHIFT+B.</span><span class="sxs-lookup"><span data-stu-id="11ac5-118">Execute the workflow application by pressing CTRL+SHIFT+B.</span></span>  
  
6.  <span data-ttu-id="11ac5-119">No visualizador de eventos, localize um evento mais recente com ID 1009 e uma mensagem semelhante ao seguinte.</span><span class="sxs-lookup"><span data-stu-id="11ac5-119">In Event Viewer, find a recent event with ID 1009 and a message similar to the following.</span></span> <span data-ttu-id="11ac5-120">Anote de tempo que a mensagem foi registrado.</span><span class="sxs-lookup"><span data-stu-id="11ac5-120">Make a note of the time that the message was logged.</span></span>  
  
 <span data-ttu-id="11ac5-121">**Atividade pai ', DisplayName: ', InstanceId: ' filho agendado atividade 'WorkflowDurationTracking.Workflow1', DisplayName: 'Workflow1', InstanceId: '1'.**</span><span class="sxs-lookup"><span data-stu-id="11ac5-121">**Parent Activity '', DisplayName: '', InstanceId: '' scheduled child Activity 'WorkflowDurationTracking.Workflow1', DisplayName: 'Workflow1', InstanceId: '1'.**</span></span>  
  
7.  <span data-ttu-id="11ac5-122">Localizar outro evento mais recente com ID 1001 e uma mensagem semelhante ao seguinte.</span><span class="sxs-lookup"><span data-stu-id="11ac5-122">Find another recent event with ID 1001 and a message similar to the following.</span></span>  <span data-ttu-id="11ac5-123">Subtrair o tempo de mensagem anteriores do valor efetuado logon esta mensagem de determinar a duração da execução de fluxo de trabalho, que deve ser aproximadamente 10 segundos.</span><span class="sxs-lookup"><span data-stu-id="11ac5-123">Subtract the previous message time from this message’s Logged value to determine workflow execution duration, which should be around 10 seconds.</span></span>  
  
 <span data-ttu-id="11ac5-124">**WorkflowInstance Id: '1bbac57b-3322-498e-9e27-8833fda3a5bf' foi concluída no estado fechado.**</span><span class="sxs-lookup"><span data-stu-id="11ac5-124">**WorkflowInstance Id: '1bbac57b-3322-498e-9e27-8833fda3a5bf' has completed in the Closed state.**</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11ac5-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="11ac5-125">See Also</span></span>  
 [<span data-ttu-id="11ac5-126">Acompanhamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="11ac5-126">Workflow Tracing</span></span>](../../../docs/framework/windows-workflow-foundation/workflow-tracing.md)  
 [<span data-ttu-id="11ac5-127">Monitoramento do Windows Server App Fabric</span><span class="sxs-lookup"><span data-stu-id="11ac5-127">Windows Server App Fabric Monitoring</span></span>](http://go.microsoft.com/fwlink/?LinkId=201273)  
 [<span data-ttu-id="11ac5-128">Monitoramento de aplicativos com App Fabric</span><span class="sxs-lookup"><span data-stu-id="11ac5-128">Monitoring Applications with App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkId=201275)
