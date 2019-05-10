---
title: Protocolo de mensagens confiável versão 1.0
ms.date: 03/30/2017
ms.assetid: a5509a5c-de24-4bc2-9a48-19138055dcce
ms.openlocfilehash: 857bbbf9ffa1311c38cfc007e0cdc6bde06d6284
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64617574"
---
# <a name="reliable-messaging-protocol-version-10"></a>Protocolo de mensagens confiável versão 1.0
Este tópico abrange detalhes de implementação do Windows Communication Foundation (WCF) para o WS-Reliable Messaging necessárias para usar o transporte HTTP de interoperação de protocolo de fevereiro de 2005 (versão 1.0). WCF segue a especificação WS-Reliable Messaging com as restrições e esclarecimentos explicados neste tópico. Observe que o protocolo de versão 1.0 WS-ReliableMessaging é implementado começando com o [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)].  
  
 O WS-Reliable Messaging de fevereiro de 2005 protocolo é implementado no WCF, o <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>.  
  
 Para sua conveniência, o tópico usa as seguintes funções:  
  
- Iniciador: o cliente que inicia a criação da sequência de mensagens WS-Reliable  
  
- Respondente: o serviço que recebe solicitações do iniciador  
  
 Este documento usa os prefixos e namespaces na tabela a seguir.  
  
|Prefixo|Namespace|  
|------------|---------------|  
|wsrm|http://schemas.xmlsoap.org/ws/2005/02/rm|  
|netrm|http://schemas.microsoft.com/ws/2006/05/rm|  
|s|http://www.w3.org/2003/05/soap-envelope|  
|wsa|http://schemas.xmlsoap.org/ws/2005/08/addressing|  
|wsse|http://docs.oasis-open.org/wss/2004/01/oasis-200401-wssecurity-secext-1.0.xsd|  
  
## <a name="messaging"></a>Mensagens  
  
### <a name="sequence-establishment-messages"></a>Mensagens de estabelecimento de sequência  
 O WCF implementa `CreateSequence` e `CreateSequenceResponse` mensagens para estabelecer uma sequência de mensagens confiável. As seguintes restrições se aplicam:  
  
- B1101: O iniciador do WCF não gera o elemento Expires opcional na `CreateSequence` mensagem ou, nos casos quando o `CreateSequence` mensagem contém um `Offer` elemento, opcional `Expires` elemento no `Offer` elemento.  
  
- B1102: Ao acessar o `CreateSequence` da mensagem, o WCF`Responder` envia e recebe ambos `Expires` elementos se eles existirem, mas não usa seus valores.  
  
 WS-Reliable Messaging apresenta o `Offer` mecanismo para estabelecer os dois conversam correlacionadas sequências que formam uma sessão.  
  
- R1103: Se `CreateSequence` contém uma `Offer` elemento, o Respondente de mensagens confiável deve aceitar a sequência e responda com `CreateSequenceResponse` que contém um `wsrm:Accept` elemento, formando dois correlacionados conversar sequências ou rejeitar a `CreateSequence`solicitação.  
  
- R1104: `SequenceAcknowledgement` e mensagens de aplicativo que fluem em sequência inverso devem ser enviadas para o `ReplyTo` referência de ponto de extremidade do `CreateSequence`.  
  
- R1105: `AcksTo` e `ReplyTo` referências de ponto de extremidade no `CreateSequence` devem ter valores de endereço que correspondem a octet-wise.  
  
     O WCF respondente verifica se a parte do URI de `AcksTo` e `ReplyTo` EPRs são idênticos antes de criar uma sequência.  
  
- R1106: `AcksTo` e `ReplyTo` referências de ponto de extremidade no `CreateSequence` deve ter o mesmo conjunto de parâmetros de referência.  
  
     WCF não impõe mas presume que [parâmetros de referência] de `AcksTo` e `ReplyTo` na `CreateSequence` são idênticas e usa [referência parâmetros] do `ReplyTo` referência de ponto de extremidade para as confirmações e mensagens de sequência inverso.  
  
- R1107: Quando duas sequências inverso são estabelecidas usando o `Offer` mecanismo, `SequenceAcknowledgement` e mensagens de aplicativo que fluem em sequências inverso devem ser enviadas para o `ReplyTo` referência de ponto de extremidade do `CreateSequence`.  
  
- R1108: Quando duas sequências inverso são estabelecidas usando o mecanismo de oferta, o `[address]` propriedade do `wsrm:AcksTo` elemento filho de referência de ponto de extremidade do `wsrm:Accept` elemento do `CreateSequenceResponse` deve corresponder ao byte-wise o URI de destino do `CreateSequence`.  
  
- R1109: Quando duas sequências inverso são estabelecidas usando o `Offer` mecanismo, as mensagens enviadas pelo iniciador e confirmações para mensagens pelo respondente devem ser enviadas para a mesma referência de ponto de extremidade.  
  
     O WCF usa WS-Reliable Messaging para estabelecer sessões confiáveis entre o iniciador e respondente. Implementação de WS-Reliable Messaging do WCF fornece sessão confiável para unidirecional, solicitação-resposta e full duplex padrões de mensagens. O WS-Reliable Messaging `Offer` mecanismo `CreateSequence` / `CreateSequenceResponse` lhe permite estabelecer duas sequências inverso correlacionados e fornece um protocolo de sessão que é adequado para todos os pontos de extremidade de mensagem. Como o WCF fornece uma garantia de segurança para essa sessão, incluindo a proteção de ponta a ponta para integridade de sessão, é prático garantir que se destina à mesma parte de mensagens chegam ao mesmo destino. Isso também permite aproveitando de confirmações de sequência em mensagens do aplicativo. Portanto, R1104, R1105 e R1108 de restrições se aplicam ao WCF.  
  
 Um exemplo de um `CreateSequence` mensagem.  
  
```xml  
<s:Envelope>  
  <s:Header>  
    <a:Action s:mustUnderstand="1">  
      http://schemas.xmlsoap.org/ws/2005/02/rm/CreateSequence  
    </a:Action>  
    <a:ReplyTo>  
      <a:Address>          
         http://Business456.com/clientA        
      </a:Address>  
    </a:ReplyTo>  
    <a:MessageID>  
      urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36  
    </a:MessageID>  
    <a:To s:mustUnderstand="1">  
      http://Business456.com/clientA  
    </a:To>  
  </s:Header>  
  <s:Body>  
    <wsrm:CreateSequence>  
      <wsrm:AcksTo>  
       <wsa:Address>  
         http://Business456.com/clientA  
       </wsa:Address>  
     </wsrm:AcksTo>  
     <wsrm:Offer>  
      <wsrm:Identifier>  
        urn:uuid:0afb8d36-bf26-4776-b8cf-8c91fddb5496  
      </wsrm:Identifier>  
     </wsrm:Offer>  
   </wsrm:CreateSequence>  
  </s:Body>  
</s:Envelope>  
```  
  
 Um exemplo de um `CreateSequenceResponse` mensagem.  
  
```xml  
<s:Envelope>  
  <s:Header>  
    <a:Action s:mustUnderstand="1">  
      http://schemas.xmlsoap.org/ws/2005/02/rm/CreateSequenceResponse  
    </a:Action>  
    <a:RelatesTo>  
      urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36  
    </a:RelatesTo>  
    <a:To s:mustUnderstand="1">  
      http://Business456.com/clientA  
    </a:To>  
  </s:Header>  
  <s:Body>  
   <wsrm:CreateSequenceResponse>  
    <Identifier>  
     urn:uuid:eea0a36c-b38a-43e8-8c76-2fabe2d76386  
    </Identifier>  
    <Accept>  
    <AcksTo>  
      <a:Address>  
        http://BusinessABC.com/serviceA  
      </a:Address>  
    </AcksTo>  
    </Accept>  
   </wsrm:CreateSequenceResponse>  
  </s:Body>  
</s:Envelope>  
```  
  
### <a name="sequence"></a>Sequência  
 A seguir está uma lista de restrições que se aplicam a sequências:  
  
- Gera B1201:WCF e maior do que de números de sequência de acessos `xs:long`do valor máximo inclusivo, 9223372036854775807.  
  
- B1202:WCF sempre gera uma mensagem de último incorporada vazio com o URI da ação de `http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage`.  
  
- B1203: O WCF recebe e entrega uma mensagem com um cabeçalho de sequência que contém um `LastMessage` elemento, desde que o URI da ação não é `http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage`.  
  
 Um exemplo de um cabeçalho de sequência.  
  
```xml  
<wsrm:Sequence>  
  <wsrm:Identifier>  
    urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36  
  </wsrm:Identifier>  
  <wsrm:MessageNumber>  
    10  
  </wsrm:MessageNumber>  
  <wsrm:LastMessage/>  
 </wsrm:Sequence>  
```  
  
### <a name="ackrequested-header"></a>Cabeçalho AckRequested  
 O WCF usa `AckRequested` cabeçalho como um mecanismo keep-alive. O WCF não gera opcional `MessageNumber` elemento. Ao receber uma mensagem com um `AckRequested` cabeçalho que contém o `MessageNumber` WCF de elemento, ignora o `MessageNumber` valor do elemento, conforme mostrado no exemplo a seguir.  
  
```xml  
<wsrm:AckRequested>  
  <wsrm:Identifier>  
    urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36  
  </wsrm:Identifier>  
</wsrm:AckRequested>  
```  
  
### <a name="sequenceacknowledgement-header"></a>Cabeçalho SequenceAcknowledgement  
 WCF usa o mecanismo de transporte-back para confirmações de sequência fornecidas no sistema de mensagens WS-Reliable.  
  
- R1401: Quando duas sequências inverso são estabelecidas usando o `Offer` mecanismo, o `SequenceAcknowledgement` cabeçalho pode ser incluído em qualquer mensagem de aplicativo transmitida ao destinatário pretendido.  
  
- B1402: Quando o WCF deve gerar uma confirmação antes de receber mensagens de qualquer sequência (por exemplo, para atender a um `AckRequested` mensagem), o WCF gera uma `SequenceAcknowledgement` cabeçalho que contém o intervalo de 0-0, conforme mostrado no exemplo a seguir.  
  
    ```xml  
    <wsrm:SequenceAcknowledgement>  
      <wsrm:Identifier>  
        urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36  
      </wsrm:Identifier>  
      <wsrm:AcknowledgementRange Upper="0" Lower="0"/>  
    </wsrm:SequenceAcknowledgement>  
    ```  
  
- B1403: O WCF não gera `SequenceAcknowledgement` cabeçalhos que contêm um `Nack` elemento, mas dá suporte a `Nack` elementos.  
  
### <a name="ws-reliablemessaging-faults"></a>Falhas de WS-ReliableMessaging  
 A seguir está uma lista de restrições que se aplicam para a implementação de WCF do WS-Reliable Messaging falhas:  
  
- B1501: O WCF não gera `MessageNumberRollover` falhas.  
  
- Ponto de extremidade B1502:WCF pode gerar `CreateSequenceRefused` conforme descrito na especificação de falhas.  
  
- B1503:when o ponto de extremidade do serviço atingir seu limite de conexão e não pode processar novas conexões, o WCF gera adicional `CreateSequenceRefused` subcódigo, de falha `netrm:ConnectionLimitReached`, conforme mostrado no exemplo a seguir.  
  
    ```xml  
    <s:Envelope>  
      <s:Header>  
        <wsa:Action>  
          http://schemas.xmlsoap.org/ws/2005/08/addressing/fault  
        </wsa:Action>  
      </s:Header>  
      <s:Body>  
        <s:Fault>  
          <s:Code>  
            <s:Value>  
              s:Receiver  
            </s:Value>  
            <s:Subcode>  
              <s:Value>  
                wsrm:CreateSequenceRefused  
              </s:Value>  
              <s:Subcode>  
                <s:Value>  
                  netrm:ConnectionLimitReached  
                </s:Value>  
              </s:Subcode>  
            </s:Subcode>  
          </s:Code>  
          <s:Reason>  
            <s:Text xml:lang="en">  
              [Reason]  
            </s:Text>  
          </s:Reason>  
        </s:Fault>  
      </s:Body>  
    </s:Envelope>  
    ```  
  
### <a name="ws-addressing-faults"></a>Falhas de WS-Addressing.  
 Como o WS-Reliable Messaging usa WS-Addressing, implementação de WCF WS-Reliable Messaging pode gerar falhas de WS-Addressing. Esta seção aborda as falhas de WS-Addressing que o WCF gera explicitamente na camada de mensagens WS-Reliable:  
  
- B1601:WCF gera a falha de mensagem de cabeçalho de endereçamento necessário quando uma das seguintes opções for verdadeira:  
  
    - Uma mensagem está falta uma `Sequence` cabeçalho e um `Action` cabeçalho.  
  
    - Um `CreateSequence` mensagem está falta um `MessageId` cabeçalho.  
  
    - Um `CreateSequence` mensagem está falta um `ReplyTo` cabeçalho.  
  
- B1602:WCF gera a falha de ação não tem suporte em resposta uma mensagem que está falta uma `Sequence` cabeçalho e tem um `Action` cabeçalho não é reconhecido na especificação WS-Reliable Messaging.  
  
- B1603:WCF gera a falha de ponto de extremidade não está disponível para indicar que o ponto de extremidade não processar a sequência com base no exame do `CreateSequence` cabeçalhos de endereçamento da mensagem.  
  
## <a name="protocol-composition"></a>Composição de protocolo  
  
### <a name="composition-with-ws-addressing"></a>Composição com o WS-Addressing.  
 O WCF oferece suporte a duas versões do WS-Addressing: 2004 de WS-Addressing/08 [WS-ADDR] e W3C WS-Addressing 1.0 recomendações [WS-ADDR-CORE] e [WS-ADDR SOAP].  
  
 Embora as menções da especificação WS-Reliable Messaging 08/somente 2004 de WS-Addressing, ele não restringe a versão de WS-Addressing a ser usado. A seguir está uma lista de restrições que se aplicam ao WCF:  
  
- R2101: ambos os 08/2004 de WS-Addressing e WS-Addressing 1.0 podem ser usado com o WS-Reliable Messaging.  
  
- R2102:A única versão do WS-Addressing deve ser usado ao longo de uma determinada sequência de WS-Reliable Messaging ou um par de sequências inverso correlacionados usando o `wsrm:Offer` mecanismo.  
  
### <a name="composition-with-soap"></a>Composição com SOAP  
 WCF oferece suporte ao uso de SOAP 1.1 e SOAP 1.2 com o WS-Reliable Messaging.  
  
### <a name="composition-with-ws-security-and-ws-secureconversation"></a>Composição com o WS-Security e WS-SecureConversation  
 WCF fornece proteção para as sequências de WS-Reliable Messaging com o uso seguro de transporte (HTTPS), composição com o WS-Security e composição com o WS-Secure Conversation. A seguir está uma lista de restrições que se aplicam ao WCF:  
  
- R2301: para proteger a integridade de uma sequência de mensagens WS-Reliable, além da integridade e a confidencialidade das mensagens individuais, o WCF exige que o WS-Secure Conversation deve ser usada.  
  
- R2302:AWS-Secure Conversation deve ser estabelecida antes de estabelecer a sequência de mensagens WS-Reliable.  
  
- R2303: Se o tempo de vida de sequência de mensagens WS-Reliable exceder o WS-Secure Conversation tempo de vida da sessão, o `SecurityContextToken` estabelecida usando WS-Secure Conversation devem ser renovada por meio de associação de WS-Secure Conversation renovação correspondente.  
  
- B2304:ws-sequência de mensagens confiáveis ou um par de sequências inverso correlacionados sempre são associados a uma única sessão do WS-SecureConversation.  
  
     A origem do WCF gera o `wsse:SecurityTokenReference` elemento na seção de extensibilidade do elemento da `CreateSequence` mensagem.  
  
- R2305:when composto com o WS-Secure Conversation, uma `CreateSequence` mensagem deve conter o `wsse:SecurityTokenReference` elemento.  
  
## <a name="ws-reliable-messaging-ws-policy-assertion"></a>Declaração de WS-Policy mensagens WS-Reliable  
 O WCF usa WS-Reliable Messaging asserção de WS-Policy `wsrm:RMAssertion` para descrever os recursos de pontos de extremidade. A seguir está uma lista de restrições que se aplicam ao WCF:  
  
- B3001: O WCF anexa `wsrm:RMAssertion` declaração de política WS para `wsdl:binding` elementos. O WCF oferece suporte a ambos os anexos `wsdl:binding` e `wsdl:port` elementos.  
  
- B3002: WCF suporta as seguintes propriedades opcionais de asserção de WS-Reliable Messaging e fornece controle sobre eles em WCF`ReliableMessagingBindingElement`:  
  
    - `wsrm:InactivityTimeout`  
  
    - `wsrm:AcknowledgementInterval`  
  
     Confira o exemplo abaixo.  
  
    ```xml  
    <wsrm:RMAssertion>  
      <wsrm:InactivityTimeout Milliseconds="600000" />  
      <wsrm:AcknowledgementInterval Milliseconds="200" />  
    </wsrm:RMAssertion>  
    ```  
  
## <a name="flow-control-ws-reliable-messaging-extension"></a>Extensão de WS-Reliable Messaging do fluxo de controle  
 O WCF usa WS-Reliable Messaging extensibilidade para proporcionar um controle adicional opcional sobre o fluxo de mensagem de sequência.  
  
 Controle de fluxo é habilitado definindo o <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.FlowControlEnabled?displayProperty=nameWithType> propriedade para `true`. A seguir está uma lista de restrições que se aplicam ao WCF:  
  
- B4001: Quando confiável fluxo de controle de mensagens está habilitado, o WCF gera uma `netrm:BufferRemaining` elemento de extensibilidade do elemento a `SequenceAcknowledgement` cabeçalho.  
  
- B4002: Quando confiável fluxo de controle de mensagens está habilitado, o WCF não exige uma `netrm:BufferRemaining` elemento esteja presente em `SequenceAcknowledgement` cabeçalho, conforme mostrado no exemplo a seguir.  
  
    ```xml  
    <wsrm:SequenceAcknowledgement>  
      <wsrm:Identifier>  
        http://fabrikam123.com/abc  
      </wsrm:Identifier>  
      <wsrm:AcknowledgementRange Upper="1" Lower="1"/>             
      <netrm:BufferRemaining>  
        8  
      </netrm:BufferRemaining>  
    </wsrm:SequenceAcknowledgement>  
    ```  
  
- B4003: O WCF usa `netrm:BufferRemaining` indicar quantas mensagens novo destino de mensagens confiável pode armazenar em buffer.  
  
- B4004: O serviço de mensagens confiável WCF limita o número de mensagens transmitidas quando o aplicativo de destino do sistema de mensagens confiável não pode receber mensagens rapidamente. As mensagens de buffers do destino de sistema de mensagens confiável e o valor do elemento cai a 0.  
  
- B4005: O WCF gera `netrm:BufferRemaining` inteiro de valores entre 0 e 4096 inclusivo e lê os valores de número inteiro entre 0 e `xs:int`do `maxInclusive` 214748364 inclusivo de valor.  
  
## <a name="message-exchange-patterns"></a>Padrões de troca de mensagem  
 Esta seção descreve o comportamento do WCF ao WS-Reliable Messaging é usado para diferentes padrões de troca de mensagem. Para cada padrão de troca de mensagem, os seguintes cenários de duas implantações são considerados:  
  
- Não endereçável iniciador: Iniciador estiver protegido por firewall. Respondente pode entregar mensagens ao iniciador apenas em respostas HTTP.  
  
- Iniciador endereçável: Iniciador e Respondente podem receber solicitações HTTP; em outras palavras, as duas conexões de HTTP inverso podem ser estabelecidas.  
  
### <a name="one-way-non-addressable-initiator"></a>Iniciador unidirecional, não endereçável  
  
#### <a name="binding"></a>Associação  
 O WCF fornece um padrão de troca de mensagens unidirecional usando uma sequência em um canal HTTP. O WCF usa as solicitações HTTP para transmitir todas as mensagens do RMS para o RMD e a resposta HTTP para transmitir todas as mensagens de RMD para o RMS.  
  
#### <a name="createsequence-exchange"></a>Exchange CreateSequence  
 O iniciador do WCF gera um `CreateSequence` mensagem com nenhuma oferta. Garante que o respondente do WCF a `CreateSequence` não tem nenhuma oferta antes de criar uma sequência. O Respondente WCF respostas para o `CreateSequence` de solicitação com um `CreateSequenceResponse` mensagem.  
  
#### <a name="sequenceacknowledgement"></a>SequenceAcknowledgement  
 O iniciador do WCF processa as confirmações na resposta de todas as mensagens, exceto o `CreateSequence` mensagem e mensagens de falha. O respondente do WCF sempre gera uma confirmação autônoma na resposta para ambos os sequência e `AckRequested` mensagens.  
  
#### <a name="terminatesequence-message"></a>Mensagem TerminateSequence  
 O WCF trata `TerminateSequence` como uma operação unidirecional, que significa que a resposta HTTP tem um corpo vazio e o código de status HTTP 202.  
  
### <a name="one-way-addressable-initiator"></a>Iniciador de uma forma, endereçável  
  
#### <a name="binding"></a>Associação  
 O WCF fornece um padrão de troca de mensagens unidirecional usando uma sequência em uma entrada e um canal de saída Http. O WCF usa as solicitações HTTP para transmitir todas as mensagens. Todas as respostas HTTP tem um corpo vazio e o código de status HTTP 202.  
  
#### <a name="createsequence-exchange"></a>Exchange CreateSequence  
 O iniciador do WCF gera um `CreateSequence` mensagem com nenhuma oferta. O Respondente WCF garante que o `CreateSequence` não tem nenhuma oferta antes de criar uma sequência. Transmite o respondente do WCF a `CreateSequenceResponse` endereçado de mensagem em uma solicitação HTTP com o `ReplyTo` referência de ponto de extremidade.  
  
### <a name="duplex-addressable-initiator"></a>Iniciador de duplex e endereçável  
  
#### <a name="binding"></a>Associação  
 O WCF fornece um padrão de troca de mensagens bidirecional assíncrona totalmente usando duas sequências em uma entrada e um canal de saída HTTP. O WCF usa as solicitações HTTP para transmitir todas as mensagens. Todas as respostas HTTP tem um corpo vazio e o código de status HTTP 202.  
  
#### <a name="createsequence-exchange"></a>Exchange CreateSequence  
 O iniciador do WCF gera um `CreateSequence` mensagem com uma oferta. O Respondente WCF garante que o `CreateSequence` tem uma oferta antes de criar uma sequência. WCF envia o `CreateSequenceResponse` na solicitação HTTP endereçado a `CreateSequence`do `ReplyTo` referência de ponto de extremidade.  
  
#### <a name="sequence-lifetime"></a>Tempo de vida de sequência  
 O WCF trata duas sequências como uma sessão duplex totalmente.  
  
 Ao gerar uma falha que uma sequência de falhas, o WCF espera que o ponto de extremidade remoto para ambas as sequências de falha. Após a leitura de uma falha que uma sequência de falhas, WCF falha em ambas as sequências.  
  
 O WCF pode fechar sua sequência de saída e continuar a processar mensagens em sua sequência de entrada. Por outro lado, o WCF pode processar o fechamento da sequência de entrada e continuar a enviar mensagens em sua sequência de saída.  
  
### <a name="request-reply-non-addressable-initiator"></a>Solicitação-resposta, o iniciador não endereçável  
  
#### <a name="binding"></a>Associação  
 O WCF oferece um unidirecional e padrão de troca de mensagem de solicitação-resposta usando duas sequências em um canal HTTP. O WCF usa as solicitações HTTP para transmitir mensagens da sequência de solicitação e usa as respostas HTTP para transmitir mensagens da sequência de resposta.  
  
#### <a name="createsequence-exchange"></a>Exchange CreateSequence  
 O iniciador do WCF gera um `CreateSequence` mensagem com uma oferta. O Respondente WCF garante que o `CreateSequence` tem uma oferta antes de criar uma sequência. O Respondente WCF respostas para o `CreateSequence` de solicitação com um `CreateSequenceResponse` mensagem.  
  
#### <a name="one-way-message"></a>Mensagem unidirecional  
 Para concluir com êxito um protocolo de troca de mensagens unidirecional, o iniciador de WCF transmite uma mensagem de sequência de solicitação na solicitação HTTP e recebe um autônomo `SequenceAcknowledgement` mensagem de resposta HTTP. O `SequenceAcknowledgement` devem reconhecer a mensagem transmitida.  
  
 O Respondente de WCF pode responder à solicitação com uma confirmação, uma falha ou uma resposta com um corpo vazio e o código de status HTTP 202.  
  
#### <a name="two-way-messages"></a>Duas mensagens de forma  
 Para concluir um protocolo de troca de mensagem de duas vias com êxito, o iniciador de WCF transmite uma mensagem de sequência de solicitação na solicitação HTTP e recebe uma mensagem de resposta de sequência na resposta HTTP. A resposta deve conter um `SequenceAcknowledgement` confirmando a mensagem de sequência de solicitação transmitida.  
  
 O Respondente de WCF pode responder à solicitação com uma resposta do aplicativo, uma falha ou uma resposta com um corpo vazio e o código de status HTTP 202.  
  
 Devido à presença de mensagens unidirecional e o tempo de respostas do aplicativo, o número de sequência da mensagem de sequência de solicitação e o número de sequência da mensagem de resposta não têm nenhuma correlação.  
  
#### <a name="retrying-replies"></a>Repetir respostas  
 O WCF conta com correlação de solicitação-resposta HTTP para correlação de protocolo de troca de mensagens bidirecional. Por isso, o iniciador do WCF não interrompe a tentar novamente uma mensagem de sequência de solicitação quando a mensagem de sequência de solicitação é confirmada, mas em vez disso, se a resposta HTTP executa uma confirmação, a mensagem do usuário ou a falha. O Respondente WCF repetições de respostas sobre o segmento de solicitação HTTP da solicitação à qual a resposta está correlacionada.  
  
#### <a name="lastmessage-exchange"></a>Exchange LastMessage  
 O iniciador do WCF gera e transmite uma mensagem de último corpo vazia no trecho de solicitação do HTTP. WCF requer uma resposta, mas ignora a mensagem de resposta real. As respostas de respondente do WCF a vazio incorporada última mensagem da sequência de solicitação com corpo vazio última mensagem da sequência de resposta.  
  
 Se o Respondente WCF recebe uma mensagem de última em que o URI da ação não é `http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage`, respostas WCF com uma última mensagem de erro. No caso de um protocolo de troca de mensagens bidirecional, a última mensagem leva a mensagem de aplicativo; no caso de um protocolo de troca de mensagens unidirecional, a última mensagem está vazia.  
  
 O respondente do WCF não exige uma confirmação para incorporada vazio última mensagem da sequência de resposta.  
  
#### <a name="terminatesequence-exchange"></a>Exchange TerminateSequence  
 Quando todas as solicitações recebeu uma resposta válida, o iniciador do WCF gera e transmite a sequência de solicitação `TerminateSequence` mensagem sobre o segmento de solicitação HTTP. WCF requer uma resposta, mas ignora a mensagem de resposta real. O Respondente WCF responde à sequência de solicitação `TerminateSequence` mensagem com a sequência de resposta `TerminateSequence` mensagem.  
  
 Em uma sequência de desligamento normal, ambos `TerminateSequence` as mensagens carregam uma gama completa `SequenceAcknowledgement`.  
  
### <a name="requestreply-addressable-initiator"></a>Solicitação/resposta, o iniciador endereçável  
  
#### <a name="binding"></a>Associação  
 O WCF fornece um padrão de troca de mensagem de solicitação-resposta usando duas sequências em uma entrada e um canal de saída HTTP. O WCF usa as solicitações HTTP para transmitir todas as mensagens. Todas as respostas HTTP tem um corpo vazio e o código de status HTTP 202.  
  
#### <a name="createsequence-exchange"></a>Exchange CreateSequence  
 O iniciador do WCF gera um `CreateSequence` mensagem com uma oferta. O Respondente WCF garante que o `CreateSequence` tem uma oferta antes de criar uma sequência. WCF envia o `CreateSequenceResponse` na solicitação HTTP endereçado a `CreateSequence`do `ReplyTo` referência de ponto de extremidade.  
  
#### <a name="requestreply-correlation"></a>Correlação de solicitação/resposta  
 Todos os urso de mensagens de solicitação de aplicativo garante que o iniciador do WCF uma `MessageId` e um `ReplyTo` referência de ponto de extremidade. O iniciador do WCF se aplica a `CreateSequence` da mensagem `ReplyTo` referência de ponto de extremidade em cada mensagem de solicitação do aplicativo. O Respondente WCF requer essa solicitação de entrada mensagens urso uma `MessageId` e um `ReplyTo`. O Respondente WCF garante que o URI da referência do ponto de extremidade de ambos os `CreateSequence` e todas as mensagens de solicitação de aplicativo são idênticas.
