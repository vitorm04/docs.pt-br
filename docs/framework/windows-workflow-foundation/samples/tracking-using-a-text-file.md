---
title: Controlar usando um arquivo de texto
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 56a82682-73c2-4b91-a206-4d8bb12c561b
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: abb29dc584bbede14adcb396df8cd37a894b6f2f
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="tracking-using-a-text-file"></a><span data-ttu-id="32ab3-102">Controlar usando um arquivo de texto</span><span class="sxs-lookup"><span data-stu-id="32ab3-102">Tracking Using a Text File</span></span>
<span data-ttu-id="32ab3-103">Este exemplo demonstra como estender o rastreamento em [!INCLUDE[wf](../../../../includes/wf-md.md)] criando um participante personalizado de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="32ab3-103">This sample demonstrates how to extend tracking in [!INCLUDE[wf](../../../../includes/wf-md.md)] by creating a custom tracking participant.</span></span> <span data-ttu-id="32ab3-104">Os participantes de rastreamento são as classes do.NET Framework que recebem registros de rastreamento em tempo de execução que são emitidas.</span><span class="sxs-lookup"><span data-stu-id="32ab3-104">Tracking participants are .NET Framework classes that receive tracking records from the runtime as they are emitted.</span></span> <span data-ttu-id="32ab3-105">Você pode criar um participante de controle para transmitir os eventos de rastreamento a qualquer destino é necessário para sua situação.</span><span class="sxs-lookup"><span data-stu-id="32ab3-105">You can create a tracking participant to transport the tracking events to whichever destination is required for your scenario.</span></span> <span data-ttu-id="32ab3-106">Por exemplo, o participante de rastreamento (ETW de rastreamento do Windows) é fornecido como parte de [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="32ab3-106">For example, ETW (Event Tracing for Windows) Tracking Participant is provided as part of the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="32ab3-107">O participante de rastreamento neste exemplo grava os registros no formato XML para um arquivo de texto.</span><span class="sxs-lookup"><span data-stu-id="32ab3-107">The tracking participant in this sample writes the records in XML format to a text file.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="32ab3-108">Detalhes de exemplo</span><span class="sxs-lookup"><span data-stu-id="32ab3-108">Sample details</span></span>  
 <span data-ttu-id="32ab3-109">Para otimizar a utilidade e robustez do seu participante de rastreamento, algumas etapas adicionais devem ser concluídas para conectar corretamente o participante de rastreamento em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="32ab3-109">To optimize the usefulness and robustness of your tracking participant, some additional steps must be completed to properly wire the tracking participant to the runtime.</span></span> <span data-ttu-id="32ab3-110">A tabela a seguir descreve as classes usadas nesse exemplo para criar um participante de rastreamento que siga as práticas recomendadas.</span><span class="sxs-lookup"><span data-stu-id="32ab3-110">The following table describes the classes used in this sample to create a tracking participant that complies with best practices.</span></span>  
  
|<span data-ttu-id="32ab3-111">Classe</span><span class="sxs-lookup"><span data-stu-id="32ab3-111">Class</span></span>|<span data-ttu-id="32ab3-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="32ab3-112">Description</span></span>|  
|-----------|-----------------|  
|`TextFileTrackingExtensionElement`|<span data-ttu-id="32ab3-113"><xref:System.ServiceModel.Configuration.BehaviorExtensionElement> é usado para definir a seção de configuração usada para configurar o participante de rastreamento do arquivo de texto.</span><span class="sxs-lookup"><span data-stu-id="32ab3-113">A <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> is used to define the configuration section used to configure the text file tracking participant.</span></span> <span data-ttu-id="32ab3-114">Isso permite que os usuários especifiquem o destino do arquivo de log usando arquivos de configuração padrão do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="32ab3-114">This allows users to specify the destination of the log file using standard .NET Framework configuration files.</span></span>|  
|`TextFileTrackingBehavior`|<span data-ttu-id="32ab3-115">Os comportamentos em [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] permitem que os usuários injetem extensões em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="32ab3-115">Behaviors in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] allow users to inject extensions into the runtime.</span></span> <span data-ttu-id="32ab3-116">Esse comportamento adicionar o participante de rastreamento para o serviço quando inicia o serviço.</span><span class="sxs-lookup"><span data-stu-id="32ab3-116">This behavior adds the tracking participant to the service when the service starts.</span></span>|  
|`TextFileTrackingParticipant`|<span data-ttu-id="32ab3-117">O participante de rastreamento que recebe participantes de rastreamento em tempo de execução e os armazena em um arquivo de log como XML.</span><span class="sxs-lookup"><span data-stu-id="32ab3-117">The tracking participant that receives tracking participants at runtime and stores them to a log file as XML.</span></span>|  
  
## <a name="behavior-extension-elements-configuration"></a><span data-ttu-id="32ab3-118">Configuração de elementos de extensão do comportamento</span><span class="sxs-lookup"><span data-stu-id="32ab3-118">Behavior Extension Elements Configuration</span></span>  
 <span data-ttu-id="32ab3-119">Uma etapa é necessária mais para utilizar o elemento de extensão do comportamento descrito anteriormente usando arquivos de configuração do.NET Framework.</span><span class="sxs-lookup"><span data-stu-id="32ab3-119">One more step is required to make use of the behavior extension element previously described using .NET Framework configuration files.</span></span> <span data-ttu-id="32ab3-120">A seguinte configuração deve ser colocada em arquivos de configuração onde a extensão deve ser usada.</span><span class="sxs-lookup"><span data-stu-id="32ab3-120">The following configuration must be placed in configuration files where the extension is to be used.</span></span>  
  
```xml  
<system.serviceModel>  
    <extensions>  
      <behaviorExtensions>  
        <add name="textFileTracking" type="Microsoft.Samples.TextFileTracking.TextFileTrackingExtensionElement, WFStockPriceApplication, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
      </behaviorExtensions>  
    </extensions>  
…  
  </system.serviceModel>  
```  
  
> [!NOTE]
>  <span data-ttu-id="32ab3-121">Consulte o exemplo no arquivo web.config para um uso completo do exemplo de configuração dos elementos de extensão do comportamento.</span><span class="sxs-lookup"><span data-stu-id="32ab3-121">See the Web.config file in the sample for a complete example usage of behavior extension elements configuration.</span></span>  
  
## <a name="custom-tracking-records"></a><span data-ttu-id="32ab3-122">Registros de rastreamento personalizadas</span><span class="sxs-lookup"><span data-stu-id="32ab3-122">Custom Tracking Records</span></span>  
 <span data-ttu-id="32ab3-123">O arquivo de GetStockPrices.cs demonstra como criar registros personalizados de rastreamento de dentro de <xref:System.Activities.CodeActivity>.</span><span class="sxs-lookup"><span data-stu-id="32ab3-123">The GetStockPrices.cs file demonstrates how to create custom tracking records from within a <xref:System.Activities.CodeActivity>.</span></span> <span data-ttu-id="32ab3-124">Procure esse registro ao executar o exemplo.</span><span class="sxs-lookup"><span data-stu-id="32ab3-124">Look for this record when running the sample.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="32ab3-125">Para usar este exemplo</span><span class="sxs-lookup"><span data-stu-id="32ab3-125">To use this sample</span></span>  
  
1.  <span data-ttu-id="32ab3-126">Usando [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], abra o arquivo de solução de WFStockPriceApplication.sln.</span><span class="sxs-lookup"><span data-stu-id="32ab3-126">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the WFStockPriceApplication.sln solution file.</span></span>  
  
2.  <span data-ttu-id="32ab3-127">Para criar a solução, pressione CTRL+SHIFT+B.</span><span class="sxs-lookup"><span data-stu-id="32ab3-127">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="32ab3-128">Para executar a solução, pressione CTRL+F5.</span><span class="sxs-lookup"><span data-stu-id="32ab3-128">To run the solution, press CTRL+F5.</span></span>  
  
     <span data-ttu-id="32ab3-129">A janela do navegador abre e mostra a listagem de diretório para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="32ab3-129">The browser window opens and shows the directory listing for the application.</span></span>  
  
4.  <span data-ttu-id="32ab3-130">No navegador, clique StockPriceService.xamlx.</span><span class="sxs-lookup"><span data-stu-id="32ab3-130">In the browser, click StockPriceService.xamlx.</span></span>  
  
5.  <span data-ttu-id="32ab3-131">O navegador exibe o **StockPriceService** página, que contém o endereço de wsdl do serviço local.</span><span class="sxs-lookup"><span data-stu-id="32ab3-131">The browser displays the **StockPriceService** page, which contains the local service wsdl address.</span></span> <span data-ttu-id="32ab3-132">Copie este endereço.</span><span class="sxs-lookup"><span data-stu-id="32ab3-132">Copy this address.</span></span>  
  
     <span data-ttu-id="32ab3-133">Um exemplo de endereço de WSDL de serviço local é http://localhost:53797/StockPriceService.xamlx?wsdl.</span><span class="sxs-lookup"><span data-stu-id="32ab3-133">An example of the local service wsdl address is http://localhost:53797/StockPriceService.xamlx?wsdl.</span></span>  
  
6.  <span data-ttu-id="32ab3-134">Usar [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], vá para a pasta de [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] (a pasta de instalação é %SystemDrive% \ program files \ Microsoft Visual Studio 10.0).</span><span class="sxs-lookup"><span data-stu-id="32ab3-134">Using [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], go to your [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] folder (the default installation folder is %SystemDrive%\Program Files\Microsoft Visual Studio 10.0).</span></span> <span data-ttu-id="32ab3-135">Localize o Common7 \ IDE \ subfolder.</span><span class="sxs-lookup"><span data-stu-id="32ab3-135">Then locate the Common7\IDE\ subfolder.</span></span>  
  
7.  <span data-ttu-id="32ab3-136">Clique duas vezes no arquivo de WcfTestClient.exe para iniciar a Test usuário.</span><span class="sxs-lookup"><span data-stu-id="32ab3-136">Double-click the WcfTestClient.exe file to launch the WCF Test Client.</span></span>  
  
8.  <span data-ttu-id="32ab3-137">No cliente de teste do WCF, selecione **Adicionar serviço...**</span><span class="sxs-lookup"><span data-stu-id="32ab3-137">In the WCF Test Client, select **Add Service…**</span></span> <span data-ttu-id="32ab3-138">do **arquivo** menu.</span><span class="sxs-lookup"><span data-stu-id="32ab3-138">from the **File** menu.</span></span>  
  
9. <span data-ttu-id="32ab3-139">Cole o URL que você copiou apenas na caixa de texto.</span><span class="sxs-lookup"><span data-stu-id="32ab3-139">Paste the URL you just copied into the text box.</span></span>  
  
10. <span data-ttu-id="32ab3-140">Clique em **Okey** para fechar a caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="32ab3-140">Click **OK** to close the dialog.</span></span>  
  
11. <span data-ttu-id="32ab3-141">Testar o serviço usando a Test usuário.</span><span class="sxs-lookup"><span data-stu-id="32ab3-141">Test the service using the WCF Test Client.</span></span>  
  
    1.  <span data-ttu-id="32ab3-142">No cliente de teste do WCF, clique duas vezes em **GetStockPrice()** sob o **IStockPriceService** nó.</span><span class="sxs-lookup"><span data-stu-id="32ab3-142">In the WCF Test Client, double-click **GetStockPrice()** under the **IStockPriceService** node.</span></span>  
  
         <span data-ttu-id="32ab3-143">O **GetStockPrice()** método aparece no painel direito, com um parâmetro.</span><span class="sxs-lookup"><span data-stu-id="32ab3-143">The **GetStockPrice()** method appears in the right pane, with one parameter.</span></span>  
  
    2.  <span data-ttu-id="32ab3-144">Digite Contoso como o valor para o parâmetro.</span><span class="sxs-lookup"><span data-stu-id="32ab3-144">Type in Contoso as the value for the parameter.</span></span>  
  
    3.  <span data-ttu-id="32ab3-145">Clique em **invocar**.</span><span class="sxs-lookup"><span data-stu-id="32ab3-145">Click **Invoke**.</span></span>  
  
12. <span data-ttu-id="32ab3-146">Consulte os eventos rastreadas no arquivo de log localizado no diretório de dados do aplicativo em %APPDATA% \ trackingRecords.log.</span><span class="sxs-lookup"><span data-stu-id="32ab3-146">See the tracked events in the log file located in your application data directory at %APPDATA%\trackingRecords.log.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="32ab3-147">% APPDATA % é uma variável de ambiente que resolve para %SystemDrive%\Users\\< nome de usuário\>\appdata\roaming. na [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[lserver](../../../../includes/lserver-md.md)], ou Windows Server 2008.</span><span class="sxs-lookup"><span data-stu-id="32ab3-147">The %APPDATA% is an environment variable that resolves to %SystemDrive%\Users\\<username\>\AppData\Roaming in [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[lserver](../../../../includes/lserver-md.md)], or Windows Server 2008.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="32ab3-148">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="32ab3-148">The samples may already be installed on your computer.</span></span> <span data-ttu-id="32ab3-149">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="32ab3-149">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="32ab3-150">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="32ab3-150">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="32ab3-151">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="32ab3-151">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\TextFileTracking`  
  
## <a name="see-also"></a><span data-ttu-id="32ab3-152">Consulte também</span><span class="sxs-lookup"><span data-stu-id="32ab3-152">See Also</span></span>  
 [<span data-ttu-id="32ab3-153">Exemplos de monitoramento do AppFabric</span><span class="sxs-lookup"><span data-stu-id="32ab3-153">AppFabric Monitoring Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193959)
