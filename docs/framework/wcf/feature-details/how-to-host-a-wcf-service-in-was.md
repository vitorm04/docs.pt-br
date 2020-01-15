---
title: Como hospedar um serviço do WCF em WAS
ms.date: 03/30/2017
ms.assetid: 9e3e213e-2dce-4f98-81a3-f62f44caeb54
ms.openlocfilehash: 9945e398bbd33776cce808b44388a4415da297a1
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/15/2020
ms.locfileid: "75964780"
---
# <a name="how-to-host-a-wcf-service-in-was"></a>Como hospedar um serviço do WCF em WAS
Este tópico descreve as etapas básicas necessárias para criar um serviço do Windows Process Activation Services (também conhecido como WAS) hospedado Windows Communication Foundation (WCF). O WAS é o novo serviço de ativação de processos que é uma generalização dos recursos de Serviços de Informações da Internet (IIS) que funciona com protocolos de transporte não HTTP. O WCF usa a interface do adaptador de escuta para comunicar as solicitações de ativação recebidas nos protocolos não HTTP com suporte do WCF, como TCP, pipes nomeados e enfileiramento de mensagens.  
  
 Essa opção de hospedagem requer que os componentes WAS de ativação sejam instalados e configurados corretamente, mas não exige que nenhum código de hospedagem seja gravado como parte do aplicativo. Para obter mais informações sobre como instalar e configurar o WAS, consulte [como instalar e configurar componentes de ativação do WCF](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md).  
  
> [!WARNING]
> A ativação do WAS não terá suporte se o pipeline de processamento de solicitação do servidor Web estiver definido para o modo clássico. O pipeline de processamento de solicitações do servidor Web deverá ser definido como modo integrado se a ativação do WAS for usada.  
  
 Quando um serviço WCF é hospedado no WAS, as associações padrão são usadas da maneira usual. No entanto, ao usar o <xref:System.ServiceModel.NetTcpBinding> e o <xref:System.ServiceModel.NetNamedPipeBinding> para configurar um serviço WAS hospedado, uma restrição deve ser satisfeita. Quando pontos de extremidade diferentes usam o mesmo transporte, as configurações de associação precisam corresponder às sete Propriedades a seguir:  
  
- connectionBufferSize  
  
- ChannelInitializationTimeout  
  
- MaxPendingConnections  
  
- MaxOutputDelay  
  
- MaxPendingAccepts  
  
- ConnectionPoolSettings.IdleTimeout  
  
- ConnectionPoolSettings.MaxOutboundConnectionsPerEndpoint  
  
 Caso contrário, o ponto de extremidade que é inicializado primeiro sempre determina os valores dessas propriedades, e os pontos de extremidade adicionados posteriormente geram um <xref:System.ServiceModel.ServiceActivationException> se eles não corresponderem a essas configurações.  
  
 Para a cópia de origem deste exemplo, consulte [ativação TCP](../../../../docs/framework/wcf/samples/tcp-activation.md).  
  
### <a name="to-create-a-basic-service-hosted-by-was"></a>Para criar um serviço básico hospedado pelo WAS  
  
1. Defina um contrato de serviço para o tipo de serviço.  
  
     [!code-csharp[C_HowTo_HostInWAS#1121](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/service.cs#1121)]  
  
2. Implemente o contrato de serviço em uma classe de serviço. Observe que as informações de endereço ou de associação não são especificadas dentro da implementação do serviço. Além disso, o código não precisa ser escrito para recuperar essas informações do arquivo de configuração.  
  
     [!code-csharp[C_HowTo_HostInWAS#1122](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/service.cs#1122)]  
  
3. Crie um arquivo Web. config para definir a associação de <xref:System.ServiceModel.NetTcpBinding> a ser usada pelos pontos de extremidade de `CalculatorService`.  
  
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
  
4. Crie um arquivo Service. svc que contenha o código a seguir.  
  
   ```
   <%@ServiceHost language=c# Service="CalculatorService" %>
   ```
  
5. Coloque o arquivo Service. svc em seu diretório virtual do IIS.  
  
### <a name="to-create-a-client-to-use-the-service"></a>Para criar um cliente para usar o serviço  
  
1. Use a [ferramenta de utilitário de metadados ServiceModel (svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) da linha de comando para gerar código de metadados de serviço.  
  
    ```console
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
    ```  
  
2. O cliente gerado contém a interface `ICalculator` que define o contrato de serviço que a implementação do cliente deve satisfazer.  
  
     [!code-csharp[C_HowTo_HostInWAS#1221](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/client.cs#1221)]  
  
3. O aplicativo cliente gerado também contém a implementação do `ClientCalculator`. Observe que as informações de endereço e de associação não são especificadas em nenhum lugar dentro da implementação do serviço. Além disso, o código não precisa ser escrito para recuperar essas informações do arquivo de configuração.  
  
     [!code-csharp[C_HowTo_HostInWAS#1222](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/client.cs#1222)]  
  
4. A configuração do cliente que usa o <xref:System.ServiceModel.NetTcpBinding> também é gerada pelo svcutil. exe. Esse arquivo deve ser nomeado no arquivo app. config ao usar o Visual Studio.  
  
     [!code-xml[C_HowTo_HostInWAS#2211](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/common/app.config#2211)]   
  
5. Crie uma instância do `ClientCalculator` em um aplicativo e, em seguida, chame as operações de serviço.  
  
     [!code-csharp[C_HowTo_HostInWAS#1223](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/client.cs#1223)]  
  
6. Compile e execute o cliente.  
  
## <a name="see-also"></a>Veja também

- [Ativação TCP](../../../../docs/framework/wcf/samples/tcp-activation.md)
- [Recursos de hospedagem do Windows Server app Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))
