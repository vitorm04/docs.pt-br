---
title: Especificando um endereço de ponto de extremidade
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- endpoints [WCF], addressing
ms.assetid: ac24f5ad-9558-4298-b168-c473c68e819b
ms.openlocfilehash: 47a7bb42ea2441ffef2fd27f26a20beceb871173
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72321129"
---
# <a name="specifying-an-endpoint-address"></a>Especificando um endereço de ponto de extremidade

Toda a comunicação com um serviço Windows Communication Foundation (WCF) ocorre por meio de seus pontos de extremidade. Cada <xref:System.ServiceModel.Description.ServiceEndpoint> contém uma <xref:System.ServiceModel.Description.ServiceEndpoint.Address%2A>, uma <xref:System.ServiceModel.Description.ServiceEndpoint.Binding%2A>e uma <xref:System.ServiceModel.Description.ServiceEndpoint.Contract%2A>. O contrato especifica quais operações estão disponíveis. A associação especifica como se comunicar com o serviço e o endereço especifica onde encontrar o serviço. Cada ponto de extremidade deve ter um endereço exclusivo. O endereço do ponto de extremidade é representado pela classe <xref:System.ServiceModel.EndpointAddress>, que contém um Uniform Resource Identifier (URI) que representa o endereço do serviço, um <xref:System.ServiceModel.EndpointAddress.Identity%2A>, que representa a identidade de segurança do serviço e uma coleção de <xref:System.ServiceModel.EndpointAddress.Headers%2A>opcional. Os cabeçalhos opcionais fornecem informações de endereçamento mais detalhadas para identificar ou interagir com o ponto de extremidade. Por exemplo, os cabeçalhos podem indicar como processar uma mensagem de entrada, em que o ponto de extremidade deve enviar uma mensagem de resposta ou qual instância de um serviço usar para processar uma mensagem de entrada de um usuário específico quando várias instâncias estão disponíveis.

## <a name="definition-of-an-endpoint-address"></a>Definição de um endereço de ponto de extremidade

No WCF, um <xref:System.ServiceModel.EndpointAddress> modela uma referência de ponto de extremidade (EPR), conforme definido no padrão WS-Addressing.

O URI de endereço para a maioria dos transportes tem quatro partes. Por exemplo, esse URI `http://www.fabrikam.com:322/mathservice.svc/secureEndpoint` tem as quatro partes a seguir:

- Esquema: http:

- Computador: `www.fabrikam.com`

- Adicional Porta: 322

- Caminho:/mathservice.svc/secureEndpoint

Parte do modelo EPR é que cada referência de ponto de extremidade pode transportar alguns parâmetros de referência que adicionam informações de identificação extras. No WCF, esses parâmetros de referência são modelados como instâncias da classe <xref:System.ServiceModel.Channels.AddressHeader>.

O endereço do ponto de extremidade para um serviço pode ser especificado de forma imperativa usando o código ou declarativamente por meio da configuração. A definição de pontos de extremidade no código geralmente não é prática porque as associações e os endereços para um serviço implantado são normalmente diferentes daqueles usados enquanto o serviço está sendo desenvolvido. Em geral, é mais prático definir pontos de extremidade de serviço usando a configuração em vez de código. Manter a ligação e as informações de endereçamento do código permite que elas sejam alteradas sem a necessidade de recompilar e reimplantar o aplicativo. Se nenhum ponto de extremidade for especificado no código ou na configuração, o tempo de execução adicionará um ponto de extremidade padrão em cada endereço base para cada contrato implementado pelo serviço.

Há duas maneiras de especificar endereços de ponto de extremidade para um serviço no WCF. Você pode especificar um endereço absoluto para cada ponto de extremidade associado ao serviço ou pode fornecer um endereço base para o <xref:System.ServiceModel.ServiceHost> de um serviço e, em seguida, especificar um endereço para cada ponto de extremidade associado a esse serviço definido em relação a esse endereço base. Você pode usar cada um desses procedimentos para especificar os endereços de ponto de extremidade para um serviço em qualquer configuração ou código. Se você não especificar um endereço relativo, o serviço usará o endereço base. Você também pode ter vários endereços base para um serviço, mas cada serviço é permitido apenas um endereço de base para cada transporte. Se você tiver vários pontos de extremidade, cada um deles configurado com uma associação diferente, seus endereços deverão ser exclusivos. Os pontos de extremidade que usam a mesma ligação, mas contratos diferentes, podem usar o mesmo endereço.

Ao hospedar com o IIS, você não gerencia a instância do <xref:System.ServiceModel.ServiceHost> por conta própria. O endereço base é sempre o endereço especificado no arquivo. svc para o serviço ao hospedar no IIS. Portanto, você deve usar endereços de ponto de extremidade relativos para pontos de extremidades de serviço hospedados no IIS. O fornecimento de um endereço de ponto de extremidade totalmente qualificado pode levar a erros na implantação do serviço. Para obter mais informações, consulte [implantando um serviço WCF hospedado por serviços de informações da Internet](./feature-details/deploying-an-internet-information-services-hosted-wcf-service.md).

## <a name="defining-endpoint-addresses-in-configuration"></a>Definindo endereços de ponto de extremidade na configuração

Para definir um ponto de extremidade em um arquivo de configuração, use o elemento [\<ponto de extremidade >](../configure-apps/file-schema/wcf/endpoint-element.md) .

[!code-xml[S_UEHelloWorld#5](../../../samples/snippets/common/VS_Snippets_CFX/s_uehelloworld/common/serviceapp2.config#5)]

Quando o método de <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> é chamado (ou seja, quando o aplicativo de hospedagem tenta iniciar o serviço), o sistema procura um elemento de [> de serviço de\<](../configure-apps/file-schema/wcf/service.md) com um atributo de nome que ESPECIFIQUE "UE. Samples. HelloService ". Se o elemento de [> de serviço de\<](../configure-apps/file-schema/wcf/service.md) for encontrado, o sistema carregará a classe especificada e criará pontos de extremidade usando as definições de Endpoint fornecidas no arquivo de configuração. Esse mecanismo permite que você carregue e inicie um serviço com duas linhas de código enquanto mantém a ligação e o endereçamento de informações do seu código. A vantagem dessa abordagem é que essas alterações podem ser feitas sem a necessidade de recompilar ou reimplantar o aplicativo.

Os cabeçalhos opcionais são declarados em um [\<cabeçalhos >](../configure-apps/file-schema/wcf/headers-element.md). Veja a seguir um exemplo dos elementos usados para especificar pontos de extremidade para um serviço em um arquivo de configuração que distingue entre dois cabeçalhos: clientes "Gold" de `http://tempuri1.org/` e clientes "Standard" da `http://tempuri2.org/`. O cliente que chama esse serviço deve ter os [cabeçalhos de\<apropriados >](../configure-apps/file-schema/wcf/headers-element.md) em seu arquivo de configuração.

[!code-xml[S_UEHelloWorld#1](../../../samples/snippets/common/VS_Snippets_CFX/s_uehelloworld/common/serviceapp.config#1)]

Os cabeçalhos também podem ser definidos em mensagens individuais em vez de todas as mensagens em um ponto de extremidade (conforme mostrado anteriormente). Isso é feito usando <xref:System.ServiceModel.OperationContextScope> para criar um novo contexto em um aplicativo cliente para adicionar um cabeçalho personalizado à mensagem de saída, conforme mostrado no exemplo a seguir.

[!code-csharp[OperationContextScope#4](../../../samples/snippets/csharp/VS_Snippets_CFX/operationcontextscope/cs/client.cs#4)]
[!code-vb[OperationContextScope#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/operationcontextscope/vb/client.vb#4)]

## <a name="endpoint-address-in-metadata"></a>Endereço do ponto de extremidade nos metadados

Um endereço de ponto de extremidade é representado no WSDL (Web Services Description Language) como um elemento de `EndpointReference` do WS-Addressing (EPR) dentro do elemento `wsdl:port` do ponto de extremidade correspondente. O EPR contém o endereço do ponto de extremidade, bem como qualquer propriedade de endereço. Observe que o EPR dentro de `wsdl:port` substitui `soap:Address` como visto no exemplo a seguir.

## <a name="defining-endpoint-addresses-in-code"></a>Definindo endereços de ponto de extremidade no código

Um endereço de ponto de extremidade pode ser criado em código com a classe <xref:System.ServiceModel.EndpointAddress>. O URI especificado para o endereço do ponto de extremidade pode ser um caminho totalmente qualificado ou um caminho relativo ao endereço base do serviço. O código a seguir ilustra como criar uma instância da classe <xref:System.ServiceModel.EndpointAddress> e adicioná-la à instância <xref:System.ServiceModel.ServiceHost> que está hospedando o serviço.

O exemplo a seguir demonstra como especificar o endereço do ponto de extremidade completo no código.

[!code-csharp[S_UEHelloWorld#2](../../../samples/snippets/csharp/VS_Snippets_CFX/s_uehelloworld/cs/snippet.cs#2)]

O exemplo a seguir demonstra como adicionar um endereço relativo ("MyService") ao endereço base do host de serviço.

[!code-csharp[S_UEHelloWorld#3](../../../samples/snippets/csharp/VS_Snippets_CFX/s_uehelloworld/cs/snippet.cs#3)]

> [!NOTE]
> As propriedades do <xref:System.ServiceModel.Description.ServiceDescription> no aplicativo de serviço não devem ser modificadas subsequentemente para o método <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> no <xref:System.ServiceModel.ServiceHostBase>. Alguns membros, como a propriedade <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> e os métodos `AddServiceEndpoint` em <xref:System.ServiceModel.ServiceHostBase> e <xref:System.ServiceModel.ServiceHost>, lançam uma exceção se modificadas após esse ponto. Outros permitem que você os modifique, mas o resultado é indefinido.
>
> Da mesma forma, no cliente, os valores de <xref:System.ServiceModel.Description.ServiceEndpoint> não devem ser modificados após a chamada para <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> no <xref:System.ServiceModel.ChannelFactory>. A propriedade <xref:System.ServiceModel.ChannelFactory.Credentials%2A> gera uma exceção se modificada após esse ponto. Os outros valores de descrição do cliente podem ser modificados sem erros, mas o resultado é indefinido.
>
> Seja para o serviço ou cliente, é recomendável que você modifique a descrição antes de chamar <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.

## <a name="using-default-endpoints"></a>Usando pontos de extremidade padrão

Se nenhum ponto de extremidade for especificado no código ou na configuração, o tempo de execução fornecerá os pontos de extremidade padrão adicionando um ponto de extremidades padrão em cada endereço base para cada contrato de serviço implementado pelo serviço. O endereço base pode ser especificado no código ou na configuração, e os pontos de extremidade padrão são adicionados quando <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> é chamado na <xref:System.ServiceModel.ServiceHost>.

Se os pontos de extremidade forem fornecidos explicitamente, os pontos de extremidade padrão ainda poderão ser adicionados chamando <xref:System.ServiceModel.ServiceHostBase.AddDefaultEndpoints%2A> na <xref:System.ServiceModel.ServiceHost> antes de chamar <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>. Para obter mais informações sobre pontos de extremidade, associações e comportamentos padrão, confira [Configuração simplificada](simplified-configuration.md) e [Configuração simplificada para serviços WCF](./samples/simplified-configuration-for-wcf-services.md).

## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.EndpointAddress>
- [Autenticação e identidade de serviço](./feature-details/service-identity-and-authentication.md)
- [Visão geral de criação de ponto de extremidade](endpoint-creation-overview.md)
- [Hospedagem](./feature-details/hosting.md)
