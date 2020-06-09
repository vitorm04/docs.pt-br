---
title: Provedor de WMI
ms.date: 03/30/2017
ms.assetid: 462f0db3-f4a4-4a4b-ac26-41fc25c670a4
ms.openlocfilehash: a01b4b70d4c497d1efb93bb53a7339f5f7f29ef9
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84591040"
---
# <a name="wmi-provider"></a><span data-ttu-id="93e48-102">Provedor de WMI</span><span class="sxs-lookup"><span data-stu-id="93e48-102">WMI Provider</span></span>
<span data-ttu-id="93e48-103">Este exemplo demonstra como coletar dados de serviços Windows Communication Foundation (WCF) em tempo de execução usando o provedor de Instrumentação de Gerenciamento do Windows (WMI) que é incorporado ao WCF.</span><span class="sxs-lookup"><span data-stu-id="93e48-103">This sample demonstrates how to gather data from Windows Communication Foundation (WCF) services at runtime by using the Windows Management Instrumentation (WMI) provider that is built into WCF.</span></span> <span data-ttu-id="93e48-104">Além disso, este exemplo demonstra como adicionar um objeto WMI definido pelo usuário a um serviço.</span><span class="sxs-lookup"><span data-stu-id="93e48-104">Also, this sample demonstrates how to add a user-defined WMI object to a service.</span></span> <span data-ttu-id="93e48-105">O exemplo ativa o provedor WMI para o [introdução](getting-started-sample.md) e demonstra como coletar dados do `ICalculator` serviço em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="93e48-105">The sample activates the WMI provider for the [Getting Started](getting-started-sample.md) and demonstrates how to gather data from the `ICalculator` service at runtime.</span></span>  
  
 <span data-ttu-id="93e48-106">O WMI é a implementação do padrão Web-Based Enterprise Management (WBEM) da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="93e48-106">WMI is Microsoft's implementation of the Web-Based Enterprise Management (WBEM) standard.</span></span> <span data-ttu-id="93e48-107">Para obter mais informações sobre o SDK do WMI, consulte [Instrumentação de gerenciamento do Windows](/windows/desktop/WmiSdk/wmi-start-page).</span><span class="sxs-lookup"><span data-stu-id="93e48-107">For more information about the WMI SDK, see [Windows Management Instrumentation](/windows/desktop/WmiSdk/wmi-start-page).</span></span> <span data-ttu-id="93e48-108">O WBEM é um padrão do setor para a forma como os aplicativos expõem a instrumentação de gerenciamento para ferramentas de gerenciamento externas.</span><span class="sxs-lookup"><span data-stu-id="93e48-108">WBEM is an industry standard for how applications expose management instrumentation to external management tools.</span></span>  
  
 <span data-ttu-id="93e48-109">O WCF implementa um provedor WMI, um componente que expõe a instrumentação em tempo de execução por meio de uma interface compatível com o WBEM.</span><span class="sxs-lookup"><span data-stu-id="93e48-109">WCF implements a WMI provider, a component that exposes instrumentation at runtime through a WBEM-compatible interface.</span></span> <span data-ttu-id="93e48-110">As ferramentas de gerenciamento podem se conectar aos serviços por meio da interface em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="93e48-110">Management tools can connect to the services through the interface at runtime.</span></span> <span data-ttu-id="93e48-111">O WCF expõe atributos de serviços como endereços, associações, comportamentos e ouvintes.</span><span class="sxs-lookup"><span data-stu-id="93e48-111">WCF exposes attributes of services such as addresses, bindings, behaviors, and listeners.</span></span>  
  
 <span data-ttu-id="93e48-112">O provedor WMI interno é ativado no arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="93e48-112">The built-in WMI provider is activated in the configuration file of the application.</span></span> <span data-ttu-id="93e48-113">Isso é feito por meio do `wmiProviderEnabled` atributo do [\<diagnostics>](../../configure-apps/file-schema/wcf/diagnostics.md) na [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) seção, conforme mostrado na seguinte configuração de exemplo:</span><span class="sxs-lookup"><span data-stu-id="93e48-113">This is done through the `wmiProviderEnabled` attribute of the [\<diagnostics>](../../configure-apps/file-schema/wcf/diagnostics.md) in the [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) section, as shown in the following sample configuration:</span></span>  
  
```xml  
<system.serviceModel>  
    ...  
    <diagnostics wmiProviderEnabled="true" />  
    ...  
</system.serviceModel>  
```  
  
 <span data-ttu-id="93e48-114">Essa entrada de configuração expõe uma interface WMI.</span><span class="sxs-lookup"><span data-stu-id="93e48-114">This configuration entry exposes a WMI interface.</span></span> <span data-ttu-id="93e48-115">Os aplicativos de gerenciamento agora podem se conectar por meio dessa interface e acessar a instrumentação de gerenciamento do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="93e48-115">Management applications can now connect through this interface and access the management instrumentation of the application.</span></span>  
  
## <a name="custom-wmi-object"></a><span data-ttu-id="93e48-116">Objeto WMI personalizado</span><span class="sxs-lookup"><span data-stu-id="93e48-116">Custom WMI Object</span></span>  
 <span data-ttu-id="93e48-117">Adicionar objetos WMI a um serviço torna possível revelar informações definidas pelo usuário juntamente com as informações internas do provedor WMI.</span><span class="sxs-lookup"><span data-stu-id="93e48-117">Adding WMI objects to a service makes it possible to reveal user-defined information along with the built-in WMI provider information.</span></span> <span data-ttu-id="93e48-118">Isso é feito por meio da publicação do esquema do serviço no WMI usando o aplicativo InstallUtil. exe.</span><span class="sxs-lookup"><span data-stu-id="93e48-118">This is accomplished by publishing the schema of the service to WMI by using the Installutil.exe application.</span></span> <span data-ttu-id="93e48-119">Instruções para fazer isso, juntamente com mais detalhes, podem ser encontradas nas instruções de instalação no final do tópico.</span><span class="sxs-lookup"><span data-stu-id="93e48-119">Instructions to accomplish this, along with more details can be found in the setup instructions at the end of the topic.</span></span>  
  
## <a name="accessing-wmi-information"></a><span data-ttu-id="93e48-120">Acessando informações do WMI</span><span class="sxs-lookup"><span data-stu-id="93e48-120">Accessing WMI Information</span></span>  

<span data-ttu-id="93e48-121">Os dados do WMI podem ser acessados de várias maneiras diferentes.</span><span class="sxs-lookup"><span data-stu-id="93e48-121">WMI data can be accessed in many different ways.</span></span> <span data-ttu-id="93e48-122">A Microsoft fornece APIs WMI para scripts, Visual Basic aplicativos, aplicativos C++ e o .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="93e48-122">Microsoft provides WMI APIs for scripts, Visual Basic applications, C++ applications, and the .NET Framework.</span></span> <span data-ttu-id="93e48-123">Para obter mais informações, consulte [usando o WMI](/windows/desktop/wmisdk/using-wmi).</span><span class="sxs-lookup"><span data-stu-id="93e48-123">For more information, see [Using WMI](/windows/desktop/wmisdk/using-wmi).</span></span>
  
 <span data-ttu-id="93e48-124">Este exemplo usa dois scripts java: um para enumerar serviços em execução no computador junto com algumas de suas propriedades e o segundo para exibir dados WMI definidos pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="93e48-124">This sample uses two Java scripts: one to enumerate services running on the computer along with some of their properties and the second to view user-defined WMI data.</span></span> <span data-ttu-id="93e48-125">O script abre uma conexão com o provedor WMI, analisa dados e exibe os dados coletados.</span><span class="sxs-lookup"><span data-stu-id="93e48-125">The script opens a connection to the WMI provider, parses data, and displays the data gathered.</span></span>  
  
 <span data-ttu-id="93e48-126">Inicie o exemplo para criar uma instância em execução de um serviço WCF.</span><span class="sxs-lookup"><span data-stu-id="93e48-126">Start the sample to create a running instance of a WCF service.</span></span> <span data-ttu-id="93e48-127">Enquanto o serviço estiver em execução, execute cada script Java usando o seguinte comando no prompt de comando:</span><span class="sxs-lookup"><span data-stu-id="93e48-127">While the service is running, run each Java script by using the following command at the command prompt:</span></span>  
  
```console  
cscript EnumerateServices.js  
```  
  
 <span data-ttu-id="93e48-128">O script acessa a instrumentação contida no serviço e produz a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="93e48-128">The script accesses the instrumentation contained in the service and produces the following output:</span></span>  
  
```console  
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
  
 <span data-ttu-id="93e48-129">Em seguida, execute o segundo script Java para exibir os dados do WMI definidos pelo usuário:</span><span class="sxs-lookup"><span data-stu-id="93e48-129">Next, run the second Java Script to display the user-defined WMI data:</span></span>  
  
```console  
cscript EnumerateCustomObjects.js  
```  
  
 <span data-ttu-id="93e48-130">O script acessa a instrumentação definida pelo usuário contida nos serviços e produz a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="93e48-130">The script accesses the user-defined instrumentation contained in the services and produces the following output:</span></span>  
  
```console
1 WMIObject(s) found.  
|-PID:           30285bfd-9d66-4c4e-9be2-310499c5cef5  
|-InstanceId:    3839  
|-WMIInfo:       User Defined WMI Information.  
```  
  
 <span data-ttu-id="93e48-131">A saída mostra que há um único serviço em execução no computador.</span><span class="sxs-lookup"><span data-stu-id="93e48-131">The output shows that there is a single service running on the computer.</span></span> <span data-ttu-id="93e48-132">O serviço expõe um ponto de extremidade que implementa o `ICalculator` contrato.</span><span class="sxs-lookup"><span data-stu-id="93e48-132">The service exposes one endpoint that implements the `ICalculator` contract.</span></span> <span data-ttu-id="93e48-133">As configurações do comportamento e da Associação implementadas pelo ponto de extremidade são listadas como a soma de elementos individuais da pilha de mensagens.</span><span class="sxs-lookup"><span data-stu-id="93e48-133">The settings of the behavior and binding that are implemented by the endpoint are listed as the sum of individual elements of the messaging stack.</span></span>  
  
 <span data-ttu-id="93e48-134">O WMI não se limita a expor a instrumentação de gerenciamento da infraestrutura do WCF.</span><span class="sxs-lookup"><span data-stu-id="93e48-134">WMI is not limited to exposing the management instrumentation of the WCF infrastructure.</span></span> <span data-ttu-id="93e48-135">O aplicativo pode expor seus próprios itens de dados específicos de domínio por meio do mesmo mecanismo.</span><span class="sxs-lookup"><span data-stu-id="93e48-135">The application can expose its own domain-specific data items through the same mechanism.</span></span> <span data-ttu-id="93e48-136">O WMI é um mecanismo unificado para inspeção e controle de um serviço Web.</span><span class="sxs-lookup"><span data-stu-id="93e48-136">WMI is a unified mechanism for inspection and control of a Web service.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="93e48-137">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="93e48-137">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="93e48-138">Verifique se você executou o [procedimento de configuração única para os exemplos de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="93e48-138">Ensure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="93e48-139">Para criar a edição C# ou Visual Basic .NET da solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="93e48-139">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="93e48-140">Publique o esquema de serviços no WMI executando o InstallUtil. exe (os locais padrão para InstallUtil. exe são "%WINDIR%\Microsoft.NET\Framework\v4.0.30319") no arquivo Service. dll no diretório de hospedagem.</span><span class="sxs-lookup"><span data-stu-id="93e48-140">Publish the services schema to WMI by running the InstallUtil.exe (the default locations for InstallUtil.exe is "%WINDIR%\Microsoft.NET\Framework\v4.0.30319") on the service.dll file in the hosting directory.</span></span> <span data-ttu-id="93e48-141">Esta etapa só precisa ser executada quando foram feitas alterações no arquivo Service. dll.</span><span class="sxs-lookup"><span data-stu-id="93e48-141">This step only needs to be executed when changes have been made to the service.dll file.</span></span>
  
4. <span data-ttu-id="93e48-142">Para executar o exemplo em uma configuração de computador único ou entre computadores, siga as instruções em [executando os exemplos de Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="93e48-142">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="93e48-143">Se você instalou o WCF depois de instalar o ASP.NET, talvez seja necessário executar "% WINDIR% \ Microsoft. Net\Framework\v3.0\Windows Communication Foundation\servicemodelreg.exe "-r-x para conceder à conta ASPNET permissão para publicar objetos WMI.</span><span class="sxs-lookup"><span data-stu-id="93e48-143">If you installed WCF after installing ASP.NET, you may need to run "%WINDIR%\ Microsoft.Net\Framework\v3.0\Windows Communication Foundation\servicemodelreg.exe " -r -x to give the ASPNET account permission to publish WMI objects.</span></span>  
  
5. <span data-ttu-id="93e48-144">Exiba os dados do exemplo na superfície por meio do WMI usando os comandos: `cscript EnumerateServices.js` ou `cscript EnumerateCustomObjects.js` .</span><span class="sxs-lookup"><span data-stu-id="93e48-144">View data from the sample surfaced through WMI by using the commands: `cscript EnumerateServices.js` or `cscript EnumerateCustomObjects.js`.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="93e48-145">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="93e48-145">The samples may already be installed on your computer.</span></span> <span data-ttu-id="93e48-146">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="93e48-146">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="93e48-147">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="93e48-147">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="93e48-148">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="93e48-148">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\WMIProvider`  
  
## <a name="see-also"></a><span data-ttu-id="93e48-149">Confira também</span><span class="sxs-lookup"><span data-stu-id="93e48-149">See also</span></span>

- <span data-ttu-id="93e48-150">[AppFabric que monitora Exemplos](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="93e48-150">[AppFabric Monitoring Samples](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span></span>
