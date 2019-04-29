---
title: Visão geral de fluxo de mensagens
ms.date: 03/30/2017
ms.assetid: fb0899e1-84cc-4d90-b45b-dc5a50063943
ms.openlocfilehash: d75a535a601612196ef66151a4685723e048848f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61797470"
---
# <a name="message-flow-overview"></a>Visão geral de fluxo de mensagens
Em um sistema distribuído que contém serviços interconectados, é necessário determinar relações causais entre os serviços. É importante entender os vários componentes que faziam parte de um fluxo de solicitação para dar suporte a cenários críticos, tais como integridade, monitoramento, solução de problemas e análise da causa raiz. Para habilitar a correlação de rastreamentos entre vários serviços, no .NET Framework 4, adicionamos suporte por meio dos seguintes recursos:

- Rastreamento analítico: Um alto desempenho e o recurso de rastreamento de baixo nível de detalhes usando o rastreamento de eventos para Windows (ETW).

- Modelo de atividade de ponta a ponta para os serviços do WCF/WF: Esse recurso dá suporte à correlação de rastreamentos gerados pelo <xref:System.ServiceModel> e <xref:System.Workflow.ComponentModel> namespaces.

- Rastreamento do WF com o ETW: Esse recurso usa registros de rastreamento gerados pelos serviços do WF para fornecer visibilidade sobre o estado atual e o progresso do fluxo de trabalho.

 Erros registrados em um rastreamento ou registro de rastreamento podem ser usados para localizar defeitos de código ou mensagens formadas incorretamente. A propriedade ActivityId do nó correlação no cabeçalho da mensagem do evento pode ser usada para determinar a atividade com falha. Para habilitar o rastreamento de fluxo de mensagem por ID de atividade, consulte [Configurando o rastreamento de fluxo de mensagem](../../../../docs/framework/wcf/diagnostics/etw/configuring-message-flow-tracing.md). Este tópico demonstra como habilitar o rastreamento de fluxo de mensagem no projeto criado no tutorial de Introdução.

### <a name="to-enable-message-flow-tracing-in-the-getting-started-tutorial"></a>Para habilitar o rastreamento de fluxo de mensagem no tutorial de Introdução

1. Abra o Visualizador de eventos clicando **inicie**, **execute**e inserindo `eventvwr.exe`.

2. Se você ainda não tiver ativado rastreamento analítico, expanda **Applications and Services Logs**, **Microsoft**, **Windows**, **aplicativos de servidor** . Selecione **modo de exibição**, **analíticos e de Logs de depuração**. Clique com botão direito **analítico** e selecione **Habilitar Log**. Deixe o Visualizador de eventos aberto para que os rastreamentos podem ser exibidos.

3. Abra o exemplo criado a [Tutorial de Introdução](../../../../docs/framework/wcf/getting-started-tutorial.md) no Visual Studio 2012. Observe que você deve executar o Visual Studio 2012 como um administrador para que o serviço pode ser criado. Se você tiver que instalar os exemplos WCF, você pode abrir o [Introdução ao](../../../../docs/framework/wcf/samples/getting-started-sample.md), que contém o projeto concluído criado no tutorial.

4. Com o botão direito do **Service** do projeto e selecione **Add**, **Novo Item**. Selecione **arquivo de configuração de aplicativo** e clique em **Okey**.

5. Adicione o seguinte código ao arquivo App. config criado na etapa anterior.

    ```xml
    <system.serviceModel>
      <diagnostics>
        <endToEndTracing propagateActivity="true" messageFlowTracing="true"/>
      </diagnostics>
    </system.serviceModel>
    ```

6. Execute o aplicativo de servidor sem depuração pressionando CTRL + F5. Executar o projeto de cliente clicando com o **Client** projeto e selecionando **Debug**, **iniciar uma nova instância**.

7. Para rastrear os eventos do cliente para o servidor, adicione o seguinte ao arquivo de configuração de aplicativo no projeto do cliente.

    ```xml
    <diagnostics>
      <endToEndTracing propagateActivity="true" messageFlowTracing="true"/>
    </diagnostics>
    ```

8. Em Program.cs no cliente, adicione a seguinte instrução Using.

    ```csharp
    using System.Diagnostics;
    ```

9. No método Main no arquivo program.cs no projeto do cliente, defina o GUID de rastreamento sejam propagadas no log de eventos.

    ```csharp
    Guid guid = Guid.NewGuid();
    Trace.CorrelationManager.ActivityId = guid;
    ```

10. Atualizar e examine os **analítico** log.  Procure um evento com 220 de ID de evento.  Selecione o evento e, em seguida, clique no **detalhes** guia no painel de visualização. Esse evento conterá a ID de correlação para a atividade de chamada.

    ```xml
    <Correlation ActivityID="{A066CCF1-8AB3-459B-B62F-F79F957A5036}" />
    ```

    > [!NOTE]
    >  Todos os eventos com o mesmo GUID em ActivityID estão relacionados a uma solicitação. Isso pode ser usado para correlacionar mensagens de um cliente específico a um serviço específico. Se o cliente chamado outro serviço, em seguida, o mesmo cliente poderia ser identificado pela ActivityID.

11. Em alguns casos, o ActivityID pode alterar de GUID original para um novo ActivityID. Nesse caso, um evento de transferência é emitido. Essa ID de evento é 499 e o evento conterá os seguintes dados no cabeçalho.

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
    >  O evento de transferência registra a alteração da ActivityID Active Directory do GUID especificado como o ActivityID ao GUID especificado como RelatedActivityID. Depois que o evento de transferência é emitido, todos os eventos conterão o novo GUID como o ActivityID.
