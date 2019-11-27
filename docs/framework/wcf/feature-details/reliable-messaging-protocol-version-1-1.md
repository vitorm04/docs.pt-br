---
title: Protocolo de mensagem confiável versão 1.1
ms.date: 03/30/2017
ms.assetid: 0da47b82-f8eb-42da-8bfe-e56ce7ba6f59
ms.openlocfilehash: 9320787317131f42c4a82c6114a16fdea87567f4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283305"
---
# <a name="reliable-messaging-protocol-version-11"></a>Protocolo de mensagem confiável versão 1.1

Este tópico aborda os detalhes de implementação do Windows Communication Foundation (WCF) para o protocolo WS-ReliableMessaging de fevereiro de 2007 (versão 1,1) necessário para interoperação usando o transporte HTTP. O WCF segue a especificação WS-ReliableMessaging com as restrições e esclarecimentos explicados neste tópico. Observe que o protocolo WS-ReliableMessaging versão 1,1 é implementado a partir do .NET Framework 3,5.

O protocolo WS-ReliableMessaging de fevereiro de 2007 é implementado no WCF pelo <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>.

Para sua conveniência, o tópico usa as seguintes funções:

- Iniciador: o cliente que inicia a criação da sequência de mensagens WS-Reliable.

- Respondente: o serviço que recebe as solicitações do iniciador.

 Este documento usa os prefixos e namespaces na tabela a seguir.

|Prefixo|{1&gt;Namespace&lt;1}|
|-|-|
|WSRM|http://docs.oasis-open.org/ws-rx/wsrm/200702|
|netrm|http://schemas.microsoft.com/ws/2006/05/rm|
|s|http://www.w3.org/2003/05/soap-envelope|
|wsa|http://schemas.xmlsoap.org/ws/2005/08/addressing|
|wsse|http://docs.oasis-open.org/wss/2004/01/oasis-200401-wssecurity-secext-1.0.xsd|
|wsrmp|http://docs.oasis-open.org/ws-rx/wsrmp/200702|
|netrmp|http://schemas.microsoft.com/ws-rx/wsrmp/200702|
|WSP|(WS-Policy 1,2 ou WS-Policy 1,5)|

## <a name="messaging"></a>Mensagens

### <a name="sequence-creation"></a>Criação de sequência

O WCF implementa `CreateSequence` e `CreateSequenceResponse` mensagens para estabelecer uma sequência de mensagens confiáveis. As seguintes restrições se aplicam:

- B1101: o iniciador do WCF usa a mesma referência de ponto de extremidade que a `CreateSequence` `ReplyTo`da mensagem, `AcksTo` e `Offer/Endpoint`.

- R1102: as referências de ponto de extremidade `AcksTo`, `ReplyTo` e `Offer/Endpoint` na mensagem de `CreateSequence` devem ter valores de endereço com representações de cadeia de caracteres idênticas, de modo que correspondam ao octeto.

  - O respondente do WCF verifica se a parte do URI do `AcksTo`, `ReplyTo` e `Endpoint` referências do ponto de extremidade são idênticas antes de criar uma sequência.

- R1103: as referências de ponto de extremidade `AcksTo`, `ReplyTo` e `Offer/Endpoint` na mensagem de `CreateSequence` devem ter o mesmo conjunto de parâmetros de referência.

  - O WCF não impõe, mas pressupõe que os parâmetros de referência do `AcksTo`, `ReplyTo` e `Offer/Endpoint` referências de ponto de extremidade em `CreateSequence` são idênticos e usa parâmetros de referência da referência de ponto de extremidade `ReplyTo` para confirmações e mensagens de sequências de inverso.

- B1104: o iniciador do WCF não gera o elemento `Expires` opcional ou `Offer/Expires` na mensagem de `CreateSequence`.

- B1105: ao acessar a mensagem de `CreateSequence`, o respondente do WCF usa o valor `Expires` no elemento `CreateSequence` como o valor `Expires` no elemento `CreateSequenceResponse`. Caso contrário, o respondente do WCF lê e ignora os valores de `Expires` e `Offer/Expires`.

- B1106: ao acessar a mensagem de `CreateSequenceResponse`, o iniciador do WCF lê o valor de `Expires` opcional, mas não o usa.

- B1107: o iniciador e o respondente do WCF sempre geram o elemento `IncompleteSequenceBehavior` opcional nos elementos `CreateSequence/Offer` e `CreateSequenceResponse`.

- B1108: o WCF usa apenas os valores `DiscardFollowingFirstGap` e `NoDiscard` no elemento `IncompleteSequenceBehavior`.

  - O WS-ReliableMessaging utiliza o mecanismo de `Offer` para estabelecer as duas sequências correlacionadas de converso que formam uma sessão.

- B1109: se `CreateSequence` contiver um elemento `Offer`, o respondente unidirecional do WCF rejeitará a sequência oferecida respondendo com um `CreateSequenceResponse` sem um elemento `Accept`.

- B1110: se um Respondente de mensagens confiável rejeitar a sequência oferecida, o iniciador do WCF falhará na sequência estabelecida recentemente.

- B1111: se `CreateSequence` não contiver um elemento `Offer`, o respondente do WCF bidirecional rejeitará a sequência oferecida respondendo com uma falha `CreateSequenceRefused`.

- R1112: quando duas sequências de conversos são estabelecidas usando o mecanismo de `Offer`, a propriedade `[address]` da referência do ponto de extremidade `CreateSequenceResponse/Accept/AcksTo` deve corresponder ao URI de destino do byte de mensagem `CreateSequence` para byte.

- R1113: quando duas sequências de conversos são estabelecidas usando o mecanismo de `Offer`, todas as mensagens em ambas as sequências que fluem do iniciador para o respondente devem ser enviadas para a mesma referência de ponto de extremidade.

O WCF usa o WS-ReliableMessaging para estabelecer sessões confiáveis entre o iniciador e o respondente. A implementação do WS-ReliableMessaging do WCF fornece uma sessão confiável para os padrões unidirecional, resposta de solicitação e mensagens em full duplex. O mecanismo de `Offer` WS-ReliableMessaging em `CreateSequence` e `CreateSequenceResponse` permite que você estabeleça duas sequências de contraverso correlacionadas e fornece um protocolo de sessão adequado para todos os pontos de extremidade da mensagem. Como o WCF fornece uma garantia de segurança para tal sessão, incluindo proteção de ponta a ponta para integridade da sessão, é prático garantir que as mensagens destinadas à mesma parte cheguem ao mesmo destino. Isso também permite "transportado" de confirmações de sequência em mensagens de aplicativo. Portanto, as restrições R1102, R1112 e R1113 se aplicam ao WCF.

Um exemplo de uma mensagem de `CreateSequence`.

```xml
<s:Envelope>
  <s:Header>
    <wsa:Action s:mustUnderstand="1">http://docs.oasis-open.org/ws-rx/wsrm/200702/CreateSequence</wsa:Action>
    <wsa:MessageID>urn:uuid:949cca61-8813-42ff-ab33-18d9e3fa82fa</wsa:MessageID>
    <wsa:ReplyTo>
        <wsa:Address>http://Business456.com/clientA</wsa:Address>
    </wsa:ReplyTo>
    <wsa:To s:mustUnderstand="1">http://BusinessABC.com/serviceA</wsa:To>
  </s:Header>
  <s:Body>
    <wsrm:CreateSequence>
      <wsrm:AcksTo>
        <wsa:Address>http://Business456.com/clientA</wsa:Address>
      </wsrm:AcksTo>
      <wsrm:Offer>
        <wsrm:Identifier>urn:uuid:066b4730-fc82-458a-a5c1-210be4fb4e4e</wsrm:Identifier>
        <wsrm:Endpoint>
          <wsa:Address>http://Business456.com/clientA</wsa:Address>
        </wsrm:Endpoint>
        <wsrm:IncompleteSequenceBehavior>DiscardFollowingFirstGap</wsrm:IncompleteSequenceBehavior>
      </wsrm:Offer>
    </wsrm:CreateSequence>
  </s:Body>
</s:Envelope>
```

Um exemplo de uma mensagem de `CreateSequenceResponse`.

```xml
<s:Envelope>
  <s:Header>
    <wsa:Action s:mustUnderstand="1">http://docs.oasis-open.org/ws-rx/wsrm/200702/CreateSequenceResponse</wsa:Action>
    <wsa:RelatesTo>urn:uuid:949cca61-8813-42ff-ab33-18d9e3fa82fa</wsa:RelatesTo>
    <wsa:To s:mustUnderstand="1">http://Business456.com/clientA</wsa:To>
  </s:Header>
  <s:Body>
    <wsrm:CreateSequenceResponse>
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>
      <wsrm:IncompleteSequenceBehavior>DiscardFollowingFirstGap</wsrm:IncompleteSequenceBehavior>
      <wsrm:Accept>
        <wsrm:AcksTo>
          <wsa:Address>http://BusinessABC.com/serviceA</wsa:Address>
        </wsrm:AcksTo>
      </wsrm:Accept>
    </wsrm:CreateSequenceResponse>
  </s:Body>
</s:Envelope>
```

### <a name="closing-a-sequence"></a>Fechando uma sequência

O WCF usa as mensagens `CloseSequence` e `CloseSequenceResponse` para um desligamento iniciado pela fonte de mensagens confiáveis. O destino de mensagens confiáveis do WCF não inicia o desligamento e a fonte de mensagens confiáveis do WCF não dá suporte a um desligamento iniciado por destino de mensagens confiáveis. As seguintes restrições se aplicam:

- B1201: a fonte de mensagens confiáveis do WCF sempre envia uma mensagem de `CloseSequence` para desligar a sequência.

- B1202: a origem da mensagem confiável aguarda a confirmação do intervalo completo de mensagens de sequência antes de enviar a mensagem de `CloseSequence`.

- B1203: a fonte de mensagens confiáveis sempre inclui o elemento `LastMsgNumber` opcional, a menos que a sequência não contenha mensagens.

- R1204: o destino do sistema de mensagens confiável não deve iniciar o desligamento enviando uma mensagem de `CloseSequence`.

- B1205: após receber uma mensagem de `CloseSequence`, a origem de mensagens confiáveis do WCF considera a sequência incompleta e envia uma falha.

 Um exemplo de uma mensagem de `CloseSequence`.

```xml
<s:Envelope>
  <s:Header>
    <wsa:Action s:mustUnderstand="1">http://docs.oasis-open.org/ws-rx/wsrm/200702/CloseSequence</wsa:Action>
    <wsa:MessageID>urn:uuid:6ce1d4c3-e1c1-474f-a8c9-4210e37f7877</wsa:MessageID>
    <wsa:ReplyTo>
      <wsa:Address>http://Business456.com/clientA</wsa:Address>
    </wsa:ReplyTo>
    <wsa:To s:mustUnderstand="1">http://BusinessABC.com/serviceA</wsa:To>
  </s:Header>
  <s:Body>
    <wsrm:CloseSequence>
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>
      <wsrm:LastMsgNumber>30</wsrm:LastMsgNumber>
    </wsrm:CloseSequence>
  </s:Body>
</s:Envelope>
```

Exemplo de `CloseSequenceResponse` mensagem:

```xml
<s:Envelope>
  <s:Header>
    <wsrm:SequenceAcknowledgement>
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>
      <wsrm:AcknowledgementRange Lower="1" Upper="30"></wsrm:AcknowledgementRange>
      <wsrm:Final></wsrm:Final>
      <netrm:BufferRemaining>8</netrm:BufferRemaining>
    </wsrm:SequenceAcknowledgement>
    <wsa:Action s:mustUnderstand="1">http://docs.oasis-open.org/ws-rx/wsrm/200702/CloseSequenceResponse</wsa:Action>
    <wsa:RelatesTo>urn:uuid:6ce1d4c3-e1c1-474f-a8c9-4210e37f7877</wsa:RelatesTo>
    <wsa:To s:mustUnderstand="1">http://Business456.com/clientA</wsa:To>
  </s:Header>
  <s:Body>
    <wsrm:CloseSequenceResponse>
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>
    </wsrm:CloseSequenceResponse>
  </s:Body>
</s:Envelope>
```

### <a name="sequence-termination"></a>Terminação de sequência

O WCF usa principalmente o handshake de `TerminateSequence/TerminateSequenceResponse` depois de concluir o handshake de `CloseSequence/CloseSequenceResponse`. O destino de mensagens confiáveis do WCF não inicia o encerramento e a fonte de mensagens confiáveis não dá suporte a um encerramento iniciado pelo destino de mensagens confiáveis. As seguintes restrições se aplicam:

- B1301: o iniciador do WCF envia apenas a mensagem de `TerminateSequence` após a conclusão bem-sucedida do handshake de `CloseSequence/CloseSequenceResponse`.

- R1302: o WCF valida que o elemento `LastMsgNumber` é consistente em todas as `CloseSequence` e `TerminateSequence` mensagens para uma determinada sequência. Isso significa que `LastMsgNumber` não está presente em todas as mensagens de `CloseSequence` e `TerminateSequence`, ou está presente e é idêntica em todas as mensagens de `CloseSequence` e `TerminateSequence`.

- B1303: ao receber uma mensagem de `TerminateSequence` após o handshake de `CloseSequence/CloseSequenceResponse`, o destino do sistema de mensagens confiável responde com uma mensagem `TerminateSequenceResponse`. Como a fonte de mensagens confiáveis tem a confirmação final antes de enviar a mensagem de `TerminateSequence`, o destino da mensagem confiável sabe sem dúvida que a sequência termina e recupera recursos imediatamente.

- B1304: ao receber uma mensagem de `TerminateSequence` antes do handshake de `CloseSequence/CloseSequenceResponse`, o destino de mensagens confiáveis do WCF responde com uma mensagem de `TerminateSequenceResponse`. Se o destino da mensagem confiável determinar que não há inconsistências na sequência, o destino da mensagem confiável aguardará um tempo especificado de destino do aplicativo antes de recuperar os recursos, para permitir que o cliente receba a confirmação final. Caso contrário, o destino da mensagem confiável recupera recursos imediatamente e indica ao destino do aplicativo que a sequência termina com a dúvida ao gerar o evento `Faulted`.

Um exemplo de uma mensagem de `TerminateSequence`.

```xml
<s:Envelope>
  <s:Header>
    <wsa:Action s:mustUnderstand="1">http://docs.oasis-open.org/ws-rx/wsrm/200702/TerminateSequence</wsa:Action>
    <wsa:MessageID>urn:uuid:3597a398-4f3c-40f4-9335-8f1515572fdf</wsa:MessageID>
    <wsa:ReplyTo>
      <wsa:Address>http://Business456.com/clientA</wsa:Address>
    </wsa:ReplyTo>
    <wsa:To s:mustUnderstand="1">http://BusinessABC.com/serviceA</wsa:To>
  </s:Header>
  <s:Body>
    <wsrm:TerminateSequence>
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>
      <wsrm:LastMsgNumber>30</wsrm:LastMsgNumber>
      </wsrm:TerminateSequence>
  </s:Body>
</s:Envelope>
```

Exemplo de `TerminateSequenceResponse` mensagem:

```xml
<s:Envelope>
  <s:Header>
    <wsrm:SequenceAcknowledgement>
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>
      <wsrm:AcknowledgementRange Lower="1" Upper="30"></wsrm:AcknowledgementRange>
      <wsrm:Final></wsrm:Final>
      <netrm:BufferRemaining>8</netrm:BufferRemaining>
    </wsrm:SequenceAcknowledgement>
    <wsa:Action s:mustUnderstand="1">http://docs.oasis-open.org/ws-rx/wsrm/200702/TerminateSequenceResponse</wsa:Action>
    <wsa:RelatesTo>urn:uuid:3597a398-4f3c-40f4-9335-8f1515572fdf</wsa:RelatesTo>
    <wsa:To s:mustUnderstand="1">://Business456.com/clientA</wsa:To>
  </s:Header>
  <s:Body>
    <wsrm:TerminateSequenceResponse>
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>
    </wsrm:TerminateSequenceResponse>
  </s:Body>
</s:Envelope>
```

### <a name="sequences"></a>Sequências

Veja a seguir uma lista de restrições que se aplicam a sequências:

- B1401: o WCF gera e acessa números de sequência que não são maiores do que `xs:long`valor inclusivo máximo, 9223372036854775807.

Um exemplo de um cabeçalho de `Sequence`.

```xml
<wsrm:Sequence s:mustUnderstand="1">
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>
  <wsrm:MessageNumber>1</wsrm:MessageNumber>
</wsrm:Sequence>
```

### <a name="request-acknowledgement"></a>Confirmação de solicitação

O WCF usa o cabeçalho `AckRequested` como um mecanismo Keep-Alive.

Um exemplo de um cabeçalho de `AckRequested`.

```xml
<wsrm:AckRequested>
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>
</wsrm:AckRequested>
```

### <a name="sequenceacknowledgement"></a>SequenceAcknowledgement

O WCF usa um mecanismo de "transportado" para confirmações de sequência fornecidas em mensagens WS-Reliable. As seguintes restrições se aplicam:

- R1601: quando duas sequências de conversos são estabelecidas usando o mecanismo de `Offer`, o cabeçalho `SequenceAcknowledgement` pode ser incluído em qualquer mensagem de aplicativo transmitida para o destinatário pretendido. O ponto de extremidade remoto deve ser capaz de acessar um cabeçalho de `SequenceAcknowledgement` acumulado.

- B1602: o WCF não gera cabeçalhos de `SequenceAcknowledgement` que contêm elementos de `Nack`. O WCF valida que cada elemento de `Nack` contém um número de sequência, mas, caso contrário, ignora o elemento `Nack` e o valor.

 Um exemplo de um cabeçalho de `SequenceAcknowledgement`.

```xml
<wsrm:SequenceAcknowledgement>
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>
  <wsrm:AcknowledgementRange Lower="1" Upper="1"></wsrm:AcknowledgementRange>
</wsrm:SequenceAcknowledgement>
```

### <a name="ws-reliablemessaging-faults"></a>Falhas de WS-ReliableMessaging

Veja a seguir uma lista de restrições que se aplicam à implementação do WCF de falhas WS-ReliableMessaging. As seguintes restrições se aplicam:

- B1701: o WCF não gera `MessageNumberRollover` falhas.

- B1702: sobre SOAP 1,2, quando o ponto de extremidade de serviço atinge seu limite de conexão e não pode processar novas conexões, o WCF gera um subcódigo de falha de `CreateSequenceRefused` aninhado, `netrm:ConnectionLimitReached`, conforme mostrado no exemplo a seguir.

```xml
<s:Envelope>
  <s:Header>
    <wsa:Action>http://docs.oasis-open.org/ws-rx/wsrm/200702/fault</wsa:Action>
  </s:Header>
  <s:Body>
    <s:Fault>
      <s:Code>
        <s:Value>s:Receiver</s:Value>
        <s:Subcode>
          <s:Value>wsrm:CreateSequenceRefused</s:Value>
          <s:Subcode>
            <s:Value>netrm:ConnectionLimitReached</s:Value>
          </s:Subcode>
        </s:Subcode>
      </s:Code>
      <s:Reason>
        <s:Text xml:lang="en">Server 'http://BusinessABC.com/serviceA' is too busy to process this request. Try again later.</s:Text>
      </s:Reason>
    </s:Fault>
  </s:Body>
</s:Envelope>
```

### <a name="ws-addressing-faults"></a>Falhas no WS-Addressing

Como o WS-ReliableMessaging usa o WS-Addressing, a implementação do WS-ReliableMessaging do WCF pode gerar e transmitir falhas de WS-Addressing. Esta seção aborda as falhas do WS-Addressing que o WCF gera e transmite explicitamente na camada WS-ReliableMessaging:

- B1801: o WCF gera e transmite a falha de `Message Addressing Header Required` quando uma das seguintes opções é verdadeira:

  - Uma `CreateSequence`, `CloseSequence` ou `TerminateSequence` mensagem está sem um cabeçalho `MessageId`.

  - Uma `CreateSequence`, `CloseSequence` ou `TerminateSequence` mensagem está sem um cabeçalho `ReplyTo`.

  - Uma mensagem `CreateSequenceResponse`, `CloseSequenceResponse`ou `TerminateSequenceResponse` está sem um cabeçalho `RelatesTo`.

- B1802: o WCF gera e transmite a falha de `Endpoint Unavailable` para indicar que não há nenhum ponto de extremidade ouvindo que possa processar a sequência com base no exame dos cabeçalhos de endereçamento na mensagem de `CreateSequence`.

## <a name="protocol-composition"></a>Composição de protocolo

### <a name="composition-with-ws-addressing"></a>Composição com WS-Addressing

O WCF dá suporte a duas versões do WS-Addressing: WS-Addressing 2004/08 [WS-ADDR] e W3C WS-Addressing 1,0 Recommendations [WS-ADDR-CORE] e [WS-ADDR-SOAP].

Embora a especificação WS-ReliableMessaging mencione apenas o WS-Addressing 2004/08, ela não restringe a versão do WS-Addressing a ser usada. Veja a seguir uma lista de restrições que se aplicam ao WCF:

- R2101: o WS-Addressing 2004/08 e o WS-Addressing 1,0 podem ser usados com o sistema de mensagens WS-Reliable.

- R2102: uma única versão do WS-Addressing deve ser usada em uma determinada sequência WS-ReliableMessaging ou um par de sequências inversas correlacionadas usando o mecanismo de `Offer`.

### <a name="composition-with-soap"></a>Composição com SOAP

O WCF dá suporte ao uso de SOAP 1,1 e SOAP 1,2 com o sistema de mensagens WS-Reliable.

### <a name="composition-with-ws-security-and-ws-secureconversation"></a>Composição com WS-Security e WS-SecureConversation

O WCF fornece proteção para sequências WS-ReliableMessaging usando transporte seguro (HTTPS), composição com WS-Security e composição com a conversa WS-Secure. O protocolo WS-ReliableMessaging 1,1, o WS-Security 1,1 e o WS-Secure Conversation protocolo 1,3 devem ser usados juntos. Veja a seguir uma lista de restrições que se aplicam ao WCF:

- R2301: para proteger a integridade de uma sequência WS-ReliableMessaging, além da integridade e da confidencialidade de mensagens individuais, o WCF requer que a conversa WS-Secure deva ser usada.

- R2302: AWS-a sessão de conversa segura deve ser estabelecida antes de estabelecer a (s) sequência (ões) WS-ReliableMessaging.

- R2303: se o tempo de vida da sequência WS-ReliableMessaging exceder o tempo de vida da sessão de conversa do WS-Secure, o `SecurityContextToken` estabelecido usando a conversa WS-Secure deve ser renovado usando a associação de renovação de conversa WS-Secure correspondente.

- B2304: a sequência WS-ReliableMessaging ou um par de sequências correlacionadas correlatas são sempre associados a uma única sessão WS-SecureConversation.

- R2305: quando composto com a conversa do WS-Secure, o respondente do WCF requer que a mensagem de `CreateSequence` contenha o elemento `wsse:SecurityTokenReference` e o cabeçalho `wsrm:UsesSequenceSTR`.

 Um exemplo de um cabeçalho de `UsesSequenceSTR`.

```xml
<wsrm:UsesSequenceSTR></wsrm:UsesSequenceSTR>
```

### <a name="composition-with-ssltls-sessions"></a>Composição com sessões SSL/TLS

O WCF não dá suporte à composição com sessões SSL/TLS:

- B2401: o WCF não gera o cabeçalho `wsrm:UsesSequenceSSL`.

- R2402: um iniciador de mensagens confiável não deve enviar uma mensagem de `CreateSequence` com um cabeçalho de `wsrm:UsesSequenceSSL` para um respondente do WCF.

### <a name="composition-with-ws-policy"></a>Composição com WS-Policy

O WCF dá suporte a duas versões de WS-Policy: WS-Policy 1,2 e WS-Policy 1,5.

## <a name="ws-reliablemessaging-ws-policy-assertion"></a>Declaração de WS-Policy de WS-ReliableMessaging

O WCF usa o WS-ReliableMessaging declaração WS-Policy `wsrm:RMAssertion` para descrever os recursos de pontos de extremidade. Veja a seguir uma lista de restrições que se aplicam ao WCF:

- B3001: o WCF anexa `wsrmn:RMAssertion` declaração WS-Policy a elementos `wsdl:binding`. O WCF dá suporte a ambos os anexos aos elementos `wsdl:binding` e `wsdl:port`.

- B3002: o WCF nunca gera a marca de `wsp:Optional`.

- B3003: ao acessar a declaração de WS-Policy `wsrmp:RMAssertion`, o WCF ignora a marca de `wsp:Optional` e trata a política WS-RM como obrigatória.

- R3004: como o WCF não compõe as sessões SSL/TLS, o WCF não aceita a política que especifica `wsrmp:SequenceTransportSecurity`.

- B3005: o WCF sempre gera o elemento `wsrmp:DeliveryAssurance`.

- B3006: o WCF sempre especifica a garantia de entrega de `wsrmp:ExactlyOnce`.

- B3007: o WCF gera e lê as seguintes propriedades da declaração WS-ReliableMessaging e fornece controle sobre elas no`ReliableSessionBindingElement`do WCF:

  - `netrmp:InactivityTimeout`

  - `netrmp:AcknowledgementInterval`

  Um exemplo de um `RMAssertion`.

  ```xml
  <wsrmp:RMAssertion>
    <wsp:Policy>
      <wsrmp:SequenceSTR/>
      <wsrmp:DeliveryAssurance>
        <wsp:Policy>
          <wsrmp:ExactlyOnce/>
          <wsrmp:InOrder/>
        </wsp:Policy>
      </wsrmp:DeliveryAssurance>
    </wsp:Policy>
    <netrmp:InactivityTimeout Milliseconds="600000"/>
    <netrmp:AcknowledgementInterval Milliseconds="200"/>
  </wsrmp:RMAssertion>
  ```

## <a name="flow-control-ws-reliablemessaging-extension"></a>Extensão WS-ReliableMessaging de controle de fluxo

O WCF usa a extensibilidade WS-ReliableMessaging para fornecer um controle mais rígido adicional opcional sobre o fluxo de mensagens de sequência.

O controle de fluxo é habilitado definindo a propriedade <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.FlowControlEnabled?displayProperty=nameWithType> como `true`. Veja a seguir uma lista de restrições que se aplicam ao WCF:

- B4001: quando o controle de fluxo de mensagens confiável está habilitado, o WCF gera um elemento `netrm:BufferRemaining` na extensibilidade do elemento do cabeçalho `SequenceAcknowledgement`, conforme mostrado no exemplo a seguir.

  ```xml
  <wsrm:SequenceAcknowledgement>
    <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>
    <wsrm:AcknowledgementRange Upper="1" Lower="1"/>
    <netrm:BufferRemaining>8</netrm:BufferRemaining>
  </wsrm:SequenceAcknowledgement>
  ```

- B4002: mesmo quando o controle de fluxo de mensagens confiável está habilitado, o WCF não requer um elemento `netrm:BufferRemaining` no cabeçalho `SequenceAcknowledgement`.

- B4003: o destino do sistema de mensagens confiável do WCF usa `netrm:BufferRemaining` para indicar quantas novas mensagens ele pode armazenar em buffer.

- B4004: quando o controle de fluxo de mensagens confiável está habilitado, a fonte de mensagens confiáveis do WCF usa o valor de `netrm:BufferRemaining` para limitar a transmissão de mensagens.

- B4005: o WCF gera `netrm:BufferRemaining` valores inteiros entre 0 e 4096, inclusive, e lê os valores inteiros entre 0 e `xs:int``maxInclusive` valor 214748364, inclusive.

## <a name="message-exchange-patterns"></a>Padrões de troca de mensagens

Esta seção descreve o comportamento do WCF quando o WS-ReliableMessaging é usado para diferentes padrões de troca de mensagens. Para cada padrão de troca de mensagens, os seguintes dois cenários de implantações são considerados:

- Iniciador não endereçável: o iniciador está protegido por um firewall; O respondente pode entregar mensagens ao iniciador somente em respostas HTTP.

- Iniciador endereçável: o iniciador e o respondente podem ser enviados solicitações HTTP; em outras palavras, duas conexões HTTP de converso podem ser estabelecidas.

### <a name="one-way-non-addressable-initiator"></a>Iniciador unidirecional e não endereçável

#### <a name="binding"></a>Associação

O WCF fornece um padrão de troca de mensagens unidirecional usando uma sequência em um canal HTTP. O WCF usa solicitações HTTP para transmitir todas as mensagens do iniciador para o respondente e respostas HTTP para transmitir todas as mensagens do Respondente para o iniciador.

#### <a name="createsequence-exchange"></a>Exchange CreateSequence

O iniciador do WCF transmite uma mensagem de `CreateSequence` sem elemento `Offer` em uma solicitação HTTP e espera a mensagem de `CreateSequenceResponse` na resposta HTTP. O respondente do WCF cria uma sequência e transmite a mensagem de `CreateSequenceResponse` sem elemento `Accept` na resposta HTTP.

#### <a name="sequenceacknowledgement"></a>SequenceAcknowledgement

O iniciador do WCF processa confirmações na resposta de todas as mensagens, exceto a mensagem de `CreateSequence` e mensagens de falha. O respondente do WCF sempre transmite uma confirmação autônoma na resposta HTTP para todas as mensagens de sequência e `AckRequested`.

#### <a name="closesequence-exchange"></a>CloseSequence Exchange

O iniciador do WCF transmite uma mensagem de `CloseSequence` em uma solicitação HTTP e espera a mensagem de `CreateSequenceResponse` na resposta HTTP. O respondente do WCF transmite a mensagem de `CloseSequenceResponse` na resposta HTTP.

#### <a name="terminatesequence-exchange"></a>Troca de TerminateSequence

O iniciador do WCF transmite uma mensagem de `TerminateSequence` em uma solicitação HTTP e espera a mensagem de `TerminateSequenceResponse` na resposta HTTP. O respondente do WCF transmite a mensagem de `TerminateSequenceResponse` na resposta HTTP.

### <a name="one-way-addressable-initiator"></a>Iniciador endereçável unidirecional

#### <a name="binding"></a>Associação

O WCF fornece um padrão de troca de mensagens unidirecional usando uma sequência em um canal HTTP de entrada e um de saída. O WCF usa as solicitações HTTP para transmitir todas as mensagens. Todas as respostas HTTP têm um corpo vazio e um código de status HTTP 202.

#### <a name="createsequence-exchange"></a>Exchange CreateSequence

O iniciador do WCF transmite uma mensagem de `CreateSequence` sem elemento `Offer` em uma solicitação HTTP. O respondente do WCF cria uma sequência e transmite a mensagem de `CreateSequenceResponse` sem elemento `Accept` em uma solicitação HTTP.

### <a name="duplex-addressable-initiator"></a>Iniciador duplex, endereçável

#### <a name="binding"></a>Associação

O WCF fornece um padrão de troca de mensagens bidirecional, totalmente assíncrono, usando duas sequências em um canal HTTP de entrada e um de saída. Esse padrão de troca de mensagens pode ser misturado com o `Request/Reply`, `Addressable` padrão de troca de mensagens do iniciador de uma maneira limitada. O WCF usa solicitações HTTP para transmitir todas as mensagens. Todas as respostas HTTP têm um corpo vazio e um código de status HTTP 202.

#### <a name="createsequence-exchange"></a>Exchange CreateSequence

O iniciador do WCF transmite uma mensagem de `CreateSequence` com um elemento `Offer` em uma solicitação HTTP. O respondente do WCF garante que o `CreateSequence` tenha um elemento `Offer` e, em seguida, crie uma sequência e transmita a mensagem `CreateSequenceResponse` com um elemento `Accept`.

#### <a name="sequence-lifetime"></a>Tempo de vida da sequência

O WCF trata as duas sequências como uma sessão totalmente duplex.

Ao gerar uma falha que apresenta uma sequência, o WCF espera que o ponto de extremidade remoto tenha uma falha nas duas sequências. Após a leitura de uma falha que falha em uma sequência, o WCF falha em ambas as sequências.

O WCF pode fechar sua sequência de saída e continuar a processar mensagens em sua sequência de entrada. Por outro lado, o WCF pode processar o fechamento da sequência de entrada e continuar a enviar mensagens em sua sequência de saída.

### <a name="request-reply-and-one-way-non-addressable-initiator"></a>Solicitação-resposta e iniciador unidirecional, não endereçável

#### <a name="binding"></a>Associação

O WCF fornece um padrão de troca de mensagens unidirecional e de solicitação-resposta usando duas sequências em um canal HTTP. O WCF usa solicitações HTTP para transmitir todas as mensagens do iniciador para o respondente e respostas HTTP para transmitir todas as mensagens do Respondente para o iniciador.

#### <a name="createsequence-exchange"></a>Exchange CreateSequence

O iniciador do WCF transmite uma mensagem de `CreateSequence` com um elemento `Offer` em uma solicitação HTTP e espera a mensagem de `CreateSequenceResponse` na resposta HTTP. O respondente do WCF cria uma sequência e transmite a mensagem de `CreateSequenceResponse` com um elemento `Accept` na resposta HTTP.

#### <a name="one-way-message"></a>Mensagem unidirecional

Para concluir uma troca de mensagens unidirecional com êxito, o iniciador do WCF transmite uma mensagem de sequência de solicitação na solicitação HTTP e recebe uma mensagem `SequenceAcknowledgement` autônoma na resposta HTTP. O `SequenceAcknowledgement` deve reconhecer a mensagem transmitida.

O respondente do WCF pode responder à solicitação com uma confirmação, uma falha ou uma resposta com um corpo vazio e um código de status HTTP 202.

#### <a name="two-way-messages"></a>Mensagens de duas vias

Para concluir com êxito um protocolo de troca de mensagens de duas vias, o iniciador do WCF transmite uma mensagem de sequência de solicitação na solicitação HTTP e recebe uma mensagem de sequência de resposta na resposta HTTP. A resposta deve transportar um `SequenceAcknowledgement` confirmando a mensagem de sequência de solicitação transmitida.

O respondente do WCF pode responder à solicitação com uma resposta do aplicativo, uma falha ou uma resposta com um corpo vazio e um código de status HTTP 202.

Devido à presença de mensagens unidirecionais e do tempo das respostas do aplicativo, o número de sequência da mensagem da sequência de solicitação e o número de sequência da mensagem de resposta não têm nenhuma correlação.

#### <a name="retrying-replies"></a>Repetindo respostas

O WCF conta com correlação de solicitação-resposta HTTP para correlação de protocolo de troca de mensagens bidirecional. Por isso, o iniciador do WCF não pára de repetir uma mensagem de sequência de solicitação quando a mensagem de sequência de solicitação é confirmada, mas quando a resposta HTTP carrega um `SequenceAcknowledgement`, uma resposta de aplicativo ou uma falha. O respondente do WCF tenta respostas novamente na resposta HTTP da solicitação à qual a resposta está correlacionada.

#### <a name="closesequence-exchange"></a>CloseSequence Exchange

Depois de receber todas as mensagens de sequência de resposta e confirmações de todas as mensagens de sequência de solicitação de uma única maneira, o iniciador do WCF transmite uma mensagem de `CloseSequence` para a sequência de solicitação em uma solicitação HTTP e espera a `CloseSequenceResponse` na resposta HTTP.

Fechar a sequência de solicitação fecha implicitamente a sequência de resposta. Isso significa que o iniciador do WCF inclui a `SequenceAcknowledgement` final da sequência de respostas na mensagem de `CloseSequence` e a sequência de resposta não tem um `CloseSequence` Exchange.

O respondente do WCF garante que todas as respostas sejam confirmadas e transmite a mensagem de `CloseSequenceResponse` na resposta HTTP.

#### <a name="terminatesequence-exchange"></a>Troca de TerminateSequence

Depois de receber a mensagem de `CloseSequenceResponse`, o iniciador do WCF transmite uma mensagem de `TerminateSequence` para a sequência de solicitação em uma solicitação HTTP e espera a `TerminateSequenceResponse` na resposta HTTP.

Como o `CloseSequence` Exchange, encerrar a sequência de solicitação encerra implicitamente a sequência de resposta. Isso significa que o iniciador do WCF inclui a `SequenceAcknowledgement` final da sequência de respostas na mensagem de `TerminateSequence` e a sequência de resposta não tem um `TerminateSequence` Exchange.

O respondente do WCF transmite a mensagem de `TerminateSequenceResponse` na resposta HTTP.

### <a name="requestreply-addressable-initiator"></a>Solicitação/resposta, iniciador endereçável

#### <a name="binding"></a>Associação

O WCF fornece um padrão de troca de mensagens de solicitação-resposta usando duas sequências em um canal HTTP de entrada e um de saída. Esse padrão de troca de mensagens pode ser misturado com o padrão de troca de mensagens do iniciador `Duplex, Addressable` de forma limitada. O WCF usa as solicitações HTTP para transmitir todas as mensagens. Todas as respostas HTTP têm um corpo vazio e um código de status HTTP 202.

#### <a name="createsequence-exchange"></a>Exchange CreateSequence

O iniciador do WCF transmite uma mensagem de `CreateSequence` com um elemento `Offer` em uma solicitação HTTP. O respondente do WCF garante que o `CreateSequence` tenha um elemento `Offer`, em seguida, crie uma sequência e transmita a mensagem `CreateSequenceResponse` com um elemento `Accept`.

#### <a name="requestreply-correlation"></a>Correlação de solicitação/resposta

O seguinte se aplica a todas as solicitações e respostas correlacionadas:

- O WCF garante que todas as mensagens de solicitação de aplicativo tenham uma referência de ponto de extremidade `ReplyTo` e uma `MessageId`.

- O WCF aplica a referência de ponto de extremidade local à medida que cada mensagem de solicitação de aplicativo `ReplyTo`. A referência do ponto de extremidade local é a `ReplyTo` da `CreateSequence` da mensagem para o iniciador e a `To` da mensagem do `CreateSequence` para o respondente.

- O WCF garante que as mensagens de solicitação de entrada tenham uma `MessageId` e uma `ReplyTo`.

- O WCF garante que o URI de referência de ponto de extremidade `ReplyTo` de todas as mensagens de solicitação de aplicativo corresponda à referência de ponto de extremidade local conforme definido anteriormente.

- O WCF garante que todas as respostas contenham os cabeçalhos corretos de `RelatesTo` e de `To` seguintes `wsa` regras de correlação de solicitação/resposta.
