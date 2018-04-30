---
title: Como hospedar um serviço do WCF em WAS
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9e3e213e-2dce-4f98-81a3-f62f44caeb54
caps.latest.revision: 25
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c4613587d829b082ee7182cc32e34d2d2d563241
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/30/2018
---
# <a name="how-to-host-a-wcf-service-in-was"></a>Como hospedar um serviço do WCF em WAS
Este tópico descreve as etapas básicas necessárias para criar um serviços de ativação de processos do Windows (também conhecido como WAS) hospedado [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] serviço. FOI é o novo serviço de ativação de processo é uma generalização dos recursos de serviços de informações da Internet (IIS) que funcionam com protocolos de transporte não HTTP. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usa a interface do adaptador de escuta para comunicar as solicitações de ativação recebidas nos protocolos não HTTP com suporte [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], como TCP, pipes nomeados e enfileiramento de mensagens.  
  
 Essa opção de hospedagem requer que os componentes de ativação do WAS são instalados e configurados corretamente, mas não exige qualquer código de hospedagem para ser gravado como parte do aplicativo. Para obter mais informações sobre como instalar e configurar o WAS, consulte [como: instalar e configurar componentes de ativação do WCF](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md).  
  
> [!WARNING]
>  Não foi oferece suporte à ativação se o pipeline de processamento de solicitação do servidor web está definido para o modo clássico. Pipeline de processamento de solicitação do servidor web deve ser definido para o modo integrado se a ativação do WAS será usado.  
  
 Quando um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço é hospedado no WAS, as associações padrão são usadas como de costume. No entanto, ao usar o <xref:System.ServiceModel.NetTcpBinding> e <xref:System.ServiceModel.NetNamedPipeBinding> para configurar um serviço hospedado do WAS, uma restrição deve ser atendida. Quando diferentes pontos de extremidade usam o mesmo transporte, as configurações de associação tem que corresponder as sete propriedades a seguir:  
  
-   connectionBufferSize  
  
-   ChannelInitializationTimeout  
  
-   MaxPendingConnections  
  
-   maxOutputDelay  
  
-   MaxPendingAccepts  
  
-   ConnectionPoolSettings.IdleTimeout  
  
-   ConnectionPoolSettings.MaxOutboundConnectionsPerEndpoint  
  
 Caso contrário, o ponto de extremidade é inicializado pela primeira vez sempre determina os valores dessas propriedades e pontos de extremidade adicionados posteriormente lançam um <xref:System.ServiceModel.ServiceActivationException> se elas não corresponderem a essas configurações.  
  
 Para a cópia de origem deste exemplo, consulte [ativação TCP](../../../../docs/framework/wcf/samples/tcp-activation.md).  
  
### <a name="to-create-a-basic-service-hosted-by-was"></a>Para criar um serviço básico hospedado pelo WAS  
  
1.  Defina um contrato de serviço para o tipo de serviço.  
  
     [!code-csharp[C_HowTo_HostInWAS#1121](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/service.cs#1121)]  
  
2.  Implemente o contrato de serviço em uma classe de serviço. Observe que as informações de endereço e associação não são especificadas dentro da implementação do serviço. Além disso, o código não tem a ser gravado para recuperar informações do arquivo de configuração.  
  
     [!code-csharp[C_HowTo_HostInWAS#1122](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/service.cs#1122)]  
  
3.  Criar um arquivo Web. config para definir o <xref:System.ServiceModel.NetTcpBinding> associação a ser usado pelo `CalculatorService` pontos de extremidade.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <system.serviceModel>  
        <bindings>  
          <netTcpBinding>  
            <binding portSharingEnabled="true">  
              <security mode="None" />  
            </binding>  
          </netTcpBinding>  
        </bindings>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
4.  Crie um arquivo SVC que contém o código a seguir.  
  
    ```  
    <%@ServiceHost language=c# Service="CalculatorService" %>   
    ```  
  
5.  Coloque o arquivo svc no diretório virtual do IIS.  
  
### <a name="to-create-a-client-to-use-the-service"></a>Para criar um cliente para usar o serviço  
  
1.  Use [Ferramenta Utilitária de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) da linha de comando para gerar o código de metadados de serviço.  
  
    ```  
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>   
    ```  
  
2.  O cliente que é gerado contém o `ICalculator` interface que define o contrato de serviço que deve atender a implementação do cliente.  
  
     [!code-csharp[C_HowTo_HostInWAS#1221](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/client.cs#1221)]  
  
3.  O aplicativo cliente gerado também contém a implementação de `ClientCalculator`. Observe que as informações de endereço e associação não são especificadas em qualquer lugar dentro da implementação do serviço. Além disso, o código não tem a ser gravado para recuperar informações do arquivo de configuração.  
  
     [!code-csharp[C_HowTo_HostInWAS#1222](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/client.cs#1222)]  
  
4.  A configuração do cliente que usa o <xref:System.ServiceModel.NetTcpBinding> também é gerado pelo Svcutil.exe. Este arquivo deve ser nomeado no arquivo App. config quando usando o Visual Studio.  
  
     [!code-xml[C_HowTo_HostInWAS#2211](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/common/app.config#2211)]   
  
5.  Criar uma instância do `ClientCalculator` em um aplicativo e, em seguida, chamar as operações de serviço.  
  
     [!code-csharp[C_HowTo_HostInWAS#1223](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/client.cs#1223)]  
  
6.  Compile e execute o cliente.  
  
## <a name="see-also"></a>Consulte também  
 [Ativação TCP](../../../../docs/framework/wcf/samples/tcp-activation.md)  
 [Recursos de hospedagem do Windows Server App Fabric](http://go.microsoft.com/fwlink/?LinkId=201276)
