---
title: Diagnosticando aplicativos transacionais
ms.date: 03/30/2017
ms.assetid: 4a993492-1088-4d10-871b-0c09916af05f
ms.openlocfilehash: 9a4f064d903092b04f8885fb00b56e18c9cfeb74
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64751122"
---
# <a name="diagnosing-transactional-applications"></a>Diagnosticando aplicativos transacionais
Este tópico descreve como usar o recurso de diagnóstico e gerenciamento do Windows Communication Foundation (WCF) para solucionar problemas de um aplicativo transacional.  
  
## <a name="performance-counters"></a>Contadores de desempenho  
 O WCF fornece um conjunto padrão de contadores de desempenho para medir o desempenho do seu aplicativo transacional. Para obter mais informações, consulte [Contadores de desempenho](../../../../docs/framework/wcf/diagnostics/performance-counters/index.md).  
  
 Contadores de desempenho estão no escopo para três níveis diferentes: de serviço, ponto de extremidade e operação, conforme descrito nas tabelas a seguir.  
  
### <a name="service-performance-counters"></a>Contadores de desempenho de serviço  
  
|Contador de desempenho|Descrição|  
|-------------------------|-----------------|  
|Fluxo de transações|O número de transações que flui para operações nesse serviço. Esse contador é incrementado sempre que uma transação está presente na mensagem que é enviada para o serviço.|  
|Fluxo de transações por segundo|O número de transações que flui para operações nesse serviço dentro de cada segundo. Esse contador é incrementado sempre que uma transação está presente na mensagem que é enviada para o serviço.|  
|Operações Transacionadas Confirmadas|O número de operações transacionadas executadas, cuja transação tiver sido concluída com resultados confirmados neste serviço. Trabalho feito nessas operações é totalmente confirmado. Os recursos são atualizados de acordo com o trabalho feito na operação.|  
|Operações Transacionadas Confirmadas por Segundo|O número de operações transacionadas executadas, cuja transação tiver sido concluída com resultados confirmados neste serviço dentro de cada segundo. Trabalho feito nessas operações é totalmente confirmado. Os recursos são atualizados de acordo com o trabalho feito na operação.|  
|Operações de transação abortadas|O número de operações transacionadas executadas, cujo transaction foi concluída com o resultado anulado neste serviço. O trabalho feito essas operações é revertido. Os recursos são revertidos para seu estado anterior.|  
|Operações Transacionadas Anuladas por Segundo|O número de operações transacionadas executadas, cujo transaction foi concluída com o resultado anulado neste serviço dentro de cada segundo. O trabalho feito essas operações é revertido. Os recursos são revertidos para seu estado anterior.|  
|Operações Transacionadas em Dúvida|O número de operações transacionadas executadas, cuja transação tiver sido concluída com resultados em dúvida neste serviço. Trabalho com resultados em dúvida está em um estado indeterminado. Os recursos são mantidos com resultado pendente.|  
|Operações Transacionadas em Dúvida por Segundo|O número de operações realizadas executadas, cuja transação tiver sido concluído com resultados em dúvida neste serviço em cada segundo. Trabalho com resultados em dúvida está em um estado indeterminado. Os recursos são mantidos com resultado pendente.|  
  
### <a name="endpoint-performance-counters"></a>Contadores de desempenho de ponto de extremidade  
  
|Contador de desempenho|Descrição|  
|-------------------------|-----------------|  
|Fluxo de transações|O número de transações que flui para operações nesse ponto de extremidade. Esse contador é incrementado sempre que uma transação está presente na mensagem que é enviada para o ponto de extremidade.|  
|Fluxo de transações por segundo|O número de transações que flui para operações nesse ponto de extremidade dentro de cada segundo. Esse contador é incrementado sempre que uma transação está presente na mensagem que é enviada para o ponto de extremidade.|  
  
### <a name="operation-performance-counters"></a>Contadores de desempenho de operação  
  
|Contador de desempenho|Descrição|  
|-------------------------|-----------------|  
|Fluxo de transações|O número de transações que flui para operações nesse ponto de extremidade. Esse contador é incrementado sempre que uma transação está presente na mensagem que é enviada para o ponto de extremidade.|  
|Fluxo de transações por segundo|O número de transações que flui para operações nesse ponto de extremidade dentro de cada segundo. Esse contador é incrementado sempre que uma transação está presente na mensagem que é enviada para o ponto de extremidade.|  
  
## <a name="windows-management-instrumentation"></a>Instrumentação de gerenciamento do Windows  
 WCF expõe dados de inspeção de um serviço em tempo de execução através de um provedor de instrumentação de gerenciamento do Windows (WMI) do WCF. Para obter mais informações sobre como acessar dados do WMI, consulte [usando o Windows Management Instrumentation para diagnóstico](../../../../docs/framework/wcf/diagnostics/wmi/index.md).  
  
 Um número de propriedades somente leitura do WMI indica as configurações aplicadas de transação de um serviço. As tabelas seguintes listam todas essas configurações.  
  
 Em um serviço, o `ServiceBehaviorAttribute` tem as seguintes propriedades.  
  
|Nome|Tipo|Descrição|  
|----------|----------|-----------------|  
|ReleaseServiceInstanceOnTransactionComplete|Boolean|Especifica se o objeto de serviço é reciclado quando a transação atual seja concluída.|  
|TransactionAutoCompleteOnSessionClose|Boolean|Especifica se as transações pendentes são foi concluída quando a sessão atual é fechada.|  
|TransactionIsolationLevel|Uma cadeia de caracteres que contém um valor válido do <xref:System.Transactions.IsolationLevel> enumeração.|Especifica o nível de isolamento da transação que dá suporte a esse serviço.|  
|TransactionTimeout|<xref:System.DateTime>|Especifica o período dentro do qual uma transação deve ser concluída.|  
  
 O `ServiceTimeoutsBehavior` tem a seguinte propriedade.  
  
|Nome|Tipo|Descrição|  
|----------|----------|-----------------|  
|TransactionTimeout|<xref:System.DateTime>|Especifica o período dentro do qual uma transação deve ser concluída.|  
  
 Em uma associação, o `TransactionFlowBindingElement` tem as seguintes propriedades.  
  
|Nome|Tipo|Descrição|  
|----------|----------|-----------------|  
|TransactionProtocol|Uma cadeia de caracteres que contém um valor válido do <xref:System.ServiceModel.TransactionProtocol> tipo.|Especifica o protocolo de transação a ser usado no fluxo de uma transação.|  
|TransactionFlow|Boolean|Especifica se o fluxo de transação de entrada está habilitado.|  
  
 Em uma operação, o `OperationBehaviorAttribute` tem as seguintes propriedades:  
  
|Nome|Tipo|Descrição|  
|----------|----------|-----------------|  
|TransactionAutoComplete|Boolean|Especifica se deve confirmar a transação atual automaticamente se não ocorrer nenhuma exceção sem tratamento.|  
|TransactionScopeRequired|Boolean|Especifica se a operação exige uma transação.|  
  
 Em uma operação, o `TransactionFlowAttribute` tem as seguintes propriedades.  
  
|Nome|Tipo|Descrição|  
|----------|----------|-----------------|  
|TransactionFlowOption|Uma cadeia de caracteres que contém um valor válido do <xref:System.ServiceModel.TransactionFlowOption> enumeração.|Especifica a extensão para qual transação fluxo é necessário.|  
  
## <a name="tracing"></a>Rastreamento  
 Rastreamentos que você possa monitorar e analisar falhas em seus aplicativos transacionais. Você pode habilitar o rastreamento usando das seguintes maneiras:  
  
- Rastreamento padrão do WCF  
  
     Esse tipo de rastreamento é o mesmo que o rastreamento de qualquer aplicativo WCF. Para obter mais informações, consulte [Configurando o rastreamento](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md).  
  
- Rastreamento de WS-AtomicTransaction  
  
     Rastreamento de WS-AtomicTransaction pode ser habilitado usando o [WS-AtomicTransaction utilitário de configuração (wsatConfig.exe)](../../../../docs/framework/wcf/ws-atomictransaction-configuration-utility-wsatconfig-exe.md). Esse rastreamento fornece informações sobre o estado de transações e os participantes dentro de um sistema. Para habilitar o rastreamento interno do modelo de serviço também, você pode definir as `HKLM\SOFTWARE\Microsoft\WSAT\3.0\ServiceModelDiagnosticTracing` chave do registro para um valor válido do <xref:System.Diagnostics.SourceLevels> enumeração. Você pode habilitar o registro em log da mesma forma que outros aplicativos do WCF de mensagem.  
  
- `System.Transactions` Rastreamento  
  
     Ao usar o protocolo de OleTransactions, mensagens de protocolo não podem ser rastreadas. O suporte de rastreamento a <xref:System.Transactions> fornece infraestrutura (que usa OleTransactions) permite que os usuários visualizem eventos que ocorreram para as transações. Para habilitar o rastreamento para um <xref:System.Transactions> aplicativo, incluem o seguinte código no `App.config` arquivo de configuração.  
  
    ```xml  
    <configuration>  
      <system.diagnostics>  
         <sources>  
            <source name="System.Transactions" switchValue="Verbose, ActivityTracing">  
               <listeners>  
                  <add name="Text"  
                     type="System.Diagnostics.XmlWriterTraceListener"  
                     initializeData="SysTx.log"  
                     traceOutputOptions="Callstack" />  
               </listeners>  
            </source>  
         </sources>  
         <trace autoflush="true" indentsize="4">  
         </trace>  
      </system.diagnostics>  
    </configuration>  
    ```  
  
     Isso também permite que o rastreamento do WCF, como o WCF também utiliza o <xref:System.Transactions> infraestrutura.  
  
## <a name="see-also"></a>Consulte também

- [Administração e diagnósticos](../../../../docs/framework/wcf/diagnostics/index.md)
- [Configurando o rastreamento](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)
- [Utilitário de configuração de WS-AtomicTransaction (wsatConfig.exe)](../../../../docs/framework/wcf/ws-atomictransaction-configuration-utility-wsatconfig-exe.md)
