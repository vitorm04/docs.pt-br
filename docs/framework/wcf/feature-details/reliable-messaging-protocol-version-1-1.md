---
title: Protocolo de mensagem confiável versão 1.1
ms.date: 03/30/2017
ms.assetid: 0da47b82-f8eb-42da-8bfe-e56ce7ba6f59
ms.openlocfilehash: 8ff02bc6953ec1e5030dd0b592a352b7e23ab0d6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="reliable-messaging-protocol-version-11"></a><span data-ttu-id="f662f-102">Protocolo de mensagem confiável versão 1.1</span><span class="sxs-lookup"><span data-stu-id="f662f-102">Reliable Messaging Protocol version 1.1</span></span>
<span data-ttu-id="f662f-103">Este tópico abrange detalhes de implementação do Windows Communication Foundation (WCF) para o WS-ReliableMessaging de fevereiro de 2007 (versão 1.1) protocolo necessário para a interoperação usando o transporte HTTP.</span><span class="sxs-lookup"><span data-stu-id="f662f-103">This topic covers Windows Communication Foundation (WCF) implementation details for the WS-ReliableMessaging February 2007 (version 1.1) protocol necessary for interoperation using the HTTP transport.</span></span> <span data-ttu-id="f662f-104">WCF segue a especificação WS-ReliableMessaging com as restrições e esclarecimentos explicados neste tópico.</span><span class="sxs-lookup"><span data-stu-id="f662f-104">WCF follows the WS-ReliableMessaging specification with the constraints and clarifications explained in this topic.</span></span> <span data-ttu-id="f662f-105">Observe que o protocolo do WS-ReliableMessaging versão 1.1 é implementado começando com o [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f662f-105">Note that the WS-ReliableMessaging version 1.1 protocol is implemented starting with the [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)].</span></span>  
  
 <span data-ttu-id="f662f-106">O WS-ReliableMessaging de fevereiro de 2007 protocolo é implementado no WCF, o <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="f662f-106">The WS-ReliableMessaging February 2007 protocol is implemented in WCF by the <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>.</span></span>  
  
 <span data-ttu-id="f662f-107">Para sua conveniência, o tópico usa as seguintes funções:</span><span class="sxs-lookup"><span data-stu-id="f662f-107">For convenience, the topic uses the following roles:</span></span>  
  
-   <span data-ttu-id="f662f-108">Iniciador: O cliente que inicia a criação de sequência de mensagem WS-Reliable.</span><span class="sxs-lookup"><span data-stu-id="f662f-108">Initiator: The client that initiates WS-Reliable Message sequence creation.</span></span>  
  
-   <span data-ttu-id="f662f-109">Respondente: O serviço que recebe as solicitações do iniciador.</span><span class="sxs-lookup"><span data-stu-id="f662f-109">Responder: The service that receives the initiator's requests.</span></span>  
  
 <span data-ttu-id="f662f-110">Este documento usa os namespaces e prefixos na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="f662f-110">This document uses the prefixes and namespaces in the following table.</span></span>  
  
|<span data-ttu-id="f662f-111">Prefixo</span><span class="sxs-lookup"><span data-stu-id="f662f-111">Prefix</span></span>|<span data-ttu-id="f662f-112">Namespace</span><span class="sxs-lookup"><span data-stu-id="f662f-112">Namespace</span></span>|  
|-|-|  
|<span data-ttu-id="f662f-113">WSRM</span><span class="sxs-lookup"><span data-stu-id="f662f-113">wsrm</span></span>|http://docs.oasis-open.org/ws-rx/wsrm/200702|  
|<span data-ttu-id="f662f-114">netrm</span><span class="sxs-lookup"><span data-stu-id="f662f-114">netrm</span></span>|http://schemas.microsoft.com/ws/2006/05/rm|  
|<span data-ttu-id="f662f-115">s</span><span class="sxs-lookup"><span data-stu-id="f662f-115">s</span></span>|http://www.w3.org/2003/05/soap-envelope|  
|<span data-ttu-id="f662f-116">wsa</span><span class="sxs-lookup"><span data-stu-id="f662f-116">wsa</span></span>|http://schemas.xmlsoap.org/ws/2005/08/addressing|  
|<span data-ttu-id="f662f-117">wsse</span><span class="sxs-lookup"><span data-stu-id="f662f-117">wsse</span></span>|http://docs.oasis-open.org/wss/2004/01/oasis-200401-wssecurity-secext-1.0.xsd|  
|<span data-ttu-id="f662f-118">wsrmp</span><span class="sxs-lookup"><span data-stu-id="f662f-118">wsrmp</span></span>|http://docs.oasis-open.org/ws-rx/wsrmp/200702|  
|<span data-ttu-id="f662f-119">netrmp</span><span class="sxs-lookup"><span data-stu-id="f662f-119">netrmp</span></span>|http://schemas.microsoft.com/ws-rx/wsrmp/200702|  
|<span data-ttu-id="f662f-120">wsp</span><span class="sxs-lookup"><span data-stu-id="f662f-120">wsp</span></span>|<span data-ttu-id="f662f-121">(WS-Policy 1.2 ou WS-Policy 1.5)</span><span class="sxs-lookup"><span data-stu-id="f662f-121">(Either WS-Policy 1.2 or WS-Policy 1.5)</span></span>|  
  
## <a name="messaging"></a><span data-ttu-id="f662f-122">Mensagens</span><span class="sxs-lookup"><span data-stu-id="f662f-122">Messaging</span></span>  
  
### <a name="sequence-creation"></a><span data-ttu-id="f662f-123">Criação de sequência</span><span class="sxs-lookup"><span data-stu-id="f662f-123">Sequence Creation</span></span>  
 <span data-ttu-id="f662f-124">O WCF implementa `CreateSequence` e `CreateSequenceResponse` de sequência de mensagens para estabelecer um sistema de mensagens confiável.</span><span class="sxs-lookup"><span data-stu-id="f662f-124">WCF implements `CreateSequence` and `CreateSequenceResponse` messages to establish a reliable messaging sequence.</span></span> <span data-ttu-id="f662f-125">As seguintes restrições se aplicam:</span><span class="sxs-lookup"><span data-stu-id="f662f-125">The following constraints apply:</span></span>  
  
-   <span data-ttu-id="f662f-126">B1101: O iniciador de WCF usa a mesma referência de ponto de extremidade como o `CreateSequence` da mensagem `ReplyTo`, `AcksTo` e `Offer/Endpoint`.</span><span class="sxs-lookup"><span data-stu-id="f662f-126">B1101: The WCF Initiator uses the same endpoint reference as the `CreateSequence` message’s `ReplyTo`, `AcksTo` and `Offer/Endpoint`.</span></span>  
  
-   <span data-ttu-id="f662f-127">R1102: O `AcksTo`, `ReplyTo` e `Offer/Endpoint` referências de ponto de extremidade no `CreateSequence` mensagem deve ter valores de endereço com representações de cadeia de caracteres idêntica, de modo que elas correspondam ao octet-wise.</span><span class="sxs-lookup"><span data-stu-id="f662f-127">R1102: The `AcksTo`, `ReplyTo` and `Offer/Endpoint` endpoint references in the `CreateSequence` message must have address values with identical string representations such that they match the octet-wise.</span></span>  
  
    -   <span data-ttu-id="f662f-128">O WCF respondente verifica se a parte do URI do `AcksTo`, `ReplyTo` e `Endpoint` referências de ponto de extremidade são idênticas antes de criar uma sequência.</span><span class="sxs-lookup"><span data-stu-id="f662f-128">The WCF Responder verifies that the URI portion of the `AcksTo`, `ReplyTo` and `Endpoint` endpoint references are identical before creating a sequence.</span></span>  
  
-   <span data-ttu-id="f662f-129">R1103: O `AcksTo`, `ReplyTo` e `Offer/Endpoint` referências de ponto de extremidade no `CreateSequence` mensagem deve ter o mesmo conjunto de parâmetros de referência.</span><span class="sxs-lookup"><span data-stu-id="f662f-129">R1103: The `AcksTo`, `ReplyTo` and `Offer/Endpoint` endpoint references in the `CreateSequence` message should have the same set of reference parameters.</span></span>  
  
    -   <span data-ttu-id="f662f-130">WCF não impõe, mas presume que referenciam parâmetros do `AcksTo`, `ReplyTo` e `Offer/Endpoint` referências de ponto de extremidade nas `CreateSequence` são idênticos e usa os parâmetros de referência do `ReplyTo` referência de ponto de extremidade para confirmações e mensagens na sequência inverso.</span><span class="sxs-lookup"><span data-stu-id="f662f-130">WCF does not enforce, but assumes that reference parameters of the `AcksTo`, `ReplyTo` and `Offer/Endpoint` endpoint references on `CreateSequence` are identical and uses reference parameters from the `ReplyTo` endpoint reference for acknowledgements and converse sequence messages.</span></span>  
  
-   <span data-ttu-id="f662f-131">B1104: O iniciador do WCF não gera opcional `Expires` ou `Offer/Expires` elemento o `CreateSequence` mensagem.</span><span class="sxs-lookup"><span data-stu-id="f662f-131">B1104: The WCF Initiator does not generate the optional `Expires` or `Offer/Expires` element in the `CreateSequence` message.</span></span>  
  
-   <span data-ttu-id="f662f-132">B1105: Ao acessar o `CreateSequence` mensagem, o WCF Respondente usa o `Expires` valor no `CreateSequence` elemento como o `Expires` valor no `CreateSequenceResponse` elemento.</span><span class="sxs-lookup"><span data-stu-id="f662f-132">B1105: When accessing the `CreateSequence` message, the WCF Responder uses the `Expires` value in the `CreateSequence` element as the `Expires` value in the `CreateSequenceResponse` element.</span></span> <span data-ttu-id="f662f-133">Caso contrário, o Respondente WCF lê e ignora o `Expires` e `Offer/Expires` valores.</span><span class="sxs-lookup"><span data-stu-id="f662f-133">Otherwise, the WCF Responder reads and ignores the `Expires` and `Offer/Expires` values.</span></span>  
  
-   <span data-ttu-id="f662f-134">B1106: Ao acessar o `CreateSequenceResponse` mensagem, o iniciador de WCF lê opcional `Expires` valor mas não usá-lo.</span><span class="sxs-lookup"><span data-stu-id="f662f-134">B1106: When accessing the `CreateSequenceResponse` message, the WCF Initiator reads the optional `Expires` value but does not use it.</span></span>  
  
-   <span data-ttu-id="f662f-135">B1107: O WCF iniciador e Respondente sempre geram opcional `IncompleteSequenceBehavior` elemento o `CreateSequence/Offer` e `CreateSequenceResponse` elementos.</span><span class="sxs-lookup"><span data-stu-id="f662f-135">B1107: The WCF Initiator and Responder always generate the optional `IncompleteSequenceBehavior` element in the `CreateSequence/Offer` and `CreateSequenceResponse` elements.</span></span>  
  
-   <span data-ttu-id="f662f-136">B1108: WCF usa apenas o `DiscardFollowingFirstGap` e `NoDiscard` valores no `IncompleteSequenceBehavior` elemento.</span><span class="sxs-lookup"><span data-stu-id="f662f-136">B1108: WCF uses only the `DiscardFollowingFirstGap` and `NoDiscard` values in the `IncompleteSequenceBehavior` element.</span></span>  
  
    -   <span data-ttu-id="f662f-137">WS-ReliableMessaging utiliza o `Offer` mecanismo para estabelecer os dois conversam correlacionadas sequências que formam uma sessão.</span><span class="sxs-lookup"><span data-stu-id="f662f-137">WS-ReliableMessaging utilizes the `Offer` mechanism to establish the two converse correlated sequences that form a session.</span></span>  
  
-   <span data-ttu-id="f662f-138">B1109: Se `CreateSequence` contém um `Offer` elemento, o Respondente unidirecional de WCF rejeita a sequência oferecida por responder com uma `CreateSequenceResponse` sem um `Accept` elemento.</span><span class="sxs-lookup"><span data-stu-id="f662f-138">B1109: If `CreateSequence` contains an `Offer` element, the one way WCF Responder rejects the offered sequence by responding with a `CreateSequenceResponse` without an `Accept` element.</span></span>  
  
-   <span data-ttu-id="f662f-139">B1110: Se um Respondente de mensagens confiável rejeita a sequência oferecida, o iniciador do WCF de falhas de sequência recentemente estabelecida.</span><span class="sxs-lookup"><span data-stu-id="f662f-139">B1110: If a Reliable Messaging Responder rejects the offered sequence, the WCF Initiator faults the newly established sequence.</span></span>  
  
-   <span data-ttu-id="f662f-140">B1111: Se `CreateSequence` não contém um `Offer` elemento, o Respondente bidirecional de WCF rejeita a sequência oferecida por responder com uma `CreateSequenceRefused` falha.</span><span class="sxs-lookup"><span data-stu-id="f662f-140">B1111: If `CreateSequence` does not contain an `Offer` element, the two-way WCF Responder rejects the offered sequence by responding with a `CreateSequenceRefused` fault.</span></span>  
  
-   <span data-ttu-id="f662f-141">R1112: Quando dois conversam sequências estabelecidas usando o `Offer` mecanismo, o `[address]` propriedade o `CreateSequenceResponse/Accept/AcksTo` referência de ponto de extremidade deve coincidir com o URI de destino do `CreateSequence` bytes de mensagem para byte.</span><span class="sxs-lookup"><span data-stu-id="f662f-141">R1112: When two converse sequences are established using the `Offer` mechanism, the `[address]` property of the `CreateSequenceResponse/Accept/AcksTo` endpoint reference must match the destination URI of the `CreateSequence` message byte for byte.</span></span>  
  
-   <span data-ttu-id="f662f-142">R1113: Quando dois conversam sequências estabelecidas usando o `Offer` mecanismo, todas as mensagens em ambas as sequências que fluem do iniciador para o respondedor devem ser enviadas para a mesma referência de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="f662f-142">R1113: When two converse sequences are established using the `Offer` mechanism, all messages on both sequences flowing from the Initiator to the Responder must be sent to the same endpoint reference.</span></span>  
  
 <span data-ttu-id="f662f-143">Para estabelecer sessões confiáveis entre o iniciador e Respondente, o WCF usa WS-ReliableMessaging.</span><span class="sxs-lookup"><span data-stu-id="f662f-143">WCF uses WS-ReliableMessaging to establish reliable sessions between the Initiator and the Responder.</span></span> <span data-ttu-id="f662f-144">A implementação de WCF WS-ReliableMessaging fornece uma sessão confiável para unidirecional, solicitação-resposta e full duplex padrões de mensagens.</span><span class="sxs-lookup"><span data-stu-id="f662f-144">The WCF WS-ReliableMessaging implementation provides a reliable session for one-way, request-reply and full duplex messaging patterns.</span></span> <span data-ttu-id="f662f-145">O WS-ReliableMessaging `Offer` mecanismo `CreateSequence` e `CreateSequenceResponse` permite que você estabeleça inverso correlacionado duas sequências e fornece um protocolo de sessão que é adequado para todos os pontos de extremidade de mensagens.</span><span class="sxs-lookup"><span data-stu-id="f662f-145">The WS-ReliableMessaging `Offer` mechanism on `CreateSequence` and `CreateSequenceResponse` lets you establish two correlated converse sequences and provides a session protocol that is suitable for all message endpoints.</span></span> <span data-ttu-id="f662f-146">Como o WCF fornece uma garantia de segurança para uma sessão incluindo proteção de ponta a ponta para integridade de sessão, é prático garantir que as mensagens destinadas a mesma parte chegarem ao mesmo destino.</span><span class="sxs-lookup"><span data-stu-id="f662f-146">Because WCF provides a security guarantee for such a session including end-to-end protection for session integrity, it is practical to ensure that messages intended for the same party arrive at the same destination.</span></span> <span data-ttu-id="f662f-147">Isso também permite que a "inclua-backup" de confirmações de sequência em mensagens de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f662f-147">This also allows "piggy-backing" of sequence acknowledgements on application messages.</span></span> <span data-ttu-id="f662f-148">Portanto, R1102, R1112 e R1113 as restrições se aplicam ao WCF.</span><span class="sxs-lookup"><span data-stu-id="f662f-148">Therefore, constraints R1102, R1112, and R1113 apply to WCF.</span></span>  
  
 <span data-ttu-id="f662f-149">Um exemplo de um `CreateSequence` mensagem.</span><span class="sxs-lookup"><span data-stu-id="f662f-149">An example of a `CreateSequence` message.</span></span>  
  
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
  
 <span data-ttu-id="f662f-150">Um exemplo de um `CreateSequenceResponse` mensagem.</span><span class="sxs-lookup"><span data-stu-id="f662f-150">An example of a `CreateSequenceResponse` message.</span></span>  
  
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
  
### <a name="closing-a-sequence"></a><span data-ttu-id="f662f-151">Fechando uma sequência</span><span class="sxs-lookup"><span data-stu-id="f662f-151">Closing a Sequence</span></span>  
 <span data-ttu-id="f662f-152">O WCF usa o `CloseSequence` e `CloseSequenceResponse` mensagens para um desligamento iniciado fonte mensagens confiáveis.</span><span class="sxs-lookup"><span data-stu-id="f662f-152">WCF uses the `CloseSequence` and `CloseSequenceResponse` messages for a Reliable Messaging source-initiated shutdown.</span></span> <span data-ttu-id="f662f-153">O destino do sistema de mensagens confiável do WCF não iniciar o desligamento e a fonte de mensagens confiáveis do WCF não dá suporte a um desligamento iniciado pelo destino mensagens confiáveis.</span><span class="sxs-lookup"><span data-stu-id="f662f-153">The WCF Reliable Messaging destination does not initiate shutdown and the WCF Reliable Messaging source does not support a Reliable Messaging destination-initiated shutdown.</span></span> <span data-ttu-id="f662f-154">As seguintes restrições se aplicam:</span><span class="sxs-lookup"><span data-stu-id="f662f-154">The following constraints apply:</span></span>  
  
-   <span data-ttu-id="f662f-155">B1201: A origem de mensagens confiáveis do WCF sempre envia um `CloseSequence` mensagem desligar a sequência.</span><span class="sxs-lookup"><span data-stu-id="f662f-155">B1201: The WCF Reliable Messaging source always sends a `CloseSequence` message to shut down the sequence.</span></span>  
  
-   <span data-ttu-id="f662f-156">B1202: A origem de mensagens confiáveis aguarda confirmação de toda a gama de mensagens na sequência antes de enviar o `CloseSequence` mensagem.</span><span class="sxs-lookup"><span data-stu-id="f662f-156">B1202: The Reliable Messaging source waits for acknowledgement of the full range of sequence messages before sending the `CloseSequence` message.</span></span>  
  
-   <span data-ttu-id="f662f-157">B1203: A origem de mensagens confiáveis sempre inclui opcional `LastMsgNumber` elemento, a menos que a sequência não contém mensagens.</span><span class="sxs-lookup"><span data-stu-id="f662f-157">B1203: The Reliable Messaging source always includes the optional `LastMsgNumber` element unless the sequence does not contain messages.</span></span>  
  
-   <span data-ttu-id="f662f-158">R1204: O destino de mensagens confiáveis não deve iniciar desligamento enviando um `CloseSequence` mensagem.</span><span class="sxs-lookup"><span data-stu-id="f662f-158">R1204: The Reliable Messaging destination must not initiate shutdown by sending a `CloseSequence` message.</span></span>  
  
-   <span data-ttu-id="f662f-159">B1205: após receber um `CloseSequence` mensagem, a origem de mensagens confiáveis do WCF considera a sequência incompleta e envia uma falha.</span><span class="sxs-lookup"><span data-stu-id="f662f-159">B1205: Upon receiving a `CloseSequence` message, the WCF Reliable Messaging source considers the sequence incomplete and sends a fault.</span></span>  
  
 <span data-ttu-id="f662f-160">Um exemplo de um `CloseSequence` mensagem.</span><span class="sxs-lookup"><span data-stu-id="f662f-160">An example of a `CloseSequence` message.</span></span>  
  
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
  
### <a name="sequence-termination"></a><span data-ttu-id="f662f-161">Término de sequência</span><span class="sxs-lookup"><span data-stu-id="f662f-161">Sequence Termination</span></span>  
 <span data-ttu-id="f662f-162">WCF usa basicamente o `TerminateSequence/TerminateSequenceResponse` handshake depois de concluir o `CloseSequence/CloseSequenceResponse` handshake.</span><span class="sxs-lookup"><span data-stu-id="f662f-162">WCF primarily uses the `TerminateSequence/TerminateSequenceResponse` handshake after completing the `CloseSequence/CloseSequenceResponse` handshake.</span></span> <span data-ttu-id="f662f-163">O destino do sistema de mensagens confiável do WCF não iniciará o encerramento e a fonte de mensagens confiáveis não dá suporte a um sistema de mensagens confiável iniciadas pelo destino encerramento.</span><span class="sxs-lookup"><span data-stu-id="f662f-163">The WCF Reliable Messaging destination does not initiate termination and the Reliable Messaging source does not support a Reliable Messaging destination-initiated termination.</span></span> <span data-ttu-id="f662f-164">As seguintes restrições se aplicam:</span><span class="sxs-lookup"><span data-stu-id="f662f-164">The following constraints apply:</span></span>  
  
-   <span data-ttu-id="f662f-165">B1301: O iniciador de WCF envia somente a `TerminateSequence` mensagem após a conclusão bem-sucedida do `CloseSequence/CloseSequenceResponse` handshake.</span><span class="sxs-lookup"><span data-stu-id="f662f-165">B1301: The WCF Initiator only sends the `TerminateSequence` message after the successful completion of the `CloseSequence/CloseSequenceResponse` handshake.</span></span>  
  
-   <span data-ttu-id="f662f-166">R1302: WCF valida que o `LastMsgNumber` elemento é consistente em todas as `CloseSequence` e `TerminateSequence` mensagens para uma determinada sequência.</span><span class="sxs-lookup"><span data-stu-id="f662f-166">R1302: WCF validates that the `LastMsgNumber` element is consistent across all `CloseSequence` and `TerminateSequence` messages for a given sequence.</span></span> <span data-ttu-id="f662f-167">Isso significa que `LastMsgNumber` não está presente em todos os `CloseSequence` e `TerminateSequence` mensagens, ou ele está presente e idênticos em todos os `CloseSequence` e `TerminateSequence` mensagens.</span><span class="sxs-lookup"><span data-stu-id="f662f-167">This means that `LastMsgNumber` is either not present on all `CloseSequence` and `TerminateSequence` messages, or it is present and identical on all `CloseSequence` and `TerminateSequence` messages.</span></span>  
  
-   <span data-ttu-id="f662f-168">B1303: Durante o recebimento de uma `TerminateSequence` mensagem após o `CloseSequence/CloseSequenceResponse` handshake, o destino do sistema de mensagens confiável responde com um `TerminateSequenceResponse` mensagem.</span><span class="sxs-lookup"><span data-stu-id="f662f-168">B1303: When receiving a `TerminateSequence` message after the `CloseSequence/CloseSequenceResponse` handshake, the Reliable Messaging destination responds with a `TerminateSequenceResponse` message.</span></span> <span data-ttu-id="f662f-169">Como a origem do sistema de mensagens confiável tem a confirmação final antes de enviar o `TerminateSequence` mensagem, o destino do sistema de mensagens confiável sabe, sem dúvida que a sequência termina e recupera os recursos imediatamente.</span><span class="sxs-lookup"><span data-stu-id="f662f-169">Because the Reliable Messaging source has the final acknowledgement before sending the `TerminateSequence` message, the Reliable Messaging destination knows without doubt that the sequence ends, and reclaims resources immediately.</span></span>  
  
-   <span data-ttu-id="f662f-170">B1304: Durante o recebimento de uma `TerminateSequence` mensagem antes do `CloseSequence/CloseSequenceResponse` handshake, o destino do sistema de mensagens confiável do WCF responde com um `TerminateSequenceResponse` mensagem.</span><span class="sxs-lookup"><span data-stu-id="f662f-170">B1304: When receiving a `TerminateSequence` message prior to the `CloseSequence/CloseSequenceResponse` handshake, the WCF Reliable Messaging destination responds with a `TerminateSequenceResponse` message.</span></span> <span data-ttu-id="f662f-171">Se o destino do sistema de mensagens confiável determina que não há nenhuma inconsistência na sequência, o destino do sistema de mensagens confiável aguarda uma hora de destino especificado do aplicativo antes da recuperação de recursos, para permitir que o cliente a chance de recebimento a confirmação final.</span><span class="sxs-lookup"><span data-stu-id="f662f-171">If the Reliable Messaging destination determines that there are no inconsistencies in the sequence, the Reliable Messaging destination waits for an application destination-specified time before reclaiming resources, to allow the client the chance to receive the final acknowledgement.</span></span> <span data-ttu-id="f662f-172">Caso contrário, o destino do sistema de mensagens confiável recupera os recursos imediatamente e indica para o destino do aplicativo que a sequência termina com dúvida, gerando o `Faulted` evento.</span><span class="sxs-lookup"><span data-stu-id="f662f-172">Otherwise, the Reliable Messaging destination reclaims resources immediately and indicates to the application destination that the sequence ends with doubt by raising the `Faulted` event.</span></span>  
  
 <span data-ttu-id="f662f-173">Um exemplo de um `TerminateSequence` mensagem.</span><span class="sxs-lookup"><span data-stu-id="f662f-173">An example of a `TerminateSequence` message.</span></span>  
  
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
  
### <a name="sequences"></a><span data-ttu-id="f662f-174">Sequências</span><span class="sxs-lookup"><span data-stu-id="f662f-174">Sequences</span></span>  
 <span data-ttu-id="f662f-175">A seguir está uma lista de restrições que se aplicam a sequências:</span><span class="sxs-lookup"><span data-stu-id="f662f-175">The following is a list of constraints that apply to sequences:</span></span>  
  
-   <span data-ttu-id="f662f-176">Gera B1401:WCF e maior do que de números de sequência de acessos `xs:long`do valor inclusivo máximo, 9223372036854775807.</span><span class="sxs-lookup"><span data-stu-id="f662f-176">B1401:WCF generates and accesses sequence numbers no higher than `xs:long`’s maximum inclusive value, 9223372036854775807.</span></span>  
  
 <span data-ttu-id="f662f-177">Um exemplo de um `Sequence` cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="f662f-177">An example of a `Sequence` header.</span></span>  
  
```xml  
<wsrm:Sequence s:mustUnderstand="1">  
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
  <wsrm:MessageNumber>1</wsrm:MessageNumber>  
</wsrm:Sequence>  
```  
  
### <a name="request-acknowledgement"></a><span data-ttu-id="f662f-178">Solicitação de confirmação</span><span class="sxs-lookup"><span data-stu-id="f662f-178">Request Acknowledgement</span></span>  
 <span data-ttu-id="f662f-179">O WCF usa o `AckRequested` cabeçalho como um mecanismo de keep-alive.</span><span class="sxs-lookup"><span data-stu-id="f662f-179">WCF uses the `AckRequested` header as a keep-alive mechanism.</span></span>  
  
 <span data-ttu-id="f662f-180">Um exemplo de um `AckRequested` cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="f662f-180">An example of an `AckRequested` header.</span></span>  
  
```xml  
<wsrm:AckRequested>  
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
</wsrm:AckRequested>  
```  
  
### <a name="sequenceacknowledgement"></a><span data-ttu-id="f662f-181">SequenceAcknowledgement</span><span class="sxs-lookup"><span data-stu-id="f662f-181">SequenceAcknowledgement</span></span>  
 <span data-ttu-id="f662f-182">WCF usa um mecanismo de "back inclua" para confirmações de sequência fornecidas em mensagens WS-Reliable.</span><span class="sxs-lookup"><span data-stu-id="f662f-182">WCF uses a "piggy-back" mechanism for sequence acknowledgements provided in WS-Reliable Messaging.</span></span> <span data-ttu-id="f662f-183">As seguintes restrições se aplicam:</span><span class="sxs-lookup"><span data-stu-id="f662f-183">The following constraints apply:</span></span>  
  
-   <span data-ttu-id="f662f-184">R1601: Quando dois conversam sequências estabelecidas usando o `Offer` mecanismo, o `SequenceAcknowledgement` cabeçalho pode ser incluído em qualquer mensagem de aplicativo transmitida para o destinatário pretendido.</span><span class="sxs-lookup"><span data-stu-id="f662f-184">R1601: When two converse sequences are established using the `Offer` mechanism, the `SequenceAcknowledgement` header may be included in any application message transmitted to the intended recipient.</span></span> <span data-ttu-id="f662f-185">O ponto de extremidade remoto deve ser capaz de acessar um acumuladas `SequenceAcknowledgement` cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="f662f-185">The remote endpoint must be able to access a piggybacked `SequenceAcknowledgement` header.</span></span>  
  
-   <span data-ttu-id="f662f-186">B1602: WCF não gerar `SequenceAcknowledgement` cabeçalhos que contêm `Nack` elementos.</span><span class="sxs-lookup"><span data-stu-id="f662f-186">B1602: WCF does not generate `SequenceAcknowledgement` headers that contain `Nack` elements.</span></span> <span data-ttu-id="f662f-187">WCF valida cada `Nack` elemento contém um número de sequência, mas ignora caso contrário, o `Nack` elemento e valor.</span><span class="sxs-lookup"><span data-stu-id="f662f-187">WCF validates that each `Nack` element contains a sequence number, but otherwise ignores the `Nack` element and value.</span></span>  
  
 <span data-ttu-id="f662f-188">Um exemplo de um `SequenceAcknowledgement` cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="f662f-188">An example of a `SequenceAcknowledgement` header.</span></span>  
  
```xml  
<wsrm:SequenceAcknowledgement>  
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
  <wsrm:AcknowledgementRange Lower="1" Upper="1"></wsrm:AcknowledgementRange>  
</wsrm:SequenceAcknowledgement>  
```  
  
### <a name="ws-reliablemessaging-faults"></a><span data-ttu-id="f662f-189">Falhas de WS-ReliableMessaging.</span><span class="sxs-lookup"><span data-stu-id="f662f-189">WS-ReliableMessaging Faults</span></span>  
 <span data-ttu-id="f662f-190">A seguir está uma lista de restrições que se aplicam a implementação de WCF de falhas de WS-ReliableMessaging.</span><span class="sxs-lookup"><span data-stu-id="f662f-190">The following is a list of constraints that apply to the WCF implementation of WS-ReliableMessaging faults.</span></span> <span data-ttu-id="f662f-191">As seguintes restrições se aplicam:</span><span class="sxs-lookup"><span data-stu-id="f662f-191">The following constraints apply:</span></span>  
  
-   <span data-ttu-id="f662f-192">B1701: WCF não gerar `MessageNumberRollover` falhas.</span><span class="sxs-lookup"><span data-stu-id="f662f-192">B1701: WCF does not generate `MessageNumberRollover` faults.</span></span>  
  
-   <span data-ttu-id="f662f-193">B1702: Sobre SOAP 1.2, quando o ponto de extremidade do serviço atinge seu limite de conexão e não pode processar novas conexões, o WCF gera um aninhada `CreateSequenceRefused` falha subcódigo, `netrm:ConnectionLimitReached`, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="f662f-193">B1702: Over SOAP 1.2, when the service endpoint reaches its connection limit and cannot process new connections, WCF generates a nested `CreateSequenceRefused` fault subcode, `netrm:ConnectionLimitReached`, as shown in the following example.</span></span>  
  
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
  
### <a name="ws-addressing-faults"></a><span data-ttu-id="f662f-194">Falhas de WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="f662f-194">WS-Addressing Faults</span></span>  
 <span data-ttu-id="f662f-195">Como WS-ReliableMessaging usa WS-Addressing, a implementação de WCF WS-ReliableMessaging pode gerar e transmitir falhas de WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="f662f-195">Because WS-ReliableMessaging uses WS-Addressing, the WCF WS-ReliableMessaging implementation may generate and transmit WS-Addressing faults.</span></span> <span data-ttu-id="f662f-196">Esta seção aborda as falhas de WS-Addressing que WCF gera e transmite na camada do WS-ReliableMessaging explicitamente:</span><span class="sxs-lookup"><span data-stu-id="f662f-196">This section covers the WS-Addressing faults that WCF explicitly generates and transmits at the WS-ReliableMessaging layer:</span></span>  
  
-   <span data-ttu-id="f662f-197">B1801:WCF gera e transmite o `Message Addressing Header Required` falha quando uma das seguintes opções for verdadeira:</span><span class="sxs-lookup"><span data-stu-id="f662f-197">B1801:WCF generates and transmits the `Message Addressing Header Required` fault when one of the following is true:</span></span>  
  
    -   <span data-ttu-id="f662f-198">Um `CreateSequence`, `CloseSequence` ou `TerminateSequence` mensagem está falta um `MessageId` cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="f662f-198">A `CreateSequence`, `CloseSequence` or `TerminateSequence` message is missing a `MessageId` header.</span></span>  
  
    -   <span data-ttu-id="f662f-199">Um `CreateSequence`, `CloseSequence` ou `TerminateSequence` mensagem está falta um `ReplyTo` cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="f662f-199">A `CreateSequence`, `CloseSequence` or `TerminateSequence` message is missing a `ReplyTo` header.</span></span>  
  
    -   <span data-ttu-id="f662f-200">Um `CreateSequenceResponse`, `CloseSequenceResponse`, ou `TerminateSequenceResponse` mensagem está falta um `RelatesTo` cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="f662f-200">A `CreateSequenceResponse`, `CloseSequenceResponse`, or `TerminateSequenceResponse` message is missing a `RelatesTo` header.</span></span>  
  
-   <span data-ttu-id="f662f-201">B1802:WCF gera e transmite o `Endpoint Unavailable` falhas para indicar que não há nenhum ponto de extremidade de escuta que podem processar a sequência com base na análise dos cabeçalhos de endereçamento no `CreateSequence` mensagem.</span><span class="sxs-lookup"><span data-stu-id="f662f-201">B1802:WCF generates and transmits the `Endpoint Unavailable` fault to indicate there is no endpoint listening that can process the sequence based on examination of the addressing headers in the `CreateSequence` message.</span></span>  
  
## <a name="protocol-composition"></a><span data-ttu-id="f662f-202">Composição de protocolo</span><span class="sxs-lookup"><span data-stu-id="f662f-202">Protocol Composition</span></span>  
  
### <a name="composition-with-ws-addressing"></a><span data-ttu-id="f662f-203">Composição com WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="f662f-203">Composition with WS-Addressing</span></span>  
 <span data-ttu-id="f662f-204">O WCF dá suporte a duas versões do WS-Addressing: 2004 do WS-Addressing/08 [WS-ADDR] e recomendações de 1.0 W3C WS-Addressing [WS-ADDR-CORE] e [WS-ADDR-SOAP].</span><span class="sxs-lookup"><span data-stu-id="f662f-204">WCF supports two versions of WS-Addressing: WS-Addressing 2004/08 [WS-ADDR] and W3C WS-Addressing 1.0 Recommendations [WS-ADDR-CORE] and [WS-ADDR-SOAP].</span></span>  
  
 <span data-ttu-id="f662f-205">Enquanto as menções de especificação WS-ReliableMessaging 2004 do WS-Addressing somente/08, não restringe a versão de WS-Addressing a ser usada.</span><span class="sxs-lookup"><span data-stu-id="f662f-205">While the WS-ReliableMessaging specification mentions only WS-Addressing 2004/08, it does not restrict the WS-Addressing version to be used.</span></span> <span data-ttu-id="f662f-206">A seguir está uma lista de restrições que se aplicam ao WCF:</span><span class="sxs-lookup"><span data-stu-id="f662f-206">The following is a list of constraints that apply to WCF:</span></span>  
  
-   <span data-ttu-id="f662f-207">R2101: Ambos 08/2004 do WS-Addressing e WS-Addressing 1.0 podem ser usado com mensagens WS-Reliable.</span><span class="sxs-lookup"><span data-stu-id="f662f-207">R2101: Both WS-Addressing 2004/08 and WS-Addressing 1.0 can be used with WS-Reliable Messaging.</span></span>  
  
-   <span data-ttu-id="f662f-208">R2102: Uma única versão do WS-Addressing deve ser usada em uma sequência WS-ReliableMessaging determinada ou um par de sequências inverso correlacionados usando o `Offer` mecanismo.</span><span class="sxs-lookup"><span data-stu-id="f662f-208">R2102: A single version of WS-Addressing must be used throughout a given WS-ReliableMessaging sequence or a pair of converse sequences correlated by using the `Offer` mechanism.</span></span>  
  
### <a name="composition-with-soap"></a><span data-ttu-id="f662f-209">Composição de SOAP</span><span class="sxs-lookup"><span data-stu-id="f662f-209">Composition with SOAP</span></span>  
 <span data-ttu-id="f662f-210">O WCF suporta o uso de SOAP 1.1 e SOAP 1.2 com mensagens WS-Reliable.</span><span class="sxs-lookup"><span data-stu-id="f662f-210">WCF supports the use of both SOAP 1.1 and SOAP 1.2 with WS-Reliable Messaging.</span></span>  
  
### <a name="composition-with-ws-security-and-ws-secureconversation"></a><span data-ttu-id="f662f-211">Composição com WS-Security e WS-SecureConversation</span><span class="sxs-lookup"><span data-stu-id="f662f-211">Composition with WS-Security and WS-SecureConversation</span></span>  
 <span data-ttu-id="f662f-212">WCF fornece proteção para as sequências de WS-ReliableMessaging usando o transporte (HTTPS), composição com WS-Security e composição seguro com WS-Secure Conversation.</span><span class="sxs-lookup"><span data-stu-id="f662f-212">WCF provides protection for WS-ReliableMessaging sequences by using secure Transport (HTTPS), composition with WS-Security, and composition with WS-Secure Conversation.</span></span> <span data-ttu-id="f662f-213">O protocolo WS-ReliableMessaging 1.1, WS-Security 1.1 e o protocolo WS-Secure Conversation 1.3 devem ser usados juntos.</span><span class="sxs-lookup"><span data-stu-id="f662f-213">The WS-ReliableMessaging 1.1 protocol, WS-Security 1.1 and WS-Secure Conversation 1.3 protocol should be used together.</span></span> <span data-ttu-id="f662f-214">A seguir está uma lista de restrições que se aplicam ao WCF:</span><span class="sxs-lookup"><span data-stu-id="f662f-214">The following is a list of constraints that apply to WCF:</span></span>  
  
-   <span data-ttu-id="f662f-215">R2301: Para proteger a integridade de uma sequência WS-ReliableMessaging além de integridade e confidencialidade de mensagens individuais, a WCF requer que o WS-Secure Conversation deve ser usado.</span><span class="sxs-lookup"><span data-stu-id="f662f-215">R2301: To protect the integrity of a WS-ReliableMessaging sequence in addition to the integrity and confidentiality of individual messages, WCF requires that WS-Secure Conversation must be used.</span></span>  
  
-   <span data-ttu-id="f662f-216">R2302:AWS-Secure Conversation deve ser estabelecida antes de estabelecer a sequência de WS-ReliableMessaging.</span><span class="sxs-lookup"><span data-stu-id="f662f-216">R2302:AWS-Secure Conversation session must be established prior to establishing WS-ReliableMessaging sequence(s).</span></span>  
  
-   <span data-ttu-id="f662f-217">R2303: Se o tempo de vida de sequência WS-ReliableMessaging excede o WS-Secure Conversation tempo de vida da sessão, o `SecurityContextToken` estabelecida usando o WS-Secure Conversation deve ser renovado usando a associação de WS-Secure Conversation renovação correspondente.</span><span class="sxs-lookup"><span data-stu-id="f662f-217">R2303: If the WS-ReliableMessaging sequence lifetime exceeds the WS-Secure Conversation session’s lifetime, the `SecurityContextToken` established by using WS-Secure Conversation must be renewed by using the corresponding WS-Secure Conversation Renewal binding.</span></span>  
  
-   <span data-ttu-id="f662f-218">B2304:WS-ReliableMessaging sequência ou um par de sequências inverso correlacionado sempre estão associados a uma única sessão do WS-SecureConversation.</span><span class="sxs-lookup"><span data-stu-id="f662f-218">B2304:WS-ReliableMessaging sequence or a pair of correlated converse sequences are always bound to a single WS-SecureConversation session.</span></span>  
  
-   <span data-ttu-id="f662f-219">R2305: Quando composto com WS-Secure Conversation, Respondente WCF requer que o `CreateSequence` mensagem contêm o `wsse:SecurityTokenReference` elemento e o `wsrm:UsesSequenceSTR` cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="f662f-219">R2305: When composed with WS-Secure Conversation, the WCF responder requires that the `CreateSequence` message contain the `wsse:SecurityTokenReference` element and the `wsrm:UsesSequenceSTR` header.</span></span>  
  
 <span data-ttu-id="f662f-220">Um exemplo de um `UsesSequenceSTR` cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="f662f-220">An example of a `UsesSequenceSTR` header.</span></span>  
  
```xml  
<wsrm:UsesSequenceSTR></wsrm:UsesSequenceSTR>  
```  
  
### <a name="composition-with-ssltls-sessions"></a><span data-ttu-id="f662f-221">Composição com sessões SSL/TLS</span><span class="sxs-lookup"><span data-stu-id="f662f-221">Composition with SSL/TLS sessions</span></span>  
 <span data-ttu-id="f662f-222">O WCF não oferece suporte a composição com sessões SSL/TLS:</span><span class="sxs-lookup"><span data-stu-id="f662f-222">WCF does not support composition with SSL/TLS sessions:</span></span>  
  
-   <span data-ttu-id="f662f-223">B2401: WCF não gera o `wsrm:UsesSequenceSSL` cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="f662f-223">B2401: WCF does not generate the `wsrm:UsesSequenceSSL` header.</span></span>  
  
-   <span data-ttu-id="f662f-224">R2402: Um iniciador de mensagens confiável não deve enviar um `CreateSequence` mensagem com um `wsrm:UsesSequenceSSL` cabeçalho para um Respondente WCF.</span><span class="sxs-lookup"><span data-stu-id="f662f-224">R2402: A Reliable Messaging Initiator must not send a `CreateSequence` message with a `wsrm:UsesSequenceSSL` header to a WCF Responder.</span></span>  
  
### <a name="composition-with-ws-policy"></a><span data-ttu-id="f662f-225">Composição com WS-Policy</span><span class="sxs-lookup"><span data-stu-id="f662f-225">Composition with WS-Policy</span></span>  
 <span data-ttu-id="f662f-226">O WCF dá suporte a duas versões do WS-Policy: WS-Policy 1.2 e WS-Policy 1.5.</span><span class="sxs-lookup"><span data-stu-id="f662f-226">WCF supports two versions of WS-Policy: WS-Policy 1.2 and WS-Policy 1.5.</span></span>  
  
## <a name="ws-reliablemessaging-ws-policy-assertion"></a><span data-ttu-id="f662f-227">WS-ReliableMessaging WS-declaração de política</span><span class="sxs-lookup"><span data-stu-id="f662f-227">WS-ReliableMessaging WS-Policy Assertion</span></span>  
 <span data-ttu-id="f662f-228">WCF usa WS-ReliableMessaging WS-Policy asserção `wsrm:RMAssertion` para descrever os recursos de pontos de extremidade.</span><span class="sxs-lookup"><span data-stu-id="f662f-228">WCF uses WS-ReliableMessaging WS-Policy Assertion `wsrm:RMAssertion` to describe endpoints capabilities.</span></span> <span data-ttu-id="f662f-229">A seguir está uma lista de restrições que se aplicam ao WCF:</span><span class="sxs-lookup"><span data-stu-id="f662f-229">The following is a list of constraints that apply to WCF:</span></span>  
  
-   <span data-ttu-id="f662f-230">B3001: WCF anexa `wsrmn:RMAssertion` asserção de WS-Policy para `wsdl:binding` elementos.</span><span class="sxs-lookup"><span data-stu-id="f662f-230">B3001: WCF attaches `wsrmn:RMAssertion` WS-Policy Assertion to `wsdl:binding` elements.</span></span> <span data-ttu-id="f662f-231">O WCF oferece suporte a ambos os anexos para `wsdl:binding` e `wsdl:port` elementos.</span><span class="sxs-lookup"><span data-stu-id="f662f-231">WCF supports both attachments to `wsdl:binding` and `wsdl:port` elements.</span></span>  
  
-   <span data-ttu-id="f662f-232">B3002: WCF nunca gera o `wsp:Optional` marca.</span><span class="sxs-lookup"><span data-stu-id="f662f-232">B3002: WCF never generates the `wsp:Optional` tag.</span></span>  
  
-   <span data-ttu-id="f662f-233">B3003: Ao acessar o `wsrmp:RMAssertion` asserção de WS-Policy WCF ignora o `wsp:Optional` marca e trata a política WS-RM como obrigatória.</span><span class="sxs-lookup"><span data-stu-id="f662f-233">B3003: When accessing the `wsrmp:RMAssertion` WS-Policy Assertion, WCF ignores the `wsp:Optional` tag and treats the WS-RM policy as mandatory.</span></span>  
  
-   <span data-ttu-id="f662f-234">R3004: Porque o WCF não compor com sessões SSL/TLS, WCF não aceita política especifica `wsrmp:SequenceTransportSecurity`.</span><span class="sxs-lookup"><span data-stu-id="f662f-234">R3004: Because WCF does not compose with SSL/TLS sessions, WCF does not accept policy that specifies `wsrmp:SequenceTransportSecurity`.</span></span>  
  
-   <span data-ttu-id="f662f-235">B3005: WCF sempre gera o `wsrmp:DeliveryAssurance` elemento.</span><span class="sxs-lookup"><span data-stu-id="f662f-235">B3005: WCF always generates the `wsrmp:DeliveryAssurance` element.</span></span>  
  
-   <span data-ttu-id="f662f-236">B3006: WCF sempre Especifica o `wsrmp:ExactlyOnce` garantia de entrega.</span><span class="sxs-lookup"><span data-stu-id="f662f-236">B3006: WCF always specifies the `wsrmp:ExactlyOnce` delivery assurance.</span></span>  
  
-   <span data-ttu-id="f662f-237">B3007: WCF gera e lê as seguintes propriedades da asserção WS-ReliableMessaging e fornece controle sobre eles em WCF`ReliableSessionBindingElement`:</span><span class="sxs-lookup"><span data-stu-id="f662f-237">B3007: WCF generates and reads the following properties of the WS-ReliableMessaging assertion and provides control over them on the WCF`ReliableSessionBindingElement`:</span></span>  
  
    -   `netrmp:InactivityTimeout`  
  
    -   `netrmp:AcknowledgementInterval`  
  
     <span data-ttu-id="f662f-238">Um exemplo de um `RMAssertion`.</span><span class="sxs-lookup"><span data-stu-id="f662f-238">An example of a `RMAssertion`.</span></span>  
  
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
  
## <a name="flow-control-ws-reliablemessaging-extension"></a><span data-ttu-id="f662f-239">Extensão de WS-ReliableMessaging de controle de fluxo</span><span class="sxs-lookup"><span data-stu-id="f662f-239">Flow Control WS-ReliableMessaging Extension</span></span>  
 <span data-ttu-id="f662f-240">WCF usa extensibilidade do WS-ReliableMessaging para fornecer maior controle adicional opcional sobre o fluxo de mensagem de sequência.</span><span class="sxs-lookup"><span data-stu-id="f662f-240">WCF uses WS-ReliableMessaging extensibility to provide optional additional tighter control over sequence message flow.</span></span>  
  
 <span data-ttu-id="f662f-241">Controle de fluxo é habilitado definindo o `ReliableSessionBindingElement`do `FlowControlEnabled``boolean` propriedade `true`.</span><span class="sxs-lookup"><span data-stu-id="f662f-241">Flow control is enabled by setting the `ReliableSessionBindingElement`’s `FlowControlEnabled``boolean` property to `true`.</span></span> <span data-ttu-id="f662f-242">A seguir está uma lista de restrições que se aplicam ao WCF:</span><span class="sxs-lookup"><span data-stu-id="f662f-242">The following is a list of constraints that apply to WCF:</span></span>  
  
-   <span data-ttu-id="f662f-243">B4001: Quando confiável de fluxo de controle de mensagens está habilitado, o WCF gera uma `netrm:BufferRemaining` a extensibilidade do elemento do elemento de `SequenceAcknowledgement` cabeçalho, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="f662f-243">B4001: When Reliable Messaging Flow Control is enabled, WCF generates a `netrm:BufferRemaining` element in the element extensibility of the `SequenceAcknowledgement` header, as shown in the following example.</span></span>  
  
    ```xml  
    <wsrm:SequenceAcknowledgement>  
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
      <wsrm:AcknowledgementRange Upper="1" Lower="1"/>             
      <netrm:BufferRemaining>8</netrm:BufferRemaining>  
    </wsrm:SequenceAcknowledgement>  
    ```  
  
-   <span data-ttu-id="f662f-244">B4002: Mesmo quando confiável de fluxo de controle de mensagens está habilitado, o WCF não exige um `netrm:BufferRemaining` elemento o `SequenceAcknowledgement` cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="f662f-244">B4002: Even when Reliable Messaging Flow Control is enabled, WCF does not require a `netrm:BufferRemaining` element in the `SequenceAcknowledgement` header.</span></span>  
  
-   <span data-ttu-id="f662f-245">B4003: Usa o destino de mensagens confiável WCF `netrm:BufferRemaining` indicar quantas novas mensagens ele consegue armazenar em buffer.</span><span class="sxs-lookup"><span data-stu-id="f662f-245">B4003: WCF Reliable Messaging Destination uses `netrm:BufferRemaining` to indicate how many new messages it can buffer.</span></span>  
  
-   <span data-ttu-id="f662f-246">B4004:when confiável de mensagens de fluxo de controle é habilitada, a origem de mensagens confiável WCF usam o valor de `netrm:BufferRemaining` para transmissão de mensagens de limitação.</span><span class="sxs-lookup"><span data-stu-id="f662f-246">B4004:When Reliable Messaging Flow Control is enabled, the WCF Reliable Messaging Source uses the value of `netrm:BufferRemaining` to throttle message transmission.</span></span>  
  
-   <span data-ttu-id="f662f-247">B4005: WCF gera `netrm:BufferRemaining` inteiro entre 0 e 4096 inclusivo de valores e lê os valores de número inteiro entre 0 e `xs:int`do `maxInclusive` valor 214748364 inclusivo.</span><span class="sxs-lookup"><span data-stu-id="f662f-247">B4005: WCF generates `netrm:BufferRemaining` integer values between 0 and 4096 inclusive, and reads integer values between 0 and `xs:int`’s `maxInclusive` value 214748364 inclusive.</span></span>  
  
## <a name="message-exchange-patterns"></a><span data-ttu-id="f662f-248">Padrões de troca de mensagem</span><span class="sxs-lookup"><span data-stu-id="f662f-248">Message Exchange Patterns</span></span>  
 <span data-ttu-id="f662f-249">Esta seção descreve o comportamento do WCF ao WS-ReliableMessaging usada para diferentes padrões de troca de mensagem.</span><span class="sxs-lookup"><span data-stu-id="f662f-249">This section describes WCF's behavior when WS-ReliableMessaging is used for different Message Exchange Patterns.</span></span> <span data-ttu-id="f662f-250">Para cada padrão de troca de mensagens, os seguintes cenários de duas implantações são considerados:</span><span class="sxs-lookup"><span data-stu-id="f662f-250">For each Message Exchange Pattern the following two deployments scenarios are considered:</span></span>  
  
-   <span data-ttu-id="f662f-251">Iniciador não endereçável: Iniciador está atrás de um firewall. Respondente pode entregar mensagens para o iniciador somente em respostas HTTP.</span><span class="sxs-lookup"><span data-stu-id="f662f-251">Non-Addressable Initiator: Initiator is behind a firewall; Responder can deliver messages to the Initiator only on HTTP responses.</span></span>  
  
-   <span data-ttu-id="f662f-252">Iniciador endereçável: Iniciador e Respondente podem ser enviadas solicitações HTTP; em outras palavras, duas conexões de HTTP inverso podem ser estabelecidas.</span><span class="sxs-lookup"><span data-stu-id="f662f-252">Addressable Initiator: Initiator and Responder both can be sent HTTP requests; in other words, two converse HTTP connections can be established.</span></span>  
  
### <a name="one-way-non-addressable-initiator"></a><span data-ttu-id="f662f-253">Iniciador unidirecional, não endereçável</span><span class="sxs-lookup"><span data-stu-id="f662f-253">One-way, Non-addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="f662f-254">Associação</span><span class="sxs-lookup"><span data-stu-id="f662f-254">Binding</span></span>  
 <span data-ttu-id="f662f-255">O WCF fornece um padrão de troca de mensagem unidirecional usando uma sequência por um canal HTTP.</span><span class="sxs-lookup"><span data-stu-id="f662f-255">WCF provides a one-way message exchange pattern using one sequence over one HTTP channel.</span></span> <span data-ttu-id="f662f-256">WCF usa solicitações HTTP para transmitir todas as mensagens do iniciador para as respostas do Respondente e HTTP para transmitir todas as mensagens do Respondente para o iniciador.</span><span class="sxs-lookup"><span data-stu-id="f662f-256">WCF uses HTTP requests to transmit all messages from the Initiator to the Responder and HTTP responses to transmit all messages from the Responder to the Initiator.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="f662f-257">CreateSequence Exchange</span><span class="sxs-lookup"><span data-stu-id="f662f-257">CreateSequence Exchange</span></span>  
 <span data-ttu-id="f662f-258">O iniciador de WCF transmite um `CreateSequence` mensagem sem nenhum `Offer` elemento em uma solicitação HTTP e espera o `CreateSequenceResponse` mensagem na resposta HTTP.</span><span class="sxs-lookup"><span data-stu-id="f662f-258">The WCF Initiator transmits a `CreateSequence` message with no `Offer` element on an HTTP request and expects the `CreateSequenceResponse` message on the HTTP response.</span></span> <span data-ttu-id="f662f-259">Cria uma sequência de Respondente WCF e transmite o `CreateSequenceResponse` mensagem sem nenhum `Accept` elemento na resposta HTTP.</span><span class="sxs-lookup"><span data-stu-id="f662f-259">The WCF Responder creates a sequence and transmits the `CreateSequenceResponse` message with no `Accept` element on the HTTP response.</span></span>  
  
#### <a name="sequenceacknowledgement"></a><span data-ttu-id="f662f-260">SequenceAcknowledgement</span><span class="sxs-lookup"><span data-stu-id="f662f-260">SequenceAcknowledgement</span></span>  
 <span data-ttu-id="f662f-261">O iniciador de WCF processa as confirmações na resposta de todas as mensagens, exceto o `CreateSequence` mensagem e mensagens de falha.</span><span class="sxs-lookup"><span data-stu-id="f662f-261">The WCF Initiator processes acknowledgements on the reply of all messages except the `CreateSequence` message and fault messages.</span></span> <span data-ttu-id="f662f-262">Respondente WCF sempre transmite uma mensagem de confirmação autônoma na resposta HTTP a sequência de todas as e `AckRequested` mensagens.</span><span class="sxs-lookup"><span data-stu-id="f662f-262">The WCF Responder always transmits a stand-alone acknowledgement on the HTTP response to all sequence and `AckRequested` messages.</span></span>  
  
#### <a name="closesequence-exchange"></a><span data-ttu-id="f662f-263">CreateSequence Exchange</span><span class="sxs-lookup"><span data-stu-id="f662f-263">CloseSequence Exchange</span></span>  
 <span data-ttu-id="f662f-264">O iniciador de WCF transmite um `CloseSequence` mensagem em uma solicitação HTTP e espera o `CreateSequenceResponse` mensagem na resposta HTTP.</span><span class="sxs-lookup"><span data-stu-id="f662f-264">The WCF Initiator transmits a `CloseSequence` message on an HTTP request and expects the `CreateSequenceResponse` message on the HTTP response.</span></span> <span data-ttu-id="f662f-265">O WCF Respondente transmite o `CloseSequenceResponse` mensagem na resposta HTTP.</span><span class="sxs-lookup"><span data-stu-id="f662f-265">The WCF Responder transmits the `CloseSequenceResponse` message on the HTTP response.</span></span>  
  
#### <a name="terminatesequence-exchange"></a><span data-ttu-id="f662f-266">TerminateSequence Exchange</span><span class="sxs-lookup"><span data-stu-id="f662f-266">TerminateSequence Exchange</span></span>  
 <span data-ttu-id="f662f-267">O iniciador de WCF transmite um `TerminateSequence` mensagem em uma solicitação HTTP e espera o `TerminateSequenceResponse` mensagem na resposta HTTP.</span><span class="sxs-lookup"><span data-stu-id="f662f-267">The WCF Initiator transmits a `TerminateSequence` message on an HTTP request and expects the `TerminateSequenceResponse` message on the HTTP response.</span></span> <span data-ttu-id="f662f-268">O WCF Respondente transmite o `TerminateSequenceResponse` mensagem na resposta HTTP.</span><span class="sxs-lookup"><span data-stu-id="f662f-268">The WCF Responder transmits the `TerminateSequenceResponse` message on the HTTP response.</span></span>  
  
### <a name="one-way-addressable-initiator"></a><span data-ttu-id="f662f-269">Iniciador de uma maneira, endereçável</span><span class="sxs-lookup"><span data-stu-id="f662f-269">One Way, Addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="f662f-270">Associação</span><span class="sxs-lookup"><span data-stu-id="f662f-270">Binding</span></span>  
 <span data-ttu-id="f662f-271">O WCF fornece um padrão de troca de mensagem unidirecional usando uma sequência sobre uma entrada e um canal HTTP de saída.</span><span class="sxs-lookup"><span data-stu-id="f662f-271">WCF provides a one-way message exchange pattern using one sequence over one inbound and one outbound HTTP channel.</span></span> <span data-ttu-id="f662f-272">WCF usa as solicitações HTTP para transmitir todas as mensagens.</span><span class="sxs-lookup"><span data-stu-id="f662f-272">WCF uses the HTTP requests to transmit all messages.</span></span> <span data-ttu-id="f662f-273">Todas as respostas HTTP tem um corpo vazio e o código de status HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="f662f-273">All HTTP responses have an empty body and HTTP 202 status code.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="f662f-274">CreateSequence Exchange</span><span class="sxs-lookup"><span data-stu-id="f662f-274">CreateSequence Exchange</span></span>  
 <span data-ttu-id="f662f-275">O iniciador de WCF transmite um `CreateSequence` mensagem sem nenhum `Offer` elemento em uma solicitação HTTP.</span><span class="sxs-lookup"><span data-stu-id="f662f-275">The WCF Initiator transmits a `CreateSequence` message with no `Offer` element on an HTTP request.</span></span> <span data-ttu-id="f662f-276">Cria uma sequência de Respondente WCF e transmite o `CreateSequenceResponse` mensagem sem nenhum `Accept` elemento em uma solicitação HTTP.</span><span class="sxs-lookup"><span data-stu-id="f662f-276">The WCF Responder creates a sequence and transmits the `CreateSequenceResponse` message with no `Accept` element on an HTTP request.</span></span>  
  
### <a name="duplex-addressable-initiator"></a><span data-ttu-id="f662f-277">Iniciador de duplex, endereçável</span><span class="sxs-lookup"><span data-stu-id="f662f-277">Duplex, Addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="f662f-278">Associação</span><span class="sxs-lookup"><span data-stu-id="f662f-278">Binding</span></span>  
 <span data-ttu-id="f662f-279">O WCF fornece um padrão de troca de mensagem assíncrono totalmente, bidirecional usando duas sequências sobre uma entrada e um canal HTTP de saída.</span><span class="sxs-lookup"><span data-stu-id="f662f-279">WCF provides a fully-asynchronous, two-way message exchange pattern using two sequences over one inbound and one outbound HTTP channel.</span></span> <span data-ttu-id="f662f-280">Esse padrão de troca de mensagem pode ser combinado com a `Request/Reply`, `Addressable` padrão de troca de mensagem do iniciador de uma maneira limitada.</span><span class="sxs-lookup"><span data-stu-id="f662f-280">This message exchange pattern can be mixed with the `Request/Reply`, `Addressable` Initiator message exchange pattern in a limited way.</span></span> <span data-ttu-id="f662f-281">WCF usa solicitações HTTP para transmitir todas as mensagens.</span><span class="sxs-lookup"><span data-stu-id="f662f-281">WCF uses HTTP requests to transmit all messages.</span></span> <span data-ttu-id="f662f-282">Todas as respostas HTTP tem um corpo vazio e o código de status HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="f662f-282">All HTTP responses have an empty body and HTTP 202 status code.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="f662f-283">CreateSequence Exchange</span><span class="sxs-lookup"><span data-stu-id="f662f-283">CreateSequence Exchange</span></span>  
 <span data-ttu-id="f662f-284">O iniciador de WCF transmite um `CreateSequence` mensagem com um `Offer` elemento em uma solicitação HTTP.</span><span class="sxs-lookup"><span data-stu-id="f662f-284">The WCF Initiator transmits a `CreateSequence` message with an `Offer` element on an HTTP request.</span></span> <span data-ttu-id="f662f-285">O Respondente WCF garante que o `CreateSequence` tem um `Offer` elemento, em seguida, cria uma sequência e transmite o `CreateSequenceResponse` mensagem com um `Accept` elemento.</span><span class="sxs-lookup"><span data-stu-id="f662f-285">The WCF Responder ensures that the `CreateSequence` has an `Offer` element, then creates a sequence and transmits the `CreateSequenceResponse` message with an `Accept` element.</span></span>  
  
#### <a name="sequence-lifetime"></a><span data-ttu-id="f662f-286">Tempo de vida de sequência</span><span class="sxs-lookup"><span data-stu-id="f662f-286">Sequence Lifetime</span></span>  
 <span data-ttu-id="f662f-287">O WCF trata as duas sequências como uma sessão duplex totalmente.</span><span class="sxs-lookup"><span data-stu-id="f662f-287">WCF treats the two sequences as one fully-duplex session.</span></span>  
  
 <span data-ttu-id="f662f-288">Após a geração de uma falha que uma sequência de falhas, o WCF espera o ponto de extremidade remoto para ambas as sequências de falha.</span><span class="sxs-lookup"><span data-stu-id="f662f-288">Upon generating a fault that faults one sequence, WCF expects the remote endpoint to fault both sequences.</span></span> <span data-ttu-id="f662f-289">Após a leitura de uma falha que uma sequência de falhas, WCF falhas de ambas as sequências.</span><span class="sxs-lookup"><span data-stu-id="f662f-289">Upon reading a fault that faults one sequence, WCF faults both sequences.</span></span>  
  
 <span data-ttu-id="f662f-290">O WCF pode fechar sua sequência de saída e continuar a processar mensagens em sua sequência de entrada.</span><span class="sxs-lookup"><span data-stu-id="f662f-290">WCF can close its outbound sequence and continue to process messages on its inbound sequence.</span></span> <span data-ttu-id="f662f-291">Por outro lado, o WCF pode processar o fechamento da sequência de entrada e continuar a enviar mensagens em sua sequência de saída.</span><span class="sxs-lookup"><span data-stu-id="f662f-291">Conversely, WCF can process the close of the inbound sequence and continue to send messages on its outbound sequence.</span></span>  
  
### <a name="request-reply-and-one-way-non-addressable-initiator"></a><span data-ttu-id="f662f-292">Unidirecional, não endereçável iniciador e solicitação-resposta</span><span class="sxs-lookup"><span data-stu-id="f662f-292">Request-Reply and One-Way, Non-Addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="f662f-293">Associação</span><span class="sxs-lookup"><span data-stu-id="f662f-293">Binding</span></span>  
 <span data-ttu-id="f662f-294">O WCF fornece um unidirecional e padrão de troca de mensagem de solicitação-resposta usando duas sequências em um canal HTTP.</span><span class="sxs-lookup"><span data-stu-id="f662f-294">WCF provides a one-way and request-reply message exchange pattern using two sequences over one HTTP channel.</span></span> <span data-ttu-id="f662f-295">WCF usa solicitações HTTP para transmitir todas as mensagens do iniciador para as respostas do Respondente e HTTP para transmitir todas as mensagens do Respondente para o iniciador.</span><span class="sxs-lookup"><span data-stu-id="f662f-295">WCF uses HTTP requests to transmit all messages from the Initiator to the Responder and HTTP responses to transmit all messages from the Responder to the Initiator.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="f662f-296">CreateSequence Exchange</span><span class="sxs-lookup"><span data-stu-id="f662f-296">CreateSequence Exchange</span></span>  
 <span data-ttu-id="f662f-297">Transmite o iniciador de WCF um `CreateSequence` mensagem com um `Offer` elemento em uma solicitação HTTP e espera o `CreateSequenceResponse` mensagem na resposta HTTP.</span><span class="sxs-lookup"><span data-stu-id="f662f-297">The WCF Initiator transmits a `CreateSequence` message with an `Offer` element on an HTTP request and expects the `CreateSequenceResponse` message on the HTTP response.</span></span> <span data-ttu-id="f662f-298">Cria uma sequência de Respondente WCF e transmite o `CreateSequenceResponse` mensagem com um `Accept` elemento na resposta HTTP.</span><span class="sxs-lookup"><span data-stu-id="f662f-298">The WCF Responder creates a sequence and transmits the `CreateSequenceResponse` message with an `Accept` element on the HTTP response.</span></span>  
  
#### <a name="one-way-message"></a><span data-ttu-id="f662f-299">Mensagem unidirecional</span><span class="sxs-lookup"><span data-stu-id="f662f-299">One-way Message</span></span>  
 <span data-ttu-id="f662f-300">Para concluir com êxito uma troca de mensagens unidirecional, o iniciador de WCF transmite uma mensagem de sequência de solicitação na solicitação HTTP e recebe um autônomo `SequenceAcknowledgement` mensagem na resposta HTTP.</span><span class="sxs-lookup"><span data-stu-id="f662f-300">To complete a one-way message exchange successfully, the WCF Initiator transmits a request sequence message on the HTTP request and receives a standalone `SequenceAcknowledgement` message on the HTTP response.</span></span> <span data-ttu-id="f662f-301">O `SequenceAcknowledgement` deve reconhecer a mensagem transmitida.</span><span class="sxs-lookup"><span data-stu-id="f662f-301">The `SequenceAcknowledgement` must acknowledge the message transmitted.</span></span>  
  
 <span data-ttu-id="f662f-302">O Respondente WCF pode responder à solicitação com uma resposta com um corpo vazio e o código de status HTTP 202, uma falha ou uma confirmação.</span><span class="sxs-lookup"><span data-stu-id="f662f-302">The WCF Responder may reply to the request with an acknowledgement, a fault, or a response with an empty body and HTTP 202 status code.</span></span>  
  
#### <a name="two-way-messages"></a><span data-ttu-id="f662f-303">Duas mensagens de maneira</span><span class="sxs-lookup"><span data-stu-id="f662f-303">Two Way Messages</span></span>  
 <span data-ttu-id="f662f-304">Para concluir com êxito um protocolo de intercâmbio de mensagens de duas vias, o iniciador de WCF transmite uma mensagem de sequência de solicitação na solicitação HTTP e recebe uma mensagem de sequência de resposta na resposta HTTP.</span><span class="sxs-lookup"><span data-stu-id="f662f-304">To complete a two way message exchange protocol successfully, the WCF Initiator transmits a request sequence message on the HTTP request and receives a reply sequence message on the HTTP response.</span></span> <span data-ttu-id="f662f-305">A resposta deve conter um `SequenceAcknowledgement` confirmando a mensagem de sequência de solicitação transmitida.</span><span class="sxs-lookup"><span data-stu-id="f662f-305">The response must carry a `SequenceAcknowledgement` acknowledging the request sequence message transmitted.</span></span>  
  
 <span data-ttu-id="f662f-306">O Respondente WCF pode responder à solicitação com uma resposta do aplicativo, uma falha ou uma resposta com um corpo vazio e o código de status HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="f662f-306">The WCF Responder may reply to the request with an application reply, a fault or a response with an empty body and HTTP 202 status code.</span></span>  
  
 <span data-ttu-id="f662f-307">Devido à presença de mensagens unidirecionais e o tempo de respostas de aplicativo, o número de sequência da mensagem de sequência de solicitação e número de sequência da mensagem de resposta não têm nenhuma correlação.</span><span class="sxs-lookup"><span data-stu-id="f662f-307">Because of the presence of one-way messages and the timing of application replies, the request sequence message’s sequence number and the response message’s sequence number have no correlation.</span></span>  
  
#### <a name="retrying-replies"></a><span data-ttu-id="f662f-308">Repetindo as respostas</span><span class="sxs-lookup"><span data-stu-id="f662f-308">Retrying Replies</span></span>  
 <span data-ttu-id="f662f-309">WCF depende de correlação de solicitação-resposta HTTP para correlação de protocolo de troca de mensagens bidirecional.</span><span class="sxs-lookup"><span data-stu-id="f662f-309">WCF relies on HTTP request-reply correlation for two-way message exchange protocol correlation.</span></span> <span data-ttu-id="f662f-310">Por isso, o iniciador do WCF não parar repetindo uma mensagem de sequência de solicitação quando a mensagem de sequência de solicitação é confirmada, mas em vez disso, quando a resposta HTTP executa um `SequenceAcknowledgement`, resposta do aplicativo ou falhas.</span><span class="sxs-lookup"><span data-stu-id="f662f-310">Because of this, the WCF Initiator does not stop retrying a request sequence message when the request sequence message is acknowledged but rather when the HTTP response carries a `SequenceAcknowledgement`, application reply, or fault.</span></span> <span data-ttu-id="f662f-311">O WCF Respondente repete respostas na resposta HTTP da solicitação para o qual a resposta correlacionada.</span><span class="sxs-lookup"><span data-stu-id="f662f-311">The WCF Responder retries replies on the HTTP response of the request to which the reply is correlated.</span></span>  
  
#### <a name="closesequence-exchange"></a><span data-ttu-id="f662f-312">CreateSequence Exchange</span><span class="sxs-lookup"><span data-stu-id="f662f-312">CloseSequence Exchange</span></span>  
 <span data-ttu-id="f662f-313">Depois de receber todas as mensagens de resposta de sequência e confirmações para todas as mensagens de sequência de solicitação unidirecional, o iniciador de WCF transmite um `CloseSequence` de mensagem para a sequência de solicitação em uma solicitação HTTP e espera o `CloseSequenceResponse` na resposta HTTP.</span><span class="sxs-lookup"><span data-stu-id="f662f-313">After receiving all reply sequence messages and acknowledgements for all one way request sequence messages, the WCF Initiator transmits a `CloseSequence` message for the request sequence on an HTTP request and expects the `CloseSequenceResponse` on the HTTP response.</span></span>  
  
 <span data-ttu-id="f662f-314">A sequência de solicitação de fechamento implicitamente fecha a sequência de resposta.</span><span class="sxs-lookup"><span data-stu-id="f662f-314">Closing the request sequence implicitly closes the reply sequence.</span></span> <span data-ttu-id="f662f-315">Isso significa que o iniciador do WCF inclui Final da sequência de resposta `SequenceAcknowledgement` no `CloseSequence` mensagem e a sequência de resposta não tem um `CloseSequence` exchange.</span><span class="sxs-lookup"><span data-stu-id="f662f-315">This means the WCF Initiator includes the reply sequence’s Final `SequenceAcknowledgement` on the `CloseSequence` message and the reply sequence does not have a `CloseSequence` exchange.</span></span>  
  
 <span data-ttu-id="f662f-316">O WCF Respondente garante que todas as respostas são confirmados e transmite o `CloseSequenceResponse` mensagem na resposta HTTP.</span><span class="sxs-lookup"><span data-stu-id="f662f-316">The WCF Responder ensures all replies are acknowledged and transmits the `CloseSequenceResponse` message on the HTTP response.</span></span>  
  
#### <a name="terminatesequence-exchange"></a><span data-ttu-id="f662f-317">TerminateSequence Exchange</span><span class="sxs-lookup"><span data-stu-id="f662f-317">TerminateSequence Exchange</span></span>  
 <span data-ttu-id="f662f-318">Após o recebimento de `CloseSequenceResponse` mensagem, o iniciador de WCF transmite um `TerminateSequence` de mensagem para a sequência de solicitação em uma solicitação HTTP e espera o `TerminateSequenceResponse` na resposta HTTP.</span><span class="sxs-lookup"><span data-stu-id="f662f-318">After receiving the `CloseSequenceResponse` message, the WCF Initiator transmits a `TerminateSequence` message for the request sequence on an HTTP request and expects the `TerminateSequenceResponse` on the HTTP response.</span></span>  
  
 <span data-ttu-id="f662f-319">Como o `CloseSequence` exchange, encerrando a sequência de solicitação implicitamente encerra a sequência de resposta.</span><span class="sxs-lookup"><span data-stu-id="f662f-319">Like the `CloseSequence` exchange, terminating the request sequence implicitly terminates the reply sequence.</span></span> <span data-ttu-id="f662f-320">Isso significa que o iniciador do WCF inclui final da sequência de resposta `SequenceAcknowledgement` no `TerminateSequence` mensagem e a sequência de resposta não tem um `TerminateSequence` exchange.</span><span class="sxs-lookup"><span data-stu-id="f662f-320">This means the WCF Initiator includes the reply sequence’s final `SequenceAcknowledgement` on the `TerminateSequence` message and the reply sequence does not have a `TerminateSequence` exchange.</span></span>  
  
 <span data-ttu-id="f662f-321">O WCF Respondente transmite o `TerminateSequenceResponse` mensagem na resposta HTTP.</span><span class="sxs-lookup"><span data-stu-id="f662f-321">The WCF Responder transmits the `TerminateSequenceResponse` message on the HTTP response.</span></span>  
  
### <a name="requestreply-addressable-initiator"></a><span data-ttu-id="f662f-322">Solicitação/resposta, o iniciador endereçável</span><span class="sxs-lookup"><span data-stu-id="f662f-322">Request/Reply, Addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="f662f-323">Associação</span><span class="sxs-lookup"><span data-stu-id="f662f-323">Binding</span></span>  
 <span data-ttu-id="f662f-324">WCF fornece um padrão de troca de mensagem de solicitação-resposta usando duas sequências sobre uma entrada e um canal HTTP de saída.</span><span class="sxs-lookup"><span data-stu-id="f662f-324">WCF provides a request-reply message exchange pattern using two sequences over one inbound and one outbound HTTP channel.</span></span> <span data-ttu-id="f662f-325">Esse padrão de troca de mensagem pode ser combinado com o `Duplex, Addressable` padrão de troca de mensagem do iniciador de uma maneira limitada.</span><span class="sxs-lookup"><span data-stu-id="f662f-325">This message exchange pattern can be mixed with the `Duplex, Addressable` Initiator message exchange pattern in a limited way.</span></span> <span data-ttu-id="f662f-326">WCF usa as solicitações HTTP para transmitir todas as mensagens.</span><span class="sxs-lookup"><span data-stu-id="f662f-326">WCF uses the HTTP requests to transmit all messages.</span></span> <span data-ttu-id="f662f-327">Todas as respostas HTTP tem um corpo vazio e o código de status HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="f662f-327">All HTTP responses have an empty body and HTTP 202 status code.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="f662f-328">CreateSequence Exchange</span><span class="sxs-lookup"><span data-stu-id="f662f-328">CreateSequence Exchange</span></span>  
 <span data-ttu-id="f662f-329">O iniciador de WCF transmite um `CreateSequence` mensagem com um `Offer` elemento em uma solicitação HTTP.</span><span class="sxs-lookup"><span data-stu-id="f662f-329">The WCF Initiator transmits a `CreateSequence` message with an `Offer` element on an HTTP request.</span></span> <span data-ttu-id="f662f-330">O Respondente WCF garante que o `CreateSequence` tem um `Offer` elemento, em seguida, cria uma sequência e transmite o `CreateSequenceResponse` mensagem com um `Accept` elemento.</span><span class="sxs-lookup"><span data-stu-id="f662f-330">The WCF Responder ensures that the `CreateSequence` has an `Offer` element then creates a sequence and transmits the `CreateSequenceResponse` message with an `Accept` element.</span></span>  
  
#### <a name="requestreply-correlation"></a><span data-ttu-id="f662f-331">Correlação de solicitação/resposta</span><span class="sxs-lookup"><span data-stu-id="f662f-331">Request/Reply Correlation</span></span>  
 <span data-ttu-id="f662f-332">O seguinte se aplica a correlacionado todas as solicitações e respostas:</span><span class="sxs-lookup"><span data-stu-id="f662f-332">The following applies to all correlated requests and replies:</span></span>  
  
-   <span data-ttu-id="f662f-333">WCF garante que todos os lembre de mensagens de solicitação de aplicativo um `ReplyTo` referência de ponto de extremidade e um `MessageId`.</span><span class="sxs-lookup"><span data-stu-id="f662f-333">WCF ensures all application request messages bear a `ReplyTo` endpoint reference and a `MessageId`.</span></span>  
  
-   <span data-ttu-id="f662f-334">WCF aplica-se a referência de ponto de extremidade local como cada mensagem de solicitação de aplicativo `ReplyTo`.</span><span class="sxs-lookup"><span data-stu-id="f662f-334">WCF applies the local endpoint reference as each application request message’s `ReplyTo`.</span></span> <span data-ttu-id="f662f-335">A referência de ponto de extremidade local é o `CreateSequence` da mensagem `ReplyTo` para o iniciador e o `CreateSequence` da mensagem `To` para o respondente.</span><span class="sxs-lookup"><span data-stu-id="f662f-335">The local endpoint reference is the `CreateSequence` message’s `ReplyTo` for the Initiator and the `CreateSequence` message’s `To` for the Responder.</span></span>  
  
-   <span data-ttu-id="f662f-336">WCF garante que mensagens de solicitação de entrada tenha uma `MessageId` e um `ReplyTo`.</span><span class="sxs-lookup"><span data-stu-id="f662f-336">WCF ensures that incoming request messages bear a `MessageId` and a `ReplyTo`.</span></span>  
  
-   <span data-ttu-id="f662f-337">WCF garante o `ReplyTo` URI da referência do ponto de extremidade de todas as mensagens de solicitação de aplicativo corresponde à referência do ponto de extremidade local, conforme definido anteriormente.</span><span class="sxs-lookup"><span data-stu-id="f662f-337">WCF ensures the `ReplyTo` endpoint reference’s URI of all application request messages match the local endpoint reference as defined earlier.</span></span>  
  
-   <span data-ttu-id="f662f-338">WCF garante que todas as respostas assume corretas `RelatesTo` e `To` cabeçalhos a seguir `wsa` regras de correlação de solicitação/resposta.</span><span class="sxs-lookup"><span data-stu-id="f662f-338">WCF ensures that all replies bear the correct `RelatesTo` and `To` headers following `wsa` request/reply correlation rules.</span></span>
