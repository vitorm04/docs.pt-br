---
title: Protocolos de mensagens
ms.date: 03/30/2017
ms.assetid: 5b20bca7-87b3-4c8f-811b-f215b5987104
ms.openlocfilehash: 3e56636e8364eec333f9585a0f62f6510561d1cc
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/09/2018
ms.locfileid: "44253059"
---
# <a name="messaging-protocols"></a><span data-ttu-id="60026-102">Protocolos de mensagens</span><span class="sxs-lookup"><span data-stu-id="60026-102">Messaging Protocols</span></span>
<span data-ttu-id="60026-103">A pilha de canais do Windows Communication Foundation (WCF) emprega canais de transporte e de codificação para transformar a representação interna de mensagem em seu formato de transmissão e enviá-lo por meio de um transporte particular.</span><span class="sxs-lookup"><span data-stu-id="60026-103">The Windows Communication Foundation (WCF) channel stack employs encoding and transport channels to transform internal message representation into its wire format and send it by using a particular transport.</span></span> <span data-ttu-id="60026-104">O transporte mais comuns usado para a interoperabilidade de serviços da Web é HTTP, e as codificações mais comuns usadas pelos serviços da Web são baseados em XML SOAP 1.1, SOAP 1.2 e MTOM Message Transmission Optimization Mechanism ().</span><span class="sxs-lookup"><span data-stu-id="60026-104">The most common transport used for Web services interoperability is HTTP, and the most common encodings used by Web services are XML-based SOAP 1.1, SOAP 1.2, and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="60026-105">Este tópico abrange detalhes de implementação de WCF para os seguintes protocolos utilizados por <xref:System.ServiceModel.Channels.HttpTransportBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="60026-105">This topic covers WCF implementation details for the following protocols employed by <xref:System.ServiceModel.Channels.HttpTransportBindingElement>.</span></span>  
  
|<span data-ttu-id="60026-106">Especificação/documento</span><span class="sxs-lookup"><span data-stu-id="60026-106">Specification/document</span></span>|<span data-ttu-id="60026-107">Vincular</span><span class="sxs-lookup"><span data-stu-id="60026-107">Link</span></span>|  
|-----------------------------|----------|  
|<span data-ttu-id="60026-108">HTTP 1.1</span><span class="sxs-lookup"><span data-stu-id="60026-108">HTTP 1.1</span></span>|http://www.ietf.org/rfc/rfc2616.txt|  
|<span data-ttu-id="60026-109">Ligação de SOAP 1.1 HTTP</span><span class="sxs-lookup"><span data-stu-id="60026-109">SOAP 1.1 HTTP Binding</span></span>|<span data-ttu-id="60026-110">http://www.w3.org/TR/2000/NOTE-SOAP-20000508/, Seção 7</span><span class="sxs-lookup"><span data-stu-id="60026-110">http://www.w3.org/TR/2000/NOTE-SOAP-20000508/, Section 7</span></span>|  
|<span data-ttu-id="60026-111">SOAP 1.2 associação de HTTP</span><span class="sxs-lookup"><span data-stu-id="60026-111">SOAP 1.2 HTTP Binding</span></span>|<span data-ttu-id="60026-112">http://www.w3.org/TR/soap12-part2/, Seção 7</span><span class="sxs-lookup"><span data-stu-id="60026-112">http://www.w3.org/TR/soap12-part2/, Section 7</span></span>|  
  
 <span data-ttu-id="60026-113">Este tópico abrange detalhes de implementação de WCF para os seguintes protocolos <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> e <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> empregar.</span><span class="sxs-lookup"><span data-stu-id="60026-113">This topic covers WCF implementation details for the following protocols  that <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> and <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> employ.</span></span>  
  
|<span data-ttu-id="60026-114">Especificação/documento</span><span class="sxs-lookup"><span data-stu-id="60026-114">Specification/Document</span></span>|<span data-ttu-id="60026-115">Vincular</span><span class="sxs-lookup"><span data-stu-id="60026-115">Link</span></span>|  
|-----------------------------|----------|  
|<span data-ttu-id="60026-116">XML</span><span class="sxs-lookup"><span data-stu-id="60026-116">XML</span></span>|http://www.w3.org/TR/REC-xml|  
|<span data-ttu-id="60026-117">SOAP 1.1</span><span class="sxs-lookup"><span data-stu-id="60026-117">SOAP 1.1</span></span>|http://www.w3.org/TR/2000/NOTE-SOAP-20000508/|  
|<span data-ttu-id="60026-118">SOAP 1.2 Core</span><span class="sxs-lookup"><span data-stu-id="60026-118">SOAP 1.2 Core</span></span>|http://www.w3.org/TR/soap12-part1/|  
|<span data-ttu-id="60026-119">2004 de WS-Addressing/08</span><span class="sxs-lookup"><span data-stu-id="60026-119">WS-Addressing 2004/08</span></span>|http://www.w3.org/Submission/2004/SUBM-ws-addressing-20040810/|  
|<span data-ttu-id="60026-120">1.0 - Core endereçamento de serviços Web do W3C</span><span class="sxs-lookup"><span data-stu-id="60026-120">W3C Web Services Addressing 1.0 - Core</span></span>|http://www.w3.org/TR/2006/REC-ws-addr-core-20060509|  
|<span data-ttu-id="60026-121">Endereçamento 1.0 - associação de SOAP de serviços de Web do W3C</span><span class="sxs-lookup"><span data-stu-id="60026-121">W3C Web Services Addressing 1.0 - SOAP Binding</span></span>|http://www.w3.org/TR/2006/REC-ws-addr-soap-20060509|  
|<span data-ttu-id="60026-122">Endereçamento 1.0 - associação de WSDL de serviços de Web do W3C</span><span class="sxs-lookup"><span data-stu-id="60026-122">W3C Web Services Addressing 1.0 - WSDL Binding</span></span>|http://www.w3.org/TR/2006/CR-ws-addr-wsdl-20060529/|  
<span data-ttu-id="60026-123">1.0 - metadados endereçamento de serviços Web do W3C</span><span class="sxs-lookup"><span data-stu-id="60026-123">W3C Web Services Addressing 1.0 - Metadata</span></span>|http://www.w3.org/TR/ws-addr-metadata/|  
|<span data-ttu-id="60026-124">Associação de SOAP1.1 WSDL</span><span class="sxs-lookup"><span data-stu-id="60026-124">WSDL SOAP1.1 Binding</span></span>|http://www.w3.org/TR/wsdl/|  
|<span data-ttu-id="60026-125">Associação de SOAP1.2 WSDL</span><span class="sxs-lookup"><span data-stu-id="60026-125">WSDL SOAP1.2 Binding</span></span>|http://www.w3.org/Submission/wsdl11soap12/|  
  
 <span data-ttu-id="60026-126">Este tópico abrange detalhes de implementação de WCF para protocolos a seguir <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> emprega.</span><span class="sxs-lookup"><span data-stu-id="60026-126">This topic covers WCF implementation details for the following protocols that <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> employs.</span></span>  
  
|<span data-ttu-id="60026-127">Especificação/documento</span><span class="sxs-lookup"><span data-stu-id="60026-127">Specification/document</span></span>|<span data-ttu-id="60026-128">Vincular</span><span class="sxs-lookup"><span data-stu-id="60026-128">Link</span></span>|  
|-----------------------------|----------|  
|<span data-ttu-id="60026-129">XOP</span><span class="sxs-lookup"><span data-stu-id="60026-129">XOP</span></span>|http://www.w3.org/TR/xop10/|  
|<span data-ttu-id="60026-130">MTOM + SOAP 1.2 de associação</span><span class="sxs-lookup"><span data-stu-id="60026-130">MTOM + SOAP 1.2 Binding</span></span>|http://www.w3.org/TR/soap12-mtom/|  
|<span data-ttu-id="60026-131">MTOM ligação de SOAP 1.1</span><span class="sxs-lookup"><span data-stu-id="60026-131">MTOM SOAP 1.1 Binding</span></span>|http://www.w3.org/Submission/soap11mtom10/|  
|<span data-ttu-id="60026-132">Asserção do WS-Policy MTOM</span><span class="sxs-lookup"><span data-stu-id="60026-132">MTOM WS-Policy Assertion</span></span>|<span data-ttu-id="60026-133">http://www.w3.org/Submission/2006/SUBM-WS-MTOMPolicy-20061101/.</span><span class="sxs-lookup"><span data-stu-id="60026-133">http://www.w3.org/Submission/2006/SUBM-WS-MTOMPolicy-20061101/.</span></span>|  
  
 <span data-ttu-id="60026-134">Os seguintes namespaces XML e prefixos associados são usados ao longo deste tópico.</span><span class="sxs-lookup"><span data-stu-id="60026-134">The following XML namespaces and associated prefixes are used throughout this topic.</span></span>  
  
|<span data-ttu-id="60026-135">Prefixo</span><span class="sxs-lookup"><span data-stu-id="60026-135">Prefix</span></span>|<span data-ttu-id="60026-136">Namespace Uniform Resource Identifier (URI)</span><span class="sxs-lookup"><span data-stu-id="60026-136">Namespace Uniform Resource Identifier (URI)</span></span>|  
|------------|---------------------------------------------------|  
|<span data-ttu-id="60026-137">s11</span><span class="sxs-lookup"><span data-stu-id="60026-137">s11</span></span>|http://schemas.xmlsoap.org/soap/envelope|  
|<span data-ttu-id="60026-138">s12</span><span class="sxs-lookup"><span data-stu-id="60026-138">s12</span></span>|http://www.w3.org/2003/05/soap-envelope|  
|<span data-ttu-id="60026-139">wsa</span><span class="sxs-lookup"><span data-stu-id="60026-139">wsa</span></span>|http://www.w3.org/2004/08/addressing|  
|<span data-ttu-id="60026-140">wsam</span><span class="sxs-lookup"><span data-stu-id="60026-140">wsam</span></span>|http://www.w3.org/2007/05/addressing/metadata|  
|<span data-ttu-id="60026-141">wsap</span><span class="sxs-lookup"><span data-stu-id="60026-141">wsap</span></span>|http://schemas.xmlsoap.org/ws/2004/09/policy/addressing|  
|<span data-ttu-id="60026-142">wsa10</span><span class="sxs-lookup"><span data-stu-id="60026-142">wsa10</span></span>|http://www.w3.org/2005/08/addressing|  
|<span data-ttu-id="60026-143">wsaw10</span><span class="sxs-lookup"><span data-stu-id="60026-143">wsaw10</span></span>|http://www.w3.org/2006/05/addressing/wsdl|  
|<span data-ttu-id="60026-144">XOP</span><span class="sxs-lookup"><span data-stu-id="60026-144">xop</span></span>|http://www.w3.org/2004/08/xop/include|  
|<span data-ttu-id="60026-145">xmime</span><span class="sxs-lookup"><span data-stu-id="60026-145">xmime</span></span>|http://www.w3.org/2004/06/xmlmime<br /><br /> http://www.w3.org/2005/05/xmlmime|  
<span data-ttu-id="60026-146">ponto de distribuição</span><span class="sxs-lookup"><span data-stu-id="60026-146">dp</span></span>|http://schemas.microsoft.com/net/2006/06/duplex|  
  
## <a name="soap-11-and-soap-12"></a><span data-ttu-id="60026-147">SOAP 1.1 e SOAP 1.2</span><span class="sxs-lookup"><span data-stu-id="60026-147">SOAP 1.1 and SOAP 1.2</span></span>  
  
### <a name="envelope-and-processing-model"></a><span data-ttu-id="60026-148">Envelope e processamento de modelo</span><span class="sxs-lookup"><span data-stu-id="60026-148">Envelope and Processing Model</span></span>  
 <span data-ttu-id="60026-149">O WCF implementa o processamento do envelope SOAP 1.1 Basic Profile 1.1 (BP11) e o Basic Profile 1.0 (SSBP10) a seguir.</span><span class="sxs-lookup"><span data-stu-id="60026-149">WCF implements SOAP 1.1 envelope processing following Basic Profile 1.1 (BP11) and Basic Profile 1.0 (SSBP10).</span></span> <span data-ttu-id="60026-150">SOAP 1.2 Envelope processamento é implementado Parte1 SOAP12 a seguir.</span><span class="sxs-lookup"><span data-stu-id="60026-150">SOAP 1.2 Envelope processing is implemented following SOAP12-Part1.</span></span>  
  
 <span data-ttu-id="60026-151">Esta seção explica a certas opções de implementação tomadas pelo WCF em relação a BP11 e SOAP12 Parte1.</span><span class="sxs-lookup"><span data-stu-id="60026-151">This section explains certain implementation choices taken by WCF with regard to BP11 and SOAP12-Part1.</span></span>  
  
#### <a name="mandatory-header-processing"></a><span data-ttu-id="60026-152">Processamento de cabeçalho obrigatórios</span><span class="sxs-lookup"><span data-stu-id="60026-152">Mandatory Header Processing</span></span>  
 <span data-ttu-id="60026-153">WCF segue as regras para processar cabeçalhos marcado `mustUnderstand` descrito nas especificações SOAP 1.1 e SOAP 1.2, com as seguintes variações.</span><span class="sxs-lookup"><span data-stu-id="60026-153">WCF follows rules for processing headers marked `mustUnderstand` described in the SOAP 1.1 and SOAP 1.2 specifications, with the following variations.</span></span>  
  
 <span data-ttu-id="60026-154">Uma mensagem que entra a pilha de canais do WCF é processada por canais individuais configurados por elementos de ligação associada, por exemplo, codificação de mensagem de texto, segurança, mensagens confiáveis e transações.</span><span class="sxs-lookup"><span data-stu-id="60026-154">A message that enters the WCF channel stack is processed by individual channels configured by associated binding elements, for example, Text Message Encoding, Security, Reliable Messaging, and Transactions.</span></span> <span data-ttu-id="60026-155">Cada canal reconhece os cabeçalhos do namespace associado e os marca como compreendido.</span><span class="sxs-lookup"><span data-stu-id="60026-155">Each channel recognizes headers from the associated namespace and marks them as understood.</span></span> <span data-ttu-id="60026-156">Depois que uma mensagem insere o dispatcher, o formatador de operação lê cabeçalhos esperados pelo contrato de mensagem/operação correspondente e marcas-los compreendidos.</span><span class="sxs-lookup"><span data-stu-id="60026-156">Once a message enters the dispatcher, the operation formatter reads headers expected by the corresponding message/operation contract and marks them understood.</span></span> <span data-ttu-id="60026-157">Em seguida, o dispatcher verifica se todos os cabeçalhos restantes não são compreendidos mas marcados como `mustUnderstand` e gera uma exceção.</span><span class="sxs-lookup"><span data-stu-id="60026-157">Then the dispatcher verifies whether any remaining headers are not understood but marked as `mustUnderstand` and throws an exception.</span></span> <span data-ttu-id="60026-158">Mensagens que contêm `mustUnderstand` cabeçalhos que são destinados ao destinatário não são processados pelo código do aplicativo de destino.</span><span class="sxs-lookup"><span data-stu-id="60026-158">Messages that contain `mustUnderstand` headers that are targeted at the recipient are not processed by recipient application code.</span></span>  
  
 <span data-ttu-id="60026-159">Como em camadas de processamento permite a separação entre as camadas de infraestrutura e aplicativo do nó SOAP:</span><span class="sxs-lookup"><span data-stu-id="60026-159">Such layered processing allows for separation between infrastructure layers and application layers of the SOAP node:</span></span>  
  
-   <span data-ttu-id="60026-160">B1111: Os cabeçalhos que não são compreendidos são detectados depois que a mensagem é processada pela pilha de canal de infraestrutura do WCF, mas antes de ser processada pelo aplicativo</span><span class="sxs-lookup"><span data-stu-id="60026-160">B1111: Headers that are not understood are detected after the message is processed by the WCF infrastructure channel stack, but before it is processed by application</span></span>  
  
     <span data-ttu-id="60026-161">O `mustUnderstand` difere do valor de cabeçalho entre SOAP 1.1 e SOAP 1.2.</span><span class="sxs-lookup"><span data-stu-id="60026-161">The `mustUnderstand` header value differs between SOAP 1.1 and SOAP 1.2.</span></span> <span data-ttu-id="60026-162">Basic Profile 1.1 requer que o `mustUnderstand` valor ser 0 ou 1 para mensagens SOAP 1.1.</span><span class="sxs-lookup"><span data-stu-id="60026-162">Basic Profile 1.1 requires that the `mustUnderstand` value be 0 or 1 for SOAP 1.1 messages.</span></span> <span data-ttu-id="60026-163">SOAP 1.2 permite 0, 1, `false`, e `true` como valores, mas recomenda emitindo uma representação canônica do `xs:boolean` valores (`false`, `true`).</span><span class="sxs-lookup"><span data-stu-id="60026-163">SOAP 1.2 allows 0, 1, `false`, and `true` as values, but recommends emitting a canonical representation of `xs:boolean` values (`false`, `true`).</span></span>  
  
-   <span data-ttu-id="60026-164">B1112: Emite de WCF `mustUnderstand` valores 0 e 1 para versões de SOAP 1.1 e SOAP 1.2 do envelope SOAP.</span><span class="sxs-lookup"><span data-stu-id="60026-164">B1112: WCF emits `mustUnderstand` values 0 and 1 for both SOAP 1.1 and SOAP 1.2 versions of the SOAP envelope.</span></span> <span data-ttu-id="60026-165">WCF aceita o espaço de todo o valor de `xs:boolean` para o `mustUnderstand` cabeçalho (0, 1, `false`, `true`)</span><span class="sxs-lookup"><span data-stu-id="60026-165">WCF accepts the entire value space of `xs:boolean` for the `mustUnderstand` header (0, 1, `false`, `true`)</span></span>  
  
#### <a name="soap-faults"></a><span data-ttu-id="60026-166">Falhas de SOAP</span><span class="sxs-lookup"><span data-stu-id="60026-166">SOAP Faults</span></span>  
 <span data-ttu-id="60026-167">A seguir está uma lista das implementações de falhas SOAP específicas do WCF.</span><span class="sxs-lookup"><span data-stu-id="60026-167">The following is a list of WCF-specific SOAP fault implementations.</span></span>  
  
-   <span data-ttu-id="60026-168">B2121: WCF retorna os seguintes códigos de falha de SOAP 1.1: `s11:mustUnderstand`, `s11:Client`, e `s11:Server`.</span><span class="sxs-lookup"><span data-stu-id="60026-168">B2121: WCF returns the following SOAP 1.1 Fault Codes: `s11:mustUnderstand`, `s11:Client`, and `s11:Server`.</span></span>  
  
-   <span data-ttu-id="60026-169">B2122: WCF retorna os seguintes códigos de falha de SOAP 1.2: `s12:MustUnderstand`, `s12:Sender`, e `s12:Receiver`.</span><span class="sxs-lookup"><span data-stu-id="60026-169">B2122: WCF returns the following SOAP 1.2 Fault Codes: `s12:MustUnderstand`, `s12:Sender`, and `s12:Receiver`.</span></span>  
  
### <a name="http-binding"></a><span data-ttu-id="60026-170">Associação de HTTP</span><span class="sxs-lookup"><span data-stu-id="60026-170">HTTP Binding</span></span>  
  
#### <a name="soap-11-http-binding"></a><span data-ttu-id="60026-171">Ligação de SOAP 1.1 HTTP</span><span class="sxs-lookup"><span data-stu-id="60026-171">SOAP 1.1 HTTP Binding</span></span>  
 <span data-ttu-id="60026-172">O WCF implementa a associação HTTP SOAP1.1 seguindo a seção 3.4 com os seguintes esclarecimentos de especificação do Basic Profile 1.1:</span><span class="sxs-lookup"><span data-stu-id="60026-172">WCF implements SOAP1.1 HTTP binding following the Basic Profile 1.1 specification section 3.4 with the following clarifications:</span></span>  
  
-   <span data-ttu-id="60026-173">B2211: Serviço do WCF não implementa o redirecionamento de solicitações HTTP POST.</span><span class="sxs-lookup"><span data-stu-id="60026-173">B2211: WCF service does not implement redirection of HTTP POST requests.</span></span>  
  
-   <span data-ttu-id="60026-174">B2212: Clientes do WCF dão suporte a Cookies HTTP de acordo com a 3.4.8.</span><span class="sxs-lookup"><span data-stu-id="60026-174">B2212: WCF clients support HTTP Cookies in accordance with 3.4.8.</span></span>  
  
#### <a name="soap-12-http-binding"></a><span data-ttu-id="60026-175">SOAP 1.2 associação de HTTP</span><span class="sxs-lookup"><span data-stu-id="60026-175">SOAP 1.2 HTTP Binding</span></span>  
 <span data-ttu-id="60026-176">O WCF implementa associação SOAP 1.2 HTTP, conforme descrito na SOAP 1.2-parte 2 (SOAP12Part2) especificação com os seguintes esclarecimentos.</span><span class="sxs-lookup"><span data-stu-id="60026-176">WCF implements SOAP 1.2 HTTP binding as described in the SOAP 1.2-part 2 (SOAP12Part2) specification with the following clarifications.</span></span>  
  
 <span data-ttu-id="60026-177">SOAP 1.2 introduziu um parâmetro de ação opcional para o `application/soap+xml` tipo de mídia.</span><span class="sxs-lookup"><span data-stu-id="60026-177">SOAP 1.2 introduced an optional action parameter for the `application/soap+xml` media type.</span></span> <span data-ttu-id="60026-178">Esse parâmetro é útil para otimizar a expedição de mensagens sem a necessidade de que o corpo da mensagem SOAP ser analisado ao WS-Addressing não é usado.</span><span class="sxs-lookup"><span data-stu-id="60026-178">This parameter is useful to optimize message dispatch without requiring that the body of the SOAP message be parsed when WS-Addressing is not used.</span></span>  
  
-   <span data-ttu-id="60026-179">R2221: O `application/soap+xml` parâmetro de ação, quando presente em uma solicitação de SOAP 1.2, deve corresponder a `soapAction` o atributo no `wsoap12:operation` elemento dentro de associação WSDL correspondente.</span><span class="sxs-lookup"><span data-stu-id="60026-179">R2221: The `application/soap+xml` action parameter, when present on a SOAP 1.2 request, must match the `soapAction` attribute on the `wsoap12:operation` element inside the corresponding WSDL binding.</span></span>  
  
-   <span data-ttu-id="60026-180">R2222: O `application/soap+xml` parâmetro de ação, quando presentes em uma mensagem SOAP 1.2, deve corresponder ao `wsa:Action` quando 2004 de WS-Addressing/08 ou WS-Addressing 1.0 são usadas.</span><span class="sxs-lookup"><span data-stu-id="60026-180">R2222: The `application/soap+xml` action parameter, when present on a SOAP 1.2 message, must match `wsa:Action` when WS-Addressing 2004/08 or WS-Addressing 1.0 are used.</span></span>  
  
 <span data-ttu-id="60026-181">Quando o WS-Addressing é desabilitado e uma solicitação de entrada não contém um parâmetro de ação, uma mensagem `Action` é considerada como não especificado.</span><span class="sxs-lookup"><span data-stu-id="60026-181">When WS-Addressing is disabled and an incoming request does not contain an action parameter, message `Action` is considered not specified.</span></span>  
  
## <a name="ws-addressing"></a><span data-ttu-id="60026-182">WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="60026-182">WS-Addressing</span></span>  
 <span data-ttu-id="60026-183">O WCF implementa as 3 versões do WS-Addressing:</span><span class="sxs-lookup"><span data-stu-id="60026-183">WCF implements 3 versions of WS-Addressing:</span></span>  
  
-   <span data-ttu-id="60026-184">2004 de WS-Addressing/08</span><span class="sxs-lookup"><span data-stu-id="60026-184">WS-Addressing 2004/08</span></span>  
  
-   <span data-ttu-id="60026-185">Serviços Web do W3C endereçamento 1.0 Core (ADDR10-núcleo) e SOAP associação (ADDR10 SOAP)</span><span class="sxs-lookup"><span data-stu-id="60026-185">W3C Web Services Addressing 1.0 Core  (ADDR10-CORE) and SOAP Binding (ADDR10-SOAP)</span></span>  
  
-   <span data-ttu-id="60026-186">WS-Addressing 1.0 - metadados</span><span class="sxs-lookup"><span data-stu-id="60026-186">WS-Addressing 1.0 - Metadata</span></span>  
  
### <a name="endpoint-references"></a><span data-ttu-id="60026-187">Referências de ponto de extremidade</span><span class="sxs-lookup"><span data-stu-id="60026-187">Endpoint References</span></span>  
 <span data-ttu-id="60026-188">Todas as versões do WS-Addressing que o WCF implementa usam referências de ponto de extremidade para descrever os pontos de extremidade.</span><span class="sxs-lookup"><span data-stu-id="60026-188">All versions of WS-Addressing that WCF implements use endpoint references to describe endpoints.</span></span>  
  
#### <a name="endpoint-references-and-ws-addressing-versions"></a><span data-ttu-id="60026-189">Referências de ponto de extremidade e WS-Addressing versões</span><span class="sxs-lookup"><span data-stu-id="60026-189">Endpoint References and WS-Addressing Versions</span></span>  
 <span data-ttu-id="60026-190">O WCF implementa um número dos protocolos de infraestrutura que usam o WS-Addressing e, em particular a `EndpointReference` elemento e `W3C.WsAddressing.EndpointReferenceType` classe (por exemplo, WS-ReliableMessaging, WS-SecureConversation e WS-Trust).</span><span class="sxs-lookup"><span data-stu-id="60026-190">WCF implements a number of the infrastructure protocols that use WS-Addressing and in particular the `EndpointReference` element and `W3C.WsAddressing.EndpointReferenceType` class (for example, WS-ReliableMessaging, WS-SecureConversation, and WS-Trust).</span></span> <span data-ttu-id="60026-191">O WCF oferece suporte ao uso de qualquer versão do WS-Addressing com outros protocolos de infraestrutura.</span><span class="sxs-lookup"><span data-stu-id="60026-191">WCF supports the use of either version of WS-Addressing with other infrastructure protocols.</span></span> <span data-ttu-id="60026-192">Pontos de extremidade do WCF dão suporte a uma versão do WS-Addressing por ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="60026-192">WCF endpoints support one version of WS-Addressing per endpoint.</span></span>  
  
 <span data-ttu-id="60026-193">Para R3111, o namespace para o `EndpointReference` elemento ou tipo usado em mensagens trocadas com um ponto de extremidade do WCF deve corresponder à versão do WS-Addressing implementada por esse ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="60026-193">For R3111, the namespace for the `EndpointReference` element or type used in messages exchanged with a WCF endpoint must match the version of WS-Addressing implemented by this endpoint.</span></span>  
  
 <span data-ttu-id="60026-194">Por exemplo, se um ponto de extremidade do WCF implementa WS-ReliableMessaging, o `AcksTo` retornado por tal um ponto de extremidade dentro do cabeçalho `CreateSequenceResponse` usa a versão de WS-Addressing que o `EncodingBinding` elemento especifica para esse ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="60026-194">For example, if a WCF endpoint implements WS-ReliableMessaging, the `AcksTo` header returned by such an endpoint inside `CreateSequenceResponse` uses the WS-Addressing version that the `EncodingBinding` element specifies for this endpoint.</span></span>  
  
#### <a name="endpoint-references-and-metadata"></a><span data-ttu-id="60026-195">Metadados e referências de ponto de extremidade</span><span class="sxs-lookup"><span data-stu-id="60026-195">Endpoint References and Metadata</span></span>  
 <span data-ttu-id="60026-196">Um número de cenários exige comunicação de metadados ou uma referência aos metadados para um determinado ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="60026-196">A number of scenarios require communicating metadata or a reference to metadata for a given endpoint.</span></span>  
  
 <span data-ttu-id="60026-197">B3121: WCF emprega mecanismos descritos na seção 6 para incluir metadados para referências de ponto de extremidade por valor ou referência de especificação de WS-MetadataExchange (MEX).</span><span class="sxs-lookup"><span data-stu-id="60026-197">B3121: WCF employs mechanisms described in the WS-MetadataExchange (MEX) specification Section 6 to include metadata for endpoint references by value or by reference.</span></span>  
  
 <span data-ttu-id="60026-198">Considere um cenário em que um serviço WCF requer autenticação usando um token de declarações marcação linguagem SAML (Security) emitido pelo emissor de token em http://sts.fabrikam123.com.</span><span class="sxs-lookup"><span data-stu-id="60026-198">Consider a scenario where a WCF service requires authentication using a Security Assertions Markup Language (SAML) token issued by the token issuer at http://sts.fabrikam123.com.</span></span> <span data-ttu-id="60026-199">O ponto de extremidade do WCF descreve esse requisito de autenticação por meio `sp:IssuedToken` asserção com aninhado `sp:Issuer` asserção que aponta para o emissor do token.</span><span class="sxs-lookup"><span data-stu-id="60026-199">The WCF endpoint describes this authentication requirement by using `sp:IssuedToken` assertion with a nested `sp:Issuer` assertion pointing to the token issuer.</span></span> <span data-ttu-id="60026-200">Aplicativos cliente que acessam o `sp:Issuer` asserção precisa saber como se comunicar com o ponto de extremidade do emissor do token.</span><span class="sxs-lookup"><span data-stu-id="60026-200">Client applications that access the `sp:Issuer` assertion need to know how to communicate with the token issuer endpoint.</span></span> <span data-ttu-id="60026-201">O cliente precisa saber os metadados sobre o emissor do token.</span><span class="sxs-lookup"><span data-stu-id="60026-201">The client needs to know metadata about the token issuer.</span></span> <span data-ttu-id="60026-202">Usando as extensões de metadados de referência de ponto de extremidade definidas no MEX, o WCF fornece uma referência aos metadados do emissor do token.</span><span class="sxs-lookup"><span data-stu-id="60026-202">Using the endpoint reference metadata extensions defined in MEX, WCF provides a reference to the token issuer metadata.</span></span>  
  
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
  
### <a name="message-addressing-headers"></a><span data-ttu-id="60026-203">Cabeçalhos de endereçamento de mensagens</span><span class="sxs-lookup"><span data-stu-id="60026-203">Message Addressing Headers</span></span>  
  
#### <a name="message-headers"></a><span data-ttu-id="60026-204">Cabeçalhos de mensagem</span><span class="sxs-lookup"><span data-stu-id="60026-204">Message Headers</span></span>  
 <span data-ttu-id="60026-205">Para ambas as versões do WS-Addressing, o WCF usa os seguintes cabeçalhos de mensagem conforme prescrito pelas especificações `wsa:To`, `wsa:ReplyTo`, `wsa:Action`, `wsa:MessageID`, e `wsa:RelatesTo`.</span><span class="sxs-lookup"><span data-stu-id="60026-205">For both WS-Addressing versions, WCF uses the following message headers as prescribed by the specifications `wsa:To`, `wsa:ReplyTo`, `wsa:Action`, `wsa:MessageID`,and `wsa:RelatesTo`.</span></span>  
  
 <span data-ttu-id="60026-206">B3211: Para todas as versões de WS-Addressing, WCF respeita, mas não produz imediato, cabeçalhos de mensagem do WS-Addressing `wsa:FaultTo` e `wsa:From`.</span><span class="sxs-lookup"><span data-stu-id="60026-206">B3211: For all WS-Addressing versions, WCF honors, but does not produce out of the box, WS-Addressing message headers `wsa:FaultTo` and `wsa:From`.</span></span>  
  
 <span data-ttu-id="60026-207">Aplicativos que interagem com aplicativos do WCF podem adicionar que esses cabeçalhos de mensagem e o WCF irá processá-las adequadamente.</span><span class="sxs-lookup"><span data-stu-id="60026-207">Applications that interact with WCF applications can add these message headers and WCF will process them accordingly.</span></span>  
  
#### <a name="reference-parameters-and-properties"></a><span data-ttu-id="60026-208">Propriedades e parâmetros de referência</span><span class="sxs-lookup"><span data-stu-id="60026-208">Reference Parameters and Properties</span></span>  
 <span data-ttu-id="60026-209">O WCF implementa o processamento de parâmetros de referência do ponto de extremidade e referência p</span><span class="sxs-lookup"><span data-stu-id="60026-209">WCF implements processing of endpoint reference parameters and reference p</span></span>  
  
 <span data-ttu-id="60026-210">Propriedades de acordo com as respectivas especificações.</span><span class="sxs-lookup"><span data-stu-id="60026-210">roperties in accordance with respective specifications.</span></span>  
  
 <span data-ttu-id="60026-211">B3221: Quando configurado para usar 08/2004 de WS-Addressing, pontos de extremidade do WCF não fazem distinção entre o processamento de propriedades de referência e parâmetros de referência.</span><span class="sxs-lookup"><span data-stu-id="60026-211">B3221: When configured to use WS-Addressing 2004/08, WCF endpoints do not differentiate between processing Reference Properties and Reference Parameters.</span></span>  
  
### <a name="message-exchange-patterns"></a><span data-ttu-id="60026-212">Padrões de troca de mensagem</span><span class="sxs-lookup"><span data-stu-id="60026-212">Message Exchange Patterns</span></span>  
 <span data-ttu-id="60026-213">A sequência das mensagens envolvidas na invocação de operação do serviço Web é conhecida como o *padrão de troca de mensagem*.</span><span class="sxs-lookup"><span data-stu-id="60026-213">The sequence of messages involved in the Web service operation invocation is referred to as the *message exchange pattern*.</span></span> <span data-ttu-id="60026-214">Padrões de troca de mensagem duplex, solicitação-resposta e dá suporte a WCF unidirecional.</span><span class="sxs-lookup"><span data-stu-id="60026-214">WCF supports one-way, request-reply, and duplex message exchange patterns.</span></span> <span data-ttu-id="60026-215">Esta seção explica os requisitos, dependendo do padrão de troca de mensagem que está sendo usado de processamento de mensagens WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="60026-215">This section clarifies WS-Addressing requirements on message processing depending on the message exchange pattern being used.</span></span>  
  
 <span data-ttu-id="60026-216">Ao longo desta seção, o solicitante envia a primeira mensagem e o Respondente recebe a primeira mensagem.</span><span class="sxs-lookup"><span data-stu-id="60026-216">Throughout this section, the requester sends the first message and the responder receives the first message.</span></span>  
  
#### <a name="one-way-message"></a><span data-ttu-id="60026-217">Mensagem unidirecional</span><span class="sxs-lookup"><span data-stu-id="60026-217">One-Way Message</span></span>  
 <span data-ttu-id="60026-218">Quando um ponto de extremidade do WCF está configurado para dar suporte a mensagens com um determinado `Action` para seguir o padrão unidirecional, o ponto de extremidade do WCF segue os requisitos e os comportamentos a seguir.</span><span class="sxs-lookup"><span data-stu-id="60026-218">When a WCF endpoint is configured to support messages with a given `Action` to follow a one-way pattern, the WCF endpoint follows the following behaviors and requirements.</span></span> <span data-ttu-id="60026-219">A menos que especificado de outra forma, regras e comportamentos se aplicam a ambas as versões do WS-Addressing tem suportada no WCF:</span><span class="sxs-lookup"><span data-stu-id="60026-219">Unless otherwise specified, behaviors and rules apply for both versions of WS-Addressing supported in WCF:</span></span>  
  
-   <span data-ttu-id="60026-220">R3311: O solicitante deve incluir `wsa:To`, `wsa:Action`e os cabeçalhos para todos os parâmetros de referência especificados pela referência de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="60026-220">R3311: The requester must include `wsa:To`, `wsa:Action`, and headers for all reference parameters specified by the endpoint reference.</span></span> <span data-ttu-id="60026-221">Quando 08/2004 de WS-Addressing é usado e [Propriedades de referência] são especificados pela referência de ponto de extremidade, os cabeçalhos correspondentes devem ser adicionados à mensagem muito.</span><span class="sxs-lookup"><span data-stu-id="60026-221">When WS-Addressing 2004/08 is used and [reference properties] are specified by the endpoint reference, the corresponding headers must be added to the message too.</span></span>  
  
-   <span data-ttu-id="60026-222">B3312: O solicitante pode incluir `MessageID`, `ReplyTo`, e `FaultTo` cabeçalhos.</span><span class="sxs-lookup"><span data-stu-id="60026-222">B3312: The requester may include `MessageID`, `ReplyTo`, and `FaultTo` headers.</span></span> <span data-ttu-id="60026-223">A infraestrutura de receptor irá ignorá-los e eles serão passados para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="60026-223">The receiver infrastructure will ignore them, and they will be passed to the application.</span></span>  
  
-   <span data-ttu-id="60026-224">R3313: Quando HTTP é usado e nenhuma mensagem está sendo enviada sobre o segmento de resposta HTTP, o Respondente deve enviar uma resposta HTTP com um corpo vazio e um código de status HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="60026-224">R3313: When HTTP is used and no message is being sent on the HTTP response leg, the responder must send an HTTP response with an empty body and an HTTP 202 status code.</span></span>  
  
     <span data-ttu-id="60026-225">Quando o transporte HTTP está em uso e o contrato de operação declara uma mensagem unidirecional, a resposta HTTP ainda pode ser usada para enviar mensagens de infraestrutura — por exemplo, o sistema de mensagens confiável pode enviar um `SequenceAcknowledgement` mensagem em uma resposta HTTP.</span><span class="sxs-lookup"><span data-stu-id="60026-225">When the HTTP transport is in use and the operation contract declares a message one-way, the HTTP response can still be used for sending infrastructure messages—for example, reliable messaging can send a `SequenceAcknowledgement` message on an HTTP response.</span></span>  
  
-   <span data-ttu-id="60026-226">B3314: O Respondente do WCF não envia uma mensagem de falha em resposta a uma mensagem unidirecional.</span><span class="sxs-lookup"><span data-stu-id="60026-226">B3314: The WCF responder does not send a fault message in response to a one-way message.</span></span>  
  
#### <a name="request-reply"></a><span data-ttu-id="60026-227">Solicitação-resposta</span><span class="sxs-lookup"><span data-stu-id="60026-227">Request-Reply</span></span>  
 <span data-ttu-id="60026-228">Quando um ponto de extremidade do WCF é configurado para uma mensagem com um determinado `Action` para seguir o padrão de solicitação-resposta, o ponto de extremidade do WCF segue os comportamentos e os requisitos abaixo.</span><span class="sxs-lookup"><span data-stu-id="60026-228">When a WCF endpoint is configured for a message with a given `Action` to follow the request-reply pattern, the WCF endpoint follows the behaviors and requirements below.</span></span> <span data-ttu-id="60026-229">A menos que especificado o contrário, comportamentos e as regras se aplicam a ambas as versões do WS-Addressing tem suportada no WCF:</span><span class="sxs-lookup"><span data-stu-id="60026-229">Unless specified otherwise, behaviors and rules apply for both versions of WS-Addressing supported in WCF:</span></span>  
  
-   <span data-ttu-id="60026-230">R3321: O solicitante deve incluir na solicitação `wsa:To`, `wsa:Action`, `wsa:MessageID`e os cabeçalhos para todos os parâmetros de referência ou referência propriedades (ou ambos) especificado pela referência de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="60026-230">R3321: The requester must include in the request `wsa:To`, `wsa:Action`, `wsa:MessageID`, and headers for all reference parameters or reference properties (or both) specified by the endpoint reference.</span></span>  
  
-   <span data-ttu-id="60026-231">R3322: Quando 08/2004 de WS-Addressing é usado, `ReplyTo` também deve ser incluído na solicitação.</span><span class="sxs-lookup"><span data-stu-id="60026-231">R3322: When WS-Addressing 2004/08 is used, `ReplyTo` must also be included in the request.</span></span>  
  
-   <span data-ttu-id="60026-232">R3323: Quando o WS-Addressing 1.0 é usado e `ReplyTo` não está presente na solicitação, uma referência de ponto de extremidade padrão com a propriedade [endereço] igual a "http://www.w3.org/2005/08/addressing/anonymous" é usado.</span><span class="sxs-lookup"><span data-stu-id="60026-232">R3323: When WS-Addressing 1.0 is used and `ReplyTo` is not present in the request, a default endpoint reference with the [address] property equal to "http://www.w3.org/2005/08/addressing/anonymous" is used.</span></span>  
  
-   <span data-ttu-id="60026-233">R3324: O solicitante deve incluir `wsa:To`, `wsa:Action`, e `wsa:RelatesTo` cabeçalhos na mensagem de resposta, bem como os cabeçalhos para todos os parâmetros de referência ou referência propriedades (ou ambos) especificado pelo `ReplyTo` referência de ponto de extremidade no solicitação.</span><span class="sxs-lookup"><span data-stu-id="60026-233">R3324: The requester must include `wsa:To`, `wsa:Action`, and `wsa:RelatesTo` headers in the reply message, as well as headers for all reference parameters or reference properties (or both) specified by the `ReplyTo` endpoint reference in the request.</span></span>  
  
### <a name="web-services-addressing-faults"></a><span data-ttu-id="60026-234">Falhas de endereçamento de serviços da Web</span><span class="sxs-lookup"><span data-stu-id="60026-234">Web Services Addressing Faults</span></span>  
 <span data-ttu-id="60026-235">R3411: O WCF gera as seguintes falhas definidas pelo 08/2004 de WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="60026-235">R3411: WCF produces the following faults defined by WS-Addressing 2004/08.</span></span>  
  
|<span data-ttu-id="60026-236">Código</span><span class="sxs-lookup"><span data-stu-id="60026-236">Code</span></span>|<span data-ttu-id="60026-237">Causa</span><span class="sxs-lookup"><span data-stu-id="60026-237">Cause</span></span>|  
|----------|-----------|  
|<span data-ttu-id="60026-238">wsa:DestinationUnreachable</span><span class="sxs-lookup"><span data-stu-id="60026-238">wsa:DestinationUnreachable</span></span>|<span data-ttu-id="60026-239">A mensagem chegou com um `ReplyTo` que é diferente do endereço de resposta estabelecido para este canal; não há nenhum ponto de extremidade escutando no endereço especificado no cabeçalho To.</span><span class="sxs-lookup"><span data-stu-id="60026-239">The message arrived with a `ReplyTo` that is different from the reply address established for this channel; there is no endpoint listening at the address specified in the To header.</span></span>|  
|<span data-ttu-id="60026-240">wsa:ActionNotSupported</span><span class="sxs-lookup"><span data-stu-id="60026-240">wsa:ActionNotSupported</span></span>|<span data-ttu-id="60026-241">canais de infraestrutura ou dispatcher associado com o ponto de extremidade não reconhecem a ação especificada no `Action` cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="60026-241">the infrastructure channels or dispatcher associated with the endpoint do not recognize the action specified in the `Action` header.</span></span>|  
  
 <span data-ttu-id="60026-242">R3412: O WCF gera as seguintes falhas definidas pelo WS-Addressing 1.0.</span><span class="sxs-lookup"><span data-stu-id="60026-242">R3412: WCF produces the following faults defined by WS-Addressing 1.0.</span></span>  
  
|<span data-ttu-id="60026-243">Código</span><span class="sxs-lookup"><span data-stu-id="60026-243">Code</span></span>|<span data-ttu-id="60026-244">Causa</span><span class="sxs-lookup"><span data-stu-id="60026-244">Cause</span></span>|  
|----------|-----------|  
|<span data-ttu-id="60026-245">wsa10:InvalidAddressingHeader</span><span class="sxs-lookup"><span data-stu-id="60026-245">wsa10:InvalidAddressingHeader</span></span>|<span data-ttu-id="60026-246">Duplicar `wsa:To`, `wsa:ReplyTo`, `wsa:From` ou `wsa:MessageID`.</span><span class="sxs-lookup"><span data-stu-id="60026-246">Duplicate `wsa:To`, `wsa:ReplyTo`, `wsa:From` or `wsa:MessageID`.</span></span> <span data-ttu-id="60026-247">Duplicar `wsa:RelatesTo` com o mesmo `RelationshipType`.</span><span class="sxs-lookup"><span data-stu-id="60026-247">Duplicate `wsa:RelatesTo` with the same `RelationshipType`.</span></span>|  
|<span data-ttu-id="60026-248">wsa10:MessageAddressingHeaderRequired</span><span class="sxs-lookup"><span data-stu-id="60026-248">wsa10:MessageAddressingHeaderRequired</span></span>|<span data-ttu-id="60026-249">O cabeçalho de endereçamento necessário está ausente.</span><span class="sxs-lookup"><span data-stu-id="60026-249">The required Addressing header is missing.</span></span>|  
|<span data-ttu-id="60026-250">wsa10:DestinationUnreachable</span><span class="sxs-lookup"><span data-stu-id="60026-250">wsa10:DestinationUnreachable</span></span>|<span data-ttu-id="60026-251">A mensagem chegou com um `ReplyTo` que é diferente do endereço de resposta estabelecido para este canal.</span><span class="sxs-lookup"><span data-stu-id="60026-251">The message arrived with a `ReplyTo` that is different from the reply address established for this channel.</span></span> <span data-ttu-id="60026-252">Não há nenhum ponto de extremidade escutando no endereço especificado no cabeçalho To.</span><span class="sxs-lookup"><span data-stu-id="60026-252">There is no endpoint listening at the address specified in the To header.</span></span>|  
|<span data-ttu-id="60026-253">wsa10:ActionNotSupported</span><span class="sxs-lookup"><span data-stu-id="60026-253">wsa10:ActionNotSupported</span></span>|<span data-ttu-id="60026-254">Uma ação especificada no `Action` cabeçalho não é reconhecido pelo dispatcher associado com o ponto de extremidade ou canais de infraestrutura.</span><span class="sxs-lookup"><span data-stu-id="60026-254">An action specified in the `Action` header is not recognized by the infrastructure channels or dispatcher associated with the endpoint.</span></span>|  
|<span data-ttu-id="60026-255">wsa10:EndpointUnavailable</span><span class="sxs-lookup"><span data-stu-id="60026-255">wsa10:EndpointUnavailable</span></span>|<span data-ttu-id="60026-256">O canal do RM envia essa falha, que indica o ponto de extremidade não processará a sequência com base no exame do `CreateSequence` cabeçalhos de endereçamento da mensagem.</span><span class="sxs-lookup"><span data-stu-id="60026-256">The RM channel sends this fault back, indicating the endpoint will not process the sequence based upon examination of the `CreateSequence` message’s addressing headers.</span></span>|  
  
 <span data-ttu-id="60026-257">Mapas de código nas tabelas anteriores ao `FaultCode` em SOAP 1.1 e `SubCode` (com o código = remetente) em SOAP 1.2.</span><span class="sxs-lookup"><span data-stu-id="60026-257">Code in the preceding tables maps to `FaultCode` in SOAP 1.1 and `SubCode` (with Code=Sender) in SOAP 1.2.</span></span>  
  
### <a name="wsdl-11-binding-and-ws-policy-assertions"></a><span data-ttu-id="60026-258">WSDL 1.1 associação e asserções WS-Policy</span><span class="sxs-lookup"><span data-stu-id="60026-258">WSDL 1.1 Binding and WS-Policy Assertions</span></span>  
  
#### <a name="indicating-use-of-ws-addressing"></a><span data-ttu-id="60026-259">Que indica o uso do WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="60026-259">Indicating Use of WS-Addressing</span></span>  
 <span data-ttu-id="60026-260">O WCF usa as declarações de política para indicar o suporte de ponto de extremidade para uma versão específica do WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="60026-260">WCF uses policy assertions to indicate endpoint support for a particular WS-Addressing version.</span></span>  
  
 <span data-ttu-id="60026-261">A seguinte declaração de política tem o assunto da diretriz de ponto de extremidade [WS-PA] e indica as mensagens enviadas e recebidas do ponto de extremidade devem usar 08/2004 de WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="60026-261">The following policy assertion has Endpoint Policy Subject [WS-PA] and indicates messages sent and received from the endpoint must use WS-Addressing 2004/08.</span></span>  
  
```xml  
<wsap:UsingAddressing />  
```  
  
 <span data-ttu-id="60026-262">Esta declaração de política aumenta a especificação de 2004 de WS-Addressing/08.</span><span class="sxs-lookup"><span data-stu-id="60026-262">This policy assertion augments the WS-Addressing 2004/08 specification.</span></span>  
  
 <span data-ttu-id="60026-263">A seguinte declaração de política, que isso indica que as mensagens enviadas/recebidas deve usar WS-Addressing 1.0.</span><span class="sxs-lookup"><span data-stu-id="60026-263">The following policy assertion this indicates that messages sent/received must use WS-Addressing 1.0.</span></span>  
  
```xml
<wsam:Addressing/>   
```  
  
 <span data-ttu-id="60026-264">A seguinte declaração de política tem um assunto de política de ponto de extremidade [WS-PA] e indica se as mensagens enviadas e recebidas do ponto de extremidade devem usar 08/2004 de WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="60026-264">The following policy assertion has an Endpoint Policy Subject [WS-PA] and indicates that messages sent and received from the endpoint must use WS-Addressing 2004/08.</span></span>  
  
```xml  
<wsaw10:UsingAddressing />  
```  
  
 <span data-ttu-id="60026-265">O `wsaw10:UsingAddressing` elemento é obtido do [WS-Addressing-WSDL] e é usado no contexto do WS-Policy em conformidade com essa especificação, seção 3.1.2.</span><span class="sxs-lookup"><span data-stu-id="60026-265">The `wsaw10:UsingAddressing` element is borrowed from [WS-Addressing-WSDL] and is used in the context of WS-Policy in compliance with that specification, section 3.1.2.</span></span>  
  
 <span data-ttu-id="60026-266">Uso de endereçamento não altera a semântica de WSDL 1.1, SOAP 1.1 e associações de HTTP SOAP 1.2.</span><span class="sxs-lookup"><span data-stu-id="60026-266">Use of Addressing does not alter the semantics of WSDL 1.1, SOAP 1.1, and SOAP 1.2 HTTP Bindings.</span></span> <span data-ttu-id="60026-267">Por exemplo, se uma resposta é esperada para uma solicitação enviada para um ponto de extremidade que usa a associação de HTTP 1.x Addressing e SOAP WSDL, a resposta deve ser enviada usando a resposta HTTP.</span><span class="sxs-lookup"><span data-stu-id="60026-267">For example, if a reply is expected to a request that is sent to an endpoint that uses Addressing and WSDL SOAP 1.x HTTP binding, the reply must be sent by using the HTTP response.</span></span>  
  
 <span data-ttu-id="60026-268">Para respostas enviadas pela resposta http, a declaração de WS-AM é:</span><span class="sxs-lookup"><span data-stu-id="60026-268">For replies sent over the http response, the WS-AM assertion is:</span></span>  
  
```xml  
<wsam:AnonymousResponses/>  
```  
  
 <span data-ttu-id="60026-269">A declaração de política completo pode ter esta aparência:</span><span class="sxs-lookup"><span data-stu-id="60026-269">The complete policy assertion might look like this:</span></span>  
  
```xml  
<wsam:Addressing>  
    <wsp:Policy>  
        <wsam:AnonymousResponses />   
    </wsp:Policy>  
</wsam:Addressing>  
```  
  
 <span data-ttu-id="60026-270">No entanto, há padrões de troca de mensagem se beneficiar de duas conexões de HTTP inverso independentes estabelecidas entre o solicitante e o Respondente, por exemplo, não solicitadas unidirecionais mensagens enviadas pelo respondente.</span><span class="sxs-lookup"><span data-stu-id="60026-270">However, there are message exchange patterns that benefit from having two independent converse HTTP connections established between the requester and the responder, for example, unsolicited one-way messages sent by the responder.</span></span>  
  
 <span data-ttu-id="60026-271">O WCF oferece um recurso pelo qual dois canais de transporte subjacente podem formar um canal dúplex de composição, onde um canal é usado para mensagens de entrada e a outra é usada para mensagens de saída.</span><span class="sxs-lookup"><span data-stu-id="60026-271">WCF offers a feature by which two underlying transport channels can form a Composite Duplex channel, where one channel is used for input messages and the other is used for output messages.</span></span> <span data-ttu-id="60026-272">No caso do transporte de HTTP dúplex de composição fornece duas conexões de HTTP do inverso.</span><span class="sxs-lookup"><span data-stu-id="60026-272">In the case of the HTTP Transport, Composite Duplex provides two converse HTTP connections.</span></span> <span data-ttu-id="60026-273">O solicitante usa uma conexão para enviar mensagens para o respondente e o Respondente usa o outro para enviar mensagens de volta ao solicitante.</span><span class="sxs-lookup"><span data-stu-id="60026-273">The requester uses one connection to send messages to the responder, and the responder uses the other to send messages back to the requester.</span></span>  
  
 <span data-ttu-id="60026-274">Para respostas enviadas por solicitações http separado, a declaração de ws-am é</span><span class="sxs-lookup"><span data-stu-id="60026-274">For replies sent over separate http requests, the ws-am assertion is</span></span>  
  
```xml  
<wsam:NonAnonymousResponses/>  
```  
  
 <span data-ttu-id="60026-275">A declaração de política completo pode ter esta aparência:</span><span class="sxs-lookup"><span data-stu-id="60026-275">The complete policy assertion might look like this:</span></span>  
  
```xml  
<wsam:Addressing>  
    <wsp:Policy>  
      <wsam:NonAnonymousResponses />   
   </wsp:Policy>  
  </wsam:Addressing>  
```  
  
 <span data-ttu-id="60026-276">Uso a seguinte asserção que tem o assunto de política de ponto de extremidade [WS-PA] em pontos de extremidade que usam associações de HTTP do WSDL 1.1 SOAP 1.x requer duas conexões de HTTP inverso separado a ser usado para mensagens que fluem do solicitante para Respondente e o Respondente ao solicitante, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="60026-276">Use of the following assertion that has Endpoint Policy Subject [WS-PA] on endpoints that use WSDL 1.1 SOAP 1.x HTTP bindings requires two separate converse HTTP connections to be used for messages flowing from requester to responder and responder to requester, respectively.</span></span>  
  
```xml  
<cdp:CompositeDuplex/>  
```  
  
 <span data-ttu-id="60026-277">A instrução anterior leva aos requisitos a seguir o `wsa:ReplyTo` cabeçalho para mensagens de solicitação:</span><span class="sxs-lookup"><span data-stu-id="60026-277">The previous statement leads to the following requirements on the `wsa:ReplyTo` header for request messages:</span></span>  
  
-   <span data-ttu-id="60026-278">R3514: Solicitar que as mensagens enviadas para um ponto de extremidade devem ter uma `ReplyTo` cabeçalho com o `[address]` propriedade não é igual a "http://www.w3.org/2005/08/addressing/anonymous" se o ponto de extremidade usa uma associação de HTTP do 1.x WSDL 1.1 SOAP e tem uma alternativa de política com um `wsap10:UsingAddressing` ou `wsap:UsingAddressing` asserção juntamente com `cdp:CompositeDuplex` anexado.</span><span class="sxs-lookup"><span data-stu-id="60026-278">R3514: Request messages sent to an endpoint must have a `ReplyTo` header with the `[address]` property not equal to "http://www.w3.org/2005/08/addressing/anonymous" if the endpoint uses a WSDL 1.1 SOAP 1.x HTTP binding and has a policy alternative with a `wsap10:UsingAddressing` or `wsap:UsingAddressing` assertion coupled with `cdp:CompositeDuplex` attached.</span></span>  
  
-   <span data-ttu-id="60026-279">R3515: Solicitar que as mensagens enviadas para um ponto de extremidade devem ter uma `ReplyTo` cabeçalho com o `[address]` propriedade igual a "http://www.w3.org/2005/08/addressing/anonymous", ou não tem um `ReplyTo` cabeçalho no lugar, se o ponto de extremidade usa uma associação de HTTP do 1.x WSDL 1.1 SOAP e tem uma alternativa de política com o `wsap10:UsingAddressing` asserção e nenhum `cdp:CompositeDuplex` asserção anexada.</span><span class="sxs-lookup"><span data-stu-id="60026-279">R3515: Request messages sent to an endpoint must have a `ReplyTo` header with the `[address]` property equal to "http://www.w3.org/2005/08/addressing/anonymous", or not have a `ReplyTo` header at all, if the endpoint uses a WSDL 1.1 SOAP 1.x HTTP binding and has a policy alternative with `wsap10:UsingAddressing` assertion and no `cdp:CompositeDuplex` assertion attached.</span></span>  
  
-   <span data-ttu-id="60026-280">R3516: Solicitar que as mensagens enviadas para um ponto de extremidade devem ter uma `ReplyTo` cabeçalho com um `[address]` propriedade igual a "http://www.w3.org/2005/08/addressing/anonymous" se o ponto de extremidade usa uma associação de HTTP do 1.x WSDL 1.1 SOAP e tem uma alternativa de política com `wsap:UsingAddressing` asserção e nenhum `cdp:CompositeDuplex`asserção anexada.</span><span class="sxs-lookup"><span data-stu-id="60026-280">R3516: Request messages sent to an endpoint must have a `ReplyTo` header with an `[address]` property equal to "http://www.w3.org/2005/08/addressing/anonymous" if the endpoint uses a WSDL 1.1 SOAP 1.x HTTP binding and has a policy alternative with `wsap:UsingAddressing` assertion and no `cdp:CompositeDuplex` assertion attached.</span></span>  
  
 <span data-ttu-id="60026-281">A especificação de WS-addressing WSDL tenta descrever as associações do protocolo semelhante com a introdução de um elemento `<wsaw:Anonymous/>` com três valores textuais (obrigatórios, opcionais e proibidos) para indicar requisitos sobre o `wsa:ReplyTo` cabeçalho (seção 3.2).</span><span class="sxs-lookup"><span data-stu-id="60026-281">The WS-addressing WSDL specification attempts to describe similar protocol bindings by introducing an element `<wsaw:Anonymous/>` with three textual values (required, optional, and prohibited) to indicate requirements on the `wsa:ReplyTo` header (section 3.2).</span></span> <span data-ttu-id="60026-282">Infelizmente, essa definição de elemento não é particularmente útil como uma asserção no contexto do WS-Policy, porque ele requer extensões específicas de domínio para dar suporte a interseção de alternativas usando esse elemento como uma asserção.</span><span class="sxs-lookup"><span data-stu-id="60026-282">Unfortunately, such element definition is not particularly usable as an assertion in the context of WS-Policy, because it requires domain-specific extensions to support the intersection of alternatives using such an element as an assertion.</span></span> <span data-ttu-id="60026-283">Essa definição de elemento também indica o valor da `ReplyTo` cabeçalho em vez do comportamento de ponto de extremidade durante a transmissão, o que torna específico ao transporte HTTP.</span><span class="sxs-lookup"><span data-stu-id="60026-283">Such element definition also indicates the value of the `ReplyTo` header as opposed to the endpoint behavior on the wire, which makes it specific to HTTP transport.</span></span>  
  
#### <a name="action-definition"></a><span data-ttu-id="60026-284">Definição de ação</span><span class="sxs-lookup"><span data-stu-id="60026-284">Action Definition</span></span>  
 <span data-ttu-id="60026-285">08/2004 de WS-Addressing define uma `wsa:Action` de atributo para o `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]` elementos.</span><span class="sxs-lookup"><span data-stu-id="60026-285">WS-Addressing 2004/08 defines a `wsa:Action` attribute for the `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]` elements.</span></span> <span data-ttu-id="60026-286">WS-Addressing 1.0 WSDL associação (WS-ADDR10 WSDL) define um atributo semelhante, `wsaw10:Action`.</span><span class="sxs-lookup"><span data-stu-id="60026-286">WS-Addressing 1.0 WSDL Binding (WS-ADDR10-WSDL) defines a similar attribute, `wsaw10:Action`.</span></span>  
  
 <span data-ttu-id="60026-287">A única diferença entre os dois é a semântica de padrão de ação padrão descrita na seção 3.3.2 do WS-ADDR e 4.4.4 do WS-ADDR10-WSDL, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="60026-287">The only difference between the two is the default Action pattern semantics described in section 3.3.2 of WS-ADDR and section 4.4.4 of WS-ADDR10-WSDL, respectively.</span></span>  
  
 <span data-ttu-id="60026-288">É razoável ter dois pontos de extremidade que compartilham o mesmo `portType` (ou um contrato, na terminologia do WCF), mas usando diferentes versões do WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="60026-288">It is a reasonable to have two endpoints that share the same `portType` (or contract, in WCF terminology) but using different versions of WS-Addressing.</span></span> <span data-ttu-id="60026-289">Mas considerando que a ação é definida pela `portType` e não devem alterar entre os pontos de extremidade que implementam o `portType`, ele se torna impossível dar suporte a ambos os padrões de ação padrão.</span><span class="sxs-lookup"><span data-stu-id="60026-289">But given that Action is defined by the `portType` and should not change across the endpoints that implement the `portType`, it becomes impossible to support both default action patterns.</span></span>  
  
 <span data-ttu-id="60026-290">Para resolver esta controvérsia incrível, o WCF oferece suporte a uma única versão do `Action` atributo.</span><span class="sxs-lookup"><span data-stu-id="60026-290">To resolve this controversy, WCF supports a single version of the `Action` attribute.</span></span>  
  
 <span data-ttu-id="60026-291">B3521: WCF usa o `wsaw10:Action` atributo `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]` elementos conforme definido em WS-ADDR10 WSDL para determinar o `Action` URI para as mensagens correspondentes independentemente da versão do WS-Addressing usadas pelo ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="60026-291">B3521: WCF uses the `wsaw10:Action` attribute on `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]` elements as defined in WS-ADDR10-WSDL to determine the `Action` URI for the corresponding messages irrespective of the WS-Addressing version used by the endpoint.</span></span>  
  
#### <a name="use-endpoint-reference-inside-wsdl-port"></a><span data-ttu-id="60026-292">Porta de WSDL de dentro do uso ponto de extremidade de referência</span><span class="sxs-lookup"><span data-stu-id="60026-292">Use Endpoint Reference Inside WSDL Port</span></span>  
 <span data-ttu-id="60026-293">WS-ADDR10-WSDL seção 4.1 estende o `wsdl:port` elemento para incluir o `<wsa10:EndpointReference…/>` elemento filho para descrever o ponto de extremidade em termos de WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="60026-293">WS-ADDR10-WSDL section 4.1 extends the `wsdl:port` element to include the `<wsa10:EndpointReference…/>` child element to describe the endpoint in WS-Addressing terms.</span></span> <span data-ttu-id="60026-294">WCF expande esse utilitário em 2004 de WS-Addressing/08, permitindo `<wsa:EndpointReference…/>` apareça como um elemento filho de `wsdl:port`.</span><span class="sxs-lookup"><span data-stu-id="60026-294">WCF expands this utility on WS-Addressing 2004/08, allowing `<wsa:EndpointReference…/>` to appear as a child element of `wsdl:port`.</span></span>  
  
-   <span data-ttu-id="60026-295">R3531: Se um ponto de extremidade tem uma alternativa de política anexada com um `<wsaw10:UsingAddressing/>` declaração de política correspondente `wsdl:port` elemento pode conter um elemento filho `<wsa10:EndpointReference …/>`.</span><span class="sxs-lookup"><span data-stu-id="60026-295">R3531: If an endpoint has an attached policy alternative with a `<wsaw10:UsingAddressing/>` policy assertion, the corresponding `wsdl:port` element can contain a child element `<wsa10:EndpointReference …/>`.</span></span>  
  
-   <span data-ttu-id="60026-296">R3532: Se um `wsdl:port` contém um elemento filho `<wsa10:EndpointReference …/>`, o `wsa10:EndpointReference/wsa10:Address` valor do elemento filho deve corresponder ao valor da `@address` atributo do irmão `wsdl:port` / `wsdl:location` elemento.</span><span class="sxs-lookup"><span data-stu-id="60026-296">R3532: If a `wsdl:port` contains a child element `<wsa10:EndpointReference …/>`, the `wsa10:EndpointReference/wsa10:Address` child element value must match the value of the `@address` attribute of the sibling `wsdl:port`/`wsdl:location` element.</span></span>  
  
-   <span data-ttu-id="60026-297">R3533: Se um ponto de extremidade tem uma alternativa de política anexada com `<wsap:UsingAddressing/>` declaração de política correspondente `wsdl:port` elemento pode conter um elemento filho `<wsa:EndpointReference …/>`.</span><span class="sxs-lookup"><span data-stu-id="60026-297">R3533: If an endpoint has an attached policy alternative with `<wsap:UsingAddressing/>` policy assertion, the corresponding `wsdl:port` element can contain a child element `<wsa:EndpointReference …/>`.</span></span>  
  
-   <span data-ttu-id="60026-298">R3534: Se um `wsdl:port` contém um elemento filho `<wsa:EndpointReference …/>`, o `wsa:EndpointReference/wsa:Address` valor do elemento filho deve corresponder ao valor da `@address` atributo do irmão `wsdl:port` / `wsdl:location` elemento.</span><span class="sxs-lookup"><span data-stu-id="60026-298">R3534: If a `wsdl:port` contains a child element `<wsa:EndpointReference …/>`, the `wsa:EndpointReference/wsa:Address` child element value must match the value of the `@address` attribute of the sibling `wsdl:port`/`wsdl:location` element.</span></span>  
  
### <a name="composition-with-ws-security"></a><span data-ttu-id="60026-299">Composição com o WS-Security</span><span class="sxs-lookup"><span data-stu-id="60026-299">Composition with WS-Security</span></span>  
 <span data-ttu-id="60026-300">De acordo com a seções de consideração de segurança no WS-ADDR e WS-ADDR10, todos os cabeçalhos de mensagem de endereçamento são recomendados sejam assinadas junto com o corpo da mensagem para ligá-los juntos.</span><span class="sxs-lookup"><span data-stu-id="60026-300">According to security consideration sections in WS-ADDR and WS-ADDR10, all addressing message headers are recommended to be signed together with the message body to bind them together.</span></span>  
  
 <span data-ttu-id="60026-301">Quando o WS-Security é usado para proteção de integridade da mensagem, WS-Addressing mensagem resultaram de cabeçalhos, bem como cabeçalhos de parâmetros de referência ou propriedades (ou ambos) deve ser assinada juntamente com o corpo da mensagem.</span><span class="sxs-lookup"><span data-stu-id="60026-301">When WS-Security is used for message integrity protection, WS-Addressing message headers as well as headers resulted from reference parameters or properties (or both) must be signed together with the body of the message.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="60026-302">Exemplos</span><span class="sxs-lookup"><span data-stu-id="60026-302">Examples</span></span>  
  
#### <a name="one-way-message"></a><span data-ttu-id="60026-303">Mensagem unidirecional</span><span class="sxs-lookup"><span data-stu-id="60026-303">One-Way Message</span></span>  
 <span data-ttu-id="60026-304">Nesse cenário, o remetente envia uma mensagem unidirecional para o receptor.</span><span class="sxs-lookup"><span data-stu-id="60026-304">In this scenario, the sender sends a one-way message to the receiver.</span></span> <span data-ttu-id="60026-305">W3C WS-Addressing 1.0, HTTP 1.1 e SOAP 1.2 são usados.</span><span class="sxs-lookup"><span data-stu-id="60026-305">SOAP 1.2, HTTP 1.1, and W3C WS-Addressing 1.0 are used.</span></span>  
  
 <span data-ttu-id="60026-306">A estrutura de mensagens de solicitação: Os cabeçalhos de mensagem incluem `wsa10:To` e `wsa10:Action` elementos.</span><span class="sxs-lookup"><span data-stu-id="60026-306">The Request Message Structure: The message headers include `wsa10:To` and `wsa10:Action` elements.</span></span> <span data-ttu-id="60026-307">O corpo da mensagem inclui um determinado `<app:Ping>` elemento do namespace do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="60026-307">The message body includes a specific `<app:Ping>` element from the application namespace.</span></span>  
  
 <span data-ttu-id="60026-308">Cabeçalhos HTTP: O destino na POSTAGEM corresponda ao URI no `wsa10:To` elemento.</span><span class="sxs-lookup"><span data-stu-id="60026-308">HTTP Headers: The destination in POST matches the URI in the `wsa10:To` element.</span></span>  
  
 <span data-ttu-id="60026-309">O cabeçalho Content-Type tem o valor de `application/soap+xml` conforme solicitado pelo SOAP 1.2.</span><span class="sxs-lookup"><span data-stu-id="60026-309">The Content-Type header has the value of `application/soap+xml` as required by SOAP 1.2.</span></span> <span data-ttu-id="60026-310">Parâmetros `charset` e `action` são incluídos.</span><span class="sxs-lookup"><span data-stu-id="60026-310">Parameters `charset` and `action` are included.</span></span> <span data-ttu-id="60026-311">O `action` parâmetro do cabeçalho Content-Type corresponde ao valor do `wsa10:Action` cabeçalho da mensagem.</span><span class="sxs-lookup"><span data-stu-id="60026-311">The `action` parameter of the Content-Type header matches the value of the `wsa10:Action` message header.</span></span>  
  
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
  
 <span data-ttu-id="60026-312">O receptor responde com uma resposta HTTP vazia e o status de 202.</span><span class="sxs-lookup"><span data-stu-id="60026-312">The receiver responds with an empty HTTP response and status 202.</span></span> <span data-ttu-id="60026-313">Um exemplo de resposta HTTP:</span><span class="sxs-lookup"><span data-stu-id="60026-313">An example of the HTTP response:</span></span>  
  
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
  
## <a name="soap-message-transmission-optimization-mechanism"></a><span data-ttu-id="60026-314">Mecanismo de otimização da transmissão de mensagens SOAP</span><span class="sxs-lookup"><span data-stu-id="60026-314">SOAP Message Transmission Optimization Mechanism</span></span>  
 <span data-ttu-id="60026-315">Esta seção descreve os detalhes de implementação de WCF para o HTTP SOAP MTOM.</span><span class="sxs-lookup"><span data-stu-id="60026-315">This section describes the WCF implementation details for the HTTP SOAP MTOM.</span></span> <span data-ttu-id="60026-316">A tecnologia MTOM é o mecanismo de codificação de mensagem SOAP da mesma classe, como codificação tradicional de texto/XML ou binário do WCF.</span><span class="sxs-lookup"><span data-stu-id="60026-316">MTOM technology is SOAP message encoding mechanism of the same class as traditional text/XML encoding or WCF Binary encoding.</span></span> <span data-ttu-id="60026-317">MTOM inclui o seguinte:</span><span class="sxs-lookup"><span data-stu-id="60026-317">MTOM includes the following:</span></span>  
  
-   <span data-ttu-id="60026-318">Uma codificação XML e o mecanismo de empacotamento descrito pelo [XOP] que otimiza a itens de informações de XML que contém dados binários codificados em base64 em partes separadas de binários.</span><span class="sxs-lookup"><span data-stu-id="60026-318">An XML encoding and packaging mechanism described by [XOP] that optimizes XML information items containing base64-encoded binary data into separate binary parts.</span></span>  
  
-   <span data-ttu-id="60026-319">Um encapsulamento MIME do pacote XOP que serializa o XML Infoset e cada parte binária do pacote XOP em uma parte MIME separada.</span><span class="sxs-lookup"><span data-stu-id="60026-319">A MIME encapsulation of the XOP package that serializes the XML Infoset and each binary part of the XOP package into a separate MIME part.</span></span>  
  
-   <span data-ttu-id="60026-320">Uma codificação de MIME XOP aplicada ao SOAP 1.x Envelope.</span><span class="sxs-lookup"><span data-stu-id="60026-320">A MIME XOP encoding applied to SOAP 1.x Envelope.</span></span>  
  
-   <span data-ttu-id="60026-321">Um HTTP ligação de transporte.</span><span class="sxs-lookup"><span data-stu-id="60026-321">An HTTP transport binding.</span></span>  
  
 <span data-ttu-id="60026-322">É possível usar o MTOM com transportes não-HTTP com WCF.</span><span class="sxs-lookup"><span data-stu-id="60026-322">It is possible to use MTOM with non-HTTP transports with WCF.</span></span> <span data-ttu-id="60026-323">No entanto, neste tópico nos concentraremos em HTTP.</span><span class="sxs-lookup"><span data-stu-id="60026-323">However, in this topic we will focus on HTTP.</span></span>  
  
 <span data-ttu-id="60026-324">O formato MTOM aproveita um grande conjunto de especificações que abrangem o MTOM em si, XOP e MIME.</span><span class="sxs-lookup"><span data-stu-id="60026-324">The MTOM format leverages a large set of specifications covering MTOM itself, XOP, and MIME.</span></span> <span data-ttu-id="60026-325">A modularidade desse conjunto da especificação torna um pouco difícil de reconstruir os requisitos exatos em que a semântica de formato e o processamento.</span><span class="sxs-lookup"><span data-stu-id="60026-325">Modularity of this specification set makes it somewhat difficult to reconstruct exact requirements on the format and processing semantics.</span></span> <span data-ttu-id="60026-326">Esta seção descreve os requisitos de formato e o processamento para a associação HTTP MTOM.</span><span class="sxs-lookup"><span data-stu-id="60026-326">This section describes the format and processing requirements for MTOM HTTP binding.</span></span>  
  
### <a name="mtom-message-encoding"></a><span data-ttu-id="60026-327">Codificação de mensagem MTOM</span><span class="sxs-lookup"><span data-stu-id="60026-327">MTOM Message Encoding</span></span>  
  
#### <a name="generating-mtom-messages"></a><span data-ttu-id="60026-328">Gerando mensagens MTOM</span><span class="sxs-lookup"><span data-stu-id="60026-328">Generating MTOM messages</span></span>  
 <span data-ttu-id="60026-329">A seção 3.1 [XOP] descreve o processo de codificação de XML com itens de informações do elemento que contêm valores de base64 em um pacote XOP definido de forma abstrata.</span><span class="sxs-lookup"><span data-stu-id="60026-329">The [XOP] section 3.1 describes the process of encoding XML with element information items that contain base64 values into an abstractly defined XOP package.</span></span>  
  
 <span data-ttu-id="60026-330">A sequência de etapas a seguir descreve o processo de codificação de MTOM específicas:</span><span class="sxs-lookup"><span data-stu-id="60026-330">The following sequence of steps describes the MTOM-specific encoding process:</span></span>  
  
1.  <span data-ttu-id="60026-331">Certifique-se de que o Envelope SOAP a ser decodificado não contém nenhum item de informação do elemento com um `[namespace name]` de "http://www.w3.org/2004/08/xop/include" e um `[local name]` de `Include`.</span><span class="sxs-lookup"><span data-stu-id="60026-331">Ensure that the SOAP Envelope to be encoded contains no element information item with a `[namespace name]` of "http://www.w3.org/2004/08/xop/include" and a `[local name]` of `Include`.</span></span>  
  
2.  <span data-ttu-id="60026-332">Crie um pacote vazio do MIME.</span><span class="sxs-lookup"><span data-stu-id="60026-332">Create an empty MIME package.</span></span>  
  
3.  <span data-ttu-id="60026-333">Identifique os itens de informações do elemento a ser otimizado dentro o XML Infoset Original.</span><span class="sxs-lookup"><span data-stu-id="60026-333">Identify within the Original XML Infoset the element information items to be optimized.</span></span> <span data-ttu-id="60026-334">Para os itens que serão otimizados, os caracteres que compõem o `[children]` as informações do elemento de item deve ser no formato canônico de `xs:base64Binary` (consulte XSD-2, 3.2.16 base64Binary) e não deve conter quaisquer caracteres de espaço em branco anteriores embutidos com, ou Após o conteúdo diferente de espaço em branco.</span><span class="sxs-lookup"><span data-stu-id="60026-334">For the items to be optimized, the characters that make up the `[children]` of the element information item must be in the canonical form of `xs:base64Binary` (see XSD-2, 3.2.16 base64Binary) and must not contain any white-space characters preceding, inline with, or following the non-white-space content.</span></span>  
  
4.  <span data-ttu-id="60026-335">Criar um Envelope SOAP XOP que é uma cópia do Envelope SOAP Original, mas com os filhos de cada informações sobre o elemento item identificado na etapa anterior é substituída por um `xop:Include` item de informação do elemento construída da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="60026-335">Create an XOP SOAP Envelope that is a copy of the Original SOAP Envelope, but with the children of each element information item identified in the previous step replaced by an `xop:Include` element information item constructed as follows:</span></span>  
  
    1.  <span data-ttu-id="60026-336">Transforme os caracteres substituídos em dados binários processando-os como dados codificados em base64.</span><span class="sxs-lookup"><span data-stu-id="60026-336">Transform the replaced characters into binary data by processing them as base64-encoded data.</span></span>  
  
    2.  <span data-ttu-id="60026-337">Gere um valor de cabeçalho Content-ID exclusivo que satisfaz os requisitos de R3133 e R3134.</span><span class="sxs-lookup"><span data-stu-id="60026-337">Generate a unique Content-ID header value that satisfies requirements R3133 and R3134.</span></span>  
  
    3.  <span data-ttu-id="60026-338">Gere um cabeçalho Content-Transfer-Encoding MIME com o valor binário.</span><span class="sxs-lookup"><span data-stu-id="60026-338">Generate a Content-Transfer-Encoding MIME header with the value binary.</span></span>  
  
    4.  <span data-ttu-id="60026-339">Se o item de informação do elemento que está sendo otimizado ([pai] de recém-inserido `xop:Include` item de informação do elemento) tem um `xmime:contentType` atributo de item de informação, gerar um cabeçalho de tipo de conteúdo MIME com o valor da `xmime:contentType` atributo.</span><span class="sxs-lookup"><span data-stu-id="60026-339">If the element information item being optimized (the [parent] of the newly inserted `xop:Include` element information item) has an `xmime:contentType` attribute information item, generate a Content-Type MIME header with the value of the `xmime:contentType` attribute.</span></span>  
  
    5.  <span data-ttu-id="60026-340">Gere uma nova parte MIME binária com conteúdo formado por dados binários decodificados dos caracteres substituídos processados como base64, o cabeçalho Content-ID do 4b, o cabeçalho Content-Transfer-Encoding de 4 núcleos, o cabeçalho Content-Type se gerado na etapa 4d.</span><span class="sxs-lookup"><span data-stu-id="60026-340">Generate a new binary MIME part with content formed by binary data decoded from the replaced characters processed as base64, Content-ID header from 4b, Content- Transfer-Encoding header from 4c, Content-Type header if generated in step 4d.</span></span>  
  
    6.  <span data-ttu-id="60026-341">Adicionar um `href` de atributo para o `xop:Include` elemento com o valor de cid: uri derivado do valor de cabeçalho de Content-ID gerado na etapa 4b.</span><span class="sxs-lookup"><span data-stu-id="60026-341">Add an `href` attribute to the `xop:Include` element with the value cid: uri derived from Content-ID header value generated in step 4b.</span></span> <span data-ttu-id="60026-342">Remover o delimitador "\<" e ">" caracteres, o restante da cadeia de caracteres e adicione o prefixo de URL-escape `cid:`.</span><span class="sxs-lookup"><span data-stu-id="60026-342">Remove the enclosing "\<" and ">" characters, URL-escape the remaining string, and add the prefix `cid:`.</span></span> <span data-ttu-id="60026-343">O conjunto mínimo de caracteres a seguir é necessário ser substituídas por RFC1738 e RFC2396.</span><span class="sxs-lookup"><span data-stu-id="60026-343">The following minimum character set is required to be escaped by RFC1738 and RFC2396.</span></span> <span data-ttu-id="60026-344">Outros caracteres podem ser substituídos.</span><span class="sxs-lookup"><span data-stu-id="60026-344">Other characters can be escaped.</span></span>  
  
        ```  
        Hexadecimal 00-1F , 7F, 20, "<" | ">" | "#" | "%" | <">  
        "{" | "}" | "|" | "\" | "^" | "[" | "]" | "`" | "~" | "^"  
        ```  
  
5.  <span data-ttu-id="60026-345">Crie uma parte MIME raiz com o Envelope SOAP de XOP da etapa 4.</span><span class="sxs-lookup"><span data-stu-id="60026-345">Create a root MIME part with the XOP SOAP Envelope from step 4.</span></span>  
  
6.  <span data-ttu-id="60026-346">Gravar os cabeçalhos HTTP, incluindo o cabeçalho HTTP Content-Type.</span><span class="sxs-lookup"><span data-stu-id="60026-346">Write the HTTP headers, including the HTTP Content-Type header.</span></span>  
  
7.  <span data-ttu-id="60026-347">O pacote MIME é gravado.</span><span class="sxs-lookup"><span data-stu-id="60026-347">Write the MIME package.</span></span>  
  
#### <a name="processing-mtom-messages"></a><span data-ttu-id="60026-348">Processamento de mensagens MTOM</span><span class="sxs-lookup"><span data-stu-id="60026-348">Processing MTOM messages</span></span>  
 <span data-ttu-id="60026-349">O processamento de um MTOM mensagem é o inverso exato do processo descrito anteriormente na "gerando MTOM mensagens" seção:</span><span class="sxs-lookup"><span data-stu-id="60026-349">Processing of an MTOM message is the exact reverse of the process described in the preceding "Generating MTOM messages" section:</span></span>  
  
1.  <span data-ttu-id="60026-350">Verifique se a parte MIME raiz tem o tipo de conteúdo `application/xop+xml`.</span><span class="sxs-lookup"><span data-stu-id="60026-350">Ensure the root MIME part has the Content-Type `application/xop+xml`.</span></span>  
  
2.  <span data-ttu-id="60026-351">Construa um Envelope SOAP ao analisar a parte MIME do pacote como um documento XML raiz.</span><span class="sxs-lookup"><span data-stu-id="60026-351">Construct a SOAP Envelope by parsing the root MIME part of the package as an XML document.</span></span> <span data-ttu-id="60026-352">Codificação de caracteres é determinada pelo `charset` parâmetro o tipo de conteúdo da parte MIME raiz.</span><span class="sxs-lookup"><span data-stu-id="60026-352">Character encoding is determined by the `charset` parameter of the Content-Type of the root MIME part.</span></span>  
  
3.  <span data-ttu-id="60026-353">Para cada item de informações do elemento no Envelope SOAP construído, que tem, como os únicos membros de sua propriedade [filhos], um `xop:Include` item de informação do elemento:</span><span class="sxs-lookup"><span data-stu-id="60026-353">For each element information item in the constructed SOAP Envelope, which has, as the sole member of its [children] property, an `xop:Include` element information item:</span></span>  
  
    1.  <span data-ttu-id="60026-354">Remover o `cid:` de prefixo e unescape todas as sequências de escape do URI (RFC 2396) no valor da `@href` atributo do `xop:Include` elemento.</span><span class="sxs-lookup"><span data-stu-id="60026-354">Remove the `cid:` prefix and unescape all URI-escape sequences (RFC 2396) in the value of the `@href` attribute of the `xop:Include` element.</span></span> <span data-ttu-id="60026-355">Coloque a cadeia de caracteres de resultado no "\<", ">".</span><span class="sxs-lookup"><span data-stu-id="60026-355">Enclose the result string in "\<", ">".</span></span>  
  
    2.  <span data-ttu-id="60026-356">Localize a parte do MIME com o valor do cabeçalho Content-ID que corresponde à cadeia de caracteres derivada na etapa 3a.</span><span class="sxs-lookup"><span data-stu-id="60026-356">Locate the MIME part with the Content-ID header value that matches the string derived in step 3a.</span></span>  
  
    3.  <span data-ttu-id="60026-357">Substitua os `xop:Include` item de informação do elemento que aparece no `children` propriedade de cada item com os itens de informações de caracteres que representam a codificação base64 canônico (consulte XSD-2, 3.2.16 base64Binary) do corpo da entidade da parte MIME identificado na etapa 3b (substituir com eficiência o `xop:Include` item de informação do elemento com os dados reconstruídos com a parte do pacote).</span><span class="sxs-lookup"><span data-stu-id="60026-357">Replace the `xop:Include` element information item that appears in the `children` property of each item with the character information items that represent the canonical base64 encoding (see XSD-2, 3.2.16 base64Binary) of the entity body of the MIME part identified in step 3b (effectively replace the `xop:Include` element information item with the data reconstructed from the package part).</span></span>  
  
#### <a name="http-content-type-header"></a><span data-ttu-id="60026-358">Cabeçalho HTTP Content-Type</span><span class="sxs-lookup"><span data-stu-id="60026-358">HTTP Content-Type Header</span></span>  
 <span data-ttu-id="60026-359">A seguir está uma lista de esclarecimentos de WCF para o formato do cabeçalho HTTP Content-Type 1.x codificada por MTOM mensagens SOAP derivado de requisitos mencionados na especificação do MTOM propriamente dito e é derivado do MTOM e RFC 2387.</span><span class="sxs-lookup"><span data-stu-id="60026-359">The following is a list of WCF clarifications for the format of the HTTP Content-Type header of a SOAP 1.x MTOM-encoded message derived from requirements stated in the MTOM specification itself and are derived from MTOM and RFC 2387.</span></span>  
  
-   <span data-ttu-id="60026-360">R4131: Um cabeçalho HTTP Content-Type deve ter o valor de diversas partes/relacionado (diferencia maiusculas de minúsculas) e seus parâmetros.</span><span class="sxs-lookup"><span data-stu-id="60026-360">R4131: An HTTP Content-Type header must have the value of multipart/related (case-insensitive) and its parameters.</span></span> <span data-ttu-id="60026-361">Nomes de parâmetros diferenciam maiusculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="60026-361">Parameter names are case-insensitive.</span></span> <span data-ttu-id="60026-362">Ordem do parâmetro não é significativa.</span><span class="sxs-lookup"><span data-stu-id="60026-362">Parameter order is not significant.</span></span>  
  
-   <span data-ttu-id="60026-363">A forma de Backus-Naur completo (BNF) do cabeçalho Content-Type para mensagens MIME é listado na RFC 2045, seção 5.1.</span><span class="sxs-lookup"><span data-stu-id="60026-363">The full Backus-Naur Form (BNF) of the Content-Type header for MIME messages is listed in RFC 2045, section 5.1.</span></span>  
  
-   <span data-ttu-id="60026-364">R4132: Um cabeçalho HTTP Content-Type deve ter um parâmetro de tipo com o valor `application/xop+xml` entre aspas duplas.</span><span class="sxs-lookup"><span data-stu-id="60026-364">R4132: An HTTP Content-Type header must have a type parameter with the value `application/xop+xml` enclosed in double quotation marks.</span></span>  
  
 <span data-ttu-id="60026-365">Embora o requisito para usar as aspas duplas não seja explícito na RFC 2387, o texto observa que todos os parâmetros de tipo de mídia com diversas partes/relacionado provavelmente contêm caracteres reservados como "\@" ou "/" e, portanto, precisam de aspas duplas marca.</span><span class="sxs-lookup"><span data-stu-id="60026-365">While the requirement to use double quotation marks is not explicit in RFC 2387, the text observes that all of the multipart/related media type parameters most likely contain reserved characters like "\@" or "/" and therefore need double quotation marks.</span></span>  
  
-   <span data-ttu-id="60026-366">R4133: Um cabeçalho HTTP Content-Type deve ter um parâmetro de inicialização com o valor do cabeçalho Content-ID da parte MIME que contém o SOAP 1.x Envelope, entre aspas duplas.</span><span class="sxs-lookup"><span data-stu-id="60026-366">R4133: An HTTP Content-Type header should have a start parameter with the value of the Content-ID header of the MIME part that contains the SOAP 1.x Envelope, enclosed in double quotation marks.</span></span> <span data-ttu-id="60026-367">Se o parâmetro start for omitido, a primeira parte MIME deve conter o SOAP 1.x Envelope.</span><span class="sxs-lookup"><span data-stu-id="60026-367">If the start parameter is omitted, the first MIME part must contain the SOAP 1.x Envelope.</span></span>  
  
-   <span data-ttu-id="60026-368">R4134: Um cabeçalho HTTP Content-Type para uma mensagem SOAP 1.1 MTOM codificado deve incluir o parâmetro de informações de início com o valor de texto/xml, entre aspas duplas.</span><span class="sxs-lookup"><span data-stu-id="60026-368">R4134: An HTTP Content-Type header for a SOAP 1.1 MTOM encoded message must include the start-info parameter with the value of text/xml, enclosed in double quotation marks.</span></span>  
  
-   <span data-ttu-id="60026-369">R4135: Um cabeçalho HTTP Content-Type para uma mensagem codificada em SOAP 1.2 MTOM deve incluir o parâmetro de informações de início com o valor de `application/soap+xml`, colocado entre aspas duplas.</span><span class="sxs-lookup"><span data-stu-id="60026-369">R4135: An HTTP Content-Type header for a SOAP 1.2 MTOM-encoded message must include the start-info parameter with the value of `application/soap+xml`, enclosed in double quotation marks.</span></span>  
  
-   <span data-ttu-id="60026-370">R4136: O cabeçalho HTTP Content-Type para uma mensagem codificada por MTOM do SOAP 1. x deve ter o parâmetro de limite com o valor de (delimitado por aspas duplas) que corresponde ao limite MIME que BNF definido no RFC 2046, seção 5.1.1</span><span class="sxs-lookup"><span data-stu-id="60026-370">R4136: HTTP Content-Type header for a SOAP 1.x MTOM-encoded message must have the boundary parameter with the value (enclosed in double quotation marks) that matches the MIME boundary BNF defined in RFC 2046, section 5.1.1</span></span>  
  
    ```  
    boundary := 0*69<bchars> bcharsnospace   
    bchars := bcharsnospace / " "   
    bcharsnospace :=    DIGIT / ALPHA / "'" / "(" / ")" / "+"   
                        / "_" / "," / "-" / "." / "/" / ":" / "=" / "?"  
    ```  
  
     <span data-ttu-id="60026-371">Exemplos:</span><span class="sxs-lookup"><span data-stu-id="60026-371">Examples:</span></span>  
  
     <span data-ttu-id="60026-372">CORRIGIR</span><span class="sxs-lookup"><span data-stu-id="60026-372">CORRECT</span></span>  
  
    ```  
    Content-Type: multipart/related; type="application/xop+xml";start=" <part0@tempuri.org>";boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1";start-info="text/xml"  
    ```  
  
     <span data-ttu-id="60026-373">CORRIGIR</span><span class="sxs-lookup"><span data-stu-id="60026-373">CORRECT</span></span>  
  
    ```  
    Content-Type: Multipart/Related; type="application/xop+xml";start-info="text/xml";boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1"  
    ```  
  
     <span data-ttu-id="60026-374">INCORRETO</span><span class="sxs-lookup"><span data-stu-id="60026-374">INCORRECT</span></span>  
  
    ```  
    Content-Type: Multipart/Related; type=application/xop+xml;start=" <part0@tempuri.org>";start-info="text/xml";boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1"   
    ```  
  
#### <a name="infoset-mime-part"></a><span data-ttu-id="60026-375">Parte do MIME Infoset</span><span class="sxs-lookup"><span data-stu-id="60026-375">Infoset MIME Part</span></span>  
 <span data-ttu-id="60026-376">O SOAP 1.x Envelope é encapsulado como parte do pacote XOP MIME raiz e geralmente é chamado de `infoset` parte.</span><span class="sxs-lookup"><span data-stu-id="60026-376">The SOAP 1.x Envelope is encapsulated as a root part of the XOP MIME package and is often called the `infoset` part.</span></span>  
  
-   <span data-ttu-id="60026-377">R4141: O SOAP 1.x Envelope deve ser encapsulado como parte da raiz do pacote XOP MIME, chamado o `infoset` parte e referenciado de tipo de conteúdo HTTP.</span><span class="sxs-lookup"><span data-stu-id="60026-377">R4141: The SOAP 1.x Envelope must be encapsulated as a root part of the XOP MIME package, called the `infoset` part and referenced from the HTTP Content-Type.</span></span>  
  
-   <span data-ttu-id="60026-378">R4142: SOAP `Infoset` parte deve incluir os seguintes cabeçalhos MIME: `Content-ID`, `Content-Transfer-Encoding`, e `Content-Type`.</span><span class="sxs-lookup"><span data-stu-id="60026-378">R4142: The SOAP `Infoset` part must include the following MIME headers: `Content-ID`, `Content-Transfer-Encoding`, and `Content-Type`.</span></span>  
  
 <span data-ttu-id="60026-379">O formato do cabeçalho Content-ID é definido por RFC 2045 como</span><span class="sxs-lookup"><span data-stu-id="60026-379">The format of the Content-ID header is defined by RFC 2045 as</span></span>  
  
```  
"Content-ID" ":" msg-id  
```  
  
 <span data-ttu-id="60026-380">onde `msg-id` é definido no RFC 2822 (que substitui o RFC 822, referenciada na RFC 2045) como:</span><span class="sxs-lookup"><span data-stu-id="60026-380">where `msg-id` is defined in RFC 2822 (that supersedes RFC 822, referenced in RFC 2045) as:</span></span>  
  
```  
msg-id    =       [CFWS] "<" id-left "@" id-right ">" [CFWS]  
```  
  
 <span data-ttu-id="60026-381">e é efetivamente um endereço de email incluído dentro de "\<" e ">".</span><span class="sxs-lookup"><span data-stu-id="60026-381">and is effectively an email address enclosed within "\<" and  ">".</span></span> <span data-ttu-id="60026-382">O `[CFWS]` prefixo e sufixo foram adicionadas no RFC 2822 para transportar os comentários e não deve ser usados para preservar a interoperabilidade.</span><span class="sxs-lookup"><span data-stu-id="60026-382">The `[CFWS]` prefix and suffix were added in RFC 2822 to carry comments and should not be used to preserve interoperability.</span></span>  
  
 <span data-ttu-id="60026-383">R4143: O valor do cabeçalho Content-ID para a parte de Infoset MIME deve seguir `msg-id` produção da RFC 2822 com o `[CFWS]` partes de prefixo e sufixo omitidas.</span><span class="sxs-lookup"><span data-stu-id="60026-383">R4143: The value of the Content-ID header for the Infoset MIME part must follow `msg-id` production from RFC 2822 with the `[CFWS]` prefix and suffix parts omitted.</span></span>  
  
 <span data-ttu-id="60026-384">Um número de implementações de MIME relaxada requisitos para o valor incluído dentro de "\<" e ">" para ser um endereço de email e usado `absoluteURI` entre "\<", ">", além do endereço de email.</span><span class="sxs-lookup"><span data-stu-id="60026-384">A number of MIME implementations relaxed requirements for the value enclosed within "\<" and ">" to be an email address and used `absoluteURI` enclosed in "\<" , ">" in addition to the email address.</span></span> <span data-ttu-id="60026-385">Esta versão do WCF usa os valores do cabeçalho MIME Content-ID do formulário:</span><span class="sxs-lookup"><span data-stu-id="60026-385">This version of WCF uses values of the Content-ID MIME header of the form:</span></span>  
  
```  
Content-ID: <http://tempuri.org/0>   
```  
  
 <span data-ttu-id="60026-386">R4144: Processadores MTOM devem aceitar valores de cabeçalho Content-ID que correspondem aos reduzida a seguir `msg-id`.</span><span class="sxs-lookup"><span data-stu-id="60026-386">R4144: MTOM processors should accept Content-ID header values that match the following relaxed `msg-id`.</span></span>  
  
```  
msg-id-relaxed =     [CFWS] "<" (absoluteURI | mail-address) ">" [CFWS]  
mail-address   =     id-left "@" id-right  
```  
  
 <span data-ttu-id="60026-387">MIME (RFC 2045) fornece o cabeçalho Content-Transfer-Encoding para comunicar a codificação do conteúdo da parte MIME.</span><span class="sxs-lookup"><span data-stu-id="60026-387">MIME (RFC 2045) provides the Content-Transfer-Encoding header to communicate encoding of the content of the MIME part.</span></span> <span data-ttu-id="60026-388">O padrão definido para o Content-Transfer-Encoding é de 7 bits, que não é adequado para a maioria das mensagens SOAP, portanto, o cabeçalho Content-Transfer-Encoding é necessária para uma interoperabilidade maior:</span><span class="sxs-lookup"><span data-stu-id="60026-388">The default defined for Content-Transfer-Encoding is 7-bit, which is not suitable for most SOAP messages, so the Content-Transfer-Encoding header is needed for greater interoperability:</span></span>  
  
-   <span data-ttu-id="60026-389">R4145: A parte de Infoset de SOAP deve conter o cabeçalho Content-Transfer-Encoding.</span><span class="sxs-lookup"><span data-stu-id="60026-389">R4145: The SOAP Infoset part must contain the Content-Transfer-Encoding header.</span></span>  
  
-   <span data-ttu-id="60026-390">R4146: Se a codificação de caracteres do Envelope SOAP é UTF-8, o valor do cabeçalho Content-Transfer-Encoding deve ser 8 bits.</span><span class="sxs-lookup"><span data-stu-id="60026-390">R4146: If the SOAP Envelope character encoding is UTF-8, the value of the Content-Transfer-Encoding header must be 8-bit.</span></span>  
  
-   <span data-ttu-id="60026-391">R4147: Se a codificação de caracteres do Envelope SOAP é UTF-16, o valor do cabeçalho Content-Transfer-Encoding deve ser binário.</span><span class="sxs-lookup"><span data-stu-id="60026-391">R4147: If the SOAP Envelope character encoding is UTF-16, the value of the Content-Transfer-Encoding header must be binary.</span></span>  
  
-   <span data-ttu-id="60026-392">[XOP] seção 5, de acordo com</span><span class="sxs-lookup"><span data-stu-id="60026-392">According to [XOP] section 5,</span></span>  
  
-   <span data-ttu-id="60026-393">R4148: Uma parte de Infoset SOAP1.1 deve conter o cabeçalho Content-Type com o tipo de mídia application/xop + xml e parâmetros de tipo = "text/xml" e o conjunto de caracteres</span><span class="sxs-lookup"><span data-stu-id="60026-393">R4148: SOAP1.1 Infoset part must contain Content-Type header with media type application/xop+xml and parameters type="text/xml" and charset</span></span>  
  
    ```  
    Content-Type: application/xop+xml;  
                  charset=utf-8;type="text/xml"  
    ```  
  
-   <span data-ttu-id="60026-394">R4149: A parte de SOAP 1.2 Infoset deve conter o cabeçalho Content-Type com o tipo de mídia `application/xop+xml` e digite parâmetros = "`application/soap+xml`" e `charset`.</span><span class="sxs-lookup"><span data-stu-id="60026-394">R4149: The SOAP 1.2 Infoset part must contain the Content-Type header with media type `application/xop+xml` and parameters type="`application/soap+xml`" and `charset`.</span></span>  
  
    ```  
    Content-Type: application/xop+xml;  
                  charset=utf-8;type="application/soap+xml"  
    ```  
  
     <span data-ttu-id="60026-395">Enquanto XOP define o `charset` parâmetro para `application/xop+xml` para que sejam opcionais, ela é necessária para interoperabilidade semelhante para o requisito de BP 1.1 a `charset` parâmetro para o `text/xml` tipo de mídia.</span><span class="sxs-lookup"><span data-stu-id="60026-395">While XOP defines the `charset` parameter for `application/xop+xml` to be optional, it is needed for interoperability similar to the BP 1.1 requirement on the `charset` parameter for the `text/xml` media type.</span></span>  
  
-   <span data-ttu-id="60026-396">R41410: O `type` e `charset` parâmetros devem estar presentes no cabeçalho Content-Type da parte de Infoset de 1.x de SOAP.</span><span class="sxs-lookup"><span data-stu-id="60026-396">R41410: The `type` and `charset` parameters must be present on the Content-Type header of the SOAP 1.x Infoset part.</span></span>  
  
#### <a name="wcf-endpoint-support-for-mtom"></a><span data-ttu-id="60026-397">Suporte de ponto de extremidade do WCF para MTOM</span><span class="sxs-lookup"><span data-stu-id="60026-397">WCF Endpoint Support for MTOM</span></span>  
 <span data-ttu-id="60026-398">A finalidade do MTOM é codificar uma mensagem SOAP para otimizar o dados codificados em base64.</span><span class="sxs-lookup"><span data-stu-id="60026-398">The purpose of MTOM is to encode a SOAP message to optimize base64-encoded data.</span></span> <span data-ttu-id="60026-399">A seguir está uma lista de restrições:</span><span class="sxs-lookup"><span data-stu-id="60026-399">The following is a list of constraints:</span></span>  
  
-   <span data-ttu-id="60026-400">R4151: Qualquer item de informações do elemento que contém dados codificados em base64 pode ser otimizado.</span><span class="sxs-lookup"><span data-stu-id="60026-400">R4151: Any element information item that contains base64-encoded data may be optimized.</span></span>  
  
-   <span data-ttu-id="60026-401">B4152: WCF otimiza os itens de informações do elemento que contêm dados codificados em base64 e excederem 1.024 bytes de comprimento.</span><span class="sxs-lookup"><span data-stu-id="60026-401">B4152: WCF optimizes element information items that contain base64-encoded data and exceed 1024 bytes in length.</span></span>  
  
 <span data-ttu-id="60026-402">Um ponto de extremidade do WCF configurado para usar MTOM sempre enviarão mensagens codificadas por MTOM.</span><span class="sxs-lookup"><span data-stu-id="60026-402">A WCF endpoint configured to use MTOM will always send MTOM-encoded messages.</span></span> <span data-ttu-id="60026-403">Mesmo que nenhuma parte atendem aos critérios necessários, a mensagem é ainda codificada por MTOM (serializado como um pacote MIME com uma única parte MIME que contém o envelope SOAP).</span><span class="sxs-lookup"><span data-stu-id="60026-403">Even if no parts meet the required criteria, the message is still MTOM-encoded (serialized as a MIME package with a single MIME part containing the SOAP envelope).</span></span>  
  
### <a name="ws-policy-assertion-for-mtom"></a><span data-ttu-id="60026-404">Asserção do WS-Policy para MTOM</span><span class="sxs-lookup"><span data-stu-id="60026-404">WS-Policy Assertion for MTOM</span></span>  
 <span data-ttu-id="60026-405">Para indicar o uso MTOM pelo ponto de extremidade, o WCF usa a seguinte declaração de política:</span><span class="sxs-lookup"><span data-stu-id="60026-405">WCF uses the following policy assertion to indicate MTOM usage by endpoint:</span></span>  
  
```xml  
<wsoma:OptimizedMimeSerialization ... />  
```  
  
-   <span data-ttu-id="60026-406">R4211: A declaração de política anterior tem um assunto de política de ponto de extremidade e especifica que todas as mensagens enviadas e recebidas do ponto de extremidade devem ser otimizadas usando MTOM.</span><span class="sxs-lookup"><span data-stu-id="60026-406">R4211: The preceding policy assertion has an Endpoint Policy Subject and specifies that all messages sent to and received from the endpoint must be optimized using MTOM.</span></span>  
  
-   <span data-ttu-id="60026-407">B4212: Quando configurado para usar a otimização MTOM, um ponto de extremidade do WCF adiciona uma declaração de política de MTOM à política de anexado ao correspondente `wsdl:binding`.</span><span class="sxs-lookup"><span data-stu-id="60026-407">B4212: When configured to use MTOM optimization, an WCF endpoint adds an MTOM Policy assertion to the policy attached to the corresponding `wsdl:binding`.</span></span>  
  
### <a name="composition-with-ws-security"></a><span data-ttu-id="60026-408">Composição com o WS-Security</span><span class="sxs-lookup"><span data-stu-id="60026-408">Composition with WS-Security</span></span>  
 <span data-ttu-id="60026-409">MTOM é um mecanismo de codificação que é semelhante ao `text/xml` e XML binário do WCF.</span><span class="sxs-lookup"><span data-stu-id="60026-409">MTOM is an encoding mechanism that is similar to `text/xml` and WCF Binary XML.</span></span> <span data-ttu-id="60026-410">MTOM oferece composição natural com o WS-Security e outros WS-\* protocolos: uma mensagem protegida usando o WS-Security pode ser otimizada usando MTOM.</span><span class="sxs-lookup"><span data-stu-id="60026-410">MTOM offers natural composition with WS-Security and other WS-\* protocols: a message secured using WS-Security can be optimized using MTOM.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="60026-411">Exemplos</span><span class="sxs-lookup"><span data-stu-id="60026-411">Examples</span></span>  
  
#### <a name="wcf-soap-11-message-encoded-using-mtom"></a><span data-ttu-id="60026-412">WCF SOAP 1.1 mensagem codificada usando MTOM</span><span class="sxs-lookup"><span data-stu-id="60026-412">WCF SOAP 1.1 Message Encoded Using MTOM</span></span>  
  
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
  
#### <a name="wcf-secure-soap-12-message-encoded-using-mtom"></a><span data-ttu-id="60026-413">WCF seguro SOAP 1.2 a mensagem codificada usando MTOM</span><span class="sxs-lookup"><span data-stu-id="60026-413">WCF Secure SOAP 1.2 Message Encoded Using MTOM</span></span>  
 <span data-ttu-id="60026-414">Neste exemplo, uma mensagem é codificada usando MTOM e SOAP 1.2 é protegida usando o WS-Security.</span><span class="sxs-lookup"><span data-stu-id="60026-414">In this example, a message is encoded using MTOM and SOAP 1.2 that is protected using WS-Security.</span></span> <span data-ttu-id="60026-415">As partes binárias identificadas para codificação é o conteúdo do `BinarySecurityToken`, `CipherValue` da `EncryptedData` correspondente à assinatura criptografada e criptografado do corpo.</span><span class="sxs-lookup"><span data-stu-id="60026-415">The binary parts identified for encoding are the contents of the `BinarySecurityToken`, `CipherValue` of the `EncryptedData` corresponding to the encrypted signature and encrypted body.</span></span> <span data-ttu-id="60026-416">Observe que o `CipherValue` do `EncryptedKey` não foi identificada para otimização pelo WCF, porque seu tamanho é menor, em seguida, 1.024 bytes.</span><span class="sxs-lookup"><span data-stu-id="60026-416">Note that the `CipherValue` of the `EncryptedKey` was not identified for optimization by WCF, because its length is less then 1024 bytes.</span></span>  
  
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
