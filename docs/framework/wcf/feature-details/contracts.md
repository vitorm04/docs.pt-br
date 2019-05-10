---
title: Contratos
ms.date: 03/30/2017
helpviewer_keywords:
- WCF [WCF], contracts
- contracts [WCF]
- Windows Communication Foundation [WCF], contracts
ms.assetid: c8364183-4ac1-480b-804a-c5e6c59a5d7d
ms.openlocfilehash: 839f7790a5dd300313931672c60e7826af39aeea
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64651099"
---
# <a name="contracts"></a>Contratos
Esta seção mostra como definir e implementar contratos do Windows Communication Foundation (WCF). Um contrato de serviço Especifica o que um ponto de extremidade comunica ao mundo externo. Em um nível mais concreto, é uma afirmação sobre um conjunto de mensagens específicas, organizados em padrões de troca de mensagens básicas (MEPs), como solicitação/resposta, unidirecional e duplex. Se um contrato de serviço é um conjunto de trocas de mensagens relacionadas logicamente, uma operação de serviço é uma troca de mensagens única. Por exemplo, um `Hello` operação obviamente deve aceitar uma mensagem (de modo que o chamador pode anunciar a saudação) e podem ou não pode retornar uma mensagem (dependendo de cortesia da operação).  
  
 Para obter mais informações sobre contratos e outros conceitos de WCF, consulte [conceitos fundamentais do Windows Communication Foundation](../../../../docs/framework/wcf/fundamental-concepts.md). Este tópico enfoca a compreensão de contratos de serviço. Para obter mais informações sobre como criar os clientes que usam os contratos de serviço para se conectar aos serviços, consulte [visão geral do cliente WCF](../../../../docs/framework/wcf/wcf-client-overview.md). Para obter mais informações sobre os canais de cliente, a arquitetura do cliente e outros problemas de cliente, consulte [clientes](../../../../docs/framework/wcf/feature-details/clients.md).  
  
## <a name="overview"></a>Visão geral  
 Este tópico fornece uma orientação conceitual de alto nível para projetar e implementar serviços WCF. Subtópicos fornecem que informações mais detalhadas sobre as especificações de design e implementação. Antes de criar e implementar seu aplicativo do WCF, é recomendável que você:  
  
- Entender é que um contrato de serviço, como ele funciona e como criá-lo.  
  
- Entender o que os contratos de estado requisitos mínimos não pode dar suporte a essa configuração de tempo de execução ou o ambiente de hospedagem.  
  
## <a name="service-contracts"></a>Contratos de serviço  
 Um contrato de serviço é uma instrução que fornece informações sobre:  
  
- O agrupamento de operações em um serviço.  
  
- A assinatura das operações em termos de mensagens trocadas.  
  
- Os tipos de dados dessas mensagens.  
  
- O local das operações.  
  
- Os protocolos específicos e formatos de serialização que são usados para dar suporte à comunicação bem-sucedida com o serviço.  
  
 Por exemplo, um contrato de ordem de compra pode ter um `CreateOrder` tipos de operação que aceita uma entrada de informações do pedido e retorna informações de êxito ou falha, incluindo um identificador do pedido. Ele também pode ter um `GetOrderStatus` operação que aceita um identificador do pedido e retorna informações de status do pedido. Um contrato de serviço desse tipo deve especificar:  
  
- Se o contrato de ordem de compra consistiu `CreateOrder` e `GetOrderStatus` operações.  
  
- Que especificou as operações de mensagens de entrada e as mensagens de saída.  
  
- Os dados que podem ser executadas por essas mensagens.  
  
- Categóricas instruções sobre a infraestrutura de comunicação necessária para processar com êxito as mensagens. Por exemplo, esses detalhes incluem se e que formas de segurança são necessárias para estabelecer a comunicação bem-sucedida.  
  
 Para transmitir esse tipo de informação para aplicativos em outras plataformas (incluindo plataformas de não-Microsoft), os contratos de serviço XML são publicamente expressas em formatos XML padrão, como [descrição linguagem WSDL (Web Services)](https://go.microsoft.com/fwlink/?LinkId=87004) e [esquema XML (XSD)](https://go.microsoft.com/fwlink/?LinkId=87005), entre outros. Os desenvolvedores para várias plataformas podem usar essas informações de contrato público para criar aplicativos que podem se comunicar com o serviço, pois eles entendem o idioma da especificação e como essas linguagens são projetadas para habilitar a interoperação descrevendo o públicos formulários, formatos e protocolos que o serviço oferece suporte. Para obter mais informações sobre como o WCF trata esse tipo de informação, consulte [metadados](../../../../docs/framework/wcf/feature-details/metadata.md).  
  
 Contratos podem ser expressos muitas maneiras, no entanto, e embora WSDL e XSD são excelentes linguagens para descrever serviços de forma acessível, elas são difíceis de idiomas a serem usados diretamente — em qualquer caso, eles são meramente descrições de um contrato de serviço, o service não implementações. Portanto, os aplicativos do WCF usarem atributos gerenciados, interfaces e classes para definir a estrutura de e para implementar um serviço.  
  
 O contrato resultante definido em tipos gerenciados pode ser convertido (também chamado de *exportados*) como metadados — WSDL e XSD — quando necessário, os clientes ou outros implementadores de serviço, especialmente em outras plataformas. O resultado é um modelo de programação simples que pode ser descrito usando metadados públicos para qualquer aplicativo cliente. Os detalhes das mensagens SOAP subjacentes, como o transporte e informações relacionadas à segurança, podem ser mantidos no WCF, que executa automaticamente as conversões necessárias para e do sistema de tipo de contrato de serviço para o sistema de tipo XML.  
  
 Para obter mais informações sobre a criação de contratos, consulte [Criando contratos de serviço](../../../../docs/framework/wcf/designing-service-contracts.md). Para obter mais informações sobre como implementar contratos, consulte [implementar contratos de serviço](../../../../docs/framework/wcf/implementing-service-contracts.md).  
  
 Além disso, o WCF também fornece a capacidade de desenvolver os contratos de serviço inteiramente no nível da mensagem. Para obter mais informações sobre o desenvolvimento de contratos de serviço no nível da mensagem, consulte [contratos de mensagem usando](../../../../docs/framework/wcf/feature-details/using-message-contracts.md). Para obter mais informações sobre o desenvolvimento de serviços em XML não SOAP, consulte [interoperabilidade com aplicativos de POX](../../../../docs/framework/wcf/feature-details/interoperability-with-pox-applications.md).  
  
### <a name="understanding-the-hierarchy-of-requirements"></a>Noções básicas sobre a hierarquia de requisitos  
 Um contrato de serviço agrupa as operações; Especifica MEP, tipos de mensagem, e a realização dessas mensagens; tipos de dados e indica as categorias de comportamento de tempo de execução, uma implementação deve ter para o contrato de suporte (por exemplo, ele pode exigir que as mensagens de ser criptografadas e assinadas). No entanto, o contrato de serviço em si, não especifica exatamente como esses requisitos forem atendidos, é só isso, eles devem ser. O tipo de criptografia ou como uma mensagem for assinada é até a implementação e configuração de um serviço em conformidade.  
  
 Observe a maneira que o contrato requer certas coisas da implementação do contrato de serviço e a configuração de tempo de execução para Adicionar comportamento. O conjunto de requisitos que devem ser atendidos para expor um serviço para uso se baseia o conjunto anterior de requisitos. Se um contrato de tornar os requisitos da implementação, uma implementação pode exigir ainda mais da configuração e as associações que permitem que o serviço seja executado. Por fim, o aplicativo host deve também dão suporte a todos os requisitos que adicionar a configuração de serviço e associações.  
  
 Esse processo aditivas requisito é importante ter em mente ao projetar, implementar, configurando e hospedando seu aplicativo de serviço do Windows Communication Foundation (WCF). Por exemplo, o contrato pode especificar que ele precisa dar suporte a uma sessão. Nesse caso, em seguida, você deve configurar a associação para dar suporte a esse requisito contratual ou a implementação do serviço não funcionará. Ou, se seu serviço requer autenticação do Windows integrada e está hospedado no Internet Information Services (IIS), o aplicativo Web no qual reside o serviço deve ter autenticação Windows integrada ativada e suporte anônimo desativado. Para obter mais informações sobre os recursos e o impacto dos tipos de aplicativos de host de serviço diferentes, consulte [hospedagem](../../../../docs/framework/wcf/feature-details/hosting.md).  
  
## <a name="see-also"></a>Consulte também

- [Pontos de extremidade: Endereços, associações e contratos](../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
- [Criando contratos de serviço](../../../../docs/framework/wcf/designing-service-contracts.md)
- [Implementando contratos de serviço](../../../../docs/framework/wcf/implementing-service-contracts.md)
