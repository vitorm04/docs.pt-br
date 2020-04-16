---
title: Protocolos de mensagens
ms.date: 03/30/2017
ms.assetid: 5b20bca7-87b3-4c8f-811b-f215b5987104
ms.openlocfilehash: 814347c77b54c4450aabf0a4f3966df223360663
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463826"
---
# <a name="messaging-protocols"></a><span data-ttu-id="4191b-102">Protocolos de mensagens</span><span class="sxs-lookup"><span data-stu-id="4191b-102">Messaging Protocols</span></span>

<span data-ttu-id="4191b-103">A pilha de canais da Windows Communication Foundation (WCF) emprega canais de codificação e transporte para transformar a representação de mensagens internas em seu formato de fio e enviá-la usando um transporte específico.</span><span class="sxs-lookup"><span data-stu-id="4191b-103">The Windows Communication Foundation (WCF) channel stack employs encoding and transport channels to transform internal message representation into its wire format and send it by using a particular transport.</span></span> <span data-ttu-id="4191b-104">O transporte mais comum usado para interoperabilidade de serviços Web é http, e as codificações mais comuns usadas pelos serviços da Web são SOAP 1.1, SOAP 1.2 e Message Transmission Optimization Mechanism (MTOM).</span><span class="sxs-lookup"><span data-stu-id="4191b-104">The most common transport used for Web services interoperability is HTTP, and the most common encodings used by Web services are XML-based SOAP 1.1, SOAP 1.2, and Message Transmission Optimization Mechanism (MTOM).</span></span>

<span data-ttu-id="4191b-105">Este tópico abrange detalhes de implementação do <xref:System.ServiceModel.Channels.HttpTransportBindingElement>WCF para os seguintes protocolos empregados por .</span><span class="sxs-lookup"><span data-stu-id="4191b-105">This topic covers WCF implementation details for the following protocols employed by <xref:System.ServiceModel.Channels.HttpTransportBindingElement>.</span></span>

<span data-ttu-id="4191b-106">Especificação/documento:</span><span class="sxs-lookup"><span data-stu-id="4191b-106">Specification/document:</span></span>

- [<span data-ttu-id="4191b-107">HTTP 1.1</span><span class="sxs-lookup"><span data-stu-id="4191b-107">HTTP 1.1</span></span>](https://www.ietf.org/rfc/rfc2616.txt)
- <span data-ttu-id="4191b-108">[SOAP 1.1 HTTP Binding](https://www.w3.org/TR/2000/NOTE-SOAP-20000508), Seção 7</span><span class="sxs-lookup"><span data-stu-id="4191b-108">[SOAP 1.1 HTTP Binding](https://www.w3.org/TR/2000/NOTE-SOAP-20000508), Section 7</span></span>
- <span data-ttu-id="4191b-109">[ENCASABÃO 1.2 HTTP Vinculação](https://www.w3.org/TR/soap12-part2) Seção 7</span><span class="sxs-lookup"><span data-stu-id="4191b-109">[SOAP 1.2 HTTP Binding](https://www.w3.org/TR/soap12-part2) Section 7</span></span>

<span data-ttu-id="4191b-110">Este tópico abrange detalhes de implementação <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> do WCF para os seguintes protocolos que e empregam.</span><span class="sxs-lookup"><span data-stu-id="4191b-110">This topic covers WCF implementation details for the following protocols  that <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> and <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> employ.</span></span>

<span data-ttu-id="4191b-111">Especificação/Documento:</span><span class="sxs-lookup"><span data-stu-id="4191b-111">Specification/Document:</span></span>

- [<span data-ttu-id="4191b-112">XML</span><span class="sxs-lookup"><span data-stu-id="4191b-112">XML</span></span>](https://www.w3.org/TR/REC-xml)
- [<span data-ttu-id="4191b-113">SABÃO 1.1</span><span class="sxs-lookup"><span data-stu-id="4191b-113">SOAP 1.1</span></span>](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/)
- [<span data-ttu-id="4191b-114">SABÃO 1.2 Núcleo</span><span class="sxs-lookup"><span data-stu-id="4191b-114">SOAP 1.2 Core</span></span>](https://www.w3.org/TR/soap12-part1/)
- [<span data-ttu-id="4191b-115">WS-Addressing 2004/08</span><span class="sxs-lookup"><span data-stu-id="4191b-115">WS-Addressing 2004/08</span></span>](https://www.w3.org/Submission/2004/SUBM-ws-addressing-20040810/)
- [<span data-ttu-id="4191b-116">W3C Web Services Endereçando 1.0 - Núcleo</span><span class="sxs-lookup"><span data-stu-id="4191b-116">W3C Web Services Addressing 1.0 - Core</span></span>](https://www.w3.org/TR/2006/REC-ws-addr-core-20060509)
- [<span data-ttu-id="4191b-117">W3C Web Services Endereçando 1.0 - Encadernamento soap</span><span class="sxs-lookup"><span data-stu-id="4191b-117">W3C Web Services Addressing 1.0 - SOAP Binding</span></span>](https://www.w3.org/TR/2006/REC-ws-addr-soap-20060509)
- [<span data-ttu-id="4191b-118">W3C Web Services Endereçando 1.0 - WSDL Binding</span><span class="sxs-lookup"><span data-stu-id="4191b-118">W3C Web Services Addressing 1.0 - WSDL Binding</span></span>](https://www.w3.org/TR/2006/CR-ws-addr-wsdl-20060529/)
- [<span data-ttu-id="4191b-119">W3C Web Services Endereçando 1.0 - Metadados</span><span class="sxs-lookup"><span data-stu-id="4191b-119">W3C Web Services Addressing 1.0 - Metadata</span></span>](https://www.w3.org/TR/ws-addr-metadata/)
- [<span data-ttu-id="4191b-120">WSDL SOAP1.1 Vinculação</span><span class="sxs-lookup"><span data-stu-id="4191b-120">WSDL SOAP1.1 Binding</span></span>](https://www.w3.org/TR/wsdl/)
- [<span data-ttu-id="4191b-121">WSDL SOAP1.2 Vinculação</span><span class="sxs-lookup"><span data-stu-id="4191b-121">WSDL SOAP1.2 Binding</span></span>](https://www.w3.org/Submission/wsdl11soap12/)

<span data-ttu-id="4191b-122">Este tópico abrange detalhes de implementação <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> do WCF para os seguintes protocolos que empregam.</span><span class="sxs-lookup"><span data-stu-id="4191b-122">This topic covers WCF implementation details for the following protocols that <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> employs.</span></span>

<span data-ttu-id="4191b-123">Especificação/documento:</span><span class="sxs-lookup"><span data-stu-id="4191b-123">Specification/document:</span></span>

- [<span data-ttu-id="4191b-124">XOP</span><span class="sxs-lookup"><span data-stu-id="4191b-124">XOP</span></span>](https://www.w3.org/TR/xop10/)
- [<span data-ttu-id="4191b-125">MTOM + SABÃO 1.2 Ligação</span><span class="sxs-lookup"><span data-stu-id="4191b-125">MTOM + SOAP 1.2 Binding</span></span>](https://www.w3.org/TR/soap12-mtom/)
- [<span data-ttu-id="4191b-126">SABÃO MTOM 1.1 Ligação</span><span class="sxs-lookup"><span data-stu-id="4191b-126">MTOM SOAP 1.1 Binding</span></span>](https://www.w3.org/Submission/soap11mtom10/)
- [<span data-ttu-id="4191b-127">Afirmação da política do MTOM WS</span><span class="sxs-lookup"><span data-stu-id="4191b-127">MTOM WS-Policy Assertion</span></span>](https://www.w3.org/Submission/2006/SUBM-WS-MTOMPolicy-20061101/)

<span data-ttu-id="4191b-128">Os seguintes namespaces XML e prefixos associados são usados ao longo deste tópico:</span><span class="sxs-lookup"><span data-stu-id="4191b-128">The following XML namespaces and associated prefixes are used throughout this topic:</span></span>

| <span data-ttu-id="4191b-129">Prefixo</span><span class="sxs-lookup"><span data-stu-id="4191b-129">Prefix</span></span> | <span data-ttu-id="4191b-130">Identificador de recursos uniforme sinuoso (URI)</span><span class="sxs-lookup"><span data-stu-id="4191b-130">Namespace Uniform Resource Identifier (URI)</span></span> |
|------------|---------------------------------------------------|
| <span data-ttu-id="4191b-131">s11</span><span class="sxs-lookup"><span data-stu-id="4191b-131">s11</span></span> | `http://schemas.xmlsoap.org/soap/envelope` |
| <span data-ttu-id="4191b-132">s12</span><span class="sxs-lookup"><span data-stu-id="4191b-132">s12</span></span> |`http://www.w3.org/2003/05/soap-envelope` |
| <span data-ttu-id="4191b-133">Wsa</span><span class="sxs-lookup"><span data-stu-id="4191b-133">wsa</span></span> |`http://www.w3.org/2004/08/addressing` |
| <span data-ttu-id="4191b-134">wsam</span><span class="sxs-lookup"><span data-stu-id="4191b-134">wsam</span></span> |`http://www.w3.org/2007/05/addressing/metadata` |
| <span data-ttu-id="4191b-135">wsap</span><span class="sxs-lookup"><span data-stu-id="4191b-135">wsap</span></span> |`http://schemas.xmlsoap.org/ws/2004/09/policy/addressing` |
| <span data-ttu-id="4191b-136">wsa10</span><span class="sxs-lookup"><span data-stu-id="4191b-136">wsa10</span></span> |`http://www.w3.org/2005/08/addressing` |
| <span data-ttu-id="4191b-137">wsaw10</span><span class="sxs-lookup"><span data-stu-id="4191b-137">wsaw10</span></span> |`http://www.w3.org/2006/05/addressing/wsdl` |
| <span data-ttu-id="4191b-138">xop</span><span class="sxs-lookup"><span data-stu-id="4191b-138">xop</span></span> |`http://www.w3.org/2004/08/xop/include` |
| <span data-ttu-id="4191b-139">xmime</span><span class="sxs-lookup"><span data-stu-id="4191b-139">xmime</span></span> |`http://www.w3.org/2004/06/xmlmime`<br /><br /> `http://www.w3.org/2005/05/xmlmime` |
| <span data-ttu-id="4191b-140">Dp</span><span class="sxs-lookup"><span data-stu-id="4191b-140">dp</span></span> |`http://schemas.microsoft.com/net/2006/06/duplex` |

## <a name="soap-11-and-soap-12"></a><span data-ttu-id="4191b-141">SABÃO 1.1 e SABÃO 1.2</span><span class="sxs-lookup"><span data-stu-id="4191b-141">SOAP 1.1 and SOAP 1.2</span></span>

### <a name="envelope-and-processing-model"></a><span data-ttu-id="4191b-142">Modelo de Envelope e Processamento</span><span class="sxs-lookup"><span data-stu-id="4191b-142">Envelope and Processing Model</span></span>
<span data-ttu-id="4191b-143">O WCF implementa o processamento de envelopes SOAP 1.1 seguindo o Perfil Básico 1.1 (BP11) e o Perfil Básico 1.0 (SSBP10).</span><span class="sxs-lookup"><span data-stu-id="4191b-143">WCF implements SOAP 1.1 envelope processing following Basic Profile 1.1 (BP11) and Basic Profile 1.0 (SSBP10).</span></span> <span data-ttu-id="4191b-144">O processamento do envelope SOAP 1.2 é implementado após o SOAP12-Part1.</span><span class="sxs-lookup"><span data-stu-id="4191b-144">SOAP 1.2 Envelope processing is implemented following SOAP12-Part1.</span></span>

<span data-ttu-id="4191b-145">Esta seção explica certas escolhas de implementação tomadas pelo WCF em relação ao BP11 e AO SOAP12-Part1.</span><span class="sxs-lookup"><span data-stu-id="4191b-145">This section explains certain implementation choices taken by WCF with regard to BP11 and SOAP12-Part1.</span></span>

#### <a name="mandatory-header-processing"></a><span data-ttu-id="4191b-146">Processamento obrigatório do cabeçalho</span><span class="sxs-lookup"><span data-stu-id="4191b-146">Mandatory Header Processing</span></span>
<span data-ttu-id="4191b-147">O WCF segue as regras `mustUnderstand` para o processamento de cabeçalhos marcados nas especificações SOAP 1.1 e SOAP 1.2, com as seguintes variações.</span><span class="sxs-lookup"><span data-stu-id="4191b-147">WCF follows rules for processing headers marked `mustUnderstand` described in the SOAP 1.1 and SOAP 1.2 specifications, with the following variations.</span></span>

<span data-ttu-id="4191b-148">Uma mensagem que entra na pilha de canais WCF é processada por canais individuais configurados por elementos de vinculação associados, por exemplo, Codificação de Mensagens de Texto, Segurança, Mensagens Confiáveis e Transações.</span><span class="sxs-lookup"><span data-stu-id="4191b-148">A message that enters the WCF channel stack is processed by individual channels configured by associated binding elements, for example, Text Message Encoding, Security, Reliable Messaging, and Transactions.</span></span> <span data-ttu-id="4191b-149">Cada canal reconhece cabeçalhos do namespace associado e os marca como entendidos.</span><span class="sxs-lookup"><span data-stu-id="4191b-149">Each channel recognizes headers from the associated namespace and marks them as understood.</span></span> <span data-ttu-id="4191b-150">Uma vez que uma mensagem entra no despachante, a matéria-chave de operação lê cabeçalhos esperados pelo contrato de mensagem/operação correspondente e os marca compreendidos.</span><span class="sxs-lookup"><span data-stu-id="4191b-150">Once a message enters the dispatcher, the operation formatter reads headers expected by the corresponding message/operation contract and marks them understood.</span></span> <span data-ttu-id="4191b-151">Em seguida, o despachante verifica se quaisquer `mustUnderstand` cabeçalhos restantes não são compreendidos, mas marcados como e lança uma exceção.</span><span class="sxs-lookup"><span data-stu-id="4191b-151">Then the dispatcher verifies whether any remaining headers are not understood but marked as `mustUnderstand` and throws an exception.</span></span> <span data-ttu-id="4191b-152">As mensagens `mustUnderstand` que contêm cabeçalhos direcionados ao destinatário não são processadas pelo código do aplicativo destinatário.</span><span class="sxs-lookup"><span data-stu-id="4191b-152">Messages that contain `mustUnderstand` headers that are targeted at the recipient are not processed by recipient application code.</span></span>

<span data-ttu-id="4191b-153">Esse processamento em camadas permite a separação entre camadas de infra-estrutura e camadas de aplicação do nó SOAP:</span><span class="sxs-lookup"><span data-stu-id="4191b-153">Such layered processing allows for separation between infrastructure layers and application layers of the SOAP node:</span></span>

- <span data-ttu-id="4191b-154">B1111: Cabeçalhos que não são compreendidos são detectados depois que a mensagem é processada pela pilha de canais de infra-estrutura WCF, mas antes de ser processada por aplicativo</span><span class="sxs-lookup"><span data-stu-id="4191b-154">B1111: Headers that are not understood are detected after the message is processed by the WCF infrastructure channel stack, but before it is processed by application</span></span>

     <span data-ttu-id="4191b-155">O `mustUnderstand` valor do cabeçalho difere entre SOAP 1.1 e SOAP 1.2.</span><span class="sxs-lookup"><span data-stu-id="4191b-155">The `mustUnderstand` header value differs between SOAP 1.1 and SOAP 1.2.</span></span> <span data-ttu-id="4191b-156">O Perfil Básico 1.1 exige que o `mustUnderstand` valor seja 0 ou 1 para mensagens SOAP 1.1.</span><span class="sxs-lookup"><span data-stu-id="4191b-156">Basic Profile 1.1 requires that the `mustUnderstand` value be 0 or 1 for SOAP 1.1 messages.</span></span> <span data-ttu-id="4191b-157">Soap 1.2 permite 0, `false` `true` 1, e como valores, mas recomenda `xs:boolean` emitir`false` `true`uma representação canônica de valores (, ).</span><span class="sxs-lookup"><span data-stu-id="4191b-157">SOAP 1.2 allows 0, 1, `false`, and `true` as values, but recommends emitting a canonical representation of `xs:boolean` values (`false`, `true`).</span></span>

- <span data-ttu-id="4191b-158">B1112: O WCF emite `mustUnderstand` valores 0 e 1 para as versões SOAP 1.1 e SOAP 1.2 do envelope SOAP.</span><span class="sxs-lookup"><span data-stu-id="4191b-158">B1112: WCF emits `mustUnderstand` values 0 and 1 for both SOAP 1.1 and SOAP 1.2 versions of the SOAP envelope.</span></span> <span data-ttu-id="4191b-159">O WCF aceita todo `xs:boolean` o `mustUnderstand` espaço de valor `false`do `true`cabeçalho (0, 1, )</span><span class="sxs-lookup"><span data-stu-id="4191b-159">WCF accepts the entire value space of `xs:boolean` for the `mustUnderstand` header (0, 1, `false`, `true`)</span></span>

#### <a name="soap-faults"></a><span data-ttu-id="4191b-160">Falhas de sabÃO</span><span class="sxs-lookup"><span data-stu-id="4191b-160">SOAP Faults</span></span>
<span data-ttu-id="4191b-161">A seguir está uma lista de implementações de falha SOAP específicas do WCF.</span><span class="sxs-lookup"><span data-stu-id="4191b-161">The following is a list of WCF-specific SOAP fault implementations.</span></span>

- <span data-ttu-id="4191b-162">B2121: O WCF retorna os seguintes `s11:mustUnderstand`códigos de falha SOAP 1.1: , `s11:Client`e `s11:Server`.</span><span class="sxs-lookup"><span data-stu-id="4191b-162">B2121: WCF returns the following SOAP 1.1 Fault Codes: `s11:mustUnderstand`, `s11:Client`, and `s11:Server`.</span></span>

- <span data-ttu-id="4191b-163">B2122: O WCF retorna os seguintes `s12:MustUnderstand`códigos de falha SOAP 1.2: , `s12:Sender`e `s12:Receiver`.</span><span class="sxs-lookup"><span data-stu-id="4191b-163">B2122: WCF returns the following SOAP 1.2 Fault Codes: `s12:MustUnderstand`, `s12:Sender`, and `s12:Receiver`.</span></span>

### <a name="http-binding"></a><span data-ttu-id="4191b-164">Vinculação HTTP</span><span class="sxs-lookup"><span data-stu-id="4191b-164">HTTP Binding</span></span>

#### <a name="soap-11-http-binding"></a><span data-ttu-id="4191b-165">ENCASABÃO 1.1 HTTP Vinculação</span><span class="sxs-lookup"><span data-stu-id="4191b-165">SOAP 1.1 HTTP Binding</span></span>
<span data-ttu-id="4191b-166">O WCF implementa a vinculação SOAP1.1 HTTP seguindo a seção de especificação perfil básico 3.4 com os seguintes esclarecimentos:</span><span class="sxs-lookup"><span data-stu-id="4191b-166">WCF implements SOAP1.1 HTTP binding following the Basic Profile 1.1 specification section 3.4 with the following clarifications:</span></span>

- <span data-ttu-id="4191b-167">B2211: O serviço WCF não implementa o redirecionamento das solicitações HTTP POST.</span><span class="sxs-lookup"><span data-stu-id="4191b-167">B2211: WCF service does not implement redirection of HTTP POST requests.</span></span>

- <span data-ttu-id="4191b-168">B2212: Os clientes WCF suportam cookies HTTP de acordo com 3.4.8.</span><span class="sxs-lookup"><span data-stu-id="4191b-168">B2212: WCF clients support HTTP Cookies in accordance with 3.4.8.</span></span>

#### <a name="soap-12-http-binding"></a><span data-ttu-id="4191b-169">ENCASABÃO 1.2 HTTP Vinculação</span><span class="sxs-lookup"><span data-stu-id="4191b-169">SOAP 1.2 HTTP Binding</span></span>
<span data-ttu-id="4191b-170">O WCF implementa a vinculação SOAP 1.2 HTTP conforme descrito na especificação SOAP 1.2-part 2 (SOAP12Part2) com os seguintes esclarecimentos.</span><span class="sxs-lookup"><span data-stu-id="4191b-170">WCF implements SOAP 1.2 HTTP binding as described in the SOAP 1.2-part 2 (SOAP12Part2) specification with the following clarifications.</span></span>

<span data-ttu-id="4191b-171">O SOAP 1.2 introduziu um `application/soap+xml` parâmetro de ação opcional para o tipo de mídia.</span><span class="sxs-lookup"><span data-stu-id="4191b-171">SOAP 1.2 introduced an optional action parameter for the `application/soap+xml` media type.</span></span> <span data-ttu-id="4191b-172">Este parâmetro é útil para otimizar o envio de mensagens sem exigir que o corpo da mensagem SOAP seja analisado quando o WS-Addressing não for usado.</span><span class="sxs-lookup"><span data-stu-id="4191b-172">This parameter is useful to optimize message dispatch without requiring that the body of the SOAP message be parsed when WS-Addressing is not used.</span></span>

- <span data-ttu-id="4191b-173">R2221: `application/soap+xml` O parâmetro de ação, quando presente em uma `soapAction` solicitação SOAP `wsoap12:operation` 1.2, deve corresponder ao atributo no elemento dentro da ligação WSDL correspondente.</span><span class="sxs-lookup"><span data-stu-id="4191b-173">R2221: The `application/soap+xml` action parameter, when present on a SOAP 1.2 request, must match the `soapAction` attribute on the `wsoap12:operation` element inside the corresponding WSDL binding.</span></span>

- <span data-ttu-id="4191b-174">R2222: `application/soap+xml` O parâmetro de ação, quando presente em uma `wsa:Action` mensagem SOAP 1.2, deve corresponder quando ws-endereçamento 2004/08 ou WS-Endereçamento 1.0 são usados.</span><span class="sxs-lookup"><span data-stu-id="4191b-174">R2222: The `application/soap+xml` action parameter, when present on a SOAP 1.2 message, must match `wsa:Action` when WS-Addressing 2004/08 or WS-Addressing 1.0 are used.</span></span>

<span data-ttu-id="4191b-175">Quando o WS-Endereçamento é desativado e uma solicitação `Action` recebida não contém um parâmetro de ação, a mensagem é considerada não especificada.</span><span class="sxs-lookup"><span data-stu-id="4191b-175">When WS-Addressing is disabled and an incoming request does not contain an action parameter, message `Action` is considered not specified.</span></span>

## <a name="ws-addressing"></a><span data-ttu-id="4191b-176">WS-Addressing</span><span class="sxs-lookup"><span data-stu-id="4191b-176">WS-Addressing</span></span>
<span data-ttu-id="4191b-177">O WCF implementa 3 versões do WS-Addressing:</span><span class="sxs-lookup"><span data-stu-id="4191b-177">WCF implements 3 versions of WS-Addressing:</span></span>

- <span data-ttu-id="4191b-178">WS-Addressing 2004/08</span><span class="sxs-lookup"><span data-stu-id="4191b-178">WS-Addressing 2004/08</span></span>

- <span data-ttu-id="4191b-179">Serviços web W3C endereçando núcleo 1.0 (ADDR10-CORE) e encadernamento de sabão (ADDR10-SOAP)</span><span class="sxs-lookup"><span data-stu-id="4191b-179">W3C Web Services Addressing 1.0 Core  (ADDR10-CORE) and SOAP Binding (ADDR10-SOAP)</span></span>

- <span data-ttu-id="4191b-180">WS-Addressing 1.0 - Metadados</span><span class="sxs-lookup"><span data-stu-id="4191b-180">WS-Addressing 1.0 - Metadata</span></span>

### <a name="endpoint-references"></a><span data-ttu-id="4191b-181">Referências de ponto final</span><span class="sxs-lookup"><span data-stu-id="4191b-181">Endpoint References</span></span>
<span data-ttu-id="4191b-182">Todas as versões do WS-Addressing que o WCF implementa usam referências de ponto final para descrever pontos finais.</span><span class="sxs-lookup"><span data-stu-id="4191b-182">All versions of WS-Addressing that WCF implements use endpoint references to describe endpoints.</span></span>

#### <a name="endpoint-references-and-ws-addressing-versions"></a><span data-ttu-id="4191b-183">Referências de ponto final e versões endereçadas ao WS</span><span class="sxs-lookup"><span data-stu-id="4191b-183">Endpoint References and WS-Addressing Versions</span></span>
<span data-ttu-id="4191b-184">O WCF implementa vários protocolos de infra-estrutura que usam `EndpointReference` o `W3C.WsAddressing.EndpointReferenceType` WS-Addressing e, em particular, o elemento e a classe (por exemplo, WS-ReliableMessaging, WS-SecureConversation e WS-Trust).</span><span class="sxs-lookup"><span data-stu-id="4191b-184">WCF implements a number of the infrastructure protocols that use WS-Addressing and in particular the `EndpointReference` element and `W3C.WsAddressing.EndpointReferenceType` class (for example, WS-ReliableMessaging, WS-SecureConversation, and WS-Trust).</span></span> <span data-ttu-id="4191b-185">O WCF suporta o uso de qualquer versão do WS-Addressing com outros protocolos de infra-estrutura.</span><span class="sxs-lookup"><span data-stu-id="4191b-185">WCF supports the use of either version of WS-Addressing with other infrastructure protocols.</span></span> <span data-ttu-id="4191b-186">Os pontos finais do WCF suportam uma versão do WS-Addressing por ponto final.</span><span class="sxs-lookup"><span data-stu-id="4191b-186">WCF endpoints support one version of WS-Addressing per endpoint.</span></span>

<span data-ttu-id="4191b-187">Para R3111, o namespace para o `EndpointReference` elemento ou tipo usado em mensagens trocadas com um ponto final WCF deve corresponder à versão do WS-Addressing implementada por este ponto final.</span><span class="sxs-lookup"><span data-stu-id="4191b-187">For R3111, the namespace for the `EndpointReference` element or type used in messages exchanged with a WCF endpoint must match the version of WS-Addressing implemented by this endpoint.</span></span>

<span data-ttu-id="4191b-188">Por exemplo, se um ponto final do WCF implementar `AcksTo` o WS-ReliableMessaging, o cabeçalho retornado por um ponto final dentro `CreateSequenceResponse` usará a versão WS-Endereçamento que o `EncodingBinding` elemento especifica para este ponto final.</span><span class="sxs-lookup"><span data-stu-id="4191b-188">For example, if a WCF endpoint implements WS-ReliableMessaging, the `AcksTo` header returned by such an endpoint inside `CreateSequenceResponse` uses the WS-Addressing version that the `EncodingBinding` element specifies for this endpoint.</span></span>

#### <a name="endpoint-references-and-metadata"></a><span data-ttu-id="4191b-189">Referências e metadados de ponto final</span><span class="sxs-lookup"><span data-stu-id="4191b-189">Endpoint References and Metadata</span></span>
<span data-ttu-id="4191b-190">Uma série de cenários requerem a comunicação de metadados ou uma referência a metadados para um determinado ponto final.</span><span class="sxs-lookup"><span data-stu-id="4191b-190">A number of scenarios require communicating metadata or a reference to metadata for a given endpoint.</span></span>

<span data-ttu-id="4191b-191">B3121: O WCF emprega mecanismos descritos na seção 6 de especificação WS-MetadataExchange (MEX) para incluir metadados para referências de ponto final por valor ou por referência.</span><span class="sxs-lookup"><span data-stu-id="4191b-191">B3121: WCF employs mechanisms described in the WS-MetadataExchange (MEX) specification Section 6 to include metadata for endpoint references by value or by reference.</span></span>

<span data-ttu-id="4191b-192">Considere um cenário em que um serviço WCF requer autenticação usando um token SAML (Security `http://sts.fabrikam123.com`Assertions Markup Language, linguagem de marcação de afirmações de segurança) emitido pelo emissor de token em .</span><span class="sxs-lookup"><span data-stu-id="4191b-192">Consider a scenario where a WCF service requires authentication using a Security Assertions Markup Language (SAML) token issued by the token issuer at `http://sts.fabrikam123.com`.</span></span> <span data-ttu-id="4191b-193">O ponto final do WCF descreve `sp:IssuedToken` esse requisito de `sp:Issuer` autenticação usando a afirmação com uma afirmação aninhada apontando para o emissor de token.</span><span class="sxs-lookup"><span data-stu-id="4191b-193">The WCF endpoint describes this authentication requirement by using `sp:IssuedToken` assertion with a nested `sp:Issuer` assertion pointing to the token issuer.</span></span> <span data-ttu-id="4191b-194">Os aplicativos clientes `sp:Issuer` que acessam a afirmação precisam saber como se comunicar com o ponto final do emissor do token.</span><span class="sxs-lookup"><span data-stu-id="4191b-194">Client applications that access the `sp:Issuer` assertion need to know how to communicate with the token issuer endpoint.</span></span> <span data-ttu-id="4191b-195">O cliente precisa saber metadados sobre o emissor de tokens.</span><span class="sxs-lookup"><span data-stu-id="4191b-195">The client needs to know metadata about the token issuer.</span></span> <span data-ttu-id="4191b-196">Usando as extensões de metadados de referência de ponto final definidas no MEX, o WCF fornece uma referência aos metadados do emissor de token.</span><span class="sxs-lookup"><span data-stu-id="4191b-196">Using the endpoint reference metadata extensions defined in MEX, WCF provides a reference to the token issuer metadata.</span></span>

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

### <a name="message-addressing-headers"></a><span data-ttu-id="4191b-197">Endereçamento de mensagens cabeçalhos</span><span class="sxs-lookup"><span data-stu-id="4191b-197">Message Addressing Headers</span></span>

#### <a name="message-headers"></a><span data-ttu-id="4191b-198">Cabeçalhos da mensagem</span><span class="sxs-lookup"><span data-stu-id="4191b-198">Message Headers</span></span>
<span data-ttu-id="4191b-199">Para ambas as versões WS-Addressing, o WCF usa `wsa:To` `wsa:ReplyTo`os `wsa:Action` `wsa:MessageID`seguintes cabeçalhos de mensagem conforme prescrito pelas especificações, e `wsa:RelatesTo`.</span><span class="sxs-lookup"><span data-stu-id="4191b-199">For both WS-Addressing versions, WCF uses the following message headers as prescribed by the specifications `wsa:To`, `wsa:ReplyTo`, `wsa:Action`, `wsa:MessageID`,and `wsa:RelatesTo`.</span></span>

<span data-ttu-id="4191b-200">B3211: Para todas as versões ws-addressing, wcf honras, mas não produz `wsa:FaultTo` fora `wsa:From`da caixa, ws-addressing cabeçalhos de mensagem e .</span><span class="sxs-lookup"><span data-stu-id="4191b-200">B3211: For all WS-Addressing versions, WCF honors, but does not produce out of the box, WS-Addressing message headers `wsa:FaultTo` and `wsa:From`.</span></span>

<span data-ttu-id="4191b-201">Os aplicativos que interagem com aplicativos WCF podem adicionar esses cabeçalhos de mensagem e o WCF irá processá-los de acordo.</span><span class="sxs-lookup"><span data-stu-id="4191b-201">Applications that interact with WCF applications can add these message headers and WCF will process them accordingly.</span></span>

#### <a name="reference-parameters-and-properties"></a><span data-ttu-id="4191b-202">Parâmetros e propriedades de referência</span><span class="sxs-lookup"><span data-stu-id="4191b-202">Reference Parameters and Properties</span></span>

<span data-ttu-id="4191b-203">O WCF implementa o processamento de parâmetros de referência de ponto final e propriedades de referência de acordo com as respectivas especificações.</span><span class="sxs-lookup"><span data-stu-id="4191b-203">WCF implements processing of endpoint reference parameters and reference properties in accordance with respective specifications.</span></span>

<span data-ttu-id="4191b-204">B3221: Quando configurados para usar o WS-Endereçamento 2004/08, os pontos finais do WCF não diferenciam entre o processamento de propriedades de referência e parâmetros de referência.</span><span class="sxs-lookup"><span data-stu-id="4191b-204">B3221: When configured to use WS-Addressing 2004/08, WCF endpoints do not differentiate between processing Reference Properties and Reference Parameters.</span></span>

### <a name="message-exchange-patterns"></a><span data-ttu-id="4191b-205">Padrões de troca de mensagens</span><span class="sxs-lookup"><span data-stu-id="4191b-205">Message Exchange Patterns</span></span>
<span data-ttu-id="4191b-206">A seqüência de mensagens envolvidas na invocação da operação de serviço web é referida como o padrão de *troca de mensagens*.</span><span class="sxs-lookup"><span data-stu-id="4191b-206">The sequence of messages involved in the Web service operation invocation is referred to as the *message exchange pattern*.</span></span> <span data-ttu-id="4191b-207">O WCF suporta padrões de troca de mensagens unidirecionais, de solicitação e de troca de mensagens duplex.</span><span class="sxs-lookup"><span data-stu-id="4191b-207">WCF supports one-way, request-reply, and duplex message exchange patterns.</span></span> <span data-ttu-id="4191b-208">Esta seção esclarece os requisitos de Endereçamento do WS no processamento de mensagens, dependendo do padrão de troca de mensagens que está sendo usado.</span><span class="sxs-lookup"><span data-stu-id="4191b-208">This section clarifies WS-Addressing requirements on message processing depending on the message exchange pattern being used.</span></span>

<span data-ttu-id="4191b-209">Ao longo desta seção, o solicitante envia a primeira mensagem e o respondente recebe a primeira mensagem.</span><span class="sxs-lookup"><span data-stu-id="4191b-209">Throughout this section, the requester sends the first message and the responder receives the first message.</span></span>

#### <a name="one-way-message"></a><span data-ttu-id="4191b-210">Mensagem unidirecional</span><span class="sxs-lookup"><span data-stu-id="4191b-210">One-Way Message</span></span>
<span data-ttu-id="4191b-211">Quando um ponto final do WCF é configurado para suportar mensagens com um dado `Action` para seguir um padrão unidirecional, o ponto final do WCF segue os seguintes comportamentos e requisitos.</span><span class="sxs-lookup"><span data-stu-id="4191b-211">When a WCF endpoint is configured to support messages with a given `Action` to follow a one-way pattern, the WCF endpoint follows the following behaviors and requirements.</span></span> <span data-ttu-id="4191b-212">A menos que especificado de outra forma, comportamentos e regras se aplicam a ambas as versões do WS-Addressing suportado no WCF:</span><span class="sxs-lookup"><span data-stu-id="4191b-212">Unless otherwise specified, behaviors and rules apply for both versions of WS-Addressing supported in WCF:</span></span>

- <span data-ttu-id="4191b-213">R3311: O solicitante `wsa:To`deve `wsa:Action`incluir , e cabeçalhos para todos os parâmetros de referência especificados pela referência do ponto final.</span><span class="sxs-lookup"><span data-stu-id="4191b-213">R3311: The requester must include `wsa:To`, `wsa:Action`, and headers for all reference parameters specified by the endpoint reference.</span></span> <span data-ttu-id="4191b-214">Quando o WS-Addressing 2004/08 for usado e [propriedades de referência] forem especificadas pela referência do ponto final, os cabeçalhos correspondentes também devem ser adicionados à mensagem.</span><span class="sxs-lookup"><span data-stu-id="4191b-214">When WS-Addressing 2004/08 is used and [reference properties] are specified by the endpoint reference, the corresponding headers must be added to the message too.</span></span>

- <span data-ttu-id="4191b-215">B3312: O solicitante `MessageID`pode `ReplyTo`incluir `FaultTo` , e cabeçalhos.</span><span class="sxs-lookup"><span data-stu-id="4191b-215">B3312: The requester may include `MessageID`, `ReplyTo`, and `FaultTo` headers.</span></span> <span data-ttu-id="4191b-216">A infra-estrutura do receptor irá ignorá-los, e eles serão passados para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4191b-216">The receiver infrastructure will ignore them, and they will be passed to the application.</span></span>

- <span data-ttu-id="4191b-217">R3313: Quando http é usado e nenhuma mensagem está sendo enviada na perna de resposta HTTP, o respondente deve enviar uma resposta HTTP com um corpo vazio e um código de status HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="4191b-217">R3313: When HTTP is used and no message is being sent on the HTTP response leg, the responder must send an HTTP response with an empty body and an HTTP 202 status code.</span></span>

     <span data-ttu-id="4191b-218">Quando o transporte HTTP estiver em uso e o contrato de operação declarar uma mensagem unidirecional, a resposta HTTP `SequenceAcknowledgement` ainda pode ser usada para enviar mensagens de infra-estrutura — por exemplo, mensagens confiáveis podem enviar uma mensagem em uma resposta HTTP.</span><span class="sxs-lookup"><span data-stu-id="4191b-218">When the HTTP transport is in use and the operation contract declares a message one-way, the HTTP response can still be used for sending infrastructure messages—for example, reliable messaging can send a `SequenceAcknowledgement` message on an HTTP response.</span></span>

- <span data-ttu-id="4191b-219">B3314: O respondente do WCF não envia uma mensagem de falha em resposta a uma mensagem unidirecional.</span><span class="sxs-lookup"><span data-stu-id="4191b-219">B3314: The WCF responder does not send a fault message in response to a one-way message.</span></span>

#### <a name="request-reply"></a><span data-ttu-id="4191b-220">Solicitação-resposta</span><span class="sxs-lookup"><span data-stu-id="4191b-220">Request-Reply</span></span>
<span data-ttu-id="4191b-221">Quando um ponto final do WCF é `Action` configurado para uma mensagem com um dado para seguir o padrão de solicitação-resposta, o ponto final do WCF segue os comportamentos e requisitos abaixo.</span><span class="sxs-lookup"><span data-stu-id="4191b-221">When a WCF endpoint is configured for a message with a given `Action` to follow the request-reply pattern, the WCF endpoint follows the behaviors and requirements below.</span></span> <span data-ttu-id="4191b-222">A menos que especificado em contrário, comportamentos e regras se aplicam a ambas as versões do WS-Addressing suportado no WCF:</span><span class="sxs-lookup"><span data-stu-id="4191b-222">Unless specified otherwise, behaviors and rules apply for both versions of WS-Addressing supported in WCF:</span></span>

- <span data-ttu-id="4191b-223">R3321: O solicitante deve incluir `wsa:To` `wsa:Action`na `wsa:MessageID`solicitação , e cabeçalhos para todos os parâmetros de referência ou propriedades de referência (ou ambos) especificados pela referência do ponto final.</span><span class="sxs-lookup"><span data-stu-id="4191b-223">R3321: The requester must include in the request `wsa:To`, `wsa:Action`, `wsa:MessageID`, and headers for all reference parameters or reference properties (or both) specified by the endpoint reference.</span></span>

- <span data-ttu-id="4191b-224">R3322: Quando o WS-Endereçamento 2004/08 for usado, `ReplyTo` também deve ser incluído na solicitação.</span><span class="sxs-lookup"><span data-stu-id="4191b-224">R3322: When WS-Addressing 2004/08 is used, `ReplyTo` must also be included in the request.</span></span>

- <span data-ttu-id="4191b-225">R3323: Quando o WS-Endereçamento `ReplyTo` 1.0 é usado e não está presente na solicitação, uma referência de ponto final padrão com a propriedade [endereço] igual a `http://www.w3.org/2005/08/addressing/anonymous` é usada.</span><span class="sxs-lookup"><span data-stu-id="4191b-225">R3323: When WS-Addressing 1.0 is used and `ReplyTo` is not present in the request, a default endpoint reference with the [address] property equal to `http://www.w3.org/2005/08/addressing/anonymous` is used.</span></span>

- <span data-ttu-id="4191b-226">R3324: O solicitante `wsa:To`deve `wsa:Action`incluir `wsa:RelatesTo` , e cabeçalhos na mensagem de resposta, bem como cabeçalhos para todos os parâmetros de referência ou propriedades de referência (ou ambos) especificados pela referência de `ReplyTo` ponto final na solicitação.</span><span class="sxs-lookup"><span data-stu-id="4191b-226">R3324: The requester must include `wsa:To`, `wsa:Action`, and `wsa:RelatesTo` headers in the reply message, as well as headers for all reference parameters or reference properties (or both) specified by the `ReplyTo` endpoint reference in the request.</span></span>

### <a name="web-services-addressing-faults"></a><span data-ttu-id="4191b-227">Serviços web abordando falhas</span><span class="sxs-lookup"><span data-stu-id="4191b-227">Web Services Addressing Faults</span></span>
<span data-ttu-id="4191b-228">R3411: O WCF produz as seguintes falhas definidas pelo WS-Addressing 2004/08.</span><span class="sxs-lookup"><span data-stu-id="4191b-228">R3411: WCF produces the following faults defined by WS-Addressing 2004/08.</span></span>

| <span data-ttu-id="4191b-229">Código</span><span class="sxs-lookup"><span data-stu-id="4191b-229">Code</span></span> | <span data-ttu-id="4191b-230">Causa</span><span class="sxs-lookup"><span data-stu-id="4191b-230">Cause</span></span> |
|----------|-----------|
| `wsa:DestinationUnreachable` | <span data-ttu-id="4191b-231">A mensagem `ReplyTo` chegou com um que é diferente do endereço de resposta estabelecido para este canal; não há ponto final ouvindo o endereço especificado no cabeçalho Para.</span><span class="sxs-lookup"><span data-stu-id="4191b-231">The message arrived with a `ReplyTo` that is different from the reply address established for this channel; there is no endpoint listening at the address specified in the To header.</span></span> |
| `wsa:ActionNotSupported` | <span data-ttu-id="4191b-232">os canais de infra-estrutura ou despachante associados ao `Action` ponto final não reconhecem a ação especificada no cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="4191b-232">the infrastructure channels or dispatcher associated with the endpoint do not recognize the action specified in the `Action` header.</span></span> |

<span data-ttu-id="4191b-233">R3412: O WCF produz as seguintes falhas definidas pelo WS-Endereçamento 1.0.</span><span class="sxs-lookup"><span data-stu-id="4191b-233">R3412: WCF produces the following faults defined by WS-Addressing 1.0.</span></span>

| <span data-ttu-id="4191b-234">Código</span><span class="sxs-lookup"><span data-stu-id="4191b-234">Code</span></span> | <span data-ttu-id="4191b-235">Causa</span><span class="sxs-lookup"><span data-stu-id="4191b-235">Cause</span></span> |
|----------|-----------|
| `wsa10:InvalidAddressingHeader` | <span data-ttu-id="4191b-236">`wsa:To`Duplicado, `wsa:From` `wsa:ReplyTo` `wsa:MessageID`ou .</span><span class="sxs-lookup"><span data-stu-id="4191b-236">Duplicate `wsa:To`, `wsa:ReplyTo`, `wsa:From` or `wsa:MessageID`.</span></span> <span data-ttu-id="4191b-237">Duplicata `wsa:RelatesTo` `RelationshipType`com o mesmo .</span><span class="sxs-lookup"><span data-stu-id="4191b-237">Duplicate `wsa:RelatesTo` with the same `RelationshipType`.</span></span> |
| `wsa10:MessageAddressingHeaderRequired` | <span data-ttu-id="4191b-238">O cabeçalho de endereçamento necessário está faltando.</span><span class="sxs-lookup"><span data-stu-id="4191b-238">The required Addressing header is missing.</span></span> |
| `wsa10:DestinationUnreachable` | <span data-ttu-id="4191b-239">A mensagem `ReplyTo` chegou com um que é diferente do endereço de resposta estabelecido para este canal.</span><span class="sxs-lookup"><span data-stu-id="4191b-239">The message arrived with a `ReplyTo` that is different from the reply address established for this channel.</span></span> <span data-ttu-id="4191b-240">Não há ponto final ouvindo o endereço especificado no cabeçalho Para.</span><span class="sxs-lookup"><span data-stu-id="4191b-240">There is no endpoint listening at the address specified in the To header.</span></span> |
| `wsa10:ActionNotSupported` | <span data-ttu-id="4191b-241">Uma ação especificada `Action` no cabeçalho não é reconhecida pelos canais de infra-estrutura ou pelo despachante associado ao ponto final.</span><span class="sxs-lookup"><span data-stu-id="4191b-241">An action specified in the `Action` header is not recognized by the infrastructure channels or dispatcher associated with the endpoint.</span></span> |
| `wsa10:EndpointUnavailable` | <span data-ttu-id="4191b-242">O canal RM envia essa falha de volta, indicando que o `CreateSequence` ponto final não processará a seqüência com base no exame dos cabeçalhos endereçados da mensagem.</span><span class="sxs-lookup"><span data-stu-id="4191b-242">The RM channel sends this fault back, indicating the endpoint will not process the sequence based upon examination of the `CreateSequence` message’s addressing headers.</span></span> |

<span data-ttu-id="4191b-243">Código nas tabelas `FaultCode` anteriores mapas para `SubCode` em SOAP 1.1 e (com Code=Sender) em SOAP 1.2.</span><span class="sxs-lookup"><span data-stu-id="4191b-243">Code in the preceding tables maps to `FaultCode` in SOAP 1.1 and `SubCode` (with Code=Sender) in SOAP 1.2.</span></span>

### <a name="wsdl-11-binding-and-ws-policy-assertions"></a><span data-ttu-id="4191b-244">Afirmações de política de vinculação e ws-saque a wsdl 1.1</span><span class="sxs-lookup"><span data-stu-id="4191b-244">WSDL 1.1 Binding and WS-Policy Assertions</span></span>

#### <a name="indicating-use-of-ws-addressing"></a><span data-ttu-id="4191b-245">Indicando o uso do WS-Addressing</span><span class="sxs-lookup"><span data-stu-id="4191b-245">Indicating Use of WS-Addressing</span></span>
<span data-ttu-id="4191b-246">O WCF usa as afirmações de diretiva para indicar o suporte ao ponto final para uma versão específica do WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="4191b-246">WCF uses policy assertions to indicate endpoint support for a particular WS-Addressing version.</span></span>

<span data-ttu-id="4191b-247">A seguinte afirmação de política tem Endpoint Policy Subject [WS-PA] e indica que as mensagens enviadas e recebidas do ponto final devem usar o WS-Addressing 2004/08.</span><span class="sxs-lookup"><span data-stu-id="4191b-247">The following policy assertion has Endpoint Policy Subject [WS-PA] and indicates messages sent and received from the endpoint must use WS-Addressing 2004/08.</span></span>

```xml
<wsap:UsingAddressing />
```

<span data-ttu-id="4191b-248">Esta afirmação de política aumenta a especificação WS-Addressing 2004/08.</span><span class="sxs-lookup"><span data-stu-id="4191b-248">This policy assertion augments the WS-Addressing 2004/08 specification.</span></span>

<span data-ttu-id="4191b-249">A seguinte afirmação de diretiva indica que as mensagens enviadas/recebidas devem usar o WS-Endereçamento 1.0.</span><span class="sxs-lookup"><span data-stu-id="4191b-249">The following policy assertion this indicates that messages sent/received must use WS-Addressing 1.0.</span></span>

```xml
<wsam:Addressing/>
```

<span data-ttu-id="4191b-250">A seguinte afirmação de diretiva tem um Assunto de Diretiva de Ponto Final [WS-PA] e indica que as mensagens enviadas e recebidas do ponto final devem usar o WS-Addressing 2004/08.</span><span class="sxs-lookup"><span data-stu-id="4191b-250">The following policy assertion has an Endpoint Policy Subject [WS-PA] and indicates that messages sent and received from the endpoint must use WS-Addressing 2004/08.</span></span>

```xml
<wsaw10:UsingAddressing />
```

<span data-ttu-id="4191b-251">O `wsaw10:UsingAddressing` elemento é emprestado de [WS-Addressing-WSDL] e é usado no contexto da WS-Policy em conformidade com essa especificação, seção 3.1.2.</span><span class="sxs-lookup"><span data-stu-id="4191b-251">The `wsaw10:UsingAddressing` element is borrowed from [WS-Addressing-WSDL] and is used in the context of WS-Policy in compliance with that specification, section 3.1.2.</span></span>

<span data-ttu-id="4191b-252">O uso de Endereçamento não altera a semântica das ligações WSDL 1.1, SOAP 1.1 e SOAP 1.2 HTTP.</span><span class="sxs-lookup"><span data-stu-id="4191b-252">Use of Addressing does not alter the semantics of WSDL 1.1, SOAP 1.1, and SOAP 1.2 HTTP Bindings.</span></span> <span data-ttu-id="4191b-253">Por exemplo, se uma resposta for esperada para uma solicitação enviada para um ponto final que usa endereçamento e vinculação WSDL SOAP 1.x HTTP, a resposta deve ser enviada usando a resposta HTTP.</span><span class="sxs-lookup"><span data-stu-id="4191b-253">For example, if a reply is expected to a request that is sent to an endpoint that uses Addressing and WSDL SOAP 1.x HTTP binding, the reply must be sent by using the HTTP response.</span></span>

<span data-ttu-id="4191b-254">Para respostas enviadas pela resposta http, a afirmação do WS-AM é:</span><span class="sxs-lookup"><span data-stu-id="4191b-254">For replies sent over the http response, the WS-AM assertion is:</span></span>

```xml
<wsam:AnonymousResponses/>
```

<span data-ttu-id="4191b-255">A afirmação completa da política pode ser assim:</span><span class="sxs-lookup"><span data-stu-id="4191b-255">The complete policy assertion might look like this:</span></span>

```xml
<wsam:Addressing>
    <wsp:Policy>
        <wsam:AnonymousResponses />
    </wsp:Policy>
</wsam:Addressing>
```

<span data-ttu-id="4191b-256">No entanto, existem padrões de troca de mensagens que se beneficiam de ter duas conexões HTTP independentes estabelecidas entre o solicitante e o respondente, por exemplo, mensagens de mão única não solicitadas enviadas pelo respondente.</span><span class="sxs-lookup"><span data-stu-id="4191b-256">However, there are message exchange patterns that benefit from having two independent converse HTTP connections established between the requester and the responder, for example, unsolicited one-way messages sent by the responder.</span></span>

<span data-ttu-id="4191b-257">O WCF oferece um recurso pelo qual dois canais de transporte subjacentes podem formar um canal Duplex Composto, onde um canal é usado para mensagens de entrada e o outro é usado para mensagens de saída.</span><span class="sxs-lookup"><span data-stu-id="4191b-257">WCF offers a feature by which two underlying transport channels can form a Composite Duplex channel, where one channel is used for input messages and the other is used for output messages.</span></span> <span data-ttu-id="4191b-258">No caso do TRANSPORTE HTTP, o Composto Duplex fornece duas conexões HTTP inversas.</span><span class="sxs-lookup"><span data-stu-id="4191b-258">In the case of the HTTP Transport, Composite Duplex provides two converse HTTP connections.</span></span> <span data-ttu-id="4191b-259">O solicitante usa uma conexão para enviar mensagens ao respondente, e o respondente usa a outra para enviar mensagens de volta ao solicitante.</span><span class="sxs-lookup"><span data-stu-id="4191b-259">The requester uses one connection to send messages to the responder, and the responder uses the other to send messages back to the requester.</span></span>

<span data-ttu-id="4191b-260">Para respostas enviadas por solicitações http separadas, a afirmação ws-am é</span><span class="sxs-lookup"><span data-stu-id="4191b-260">For replies sent over separate http requests, the ws-am assertion is</span></span>

```xml
<wsam:NonAnonymousResponses/>
```

<span data-ttu-id="4191b-261">A afirmação completa da política pode ser assim:</span><span class="sxs-lookup"><span data-stu-id="4191b-261">The complete policy assertion might look like this:</span></span>

```xml
<wsam:Addressing>
    <wsp:Policy>
        <wsam:NonAnonymousResponses />
    </wsp:Policy>
</wsam:Addressing>
```

<span data-ttu-id="4191b-262">O uso da seguinte afirmação que tem O Assunto da Política de Ponto Final [WS-PA] em pontos finais que usam as vinculações WSDL 1.1 SOAP 1.x HTTP requer duas conexões HTTP inversas separadas para serem usadas para mensagens que fluem do solicitante para responder e responder ao solicitante, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="4191b-262">Use of the following assertion that has Endpoint Policy Subject [WS-PA] on endpoints that use WSDL 1.1 SOAP 1.x HTTP bindings requires two separate converse HTTP connections to be used for messages flowing from requester to responder and responder to requester, respectively.</span></span>

```xml
<cdp:CompositeDuplex/>
```

<span data-ttu-id="4191b-263">A declaração anterior leva aos `wsa:ReplyTo` seguintes requisitos no cabeçalho para mensagens de solicitação:</span><span class="sxs-lookup"><span data-stu-id="4191b-263">The previous statement leads to the following requirements on the `wsa:ReplyTo` header for request messages:</span></span>

- <span data-ttu-id="4191b-264">R3514: As mensagens de solicitação enviadas `ReplyTo` a `[address]` um ponto `http://www.w3.org/2005/08/addressing/anonymous` final devem ter um cabeçalho com a propriedade não igual a se `wsap10:UsingAddressing` o `wsap:UsingAddressing` ponto `cdp:CompositeDuplex` final usar uma vinculação WSDL 1.1 SOAP 1.x HTTP e tiver uma alternativa de política com uma ou afirmação acoplada à anexada.</span><span class="sxs-lookup"><span data-stu-id="4191b-264">R3514: Request messages sent to an endpoint must have a `ReplyTo` header with the `[address]` property not equal to `http://www.w3.org/2005/08/addressing/anonymous` if the endpoint uses a WSDL 1.1 SOAP 1.x HTTP binding and has a policy alternative with a `wsap10:UsingAddressing` or `wsap:UsingAddressing` assertion coupled with `cdp:CompositeDuplex` attached.</span></span>

- <span data-ttu-id="4191b-265">R3515: As mensagens de solicitação enviadas `ReplyTo` a `[address]` um ponto `http://www.w3.org/2005/08/addressing/anonymous`final devem `ReplyTo` ter um cabeçalho com a propriedade igual ou não ter um cabeçalho, `wsap10:UsingAddressing` se o `cdp:CompositeDuplex` ponto final usar uma vinculação WSDL 1.1 SOAP 1.x HTTP e tiver uma alternativa de política com afirmação e nenhuma afirmação anexada.</span><span class="sxs-lookup"><span data-stu-id="4191b-265">R3515: Request messages sent to an endpoint must have a `ReplyTo` header with the `[address]` property equal to `http://www.w3.org/2005/08/addressing/anonymous`, or not have a `ReplyTo` header at all, if the endpoint uses a WSDL 1.1 SOAP 1.x HTTP binding and has a policy alternative with `wsap10:UsingAddressing` assertion and no `cdp:CompositeDuplex` assertion attached.</span></span>

- <span data-ttu-id="4191b-266">R3516: As mensagens de solicitação enviadas `ReplyTo` a `[address]` um ponto `http://www.w3.org/2005/08/addressing/anonymous` final devem ter um cabeçalho com uma propriedade igual a se `wsap:UsingAddressing` o ponto `cdp:CompositeDuplex` final usar uma vinculação WSDL 1.1 SOAP 1.x HTTP e tiver uma alternativa de política com afirmação e nenhuma afirmação anexada.</span><span class="sxs-lookup"><span data-stu-id="4191b-266">R3516: Request messages sent to an endpoint must have a `ReplyTo` header with an `[address]` property equal to `http://www.w3.org/2005/08/addressing/anonymous` if the endpoint uses a WSDL 1.1 SOAP 1.x HTTP binding and has a policy alternative with `wsap:UsingAddressing` assertion and no `cdp:CompositeDuplex` assertion attached.</span></span>

<span data-ttu-id="4191b-267">A especificação WSDL que trata do WSDL tenta descrever `<wsaw:Anonymous/>` vinculações de protocolo semelhantes introduzindo um elemento com `wsa:ReplyTo` três valores textuais (necessários, opcionais e proibidos) para indicar requisitos no cabeçalho (seção 3.2).</span><span class="sxs-lookup"><span data-stu-id="4191b-267">The WS-addressing WSDL specification attempts to describe similar protocol bindings by introducing an element `<wsaw:Anonymous/>` with three textual values (required, optional, and prohibited) to indicate requirements on the `wsa:ReplyTo` header (section 3.2).</span></span> <span data-ttu-id="4191b-268">Infelizmente, tal definição de elemento não é particularmente utilizável como uma afirmação no contexto da WS-Policy, porque requer extensões específicas de domínio para apoiar a intersecção de alternativas usando tal elemento como uma afirmação.</span><span class="sxs-lookup"><span data-stu-id="4191b-268">Unfortunately, such element definition is not particularly usable as an assertion in the context of WS-Policy, because it requires domain-specific extensions to support the intersection of alternatives using such an element as an assertion.</span></span> <span data-ttu-id="4191b-269">Essa definição de elemento também `ReplyTo` indica o valor do cabeçalho em oposição ao comportamento do ponto final no fio, o que o torna específico para o transporte HTTP.</span><span class="sxs-lookup"><span data-stu-id="4191b-269">Such element definition also indicates the value of the `ReplyTo` header as opposed to the endpoint behavior on the wire, which makes it specific to HTTP transport.</span></span>

#### <a name="action-definition"></a><span data-ttu-id="4191b-270">Definição de Ação</span><span class="sxs-lookup"><span data-stu-id="4191b-270">Action Definition</span></span>
<span data-ttu-id="4191b-271">WS-Addressing 2004/08 define `wsa:Action` um `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]` atributo para os elementos.</span><span class="sxs-lookup"><span data-stu-id="4191b-271">WS-Addressing 2004/08 defines a `wsa:Action` attribute for the `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]` elements.</span></span> <span data-ttu-id="4191b-272">WS-Addressing 1.0 WSDL Binding (WS-ADDR10-WSDL) define `wsaw10:Action`um atributo semelhante, .</span><span class="sxs-lookup"><span data-stu-id="4191b-272">WS-Addressing 1.0 WSDL Binding (WS-ADDR10-WSDL) defines a similar attribute, `wsaw10:Action`.</span></span>

<span data-ttu-id="4191b-273">A única diferença entre os dois é a semântica padrão de padrão de ação descrita na seção 3.3.2 do WS-ADDR e na seção 4.4.4 do WS-ADDR10-WSDL, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="4191b-273">The only difference between the two is the default Action pattern semantics described in section 3.3.2 of WS-ADDR and section 4.4.4 of WS-ADDR10-WSDL, respectively.</span></span>

<span data-ttu-id="4191b-274">É razoável ter dois pontos finais que `portType` compartilham o mesmo (ou contrato, na terminologia wcf), mas usando versões diferentes do WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="4191b-274">It is a reasonable to have two endpoints that share the same `portType` (or contract, in WCF terminology) but using different versions of WS-Addressing.</span></span> <span data-ttu-id="4191b-275">Mas dado que a `portType` Ação é definida pelo e `portType`não deve mudar entre os pontos finais que implementam o , torna-se impossível suportar ambos os padrões de ação padrão.</span><span class="sxs-lookup"><span data-stu-id="4191b-275">But given that Action is defined by the `portType` and should not change across the endpoints that implement the `portType`, it becomes impossible to support both default action patterns.</span></span>

<span data-ttu-id="4191b-276">Para resolver essa controvérsia, o WCF suporta `Action` uma única versão do atributo.</span><span class="sxs-lookup"><span data-stu-id="4191b-276">To resolve this controversy, WCF supports a single version of the `Action` attribute.</span></span>

<span data-ttu-id="4191b-277">B3521: O WCF usa o atributo `wsaw10:Action` em `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]` elementos definidos no WS-ADDR10-WSDL para determinar o `Action` URI para as mensagens correspondentes, independentemente da versão WS-Endereçamento usada pelo ponto final.</span><span class="sxs-lookup"><span data-stu-id="4191b-277">B3521: WCF uses the `wsaw10:Action` attribute on `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]` elements as defined in WS-ADDR10-WSDL to determine the `Action` URI for the corresponding messages irrespective of the WS-Addressing version used by the endpoint.</span></span>

#### <a name="use-endpoint-reference-inside-wsdl-port"></a><span data-ttu-id="4191b-278">Use a referência de ponto final dentro da porta WSDL</span><span class="sxs-lookup"><span data-stu-id="4191b-278">Use Endpoint Reference Inside WSDL Port</span></span>
<span data-ttu-id="4191b-279">A seção 4.1 WS-ADDR10-WSDL estende o `wsdl:port` elemento para incluir o `<wsa10:EndpointReference…/>` elemento filho para descrever o ponto final nos termos de endereçamento de WS.</span><span class="sxs-lookup"><span data-stu-id="4191b-279">WS-ADDR10-WSDL section 4.1 extends the `wsdl:port` element to include the `<wsa10:EndpointReference…/>` child element to describe the endpoint in WS-Addressing terms.</span></span> <span data-ttu-id="4191b-280">O WCF expande esse utilitário no WS-Addressing 2004/08, permitindo `<wsa:EndpointReference…/>` aparecer como um elemento infantil de `wsdl:port`.</span><span class="sxs-lookup"><span data-stu-id="4191b-280">WCF expands this utility on WS-Addressing 2004/08, allowing `<wsa:EndpointReference…/>` to appear as a child element of `wsdl:port`.</span></span>

- <span data-ttu-id="4191b-281">R3531: Se um ponto final tiver uma `<wsaw10:UsingAddressing/>` alternativa de `wsdl:port` política anexada com `<wsa10:EndpointReference …/>`uma afirmação de política, o elemento correspondente pode conter um elemento filho .</span><span class="sxs-lookup"><span data-stu-id="4191b-281">R3531: If an endpoint has an attached policy alternative with a `<wsaw10:UsingAddressing/>` policy assertion, the corresponding `wsdl:port` element can contain a child element `<wsa10:EndpointReference …/>`.</span></span>

- <span data-ttu-id="4191b-282">R3532: Se `wsdl:port` a contém `<wsa10:EndpointReference …/>`um `wsa10:EndpointReference/wsa10:Address` elemento filho, o valor `@address` do elemento `wsdl:port` / `wsdl:location` filho deve corresponder ao valor do atributo do elemento irmão.</span><span class="sxs-lookup"><span data-stu-id="4191b-282">R3532: If a `wsdl:port` contains a child element `<wsa10:EndpointReference …/>`, the `wsa10:EndpointReference/wsa10:Address` child element value must match the value of the `@address` attribute of the sibling `wsdl:port`/`wsdl:location` element.</span></span>

- <span data-ttu-id="4191b-283">R3533: Se um ponto final tiver `<wsap:UsingAddressing/>` uma alternativa de `wsdl:port` política anexada `<wsa:EndpointReference …/>`com a afirmação da política, o elemento correspondente pode conter um elemento filho .</span><span class="sxs-lookup"><span data-stu-id="4191b-283">R3533: If an endpoint has an attached policy alternative with `<wsap:UsingAddressing/>` policy assertion, the corresponding `wsdl:port` element can contain a child element `<wsa:EndpointReference …/>`.</span></span>

- <span data-ttu-id="4191b-284">R3534: Se `wsdl:port` a contém `<wsa:EndpointReference …/>`um `wsa:EndpointReference/wsa:Address` elemento filho, o valor `@address` do elemento `wsdl:port` / `wsdl:location` filho deve corresponder ao valor do atributo do elemento irmão.</span><span class="sxs-lookup"><span data-stu-id="4191b-284">R3534: If a `wsdl:port` contains a child element `<wsa:EndpointReference …/>`, the `wsa:EndpointReference/wsa:Address` child element value must match the value of the `@address` attribute of the sibling `wsdl:port`/`wsdl:location` element.</span></span>

### <a name="composition-with-ws-security"></a><span data-ttu-id="4191b-285">Composição com WS-Security</span><span class="sxs-lookup"><span data-stu-id="4191b-285">Composition with WS-Security</span></span>
<span data-ttu-id="4191b-286">De acordo com as seções de consideração de segurança no WS-ADDR e ws-ADDR10, todos os cabeçalhos de mensagem endereçados são recomendados a serem assinados juntamente com o corpo de mensagens para amarrá-los juntos.</span><span class="sxs-lookup"><span data-stu-id="4191b-286">According to security consideration sections in WS-ADDR and WS-ADDR10, all addressing message headers are recommended to be signed together with the message body to bind them together.</span></span>

<span data-ttu-id="4191b-287">Quando o WS-Security for usado para proteção da integridade da mensagem, os cabeçalhos de mensagem que endereçam o WS, bem como os cabeçalhos resultantes de parâmetros de referência ou propriedades (ou ambos) devem ser assinados juntamente com o corpo da mensagem.</span><span class="sxs-lookup"><span data-stu-id="4191b-287">When WS-Security is used for message integrity protection, WS-Addressing message headers as well as headers resulted from reference parameters or properties (or both) must be signed together with the body of the message.</span></span>

### <a name="examples"></a><span data-ttu-id="4191b-288">Exemplos</span><span class="sxs-lookup"><span data-stu-id="4191b-288">Examples</span></span>

#### <a name="one-way-message"></a><span data-ttu-id="4191b-289">Mensagem unidirecional</span><span class="sxs-lookup"><span data-stu-id="4191b-289">One-Way Message</span></span>
<span data-ttu-id="4191b-290">Neste cenário, o remetente envia uma mensagem de mão única para o receptor.</span><span class="sxs-lookup"><span data-stu-id="4191b-290">In this scenario, the sender sends a one-way message to the receiver.</span></span> <span data-ttu-id="4191b-291">SOAP 1.2, HTTP 1.1 e W3C WS-Addressing 1.0 são usados.</span><span class="sxs-lookup"><span data-stu-id="4191b-291">SOAP 1.2, HTTP 1.1, and W3C WS-Addressing 1.0 are used.</span></span>

<span data-ttu-id="4191b-292">A estrutura da mensagem de `wsa10:To` `wsa10:Action` solicitação: os cabeçalhos de mensagem incluem e elementos.</span><span class="sxs-lookup"><span data-stu-id="4191b-292">The Request Message Structure: The message headers include `wsa10:To` and `wsa10:Action` elements.</span></span> <span data-ttu-id="4191b-293">O corpo da mensagem inclui um elemento específico `<app:Ping>` do namespace do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4191b-293">The message body includes a specific `<app:Ping>` element from the application namespace.</span></span>

<span data-ttu-id="4191b-294">Cabeçalhos HTTP: O destino no `wsa10:To` POST corresponde ao URI no elemento.</span><span class="sxs-lookup"><span data-stu-id="4191b-294">HTTP Headers: The destination in POST matches the URI in the `wsa10:To` element.</span></span>

<span data-ttu-id="4191b-295">O cabeçalho tipo de `application/soap+xml` conteúdo tem o valor do que é exigido pelo SOAP 1.2.</span><span class="sxs-lookup"><span data-stu-id="4191b-295">The Content-Type header has the value of `application/soap+xml` as required by SOAP 1.2.</span></span> <span data-ttu-id="4191b-296">`charset` Parâmetros `action` e estão incluídos.</span><span class="sxs-lookup"><span data-stu-id="4191b-296">Parameters `charset` and `action` are included.</span></span> <span data-ttu-id="4191b-297">O `action` parâmetro do cabeçalho tipo de `wsa10:Action` conteúdo corresponde ao valor do cabeçalho da mensagem.</span><span class="sxs-lookup"><span data-stu-id="4191b-297">The `action` parameter of the Content-Type header matches the value of the `wsa10:Action` message header.</span></span>

```
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

<span data-ttu-id="4191b-298">O receptor responde com uma resposta HTTP vazia e status 202.</span><span class="sxs-lookup"><span data-stu-id="4191b-298">The receiver responds with an empty HTTP response and status 202.</span></span> <span data-ttu-id="4191b-299">Um exemplo da resposta HTTP:</span><span class="sxs-lookup"><span data-stu-id="4191b-299">An example of the HTTP response:</span></span>

```
HTTP/1.1 202 Accepted
Date: Fri, 15 Jul 2005 08:56:07 GMT
Server: Microsoft-IIS/6.0
MicrosoftOfficeWebServer: 5.0_Pub
X-Powered-By: ASP.NET
X-AspNet-Version: 2.0.50215
Cache-Control: private
Content-Length: 0
```

## <a name="soap-message-transmission-optimization-mechanism"></a><span data-ttu-id="4191b-300">Mecanismo de otimização de transmissão de mensagens soap</span><span class="sxs-lookup"><span data-stu-id="4191b-300">SOAP Message Transmission Optimization Mechanism</span></span>
<span data-ttu-id="4191b-301">Esta seção descreve os detalhes de implementação do WCF para o HTTP SOAP MTOM.</span><span class="sxs-lookup"><span data-stu-id="4191b-301">This section describes the WCF implementation details for the HTTP SOAP MTOM.</span></span> <span data-ttu-id="4191b-302">A tecnologia MTOM é o mecanismo de codificação de mensagens SOAP da mesma classe que a codificação de texto/XML tradicional ou codificação binária WCF.</span><span class="sxs-lookup"><span data-stu-id="4191b-302">MTOM technology is SOAP message encoding mechanism of the same class as traditional text/XML encoding or WCF Binary encoding.</span></span> <span data-ttu-id="4191b-303">MTOM inclui o seguinte:</span><span class="sxs-lookup"><span data-stu-id="4191b-303">MTOM includes the following:</span></span>

- <span data-ttu-id="4191b-304">Um mecanismo de codificação e embalagem XML descrito por [XOP] que otimiza os itens de informações XML contendo dados binários codificados base64 em partes binárias separadas.</span><span class="sxs-lookup"><span data-stu-id="4191b-304">An XML encoding and packaging mechanism described by [XOP] that optimizes XML information items containing base64-encoded binary data into separate binary parts.</span></span>

- <span data-ttu-id="4191b-305">Um encapsulamento MIME do pacote XOP que serializa o Infoset XML e cada parte binária do pacote XOP em uma parte MIME separada.</span><span class="sxs-lookup"><span data-stu-id="4191b-305">A MIME encapsulation of the XOP package that serializes the XML Infoset and each binary part of the XOP package into a separate MIME part.</span></span>

- <span data-ttu-id="4191b-306">Uma codificação MIME XOP aplicada ao ENVELOPE SOAP 1.x.</span><span class="sxs-lookup"><span data-stu-id="4191b-306">A MIME XOP encoding applied to SOAP 1.x Envelope.</span></span>

- <span data-ttu-id="4191b-307">Uma vinculação de transporte HTTP.</span><span class="sxs-lookup"><span data-stu-id="4191b-307">An HTTP transport binding.</span></span>

<span data-ttu-id="4191b-308">É possível usar MTOM com transportes não-HTTP com WCF.</span><span class="sxs-lookup"><span data-stu-id="4191b-308">It is possible to use MTOM with non-HTTP transports with WCF.</span></span> <span data-ttu-id="4191b-309">No entanto, neste tópico vamos focar em HTTP.</span><span class="sxs-lookup"><span data-stu-id="4191b-309">However, in this topic we will focus on HTTP.</span></span>

<span data-ttu-id="4191b-310">O formato MTOM aproveita um grande conjunto de especificações que abrangem o próprio MTOM, XOP e MIME.</span><span class="sxs-lookup"><span data-stu-id="4191b-310">The MTOM format leverages a large set of specifications covering MTOM itself, XOP, and MIME.</span></span> <span data-ttu-id="4191b-311">A modularidade deste conjunto de especificações torna um pouco difícil reconstruir os requisitos exatos sobre o formato e a semântica de processamento.</span><span class="sxs-lookup"><span data-stu-id="4191b-311">Modularity of this specification set makes it somewhat difficult to reconstruct exact requirements on the format and processing semantics.</span></span> <span data-ttu-id="4191b-312">Esta seção descreve os requisitos de formato e processamento para a vinculação MTOM HTTP.</span><span class="sxs-lookup"><span data-stu-id="4191b-312">This section describes the format and processing requirements for MTOM HTTP binding.</span></span>

### <a name="mtom-message-encoding"></a><span data-ttu-id="4191b-313">Codificação de mensagens MTOM</span><span class="sxs-lookup"><span data-stu-id="4191b-313">MTOM Message Encoding</span></span>

#### <a name="generating-mtom-messages"></a><span data-ttu-id="4191b-314">Gerando mensagens MTOM</span><span class="sxs-lookup"><span data-stu-id="4191b-314">Generating MTOM messages</span></span>
<span data-ttu-id="4191b-315">A seção [XOP] 3.1 descreve o processo de codificação xml com itens de informações de elementoque contêm valores base64 em um pacote XOP definido abstratamente.</span><span class="sxs-lookup"><span data-stu-id="4191b-315">The [XOP] section 3.1 describes the process of encoding XML with element information items that contain base64 values into an abstractly defined XOP package.</span></span>

<span data-ttu-id="4191b-316">A seqüência de etapas a seguir descreve o processo de codificação específico do MTOM:</span><span class="sxs-lookup"><span data-stu-id="4191b-316">The following sequence of steps describes the MTOM-specific encoding process:</span></span>

1. <span data-ttu-id="4191b-317">Certifique-se de que o envelope SOAP a ser `[namespace name]` codificado não contém nenhum item de informação de elemento com um de `http://www.w3.org/2004/08/xop/include` e a `[local name]` de `Include`.</span><span class="sxs-lookup"><span data-stu-id="4191b-317">Ensure that the SOAP Envelope to be encoded contains no element information item with a `[namespace name]` of `http://www.w3.org/2004/08/xop/include` and a `[local name]` of `Include`.</span></span>

2. <span data-ttu-id="4191b-318">Crie um pacote MIME vazio.</span><span class="sxs-lookup"><span data-stu-id="4191b-318">Create an empty MIME package.</span></span>

3. <span data-ttu-id="4191b-319">Identifique dentro do Conjunto de informações XML original os itens de informações do elemento a serem otimizados.</span><span class="sxs-lookup"><span data-stu-id="4191b-319">Identify within the Original XML Infoset the element information items to be optimized.</span></span> <span data-ttu-id="4191b-320">Para que os itens sejam otimizados, os `[children]` caracteres que compõem o item de `xs:base64Binary` informação do elemento devem estar na forma canônica de (ver XSD-2, 3.2.16 base64Binary) e não devem conter nenhum caractere de espaço branco anterior, em linha ou seguindo o conteúdo não-espaço branco.</span><span class="sxs-lookup"><span data-stu-id="4191b-320">For the items to be optimized, the characters that make up the `[children]` of the element information item must be in the canonical form of `xs:base64Binary` (see XSD-2, 3.2.16 base64Binary) and must not contain any white-space characters preceding, inline with, or following the non-white-space content.</span></span>

4. <span data-ttu-id="4191b-321">Crie um envelope xop soap que seja uma cópia do envelope SOAP original, mas com os filhos `xop:Include` de cada item de informações de elemento identificados na etapa anterior substituído por um item de informações de elemento construído da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="4191b-321">Create an XOP SOAP Envelope that is a copy of the Original SOAP Envelope, but with the children of each element information item identified in the previous step replaced by an `xop:Include` element information item constructed as follows:</span></span>

    1. <span data-ttu-id="4191b-322">Transforme os caracteres substituídos em dados binários processando-os como dados codificados pela base64.</span><span class="sxs-lookup"><span data-stu-id="4191b-322">Transform the replaced characters into binary data by processing them as base64-encoded data.</span></span>

    2. <span data-ttu-id="4191b-323">Gerar um valor de cabeçalho exclusivo de ID de conteúdo que satisfaça os requisitos R3133 e R3134.</span><span class="sxs-lookup"><span data-stu-id="4191b-323">Generate a unique Content-ID header value that satisfies requirements R3133 and R3134.</span></span>

    3. <span data-ttu-id="4191b-324">Gerar um cabeçalho MIME de codificação de transferência de conteúdo com o binário de valor.</span><span class="sxs-lookup"><span data-stu-id="4191b-324">Generate a Content-Transfer-Encoding MIME header with the value binary.</span></span>

    4. <span data-ttu-id="4191b-325">Se o item de informações de elemento sotimizar `xop:Include` (o [pai] `xmime:contentType` do item de informações de elemento recém-inserido) `xmime:contentType` tiver um item de informações de atributo, gerare um cabeçalho MIME tipo de conteúdo com o valor do atributo.</span><span class="sxs-lookup"><span data-stu-id="4191b-325">If the element information item being optimized (the [parent] of the newly inserted `xop:Include` element information item) has an `xmime:contentType` attribute information item, generate a Content-Type MIME header with the value of the `xmime:contentType` attribute.</span></span>

    5. <span data-ttu-id="4191b-326">Gerar uma nova parte mime binária com conteúdo formado por dados binários decodificados a partir dos caracteres substituídos processados como base64, cabeçalho de ID de conteúdo a partir de 4b, cabeçalho de codificação de conteúdo a partir de 4c, cabeçalho tipo de conteúdo se gerado na etapa 4d.</span><span class="sxs-lookup"><span data-stu-id="4191b-326">Generate a new binary MIME part with content formed by binary data decoded from the replaced characters processed as base64, Content-ID header from 4b, Content- Transfer-Encoding header from 4c, Content-Type header if generated in step 4d.</span></span>

    6. <span data-ttu-id="4191b-327">Adicione `href` um atributo ao `xop:Include` elemento com o valor cid: uri derivado do valor de cabeçalho de ID de conteúdo gerado na etapa 4b.</span><span class="sxs-lookup"><span data-stu-id="4191b-327">Add an `href` attribute to the `xop:Include` element with the value cid: uri derived from Content-ID header value generated in step 4b.</span></span> <span data-ttu-id="4191b-328">Remova os caracteres\<"" e ">", escape da seqüência `cid:`de URL e adicione o prefixo .</span><span class="sxs-lookup"><span data-stu-id="4191b-328">Remove the enclosing "\<" and ">" characters, URL-escape the remaining string, and add the prefix `cid:`.</span></span> <span data-ttu-id="4191b-329">O seguinte conjunto mínimo de caracteres é necessário para ser escapado por RFC1738 e RFC2396.</span><span class="sxs-lookup"><span data-stu-id="4191b-329">The following minimum character set is required to be escaped by RFC1738 and RFC2396.</span></span> <span data-ttu-id="4191b-330">Outros personagens podem ser escapados.</span><span class="sxs-lookup"><span data-stu-id="4191b-330">Other characters can be escaped.</span></span>

        ```
        Hexadecimal 00-1F , 7F, 20, "<" | ">" | "#" | "%" | <">
        "{" | "}" | "|" | "\" | "^" | "[" | "]" | "`" | "~" | "^"
        ```

5. <span data-ttu-id="4191b-331">Crie uma parte MIME raiz com o envelope xop soap do passo 4.</span><span class="sxs-lookup"><span data-stu-id="4191b-331">Create a root MIME part with the XOP SOAP Envelope from step 4.</span></span>

6. <span data-ttu-id="4191b-332">Escreva os cabeçalhos HTTP, incluindo o cabeçalho HTTP Tipo de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="4191b-332">Write the HTTP headers, including the HTTP Content-Type header.</span></span>

7. <span data-ttu-id="4191b-333">Escreva o pacote MIME.</span><span class="sxs-lookup"><span data-stu-id="4191b-333">Write the MIME package.</span></span>

#### <a name="processing-mtom-messages"></a><span data-ttu-id="4191b-334">Processamento de mensagens MTOM</span><span class="sxs-lookup"><span data-stu-id="4191b-334">Processing MTOM messages</span></span>
<span data-ttu-id="4191b-335">O processamento de uma mensagem MTOM é o inverso exato do processo descrito na seção anterior "Gerando mensagens MTOM":</span><span class="sxs-lookup"><span data-stu-id="4191b-335">Processing of an MTOM message is the exact reverse of the process described in the preceding "Generating MTOM messages" section:</span></span>

1. <span data-ttu-id="4191b-336">Certifique-se de que a parte `application/xop+xml`RAIZ MIME tenha o Tipo de Conteúdo .</span><span class="sxs-lookup"><span data-stu-id="4191b-336">Ensure the root MIME part has the Content-Type `application/xop+xml`.</span></span>

2. <span data-ttu-id="4191b-337">Construa um envelope SOAP analisando a parte mime raiz do pacote como um documento XML.</span><span class="sxs-lookup"><span data-stu-id="4191b-337">Construct a SOAP Envelope by parsing the root MIME part of the package as an XML document.</span></span> <span data-ttu-id="4191b-338">A codificação de `charset` caracteres é determinada pelo parâmetro do Tipo de conteúdo da parte MIME raiz.</span><span class="sxs-lookup"><span data-stu-id="4191b-338">Character encoding is determined by the `charset` parameter of the Content-Type of the root MIME part.</span></span>

3. <span data-ttu-id="4191b-339">Para cada item de informação de elemento no envelope SOAP construído, que tem, `xop:Include` como único membro de sua propriedade [crianças], um item de informação de elemento:</span><span class="sxs-lookup"><span data-stu-id="4191b-339">For each element information item in the constructed SOAP Envelope, which has, as the sole member of its [children] property, an `xop:Include` element information item:</span></span>

    1. <span data-ttu-id="4191b-340">Remova `cid:` o prefixo e o inescapar todas as seqüências de `@href` saída `xop:Include` uri (RFC 2396) no valor do atributo do elemento.</span><span class="sxs-lookup"><span data-stu-id="4191b-340">Remove the `cid:` prefix and unescape all URI-escape sequences (RFC 2396) in the value of the `@href` attribute of the `xop:Include` element.</span></span> <span data-ttu-id="4191b-341">Enclose a seqüência de resultado em "\<", ">".</span><span class="sxs-lookup"><span data-stu-id="4191b-341">Enclose the result string in "\<", ">".</span></span>

    2. <span data-ttu-id="4191b-342">Localize a parte MIME com o valor de cabeçalho De ID de conteúdo que corresponde à seqüência derivada na etapa 3a.</span><span class="sxs-lookup"><span data-stu-id="4191b-342">Locate the MIME part with the Content-ID header value that matches the string derived in step 3a.</span></span>

    3. <span data-ttu-id="4191b-343">Substitua `xop:Include` o item de `children` informação do elemento que aparece na propriedade de cada item pelos itens de informação de caractereque representam a codificação base64 canônica (ver XSD-2, 3.2.16 base64Binary) do corpo da entidade da parte MIME identificada na etapa 3b (substitua efetivamente o item de informações do `xop:Include` elemento pelos dados reconstruídos a partir da peça do pacote).</span><span class="sxs-lookup"><span data-stu-id="4191b-343">Replace the `xop:Include` element information item that appears in the `children` property of each item with the character information items that represent the canonical base64 encoding (see XSD-2, 3.2.16 base64Binary) of the entity body of the MIME part identified in step 3b (effectively replace the `xop:Include` element information item with the data reconstructed from the package part).</span></span>

#### <a name="http-content-type-header"></a><span data-ttu-id="4191b-344">Cabeçalho do tipo de conteúdo HTTP</span><span class="sxs-lookup"><span data-stu-id="4191b-344">HTTP Content-Type Header</span></span>
<span data-ttu-id="4191b-345">A seguir está uma lista de esclarecimentos wcf para o formato do cabeçalho HTTP Tipo de conteúdo de uma mensagem codificada SOAP 1.x MTOM derivada de requisitos indicados na própria especificação MTOM e são derivados de MTOM e RFC 2387.</span><span class="sxs-lookup"><span data-stu-id="4191b-345">The following is a list of WCF clarifications for the format of the HTTP Content-Type header of a SOAP 1.x MTOM-encoded message derived from requirements stated in the MTOM specification itself and are derived from MTOM and RFC 2387.</span></span>

- <span data-ttu-id="4191b-346">R4131: Um cabeçalho HTTP Tipo de conteúdo deve ter o valor de multiparte/relacionado (insensível a casos) e seus parâmetros.</span><span class="sxs-lookup"><span data-stu-id="4191b-346">R4131: An HTTP Content-Type header must have the value of multipart/related (case-insensitive) and its parameters.</span></span> <span data-ttu-id="4191b-347">Nomes de parâmetros são insensíveis a casos.</span><span class="sxs-lookup"><span data-stu-id="4191b-347">Parameter names are case-insensitive.</span></span> <span data-ttu-id="4191b-348">A ordem dos parâmetros não é significativa.</span><span class="sxs-lookup"><span data-stu-id="4191b-348">Parameter order is not significant.</span></span>

- <span data-ttu-id="4191b-349">O formulário backus-naur completo (BNF) do cabeçalho tipo de conteúdo para mensagens MIME está listado no RFC 2045, seção 5.1.</span><span class="sxs-lookup"><span data-stu-id="4191b-349">The full Backus-Naur Form (BNF) of the Content-Type header for MIME messages is listed in RFC 2045, section 5.1.</span></span>

- <span data-ttu-id="4191b-350">R4132: Um cabeçalho HTTP Tipo de conteúdo `application/xop+xml` deve ter um parâmetro de tipo com o valor incluído entre aspas duplas.</span><span class="sxs-lookup"><span data-stu-id="4191b-350">R4132: An HTTP Content-Type header must have a type parameter with the value `application/xop+xml` enclosed in double quotation marks.</span></span>

<span data-ttu-id="4191b-351">Embora a exigência de usar aspas duplas não esteja explícita no RFC 2387, o texto observa que todos\@os parâmetros de tipo de mídia multiparte/relacionado provavelmente contêm caracteres reservados como " " ou "/" e, portanto, precisam de aspas duplas.</span><span class="sxs-lookup"><span data-stu-id="4191b-351">While the requirement to use double quotation marks is not explicit in RFC 2387, the text observes that all of the multipart/related media type parameters most likely contain reserved characters like "\@" or "/" and therefore need double quotation marks.</span></span>

- <span data-ttu-id="4191b-352">R4133: Um cabeçalho HTTP Tipo de conteúdo deve ter um parâmetro inicial com o valor do cabeçalho de Identificação de Conteúdo da parte MIME que contém o Envelope SOAP 1.x, incluído em aspas duplas.</span><span class="sxs-lookup"><span data-stu-id="4191b-352">R4133: An HTTP Content-Type header should have a start parameter with the value of the Content-ID header of the MIME part that contains the SOAP 1.x Envelope, enclosed in double quotation marks.</span></span> <span data-ttu-id="4191b-353">Se o parâmetro de partida for omitido, a primeira parte MIME deve conter o envelope SOAP 1.x.</span><span class="sxs-lookup"><span data-stu-id="4191b-353">If the start parameter is omitted, the first MIME part must contain the SOAP 1.x Envelope.</span></span>

- <span data-ttu-id="4191b-354">R4134: Um cabeçalho http tipo de conteúdo para uma mensagem codificada SOAP 1.1 MTOM deve incluir o parâmetro start-info com o valor de texto/xml, incluído em aspas duplas.</span><span class="sxs-lookup"><span data-stu-id="4191b-354">R4134: An HTTP Content-Type header for a SOAP 1.1 MTOM encoded message must include the start-info parameter with the value of text/xml, enclosed in double quotation marks.</span></span>

- <span data-ttu-id="4191b-355">R4135: Um cabeçalho http tipo de conteúdo para uma mensagem codificada em SOAP 1.2 MTOM deve incluir o parâmetro start-info com o valor de `application/soap+xml`, incluído em aspas duplas.</span><span class="sxs-lookup"><span data-stu-id="4191b-355">R4135: An HTTP Content-Type header for a SOAP 1.2 MTOM-encoded message must include the start-info parameter with the value of `application/soap+xml`, enclosed in double quotation marks.</span></span>

- <span data-ttu-id="4191b-356">R4136: O cabeçalho http tipo de conteúdo para uma mensagem codificada por SOAP 1.x MTOM deve ter o parâmetro de limite com o valor (incluído entre aspas duplas) que corresponde ao limite MIME BNF definido na RFC 2046, seção 5.1.1</span><span class="sxs-lookup"><span data-stu-id="4191b-356">R4136: HTTP Content-Type header for a SOAP 1.x MTOM-encoded message must have the boundary parameter with the value (enclosed in double quotation marks) that matches the MIME boundary BNF defined in RFC 2046, section 5.1.1</span></span>

    ```
    boundary := 0*69<bchars> bcharsnospace
    bchars := bcharsnospace / " "
    bcharsnospace :=    DIGIT / ALPHA / "'" / "(" / ")" / "+"
                        / "_" / "," / "-" / "." / "/" / ":" / "=" / "?"
    ```

     <span data-ttu-id="4191b-357">Exemplos:</span><span class="sxs-lookup"><span data-stu-id="4191b-357">Examples:</span></span>

     <span data-ttu-id="4191b-358">Correto</span><span class="sxs-lookup"><span data-stu-id="4191b-358">CORRECT</span></span>

    ```
    Content-Type: multipart/related; type="application/xop+xml";start=" <part0@tempuri.org>";boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1";start-info="text/xml"
    ```

     <span data-ttu-id="4191b-359">Correto</span><span class="sxs-lookup"><span data-stu-id="4191b-359">CORRECT</span></span>

    ```
    Content-Type: Multipart/Related; type="application/xop+xml";start-info="text/xml";boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1"
    ```

     <span data-ttu-id="4191b-360">Incorreto</span><span class="sxs-lookup"><span data-stu-id="4191b-360">INCORRECT</span></span>

    ```
    Content-Type: Multipart/Related; type=application/xop+xml;start=" <part0@tempuri.org>";start-info="text/xml";boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1"
    ```

#### <a name="infoset-mime-part"></a><span data-ttu-id="4191b-361">Peça MIME infoset</span><span class="sxs-lookup"><span data-stu-id="4191b-361">Infoset MIME Part</span></span>
<span data-ttu-id="4191b-362">O envelope SOAP 1.x é encapsulado como uma parte raiz do `infoset` pacote XOP MIME e é frequentemente chamado de peça.</span><span class="sxs-lookup"><span data-stu-id="4191b-362">The SOAP 1.x Envelope is encapsulated as a root part of the XOP MIME package and is often called the `infoset` part.</span></span>

- <span data-ttu-id="4191b-363">R4141: O envelope SOAP 1.x deve ser encapsulado como parte raiz `infoset` do pacote XOP MIME, chamado de peça e referenciado a partir do Tipo de Conteúdo HTTP.</span><span class="sxs-lookup"><span data-stu-id="4191b-363">R4141: The SOAP 1.x Envelope must be encapsulated as a root part of the XOP MIME package, called the `infoset` part and referenced from the HTTP Content-Type.</span></span>

- <span data-ttu-id="4191b-364">R4142: A `Infoset` parte SOAP deve incluir os `Content-ID` `Content-Transfer-Encoding`seguintes `Content-Type`cabeçalhos MIME: , e .</span><span class="sxs-lookup"><span data-stu-id="4191b-364">R4142: The SOAP `Infoset` part must include the following MIME headers: `Content-ID`, `Content-Transfer-Encoding`, and `Content-Type`.</span></span>

<span data-ttu-id="4191b-365">O formato do cabeçalho de ID de conteúdo é definido pela RFC 2045 como</span><span class="sxs-lookup"><span data-stu-id="4191b-365">The format of the Content-ID header is defined by RFC 2045 as</span></span>

```
"Content-ID" ":" msg-id
```

<span data-ttu-id="4191b-366">onde `msg-id` é definido na RFC 2822 (que substitui o RFC 822, referenciado na RFC 2045) como:</span><span class="sxs-lookup"><span data-stu-id="4191b-366">where `msg-id` is defined in RFC 2822 (that supersedes RFC 822, referenced in RFC 2045) as:</span></span>

```
msg-id    =       [CFWS] "<" id-left "@" id-right ">" [CFWS]
```

<span data-ttu-id="4191b-367">e é efetivamente um endereço\<de e-mail incluído dentro " " e ">".</span><span class="sxs-lookup"><span data-stu-id="4191b-367">and is effectively an email address enclosed within "\<" and  ">".</span></span> <span data-ttu-id="4191b-368">O `[CFWS]` prefixo e o sufixo foram adicionados na RFC 2822 para realizar comentários e não devem ser usados para preservar a interoperabilidade.</span><span class="sxs-lookup"><span data-stu-id="4191b-368">The `[CFWS]` prefix and suffix were added in RFC 2822 to carry comments and should not be used to preserve interoperability.</span></span>

<span data-ttu-id="4191b-369">R4143: O valor do cabeçalho de ID de `msg-id` conteúdo para a peça Infoset `[CFWS]` MIME deve seguir a produção da RFC 2822 com as peças de prefixo e sufixo omitidas.</span><span class="sxs-lookup"><span data-stu-id="4191b-369">R4143: The value of the Content-ID header for the Infoset MIME part must follow `msg-id` production from RFC 2822 with the `[CFWS]` prefix and suffix parts omitted.</span></span>

<span data-ttu-id="4191b-370">Uma série de implementações do MIME afrouxavam os requisitos para o valor incluído dentro "\<e ">" para ser um endereço de e-mail e usado `absoluteURI` em " "\<" " " " " " " " " " " " " " " ">" além do endereço de e-mail.</span><span class="sxs-lookup"><span data-stu-id="4191b-370">A number of MIME implementations relaxed requirements for the value enclosed within "\<" and ">" to be an email address and used `absoluteURI` enclosed in "\<" , ">" in addition to the email address.</span></span> <span data-ttu-id="4191b-371">Esta versão do WCF usa valores do cabeçalho MIME do Formulário ID de conteúdo:</span><span class="sxs-lookup"><span data-stu-id="4191b-371">This version of WCF uses values of the Content-ID MIME header of the form:</span></span>

```
Content-ID: <http://tempuri.org/0>
```

<span data-ttu-id="4191b-372">R4144: Os processadores MTOM devem aceitar valores de `msg-id`cabeçalho de ID de conteúdo que correspondam aos seguintes relaxados .</span><span class="sxs-lookup"><span data-stu-id="4191b-372">R4144: MTOM processors should accept Content-ID header values that match the following relaxed `msg-id`.</span></span>

```
msg-id-relaxed =     [CFWS] "<" (absoluteURI | mail-address) ">" [CFWS]
mail-address   =     id-left "@" id-right
```

<span data-ttu-id="4191b-373">O MIME (RFC 2045) fornece o cabeçalho codificador de transferência de conteúdo para comunicar a codificação do conteúdo da parte MIME.</span><span class="sxs-lookup"><span data-stu-id="4191b-373">MIME (RFC 2045) provides the Content-Transfer-Encoding header to communicate encoding of the content of the MIME part.</span></span> <span data-ttu-id="4191b-374">O padrão definido para codificação de transferência de conteúdo é de 7 bits, o que não é adequado para a maioria das mensagens SOAP, de modo que o cabeçalho de codificação de transferência de conteúdo é necessário para maior interoperabilidade:</span><span class="sxs-lookup"><span data-stu-id="4191b-374">The default defined for Content-Transfer-Encoding is 7-bit, which is not suitable for most SOAP messages, so the Content-Transfer-Encoding header is needed for greater interoperability:</span></span>

- <span data-ttu-id="4191b-375">R4145: A parte do SOAP Infoset deve conter o cabeçalho codificador de transferência de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="4191b-375">R4145: The SOAP Infoset part must contain the Content-Transfer-Encoding header.</span></span>

- <span data-ttu-id="4191b-376">R4146: Se a codificação do caractere SOAP Envelope for UTF-8, o valor do cabeçalho codificador de transferência de conteúdo deve ser de 8 bits.</span><span class="sxs-lookup"><span data-stu-id="4191b-376">R4146: If the SOAP Envelope character encoding is UTF-8, the value of the Content-Transfer-Encoding header must be 8-bit.</span></span>

- <span data-ttu-id="4191b-377">R4147: Se a codificação do caractere SOAP Envelope for UTF-16, o valor do cabeçalho codificador de transferência de conteúdo deve ser binário.</span><span class="sxs-lookup"><span data-stu-id="4191b-377">R4147: If the SOAP Envelope character encoding is UTF-16, the value of the Content-Transfer-Encoding header must be binary.</span></span>

- <span data-ttu-id="4191b-378">De acordo com a seção 5 da [XOP],</span><span class="sxs-lookup"><span data-stu-id="4191b-378">According to [XOP] section 5,</span></span>

- <span data-ttu-id="4191b-379">R4148: SOAP1.1 A parte do infoset deve conter cabeçalho tipo de conteúdo com aplicativo do tipo de mídia/xop+xml e parâmetros tipo="texto/xml" e charset</span><span class="sxs-lookup"><span data-stu-id="4191b-379">R4148: SOAP1.1 Infoset part must contain Content-Type header with media type application/xop+xml and parameters type="text/xml" and charset</span></span>

    ```
    Content-Type: application/xop+xml;
                  charset=utf-8;type="text/xml"
    ```

- <span data-ttu-id="4191b-380">R4149: A parte DO INFOSET SOAP 1.2 deve `application/xop+xml` conter o cabeçalho tipo de conteúdo com tipo de mídia e tipo de parâmetros="`application/soap+xml`e `charset`.</span><span class="sxs-lookup"><span data-stu-id="4191b-380">R4149: The SOAP 1.2 Infoset part must contain the Content-Type header with media type `application/xop+xml` and parameters type="`application/soap+xml`" and `charset`.</span></span>

    ```
    Content-Type: application/xop+xml;
                  charset=utf-8;type="application/soap+xml"
    ```

     <span data-ttu-id="4191b-381">Embora o XOP `charset` defina `application/xop+xml` o parâmetro para ser opcional, é necessário para interoperabilidade `charset` semelhante ao `text/xml` requisito BP 1.1 no parâmetro para o tipo de mídia.</span><span class="sxs-lookup"><span data-stu-id="4191b-381">While XOP defines the `charset` parameter for `application/xop+xml` to be optional, it is needed for interoperability similar to the BP 1.1 requirement on the `charset` parameter for the `text/xml` media type.</span></span>

- <span data-ttu-id="4191b-382">R41410: `type` Os `charset` parâmetros devem estar presentes no cabeçalho tipo de conteúdo da peça SOAP 1.x Infoset.</span><span class="sxs-lookup"><span data-stu-id="4191b-382">R41410: The `type` and `charset` parameters must be present on the Content-Type header of the SOAP 1.x Infoset part.</span></span>

#### <a name="wcf-endpoint-support-for-mtom"></a><span data-ttu-id="4191b-383">Suporte ao ponto final do WCF para MTOM</span><span class="sxs-lookup"><span data-stu-id="4191b-383">WCF Endpoint Support for MTOM</span></span>
<span data-ttu-id="4191b-384">O objetivo do MTOM é codificar uma mensagem SOAP para otimizar dados codificados com base64.</span><span class="sxs-lookup"><span data-stu-id="4191b-384">The purpose of MTOM is to encode a SOAP message to optimize base64-encoded data.</span></span> <span data-ttu-id="4191b-385">A seguir está uma lista de restrições:</span><span class="sxs-lookup"><span data-stu-id="4191b-385">The following is a list of constraints:</span></span>

- <span data-ttu-id="4191b-386">R4151: Qualquer item de informação de elemento que contenha dados codificados com base64 pode ser otimizado.</span><span class="sxs-lookup"><span data-stu-id="4191b-386">R4151: Any element information item that contains base64-encoded data may be optimized.</span></span>

- <span data-ttu-id="4191b-387">B4152: O WCF otimiza itens de informação de elementos que contêm dados codificados base64 e excedem 1024 bytes de comprimento.</span><span class="sxs-lookup"><span data-stu-id="4191b-387">B4152: WCF optimizes element information items that contain base64-encoded data and exceed 1024 bytes in length.</span></span>

<span data-ttu-id="4191b-388">Um ponto final wcf configurado para usar o MTOM sempre enviará mensagens codificadas pelo MTOM.</span><span class="sxs-lookup"><span data-stu-id="4191b-388">A WCF endpoint configured to use MTOM will always send MTOM-encoded messages.</span></span> <span data-ttu-id="4191b-389">Mesmo que nenhuma peça atenda aos critérios necessários, a mensagem ainda é codificada em MTOM (serializada como um pacote MIME com uma única peça MIME contendo o envelope SOAP).</span><span class="sxs-lookup"><span data-stu-id="4191b-389">Even if no parts meet the required criteria, the message is still MTOM-encoded (serialized as a MIME package with a single MIME part containing the SOAP envelope).</span></span>

### <a name="ws-policy-assertion-for-mtom"></a><span data-ttu-id="4191b-390">Afirmação da política WS para MTOM</span><span class="sxs-lookup"><span data-stu-id="4191b-390">WS-Policy Assertion for MTOM</span></span>
<span data-ttu-id="4191b-391">O WCF usa a seguinte afirmação de diretiva para indicar o uso do MTOM por ponto final:</span><span class="sxs-lookup"><span data-stu-id="4191b-391">WCF uses the following policy assertion to indicate MTOM usage by endpoint:</span></span>

```xml
<wsoma:OptimizedMimeSerialization />
```

- <span data-ttu-id="4191b-392">R4211: A afirmação da diretiva anterior tem um Assunto de Política de Ponto Final e especifica que todas as mensagens enviadas e recebidas do ponto final devem ser otimizadas usando o MTOM.</span><span class="sxs-lookup"><span data-stu-id="4191b-392">R4211: The preceding policy assertion has an Endpoint Policy Subject and specifies that all messages sent to and received from the endpoint must be optimized using MTOM.</span></span>

- <span data-ttu-id="4191b-393">B4212: Quando configurado para usar a otimização do MTOM, um ponto final do `wsdl:binding`WCF adiciona uma afirmação de diretiva MTOM à diretiva anexada ao correspondente .</span><span class="sxs-lookup"><span data-stu-id="4191b-393">B4212: When configured to use MTOM optimization, an WCF endpoint adds an MTOM Policy assertion to the policy attached to the corresponding `wsdl:binding`.</span></span>

### <a name="composition-with-ws-security"></a><span data-ttu-id="4191b-394">Composição com WS-Security</span><span class="sxs-lookup"><span data-stu-id="4191b-394">Composition with WS-Security</span></span>
<span data-ttu-id="4191b-395">MTOM é um mecanismo de `text/xml` codificação semelhante ao WCF Binary XML.</span><span class="sxs-lookup"><span data-stu-id="4191b-395">MTOM is an encoding mechanism that is similar to `text/xml` and WCF Binary XML.</span></span> <span data-ttu-id="4191b-396">O MTOM oferece composição natural com o WS-Security e outros protocolos WS-\*: uma mensagem protegida usando o WS-Security pode ser otimizada usando o MTOM.</span><span class="sxs-lookup"><span data-stu-id="4191b-396">MTOM offers natural composition with WS-Security and other WS-\* protocols: a message secured using WS-Security can be optimized using MTOM.</span></span>

### <a name="examples"></a><span data-ttu-id="4191b-397">Exemplos</span><span class="sxs-lookup"><span data-stu-id="4191b-397">Examples</span></span>

#### <a name="wcf-soap-11-message-encoded-using-mtom"></a><span data-ttu-id="4191b-398">WCF SOAP 1.1 Mensagem Codificada Usando MTOM</span><span class="sxs-lookup"><span data-stu-id="4191b-398">WCF SOAP 1.1 Message Encoded Using MTOM</span></span>

```
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

#### <a name="wcf-secure-soap-12-message-encoded-using-mtom"></a><span data-ttu-id="4191b-399">WCF Secure SOAP 1.2 Mensagem Codificada Usando MTOM</span><span class="sxs-lookup"><span data-stu-id="4191b-399">WCF Secure SOAP 1.2 Message Encoded Using MTOM</span></span>
<span data-ttu-id="4191b-400">Neste exemplo, uma mensagem é codificada usando MTOM e SOAP 1.2 que é protegido usando O WS-Security.</span><span class="sxs-lookup"><span data-stu-id="4191b-400">In this example, a message is encoded using MTOM and SOAP 1.2 that is protected using WS-Security.</span></span> <span data-ttu-id="4191b-401">As partes binárias identificadas para `BinarySecurityToken` `CipherValue` codificação `EncryptedData` são o conteúdo do , do correspondente à assinatura criptografada e corpo criptografado.</span><span class="sxs-lookup"><span data-stu-id="4191b-401">The binary parts identified for encoding are the contents of the `BinarySecurityToken`, `CipherValue` of the `EncryptedData` corresponding to the encrypted signature and encrypted body.</span></span> <span data-ttu-id="4191b-402">Note-se `CipherValue` que `EncryptedKey` o do não foi identificado para otimização pelo WCF, pois seu comprimento é menor que 1024 bytes.</span><span class="sxs-lookup"><span data-stu-id="4191b-402">Note that the `CipherValue` of the `EncryptedKey` was not identified for optimization by WCF, because its length is less then 1024 bytes.</span></span>

```
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
