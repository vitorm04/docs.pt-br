---
title: WSTrustChannelFactory e WSTrustChannel
ms.date: 03/30/2017
ms.assetid: 96cec467-e963-4132-b18b-7d0b3a2e979f
author: BrucePerlerMS
ms.openlocfilehash: ecc62292b2b064219127c369f43141a31ffe606d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61780062"
---
# <a name="wstrustchannelfactory-and-wstrustchannel"></a>WSTrustChannelFactory e WSTrustChannel
Se você já estiver familiarizado com o WCF (Windows Communication Foundation), saberá que um cliente WCF já é baseado em federação. Configurando um cliente WCF com uma <xref:System.ServiceModel.WSFederationHttpBinding> ou uma associação personalizada semelhante, você pode habilitar a autenticação federada em um serviço.

 O WCF obtém o token emitido pelo STS (serviço de token de segurança) nos bastidores e usa esse token para se autenticar no serviço. A principal limitação dessa abordagem é que não há nenhuma visibilidade na comunicação do cliente com o servidor. O WCF gera o RST (token de segurança de solicitação) automaticamente para o STS, com base nos parâmetros do token emitido na associação. Isso significa que o cliente não pode variar os parâmetros do RST por solicitação, inspecionar a RSTR (resposta do token de segurança de solicitação) para obter informações como as declarações de exibição nem armazenar o token em cache para uso futuro.

 No momento, o cliente WCF é adequado para cenários de federação básica. No entanto, um dos principais cenários ao qual o WIF (Windows Identity Foundation) dá suporte exige controle sobre o RST em um nível que o WCF não permite facilmente. Portanto, o WIF adiciona recursos que proporcionam mais controle sobre a comunicação com o STS.

 O WIF dá suporte aos seguintes cenários de federação:

- Uso de um cliente WCF sem nenhuma dependência do WIF para se autenticar em um serviço federado

- Habilitação do WIF em um cliente WCF para inserir um elemento ActAs ou OnBehalfOf no RST para o STS

- Uso do WIF sozinho para obter um token do STS e, em seguida, permissão para que um cliente WCF se autentique com esse token. Para obter mais informações, consulte a amostra [ClaimsAwareWebService](https://go.microsoft.com/fwlink/?LinkID=248406).

 O primeiro cenário é autoexplicativo: Os clientes WCF existentes continuarão a trabalhar com partes confiáveis do WIF e STSs. Este tópico aborda os dois cenários restantes.

## <a name="enhancing-an-existing-wcf-client-with-actas--onbehalfof"></a>Melhorando um cliente WCF existente com ActAs/OnBehalfOf
Em um cenário típico de delegação de identidade, um cliente chama um serviço de camada intermediária, que, em seguida, chama um serviço back-end. O serviço de camada intermediária atua como ou em nome do cliente.

> [!TIP]
> Qual é a diferença entre ActAs e OnBehalfOf?
>
> Do ponto de vista de protocolo WS-Trust:
>
> 1. Um elemento RST ActAs indica que o solicitante deseja obter um token que contém declarações sobre duas entidades distintas: o solicitante e uma entidade externa representada pelo token no elemento ActAs.
> 2. Um elemento RST OnBehalfOf indica que o solicitante deseja obter um token que contém declarações somente sobre uma entidade: a entidade externa representada pelo token no elemento OnBehalfOf.
>
> O recurso ActAs normalmente é usado em cenários que exigem a delegação de composição, em que o destinatário final do token emitido pode inspecionar a cadeia inteira de delegação e ver não apenas o cliente, mas todos os intermediários. Isso permite que ele execute o controle de acesso, a auditoria e outras atividades relacionadas, com base na cadeia inteira de delegação de identidade. O recurso ActAs normalmente é usado em sistemas de várias camadas para autenticar e transmitir informações sobre identidades entre as camadas, sem precisar passar essas informações na camada do aplicativo/lógica de negócios.
>
> O recurso OnBehalfOf é usado em cenários em que somente a identidade do cliente original é importante e é praticamente a mesma que o recurso de representação de identidade disponível no Windows. Quando OnBehalfOf é usado, o destinatário final do token emitido somente pode ver declarações sobre o cliente original e as informações sobre intermediários não são preservadas. Um padrão comum em que o recurso OnBehalfOf é usado é o padrão de proxy, no qual o cliente não pode acessar o STS diretamente, mas se comunica por meio de um gateway de proxy. O gateway de proxy autentica o chamador e coloca informações sobre o chamador no elemento OnBehalfOf da mensagem RST que ele então envia para o STS real para processamento. O token resultante contém apenas declarações relacionadas ao cliente do proxy, tornando o proxy completamente transparente para o receptor do token emitido. Observe que o WIF não dá suporte a \<wsse:SecurityTokenReference> nem a \<wsa:EndpointReferences> como filho de \<wst:OnBehalfOf>. A especificação WS-Trust permite três maneiras de identificar o solicitante original (em nome de quem o proxy está atuando). Elas são:
>
> - Referência de token de segurança. Uma referência a um token, na mensagem ou possivelmente recuperada fora de banda.
> - Referência de ponto de extremidade. Usada como uma chave para pesquisar dados, novamente fora de banda.
> - Token de segurança. Identifica o solicitante original diretamente.
>
> O WIF dá suporte apenas a tokens de segurança, criptografados ou não criptografados, como um elemento filho direto de \<wst:OnBehalfOf>.

 Essas informações são transmitidas para um emissor do WS-Trust usando os elementos de token ActAs e OnBehalfOf no RST.

 O WCF expõe um ponto de extensibilidade na associação que permite que os elementos XML arbitrários sejam adicionados ao RST. No entanto, como o ponto de extensibilidade está vinculado à associação, os cenários que exigem que o conteúdo do RST varie por chamada devem recriar o cliente para cada chamada, o que diminui o desempenho. O WIF usa métodos de extensão na classe `ChannelFactory` para permitir aos desenvolvedores anexar qualquer token obtido fora de banda ao RST. O exemplo de código a seguir mostra como usar um token que representa o cliente (como um X.509, nome de usuário ou token SAML [Security Assertion Markup Language]) e anexá-lo ao RST enviado para o emissor.

```csharp
IHelloService serviceChannel = channelFactory.CreateChannelActingAs<IHelloService>(clientSamlToken);
serviceChannel.Hello("Hi!");
```

 O WIF oferece os seguintes benefícios:

- O RST pode ser modificado por canal. Portanto, os serviços de camada intermediária não precisam recriar a fábrica de canais para cada cliente, o que melhora o desempenho.

- Isso funciona com os clientes WCF existentes, que possibilita um caminho de upgrade fácil para os serviços de camada intermediária do WCF existentes que desejam habilitar a semântica de delegação de identidade.

 No entanto, ainda não há nenhuma visibilidade na comunicação do cliente com o STS. Examinaremos isso no terceiro cenário.

## <a name="communicating-directly-with-an-issuer-and-using-the-issued-token-to-authenticate"></a>Comunicando-se diretamente com um emissor e usando o token emitido para autenticação
Para alguns cenários avançados, a melhoria de um cliente WCF não é suficiente. Os desenvolvedores que usam apenas o WCF normalmente usam contratos de Mensagem de Entrada/Mensagem de Saída e administram a análise do lado do cliente do emissor manualmente.

O WIF introduz as classes <xref:System.ServiceModel.Security.WSTrustChannelFactory> e <xref:System.ServiceModel.Security.WSTrustChannel> para permitir que o cliente se comunique diretamente com um emissor do WS-Trust. As classes <xref:System.ServiceModel.Security.WSTrustChannelFactory> e <xref:System.ServiceModel.Security.WSTrustChannel> permitem que objetos RST e RSTR fortemente tipados fluam entre o cliente e o emissor, conforme mostrado no exemplo de código a seguir.

```csharp
WSTrustChannelFactory trustChannelFactory = new WSTrustChannelFactory(stsBinding, stsAddress);
WSTrustChannel channel = (WSTrustChannel) trustChannelFactory.CreateChannel();
RequestSecurityToken rst = new RequestSecurityToken(RequestTypes.Issue);
rst.AppliesTo = new EndpointAddress(serviceAddress);
RequestSecurityTokenResponse rstr = null;
SecurityToken token = channel.Issue(rst, out rstr);
```

Observe que o parâmetro `out` no método <xref:System.ServiceModel.Security.WSTrustChannel.Issue%2A> permite o acesso ao RSTR para a inspeção do lado do cliente.

Até agora, você apenas viu como obter um token. O token retornado do objeto <xref:System.ServiceModel.Security.WSTrustChannel> é um `GenericXmlSecurityToken` que contém todas as informações necessárias para a autenticação em uma terceira parte confiável. O exemplo de código a seguir mostra como usar esse token.

```csharp
IHelloService serviceChannel = channelFactory.CreateChannelWithIssuedToken<IHelloService>( token );
serviceChannel.Hello("Hi!");
```

O método de extensão <xref:System.ServiceModel.ChannelFactory%601.CreateChannelWithIssuedToken%2A> no objeto `ChannelFactory` indica ao WIF que você obteve um token fora de banda e que ele deve interromper a chamada normal do WCF ao emissor e, em vez disso, usar o token obtido para se autenticar na terceira parte confiável. Isso traz os seguintes benefícios:

- Proporciona controle total sobre o processo de emissão de token.

- Dá suporte a cenários de ActAs/OnBehalfOf com a configuração direta dessas propriedades no RST de saída.

- Permite que decisões dinâmicas de confiança do lado do cliente sejam feitas com base no conteúdo do RSTR.

- Permite armazenar em cache e reutilizar o token retornado do método <xref:System.ServiceModel.Security.WSTrustChannel.Issue%2A>.

- <xref:System.ServiceModel.Security.WSTrustChannelFactory> e <xref:System.ServiceModel.Security.WSTrustChannel> permitem o controle do cache de canal, de falhas e da semântica de recuperação de acordo com as melhores práticas do WCF.

## <a name="see-also"></a>Consulte também

- [Recursos do WIF](../../../docs/framework/security/wif-features.md)