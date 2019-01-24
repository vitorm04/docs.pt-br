---
title: Resolvedor peer
ms.date: 03/30/2017
ms.assetid: d86d12a1-7358-450f-9727-b6afb95adb9c
ms.openlocfilehash: b16358d05b9e457b4542e41297908e225885dad9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54496839"
---
# <a name="peer-resolvers"></a>Resolvedor peer
Para se conectar a uma malha, um nó par exige que os endereços IP dos outros nós. Endereços IP são obtidos por entrar em contato com um serviço de resolvedor, que usa a ID de malha e retorna uma lista de endereços correspondentes a nós registrados com essa ID de malha. O resolvedor mantém uma lista de endereços registrados, que será criado, fazendo com que cada nó na malha registrar com o serviço.  
  
 Você pode especificar qual serviço PeerResolver usar por meio de `Resolver` propriedade do <xref:System.ServiceModel.NetPeerTcpBinding>.  
  
## <a name="supported-peer-resolvers"></a>Resolvedores de pares com suporte  
 Canal par dá suporte a dois tipos de resolvedores de: Resolução de protocolo PNRP (Peer Name) e serviços do resolvedor personalizado.  
  
 Por padrão, o canal de mesmo nível usa o serviço de resolvedor de pares PNRP para a descoberta de vizinhos e colegas na malha. Para situações/plataformas em que o PNRP não está disponível ou é viável, o Windows Communication Foundation (WCF) fornece um serviço de descoberta, com base em servidor alternativo - o <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService>. Você pode definir explicitamente um serviço de resolvedor personalizado, escrevendo uma classe que implementa o <xref:System.ServiceModel.PeerResolvers.IPeerResolverContract> interface.  
  
### <a name="peer-name-resolution-protocol-pnrp"></a>Protocolo de resolução de nome de ponto (PNRP)  
 O PNRP, o resolvedor padrão para [!INCLUDE[wv](../../../../includes/wv-md.md)], é um serviço de resolvedor de nome distribuídos, sem servidor. O PNRP também pode ser usado em [!INCLUDE[wxpsp2](../../../../includes/wxpsp2-md.md)] instalando o Advanced Networking Pack. Quaisquer dois clientes executando a mesma versão do PNRP podem localizar uns aos outros usando esse protocolo, desde que eles atendem a determinadas condições (como a falta de um firewall corporativo intermediário). Observe que a versão do PNRP que é fornecido com [!INCLUDE[wv](../../../../includes/wv-md.md)] for mais recente que a versão incluída no Advanced Networking Pack. Verificar Microsoft Download Center as atualizações do PNRP para [!INCLUDE[wxpsp2](../../../../includes/wxpsp2-md.md)].  
  
### <a name="custom-resolver-services"></a>Serviços do resolvedor personalizado  
 Quando o serviço de PNRP não está disponível ou você deseja controle total sobre a formatação de malha, você pode usar um serviço de resolvedor personalizado, com base em servidor. Você pode definir explicitamente esse serviço, escrevendo uma classe de resolvedor Implementando a <xref:System.ServiceModel.PeerResolvers.IPeerResolverContract> interface ou usando a implementação padrão da caixa de entrada, <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService>.  
  
 Na implementação padrão do serviço, registros de cliente expirarem após um determinado período de tempo, se o cliente não atualiza explicitamente o registro. Os clientes que usam o serviço de resolvedor devem estar cientes do limite superior na latência de cliente-servidor para atualizar os registros com êxito no tempo. Isso envolve a escolha de um tempo limite de atualização apropriado (`RefreshInterval`) no serviço resolvedor. (Para obter mais informações, consulte [dentro o CustomPeerResolverService: Registros de cliente](../../../../docs/framework/wcf/feature-details/inside-the-custompeerresolverservice-client-registrations.md).)  
  
 O criador do aplicativo também deve considerar para proteger a conexão entre clientes e o serviço de resolvedor personalizado. Você pode fazer isso usando configurações de segurança no <xref:System.ServiceModel.NetTcpBinding> que os clientes usam para contatar o serviço resolvedor. Você deve especificar as credenciais (se usado) no `ChannelFactory` usado para criar o canal par. Essas credenciais são passadas para o `ChannelFactory` usado para criar canais para o resolvedor personalizado.  
  
> [!NOTE]
>  Ao usar redes locais e improvisadas com um resolvedor personalizado, é altamente recomendável que os aplicativos usando ou que dão suporte a redes de local de link ou improvisadas incluem lógica que seleciona um único endereço de vínculo local para usar ao se conectar. Isso impede que qualquer confusão potencialmente causado por computadores com vários endereços de vínculo local. Acordo com isso, Peer Channel dá suporte somente a um único endereço de vínculo local a qualquer momento. Você pode especificar esse endereço com o `ListenIpAddress` propriedade no <xref:System.ServiceModel.NetPeerTcpBinding>.  
  
 Para ver uma demonstração de como implementar um resolvedor personalizado, consulte [resolvedor de pares personalizado Peer Channel](https://msdn.microsoft.com/library/5b75a2bb-7ff1-4a14-abe7-3debf0537d23).  
  
## <a name="in-this-section"></a>Nesta seção  
 [O custompeerresolverservice: Registros de cliente](../../../../docs/framework/wcf/feature-details/inside-the-custompeerresolverservice-client-registrations.md)  
  
## <a name="see-also"></a>Consulte também
- [Conceitos de canal par](../../../../docs/framework/wcf/feature-details/peer-channel-concepts.md)
- [Segurança de canal par](../../../../docs/framework/wcf/feature-details/peer-channel-security.md)
- [Compilando um aplicativo de canal par](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md)
