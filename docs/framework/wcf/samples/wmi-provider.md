---
title: Provedor WMI
ms.date: 03/30/2017
ms.assetid: 462f0db3-f4a4-4a4b-ac26-41fc25c670a4
ms.openlocfilehash: 04fdbb7efcae6fdbb78f467352e6106ac5218799
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183195"
---
# <a name="wmi-provider"></a><span data-ttu-id="5c0df-102">Provedor WMI</span><span class="sxs-lookup"><span data-stu-id="5c0df-102">WMI Provider</span></span>
<span data-ttu-id="5c0df-103">Esta amostra demonstra como coletar dados dos serviços da Windows Communication Foundation (WCF) em tempo de execução usando o provedor de Instrumentação de Gerenciamento do Windows (WMI) que é incorporado ao WCF.</span><span class="sxs-lookup"><span data-stu-id="5c0df-103">This sample demonstrates how to gather data from Windows Communication Foundation (WCF) services at runtime by using the Windows Management Instrumentation (WMI) provider that is built into WCF.</span></span> <span data-ttu-id="5c0df-104">Além disso, esta amostra demonstra como adicionar um objeto WMI definido pelo usuário a um serviço.</span><span class="sxs-lookup"><span data-stu-id="5c0df-104">Also, this sample demonstrates how to add a user-defined WMI object to a service.</span></span> <span data-ttu-id="5c0df-105">A amostra ativa o provedor WMI para o [Getting](../../../../docs/framework/wcf/samples/getting-started-sample.md) Started `ICalculator` e demonstra como coletar dados do serviço em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="5c0df-105">The sample activates the WMI provider for the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) and demonstrates how to gather data from the `ICalculator` service at runtime.</span></span>  
  
 <span data-ttu-id="5c0df-106">O WMI é a implementação da Microsoft do padrão WBEM (Web-Based Enterprise Management, gerenciamento de empresas baseado na Web).</span><span class="sxs-lookup"><span data-stu-id="5c0df-106">WMI is Microsoft's implementation of the Web-Based Enterprise Management (WBEM) standard.</span></span> <span data-ttu-id="5c0df-107">Para obter mais informações sobre o WMI SDK, consulte [A Instrumentação de Gerenciamento do Windows](/windows/desktop/WmiSdk/wmi-start-page).</span><span class="sxs-lookup"><span data-stu-id="5c0df-107">For more information about the WMI SDK, see [Windows Management Instrumentation](/windows/desktop/WmiSdk/wmi-start-page).</span></span> <span data-ttu-id="5c0df-108">O WBEM é um padrão do setor para como as aplicações expõem a instrumentação de gerenciamento a ferramentas de gestão externa.</span><span class="sxs-lookup"><span data-stu-id="5c0df-108">WBEM is an industry standard for how applications expose management instrumentation to external management tools.</span></span>  
  
 <span data-ttu-id="5c0df-109">O WCF implementa um provedor WMI, um componente que expõe a instrumentação em tempo de execução através de uma interface compatível com WBEM.</span><span class="sxs-lookup"><span data-stu-id="5c0df-109">WCF implements a WMI provider, a component that exposes instrumentation at runtime through a WBEM-compatible interface.</span></span> <span data-ttu-id="5c0df-110">As ferramentas de gerenciamento podem se conectar aos serviços através da interface em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="5c0df-110">Management tools can connect to the services through the interface at runtime.</span></span> <span data-ttu-id="5c0df-111">O WCF expõe atributos de serviços como endereços, vinculações, comportamentos e ouvintes.</span><span class="sxs-lookup"><span data-stu-id="5c0df-111">WCF exposes attributes of services such as addresses, bindings, behaviors, and listeners.</span></span>  
  
 <span data-ttu-id="5c0df-112">O provedor WMI incorporado é ativado no arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5c0df-112">The built-in WMI provider is activated in the configuration file of the application.</span></span> <span data-ttu-id="5c0df-113">Isso é feito `wmiProviderEnabled` através do atributo do [ \<>de diagnóstico](../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md) na seção [ \<system.serviceModel>,](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) conforme mostrado na seguinte configuração de amostra:</span><span class="sxs-lookup"><span data-stu-id="5c0df-113">This is done through the `wmiProviderEnabled` attribute of the [\<diagnostics>](../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md) in the [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) section, as shown in the following sample configuration:</span></span>  
  
```xml  
<system.serviceModel>  
    ...  
    <diagnostics wmiProviderEnabled="true" />  
    ...  
</system.serviceModel>  
```  
  
 <span data-ttu-id="5c0df-114">Esta entrada de configuração expõe uma interface WMI.</span><span class="sxs-lookup"><span data-stu-id="5c0df-114">This configuration entry exposes a WMI interface.</span></span> <span data-ttu-id="5c0df-115">Os aplicativos de gerenciamento agora podem se conectar através desta interface e acessar a instrumentação de gerenciamento do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5c0df-115">Management applications can now connect through this interface and access the management instrumentation of the application.</span></span>  
  
## <a name="custom-wmi-object"></a><span data-ttu-id="5c0df-116">Objeto WMI personalizado</span><span class="sxs-lookup"><span data-stu-id="5c0df-116">Custom WMI Object</span></span>  
 <span data-ttu-id="5c0df-117">A adição de objetos WMI a um serviço permite revelar informações definidas pelo usuário, juntamente com as informações incorporadas do provedor WMI.</span><span class="sxs-lookup"><span data-stu-id="5c0df-117">Adding WMI objects to a service makes it possible to reveal user-defined information along with the built-in WMI provider information.</span></span> <span data-ttu-id="5c0df-118">Isso é feito publicando o esquema do serviço para o WMI usando o aplicativo Installutil.exe.</span><span class="sxs-lookup"><span data-stu-id="5c0df-118">This is accomplished by publishing the schema of the service to WMI by using the Installutil.exe application.</span></span> <span data-ttu-id="5c0df-119">Instruções para isso, juntamente com mais detalhes podem ser encontradas nas instruções de configuração no final do tópico.</span><span class="sxs-lookup"><span data-stu-id="5c0df-119">Instructions to accomplish this, along with more details can be found in the setup instructions at the end of the topic.</span></span>  
  
## <a name="accessing-wmi-information"></a><span data-ttu-id="5c0df-120">Acessando as informações do WMI</span><span class="sxs-lookup"><span data-stu-id="5c0df-120">Accessing WMI Information</span></span>  

<span data-ttu-id="5c0df-121">Os dados WMI podem ser acessados de muitas maneiras diferentes.</span><span class="sxs-lookup"><span data-stu-id="5c0df-121">WMI data can be accessed in many different ways.</span></span> <span data-ttu-id="5c0df-122">A Microsoft fornece APIs WMI para scripts, aplicativos Visual Basic, aplicativos C++ e o .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5c0df-122">Microsoft provides WMI APIs for scripts, Visual Basic applications, C++ applications, and the .NET Framework.</span></span> <span data-ttu-id="5c0df-123">Para obter mais informações, consulte [Usando WMI](/windows/desktop/wmisdk/using-wmi).</span><span class="sxs-lookup"><span data-stu-id="5c0df-123">For more information, see [Using WMI](/windows/desktop/wmisdk/using-wmi).</span></span>
  
 <span data-ttu-id="5c0df-124">Esta amostra usa dois scripts Java: um para enumerar serviços em execução no computador, juntamente com algumas de suas propriedades e o segundo para visualizar dados WMI definidos pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="5c0df-124">This sample uses two Java scripts: one to enumerate services running on the computer along with some of their properties and the second to view user-defined WMI data.</span></span> <span data-ttu-id="5c0df-125">O script abre uma conexão com o provedor WMI, analisa dados e exibe os dados coletados.</span><span class="sxs-lookup"><span data-stu-id="5c0df-125">The script opens a connection to the WMI provider, parses data, and displays the data gathered.</span></span>  
  
 <span data-ttu-id="5c0df-126">Inicie a amostra para criar uma instância em execução de um serviço WCF.</span><span class="sxs-lookup"><span data-stu-id="5c0df-126">Start the sample to create a running instance of a WCF service.</span></span> <span data-ttu-id="5c0df-127">Enquanto o serviço estiver em execução, execute cada script Java usando o seguinte comando no prompt de comando:</span><span class="sxs-lookup"><span data-stu-id="5c0df-127">While the service is running, run each Java script by using the following command at the command prompt:</span></span>  
  
```console  
cscript EnumerateServices.js  
```  
  
 <span data-ttu-id="5c0df-128">O script acessa a instrumentação contida no serviço e produz a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="5c0df-128">The script accesses the instrumentation contained in the service and produces the following output:</span></span>  
  
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
  
 <span data-ttu-id="5c0df-129">Em seguida, execute o segundo Script Java para exibir os dados WMI definidos pelo usuário:</span><span class="sxs-lookup"><span data-stu-id="5c0df-129">Next, run the second Java Script to display the user-defined WMI data:</span></span>  
  
```console  
cscript EnumerateCustomObjects.js  
```  
  
 <span data-ttu-id="5c0df-130">O script acessa a instrumentação definida pelo usuário contida nos serviços e produz a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="5c0df-130">The script accesses the user-defined instrumentation contained in the services and produces the following output:</span></span>  
  
```console
1 WMIObject(s) found.  
|-PID:           30285bfd-9d66-4c4e-9be2-310499c5cef5  
|-InstanceId:    3839  
|-WMIInfo:       User Defined WMI Information.  
```  
  
 <span data-ttu-id="5c0df-131">A saída mostra que há um único serviço em execução no computador.</span><span class="sxs-lookup"><span data-stu-id="5c0df-131">The output shows that there is a single service running on the computer.</span></span> <span data-ttu-id="5c0df-132">O serviço expõe um ponto final `ICalculator` que implementa o contrato.</span><span class="sxs-lookup"><span data-stu-id="5c0df-132">The service exposes one endpoint that implements the `ICalculator` contract.</span></span> <span data-ttu-id="5c0df-133">As configurações do comportamento e da vinculação que são implementadas até o ponto final são listadas como a soma de elementos individuais da pilha de mensagens.</span><span class="sxs-lookup"><span data-stu-id="5c0df-133">The settings of the behavior and binding that are implemented by the endpoint are listed as the sum of individual elements of the messaging stack.</span></span>  
  
 <span data-ttu-id="5c0df-134">O WMI não se limita a expor a instrumentação gerencial da infra-estrutura do WCF.</span><span class="sxs-lookup"><span data-stu-id="5c0df-134">WMI is not limited to exposing the management instrumentation of the WCF infrastructure.</span></span> <span data-ttu-id="5c0df-135">O aplicativo pode expor seus próprios itens de dados específicos de domínio através do mesmo mecanismo.</span><span class="sxs-lookup"><span data-stu-id="5c0df-135">The application can expose its own domain-specific data items through the same mechanism.</span></span> <span data-ttu-id="5c0df-136">WMI é um mecanismo unificado para inspeção e controle de um serviço Web.</span><span class="sxs-lookup"><span data-stu-id="5c0df-136">WMI is a unified mechanism for inspection and control of a Web service.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="5c0df-137">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="5c0df-137">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="5c0df-138">Certifique-se de ter realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5c0df-138">Ensure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="5c0df-139">Para construir a edição C# ou Visual Basic .NET da solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5c0df-139">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="5c0df-140">Publique o esquema de serviços para o WMI executando o InstallUtil.exe (os locais padrão para InstallUtil.exe é "%WINDIR%\Microsoft.NET\Framework\v4.0.30319") no arquivo service.dll no diretório de hospedagem.</span><span class="sxs-lookup"><span data-stu-id="5c0df-140">Publish the services schema to WMI by running the InstallUtil.exe (the default locations for InstallUtil.exe is "%WINDIR%\Microsoft.NET\Framework\v4.0.30319") on the service.dll file in the hosting directory.</span></span> <span data-ttu-id="5c0df-141">Esta etapa só precisa ser executada quando alterações forem feitas no arquivo service.dll.</span><span class="sxs-lookup"><span data-stu-id="5c0df-141">This step only needs to be executed when changes have been made to the service.dll file.</span></span>
  
4. <span data-ttu-id="5c0df-142">Para executar a amostra em uma configuração de computador único ou cruzado, siga as instruções em [Executar as amostras da Fundação](../../../../docs/framework/wcf/samples/running-the-samples.md)de Comunicação do Windows .</span><span class="sxs-lookup"><span data-stu-id="5c0df-142">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="5c0df-143">Se você instalou o WCF depois de instalar ASP.NET, talvez seja necessário executar "%WINDIR%\ Microsoft.Net\Framework\v3.0\Windows Communication Foundation\servicemodelreg.exe " -r -x para dar à conta ASPNET permissão para publicar objetos WMI.</span><span class="sxs-lookup"><span data-stu-id="5c0df-143">If you installed WCF after installing ASP.NET, you may need to run "%WINDIR%\ Microsoft.Net\Framework\v3.0\Windows Communication Foundation\servicemodelreg.exe " -r -x to give the ASPNET account permission to publish WMI objects.</span></span>  
  
5. <span data-ttu-id="5c0df-144">Exibir dados da amostra em sipor através `cscript EnumerateServices.js` do `cscript EnumerateCustomObjects.js`WMI usando os comandos: ou .</span><span class="sxs-lookup"><span data-stu-id="5c0df-144">View data from the sample surfaced through WMI by using the commands: `cscript EnumerateServices.js` or `cscript EnumerateCustomObjects.js`.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="5c0df-145">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="5c0df-145">The samples may already be installed on your computer.</span></span> <span data-ttu-id="5c0df-146">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="5c0df-146">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="5c0df-147">Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation).</span><span class="sxs-lookup"><span data-stu-id="5c0df-147">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5c0df-148">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="5c0df-148">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\WMIProvider`  
  
## <a name="see-also"></a><span data-ttu-id="5c0df-149">Confira também</span><span class="sxs-lookup"><span data-stu-id="5c0df-149">See also</span></span>

- <span data-ttu-id="5c0df-150">[AppFabric que monitora Exemplos](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="5c0df-150">[AppFabric Monitoring Samples](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span></span>
