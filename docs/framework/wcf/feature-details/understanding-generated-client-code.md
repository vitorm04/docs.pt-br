---
title: Noções básicas de código de cliente gerado
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c3f6e4b0-1131-4c94-aa39-a197c5c2f2ca
ms.openlocfilehash: 226b77d1c638ec4f8505140332ad35d4029ef0b0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59189151"
---
# <a name="understanding-generated-client-code"></a>Noções básicas de código de cliente gerado
O [ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) gera o código de cliente e um arquivo de configuração de aplicativo do cliente para uso na criação de aplicativos cliente. Este tópico fornece um tour dos exemplos de código gerado para cenários de contrato de serviço padrão. Para obter mais informações sobre a criação de um aplicativo cliente usando o código gerado, consulte [visão geral do cliente WCF](../../../../docs/framework/wcf/wcf-client-overview.md).  
  
## <a name="overview"></a>Visão geral  
 Se você usar o Visual Studio para gerar tipos de cliente do Windows Communication Foundation (WCF) para seu projeto, você normalmente não precisará examinar o código de cliente gerado. Se você não estiver usando um ambiente de desenvolvimento que executa os mesmos serviços para você, você pode usar uma ferramenta como Svcutil.exe para gerar o código do cliente e, em seguida, usar esse código para desenvolver seu aplicativo cliente.  
  
 Como Svcutil.exe tem várias opções que modificam as informações de tipo gerado, este tópico não aborda todos os cenários. No entanto, as seguintes tarefas padrão envolvem localizando o código gerado:  
  
-   Identificando as interfaces de contrato de serviço.  
  
-   Identifica a classe de cliente do WCF.  
  
-   Identificar os tipos de dados.  
  
-   Identificando os contratos de retorno de chamada para serviços duplex.  
  
-   Identifica a interface de canal de contrato de serviço auxiliar.  
  
### <a name="finding-service-contract-interfaces"></a>Interfaces de contrato de serviço de localização  
 Para localizar as interfaces que modelam contratos de serviço, procure a interfaces que são marcados com o <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType> atributo. Geralmente, esse atributo pode ser difícil localizar com uma rápida devido à presença de outros atributos de leitura e as propriedades explícitas definido no atributo em si. Lembre-se de que a interface de contrato de serviço e a interface de contrato do cliente são dois tipos diferentes. O exemplo de código a seguir mostra o contrato de serviço original.  
  
 [!code-csharp[C_GeneratedCodeFiles#22](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#22)]  
  
 O exemplo de código a seguir mostra o mesmo contrato de serviço gerada pelo Svcutil.exe.  
  
 [!code-csharp[C_GeneratedCodeFiles#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#12)]  
  
 Você pode usar a interface de contrato de serviço gerado junto com o <xref:System.ServiceModel.ChannelFactory?displayProperty=nameWithType> classe para criar um objeto de canal WCF com o qual invocar operações de serviço. Para obter mais informações, confira [Como: Usar o ChannelFactory](../../../../docs/framework/wcf/feature-details/how-to-use-the-channelfactory.md).  
  
### <a name="finding-wcf-client-classes"></a>Localizando as Classes de cliente do WCF  
 Para localizar a classe de cliente do WCF que implementa o contrato de serviço que você deseja usar, procure uma extensão da <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType>, localizado em que o parâmetro de tipo é o contrato de serviço de interface que você anteriormente e que se estende essa interface. O seguinte exemplo de código mostra a <xref:System.ServiceModel.ClientBase%601> classe do tipo `ISampleService`.  
  
 [!code-csharp[C_GeneratedCodeFiles#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#14)]  
  
 Você pode usar essa classe de cliente do WCF, criando uma nova instância dele e chamando os métodos que ele implementa. Esses métodos invocam a operação de serviço com o qual ele foi criado e configurado para interagir. Para obter mais informações, consulte [visão geral do cliente WCF](../../../../docs/framework/wcf/wcf-client-overview.md).  
  
> [!NOTE]
>  Quando SvcUtil.exe gera uma classe de cliente do WCF, ele adiciona um <xref:System.Diagnostics.DebuggerStepThroughAttribute> à classe de cliente que impede que os depuradores de percorrer a classe de cliente do WCF.  
  
### <a name="finding-data-types"></a>Localizando os tipos de dados  
 Para localizar os tipos de dados no código gerado, o mecanismo mais básico é identificar o nome do tipo especificado em um contrato e procurar o código para esse tipo de declaração. Por exemplo, o seguinte contrato especifica que o `SampleMethod` pode retornar uma falha SOAP do tipo `microsoft.wcf.documentation.SampleFault`.  
  
 [!code-csharp[C_GeneratedCodeFiles#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#11)]  
  
 Procurando `SampleFault` localiza a seguinte declaração de tipo.  
  
 [!code-csharp[C_GeneratedCodeFiles#30](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#30)]  
  
 Nesse caso, o tipo de dados é o tipo de detalhe gerado por uma exceção específica no cliente, uma <xref:System.ServiceModel.FaultException%601> onde o parâmetro de tipo de detalhe é `microsoft.wcf.documentation.SampleFault`. Para obter mais informações sobre tipos de dados, consulte [especificando a transferência de dados em contratos de serviço](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md). Para obter mais informações sobre como manipular exceções em clientes, consulte [enviando e recebendo falhas](../../../../docs/framework/wcf/sending-and-receiving-faults.md).  
  
### <a name="finding-callback-contracts-for-duplex-services"></a>Localizando os contratos de retorno de chamada para serviços Duplex  
 Se você localizar um contrato de serviço para o qual a interface de contrato especifica um valor para o <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType> propriedade e, em seguida, esse contrato especifica um contrato duplex. Contratos duplex exigem que o aplicativo de cliente para criar uma classe de retorno de chamada que implementa o contrato de retorno de chamada e passar uma instância da classe para o <xref:System.ServiceModel.DuplexClientBase%601?displayProperty=nameWithType> ou <xref:System.ServiceModel.DuplexChannelFactory%601?displayProperty=nameWithType> usado para se comunicar com o serviço. Para obter mais informações sobre clientes duplex, consulte [como: Acessar os serviços com um contrato Duplex](../../../../docs/framework/wcf/feature-details/how-to-access-services-with-a-duplex-contract.md).  
  
 O seguinte contrato especifica um contrato de retorno de chamada do tipo `SampleDuplexHelloCallback`.  
  
 [!code-csharp[C_GeneratedCodeFiles#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/duplexproxycode.cs#2)]
 [!code-vb[C_GeneratedCodeFiles#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_generatedcodefiles/vb/duplexproxycode.vb#2)]  
  
 Procurando por esse contrato de retorno de chamada localiza a seguinte interface que o aplicativo cliente deve implementar.  
  
 [!code-csharp[C_GeneratedCodeFiles#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/duplexproxycode.cs#4)]
 [!code-vb[C_GeneratedCodeFiles#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_generatedcodefiles/vb/duplexproxycode.vb#4)]  
  
### <a name="finding-service-contract-channel-interfaces"></a>Interfaces de canal de contrato de serviço de localização  
 Ao usar o <xref:System.ServiceModel.ChannelFactory> classe com uma interface de contrato de serviço, você deve converter para o <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType> interface explicitamente abrir, fechar ou anular o canal. Para tornar mais fácil trabalhar com, a ferramenta Svcutil.exe também gera uma interface de auxiliar que implementa tanto a interface de contrato de serviço e <xref:System.ServiceModel.IClientChannel> para que você possa interagir com a infra-estrutura de canal do cliente sem a necessidade de converter. O código a seguir mostra a definição de um canal de cliente do auxiliar que implementa o contrato de serviço anterior.  
  
 [!code-csharp[C_GeneratedCodeFiles#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#13)]  
  
## <a name="see-also"></a>Consulte também

- [Visão geral do cliente do WCF](../../../../docs/framework/wcf/wcf-client-overview.md)
