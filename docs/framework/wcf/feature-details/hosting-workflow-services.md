---
title: Serviços de fluxo de trabalho de hospedagem
ms.date: 03/30/2017
ms.assetid: 2d55217e-8697-4113-94ce-10b60863342e
ms.openlocfilehash: 0b89eb05513d6b3973de50cd6360711c4f967f68
ms.sourcegitcommit: 97405ed212f69b0a32faa66a5d5fae7e76628b68
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2020
ms.locfileid: "91609454"
---
# <a name="hosting-workflow-services"></a>Serviços de fluxo de trabalho de hospedagem

Um serviço de fluxo de trabalho deve ser hospedado para que ele responda às mensagens de entrada. Os serviços de fluxo de trabalho usam a infraestrutura de mensagens do WCF e, portanto, são hospedados de maneiras semelhantes. Como os serviços WCF, os serviços de fluxo de trabalho podem ser hospedados em qualquer aplicativo gerenciado, em Serviços de Informações da Internet (IIS) ou em WAS (serviços de ativação de processos do Windows). Além disso, os serviços de fluxo de trabalho podem ser hospedados na malha de aplicativos do Windows Server. Para obter mais informações sobre a malha de aplicativos do Windows Server, consulte [documentação do Windows Server app Fabric](/previous-versions/appfabric/ff384253(v=azure.10)), [recursos de hospedagem do AppFabric](/previous-versions/appfabric/ee677189(v=azure.10))e conceitos de hospedagem do [AppFabric](/previous-versions/appfabric/ee677371(v=azure.10)). Para obter mais informações sobre as várias maneiras de hospedar serviços WCF, consulte [serviços de hospedagem](../hosting-services.md).

## <a name="hosting-in-a-managed-application"></a>Hospedando em um aplicativo gerenciado
 Para hospedar um serviço de fluxo de trabalho em um aplicativo gerenciado, use a <xref:System.ServiceModel.Activities.WorkflowServiceHost> classe. O <xref:System.ServiceModel.Activities.WorkflowServiceHost> construtor permite que você especifique uma instância de serviço de fluxo de trabalho singleton, uma definição de serviço de fluxo de trabalho ou uma atividade que usa as atividades de mensagens de fluxo de trabalho. <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>A chamada faz com que o serviço inicie a escuta de mensagens de entrada.

## <a name="hosting-under-iis-or-was"></a>Hospedagem no IIS ou WAS
 Hospedar um serviço de fluxo de trabalho no IIS ou o WAS envolve a criação de um diretório virtual e a colocação de arquivos no diretório virtual que definem o serviço e seu comportamento. Ao hospedar um serviço de fluxo de trabalho no IIS ou o WAS há várias possibilidades:

- Coloque um arquivo. xamlx que define o serviço de fluxo de trabalho em um diretório virtual do IIS/WAS, juntamente com um arquivo de Web.config que especifica os comportamentos de serviço, os pontos de extremidade e outros elementos de configuração.

- Coloque um arquivo. xamlx que define o serviço de fluxo de trabalho em um diretório virtual do IIS/WAS. O arquivo. xamlx especifica os pontos de extremidade a serem expostos. Os pontos de extremidade são especificados em um `WorkflowService.Endpoints` elemento, conforme mostrado no exemplo a seguir.

    ```xml
    <WorkflowService xmlns="http://schemas.microsoft.com/netfx/2009/xaml/servicemodel"  xmlns:p1="http://schemas.microsoft.com/netfx/2009/xaml/activities" xmlns:sad="clr-namespace:System.Activities.Debugger;assembly=System.Activities" xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">
      <WorkflowService.Endpoints>
        <Endpoint ServiceContractName="IWorkFlowEchoService" AddressUri="">
          <Endpoint.Binding>
            <BasicHttpBinding />
          </Endpoint.Binding>
        </Endpoint>
      </WorkflowService.Endpoints>
    <!-- ... -->
    </WorkflowService>
    ```

    > [!NOTE]
    > Os comportamentos não podem ser especificados em um arquivo. xamlx, portanto, você deve usar um Web.config se precisar especificar configurações de comportamento.

- Coloque um arquivo. xamlx que define o serviço de fluxo de trabalho em um diretório virtual do IIS/WAS. Além disso, coloque um arquivo. svc no diretório virtual. O arquivo. svc permite especificar uma fábrica de hosts de serviço Web personalizada, aplicar o comportamento personalizado ou carregar a configuração de um local personalizado.

- Coloque um assembly no diretório virtual do IIS/WAS que contém uma atividade que usa as atividades de mensagens do WCF.

 Um arquivo. xamlx que define um serviço de fluxo de trabalho deve conter um `Service` elemento raiz <> ou um elemento raiz que contenha qualquer tipo derivado de <xref:System.Workflow.ComponentModel.Activity> . Ao usar o modelo de atividade do Visual Studio, um arquivo. xamlx é criado. Ao usar o modelo de serviço de fluxo de trabalho do WCF, um arquivo. xamlx é criado.

## <a name="hosting-workflow-services-under-windows-server-app-fabric"></a>Hospedando serviços de fluxo de trabalho no Windows Server app Fabric
 A hospedagem de um serviço de fluxo de trabalho no Windows Server app Fabric é feita da mesma maneira que a hospedagem no IIS/WAS. A única diferença é o fato de que o Windows Server app Fabric está instalado. O Windows Server app Fabric fornece ferramentas que são adicionadas ao Serviços de Informações da Internet Manager, bem como PowerShell commandlets. Essas ferramentas simplificam a implantação, o gerenciamento e o acompanhamento de serviços de fluxo de trabalho e serviços WCF.

## <a name="referencing-custom-activities"></a>Referenciando atividades personalizadas
 As referências a atividades personalizadas devem ser adicionadas à `Assemblies` seção <> em <`System.Web.Compilation`> para que elas sejam carregadas no domínio do aplicativo e o desserializador de XAML seja capaz de localizar os tipos. Essas configurações podem ser feitas no nível do aplicativo ou na Web.config raiz se as configurações devem ser aplicadas a todos os aplicativos no computador.

## <a name="deployment"></a>Implantação
 A ferramenta de implantação da Web foi criada para facilitar o trabalho de implantação. A ferramenta permite migrar aplicativos entre o IIS 6,0 e o IIS 7,0, sincronizar farms de servidores e empacotar, arquivar e implantar aplicativos Web. Para obter mais informações, consulte [ferramenta de implantação da MS](https://go.microsoft.com/fwlink/?LinkId=178690).

## <a name="see-also"></a>Confira também

- [Internos do host de serviço de fluxo de trabalho](workflow-service-host-internals.md)
- [Configurando WorkflowServiceHost](configuring-workflowservicehost.md)
