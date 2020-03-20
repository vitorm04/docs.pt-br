---
title: Serviços e rastreamento de eventos WCF para Windows
ms.date: 03/30/2017
ms.assetid: eda4355d-0bd0-4dc9-80a2-d2c832152272
ms.openlocfilehash: b8a1f30f20aa2c541a574a070b3644569d633ca2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183206"
---
# <a name="wcf-services-and-event-tracing-for-windows"></a><span data-ttu-id="03b5a-102">Serviços e rastreamento de eventos WCF para Windows</span><span class="sxs-lookup"><span data-stu-id="03b5a-102">WCF Services and Event Tracing for Windows</span></span>
<span data-ttu-id="03b5a-103">Esta amostra demonstra como usar o rastreamento analítico no Windows Communication Foundation (WCF) para emitir eventos no Event Tracing for Windows (ETW).</span><span class="sxs-lookup"><span data-stu-id="03b5a-103">This sample demonstrates how to use the analytic tracing in Windows Communication Foundation (WCF) to emit events in Event Tracing for Windows (ETW).</span></span> <span data-ttu-id="03b5a-104">Os traços analíticos são eventos emitidos em pontos-chave na pilha WCF que permitem a solução de problemas de serviços WCF no ambiente de produção.</span><span class="sxs-lookup"><span data-stu-id="03b5a-104">The analytic traces are events emitted at key points in the WCF stack that allow troubleshooting of WCF services in production environment.</span></span>

 <span data-ttu-id="03b5a-105">O rastreamento analítico nos serviços wcf é o rastreamento que pode ser ligado em um ambiente de produção com impacto mínimo no desempenho.</span><span class="sxs-lookup"><span data-stu-id="03b5a-105">Analytic trace in WCF services is tracing that can be turned on in a production environment with minimal impact on performance.</span></span> <span data-ttu-id="03b5a-106">Esses traços são emitidos como eventos para uma sessão de ETW.</span><span class="sxs-lookup"><span data-stu-id="03b5a-106">These traces are emitted as events to an ETW session.</span></span>

 <span data-ttu-id="03b5a-107">Esta amostra inclui um serviço básico de WCF no qual os eventos são emitidos do serviço para o registro de eventos, que podem ser visualizados usando o Event Viewer.</span><span class="sxs-lookup"><span data-stu-id="03b5a-107">This sample includes a basic WCF service in which events are emitted from the service to the event log, which can be viewed using Event Viewer.</span></span> <span data-ttu-id="03b5a-108">Também é possível iniciar uma sessão dedicada de ETW que ouve eventos do serviço WCF.</span><span class="sxs-lookup"><span data-stu-id="03b5a-108">It is also possible to start a dedicated ETW session that listens for events from the WCF service.</span></span> <span data-ttu-id="03b5a-109">A amostra inclui um script para criar uma sessão de ETW dedicada que armazena eventos em um arquivo binário que pode ser lido usando o Event Viewer.</span><span class="sxs-lookup"><span data-stu-id="03b5a-109">The sample includes a script to create a dedicated ETW session that stores events in a binary file that can be read using Event Viewer.</span></span>

#### <a name="to-use-this-sample"></a><span data-ttu-id="03b5a-110">Para usar este exemplo</span><span class="sxs-lookup"><span data-stu-id="03b5a-110">To use this sample</span></span>

1. <span data-ttu-id="03b5a-111">Usando o Visual Studio 2012, abra o arquivo de solução EtwAnalyticTraceSample.sln.</span><span class="sxs-lookup"><span data-stu-id="03b5a-111">Using Visual Studio 2012, open the EtwAnalyticTraceSample.sln solution file.</span></span>

2. <span data-ttu-id="03b5a-112">Para criar a solução, pressione CTRL+SHIFT+B.</span><span class="sxs-lookup"><span data-stu-id="03b5a-112">To build the solution, press CTRL+SHIFT+B.</span></span>

3. <span data-ttu-id="03b5a-113">Para executar a solução, pressione CTRL+F5.</span><span class="sxs-lookup"><span data-stu-id="03b5a-113">To run the solution, press CTRL+F5.</span></span>

     <span data-ttu-id="03b5a-114">No navegador da Web, clique em **Calculadora.svc**.</span><span class="sxs-lookup"><span data-stu-id="03b5a-114">In the Web browser, click **Calculator.svc**.</span></span> <span data-ttu-id="03b5a-115">O URI do documento WSDL para o serviço deve aparecer no navegador.</span><span class="sxs-lookup"><span data-stu-id="03b5a-115">The URI of the WSDL document for the service should appear in the browser.</span></span> <span data-ttu-id="03b5a-116">Copie esse URI.</span><span class="sxs-lookup"><span data-stu-id="03b5a-116">Copy that URI.</span></span>

     <span data-ttu-id="03b5a-117">Por padrão, o serviço começa a ouvir `http://localhost:1378/Calculator.svc`solicitações na porta 1378 .</span><span class="sxs-lookup"><span data-stu-id="03b5a-117">By default, the service starts listening for requests on port 1378 `http://localhost:1378/Calculator.svc`.</span></span>

4. <span data-ttu-id="03b5a-118">Execute o cliente de teste WCF (WcfTestClient.exe).</span><span class="sxs-lookup"><span data-stu-id="03b5a-118">Run the WCF test client (WcfTestClient.exe).</span></span>

     <span data-ttu-id="03b5a-119">O cliente de teste WCF (WcfTestClient.exe) está localizado em `\<Visual Studio 2012 Install Dir>\Common7\IDE\WcfTestClient.exe`.</span><span class="sxs-lookup"><span data-stu-id="03b5a-119">The WCF test client (WcfTestClient.exe) is located at `\<Visual Studio 2012 Install Dir>\Common7\IDE\WcfTestClient.exe`.</span></span>  <span data-ttu-id="03b5a-120">O visual studio padrão 2012 instalar dir é `C:\Program Files\Microsoft Visual Studio 10.0`.</span><span class="sxs-lookup"><span data-stu-id="03b5a-120">The default Visual Studio 2012 install dir is `C:\Program Files\Microsoft Visual Studio 10.0`.</span></span>

5. <span data-ttu-id="03b5a-121">Dentro do cliente de teste WCF, adicione o serviço selecionando **Arquivo**e, em seguida, **Adicione serviço**.</span><span class="sxs-lookup"><span data-stu-id="03b5a-121">Within the WCF test client, add the service by selecting **File**, and then **Add Service**.</span></span>

     <span data-ttu-id="03b5a-122">Adicione o endereço do ponto de extremidade na caixa de entrada.</span><span class="sxs-lookup"><span data-stu-id="03b5a-122">Add the endpoint address in the input box.</span></span> <span data-ttu-id="03b5a-123">O padrão é `http://localhost:1378/Calculator.svc`.</span><span class="sxs-lookup"><span data-stu-id="03b5a-123">The default is `http://localhost:1378/Calculator.svc`.</span></span>

6. <span data-ttu-id="03b5a-124">Abra o aplicativo visualizador de eventos.</span><span class="sxs-lookup"><span data-stu-id="03b5a-124">Open the Event Viewer application.</span></span>

     <span data-ttu-id="03b5a-125">Antes de invocar o serviço, inicie o Event Viewer e certifique-se de que o registro de eventos esteja ouvindo o rastreamento de eventos emitidos pelo serviço WCF.</span><span class="sxs-lookup"><span data-stu-id="03b5a-125">Before invoking the service, start Event Viewer and ensure that the event log is listening for tracking events emitted from the WCF service.</span></span>

7. <span data-ttu-id="03b5a-126">No menu **Iniciar,** selecione **Ferramentas Administrativas**e, em seguida, **Visualizador de Eventos**.</span><span class="sxs-lookup"><span data-stu-id="03b5a-126">From the **Start** menu, select **Administrative Tools**, and then **Event Viewer**.</span></span>  <span data-ttu-id="03b5a-127">Habilite os **registros de análise** e **depuração.**</span><span class="sxs-lookup"><span data-stu-id="03b5a-127">Enable the **Analytic** and **Debug** logs.</span></span>

8. <span data-ttu-id="03b5a-128">Na exibição da árvore no Event Viewer, navegue até **o Event Viewer,** **Applications and Services Logs,** **Microsoft,** **Windows**e, em seguida, **Application Server-Applications**.</span><span class="sxs-lookup"><span data-stu-id="03b5a-128">In the tree view in Event Viewer, navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application Server-Applications**.</span></span> <span data-ttu-id="03b5a-129">Clique com o botão direito do mouse **aplicativos de servidor de aplicativos,** selecione **Exibir**e, em seguida, mostrar registros de análise **e depuração**.</span><span class="sxs-lookup"><span data-stu-id="03b5a-129">Right-click **Application Server-Applications**, select **View**, and then **Show Analytic and Debug Logs**.</span></span>

     <span data-ttu-id="03b5a-130">Certifique-se de que a opção **Mostrar registros de análise e depuração** seja verificada.</span><span class="sxs-lookup"><span data-stu-id="03b5a-130">Ensure that the **Show Analytic and Debug Logs** option is checked.</span></span>

9. <span data-ttu-id="03b5a-131">Habilite o **registro analítico.**</span><span class="sxs-lookup"><span data-stu-id="03b5a-131">Enable the **Analytic** log.</span></span>

     <span data-ttu-id="03b5a-132">Na exibição da árvore no Event Viewer, navegue até **o Event Viewer,** **Applications and Services Logs,** **Microsoft,** **Windows**e, em seguida, **Application Server-Applications**.</span><span class="sxs-lookup"><span data-stu-id="03b5a-132">In the tree view in Event Viewer, navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application Server-Applications**.</span></span> <span data-ttu-id="03b5a-133">Clique com o botão direito do mouse **Em Análise** e **selecione Ativar log**.</span><span class="sxs-lookup"><span data-stu-id="03b5a-133">Right-click **Analytic** and select **Enable Log**.</span></span>

#### <a name="to-test-the-service"></a><span data-ttu-id="03b5a-134">Para testar o serviço</span><span class="sxs-lookup"><span data-stu-id="03b5a-134">To test the service</span></span>

1. <span data-ttu-id="03b5a-135">Volte para o cliente de teste `Divide` WCF e clique duas vezes e mantenha os valores padrão, que especificam um denominador de 0.</span><span class="sxs-lookup"><span data-stu-id="03b5a-135">Switch back to WCF test client and double-click `Divide` and keep the default values, which specify a denominator of 0.</span></span>

     <span data-ttu-id="03b5a-136">Se o denominador é 0, então o serviço lança uma falha.</span><span class="sxs-lookup"><span data-stu-id="03b5a-136">If the denominator is 0, then the service throws a fault.</span></span>

2. <span data-ttu-id="03b5a-137">Observe os eventos emitidos pelo serviço.</span><span class="sxs-lookup"><span data-stu-id="03b5a-137">Observe the events emitted from the service.</span></span>

     <span data-ttu-id="03b5a-138">Volte para o Visualizador de Eventos e navegue até **o Visualizador de Eventos,** **Registros de Aplicativos e Serviços,** **Microsoft,** **Windows**e, em seguida, Aplicativos de Servidor **de Aplicativos**.</span><span class="sxs-lookup"><span data-stu-id="03b5a-138">Switch back to Event Viewer and navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application Server-Applications**.</span></span> <span data-ttu-id="03b5a-139">Clique com o botão direito do mouse **Em Analítica** e selecione **Atualizar**.</span><span class="sxs-lookup"><span data-stu-id="03b5a-139">Right-click **Analytic** and select **Refresh**.</span></span>

     <span data-ttu-id="03b5a-140">Os eventos de rastreamento analítico wcf são exibidos no visualizador do evento.</span><span class="sxs-lookup"><span data-stu-id="03b5a-140">The WCF analytic trace events are displayed in the event viewer.</span></span> <span data-ttu-id="03b5a-141">Observe que, como uma falha foi lançada pelo serviço, um evento de rastreamento de erro é exibido no visualizador do evento.</span><span class="sxs-lookup"><span data-stu-id="03b5a-141">Notice that because a fault was thrown by the service an error trace event is displayed in the event viewer.</span></span>

3. <span data-ttu-id="03b5a-142">Repita as etapas 1 e 2, mas com entradas válidas.</span><span class="sxs-lookup"><span data-stu-id="03b5a-142">Repeat steps 1 and 2, but with valid inputs.</span></span> <span data-ttu-id="03b5a-143">O valor `N2` do parâmetro pode ser qualquer número diferente de 0.</span><span class="sxs-lookup"><span data-stu-id="03b5a-143">The value of the `N2` parameter can be any number other than 0.</span></span>

     <span data-ttu-id="03b5a-144">Atualize o canal analítico para visualizar os eventos WCF não inclua nenhum evento de erro.</span><span class="sxs-lookup"><span data-stu-id="03b5a-144">Refresh the analytic channel to view the WCF events do not include any error events.</span></span>

 <span data-ttu-id="03b5a-145">A amostra demonstra os eventos de rastreamento analítico emitidos a partir de um serviço WCF.</span><span class="sxs-lookup"><span data-stu-id="03b5a-145">The sample demonstrates the analytic trace events emitted from a WCF service.</span></span>

#### <a name="to-cleanup-optional"></a><span data-ttu-id="03b5a-146">A limpeza (opcional)</span><span class="sxs-lookup"><span data-stu-id="03b5a-146">To cleanup (Optional)</span></span>

1. <span data-ttu-id="03b5a-147">Visualizador de EventosAberto.</span><span class="sxs-lookup"><span data-stu-id="03b5a-147">Open Event Viewer.</span></span>

2. <span data-ttu-id="03b5a-148">Navegue até **o Visualizador de Eventos,** **Registros de aplicativos e serviços,** **Microsoft,** **Windows**e, em seguida, aplicativos de servidor **de aplicativos**.</span><span class="sxs-lookup"><span data-stu-id="03b5a-148">Navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application-Server-Applications**.</span></span> <span data-ttu-id="03b5a-149">Clique com o botão direito do mouse **Em Analítica** e **selecione Desativar log**.</span><span class="sxs-lookup"><span data-stu-id="03b5a-149">Right-click **Analytic** and select **Disable Log**.</span></span>

3. <span data-ttu-id="03b5a-150">Navegue até **o Visualizador de Eventos,** **Registros de aplicativos e serviços,** **Microsoft,** **Windows**e, em seguida, aplicativos de servidor **de aplicativos**.</span><span class="sxs-lookup"><span data-stu-id="03b5a-150">Navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application-Server-Applications**.</span></span> <span data-ttu-id="03b5a-151">Clique com o botão direito do mouse **Em Analítico** e selecione **Limpar Log**.</span><span class="sxs-lookup"><span data-stu-id="03b5a-151">Right-click **Analytic** and select **Clear Log**.</span></span>

4. <span data-ttu-id="03b5a-152">Escolha a opção **Limpar** para limpar os eventos.</span><span class="sxs-lookup"><span data-stu-id="03b5a-152">Choose the **Clear** option to clear the events.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="03b5a-153">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="03b5a-153">The samples may already be installed on your computer.</span></span> <span data-ttu-id="03b5a-154">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="03b5a-154">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="03b5a-155">Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation).</span><span class="sxs-lookup"><span data-stu-id="03b5a-155">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="03b5a-156">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="03b5a-156">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ETWTracing`  
  
## <a name="see-also"></a><span data-ttu-id="03b5a-157">Confira também</span><span class="sxs-lookup"><span data-stu-id="03b5a-157">See also</span></span>

- <span data-ttu-id="03b5a-158">[AppFabric que monitora Exemplos](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="03b5a-158">[AppFabric Monitoring Samples](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span></span>
