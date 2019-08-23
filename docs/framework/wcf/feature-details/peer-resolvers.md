---
title: Resolvedor peer
ms.date: 03/30/2017
ms.assetid: d86d12a1-7358-450f-9727-b6afb95adb9c
ms.openlocfilehash: 0547bb37b03235c61f43cec365551438f7931ad1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69909920"
---
# <a name="peer-resolvers"></a>Resolvedor peer
Para se conectar a uma malha, um nó par requer os endereços IP de outros nós. Os endereços IP são obtidos entrando em contato com um serviço resolvedor, que usa a ID de malha e retorna uma lista de endereços correspondentes aos nós registrados com essa ID de malha específica. O resolvedor mantém uma lista de endereços registrados, que ele cria, fazendo com que cada nó na malha seja registrado no serviço.  
  
 Você pode especificar qual serviço concreta PeerResolver usar por meio da `Resolver` propriedade <xref:System.ServiceModel.NetPeerTcpBinding>do.  
  
## <a name="supported-peer-resolvers"></a>Resolvedores de pares com suporte  
 O canal par dá suporte a dois tipos de resolvedores: PNRP (Peer Name Resolution Protocol) e serviços de resolvedor personalizado.  
  
 Por padrão, o canal de mesmo nível usa o serviço resolvedor de pares PNRP para a descoberta de pares e vizinhos na malha. Para situações/plataformas em que o PNRP não está disponível ou é viável, Windows Communication Foundation (WCF) fornece um serviço de descoberta alternativo baseado em <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService>servidor – o. Você também pode definir explicitamente um serviço de resolvedor personalizado escrevendo uma classe que implementa <xref:System.ServiceModel.PeerResolvers.IPeerResolverContract> a interface.  
  
### <a name="peer-name-resolution-protocol-pnrp"></a>PNRP (Peer Name Resolution Protocol)  
 O PNRP, o resolvedor [!INCLUDE[wv](../../../../includes/wv-md.md)]padrão para, é um serviço de resolução de nomes distribuído e sem servidor. O PNRP também pode ser usado [!INCLUDE[wxpsp2](../../../../includes/wxpsp2-md.md)] no instalando o pacote de rede avançado. Quaisquer dois clientes que executam a mesma versão do PNRP podem localizar um ao outro usando esse protocolo, desde que eles atendam a determinadas condições (como a falta de um firewall corporativo intermediário). Observe que a versão do PNRP fornecida com [!INCLUDE[wv](../../../../includes/wv-md.md)] o é mais recente do que a versão incluída no pacote de rede avançado. Verifique o centro de download da Microsoft para obter atualizações [!INCLUDE[wxpsp2](../../../../includes/wxpsp2-md.md)]para o PNRP para o.  
  
### <a name="custom-resolver-services"></a>Serviços de resolvedor personalizado  
 Quando o serviço PNRP está indisponível ou você deseja ter controle total sobre a modelagem de malha, você pode usar um serviço de resolvedor personalizado baseado em servidor. Você pode definir explicitamente esse serviço escrevendo uma classe de resolvedor implementando a <xref:System.ServiceModel.PeerResolvers.IPeerResolverContract> interface ou usando a implementação padrão na caixa,. <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService>  
  
 Na implementação padrão do serviço, os registros do cliente expiram após um determinado período de tempo se o cliente não atualizar explicitamente o registro. Os clientes que usam o serviço resolvedor devem estar cientes do limite superior na latência do cliente-servidor para atualizar os registros no tempo com êxito. Isso envolve a escolha de um tempo limite de atualização`RefreshInterval`apropriado () no serviço resolvedor. (Para obter mais informações, [consulte dentro do CustomPeerResolverService: Registros de cliente](../../../../docs/framework/wcf/feature-details/inside-the-custompeerresolverservice-client-registrations.md).)  
  
 O gravador de aplicativos também deve considerar a proteção da conexão entre os clientes e o serviço de resolvedor personalizado. Você pode fazer isso usando as configurações de segurança no <xref:System.ServiceModel.NetTcpBinding> que os clientes usam para entrar em contato com o serviço de resolvedor. Você deve especificar as credenciais (se usadas) no `ChannelFactory` usado para criar o canal par. Essas credenciais são passadas para `ChannelFactory` o usado para criar canais para o resolvedor personalizado.  
  
> [!NOTE]
> Ao usar redes locais e improvisadas com um resolvedor personalizado, é altamente recomendável que os aplicativos que usam ou suportem redes de link local ou improvisadas incluam uma lógica que selecione um único endereço de link local para usar ao se conectar. Isso evita qualquer confusão possivelmente causada por computadores com vários endereços de link local. De acordo com isso, o canal par só dá suporte ao uso de um único endereço de link local a qualquer momento. Você pode especificar esse endereço com a `ListenIpAddress` propriedade <xref:System.ServiceModel.NetPeerTcpBinding>no.  
  
 Para ver uma demonstração de como implementar um resolvedor personalizado, consulte resolvedor de [pares personalizado do canal par](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751466(v=vs.90)).  
  
## <a name="in-this-section"></a>Nesta seção  
 [Dentro do CustomPeerResolverService: Registros de cliente](../../../../docs/framework/wcf/feature-details/inside-the-custompeerresolverservice-client-registrations.md)  
  
## <a name="see-also"></a>Consulte também

- [Conceitos de canal par](../../../../docs/framework/wcf/feature-details/peer-channel-concepts.md)
- [Segurança de canal par](../../../../docs/framework/wcf/feature-details/peer-channel-security.md)
- [Compilando um aplicativo de canal par](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md)
