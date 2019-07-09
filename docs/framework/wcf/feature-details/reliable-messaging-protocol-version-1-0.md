---
title: Protocolo de mensagens confiável versão 1.0
ms.date: 03/30/2017
ms.assetid: a5509a5c-de24-4bc2-9a48-19138055dcce
ms.openlocfilehash: 6fceb49d107e4268a4b9fad6197335ff9e2af9ab
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67662803"
---
# <a name="reliable-messaging-protocol-version-10"></a><span data-ttu-id="b411b-102">Protocolo de mensagens confiável versão 1.0</span><span class="sxs-lookup"><span data-stu-id="b411b-102">Reliable Messaging Protocol version 1.0</span></span>

<span data-ttu-id="b411b-103">Este tópico abrange detalhes de implementação do Windows Communication Foundation (WCF) para o WS-Reliable Messaging necessárias para usar o transporte HTTP de interoperação de protocolo de fevereiro de 2005 (versão 1.0).</span><span class="sxs-lookup"><span data-stu-id="b411b-103">This topic covers Windows Communication Foundation (WCF) implementation details for the WS-Reliable Messaging February 2005 (version 1.0) protocol necessary for interoperation using the HTTP transport.</span></span> <span data-ttu-id="b411b-104">WCF segue a especificação WS-Reliable Messaging com as restrições e esclarecimentos explicados neste tópico.</span><span class="sxs-lookup"><span data-stu-id="b411b-104">WCF follows the WS-Reliable Messaging specification with the constraints and clarifications explained in this topic.</span></span> <span data-ttu-id="b411b-105">Observe que o protocolo de versão 1.0 WS-ReliableMessaging é implementado começando com o WinFX.</span><span class="sxs-lookup"><span data-stu-id="b411b-105">Note that the WS-ReliableMessaging version 1.0 protocol is implemented starting with the WinFX.</span></span>

<span data-ttu-id="b411b-106">O WS-Reliable Messaging de fevereiro de 2005 protocolo é implementado no WCF, o <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="b411b-106">The WS-Reliable Messaging February 2005 protocol is implemented in WCF by the <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>.</span></span>

<span data-ttu-id="b411b-107">Para sua conveniência, o tópico usa as seguintes funções:</span><span class="sxs-lookup"><span data-stu-id="b411b-107">For convenience, the topic uses the following roles:</span></span>

- <span data-ttu-id="b411b-108">Iniciador: o cliente que inicia a criação da sequência de mensagens WS-Reliable</span><span class="sxs-lookup"><span data-stu-id="b411b-108">Initiator: the client that initiates WS-Reliable Message sequence creation</span></span>

- <span data-ttu-id="b411b-109">Respondente: o serviço que recebe solicitações do iniciador</span><span class="sxs-lookup"><span data-stu-id="b411b-109">Responder: the service that receives the initiator's requests</span></span>

<span data-ttu-id="b411b-110">Este documento usa os prefixos e namespaces na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="b411b-110">This document uses the prefixes and namespaces in the following table.</span></span>

|<span data-ttu-id="b411b-111">Prefixo</span><span class="sxs-lookup"><span data-stu-id="b411b-111">Prefix</span></span>|<span data-ttu-id="b411b-112">Namespace</span><span class="sxs-lookup"><span data-stu-id="b411b-112">Namespace</span></span>|
|------------|---------------|
|<span data-ttu-id="b411b-113">wsrm</span><span class="sxs-lookup"><span data-stu-id="b411b-113">wsrm</span></span>|http://schemas.xmlsoap.org/ws/2005/02/rm|
|<span data-ttu-id="b411b-114">netrm</span><span class="sxs-lookup"><span data-stu-id="b411b-114">netrm</span></span>|http://schemas.microsoft.com/ws/2006/05/rm|
|<span data-ttu-id="b411b-115">s</span><span class="sxs-lookup"><span data-stu-id="b411b-115">s</span></span>|http://www.w3.org/2003/05/soap-envelope|
|<span data-ttu-id="b411b-116">wsa</span><span class="sxs-lookup"><span data-stu-id="b411b-116">wsa</span></span>|http://schemas.xmlsoap.org/ws/2005/08/addressing|
|<span data-ttu-id="b411b-117">wsse</span><span class="sxs-lookup"><span data-stu-id="b411b-117">wsse</span></span>|http://docs.oasis-open.org/wss/2004/01/oasis-200401-wssecurity-secext-1.0.xsd|

## <a name="messaging"></a><span data-ttu-id="b411b-118">Mensagens</span><span class="sxs-lookup"><span data-stu-id="b411b-118">Messaging</span></span>

### <a name="sequence-establishment-messages"></a><span data-ttu-id="b411b-119">Mensagens de estabelecimento de sequência</span><span class="sxs-lookup"><span data-stu-id="b411b-119">Sequence Establishment Messages</span></span>

<span data-ttu-id="b411b-120">O WCF implementa `CreateSequence` e `CreateSequenceResponse` mensagens para estabelecer uma sequência de mensagens confiável.</span><span class="sxs-lookup"><span data-stu-id="b411b-120">WCF implements `CreateSequence` and `CreateSequenceResponse` messages to establish a reliable message sequence.</span></span> <span data-ttu-id="b411b-121">As seguintes restrições se aplicam:</span><span class="sxs-lookup"><span data-stu-id="b411b-121">The following constraints apply:</span></span>

- <span data-ttu-id="b411b-122">B1101: O iniciador do WCF não gera o elemento Expires opcional na `CreateSequence` mensagem ou, nos casos quando o `CreateSequence` mensagem contém um `Offer` elemento, opcional `Expires` elemento no `Offer` elemento.</span><span class="sxs-lookup"><span data-stu-id="b411b-122">B1101: The WCF Initiator does not generate the optional Expires element in the `CreateSequence` message or, in the cases when the `CreateSequence` message contains an `Offer` element, the optional `Expires` element in the `Offer` element.</span></span>

- <span data-ttu-id="b411b-123">B1102: Ao acessar o `CreateSequence` da mensagem, o WCF`Responder` envia e recebe ambos `Expires` elementos se eles existirem, mas não usa seus valores.</span><span class="sxs-lookup"><span data-stu-id="b411b-123">B1102: When accessing the `CreateSequence` message, the WCF`Responder` sends and receives both `Expires` elements if they exist, but does not use their values.</span></span>

<span data-ttu-id="b411b-124">WS-Reliable Messaging apresenta o `Offer` mecanismo para estabelecer os dois conversam correlacionadas sequências que formam uma sessão.</span><span class="sxs-lookup"><span data-stu-id="b411b-124">WS-Reliable Messaging introduces the `Offer` mechanism to establish the two converse correlated sequences that form a session.</span></span>

- <span data-ttu-id="b411b-125">R1103: Se `CreateSequence` contém uma `Offer` elemento, o Respondente de mensagens confiável deve aceitar a sequência e responda com `CreateSequenceResponse` que contém um `wsrm:Accept` elemento, formando dois correlacionados conversar sequências ou rejeitar a `CreateSequence`solicitação.</span><span class="sxs-lookup"><span data-stu-id="b411b-125">R1103: If `CreateSequence` contains an `Offer` element, the Reliable Messaging Responder must either accept the sequence and respond with `CreateSequenceResponse` that contains a `wsrm:Accept` element, forming two correlated converse sequences or reject the `CreateSequence` request.</span></span>

- <span data-ttu-id="b411b-126">R1104: `SequenceAcknowledgement` e mensagens de aplicativo que fluem em sequência inverso devem ser enviadas para o `ReplyTo` referência de ponto de extremidade do `CreateSequence`.</span><span class="sxs-lookup"><span data-stu-id="b411b-126">R1104: `SequenceAcknowledgement` and application messages flowing on converse sequence must be sent to the `ReplyTo` endpoint reference of the `CreateSequence`.</span></span>

- <span data-ttu-id="b411b-127">R1105: `AcksTo` e `ReplyTo` referências de ponto de extremidade no `CreateSequence` devem ter valores de endereço que correspondem a octet-wise.</span><span class="sxs-lookup"><span data-stu-id="b411b-127">R1105: `AcksTo` and `ReplyTo` endpoint references in the `CreateSequence` must have address values that match the octet-wise.</span></span>

  <span data-ttu-id="b411b-128">O WCF respondente verifica se a parte do URI de `AcksTo` e `ReplyTo` EPRs são idênticos antes de criar uma sequência.</span><span class="sxs-lookup"><span data-stu-id="b411b-128">The WCF Responder verifies that the URI portion of the `AcksTo` and `ReplyTo` EPRs are identical before creating a sequence.</span></span>

- <span data-ttu-id="b411b-129">R1106: `AcksTo` e `ReplyTo` referências de ponto de extremidade no `CreateSequence` deve ter o mesmo conjunto de parâmetros de referência.</span><span class="sxs-lookup"><span data-stu-id="b411b-129">R1106: `AcksTo` and `ReplyTo` Endpoint References in the `CreateSequence` should have the same set of reference parameters.</span></span>

  <span data-ttu-id="b411b-130">WCF não impõe mas presume que [parâmetros de referência] de `AcksTo` e `ReplyTo` na `CreateSequence` são idênticas e usa [referência parâmetros] do `ReplyTo` referência de ponto de extremidade para as confirmações e mensagens de sequência inverso.</span><span class="sxs-lookup"><span data-stu-id="b411b-130">WCF does not enforce but assumes that [reference parameters] of `AcksTo` and `ReplyTo` on `CreateSequence` are identical and uses [reference parameters] from `ReplyTo` endpoint reference for acknowledgements and converse sequence messages.</span></span>

- <span data-ttu-id="b411b-131">R1107: Quando duas sequências inverso são estabelecidas usando o `Offer` mecanismo, `SequenceAcknowledgement` e mensagens de aplicativo que fluem em sequências inverso devem ser enviadas para o `ReplyTo` referência de ponto de extremidade do `CreateSequence`.</span><span class="sxs-lookup"><span data-stu-id="b411b-131">R1107: When two converse sequences are established using the `Offer` mechanism, `SequenceAcknowledgement` and application messages flowing on converse sequences must be sent to the `ReplyTo` endpoint reference of the `CreateSequence`.</span></span>

- <span data-ttu-id="b411b-132">R1108: Quando duas sequências inverso são estabelecidas usando o mecanismo de oferta, o `[address]` propriedade do `wsrm:AcksTo` elemento filho de referência de ponto de extremidade do `wsrm:Accept` elemento do `CreateSequenceResponse` deve corresponder ao byte-wise o URI de destino do `CreateSequence`.</span><span class="sxs-lookup"><span data-stu-id="b411b-132">R1108: When two converse sequences are established using the Offer mechanism, the `[address]` property of the `wsrm:AcksTo` Endpoint Reference child element of the `wsrm:Accept` element of the `CreateSequenceResponse` must match byte-wise the destination URI of the `CreateSequence`.</span></span>

- <span data-ttu-id="b411b-133">R1109: Quando duas sequências inverso são estabelecidas usando o `Offer` mecanismo, as mensagens enviadas pelo iniciador e confirmações para mensagens pelo respondente devem ser enviadas para a mesma referência de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="b411b-133">R1109: When two converse sequences are established using the `Offer` mechanism, messages sent by initiator and acknowledgements to messages by responder must be sent to the same Endpoint Reference.</span></span>

  <span data-ttu-id="b411b-134">O WCF usa WS-Reliable Messaging para estabelecer sessões confiáveis entre o iniciador e respondente.</span><span class="sxs-lookup"><span data-stu-id="b411b-134">WCF uses WS-Reliable Messaging to establish reliable sessions between the Initiator and Responder.</span></span> <span data-ttu-id="b411b-135">Implementação de WS-Reliable Messaging do WCF fornece sessão confiável para unidirecional, solicitação-resposta e full duplex padrões de mensagens.</span><span class="sxs-lookup"><span data-stu-id="b411b-135">WCF's WS-Reliable Messaging implementation provides reliable session for one-way, request-reply and full duplex messaging patterns.</span></span> <span data-ttu-id="b411b-136">O WS-Reliable Messaging `Offer` mecanismo `CreateSequence` / `CreateSequenceResponse` lhe permite estabelecer duas sequências inverso correlacionados e fornece um protocolo de sessão que é adequado para todos os pontos de extremidade de mensagem.</span><span class="sxs-lookup"><span data-stu-id="b411b-136">The WS-Reliable Messaging `Offer` mechanism on `CreateSequence`/`CreateSequenceResponse` lets you establish two correlated converse sequences, and provides a session protocol that is suitable for all message endpoints.</span></span> <span data-ttu-id="b411b-137">Como o WCF fornece uma garantia de segurança para essa sessão, incluindo a proteção de ponta a ponta para integridade de sessão, é prático garantir que se destina à mesma parte de mensagens chegam ao mesmo destino.</span><span class="sxs-lookup"><span data-stu-id="b411b-137">Because WCF provides a security guarantee for such a session including end-to-end protection for session integrity, it is practical to ensure messages intended to the same party are arriving at the same destination.</span></span> <span data-ttu-id="b411b-138">Isso também permite aproveitando de confirmações de sequência em mensagens do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b411b-138">This also allows piggy-backing of sequence acknowledgements on application messages.</span></span> <span data-ttu-id="b411b-139">Portanto, R1104, R1105 e R1108 de restrições se aplicam ao WCF.</span><span class="sxs-lookup"><span data-stu-id="b411b-139">Therefore, constraints R1104, R1105, and R1108 apply to WCF.</span></span>

<span data-ttu-id="b411b-140">Um exemplo de um `CreateSequence` mensagem.</span><span class="sxs-lookup"><span data-stu-id="b411b-140">An example of a `CreateSequence` message.</span></span>

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

 <span data-ttu-id="b411b-141">Um exemplo de um `CreateSequenceResponse` mensagem.</span><span class="sxs-lookup"><span data-stu-id="b411b-141">An example of a `CreateSequenceResponse` message.</span></span>

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

### <a name="sequence"></a><span data-ttu-id="b411b-142">Sequência</span><span class="sxs-lookup"><span data-stu-id="b411b-142">Sequence</span></span>

<span data-ttu-id="b411b-143">A seguir está uma lista de restrições que se aplicam a sequências:</span><span class="sxs-lookup"><span data-stu-id="b411b-143">The following is a list of constraints that apply to sequences:</span></span>

- <span data-ttu-id="b411b-144">Gera B1201:WCF e maior do que de números de sequência de acessos `xs:long`do valor máximo inclusivo, 9223372036854775807.</span><span class="sxs-lookup"><span data-stu-id="b411b-144">B1201:WCF generates and accesses sequence numbers no higher than `xs:long`’s maximum inclusive value, 9223372036854775807.</span></span>

- <span data-ttu-id="b411b-145">B1202:WCF sempre gera uma mensagem de último incorporada vazio com o URI da ação de `http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage`.</span><span class="sxs-lookup"><span data-stu-id="b411b-145">B1202:WCF always generates an empty-bodied last message with the action URI of `http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage`.</span></span>

- <span data-ttu-id="b411b-146">B1203: O WCF recebe e entrega uma mensagem com um cabeçalho de sequência que contém um `LastMessage` elemento, desde que o URI da ação não é `http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage`.</span><span class="sxs-lookup"><span data-stu-id="b411b-146">B1203: WCF receives and delivers a message with a Sequence header that contains a `LastMessage` element as long as the action URI is not `http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage`.</span></span>

<span data-ttu-id="b411b-147">Um exemplo de um cabeçalho de sequência.</span><span class="sxs-lookup"><span data-stu-id="b411b-147">An example of a Sequence Header.</span></span>

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

### <a name="ackrequested-header"></a><span data-ttu-id="b411b-148">Cabeçalho AckRequested</span><span class="sxs-lookup"><span data-stu-id="b411b-148">AckRequested Header</span></span>

<span data-ttu-id="b411b-149">O WCF usa `AckRequested` cabeçalho como um mecanismo keep-alive.</span><span class="sxs-lookup"><span data-stu-id="b411b-149">WCF uses `AckRequested` Header as a keep-alive mechanism.</span></span> <span data-ttu-id="b411b-150">O WCF não gera opcional `MessageNumber` elemento.</span><span class="sxs-lookup"><span data-stu-id="b411b-150">WCF does not generate the optional `MessageNumber` element.</span></span> <span data-ttu-id="b411b-151">Ao receber uma mensagem com um `AckRequested` cabeçalho que contém o `MessageNumber` WCF de elemento, ignora o `MessageNumber` valor do elemento, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="b411b-151">Upon receiving a message with an `AckRequested` header that contains the `MessageNumber` element, WCF ignores the `MessageNumber` element’s value, as shown in the following example.</span></span>

```xml
<wsrm:AckRequested>
  <wsrm:Identifier>
    urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36
  </wsrm:Identifier>
</wsrm:AckRequested>
```

### <a name="sequenceacknowledgement-header"></a><span data-ttu-id="b411b-152">Cabeçalho SequenceAcknowledgement</span><span class="sxs-lookup"><span data-stu-id="b411b-152">SequenceAcknowledgement Header</span></span>

<span data-ttu-id="b411b-153">WCF usa o mecanismo de transporte-back para confirmações de sequência fornecidas no sistema de mensagens WS-Reliable.</span><span class="sxs-lookup"><span data-stu-id="b411b-153">WCF uses piggy-back mechanism for sequence acknowledgements provided in WS-Reliable Messaging.</span></span>

- <span data-ttu-id="b411b-154">R1401: Quando duas sequências inverso são estabelecidas usando o `Offer` mecanismo, o `SequenceAcknowledgement` cabeçalho pode ser incluído em qualquer mensagem de aplicativo transmitida ao destinatário pretendido.</span><span class="sxs-lookup"><span data-stu-id="b411b-154">R1401: When two converse sequences are established using the `Offer` mechanism, the `SequenceAcknowledgement` header may be included in any application message transmitted to the intended recipient.</span></span>

- <span data-ttu-id="b411b-155">B1402: Quando o WCF deve gerar uma confirmação antes de receber mensagens de qualquer sequência (por exemplo, para atender a um `AckRequested` mensagem), o WCF gera uma `SequenceAcknowledgement` cabeçalho que contém o intervalo de 0-0, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="b411b-155">B1402: When WCF must generate an acknowledgement prior to receiving any sequence messages (for example, to satisfy an `AckRequested` message), WCF generates a `SequenceAcknowledgement` header that contains the range 0-0, as shown in the following example.</span></span>

  ```xml
  <wsrm:SequenceAcknowledgement>
    <wsrm:Identifier>
      urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36
    </wsrm:Identifier>
    <wsrm:AcknowledgementRange Upper="0" Lower="0"/>
  </wsrm:SequenceAcknowledgement>
  ```

- <span data-ttu-id="b411b-156">B1403: O WCF não gera `SequenceAcknowledgement` cabeçalhos que contêm um `Nack` elemento, mas dá suporte a `Nack` elementos.</span><span class="sxs-lookup"><span data-stu-id="b411b-156">B1403: WCF does not generate `SequenceAcknowledgement` headers that contain a `Nack` element but supports `Nack` elements.</span></span>

### <a name="ws-reliablemessaging-faults"></a><span data-ttu-id="b411b-157">Falhas de WS-ReliableMessaging</span><span class="sxs-lookup"><span data-stu-id="b411b-157">WS-ReliableMessaging Faults</span></span>

<span data-ttu-id="b411b-158">A seguir está uma lista de restrições que se aplicam para a implementação de WCF do WS-Reliable Messaging falhas:</span><span class="sxs-lookup"><span data-stu-id="b411b-158">The following is a list of constraints that apply to the WCF implementation of WS-Reliable Messaging faults:</span></span>

- <span data-ttu-id="b411b-159">B1501: O WCF não gera `MessageNumberRollover` falhas.</span><span class="sxs-lookup"><span data-stu-id="b411b-159">B1501: WCF does not generate `MessageNumberRollover` faults.</span></span>

- <span data-ttu-id="b411b-160">Ponto de extremidade B1502:WCF pode gerar `CreateSequenceRefused` conforme descrito na especificação de falhas.</span><span class="sxs-lookup"><span data-stu-id="b411b-160">B1502:WCF endpoint may generate `CreateSequenceRefused` faults as described in the specification.</span></span>

- <span data-ttu-id="b411b-161">B1503:when o ponto de extremidade do serviço atingir seu limite de conexão e não pode processar novas conexões, o WCF gera adicional `CreateSequenceRefused` subcódigo, de falha `netrm:ConnectionLimitReached`, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="b411b-161">B1503:When the service endpoint reaches its connection limit and cannot process new connections, WCF generates an additional `CreateSequenceRefused` fault subcode, `netrm:ConnectionLimitReached`, as shown in the following example.</span></span>

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

### <a name="ws-addressing-faults"></a><span data-ttu-id="b411b-162">Falhas de WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="b411b-162">WS-Addressing Faults</span></span>

<span data-ttu-id="b411b-163">Como o WS-Reliable Messaging usa WS-Addressing, implementação de WCF WS-Reliable Messaging pode gerar falhas de WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="b411b-163">Because WS-Reliable Messaging uses WS-Addressing, WCF WS-Reliable Messaging implementation may generate WS-Addressing faults.</span></span> <span data-ttu-id="b411b-164">Esta seção aborda as falhas de WS-Addressing que o WCF gera explicitamente na camada de mensagens WS-Reliable:</span><span class="sxs-lookup"><span data-stu-id="b411b-164">This section covers the WS-Addressing faults that WCF explicitly generates at the WS-Reliable Messaging layer:</span></span>

- <span data-ttu-id="b411b-165">B1601:WCF gera a falha de mensagem de cabeçalho de endereçamento necessário quando uma das seguintes opções for verdadeira:</span><span class="sxs-lookup"><span data-stu-id="b411b-165">B1601:WCF generates the fault Message Addressing Header Required when one of the following is true:</span></span>

  - <span data-ttu-id="b411b-166">Uma mensagem está falta uma `Sequence` cabeçalho e um `Action` cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="b411b-166">A message is missing a `Sequence` header and an `Action` header.</span></span>

  - <span data-ttu-id="b411b-167">Um `CreateSequence` mensagem está falta um `MessageId` cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="b411b-167">A `CreateSequence` message is missing a `MessageId` header.</span></span>

  - <span data-ttu-id="b411b-168">Um `CreateSequence` mensagem está falta um `ReplyTo` cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="b411b-168">A `CreateSequence` message is missing a `ReplyTo` header.</span></span>

- <span data-ttu-id="b411b-169">B1602:WCF gera a falha de ação não tem suporte em resposta uma mensagem que está falta uma `Sequence` cabeçalho e tem um `Action` cabeçalho não é reconhecido na especificação WS-Reliable Messaging.</span><span class="sxs-lookup"><span data-stu-id="b411b-169">B1602:WCF generates the fault Action Not Supported in reply to a message that is missing a `Sequence` header and has an `Action` header that is not a recognized in the WS-Reliable Messaging specification.</span></span>

- <span data-ttu-id="b411b-170">B1603:WCF gera a falha de ponto de extremidade não está disponível para indicar que o ponto de extremidade não processar a sequência com base no exame do `CreateSequence` cabeçalhos de endereçamento da mensagem.</span><span class="sxs-lookup"><span data-stu-id="b411b-170">B1603:WCF generates the fault Endpoint Unavailable to indicate that the endpoint does not process the sequence based upon examination of the `CreateSequence` message’s addressing headers.</span></span>

## <a name="protocol-composition"></a><span data-ttu-id="b411b-171">Composição de protocolo</span><span class="sxs-lookup"><span data-stu-id="b411b-171">Protocol Composition</span></span>

### <a name="composition-with-ws-addressing"></a><span data-ttu-id="b411b-172">Composição com o WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="b411b-172">Composition with WS-Addressing</span></span>

<span data-ttu-id="b411b-173">O WCF oferece suporte a duas versões do WS-Addressing: 2004 de WS-Addressing/08 [WS-ADDR] e W3C WS-Addressing 1.0 recomendações [WS-ADDR-CORE] e [WS-ADDR SOAP].</span><span class="sxs-lookup"><span data-stu-id="b411b-173">WCF supports two versions of WS-Addressing: WS-Addressing 2004/08 [WS-ADDR] and W3C WS-Addressing 1.0 Recommendations [WS-ADDR-CORE] and [WS-ADDR-SOAP].</span></span>

<span data-ttu-id="b411b-174">Embora as menções da especificação WS-Reliable Messaging 08/somente 2004 de WS-Addressing, ele não restringe a versão de WS-Addressing a ser usado.</span><span class="sxs-lookup"><span data-stu-id="b411b-174">While the WS-Reliable Messaging specification mentions only WS-Addressing 2004/08, it does not restrict the WS-Addressing version to be used.</span></span> <span data-ttu-id="b411b-175">A seguir está uma lista de restrições que se aplicam ao WCF:</span><span class="sxs-lookup"><span data-stu-id="b411b-175">The following is a list of constraints that apply to WCF:</span></span>

- <span data-ttu-id="b411b-176">R2101: ambos os 08/2004 de WS-Addressing e WS-Addressing 1.0 podem ser usado com o WS-Reliable Messaging.</span><span class="sxs-lookup"><span data-stu-id="b411b-176">R2101:Both WS-Addressing 2004/08 and WS-Addressing 1.0 can be used with WS-Reliable Messaging.</span></span>

- <span data-ttu-id="b411b-177">R2102:A única versão do WS-Addressing deve ser usado ao longo de uma determinada sequência de WS-Reliable Messaging ou um par de sequências inverso correlacionados usando o `wsrm:Offer` mecanismo.</span><span class="sxs-lookup"><span data-stu-id="b411b-177">R2102:A single version of WS-Addressing must be used throughout a given WS-Reliable Messaging sequence or a pair of converse sequences correlated by using the `wsrm:Offer` mechanism.</span></span>

### <a name="composition-with-soap"></a><span data-ttu-id="b411b-178">Composição com SOAP</span><span class="sxs-lookup"><span data-stu-id="b411b-178">Composition with SOAP</span></span>

<span data-ttu-id="b411b-179">WCF oferece suporte ao uso de SOAP 1.1 e SOAP 1.2 com o WS-Reliable Messaging.</span><span class="sxs-lookup"><span data-stu-id="b411b-179">WCF supports use of both SOAP 1.1 and SOAP 1.2 with WS-Reliable Messaging.</span></span>

### <a name="composition-with-ws-security-and-ws-secureconversation"></a><span data-ttu-id="b411b-180">Composição com o WS-Security e WS-SecureConversation</span><span class="sxs-lookup"><span data-stu-id="b411b-180">Composition with WS-Security and WS-SecureConversation</span></span>

<span data-ttu-id="b411b-181">WCF fornece proteção para as sequências de WS-Reliable Messaging com o uso seguro de transporte (HTTPS), composição com o WS-Security e composição com o WS-Secure Conversation.</span><span class="sxs-lookup"><span data-stu-id="b411b-181">WCF provides protection for WS-Reliable Messaging sequences by using secure Transport (HTTPS), composition with WS-Security, and composition with WS-Secure Conversation.</span></span> <span data-ttu-id="b411b-182">A seguir está uma lista de restrições que se aplicam ao WCF:</span><span class="sxs-lookup"><span data-stu-id="b411b-182">The following is a list of constraints that apply to WCF:</span></span>

- <span data-ttu-id="b411b-183">R2301: para proteger a integridade de uma sequência de mensagens WS-Reliable, além da integridade e a confidencialidade das mensagens individuais, o WCF exige que o WS-Secure Conversation deve ser usada.</span><span class="sxs-lookup"><span data-stu-id="b411b-183">R2301:To protect the integrity of a WS-Reliable Messaging sequence in addition to the integrity and confidentiality of individual messages, WCF requires that WS-Secure Conversation must be used.</span></span>

- <span data-ttu-id="b411b-184">R2302:AWS-Secure Conversation deve ser estabelecida antes de estabelecer a sequência de mensagens WS-Reliable.</span><span class="sxs-lookup"><span data-stu-id="b411b-184">R2302:AWS-Secure Conversation session must be established prior to establishing WS-Reliable Messaging sequence(s).</span></span>

- <span data-ttu-id="b411b-185">R2303: Se o tempo de vida de sequência de mensagens WS-Reliable exceder o WS-Secure Conversation tempo de vida da sessão, o `SecurityContextToken` estabelecida usando WS-Secure Conversation devem ser renovada por meio de associação de WS-Secure Conversation renovação correspondente.</span><span class="sxs-lookup"><span data-stu-id="b411b-185">R2303: If the WS-Reliable Messaging sequence lifetime exceeds the WS-Secure Conversation session’s lifetime, the `SecurityContextToken` established by using WS-Secure Conversation must be renewed by using the corresponding WS-Secure Conversation Renewal binding.</span></span>

- <span data-ttu-id="b411b-186">B2304:ws-sequência de mensagens confiáveis ou um par de sequências inverso correlacionados sempre são associados a uma única sessão do WS-SecureConversation.</span><span class="sxs-lookup"><span data-stu-id="b411b-186">B2304:WS-Reliable Messaging sequence or a pair of correlated converse sequences are always bound to a single WS-SecureConversation session.</span></span>

  <span data-ttu-id="b411b-187">A origem do WCF gera o `wsse:SecurityTokenReference` elemento na seção de extensibilidade do elemento da `CreateSequence` mensagem.</span><span class="sxs-lookup"><span data-stu-id="b411b-187">The WCF source generates the `wsse:SecurityTokenReference` element in the element extensibility section of the `CreateSequence` message.</span></span>

- <span data-ttu-id="b411b-188">R2305:when composto com o WS-Secure Conversation, uma `CreateSequence` mensagem deve conter o `wsse:SecurityTokenReference` elemento.</span><span class="sxs-lookup"><span data-stu-id="b411b-188">R2305:When composed with WS-Secure Conversation, a `CreateSequence` message must contain the `wsse:SecurityTokenReference` element.</span></span>

## <a name="ws-reliable-messaging-ws-policy-assertion"></a><span data-ttu-id="b411b-189">Declaração de WS-Policy mensagens WS-Reliable</span><span class="sxs-lookup"><span data-stu-id="b411b-189">WS-Reliable Messaging WS-Policy Assertion</span></span>

<span data-ttu-id="b411b-190">O WCF usa WS-Reliable Messaging asserção de WS-Policy `wsrm:RMAssertion` para descrever os recursos de pontos de extremidade.</span><span class="sxs-lookup"><span data-stu-id="b411b-190">WCF uses WS-Reliable Messaging WS-Policy Assertion `wsrm:RMAssertion` to describe endpoints capabilities.</span></span> <span data-ttu-id="b411b-191">A seguir está uma lista de restrições que se aplicam ao WCF:</span><span class="sxs-lookup"><span data-stu-id="b411b-191">The following is a list of constraints that apply to WCF:</span></span>

- <span data-ttu-id="b411b-192">B3001: O WCF anexa `wsrm:RMAssertion` declaração de política WS para `wsdl:binding` elementos.</span><span class="sxs-lookup"><span data-stu-id="b411b-192">B3001: WCF attaches `wsrm:RMAssertion` WS-Policy Assertion to `wsdl:binding` elements.</span></span> <span data-ttu-id="b411b-193">O WCF oferece suporte a ambos os anexos `wsdl:binding` e `wsdl:port` elementos.</span><span class="sxs-lookup"><span data-stu-id="b411b-193">WCF supports both attachments to `wsdl:binding` and `wsdl:port` elements.</span></span>

- <span data-ttu-id="b411b-194">B3002: WCF suporta as seguintes propriedades opcionais de asserção de WS-Reliable Messaging e fornece controle sobre eles em WCF`ReliableMessagingBindingElement`:</span><span class="sxs-lookup"><span data-stu-id="b411b-194">B3002: WCF supports the following optional properties of WS-Reliable Messaging assertion and provides control over them on the WCF`ReliableMessagingBindingElement`:</span></span>

  - `wsrm:InactivityTimeout`

  - `wsrm:AcknowledgementInterval`

  <span data-ttu-id="b411b-195">Confira o exemplo abaixo.</span><span class="sxs-lookup"><span data-stu-id="b411b-195">The following is an example.</span></span>

  ```xml
  <wsrm:RMAssertion>
    <wsrm:InactivityTimeout Milliseconds="600000" />
    <wsrm:AcknowledgementInterval Milliseconds="200" />
  </wsrm:RMAssertion>
  ```

## <a name="flow-control-ws-reliable-messaging-extension"></a><span data-ttu-id="b411b-196">Extensão de WS-Reliable Messaging do fluxo de controle</span><span class="sxs-lookup"><span data-stu-id="b411b-196">Flow Control WS-Reliable Messaging Extension</span></span>

<span data-ttu-id="b411b-197">O WCF usa WS-Reliable Messaging extensibilidade para proporcionar um controle adicional opcional sobre o fluxo de mensagem de sequência.</span><span class="sxs-lookup"><span data-stu-id="b411b-197">WCF uses WS-Reliable Messaging extensibility to provide optional additional tighter control over sequence message flow.</span></span>

<span data-ttu-id="b411b-198">Controle de fluxo é habilitado definindo o <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.FlowControlEnabled?displayProperty=nameWithType> propriedade para `true`.</span><span class="sxs-lookup"><span data-stu-id="b411b-198">Flow control is enabled by setting the <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.FlowControlEnabled?displayProperty=nameWithType> property to `true`.</span></span> <span data-ttu-id="b411b-199">A seguir está uma lista de restrições que se aplicam ao WCF:</span><span class="sxs-lookup"><span data-stu-id="b411b-199">The following is a list of constraints that apply to WCF:</span></span>

- <span data-ttu-id="b411b-200">B4001: Quando confiável fluxo de controle de mensagens está habilitado, o WCF gera uma `netrm:BufferRemaining` elemento de extensibilidade do elemento a `SequenceAcknowledgement` cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="b411b-200">B4001: When Reliable Messaging Flow Control is enabled, WCF generates a `netrm:BufferRemaining` element in the element extensibility of the `SequenceAcknowledgement` header.</span></span>

- <span data-ttu-id="b411b-201">B4002: Quando confiável fluxo de controle de mensagens está habilitado, o WCF não exige uma `netrm:BufferRemaining` elemento esteja presente em `SequenceAcknowledgement` cabeçalho, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="b411b-201">B4002: When Reliable Messaging Flow Control is enabled, WCF does not require a `netrm:BufferRemaining` element to be present in `SequenceAcknowledgement` header, as shown in the following example.</span></span>

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

- <span data-ttu-id="b411b-202">B4003: O WCF usa `netrm:BufferRemaining` indicar quantas mensagens novo destino de mensagens confiável pode armazenar em buffer.</span><span class="sxs-lookup"><span data-stu-id="b411b-202">B4003: WCF uses `netrm:BufferRemaining` to indicate how many new messages the Reliable Messaging Destination can buffer.</span></span>

- <span data-ttu-id="b411b-203">B4004: O serviço de mensagens confiável WCF limita o número de mensagens transmitidas quando o aplicativo de destino do sistema de mensagens confiável não pode receber mensagens rapidamente.</span><span class="sxs-lookup"><span data-stu-id="b411b-203">B4004:The WCF Reliable Messaging Service throttles the number of messages transmitted when the Reliable Messaging destination application cannot receive messages quickly.</span></span> <span data-ttu-id="b411b-204">As mensagens de buffers do destino de sistema de mensagens confiável e o valor do elemento cai a 0.</span><span class="sxs-lookup"><span data-stu-id="b411b-204">The Reliable Messaging destination buffers messages and the element’s value drops to 0.</span></span>

- <span data-ttu-id="b411b-205">B4005: O WCF gera `netrm:BufferRemaining` inteiro de valores entre 0 e 4096 inclusivo e lê os valores de número inteiro entre 0 e `xs:int`do `maxInclusive` 214748364 inclusivo de valor.</span><span class="sxs-lookup"><span data-stu-id="b411b-205">B4005: WCF generates `netrm:BufferRemaining` integer values between 0 and 4096 inclusive, and reads integer values between 0 and `xs:int`’s `maxInclusive` value 214748364 inclusive.</span></span>

## <a name="message-exchange-patterns"></a><span data-ttu-id="b411b-206">Padrões de troca de mensagem</span><span class="sxs-lookup"><span data-stu-id="b411b-206">Message Exchange Patterns</span></span>

<span data-ttu-id="b411b-207">Esta seção descreve o comportamento do WCF ao WS-Reliable Messaging é usado para diferentes padrões de troca de mensagem.</span><span class="sxs-lookup"><span data-stu-id="b411b-207">This section describes WCF's behavior when WS-Reliable Messaging is used for different Message Exchange Patterns.</span></span> <span data-ttu-id="b411b-208">Para cada padrão de troca de mensagem, os seguintes cenários de duas implantações são considerados:</span><span class="sxs-lookup"><span data-stu-id="b411b-208">For each Message Exchange Pattern the following two deployments scenarios are considered:</span></span>

- <span data-ttu-id="b411b-209">Não endereçável iniciador: Iniciador estiver protegido por firewall. Respondente pode entregar mensagens ao iniciador apenas em respostas HTTP.</span><span class="sxs-lookup"><span data-stu-id="b411b-209">Non-Addressable Initiator: Initiator is behind firewall; Responder can deliver messages to Initiator only on HTTP responses.</span></span>

- <span data-ttu-id="b411b-210">Iniciador endereçável: Iniciador e Respondente podem receber solicitações HTTP; em outras palavras, as duas conexões de HTTP inverso podem ser estabelecidas.</span><span class="sxs-lookup"><span data-stu-id="b411b-210">Addressable Initiator: Initiator and Responder both can be sent HTTP requests; in other words, two converse HTTP connections can be established.</span></span>

### <a name="one-way-non-addressable-initiator"></a><span data-ttu-id="b411b-211">Iniciador unidirecional, não endereçável</span><span class="sxs-lookup"><span data-stu-id="b411b-211">One-way, Non-addressable Initiator</span></span>

#### <a name="binding"></a><span data-ttu-id="b411b-212">Associação</span><span class="sxs-lookup"><span data-stu-id="b411b-212">Binding</span></span>

<span data-ttu-id="b411b-213">O WCF fornece um padrão de troca de mensagens unidirecional usando uma sequência em um canal HTTP.</span><span class="sxs-lookup"><span data-stu-id="b411b-213">WCF provides a one-way message exchange pattern using one sequence over one HTTP channel.</span></span> <span data-ttu-id="b411b-214">O WCF usa as solicitações HTTP para transmitir todas as mensagens do RMS para o RMD e a resposta HTTP para transmitir todas as mensagens de RMD para o RMS.</span><span class="sxs-lookup"><span data-stu-id="b411b-214">WCF uses the HTTP requests to transmit all messages from the RMS to the RMD and the HTTP response to transmit all messages from the RMD to the RMS.</span></span>

#### <a name="createsequence-exchange"></a><span data-ttu-id="b411b-215">Exchange CreateSequence</span><span class="sxs-lookup"><span data-stu-id="b411b-215">CreateSequence Exchange</span></span>

<span data-ttu-id="b411b-216">O iniciador do WCF gera um `CreateSequence` mensagem com nenhuma oferta.</span><span class="sxs-lookup"><span data-stu-id="b411b-216">The WCF Initiator generates a `CreateSequence` message with no offer.</span></span> <span data-ttu-id="b411b-217">Garante que o respondente do WCF a `CreateSequence` não tem nenhuma oferta antes de criar uma sequência.</span><span class="sxs-lookup"><span data-stu-id="b411b-217">The WCF Responder ensures the `CreateSequence` has no offer before creating a sequence.</span></span> <span data-ttu-id="b411b-218">O Respondente WCF respostas para o `CreateSequence` de solicitação com um `CreateSequenceResponse` mensagem.</span><span class="sxs-lookup"><span data-stu-id="b411b-218">The WCF Responder replies to the `CreateSequence` request with a `CreateSequenceResponse` message.</span></span>

#### <a name="sequenceacknowledgement"></a><span data-ttu-id="b411b-219">SequenceAcknowledgement</span><span class="sxs-lookup"><span data-stu-id="b411b-219">SequenceAcknowledgement</span></span>

<span data-ttu-id="b411b-220">O iniciador do WCF processa as confirmações na resposta de todas as mensagens, exceto o `CreateSequence` mensagem e mensagens de falha.</span><span class="sxs-lookup"><span data-stu-id="b411b-220">The WCF Initiator processes acknowledgements on the reply of all messages except the `CreateSequence` message and fault messages.</span></span> <span data-ttu-id="b411b-221">O respondente do WCF sempre gera uma confirmação autônoma na resposta para ambos os sequência e `AckRequested` mensagens.</span><span class="sxs-lookup"><span data-stu-id="b411b-221">The WCF Responder always generates a stand-alone acknowledgement in the response to both sequence and `AckRequested` messages.</span></span>

#### <a name="terminatesequence-message"></a><span data-ttu-id="b411b-222">Mensagem TerminateSequence</span><span class="sxs-lookup"><span data-stu-id="b411b-222">TerminateSequence message</span></span>

<span data-ttu-id="b411b-223">O WCF trata `TerminateSequence` como uma operação unidirecional, que significa que a resposta HTTP tem um corpo vazio e o código de status HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="b411b-223">WCF treats `TerminateSequence` as a one-way operation, meaning the HTTP response has an empty body and HTTP 202 status code.</span></span>

### <a name="one-way-addressable-initiator"></a><span data-ttu-id="b411b-224">Iniciador de uma forma, endereçável</span><span class="sxs-lookup"><span data-stu-id="b411b-224">One Way, Addressable Initiator</span></span>

#### <a name="binding"></a><span data-ttu-id="b411b-225">Associação</span><span class="sxs-lookup"><span data-stu-id="b411b-225">Binding</span></span>

<span data-ttu-id="b411b-226">O WCF fornece um padrão de troca de mensagens unidirecional usando uma sequência em uma entrada e um canal de saída Http.</span><span class="sxs-lookup"><span data-stu-id="b411b-226">WCF provides a one-way message exchange pattern using one sequence over an inbound and an outbound Http channel.</span></span> <span data-ttu-id="b411b-227">O WCF usa as solicitações HTTP para transmitir todas as mensagens.</span><span class="sxs-lookup"><span data-stu-id="b411b-227">WCF uses the HTTP requests to transmit all messages.</span></span> <span data-ttu-id="b411b-228">Todas as respostas HTTP tem um corpo vazio e o código de status HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="b411b-228">All HTTP responses have an empty body and HTTP 202 status code.</span></span>

#### <a name="createsequence-exchange"></a><span data-ttu-id="b411b-229">Exchange CreateSequence</span><span class="sxs-lookup"><span data-stu-id="b411b-229">CreateSequence Exchange</span></span>

<span data-ttu-id="b411b-230">O iniciador do WCF gera um `CreateSequence` mensagem com nenhuma oferta.</span><span class="sxs-lookup"><span data-stu-id="b411b-230">The WCF Initiator generates a `CreateSequence` message with no offer.</span></span> <span data-ttu-id="b411b-231">O Respondente WCF garante que o `CreateSequence` não tem nenhuma oferta antes de criar uma sequência.</span><span class="sxs-lookup"><span data-stu-id="b411b-231">The WCF Responder ensures that the `CreateSequence` has no offer before creating a sequence.</span></span> <span data-ttu-id="b411b-232">Transmite o respondente do WCF a `CreateSequenceResponse` endereçado de mensagem em uma solicitação HTTP com o `ReplyTo` referência de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="b411b-232">The WCF Responder transmits the `CreateSequenceResponse` message on an HTTP request addressed with the `ReplyTo` endpoint reference.</span></span>

### <a name="duplex-addressable-initiator"></a><span data-ttu-id="b411b-233">Iniciador de duplex e endereçável</span><span class="sxs-lookup"><span data-stu-id="b411b-233">Duplex, Addressable Initiator</span></span>

#### <a name="binding"></a><span data-ttu-id="b411b-234">Associação</span><span class="sxs-lookup"><span data-stu-id="b411b-234">Binding</span></span>

<span data-ttu-id="b411b-235">O WCF fornece um padrão de troca de mensagens bidirecional assíncrona totalmente usando duas sequências em uma entrada e um canal de saída HTTP.</span><span class="sxs-lookup"><span data-stu-id="b411b-235">WCF provides a fully asynchronous two-way message exchange pattern using two sequences over an inbound and an outbound HTTP channel.</span></span> <span data-ttu-id="b411b-236">O WCF usa as solicitações HTTP para transmitir todas as mensagens.</span><span class="sxs-lookup"><span data-stu-id="b411b-236">WCF uses the HTTP requests to transmit all messages.</span></span> <span data-ttu-id="b411b-237">Todas as respostas HTTP tem um corpo vazio e o código de status HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="b411b-237">All HTTP responses have an empty body and HTTP 202 status code.</span></span>

#### <a name="createsequence-exchange"></a><span data-ttu-id="b411b-238">Exchange CreateSequence</span><span class="sxs-lookup"><span data-stu-id="b411b-238">CreateSequence Exchange</span></span>

<span data-ttu-id="b411b-239">O iniciador do WCF gera um `CreateSequence` mensagem com uma oferta.</span><span class="sxs-lookup"><span data-stu-id="b411b-239">The WCF Initiator generates a `CreateSequence` message with an offer.</span></span> <span data-ttu-id="b411b-240">O Respondente WCF garante que o `CreateSequence` tem uma oferta antes de criar uma sequência.</span><span class="sxs-lookup"><span data-stu-id="b411b-240">The WCF Responder ensures that the `CreateSequence` has an offer before creating a sequence.</span></span> <span data-ttu-id="b411b-241">WCF envia o `CreateSequenceResponse` na solicitação HTTP endereçado a `CreateSequence`do `ReplyTo` referência de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="b411b-241">WCF sends the `CreateSequenceResponse` on the HTTP request addressed to the `CreateSequence`’s `ReplyTo` endpoint reference.</span></span>

#### <a name="sequence-lifetime"></a><span data-ttu-id="b411b-242">Tempo de vida de sequência</span><span class="sxs-lookup"><span data-stu-id="b411b-242">Sequence Lifetime</span></span>

<span data-ttu-id="b411b-243">O WCF trata duas sequências como uma sessão duplex totalmente.</span><span class="sxs-lookup"><span data-stu-id="b411b-243">WCF treats the two sequences as one fully duplex session.</span></span>

<span data-ttu-id="b411b-244">Ao gerar uma falha que uma sequência de falhas, o WCF espera que o ponto de extremidade remoto para ambas as sequências de falha.</span><span class="sxs-lookup"><span data-stu-id="b411b-244">Upon generating a fault that faults one sequence, WCF expects the remote endpoint to fault both sequences.</span></span> <span data-ttu-id="b411b-245">Após a leitura de uma falha que uma sequência de falhas, WCF falha em ambas as sequências.</span><span class="sxs-lookup"><span data-stu-id="b411b-245">Upon reading a fault that faults one sequence, WCF faults both sequences.</span></span>

<span data-ttu-id="b411b-246">O WCF pode fechar sua sequência de saída e continuar a processar mensagens em sua sequência de entrada.</span><span class="sxs-lookup"><span data-stu-id="b411b-246">WCF can close its outbound sequence and continue to process messages on its inbound sequence.</span></span> <span data-ttu-id="b411b-247">Por outro lado, o WCF pode processar o fechamento da sequência de entrada e continuar a enviar mensagens em sua sequência de saída.</span><span class="sxs-lookup"><span data-stu-id="b411b-247">Conversely, WCF can process the close of the inbound sequence and continue to send messages on its outbound sequence.</span></span>

### <a name="request-reply-non-addressable-initiator"></a><span data-ttu-id="b411b-248">Solicitação-resposta, o iniciador não endereçável</span><span class="sxs-lookup"><span data-stu-id="b411b-248">Request-Reply, Non-Addressable Initiator</span></span>

#### <a name="binding"></a><span data-ttu-id="b411b-249">Associação</span><span class="sxs-lookup"><span data-stu-id="b411b-249">Binding</span></span>

<span data-ttu-id="b411b-250">O WCF oferece um unidirecional e padrão de troca de mensagem de solicitação-resposta usando duas sequências em um canal HTTP.</span><span class="sxs-lookup"><span data-stu-id="b411b-250">WCF provides a one-way and request-reply message exchange pattern using two sequences over one HTTP channel.</span></span> <span data-ttu-id="b411b-251">O WCF usa as solicitações HTTP para transmitir mensagens da sequência de solicitação e usa as respostas HTTP para transmitir mensagens da sequência de resposta.</span><span class="sxs-lookup"><span data-stu-id="b411b-251">WCF uses the HTTP requests to transmit the request sequence’s messages and uses the HTTP responses to transmit the reply sequence’s messages.</span></span>

#### <a name="createsequence-exchange"></a><span data-ttu-id="b411b-252">Exchange CreateSequence</span><span class="sxs-lookup"><span data-stu-id="b411b-252">CreateSequence Exchange</span></span>

<span data-ttu-id="b411b-253">O iniciador do WCF gera um `CreateSequence` mensagem com uma oferta.</span><span class="sxs-lookup"><span data-stu-id="b411b-253">The WCF Initiator generates a `CreateSequence` message with an offer.</span></span> <span data-ttu-id="b411b-254">O Respondente WCF garante que o `CreateSequence` tem uma oferta antes de criar uma sequência.</span><span class="sxs-lookup"><span data-stu-id="b411b-254">The WCF Responder ensures that the `CreateSequence` has an offer before creating a sequence.</span></span> <span data-ttu-id="b411b-255">O Respondente WCF respostas para o `CreateSequence` de solicitação com um `CreateSequenceResponse` mensagem.</span><span class="sxs-lookup"><span data-stu-id="b411b-255">The WCF Responder replies to the `CreateSequence` request with a `CreateSequenceResponse` message.</span></span>

#### <a name="one-way-message"></a><span data-ttu-id="b411b-256">Mensagem unidirecional</span><span class="sxs-lookup"><span data-stu-id="b411b-256">One-way Message</span></span>

<span data-ttu-id="b411b-257">Para concluir com êxito um protocolo de troca de mensagens unidirecional, o iniciador de WCF transmite uma mensagem de sequência de solicitação na solicitação HTTP e recebe um autônomo `SequenceAcknowledgement` mensagem de resposta HTTP.</span><span class="sxs-lookup"><span data-stu-id="b411b-257">To complete a one-way message exchange protocol successfully, the WCF Initiator transmits a request sequence message on the HTTP request and receives a standalone `SequenceAcknowledgement` message on the HTTP response.</span></span> <span data-ttu-id="b411b-258">O `SequenceAcknowledgement` devem reconhecer a mensagem transmitida.</span><span class="sxs-lookup"><span data-stu-id="b411b-258">The `SequenceAcknowledgement` must acknowledge the message transmitted.</span></span>

<span data-ttu-id="b411b-259">O Respondente de WCF pode responder à solicitação com uma confirmação, uma falha ou uma resposta com um corpo vazio e o código de status HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="b411b-259">The WCF Responder can reply to the request with an acknowledgement, a fault, or a response with an empty body and HTTP 202 status code.</span></span>

#### <a name="two-way-messages"></a><span data-ttu-id="b411b-260">Duas mensagens de forma</span><span class="sxs-lookup"><span data-stu-id="b411b-260">Two Way Messages</span></span>

<span data-ttu-id="b411b-261">Para concluir um protocolo de troca de mensagem de duas vias com êxito, o iniciador de WCF transmite uma mensagem de sequência de solicitação na solicitação HTTP e recebe uma mensagem de resposta de sequência na resposta HTTP.</span><span class="sxs-lookup"><span data-stu-id="b411b-261">To complete a two way message exchange protocol successfully, the WCF Initiator transmits a request sequence message on the HTTP request and receives a reply sequence message on the HTTP response.</span></span> <span data-ttu-id="b411b-262">A resposta deve conter um `SequenceAcknowledgement` confirmando a mensagem de sequência de solicitação transmitida.</span><span class="sxs-lookup"><span data-stu-id="b411b-262">The response must carry a `SequenceAcknowledgement` acknowledging the request sequence message transmitted.</span></span>

<span data-ttu-id="b411b-263">O Respondente de WCF pode responder à solicitação com uma resposta do aplicativo, uma falha ou uma resposta com um corpo vazio e o código de status HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="b411b-263">The WCF Responder can reply to the request with an application reply, a fault or a response with an empty body and HTTP 202 status code.</span></span>

<span data-ttu-id="b411b-264">Devido à presença de mensagens unidirecional e o tempo de respostas do aplicativo, o número de sequência da mensagem de sequência de solicitação e o número de sequência da mensagem de resposta não têm nenhuma correlação.</span><span class="sxs-lookup"><span data-stu-id="b411b-264">Because of the presence of one-way messages and the timing of application replies, the request sequence message’s sequence number and the response message’s sequence number have no correlation.</span></span>

#### <a name="retrying-replies"></a><span data-ttu-id="b411b-265">Repetir respostas</span><span class="sxs-lookup"><span data-stu-id="b411b-265">Retrying Replies</span></span>

<span data-ttu-id="b411b-266">O WCF conta com correlação de solicitação-resposta HTTP para correlação de protocolo de troca de mensagens bidirecional.</span><span class="sxs-lookup"><span data-stu-id="b411b-266">WCF relies on HTTP request-reply correlation for two-way message exchange protocol correlation.</span></span> <span data-ttu-id="b411b-267">Por isso, o iniciador do WCF não interrompe a tentar novamente uma mensagem de sequência de solicitação quando a mensagem de sequência de solicitação é confirmada, mas em vez disso, se a resposta HTTP executa uma confirmação, a mensagem do usuário ou a falha.</span><span class="sxs-lookup"><span data-stu-id="b411b-267">Because of this, the WCF Initiator does not stop retrying a request sequence message when the request sequence message is acknowledged but rather when the HTTP response carries an acknowledgement, user message, or fault.</span></span> <span data-ttu-id="b411b-268">O Respondente WCF repetições de respostas sobre o segmento de solicitação HTTP da solicitação à qual a resposta está correlacionada.</span><span class="sxs-lookup"><span data-stu-id="b411b-268">The WCF Responder retries replies on the HTTP request leg of the request to which the reply is correlated.</span></span>

#### <a name="lastmessage-exchange"></a><span data-ttu-id="b411b-269">Exchange LastMessage</span><span class="sxs-lookup"><span data-stu-id="b411b-269">LastMessage Exchange</span></span>

<span data-ttu-id="b411b-270">O iniciador do WCF gera e transmite uma mensagem de último corpo vazia no trecho de solicitação do HTTP.</span><span class="sxs-lookup"><span data-stu-id="b411b-270">The WCF Initiator generates and transmits an empty bodied last message on the HTTP request leg.</span></span> <span data-ttu-id="b411b-271">WCF requer uma resposta, mas ignora a mensagem de resposta real.</span><span class="sxs-lookup"><span data-stu-id="b411b-271">WCF requires a response but ignores the actual response message.</span></span> <span data-ttu-id="b411b-272">As respostas de respondente do WCF a vazio incorporada última mensagem da sequência de solicitação com corpo vazio última mensagem da sequência de resposta.</span><span class="sxs-lookup"><span data-stu-id="b411b-272">The WCF Responder replies to the request sequence’s empty-bodied last message with the reply sequence’s empty-bodied last message.</span></span>

<span data-ttu-id="b411b-273">Se o Respondente WCF recebe uma mensagem de última em que o URI da ação não é `http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage`, respostas WCF com uma última mensagem de erro.</span><span class="sxs-lookup"><span data-stu-id="b411b-273">If the WCF Responder receives a last message in which the action URI is not `http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage`, WCF replies with a last message.</span></span> <span data-ttu-id="b411b-274">No caso de um protocolo de troca de mensagens bidirecional, a última mensagem leva a mensagem de aplicativo; no caso de um protocolo de troca de mensagens unidirecional, a última mensagem está vazia.</span><span class="sxs-lookup"><span data-stu-id="b411b-274">In the case of a two-way message exchange protocol, the last message carries the application message; in the case of a one-way message exchange protocol, the last message is empty.</span></span>

<span data-ttu-id="b411b-275">O respondente do WCF não exige uma confirmação para incorporada vazio última mensagem da sequência de resposta.</span><span class="sxs-lookup"><span data-stu-id="b411b-275">The WCF Responder does not require an acknowledgement for the reply sequence’s empty-bodied last message.</span></span>

#### <a name="terminatesequence-exchange"></a><span data-ttu-id="b411b-276">Exchange TerminateSequence</span><span class="sxs-lookup"><span data-stu-id="b411b-276">TerminateSequence Exchange</span></span>

<span data-ttu-id="b411b-277">Quando todas as solicitações recebeu uma resposta válida, o iniciador do WCF gera e transmite a sequência de solicitação `TerminateSequence` mensagem sobre o segmento de solicitação HTTP.</span><span class="sxs-lookup"><span data-stu-id="b411b-277">When all requests have received a valid reply, the WCF Initiator generates and transmits the request sequence’s `TerminateSequence` message on the HTTP request leg.</span></span> <span data-ttu-id="b411b-278">WCF requer uma resposta, mas ignora a mensagem de resposta real.</span><span class="sxs-lookup"><span data-stu-id="b411b-278">WCF requires a response but ignores the actual response message.</span></span> <span data-ttu-id="b411b-279">O Respondente WCF responde à sequência de solicitação `TerminateSequence` mensagem com a sequência de resposta `TerminateSequence` mensagem.</span><span class="sxs-lookup"><span data-stu-id="b411b-279">The WCF Responder replies to the request sequence’s `TerminateSequence` message with the reply sequence’s `TerminateSequence` message.</span></span>

<span data-ttu-id="b411b-280">Em uma sequência de desligamento normal, ambos `TerminateSequence` as mensagens carregam uma gama completa `SequenceAcknowledgement`.</span><span class="sxs-lookup"><span data-stu-id="b411b-280">In a normal shutdown sequence, both `TerminateSequence` messages carry a full range `SequenceAcknowledgement`.</span></span>

### <a name="requestreply-addressable-initiator"></a><span data-ttu-id="b411b-281">Solicitação/resposta, o iniciador endereçável</span><span class="sxs-lookup"><span data-stu-id="b411b-281">Request/Reply, Addressable Initiator</span></span>

#### <a name="binding"></a><span data-ttu-id="b411b-282">Associação</span><span class="sxs-lookup"><span data-stu-id="b411b-282">Binding</span></span>

<span data-ttu-id="b411b-283">O WCF fornece um padrão de troca de mensagem de solicitação-resposta usando duas sequências em uma entrada e um canal de saída HTTP.</span><span class="sxs-lookup"><span data-stu-id="b411b-283">WCF provides a request-reply message exchange pattern using two sequences over an inbound and an outbound HTTP channel.</span></span> <span data-ttu-id="b411b-284">O WCF usa as solicitações HTTP para transmitir todas as mensagens.</span><span class="sxs-lookup"><span data-stu-id="b411b-284">WCF uses the HTTP requests to transmit all messages.</span></span> <span data-ttu-id="b411b-285">Todas as respostas HTTP tem um corpo vazio e o código de status HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="b411b-285">All HTTP responses have an empty body and HTTP 202 status code.</span></span>

#### <a name="createsequence-exchange"></a><span data-ttu-id="b411b-286">Exchange CreateSequence</span><span class="sxs-lookup"><span data-stu-id="b411b-286">CreateSequence Exchange</span></span>

<span data-ttu-id="b411b-287">O iniciador do WCF gera um `CreateSequence` mensagem com uma oferta.</span><span class="sxs-lookup"><span data-stu-id="b411b-287">The WCF Initiator generates a `CreateSequence` message with an offer.</span></span> <span data-ttu-id="b411b-288">O Respondente WCF garante que o `CreateSequence` tem uma oferta antes de criar uma sequência.</span><span class="sxs-lookup"><span data-stu-id="b411b-288">The WCF Responder ensures that the `CreateSequence` has an offer before creating a sequence.</span></span> <span data-ttu-id="b411b-289">WCF envia o `CreateSequenceResponse` na solicitação HTTP endereçado a `CreateSequence`do `ReplyTo` referência de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="b411b-289">WCF sends the `CreateSequenceResponse` on the HTTP request addressed to the `CreateSequence`’s `ReplyTo` endpoint reference.</span></span>

#### <a name="requestreply-correlation"></a><span data-ttu-id="b411b-290">Correlação de solicitação/resposta</span><span class="sxs-lookup"><span data-stu-id="b411b-290">Request/Reply Correlation</span></span>

<span data-ttu-id="b411b-291">Todos os urso de mensagens de solicitação de aplicativo garante que o iniciador do WCF uma `MessageId` e um `ReplyTo` referência de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="b411b-291">The WCF Initiator ensures all application request messages bear a `MessageId` and a `ReplyTo` endpoint reference.</span></span> <span data-ttu-id="b411b-292">O iniciador do WCF se aplica a `CreateSequence` da mensagem `ReplyTo` referência de ponto de extremidade em cada mensagem de solicitação do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b411b-292">The WCF Initiator applies the `CreateSequence` message’s `ReplyTo` endpoint reference on each application request message.</span></span> <span data-ttu-id="b411b-293">O Respondente WCF requer essa solicitação de entrada mensagens urso uma `MessageId` e um `ReplyTo`.</span><span class="sxs-lookup"><span data-stu-id="b411b-293">The WCF Responder requires that incoming request messages bear a `MessageId` and a `ReplyTo`.</span></span> <span data-ttu-id="b411b-294">O Respondente WCF garante que o URI da referência do ponto de extremidade de ambos os `CreateSequence` e todas as mensagens de solicitação de aplicativo são idênticas.</span><span class="sxs-lookup"><span data-stu-id="b411b-294">The WCF Responder ensures that the endpoint reference’s URI of both the `CreateSequence` and all application request messages are identical.</span></span>
