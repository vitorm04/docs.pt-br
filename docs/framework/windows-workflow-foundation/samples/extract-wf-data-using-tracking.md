---
title: Dados de extrair WF usando o rastreamento
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e30c68f5-8c6a-495a-bd20-667a4364c68e
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4d6c269dc9c8b5a0050cfc3ffcefc3160b07c897
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="extract-wf-data-using-tracking"></a><span data-ttu-id="0a6f8-102">Dados de extrair WF usando o rastreamento</span><span class="sxs-lookup"><span data-stu-id="0a6f8-102">Extract WF Data using Tracking</span></span>
<span data-ttu-id="0a6f8-103">Este exemplo demonstra como usar o rastreamento de fluxo de trabalho para extrair variáveis e argumentos de fluxo de trabalho de atividades.</span><span class="sxs-lookup"><span data-stu-id="0a6f8-103">This sample demonstrates how to use workflow tracking to extract workflow variables and arguments from activities.</span></span> <span data-ttu-id="0a6f8-104">Ele também mostra a adição de anotações a acompanhar registros e a extração de carregamento útil dos dados dentro dos registros personalizados de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="0a6f8-104">It also shows the addition of annotations to tracking records and the extraction of data payload within custom tracking records.</span></span> <span data-ttu-id="0a6f8-105">O exemplo usa o rastreamento de evento para o Windows (ETW) que controla o participante para extrair dados de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="0a6f8-105">The sample uses the Event Tracing for Windows (ETW) tracking participant to extract data from the workflow.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="0a6f8-106">Detalhes de exemplo</span><span class="sxs-lookup"><span data-stu-id="0a6f8-106">Sample Details</span></span>  
 [!INCLUDE[wf](../../../../includes/wf-md.md)]<span data-ttu-id="0a6f8-107"> fornece o rastreamento para a visibilidade de ganho em execução de uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="0a6f8-107"> provides tracking to gain visibility into the execution of a workflow instance.</span></span> <span data-ttu-id="0a6f8-108">O tempo de execução de rastreamento emite-se registros de acompanhamento de fluxo de trabalho durante a execução de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="0a6f8-108">The tracking runtime emits workflow tracking records during the execution of the workflow.</span></span> <span data-ttu-id="0a6f8-109">Juntamente com os registros de acompanhamento de fluxo de trabalho, os dados dentro de instância de fluxo de trabalho podem ser extraídos de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="0a6f8-109">Along with the workflow tracking records, data within the workflow instance can be extracted from the workflow.</span></span> <span data-ttu-id="0a6f8-110">A lista a seguir detalha os tipos de dados que podem ser extraídos de registros de acompanhamento:</span><span class="sxs-lookup"><span data-stu-id="0a6f8-110">The following list details the types of data that can be extracted from tracking records:</span></span>  
  
1.  <span data-ttu-id="0a6f8-111">Variáveis de fluxo de trabalho em uma atividade e registros de rastreamento durante a execução da atividade.</span><span class="sxs-lookup"><span data-stu-id="0a6f8-111">Workflow variables within an activity and tracking records during activity execution.</span></span>  
  
     <span data-ttu-id="0a6f8-112">Para extrair variáveis de fluxo de trabalho, as variáveis a ser extraídos são especificados em um perfil.</span><span class="sxs-lookup"><span data-stu-id="0a6f8-112">To extract workflow variables, the variables to be extracted are specified in a profile.</span></span> <span data-ttu-id="0a6f8-113">As variáveis a ser extraídos só podem ser especificados com `ActivityStateQueries`.</span><span class="sxs-lookup"><span data-stu-id="0a6f8-113">Variables to be extracted can only be specified with `ActivityStateQueries`.</span></span> <span data-ttu-id="0a6f8-114">O exemplo de código a seguir demonstra um perfil de rastreamento usado para extrair a variável de fluxo de trabalho de uma atividade.</span><span class="sxs-lookup"><span data-stu-id="0a6f8-114">The following code example demonstrates a tracking profile used to extract the workflow variable from an activity.</span></span>  
  
    ```xml  
    <activityStateQuery activityName="StockPriceService">  
         <states>  
              <state name="Closed"/>  
         </states>  
         <variables>  
              <variable name="symbol"/>  
         </variables>  
    </activityStateQuery>  
    ```  
  
2.  <span data-ttu-id="0a6f8-115">Argumentos de atividade e estado da atividade que acompanha registros.</span><span class="sxs-lookup"><span data-stu-id="0a6f8-115">Activity arguments and activity state tracking records.</span></span>  
  
     <span data-ttu-id="0a6f8-116">Os argumentos definem os fluxos de dados de forma ou de uma atividade.</span><span class="sxs-lookup"><span data-stu-id="0a6f8-116">Arguments define the way data flows in or out of an activity.</span></span> <span data-ttu-id="0a6f8-117">Os argumentos para ser extraídos são especificados usando <xref:System.Activities.Tracking.ActivityStateQuery>. O exemplo de código é um perfil de rastreamento que extrai o argumento de `Value` .</span><span class="sxs-lookup"><span data-stu-id="0a6f8-117">Arguments to be extracted are specified using an <xref:System.Activities.Tracking.ActivityStateQuery>.The following code example is a tracking profile that extracts the `Value` argument.</span></span>  
  
    ```xml  
    <activityStateQuery activityName="GetStockPrice">  
         <states>  
              <state name="Closed"/>  
         </states>  
         <arguments>  
              <argument name="Value"/>  
         </arguments>  
    </activityStateQuery>  
    ```  
  
3.  <span data-ttu-id="0a6f8-118">As anotações são pares chave/valor que pode ser adicionado a qualquer registro de rastreamento que é emitida.</span><span class="sxs-lookup"><span data-stu-id="0a6f8-118">Annotations are key/value pairs that can be added to any tracking record that is emitted.</span></span>  
  
     <span data-ttu-id="0a6f8-119">As anotações servem como um mecanismo de posicionamento de rótulos para controlar registros.</span><span class="sxs-lookup"><span data-stu-id="0a6f8-119">Annotations serve as a tagging mechanism for tracking records.</span></span> <span data-ttu-id="0a6f8-120">As anotações são adicionadas a acompanhar registros com um perfil de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="0a6f8-120">Annotations are added to tracking records through a tracking profile.</span></span> <span data-ttu-id="0a6f8-121">As anotações podem ser adicionadas a qualquer tipo de uma consulta de acompanhamento de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="0a6f8-121">Annotations can be added to any type of a workflow tracking query.</span></span> <span data-ttu-id="0a6f8-122">O exemplo de código é um perfil de rastreamento que mostra como uma anotação pode ser adicionada a um registro de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="0a6f8-122">The following code example is a tracking profile that shows how an annotation can be added to a tracking record.</span></span>  
  
    ```xml  
    <workflowInstanceQuery>  
         <states>  
              <state name="Started"/>  
         </states>  
         <annotations>  
              <annotation name="StockPriceWorkflow" value="Begin"/>  
         </annotations>  
    </workflowInstanceQuery>  
    ```  
  
4.  <span data-ttu-id="0a6f8-123">Os registros personalizados são emitidas de rastreamento de atividades definidos pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="0a6f8-123">Custom tracking records are emitted from user-defined activities.</span></span>  
  
     <span data-ttu-id="0a6f8-124">Os registros personalizados de rastreamento podem carregar os dados de carregamento útil definidos dentro desta atividade.</span><span class="sxs-lookup"><span data-stu-id="0a6f8-124">Custom tracking records can carry payload data defined within this activity.</span></span> <span data-ttu-id="0a6f8-125">Para assinar registros personalizados de rastreamento em um perfil de rastreamento permite a extração de carregamento útil no registro de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="0a6f8-125">Subscribing for custom tracking records in a tracking profile allows the extraction of the payload within the tracking record.</span></span> <span data-ttu-id="0a6f8-126">Os registros personalizados de rastreamento podem ser extraídos com <xref:System.Activities.Tracking.TrackingQuery>personalizado.</span><span class="sxs-lookup"><span data-stu-id="0a6f8-126">The custom tracking records can be extracted with custom a <xref:System.Activities.Tracking.TrackingQuery>.</span></span> <span data-ttu-id="0a6f8-127">O exemplo de código é um perfil de rastreamento que extrai um registro de rastreamento personalizada juntamente com sua carga útil.</span><span class="sxs-lookup"><span data-stu-id="0a6f8-127">The following code example is a tracking profile that extracts a custom tracking record along with its payload.</span></span>  
  
    ```xml  
    <customTrackingQuery name="QuoteLookupEvent" activityName="GetStockPrice"/>  
    ```  
  
 <span data-ttu-id="0a6f8-128">O exemplo demonstra a extração de variáveis, argumentos, registros personalizado e anotações adicionar usando um perfil especificado em um Web.config. O rastreamento está ativado no serviço de fluxo de trabalho de exemplo adicionando um elemento do comportamento de `<etwTracking>` .</span><span class="sxs-lookup"><span data-stu-id="0a6f8-128">The sample demonstrates the extraction of a variables, arguments, custom records and adding annotations using a profile specified in a Web.config. Tracking is enabled on the sample workflow service by adding an `<etwTracking>` behavior element.</span></span> <span data-ttu-id="0a6f8-129">O exemplo de código ativar o rastreamento para `ExtractWorkflowVariables` que controla o perfil.</span><span class="sxs-lookup"><span data-stu-id="0a6f8-129">The following code example enables tracking for the `ExtractWorkflowVariables` tracking profile.</span></span>  
  
```xml  
<serviceBehaviors>  
     <behavior>  
               <etwTracking profileName="ExtractWorkflowVariables"/>  
     </behavior>  
</serviceBehaviors>  
```  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="0a6f8-130">Para usar este exemplo</span><span class="sxs-lookup"><span data-stu-id="0a6f8-130">To use this sample</span></span>  
  
1.  <span data-ttu-id="0a6f8-131">Usando [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], abra o arquivo de solução de WFStockPriceApplication.sln.</span><span class="sxs-lookup"><span data-stu-id="0a6f8-131">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the WFStockPriceApplication.sln solution file.</span></span>  
  
2.  <span data-ttu-id="0a6f8-132">Para criar a solução, pressione CTRL+SHIFT+B.</span><span class="sxs-lookup"><span data-stu-id="0a6f8-132">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="0a6f8-133">Para executar a solução, pressione F5.</span><span class="sxs-lookup"><span data-stu-id="0a6f8-133">To run the solution, press F5.</span></span>  
  
     <span data-ttu-id="0a6f8-134">A janela do navegador abre e mostra a listagem de diretório para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0a6f8-134">The browser window opens and shows the directory listing for the application.</span></span>  
  
4.  <span data-ttu-id="0a6f8-135">No navegador, clique StockPriceService.xamlx.</span><span class="sxs-lookup"><span data-stu-id="0a6f8-135">In the browser, click StockPriceService.xamlx.</span></span>  
  
5.  <span data-ttu-id="0a6f8-136">O navegador exibe a página de StockPriceService, que contém o endereço de WSDL de serviço local.</span><span class="sxs-lookup"><span data-stu-id="0a6f8-136">The browser displays the StockPriceService page, which contains the local service WSDL address.</span></span> <span data-ttu-id="0a6f8-137">Copie este endereço.</span><span class="sxs-lookup"><span data-stu-id="0a6f8-137">Copy this address.</span></span>  
  
     <span data-ttu-id="0a6f8-138">O exemplo a seguir mostra um endereço de WSDL de serviço local.</span><span class="sxs-lookup"><span data-stu-id="0a6f8-138">The following example shows a local service WSDL address.</span></span> `http://localhost:53797/StockPriceService.xamlx?wsdl`  
  
6.  <span data-ttu-id="0a6f8-139">Antes de chamar o serviço, ligue o visualizador de eventos e certifique-se de que o log de eventos é escutando eventos de rastreamento emissores de serviço de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="0a6f8-139">Before invoking the service, start Event Viewer and ensure that the event log is listening for tracking events emitted from the workflow service.</span></span>  
  
7.  <span data-ttu-id="0a6f8-140">Do **iniciar** menu, selecione **ferramentas administrativas** e **Visualizador de eventos**.</span><span class="sxs-lookup"><span data-stu-id="0a6f8-140">From the **Start** menu, select **Administrative Tools** and then **Event Viewer**.</span></span>  
  
8.  <span data-ttu-id="0a6f8-141">Na exibição de árvore no Visualizador de eventos, navegue até **Visualizador de eventos**, **Applications and Services Logs**, e **Microsoft**.</span><span class="sxs-lookup"><span data-stu-id="0a6f8-141">In the tree view in Event Viewer, navigate to **Event Viewer**, **Applications and Services Logs**, and **Microsoft**.</span></span> <span data-ttu-id="0a6f8-142">Clique com botão direito **Microsoft** e selecione **exibição** e **Mostrar Logs analíticos e depuração**.</span><span class="sxs-lookup"><span data-stu-id="0a6f8-142">Right-click **Microsoft** and select **View** and then **Show Analytic and Debug Logs**.</span></span>  
  
     <span data-ttu-id="0a6f8-143">Certifique-se de que o **Mostrar Logs analíticos e depuração** opção estiver marcada.</span><span class="sxs-lookup"><span data-stu-id="0a6f8-143">Ensure that the **Show Analytic and Debug Logs** option is checked.</span></span>  
  
9. <span data-ttu-id="0a6f8-144">Na exibição de árvore no Visualizador de eventos, navegue até **Visualizador de eventos**, **Applications and Services Logs**, **Microsoft**, **Windows**,  **Aplicativos de servidor de aplicativo**.</span><span class="sxs-lookup"><span data-stu-id="0a6f8-144">In the tree view in Event Viewer, navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.</span></span> <span data-ttu-id="0a6f8-145">Clique com botão direito **analítico** e selecione **Habilitar Log**.</span><span class="sxs-lookup"><span data-stu-id="0a6f8-145">Right-click **Analytic** and select **Enable Log**.</span></span>  
  
10. <span data-ttu-id="0a6f8-146">Usando [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], abra o cliente de teste de windows.</span><span class="sxs-lookup"><span data-stu-id="0a6f8-146">Using [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], open the WCF test client.</span></span>  
  
     <span data-ttu-id="0a6f8-147">O cliente de teste do WCF (WcfTestClient.exe) está localizado no \< [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] pasta de instalação > \Common7\IDE\ pasta.</span><span class="sxs-lookup"><span data-stu-id="0a6f8-147">The WCF test client (WcfTestClient.exe) is located in the \<[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] installation folder>\Common7\IDE\ folder.</span></span>  
  
     <span data-ttu-id="0a6f8-148">A pasta de instalação de [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] é C:\Program Files\Microsoft Visual Studio 10,0.</span><span class="sxs-lookup"><span data-stu-id="0a6f8-148">The default [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] installation folder is C:\Program Files\Microsoft Visual Studio 10.0.</span></span>  
  
11. <span data-ttu-id="0a6f8-149">No cliente de teste do WCF, selecione **Adicionar serviço** do **arquivo** menu.</span><span class="sxs-lookup"><span data-stu-id="0a6f8-149">In WCF test client, select **Add Service** from the **File** menu.</span></span>  
  
     <span data-ttu-id="0a6f8-150">Adicione o endereço de WSDL de serviço local você copiou anterior na caixa de entrada.</span><span class="sxs-lookup"><span data-stu-id="0a6f8-150">Add the local service WSDL address you copied earlier in the input box.</span></span>  
  
12. <span data-ttu-id="0a6f8-151">No cliente de teste de windows, clique duas vezes em `GetStockPrice`.</span><span class="sxs-lookup"><span data-stu-id="0a6f8-151">In WCF test client, double-click `GetStockPrice`.</span></span>  
  
     <span data-ttu-id="0a6f8-152">Isso abre o método de `GetStockPrice` .</span><span class="sxs-lookup"><span data-stu-id="0a6f8-152">This opens the `GetStockPrice` method.</span></span> <span data-ttu-id="0a6f8-153">A solicitação aceita um parâmetro.</span><span class="sxs-lookup"><span data-stu-id="0a6f8-153">The request accepts one parameter.</span></span> <span data-ttu-id="0a6f8-154">Use o valor **Contoso**.</span><span class="sxs-lookup"><span data-stu-id="0a6f8-154">Use the value **Contoso**.</span></span>  
  
13. <span data-ttu-id="0a6f8-155">Clique em **invocar**.</span><span class="sxs-lookup"><span data-stu-id="0a6f8-155">Click **Invoke**.</span></span>  
  
14. <span data-ttu-id="0a6f8-156">Retorne ao Visualizador de eventos e navegue até **Visualizador de eventos**, **Applications and Services Logs**, **Microsoft**, **Windows**,  **Aplicativos de servidor de aplicativo**.</span><span class="sxs-lookup"><span data-stu-id="0a6f8-156">Switch back to Event Viewer and navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.</span></span> <span data-ttu-id="0a6f8-157">Clique com botão direito **analítico** e selecione **atualizar**.</span><span class="sxs-lookup"><span data-stu-id="0a6f8-157">Right-click **Analytic** and select **Refresh**.</span></span> <span data-ttu-id="0a6f8-158">Os eventos de fluxo de trabalho são em intervalos de identificação de evento 100-199.</span><span class="sxs-lookup"><span data-stu-id="0a6f8-158">The workflow events are in the event ID ranges 100-199.</span></span>  
  
     <span data-ttu-id="0a6f8-159">Os eventos contêm as anotações, variáveis, os argumentos e os registros personalizados de rastreamento que podem ser exibidos no visualizador de eventos.</span><span class="sxs-lookup"><span data-stu-id="0a6f8-159">The events contain the annotations, variables, arguments and custom tracking records that can be viewed in the event viewer.</span></span>  
  
## <a name="cleaning-up-in-the-event-viewer"></a><span data-ttu-id="0a6f8-160">Limpar no visualizador de eventos</span><span class="sxs-lookup"><span data-stu-id="0a6f8-160">Cleaning up in the Event Viewer</span></span>  
 <span data-ttu-id="0a6f8-161">O canal analítico no log de eventos pode ser limpado no visualizador de eventos fazendo o seguinte.</span><span class="sxs-lookup"><span data-stu-id="0a6f8-161">The analytic channel in the event log can be cleaned up in the Event Viewer by doing the following.</span></span>  
  
#### <a name="to-clean-up-optional"></a><span data-ttu-id="0a6f8-162">Para limpar (opcional)</span><span class="sxs-lookup"><span data-stu-id="0a6f8-162">To clean up (Optional)</span></span>  
  
1.  <span data-ttu-id="0a6f8-163">Visualizador de EventosAberto.</span><span class="sxs-lookup"><span data-stu-id="0a6f8-163">Open Event Viewer.</span></span>  
  
2.  <span data-ttu-id="0a6f8-164">Navegue até **Visualizador de eventos**, **Applications and Services Logs**, **Microsoft**, **Windows**, **aplicativo Aplicativos de servidor**.</span><span class="sxs-lookup"><span data-stu-id="0a6f8-164">Navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.</span></span> <span data-ttu-id="0a6f8-165">Clique com botão direito **analítico** e selecione **desabilitar Log**.</span><span class="sxs-lookup"><span data-stu-id="0a6f8-165">Right-click **Analytic** and select **Disable Log**.</span></span>  
  
3.  <span data-ttu-id="0a6f8-166">Navegue até **Visualizador de eventos**, **Applications and Services Logs**, **Microsoft**, **Windows**, **aplicativo Aplicativos de servidor**.</span><span class="sxs-lookup"><span data-stu-id="0a6f8-166">Navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.</span></span> <span data-ttu-id="0a6f8-167">Clique com botão direito **analítico** e selecione **Limpar Log**.</span><span class="sxs-lookup"><span data-stu-id="0a6f8-167">Right-click **Analytic** and select **Clear Log**.</span></span>  
  
     <span data-ttu-id="0a6f8-168">Escolha o **limpar** opção para limpar os eventos.</span><span class="sxs-lookup"><span data-stu-id="0a6f8-168">Choose the **Clear** option to clear the events.</span></span>  
  
## <a name="known-issue"></a><span data-ttu-id="0a6f8-169">Problema conhecido</span><span class="sxs-lookup"><span data-stu-id="0a6f8-169">Known Issue</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0a6f8-170">Há um problema conhecido em Visualizador de Eventos onde pode não decodifica eventos de ETW.</span><span class="sxs-lookup"><span data-stu-id="0a6f8-170">There is a known issue in the Event Viewer where it may fail to decode ETW events.</span></span> <span data-ttu-id="0a6f8-171">Você pode ver a uma mensagem de erro semelhante ao seguinte.</span><span class="sxs-lookup"><span data-stu-id="0a6f8-171">You may see an error message that looks like the following.</span></span>  
>   
>  `The description for Event ID <id> from source Microsoft-Windows-Application Server-Applications cannot be found. Either the component that raises this event is not installed on your local computer or the installation is corrupted. You can install or repair the component on the local computer.`  
>   
>  <span data-ttu-id="0a6f8-172">Se você encontrar esse erro, clique em **atualização** no painel Ações.</span><span class="sxs-lookup"><span data-stu-id="0a6f8-172">If you encounter this error, click **Refresh** in the actions pane.</span></span> <span data-ttu-id="0a6f8-173">O evento agora deve decodificar corretamente.</span><span class="sxs-lookup"><span data-stu-id="0a6f8-173">The event should now decode properly.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="0a6f8-174">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="0a6f8-174">The samples may already be installed on your computer.</span></span> <span data-ttu-id="0a6f8-175">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="0a6f8-175">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="0a6f8-176">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="0a6f8-176">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="0a6f8-177">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="0a6f8-177">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\ExtractWfData`  
  
## <a name="see-also"></a><span data-ttu-id="0a6f8-178">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0a6f8-178">See Also</span></span>  
 [<span data-ttu-id="0a6f8-179">Exemplos de monitoramento do AppFabric</span><span class="sxs-lookup"><span data-stu-id="0a6f8-179">AppFabric Monitoring Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193959)
