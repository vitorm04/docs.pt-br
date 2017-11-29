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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d204600682ec8acbc229240c4e1bc859d8ea4d21
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="reliable-messaging-protocol-version-10"></a><span data-ttu-id="738eb-102">Protocolo de mensagens confiável versão 1.0</span><span class="sxs-lookup"><span data-stu-id="738eb-102">Reliable Messaging Protocol version 1.0</span></span>
<span data-ttu-id="738eb-103">Este tópico aborda [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] detalhes de implementação para mensagens WS-Reliable de fevereiro de 2005 (versão 1.0) protocolo necessárias para a interoperação usando o transporte HTTP.</span><span class="sxs-lookup"><span data-stu-id="738eb-103">This topic covers [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] implementation details for the WS-Reliable Messaging February 2005 (version 1.0) protocol necessary for interoperation using the HTTP transport.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="738eb-104">segue a especificação de mensagens WS-Reliable com as restrições e esclarecimentos explicados neste tópico.</span><span class="sxs-lookup"><span data-stu-id="738eb-104"> follows the WS-Reliable Messaging specification with the constraints and clarifications explained in this topic.</span></span> <span data-ttu-id="738eb-105">Observe que o protocolo do WS-ReliableMessaging versão 1.0 é implementado começando com o [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)].</span><span class="sxs-lookup"><span data-stu-id="738eb-105">Note that the WS-ReliableMessaging version 1.0 protocol is implemented starting with the [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)].</span></span>  
  
 <span data-ttu-id="738eb-106">As mensagens WS-Reliable de fevereiro de 2005 protocolo é implementado em [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] pelo <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="738eb-106">The WS-Reliable Messaging February 2005 protocol is implemented in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] by the <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>.</span></span>  
  
 <span data-ttu-id="738eb-107">Para sua conveniência, o tópico usa as seguintes funções:</span><span class="sxs-lookup"><span data-stu-id="738eb-107">For convenience, the topic uses the following roles:</span></span>  
  
-   <span data-ttu-id="738eb-108">Iniciador: o cliente que inicia a criação de sequência de mensagem WS-Reliable</span><span class="sxs-lookup"><span data-stu-id="738eb-108">Initiator: the client that initiates WS-Reliable Message sequence creation</span></span>  
  
-   <span data-ttu-id="738eb-109">Respondente: o serviço que recebe solicitações do iniciador</span><span class="sxs-lookup"><span data-stu-id="738eb-109">Responder: the service that receives the initiator's requests</span></span>  
  
 <span data-ttu-id="738eb-110">Este documento usa os namespaces e prefixos na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="738eb-110">This document uses the prefixes and namespaces in the following table.</span></span>  
  
|<span data-ttu-id="738eb-111">Prefixo</span><span class="sxs-lookup"><span data-stu-id="738eb-111">Prefix</span></span>|<span data-ttu-id="738eb-112">Namespace</span><span class="sxs-lookup"><span data-stu-id="738eb-112">Namespace</span></span>|  
|------------|---------------|  
|<span data-ttu-id="738eb-113">WSRM</span><span class="sxs-lookup"><span data-stu-id="738eb-113">wsrm</span></span>|<span data-ttu-id="738eb-114">http://schemas.xmlsoap.org/ws/2005/02/RM</span><span class="sxs-lookup"><span data-stu-id="738eb-114">http://schemas.xmlsoap.org/ws/2005/02/rm</span></span>|  
|<span data-ttu-id="738eb-115">netrm</span><span class="sxs-lookup"><span data-stu-id="738eb-115">netrm</span></span>|<span data-ttu-id="738eb-116">http://schemas.microsoft.com/WS/2006/05/RM</span><span class="sxs-lookup"><span data-stu-id="738eb-116">http://schemas.microsoft.com/ws/2006/05/rm</span></span>|  
|<span data-ttu-id="738eb-117">s</span><span class="sxs-lookup"><span data-stu-id="738eb-117">s</span></span>|<span data-ttu-id="738eb-118">http://www.w3.org/2003/05/SOAP-envelope</span><span class="sxs-lookup"><span data-stu-id="738eb-118">http://www.w3.org/2003/05/soap-envelope</span></span>|  
|<span data-ttu-id="738eb-119">wsa</span><span class="sxs-lookup"><span data-stu-id="738eb-119">wsa</span></span>|<span data-ttu-id="738eb-120">http://schemas.xmlsoap.org/ws/2005/08/Addressing</span><span class="sxs-lookup"><span data-stu-id="738eb-120">http://schemas.xmlsoap.org/ws/2005/08/addressing</span></span>|  
|<span data-ttu-id="738eb-121">wsse</span><span class="sxs-lookup"><span data-stu-id="738eb-121">wsse</span></span>|<span data-ttu-id="738eb-122">http://docs.oasis-open.org/WSS/2004/01/OASIS-200401-wssecurity-secext-1.0.xsd</span><span class="sxs-lookup"><span data-stu-id="738eb-122">http://docs.oasis-open.org/wss/2004/01/oasis-200401-wssecurity-secext-1.0.xsd</span></span>|  
  
## <a name="messaging"></a><span data-ttu-id="738eb-123">Mensagens</span><span class="sxs-lookup"><span data-stu-id="738eb-123">Messaging</span></span>  
  
### <a name="sequence-establishment-messages"></a><span data-ttu-id="738eb-124">Mensagens de estabelecimento de sequência</span><span class="sxs-lookup"><span data-stu-id="738eb-124">Sequence Establishment Messages</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="738eb-125">implementa `CreateSequence` e `CreateSequenceResponse` mensagens para estabelecer uma sequência de mensagens confiável.</span><span class="sxs-lookup"><span data-stu-id="738eb-125"> implements `CreateSequence` and `CreateSequenceResponse` messages to establish a reliable message sequence.</span></span> <span data-ttu-id="738eb-126">As seguintes restrições se aplicam:</span><span class="sxs-lookup"><span data-stu-id="738eb-126">The following constraints apply:</span></span>  
  
-   <span data-ttu-id="738eb-127">B1101: O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] iniciador não gera o elemento Expires opcional no `CreateSequence` mensagem ou, nos casos quando o `CreateSequence` mensagem contém um `Offer` elemento, opcional `Expires` elemento no `Offer` elemento.</span><span class="sxs-lookup"><span data-stu-id="738eb-127">B1101: The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator does not generate the optional Expires element in the `CreateSequence` message or, in the cases when the `CreateSequence` message contains an `Offer` element, the optional `Expires` element in the `Offer` element.</span></span>  
  
-   <span data-ttu-id="738eb-128">B1102: Ao acessar o `CreateSequence` mensagem, o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] `Responder` envia e recebe ambos `Expires` se eles existem, mas não usa os valores de elementos.</span><span class="sxs-lookup"><span data-stu-id="738eb-128">B1102: When accessing the `CreateSequence` message, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]`Responder` sends and receives both `Expires` elements if they exist, but does not use their values.</span></span>  
  
 <span data-ttu-id="738eb-129">Mensagens WS-Reliable apresenta o `Offer` mecanismo para estabelecer os dois conversam correlacionadas sequências que formam uma sessão.</span><span class="sxs-lookup"><span data-stu-id="738eb-129">WS-Reliable Messaging introduces the `Offer` mechanism to establish the two converse correlated sequences that form a session.</span></span>  
  
-   <span data-ttu-id="738eb-130">R1103: Se `CreateSequence` contém um `Offer` elemento, o Respondente confiável de mensagens deve a aceitar a sequência e responder com `CreateSequenceResponse` que contém um `wsrm:Accept` elemento, cria dois correlacionados conversar sequências ou rejeitar o `CreateSequence` solicitação.</span><span class="sxs-lookup"><span data-stu-id="738eb-130">R1103: If `CreateSequence` contains an `Offer` element, the Reliable Messaging Responder must either accept the sequence and respond with `CreateSequenceResponse` that contains a `wsrm:Accept` element, forming two correlated converse sequences or reject the `CreateSequence` request.</span></span>  
  
-   <span data-ttu-id="738eb-131">R1104: `SequenceAcknowledgement` e mensagens de aplicativo que fluem em sequência inverso devem ser enviadas para o `ReplyTo` referência de ponto de extremidade do `CreateSequence`.</span><span class="sxs-lookup"><span data-stu-id="738eb-131">R1104: `SequenceAcknowledgement` and application messages flowing on converse sequence must be sent to the `ReplyTo` endpoint reference of the `CreateSequence`.</span></span>  
  
-   <span data-ttu-id="738eb-132">R1105: `AcksTo` e `ReplyTo` referências de ponto de extremidade no `CreateSequence` devem ter valores de endereço que correspondem a octet-wise.</span><span class="sxs-lookup"><span data-stu-id="738eb-132">R1105: `AcksTo` and `ReplyTo` endpoint references in the `CreateSequence` must have address values that match the octet-wise.</span></span>  
  
     <span data-ttu-id="738eb-133">O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] respondente verifica se a parte do URI do `AcksTo` e `ReplyTo` EPRs são idênticos antes de criar uma sequência.</span><span class="sxs-lookup"><span data-stu-id="738eb-133">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder verifies that the URI portion of the `AcksTo` and `ReplyTo` EPRs are identical before creating a sequence.</span></span>  
  
-   <span data-ttu-id="738eb-134">R1106: `AcksTo` e `ReplyTo` referências de ponto de extremidade no `CreateSequence` devem ter o mesmo conjunto de parâmetros de referência.</span><span class="sxs-lookup"><span data-stu-id="738eb-134">R1106: `AcksTo` and `ReplyTo` Endpoint References in the `CreateSequence` should have the same set of reference parameters.</span></span>  
  
     [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="738eb-135">não impõe mas presume que [parâmetros de referência] de `AcksTo` e `ReplyTo` na `CreateSequence` são idêntico e usa [referência parâmetros] do `ReplyTo` referência de ponto de extremidade para confirmações e mensagens na sequência inverso.</span><span class="sxs-lookup"><span data-stu-id="738eb-135"> does not enforce but assumes that [reference parameters] of `AcksTo` and `ReplyTo` on `CreateSequence` are identical and uses [reference parameters] from `ReplyTo` endpoint reference for acknowledgements and converse sequence messages.</span></span>  
  
-   <span data-ttu-id="738eb-136">R1107: Quando dois conversam sequências estabelecidas usando o `Offer` mecanismo, `SequenceAcknowledgement` e mensagens de aplicativo que fluem em sequências inverso devem ser enviadas para o `ReplyTo` referência de ponto de extremidade do `CreateSequence`.</span><span class="sxs-lookup"><span data-stu-id="738eb-136">R1107: When two converse sequences are established using the `Offer` mechanism, `SequenceAcknowledgement` and application messages flowing on converse sequences must be sent to the `ReplyTo` endpoint reference of the `CreateSequence`.</span></span>  
  
-   <span data-ttu-id="738eb-137">R1108: Quando dois conversam sequências estabelecidas usando o mecanismo de oferta, o `[address]` propriedade do `wsrm:AcksTo` elemento filho de referência de ponto de extremidade do `wsrm:Accept` elemento do `CreateSequenceResponse` devem corresponder byte-wise o URI de destino da `CreateSequence`.</span><span class="sxs-lookup"><span data-stu-id="738eb-137">R1108: When two converse sequences are established using the Offer mechanism, the `[address]` property of the `wsrm:AcksTo` Endpoint Reference child element of the `wsrm:Accept` element of the `CreateSequenceResponse` must match byte-wise the destination URI of the `CreateSequence`.</span></span>  
  
-   <span data-ttu-id="738eb-138">R1109: Quando dois conversam sequências estabelecidas usando o `Offer` mecanismo, as mensagens enviadas pelo iniciador e confirmações para mensagens pelo respondente deve ser enviada para a mesma referência de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="738eb-138">R1109: When two converse sequences are established using the `Offer` mechanism, messages sent by initiator and acknowledgements to messages by responder must be sent to the same Endpoint Reference.</span></span>  
  
     [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="738eb-139">usa mensagens WS-Reliable estabelecer sessões confiáveis entre o iniciador e respondente.</span><span class="sxs-lookup"><span data-stu-id="738eb-139"> uses WS-Reliable Messaging to establish reliable sessions between the Initiator and Responder.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="738eb-140">da implementação de mensagens WS-Reliable fornece a sessão confiável para unidirecional, solicitação-resposta e completo duplex padrões de mensagens.</span><span class="sxs-lookup"><span data-stu-id="738eb-140">'s WS-Reliable Messaging implementation provides reliable session for one-way, request-reply and full duplex messaging patterns.</span></span> <span data-ttu-id="738eb-141">Mensagens WS-Reliable `Offer` mecanismo `CreateSequence` / `CreateSequenceResponse` lhe permite estabelecer duas sequências inverso correlacionados e fornece um protocolo de sessão que é adequado para todos os pontos de extremidade de mensagens.</span><span class="sxs-lookup"><span data-stu-id="738eb-141">The WS-Reliable Messaging `Offer` mechanism on `CreateSequence`/`CreateSequenceResponse` lets you establish two correlated converse sequences, and provides a session protocol that is suitable for all message endpoints.</span></span> <span data-ttu-id="738eb-142">Porque [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] fornece uma garantia de segurança para uma sessão incluindo proteção de ponta a ponta para integridade de sessão, é prático garantir que se destina à mesma parte de mensagens chegam ao mesmo destino.</span><span class="sxs-lookup"><span data-stu-id="738eb-142">Because [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] provides a security guarantee for such a session including end-to-end protection for session integrity, it is practical to ensure messages intended to the same party are arriving at the same destination.</span></span> <span data-ttu-id="738eb-143">Isso também permite que inclua-backup de confirmações de sequência em mensagens de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="738eb-143">This also allows piggy-backing of sequence acknowledgements on application messages.</span></span> <span data-ttu-id="738eb-144">Portanto, R1104, R1105 e R1108 as restrições se aplicam a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="738eb-144">Therefore, constraints R1104, R1105, and R1108 apply to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
 <span data-ttu-id="738eb-145">Um exemplo de um `CreateSequence` mensagem.</span><span class="sxs-lookup"><span data-stu-id="738eb-145">An example of a `CreateSequence` message.</span></span>  
  
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
  
 <span data-ttu-id="738eb-146">Um exemplo de um `CreateSequenceResponse` mensagem.</span><span class="sxs-lookup"><span data-stu-id="738eb-146">An example of a `CreateSequenceResponse` message.</span></span>  
  
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
  
### <a name="sequence"></a><span data-ttu-id="738eb-147">Sequência</span><span class="sxs-lookup"><span data-stu-id="738eb-147">Sequence</span></span>  
 <span data-ttu-id="738eb-148">A seguir está uma lista de restrições que se aplicam a sequências:</span><span class="sxs-lookup"><span data-stu-id="738eb-148">The following is a list of constraints that apply to sequences:</span></span>  
  
-   <span data-ttu-id="738eb-149">B1201:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] gera e acessa os números de sequência não mais que `xs:long`do valor inclusivo máximo, 9223372036854775807.</span><span class="sxs-lookup"><span data-stu-id="738eb-149">B1201:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generates and accesses sequence numbers no higher than `xs:long`’s maximum inclusive value, 9223372036854775807.</span></span>  
  
-   <span data-ttu-id="738eb-150">B1202:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sempre gera uma mensagem de última bodied vazio com o URI da ação de http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage.</span><span class="sxs-lookup"><span data-stu-id="738eb-150">B1202:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] always generates an empty-bodied last message with the action URI of http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage.</span></span>  
  
-   <span data-ttu-id="738eb-151">B1203: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] recebe e envia uma mensagem com um cabeçalho de sequência que contém um `LastMessage` elemento desde que o URI da ação não é http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage.</span><span class="sxs-lookup"><span data-stu-id="738eb-151">B1203: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] receives and delivers a message with a Sequence header that contains a `LastMessage` element as long as the action URI is not http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage.</span></span>  
  
 <span data-ttu-id="738eb-152">Um exemplo de um cabeçalho de sequência.</span><span class="sxs-lookup"><span data-stu-id="738eb-152">An example of a Sequence Header.</span></span>  
  
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
  
### <a name="ackrequested-header"></a><span data-ttu-id="738eb-153">Cabeçalho AckRequested</span><span class="sxs-lookup"><span data-stu-id="738eb-153">AckRequested Header</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="738eb-154">usa `AckRequested` cabeçalho como um mecanismo de keep-alive.</span><span class="sxs-lookup"><span data-stu-id="738eb-154"> uses `AckRequested` Header as a keep-alive mechanism.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="738eb-155">não gera opcional `MessageNumber` elemento.</span><span class="sxs-lookup"><span data-stu-id="738eb-155"> does not generate the optional `MessageNumber` element.</span></span> <span data-ttu-id="738eb-156">Ao receber uma mensagem com um `AckRequested` cabeçalho que contém o `MessageNumber` elemento [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ignora o `MessageNumber` valor do elemento, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="738eb-156">Upon receiving a message with an `AckRequested` header that contains the `MessageNumber` element, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ignores the `MessageNumber` element’s value, as shown in the following example.</span></span>  
  
```xml  
<wsrm:AckRequested>  
  <wsrm:Identifier>  
    urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36  
  </wsrm:Identifier>  
</wsrm:AckRequested>  
```  
  
### <a name="sequenceacknowledgement-header"></a><span data-ttu-id="738eb-157">Cabeçalho SequenceAcknowledgement</span><span class="sxs-lookup"><span data-stu-id="738eb-157">SequenceAcknowledgement Header</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="738eb-158">usa o mecanismo de inclua para confirmações de sequência fornecidas em mensagens WS-Reliable.</span><span class="sxs-lookup"><span data-stu-id="738eb-158"> uses piggy-back mechanism for sequence acknowledgements provided in WS-Reliable Messaging.</span></span>  
  
-   <span data-ttu-id="738eb-159">R1401: Quando dois conversam sequências estabelecidas usando o `Offer` mecanismo, o `SequenceAcknowledgement` cabeçalho pode ser incluído em qualquer mensagem de aplicativo transmitida para o destinatário pretendido.</span><span class="sxs-lookup"><span data-stu-id="738eb-159">R1401: When two converse sequences are established using the `Offer` mechanism, the `SequenceAcknowledgement` header may be included in any application message transmitted to the intended recipient.</span></span>  
  
-   <span data-ttu-id="738eb-160">B1402: Quando [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] deve gerar uma confirmação antes de receber as mensagens de sequência (por exemplo, para satisfazer um `AckRequested` mensagem), [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] gera um `SequenceAcknowledgement` cabeçalho que contém o intervalo de 0-0, conforme mostrado a seguir exemplo.</span><span class="sxs-lookup"><span data-stu-id="738eb-160">B1402: When [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] must generate an acknowledgement prior to receiving any sequence messages (for example, to satisfy an `AckRequested` message), [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generates a `SequenceAcknowledgement` header that contains the range 0-0, as shown in the following example.</span></span>  
  
    ```xml  
    <wsrm:SequenceAcknowledgement>  
      <wsrm:Identifier>  
        urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36  
      </wsrm:Identifier>  
      <wsrm:AcknowledgementRange Upper="0" Lower="0"/>  
    </wsrm:SequenceAcknowledgement>  
    ```  
  
-   <span data-ttu-id="738eb-161">B1403: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] não gera `SequenceAcknowledgement` cabeçalhos que contêm um `Nack` elemento, mas oferece suporte a `Nack` elementos.</span><span class="sxs-lookup"><span data-stu-id="738eb-161">B1403: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] does not generate `SequenceAcknowledgement` headers that contain a `Nack` element but supports `Nack` elements.</span></span>  
  
### <a name="ws-reliablemessaging-faults"></a><span data-ttu-id="738eb-162">Falhas de WS-ReliableMessaging.</span><span class="sxs-lookup"><span data-stu-id="738eb-162">WS-ReliableMessaging Faults</span></span>  
 <span data-ttu-id="738eb-163">A seguir está uma lista de restrições que se aplicam a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] implementação de mensagens WS-Reliable falhas:</span><span class="sxs-lookup"><span data-stu-id="738eb-163">The following is a list of constraints that apply to the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] implementation of WS-Reliable Messaging faults:</span></span>  
  
-   <span data-ttu-id="738eb-164">B1501: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] não gera `MessageNumberRollover` falhas.</span><span class="sxs-lookup"><span data-stu-id="738eb-164">B1501: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] does not generate `MessageNumberRollover` faults.</span></span>  
  
-   <span data-ttu-id="738eb-165">B1502:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ponto de extremidade pode gerar `CreateSequenceRefused` conforme descrito na especificação de falhas.</span><span class="sxs-lookup"><span data-stu-id="738eb-165">B1502:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] endpoint may generate `CreateSequenceRefused` faults as described in the specification.</span></span>  
  
-   <span data-ttu-id="738eb-166">O ponto de extremidade do serviço de B1503:when atingir seu limite de conexão e não pode processar novas conexões, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] gera adicional `CreateSequenceRefused` falha subcódigo, `netrm:ConnectionLimitReached`, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="738eb-166">B1503:When the service endpoint reaches its connection limit and cannot process new connections, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generates an additional `CreateSequenceRefused` fault subcode, `netrm:ConnectionLimitReached`, as shown in the following example.</span></span>  
  
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
  
### <a name="ws-addressing-faults"></a><span data-ttu-id="738eb-167">Falhas de WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="738eb-167">WS-Addressing Faults</span></span>  
 <span data-ttu-id="738eb-168">Como mensagens WS-Reliable usa WS-Addressing, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] mensagens WS-Reliable implementação pode gerar falhas de WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="738eb-168">Because WS-Reliable Messaging uses WS-Addressing, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WS-Reliable Messaging implementation may generate WS-Addressing faults.</span></span> <span data-ttu-id="738eb-169">Este abrange seção WS-Addressing falhas que [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] gera explicitamente na camada de mensagens WS-Reliable:</span><span class="sxs-lookup"><span data-stu-id="738eb-169">This section covers the WS-Addressing faults that [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] explicitly generates at the WS-Reliable Messaging layer:</span></span>  
  
-   <span data-ttu-id="738eb-170">B1601:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] gera a falha de mensagem de cabeçalho de endereçamento necessário quando uma das seguintes opções for verdadeira:</span><span class="sxs-lookup"><span data-stu-id="738eb-170">B1601:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generates the fault Message Addressing Header Required when one of the following is true:</span></span>  
  
    -   <span data-ttu-id="738eb-171">Uma mensagem está falta um `Sequence` cabeçalho e um `Action` cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="738eb-171">A message is missing a `Sequence` header and an `Action` header.</span></span>  
  
    -   <span data-ttu-id="738eb-172">Um `CreateSequence` mensagem está falta um `MessageId` cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="738eb-172">A `CreateSequence` message is missing a `MessageId` header.</span></span>  
  
    -   <span data-ttu-id="738eb-173">Um `CreateSequence` mensagem está falta um `ReplyTo` cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="738eb-173">A `CreateSequence` message is missing a `ReplyTo` header.</span></span>  
  
-   <span data-ttu-id="738eb-174">B1602:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] gera a falha de ação não tem suporte em resposta a uma mensagem que está falta um `Sequence` cabeçalho e tem um `Action` cabeçalho não é reconhecido na especificação de mensagens WS-Reliable.</span><span class="sxs-lookup"><span data-stu-id="738eb-174">B1602:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generates the fault Action Not Supported in reply to a message that is missing a `Sequence` header and has an `Action` header that is not a recognized in the WS-Reliable Messaging specification.</span></span>  
  
-   <span data-ttu-id="738eb-175">B1603:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] gera a falha do ponto de extremidade não está disponível para indicar que o ponto de extremidade não processar a sequência com base na análise do `CreateSequence` cabeçalhos de endereçamento da mensagem.</span><span class="sxs-lookup"><span data-stu-id="738eb-175">B1603:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generates the fault Endpoint Unavailable to indicate that the endpoint does not process the sequence based upon examination of the `CreateSequence` message’s addressing headers.</span></span>  
  
## <a name="protocol-composition"></a><span data-ttu-id="738eb-176">Composição de protocolo</span><span class="sxs-lookup"><span data-stu-id="738eb-176">Protocol Composition</span></span>  
  
### <a name="composition-with-ws-addressing"></a><span data-ttu-id="738eb-177">Composição com WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="738eb-177">Composition with WS-Addressing</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="738eb-178">dá suporte a duas versões do WS-Addressing: 2004 do WS-Addressing/08 [WS-ADDR] e recomendações de 1.0 W3C WS-Addressing [WS-ADDR-CORE] e [WS-ADDR-SOAP].</span><span class="sxs-lookup"><span data-stu-id="738eb-178"> supports two versions of WS-Addressing: WS-Addressing 2004/08 [WS-ADDR] and W3C WS-Addressing 1.0 Recommendations [WS-ADDR-CORE] and [WS-ADDR-SOAP].</span></span>  
  
 <span data-ttu-id="738eb-179">Enquanto as menções de especificação de mensagens WS-Reliable 2004 do WS-Addressing somente/08, não restringe a versão de WS-Addressing a ser usada.</span><span class="sxs-lookup"><span data-stu-id="738eb-179">While the WS-Reliable Messaging specification mentions only WS-Addressing 2004/08, it does not restrict the WS-Addressing version to be used.</span></span> <span data-ttu-id="738eb-180">A seguir está uma lista de restrições que se aplicam a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="738eb-180">The following is a list of constraints that apply to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:</span></span>  
  
-   <span data-ttu-id="738eb-181">R2101: os dois 08/2004 do WS-Addressing e WS-Addressing 1.0 podem ser usado com mensagens WS-Reliable.</span><span class="sxs-lookup"><span data-stu-id="738eb-181">R2101:Both WS-Addressing 2004/08 and WS-Addressing 1.0 can be used with WS-Reliable Messaging.</span></span>  
  
-   <span data-ttu-id="738eb-182">A única versão R2102:A do WS-Addressing deve ser usada ao longo de uma sequência de mensagens WS-Reliable determinada ou um par de sequências inverso correlacionados usando o `wsrm:Offer` mecanismo.</span><span class="sxs-lookup"><span data-stu-id="738eb-182">R2102:A single version of WS-Addressing must be used throughout a given WS-Reliable Messaging sequence or a pair of converse sequences correlated by using the `wsrm:Offer` mechanism.</span></span>  
  
### <a name="composition-with-soap"></a><span data-ttu-id="738eb-183">Composição de SOAP</span><span class="sxs-lookup"><span data-stu-id="738eb-183">Composition with SOAP</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="738eb-184">oferece suporte ao uso de SOAP 1.1 e SOAP 1.2 com mensagens WS-Reliable.</span><span class="sxs-lookup"><span data-stu-id="738eb-184"> supports use of both SOAP 1.1 and SOAP 1.2 with WS-Reliable Messaging.</span></span>  
  
### <a name="composition-with-ws-security-and-ws-secureconversation"></a><span data-ttu-id="738eb-185">Composição com WS-Security e WS-SecureConversation</span><span class="sxs-lookup"><span data-stu-id="738eb-185">Composition with WS-Security and WS-SecureConversation</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="738eb-186">fornece proteção para mensagens WS-Reliable sequências usando segura de transporte (HTTPS), composição com WS-Security e composição com WS-Secure Conversation.</span><span class="sxs-lookup"><span data-stu-id="738eb-186"> provides protection for WS-Reliable Messaging sequences by using secure Transport (HTTPS), composition with WS-Security, and composition with WS-Secure Conversation.</span></span> <span data-ttu-id="738eb-187">A seguir está uma lista de restrições que se aplicam a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="738eb-187">The following is a list of constraints that apply to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:</span></span>  
  
-   <span data-ttu-id="738eb-188">R2301: para proteger a integridade de uma sequência de mensagens WS-Reliable além de integridade e confidencialidade de mensagens individuais, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] requer que o WS-Secure Conversation deve ser usada.</span><span class="sxs-lookup"><span data-stu-id="738eb-188">R2301:To protect the integrity of a WS-Reliable Messaging sequence in addition to the integrity and confidentiality of individual messages, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] requires that WS-Secure Conversation must be used.</span></span>  
  
-   <span data-ttu-id="738eb-189">R2302:AWS-Secure Conversation deve ser estabelecida antes de estabelecer a sequência de mensagens WS-Reliable.</span><span class="sxs-lookup"><span data-stu-id="738eb-189">R2302:AWS-Secure Conversation session must be established prior to establishing WS-Reliable Messaging sequence(s).</span></span>  
  
-   <span data-ttu-id="738eb-190">R2303: Se o tempo de vida de sequência de mensagens WS-Reliable excede o WS-Secure Conversation tempo de vida da sessão, o `SecurityContextToken` estabelecida usando o WS-Secure Conversation deve ser renovado usando a associação de WS-Secure Conversation renovação correspondente.</span><span class="sxs-lookup"><span data-stu-id="738eb-190">R2303: If the WS-Reliable Messaging sequence lifetime exceeds the WS-Secure Conversation session’s lifetime, the `SecurityContextToken` established by using WS-Secure Conversation must be renewed by using the corresponding WS-Secure Conversation Renewal binding.</span></span>  
  
-   <span data-ttu-id="738eb-191">B2304:ws-sequência de mensagens confiável ou um par de sequências inverso correlacionado sempre estão associados a uma única sessão do WS-SecureConversation.</span><span class="sxs-lookup"><span data-stu-id="738eb-191">B2304:WS-Reliable Messaging sequence or a pair of correlated converse sequences are always bound to a single WS-SecureConversation session.</span></span>  
  
     <span data-ttu-id="738eb-192">O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] origem gera o `wsse:SecurityTokenReference` elemento na seção de extensibilidade de elemento do `CreateSequence` mensagem.</span><span class="sxs-lookup"><span data-stu-id="738eb-192">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] source generates the `wsse:SecurityTokenReference` element in the element extensibility section of the `CreateSequence` message.</span></span>  
  
-   <span data-ttu-id="738eb-193">R2305:when composto com WS-Secure Conversation um `CreateSequence` mensagem deve conter o `wsse:SecurityTokenReference` elemento.</span><span class="sxs-lookup"><span data-stu-id="738eb-193">R2305:When composed with WS-Secure Conversation, a `CreateSequence` message must contain the `wsse:SecurityTokenReference` element.</span></span>  
  
## <a name="ws-reliable-messaging-ws-policy-assertion"></a><span data-ttu-id="738eb-194">Declaração de WS-Policy mensagens WS-Reliable</span><span class="sxs-lookup"><span data-stu-id="738eb-194">WS-Reliable Messaging WS-Policy Assertion</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="738eb-195">usa a asserção de WS-Policy mensagens WS-Reliable `wsrm:RMAssertion` para descrever os recursos de pontos de extremidade.</span><span class="sxs-lookup"><span data-stu-id="738eb-195"> uses WS-Reliable Messaging WS-Policy Assertion `wsrm:RMAssertion` to describe endpoints capabilities.</span></span> <span data-ttu-id="738eb-196">A seguir está uma lista de restrições que se aplicam a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="738eb-196">The following is a list of constraints that apply to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:</span></span>  
  
-   <span data-ttu-id="738eb-197">B3001: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] anexa `wsrm:RMAssertion` asserção de WS-Policy para `wsdl:binding` elementos.</span><span class="sxs-lookup"><span data-stu-id="738eb-197">B3001: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] attaches `wsrm:RMAssertion` WS-Policy Assertion to `wsdl:binding` elements.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="738eb-198">dá suporte a ambos os anexos para `wsdl:binding` e `wsdl:port` elementos.</span><span class="sxs-lookup"><span data-stu-id="738eb-198"> supports both attachments to `wsdl:binding` and `wsdl:port` elements.</span></span>  
  
-   <span data-ttu-id="738eb-199">B3002: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] suporta as seguintes propriedades opcionais de mensagens WS-Reliable asserção e fornece controle sobre eles no [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] `ReliableMessagingBindingElement`:</span><span class="sxs-lookup"><span data-stu-id="738eb-199">B3002: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] supports the following optional properties of WS-Reliable Messaging assertion and provides control over them on the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]`ReliableMessagingBindingElement`:</span></span>  
  
    -   `wsrm:InactivityTimeout`  
  
    -   `wsrm:AcknowledgementInterval`  
  
     <span data-ttu-id="738eb-200">Confira o exemplo abaixo.</span><span class="sxs-lookup"><span data-stu-id="738eb-200">The following is an example.</span></span>  
  
    ```xml  
    <wsrm:RMAssertion>  
      <wsrm:InactivityTimeout Milliseconds="600000" />  
      <wsrm:AcknowledgementInterval Milliseconds="200" />  
    </wsrm:RMAssertion>  
    ```  
  
## <a name="flow-control-ws-reliable-messaging-extension"></a><span data-ttu-id="738eb-201">Extensão de controle de fluxo de mensagens WS-Reliable</span><span class="sxs-lookup"><span data-stu-id="738eb-201">Flow Control WS-Reliable Messaging Extension</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="738eb-202">usa mensagens WS-Reliable extensibilidade para fornecer maior controle adicional opcional sobre o fluxo de mensagem de sequência.</span><span class="sxs-lookup"><span data-stu-id="738eb-202"> uses WS-Reliable Messaging extensibility to provide optional additional tighter control over sequence message flow.</span></span>  
  
 <span data-ttu-id="738eb-203">Controle de fluxo é habilitado definindo o `ReliableSessionBindingElement`do `FlowControlEnabled``bool` propriedade `true`.</span><span class="sxs-lookup"><span data-stu-id="738eb-203">Flow control is enabled by setting the `ReliableSessionBindingElement`’s `FlowControlEnabled``bool` property to `true`.</span></span> <span data-ttu-id="738eb-204">A seguir está uma lista de restrições que se aplicam a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="738eb-204">The following is a list of constraints that apply to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:</span></span>  
  
-   <span data-ttu-id="738eb-205">B4001: Controlar quando o fluxo de mensagens confiável estiver habilitada, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] gera um `netrm:BufferRemaining` a extensibilidade do elemento do elemento de `SequenceAcknowledgement` cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="738eb-205">B4001: When Reliable Messaging Flow Control is enabled, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generates a `netrm:BufferRemaining` element in the element extensibility of the `SequenceAcknowledgement` header.</span></span>  
  
-   <span data-ttu-id="738eb-206">B4002: Controlar quando o fluxo de mensagens confiável estiver habilitada, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] não requer um `netrm:BufferRemaining` elemento esteja presente no `SequenceAcknowledgement` cabeçalho, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="738eb-206">B4002: When Reliable Messaging Flow Control is enabled, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] does not require a `netrm:BufferRemaining` element to be present in `SequenceAcknowledgement` header, as shown in the following example.</span></span>  
  
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
  
-   <span data-ttu-id="738eb-207">B4003: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usa `netrm:BufferRemaining` indicar quantas novas mensagens de destino de mensagens confiável pode buffer.</span><span class="sxs-lookup"><span data-stu-id="738eb-207">B4003: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uses `netrm:BufferRemaining` to indicate how many new messages the Reliable Messaging Destination can buffer.</span></span>  
  
-   <span data-ttu-id="738eb-208">B4004: O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço de mensagens confiável limita o número de mensagens transmitidas quando o aplicativo de destino de mensagens confiável não pode receber mensagens rapidamente.</span><span class="sxs-lookup"><span data-stu-id="738eb-208">B4004:The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Reliable Messaging Service throttles the number of messages transmitted when the Reliable Messaging destination application cannot receive messages quickly.</span></span> <span data-ttu-id="738eb-209">As mensagens de buffers do destino de sistema de mensagens confiável e o valor do elemento cair para 0.</span><span class="sxs-lookup"><span data-stu-id="738eb-209">The Reliable Messaging destination buffers messages and the element’s value drops to 0.</span></span>  
  
-   <span data-ttu-id="738eb-210">B4005: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] gera `netrm:BufferRemaining` inteiro entre 0 e 4096 inclusivo de valores e lê os valores de número inteiro entre 0 e `xs:int`do `maxInclusive` valor 214748364 inclusivo.</span><span class="sxs-lookup"><span data-stu-id="738eb-210">B4005: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generates `netrm:BufferRemaining` integer values between 0 and 4096 inclusive, and reads integer values between 0 and `xs:int`’s `maxInclusive` value 214748364 inclusive.</span></span>  
  
## <a name="message-exchange-patterns"></a><span data-ttu-id="738eb-211">Padrões de troca de mensagem</span><span class="sxs-lookup"><span data-stu-id="738eb-211">Message Exchange Patterns</span></span>  
 <span data-ttu-id="738eb-212">Esta seção descreve [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]do comportamento quando mensagens WS-Reliable é usada por diferentes padrões de troca de mensagem.</span><span class="sxs-lookup"><span data-stu-id="738eb-212">This section describes [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]'s behavior when WS-Reliable Messaging is used for different Message Exchange Patterns.</span></span> <span data-ttu-id="738eb-213">Para cada padrão de troca de mensagens, os seguintes cenários de duas implantações são considerados:</span><span class="sxs-lookup"><span data-stu-id="738eb-213">For each Message Exchange Pattern the following two deployments scenarios are considered:</span></span>  
  
-   <span data-ttu-id="738eb-214">Iniciador não endereçável: Iniciador é protegido por firewall. Respondente pode entregar mensagens para o iniciador somente em respostas HTTP.</span><span class="sxs-lookup"><span data-stu-id="738eb-214">Non-Addressable Initiator: Initiator is behind firewall; Responder can deliver messages to Initiator only on HTTP responses.</span></span>  
  
-   <span data-ttu-id="738eb-215">Iniciador endereçável: Iniciador e Respondente podem ser enviadas solicitações HTTP; em outras palavras, duas conexões de HTTP inverso podem ser estabelecidas.</span><span class="sxs-lookup"><span data-stu-id="738eb-215">Addressable Initiator: Initiator and Responder both can be sent HTTP requests; in other words, two converse HTTP connections can be established.</span></span>  
  
### <a name="one-way-non-addressable-initiator"></a><span data-ttu-id="738eb-216">Iniciador unidirecional, não endereçável</span><span class="sxs-lookup"><span data-stu-id="738eb-216">One-way, Non-addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="738eb-217">Associação</span><span class="sxs-lookup"><span data-stu-id="738eb-217">Binding</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="738eb-218">Fornece um padrão de troca de mensagem unidirecional usando uma sequência por um canal HTTP.</span><span class="sxs-lookup"><span data-stu-id="738eb-218"> provides a one-way message exchange pattern using one sequence over one HTTP channel.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="738eb-219">usa as solicitações HTTP para transmitir todas as mensagens do RMS para RMD e a resposta HTTP para transmitir todas as mensagens de RMD com o RMS.</span><span class="sxs-lookup"><span data-stu-id="738eb-219"> uses the HTTP requests to transmit all messages from the RMS to the RMD and the HTTP response to transmit all messages from the RMD to the RMS.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="738eb-220">CreateSequence Exchange</span><span class="sxs-lookup"><span data-stu-id="738eb-220">CreateSequence Exchange</span></span>  
 <span data-ttu-id="738eb-221">O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] iniciador gera um `CreateSequence` mensagem com nenhuma oferta.</span><span class="sxs-lookup"><span data-stu-id="738eb-221">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator generates a `CreateSequence` message with no offer.</span></span> <span data-ttu-id="738eb-222">O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Respondente garante o `CreateSequence` não tem nenhuma oferta antes de criar uma sequência.</span><span class="sxs-lookup"><span data-stu-id="738eb-222">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder ensures the `CreateSequence` has no offer before creating a sequence.</span></span> <span data-ttu-id="738eb-223">O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Respondente responde a `CreateSequence` solicitação com um `CreateSequenceResponse` mensagem.</span><span class="sxs-lookup"><span data-stu-id="738eb-223">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder replies to the `CreateSequence` request with a `CreateSequenceResponse` message.</span></span>  
  
#### <a name="sequenceacknowledgement"></a><span data-ttu-id="738eb-224">SequenceAcknowledgement</span><span class="sxs-lookup"><span data-stu-id="738eb-224">SequenceAcknowledgement</span></span>  
 <span data-ttu-id="738eb-225">O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] iniciador processa as confirmações na resposta de todas as mensagens, exceto o `CreateSequence` mensagem e mensagens de falha.</span><span class="sxs-lookup"><span data-stu-id="738eb-225">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator processes acknowledgements on the reply of all messages except the `CreateSequence` message and fault messages.</span></span> <span data-ttu-id="738eb-226">O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Respondente sempre gera uma mensagem de confirmação autônoma na resposta para ambos os sequência e `AckRequested` mensagens.</span><span class="sxs-lookup"><span data-stu-id="738eb-226">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder always generates a stand-alone acknowledgement in the response to both sequence and `AckRequested` messages.</span></span>  
  
#### <a name="terminatesequence-message"></a><span data-ttu-id="738eb-227">Mensagem TerminateSequence</span><span class="sxs-lookup"><span data-stu-id="738eb-227">TerminateSequence message</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="738eb-228">trata `TerminateSequence` como uma operação unidirecional, que significa que a resposta HTTP tem um corpo vazio e o código de status HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="738eb-228"> treats `TerminateSequence` as a one-way operation, meaning the HTTP response has an empty body and HTTP 202 status code.</span></span>  
  
### <a name="one-way-addressable-initiator"></a><span data-ttu-id="738eb-229">Iniciador de uma maneira, endereçável</span><span class="sxs-lookup"><span data-stu-id="738eb-229">One Way, Addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="738eb-230">Associação</span><span class="sxs-lookup"><span data-stu-id="738eb-230">Binding</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="738eb-231">Fornece um padrão de troca de mensagem unidirecional usando uma sequência em uma entrada e um canal de Http de saída.</span><span class="sxs-lookup"><span data-stu-id="738eb-231"> provides a one-way message exchange pattern using one sequence over an inbound and an outbound Http channel.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="738eb-232">usa as solicitações HTTP para transmitir todas as mensagens.</span><span class="sxs-lookup"><span data-stu-id="738eb-232"> uses the HTTP requests to transmit all messages.</span></span> <span data-ttu-id="738eb-233">Todas as respostas HTTP tem um corpo vazio e o código de status HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="738eb-233">All HTTP responses have an empty body and HTTP 202 status code.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="738eb-234">CreateSequence Exchange</span><span class="sxs-lookup"><span data-stu-id="738eb-234">CreateSequence Exchange</span></span>  
 <span data-ttu-id="738eb-235">O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] iniciador gera um `CreateSequence` mensagem com nenhuma oferta.</span><span class="sxs-lookup"><span data-stu-id="738eb-235">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator generates a `CreateSequence` message with no offer.</span></span> <span data-ttu-id="738eb-236">O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Respondente garante que o `CreateSequence` não tem nenhuma oferta antes de criar uma sequência.</span><span class="sxs-lookup"><span data-stu-id="738eb-236">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder ensures that the `CreateSequence` has no offer before creating a sequence.</span></span> <span data-ttu-id="738eb-237">O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Respondente transmite o `CreateSequenceResponse` mensagem em uma solicitação HTTP tratados com o `ReplyTo` referência de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="738eb-237">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder transmits the `CreateSequenceResponse` message on an HTTP request addressed with the `ReplyTo` endpoint reference.</span></span>  
  
### <a name="duplex-addressable-initiator"></a><span data-ttu-id="738eb-238">Iniciador de duplex, endereçável</span><span class="sxs-lookup"><span data-stu-id="738eb-238">Duplex, Addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="738eb-239">Associação</span><span class="sxs-lookup"><span data-stu-id="738eb-239">Binding</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="738eb-240">Fornece um padrão de troca de mensagens bidirecionais totalmente assíncronos usando duas sequências em uma entrada e um canal de HTTP de saída.</span><span class="sxs-lookup"><span data-stu-id="738eb-240"> provides a fully asynchronous two-way message exchange pattern using two sequences over an inbound and an outbound HTTP channel.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="738eb-241">usa as solicitações HTTP para transmitir todas as mensagens.</span><span class="sxs-lookup"><span data-stu-id="738eb-241"> uses the HTTP requests to transmit all messages.</span></span> <span data-ttu-id="738eb-242">Todas as respostas HTTP tem um corpo vazio e o código de status HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="738eb-242">All HTTP responses have an empty body and HTTP 202 status code.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="738eb-243">CreateSequence Exchange</span><span class="sxs-lookup"><span data-stu-id="738eb-243">CreateSequence Exchange</span></span>  
 <span data-ttu-id="738eb-244">O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] iniciador gera um `CreateSequence` mensagem com uma oferta.</span><span class="sxs-lookup"><span data-stu-id="738eb-244">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator generates a `CreateSequence` message with an offer.</span></span> <span data-ttu-id="738eb-245">O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Respondente garante que o `CreateSequence` tem uma oferta antes de criar uma sequência.</span><span class="sxs-lookup"><span data-stu-id="738eb-245">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder ensures that the `CreateSequence` has an offer before creating a sequence.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="738eb-246">envia o `CreateSequenceResponse` na solicitação HTTP endereçado a `CreateSequence`do `ReplyTo` referência de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="738eb-246"> sends the `CreateSequenceResponse` on the HTTP request addressed to the `CreateSequence`’s `ReplyTo` endpoint reference.</span></span>  
  
#### <a name="sequence-lifetime"></a><span data-ttu-id="738eb-247">Tempo de vida de sequência</span><span class="sxs-lookup"><span data-stu-id="738eb-247">Sequence Lifetime</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="738eb-248">trata as duas sequências como uma sessão duplex totalmente.</span><span class="sxs-lookup"><span data-stu-id="738eb-248"> treats the two sequences as one fully duplex session.</span></span>  
  
 <span data-ttu-id="738eb-249">Após a geração de uma falha que falhas de uma sequência, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] espera que o ponto de extremidade remoto para ambas as sequências de falha.</span><span class="sxs-lookup"><span data-stu-id="738eb-249">Upon generating a fault that faults one sequence, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] expects the remote endpoint to fault both sequences.</span></span> <span data-ttu-id="738eb-250">Após a leitura de uma falha que falhas de uma sequência, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ambas as sequências de falhas.</span><span class="sxs-lookup"><span data-stu-id="738eb-250">Upon reading a fault that faults one sequence, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] faults both sequences.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="738eb-251">Feche a sequência de saída e continuar a processar mensagens em sua sequência de entrada.</span><span class="sxs-lookup"><span data-stu-id="738eb-251"> can close its outbound sequence and continue to process messages on its inbound sequence.</span></span> <span data-ttu-id="738eb-252">Por outro lado, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] pode processar o fechamento da sequência de entrada e continuar a enviar mensagens em sua sequência de saída.</span><span class="sxs-lookup"><span data-stu-id="738eb-252">Conversely, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] can process the close of the inbound sequence and continue to send messages on its outbound sequence.</span></span>  
  
### <a name="request-reply-non-addressable-initiator"></a><span data-ttu-id="738eb-253">Solicitação-resposta, o iniciador não endereçável</span><span class="sxs-lookup"><span data-stu-id="738eb-253">Request-Reply, Non-Addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="738eb-254">Associação</span><span class="sxs-lookup"><span data-stu-id="738eb-254">Binding</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="738eb-255">Fornece um padrão de troca de mensagem unidirecional e de solicitação-resposta usando duas sequências em um canal HTTP.</span><span class="sxs-lookup"><span data-stu-id="738eb-255"> provides a one-way and request-reply message exchange pattern using two sequences over one HTTP channel.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="738eb-256">usa as solicitações HTTP para transmitir mensagens na sequência de solicitação e usa as respostas HTTP para transmitir mensagens da sequência de resposta.</span><span class="sxs-lookup"><span data-stu-id="738eb-256"> uses the HTTP requests to transmit the request sequence’s messages and uses the HTTP responses to transmit the reply sequence’s messages.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="738eb-257">CreateSequence Exchange</span><span class="sxs-lookup"><span data-stu-id="738eb-257">CreateSequence Exchange</span></span>  
 <span data-ttu-id="738eb-258">O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] iniciador gera um `CreateSequence` mensagem com uma oferta.</span><span class="sxs-lookup"><span data-stu-id="738eb-258">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator generates a `CreateSequence` message with an offer.</span></span> <span data-ttu-id="738eb-259">O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Respondente garante que o `CreateSequence` tem uma oferta antes de criar uma sequência.</span><span class="sxs-lookup"><span data-stu-id="738eb-259">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder ensures that the `CreateSequence` has an offer before creating a sequence.</span></span> <span data-ttu-id="738eb-260">O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Respondente responde a `CreateSequence` solicitação com um `CreateSequenceResponse` mensagem.</span><span class="sxs-lookup"><span data-stu-id="738eb-260">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder replies to the `CreateSequence` request with a `CreateSequenceResponse` message.</span></span>  
  
#### <a name="one-way-message"></a><span data-ttu-id="738eb-261">Mensagem unidirecional</span><span class="sxs-lookup"><span data-stu-id="738eb-261">One-way Message</span></span>  
 <span data-ttu-id="738eb-262">Para concluir um protocolo de intercâmbio de mensagens unidirecional com êxito, o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] iniciador transmite uma mensagem de sequência de solicitação na solicitação HTTP e recebe um autônomo `SequenceAcknowledgement` mensagem na resposta HTTP.</span><span class="sxs-lookup"><span data-stu-id="738eb-262">To complete a one-way message exchange protocol successfully, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator transmits a request sequence message on the HTTP request and receives a standalone `SequenceAcknowledgement` message on the HTTP response.</span></span> <span data-ttu-id="738eb-263">O `SequenceAcknowledgement` deve reconhecer a mensagem transmitida.</span><span class="sxs-lookup"><span data-stu-id="738eb-263">The `SequenceAcknowledgement` must acknowledge the message transmitted.</span></span>  
  
 <span data-ttu-id="738eb-264">O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Respondente pode responder à solicitação com uma resposta com um corpo vazio e o código de status HTTP 202, uma falha ou uma confirmação.</span><span class="sxs-lookup"><span data-stu-id="738eb-264">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder can reply to the request with an acknowledgement, a fault, or a response with an empty body and HTTP 202 status code.</span></span>  
  
#### <a name="two-way-messages"></a><span data-ttu-id="738eb-265">Duas mensagens de maneira</span><span class="sxs-lookup"><span data-stu-id="738eb-265">Two Way Messages</span></span>  
 <span data-ttu-id="738eb-266">Para concluir um protocolo de intercâmbio de mensagens de duas vias com êxito, o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] iniciador transmite uma mensagem de sequência de solicitação na solicitação HTTP e recebe uma mensagem de sequência de resposta na resposta HTTP.</span><span class="sxs-lookup"><span data-stu-id="738eb-266">To complete a two way message exchange protocol successfully, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator transmits a request sequence message on the HTTP request and receives a reply sequence message on the HTTP response.</span></span> <span data-ttu-id="738eb-267">A resposta deve conter um `SequenceAcknowledgement` confirmando a mensagem de sequência de solicitação transmitida.</span><span class="sxs-lookup"><span data-stu-id="738eb-267">The response must carry a `SequenceAcknowledgement` acknowledging the request sequence message transmitted.</span></span>  
  
 <span data-ttu-id="738eb-268">O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Respondente pode responder à solicitação com uma resposta do aplicativo, uma falha ou uma resposta com um corpo vazio e o código de status HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="738eb-268">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder can reply to the request with an application reply, a fault or a response with an empty body and HTTP 202 status code.</span></span>  
  
 <span data-ttu-id="738eb-269">Devido à presença de mensagens unidirecionais e o tempo de respostas de aplicativo, o número de sequência da mensagem de sequência de solicitação e número de sequência da mensagem de resposta não têm nenhuma correlação.</span><span class="sxs-lookup"><span data-stu-id="738eb-269">Because of the presence of one-way messages and the timing of application replies, the request sequence message’s sequence number and the response message’s sequence number have no correlation.</span></span>  
  
#### <a name="retrying-replies"></a><span data-ttu-id="738eb-270">Repetindo as respostas</span><span class="sxs-lookup"><span data-stu-id="738eb-270">Retrying Replies</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="738eb-271">depende da correlação de solicitação-resposta HTTP para correlação de protocolo de troca de mensagens bidirecional.</span><span class="sxs-lookup"><span data-stu-id="738eb-271"> relies on HTTP request-reply correlation for two-way message exchange protocol correlation.</span></span> <span data-ttu-id="738eb-272">Por isso, o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] iniciador não parar de tentar novamente uma mensagem de sequência de solicitação quando a mensagem de sequência de solicitação é confirmada, mas em vez disso, quando a resposta HTTP executa uma confirmação, a mensagem de usuário ou a falha.</span><span class="sxs-lookup"><span data-stu-id="738eb-272">Because of this, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator does not stop retrying a request sequence message when the request sequence message is acknowledged but rather when the HTTP response carries an acknowledgement, user message, or fault.</span></span> <span data-ttu-id="738eb-273">O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Respondente repete as respostas no trecho de solicitação HTTP da solicitação para o qual a resposta correlacionada.</span><span class="sxs-lookup"><span data-stu-id="738eb-273">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder retries replies on the HTTP request leg of the request to which the reply is correlated.</span></span>  
  
#### <a name="lastmessage-exchange"></a><span data-ttu-id="738eb-274">Exchange LastMessage</span><span class="sxs-lookup"><span data-stu-id="738eb-274">LastMessage Exchange</span></span>  
 <span data-ttu-id="738eb-275">O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] iniciador gera e transmite uma mensagem de última bodied vazia no trecho de solicitação HTTP.</span><span class="sxs-lookup"><span data-stu-id="738eb-275">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator generates and transmits an empty bodied last message on the HTTP request leg.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="738eb-276">requer uma resposta, mas ignora a mensagem de resposta real.</span><span class="sxs-lookup"><span data-stu-id="738eb-276"> requires a response but ignores the actual response message.</span></span> <span data-ttu-id="738eb-277">O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Respondente respostas para bodied vazio última mensagem a sequência solicitação com bodied vazio última mensagem da sequência de resposta.</span><span class="sxs-lookup"><span data-stu-id="738eb-277">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder replies to the request sequence’s empty-bodied last message with the reply sequence’s empty-bodied last message.</span></span>  
  
 <span data-ttu-id="738eb-278">Se o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Respondente recebe uma mensagem de última em que o URI da ação não é http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] responde com uma mensagem de última.</span><span class="sxs-lookup"><span data-stu-id="738eb-278">If the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder receives a last message in which the action URI is not http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] replies with a last message.</span></span> <span data-ttu-id="738eb-279">No caso de um protocolo de intercâmbio de mensagens bidirecionais, a última mensagem transmite a mensagem de aplicativo. no caso de um protocolo de intercâmbio de mensagens unidirecional, a última mensagem está vazia.</span><span class="sxs-lookup"><span data-stu-id="738eb-279">In the case of a two-way message exchange protocol, the last message carries the application message; in the case of a one-way message exchange protocol, the last message is empty.</span></span>  
  
 <span data-ttu-id="738eb-280">O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Respondente não requer uma confirmação para bodied vazio última mensagem da sequência de resposta.</span><span class="sxs-lookup"><span data-stu-id="738eb-280">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder does not require an acknowledgement for the reply sequence’s empty-bodied last message.</span></span>  
  
#### <a name="terminatesequence-exchange"></a><span data-ttu-id="738eb-281">TerminateSequence Exchange</span><span class="sxs-lookup"><span data-stu-id="738eb-281">TerminateSequence Exchange</span></span>  
 <span data-ttu-id="738eb-282">Quando todas as solicitações recebeu uma resposta válida, o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] iniciador gera e transmite a sequência de solicitação `TerminateSequence` mensagem no trecho de solicitação HTTP.</span><span class="sxs-lookup"><span data-stu-id="738eb-282">When all requests have received a valid reply, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator generates and transmits the request sequence’s `TerminateSequence` message on the HTTP request leg.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="738eb-283">requer uma resposta, mas ignora a mensagem de resposta real.</span><span class="sxs-lookup"><span data-stu-id="738eb-283"> requires a response but ignores the actual response message.</span></span> <span data-ttu-id="738eb-284">O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Respondente respostas para a sequência de solicitação `TerminateSequence` mensagem com a sequência de resposta `TerminateSequence` mensagem.</span><span class="sxs-lookup"><span data-stu-id="738eb-284">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder replies to the request sequence’s `TerminateSequence` message with the reply sequence’s `TerminateSequence` message.</span></span>  
  
 <span data-ttu-id="738eb-285">Em uma sequência de desligamento normal, ambos `TerminateSequence` mensagens carregam uma gama completa `SequenceAcknowledgement`.</span><span class="sxs-lookup"><span data-stu-id="738eb-285">In a normal shutdown sequence, both `TerminateSequence` messages carry a full range `SequenceAcknowledgement`.</span></span>  
  
### <a name="requestreply-addressable-initiator"></a><span data-ttu-id="738eb-286">Solicitação/resposta, o iniciador endereçável</span><span class="sxs-lookup"><span data-stu-id="738eb-286">Request/Reply, Addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="738eb-287">Associação</span><span class="sxs-lookup"><span data-stu-id="738eb-287">Binding</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="738eb-288">Fornece um padrão de troca de mensagem de solicitação-resposta usando duas sequências em uma entrada e um canal de HTTP de saída.</span><span class="sxs-lookup"><span data-stu-id="738eb-288"> provides a request-reply message exchange pattern using two sequences over an inbound and an outbound HTTP channel.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="738eb-289">usa as solicitações HTTP para transmitir todas as mensagens.</span><span class="sxs-lookup"><span data-stu-id="738eb-289"> uses the HTTP requests to transmit all messages.</span></span> <span data-ttu-id="738eb-290">Todas as respostas HTTP tem um corpo vazio e o código de status HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="738eb-290">All HTTP responses have an empty body and HTTP 202 status code.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="738eb-291">CreateSequence Exchange</span><span class="sxs-lookup"><span data-stu-id="738eb-291">CreateSequence Exchange</span></span>  
 <span data-ttu-id="738eb-292">O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] iniciador gera um `CreateSequence` mensagem com uma oferta.</span><span class="sxs-lookup"><span data-stu-id="738eb-292">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator generates a `CreateSequence` message with an offer.</span></span> <span data-ttu-id="738eb-293">O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Respondente garante que o `CreateSequence` tem uma oferta antes de criar uma sequência.</span><span class="sxs-lookup"><span data-stu-id="738eb-293">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder ensures that the `CreateSequence` has an offer before creating a sequence.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="738eb-294">envia o `CreateSequenceResponse` na solicitação HTTP endereçado a `CreateSequence`do `ReplyTo` referência de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="738eb-294"> sends the `CreateSequenceResponse` on the HTTP request addressed to the `CreateSequence`’s `ReplyTo` endpoint reference.</span></span>  
  
#### <a name="requestreply-correlation"></a><span data-ttu-id="738eb-295">Correlação de solicitação/resposta</span><span class="sxs-lookup"><span data-stu-id="738eb-295">Request/Reply Correlation</span></span>  
 <span data-ttu-id="738eb-296">O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] iniciador garante que todos os lembre de mensagens de solicitação de aplicativo um `MessageId` e um `ReplyTo` referência de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="738eb-296">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator ensures all application request messages bear a `MessageId` and a `ReplyTo` endpoint reference.</span></span> <span data-ttu-id="738eb-297">O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] iniciador se aplica a `CreateSequence` da mensagem `ReplyTo` referência de ponto de extremidade em cada mensagem de solicitação do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="738eb-297">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator applies the `CreateSequence` message’s `ReplyTo` endpoint reference on each application request message.</span></span> <span data-ttu-id="738eb-298">O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Respondente requer mensagens de solicitação de entrada tenha uma `MessageId` e um `ReplyTo`.</span><span class="sxs-lookup"><span data-stu-id="738eb-298">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder requires that incoming request messages bear a `MessageId` and a `ReplyTo`.</span></span> <span data-ttu-id="738eb-299">O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Respondente garante que o URI da referência de ponto de extremidade de ambos os `CreateSequence` e todas as mensagens de solicitação de aplicativo são idênticas.</span><span class="sxs-lookup"><span data-stu-id="738eb-299">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder ensures that the endpoint reference’s URI of both the `CreateSequence` and all application request messages are identical.</span></span>
