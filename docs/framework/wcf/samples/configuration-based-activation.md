---
title: Ativação com base em configuração
ms.date: 03/30/2017
ms.assetid: 21bb762e-c43e-4b0c-887b-5e434d665838
ms.openlocfilehash: 3ac4edd2a51e4ed8a5c0b7e73d7d1afa31334c33
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2018
---
# <a name="configuration-based-activation"></a><span data-ttu-id="ef0e2-102">Ativação com base em configuração</span><span class="sxs-lookup"><span data-stu-id="ef0e2-102">Configuration-Based Activation</span></span>
<span data-ttu-id="ef0e2-103">Este exemplo demonstra como ativar serviços Windows Communication Foundation (WCF) sem a necessidade de um arquivo. svc.</span><span class="sxs-lookup"><span data-stu-id="ef0e2-103">This sample demonstrates how to activate Windows Communication Foundation (WCF) services without requiring a .svc file.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ef0e2-104">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="ef0e2-104">The samples may already be installed on your computer.</span></span> <span data-ttu-id="ef0e2-105">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="ef0e2-105">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="ef0e2-106">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="ef0e2-106">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ef0e2-107">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="ef0e2-107">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\ConfigBasedActivation`  
  
## <a name="sample-details"></a><span data-ttu-id="ef0e2-108">Detalhes de exemplo</span><span class="sxs-lookup"><span data-stu-id="ef0e2-108">Sample Details</span></span>  
 <span data-ttu-id="ef0e2-109">Neste exemplo, o cliente é o cliente de teste do WCF e o serviço está hospedado no IIS.</span><span class="sxs-lookup"><span data-stu-id="ef0e2-109">In this sample, the client is the WCF test client and the service is hosted in IIS.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ef0e2-110">As instruções de instalação e compilação para este exemplo estão localizadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="ef0e2-110">The setup and build instructions for this sample are located at the end of this topic.</span></span>  
  
### <a name="activation-of-services-without-requiring-a-svc-file"></a><span data-ttu-id="ef0e2-111">Ativação de serviços sem a necessidade de um arquivo. svc</span><span class="sxs-lookup"><span data-stu-id="ef0e2-111">Activation of services without requiring a .svc file</span></span>  
 <span data-ttu-id="ef0e2-112">Em [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)], um arquivo. svc foi necessário para um serviço de ativação.</span><span class="sxs-lookup"><span data-stu-id="ef0e2-112">In [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)], a .svc file was required for activating a service.</span></span> <span data-ttu-id="ef0e2-113">Isso causa sobrecarga de gerenciamento adicionais, um arquivo adicional foi necessário para ser implantado e mantido junto com o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ef0e2-113">This caused additional management overhead, because an additional file was required to be deployed and maintained along with the application.</span></span> <span data-ttu-id="ef0e2-114">Com o lançamento do [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)], os componentes de ativação podem ser configurados usando o arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ef0e2-114">With the release of [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)], the activation components can be configured using the application configuration file.</span></span>  
  
 [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)]<span data-ttu-id="ef0e2-115"> apresenta um novo elemento de configuração (<xref:System.ServiceModel.Configuration.ServiceActivationElement>), além de <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection> do arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ef0e2-115"> introduces a new configuration element (<xref:System.ServiceModel.Configuration.ServiceActivationElement>), in the <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection> of the application configuration file.</span></span> <span data-ttu-id="ef0e2-116">O <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection> coleção aceita uma coleção de serviços para ativar, conforme mostrado no exemplo de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="ef0e2-116">The <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection> collection accepts a collection of services to activate, as shown in the following code example.</span></span>  
  
```xml  
<serviceActivations>  
   <add relativeAddress="Calculator.svc" service="Microsoft.ServiceModel.Samples.CalculatorService" />  
  
<serviceActivations>  
```  
  
 <span data-ttu-id="ef0e2-117">Observação a fazer é que a configuração é bem parecida com a configuração de arquivos. svc.</span><span class="sxs-lookup"><span data-stu-id="ef0e2-117">The observation to make is the configuration looks very similar to the configuration of .svc files.</span></span> <span data-ttu-id="ef0e2-118">É um atributo adicional que é apresentado a `relativeAddress` que fornece o endereço do serviço.</span><span class="sxs-lookup"><span data-stu-id="ef0e2-118">An additional attribute that is introduced is the `relativeAddress` that provides the address of the service.</span></span> <span data-ttu-id="ef0e2-119">O endereço relativo também é o caminho virtual para o serviço.</span><span class="sxs-lookup"><span data-stu-id="ef0e2-119">The relative address is also the virtual path for the service.</span></span> <span data-ttu-id="ef0e2-120">O host recupera o arquivo Web. config do arquivo a partir de `virtualPath` local, se presente; caso contrário, o host pesquisará seu recursivamente da pasta pai.</span><span class="sxs-lookup"><span data-stu-id="ef0e2-120">The host retrieves the Web.config file of the file from the `virtualPath` location, if present; otherwise the host searches its parent folder recursively.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ef0e2-121">Este exemplo requer a função de hospedagem no IIS.</span><span class="sxs-lookup"><span data-stu-id="ef0e2-121">This sample requires hosting in IIS to function.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="ef0e2-122">Para usar este exemplo</span><span class="sxs-lookup"><span data-stu-id="ef0e2-122">To use this sample</span></span>  
  
1.  <span data-ttu-id="ef0e2-123">Usando [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], abra o arquivo Service.csproj.</span><span class="sxs-lookup"><span data-stu-id="ef0e2-123">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open the Service.csproj file.</span></span>  
  
2.  <span data-ttu-id="ef0e2-124">Para criar a solução, pressione CTRL+SHIFT+B.</span><span class="sxs-lookup"><span data-stu-id="ef0e2-124">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="ef0e2-125">Teste o serviço executando WCFTestClient.exe.</span><span class="sxs-lookup"><span data-stu-id="ef0e2-125">Test the service by running WCFTestClient.exe.</span></span>  
  
4.  <span data-ttu-id="ef0e2-126">Usando [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], navegue até a pasta de 10.0\Common7\IDE %SystemDrive%\Program Files\Microsoft Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ef0e2-126">Using [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], navigate to the %SystemDrive%\Program Files\Microsoft Visual Studio 10.0\Common7\IDE folder.</span></span>  
  
5.  <span data-ttu-id="ef0e2-127">Execução WcfTestClient.exe.</span><span class="sxs-lookup"><span data-stu-id="ef0e2-127">Run WcfTestClient.exe.</span></span>  
  
6.  <span data-ttu-id="ef0e2-128">Defina o endereço MEX do serviço.</span><span class="sxs-lookup"><span data-stu-id="ef0e2-128">Set the MEX address of the service.</span></span>  
  
7.  <span data-ttu-id="ef0e2-129">Pressione CTRL + SHIFT + A para definir o endereço do serviço.</span><span class="sxs-lookup"><span data-stu-id="ef0e2-129">Press CTRL+SHIFT+A to set the service address.</span></span>  
  
8.  <span data-ttu-id="ef0e2-130">Definir o endereço http://localhost/ServiceModelSamples/Calculator.svc.</span><span class="sxs-lookup"><span data-stu-id="ef0e2-130">Set the address to http://localhost/ServiceModelSamples/Calculator.svc.</span></span>  
  
9. <span data-ttu-id="ef0e2-131">Executar o `Add` operação.</span><span class="sxs-lookup"><span data-stu-id="ef0e2-131">Perform the `Add` operation.</span></span> <span data-ttu-id="ef0e2-132">Definir o valor no `n1` parâmetro para o valor 10 e definido no `n2` parâmetro para 15.</span><span class="sxs-lookup"><span data-stu-id="ef0e2-132">Set value on the `n1` parameter to 10 and set value on the `n2` parameter to 15.</span></span>  
  
10. <span data-ttu-id="ef0e2-133">Pressione **invocar**.</span><span class="sxs-lookup"><span data-stu-id="ef0e2-133">Press **Invoke**.</span></span>  
  
     <span data-ttu-id="ef0e2-134">O resultado esperado é 25.</span><span class="sxs-lookup"><span data-stu-id="ef0e2-134">The expected result is 25.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ef0e2-135">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="ef0e2-135">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="ef0e2-136">Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ef0e2-136">Be sure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="ef0e2-137">Para compilar o c# ou Visual Basic .NET edição da solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ef0e2-137">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="ef0e2-138">Após a solução foi criada, execute bat para configurar o aplicativo ServiceModelSamples no IIS.</span><span class="sxs-lookup"><span data-stu-id="ef0e2-138">After the solution has been built, run Setup.bat to set up the ServiceModelSamples Application in IIS.</span></span> <span data-ttu-id="ef0e2-139">O diretório ServiceModelSamples agora deve aparecer como um aplicativo do IIS.</span><span class="sxs-lookup"><span data-stu-id="ef0e2-139">The ServiceModelSamples directory should now appear as an IIS Application.</span></span>  
  
4.  <span data-ttu-id="ef0e2-140">Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ef0e2-140">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef0e2-141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ef0e2-141">See Also</span></span>  
 [<span data-ttu-id="ef0e2-142">Exemplos de persistência e hospedagem de AppFabric</span><span class="sxs-lookup"><span data-stu-id="ef0e2-142">AppFabric Hosting and Persistence Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193961)
