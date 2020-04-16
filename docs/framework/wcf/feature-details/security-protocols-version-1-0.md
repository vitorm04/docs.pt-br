---
title: Protocolos de segurança versão 1.0
ms.date: 03/30/2017
ms.assetid: ee3402d2-1076-410b-a3cb-fae0372bd7af
ms.openlocfilehash: 0b86d870350d8728134cd2b42bbeb232183535bc
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463800"
---
# <a name="security-protocols-version-10"></a><span data-ttu-id="db74a-102">Protocolos de segurança versão 1.0</span><span class="sxs-lookup"><span data-stu-id="db74a-102">Security Protocols version 1.0</span></span>
<span data-ttu-id="db74a-103">Os Protocolos de Segurança de Serviços Web fornecem mecanismos de segurança de serviços da Web que cobrem todos os requisitos de segurança de mensagens corporativas existentes.</span><span class="sxs-lookup"><span data-stu-id="db74a-103">The Web Services Security Protocols provide Web services security mechanisms that cover all existing enterprise messaging security requirements.</span></span> <span data-ttu-id="db74a-104">Esta seção descreve os detalhes da versão 1.0 da <xref:System.ServiceModel.Channels.SecurityBindingElement>Windows Communication Foundation (WCF) (implementados no ) para os seguintes protocolos de segurança de serviços da Web.</span><span class="sxs-lookup"><span data-stu-id="db74a-104">This section describes the Windows Communication Foundation (WCF) version 1.0 details (implemented in the <xref:System.ServiceModel.Channels.SecurityBindingElement>) for the following Web services security protocols.</span></span>  
  
|<span data-ttu-id="db74a-105">Especificação/Documento</span><span class="sxs-lookup"><span data-stu-id="db74a-105">Specification/Document</span></span>|<span data-ttu-id="db74a-106">Link</span><span class="sxs-lookup"><span data-stu-id="db74a-106">Link</span></span>|  
|-|-|  
|<span data-ttu-id="db74a-107">WSS: Segurança de mensagens SOAP 1.0</span><span class="sxs-lookup"><span data-stu-id="db74a-107">WSS: SOAP Message Security 1.0</span></span>|<https://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0.pdf>|
|<span data-ttu-id="db74a-108">WSS: Perfil de token de nome de usuário 1.0</span><span class="sxs-lookup"><span data-stu-id="db74a-108">WSS: Username Token Profile 1.0</span></span>|<https://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0.pdf>|
|<span data-ttu-id="db74a-109">WSS: Perfil de Token X509 1.0</span><span class="sxs-lookup"><span data-stu-id="db74a-109">WSS: X509 Token Profile 1.0</span></span>|<https://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-x509-token-profile-1.0.pdf>|
|<span data-ttu-id="db74a-110">WSS: SAML 1.1 Token Profile 1.0</span><span class="sxs-lookup"><span data-stu-id="db74a-110">WSS: SAML 1.1 Token Profile 1.0</span></span>|<https://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.0.pdf>|
|<span data-ttu-id="db74a-111">WSS: Segurança de mensagens SOAP 1.1</span><span class="sxs-lookup"><span data-stu-id="db74a-111">WSS: SOAP Message Security 1.1</span></span>|<https://www.oasis-open.org/committees/download.php/16790/wss-v1.1-spec-os-SOAPMessageSecurity.pdf>|
|<span data-ttu-id="db74a-112">Perfil de token wss nome de usuário 1.1</span><span class="sxs-lookup"><span data-stu-id="db74a-112">WSS Username Token Profile 1.1</span></span>|<https://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0.pdf>|
|<span data-ttu-id="db74a-113">WSS: Perfil de Token X.509 1.1</span><span class="sxs-lookup"><span data-stu-id="db74a-113">WSS: X.509 Token Profile 1.1</span></span>|<https://www.oasis-open.org/committees/download.php/16785/wss-v1.1-spec-os-x509TokenProfile.pdf>|
|<span data-ttu-id="db74a-114">WSS: Perfil do Token Kerberos 1.1</span><span class="sxs-lookup"><span data-stu-id="db74a-114">WSS: Kerberos Token Profile 1.1</span></span>|<https://www.oasis-open.org/committees/download.php/16788/wss-v1.1-spec-os-KerberosTokenProfile.pdf>|
|<span data-ttu-id="db74a-115">WSS: SAML 1.1 Token Profile 1.1</span><span class="sxs-lookup"><span data-stu-id="db74a-115">WSS: SAML 1.1 Token Profile 1.1</span></span>|<https://www.oasis-open.org/committees/download.php/16768/wss-v1.1-spec-os-SAMLTokenProfile.pdf>|
|<span data-ttu-id="db74a-116">Conversa ws-segura</span><span class="sxs-lookup"><span data-stu-id="db74a-116">WS-Secure Conversation</span></span>|<https://specs.xmlsoap.org/ws/2005/02/sc/WS-SecureConversation.pdf>|
|<span data-ttu-id="db74a-117">WS-Trust</span><span class="sxs-lookup"><span data-stu-id="db74a-117">WS-Trust</span></span>|<https://specs.xmlsoap.org/ws/2005/02/trust/ws-trust.pdf>|
|<span data-ttu-id="db74a-118">Nota do aplicativo:</span><span class="sxs-lookup"><span data-stu-id="db74a-118">Application Note:</span></span><br /><br /> <span data-ttu-id="db74a-119">Usando ws-trust para aperto de mão TLS</span><span class="sxs-lookup"><span data-stu-id="db74a-119">Using WS-Trust for TLS Handshake</span></span>|<span data-ttu-id="db74a-120">A ser publicado</span><span class="sxs-lookup"><span data-stu-id="db74a-120">To be published</span></span>|  
|<span data-ttu-id="db74a-121">Nota do aplicativo:</span><span class="sxs-lookup"><span data-stu-id="db74a-121">Application Note:</span></span><br /><br /> <span data-ttu-id="db74a-122">Usando ws-trust para SPNEGO</span><span class="sxs-lookup"><span data-stu-id="db74a-122">Using WS-Trust for SPNEGO</span></span>|<span data-ttu-id="db74a-123">A ser publicado</span><span class="sxs-lookup"><span data-stu-id="db74a-123">To be published</span></span>|  
|<span data-ttu-id="db74a-124">Nota do aplicativo:</span><span class="sxs-lookup"><span data-stu-id="db74a-124">Application Note:</span></span><br /><br /> <span data-ttu-id="db74a-125">Serviços web abordando referências e identidade de ponto final</span><span class="sxs-lookup"><span data-stu-id="db74a-125">Web Services Addressing Endpoint References And Identity</span></span>|<span data-ttu-id="db74a-126">A ser publicado</span><span class="sxs-lookup"><span data-stu-id="db74a-126">To be published</span></span>|  
|<span data-ttu-id="db74a-127">Política WS-Segurança 1.1</span><span class="sxs-lookup"><span data-stu-id="db74a-127">WS-SecurityPolicy 1.1</span></span><br /><br /> <span data-ttu-id="db74a-128">(2005/07)</span><span class="sxs-lookup"><span data-stu-id="db74a-128">(2005/07)</span></span>|<https://specs.xmlsoap.org/ws/2005/07/securitypolicy/ws-securitypolicy.pdf><br /><br /> <span data-ttu-id="db74a-129">conforme alterado pela [errata](https://lists.oasis-open.org/archives/ws-sx/200512/msg00017.html) submetida ao Comitê Técnico do OASIS WS-SX</span><span class="sxs-lookup"><span data-stu-id="db74a-129">as amended by [errata](https://lists.oasis-open.org/archives/ws-sx/200512/msg00017.html) submitted to OASIS WS-SX Technical Committee</span></span> |  
  
 <span data-ttu-id="db74a-130">O WCF, versão 1, fornece 17 modos de autenticação que podem ser usados como base para a configuração de segurança dos serviços da Web.</span><span class="sxs-lookup"><span data-stu-id="db74a-130">WCF, version 1, provides 17 authentication modes that can be used as the basis for Web services security configuration.</span></span> <span data-ttu-id="db74a-131">Cada modo é otimizado para um conjunto comum de requisitos de implantação, tais como:</span><span class="sxs-lookup"><span data-stu-id="db74a-131">Each mode is optimized for a common set of deployment requirements, such as:</span></span>  
  
- <span data-ttu-id="db74a-132">Credenciais usadas para autenticar cliente e serviço.</span><span class="sxs-lookup"><span data-stu-id="db74a-132">Credentials used to authenticate client and service.</span></span>  
  
- <span data-ttu-id="db74a-133">Mecanismos de proteção de segurança de mensagens ou transportes.</span><span class="sxs-lookup"><span data-stu-id="db74a-133">Message or transport security protection mechanisms.</span></span>  
  
- <span data-ttu-id="db74a-134">Padrões de troca de mensagens.</span><span class="sxs-lookup"><span data-stu-id="db74a-134">Message exchange patterns.</span></span>  
  
|<span data-ttu-id="db74a-135">Modo de autenticação</span><span class="sxs-lookup"><span data-stu-id="db74a-135">Authentication Mode</span></span>|<span data-ttu-id="db74a-136">Autenticação de cliente</span><span class="sxs-lookup"><span data-stu-id="db74a-136">Client Authentication</span></span>|<span data-ttu-id="db74a-137">Autenticação do servidor</span><span class="sxs-lookup"><span data-stu-id="db74a-137">Server Authentication</span></span>|<span data-ttu-id="db74a-138">Mode</span><span class="sxs-lookup"><span data-stu-id="db74a-138">Mode</span></span>|  
|-------------------------|---------------------------|---------------------------|----------|  
|<span data-ttu-id="db74a-139">Nome de usuárioSobre transporte</span><span class="sxs-lookup"><span data-stu-id="db74a-139">UserNameOverTransport</span></span>|<span data-ttu-id="db74a-140">Nome de usuário/senha</span><span class="sxs-lookup"><span data-stu-id="db74a-140">User name/password</span></span>|<span data-ttu-id="db74a-141">X509</span><span class="sxs-lookup"><span data-stu-id="db74a-141">X509</span></span>|<span data-ttu-id="db74a-142">Transporte</span><span class="sxs-lookup"><span data-stu-id="db74a-142">Transport</span></span>|  
|<span data-ttu-id="db74a-143">Transporte por excesso de certificados</span><span class="sxs-lookup"><span data-stu-id="db74a-143">CertificateOverTransport</span></span>|<span data-ttu-id="db74a-144">X509</span><span class="sxs-lookup"><span data-stu-id="db74a-144">X509</span></span>|<span data-ttu-id="db74a-145">X509</span><span class="sxs-lookup"><span data-stu-id="db74a-145">X509</span></span>|<span data-ttu-id="db74a-146">Transporte</span><span class="sxs-lookup"><span data-stu-id="db74a-146">Transport</span></span>|  
|<span data-ttu-id="db74a-147">KerberosOverTransport</span><span class="sxs-lookup"><span data-stu-id="db74a-147">KerberosOverTransport</span></span>|<span data-ttu-id="db74a-148">Windows</span><span class="sxs-lookup"><span data-stu-id="db74a-148">Windows</span></span>|<span data-ttu-id="db74a-149">X509</span><span class="sxs-lookup"><span data-stu-id="db74a-149">X509</span></span>|<span data-ttu-id="db74a-150">Transporte</span><span class="sxs-lookup"><span data-stu-id="db74a-150">Transport</span></span>|  
|<span data-ttu-id="db74a-151">EmitidoTokenOverTransport</span><span class="sxs-lookup"><span data-stu-id="db74a-151">IssuedTokenOverTransport</span></span>|<span data-ttu-id="db74a-152">Federado</span><span class="sxs-lookup"><span data-stu-id="db74a-152">Federated</span></span>|<span data-ttu-id="db74a-153">X509</span><span class="sxs-lookup"><span data-stu-id="db74a-153">X509</span></span>|<span data-ttu-id="db74a-154">Transporte</span><span class="sxs-lookup"><span data-stu-id="db74a-154">Transport</span></span>|  
|<span data-ttu-id="db74a-155">SspiNegociedOverTransport</span><span class="sxs-lookup"><span data-stu-id="db74a-155">SspiNegotiatedOverTransport</span></span>|<span data-ttu-id="db74a-156">Windows Sspi Negociado</span><span class="sxs-lookup"><span data-stu-id="db74a-156">Windows Sspi Negotiated</span></span>|<span data-ttu-id="db74a-157">Windows Sspi Negociado</span><span class="sxs-lookup"><span data-stu-id="db74a-157">Windows Sspi Negotiated</span></span>|<span data-ttu-id="db74a-158">Transporte</span><span class="sxs-lookup"><span data-stu-id="db74a-158">Transport</span></span>|  
|<span data-ttu-id="db74a-159">Certificado anônimo</span><span class="sxs-lookup"><span data-stu-id="db74a-159">AnonymousForCertificate</span></span>|<span data-ttu-id="db74a-160">Nenhum</span><span class="sxs-lookup"><span data-stu-id="db74a-160">None</span></span>|<span data-ttu-id="db74a-161">X509</span><span class="sxs-lookup"><span data-stu-id="db74a-161">X509</span></span>|<span data-ttu-id="db74a-162">Mensagem</span><span class="sxs-lookup"><span data-stu-id="db74a-162">Message</span></span>|  
|<span data-ttu-id="db74a-163">Nome de usuárioParacertificado</span><span class="sxs-lookup"><span data-stu-id="db74a-163">UserNameForCertificate</span></span>|<span data-ttu-id="db74a-164">Nome de usuário/senha</span><span class="sxs-lookup"><span data-stu-id="db74a-164">User name/password</span></span>|<span data-ttu-id="db74a-165">X509</span><span class="sxs-lookup"><span data-stu-id="db74a-165">X509</span></span>|<span data-ttu-id="db74a-166">Mensagem</span><span class="sxs-lookup"><span data-stu-id="db74a-166">Message</span></span>|  
|<span data-ttu-id="db74a-167">Certificado mútuo</span><span class="sxs-lookup"><span data-stu-id="db74a-167">MutualCertificate</span></span>|<span data-ttu-id="db74a-168">X509</span><span class="sxs-lookup"><span data-stu-id="db74a-168">X509</span></span>|<span data-ttu-id="db74a-169">X509</span><span class="sxs-lookup"><span data-stu-id="db74a-169">X509</span></span>|<span data-ttu-id="db74a-170">Mensagem</span><span class="sxs-lookup"><span data-stu-id="db74a-170">Message</span></span>|  
|<span data-ttu-id="db74a-171">MutualCertificateDuplex</span><span class="sxs-lookup"><span data-stu-id="db74a-171">MutualCertificateDuplex</span></span>|<span data-ttu-id="db74a-172">X509</span><span class="sxs-lookup"><span data-stu-id="db74a-172">X509</span></span>|<span data-ttu-id="db74a-173">X509</span><span class="sxs-lookup"><span data-stu-id="db74a-173">X509</span></span>|<span data-ttu-id="db74a-174">Mensagem</span><span class="sxs-lookup"><span data-stu-id="db74a-174">Message</span></span>|  
|<span data-ttu-id="db74a-175">EmitidoTokenForCertificate</span><span class="sxs-lookup"><span data-stu-id="db74a-175">IssuedTokenForCertificate</span></span>|<span data-ttu-id="db74a-176">Federado</span><span class="sxs-lookup"><span data-stu-id="db74a-176">Federated</span></span>|<span data-ttu-id="db74a-177">X509</span><span class="sxs-lookup"><span data-stu-id="db74a-177">X509</span></span>|<span data-ttu-id="db74a-178">Mensagem</span><span class="sxs-lookup"><span data-stu-id="db74a-178">Message</span></span>|  
|<span data-ttu-id="db74a-179">Kerberos</span><span class="sxs-lookup"><span data-stu-id="db74a-179">Kerberos</span></span>|<span data-ttu-id="db74a-180">Windows</span><span class="sxs-lookup"><span data-stu-id="db74a-180">Windows</span></span>|<span data-ttu-id="db74a-181">Windows</span><span class="sxs-lookup"><span data-stu-id="db74a-181">Windows</span></span>|<span data-ttu-id="db74a-182">Mensagem</span><span class="sxs-lookup"><span data-stu-id="db74a-182">Message</span></span>|  
|<span data-ttu-id="db74a-183">IssuedToken</span><span class="sxs-lookup"><span data-stu-id="db74a-183">IssuedToken</span></span>|<span data-ttu-id="db74a-184">Federado</span><span class="sxs-lookup"><span data-stu-id="db74a-184">Federated</span></span>|<span data-ttu-id="db74a-185">Federado</span><span class="sxs-lookup"><span data-stu-id="db74a-185">Federated</span></span>|<span data-ttu-id="db74a-186">Mensagem</span><span class="sxs-lookup"><span data-stu-id="db74a-186">Message</span></span>|  
|<span data-ttu-id="db74a-187">SspiNegociado</span><span class="sxs-lookup"><span data-stu-id="db74a-187">SspiNegotiated</span></span>|<span data-ttu-id="db74a-188">Windows Sspi Negociado</span><span class="sxs-lookup"><span data-stu-id="db74a-188">Windows Sspi Negotiated</span></span>|<span data-ttu-id="db74a-189">Windows Sspi Negociado</span><span class="sxs-lookup"><span data-stu-id="db74a-189">Windows Sspi Negotiated</span></span>|<span data-ttu-id="db74a-190">Mensagem</span><span class="sxs-lookup"><span data-stu-id="db74a-190">Message</span></span>|  
|<span data-ttu-id="db74a-191">AnonymousForSslNegociado</span><span class="sxs-lookup"><span data-stu-id="db74a-191">AnonymousForSslNegotiated</span></span>|<span data-ttu-id="db74a-192">Nenhum</span><span class="sxs-lookup"><span data-stu-id="db74a-192">None</span></span>|<span data-ttu-id="db74a-193">X509</span><span class="sxs-lookup"><span data-stu-id="db74a-193">X509, TLS-Nego</span></span>|<span data-ttu-id="db74a-194">Mensagem</span><span class="sxs-lookup"><span data-stu-id="db74a-194">Message</span></span>|  
|<span data-ttu-id="db74a-195">Nome do usuárioForSslNegociado</span><span class="sxs-lookup"><span data-stu-id="db74a-195">UserNameForSslNegotiated</span></span>|<span data-ttu-id="db74a-196">Nome de usuário/senha</span><span class="sxs-lookup"><span data-stu-id="db74a-196">User name/password</span></span>|<span data-ttu-id="db74a-197">X509</span><span class="sxs-lookup"><span data-stu-id="db74a-197">X509, TLS-Nego</span></span>|<span data-ttu-id="db74a-198">Mensagem</span><span class="sxs-lookup"><span data-stu-id="db74a-198">Message</span></span>|  
|<span data-ttu-id="db74a-199">MutualSslNegociado</span><span class="sxs-lookup"><span data-stu-id="db74a-199">MutualSslNegotiated</span></span>|<span data-ttu-id="db74a-200">X509</span><span class="sxs-lookup"><span data-stu-id="db74a-200">X509</span></span>|<span data-ttu-id="db74a-201">X509</span><span class="sxs-lookup"><span data-stu-id="db74a-201">X509, TLS-Nego</span></span>|<span data-ttu-id="db74a-202">Mensagem</span><span class="sxs-lookup"><span data-stu-id="db74a-202">Message</span></span>|  
|<span data-ttu-id="db74a-203">EmitidoTokenForSslNegociado</span><span class="sxs-lookup"><span data-stu-id="db74a-203">IssuedTokenForSslNegotiated</span></span>|<span data-ttu-id="db74a-204">Federado</span><span class="sxs-lookup"><span data-stu-id="db74a-204">Federated</span></span>|<span data-ttu-id="db74a-205">X509</span><span class="sxs-lookup"><span data-stu-id="db74a-205">X509, TLS-Nego</span></span>|<span data-ttu-id="db74a-206">Mensagem</span><span class="sxs-lookup"><span data-stu-id="db74a-206">Message</span></span>|  
  
 <span data-ttu-id="db74a-207">Os pontos finais que usam esses modos de autenticação podem expressar seus requisitos de segurança usando o WS-SecurityPolicy (WS-SP).</span><span class="sxs-lookup"><span data-stu-id="db74a-207">Endpoints using such authentication modes can express their security requirements using WS-SecurityPolicy (WS-SP).</span></span> <span data-ttu-id="db74a-208">Este documento descreve a estrutura de mensagens de cabeçalho de segurança e infra-estrutura para cada modo de autenticação e fornece exemplos de políticas e mensagens.</span><span class="sxs-lookup"><span data-stu-id="db74a-208">This document describes the structure of security header and infrastructure messages for each authentication mode and provides examples of policies and messages.</span></span>  
  
 <span data-ttu-id="db74a-209">O WCF aproveita o WS-SecureConversation para fornecer suporte a sessões seguras para proteger trocas de várias mensagens entre aplicativos.</span><span class="sxs-lookup"><span data-stu-id="db74a-209">WCF leverages WS-SecureConversation to provide secure sessions support to protect multi-message exchanges between applications.</span></span>  <span data-ttu-id="db74a-210">Consulte "Sessões Seguras" abaixo para obter detalhes da implementação.</span><span class="sxs-lookup"><span data-stu-id="db74a-210">See "Secure Sessions" below for implementation details.</span></span>  
  
 <span data-ttu-id="db74a-211">Além dos modos de autenticação, o WCF fornece configurações para controlar mecanismos comuns de proteção que se aplicam à maioria dos modos de autenticação baseados em segurança de mensagens, por exemplo: ordem de assinatura versus operações de criptografia, suítes de algoritmos, derivação de chaves e confirmação de assinatura.</span><span class="sxs-lookup"><span data-stu-id="db74a-211">In addition to authentication modes, WCF provides settings to control common protection mechanisms that apply to most message security-based authentication modes, for example: order of signature versus encryption operations, algorithm suites, key derivation, and signature confirmation.</span></span>  
  
 <span data-ttu-id="db74a-212">Os seguintes prefixos e namespaces são usados neste documento.</span><span class="sxs-lookup"><span data-stu-id="db74a-212">The following prefixes and namespaces are used in this document.</span></span>  
  
|<span data-ttu-id="db74a-213">Prefixo</span><span class="sxs-lookup"><span data-stu-id="db74a-213">Prefix</span></span>|<span data-ttu-id="db74a-214">Namespace</span><span class="sxs-lookup"><span data-stu-id="db74a-214">Namespace</span></span>|  
|------------|---------------|  
|<span data-ttu-id="db74a-215">s</span><span class="sxs-lookup"><span data-stu-id="db74a-215">s</span></span>|<http://www.w3.org/2003/05/soap-envelope/>|
|<span data-ttu-id="db74a-216">sp</span><span class="sxs-lookup"><span data-stu-id="db74a-216">sp</span></span>|<http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/>|
|<span data-ttu-id="db74a-217">a</span><span class="sxs-lookup"><span data-stu-id="db74a-217">a</span></span>|<http://www.w3.org/2005/08/addressing>|  
|<span data-ttu-id="db74a-218">wsse</span><span class="sxs-lookup"><span data-stu-id="db74a-218">wsse</span></span>|<span data-ttu-id="db74a-219">TBD – OASIS WSS 1.0 URI</span><span class="sxs-lookup"><span data-stu-id="db74a-219">TBD – OASIS WSS 1.0 URI</span></span>|  
|<span data-ttu-id="db74a-220">wsse11</span><span class="sxs-lookup"><span data-stu-id="db74a-220">wsse11</span></span>|<span data-ttu-id="db74a-221">TBD – OASIS WSS 1.1 URI</span><span class="sxs-lookup"><span data-stu-id="db74a-221">TBD – OASIS WSS 1.1 URI</span></span>|  
|<span data-ttu-id="db74a-222">Wsu</span><span class="sxs-lookup"><span data-stu-id="db74a-222">wsu</span></span>|<span data-ttu-id="db74a-223">TBD – OASIS WSS 1.0 Utilitário URI</span><span class="sxs-lookup"><span data-stu-id="db74a-223">TBD – OASIS WSS 1.0 Utility URI</span></span>|  
|<span data-ttu-id="db74a-224">Ds</span><span class="sxs-lookup"><span data-stu-id="db74a-224">ds</span></span>|<span data-ttu-id="db74a-225">TBD – W3C XMLDSig URI</span><span class="sxs-lookup"><span data-stu-id="db74a-225">TBD – W3C XMLDSig URI</span></span>|  
|<span data-ttu-id="db74a-226">Wst</span><span class="sxs-lookup"><span data-stu-id="db74a-226">wst</span></span>|<span data-ttu-id="db74a-227">TBD – WS-Trust 2005/02 URI</span><span class="sxs-lookup"><span data-stu-id="db74a-227">TBD – WS-Trust 2005/02 URI</span></span>|  
|<span data-ttu-id="db74a-228">wssc</span><span class="sxs-lookup"><span data-stu-id="db74a-228">wssc</span></span>|<span data-ttu-id="db74a-229">TBD – WS-SecureConversation 2005/02 URI</span><span class="sxs-lookup"><span data-stu-id="db74a-229">TBD – WS-SecureConversation 2005/02 URI</span></span>|  
|<span data-ttu-id="db74a-230">serragem</span><span class="sxs-lookup"><span data-stu-id="db74a-230">wsaw</span></span>|<span data-ttu-id="db74a-231">TBD - Espaço de nome da política ws-addressing</span><span class="sxs-lookup"><span data-stu-id="db74a-231">TBD - WS-Addressing policy namespace</span></span>|  
|<span data-ttu-id="db74a-232">Wsp</span><span class="sxs-lookup"><span data-stu-id="db74a-232">wsp</span></span>|<http://schemas.xmlsoap.org/ws/2004/09/policy>|  
|<span data-ttu-id="db74a-233">Mssp</span><span class="sxs-lookup"><span data-stu-id="db74a-233">mssp</span></span>|<http://schemas.xmlsoap.org/ws/2005/07/securitypolicy>|
  
## <a name="1-token-profiles"></a><span data-ttu-id="db74a-234">1. Perfis de token</span><span class="sxs-lookup"><span data-stu-id="db74a-234">1. Token Profiles</span></span>  
 <span data-ttu-id="db74a-235">As especificações de segurança dos Serviços Web representam credencial como tokens de segurança.</span><span class="sxs-lookup"><span data-stu-id="db74a-235">Web Services Security specifications represent credential as security tokens.</span></span> <span data-ttu-id="db74a-236">O WCF suporta os seguintes tipos de tokens:</span><span class="sxs-lookup"><span data-stu-id="db74a-236">WCF supports the following token types:</span></span>  
  
### <a name="11-usernametoken"></a><span data-ttu-id="db74a-237">1.1 Nome de usuárioToken</span><span class="sxs-lookup"><span data-stu-id="db74a-237">1.1 UsernameToken</span></span>  
 <span data-ttu-id="db74a-238">O WCF segue os perfis UsernameToken10 e UsernameToken11 com as seguintes restrições:</span><span class="sxs-lookup"><span data-stu-id="db74a-238">WCF follows UsernameToken10 and UsernameToken11 profiles with the following constraints:</span></span>  
  
 <span data-ttu-id="db74a-239">R1101 PasswordType atributo no nome de usuárioToken\Elemento senha DEVE ser omitido ou ter valor #PasswordText (padrão).</span><span class="sxs-lookup"><span data-stu-id="db74a-239">R1101 PasswordType attribute on UsernameToken\Password element MUST be either omitted or have value #PasswordText (default).</span></span>  
  
 <span data-ttu-id="db74a-240">Pode-se implementar o #PasswordDigest usando extensibilidade.</span><span class="sxs-lookup"><span data-stu-id="db74a-240">One can implement the #PasswordDigest using extensibility.</span></span> <span data-ttu-id="db74a-241">Observou-se que #PasswordDigest muitas vezes foi confundido por ser um mecanismo de proteção por senha seguro o suficiente.</span><span class="sxs-lookup"><span data-stu-id="db74a-241">It has been observed that #PasswordDigest was often mistaken to be a secure enough password protection mechanism.</span></span> <span data-ttu-id="db74a-242">Mas #PasswordDigest não pode servir como um substituto para a criptografia do UsernameToken.</span><span class="sxs-lookup"><span data-stu-id="db74a-242">But #PasswordDigest cannot serve as a substitute for encryption of the UsernameToken.</span></span> <span data-ttu-id="db74a-243">O objetivo principal do #PasswordDigest é a proteção contra ataques de repetição.</span><span class="sxs-lookup"><span data-stu-id="db74a-243">The primary goal of #PasswordDigest is protection against replay attacks.</span></span> <span data-ttu-id="db74a-244">Nos modos de autenticação WCF, as ameaças de ataque de repetição são mitigadas usando assinaturas de mensagens.</span><span class="sxs-lookup"><span data-stu-id="db74a-244">In WCF authentication modes, replay attack threats are mitigated by using message signatures.</span></span>  
  
 <span data-ttu-id="db74a-245">B1102 WCF nunca emite subelementos Nonce e Criado do Nome de UsuárioToken.</span><span class="sxs-lookup"><span data-stu-id="db74a-245">B1102 WCF never emits Nonce and Created sub-elements of the UsernameToken.</span></span>  
  
 <span data-ttu-id="db74a-246">Esses subelementos destinam-se a ajudar na detecção de repetição.</span><span class="sxs-lookup"><span data-stu-id="db74a-246">These sub-elements are intended to help replay detection.</span></span> <span data-ttu-id="db74a-247">O WCF usa assinaturas de mensagens em vez disso.</span><span class="sxs-lookup"><span data-stu-id="db74a-247">WCF uses message signatures instead.</span></span>  
  
 <span data-ttu-id="db74a-248">OOASIs WSS SOAP Message Security UsernameToken Profile 1.1 (UsernameToken11) introduziu a derivação de chave do recurso de senha.</span><span class="sxs-lookup"><span data-stu-id="db74a-248">OASIS WSS SOAP Message Security UsernameToken Profile 1.1 (UsernameToken11) introduced key derivation from password feature.</span></span>  
  
 <span data-ttu-id="db74a-249">B1103 A senha do nome de usuárioToken não deve ser usada para derivação de chaves e, portanto, para operações criptográficas.</span><span class="sxs-lookup"><span data-stu-id="db74a-249">B1103 UsernameToken password MUST not be used for key derivation and therefore for cryptographic operations.</span></span>  
  
 <span data-ttu-id="db74a-250">Raciocínio: as senhas são geralmente consideradas fracas demais para serem usadas em operações criptográficas.</span><span class="sxs-lookup"><span data-stu-id="db74a-250">Rationale: passwords are generally considered too weak to be used for cryptographic operations.</span></span>  
  
### <a name="12-x509-token"></a><span data-ttu-id="db74a-251">1.2 Token X509</span><span class="sxs-lookup"><span data-stu-id="db74a-251">1.2 X509 Token</span></span>  
 <span data-ttu-id="db74a-252">O WCF suporta certificados X509v3 como um tipo de credencial e segue X509TokenProfile1.0 e X509TokenProfile1.1 com as seguintes restrições:</span><span class="sxs-lookup"><span data-stu-id="db74a-252">WCF supports X509v3 certificates as a credential type and follows X509TokenProfile1.0 and X509TokenProfile1.1 with the following constraints:</span></span>  
  
 <span data-ttu-id="db74a-253">R1201 O atributo ValueType no elemento BinarySecurityToken deve ter valor #X509v3 quando contiver um certificado X509v3.</span><span class="sxs-lookup"><span data-stu-id="db74a-253">R1201 The ValueType attribute on the BinarySecurityToken element must have value #X509v3 when it contains an X509v3 certificate.</span></span>  
  
 <span data-ttu-id="db74a-254">O Perfil de Token WSS X509 1.0 e 1.1 definem também #X509PKIPathv1 e #PKCS7 como tipos de valor.</span><span class="sxs-lookup"><span data-stu-id="db74a-254">WSS X509 Token Profile 1.0 and 1.1 define also #X509PKIPathv1 and #PKCS7 as value types.</span></span> <span data-ttu-id="db74a-255">O WCF não suporta esses tipos.</span><span class="sxs-lookup"><span data-stu-id="db74a-255">WCF does not support these types.</span></span>  
  
 <span data-ttu-id="db74a-256">R1202 Se uma extensão do SubjectKeyIdentifier (SKI) estiver presente em um certificado X509, wsse:KeyIdentifier deve ser usado para referências externas ao token, com o atributo ValueType como #X509SubjectKeyIdentifier e seu conteúdo o valor codificado base64 da extensão SKI do certificado.</span><span class="sxs-lookup"><span data-stu-id="db74a-256">R1202 If a SubjectKeyIdentifier (SKI) extension is present in an X509 certificate, wsse:KeyIdentifier should be used for external references to the token, with the ValueType attribute as #X509SubjectKeyIdentifier and its content the base64-encoded value of certificate's SKI extension.</span></span>  
  
 <span data-ttu-id="db74a-257">As referências SKI são amplamente implementadas e comprovadamente um tipo de referência externa altamente interoperável.</span><span class="sxs-lookup"><span data-stu-id="db74a-257">SKI references are widely implemented and proven to be a highly interoperable external reference type.</span></span>  
  
 <span data-ttu-id="db74a-258">R1203 Uma referência externa ao Token de Segurança X509 NÃO deve usar ds:X509IssuerSerial.</span><span class="sxs-lookup"><span data-stu-id="db74a-258">R1203 An external Reference to X509 Security Token SHOULD NOT use ds:X509IssuerSerial.</span></span>  
  
 <span data-ttu-id="db74a-259">R1204 Se x509TokenProfile1.1 estiver em uso, uma referência externa ao Token de Segurança X509 DEVE usar a impressão digital introduzida pelo WS-Security 1.1.</span><span class="sxs-lookup"><span data-stu-id="db74a-259">R1204 If X509TokenProfile1.1 is in use, an external reference to X509 Security Token SHOULD use the thumbprint introduced by WS-Security 1.1.</span></span>  
  
 <span data-ttu-id="db74a-260">O WCF suporta X509IssuerSerial.</span><span class="sxs-lookup"><span data-stu-id="db74a-260">WCF supports X509IssuerSerial.</span></span> <span data-ttu-id="db74a-261">No entanto, existem problemas de interoperabilidade com X509IssuerSerial: O WCF usa uma string para comparar dois valores do X509IssuerSerial.</span><span class="sxs-lookup"><span data-stu-id="db74a-261">However There are interoperability issues with X509IssuerSerial: WCF uses a string to compare two values of X509IssuerSerial.</span></span> <span data-ttu-id="db74a-262">Portanto, se alguém reordena componentes do Nome do Assunto e envia para um serviço WCF uma referência a um certificado, ele pode não ser encontrado.</span><span class="sxs-lookup"><span data-stu-id="db74a-262">Therefore if one reorders components of the Subject Name and sends to an WCF service a reference to a certificate, it may not be found.</span></span>  
  
### <a name="13-kerberos-token"></a><span data-ttu-id="db74a-263">1.3 Token Kerberos</span><span class="sxs-lookup"><span data-stu-id="db74a-263">1.3 Kerberos Token</span></span>  
 <span data-ttu-id="db74a-264">O WCF suporta o KerberosTokenProfile1.1 para fins de autenticação do Windows com as seguintes restrições:</span><span class="sxs-lookup"><span data-stu-id="db74a-264">WCF supports KerberosTokenProfile1.1 for the purpose of Windows authentication with the following constraints:</span></span>  
  
 <span data-ttu-id="db74a-265">R1301 A Kerberos Token deve levar o valor de um GSS embrulhado Kerberos v4 AP_REQ como definido em GSS_API e a especificação Kerberos, e deve ter o atributo ValueType com o valor #GSS_Kerberosv5_AP_REQ.</span><span class="sxs-lookup"><span data-stu-id="db74a-265">R1301 A Kerberos Token must carry the value of a GSS wrapped Kerberos v4 AP_REQ as defined in GSS_API and the Kerberos specification, and must have the ValueType attribute with the value #GSS_Kerberosv5_AP_REQ.</span></span>  
  
 <span data-ttu-id="db74a-266">O WCF usa O Ap-REQ embrulhado em Kerberos GSS, não um AP-REQ nu.</span><span class="sxs-lookup"><span data-stu-id="db74a-266">WCF uses GSS wrapped Kerberos AP-REQ, not a bare AP-REQ.</span></span> <span data-ttu-id="db74a-267">Esta é uma prática de segurança.</span><span class="sxs-lookup"><span data-stu-id="db74a-267">This is a security best practice.</span></span>  
  
### <a name="14-saml-v11-token"></a><span data-ttu-id="db74a-268">1.4 SAML v1.1 Token</span><span class="sxs-lookup"><span data-stu-id="db74a-268">1.4 SAML v1.1 Token</span></span>  
 <span data-ttu-id="db74a-269">O WCF suporta os perfis WSS SAML Token 1.0 e 1.1 para tokens SAML v1.1.</span><span class="sxs-lookup"><span data-stu-id="db74a-269">WCF supports WSS SAML Token profiles 1.0 and 1.1 for SAML v1.1 tokens.</span></span> <span data-ttu-id="db74a-270">É possível implementar outras versões de formatos de token SAML.</span><span class="sxs-lookup"><span data-stu-id="db74a-270">It is possible to implement other versions of SAML token formats.</span></span>  
  
### <a name="15-security-context-token"></a><span data-ttu-id="db74a-271">1.5 Token de contexto de segurança</span><span class="sxs-lookup"><span data-stu-id="db74a-271">1.5 Security Context Token</span></span>  
 <span data-ttu-id="db74a-272">O WCF suporta o SCT (Security Context Token, token de contexto de segurança) introduzido no WS-SecureConversation.</span><span class="sxs-lookup"><span data-stu-id="db74a-272">WCF supports the Security Context Token (SCT) introduced in WS-SecureConversation.</span></span> <span data-ttu-id="db74a-273">O SCT é usado para representar um contexto de segurança estabelecido no SecureConversation, bem como os protocolos binários de negociação TLS e SSPI, descritos abaixo.</span><span class="sxs-lookup"><span data-stu-id="db74a-273">SCT is used to represent a security context established in SecureConversation as well as the binary negotiation protocols TLS and SSPI, described below.</span></span>  
  
## <a name="2-common-message-security-parameters"></a><span data-ttu-id="db74a-274">2. Parâmetros comuns de segurança de mensagens</span><span class="sxs-lookup"><span data-stu-id="db74a-274">2. Common Message Security Parameters</span></span>  
  
### <a name="21-timestamp"></a><span data-ttu-id="db74a-275">2.1 Carimbo de tempo</span><span class="sxs-lookup"><span data-stu-id="db74a-275">2.1 TimeStamp</span></span>  
 <span data-ttu-id="db74a-276">A presença de carimbo <xref:System.ServiceModel.Channels.SecurityBindingElement.IncludeTimestamp%2A> de <xref:System.ServiceModel.Channels.SecurityBindingElement> data e hora é controlada usando a propriedade da classe.</span><span class="sxs-lookup"><span data-stu-id="db74a-276">Timestamp presence is controlled using the <xref:System.ServiceModel.Channels.SecurityBindingElement.IncludeTimestamp%2A> property of the <xref:System.ServiceModel.Channels.SecurityBindingElement> class.</span></span> <span data-ttu-id="db74a-277">O WCF sempre serializa wsse:TimeStamp com wsse:Created e wsse:Expires fields.</span><span class="sxs-lookup"><span data-stu-id="db74a-277">WCF always serializes wsse:TimeStamp with wsse:Created and wsse:Expires fields.</span></span> <span data-ttu-id="db74a-278">O wsse:TimeStamp é sempre assinado quando a assinatura é usada.</span><span class="sxs-lookup"><span data-stu-id="db74a-278">The wsse:TimeStamp is always signed when signing is used.</span></span>  
  
### <a name="22-protection-order"></a><span data-ttu-id="db74a-279">2.2 Ordem de Proteção</span><span class="sxs-lookup"><span data-stu-id="db74a-279">2.2 Protection Order</span></span>  
 <span data-ttu-id="db74a-280">O WCF suporta a ordem de proteção de mensagens "Assinar antes de criptografar" e "Criptografar antes de assinar" (Política de segurança 1.1).</span><span class="sxs-lookup"><span data-stu-id="db74a-280">WCF supports the message protection order "Sign Before Encrypt" and "Encrypt Before Sign" (Security Policy 1.1).</span></span> <span data-ttu-id="db74a-281">"Assinar antes de criptografar" é recomendado por razões que incluem: mensagens protegidas com Encrypt Before Sign estão abertas a ataques de substituição de assinatura, a menos que o mecanismo WS-Security 1.1 SignatureConfirmation seja usado e uma assinatura sobre conteúdo criptografado dificulte a auditoria.</span><span class="sxs-lookup"><span data-stu-id="db74a-281">"Sign Before Encrypt" is recommended for reasons including: messages protected with Encrypt Before Sign are open to signature substitution attacks unless the WS-Security 1.1 SignatureConfirmation mechanism is used, and a signature over encrypted content makes auditing harder.</span></span>  
  
### <a name="23-signature-protection"></a><span data-ttu-id="db74a-282">2.3 Proteção de assinatura</span><span class="sxs-lookup"><span data-stu-id="db74a-282">2.3 Signature Protection</span></span>  
 <span data-ttu-id="db74a-283">Quando o Encrypt Before Sign é usado, recomenda-se proteger a assinatura para evitar ataques de força bruta para adivinhar o conteúdo criptografado ou a chave de assinatura (especialmente quando um token personalizado é usado com material chave fraco).</span><span class="sxs-lookup"><span data-stu-id="db74a-283">When Encrypt Before Sign is used, it is recommended to protect the signature to prevent brute force attacks for guessing the encrypted content or the signing key (especially when a custom token is used with weak key material).</span></span>  
  
### <a name="24-algorithm-suite"></a><span data-ttu-id="db74a-284">2.4 Suíte de Algoritmos</span><span class="sxs-lookup"><span data-stu-id="db74a-284">2.4 Algorithm Suite</span></span>  
 <span data-ttu-id="db74a-285">O WCF suporta todos os conjuntos de algoritmos listados na Política de Segurança 1.1.</span><span class="sxs-lookup"><span data-stu-id="db74a-285">WCF supports all algorithm suites listed in Security Policy 1.1.</span></span>  
  
### <a name="25-key-derivation"></a><span data-ttu-id="db74a-286">2.5 Derivação de Chaves</span><span class="sxs-lookup"><span data-stu-id="db74a-286">2.5 Key Derivation</span></span>  
 <span data-ttu-id="db74a-287">O WCF usa "Derivação de chave para chaves simétricas" conforme descrito no WS-SecureConversation.</span><span class="sxs-lookup"><span data-stu-id="db74a-287">WCF uses "Key Derivation for symmetric keys" as described in WS-SecureConversation.</span></span>  
  
### <a name="26-signature-confirmation"></a><span data-ttu-id="db74a-288">2.6 Confirmação de assinatura</span><span class="sxs-lookup"><span data-stu-id="db74a-288">2.6 Signature Confirmation</span></span>  
 <span data-ttu-id="db74a-289">A confirmação da assinatura pode ser a proteção contra ataques do intermediário para proteger o conjunto de assinaturas.</span><span class="sxs-lookup"><span data-stu-id="db74a-289">Signature confirmation can be as protection from middle man attacks to protect the set of signatures.</span></span>  
  
### <a name="27-security-header-layout"></a><span data-ttu-id="db74a-290">2.7 Layout do cabeçalho de segurança</span><span class="sxs-lookup"><span data-stu-id="db74a-290">2.7 Security Header Layout</span></span>  
 <span data-ttu-id="db74a-291">Cada modo de autenticação descreve um certo layout para o cabeçalho de segurança.</span><span class="sxs-lookup"><span data-stu-id="db74a-291">Each authentication mode describes a certain layout for the security header.</span></span> <span data-ttu-id="db74a-292">Os elementos dentro do cabeçalho de segurança são semi-ordenados.</span><span class="sxs-lookup"><span data-stu-id="db74a-292">Elements within the security header are semi-ordered.</span></span> <span data-ttu-id="db74a-293">Para definir a ordem dos elementos de criança do cabeçalho de segurança, a Política WS-Security define os seguintes modos de layout de cabeçalho de segurança:</span><span class="sxs-lookup"><span data-stu-id="db74a-293">To define the order of security header child elements, WS-Security Policy defines the following security header layout modes:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="db74a-294">Rigoroso</span><span class="sxs-lookup"><span data-stu-id="db74a-294">Strict</span></span>|<span data-ttu-id="db74a-295">Os itens são adicionados ao cabeçalho de segurança seguindo as regras de layout numeradas descritas na seção Política de Segurança 7.7.1 de acordo com um princípio geral de "declarar antes de usar".</span><span class="sxs-lookup"><span data-stu-id="db74a-295">Items are added to the security header following the numbered layout rules described in Security Policy section 7.7.1 according to a general principle of "declare before use".</span></span>|  
|<span data-ttu-id="db74a-296">Lax</span><span class="sxs-lookup"><span data-stu-id="db74a-296">Lax</span></span>|<span data-ttu-id="db74a-297">Os itens são adicionados ao cabeçalho de segurança em qualquer ordem que esteja em conformidade com o WSS: SOAP Message Security.</span><span class="sxs-lookup"><span data-stu-id="db74a-297">Items are added to the security header in any order that conforms to WSS: SOAP Message Security.</span></span>|  
|<span data-ttu-id="db74a-298">LaxTimestampFirst</span><span class="sxs-lookup"><span data-stu-id="db74a-298">LaxTimestampFirst</span></span>|<span data-ttu-id="db74a-299">O mesmo que Lax, exceto que o primeiro item no cabeçalho de segurança deve ser um wsse:Timestamp</span><span class="sxs-lookup"><span data-stu-id="db74a-299">Same as Lax except that the first item in the security header must be a wsse:Timestamp</span></span>|  
|<span data-ttu-id="db74a-300">LaxTimestampLast</span><span class="sxs-lookup"><span data-stu-id="db74a-300">LaxTimestampLast</span></span>|<span data-ttu-id="db74a-301">O mesmo que frouxo, exceto que o último item no cabeçalho de segurança deve ser um wsse:Timestamp</span><span class="sxs-lookup"><span data-stu-id="db74a-301">Same as lax except that the last item in the security header must be a wsse:Timestamp</span></span>|  
  
 <span data-ttu-id="db74a-302">O WCF suporta todos os quatro modos para layout de cabeçalho de segurança.</span><span class="sxs-lookup"><span data-stu-id="db74a-302">WCF supports all four modes for security header layout.</span></span> <span data-ttu-id="db74a-303">A estrutura do cabeçalho de segurança e os exemplos de mensagens para os modos de autenticação abaixo seguem o modo "Strict".</span><span class="sxs-lookup"><span data-stu-id="db74a-303">Security header structure and message examples for authentication modes below follow the "Strict" mode.</span></span>  
  
## <a name="2-common-message-security-parameters"></a><span data-ttu-id="db74a-304">2. Parâmetros comuns de segurança de mensagens</span><span class="sxs-lookup"><span data-stu-id="db74a-304">2. Common Message Security Parameters</span></span>  
 <span data-ttu-id="db74a-305">Esta seção fornece políticas de exemplo para cada modo de autenticação, juntamente com exemplos mostrando a estrutura do cabeçalho de segurança em mensagens trocadas pelo cliente e pelo serviço.</span><span class="sxs-lookup"><span data-stu-id="db74a-305">This section provides example policies for each authentication mode along with examples showing security header structure in messages exchanged by client and service.</span></span>  
  
### <a name="61-transport-protection"></a><span data-ttu-id="db74a-306">6.1 Proteção de transporte</span><span class="sxs-lookup"><span data-stu-id="db74a-306">6.1 Transport Protection</span></span>  
 <span data-ttu-id="db74a-307">O WCF fornece cinco modos de autenticação que usam transporte seguro para proteger mensagens; UserNameOverTransport, CertificateOverTransport, KerberosOverTransport, IssuedTokenOverTransport e SspiNegotiatedOverTransport.</span><span class="sxs-lookup"><span data-stu-id="db74a-307">WCF provides five authentication modes that use secure transport to protect messages; UserNameOverTransport, CertificateOverTransport, KerberosOverTransport, IssuedTokenOverTransport and SspiNegotiatedOverTransport.</span></span>  
  
 <span data-ttu-id="db74a-308">Esses modos de autenticação são construídos usando a vinculação de transporte descrita na SecurityPolicy.</span><span class="sxs-lookup"><span data-stu-id="db74a-308">These authentication modes are constructed using the transport binding described in SecurityPolicy.</span></span> <span data-ttu-id="db74a-309">Para o modo de autenticação UserNameOverTransport, o UsernameToken é um token de suporte assinado.</span><span class="sxs-lookup"><span data-stu-id="db74a-309">For the UserNameOverTransport authentication mode the UsernameToken is a signed supporting token.</span></span> <span data-ttu-id="db74a-310">Para os outros modos de autenticação, o token aparece como um token de endossamento assinado.</span><span class="sxs-lookup"><span data-stu-id="db74a-310">For the other authentication modes the token appears as a signed endorsing token.</span></span> <span data-ttu-id="db74a-311">O apêndice C.1.2 e C.1.3 da SecurityPolicy descrevem o layout do cabeçalho de segurança em detalhes.</span><span class="sxs-lookup"><span data-stu-id="db74a-311">Appendix C.1.2 and C.1.3 of SecurityPolicy describe the security header layout in detail.</span></span> <span data-ttu-id="db74a-312">O exemplo a seguir, os cabeçalhos de segurança mostram o layout Strict para um determinado modo de autenticação.</span><span class="sxs-lookup"><span data-stu-id="db74a-312">The following example security headers show the Strict layout for a given authentication mode.</span></span>  
  
 <span data-ttu-id="db74a-313">O valor da propriedade "Chaves Derivadas" para os tokens em todos os casos é "falso".</span><span class="sxs-lookup"><span data-stu-id="db74a-313">The value of the "Derived Keys" property for the tokens in all cases is "false".</span></span>  
  
 <span data-ttu-id="db74a-314">Os valores das várias propriedades da ligação de transporte são os seguintes:</span><span class="sxs-lookup"><span data-stu-id="db74a-314">The values of the various properties of the transport binding are as follows:</span></span>  
  
 <span data-ttu-id="db74a-315">Carimbo de tempo: verdadeiro</span><span class="sxs-lookup"><span data-stu-id="db74a-315">Timestamp: true</span></span>  
  
 <span data-ttu-id="db74a-316">Layout do cabeçalho de segurança: rigoroso</span><span class="sxs-lookup"><span data-stu-id="db74a-316">Security Header Layout: Strict</span></span>  
  
 <span data-ttu-id="db74a-317">Suíte algoritmo: Basic256</span><span class="sxs-lookup"><span data-stu-id="db74a-317">Algorithm Suite: Basic256</span></span>  
  
#### <a name="611-usernameovertransport"></a><span data-ttu-id="db74a-318">6.1.1 Nome de usuárioOverTransport</span><span class="sxs-lookup"><span data-stu-id="db74a-318">6.1.1 UsernameOverTransport</span></span>  
 <span data-ttu-id="db74a-319">Com este modo de autenticação, o cliente autentica com um Token de nome de usuário que aparece na camada SOAP como um token de suporte assinado que é sempre enviado do iniciador para o destinatário.</span><span class="sxs-lookup"><span data-stu-id="db74a-319">With this authentication mode, the client authenticates with a Username Token which appears at the SOAP layer as a signed supporting token that is always sent from the initiator to the recipient.</span></span> <span data-ttu-id="db74a-320">O serviço é autenticado usando um certificado X.509 na camada de transporte.</span><span class="sxs-lookup"><span data-stu-id="db74a-320">The service is authenticated using an X.509 certificate at the transport layer.</span></span> <span data-ttu-id="db74a-321">A ligação utilizada é uma ligação de transporte.</span><span class="sxs-lookup"><span data-stu-id="db74a-321">The binding used is a transport binding.</span></span>  
  
 <span data-ttu-id="db74a-322">Política</span><span class="sxs-lookup"><span data-stu-id="db74a-322">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id='UsernameOverTransport_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:TransportBinding >  
        <wsp:Policy>  
          <sp:TransportToken>  
            <wsp:Policy>  
              <sp:HttpsToken RequireClientCertificate='false' />
            </wsp:Policy>  
          </sp:TransportToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />
        </wsp:Policy>  
      </sp:TransportBinding>  
      <sp:SignedSupportingTokens >  
        <wsp:Policy>  
          <sp:UsernameToken
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
            <wsp:Policy>  
              <sp:WssUsernameToken10 />
            </wsp:Policy>  
          </sp:UsernameToken>  
        </wsp:Policy>  
      </sp:SignedSupportingTokens>  
      <sp:Wss11 >  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />
          <sp:MustSupportRefIssuerSerial />
          <sp:MustSupportRefThumbprint />
          <sp:MustSupportRefEncryptedKey />
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10 >  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />
          <sp:RequireClientEntropy />
          <sp:RequireServerEntropy />
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
 <span data-ttu-id="db74a-323">Layout do cabeçalho de segurança</span><span class="sxs-lookup"><span data-stu-id="db74a-323">Security Header Layout</span></span>  
  
 <span data-ttu-id="db74a-324">Solicitação</span><span class="sxs-lookup"><span data-stu-id="db74a-324">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wsse:UsernameToken>  
  ...  
  </wsse:UsernameToken>  
</wsse:Security>  
```  
  
 <span data-ttu-id="db74a-325">Resposta</span><span class="sxs-lookup"><span data-stu-id="db74a-325">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
#### <a name="612-certificateovertransport"></a><span data-ttu-id="db74a-326">6.1.2 Certificadosobre transporte</span><span class="sxs-lookup"><span data-stu-id="db74a-326">6.1.2 CertificateOverTransport</span></span>  
 <span data-ttu-id="db74a-327">Com este modo de autenticação, o cliente autentica usando um certificado X.509 que aparece na camada SOAP como um token de suporte de endossamento que é sempre enviado do iniciador para o destinatário.</span><span class="sxs-lookup"><span data-stu-id="db74a-327">With this authentication mode the client authenticates using an X.509 certificate which appears at the SOAP layer as an endorsing supporting token that is always sent from the initiator to the recipient.</span></span> <span data-ttu-id="db74a-328">O serviço é autenticado usando um certificado X.509 na camada de transporte.</span><span class="sxs-lookup"><span data-stu-id="db74a-328">The service is authenticated using an X.509 certificate at the transport layer.</span></span> <span data-ttu-id="db74a-329">A ligação utilizada é uma ligação de transporte.</span><span class="sxs-lookup"><span data-stu-id="db74a-329">The binding used is a transport binding.</span></span>  
  
 <span data-ttu-id="db74a-330">Política</span><span class="sxs-lookup"><span data-stu-id="db74a-330">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id='CertificateOverTransport_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:TransportBinding xmlns:sp='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy' >  
        <wsp:Policy>  
          <sp:TransportToken>  
            <wsp:Policy>  
             <sp:HttpsToken RequireClientCertificate='false' />
            </wsp:Policy>  
          </sp:TransportToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />
        </wsp:Policy>  
      </sp:TransportBinding>  
      <sp:EndorsingSupportingTokens>  
        <wsp:Policy>  
          <sp:X509Token
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
            <wsp:Policy>  
              <sp:RequireThumbprintReference />
              <sp:WssX509V3Token10 />
            </wsp:Policy>  
          </sp:X509Token>  
          <sp:SignedParts>  
            <sp:Header Name='To'
Namespace='http://www.w3.org/2005/08/addressing' />
          </sp:SignedParts>  
        </wsp:Policy>  
      </sp:EndorsingSupportingTokens>  
      <sp:Wss11>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />
          <sp:MustSupportRefIssuerSerial />
          <sp:MustSupportRefThumbprint />
          <sp:MustSupportRefEncryptedKey />
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />
          <sp:RequireClientEntropy />
          <sp:RequireServerEntropy />
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
 <span data-ttu-id="db74a-331">Layout do cabeçalho de segurança</span><span class="sxs-lookup"><span data-stu-id="db74a-331">Security Header Layout</span></span>  
  
 <span data-ttu-id="db74a-332">Solicitação</span><span class="sxs-lookup"><span data-stu-id="db74a-332">Request</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wse:Timestamp u:Id="_0">  
  ...  
  </wse:Timestamp>  
  <wsse:BinarySecurityToken>  
  ...  
  </wsse:BinarySecurityToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
</wsse:Security>  
```  
  
 <span data-ttu-id="db74a-333">Resposta</span><span class="sxs-lookup"><span data-stu-id="db74a-333">Response</span></span>  
  
```xml  
<o:Security>  
  <u:Timestamp u:Id="_0">  
  ...  
  </u:Timestamp>  
</o:Security>  
```  
  
#### <a name="613-issuedtokenovertransport"></a><span data-ttu-id="db74a-334">6.1.3 EmitidoTokenOverTransport</span><span class="sxs-lookup"><span data-stu-id="db74a-334">6.1.3 IssuedTokenOverTransport</span></span>  
 <span data-ttu-id="db74a-335">Com este modo de autenticação, o cliente não autentica o serviço, como tal, mas apresenta um token emitido por um Security Token Service (STS) e comprova o conhecimento de uma chave compartilhada.</span><span class="sxs-lookup"><span data-stu-id="db74a-335">With this authentication mode the client does not authenticate to the service, as such, but rather presents a token issued by a Security Token Service (STS) and proves knowledge of a shared key.</span></span> <span data-ttu-id="db74a-336">O token emitido aparece na camada SOAP como um token de suporte de endossamento que é sempre enviado do iniciador para o destinatário.</span><span class="sxs-lookup"><span data-stu-id="db74a-336">The issued token appears at the SOAP layer as an endorsing supporting token that is always sent from the initiator to the recipient.</span></span> <span data-ttu-id="db74a-337">O serviço é autenticado usando um certificado X.509 na camada de transporte.</span><span class="sxs-lookup"><span data-stu-id="db74a-337">The service is authenticated using an X.509 certificate at the transport layer.</span></span> <span data-ttu-id="db74a-338">A ligação é uma ligação de transporte.</span><span class="sxs-lookup"><span data-stu-id="db74a-338">The binding is a transport binding.</span></span>  
  
 <span data-ttu-id="db74a-339">Política</span><span class="sxs-lookup"><span data-stu-id="db74a-339">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id='IssuedTokenOverTransport_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:TransportBinding >  
        <wsp:Policy>  
          <sp:TransportToken>  
            <wsp:Policy>  
              <sp:HttpsToken RequireClientCertificate='false' />
            </wsp:Policy>  
          </sp:TransportToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />
        </wsp:Policy>  
      </sp:TransportBinding>  
      <sp:EndorsingSupportingTokens>  
        <wsp:Policy>  
          <sp:IssuedToken
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
            <sp:RequestSecurityTokenTemplate>  
              <wst:KeyType>  
              http://schemas.xmlsoap.org/ws/2005/02/trust/SymmetricKey  
              </wst:KeyType>
            </sp:RequestSecurityTokenTemplate>  
            <wsp:Policy>  
              <sp:RequireInternalReference />
            </wsp:Policy>  
          </sp:IssuedToken>  
          <sp:SignedParts>  
            <sp:Header Name='To'
Namespace='http://www.w3.org/2005/08/addressing' />
          </sp:SignedParts>  
        </wsp:Policy>  
      </sp:EndorsingSupportingTokens>  
      <sp:Wss11>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />
          <sp:MustSupportRefIssuerSerial />
          <sp:MustSupportRefThumbprint />
          <sp:MustSupportRefEncryptedKey />
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />
          <sp:RequireClientEntropy />
          <sp:RequireServerEntropy />
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
 <span data-ttu-id="db74a-340">Layout do cabeçalho de segurança</span><span class="sxs-lookup"><span data-stu-id="db74a-340">Security Header Layout</span></span>  
  
 <span data-ttu-id="db74a-341">Solicitação</span><span class="sxs-lookup"><span data-stu-id="db74a-341">Request</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1" >  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <saml:Assertion>  
  ...  
  </saml:Assertion>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
</wsse:Security>  
```  
  
 <span data-ttu-id="db74a-342">Resposta</span><span class="sxs-lookup"><span data-stu-id="db74a-342">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
#### <a name="614-kerberosovertransport"></a><span data-ttu-id="db74a-343">6.1.4 KerberosOverTransport</span><span class="sxs-lookup"><span data-stu-id="db74a-343">6.1.4 KerberosOverTransport</span></span>  
 <span data-ttu-id="db74a-344">Com este modo de autenticação, o cliente autentica-se ao serviço usando um bilhete Kerberos.</span><span class="sxs-lookup"><span data-stu-id="db74a-344">With this authentication mode the client authenticates to the service using a Kerberos ticket.</span></span> <span data-ttu-id="db74a-345">O token Kerberos aparece na camada SOAP como um token de suporte endossando.</span><span class="sxs-lookup"><span data-stu-id="db74a-345">The Kerberos token appears at the SOAP layer as an endorsing supporting token.</span></span> <span data-ttu-id="db74a-346">O serviço é autenticado usando um certificado X.509 na camada de transporte.</span><span class="sxs-lookup"><span data-stu-id="db74a-346">The service is authenticated using an X.509 certificate at the transport layer.</span></span> <span data-ttu-id="db74a-347">A ligação é uma ligação de transporte.</span><span class="sxs-lookup"><span data-stu-id="db74a-347">The binding is a transport binding.</span></span>  
  
 <span data-ttu-id="db74a-348">Política</span><span class="sxs-lookup"><span data-stu-id="db74a-348">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id='KerberosOverTransport_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:TransportBinding>  
        <wsp:Policy>  
          <sp:TransportToken>  
            <wsp:Policy>  
              <sp:HttpsToken RequireClientCertificate='false' />
            </wsp:Policy>  
          </sp:TransportToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic128 />
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />
        </wsp:Policy>  
      </sp:TransportBinding>  
      <sp:EndorsingSupportingTokens>  
        <wsp:Policy>  
          <sp:KerberosToken  
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/Once' >  
            <wsp:Policy>  
              <sp:WssGssKerberosV5ApReqToken11 />
            </wsp:Policy>  
          </sp:KerberosToken>  
          <sp:SignedParts>  
            <sp:Header Name='To'
Namespace='http://www.w3.org/2005/08/addressing' />
          </sp:SignedParts>  
        </wsp:Policy>  
      </sp:EndorsingSupportingTokens>  
      <sp:Wss11>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />
          <sp:MustSupportRefIssuerSerial />
          <sp:MustSupportRefThumbprint />
          <sp:MustSupportRefEncryptedKey />
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />
          <sp:RequireClientEntropy />
          <sp:RequireServerEntropy />
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
 <span data-ttu-id="db74a-349">Layout do cabeçalho de segurança</span><span class="sxs-lookup"><span data-stu-id="db74a-349">Security Header Layout</span></span>  
  
 <span data-ttu-id="db74a-350">Solicitação</span><span class="sxs-lookup"><span data-stu-id="db74a-350">Request</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1" >  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wsse:BinarySecurityToken ValueType="...#GSS_Kerberosv5_AP_REQ">  
  ...  
  </wsse:BinarySecurityToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
</wsse:Security>  
```  
  
 <span data-ttu-id="db74a-351">Resposta</span><span class="sxs-lookup"><span data-stu-id="db74a-351">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
#### <a name="615-sspinegotiatedovertransport"></a><span data-ttu-id="db74a-352">6.1.5 SspiNegociedOverTransport</span><span class="sxs-lookup"><span data-stu-id="db74a-352">6.1.5 SspiNegotiatedOverTransport</span></span>  
 <span data-ttu-id="db74a-353">Com este modo, um protocolo de negociação é usado para executar a autenticação do cliente e do servidor.</span><span class="sxs-lookup"><span data-stu-id="db74a-353">With this mode a negotiation protocol is used to perform client and server authentication.</span></span> <span data-ttu-id="db74a-354">Kerberos é usado se possível, caso contrário NTLM.</span><span class="sxs-lookup"><span data-stu-id="db74a-354">Kerberos is used if possible, otherwise NTLM.</span></span> <span data-ttu-id="db74a-355">O SCT resultante aparece na camada SOAP como um token de suporte de endossamento que é sempre enviado do iniciador para o destinatário.</span><span class="sxs-lookup"><span data-stu-id="db74a-355">The resulting SCT appears at the SOAP layer as an endorsing supporting token that is always sent from initiator to recipient.</span></span> <span data-ttu-id="db74a-356">O serviço é autenticado adicionalmente na camada de transporte por um certificado X.509.</span><span class="sxs-lookup"><span data-stu-id="db74a-356">The service is additionally authenticated at the transport layer by an X.509 certificate.</span></span> <span data-ttu-id="db74a-357">A ligação utilizada é uma ligação de transporte.</span><span class="sxs-lookup"><span data-stu-id="db74a-357">The binding used is a transport binding.</span></span> <span data-ttu-id="db74a-358">"SPNEGO" (negociação) descreve como o WCF usa o protocolo de negociação binária SSPI com o WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="db74a-358">"SPNEGO" (negotiation) describes how WCF uses SSPI binary negotiation protocol with WS-Trust.</span></span> <span data-ttu-id="db74a-359">Os exemplos de cabeçalho de segurança nesta seção são após o SCT ter sido estabelecido através do aperto de mão SPNEGO.</span><span class="sxs-lookup"><span data-stu-id="db74a-359">Security header examples in this section are after the SCT has been established through the SPNEGO handshake.</span></span>  
  
 <span data-ttu-id="db74a-360">Política</span><span class="sxs-lookup"><span data-stu-id="db74a-360">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id='SspiNegotiatedOverTransport_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:TransportBinding>  
        <wsp:Policy>  
          <sp:TransportToken>  
            <wsp:Policy>  
              <sp:HttpsToken RequireClientCertificate='false' />
            </wsp:Policy>  
          </sp:TransportToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />
        </wsp:Policy>  
      </sp:TransportBinding>  
      <sp:EndorsingSupportingTokens>  
        <wsp:Policy>  
          <sp:SpnegoContextToken
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
            <wsp:Policy />
          </sp:SpnegoContextToken>  
          <sp:SignedParts>  
            <sp:Header Name='To'
Namespace='http://www.w3.org/2005/08/addressing' />
          </sp:SignedParts>  
        </wsp:Policy>  
      </sp:EndorsingSupportingTokens>  
      <sp:Wss11>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />
          <sp:MustSupportRefIssuerSerial />
          <sp:MustSupportRefThumbprint />
          <sp:MustSupportRefEncryptedKey />
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />
          <sp:RequireClientEntropy />
          <sp:RequireServerEntropy />
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
### <a name="security-header-examples"></a><span data-ttu-id="db74a-361">Exemplos de cabeçalho de segurança</span><span class="sxs-lookup"><span data-stu-id="db74a-361">Security Header Examples</span></span>  
 <span data-ttu-id="db74a-362">Uma vez que o Token de Contexto de Segurança é estabelecido através do aperto de mão SPNEGO usando a Negociação Binária WS-Trust, as mensagens do aplicativo têm cabeçalhos de segurança com a seguinte estrutura.</span><span class="sxs-lookup"><span data-stu-id="db74a-362">Once the Security Context Token is established through SPNEGO handshake using WS-Trust Binary Negotiation, the application messages have security headers with the following structure.</span></span>  
  
 <span data-ttu-id="db74a-363">Solicitação</span><span class="sxs-lookup"><span data-stu-id="db74a-363">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wssc:SecurityContextToken u:Id="uuid-2202746a-7725-453d-8747-809cb718dab0-29" >  
  ...  
  </wssc:SecurityContextToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
</wsse:Security>  
```  
  
 <span data-ttu-id="db74a-364">Resposta</span><span class="sxs-lookup"><span data-stu-id="db74a-364">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
### <a name="62-using-x509-certificates-for-service-authentication"></a><span data-ttu-id="db74a-365">6.2 Usando certificados X.509 para autenticação de serviço</span><span class="sxs-lookup"><span data-stu-id="db74a-365">6.2 Using X.509 Certificates for Service Authentication</span></span>  
 <span data-ttu-id="db74a-366">Esta seção descreve os seguintes modos de autenticação: MutualCertificate WSS1.0, Mutual CertificateDuplex, MutualCertificate WSS1.1, AnonymousForCertificate, UserNameForCertificate e IssuedTokenForCertificate.</span><span class="sxs-lookup"><span data-stu-id="db74a-366">This section describes the following authentication modes: MutualCertificate WSS1.0, Mutual CertificateDuplex, MutualCertificate WSS1.1, AnonymousForCertificate, UserNameForCertificate and IssuedTokenForCertificate.</span></span>  
  
#### <a name="621-mutualcertificate-wss10"></a><span data-ttu-id="db74a-367">6.2.1 Certificado Mútuo WSS1.0</span><span class="sxs-lookup"><span data-stu-id="db74a-367">6.2.1 MutualCertificate WSS1.0</span></span>  
 <span data-ttu-id="db74a-368">Com este modo de autenticação, o cliente autentica usando um certificado X.509 que aparece na camada SOAP como token iniciador.</span><span class="sxs-lookup"><span data-stu-id="db74a-368">With this authentication mode the client authenticates using an X.509 certificate which appears at the SOAP layer as the initiator token.</span></span> <span data-ttu-id="db74a-369">O serviço também é autenticado usando um certificado X.509.</span><span class="sxs-lookup"><span data-stu-id="db74a-369">The service is also authenticated using an X.509 certificate.</span></span>  
  
 <span data-ttu-id="db74a-370">A vinculação utilizada é uma vinculação assimétrica com os seguintes valores de propriedade:</span><span class="sxs-lookup"><span data-stu-id="db74a-370">The binding used is an asymmetric binding with the following property values:</span></span>  
  
 <span data-ttu-id="db74a-371">Token iniciador: o certificado X.509 do cliente, com o modo de inclusão definido como .../IncludeToken/AlwaysToRecipient</span><span class="sxs-lookup"><span data-stu-id="db74a-371">Initiator Token: the client’s X.509 certificate, with inclusion mode set to …/IncludeToken/AlwaysToRecipient</span></span>  
  
 <span data-ttu-id="db74a-372">Token destinatário: certificado X.509 do servidor, com o modo de inclusão é definido .../IncludeToken/Never</span><span class="sxs-lookup"><span data-stu-id="db74a-372">Recipient Token: Server’s X.509 Certificate, with inclusion mode is set …/IncludeToken/Never</span></span>  
  
 <span data-ttu-id="db74a-373">Proteção de tokens: falso</span><span class="sxs-lookup"><span data-stu-id="db74a-373">Token Protection: False</span></span>  
  
 <span data-ttu-id="db74a-374">Cabeçalho inteiro e assinaturas do corpo: Verdadeiro</span><span class="sxs-lookup"><span data-stu-id="db74a-374">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="db74a-375">Ordem de proteção: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="db74a-375">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="db74a-376">Assinar assinatura: True</span><span class="sxs-lookup"><span data-stu-id="db74a-376">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="db74a-377">Política</span><span class="sxs-lookup"><span data-stu-id="db74a-377">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id='MutualCertificate_WSS10_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:AsymmetricBinding>  
        <wsp:Policy>  
          <sp:InitiatorToken>  
            <wsp:Policy>  
              <sp:X509Token
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
                <wsp:Policy>  
                  <sp:WssX509V3Token10 />
                </wsp:Policy>  
              </sp:X509Token>  
            </wsp:Policy>  
          </sp:InitiatorToken>  
          <sp:RecipientToken>  
            <wsp:Policy>  
              <sp:X509Token
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/Never' >  
                <wsp:Policy>  
                  <sp:WssX509V3Token10 />
                </wsp:Policy>  
              </sp:X509Token>  
            </wsp:Policy>  
          </sp:RecipientToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />
          <sp:EncryptSignature />
          <sp:OnlySignEntireHeadersAndBody />
        </wsp:Policy>  
      </sp:AsymmetricBinding>  
      <sp:Wss10>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />
          <sp:MustSupportRefIssuerSerial />
        </wsp:Policy>  
      </sp:Wss10>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />
          <sp:RequireClientEntropy />
          <sp:RequireServerEntropy />
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="db74a-378">Exemplos de cabeçalho de segurança: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="db74a-378">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="db74a-379">Solicitação</span><span class="sxs-lookup"><span data-stu-id="db74a-379">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wsse:BinarySecurityToken>  
  ...  
  </wsse:BinarySecurityToken>  
  <xenc:EncryptedKey>  
  ...  
    <xenc:ReferenceList>  
    ...  
    </xenc:ReferenceList>  
  </xenc:EncryptedKey>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="db74a-380">Resposta</span><span class="sxs-lookup"><span data-stu-id="db74a-380">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
    <xenc:ReferenceList>  
    ...  
    </xenc:ReferenceList>  
  </xenc:EncryptedKey>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="db74a-381">Exemplos de cabeçalho de segurança: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="db74a-381">Security Header Examples: EncryptBeforeSign</span></span>  
  
 <span data-ttu-id="db74a-382">Solicitação</span><span class="sxs-lookup"><span data-stu-id="db74a-382">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wsse:BinarySecurityToken>  
  ...  
  </wsse:BinarySecurityToken>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 <span data-ttu-id="db74a-383">Resposta</span><span class="sxs-lookup"><span data-stu-id="db74a-383">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
#### <a name="622-mutualcertificateduplex"></a><span data-ttu-id="db74a-384">6.2.2 MutualCertificateDuplex</span><span class="sxs-lookup"><span data-stu-id="db74a-384">6.2.2 MutualCertificateDuplex</span></span>  
 <span data-ttu-id="db74a-385">Com este modo de autenticação, o cliente autentica usando um certificado X.509 que aparece na camada SOAP como token iniciador.</span><span class="sxs-lookup"><span data-stu-id="db74a-385">With this authentication mode the client authenticates using an X.509 certificate which appears at the SOAP layer as the initiator token.</span></span> <span data-ttu-id="db74a-386">O serviço também é autenticado usando um certificado X.509.</span><span class="sxs-lookup"><span data-stu-id="db74a-386">The service is also authenticated using an X.509 certificate.</span></span>  
  
 <span data-ttu-id="db74a-387">A vinculação utilizada é uma vinculação assimétrica com os seguintes valores de propriedade:</span><span class="sxs-lookup"><span data-stu-id="db74a-387">The binding used is an asymmetric binding with the following property values:</span></span>  
  
 <span data-ttu-id="db74a-388">Token iniciador: certificado X509 do cliente, o modo de inclusão está definido como .../IncludeToken/AlwaysToRecipient</span><span class="sxs-lookup"><span data-stu-id="db74a-388">Initiator Token: Client’s X509 Certificate, inclusion mode is set to …/IncludeToken/AlwaysToRecipient</span></span>  
  
 <span data-ttu-id="db74a-389">Token destinatário: Certificado X509 do servidor, o modo de inclusão está definido como .../IncludeToken/AlwaysToInitiator</span><span class="sxs-lookup"><span data-stu-id="db74a-389">Recipient Token: Server’s X509 Certificate, inclusion mode is set to …/IncludeToken/AlwaysToInitiator</span></span>  
  
 <span data-ttu-id="db74a-390">Proteção de tokens: falso</span><span class="sxs-lookup"><span data-stu-id="db74a-390">Token Protection: False</span></span>  
  
 <span data-ttu-id="db74a-391">Cabeçalho inteiro e assinaturas do corpo: Verdadeiro</span><span class="sxs-lookup"><span data-stu-id="db74a-391">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="db74a-392">Ordem de proteção: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="db74a-392">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="db74a-393">Assinar assinatura: True</span><span class="sxs-lookup"><span data-stu-id="db74a-393">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="db74a-394">Política</span><span class="sxs-lookup"><span data-stu-id="db74a-394">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id='MutualCertificateDuplex_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:AsymmetricBinding>  
        <wsp:Policy>  
          <sp:InitiatorToken>  
            <wsp:Policy>  
              <sp:X509Token
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
                <wsp:Policy>  
                  <sp:WssX509V3Token10 />
                </wsp:Policy>  
              </sp:X509Token>  
            </wsp:Policy>  
          </sp:InitiatorToken>  
          <sp:RecipientToken>  
            <wsp:Policy>  
              <sp:X509Token
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToInitiator' >  
                <wsp:Policy>  
                  <sp:WssX509V3Token10 />
                </wsp:Policy>  
              </sp:X509Token>  
            </wsp:Policy>  
          </sp:RecipientToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />
          <sp:EncryptSignature />
          <sp:OnlySignEntireHeadersAndBody />
        </wsp:Policy>  
      </sp:AsymmetricBinding>  
      <sp:Wss10>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />
          <sp:MustSupportRefIssuerSerial />
        </wsp:Policy>  
      </sp:Wss10>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />
          <sp:RequireClientEntropy />
          <sp:RequireServerEntropy />
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="db74a-395">Exemplos de cabeçalho de segurança: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="db74a-395">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="db74a-396">Solicitação e Resposta</span><span class="sxs-lookup"><span data-stu-id="db74a-396">Request and Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wsse:BinarySecurityToken>  
  ...  
  </wsse:BinarySecurityToken>  
  <xenc:EncryptedKey>  
  ...  
    <xenc:ReferenceList>  
    ...  
    </xenc:ReferenceList>  
  </xenc:EncryptedKey>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="db74a-397">Exemplos de cabeçalho de segurança: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="db74a-397">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="db74a-398">Solicitação e Resposta</span><span class="sxs-lookup"><span data-stu-id="db74a-398">Request and Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wsse:BinarySecurityToken>  
  ...  
  </wsse:BinarySecurityToken>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
#### <a name="623-using-symmetricbinding-with-x509-service-authentication"></a><span data-ttu-id="db74a-399">6.2.3 Usando simétricovincule autenticação de serviço X.509</span><span class="sxs-lookup"><span data-stu-id="db74a-399">6.2.3 Using SymmetricBinding with X.509 Service Authentication</span></span>  
 <span data-ttu-id="db74a-400">"WSS10" forneceu suporte limitado para cenários com tokens X509.</span><span class="sxs-lookup"><span data-stu-id="db74a-400">"WSS10" provided limited support for scenarios with X509 tokens.</span></span> <span data-ttu-id="db74a-401">Por exemplo, não havia como fornecer proteção de assinatura e criptografia para mensagens usando apenas o token de serviço X509.</span><span class="sxs-lookup"><span data-stu-id="db74a-401">For example, there was no way to provide signature and encryption protection for messages using only service X509 token.</span></span> <span data-ttu-id="db74a-402">"WSS11" introduziu o uso do EncryptedKey como um token simétrico.</span><span class="sxs-lookup"><span data-stu-id="db74a-402">"WSS11" introduced the usage of EncryptedKey as a symmetric token.</span></span> <span data-ttu-id="db74a-403">Agora, uma chave temporária criptografada para o certificado X.509 do serviço pode ser usada tanto para proteção de mensagens de solicitação quanto de resposta.</span><span class="sxs-lookup"><span data-stu-id="db74a-403">Now a temporary key encrypted for the service's X.509 certificate could be used for both request and response messages protection.</span></span> <span data-ttu-id="db74a-404">Os modos de autenticação descritos na seção 6.4 abaixo usam este padrão.</span><span class="sxs-lookup"><span data-stu-id="db74a-404">The authentication modes described in the section 6.4 below use this pattern.</span></span>  
  
 <span data-ttu-id="db74a-405">O WS-SecurityPolicy descreve esse padrão usando o token SymetricBinding with Service X509 como o token de proteção.</span><span class="sxs-lookup"><span data-stu-id="db74a-405">WS-SecurityPolicy describes this pattern using SymmetricBinding with Service X509 token as the protection token.</span></span>  
  
 <span data-ttu-id="db74a-406">Modos de autenticação AnonymousForCertificate, UsernameForCertificate, MutualCertificate WSS11 e IssuedTokenForCertificate todos usam uma instância semelhante de sp:SimétricoBinding com os seguintes valores de propriedade:</span><span class="sxs-lookup"><span data-stu-id="db74a-406">Authentication modes AnonymousForCertificate, UsernameForCertificate, MutualCertificate WSS11 and IssuedTokenForCertificate all use a similar instance of sp:SymmetricBinding with the following property values:</span></span>  
  
 <span data-ttu-id="db74a-407">Token de proteção: certificado X509 do servidor, o modo de inclusão está definido como .../IncludeToken/Never</span><span class="sxs-lookup"><span data-stu-id="db74a-407">Protection Token: Server’s X509 Certificate, inclusion mode is set to .../IncludeToken/Never</span></span>  
<span data-ttu-id="db74a-408">Proteção de tokens: falso</span><span class="sxs-lookup"><span data-stu-id="db74a-408">Token Protection: False</span></span>  
  
 <span data-ttu-id="db74a-409">Cabeçalho inteiro e assinaturas do corpo: Verdadeiro</span><span class="sxs-lookup"><span data-stu-id="db74a-409">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="db74a-410">Ordem de proteção: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="db74a-410">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="db74a-411">Assinar assinatura: True</span><span class="sxs-lookup"><span data-stu-id="db74a-411">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="db74a-412">Os modos de autenticação acima só diferem pelos tokens de suporte que eles usam.</span><span class="sxs-lookup"><span data-stu-id="db74a-412">The above authentication modes only differ by the supporting tokens they use.</span></span> <span data-ttu-id="db74a-413">AnonymousForCertificate não tem nenhum token de suporte, MutualCertificate WSS 1.1 tem o certificado X509 do cliente como um endossando tokens de suporte, UserNameForCertificate tem um Token UserName como um token de suporte assinado e O EmissãoTokenForCertificate tem o token emitido como um token de suporte de suporte.</span><span class="sxs-lookup"><span data-stu-id="db74a-413">AnonymousForCertificate does not have any supporting tokens, MutualCertificate WSS 1.1 has the client’s X509 certificate as an endorsing supporting tokens, UserNameForCertificate has a UserName Token as a signed supporting token and IssuedTokenForCertificate has the issued token as an endorsing supporting token.</span></span>  
  
 <span data-ttu-id="db74a-414">Política</span><span class="sxs-lookup"><span data-stu-id="db74a-414">Policy</span></span>  
  
 <span data-ttu-id="db74a-415">Ligação simétrica</span><span class="sxs-lookup"><span data-stu-id="db74a-415">Symmetric Binding</span></span>  
  
```xml  
<wsp:Policy wsu:Id='SymmetricCert_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:SymmetricBinding>  
        <wsp:Policy>  
          <sp:ProtectionToken>  
            <wsp:Policy>  
              <sp:X509Token
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/Never' >  
                <wsp:Policy>  
                  <sp:RequireDerivedKeys />
                  <sp:RequireThumbprintReference />
                  <sp:WssX509V3Token10 />
                </wsp:Policy>  
              </sp:X509Token>  
            </wsp:Policy>  
          </sp:ProtectionToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />
          <sp:EncryptSignature />
          <sp:OnlySignEntireHeadersAndBody />  
        </wsp:Policy>  
      </sp:SymmetricBinding>  
      <!-- Supporting Token Assertions appear here -->  
      ...  
      <sp:Wss11>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />
          <sp:MustSupportRefIssuerSerial />
          <sp:MustSupportRefThumbprint />
          <sp:MustSupportRefEncryptedKey />
          <sp:RequireSignatureConfirmation />
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />
          <sp:RequireClientEntropy />
          <sp:RequireServerEntropy />
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
#### <a name="624-anonymousforcertificate"></a><span data-ttu-id="db74a-416">6.2.4 Certificado anônimo</span><span class="sxs-lookup"><span data-stu-id="db74a-416">6.2.4 AnonymousForCertificate</span></span>  
 <span data-ttu-id="db74a-417">Com este modo de autenticação, o cliente é anônimo e o serviço é autenticado usando um certificado X.509.</span><span class="sxs-lookup"><span data-stu-id="db74a-417">With this authentication mode the client is anonymous and the service is authenticated using an X.509 certificate.</span></span> <span data-ttu-id="db74a-418">A vinculação utilizada é uma instância de vinculação simétrica descrita em 6.4.2.</span><span class="sxs-lookup"><span data-stu-id="db74a-418">The binding used is an instance of symmetric binding as described in 6.4.2.</span></span>  
  
 <span data-ttu-id="db74a-419">Política</span><span class="sxs-lookup"><span data-stu-id="db74a-419">Policy</span></span>  
  
 <span data-ttu-id="db74a-420">Consulte "Política" em 6.2.3 acima para obter detalhes vinculativos</span><span class="sxs-lookup"><span data-stu-id="db74a-420">See "Policy" in 6.2.3 above for binding details</span></span>  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="db74a-421">Exemplos de cabeçalho de segurança: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="db74a-421">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="db74a-422">Solicitação</span><span class="sxs-lookup"><span data-stu-id="db74a-422">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="db74a-423">Resposta</span><span class="sxs-lookup"><span data-stu-id="db74a-423">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="db74a-424">Exemplos de cabeçalho de segurança: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="db74a-424">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="db74a-425">Solicitação</span><span class="sxs-lookup"><span data-stu-id="db74a-425">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 <span data-ttu-id="db74a-426">Resposta</span><span class="sxs-lookup"><span data-stu-id="db74a-426">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wsse11:SignatureConfirmation />  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
#### <a name="625-usernameforcertificate"></a><span data-ttu-id="db74a-427">6.2.5 Nome de usuárioParacertificado</span><span class="sxs-lookup"><span data-stu-id="db74a-427">6.2.5 UserNameForCertificate</span></span>  
 <span data-ttu-id="db74a-428">Com este modo de autenticação, o cliente autentica ao serviço usando um Token de nome de usuário que aparece na camada SOAP como um token de suporte assinado.</span><span class="sxs-lookup"><span data-stu-id="db74a-428">With this authentication mode the client authenticates to the service using a Username Token which appears at the SOAP layer as a signed supporting token.</span></span> <span data-ttu-id="db74a-429">O serviço é autenticado ao cliente usando um certificado X.509.</span><span class="sxs-lookup"><span data-stu-id="db74a-429">The service authenticates to the client using an X.509 certificate.</span></span> <span data-ttu-id="db74a-430">A vinculação utilizada é uma vinculação simétrica com o token de proteção sendo uma chave gerada pelo cliente, criptografada com a chave pública do serviço.</span><span class="sxs-lookup"><span data-stu-id="db74a-430">The binding used is a symmetric binding with the protection token being a key generated by the client, encrypted with the public key of the service.</span></span>  
  
 <span data-ttu-id="db74a-431">Política</span><span class="sxs-lookup"><span data-stu-id="db74a-431">Policy</span></span>  
  
 <span data-ttu-id="db74a-432">Consulte "Política" em 6.2.3 acima para obter detalhes vinculativos</span><span class="sxs-lookup"><span data-stu-id="db74a-432">See "Policy" in 6.2.3 above for binding details</span></span>  
  
 <span data-ttu-id="db74a-433">Token de suporte assinado</span><span class="sxs-lookup"><span data-stu-id="db74a-433">Signed Supporting Token</span></span>  
  
```xml  
<sp:SignedSupportingTokens>  
  <wsp:Policy>  
    <sp:UsernameToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
      <wsp:Policy>  
        <sp:WssUsernameToken10 />
      </wsp:Policy>  
    </sp:UsernameToken>  
  </wsp:Policy>  
</sp:SignedSupportingTokens>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="db74a-434">Exemplos de cabeçalho de segurança: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="db74a-434">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="db74a-435">Solicitação</span><span class="sxs-lookup"><span data-stu-id="db74a-435">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="db74a-436">Resposta</span><span class="sxs-lookup"><span data-stu-id="db74a-436">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="db74a-437">Exemplos de cabeçalho de segurança: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="db74a-437">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="db74a-438">Solicitação</span><span class="sxs-lookup"><span data-stu-id="db74a-438">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 <span data-ttu-id="db74a-439">Resposta</span><span class="sxs-lookup"><span data-stu-id="db74a-439">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
#### <a name="626-mutualcertificate-wss-11"></a><span data-ttu-id="db74a-440">6.2.6 Certificado Mútuo (WSS 1.1)</span><span class="sxs-lookup"><span data-stu-id="db74a-440">6.2.6 MutualCertificate (WSS 1.1)</span></span>  
 <span data-ttu-id="db74a-441">Com este modo de autenticação, o cliente autentica usando um certificado X.509 que aparece na camada SOAP como um token de suporte de suporte endossando.</span><span class="sxs-lookup"><span data-stu-id="db74a-441">With this authentication mode the client authenticates using an X.509 certificate which appears at the SOAP layer as an endorsing supporting token.</span></span> <span data-ttu-id="db74a-442">O serviço também é autenticado usando um certificado X.509.</span><span class="sxs-lookup"><span data-stu-id="db74a-442">The service is also authenticated using an X.509 certificate.</span></span> <span data-ttu-id="db74a-443">A vinculação utilizada é uma vinculação simétrica com o token de proteção sendo uma chave gerada pelo cliente, criptografada com a chave pública do serviço.</span><span class="sxs-lookup"><span data-stu-id="db74a-443">The binding used is a symmetric binding with the protection token being a key generated by the client, encrypted with the public key of the service.</span></span>  
  
 <span data-ttu-id="db74a-444">Política</span><span class="sxs-lookup"><span data-stu-id="db74a-444">Policy</span></span>  
  
 <span data-ttu-id="db74a-445">Consulte Política em 6.2.3 para obter detalhes vinculativos</span><span class="sxs-lookup"><span data-stu-id="db74a-445">See Policy in 6.2.3 for binding details</span></span>  
  
 <span data-ttu-id="db74a-446">Endossando o Token de Suporte</span><span class="sxs-lookup"><span data-stu-id="db74a-446">Endorsing Supporting Token</span></span>  
  
```xml  
<sp:EndorsingSupportingTokens>  
  <wsp:Policy>  
    <sp:X509Token sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
      <wsp:Policy>  
        <sp:RequireThumbprintReference />
        <sp:WssX509V3Token10 />
      </wsp:Policy>  
    </sp:X509Token>  
  </wsp:Policy>  
</sp:EndorsingSupportingTokens>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="db74a-447">Exemplos de cabeçalho de segurança: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="db74a-447">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="db74a-448">Solicitação</span><span class="sxs-lookup"><span data-stu-id="db74a-448">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <wsse:BinarySecurityToken>  
  ...  
  </wsse:BinarySecurityToken>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="db74a-449">Resposta</span><span class="sxs-lookup"><span data-stu-id="db74a-449">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <wsse:BinarySecurityToken>  
  ...  
  </wsse:BinarySecurityToken>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="db74a-450">Exemplos de cabeçalho de segurança: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="db74a-450">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="db74a-451">Solicitação</span><span class="sxs-lookup"><span data-stu-id="db74a-451">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wsse:BinarySecurityToken>  
  ...  
  </wsse:BinarySecurityToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 <span data-ttu-id="db74a-452">Resposta</span><span class="sxs-lookup"><span data-stu-id="db74a-452">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wsse11:SignatureConfirmation />  
  <wsse11:SignatureConfirmation />  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
#### <a name="627-issuedtokenforcertificate"></a><span data-ttu-id="db74a-453">6.2.7 EmitidoTokenForCertificate</span><span class="sxs-lookup"><span data-stu-id="db74a-453">6.2.7 IssuedTokenForCertificate</span></span>  
 <span data-ttu-id="db74a-454">Com este modo de autenticação, o cliente não autentica o serviço, como tal, mas apresenta um token emitido por um STS e comprova o conhecimento de uma chave compartilhada.</span><span class="sxs-lookup"><span data-stu-id="db74a-454">With this authentication mode the client does not authenticate to the service, as such, but instead presents a token issued by a STS and proves knowledge of a shared key.</span></span> <span data-ttu-id="db74a-455">O token emitido aparece na camada SOAP como um token de suporte endossando.</span><span class="sxs-lookup"><span data-stu-id="db74a-455">The issued token appears at the SOAP layer as an endorsing supporting token.</span></span> <span data-ttu-id="db74a-456">O serviço é autenticado ao cliente usando um certificado X.509.</span><span class="sxs-lookup"><span data-stu-id="db74a-456">The service authenticates to the client using an X.509 certificate.</span></span> <span data-ttu-id="db74a-457">A vinculação utilizada é uma vinculação simétrica com o token de proteção sendo uma chave gerada pelo cliente, criptografada com a chave pública do serviço.</span><span class="sxs-lookup"><span data-stu-id="db74a-457">The binding used is a symmetric binding with the protection token being a key generated by the client, encrypted with the public key of the service.</span></span>  
  
 <span data-ttu-id="db74a-458">Política</span><span class="sxs-lookup"><span data-stu-id="db74a-458">Policy</span></span>  
  
 <span data-ttu-id="db74a-459">Consulte Política em 6.2.3 acima para obter detalhes vinculativos</span><span class="sxs-lookup"><span data-stu-id="db74a-459">See Policy in 6.2.3 above for binding details</span></span>  
  
 <span data-ttu-id="db74a-460">Endossando o Token de Suporte</span><span class="sxs-lookup"><span data-stu-id="db74a-460">Endorsing Supporting Token</span></span>  
  
```xml  
<sp:EndorsingSupportingTokens>  
  <wsp:Policy>  
    <sp:IssuedToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
      <sp:RequestSecurityTokenTemplate>  
        <wst:KeyType>  
http://schemas.xmlsoap.org/ws/2005/02/trust/SymmetricKey  
       </wst:KeyType>  
     </sp:RequestSecurityTokenTemplate>  
     <wsp:Policy>  
       <sp:RequireDerivedKeys />
       <sp:RequireInternalReference />
     </wsp:Policy>  
   </sp:IssuedToken>  
  </wsp:Policy>  
</sp:EndorsingSupportingTokens>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="db74a-461">Exemplos de cabeçalho de segurança: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="db74a-461">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="db74a-462">Solicitação</span><span class="sxs-lookup"><span data-stu-id="db74a-462">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <saml:Assertion>  
  ...  
  </saml:Assertion>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="db74a-463">Resposta</span><span class="sxs-lookup"><span data-stu-id="db74a-463">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="db74a-464">Exemplos de cabeçalho de segurança: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="db74a-464">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="db74a-465">Solicitação</span><span class="sxs-lookup"><span data-stu-id="db74a-465">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <saml:Assertion>  
  ...  
  </saml:Assertion>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 <span data-ttu-id="db74a-466">Resposta</span><span class="sxs-lookup"><span data-stu-id="db74a-466">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wsse11:SignatureConfirmation />  
  <wsse11:SignatureConfirmation />  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
## <a name="63-kerberos"></a><span data-ttu-id="db74a-467">6.3 Kerberos</span><span class="sxs-lookup"><span data-stu-id="db74a-467">6.3 Kerberos</span></span>  
 <span data-ttu-id="db74a-468">Com este modo de autenticação, o cliente autentica-se ao serviço usando um bilhete Kerberos.</span><span class="sxs-lookup"><span data-stu-id="db74a-468">With this authentication mode the client authenticates to the service using a Kerberos ticket.</span></span> <span data-ttu-id="db74a-469">Esse mesmo ticket também fornece autenticação do servidor.</span><span class="sxs-lookup"><span data-stu-id="db74a-469">That same ticket also provides server authentication.</span></span> <span data-ttu-id="db74a-470">A vinculação utilizada é uma ligação simétrica com as seguintes propriedades;</span><span class="sxs-lookup"><span data-stu-id="db74a-470">The binding used is a symmetric binding with the following properties;</span></span>  
  
 <span data-ttu-id="db74a-471">Token de proteção: Kerberos Ticket, modo de inclusão é definido como .../IncludeToken/Once</span><span class="sxs-lookup"><span data-stu-id="db74a-471">Protection Token: Kerberos Ticket, inclusion mode is set to .../IncludeToken/Once</span></span>  
<span data-ttu-id="db74a-472">Proteção de tokens: falso</span><span class="sxs-lookup"><span data-stu-id="db74a-472">Token Protection: False</span></span>  
  
 <span data-ttu-id="db74a-473">Cabeçalho inteiro e assinaturas do corpo: Verdadeiro</span><span class="sxs-lookup"><span data-stu-id="db74a-473">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="db74a-474">Ordem de proteção: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="db74a-474">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="db74a-475">Assinar assinatura: True</span><span class="sxs-lookup"><span data-stu-id="db74a-475">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="db74a-476">Política</span><span class="sxs-lookup"><span data-stu-id="db74a-476">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id='Kerberos_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:SymmetricBinding>  
        <wsp:Policy>  
          <sp:ProtectionToken>  
            <wsp:Policy>  
              <sp:KerberosToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/Once' >  
                <wsp:Policy>  
                  <sp:RequireDerivedKeys />
                  <sp:WssGssKerberosV5ApReqToken11 />
                </wsp:Policy>  
              </sp:KerberosToken>  
            </wsp:Policy>  
          </sp:ProtectionToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic128 />
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />
          <sp:EncryptSignature />
          <sp:OnlySignEntireHeadersAndBody />
        </wsp:Policy>  
      </sp:SymmetricBinding>  
      <sp:Wss11>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />
          <sp:MustSupportRefIssuerSerial />
          <sp:MustSupportRefThumbprint />
          <sp:MustSupportRefEncryptedKey />
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />
          <sp:RequireClientEntropy />
          <sp:RequireServerEntropy />
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="db74a-477">Exemplos de cabeçalho de segurança: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="db74a-477">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="db74a-478">Solicitação</span><span class="sxs-lookup"><span data-stu-id="db74a-478">Request</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsse:BinarySecurityToken>  
  ...  
  </wsse:BinarySecurityToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="db74a-479">Resposta</span><span class="sxs-lookup"><span data-stu-id="db74a-479">Response</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="db74a-480">Exemplos de cabeçalho de segurança: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="db74a-480">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="db74a-481">Solicitação</span><span class="sxs-lookup"><span data-stu-id="db74a-481">Request</span></span>  
  
```xml  
<wsse:Security>  
TBD  
</wsse:Security>  
```  
  
 <span data-ttu-id="db74a-482">Resposta</span><span class="sxs-lookup"><span data-stu-id="db74a-482">Response</span></span>  
  
```xml  
<wsse:Security>  
TBD  
</wsse:Security>  
```  
  
#### <a name="64-issuedtoken"></a><span data-ttu-id="db74a-483">6.4 EmitidoToken</span><span class="sxs-lookup"><span data-stu-id="db74a-483">6.4 IssuedToken</span></span>  
 <span data-ttu-id="db74a-484">Com este modo de autenticação, o cliente não autentica o serviço, como tal, ao invés disso, o cliente apresenta um token emitido por um STS e comprova o conhecimento de uma chave compartilhada.</span><span class="sxs-lookup"><span data-stu-id="db74a-484">With this authentication mode the client does not authenticate to the service, as such, rather the client presents a token issued by an STS and proves knowledge of a shared key.</span></span> <span data-ttu-id="db74a-485">O serviço não é autenticado ao cliente, como tal, em vez disso, o STS criptografa a chave compartilhada como parte do token emitido de tal forma que apenas o serviço pode descriptografar a chave.</span><span class="sxs-lookup"><span data-stu-id="db74a-485">The service is not authenticated to the client, as such, instead the STS encrypts the shared key as part of the issued token such that only the service can decrypt the key.</span></span> <span data-ttu-id="db74a-486">A vinculação utilizada é como ligação simétrica com as seguintes propriedades;</span><span class="sxs-lookup"><span data-stu-id="db74a-486">The binding used is as symmetric binding with the following properties;</span></span>  
  
 <span data-ttu-id="db74a-487">Token de proteção: Token emitido, o modo de inclusão está definido como .../IncludeToken/AlwaysToRecipient</span><span class="sxs-lookup"><span data-stu-id="db74a-487">Protection Token: Issued Token, inclusion mode is set to .../IncludeToken/AlwaysToRecipient</span></span>  
<span data-ttu-id="db74a-488">Proteção de tokens: falso</span><span class="sxs-lookup"><span data-stu-id="db74a-488">Token Protection: False</span></span>  
  
 <span data-ttu-id="db74a-489">Cabeçalho inteiro e assinaturas do corpo: Verdadeiro</span><span class="sxs-lookup"><span data-stu-id="db74a-489">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="db74a-490">Ordem de proteção: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="db74a-490">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="db74a-491">Assinar assinatura: True</span><span class="sxs-lookup"><span data-stu-id="db74a-491">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="db74a-492">Política</span><span class="sxs-lookup"><span data-stu-id="db74a-492">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id='CustomBinding_ISimple3_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:SymmetricBinding>  
        <wsp:Policy>  
          <sp:ProtectionToken>  
            <wsp:Policy>  
              <sp:IssuedToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
                <sp:RequestSecurityTokenTemplate>  
                  <wst:KeyType>  
http://schemas.xmlsoap.org/ws/2005/02/trust/SymmetricKey  
                  </wst:KeyType>
                </sp:RequestSecurityTokenTemplate>  
                <wsp:Policy>  
                  <sp:RequireDerivedKeys />
                  <sp:RequireInternalReference />
                </wsp:Policy>  
              </sp:IssuedToken>  
            </wsp:Policy>  
          </sp:ProtectionToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />
          <sp:EncryptSignature />
          <sp:OnlySignEntireHeadersAndBody />
        </wsp:Policy>  
      </sp:SymmetricBinding>  
      <sp:Wss11>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />
          <sp:MustSupportRefIssuerSerial />
          <sp:MustSupportRefThumbprint />
          <sp:MustSupportRefEncryptedKey />
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />
          <sp:RequireClientEntropy />
          <sp:RequireServerEntropy />
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="db74a-493">Exemplos de cabeçalho de segurança: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="db74a-493">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="db74a-494">Solicitação</span><span class="sxs-lookup"><span data-stu-id="db74a-494">Request</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <saml:Assertion>  
  ...  
  </saml:Assertion>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="db74a-495">Resposta</span><span class="sxs-lookup"><span data-stu-id="db74a-495">Response</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="db74a-496">Exemplos de cabeçalho de segurança: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="db74a-496">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="db74a-497">Solicitação</span><span class="sxs-lookup"><span data-stu-id="db74a-497">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <saml:Assertion>  
  ...  
  </saml:Assertion>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 <span data-ttu-id="db74a-498">Resposta</span><span class="sxs-lookup"><span data-stu-id="db74a-498">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
### <a name="65-using-sslnegotiated-for-service-authentication"></a><span data-ttu-id="db74a-499">6.5 Usando SslNegociado para autenticação de serviço</span><span class="sxs-lookup"><span data-stu-id="db74a-499">6.5 Using SslNegotiated for Service Authentication</span></span>  
 <span data-ttu-id="db74a-500">Esta seção descreve um grupo de modos de autenticação que usam uma vinculação simétrica com o token de proteção sendo um Token de Contexto de Segurança por WS-SecureConversation (WS-SC) cujo valor-chave é negociado executando o protocolo TLS sobre mensagens RST/RSTR WS-Trust (WS-T).</span><span class="sxs-lookup"><span data-stu-id="db74a-500">This section describes a group of authentication modes that use a symmetric binding with the protection token being a Security Context Token per WS-SecureConversation (WS-SC) whose key value is negotiated by executing the TLS protocol over WS-Trust (WS-T) RST/RSTR messages.</span></span> <span data-ttu-id="db74a-501">Detalhes da implementação do aperto de mão TLS usando o WS-Trust são descritos no TLSNEGO.</span><span class="sxs-lookup"><span data-stu-id="db74a-501">Details of the TLS handshake implementation using WS-Trust are described in TLSNEGO.</span></span> <span data-ttu-id="db74a-502">Aqui nos exemplos de mensagem vamos assumir que o SCT com um contexto de segurança associado já está estabelecido através de um aperto de mão.</span><span class="sxs-lookup"><span data-stu-id="db74a-502">Here in the message examples we will assume that SCT with an associated security context is already established through a handshake.</span></span>  
  
 <span data-ttu-id="db74a-503">A vinculação utilizada é uma ligação simétrica com as seguintes propriedades;</span><span class="sxs-lookup"><span data-stu-id="db74a-503">The binding used is a symmetric binding with the following properties;</span></span>  
  
 <span data-ttu-id="db74a-504">Token de proteção: SslContextToken, o modo de inclusão está definido como .../IncludeToken/Never</span><span class="sxs-lookup"><span data-stu-id="db74a-504">Protection Token: SslContextToken, inclusion mode is set to .../IncludeToken/Never</span></span>  
<span data-ttu-id="db74a-505">Proteção de tokens: falso</span><span class="sxs-lookup"><span data-stu-id="db74a-505">Token Protection: False</span></span>  
  
 <span data-ttu-id="db74a-506">Cabeçalho inteiro e assinaturas do corpo: Verdadeiro</span><span class="sxs-lookup"><span data-stu-id="db74a-506">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="db74a-507">Ordem de proteção: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="db74a-507">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="db74a-508">Assinar assinatura: True</span><span class="sxs-lookup"><span data-stu-id="db74a-508">Encrypt Signature: True</span></span>  
  
#### <a name="651-policy-for-sslnegotiated-service-authentication"></a><span data-ttu-id="db74a-509">6.5.1 Política para autenticação de serviço sslNegociada</span><span class="sxs-lookup"><span data-stu-id="db74a-509">6.5.1 Policy for SslNegotiated service authentication</span></span>  
 <span data-ttu-id="db74a-510">A política para todos os modos de autenticação nesta seção é semelhante e difere apenas por tokens de suporte ou endossamento assinados específicos usados.</span><span class="sxs-lookup"><span data-stu-id="db74a-510">Policy for all authentication modes in this section are similar and differ only by specific signed supporting or endorsing tokens used.</span></span>  
  
```xml  
<wsp:Policy wsu:Id='SslNegotiated_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:SymmetricBinding>  
        <wsp:Policy>  
          <sp:ProtectionToken>  
            <wsp:Policy>  
              <mssp:SslContextToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient'>  
                <wsp:Policy>  
                  <sp:RequireDerivedKeys />
                </wsp:Policy>  
              </mssp:SslContextToken>  
            </wsp:Policy>  
          </sp:ProtectionToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />
          <sp:EncryptSignature />
          <sp:OnlySignEntireHeadersAndBody />
        </wsp:Policy>  
      </sp:SymmetricBinding>  
      <!-- Supporting token assertions go here -->  
      ..  
      <sp:Wss11>
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />
          <sp:MustSupportRefIssuerSerial />
          <sp:MustSupportRefThumbprint />
          <sp:MustSupportRefEncryptedKey />
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />
          <sp:RequireClientEntropy />
          <sp:RequireServerEntropy />
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
#### <a name="652-anonymousforsslnegotiated"></a><span data-ttu-id="db74a-511">6.5.2 AnônimoSlNegociado</span><span class="sxs-lookup"><span data-stu-id="db74a-511">6.5.2 AnonymousForSslNegotiated</span></span>  
 <span data-ttu-id="db74a-512">Com este modo de autenticação, o cliente é anônimo e o serviço é autenticado usando um certificado X.509.</span><span class="sxs-lookup"><span data-stu-id="db74a-512">With this authentication mode the client is anonymous and the service is authenticated using an X.509 certificate.</span></span> <span data-ttu-id="db74a-513">A vinculação utilizada é uma instância de vinculação simétrica descrita em 6.5.1 acima.</span><span class="sxs-lookup"><span data-stu-id="db74a-513">The binding used is an instance of symmetric binding as described in 6.5.1 above.</span></span>  
  
 <span data-ttu-id="db74a-514">Política</span><span class="sxs-lookup"><span data-stu-id="db74a-514">Policy</span></span>  
  
 <span data-ttu-id="db74a-515">Consulte Política em 6.5.1 acima para obter detalhes de vinculação.</span><span class="sxs-lookup"><span data-stu-id="db74a-515">See Policy in 6.5.1 above for binding details.</span></span>  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="db74a-516">Exemplos de cabeçalho de segurança: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="db74a-516">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="db74a-517">Solicitação</span><span class="sxs-lookup"><span data-stu-id="db74a-517">Request</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="db74a-518">Resposta</span><span class="sxs-lookup"><span data-stu-id="db74a-518">Response</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="db74a-519">Exemplos de cabeçalho de segurança: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="db74a-519">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="db74a-520">Solicitação</span><span class="sxs-lookup"><span data-stu-id="db74a-520">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 <span data-ttu-id="db74a-521">Resposta</span><span class="sxs-lookup"><span data-stu-id="db74a-521">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
#### <a name="653-usernameforsslnegotiated"></a><span data-ttu-id="db74a-522">6.5.3 Nome de UsuárioForSslNegociado</span><span class="sxs-lookup"><span data-stu-id="db74a-522">6.5.3 UserNameForSslNegotiated</span></span>  
 <span data-ttu-id="db74a-523">Com este modo de autenticação, o cliente é autenticado usando um Token de nome de usuário que aparece na camada SOAP como um token de suporte assinado.</span><span class="sxs-lookup"><span data-stu-id="db74a-523">With this authentication mode the client is authenticates using a Username Token which appears at the SOAP layer as a signed supporting token.</span></span> <span data-ttu-id="db74a-524">O serviço é autenticado usando um certificado X.509.</span><span class="sxs-lookup"><span data-stu-id="db74a-524">The service is authenticated using an X.509 certificate.</span></span> <span data-ttu-id="db74a-525">A vinculação utilizada é uma instância de vinculação simétrica descrita em 6.5.1.</span><span class="sxs-lookup"><span data-stu-id="db74a-525">The binding used is an instance of symmetric binding as described in 6.5.1.</span></span>  
  
 <span data-ttu-id="db74a-526">Política</span><span class="sxs-lookup"><span data-stu-id="db74a-526">Policy</span></span>  
  
 <span data-ttu-id="db74a-527">Consulte a seção 6.5.1 acima para obter detalhes de vinculação</span><span class="sxs-lookup"><span data-stu-id="db74a-527">See section 6.5.1 above for binding details</span></span>  
  
 <span data-ttu-id="db74a-528">Token de suporte assinado</span><span class="sxs-lookup"><span data-stu-id="db74a-528">Signed Supporting Token</span></span>  
  
```xml  
<sp:SignedSupportingTokens>  
  <wsp:Policy>  
    <sp:UsernameToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
      <wsp:Policy>  
        <sp:WssUsernameToken10 />
      </wsp:Policy>  
    </sp:UsernameToken>  
  </wsp:Policy>  
</sp:SignedSupportingTokens>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="db74a-529">Exemplos de cabeçalho de segurança: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="db74a-529">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="db74a-530">Solicitação</span><span class="sxs-lookup"><span data-stu-id="db74a-530">Request</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="db74a-531">Resposta</span><span class="sxs-lookup"><span data-stu-id="db74a-531">Response</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="db74a-532">Exemplos de cabeçalho de segurança: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="db74a-532">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="db74a-533">Solicitação</span><span class="sxs-lookup"><span data-stu-id="db74a-533">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 <span data-ttu-id="db74a-534">Resposta</span><span class="sxs-lookup"><span data-stu-id="db74a-534">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
#### <a name="654-issuedtokenforsslnegotiated"></a><span data-ttu-id="db74a-535">6.5.4 EmitidoTokenForSslNegociado</span><span class="sxs-lookup"><span data-stu-id="db74a-535">6.5.4 IssuedTokenForSslNegotiated</span></span>  
 <span data-ttu-id="db74a-536">Com este modo de autenticação, o cliente não autentica o serviço, como tal, mas apresenta um token emitido por um STS e comprova o conhecimento de uma chave compartilhada.</span><span class="sxs-lookup"><span data-stu-id="db74a-536">With this authentication mode the client does not authenticate to the service, as such, but instead presents a token issued by an STS and proves knowledge of a shared key.</span></span> <span data-ttu-id="db74a-537">O token emitido aparece na camada SOAP como um token de suporte endossando.</span><span class="sxs-lookup"><span data-stu-id="db74a-537">The issued token appears at the SOAP layer as an endorsing supporting token.</span></span> <span data-ttu-id="db74a-538">O serviço é autenticado usando um certificado X.509.</span><span class="sxs-lookup"><span data-stu-id="db74a-538">The service is authenticated using an X.509 certificate.</span></span> <span data-ttu-id="db74a-539">A vinculação utilizada é uma instância de vinculação simétrica descrita em 6.5.1 acima.</span><span class="sxs-lookup"><span data-stu-id="db74a-539">The binding used is an instance of symmetric binding as described in 6.5.1 above.</span></span>  
  
 <span data-ttu-id="db74a-540">Política</span><span class="sxs-lookup"><span data-stu-id="db74a-540">Policy</span></span>  
  
 <span data-ttu-id="db74a-541">Consulte a seção 6.5.1 acima para obter detalhes de vinculação</span><span class="sxs-lookup"><span data-stu-id="db74a-541">See section 6.5.1 above for binding details</span></span>  
  
 <span data-ttu-id="db74a-542">Endossando o Token de Suporte</span><span class="sxs-lookup"><span data-stu-id="db74a-542">Endorsing Supporting Token</span></span>  
  
```xml  
<sp:EndorsingSupportingTokens>  
  <wsp:Policy>  
    <sp:IssuedToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
      <sp:RequestSecurityTokenTemplate>  
        <wst:KeyType>  
http://schemas.xmlsoap.org/ws/2005/02/trust/SymmetricKey  
        </wst:KeyType>
      </sp:RequestSecurityTokenTemplate>  
      <wsp:Policy>  
        <sp:RequireDerivedKeys />
        <sp:RequireInternalReference />
      </wsp:Policy>  
    </sp:IssuedToken>  
  </wsp:Policy>  
</sp:EndorsingSupportingTokens>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="db74a-543">Exemplos de cabeçalho de segurança: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="db74a-543">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="db74a-544">Solicitação</span><span class="sxs-lookup"><span data-stu-id="db74a-544">Request</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <saml:Assertion>  
  ...  
  </saml:Assertion>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="db74a-545">Resposta</span><span class="sxs-lookup"><span data-stu-id="db74a-545">Response</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="db74a-546">Exemplos de cabeçalho de segurança: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="db74a-546">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="db74a-547">Solicitação</span><span class="sxs-lookup"><span data-stu-id="db74a-547">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <saml:Assertion>  
  ...  
  </saml:Assertion>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 <span data-ttu-id="db74a-548">Resposta</span><span class="sxs-lookup"><span data-stu-id="db74a-548">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsse11:SignatureConfirmation />  
  <wsse11:SignatureConfirmation />  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
#### <a name="655-mutualsslnegotiated"></a><span data-ttu-id="db74a-549">6.5.5 MutualSslNegociado</span><span class="sxs-lookup"><span data-stu-id="db74a-549">6.5.5 MutualSslNegotiated</span></span>  
 <span data-ttu-id="db74a-550">Com este modo de autenticação, o cliente e o serviço autenticam usando certificados X.509.</span><span class="sxs-lookup"><span data-stu-id="db74a-550">With this authentication mode the client and the service authenticate using X.509 certificates.</span></span> <span data-ttu-id="db74a-551">A vinculação utilizada é uma instância de vinculação simétrica descrita em 6.5.1 acima.</span><span class="sxs-lookup"><span data-stu-id="db74a-551">The binding used is an instance of symmetric binding as described in 6.5.1 above.</span></span>  
  
 <span data-ttu-id="db74a-552">Política</span><span class="sxs-lookup"><span data-stu-id="db74a-552">Policy</span></span>  
  
 <span data-ttu-id="db74a-553">Consulte a seção 6.5.1 acima para obter detalhes de vinculação</span><span class="sxs-lookup"><span data-stu-id="db74a-553">See section 6.5.1 above for binding details</span></span>  
  
 <span data-ttu-id="db74a-554">Endossando o Token de Suporte</span><span class="sxs-lookup"><span data-stu-id="db74a-554">Endorsing Supporting Token</span></span>  
  
```xml  
<sp:EndorsingSupportingTokens>  
  <wsp:Policy>  
    <sp:X509Token sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
      <wsp:Policy>  
        <sp:RequireThumbprintReference />
        <sp:WssX509V3Token10 />
      </wsp:Policy>  
    </sp:X509Token>  
  </wsp:Policy>  
</sp:EndorsingSupportingTokens>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="db74a-555">Exemplos de cabeçalho de segurança: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="db74a-555">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="db74a-556">Solicitação</span><span class="sxs-lookup"><span data-stu-id="db74a-556">Request</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="db74a-557">Resposta</span><span class="sxs-lookup"><span data-stu-id="db74a-557">Response</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="db74a-558">Exemplos de cabeçalho de segurança: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="db74a-558">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="db74a-559">Solicitação</span><span class="sxs-lookup"><span data-stu-id="db74a-559">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 <span data-ttu-id="db74a-560">Resposta</span><span class="sxs-lookup"><span data-stu-id="db74a-560">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
### <a name="66-sspinegotiated"></a><span data-ttu-id="db74a-561">6.6 SspiNegociado</span><span class="sxs-lookup"><span data-stu-id="db74a-561">6.6 SspiNegotiated</span></span>  
 <span data-ttu-id="db74a-562">Com este modo de autenticação, um protocolo de negociação é usado para executar a autenticação do cliente e do servidor.</span><span class="sxs-lookup"><span data-stu-id="db74a-562">With this authentication mode a negotiation protocol is used to perform client and server authentication.</span></span> <span data-ttu-id="db74a-563">Kerberos é usado se possível, caso contrário NTLM.</span><span class="sxs-lookup"><span data-stu-id="db74a-563">Kerberos is used if possible, otherwise NTLM.</span></span> <span data-ttu-id="db74a-564">A vinculação utilizada é uma ligação simétrica com as seguintes propriedades;</span><span class="sxs-lookup"><span data-stu-id="db74a-564">The binding used is a symmetric binding with the following properties;</span></span>  
  
 <span data-ttu-id="db74a-565">Token de proteção: SpnegoContextToken, o modo de inclusão está definido como .../IncludeToken/AlwaysToRecipient</span><span class="sxs-lookup"><span data-stu-id="db74a-565">Protection Token: SpnegoContextToken, inclusion mode is set to .../IncludeToken/AlwaysToRecipient</span></span>  
<span data-ttu-id="db74a-566">Proteção de tokens: falso</span><span class="sxs-lookup"><span data-stu-id="db74a-566">Token Protection: False</span></span>  
  
 <span data-ttu-id="db74a-567">Cabeçalho inteiro e assinaturas do corpo: Verdadeiro</span><span class="sxs-lookup"><span data-stu-id="db74a-567">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="db74a-568">Ordem de proteção: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="db74a-568">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="db74a-569">Assinar assinatura: True</span><span class="sxs-lookup"><span data-stu-id="db74a-569">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="db74a-570">Política</span><span class="sxs-lookup"><span data-stu-id="db74a-570">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id='CustomBinding_ISimple13_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:SymmetricBinding>  
        <wsp:Policy>  
          <sp:ProtectionToken>  
            <wsp:Policy>  
              <sp:SpnegoContextToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
                <wsp:Policy>  
                  <sp:RequireDerivedKeys />
                </wsp:Policy>  
              </sp:SpnegoContextToken>  
            </wsp:Policy>  
          </sp:ProtectionToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />
          <sp:EncryptSignature />
          <sp:OnlySignEntireHeadersAndBody />
        </wsp:Policy>  
      </sp:SymmetricBinding>  
      <sp:Wss11>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />
          <sp:MustSupportRefIssuerSerial />
          <sp:MustSupportRefThumbprint />
          <sp:MustSupportRefEncryptedKey />
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />
          <sp:RequireClientEntropy />
          <sp:RequireServerEntropy />
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="db74a-571">Exemplos de cabeçalho de segurança: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="db74a-571">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="db74a-572">Solicitação</span><span class="sxs-lookup"><span data-stu-id="db74a-572">Request</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="db74a-573">Resposta</span><span class="sxs-lookup"><span data-stu-id="db74a-573">Response</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="db74a-574">Exemplos de cabeçalho de segurança: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="db74a-574">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="db74a-575">Solicitação</span><span class="sxs-lookup"><span data-stu-id="db74a-575">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 <span data-ttu-id="db74a-576">Resposta</span><span class="sxs-lookup"><span data-stu-id="db74a-576">Response</span></span>  
  
```xml  
<wsse:Security>  
<wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
### <a name="67-secureconversation"></a><span data-ttu-id="db74a-577">6.7 SecureConversation</span><span class="sxs-lookup"><span data-stu-id="db74a-577">6.7 SecureConversation</span></span>  
 <span data-ttu-id="db74a-578">A vinculação utilizada é uma vinculação simétrica com o token de proteção sendo um SCT por WS-SecureConversation (WS-SC).</span><span class="sxs-lookup"><span data-stu-id="db74a-578">The binding used is a symmetric binding with the protection token being a SCT per WS-SecureConversation (WS-SC).</span></span> <span data-ttu-id="db74a-579">O SCT é negociado usando ws-trust (WS-Trust) ou WS-SecureConversation (WS-SC) de acordo com uma vinculação aninhada, que é em si uma vinculação simétrica que usa um protocolo de negociação.</span><span class="sxs-lookup"><span data-stu-id="db74a-579">The SCT is negotiated using WS-Trust (WS-Trust) or WS-SecureConversation (WS-SC) according to a nested binding, which is itself a symmetric binding that uses a negotiation protocol.</span></span> <span data-ttu-id="db74a-580">O protocolo de negociação usará o Kerberos para realizar a autenticação do cliente e do servidor, se possível.</span><span class="sxs-lookup"><span data-stu-id="db74a-580">The negotiation protocol will use Kerberos to perform client and server authentication if possible.</span></span> <span data-ttu-id="db74a-581">Se Kerberos não puder ser usado, ele voltará para NTLM.</span><span class="sxs-lookup"><span data-stu-id="db74a-581">If Kerberos cannot be used, it will fall back to NTLM.</span></span>  
  
 <span data-ttu-id="db74a-582">Política</span><span class="sxs-lookup"><span data-stu-id="db74a-582">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id='SecureConversation_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:SymmetricBinding>  
        <wsp:Policy>  
          <sp:ProtectionToken>  
            <wsp:Policy>  
              <sp:SecureConversationToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
                <wsp:Policy>  
                  <sp:RequireDerivedKeys />
                  <sp:BootstrapPolicy>  
                    <wsp:Policy>  
                      <sp:SignedParts>  
                        <sp:Body />
                        <sp:Header Name='To' Namespace='http://www.w3.org/2005/08/addressing' />
                        <sp:Header Name='From' Namespace='http://www.w3.org/2005/08/addressing' />
                        <sp:Header Name='FaultTo' Namespace='http://www.w3.org/2005/08/addressing' />
                        <sp:Header Name='ReplyTo' Namespace='http://www.w3.org/2005/08/addressing' />
                        <sp:Header Name='MessageID' Namespace='http://www.w3.org/2005/08/addressing' />
                        <sp:Header Name='RelatesTo' Namespace='http://www.w3.org/2005/08/addressing' />
                        <sp:Header Name='Action' Namespace='http://www.w3.org/2005/08/addressing' />
                      </sp:SignedParts>  
                      <sp:EncryptedParts>  
                        <sp:Body />
                      </sp:EncryptedParts>  
                      <sp:SymmetricBinding>  
                        <wsp:Policy>  
                          <sp:ProtectionToken>  
                            <wsp:Policy>  
                              <sp:SpnegoContextToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
                                <wsp:Policy>  
                                  <sp:RequireDerivedKeys />
                                </wsp:Policy>  
                              </sp:SpnegoContextToken>  
                            </wsp:Policy>  
                          </sp:ProtectionToken>  
                          <sp:AlgorithmSuite>  
                            <wsp:Policy>  
                              <sp:Basic256 />
                            </wsp:Policy>  
                          </sp:AlgorithmSuite>  
                          <sp:Layout>  
                            <wsp:Policy>  
                              <sp:Strict />
                            </wsp:Policy>  
                          </sp:Layout>  
                          <sp:IncludeTimestamp />
                          <sp:EncryptSignature />
                          <sp:OnlySignEntireHeadersAndBody />
                        </wsp:Policy>  
                      </sp:SymmetricBinding>  
                      <sp:Wss11>  
                        <wsp:Policy>  
                          <sp:MustSupportRefKeyIdentifier />
                          <sp:MustSupportRefIssuerSerial />
                          <sp:MustSupportRefThumbprint />
                          <sp:MustSupportRefEncryptedKey />
                        </wsp:Policy>  
                      </sp:Wss11>  
                      <sp:Trust10>  
                        <wsp:Policy>  
                          <sp:MustSupportIssuedTokens />
                          <sp:RequireClientEntropy />
                          <sp:RequireServerEntropy />
                        </wsp:Policy>  
                      </sp:Trust10>  
                    </wsp:Policy>  
                  </sp:BootstrapPolicy>  
                </wsp:Policy>  
              </sp:SecureConversationToken>  
            </wsp:Policy>  
          </sp:ProtectionToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />
          <sp:EncryptSignature />
          <sp:OnlySignEntireHeadersAndBody />
        </wsp:Policy>  
      </sp:SymmetricBinding>  
      <sp:Wss11>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />
          <sp:MustSupportRefIssuerSerial />
          <sp:MustSupportRefThumbprint />
          <sp:MustSupportRefEncryptedKey />
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />
          <sp:RequireClientEntropy />
          <sp:RequireServerEntropy />
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="db74a-583">Exemplos de cabeçalho de segurança: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="db74a-583">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="db74a-584">Solicitação</span><span class="sxs-lookup"><span data-stu-id="db74a-584">Request</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="db74a-585">Resposta</span><span class="sxs-lookup"><span data-stu-id="db74a-585">Response</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="db74a-586">Exemplos de cabeçalho de segurança: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="db74a-586">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="db74a-587">Solicitação</span><span class="sxs-lookup"><span data-stu-id="db74a-587">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 <span data-ttu-id="db74a-588">Resposta</span><span class="sxs-lookup"><span data-stu-id="db74a-588">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```
