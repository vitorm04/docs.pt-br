---
title: Noções básicas de código de cliente gerado
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: c3f6e4b0-1131-4c94-aa39-a197c5c2f2ca
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 95e27941cece3bfb96c4567516d07bcbe07c7490
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2018
---
# <a name="understanding-generated-client-code"></a>Noções básicas de código de cliente gerado
O [Ferramenta Utilitária de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) gera o código de cliente e um arquivo de configuração do aplicativo cliente para uso na criação de aplicativos cliente. Este tópico fornece um tour dos exemplos de código gerado para cenários de contrato de serviço padrão. [!INCLUDE[crabout](../../../../includes/crabout-md.md)] Criando um aplicativo cliente usando o código gerado, consulte [visão geral do cliente WCF](../../../../docs/framework/wcf/wcf-client-overview.md).  
  
## <a name="overview"></a>Visão geral  
 Se você usar o Visual Studio para gerar [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] tipos de cliente para o seu projeto, você normalmente não precisa examinar o código de cliente gerada. Se você não estiver usando um ambiente de desenvolvimento que executa os mesmos serviços para você, você pode usar uma ferramenta como o Svcutil.exe para gerar o código de cliente e, em seguida, use esse código para desenvolver seu aplicativo cliente.  
  
 Como Svcutil.exe tem várias opções que modificam as informações de tipo gerado, este tópico não aborda todos os cenários. No entanto, as seguintes tarefas padrão envolvem localizando o código gerado:  
  
-   A identificação de interfaces de contrato de serviço.  
  
-   Identificando o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] classe cliente.  
  
-   Identificar os tipos de dados.  
  
-   Identificando os contratos de retorno de chamada para serviços de duplex.  
  
-   Identifica a interface de canal de contrato de serviço auxiliar.  
  
### <a name="finding-service-contract-interfaces"></a>Interfaces de contrato de serviço de localização  
 Para localizar as interfaces que modelam contratos de serviço, procure a interfaces que são marcados com o <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType> atributo. Geralmente, esse atributo pode ser difícil localizar com uma rápida leitura devido à presença de outros atributos e as propriedades de explícitas definidas no próprio atributo. Lembre-se de que a interface de contrato de serviço e a interface de contrato do cliente são dois tipos diferentes. O exemplo de código a seguir mostra o contrato de serviço original.  
  
 [!code-csharp[C_GeneratedCodeFiles#22](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#22)]  
  
 O exemplo de código a seguir mostra o mesmo contrato de serviço geradas pelo Svcutil.exe.  
  
 [!code-csharp[C_GeneratedCodeFiles#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#12)]  
  
 Você pode usar a interface de contrato de serviço gerado junto com o <xref:System.ServiceModel.ChannelFactory?displayProperty=nameWithType> classe para criar um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] objeto do canal com o qual chamar operações de serviço. Para obter mais informações, consulte [como: usar o ChannelFactory](../../../../docs/framework/wcf/feature-details/how-to-use-the-channelfactory.md).  
  
### <a name="finding-wcf-client-classes"></a>Localização de Classes de cliente do WCF  
 Para localizar o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] classe de cliente que implementa o contrato de serviço que você deseja usar, de pesquisa para uma extensão de <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType>, localizado em que o parâmetro de tipo é o contrato de serviço que você interface anteriormente e que estende a interface. O seguinte exemplo de código mostra o <xref:System.ServiceModel.ClientBase%601> classe do tipo `ISampleService`.  
  
 [!code-csharp[C_GeneratedCodeFiles#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#14)]  
  
 Você pode usar isso [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] classe cliente criando uma nova instância dela e chamar os métodos que ele implementa. Os métodos de invocar a operação de serviço com o qual ele foi criado e configurado para interagir. Para obter mais informações, consulte [visão geral do cliente WCF](../../../../docs/framework/wcf/wcf-client-overview.md).  
  
> [!NOTE]
>  Quando o SvcUtil.exe gera uma classe de cliente do WCF, ele adiciona um <xref:System.Diagnostics.DebuggerStepThroughAttribute> para a classe de cliente que impede que os depuradores de percorrendo a classe de cliente do WCF.  
  
### <a name="finding-data-types"></a>Localizando os tipos de dados  
 Para localizar os tipos de dados no código gerado, o mecanismo mais básico é identificar o nome do tipo especificado em um contrato e procurar o código para esse tipo de declaração. Por exemplo, o contrato a seguir especifica que o `SampleMethod` pode retornar uma falha SOAP do tipo `microsoft.wcf.documentation.SampleFault`.  
  
 [!code-csharp[C_GeneratedCodeFiles#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#11)]  
  
 Procurando `SampleFault` localiza o tipo de declaração a seguir.  
  
 [!code-csharp[C_GeneratedCodeFiles#30](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#30)]  
  
 Nesse caso, o tipo de dados é o tipo de detalhe gerado por uma exceção específica no cliente, um <xref:System.ServiceModel.FaultException%601> onde o parâmetro de tipo de detalhe é `microsoft.wcf.documentation.SampleFault`. [!INCLUDE[crabout](../../../../includes/crabout-md.md)] tipos de dados, consulte [especificando a transferência de dados em contratos de serviço](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md). [!INCLUDE[crabout](../../../../includes/crabout-md.md)] tratamento de exceções em clientes, consulte [enviando e recebendo falhas](../../../../docs/framework/wcf/sending-and-receiving-faults.md).  
  
### <a name="finding-callback-contracts-for-duplex-services"></a>Localizando os contratos de retorno de chamada de serviços de Duplex  
 Se você localizar um contrato de serviço para o qual a interface de contrato especifica um valor para o <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType> propriedade e, em seguida, esse contrato especifica um contrato duplex. Contratos duplex requerem que o aplicativo de cliente para criar uma classe de retorno de chamada que implementa o contrato de retorno de chamada e passar uma instância da classe para o <xref:System.ServiceModel.DuplexClientBase%601?displayProperty=nameWithType> ou <xref:System.ServiceModel.DuplexChannelFactory%601?displayProperty=nameWithType> usado para se comunicar com o serviço. [!INCLUDE[crabout](../../../../includes/crabout-md.md)] clientes duplex, consulte [como: serviços do Access com um contrato Duplex](../../../../docs/framework/wcf/feature-details/how-to-access-services-with-a-duplex-contract.md).  
  
 O contrato a seguir especifica um contrato de retorno de chamada do tipo `SampleDuplexHelloCallback`.  
  
 [!code-csharp[C_GeneratedCodeFiles#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/duplexproxycode.cs#2)]
 [!code-vb[C_GeneratedCodeFiles#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_generatedcodefiles/vb/duplexproxycode.vb#2)]  
  
 Procurando esse contrato de retorno de chamada localiza a seguinte interface que o aplicativo cliente deve implementar.  
  
 [!code-csharp[C_GeneratedCodeFiles#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/duplexproxycode.cs#4)]
 [!code-vb[C_GeneratedCodeFiles#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_generatedcodefiles/vb/duplexproxycode.vb#4)]  
  
### <a name="finding-service-contract-channel-interfaces"></a>Interfaces de canal de contrato de serviço de localização  
 Ao usar o <xref:System.ServiceModel.ChannelFactory> classe com uma interface de contrato de serviço, você deve converter para o <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType> interface explicitamente abrir, fechar ou anule o canal. Para tornar mais fácil trabalhar com, a ferramenta Svcutil.exe também gera uma interface do auxiliar que implementa a interface de contrato de serviço e <xref:System.ServiceModel.IClientChannel> para que você possa interagir com a infraestrutura de canal do cliente sem a necessidade de conversão. O código a seguir mostra a definição de um canal de cliente auxiliar que implementa o contrato de serviço anterior.  
  
 [!code-csharp[C_GeneratedCodeFiles#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#13)]  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral do cliente do WCF](../../../../docs/framework/wcf/wcf-client-overview.md)
