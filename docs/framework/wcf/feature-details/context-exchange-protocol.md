---
title: Protocolo de intercâmbio de contexto
ms.date: 03/30/2017
ms.assetid: 3dfd38e0-ae52-491c-94f4-7a862b9843d4
ms.openlocfilehash: 00adb68d96f77ce0953811d13b5377ec4ed1e0ea
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185257"
---
# <a name="context-exchange-protocol"></a>Protocolo de intercâmbio de contexto
Esta seção descreve o protocolo de troca de contexto introduzido na versão .NET Framework versão 3.5 da Windows Communication Foundation (Windows Communication Foundation). Este protocolo permite que o canal do cliente aceite um contexto fornecido por um serviço e aplique-o a todas as solicitações subseqüentes a esse serviço enviadas pela mesma instância do canal do cliente. A implementação do protocolo de troca de contexto pode usar um dos dois seguintes mecanismos para propagar o contexto entre o servidor e o cliente: cookies HTTP ou um cabeçalho SOAP.  
  
 O protocolo de troca de contexto é implementado em uma camada de canal personalizada. O canal comunica o contexto de e <xref:System.ServiceModel.Channels.ContextMessageProperty> para a camada de aplicativo usando uma propriedade. Para transmissão entre pontos finais, o valor do contexto é serializado como um cabeçalho SOAP na camada do canal ou convertido para ou a partir das propriedades de mensagem que representam uma solicitação e resposta HTTP. Neste último caso, espera-se que uma das camadas de canal subjacente converta as propriedades de solicitação e mensagem de resposta HTTP para e a partir de cookies HTTP, respectivamente. A escolha do mecanismo utilizado para trocar <xref:System.ServiceModel.Channels.ContextExchangeMechanism> o contexto <xref:System.ServiceModel.Channels.ContextBindingElement>é feita utilizando a propriedade no . Os valores válidos são `HttpCookie` ou `SoapHeader`.  
  
 No cliente, uma instância de um canal pode operar em dois modos <xref:System.ServiceModel.Channels.IContextManager.Enabled%2A>com base nas configurações na propriedade do canal, .  
  
## <a name="mode-1-channel-context-management"></a>Modo 1: Gerenciamento de contexto de canal  
 Este é o <xref:System.ServiceModel.Channels.IContextManager.Enabled%2A> modo padrão `true`onde está definido para . Neste modo, o canal de contexto gerencia o contexto e armazena o contexto durante sua vida. O contexto pode ser recuperado do `IContextManager` canal `GetContext` através da propriedade do canal, chamando o método. O canal também pode ser pré-inicializado com contexto `SetContext` específico antes de ser aberto, chamando o método na propriedade do canal. Uma vez que o canal é inicializado com contexto, ele não pode ser reiniciado.  
  
 A seguir está uma lista de invariantes neste modo:  
  
- Qualquer tentativa de redefinir `SetContext` o contexto usando após <xref:System.InvalidOperationException>a abertura do canal lança um .  
  
- Qualquer tentativa de enviar <xref:System.ServiceModel.Channels.ContextMessageProperty> contexto usando o em <xref:System.InvalidOperationException>uma mensagem de saída lança um .  
  
- Se uma mensagem for recebida do servidor com um contexto específico, quando o canal <xref:System.ServiceModel.ProtocolException>já tiver sido inicializado com um contexto específico, isso resultará em um .  
  
    > [!NOTE]
    > É apropriado receber um contexto inicial do servidor somente se o canal for aberto sem qualquer contexto definido explicitamente.  
  
- A <xref:System.ServiceModel.Channels.ContextMessageProperty> mensagem de entrada é sempre nula.  
  
## <a name="mode-2-application-context-management"></a>Modo 2: Gerenciamento de contexto de aplicativos  
 Este é o <xref:System.ServiceModel.Channels.IContextManager.Enabled%2A> modo `false`quando é definido para . Neste modo, o canal de contexto não gerencia o contexto. É responsabilidade do aplicativo recuperar, gerenciar e aplicar <xref:System.ServiceModel.Channels.ContextMessageProperty>o contexto usando o . Qualquer tentativa `GetContext` de `SetContext` ligar <xref:System.InvalidOperationException>ou resultar em um .  
  
 Não importa qual modo seja escolhido, <xref:System.ServiceModel.Channels.IRequestChannel> <xref:System.ServiceModel.Channels.IRequestSessionChannel>a <xref:System.ServiceModel.Channels.IDuplexSessionChannel> fábrica do canal cliente suporta e os padrões de troca de mensagens.  
  
 No serviço, uma instância do canal é responsável por converter o contexto fornecido <xref:System.ServiceModel.Channels.ContextMessageProperty>pelo cliente em mensagens recebidas para o . A propriedade de mensagem pode então ser acessada pela camada do aplicativo ou outros canais mais adiante na pilha de chamadas. Os canais de serviço também permitem que a camada do aplicativo especifique <xref:System.ServiceModel.Channels.ContextMessageProperty> um novo valor de contexto a ser propagado de volta ao cliente, anexando um à mensagem de resposta. Esta propriedade é convertida para o cabeçalho SOAP ou biscoito HTTP que contém o contexto, que depende da configuração da vinculação. O ouvinte do canal <xref:System.ServiceModel.Channels.IReplyChannel> <xref:System.ServiceModel.Channels.IReplySessionChannel>de <xref:System.ServiceModel.Channels.IReplySessionChannel> serviço suporta padrões de troca de mensagens e de troca de mensagens.  
  
 O protocolo de troca `wsc:Context` de contexto introduz um novo cabeçalho SOAP para representar as informações de contexto quando os cookies HTTP não são usados para propagar o contexto. O esquema de cabeçalho de contexto permite qualquer número de elementos infantis, cada um com uma tecla de seqüência e conteúdo de seqüência. O seguinte é um exemplo de um cabeçalho de contexto.  
  
 `<Context xmlns="http://schemas.microsoft.com/ws/2006/05/context">`  
  
 `<property name="myContext">context-2</property>`  
  
 `</Context>`  
  
 Quando `HttpCookie` no modo, os `SetCookie` cookies são definidos usando o cabeçalho. O nome `WscContext`do cookie é . O valor do cookie é a codificação `wsc:Context` Base64 do cabeçalho. Este valor é incluído nas cotações.  
  
 O valor do contexto deve ser protegido contra modificações enquanto estiver em trânsito pela mesma razão que os cabeçalhos ws-endereçamento são protegidos – o cabeçalho é usado para determinar para onde despachar a solicitação no serviço. Portanto, `wsc:Context` o cabeçalho é necessário para ser assinado digitalmente ou assinado e criptografado no nível SOAP ou de transporte quando a vinculação oferece capacidade de proteção de mensagens. Quando os cookies HTTP são usados para propagar contexto, eles devem ser protegidos usando a segurança do transporte.  
  
 Os pontos finais de serviço que requerem suporte para o protocolo de troca de contexto podem torná-lo explícito na política publicada. Duas novas afirmações de política foram introduzidas para representar o requisito para que o cliente suporte o protocolo de troca de contexto no nível SOAP ou para habilitar o suporte a cookies HTTP. A geração dessas afirmações na política sobre o serviço <xref:System.ServiceModel.Channels.ContextBindingElement.ContextExchangeMechanism%2A> é controlada pelo valor da propriedade da seguinte forma:  
  
- Para <xref:System.ServiceModel.Channels.ContextExchangeMechanism.ContextSoapHeader>, a seguinte afirmação é gerada:  
  
    ```xml  
    <IncludeContext
    xmlns="http://schemas.microsoft.com/ws/2006/05/context"  
    protectionLevel="Sign" />  
    ```  
  
- Para <xref:System.ServiceModel.Channels.ContextExchangeMechanism.HttpCookie>, a seguinte afirmação é gerada:  
  
    ```xml  
    <HttpUseCookie xmlns="http://schemas.xmlsoap.org/soap/http"/>  
    ```  
  
## <a name="see-also"></a>Confira também

- [Guia de interoperabilidade de protocolos de serviços Web](../../../../docs/framework/wcf/feature-details/web-services-protocols-interoperability-guide.md)
