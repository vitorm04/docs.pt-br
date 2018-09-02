---
title: Especificando um endereço de ponto de extremidade
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- endpoints [WCF], addressing
ms.assetid: ac24f5ad-9558-4298-b168-c473c68e819b
ms.openlocfilehash: 718a0c086181546ba7b7fb3b31fce0732dd99382
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43401761"
---
# <a name="specifying-an-endpoint-address"></a>Especificando um endereço de ponto de extremidade
Toda a comunicação com um serviço do Windows Communication Foundation (WCF) ocorre por meio de seus pontos de extremidade. Cada <xref:System.ServiceModel.Description.ServiceEndpoint> contém uma <xref:System.ServiceModel.Description.ServiceEndpoint.Address%2A>, um <xref:System.ServiceModel.Description.ServiceEndpoint.Binding%2A>e um <xref:System.ServiceModel.Description.ServiceEndpoint.Contract%2A>. O contrato especifica quais operações estão disponíveis. A associação especifica como se comunicar com o serviço e o endereço Especifica onde encontrar o serviço. Cada ponto de extremidade deve ter um endereço exclusivo. O endereço do ponto de extremidade é representado pela <xref:System.ServiceModel.EndpointAddress> classe, que contém um identificador de URI (Uniform Resource) que representa o endereço do serviço, um <xref:System.ServiceModel.EndpointAddress.Identity%2A>, que representa a identidade de segurança do serviço e uma coleção de opcional <xref:System.ServiceModel.EndpointAddress.Headers%2A>. Os cabeçalhos opcionais fornecem informações mais detalhadas de endereçamento para identificar ou interagir com o ponto de extremidade. Por exemplo, os cabeçalhos podem indicar qual instância de um serviço para usar para processar uma mensagem de entrada de um determinado usuário, quando várias instâncias estiverem disponíveis, onde o ponto de extremidade deve enviar uma mensagem de resposta ou como processar uma mensagem de entrada.  
  
## <a name="definition-of-an-endpoint-address"></a>Definição de um endereço de ponto de extremidade  
 No WCF, um <xref:System.ServiceModel.EndpointAddress> modela uma referência de ponto de extremidade (EPR) conforme definido no padrão de WS-Addressing.  
  
 O endereço URI para a maioria dos transportes tem quatro partes. Por exemplo, esse URI, `http://www.fabrikam.com:322/mathservice.svc/secureEndpoint` tem as seguintes quatro partes:  
  
-   Esquema: http:  
  
-   Computador: `www.fabrikam.com`  
  
-   (Opcional) Porta: 322  
  
-   Caminho: /mathservice.svc/secureEndpoint  
  
 Parte do modelo EPR é que cada referência de ponto de extremidade pode carregar alguns parâmetros de referência que adicionar informações de identificação extra. No WCF, esses parâmetros de referência são modelados como instâncias do <xref:System.ServiceModel.Channels.AddressHeader> classe.  
  
 O endereço do ponto de extremidade para um serviço pode ser especificado imperativamente por meio de código ou declarativamente por meio da configuração. Definir pontos de extremidade no código geralmente não é prático porque as associações e endereços para um serviço implantado normalmente são diferentes daqueles usados enquanto o serviço está sendo desenvolvido. Em geral, é mais prático definir pontos de extremidade de serviço usando a configuração em vez de código. Informações fora do código de endereçamento e manter a associação permite que eles alterem os sem ter que recompilar e reimplantar o aplicativo. Se nenhum ponto de extremidade forem especificados no código ou na configuração, o tempo de execução adiciona um ponto de extremidade padrão em cada endereço base para cada contrato implementado pelo serviço.  
  
 Há duas maneiras para especificar endereços de ponto de extremidade para um serviço do WCF. Você pode especificar um endereço absoluto para cada ponto de extremidade associado ao serviço ou você pode fornecer um endereço base para o <xref:System.ServiceModel.ServiceHost> de um serviço e, em seguida, especifique um endereço para cada ponto de extremidade associado a esse serviço que é definido em relação a essa base endereço. Você pode usar cada um desses procedimentos para especificar os endereços de ponto de extremidade para um serviço na configuração ou código. Se você não especificar um endereço relativo, o serviço usa o endereço básico. Você também pode ter vários endereços de base para um serviço, mas cada serviço é permitido apenas um endereço base para cada transporte. Se você tiver vários pontos de extremidade, cada um deles é configurada com uma ligação diferente, seus endereços devem ser exclusivos. Pontos de extremidade que usam a mesma associação contratos diferentes, mas pode usar o mesmo endereço.  
  
 Ao hospedar com o IIS, você não gerencia o <xref:System.ServiceModel.ServiceHost> instância por conta própria. O endereço base sempre é o endereço especificado no arquivo. svc para o serviço ao hospedar no IIS. Portanto, você deve usar endereços de ponto de extremidade relativos para pontos de extremidade de serviço hospedados no IIS. Fornecendo um endereço de ponto de extremidade totalmente qualificado pode levar a erros na implantação do serviço. Para obter mais informações, consulte [Implantando um serviço do WCF Internet Information Services-Hosted](../../../docs/framework/wcf/feature-details/deploying-an-internet-information-services-hosted-wcf-service.md).  
  
## <a name="defining-endpoint-addresses-in-configuration"></a>Definir os endereços de ponto de extremidade na configuração  
 Para definir um ponto de extremidade em um arquivo de configuração, use o [ \<ponto de extremidade >](https://msdn.microsoft.com/library/13aa23b7-2f08-4add-8dbf-a99f8127c017) elemento.  
  
 [!code-xml[S_UEHelloWorld#5](../../../samples/snippets/common/VS_Snippets_CFX/s_uehelloworld/common/serviceapp2.config#5)]  
  
 Quando o <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> método é chamado (ou seja, quando o aplicativo host tenta iniciar o serviço), o sistema procura por um [ \<service >](../../../docs/framework/configure-apps/file-schema/wcf/service.md) elemento com um atributo de nome que especifica "UE. Samples.HelloService". Se o [ \<service >](../../../docs/framework/configure-apps/file-schema/wcf/service.md) elemento for encontrado, o sistema carrega a classe especificada e cria pontos de extremidade usando as definições de ponto de extremidade fornecidas no arquivo de configuração. Esse mecanismo permite que você carregar e iniciar um serviço com duas linhas de código enquanto mantém a associação e informações fora do seu código de endereçamento. A vantagem dessa abordagem é que essas alterações podem ser feitas sem ter que recompilar ou reimplantar o aplicativo.  
  
 Os cabeçalhos opcionais são declarados em uma [ \<cabeçalhos >](../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md). A seguir está um exemplo dos elementos usados para especificar pontos de extremidade para um serviço em um arquivo de configuração que faz distinção entre dois cabeçalhos: "Gold" clientes do `http://tempuri1.org/` e os clientes "Padrão" de `http://tempuri2.org/`. O cliente chamar esse serviço deve ter o devido [ \<cabeçalhos >](../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md) em seu arquivo de configuração.  
  
 [!code-xml[S_UEHelloWorld#1](../../../samples/snippets/common/VS_Snippets_CFX/s_uehelloworld/common/serviceapp.config#1)]  
  
 Cabeçalhos também podem ser definidos em mensagens individuais em vez de todas as mensagens em um ponto de extremidade (conforme mostrado anteriormente). Isso é feito usando <xref:System.ServiceModel.OperationContextScope> para criar um novo contexto em um aplicativo cliente para adicionar um cabeçalho personalizado à mensagem de saída, conforme mostrado no exemplo a seguir.  
  
 [!code-csharp[OperationContextScope#4](../../../samples/snippets/csharp/VS_Snippets_CFX/operationcontextscope/cs/client.cs#4)]
 [!code-vb[OperationContextScope#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/operationcontextscope/vb/client.vb#4)]  
  
## <a name="endpoint-address-in-metadata"></a>Endereço do ponto de extremidade nos metadados  
 Um endereço de ponto de extremidade é representado na descrição de linguagem WSDL (Web Services) como WS-Addressing `EndpointReference` elemento (EPR) dentro de um ponto de extremidade correspondente `wsdl:port` elemento. O EPR contém o endereço do ponto de extremidade, bem como quaisquer propriedades de endereço. Observe que o EPR dentro `wsdl:port` substitui `soap:Address` conforme mostrado no exemplo a seguir.  
  
  
  
## <a name="defining-endpoint-addresses-in-code"></a>Definir os endereços de ponto de extremidade no código  
 Um endereço de ponto de extremidade pode ser criado em código com o <xref:System.ServiceModel.EndpointAddress> classe. O URI especificado para o endereço do ponto de extremidade pode ser um caminho totalmente qualificado ou um caminho relativo ao endereço base do serviço. O código a seguir ilustra como criar uma instância da <xref:System.ServiceModel.EndpointAddress> de classe e adicioná-lo para o <xref:System.ServiceModel.ServiceHost> instância que hospeda o serviço.  
  
 O exemplo a seguir demonstra como especificar o endereço do ponto de extremidade completo no código.  
  
 [!code-csharp[S_UEHelloWorld#2](../../../samples/snippets/csharp/VS_Snippets_CFX/s_uehelloworld/cs/snippet.cs#2)]  
  
 O exemplo a seguir demonstra como adicionar um endereço relativo ("MyService") para o endereço básico do host do serviço.  
  
 [!code-csharp[S_UEHelloWorld#3](../../../samples/snippets/csharp/VS_Snippets_CFX/s_uehelloworld/cs/snippet.cs#3)]  
  
> [!NOTE]
>  Propriedades do <xref:System.ServiceModel.Description.ServiceDescription> no serviço de aplicativo não deve ser modificado subsequente para o <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> método em <xref:System.ServiceModel.ServiceHostBase>. Alguns membros, como o <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> propriedade e o `AddServiceEndpoint` métodos <xref:System.ServiceModel.ServiceHostBase> e <xref:System.ServiceModel.ServiceHost>, lançar uma exceção se modificado após esse ponto. Outros permitem que você modificá-los, mas o resultado será indefinido.  
>   
>  Da mesma forma, no cliente a <xref:System.ServiceModel.Description.ServiceEndpoint> valores não devem ser modificados após a chamada para <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> sobre o <xref:System.ServiceModel.ChannelFactory>. O <xref:System.ServiceModel.ChannelFactory.Credentials%2A> propriedade gera uma exceção se modificado após esse ponto. Os outros valores de descrição de cliente podem ser modificados sem erro, mas o resultado será indefinido.  
>   
>  Se para o serviço ou cliente, é recomendável que você modifique a descrição antes de chamar <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.  
  
## <a name="using-default-endpoints"></a>Usando pontos de extremidade padrão  
 Se nenhum ponto de extremidade forem especificados no código ou na configuração, em seguida, o tempo de execução fornece pontos de extremidade padrão com a adição de um ponto de extremidade padrão em cada endereço base para cada contrato de serviço implementado pelo serviço. O endereço base pode ser especificado no código ou na configuração e os pontos de extremidade padrão são adicionados quando <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> é chamado de <xref:System.ServiceModel.ServiceHost>.  
  
 Se os pontos de extremidade forem fornecidos explicitamente, os pontos de extremidade padrão ainda podem ser adicionados chamando <xref:System.ServiceModel.ServiceHostBase.AddDefaultEndpoints%2A> sobre o <xref:System.ServiceModel.ServiceHost> antes de chamar <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>. Para obter mais informações sobre pontos de extremidade, associações e comportamentos padrão, confira [Configuração simplificada](../../../docs/framework/wcf/simplified-configuration.md) e [Configuração simplificada para serviços WCF](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.EndpointAddress>  
 [Autenticação e identidade de serviço](../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [Visão geral de criação de ponto de extremidade](../../../docs/framework/wcf/endpoint-creation-overview.md)  
 [Hospedagem](../../../docs/framework/wcf/feature-details/hosting.md)
