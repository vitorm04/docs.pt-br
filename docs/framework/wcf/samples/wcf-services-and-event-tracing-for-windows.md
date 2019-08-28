---
title: Serviços e rastreamento de eventos WCF para Windows
ms.date: 03/30/2017
ms.assetid: eda4355d-0bd0-4dc9-80a2-d2c832152272
ms.openlocfilehash: e1ee7154e2ad5b22ff0debcdd15d5809fc55df13
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044524"
---
# <a name="wcf-services-and-event-tracing-for-windows"></a><span data-ttu-id="faf42-102">Serviços e rastreamento de eventos WCF para Windows</span><span class="sxs-lookup"><span data-stu-id="faf42-102">WCF Services and Event Tracing for Windows</span></span>
<span data-ttu-id="faf42-103">Este exemplo demonstra como usar o rastreamento analítico no Windows Communication Foundation (WCF) para emitir eventos no ETW (rastreamento de eventos para Windows).</span><span class="sxs-lookup"><span data-stu-id="faf42-103">This sample demonstrates how to use the analytic tracing in Windows Communication Foundation (WCF) to emit events in Event Tracing for Windows (ETW).</span></span> <span data-ttu-id="faf42-104">Os rastreamentos analíticos são eventos emitidos em pontos-chave na pilha do WCF que permitem a solução de problemas de serviços WCF no ambiente de produção.</span><span class="sxs-lookup"><span data-stu-id="faf42-104">The analytic traces are events emitted at key points in the WCF stack that allow troubleshooting of WCF services in production environment.</span></span>

 <span data-ttu-id="faf42-105">O rastreamento analítico nos serviços WCF é o rastreamento que pode ser ativado em um ambiente de produção com impacto mínimo sobre o desempenho.</span><span class="sxs-lookup"><span data-stu-id="faf42-105">Analytic trace in WCF services is tracing that can be turned on in a production environment with minimal impact on performance.</span></span> <span data-ttu-id="faf42-106">Esses rastreamentos são emitidos como eventos para uma sessão do ETW.</span><span class="sxs-lookup"><span data-stu-id="faf42-106">These traces are emitted as events to an ETW session.</span></span>

 <span data-ttu-id="faf42-107">Este exemplo inclui um serviço WCF básico no qual os eventos são emitidos do serviço para o log de eventos, que pode ser exibido usando Visualizador de Eventos.</span><span class="sxs-lookup"><span data-stu-id="faf42-107">This sample includes a basic WCF service in which events are emitted from the service to the event log, which can be viewed using Event Viewer.</span></span> <span data-ttu-id="faf42-108">Também é possível iniciar uma sessão de ETW dedicada que escuta eventos do serviço WCF.</span><span class="sxs-lookup"><span data-stu-id="faf42-108">It is also possible to start a dedicated ETW session that listens for events from the WCF service.</span></span> <span data-ttu-id="faf42-109">O exemplo inclui um script para criar uma sessão de ETW dedicada que armazena eventos em um arquivo binário que pode ser lido usando Visualizador de Eventos.</span><span class="sxs-lookup"><span data-stu-id="faf42-109">The sample includes a script to create a dedicated ETW session that stores events in a binary file that can be read using Event Viewer.</span></span>

#### <a name="to-use-this-sample"></a><span data-ttu-id="faf42-110">Para usar este exemplo</span><span class="sxs-lookup"><span data-stu-id="faf42-110">To use this sample</span></span>

1. <span data-ttu-id="faf42-111">Usando o Visual Studio 2012, abra o arquivo de solução EtwAnalyticTraceSample. sln.</span><span class="sxs-lookup"><span data-stu-id="faf42-111">Using Visual Studio 2012, open the EtwAnalyticTraceSample.sln solution file.</span></span>

2. <span data-ttu-id="faf42-112">Para criar a solução, pressione CTRL+SHIFT+B.</span><span class="sxs-lookup"><span data-stu-id="faf42-112">To build the solution, press CTRL+SHIFT+B.</span></span>

3. <span data-ttu-id="faf42-113">Para executar a solução, pressione CTRL+F5.</span><span class="sxs-lookup"><span data-stu-id="faf42-113">To run the solution, press CTRL+F5.</span></span>

     <span data-ttu-id="faf42-114">No navegador da Web, clique em **Calculator. svc**.</span><span class="sxs-lookup"><span data-stu-id="faf42-114">In the Web browser, click **Calculator.svc**.</span></span> <span data-ttu-id="faf42-115">O URI do documento WSDL para o serviço deve aparecer no navegador.</span><span class="sxs-lookup"><span data-stu-id="faf42-115">The URI of the WSDL document for the service should appear in the browser.</span></span> <span data-ttu-id="faf42-116">Copie esse URI.</span><span class="sxs-lookup"><span data-stu-id="faf42-116">Copy that URI.</span></span>

     <span data-ttu-id="faf42-117">Por padrão, o serviço começa a escutar solicitações na porta 1378 `http://localhost:1378/Calculator.svc`.</span><span class="sxs-lookup"><span data-stu-id="faf42-117">By default, the service starts listening for requests on port 1378 `http://localhost:1378/Calculator.svc`.</span></span>

4. <span data-ttu-id="faf42-118">Execute o cliente de teste do WCF (WcfTestClient. exe).</span><span class="sxs-lookup"><span data-stu-id="faf42-118">Run the WCF test client (WcfTestClient.exe).</span></span>

     <span data-ttu-id="faf42-119">O cliente de teste do WCF (WcfTestClient. exe) está `\<Visual Studio 2012 Install Dir>\Common7\IDE\WcfTestClient.exe`localizado em.</span><span class="sxs-lookup"><span data-stu-id="faf42-119">The WCF test client (WcfTestClient.exe) is located at `\<Visual Studio 2012 Install Dir>\Common7\IDE\WcfTestClient.exe`.</span></span>  <span data-ttu-id="faf42-120">O dir de instalação padrão do Visual Studio `C:\Program Files\Microsoft Visual Studio 10.0`2012 é.</span><span class="sxs-lookup"><span data-stu-id="faf42-120">The default Visual Studio 2012 install dir is `C:\Program Files\Microsoft Visual Studio 10.0`.</span></span>

5. <span data-ttu-id="faf42-121">No cliente de teste do WCF, adicione o serviço selecionando **arquivo**e, em seguida, **Adicionar serviço**.</span><span class="sxs-lookup"><span data-stu-id="faf42-121">Within the WCF test client, add the service by selecting **File**, and then **Add Service**.</span></span>

     <span data-ttu-id="faf42-122">Adicione o endereço do ponto de extremidade na caixa de entrada.</span><span class="sxs-lookup"><span data-stu-id="faf42-122">Add the endpoint address in the input box.</span></span> <span data-ttu-id="faf42-123">O padrão é `http://localhost:1378/Calculator.svc`.</span><span class="sxs-lookup"><span data-stu-id="faf42-123">The default is `http://localhost:1378/Calculator.svc`.</span></span>

6. <span data-ttu-id="faf42-124">Abra o aplicativo visualizador de eventos.</span><span class="sxs-lookup"><span data-stu-id="faf42-124">Open the Event Viewer application.</span></span>

     <span data-ttu-id="faf42-125">Antes de invocar o serviço, inicie Visualizador de Eventos e verifique se o log de eventos está escutando eventos emitidos do serviço WCF.</span><span class="sxs-lookup"><span data-stu-id="faf42-125">Before invoking the service, start Event Viewer and ensure that the event log is listening for tracking events emitted from the WCF service.</span></span>

7. <span data-ttu-id="faf42-126">No menu **Iniciar** , selecione **Ferramentas administrativas**e, em seguida, **Visualizador de eventos**.</span><span class="sxs-lookup"><span data-stu-id="faf42-126">From the **Start** menu, select **Administrative Tools**, and then **Event Viewer**.</span></span>  <span data-ttu-id="faf42-127">Habilite os logs analíticos e de **depuração** .</span><span class="sxs-lookup"><span data-stu-id="faf42-127">Enable the **Analytic** and **Debug** logs.</span></span>

8. <span data-ttu-id="faf42-128">No modo de exibição de árvore no Visualizador de Eventos, navegue até **Visualizador de eventos**, **logs de aplicativos e serviços**, **Microsoft**, **Windows**e, em seguida, **servidor de aplicativos-aplicativos**.</span><span class="sxs-lookup"><span data-stu-id="faf42-128">In the tree view in Event Viewer, navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application Server-Applications**.</span></span> <span data-ttu-id="faf42-129">Clique com o botão direito do mouse em **servidor de aplicativos**, selecione **Exibir**e, em seguida, **Mostrar logs analíticos e de depuração**.</span><span class="sxs-lookup"><span data-stu-id="faf42-129">Right-click **Application Server-Applications**, select **View**, and then **Show Analytic and Debug Logs**.</span></span>

     <span data-ttu-id="faf42-130">Verifique se a opção **Mostrar logs analíticos e de depuração** está marcada.</span><span class="sxs-lookup"><span data-stu-id="faf42-130">Ensure that the **Show Analytic and Debug Logs** option is checked.</span></span>

9. <span data-ttu-id="faf42-131">Habilite o log **analítico** .</span><span class="sxs-lookup"><span data-stu-id="faf42-131">Enable the **Analytic** log.</span></span>

     <span data-ttu-id="faf42-132">No modo de exibição de árvore no Visualizador de Eventos, navegue até **Visualizador de eventos**, **logs de aplicativos e serviços**, **Microsoft**, **Windows**e, em seguida, **servidor de aplicativos-aplicativos**.</span><span class="sxs-lookup"><span data-stu-id="faf42-132">In the tree view in Event Viewer, navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application Server-Applications**.</span></span> <span data-ttu-id="faf42-133">Clique com o botão direito do mouse em **analítica** e selecione **habilitar log**.</span><span class="sxs-lookup"><span data-stu-id="faf42-133">Right-click **Analytic** and select **Enable Log**.</span></span>

#### <a name="to-test-the-service"></a><span data-ttu-id="faf42-134">Para testar o serviço</span><span class="sxs-lookup"><span data-stu-id="faf42-134">To test the service</span></span>

1. <span data-ttu-id="faf42-135">Volte para o cliente de teste do WCF e clique `Divide` duas vezes e mantenha os valores padrão, que especificam um denominador de 0.</span><span class="sxs-lookup"><span data-stu-id="faf42-135">Switch back to WCF test client and double-click `Divide` and keep the default values, which specify a denominator of 0.</span></span>

     <span data-ttu-id="faf42-136">Se o denominador for 0, o serviço lançará uma falha.</span><span class="sxs-lookup"><span data-stu-id="faf42-136">If the denominator is 0, then the service throws a fault.</span></span>

2. <span data-ttu-id="faf42-137">Observe os eventos emitidos do serviço.</span><span class="sxs-lookup"><span data-stu-id="faf42-137">Observe the events emitted from the service.</span></span>

     <span data-ttu-id="faf42-138">Volte para Visualizador de Eventos e navegue até **Visualizador de eventos**, **logs de aplicativos e serviços**, **Microsoft**, **Windows**e, em seguida, **aplicativos de servidor de aplicativos**.</span><span class="sxs-lookup"><span data-stu-id="faf42-138">Switch back to Event Viewer and navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application Server-Applications**.</span></span> <span data-ttu-id="faf42-139">Clique com o botão direito do mouse em **analítica** e selecione **Atualizar**.</span><span class="sxs-lookup"><span data-stu-id="faf42-139">Right-click **Analytic** and select **Refresh**.</span></span>

     <span data-ttu-id="faf42-140">Os eventos de rastreamento analítico do WCF são exibidos no Visualizador de eventos.</span><span class="sxs-lookup"><span data-stu-id="faf42-140">The WCF analytic trace events are displayed in the event viewer.</span></span> <span data-ttu-id="faf42-141">Observe que, como uma falha foi gerada pelo serviço, um evento de rastreamento de erro é exibido no Visualizador de eventos.</span><span class="sxs-lookup"><span data-stu-id="faf42-141">Notice that because a fault was thrown by the service an error trace event is displayed in the event viewer.</span></span>

3. <span data-ttu-id="faf42-142">Repita as etapas 1 e 2, mas com entradas válidas.</span><span class="sxs-lookup"><span data-stu-id="faf42-142">Repeat steps 1 and 2, but with valid inputs.</span></span> <span data-ttu-id="faf42-143">O valor do `N2` parâmetro pode ser qualquer número diferente de 0.</span><span class="sxs-lookup"><span data-stu-id="faf42-143">The value of the `N2` parameter can be any number other than 0.</span></span>

     <span data-ttu-id="faf42-144">Atualize o canal analítico para exibir os eventos do WCF não inclua nenhum evento de erro.</span><span class="sxs-lookup"><span data-stu-id="faf42-144">Refresh the analytic channel to view the WCF events do not include any error events.</span></span>

 <span data-ttu-id="faf42-145">O exemplo demonstra os eventos de rastreamento analítico emitidos de um serviço WCF.</span><span class="sxs-lookup"><span data-stu-id="faf42-145">The sample demonstrates the analytic trace events emitted from a WCF service.</span></span>

#### <a name="to-cleanup-optional"></a><span data-ttu-id="faf42-146">A limpeza (opcional)</span><span class="sxs-lookup"><span data-stu-id="faf42-146">To cleanup (Optional)</span></span>

1. <span data-ttu-id="faf42-147">Visualizador de EventosAberto.</span><span class="sxs-lookup"><span data-stu-id="faf42-147">Open Event Viewer.</span></span>

2. <span data-ttu-id="faf42-148">Navegue até **Visualizador de eventos**, **logs de aplicativos e serviços**, **Microsoft**, **Windows**e, em seguida, aplicativos **-Server-** Applications.</span><span class="sxs-lookup"><span data-stu-id="faf42-148">Navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application-Server-Applications**.</span></span> <span data-ttu-id="faf42-149">Clique com o botão direito do mouse em **analítica** e selecione **desabilitar log**.</span><span class="sxs-lookup"><span data-stu-id="faf42-149">Right-click **Analytic** and select **Disable Log**.</span></span>

3. <span data-ttu-id="faf42-150">Navegue até **Visualizador de eventos**, **logs de aplicativos e serviços**, **Microsoft**, **Windows**e, em seguida, aplicativos **-Server-** Applications.</span><span class="sxs-lookup"><span data-stu-id="faf42-150">Navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application-Server-Applications**.</span></span> <span data-ttu-id="faf42-151">Clique com o botão direito do mouse em **analítica** e selecione **limpar log**.</span><span class="sxs-lookup"><span data-stu-id="faf42-151">Right-click **Analytic** and select **Clear Log**.</span></span>

4. <span data-ttu-id="faf42-152">Escolha a opção **limpar** para limpar os eventos.</span><span class="sxs-lookup"><span data-stu-id="faf42-152">Choose the **Clear** option to clear the events.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="faf42-153">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="faf42-153">The samples may already be installed on your computer.</span></span> <span data-ttu-id="faf42-154">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="faf42-154">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="faf42-155">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) [!INCLUDE[wf1](../../../../includes/wf1-md.md)] e exemplos.</span><span class="sxs-lookup"><span data-stu-id="faf42-155">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="faf42-156">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="faf42-156">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ETWTracing`  
  
## <a name="see-also"></a><span data-ttu-id="faf42-157">Consulte também</span><span class="sxs-lookup"><span data-stu-id="faf42-157">See also</span></span>

- [<span data-ttu-id="faf42-158">Exemplos de monitoramento do AppFabric</span><span class="sxs-lookup"><span data-stu-id="faf42-158">AppFabric Monitoring Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193959)
