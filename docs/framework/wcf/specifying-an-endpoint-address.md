---
title: "Especificando um endereço de ponto de extremidade"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- endpoints [WCF], addressing
ms.assetid: ac24f5ad-9558-4298-b168-c473c68e819b
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 403ff897de4dc9ee95a854d9658bdee344755d59
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="specifying-an-endpoint-address"></a>Especificando um endereço de ponto de extremidade
Toda a comunicação com um [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] serviço ocorre por meio de seus pontos de extremidade. Cada <xref:System.ServiceModel.Description.ServiceEndpoint> contém um <xref:System.ServiceModel.Description.ServiceEndpoint.Address%2A>, um <xref:System.ServiceModel.Description.ServiceEndpoint.Binding%2A>e um <xref:System.ServiceModel.Description.ServiceEndpoint.Contract%2A>. O contrato especifica quais operações estão disponíveis. Especifica a associação para se comunicar com o serviço e o endereço Especifica onde encontrar o serviço. Cada ponto de extremidade deve ter um endereço exclusivo. O endereço do ponto de extremidade é representado pelo <xref:System.ServiceModel.EndpointAddress> classe, que contém um identificador de recursos uniforme (URI) que representa o endereço do serviço, um <xref:System.ServiceModel.EndpointAddress.Identity%2A>, que representa a identidade de segurança do serviço e uma coleção de opcional <xref:System.ServiceModel.EndpointAddress.Headers%2A>. Os cabeçalhos opcionais fornecem informações mais detalhadas de endereçamento para identificar ou interagir com o ponto de extremidade. Por exemplo, os cabeçalhos podem indicar como processar uma mensagem de entrada, onde o ponto de extremidade deve enviar uma mensagem de resposta ou qual instância de um serviço para usar para processar uma mensagem de entrada de um determinado usuário quando houver várias instâncias.  
  
## <a name="definition-of-an-endpoint-address"></a>Definição de um endereço de ponto de extremidade  
 Em [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], um <xref:System.ServiceModel.EndpointAddress> modelos de uma referência de ponto de extremidade (EPR) conforme definido no padrão de WS-Addressing.  
  
 O endereço de URI para a maioria dos transportes tem quatro partes. Por exemplo, esse URI, "http://www.fabrikam.com:322/mathservice.svc/secureEndpoint" tem as seguintes quatro partes:  
  
-   Esquema: http:  
  
-   Machine: www.fabrikam.com  
  
-   (Opcional) Porta: 322  
  
-   Path: /mathservice.svc/secureEndpoint  
  
 Parte do modelo EPR é que cada referência de ponto de extremidade pode executar alguns parâmetros de referência que adicionar informações de identificação extra. Em [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], esses parâmetros de referência são modelados como instâncias de <xref:System.ServiceModel.Channels.AddressHeader> classe.  
  
 O endereço de ponto de extremidade para um serviço pode ser especificado imperativa por meio de código ou declarativamente por meio da configuração. Definir pontos de extremidade no código geralmente não é prático porque as associações e os endereços para um serviço implantado normalmente são diferentes daqueles usados enquanto o serviço está sendo desenvolvido. Geralmente, é mais prático definir pontos de extremidade de serviço usando a configuração em vez do código. Informações sem o código de endereçamento e manter a associação permite que a alteração sem ter que recompilar e reimplantar o aplicativo. Se nenhum ponto de extremidade está especificados no código ou na configuração, o tempo de execução adiciona um ponto de extremidade padrão em cada endereço base para cada contrato implementado pelo serviço.  
  
 Há duas maneiras de especificar endereços de ponto de extremidade para um serviço em [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]. Você pode especificar um endereço absoluto para cada ponto de extremidade associado ao serviço ou você pode fornecer um endereço base para o <xref:System.ServiceModel.ServiceHost> de um serviço e, em seguida, especifique um endereço para cada ponto de extremidade associado a esse serviço que é definido em relação a essa base endereço. Você pode usar cada um dos procedimentos a seguir para especificar os endereços de ponto de extremidade para um serviço na configuração ou código. Se você não especificar um endereço relativo, o serviço usa o endereço base. Você também pode ter vários endereços de base para um serviço, mas cada serviço é permitido somente um endereço base para cada transporte. Se você tiver vários pontos de extremidade, cada um deles é configurada com uma associação diferente, seus endereços devem ser exclusivos. Pontos de extremidade que usam a mesma associação contratos mas diferentes pode usar o mesmo endereço.  
  
 Ao hospedar no IIS, você não gerencia o <xref:System.ServiceModel.ServiceHost> instância por conta própria. O endereço base sempre é o endereço especificado no arquivo. svc para o serviço ao hospedar no IIS. Portanto, você deve usar endereços de ponto de extremidade relativa para pontos de extremidade do serviço hospedado no IIS. Fornecendo um endereço de ponto de extremidade totalmente qualificado pode resultar em erros na implantação do serviço. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Implantando um serviço WCF hospedados em serviços de informações da Internet](../../../docs/framework/wcf/feature-details/deploying-an-internet-information-services-hosted-wcf-service.md).  
  
## <a name="defining-endpoint-addresses-in-configuration"></a>Definir os endereços de ponto de extremidade na configuração  
 Para definir um ponto de extremidade em um arquivo de configuração, use o [ \<ponto de extremidade >](http://msdn.microsoft.com/library/13aa23b7-2f08-4add-8dbf-a99f8127c017) elemento.  
  
 [!code-xml[S_UEHelloWorld#5](../../../samples/snippets/common/VS_Snippets_CFX/s_uehelloworld/common/serviceapp2.config#5)]  
  
 Quando o <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> método é chamado (ou seja, quando o aplicativo host tenta iniciar o serviço), o sistema procurará um [ \<service >](../../../docs/framework/configure-apps/file-schema/wcf/service.md) elemento com um atributo name que especifica "UE. Samples.HelloService". Se o [ \<service >](../../../docs/framework/configure-apps/file-schema/wcf/service.md) elemento for encontrado, o sistema carrega a classe especificada e cria pontos de extremidade usando as definições de ponto de extremidade fornecidas no arquivo de configuração. Esse mecanismo permite que você carregar e iniciar um serviço com duas linhas de código ao mesmo tempo mantendo informações fora do seu código de endereçamento e associação. A vantagem dessa abordagem é que essas alterações podem ser feitas sem precisar recompilar ou reimplantar o aplicativo.  
  
 Os cabeçalhos opcionais são declarados em um [ \<cabeçalhos >](../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md). A seguir está um exemplo de como os elementos usados para especificar pontos de extremidade para um serviço em um arquivo de configuração que faz distinção entre dois cabeçalhos: clientes "Ouro" clientes "Padrão" de http://tempuri2.org/ e http://tempuri1.org/. O cliente chama esse serviço deve ter apropriada [ \<cabeçalhos >](../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md) em seu arquivo de configuração.  
  
 [!code-xml[S_UEHelloWorld#1](../../../samples/snippets/common/VS_Snippets_CFX/s_uehelloworld/common/serviceapp.config#1)]  
  
 Cabeçalhos também podem ser definidos em mensagens individuais em vez de todas as mensagens em um ponto de extremidade (conforme mostrado anteriormente). Isso é feito usando <xref:System.ServiceModel.OperationContextScope> para criar um novo contexto em um aplicativo cliente para adicionar um cabeçalho personalizado à mensagem de saída, conforme mostrado no exemplo a seguir.  
  
 [!code-csharp[OperationContextScope#4](../../../samples/snippets/csharp/VS_Snippets_CFX/operationcontextscope/cs/client.cs#4)]
 [!code-vb[OperationContextScope#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/operationcontextscope/vb/client.vb#4)]  
  
## <a name="endpoint-address-in-metadata"></a>Endereço de ponto de extremidade de metadados  
 Um endereço de ponto de extremidade é representado no WSDL Web Services Description Language () como WS-Addressing `EndpointReference` elemento (EPR) dentro do ponto de extremidade correspondente `wsdl:port` elemento. O EPR contém o endereço do ponto de extremidade, bem como as propriedades do endereço. Observe que o EPR dentro `wsdl:port` substitui `soap:Address` como visto no exemplo a seguir.  
  
  
  
## <a name="defining-endpoint-addresses-in-code"></a>Definir os endereços de ponto de extremidade no código  
 Um endereço de ponto de extremidade pode ser criado em código com o <xref:System.ServiceModel.EndpointAddress> classe. O URI especificado para o endereço do ponto de extremidade pode ser um caminho totalmente qualificado ou um caminho relativo ao endereço base do serviço. O código a seguir ilustra como criar uma instância do <xref:System.ServiceModel.EndpointAddress> classe e adicione-o para a <xref:System.ServiceModel.ServiceHost> instância que hospeda o serviço.  
  
 O exemplo a seguir demonstra como especificar o endereço do ponto de extremidade completa no código.  
  
 [!code-csharp[S_UEHelloWorld#2](../../../samples/snippets/csharp/VS_Snippets_CFX/s_uehelloworld/cs/snippet.cs#2)]  
  
 O exemplo a seguir demonstra como adicionar um endereço relativo ("MyService") para o endereço base do host do serviço.  
  
 [!code-csharp[S_UEHelloWorld#3](../../../samples/snippets/csharp/VS_Snippets_CFX/s_uehelloworld/cs/snippet.cs#3)]  
  
> [!NOTE]
>  Propriedades do <xref:System.ServiceModel.Description.ServiceDescription> no serviço de aplicativo não deve ser modificado após o <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> método <xref:System.ServiceModel.ServiceHostBase>. Alguns membros, como o <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> propriedade e o `AddServiceEndpoint` métodos em <xref:System.ServiceModel.ServiceHostBase> e <xref:System.ServiceModel.ServiceHost>, lançar uma exceção se modificado depois desse ponto. Outros permitem que você modificá-las, mas o resultado é indefinido.  
>   
>  Da mesma forma, no cliente de <xref:System.ServiceModel.Description.ServiceEndpoint> valores não devem ser modificados após a chamada a <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> no <xref:System.ServiceModel.ChannelFactory>. O <xref:System.ServiceModel.ChannelFactory.Credentials%2A> propriedade gera uma exceção se modificado depois desse ponto. Os outros valores de descrição do cliente podem ser modificados sem erro, mas o resultado é indefinido.  
>   
>  Se para o serviço ou cliente, é recomendável que você modifique a descrição antes de chamar <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.  
  
## <a name="using-default-endpoints"></a>Usando pontos de extremidade padrão  
 Se nenhum ponto de extremidade está especificados no código ou na configuração de tempo de execução fornece pontos de extremidade padrão com a adição de um ponto de extremidade padrão em cada endereço base para cada contrato de serviço implementado pelo serviço. O endereço base pode ser especificado no código ou na configuração e os pontos de extremidade padrão são adicionados quando <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> é chamado de <xref:System.ServiceModel.ServiceHost>.  
  
 Se os pontos de extremidade são explicitamente fornecidos, os pontos de extremidade padrão ainda podem ser adicionados ao chamar <xref:System.ServiceModel.ServiceHostBase.AddDefaultEndpoints%2A> no <xref:System.ServiceModel.ServiceHost> antes de chamar <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>. [!INCLUDE[crabout](../../../includes/crabout-md.md)]pontos de extremidade padrão, associações e comportamentos, consulte [configuração simplificada](../../../docs/framework/wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.EndpointAddress>  
 [Autenticação e identidade de serviço](../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [Visão geral de criação de ponto de extremidade](../../../docs/framework/wcf/endpoint-creation-overview.md)  
 [Hospedagem](../../../docs/framework/wcf/feature-details/hosting.md)
