---
title: Associações e elementos de associações
ms.date: 03/30/2017
helpviewer_keywords:
- binding elements [WCF]
ms.assetid: 765ff77b-7682-4ea3-90eb-e4d751e37379
ms.openlocfilehash: 33ebb07e350dbbbdd324b442f52dfb6287322bd8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59976762"
---
# <a name="bindings-and-binding-elements"></a>Associações e elementos de associações
Associações são coleções de elementos de configuração especial, chamados *elementos de associação*, que é avaliado no tempo de execução do serviço sempre que um cliente ou o ponto de extremidade de serviço está sendo construído. O tipo e a ordem dos elementos de associação dentro de uma associação determina a seleção e a ordem de empilhamento dos canais de transporte e protocolo na pilha de canais de um ponto de extremidade.  
  
 Associações, especialmente as associações fornecidas pelo sistema, normalmente, também têm um número de propriedades de configuração que refletem as propriedades mais comumente modificadas dos elementos de associação encapsulado.  
  
 Uma associação deve conter exatamente um elemento de associação de transporte. Cada elemento de associação de transporte implica uma elemento de associação, que pode ser substituído pela adição de no máximo uma mensagem de codificação de elemento de associação para a associação de codificação de mensagens de padrão. Além dos elementos de associação do codificador e transporte, a associação pode conter qualquer número de elementos de associação de protocolo que juntos implementar a funcionalidade necessária para o serviço e enviar uma mensagem SOAP de um ponto de extremidade para outro. Para obter detalhes, consulte [usando associações para configurar os serviços e clientes](../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md).  
  
## <a name="extending-bindings-and-binding-elements"></a>Estendendo associações e elementos de associação  
 Windows Communication Foundation (WCF) inclui associações fornecidas pelo sistema que abrangem uma ampla variedade de cenários. (Para obter mais informações, consulte [System-Provided associações](../../../../docs/framework/wcf/system-provided-bindings.md).) Pode haver ocasiões, no entanto, quando você precisa criar e usar uma associação que não está incluída no WCF. Os cenários a seguir exigem a criação de uma nova associação.  
  
-   Para usar um novo elemento de associação (por exemplo, um novo transporte, codificação ou elemento de associação de protocolo), você deve criar uma nova associação que inclui esse elemento de ligação. Por exemplo, se você tiver adicionado um personalizado `UdpTransportBindingElement` para transporte UDP, você precisaria criar uma nova associação para fazer uso dele. Para obter informações sobre como executar esse comportamento usando o <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> de tipo, consulte [ligações personalizadas](../../../../docs/framework/wcf/extending/custom-bindings.md).  
  
-   Para configurar os elementos de associação existente de forma que as associações fornecidas pelo sistema para não expor em propriedades públicas. Por exemplo, você deve criar uma nova associação para alterar a ordem na qual assinatura e criptografia operações são executadas. Para obter informações sobre como executar esse comportamento, consulte [como: Personalizar uma associação fornecida pelo sistema](../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md).  
  
-   Para estabelecer associações padrão corporativas que expõem apenas as opções de configuração específicas. Por exemplo, para criar para a sua empresa uma variante do <xref:System.ServiceModel.WSHttpBinding> para sua empresa em que a segurança não pode ser desabilitada, crie uma nova associação que se comporta como o <xref:System.ServiceModel.WSHttpBinding>, mas com a segurança sempre ativa. Para obter detalhes, consulte [Criando associações](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md).  
  
-   Para executar alguma personalização de metadados, normalmente, mas não necessariamente para configurar ou usar algum elemento de associação personalizada. Para obter mais informações sobre como fornecer suporte a metadados para associações e elementos de associação, consulte [configuração e suporte a metadados](../../../../docs/framework/wcf/extending/configuration-and-metadata-support.md).  

## <a name="channels-bindings-and-binding-elements"></a>Canais, associações e elementos de associação  
 Associações e elementos de associação são a conexão entre o modelo de programação de aplicativo, que inclui os atributos e comportamentos, e o modelo de canal, que inclui as fábricas e ouvintes, codificadores de mensagem e transporte e protocolo implementações. Normalmente, associações e elementos de associação são implementadas para habilitar os canais a ser usada pela camada de aplicativo.  
  
 A camada de canais transmite ou recebe mensagens de e para a camada de serviço e transporta as mensagens entre pontos de extremidade. Em um cliente, a camada de canais é uma pilha de fábricas de canais que criam canais de um ponto de extremidade de rede. Em um serviço, a camada de canais é uma pilha de ouvintes de canais para aceitar canais recebidos um ponto de extremidade de rede.  
  
 Há dois tipos gerais de canais: canais de protocolo e canais de transporte. Canais de transporte são responsáveis pela transmissão real de uma mensagem de ponto de extremidade de uma rede para outra. Canais de transporte devem ter um codificador de mensagem padrão e devem ser capazes de usar um codificador de mensagem alternativo fornecido por meio de um elemento de associação do codificador de mensagem. Um codificador de mensagem é responsável por transformar uma <xref:System.ServiceModel.Channels.Message?displayProperty=nameWithType> em uma representação eletrônica e vice-versa. Canais de protocolo serão responsáveis por implementar os protocolos de nível de SOAP (por exemplo, WS-Security ou WS-ReliableMessaging).  
  
 O requisito primário para os canais de transporte e protocolo é que eles implementem as interfaces necessárias do canal. Para criar uma camada de canais de trabalho deve ter associado fábricas e ouvintes, e assim por diante. Para usar as implementações de canal do WCF, é preciso haver um elementos de associação associado derivado de <xref:System.ServiceModel.Channels.BindingElement> para cada canal e deve haver um elemento de extensão de associação relacionados para inclusão nos arquivos de configuração que é derivada de <xref:System.ServiceModel.Configuration.BindingElementExtensionElement>.  
  
 Como mencionados elementos anteriores, associações para codificadores de mensagem, protocolo e transporte implementações de canal podem ser empilhadas para formar uma pilha de canais e o mecanismo para alinhá-las em um conjunto ordenado é a associação. Associações e elementos de associação conecte-se o modelo de programação de aplicativo para o modelo de canal. Você pode usar suas implementações de canal do código diretamente, mas a menos que os protocolos, transportes e codificadores são implementados como elementos de associação não pode ser usados do modelo de programação de camada de serviço.  
  
 Para obter detalhes sobre o desenvolvimento de canais e seus elementos de associação, consulte [estendendo a camada do canal](../../../../docs/framework/wcf/extending/extending-the-channel-layer.md).
