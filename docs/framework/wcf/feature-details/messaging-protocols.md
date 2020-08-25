---
title: Protocolos de mensagens
ms.date: 03/30/2017
ms.assetid: 5b20bca7-87b3-4c8f-811b-f215b5987104
ms.openlocfilehash: 69a92bfb406e2e1af3bdcbb0316711dbf531204b
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88812049"
---
# <a name="messaging-protocols"></a><span data-ttu-id="79be0-102">Protocolos de mensagens</span><span class="sxs-lookup"><span data-stu-id="79be0-102">Messaging Protocols</span></span>

<span data-ttu-id="79be0-103">A pilha de canais do Windows Communication Foundation (WCF) emprega canais de codificação e transporte para transformar a representação de mensagem interna em seu formato de conexão e enviá-la usando um transporte específico.</span><span class="sxs-lookup"><span data-stu-id="79be0-103">The Windows Communication Foundation (WCF) channel stack employs encoding and transport channels to transform internal message representation into its wire format and send it by using a particular transport.</span></span> <span data-ttu-id="79be0-104">O transporte mais comum usado para a interoperabilidade de serviços Web é HTTP, e as codificações mais comuns usadas pelos serviços Web são SOAP 1,1 baseado em XML, SOAP 1,2 e MTOM (mecanismo de otimização de transmissão de mensagens).</span><span class="sxs-lookup"><span data-stu-id="79be0-104">The most common transport used for Web services interoperability is HTTP, and the most common encodings used by Web services are XML-based SOAP 1.1, SOAP 1.2, and Message Transmission Optimization Mechanism (MTOM).</span></span>

<span data-ttu-id="79be0-105">Este tópico aborda os detalhes de implementação do WCF para os seguintes protocolos empregados pelo <xref:System.ServiceModel.Channels.HttpTransportBindingElement> .</span><span class="sxs-lookup"><span data-stu-id="79be0-105">This topic covers WCF implementation details for the following protocols employed by <xref:System.ServiceModel.Channels.HttpTransportBindingElement>.</span></span>

<span data-ttu-id="79be0-106">Especificação/documento:</span><span class="sxs-lookup"><span data-stu-id="79be0-106">Specification/document:</span></span>

- [<span data-ttu-id="79be0-107">HTTP 1.1</span><span class="sxs-lookup"><span data-stu-id="79be0-107">HTTP 1.1</span></span>](https://www.ietf.org/rfc/rfc2616.txt)
- <span data-ttu-id="79be0-108">[Associação HTTP SOAP 1,1](https://www.w3.org/TR/2000/NOTE-SOAP-20000508), seção 7</span><span class="sxs-lookup"><span data-stu-id="79be0-108">[SOAP 1.1 HTTP Binding](https://www.w3.org/TR/2000/NOTE-SOAP-20000508), Section 7</span></span>
- <span data-ttu-id="79be0-109">[Associação HTTP SOAP 1,2](https://www.w3.org/TR/soap12-part2) Seção 7</span><span class="sxs-lookup"><span data-stu-id="79be0-109">[SOAP 1.2 HTTP Binding](https://www.w3.org/TR/soap12-part2) Section 7</span></span>

<span data-ttu-id="79be0-110">Este tópico aborda os detalhes de implementação do WCF para os seguintes protocolos que <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> e <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> empregam.</span><span class="sxs-lookup"><span data-stu-id="79be0-110">This topic covers WCF implementation details for the following protocols  that <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> and <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> employ.</span></span>

<span data-ttu-id="79be0-111">Especificação/documento:</span><span class="sxs-lookup"><span data-stu-id="79be0-111">Specification/Document:</span></span>

- [<span data-ttu-id="79be0-112">XML</span><span class="sxs-lookup"><span data-stu-id="79be0-112">XML</span></span>](https://www.w3.org/TR/REC-xml)
- [<span data-ttu-id="79be0-113">SOAP 1,1</span><span class="sxs-lookup"><span data-stu-id="79be0-113">SOAP 1.1</span></span>](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/)
- [<span data-ttu-id="79be0-114">Núcleo SOAP 1,2</span><span class="sxs-lookup"><span data-stu-id="79be0-114">SOAP 1.2 Core</span></span>](https://www.w3.org/TR/soap12-part1/)
- [<span data-ttu-id="79be0-115">WS-Addressing 2004/08</span><span class="sxs-lookup"><span data-stu-id="79be0-115">WS-Addressing 2004/08</span></span>](https://www.w3.org/Submission/2004/SUBM-ws-addressing-20040810/)
- [<span data-ttu-id="79be0-116">Endereçamento de serviços da Web do W3C 1,0-Core</span><span class="sxs-lookup"><span data-stu-id="79be0-116">W3C Web Services Addressing 1.0 - Core</span></span>](https://www.w3.org/TR/2006/REC-ws-addr-core-20060509)
- [<span data-ttu-id="79be0-117">Endereçamento de serviços Web W3C 1,0-Associação SOAP</span><span class="sxs-lookup"><span data-stu-id="79be0-117">W3C Web Services Addressing 1.0 - SOAP Binding</span></span>](https://www.w3.org/TR/2006/REC-ws-addr-soap-20060509)
- [<span data-ttu-id="79be0-118">Endereçamento de serviços Web W3C 1,0-Associação de WSDL</span><span class="sxs-lookup"><span data-stu-id="79be0-118">W3C Web Services Addressing 1.0 - WSDL Binding</span></span>](https://www.w3.org/TR/2006/CR-ws-addr-wsdl-20060529/)
- [<span data-ttu-id="79be0-119">Endereçamento de serviços Web W3C 1,0-metadados</span><span class="sxs-lookup"><span data-stu-id="79be0-119">W3C Web Services Addressing 1.0 - Metadata</span></span>](https://www.w3.org/TR/ws-addr-metadata/)
- [<span data-ttu-id="79be0-120">Associação WSDL SOAP 1.1</span><span class="sxs-lookup"><span data-stu-id="79be0-120">WSDL SOAP1.1 Binding</span></span>](https://www.w3.org/TR/wsdl/)
- [<span data-ttu-id="79be0-121">Associação WSDL de SOAP 1.2</span><span class="sxs-lookup"><span data-stu-id="79be0-121">WSDL SOAP1.2 Binding</span></span>](https://www.w3.org/Submission/wsdl11soap12/)

<span data-ttu-id="79be0-122">Este tópico aborda os detalhes de implementação do WCF para os seguintes protocolos que o <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> emprega.</span><span class="sxs-lookup"><span data-stu-id="79be0-122">This topic covers WCF implementation details for the following protocols that <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> employs.</span></span>

<span data-ttu-id="79be0-123">Especificação/documento:</span><span class="sxs-lookup"><span data-stu-id="79be0-123">Specification/document:</span></span>

- [<span data-ttu-id="79be0-124">XOP</span><span class="sxs-lookup"><span data-stu-id="79be0-124">XOP</span></span>](https://www.w3.org/TR/xop10/)
- [<span data-ttu-id="79be0-125">Associação de MTOM + SOAP 1,2</span><span class="sxs-lookup"><span data-stu-id="79be0-125">MTOM + SOAP 1.2 Binding</span></span>](https://www.w3.org/TR/soap12-mtom/)
- [<span data-ttu-id="79be0-126">Associação de SOAP 1,1 de MTOM</span><span class="sxs-lookup"><span data-stu-id="79be0-126">MTOM SOAP 1.1 Binding</span></span>](https://www.w3.org/Submission/soap11mtom10/)
- [<span data-ttu-id="79be0-127">Declaração WS-Policy de MTOM</span><span class="sxs-lookup"><span data-stu-id="79be0-127">MTOM WS-Policy Assertion</span></span>](https://www.w3.org/Submission/2006/SUBM-WS-MTOMPolicy-20061101/)

<span data-ttu-id="79be0-128">Os namespaces XML e os prefixos associados a seguir são usados em todo este tópico:</span><span class="sxs-lookup"><span data-stu-id="79be0-128">The following XML namespaces and associated prefixes are used throughout this topic:</span></span>

| <span data-ttu-id="79be0-129">Prefixo</span><span class="sxs-lookup"><span data-stu-id="79be0-129">Prefix</span></span> | <span data-ttu-id="79be0-130">Uniform Resource Identifier de namespace (URI)</span><span class="sxs-lookup"><span data-stu-id="79be0-130">Namespace Uniform Resource Identifier (URI)</span></span> |
|------------|---------------------------------------------------|
| <span data-ttu-id="79be0-131">S11</span><span class="sxs-lookup"><span data-stu-id="79be0-131">s11</span></span> | `http://schemas.xmlsoap.org/soap/envelope` |
| <span data-ttu-id="79be0-132">S12</span><span class="sxs-lookup"><span data-stu-id="79be0-132">s12</span></span> |`http://www.w3.org/2003/05/soap-envelope` |
| <span data-ttu-id="79be0-133">WSA</span><span class="sxs-lookup"><span data-stu-id="79be0-133">wsa</span></span> |`http://www.w3.org/2004/08/addressing` |
| <span data-ttu-id="79be0-134">wsam</span><span class="sxs-lookup"><span data-stu-id="79be0-134">wsam</span></span> |`http://www.w3.org/2007/05/addressing/metadata` |
| <span data-ttu-id="79be0-135">wsap</span><span class="sxs-lookup"><span data-stu-id="79be0-135">wsap</span></span> |`http://schemas.xmlsoap.org/ws/2004/09/policy/addressing` |
| <span data-ttu-id="79be0-136">wsa10</span><span class="sxs-lookup"><span data-stu-id="79be0-136">wsa10</span></span> |`http://www.w3.org/2005/08/addressing` |
| <span data-ttu-id="79be0-137">wsaw10</span><span class="sxs-lookup"><span data-stu-id="79be0-137">wsaw10</span></span> |`http://www.w3.org/2006/05/addressing/wsdl` |
| <span data-ttu-id="79be0-138">XOP</span><span class="sxs-lookup"><span data-stu-id="79be0-138">xop</span></span> |`http://www.w3.org/2004/08/xop/include` |
| <span data-ttu-id="79be0-139">xmime</span><span class="sxs-lookup"><span data-stu-id="79be0-139">xmime</span></span> |`http://www.w3.org/2004/06/xmlmime`<br /><br /> `http://www.w3.org/2005/05/xmlmime` |
| <span data-ttu-id="79be0-140">DP</span><span class="sxs-lookup"><span data-stu-id="79be0-140">dp</span></span> |`http://schemas.microsoft.com/net/2006/06/duplex` |

## <a name="soap-11-and-soap-12"></a><span data-ttu-id="79be0-141">SOAP 1,1 e SOAP 1,2</span><span class="sxs-lookup"><span data-stu-id="79be0-141">SOAP 1.1 and SOAP 1.2</span></span>

### <a name="envelope-and-processing-model"></a><span data-ttu-id="79be0-142">Modelo de envelope e processamento</span><span class="sxs-lookup"><span data-stu-id="79be0-142">Envelope and Processing Model</span></span>
<span data-ttu-id="79be0-143">O WCF implementa o processamento de envelope SOAP 1,1 seguindo o perfil básico 1,1 (BP11) e o perfil básico 1,0 (SSBP10).</span><span class="sxs-lookup"><span data-stu-id="79be0-143">WCF implements SOAP 1.1 envelope processing following Basic Profile 1.1 (BP11) and Basic Profile 1.0 (SSBP10).</span></span> <span data-ttu-id="79be0-144">O processamento de envelope SOAP 1,2 é implementado após SOAP12-part1.</span><span class="sxs-lookup"><span data-stu-id="79be0-144">SOAP 1.2 Envelope processing is implemented following SOAP12-Part1.</span></span>

<span data-ttu-id="79be0-145">Esta seção explica algumas opções de implementação feitas pelo WCF em relação a BP11 e SOAP12-part1.</span><span class="sxs-lookup"><span data-stu-id="79be0-145">This section explains certain implementation choices taken by WCF with regard to BP11 and SOAP12-Part1.</span></span>

#### <a name="mandatory-header-processing"></a><span data-ttu-id="79be0-146">Processamento de cabeçalho obrigatório</span><span class="sxs-lookup"><span data-stu-id="79be0-146">Mandatory Header Processing</span></span>
<span data-ttu-id="79be0-147">O WCF segue as regras para o processamento de cabeçalhos marcados como `mustUnderstand` descrito nas especificações soap 1,1 e soap 1,2, com as seguintes variações.</span><span class="sxs-lookup"><span data-stu-id="79be0-147">WCF follows rules for processing headers marked `mustUnderstand` described in the SOAP 1.1 and SOAP 1.2 specifications, with the following variations.</span></span>

<span data-ttu-id="79be0-148">Uma mensagem que entra na pilha de canais do WCF é processada por canais individuais configurados por elementos de associação associados, por exemplo, codificação de mensagem de texto, segurança, mensagens confiáveis e transações.</span><span class="sxs-lookup"><span data-stu-id="79be0-148">A message that enters the WCF channel stack is processed by individual channels configured by associated binding elements, for example, Text Message Encoding, Security, Reliable Messaging, and Transactions.</span></span> <span data-ttu-id="79be0-149">Cada canal reconhece cabeçalhos do namespace associado e os marca como entendi.</span><span class="sxs-lookup"><span data-stu-id="79be0-149">Each channel recognizes headers from the associated namespace and marks them as understood.</span></span> <span data-ttu-id="79be0-150">Quando uma mensagem entra no Dispatcher, o formatador de operação lê os cabeçalhos esperados pelo contrato de mensagem/operação correspondente e os marca como entendi.</span><span class="sxs-lookup"><span data-stu-id="79be0-150">Once a message enters the dispatcher, the operation formatter reads headers expected by the corresponding message/operation contract and marks them understood.</span></span> <span data-ttu-id="79be0-151">Em seguida, o Dispatcher verifica se os cabeçalhos restantes não são compreendidos, mas marcados como `mustUnderstand` e gera uma exceção.</span><span class="sxs-lookup"><span data-stu-id="79be0-151">Then the dispatcher verifies whether any remaining headers are not understood but marked as `mustUnderstand` and throws an exception.</span></span> <span data-ttu-id="79be0-152">As mensagens que contêm `mustUnderstand` cabeçalhos que são direcionados ao destinatário não são processadas pelo código do aplicativo de destinatário.</span><span class="sxs-lookup"><span data-stu-id="79be0-152">Messages that contain `mustUnderstand` headers that are targeted at the recipient are not processed by recipient application code.</span></span>

<span data-ttu-id="79be0-153">Esse processamento em camadas permite a separação entre camadas de infraestrutura e camadas de aplicativo do nó SOAP:</span><span class="sxs-lookup"><span data-stu-id="79be0-153">Such layered processing allows for separation between infrastructure layers and application layers of the SOAP node:</span></span>

- <span data-ttu-id="79be0-154">B1111: cabeçalhos que não são compreendidos são detectados depois que a mensagem é processada pela pilha de canais da infraestrutura do WCF, mas antes de ser processada pelo aplicativo</span><span class="sxs-lookup"><span data-stu-id="79be0-154">B1111: Headers that are not understood are detected after the message is processed by the WCF infrastructure channel stack, but before it is processed by application</span></span>

     <span data-ttu-id="79be0-155">O `mustUnderstand` valor do cabeçalho difere entre soap 1,1 e soap 1,2.</span><span class="sxs-lookup"><span data-stu-id="79be0-155">The `mustUnderstand` header value differs between SOAP 1.1 and SOAP 1.2.</span></span> <span data-ttu-id="79be0-156">O perfil básico 1,1 requer que o `mustUnderstand` valor seja 0 ou 1 para mensagens SOAP 1,1.</span><span class="sxs-lookup"><span data-stu-id="79be0-156">Basic Profile 1.1 requires that the `mustUnderstand` value be 0 or 1 for SOAP 1.1 messages.</span></span> <span data-ttu-id="79be0-157">O SOAP 1,2 permite 0, 1, `false` e `true` como valores, mas recomenda emitir uma representação canônica de `xs:boolean` valores ( `false` , `true` ).</span><span class="sxs-lookup"><span data-stu-id="79be0-157">SOAP 1.2 allows 0, 1, `false`, and `true` as values, but recommends emitting a canonical representation of `xs:boolean` values (`false`, `true`).</span></span>

- <span data-ttu-id="79be0-158">B1112: o WCF emite `mustUnderstand` os valores 0 e 1 para as versões soap 1,1 e soap 1,2 do envelope SOAP.</span><span class="sxs-lookup"><span data-stu-id="79be0-158">B1112: WCF emits `mustUnderstand` values 0 and 1 for both SOAP 1.1 and SOAP 1.2 versions of the SOAP envelope.</span></span> <span data-ttu-id="79be0-159">O WCF aceita todo o espaço de valor de `xs:boolean` para o `mustUnderstand` cabeçalho (0, 1, `false` , `true` )</span><span class="sxs-lookup"><span data-stu-id="79be0-159">WCF accepts the entire value space of `xs:boolean` for the `mustUnderstand` header (0, 1, `false`, `true`)</span></span>

#### <a name="soap-faults"></a><span data-ttu-id="79be0-160">Falhas de SOAP</span><span class="sxs-lookup"><span data-stu-id="79be0-160">SOAP Faults</span></span>
<span data-ttu-id="79be0-161">Veja a seguir uma lista de implementações de falhas SOAP específicas do WCF.</span><span class="sxs-lookup"><span data-stu-id="79be0-161">The following is a list of WCF-specific SOAP fault implementations.</span></span>

- <span data-ttu-id="79be0-162">B2121: o WCF retorna os seguintes códigos de falha SOAP 1,1: `s11:mustUnderstand` , `s11:Client` e `s11:Server` .</span><span class="sxs-lookup"><span data-stu-id="79be0-162">B2121: WCF returns the following SOAP 1.1 Fault Codes: `s11:mustUnderstand`, `s11:Client`, and `s11:Server`.</span></span>

- <span data-ttu-id="79be0-163">B2122: o WCF retorna os seguintes códigos de falha SOAP 1,2: `s12:MustUnderstand` , `s12:Sender` e `s12:Receiver` .</span><span class="sxs-lookup"><span data-stu-id="79be0-163">B2122: WCF returns the following SOAP 1.2 Fault Codes: `s12:MustUnderstand`, `s12:Sender`, and `s12:Receiver`.</span></span>

### <a name="http-binding"></a><span data-ttu-id="79be0-164">Associação HTTP</span><span class="sxs-lookup"><span data-stu-id="79be0-164">HTTP Binding</span></span>

#### <a name="soap-11-http-binding"></a><span data-ttu-id="79be0-165">Associação HTTP SOAP 1,1</span><span class="sxs-lookup"><span data-stu-id="79be0-165">SOAP 1.1 HTTP Binding</span></span>
<span data-ttu-id="79be0-166">O WCF implementa a associação HTTP SOAP 1.1 seguindo a seção de especificação Basic Profile 1,1 3,4 com os seguintes esclarecimentos:</span><span class="sxs-lookup"><span data-stu-id="79be0-166">WCF implements SOAP1.1 HTTP binding following the Basic Profile 1.1 specification section 3.4 with the following clarifications:</span></span>

- <span data-ttu-id="79be0-167">B2211: o serviço WCF não implementa o redirecionamento de solicitações HTTP POST.</span><span class="sxs-lookup"><span data-stu-id="79be0-167">B2211: WCF service does not implement redirection of HTTP POST requests.</span></span>

- <span data-ttu-id="79be0-168">B2212: os clientes WCF dão suporte a cookies HTTP de acordo com o 3.4.8.</span><span class="sxs-lookup"><span data-stu-id="79be0-168">B2212: WCF clients support HTTP Cookies in accordance with 3.4.8.</span></span>

#### <a name="soap-12-http-binding"></a><span data-ttu-id="79be0-169">Associação HTTP SOAP 1,2</span><span class="sxs-lookup"><span data-stu-id="79be0-169">SOAP 1.2 HTTP Binding</span></span>
<span data-ttu-id="79be0-170">O WCF implementa a associação HTTP SOAP 1,2, conforme descrito na especificação SOAP 1,2-parte 2 (SOAP12Part2) com os seguintes esclarecimentos.</span><span class="sxs-lookup"><span data-stu-id="79be0-170">WCF implements SOAP 1.2 HTTP binding as described in the SOAP 1.2-part 2 (SOAP12Part2) specification with the following clarifications.</span></span>

<span data-ttu-id="79be0-171">O SOAP 1,2 introduziu um parâmetro de ação opcional para o `application/soap+xml` tipo de mídia.</span><span class="sxs-lookup"><span data-stu-id="79be0-171">SOAP 1.2 introduced an optional action parameter for the `application/soap+xml` media type.</span></span> <span data-ttu-id="79be0-172">Esse parâmetro é útil para otimizar a expedição de mensagens sem a necessidade de que o corpo da mensagem SOAP seja analisado quando o WS-Addressing não for usado.</span><span class="sxs-lookup"><span data-stu-id="79be0-172">This parameter is useful to optimize message dispatch without requiring that the body of the SOAP message be parsed when WS-Addressing is not used.</span></span>

- <span data-ttu-id="79be0-173">R2221: o `application/soap+xml` parâmetro Action, quando presente em uma solicitação SOAP 1,2, deve corresponder ao `soapAction` atributo no `wsoap12:operation` elemento dentro da Associação WSDL correspondente.</span><span class="sxs-lookup"><span data-stu-id="79be0-173">R2221: The `application/soap+xml` action parameter, when present on a SOAP 1.2 request, must match the `soapAction` attribute on the `wsoap12:operation` element inside the corresponding WSDL binding.</span></span>

- <span data-ttu-id="79be0-174">R2222: o `application/soap+xml` parâmetro Action, quando presente em uma mensagem SOAP 1,2, deve corresponder `wsa:Action` quando WS-addressing 2004/08 ou WS-addressing 1,0 forem usados.</span><span class="sxs-lookup"><span data-stu-id="79be0-174">R2222: The `application/soap+xml` action parameter, when present on a SOAP 1.2 message, must match `wsa:Action` when WS-Addressing 2004/08 or WS-Addressing 1.0 are used.</span></span>

<span data-ttu-id="79be0-175">Quando o WS-Addressing estiver desabilitado e uma solicitação de entrada não contiver um parâmetro de ação, a mensagem `Action` será considerada não especificada.</span><span class="sxs-lookup"><span data-stu-id="79be0-175">When WS-Addressing is disabled and an incoming request does not contain an action parameter, message `Action` is considered not specified.</span></span>

## <a name="ws-addressing"></a><span data-ttu-id="79be0-176">WS-Addressing</span><span class="sxs-lookup"><span data-stu-id="79be0-176">WS-Addressing</span></span>
<span data-ttu-id="79be0-177">O WCF implementa 3 versões do WS-Addressing:</span><span class="sxs-lookup"><span data-stu-id="79be0-177">WCF implements 3 versions of WS-Addressing:</span></span>

- <span data-ttu-id="79be0-178">WS-Addressing 2004/08</span><span class="sxs-lookup"><span data-stu-id="79be0-178">WS-Addressing 2004/08</span></span>

- <span data-ttu-id="79be0-179">W3C Web Services Addressing 1,0 Core (ADDR10-CORE) e ligação SOAP (ADDR10-SOAP)</span><span class="sxs-lookup"><span data-stu-id="79be0-179">W3C Web Services Addressing 1.0 Core  (ADDR10-CORE) and SOAP Binding (ADDR10-SOAP)</span></span>

- <span data-ttu-id="79be0-180">WS-Addressing 1,0-Metadata</span><span class="sxs-lookup"><span data-stu-id="79be0-180">WS-Addressing 1.0 - Metadata</span></span>

### <a name="endpoint-references"></a><span data-ttu-id="79be0-181">Referências de ponto de extremidade</span><span class="sxs-lookup"><span data-stu-id="79be0-181">Endpoint References</span></span>
<span data-ttu-id="79be0-182">Todas as versões do WS-Addressing que o WCF implementa usam referências de ponto de extremidade para descrever pontos de extremidades.</span><span class="sxs-lookup"><span data-stu-id="79be0-182">All versions of WS-Addressing that WCF implements use endpoint references to describe endpoints.</span></span>

#### <a name="endpoint-references-and-ws-addressing-versions"></a><span data-ttu-id="79be0-183">Referências de ponto de extremidade e versões WS-Addressing</span><span class="sxs-lookup"><span data-stu-id="79be0-183">Endpoint References and WS-Addressing Versions</span></span>
<span data-ttu-id="79be0-184">O WCF implementa vários protocolos de infraestrutura que usam WS-Addressing e, em particular `EndpointReference` , o elemento e a `W3C.WsAddressing.EndpointReferenceType` classe (por exemplo, WS-RELIABLEMESSAGING, WS-SECURECONVERSATION e WS-Trust).</span><span class="sxs-lookup"><span data-stu-id="79be0-184">WCF implements a number of the infrastructure protocols that use WS-Addressing and in particular the `EndpointReference` element and `W3C.WsAddressing.EndpointReferenceType` class (for example, WS-ReliableMessaging, WS-SecureConversation, and WS-Trust).</span></span> <span data-ttu-id="79be0-185">O WCF dá suporte ao uso de qualquer versão do WS-Addressing com outros protocolos de infraestrutura.</span><span class="sxs-lookup"><span data-stu-id="79be0-185">WCF supports the use of either version of WS-Addressing with other infrastructure protocols.</span></span> <span data-ttu-id="79be0-186">Os pontos de extremidade do WCF dão suporte a uma versão do WS-Addressing por Endpoint.</span><span class="sxs-lookup"><span data-stu-id="79be0-186">WCF endpoints support one version of WS-Addressing per endpoint.</span></span>

<span data-ttu-id="79be0-187">Para R3111, o namespace para o `EndpointReference` elemento ou tipo usado em mensagens trocadas com um ponto de extremidade do WCF deve corresponder à versão do WS-Addressing implementada por esse ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="79be0-187">For R3111, the namespace for the `EndpointReference` element or type used in messages exchanged with a WCF endpoint must match the version of WS-Addressing implemented by this endpoint.</span></span>

<span data-ttu-id="79be0-188">Por exemplo, se um ponto de extremidade WCF implementa WS-ReliableMessaging, o `AcksTo` cabeçalho retornado por tal ponto de extremidade dentro `CreateSequenceResponse` usa a versão WS-Addressing que o `EncodingBinding` elemento especifica para esse ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="79be0-188">For example, if a WCF endpoint implements WS-ReliableMessaging, the `AcksTo` header returned by such an endpoint inside `CreateSequenceResponse` uses the WS-Addressing version that the `EncodingBinding` element specifies for this endpoint.</span></span>

#### <a name="endpoint-references-and-metadata"></a><span data-ttu-id="79be0-189">Referências de ponto de extremidade e metadados</span><span class="sxs-lookup"><span data-stu-id="79be0-189">Endpoint References and Metadata</span></span>
<span data-ttu-id="79be0-190">Vários cenários exigem a comunicação de metadados ou uma referência a metadados para um determinado ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="79be0-190">A number of scenarios require communicating metadata or a reference to metadata for a given endpoint.</span></span>

<span data-ttu-id="79be0-191">B3121: o WCF emprega mecanismos descritos na especificação de WS-MetadataExchange (MEX) 6 para incluir metadados para referências de ponto de extremidade por valor ou por referência.</span><span class="sxs-lookup"><span data-stu-id="79be0-191">B3121: WCF employs mechanisms described in the WS-MetadataExchange (MEX) specification Section 6 to include metadata for endpoint references by value or by reference.</span></span>

<span data-ttu-id="79be0-192">Considere um cenário em que um serviço WCF requer autenticação usando um token SAML (Security Asserts Markup Language) emitido pelo emissor do token em `http://sts.fabrikam123.com` .</span><span class="sxs-lookup"><span data-stu-id="79be0-192">Consider a scenario where a WCF service requires authentication using a Security Assertions Markup Language (SAML) token issued by the token issuer at `http://sts.fabrikam123.com`.</span></span> <span data-ttu-id="79be0-193">O ponto de extremidade do WCF descreve esse requisito de autenticação usando `sp:IssuedToken` a asserção com uma asserção aninhada `sp:Issuer` apontando para o emissor do token.</span><span class="sxs-lookup"><span data-stu-id="79be0-193">The WCF endpoint describes this authentication requirement by using `sp:IssuedToken` assertion with a nested `sp:Issuer` assertion pointing to the token issuer.</span></span> <span data-ttu-id="79be0-194">Os aplicativos cliente que acessam a `sp:Issuer` declaração precisam saber como se comunicar com o ponto de extremidade do emissor do token.</span><span class="sxs-lookup"><span data-stu-id="79be0-194">Client applications that access the `sp:Issuer` assertion need to know how to communicate with the token issuer endpoint.</span></span> <span data-ttu-id="79be0-195">O cliente precisa saber os metadados sobre o emissor do token.</span><span class="sxs-lookup"><span data-stu-id="79be0-195">The client needs to know metadata about the token issuer.</span></span> <span data-ttu-id="79be0-196">Usando as extensões de metadados de referência do ponto de extremidade definidas em MEX, o WCF fornece uma referência aos metadados do emissor do token.</span><span class="sxs-lookup"><span data-stu-id="79be0-196">Using the endpoint reference metadata extensions defined in MEX, WCF provides a reference to the token issuer metadata.</span></span>

```xml
<sp:IssuedToken>
  <sp:Issuer>
    <wsa10:Address>
      http://sts.fabrikam123.com
    </wsa10:Address>
    <wsa10:Metadata>
      <mex:Metadata>
        <mex:MetadataSection>
          <mex:MetadataReference>
            <wsa10:Address>
              http://sts.fabrikam123.com/mex
            </wsa10:Address>
          </mex:MetadataReference>
        </mex:MetadataSection>
      </mex:Metadata>
    </wsa10:Metadata>
  </sp:Issuer>
</sp:IssuedToken>
```

### <a name="message-addressing-headers"></a><span data-ttu-id="79be0-197">Cabeçalhos de endereçamento de mensagens</span><span class="sxs-lookup"><span data-stu-id="79be0-197">Message Addressing Headers</span></span>

#### <a name="message-headers"></a><span data-ttu-id="79be0-198">Cabeçalhos da mensagem</span><span class="sxs-lookup"><span data-stu-id="79be0-198">Message Headers</span></span>
<span data-ttu-id="79be0-199">Para as versões do WS-Addressing, o WCF usa os seguintes cabeçalhos de mensagem, conforme prescrito pelas especificações `wsa:To` , `wsa:ReplyTo` ,, `wsa:Action` `wsa:MessageID` e `wsa:RelatesTo` .</span><span class="sxs-lookup"><span data-stu-id="79be0-199">For both WS-Addressing versions, WCF uses the following message headers as prescribed by the specifications `wsa:To`, `wsa:ReplyTo`, `wsa:Action`, `wsa:MessageID`,and `wsa:RelatesTo`.</span></span>

<span data-ttu-id="79be0-200">B3211: para todas as versões de WS-Addressing, o WCF honra, mas não produz os cabeçalhos de mensagem WS-Addressing `wsa:FaultTo` e `wsa:From` .</span><span class="sxs-lookup"><span data-stu-id="79be0-200">B3211: For all WS-Addressing versions, WCF honors, but does not produce out of the box, WS-Addressing message headers `wsa:FaultTo` and `wsa:From`.</span></span>

<span data-ttu-id="79be0-201">Os aplicativos que interagem com aplicativos WCF podem adicionar esses cabeçalhos de mensagens e o WCF os processará de forma adequada.</span><span class="sxs-lookup"><span data-stu-id="79be0-201">Applications that interact with WCF applications can add these message headers and WCF will process them accordingly.</span></span>

#### <a name="reference-parameters-and-properties"></a><span data-ttu-id="79be0-202">Parâmetros e propriedades de referência</span><span class="sxs-lookup"><span data-stu-id="79be0-202">Reference Parameters and Properties</span></span>

<span data-ttu-id="79be0-203">O WCF implementa o processamento de parâmetros de referência de ponto de extremidade e propriedades de referência de acordo com as respectivas especificações.</span><span class="sxs-lookup"><span data-stu-id="79be0-203">WCF implements processing of endpoint reference parameters and reference properties in accordance with respective specifications.</span></span>

<span data-ttu-id="79be0-204">B3221: quando configurado para usar o WS-Addressing 2004/08, os pontos de extremidade do WCF não diferenciam as propriedades de referência de processamento e os parâmetros de referência.</span><span class="sxs-lookup"><span data-stu-id="79be0-204">B3221: When configured to use WS-Addressing 2004/08, WCF endpoints do not differentiate between processing Reference Properties and Reference Parameters.</span></span>

### <a name="message-exchange-patterns"></a><span data-ttu-id="79be0-205">Padrões de troca de mensagens</span><span class="sxs-lookup"><span data-stu-id="79be0-205">Message Exchange Patterns</span></span>
<span data-ttu-id="79be0-206">A sequência de mensagens envolvidas na invocação de operação do serviço Web é chamada de *padrão de troca de mensagens*.</span><span class="sxs-lookup"><span data-stu-id="79be0-206">The sequence of messages involved in the Web service operation invocation is referred to as the *message exchange pattern*.</span></span> <span data-ttu-id="79be0-207">O WCF dá suporte a padrões unidirecionais, de solicitação-resposta e de troca de mensagens duplex.</span><span class="sxs-lookup"><span data-stu-id="79be0-207">WCF supports one-way, request-reply, and duplex message exchange patterns.</span></span> <span data-ttu-id="79be0-208">Esta seção esclarece os requisitos de WS-Addressing no processamento de mensagens, dependendo do padrão de troca de mensagens que está sendo usado.</span><span class="sxs-lookup"><span data-stu-id="79be0-208">This section clarifies WS-Addressing requirements on message processing depending on the message exchange pattern being used.</span></span>

<span data-ttu-id="79be0-209">Ao longo desta seção, o solicitante envia a primeira mensagem e o respondente recebe a primeira mensagem.</span><span class="sxs-lookup"><span data-stu-id="79be0-209">Throughout this section, the requester sends the first message and the responder receives the first message.</span></span>

#### <a name="one-way-message"></a><span data-ttu-id="79be0-210">Mensagem unidirecional</span><span class="sxs-lookup"><span data-stu-id="79be0-210">One-Way Message</span></span>
<span data-ttu-id="79be0-211">Quando um ponto de extremidade WCF é configurado para dar suporte a mensagens com um determinado `Action` para seguir um padrão unidirecional, o ponto de extremidade do WCF segue os seguintes comportamentos e requisitos.</span><span class="sxs-lookup"><span data-stu-id="79be0-211">When a WCF endpoint is configured to support messages with a given `Action` to follow a one-way pattern, the WCF endpoint follows the following behaviors and requirements.</span></span> <span data-ttu-id="79be0-212">A menos que especificado de outra forma, os comportamentos e as regras se aplicam a ambas as versões do WS-Addressing com suporte no WCF:</span><span class="sxs-lookup"><span data-stu-id="79be0-212">Unless otherwise specified, behaviors and rules apply for both versions of WS-Addressing supported in WCF:</span></span>

- <span data-ttu-id="79be0-213">R3311: o solicitante deve incluir `wsa:To` `wsa:Action` cabeçalhos, e para todos os parâmetros de referência especificados pela referência do ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="79be0-213">R3311: The requester must include `wsa:To`, `wsa:Action`, and headers for all reference parameters specified by the endpoint reference.</span></span> <span data-ttu-id="79be0-214">Quando o WS-Addressing 2004/08 é usado e [Propriedades de referência] são especificados pela referência do ponto de extremidade, os cabeçalhos correspondentes também devem ser adicionados à mensagem.</span><span class="sxs-lookup"><span data-stu-id="79be0-214">When WS-Addressing 2004/08 is used and [reference properties] are specified by the endpoint reference, the corresponding headers must be added to the message too.</span></span>

- <span data-ttu-id="79be0-215">B3312: o solicitante pode incluir `MessageID` `ReplyTo` cabeçalhos, e `FaultTo` .</span><span class="sxs-lookup"><span data-stu-id="79be0-215">B3312: The requester may include `MessageID`, `ReplyTo`, and `FaultTo` headers.</span></span> <span data-ttu-id="79be0-216">A infraestrutura do receptor irá ignorá-las e elas serão passadas para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="79be0-216">The receiver infrastructure will ignore them, and they will be passed to the application.</span></span>

- <span data-ttu-id="79be0-217">R3313: quando HTTP é usado e nenhuma mensagem está sendo enviada no trecho de resposta HTTP, o respondente deve enviar uma resposta HTTP com um corpo vazio e um código de status HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="79be0-217">R3313: When HTTP is used and no message is being sent on the HTTP response leg, the responder must send an HTTP response with an empty body and an HTTP 202 status code.</span></span>

     <span data-ttu-id="79be0-218">Quando o transporte HTTP está em uso e o contrato de operação declara uma mensagem unidirecional, a resposta HTTP ainda pode ser usada para enviar mensagens de infraestrutura — por exemplo, mensagens confiáveis podem enviar uma `SequenceAcknowledgement` mensagem em uma resposta http.</span><span class="sxs-lookup"><span data-stu-id="79be0-218">When the HTTP transport is in use and the operation contract declares a message one-way, the HTTP response can still be used for sending infrastructure messages—for example, reliable messaging can send a `SequenceAcknowledgement` message on an HTTP response.</span></span>

- <span data-ttu-id="79be0-219">B3314: o respondente do WCF não envia uma mensagem de falha em resposta a uma mensagem unidirecional.</span><span class="sxs-lookup"><span data-stu-id="79be0-219">B3314: The WCF responder does not send a fault message in response to a one-way message.</span></span>

#### <a name="request-reply"></a><span data-ttu-id="79be0-220">Solicitação-resposta</span><span class="sxs-lookup"><span data-stu-id="79be0-220">Request-Reply</span></span>
<span data-ttu-id="79be0-221">Quando um ponto de extremidade do WCF é configurado para uma mensagem com um determinado `Action` para seguir o padrão de solicitação-resposta, o ponto de extremidade do WCF segue os comportamentos e os requisitos abaixo.</span><span class="sxs-lookup"><span data-stu-id="79be0-221">When a WCF endpoint is configured for a message with a given `Action` to follow the request-reply pattern, the WCF endpoint follows the behaviors and requirements below.</span></span> <span data-ttu-id="79be0-222">A menos que especificado caso contrário, os comportamentos e as regras se aplicam a ambas as versões do WS-Addressing com suporte no WCF:</span><span class="sxs-lookup"><span data-stu-id="79be0-222">Unless specified otherwise, behaviors and rules apply for both versions of WS-Addressing supported in WCF:</span></span>

- <span data-ttu-id="79be0-223">R3321: o solicitante deve incluir nos cabeçalhos Request `wsa:To` , `wsa:Action` , `wsa:MessageID` e para todos os parâmetros de referência ou propriedades de referência (ou ambos) especificados pela referência do ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="79be0-223">R3321: The requester must include in the request `wsa:To`, `wsa:Action`, `wsa:MessageID`, and headers for all reference parameters or reference properties (or both) specified by the endpoint reference.</span></span>

- <span data-ttu-id="79be0-224">R3322: quando o WS-Addressing 2004/08 é usado, `ReplyTo` também deve ser incluído na solicitação.</span><span class="sxs-lookup"><span data-stu-id="79be0-224">R3322: When WS-Addressing 2004/08 is used, `ReplyTo` must also be included in the request.</span></span>

- <span data-ttu-id="79be0-225">R3323: quando o WS-Addressing 1,0 é usado e `ReplyTo` não está presente na solicitação, uma referência de ponto de extremidade padrão com a propriedade [address] igual a `http://www.w3.org/2005/08/addressing/anonymous` é usada.</span><span class="sxs-lookup"><span data-stu-id="79be0-225">R3323: When WS-Addressing 1.0 is used and `ReplyTo` is not present in the request, a default endpoint reference with the [address] property equal to `http://www.w3.org/2005/08/addressing/anonymous` is used.</span></span>

- <span data-ttu-id="79be0-226">R3324: o solicitante deve incluir `wsa:To` `wsa:Action` cabeçalhos, e `wsa:RelatesTo` na mensagem de resposta, bem como cabeçalhos para todos os parâmetros de referência ou propriedades de referência (ou ambos) especificados pela `ReplyTo` referência do ponto de extremidade na solicitação.</span><span class="sxs-lookup"><span data-stu-id="79be0-226">R3324: The requester must include `wsa:To`, `wsa:Action`, and `wsa:RelatesTo` headers in the reply message, as well as headers for all reference parameters or reference properties (or both) specified by the `ReplyTo` endpoint reference in the request.</span></span>

### <a name="web-services-addressing-faults"></a><span data-ttu-id="79be0-227">Falhas de endereçamento de serviços Web</span><span class="sxs-lookup"><span data-stu-id="79be0-227">Web Services Addressing Faults</span></span>
<span data-ttu-id="79be0-228">R3411: o WCF produz as seguintes falhas definidas pelo WS-Addressing 2004/08.</span><span class="sxs-lookup"><span data-stu-id="79be0-228">R3411: WCF produces the following faults defined by WS-Addressing 2004/08.</span></span>

| <span data-ttu-id="79be0-229">Código</span><span class="sxs-lookup"><span data-stu-id="79be0-229">Code</span></span> | <span data-ttu-id="79be0-230">Causa</span><span class="sxs-lookup"><span data-stu-id="79be0-230">Cause</span></span> |
|----------|-----------|
| `wsa:DestinationUnreachable` | <span data-ttu-id="79be0-231">A mensagem recebida com um `ReplyTo` que é diferente do endereço de resposta estabelecido para este canal; não há nenhum ponto de extremidade ouvindo no endereço especificado no cabeçalho to.</span><span class="sxs-lookup"><span data-stu-id="79be0-231">The message arrived with a `ReplyTo` that is different from the reply address established for this channel; there is no endpoint listening at the address specified in the To header.</span></span> |
| `wsa:ActionNotSupported` | <span data-ttu-id="79be0-232">os canais de infraestrutura ou o Dispatcher associado ao ponto de extremidade não reconhece a ação especificada no `Action` cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="79be0-232">the infrastructure channels or dispatcher associated with the endpoint do not recognize the action specified in the `Action` header.</span></span> |

<span data-ttu-id="79be0-233">R3412: o WCF produz as seguintes falhas definidas pelo WS-Addressing 1,0.</span><span class="sxs-lookup"><span data-stu-id="79be0-233">R3412: WCF produces the following faults defined by WS-Addressing 1.0.</span></span>

| <span data-ttu-id="79be0-234">Código</span><span class="sxs-lookup"><span data-stu-id="79be0-234">Code</span></span> | <span data-ttu-id="79be0-235">Causa</span><span class="sxs-lookup"><span data-stu-id="79be0-235">Cause</span></span> |
|----------|-----------|
| `wsa10:InvalidAddressingHeader` | <span data-ttu-id="79be0-236">Duplicar `wsa:To` , `wsa:ReplyTo` , `wsa:From` ou `wsa:MessageID` .</span><span class="sxs-lookup"><span data-stu-id="79be0-236">Duplicate `wsa:To`, `wsa:ReplyTo`, `wsa:From` or `wsa:MessageID`.</span></span> <span data-ttu-id="79be0-237">Duplicar `wsa:RelatesTo` com o mesmo `RelationshipType` .</span><span class="sxs-lookup"><span data-stu-id="79be0-237">Duplicate `wsa:RelatesTo` with the same `RelationshipType`.</span></span> |
| `wsa10:MessageAddressingHeaderRequired` | <span data-ttu-id="79be0-238">O cabeçalho de endereçamento necessário está ausente.</span><span class="sxs-lookup"><span data-stu-id="79be0-238">The required Addressing header is missing.</span></span> |
| `wsa10:DestinationUnreachable` | <span data-ttu-id="79be0-239">A mensagem recebida com um `ReplyTo` que é diferente do endereço de resposta estabelecido para esse canal.</span><span class="sxs-lookup"><span data-stu-id="79be0-239">The message arrived with a `ReplyTo` that is different from the reply address established for this channel.</span></span> <span data-ttu-id="79be0-240">Não há nenhum ponto de extremidade ouvindo no endereço especificado no cabeçalho to.</span><span class="sxs-lookup"><span data-stu-id="79be0-240">There is no endpoint listening at the address specified in the To header.</span></span> |
| `wsa10:ActionNotSupported` | <span data-ttu-id="79be0-241">Uma ação especificada no `Action` cabeçalho não é reconhecida pelos canais de infraestrutura ou pelo Dispatcher associado ao ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="79be0-241">An action specified in the `Action` header is not recognized by the infrastructure channels or dispatcher associated with the endpoint.</span></span> |
| `wsa10:EndpointUnavailable` | <span data-ttu-id="79be0-242">O canal do RM envia essa falha de volta, indicando que o ponto de extremidade não processará a sequência com base no exame dos `CreateSequence` cabeçalhos de endereçamento da mensagem.</span><span class="sxs-lookup"><span data-stu-id="79be0-242">The RM channel sends this fault back, indicating the endpoint will not process the sequence based upon examination of the `CreateSequence` message’s addressing headers.</span></span> |

<span data-ttu-id="79be0-243">O código nas tabelas anteriores é mapeado para `FaultCode` em soap 1,1 e `SubCode` (com código = remetente) em SOAP 1,2.</span><span class="sxs-lookup"><span data-stu-id="79be0-243">Code in the preceding tables maps to `FaultCode` in SOAP 1.1 and `SubCode` (with Code=Sender) in SOAP 1.2.</span></span>

### <a name="wsdl-11-binding-and-ws-policy-assertions"></a><span data-ttu-id="79be0-244">Associação de WSDL 1,1 e declarações de WS-Policy</span><span class="sxs-lookup"><span data-stu-id="79be0-244">WSDL 1.1 Binding and WS-Policy Assertions</span></span>

#### <a name="indicating-use-of-ws-addressing"></a><span data-ttu-id="79be0-245">Indicando o uso de WS-Addressing</span><span class="sxs-lookup"><span data-stu-id="79be0-245">Indicating Use of WS-Addressing</span></span>
<span data-ttu-id="79be0-246">O WCF usa asserções de política para indicar o suporte de ponto de extremidade para uma versão específica de WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="79be0-246">WCF uses policy assertions to indicate endpoint support for a particular WS-Addressing version.</span></span>

<span data-ttu-id="79be0-247">A declaração de política a seguir tem o assunto da política de ponto de extremidade [WS-PA] e indica que as mensagens enviadas e recebidas do ponto de extremidade devem usar WS-Addressing 2004/08.</span><span class="sxs-lookup"><span data-stu-id="79be0-247">The following policy assertion has Endpoint Policy Subject [WS-PA] and indicates messages sent and received from the endpoint must use WS-Addressing 2004/08.</span></span>

```xml
<wsap:UsingAddressing />
```

<span data-ttu-id="79be0-248">Essa declaração de política aumenta a especificação 2004/08 WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="79be0-248">This policy assertion augments the WS-Addressing 2004/08 specification.</span></span>

<span data-ttu-id="79be0-249">A declaração de política a seguir indica que as mensagens enviadas/recebidas devem usar WS-Addressing 1,0.</span><span class="sxs-lookup"><span data-stu-id="79be0-249">The following policy assertion this indicates that messages sent/received must use WS-Addressing 1.0.</span></span>

```xml
<wsam:Addressing/>
```

<span data-ttu-id="79be0-250">A declaração de política a seguir tem um assunto de política de ponto de extremidade [WS-PA] e indica que as mensagens enviadas e recebidas do ponto de extremidade devem usar WS-Addressing 2004/08.</span><span class="sxs-lookup"><span data-stu-id="79be0-250">The following policy assertion has an Endpoint Policy Subject [WS-PA] and indicates that messages sent and received from the endpoint must use WS-Addressing 2004/08.</span></span>

```xml
<wsaw10:UsingAddressing />
```

<span data-ttu-id="79be0-251">O `wsaw10:UsingAddressing` elemento é emprestado de [WS-Addressing-WSDL] e é usado no contexto de WS-Policy em conformidade com essa especificação, seção 3.1.2.</span><span class="sxs-lookup"><span data-stu-id="79be0-251">The `wsaw10:UsingAddressing` element is borrowed from [WS-Addressing-WSDL] and is used in the context of WS-Policy in compliance with that specification, section 3.1.2.</span></span>

<span data-ttu-id="79be0-252">O uso de endereçamento não altera a semântica de associações HTTP de WSDL 1,1, SOAP 1,1 e SOAP 1,2.</span><span class="sxs-lookup"><span data-stu-id="79be0-252">Use of Addressing does not alter the semantics of WSDL 1.1, SOAP 1.1, and SOAP 1.2 HTTP Bindings.</span></span> <span data-ttu-id="79be0-253">Por exemplo, se uma resposta for esperada para uma solicitação que é enviada para um ponto de extremidade que usa o endereçamento e a associação HTTP SOAP 1. x WSDL, a resposta deve ser enviada usando a resposta HTTP.</span><span class="sxs-lookup"><span data-stu-id="79be0-253">For example, if a reply is expected to a request that is sent to an endpoint that uses Addressing and WSDL SOAP 1.x HTTP binding, the reply must be sent by using the HTTP response.</span></span>

<span data-ttu-id="79be0-254">Para respostas enviadas pela resposta http, a declaração WS-AM é:</span><span class="sxs-lookup"><span data-stu-id="79be0-254">For replies sent over the http response, the WS-AM assertion is:</span></span>

```xml
<wsam:AnonymousResponses/>
```

<span data-ttu-id="79be0-255">A declaração de política completa pode ser parecida com esta:</span><span class="sxs-lookup"><span data-stu-id="79be0-255">The complete policy assertion might look like this:</span></span>

```xml
<wsam:Addressing>
    <wsp:Policy>
        <wsam:AnonymousResponses />
    </wsp:Policy>
</wsam:Addressing>
```

<span data-ttu-id="79be0-256">No entanto, há padrões de troca de mensagens que se beneficiam da existência de duas conexões HTTP de converso independentes estabelecidas entre o solicitante e o respondente, por exemplo, mensagens unidirecionais não solicitadas enviadas pelo respondente.</span><span class="sxs-lookup"><span data-stu-id="79be0-256">However, there are message exchange patterns that benefit from having two independent converse HTTP connections established between the requester and the responder, for example, unsolicited one-way messages sent by the responder.</span></span>

<span data-ttu-id="79be0-257">O WCF oferece um recurso pelo qual dois canais de transporte subjacentes podem formar um canal duplex composto, em que um canal é usado para mensagens de entrada e o outro é usado para mensagens de saída.</span><span class="sxs-lookup"><span data-stu-id="79be0-257">WCF offers a feature by which two underlying transport channels can form a Composite Duplex channel, where one channel is used for input messages and the other is used for output messages.</span></span> <span data-ttu-id="79be0-258">No caso do transporte HTTP, o Composite duplex fornece duas conexões HTTP de contrapartida.</span><span class="sxs-lookup"><span data-stu-id="79be0-258">In the case of the HTTP Transport, Composite Duplex provides two converse HTTP connections.</span></span> <span data-ttu-id="79be0-259">O solicitante usa uma conexão para enviar mensagens ao Respondente e o respondente usa o outro para enviar mensagens de volta para o solicitante.</span><span class="sxs-lookup"><span data-stu-id="79be0-259">The requester uses one connection to send messages to the responder, and the responder uses the other to send messages back to the requester.</span></span>

<span data-ttu-id="79be0-260">Para respostas enviadas por solicitações HTTP separadas, a declaração WS-am é</span><span class="sxs-lookup"><span data-stu-id="79be0-260">For replies sent over separate http requests, the ws-am assertion is</span></span>

```xml
<wsam:NonAnonymousResponses/>
```

<span data-ttu-id="79be0-261">A declaração de política completa pode ser parecida com esta:</span><span class="sxs-lookup"><span data-stu-id="79be0-261">The complete policy assertion might look like this:</span></span>

```xml
<wsam:Addressing>
    <wsp:Policy>
        <wsam:NonAnonymousResponses />
    </wsp:Policy>
</wsam:Addressing>
```

<span data-ttu-id="79be0-262">O uso da declaração a seguir que tem o assunto da política de ponto de extremidade [WS-PA] em pontos de extremidades que usam associações HTTP SOAP 1. x de WSDL 1,1 requer duas conexões HTTP de discagem separadas a serem usadas para mensagens que fluem do solicitante para Respondente e Respondente ao solicitante, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="79be0-262">Use of the following assertion that has Endpoint Policy Subject [WS-PA] on endpoints that use WSDL 1.1 SOAP 1.x HTTP bindings requires two separate converse HTTP connections to be used for messages flowing from requester to responder and responder to requester, respectively.</span></span>

```xml
<cdp:CompositeDuplex/>
```

<span data-ttu-id="79be0-263">A instrução anterior leva aos seguintes requisitos no `wsa:ReplyTo` cabeçalho para mensagens de solicitação:</span><span class="sxs-lookup"><span data-stu-id="79be0-263">The previous statement leads to the following requirements on the `wsa:ReplyTo` header for request messages:</span></span>

- <span data-ttu-id="79be0-264">R3514: as mensagens de solicitação enviadas a um ponto de extremidade devem ter um `ReplyTo` cabeçalho com a propriedade diferente de `[address]` `http://www.w3.org/2005/08/addressing/anonymous` se o ponto de extremidade usa uma associação HTTP SOAP 1. x WSDL 1,1 e tem uma alternativa de política com uma `wsap10:UsingAddressing` asserção ou associada `wsap:UsingAddressing` com `cdp:CompositeDuplex` anexada.</span><span class="sxs-lookup"><span data-stu-id="79be0-264">R3514: Request messages sent to an endpoint must have a `ReplyTo` header with the `[address]` property not equal to `http://www.w3.org/2005/08/addressing/anonymous` if the endpoint uses a WSDL 1.1 SOAP 1.x HTTP binding and has a policy alternative with a `wsap10:UsingAddressing` or `wsap:UsingAddressing` assertion coupled with `cdp:CompositeDuplex` attached.</span></span>

- <span data-ttu-id="79be0-265">R3515: as mensagens de solicitação enviadas a um ponto de extremidade devem ter um `ReplyTo` cabeçalho com a `[address]` propriedade igual a `http://www.w3.org/2005/08/addressing/anonymous` , ou não ter um `ReplyTo` cabeçalho, se o ponto de extremidade usar uma associação HTTP SOAP 1. x WSDL 1,1 e tiver uma alternativa de política com `wsap10:UsingAddressing` asserção e nenhuma `cdp:CompositeDuplex` declaração anexada.</span><span class="sxs-lookup"><span data-stu-id="79be0-265">R3515: Request messages sent to an endpoint must have a `ReplyTo` header with the `[address]` property equal to `http://www.w3.org/2005/08/addressing/anonymous`, or not have a `ReplyTo` header at all, if the endpoint uses a WSDL 1.1 SOAP 1.x HTTP binding and has a policy alternative with `wsap10:UsingAddressing` assertion and no `cdp:CompositeDuplex` assertion attached.</span></span>

- <span data-ttu-id="79be0-266">R3516: as mensagens de solicitação enviadas a um ponto de extremidade devem ter um `ReplyTo` cabeçalho com uma `[address]` propriedade igual a `http://www.w3.org/2005/08/addressing/anonymous` se o ponto de extremidade usa uma associação HTTP SOAP 1. x WSDL 1,1 e tem uma alternativa de política com `wsap:UsingAddressing` asserção e nenhuma `cdp:CompositeDuplex` declaração anexada.</span><span class="sxs-lookup"><span data-stu-id="79be0-266">R3516: Request messages sent to an endpoint must have a `ReplyTo` header with an `[address]` property equal to `http://www.w3.org/2005/08/addressing/anonymous` if the endpoint uses a WSDL 1.1 SOAP 1.x HTTP binding and has a policy alternative with `wsap:UsingAddressing` assertion and no `cdp:CompositeDuplex` assertion attached.</span></span>

<span data-ttu-id="79be0-267">A especificação WSDL do WS-Addressing tenta descrever associações de protocolo semelhantes introduzindo um elemento `<wsaw:Anonymous/>` com três valores textuais (obrigatório, opcional e proibido) para indicar os requisitos no `wsa:ReplyTo` cabeçalho (seção 3,2).</span><span class="sxs-lookup"><span data-stu-id="79be0-267">The WS-addressing WSDL specification attempts to describe similar protocol bindings by introducing an element `<wsaw:Anonymous/>` with three textual values (required, optional, and prohibited) to indicate requirements on the `wsa:ReplyTo` header (section 3.2).</span></span> <span data-ttu-id="79be0-268">Infelizmente, essa definição de elemento não é particularmente utilizável como uma declaração no contexto de WS-Policy, pois requer extensões específicas de domínio para dar suporte à interseção de alternativas usando um elemento como uma asserção.</span><span class="sxs-lookup"><span data-stu-id="79be0-268">Unfortunately, such element definition is not particularly usable as an assertion in the context of WS-Policy, because it requires domain-specific extensions to support the intersection of alternatives using such an element as an assertion.</span></span> <span data-ttu-id="79be0-269">Essa definição de elemento também indica o valor do `ReplyTo` cabeçalho em oposição ao comportamento do ponto de extremidade na conexão, o que o torna específico ao transporte http.</span><span class="sxs-lookup"><span data-stu-id="79be0-269">Such element definition also indicates the value of the `ReplyTo` header as opposed to the endpoint behavior on the wire, which makes it specific to HTTP transport.</span></span>

#### <a name="action-definition"></a><span data-ttu-id="79be0-270">Definição de ação</span><span class="sxs-lookup"><span data-stu-id="79be0-270">Action Definition</span></span>
<span data-ttu-id="79be0-271">O WS-Addressing 2004/08 define um `wsa:Action` atributo para os `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]` elementos.</span><span class="sxs-lookup"><span data-stu-id="79be0-271">WS-Addressing 2004/08 defines a `wsa:Action` attribute for the `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]` elements.</span></span> <span data-ttu-id="79be0-272">A associação de WSDL do WS-Addressing 1,0 (WS-ADDR10-WSDL) define um atributo semelhante, `wsaw10:Action` .</span><span class="sxs-lookup"><span data-stu-id="79be0-272">WS-Addressing 1.0 WSDL Binding (WS-ADDR10-WSDL) defines a similar attribute, `wsaw10:Action`.</span></span>

<span data-ttu-id="79be0-273">A única diferença entre os dois é a semântica padrão de padrão de ação descrita na seção 3.3.2 do WS-ADDR e da seção 4.4.4 de WS-ADDR10-WSDL, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="79be0-273">The only difference between the two is the default Action pattern semantics described in section 3.3.2 of WS-ADDR and section 4.4.4 of WS-ADDR10-WSDL, respectively.</span></span>

<span data-ttu-id="79be0-274">É razoável ter dois pontos de extremidade que compartilham o mesmo `portType` (ou contrato, na terminologia do WCF), mas usando versões diferentes do WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="79be0-274">It is a reasonable to have two endpoints that share the same `portType` (or contract, in WCF terminology) but using different versions of WS-Addressing.</span></span> <span data-ttu-id="79be0-275">Mas, Considerando que a ação é definida pelo `portType` e não deve ser alterada nos pontos de extremidade que implementam o `portType` , torna-se impossível dar suporte a ambos os padrões de ação padrão.</span><span class="sxs-lookup"><span data-stu-id="79be0-275">But given that Action is defined by the `portType` and should not change across the endpoints that implement the `portType`, it becomes impossible to support both default action patterns.</span></span>

<span data-ttu-id="79be0-276">Para resolver esse secou, o WCF dá suporte a uma única versão do `Action` atributo.</span><span class="sxs-lookup"><span data-stu-id="79be0-276">To resolve this controversy, WCF supports a single version of the `Action` attribute.</span></span>

<span data-ttu-id="79be0-277">B3521: o WCF usa o `wsaw10:Action` atributo em `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]` elementos, conforme definido em WS-ADDR10-WSDL para determinar o `Action` URI das mensagens correspondentes, independentemente da versão do WS-Addressing usada pelo ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="79be0-277">B3521: WCF uses the `wsaw10:Action` attribute on `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]` elements as defined in WS-ADDR10-WSDL to determine the `Action` URI for the corresponding messages irrespective of the WS-Addressing version used by the endpoint.</span></span>

#### <a name="use-endpoint-reference-inside-wsdl-port"></a><span data-ttu-id="79be0-278">Usar referência de ponto de extremidade dentro da porta WSDL</span><span class="sxs-lookup"><span data-stu-id="79be0-278">Use Endpoint Reference Inside WSDL Port</span></span>
<span data-ttu-id="79be0-279">A seção 4,1 do WS-ADDR10-WSDL estende o `wsdl:port` elemento para incluir o `<wsa10:EndpointReference…/>` elemento filho para descrever o ponto de extremidade em termos de endereçamento WS.</span><span class="sxs-lookup"><span data-stu-id="79be0-279">WS-ADDR10-WSDL section 4.1 extends the `wsdl:port` element to include the `<wsa10:EndpointReference…/>` child element to describe the endpoint in WS-Addressing terms.</span></span> <span data-ttu-id="79be0-280">O WCF expande esse utilitário no WS-Addressing 2004/08, permitindo que `<wsa:EndpointReference…/>` apareça como um elemento filho de `wsdl:port` .</span><span class="sxs-lookup"><span data-stu-id="79be0-280">WCF expands this utility on WS-Addressing 2004/08, allowing `<wsa:EndpointReference…/>` to appear as a child element of `wsdl:port`.</span></span>

- <span data-ttu-id="79be0-281">R3531: se um ponto de extremidade tiver uma alternativa de política anexada com uma `<wsaw10:UsingAddressing/>` declaração de política, o `wsdl:port` elemento correspondente poderá conter um elemento filho `<wsa10:EndpointReference …/>` .</span><span class="sxs-lookup"><span data-stu-id="79be0-281">R3531: If an endpoint has an attached policy alternative with a `<wsaw10:UsingAddressing/>` policy assertion, the corresponding `wsdl:port` element can contain a child element `<wsa10:EndpointReference …/>`.</span></span>

- <span data-ttu-id="79be0-282">R3532: se um `wsdl:port` contiver um elemento filho `<wsa10:EndpointReference …/>` , o `wsa10:EndpointReference/wsa10:Address` valor do elemento filho deverá corresponder ao valor do `@address` atributo do `wsdl:port` / `wsdl:location` elemento irmão.</span><span class="sxs-lookup"><span data-stu-id="79be0-282">R3532: If a `wsdl:port` contains a child element `<wsa10:EndpointReference …/>`, the `wsa10:EndpointReference/wsa10:Address` child element value must match the value of the `@address` attribute of the sibling `wsdl:port`/`wsdl:location` element.</span></span>

- <span data-ttu-id="79be0-283">R3533: se um ponto de extremidade tiver uma alternativa de política anexada com `<wsap:UsingAddressing/>` a declaração de política, o `wsdl:port` elemento correspondente poderá conter um elemento filho `<wsa:EndpointReference …/>` .</span><span class="sxs-lookup"><span data-stu-id="79be0-283">R3533: If an endpoint has an attached policy alternative with `<wsap:UsingAddressing/>` policy assertion, the corresponding `wsdl:port` element can contain a child element `<wsa:EndpointReference …/>`.</span></span>

- <span data-ttu-id="79be0-284">R3534: se um `wsdl:port` contiver um elemento filho `<wsa:EndpointReference …/>` , o `wsa:EndpointReference/wsa:Address` valor do elemento filho deverá corresponder ao valor do `@address` atributo do `wsdl:port` / `wsdl:location` elemento irmão.</span><span class="sxs-lookup"><span data-stu-id="79be0-284">R3534: If a `wsdl:port` contains a child element `<wsa:EndpointReference …/>`, the `wsa:EndpointReference/wsa:Address` child element value must match the value of the `@address` attribute of the sibling `wsdl:port`/`wsdl:location` element.</span></span>

### <a name="composition-with-ws-security"></a><span data-ttu-id="79be0-285">Composição com WS-Security</span><span class="sxs-lookup"><span data-stu-id="79be0-285">Composition with WS-Security</span></span>
<span data-ttu-id="79be0-286">De acordo com as seções de consideração de segurança em WS-ADDR e WS-ADDR10, é recomendável que todos os cabeçalhos de mensagens de endereçamento sejam assinados junto com o corpo da mensagem para associá-los.</span><span class="sxs-lookup"><span data-stu-id="79be0-286">According to security consideration sections in WS-ADDR and WS-ADDR10, all addressing message headers are recommended to be signed together with the message body to bind them together.</span></span>

<span data-ttu-id="79be0-287">Quando o WS-Security é usado para proteção de integridade de mensagem, os cabeçalhos de mensagem do WS-Addressing, bem como os cabeçalhos resultantes de parâmetros de referência ou Propriedades (ou ambos) devem ser assinados com o corpo da mensagem.</span><span class="sxs-lookup"><span data-stu-id="79be0-287">When WS-Security is used for message integrity protection, WS-Addressing message headers as well as headers resulted from reference parameters or properties (or both) must be signed together with the body of the message.</span></span>

### <a name="examples"></a><span data-ttu-id="79be0-288">Exemplos</span><span class="sxs-lookup"><span data-stu-id="79be0-288">Examples</span></span>

#### <a name="one-way-message"></a><span data-ttu-id="79be0-289">Mensagem unidirecional</span><span class="sxs-lookup"><span data-stu-id="79be0-289">One-Way Message</span></span>
<span data-ttu-id="79be0-290">Nesse cenário, o remetente envia uma mensagem unidirecional para o destinatário.</span><span class="sxs-lookup"><span data-stu-id="79be0-290">In this scenario, the sender sends a one-way message to the receiver.</span></span> <span data-ttu-id="79be0-291">SOAP 1,2, HTTP 1,1 e W3C WS-Addressing 1,0 são usados.</span><span class="sxs-lookup"><span data-stu-id="79be0-291">SOAP 1.2, HTTP 1.1, and W3C WS-Addressing 1.0 are used.</span></span>

<span data-ttu-id="79be0-292">A estrutura da mensagem de solicitação: os cabeçalhos de mensagem incluem `wsa10:To` `wsa10:Action` elementos e.</span><span class="sxs-lookup"><span data-stu-id="79be0-292">The Request Message Structure: The message headers include `wsa10:To` and `wsa10:Action` elements.</span></span> <span data-ttu-id="79be0-293">O corpo da mensagem inclui um `<app:Ping>` elemento específico do namespace do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="79be0-293">The message body includes a specific `<app:Ping>` element from the application namespace.</span></span>

<span data-ttu-id="79be0-294">Cabeçalhos HTTP: o destino em POST corresponde ao URI no `wsa10:To` elemento.</span><span class="sxs-lookup"><span data-stu-id="79be0-294">HTTP Headers: The destination in POST matches the URI in the `wsa10:To` element.</span></span>

<span data-ttu-id="79be0-295">O cabeçalho Content-Type tem o valor de `application/soap+xml` conforme exigido pelo SOAP 1,2.</span><span class="sxs-lookup"><span data-stu-id="79be0-295">The Content-Type header has the value of `application/soap+xml` as required by SOAP 1.2.</span></span> <span data-ttu-id="79be0-296">Parâmetros `charset` e `action` são incluídos.</span><span class="sxs-lookup"><span data-stu-id="79be0-296">Parameters `charset` and `action` are included.</span></span> <span data-ttu-id="79be0-297">O `action` parâmetro do cabeçalho Content-Type corresponde ao valor do cabeçalho da `wsa10:Action` mensagem.</span><span class="sxs-lookup"><span data-stu-id="79be0-297">The `action` parameter of the Content-Type header matches the value of the `wsa10:Action` message header.</span></span>

```http
POST http://fabrikam123.com/Service HTTP/1.1
Content-Type: application/soap+xml; charset=utf-8;  
              action="http://fabrikam123.com/Service/OneWay"
Host: 131.107.72.15
Content-Length: 1501
Expect: 100-continue
Proxy-Connection: Keep-Alive
<s12:Envelope>
  <s12:Header>
    <wsa10:To s12:mustUnderstand="1">
        http://fabrikam123.com/Service
    </wsa10:To>
    <wsa10:Action s12:mustUnderstand="1">
        http://fabrikam123.com/Service/OneWay
    </wsa10:Action>
  </s12:Header>
  <s12:Body>
    <Ping xmlns="http://fabrikam123.com/Service/">
      <Text>Hello World</Text>
    </Ping>
  </s12:Body>
</s12:Envelope>
```

<span data-ttu-id="79be0-298">O receptor responde com uma resposta HTTP vazia e o status 202.</span><span class="sxs-lookup"><span data-stu-id="79be0-298">The receiver responds with an empty HTTP response and status 202.</span></span> <span data-ttu-id="79be0-299">Um exemplo da resposta HTTP:</span><span class="sxs-lookup"><span data-stu-id="79be0-299">An example of the HTTP response:</span></span>

```http
HTTP/1.1 202 Accepted
Date: Fri, 15 Jul 2005 08:56:07 GMT
Server: Microsoft-IIS/6.0
MicrosoftOfficeWebServer: 5.0_Pub
X-Powered-By: ASP.NET
X-AspNet-Version: 2.0.50215
Cache-Control: private
Content-Length: 0
```

## <a name="soap-message-transmission-optimization-mechanism"></a><span data-ttu-id="79be0-300">Mecanismo de otimização de transmissão de mensagens SOAP</span><span class="sxs-lookup"><span data-stu-id="79be0-300">SOAP Message Transmission Optimization Mechanism</span></span>
<span data-ttu-id="79be0-301">Esta seção descreve os detalhes de implementação do WCF para HTTP SOAP MTOM.</span><span class="sxs-lookup"><span data-stu-id="79be0-301">This section describes the WCF implementation details for the HTTP SOAP MTOM.</span></span> <span data-ttu-id="79be0-302">A tecnologia MTOM é um mecanismo de codificação de mensagens SOAP da mesma classe que a codificação de texto/XML tradicional ou a codificação binária do WCF.</span><span class="sxs-lookup"><span data-stu-id="79be0-302">MTOM technology is SOAP message encoding mechanism of the same class as traditional text/XML encoding or WCF Binary encoding.</span></span> <span data-ttu-id="79be0-303">O MTOM inclui o seguinte:</span><span class="sxs-lookup"><span data-stu-id="79be0-303">MTOM includes the following:</span></span>

- <span data-ttu-id="79be0-304">Um mecanismo de codificação e empacotamento XML descrito por [XOP] que otimiza itens de informações XML contendo dados binários codificados na base64 em partes binárias separadas.</span><span class="sxs-lookup"><span data-stu-id="79be0-304">An XML encoding and packaging mechanism described by [XOP] that optimizes XML information items containing base64-encoded binary data into separate binary parts.</span></span>

- <span data-ttu-id="79be0-305">Um encapsulamento MIME do pacote XOP que serializa o XML infoset e cada parte binária do pacote XOP em uma parte MIME separada.</span><span class="sxs-lookup"><span data-stu-id="79be0-305">A MIME encapsulation of the XOP package that serializes the XML Infoset and each binary part of the XOP package into a separate MIME part.</span></span>

- <span data-ttu-id="79be0-306">Uma codificação de XOP MIME aplicada ao envelope SOAP 1. x.</span><span class="sxs-lookup"><span data-stu-id="79be0-306">A MIME XOP encoding applied to SOAP 1.x Envelope.</span></span>

- <span data-ttu-id="79be0-307">Uma associação de transporte HTTP.</span><span class="sxs-lookup"><span data-stu-id="79be0-307">An HTTP transport binding.</span></span>

<span data-ttu-id="79be0-308">É possível usar o MTOM com transportes não HTTP com o WCF.</span><span class="sxs-lookup"><span data-stu-id="79be0-308">It is possible to use MTOM with non-HTTP transports with WCF.</span></span> <span data-ttu-id="79be0-309">No entanto, neste tópico, vamos nos concentrar no HTTP.</span><span class="sxs-lookup"><span data-stu-id="79be0-309">However, in this topic we will focus on HTTP.</span></span>

<span data-ttu-id="79be0-310">O formato MTOM aproveita um grande conjunto de especificações que abrangem o próprio MTOM, XOP e MIME.</span><span class="sxs-lookup"><span data-stu-id="79be0-310">The MTOM format leverages a large set of specifications covering MTOM itself, XOP, and MIME.</span></span> <span data-ttu-id="79be0-311">A modularidade desse conjunto de especificação torna um pouco difícil reconstruir os requisitos exatos no formato e na semântica de processamento.</span><span class="sxs-lookup"><span data-stu-id="79be0-311">Modularity of this specification set makes it somewhat difficult to reconstruct exact requirements on the format and processing semantics.</span></span> <span data-ttu-id="79be0-312">Esta seção descreve os requisitos de formato e processamento para a associação HTTP MTOM.</span><span class="sxs-lookup"><span data-stu-id="79be0-312">This section describes the format and processing requirements for MTOM HTTP binding.</span></span>

### <a name="mtom-message-encoding"></a><span data-ttu-id="79be0-313">Codificação de mensagem MTOM</span><span class="sxs-lookup"><span data-stu-id="79be0-313">MTOM Message Encoding</span></span>

#### <a name="generating-mtom-messages"></a><span data-ttu-id="79be0-314">Gerando mensagens MTOM</span><span class="sxs-lookup"><span data-stu-id="79be0-314">Generating MTOM messages</span></span>
<span data-ttu-id="79be0-315">A seção [XOP] 3,1 descreve o processo de codificação de XML com itens de informações de elemento que contêm valores de Base64 em um pacote XOP definido de forma abstrata.</span><span class="sxs-lookup"><span data-stu-id="79be0-315">The [XOP] section 3.1 describes the process of encoding XML with element information items that contain base64 values into an abstractly defined XOP package.</span></span>

<span data-ttu-id="79be0-316">A seguinte sequência de etapas descreve o processo de codificação específico de MTOM:</span><span class="sxs-lookup"><span data-stu-id="79be0-316">The following sequence of steps describes the MTOM-specific encoding process:</span></span>

1. <span data-ttu-id="79be0-317">Verifique se o envelope SOAP a ser codificado não contém nenhum item de informações de elemento com um `[namespace name]` de `http://www.w3.org/2004/08/xop/include` e um `[local name]` de `Include` .</span><span class="sxs-lookup"><span data-stu-id="79be0-317">Ensure that the SOAP Envelope to be encoded contains no element information item with a `[namespace name]` of `http://www.w3.org/2004/08/xop/include` and a `[local name]` of `Include`.</span></span>

2. <span data-ttu-id="79be0-318">Crie um pacote MIME vazio.</span><span class="sxs-lookup"><span data-stu-id="79be0-318">Create an empty MIME package.</span></span>

3. <span data-ttu-id="79be0-319">Identifique dentro do XML infoset original os itens de informações de elemento a serem otimizados.</span><span class="sxs-lookup"><span data-stu-id="79be0-319">Identify within the Original XML Infoset the element information items to be optimized.</span></span> <span data-ttu-id="79be0-320">Para os itens a serem otimizados, os caracteres que compõem o `[children]` do item de informações do elemento devem estar na forma canônica de `xs:base64Binary` (consulte XSD-2, 3.2.16 base64Binary) e não devem conter nenhum caractere de espaço em branco anterior, embutido ou seguir o conteúdo que não seja de espaço em branco.</span><span class="sxs-lookup"><span data-stu-id="79be0-320">For the items to be optimized, the characters that make up the `[children]` of the element information item must be in the canonical form of `xs:base64Binary` (see XSD-2, 3.2.16 base64Binary) and must not contain any white-space characters preceding, inline with, or following the non-white-space content.</span></span>

4. <span data-ttu-id="79be0-321">Crie um envelope de XOP SOAP que seja uma cópia do envelope SOAP original, mas com os filhos de cada item de informações de elemento identificado na etapa anterior substituída por um `xop:Include` item de informações de elemento construído da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="79be0-321">Create an XOP SOAP Envelope that is a copy of the Original SOAP Envelope, but with the children of each element information item identified in the previous step replaced by an `xop:Include` element information item constructed as follows:</span></span>

    1. <span data-ttu-id="79be0-322">Transforme os caracteres substituídos em dados binários processando-os como dados codificados em base64.</span><span class="sxs-lookup"><span data-stu-id="79be0-322">Transform the replaced characters into binary data by processing them as base64-encoded data.</span></span>

    2. <span data-ttu-id="79be0-323">Gere um valor de cabeçalho Content-ID exclusivo que atenda aos requisitos R3133 e R3134.</span><span class="sxs-lookup"><span data-stu-id="79be0-323">Generate a unique Content-ID header value that satisfies requirements R3133 and R3134.</span></span>

    3. <span data-ttu-id="79be0-324">Gere um cabeçalho MIME de codificação de transferência de conteúdo com o valor binário.</span><span class="sxs-lookup"><span data-stu-id="79be0-324">Generate a Content-Transfer-Encoding MIME header with the value binary.</span></span>

    4. <span data-ttu-id="79be0-325">Se o item de informações do elemento que está sendo otimizado (o [pai] do item de informações do elemento recentemente inserido `xop:Include` ) tiver um `xmime:contentType` item de informações de atributo, gere um cabeçalho MIME de tipo de conteúdo com o valor do `xmime:contentType` atributo.</span><span class="sxs-lookup"><span data-stu-id="79be0-325">If the element information item being optimized (the [parent] of the newly inserted `xop:Include` element information item) has an `xmime:contentType` attribute information item, generate a Content-Type MIME header with the value of the `xmime:contentType` attribute.</span></span>

    5. <span data-ttu-id="79be0-326">Gere uma nova parte Binary binária com o conteúdo formado por dados binários decodificados a partir dos caracteres substituídos processados como Base64, cabeçalho Content-ID do cabeçalho 4B, Content-Transfer-Encoding do cabeçalho 4C, Content-Type, se gerado na etapa 4D.</span><span class="sxs-lookup"><span data-stu-id="79be0-326">Generate a new binary MIME part with content formed by binary data decoded from the replaced characters processed as base64, Content-ID header from 4b, Content- Transfer-Encoding header from 4c, Content-Type header if generated in step 4d.</span></span>

    6. <span data-ttu-id="79be0-327">Adicione um `href` atributo ao `xop:Include` elemento com o valor CID: URI derivado do valor de cabeçalho Content-ID gerado na etapa 4B.</span><span class="sxs-lookup"><span data-stu-id="79be0-327">Add an `href` attribute to the `xop:Include` element with the value cid: uri derived from Content-ID header value generated in step 4b.</span></span> <span data-ttu-id="79be0-328">Remova o "" caracteres de circunscrição \<" and "> , a URL-escape a cadeia de caracteres restante e adicione o prefixo `cid:` .</span><span class="sxs-lookup"><span data-stu-id="79be0-328">Remove the enclosing "\<" and ">" characters, URL-escape the remaining string, and add the prefix `cid:`.</span></span> <span data-ttu-id="79be0-329">O seguinte conjunto mínimo de caracteres deve ser ignorado por RFC1738 e RFC2396.</span><span class="sxs-lookup"><span data-stu-id="79be0-329">The following minimum character set is required to be escaped by RFC1738 and RFC2396.</span></span> <span data-ttu-id="79be0-330">Outros caracteres podem ter escape.</span><span class="sxs-lookup"><span data-stu-id="79be0-330">Other characters can be escaped.</span></span>

        ```
        Hexadecimal 00-1F , 7F, 20, "<" | ">" | "#" | "%" | <">
        "{" | "}" | "|" | "\" | "^" | "[" | "]" | "`" | "~" | "^"
        ```

5. <span data-ttu-id="79be0-331">Crie uma parte raiz MIME com o envelope XOP SOAP da etapa 4.</span><span class="sxs-lookup"><span data-stu-id="79be0-331">Create a root MIME part with the XOP SOAP Envelope from step 4.</span></span>

6. <span data-ttu-id="79be0-332">Grave os cabeçalhos HTTP, incluindo o cabeçalho Content-Type HTTP.</span><span class="sxs-lookup"><span data-stu-id="79be0-332">Write the HTTP headers, including the HTTP Content-Type header.</span></span>

7. <span data-ttu-id="79be0-333">Grave o pacote MIME.</span><span class="sxs-lookup"><span data-stu-id="79be0-333">Write the MIME package.</span></span>

#### <a name="processing-mtom-messages"></a><span data-ttu-id="79be0-334">Processando mensagens MTOM</span><span class="sxs-lookup"><span data-stu-id="79be0-334">Processing MTOM messages</span></span>
<span data-ttu-id="79be0-335">O processamento de uma mensagem MTOM é o inverso exato do processo descrito na seção "gerando mensagens MTOM" anteriores:</span><span class="sxs-lookup"><span data-stu-id="79be0-335">Processing of an MTOM message is the exact reverse of the process described in the preceding "Generating MTOM messages" section:</span></span>

1. <span data-ttu-id="79be0-336">Verifique se a parte MIME raiz tem o tipo de conteúdo `application/xop+xml` .</span><span class="sxs-lookup"><span data-stu-id="79be0-336">Ensure the root MIME part has the Content-Type `application/xop+xml`.</span></span>

2. <span data-ttu-id="79be0-337">Construa um envelope SOAP analisando a parte MIME raiz do pacote como um documento XML.</span><span class="sxs-lookup"><span data-stu-id="79be0-337">Construct a SOAP Envelope by parsing the root MIME part of the package as an XML document.</span></span> <span data-ttu-id="79be0-338">A codificação de caracteres é determinada pelo `charset` parâmetro do tipo de conteúdo da parte MIME raiz.</span><span class="sxs-lookup"><span data-stu-id="79be0-338">Character encoding is determined by the `charset` parameter of the Content-Type of the root MIME part.</span></span>

3. <span data-ttu-id="79be0-339">Para cada item de informações de elemento no envelope SOAP construído, que tem, como o único membro de sua propriedade [Children], um `xop:Include` item de informações do elemento:</span><span class="sxs-lookup"><span data-stu-id="79be0-339">For each element information item in the constructed SOAP Envelope, which has, as the sole member of its [children] property, an `xop:Include` element information item:</span></span>

    1. <span data-ttu-id="79be0-340">Remova o `cid:` prefixo e desescape todas as sequências de escape URI (RFC 2396) no valor do `@href` atributo do `xop:Include` elemento.</span><span class="sxs-lookup"><span data-stu-id="79be0-340">Remove the `cid:` prefix and unescape all URI-escape sequences (RFC 2396) in the value of the `@href` attribute of the `xop:Include` element.</span></span> <span data-ttu-id="79be0-341">Coloque a cadeia de caracteres de resultado em " \<", "> ".</span><span class="sxs-lookup"><span data-stu-id="79be0-341">Enclose the result string in "\<", ">".</span></span>

    2. <span data-ttu-id="79be0-342">Localize a parte MIME com o valor de cabeçalho Content-ID que corresponde à cadeia de caracteres derivada na etapa 3a.</span><span class="sxs-lookup"><span data-stu-id="79be0-342">Locate the MIME part with the Content-ID header value that matches the string derived in step 3a.</span></span>

    3. <span data-ttu-id="79be0-343">Substitua o `xop:Include` item de informações do elemento que aparece na `children` propriedade de cada item com os itens de informações de caractere que representam a codificação canônica Base64 (consulte XSD-2, 3.2.16 base64Binary) do corpo da entidade da parte MIME identificada na etapa 3B (substitua efetivamente o `xop:Include` item de informações do elemento pelos dados reconstruídos da parte do pacote).</span><span class="sxs-lookup"><span data-stu-id="79be0-343">Replace the `xop:Include` element information item that appears in the `children` property of each item with the character information items that represent the canonical base64 encoding (see XSD-2, 3.2.16 base64Binary) of the entity body of the MIME part identified in step 3b (effectively replace the `xop:Include` element information item with the data reconstructed from the package part).</span></span>

#### <a name="http-content-type-header"></a><span data-ttu-id="79be0-344">Cabeçalho de tipo de conteúdo HTTP</span><span class="sxs-lookup"><span data-stu-id="79be0-344">HTTP Content-Type Header</span></span>
<span data-ttu-id="79be0-345">Veja a seguir uma lista de esclarecimentos do WCF para o formato do cabeçalho de tipo de conteúdo HTTP de uma mensagem codificada por MTOM SOAP 1. x derivada dos requisitos declarados na própria especificação MTOM e são derivados de MTOM e RFC 2387.</span><span class="sxs-lookup"><span data-stu-id="79be0-345">The following is a list of WCF clarifications for the format of the HTTP Content-Type header of a SOAP 1.x MTOM-encoded message derived from requirements stated in the MTOM specification itself and are derived from MTOM and RFC 2387.</span></span>

- <span data-ttu-id="79be0-346">R4131: um cabeçalho de tipo de conteúdo HTTP deve ter o valor de várias partes/relacionadas (não diferencia maiúsculas de minúsculas) e seus parâmetros.</span><span class="sxs-lookup"><span data-stu-id="79be0-346">R4131: An HTTP Content-Type header must have the value of multipart/related (case-insensitive) and its parameters.</span></span> <span data-ttu-id="79be0-347">Os nomes de parâmetro não diferenciam maiúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="79be0-347">Parameter names are case-insensitive.</span></span> <span data-ttu-id="79be0-348">A ordem dos parâmetros não é significativa.</span><span class="sxs-lookup"><span data-stu-id="79be0-348">Parameter order is not significant.</span></span>

- <span data-ttu-id="79be0-349">O BNF (formulário Backus-Naur) completo do cabeçalho Content-Type para mensagens MIME está listado na RFC 2045, seção 5,1.</span><span class="sxs-lookup"><span data-stu-id="79be0-349">The full Backus-Naur Form (BNF) of the Content-Type header for MIME messages is listed in RFC 2045, section 5.1.</span></span>

- <span data-ttu-id="79be0-350">R4132: um cabeçalho de tipo de conteúdo HTTP deve ter um parâmetro de tipo com o valor `application/xop+xml` entre aspas duplas.</span><span class="sxs-lookup"><span data-stu-id="79be0-350">R4132: An HTTP Content-Type header must have a type parameter with the value `application/xop+xml` enclosed in double quotation marks.</span></span>

<span data-ttu-id="79be0-351">Embora a necessidade de usar aspas duplas não seja explícita no RFC 2387, o texto observa que todos os parâmetros de tipo de mídia com diversas partes/relacionadas provavelmente contenham caracteres reservados como " \@ " ou "/" e, portanto, precisam de aspas duplas.</span><span class="sxs-lookup"><span data-stu-id="79be0-351">While the requirement to use double quotation marks is not explicit in RFC 2387, the text observes that all of the multipart/related media type parameters most likely contain reserved characters like "\@" or "/" and therefore need double quotation marks.</span></span>

- <span data-ttu-id="79be0-352">R4133: um cabeçalho de tipo de conteúdo HTTP deve ter um parâmetro de inicialização com o valor do cabeçalho Content-ID da parte MIME que contém o envelope SOAP 1. x, entre aspas duplas.</span><span class="sxs-lookup"><span data-stu-id="79be0-352">R4133: An HTTP Content-Type header should have a start parameter with the value of the Content-ID header of the MIME part that contains the SOAP 1.x Envelope, enclosed in double quotation marks.</span></span> <span data-ttu-id="79be0-353">Se o parâmetro Start for omitido, a primeira parte MIME deverá conter o envelope SOAP 1. x.</span><span class="sxs-lookup"><span data-stu-id="79be0-353">If the start parameter is omitted, the first MIME part must contain the SOAP 1.x Envelope.</span></span>

- <span data-ttu-id="79be0-354">R4134: um cabeçalho de tipo de conteúdo HTTP para uma mensagem codificada de MTOM SOAP 1,1 deve incluir o parâmetro Start-info com o valor de text/xml, entre aspas duplas.</span><span class="sxs-lookup"><span data-stu-id="79be0-354">R4134: An HTTP Content-Type header for a SOAP 1.1 MTOM encoded message must include the start-info parameter with the value of text/xml, enclosed in double quotation marks.</span></span>

- <span data-ttu-id="79be0-355">R4135: um cabeçalho de tipo de conteúdo HTTP para uma mensagem codificada em MTOM SOAP 1,2 deve incluir o parâmetro Start-info com o valor de `application/soap+xml` , entre aspas duplas.</span><span class="sxs-lookup"><span data-stu-id="79be0-355">R4135: An HTTP Content-Type header for a SOAP 1.2 MTOM-encoded message must include the start-info parameter with the value of `application/soap+xml`, enclosed in double quotation marks.</span></span>

- <span data-ttu-id="79be0-356">R4136: cabeçalho Content-Type de HTTP para uma mensagem codificada em MTOM SOAP 1. x deve ter o parâmetro de limite com o valor (entre aspas duplas) que corresponde ao limite MIME BNF definido no RFC 2046, seção 5.1.1</span><span class="sxs-lookup"><span data-stu-id="79be0-356">R4136: HTTP Content-Type header for a SOAP 1.x MTOM-encoded message must have the boundary parameter with the value (enclosed in double quotation marks) that matches the MIME boundary BNF defined in RFC 2046, section 5.1.1</span></span>

    ```
    boundary := 0*69<bchars> bcharsnospace
    bchars := bcharsnospace / " "
    bcharsnospace :=    DIGIT / ALPHA / "'" / "(" / ")" / "+"
                        / "_" / "," / "-" / "." / "/" / ":" / "=" / "?"
    ```

     <span data-ttu-id="79be0-357">Exemplos:</span><span class="sxs-lookup"><span data-stu-id="79be0-357">Examples:</span></span>

     <span data-ttu-id="79be0-358">CORRIGI</span><span class="sxs-lookup"><span data-stu-id="79be0-358">CORRECT</span></span>

    ```http
    Content-Type: multipart/related; type="application/xop+xml";start=" <part0@tempuri.org>";boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1";start-info="text/xml"
    ```

     <span data-ttu-id="79be0-359">CORRIGI</span><span class="sxs-lookup"><span data-stu-id="79be0-359">CORRECT</span></span>

    ```http
    Content-Type: Multipart/Related; type="application/xop+xml";start-info="text/xml";boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1"
    ```

     <span data-ttu-id="79be0-360">INCORRETO</span><span class="sxs-lookup"><span data-stu-id="79be0-360">INCORRECT</span></span>

    ```http
    Content-Type: Multipart/Related; type=application/xop+xml;start=" <part0@tempuri.org>";start-info="text/xml";boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1"
    ```

#### <a name="infoset-mime-part"></a><span data-ttu-id="79be0-361">Parte MIME do infoset</span><span class="sxs-lookup"><span data-stu-id="79be0-361">Infoset MIME Part</span></span>
<span data-ttu-id="79be0-362">O envelope SOAP 1. x é encapsulado como uma parte raiz do pacote de MIME XOP e geralmente é chamado de `infoset` parte.</span><span class="sxs-lookup"><span data-stu-id="79be0-362">The SOAP 1.x Envelope is encapsulated as a root part of the XOP MIME package and is often called the `infoset` part.</span></span>

- <span data-ttu-id="79be0-363">R4141: o envelope SOAP 1. x deve ser encapsulado como uma parte raiz do pacote do XOP MIME, chamado de `infoset` parte e referenciado do tipo de conteúdo http.</span><span class="sxs-lookup"><span data-stu-id="79be0-363">R4141: The SOAP 1.x Envelope must be encapsulated as a root part of the XOP MIME package, called the `infoset` part and referenced from the HTTP Content-Type.</span></span>

- <span data-ttu-id="79be0-364">R4142: a `Infoset` parte SOAP deve incluir os seguintes cabeçalhos MIME: `Content-ID` , `Content-Transfer-Encoding` , e `Content-Type` .</span><span class="sxs-lookup"><span data-stu-id="79be0-364">R4142: The SOAP `Infoset` part must include the following MIME headers: `Content-ID`, `Content-Transfer-Encoding`, and `Content-Type`.</span></span>

<span data-ttu-id="79be0-365">O formato do cabeçalho Content-ID é definido pela RFC 2045 como</span><span class="sxs-lookup"><span data-stu-id="79be0-365">The format of the Content-ID header is defined by RFC 2045 as</span></span>

```
"Content-ID" ":" msg-id
```

<span data-ttu-id="79be0-366">onde `msg-id` é definido no rfc 2822 (que substitui a rfc 822, referenciada na rfc 2045) como:</span><span class="sxs-lookup"><span data-stu-id="79be0-366">where `msg-id` is defined in RFC 2822 (that supersedes RFC 822, referenced in RFC 2045) as:</span></span>

```
msg-id    =       [CFWS] "<" id-left "@" id-right ">" [CFWS]
```

<span data-ttu-id="79be0-367">e é efetivamente um endereço de email entre " \<" and  "> ".</span><span class="sxs-lookup"><span data-stu-id="79be0-367">and is effectively an email address enclosed within "\<" and  ">".</span></span> <span data-ttu-id="79be0-368">O `[CFWS]` prefixo e o sufixo foram adicionados ao RFC 2822 para transportar comentários e não devem ser usados para preservar a interoperabilidade.</span><span class="sxs-lookup"><span data-stu-id="79be0-368">The `[CFWS]` prefix and suffix were added in RFC 2822 to carry comments and should not be used to preserve interoperability.</span></span>

<span data-ttu-id="79be0-369">R4143: o valor do cabeçalho Content-ID para a parte MIME infoset deve seguir a `msg-id` produção do RFC 2822 com as `[CFWS]` partes de prefixo e sufixo omitidas.</span><span class="sxs-lookup"><span data-stu-id="79be0-369">R4143: The value of the Content-ID header for the Infoset MIME part must follow `msg-id` production from RFC 2822 with the `[CFWS]` prefix and suffix parts omitted.</span></span>

<span data-ttu-id="79be0-370">Várias implementações de MIME requisitos relaxados para o valor incluído em " \<" and "> " para serem um endereço de email e usados `absoluteURI` entre " \<" , "> ", além do endereço de email.</span><span class="sxs-lookup"><span data-stu-id="79be0-370">A number of MIME implementations relaxed requirements for the value enclosed within "\<" and ">" to be an email address and used `absoluteURI` enclosed in "\<" , ">" in addition to the email address.</span></span> <span data-ttu-id="79be0-371">Esta versão do WCF usa valores do cabeçalho MIME Content-ID do formulário:</span><span class="sxs-lookup"><span data-stu-id="79be0-371">This version of WCF uses values of the Content-ID MIME header of the form:</span></span>

```
Content-ID: <http://tempuri.org/0>
```

<span data-ttu-id="79be0-372">R4144: os processadores MTOM devem aceitar valores de cabeçalho Content-ID que correspondam aos seguintes relaxados `msg-id` .</span><span class="sxs-lookup"><span data-stu-id="79be0-372">R4144: MTOM processors should accept Content-ID header values that match the following relaxed `msg-id`.</span></span>

```
msg-id-relaxed =     [CFWS] "<" (absoluteURI | mail-address) ">" [CFWS]
mail-address   =     id-left "@" id-right
```

<span data-ttu-id="79be0-373">MIME (RFC 2045) fornece o cabeçalho Content-Transfer-Encoding para comunicar a codificação do conteúdo da parte MIME.</span><span class="sxs-lookup"><span data-stu-id="79be0-373">MIME (RFC 2045) provides the Content-Transfer-Encoding header to communicate encoding of the content of the MIME part.</span></span> <span data-ttu-id="79be0-374">O padrão definido para a codificação de transferência de conteúdo é de 7 bits, o que não é adequado para a maioria das mensagens SOAP, portanto, o cabeçalho de codificação de transferência de conteúdo é necessário para uma interoperabilidade maior:</span><span class="sxs-lookup"><span data-stu-id="79be0-374">The default defined for Content-Transfer-Encoding is 7-bit, which is not suitable for most SOAP messages, so the Content-Transfer-Encoding header is needed for greater interoperability:</span></span>

- <span data-ttu-id="79be0-375">R4145: a parte do infoset SOAP deve conter o cabeçalho Content-Transfer-Encoding.</span><span class="sxs-lookup"><span data-stu-id="79be0-375">R4145: The SOAP Infoset part must contain the Content-Transfer-Encoding header.</span></span>

- <span data-ttu-id="79be0-376">R4146: se a codificação de caracteres de envelope SOAP for UTF-8, o valor do cabeçalho Content-Transfer-Encoding deverá ser de 8 bits.</span><span class="sxs-lookup"><span data-stu-id="79be0-376">R4146: If the SOAP Envelope character encoding is UTF-8, the value of the Content-Transfer-Encoding header must be 8-bit.</span></span>

- <span data-ttu-id="79be0-377">R4147: se a codificação de caracteres de envelope SOAP for UTF-16, o valor do cabeçalho Content-Transfer-Encoding deverá ser binário.</span><span class="sxs-lookup"><span data-stu-id="79be0-377">R4147: If the SOAP Envelope character encoding is UTF-16, the value of the Content-Transfer-Encoding header must be binary.</span></span>

- <span data-ttu-id="79be0-378">De acordo com [XOP] seção 5,</span><span class="sxs-lookup"><span data-stu-id="79be0-378">According to [XOP] section 5,</span></span>

- <span data-ttu-id="79be0-379">R4148: a parte do infoset SOAP 1.1 deve conter o cabeçalho Content-Type com o tipo de mídia Application/XOP + XML e os parâmetros Type = "text/xml" e charset</span><span class="sxs-lookup"><span data-stu-id="79be0-379">R4148: SOAP1.1 Infoset part must contain Content-Type header with media type application/xop+xml and parameters type="text/xml" and charset</span></span>

    ```http
    Content-Type: application/xop+xml;
                  charset=utf-8;type="text/xml"
    ```

- <span data-ttu-id="79be0-380">R4149: a parte do infoset SOAP 1,2 deve conter o cabeçalho Content-Type com tipo `application/xop+xml` de mídia e parâmetros Type = " `application/soap+xml` " e `charset` .</span><span class="sxs-lookup"><span data-stu-id="79be0-380">R4149: The SOAP 1.2 Infoset part must contain the Content-Type header with media type `application/xop+xml` and parameters type="`application/soap+xml`" and `charset`.</span></span>

    ```http
    Content-Type: application/xop+xml;
                  charset=utf-8;type="application/soap+xml"
    ```

     <span data-ttu-id="79be0-381">Embora XOP defina o `charset` parâmetro para `application/xop+xml` ser opcional, ele é necessário para interoperabilidade semelhante ao requisito 1,1 de BP no `charset` parâmetro para o `text/xml` tipo de mídia.</span><span class="sxs-lookup"><span data-stu-id="79be0-381">While XOP defines the `charset` parameter for `application/xop+xml` to be optional, it is needed for interoperability similar to the BP 1.1 requirement on the `charset` parameter for the `text/xml` media type.</span></span>

- <span data-ttu-id="79be0-382">R41410: os `type` `charset` parâmetros e devem estar presentes no cabeçalho Content-Type da parte SOAP 1. x infoset.</span><span class="sxs-lookup"><span data-stu-id="79be0-382">R41410: The `type` and `charset` parameters must be present on the Content-Type header of the SOAP 1.x Infoset part.</span></span>

#### <a name="wcf-endpoint-support-for-mtom"></a><span data-ttu-id="79be0-383">Suporte de ponto de extremidade WCF para MTOM</span><span class="sxs-lookup"><span data-stu-id="79be0-383">WCF Endpoint Support for MTOM</span></span>
<span data-ttu-id="79be0-384">A finalidade do MTOM é codificar uma mensagem SOAP para otimizar os dados codificados em base64.</span><span class="sxs-lookup"><span data-stu-id="79be0-384">The purpose of MTOM is to encode a SOAP message to optimize base64-encoded data.</span></span> <span data-ttu-id="79be0-385">Veja a seguir uma lista de restrições:</span><span class="sxs-lookup"><span data-stu-id="79be0-385">The following is a list of constraints:</span></span>

- <span data-ttu-id="79be0-386">R4151: qualquer item de informações de elemento que contenha dados codificados em base64 pode ser otimizado.</span><span class="sxs-lookup"><span data-stu-id="79be0-386">R4151: Any element information item that contains base64-encoded data may be optimized.</span></span>

- <span data-ttu-id="79be0-387">B4152: o WCF otimiza itens de informações de elemento que contêm dados codificados na Base64 e excede 1024 bytes de comprimento.</span><span class="sxs-lookup"><span data-stu-id="79be0-387">B4152: WCF optimizes element information items that contain base64-encoded data and exceed 1024 bytes in length.</span></span>

<span data-ttu-id="79be0-388">Um ponto de extremidade WCF configurado para usar o MTOM sempre enviará mensagens codificadas em MTOM.</span><span class="sxs-lookup"><span data-stu-id="79be0-388">A WCF endpoint configured to use MTOM will always send MTOM-encoded messages.</span></span> <span data-ttu-id="79be0-389">Mesmo que nenhuma peça atenda aos critérios necessários, a mensagem ainda é codificada por MTOM (serializada como um pacote MIME com uma única parte MIME que contém o envelope SOAP).</span><span class="sxs-lookup"><span data-stu-id="79be0-389">Even if no parts meet the required criteria, the message is still MTOM-encoded (serialized as a MIME package with a single MIME part containing the SOAP envelope).</span></span>

### <a name="ws-policy-assertion-for-mtom"></a><span data-ttu-id="79be0-390">Declaração de WS-Policy para MTOM</span><span class="sxs-lookup"><span data-stu-id="79be0-390">WS-Policy Assertion for MTOM</span></span>
<span data-ttu-id="79be0-391">O WCF usa a seguinte declaração de política para indicar o uso de MTOM pelo ponto de extremidade:</span><span class="sxs-lookup"><span data-stu-id="79be0-391">WCF uses the following policy assertion to indicate MTOM usage by endpoint:</span></span>

```xml
<wsoma:OptimizedMimeSerialization />
```

- <span data-ttu-id="79be0-392">R4211: a declaração de política anterior tem um assunto de política de ponto de extremidade e especifica que todas as mensagens enviadas e recebidas do ponto de extremidade devem ser otimizadas usando MTOM.</span><span class="sxs-lookup"><span data-stu-id="79be0-392">R4211: The preceding policy assertion has an Endpoint Policy Subject and specifies that all messages sent to and received from the endpoint must be optimized using MTOM.</span></span>

- <span data-ttu-id="79be0-393">B4212: quando configurado para usar a otimização de MTOM, um ponto de extremidade WCF adiciona uma declaração de política de MTOM à política anexada ao correspondente `wsdl:binding` .</span><span class="sxs-lookup"><span data-stu-id="79be0-393">B4212: When configured to use MTOM optimization, an WCF endpoint adds an MTOM Policy assertion to the policy attached to the corresponding `wsdl:binding`.</span></span>

### <a name="composition-with-ws-security"></a><span data-ttu-id="79be0-394">Composição com WS-Security</span><span class="sxs-lookup"><span data-stu-id="79be0-394">Composition with WS-Security</span></span>
<span data-ttu-id="79be0-395">MTOM é um mecanismo de codificação semelhante a `text/xml` e XML binário do WCF.</span><span class="sxs-lookup"><span data-stu-id="79be0-395">MTOM is an encoding mechanism that is similar to `text/xml` and WCF Binary XML.</span></span> <span data-ttu-id="79be0-396">O MTOM oferece uma composição natural com o WS-Security e outros protocolos WS-\*: uma mensagem protegida usando o WS-Security pode ser otimizada usando MTOM.</span><span class="sxs-lookup"><span data-stu-id="79be0-396">MTOM offers natural composition with WS-Security and other WS-\* protocols: a message secured using WS-Security can be optimized using MTOM.</span></span>

### <a name="examples"></a><span data-ttu-id="79be0-397">Exemplos</span><span class="sxs-lookup"><span data-stu-id="79be0-397">Examples</span></span>

#### <a name="wcf-soap-11-message-encoded-using-mtom"></a><span data-ttu-id="79be0-398">Mensagem do WCF SOAP 1,1 codificada usando MTOM</span><span class="sxs-lookup"><span data-stu-id="79be0-398">WCF SOAP 1.1 Message Encoded Using MTOM</span></span>

```http
POST http://131.107.72.15/Mtom/svc/service.svc/Soap11MtomUTF8 HTTP/1.1
SOAPAction: "http://xmlsoap.org/echoBinaryAsString"
Content-Type: multipart/related;type="application/xop+xml";
              start="<http://tempuri.org/0>";start-info="text/xml";
       boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1"
Host: 131.107.72.15
Content-Length: 1501
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1
Content-ID: <http://tempuri.org/0>
Content-Transfer-Encoding: 8bit
Content-Type: application/xop+xml;charset=utf-8;type="text/xml"
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Body>
    <EchoBinaryAsString xmlns="http://xmlsoap.org/Ping">
      <array>
        <xop:Include
         href="cid:http%3A%2F%2Ftempuri.org%2F1%2F632618206521093670"
         xmlns:xop="http://www.w3.org/2004/08/xop/include"/>
      </array>
    </EchoBinaryAsString>
  </s:Body>
</s:Envelope>
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1
Content-ID: <http://tempuri.org/1/632618206521093670>
Content-Transfer-Encoding: binary
Content-Type: application/octet-stream
…Binary Content..
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1
```

#### <a name="wcf-secure-soap-12-message-encoded-using-mtom"></a><span data-ttu-id="79be0-399">Mensagem SMB Secure SOAP 1,2 codificada usando MTOM</span><span class="sxs-lookup"><span data-stu-id="79be0-399">WCF Secure SOAP 1.2 Message Encoded Using MTOM</span></span>
<span data-ttu-id="79be0-400">Neste exemplo, uma mensagem é codificada usando MTOM e SOAP 1,2 que é protegido usando o WS-Security.</span><span class="sxs-lookup"><span data-stu-id="79be0-400">In this example, a message is encoded using MTOM and SOAP 1.2 that is protected using WS-Security.</span></span> <span data-ttu-id="79be0-401">As partes binárias identificadas para codificação são o conteúdo do `BinarySecurityToken` , `CipherValue` do `EncryptedData` correspondente à assinatura criptografada e ao corpo criptografado.</span><span class="sxs-lookup"><span data-stu-id="79be0-401">The binary parts identified for encoding are the contents of the `BinarySecurityToken`, `CipherValue` of the `EncryptedData` corresponding to the encrypted signature and encrypted body.</span></span> <span data-ttu-id="79be0-402">Observe que o `CipherValue` de `EncryptedKey` não foi identificado para otimização pelo WCF, pois seu comprimento é menor que 1024 bytes.</span><span class="sxs-lookup"><span data-stu-id="79be0-402">Note that the `CipherValue` of the `EncryptedKey` was not identified for optimization by WCF, because its length is less then 1024 bytes.</span></span>

```http
POST http://131.107.72.15/Mtom/service.svc/Soap12MtomSecureSignEncrypt HTTP/1.1
Content-Type: multipart/related; type="application/xop+xml";
              start="<http://tempuri.org/0>";
            boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=3";
              start-info="application/soap+xml";
              action="http://xmlsoap.org/echoBinaryAsString"
Host: 131.107.72.15
Content-Length: 1941
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=3
Content-ID: <http://tempuri.org/0>
Content-Transfer-Encoding: 8bit
Content-Type: application/xop+xml;charset=utf-8;type="application/soap+xml"
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/" xmlns:u="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">
  <s:Header>
    <o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">
      <u:Timestamp u:Id="uuid-4d4ee765-5717-4d53-9ac9-99bddc07df6c-5">
        <u:Created>2005-09-09T06:57:32.488Z</u:Created>
        <u:Expires>2005-09-09T07:02:32.488Z</u:Expires>
      </u:Timestamp>
      <o:BinarySecurityToken u:Id="uuid-4d4ee765-5717-4d53-9ac9-99bddc07df6c-2" ValueType="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-x509-token-profile-1.0#X509v3" EncodingType="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0#Base64Binary">
        <xop:Include href="cid:http%3A%2F%2Ftempuri.org%2F1%2F632618206525089430" xmlns:xop="http://www.w3.org/2004/08/xop/include"/>
      </o:BinarySecurityToken>
      <e:EncryptedKey Id="_1" xmlns:e="http://www.w3.org/2001/04/xmlenc#">
        <e:EncryptionMethod Algorithm="http://www.w3.org/2001/04/xmlenc#rsa-oaep-mgf1p"/>
        <KeyInfo xmlns="http://www.w3.org/2000/09/xmldsig#">
          <o:SecurityTokenReference>
            <o:KeyIdentifier ValueType="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-x509-token-profile-1.0#X509SubjectKeyIdentifier">Xeg55vRyK3ZhAEhEf+YT0z986L0=</o:KeyIdentifier>
          </o:SecurityTokenReference>
        </KeyInfo>
        <e:CipherData>          <e:CipherValue>oQfpxwT8/SAGyZQzKE2b4yO6dXuQj7pwJ+5CGL3Rf7C06bQ5ttMoQ9GLJcQYkXTzin+WwHEgs5bj5ml9HKTW9QAU5JJ6lksdymmQvWP5ZtGPBVchO4sofEGoCKmBiZL/DYS/cnbzgnc/3a6NYnc10y2fWGaGLiqa00zijAw7o0Y=</e:CipherValue>
        </e:CipherData>
      </e:EncryptedKey>
      <c:DerivedKeyToken u:Id="_2" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc">
        <o:SecurityTokenReference>
          <o:Reference URI="#_1"/>
        </o:SecurityTokenReference>
        <c:Nonce>OrEPRX7fISIS4sXYWPMv3g==</c:Nonce>
      </c:DerivedKeyToken>
      <e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#">
        <e:DataReference URI="#_3"/>
        <e:DataReference URI="#_4"/>
      </e:ReferenceList>
      <e:EncryptedData Id="_4" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#">
        <e:EncryptionMethod Algorithm="http://www.w3.org/2001/04/xmlenc#aes256-cbc"/>
        <KeyInfo xmlns="http://www.w3.org/2000/09/xmldsig#">
          <o:SecurityTokenReference>
            <o:Reference URI="#_2"/>
          </o:SecurityTokenReference>
        </KeyInfo>
        <e:CipherData>
          <e:CipherValue>
            <xop:Include href="cid:http%3A%2F%2Ftempuri.org%2F2%2F632618206525089430" xmlns:xop="http://www.w3.org/2004/08/xop/include"/>
          </e:CipherValue>
        </e:CipherData>
      </e:EncryptedData>
    </o:Security>
  </s:Header>
  <s:Body u:Id="_0">
    <e:EncryptedData Id="_3" Type="http://www.w3.org/2001/04/xmlenc#Content" xmlns:e="http://www.w3.org/2001/04/xmlenc#">
      <e:EncryptionMethod Algorithm="http://www.w3.org/2001/04/xmlenc#aes256-cbc"/>
      <KeyInfo xmlns="http://www.w3.org/2000/09/xmldsig#">
        <o:SecurityTokenReference xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">
          <o:Reference URI="#_2"/>
        </o:SecurityTokenReference>
      </KeyInfo>
      <e:CipherData>
        <e:CipherValue>
          <xop:Include href="cid:http%3A%2F%2Ftempuri.org%2F3%2F632618206525089430" xmlns:xop="http://www.w3.org/2004/08/xop/include"/>
        </e:CipherValue>
      </e:CipherData>
    </e:EncryptedData>
  </s:Body>
</s:Envelope>
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=3
Content-ID: <http://tempuri.org/1/632618206525089430>
Content-Transfer-Encoding: binary
Content-Type: application/octet-stream
...Binary content of BinarySecurityToken - X509 Certificate...
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=3
Content-ID: <http://tempuri.org/2/632618206525089430>
Content-Transfer-Encoding: binary
Content-Type: application/octet-stream
...Binary serialization of the encrypted primary signature...
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=3
Content-ID: <http://tempuri.org/3/632618206525089430>
Content-Transfer-Encoding: binary
Content-Type: application/octet-stream
...Binary serialization of the encrypted Body...
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=3--
```
