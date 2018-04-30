---
title: Serviços de fluxo de trabalho de hospedagem
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2d55217e-8697-4113-94ce-10b60863342e
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 21c4ba6a85c2da655b3d0988917165bf84ae64d1
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/30/2018
---
# <a name="hosting-workflow-services"></a>Serviços de fluxo de trabalho de hospedagem
Um serviço de fluxo de trabalho deve ser hospedado para responder às mensagens de entrada. Serviços de fluxo de trabalho usam o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] mensagens infraestrutura e são, portanto, hospedado de forma semelhante. Como [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviços de fluxo de trabalho de serviços podem ser hospedados em qualquer aplicativo gerenciado, em serviços de informações da Internet (IIS), ou em serviços de ativação de processo para Windows (WAS). Além disso, serviços de fluxo de trabalho podem ser hospedados em Windows Server App Fabric. Para obter mais informações sobre o Windows Server App Fabric consulte [documentação do Windows Server App Fabric](http://go.microsoft.com/fwlink/?LinkId=193037), [recursos de hospedagem do AppFabric](http://go.microsoft.com/fwlink/?LinkId=196494), e [conceitos de hospedagem do AppFabric](http://go.microsoft.com/fwlink/?LinkId=196495). Para obter mais informações sobre as várias maneiras de host [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services consulte [serviços de hospedagem](../../../../docs/framework/wcf/hosting-services.md).  
  
## <a name="hosting-in-a-managed-application"></a>Hospedando em um aplicativo gerenciado  
 Para hospedar um serviço de fluxo de trabalho em um aplicativo gerenciado, use o <xref:System.ServiceModel.Activities.WorkflowServiceHost> classe. O <xref:System.ServiceModel.Activities.WorkflowServiceHost> construtor permite que você especifique uma instância de serviço de fluxo de trabalho de singleton, uma definição de serviço de fluxo de trabalho ou uma atividade que usa o fluxo de trabalho de atividades de mensagens. Chamar <<!--zz xref:System.ServiceModel.Activities.WorkflowServiceHost.Open%2A--> `System.ServiceModel.Activities.WorkflowServiceHost.Open`> faz com que o serviço escutar mensagens de entrada.  
  
## <a name="hosting-under-iis-or-was"></a>Hospedando em IIS ou do WAS  
 Hospedar um serviço de fluxo de trabalho em IIS ou do WAS envolve a criação de um diretório virtual e colocar arquivos no diretório virtual que definem o serviço e seu comportamento. Quando hospedar um serviço de fluxo de trabalho em IIS ou do WAS há várias possibilidades:  
  
-   Coloca um arquivo .xamlx que define o serviço de fluxo de trabalho em um IIS / WAS no diretório virtual com um arquivo Web. config que especifica os comportamentos de serviço, os pontos de extremidade e outros elementos de configuração.  
  
-   Coloca um arquivo .xamlx que define o serviço de fluxo de trabalho em um IIS / WAS diretório virtual. O arquivo .xamlx especifica para expor os pontos de extremidade. Pontos de extremidade são especificados em um `WorkflowService.Endpoints` elemento conforme mostrado no exemplo a seguir.  
  
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
    >  Comportamentos não podem ser especificados em um arquivo .xamlx, portanto, você deve usar um Web. config se você precisar especificar configurações de comportamento.  
  
-   Coloca um arquivo .xamlx que define o serviço de fluxo de trabalho em um IIS / WAS diretório virtual. Além disso, coloca um arquivo. svc no diretório virtual. O arquivo. svc permite que você especifique uma fábrica de host de serviço da Web personalizada, aplicar um comportamento personalizado ou carregar a configuração de um local personalizado.  
  
-   Coloque um assembly em IIS / foi diretório virtual que contém uma atividade que usa o WCF atividades de mensagens.  
  
 Um arquivo .xamlx que define um serviço de fluxo de trabalho deve conter um <`Service`> elemento raiz ou um elemento raiz que contém qualquer tipo derivado de <xref:System.Workflow.ComponentModel.Activity>. Ao usar o [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] modelo de atividade de um arquivo .xamlx é criado. Ao usar o modelo de serviço de fluxo de trabalho WCF que será criado um arquivo .xamlx.  
  
## <a name="hosting-workflow-services-under-windows-server-app-fabric"></a>Serviços de hospedagem de fluxo de trabalho no Windows Server AppFabric  
 Hospedar um serviço de fluxo de trabalho no Windows Server AppFabric é feito da mesma forma como hospedagem no IIS / WAS. A única diferença é o fato de que o Windows Server App Fabric está instalado. Malha de aplicativos do Windows Server fornece ferramentas que são adicionadas ao Gerenciador de serviços de informações da Internet, bem como os cmdlets do powershell. Essas ferramentas simplificam a implantação, gerenciamento e controle de serviços de fluxo de trabalho e serviços WCF. . Para obter mais informações sobre o Windows Server App Fabric consulte [Windows Server App Fabric](http://go.microsoft.com/fwlink/?LinkId=193037)  
  
## <a name="referencing-custom-activities"></a>Referência de atividades personalizadas  
 Referências a atividades personalizadas devem ser adicionadas para o <`Assemblies`> seção em <`System.Web.Compilation`> para que eles são carregados para o domínio de aplicativo e o desserializador XAML é capaz de localizar os tipos. Essas configurações podem ser feitas no nível do aplicativo ou na Web. config raiz se as configurações devem ser aplicadas a todos os aplicativos no computador.  
  
## <a name="deployment"></a>Implantação  
 A ferramenta de implantação da Web foi criada para facilitar o trabalho de implantação. A ferramenta permite que você migrar aplicativos entre o IIS 6.0 e IIS 7.0, sincronizar farms de servidores e empacotar, arquivar e implantar aplicativos da Web. Para obter mais informações, consulte [ferramenta de implantação da MS](http://go.microsoft.com/fwlink/?LinkId=178690)  
  
## <a name="see-also"></a>Consulte também  
 [Detalhes internos do host de serviço de fluxo de trabalho](../../../../docs/framework/wcf/feature-details/workflow-service-host-internals.md)  
 [Configurando WorkflowServiceHost](../../../../docs/framework/wcf/feature-details/configuring-workflowservicehost.md)
