---
title: Resolvedor peer
ms.date: 03/30/2017
ms.assetid: d86d12a1-7358-450f-9727-b6afb95adb9c
ms.openlocfilehash: 33afffcbf11d757dfd003d1fd2bc9a17a3047a69
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837370"
---
# <a name="peer-resolvers"></a>Resolvedor peer
Para se conectar a uma malha, um nó par requer os endereços IP de outros nós. Os endereços IP são obtidos entrando em contato com um serviço resolvedor, que usa a ID de malha e retorna uma lista de endereços correspondentes aos nós registrados com essa ID de malha específica. O resolvedor mantém uma lista de endereços registrados, que ele cria, fazendo com que cada nó na malha seja registrado no serviço.  
  
 Você pode especificar qual serviço concreta PeerResolver usar por meio da propriedade `Resolver` da <xref:System.ServiceModel.NetPeerTcpBinding>.  
  
## <a name="supported-peer-resolvers"></a>Resolvedores de pares com suporte  
 O canal par dá suporte a dois tipos de resolvedores: PNRP (Peer Name Resolution Protocol) e serviços de resolvedor personalizado.  
  
 Por padrão, o canal de mesmo nível usa o serviço resolvedor de pares PNRP para a descoberta de pares e vizinhos na malha. Para situações/plataformas em que o PNRP não está disponível ou é viável, Windows Communication Foundation (WCF) fornece um serviço de descoberta alternativo baseado em servidor – o <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService>. Você também pode definir explicitamente um serviço de resolvedor personalizado escrevendo uma classe que implementa a interface <xref:System.ServiceModel.PeerResolvers.IPeerResolverContract>.  
  
### <a name="peer-name-resolution-protocol-pnrp"></a>PNRP (Peer Name Resolution Protocol)  
 O PNRP, o resolvedor padrão do Windows Vista, é um serviço de resolvedor de nomes distribuído e sem servidor. O PNRP também pode ser usado em [!INCLUDE[wxpsp2](../../../../includes/wxpsp2-md.md)] instalando o Advanced Networking Pack. Quaisquer dois clientes que executam a mesma versão do PNRP podem localizar um ao outro usando esse protocolo, desde que eles atendam a determinadas condições (como a falta de um firewall corporativo intermediário). Observe que a versão do PNRP fornecida com o Windows Vista é mais recente do que a versão incluída no pacote de rede avançado. Verifique o centro de download da Microsoft para obter atualizações para o PNRP para [!INCLUDE[wxpsp2](../../../../includes/wxpsp2-md.md)].  
  
### <a name="custom-resolver-services"></a>Serviços de resolvedor personalizado  
 Quando o serviço PNRP está indisponível ou você deseja ter controle total sobre a modelagem de malha, você pode usar um serviço de resolvedor personalizado baseado em servidor. Você pode definir explicitamente esse serviço escrevendo uma classe de resolvedor implementando a interface <xref:System.ServiceModel.PeerResolvers.IPeerResolverContract> ou usando a implementação padrão, <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService>.  
  
 Na implementação padrão do serviço, os registros do cliente expiram após um determinado período de tempo se o cliente não atualizar explicitamente o registro. Os clientes que usam o serviço resolvedor devem estar cientes do limite superior na latência do cliente-servidor para atualizar os registros no tempo com êxito. Isso envolve a escolha de um tempo limite de atualização apropriado (`RefreshInterval`) no serviço resolvedor. (Para obter mais informações, consulte [dentro do CustomPeerResolverService: registros de cliente](../../../../docs/framework/wcf/feature-details/inside-the-custompeerresolverservice-client-registrations.md).)  
  
 O gravador de aplicativos também deve considerar a proteção da conexão entre os clientes e o serviço de resolvedor personalizado. Você pode fazer isso usando as configurações de segurança no <xref:System.ServiceModel.NetTcpBinding> que os clientes usam para entrar em contato com o serviço de resolvedor. Você deve especificar as credenciais (se usadas) no `ChannelFactory` usado para criar o canal par. Essas credenciais são passadas para o `ChannelFactory` usado para criar canais para o resolvedor personalizado.  
  
> [!NOTE]
> Ao usar redes locais e improvisadas com um resolvedor personalizado, é altamente recomendável que os aplicativos que usam ou suportem redes de link local ou improvisadas incluam uma lógica que selecione um único endereço de link local para usar ao se conectar. Isso evita qualquer confusão possivelmente causada por computadores com vários endereços de link local. De acordo com isso, o canal par só dá suporte ao uso de um único endereço de link local a qualquer momento. Você pode especificar esse endereço com a propriedade `ListenIpAddress` no <xref:System.ServiceModel.NetPeerTcpBinding>.  
  
 Para ver uma demonstração de como implementar um resolvedor personalizado, consulte [resolvedor de pares personalizado do canal par](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751466(v=vs.90)).  
  
## <a name="in-this-section"></a>Nesta seção  
 [Sobre o CustomPeerResolverService: Registro de clientes](../../../../docs/framework/wcf/feature-details/inside-the-custompeerresolverservice-client-registrations.md)  
  
## <a name="see-also"></a>Consulte também

- [Conceitos de canal par](../../../../docs/framework/wcf/feature-details/peer-channel-concepts.md)
- [Segurança de canal par](../../../../docs/framework/wcf/feature-details/peer-channel-security.md)
- [Compilando um aplicativo de canal par](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md)
