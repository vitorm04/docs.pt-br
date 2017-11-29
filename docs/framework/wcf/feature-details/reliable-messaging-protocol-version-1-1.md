---
title: "Protocolo de mensagem confiável versão 1.1"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0da47b82-f8eb-42da-8bfe-e56ce7ba6f59
caps.latest.revision: "13"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 98fe8ac04b7ac811802466cf63c58ea4cebd791e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="reliable-messaging-protocol-version-11"></a>Protocolo de mensagem confiável versão 1.1
Este tópico aborda [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] detalhes de implementação para o WS-ReliableMessaging de fevereiro de 2007 (versão 1.1) protocolo necessárias para a interoperação usando o transporte HTTP. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]segue a especificação WS-ReliableMessaging com as restrições e esclarecimentos explicados neste tópico. Observe que o protocolo do WS-ReliableMessaging versão 1.1 é implementado começando com o [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)].  
  
 O WS-ReliableMessaging de fevereiro de 2007 protocolo é implementado em [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] pelo <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>.  
  
 Para sua conveniência, o tópico usa as seguintes funções:  
  
-   Iniciador: O cliente que inicia a criação de sequência de mensagem WS-Reliable.  
  
-   Respondente: O serviço que recebe as solicitações do iniciador.  
  
 Este documento usa os namespaces e prefixos na tabela a seguir.  
  
|Prefixo|Namespace|  
|-|-|  
|WSRM|http://docs.oasis-open.org/ws-Rx/WSRM/200702|  
|netrm|http://schemas.microsoft.com/WS/2006/05/RM|  
|s|http://www.w3.org/2003/05/SOAP-envelope|  
|wsa|http://schemas.xmlsoap.org/ws/2005/08/Addressing|  
|wsse|http://docs.oasis-open.org/WSS/2004/01/OASIS-200401-wssecurity-secext-1.0.xsd|  
|wsrmp|http://docs.oasis-open.org/ws-Rx/wsrmp/200702|  
|netrmp|http://schemas.microsoft.com/WS-Rx/wsrmp/200702|  
|wsp|(WS-Policy 1.2 ou WS-Policy 1.5)|  
  
## <a name="messaging"></a>Mensagens  
  
### <a name="sequence-creation"></a>Criação de sequência  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]implementa `CreateSequence` e `CreateSequenceResponse` de sequência de mensagens para estabelecer um sistema de mensagens confiável. As seguintes restrições se aplicam:  
  
-   B1101: O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] iniciador usa a mesma referência de ponto de extremidade como o `CreateSequence` da mensagem `ReplyTo`, `AcksTo` e `Offer/Endpoint`.  
  
-   R1102: O `AcksTo`, `ReplyTo` e `Offer/Endpoint` referências de ponto de extremidade no `CreateSequence` mensagem deve ter valores de endereço com representações de cadeia de caracteres idêntica, de modo que elas correspondam ao octet-wise.  
  
    -   O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] respondente verifica se a parte do URI do `AcksTo`, `ReplyTo` e `Endpoint` referências de ponto de extremidade são idênticas antes de criar uma sequência.  
  
-   R1103: O `AcksTo`, `ReplyTo` e `Offer/Endpoint` referências de ponto de extremidade no `CreateSequence` mensagem deve ter o mesmo conjunto de parâmetros de referência.  
  
    -   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]não impõe, mas presume que façam referência a parâmetros do `AcksTo`, `ReplyTo` e `Offer/Endpoint` referências de ponto de extremidade nas `CreateSequence` são idênticos e usa os parâmetros de referência do `ReplyTo` referência de ponto de extremidade para confirmações e mensagens na sequência inverso.  
  
-   B1104: O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] iniciador não gera opcional `Expires` ou `Offer/Expires` elemento o `CreateSequence` mensagem.  
  
-   B1105: Ao acessar o `CreateSequence` mensagem, o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Respondente usa o `Expires` valor no `CreateSequence` elemento como o `Expires` valor no `CreateSequenceResponse` elemento. Caso contrário, o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Respondente lê e ignora o `Expires` e `Offer/Expires` valores.  
  
-   B1106: Ao acessar o `CreateSequenceResponse` mensagem, o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] iniciador lê opcional `Expires` valor mas não usá-lo.  
  
-   B1107: O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] iniciador e Respondente sempre geram opcional `IncompleteSequenceBehavior` elemento o `CreateSequence/Offer` e `CreateSequenceResponse` elementos.  
  
-   B1108: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usa apenas o `DiscardFollowingFirstGap` e `NoDiscard` valores no `IncompleteSequenceBehavior` elemento.  
  
    -   WS-ReliableMessaging utiliza o `Offer` mecanismo para estabelecer os dois conversam correlacionadas sequências que formam uma sessão.  
  
-   B1109: Se `CreateSequence` contém um `Offer` elemento, uma maneira [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Respondente rejeita a sequência oferecida por responder com uma `CreateSequenceResponse` sem um `Accept` elemento.  
  
-   B1110: Se um Respondente de mensagens confiável rejeita a sequência oferecida, o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] a sequência recentemente estabelecida de falhas de iniciador.  
  
-   B1111: Se `CreateSequence` não contém um `Offer` elemento, o bidirecional [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Respondente rejeita a sequência oferecida por responder com uma `CreateSequenceRefused` falha.  
  
-   R1112: Quando dois conversam sequências estabelecidas usando o `Offer` mecanismo, o `[address]` propriedade o `CreateSequenceResponse/Accept/AcksTo` referência de ponto de extremidade deve coincidir com o URI de destino do `CreateSequence` bytes de mensagem para byte.  
  
-   R1113: Quando dois conversam sequências estabelecidas usando o `Offer` mecanismo, todas as mensagens em ambas as sequências que fluem do iniciador para o respondedor devem ser enviadas para a mesma referência de ponto de extremidade.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]usa o WS-ReliableMessaging para estabelecer sessões confiáveis entre o iniciador e respondente. O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WS-ReliableMessaging implementação fornece uma sessão confiável para unidirecional, solicitação-resposta e completo duplex padrões de mensagens. O WS-ReliableMessaging `Offer` mecanismo `CreateSequence` e `CreateSequenceResponse` permite que você estabeleça inverso correlacionado duas sequências e fornece um protocolo de sessão que é adequado para todos os pontos de extremidade de mensagens. Porque [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] fornece uma garantia de segurança para uma sessão incluindo proteção de ponta a ponta para integridade de sessão, é prático garantir que as mensagens destinadas a mesma parte chegarem ao mesmo destino. Isso também permite que a "inclua-backup" de confirmações de sequência em mensagens de aplicativo. Portanto, R1102, R1112 e R1113 as restrições se aplicam a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
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
  
### <a name="closing-a-sequence"></a>Fechando uma sequência  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]usa o `CloseSequence` e `CloseSequenceResponse` mensagens para um desligamento iniciado fonte mensagens confiáveis. O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] destino mensagens confiáveis não iniciar o desligamento e a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] fonte confiável de mensagens não oferece suporte a um desligamento iniciado pelo destino mensagens confiáveis. As seguintes restrições se aplicam:  
  
-   B1201: O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] origem de mensagens confiáveis sempre envia um `CloseSequence` mensagem desligar a sequência.  
  
-   B1202: A origem de mensagens confiáveis aguarda confirmação de toda a gama de mensagens na sequência antes de enviar o `CloseSequence` mensagem.  
  
-   B1203: A origem de mensagens confiáveis sempre inclui opcional `LastMsgNumber` elemento, a menos que a sequência não contém mensagens.  
  
-   R1204: O destino de mensagens confiáveis não deve iniciar desligamento enviando um `CloseSequence` mensagem.  
  
-   B1205: após receber uma `CloseSequence` mensagem, o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] origem de mensagens confiáveis considera a sequência incompleta e envia uma falha.  
  
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
Example CloseSequenceResponse message:  
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
  
### <a name="sequence-termination"></a>Término de sequência  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]usa basicamente o `TerminateSequence/TerminateSequenceResponse` handshake depois de concluir o `CloseSequence/CloseSequenceResponse` handshake. O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] destino mensagens confiáveis não iniciará o encerramento e a fonte de mensagens confiáveis não dá suporte a um sistema de mensagens confiável iniciadas pelo destino encerramento. As seguintes restrições se aplicam:  
  
-   B1301: O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] iniciador envia somente a `TerminateSequence` mensagem após a conclusão bem-sucedida do `CloseSequence/CloseSequenceResponse` handshake.  
  
-   R1302: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] valida que o `LastMsgNumber` elemento é consistente em todas as `CloseSequence` e `TerminateSequence` mensagens para uma determinada sequência. Isso significa que `LastMsgNumber` não está presente em todos os `CloseSequence` e `TerminateSequence` mensagens, ou ele está presente e idênticos em todos os `CloseSequence` e `TerminateSequence` mensagens.  
  
-   B1303: Durante o recebimento de uma `TerminateSequence` mensagem após o `CloseSequence/CloseSequenceResponse` handshake, o destino do sistema de mensagens confiável responde com um `TerminateSequenceResponse` mensagem. Como a origem do sistema de mensagens confiável tem a confirmação final antes de enviar o `TerminateSequence` mensagem, o destino do sistema de mensagens confiável sabe, sem dúvida que a sequência termina e recupera os recursos imediatamente.  
  
-   B1304: Durante o recebimento de uma `TerminateSequence` mensagem antes do `CloseSequence/CloseSequenceResponse` handshake, o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] mensagens confiáveis destino responde com um `TerminateSequenceResponse` mensagem. Se o destino do sistema de mensagens confiável determina que não há nenhuma inconsistência na sequência, o destino do sistema de mensagens confiável aguarda uma hora de destino especificado do aplicativo antes da recuperação de recursos, para permitir que o cliente a chance de recebimento a confirmação final. Caso contrário, o destino do sistema de mensagens confiável recupera os recursos imediatamente e indica para o destino do aplicativo que a sequência termina com dúvida, gerando o `Faulted` evento.  
  
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
Example TerminateSequenceResponse message:  
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
  
-   B1401:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] gera e acessa os números de sequência não mais que `xs:long`do valor inclusivo máximo, 9223372036854775807.  
  
 Um exemplo de um `Sequence` cabeçalho.  
  
```xml  
<wsrm:Sequence s:mustUnderstand="1">  
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
  <wsrm:MessageNumber>1</wsrm:MessageNumber>  
</wsrm:Sequence>  
```  
  
### <a name="request-acknowledgement"></a>Solicitação de confirmação  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]usa o `AckRequested` cabeçalho como um mecanismo de keep-alive.  
  
 Um exemplo de um `AckRequested` cabeçalho.  
  
```xml  
<wsrm:AckRequested>  
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
</wsrm:AckRequested>  
```  
  
### <a name="sequenceacknowledgement"></a>SequenceAcknowledgement  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]usa um mecanismo de "back inclua" para confirmações de sequência fornecidas em mensagens WS-Reliable. As seguintes restrições se aplicam:  
  
-   R1601: Quando dois conversam sequências estabelecidas usando o `Offer` mecanismo, o `SequenceAcknowledgement` cabeçalho pode ser incluído em qualquer mensagem de aplicativo transmitida para o destinatário pretendido. O ponto de extremidade remoto deve ser capaz de acessar um acumuladas `SequenceAcknowledgement` cabeçalho.  
  
-   B1602: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] não gera `SequenceAcknowledgement` cabeçalhos que contêm `Nack` elementos. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]valida que cada `Nack` elemento contém um número de sequência, mas ignora caso contrário, o `Nack` elemento e valor.  
  
 Um exemplo de um `SequenceAcknowledgement` cabeçalho.  
  
```xml  
<wsrm:SequenceAcknowledgement>  
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
  <wsrm:AcknowledgementRange Lower="1" Upper="1"></wsrm:AcknowledgementRange>  
</wsrm:SequenceAcknowledgement>  
```  
  
### <a name="ws-reliablemessaging-faults"></a>Falhas de WS-ReliableMessaging.  
 A seguir está uma lista de restrições que se aplicam a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] implementação de falhas de WS-ReliableMessaging. As seguintes restrições se aplicam:  
  
-   B1701: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] não gera `MessageNumberRollover` falhas.  
  
-   B1702: Sobre SOAP 1.2, quando o ponto de extremidade do serviço atinge seu limite de conexão e não pode processar novas conexões, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] gera um aninhada `CreateSequenceRefused` falha subcódigo, `netrm:ConnectionLimitReached`, conforme mostrado no exemplo a seguir.  
  
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
 Como o WS-ReliableMessaging usa WS-Addressing, o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] implementação de WS-ReliableMessaging pode gerar e WS-Addressing falhas de transmissão. Este abrange seção WS-Addressing falhas que [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] gera e transmite na camada do WS-ReliableMessaging explicitamente:  
  
-   B1801:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] gera e transmite o `Message Addressing Header Required` falha quando uma das seguintes opções for verdadeira:  
  
    -   Um `CreateSequence`, `CloseSequence` ou `TerminateSequence` mensagem está falta um `MessageId` cabeçalho.  
  
    -   Um `CreateSequence`, `CloseSequence` ou `TerminateSequence` mensagem está falta um `ReplyTo` cabeçalho.  
  
    -   Um `CreateSequenceResponse`, `CloseSequenceResponse`, ou `TerminateSequenceResponse` mensagem está falta um `RelatesTo` cabeçalho.  
  
-   B1802:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] gera e transmite o `Endpoint Unavailable` falhas para indicar que não há nenhum ponto de extremidade de escuta que podem processar a sequência com base na análise dos cabeçalhos de endereçamento no `CreateSequence` mensagem.  
  
## <a name="protocol-composition"></a>Composição de protocolo  
  
### <a name="composition-with-ws-addressing"></a>Composição com WS-Addressing.  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]dá suporte a duas versões do WS-Addressing: 2004 do WS-Addressing/08 [WS-ADDR] e recomendações de 1.0 W3C WS-Addressing [WS-ADDR-CORE] e [WS-ADDR-SOAP].  
  
 Enquanto as menções de especificação WS-ReliableMessaging 2004 do WS-Addressing somente/08, não restringe a versão de WS-Addressing a ser usada. A seguir está uma lista de restrições que se aplicam a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:  
  
-   R2101: Ambos 08/2004 do WS-Addressing e WS-Addressing 1.0 podem ser usado com mensagens WS-Reliable.  
  
-   R2102: Uma única versão do WS-Addressing deve ser usada em uma sequência WS-ReliableMessaging determinada ou um par de sequências inverso correlacionados usando o `Offer` mecanismo.  
  
### <a name="composition-with-soap"></a>Composição de SOAP  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]oferece suporte ao uso de SOAP 1.1 e SOAP 1.2 com mensagens WS-Reliable.  
  
### <a name="composition-with-ws-security-and-ws-secureconversation"></a>Composição com WS-Security e WS-SecureConversation  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]fornece proteção para as sequências de WS-ReliableMessaging usando segura de transporte (HTTPS), composição com WS-Security e composição com WS-Secure Conversation. O protocolo WS-ReliableMessaging 1.1, WS-Security 1.1 e o protocolo WS-Secure Conversation 1.3 devem ser usados juntos. A seguir está uma lista de restrições que se aplicam a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:  
  
-   R2301: Para proteger a integridade de um WS-ReliableMessaging sequência além de integridade e confidencialidade de mensagens individuais, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] requer que o WS-Secure Conversation deve ser usada.  
  
-   R2302:AWS-Secure Conversation deve ser estabelecida antes de estabelecer a sequência de WS-ReliableMessaging.  
  
-   R2303: Se o tempo de vida de sequência WS-ReliableMessaging excede o WS-Secure Conversation tempo de vida da sessão, o `SecurityContextToken` estabelecida usando o WS-Secure Conversation deve ser renovado usando a associação de WS-Secure Conversation renovação correspondente.  
  
-   B2304:WS-ReliableMessaging sequência ou um par de sequências inverso correlacionado sempre estão associados a uma única sessão do WS-SecureConversation.  
  
-   R2305: Quando composto com WS-Secure Conversation, a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Respondente requer que o `CreateSequence` mensagem contêm o `wsse:SecurityTokenReference` elemento e o `wsrm:UsesSequenceSTR` cabeçalho.  
  
 Um exemplo de um `UsesSequenceSTR` cabeçalho.  
  
```xml  
<wsrm:UsesSequenceSTR></wsrm:UsesSequenceSTR>  
```  
  
### <a name="composition-with-ssltls-sessions"></a>Composição com sessões SSL/TLS  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]não oferece suporte a composição com sessões SSL/TLS:  
  
-   B2401: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] não gera o `wsrm:UsesSequenceSSL` cabeçalho.  
  
-   R2402: Um iniciador de mensagens confiável não deve enviar um `CreateSequence` mensagem com um `wsrm:UsesSequenceSSL` cabeçalho para um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Respondente.  
  
### <a name="composition-with-ws-policy"></a>Composição com WS-Policy  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]dá suporte a duas versões do WS-Policy: WS-Policy 1.2 e WS-Policy 1.5.  
  
## <a name="ws-reliablemessaging-ws-policy-assertion"></a>WS-ReliableMessaging WS-declaração de política  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]usa o WS-ReliableMessaging WS-Policy asserção `wsrm:RMAssertion` para descrever os recursos de pontos de extremidade. A seguir está uma lista de restrições que se aplicam a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:  
  
-   B3001: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] anexa `wsrmn:RMAssertion` asserção de WS-Policy para `wsdl:binding` elementos. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]dá suporte a ambos os anexos para `wsdl:binding` e `wsdl:port` elementos.  
  
-   B3002: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] nunca gera o `wsp:Optional` marca.  
  
-   B3003: Ao acessar o `wsrmp:RMAssertion` asserção de WS-Policy [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ignora o `wsp:Optional` marca e trata a política WS-RM como obrigatória.  
  
-   R3004: Porque [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] não compor com sessões SSL/TLS, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] não aceita a política que especifica `wsrmp:SequenceTransportSecurity`.  
  
-   B3005: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sempre gera o `wsrmp:DeliveryAssurance` elemento.  
  
-   B3006: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sempre Especifica o `wsrmp:ExactlyOnce` garantia de entrega.  
  
-   B3007: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] gera e lê as seguintes propriedades da asserção WS-ReliableMessaging e fornece controle sobre eles no [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] `ReliableSessionBindingElement`:  
  
    -   `netrmp:InactivityTimeout`  
  
    -   `netrmp:AcknowledgementInterval`  
  
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
  
## <a name="flow-control-ws-reliablemessaging-extension"></a>Extensão de WS-ReliableMessaging de controle de fluxo  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]usa extensibilidade do WS-ReliableMessaging para fornecer maior controle adicional opcional sobre o fluxo de mensagem de sequência.  
  
 Controle de fluxo é habilitado definindo o `ReliableSessionBindingElement`do `FlowControlEnabled``boolean` propriedade `true`. A seguir está uma lista de restrições que se aplicam a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:  
  
-   B4001: Controlar quando o fluxo de mensagens confiável estiver habilitada, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] gera um `netrm:BufferRemaining` a extensibilidade do elemento do elemento de `SequenceAcknowledgement` cabeçalho, conforme mostrado no exemplo a seguir.  
  
    ```xml  
    <wsrm:SequenceAcknowledgement>  
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
      <wsrm:AcknowledgementRange Upper="1" Lower="1"/>             
      <netrm:BufferRemaining>8</netrm:BufferRemaining>  
    </wsrm:SequenceAcknowledgement>  
    ```  
  
-   B4002: O controle de fluxo de mensagens mesmo quando confiável estiver habilitado, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] não requer um `netrm:BufferRemaining` elemento o `SequenceAcknowledgement` cabeçalho.  
  
-   B4003: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usa o destino de mensagens confiável `netrm:BufferRemaining` indicar quantas novas mensagens ele consegue armazenar em buffer.  
  
-   B4004:when confiável de mensagens de fluxo de controle é habilitado, o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] fonte confiável de mensagens usará o valor de `netrm:BufferRemaining` para transmissão de mensagens de limitação.  
  
-   B4005: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] gera `netrm:BufferRemaining` inteiro entre 0 e 4096 inclusivo de valores e lê os valores de número inteiro entre 0 e `xs:int`do `maxInclusive` valor 214748364 inclusivo.  
  
## <a name="message-exchange-patterns"></a>Padrões de troca de mensagem  
 Esta seção descreve [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]do comportamento ao WS-ReliableMessaging usada para diferentes padrões de troca de mensagem. Para cada padrão de troca de mensagens, os seguintes cenários de duas implantações são considerados:  
  
-   Iniciador não endereçável: Iniciador está atrás de um firewall. Respondente pode entregar mensagens para o iniciador somente em respostas HTTP.  
  
-   Iniciador endereçável: Iniciador e Respondente podem ser enviadas solicitações HTTP; em outras palavras, duas conexões de HTTP inverso podem ser estabelecidas.  
  
### <a name="one-way-non-addressable-initiator"></a>Iniciador unidirecional, não endereçável  
  
#### <a name="binding"></a>Associação  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Fornece um padrão de troca de mensagem unidirecional usando uma sequência por um canal HTTP. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]usa as solicitações HTTP para transmitir todas as mensagens do iniciador para as respostas do Respondente e HTTP para transmitir todas as mensagens do Respondente para o iniciador.  
  
#### <a name="createsequence-exchange"></a>CreateSequence Exchange  
 O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] iniciador transmite um `CreateSequence` mensagem sem nenhum `Offer` elemento em uma solicitação HTTP e espera o `CreateSequenceResponse` mensagem na resposta HTTP. O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Respondente cria uma sequência e transmite o `CreateSequenceResponse` mensagem sem nenhum `Accept` elemento na resposta HTTP.  
  
#### <a name="sequenceacknowledgement"></a>SequenceAcknowledgement  
 O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] iniciador processa as confirmações na resposta de todas as mensagens, exceto o `CreateSequence` mensagem e mensagens de falha. O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Respondente sempre transmite uma mensagem de confirmação autônoma na resposta HTTP a sequência de todas as e `AckRequested` mensagens.  
  
#### <a name="closesequence-exchange"></a>CreateSequence Exchange  
 O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] iniciador transmite um `CloseSequence` mensagem em uma solicitação HTTP e espera o `CreateSequenceResponse` mensagem na resposta HTTP. O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Respondente transmite o `CloseSequenceResponse` mensagem na resposta HTTP.  
  
#### <a name="terminatesequence-exchange"></a>TerminateSequence Exchange  
 O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] iniciador transmite um `TerminateSequence` mensagem em uma solicitação HTTP e espera o `TerminateSequenceResponse` mensagem na resposta HTTP. O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Respondente transmite o `TerminateSequenceResponse` mensagem na resposta HTTP.  
  
### <a name="one-way-addressable-initiator"></a>Iniciador de uma maneira, endereçável  
  
#### <a name="binding"></a>Associação  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Fornece um padrão de troca de mensagem unidirecional usando uma sequência sobre uma entrada e um canal HTTP de saída. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]usa as solicitações HTTP para transmitir todas as mensagens. Todas as respostas HTTP tem um corpo vazio e o código de status HTTP 202.  
  
#### <a name="createsequence-exchange"></a>CreateSequence Exchange  
 O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] iniciador transmite um `CreateSequence` mensagem sem nenhum `Offer` elemento em uma solicitação HTTP. O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Respondente cria uma sequência e transmite o `CreateSequenceResponse` mensagem sem nenhum `Accept` elemento em uma solicitação HTTP.  
  
### <a name="duplex-addressable-initiator"></a>Iniciador de duplex, endereçável  
  
#### <a name="binding"></a>Associação  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Fornece um padrão de troca de mensagem assíncrono totalmente, bidirecional usando duas sequências sobre uma entrada e um canal HTTP de saída. Esse padrão de troca de mensagem pode ser combinado com a `Request/Reply`, `Addressable` padrão de troca de mensagem do iniciador de uma maneira limitada. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]usa as solicitações HTTP para transmitir todas as mensagens. Todas as respostas HTTP tem um corpo vazio e o código de status HTTP 202.  
  
#### <a name="createsequence-exchange"></a>CreateSequence Exchange  
 O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] iniciador transmite um `CreateSequence` mensagem com um `Offer` elemento em uma solicitação HTTP. O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Respondente garante que o `CreateSequence` tem um `Offer` elemento, em seguida, cria uma sequência e transmite o `CreateSequenceResponse` mensagem com um `Accept` elemento.  
  
#### <a name="sequence-lifetime"></a>Tempo de vida de sequência  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]trata as duas sequências como uma sessão duplex totalmente.  
  
 Após a geração de uma falha que falhas de uma sequência, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] espera que o ponto de extremidade remoto para ambas as sequências de falha. Após a leitura de uma falha que falhas de uma sequência, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ambas as sequências de falhas.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Feche a sequência de saída e continuar a processar mensagens em sua sequência de entrada. Por outro lado, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] pode processar o fechamento da sequência de entrada e continuar a enviar mensagens em sua sequência de saída.  
  
### <a name="request-reply-and-one-way-non-addressable-initiator"></a>Unidirecional, não endereçável iniciador e solicitação-resposta  
  
#### <a name="binding"></a>Associação  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Fornece um padrão de troca de mensagem unidirecional e de solicitação-resposta usando duas sequências em um canal HTTP. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]usa as solicitações HTTP para transmitir todas as mensagens do iniciador para as respostas do Respondente e HTTP para transmitir todas as mensagens do Respondente para o iniciador.  
  
#### <a name="createsequence-exchange"></a>CreateSequence Exchange  
 O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] iniciador transmite um `CreateSequence` mensagem com um `Offer` elemento em uma solicitação HTTP e espera o `CreateSequenceResponse` mensagem na resposta HTTP. O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Respondente cria uma sequência e transmite o `CreateSequenceResponse` mensagem com um `Accept` elemento na resposta HTTP.  
  
#### <a name="one-way-message"></a>Mensagem unidirecional  
 Para concluir uma troca de mensagens unidirecional com êxito, o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] iniciador transmite uma mensagem de sequência de solicitação na solicitação HTTP e recebe um autônomo `SequenceAcknowledgement` mensagem na resposta HTTP. O `SequenceAcknowledgement` deve reconhecer a mensagem transmitida.  
  
 O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Respondente pode responder à solicitação com uma resposta com um corpo vazio e o código de status HTTP 202, uma falha ou uma confirmação.  
  
#### <a name="two-way-messages"></a>Duas mensagens de maneira  
 Para concluir um protocolo de intercâmbio de mensagens de duas vias com êxito, o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] iniciador transmite uma mensagem de sequência de solicitação na solicitação HTTP e recebe uma mensagem de sequência de resposta na resposta HTTP. A resposta deve conter um `SequenceAcknowledgement` confirmando a mensagem de sequência de solicitação transmitida.  
  
 O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Respondente pode responder à solicitação com uma resposta do aplicativo, uma falha ou uma resposta com um corpo vazio e o código de status HTTP 202.  
  
 Devido à presença de mensagens unidirecionais e o tempo de respostas de aplicativo, o número de sequência da mensagem de sequência de solicitação e número de sequência da mensagem de resposta não têm nenhuma correlação.  
  
#### <a name="retrying-replies"></a>Repetindo as respostas  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]depende da correlação de solicitação-resposta HTTP para correlação de protocolo de troca de mensagens bidirecional. Por isso, o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] iniciador não parar de tentar novamente uma mensagem de sequência de solicitação quando a mensagem de sequência de solicitação é confirmada, mas em vez disso, quando a resposta HTTP executa um `SequenceAcknowledgement`, resposta do aplicativo ou falhas. O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Respondente repete as respostas na resposta HTTP da solicitação para o qual a resposta correlacionada.  
  
#### <a name="closesequence-exchange"></a>CreateSequence Exchange  
 Depois de receber todas as mensagens de resposta de sequência e confirmações para todas as mensagens de sequência de solicitação unidirecional, o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] iniciador transmite um `CloseSequence` de mensagem para a sequência de solicitação em uma solicitação HTTP e espera que o `CloseSequenceResponse` em HTTP resposta.  
  
 A sequência de solicitação de fechamento implicitamente fecha a sequência de resposta. Isso significa que o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] iniciador inclui Final da sequência de resposta `SequenceAcknowledgement` no `CloseSequence` mensagem e a sequência de resposta não tem um `CloseSequence` exchange.  
  
 O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Respondente garante que todas as respostas são confirmados e transmite o `CloseSequenceResponse` mensagem na resposta HTTP.  
  
#### <a name="terminatesequence-exchange"></a>TerminateSequence Exchange  
 Após o recebimento de `CloseSequenceResponse` mensagem, o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] iniciador transmite um `TerminateSequence` de mensagem para a sequência de solicitação em uma solicitação HTTP e espera o `TerminateSequenceResponse` na resposta HTTP.  
  
 Como o `CloseSequence` exchange, encerrando a sequência de solicitação implicitamente encerra a sequência de resposta. Isso significa que o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] iniciador inclui final da sequência de resposta `SequenceAcknowledgement` no `TerminateSequence` mensagem e a sequência de resposta não tem um `TerminateSequence` exchange.  
  
 O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Respondente transmite o `TerminateSequenceResponse` mensagem na resposta HTTP.  
  
### <a name="requestreply-addressable-initiator"></a>Solicitação/resposta, o iniciador endereçável  
  
#### <a name="binding"></a>Associação  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Fornece um padrão de troca de mensagem de solicitação-resposta usando duas sequências sobre uma entrada e um canal HTTP de saída. Esse padrão de troca de mensagem pode ser combinado com o `Duplex, Addressable` padrão de troca de mensagem do iniciador de uma maneira limitada. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]usa as solicitações HTTP para transmitir todas as mensagens. Todas as respostas HTTP tem um corpo vazio e o código de status HTTP 202.  
  
#### <a name="createsequence-exchange"></a>CreateSequence Exchange  
 O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] iniciador transmite um `CreateSequence` mensagem com um `Offer` elemento em uma solicitação HTTP. O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Respondente garante que o `CreateSequence` tem um `Offer` elemento, em seguida, cria uma sequência e transmite o `CreateSequenceResponse` mensagem com um `Accept` elemento.  
  
#### <a name="requestreply-correlation"></a>Correlação de solicitação/resposta  
 O seguinte se aplica a correlacionado todas as solicitações e respostas:  
  
-   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]garante que todos os lembre de mensagens de solicitação de aplicativo um `ReplyTo` referência de ponto de extremidade e um `MessageId`.  
  
-   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]aplica-se a referência de ponto de extremidade local como cada mensagem de solicitação de aplicativo `ReplyTo`. A referência de ponto de extremidade local é o `CreateSequence` da mensagem `ReplyTo` para o iniciador e o `CreateSequence` da mensagem `To` para o respondente.  
  
-   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]garante que mensagens de solicitação de entrada tenha uma `MessageId` e um `ReplyTo`.  
  
-   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]garante a `ReplyTo` URI da referência do ponto de extremidade de todas as mensagens de solicitação de aplicativo corresponde à referência do ponto de extremidade local, conforme definido anteriormente.  
  
-   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]garante que todas as respostas assume corretas `RelatesTo` e `To` cabeçalhos a seguir `wsa` regras de correlação de solicitação/resposta.
