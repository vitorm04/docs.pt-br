---
title: Noções básicas de código de cliente gerado
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c3f6e4b0-1131-4c94-aa39-a197c5c2f2ca
ms.openlocfilehash: 6bc921355e54023ead3a308a7877ab609f868221
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968619"
---
# <a name="understanding-generated-client-code"></a>Noções básicas de código de cliente gerado
A [ferramenta de utilitário de metadados ServiceModel (svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) gera o código do cliente e um arquivo de configuração de aplicativo cliente para uso na criação de aplicativos cliente. Este tópico fornece um tour pelos exemplos de código gerados para cenários de contrato de serviço padrão. Para obter mais informações sobre como criar um aplicativo cliente usando o código gerado, consulte [visão geral do cliente WCF](../../../../docs/framework/wcf/wcf-client-overview.md).  
  
## <a name="overview"></a>Visão geral  
 Se você usar o Visual Studio para gerar tipos de cliente Windows Communication Foundation (WCF) para seu projeto, normalmente não será necessário examinar o código do cliente gerado. Se você não estiver usando um ambiente de desenvolvimento que execute os mesmos serviços para você, poderá usar uma ferramenta como SvcUtil. exe para gerar o código do cliente e, em seguida, usar esse código para desenvolver seu aplicativo cliente.  
  
 Como SvcUtil. exe tem várias opções que modificam as informações de tipo geradas, este tópico não aborda todos os cenários. No entanto, as seguintes tarefas padrão envolvem a localização de código gerado:  
  
- Identificando as interfaces do contrato de serviço.  
  
- Identificação da classe de cliente WCF.  
  
- Identificando tipos de dados.  
  
- Identificação de contratos de retorno de chamada para serviços duplex.  
  
- Identificação da interface do canal do contrato do serviço auxiliar.  
  
### <a name="finding-service-contract-interfaces"></a>Localizando interfaces de contrato de serviço  
 Para localizar as interfaces que modelam os contratos de serviço, pesquise as interfaces que <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType> estão marcadas com o atributo. Geralmente, esse atributo pode ser difícil de localizar com uma leitura rápida devido à presença de outros atributos e às propriedades explícitas definidas no próprio atributo. Lembre-se de que a interface do contrato de serviço e a interface de contrato do cliente são dois tipos diferentes. O exemplo de código a seguir mostra o contrato de serviço original.  
  
 [!code-csharp[C_GeneratedCodeFiles#22](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#22)]  
  
 O exemplo de código a seguir mostra o mesmo contrato de serviço gerado por svcutil. exe.  
  
 [!code-csharp[C_GeneratedCodeFiles#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#12)]  
  
 Você pode usar a interface do contrato de serviço gerada junto <xref:System.ServiceModel.ChannelFactory?displayProperty=nameWithType> com a classe para criar um objeto de canal do WCF com o qual invocar operações de serviço. Para obter mais informações, confira [Como: Use a ChannelFactory](../../../../docs/framework/wcf/feature-details/how-to-use-the-channelfactory.md).  
  
### <a name="finding-wcf-client-classes"></a>Localizando classes de cliente WCF  
 Para localizar a classe de cliente WCF que implementa o contrato de serviço que você deseja usar, pesquise por uma <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType>extensão do, em que o parâmetro de tipo é a interface de contrato de serviço que você localizou anteriormente e que estende essa interface. O exemplo de código a seguir <xref:System.ServiceModel.ClientBase%601> mostra a classe `ISampleService`do tipo.  
  
 [!code-csharp[C_GeneratedCodeFiles#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#14)]  
  
 Você pode usar essa classe de cliente WCF criando uma nova instância dela e chamando os métodos que ela implementa. Esses métodos invocam a operação de serviço com a qual ele foi projetado e configurado para interagir. Para obter mais informações, consulte [visão geral do cliente WCF](../../../../docs/framework/wcf/wcf-client-overview.md).  
  
> [!NOTE]
> Quando SvcUtil. exe gera uma classe de cliente WCF, ele adiciona <xref:System.Diagnostics.DebuggerStepThroughAttribute> um à classe de cliente que impede que os depuradores percorram a classe WCF Client.  
  
### <a name="finding-data-types"></a>Localizando tipos de dados  
 Para localizar tipos de dados no código gerado, o mecanismo mais básico é identificar o nome de tipo especificado em um contrato e pesquisar o código para essa declaração de tipo. Por exemplo, o contrato a seguir especifica que `SampleMethod` o pode retornar uma falha SOAP do `microsoft.wcf.documentation.SampleFault`tipo.  
  
 [!code-csharp[C_GeneratedCodeFiles#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#11)]  
  
 `SampleFault` Procurar localiza a seguinte declaração de tipo.  
  
 [!code-csharp[C_GeneratedCodeFiles#30](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#30)]  
  
 Nesse caso, o tipo de dados é o tipo de detalhe lançado por uma exceção específica no cliente, <xref:System.ServiceModel.FaultException%601> um onde o parâmetro de tipo `microsoft.wcf.documentation.SampleFault`de detalhe é. Para obter mais informações sobre tipos de dados, consulte [especificando transferência de dados em contratos de serviço](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md). Para obter mais informações sobre como lidar com exceções em clientes, consulte [envio e recebimento de falhas](../../../../docs/framework/wcf/sending-and-receiving-faults.md).  
  
### <a name="finding-callback-contracts-for-duplex-services"></a>Localizando contratos de retorno de chamada para serviços duplex  
 Se você localizar um contrato de serviço para o qual a interface de contrato especifica um <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType> valor para a propriedade, esse contrato especificará um contrato duplex. Os contratos duplex exigem que o aplicativo cliente crie uma classe de retorno de chamada que implemente o contrato de retorno de chamada e <xref:System.ServiceModel.DuplexClientBase%601?displayProperty=nameWithType> transmita uma instância dessa classe para a ou <xref:System.ServiceModel.DuplexChannelFactory%601?displayProperty=nameWithType> usada para se comunicar com o serviço. Para obter mais informações sobre clientes duplex, [consulte Como: Acesse os serviços com um](../../../../docs/framework/wcf/feature-details/how-to-access-services-with-a-duplex-contract.md)contrato duplex.  
  
 O contrato a seguir especifica um contrato de retorno `SampleDuplexHelloCallback`de chamada do tipo.  
  
 [!code-csharp[C_GeneratedCodeFiles#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/duplexproxycode.cs#2)]
 [!code-vb[C_GeneratedCodeFiles#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_generatedcodefiles/vb/duplexproxycode.vb#2)]  
  
 Pesquisar esse contrato de retorno de chamada localiza a seguinte interface que o aplicativo cliente deve implementar.  
  
 [!code-csharp[C_GeneratedCodeFiles#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/duplexproxycode.cs#4)]
 [!code-vb[C_GeneratedCodeFiles#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_generatedcodefiles/vb/duplexproxycode.vb#4)]  
  
### <a name="finding-service-contract-channel-interfaces"></a>Localizando interfaces de canal do contrato de serviço  
 Ao usar a <xref:System.ServiceModel.ChannelFactory> classe com uma interface de contrato de serviço, você deve converter <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType> na interface para abrir, fechar ou abortar o canal explicitamente. Para facilitar o trabalho com o, a ferramenta svcutil. exe também gera uma interface auxiliar que implementa a interface do contrato de serviço e <xref:System.ServiceModel.IClientChannel> para permitir que você interaja com a infraestrutura de canal do cliente sem precisar fazer a conversão. O código a seguir mostra a definição de um canal cliente auxiliar que implementa o contrato de serviço anterior.  
  
 [!code-csharp[C_GeneratedCodeFiles#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#13)]  
  
## <a name="see-also"></a>Consulte também

- [Visão geral do cliente do WCF](../../../../docs/framework/wcf/wcf-client-overview.md)
