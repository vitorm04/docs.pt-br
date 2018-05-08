---
title: Contratos
ms.date: 03/30/2017
helpviewer_keywords:
- WCF [WCF], contracts
- contracts [WCF]
- Windows Communication Foundation [WCF], contracts
ms.assetid: c8364183-4ac1-480b-804a-c5e6c59a5d7d
ms.openlocfilehash: 8522ae89ca69ec594f62e272f8479b607609f064
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="contracts"></a>Contratos
Esta seção mostra como definir e implementar contratos do Windows Communication Foundation (WCF). Um contrato de serviço Especifica o que um ponto de extremidade se comunica com o mundo exterior. Em um nível mais concreto, é uma afirmação sobre um conjunto de mensagens específicas organizados em padrões de troca de mensagem básica (MEPs), como solicitação/resposta, unidirecional e duplex. Se um contrato de serviço é um conjunto logicamente relacionado de troca de mensagens, uma operação de serviço é uma troca de mensagens único. Por exemplo, um `Hello` operação obviamente deve aceitar uma mensagem (de modo que o chamador pode anunciar a saudação) e pode ou não pode retornar uma mensagem (dependendo de cortesia da operação).  
  
 Para obter mais informações sobre contratos e outros conceitos fundamentais do WCF, consulte [fundamentais conceitos do Windows Communication Foundation](../../../../docs/framework/wcf/fundamental-concepts.md). Este tópico se concentra em entender os contratos de serviço. Para obter mais informações sobre como criar os clientes que usam os contratos de serviço para se conectar a serviços, consulte [visão geral do cliente WCF](../../../../docs/framework/wcf/wcf-client-overview.md). Para obter mais informações sobre os canais de cliente, a arquitetura do cliente e outros problemas de cliente, consulte [clientes](../../../../docs/framework/wcf/feature-details/clients.md).  
  
## <a name="overview"></a>Visão geral  
 Este tópico fornece uma orientação conceitual de alto nível para projetar e implementar serviços WCF. Subtópicos fornecem que informações mais detalhadas sobre as especificações de design e implementação. Antes de projetar e implementar um aplicativo WCF, é recomendável que você:  
  
-   Entender é que um contrato de serviço, como ele funciona e como criar um.  
  
-   Entender a contratos estado requisitos mínimos não pode dar suporte a essa configuração de tempo de execução ou o ambiente de hospedagem.  
  
## <a name="service-contracts"></a>Contratos de serviço  
 Um contrato de serviço é uma instrução que fornece informações sobre:  
  
-   O agrupamento de operações em um serviço.  
  
-   A assinatura de operações em termos de mensagens trocadas.  
  
-   Os tipos de dados dessas mensagens.  
  
-   O local das operações.  
  
-   Os protocolos específicos e formatos de serialização que são usados para dar suporte à comunicação com êxito com o serviço.  
  
 Por exemplo, um contrato de ordem de compra pode ter um `CreateOrder` tipos de operação que aceita uma entrada de informações de ordem e retorna informações de êxito ou falha, incluindo um identificador de ordem. Ele também pode ter um `GetOrderStatus` operação que aceita um identificador de ordem e retorna informações de status de ordem. Um contrato de serviço desse tipo deve especificar:  
  
-   Se o contrato de ordem de compra consistiu em `CreateOrder` e `GetOrderStatus` operações.  
  
-   Se as operações especificadas mensagens de entrada e mensagens de saída.  
  
-   Os dados que podem realizar essas mensagens.  
  
-   Categóricas instruções sobre a infra-estrutura de comunicação necessária para processar as mensagens. Por exemplo, esses detalhes incluem se e que formas de segurança são necessárias para estabelecer comunicação com êxito.  
  
 Para transmitir esse tipo de informações para aplicativos em outras plataformas (incluindo plataformas de não-Microsoft), XML contratos de serviço são publicamente expressas em formatos padrão de XML, como [WSDL Web Services Description Language ()](http://go.microsoft.com/fwlink/?LinkId=87004) e [esquema XML (XSD)](http://go.microsoft.com/fwlink/?LinkId=87005), entre outros. Os desenvolvedores para plataformas podem usar essas informações de contrato público para criar aplicativos que podem se comunicar com o serviço, pois eles entendem o idioma da especificação e como essas linguagens são projetadas para habilitar a interoperação descrevendo os formulários públicos, formatos e protocolos com suporte do serviço. Para obter mais informações sobre como o WCF trata esse tipo de informações, consulte [metadados](../../../../docs/framework/wcf/feature-details/metadata.md).  
  
 Contratos podem ser expressos muitas maneiras, no entanto, e enquanto WSDL e XSD são idiomas excelentes para descrever serviços de forma acessível, são difíceis idiomas a serem usados diretamente, em qualquer caso, eles são simplesmente descrições de um contrato de serviço, não de serviço implementações. Portanto, aplicativos WCF usam atributos gerenciados, interfaces e classes para definir a estrutura de e para implementar um serviço.  
  
 O contrato resultante definido em tipos gerenciados pode ser convertido (também chamado de *exportado*) como metadados — WSDL e XSD — quando necessário, os clientes ou outros implementadores de serviço, especialmente em outras plataformas. O resultado é um modelo de programação simples que pode ser descrito usando metadados públicos para qualquer aplicativo cliente. Os detalhes das mensagens de SOAP subjacentes, como o transporte e informações relacionadas à segurança, podem ser deixados com WCF, que executa automaticamente as conversões necessárias para e do sistema de tipo de contrato de serviço para o sistema de tipo XML.  
  
 Para obter mais informações sobre como criar contratos, consulte [criar contratos de serviço](../../../../docs/framework/wcf/designing-service-contracts.md). Para obter mais informações sobre a implementação de contratos, consulte [implementando contratos de serviço](../../../../docs/framework/wcf/implementing-service-contracts.md).  
  
 Além disso, o WCF também fornece a capacidade de desenvolver contratos de serviço inteiramente no nível da mensagem. Para obter mais informações sobre o desenvolvimento de contratos de serviço no nível da mensagem, consulte [usando contratos de mensagem](../../../../docs/framework/wcf/feature-details/using-message-contracts.md). Para obter mais informações sobre como desenvolver serviços em XML não SOAP, consulte [interoperabilidade com aplicativos de POX](../../../../docs/framework/wcf/feature-details/interoperability-with-pox-applications.md).  
  
### <a name="understanding-the-hierarchy-of-requirements"></a>Noções básicas sobre a hierarquia de requisitos  
 Um contrato de serviço agrupa as operações; Especifica MEPS, tipos de mensagem e carregam as mensagens; tipos de dados e indica as categorias de comportamento de tempo de execução deve ter uma implementação para o contrato de suporte (por exemplo, ele pode exigir que as mensagens de ser criptografadas e assinadas). O contrato de serviço, no entanto, não especifique exatamente como esses requisitos forem atendidos, só que eles devem ser. É o tipo de criptografia ou como uma mensagem é assinada até a implementação e configuração de um serviço compatível.  
  
 Observe a maneira que o contrato requer alguns detalhes de implementação do contrato de serviço e a configuração de tempo de execução para Adicionar comportamento. Cria o conjunto de requisitos que devem ser atendidos para expor um serviço para uso no conjunto de requisitos anterior. Se um contrato de requisitos da implementação de uma implementação pode exigir ainda mais a configuração e as associações que permitem que o serviço seja executado. Por fim, o aplicativo host também deve dar suporte a qualquer requisito que adiciona a configuração de serviço e associações.  
  
 Esse processo aditivas requisito é importante ter em mente durante a criação, implementação, configuração e hospedando o seu aplicativo de serviço do Windows Communication Foundation (WCF). Por exemplo, o contrato pode especificar que ele precisa dar suporte a uma sessão. Nesse caso, você deve configurar a associação para dar suporte a esse requisito contratual ou a implementação de serviço não funcionará. Ou, se seu serviço requer a autenticação integrada do Windows e está hospedado no Internet Information Services (IIS), o aplicativo Web no qual reside o serviço deve ter autenticação integrada do Windows ativado e suporte anônimo desativado. Para obter mais informações sobre os recursos e o impacto dos tipos de aplicativo de host de serviço diferentes, consulte [hospedagem](../../../../docs/framework/wcf/feature-details/hosting.md).  
  
## <a name="see-also"></a>Consulte também  
 [Pontos de extremidade: endereços, associações e contratos](../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)  
 [Criando contratos de serviço](../../../../docs/framework/wcf/designing-service-contracts.md)  
 [Implementando contratos de serviço](../../../../docs/framework/wcf/implementing-service-contracts.md)
