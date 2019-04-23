---
title: Serviços e rastreamento de eventos WCF para Windows
ms.date: 03/30/2017
ms.assetid: eda4355d-0bd0-4dc9-80a2-d2c832152272
ms.openlocfilehash: 35d0202a3b9cf4060240dc521554644d419a5c23
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59338963"
---
# <a name="wcf-services-and-event-tracing-for-windows"></a><span data-ttu-id="e2afe-102">Serviços e rastreamento de eventos WCF para Windows</span><span class="sxs-lookup"><span data-stu-id="e2afe-102">WCF Services and Event Tracing for Windows</span></span>
<span data-ttu-id="e2afe-103">Este exemplo demonstra como usar o rastreamento analítico no Windows Communication Foundation (WCF) para emitir eventos no rastreamento de eventos para Windows (ETW).</span><span class="sxs-lookup"><span data-stu-id="e2afe-103">This sample demonstrates how to use the analytic tracing in Windows Communication Foundation (WCF) to emit events in Event Tracing for Windows (ETW).</span></span> <span data-ttu-id="e2afe-104">Os rastreamentos analíticos são eventos emitidos nos pontos-chave na pilha do WCF que permitem a solução de problemas dos serviços WCF no ambiente de produção.</span><span class="sxs-lookup"><span data-stu-id="e2afe-104">The analytic traces are events emitted at key points in the WCF stack that allow troubleshooting of WCF services in production environment.</span></span>

 <span data-ttu-id="e2afe-105">Rastreamento analítico nos serviços do WCF é rastreamento que pode ser ativado em um ambiente de produção com impacto mínimo no desempenho.</span><span class="sxs-lookup"><span data-stu-id="e2afe-105">Analytic trace in WCF services is tracing that can be turned on in a production environment with minimal impact on performance.</span></span> <span data-ttu-id="e2afe-106">Esses rastreamentos são emitidos como eventos em uma sessão do ETW.</span><span class="sxs-lookup"><span data-stu-id="e2afe-106">These traces are emitted as events to an ETW session.</span></span>

 <span data-ttu-id="e2afe-107">Este exemplo inclui um serviço WCF básico no qual os eventos são emitidos pelo serviço no log de eventos, que podem ser exibidos usando o Visualizador de eventos.</span><span class="sxs-lookup"><span data-stu-id="e2afe-107">This sample includes a basic WCF service in which events are emitted from the service to the event log, which can be viewed using Event Viewer.</span></span> <span data-ttu-id="e2afe-108">Também é possível iniciar uma sessão ETW dedicada que escuta eventos do serviço WCF.</span><span class="sxs-lookup"><span data-stu-id="e2afe-108">It is also possible to start a dedicated ETW session that listens for events from the WCF service.</span></span> <span data-ttu-id="e2afe-109">O exemplo inclui um script para criar uma sessão ETW dedicada que armazena os eventos em um arquivo binário que pode ser lido usando o Visualizador de eventos.</span><span class="sxs-lookup"><span data-stu-id="e2afe-109">The sample includes a script to create a dedicated ETW session that stores events in a binary file that can be read using Event Viewer.</span></span>

#### <a name="to-use-this-sample"></a><span data-ttu-id="e2afe-110">Para usar este exemplo</span><span class="sxs-lookup"><span data-stu-id="e2afe-110">To use this sample</span></span>

1. <span data-ttu-id="e2afe-111">Usando o Visual Studio 2012, abra o arquivo de solução EtwAnalyticTraceSample.sln.</span><span class="sxs-lookup"><span data-stu-id="e2afe-111">Using Visual Studio 2012, open the EtwAnalyticTraceSample.sln solution file.</span></span>

2. <span data-ttu-id="e2afe-112">Para criar a solução, pressione CTRL+SHIFT+B.</span><span class="sxs-lookup"><span data-stu-id="e2afe-112">To build the solution, press CTRL+SHIFT+B.</span></span>

3. <span data-ttu-id="e2afe-113">Para executar a solução, pressione CTRL+F5.</span><span class="sxs-lookup"><span data-stu-id="e2afe-113">To run the solution, press CTRL+F5.</span></span>

     <span data-ttu-id="e2afe-114">No navegador da Web, clique em **Calculator.svc**.</span><span class="sxs-lookup"><span data-stu-id="e2afe-114">In the Web browser, click **Calculator.svc**.</span></span> <span data-ttu-id="e2afe-115">O URI do documento WSDL para o serviço deve aparecer no navegador.</span><span class="sxs-lookup"><span data-stu-id="e2afe-115">The URI of the WSDL document for the service should appear in the browser.</span></span> <span data-ttu-id="e2afe-116">Copie esse URI.</span><span class="sxs-lookup"><span data-stu-id="e2afe-116">Copy that URI.</span></span>

     <span data-ttu-id="e2afe-117">Por padrão, o serviço começa a escutar solicitações na porta 1378 `http://localhost:1378/Calculator.svc`.</span><span class="sxs-lookup"><span data-stu-id="e2afe-117">By default, the service starts listening for requests on port 1378 `http://localhost:1378/Calculator.svc`.</span></span>

4. <span data-ttu-id="e2afe-118">Execute o cliente de teste do WCF (WcfTestClient.exe).</span><span class="sxs-lookup"><span data-stu-id="e2afe-118">Run the WCF test client (WcfTestClient.exe).</span></span>

     <span data-ttu-id="e2afe-119">O cliente de teste do WCF (WcfTestClient.exe) está localizado em `\<Visual Studio 2012 Install Dir>\Common7\IDE\WcfTestClient.exe`.</span><span class="sxs-lookup"><span data-stu-id="e2afe-119">The WCF test client (WcfTestClient.exe) is located at `\<Visual Studio 2012 Install Dir>\Common7\IDE\WcfTestClient.exe`.</span></span>  <span data-ttu-id="e2afe-120">Dir de instalação do Visual Studio 2012 padrão é `C:\Program Files\Microsoft Visual Studio 10.0`.</span><span class="sxs-lookup"><span data-stu-id="e2afe-120">The default Visual Studio 2012 install dir is `C:\Program Files\Microsoft Visual Studio 10.0`.</span></span>

5. <span data-ttu-id="e2afe-121">Dentro do cliente de teste do WCF, adicione o serviço, selecionando **arquivo**e então **Adicionar serviço**.</span><span class="sxs-lookup"><span data-stu-id="e2afe-121">Within the WCF test client, add the service by selecting **File**, and then **Add Service**.</span></span>

     <span data-ttu-id="e2afe-122">Adicione o endereço do ponto de extremidade na caixa de entrada.</span><span class="sxs-lookup"><span data-stu-id="e2afe-122">Add the endpoint address in the input box.</span></span> <span data-ttu-id="e2afe-123">O padrão é `http://localhost:1378/Calculator.svc`.</span><span class="sxs-lookup"><span data-stu-id="e2afe-123">The default is `http://localhost:1378/Calculator.svc`.</span></span>

6. <span data-ttu-id="e2afe-124">Abra o aplicativo visualizador de eventos.</span><span class="sxs-lookup"><span data-stu-id="e2afe-124">Open the Event Viewer application.</span></span>

     <span data-ttu-id="e2afe-125">Antes de invocar o serviço, inicie o Visualizador de eventos e certifique-se de que o log de eventos é escutando eventos de rastreamento emitidos de serviço do WCF.</span><span class="sxs-lookup"><span data-stu-id="e2afe-125">Before invoking the service, start Event Viewer and ensure that the event log is listening for tracking events emitted from the WCF service.</span></span>

7. <span data-ttu-id="e2afe-126">Dos **inicie** menu, selecione **ferramentas administrativas**e, em seguida, **Visualizador de eventos**.</span><span class="sxs-lookup"><span data-stu-id="e2afe-126">From the **Start** menu, select **Administrative Tools**, and then **Event Viewer**.</span></span>  <span data-ttu-id="e2afe-127">Habilitar o **analítico** e **depurar** logs.</span><span class="sxs-lookup"><span data-stu-id="e2afe-127">Enable the **Analytic** and **Debug** logs.</span></span>

8. <span data-ttu-id="e2afe-128">Na exibição de árvore no Visualizador de eventos, navegue até **Visualizador de eventos**, **Applications and Services Logs**, **Microsoft**, **Windows**e, em seguida, **Aplicativos de servidor**.</span><span class="sxs-lookup"><span data-stu-id="e2afe-128">In the tree view in Event Viewer, navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application Server-Applications**.</span></span> <span data-ttu-id="e2afe-129">Clique com botão direito **aplicativos de servidor**, selecione **exibição**e então **Mostrar Logs analíticos e depuração**.</span><span class="sxs-lookup"><span data-stu-id="e2afe-129">Right-click **Application Server-Applications**, select **View**, and then **Show Analytic and Debug Logs**.</span></span>

     <span data-ttu-id="e2afe-130">Certifique-se de que o **Mostrar Logs analíticos e depuração** opção estiver marcada.</span><span class="sxs-lookup"><span data-stu-id="e2afe-130">Ensure that the **Show Analytic and Debug Logs** option is checked.</span></span>

9. <span data-ttu-id="e2afe-131">Habilitar o **analítico** log.</span><span class="sxs-lookup"><span data-stu-id="e2afe-131">Enable the **Analytic** log.</span></span>

     <span data-ttu-id="e2afe-132">Na exibição de árvore no Visualizador de eventos, navegue até **Visualizador de eventos**, **Applications and Services Logs**, **Microsoft**, **Windows**e, em seguida, **Aplicativos de servidor**.</span><span class="sxs-lookup"><span data-stu-id="e2afe-132">In the tree view in Event Viewer, navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application Server-Applications**.</span></span> <span data-ttu-id="e2afe-133">Clique com botão direito **analítico** e selecione **Habilitar Log**.</span><span class="sxs-lookup"><span data-stu-id="e2afe-133">Right-click **Analytic** and select **Enable Log**.</span></span>

#### <a name="to-test-the-service"></a><span data-ttu-id="e2afe-134">Para testar o serviço</span><span class="sxs-lookup"><span data-stu-id="e2afe-134">To test the service</span></span>

1. <span data-ttu-id="e2afe-135">Volte para o cliente de teste do WCF e clique duas vezes em `Divide` e mantenha os valores padrão, que especificam um denominador de 0.</span><span class="sxs-lookup"><span data-stu-id="e2afe-135">Switch back to WCF test client and double-click `Divide` and keep the default values, which specify a denominator of 0.</span></span>

     <span data-ttu-id="e2afe-136">Se o denominador é 0, o serviço gera uma falha.</span><span class="sxs-lookup"><span data-stu-id="e2afe-136">If the denominator is 0, then the service throws a fault.</span></span>

2. <span data-ttu-id="e2afe-137">Observe os eventos emitidos de serviço.</span><span class="sxs-lookup"><span data-stu-id="e2afe-137">Observe the events emitted from the service.</span></span>

     <span data-ttu-id="e2afe-138">Retorne ao Visualizador de eventos e navegue até **Visualizador de eventos**, **Applications and Services Logs**, **Microsoft**, **Windows**e, em seguida, **Aplicativos de servidor**.</span><span class="sxs-lookup"><span data-stu-id="e2afe-138">Switch back to Event Viewer and navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application Server-Applications**.</span></span> <span data-ttu-id="e2afe-139">Clique com botão direito **analítico** e selecione **atualizar**.</span><span class="sxs-lookup"><span data-stu-id="e2afe-139">Right-click **Analytic** and select **Refresh**.</span></span>

     <span data-ttu-id="e2afe-140">Os eventos de rastreamento analítico do WCF são exibidos no Visualizador de eventos.</span><span class="sxs-lookup"><span data-stu-id="e2afe-140">The WCF analytic trace events are displayed in the event viewer.</span></span> <span data-ttu-id="e2afe-141">Observe que porque uma falha foi gerada pelo serviço que é um evento de rastreamento de erro exibidos em Visualizar eventos.</span><span class="sxs-lookup"><span data-stu-id="e2afe-141">Notice that because a fault was thrown by the service an error trace event is displayed in the event viewer.</span></span>

3. <span data-ttu-id="e2afe-142">Repita as etapas 1 e 2, mas com as entradas válidas.</span><span class="sxs-lookup"><span data-stu-id="e2afe-142">Repeat steps 1 and 2, but with valid inputs.</span></span> <span data-ttu-id="e2afe-143">O valor da `N2` parâmetro pode ser qualquer número diferente de 0.</span><span class="sxs-lookup"><span data-stu-id="e2afe-143">The value of the `N2` parameter can be any number other than 0.</span></span>

     <span data-ttu-id="e2afe-144">Atualizar o canal analítico para exibir o WCF eventos não incluem nenhum evento de erro.</span><span class="sxs-lookup"><span data-stu-id="e2afe-144">Refresh the analytic channel to view the WCF events do not include any error events.</span></span>

 <span data-ttu-id="e2afe-145">O exemplo demonstra os eventos de rastreamento analítico emitidos de um serviço WCF.</span><span class="sxs-lookup"><span data-stu-id="e2afe-145">The sample demonstrates the analytic trace events emitted from a WCF service.</span></span>

#### <a name="to-cleanup-optional"></a><span data-ttu-id="e2afe-146">A limpeza (opcional)</span><span class="sxs-lookup"><span data-stu-id="e2afe-146">To cleanup (Optional)</span></span>

1. <span data-ttu-id="e2afe-147">Visualizador de EventosAberto.</span><span class="sxs-lookup"><span data-stu-id="e2afe-147">Open Event Viewer.</span></span>

2. <span data-ttu-id="e2afe-148">Navegue até **Visualizador de eventos**, **Applications and Services Logs**, **Microsoft**, **Windows**e, em seguida,  **Aplicativos de servidor**.</span><span class="sxs-lookup"><span data-stu-id="e2afe-148">Navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application-Server-Applications**.</span></span> <span data-ttu-id="e2afe-149">Clique com botão direito **analítico** e selecione **desabilitar Log**.</span><span class="sxs-lookup"><span data-stu-id="e2afe-149">Right-click **Analytic** and select **Disable Log**.</span></span>

3. <span data-ttu-id="e2afe-150">Navegue até **Visualizador de eventos**, **Applications and Services Logs**, **Microsoft**, **Windows**e, em seguida,  **Aplicativos de servidor**.</span><span class="sxs-lookup"><span data-stu-id="e2afe-150">Navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application-Server-Applications**.</span></span> <span data-ttu-id="e2afe-151">Clique com botão direito **analítico** e selecione **Limpar Log**.</span><span class="sxs-lookup"><span data-stu-id="e2afe-151">Right-click **Analytic** and select **Clear Log**.</span></span>

4. <span data-ttu-id="e2afe-152">Escolha o **limpar** opção para limpar os eventos.</span><span class="sxs-lookup"><span data-stu-id="e2afe-152">Choose the **Clear** option to clear the events.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="e2afe-153">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="e2afe-153">The samples may already be installed on your computer.</span></span> <span data-ttu-id="e2afe-154">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="e2afe-154">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="e2afe-155">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="e2afe-155">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e2afe-156">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="e2afe-156">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ETWTracing`  
  
## <a name="see-also"></a><span data-ttu-id="e2afe-157">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e2afe-157">See also</span></span>

- [<span data-ttu-id="e2afe-158">AppFabric que monitora exemplos</span><span class="sxs-lookup"><span data-stu-id="e2afe-158">AppFabric Monitoring Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193959)
