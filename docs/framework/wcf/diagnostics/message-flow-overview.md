---
title: "Visão geral de fluxo de mensagens"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fb0899e1-84cc-4d90-b45b-dc5a50063943
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6fe4d8222bfed231c618ee4e5616dab37f912836
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="message-flow-overview"></a>Visão geral de fluxo de mensagens
Em um sistema distribuído que contêm serviços interconectados, é necessário determinar relações causais entre os serviços. É importante entender os vários componentes que fazem parte de um fluxo de solicitação para dar suporte a cenários críticos como monitoramento, solução de problemas de integridade e análise da causa raiz. Para habilitar a correlação de rastreamentos entre vários serviços, no .NET Framework 4, adicionamos suporte por meio dos seguintes recursos:  
  
-   Rastreamento analítico: um alto desempenho e o recurso de rastreamento de baixo nível de detalhes usando o rastreamento de eventos para Windows (ETW).  
  
-   Modelo de atividade de ponta a ponta para serviços WCF/WF: esse recurso oferece suporte à correlação de rastreamento gerados pelo <xref:System.ServiceModel> e <xref:System.Workflow.ComponentModel> namespaces.  
  
-   ETW de controle do WF: esse recurso usa registros de rastreamento gerados pelos serviços do WF para fornecer visibilidade sobre o estado atual e o progresso do fluxo de trabalho.  
  
 Erros registrados em um controle ou registro de rastreamento podem ser usados para localizar os defeitos de código ou mensagens formadas incorretamente. A propriedade ActivityId do nó correlação no cabeçalho da mensagem do evento pode ser usada para determinar a atividade com falha. Para habilitar o rastreamento de fluxo de mensagem por ID de atividade, consulte [Configurando o rastreamento de fluxo de mensagem](../../../../docs/framework/wcf/diagnostics/etw/configuring-message-flow-tracing.md). Este tópico demonstra como habilitar o rastreamento de fluxo de mensagem no projeto criado no tutorial de Introdução.  
  
### <a name="to-enable-message-flow-tracing-in-the-getting-started-tutorial"></a>Para habilitar o rastreamento de fluxo de mensagem no tutorial de Introdução  
  
1.  Abra o Visualizador de eventos clicando **iniciar**, **executar**e digitando `eventvwr.exe`.  
  
2.  Se você ainda não ativou o rastreamento analítico, expanda **Applications and Services Logs**, **Microsoft**, **Windows**, **aplicativos de servidor de aplicativo** . Selecione **exibição**, **Mostrar analítica e Logs de depuração**. Clique com botão direito **analítico** e selecione **Habilitar Log**. Deixe o Visualizador de eventos aberto para que os rastreamentos podem ser exibidos.  
  
3.  Abra o exemplo criado o [Tutorial de Introdução](../../../../docs/framework/wcf/getting-started-tutorial.md) em [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]. Observe que você deve executar [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] como um administrador para que o serviço pode ser criado. Se você tiver o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] exemplos instalados, você pode abrir o [Introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md), que contém o projeto completo criado no tutorial.  
  
4.  Clique com botão direito do **Service** do projeto e selecione **adicionar**, **Novo Item**. Selecione **arquivo de configuração do aplicativo** e clique em **Okey**.  
  
5.  Adicione o seguinte código ao arquivo App. config criado na etapa anterior.  
  
    ```xml  
    <system.serviceModel>  
      <diagnostics>  
        <endToEndTracing propagateActivity="true" messageFlowTracing="true"/>  
      </diagnostics>  
    </system.serviceModel>  
    ```  
  
6.  Execute o aplicativo de servidor sem depuração pressionando CTRL + F5. Execute o projeto cliente clicando com o **cliente** projeto e selecionando **depurar**, **iniciar uma nova instância**.  
  
7.  Para rastrear eventos do cliente para o servidor, adicione o seguinte no arquivo de configuração do aplicativo no projeto do cliente.  
  
    ```xml  
    <diagnostics>  
      <endToEndTracing propagateActivity="true" messageFlowTracing="true"/>  
    </diagnostics>  
    ```  
  
8.  Em Program.cs no cliente, adicione a seguinte instrução Using.  
  
    ```  
    using System.Diagnostics;  
    ```  
  
9. No método Main no arquivo program.cs no projeto do cliente, defina o GUID de rastreamento sejam propagadas no log de eventos.  
  
    ```  
    Guid guid = Guid.NewGuid();  
    Trace.CorrelationManager.ActivityId = guid;  
    ```  
  
10. Atualizar e examinar o **analítico** log.  Procure um evento com 220 de ID de evento.  Selecione o evento e, em seguida, clique no **detalhes** guia no painel de visualização. Esse evento conterá a ID de correlação para a atividade de chamada.  
  
    ```xml  
    <Correlation ActivityID="{A066CCF1-8AB3-459B-B62F-F79F957A5036}" />  
    ```  
  
    > [!NOTE]
    >  Todos os eventos com o mesmo GUID de ActivityID estão relacionados a uma solicitação. Isso pode ser usado para correlacionar as mensagens de um cliente específico para um serviço específico. Se o cliente chamado outro serviço, o mesmo cliente pode ser identificado pelo ActivityID.  
  
11. Em alguns casos, o ActivityID pode mudar de GUID original para uma nova ActivityID. Nesse caso, um evento de transferência é emitido. Essa ID de evento é 499, e o evento conterá os dados a seguir no cabeçalho.  
  
    ```xml  
    <Event xmlns="http://schemas.microsoft.com/win/2004/08/events/event">  
        <System>  
            <Provider Name="Microsoft-Windows-Application Server-Applications" Guid="{c651f5f6-1c0d-492e-8ae1-b4efd7c9d503}" />   
            <EventID>499</EventID>   
            ...  
            <Correlation ActivityID="{A066CCF1-8AB3-459B-B62F-F79F957A5036}" RelatedActivityID="{85FC0930-9C49-42DA-804B-A7368104BD1B}" />   
            ...  
       </System>  
    </Event>  
    ```  
  
    > [!NOTE]
    >  O evento de transferência registra a alteração do ActivityID active do GUID especificado como o ActivityID para o GUID especificado como RelatedActivityID. Depois que o evento de transferência é emitido, todos os eventos conterá o novo GUID como o ActivityID.
