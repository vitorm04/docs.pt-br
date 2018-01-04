---
title: Resolvedor peer
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d86d12a1-7358-450f-9727-b6afb95adb9c
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e946066a352fb29c593a7d84fd6e728c226a3175
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="peer-resolvers"></a>Resolvedor peer
Para conectar a uma malha, um nó ponto requer que os endereços IP de outros nós. Endereços IP são obtidos entrando em contato com um serviço de resolução, que usa a ID de malha e retorna uma lista de endereços correspondentes a nós registrado com esse ID de malha. O resolvedor mantém uma lista de endereços de registrado, ele cria, fazendo com que cada nó na malha registrar com o serviço.  
  
 Você pode especificar qual serviço PeerResolver usar por meio de `Resolver` propriedade do <xref:System.ServiceModel.NetPeerTcpBinding>.  
  
## <a name="supported-peer-resolvers"></a>Resolvedor Peer com suporte  
 Canal par dá suporte a dois tipos de resolvedores: resolução de protocolo PNRP (Peer Name) e os serviços do resolvedor personalizado.  
  
 Por padrão, o canal de mesmo nível usa o serviço de resolução PNRP ponto a ponto para a descoberta de pontos e vizinhos na malha. Para situações/plataformas em que o PNRP não está disponível ou for viável, [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] fornece um serviço de detecção baseada em servidor alternativo - o <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService>. Você pode definir explicitamente um serviço resolvedor personalizado, escrevendo uma classe que implementa o <xref:System.ServiceModel.PeerResolvers.IPeerResolverContract> interface.  
  
### <a name="peer-name-resolution-protocol-pnrp"></a>Protocolo PNRP (PNRP)  
 O PNRP, o resolvedor padrão para [!INCLUDE[wv](../../../../includes/wv-md.md)], é um serviço de resolução de nome distribuída, sem servidor. O PNRP também pode ser usado em [!INCLUDE[wxpsp2](../../../../includes/wxpsp2-md.md)] instalando o pacote de rede avançado. Dois clientes executando a mesma versão do PNRP podem localizar uns aos outros usando esse protocolo, desde que eles atendam a certas condições (como a falta de um firewall corporativo intermediário). Observe que a versão do PNRP que acompanha o [!INCLUDE[wv](../../../../includes/wv-md.md)] é mais recente que a versão incluída no pacote de rede avançado. Verifique a Microsoft Download Center para atualizações PNRP para [!INCLUDE[wxpsp2](../../../../includes/wxpsp2-md.md)].  
  
### <a name="custom-resolver-services"></a>Serviços de resolvedor personalizado  
 Quando o serviço PNRP não está disponível ou você deseja controle total sobre a formatação de malha, você pode usar um serviço resolvedor personalizado, com base em servidor. Você pode definir explicitamente esse serviço, escrevendo uma classe do resolvedor Implementando o <xref:System.ServiceModel.PeerResolvers.IPeerResolverContract> interface ou usando a implementação do padrão de caixa de entrada, <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService>.  
  
 Na implementação padrão do serviço, registros de cliente expirarem após um determinado período de tempo se o cliente não atualiza explicitamente o registro. Os clientes que usam o serviço de resolução devem estar atento o limite superior na latência de cliente-servidor para atualizar com êxito os registros no tempo. Isso envolve a escolha de um tempo limite de atualização apropriado (`RefreshInterval`) no serviço de resolução. (Para obter mais informações, consulte [dentro o CustomPeerResolverService: registro de clientes](../../../../docs/framework/wcf/feature-details/inside-the-custompeerresolverservice-client-registrations.md).)  
  
 O gravador de aplicativos também deve considerar para proteger a conexão entre clientes e o serviço resolvedor personalizado. Você pode fazer isso usando as configurações de segurança no <xref:System.ServiceModel.NetTcpBinding> que os clientes usam para entrar em contato com o serviço de resolução. Você deve especificar credenciais (se usado) no `ChannelFactory` usado para criar o canal par. Essas credenciais são passadas para o `ChannelFactory` usado para criar canais para o resolvedor personalizado.  
  
> [!NOTE]
>  Ao usar redes locais e imediatamente com um resolvedor personalizado, é altamente recomendável que aplicativos usando o ou o suporte a redes de local de link ou imediatamente incluem lógica que seleciona um único endereço de conexão local para usar ao se conectar. Isso evita confusão potencialmente causado por computadores com vários endereços de conexão local. Acordo com isso, canal par somente oferece suporte a um único endereço de conexão local a qualquer momento. Você pode especificar esse endereço com o `ListenIpAddress` propriedade o <xref:System.ServiceModel.NetPeerTcpBinding>.  
  
 Para ver uma demonstração de como implementar um resolvedor personalizado, consulte [resolvedor ponto a ponto personalizado de canal par](http://msdn.microsoft.com/en-us/5b75a2bb-7ff1-4a14-abe7-3debf0537d23).  
  
## <a name="in-this-section"></a>Nesta seção  
 [Sobre o CustomPeerResolverService: Registro de clientes](../../../../docs/framework/wcf/feature-details/inside-the-custompeerresolverservice-client-registrations.md)  
  
## <a name="see-also"></a>Consulte também  
 [Conceitos de canal par](../../../../docs/framework/wcf/feature-details/peer-channel-concepts.md)  
 [Segurança de canal par](../../../../docs/framework/wcf/feature-details/peer-channel-security.md)  
 [Compilando um aplicativo de canal par](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md)
