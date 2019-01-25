---
title: Serviços de implantação e projeção
ms.date: 03/30/2017
helpviewer_keywords:
- defining service contracts [WCF]
ms.assetid: 036fae20-7c55-4002-b71d-ac4466e167a3
ms.openlocfilehash: 51cdcc4789ac553c2775c89d6124cf90624b8747
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54716046"
---
# <a name="designing-and-implementing-services"></a>Serviços de implantação e projeção
Esta seção mostra como definir e implementar contratos do WCF. Um contrato de serviço Especifica o que um ponto de extremidade comunica ao mundo externo. Em um nível mais concreto, é uma afirmação sobre um conjunto de mensagens específicas, organizados em padrões de troca de mensagens básicas (MEPs), como solicitação/resposta, unidirecional e duplex. Se um contrato de serviço é um conjunto de trocas de mensagens relacionadas logicamente, uma operação de serviço é uma troca de mensagens única. Por exemplo, um `Hello` operação obviamente deve aceitar uma mensagem (de modo que o chamador pode anunciar a saudação) e podem ou não pode retornar uma mensagem (dependendo de cortesia da operação).  
  
 Para obter mais informações sobre contratos e outros conceitos do Windows Communication Foundation (WCF), consulte [conceitos fundamentais do Windows Communication Foundation](../../../docs/framework/wcf/fundamental-concepts.md). Este tópico enfoca a compreensão de contratos de serviço. Para obter mais informações sobre como criar os clientes que usam os contratos de serviço para se conectar aos serviços, consulte [visão geral do cliente WCF](../../../docs/framework/wcf/wcf-client-overview.md).  
  
## <a name="overview"></a>Visão geral  
 Este tópico fornece uma orientação conceitual de alto nível para projetar e implementar serviços WCF. Subtópicos fornecem informações mais detalhadas sobre as especificações de design e implementação. Antes de criar e implementar seu aplicativo do WCF, é recomendável que você:  
  
-   Entender é que um contrato de serviço, como ele funciona e como criá-lo.  
  
-   Entender o que os contratos de estado requisitos mínimos não pode dar suporte a essa configuração de tempo de execução ou o ambiente de hospedagem.  
  
## <a name="service-contracts"></a>Contratos de serviço  
 Um contrato de serviço Especifica o seguinte:  
  
-   As operações de um contrato expõe.  
  
-   A assinatura das operações em termos de mensagens trocadas.  
  
-   Os tipos de dados dessas mensagens.  
  
-   O local das operações.  
  
-   Os protocolos específicos e formatos de serialização que são usados para dar suporte à comunicação bem-sucedida com o serviço.  
  
 Por exemplo, um contrato de ordem de compra pode ter um `CreateOrder` tipos de operação que aceita uma entrada de informações do pedido e retorna informações de êxito ou falha, incluindo um identificador do pedido. Ele também pode ter um `GetOrderStatus` operação que aceita um identificador do pedido e retorna informações de status do pedido. Um contrato de serviço desse tipo deve especificar:  
  
1.  Se o contrato de ordem de compra consistiu `CreateOrder` e `GetOrderStatus` operações.  
  
2.  Que especificou as operações de mensagens de entrada e as mensagens de saída.  
  
3.  Os dados que podem ser executadas por essas mensagens.  
  
4.  Categóricas instruções sobre a infraestrutura de comunicação necessária para processar com êxito as mensagens. Por exemplo, esses detalhes incluem se e que formas de segurança são necessárias para estabelecer a comunicação bem-sucedida.  
  
 Para transmitir esse tipo de informação para outros aplicativos em várias plataformas (incluindo plataformas de não-Microsoft), os contratos de serviço XML são publicamente expressas em formatos XML padrão, como [Web Services Description Language](https://go.microsoft.com/fwlink/?LinkId=94952) ( WSDL) e [esquema XML](https://go.microsoft.com/fwlink/?LinkId=94953) (XSD), entre outros. Os desenvolvedores para várias plataformas podem usar essas informações de contrato público para criar aplicativos que podem se comunicar com o serviço, pois eles entendem o idioma da especificação e como essas linguagens são projetadas para habilitar a interoperação descrevendo o públicos formulários, formatos e protocolos que o serviço oferece suporte. Para obter mais informações sobre como o WCF trata esse tipo de informação, consulte [metadados](../../../docs/framework/wcf/feature-details/metadata.md).  
  
 Contratos podem ser expressas de muitas maneiras, e enquanto WSDL e XSD são excelentes linguagens para descrever serviços de forma acessível, eles são difíceis de idiomas a serem usados diretamente e são meramente descrições de um serviço, não as implementações de contrato de serviço. Portanto, os aplicativos do WCF usarem atributos gerenciados, interfaces e classes para definir a estrutura de um serviço e implementá-lo.  
  
 O contrato resultante definido em tipos gerenciados pode ser *exportados* como metadados — WSDL e XSD — quando necessário, os clientes ou outros implementadores de serviço. O resultado é um modelo de programação simples que pode ser descrito (usando metadados públicos) para qualquer aplicativo cliente. Os detalhes de mensagens SOAP subjacentes, o transporte e informações relacionadas à segurança e assim por diante, podem ser deixados para o WCF, que executa as conversões necessárias para e do sistema de tipo de contrato de serviço para o sistema de tipos XML automaticamente.  
  
 Para obter mais informações sobre a criação de contratos, consulte [Criando contratos de serviço](../../../docs/framework/wcf/designing-service-contracts.md). Para obter mais informações sobre como implementar contratos, consulte [implementar contratos de serviço](../../../docs/framework/wcf/implementing-service-contracts.md).  
  
### <a name="messages-up-front-and-center"></a>Mensagens de frente e no Centro  
 Usar interfaces gerenciadas, classes e métodos para operações de serviço de modelo é simples quando você está acostumado a chamada de procedimento remoto (RPC)-estilo de assinaturas de método, em que passar parâmetros para um método e receber valores de retorno é a forma normal de solicitando a funcionalidade de um objeto ou outro tipo de código. Por exemplo, os programadores que usam linguagens gerenciadas, como Visual Basic e C++ COM podem aplicar seus conhecimentos sobre a abordagem de estilo RPC (se estiver usando objetos ou interfaces) para a criação de contratos de serviço do WCF sem enfrentando os problemas inerentes Estilo RPC distribuídos sistemas do objeto. Orientação de serviço oferece os benefícios de programação orientado a mensagens, menos rígido, mantendo a facilidade e a familiaridade do RPC experiência em programação.  
  
 Muitos programadores são mais confortáveis com o aplicativo orientado a mensagens, interfaces de programação, como filas de mensagens, como Microsoft MSMQ, a <xref:System.Messaging> namespaces no .NET Framework ou envio de XML não estruturado em solicitações HTTP, para citar alguns. Para obter mais informações sobre programação no nível da mensagem, consulte [contratos de mensagem usando](../../../docs/framework/wcf/feature-details/using-message-contracts.md), [programação de nível de serviço canal](../../../docs/framework/wcf/extending/service-channel-level-programming.md), e [interoperabilidade com aplicativos de POX](../../../docs/framework/wcf/feature-details/interoperability-with-pox-applications.md).  
  
### <a name="understanding-the-hierarchy-of-requirements"></a>Noções básicas sobre a hierarquia de requisitos  
 Um contrato de serviço agrupa as operações; Especifica o padrão de troca de mensagem, os tipos de mensagem e os dados tipos realização dessas mensagens; e indica as categorias de comportamento de tempo de execução, uma implementação deve ter para o contrato de suporte (por exemplo, ele pode exigir que as mensagens de ser criptografadas e assinadas). O contrato de serviço em si não especifica exatamente como esses requisitos forem atendidos, é só isso, eles devem ser. O tipo de criptografia ou a forma em que uma mensagem for assinada é até a implementação e configuração de um serviço em conformidade.  
  
 Observe a maneira que o contrato requer certas coisas da implementação do contrato de serviço e a configuração de tempo de execução para Adicionar comportamento. O conjunto de requisitos que devem ser atendidos para expor um serviço para uso se baseia o conjunto anterior de requisitos. Se um contrato de tornar os requisitos da implementação, uma implementação pode exigir ainda mais da configuração e as associações que permitem que o serviço seja executado. Por fim, o aplicativo host deve também dão suporte a todos os requisitos que adicionar a configuração de serviço e associações.  
  
 Esse processo aditivas requisito é importante ter em mente ao projetar, implementar, configurar e hospedar um aplicativo de serviço do Windows Communication Foundation (WCF). Por exemplo, o contrato pode especificar que ele precisa dar suporte a uma sessão. Nesse caso, em seguida, você deve configurar a associação para dar suporte a esse requisito contratual ou a implementação do serviço não funcionará. Ou, se seu serviço requer a autenticação integrada do Windows e é hospedado no Internet Information Services (IIS), o aplicativo Web no qual reside o serviço deve ter autenticação integrada do Windows ativado e suporte anônimo desativado. Para obter mais informações sobre os recursos e o impacto dos tipos de aplicativos de host de serviço diferentes, consulte [serviços de hospedagem](../../../docs/framework/wcf/hosting-services.md).  
  
## <a name="see-also"></a>Consulte também
- [Criando contratos de serviço](../../../docs/framework/wcf/designing-service-contracts.md)
- [Implementando contratos de serviço](../../../docs/framework/wcf/implementing-service-contracts.md)
