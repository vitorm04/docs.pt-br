---
title: Contadores de desempenho do WCF
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- performance counters [WCF]
ms.assetid: f559b2bd-ed83-4988-97a1-e88f06646609
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: be4ffac8444f6365dacb2b20db6abbb6792c2239
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="wcf-performance-counters"></a>Contadores de desempenho do WCF
[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]inclui um grande conjunto de contadores de desempenho para ajudá-lo a avaliar o desempenho do aplicativo.  
  
## <a name="enabling-performance-counters"></a>Habilitar contadores de desempenho  
 Você pode habilitar os contadores de desempenho para um [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] serviço por meio do arquivo de configuração App. config do [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] de serviço da seguinte maneira:  
  
```xml  
<configuration>  
    <system.serviceModel>  
        <diagnostics performanceCounters="All" />  
    </system.serviceModel>  
</configuration>  
```  
  
 O `performanceCounters` atributo pode ser definido para habilitar um tipo específico de contadores de desempenho. Os valores válidos são  
  
-   Todos: Todos os contadores de categoria (ServiceModelService, ServiceModelEndpoint e ServiceModelOperation) estão habilitados.  
  
-   ServiceOnly: Somente contadores de categoria de ServiceModelService estão habilitados. Este é o valor padrão.  
  
-   Off: Os contadores de desempenho do ServiceModel * são desabilitados.  
  
 Se você deseja habilitar os contadores de desempenho para todos os [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] aplicativos, você pode colocar as definições de configuração no arquivo Machine. config.  Consulte o **aumentando o tamanho de memória para contadores de desempenho** seção abaixo para obter mais informações sobre como configurar a memória suficiente para contadores de desempenho em seu computador.  
  
 Se você usar [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] pontos de extensibilidade, como chamadores de operação personalizado, você deve também emitir seus próprios contadores de desempenho. Isso ocorre porque se você implementar um ponto de extensibilidade, [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] não pode emitir os dados do contador de desempenho padrão no caminho padrão. Se você não implementa o suporte de contador de desempenho manual, você não verá os dados de contador de desempenho esperados.  
  
 Você também pode habilitar os contadores de desempenho no seu código seguinte:  
  
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
  
## <a name="viewing-performance-data"></a>Exibir dados de desempenho  
 Para exibir os dados capturados por contadores de desempenho, você pode usar o Monitor de desempenho (Perfmon.exe) que vem com o Windows. Você pode iniciar essa ferramenta indo para **iniciar**e clique em **executar** e digite `perfmon.exe` na caixa de diálogo.  
  
> [!NOTE]
>  Instâncias do contador de desempenho podem ser liberadas antes das últimas mensagens foram processadas pelo dispatcher do ponto de extremidade. Isso pode resultar em dados de desempenho não são capturados para algumas mensagens.  
  
## <a name="increasing-memory-size-for-performance-counters"></a>Aumentando o tamanho de memória para contadores de desempenho  
 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]usa separar memória compartilhada para suas categorias de contador de desempenho.  
  
 Por padrão, separado de memória compartilhada é definida como um quarto do tamanho da memória do contador de desempenho global. A memória de contador de desempenho global padrão é 524.288 bytes. Portanto, os três [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] categorias de contador de desempenho têm um tamanho padrão de aproximadamente 128 KB cada. Dependendo das características tempo de execução do [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] aplicativos em um computador, a memória de contador de desempenho podem ser esgotados. Quando isso acontece, [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] grava um erro no log de eventos do aplicativo. O conteúdo do erro informa que um contador de desempenho não foi carregado, e a entrada contém a exceção "System. InvalidOperationException: modo de exibição de arquivo de contadores personalizados está esgotada." Se o rastreamento estiver habilitado no nível de erro, essa falha também é rastreada. Se a memória de contador de desempenho é esgotada, continuando a executar sua [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] aplicativos com contadores de desempenho ativados podem resultar em degradação do desempenho. Se você for um administrador do computador, você deve configurá-lo para alocar memória suficiente para suportar o número máximo de contadores de desempenho que podem existir a qualquer momento.  
  
 Você pode alterar a quantidade de memória do contador de desempenho para [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] categorias no registro. Para fazer isso, você precisa adicionar um novo valor DWORD chamado `FileMappingSize` para três locais a seguir e defina-o como o valor desejado em bytes. Reinicialize o computador para que essas alterações são levadas em vigor.  
  
-   HKLM\System\CurrentControlSet\Services\ServiceModelEndpoint 4.0.0.0\Performance  
  
-   HKLM\System\CurrentControlSet\Services\ServiceModelOperation 4.0.0.0\Performance  
  
-   HKLM\System\CurrentControlSet\Services\ServiceModelService 4.0.0.0\Performance  
  
 Quando um grande número de objetos (por exemplo, ServiceHost) é descartado, mas esperando para ser coletado como lixo, a `PrivateBytes` contador de desempenho registrará um número extraordinariamente alto. Para resolver esse problema, você pode adicionar seus próprios contadores específicos do aplicativo, ou usar o `performanceCounters` atributo para habilitar os contadores de nível de serviço somente.  
  
## <a name="types-of-performance-counters"></a>Tipos de contadores de desempenho  
 Contadores de desempenho têm como escopo três níveis diferentes: serviço, o ponto de extremidade e a operação.  
  
 Você pode usar o WMI para recuperar o nome de uma instância de contador de desempenho. Por exemplo,  
  
-   Nome de instância do contador de serviço pode ser obtido por meio do WMI [Service](../../../../../docs/framework/wcf/diagnostics/wmi/service.md) propriedade de "CounterInstanceName" da instância.  
  
-   Nome de instância de contador do ponto de extremidade pode ser obtido por meio do WMI [ponto de extremidade](../../../../../docs/framework/wcf/diagnostics/wmi/endpoint.md) propriedade de "CounterInstanceName" da instância.  
  
-   Nome de instância do contador de operação pode ser obtido por meio do WMI [ponto de extremidade](../../../../../docs/framework/wcf/diagnostics/wmi/endpoint.md) "GetOperationCounterInstanceName" de método instância do.  
  
 Para obter mais informações sobre WMI, consulte [usando o Windows Management Instrumentation para diagnóstico](../../../../../docs/framework/wcf/diagnostics/wmi/index.md).  
  
### <a name="service-performance-counters"></a>Contadores de desempenho do serviço  
 Contadores de desempenho serviço medem o comportamento de serviço como um todo e podem ser usados para diagnosticar o desempenho do serviço inteiro. Eles podem ser encontrados no `ServiceModelService 4.0.0.0` objeto de desempenho durante a exibição de Monitor de desempenho. As instâncias são nomeadas usando o seguinte padrão:  
  
```  
ServiceName@ServiceBaseAddress  
```  
  
 Um contador em um escopo do serviço é agregado de contador em uma coleção de pontos de extremidade.  
  
 Contadores de desempenho para a criação de instância de serviço são incrementados quando um InstanceContext novo é criado. Observe que um InstanceContext novo é criado, mesmo quando você receber uma mensagem de ativação não (com um serviço existente), ou quando você se conectar a uma instância de uma sessão, encerra a sessão e, em seguida, reconectar-se de outra sessão.  
  
### <a name="endpoint-performance-counters"></a>Contadores de desempenho do ponto de extremidade  
 Contadores de desempenho do ponto de extremidade permitem que você examinar dados refletindo como um ponto de extremidade é aceitar mensagens. Eles podem ser encontrados no `ServiceModelEndpoint 4.0.0.0` objeto de desempenho ao exibir usando o Monitor de desempenho. As instâncias são nomeadas usando o seguinte padrão:  
  
```  
(ServiceName).(ContractName)@(endpoint listener address)  
```  
  
 Os dados são semelhantes ao que é coletado para operações individuais, mas só é agregado entre o ponto de extremidade.  
  
 Um contador em um escopo de ponto de extremidade é agregado de contadores em uma coleção de operações.  
  
> [!NOTE]
>  Se dois pontos de extremidade têm endereços e nomes de contrato idênticos, eles serão mapeados para a mesma instância do contador.  
  
### <a name="operation-performance-counters"></a>Contadores de desempenho da operação  
 Contadores de desempenho da operação estão localizados sob o `ServiceModelOperation 4.0.0.0` objeto de desempenho durante a exibição com o Monitor de desempenho. Cada operação tem uma instância individual. Ou seja, se um dado contrato tem operações de 10, 10 instâncias de contador de operação são associadas com esse contrato. As instâncias de objeto são nomeadas usando o seguinte padrão:  
  
```  
(ServiceName).(ContractName).(OperationName)@(first endpoint listener address)  
```  
  
 Esse contador permite avaliar como a chamada está sendo usada e como a operação está sendo executado.  
  
 Quando os contadores estão visíveis em vários escopos, os dados coletados de um escopo superior são agregados com dados de escopos inferiores. Por exemplo, `Calls` em um ponto de extremidade representa a soma de todas as chamadas de operação no ponto de extremidade; `Calls` em um serviço representa a soma de todas as chamadas para todos os pontos de extremidade no serviço.  
  
> [!NOTE]
>  Se você tiver nomes de operação duplicado em um contrato, você somente obtém instâncias de um contador para as duas operações.  
  
## <a name="programming-the-wcf-performance-counters"></a>Os contadores de desempenho do WCF de programação  
 Vários arquivos são instalados na pasta de instalação do SDK para que você pode acessar o [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] programaticamente os contadores de desempenho. Esses arquivos estão listados a seguir.  
  
-   _ServiceModelEndpointPerfCounters.vrg  
  
-   _ServiceModelOperationPerfCounters.vrg  
  
-   _ServiceModelServicePerfCounters.vrg  
  
-   _SMSvcHostPerfCounters.vrg  
  
-   _TransactionBridgePerfCounters.vrg  
  
 Para obter mais informações sobre como acessar os contadores de forma programática, consulte [arquitetura de programação de contador de desempenho](http://go.microsoft.com/fwlink/?LinkId=95179).  
  
## <a name="see-also"></a>Consulte também  
 [Administração e diagnósticos](../../../../../docs/framework/wcf/diagnostics/index.md)
