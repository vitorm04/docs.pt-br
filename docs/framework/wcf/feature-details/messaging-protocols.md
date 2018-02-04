---
title: Protocolos de mensagens
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5b20bca7-87b3-4c8f-811b-f215b5987104
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 75a39fa1d0301a48cec7ad61c968ee3fc82d189c
ms.sourcegitcommit: cf22b29db780e532e1090c6e755aa52d28273fa6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2018
---
# <a name="messaging-protocols"></a><span data-ttu-id="ce270-102">Protocolos de mensagens</span><span class="sxs-lookup"><span data-stu-id="ce270-102">Messaging Protocols</span></span>
<span data-ttu-id="ce270-103">O [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] pilha de canais emprega canais de codificação e transporte para transformar a representação interna de mensagem em seu formato de transmissão e enviá-lo usando um transporte particular.</span><span class="sxs-lookup"><span data-stu-id="ce270-103">The [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] channel stack employs encoding and transport channels to transform internal message representation into its wire format and send it by using a particular transport.</span></span> <span data-ttu-id="ce270-104">O transporte mais comuns usado para interoperabilidade de serviços da Web é HTTP e as codificações mais comuns usadas pelos serviços da Web são baseadas em XML SOAP 1.1, SOAP 1.2 e mecanismo de otimização de transmissão mensagem (MTOM).</span><span class="sxs-lookup"><span data-stu-id="ce270-104">The most common transport used for Web services interoperability is HTTP, and the most common encodings used by Web services are XML-based SOAP 1.1, SOAP 1.2, and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="ce270-105">Este tópico aborda [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] detalhes de implementação para os seguintes protocolos usados pelo <xref:System.ServiceModel.Channels.HttpTransportBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="ce270-105">This topic covers [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] implementation details for the following protocols employed by <xref:System.ServiceModel.Channels.HttpTransportBindingElement>.</span></span>  
  
|<span data-ttu-id="ce270-106">Documento de especificação /</span><span class="sxs-lookup"><span data-stu-id="ce270-106">Specification/document</span></span>|<span data-ttu-id="ce270-107">Link</span><span class="sxs-lookup"><span data-stu-id="ce270-107">Link</span></span>|  
|-----------------------------|----------|  
|<span data-ttu-id="ce270-108">HTTP 1.1</span><span class="sxs-lookup"><span data-stu-id="ce270-108">HTTP 1.1</span></span>|<span data-ttu-id="ce270-109">http://www.ietf.org/rfc/rfc2616.txt</span><span class="sxs-lookup"><span data-stu-id="ce270-109">http://www.ietf.org/rfc/rfc2616.txt</span></span>|  
|<span data-ttu-id="ce270-110">Ligação de SOAP 1.1 HTTP</span><span class="sxs-lookup"><span data-stu-id="ce270-110">SOAP 1.1 HTTP Binding</span></span>|<span data-ttu-id="ce270-111">http://www.w3.org/TR/2000/NOTE-SOAP-20000508/, Section 7</span><span class="sxs-lookup"><span data-stu-id="ce270-111">http://www.w3.org/TR/2000/NOTE-SOAP-20000508/, Section 7</span></span>|  
|<span data-ttu-id="ce270-112">SOAP 1.2 associação de HTTP</span><span class="sxs-lookup"><span data-stu-id="ce270-112">SOAP 1.2 HTTP Binding</span></span>|<span data-ttu-id="ce270-113">http://www.w3.org/TR/soap12-part2/, Section 7</span><span class="sxs-lookup"><span data-stu-id="ce270-113">http://www.w3.org/TR/soap12-part2/, Section 7</span></span>|  
  
 <span data-ttu-id="ce270-114">Este tópico aborda [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] detalhes de implementação para os seguintes protocolos que <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> e <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> empregar.</span><span class="sxs-lookup"><span data-stu-id="ce270-114">This topic covers [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] implementation details for the following protocols  that <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> and <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> employ.</span></span>  
  
|<span data-ttu-id="ce270-115">Documento de especificação /</span><span class="sxs-lookup"><span data-stu-id="ce270-115">Specification/Document</span></span>|<span data-ttu-id="ce270-116">Link</span><span class="sxs-lookup"><span data-stu-id="ce270-116">Link</span></span>|  
|-----------------------------|----------|  
|<span data-ttu-id="ce270-117">XML</span><span class="sxs-lookup"><span data-stu-id="ce270-117">XML</span></span>|<span data-ttu-id="ce270-118">http://www.w3.org/TR/REC-xml</span><span class="sxs-lookup"><span data-stu-id="ce270-118">http://www.w3.org/TR/REC-xml</span></span>|  
|<span data-ttu-id="ce270-119">SOAP 1.1</span><span class="sxs-lookup"><span data-stu-id="ce270-119">SOAP 1.1</span></span>|<span data-ttu-id="ce270-120">http://www.w3.org/TR/2000/NOTE-SOAP-20000508/</span><span class="sxs-lookup"><span data-stu-id="ce270-120">http://www.w3.org/TR/2000/NOTE-SOAP-20000508/</span></span>|  
|<span data-ttu-id="ce270-121">SOAP 1.2 Core</span><span class="sxs-lookup"><span data-stu-id="ce270-121">SOAP 1.2 Core</span></span>|<span data-ttu-id="ce270-122">http://www.w3.org/TR/soap12-part1/</span><span class="sxs-lookup"><span data-stu-id="ce270-122">http://www.w3.org/TR/soap12-part1/</span></span>|  
|<span data-ttu-id="ce270-123">WS-Addressing 2004/08</span><span class="sxs-lookup"><span data-stu-id="ce270-123">WS-Addressing 2004/08</span></span>|<span data-ttu-id="ce270-124">http://www.w3.org/Submission/2004/SUBM-ws-addressing-20040810/</span><span class="sxs-lookup"><span data-stu-id="ce270-124">http://www.w3.org/Submission/2004/SUBM-ws-addressing-20040810/</span></span>|  
|<span data-ttu-id="ce270-125">Endereçamento 1.0 - Core de serviços Web do W3C</span><span class="sxs-lookup"><span data-stu-id="ce270-125">W3C Web Services Addressing 1.0 - Core</span></span>|<span data-ttu-id="ce270-126">http://www.w3.org/TR/2006/REC-ws-addr-core-20060509</span><span class="sxs-lookup"><span data-stu-id="ce270-126">http://www.w3.org/TR/2006/REC-ws-addr-core-20060509</span></span>|  
|<span data-ttu-id="ce270-127">Endereçamento associação SOAP 1.0 - de serviços Web do W3C</span><span class="sxs-lookup"><span data-stu-id="ce270-127">W3C Web Services Addressing 1.0 - SOAP Binding</span></span>|<span data-ttu-id="ce270-128">http://www.w3.org/TR/2006/REC-ws-addr-soap-20060509</span><span class="sxs-lookup"><span data-stu-id="ce270-128">http://www.w3.org/TR/2006/REC-ws-addr-soap-20060509</span></span>|  
|<span data-ttu-id="ce270-129">Endereçamento associação WSDL 1.0 - de serviços Web do W3C</span><span class="sxs-lookup"><span data-stu-id="ce270-129">W3C Web Services Addressing 1.0 - WSDL Binding</span></span>|<span data-ttu-id="ce270-130">http://www.w3.org/TR/2006/CR-ws-addr-wsdl-20060529/</span><span class="sxs-lookup"><span data-stu-id="ce270-130">http://www.w3.org/TR/2006/CR-ws-addr-wsdl-20060529/</span></span>|  
<span data-ttu-id="ce270-131">Endereçamento 1.0 - metadados de serviços Web do W3C</span><span class="sxs-lookup"><span data-stu-id="ce270-131">W3C Web Services Addressing 1.0 - Metadata</span></span>|<span data-ttu-id="ce270-132">http://www.w3.org/TR/ws-addr-metadata/</span><span class="sxs-lookup"><span data-stu-id="ce270-132">http://www.w3.org/TR/ws-addr-metadata/</span></span>|  
|<span data-ttu-id="ce270-133">Associação de SOAP1.1 WSDL</span><span class="sxs-lookup"><span data-stu-id="ce270-133">WSDL SOAP1.1 Binding</span></span>|<span data-ttu-id="ce270-134">http://www.w3.org/TR/wsdl/</span><span class="sxs-lookup"><span data-stu-id="ce270-134">http://www.w3.org/TR/wsdl/</span></span>|  
|<span data-ttu-id="ce270-135">Associação de SOAP1.2 WSDL</span><span class="sxs-lookup"><span data-stu-id="ce270-135">WSDL SOAP1.2 Binding</span></span>|<span data-ttu-id="ce270-136">http://www.w3.org/Submission/wsdl11soap12/</span><span class="sxs-lookup"><span data-stu-id="ce270-136">http://www.w3.org/Submission/wsdl11soap12/</span></span>|  
  
 <span data-ttu-id="ce270-137">Este tópico aborda [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] detalhes de implementação para os seguintes protocolos que <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> utiliza.</span><span class="sxs-lookup"><span data-stu-id="ce270-137">This topic covers [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] implementation details for the following protocols that <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> employs.</span></span>  
  
|<span data-ttu-id="ce270-138">Documento de especificação /</span><span class="sxs-lookup"><span data-stu-id="ce270-138">Specification/document</span></span>|<span data-ttu-id="ce270-139">Link</span><span class="sxs-lookup"><span data-stu-id="ce270-139">Link</span></span>|  
|-----------------------------|----------|  
|<span data-ttu-id="ce270-140">XOP</span><span class="sxs-lookup"><span data-stu-id="ce270-140">XOP</span></span>|<span data-ttu-id="ce270-141">http://www.w3.org/TR/xop10/</span><span class="sxs-lookup"><span data-stu-id="ce270-141">http://www.w3.org/TR/xop10/</span></span>|  
|<span data-ttu-id="ce270-142">MTOM + SOAP 1.2 associação</span><span class="sxs-lookup"><span data-stu-id="ce270-142">MTOM + SOAP 1.2 Binding</span></span>|<span data-ttu-id="ce270-143">http://www.w3.org/TR/soap12-mtom/</span><span class="sxs-lookup"><span data-stu-id="ce270-143">http://www.w3.org/TR/soap12-mtom/</span></span>|  
|<span data-ttu-id="ce270-144">MTOM ligação de SOAP 1.1</span><span class="sxs-lookup"><span data-stu-id="ce270-144">MTOM SOAP 1.1 Binding</span></span>|<span data-ttu-id="ce270-145">http://www.w3.org/Submission/soap11mtom10/</span><span class="sxs-lookup"><span data-stu-id="ce270-145">http://www.w3.org/Submission/soap11mtom10/</span></span>|  
|<span data-ttu-id="ce270-146">Asserção do WS-Policy MTOM</span><span class="sxs-lookup"><span data-stu-id="ce270-146">MTOM WS-Policy Assertion</span></span>|<span data-ttu-id="ce270-147">http://www.w3.org/Submission/2006/SUBM-WS-MTOMPolicy-20061101/.</span><span class="sxs-lookup"><span data-stu-id="ce270-147">http://www.w3.org/Submission/2006/SUBM-WS-MTOMPolicy-20061101/.</span></span>|  
  
 <span data-ttu-id="ce270-148">Os seguintes namespaces XML e prefixos associados são usados ao longo deste tópico.</span><span class="sxs-lookup"><span data-stu-id="ce270-148">The following XML namespaces and associated prefixes are used throughout this topic.</span></span>  
  
|<span data-ttu-id="ce270-149">Prefixo</span><span class="sxs-lookup"><span data-stu-id="ce270-149">Prefix</span></span>|<span data-ttu-id="ce270-150">Namespace Uniform Resource Identifier (URI)</span><span class="sxs-lookup"><span data-stu-id="ce270-150">Namespace Uniform Resource Identifier (URI)</span></span>|  
|------------|---------------------------------------------------|  
|<span data-ttu-id="ce270-151">s11</span><span class="sxs-lookup"><span data-stu-id="ce270-151">s11</span></span>|<span data-ttu-id="ce270-152">http://schemas.xmlsoap.org/soap/envelope</span><span class="sxs-lookup"><span data-stu-id="ce270-152">http://schemas.xmlsoap.org/soap/envelope</span></span>|  
|<span data-ttu-id="ce270-153">s12</span><span class="sxs-lookup"><span data-stu-id="ce270-153">s12</span></span>|<span data-ttu-id="ce270-154">http://www.w3.org/2003/05/soap-envelope</span><span class="sxs-lookup"><span data-stu-id="ce270-154">http://www.w3.org/2003/05/soap-envelope</span></span>|  
|<span data-ttu-id="ce270-155">wsa</span><span class="sxs-lookup"><span data-stu-id="ce270-155">wsa</span></span>|<span data-ttu-id="ce270-156">http://www.w3.org/2004/08/addressing</span><span class="sxs-lookup"><span data-stu-id="ce270-156">http://www.w3.org/2004/08/addressing</span></span>|  
|<span data-ttu-id="ce270-157">wsam</span><span class="sxs-lookup"><span data-stu-id="ce270-157">wsam</span></span>|<span data-ttu-id="ce270-158">http://www.w3.org/2007/05/addressing/metadata</span><span class="sxs-lookup"><span data-stu-id="ce270-158">http://www.w3.org/2007/05/addressing/metadata</span></span>|  
|<span data-ttu-id="ce270-159">wsap</span><span class="sxs-lookup"><span data-stu-id="ce270-159">wsap</span></span>|<span data-ttu-id="ce270-160">http://schemas.xmlsoap.org/ws/2004/09/policy/addressing</span><span class="sxs-lookup"><span data-stu-id="ce270-160">http://schemas.xmlsoap.org/ws/2004/09/policy/addressing</span></span>|  
|<span data-ttu-id="ce270-161">wsa10</span><span class="sxs-lookup"><span data-stu-id="ce270-161">wsa10</span></span>|<span data-ttu-id="ce270-162">http://www.w3.org/2005/08/addressing</span><span class="sxs-lookup"><span data-stu-id="ce270-162">http://www.w3.org/2005/08/addressing</span></span>|  
|<span data-ttu-id="ce270-163">wsaw10</span><span class="sxs-lookup"><span data-stu-id="ce270-163">wsaw10</span></span>|<span data-ttu-id="ce270-164">http://www.w3.org/2006/05/addressing/wsdl</span><span class="sxs-lookup"><span data-stu-id="ce270-164">http://www.w3.org/2006/05/addressing/wsdl</span></span>|  
|<span data-ttu-id="ce270-165">XOP</span><span class="sxs-lookup"><span data-stu-id="ce270-165">xop</span></span>|<span data-ttu-id="ce270-166">http://www.w3.org/2004/08/xop/include</span><span class="sxs-lookup"><span data-stu-id="ce270-166">http://www.w3.org/2004/08/xop/include</span></span>|  
|<span data-ttu-id="ce270-167">xmime</span><span class="sxs-lookup"><span data-stu-id="ce270-167">xmime</span></span>|<span data-ttu-id="ce270-168">http://www.w3.org/2004/06/xmlmime</span><span class="sxs-lookup"><span data-stu-id="ce270-168">http://www.w3.org/2004/06/xmlmime</span></span><br /><br /> <span data-ttu-id="ce270-169">http://www.w3.org/2005/05/xmlmime</span><span class="sxs-lookup"><span data-stu-id="ce270-169">http://www.w3.org/2005/05/xmlmime</span></span>|  
<span data-ttu-id="ce270-170">dp</span><span class="sxs-lookup"><span data-stu-id="ce270-170">dp</span></span>|<span data-ttu-id="ce270-171">http://schemas.microsoft.com/net/2006/06/duplex</span><span class="sxs-lookup"><span data-stu-id="ce270-171">http://schemas.microsoft.com/net/2006/06/duplex</span></span>|  
  
## <a name="soap-11-and-soap-12"></a><span data-ttu-id="ce270-172">SOAP 1.1 e SOAP 1.2</span><span class="sxs-lookup"><span data-stu-id="ce270-172">SOAP 1.1 and SOAP 1.2</span></span>  
  
### <a name="envelope-and-processing-model"></a><span data-ttu-id="ce270-173">Envelope e processamento de modelo</span><span class="sxs-lookup"><span data-stu-id="ce270-173">Envelope and Processing Model</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] <span data-ttu-id="ce270-174">implementa o processamento do envelope SOAP 1.1 Basic Profile 1.1 (BP11) e Basic Profile 1.0 (SSBP10) a seguir.</span><span class="sxs-lookup"><span data-stu-id="ce270-174">implements SOAP 1.1 envelope processing following Basic Profile 1.1 (BP11) and Basic Profile 1.0 (SSBP10).</span></span> <span data-ttu-id="ce270-175">SOAP 1.2 Envelope processamento é implementado Parte1 SOAP12 a seguir.</span><span class="sxs-lookup"><span data-stu-id="ce270-175">SOAP 1.2 Envelope processing is implemented following SOAP12-Part1.</span></span>  
  
 <span data-ttu-id="ce270-176">Esta seção explica certas opções de implementação realizadas pelo [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] relativas à BP11 e SOAP12 Parte1.</span><span class="sxs-lookup"><span data-stu-id="ce270-176">This section explains certain implementation choices taken by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] with regard to BP11 and SOAP12-Part1.</span></span>  
  
#### <a name="mandatory-header-processing"></a><span data-ttu-id="ce270-177">Processamento de cabeçalho obrigatório</span><span class="sxs-lookup"><span data-stu-id="ce270-177">Mandatory Header Processing</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] <span data-ttu-id="ce270-178">segue as regras para processar cabeçalhos marcados `mustUnderstand` descrito nas especificações SOAP 1.1 e SOAP 1.2, com as seguintes variações.</span><span class="sxs-lookup"><span data-stu-id="ce270-178">follows rules for processing headers marked `mustUnderstand` described in the SOAP 1.1 and SOAP 1.2 specifications, with the following variations.</span></span>  
  
 <span data-ttu-id="ce270-179">Uma mensagem que entra o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] pilha de canais é processada pelo canais individuais configurados pelos elementos de associação associada, por exemplo, codificação de mensagem de texto, segurança, mensagens confiáveis e transações.</span><span class="sxs-lookup"><span data-stu-id="ce270-179">A message that enters the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] channel stack is processed by individual channels configured by associated binding elements, for example, Text Message Encoding, Security, Reliable Messaging, and Transactions.</span></span> <span data-ttu-id="ce270-180">Cada canal reconhece os cabeçalhos do namespace associado e marca-os conforme entendido.</span><span class="sxs-lookup"><span data-stu-id="ce270-180">Each channel recognizes headers from the associated namespace and marks them as understood.</span></span> <span data-ttu-id="ce270-181">Depois que uma mensagem insere o distribuidor, o formatador de operação lê cabeçalhos esperados pelo contrato de mensagem/operação e marcas-los compreendidos correspondente.</span><span class="sxs-lookup"><span data-stu-id="ce270-181">Once a message enters the dispatcher, the operation formatter reads headers expected by the corresponding message/operation contract and marks them understood.</span></span> <span data-ttu-id="ce270-182">Em seguida, o distribuidor verifica se todos os cabeçalhos restantes não são compreendidos mas marcados como `mustUnderstand` e lançará uma exceção.</span><span class="sxs-lookup"><span data-stu-id="ce270-182">Then the dispatcher verifies whether any remaining headers are not understood but marked as `mustUnderstand` and throws an exception.</span></span> <span data-ttu-id="ce270-183">As mensagens que contêm `mustUnderstand` cabeçalhos que são destinados ao destinatário não são processados pelo código do aplicativo de destino.</span><span class="sxs-lookup"><span data-stu-id="ce270-183">Messages that contain `mustUnderstand` headers that are targeted at the recipient are not processed by recipient application code.</span></span>  
  
 <span data-ttu-id="ce270-184">Como em camadas processamento permite a separação entre camadas de infraestrutura e de aplicativo do nó de SOAP:</span><span class="sxs-lookup"><span data-stu-id="ce270-184">Such layered processing allows for separation between infrastructure layers and application layers of the SOAP node:</span></span>  
  
-   <span data-ttu-id="ce270-185">B1111: Cabeçalhos que não são compreendidos são detectados depois que a mensagem é processada pelo [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] pilha de canais de infraestrutura, mas antes de ser processada por aplicativo</span><span class="sxs-lookup"><span data-stu-id="ce270-185">B1111: Headers that are not understood are detected after the message is processed by the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] infrastructure channel stack, but before it is processed by application</span></span>  
  
     <span data-ttu-id="ce270-186">O `mustUnderstand` difere do valor do cabeçalho entre SOAP 1.1 e SOAP 1.2.</span><span class="sxs-lookup"><span data-stu-id="ce270-186">The `mustUnderstand` header value differs between SOAP 1.1 and SOAP 1.2.</span></span> <span data-ttu-id="ce270-187">Basic Profile 1.1 requer que o `mustUnderstand` valor ser 0 ou 1 para mensagens SOAP 1.1.</span><span class="sxs-lookup"><span data-stu-id="ce270-187">Basic Profile 1.1 requires that the `mustUnderstand` value be 0 or 1 for SOAP 1.1 messages.</span></span> <span data-ttu-id="ce270-188">SOAP 1.2 permite 0, 1, `false`, e `true` como valores, mas recomenda emitindo uma representação canônica `xs:boolean` valores (`false`, `true`).</span><span class="sxs-lookup"><span data-stu-id="ce270-188">SOAP 1.2 allows 0, 1, `false`, and `true` as values, but recommends emitting a canonical representation of `xs:boolean` values (`false`, `true`).</span></span>  
  
-   <span data-ttu-id="ce270-189">B1112: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] emite `mustUnderstand` valores 0 e 1 para versões de SOAP 1.1 e SOAP 1.2 do envelope SOAP.</span><span class="sxs-lookup"><span data-stu-id="ce270-189">B1112: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] emits `mustUnderstand` values 0 and 1 for both SOAP 1.1 and SOAP 1.2 versions of the SOAP envelope.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="ce270-190">aceita o espaço de valor inteiro de `xs:boolean` para o `mustUnderstand` cabeçalho (0, 1, `false`, `true`)</span><span class="sxs-lookup"><span data-stu-id="ce270-190"> accepts the entire value space of `xs:boolean` for the `mustUnderstand` header (0, 1, `false`, `true`)</span></span>  
  
#### <a name="soap-faults"></a><span data-ttu-id="ce270-191">Falhas de SOAP</span><span class="sxs-lookup"><span data-stu-id="ce270-191">SOAP Faults</span></span>  
 <span data-ttu-id="ce270-192">A seguir está uma lista de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]-implementações específicas de falhas SOAP.</span><span class="sxs-lookup"><span data-stu-id="ce270-192">The following is a list of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]-specific SOAP fault implementations.</span></span>  
  
-   <span data-ttu-id="ce270-193">B2121: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] retorna os seguintes códigos de falha de SOAP 1.1: `s11:mustUnderstand`, `s11:Client`, e `s11:Server`.</span><span class="sxs-lookup"><span data-stu-id="ce270-193">B2121: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] returns the following SOAP 1.1 Fault Codes: `s11:mustUnderstand`, `s11:Client`, and `s11:Server`.</span></span>  
  
-   <span data-ttu-id="ce270-194">B2122: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] retorna os seguintes códigos de falha de SOAP 1.2: `s12:MustUnderstand`, `s12:Sender`, e `s12:Receiver`.</span><span class="sxs-lookup"><span data-stu-id="ce270-194">B2122: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] returns the following SOAP 1.2 Fault Codes: `s12:MustUnderstand`, `s12:Sender`, and `s12:Receiver`.</span></span>  
  
### <a name="http-binding"></a><span data-ttu-id="ce270-195">Associação HTTP</span><span class="sxs-lookup"><span data-stu-id="ce270-195">HTTP Binding</span></span>  
  
#### <a name="soap-11-http-binding"></a><span data-ttu-id="ce270-196">Ligação de SOAP 1.1 HTTP</span><span class="sxs-lookup"><span data-stu-id="ce270-196">SOAP 1.1 HTTP Binding</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] <span data-ttu-id="ce270-197">implementa a associação HTTP SOAP1.1 após a especificação de Basic Profile 1.1 seção 3.4 com os seguintes esclarecimentos:</span><span class="sxs-lookup"><span data-stu-id="ce270-197">implements SOAP1.1 HTTP binding following the Basic Profile 1.1 specification section 3.4 with the following clarifications:</span></span>  
  
-   <span data-ttu-id="ce270-198">B2211: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço não implementa o redirecionamento de solicitações HTTP POST.</span><span class="sxs-lookup"><span data-stu-id="ce270-198">B2211: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service does not implement redirection of HTTP POST requests.</span></span>  
  
-   <span data-ttu-id="ce270-199">B2212: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] os clientes oferecem suporte a Cookies HTTP conforme 3.4.8.</span><span class="sxs-lookup"><span data-stu-id="ce270-199">B2212: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] clients support HTTP Cookies in accordance with 3.4.8.</span></span>  
  
#### <a name="soap-12-http-binding"></a><span data-ttu-id="ce270-200">SOAP 1.2 associação de HTTP</span><span class="sxs-lookup"><span data-stu-id="ce270-200">SOAP 1.2 HTTP Binding</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] <span data-ttu-id="ce270-201">implementa associação SOAP 1.2 HTTP conforme descrito na SOAP 1.2-parte 2 (SOAP12Part2) especificação com as seguintes esclarecimentos.</span><span class="sxs-lookup"><span data-stu-id="ce270-201">implements SOAP 1.2 HTTP binding as described in the SOAP 1.2-part 2 (SOAP12Part2) specification with the following clarifications.</span></span>  
  
 <span data-ttu-id="ce270-202">SOAP 1.2 introduziu um parâmetro de ação opcional para o `application/soap+xml` tipo de mídia.</span><span class="sxs-lookup"><span data-stu-id="ce270-202">SOAP 1.2 introduced an optional action parameter for the `application/soap+xml` media type.</span></span> <span data-ttu-id="ce270-203">Esse parâmetro é útil para otimizar a expedição de mensagem sem a necessidade de que o corpo da mensagem SOAP servirá quando WS-Addressing não é usado.</span><span class="sxs-lookup"><span data-stu-id="ce270-203">This parameter is useful to optimize message dispatch without requiring that the body of the SOAP message be parsed when WS-Addressing is not used.</span></span>  
  
-   <span data-ttu-id="ce270-204">R2221: O `application/soap+xml` parâmetro action, quando presente em uma solicitação de SOAP 1.2, deve corresponder a `soapAction` atributo no `wsoap12:operation` elemento de associação WSDL correspondente.</span><span class="sxs-lookup"><span data-stu-id="ce270-204">R2221: The `application/soap+xml` action parameter, when present on a SOAP 1.2 request, must match the `soapAction` attribute on the `wsoap12:operation` element inside the corresponding WSDL binding.</span></span>  
  
-   <span data-ttu-id="ce270-205">R2222: O `application/soap+xml` parâmetro action, quando presente em uma mensagem SOAP 1.2, deve corresponder `wsa:Action` quando 08/2004 do WS-Addressing ou WS-Addressing 1.0 são usados.</span><span class="sxs-lookup"><span data-stu-id="ce270-205">R2222: The `application/soap+xml` action parameter, when present on a SOAP 1.2 message, must match `wsa:Action` when WS-Addressing 2004/08 or WS-Addressing 1.0 are used.</span></span>  
  
 <span data-ttu-id="ce270-206">Quando o WS-Addressing é desabilitado e uma solicitação de entrada não contém um parâmetro de ação, uma mensagem `Action` é considerado não especificado.</span><span class="sxs-lookup"><span data-stu-id="ce270-206">When WS-Addressing is disabled and an incoming request does not contain an action parameter, message `Action` is considered not specified.</span></span>  
  
## <a name="ws-addressing"></a><span data-ttu-id="ce270-207">WS-Addressing</span><span class="sxs-lookup"><span data-stu-id="ce270-207">WS-Addressing</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] <span data-ttu-id="ce270-208">implementa 3 versões do WS-Addressing:</span><span class="sxs-lookup"><span data-stu-id="ce270-208">implements 3 versions of WS-Addressing:</span></span>  
  
-   <span data-ttu-id="ce270-209">WS-Addressing 2004/08</span><span class="sxs-lookup"><span data-stu-id="ce270-209">WS-Addressing 2004/08</span></span>  
  
-   <span data-ttu-id="ce270-210">Serviços Web do W3C endereçamento SOAP Binding (ADDR10 SOAP) e 1.0 Core (ADDR10 NÚCLEOS)</span><span class="sxs-lookup"><span data-stu-id="ce270-210">W3C Web Services Addressing 1.0 Core  (ADDR10-CORE) and SOAP Binding (ADDR10-SOAP)</span></span>  
  
-   <span data-ttu-id="ce270-211">WS-Addressing 1.0 - metadados</span><span class="sxs-lookup"><span data-stu-id="ce270-211">WS-Addressing 1.0 - Metadata</span></span>  
  
### <a name="endpoint-references"></a><span data-ttu-id="ce270-212">Referências de ponto de extremidade</span><span class="sxs-lookup"><span data-stu-id="ce270-212">Endpoint References</span></span>  
 <span data-ttu-id="ce270-213">Todas as versões do WS-Addressing que [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] implementa usa referências de ponto de extremidade para descrever os pontos de extremidade.</span><span class="sxs-lookup"><span data-stu-id="ce270-213">All versions of WS-Addressing that [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] implements use endpoint references to describe endpoints.</span></span>  
  
#### <a name="endpoint-references-and-ws-addressing-versions"></a><span data-ttu-id="ce270-214">Referências de ponto de extremidade e WS-Addressing versões</span><span class="sxs-lookup"><span data-stu-id="ce270-214">Endpoint References and WS-Addressing Versions</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] <span data-ttu-id="ce270-215">implementa vários dos protocolos de infraestrutura que usam o WS-Addressing e, em particular a `EndpointReference` elemento e `W3C.WsAddressing.EndpointReferenceType` classe (por exemplo, WS-ReliableMessaging, WS-SecureConversation e WS-Trust).</span><span class="sxs-lookup"><span data-stu-id="ce270-215">implements a number of the infrastructure protocols that use WS-Addressing and in particular the `EndpointReference` element and `W3C.WsAddressing.EndpointReferenceType` class (for example, WS-ReliableMessaging, WS-SecureConversation, and WS-Trust).</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="ce270-216">oferece suporte ao uso de qualquer versão do WS-Addressing com outros protocolos de infraestrutura.</span><span class="sxs-lookup"><span data-stu-id="ce270-216"> supports the use of either version of WS-Addressing with other infrastructure protocols.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="ce270-217">suportam a pontos de extremidade de uma versão do WS-Addressing por ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="ce270-217"> endpoints support one version of WS-Addressing per endpoint.</span></span>  
  
 <span data-ttu-id="ce270-218">Para R3111, o namespace para o `EndpointReference` elemento ou tipo usado em mensagens trocadas com um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ponto de extremidade deve corresponder à versão do WS-Addressing implementada por este ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="ce270-218">For R3111, the namespace for the `EndpointReference` element or type used in messages exchanged with a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] endpoint must match the version of WS-Addressing implemented by this endpoint.</span></span>  
  
 <span data-ttu-id="ce270-219">Por exemplo, se um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ponto de extremidade implementa o WS-ReliableMessaging a `AcksTo` retornado por tal um ponto de extremidade dentro do cabeçalho `CreateSequenceResponse` usa a versão do WS-Addressing que o `EncodingBinding` elemento especifica para esse ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="ce270-219">For example, if a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] endpoint implements WS-ReliableMessaging, the `AcksTo` header returned by such an endpoint inside `CreateSequenceResponse` uses the WS-Addressing version that the `EncodingBinding` element specifies for this endpoint.</span></span>  
  
#### <a name="endpoint-references-and-metadata"></a><span data-ttu-id="ce270-220">Metadados e referências de ponto de extremidade</span><span class="sxs-lookup"><span data-stu-id="ce270-220">Endpoint References and Metadata</span></span>  
 <span data-ttu-id="ce270-221">Vários cenários exigem a comunicação de metadados ou uma referência aos metadados para um determinado ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="ce270-221">A number of scenarios require communicating metadata or a reference to metadata for a given endpoint.</span></span>  
  
 <span data-ttu-id="ce270-222">B3121: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] emprega mecanismos descritos na especificação do WS-MetadataExchange (MEX), seção 6 para incluir metadados para referências de ponto de extremidade por valor ou por referência.</span><span class="sxs-lookup"><span data-stu-id="ce270-222">B3121: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] employs mechanisms described in the WS-MetadataExchange (MEX) specification Section 6 to include metadata for endpoint references by value or by reference.</span></span>  
  
 <span data-ttu-id="ce270-223">Considere um cenário onde um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço requer autenticação usando um token de segurança asserções Markup Language (SAML) emitido pelo emissor de token em http://sts.fabrikam123.com. O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ponto de extremidade descreve esse requisito de autenticação usando `sp:IssuedToken` asserção com uma instrução `sp:Issuer` asserção apontando para o emissor do token.</span><span class="sxs-lookup"><span data-stu-id="ce270-223">Consider a scenario where a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service requires authentication using a Security Assertions Markup Language (SAML) token issued by the token issuer at http://sts.fabrikam123.com. The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] endpoint describes this authentication requirement by using `sp:IssuedToken` assertion with a nested `sp:Issuer` assertion pointing to the token issuer.</span></span> <span data-ttu-id="ce270-224">Aplicativos cliente que acessam o `sp:Issuer` asserção precisam saber como se comunicar com o ponto de extremidade do emissor do token.</span><span class="sxs-lookup"><span data-stu-id="ce270-224">Client applications that access the `sp:Issuer` assertion need to know how to communicate with the token issuer endpoint.</span></span> <span data-ttu-id="ce270-225">O cliente precisa saber metadados sobre o emissor do token.</span><span class="sxs-lookup"><span data-stu-id="ce270-225">The client needs to know metadata about the token issuer.</span></span> <span data-ttu-id="ce270-226">Usando as extensões de metadados de referência do ponto de extremidade definidas no MEX, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] fornece uma referência aos metadados do emissor do token.</span><span class="sxs-lookup"><span data-stu-id="ce270-226">Using the endpoint reference metadata extensions defined in MEX, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] provides a reference to the token issuer metadata.</span></span>  
  
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
  
### <a name="message-addressing-headers"></a><span data-ttu-id="ce270-227">Cabeçalhos de endereçamento de mensagem</span><span class="sxs-lookup"><span data-stu-id="ce270-227">Message Addressing Headers</span></span>  
  
#### <a name="message-headers"></a><span data-ttu-id="ce270-228">Cabeçalhos de mensagem</span><span class="sxs-lookup"><span data-stu-id="ce270-228">Message Headers</span></span>  
 <span data-ttu-id="ce270-229">Para ambas as versões do WS-Addressing, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usa os seguintes cabeçalhos de mensagem, conforme descrito pelas especificações `wsa:To`, `wsa:ReplyTo`, `wsa:Action`, `wsa:MessageID`, e `wsa:RelatesTo`.</span><span class="sxs-lookup"><span data-stu-id="ce270-229">For both WS-Addressing versions, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uses the following message headers as prescribed by the specifications `wsa:To`, `wsa:ReplyTo`, `wsa:Action`, `wsa:MessageID`,and `wsa:RelatesTo`.</span></span>  
  
 <span data-ttu-id="ce270-230">B3211: para todas as versões de WS-Addressing, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] honra, mas não produzir pronta, cabeçalhos de mensagem do WS-Addressing `wsa:FaultTo` e `wsa:From`.</span><span class="sxs-lookup"><span data-stu-id="ce270-230">B3211: For all WS-Addressing versions, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] honors, but does not produce out of the box, WS-Addressing message headers `wsa:FaultTo` and `wsa:From`.</span></span>  
  
 <span data-ttu-id="ce270-231">Aplicativos que interagem com [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplicativos podem adicionar esses cabeçalhos de mensagem e [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] processará adequadamente.</span><span class="sxs-lookup"><span data-stu-id="ce270-231">Applications that interact with [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications can add these message headers and [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] will process them accordingly.</span></span>  
  
#### <a name="reference-parameters-and-properties"></a><span data-ttu-id="ce270-232">Propriedades e parâmetros de referência</span><span class="sxs-lookup"><span data-stu-id="ce270-232">Reference Parameters and Properties</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] <span data-ttu-id="ce270-233">implementa o processamento dos parâmetros de referência de ponto de extremidade e referência p</span><span class="sxs-lookup"><span data-stu-id="ce270-233">implements processing of endpoint reference parameters and reference p</span></span>  
  
 <span data-ttu-id="ce270-234">Propriedades de acordo com as especificações do respectivas.</span><span class="sxs-lookup"><span data-stu-id="ce270-234">roperties in accordance with respective specifications.</span></span>  
  
 <span data-ttu-id="ce270-235">B3221: Quando estiver configurado para usar 08/2004 do WS-Addressing, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] pontos de extremidade não fazem distinção entre propriedades de referência e parâmetros de referência de processamento.</span><span class="sxs-lookup"><span data-stu-id="ce270-235">B3221: When configured to use WS-Addressing 2004/08, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] endpoints do not differentiate between processing Reference Properties and Reference Parameters.</span></span>  
  
### <a name="message-exchange-patterns"></a><span data-ttu-id="ce270-236">Padrões de troca de mensagem</span><span class="sxs-lookup"><span data-stu-id="ce270-236">Message Exchange Patterns</span></span>  
 <span data-ttu-id="ce270-237">A sequência de mensagens envolvidas na invocação de operação de serviço da Web é conhecida como o *padrão de troca de mensagem*.</span><span class="sxs-lookup"><span data-stu-id="ce270-237">The sequence of messages involved in the Web service operation invocation is referred to as the *message exchange pattern*.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="ce270-238">padrões de troca unidirecional dá suporte à solicitação-resposta e mensagens duplex.</span><span class="sxs-lookup"><span data-stu-id="ce270-238"> supports one-way, request-reply, and duplex message exchange patterns.</span></span> <span data-ttu-id="ce270-239">Esta seção explica WS-Addressing requisitos na mensagem de processamento dependendo do padrão de troca de mensagem que está sendo usado.</span><span class="sxs-lookup"><span data-stu-id="ce270-239">This section clarifies WS-Addressing requirements on message processing depending on the message exchange pattern being used.</span></span>  
  
 <span data-ttu-id="ce270-240">Ao longo desta seção, o solicitante envia a primeira mensagem e o respondedor recebe a primeira mensagem.</span><span class="sxs-lookup"><span data-stu-id="ce270-240">Throughout this section, the requester sends the first message and the responder receives the first message.</span></span>  
  
#### <a name="one-way-message"></a><span data-ttu-id="ce270-241">Mensagem unidirecional</span><span class="sxs-lookup"><span data-stu-id="ce270-241">One-Way Message</span></span>  
 <span data-ttu-id="ce270-242">Quando um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ponto de extremidade é configurado para oferecer suporte a mensagens com um determinado `Action` para seguir o padrão unidirecional, o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ponto de extremidade segue os requisitos e os comportamentos a seguir.</span><span class="sxs-lookup"><span data-stu-id="ce270-242">When a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] endpoint is configured to support messages with a given `Action` to follow a one-way pattern, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] endpoint follows the following behaviors and requirements.</span></span> <span data-ttu-id="ce270-243">A menos que especificado o contrário, comportamentos e regras se aplicam para ambas as versões do WS-Addressing tem suporte em [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="ce270-243">Unless otherwise specified, behaviors and rules apply for both versions of WS-Addressing supported in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:</span></span>  
  
-   <span data-ttu-id="ce270-244">R3311: O solicitante deve incluir `wsa:To`, `wsa:Action`e os cabeçalhos para todos os parâmetros de referência especificados pela referência de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="ce270-244">R3311: The requester must include `wsa:To`, `wsa:Action`, and headers for all reference parameters specified by the endpoint reference.</span></span> <span data-ttu-id="ce270-245">Quando 08/2004 do WS-Addressing é usado e [Propriedades da referência] são especificados pela referência de ponto de extremidade, os cabeçalhos correspondentes devem ser adicionados à mensagem muito.</span><span class="sxs-lookup"><span data-stu-id="ce270-245">When WS-Addressing 2004/08 is used and [reference properties] are specified by the endpoint reference, the corresponding headers must be added to the message too.</span></span>  
  
-   <span data-ttu-id="ce270-246">B3312: O solicitante pode incluir `MessageID`, `ReplyTo`, e `FaultTo` cabeçalhos.</span><span class="sxs-lookup"><span data-stu-id="ce270-246">B3312: The requester may include `MessageID`, `ReplyTo`, and `FaultTo` headers.</span></span> <span data-ttu-id="ce270-247">A infraestrutura de destinatário irá ignorá-las e eles serão passados para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ce270-247">The receiver infrastructure will ignore them, and they will be passed to the application.</span></span>  
  
-   <span data-ttu-id="ce270-248">R3313: Quando HTTP é usado e nenhuma mensagem está sendo enviada no trecho de resposta HTTP, o Respondente deve enviar uma resposta HTTP com um corpo vazio e um código de status HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="ce270-248">R3313: When HTTP is used and no message is being sent on the HTTP response leg, the responder must send an HTTP response with an empty body and an HTTP 202 status code.</span></span>  
  
     <span data-ttu-id="ce270-249">Quando o transporte HTTP está em uso e o contrato da operação declara uma mensagem unidirecional, a resposta HTTP ainda pode ser usada para enviar mensagens de infraestrutura — por exemplo, o sistema de mensagens confiável pode enviar um `SequenceAcknowledgement` mensagem em uma resposta HTTP.</span><span class="sxs-lookup"><span data-stu-id="ce270-249">When the HTTP transport is in use and the operation contract declares a message one-way, the HTTP response can still be used for sending infrastructure messages—for example, reliable messaging can send a `SequenceAcknowledgement` message on an HTTP response.</span></span>  
  
-   <span data-ttu-id="ce270-250">B3314: O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Respondente não envia uma mensagem de falha em resposta a uma mensagem unidirecional.</span><span class="sxs-lookup"><span data-stu-id="ce270-250">B3314: The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] responder does not send a fault message in response to a one-way message.</span></span>  
  
#### <a name="request-reply"></a><span data-ttu-id="ce270-251">Solicitação-resposta</span><span class="sxs-lookup"><span data-stu-id="ce270-251">Request-Reply</span></span>  
 <span data-ttu-id="ce270-252">Quando um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ponto de extremidade é configurado para uma mensagem com um determinado `Action` seguir o padrão de solicitação-resposta, o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ponto de extremidade segue os comportamentos e os requisitos abaixo.</span><span class="sxs-lookup"><span data-stu-id="ce270-252">When a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] endpoint is configured for a message with a given `Action` to follow the request-reply pattern, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] endpoint follows the behaviors and requirements below.</span></span> <span data-ttu-id="ce270-253">A menos que especificado o contrário, comportamentos e regras se aplicam para ambas as versões do WS-Addressing tem suporte em [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="ce270-253">Unless specified otherwise, behaviors and rules apply for both versions of WS-Addressing supported in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:</span></span>  
  
-   <span data-ttu-id="ce270-254">R3321: O solicitante deve incluir na solicitação `wsa:To`, `wsa:Action`, `wsa:MessageID`e os cabeçalhos para todos os parâmetros de referência ou referência propriedades (ou ambos) especificado pela referência de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="ce270-254">R3321: The requester must include in the request `wsa:To`, `wsa:Action`, `wsa:MessageID`, and headers for all reference parameters or reference properties (or both) specified by the endpoint reference.</span></span>  
  
-   <span data-ttu-id="ce270-255">R3322: Quando 08/2004 do WS-Addressing é usado, `ReplyTo` também deve ser incluído na solicitação.</span><span class="sxs-lookup"><span data-stu-id="ce270-255">R3322: When WS-Addressing 2004/08 is used, `ReplyTo` must also be included in the request.</span></span>  
  
-   <span data-ttu-id="ce270-256">R3323: Quando WS-Addressing 1.0 é usada e `ReplyTo` é não está presente na solicitação, uma referência de ponto de extremidade padrão com a propriedade [address] igual a "http://www.w3.org/2005/08/addressing/anonymous" é usada.</span><span class="sxs-lookup"><span data-stu-id="ce270-256">R3323: When WS-Addressing 1.0 is used and `ReplyTo` is not present in the request, a default endpoint reference with the [address] property equal to "http://www.w3.org/2005/08/addressing/anonymous" is used.</span></span>  
  
-   <span data-ttu-id="ce270-257">R3324: O solicitante deve incluir `wsa:To`, `wsa:Action`, e `wsa:RelatesTo` cabeçalhos na mensagem de resposta, bem como os cabeçalhos para todos os parâmetros de referência ou referência propriedades (ou ambos) especificado pelo `ReplyTo` referência de ponto de extremidade do solicitação.</span><span class="sxs-lookup"><span data-stu-id="ce270-257">R3324: The requester must include `wsa:To`, `wsa:Action`, and `wsa:RelatesTo` headers in the reply message, as well as headers for all reference parameters or reference properties (or both) specified by the `ReplyTo` endpoint reference in the request.</span></span>  
  
### <a name="web-services-addressing-faults"></a><span data-ttu-id="ce270-258">Falhas de endereçamento de serviços Web</span><span class="sxs-lookup"><span data-stu-id="ce270-258">Web Services Addressing Faults</span></span>  
 <span data-ttu-id="ce270-259">R3411: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] produz as seguintes falhas definidas pelo 2004 do WS-Addressing/08.</span><span class="sxs-lookup"><span data-stu-id="ce270-259">R3411: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] produces the following faults defined by WS-Addressing 2004/08.</span></span>  
  
|<span data-ttu-id="ce270-260">Código</span><span class="sxs-lookup"><span data-stu-id="ce270-260">Code</span></span>|<span data-ttu-id="ce270-261">Causa</span><span class="sxs-lookup"><span data-stu-id="ce270-261">Cause</span></span>|  
|----------|-----------|  
|<span data-ttu-id="ce270-262">wsa:DestinationUnreachable</span><span class="sxs-lookup"><span data-stu-id="ce270-262">wsa:DestinationUnreachable</span></span>|<span data-ttu-id="ce270-263">A mensagem chegou com um `ReplyTo` , que é diferente do endereço de resposta estabelecido para este canal; não há nenhum ponto de extremidade escutando no endereço especificado no cabeçalho de para.</span><span class="sxs-lookup"><span data-stu-id="ce270-263">The message arrived with a `ReplyTo` that is different from the reply address established for this channel; there is no endpoint listening at the address specified in the To header.</span></span>|  
|<span data-ttu-id="ce270-264">wsa:ActionNotSupported</span><span class="sxs-lookup"><span data-stu-id="ce270-264">wsa:ActionNotSupported</span></span>|<span data-ttu-id="ce270-265">os canais de infraestrutura ou distribuidor associado com o ponto de extremidade não reconhecem a ação especificada no `Action` cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="ce270-265">the infrastructure channels or dispatcher associated with the endpoint do not recognize the action specified in the `Action` header.</span></span>|  
  
 <span data-ttu-id="ce270-266">R3412: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] produz as seguintes falhas definidas por WS-Addressing 1.0.</span><span class="sxs-lookup"><span data-stu-id="ce270-266">R3412: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] produces the following faults defined by WS-Addressing 1.0.</span></span>  
  
|<span data-ttu-id="ce270-267">Código</span><span class="sxs-lookup"><span data-stu-id="ce270-267">Code</span></span>|<span data-ttu-id="ce270-268">Causa</span><span class="sxs-lookup"><span data-stu-id="ce270-268">Cause</span></span>|  
|----------|-----------|  
|<span data-ttu-id="ce270-269">wsa10:InvalidAddressingHeader</span><span class="sxs-lookup"><span data-stu-id="ce270-269">wsa10:InvalidAddressingHeader</span></span>|<span data-ttu-id="ce270-270">Duplicar `wsa:To`, `wsa:ReplyTo`, `wsa:From` ou `wsa:MessageID`.</span><span class="sxs-lookup"><span data-stu-id="ce270-270">Duplicate `wsa:To`, `wsa:ReplyTo`, `wsa:From` or `wsa:MessageID`.</span></span> <span data-ttu-id="ce270-271">Duplicar `wsa:RelatesTo` com o mesmo `RelationshipType`.</span><span class="sxs-lookup"><span data-stu-id="ce270-271">Duplicate `wsa:RelatesTo` with the same `RelationshipType`.</span></span>|  
|<span data-ttu-id="ce270-272">wsa10:MessageAddressingHeaderRequired</span><span class="sxs-lookup"><span data-stu-id="ce270-272">wsa10:MessageAddressingHeaderRequired</span></span>|<span data-ttu-id="ce270-273">O cabeçalho de endereçamento necessário está ausente.</span><span class="sxs-lookup"><span data-stu-id="ce270-273">The required Addressing header is missing.</span></span>|  
|<span data-ttu-id="ce270-274">wsa10:DestinationUnreachable</span><span class="sxs-lookup"><span data-stu-id="ce270-274">wsa10:DestinationUnreachable</span></span>|<span data-ttu-id="ce270-275">A mensagem chegou com um `ReplyTo` , que é diferente do endereço de resposta estabelecido para este canal.</span><span class="sxs-lookup"><span data-stu-id="ce270-275">The message arrived with a `ReplyTo` that is different from the reply address established for this channel.</span></span> <span data-ttu-id="ce270-276">Não há nenhum ponto de extremidade escutando no endereço especificado no cabeçalho de para.</span><span class="sxs-lookup"><span data-stu-id="ce270-276">There is no endpoint listening at the address specified in the To header.</span></span>|  
|<span data-ttu-id="ce270-277">wsa10:ActionNotSupported</span><span class="sxs-lookup"><span data-stu-id="ce270-277">wsa10:ActionNotSupported</span></span>|<span data-ttu-id="ce270-278">Uma ação especificada no `Action` cabeçalho não é reconhecido pelo canais de infraestrutura ou distribuidor associado com o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="ce270-278">An action specified in the `Action` header is not recognized by the infrastructure channels or dispatcher associated with the endpoint.</span></span>|  
|<span data-ttu-id="ce270-279">wsa10:EndpointUnavailable</span><span class="sxs-lookup"><span data-stu-id="ce270-279">wsa10:EndpointUnavailable</span></span>|<span data-ttu-id="ce270-280">O canal de RM envia essa falha, que indica o ponto de extremidade não processará a sequência com base na análise do `CreateSequence` cabeçalhos de endereçamento da mensagem.</span><span class="sxs-lookup"><span data-stu-id="ce270-280">The RM channel sends this fault back, indicating the endpoint will not process the sequence based upon examination of the `CreateSequence` message’s addressing headers.</span></span>|  
  
 <span data-ttu-id="ce270-281">Mapas de código nas tabelas anteriores para `FaultCode` em SOAP 1.1 e `SubCode` (com o código = remetente) em SOAP 1.2.</span><span class="sxs-lookup"><span data-stu-id="ce270-281">Code in the preceding tables maps to `FaultCode` in SOAP 1.1 and `SubCode` (with Code=Sender) in SOAP 1.2.</span></span>  
  
### <a name="wsdl-11-binding-and-ws-policy-assertions"></a><span data-ttu-id="ce270-282">WSDL 1.1 asserções de WS-Policy e associação</span><span class="sxs-lookup"><span data-stu-id="ce270-282">WSDL 1.1 Binding and WS-Policy Assertions</span></span>  
  
#### <a name="indicating-use-of-ws-addressing"></a><span data-ttu-id="ce270-283">Indicam o uso de WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="ce270-283">Indicating Use of WS-Addressing</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] <span data-ttu-id="ce270-284">usa declarações de política para indicar o suporte de ponto de extremidade para uma versão específica do WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="ce270-284">uses policy assertions to indicate endpoint support for a particular WS-Addressing version.</span></span>  
  
 <span data-ttu-id="ce270-285">A declaração de política a seguir tem assunto de política do ponto de extremidade [WS-PA] e indica as mensagens enviadas e recebidas do ponto de extremidade devem usar 08/2004 do WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="ce270-285">The following policy assertion has Endpoint Policy Subject [WS-PA] and indicates messages sent and received from the endpoint must use WS-Addressing 2004/08.</span></span>  
  
```xml  
<wsap:UsingAddressing />  
```  
  
 <span data-ttu-id="ce270-286">Esta declaração de política de aumenta a especificação de 2004 do WS-Addressing/08.</span><span class="sxs-lookup"><span data-stu-id="ce270-286">This policy assertion augments the WS-Addressing 2004/08 specification.</span></span>  
  
 <span data-ttu-id="ce270-287">A seguinte declaração de política indica que as mensagens enviadas/recebidas deve usar WS-Addressing 1.0.</span><span class="sxs-lookup"><span data-stu-id="ce270-287">The following policy assertion this indicates that messages sent/received must use WS-Addressing 1.0.</span></span>  
  
```xml
<wsam:Addressing/>   
```  
  
 <span data-ttu-id="ce270-288">A seguinte declaração de política tem um assunto de política do ponto de extremidade [WS-PA] e indica se as mensagens enviadas e recebidas do ponto de extremidade devem usar 08/2004 do WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="ce270-288">The following policy assertion has an Endpoint Policy Subject [WS-PA] and indicates that messages sent and received from the endpoint must use WS-Addressing 2004/08.</span></span>  
  
```xml  
<wsaw10:UsingAddressing />  
```  
  
 <span data-ttu-id="ce270-289">O `wsaw10:UsingAddressing` elemento é obtido do [WS-Addressing-WSDL] e é usado no contexto do WS-Policy em conformidade com essa especificação, seção 3.1.2.</span><span class="sxs-lookup"><span data-stu-id="ce270-289">The `wsaw10:UsingAddressing` element is borrowed from [WS-Addressing-WSDL] and is used in the context of WS-Policy in compliance with that specification, section 3.1.2.</span></span>  
  
 <span data-ttu-id="ce270-290">Uso de endereçamento não altera a semântica da WSDL 1.1, SOAP 1.1 e SOAP 1.2 HTTP associações.</span><span class="sxs-lookup"><span data-stu-id="ce270-290">Use of Addressing does not alter the semantics of WSDL 1.1, SOAP 1.1, and SOAP 1.2 HTTP Bindings.</span></span> <span data-ttu-id="ce270-291">Por exemplo, se uma resposta é esperada para uma solicitação que é enviada para um ponto de extremidade que usa a associação HTTP de 1. x endereçamento e WSDL SOAP, a resposta deve ser enviada usando-se a resposta HTTP.</span><span class="sxs-lookup"><span data-stu-id="ce270-291">For example, if a reply is expected to a request that is sent to an endpoint that uses Addressing and WSDL SOAP 1.x HTTP binding, the reply must be sent by using the HTTP response.</span></span>  
  
 <span data-ttu-id="ce270-292">Para respostas enviadas pela resposta http, a declaração de WS-AM é:</span><span class="sxs-lookup"><span data-stu-id="ce270-292">For replies sent over the http response, the WS-AM assertion is:</span></span>  
  
```xml  
<wsam:AnonymousResponses/>  
```  
  
 <span data-ttu-id="ce270-293">A declaração de política concluída pode ter esta aparência:</span><span class="sxs-lookup"><span data-stu-id="ce270-293">The complete policy assertion might look like this:</span></span>  
  
```xml  
<wsam:Addressing>  
    <wsp:Policy>  
        <wsam:AnonymousResponses />   
    </wsp:Policy>  
</wsam:Addressing>  
```  
  
 <span data-ttu-id="ce270-294">No entanto, há padrões de troca de mensagem se beneficiar de duas conexões de HTTP inverso independentes estabelecidas entre o solicitante e o respondedor, por exemplo, unidirecionais mensagens enviadas pelo respondente.</span><span class="sxs-lookup"><span data-stu-id="ce270-294">However, there are message exchange patterns that benefit from having two independent converse HTTP connections established between the requester and the responder, for example, unsolicited one-way messages sent by the responder.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] <span data-ttu-id="ce270-295">oferece um recurso pelo qual dois canais de transporte subjacente podem formar um canal Duplex compostos, onde um canal é usado para mensagens de entrada e a outra é usada para mensagens de saída.</span><span class="sxs-lookup"><span data-stu-id="ce270-295">offers a feature by which two underlying transport channels can form a Composite Duplex channel, where one channel is used for input messages and the other is used for output messages.</span></span> <span data-ttu-id="ce270-296">No caso de transporte HTTP, Duplex compostos fornece duas conexões de HTTP inverso.</span><span class="sxs-lookup"><span data-stu-id="ce270-296">In the case of the HTTP Transport, Composite Duplex provides two converse HTTP connections.</span></span> <span data-ttu-id="ce270-297">O solicitante usa uma conexão para enviar mensagens para o respondente e o respondedor usa o outro para enviar mensagens de volta para o solicitante.</span><span class="sxs-lookup"><span data-stu-id="ce270-297">The requester uses one connection to send messages to the responder, and the responder uses the other to send messages back to the requester.</span></span>  
  
 <span data-ttu-id="ce270-298">Para respostas enviadas por solicitações de http separados, a declaração de ws-am é</span><span class="sxs-lookup"><span data-stu-id="ce270-298">For replies sent over separate http requests, the ws-am assertion is</span></span>  
  
```xml  
<wsam:NonAnonymousResponses/>  
```  
  
 <span data-ttu-id="ce270-299">A declaração de política concluída pode ter esta aparência:</span><span class="sxs-lookup"><span data-stu-id="ce270-299">The complete policy assertion might look like this:</span></span>  
  
```xml  
<wsam:Addressing>  
    <wsp:Policy>  
      <wsam:NonAnonymousResponses />   
   </wsp:Policy>  
  </wsam:Addressing>  
```  
  
 <span data-ttu-id="ce270-300">Use o seguinte declaração que tem o ponto de extremidade de política de entidade [WS-PA] nos pontos de extremidade usam associações de HTTP do WSDL 1.1 SOAP 1. x requer duas conexões de HTTP inverso separado a ser usado para mensagens que fluem do solicitante Respondente e Respondente ao solicitante, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="ce270-300">Use of the following assertion that has Endpoint Policy Subject [WS-PA] on endpoints that use WSDL 1.1 SOAP 1.x HTTP bindings requires two separate converse HTTP connections to be used for messages flowing from requester to responder and responder to requester, respectively.</span></span>  
  
```xml  
<cdp:CompositeDuplex/>  
```  
  
 <span data-ttu-id="ce270-301">A instrução anterior gera os seguintes requisitos `wsa:ReplyTo` cabeçalho para mensagens de solicitação:</span><span class="sxs-lookup"><span data-stu-id="ce270-301">The previous statement leads to the following requirements on the `wsa:ReplyTo` header for request messages:</span></span>  
  
-   <span data-ttu-id="ce270-302">R3514: Solicitar mensagens enviadas para um ponto de extremidade devem ter um `ReplyTo` cabeçalho com o `[address]` propriedade não é igual a "http://www.w3.org/2005/08/addressing/anonymous" se o ponto de extremidade usa uma associação de 1. x HTTP WSDL 1.1 SOAP e tem uma alternativa de política com um `wsap10:UsingAddressing` ou `wsap:UsingAddressing` associado a asserção `cdp:CompositeDuplex` anexado.</span><span class="sxs-lookup"><span data-stu-id="ce270-302">R3514: Request messages sent to an endpoint must have a `ReplyTo` header with the `[address]` property not equal to "http://www.w3.org/2005/08/addressing/anonymous" if the endpoint uses a WSDL 1.1 SOAP 1.x HTTP binding and has a policy alternative with a `wsap10:UsingAddressing` or `wsap:UsingAddressing` assertion coupled with `cdp:CompositeDuplex` attached.</span></span>  
  
-   <span data-ttu-id="ce270-303">R3515: Solicitar mensagens enviadas para um ponto de extremidade devem ter um `ReplyTo` cabeçalho com o `[address]` propriedade igual a "http://www.w3.org/2005/08/addressing/anonymous" ou não tem um `ReplyTo` cabeçalho todos, se o ponto de extremidade usa um WSDL 1.1 SOAP HTTP de 1. x associação e tem uma alternativa de política com `wsap10:UsingAddressing` asserção e nenhum `cdp:CompositeDuplex` asserção anexada.</span><span class="sxs-lookup"><span data-stu-id="ce270-303">R3515: Request messages sent to an endpoint must have a `ReplyTo` header with the `[address]` property equal to "http://www.w3.org/2005/08/addressing/anonymous", or not have a `ReplyTo` header at all, if the endpoint uses a WSDL 1.1 SOAP 1.x HTTP binding and has a policy alternative with `wsap10:UsingAddressing` assertion and no `cdp:CompositeDuplex` assertion attached.</span></span>  
  
-   <span data-ttu-id="ce270-304">R3516: Solicitar mensagens enviadas para um ponto de extremidade devem ter um `ReplyTo` cabeçalho com um `[address]` propriedade igual a "http://www.w3.org/2005/08/addressing/anonymous" se o ponto de extremidade usa uma associação de 1. x HTTP WSDL 1.1 SOAP e tem uma alternativa de política com `wsap:UsingAddressing` asserção e nenhum `cdp:CompositeDuplex` asserção anexada.</span><span class="sxs-lookup"><span data-stu-id="ce270-304">R3516: Request messages sent to an endpoint must have a `ReplyTo` header with an `[address]` property equal to "http://www.w3.org/2005/08/addressing/anonymous" if the endpoint uses a WSDL 1.1 SOAP 1.x HTTP binding and has a policy alternative with `wsap:UsingAddressing` assertion and no `cdp:CompositeDuplex` assertion attached.</span></span>  
  
 <span data-ttu-id="ce270-305">A especificação WS-addressing WSDL tenta descrever associações de protocolo semelhante com a introdução de um elemento `<wsaw:Anonymous/>` com três valores textuais (obrigatórios, opcionais e proibidos) para indicar requisitos sobre o `wsa:ReplyTo` cabeçalho (seção 3.2).</span><span class="sxs-lookup"><span data-stu-id="ce270-305">The WS-addressing WSDL specification attempts to describe similar protocol bindings by introducing an element `<wsaw:Anonymous/>` with three textual values (required, optional, and prohibited) to indicate requirements on the `wsa:ReplyTo` header (section 3.2).</span></span> <span data-ttu-id="ce270-306">Infelizmente, essa definição de elemento não é particularmente útil como uma declaração no contexto do WS-Policy, porque ele requer extensões específicas de domínio para dar suporte a interseção de alternativas usando esse elemento como uma declaração.</span><span class="sxs-lookup"><span data-stu-id="ce270-306">Unfortunately, such element definition is not particularly usable as an assertion in the context of WS-Policy, because it requires domain-specific extensions to support the intersection of alternatives using such an element as an assertion.</span></span> <span data-ttu-id="ce270-307">Essa definição de elemento também indica o valor da `ReplyTo` cabeçalho em vez do comportamento de ponto de extremidade na conexão, que é específico para o transporte HTTP.</span><span class="sxs-lookup"><span data-stu-id="ce270-307">Such element definition also indicates the value of the `ReplyTo` header as opposed to the endpoint behavior on the wire, which makes it specific to HTTP transport.</span></span>  
  
#### <a name="action-definition"></a><span data-ttu-id="ce270-308">Definição da ação</span><span class="sxs-lookup"><span data-stu-id="ce270-308">Action Definition</span></span>  
 <span data-ttu-id="ce270-309">08/2004 do WS-Addressing define uma `wsa:Action` de atributo para o `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]` elementos.</span><span class="sxs-lookup"><span data-stu-id="ce270-309">WS-Addressing 2004/08 defines a `wsa:Action` attribute for the `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]` elements.</span></span> <span data-ttu-id="ce270-310">WS-Addressing 1.0 WSDL associação (WS-ADDR10-WSDL) define um atributo semelhante, `wsaw10:Action`.</span><span class="sxs-lookup"><span data-stu-id="ce270-310">WS-Addressing 1.0 WSDL Binding (WS-ADDR10-WSDL) defines a similar attribute, `wsaw10:Action`.</span></span>  
  
 <span data-ttu-id="ce270-311">A única diferença entre os dois é a semântica de padrão de ação padrão descrita na seção 3.3.2 do WS-ADDR e 4.4.4 do WS-ADDR10-WSDL, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="ce270-311">The only difference between the two is the default Action pattern semantics described in section 3.3.2 of WS-ADDR and section 4.4.4 of WS-ADDR10-WSDL, respectively.</span></span>  
  
 <span data-ttu-id="ce270-312">É razoável ter dois pontos de extremidade que compartilham o mesmo `portType` (ou um contrato, na [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] terminologia), mas com diferentes versões do WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="ce270-312">It is a reasonable to have two endpoints that share the same `portType` (or contract, in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] terminology) but using different versions of WS-Addressing.</span></span> <span data-ttu-id="ce270-313">Mas, considerando que a ação é definida pelo `portType` e não devem alterar entre os pontos de extremidade que implementam o `portType`, torna impossível dar suporte a ambos os padrões de ação padrão.</span><span class="sxs-lookup"><span data-stu-id="ce270-313">But given that Action is defined by the `portType` and should not change across the endpoints that implement the `portType`, it becomes impossible to support both default action patterns.</span></span>  
  
 <span data-ttu-id="ce270-314">Para resolver esse controvérsia incrível, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] oferece suporte a uma única versão do `Action` atributo.</span><span class="sxs-lookup"><span data-stu-id="ce270-314">To resolve this controversy, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] supports a single version of the `Action` attribute.</span></span>  
  
 <span data-ttu-id="ce270-315">B3521: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usa o `wsaw10:Action` atributo no `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]` elementos conforme definido em WS-ADDR10-WSDL para determinar o `Action` URI para as mensagens correspondentes independentemente da versão do WS-Addressing usado pelo ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="ce270-315">B3521: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uses the `wsaw10:Action` attribute on `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]` elements as defined in WS-ADDR10-WSDL to determine the `Action` URI for the corresponding messages irrespective of the WS-Addressing version used by the endpoint.</span></span>  
  
#### <a name="use-endpoint-reference-inside-wsdl-port"></a><span data-ttu-id="ce270-316">Use ponto de extremidade de referência interna WSDL porta</span><span class="sxs-lookup"><span data-stu-id="ce270-316">Use Endpoint Reference Inside WSDL Port</span></span>  
 <span data-ttu-id="ce270-317">WS-ADDR10-WSDL seção 4.1 estende o `wsdl:port` elemento para incluir o `<wsa10:EndpointReference…/>` elemento filho para descrever o ponto de extremidade em termos de WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="ce270-317">WS-ADDR10-WSDL section 4.1 extends the `wsdl:port` element to include the `<wsa10:EndpointReference…/>` child element to describe the endpoint in WS-Addressing terms.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="ce270-318">expande esse utilitário em 08/2004 do WS-Addressing, permitindo que `<wsa:EndpointReference…/>` apareça como um elemento filho do `wsdl:port`.</span><span class="sxs-lookup"><span data-stu-id="ce270-318"> expands this utility on WS-Addressing 2004/08, allowing `<wsa:EndpointReference…/>` to appear as a child element of `wsdl:port`.</span></span>  
  
-   <span data-ttu-id="ce270-319">R3531: Se um ponto de extremidade tem uma alternativa de política anexada com um `<wsaw10:UsingAddressing/>` declaração de política correspondente `wsdl:port` elemento pode conter um elemento filho `<wsa10:EndpointReference …/>`.</span><span class="sxs-lookup"><span data-stu-id="ce270-319">R3531: If an endpoint has an attached policy alternative with a `<wsaw10:UsingAddressing/>` policy assertion, the corresponding `wsdl:port` element can contain a child element `<wsa10:EndpointReference …/>`.</span></span>  
  
-   <span data-ttu-id="ce270-320">R3532: Se um `wsdl:port` contém um elemento filho `<wsa10:EndpointReference …/>`, o `wsa10:EndpointReference/wsa10:Address` valor do elemento filho deve corresponder ao valor da `@address` atributo do irmão `wsdl:port` / `wsdl:location` elemento.</span><span class="sxs-lookup"><span data-stu-id="ce270-320">R3532: If a `wsdl:port` contains a child element `<wsa10:EndpointReference …/>`, the `wsa10:EndpointReference/wsa10:Address` child element value must match the value of the `@address` attribute of the sibling `wsdl:port`/`wsdl:location` element.</span></span>  
  
-   <span data-ttu-id="ce270-321">R3533: Se um ponto de extremidade tem uma alternativa de política anexada com `<wsap:UsingAddressing/>` declaração de política correspondente `wsdl:port` elemento pode conter um elemento filho `<wsa:EndpointReference …/>`.</span><span class="sxs-lookup"><span data-stu-id="ce270-321">R3533: If an endpoint has an attached policy alternative with `<wsap:UsingAddressing/>` policy assertion, the corresponding `wsdl:port` element can contain a child element `<wsa:EndpointReference …/>`.</span></span>  
  
-   <span data-ttu-id="ce270-322">R3534: Se um `wsdl:port` contém um elemento filho `<wsa:EndpointReference …/>`, o `wsa:EndpointReference/wsa:Address` valor do elemento filho deve corresponder ao valor da `@address` atributo do irmão `wsdl:port` / `wsdl:location` elemento.</span><span class="sxs-lookup"><span data-stu-id="ce270-322">R3534: If a `wsdl:port` contains a child element `<wsa:EndpointReference …/>`, the `wsa:EndpointReference/wsa:Address` child element value must match the value of the `@address` attribute of the sibling `wsdl:port`/`wsdl:location` element.</span></span>  
  
### <a name="composition-with-ws-security"></a><span data-ttu-id="ce270-323">Composição com WS-Security</span><span class="sxs-lookup"><span data-stu-id="ce270-323">Composition with WS-Security</span></span>  
 <span data-ttu-id="ce270-324">De acordo com a seções de consideração de segurança em WS-ADDR e WS-ADDR10, todos os cabeçalhos de mensagem de endereçamento são recomendados sejam assinados com o corpo da mensagem para associá-los juntos.</span><span class="sxs-lookup"><span data-stu-id="ce270-324">According to security consideration sections in WS-ADDR and WS-ADDR10, all addressing message headers are recommended to be signed together with the message body to bind them together.</span></span>  
  
 <span data-ttu-id="ce270-325">Quando WS-Security é usado para proteção de integridade de mensagem, a mensagem WS-Addressing cabeçalhos, bem como cabeçalhos resultaram de parâmetros de referência ou propriedades (ou ambos) deve ser assinada junto com o corpo da mensagem.</span><span class="sxs-lookup"><span data-stu-id="ce270-325">When WS-Security is used for message integrity protection, WS-Addressing message headers as well as headers resulted from reference parameters or properties (or both) must be signed together with the body of the message.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="ce270-326">Exemplos</span><span class="sxs-lookup"><span data-stu-id="ce270-326">Examples</span></span>  
  
#### <a name="one-way-message"></a><span data-ttu-id="ce270-327">Mensagem unidirecional</span><span class="sxs-lookup"><span data-stu-id="ce270-327">One-Way Message</span></span>  
 <span data-ttu-id="ce270-328">Nesse cenário, o remetente envia uma mensagem unidirecional para o receptor.</span><span class="sxs-lookup"><span data-stu-id="ce270-328">In this scenario, the sender sends a one-way message to the receiver.</span></span> <span data-ttu-id="ce270-329">1.0 W3C WS-Addressing, HTTP 1.1 e SOAP 1.2 são usados.</span><span class="sxs-lookup"><span data-stu-id="ce270-329">SOAP 1.2, HTTP 1.1, and W3C WS-Addressing 1.0 are used.</span></span>  
  
 <span data-ttu-id="ce270-330">A estrutura de mensagens de solicitação: Os cabeçalhos de mensagem incluem `wsa10:To` e `wsa10:Action` elementos.</span><span class="sxs-lookup"><span data-stu-id="ce270-330">The Request Message Structure: The message headers include `wsa10:To` and `wsa10:Action` elements.</span></span> <span data-ttu-id="ce270-331">O corpo da mensagem inclui um determinado `<app:Ping>` elemento do namespace do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ce270-331">The message body includes a specific `<app:Ping>` element from the application namespace.</span></span>  
  
 <span data-ttu-id="ce270-332">Cabeçalhos HTTP: O destino na POSTAGEM coincide com o URI no `wsa10:To` elemento.</span><span class="sxs-lookup"><span data-stu-id="ce270-332">HTTP Headers: The destination in POST matches the URI in the `wsa10:To` element.</span></span>  
  
 <span data-ttu-id="ce270-333">O cabeçalho Content-Type tem o valor de `application/soap+xml` conforme solicitado pelo SOAP 1.2.</span><span class="sxs-lookup"><span data-stu-id="ce270-333">The Content-Type header has the value of `application/soap+xml` as required by SOAP 1.2.</span></span> <span data-ttu-id="ce270-334">Parâmetros `charset` e `action` são incluídos.</span><span class="sxs-lookup"><span data-stu-id="ce270-334">Parameters `charset` and `action` are included.</span></span> <span data-ttu-id="ce270-335">O `action` parâmetro do cabeçalho Content-Type corresponde ao valor do `wsa10:Action` cabeçalho da mensagem.</span><span class="sxs-lookup"><span data-stu-id="ce270-335">The `action` parameter of the Content-Type header matches the value of the `wsa10:Action` message header.</span></span>  
  
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
  
 <span data-ttu-id="ce270-336">O receptor responde com uma resposta HTTP vazia e o status de 202.</span><span class="sxs-lookup"><span data-stu-id="ce270-336">The receiver responds with an empty HTTP response and status 202.</span></span> <span data-ttu-id="ce270-337">Um exemplo de resposta HTTP:</span><span class="sxs-lookup"><span data-stu-id="ce270-337">An example of the HTTP response:</span></span>  
  
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
  
## <a name="soap-message-transmission-optimization-mechanism"></a><span data-ttu-id="ce270-338">Mecanismo de otimização de transmissão de mensagem SOAP</span><span class="sxs-lookup"><span data-stu-id="ce270-338">SOAP Message Transmission Optimization Mechanism</span></span>  
 <span data-ttu-id="ce270-339">Esta seção descreve o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] detalhes de implementação para o HTTP SOAP MTOM.</span><span class="sxs-lookup"><span data-stu-id="ce270-339">This section describes the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] implementation details for the HTTP SOAP MTOM.</span></span> <span data-ttu-id="ce270-340">Tecnologia MTOM é o mecanismo de codificação de mensagem SOAP da mesma classe como codificação tradicional de texto/XML ou [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] codificação binária.</span><span class="sxs-lookup"><span data-stu-id="ce270-340">MTOM technology is SOAP message encoding mechanism of the same class as traditional text/XML encoding or [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Binary encoding.</span></span> <span data-ttu-id="ce270-341">MTOM inclui o seguinte:</span><span class="sxs-lookup"><span data-stu-id="ce270-341">MTOM includes the following:</span></span>  
  
-   <span data-ttu-id="ce270-342">Um mecanismo de empacotamento descrito pelo [XOP] e a codificação XML que otimiza os itens de informações XML que contém dados binários codificados na base64 em partes separadas de binários.</span><span class="sxs-lookup"><span data-stu-id="ce270-342">An XML encoding and packaging mechanism described by [XOP] that optimizes XML information items containing base64-encoded binary data into separate binary parts.</span></span>  
  
-   <span data-ttu-id="ce270-343">Um encapsulamento MIME do pacote XOP que serializa o Infoset XML e cada parte binária do pacote XOP em uma parte MIME separada.</span><span class="sxs-lookup"><span data-stu-id="ce270-343">A MIME encapsulation of the XOP package that serializes the XML Infoset and each binary part of the XOP package into a separate MIME part.</span></span>  
  
-   <span data-ttu-id="ce270-344">Uma codificação de MIME XOP aplicada ao SOAP Envelope de 1. x.</span><span class="sxs-lookup"><span data-stu-id="ce270-344">A MIME XOP encoding applied to SOAP 1.x Envelope.</span></span>  
  
-   <span data-ttu-id="ce270-345">Um HTTP associação de transporte.</span><span class="sxs-lookup"><span data-stu-id="ce270-345">An HTTP transport binding.</span></span>  
  
 <span data-ttu-id="ce270-346">É possível usar MTOM com transportes não HTTP com [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ce270-346">It is possible to use MTOM with non-HTTP transports with [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span> <span data-ttu-id="ce270-347">No entanto, neste tópico nos concentraremos no HTTP.</span><span class="sxs-lookup"><span data-stu-id="ce270-347">However, in this topic we will focus on HTTP.</span></span>  
  
 <span data-ttu-id="ce270-348">O formato MTOM aproveita um grande conjunto de especificações que abrangem MTOM em si, XOP e MIME.</span><span class="sxs-lookup"><span data-stu-id="ce270-348">The MTOM format leverages a large set of specifications covering MTOM itself, XOP, and MIME.</span></span> <span data-ttu-id="ce270-349">Modularidade desse conjunto de especificação dificulta um pouco reconstruir os requisitos exatos na semântica de formato e o processamento.</span><span class="sxs-lookup"><span data-stu-id="ce270-349">Modularity of this specification set makes it somewhat difficult to reconstruct exact requirements on the format and processing semantics.</span></span> <span data-ttu-id="ce270-350">Esta seção descreve os requisitos de processamento e o formato para a associação HTTP MTOM.</span><span class="sxs-lookup"><span data-stu-id="ce270-350">This section describes the format and processing requirements for MTOM HTTP binding.</span></span>  
  
### <a name="mtom-message-encoding"></a><span data-ttu-id="ce270-351">Codificação de mensagem MTOM</span><span class="sxs-lookup"><span data-stu-id="ce270-351">MTOM Message Encoding</span></span>  
  
#### <a name="generating-mtom-messages"></a><span data-ttu-id="ce270-352">Gerando mensagens MTOM</span><span class="sxs-lookup"><span data-stu-id="ce270-352">Generating MTOM messages</span></span>  
 <span data-ttu-id="ce270-353">A seção 3.1 [XOP] descreve o processo de codificação XML com itens de informações de elemento que contêm valores de base64 em um pacote XOP abstrata definido.</span><span class="sxs-lookup"><span data-stu-id="ce270-353">The [XOP] section 3.1 describes the process of encoding XML with element information items that contain base64 values into an abstractly defined XOP package.</span></span>  
  
 <span data-ttu-id="ce270-354">A sequência de etapas a seguir descreve o processo de codificação de MTOM específico:</span><span class="sxs-lookup"><span data-stu-id="ce270-354">The following sequence of steps describes the MTOM-specific encoding process:</span></span>  
  
1.  <span data-ttu-id="ce270-355">Certifique-se de que o Envelope SOAP a ser decodificado não contém nenhum item de informação do elemento com um `[namespace name]` de "http://www.w3.org/2004/08/xop/include" e um `[local name]` de `Include`.</span><span class="sxs-lookup"><span data-stu-id="ce270-355">Ensure that the SOAP Envelope to be encoded contains no element information item with a `[namespace name]` of "http://www.w3.org/2004/08/xop/include" and a `[local name]` of `Include`.</span></span>  
  
2.  <span data-ttu-id="ce270-356">Crie um pacote vazio do MIME.</span><span class="sxs-lookup"><span data-stu-id="ce270-356">Create an empty MIME package.</span></span>  
  
3.  <span data-ttu-id="ce270-357">Identifica os itens de informações do elemento a ser otimizado em Infoset XML Original.</span><span class="sxs-lookup"><span data-stu-id="ce270-357">Identify within the Original XML Infoset the element information items to be optimized.</span></span> <span data-ttu-id="ce270-358">Para os itens deve ser otimizada, os caracteres que compõem o `[children]` as informações do elemento item deve ser na forma canônica de `xs:base64Binary` (consulte XSD-2, 3.2.16 base64Binary) e não deve conter nenhum caractere de espaço em branco anterior, embutido, ou Após o conteúdo não seja espaço em branco.</span><span class="sxs-lookup"><span data-stu-id="ce270-358">For the items to be optimized, the characters that make up the `[children]` of the element information item must be in the canonical form of `xs:base64Binary` (see XSD-2, 3.2.16 base64Binary) and must not contain any whitespace characters preceding, inline with, or following the non-whitespace content.</span></span>  
  
4.  <span data-ttu-id="ce270-359">Criar um Envelope SOAP XOP que é uma cópia do Envelope SOAP Original, mas com os filhos de cada informação do elemento item identificado na etapa anterior é substituída por um `xop:Include` item de informação do elemento construída da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="ce270-359">Create an XOP SOAP Envelope that is a copy of the Original SOAP Envelope, but with the children of each element information item identified in the previous step replaced by an `xop:Include` element information item constructed as follows:</span></span>  
  
    1.  <span data-ttu-id="ce270-360">Transforme os caracteres substituídos em dados binários processando-os como dados codificados na base64.</span><span class="sxs-lookup"><span data-stu-id="ce270-360">Transform the replaced characters into binary data by processing them as base64-encoded data.</span></span>  
  
    2.  <span data-ttu-id="ce270-361">Gere um valor de cabeçalho de Content-ID exclusivo que satisfaz os requisitos de R3133 e R3134.</span><span class="sxs-lookup"><span data-stu-id="ce270-361">Generate a unique Content-ID header value that satisfies requirements R3133 and R3134.</span></span>  
  
    3.  <span data-ttu-id="ce270-362">Gere um cabeçalho de codificação de transferência de conteúdo MIME com o valor binário.</span><span class="sxs-lookup"><span data-stu-id="ce270-362">Generate a Content-Transfer-Encoding MIME header with the value binary.</span></span>  
  
    4.  <span data-ttu-id="ce270-363">Se o item de informação do elemento que está sendo otimizado ([pai] recentemente inserido `xop:Include` item de informação do elemento) tem um `xmime:contentType` item de informação de atributo, gerar um cabeçalho de tipo de conteúdo MIME com o valor da `xmime:contentType` atributo.</span><span class="sxs-lookup"><span data-stu-id="ce270-363">If the element information item being optimized (the [parent] of the newly inserted `xop:Include` element information item) has an `xmime:contentType` attribute information item, generate a Content-Type MIME header with the value of the `xmime:contentType` attribute.</span></span>  
  
    5.  <span data-ttu-id="ce270-364">Gere uma nova parte MIME binária com conteúdo formado por dados binários decodificados dos caracteres substituídos processados como base64, o cabeçalho Content-ID do 4b, o cabeçalho de codificação de transferência de conteúdo de 4 núcleos, o cabeçalho Content-Type se gerado na etapa 4d.</span><span class="sxs-lookup"><span data-stu-id="ce270-364">Generate a new binary MIME part with content formed by binary data decoded from the replaced characters processed as base64, Content-ID header from 4b, Content- Transfer-Encoding header from 4c, Content-Type header if generated in step 4d.</span></span>  
  
    6.  <span data-ttu-id="ce270-365">Adicionar uma `href` de atributo para o `xop:Include` elemento com o valor de cid: uri derivado do valor do cabeçalho Content-ID gerado na etapa 4b.</span><span class="sxs-lookup"><span data-stu-id="ce270-365">Add an `href` attribute to the `xop:Include` element with the value cid: uri derived from Content-ID header value generated in step 4b.</span></span> <span data-ttu-id="ce270-366">Remover o delimitador "\<" e ">" caracteres, o restante da cadeia de caracteres e adicione o prefixo de URL-escape `cid:`.</span><span class="sxs-lookup"><span data-stu-id="ce270-366">Remove the enclosing "\<" and ">" characters, URL-escape the remaining string, and add the prefix `cid:`.</span></span> <span data-ttu-id="ce270-367">O conjunto mínimo de caracteres a seguir é necessário para ser substituídas por RFC1738 e RFC2396.</span><span class="sxs-lookup"><span data-stu-id="ce270-367">The following minimum character set is required to be escaped by RFC1738 and RFC2396.</span></span> <span data-ttu-id="ce270-368">Outros caracteres podem ser substituídos.</span><span class="sxs-lookup"><span data-stu-id="ce270-368">Other characters can be escaped.</span></span>  
  
        ```  
        Hexadecimal 00-1F , 7F, 20, "<" | ">" | "#" | "%" | <">  
        "{" | "}" | "|" | "\" | "^" | "[" | "]" | "`" | "~" | "^"  
        ```  
  
5.  <span data-ttu-id="ce270-369">Crie uma parte MIME raiz com o Envelope de SOAP XOP da etapa 4.</span><span class="sxs-lookup"><span data-stu-id="ce270-369">Create a root MIME part with the XOP SOAP Envelope from step 4.</span></span>  
  
6.  <span data-ttu-id="ce270-370">Grave os cabeçalhos HTTP, incluindo o cabeçalho de tipo de conteúdo HTTP.</span><span class="sxs-lookup"><span data-stu-id="ce270-370">Write the HTTP headers, including the HTTP Content-Type header.</span></span>  
  
7.  <span data-ttu-id="ce270-371">Grave o pacote MIME.</span><span class="sxs-lookup"><span data-stu-id="ce270-371">Write the MIME package.</span></span>  
  
#### <a name="processing-mtom-messages"></a><span data-ttu-id="ce270-372">Processando mensagens MTOM</span><span class="sxs-lookup"><span data-stu-id="ce270-372">Processing MTOM messages</span></span>  
 <span data-ttu-id="ce270-373">O processamento de um MTOM mensagem é o contrário exato do processo descrito na anterior "gerando MTOM mensagens" seção:</span><span class="sxs-lookup"><span data-stu-id="ce270-373">Processing of an MTOM message is the exact reverse of the process described in the preceding "Generating MTOM messages" section:</span></span>  
  
1.  <span data-ttu-id="ce270-374">Certifique-se de que a parte MIME raiz tem o tipo de conteúdo `application/xop+xml`.</span><span class="sxs-lookup"><span data-stu-id="ce270-374">Ensure the root MIME part has the Content-Type `application/xop+xml`.</span></span>  
  
2.  <span data-ttu-id="ce270-375">Construa um Envelope SOAP ao analisar a parte MIME do pacote como um documento XML raiz.</span><span class="sxs-lookup"><span data-stu-id="ce270-375">Construct a SOAP Envelope by parsing the root MIME part of the package as an XML document.</span></span> <span data-ttu-id="ce270-376">Codificação de caracteres é determinado pelo `charset` parâmetro do tipo de conteúdo da parte MIME raiz.</span><span class="sxs-lookup"><span data-stu-id="ce270-376">Character encoding is determined by the `charset` parameter of the Content-Type of the root MIME part.</span></span>  
  
3.  <span data-ttu-id="ce270-377">Para cada item de informação do elemento no Envelope SOAP construído, que tem, como o único membro de sua propriedade [filhos], um `xop:Include` item de informação do elemento:</span><span class="sxs-lookup"><span data-stu-id="ce270-377">For each element information item in the constructed SOAP Envelope, which has, as the sole member of its [children] property, an `xop:Include` element information item:</span></span>  
  
    1.  <span data-ttu-id="ce270-378">Remover o `cid:` prefixo e unescape todas as sequências de escape de URI (RFC 2396) no valor da `@href` atributo do `xop:Include` elemento.</span><span class="sxs-lookup"><span data-stu-id="ce270-378">Remove the `cid:` prefix and unescape all URI-escape sequences (RFC 2396) in the value of the `@href` attribute of the `xop:Include` element.</span></span> <span data-ttu-id="ce270-379">Coloque a cadeia de caracteres de resultado em "\<", ">".</span><span class="sxs-lookup"><span data-stu-id="ce270-379">Enclose the result string in "\<", ">".</span></span>  
  
    2.  <span data-ttu-id="ce270-380">Localize a parte MIME com o valor do cabeçalho Content-ID que corresponde à cadeia derivada na etapa 3a.</span><span class="sxs-lookup"><span data-stu-id="ce270-380">Locate the MIME part with the Content-ID header value that matches the string derived in step 3a.</span></span>  
  
    3.  <span data-ttu-id="ce270-381">Substitua o `xop:Include` item de informação do elemento que aparece no `children` propriedade de cada item com os itens de informações de caracteres que representam a codificação base64 canônico (consulte XSD-2, 3.2.16 base64Binary) do corpo da entidade da parte MIME identificado na etapa 3b (substitua efetivamente o `xop:Include` item de informação do elemento com os dados reconstruídos com a parte do pacote).</span><span class="sxs-lookup"><span data-stu-id="ce270-381">Replace the `xop:Include` element information item that appears in the `children` property of each item with the character information items that represent the canonical base64 encoding (see XSD-2, 3.2.16 base64Binary) of the entity body of the MIME part identified in step 3b (effectively replace the `xop:Include` element information item with the data reconstructed from the package part).</span></span>  
  
#### <a name="http-content-type-header"></a><span data-ttu-id="ce270-382">Cabeçalho de tipo de conteúdo HTTP</span><span class="sxs-lookup"><span data-stu-id="ce270-382">HTTP Content-Type Header</span></span>  
 <span data-ttu-id="ce270-383">A seguir está uma lista de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] esclarecimentos para o formato do cabeçalho HTTP conteúdo-tipo de uma mensagem MTOM codificado do SOAP 1. x derivado de requisitos indicados na especificação MTOM e derivados de MTOM e RFC 2387.</span><span class="sxs-lookup"><span data-stu-id="ce270-383">The following is a list of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] clarifications for the format of the HTTP Content-Type header of a SOAP 1.x MTOM-encoded message derived from requirements stated in the MTOM specification itself and are derived from MTOM and RFC 2387.</span></span>  
  
-   <span data-ttu-id="ce270-384">R4131: Um cabeçalho HTTP conteúdo-tipo deve ter o valor de diversas partes/relacionado (diferencia maiusculas de minúsculas) e seus parâmetros.</span><span class="sxs-lookup"><span data-stu-id="ce270-384">R4131: An HTTP Content-Type header must have the value of multipart/related (case-insensitive) and its parameters.</span></span> <span data-ttu-id="ce270-385">Nomes de parâmetros diferenciam maiusculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="ce270-385">Parameter names are case-insensitive.</span></span> <span data-ttu-id="ce270-386">Ordem do parâmetro não é significativa.</span><span class="sxs-lookup"><span data-stu-id="ce270-386">Parameter order is not significant.</span></span>  
  
-   <span data-ttu-id="ce270-387">A forma de Backus-Naur completo (BNF) do cabeçalho Content-Type para mensagens MIME é listado na RFC 2045, seção 5.1.</span><span class="sxs-lookup"><span data-stu-id="ce270-387">The full Backus-Naur Form (BNF) of the Content-Type header for MIME messages is listed in RFC 2045, section 5.1.</span></span>  
  
-   <span data-ttu-id="ce270-388">R4132: Um cabeçalho HTTP conteúdo-tipo deve ter um parâmetro de tipo com o valor `application/xop+xml` entre aspas duplas.</span><span class="sxs-lookup"><span data-stu-id="ce270-388">R4132: An HTTP Content-Type header must have a type parameter with the value `application/xop+xml` enclosed in double quotation marks.</span></span>  
  
 <span data-ttu-id="ce270-389">Embora o requisito para usar aspas duplas não seja explícito no RFC 2387, o texto observa que todo o tipo de mídia com diversas partes/relacionado que contêm parâmetros provavelmente reservada caracteres, como "@" or "/" e, portanto, precisam de aspas duplas.</span><span class="sxs-lookup"><span data-stu-id="ce270-389">While the requirement to use double quotation marks is not explicit in RFC 2387, the text observes that all of the multipart/related media type parameters most likely contain reserved characters like "@" or "/" and therefore need double quotation marks.</span></span>  
  
-   <span data-ttu-id="ce270-390">R4133: Um cabeçalho HTTP conteúdo-tipo deve ter um parâmetro de inicialização com o valor do cabeçalho Content-ID da parte MIME que contém o SOAP 1. x Envelope, entre aspas duplas.</span><span class="sxs-lookup"><span data-stu-id="ce270-390">R4133: An HTTP Content-Type header should have a start parameter with the value of the Content-ID header of the MIME part that contains the SOAP 1.x Envelope, enclosed in double quotation marks.</span></span> <span data-ttu-id="ce270-391">Se o parâmetro start for omitido, a primeira parte MIME deve conter o SOAP Envelope de 1. x.</span><span class="sxs-lookup"><span data-stu-id="ce270-391">If the start parameter is omitted, the first MIME part must contain the SOAP 1.x Envelope.</span></span>  
  
-   <span data-ttu-id="ce270-392">R4134: Um cabeçalho de tipo de conteúdo HTTP para uma mensagem SOAP 1.1 MTOM codificado deve incluir o parâmetro de informações de início com o valor de texto/xml, entre aspas duplas.</span><span class="sxs-lookup"><span data-stu-id="ce270-392">R4134: An HTTP Content-Type header for a SOAP 1.1 MTOM encoded message must include the start-info parameter with the value of text/xml, enclosed in double quotation marks.</span></span>  
  
-   <span data-ttu-id="ce270-393">R4135: Um cabeçalho de tipo de conteúdo HTTP para uma mensagem SOAP 1.2 MTOM codificado deve incluir o parâmetro de informações de início com o valor de `application/soap+xml`, entre aspas duplas.</span><span class="sxs-lookup"><span data-stu-id="ce270-393">R4135: An HTTP Content-Type header for a SOAP 1.2 MTOM-encoded message must include the start-info parameter with the value of `application/soap+xml`, enclosed in double quotation marks.</span></span>  
  
-   <span data-ttu-id="ce270-394">R4136: O cabeçalho de tipo de conteúdo HTTP para uma mensagem MTOM codificado do SOAP 1. x deve ter o parâmetro de limite com o valor (entre aspas duplas) que corresponde a limites MIME que BNF definido em RFC 2046, seção 5.1.1</span><span class="sxs-lookup"><span data-stu-id="ce270-394">R4136: HTTP Content-Type header for a SOAP 1.x MTOM-encoded message must have the boundary parameter with the value (enclosed in double quotation marks) that matches the MIME boundary BNF defined in RFC 2046, section 5.1.1</span></span>  
  
    ```  
    boundary := 0*69<bchars> bcharsnospace   
    bchars := bcharsnospace / " "   
    bcharsnospace :=    DIGIT / ALPHA / "'" / "(" / ")" / "+"   
                        / "_" / "," / "-" / "." / "/" / ":" / "=" / "?"  
    ```  
  
     <span data-ttu-id="ce270-395">Exemplos:</span><span class="sxs-lookup"><span data-stu-id="ce270-395">Examples:</span></span>  
  
     <span data-ttu-id="ce270-396">CORRIGIR</span><span class="sxs-lookup"><span data-stu-id="ce270-396">CORRECT</span></span>  
  
    ```  
    Content-Type: multipart/related; type="application/xop+xml";start=" <part0@tempuri.org>";boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1";start-info="text/xml"  
    ```  
  
     <span data-ttu-id="ce270-397">CORRIGIR</span><span class="sxs-lookup"><span data-stu-id="ce270-397">CORRECT</span></span>  
  
    ```  
    Content-Type: Multipart/Related; type="application/xop+xml";start-info="text/xml";boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1"  
    ```  
  
     <span data-ttu-id="ce270-398">INCORRECT</span><span class="sxs-lookup"><span data-stu-id="ce270-398">INCORRECT</span></span>  
  
    ```  
    Content-Type: Multipart/Related; type=application/xop+xml;start=" <part0@tempuri.org>";start-info="text/xml";boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1"   
    ```  
  
#### <a name="infoset-mime-part"></a><span data-ttu-id="ce270-399">Parte MIME de infoset</span><span class="sxs-lookup"><span data-stu-id="ce270-399">Infoset MIME Part</span></span>  
 <span data-ttu-id="ce270-400">O SOAP 1. x Envelope é encapsulado como parte do pacote XOP MIME raiz e é geralmente chamado de `infoset` parte.</span><span class="sxs-lookup"><span data-stu-id="ce270-400">The SOAP 1.x Envelope is encapsulated as a root part of the XOP MIME package and is often called the `infoset` part.</span></span>  
  
-   <span data-ttu-id="ce270-401">R4141: O SOAP 1. x Envelope deve ser encapsulado como parte do pacote XOP MIME, chamado raiz a `infoset` parte e referenciado de tipo de conteúdo HTTP.</span><span class="sxs-lookup"><span data-stu-id="ce270-401">R4141: The SOAP 1.x Envelope must be encapsulated as a root part of the XOP MIME package, called the `infoset` part and referenced from the HTTP Content-Type.</span></span>  
  
-   <span data-ttu-id="ce270-402">R4142: O SOAP `Infoset` parte deve incluir os seguintes cabeçalhos MIME: `Content-ID`, `Content-Transfer-Encoding`, e `Content-Type`.</span><span class="sxs-lookup"><span data-stu-id="ce270-402">R4142: The SOAP `Infoset` part must include the following MIME headers: `Content-ID`, `Content-Transfer-Encoding`, and `Content-Type`.</span></span>  
  
 <span data-ttu-id="ce270-403">O formato do cabeçalho Content-ID é definido por RFC 2045 como</span><span class="sxs-lookup"><span data-stu-id="ce270-403">The format of the Content-ID header is defined by RFC 2045 as</span></span>  
  
```  
"Content-ID" ":" msg-id  
```  
  
 <span data-ttu-id="ce270-404">onde `msg-id` é definido na RFC 2822 (que substitui o RFC 822, referenciada na RFC 2045) como:</span><span class="sxs-lookup"><span data-stu-id="ce270-404">where `msg-id` is defined in RFC 2822 (that supersedes RFC 822, referenced in RFC 2045) as:</span></span>  
  
```  
msg-id    =       [CFWS] "<" id-left "@" id-right ">" [CFWS]  
```  
  
 <span data-ttu-id="ce270-405">e é efetivamente um endereço de email incluído dentro de "\<" e ">".</span><span class="sxs-lookup"><span data-stu-id="ce270-405">and is effectively an email address enclosed within "\<" and  ">".</span></span> <span data-ttu-id="ce270-406">O `[CFWS]` prefixo e sufixo foram adicionadas no RFC 2822 para transportar comentários e não deve ser usados para preservar a interoperabilidade.</span><span class="sxs-lookup"><span data-stu-id="ce270-406">The `[CFWS]` prefix and suffix were added in RFC 2822 to carry comments and should not be used to preserve interoperability.</span></span>  
  
 <span data-ttu-id="ce270-407">R4143: O valor do cabeçalho Content-ID para a parte MIME Infoset deve seguir `msg-id` produção da RFC 2822 com o `[CFWS]` partes de prefixo e sufixo omitidos.</span><span class="sxs-lookup"><span data-stu-id="ce270-407">R4143: The value of the Content-ID header for the Infoset MIME part must follow `msg-id` production from RFC 2822 with the `[CFWS]` prefix and suffix parts omitted.</span></span>  
  
 <span data-ttu-id="ce270-408">Um número de implementações de MIME relaxada requisitos para o valor entre "\<" e ">" deve ser um endereço de email e usado `absoluteURI` entre "\<", ">" Além do endereço de email.</span><span class="sxs-lookup"><span data-stu-id="ce270-408">A number of MIME implementations relaxed requirements for the value enclosed within "\<" and ">" to be an email address and used `absoluteURI` enclosed in "\<" , ">" in addition to the email address.</span></span> <span data-ttu-id="ce270-409">Esta versão do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usa valores de cabeçalho MIME Content-ID do formulário:</span><span class="sxs-lookup"><span data-stu-id="ce270-409">This version of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uses values of the Content-ID MIME header of the form:</span></span>  
  
```  
Content-ID: <http://tempuri.org/0>   
```  
  
 <span data-ttu-id="ce270-410">R4144: Processadores MTOM devem aceitar valores de cabeçalho de Content-ID que correspondem reduzidas a seguir `msg-id`.</span><span class="sxs-lookup"><span data-stu-id="ce270-410">R4144: MTOM processors should accept Content-ID header values that match the following relaxed `msg-id`.</span></span>  
  
```  
msg-id-relaxed =     [CFWS] "<" (absoluteURI | mail-address) ">" [CFWS]  
mail-address   =     id-left "@" id-right  
```  
  
 <span data-ttu-id="ce270-411">MIME (RFC 2045) fornece o cabeçalho de codificação de transferência de conteúdo para comunicar-se a codificação do conteúdo da parte MIME.</span><span class="sxs-lookup"><span data-stu-id="ce270-411">MIME (RFC 2045) provides the Content-Transfer-Encoding header to communicate encoding of the content of the MIME part.</span></span> <span data-ttu-id="ce270-412">O padrão definido para codificação de transferência de conteúdo é 7-bits, que não é adequado para a maioria das mensagens SOAP, portanto, o cabeçalho de codificação de transferência de conteúdo é necessária para obter melhor interoperabilidade:</span><span class="sxs-lookup"><span data-stu-id="ce270-412">The default defined for Content-Transfer-Encoding is 7-bit, which is not suitable for most SOAP messages, so the Content-Transfer-Encoding header is needed for greater interoperability:</span></span>  
  
-   <span data-ttu-id="ce270-413">R4145: A parte de SOAP Infoset deve conter o cabeçalho de codificação de transferência de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="ce270-413">R4145: The SOAP Infoset part must contain the Content-Transfer-Encoding header.</span></span>  
  
-   <span data-ttu-id="ce270-414">R4146: Se a codificação de caracteres de Envelope SOAP é UTF-8, o valor do cabeçalho de codificação de transferência de conteúdo deve ser 8 bits.</span><span class="sxs-lookup"><span data-stu-id="ce270-414">R4146: If the SOAP Envelope character encoding is UTF-8, the value of the Content-Transfer-Encoding header must be 8-bit.</span></span>  
  
-   <span data-ttu-id="ce270-415">R4147: Se a codificação de caracteres de Envelope SOAP é UTF-16, o valor do cabeçalho de codificação de transferência de conteúdo deve ser binário.</span><span class="sxs-lookup"><span data-stu-id="ce270-415">R4147: If the SOAP Envelope character encoding is UTF-16, the value of the Content-Transfer-Encoding header must be binary.</span></span>  
  
-   <span data-ttu-id="ce270-416">[XOP] seção 5, de acordo com</span><span class="sxs-lookup"><span data-stu-id="ce270-416">According to [XOP] section 5,</span></span>  
  
-   <span data-ttu-id="ce270-417">R4148: SOAP1.1 Infoset parte deve conter o cabeçalho Content-Type com o tipo de mídia application/xop + xml e parâmetros de tipo = "text/xml" e o conjunto de caracteres</span><span class="sxs-lookup"><span data-stu-id="ce270-417">R4148: SOAP1.1 Infoset part must contain Content-Type header with media type application/xop+xml and parameters type="text/xml" and charset</span></span>  
  
    ```  
    Content-Type: application/xop+xml;  
                  charset=utf-8;type="text/xml"  
    ```  
  
-   <span data-ttu-id="ce270-418">R4149: A parte de SOAP 1.2 Infoset deve conter o cabeçalho Content-Type com o tipo de mídia `application/xop+xml` e parâmetros de tipo = "`application/soap+xml`" e `charset`.</span><span class="sxs-lookup"><span data-stu-id="ce270-418">R4149: The SOAP 1.2 Infoset part must contain the Content-Type header with media type `application/xop+xml` and parameters type="`application/soap+xml`" and `charset`.</span></span>  
  
    ```  
    Content-Type: application/xop+xml;  
                  charset=utf-8;type="application/soap+xml"  
    ```  
  
     <span data-ttu-id="ce270-419">Enquanto XOP define o `charset` parâmetro `application/xop+xml` para ser opcional, é necessário para interoperabilidade semelhante para o requisito de BP 1.1 o `charset` parâmetro para o `text/xml` tipo de mídia.</span><span class="sxs-lookup"><span data-stu-id="ce270-419">While XOP defines the `charset` parameter for `application/xop+xml` to be optional, it is needed for interoperability similar to the BP 1.1 requirement on the `charset` parameter for the `text/xml` media type.</span></span>  
  
-   <span data-ttu-id="ce270-420">R41410: O `type` e `charset` parâmetros devem estar presentes no cabeçalho de Content-Type da parte de Infoset de SOAP 1. x.</span><span class="sxs-lookup"><span data-stu-id="ce270-420">R41410: The `type` and `charset` parameters must be present on the Content-Type header of the SOAP 1.x Infoset part.</span></span>  
  
#### <a name="wcf-endpoint-support-for-mtom"></a><span data-ttu-id="ce270-421">Suporte de ponto de extremidade do WCF para MTOM</span><span class="sxs-lookup"><span data-stu-id="ce270-421">WCF Endpoint Support for MTOM</span></span>  
 <span data-ttu-id="ce270-422">A finalidade de MTOM é codificar uma mensagem SOAP para otimizar o dados codificados na base64.</span><span class="sxs-lookup"><span data-stu-id="ce270-422">The purpose of MTOM is to encode a SOAP message to optimize base64-encoded data.</span></span> <span data-ttu-id="ce270-423">A seguir está uma lista de restrições:</span><span class="sxs-lookup"><span data-stu-id="ce270-423">The following is a list of constraints:</span></span>  
  
-   <span data-ttu-id="ce270-424">R4151: Qualquer item de informação do elemento que contém dados codificados em base64 pode ser otimizado.</span><span class="sxs-lookup"><span data-stu-id="ce270-424">R4151: Any element information item that contains base64-encoded data may be optimized.</span></span>  
  
-   <span data-ttu-id="ce270-425">B4152: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] otimiza os itens de informações do elemento que contêm dados codificados em base64 e excederem 1024 bytes de comprimento.</span><span class="sxs-lookup"><span data-stu-id="ce270-425">B4152: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] optimizes element information items that contain base64-encoded data and exceed 1024 bytes in length.</span></span>  
  
 <span data-ttu-id="ce270-426">Um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ponto de extremidade configurado para usar MTOM sempre enviará mensagens codificadas MTOM.</span><span class="sxs-lookup"><span data-stu-id="ce270-426">A [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] endpoint configured to use MTOM will always send MTOM-encoded messages.</span></span> <span data-ttu-id="ce270-427">Mesmo que nenhuma parte de atender aos critérios necessários, a mensagem é codificado ainda MTOM (serializado como um pacote MIME com uma única parte MIME que contém o envelope SOAP).</span><span class="sxs-lookup"><span data-stu-id="ce270-427">Even if no parts meet the required criteria, the message is still MTOM-encoded (serialized as a MIME package with a single MIME part containing the SOAP envelope).</span></span>  
  
### <a name="ws-policy-assertion-for-mtom"></a><span data-ttu-id="ce270-428">Asserção do WS-Policy para MTOM</span><span class="sxs-lookup"><span data-stu-id="ce270-428">WS-Policy Assertion for MTOM</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] <span data-ttu-id="ce270-429">usa a seguinte declaração de política para indicar o uso MTOM pelo ponto de extremidade:</span><span class="sxs-lookup"><span data-stu-id="ce270-429">uses the following policy assertion to indicate MTOM usage by endpoint:</span></span>  
  
```xml  
<wsoma:OptimizedMimeSerialization ... />  
```  
  
-   <span data-ttu-id="ce270-430">R4211: A declaração de política anterior tem um assunto de política do ponto de extremidade e especifica que todas as mensagens enviadas e recebidas do ponto de extremidade devem ser otimizadas usando MTOM.</span><span class="sxs-lookup"><span data-stu-id="ce270-430">R4211: The preceding policy assertion has an Endpoint Policy Subject and specifies that all messages sent to and received from the endpoint must be optimized using MTOM.</span></span>  
  
-   <span data-ttu-id="ce270-431">B4212: Quando estiver configurado para usar a otimização MTOM, um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ponto de extremidade adiciona uma declaração de política de MTOM para a diretiva anexada ao correspondente `wsdl:binding`.</span><span class="sxs-lookup"><span data-stu-id="ce270-431">B4212: When configured to use MTOM optimization, an [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] endpoint adds an MTOM Policy assertion to the policy attached to the corresponding `wsdl:binding`.</span></span>  
  
### <a name="composition-with-ws-security"></a><span data-ttu-id="ce270-432">Composição com WS-Security</span><span class="sxs-lookup"><span data-stu-id="ce270-432">Composition with WS-Security</span></span>  
 <span data-ttu-id="ce270-433">MTOM é um mecanismo de codificação é semelhante a `text/xml` e [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] XML binário.</span><span class="sxs-lookup"><span data-stu-id="ce270-433">MTOM is an encoding mechanism that is similar to `text/xml` and [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Binary XML.</span></span> <span data-ttu-id="ce270-434">MTOM oferece composição natural com WS-Security e outros WS-\* protocolos: uma mensagem protegida usando o WS-Security pode ser otimizada MTOM.</span><span class="sxs-lookup"><span data-stu-id="ce270-434">MTOM offers natural composition with WS-Security and other WS-\* protocols: a message secured using WS-Security can be optimized using MTOM.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="ce270-435">Exemplos</span><span class="sxs-lookup"><span data-stu-id="ce270-435">Examples</span></span>  
  
#### <a name="wcf-soap-11-message-encoded-using-mtom"></a><span data-ttu-id="ce270-436">WCF SOAP 1.1 mensagem codificada usando MTOM</span><span class="sxs-lookup"><span data-stu-id="ce270-436">WCF SOAP 1.1 Message Encoded Using MTOM</span></span>  
  
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
  
#### <a name="wcf-secure-soap-12-message-encoded-using-mtom"></a><span data-ttu-id="ce270-437">WCF seguro SOAP 1.2 a mensagem codificada usando MTOM</span><span class="sxs-lookup"><span data-stu-id="ce270-437">WCF Secure SOAP 1.2 Message Encoded Using MTOM</span></span>  
 <span data-ttu-id="ce270-438">Neste exemplo, uma mensagem é codificada usando MTOM e SOAP 1.2 são protegidos usando o WS-Security.</span><span class="sxs-lookup"><span data-stu-id="ce270-438">In this example, a message is encoded using MTOM and SOAP 1.2 that is protected using WS-Security.</span></span> <span data-ttu-id="ce270-439">As partes binárias identificadas para codificação é o conteúdo do `BinarySecurityToken`, `CipherValue` do `EncryptedData` correspondente para a assinatura criptografada e o corpo criptografado.</span><span class="sxs-lookup"><span data-stu-id="ce270-439">The binary parts identified for encoding are the contents of the `BinarySecurityToken`, `CipherValue` of the `EncryptedData` corresponding to the encrypted signature and encrypted body.</span></span> <span data-ttu-id="ce270-440">Observe que o `CipherValue` do `EncryptedKey` não foi identificado para a otimização, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], pois seu tamanho é menor, em seguida, 1024 bytes.</span><span class="sxs-lookup"><span data-stu-id="ce270-440">Note that the `CipherValue` of the `EncryptedKey` was not identified for optimization by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], because its length is less then 1024 bytes.</span></span>  
  
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
