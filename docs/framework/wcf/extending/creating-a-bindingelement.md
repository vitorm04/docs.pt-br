---
title: Criando um BindingElement
ms.date: 03/30/2017
ms.assetid: 01a35307-a41f-4ef6-a3db-322af40afc99
ms.openlocfilehash: 4b760f9373e64e153bd5a21469eb7a503283d35c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795828"
---
# <a name="creating-a-bindingelement"></a>Criando um BindingElement
Associações e elementos de associação (objetos que estendem <xref:System.ServiceModel.Channels.Binding?displayProperty=nameWithType> e <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType>, respectivamente) são o local em que o modelo de aplicativo Windows Communication Foundation (WCF) está associado a fábricas de canal e ouvintes de canal. Sem associações, o uso de canais personalizados requer programação no nível do canal, conforme descrito em programação de [nível de canal de serviço](service-channel-level-programming.md) e [programação de nível de canal de cliente](client-channel-level-programming.md). Este tópico discute o requisito mínimo para habilitar o uso do canal no WCF, o desenvolvimento de um <xref:System.ServiceModel.Channels.BindingElement> para seu canal e a habilitação do uso do aplicativo, conforme descrito na etapa 4 do [desenvolvimento de canais](developing-channels.md).  
  
## <a name="overview"></a>Visão geral  
 A criação <xref:System.ServiceModel.Channels.BindingElement> de um para seu canal permite que os desenvolvedores o usem em um aplicativo WCF. <xref:System.ServiceModel.Channels.BindingElement>os <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType> objetos podem ser usados da classe para conectar um aplicativo WCF ao seu canal sem ter que obter as informações de tipo precisas de seu canal.  
  
 Depois que <xref:System.ServiceModel.Channels.BindingElement> um tiver sido criado, você poderá habilitar mais funcionalidade, dependendo dos requisitos, seguindo as etapas de desenvolvimento de canal restantes descritas em [desenvolvimento de canais](developing-channels.md).  
  
## <a name="adding-a-binding-element"></a>Adicionando um elemento de associação  
 Para implementar um personalizado <xref:System.ServiceModel.Channels.BindingElement>, escreva uma classe que herde <xref:System.ServiceModel.Channels.BindingElement>de. Por exemplo, se você tiver desenvolvido um `ChunkingChannel` que pode dividir mensagens grandes em partes e remontá-las na outra extremidade, poderá usar esse canal em qualquer associação implementando um <xref:System.ServiceModel.Channels.BindingElement> e configurando a associação para usá-lo. O restante deste tópico usa o `ChunkingChannel` como um exemplo para demonstrar os requisitos de implementação de um elemento de associação.  
  
 Um `ChunkingBindingElement` é responsável por criar o `ChunkingChannelFactory` e `ChunkingChannelListener`o. Ele substitui <xref:System.ServiceModel.Channels.BindingElement.CanBuildChannelFactory%2A> e <xref:System.ServiceModel.Channels.BindingElement.CanBuildChannelListener%2A> implementa e verifica se o parâmetro de tipo é <xref:System.ServiceModel.Channels.IDuplexSessionChannel> (em nosso exemplo, essa é a única forma de canal com `ChunkingChannel`suporte no) e se os outros elementos de ligação na associação dão suporte a isso forma de canal.  
  
 <xref:System.ServiceModel.Channels.BindingElement.BuildChannelFactory%2A>primeiro verifica se a forma de canal solicitada pode ser criada e, em seguida, obtém uma lista de ações de mensagens a serem enfileiradas. Em seguida, ele cria `ChunkingChannelFactory`um novo, passando-o para a fábrica de canais interna. (Se você estiver criando um elemento de associação de transporte, esse elemento será o último na pilha de associação e, portanto, deverá criar um ouvinte de canal ou fábrica de canais.)  
  
 <xref:System.ServiceModel.Channels.BindingElement.BuildChannelListener%2A>o tem uma implementação semelhante para `ChunkingChannelListener` criar e passar o ouvinte de canal interno.  
  
 Como outro exemplo usando um canal de transporte, [o transporte: O](../samples/transport-udp.md) exemplo de UDP fornece a substituição a seguir.  
  
 No exemplo, o elemento de associação é `UdpTransportBindingElement`, que deriva de. <xref:System.ServiceModel.Channels.TransportBindingElement> Ele substitui os métodos a seguir para criar as fábricas associadas ao canal.  
  
```csharp  
public IChannelFactory<TChannel> BuildChannelFactory<TChannel>(BindingContext context)  
{  
    return (IChannelFactory<TChannel>)(object)new UdpChannelFactory(this, context);  
}  
  
public IChannelListener<TChannel> BuildChannelListener<TChannel>(BindingContext context)  
{  
    return (IChannelListener<TChannel>)(object)new UdpChannelListener(this, context);  
}  
```  
  
 Ele também contém membros para clonar `BindingElement` e retornar nosso esquema (SOAP. UDP).  
  
#### <a name="protocol-binding-elements"></a>Elementos de associação de protocolo  
 Novos elementos de associação podem substituir ou aumentar qualquer um dos elementos de associação incluídos, adicionando novos transportes, codificações ou protocolos de nível superior. Para criar um novo elemento de associação de protocolo, comece estendendo a <xref:System.ServiceModel.Channels.BindingElement> classe. No mínimo, você deve implementar o <xref:System.ServiceModel.Channels.BindingElement.Clone%2A?displayProperty=nameWithType> e implementar o usando <xref:System.ServiceModel.Channels.IChannel.GetProperty%2A?displayProperty=nameWithType>o `ChannelProtectionRequirements` . Isso retorna o <xref:System.ServiceModel.Security.ChannelProtectionRequirements> para esse elemento de associação.  Para obter mais informações, consulte <xref:System.ServiceModel.Security.ChannelProtectionRequirements>.  
  
 <xref:System.ServiceModel.Channels.BindingElement.Clone%2A>deve retornar uma cópia nova desse elemento de associação. Como prática recomendada, recomendamos que os autores de elemento de <xref:System.ServiceModel.Channels.BindingElement.Clone%2A> Associação implementem usando um construtor de cópia que chama o construtor de cópia base e, em seguida, clona quaisquer campos adicionais nessa classe.  
  
#### <a name="transport-binding-elements"></a>Elementos de associação de transporte  
 Para criar um novo elemento de associação de transporte, <xref:System.ServiceModel.Channels.TransportBindingElement> estenda a interface. No mínimo, você deve implementar o <xref:System.ServiceModel.Channels.BindingElement.Clone%2A> método e a <xref:System.ServiceModel.Channels.TransportBindingElement.Scheme%2A?displayProperty=nameWithType> propriedade.  
  
 <xref:System.ServiceModel.Channels.BindingElement.Clone%2A>– Deve retornar uma cópia nova desse elemento de associação.  Como prática recomendada, recomendamos que os autores de elemento de associação implementem clone por meio de um construtor de cópia que chama o construtor de cópia base e, em seguida, clona quaisquer campos adicionais nessa classe.  
  
 <xref:System.ServiceModel.Channels.TransportBindingElement.Scheme%2A>– A <xref:System.ServiceModel.Channels.TransportBindingElement.Scheme%2A> propriedade Get retorna o esquema de URI para o protocolo de transporte representado pelo elemento Binding. Por exemplo, o <xref:System.ServiceModel.Channels.HttpTransportBindingElement?displayProperty=nameWithType> e o <xref:System.ServiceModel.Channels.TcpTransportBindingElement?displayProperty=nameWithType> retornam "http" e "net. TCP" de suas <xref:System.ServiceModel.Channels.TransportBindingElement.Scheme%2A> respectivas propriedades.  
  
#### <a name="encoding-binding-elements"></a>Codificando elementos de associação  
 Para criar novos elementos de associação de codificação, comece estendendo a <xref:System.ServiceModel.Channels.BindingElement> classe e implementando a <xref:System.ServiceModel.Channels.MessageEncodingBindingElement?displayProperty=nameWithType> classe. No mínimo, você deve implementar os <xref:System.ServiceModel.Channels.BindingElement.Clone%2A>métodos, <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.CreateMessageEncoderFactory%2A?displayProperty=nameWithType> e a <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.MessageVersion%2A?displayProperty=nameWithType> propriedade.  
  
- <xref:System.ServiceModel.Channels.BindingElement.Clone%2A>. Retorna uma nova cópia desse elemento de associação. Como prática recomendada, recomendamos que os autores de elemento de <xref:System.ServiceModel.Channels.BindingElement.Clone%2A> Associação implementem usando um construtor de cópia que chama o construtor de cópia base e, em seguida, clona quaisquer campos adicionais nessa classe.  
  
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.CreateMessageEncoderFactory%2A>. Retorna um <xref:System.ServiceModel.Channels.MessageEncoderFactory>, que fornece um identificador para a classe real que implementa o novo codificador e que deve <xref:System.ServiceModel.Channels.MessageEncoder>ser estendido. Para obter mais informações, consulte <xref:System.ServiceModel.Channels.MessageEncoderFactory> e <xref:System.ServiceModel.Channels.MessageEncoder>.  
  
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.MessageVersion%2A>. Retorna o <xref:System.ServiceModel.Channels.MessageVersion> usado nessa codificação, que representa as versões de SOAP e WS-Addressing em uso.  
  
 Para obter uma lista completa de métodos e propriedades opcionais para elementos de associação de codificação definidos <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>pelo usuário, consulte.  
  
 Para obter mais informações sobre como criar um novo elemento de associação, consulte [Criando associações definidas pelo usuário](creating-user-defined-bindings.md).  
  
 Depois de criar um elemento de associação para seu canal, retorne ao tópico [desenvolvendo canais](developing-channels.md) para ver se você deseja adicionar suporte ao arquivo de configuração ao seu elemento de associação, se e como adicionar suporte à publicação de metadados e se e como Construa uma associação definida pelo usuário que usa seu elemento de associação.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Channels.BindingElement>
- [Desenvolvimento de canais](developing-channels.md)
- [Porta UDP](../samples/transport-udp.md)
