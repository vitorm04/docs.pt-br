---
title: Arquitetura do cliente
ms.date: 03/30/2017
ms.assetid: 02624403-0d77-41cb-9a86-ab55e98c7966
ms.openlocfilehash: 4ced24f370e2ab54528c6adb2b3617d3d849e745
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="client-architecture"></a>Arquitetura do cliente
Aplicativos usam objetos de cliente do Windows Communication Foundation (WCF) para chamar operações de serviço. Este tópico discute os objetos de cliente do WCF, canais de cliente do WCF e suas relações com a arquitetura de canal subjacente. Para obter uma visão geral básica de objetos de cliente do WCF, consulte [visão geral do cliente WCF](../../../../docs/framework/wcf/wcf-client-overview.md). Para obter mais informações sobre a camada do canal, consulte [estendendo a camada do canal](../../../../docs/framework/wcf/extending/extending-the-channel-layer.md).  
  
## <a name="overview"></a>Visão geral  
 O modelo de serviço no tempo de execução cria a clientes do WCF, que são compostos das seguintes opções:  
  
-   Uma implementação de cliente gerado automaticamente de um contrato de serviço, que transforma a chamadas de código do aplicativo em mensagens de saída e mensagens de resposta se transforma em parâmetros de saída e valores de retorno que seu aplicativo pode recuperar.  
  
-   Uma implementação de uma interface de controle (<xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType>) que agrupa várias interfaces e fornece acesso para controlar a funcionalidade, principalmente a possibilidade de fechar a sessão de cliente e descartar o canal.  
  
-   Um canal de cliente que é criado com base nas definições de configuração especificadas pela associação usada.  
  
 Aplicativos podem criar esses clientes sob demanda, por meio de um <xref:System.ServiceModel.ChannelFactory?displayProperty=nameWithType> ou criando uma instância de um <xref:System.ServiceModel.ClientBase%601> classe derivada, que é gerada pelo [Ferramenta Utilitária de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Essas classes de cliente pronta encapsular e delegar uma implementação de canal do cliente que é construído dinamicamente por um <xref:System.ServiceModel.ChannelFactory>. Portanto, o canal do cliente e a fábrica de canais que produz a eles são o ponto focal de interesse para esta discussão.  
  
## <a name="client-objects-and-client-channels"></a>Objetos de cliente e canais de cliente  
 A interface base de clientes do WCF é o <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType> interface, que expõe a funcionalidade de cliente principal, bem como a funcionalidade do objeto de comunicação básica de <xref:System.ServiceModel.ICommunicationObject?displayProperty=nameWithType>, a funcionalidade de contexto de <xref:System.ServiceModel.IContextChannel?displayProperty=nameWithType>e o comportamento extensível do <xref:System.ServiceModel.IExtensibleObject%601?displayProperty=nameWithType>.  
  
 O <xref:System.ServiceModel.IClientChannel> interface, no entanto, não define um contrato de serviço. Aqueles são declarados pela interface de contrato de serviço (normalmente gerada a partir de metadados de serviço usando uma ferramenta como o [Ferramenta Utilitária de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)). Tipos de cliente do WCF estendem ambos <xref:System.ServiceModel.IClientChannel> e a interface de contrato de serviço de destino para habilitar aplicativos para chamar operações diretamente e também ter acesso à funcionalidade de tempo de execução do lado do cliente. Criando um cliente WCF fornece WCF<xref:System.ServiceModel.ChannelFactory?displayProperty=nameWithType> objetos com as informações necessárias para criar um tempo de execução que podem se conectar e interagir com o ponto de extremidade de serviço configurado.  
  
 Como mencionado anteriormente, os dois tipos de cliente do WCF devem ser configurados antes de você pode usá-los. Os tipos de cliente WCF mais simples são objetos que derivam de <xref:System.ServiceModel.ClientBase%601> (ou <xref:System.ServiceModel.DuplexClientBase%601> se o contrato de serviço é um contrato duplex). Você pode criar esses tipos usando um construtor, configurado programaticamente, ou usando um arquivo de configuração e, em seguida, chamado diretamente para chamar operações de serviço. Para uma visão geral básica de <xref:System.ServiceModel.ClientBase%601> objetos, consulte [visão geral do cliente WCF](../../../../docs/framework/wcf/wcf-client-overview.md).  
  
 O segundo tipo é gerado em tempo de execução de uma chamada para o <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A> método. Aplicativos preocupados com controle rigoroso das especificações de comunicação normalmente usam esse tipo de cliente, chamado um *objeto do canal do cliente*, porque ele permite uma interação mais direta do tempo de execução de cliente subjacente e de canal sistema.  
  
## <a name="channel-factories"></a>Fábricas de canais  
 A classe que é responsável pela criação subjacente que dá suporte a chamadas de cliente tempo de execução é o <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> classe. Use objetos de canal de objetos de cliente do WCF e o cliente WCF um <xref:System.ServiceModel.ChannelFactory%601> objeto para criar instâncias; o <xref:System.ServiceModel.ClientBase%601> objeto derivado de cliente encapsula a manipulação de fábrica de canais, mas para um número de cenários é perfeitamente razoável usar o fábrica de canais diretamente. O cenário comum para isso é se você deseja criar repetidamente novo cliente canais de uma fábrica existente. Se você estiver usando um objeto de cliente, você pode obter a fábrica de canais subjacente de um objeto de cliente WCF chamando o <xref:System.ServiceModel.ClientBase%601.ChannelFactory%2A?displayProperty=nameWithType> propriedade.  
  
 O mais importante sobre fábricas de canais é que criar novas instâncias do cliente de canais para a configuração fornecida-los antes de chamar <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A?displayProperty=nameWithType>. Depois de você chamar <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A> (ou <xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType>, <xref:System.ServiceModel.ClientBase%601.CreateChannel%2A?displayProperty=nameWithType>, ou qualquer operação em um objeto de cliente do WCF), você não pode modificar a fábrica de canais e pretende obter canais para instâncias de serviço diferente, mesmo se você estiver alterando apenas o endereço do ponto de extremidade de destino. Se você quiser criar um objeto de cliente ou um canal de cliente com uma configuração diferente, você deve criar uma nova fábrica de canais primeiro.  
  
 Para obter mais informações sobre diversos problemas usando objetos de cliente do WCF e canais de cliente do WCF, consulte [Acessando serviços usando um cliente WCF](../../../../docs/framework/wcf/feature-details/accessing-services-using-a-client.md).  
  
 As seções a seguir descrevem a criação e uso de objetos de canal de cliente do WCF.  
  
#### <a name="creating-a-new-wcf-client-channel-object"></a>Criando um novo objeto de canal de cliente do WCF  
 Para ilustrar o uso de um canal de cliente, suponha que o contrato de serviço a seguir foi gerado.  
  
 [!code-csharp[C_GeneratedCodeFiles#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#12)]  
  
 Para se conectar a um `ISampleService` de serviço, use a interface de contrato gerado diretamente com uma fábrica de canais (<xref:System.ServiceModel.ChannelFactory%601>). Depois de criar e configurar uma fábrica de canais de um contrato específico, você pode chamar o <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A> método para retornar o cliente objetos de canal que você pode usar para se comunicar com um `ISampleService` serviço.  
  
 Ao usar o <xref:System.ServiceModel.ChannelFactory%601> classe com uma interface de contrato de serviço, você deve converter para o <xref:System.ServiceModel.IClientChannel> interface explicitamente abrir, fechar ou anule o canal. Para tornar mais fácil trabalhar com, a ferramenta Svcutil.exe também gera uma interface do auxiliar que implementa a interface de contrato de serviço e <xref:System.ServiceModel.IClientChannel> para que você possa interagir com a infraestrutura de canal do cliente sem a necessidade de conversão. O código a seguir mostra a definição de um canal de cliente auxiliar que implementa o contrato de serviço anterior.  
  
 [!code-csharp[C_GeneratedCodeFiles#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#13)]  
  
#### <a name="creating-a-new-wcf-client-channel-object"></a>Criando um novo objeto de canal de cliente do WCF  
 Para usar um canal de cliente para se conectar a um `ISampleService` de serviço, use a interface de contrato gerado (ou a versão de auxiliar) diretamente com uma fábrica de canais, passando o tipo de interface de contrato como o parâmetro de tipo. Depois que uma fábrica de canais de um contrato específico foi criada e configurada, você pode chamar o <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A?displayProperty=nameWithType> método para retornar o cliente objetos de canal que você pode usar para se comunicar com um `ISampleService` serviço.  
  
 Quando criado, os objetos de canal cliente implementam <xref:System.ServiceModel.IClientChannel> e a interface de contrato. Portanto, você pode usá-los diretamente para chamar as operações que interagem com um serviço que dá suporte a esse contrato.  
  
 A diferença entre usar objetos de cliente e objetos de canal do cliente é simplesmente um controle e a facilidade de uso para desenvolvedores. Muitos desenvolvedores que estão confortáveis para trabalhar com classes e objetos vão preferir usar o objeto de cliente do WCF em vez do canal de cliente do WCF.  
  
 Para obter um exemplo, consulte [como: usar o ChannelFactory](../../../../docs/framework/wcf/feature-details/how-to-use-the-channelfactory.md).
