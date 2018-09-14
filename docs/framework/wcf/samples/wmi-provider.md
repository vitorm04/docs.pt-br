---
title: Provedor de WMI
ms.date: 03/30/2017
ms.assetid: 462f0db3-f4a4-4a4b-ac26-41fc25c670a4
ms.openlocfilehash: c3eb97537706282491de1863224e1502d6b56fda
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/14/2018
ms.locfileid: "45585520"
---
# <a name="wmi-provider"></a><span data-ttu-id="2d15f-102">Provedor de WMI</span><span class="sxs-lookup"><span data-stu-id="2d15f-102">WMI Provider</span></span>
<span data-ttu-id="2d15f-103">Este exemplo demonstra como coletar dados de serviços do Windows Communication Foundation (WCF) em tempo de execução, usando o provedor Windows Management Instrumentation (WMI) que é incorporado ao WCF.</span><span class="sxs-lookup"><span data-stu-id="2d15f-103">This sample demonstrates how to gather data from Windows Communication Foundation (WCF) services at runtime by using the Windows Management Instrumentation (WMI) provider that is built into WCF.</span></span> <span data-ttu-id="2d15f-104">Além disso, este exemplo demonstra como adicionar um objeto WMI definido pelo usuário a um serviço.</span><span class="sxs-lookup"><span data-stu-id="2d15f-104">Also, this sample demonstrates how to add a user-defined WMI object to a service.</span></span> <span data-ttu-id="2d15f-105">O exemplo ativa o provedor WMI para o [guia de Introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md) e demonstra como coletar dados do `ICalculator` serviço em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="2d15f-105">The sample activates the WMI provider for the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) and demonstrates how to gather data from the `ICalculator` service at runtime.</span></span>  
  
 <span data-ttu-id="2d15f-106">O WMI é a implementação da Microsoft do Web-Based Enterprise Management (WBEM) padrão.</span><span class="sxs-lookup"><span data-stu-id="2d15f-106">WMI is Microsoft's implementation of the Web-Based Enterprise Management (WBEM) standard.</span></span> <span data-ttu-id="2d15f-107">Para obter mais informações sobre o SDK do WMI, consulte [instrumentação de gerenciamento do Windows](/windows/desktop/WmiSdk/wmi-start-page).</span><span class="sxs-lookup"><span data-stu-id="2d15f-107">For more information about the WMI SDK, see [Windows Management Instrumentation](/windows/desktop/WmiSdk/wmi-start-page).</span></span> <span data-ttu-id="2d15f-108">O WBEM é um padrão do setor para como os aplicativos expõem instrumentação de gerenciamento para as ferramentas de gerenciamento externo.</span><span class="sxs-lookup"><span data-stu-id="2d15f-108">WBEM is an industry standard for how applications expose management instrumentation to external management tools.</span></span>  
  
 <span data-ttu-id="2d15f-109">O WCF implementa um provedor WMI, um componente que expõe a instrumentação no tempo de execução por meio de uma interface compatível com a iniciativa WBEM.</span><span class="sxs-lookup"><span data-stu-id="2d15f-109">WCF implements a WMI provider, a component that exposes instrumentation at runtime through a WBEM-compatible interface.</span></span> <span data-ttu-id="2d15f-110">Ferramentas de gerenciamento podem se conectar aos serviços por meio da interface em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="2d15f-110">Management tools can connect to the services through the interface at runtime.</span></span> <span data-ttu-id="2d15f-111">O WCF expõe atributos de serviços, como endereços, associações, comportamentos e ouvintes.</span><span class="sxs-lookup"><span data-stu-id="2d15f-111">WCF exposes attributes of services such as addresses, bindings, behaviors, and listeners.</span></span>  
  
 <span data-ttu-id="2d15f-112">O provedor WMI interno é ativado no arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2d15f-112">The built-in WMI provider is activated in the configuration file of the application.</span></span> <span data-ttu-id="2d15f-113">Isso é feito por meio das `wmiProviderEnabled` atributo do [ \<diagnóstico >](../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md) no [ \<System. ServiceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) seção, conforme mostrado no exemplo a seguir configuração:</span><span class="sxs-lookup"><span data-stu-id="2d15f-113">This is done through the `wmiProviderEnabled` attribute of the [\<diagnostics>](../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md) in the [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) section, as shown in the following sample configuration:</span></span>  
  
```xml  
<system.serviceModel>  
    ...  
    <diagnostics wmiProviderEnabled="true" />  
    ...  
</system.serviceModel>  
```  
  
 <span data-ttu-id="2d15f-114">Essa entrada de configuração expõe uma interface WMI.</span><span class="sxs-lookup"><span data-stu-id="2d15f-114">This configuration entry exposes a WMI interface.</span></span> <span data-ttu-id="2d15f-115">Aplicativos de gerenciamento agora podem se conectar por meio dessa interface e acessar a instrumentação de gerenciamento do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2d15f-115">Management applications can now connect through this interface and access the management instrumentation of the application.</span></span>  
  
## <a name="custom-wmi-object"></a><span data-ttu-id="2d15f-116">Objeto WMI personalizados</span><span class="sxs-lookup"><span data-stu-id="2d15f-116">Custom WMI Object</span></span>  
 <span data-ttu-id="2d15f-117">Adicionar objetos WMI a um serviço torna possível revelar informações definidas pelo usuário, juntamente com as informações do provedor WMI internos.</span><span class="sxs-lookup"><span data-stu-id="2d15f-117">Adding WMI objects to a service makes it possible to reveal user-defined information along with the built-in WMI provider information.</span></span> <span data-ttu-id="2d15f-118">Isso é feito ao publicar o esquema do serviço WMI, usando o aplicativo Installutil.exe.</span><span class="sxs-lookup"><span data-stu-id="2d15f-118">This is accomplished by publishing the schema of the service to WMI by using the Installutil.exe application.</span></span> <span data-ttu-id="2d15f-119">Instruções para fazer isso, juntamente com mais detalhes podem ser encontradas nas instruções de instalação no final do tópico.</span><span class="sxs-lookup"><span data-stu-id="2d15f-119">Instructions to accomplish this, along with more details can be found in the setup instructions at the end of the topic.</span></span>  
  
## <a name="accessing-wmi-information"></a><span data-ttu-id="2d15f-120">Acessando informações de WMI</span><span class="sxs-lookup"><span data-stu-id="2d15f-120">Accessing WMI Information</span></span>  
 <span data-ttu-id="2d15f-121">Dados do WMI podem ser acessados de várias maneiras diferentes.</span><span class="sxs-lookup"><span data-stu-id="2d15f-121">WMI data can be accessed many different ways.</span></span> <span data-ttu-id="2d15f-122">A Microsoft fornece as APIs do WMI para scripts, aplicativos do Visual Basic, aplicativos de C++ e o [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] (http://msdn.microsoft.com/library/default.asp?url=/library/wmisdk/wmi/using_wmi.asp).</span><span class="sxs-lookup"><span data-stu-id="2d15f-122">Microsoft provides WMI APIs for scripts, Visual Basic applications, C++ applications, and the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] (http://msdn.microsoft.com/library/default.asp?url=/library/wmisdk/wmi/using_wmi.asp).</span></span>  
  
 <span data-ttu-id="2d15f-123">Este exemplo usa dois scripts de Java: uma para enumerar os serviços em execução no computador junto com algumas das suas propriedades e a segunda para exibir dados WMI definido pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="2d15f-123">This sample uses two Java scripts: one to enumerate services running on the computer along with some of their properties and the second to view user-defined WMI data.</span></span> <span data-ttu-id="2d15f-124">O script abre uma conexão para o provedor WMI, analisa os dados e exibe os dados coletados.</span><span class="sxs-lookup"><span data-stu-id="2d15f-124">The script opens a connection to the WMI provider, parses data, and displays the data gathered.</span></span>  
  
 <span data-ttu-id="2d15f-125">Inicie a amostra para criar uma instância em execução de um serviço WCF.</span><span class="sxs-lookup"><span data-stu-id="2d15f-125">Start the sample to create a running instance of a WCF service.</span></span> <span data-ttu-id="2d15f-126">Enquanto o serviço está em execução, execute cada script de Java usando o seguinte comando no prompt de comando:</span><span class="sxs-lookup"><span data-stu-id="2d15f-126">While the service is running, run each Java script by using the following command at the command prompt:</span></span>  
  
```  
cscript EnumerateServices.js  
```  
  
 <span data-ttu-id="2d15f-127">O script acessa a instrumentação contida no serviço e gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="2d15f-127">The script accesses the instrumentation contained in the service and produces the following output:</span></span>  
  
```  
Microsoft (R) Windows Script Host Version 5.6  
Copyright © Microsoft Corporation 1996-2001. All rights reserved.  
  
1 service(s) found.  
|-PID:           5776  
|-DistinguishedName:  CalculatorService@http://localhost/ServiceModelSamples/service.svc  
|-Endpoints:     1 endpoints  
  |-CalculatorService.ICalculator@http://localhost/ServiceModelSamples/service.svc  
    |-Address:                        http://localhost/ServiceModelSamples/service.svc  
    |-CounterInstanceName:  
    |-AddressHeaders:                 0  
    |-ContractType:                   Contract.Name='ICalculator'  
    |-BindingElements:                4 bindings  
      |-BindingElements[0]  
        |-Type:                       TransactionFlowBindingElement  
      |-BindingElements[1]  
        |-Type:                       SymmetricSecurityBindingElement  
      |-BindingElements[2]  
        |-Type:                       TextMessageEncodingBindingElement  
        |-MaxReadPoolSize:            64  
        |-MaxWritePoolSize:           16  
      |-BindingElements[3]  
        |-Type:                       HttpTransportBindingElement  
        |-ManualAddressing:           false  
        |-MaxBufferSize:              65536  
        |-AllowCookies:               false  
        |-AuthenticationScheme:       Anonymous  
        |-BypassProxyOnLocal:         false  
        |-HostNameComparisonMode:     StrongWildcard  
        |-ProxyAddress:               null  
        |-ProxyAuthenticationScheme:  Anonymous  
        |-Realm:  
        |-TransferMode:               Buffered  
        |-UseDefaultWebProxy:         true  
|-Behaviors:     5 behaviors  
      |-Behavior[0]  
      |-Type:                       ServiceBehaviorAttribute  
        |-AddressFilterMode:               Exact  
        |-AutomaticSessionShutdown:        true  
        |-ConcurrencyMode:                 Single  
        |-IncludeExceptionDetailInFaults:  false  
        |-InstanceContextMode:             PerSession  
        |-TransactionIsolationLevel:       Unspecified  
        |-TransactionTimeout:              null  
        |-ValidateMustUnderstand:          true  
      |-Behavior[1]  
      |-Type:                       AspNetCompatibilityRequirementsAttribute  
      |-Behavior[2]  
      |-Type:                       ServiceDebugBehavior  
      |-Behavior[3]  
      |-Type:                       ServiceAuthorizationBehavior  
      |-Behavior[4]  
      |-Type:                       Behavior  
```  
  
 <span data-ttu-id="2d15f-128">Em seguida, execute o segundo Script de Java para exibir os dados WMI definido pelo usuário:</span><span class="sxs-lookup"><span data-stu-id="2d15f-128">Next, run the second Java Script to display the user-defined WMI data:</span></span>  
  
```  
cscript EnumerateCustomObjects.js  
```  
  
 <span data-ttu-id="2d15f-129">O script acessa a instrumentação definida pelo usuário contida nos serviços e produz a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="2d15f-129">The script accesses the user-defined instrumentation contained in the services and produces the following output:</span></span>  
  
```  
1 WMIObject(s) found.  
|-PID:           30285bfd-9d66-4c4e-9be2-310499c5cef5  
|-InstanceId:    3839  
|-WMIInfo:       User Defined WMI Information.  
```  
  
 <span data-ttu-id="2d15f-130">A saída mostra que há um único serviço em execução no computador.</span><span class="sxs-lookup"><span data-stu-id="2d15f-130">The output shows that there is a single service running on the computer.</span></span> <span data-ttu-id="2d15f-131">O serviço expõe um ponto de extremidade que implementa o `ICalculator` contrato.</span><span class="sxs-lookup"><span data-stu-id="2d15f-131">The service exposes one endpoint that implements the `ICalculator` contract.</span></span> <span data-ttu-id="2d15f-132">As configurações do comportamento e a associação que são implementados pelo ponto de extremidade são listados como a soma dos elementos individuais da pilha de mensagens.</span><span class="sxs-lookup"><span data-stu-id="2d15f-132">The settings of the behavior and binding that are implemented by the endpoint are listed as the sum of individual elements of the messaging stack.</span></span>  
  
 <span data-ttu-id="2d15f-133">WMI não se limita a exposição a instrumentação de gerenciamento da infraestrutura do WCF.</span><span class="sxs-lookup"><span data-stu-id="2d15f-133">WMI is not limited to exposing the management instrumentation of the WCF infrastructure.</span></span> <span data-ttu-id="2d15f-134">O aplicativo pode expor seus próprios itens de dados específicos do domínio por meio do mesmo mecanismo.</span><span class="sxs-lookup"><span data-stu-id="2d15f-134">The application can expose its own domain-specific data items through the same mechanism.</span></span> <span data-ttu-id="2d15f-135">O WMI é um mecanismo unificado para inspeção e controle de um serviço Web.</span><span class="sxs-lookup"><span data-stu-id="2d15f-135">WMI is a unified mechanism for inspection and control of a Web service.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="2d15f-136">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="2d15f-136">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="2d15f-137">Verifique se você tiver executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2d15f-137">Ensure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="2d15f-138">Para compilar a edição em C# ou Visual Basic .NET da solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2d15f-138">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="2d15f-139">Publica o esquema de serviços com o WMI, executando o InstallUtil.exe (os locais padrão de InstallUtil.exe é "% WINDIR%\Microsoft.NET\Framework\v4.0.30319") no arquivo service.dll no diretório de hospedagem.</span><span class="sxs-lookup"><span data-stu-id="2d15f-139">Publish the services schema to WMI by running the InstallUtil.exe (the default locations for InstallUtil.exe is "%WINDIR%\Microsoft.NET\Framework\v4.0.30319") on the service.dll file in the hosting directory.</span></span> <span data-ttu-id="2d15f-140">Esta etapa só precisa ser executado quando as alterações foram feitas no arquivo service.dll.</span><span class="sxs-lookup"><span data-stu-id="2d15f-140">This step only needs to be executed when changes have been made to the service.dll file.</span></span> <span data-ttu-id="2d15f-141">Para obter mais informações, consulte fornecendo informações de gerenciamento por instrumentação de aplicativos em: http://msdn2.microsoft.com/library/ms186147.aspx na seção "Como para: publicar o esquema para WMI para um instrumentado aplicativo".</span><span class="sxs-lookup"><span data-stu-id="2d15f-141">For more information, see Providing Management Information by Instrumenting Applications at: http://msdn2.microsoft.com/library/ms186147.aspx in the "How To: Publish the Scheme to WMI for an Instrumented Application" section.</span></span>  
  
4.  <span data-ttu-id="2d15f-142">Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2d15f-142">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="2d15f-143">Se você instalou o WCF depois de instalar o ASP.NET, você talvez precise executar "%WINDIR%\ Microsoft.Net\Framework\v3.0\Windows comunicação Foundation\servicemodelreg.exe "- r - x para dar permissão à conta ASPNET para publicar objetos WMI.</span><span class="sxs-lookup"><span data-stu-id="2d15f-143">If you installed WCF after installing ASP.NET, you may need to run "%WINDIR%\ Microsoft.Net\Framework\v3.0\Windows Communication Foundation\servicemodelreg.exe " -r -x to give the ASPNET account permission to publish WMI objects.</span></span>  
  
5.  <span data-ttu-id="2d15f-144">Exibir dados de exemplo exibido por meio do WMI usando os comandos: `cscript EnumerateServices.js` ou `cscript EnumerateCustomObjects.js`.</span><span class="sxs-lookup"><span data-stu-id="2d15f-144">View data from the sample surfaced through WMI by using the commands: `cscript EnumerateServices.js` or `cscript EnumerateCustomObjects.js`.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="2d15f-145">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="2d15f-145">The samples may already be installed on your computer.</span></span> <span data-ttu-id="2d15f-146">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="2d15f-146">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="2d15f-147">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="2d15f-147">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="2d15f-148">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="2d15f-148">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\WMIProvider`  
  
## <a name="see-also"></a><span data-ttu-id="2d15f-149">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2d15f-149">See Also</span></span>  
 [<span data-ttu-id="2d15f-150">AppFabric que monitora exemplos</span><span class="sxs-lookup"><span data-stu-id="2d15f-150">AppFabric Monitoring Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193959)
