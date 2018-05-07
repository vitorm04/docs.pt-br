---
title: Criando um BindingElement
ms.date: 03/30/2017
ms.assetid: 01a35307-a41f-4ef6-a3db-322af40afc99
ms.openlocfilehash: fdc3ec1fef86ad31434ea372740497969c7ae6a7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="creating-a-bindingelement"></a>Criando um BindingElement
Associações e elementos de associação (objetos que estendem <xref:System.ServiceModel.Channels.Binding?displayProperty=nameWithType> e <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType>, respectivamente) são o local onde o modelo de aplicativo do Windows Communication Foundation (WCF) é associado fábricas de canais e ouvintes de canais. Sem associações, usar os canais personalizados exige a programação no nível do canal como descrito em [programação de nível de serviço de canal](../../../../docs/framework/wcf/extending/service-channel-level-programming.md) e [programação de nível de canal cliente](../../../../docs/framework/wcf/extending/client-channel-level-programming.md). Este tópico discute o requisito mínimo para habilitar o uso do seu canal em [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], o desenvolvimento de um <xref:System.ServiceModel.Channels.BindingElement> de canal e habilitar o uso do aplicativo conforme descrito na etapa 4 do [canais de desenvolvimento](../../../../docs/framework/wcf/extending/developing-channels.md).  
  
## <a name="overview"></a>Visão geral  
 Criando um <xref:System.ServiceModel.Channels.BindingElement> para seu canal permite que os desenvolvedores para usá-lo em um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplicativo. <xref:System.ServiceModel.Channels.BindingElement> objetos podem ser usados do <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType> classe para conectar-se um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplicativo para o canal sem a necessidade das informações de tipo exato do seu canal.  
  
 Uma vez um <xref:System.ServiceModel.Channels.BindingElement> tiver sido criado, você pode habilitar a funcionalidade mais, dependendo das suas necessidades, seguindo as etapas restantes de desenvolvimento de canal descritas em [canais de desenvolvimento](../../../../docs/framework/wcf/extending/developing-channels.md).  
  
## <a name="adding-a-binding-element"></a>Adicionando um elemento de associação  
 Para implementar um personalizado <xref:System.ServiceModel.Channels.BindingElement>, escrever uma classe que herda de <xref:System.ServiceModel.Channels.BindingElement>. Por exemplo, se você tiver desenvolvido uma `ChunkingChannel` que pode quebrar mensagens grandes em partes e remonte-los na outra extremidade, você pode usar esse canal em qualquer associação com a implementação de um <xref:System.ServiceModel.Channels.BindingElement> e configurar a associação para usá-lo. O restante deste tópico usa o `ChunkingChannel` como um exemplo para demonstrar os requisitos de implementação de um elemento de associação.  
  
 Um `ChunkingBindingElement` é responsável pela criação de `ChunkingChannelFactory` e `ChunkingChannelListener`. Ela substitui <xref:System.ServiceModel.Channels.BindingElement.CanBuildChannelFactory%2A> e <xref:System.ServiceModel.Channels.BindingElement.CanBuildChannelListener%2A> implementações e verifica se o parâmetro de tipo está <xref:System.ServiceModel.Channels.IDuplexSessionChannel> (em nosso exemplo, essa é a forma de canal único com suporte a `ChunkingChannel`) e que os outros elementos de associação na associação oferece suporte a isso forma de canal.  
  
 <xref:System.ServiceModel.Channels.BindingElement.BuildChannelFactory%2A> primeiro verifica que a forma de canal solicitado pode ser criada e, em seguida, obtém uma lista de ações de mensagem a ser em partes. Em seguida, cria um novo `ChunkingChannelFactory`, passando a fábrica interna de canais. (Se você estiver criando um elemento de associação de transporte, esse elemento é o último na pilha de associação e, portanto, deve criar um ouvinte de canal ou fábrica de canais.)  
  
 <xref:System.ServiceModel.Channels.BindingElement.BuildChannelListener%2A> tem uma implementação semelhante para a criação de `ChunkingChannelListener` e passá-lo a escuta de canal interna.  
  
 Como outro exemplo, usando um canal de transporte, o [transporte: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) exemplo fornece a substituição a seguir.  
  
 No exemplo, o elemento de associação é `UdpTransportBindingElement`, que é derivado de <xref:System.ServiceModel.Channels.TransportBindingElement>. Ela substitui os seguintes métodos para criar as fábricas associadas ao canal.  
  
```  
public IChannelFactory<TChannel> BuildChannelFactory<TChannel>(BindingContext context)  
{  
            return (IChannelFactory<TChannel>)(object)new UdpChannelFactory(this, context);  
}  
  
public IChannelListener<TChannel> BuildChannelListener<TChannel>(BindingContext context)  
{  
            return (IChannelListener<TChannel>)(object)new UdpChannelListener(this, context);  
}  
```  
  
 Ele também contém membros para clonagem de `BindingElement` e retornando nosso esquema (soap.udp).  
  
#### <a name="protocol-binding-elements"></a>Elementos de associação de protocolo  
 Novos elementos de associação podem substituir ou aumentar a qualquer um dos elementos de associação incluído, adicionando novos transportes, codificações ou protocolos de nível superior. Para criar um novo elemento de associação de protocolo, iniciar, estendendo o <xref:System.ServiceModel.Channels.BindingElement> classe. No mínimo, em seguida, você deve implementar o <xref:System.ServiceModel.Channels.BindingElement.Clone%2A?displayProperty=nameWithType> e implementar o `ChannelProtectionRequirements` usando <xref:System.ServiceModel.Channels.IChannel.GetProperty%2A?displayProperty=nameWithType>. Isso retorna o <xref:System.ServiceModel.Security.ChannelProtectionRequirements> para esse elemento de associação.  Para obter mais informações, consulte <xref:System.ServiceModel.Security.ChannelProtectionRequirements>.  
  
 <xref:System.ServiceModel.Channels.BindingElement.Clone%2A> deve retornar uma nova cópia deste elemento de associação. Como prática recomendada, é recomendável que esse elemento de associação autores implementar <xref:System.ServiceModel.Channels.BindingElement.Clone%2A> usando um construtor de cópia que chama o construtor de cópia base, em seguida, clona outros campos nesta classe.  
  
#### <a name="transport-binding-elements"></a>Elementos de associação de transporte  
 Para criar um novo elemento de associação de transporte, estender o <xref:System.ServiceModel.Channels.TransportBindingElement> interface. No mínimo, em seguida, você deve implementar o <xref:System.ServiceModel.Channels.BindingElement.Clone%2A> método e o <xref:System.ServiceModel.Channels.TransportBindingElement.Scheme%2A?displayProperty=nameWithType> propriedade.  
  
 <xref:System.ServiceModel.Channels.BindingElement.Clone%2A> – Deve retornar uma nova cópia do elemento de associação.  Como prática recomendada, recomendamos que os autores do elemento de associação implementem Clone por meio de um construtor de cópia que chama o construtor de cópia base, em seguida, copia todos os campos adicionais nesta classe.  
  
 <xref:System.ServiceModel.Channels.TransportBindingElement.Scheme%2A> – A <xref:System.ServiceModel.Channels.TransportBindingElement.Scheme%2A> obter propriedade retorna o esquema de URI para o protocolo de transporte representado pelo elemento de associação. Por exemplo, o <xref:System.ServiceModel.Channels.HttpTransportBindingElement?displayProperty=nameWithType> e <xref:System.ServiceModel.Channels.TcpTransportBindingElement?displayProperty=nameWithType> retornar "http" e "NET" de seus respectivos <xref:System.ServiceModel.Channels.TransportBindingElement.Scheme%2A> propriedades.  
  
#### <a name="encoding-binding-elements"></a>Codificação de elementos de associação  
 Para criar a nova codificação elementos de associação, iniciar, estendendo o <xref:System.ServiceModel.Channels.BindingElement> classe e implementar a <xref:System.ServiceModel.Channels.MessageEncodingBindingElement?displayProperty=nameWithType> classe. No mínimo, em seguida, você deve implementar o <xref:System.ServiceModel.Channels.BindingElement.Clone%2A>, <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.CreateMessageEncoderFactory%2A?displayProperty=nameWithType> métodos e <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.MessageVersion%2A?displayProperty=nameWithType> propriedade.  
  
-   <xref:System.ServiceModel.Channels.BindingElement.Clone%2A>. Retorna uma nova cópia deste elemento de associação. Como prática recomendada, é recomendável que esse elemento de associação autores implementar <xref:System.ServiceModel.Channels.BindingElement.Clone%2A> usando um construtor de cópia que chama o construtor de cópia base, em seguida, clona outros campos nesta classe.  
  
-   <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.CreateMessageEncoderFactory%2A>. Retorna um <xref:System.ServiceModel.Channels.MessageEncoderFactory>, que fornece um identificador à classe real que implementa o novo codificador e que deve se estender <xref:System.ServiceModel.Channels.MessageEncoder>. Para obter mais informações, consulte <xref:System.ServiceModel.Channels.MessageEncoderFactory> e <xref:System.ServiceModel.Channels.MessageEncoder>.  
  
-   <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.MessageVersion%2A>. Retorna o <xref:System.ServiceModel.Channels.MessageVersion> usado nesta codificação, que representa as versões de SOAP e WS-Addressing em uso.  
  
 Para obter uma lista completa de métodos opcionais e as propriedades de elementos definidos pelo usuário de ligação de codificação, consulte <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>.  
  
 Para obter mais informações sobre como criar um novo elemento de associação, consulte [Criando associações](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md).  
  
 Depois de criar um elemento de associação para o canal, retornar para o [canais de desenvolvimento](../../../../docs/framework/wcf/extending/developing-channels.md) tópico para ver se você deseja adicionar suporte para arquivo de configuração para o elemento de associação, se e como adicionar suporte de publicação de metadados, e Se e como construir uma associação definida pelo usuário que usa o elemento de associação.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Channels.BindingElement>  
 [Desenvolvimento de canais](../../../../docs/framework/wcf/extending/developing-channels.md)  
 [Transporte: UDP](../../../../docs/framework/wcf/samples/transport-udp.md)
