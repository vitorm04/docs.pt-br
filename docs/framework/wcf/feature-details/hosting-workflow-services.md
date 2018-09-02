---
title: Serviços de fluxo de trabalho de hospedagem
ms.date: 03/30/2017
ms.assetid: 2d55217e-8697-4113-94ce-10b60863342e
ms.openlocfilehash: f75b8cc4cde0372b995c39a5da3ae4b71590743e
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43416359"
---
# <a name="hosting-workflow-services"></a>Serviços de fluxo de trabalho de hospedagem
Um serviço de fluxo de trabalho deve ser hospedado para responder às mensagens de entrada. Serviços de fluxo de trabalho usam a infraestrutura de mensagens do WCF e, portanto, são hospedados de maneiras semelhantes. Assim como serviços WCF, serviços de fluxo de trabalho podem ser hospedados em qualquer aplicativo gerenciado, em serviços de informações da Internet (IIS) ou em Windows processo WAS (Activation Services). Além disso, os serviços de fluxo de trabalho podem ser hospedados no Windows Server App Fabric. Para obter mais informações sobre o Windows Server AppFabric, consulte [documentação do Windows Server AppFabric](https://go.microsoft.com/fwlink/?LinkId=193037), [recursos de hospedagem de AppFabric](https://go.microsoft.com/fwlink/?LinkId=196494), e [conceitos de hospedagem de AppFabric](https://go.microsoft.com/fwlink/?LinkId=196495). Para obter mais informações sobre as várias maneiras de WCF do host dos serviços de ver [serviços de hospedagem](../../../../docs/framework/wcf/hosting-services.md).

## <a name="hosting-in-a-managed-application"></a>Hospedagem em um aplicativo gerenciado
 Para hospedar um serviço de fluxo de trabalho em um aplicativo gerenciado, use o <xref:System.ServiceModel.Activities.WorkflowServiceHost> classe. O <xref:System.ServiceModel.Activities.WorkflowServiceHost> construtor permite que você especifique uma instância singleton do serviço de fluxo de trabalho, uma definição de serviço de fluxo de trabalho ou uma atividade que usa o fluxo de trabalho de atividades de mensagem. Chamar <<!--zz xref:System.ServiceModel.Activities.WorkflowServiceHost.Open%2A--> `System.ServiceModel.Activities.WorkflowServiceHost.Open`> faz com que o serviço iniciar a escuta para mensagens de entrada.

## <a name="hosting-under-iis-or-was"></a>Hospedarmos no IIS ou WAS
 Hospedar um serviço de fluxo de trabalho em IIS ou WAS envolve a criação de um diretório virtual e colocar arquivos no diretório virtual que definem o serviço e seu comportamento. Ao hospedar um serviço de fluxo de trabalho em IIS ou WAS lá é várias possibilidades:

-   Colocar um arquivo. xamlx que define o serviço de fluxo de trabalho em um IIS / WAS diretório virtual junto com um arquivo Web. config que especifica os comportamentos de serviço, os pontos de extremidade e outros elementos de configuração.

-   Colocar um arquivo. xamlx que define o serviço de fluxo de trabalho em um IIS / WAS diretório virtual. O arquivo. xamlx Especifica os pontos de extremidade para expor. Pontos de extremidade são especificados em um `WorkflowService.Endpoints` elemento, conforme mostrado no exemplo a seguir.

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
    > Comportamentos não podem ser especificados em um arquivo. xamlx, então você deve usar um Web. config, se você precisa especificar as configurações de comportamento.

-   Colocar um arquivo. xamlx que define o serviço de fluxo de trabalho em um IIS / WAS diretório virtual. Além disso, coloque um arquivo. svc no diretório virtual. O arquivo. svc permite que você especifique uma fábrica do host de serviço da Web personalizada, aplicar o comportamento personalizado ou carregar a configuração de um local personalizado.

-   Colocar um assembly no IIS / foi um diretório virtual que contém uma atividade que usa o WCF atividades de mensagem.

 Um arquivo. xamlx que define um serviço de fluxo de trabalho deve conter um <`Service`> elemento raiz ou um elemento raiz que contém qualquer tipo derivado de <xref:System.Workflow.ComponentModel.Activity>. Ao usar o modelo de atividade do Visual Studio, um arquivo. xamlx é criado. Ao usar o modelo de serviço de fluxo de trabalho do WCF, um arquivo. xamlx é criado.

## <a name="hosting-workflow-services-under-windows-server-app-fabric"></a>Serviços de hospedagem de fluxo de trabalho no Windows Server App Fabric
 Hospedar um serviço de fluxo de trabalho no Windows Server AppFabric é feito da mesma forma como hospedagem no IIS / WAS. A única diferença é o fato de que a malha de aplicativos do Windows Server está instalada. Windows Server AppFabric fornece ferramentas que são adicionadas ao Gerenciador de serviços de informações da Internet, bem como os cmdlets do powershell. Essas ferramentas simplificam implantando, gerenciando e controle de serviços de fluxo de trabalho e serviços WCF.

## <a name="referencing-custom-activities"></a>Referência de atividades personalizadas
 Referências para atividades personalizadas devem ser adicionadas para o <`Assemblies`> seção <`System.Web.Compilation`> para que eles são carregados no domínio do aplicativo e o desserializador XAML é capaz de localizar os tipos. Essas configurações podem ser feitas no nível do aplicativo ou na raiz da Web. config se as configurações devem ser aplicadas a todos os aplicativos no computador.

## <a name="deployment"></a>Implantação
 A ferramenta de implantação da Web foi criada para facilitar o trabalho de implantação. A ferramenta permite que você migrar aplicativos entre o IIS 6.0 e IIS 7.0, sincronizar os farms de servidores e empacotar, arquivar e implantar aplicativos da Web. Para obter mais informações, consulte [ferramenta de implantação MS](https://go.microsoft.com/fwlink/?LinkId=178690).

## <a name="see-also"></a>Consulte também

- [Detalhes internos do host de serviço de fluxo de trabalho](../../../../docs/framework/wcf/feature-details/workflow-service-host-internals.md)
- [Configurando WorkflowServiceHost](../../../../docs/framework/wcf/feature-details/configuring-workflowservicehost.md)