---
title: Contadores de desempenho do WCF
ms.date: 03/30/2017
helpviewer_keywords:
- performance counters [WCF]
ms.assetid: f559b2bd-ed83-4988-97a1-e88f06646609
ms.openlocfilehash: a9bddcbd907e37d9bdf757b1999946c99e10440c
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855635"
---
# <a name="wcf-performance-counters"></a><span data-ttu-id="ab16d-102">Contadores de desempenho do WCF</span><span class="sxs-lookup"><span data-stu-id="ab16d-102">WCF Performance Counters</span></span>
<span data-ttu-id="ab16d-103">O Windows Communication Foundation (WCF) inclui um grande conjunto de contadores de desempenho para ajudá-lo a medir o desempenho do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ab16d-103">Windows Communication Foundation (WCF) includes a large set of performance counters to help you gauge your application's performance.</span></span>  
  
## <a name="enabling-performance-counters"></a><span data-ttu-id="ab16d-104">Habilitando contadores de desempenho</span><span class="sxs-lookup"><span data-stu-id="ab16d-104">Enabling Performance Counters</span></span>  
 <span data-ttu-id="ab16d-105">Você pode habilitar contadores de desempenho para um serviço WCF por meio do arquivo de configuração app. config do serviço WCF da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="ab16d-105">You can enable performance counters for a WCF service through the app.config configuration file of the WCF service as follows:</span></span>  
  
```xml  
<configuration>  
    <system.serviceModel>  
        <diagnostics performanceCounters="All" />  
    </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="ab16d-106">O `performanceCounters` atributo pode ser definido para habilitar um tipo específico de contadores de desempenho.</span><span class="sxs-lookup"><span data-stu-id="ab16d-106">The `performanceCounters` attribute can be set to enable a specific type of performance counters.</span></span> <span data-ttu-id="ab16d-107">Os valores válidos são</span><span class="sxs-lookup"><span data-stu-id="ab16d-107">Valid values are</span></span>  
  
- <span data-ttu-id="ab16d-108">Os Todos os contadores de categoria (ServiceModelService, ServiceModelEndpoint e ServiceModelOperation) estão habilitados.</span><span class="sxs-lookup"><span data-stu-id="ab16d-108">All: All category counters (ServiceModelService, ServiceModelEndpoint and ServiceModelOperation) are enabled.</span></span>  
  
- <span data-ttu-id="ab16d-109">Somente de: Somente os contadores de categoria ServiceModelService estão habilitados.</span><span class="sxs-lookup"><span data-stu-id="ab16d-109">ServiceOnly: Only ServiceModelService category counters are enabled.</span></span> <span data-ttu-id="ab16d-110">Este é o valor padrão.</span><span class="sxs-lookup"><span data-stu-id="ab16d-110">This is the default value.</span></span>  
  
- <span data-ttu-id="ab16d-111">Desconto Os contadores de desempenho ServiceModel \* estão desabilitados.</span><span class="sxs-lookup"><span data-stu-id="ab16d-111">Off: ServiceModel\* performance counters are disabled.</span></span>  
  
 <span data-ttu-id="ab16d-112">Se você quiser habilitar contadores de desempenho para todos os aplicativos WCF, poderá posicionar as definições de configuração no arquivo Machine. config.</span><span class="sxs-lookup"><span data-stu-id="ab16d-112">If you want to enable performance counters for all WCF applications, you can place the configuration settings in the Machine.config file.</span></span>  <span data-ttu-id="ab16d-113">Consulte a seção **aumentar tamanho da memória para contadores de desempenho** abaixo para obter mais informações sobre como configurar memória suficiente para contadores de desempenho em seu computador.</span><span class="sxs-lookup"><span data-stu-id="ab16d-113">Please see the **Increasing Memory Size for Performance Counters** section below for more information on configuring sufficient memory for performance counters on your machine.</span></span>  
  
 <span data-ttu-id="ab16d-114">Se você usar pontos de extensibilidade do WCF, como chamadores de operação personalizados, também deverá emitir seus próprios contadores de desempenho.</span><span class="sxs-lookup"><span data-stu-id="ab16d-114">If you use WCF extensibility points such as custom operation invokers, you should also emit your own performance counters.</span></span> <span data-ttu-id="ab16d-115">Isso ocorre porque, se você implementar um ponto de extensibilidade, o WCF poderá não emitir mais os dados do contador de desempenho padrão no caminho padrão.</span><span class="sxs-lookup"><span data-stu-id="ab16d-115">This is because if you implement an extensibility point, WCF may no longer emit the standard performance counter data in the default path.</span></span> <span data-ttu-id="ab16d-116">Se você não implementar o suporte de contador de desempenho manual, talvez não veja os dados do contador de desempenho que espera.</span><span class="sxs-lookup"><span data-stu-id="ab16d-116">If you do not implement manual performance counter support, you may not see the performance counter data you expect.</span></span>  
  
 <span data-ttu-id="ab16d-117">Você também pode habilitar contadores de desempenho em seu código da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="ab16d-117">You can also enable performance counters in your code as follows,</span></span>  
  
```csharp
using System.Configuration;  
using System.ServiceModel.Configuration;  
using System.ServiceModel.Diagnostics;  
Configuration config = ConfigurationManager.OpenExeConfiguration(  
    ConfigurationUserLevel.None);  
ServiceModelSectionGroup sg = ServiceModelSectionGroup.GetSectionGroup(config);  
sg.Diagnostic.PerformanceCounters = PerformanceCounterScope.All;  
config.Save();  
```  
  
## <a name="viewing-performance-data"></a><span data-ttu-id="ab16d-118">Exibindo dados de desempenho</span><span class="sxs-lookup"><span data-stu-id="ab16d-118">Viewing Performance Data</span></span>  
 <span data-ttu-id="ab16d-119">Para exibir os dados capturados pelos contadores de desempenho, você pode usar o monitor de desempenho (Perfmon. exe) fornecido com o Windows.</span><span class="sxs-lookup"><span data-stu-id="ab16d-119">To view data captured by the performance counters, you can use the Performance Monitor (Perfmon.exe) that comes with Windows.</span></span> <span data-ttu-id="ab16d-120">Você pode iniciar essa ferramenta acessando **Iniciar**e, em seguida, clique `perfmon.exe` em executar e digite na caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="ab16d-120">You can launch this tool by going to **Start**, and click **Run** and type `perfmon.exe` in the dialog box.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ab16d-121">As instâncias do contador de desempenho podem ser liberadas antes que as últimas mensagens sejam processadas pelo dispatcher do ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="ab16d-121">Performance counter instances may be released before the last messages have been processed by the endpoint dispatcher.</span></span> <span data-ttu-id="ab16d-122">Isso pode fazer com que os dados de desempenho não sejam capturados para algumas mensagens.</span><span class="sxs-lookup"><span data-stu-id="ab16d-122">This can result in performance data not being captured for a few messages.</span></span>  
  
## <a name="increasing-memory-size-for-performance-counters"></a><span data-ttu-id="ab16d-123">Aumentando o tamanho da memória para contadores de desempenho</span><span class="sxs-lookup"><span data-stu-id="ab16d-123">Increasing Memory Size for Performance Counters</span></span>  
 <span data-ttu-id="ab16d-124">O WCF usa memória compartilhada separada para suas categorias de contador de desempenho.</span><span class="sxs-lookup"><span data-stu-id="ab16d-124">WCF uses separate shared memory for its performance counter categories.</span></span>  
  
 <span data-ttu-id="ab16d-125">Por padrão, a memória compartilhada separada é definida como um trimestre do tamanho da memória do contador de desempenho global.</span><span class="sxs-lookup"><span data-stu-id="ab16d-125">By default, separate shared memory is set to a quarter the size of global performance counter memory.</span></span> <span data-ttu-id="ab16d-126">A memória padrão do contador de desempenho global é de 524.288 bytes.</span><span class="sxs-lookup"><span data-stu-id="ab16d-126">The default global performance counter memory is 524,288 bytes.</span></span> <span data-ttu-id="ab16d-127">Portanto, as três categorias de contador de desempenho do WCF têm um tamanho padrão de aproximadamente 128KB cada.</span><span class="sxs-lookup"><span data-stu-id="ab16d-127">Therefore, the three WCF performance counter categories have a default size of approximately 128KB each.</span></span> <span data-ttu-id="ab16d-128">Dependendo das características de tempo de execução dos aplicativos WCF em um computador, a memória do contador de desempenho pode ser esgotada.</span><span class="sxs-lookup"><span data-stu-id="ab16d-128">Depending upon the runtime characteristics of the WCF applications on a machine, performance counter memory may be exhausted.</span></span> <span data-ttu-id="ab16d-129">Quando isso acontece, o WCF grava um erro no log de eventos do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ab16d-129">When this happens, WCF writes an error to the application event log.</span></span> <span data-ttu-id="ab16d-130">O conteúdo do erro informa que um contador de desempenho não foi carregado e a entrada contém a exceção "System. InvalidOperationException: A exibição do arquivo de contadores personalizados está sem memória. "</span><span class="sxs-lookup"><span data-stu-id="ab16d-130">The content of the error states that a performance counter was not loaded, and the entry contains the exception "System.InvalidOperationException: Custom counters file view is out of memory."</span></span> <span data-ttu-id="ab16d-131">Se o rastreamento estiver habilitado no nível de erro, essa falha também será rastreada.</span><span class="sxs-lookup"><span data-stu-id="ab16d-131">If tracing is enabled at the error level, this failure is also traced.</span></span> <span data-ttu-id="ab16d-132">Se a memória do contador de desempenho estiver esgotada, continuar a executar seus aplicativos WCF com os contadores de desempenho habilitado pode resultar em degradação do desempenho.</span><span class="sxs-lookup"><span data-stu-id="ab16d-132">If performance counter memory is exhausted, continuing to run your WCF applications with performance counters enabled could result in performance degradation.</span></span> <span data-ttu-id="ab16d-133">Se você for um administrador do computador, deverá configurá-lo para alocar memória suficiente para dar suporte ao número máximo de contadores de desempenho que podem existir a qualquer momento.</span><span class="sxs-lookup"><span data-stu-id="ab16d-133">If you are an administrator of the machine, you should configure it to allocate enough memory to support the maximum number of performance counters that can exist at any time.</span></span>  
  
 <span data-ttu-id="ab16d-134">Você pode alterar a quantidade de memória do contador de desempenho para categorias do WCF no registro.</span><span class="sxs-lookup"><span data-stu-id="ab16d-134">You can change the amount of performance counter memory for WCF categories in the registry.</span></span> <span data-ttu-id="ab16d-135">Para fazer isso, você precisa adicionar um novo valor DWORD chamado `FileMappingSize` aos três locais a seguir e defini-lo como o valor desejado em bytes.</span><span class="sxs-lookup"><span data-stu-id="ab16d-135">To do so, you need to add a new DWORD value named `FileMappingSize` to the three following locations, and set it to the desired value in bytes.</span></span> <span data-ttu-id="ab16d-136">Reinicialize o computador para que essas alterações sejam levadas em vigor.</span><span class="sxs-lookup"><span data-stu-id="ab16d-136">Reboot your machine so that these changes are taken into effect.</span></span>  
  
- <span data-ttu-id="ab16d-137">HKLM\System\CurrentControlSet\Services\ServiceModelEndpoint 4.0.0.0 \ desempenho</span><span class="sxs-lookup"><span data-stu-id="ab16d-137">HKLM\System\CurrentControlSet\Services\ServiceModelEndpoint 4.0.0.0\Performance</span></span>  
  
- <span data-ttu-id="ab16d-138">HKLM\System\CurrentControlSet\Services\ServiceModelOperation 4.0.0.0 \ desempenho</span><span class="sxs-lookup"><span data-stu-id="ab16d-138">HKLM\System\CurrentControlSet\Services\ServiceModelOperation 4.0.0.0\Performance</span></span>  
  
- <span data-ttu-id="ab16d-139">HKLM\System\CurrentControlSet\Services\ServiceModelService 4.0.0.0 \ desempenho</span><span class="sxs-lookup"><span data-stu-id="ab16d-139">HKLM\System\CurrentControlSet\Services\ServiceModelService 4.0.0.0\Performance</span></span>  
  
 <span data-ttu-id="ab16d-140">Quando um grande número de objetos (por exemplo, ServiceHost) é Descartado, mas aguardando para ser coletado pelo lixo `PrivateBytes` , o contador de desempenho registrará um número excepcionalmente alto.</span><span class="sxs-lookup"><span data-stu-id="ab16d-140">When a large number of objects (for example, ServiceHost) are disposed of but waiting to be garbage-collected, the `PrivateBytes` performance counter will register an unusually high number.</span></span> <span data-ttu-id="ab16d-141">Para resolver esse problema, você pode adicionar seus próprios contadores específicos do aplicativo ou usar o `performanceCounters` atributo para habilitar somente contadores de nível de serviço.</span><span class="sxs-lookup"><span data-stu-id="ab16d-141">To resolve this problem, you can either add your own application-specific counters, or use the `performanceCounters` attribute to enable only service-level counters.</span></span>  
  
## <a name="types-of-performance-counters"></a><span data-ttu-id="ab16d-142">Tipos de contadores de desempenho</span><span class="sxs-lookup"><span data-stu-id="ab16d-142">Types of Performance Counters</span></span>  
 <span data-ttu-id="ab16d-143">Os contadores de desempenho têm como escopo três níveis diferentes: Serviço, ponto de extremidade e operação.</span><span class="sxs-lookup"><span data-stu-id="ab16d-143">Performance counters are scoped to three different levels: Service, Endpoint and Operation.</span></span>  
  
 <span data-ttu-id="ab16d-144">Você pode usar o WMI para recuperar o nome de uma instância do contador de desempenho.</span><span class="sxs-lookup"><span data-stu-id="ab16d-144">You can use WMI to retrieve the name of a performance counter instance.</span></span> <span data-ttu-id="ab16d-145">Por exemplo,</span><span class="sxs-lookup"><span data-stu-id="ab16d-145">For example,</span></span>  
  
- <span data-ttu-id="ab16d-146">O nome da instância do contador de serviço pode ser obtido por meio da propriedade "referendaname" da instância do [serviço](../../../../../docs/framework/wcf/diagnostics/wmi/service.md) WMI.</span><span class="sxs-lookup"><span data-stu-id="ab16d-146">Service counter instance name can be obtained through WMI [Service](../../../../../docs/framework/wcf/diagnostics/wmi/service.md) instance's "CounterInstanceName" property.</span></span>  
  
- <span data-ttu-id="ab16d-147">O nome da instância do contador de ponto de extremidade pode ser obtido por meio da propriedade "referendaname" da instância do [ponto de extremidade](../../../../../docs/framework/wcf/diagnostics/wmi/endpoint.md) do WMI.</span><span class="sxs-lookup"><span data-stu-id="ab16d-147">Endpoint counter instance name can be obtained through WMI [Endpoint](../../../../../docs/framework/wcf/diagnostics/wmi/endpoint.md) instance's "CounterInstanceName" property.</span></span>  
  
- <span data-ttu-id="ab16d-148">O nome da instância do contador de operações pode ser obtido por meio do método "GetOperationCounterInstanceName" da instância do [ponto de extremidade](../../../../../docs/framework/wcf/diagnostics/wmi/endpoint.md) do WMI.</span><span class="sxs-lookup"><span data-stu-id="ab16d-148">Operation counter instance name can be obtained through WMI [Endpoint](../../../../../docs/framework/wcf/diagnostics/wmi/endpoint.md) instance's "GetOperationCounterInstanceName" method.</span></span>  
  
 <span data-ttu-id="ab16d-149">Para obter mais informações sobre o WMI, consulte [usando instrumentação de gerenciamento do Windows para diagnóstico](../../../../../docs/framework/wcf/diagnostics/wmi/index.md).</span><span class="sxs-lookup"><span data-stu-id="ab16d-149">For more information on WMI, see [Using Windows Management Instrumentation for Diagnostics](../../../../../docs/framework/wcf/diagnostics/wmi/index.md).</span></span>  
  
### <a name="service-performance-counters"></a><span data-ttu-id="ab16d-150">Contadores de desempenho de serviço</span><span class="sxs-lookup"><span data-stu-id="ab16d-150">Service performance counters</span></span>  
 <span data-ttu-id="ab16d-151">Os contadores de desempenho de serviço medem o comportamento do serviço como um todo e podem ser usados para diagnosticar o desempenho do serviço inteiro.</span><span class="sxs-lookup"><span data-stu-id="ab16d-151">Service performance counters measure the service behavior as a whole and can be used to diagnose the performance of the whole service.</span></span> <span data-ttu-id="ab16d-152">Eles podem ser encontrados no objeto `ServiceModelService 4.0.0.0` de desempenho ao exibir com o monitor de desempenho.</span><span class="sxs-lookup"><span data-stu-id="ab16d-152">They can be found under the `ServiceModelService 4.0.0.0` performance object when viewing with Performance Monitor.</span></span> <span data-ttu-id="ab16d-153">As instâncias são nomeadas usando o seguinte padrão:</span><span class="sxs-lookup"><span data-stu-id="ab16d-153">The instances are named using the following pattern:</span></span>  
  
`ServiceName@ServiceBaseAddress`
  
 <span data-ttu-id="ab16d-154">Um contador em um escopo de serviço é agregado do contador em uma coleção de pontos de extremidade.</span><span class="sxs-lookup"><span data-stu-id="ab16d-154">A counter in a service scope is aggregated from counter in a collection of endpoints.</span></span>  
  
 <span data-ttu-id="ab16d-155">Os contadores de desempenho para a criação da instância de serviço são incrementados quando um novo InstanceContext é criado.</span><span class="sxs-lookup"><span data-stu-id="ab16d-155">Performance counters for service instance creation are incremented when a new InstanceContext is created.</span></span> <span data-ttu-id="ab16d-156">Observe que um novo InstanceContext é criado mesmo quando você recebe uma mensagem que não está sendo ativada (com um serviço existente) ou quando você se conecta a uma instância de uma sessão, encerra a sessão e, em seguida, reconecta a partir de outra sessão.</span><span class="sxs-lookup"><span data-stu-id="ab16d-156">Note that a new InstanceContext is created even when you receive a non-activating message (with an existing service), or when you connect to an instance from one session, end the session, and then reconnect from another session.</span></span>  
  
### <a name="endpoint-performance-counters"></a><span data-ttu-id="ab16d-157">Contadores de desempenho de ponto de extremidade</span><span class="sxs-lookup"><span data-stu-id="ab16d-157">Endpoint performance counters</span></span>  
 <span data-ttu-id="ab16d-158">Os contadores de desempenho do ponto de extremidade permitem que você examine os dados que refletem como um ponto de extremidade está aceitando mensagens.</span><span class="sxs-lookup"><span data-stu-id="ab16d-158">Endpoint performance counters enable you to look at data reflecting how an endpoint is accepting messages.</span></span> <span data-ttu-id="ab16d-159">Eles podem ser encontrados no objeto `ServiceModelEndpoint 4.0.0.0` de desempenho ao exibir usando o monitor de desempenho.</span><span class="sxs-lookup"><span data-stu-id="ab16d-159">They can be found under the `ServiceModelEndpoint 4.0.0.0` performance object when viewing using the Performance Monitor.</span></span> <span data-ttu-id="ab16d-160">As instâncias são nomeadas usando o seguinte padrão:</span><span class="sxs-lookup"><span data-stu-id="ab16d-160">The instances are named using the following pattern:</span></span>  
  
`(ServiceName).(ContractName)@(endpoint listener address)`
  
 <span data-ttu-id="ab16d-161">Os dados são semelhantes ao que é coletado para operações individuais, mas é agregado somente no ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="ab16d-161">The data is similar to what is collected for individual operations, but is only aggregated across the endpoint.</span></span>  
  
 <span data-ttu-id="ab16d-162">Um contador em um escopo de ponto de extremidade é agregado dos contadores em uma coleção de operações.</span><span class="sxs-lookup"><span data-stu-id="ab16d-162">A counter in an endpoint scope is aggregated from counters in a collection of operations.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ab16d-163">Se dois pontos de extremidade tiverem nomes de contrato e endereços idênticos, eles serão mapeados para a mesma instância do contador.</span><span class="sxs-lookup"><span data-stu-id="ab16d-163">If two endpoints have identical contract names and addresses, they are mapped to the same counter instance.</span></span>  
  
### <a name="operation-performance-counters"></a><span data-ttu-id="ab16d-164">Contadores de desempenho de operação</span><span class="sxs-lookup"><span data-stu-id="ab16d-164">Operation performance counters</span></span>  
 <span data-ttu-id="ab16d-165">Os contadores de desempenho de operação são `ServiceModelOperation 4.0.0.0` encontrados no objeto de desempenho ao exibir com o monitor de desempenho.</span><span class="sxs-lookup"><span data-stu-id="ab16d-165">Operation performance counters are found under the `ServiceModelOperation 4.0.0.0` performance object when viewing with the Performance Monitor.</span></span> <span data-ttu-id="ab16d-166">Cada operação tem uma instância individual.</span><span class="sxs-lookup"><span data-stu-id="ab16d-166">Each operation has an individual instance.</span></span> <span data-ttu-id="ab16d-167">Ou seja, se um determinado contrato tiver 10 operações, 10 instâncias do contador de operações serão associadas a esse contrato.</span><span class="sxs-lookup"><span data-stu-id="ab16d-167">That is, if a given contract has 10 operations, 10 operation counter instances are associated with that contract.</span></span> <span data-ttu-id="ab16d-168">As instâncias de objeto são nomeadas usando o seguinte padrão:</span><span class="sxs-lookup"><span data-stu-id="ab16d-168">The object instances are named using the following pattern:</span></span>  
  
`(ServiceName).(ContractName).(OperationName)@(first endpoint listener address)`
  
 <span data-ttu-id="ab16d-169">Esse contador permite que você meça como a chamada está sendo usada e o quão bem a operação está sendo executada.</span><span class="sxs-lookup"><span data-stu-id="ab16d-169">This counter enables you to measure how the call is being used and how well the operation is performing.</span></span>  
  
 <span data-ttu-id="ab16d-170">Quando os contadores são visíveis em vários escopos, os dados coletados de um escopo superior são agregados com dados de escopos inferiores.</span><span class="sxs-lookup"><span data-stu-id="ab16d-170">When counters are visible at multiple scopes, data gathered from a higher scope are aggregated with data from lower scopes.</span></span> <span data-ttu-id="ab16d-171">Por exemplo, `Calls` em um ponto de extremidade representa a soma de todas as chamadas de operação dentro do ponto de extremidade; `Calls` em um serviço representa a soma de todas as chamadas para todos os pontos de extremidade no serviço.</span><span class="sxs-lookup"><span data-stu-id="ab16d-171">For example, `Calls` at an endpoint represents the sum of all operation calls within the endpoint; `Calls` at a service represents the sum of all calls to all endpoints within the service.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ab16d-172">Se você tiver nomes de operação duplicados em um contrato, você só obterá uma instância de contador para ambas as operações.</span><span class="sxs-lookup"><span data-stu-id="ab16d-172">If you have duplicate operation names on a contract, you only get one counter instances for both operations.</span></span>  
  
## <a name="programming-the-wcf-performance-counters"></a><span data-ttu-id="ab16d-173">Programando os contadores de desempenho do WCF</span><span class="sxs-lookup"><span data-stu-id="ab16d-173">Programming the WCF Performance Counters</span></span>  
 <span data-ttu-id="ab16d-174">Vários arquivos são instalados na pasta de instalação do SDK para que você possa acessar os contadores de desempenho do WCF programaticamente.</span><span class="sxs-lookup"><span data-stu-id="ab16d-174">Several files are installed in the SDK install folder so that you can access the WCF performance counters programmatically.</span></span> <span data-ttu-id="ab16d-175">Esses arquivos são listados da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="ab16d-175">These files are listed as follows.</span></span>  
  
- <span data-ttu-id="ab16d-176">_ServiceModelEndpointPerfCounters.vrg</span><span class="sxs-lookup"><span data-stu-id="ab16d-176">_ServiceModelEndpointPerfCounters.vrg</span></span>  
  
- <span data-ttu-id="ab16d-177">_ServiceModelOperationPerfCounters.vrg</span><span class="sxs-lookup"><span data-stu-id="ab16d-177">_ServiceModelOperationPerfCounters.vrg</span></span>  
  
- <span data-ttu-id="ab16d-178">_ServiceModelServicePerfCounters.vrg</span><span class="sxs-lookup"><span data-stu-id="ab16d-178">_ServiceModelServicePerfCounters.vrg</span></span>  
  
- <span data-ttu-id="ab16d-179">_SMSvcHostPerfCounters.vrg</span><span class="sxs-lookup"><span data-stu-id="ab16d-179">_SMSvcHostPerfCounters.vrg</span></span>  
  
- <span data-ttu-id="ab16d-180">_TransactionBridgePerfCounters.vrg</span><span class="sxs-lookup"><span data-stu-id="ab16d-180">_TransactionBridgePerfCounters.vrg</span></span>  
  
 <span data-ttu-id="ab16d-181">Para obter mais informações sobre como acessar os contadores programaticamente, consulte [arquitetura de programação de contador de desempenho](https://go.microsoft.com/fwlink/?LinkId=95179).</span><span class="sxs-lookup"><span data-stu-id="ab16d-181">For more information on how to access the counters programmatically, see [Performance Counter Programming Architecture](https://go.microsoft.com/fwlink/?LinkId=95179).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab16d-182">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ab16d-182">See also</span></span>

- [<span data-ttu-id="ab16d-183">Administração e diagnósticos</span><span class="sxs-lookup"><span data-stu-id="ab16d-183">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
