---
title: Protocolo de mensagem confiável versão 1.1
ms.date: 03/30/2017
ms.assetid: 0da47b82-f8eb-42da-8bfe-e56ce7ba6f59
ms.openlocfilehash: 6b8732e0b48797c219b53bb8bf70e1ba57e25c42
ms.sourcegitcommit: d9a0071d0fd490ae006c816f78a563b9946e269a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/26/2019
ms.locfileid: "55073220"
---
# <a name="reliable-messaging-protocol-version-11"></a><span data-ttu-id="abcae-102">Protocolo de mensagem confiável versão 1.1</span><span class="sxs-lookup"><span data-stu-id="abcae-102">Reliable Messaging Protocol version 1.1</span></span>
<span data-ttu-id="abcae-103">Este tópico abrange detalhes de implementação do Windows Communication Foundation (WCF) para o WS-ReliableMessaging necessárias para usar o transporte HTTP de interoperação de protocolo de fevereiro de 2007 (versão 1.1).</span><span class="sxs-lookup"><span data-stu-id="abcae-103">This topic covers Windows Communication Foundation (WCF) implementation details for the WS-ReliableMessaging February 2007 (version 1.1) protocol necessary for interoperation using the HTTP transport.</span></span> <span data-ttu-id="abcae-104">WCF segue a especificação de WS-ReliableMessaging com as restrições e esclarecimentos explicados neste tópico.</span><span class="sxs-lookup"><span data-stu-id="abcae-104">WCF follows the WS-ReliableMessaging specification with the constraints and clarifications explained in this topic.</span></span> <span data-ttu-id="abcae-105">Observe que o protocolo de versão 1.1 WS-ReliableMessaging é implementado começando com o [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="abcae-105">Note that the WS-ReliableMessaging version 1.1 protocol is implemented starting with the [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)].</span></span>  
  
 <span data-ttu-id="abcae-106">O WS-ReliableMessaging de fevereiro de 2007 protocolo é implementado no WCF, o <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="abcae-106">The WS-ReliableMessaging February 2007 protocol is implemented in WCF by the <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>.</span></span>  
  
 <span data-ttu-id="abcae-107">Para sua conveniência, o tópico usa as seguintes funções:</span><span class="sxs-lookup"><span data-stu-id="abcae-107">For convenience, the topic uses the following roles:</span></span>  
  
-   <span data-ttu-id="abcae-108">Iniciador: O cliente que inicia a criação da sequência de mensagens WS-Reliable.</span><span class="sxs-lookup"><span data-stu-id="abcae-108">Initiator: The client that initiates WS-Reliable Message sequence creation.</span></span>  
  
-   <span data-ttu-id="abcae-109">Respondente: O serviço que recebe solicitações do iniciador.</span><span class="sxs-lookup"><span data-stu-id="abcae-109">Responder: The service that receives the initiator's requests.</span></span>  
  
 <span data-ttu-id="abcae-110">Este documento usa os prefixos e namespaces na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="abcae-110">This document uses the prefixes and namespaces in the following table.</span></span>  
  
|<span data-ttu-id="abcae-111">Prefixo</span><span class="sxs-lookup"><span data-stu-id="abcae-111">Prefix</span></span>|<span data-ttu-id="abcae-112">Namespace</span><span class="sxs-lookup"><span data-stu-id="abcae-112">Namespace</span></span>|  
|-|-|  
|<span data-ttu-id="abcae-113">wsrm</span><span class="sxs-lookup"><span data-stu-id="abcae-113">wsrm</span></span>|http://docs.oasis-open.org/ws-rx/wsrm/200702|  
|<span data-ttu-id="abcae-114">netrm</span><span class="sxs-lookup"><span data-stu-id="abcae-114">netrm</span></span>|http://schemas.microsoft.com/ws/2006/05/rm|  
|<span data-ttu-id="abcae-115">s</span><span class="sxs-lookup"><span data-stu-id="abcae-115">s</span></span>|http://www.w3.org/2003/05/soap-envelope|  
|<span data-ttu-id="abcae-116">wsa</span><span class="sxs-lookup"><span data-stu-id="abcae-116">wsa</span></span>|http://schemas.xmlsoap.org/ws/2005/08/addressing|  
|<span data-ttu-id="abcae-117">wsse</span><span class="sxs-lookup"><span data-stu-id="abcae-117">wsse</span></span>|http://docs.oasis-open.org/wss/2004/01/oasis-200401-wssecurity-secext-1.0.xsd|  
|<span data-ttu-id="abcae-118">wsrmp</span><span class="sxs-lookup"><span data-stu-id="abcae-118">wsrmp</span></span>|http://docs.oasis-open.org/ws-rx/wsrmp/200702|  
|<span data-ttu-id="abcae-119">netrmp</span><span class="sxs-lookup"><span data-stu-id="abcae-119">netrmp</span></span>|http://schemas.microsoft.com/ws-rx/wsrmp/200702|  
|<span data-ttu-id="abcae-120">wsp</span><span class="sxs-lookup"><span data-stu-id="abcae-120">wsp</span></span>|<span data-ttu-id="abcae-121">(WS-Policy 1.2 ou WS-Policy 1.5)</span><span class="sxs-lookup"><span data-stu-id="abcae-121">(Either WS-Policy 1.2 or WS-Policy 1.5)</span></span>|  
  
## <a name="messaging"></a><span data-ttu-id="abcae-122">Mensagens</span><span class="sxs-lookup"><span data-stu-id="abcae-122">Messaging</span></span>  
  
### <a name="sequence-creation"></a><span data-ttu-id="abcae-123">Criação da sequência</span><span class="sxs-lookup"><span data-stu-id="abcae-123">Sequence Creation</span></span>  
 <span data-ttu-id="abcae-124">O WCF implementa `CreateSequence` e `CreateSequenceResponse` mensagens para estabelecer um sistema de mensagens confiável de sequência.</span><span class="sxs-lookup"><span data-stu-id="abcae-124">WCF implements `CreateSequence` and `CreateSequenceResponse` messages to establish a reliable messaging sequence.</span></span> <span data-ttu-id="abcae-125">As seguintes restrições se aplicam:</span><span class="sxs-lookup"><span data-stu-id="abcae-125">The following constraints apply:</span></span>  
  
-   <span data-ttu-id="abcae-126">B1101: O iniciador do WCF usa a mesma referência de ponto de extremidade como o `CreateSequence` da mensagem `ReplyTo`, `AcksTo` e `Offer/Endpoint`.</span><span class="sxs-lookup"><span data-stu-id="abcae-126">B1101: The WCF Initiator uses the same endpoint reference as the `CreateSequence` message’s `ReplyTo`, `AcksTo` and `Offer/Endpoint`.</span></span>  
  
-   <span data-ttu-id="abcae-127">R1102: O `AcksTo`, `ReplyTo` e `Offer/Endpoint` referências de ponto de extremidade no `CreateSequence` mensagem deve ter valores de endereço com representações de cadeia de caracteres idêntica, de modo que eles correspondam a octet-wise.</span><span class="sxs-lookup"><span data-stu-id="abcae-127">R1102: The `AcksTo`, `ReplyTo` and `Offer/Endpoint` endpoint references in the `CreateSequence` message must have address values with identical string representations such that they match the octet-wise.</span></span>  
  
    -   <span data-ttu-id="abcae-128">O WCF respondente verifica se a parte do URI de `AcksTo`, `ReplyTo` e `Endpoint` referências de ponto de extremidade são idênticas antes de criar uma sequência.</span><span class="sxs-lookup"><span data-stu-id="abcae-128">The WCF Responder verifies that the URI portion of the `AcksTo`, `ReplyTo` and `Endpoint` endpoint references are identical before creating a sequence.</span></span>  
  
-   <span data-ttu-id="abcae-129">R1103: O `AcksTo`, `ReplyTo` e `Offer/Endpoint` referências de ponto de extremidade no `CreateSequence` mensagem deve ter o mesmo conjunto de parâmetros de referência.</span><span class="sxs-lookup"><span data-stu-id="abcae-129">R1103: The `AcksTo`, `ReplyTo` and `Offer/Endpoint` endpoint references in the `CreateSequence` message should have the same set of reference parameters.</span></span>  
  
    -   <span data-ttu-id="abcae-130">WCF não impõe, mas presume que fazem referência parâmetros do `AcksTo`, `ReplyTo` e `Offer/Endpoint` ponto de extremidade faz referência na `CreateSequence` são idênticos e usa os parâmetros de referência do `ReplyTo` referência de ponto de extremidade para as confirmações e mensagens de sequência inverso.</span><span class="sxs-lookup"><span data-stu-id="abcae-130">WCF does not enforce, but assumes that reference parameters of the `AcksTo`, `ReplyTo` and `Offer/Endpoint` endpoint references on `CreateSequence` are identical and uses reference parameters from the `ReplyTo` endpoint reference for acknowledgements and converse sequence messages.</span></span>  
  
-   <span data-ttu-id="abcae-131">B1104: O iniciador do WCF não gera opcional `Expires` ou `Offer/Expires` elemento o `CreateSequence` mensagem.</span><span class="sxs-lookup"><span data-stu-id="abcae-131">B1104: The WCF Initiator does not generate the optional `Expires` or `Offer/Expires` element in the `CreateSequence` message.</span></span>  
  
-   <span data-ttu-id="abcae-132">B1105: Ao acessar o `CreateSequence` mensagem, o respondente do WCF usa o `Expires` valor na `CreateSequence` elemento como o `Expires` valor no `CreateSequenceResponse` elemento.</span><span class="sxs-lookup"><span data-stu-id="abcae-132">B1105: When accessing the `CreateSequence` message, the WCF Responder uses the `Expires` value in the `CreateSequence` element as the `Expires` value in the `CreateSequenceResponse` element.</span></span> <span data-ttu-id="abcae-133">Caso contrário, o Respondente WCF lê e ignora a `Expires` e `Offer/Expires` valores.</span><span class="sxs-lookup"><span data-stu-id="abcae-133">Otherwise, the WCF Responder reads and ignores the `Expires` and `Offer/Expires` values.</span></span>  
  
-   <span data-ttu-id="abcae-134">B1106: Ao acessar o `CreateSequenceResponse` mensagem, o iniciador do WCF lê opcional `Expires` valor, mas não usá-lo.</span><span class="sxs-lookup"><span data-stu-id="abcae-134">B1106: When accessing the `CreateSequenceResponse` message, the WCF Initiator reads the optional `Expires` value but does not use it.</span></span>  
  
-   <span data-ttu-id="abcae-135">B1107: O iniciador do WCF e o Respondente sempre geram opcional `IncompleteSequenceBehavior` elemento na `CreateSequence/Offer` e `CreateSequenceResponse` elementos.</span><span class="sxs-lookup"><span data-stu-id="abcae-135">B1107: The WCF Initiator and Responder always generate the optional `IncompleteSequenceBehavior` element in the `CreateSequence/Offer` and `CreateSequenceResponse` elements.</span></span>  
  
-   <span data-ttu-id="abcae-136">B1108: O WCF usa apenas o `DiscardFollowingFirstGap` e `NoDiscard` os valores no `IncompleteSequenceBehavior` elemento.</span><span class="sxs-lookup"><span data-stu-id="abcae-136">B1108: WCF uses only the `DiscardFollowingFirstGap` and `NoDiscard` values in the `IncompleteSequenceBehavior` element.</span></span>  
  
    -   <span data-ttu-id="abcae-137">WS-ReliableMessaging utiliza o `Offer` mecanismo para estabelecer os dois conversam correlacionadas sequências que formam uma sessão.</span><span class="sxs-lookup"><span data-stu-id="abcae-137">WS-ReliableMessaging utilizes the `Offer` mechanism to establish the two converse correlated sequences that form a session.</span></span>  
  
-   <span data-ttu-id="abcae-138">B1109: Se `CreateSequence` contém uma `Offer` elemento, o Respondente unidirecional de WCF rejeita a sequência oferecida por responder com um `CreateSequenceResponse` sem um `Accept` elemento.</span><span class="sxs-lookup"><span data-stu-id="abcae-138">B1109: If `CreateSequence` contains an `Offer` element, the one way WCF Responder rejects the offered sequence by responding with a `CreateSequenceResponse` without an `Accept` element.</span></span>  
  
-   <span data-ttu-id="abcae-139">B1110: Se um Respondente de mensagens confiável rejeita a sequência oferecida, o iniciador do WCF falha em sequência recentemente estabelecida.</span><span class="sxs-lookup"><span data-stu-id="abcae-139">B1110: If a Reliable Messaging Responder rejects the offered sequence, the WCF Initiator faults the newly established sequence.</span></span>  
  
-   <span data-ttu-id="abcae-140">B1111: Se `CreateSequence` não contém um `Offer` elemento, o Respondente bidirecional de WCF rejeita a sequência oferecida por responder com um `CreateSequenceRefused` falha.</span><span class="sxs-lookup"><span data-stu-id="abcae-140">B1111: If `CreateSequence` does not contain an `Offer` element, the two-way WCF Responder rejects the offered sequence by responding with a `CreateSequenceRefused` fault.</span></span>  
  
-   <span data-ttu-id="abcae-141">R1112: Quando duas sequências inverso são estabelecidas usando o `Offer` mecanismo, o `[address]` propriedade da `CreateSequenceResponse/Accept/AcksTo` referência de ponto de extremidade deve coincidir com o URI de destino do `CreateSequence` byte de mensagem por byte.</span><span class="sxs-lookup"><span data-stu-id="abcae-141">R1112: When two converse sequences are established using the `Offer` mechanism, the `[address]` property of the `CreateSequenceResponse/Accept/AcksTo` endpoint reference must match the destination URI of the `CreateSequence` message byte for byte.</span></span>  
  
-   <span data-ttu-id="abcae-142">R1113: Quando duas sequências inverso são estabelecidas usando o `Offer` mecanismo, todas as mensagens em ambas as sequências que fluem do iniciador para o Respondente devem ser enviadas para a mesma referência de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="abcae-142">R1113: When two converse sequences are established using the `Offer` mechanism, all messages on both sequences flowing from the Initiator to the Responder must be sent to the same endpoint reference.</span></span>  
  
 <span data-ttu-id="abcae-143">O WCF usa WS-ReliableMessaging para estabelecer sessões confiáveis entre o iniciador e o respondente.</span><span class="sxs-lookup"><span data-stu-id="abcae-143">WCF uses WS-ReliableMessaging to establish reliable sessions between the Initiator and the Responder.</span></span> <span data-ttu-id="abcae-144">A implementação de WCF WS-ReliableMessaging fornece uma sessão confiável para unidirecional, solicitação-resposta e full duplex padrões de mensagens.</span><span class="sxs-lookup"><span data-stu-id="abcae-144">The WCF WS-ReliableMessaging implementation provides a reliable session for one-way, request-reply and full duplex messaging patterns.</span></span> <span data-ttu-id="abcae-145">O WS-ReliableMessaging `Offer` mecanismo `CreateSequence` e `CreateSequenceResponse` permite que você estabeleça inverso correlacionados duas sequências e fornece um protocolo de sessão que é adequado para todos os pontos de extremidade de mensagem.</span><span class="sxs-lookup"><span data-stu-id="abcae-145">The WS-ReliableMessaging `Offer` mechanism on `CreateSequence` and `CreateSequenceResponse` lets you establish two correlated converse sequences and provides a session protocol that is suitable for all message endpoints.</span></span> <span data-ttu-id="abcae-146">Como o WCF fornece uma garantia de segurança para essa sessão, incluindo a proteção de ponta a ponta para integridade de sessão, é prático garantir que as mensagens destinadas a mesma parte chegam ao mesmo destino.</span><span class="sxs-lookup"><span data-stu-id="abcae-146">Because WCF provides a security guarantee for such a session including end-to-end protection for session integrity, it is practical to ensure that messages intended for the same party arrive at the same destination.</span></span> <span data-ttu-id="abcae-147">Isso também permite "aproveitando" de confirmações de sequência em mensagens do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="abcae-147">This also allows "piggy-backing" of sequence acknowledgements on application messages.</span></span> <span data-ttu-id="abcae-148">Portanto, R1102, R1112 e R1113 de restrições se aplicam ao WCF.</span><span class="sxs-lookup"><span data-stu-id="abcae-148">Therefore, constraints R1102, R1112, and R1113 apply to WCF.</span></span>  
  
 <span data-ttu-id="abcae-149">Um exemplo de um `CreateSequence` mensagem.</span><span class="sxs-lookup"><span data-stu-id="abcae-149">An example of a `CreateSequence` message.</span></span>  
  
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
  
 <span data-ttu-id="abcae-150">Um exemplo de um `CreateSequenceResponse` mensagem.</span><span class="sxs-lookup"><span data-stu-id="abcae-150">An example of a `CreateSequenceResponse` message.</span></span>  
  
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
  
### <a name="closing-a-sequence"></a><span data-ttu-id="abcae-151">Uma sequência de fechamento</span><span class="sxs-lookup"><span data-stu-id="abcae-151">Closing a Sequence</span></span>  
 <span data-ttu-id="abcae-152">O WCF usa o `CloseSequence` e `CloseSequenceResponse` mensagens para um sistema de mensagens confiável desligamento iniciada pela origem.</span><span class="sxs-lookup"><span data-stu-id="abcae-152">WCF uses the `CloseSequence` and `CloseSequenceResponse` messages for a Reliable Messaging source-initiated shutdown.</span></span> <span data-ttu-id="abcae-153">O destino de sistema de mensagens confiável do WCF não iniciam o desligamento e a fonte de sistema de mensagens confiável do WCF não oferece suporte a um desligamento iniciado pelo destino mensagens confiáveis.</span><span class="sxs-lookup"><span data-stu-id="abcae-153">The WCF Reliable Messaging destination does not initiate shutdown and the WCF Reliable Messaging source does not support a Reliable Messaging destination-initiated shutdown.</span></span> <span data-ttu-id="abcae-154">As seguintes restrições se aplicam:</span><span class="sxs-lookup"><span data-stu-id="abcae-154">The following constraints apply:</span></span>  
  
-   <span data-ttu-id="abcae-155">B1201: A fonte de sistema de mensagens confiável do WCF sempre envia um `CloseSequence` mensagem para desligar a sequência.</span><span class="sxs-lookup"><span data-stu-id="abcae-155">B1201: The WCF Reliable Messaging source always sends a `CloseSequence` message to shut down the sequence.</span></span>  
  
-   <span data-ttu-id="abcae-156">B1202: A fonte de sistema de mensagens confiável aguarda a confirmação de toda a série de mensagens de sequência antes de enviar o `CloseSequence` mensagem.</span><span class="sxs-lookup"><span data-stu-id="abcae-156">B1202: The Reliable Messaging source waits for acknowledgement of the full range of sequence messages before sending the `CloseSequence` message.</span></span>  
  
-   <span data-ttu-id="abcae-157">B1203: A fonte de sistema de mensagens confiável sempre inclui opcional `LastMsgNumber` elemento, a menos que a sequência não contém mensagens.</span><span class="sxs-lookup"><span data-stu-id="abcae-157">B1203: The Reliable Messaging source always includes the optional `LastMsgNumber` element unless the sequence does not contain messages.</span></span>  
  
-   <span data-ttu-id="abcae-158">R1204: O destino de sistema de mensagens confiável não deve iniciar o desligamento, enviando um `CloseSequence` mensagem.</span><span class="sxs-lookup"><span data-stu-id="abcae-158">R1204: The Reliable Messaging destination must not initiate shutdown by sending a `CloseSequence` message.</span></span>  
  
-   <span data-ttu-id="abcae-159">B1205: Ao receber um `CloseSequence` mensagem, a fonte de sistema de mensagens confiável do WCF considera a sequência incompleta e envia uma falha.</span><span class="sxs-lookup"><span data-stu-id="abcae-159">B1205: Upon receiving a `CloseSequence` message, the WCF Reliable Messaging source considers the sequence incomplete and sends a fault.</span></span>  
  
 <span data-ttu-id="abcae-160">Um exemplo de um `CloseSequence` mensagem.</span><span class="sxs-lookup"><span data-stu-id="abcae-160">An example of a `CloseSequence` message.</span></span>  
  
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
  
### <a name="sequence-termination"></a><span data-ttu-id="abcae-161">Sequência de terminação</span><span class="sxs-lookup"><span data-stu-id="abcae-161">Sequence Termination</span></span>  
 <span data-ttu-id="abcae-162">O WCF usa principalmente o `TerminateSequence/TerminateSequenceResponse` handshake depois de concluir o `CloseSequence/CloseSequenceResponse` handshake.</span><span class="sxs-lookup"><span data-stu-id="abcae-162">WCF primarily uses the `TerminateSequence/TerminateSequenceResponse` handshake after completing the `CloseSequence/CloseSequenceResponse` handshake.</span></span> <span data-ttu-id="abcae-163">O destino de sistema de mensagens confiável do WCF não inicie o encerramento e a fonte de sistema de mensagens confiável não oferece suporte a um encerramento confiável de mensagens iniciado pelo destino.</span><span class="sxs-lookup"><span data-stu-id="abcae-163">The WCF Reliable Messaging destination does not initiate termination and the Reliable Messaging source does not support a Reliable Messaging destination-initiated termination.</span></span> <span data-ttu-id="abcae-164">As seguintes restrições se aplicam:</span><span class="sxs-lookup"><span data-stu-id="abcae-164">The following constraints apply:</span></span>  
  
-   <span data-ttu-id="abcae-165">B1301: O iniciador do WCF envia apenas o `TerminateSequence` mensagem após a conclusão bem-sucedida do `CloseSequence/CloseSequenceResponse` handshake.</span><span class="sxs-lookup"><span data-stu-id="abcae-165">B1301: The WCF Initiator only sends the `TerminateSequence` message after the successful completion of the `CloseSequence/CloseSequenceResponse` handshake.</span></span>  
  
-   <span data-ttu-id="abcae-166">R1302: WCF valida que o `LastMsgNumber` elemento é consistente em todos os `CloseSequence` e `TerminateSequence` mensagens para uma determinada sequência.</span><span class="sxs-lookup"><span data-stu-id="abcae-166">R1302: WCF validates that the `LastMsgNumber` element is consistent across all `CloseSequence` and `TerminateSequence` messages for a given sequence.</span></span> <span data-ttu-id="abcae-167">Isso significa que `LastMsgNumber` não está presente em todos os `CloseSequence` e `TerminateSequence` mensagens, ou ele está presente e idênticos em todos os `CloseSequence` e `TerminateSequence` mensagens.</span><span class="sxs-lookup"><span data-stu-id="abcae-167">This means that `LastMsgNumber` is either not present on all `CloseSequence` and `TerminateSequence` messages, or it is present and identical on all `CloseSequence` and `TerminateSequence` messages.</span></span>  
  
-   <span data-ttu-id="abcae-168">B1303: Ao receber um `TerminateSequence` da mensagem após o `CloseSequence/CloseSequenceResponse` handshake, o destino de sistema de mensagens confiável responde com um `TerminateSequenceResponse` mensagem.</span><span class="sxs-lookup"><span data-stu-id="abcae-168">B1303: When receiving a `TerminateSequence` message after the `CloseSequence/CloseSequenceResponse` handshake, the Reliable Messaging destination responds with a `TerminateSequenceResponse` message.</span></span> <span data-ttu-id="abcae-169">Como a origem do sistema de mensagens confiável tem a confirmação final antes de enviar o `TerminateSequence` mensagem, o destino de sistema de mensagens confiável sabe sem dúvida que a sequência termina e recupera os recursos imediatamente.</span><span class="sxs-lookup"><span data-stu-id="abcae-169">Because the Reliable Messaging source has the final acknowledgement before sending the `TerminateSequence` message, the Reliable Messaging destination knows without doubt that the sequence ends, and reclaims resources immediately.</span></span>  
  
-   <span data-ttu-id="abcae-170">B1304: Ao receber um `TerminateSequence` da mensagem antes do `CloseSequence/CloseSequenceResponse` handshake, o destino de sistema de mensagens confiável do WCF responde com um `TerminateSequenceResponse` mensagem.</span><span class="sxs-lookup"><span data-stu-id="abcae-170">B1304: When receiving a `TerminateSequence` message prior to the `CloseSequence/CloseSequenceResponse` handshake, the WCF Reliable Messaging destination responds with a `TerminateSequenceResponse` message.</span></span> <span data-ttu-id="abcae-171">Se o destino de sistema de mensagens confiável determina que não há nenhuma inconsistência na sequência, o destino de sistema de mensagens confiável aguarda uma hora especificada pelo destino do aplicativo antes da recuperação de recursos, para permitir que o cliente a oportunidade de receber a confirmação final.</span><span class="sxs-lookup"><span data-stu-id="abcae-171">If the Reliable Messaging destination determines that there are no inconsistencies in the sequence, the Reliable Messaging destination waits for an application destination-specified time before reclaiming resources, to allow the client the chance to receive the final acknowledgement.</span></span> <span data-ttu-id="abcae-172">Caso contrário, o destino de sistema de mensagens confiável recupera recursos imediatamente e indica para o destino do aplicativo que a sequência termina com caso de dúvida, gerando o `Faulted` eventos.</span><span class="sxs-lookup"><span data-stu-id="abcae-172">Otherwise, the Reliable Messaging destination reclaims resources immediately and indicates to the application destination that the sequence ends with doubt by raising the `Faulted` event.</span></span>  
  
 <span data-ttu-id="abcae-173">Um exemplo de um `TerminateSequence` mensagem.</span><span class="sxs-lookup"><span data-stu-id="abcae-173">An example of a `TerminateSequence` message.</span></span>  
  
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
  
### <a name="sequences"></a><span data-ttu-id="abcae-174">Sequências</span><span class="sxs-lookup"><span data-stu-id="abcae-174">Sequences</span></span>  
 <span data-ttu-id="abcae-175">A seguir está uma lista de restrições que se aplicam a sequências:</span><span class="sxs-lookup"><span data-stu-id="abcae-175">The following is a list of constraints that apply to sequences:</span></span>  
  
-   <span data-ttu-id="abcae-176">Gera B1401:WCF e maior do que de números de sequência de acessos `xs:long`do valor máximo inclusivo, 9223372036854775807.</span><span class="sxs-lookup"><span data-stu-id="abcae-176">B1401:WCF generates and accesses sequence numbers no higher than `xs:long`’s maximum inclusive value, 9223372036854775807.</span></span>  
  
 <span data-ttu-id="abcae-177">Um exemplo de um `Sequence` cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="abcae-177">An example of a `Sequence` header.</span></span>  
  
```xml  
<wsrm:Sequence s:mustUnderstand="1">  
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
  <wsrm:MessageNumber>1</wsrm:MessageNumber>  
</wsrm:Sequence>  
```  
  
### <a name="request-acknowledgement"></a><span data-ttu-id="abcae-178">Solicitação de confirmação</span><span class="sxs-lookup"><span data-stu-id="abcae-178">Request Acknowledgement</span></span>  
 <span data-ttu-id="abcae-179">O WCF usa o `AckRequested` cabeçalho como um mecanismo keep-alive.</span><span class="sxs-lookup"><span data-stu-id="abcae-179">WCF uses the `AckRequested` header as a keep-alive mechanism.</span></span>  
  
 <span data-ttu-id="abcae-180">Um exemplo de um `AckRequested` cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="abcae-180">An example of an `AckRequested` header.</span></span>  
  
```xml  
<wsrm:AckRequested>  
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
</wsrm:AckRequested>  
```  
  
### <a name="sequenceacknowledgement"></a><span data-ttu-id="abcae-181">SequenceAcknowledgement</span><span class="sxs-lookup"><span data-stu-id="abcae-181">SequenceAcknowledgement</span></span>  
 <span data-ttu-id="abcae-182">O WCF usa um mecanismo de "back transporte" para confirmações de sequência fornecidas no sistema de mensagens WS-Reliable.</span><span class="sxs-lookup"><span data-stu-id="abcae-182">WCF uses a "piggy-back" mechanism for sequence acknowledgements provided in WS-Reliable Messaging.</span></span> <span data-ttu-id="abcae-183">As seguintes restrições se aplicam:</span><span class="sxs-lookup"><span data-stu-id="abcae-183">The following constraints apply:</span></span>  
  
-   <span data-ttu-id="abcae-184">R1601: Quando duas sequências inverso são estabelecidas usando o `Offer` mecanismo, o `SequenceAcknowledgement` cabeçalho pode ser incluído em qualquer mensagem de aplicativo transmitida ao destinatário pretendido.</span><span class="sxs-lookup"><span data-stu-id="abcae-184">R1601: When two converse sequences are established using the `Offer` mechanism, the `SequenceAcknowledgement` header may be included in any application message transmitted to the intended recipient.</span></span> <span data-ttu-id="abcae-185">O ponto de extremidade remoto deve ser capaz de acessar um acumuladas `SequenceAcknowledgement` cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="abcae-185">The remote endpoint must be able to access a piggybacked `SequenceAcknowledgement` header.</span></span>  
  
-   <span data-ttu-id="abcae-186">B1602: O WCF não gera `SequenceAcknowledgement` que contêm cabeçalhos `Nack` elementos.</span><span class="sxs-lookup"><span data-stu-id="abcae-186">B1602: WCF does not generate `SequenceAcknowledgement` headers that contain `Nack` elements.</span></span> <span data-ttu-id="abcae-187">WCF valida que cada `Nack` elemento contém um número de sequência, mas caso contrário, ignora o `Nack` elemento e valor.</span><span class="sxs-lookup"><span data-stu-id="abcae-187">WCF validates that each `Nack` element contains a sequence number, but otherwise ignores the `Nack` element and value.</span></span>  
  
 <span data-ttu-id="abcae-188">Um exemplo de um `SequenceAcknowledgement` cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="abcae-188">An example of a `SequenceAcknowledgement` header.</span></span>  
  
```xml  
<wsrm:SequenceAcknowledgement>  
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
  <wsrm:AcknowledgementRange Lower="1" Upper="1"></wsrm:AcknowledgementRange>  
</wsrm:SequenceAcknowledgement>  
```  
  
### <a name="ws-reliablemessaging-faults"></a><span data-ttu-id="abcae-189">Falhas de WS-ReliableMessaging</span><span class="sxs-lookup"><span data-stu-id="abcae-189">WS-ReliableMessaging Faults</span></span>  
 <span data-ttu-id="abcae-190">O exemplo a seguir é uma lista de restrições que se aplicam a implementação do WCF de WS-ReliableMessaging falhas.</span><span class="sxs-lookup"><span data-stu-id="abcae-190">The following is a list of constraints that apply to the WCF implementation of WS-ReliableMessaging faults.</span></span> <span data-ttu-id="abcae-191">As seguintes restrições se aplicam:</span><span class="sxs-lookup"><span data-stu-id="abcae-191">The following constraints apply:</span></span>  
  
-   <span data-ttu-id="abcae-192">B1701: O WCF não gera `MessageNumberRollover` falhas.</span><span class="sxs-lookup"><span data-stu-id="abcae-192">B1701: WCF does not generate `MessageNumberRollover` faults.</span></span>  
  
-   <span data-ttu-id="abcae-193">B1702: Ao longo de SOAP 1.2, quando o ponto de extremidade do serviço atinge seu limite de conexão e não pode processar novas conexões, o WCF gera aninhado `CreateSequenceRefused` subcódigo, de falha `netrm:ConnectionLimitReached`, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="abcae-193">B1702: Over SOAP 1.2, when the service endpoint reaches its connection limit and cannot process new connections, WCF generates a nested `CreateSequenceRefused` fault subcode, `netrm:ConnectionLimitReached`, as shown in the following example.</span></span>  
  
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
  
### <a name="ws-addressing-faults"></a><span data-ttu-id="abcae-194">Falhas de WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="abcae-194">WS-Addressing Faults</span></span>  
 <span data-ttu-id="abcae-195">Como WS-ReliableMessaging usa WS-Addressing, a implementação de WCF WS-ReliableMessaging pode gerar e WS-Addressing falhas de transmissão.</span><span class="sxs-lookup"><span data-stu-id="abcae-195">Because WS-ReliableMessaging uses WS-Addressing, the WCF WS-ReliableMessaging implementation may generate and transmit WS-Addressing faults.</span></span> <span data-ttu-id="abcae-196">Esta seção aborda as falhas de WS-Addressing que o WCF gera e transmite na camada de WS-ReliableMessaging explicitamente:</span><span class="sxs-lookup"><span data-stu-id="abcae-196">This section covers the WS-Addressing faults that WCF explicitly generates and transmits at the WS-ReliableMessaging layer:</span></span>  
  
-   <span data-ttu-id="abcae-197">B1801:WCF gera e transmite o `Message Addressing Header Required` falha quando uma das seguintes opções for verdadeira:</span><span class="sxs-lookup"><span data-stu-id="abcae-197">B1801:WCF generates and transmits the `Message Addressing Header Required` fault when one of the following is true:</span></span>  
  
    -   <span data-ttu-id="abcae-198">Um `CreateSequence`, `CloseSequence` ou `TerminateSequence` mensagem está falta um `MessageId` cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="abcae-198">A `CreateSequence`, `CloseSequence` or `TerminateSequence` message is missing a `MessageId` header.</span></span>  
  
    -   <span data-ttu-id="abcae-199">Um `CreateSequence`, `CloseSequence` ou `TerminateSequence` mensagem está falta um `ReplyTo` cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="abcae-199">A `CreateSequence`, `CloseSequence` or `TerminateSequence` message is missing a `ReplyTo` header.</span></span>  
  
    -   <span data-ttu-id="abcae-200">Um `CreateSequenceResponse`, `CloseSequenceResponse`, ou `TerminateSequenceResponse` mensagem está falta um `RelatesTo` cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="abcae-200">A `CreateSequenceResponse`, `CloseSequenceResponse`, or `TerminateSequenceResponse` message is missing a `RelatesTo` header.</span></span>  
  
-   <span data-ttu-id="abcae-201">B1802:WCF gera e transmite a `Endpoint Unavailable` falha para indicar que não há nenhum ponto de extremidade que pode processar a sequência com base no exame dos cabeçalhos de endereçamento no `CreateSequence` mensagem.</span><span class="sxs-lookup"><span data-stu-id="abcae-201">B1802:WCF generates and transmits the `Endpoint Unavailable` fault to indicate there is no endpoint listening that can process the sequence based on examination of the addressing headers in the `CreateSequence` message.</span></span>  
  
## <a name="protocol-composition"></a><span data-ttu-id="abcae-202">Composição de protocolo</span><span class="sxs-lookup"><span data-stu-id="abcae-202">Protocol Composition</span></span>  
  
### <a name="composition-with-ws-addressing"></a><span data-ttu-id="abcae-203">Composição com o WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="abcae-203">Composition with WS-Addressing</span></span>  
 <span data-ttu-id="abcae-204">O WCF oferece suporte a duas versões do WS-Addressing: 2004 de WS-Addressing/08 [WS-ADDR] e W3C WS-Addressing 1.0 recomendações [WS-ADDR-CORE] e [WS-ADDR SOAP].</span><span class="sxs-lookup"><span data-stu-id="abcae-204">WCF supports two versions of WS-Addressing: WS-Addressing 2004/08 [WS-ADDR] and W3C WS-Addressing 1.0 Recommendations [WS-ADDR-CORE] and [WS-ADDR-SOAP].</span></span>  
  
 <span data-ttu-id="abcae-205">Enquanto as menções de especificação WS-ReliableMessaging 08/somente 2004 de WS-Addressing, ele não restringe a versão de WS-Addressing a ser usado.</span><span class="sxs-lookup"><span data-stu-id="abcae-205">While the WS-ReliableMessaging specification mentions only WS-Addressing 2004/08, it does not restrict the WS-Addressing version to be used.</span></span> <span data-ttu-id="abcae-206">A seguir está uma lista de restrições que se aplicam ao WCF:</span><span class="sxs-lookup"><span data-stu-id="abcae-206">The following is a list of constraints that apply to WCF:</span></span>  
  
-   <span data-ttu-id="abcae-207">R2101: 08/2004 de WS-Addressing e WS-Addressing 1.0 podem ser usado com o WS-Reliable Messaging.</span><span class="sxs-lookup"><span data-stu-id="abcae-207">R2101: Both WS-Addressing 2004/08 and WS-Addressing 1.0 can be used with WS-Reliable Messaging.</span></span>  
  
-   <span data-ttu-id="abcae-208">R2102: Uma única versão do WS-Addressing deve ser usada ao longo de uma determinada sequência WS-ReliableMessaging ou um par de sequências inverso correlacionados usando o `Offer` mecanismo.</span><span class="sxs-lookup"><span data-stu-id="abcae-208">R2102: A single version of WS-Addressing must be used throughout a given WS-ReliableMessaging sequence or a pair of converse sequences correlated by using the `Offer` mechanism.</span></span>  
  
### <a name="composition-with-soap"></a><span data-ttu-id="abcae-209">Composição com SOAP</span><span class="sxs-lookup"><span data-stu-id="abcae-209">Composition with SOAP</span></span>  
 <span data-ttu-id="abcae-210">O WCF oferece suporte ao uso de SOAP 1.1 e SOAP 1.2 com o WS-Reliable Messaging.</span><span class="sxs-lookup"><span data-stu-id="abcae-210">WCF supports the use of both SOAP 1.1 and SOAP 1.2 with WS-Reliable Messaging.</span></span>  
  
### <a name="composition-with-ws-security-and-ws-secureconversation"></a><span data-ttu-id="abcae-211">Composição com o WS-Security e WS-SecureConversation</span><span class="sxs-lookup"><span data-stu-id="abcae-211">Composition with WS-Security and WS-SecureConversation</span></span>  
 <span data-ttu-id="abcae-212">O WCF fornece proteção para WS-ReliableMessaging sequências com o uso seguro de transporte (HTTPS), composição com o WS-Security e composição com o WS-Secure Conversation.</span><span class="sxs-lookup"><span data-stu-id="abcae-212">WCF provides protection for WS-ReliableMessaging sequences by using secure Transport (HTTPS), composition with WS-Security, and composition with WS-Secure Conversation.</span></span> <span data-ttu-id="abcae-213">O protocolo WS-ReliableMessaging 1.1, WS-Security 1.1 e o protocolo WS-Secure Conversation 1.3 devem ser usados juntos.</span><span class="sxs-lookup"><span data-stu-id="abcae-213">The WS-ReliableMessaging 1.1 protocol, WS-Security 1.1 and WS-Secure Conversation 1.3 protocol should be used together.</span></span> <span data-ttu-id="abcae-214">A seguir está uma lista de restrições que se aplicam ao WCF:</span><span class="sxs-lookup"><span data-stu-id="abcae-214">The following is a list of constraints that apply to WCF:</span></span>  
  
-   <span data-ttu-id="abcae-215">R2301: Para proteger a integridade de uma sequência de WS-ReliableMessaging, além da integridade e a confidencialidade das mensagens individuais, o WCF exige que o WS-Secure Conversation deve ser usada.</span><span class="sxs-lookup"><span data-stu-id="abcae-215">R2301: To protect the integrity of a WS-ReliableMessaging sequence in addition to the integrity and confidentiality of individual messages, WCF requires that WS-Secure Conversation must be used.</span></span>  
  
-   <span data-ttu-id="abcae-216">R2302:AWS-Secure Conversation deve ser estabelecida antes de estabelecer a sequência de WS-ReliableMessaging.</span><span class="sxs-lookup"><span data-stu-id="abcae-216">R2302:AWS-Secure Conversation session must be established prior to establishing WS-ReliableMessaging sequence(s).</span></span>  
  
-   <span data-ttu-id="abcae-217">R2303: Se o tempo de vida de sequência WS-ReliableMessaging exceder o WS-Secure Conversation tempo de vida da sessão, o `SecurityContextToken` estabelecida usando WS-Secure Conversation devem ser renovada por meio de associação de WS-Secure Conversation renovação correspondente.</span><span class="sxs-lookup"><span data-stu-id="abcae-217">R2303: If the WS-ReliableMessaging sequence lifetime exceeds the WS-Secure Conversation session’s lifetime, the `SecurityContextToken` established by using WS-Secure Conversation must be renewed by using the corresponding WS-Secure Conversation Renewal binding.</span></span>  
  
-   <span data-ttu-id="abcae-218">B2304:WS-ReliableMessaging sequência ou um par de sequências inverso correlacionados sempre são associados a uma única sessão do WS-SecureConversation.</span><span class="sxs-lookup"><span data-stu-id="abcae-218">B2304:WS-ReliableMessaging sequence or a pair of correlated converse sequences are always bound to a single WS-SecureConversation session.</span></span>  
  
-   <span data-ttu-id="abcae-219">R2305: Quando composto com o WS-Secure Conversation, o Respondente WCF requer que o `CreateSequence` a mensagem contém o `wsse:SecurityTokenReference` elemento e o `wsrm:UsesSequenceSTR` cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="abcae-219">R2305: When composed with WS-Secure Conversation, the WCF responder requires that the `CreateSequence` message contain the `wsse:SecurityTokenReference` element and the `wsrm:UsesSequenceSTR` header.</span></span>  
  
 <span data-ttu-id="abcae-220">Um exemplo de um `UsesSequenceSTR` cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="abcae-220">An example of a `UsesSequenceSTR` header.</span></span>  
  
```xml  
<wsrm:UsesSequenceSTR></wsrm:UsesSequenceSTR>  
```  
  
### <a name="composition-with-ssltls-sessions"></a><span data-ttu-id="abcae-221">Composição com sessões SSL/TLS</span><span class="sxs-lookup"><span data-stu-id="abcae-221">Composition with SSL/TLS sessions</span></span>  
 <span data-ttu-id="abcae-222">O WCF não oferece suporte a composição com sessões SSL/TLS:</span><span class="sxs-lookup"><span data-stu-id="abcae-222">WCF does not support composition with SSL/TLS sessions:</span></span>  
  
-   <span data-ttu-id="abcae-223">B2401: O WCF não gera o `wsrm:UsesSequenceSSL` cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="abcae-223">B2401: WCF does not generate the `wsrm:UsesSequenceSSL` header.</span></span>  
  
-   <span data-ttu-id="abcae-224">R2402: Um iniciador de mensagens confiável não deve enviar uma `CreateSequence` da mensagem com um `wsrm:UsesSequenceSSL` cabeçalho para um respondente do WCF.</span><span class="sxs-lookup"><span data-stu-id="abcae-224">R2402: A Reliable Messaging Initiator must not send a `CreateSequence` message with a `wsrm:UsesSequenceSSL` header to a WCF Responder.</span></span>  
  
### <a name="composition-with-ws-policy"></a><span data-ttu-id="abcae-225">Composição com o WS-Policy</span><span class="sxs-lookup"><span data-stu-id="abcae-225">Composition with WS-Policy</span></span>  
 <span data-ttu-id="abcae-226">O WCF oferece suporte a duas versões do WS-Policy: 1.2 do WS-Policy e WS-Policy 1.5.</span><span class="sxs-lookup"><span data-stu-id="abcae-226">WCF supports two versions of WS-Policy: WS-Policy 1.2 and WS-Policy 1.5.</span></span>  
  
## <a name="ws-reliablemessaging-ws-policy-assertion"></a><span data-ttu-id="abcae-227">WS-ReliableMessaging WS-Policy Assertion</span><span class="sxs-lookup"><span data-stu-id="abcae-227">WS-ReliableMessaging WS-Policy Assertion</span></span>  
 <span data-ttu-id="abcae-228">O WCF usa a asserção de WS-Policy WS-ReliableMessaging `wsrm:RMAssertion` para descrever os recursos de pontos de extremidade.</span><span class="sxs-lookup"><span data-stu-id="abcae-228">WCF uses WS-ReliableMessaging WS-Policy Assertion `wsrm:RMAssertion` to describe endpoints capabilities.</span></span> <span data-ttu-id="abcae-229">A seguir está uma lista de restrições que se aplicam ao WCF:</span><span class="sxs-lookup"><span data-stu-id="abcae-229">The following is a list of constraints that apply to WCF:</span></span>  
  
-   <span data-ttu-id="abcae-230">B3001: O WCF anexa `wsrmn:RMAssertion` declaração de política WS para `wsdl:binding` elementos.</span><span class="sxs-lookup"><span data-stu-id="abcae-230">B3001: WCF attaches `wsrmn:RMAssertion` WS-Policy Assertion to `wsdl:binding` elements.</span></span> <span data-ttu-id="abcae-231">O WCF oferece suporte a ambos os anexos `wsdl:binding` e `wsdl:port` elementos.</span><span class="sxs-lookup"><span data-stu-id="abcae-231">WCF supports both attachments to `wsdl:binding` and `wsdl:port` elements.</span></span>  
  
-   <span data-ttu-id="abcae-232">B3002: O WCF nunca gera o `wsp:Optional` marca.</span><span class="sxs-lookup"><span data-stu-id="abcae-232">B3002: WCF never generates the `wsp:Optional` tag.</span></span>  
  
-   <span data-ttu-id="abcae-233">B3003: Ao acessar o `wsrmp:RMAssertion` WCF de asserção de WS-Policy, ignora o `wsp:Optional` de marca e trata a política WS-RM como obrigatórias.</span><span class="sxs-lookup"><span data-stu-id="abcae-233">B3003: When accessing the `wsrmp:RMAssertion` WS-Policy Assertion, WCF ignores the `wsp:Optional` tag and treats the WS-RM policy as mandatory.</span></span>  
  
-   <span data-ttu-id="abcae-234">R3004: Porque o WCF não compõe com sessões SSL/TLS, o WCF não aceita a política que especifica `wsrmp:SequenceTransportSecurity`.</span><span class="sxs-lookup"><span data-stu-id="abcae-234">R3004: Because WCF does not compose with SSL/TLS sessions, WCF does not accept policy that specifies `wsrmp:SequenceTransportSecurity`.</span></span>  
  
-   <span data-ttu-id="abcae-235">B3005: O WCF sempre gera o `wsrmp:DeliveryAssurance` elemento.</span><span class="sxs-lookup"><span data-stu-id="abcae-235">B3005: WCF always generates the `wsrmp:DeliveryAssurance` element.</span></span>  
  
-   <span data-ttu-id="abcae-236">B3006: O WCF sempre Especifica o `wsrmp:ExactlyOnce` garantia de entrega.</span><span class="sxs-lookup"><span data-stu-id="abcae-236">B3006: WCF always specifies the `wsrmp:ExactlyOnce` delivery assurance.</span></span>  
  
-   <span data-ttu-id="abcae-237">B3007: WCF gera e lê as propriedades a seguir da asserção WS-ReliableMessaging e fornece controle sobre eles em WCF`ReliableSessionBindingElement`:</span><span class="sxs-lookup"><span data-stu-id="abcae-237">B3007: WCF generates and reads the following properties of the WS-ReliableMessaging assertion and provides control over them on the WCF`ReliableSessionBindingElement`:</span></span>  
  
    -   `netrmp:InactivityTimeout`  
  
    -   `netrmp:AcknowledgementInterval`  
  
     <span data-ttu-id="abcae-238">Um exemplo de um `RMAssertion`.</span><span class="sxs-lookup"><span data-stu-id="abcae-238">An example of a `RMAssertion`.</span></span>  
  
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
  
## <a name="flow-control-ws-reliablemessaging-extension"></a><span data-ttu-id="abcae-239">Extensão de WS-ReliableMessaging do fluxo de controle</span><span class="sxs-lookup"><span data-stu-id="abcae-239">Flow Control WS-ReliableMessaging Extension</span></span>  
 <span data-ttu-id="abcae-240">O WCF usa WS-ReliableMessaging extensibilidade para proporcionar um controle adicional opcional sobre o fluxo de mensagem de sequência.</span><span class="sxs-lookup"><span data-stu-id="abcae-240">WCF uses WS-ReliableMessaging extensibility to provide optional additional tighter control over sequence message flow.</span></span>  
  
 <span data-ttu-id="abcae-241">Controle de fluxo é habilitado definindo o <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.FlowControlEnabled?displayProperty=nameWithType> propriedade para `true`.</span><span class="sxs-lookup"><span data-stu-id="abcae-241">Flow control is enabled by setting the <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.FlowControlEnabled?displayProperty=nameWithType> property to `true`.</span></span> <span data-ttu-id="abcae-242">A seguir está uma lista de restrições que se aplicam ao WCF:</span><span class="sxs-lookup"><span data-stu-id="abcae-242">The following is a list of constraints that apply to WCF:</span></span>  
  
-   <span data-ttu-id="abcae-243">B4001: Quando confiável fluxo de controle de mensagens está habilitado, o WCF gera uma `netrm:BufferRemaining` elemento de extensibilidade do elemento a `SequenceAcknowledgement` cabeçalho, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="abcae-243">B4001: When Reliable Messaging Flow Control is enabled, WCF generates a `netrm:BufferRemaining` element in the element extensibility of the `SequenceAcknowledgement` header, as shown in the following example.</span></span>  
  
    ```xml  
    <wsrm:SequenceAcknowledgement>  
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
      <wsrm:AcknowledgementRange Upper="1" Lower="1"/>             
      <netrm:BufferRemaining>8</netrm:BufferRemaining>  
    </wsrm:SequenceAcknowledgement>  
    ```  
  
-   <span data-ttu-id="abcae-244">B4002: Mesmo quando o sistema de mensagens confiável fluxo de controle é habilitado, o WCF não exige uma `netrm:BufferRemaining` elemento no `SequenceAcknowledgement` cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="abcae-244">B4002: Even when Reliable Messaging Flow Control is enabled, WCF does not require a `netrm:BufferRemaining` element in the `SequenceAcknowledgement` header.</span></span>  
  
-   <span data-ttu-id="abcae-245">B4003: Destino de sistema de mensagens confiável WCF usa `netrm:BufferRemaining` indicar quantas novas mensagens ele pode armazenar em buffer.</span><span class="sxs-lookup"><span data-stu-id="abcae-245">B4003: WCF Reliable Messaging Destination uses `netrm:BufferRemaining` to indicate how many new messages it can buffer.</span></span>  
  
-   <span data-ttu-id="abcae-246">B4004:when Reliable Messaging fluxo de controle está habilitado, a fonte de sistema de mensagens confiável WCF usa o valor de `netrm:BufferRemaining` para transmissão de mensagens de limitação.</span><span class="sxs-lookup"><span data-stu-id="abcae-246">B4004:When Reliable Messaging Flow Control is enabled, the WCF Reliable Messaging Source uses the value of `netrm:BufferRemaining` to throttle message transmission.</span></span>  
  
-   <span data-ttu-id="abcae-247">B4005: O WCF gera `netrm:BufferRemaining` inteiro de valores entre 0 e 4096 inclusivo e lê os valores de número inteiro entre 0 e `xs:int`do `maxInclusive` 214748364 inclusivo de valor.</span><span class="sxs-lookup"><span data-stu-id="abcae-247">B4005: WCF generates `netrm:BufferRemaining` integer values between 0 and 4096 inclusive, and reads integer values between 0 and `xs:int`’s `maxInclusive` value 214748364 inclusive.</span></span>  
  
## <a name="message-exchange-patterns"></a><span data-ttu-id="abcae-248">Padrões de troca de mensagem</span><span class="sxs-lookup"><span data-stu-id="abcae-248">Message Exchange Patterns</span></span>  
 <span data-ttu-id="abcae-249">Esta seção descreve o comportamento do WCF quando WS-ReliableMessaging é usado para diferentes padrões de troca de mensagem.</span><span class="sxs-lookup"><span data-stu-id="abcae-249">This section describes WCF's behavior when WS-ReliableMessaging is used for different Message Exchange Patterns.</span></span> <span data-ttu-id="abcae-250">Para cada padrão de troca de mensagem, os seguintes cenários de duas implantações são considerados:</span><span class="sxs-lookup"><span data-stu-id="abcae-250">For each Message Exchange Pattern the following two deployments scenarios are considered:</span></span>  
  
-   <span data-ttu-id="abcae-251">Não endereçável iniciador: Iniciador estiver atrás de um firewall. Respondente pode enviar mensagens para o iniciador apenas em respostas HTTP.</span><span class="sxs-lookup"><span data-stu-id="abcae-251">Non-Addressable Initiator: Initiator is behind a firewall; Responder can deliver messages to the Initiator only on HTTP responses.</span></span>  
  
-   <span data-ttu-id="abcae-252">Iniciador endereçável: Iniciador e Respondente podem receber solicitações HTTP; em outras palavras, as duas conexões de HTTP inverso podem ser estabelecidas.</span><span class="sxs-lookup"><span data-stu-id="abcae-252">Addressable Initiator: Initiator and Responder both can be sent HTTP requests; in other words, two converse HTTP connections can be established.</span></span>  
  
### <a name="one-way-non-addressable-initiator"></a><span data-ttu-id="abcae-253">Iniciador unidirecional, não endereçável</span><span class="sxs-lookup"><span data-stu-id="abcae-253">One-way, Non-addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="abcae-254">Associação</span><span class="sxs-lookup"><span data-stu-id="abcae-254">Binding</span></span>  
 <span data-ttu-id="abcae-255">O WCF fornece um padrão de troca de mensagens unidirecional usando uma sequência em um canal HTTP.</span><span class="sxs-lookup"><span data-stu-id="abcae-255">WCF provides a one-way message exchange pattern using one sequence over one HTTP channel.</span></span> <span data-ttu-id="abcae-256">O WCF usa solicitações HTTP para transmitir todas as mensagens do iniciador para as respostas HTTP e o respondente para transmitir todas as mensagens do respondedor para o iniciador.</span><span class="sxs-lookup"><span data-stu-id="abcae-256">WCF uses HTTP requests to transmit all messages from the Initiator to the Responder and HTTP responses to transmit all messages from the Responder to the Initiator.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="abcae-257">Exchange CreateSequence</span><span class="sxs-lookup"><span data-stu-id="abcae-257">CreateSequence Exchange</span></span>  
 <span data-ttu-id="abcae-258">O iniciador do WCF transmite uma `CreateSequence` mensagem sem nenhum `Offer` elemento em uma solicitação HTTP e espera que o `CreateSequenceResponse` mensagem de resposta HTTP.</span><span class="sxs-lookup"><span data-stu-id="abcae-258">The WCF Initiator transmits a `CreateSequence` message with no `Offer` element on an HTTP request and expects the `CreateSequenceResponse` message on the HTTP response.</span></span> <span data-ttu-id="abcae-259">O Respondente WCF cria uma sequência e transmite a `CreateSequenceResponse` mensagem sem nenhum `Accept` elemento na resposta HTTP.</span><span class="sxs-lookup"><span data-stu-id="abcae-259">The WCF Responder creates a sequence and transmits the `CreateSequenceResponse` message with no `Accept` element on the HTTP response.</span></span>  
  
#### <a name="sequenceacknowledgement"></a><span data-ttu-id="abcae-260">SequenceAcknowledgement</span><span class="sxs-lookup"><span data-stu-id="abcae-260">SequenceAcknowledgement</span></span>  
 <span data-ttu-id="abcae-261">O iniciador do WCF processa as confirmações na resposta de todas as mensagens, exceto o `CreateSequence` mensagem e mensagens de falha.</span><span class="sxs-lookup"><span data-stu-id="abcae-261">The WCF Initiator processes acknowledgements on the reply of all messages except the `CreateSequence` message and fault messages.</span></span> <span data-ttu-id="abcae-262">O Respondente WCF sempre transmite uma confirmação autônoma na resposta HTTP a sequência de todas as e `AckRequested` mensagens.</span><span class="sxs-lookup"><span data-stu-id="abcae-262">The WCF Responder always transmits a stand-alone acknowledgement on the HTTP response to all sequence and `AckRequested` messages.</span></span>  
  
#### <a name="closesequence-exchange"></a><span data-ttu-id="abcae-263">Exchange CreateSequence</span><span class="sxs-lookup"><span data-stu-id="abcae-263">CloseSequence Exchange</span></span>  
 <span data-ttu-id="abcae-264">O iniciador do WCF transmite uma `CloseSequence` da mensagem em uma solicitação HTTP e espera que o `CreateSequenceResponse` mensagem de resposta HTTP.</span><span class="sxs-lookup"><span data-stu-id="abcae-264">The WCF Initiator transmits a `CloseSequence` message on an HTTP request and expects the `CreateSequenceResponse` message on the HTTP response.</span></span> <span data-ttu-id="abcae-265">O Respondente WCF transmite o `CloseSequenceResponse` mensagem de resposta HTTP.</span><span class="sxs-lookup"><span data-stu-id="abcae-265">The WCF Responder transmits the `CloseSequenceResponse` message on the HTTP response.</span></span>  
  
#### <a name="terminatesequence-exchange"></a><span data-ttu-id="abcae-266">Exchange TerminateSequence</span><span class="sxs-lookup"><span data-stu-id="abcae-266">TerminateSequence Exchange</span></span>  
 <span data-ttu-id="abcae-267">O iniciador do WCF transmite uma `TerminateSequence` da mensagem em uma solicitação HTTP e espera que o `TerminateSequenceResponse` mensagem de resposta HTTP.</span><span class="sxs-lookup"><span data-stu-id="abcae-267">The WCF Initiator transmits a `TerminateSequence` message on an HTTP request and expects the `TerminateSequenceResponse` message on the HTTP response.</span></span> <span data-ttu-id="abcae-268">O Respondente WCF transmite o `TerminateSequenceResponse` mensagem de resposta HTTP.</span><span class="sxs-lookup"><span data-stu-id="abcae-268">The WCF Responder transmits the `TerminateSequenceResponse` message on the HTTP response.</span></span>  
  
### <a name="one-way-addressable-initiator"></a><span data-ttu-id="abcae-269">Iniciador de uma forma, endereçável</span><span class="sxs-lookup"><span data-stu-id="abcae-269">One Way, Addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="abcae-270">Associação</span><span class="sxs-lookup"><span data-stu-id="abcae-270">Binding</span></span>  
 <span data-ttu-id="abcae-271">O WCF fornece um padrão de troca de mensagens unidirecional usando uma sequência sobre uma entrada e um canal HTTP de saída.</span><span class="sxs-lookup"><span data-stu-id="abcae-271">WCF provides a one-way message exchange pattern using one sequence over one inbound and one outbound HTTP channel.</span></span> <span data-ttu-id="abcae-272">O WCF usa as solicitações HTTP para transmitir todas as mensagens.</span><span class="sxs-lookup"><span data-stu-id="abcae-272">WCF uses the HTTP requests to transmit all messages.</span></span> <span data-ttu-id="abcae-273">Todas as respostas HTTP tem um corpo vazio e o código de status HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="abcae-273">All HTTP responses have an empty body and HTTP 202 status code.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="abcae-274">Exchange CreateSequence</span><span class="sxs-lookup"><span data-stu-id="abcae-274">CreateSequence Exchange</span></span>  
 <span data-ttu-id="abcae-275">O iniciador do WCF transmite uma `CreateSequence` mensagem sem nenhum `Offer` elemento em uma solicitação HTTP.</span><span class="sxs-lookup"><span data-stu-id="abcae-275">The WCF Initiator transmits a `CreateSequence` message with no `Offer` element on an HTTP request.</span></span> <span data-ttu-id="abcae-276">O Respondente WCF cria uma sequência e transmite a `CreateSequenceResponse` mensagem sem nenhum `Accept` elemento em uma solicitação HTTP.</span><span class="sxs-lookup"><span data-stu-id="abcae-276">The WCF Responder creates a sequence and transmits the `CreateSequenceResponse` message with no `Accept` element on an HTTP request.</span></span>  
  
### <a name="duplex-addressable-initiator"></a><span data-ttu-id="abcae-277">Iniciador de duplex e endereçável</span><span class="sxs-lookup"><span data-stu-id="abcae-277">Duplex, Addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="abcae-278">Associação</span><span class="sxs-lookup"><span data-stu-id="abcae-278">Binding</span></span>  
 <span data-ttu-id="abcae-279">O WCF fornece um padrão de troca de mensagem assíncrona totalmente bidirecional usando duas sequências sobre uma entrada e um canal HTTP de saída.</span><span class="sxs-lookup"><span data-stu-id="abcae-279">WCF provides a fully-asynchronous, two-way message exchange pattern using two sequences over one inbound and one outbound HTTP channel.</span></span> <span data-ttu-id="abcae-280">Esse padrão de troca de mensagem pode ser combinado com o `Request/Reply`, `Addressable` padrão de troca de mensagem do iniciador de uma maneira limitada.</span><span class="sxs-lookup"><span data-stu-id="abcae-280">This message exchange pattern can be mixed with the `Request/Reply`, `Addressable` Initiator message exchange pattern in a limited way.</span></span> <span data-ttu-id="abcae-281">O WCF usa solicitações HTTP para transmitir todas as mensagens.</span><span class="sxs-lookup"><span data-stu-id="abcae-281">WCF uses HTTP requests to transmit all messages.</span></span> <span data-ttu-id="abcae-282">Todas as respostas HTTP tem um corpo vazio e o código de status HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="abcae-282">All HTTP responses have an empty body and HTTP 202 status code.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="abcae-283">Exchange CreateSequence</span><span class="sxs-lookup"><span data-stu-id="abcae-283">CreateSequence Exchange</span></span>  
 <span data-ttu-id="abcae-284">O iniciador do WCF transmite uma `CreateSequence` da mensagem com um `Offer` elemento em uma solicitação HTTP.</span><span class="sxs-lookup"><span data-stu-id="abcae-284">The WCF Initiator transmits a `CreateSequence` message with an `Offer` element on an HTTP request.</span></span> <span data-ttu-id="abcae-285">O Respondente WCF garante que o `CreateSequence` tem um `Offer` elemento, em seguida, cria uma sequência e transmite a `CreateSequenceResponse` da mensagem com um `Accept` elemento.</span><span class="sxs-lookup"><span data-stu-id="abcae-285">The WCF Responder ensures that the `CreateSequence` has an `Offer` element, then creates a sequence and transmits the `CreateSequenceResponse` message with an `Accept` element.</span></span>  
  
#### <a name="sequence-lifetime"></a><span data-ttu-id="abcae-286">Tempo de vida de sequência</span><span class="sxs-lookup"><span data-stu-id="abcae-286">Sequence Lifetime</span></span>  
 <span data-ttu-id="abcae-287">O WCF trata duas sequências como uma sessão duplex totalmente.</span><span class="sxs-lookup"><span data-stu-id="abcae-287">WCF treats the two sequences as one fully-duplex session.</span></span>  
  
 <span data-ttu-id="abcae-288">Ao gerar uma falha que uma sequência de falhas, o WCF espera que o ponto de extremidade remoto para ambas as sequências de falha.</span><span class="sxs-lookup"><span data-stu-id="abcae-288">Upon generating a fault that faults one sequence, WCF expects the remote endpoint to fault both sequences.</span></span> <span data-ttu-id="abcae-289">Após a leitura de uma falha que uma sequência de falhas, WCF falha em ambas as sequências.</span><span class="sxs-lookup"><span data-stu-id="abcae-289">Upon reading a fault that faults one sequence, WCF faults both sequences.</span></span>  
  
 <span data-ttu-id="abcae-290">O WCF pode fechar sua sequência de saída e continuar a processar mensagens em sua sequência de entrada.</span><span class="sxs-lookup"><span data-stu-id="abcae-290">WCF can close its outbound sequence and continue to process messages on its inbound sequence.</span></span> <span data-ttu-id="abcae-291">Por outro lado, o WCF pode processar o fechamento da sequência de entrada e continuar a enviar mensagens em sua sequência de saída.</span><span class="sxs-lookup"><span data-stu-id="abcae-291">Conversely, WCF can process the close of the inbound sequence and continue to send messages on its outbound sequence.</span></span>  
  
### <a name="request-reply-and-one-way-non-addressable-initiator"></a><span data-ttu-id="abcae-292">Iniciador de unidirecional, não endereçável e solicitação-resposta</span><span class="sxs-lookup"><span data-stu-id="abcae-292">Request-Reply and One-Way, Non-Addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="abcae-293">Associação</span><span class="sxs-lookup"><span data-stu-id="abcae-293">Binding</span></span>  
 <span data-ttu-id="abcae-294">O WCF oferece um unidirecional e padrão de troca de mensagem de solicitação-resposta usando duas sequências em um canal HTTP.</span><span class="sxs-lookup"><span data-stu-id="abcae-294">WCF provides a one-way and request-reply message exchange pattern using two sequences over one HTTP channel.</span></span> <span data-ttu-id="abcae-295">O WCF usa solicitações HTTP para transmitir todas as mensagens do iniciador para as respostas HTTP e o respondente para transmitir todas as mensagens do respondedor para o iniciador.</span><span class="sxs-lookup"><span data-stu-id="abcae-295">WCF uses HTTP requests to transmit all messages from the Initiator to the Responder and HTTP responses to transmit all messages from the Responder to the Initiator.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="abcae-296">Exchange CreateSequence</span><span class="sxs-lookup"><span data-stu-id="abcae-296">CreateSequence Exchange</span></span>  
 <span data-ttu-id="abcae-297">Transmite o iniciador do WCF uma `CreateSequence` da mensagem com um `Offer` elemento em uma solicitação HTTP e espera que o `CreateSequenceResponse` mensagem de resposta HTTP.</span><span class="sxs-lookup"><span data-stu-id="abcae-297">The WCF Initiator transmits a `CreateSequence` message with an `Offer` element on an HTTP request and expects the `CreateSequenceResponse` message on the HTTP response.</span></span> <span data-ttu-id="abcae-298">O Respondente WCF cria uma sequência e transmite a `CreateSequenceResponse` da mensagem com um `Accept` elemento na resposta HTTP.</span><span class="sxs-lookup"><span data-stu-id="abcae-298">The WCF Responder creates a sequence and transmits the `CreateSequenceResponse` message with an `Accept` element on the HTTP response.</span></span>  
  
#### <a name="one-way-message"></a><span data-ttu-id="abcae-299">Mensagem unidirecional</span><span class="sxs-lookup"><span data-stu-id="abcae-299">One-way Message</span></span>  
 <span data-ttu-id="abcae-300">Para concluir com êxito uma troca de mensagens unidirecional, o iniciador de WCF transmite uma mensagem de sequência de solicitação na solicitação HTTP e recebe um autônomo `SequenceAcknowledgement` mensagem de resposta HTTP.</span><span class="sxs-lookup"><span data-stu-id="abcae-300">To complete a one-way message exchange successfully, the WCF Initiator transmits a request sequence message on the HTTP request and receives a standalone `SequenceAcknowledgement` message on the HTTP response.</span></span> <span data-ttu-id="abcae-301">O `SequenceAcknowledgement` devem reconhecer a mensagem transmitida.</span><span class="sxs-lookup"><span data-stu-id="abcae-301">The `SequenceAcknowledgement` must acknowledge the message transmitted.</span></span>  
  
 <span data-ttu-id="abcae-302">O Respondente de WCF pode responder à solicitação com uma confirmação, uma falha ou uma resposta com um corpo vazio e o código de status HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="abcae-302">The WCF Responder may reply to the request with an acknowledgement, a fault, or a response with an empty body and HTTP 202 status code.</span></span>  
  
#### <a name="two-way-messages"></a><span data-ttu-id="abcae-303">Duas mensagens de forma</span><span class="sxs-lookup"><span data-stu-id="abcae-303">Two Way Messages</span></span>  
 <span data-ttu-id="abcae-304">Para concluir um protocolo de troca de mensagem de duas vias com êxito, o iniciador de WCF transmite uma mensagem de sequência de solicitação na solicitação HTTP e recebe uma mensagem de resposta de sequência na resposta HTTP.</span><span class="sxs-lookup"><span data-stu-id="abcae-304">To complete a two way message exchange protocol successfully, the WCF Initiator transmits a request sequence message on the HTTP request and receives a reply sequence message on the HTTP response.</span></span> <span data-ttu-id="abcae-305">A resposta deve conter um `SequenceAcknowledgement` confirmando a mensagem de sequência de solicitação transmitida.</span><span class="sxs-lookup"><span data-stu-id="abcae-305">The response must carry a `SequenceAcknowledgement` acknowledging the request sequence message transmitted.</span></span>  
  
 <span data-ttu-id="abcae-306">O Respondente de WCF pode responder à solicitação com uma resposta do aplicativo, uma falha ou uma resposta com um corpo vazio e o código de status HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="abcae-306">The WCF Responder may reply to the request with an application reply, a fault or a response with an empty body and HTTP 202 status code.</span></span>  
  
 <span data-ttu-id="abcae-307">Devido à presença de mensagens unidirecional e o tempo de respostas do aplicativo, o número de sequência da mensagem de sequência de solicitação e o número de sequência da mensagem de resposta não têm nenhuma correlação.</span><span class="sxs-lookup"><span data-stu-id="abcae-307">Because of the presence of one-way messages and the timing of application replies, the request sequence message’s sequence number and the response message’s sequence number have no correlation.</span></span>  
  
#### <a name="retrying-replies"></a><span data-ttu-id="abcae-308">Repetir respostas</span><span class="sxs-lookup"><span data-stu-id="abcae-308">Retrying Replies</span></span>  
 <span data-ttu-id="abcae-309">O WCF conta com correlação de solicitação-resposta HTTP para correlação de protocolo de troca de mensagens bidirecional.</span><span class="sxs-lookup"><span data-stu-id="abcae-309">WCF relies on HTTP request-reply correlation for two-way message exchange protocol correlation.</span></span> <span data-ttu-id="abcae-310">Por causa disso, o iniciador do WCF não para tentar novamente uma mensagem de sequência de solicitação quando a mensagem de sequência de solicitação é confirmada, mas em vez disso, quando a resposta HTTP transporta um `SequenceAcknowledgement`, resposta do aplicativo ou falhas.</span><span class="sxs-lookup"><span data-stu-id="abcae-310">Because of this, the WCF Initiator does not stop retrying a request sequence message when the request sequence message is acknowledged but rather when the HTTP response carries a `SequenceAcknowledgement`, application reply, or fault.</span></span> <span data-ttu-id="abcae-311">O Respondente WCF repetições de respostas na resposta HTTP da solicitação à qual a resposta está correlacionada.</span><span class="sxs-lookup"><span data-stu-id="abcae-311">The WCF Responder retries replies on the HTTP response of the request to which the reply is correlated.</span></span>  
  
#### <a name="closesequence-exchange"></a><span data-ttu-id="abcae-312">Exchange CreateSequence</span><span class="sxs-lookup"><span data-stu-id="abcae-312">CloseSequence Exchange</span></span>  
 <span data-ttu-id="abcae-313">Depois de receber todas as mensagens de resposta de sequência e as confirmações para todas as mensagens de sequência de solicitação unidirecional, o iniciador do WCF transmite uma `CloseSequence` da mensagem para a sequência de solicitação em uma solicitação HTTP e espera que o `CloseSequenceResponse` na resposta HTTP.</span><span class="sxs-lookup"><span data-stu-id="abcae-313">After receiving all reply sequence messages and acknowledgements for all one way request sequence messages, the WCF Initiator transmits a `CloseSequence` message for the request sequence on an HTTP request and expects the `CloseSequenceResponse` on the HTTP response.</span></span>  
  
 <span data-ttu-id="abcae-314">A sequência de solicitação de fechamento implicitamente fecha a sequência de resposta.</span><span class="sxs-lookup"><span data-stu-id="abcae-314">Closing the request sequence implicitly closes the reply sequence.</span></span> <span data-ttu-id="abcae-315">Isso significa que o iniciador do WCF inclui o Final da sequência de resposta `SequenceAcknowledgement` sobre o `CloseSequence` mensagem e a sequência de resposta não tem um `CloseSequence` exchange.</span><span class="sxs-lookup"><span data-stu-id="abcae-315">This means the WCF Initiator includes the reply sequence’s Final `SequenceAcknowledgement` on the `CloseSequence` message and the reply sequence does not have a `CloseSequence` exchange.</span></span>  
  
 <span data-ttu-id="abcae-316">O Respondente WCF garante que todas as respostas são confirmadas e transmite o `CloseSequenceResponse` mensagem de resposta HTTP.</span><span class="sxs-lookup"><span data-stu-id="abcae-316">The WCF Responder ensures all replies are acknowledged and transmits the `CloseSequenceResponse` message on the HTTP response.</span></span>  
  
#### <a name="terminatesequence-exchange"></a><span data-ttu-id="abcae-317">Exchange TerminateSequence</span><span class="sxs-lookup"><span data-stu-id="abcae-317">TerminateSequence Exchange</span></span>  
 <span data-ttu-id="abcae-318">Após o recebimento de `CloseSequenceResponse` o iniciador do WCF de mensagem, transmite um `TerminateSequence` da mensagem para a sequência de solicitação em uma solicitação HTTP e espera que o `TerminateSequenceResponse` na resposta HTTP.</span><span class="sxs-lookup"><span data-stu-id="abcae-318">After receiving the `CloseSequenceResponse` message, the WCF Initiator transmits a `TerminateSequence` message for the request sequence on an HTTP request and expects the `TerminateSequenceResponse` on the HTTP response.</span></span>  
  
 <span data-ttu-id="abcae-319">Como o `CloseSequence` exchange, encerrando a sequência de solicitação implicitamente encerra a sequência de resposta.</span><span class="sxs-lookup"><span data-stu-id="abcae-319">Like the `CloseSequence` exchange, terminating the request sequence implicitly terminates the reply sequence.</span></span> <span data-ttu-id="abcae-320">Isso significa que o iniciador do WCF inclui o final da sequência de resposta `SequenceAcknowledgement` sobre o `TerminateSequence` mensagem e a sequência de resposta não tem um `TerminateSequence` exchange.</span><span class="sxs-lookup"><span data-stu-id="abcae-320">This means the WCF Initiator includes the reply sequence’s final `SequenceAcknowledgement` on the `TerminateSequence` message and the reply sequence does not have a `TerminateSequence` exchange.</span></span>  
  
 <span data-ttu-id="abcae-321">O Respondente WCF transmite o `TerminateSequenceResponse` mensagem de resposta HTTP.</span><span class="sxs-lookup"><span data-stu-id="abcae-321">The WCF Responder transmits the `TerminateSequenceResponse` message on the HTTP response.</span></span>  
  
### <a name="requestreply-addressable-initiator"></a><span data-ttu-id="abcae-322">Solicitação/resposta, o iniciador endereçável</span><span class="sxs-lookup"><span data-stu-id="abcae-322">Request/Reply, Addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="abcae-323">Associação</span><span class="sxs-lookup"><span data-stu-id="abcae-323">Binding</span></span>  
 <span data-ttu-id="abcae-324">O WCF fornece um padrão de troca de mensagem de solicitação-resposta usando duas sequências sobre uma entrada e um canal HTTP de saída.</span><span class="sxs-lookup"><span data-stu-id="abcae-324">WCF provides a request-reply message exchange pattern using two sequences over one inbound and one outbound HTTP channel.</span></span> <span data-ttu-id="abcae-325">Esse padrão de troca de mensagem pode ser combinado com o `Duplex, Addressable` padrão de troca de mensagem do iniciador de uma maneira limitada.</span><span class="sxs-lookup"><span data-stu-id="abcae-325">This message exchange pattern can be mixed with the `Duplex, Addressable` Initiator message exchange pattern in a limited way.</span></span> <span data-ttu-id="abcae-326">O WCF usa as solicitações HTTP para transmitir todas as mensagens.</span><span class="sxs-lookup"><span data-stu-id="abcae-326">WCF uses the HTTP requests to transmit all messages.</span></span> <span data-ttu-id="abcae-327">Todas as respostas HTTP tem um corpo vazio e o código de status HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="abcae-327">All HTTP responses have an empty body and HTTP 202 status code.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="abcae-328">Exchange CreateSequence</span><span class="sxs-lookup"><span data-stu-id="abcae-328">CreateSequence Exchange</span></span>  
 <span data-ttu-id="abcae-329">O iniciador do WCF transmite uma `CreateSequence` da mensagem com um `Offer` elemento em uma solicitação HTTP.</span><span class="sxs-lookup"><span data-stu-id="abcae-329">The WCF Initiator transmits a `CreateSequence` message with an `Offer` element on an HTTP request.</span></span> <span data-ttu-id="abcae-330">O Respondente WCF garante que o `CreateSequence` tem um `Offer` elemento, em seguida, cria uma sequência e transmite a `CreateSequenceResponse` da mensagem com um `Accept` elemento.</span><span class="sxs-lookup"><span data-stu-id="abcae-330">The WCF Responder ensures that the `CreateSequence` has an `Offer` element then creates a sequence and transmits the `CreateSequenceResponse` message with an `Accept` element.</span></span>  
  
#### <a name="requestreply-correlation"></a><span data-ttu-id="abcae-331">Correlação de solicitação/resposta</span><span class="sxs-lookup"><span data-stu-id="abcae-331">Request/Reply Correlation</span></span>  
 <span data-ttu-id="abcae-332">O seguinte se aplica a correlacionados todas as solicitações e respostas:</span><span class="sxs-lookup"><span data-stu-id="abcae-332">The following applies to all correlated requests and replies:</span></span>  
  
-   <span data-ttu-id="abcae-333">WCF garante que todos os urso de mensagens de solicitação de aplicativo um `ReplyTo` referência de ponto de extremidade e um `MessageId`.</span><span class="sxs-lookup"><span data-stu-id="abcae-333">WCF ensures all application request messages bear a `ReplyTo` endpoint reference and a `MessageId`.</span></span>  
  
-   <span data-ttu-id="abcae-334">WCF aplica-se a referência de ponto de extremidade local como cada mensagem de solicitação de aplicativo `ReplyTo`.</span><span class="sxs-lookup"><span data-stu-id="abcae-334">WCF applies the local endpoint reference as each application request message’s `ReplyTo`.</span></span> <span data-ttu-id="abcae-335">A referência de ponto de extremidade local é o `CreateSequence` da mensagem `ReplyTo` para o iniciador e o `CreateSequence` da mensagem `To` para o respondente.</span><span class="sxs-lookup"><span data-stu-id="abcae-335">The local endpoint reference is the `CreateSequence` message’s `ReplyTo` for the Initiator and the `CreateSequence` message’s `To` for the Responder.</span></span>  
  
-   <span data-ttu-id="abcae-336">WCF garante essa solicitação de entrada de mensagens tenha uma `MessageId` e um `ReplyTo`.</span><span class="sxs-lookup"><span data-stu-id="abcae-336">WCF ensures that incoming request messages bear a `MessageId` and a `ReplyTo`.</span></span>  
  
-   <span data-ttu-id="abcae-337">WCF garante a `ReplyTo` URI da referência do ponto de extremidade de todas as mensagens de solicitação do aplicativo corresponde à referência do ponto de extremidade local, conforme definido anteriormente.</span><span class="sxs-lookup"><span data-stu-id="abcae-337">WCF ensures the `ReplyTo` endpoint reference’s URI of all application request messages match the local endpoint reference as defined earlier.</span></span>  
  
-   <span data-ttu-id="abcae-338">WCF garante que todas as respostas assume integralmente o correto `RelatesTo` e `To` cabeçalhos a seguir `wsa` regras de correlação de solicitação/resposta.</span><span class="sxs-lookup"><span data-stu-id="abcae-338">WCF ensures that all replies bear the correct `RelatesTo` and `To` headers following `wsa` request/reply correlation rules.</span></span>
