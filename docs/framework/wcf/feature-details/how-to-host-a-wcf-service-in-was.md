---
title: 'Como: hospedar um serviço WCF no WAS'
ms.date: 03/30/2017
ms.assetid: 9e3e213e-2dce-4f98-81a3-f62f44caeb54
ms.openlocfilehash: 9c60248342c9cfa0e1b70d86df47a478dd34a60f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59195443"
---
# <a name="how-to-host-a-wcf-service-in-was"></a>Como: hospedar um serviço WCF no WAS
Este tópico descreve as etapas básicas necessárias para criar um serviços de ativação de processo do Windows (também conhecido como WAS) hospedado o serviço Windows Communication Foundation (WCF). FOI é o novo serviço de ativação de processo é uma generalização dos recursos de serviços de informações da Internet (IIS) que funcionam com protocolos de transporte não HTTP. O WCF usa o adaptador de escuta para comunicar as solicitações de ativação recebidas pelos protocolos não HTTP com suporte do WCF, como TCP, pipes nomeados e enfileiramento de mensagens.  
  
 Essa opção de hospedagem requer que os componentes de ativação do WAS são instalados e configurados corretamente, mas ele não requer nenhum código de hospedagem a ser gravado como parte do aplicativo. Para obter mais informações sobre como instalar e configurando o WAS, consulte [como: Instalar e configurar os componentes de ativação do WCF](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md).  
  
> [!WARNING]
>  Não era oferece suporte à ativação se o pipeline de processamento de solicitação do servidor web está definido para o modo clássico. Pipeline de processamento de solicitação do servidor web deve ser definido para o modo integrado se a ativação do WAS deve ser usada.  
  
 Quando um serviço WCF é hospedado no WAS, as ligações padrão são usadas como de costume. No entanto, ao usar o <xref:System.ServiceModel.NetTcpBinding> e o <xref:System.ServiceModel.NetNamedPipeBinding> para configurar um serviço hospedado do WAS, uma restrição deve ser atendida. Quando diferentes pontos de extremidade usam o mesmo transporte, as configurações de ligação tem que corresponder as sete propriedades a seguir:  
  
-   ConnectionBufferSize  
  
-   ChannelInitializationTimeout  
  
-   MaxPendingConnections  
  
-   MaxOutputDelay  
  
-   MaxPendingAccepts  
  
-   ConnectionPoolSettings.IdleTimeout  
  
-   ConnectionPoolSettings.MaxOutboundConnectionsPerEndpoint  
  
 Caso contrário, o ponto de extremidade que é inicializado pela primeira vez sempre determina os valores dessas propriedades e os pontos de extremidade adicionados posteriormente lançar um <xref:System.ServiceModel.ServiceActivationException> se eles não corresponderem a essas configurações.  
  
 Para a cópia de origem deste exemplo, consulte [ativação TCP](../../../../docs/framework/wcf/samples/tcp-activation.md).  
  
### <a name="to-create-a-basic-service-hosted-by-was"></a>Para criar um serviço básico hospedado pelo WAS  
  
1.  Defina um contrato de serviço para o tipo de serviço.  
  
     [!code-csharp[C_HowTo_HostInWAS#1121](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/service.cs#1121)]  
  
2.  Implemente o contrato de serviço em uma classe de serviço. Observe que as informações de associação ou o endereço não são especificadas dentro da implementação do serviço. Além disso, código não precisa ser escrita para recuperar essas informações do arquivo de configuração.  
  
     [!code-csharp[C_HowTo_HostInWAS#1122](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/service.cs#1122)]  
  
3.  Crie um arquivo Web. config para definir a <xref:System.ServiceModel.NetTcpBinding> associação a ser usada pelo `CalculatorService` pontos de extremidade.  
  
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
  
4.  Crie um arquivo Service SVC que contém o código a seguir.  
  
    ```  
    <%@ServiceHost language=c# Service="CalculatorService" %>   
    ```  
  
5.  Coloque o arquivo Service svc no diretório virtual IIS.  
  
### <a name="to-create-a-client-to-use-the-service"></a>Para criar um cliente para usar o serviço  
  
1.  Use [ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) da linha de comando para gerar o código de metadados de serviço.  
  
    ```  
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>   
    ```  
  
2.  O cliente que é gerado contém o `ICalculator` interface que define o contrato de serviço que a implementação do cliente deve satisfazer.  
  
     [!code-csharp[C_HowTo_HostInWAS#1221](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/client.cs#1221)]  
  
3.  O aplicativo de cliente gerado também contém a implementação do `ClientCalculator`. Observe que as informações de endereço e a associação não são especificadas em qualquer lugar dentro da implementação do serviço. Além disso, código não precisa ser escrita para recuperar essas informações do arquivo de configuração.  
  
     [!code-csharp[C_HowTo_HostInWAS#1222](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/client.cs#1222)]  
  
4.  A configuração do cliente que usa o <xref:System.ServiceModel.NetTcpBinding> também é gerado pelo Svcutil.exe. Este arquivo deve ser nomeado no arquivo App. config ao usar o Visual Studio.  
  
     [!code-xml[C_HowTo_HostInWAS#2211](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/common/app.config#2211)]   
  
5.  Criar uma instância das `ClientCalculator` em um aplicativo e, em seguida, chamar as operações de serviço.  
  
     [!code-csharp[C_HowTo_HostInWAS#1223](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/client.cs#1223)]  
  
6.  Compile e execute o cliente.  
  
## <a name="see-also"></a>Consulte também

- [Ativação TCP](../../../../docs/framework/wcf/samples/tcp-activation.md)
- [Recursos de hospedagem do Windows Server AppFabric](https://go.microsoft.com/fwlink/?LinkId=201276)
