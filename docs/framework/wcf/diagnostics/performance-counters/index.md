---
title: Contadores de desempenho do WCF
ms.date: 03/30/2017
helpviewer_keywords:
- performance counters [WCF]
ms.assetid: f559b2bd-ed83-4988-97a1-e88f06646609
ms.openlocfilehash: d0ad7ee0bc3ea1d15197e6b8d9888d60b21a2f15
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48032682"
---
# <a name="wcf-performance-counters"></a>Contadores de desempenho do WCF
Windows Communication Foundation (WCF) inclui um grande conjunto de contadores de desempenho para ajudá-lo a medir o desempenho do seu aplicativo.  
  
## <a name="enabling-performance-counters"></a>Habilitar os contadores de desempenho  
 Você pode habilitar os contadores de desempenho para um serviço WCF por meio do arquivo de configuração App. config do serviço WCF da seguinte maneira:  
  
```xml  
<configuration>  
    <system.serviceModel>  
        <diagnostics performanceCounters="All" />  
    </system.serviceModel>  
</configuration>  
```  
  
 O `performanceCounters` atributo pode ser definido para habilitar um tipo específico de contadores de desempenho. Os valores válidos são  
  
-   All: Todos os contadores de categoria (ServiceModelService, ServiceModelEndpoint e ServiceModelOperation) estão habilitados.  
  
-   ServiceOnly: Somente contadores de categoria ServiceModelService estão habilitados. Este é o valor padrão.  
  
-   Off: Contadores de desempenho do ServiceModel * estão desabilitados.  
  
 Se você quiser habilitar os contadores de desempenho para todos os aplicativos do WCF, você pode colocar as definições de configuração no arquivo Machine. config.  Consulte a **aumentando o tamanho de memória para contadores de desempenho** seção abaixo para obter mais informações sobre como configurar a memória suficiente para contadores de desempenho em seu computador.  
  
 Se você usar pontos de extensibilidade do WCF, como chamadores de operação personalizado, você também deve emitir seus próprios contadores de desempenho. Isso ocorre porque se você implementar um ponto de extensibilidade, o WCF não pode emitir os dados do contador de desempenho padrão no caminho padrão. Se você não implementar o suporte de contador de desempenho manual, você não poderá ver os dados de contador de desempenho esperados.  
  
 Você também pode habilitar os contadores de desempenho em seu código da seguinte maneira  
  
```  
using System.Configuration;  
using System.ServiceModel.Configuration;  
using System.ServiceModel.Diagnostics;  
Configuration config = ConfigurationManager.OpenExeConfiguration(  
    ConfigurationUserLevel.None);  
ServiceModelSectionGroup sg = ServiceModelSectionGroup.GetSectionGroup(config);  
sg.Diagnostic.PerformanceCounters = PerformanceCounterScope.All;  
config.Save();  
```  
  
## <a name="viewing-performance-data"></a>Exibindo dados de desempenho  
 Para exibir os dados capturados pelos contadores de desempenho, você pode usar o Monitor de desempenho (Perfmon.exe) que acompanha o Windows. Você pode iniciar essa ferramenta, vá para **inicie**e clique em **execute** e digite `perfmon.exe` na caixa de diálogo.  
  
> [!NOTE]
>  Instâncias de contador de desempenho poderão ser liberadas antes que o último mensagens foram processadas pelo dispatcher do ponto de extremidade. Isso pode resultar em dados de desempenho não são capturados para algumas mensagens.  
  
## <a name="increasing-memory-size-for-performance-counters"></a>Aumentando o tamanho da memória para contadores de desempenho  
 WCF usa a memória compartilhada separada para suas categorias de contador de desempenho.  
  
 Por padrão, memória compartilhada separada é definida como um quarto do tamanho da memória do contador de desempenho global. A memória de contador de desempenho global padrão é 524.288 bytes. Portanto, as três categorias de contador de desempenho do WCF têm um tamanho padrão de aproximadamente 128KB cada. Dependendo as características de tempo de execução de aplicativos WCF em um computador, memória de contador de desempenho pode ser esgotada. Quando isso acontece, o WCF grava um erro no log de eventos do aplicativo. O conteúdo do erro informa que um contador de desempenho não foi carregado, e a entrada contém a exceção "System. InvalidOperationException: modo de exibição de arquivo de contadores personalizado está sem memória." Se o rastreamento está habilitado no nível de erro, essa falha também é rastreada. Se a memória de contador de desempenho é esgotada, continuando a executar seus aplicativos do WCF com contadores de desempenho habilitados pode resultar em degradação de desempenho. Se você for um administrador da máquina, você deve configurá-lo para alocar memória suficiente para suportar o número máximo de contadores de desempenho que podem existir em qualquer momento.  
  
 Você pode alterar a quantidade de memória do contador de desempenho para as categorias WCF no registro. Para fazer isso, você precisará adicionar um novo valor DWORD chamado `FileMappingSize` para os três locais a seguir e defina-o como o valor desejado em bytes. Reinicie o computador para que essas alterações são levadas em efeito.  
  
-   HKLM\System\CurrentControlSet\Services\ServiceModelEndpoint 4.0.0.0\Performance  
  
-   HKLM\System\CurrentControlSet\Services\ServiceModelOperation 4.0.0.0\Performance  
  
-   HKLM\System\CurrentControlSet\Services\ServiceModelService 4.0.0.0\Performance  
  
 Quando um grande número de objetos (por exemplo, o ServiceHost) sejam descartado, mas esperando para ser coletado como lixo, o `PrivateBytes` contador de desempenho serão registrados em um número extraordinariamente alto. Para resolver esse problema, você pode adicionar seus próprios contadores específicos do aplicativo, ou usar o `performanceCounters` atributo para habilitar os contadores apenas do nível de serviço.  
  
## <a name="types-of-performance-counters"></a>Tipos de contadores de desempenho  
 Contadores de desempenho estão no escopo para três níveis diferentes: serviço, o ponto de extremidade e a operação.  
  
 Você pode usar o WMI para recuperar o nome de uma instância do contador de desempenho. Por exemplo,  
  
-   Nome de instância do contador de serviço pode ser obtido por meio do WMI [serviço](../../../../../docs/framework/wcf/diagnostics/wmi/service.md) propriedade de "CounterInstanceName" da instância.  
  
-   Nome de instância de contador do ponto de extremidade pode ser obtido por meio do WMI [ponto de extremidade](../../../../../docs/framework/wcf/diagnostics/wmi/endpoint.md) propriedade de "CounterInstanceName" da instância.  
  
-   Nome de instância do contador de operação pode ser obtido por meio do WMI [ponto de extremidade](../../../../../docs/framework/wcf/diagnostics/wmi/endpoint.md) "GetOperationCounterInstanceName" de método instância do.  
  
 Para obter mais informações sobre WMI, consulte [usando o Windows Management Instrumentation para diagnóstico](../../../../../docs/framework/wcf/diagnostics/wmi/index.md).  
  
### <a name="service-performance-counters"></a>Contadores de desempenho do serviço  
 Contadores de desempenho serviço medem o comportamento de serviço como um todo e podem ser usados para diagnosticar o desempenho do serviço inteiro. Eles podem ser encontrados no `ServiceModelService 4.0.0.0` objeto de desempenho durante a exibição com o Monitor de desempenho. As instâncias são nomeadas usando o seguinte padrão:  
  
```  
ServiceName@ServiceBaseAddress  
```  
  
 Um contador em um escopo de serviço é agregado do contador em uma coleção de pontos de extremidade.  
  
 Contadores de desempenho para criação de instância de serviço são incrementados quando um novo InstanceContext é criado. Observe que um novo InstanceContext é criado até mesmo quando você receber uma mensagem não ativando (com um serviço existente), ou quando você se conectar a uma instância de uma sessão, encerra a sessão e, em seguida, reconectar-se de outra sessão.  
  
### <a name="endpoint-performance-counters"></a>Contadores de desempenho do ponto de extremidade  
 Contadores de desempenho do ponto de extremidade permitem que você examinar dados refletindo como um ponto de extremidade é aceitar mensagens. Eles podem ser encontrados no `ServiceModelEndpoint 4.0.0.0` objeto de desempenho durante a exibição usando o Monitor de desempenho. As instâncias são nomeadas usando o seguinte padrão:  
  
```  
(ServiceName).(ContractName)@(endpoint listener address)  
```  
  
 Os dados são semelhantes a que é coletado para operações individuais, mas só é agregado entre o ponto de extremidade.  
  
 Um contador em um escopo de ponto de extremidade é agregado dos contadores em uma coleção de operações.  
  
> [!NOTE]
>  Se dois pontos de extremidade tem endereços e nomes de contrato idênticos, eles são mapeados para a mesma instância do contador.  
  
### <a name="operation-performance-counters"></a>Contadores de desempenho de operação  
 Contadores de desempenho da operação estiverem localizados no `ServiceModelOperation 4.0.0.0` objeto de desempenho durante a exibição com o Monitor de desempenho. Cada operação tem uma instância individual. Ou seja, se um determinado contrato tem 10 operações, 10 instâncias de contador de operação são associadas esse contrato. As instâncias de objeto são nomeadas usando o seguinte padrão:  
  
```  
(ServiceName).(ContractName).(OperationName)@(first endpoint listener address)  
```  
  
 Esse contador permite medir como a chamada está sendo usada e como a operação está sendo executado.  
  
 Quando contadores estão visíveis em vários escopos, os dados coletados de um escopo superior são agregados com os dados dos escopos menores. Por exemplo, `Calls` em um ponto de extremidade representa a soma de todas as chamadas de operação no ponto de extremidade. `Calls` em um serviço representa a soma de todas as chamadas para todos os pontos de extremidade dentro do serviço.  
  
> [!NOTE]
>  Se você tiver nomes de operação duplicadas em um contrato, você somente obtém uma instância do contador para ambas as operações.  
  
## <a name="programming-the-wcf-performance-counters"></a>Os contadores de desempenho do WCF de programação  
 Vários arquivos são instalados na pasta de instalação do SDK para que você possa acessar os contadores de desempenho do WCF por meio de programação. Esses arquivos são listados a seguir.  
  
-   _ServiceModelEndpointPerfCounters.vrg  
  
-   _ServiceModelOperationPerfCounters.vrg  
  
-   _ServiceModelServicePerfCounters.vrg  
  
-   _SMSvcHostPerfCounters.vrg  
  
-   _TransactionBridgePerfCounters.vrg  
  
 Para obter mais informações sobre como acessar os contadores de forma programática, consulte [arquitetura de programação de contador de desempenho](https://go.microsoft.com/fwlink/?LinkId=95179).  
  
## <a name="see-also"></a>Consulte também  
 [Administração e diagnósticos](../../../../../docs/framework/wcf/diagnostics/index.md)
