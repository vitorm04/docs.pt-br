---
title: "Protocolo de mensagens confiável versão 1.0"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a5509a5c-de24-4bc2-9a48-19138055dcce
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a32c16067446459817e9943c2d729a67373a0333
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="reliable-messaging-protocol-version-10"></a>Protocolo de mensagens confiável versão 1.0
Este tópico aborda [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] detalhes de implementação para mensagens WS-Reliable de fevereiro de 2005 (versão 1.0) protocolo necessárias para a interoperação usando o transporte HTTP. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]segue a especificação de mensagens WS-Reliable com as restrições e esclarecimentos explicados neste tópico. Observe que o protocolo do WS-ReliableMessaging versão 1.0 é implementado começando com o [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)].  
  
 As mensagens WS-Reliable de fevereiro de 2005 protocolo é implementado em [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] pelo <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>.  
  
 Para sua conveniência, o tópico usa as seguintes funções:  
  
-   Iniciador: o cliente que inicia a criação de sequência de mensagem WS-Reliable  
  
-   Respondente: o serviço que recebe solicitações do iniciador  
  
 Este documento usa os namespaces e prefixos na tabela a seguir.  
  
|Prefixo|Namespace|  
|------------|---------------|  
|WSRM|http://schemas.xmlsoap.org/ws/2005/02/RM|  
|netrm|http://schemas.microsoft.com/WS/2006/05/RM|  
|s|http://www.w3.org/2003/05/SOAP-envelope|  
|wsa|http://schemas.xmlsoap.org/ws/2005/08/Addressing|  
|wsse|http://docs.oasis-open.org/WSS/2004/01/OASIS-200401-wssecurity-secext-1.0.xsd|  
  
## <a name="messaging"></a>Mensagens  
  
### <a name="sequence-establishment-messages"></a>Mensagens de estabelecimento de sequência  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]implementa `CreateSequence` e `CreateSequenceResponse` mensagens para estabelecer uma sequência de mensagens confiável. As seguintes restrições se aplicam:  
  
-   B1101: O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] iniciador não gera o elemento Expires opcional no `CreateSequence` mensagem ou, nos casos quando o `CreateSequence` mensagem contém um `Offer` elemento, opcional `Expires` elemento no `Offer` elemento.  
  
-   B1102: Ao acessar o `CreateSequence` mensagem, o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] `Responder` envia e recebe ambos `Expires` se eles existem, mas não usa os valores de elementos.  
  
 Mensagens WS-Reliable apresenta o `Offer` mecanismo para estabelecer os dois conversam correlacionadas sequências que formam uma sessão.  
  
-   R1103: Se `CreateSequence` contém um `Offer` elemento, o Respondente confiável de mensagens deve a aceitar a sequência e responder com `CreateSequenceResponse` que contém um `wsrm:Accept` elemento, cria dois correlacionados conversar sequências ou rejeitar o `CreateSequence` solicitação.  
  
-   R1104: `SequenceAcknowledgement` e mensagens de aplicativo que fluem em sequência inverso devem ser enviadas para o `ReplyTo` referência de ponto de extremidade do `CreateSequence`.  
  
-   R1105: `AcksTo` e `ReplyTo` referências de ponto de extremidade no `CreateSequence` devem ter valores de endereço que correspondem a octet-wise.  
  
     O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] respondente verifica se a parte do URI do `AcksTo` e `ReplyTo` EPRs são idênticos antes de criar uma sequência.  
  
-   R1106: `AcksTo` e `ReplyTo` referências de ponto de extremidade no `CreateSequence` devem ter o mesmo conjunto de parâmetros de referência.  
  
     [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]não impõe mas presume que [parâmetros de referência] de `AcksTo` e `ReplyTo` na `CreateSequence` são idêntico e usa [referência parâmetros] do `ReplyTo` referência de ponto de extremidade para confirmações e mensagens na sequência inverso.  
  
-   R1107: Quando dois conversam sequências estabelecidas usando o `Offer` mecanismo, `SequenceAcknowledgement` e mensagens de aplicativo que fluem em sequências inverso devem ser enviadas para o `ReplyTo` referência de ponto de extremidade do `CreateSequence`.  
  
-   R1108: Quando dois conversam sequências estabelecidas usando o mecanismo de oferta, o `[address]` propriedade do `wsrm:AcksTo` elemento filho de referência de ponto de extremidade do `wsrm:Accept` elemento do `CreateSequenceResponse` devem corresponder byte-wise o URI de destino da `CreateSequence`.  
  
-   R1109: Quando dois conversam sequências estabelecidas usando o `Offer` mecanismo, as mensagens enviadas pelo iniciador e confirmações para mensagens pelo respondente deve ser enviada para a mesma referência de ponto de extremidade.  
  
     [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]usa mensagens WS-Reliable estabelecer sessões confiáveis entre o iniciador e respondente. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]da implementação de mensagens WS-Reliable fornece a sessão confiável para unidirecional, solicitação-resposta e completo duplex padrões de mensagens. Mensagens WS-Reliable `Offer` mecanismo `CreateSequence` / `CreateSequenceResponse` lhe permite estabelecer duas sequências inverso correlacionados e fornece um protocolo de sessão que é adequado para todos os pontos de extremidade de mensagens. Porque [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] fornece uma garantia de segurança para uma sessão incluindo proteção de ponta a ponta para integridade de sessão, é prático garantir que se destina à mesma parte de mensagens chegam ao mesmo destino. Isso também permite que inclua-backup de confirmações de sequência em mensagens de aplicativo. Portanto, R1104, R1105 e R1108 as restrições se aplicam a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
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
  
-   B1201:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] gera e acessa os números de sequência não mais que `xs:long`do valor inclusivo máximo, 9223372036854775807.  
  
-   B1202:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sempre gera uma mensagem de última bodied vazio com o URI da ação de http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage.  
  
-   B1203: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] recebe e envia uma mensagem com um cabeçalho de sequência que contém um `LastMessage` elemento desde que o URI da ação não é http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage.  
  
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
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]usa `AckRequested` cabeçalho como um mecanismo de keep-alive. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]não gera opcional `MessageNumber` elemento. Ao receber uma mensagem com um `AckRequested` cabeçalho que contém o `MessageNumber` elemento [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ignora o `MessageNumber` valor do elemento, conforme mostrado no exemplo a seguir.  
  
```xml  
<wsrm:AckRequested>  
  <wsrm:Identifier>  
    urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36  
  </wsrm:Identifier>  
</wsrm:AckRequested>  
```  
  
### <a name="sequenceacknowledgement-header"></a>Cabeçalho SequenceAcknowledgement  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]usa o mecanismo de inclua para confirmações de sequência fornecidas em mensagens WS-Reliable.  
  
-   R1401: Quando dois conversam sequências estabelecidas usando o `Offer` mecanismo, o `SequenceAcknowledgement` cabeçalho pode ser incluído em qualquer mensagem de aplicativo transmitida para o destinatário pretendido.  
  
-   B1402: Quando [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] deve gerar uma confirmação antes de receber as mensagens de sequência (por exemplo, para satisfazer um `AckRequested` mensagem), [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] gera um `SequenceAcknowledgement` cabeçalho que contém o intervalo de 0-0, conforme mostrado a seguir exemplo.  
  
    ```xml  
    <wsrm:SequenceAcknowledgement>  
      <wsrm:Identifier>  
        urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36  
      </wsrm:Identifier>  
      <wsrm:AcknowledgementRange Upper="0" Lower="0"/>  
    </wsrm:SequenceAcknowledgement>  
    ```  
  
-   B1403: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] não gera `SequenceAcknowledgement` cabeçalhos que contêm um `Nack` elemento, mas oferece suporte a `Nack` elementos.  
  
### <a name="ws-reliablemessaging-faults"></a>Falhas de WS-ReliableMessaging.  
 A seguir está uma lista de restrições que se aplicam a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] implementação de mensagens WS-Reliable falhas:  
  
-   B1501: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] não gera `MessageNumberRollover` falhas.  
  
-   B1502:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ponto de extremidade pode gerar `CreateSequenceRefused` conforme descrito na especificação de falhas.  
  
-   O ponto de extremidade do serviço de B1503:when atingir seu limite de conexão e não pode processar novas conexões, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] gera adicional `CreateSequenceRefused` falha subcódigo, `netrm:ConnectionLimitReached`, conforme mostrado no exemplo a seguir.  
  
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
 Como mensagens WS-Reliable usa WS-Addressing, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] mensagens WS-Reliable implementação pode gerar falhas de WS-Addressing. Este abrange seção WS-Addressing falhas que [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] gera explicitamente na camada de mensagens WS-Reliable:  
  
-   B1601:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] gera a falha de mensagem de cabeçalho de endereçamento necessário quando uma das seguintes opções for verdadeira:  
  
    -   Uma mensagem está falta um `Sequence` cabeçalho e um `Action` cabeçalho.  
  
    -   Um `CreateSequence` mensagem está falta um `MessageId` cabeçalho.  
  
    -   Um `CreateSequence` mensagem está falta um `ReplyTo` cabeçalho.  
  
-   B1602:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] gera a falha de ação não tem suporte em resposta a uma mensagem que está falta um `Sequence` cabeçalho e tem um `Action` cabeçalho não é reconhecido na especificação de mensagens WS-Reliable.  
  
-   B1603:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] gera a falha do ponto de extremidade não está disponível para indicar que o ponto de extremidade não processar a sequência com base na análise do `CreateSequence` cabeçalhos de endereçamento da mensagem.  
  
## <a name="protocol-composition"></a>Composição de protocolo  
  
### <a name="composition-with-ws-addressing"></a>Composição com WS-Addressing.  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]dá suporte a duas versões do WS-Addressing: 2004 do WS-Addressing/08 [WS-ADDR] e recomendações de 1.0 W3C WS-Addressing [WS-ADDR-CORE] e [WS-ADDR-SOAP].  
  
 Enquanto as menções de especificação de mensagens WS-Reliable 2004 do WS-Addressing somente/08, não restringe a versão de WS-Addressing a ser usada. A seguir está uma lista de restrições que se aplicam a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:  
  
-   R2101: os dois 08/2004 do WS-Addressing e WS-Addressing 1.0 podem ser usado com mensagens WS-Reliable.  
  
-   A única versão R2102:A do WS-Addressing deve ser usada ao longo de uma sequência de mensagens WS-Reliable determinada ou um par de sequências inverso correlacionados usando o `wsrm:Offer` mecanismo.  
  
### <a name="composition-with-soap"></a>Composição de SOAP  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]oferece suporte ao uso de SOAP 1.1 e SOAP 1.2 com mensagens WS-Reliable.  
  
### <a name="composition-with-ws-security-and-ws-secureconversation"></a>Composição com WS-Security e WS-SecureConversation  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]fornece proteção para mensagens WS-Reliable sequências usando segura de transporte (HTTPS), composição com WS-Security e composição com WS-Secure Conversation. A seguir está uma lista de restrições que se aplicam a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:  
  
-   R2301: para proteger a integridade de uma sequência de mensagens WS-Reliable além de integridade e confidencialidade de mensagens individuais, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] requer que o WS-Secure Conversation deve ser usada.  
  
-   R2302:AWS-Secure Conversation deve ser estabelecida antes de estabelecer a sequência de mensagens WS-Reliable.  
  
-   R2303: Se o tempo de vida de sequência de mensagens WS-Reliable excede o WS-Secure Conversation tempo de vida da sessão, o `SecurityContextToken` estabelecida usando o WS-Secure Conversation deve ser renovado usando a associação de WS-Secure Conversation renovação correspondente.  
  
-   B2304:ws-sequência de mensagens confiável ou um par de sequências inverso correlacionado sempre estão associados a uma única sessão do WS-SecureConversation.  
  
     O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] origem gera o `wsse:SecurityTokenReference` elemento na seção de extensibilidade de elemento do `CreateSequence` mensagem.  
  
-   R2305:when composto com WS-Secure Conversation um `CreateSequence` mensagem deve conter o `wsse:SecurityTokenReference` elemento.  
  
## <a name="ws-reliable-messaging-ws-policy-assertion"></a>Declaração de WS-Policy mensagens WS-Reliable  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]usa a asserção de WS-Policy mensagens WS-Reliable `wsrm:RMAssertion` para descrever os recursos de pontos de extremidade. A seguir está uma lista de restrições que se aplicam a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:  
  
-   B3001: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] anexa `wsrm:RMAssertion` asserção de WS-Policy para `wsdl:binding` elementos. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]dá suporte a ambos os anexos para `wsdl:binding` e `wsdl:port` elementos.  
  
-   B3002: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] suporta as seguintes propriedades opcionais de mensagens WS-Reliable asserção e fornece controle sobre eles no [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] `ReliableMessagingBindingElement`:  
  
    -   `wsrm:InactivityTimeout`  
  
    -   `wsrm:AcknowledgementInterval`  
  
     Confira o exemplo abaixo.  
  
    ```xml  
    <wsrm:RMAssertion>  
      <wsrm:InactivityTimeout Milliseconds="600000" />  
      <wsrm:AcknowledgementInterval Milliseconds="200" />  
    </wsrm:RMAssertion>  
    ```  
  
## <a name="flow-control-ws-reliable-messaging-extension"></a>Extensão de controle de fluxo de mensagens WS-Reliable  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]usa mensagens WS-Reliable extensibilidade para fornecer maior controle adicional opcional sobre o fluxo de mensagem de sequência.  
  
 Controle de fluxo é habilitado definindo o `ReliableSessionBindingElement`do `FlowControlEnabled``bool` propriedade `true`. A seguir está uma lista de restrições que se aplicam a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:  
  
-   B4001: Controlar quando o fluxo de mensagens confiável estiver habilitada, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] gera um `netrm:BufferRemaining` a extensibilidade do elemento do elemento de `SequenceAcknowledgement` cabeçalho.  
  
-   B4002: Controlar quando o fluxo de mensagens confiável estiver habilitada, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] não requer um `netrm:BufferRemaining` elemento esteja presente no `SequenceAcknowledgement` cabeçalho, conforme mostrado no exemplo a seguir.  
  
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
  
-   B4003: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usa `netrm:BufferRemaining` indicar quantas novas mensagens de destino de mensagens confiável pode buffer.  
  
-   B4004: O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço de mensagens confiável limita o número de mensagens transmitidas quando o aplicativo de destino de mensagens confiável não pode receber mensagens rapidamente. As mensagens de buffers do destino de sistema de mensagens confiável e o valor do elemento cair para 0.  
  
-   B4005: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] gera `netrm:BufferRemaining` inteiro entre 0 e 4096 inclusivo de valores e lê os valores de número inteiro entre 0 e `xs:int`do `maxInclusive` valor 214748364 inclusivo.  
  
## <a name="message-exchange-patterns"></a>Padrões de troca de mensagem  
 Esta seção descreve [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]do comportamento quando mensagens WS-Reliable é usada por diferentes padrões de troca de mensagem. Para cada padrão de troca de mensagens, os seguintes cenários de duas implantações são considerados:  
  
-   Iniciador não endereçável: Iniciador é protegido por firewall. Respondente pode entregar mensagens para o iniciador somente em respostas HTTP.  
  
-   Iniciador endereçável: Iniciador e Respondente podem ser enviadas solicitações HTTP; em outras palavras, duas conexões de HTTP inverso podem ser estabelecidas.  
  
### <a name="one-way-non-addressable-initiator"></a>Iniciador unidirecional, não endereçável  
  
#### <a name="binding"></a>Associação  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Fornece um padrão de troca de mensagem unidirecional usando uma sequência por um canal HTTP. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]usa as solicitações HTTP para transmitir todas as mensagens do RMS para RMD e a resposta HTTP para transmitir todas as mensagens de RMD com o RMS.  
  
#### <a name="createsequence-exchange"></a>CreateSequence Exchange  
 O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] iniciador gera um `CreateSequence` mensagem com nenhuma oferta. O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Respondente garante o `CreateSequence` não tem nenhuma oferta antes de criar uma sequência. O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Respondente responde a `CreateSequence` solicitação com um `CreateSequenceResponse` mensagem.  
  
#### <a name="sequenceacknowledgement"></a>SequenceAcknowledgement  
 O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] iniciador processa as confirmações na resposta de todas as mensagens, exceto o `CreateSequence` mensagem e mensagens de falha. O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Respondente sempre gera uma mensagem de confirmação autônoma na resposta para ambos os sequência e `AckRequested` mensagens.  
  
#### <a name="terminatesequence-message"></a>Mensagem TerminateSequence  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]trata `TerminateSequence` como uma operação unidirecional, que significa que a resposta HTTP tem um corpo vazio e o código de status HTTP 202.  
  
### <a name="one-way-addressable-initiator"></a>Iniciador de uma maneira, endereçável  
  
#### <a name="binding"></a>Associação  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Fornece um padrão de troca de mensagem unidirecional usando uma sequência em uma entrada e um canal de Http de saída. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]usa as solicitações HTTP para transmitir todas as mensagens. Todas as respostas HTTP tem um corpo vazio e o código de status HTTP 202.  
  
#### <a name="createsequence-exchange"></a>CreateSequence Exchange  
 O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] iniciador gera um `CreateSequence` mensagem com nenhuma oferta. O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Respondente garante que o `CreateSequence` não tem nenhuma oferta antes de criar uma sequência. O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Respondente transmite o `CreateSequenceResponse` mensagem em uma solicitação HTTP tratados com o `ReplyTo` referência de ponto de extremidade.  
  
### <a name="duplex-addressable-initiator"></a>Iniciador de duplex, endereçável  
  
#### <a name="binding"></a>Associação  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Fornece um padrão de troca de mensagens bidirecionais totalmente assíncronos usando duas sequências em uma entrada e um canal de HTTP de saída. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]usa as solicitações HTTP para transmitir todas as mensagens. Todas as respostas HTTP tem um corpo vazio e o código de status HTTP 202.  
  
#### <a name="createsequence-exchange"></a>CreateSequence Exchange  
 O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] iniciador gera um `CreateSequence` mensagem com uma oferta. O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Respondente garante que o `CreateSequence` tem uma oferta antes de criar uma sequência. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]envia o `CreateSequenceResponse` na solicitação HTTP endereçado a `CreateSequence`do `ReplyTo` referência de ponto de extremidade.  
  
#### <a name="sequence-lifetime"></a>Tempo de vida de sequência  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]trata as duas sequências como uma sessão duplex totalmente.  
  
 Após a geração de uma falha que falhas de uma sequência, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] espera que o ponto de extremidade remoto para ambas as sequências de falha. Após a leitura de uma falha que falhas de uma sequência, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ambas as sequências de falhas.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Feche a sequência de saída e continuar a processar mensagens em sua sequência de entrada. Por outro lado, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] pode processar o fechamento da sequência de entrada e continuar a enviar mensagens em sua sequência de saída.  
  
### <a name="request-reply-non-addressable-initiator"></a>Solicitação-resposta, o iniciador não endereçável  
  
#### <a name="binding"></a>Associação  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Fornece um padrão de troca de mensagem unidirecional e de solicitação-resposta usando duas sequências em um canal HTTP. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]usa as solicitações HTTP para transmitir mensagens na sequência de solicitação e usa as respostas HTTP para transmitir mensagens da sequência de resposta.  
  
#### <a name="createsequence-exchange"></a>CreateSequence Exchange  
 O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] iniciador gera um `CreateSequence` mensagem com uma oferta. O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Respondente garante que o `CreateSequence` tem uma oferta antes de criar uma sequência. O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Respondente responde a `CreateSequence` solicitação com um `CreateSequenceResponse` mensagem.  
  
#### <a name="one-way-message"></a>Mensagem unidirecional  
 Para concluir um protocolo de intercâmbio de mensagens unidirecional com êxito, o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] iniciador transmite uma mensagem de sequência de solicitação na solicitação HTTP e recebe um autônomo `SequenceAcknowledgement` mensagem na resposta HTTP. O `SequenceAcknowledgement` deve reconhecer a mensagem transmitida.  
  
 O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Respondente pode responder à solicitação com uma resposta com um corpo vazio e o código de status HTTP 202, uma falha ou uma confirmação.  
  
#### <a name="two-way-messages"></a>Duas mensagens de maneira  
 Para concluir um protocolo de intercâmbio de mensagens de duas vias com êxito, o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] iniciador transmite uma mensagem de sequência de solicitação na solicitação HTTP e recebe uma mensagem de sequência de resposta na resposta HTTP. A resposta deve conter um `SequenceAcknowledgement` confirmando a mensagem de sequência de solicitação transmitida.  
  
 O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Respondente pode responder à solicitação com uma resposta do aplicativo, uma falha ou uma resposta com um corpo vazio e o código de status HTTP 202.  
  
 Devido à presença de mensagens unidirecionais e o tempo de respostas de aplicativo, o número de sequência da mensagem de sequência de solicitação e número de sequência da mensagem de resposta não têm nenhuma correlação.  
  
#### <a name="retrying-replies"></a>Repetindo as respostas  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]depende da correlação de solicitação-resposta HTTP para correlação de protocolo de troca de mensagens bidirecional. Por isso, o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] iniciador não parar de tentar novamente uma mensagem de sequência de solicitação quando a mensagem de sequência de solicitação é confirmada, mas em vez disso, quando a resposta HTTP executa uma confirmação, a mensagem de usuário ou a falha. O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Respondente repete as respostas no trecho de solicitação HTTP da solicitação para o qual a resposta correlacionada.  
  
#### <a name="lastmessage-exchange"></a>Exchange LastMessage  
 O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] iniciador gera e transmite uma mensagem de última bodied vazia no trecho de solicitação HTTP. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]requer uma resposta, mas ignora a mensagem de resposta real. O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Respondente respostas para bodied vazio última mensagem a sequência solicitação com bodied vazio última mensagem da sequência de resposta.  
  
 Se o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Respondente recebe uma mensagem de última em que o URI da ação não é http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] responde com uma mensagem de última. No caso de um protocolo de intercâmbio de mensagens bidirecionais, a última mensagem transmite a mensagem de aplicativo. no caso de um protocolo de intercâmbio de mensagens unidirecional, a última mensagem está vazia.  
  
 O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Respondente não requer uma confirmação para bodied vazio última mensagem da sequência de resposta.  
  
#### <a name="terminatesequence-exchange"></a>TerminateSequence Exchange  
 Quando todas as solicitações recebeu uma resposta válida, o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] iniciador gera e transmite a sequência de solicitação `TerminateSequence` mensagem no trecho de solicitação HTTP. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]requer uma resposta, mas ignora a mensagem de resposta real. O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Respondente respostas para a sequência de solicitação `TerminateSequence` mensagem com a sequência de resposta `TerminateSequence` mensagem.  
  
 Em uma sequência de desligamento normal, ambos `TerminateSequence` mensagens carregam uma gama completa `SequenceAcknowledgement`.  
  
### <a name="requestreply-addressable-initiator"></a>Solicitação/resposta, o iniciador endereçável  
  
#### <a name="binding"></a>Associação  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Fornece um padrão de troca de mensagem de solicitação-resposta usando duas sequências em uma entrada e um canal de HTTP de saída. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]usa as solicitações HTTP para transmitir todas as mensagens. Todas as respostas HTTP tem um corpo vazio e o código de status HTTP 202.  
  
#### <a name="createsequence-exchange"></a>CreateSequence Exchange  
 O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] iniciador gera um `CreateSequence` mensagem com uma oferta. O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Respondente garante que o `CreateSequence` tem uma oferta antes de criar uma sequência. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]envia o `CreateSequenceResponse` na solicitação HTTP endereçado a `CreateSequence`do `ReplyTo` referência de ponto de extremidade.  
  
#### <a name="requestreply-correlation"></a>Correlação de solicitação/resposta  
 O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] iniciador garante que todos os lembre de mensagens de solicitação de aplicativo um `MessageId` e um `ReplyTo` referência de ponto de extremidade. O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] iniciador se aplica a `CreateSequence` da mensagem `ReplyTo` referência de ponto de extremidade em cada mensagem de solicitação do aplicativo. O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Respondente requer mensagens de solicitação de entrada tenha uma `MessageId` e um `ReplyTo`. O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Respondente garante que o URI da referência de ponto de extremidade de ambos os `CreateSequence` e todas as mensagens de solicitação de aplicativo são idênticas.
