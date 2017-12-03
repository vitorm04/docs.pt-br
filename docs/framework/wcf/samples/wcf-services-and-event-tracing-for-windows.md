---
title: "Serviços e rastreamento de eventos WCF para Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eda4355d-0bd0-4dc9-80a2-d2c832152272
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ed3b7b370ed6b1d9a900579ff0e6f1b0a22290c3
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="wcf-services-and-event-tracing-for-windows"></a><span data-ttu-id="6685d-102">Serviços e rastreamento de eventos WCF para Windows</span><span class="sxs-lookup"><span data-stu-id="6685d-102">WCF Services and Event Tracing for Windows</span></span>
<span data-ttu-id="6685d-103">Este exemplo demonstra como usar o rastreamento analítico em [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] de emissão de eventos no evento de rastreamento para Windows (ETW).</span><span class="sxs-lookup"><span data-stu-id="6685d-103">This sample demonstrates how to use the analytic tracing in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] to emit events in Event Tracing for Windows (ETW).</span></span> <span data-ttu-id="6685d-104">Os rastreamentos analíticos são eventos emitidos nos pontos-chave no [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] pilha que permitem a solução de problemas de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviços no ambiente de produção.</span><span class="sxs-lookup"><span data-stu-id="6685d-104">The analytic traces are events emitted at key points in the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] stack that allow troubleshooting of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services in production environment.</span></span>  
  
 <span data-ttu-id="6685d-105">Rastreamento analítico em [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] é de serviços de rastreamento que pode ser ativado em um ambiente de produção com impacto mínimo no desempenho.</span><span class="sxs-lookup"><span data-stu-id="6685d-105">Analytic trace in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services is tracing that can be turned on in a production environment with minimal impact on performance.</span></span> <span data-ttu-id="6685d-106">Os rastreamentos são emitidos como eventos para uma sessão do ETW.</span><span class="sxs-lookup"><span data-stu-id="6685d-106">These traces are emitted as events to an ETW session.</span></span>  
  
 <span data-ttu-id="6685d-107">Este exemplo inclui um basic [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço em quais eventos são emitidos do serviço de log de eventos, que podem ser exibidos usando o Visualizador de eventos.</span><span class="sxs-lookup"><span data-stu-id="6685d-107">This sample includes a basic [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service in which events are emitted from the service to the event log, which can be viewed using Event Viewer.</span></span> <span data-ttu-id="6685d-108">Também é possível iniciar uma sessão ETW dedicada que escuta eventos a partir de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span><span class="sxs-lookup"><span data-stu-id="6685d-108">It is also possible to start a dedicated ETW session that listens for events from the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span></span> <span data-ttu-id="6685d-109">O exemplo inclui um script para criar uma sessão ETW dedicada que armazena os eventos em um arquivo binário que pode ser lida usando o Visualizador de eventos.</span><span class="sxs-lookup"><span data-stu-id="6685d-109">The sample includes a script to create a dedicated ETW session that stores events in a binary file that can be read using Event Viewer.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="6685d-110">Para usar este exemplo</span><span class="sxs-lookup"><span data-stu-id="6685d-110">To use this sample</span></span>  
  
1.  <span data-ttu-id="6685d-111">Usando [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], abra o arquivo de solução de EtwAnalyticTraceSample.sln.</span><span class="sxs-lookup"><span data-stu-id="6685d-111">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open the EtwAnalyticTraceSample.sln solution file.</span></span>  
  
2.  <span data-ttu-id="6685d-112">Para criar a solução, pressione CTRL+SHIFT+B.</span><span class="sxs-lookup"><span data-stu-id="6685d-112">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="6685d-113">Para executar a solução, pressione CTRL+F5.</span><span class="sxs-lookup"><span data-stu-id="6685d-113">To run the solution, press CTRL+F5.</span></span>  
  
     <span data-ttu-id="6685d-114">No navegador da Web, clique em **Calculator.svc**.</span><span class="sxs-lookup"><span data-stu-id="6685d-114">In the Web browser, click **Calculator.svc**.</span></span> <span data-ttu-id="6685d-115">O URI do documento WSDL para o serviço deve aparecer no navegador.</span><span class="sxs-lookup"><span data-stu-id="6685d-115">The URI of the WSDL document for the service should appear in the browser.</span></span> <span data-ttu-id="6685d-116">Copie esse URI.</span><span class="sxs-lookup"><span data-stu-id="6685d-116">Copy that URI.</span></span>  
  
     <span data-ttu-id="6685d-117">Por padrão, o serviço começa a escuta de solicitações na porta 1378 (http://localhost:1378/Calculator.svc).</span><span class="sxs-lookup"><span data-stu-id="6685d-117">By default, the service starts listening for requests on port 1378 (http://localhost:1378/Calculator.svc).</span></span>  
  
4.  <span data-ttu-id="6685d-118">Execute o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] cliente de teste (WcfTestClient.exe).</span><span class="sxs-lookup"><span data-stu-id="6685d-118">Run the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] test client (WcfTestClient.exe).</span></span>  
  
     <span data-ttu-id="6685d-119">O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] cliente de teste (WcfTestClient.exe) está localizado no \< [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] instalar Dir > \Common7\IDE\ WcfTestClient.exe (padrão [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] dir de instalação é C:\Program Files\Microsoft Visual Studio 10.0).</span><span class="sxs-lookup"><span data-stu-id="6685d-119">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] test client (WcfTestClient.exe) is located in the \<[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Install Dir>\Common7\IDE\ WcfTestClient.exe (default [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] install dir is C:\Program Files\Microsoft Visual Studio 10.0).</span></span>  
  
5.  <span data-ttu-id="6685d-120">Dentro de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] cliente de teste, adicione o serviço selecionando **arquivo**e, em seguida, **Adicionar serviço**.</span><span class="sxs-lookup"><span data-stu-id="6685d-120">Within the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] test client, add the service by selecting **File**, and then **Add Service**.</span></span>  
  
     <span data-ttu-id="6685d-121">Adicione o endereço do ponto de extremidade na caixa de entrada.</span><span class="sxs-lookup"><span data-stu-id="6685d-121">Add the endpoint address in the input box.</span></span> <span data-ttu-id="6685d-122">O padrão é http://localhost:1378/Calculator.svc.</span><span class="sxs-lookup"><span data-stu-id="6685d-122">The default is http://localhost:1378/Calculator.svc.</span></span>  
  
6.  <span data-ttu-id="6685d-123">Abra o aplicativo visualizador de eventos.</span><span class="sxs-lookup"><span data-stu-id="6685d-123">Open the Event Viewer application.</span></span>  
  
     <span data-ttu-id="6685d-124">Antes de chamar o serviço, iniciar o Visualizador de eventos e certifique-se de que o log de eventos está escutando para rastreamento de eventos emitidas a partir de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span><span class="sxs-lookup"><span data-stu-id="6685d-124">Before invoking the service, start Event Viewer and ensure that the event log is listening for tracking events emitted from the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span></span>  
  
7.  <span data-ttu-id="6685d-125">Do **iniciar** menu, selecione **ferramentas administrativas**e, em seguida, **Visualizador de eventos**.</span><span class="sxs-lookup"><span data-stu-id="6685d-125">From the **Start** menu, select **Administrative Tools**, and then **Event Viewer**.</span></span>  <span data-ttu-id="6685d-126">Habilitar o **analítico** e **depurar** logs.</span><span class="sxs-lookup"><span data-stu-id="6685d-126">Enable the **Analytic** and **Debug** logs.</span></span>  
  
8.  <span data-ttu-id="6685d-127">Na exibição de árvore no Visualizador de eventos, navegue até **Visualizador de eventos**, **Applications and Services Logs**, **Microsoft**, **Windows**e, em seguida, **Aplicativos de servidor de aplicativo**.</span><span class="sxs-lookup"><span data-stu-id="6685d-127">In the tree view in Event Viewer, navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application Server-Applications**.</span></span> <span data-ttu-id="6685d-128">Clique com botão direito **aplicativos de servidor de aplicativo**, selecione **exibição**e, em seguida, **Mostrar Logs analíticos e depuração**.</span><span class="sxs-lookup"><span data-stu-id="6685d-128">Right-click **Application Server-Applications**, select **View**, and then **Show Analytic and Debug Logs**.</span></span>  
  
     <span data-ttu-id="6685d-129">Certifique-se de que o **Mostrar Logs analíticos e depuração** opção estiver marcada.</span><span class="sxs-lookup"><span data-stu-id="6685d-129">Ensure that the **Show Analytic and Debug Logs** option is checked.</span></span>  
  
9. <span data-ttu-id="6685d-130">Habilitar o **analítico** log.</span><span class="sxs-lookup"><span data-stu-id="6685d-130">Enable the **Analytic** log.</span></span>  
  
     <span data-ttu-id="6685d-131">Na exibição de árvore no Visualizador de eventos, navegue até **Visualizador de eventos**, **Applications and Services Logs**, **Microsoft**, **Windows**e, em seguida, **Aplicativos de servidor de aplicativo**.</span><span class="sxs-lookup"><span data-stu-id="6685d-131">In the tree view in Event Viewer, navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application Server-Applications**.</span></span> <span data-ttu-id="6685d-132">Clique com botão direito **analítico** e selecione **Habilitar Log**.</span><span class="sxs-lookup"><span data-stu-id="6685d-132">Right-click **Analytic** and select **Enable Log**.</span></span>  
  
#### <a name="to-test-the-service"></a><span data-ttu-id="6685d-133">Para testar o serviço</span><span class="sxs-lookup"><span data-stu-id="6685d-133">To test the service</span></span>  
  
1.  <span data-ttu-id="6685d-134">Voltar ao [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] cliente de teste e clique duas vezes em `Divide` e mantenha os valores padrão, que especificam um denominador igual a 0.</span><span class="sxs-lookup"><span data-stu-id="6685d-134">Switch back to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] test client and double-click `Divide` and keep the default values, which specify a denominator of 0.</span></span>  
  
     <span data-ttu-id="6685d-135">Se o denominador é 0, o serviço gera uma falha.</span><span class="sxs-lookup"><span data-stu-id="6685d-135">If the denominator is 0, then the service throws a fault.</span></span>  
  
2.  <span data-ttu-id="6685d-136">Observe os eventos emitidos a partir do serviço.</span><span class="sxs-lookup"><span data-stu-id="6685d-136">Observe the events emitted from the service.</span></span>  
  
     <span data-ttu-id="6685d-137">Retorne ao Visualizador de eventos e navegue até **Visualizador de eventos**, **Applications and Services Logs**, **Microsoft**, **Windows**e, em seguida, **Aplicativos de servidor de aplicativo**.</span><span class="sxs-lookup"><span data-stu-id="6685d-137">Switch back to Event Viewer and navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application Server-Applications**.</span></span> <span data-ttu-id="6685d-138">Clique com botão direito **analítico** e selecione **atualizar**.</span><span class="sxs-lookup"><span data-stu-id="6685d-138">Right-click **Analytic** and select **Refresh**.</span></span>  
  
     <span data-ttu-id="6685d-139">Os eventos de rastreamento analítico do WCF são exibidos no Visualizador de eventos.</span><span class="sxs-lookup"><span data-stu-id="6685d-139">The WCF analytic trace events are displayed in the event viewer.</span></span> <span data-ttu-id="6685d-140">Observe que porque uma falha foi gerada pelo serviço que é um evento de rastreamento de erro no evento exibidas visualizador.</span><span class="sxs-lookup"><span data-stu-id="6685d-140">Notice that because a fault was thrown by the service an error trace event is displayed in the event viewer.</span></span>  
  
3.  <span data-ttu-id="6685d-141">Repita as etapas 1 e 2, mas com as entradas válidas.</span><span class="sxs-lookup"><span data-stu-id="6685d-141">Repeat steps 1 and 2, but with valid inputs.</span></span> <span data-ttu-id="6685d-142">O valor de `N2` parâmetro pode ser qualquer número diferente de 0.</span><span class="sxs-lookup"><span data-stu-id="6685d-142">The value of the `N2` parameter can be any number other than 0.</span></span>  
  
     <span data-ttu-id="6685d-143">Atualizar o canal analítico para exibir o WCF eventos não têm qualquer evento de erro.</span><span class="sxs-lookup"><span data-stu-id="6685d-143">Refresh the analytic channel to view the WCF events do not include any error events.</span></span>  
  
 <span data-ttu-id="6685d-144">O exemplo demonstra que os eventos de rastreamento analítico emitidos a partir de um serviço WCF.</span><span class="sxs-lookup"><span data-stu-id="6685d-144">The sample demonstrates the analytic trace events emitted from a WCF service.</span></span>  
  
#### <a name="to-cleanup-optional"></a><span data-ttu-id="6685d-145">A limpeza (opcional)</span><span class="sxs-lookup"><span data-stu-id="6685d-145">To cleanup (Optional)</span></span>  
  
1.  <span data-ttu-id="6685d-146">Visualizador de EventosAberto.</span><span class="sxs-lookup"><span data-stu-id="6685d-146">Open Event Viewer.</span></span>  
  
2.  <span data-ttu-id="6685d-147">Navegue até **Visualizador de eventos**, **Applications and Services Logs**, **Microsoft**, **Windows**e, em seguida,  **Aplicativos de servidor de aplicativo**.</span><span class="sxs-lookup"><span data-stu-id="6685d-147">Navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application-Server-Applications**.</span></span> <span data-ttu-id="6685d-148">Clique com botão direito **analítico** e selecione **desabilitar Log**.</span><span class="sxs-lookup"><span data-stu-id="6685d-148">Right-click **Analytic** and select **Disable Log**.</span></span>  
  
3.  <span data-ttu-id="6685d-149">Navegue até **Visualizador de eventos**, **Applications and Services Logs**, **Microsoft**, **Windows**e, em seguida,  **Aplicativos de servidor de aplicativo**.</span><span class="sxs-lookup"><span data-stu-id="6685d-149">Navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application-Server-Applications**.</span></span> <span data-ttu-id="6685d-150">Clique com botão direito **analítico** e selecione **Limpar Log**.</span><span class="sxs-lookup"><span data-stu-id="6685d-150">Right-click **Analytic** and select **Clear Log**.</span></span>  
  
4.  <span data-ttu-id="6685d-151">Escolha o **limpar** opção para limpar os eventos.</span><span class="sxs-lookup"><span data-stu-id="6685d-151">Choose the **Clear** option to clear the events.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="6685d-152">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="6685d-152">The samples may already be installed on your computer.</span></span> <span data-ttu-id="6685d-153">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="6685d-153">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="6685d-154">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="6685d-154">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="6685d-155">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="6685d-155">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ETWTracing`  
  
## <a name="see-also"></a><span data-ttu-id="6685d-156">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6685d-156">See Also</span></span>  
 [<span data-ttu-id="6685d-157">Exemplos de monitoramento do AppFabric</span><span class="sxs-lookup"><span data-stu-id="6685d-157">AppFabric Monitoring Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193959)
