---
title: Protocolo de mensagem confiável versão 1.1
ms.date: 03/30/2017
ms.assetid: 0da47b82-f8eb-42da-8bfe-e56ce7ba6f59
ms.openlocfilehash: 349c4dec8f127640d2709abcd63295aace6826df
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64754110"
---
# <a name="reliable-messaging-protocol-version-11"></a>Protocolo de mensagem confiável versão 1.1

Este tópico abrange detalhes de implementação do Windows Communication Foundation (WCF) para o WS-ReliableMessaging necessárias para usar o transporte HTTP de interoperação de protocolo de fevereiro de 2007 (versão 1.1). WCF segue a especificação de WS-ReliableMessaging com as restrições e esclarecimentos explicados neste tópico. Observe que o protocolo de versão 1.1 WS-ReliableMessaging é implementado começando com o [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)].

O WS-ReliableMessaging de fevereiro de 2007 protocolo é implementado no WCF, o <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>.

Para sua conveniência, o tópico usa as seguintes funções:

- Iniciador: O cliente que inicia a criação da sequência de mensagens WS-Reliable.

- Respondente: O serviço que recebe solicitações do iniciador.

 Este documento usa os prefixos e namespaces na tabela a seguir.

|Prefixo|Namespace|
|-|-|
|wsrm|http://docs.oasis-open.org/ws-rx/wsrm/200702|
|netrm|http://schemas.microsoft.com/ws/2006/05/rm|
|s|http://www.w3.org/2003/05/soap-envelope|
|wsa|http://schemas.xmlsoap.org/ws/2005/08/addressing|
|wsse|http://docs.oasis-open.org/wss/2004/01/oasis-200401-wssecurity-secext-1.0.xsd|
|wsrmp|http://docs.oasis-open.org/ws-rx/wsrmp/200702|
|netrmp|http://schemas.microsoft.com/ws-rx/wsrmp/200702|
|wsp|(WS-Policy 1.2 ou WS-Policy 1.5)|

## <a name="messaging"></a>Mensagens

### <a name="sequence-creation"></a>Criação da sequência

O WCF implementa `CreateSequence` e `CreateSequenceResponse` mensagens para estabelecer um sistema de mensagens confiável de sequência. As seguintes restrições se aplicam:

- B1101: O iniciador do WCF usa a mesma referência de ponto de extremidade como o `CreateSequence` da mensagem `ReplyTo`, `AcksTo` e `Offer/Endpoint`.

- R1102: O `AcksTo`, `ReplyTo` e `Offer/Endpoint` referências de ponto de extremidade no `CreateSequence` mensagem deve ter valores de endereço com representações de cadeia de caracteres idêntica, de modo que eles correspondam a octet-wise.

  - O WCF respondente verifica se a parte do URI de `AcksTo`, `ReplyTo` e `Endpoint` referências de ponto de extremidade são idênticas antes de criar uma sequência.

- R1103: O `AcksTo`, `ReplyTo` e `Offer/Endpoint` referências de ponto de extremidade no `CreateSequence` mensagem deve ter o mesmo conjunto de parâmetros de referência.

  - WCF não impõe, mas presume que fazem referência parâmetros do `AcksTo`, `ReplyTo` e `Offer/Endpoint` ponto de extremidade faz referência na `CreateSequence` são idênticos e usa os parâmetros de referência do `ReplyTo` referência de ponto de extremidade para as confirmações e mensagens de sequência inverso.

- B1104: O iniciador do WCF não gera opcional `Expires` ou `Offer/Expires` elemento o `CreateSequence` mensagem.

- B1105: Ao acessar o `CreateSequence` mensagem, o respondente do WCF usa o `Expires` valor na `CreateSequence` elemento como o `Expires` valor no `CreateSequenceResponse` elemento. Caso contrário, o Respondente WCF lê e ignora a `Expires` e `Offer/Expires` valores.

- B1106: Ao acessar o `CreateSequenceResponse` mensagem, o iniciador do WCF lê opcional `Expires` valor, mas não usá-lo.

- B1107: O iniciador do WCF e o Respondente sempre geram opcional `IncompleteSequenceBehavior` elemento na `CreateSequence/Offer` e `CreateSequenceResponse` elementos.

- B1108: O WCF usa apenas o `DiscardFollowingFirstGap` e `NoDiscard` os valores no `IncompleteSequenceBehavior` elemento.

  - WS-ReliableMessaging utiliza o `Offer` mecanismo para estabelecer os dois conversam correlacionadas sequências que formam uma sessão.

- B1109: Se `CreateSequence` contém uma `Offer` elemento, o Respondente unidirecional de WCF rejeita a sequência oferecida por responder com um `CreateSequenceResponse` sem um `Accept` elemento.

- B1110: Se um Respondente de mensagens confiável rejeita a sequência oferecida, o iniciador do WCF falha em sequência recentemente estabelecida.

- B1111: Se `CreateSequence` não contém um `Offer` elemento, o Respondente bidirecional de WCF rejeita a sequência oferecida por responder com um `CreateSequenceRefused` falha.

- R1112: Quando duas sequências inverso são estabelecidas usando o `Offer` mecanismo, o `[address]` propriedade da `CreateSequenceResponse/Accept/AcksTo` referência de ponto de extremidade deve coincidir com o URI de destino do `CreateSequence` byte de mensagem por byte.

- R1113: Quando duas sequências inverso são estabelecidas usando o `Offer` mecanismo, todas as mensagens em ambas as sequências que fluem do iniciador para o Respondente devem ser enviadas para a mesma referência de ponto de extremidade.

O WCF usa WS-ReliableMessaging para estabelecer sessões confiáveis entre o iniciador e o respondente. A implementação de WCF WS-ReliableMessaging fornece uma sessão confiável para unidirecional, solicitação-resposta e full duplex padrões de mensagens. O WS-ReliableMessaging `Offer` mecanismo `CreateSequence` e `CreateSequenceResponse` permite que você estabeleça inverso correlacionados duas sequências e fornece um protocolo de sessão que é adequado para todos os pontos de extremidade de mensagem. Como o WCF fornece uma garantia de segurança para essa sessão, incluindo a proteção de ponta a ponta para integridade de sessão, é prático garantir que as mensagens destinadas a mesma parte chegam ao mesmo destino. Isso também permite "aproveitando" de confirmações de sequência em mensagens do aplicativo. Portanto, R1102, R1112 e R1113 de restrições se aplicam ao WCF.

Um exemplo de um `CreateSequence` mensagem.

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

Um exemplo de um `CreateSequenceResponse` mensagem.

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

### <a name="closing-a-sequence"></a>Uma sequência de fechamento

O WCF usa o `CloseSequence` e `CloseSequenceResponse` mensagens para um sistema de mensagens confiável desligamento iniciada pela origem. O destino de sistema de mensagens confiável do WCF não iniciam o desligamento e a fonte de sistema de mensagens confiável do WCF não oferece suporte a um desligamento iniciado pelo destino mensagens confiáveis. As seguintes restrições se aplicam:

- B1201: A fonte de sistema de mensagens confiável do WCF sempre envia um `CloseSequence` mensagem para desligar a sequência.

- B1202: A fonte de sistema de mensagens confiável aguarda a confirmação de toda a série de mensagens de sequência antes de enviar o `CloseSequence` mensagem.

- B1203: A fonte de sistema de mensagens confiável sempre inclui opcional `LastMsgNumber` elemento, a menos que a sequência não contém mensagens.

- R1204: O destino de sistema de mensagens confiável não deve iniciar o desligamento, enviando um `CloseSequence` mensagem.

- B1205: Ao receber um `CloseSequence` mensagem, a fonte de sistema de mensagens confiável do WCF considera a sequência incompleta e envia uma falha.

 Um exemplo de um `CloseSequence` mensagem.

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

Exemplo `CloseSequenceResponse` mensagem:

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

### <a name="sequence-termination"></a>Sequência de terminação

O WCF usa principalmente o `TerminateSequence/TerminateSequenceResponse` handshake depois de concluir o `CloseSequence/CloseSequenceResponse` handshake. O destino de sistema de mensagens confiável do WCF não inicie o encerramento e a fonte de sistema de mensagens confiável não oferece suporte a um encerramento confiável de mensagens iniciado pelo destino. As seguintes restrições se aplicam:

- B1301: O iniciador do WCF envia apenas o `TerminateSequence` mensagem após a conclusão bem-sucedida do `CloseSequence/CloseSequenceResponse` handshake.

- R1302: WCF valida que o `LastMsgNumber` elemento é consistente em todos os `CloseSequence` e `TerminateSequence` mensagens para uma determinada sequência. Isso significa que `LastMsgNumber` não está presente em todos os `CloseSequence` e `TerminateSequence` mensagens, ou ele está presente e idênticos em todos os `CloseSequence` e `TerminateSequence` mensagens.

- B1303: Ao receber um `TerminateSequence` da mensagem após o `CloseSequence/CloseSequenceResponse` handshake, o destino de sistema de mensagens confiável responde com um `TerminateSequenceResponse` mensagem. Como a origem do sistema de mensagens confiável tem a confirmação final antes de enviar o `TerminateSequence` mensagem, o destino de sistema de mensagens confiável sabe sem dúvida que a sequência termina e recupera os recursos imediatamente.

- B1304: Ao receber um `TerminateSequence` da mensagem antes do `CloseSequence/CloseSequenceResponse` handshake, o destino de sistema de mensagens confiável do WCF responde com um `TerminateSequenceResponse` mensagem. Se o destino de sistema de mensagens confiável determina que não há nenhuma inconsistência na sequência, o destino de sistema de mensagens confiável aguarda uma hora especificada pelo destino do aplicativo antes da recuperação de recursos, para permitir que o cliente a oportunidade de receber a confirmação final. Caso contrário, o destino de sistema de mensagens confiável recupera recursos imediatamente e indica para o destino do aplicativo que a sequência termina com caso de dúvida, gerando o `Faulted` eventos.

Um exemplo de um `TerminateSequence` mensagem.

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

Exemplo `TerminateSequenceResponse` mensagem:

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

A seguir está uma lista de restrições que se aplicam a sequências:

- Gera B1401:WCF e maior do que de números de sequência de acessos `xs:long`do valor máximo inclusivo, 9223372036854775807.

Um exemplo de um `Sequence` cabeçalho.

```xml
<wsrm:Sequence s:mustUnderstand="1">
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>
  <wsrm:MessageNumber>1</wsrm:MessageNumber>
</wsrm:Sequence>
```

### <a name="request-acknowledgement"></a>Solicitação de confirmação

O WCF usa o `AckRequested` cabeçalho como um mecanismo keep-alive.

Um exemplo de um `AckRequested` cabeçalho.

```xml
<wsrm:AckRequested>
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>
</wsrm:AckRequested>
```

### <a name="sequenceacknowledgement"></a>SequenceAcknowledgement

O WCF usa um mecanismo de "back transporte" para confirmações de sequência fornecidas no sistema de mensagens WS-Reliable. As seguintes restrições se aplicam:

- R1601: Quando duas sequências inverso são estabelecidas usando o `Offer` mecanismo, o `SequenceAcknowledgement` cabeçalho pode ser incluído em qualquer mensagem de aplicativo transmitida ao destinatário pretendido. O ponto de extremidade remoto deve ser capaz de acessar um acumuladas `SequenceAcknowledgement` cabeçalho.

- B1602: O WCF não gera `SequenceAcknowledgement` que contêm cabeçalhos `Nack` elementos. WCF valida que cada `Nack` elemento contém um número de sequência, mas caso contrário, ignora o `Nack` elemento e valor.

 Um exemplo de um `SequenceAcknowledgement` cabeçalho.

```xml
<wsrm:SequenceAcknowledgement>
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>
  <wsrm:AcknowledgementRange Lower="1" Upper="1"></wsrm:AcknowledgementRange>
</wsrm:SequenceAcknowledgement>
```

### <a name="ws-reliablemessaging-faults"></a>Falhas de WS-ReliableMessaging

O exemplo a seguir é uma lista de restrições que se aplicam a implementação do WCF de WS-ReliableMessaging falhas. As seguintes restrições se aplicam:

- B1701: O WCF não gera `MessageNumberRollover` falhas.

- B1702: Ao longo de SOAP 1.2, quando o ponto de extremidade do serviço atinge seu limite de conexão e não pode processar novas conexões, o WCF gera aninhado `CreateSequenceRefused` subcódigo, de falha `netrm:ConnectionLimitReached`, conforme mostrado no exemplo a seguir.

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

### <a name="ws-addressing-faults"></a>Falhas de WS-Addressing.

Como WS-ReliableMessaging usa WS-Addressing, a implementação de WCF WS-ReliableMessaging pode gerar e WS-Addressing falhas de transmissão. Esta seção aborda as falhas de WS-Addressing que o WCF gera e transmite na camada de WS-ReliableMessaging explicitamente:

- B1801:WCF gera e transmite o `Message Addressing Header Required` falha quando uma das seguintes opções for verdadeira:

  - Um `CreateSequence`, `CloseSequence` ou `TerminateSequence` mensagem está falta um `MessageId` cabeçalho.

  - Um `CreateSequence`, `CloseSequence` ou `TerminateSequence` mensagem está falta um `ReplyTo` cabeçalho.

  - Um `CreateSequenceResponse`, `CloseSequenceResponse`, ou `TerminateSequenceResponse` mensagem está falta um `RelatesTo` cabeçalho.

- B1802:WCF gera e transmite a `Endpoint Unavailable` falha para indicar que não há nenhum ponto de extremidade que pode processar a sequência com base no exame dos cabeçalhos de endereçamento no `CreateSequence` mensagem.

## <a name="protocol-composition"></a>Composição de protocolo

### <a name="composition-with-ws-addressing"></a>Composição com o WS-Addressing.

O WCF oferece suporte a duas versões do WS-Addressing: 2004 de WS-Addressing/08 [WS-ADDR] e W3C WS-Addressing 1.0 recomendações [WS-ADDR-CORE] e [WS-ADDR SOAP].

Enquanto as menções de especificação WS-ReliableMessaging 08/somente 2004 de WS-Addressing, ele não restringe a versão de WS-Addressing a ser usado. A seguir está uma lista de restrições que se aplicam ao WCF:

- R2101: 08/2004 de WS-Addressing e WS-Addressing 1.0 podem ser usado com o WS-Reliable Messaging.

- R2102: Uma única versão do WS-Addressing deve ser usada ao longo de uma determinada sequência WS-ReliableMessaging ou um par de sequências inverso correlacionados usando o `Offer` mecanismo.

### <a name="composition-with-soap"></a>Composição com SOAP

O WCF oferece suporte ao uso de SOAP 1.1 e SOAP 1.2 com o WS-Reliable Messaging.

### <a name="composition-with-ws-security-and-ws-secureconversation"></a>Composição com o WS-Security e WS-SecureConversation

O WCF fornece proteção para WS-ReliableMessaging sequências com o uso seguro de transporte (HTTPS), composição com o WS-Security e composição com o WS-Secure Conversation. O protocolo WS-ReliableMessaging 1.1, WS-Security 1.1 e o protocolo WS-Secure Conversation 1.3 devem ser usados juntos. A seguir está uma lista de restrições que se aplicam ao WCF:

- R2301: Para proteger a integridade de uma sequência de WS-ReliableMessaging, além da integridade e a confidencialidade das mensagens individuais, o WCF exige que o WS-Secure Conversation deve ser usada.

- R2302:AWS-Secure Conversation deve ser estabelecida antes de estabelecer a sequência de WS-ReliableMessaging.

- R2303: Se o tempo de vida de sequência WS-ReliableMessaging exceder o WS-Secure Conversation tempo de vida da sessão, o `SecurityContextToken` estabelecida usando WS-Secure Conversation devem ser renovada por meio de associação de WS-Secure Conversation renovação correspondente.

- B2304:WS-ReliableMessaging sequência ou um par de sequências inverso correlacionados sempre são associados a uma única sessão do WS-SecureConversation.

- R2305: Quando composto com o WS-Secure Conversation, o Respondente WCF requer que o `CreateSequence` a mensagem contém o `wsse:SecurityTokenReference` elemento e o `wsrm:UsesSequenceSTR` cabeçalho.

 Um exemplo de um `UsesSequenceSTR` cabeçalho.

```xml
<wsrm:UsesSequenceSTR></wsrm:UsesSequenceSTR>
```

### <a name="composition-with-ssltls-sessions"></a>Composição com sessões SSL/TLS

O WCF não oferece suporte a composição com sessões SSL/TLS:

- B2401: O WCF não gera o `wsrm:UsesSequenceSSL` cabeçalho.

- R2402: Um iniciador de mensagens confiável não deve enviar uma `CreateSequence` da mensagem com um `wsrm:UsesSequenceSSL` cabeçalho para um respondente do WCF.

### <a name="composition-with-ws-policy"></a>Composição com o WS-Policy

O WCF oferece suporte a duas versões do WS-Policy: 1.2 do WS-Policy e WS-Policy 1.5.

## <a name="ws-reliablemessaging-ws-policy-assertion"></a>WS-ReliableMessaging WS-Policy Assertion

O WCF usa a asserção de WS-Policy WS-ReliableMessaging `wsrm:RMAssertion` para descrever os recursos de pontos de extremidade. A seguir está uma lista de restrições que se aplicam ao WCF:

- B3001: O WCF anexa `wsrmn:RMAssertion` declaração de política WS para `wsdl:binding` elementos. O WCF oferece suporte a ambos os anexos `wsdl:binding` e `wsdl:port` elementos.

- B3002: O WCF nunca gera o `wsp:Optional` marca.

- B3003: Ao acessar o `wsrmp:RMAssertion` WCF de asserção de WS-Policy, ignora o `wsp:Optional` de marca e trata a política WS-RM como obrigatórias.

- R3004: Porque o WCF não compõe com sessões SSL/TLS, o WCF não aceita a política que especifica `wsrmp:SequenceTransportSecurity`.

- B3005: O WCF sempre gera o `wsrmp:DeliveryAssurance` elemento.

- B3006: O WCF sempre Especifica o `wsrmp:ExactlyOnce` garantia de entrega.

- B3007: WCF gera e lê as propriedades a seguir da asserção WS-ReliableMessaging e fornece controle sobre eles em WCF`ReliableSessionBindingElement`:

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

## <a name="flow-control-ws-reliablemessaging-extension"></a>Extensão de WS-ReliableMessaging do fluxo de controle

O WCF usa WS-ReliableMessaging extensibilidade para proporcionar um controle adicional opcional sobre o fluxo de mensagem de sequência.

Controle de fluxo é habilitado definindo o <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.FlowControlEnabled?displayProperty=nameWithType> propriedade para `true`. A seguir está uma lista de restrições que se aplicam ao WCF:

- B4001: Quando confiável fluxo de controle de mensagens está habilitado, o WCF gera uma `netrm:BufferRemaining` elemento de extensibilidade do elemento a `SequenceAcknowledgement` cabeçalho, conforme mostrado no exemplo a seguir.

  ```xml
  <wsrm:SequenceAcknowledgement>
    <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>
    <wsrm:AcknowledgementRange Upper="1" Lower="1"/>
    <netrm:BufferRemaining>8</netrm:BufferRemaining>
  </wsrm:SequenceAcknowledgement>
  ```

- B4002: Mesmo quando o sistema de mensagens confiável fluxo de controle é habilitado, o WCF não exige uma `netrm:BufferRemaining` elemento no `SequenceAcknowledgement` cabeçalho.

- B4003: Destino de sistema de mensagens confiável WCF usa `netrm:BufferRemaining` indicar quantas novas mensagens ele pode armazenar em buffer.

- B4004:when Reliable Messaging fluxo de controle está habilitado, a fonte de sistema de mensagens confiável WCF usa o valor de `netrm:BufferRemaining` para transmissão de mensagens de limitação.

- B4005: O WCF gera `netrm:BufferRemaining` inteiro de valores entre 0 e 4096 inclusivo e lê os valores de número inteiro entre 0 e `xs:int`do `maxInclusive` 214748364 inclusivo de valor.

## <a name="message-exchange-patterns"></a>Padrões de troca de mensagem

Esta seção descreve o comportamento do WCF quando WS-ReliableMessaging é usado para diferentes padrões de troca de mensagem. Para cada padrão de troca de mensagem, os seguintes cenários de duas implantações são considerados:

- Não endereçável iniciador: Iniciador estiver atrás de um firewall. Respondente pode enviar mensagens para o iniciador apenas em respostas HTTP.

- Iniciador endereçável: Iniciador e Respondente podem receber solicitações HTTP; em outras palavras, as duas conexões de HTTP inverso podem ser estabelecidas.

### <a name="one-way-non-addressable-initiator"></a>Iniciador unidirecional, não endereçável

#### <a name="binding"></a>Associação

O WCF fornece um padrão de troca de mensagens unidirecional usando uma sequência em um canal HTTP. O WCF usa solicitações HTTP para transmitir todas as mensagens do iniciador para as respostas HTTP e o respondente para transmitir todas as mensagens do respondedor para o iniciador.

#### <a name="createsequence-exchange"></a>Exchange CreateSequence

O iniciador do WCF transmite uma `CreateSequence` mensagem sem nenhum `Offer` elemento em uma solicitação HTTP e espera que o `CreateSequenceResponse` mensagem de resposta HTTP. O Respondente WCF cria uma sequência e transmite a `CreateSequenceResponse` mensagem sem nenhum `Accept` elemento na resposta HTTP.

#### <a name="sequenceacknowledgement"></a>SequenceAcknowledgement

O iniciador do WCF processa as confirmações na resposta de todas as mensagens, exceto o `CreateSequence` mensagem e mensagens de falha. O Respondente WCF sempre transmite uma confirmação autônoma na resposta HTTP a sequência de todas as e `AckRequested` mensagens.

#### <a name="closesequence-exchange"></a>Exchange CreateSequence

O iniciador do WCF transmite uma `CloseSequence` da mensagem em uma solicitação HTTP e espera que o `CreateSequenceResponse` mensagem de resposta HTTP. O Respondente WCF transmite o `CloseSequenceResponse` mensagem de resposta HTTP.

#### <a name="terminatesequence-exchange"></a>Exchange TerminateSequence

O iniciador do WCF transmite uma `TerminateSequence` da mensagem em uma solicitação HTTP e espera que o `TerminateSequenceResponse` mensagem de resposta HTTP. O Respondente WCF transmite o `TerminateSequenceResponse` mensagem de resposta HTTP.

### <a name="one-way-addressable-initiator"></a>Iniciador de uma forma, endereçável

#### <a name="binding"></a>Associação

O WCF fornece um padrão de troca de mensagens unidirecional usando uma sequência sobre uma entrada e um canal HTTP de saída. O WCF usa as solicitações HTTP para transmitir todas as mensagens. Todas as respostas HTTP tem um corpo vazio e o código de status HTTP 202.

#### <a name="createsequence-exchange"></a>Exchange CreateSequence

O iniciador do WCF transmite uma `CreateSequence` mensagem sem nenhum `Offer` elemento em uma solicitação HTTP. O Respondente WCF cria uma sequência e transmite a `CreateSequenceResponse` mensagem sem nenhum `Accept` elemento em uma solicitação HTTP.

### <a name="duplex-addressable-initiator"></a>Iniciador de duplex e endereçável

#### <a name="binding"></a>Associação

O WCF fornece um padrão de troca de mensagem assíncrona totalmente bidirecional usando duas sequências sobre uma entrada e um canal HTTP de saída. Esse padrão de troca de mensagem pode ser combinado com o `Request/Reply`, `Addressable` padrão de troca de mensagem do iniciador de uma maneira limitada. O WCF usa solicitações HTTP para transmitir todas as mensagens. Todas as respostas HTTP tem um corpo vazio e o código de status HTTP 202.

#### <a name="createsequence-exchange"></a>Exchange CreateSequence

O iniciador do WCF transmite uma `CreateSequence` da mensagem com um `Offer` elemento em uma solicitação HTTP. O Respondente WCF garante que o `CreateSequence` tem um `Offer` elemento, em seguida, cria uma sequência e transmite a `CreateSequenceResponse` da mensagem com um `Accept` elemento.

#### <a name="sequence-lifetime"></a>Tempo de vida de sequência

O WCF trata duas sequências como uma sessão duplex totalmente.

Ao gerar uma falha que uma sequência de falhas, o WCF espera que o ponto de extremidade remoto para ambas as sequências de falha. Após a leitura de uma falha que uma sequência de falhas, WCF falha em ambas as sequências.

O WCF pode fechar sua sequência de saída e continuar a processar mensagens em sua sequência de entrada. Por outro lado, o WCF pode processar o fechamento da sequência de entrada e continuar a enviar mensagens em sua sequência de saída.

### <a name="request-reply-and-one-way-non-addressable-initiator"></a>Iniciador de unidirecional, não endereçável e solicitação-resposta

#### <a name="binding"></a>Associação

O WCF oferece um unidirecional e padrão de troca de mensagem de solicitação-resposta usando duas sequências em um canal HTTP. O WCF usa solicitações HTTP para transmitir todas as mensagens do iniciador para as respostas HTTP e o respondente para transmitir todas as mensagens do respondedor para o iniciador.

#### <a name="createsequence-exchange"></a>Exchange CreateSequence

Transmite o iniciador do WCF uma `CreateSequence` da mensagem com um `Offer` elemento em uma solicitação HTTP e espera que o `CreateSequenceResponse` mensagem de resposta HTTP. O Respondente WCF cria uma sequência e transmite a `CreateSequenceResponse` da mensagem com um `Accept` elemento na resposta HTTP.

#### <a name="one-way-message"></a>Mensagem unidirecional

Para concluir com êxito uma troca de mensagens unidirecional, o iniciador de WCF transmite uma mensagem de sequência de solicitação na solicitação HTTP e recebe um autônomo `SequenceAcknowledgement` mensagem de resposta HTTP. O `SequenceAcknowledgement` devem reconhecer a mensagem transmitida.

O Respondente de WCF pode responder à solicitação com uma confirmação, uma falha ou uma resposta com um corpo vazio e o código de status HTTP 202.

#### <a name="two-way-messages"></a>Duas mensagens de forma

Para concluir um protocolo de troca de mensagem de duas vias com êxito, o iniciador de WCF transmite uma mensagem de sequência de solicitação na solicitação HTTP e recebe uma mensagem de resposta de sequência na resposta HTTP. A resposta deve conter um `SequenceAcknowledgement` confirmando a mensagem de sequência de solicitação transmitida.

O Respondente de WCF pode responder à solicitação com uma resposta do aplicativo, uma falha ou uma resposta com um corpo vazio e o código de status HTTP 202.

Devido à presença de mensagens unidirecional e o tempo de respostas do aplicativo, o número de sequência da mensagem de sequência de solicitação e o número de sequência da mensagem de resposta não têm nenhuma correlação.

#### <a name="retrying-replies"></a>Repetir respostas

O WCF conta com correlação de solicitação-resposta HTTP para correlação de protocolo de troca de mensagens bidirecional. Por causa disso, o iniciador do WCF não para tentar novamente uma mensagem de sequência de solicitação quando a mensagem de sequência de solicitação é confirmada, mas em vez disso, quando a resposta HTTP transporta um `SequenceAcknowledgement`, resposta do aplicativo ou falhas. O Respondente WCF repetições de respostas na resposta HTTP da solicitação à qual a resposta está correlacionada.

#### <a name="closesequence-exchange"></a>Exchange CreateSequence

Depois de receber todas as mensagens de resposta de sequência e as confirmações para todas as mensagens de sequência de solicitação unidirecional, o iniciador do WCF transmite uma `CloseSequence` da mensagem para a sequência de solicitação em uma solicitação HTTP e espera que o `CloseSequenceResponse` na resposta HTTP.

A sequência de solicitação de fechamento implicitamente fecha a sequência de resposta. Isso significa que o iniciador do WCF inclui o Final da sequência de resposta `SequenceAcknowledgement` sobre o `CloseSequence` mensagem e a sequência de resposta não tem um `CloseSequence` exchange.

O Respondente WCF garante que todas as respostas são confirmadas e transmite o `CloseSequenceResponse` mensagem de resposta HTTP.

#### <a name="terminatesequence-exchange"></a>Exchange TerminateSequence

Após o recebimento de `CloseSequenceResponse` o iniciador do WCF de mensagem, transmite um `TerminateSequence` da mensagem para a sequência de solicitação em uma solicitação HTTP e espera que o `TerminateSequenceResponse` na resposta HTTP.

Como o `CloseSequence` exchange, encerrando a sequência de solicitação implicitamente encerra a sequência de resposta. Isso significa que o iniciador do WCF inclui o final da sequência de resposta `SequenceAcknowledgement` sobre o `TerminateSequence` mensagem e a sequência de resposta não tem um `TerminateSequence` exchange.

O Respondente WCF transmite o `TerminateSequenceResponse` mensagem de resposta HTTP.

### <a name="requestreply-addressable-initiator"></a>Solicitação/resposta, o iniciador endereçável

#### <a name="binding"></a>Associação

O WCF fornece um padrão de troca de mensagem de solicitação-resposta usando duas sequências sobre uma entrada e um canal HTTP de saída. Esse padrão de troca de mensagem pode ser combinado com o `Duplex, Addressable` padrão de troca de mensagem do iniciador de uma maneira limitada. O WCF usa as solicitações HTTP para transmitir todas as mensagens. Todas as respostas HTTP tem um corpo vazio e o código de status HTTP 202.

#### <a name="createsequence-exchange"></a>Exchange CreateSequence

O iniciador do WCF transmite uma `CreateSequence` da mensagem com um `Offer` elemento em uma solicitação HTTP. O Respondente WCF garante que o `CreateSequence` tem um `Offer` elemento, em seguida, cria uma sequência e transmite a `CreateSequenceResponse` da mensagem com um `Accept` elemento.

#### <a name="requestreply-correlation"></a>Correlação de solicitação/resposta

O seguinte se aplica a correlacionados todas as solicitações e respostas:

- WCF garante que todos os urso de mensagens de solicitação de aplicativo um `ReplyTo` referência de ponto de extremidade e um `MessageId`.

- WCF aplica-se a referência de ponto de extremidade local como cada mensagem de solicitação de aplicativo `ReplyTo`. A referência de ponto de extremidade local é o `CreateSequence` da mensagem `ReplyTo` para o iniciador e o `CreateSequence` da mensagem `To` para o respondente.

- WCF garante essa solicitação de entrada de mensagens tenha uma `MessageId` e um `ReplyTo`.

- WCF garante a `ReplyTo` URI da referência do ponto de extremidade de todas as mensagens de solicitação do aplicativo corresponde à referência do ponto de extremidade local, conforme definido anteriormente.

- WCF garante que todas as respostas assume integralmente o correto `RelatesTo` e `To` cabeçalhos a seguir `wsa` regras de correlação de solicitação/resposta.
