---
title: "Serviços de implantação e projeção"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- defining service contracts [WCF]
ms.assetid: 036fae20-7c55-4002-b71d-ac4466e167a3
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b6d5a2dfb4db1d57f60e4c7f8cf3300b766402e1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="designing-and-implementing-services"></a>Serviços de implantação e projeção
Esta seção mostra como definir e implementar [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] contratos. Um contrato de serviço Especifica o que um ponto de extremidade se comunica com o mundo exterior. Em um nível mais concreto, é uma afirmação sobre um conjunto de mensagens específicas organizados em padrões de troca de mensagem básica (MEPs), como solicitação/resposta, unidirecional e duplex. Se um contrato de serviço é um conjunto logicamente relacionado de troca de mensagens, uma operação de serviço é uma troca de mensagens único. Por exemplo, um `Hello` operação obviamente deve aceitar uma mensagem (de modo que o chamador pode anunciar a saudação) e pode ou não pode retornar uma mensagem (dependendo de cortesia da operação).  
  
 Para obter mais informações sobre contratos e outros principais [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] conceitos, consulte [fundamentais conceitos do Windows Communication Foundation](../../../docs/framework/wcf/fundamental-concepts.md). Este tópico se concentra em entender os contratos de serviço. Para obter mais informações sobre como criar os clientes que usam os contratos de serviço para se conectar a serviços, consulte [visão geral do cliente WCF](../../../docs/framework/wcf/wcf-client-overview.md).  
  
## <a name="overview"></a>Visão geral  
 Este tópico fornece uma orientação conceitual de alto nível para projetar e implementar [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] serviços. Subtópicos fornecem informações mais detalhadas sobre as especificações de design e implementação. Antes de projetar e implementar sua [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] aplicativo, é recomendável que você:  
  
-   Entender é que um contrato de serviço, como ele funciona e como criar um.  
  
-   Entender a contratos estado requisitos mínimos não pode dar suporte a essa configuração de tempo de execução ou o ambiente de hospedagem.  
  
## <a name="service-contracts"></a>Contratos de serviço  
 Um contrato de serviço Especifica o seguinte:  
  
-   Expõe as operações de um contrato.  
  
-   A assinatura de operações em termos de mensagens trocadas.  
  
-   Os tipos de dados dessas mensagens.  
  
-   O local das operações.  
  
-   Os protocolos específicos e formatos de serialização que são usados para dar suporte à comunicação com êxito com o serviço.  
  
 Por exemplo, um contrato de ordem de compra pode ter um `CreateOrder` tipos de operação que aceita uma entrada de informações de ordem e retorna informações de êxito ou falha, incluindo um identificador de ordem. Ele também pode ter um `GetOrderStatus` operação que aceita um identificador de ordem e retorna informações de status de ordem. Um contrato de serviço desse tipo deve especificar:  
  
1.  Se o contrato de ordem de compra consistiu em `CreateOrder` e `GetOrderStatus` operações.  
  
2.  Se as operações especificadas mensagens de entrada e mensagens de saída.  
  
3.  Os dados que podem realizar essas mensagens.  
  
4.  Categóricas instruções sobre a infra-estrutura de comunicação necessária para processar as mensagens. Por exemplo, esses detalhes incluem se e que formas de segurança são necessárias para estabelecer comunicação com êxito.  
  
 Para transmitir esse tipo de informação para outros aplicativos em várias plataformas (incluindo plataformas de não-Microsoft), XML contratos de serviço são publicamente expressas em formatos padrão de XML, como [Web Services Description Language](http://go.microsoft.com/fwlink/?LinkId=94952) ( WSDL) e [esquema XML](http://go.microsoft.com/fwlink/?LinkId=94953) (XSD), entre outros. Os desenvolvedores para plataformas podem usar essas informações de contrato público para criar aplicativos que podem se comunicar com o serviço, pois eles entendem o idioma da especificação e como essas linguagens são projetadas para habilitar a interoperação descrevendo os formulários públicos, formatos e protocolos com suporte do serviço. Para obter mais informações sobre como [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] identificadores nesse tipo de informações, consulte [metadados](../../../docs/framework/wcf/feature-details/metadata.md).  
  
 Contratos podem ser expressas de muitas maneiras, e enquanto WSDL e XSD são idiomas excelentes para descrever serviços de forma acessível, são idiomas difícil usar diretamente e apenas as descrições de um serviço, não implementações de contrato de serviço. Portanto, [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] aplicativos usam atributos gerenciados, interfaces e classes para definir a estrutura de um serviço e implementá-lo.  
  
 O contrato resultante definido em tipos gerenciados pode ser *exportado* como metadados — WSDL e XSD, quando necessário, os clientes ou outros implementadores de serviço. O resultado é um modelo de programação simples que pode ser descrito (usando metadados público) para qualquer aplicativo cliente. Os detalhes de como as mensagens SOAP subjacentes, o transporte e informações relacionadas à segurança e assim por diante, podem ser deixados para [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], que realiza as conversões necessárias para e do tipo de contrato de serviço sistema ao XML digite sistema automaticamente.  
  
 Para obter mais informações sobre como criar contratos, consulte [criar contratos de serviço](../../../docs/framework/wcf/designing-service-contracts.md). Para obter mais informações sobre a implementação de contratos, consulte [implementando contratos de serviço](../../../docs/framework/wcf/implementing-service-contracts.md).  
  
### <a name="messages-up-front-and-center"></a>Mensagens de frente e no Centro  
 Usando interfaces gerenciadas, classes e métodos para operações de serviço do modelo é simples quando você está acostumado a chamada de procedimento remoto (RPC)-estilo de assinaturas de método, passar parâmetros para um método e receber valores de retorno é o formulário normal de solicitando a funcionalidade de um objeto ou outro tipo de código. Por exemplo, os programadores que usam linguagens gerenciadas, como [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] e COM C++ pode aplicar seus conhecimentos sobre a abordagem de estilo RPC (se estiver usando objetos ou interfaces) para a criação de [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] contratos de serviço sem se deparar com problemas sistemas de objeto distribuídos inerentes no estilo RPC. Orientação de serviço fornece os benefícios de programação acoplada, orientado a mensagens enquanto retém a facilidade e a familiaridade RPC experiência em programação.  
  
 Os programadores muitas são mais confortáveis com aplicativo orientado a mensagens interfaces de programação, como filas de mensagens, como o Microsoft MSMQ a <xref:System.Messaging> namespaces no .NET Framework ou envio XML não estruturado em solicitações HTTP, para citar alguns. Para obter mais informações sobre programação no nível da mensagem, consulte [usando contratos de mensagem](../../../docs/framework/wcf/feature-details/using-message-contracts.md), [programação de nível de serviço de canal](../../../docs/framework/wcf/extending/service-channel-level-programming.md), e [interoperabilidade com aplicativos de POX](../../../docs/framework/wcf/feature-details/interoperability-with-pox-applications.md).  
  
### <a name="understanding-the-hierarchy-of-requirements"></a>Noções básicas sobre a hierarquia de requisitos  
 Um contrato de serviço agrupa as operações; Especifica o padrão de troca de mensagens, os tipos de mensagem e os dados tipos transportam essas mensagens; e indica as categorias de comportamento de tempo de execução deve ter uma implementação para o contrato de suporte (por exemplo, ele pode exigir que as mensagens de ser criptografadas e assinadas). O contrato de serviço não especifica exatamente como esses requisitos forem atendidos, só que eles devem ser. É o tipo de criptografia ou a maneira na qual uma mensagem é assinada até a implementação e configuração de um serviço compatível.  
  
 Observe a maneira que o contrato requer alguns detalhes de implementação do contrato de serviço e a configuração de tempo de execução para Adicionar comportamento. Cria o conjunto de requisitos que devem ser atendidos para expor um serviço para uso no conjunto de requisitos anterior. Se um contrato de requisitos da implementação de uma implementação pode exigir ainda mais a configuração e as associações que permitem que o serviço seja executado. Por fim, o aplicativo host também deve dar suporte a qualquer requisito que adiciona a configuração de serviço e associações.  
  
 Esse processo aditivas requisito é importante ter em mente ao projetar, implementação, configuração e hospedagem um [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] aplicativo de serviço. Por exemplo, o contrato pode especificar que ele precisa dar suporte a uma sessão. Nesse caso, você deve configurar a associação para dar suporte a esse requisito contratual ou a implementação de serviço não funcionará. Ou, se seu serviço requer a autenticação integrada do Windows e está hospedado no Internet Information Services (IIS), o aplicativo Web no qual reside o serviço deve ter autenticação integrada do Windows ativado e suporte anônimo desativado. Para obter mais informações sobre os recursos e o impacto dos tipos de aplicativo de host de serviço diferentes, consulte [serviços de hospedagem](../../../docs/framework/wcf/hosting-services.md).  
  
## <a name="see-also"></a>Consulte também  
 [Criando contratos de serviço](../../../docs/framework/wcf/designing-service-contracts.md)  
 [Implementando contratos de serviço](../../../docs/framework/wcf/implementing-service-contracts.md)
