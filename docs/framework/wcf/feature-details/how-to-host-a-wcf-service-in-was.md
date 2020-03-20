---
title: Como hospedar um serviço do WCF em WAS
ms.date: 03/30/2017
ms.assetid: 9e3e213e-2dce-4f98-81a3-f62f44caeb54
ms.openlocfilehash: 823c3b8452a3fd1c95758d2d09a9effdf02075c8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184911"
---
# <a name="how-to-host-a-wcf-service-in-was"></a>Como hospedar um serviço do WCF em WAS
Este tópico descreve as etapas básicas necessárias para criar um serviço de ativação de processos do Windows (também conhecido como WAS) hospedado no Serviço da Windows Communication Foundation (WCF). O WAS é o novo serviço de ativação de processos que é uma generalização dos recursos dos Serviços de Informação da Internet (IIS) que trabalham com protocolos de transporte não-HTTP. O WCF usa a interface do adaptador de ouvinte para comunicar solicitações de ativação recebidas pelos protocolos não-HTTP suportados pelo WCF, como TCP, tubos nomeados e Fila de Mensagens.  
  
 Esta opção de hospedagem exige que os componentes de ativação WAS estejam instalados e configurados corretamente, mas não requer nenhum código de hospedagem para ser gravado como parte do aplicativo. Para obter mais informações sobre como instalar e configurar was, consulte [Como: Instalar e configurar componentes de ativação wcf](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md).  
  
> [!WARNING]
> A ativação was não é suportada se o pipeline de processamento de solicitação do servidor web estiver definido para o modo Classic. O pipeline de processamento de solicitação do servidor web deve ser definido como modo integrado se a ativação WAS for usada.  
  
 Quando um serviço WCF é hospedado no WAS, as vinculações padrão são usadas da maneira usual. No entanto, <xref:System.ServiceModel.NetTcpBinding> ao <xref:System.ServiceModel.NetNamedPipeBinding> usar o e o para configurar um serviço hospedado em WAS, uma restrição deve ser satisfeita. Quando diferentes pontos finais usam o mesmo transporte, as configurações de vinculação têm de corresponder às sete propriedades a seguir:  
  
- Bufferde conexão  
  
- ChannelInitializationTimeout  
  
- MaxPendingConnections  
  
- MaxOutputDelay  
  
- MaxPendingAccepts  
  
- ConexãoPoolSettings.IdleTimeout  
  
- ConexãoConfigurações de pool.MaxOutboundConnectionsPerEndpoint  
  
 Caso contrário, o ponto final que é inicializado primeiro sempre determina os valores dessas propriedades, e os pontos finais adicionados posteriormente jogam um <xref:System.ServiceModel.ServiceActivationException> se eles não corresponderem a essas configurações.  
  
 Para obter a cópia de origem deste exemplo, consulte [Ativação TCP](../../../../docs/framework/wcf/samples/tcp-activation.md).  
  
### <a name="to-create-a-basic-service-hosted-by-was"></a>Para criar um serviço básico hospedado pela WAS  
  
1. Defina um contrato de serviço para o tipo de serviço.  
  
     [!code-csharp[C_HowTo_HostInWAS#1121](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/service.cs#1121)]  
  
2. Implemente o contrato de serviço em uma classe de serviço. Observe que as informações de endereço ou vinculação não são especificadas dentro da implementação do serviço. Além disso, o código não precisa ser escrito para recuperar essas informações do arquivo de configuração.  
  
     [!code-csharp[C_HowTo_HostInWAS#1122](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/service.cs#1122)]  
  
3. Crie um arquivo Web.config <xref:System.ServiceModel.NetTcpBinding> para definir a `CalculatorService` vinculação a ser usada pelos pontos finais.  
  
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
  
4. Crie um arquivo Service.svc que contenha o seguinte código.  
  
   ```
   <%@ServiceHost language=c# Service="CalculatorService" %>
   ```
  
5. Coloque o arquivo Service.svc em seu diretório virtual IIS.  
  
### <a name="to-create-a-client-to-use-the-service"></a>Para criar um cliente para usar o serviço  
  
1. Use [serviceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) da linha de comando para gerar código a partir de metadados de serviço.  
  
    ```console
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
    ```  
  
2. O cliente gerado contém `ICalculator` a interface que define o contrato de serviço que a implementação do cliente deve satisfazer.  
  
     [!code-csharp[C_HowTo_HostInWAS#1221](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/client.cs#1221)]  
  
3. O aplicativo cliente gerado também `ClientCalculator`contém a implementação do . Observe que o endereço e as informações de vinculação não são especificados em nenhum lugar dentro da implementação do serviço. Além disso, o código não precisa ser escrito para recuperar essas informações do arquivo de configuração.  
  
     [!code-csharp[C_HowTo_HostInWAS#1222](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/client.cs#1222)]  
  
4. A configuração para o <xref:System.ServiceModel.NetTcpBinding> cliente que usa o também é gerada por Svcutil.exe. Este arquivo deve ser nomeado no arquivo App.config ao usar o Visual Studio.  
  
     [!code-xml[C_HowTo_HostInWAS#2211](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/common/app.config#2211)]
  
5. Crie uma instância `ClientCalculator` do em um aplicativo e, em seguida, chame as operações de serviço.  
  
     [!code-csharp[C_HowTo_HostInWAS#1223](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/client.cs#1223)]  
  
6. Compile e execute o cliente.  
  
## <a name="see-also"></a>Confira também

- [Ativação TCP](../../../../docs/framework/wcf/samples/tcp-activation.md)
- [Recursos de hospedagem do Windows Server AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))
