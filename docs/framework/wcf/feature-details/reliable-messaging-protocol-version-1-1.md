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
# <a name="reliable-messaging-protocol-version-11"></a><span data-ttu-id="e4b23-102">Protocolo de mensagem confiável versão 1.1</span><span class="sxs-lookup"><span data-stu-id="e4b23-102">Reliable Messaging Protocol version 1.1</span></span>

<span data-ttu-id="e4b23-103">Este tópico aborda os detalhes de implementação do Windows Communication Foundation (WCF) para o protocolo WS-ReliableMessaging de fevereiro de 2007 (versão 1,1) necessário para interoperação usando o transporte HTTP.</span><span class="sxs-lookup"><span data-stu-id="e4b23-103">This topic covers Windows Communication Foundation (WCF) implementation details for the WS-ReliableMessaging February 2007 (version 1.1) protocol necessary for interoperation using the HTTP transport.</span></span> <span data-ttu-id="e4b23-104">O WCF segue a especificação WS-ReliableMessaging com as restrições e esclarecimentos explicados neste tópico.</span><span class="sxs-lookup"><span data-stu-id="e4b23-104">WCF follows the WS-ReliableMessaging specification with the constraints and clarifications explained in this topic.</span></span> <span data-ttu-id="e4b23-105">Observe que o protocolo WS-ReliableMessaging versão 1,1 é implementado a partir do .NET Framework 3,5.</span><span class="sxs-lookup"><span data-stu-id="e4b23-105">Note that the WS-ReliableMessaging version 1.1 protocol is implemented starting with .NET Framework 3.5.</span></span>

<span data-ttu-id="e4b23-106">O protocolo WS-ReliableMessaging de fevereiro de 2007 é implementado no WCF pelo <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="e4b23-106">The WS-ReliableMessaging February 2007 protocol is implemented in WCF by the <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>.</span></span>

<span data-ttu-id="e4b23-107">Para sua conveniência, o tópico usa as seguintes funções:</span><span class="sxs-lookup"><span data-stu-id="e4b23-107">For convenience, the topic uses the following roles:</span></span>

- <span data-ttu-id="e4b23-108">Iniciador: o cliente que inicia a criação da sequência de mensagens WS-Reliable.</span><span class="sxs-lookup"><span data-stu-id="e4b23-108">Initiator: The client that initiates WS-Reliable Message sequence creation.</span></span>

- <span data-ttu-id="e4b23-109">Respondente: o serviço que recebe as solicitações do iniciador.</span><span class="sxs-lookup"><span data-stu-id="e4b23-109">Responder: The service that receives the initiator's requests.</span></span>

 <span data-ttu-id="e4b23-110">Este documento usa os prefixos e namespaces na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="e4b23-110">This document uses the prefixes and namespaces in the following table.</span></span>

|<span data-ttu-id="e4b23-111">Prefixo</span><span class="sxs-lookup"><span data-stu-id="e4b23-111">Prefix</span></span>|<span data-ttu-id="e4b23-112">{1&gt;Namespace&lt;1}</span><span class="sxs-lookup"><span data-stu-id="e4b23-112">Namespace</span></span>|
|-|-|
|<span data-ttu-id="e4b23-113">WSRM</span><span class="sxs-lookup"><span data-stu-id="e4b23-113">wsrm</span></span>|http://docs.oasis-open.org/ws-rx/wsrm/200702|
|<span data-ttu-id="e4b23-114">netrm</span><span class="sxs-lookup"><span data-stu-id="e4b23-114">netrm</span></span>|http://schemas.microsoft.com/ws/2006/05/rm|
|<span data-ttu-id="e4b23-115">s</span><span class="sxs-lookup"><span data-stu-id="e4b23-115">s</span></span>|http://www.w3.org/2003/05/soap-envelope|
|<span data-ttu-id="e4b23-116">wsa</span><span class="sxs-lookup"><span data-stu-id="e4b23-116">wsa</span></span>|http://schemas.xmlsoap.org/ws/2005/08/addressing|
|<span data-ttu-id="e4b23-117">wsse</span><span class="sxs-lookup"><span data-stu-id="e4b23-117">wsse</span></span>|http://docs.oasis-open.org/wss/2004/01/oasis-200401-wssecurity-secext-1.0.xsd|
|<span data-ttu-id="e4b23-118">wsrmp</span><span class="sxs-lookup"><span data-stu-id="e4b23-118">wsrmp</span></span>|http://docs.oasis-open.org/ws-rx/wsrmp/200702|
|<span data-ttu-id="e4b23-119">netrmp</span><span class="sxs-lookup"><span data-stu-id="e4b23-119">netrmp</span></span>|http://schemas.microsoft.com/ws-rx/wsrmp/200702|
|<span data-ttu-id="e4b23-120">WSP</span><span class="sxs-lookup"><span data-stu-id="e4b23-120">wsp</span></span>|<span data-ttu-id="e4b23-121">(WS-Policy 1,2 ou WS-Policy 1,5)</span><span class="sxs-lookup"><span data-stu-id="e4b23-121">(Either WS-Policy 1.2 or WS-Policy 1.5)</span></span>|

## <a name="messaging"></a><span data-ttu-id="e4b23-122">Mensagens</span><span class="sxs-lookup"><span data-stu-id="e4b23-122">Messaging</span></span>

### <a name="sequence-creation"></a><span data-ttu-id="e4b23-123">Criação de sequência</span><span class="sxs-lookup"><span data-stu-id="e4b23-123">Sequence Creation</span></span>

<span data-ttu-id="e4b23-124">O WCF implementa `CreateSequence` e `CreateSequenceResponse` mensagens para estabelecer uma sequência de mensagens confiáveis.</span><span class="sxs-lookup"><span data-stu-id="e4b23-124">WCF implements `CreateSequence` and `CreateSequenceResponse` messages to establish a reliable messaging sequence.</span></span> <span data-ttu-id="e4b23-125">As seguintes restrições se aplicam:</span><span class="sxs-lookup"><span data-stu-id="e4b23-125">The following constraints apply:</span></span>

- <span data-ttu-id="e4b23-126">B1101: o iniciador do WCF usa a mesma referência de ponto de extremidade que a `CreateSequence` `ReplyTo`da mensagem, `AcksTo` e `Offer/Endpoint`.</span><span class="sxs-lookup"><span data-stu-id="e4b23-126">B1101: The WCF Initiator uses the same endpoint reference as the `CreateSequence` message’s `ReplyTo`, `AcksTo` and `Offer/Endpoint`.</span></span>

- <span data-ttu-id="e4b23-127">R1102: as referências de ponto de extremidade `AcksTo`, `ReplyTo` e `Offer/Endpoint` na mensagem de `CreateSequence` devem ter valores de endereço com representações de cadeia de caracteres idênticas, de modo que correspondam ao octeto.</span><span class="sxs-lookup"><span data-stu-id="e4b23-127">R1102: The `AcksTo`, `ReplyTo` and `Offer/Endpoint` endpoint references in the `CreateSequence` message must have address values with identical string representations such that they match the octet-wise.</span></span>

  - <span data-ttu-id="e4b23-128">O respondente do WCF verifica se a parte do URI do `AcksTo`, `ReplyTo` e `Endpoint` referências do ponto de extremidade são idênticas antes de criar uma sequência.</span><span class="sxs-lookup"><span data-stu-id="e4b23-128">The WCF Responder verifies that the URI portion of the `AcksTo`, `ReplyTo` and `Endpoint` endpoint references are identical before creating a sequence.</span></span>

- <span data-ttu-id="e4b23-129">R1103: as referências de ponto de extremidade `AcksTo`, `ReplyTo` e `Offer/Endpoint` na mensagem de `CreateSequence` devem ter o mesmo conjunto de parâmetros de referência.</span><span class="sxs-lookup"><span data-stu-id="e4b23-129">R1103: The `AcksTo`, `ReplyTo` and `Offer/Endpoint` endpoint references in the `CreateSequence` message should have the same set of reference parameters.</span></span>

  - <span data-ttu-id="e4b23-130">O WCF não impõe, mas pressupõe que os parâmetros de referência do `AcksTo`, `ReplyTo` e `Offer/Endpoint` referências de ponto de extremidade em `CreateSequence` são idênticos e usa parâmetros de referência da referência de ponto de extremidade `ReplyTo` para confirmações e mensagens de sequências de inverso.</span><span class="sxs-lookup"><span data-stu-id="e4b23-130">WCF does not enforce, but assumes that reference parameters of the `AcksTo`, `ReplyTo` and `Offer/Endpoint` endpoint references on `CreateSequence` are identical and uses reference parameters from the `ReplyTo` endpoint reference for acknowledgements and converse sequence messages.</span></span>

- <span data-ttu-id="e4b23-131">B1104: o iniciador do WCF não gera o elemento `Expires` opcional ou `Offer/Expires` na mensagem de `CreateSequence`.</span><span class="sxs-lookup"><span data-stu-id="e4b23-131">B1104: The WCF Initiator does not generate the optional `Expires` or `Offer/Expires` element in the `CreateSequence` message.</span></span>

- <span data-ttu-id="e4b23-132">B1105: ao acessar a mensagem de `CreateSequence`, o respondente do WCF usa o valor `Expires` no elemento `CreateSequence` como o valor `Expires` no elemento `CreateSequenceResponse`.</span><span class="sxs-lookup"><span data-stu-id="e4b23-132">B1105: When accessing the `CreateSequence` message, the WCF Responder uses the `Expires` value in the `CreateSequence` element as the `Expires` value in the `CreateSequenceResponse` element.</span></span> <span data-ttu-id="e4b23-133">Caso contrário, o respondente do WCF lê e ignora os valores de `Expires` e `Offer/Expires`.</span><span class="sxs-lookup"><span data-stu-id="e4b23-133">Otherwise, the WCF Responder reads and ignores the `Expires` and `Offer/Expires` values.</span></span>

- <span data-ttu-id="e4b23-134">B1106: ao acessar a mensagem de `CreateSequenceResponse`, o iniciador do WCF lê o valor de `Expires` opcional, mas não o usa.</span><span class="sxs-lookup"><span data-stu-id="e4b23-134">B1106: When accessing the `CreateSequenceResponse` message, the WCF Initiator reads the optional `Expires` value but does not use it.</span></span>

- <span data-ttu-id="e4b23-135">B1107: o iniciador e o respondente do WCF sempre geram o elemento `IncompleteSequenceBehavior` opcional nos elementos `CreateSequence/Offer` e `CreateSequenceResponse`.</span><span class="sxs-lookup"><span data-stu-id="e4b23-135">B1107: The WCF Initiator and Responder always generate the optional `IncompleteSequenceBehavior` element in the `CreateSequence/Offer` and `CreateSequenceResponse` elements.</span></span>

- <span data-ttu-id="e4b23-136">B1108: o WCF usa apenas os valores `DiscardFollowingFirstGap` e `NoDiscard` no elemento `IncompleteSequenceBehavior`.</span><span class="sxs-lookup"><span data-stu-id="e4b23-136">B1108: WCF uses only the `DiscardFollowingFirstGap` and `NoDiscard` values in the `IncompleteSequenceBehavior` element.</span></span>

  - <span data-ttu-id="e4b23-137">O WS-ReliableMessaging utiliza o mecanismo de `Offer` para estabelecer as duas sequências correlacionadas de converso que formam uma sessão.</span><span class="sxs-lookup"><span data-stu-id="e4b23-137">WS-ReliableMessaging utilizes the `Offer` mechanism to establish the two converse correlated sequences that form a session.</span></span>

- <span data-ttu-id="e4b23-138">B1109: se `CreateSequence` contiver um elemento `Offer`, o respondente unidirecional do WCF rejeitará a sequência oferecida respondendo com um `CreateSequenceResponse` sem um elemento `Accept`.</span><span class="sxs-lookup"><span data-stu-id="e4b23-138">B1109: If `CreateSequence` contains an `Offer` element, the one way WCF Responder rejects the offered sequence by responding with a `CreateSequenceResponse` without an `Accept` element.</span></span>

- <span data-ttu-id="e4b23-139">B1110: se um Respondente de mensagens confiável rejeitar a sequência oferecida, o iniciador do WCF falhará na sequência estabelecida recentemente.</span><span class="sxs-lookup"><span data-stu-id="e4b23-139">B1110: If a Reliable Messaging Responder rejects the offered sequence, the WCF Initiator faults the newly established sequence.</span></span>

- <span data-ttu-id="e4b23-140">B1111: se `CreateSequence` não contiver um elemento `Offer`, o respondente do WCF bidirecional rejeitará a sequência oferecida respondendo com uma falha `CreateSequenceRefused`.</span><span class="sxs-lookup"><span data-stu-id="e4b23-140">B1111: If `CreateSequence` does not contain an `Offer` element, the two-way WCF Responder rejects the offered sequence by responding with a `CreateSequenceRefused` fault.</span></span>

- <span data-ttu-id="e4b23-141">R1112: quando duas sequências de conversos são estabelecidas usando o mecanismo de `Offer`, a propriedade `[address]` da referência do ponto de extremidade `CreateSequenceResponse/Accept/AcksTo` deve corresponder ao URI de destino do byte de mensagem `CreateSequence` para byte.</span><span class="sxs-lookup"><span data-stu-id="e4b23-141">R1112: When two converse sequences are established using the `Offer` mechanism, the `[address]` property of the `CreateSequenceResponse/Accept/AcksTo` endpoint reference must match the destination URI of the `CreateSequence` message byte for byte.</span></span>

- <span data-ttu-id="e4b23-142">R1113: quando duas sequências de conversos são estabelecidas usando o mecanismo de `Offer`, todas as mensagens em ambas as sequências que fluem do iniciador para o respondente devem ser enviadas para a mesma referência de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="e4b23-142">R1113: When two converse sequences are established using the `Offer` mechanism, all messages on both sequences flowing from the Initiator to the Responder must be sent to the same endpoint reference.</span></span>

<span data-ttu-id="e4b23-143">O WCF usa o WS-ReliableMessaging para estabelecer sessões confiáveis entre o iniciador e o respondente.</span><span class="sxs-lookup"><span data-stu-id="e4b23-143">WCF uses WS-ReliableMessaging to establish reliable sessions between the Initiator and the Responder.</span></span> <span data-ttu-id="e4b23-144">A implementação do WS-ReliableMessaging do WCF fornece uma sessão confiável para os padrões unidirecional, resposta de solicitação e mensagens em full duplex.</span><span class="sxs-lookup"><span data-stu-id="e4b23-144">The WCF WS-ReliableMessaging implementation provides a reliable session for one-way, request-reply and full duplex messaging patterns.</span></span> <span data-ttu-id="e4b23-145">O mecanismo de `Offer` WS-ReliableMessaging em `CreateSequence` e `CreateSequenceResponse` permite que você estabeleça duas sequências de contraverso correlacionadas e fornece um protocolo de sessão adequado para todos os pontos de extremidade da mensagem.</span><span class="sxs-lookup"><span data-stu-id="e4b23-145">The WS-ReliableMessaging `Offer` mechanism on `CreateSequence` and `CreateSequenceResponse` lets you establish two correlated converse sequences and provides a session protocol that is suitable for all message endpoints.</span></span> <span data-ttu-id="e4b23-146">Como o WCF fornece uma garantia de segurança para tal sessão, incluindo proteção de ponta a ponta para integridade da sessão, é prático garantir que as mensagens destinadas à mesma parte cheguem ao mesmo destino.</span><span class="sxs-lookup"><span data-stu-id="e4b23-146">Because WCF provides a security guarantee for such a session including end-to-end protection for session integrity, it is practical to ensure that messages intended for the same party arrive at the same destination.</span></span> <span data-ttu-id="e4b23-147">Isso também permite "transportado" de confirmações de sequência em mensagens de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e4b23-147">This also allows "piggy-backing" of sequence acknowledgements on application messages.</span></span> <span data-ttu-id="e4b23-148">Portanto, as restrições R1102, R1112 e R1113 se aplicam ao WCF.</span><span class="sxs-lookup"><span data-stu-id="e4b23-148">Therefore, constraints R1102, R1112, and R1113 apply to WCF.</span></span>

<span data-ttu-id="e4b23-149">Um exemplo de uma mensagem de `CreateSequence`.</span><span class="sxs-lookup"><span data-stu-id="e4b23-149">An example of a `CreateSequence` message.</span></span>

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

<span data-ttu-id="e4b23-150">Um exemplo de uma mensagem de `CreateSequenceResponse`.</span><span class="sxs-lookup"><span data-stu-id="e4b23-150">An example of a `CreateSequenceResponse` message.</span></span>

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

### <a name="closing-a-sequence"></a><span data-ttu-id="e4b23-151">Fechando uma sequência</span><span class="sxs-lookup"><span data-stu-id="e4b23-151">Closing a Sequence</span></span>

<span data-ttu-id="e4b23-152">O WCF usa as mensagens `CloseSequence` e `CloseSequenceResponse` para um desligamento iniciado pela fonte de mensagens confiáveis.</span><span class="sxs-lookup"><span data-stu-id="e4b23-152">WCF uses the `CloseSequence` and `CloseSequenceResponse` messages for a Reliable Messaging source-initiated shutdown.</span></span> <span data-ttu-id="e4b23-153">O destino de mensagens confiáveis do WCF não inicia o desligamento e a fonte de mensagens confiáveis do WCF não dá suporte a um desligamento iniciado por destino de mensagens confiáveis.</span><span class="sxs-lookup"><span data-stu-id="e4b23-153">The WCF Reliable Messaging destination does not initiate shutdown and the WCF Reliable Messaging source does not support a Reliable Messaging destination-initiated shutdown.</span></span> <span data-ttu-id="e4b23-154">As seguintes restrições se aplicam:</span><span class="sxs-lookup"><span data-stu-id="e4b23-154">The following constraints apply:</span></span>

- <span data-ttu-id="e4b23-155">B1201: a fonte de mensagens confiáveis do WCF sempre envia uma mensagem de `CloseSequence` para desligar a sequência.</span><span class="sxs-lookup"><span data-stu-id="e4b23-155">B1201: The WCF Reliable Messaging source always sends a `CloseSequence` message to shut down the sequence.</span></span>

- <span data-ttu-id="e4b23-156">B1202: a origem da mensagem confiável aguarda a confirmação do intervalo completo de mensagens de sequência antes de enviar a mensagem de `CloseSequence`.</span><span class="sxs-lookup"><span data-stu-id="e4b23-156">B1202: The Reliable Messaging source waits for acknowledgement of the full range of sequence messages before sending the `CloseSequence` message.</span></span>

- <span data-ttu-id="e4b23-157">B1203: a fonte de mensagens confiáveis sempre inclui o elemento `LastMsgNumber` opcional, a menos que a sequência não contenha mensagens.</span><span class="sxs-lookup"><span data-stu-id="e4b23-157">B1203: The Reliable Messaging source always includes the optional `LastMsgNumber` element unless the sequence does not contain messages.</span></span>

- <span data-ttu-id="e4b23-158">R1204: o destino do sistema de mensagens confiável não deve iniciar o desligamento enviando uma mensagem de `CloseSequence`.</span><span class="sxs-lookup"><span data-stu-id="e4b23-158">R1204: The Reliable Messaging destination must not initiate shutdown by sending a `CloseSequence` message.</span></span>

- <span data-ttu-id="e4b23-159">B1205: após receber uma mensagem de `CloseSequence`, a origem de mensagens confiáveis do WCF considera a sequência incompleta e envia uma falha.</span><span class="sxs-lookup"><span data-stu-id="e4b23-159">B1205: Upon receiving a `CloseSequence` message, the WCF Reliable Messaging source considers the sequence incomplete and sends a fault.</span></span>

 <span data-ttu-id="e4b23-160">Um exemplo de uma mensagem de `CloseSequence`.</span><span class="sxs-lookup"><span data-stu-id="e4b23-160">An example of a `CloseSequence` message.</span></span>

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

<span data-ttu-id="e4b23-161">Exemplo de `CloseSequenceResponse` mensagem:</span><span class="sxs-lookup"><span data-stu-id="e4b23-161">Example `CloseSequenceResponse` message:</span></span>

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

### <a name="sequence-termination"></a><span data-ttu-id="e4b23-162">Terminação de sequência</span><span class="sxs-lookup"><span data-stu-id="e4b23-162">Sequence Termination</span></span>

<span data-ttu-id="e4b23-163">O WCF usa principalmente o handshake de `TerminateSequence/TerminateSequenceResponse` depois de concluir o handshake de `CloseSequence/CloseSequenceResponse`.</span><span class="sxs-lookup"><span data-stu-id="e4b23-163">WCF primarily uses the `TerminateSequence/TerminateSequenceResponse` handshake after completing the `CloseSequence/CloseSequenceResponse` handshake.</span></span> <span data-ttu-id="e4b23-164">O destino de mensagens confiáveis do WCF não inicia o encerramento e a fonte de mensagens confiáveis não dá suporte a um encerramento iniciado pelo destino de mensagens confiáveis.</span><span class="sxs-lookup"><span data-stu-id="e4b23-164">The WCF Reliable Messaging destination does not initiate termination and the Reliable Messaging source does not support a Reliable Messaging destination-initiated termination.</span></span> <span data-ttu-id="e4b23-165">As seguintes restrições se aplicam:</span><span class="sxs-lookup"><span data-stu-id="e4b23-165">The following constraints apply:</span></span>

- <span data-ttu-id="e4b23-166">B1301: o iniciador do WCF envia apenas a mensagem de `TerminateSequence` após a conclusão bem-sucedida do handshake de `CloseSequence/CloseSequenceResponse`.</span><span class="sxs-lookup"><span data-stu-id="e4b23-166">B1301: The WCF Initiator only sends the `TerminateSequence` message after the successful completion of the `CloseSequence/CloseSequenceResponse` handshake.</span></span>

- <span data-ttu-id="e4b23-167">R1302: o WCF valida que o elemento `LastMsgNumber` é consistente em todas as `CloseSequence` e `TerminateSequence` mensagens para uma determinada sequência.</span><span class="sxs-lookup"><span data-stu-id="e4b23-167">R1302: WCF validates that the `LastMsgNumber` element is consistent across all `CloseSequence` and `TerminateSequence` messages for a given sequence.</span></span> <span data-ttu-id="e4b23-168">Isso significa que `LastMsgNumber` não está presente em todas as mensagens de `CloseSequence` e `TerminateSequence`, ou está presente e é idêntica em todas as mensagens de `CloseSequence` e `TerminateSequence`.</span><span class="sxs-lookup"><span data-stu-id="e4b23-168">This means that `LastMsgNumber` is either not present on all `CloseSequence` and `TerminateSequence` messages, or it is present and identical on all `CloseSequence` and `TerminateSequence` messages.</span></span>

- <span data-ttu-id="e4b23-169">B1303: ao receber uma mensagem de `TerminateSequence` após o handshake de `CloseSequence/CloseSequenceResponse`, o destino do sistema de mensagens confiável responde com uma mensagem `TerminateSequenceResponse`.</span><span class="sxs-lookup"><span data-stu-id="e4b23-169">B1303: When receiving a `TerminateSequence` message after the `CloseSequence/CloseSequenceResponse` handshake, the Reliable Messaging destination responds with a `TerminateSequenceResponse` message.</span></span> <span data-ttu-id="e4b23-170">Como a fonte de mensagens confiáveis tem a confirmação final antes de enviar a mensagem de `TerminateSequence`, o destino da mensagem confiável sabe sem dúvida que a sequência termina e recupera recursos imediatamente.</span><span class="sxs-lookup"><span data-stu-id="e4b23-170">Because the Reliable Messaging source has the final acknowledgement before sending the `TerminateSequence` message, the Reliable Messaging destination knows without doubt that the sequence ends, and reclaims resources immediately.</span></span>

- <span data-ttu-id="e4b23-171">B1304: ao receber uma mensagem de `TerminateSequence` antes do handshake de `CloseSequence/CloseSequenceResponse`, o destino de mensagens confiáveis do WCF responde com uma mensagem de `TerminateSequenceResponse`.</span><span class="sxs-lookup"><span data-stu-id="e4b23-171">B1304: When receiving a `TerminateSequence` message prior to the `CloseSequence/CloseSequenceResponse` handshake, the WCF Reliable Messaging destination responds with a `TerminateSequenceResponse` message.</span></span> <span data-ttu-id="e4b23-172">Se o destino da mensagem confiável determinar que não há inconsistências na sequência, o destino da mensagem confiável aguardará um tempo especificado de destino do aplicativo antes de recuperar os recursos, para permitir que o cliente receba a confirmação final.</span><span class="sxs-lookup"><span data-stu-id="e4b23-172">If the Reliable Messaging destination determines that there are no inconsistencies in the sequence, the Reliable Messaging destination waits for an application destination-specified time before reclaiming resources, to allow the client the chance to receive the final acknowledgement.</span></span> <span data-ttu-id="e4b23-173">Caso contrário, o destino da mensagem confiável recupera recursos imediatamente e indica ao destino do aplicativo que a sequência termina com a dúvida ao gerar o evento `Faulted`.</span><span class="sxs-lookup"><span data-stu-id="e4b23-173">Otherwise, the Reliable Messaging destination reclaims resources immediately and indicates to the application destination that the sequence ends with doubt by raising the `Faulted` event.</span></span>

<span data-ttu-id="e4b23-174">Um exemplo de uma mensagem de `TerminateSequence`.</span><span class="sxs-lookup"><span data-stu-id="e4b23-174">An example of a `TerminateSequence` message.</span></span>

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

<span data-ttu-id="e4b23-175">Exemplo de `TerminateSequenceResponse` mensagem:</span><span class="sxs-lookup"><span data-stu-id="e4b23-175">Example `TerminateSequenceResponse` message:</span></span>

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

### <a name="sequences"></a><span data-ttu-id="e4b23-176">Sequências</span><span class="sxs-lookup"><span data-stu-id="e4b23-176">Sequences</span></span>

<span data-ttu-id="e4b23-177">Veja a seguir uma lista de restrições que se aplicam a sequências:</span><span class="sxs-lookup"><span data-stu-id="e4b23-177">The following is a list of constraints that apply to sequences:</span></span>

- <span data-ttu-id="e4b23-178">B1401: o WCF gera e acessa números de sequência que não são maiores do que `xs:long`valor inclusivo máximo, 9223372036854775807.</span><span class="sxs-lookup"><span data-stu-id="e4b23-178">B1401:WCF generates and accesses sequence numbers no higher than `xs:long`’s maximum inclusive value, 9223372036854775807.</span></span>

<span data-ttu-id="e4b23-179">Um exemplo de um cabeçalho de `Sequence`.</span><span class="sxs-lookup"><span data-stu-id="e4b23-179">An example of a `Sequence` header.</span></span>

```xml
<wsrm:Sequence s:mustUnderstand="1">
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>
  <wsrm:MessageNumber>1</wsrm:MessageNumber>
</wsrm:Sequence>
```

### <a name="request-acknowledgement"></a><span data-ttu-id="e4b23-180">Confirmação de solicitação</span><span class="sxs-lookup"><span data-stu-id="e4b23-180">Request Acknowledgement</span></span>

<span data-ttu-id="e4b23-181">O WCF usa o cabeçalho `AckRequested` como um mecanismo Keep-Alive.</span><span class="sxs-lookup"><span data-stu-id="e4b23-181">WCF uses the `AckRequested` header as a keep-alive mechanism.</span></span>

<span data-ttu-id="e4b23-182">Um exemplo de um cabeçalho de `AckRequested`.</span><span class="sxs-lookup"><span data-stu-id="e4b23-182">An example of an `AckRequested` header.</span></span>

```xml
<wsrm:AckRequested>
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>
</wsrm:AckRequested>
```

### <a name="sequenceacknowledgement"></a><span data-ttu-id="e4b23-183">SequenceAcknowledgement</span><span class="sxs-lookup"><span data-stu-id="e4b23-183">SequenceAcknowledgement</span></span>

<span data-ttu-id="e4b23-184">O WCF usa um mecanismo de "transportado" para confirmações de sequência fornecidas em mensagens WS-Reliable.</span><span class="sxs-lookup"><span data-stu-id="e4b23-184">WCF uses a "piggy-back" mechanism for sequence acknowledgements provided in WS-Reliable Messaging.</span></span> <span data-ttu-id="e4b23-185">As seguintes restrições se aplicam:</span><span class="sxs-lookup"><span data-stu-id="e4b23-185">The following constraints apply:</span></span>

- <span data-ttu-id="e4b23-186">R1601: quando duas sequências de conversos são estabelecidas usando o mecanismo de `Offer`, o cabeçalho `SequenceAcknowledgement` pode ser incluído em qualquer mensagem de aplicativo transmitida para o destinatário pretendido.</span><span class="sxs-lookup"><span data-stu-id="e4b23-186">R1601: When two converse sequences are established using the `Offer` mechanism, the `SequenceAcknowledgement` header may be included in any application message transmitted to the intended recipient.</span></span> <span data-ttu-id="e4b23-187">O ponto de extremidade remoto deve ser capaz de acessar um cabeçalho de `SequenceAcknowledgement` acumulado.</span><span class="sxs-lookup"><span data-stu-id="e4b23-187">The remote endpoint must be able to access a piggybacked `SequenceAcknowledgement` header.</span></span>

- <span data-ttu-id="e4b23-188">B1602: o WCF não gera cabeçalhos de `SequenceAcknowledgement` que contêm elementos de `Nack`.</span><span class="sxs-lookup"><span data-stu-id="e4b23-188">B1602: WCF does not generate `SequenceAcknowledgement` headers that contain `Nack` elements.</span></span> <span data-ttu-id="e4b23-189">O WCF valida que cada elemento de `Nack` contém um número de sequência, mas, caso contrário, ignora o elemento `Nack` e o valor.</span><span class="sxs-lookup"><span data-stu-id="e4b23-189">WCF validates that each `Nack` element contains a sequence number, but otherwise ignores the `Nack` element and value.</span></span>

 <span data-ttu-id="e4b23-190">Um exemplo de um cabeçalho de `SequenceAcknowledgement`.</span><span class="sxs-lookup"><span data-stu-id="e4b23-190">An example of a `SequenceAcknowledgement` header.</span></span>

```xml
<wsrm:SequenceAcknowledgement>
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>
  <wsrm:AcknowledgementRange Lower="1" Upper="1"></wsrm:AcknowledgementRange>
</wsrm:SequenceAcknowledgement>
```

### <a name="ws-reliablemessaging-faults"></a><span data-ttu-id="e4b23-191">Falhas de WS-ReliableMessaging</span><span class="sxs-lookup"><span data-stu-id="e4b23-191">WS-ReliableMessaging Faults</span></span>

<span data-ttu-id="e4b23-192">Veja a seguir uma lista de restrições que se aplicam à implementação do WCF de falhas WS-ReliableMessaging.</span><span class="sxs-lookup"><span data-stu-id="e4b23-192">The following is a list of constraints that apply to the WCF implementation of WS-ReliableMessaging faults.</span></span> <span data-ttu-id="e4b23-193">As seguintes restrições se aplicam:</span><span class="sxs-lookup"><span data-stu-id="e4b23-193">The following constraints apply:</span></span>

- <span data-ttu-id="e4b23-194">B1701: o WCF não gera `MessageNumberRollover` falhas.</span><span class="sxs-lookup"><span data-stu-id="e4b23-194">B1701: WCF does not generate `MessageNumberRollover` faults.</span></span>

- <span data-ttu-id="e4b23-195">B1702: sobre SOAP 1,2, quando o ponto de extremidade de serviço atinge seu limite de conexão e não pode processar novas conexões, o WCF gera um subcódigo de falha de `CreateSequenceRefused` aninhado, `netrm:ConnectionLimitReached`, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="e4b23-195">B1702: Over SOAP 1.2, when the service endpoint reaches its connection limit and cannot process new connections, WCF generates a nested `CreateSequenceRefused` fault subcode, `netrm:ConnectionLimitReached`, as shown in the following example.</span></span>

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

### <a name="ws-addressing-faults"></a><span data-ttu-id="e4b23-196">Falhas no WS-Addressing</span><span class="sxs-lookup"><span data-stu-id="e4b23-196">WS-Addressing Faults</span></span>

<span data-ttu-id="e4b23-197">Como o WS-ReliableMessaging usa o WS-Addressing, a implementação do WS-ReliableMessaging do WCF pode gerar e transmitir falhas de WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="e4b23-197">Because WS-ReliableMessaging uses WS-Addressing, the WCF WS-ReliableMessaging implementation may generate and transmit WS-Addressing faults.</span></span> <span data-ttu-id="e4b23-198">Esta seção aborda as falhas do WS-Addressing que o WCF gera e transmite explicitamente na camada WS-ReliableMessaging:</span><span class="sxs-lookup"><span data-stu-id="e4b23-198">This section covers the WS-Addressing faults that WCF explicitly generates and transmits at the WS-ReliableMessaging layer:</span></span>

- <span data-ttu-id="e4b23-199">B1801: o WCF gera e transmite a falha de `Message Addressing Header Required` quando uma das seguintes opções é verdadeira:</span><span class="sxs-lookup"><span data-stu-id="e4b23-199">B1801:WCF generates and transmits the `Message Addressing Header Required` fault when one of the following is true:</span></span>

  - <span data-ttu-id="e4b23-200">Uma `CreateSequence`, `CloseSequence` ou `TerminateSequence` mensagem está sem um cabeçalho `MessageId`.</span><span class="sxs-lookup"><span data-stu-id="e4b23-200">A `CreateSequence`, `CloseSequence` or `TerminateSequence` message is missing a `MessageId` header.</span></span>

  - <span data-ttu-id="e4b23-201">Uma `CreateSequence`, `CloseSequence` ou `TerminateSequence` mensagem está sem um cabeçalho `ReplyTo`.</span><span class="sxs-lookup"><span data-stu-id="e4b23-201">A `CreateSequence`, `CloseSequence` or `TerminateSequence` message is missing a `ReplyTo` header.</span></span>

  - <span data-ttu-id="e4b23-202">Uma mensagem `CreateSequenceResponse`, `CloseSequenceResponse`ou `TerminateSequenceResponse` está sem um cabeçalho `RelatesTo`.</span><span class="sxs-lookup"><span data-stu-id="e4b23-202">A `CreateSequenceResponse`, `CloseSequenceResponse`, or `TerminateSequenceResponse` message is missing a `RelatesTo` header.</span></span>

- <span data-ttu-id="e4b23-203">B1802: o WCF gera e transmite a falha de `Endpoint Unavailable` para indicar que não há nenhum ponto de extremidade ouvindo que possa processar a sequência com base no exame dos cabeçalhos de endereçamento na mensagem de `CreateSequence`.</span><span class="sxs-lookup"><span data-stu-id="e4b23-203">B1802:WCF generates and transmits the `Endpoint Unavailable` fault to indicate there is no endpoint listening that can process the sequence based on examination of the addressing headers in the `CreateSequence` message.</span></span>

## <a name="protocol-composition"></a><span data-ttu-id="e4b23-204">Composição de protocolo</span><span class="sxs-lookup"><span data-stu-id="e4b23-204">Protocol Composition</span></span>

### <a name="composition-with-ws-addressing"></a><span data-ttu-id="e4b23-205">Composição com WS-Addressing</span><span class="sxs-lookup"><span data-stu-id="e4b23-205">Composition with WS-Addressing</span></span>

<span data-ttu-id="e4b23-206">O WCF dá suporte a duas versões do WS-Addressing: WS-Addressing 2004/08 [WS-ADDR] e W3C WS-Addressing 1,0 Recommendations [WS-ADDR-CORE] e [WS-ADDR-SOAP].</span><span class="sxs-lookup"><span data-stu-id="e4b23-206">WCF supports two versions of WS-Addressing: WS-Addressing 2004/08 [WS-ADDR] and W3C WS-Addressing 1.0 Recommendations [WS-ADDR-CORE] and [WS-ADDR-SOAP].</span></span>

<span data-ttu-id="e4b23-207">Embora a especificação WS-ReliableMessaging mencione apenas o WS-Addressing 2004/08, ela não restringe a versão do WS-Addressing a ser usada.</span><span class="sxs-lookup"><span data-stu-id="e4b23-207">While the WS-ReliableMessaging specification mentions only WS-Addressing 2004/08, it does not restrict the WS-Addressing version to be used.</span></span> <span data-ttu-id="e4b23-208">Veja a seguir uma lista de restrições que se aplicam ao WCF:</span><span class="sxs-lookup"><span data-stu-id="e4b23-208">The following is a list of constraints that apply to WCF:</span></span>

- <span data-ttu-id="e4b23-209">R2101: o WS-Addressing 2004/08 e o WS-Addressing 1,0 podem ser usados com o sistema de mensagens WS-Reliable.</span><span class="sxs-lookup"><span data-stu-id="e4b23-209">R2101: Both WS-Addressing 2004/08 and WS-Addressing 1.0 can be used with WS-Reliable Messaging.</span></span>

- <span data-ttu-id="e4b23-210">R2102: uma única versão do WS-Addressing deve ser usada em uma determinada sequência WS-ReliableMessaging ou um par de sequências inversas correlacionadas usando o mecanismo de `Offer`.</span><span class="sxs-lookup"><span data-stu-id="e4b23-210">R2102: A single version of WS-Addressing must be used throughout a given WS-ReliableMessaging sequence or a pair of converse sequences correlated by using the `Offer` mechanism.</span></span>

### <a name="composition-with-soap"></a><span data-ttu-id="e4b23-211">Composição com SOAP</span><span class="sxs-lookup"><span data-stu-id="e4b23-211">Composition with SOAP</span></span>

<span data-ttu-id="e4b23-212">O WCF dá suporte ao uso de SOAP 1,1 e SOAP 1,2 com o sistema de mensagens WS-Reliable.</span><span class="sxs-lookup"><span data-stu-id="e4b23-212">WCF supports the use of both SOAP 1.1 and SOAP 1.2 with WS-Reliable Messaging.</span></span>

### <a name="composition-with-ws-security-and-ws-secureconversation"></a><span data-ttu-id="e4b23-213">Composição com WS-Security e WS-SecureConversation</span><span class="sxs-lookup"><span data-stu-id="e4b23-213">Composition with WS-Security and WS-SecureConversation</span></span>

<span data-ttu-id="e4b23-214">O WCF fornece proteção para sequências WS-ReliableMessaging usando transporte seguro (HTTPS), composição com WS-Security e composição com a conversa WS-Secure.</span><span class="sxs-lookup"><span data-stu-id="e4b23-214">WCF provides protection for WS-ReliableMessaging sequences by using secure Transport (HTTPS), composition with WS-Security, and composition with WS-Secure Conversation.</span></span> <span data-ttu-id="e4b23-215">O protocolo WS-ReliableMessaging 1,1, o WS-Security 1,1 e o WS-Secure Conversation protocolo 1,3 devem ser usados juntos.</span><span class="sxs-lookup"><span data-stu-id="e4b23-215">The WS-ReliableMessaging 1.1 protocol, WS-Security 1.1 and WS-Secure Conversation 1.3 protocol should be used together.</span></span> <span data-ttu-id="e4b23-216">Veja a seguir uma lista de restrições que se aplicam ao WCF:</span><span class="sxs-lookup"><span data-stu-id="e4b23-216">The following is a list of constraints that apply to WCF:</span></span>

- <span data-ttu-id="e4b23-217">R2301: para proteger a integridade de uma sequência WS-ReliableMessaging, além da integridade e da confidencialidade de mensagens individuais, o WCF requer que a conversa WS-Secure deva ser usada.</span><span class="sxs-lookup"><span data-stu-id="e4b23-217">R2301: To protect the integrity of a WS-ReliableMessaging sequence in addition to the integrity and confidentiality of individual messages, WCF requires that WS-Secure Conversation must be used.</span></span>

- <span data-ttu-id="e4b23-218">R2302: AWS-a sessão de conversa segura deve ser estabelecida antes de estabelecer a (s) sequência (ões) WS-ReliableMessaging.</span><span class="sxs-lookup"><span data-stu-id="e4b23-218">R2302:AWS-Secure Conversation session must be established prior to establishing WS-ReliableMessaging sequence(s).</span></span>

- <span data-ttu-id="e4b23-219">R2303: se o tempo de vida da sequência WS-ReliableMessaging exceder o tempo de vida da sessão de conversa do WS-Secure, o `SecurityContextToken` estabelecido usando a conversa WS-Secure deve ser renovado usando a associação de renovação de conversa WS-Secure correspondente.</span><span class="sxs-lookup"><span data-stu-id="e4b23-219">R2303: If the WS-ReliableMessaging sequence lifetime exceeds the WS-Secure Conversation session’s lifetime, the `SecurityContextToken` established by using WS-Secure Conversation must be renewed by using the corresponding WS-Secure Conversation Renewal binding.</span></span>

- <span data-ttu-id="e4b23-220">B2304: a sequência WS-ReliableMessaging ou um par de sequências correlacionadas correlatas são sempre associados a uma única sessão WS-SecureConversation.</span><span class="sxs-lookup"><span data-stu-id="e4b23-220">B2304:WS-ReliableMessaging sequence or a pair of correlated converse sequences are always bound to a single WS-SecureConversation session.</span></span>

- <span data-ttu-id="e4b23-221">R2305: quando composto com a conversa do WS-Secure, o respondente do WCF requer que a mensagem de `CreateSequence` contenha o elemento `wsse:SecurityTokenReference` e o cabeçalho `wsrm:UsesSequenceSTR`.</span><span class="sxs-lookup"><span data-stu-id="e4b23-221">R2305: When composed with WS-Secure Conversation, the WCF responder requires that the `CreateSequence` message contain the `wsse:SecurityTokenReference` element and the `wsrm:UsesSequenceSTR` header.</span></span>

 <span data-ttu-id="e4b23-222">Um exemplo de um cabeçalho de `UsesSequenceSTR`.</span><span class="sxs-lookup"><span data-stu-id="e4b23-222">An example of a `UsesSequenceSTR` header.</span></span>

```xml
<wsrm:UsesSequenceSTR></wsrm:UsesSequenceSTR>
```

### <a name="composition-with-ssltls-sessions"></a><span data-ttu-id="e4b23-223">Composição com sessões SSL/TLS</span><span class="sxs-lookup"><span data-stu-id="e4b23-223">Composition with SSL/TLS sessions</span></span>

<span data-ttu-id="e4b23-224">O WCF não dá suporte à composição com sessões SSL/TLS:</span><span class="sxs-lookup"><span data-stu-id="e4b23-224">WCF does not support composition with SSL/TLS sessions:</span></span>

- <span data-ttu-id="e4b23-225">B2401: o WCF não gera o cabeçalho `wsrm:UsesSequenceSSL`.</span><span class="sxs-lookup"><span data-stu-id="e4b23-225">B2401: WCF does not generate the `wsrm:UsesSequenceSSL` header.</span></span>

- <span data-ttu-id="e4b23-226">R2402: um iniciador de mensagens confiável não deve enviar uma mensagem de `CreateSequence` com um cabeçalho de `wsrm:UsesSequenceSSL` para um respondente do WCF.</span><span class="sxs-lookup"><span data-stu-id="e4b23-226">R2402: A Reliable Messaging Initiator must not send a `CreateSequence` message with a `wsrm:UsesSequenceSSL` header to a WCF Responder.</span></span>

### <a name="composition-with-ws-policy"></a><span data-ttu-id="e4b23-227">Composição com WS-Policy</span><span class="sxs-lookup"><span data-stu-id="e4b23-227">Composition with WS-Policy</span></span>

<span data-ttu-id="e4b23-228">O WCF dá suporte a duas versões de WS-Policy: WS-Policy 1,2 e WS-Policy 1,5.</span><span class="sxs-lookup"><span data-stu-id="e4b23-228">WCF supports two versions of WS-Policy: WS-Policy 1.2 and WS-Policy 1.5.</span></span>

## <a name="ws-reliablemessaging-ws-policy-assertion"></a><span data-ttu-id="e4b23-229">Declaração de WS-Policy de WS-ReliableMessaging</span><span class="sxs-lookup"><span data-stu-id="e4b23-229">WS-ReliableMessaging WS-Policy Assertion</span></span>

<span data-ttu-id="e4b23-230">O WCF usa o WS-ReliableMessaging declaração WS-Policy `wsrm:RMAssertion` para descrever os recursos de pontos de extremidade.</span><span class="sxs-lookup"><span data-stu-id="e4b23-230">WCF uses WS-ReliableMessaging WS-Policy Assertion `wsrm:RMAssertion` to describe endpoints capabilities.</span></span> <span data-ttu-id="e4b23-231">Veja a seguir uma lista de restrições que se aplicam ao WCF:</span><span class="sxs-lookup"><span data-stu-id="e4b23-231">The following is a list of constraints that apply to WCF:</span></span>

- <span data-ttu-id="e4b23-232">B3001: o WCF anexa `wsrmn:RMAssertion` declaração WS-Policy a elementos `wsdl:binding`.</span><span class="sxs-lookup"><span data-stu-id="e4b23-232">B3001: WCF attaches `wsrmn:RMAssertion` WS-Policy Assertion to `wsdl:binding` elements.</span></span> <span data-ttu-id="e4b23-233">O WCF dá suporte a ambos os anexos aos elementos `wsdl:binding` e `wsdl:port`.</span><span class="sxs-lookup"><span data-stu-id="e4b23-233">WCF supports both attachments to `wsdl:binding` and `wsdl:port` elements.</span></span>

- <span data-ttu-id="e4b23-234">B3002: o WCF nunca gera a marca de `wsp:Optional`.</span><span class="sxs-lookup"><span data-stu-id="e4b23-234">B3002: WCF never generates the `wsp:Optional` tag.</span></span>

- <span data-ttu-id="e4b23-235">B3003: ao acessar a declaração de WS-Policy `wsrmp:RMAssertion`, o WCF ignora a marca de `wsp:Optional` e trata a política WS-RM como obrigatória.</span><span class="sxs-lookup"><span data-stu-id="e4b23-235">B3003: When accessing the `wsrmp:RMAssertion` WS-Policy Assertion, WCF ignores the `wsp:Optional` tag and treats the WS-RM policy as mandatory.</span></span>

- <span data-ttu-id="e4b23-236">R3004: como o WCF não compõe as sessões SSL/TLS, o WCF não aceita a política que especifica `wsrmp:SequenceTransportSecurity`.</span><span class="sxs-lookup"><span data-stu-id="e4b23-236">R3004: Because WCF does not compose with SSL/TLS sessions, WCF does not accept policy that specifies `wsrmp:SequenceTransportSecurity`.</span></span>

- <span data-ttu-id="e4b23-237">B3005: o WCF sempre gera o elemento `wsrmp:DeliveryAssurance`.</span><span class="sxs-lookup"><span data-stu-id="e4b23-237">B3005: WCF always generates the `wsrmp:DeliveryAssurance` element.</span></span>

- <span data-ttu-id="e4b23-238">B3006: o WCF sempre especifica a garantia de entrega de `wsrmp:ExactlyOnce`.</span><span class="sxs-lookup"><span data-stu-id="e4b23-238">B3006: WCF always specifies the `wsrmp:ExactlyOnce` delivery assurance.</span></span>

- <span data-ttu-id="e4b23-239">B3007: o WCF gera e lê as seguintes propriedades da declaração WS-ReliableMessaging e fornece controle sobre elas no`ReliableSessionBindingElement`do WCF:</span><span class="sxs-lookup"><span data-stu-id="e4b23-239">B3007: WCF generates and reads the following properties of the WS-ReliableMessaging assertion and provides control over them on the WCF`ReliableSessionBindingElement`:</span></span>

  - `netrmp:InactivityTimeout`

  - `netrmp:AcknowledgementInterval`

  <span data-ttu-id="e4b23-240">Um exemplo de um `RMAssertion`.</span><span class="sxs-lookup"><span data-stu-id="e4b23-240">An example of a `RMAssertion`.</span></span>

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

## <a name="flow-control-ws-reliablemessaging-extension"></a><span data-ttu-id="e4b23-241">Extensão WS-ReliableMessaging de controle de fluxo</span><span class="sxs-lookup"><span data-stu-id="e4b23-241">Flow Control WS-ReliableMessaging Extension</span></span>

<span data-ttu-id="e4b23-242">O WCF usa a extensibilidade WS-ReliableMessaging para fornecer um controle mais rígido adicional opcional sobre o fluxo de mensagens de sequência.</span><span class="sxs-lookup"><span data-stu-id="e4b23-242">WCF uses WS-ReliableMessaging extensibility to provide optional additional tighter control over sequence message flow.</span></span>

<span data-ttu-id="e4b23-243">O controle de fluxo é habilitado definindo a propriedade <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.FlowControlEnabled?displayProperty=nameWithType> como `true`.</span><span class="sxs-lookup"><span data-stu-id="e4b23-243">Flow control is enabled by setting the <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.FlowControlEnabled?displayProperty=nameWithType> property to `true`.</span></span> <span data-ttu-id="e4b23-244">Veja a seguir uma lista de restrições que se aplicam ao WCF:</span><span class="sxs-lookup"><span data-stu-id="e4b23-244">The following is a list of constraints that apply to WCF:</span></span>

- <span data-ttu-id="e4b23-245">B4001: quando o controle de fluxo de mensagens confiável está habilitado, o WCF gera um elemento `netrm:BufferRemaining` na extensibilidade do elemento do cabeçalho `SequenceAcknowledgement`, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="e4b23-245">B4001: When Reliable Messaging Flow Control is enabled, WCF generates a `netrm:BufferRemaining` element in the element extensibility of the `SequenceAcknowledgement` header, as shown in the following example.</span></span>

  ```xml
  <wsrm:SequenceAcknowledgement>
    <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>
    <wsrm:AcknowledgementRange Upper="1" Lower="1"/>
    <netrm:BufferRemaining>8</netrm:BufferRemaining>
  </wsrm:SequenceAcknowledgement>
  ```

- <span data-ttu-id="e4b23-246">B4002: mesmo quando o controle de fluxo de mensagens confiável está habilitado, o WCF não requer um elemento `netrm:BufferRemaining` no cabeçalho `SequenceAcknowledgement`.</span><span class="sxs-lookup"><span data-stu-id="e4b23-246">B4002: Even when Reliable Messaging Flow Control is enabled, WCF does not require a `netrm:BufferRemaining` element in the `SequenceAcknowledgement` header.</span></span>

- <span data-ttu-id="e4b23-247">B4003: o destino do sistema de mensagens confiável do WCF usa `netrm:BufferRemaining` para indicar quantas novas mensagens ele pode armazenar em buffer.</span><span class="sxs-lookup"><span data-stu-id="e4b23-247">B4003: WCF Reliable Messaging Destination uses `netrm:BufferRemaining` to indicate how many new messages it can buffer.</span></span>

- <span data-ttu-id="e4b23-248">B4004: quando o controle de fluxo de mensagens confiável está habilitado, a fonte de mensagens confiáveis do WCF usa o valor de `netrm:BufferRemaining` para limitar a transmissão de mensagens.</span><span class="sxs-lookup"><span data-stu-id="e4b23-248">B4004:When Reliable Messaging Flow Control is enabled, the WCF Reliable Messaging Source uses the value of `netrm:BufferRemaining` to throttle message transmission.</span></span>

- <span data-ttu-id="e4b23-249">B4005: o WCF gera `netrm:BufferRemaining` valores inteiros entre 0 e 4096, inclusive, e lê os valores inteiros entre 0 e `xs:int``maxInclusive` valor 214748364, inclusive.</span><span class="sxs-lookup"><span data-stu-id="e4b23-249">B4005: WCF generates `netrm:BufferRemaining` integer values between 0 and 4096 inclusive, and reads integer values between 0 and `xs:int`’s `maxInclusive` value 214748364 inclusive.</span></span>

## <a name="message-exchange-patterns"></a><span data-ttu-id="e4b23-250">Padrões de troca de mensagens</span><span class="sxs-lookup"><span data-stu-id="e4b23-250">Message Exchange Patterns</span></span>

<span data-ttu-id="e4b23-251">Esta seção descreve o comportamento do WCF quando o WS-ReliableMessaging é usado para diferentes padrões de troca de mensagens.</span><span class="sxs-lookup"><span data-stu-id="e4b23-251">This section describes WCF's behavior when WS-ReliableMessaging is used for different Message Exchange Patterns.</span></span> <span data-ttu-id="e4b23-252">Para cada padrão de troca de mensagens, os seguintes dois cenários de implantações são considerados:</span><span class="sxs-lookup"><span data-stu-id="e4b23-252">For each Message Exchange Pattern the following two deployments scenarios are considered:</span></span>

- <span data-ttu-id="e4b23-253">Iniciador não endereçável: o iniciador está protegido por um firewall; O respondente pode entregar mensagens ao iniciador somente em respostas HTTP.</span><span class="sxs-lookup"><span data-stu-id="e4b23-253">Non-Addressable Initiator: Initiator is behind a firewall; Responder can deliver messages to the Initiator only on HTTP responses.</span></span>

- <span data-ttu-id="e4b23-254">Iniciador endereçável: o iniciador e o respondente podem ser enviados solicitações HTTP; em outras palavras, duas conexões HTTP de converso podem ser estabelecidas.</span><span class="sxs-lookup"><span data-stu-id="e4b23-254">Addressable Initiator: Initiator and Responder both can be sent HTTP requests; in other words, two converse HTTP connections can be established.</span></span>

### <a name="one-way-non-addressable-initiator"></a><span data-ttu-id="e4b23-255">Iniciador unidirecional e não endereçável</span><span class="sxs-lookup"><span data-stu-id="e4b23-255">One-way, Non-addressable Initiator</span></span>

#### <a name="binding"></a><span data-ttu-id="e4b23-256">Associação</span><span class="sxs-lookup"><span data-stu-id="e4b23-256">Binding</span></span>

<span data-ttu-id="e4b23-257">O WCF fornece um padrão de troca de mensagens unidirecional usando uma sequência em um canal HTTP.</span><span class="sxs-lookup"><span data-stu-id="e4b23-257">WCF provides a one-way message exchange pattern using one sequence over one HTTP channel.</span></span> <span data-ttu-id="e4b23-258">O WCF usa solicitações HTTP para transmitir todas as mensagens do iniciador para o respondente e respostas HTTP para transmitir todas as mensagens do Respondente para o iniciador.</span><span class="sxs-lookup"><span data-stu-id="e4b23-258">WCF uses HTTP requests to transmit all messages from the Initiator to the Responder and HTTP responses to transmit all messages from the Responder to the Initiator.</span></span>

#### <a name="createsequence-exchange"></a><span data-ttu-id="e4b23-259">Exchange CreateSequence</span><span class="sxs-lookup"><span data-stu-id="e4b23-259">CreateSequence Exchange</span></span>

<span data-ttu-id="e4b23-260">O iniciador do WCF transmite uma mensagem de `CreateSequence` sem elemento `Offer` em uma solicitação HTTP e espera a mensagem de `CreateSequenceResponse` na resposta HTTP.</span><span class="sxs-lookup"><span data-stu-id="e4b23-260">The WCF Initiator transmits a `CreateSequence` message with no `Offer` element on an HTTP request and expects the `CreateSequenceResponse` message on the HTTP response.</span></span> <span data-ttu-id="e4b23-261">O respondente do WCF cria uma sequência e transmite a mensagem de `CreateSequenceResponse` sem elemento `Accept` na resposta HTTP.</span><span class="sxs-lookup"><span data-stu-id="e4b23-261">The WCF Responder creates a sequence and transmits the `CreateSequenceResponse` message with no `Accept` element on the HTTP response.</span></span>

#### <a name="sequenceacknowledgement"></a><span data-ttu-id="e4b23-262">SequenceAcknowledgement</span><span class="sxs-lookup"><span data-stu-id="e4b23-262">SequenceAcknowledgement</span></span>

<span data-ttu-id="e4b23-263">O iniciador do WCF processa confirmações na resposta de todas as mensagens, exceto a mensagem de `CreateSequence` e mensagens de falha.</span><span class="sxs-lookup"><span data-stu-id="e4b23-263">The WCF Initiator processes acknowledgements on the reply of all messages except the `CreateSequence` message and fault messages.</span></span> <span data-ttu-id="e4b23-264">O respondente do WCF sempre transmite uma confirmação autônoma na resposta HTTP para todas as mensagens de sequência e `AckRequested`.</span><span class="sxs-lookup"><span data-stu-id="e4b23-264">The WCF Responder always transmits a stand-alone acknowledgement on the HTTP response to all sequence and `AckRequested` messages.</span></span>

#### <a name="closesequence-exchange"></a><span data-ttu-id="e4b23-265">CloseSequence Exchange</span><span class="sxs-lookup"><span data-stu-id="e4b23-265">CloseSequence Exchange</span></span>

<span data-ttu-id="e4b23-266">O iniciador do WCF transmite uma mensagem de `CloseSequence` em uma solicitação HTTP e espera a mensagem de `CreateSequenceResponse` na resposta HTTP.</span><span class="sxs-lookup"><span data-stu-id="e4b23-266">The WCF Initiator transmits a `CloseSequence` message on an HTTP request and expects the `CreateSequenceResponse` message on the HTTP response.</span></span> <span data-ttu-id="e4b23-267">O respondente do WCF transmite a mensagem de `CloseSequenceResponse` na resposta HTTP.</span><span class="sxs-lookup"><span data-stu-id="e4b23-267">The WCF Responder transmits the `CloseSequenceResponse` message on the HTTP response.</span></span>

#### <a name="terminatesequence-exchange"></a><span data-ttu-id="e4b23-268">Troca de TerminateSequence</span><span class="sxs-lookup"><span data-stu-id="e4b23-268">TerminateSequence Exchange</span></span>

<span data-ttu-id="e4b23-269">O iniciador do WCF transmite uma mensagem de `TerminateSequence` em uma solicitação HTTP e espera a mensagem de `TerminateSequenceResponse` na resposta HTTP.</span><span class="sxs-lookup"><span data-stu-id="e4b23-269">The WCF Initiator transmits a `TerminateSequence` message on an HTTP request and expects the `TerminateSequenceResponse` message on the HTTP response.</span></span> <span data-ttu-id="e4b23-270">O respondente do WCF transmite a mensagem de `TerminateSequenceResponse` na resposta HTTP.</span><span class="sxs-lookup"><span data-stu-id="e4b23-270">The WCF Responder transmits the `TerminateSequenceResponse` message on the HTTP response.</span></span>

### <a name="one-way-addressable-initiator"></a><span data-ttu-id="e4b23-271">Iniciador endereçável unidirecional</span><span class="sxs-lookup"><span data-stu-id="e4b23-271">One Way, Addressable Initiator</span></span>

#### <a name="binding"></a><span data-ttu-id="e4b23-272">Associação</span><span class="sxs-lookup"><span data-stu-id="e4b23-272">Binding</span></span>

<span data-ttu-id="e4b23-273">O WCF fornece um padrão de troca de mensagens unidirecional usando uma sequência em um canal HTTP de entrada e um de saída.</span><span class="sxs-lookup"><span data-stu-id="e4b23-273">WCF provides a one-way message exchange pattern using one sequence over one inbound and one outbound HTTP channel.</span></span> <span data-ttu-id="e4b23-274">O WCF usa as solicitações HTTP para transmitir todas as mensagens.</span><span class="sxs-lookup"><span data-stu-id="e4b23-274">WCF uses the HTTP requests to transmit all messages.</span></span> <span data-ttu-id="e4b23-275">Todas as respostas HTTP têm um corpo vazio e um código de status HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="e4b23-275">All HTTP responses have an empty body and HTTP 202 status code.</span></span>

#### <a name="createsequence-exchange"></a><span data-ttu-id="e4b23-276">Exchange CreateSequence</span><span class="sxs-lookup"><span data-stu-id="e4b23-276">CreateSequence Exchange</span></span>

<span data-ttu-id="e4b23-277">O iniciador do WCF transmite uma mensagem de `CreateSequence` sem elemento `Offer` em uma solicitação HTTP.</span><span class="sxs-lookup"><span data-stu-id="e4b23-277">The WCF Initiator transmits a `CreateSequence` message with no `Offer` element on an HTTP request.</span></span> <span data-ttu-id="e4b23-278">O respondente do WCF cria uma sequência e transmite a mensagem de `CreateSequenceResponse` sem elemento `Accept` em uma solicitação HTTP.</span><span class="sxs-lookup"><span data-stu-id="e4b23-278">The WCF Responder creates a sequence and transmits the `CreateSequenceResponse` message with no `Accept` element on an HTTP request.</span></span>

### <a name="duplex-addressable-initiator"></a><span data-ttu-id="e4b23-279">Iniciador duplex, endereçável</span><span class="sxs-lookup"><span data-stu-id="e4b23-279">Duplex, Addressable Initiator</span></span>

#### <a name="binding"></a><span data-ttu-id="e4b23-280">Associação</span><span class="sxs-lookup"><span data-stu-id="e4b23-280">Binding</span></span>

<span data-ttu-id="e4b23-281">O WCF fornece um padrão de troca de mensagens bidirecional, totalmente assíncrono, usando duas sequências em um canal HTTP de entrada e um de saída.</span><span class="sxs-lookup"><span data-stu-id="e4b23-281">WCF provides a fully-asynchronous, two-way message exchange pattern using two sequences over one inbound and one outbound HTTP channel.</span></span> <span data-ttu-id="e4b23-282">Esse padrão de troca de mensagens pode ser misturado com o `Request/Reply`, `Addressable` padrão de troca de mensagens do iniciador de uma maneira limitada.</span><span class="sxs-lookup"><span data-stu-id="e4b23-282">This message exchange pattern can be mixed with the `Request/Reply`, `Addressable` Initiator message exchange pattern in a limited way.</span></span> <span data-ttu-id="e4b23-283">O WCF usa solicitações HTTP para transmitir todas as mensagens.</span><span class="sxs-lookup"><span data-stu-id="e4b23-283">WCF uses HTTP requests to transmit all messages.</span></span> <span data-ttu-id="e4b23-284">Todas as respostas HTTP têm um corpo vazio e um código de status HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="e4b23-284">All HTTP responses have an empty body and HTTP 202 status code.</span></span>

#### <a name="createsequence-exchange"></a><span data-ttu-id="e4b23-285">Exchange CreateSequence</span><span class="sxs-lookup"><span data-stu-id="e4b23-285">CreateSequence Exchange</span></span>

<span data-ttu-id="e4b23-286">O iniciador do WCF transmite uma mensagem de `CreateSequence` com um elemento `Offer` em uma solicitação HTTP.</span><span class="sxs-lookup"><span data-stu-id="e4b23-286">The WCF Initiator transmits a `CreateSequence` message with an `Offer` element on an HTTP request.</span></span> <span data-ttu-id="e4b23-287">O respondente do WCF garante que o `CreateSequence` tenha um elemento `Offer` e, em seguida, crie uma sequência e transmita a mensagem `CreateSequenceResponse` com um elemento `Accept`.</span><span class="sxs-lookup"><span data-stu-id="e4b23-287">The WCF Responder ensures that the `CreateSequence` has an `Offer` element, then creates a sequence and transmits the `CreateSequenceResponse` message with an `Accept` element.</span></span>

#### <a name="sequence-lifetime"></a><span data-ttu-id="e4b23-288">Tempo de vida da sequência</span><span class="sxs-lookup"><span data-stu-id="e4b23-288">Sequence Lifetime</span></span>

<span data-ttu-id="e4b23-289">O WCF trata as duas sequências como uma sessão totalmente duplex.</span><span class="sxs-lookup"><span data-stu-id="e4b23-289">WCF treats the two sequences as one fully-duplex session.</span></span>

<span data-ttu-id="e4b23-290">Ao gerar uma falha que apresenta uma sequência, o WCF espera que o ponto de extremidade remoto tenha uma falha nas duas sequências.</span><span class="sxs-lookup"><span data-stu-id="e4b23-290">Upon generating a fault that faults one sequence, WCF expects the remote endpoint to fault both sequences.</span></span> <span data-ttu-id="e4b23-291">Após a leitura de uma falha que falha em uma sequência, o WCF falha em ambas as sequências.</span><span class="sxs-lookup"><span data-stu-id="e4b23-291">Upon reading a fault that faults one sequence, WCF faults both sequences.</span></span>

<span data-ttu-id="e4b23-292">O WCF pode fechar sua sequência de saída e continuar a processar mensagens em sua sequência de entrada.</span><span class="sxs-lookup"><span data-stu-id="e4b23-292">WCF can close its outbound sequence and continue to process messages on its inbound sequence.</span></span> <span data-ttu-id="e4b23-293">Por outro lado, o WCF pode processar o fechamento da sequência de entrada e continuar a enviar mensagens em sua sequência de saída.</span><span class="sxs-lookup"><span data-stu-id="e4b23-293">Conversely, WCF can process the close of the inbound sequence and continue to send messages on its outbound sequence.</span></span>

### <a name="request-reply-and-one-way-non-addressable-initiator"></a><span data-ttu-id="e4b23-294">Solicitação-resposta e iniciador unidirecional, não endereçável</span><span class="sxs-lookup"><span data-stu-id="e4b23-294">Request-Reply and One-Way, Non-Addressable Initiator</span></span>

#### <a name="binding"></a><span data-ttu-id="e4b23-295">Associação</span><span class="sxs-lookup"><span data-stu-id="e4b23-295">Binding</span></span>

<span data-ttu-id="e4b23-296">O WCF fornece um padrão de troca de mensagens unidirecional e de solicitação-resposta usando duas sequências em um canal HTTP.</span><span class="sxs-lookup"><span data-stu-id="e4b23-296">WCF provides a one-way and request-reply message exchange pattern using two sequences over one HTTP channel.</span></span> <span data-ttu-id="e4b23-297">O WCF usa solicitações HTTP para transmitir todas as mensagens do iniciador para o respondente e respostas HTTP para transmitir todas as mensagens do Respondente para o iniciador.</span><span class="sxs-lookup"><span data-stu-id="e4b23-297">WCF uses HTTP requests to transmit all messages from the Initiator to the Responder and HTTP responses to transmit all messages from the Responder to the Initiator.</span></span>

#### <a name="createsequence-exchange"></a><span data-ttu-id="e4b23-298">Exchange CreateSequence</span><span class="sxs-lookup"><span data-stu-id="e4b23-298">CreateSequence Exchange</span></span>

<span data-ttu-id="e4b23-299">O iniciador do WCF transmite uma mensagem de `CreateSequence` com um elemento `Offer` em uma solicitação HTTP e espera a mensagem de `CreateSequenceResponse` na resposta HTTP.</span><span class="sxs-lookup"><span data-stu-id="e4b23-299">The WCF Initiator transmits a `CreateSequence` message with an `Offer` element on an HTTP request and expects the `CreateSequenceResponse` message on the HTTP response.</span></span> <span data-ttu-id="e4b23-300">O respondente do WCF cria uma sequência e transmite a mensagem de `CreateSequenceResponse` com um elemento `Accept` na resposta HTTP.</span><span class="sxs-lookup"><span data-stu-id="e4b23-300">The WCF Responder creates a sequence and transmits the `CreateSequenceResponse` message with an `Accept` element on the HTTP response.</span></span>

#### <a name="one-way-message"></a><span data-ttu-id="e4b23-301">Mensagem unidirecional</span><span class="sxs-lookup"><span data-stu-id="e4b23-301">One-way Message</span></span>

<span data-ttu-id="e4b23-302">Para concluir uma troca de mensagens unidirecional com êxito, o iniciador do WCF transmite uma mensagem de sequência de solicitação na solicitação HTTP e recebe uma mensagem `SequenceAcknowledgement` autônoma na resposta HTTP.</span><span class="sxs-lookup"><span data-stu-id="e4b23-302">To complete a one-way message exchange successfully, the WCF Initiator transmits a request sequence message on the HTTP request and receives a standalone `SequenceAcknowledgement` message on the HTTP response.</span></span> <span data-ttu-id="e4b23-303">O `SequenceAcknowledgement` deve reconhecer a mensagem transmitida.</span><span class="sxs-lookup"><span data-stu-id="e4b23-303">The `SequenceAcknowledgement` must acknowledge the message transmitted.</span></span>

<span data-ttu-id="e4b23-304">O respondente do WCF pode responder à solicitação com uma confirmação, uma falha ou uma resposta com um corpo vazio e um código de status HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="e4b23-304">The WCF Responder may reply to the request with an acknowledgement, a fault, or a response with an empty body and HTTP 202 status code.</span></span>

#### <a name="two-way-messages"></a><span data-ttu-id="e4b23-305">Mensagens de duas vias</span><span class="sxs-lookup"><span data-stu-id="e4b23-305">Two Way Messages</span></span>

<span data-ttu-id="e4b23-306">Para concluir com êxito um protocolo de troca de mensagens de duas vias, o iniciador do WCF transmite uma mensagem de sequência de solicitação na solicitação HTTP e recebe uma mensagem de sequência de resposta na resposta HTTP.</span><span class="sxs-lookup"><span data-stu-id="e4b23-306">To complete a two way message exchange protocol successfully, the WCF Initiator transmits a request sequence message on the HTTP request and receives a reply sequence message on the HTTP response.</span></span> <span data-ttu-id="e4b23-307">A resposta deve transportar um `SequenceAcknowledgement` confirmando a mensagem de sequência de solicitação transmitida.</span><span class="sxs-lookup"><span data-stu-id="e4b23-307">The response must carry a `SequenceAcknowledgement` acknowledging the request sequence message transmitted.</span></span>

<span data-ttu-id="e4b23-308">O respondente do WCF pode responder à solicitação com uma resposta do aplicativo, uma falha ou uma resposta com um corpo vazio e um código de status HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="e4b23-308">The WCF Responder may reply to the request with an application reply, a fault or a response with an empty body and HTTP 202 status code.</span></span>

<span data-ttu-id="e4b23-309">Devido à presença de mensagens unidirecionais e do tempo das respostas do aplicativo, o número de sequência da mensagem da sequência de solicitação e o número de sequência da mensagem de resposta não têm nenhuma correlação.</span><span class="sxs-lookup"><span data-stu-id="e4b23-309">Because of the presence of one-way messages and the timing of application replies, the request sequence message’s sequence number and the response message’s sequence number have no correlation.</span></span>

#### <a name="retrying-replies"></a><span data-ttu-id="e4b23-310">Repetindo respostas</span><span class="sxs-lookup"><span data-stu-id="e4b23-310">Retrying Replies</span></span>

<span data-ttu-id="e4b23-311">O WCF conta com correlação de solicitação-resposta HTTP para correlação de protocolo de troca de mensagens bidirecional.</span><span class="sxs-lookup"><span data-stu-id="e4b23-311">WCF relies on HTTP request-reply correlation for two-way message exchange protocol correlation.</span></span> <span data-ttu-id="e4b23-312">Por isso, o iniciador do WCF não pára de repetir uma mensagem de sequência de solicitação quando a mensagem de sequência de solicitação é confirmada, mas quando a resposta HTTP carrega um `SequenceAcknowledgement`, uma resposta de aplicativo ou uma falha.</span><span class="sxs-lookup"><span data-stu-id="e4b23-312">Because of this, the WCF Initiator does not stop retrying a request sequence message when the request sequence message is acknowledged but rather when the HTTP response carries a `SequenceAcknowledgement`, application reply, or fault.</span></span> <span data-ttu-id="e4b23-313">O respondente do WCF tenta respostas novamente na resposta HTTP da solicitação à qual a resposta está correlacionada.</span><span class="sxs-lookup"><span data-stu-id="e4b23-313">The WCF Responder retries replies on the HTTP response of the request to which the reply is correlated.</span></span>

#### <a name="closesequence-exchange"></a><span data-ttu-id="e4b23-314">CloseSequence Exchange</span><span class="sxs-lookup"><span data-stu-id="e4b23-314">CloseSequence Exchange</span></span>

<span data-ttu-id="e4b23-315">Depois de receber todas as mensagens de sequência de resposta e confirmações de todas as mensagens de sequência de solicitação de uma única maneira, o iniciador do WCF transmite uma mensagem de `CloseSequence` para a sequência de solicitação em uma solicitação HTTP e espera a `CloseSequenceResponse` na resposta HTTP.</span><span class="sxs-lookup"><span data-stu-id="e4b23-315">After receiving all reply sequence messages and acknowledgements for all one way request sequence messages, the WCF Initiator transmits a `CloseSequence` message for the request sequence on an HTTP request and expects the `CloseSequenceResponse` on the HTTP response.</span></span>

<span data-ttu-id="e4b23-316">Fechar a sequência de solicitação fecha implicitamente a sequência de resposta.</span><span class="sxs-lookup"><span data-stu-id="e4b23-316">Closing the request sequence implicitly closes the reply sequence.</span></span> <span data-ttu-id="e4b23-317">Isso significa que o iniciador do WCF inclui a `SequenceAcknowledgement` final da sequência de respostas na mensagem de `CloseSequence` e a sequência de resposta não tem um `CloseSequence` Exchange.</span><span class="sxs-lookup"><span data-stu-id="e4b23-317">This means the WCF Initiator includes the reply sequence’s Final `SequenceAcknowledgement` on the `CloseSequence` message and the reply sequence does not have a `CloseSequence` exchange.</span></span>

<span data-ttu-id="e4b23-318">O respondente do WCF garante que todas as respostas sejam confirmadas e transmite a mensagem de `CloseSequenceResponse` na resposta HTTP.</span><span class="sxs-lookup"><span data-stu-id="e4b23-318">The WCF Responder ensures all replies are acknowledged and transmits the `CloseSequenceResponse` message on the HTTP response.</span></span>

#### <a name="terminatesequence-exchange"></a><span data-ttu-id="e4b23-319">Troca de TerminateSequence</span><span class="sxs-lookup"><span data-stu-id="e4b23-319">TerminateSequence Exchange</span></span>

<span data-ttu-id="e4b23-320">Depois de receber a mensagem de `CloseSequenceResponse`, o iniciador do WCF transmite uma mensagem de `TerminateSequence` para a sequência de solicitação em uma solicitação HTTP e espera a `TerminateSequenceResponse` na resposta HTTP.</span><span class="sxs-lookup"><span data-stu-id="e4b23-320">After receiving the `CloseSequenceResponse` message, the WCF Initiator transmits a `TerminateSequence` message for the request sequence on an HTTP request and expects the `TerminateSequenceResponse` on the HTTP response.</span></span>

<span data-ttu-id="e4b23-321">Como o `CloseSequence` Exchange, encerrar a sequência de solicitação encerra implicitamente a sequência de resposta.</span><span class="sxs-lookup"><span data-stu-id="e4b23-321">Like the `CloseSequence` exchange, terminating the request sequence implicitly terminates the reply sequence.</span></span> <span data-ttu-id="e4b23-322">Isso significa que o iniciador do WCF inclui a `SequenceAcknowledgement` final da sequência de respostas na mensagem de `TerminateSequence` e a sequência de resposta não tem um `TerminateSequence` Exchange.</span><span class="sxs-lookup"><span data-stu-id="e4b23-322">This means the WCF Initiator includes the reply sequence’s final `SequenceAcknowledgement` on the `TerminateSequence` message and the reply sequence does not have a `TerminateSequence` exchange.</span></span>

<span data-ttu-id="e4b23-323">O respondente do WCF transmite a mensagem de `TerminateSequenceResponse` na resposta HTTP.</span><span class="sxs-lookup"><span data-stu-id="e4b23-323">The WCF Responder transmits the `TerminateSequenceResponse` message on the HTTP response.</span></span>

### <a name="requestreply-addressable-initiator"></a><span data-ttu-id="e4b23-324">Solicitação/resposta, iniciador endereçável</span><span class="sxs-lookup"><span data-stu-id="e4b23-324">Request/Reply, Addressable Initiator</span></span>

#### <a name="binding"></a><span data-ttu-id="e4b23-325">Associação</span><span class="sxs-lookup"><span data-stu-id="e4b23-325">Binding</span></span>

<span data-ttu-id="e4b23-326">O WCF fornece um padrão de troca de mensagens de solicitação-resposta usando duas sequências em um canal HTTP de entrada e um de saída.</span><span class="sxs-lookup"><span data-stu-id="e4b23-326">WCF provides a request-reply message exchange pattern using two sequences over one inbound and one outbound HTTP channel.</span></span> <span data-ttu-id="e4b23-327">Esse padrão de troca de mensagens pode ser misturado com o padrão de troca de mensagens do iniciador `Duplex, Addressable` de forma limitada.</span><span class="sxs-lookup"><span data-stu-id="e4b23-327">This message exchange pattern can be mixed with the `Duplex, Addressable` Initiator message exchange pattern in a limited way.</span></span> <span data-ttu-id="e4b23-328">O WCF usa as solicitações HTTP para transmitir todas as mensagens.</span><span class="sxs-lookup"><span data-stu-id="e4b23-328">WCF uses the HTTP requests to transmit all messages.</span></span> <span data-ttu-id="e4b23-329">Todas as respostas HTTP têm um corpo vazio e um código de status HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="e4b23-329">All HTTP responses have an empty body and HTTP 202 status code.</span></span>

#### <a name="createsequence-exchange"></a><span data-ttu-id="e4b23-330">Exchange CreateSequence</span><span class="sxs-lookup"><span data-stu-id="e4b23-330">CreateSequence Exchange</span></span>

<span data-ttu-id="e4b23-331">O iniciador do WCF transmite uma mensagem de `CreateSequence` com um elemento `Offer` em uma solicitação HTTP.</span><span class="sxs-lookup"><span data-stu-id="e4b23-331">The WCF Initiator transmits a `CreateSequence` message with an `Offer` element on an HTTP request.</span></span> <span data-ttu-id="e4b23-332">O respondente do WCF garante que o `CreateSequence` tenha um elemento `Offer`, em seguida, crie uma sequência e transmita a mensagem `CreateSequenceResponse` com um elemento `Accept`.</span><span class="sxs-lookup"><span data-stu-id="e4b23-332">The WCF Responder ensures that the `CreateSequence` has an `Offer` element then creates a sequence and transmits the `CreateSequenceResponse` message with an `Accept` element.</span></span>

#### <a name="requestreply-correlation"></a><span data-ttu-id="e4b23-333">Correlação de solicitação/resposta</span><span class="sxs-lookup"><span data-stu-id="e4b23-333">Request/Reply Correlation</span></span>

<span data-ttu-id="e4b23-334">O seguinte se aplica a todas as solicitações e respostas correlacionadas:</span><span class="sxs-lookup"><span data-stu-id="e4b23-334">The following applies to all correlated requests and replies:</span></span>

- <span data-ttu-id="e4b23-335">O WCF garante que todas as mensagens de solicitação de aplicativo tenham uma referência de ponto de extremidade `ReplyTo` e uma `MessageId`.</span><span class="sxs-lookup"><span data-stu-id="e4b23-335">WCF ensures all application request messages bear a `ReplyTo` endpoint reference and a `MessageId`.</span></span>

- <span data-ttu-id="e4b23-336">O WCF aplica a referência de ponto de extremidade local à medida que cada mensagem de solicitação de aplicativo `ReplyTo`.</span><span class="sxs-lookup"><span data-stu-id="e4b23-336">WCF applies the local endpoint reference as each application request message’s `ReplyTo`.</span></span> <span data-ttu-id="e4b23-337">A referência do ponto de extremidade local é a `ReplyTo` da `CreateSequence` da mensagem para o iniciador e a `To` da mensagem do `CreateSequence` para o respondente.</span><span class="sxs-lookup"><span data-stu-id="e4b23-337">The local endpoint reference is the `CreateSequence` message’s `ReplyTo` for the Initiator and the `CreateSequence` message’s `To` for the Responder.</span></span>

- <span data-ttu-id="e4b23-338">O WCF garante que as mensagens de solicitação de entrada tenham uma `MessageId` e uma `ReplyTo`.</span><span class="sxs-lookup"><span data-stu-id="e4b23-338">WCF ensures that incoming request messages bear a `MessageId` and a `ReplyTo`.</span></span>

- <span data-ttu-id="e4b23-339">O WCF garante que o URI de referência de ponto de extremidade `ReplyTo` de todas as mensagens de solicitação de aplicativo corresponda à referência de ponto de extremidade local conforme definido anteriormente.</span><span class="sxs-lookup"><span data-stu-id="e4b23-339">WCF ensures the `ReplyTo` endpoint reference’s URI of all application request messages match the local endpoint reference as defined earlier.</span></span>

- <span data-ttu-id="e4b23-340">O WCF garante que todas as respostas contenham os cabeçalhos corretos de `RelatesTo` e de `To` seguintes `wsa` regras de correlação de solicitação/resposta.</span><span class="sxs-lookup"><span data-stu-id="e4b23-340">WCF ensures that all replies bear the correct `RelatesTo` and `To` headers following `wsa` request/reply correlation rules.</span></span>
