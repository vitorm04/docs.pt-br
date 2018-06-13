---
title: Protocolos de segurança versão 1.0
ms.date: 03/30/2017
ms.assetid: ee3402d2-1076-410b-a3cb-fae0372bd7af
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 1b1e911b20ac8974dbc8cfa79e03fbd14f9beb17
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33509171"
---
# <a name="security-protocols-version-10"></a><span data-ttu-id="d309e-102">Protocolos de segurança versão 1.0</span><span class="sxs-lookup"><span data-stu-id="d309e-102">Security Protocols version 1.0</span></span>
<span data-ttu-id="d309e-103">Os protocolos de segurança de serviços Web fornecer mecanismos de segurança de serviços Web que abrangem todos os enterprise existente, requisitos de segurança de mensagens.</span><span class="sxs-lookup"><span data-stu-id="d309e-103">The Web Services Security Protocols provide Web services security mechanisms that cover all existing enterprise messaging security requirements.</span></span> <span data-ttu-id="d309e-104">Esta seção descreve os detalhes do Windows Communication Foundation (WCF) versão 1.0 (implementado no <xref:System.ServiceModel.Channels.SecurityBindingElement>) para protocolos de segurança de serviços Web a seguir.</span><span class="sxs-lookup"><span data-stu-id="d309e-104">This section describes the Windows Communication Foundation (WCF) version 1.0 details (implemented in the <xref:System.ServiceModel.Channels.SecurityBindingElement>) for the following Web services security protocols.</span></span>  
  
|<span data-ttu-id="d309e-105">Documento de especificação /</span><span class="sxs-lookup"><span data-stu-id="d309e-105">Specification/Document</span></span>|<span data-ttu-id="d309e-106">Link</span><span class="sxs-lookup"><span data-stu-id="d309e-106">Link</span></span>|  
|-|-|  
|<span data-ttu-id="d309e-107">WSS: Segurança de mensagens SOAP 1.0</span><span class="sxs-lookup"><span data-stu-id="d309e-107">WSS: SOAP Message Security 1.0</span></span>|http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0.pdf|  
|<span data-ttu-id="d309e-108">WSS: Perfil de Token de nome de usuário 1.0</span><span class="sxs-lookup"><span data-stu-id="d309e-108">WSS: Username Token Profile 1.0</span></span>|http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0.pdf|  
|<span data-ttu-id="d309e-109">WSS: X509 Token perfil 1.0</span><span class="sxs-lookup"><span data-stu-id="d309e-109">WSS: X509 Token Profile 1.0</span></span>|http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-x509-token-profile-1.0.pdf|  
|<span data-ttu-id="d309e-110">WSS: SAML 1.1 Profile 1.0 do Token</span><span class="sxs-lookup"><span data-stu-id="d309e-110">WSS: SAML 1.1 Token Profile 1.0</span></span>|http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.0.pdf|  
|<span data-ttu-id="d309e-111">WSS: Segurança de mensagens SOAP 1.1</span><span class="sxs-lookup"><span data-stu-id="d309e-111">WSS: SOAP Message Security 1.1</span></span>|http://www.oasis-open.org/committees/download.php/16790/wss-v1.1-spec-os-SOAPMessageSecurity.pdf|  
|<span data-ttu-id="d309e-112">Perfil de Token de nome de usuário 1.1 do WSS</span><span class="sxs-lookup"><span data-stu-id="d309e-112">WSS Username Token Profile 1.1</span></span>|http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0.pdf|  
|<span data-ttu-id="d309e-113">WSS: Perfil de Token de x. 509 1.1</span><span class="sxs-lookup"><span data-stu-id="d309e-113">WSS: X.509 Token Profile 1.1</span></span>|http://www.oasis-open.org/committees/download.php/16785/wss-v1.1-spec-os-x509TokenProfile.pdf|  
|<span data-ttu-id="d309e-114">WSS: Perfil de Token Kerberos 1.1</span><span class="sxs-lookup"><span data-stu-id="d309e-114">WSS: Kerberos Token Profile 1.1</span></span>|http://www.oasis-open.org/committees/download.php/16788/wss-v1.1-spec-os-KerberosTokenProfile.pdf|  
|<span data-ttu-id="d309e-115">WSS: SAML 1.1 Profile 1.1 do Token</span><span class="sxs-lookup"><span data-stu-id="d309e-115">WSS: SAML 1.1 Token Profile 1.1</span></span>|http://www.oasis-open.org/committees/download.php/16768/wss-v1.1-spec-os-SAMLTokenProfile.pdf|  
|<span data-ttu-id="d309e-116">WS-Secure Conversation</span><span class="sxs-lookup"><span data-stu-id="d309e-116">WS-Secure Conversation</span></span>|http://msdn.microsoft.com/ws/2005/02/ws-secure-conversation/|  
|<span data-ttu-id="d309e-117">WS-Trust</span><span class="sxs-lookup"><span data-stu-id="d309e-117">WS-Trust</span></span>|http://msdn.microsoft.com/ws/2005/02/ws-trust/|  
|<span data-ttu-id="d309e-118">Observação do aplicativo:</span><span class="sxs-lookup"><span data-stu-id="d309e-118">Application Note:</span></span><br /><br /> <span data-ttu-id="d309e-119">Usando o WS-Trust de Handshake TLS</span><span class="sxs-lookup"><span data-stu-id="d309e-119">Using WS-Trust for TLS Handshake</span></span>|<span data-ttu-id="d309e-120">A publicação</span><span class="sxs-lookup"><span data-stu-id="d309e-120">To be published</span></span>|  
|<span data-ttu-id="d309e-121">Observação do aplicativo:</span><span class="sxs-lookup"><span data-stu-id="d309e-121">Application Note:</span></span><br /><br /> <span data-ttu-id="d309e-122">Usando o WS-Trust para SPNEGO</span><span class="sxs-lookup"><span data-stu-id="d309e-122">Using WS-Trust for SPNEGO</span></span>|<span data-ttu-id="d309e-123">A publicação</span><span class="sxs-lookup"><span data-stu-id="d309e-123">To be published</span></span>|  
|<span data-ttu-id="d309e-124">Observação do aplicativo:</span><span class="sxs-lookup"><span data-stu-id="d309e-124">Application Note:</span></span><br /><br /> <span data-ttu-id="d309e-125">Identidade e referências de endereçamento de ponto de extremidade de serviços Web</span><span class="sxs-lookup"><span data-stu-id="d309e-125">Web Services Addressing Endpoint References And Identity</span></span>|<span data-ttu-id="d309e-126">A publicação</span><span class="sxs-lookup"><span data-stu-id="d309e-126">To be published</span></span>|  
|<span data-ttu-id="d309e-127">O WS-SecurityPolicy 1.1</span><span class="sxs-lookup"><span data-stu-id="d309e-127">WS-SecurityPolicy 1.1</span></span><br /><br /> <span data-ttu-id="d309e-128">(2005/07)</span><span class="sxs-lookup"><span data-stu-id="d309e-128">(2005/07)</span></span>|http://msdn.microsoft.com/ws/2005/07/ws-security-policy/<br /><br /> <span data-ttu-id="d309e-129">como corrigida por errata enviado ao OASIS WS-SX Technical Committee http://www.oasis-open.org/archives/ws-sx/200512/msg00017.html</span><span class="sxs-lookup"><span data-stu-id="d309e-129">as amended by errata submitted to OASIS WS-SX Technical Committee http://www.oasis-open.org/archives/ws-sx/200512/msg00017.html</span></span>|  
  
 <span data-ttu-id="d309e-130">WCF, versão 1, fornece 17 modos de autenticação que podem ser usados como a base de configuração de segurança de serviços da Web.</span><span class="sxs-lookup"><span data-stu-id="d309e-130">WCF, version 1, provides 17 authentication modes that can be used as the basis for Web services security configuration.</span></span> <span data-ttu-id="d309e-131">Cada modo é otimizado para um conjunto comum de requisitos de implantação, como:</span><span class="sxs-lookup"><span data-stu-id="d309e-131">Each mode is optimized for a common set of deployment requirements, such as:</span></span>  
  
-   <span data-ttu-id="d309e-132">Credenciais usadas para autenticar o cliente e o serviço.</span><span class="sxs-lookup"><span data-stu-id="d309e-132">Credentials used to authenticate client and service.</span></span>  
  
-   <span data-ttu-id="d309e-133">Mecanismos de proteção de segurança transporte ou mensagem.</span><span class="sxs-lookup"><span data-stu-id="d309e-133">Message or transport security protection mechanisms.</span></span>  
  
-   <span data-ttu-id="d309e-134">Padrões de troca de mensagem.</span><span class="sxs-lookup"><span data-stu-id="d309e-134">Message exchange patterns.</span></span>  
  
|<span data-ttu-id="d309e-135">Modo de autenticação</span><span class="sxs-lookup"><span data-stu-id="d309e-135">Authentication Mode</span></span>|<span data-ttu-id="d309e-136">Autenticação de cliente</span><span class="sxs-lookup"><span data-stu-id="d309e-136">Client Authentication</span></span>|<span data-ttu-id="d309e-137">Autenticação de servidor</span><span class="sxs-lookup"><span data-stu-id="d309e-137">Server Authentication</span></span>|<span data-ttu-id="d309e-138">Modo</span><span class="sxs-lookup"><span data-stu-id="d309e-138">Mode</span></span>|  
|-------------------------|---------------------------|---------------------------|----------|  
|<span data-ttu-id="d309e-139">UserNameOverTransport</span><span class="sxs-lookup"><span data-stu-id="d309e-139">UserNameOverTransport</span></span>|<span data-ttu-id="d309e-140">Nome de usuário/senha</span><span class="sxs-lookup"><span data-stu-id="d309e-140">User name/password</span></span>|<span data-ttu-id="d309e-141">X509</span><span class="sxs-lookup"><span data-stu-id="d309e-141">X509</span></span>|<span data-ttu-id="d309e-142">Transporte</span><span class="sxs-lookup"><span data-stu-id="d309e-142">Transport</span></span>|  
|<span data-ttu-id="d309e-143">CertificateOverTransport</span><span class="sxs-lookup"><span data-stu-id="d309e-143">CertificateOverTransport</span></span>|<span data-ttu-id="d309e-144">X509</span><span class="sxs-lookup"><span data-stu-id="d309e-144">X509</span></span>|<span data-ttu-id="d309e-145">X509</span><span class="sxs-lookup"><span data-stu-id="d309e-145">X509</span></span>|<span data-ttu-id="d309e-146">Transporte</span><span class="sxs-lookup"><span data-stu-id="d309e-146">Transport</span></span>|  
|<span data-ttu-id="d309e-147">KerberosOverTransport</span><span class="sxs-lookup"><span data-stu-id="d309e-147">KerberosOverTransport</span></span>|<span data-ttu-id="d309e-148">Windows</span><span class="sxs-lookup"><span data-stu-id="d309e-148">Windows</span></span>|<span data-ttu-id="d309e-149">X509</span><span class="sxs-lookup"><span data-stu-id="d309e-149">X509</span></span>|<span data-ttu-id="d309e-150">Transporte</span><span class="sxs-lookup"><span data-stu-id="d309e-150">Transport</span></span>|  
|<span data-ttu-id="d309e-151">IssuedTokenOverTransport</span><span class="sxs-lookup"><span data-stu-id="d309e-151">IssuedTokenOverTransport</span></span>|<span data-ttu-id="d309e-152">Federado</span><span class="sxs-lookup"><span data-stu-id="d309e-152">Federated</span></span>|<span data-ttu-id="d309e-153">X509</span><span class="sxs-lookup"><span data-stu-id="d309e-153">X509</span></span>|<span data-ttu-id="d309e-154">Transporte</span><span class="sxs-lookup"><span data-stu-id="d309e-154">Transport</span></span>|  
|<span data-ttu-id="d309e-155">SspiNegotiatedOverTransport</span><span class="sxs-lookup"><span data-stu-id="d309e-155">SspiNegotiatedOverTransport</span></span>|<span data-ttu-id="d309e-156">Negociada Sspi do Windows</span><span class="sxs-lookup"><span data-stu-id="d309e-156">Windows Sspi Negotiated</span></span>|<span data-ttu-id="d309e-157">Negociada Sspi do Windows</span><span class="sxs-lookup"><span data-stu-id="d309e-157">Windows Sspi Negotiated</span></span>|<span data-ttu-id="d309e-158">Transporte</span><span class="sxs-lookup"><span data-stu-id="d309e-158">Transport</span></span>|  
|<span data-ttu-id="d309e-159">AnonymousForCertificate</span><span class="sxs-lookup"><span data-stu-id="d309e-159">AnonymousForCertificate</span></span>|<span data-ttu-id="d309e-160">Nenhum</span><span class="sxs-lookup"><span data-stu-id="d309e-160">None</span></span>|<span data-ttu-id="d309e-161">X509</span><span class="sxs-lookup"><span data-stu-id="d309e-161">X509</span></span>|<span data-ttu-id="d309e-162">Mensagem</span><span class="sxs-lookup"><span data-stu-id="d309e-162">Message</span></span>|  
|<span data-ttu-id="d309e-163">UserNameForCertificate</span><span class="sxs-lookup"><span data-stu-id="d309e-163">UserNameForCertificate</span></span>|<span data-ttu-id="d309e-164">Nome de usuário/senha</span><span class="sxs-lookup"><span data-stu-id="d309e-164">User name/password</span></span>|<span data-ttu-id="d309e-165">X509</span><span class="sxs-lookup"><span data-stu-id="d309e-165">X509</span></span>|<span data-ttu-id="d309e-166">Mensagem</span><span class="sxs-lookup"><span data-stu-id="d309e-166">Message</span></span>|  
|<span data-ttu-id="d309e-167">MutualCertificate</span><span class="sxs-lookup"><span data-stu-id="d309e-167">MutualCertificate</span></span>|<span data-ttu-id="d309e-168">X509</span><span class="sxs-lookup"><span data-stu-id="d309e-168">X509</span></span>|<span data-ttu-id="d309e-169">X509</span><span class="sxs-lookup"><span data-stu-id="d309e-169">X509</span></span>|<span data-ttu-id="d309e-170">Mensagem</span><span class="sxs-lookup"><span data-stu-id="d309e-170">Message</span></span>|  
|<span data-ttu-id="d309e-171">MutualCertificateDuplex</span><span class="sxs-lookup"><span data-stu-id="d309e-171">MutualCertificateDuplex</span></span>|<span data-ttu-id="d309e-172">X509</span><span class="sxs-lookup"><span data-stu-id="d309e-172">X509</span></span>|<span data-ttu-id="d309e-173">X509</span><span class="sxs-lookup"><span data-stu-id="d309e-173">X509</span></span>|<span data-ttu-id="d309e-174">Mensagem</span><span class="sxs-lookup"><span data-stu-id="d309e-174">Message</span></span>|  
|<span data-ttu-id="d309e-175">IssuedTokenForCertificate</span><span class="sxs-lookup"><span data-stu-id="d309e-175">IssuedTokenForCertificate</span></span>|<span data-ttu-id="d309e-176">Federado</span><span class="sxs-lookup"><span data-stu-id="d309e-176">Federated</span></span>|<span data-ttu-id="d309e-177">X509</span><span class="sxs-lookup"><span data-stu-id="d309e-177">X509</span></span>|<span data-ttu-id="d309e-178">Mensagem</span><span class="sxs-lookup"><span data-stu-id="d309e-178">Message</span></span>|  
|<span data-ttu-id="d309e-179">Kerberos</span><span class="sxs-lookup"><span data-stu-id="d309e-179">Kerberos</span></span>|<span data-ttu-id="d309e-180">Windows</span><span class="sxs-lookup"><span data-stu-id="d309e-180">Windows</span></span>|<span data-ttu-id="d309e-181">Windows</span><span class="sxs-lookup"><span data-stu-id="d309e-181">Windows</span></span>|<span data-ttu-id="d309e-182">Mensagem</span><span class="sxs-lookup"><span data-stu-id="d309e-182">Message</span></span>|  
|<span data-ttu-id="d309e-183">IssuedToken</span><span class="sxs-lookup"><span data-stu-id="d309e-183">IssuedToken</span></span>|<span data-ttu-id="d309e-184">Federado</span><span class="sxs-lookup"><span data-stu-id="d309e-184">Federated</span></span>|<span data-ttu-id="d309e-185">Federado</span><span class="sxs-lookup"><span data-stu-id="d309e-185">Federated</span></span>|<span data-ttu-id="d309e-186">Mensagem</span><span class="sxs-lookup"><span data-stu-id="d309e-186">Message</span></span>|  
|<span data-ttu-id="d309e-187">SspiNegotiated</span><span class="sxs-lookup"><span data-stu-id="d309e-187">SspiNegotiated</span></span>|<span data-ttu-id="d309e-188">Negociada Sspi do Windows</span><span class="sxs-lookup"><span data-stu-id="d309e-188">Windows Sspi Negotiated</span></span>|<span data-ttu-id="d309e-189">Negociada Sspi do Windows</span><span class="sxs-lookup"><span data-stu-id="d309e-189">Windows Sspi Negotiated</span></span>|<span data-ttu-id="d309e-190">Mensagem</span><span class="sxs-lookup"><span data-stu-id="d309e-190">Message</span></span>|  
|<span data-ttu-id="d309e-191">AnonymousForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="d309e-191">AnonymousForSslNegotiated</span></span>|<span data-ttu-id="d309e-192">Nenhum</span><span class="sxs-lookup"><span data-stu-id="d309e-192">None</span></span>|<span data-ttu-id="d309e-193">X509, Nego TLS</span><span class="sxs-lookup"><span data-stu-id="d309e-193">X509, TLS-Nego</span></span>|<span data-ttu-id="d309e-194">Mensagem</span><span class="sxs-lookup"><span data-stu-id="d309e-194">Message</span></span>|  
|<span data-ttu-id="d309e-195">UserNameForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="d309e-195">UserNameForSslNegotiated</span></span>|<span data-ttu-id="d309e-196">Nome de usuário/senha</span><span class="sxs-lookup"><span data-stu-id="d309e-196">User name/password</span></span>|<span data-ttu-id="d309e-197">X509, Nego TLS</span><span class="sxs-lookup"><span data-stu-id="d309e-197">X509, TLS-Nego</span></span>|<span data-ttu-id="d309e-198">Mensagem</span><span class="sxs-lookup"><span data-stu-id="d309e-198">Message</span></span>|  
|<span data-ttu-id="d309e-199">MutualSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="d309e-199">MutualSslNegotiated</span></span>|<span data-ttu-id="d309e-200">X509</span><span class="sxs-lookup"><span data-stu-id="d309e-200">X509</span></span>|<span data-ttu-id="d309e-201">X509, Nego TLS</span><span class="sxs-lookup"><span data-stu-id="d309e-201">X509, TLS-Nego</span></span>|<span data-ttu-id="d309e-202">Mensagem</span><span class="sxs-lookup"><span data-stu-id="d309e-202">Message</span></span>|  
|<span data-ttu-id="d309e-203">IssuedTokenForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="d309e-203">IssuedTokenForSslNegotiated</span></span>|<span data-ttu-id="d309e-204">Federado</span><span class="sxs-lookup"><span data-stu-id="d309e-204">Federated</span></span>|<span data-ttu-id="d309e-205">X509, Nego TLS</span><span class="sxs-lookup"><span data-stu-id="d309e-205">X509, TLS-Nego</span></span>|<span data-ttu-id="d309e-206">Mensagem</span><span class="sxs-lookup"><span data-stu-id="d309e-206">Message</span></span>|  
  
 <span data-ttu-id="d309e-207">Pontos de extremidade usando esses modos de autenticação podem expressar seus requisitos de segurança usando o WS-SecurityPolicy (WS-SP).</span><span class="sxs-lookup"><span data-stu-id="d309e-207">Endpoints using such authentication modes can express their security requirements using WS-SecurityPolicy (WS-SP).</span></span> <span data-ttu-id="d309e-208">Este documento descreve a estrutura de cabeçalho de segurança e mensagens de infraestrutura para cada modo de autenticação e fornece exemplos de políticas e mensagens.</span><span class="sxs-lookup"><span data-stu-id="d309e-208">This document describes the structure of security header and infrastructure messages for each authentication mode and provides examples of policies and messages.</span></span>  
  
 <span data-ttu-id="d309e-209">WCF aproveita o WS-SecureConversation para oferecer suportam a sessões seguras para proteger os intercâmbios de várias mensagens entre aplicativos.</span><span class="sxs-lookup"><span data-stu-id="d309e-209">WCF leverages WS-SecureConversation to provide secure sessions support to protect multi-message exchanges between applications.</span></span>  <span data-ttu-id="d309e-210">Consulte "Proteger sessões" abaixo para obter detalhes de implementação.</span><span class="sxs-lookup"><span data-stu-id="d309e-210">See "Secure Sessions" below for implementation details.</span></span>  
  
 <span data-ttu-id="d309e-211">Além dos modos de autenticação, o WCF fornece configurações para controlar os mecanismos de proteção comuns que se aplicam à maioria dos modos de autenticação com base em segurança de mensagem, por exemplo: ordem de assinatura versus operações de criptografia, conjuntos de algoritmo, derivação de chaves e a confirmação de assinatura.</span><span class="sxs-lookup"><span data-stu-id="d309e-211">In addition to authentication modes, WCF provides settings to control common protection mechanisms that apply to most message security-based authentication modes, for example: order of signature versus encryption operations, algorithm suites, key derivation, and signature confirmation.</span></span>  
  
 <span data-ttu-id="d309e-212">Os prefixos e os namespaces a seguir são usadas neste documento.</span><span class="sxs-lookup"><span data-stu-id="d309e-212">The following prefixes and namespaces are used in this document.</span></span>  
  
|<span data-ttu-id="d309e-213">Prefixo</span><span class="sxs-lookup"><span data-stu-id="d309e-213">Prefix</span></span>|<span data-ttu-id="d309e-214">Namespace</span><span class="sxs-lookup"><span data-stu-id="d309e-214">Namespace</span></span>|  
|------------|---------------|  
|<span data-ttu-id="d309e-215">s</span><span class="sxs-lookup"><span data-stu-id="d309e-215">s</span></span>|http://www.w3.org/2003/05/soap-envelope|  
|<span data-ttu-id="d309e-216">SP</span><span class="sxs-lookup"><span data-stu-id="d309e-216">sp</span></span>|http://schemas.xmlsoap.org/ws/2005/07/securitypolicy|  
|<span data-ttu-id="d309e-217">a</span><span class="sxs-lookup"><span data-stu-id="d309e-217">a</span></span>|http://www.w3.org/2005/08/addressing|  
|<span data-ttu-id="d309e-218">wsse</span><span class="sxs-lookup"><span data-stu-id="d309e-218">wsse</span></span>|<span data-ttu-id="d309e-219">TBD-OASIS WSS 1.0 URI</span><span class="sxs-lookup"><span data-stu-id="d309e-219">TBD – OASIS WSS 1.0 URI</span></span>|  
|<span data-ttu-id="d309e-220">wsse11</span><span class="sxs-lookup"><span data-stu-id="d309e-220">wsse11</span></span>|<span data-ttu-id="d309e-221">TBD-OASIS WSS 1.1 URI</span><span class="sxs-lookup"><span data-stu-id="d309e-221">TBD – OASIS WSS 1.1 URI</span></span>|  
|<span data-ttu-id="d309e-222">wsu</span><span class="sxs-lookup"><span data-stu-id="d309e-222">wsu</span></span>|<span data-ttu-id="d309e-223">TBD-OASIS WSS 1.0 utilitário URI</span><span class="sxs-lookup"><span data-stu-id="d309e-223">TBD – OASIS WSS 1.0 Utility URI</span></span>|  
|<span data-ttu-id="d309e-224">DS</span><span class="sxs-lookup"><span data-stu-id="d309e-224">ds</span></span>|<span data-ttu-id="d309e-225">TBD-W3C XMLDSig URI</span><span class="sxs-lookup"><span data-stu-id="d309e-225">TBD – W3C XMLDSig URI</span></span>|  
|<span data-ttu-id="d309e-226">WST</span><span class="sxs-lookup"><span data-stu-id="d309e-226">wst</span></span>|<span data-ttu-id="d309e-227">TBD-02/2005 WS-Trust URI</span><span class="sxs-lookup"><span data-stu-id="d309e-227">TBD – WS-Trust 2005/02 URI</span></span>|  
|<span data-ttu-id="d309e-228">wssc</span><span class="sxs-lookup"><span data-stu-id="d309e-228">wssc</span></span>|<span data-ttu-id="d309e-229">TBD-02/2005 WS-SecureConversation URI</span><span class="sxs-lookup"><span data-stu-id="d309e-229">TBD – WS-SecureConversation 2005/02 URI</span></span>|  
|<span data-ttu-id="d309e-230">wsaw</span><span class="sxs-lookup"><span data-stu-id="d309e-230">wsaw</span></span>|<span data-ttu-id="d309e-231">TBD - WS-Addressing namespace de política</span><span class="sxs-lookup"><span data-stu-id="d309e-231">TBD - WS-Addressing policy namespace</span></span>|  
|<span data-ttu-id="d309e-232">wsp</span><span class="sxs-lookup"><span data-stu-id="d309e-232">wsp</span></span>|http://schemas.xmlsoap.org/ws/2004/09/policy|  
|<span data-ttu-id="d309e-233">mssp</span><span class="sxs-lookup"><span data-stu-id="d309e-233">mssp</span></span>|http://schemas.microsoft.com/ws/2005/07/securitypolicy|  
  
## <a name="1-token-profiles"></a><span data-ttu-id="d309e-234">1. Perfis de token</span><span class="sxs-lookup"><span data-stu-id="d309e-234">1. Token Profiles</span></span>  
 <span data-ttu-id="d309e-235">Especificações de segurança dos serviços da Web representam credencial como tokens de segurança.</span><span class="sxs-lookup"><span data-stu-id="d309e-235">Web Services Security specifications represent credential as security tokens.</span></span> <span data-ttu-id="d309e-236">O WCF suporta os seguintes tipos de token:</span><span class="sxs-lookup"><span data-stu-id="d309e-236">WCF supports the following token types:</span></span>  
  
### <a name="11-usernametoken"></a><span data-ttu-id="d309e-237">1.1 UsernameToken</span><span class="sxs-lookup"><span data-stu-id="d309e-237">1.1 UsernameToken</span></span>  
 <span data-ttu-id="d309e-238">WCF segue perfis UsernameToken10 e UsernameToken11 com as seguintes restrições:</span><span class="sxs-lookup"><span data-stu-id="d309e-238">WCF follows UsernameToken10 and UsernameToken11 profiles with the following constraints:</span></span>  
  
 <span data-ttu-id="d309e-239">R1101 PasswordType atributo no elemento UsernameToken\Password deve ser omitido ou tem valor #PasswordText (padrão).</span><span class="sxs-lookup"><span data-stu-id="d309e-239">R1101 PasswordType attribute on UsernameToken\Password element MUST be either omitted or have value #PasswordText (default).</span></span>  
  
 <span data-ttu-id="d309e-240">O #PasswordDigest usando extensibilidade podem ser implementados.</span><span class="sxs-lookup"><span data-stu-id="d309e-240">One can implement the #PasswordDigest using extensibility.</span></span> <span data-ttu-id="d309e-241">Foi observado que #PasswordDigest foi enganado geralmente para ser um mecanismo de proteção de senha segura o suficiente.</span><span class="sxs-lookup"><span data-stu-id="d309e-241">It has been observed that #PasswordDigest was often mistaken to be a secure enough password protection mechanism.</span></span> <span data-ttu-id="d309e-242">Mas #PasswordDigest não pode servir como um substituto para criptografia de UsernameToken.</span><span class="sxs-lookup"><span data-stu-id="d309e-242">But #PasswordDigest cannot serve as a substitute for encryption of the UsernameToken.</span></span> <span data-ttu-id="d309e-243">O objetivo principal do #PasswordDigest é a proteção contra ataques de repetição.</span><span class="sxs-lookup"><span data-stu-id="d309e-243">The primary goal of #PasswordDigest is protection against replay attacks.</span></span> <span data-ttu-id="d309e-244">Nos modos de autenticação do WCF, ataque ameaças sejam atenuadas usando assinaturas de mensagem de repetição.</span><span class="sxs-lookup"><span data-stu-id="d309e-244">In WCF authentication modes, replay attack threats are mitigated by using message signatures.</span></span>  
  
 <span data-ttu-id="d309e-245">B1102 WCF nunca emite Nonce e criado subelementos UsernameToken.</span><span class="sxs-lookup"><span data-stu-id="d309e-245">B1102 WCF never emits Nonce and Created sub-elements of the UsernameToken.</span></span>  
  
 <span data-ttu-id="d309e-246">Estes subelementos destinam-se a ajudar na detecção de repetição.</span><span class="sxs-lookup"><span data-stu-id="d309e-246">These sub-elements are intended to help replay detection.</span></span> <span data-ttu-id="d309e-247">Em vez disso, o WCF usa assinaturas de mensagem.</span><span class="sxs-lookup"><span data-stu-id="d309e-247">WCF uses message signatures instead.</span></span>  
  
 <span data-ttu-id="d309e-248">OASIS WSS SOAP mensagem segurança UsernameToken Profile 1.1 (UsernameToken11) introduziu a derivação de chave de recurso de senha.</span><span class="sxs-lookup"><span data-stu-id="d309e-248">OASIS WSS SOAP Message Security UsernameToken Profile 1.1 (UsernameToken11) introduced key derivation from password feature.</span></span>  
  
 <span data-ttu-id="d309e-249">B1103 UsernameToken senha não deve ser usada para derivação de chaves e, portanto, para operações criptográficas.</span><span class="sxs-lookup"><span data-stu-id="d309e-249">B1103 UsernameToken password MUST not be used for key derivation and therefore for cryptographic operations.</span></span>  
  
 <span data-ttu-id="d309e-250">Motivo: senhas geralmente são consideradas muito fracas para ser usada para operações criptográficas.</span><span class="sxs-lookup"><span data-stu-id="d309e-250">Rationale: passwords are generally considered too weak to be used for cryptographic operations.</span></span>  
  
### <a name="12-x509-token"></a><span data-ttu-id="d309e-251">1.2 x 509 Token</span><span class="sxs-lookup"><span data-stu-id="d309e-251">1.2 X509 Token</span></span>  
 <span data-ttu-id="d309e-252">O WCF dá suporte a certificados X509v3 como um tipo de credencial e segue X509TokenProfile1.0 e X509TokenProfile1.1 com as seguintes restrições:</span><span class="sxs-lookup"><span data-stu-id="d309e-252">WCF supports X509v3 certificates as a credential type and follows X509TokenProfile1.0 and X509TokenProfile1.1 with the following constraints:</span></span>  
  
 <span data-ttu-id="d309e-253">Atributo ValueType o R1201 no elemento BinarySecurityToken deve ter valor #X509v3 quando ele contém um certificado de X509v3.</span><span class="sxs-lookup"><span data-stu-id="d309e-253">R1201 The ValueType attribute on the BinarySecurityToken element must have value #X509v3 when it contains an X509v3 certificate.</span></span>  
  
 <span data-ttu-id="d309e-254">WSS X509 Token Profile 1.0 e 1.1 definem também X509PKIPathv1 # e #PKCS7 como tipos de valor.</span><span class="sxs-lookup"><span data-stu-id="d309e-254">WSS X509 Token Profile 1.0 and 1.1 define also #X509PKIPathv1 and #PKCS7 as value types.</span></span> <span data-ttu-id="d309e-255">O WCF não oferece suporte a esses tipos.</span><span class="sxs-lookup"><span data-stu-id="d309e-255">WCF does not support these types.</span></span>  
  
 <span data-ttu-id="d309e-256">R1202 se uma extensão de SubjectKeyIdentifier (SKI) está presente no X509 certificado, wsse:KeyIdentifier deve ser usado para referências externas para o token, com ValueType como #X509SubjectKeyIdentifier e seu conteúdo o codificada em base64 valor de atributo extensão SKI do certificado.</span><span class="sxs-lookup"><span data-stu-id="d309e-256">R1202 If a SubjectKeyIdentifier (SKI) extension is present in an X509 certificate, wsse:KeyIdentifier should be used for external references to the token, with the ValueType attribute as #X509SubjectKeyIdentifier and its content the base64-encoded value of certificate's SKI extension.</span></span>  
  
 <span data-ttu-id="d309e-257">Referências SKI são amplamente implementadas e mostrou para ser um tipo de referência externa altamente interoperável.</span><span class="sxs-lookup"><span data-stu-id="d309e-257">SKI references are widely implemented and proven to be a highly interoperable external reference type.</span></span>  
  
 <span data-ttu-id="d309e-258">R1203 Uma referência externa para X509 segurança Token não devem usar ds:X509IssuerSerial.</span><span class="sxs-lookup"><span data-stu-id="d309e-258">R1203 An external Reference to X509 Security Token SHOULD NOT use ds:X509IssuerSerial.</span></span>  
  
 <span data-ttu-id="d309e-259">X509TokenProfile1.1 de R1204 se estiver em uso, uma referência externa para X509 segurança Token deve usar a impressão digital introduzida por 1,1 WS-Security.</span><span class="sxs-lookup"><span data-stu-id="d309e-259">R1204 If X509TokenProfile1.1 is in use, an external reference to X509 Security Token SHOULD use the thumbprint introduced by WS-Security 1.1.</span></span>  
  
 <span data-ttu-id="d309e-260">O WCF suporta X509IssuerSerial.</span><span class="sxs-lookup"><span data-stu-id="d309e-260">WCF supports X509IssuerSerial.</span></span> <span data-ttu-id="d309e-261">No entanto, há problemas de interoperabilidade com X509IssuerSerial: WCF usa uma cadeia de caracteres para comparar dois valores de X509IssuerSerial.</span><span class="sxs-lookup"><span data-stu-id="d309e-261">However There are interoperability issues with X509IssuerSerial: WCF uses a string to compare two values of X509IssuerSerial.</span></span> <span data-ttu-id="d309e-262">Portanto, se um reorganiza os componentes do nome da entidade e envia a um serviço WCF em uma referência a um certificado, ele pode não ser encontrado.</span><span class="sxs-lookup"><span data-stu-id="d309e-262">Therefore if one reorders components of the Subject Name and sends to an WCF service a reference to a certificate, it may not be found.</span></span>  
  
### <a name="13-kerberos-token"></a><span data-ttu-id="d309e-263">1.3 Token Kerberos</span><span class="sxs-lookup"><span data-stu-id="d309e-263">1.3 Kerberos Token</span></span>  
 <span data-ttu-id="d309e-264">O WCF suporta KerberosTokenProfile1.1 para fins de autenticação do Windows com as seguintes restrições:</span><span class="sxs-lookup"><span data-stu-id="d309e-264">WCF supports KerberosTokenProfile1.1 for the purpose of Windows authentication with the following constraints:</span></span>  
  
 <span data-ttu-id="d309e-265">R1301 um Kerberos Token deve conter o valor de um GSS encapsulado Kerberos v4 AP_REQ conforme definido em GSS_API e a especificação de Kerberos e deve ter o atributo ValueType com o valor #GSS_Kerberosv5_AP_REQ.</span><span class="sxs-lookup"><span data-stu-id="d309e-265">R1301 A Kerberos Token must carry the value of a GSS wrapped Kerberos v4 AP_REQ as defined in GSS_API and the Kerberos specification, and must have the ValueType attribute with the value #GSS_Kerberosv5_AP_REQ.</span></span>  
  
 <span data-ttu-id="d309e-266">Usa o WCF GSS encapsulado AP-REQ Kerberos, não um bare AP-REQ.</span><span class="sxs-lookup"><span data-stu-id="d309e-266">WCF uses GSS wrapped Kerberos AP-REQ, not a bare AP-REQ.</span></span> <span data-ttu-id="d309e-267">Isso é uma prática recomendada de segurança.</span><span class="sxs-lookup"><span data-stu-id="d309e-267">This is a security best practice.</span></span>  
  
### <a name="14-saml-v11-token"></a><span data-ttu-id="d309e-268">1.4 SAML 1.1 Token</span><span class="sxs-lookup"><span data-stu-id="d309e-268">1.4 SAML v1.1 Token</span></span>  
 <span data-ttu-id="d309e-269">O WCF dá suporte a perfis de Token de SAML do WSS 1.0 e 1.1 para tokens do SAML 1.1.</span><span class="sxs-lookup"><span data-stu-id="d309e-269">WCF supports WSS SAML Token profiles 1.0 and 1.1 for SAML v1.1 tokens.</span></span> <span data-ttu-id="d309e-270">É possível implementar a outras versões de formatos de token SAML.</span><span class="sxs-lookup"><span data-stu-id="d309e-270">It is possible to implement other versions of SAML token formats.</span></span>  
  
### <a name="15-security-context-token"></a><span data-ttu-id="d309e-271">1.5 Token de contexto de segurança de</span><span class="sxs-lookup"><span data-stu-id="d309e-271">1.5 Security Context Token</span></span>  
 <span data-ttu-id="d309e-272">O WCF suporta a segurança contexto Token SCT () introduzido no WS-SecureCoversation.</span><span class="sxs-lookup"><span data-stu-id="d309e-272">WCF supports the Security Context Token (SCT) introduced in WS-SecureCoversation.</span></span> <span data-ttu-id="d309e-273">SCT é usada para representar o contexto de segurança estabelecido no SecureConversation, bem como a negociação binária protocolos TLS e SSPI, descrito abaixo.</span><span class="sxs-lookup"><span data-stu-id="d309e-273">SCT is used to represent a security context established in SecureConversation as well as the binary negotiation protocols TLS and SSPI, described below.</span></span>  
  
## <a name="2-common-message-security-parameters"></a><span data-ttu-id="d309e-274">2. Parâmetros comuns de segurança de mensagem</span><span class="sxs-lookup"><span data-stu-id="d309e-274">2. Common Message Security Parameters</span></span>  
  
### <a name="21-timestamp"></a><span data-ttu-id="d309e-275">2.1 TimeStamp</span><span class="sxs-lookup"><span data-stu-id="d309e-275">2.1 TimeStamp</span></span>  
 <span data-ttu-id="d309e-276">Presença de carimbo de hora é controlada usando o <xref:System.ServiceModel.Channels.SecurityBindingElement.IncludeTimestamp%2A> propriedade o <xref:System.ServiceModel.Channels.SecurityBindingElement> classe.</span><span class="sxs-lookup"><span data-stu-id="d309e-276">Timestamp presence is controlled using the <xref:System.ServiceModel.Channels.SecurityBindingElement.IncludeTimestamp%2A> property of the <xref:System.ServiceModel.Channels.SecurityBindingElement> class.</span></span> <span data-ttu-id="d309e-277">WCF sempre serializa wsse:TimeStamp com wsse: criados e wsse: campos de expirar.</span><span class="sxs-lookup"><span data-stu-id="d309e-277">WCF always serializes wsse:TimeStamp with wsse:Created and wsse:Expires fields.</span></span> <span data-ttu-id="d309e-278">O wsse:TimeStamp sempre é assinado quando a assinatura é usada.</span><span class="sxs-lookup"><span data-stu-id="d309e-278">The wsse:TimeStamp is always signed when signing is used.</span></span>  
  
### <a name="22-protection-order"></a><span data-ttu-id="d309e-279">2.2 ordem de proteção</span><span class="sxs-lookup"><span data-stu-id="d309e-279">2.2 Protection Order</span></span>  
 <span data-ttu-id="d309e-280">O WCF oferece suporte a ordem de proteção de mensagem "Logon antes de criptografar" e "Criptografar antes de inscrever-se" (1.1 de política de segurança).</span><span class="sxs-lookup"><span data-stu-id="d309e-280">WCF supports the message protection order "Sign Before Encrypt" and "Encrypt Before Sign" (Security Policy 1.1).</span></span> <span data-ttu-id="d309e-281">"Entrar antes de criptografar" é recomendado por motivos como: mensagens protegidas com criptografar antes de sinal estão sujeitos a ataques de substituição de assinatura a menos que o mecanismo do WS-Security 1.1 SignatureConfirmation for usado, e faz com que uma assinatura sobre conteúdo criptografado auditoria mais difícil.</span><span class="sxs-lookup"><span data-stu-id="d309e-281">"Sign Before Encrypt" is recommended for reasons including: messages protected with Encrypt Before Sign are open to signature substitution attacks unless the WS-Security 1.1 SignatureConfirmation mechanism is used, and a signature over encrypted content makes auditing harder.</span></span>  
  
### <a name="23-signature-protection"></a><span data-ttu-id="d309e-282">2.3 proteção de assinatura</span><span class="sxs-lookup"><span data-stu-id="d309e-282">2.3 Signature Protection</span></span>  
 <span data-ttu-id="d309e-283">Quando criptografar antes de logon é usado, é recomendável para proteger a assinatura para evitar ataques de força bruta para adivinhar o conteúdo criptografado ou a chave de assinatura (especialmente quando um token personalizado é usado com material de chave fraca).</span><span class="sxs-lookup"><span data-stu-id="d309e-283">When Encrypt Before Sign is used, it is recommended to protect the signature to prevent brute force attacks for guessing the encrypted content or the signing key (especially when a custom token is used with weak key material).</span></span>  
  
### <a name="24-algorithm-suite"></a><span data-ttu-id="d309e-284">2.4 conjunto de algoritmos de</span><span class="sxs-lookup"><span data-stu-id="d309e-284">2.4 Algorithm Suite</span></span>  
 <span data-ttu-id="d309e-285">O WCF dá suporte a todos os conjuntos de algoritmo listados na 1.1 de política de segurança.</span><span class="sxs-lookup"><span data-stu-id="d309e-285">WCF supports all algorithm suites listed in Security Policy 1.1.</span></span>  
  
### <a name="25-key-derivation"></a><span data-ttu-id="d309e-286">2.5 derivação de chave</span><span class="sxs-lookup"><span data-stu-id="d309e-286">2.5 Key Derivation</span></span>  
 <span data-ttu-id="d309e-287">WCF usa "Derivação de chave para chaves simétricas", conforme descrito em WS-SecureConversation.</span><span class="sxs-lookup"><span data-stu-id="d309e-287">WCF uses "Key Derivation for symmetric keys" as described in WS-SecureConversation.</span></span>  
  
### <a name="26-signature-confirmation"></a><span data-ttu-id="d309e-288">2.6 confirmação de assinatura</span><span class="sxs-lookup"><span data-stu-id="d309e-288">2.6 Signature Confirmation</span></span>  
 <span data-ttu-id="d309e-289">Confirmação de assinatura pode ser como proteção contra ataques intermediária para proteger o conjunto de assinaturas.</span><span class="sxs-lookup"><span data-stu-id="d309e-289">Signature confirmation can be as protection from middle man attacks to protect the set of signatures.</span></span>  
  
### <a name="27-security-header-layout"></a><span data-ttu-id="d309e-290">2.7 Layout de cabeçalho de segurança</span><span class="sxs-lookup"><span data-stu-id="d309e-290">2.7 Security Header Layout</span></span>  
 <span data-ttu-id="d309e-291">Cada modo de autenticação descreve um determinado layout para o cabeçalho de segurança.</span><span class="sxs-lookup"><span data-stu-id="d309e-291">Each authentication mode describes a certain layout for the security header.</span></span> <span data-ttu-id="d309e-292">Elementos dentro do cabeçalho de segurança são ordenados semi-estruturados.</span><span class="sxs-lookup"><span data-stu-id="d309e-292">Elements within the security header are semi-ordered.</span></span> <span data-ttu-id="d309e-293">Para definir a ordem dos elementos de filhos do cabeçalho de segurança, WS-Security Policy define os seguintes modos de layout de cabeçalho de segurança:</span><span class="sxs-lookup"><span data-stu-id="d309e-293">To define the order of security header child elements, WS-Security Policy defines the following security header layout modes:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d309e-294">Estrito</span><span class="sxs-lookup"><span data-stu-id="d309e-294">Strict</span></span>|<span data-ttu-id="d309e-295">Itens são adicionados para o seguinte cabeçalho de segurança, que as regras de layout numerados descrito na seção 7.7.1 de acordo com um geral de política de segurança princípio de "declarar antes do uso".</span><span class="sxs-lookup"><span data-stu-id="d309e-295">Items are added to the security header following the numbered layout rules described in Security Policy section 7.7.1 according to a general principle of "declare before use".</span></span>|  
|<span data-ttu-id="d309e-296">Incerta</span><span class="sxs-lookup"><span data-stu-id="d309e-296">Lax</span></span>|<span data-ttu-id="d309e-297">Itens são adicionados ao cabeçalho de segurança em qualquer ordem compatível com WSS: segurança de mensagens SOAP.</span><span class="sxs-lookup"><span data-stu-id="d309e-297">Items are added to the security header in any order that conforms to WSS: SOAP Message Security.</span></span>|  
|<span data-ttu-id="d309e-298">LaxTimestampFirst</span><span class="sxs-lookup"><span data-stu-id="d309e-298">LaxTimestampFirst</span></span>|<span data-ttu-id="d309e-299">Mesmo como Lax exceto que o primeiro item no cabeçalho de segurança deve ser um wsse:Timestamp</span><span class="sxs-lookup"><span data-stu-id="d309e-299">Same as Lax except that the first item in the security header must be a wsse:Timestamp</span></span>|  
|<span data-ttu-id="d309e-300">LaxTimestampLast</span><span class="sxs-lookup"><span data-stu-id="d309e-300">LaxTimestampLast</span></span>|<span data-ttu-id="d309e-301">Mesmo que incerta exceto que o último item no cabeçalho de segurança deve ser um wsse:Timestamp</span><span class="sxs-lookup"><span data-stu-id="d309e-301">Same as lax except that the last item in the security header must be a wsse:Timestamp</span></span>|  
  
 <span data-ttu-id="d309e-302">WCF dá suporte a todos os quatro modos de layout de cabeçalho de segurança.</span><span class="sxs-lookup"><span data-stu-id="d309e-302">WCF supports all four modes for security header layout.</span></span> <span data-ttu-id="d309e-303">Exemplos de estrutura e a mensagem de cabeçalho de segurança para os modos de autenticação abaixo siga o modo de "Strict".</span><span class="sxs-lookup"><span data-stu-id="d309e-303">Security header structure and message examples for authentication modes below follow the "Strict" mode.</span></span>  
  
## <a name="2-common-message-security-parameters"></a><span data-ttu-id="d309e-304">2. Parâmetros comuns de segurança de mensagem</span><span class="sxs-lookup"><span data-stu-id="d309e-304">2. Common Message Security Parameters</span></span>  
 <span data-ttu-id="d309e-305">Esta seção fornece as políticas de exemplo para cada modo de autenticação junto com exemplos mostrando a estrutura de cabeçalho de segurança em mensagens trocadas por cliente e de serviço.</span><span class="sxs-lookup"><span data-stu-id="d309e-305">This section provides example policies for each authentication mode along with examples showing security header structure in messages exchanged by client and service.</span></span>  
  
### <a name="61-transport-protection"></a><span data-ttu-id="d309e-306">6.1 proteção de transporte</span><span class="sxs-lookup"><span data-stu-id="d309e-306">6.1 Transport Protection</span></span>  
 <span data-ttu-id="d309e-307">O WCF fornece cinco modos de autenticação que usam um transporte seguro para proteger as mensagens; UserNameOverTransport, CertificateOverTransport, KerberosOverTransport, IssuedTokenOverTransport e SspiNegotiatedOverTransport.</span><span class="sxs-lookup"><span data-stu-id="d309e-307">WCF provides five authentication modes that use secure transport to protect messages; UserNameOverTransport, CertificateOverTransport, KerberosOverTransport, IssuedTokenOverTransport and SspiNegotiatedOverTransport.</span></span>  
  
 <span data-ttu-id="d309e-308">Esses modos de autenticação são construídos usando a associação de transporte descrita em SecurityPolicy.</span><span class="sxs-lookup"><span data-stu-id="d309e-308">These authentication modes are constructed using the transport binding described in SecurityPolicy.</span></span> <span data-ttu-id="d309e-309">Para o UserNameOverTransport UsernameToken o modo de autenticação é um token de suporte assinado.</span><span class="sxs-lookup"><span data-stu-id="d309e-309">For the UserNameOverTransport authentication mode the UsernameToken is a signed supporting token.</span></span> <span data-ttu-id="d309e-310">Para outros modos de autenticação de token aparece como um token de endosso assinado.</span><span class="sxs-lookup"><span data-stu-id="d309e-310">For the other authentication modes the token appears as a signed endorsing token.</span></span> <span data-ttu-id="d309e-311">Apêndice C.1.2 e C.1.3 de SecurityPolicy descrevem o layout do cabeçalho de segurança em detalhes.</span><span class="sxs-lookup"><span data-stu-id="d309e-311">Appendix C.1.2 and C.1.3 of SecurityPolicy describe the security header layout in detail.</span></span> <span data-ttu-id="d309e-312">Os cabeçalhos de segurança de exemplo a seguir mostram o layout estrito para um modo de autenticação específico.</span><span class="sxs-lookup"><span data-stu-id="d309e-312">The following example security headers show the Strict layout for a given authentication mode.</span></span>  
  
 <span data-ttu-id="d309e-313">O valor da propriedade "Chaves derivadas" para os tokens em todos os casos é "false".</span><span class="sxs-lookup"><span data-stu-id="d309e-313">The value of the "Derived Keys" property for the tokens in all cases is "false".</span></span>  
  
 <span data-ttu-id="d309e-314">Os valores de várias propriedades da associação de transporte são da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="d309e-314">The values of the various properties of the transport binding are as follows:</span></span>  
  
 <span data-ttu-id="d309e-315">Carimbo de hora: true</span><span class="sxs-lookup"><span data-stu-id="d309e-315">Timestamp: true</span></span>  
  
 <span data-ttu-id="d309e-316">Layout de cabeçalho de segurança: estrito</span><span class="sxs-lookup"><span data-stu-id="d309e-316">Security Header Layout: Strict</span></span>  
  
 <span data-ttu-id="d309e-317">Conjunto de algoritmos: Basic256</span><span class="sxs-lookup"><span data-stu-id="d309e-317">Algorithm Suite: Basic256</span></span>  
  
#### <a name="611-usernameovertransport"></a><span data-ttu-id="d309e-318">6.1.1 UsernameOverTransport</span><span class="sxs-lookup"><span data-stu-id="d309e-318">6.1.1 UsernameOverTransport</span></span>  
 <span data-ttu-id="d309e-319">Com esse modo de autenticação, o cliente autentica com um Token de nome de usuário que aparece na camada de SOAP como um token de suporte assinado que é sempre enviado do iniciador para o destinatário.</span><span class="sxs-lookup"><span data-stu-id="d309e-319">With this authentication mode, the client authenticates with a Username Token which appears at the SOAP layer as a signed supporting token that is always sent from the initiator to the recipient.</span></span> <span data-ttu-id="d309e-320">O serviço é autenticado usando um certificado x. 509 na camada de transporte.</span><span class="sxs-lookup"><span data-stu-id="d309e-320">The service is authenticated using an X.509 certificate at the transport layer.</span></span> <span data-ttu-id="d309e-321">A associação usada é uma associação de transporte.</span><span class="sxs-lookup"><span data-stu-id="d309e-321">The binding used is a transport binding.</span></span>  
  
 <span data-ttu-id="d309e-322">Política</span><span class="sxs-lookup"><span data-stu-id="d309e-322">Policy</span></span>  
  
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
  
 <span data-ttu-id="d309e-323">Layout de cabeçalho de segurança</span><span class="sxs-lookup"><span data-stu-id="d309e-323">Security Header Layout</span></span>  
  
 <span data-ttu-id="d309e-324">Solicitação</span><span class="sxs-lookup"><span data-stu-id="d309e-324">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wsse:UsernameToken ... >  
  ...  
  </wsse:UsernameToken>  
</wsse:Security>  
```  
  
 <span data-ttu-id="d309e-325">Resposta</span><span class="sxs-lookup"><span data-stu-id="d309e-325">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
#### <a name="612-certificateovertransport"></a><span data-ttu-id="d309e-326">6.1.2 CertificateOverTransport</span><span class="sxs-lookup"><span data-stu-id="d309e-326">6.1.2 CertificateOverTransport</span></span>  
 <span data-ttu-id="d309e-327">Com esse modo de autenticação que o cliente autentica com um x. 509 do certificado que aparece na camada de SOAP como um token de suporte de endosso que é sempre enviado do iniciador para o destinatário.</span><span class="sxs-lookup"><span data-stu-id="d309e-327">With this authentication mode the client authenticates using an X.509 certificate which appears at the SOAP layer as an endorsing supporting token that is always sent from the initiator to the recipient.</span></span> <span data-ttu-id="d309e-328">O serviço é autenticado usando um certificado x. 509 na camada de transporte.</span><span class="sxs-lookup"><span data-stu-id="d309e-328">The service is authenticated using an X.509 certificate at the transport layer.</span></span> <span data-ttu-id="d309e-329">A associação usada é uma associação de transporte.</span><span class="sxs-lookup"><span data-stu-id="d309e-329">The binding used is a transport binding.</span></span>  
  
 <span data-ttu-id="d309e-330">Política</span><span class="sxs-lookup"><span data-stu-id="d309e-330">Policy</span></span>  
  
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
  
 <span data-ttu-id="d309e-331">Layout de cabeçalho de segurança</span><span class="sxs-lookup"><span data-stu-id="d309e-331">Security Header Layout</span></span>  
  
 <span data-ttu-id="d309e-332">Solicitação</span><span class="sxs-lookup"><span data-stu-id="d309e-332">Request</span></span>  
  
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
  
 <span data-ttu-id="d309e-333">Resposta</span><span class="sxs-lookup"><span data-stu-id="d309e-333">Response</span></span>  
  
```xml  
<o:Security>  
  <u:Timestamp u:Id="_0">  
  ...  
  </u:Timestamp>  
</o:Security>  
```  
  
#### <a name="613-issuedtokenovertransport"></a><span data-ttu-id="d309e-334">6.1.3 IssuedTokenOverTransport</span><span class="sxs-lookup"><span data-stu-id="d309e-334">6.1.3 IssuedTokenOverTransport</span></span>  
 <span data-ttu-id="d309e-335">Com esse modo de autenticação o cliente não autentica para o serviço, como tal, mas em vez disso, apresenta um token emitido por um Token de segurança Service (STS) e comprova conhecimento de uma chave compartilhada.</span><span class="sxs-lookup"><span data-stu-id="d309e-335">With this authentication mode the client does not authenticate to the service, as such, but rather presents a token issued by a Security Token Service (STS) and proves knowledge of a shared key.</span></span> <span data-ttu-id="d309e-336">O token emitido é exibido na camada de SOAP como um token de suporte de endosso que é sempre enviado do iniciador para o destinatário.</span><span class="sxs-lookup"><span data-stu-id="d309e-336">The issued token appears at the SOAP layer as an endorsing supporting token that is always sent from the initiator to the recipient.</span></span> <span data-ttu-id="d309e-337">O serviço é autenticado usando um certificado x. 509 na camada de transporte.</span><span class="sxs-lookup"><span data-stu-id="d309e-337">The service is authenticated using an X.509 certificate at the transport layer.</span></span> <span data-ttu-id="d309e-338">A associação é uma associação de transporte.</span><span class="sxs-lookup"><span data-stu-id="d309e-338">The binding is a transport binding.</span></span>  
  
 <span data-ttu-id="d309e-339">Política</span><span class="sxs-lookup"><span data-stu-id="d309e-339">Policy</span></span>  
  
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
  
 <span data-ttu-id="d309e-340">Layout de cabeçalho de segurança</span><span class="sxs-lookup"><span data-stu-id="d309e-340">Security Header Layout</span></span>  
  
 <span data-ttu-id="d309e-341">Solicitação</span><span class="sxs-lookup"><span data-stu-id="d309e-341">Request</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1" >  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <saml:Assertion ...>  
  ...  
  </saml:Assertion>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
</wsse:Security>  
```  
  
 <span data-ttu-id="d309e-342">Resposta</span><span class="sxs-lookup"><span data-stu-id="d309e-342">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
#### <a name="614-kerberosovertransport"></a><span data-ttu-id="d309e-343">6.1.4 KerberosOverTransport</span><span class="sxs-lookup"><span data-stu-id="d309e-343">6.1.4 KerberosOverTransport</span></span>  
 <span data-ttu-id="d309e-344">Com esse modo de autenticação o cliente autentica para o serviço usando um tíquete Kerberos.</span><span class="sxs-lookup"><span data-stu-id="d309e-344">With this authentication mode the client authenticates to the service using a Kerberos ticket.</span></span> <span data-ttu-id="d309e-345">O token Kerberos aparece na camada de SOAP como um token de suporte de endosso.</span><span class="sxs-lookup"><span data-stu-id="d309e-345">The Kerberos token appears at the SOAP layer as an endorsing supporting token.</span></span> <span data-ttu-id="d309e-346">O serviço é autenticado usando um certificado x. 509 na camada de transporte.</span><span class="sxs-lookup"><span data-stu-id="d309e-346">The service is authenticated using an X.509 certificate at the transport layer.</span></span> <span data-ttu-id="d309e-347">A associação é uma associação de transporte.</span><span class="sxs-lookup"><span data-stu-id="d309e-347">The binding is a transport binding.</span></span>  
  
 <span data-ttu-id="d309e-348">Política</span><span class="sxs-lookup"><span data-stu-id="d309e-348">Policy</span></span>  
  
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
  
 <span data-ttu-id="d309e-349">Layout de cabeçalho de segurança</span><span class="sxs-lookup"><span data-stu-id="d309e-349">Security Header Layout</span></span>  
  
 <span data-ttu-id="d309e-350">Solicitação</span><span class="sxs-lookup"><span data-stu-id="d309e-350">Request</span></span>  
  
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
  
 <span data-ttu-id="d309e-351">Resposta</span><span class="sxs-lookup"><span data-stu-id="d309e-351">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
#### <a name="615-sspinegotiatedovertransport"></a><span data-ttu-id="d309e-352">6.1.5 SspiNegotiatedOverTransport</span><span class="sxs-lookup"><span data-stu-id="d309e-352">6.1.5 SspiNegotiatedOverTransport</span></span>  
 <span data-ttu-id="d309e-353">Com esse modo, um protocolo de negociação é usado para realizar a autenticação de cliente e servidor.</span><span class="sxs-lookup"><span data-stu-id="d309e-353">With this mode a negotiation protocol is used to perform client and server authentication.</span></span> <span data-ttu-id="d309e-354">Kerberos é usado, se possível, caso contrário NTLM.</span><span class="sxs-lookup"><span data-stu-id="d309e-354">Kerberos is used if possible, otherwise NTLM.</span></span> <span data-ttu-id="d309e-355">O SCT resultante aparece na camada de SOAP como um token de suporte de endosso que é sempre enviado do iniciador ao destinatário.</span><span class="sxs-lookup"><span data-stu-id="d309e-355">The resulting SCT appears at the SOAP layer as an endorsing supporting token that is always sent from initiator to recipient.</span></span> <span data-ttu-id="d309e-356">Além disso, o serviço é autenticado na camada de transporte por um certificado x. 509.</span><span class="sxs-lookup"><span data-stu-id="d309e-356">The service is additionally authenticated at the transport layer by an X.509 certificate.</span></span> <span data-ttu-id="d309e-357">A associação usada é uma associação de transporte.</span><span class="sxs-lookup"><span data-stu-id="d309e-357">The binding used is a transport binding.</span></span> <span data-ttu-id="d309e-358">"SPNEGO" (negociação) descreve como o WCF usa o protocolo de negociação binária SSPI com WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="d309e-358">"SPNEGO" (negotiation) describes how WCF uses SSPI binary negotiation protocol with WS-Trust.</span></span> <span data-ttu-id="d309e-359">Exemplos de cabeçalho de segurança nesta seção são depois que o SCT foi estabelecida por meio de handshake SPNEGO.</span><span class="sxs-lookup"><span data-stu-id="d309e-359">Security header examples in this section are after the SCT has been established through the SPNEGO handshake.</span></span>  
  
 <span data-ttu-id="d309e-360">Política</span><span class="sxs-lookup"><span data-stu-id="d309e-360">Policy</span></span>  
  
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
  
### <a name="security-header-examples"></a><span data-ttu-id="d309e-361">Exemplos de cabeçalho de segurança</span><span class="sxs-lookup"><span data-stu-id="d309e-361">Security Header Examples</span></span>  
 <span data-ttu-id="d309e-362">Quando o Token de contexto de segurança é estabelecido por meio de handshake SPNEGO usando negociação binária do WS-Trust, as mensagens de aplicativo têm cabeçalhos de segurança com a seguinte estrutura.</span><span class="sxs-lookup"><span data-stu-id="d309e-362">Once the Security Context Token is established through SPNEGO handshake using WS-Trust Binary Negotiation, the application messages have security headers with the following structure.</span></span>  
  
 <span data-ttu-id="d309e-363">Solicitação</span><span class="sxs-lookup"><span data-stu-id="d309e-363">Request</span></span>  
  
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
  
 <span data-ttu-id="d309e-364">Resposta</span><span class="sxs-lookup"><span data-stu-id="d309e-364">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
### <a name="62-using-x509-certificates-for-service-authentication"></a><span data-ttu-id="d309e-365">6.2 usando certificados x. 509 para autenticação de serviço</span><span class="sxs-lookup"><span data-stu-id="d309e-365">6.2 Using X.509 Certificates for Service Authentication</span></span>  
 <span data-ttu-id="d309e-366">Esta seção descreve os seguintes modos de autenticação: MutualCertificate WSS1.0, CertificateDuplex mútua, MutualCertificate WSS1.1, AnonymousForCertificate, UserNameForCertificate e IssuedTokenForCertificate.</span><span class="sxs-lookup"><span data-stu-id="d309e-366">This section describes the following authentication modes: MutualCertificate WSS1.0, Mutual CertificateDuplex, MutualCertificate WSS1.1, AnonymousForCertificate, UserNameForCertificate and IssuedTokenForCertificate.</span></span>  
  
#### <a name="621-mutualcertificate-wss10"></a><span data-ttu-id="d309e-367">6.2.1 MutualCertificate WSS1.0</span><span class="sxs-lookup"><span data-stu-id="d309e-367">6.2.1 MutualCertificate WSS1.0</span></span>  
 <span data-ttu-id="d309e-368">Com esse modo de autenticação que o cliente autentica com um x. 509 do certificado que aparece na camada de SOAP que o token de iniciador.</span><span class="sxs-lookup"><span data-stu-id="d309e-368">With this authentication mode the client authenticates using an X.509 certificate which appears at the SOAP layer as the initiator token.</span></span> <span data-ttu-id="d309e-369">O serviço também é autenticado usando um certificado x. 509.</span><span class="sxs-lookup"><span data-stu-id="d309e-369">The service is also authenticated using an X.509 certificate.</span></span>  
  
 <span data-ttu-id="d309e-370">A associação usada é uma associação assimétrica com os seguintes valores de propriedade:</span><span class="sxs-lookup"><span data-stu-id="d309e-370">The binding used is an asymmetric binding with the following property values:</span></span>  
  
 <span data-ttu-id="d309e-371">Token de iniciador: o certificado do cliente x. 509, com o modo de inclusão definido como .../IncludeToken/AlwaysToRecipient</span><span class="sxs-lookup"><span data-stu-id="d309e-371">Initiator Token: the client’s X.509 certificate, with inclusion mode set to …/IncludeToken/AlwaysToRecipient</span></span>  
  
 <span data-ttu-id="d309e-372">Token de destinatário: Servidor do certificado x. 509, com o modo de inclusão é definido .../IncludeToken/Never</span><span class="sxs-lookup"><span data-stu-id="d309e-372">Recipient Token: Server’s X.509 Certificate, with inclusion mode is set …/IncludeToken/Never</span></span>  
  
 <span data-ttu-id="d309e-373">Proteção de token: False</span><span class="sxs-lookup"><span data-stu-id="d309e-373">Token Protection: False</span></span>  
  
 <span data-ttu-id="d309e-374">Todo cabeçalho e corpo assinaturas: True</span><span class="sxs-lookup"><span data-stu-id="d309e-374">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="d309e-375">Ordem de proteção: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="d309e-375">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="d309e-376">Criptografar assinatura: True</span><span class="sxs-lookup"><span data-stu-id="d309e-376">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="d309e-377">Política</span><span class="sxs-lookup"><span data-stu-id="d309e-377">Policy</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="d309e-378">Exemplos de cabeçalho de segurança: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="d309e-378">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="d309e-379">Solicitação</span><span class="sxs-lookup"><span data-stu-id="d309e-379">Request</span></span>  
  
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
  
 <span data-ttu-id="d309e-380">Resposta</span><span class="sxs-lookup"><span data-stu-id="d309e-380">Response</span></span>  
  
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
  
 <span data-ttu-id="d309e-381">Exemplos de cabeçalho de segurança: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="d309e-381">Security Header Examples: EncryptBeforeSign</span></span>  
  
 <span data-ttu-id="d309e-382">Solicitação</span><span class="sxs-lookup"><span data-stu-id="d309e-382">Request</span></span>  
  
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
  
 <span data-ttu-id="d309e-383">Resposta</span><span class="sxs-lookup"><span data-stu-id="d309e-383">Response</span></span>  
  
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
  
#### <a name="622-mutualcertificateduplex"></a><span data-ttu-id="d309e-384">6.2.2 MutualCertificateDuplex</span><span class="sxs-lookup"><span data-stu-id="d309e-384">6.2.2 MutualCertificateDuplex</span></span>  
 <span data-ttu-id="d309e-385">Com esse modo de autenticação que o cliente autentica com um x. 509 do certificado que aparece na camada de SOAP que o token de iniciador.</span><span class="sxs-lookup"><span data-stu-id="d309e-385">With this authentication mode the client authenticates using an X.509 certificate which appears at the SOAP layer as the initiator token.</span></span> <span data-ttu-id="d309e-386">O serviço também é autenticado usando um certificado x. 509.</span><span class="sxs-lookup"><span data-stu-id="d309e-386">The service is also authenticated using an X.509 certificate.</span></span>  
  
 <span data-ttu-id="d309e-387">A associação usada é uma associação assimétrica com os seguintes valores de propriedade:</span><span class="sxs-lookup"><span data-stu-id="d309e-387">The binding used is an asymmetric binding with the following property values:</span></span>  
  
 <span data-ttu-id="d309e-388">Token de iniciador: X509 do cliente certificado, o modo de inclusão estiver definido como .../IncludeToken/AlwaysToRecipient</span><span class="sxs-lookup"><span data-stu-id="d309e-388">Initiator Token: Client’s X509 Certificate, inclusion mode is set to …/IncludeToken/AlwaysToRecipient</span></span>  
  
 <span data-ttu-id="d309e-389">Token de destinatário: X509 do servidor certificado, o modo de inclusão estiver definido como .../IncludeToken/AlwaysToInitiator</span><span class="sxs-lookup"><span data-stu-id="d309e-389">Recipient Token: Server’s X509 Certificate, inclusion mode is set to …/IncludeToken/AlwaysToInitiator</span></span>  
  
 <span data-ttu-id="d309e-390">Proteção de token: False</span><span class="sxs-lookup"><span data-stu-id="d309e-390">Token Protection: False</span></span>  
  
 <span data-ttu-id="d309e-391">Todo cabeçalho e corpo assinaturas: True</span><span class="sxs-lookup"><span data-stu-id="d309e-391">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="d309e-392">Ordem de proteção: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="d309e-392">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="d309e-393">Criptografar assinatura: True</span><span class="sxs-lookup"><span data-stu-id="d309e-393">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="d309e-394">Política</span><span class="sxs-lookup"><span data-stu-id="d309e-394">Policy</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="d309e-395">Exemplos de cabeçalho de segurança: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="d309e-395">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="d309e-396">Solicitação e resposta</span><span class="sxs-lookup"><span data-stu-id="d309e-396">Request and Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="d309e-397">Exemplos de cabeçalho de segurança: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="d309e-397">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="d309e-398">Solicitação e resposta</span><span class="sxs-lookup"><span data-stu-id="d309e-398">Request and Response</span></span>  
  
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
  
#### <a name="623-using-symmetricbinding-with-x509-service-authentication"></a><span data-ttu-id="d309e-399">6.2.3 usando SymmetricBinding com a autenticação do serviço x. 509</span><span class="sxs-lookup"><span data-stu-id="d309e-399">6.2.3 Using SymmetricBinding with X.509 Service Authentication</span></span>  
 <span data-ttu-id="d309e-400">"WSS10" fornecido suporte limitado para cenários com X509 tokens.</span><span class="sxs-lookup"><span data-stu-id="d309e-400">"WSS10" provided limited support for scenarios with X509 tokens.</span></span> <span data-ttu-id="d309e-401">Por exemplo, não havia uma maneira para fornecer proteção de assinatura e criptografia de mensagens usando apenas o token de serviço X509.</span><span class="sxs-lookup"><span data-stu-id="d309e-401">For example, there was no way to provide signature and encryption protection for messages using only service X509 token.</span></span> <span data-ttu-id="d309e-402">"WSS11" introduziu o uso de EncryptedKey como um token simétrico.</span><span class="sxs-lookup"><span data-stu-id="d309e-402">"WSS11" introduced the usage of EncryptedKey as a symmetric token.</span></span> <span data-ttu-id="d309e-403">Agora, uma chave temporária criptografada para o certificado de x. 509 do serviço pode ser usada para proteção de mensagens de solicitação e resposta.</span><span class="sxs-lookup"><span data-stu-id="d309e-403">Now a temporary key encrypted for the service's X.509 certificate could be used for both request and response messages protection.</span></span> <span data-ttu-id="d309e-404">Os modos de autenticação descritos na seção 6.4 abaixo usam esse padrão.</span><span class="sxs-lookup"><span data-stu-id="d309e-404">The authentication modes described in the section 6.4 below use this pattern.</span></span>  
  
 <span data-ttu-id="d309e-405">O WS-SecurityPolicy descreve esse padrão usando SymmetricBinding com o serviço de token X509 como o token de proteção.</span><span class="sxs-lookup"><span data-stu-id="d309e-405">WS-SecurityPolicy describes this pattern using SymmetricBinding with Service X509 token as the protection token.</span></span>  
  
 <span data-ttu-id="d309e-406">Modos de autenticação AnonymousForCertificate, UsernameForCertificate, MutualCertificate WSS11 e IssuedTokenForCertificate todos usam uma instância semelhante de sp:SymmetricBinding com os seguintes valores de propriedade:</span><span class="sxs-lookup"><span data-stu-id="d309e-406">Authentication modes AnonymousForCertificate, UsernameForCertificate, MutualCertificate WSS11 and IssuedTokenForCertificate all use a similar instance of sp:SymmetricBinding with the following property values:</span></span>  
  
 <span data-ttu-id="d309e-407">Token de proteção: X509 do servidor certificado, o modo de inclusão estiver definido como .../IncludeToken/Never</span><span class="sxs-lookup"><span data-stu-id="d309e-407">Protection Token: Server’s X509 Certificate, inclusion mode is set to .../IncludeToken/Never</span></span>  
<span data-ttu-id="d309e-408">Proteção de token: False</span><span class="sxs-lookup"><span data-stu-id="d309e-408">Token Protection: False</span></span>  
  
 <span data-ttu-id="d309e-409">Todo cabeçalho e corpo assinaturas: True</span><span class="sxs-lookup"><span data-stu-id="d309e-409">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="d309e-410">Ordem de proteção: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="d309e-410">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="d309e-411">Criptografar assinatura: True</span><span class="sxs-lookup"><span data-stu-id="d309e-411">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="d309e-412">Os modos de autenticação acima diferem apenas por tokens de suporte que eles usam.</span><span class="sxs-lookup"><span data-stu-id="d309e-412">The above authentication modes only differ by the supporting tokens they use.</span></span> <span data-ttu-id="d309e-413">AnonymousForCertificate não tem todos os tokens de suporte, MutualCertificate WSS 1.1 tem o cliente do certificado X509 como um endossando dar suporte a tokens, UserNameForCertificate tem um Token de nome de usuário como um token de suporte assinado e IssuedTokenForCertificate tem o token emitido como um token de suporte de endosso.</span><span class="sxs-lookup"><span data-stu-id="d309e-413">AnonymousForCertificate does not have any supporting tokens, MutualCertificate WSS 1.1 has the client’s X509 certificate as an endorsing supporting tokens, UserNameForCertificate has a UserName Token as a signed supporting token and IssuedTokenForCertificate has the issued token as an endorsing supporting token.</span></span>  
  
 <span data-ttu-id="d309e-414">Política</span><span class="sxs-lookup"><span data-stu-id="d309e-414">Policy</span></span>  
  
 <span data-ttu-id="d309e-415">Vinculação simétrica</span><span class="sxs-lookup"><span data-stu-id="d309e-415">Symmetric Binding</span></span>  
  
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
  
#### <a name="624-anonymousforcertificate"></a><span data-ttu-id="d309e-416">6.2.4 AnonymousForCertificate</span><span class="sxs-lookup"><span data-stu-id="d309e-416">6.2.4 AnonymousForCertificate</span></span>  
 <span data-ttu-id="d309e-417">Com esse modo de autenticação o cliente é anônimo e o serviço é autenticado usando um certificado x. 509.</span><span class="sxs-lookup"><span data-stu-id="d309e-417">With this authentication mode the client is anonymous and the service is authenticated using an X.509 certificate.</span></span> <span data-ttu-id="d309e-418">A associação usada é uma instância de associação simétrica, conforme descrito em 6.4.2.</span><span class="sxs-lookup"><span data-stu-id="d309e-418">The binding used is an instance of symmetric binding as described in 6.4.2.</span></span>  
  
 <span data-ttu-id="d309e-419">Política</span><span class="sxs-lookup"><span data-stu-id="d309e-419">Policy</span></span>  
  
 <span data-ttu-id="d309e-420">Consulte "Política" 6.2.3 acima para obter detalhes de associação</span><span class="sxs-lookup"><span data-stu-id="d309e-420">See "Policy" in 6.2.3 above for binding details</span></span>  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="d309e-421">Exemplos de cabeçalho de segurança: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="d309e-421">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="d309e-422">Solicitação</span><span class="sxs-lookup"><span data-stu-id="d309e-422">Request</span></span>  
  
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
  
 <span data-ttu-id="d309e-423">Resposta</span><span class="sxs-lookup"><span data-stu-id="d309e-423">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="d309e-424">Exemplos de cabeçalho de segurança: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="d309e-424">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="d309e-425">Solicitação</span><span class="sxs-lookup"><span data-stu-id="d309e-425">Request</span></span>  
  
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
  
 <span data-ttu-id="d309e-426">Resposta</span><span class="sxs-lookup"><span data-stu-id="d309e-426">Response</span></span>  
  
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
  
#### <a name="625-usernameforcertificate"></a><span data-ttu-id="d309e-427">6.2.5 UserNameForCertificate</span><span class="sxs-lookup"><span data-stu-id="d309e-427">6.2.5 UserNameForCertificate</span></span>  
 <span data-ttu-id="d309e-428">Com esse modo de autenticação o cliente autentica para o serviço usando um Token de nome de usuário que aparece na camada de SOAP como um token de suporte assinado.</span><span class="sxs-lookup"><span data-stu-id="d309e-428">With this authentication mode the client authenticates to the service using a Username Token which appears at the SOAP layer as a signed supporting token.</span></span> <span data-ttu-id="d309e-429">O serviço autentica o cliente usando um certificado x. 509.</span><span class="sxs-lookup"><span data-stu-id="d309e-429">The service authenticates to the client using an X.509 certificate.</span></span> <span data-ttu-id="d309e-430">A associação usada é uma associação simétrica com o token de proteção sendo uma chave gerada pelo cliente, criptografado com a chave pública do serviço.</span><span class="sxs-lookup"><span data-stu-id="d309e-430">The binding used is a symmetric binding with the protection token being a key generated by the client, encrypted with the public key of the service.</span></span>  
  
 <span data-ttu-id="d309e-431">Política</span><span class="sxs-lookup"><span data-stu-id="d309e-431">Policy</span></span>  
  
 <span data-ttu-id="d309e-432">Consulte "Política" 6.2.3 acima para obter detalhes de associação</span><span class="sxs-lookup"><span data-stu-id="d309e-432">See "Policy" in 6.2.3 above for binding details</span></span>  
  
 <span data-ttu-id="d309e-433">Assinatura de Token de suporte</span><span class="sxs-lookup"><span data-stu-id="d309e-433">Signed Supporting Token</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="d309e-434">Exemplos de cabeçalho de segurança: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="d309e-434">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="d309e-435">Solicitação</span><span class="sxs-lookup"><span data-stu-id="d309e-435">Request</span></span>  
  
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
  
 <span data-ttu-id="d309e-436">Resposta</span><span class="sxs-lookup"><span data-stu-id="d309e-436">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="d309e-437">Exemplos de cabeçalho de segurança: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="d309e-437">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="d309e-438">Solicitação</span><span class="sxs-lookup"><span data-stu-id="d309e-438">Request</span></span>  
  
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
  
 <span data-ttu-id="d309e-439">Resposta</span><span class="sxs-lookup"><span data-stu-id="d309e-439">Response</span></span>  
  
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
  
#### <a name="626-mutualcertificate-wss-11"></a><span data-ttu-id="d309e-440">6.2.6 MutualCertificate (WSS 1.1)</span><span class="sxs-lookup"><span data-stu-id="d309e-440">6.2.6 MutualCertificate (WSS 1.1)</span></span>  
 <span data-ttu-id="d309e-441">Com esse modo de autenticação que o cliente autentica com um x. 509 do certificado que aparece na camada de SOAP como um token de suporte de endosso.</span><span class="sxs-lookup"><span data-stu-id="d309e-441">With this authentication mode the client authenticates using an X.509 certificate which appears at the SOAP layer as an endorsing supporting token.</span></span> <span data-ttu-id="d309e-442">O serviço também é autenticado usando um certificado x. 509.</span><span class="sxs-lookup"><span data-stu-id="d309e-442">The service is also authenticated using an X.509 certificate.</span></span> <span data-ttu-id="d309e-443">A associação usada é uma associação simétrica com o token de proteção sendo uma chave gerada pelo cliente, criptografado com a chave pública do serviço.</span><span class="sxs-lookup"><span data-stu-id="d309e-443">The binding used is a symmetric binding with the protection token being a key generated by the client, encrypted with the public key of the service.</span></span>  
  
 <span data-ttu-id="d309e-444">Política</span><span class="sxs-lookup"><span data-stu-id="d309e-444">Policy</span></span>  
  
 <span data-ttu-id="d309e-445">Consulte a política em 6.2.3 para os detalhes da associação</span><span class="sxs-lookup"><span data-stu-id="d309e-445">See Policy in 6.2.3 for binding details</span></span>  
  
 <span data-ttu-id="d309e-446">Endossando o Token de suporte</span><span class="sxs-lookup"><span data-stu-id="d309e-446">Endorsing Supporting Token</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="d309e-447">Exemplos de cabeçalho de segurança: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="d309e-447">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="d309e-448">Solicitação</span><span class="sxs-lookup"><span data-stu-id="d309e-448">Request</span></span>  
  
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
  
 <span data-ttu-id="d309e-449">Resposta</span><span class="sxs-lookup"><span data-stu-id="d309e-449">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="d309e-450">Exemplos de cabeçalho de segurança: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="d309e-450">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="d309e-451">Solicitação</span><span class="sxs-lookup"><span data-stu-id="d309e-451">Request</span></span>  
  
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
  
 <span data-ttu-id="d309e-452">Resposta</span><span class="sxs-lookup"><span data-stu-id="d309e-452">Response</span></span>  
  
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
  
#### <a name="627-issuedtokenforcertificate"></a><span data-ttu-id="d309e-453">6.2.7 IssuedTokenForCertificate</span><span class="sxs-lookup"><span data-stu-id="d309e-453">6.2.7 IssuedTokenForCertificate</span></span>  
 <span data-ttu-id="d309e-454">Com essa autenticação o cliente não autenticar para o serviço, como tal, mas em vez disso, o modo apresenta um token emitido por um STS e comprova conhecimento de uma chave compartilhada.</span><span class="sxs-lookup"><span data-stu-id="d309e-454">With this authentication mode the client does not authenticate to the service, as such, but instead presents a token issued by a STS and proves knowledge of a shared key.</span></span> <span data-ttu-id="d309e-455">O token emitido é exibido na camada de SOAP como um token de suporte de endosso.</span><span class="sxs-lookup"><span data-stu-id="d309e-455">The issued token appears at the SOAP layer as an endorsing supporting token.</span></span> <span data-ttu-id="d309e-456">O serviço autentica o cliente usando um certificado x. 509.</span><span class="sxs-lookup"><span data-stu-id="d309e-456">The service authenticates to the client using an X.509 certificate.</span></span> <span data-ttu-id="d309e-457">A associação usada é uma associação simétrica com o token de proteção sendo uma chave gerada pelo cliente, criptografado com a chave pública do serviço.</span><span class="sxs-lookup"><span data-stu-id="d309e-457">The binding used is a symmetric binding with the protection token being a key generated by the client, encrypted with the public key of the service.</span></span>  
  
 <span data-ttu-id="d309e-458">Política</span><span class="sxs-lookup"><span data-stu-id="d309e-458">Policy</span></span>  
  
 <span data-ttu-id="d309e-459">Consulte a política em 6.2.3 acima para obter detalhes de associação</span><span class="sxs-lookup"><span data-stu-id="d309e-459">See Policy in 6.2.3 above for binding details</span></span>  
  
 <span data-ttu-id="d309e-460">Endossando o Token de suporte</span><span class="sxs-lookup"><span data-stu-id="d309e-460">Endorsing Supporting Token</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="d309e-461">Exemplos de cabeçalho de segurança: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="d309e-461">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="d309e-462">Solicitação</span><span class="sxs-lookup"><span data-stu-id="d309e-462">Request</span></span>  
  
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
  
 <span data-ttu-id="d309e-463">Resposta</span><span class="sxs-lookup"><span data-stu-id="d309e-463">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="d309e-464">Exemplos de cabeçalho de segurança: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="d309e-464">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="d309e-465">Solicitação</span><span class="sxs-lookup"><span data-stu-id="d309e-465">Request</span></span>  
  
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
  
 <span data-ttu-id="d309e-466">Resposta</span><span class="sxs-lookup"><span data-stu-id="d309e-466">Response</span></span>  
  
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
  
## <a name="63-kerberos"></a><span data-ttu-id="d309e-467">6.3 Kerberos</span><span class="sxs-lookup"><span data-stu-id="d309e-467">6.3 Kerberos</span></span>  
 <span data-ttu-id="d309e-468">Com esse modo de autenticação o cliente autentica para o serviço usando um tíquete Kerberos.</span><span class="sxs-lookup"><span data-stu-id="d309e-468">With this authentication mode the client authenticates to the service using a Kerberos ticket.</span></span> <span data-ttu-id="d309e-469">Esse tíquete mesmo também fornece autenticação de servidor.</span><span class="sxs-lookup"><span data-stu-id="d309e-469">That same ticket also provides server authentication.</span></span> <span data-ttu-id="d309e-470">A associação usada é uma associação simétrica com as seguintes propriedades;</span><span class="sxs-lookup"><span data-stu-id="d309e-470">The binding used is a symmetric binding with the following properties;</span></span>  
  
 <span data-ttu-id="d309e-471">Token de proteção: Tíquete Kerberos, o modo de inclusão estiver definido como .../IncludeToken/Once</span><span class="sxs-lookup"><span data-stu-id="d309e-471">Protection Token: Kerberos Ticket, inclusion mode is set to .../IncludeToken/Once</span></span>  
<span data-ttu-id="d309e-472">Proteção de token: False</span><span class="sxs-lookup"><span data-stu-id="d309e-472">Token Protection: False</span></span>  
  
 <span data-ttu-id="d309e-473">Todo cabeçalho e corpo assinaturas: True</span><span class="sxs-lookup"><span data-stu-id="d309e-473">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="d309e-474">Ordem de proteção: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="d309e-474">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="d309e-475">Criptografar assinatura: True</span><span class="sxs-lookup"><span data-stu-id="d309e-475">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="d309e-476">Política</span><span class="sxs-lookup"><span data-stu-id="d309e-476">Policy</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="d309e-477">Exemplos de cabeçalho de segurança: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="d309e-477">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="d309e-478">Solicitação</span><span class="sxs-lookup"><span data-stu-id="d309e-478">Request</span></span>  
  
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
  
 <span data-ttu-id="d309e-479">Resposta</span><span class="sxs-lookup"><span data-stu-id="d309e-479">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="d309e-480">Exemplos de cabeçalho de segurança: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="d309e-480">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="d309e-481">Solicitação</span><span class="sxs-lookup"><span data-stu-id="d309e-481">Request</span></span>  
  
```xml  
<wsse:Security>  
TBD  
</wsse:Security>  
```  
  
 <span data-ttu-id="d309e-482">Resposta</span><span class="sxs-lookup"><span data-stu-id="d309e-482">Response</span></span>  
  
```xml  
<wsse:Security>  
TBD  
</wsse:Security>  
```  
  
#### <a name="64-issuedtoken"></a><span data-ttu-id="d309e-483">6.4 IssuedToken</span><span class="sxs-lookup"><span data-stu-id="d309e-483">6.4 IssuedToken</span></span>  
 <span data-ttu-id="d309e-484">Com esse modo de autenticação que o cliente não autenticar para o serviço, assim, em vez disso, o cliente apresenta um token emitido por um STS e comprova conhecimento de uma chave compartilhada.</span><span class="sxs-lookup"><span data-stu-id="d309e-484">With this authentication mode the client does not authenticate to the service, as such, rather the client presents a token issued by an STS and proves knowledge of a shared key.</span></span> <span data-ttu-id="d309e-485">O serviço não é autenticado para o cliente, como tal, em vez disso, o STS criptografa a chave compartilhada como parte do token emitido, de modo que apenas o serviço possa descriptografar a chave.</span><span class="sxs-lookup"><span data-stu-id="d309e-485">The service is not authenticated to the client, as such, instead the STS encrypts the shared key as part of the issued token such that only the service can decrypt the key.</span></span> <span data-ttu-id="d309e-486">A associação usada é simétrica associação com as seguintes propriedades;</span><span class="sxs-lookup"><span data-stu-id="d309e-486">The binding used is as symmetric binding with the following properties;</span></span>  
  
 <span data-ttu-id="d309e-487">Modo de inclusão de Token de proteção: O Token emitido, é definido como .../IncludeToken/AlwaysToRecipient</span><span class="sxs-lookup"><span data-stu-id="d309e-487">Protection Token: Issued Token, inclusion mode is set to .../IncludeToken/AlwaysToRecipient</span></span>  
<span data-ttu-id="d309e-488">Proteção de token: False</span><span class="sxs-lookup"><span data-stu-id="d309e-488">Token Protection: False</span></span>  
  
 <span data-ttu-id="d309e-489">Todo cabeçalho e corpo assinaturas: True</span><span class="sxs-lookup"><span data-stu-id="d309e-489">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="d309e-490">Ordem de proteção: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="d309e-490">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="d309e-491">Criptografar assinatura: True</span><span class="sxs-lookup"><span data-stu-id="d309e-491">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="d309e-492">Política</span><span class="sxs-lookup"><span data-stu-id="d309e-492">Policy</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="d309e-493">Exemplos de cabeçalho de segurança: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="d309e-493">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="d309e-494">Solicitação</span><span class="sxs-lookup"><span data-stu-id="d309e-494">Request</span></span>  
  
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
  
 <span data-ttu-id="d309e-495">Resposta</span><span class="sxs-lookup"><span data-stu-id="d309e-495">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="d309e-496">Exemplos de cabeçalho de segurança: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="d309e-496">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="d309e-497">Solicitação</span><span class="sxs-lookup"><span data-stu-id="d309e-497">Request</span></span>  
  
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
  
 <span data-ttu-id="d309e-498">Resposta</span><span class="sxs-lookup"><span data-stu-id="d309e-498">Response</span></span>  
  
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
  
### <a name="65-using-sslnegotiated-for-service-authentication"></a><span data-ttu-id="d309e-499">6.5 usando SslNegotiated para autenticação de serviço</span><span class="sxs-lookup"><span data-stu-id="d309e-499">6.5 Using SslNegotiated for Service Authentication</span></span>  
 <span data-ttu-id="d309e-500">Esta seção descreve um grupo de modos de autenticação que usa uma associação simétrica com o token de proteção sendo um Token de contexto de segurança por WS-SecureConversation (WS-SC) cujo valor da chave é negociado executando o protocolo TLS sobre WS-Trust (WS-F) primeira / Mensagens RSTR.</span><span class="sxs-lookup"><span data-stu-id="d309e-500">This section describes a group of authentication modes that use a symmetric binding with the protection token being a Security Context Token per WS-SecureConversation (WS-SC) whose key value is negotiated by executing the TLS protocol over WS-Trust (WS-T) RST/RSTR messages.</span></span> <span data-ttu-id="d309e-501">Detalhes da implementação de handshake TLS usando o WS-Trust são descritos em TLSNEGO.</span><span class="sxs-lookup"><span data-stu-id="d309e-501">Details of the TLS handshake implementation using WS-Trust are described in TLSNEGO.</span></span> <span data-ttu-id="d309e-502">Veja os exemplos de mensagem, vamos pressupor que SCT com um contexto de segurança associadas já está estabelecida por meio de um handshake.</span><span class="sxs-lookup"><span data-stu-id="d309e-502">Here in the message examples we will assume that SCT with an associated security context is already established through a handshake.</span></span>  
  
 <span data-ttu-id="d309e-503">A associação usada é uma associação simétrica com as seguintes propriedades;</span><span class="sxs-lookup"><span data-stu-id="d309e-503">The binding used is a symmetric binding with the following properties;</span></span>  
  
 <span data-ttu-id="d309e-504">Token de proteção: SslContextToken, modo de inclusão estiver definido como .../IncludeToken/Never</span><span class="sxs-lookup"><span data-stu-id="d309e-504">Protection Token: SslContextToken, inclusion mode is set to .../IncludeToken/Never</span></span>  
<span data-ttu-id="d309e-505">Proteção de token: False</span><span class="sxs-lookup"><span data-stu-id="d309e-505">Token Protection: False</span></span>  
  
 <span data-ttu-id="d309e-506">Todo cabeçalho e corpo assinaturas: True</span><span class="sxs-lookup"><span data-stu-id="d309e-506">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="d309e-507">Ordem de proteção: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="d309e-507">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="d309e-508">Criptografar assinatura: True</span><span class="sxs-lookup"><span data-stu-id="d309e-508">Encrypt Signature: True</span></span>  
  
#### <a name="651-policy-for-sslnegotiated-service-authentication"></a><span data-ttu-id="d309e-509">6.5.1 política de para autenticação do serviço SslNegotiated</span><span class="sxs-lookup"><span data-stu-id="d309e-509">6.5.1 Policy for SslNegotiated service authentication</span></span>  
 <span data-ttu-id="d309e-510">Política para todos os modos de autenticação nesta seção são semelhante e diferem apenas por específicas de suporte assinado ou endossando tokens usados.</span><span class="sxs-lookup"><span data-stu-id="d309e-510">Policy for all authentication modes in this section are similar and differ only by specific signed supporting or endorsing tokens used.</span></span>  
  
```xml  
<wsp:Policy wsu:Id='SslNegotiated_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:SymmetricBinding>  
        <wsp:Policy>  
          <sp:ProtectionToken>  
            <wsp:Policy>  
              <mssp:SslContextToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' />  
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
  
#### <a name="652-anonymousforsslnegotiated"></a><span data-ttu-id="d309e-511">6.5.2 AnonymousForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="d309e-511">6.5.2 AnonymousForSslNegotiated</span></span>  
 <span data-ttu-id="d309e-512">Com esse modo de autenticação o cliente é anônimo e o serviço é autenticado usando um certificado x. 509.</span><span class="sxs-lookup"><span data-stu-id="d309e-512">With this authentication mode the client is anonymous and the service is authenticated using an X.509 certificate.</span></span> <span data-ttu-id="d309e-513">A associação usada é uma instância de associação simétrica, conforme descrito em 6.5.1 acima.</span><span class="sxs-lookup"><span data-stu-id="d309e-513">The binding used is an instance of symmetric binding as described in 6.5.1 above.</span></span>  
  
 <span data-ttu-id="d309e-514">Política</span><span class="sxs-lookup"><span data-stu-id="d309e-514">Policy</span></span>  
  
 <span data-ttu-id="d309e-515">Consulte a política em 6.5.1 acima para obter detalhes de associação.</span><span class="sxs-lookup"><span data-stu-id="d309e-515">See Policy in 6.5.1 above for binding details.</span></span>  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="d309e-516">Exemplos de cabeçalho de segurança: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="d309e-516">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="d309e-517">Solicitação</span><span class="sxs-lookup"><span data-stu-id="d309e-517">Request</span></span>  
  
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
  
 <span data-ttu-id="d309e-518">Resposta</span><span class="sxs-lookup"><span data-stu-id="d309e-518">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="d309e-519">Exemplos de cabeçalho de segurança: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="d309e-519">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="d309e-520">Solicitação</span><span class="sxs-lookup"><span data-stu-id="d309e-520">Request</span></span>  
  
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
  
 <span data-ttu-id="d309e-521">Resposta</span><span class="sxs-lookup"><span data-stu-id="d309e-521">Response</span></span>  
  
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
  
#### <a name="653-usernameforsslnegotiated"></a><span data-ttu-id="d309e-522">6.5.3 UserNameForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="d309e-522">6.5.3 UserNameForSslNegotiated</span></span>  
 <span data-ttu-id="d309e-523">Com essa autenticação modo que é o cliente autentica usando um Token de nome de usuário que aparece na camada de SOAP como um token de suporte assinado.</span><span class="sxs-lookup"><span data-stu-id="d309e-523">With this authentication mode the client is authenticates using a Username Token which appears at the SOAP layer as a signed supporting token.</span></span> <span data-ttu-id="d309e-524">O serviço é autenticado usando um certificado x. 509.</span><span class="sxs-lookup"><span data-stu-id="d309e-524">The service is authenticated using an X.509 certificate.</span></span> <span data-ttu-id="d309e-525">A associação usada é uma instância de associação simétrica, conforme descrito em 6.5.1.</span><span class="sxs-lookup"><span data-stu-id="d309e-525">The binding used is an instance of symmetric binding as described in 6.5.1.</span></span>  
  
 <span data-ttu-id="d309e-526">Política</span><span class="sxs-lookup"><span data-stu-id="d309e-526">Policy</span></span>  
  
 <span data-ttu-id="d309e-527">Consulte a seção 6.5.1 acima para obter detalhes de associação</span><span class="sxs-lookup"><span data-stu-id="d309e-527">See section 6.5.1 above for binding details</span></span>  
  
 <span data-ttu-id="d309e-528">Assinatura de Token de suporte</span><span class="sxs-lookup"><span data-stu-id="d309e-528">Signed Supporting Token</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="d309e-529">Exemplos de cabeçalho de segurança: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="d309e-529">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="d309e-530">Solicitação</span><span class="sxs-lookup"><span data-stu-id="d309e-530">Request</span></span>  
  
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
  
 <span data-ttu-id="d309e-531">Resposta</span><span class="sxs-lookup"><span data-stu-id="d309e-531">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="d309e-532">Exemplos de cabeçalho de segurança: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="d309e-532">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="d309e-533">Solicitação</span><span class="sxs-lookup"><span data-stu-id="d309e-533">Request</span></span>  
  
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
  
 <span data-ttu-id="d309e-534">Resposta</span><span class="sxs-lookup"><span data-stu-id="d309e-534">Response</span></span>  
  
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
  
#### <a name="654-issuedtokenforsslnegotiated"></a><span data-ttu-id="d309e-535">6.5.4 IssuedTokenForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="d309e-535">6.5.4 IssuedTokenForSslNegotiated</span></span>  
 <span data-ttu-id="d309e-536">Com essa autenticação o cliente não autenticar para o serviço, como tal, mas em vez disso, o modo apresenta um token emitido por um STS e comprova conhecimento de uma chave compartilhada.</span><span class="sxs-lookup"><span data-stu-id="d309e-536">With this authentication mode the client does not authenticate to the service, as such, but instead presents a token issued by an STS and proves knowledge of a shared key.</span></span> <span data-ttu-id="d309e-537">O token emitido é exibido na camada de SOAP como um token de suporte de endosso.</span><span class="sxs-lookup"><span data-stu-id="d309e-537">The issued token appears at the SOAP layer as an endorsing supporting token.</span></span> <span data-ttu-id="d309e-538">O serviço é autenticado usando um certificado x. 509.</span><span class="sxs-lookup"><span data-stu-id="d309e-538">The service is authenticated using an X.509 certificate.</span></span> <span data-ttu-id="d309e-539">A associação usada é uma instância de associação simétrica, conforme descrito em 6.5.1 acima.</span><span class="sxs-lookup"><span data-stu-id="d309e-539">The binding used is an instance of symmetric binding as described in 6.5.1 above.</span></span>  
  
 <span data-ttu-id="d309e-540">Política</span><span class="sxs-lookup"><span data-stu-id="d309e-540">Policy</span></span>  
  
 <span data-ttu-id="d309e-541">Consulte a seção 6.5.1 acima para obter detalhes de associação</span><span class="sxs-lookup"><span data-stu-id="d309e-541">See section 6.5.1 above for binding details</span></span>  
  
 <span data-ttu-id="d309e-542">Endossando o Token de suporte</span><span class="sxs-lookup"><span data-stu-id="d309e-542">Endorsing Supporting Token</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="d309e-543">Exemplos de cabeçalho de segurança: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="d309e-543">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="d309e-544">Solicitação</span><span class="sxs-lookup"><span data-stu-id="d309e-544">Request</span></span>  
  
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
  
 <span data-ttu-id="d309e-545">Resposta</span><span class="sxs-lookup"><span data-stu-id="d309e-545">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="d309e-546">Exemplos de cabeçalho de segurança: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="d309e-546">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="d309e-547">Solicitação</span><span class="sxs-lookup"><span data-stu-id="d309e-547">Request</span></span>  
  
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
  
 <span data-ttu-id="d309e-548">Resposta</span><span class="sxs-lookup"><span data-stu-id="d309e-548">Response</span></span>  
  
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
  
#### <a name="655-mutualsslnegotiated"></a><span data-ttu-id="d309e-549">6.5.5 MutualSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="d309e-549">6.5.5 MutualSslNegotiated</span></span>  
 <span data-ttu-id="d309e-550">Com esse modo de autenticação o cliente e o serviço de autenticação usando certificados x. 509.</span><span class="sxs-lookup"><span data-stu-id="d309e-550">With this authentication mode the client and the service authenticate using X.509 certificates.</span></span> <span data-ttu-id="d309e-551">A associação usada é uma instância de associação simétrica, conforme descrito em 6.5.1 acima.</span><span class="sxs-lookup"><span data-stu-id="d309e-551">The binding used is an instance of symmetric binding as described in 6.5.1 above.</span></span>  
  
 <span data-ttu-id="d309e-552">Política</span><span class="sxs-lookup"><span data-stu-id="d309e-552">Policy</span></span>  
  
 <span data-ttu-id="d309e-553">Consulte a seção 6.5.1 acima para obter detalhes de associação</span><span class="sxs-lookup"><span data-stu-id="d309e-553">See section 6.5.1 above for binding details</span></span>  
  
 <span data-ttu-id="d309e-554">Endossando o Token de suporte</span><span class="sxs-lookup"><span data-stu-id="d309e-554">Endorsing Supporting Token</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="d309e-555">Exemplos de cabeçalho de segurança: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="d309e-555">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="d309e-556">Solicitação</span><span class="sxs-lookup"><span data-stu-id="d309e-556">Request</span></span>  
  
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
  
 <span data-ttu-id="d309e-557">Resposta</span><span class="sxs-lookup"><span data-stu-id="d309e-557">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="d309e-558">Exemplos de cabeçalho de segurança: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="d309e-558">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="d309e-559">Solicitação</span><span class="sxs-lookup"><span data-stu-id="d309e-559">Request</span></span>  
  
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
  
 <span data-ttu-id="d309e-560">Resposta</span><span class="sxs-lookup"><span data-stu-id="d309e-560">Response</span></span>  
  
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
  
### <a name="66-sspinegotiated"></a><span data-ttu-id="d309e-561">6.6 SspiNegotiated</span><span class="sxs-lookup"><span data-stu-id="d309e-561">6.6 SspiNegotiated</span></span>  
 <span data-ttu-id="d309e-562">Com esse modo de autenticação, um protocolo de negociação é usado para realizar a autenticação de cliente e servidor.</span><span class="sxs-lookup"><span data-stu-id="d309e-562">With this authentication mode a negotiation protocol is used to perform client and server authentication.</span></span> <span data-ttu-id="d309e-563">Kerberos é usado, se possível, caso contrário NTLM.</span><span class="sxs-lookup"><span data-stu-id="d309e-563">Kerberos is used if possible, otherwise NTLM.</span></span> <span data-ttu-id="d309e-564">A associação usada é uma associação simétrica com as seguintes propriedades;</span><span class="sxs-lookup"><span data-stu-id="d309e-564">The binding used is a symmetric binding with the following properties;</span></span>  
  
 <span data-ttu-id="d309e-565">Token de proteção: SpnegoContextToken, modo de inclusão estiver definido como .../IncludeToken/AlwaysToRecipient</span><span class="sxs-lookup"><span data-stu-id="d309e-565">Protection Token: SpnegoContextToken, inclusion mode is set to .../IncludeToken/AlwaysToRecipient</span></span>  
<span data-ttu-id="d309e-566">Proteção de token: False</span><span class="sxs-lookup"><span data-stu-id="d309e-566">Token Protection: False</span></span>  
  
 <span data-ttu-id="d309e-567">Todo cabeçalho e corpo assinaturas: True</span><span class="sxs-lookup"><span data-stu-id="d309e-567">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="d309e-568">Ordem de proteção: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="d309e-568">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="d309e-569">Criptografar assinatura: True</span><span class="sxs-lookup"><span data-stu-id="d309e-569">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="d309e-570">Política</span><span class="sxs-lookup"><span data-stu-id="d309e-570">Policy</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="d309e-571">Exemplos de cabeçalho de segurança: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="d309e-571">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="d309e-572">Solicitação</span><span class="sxs-lookup"><span data-stu-id="d309e-572">Request</span></span>  
  
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
  
 <span data-ttu-id="d309e-573">Resposta</span><span class="sxs-lookup"><span data-stu-id="d309e-573">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="d309e-574">Exemplos de cabeçalho de segurança: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="d309e-574">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="d309e-575">Solicitação</span><span class="sxs-lookup"><span data-stu-id="d309e-575">Request</span></span>  
  
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
  
 <span data-ttu-id="d309e-576">Resposta</span><span class="sxs-lookup"><span data-stu-id="d309e-576">Response</span></span>  
  
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
  
### <a name="67-secureconversation"></a><span data-ttu-id="d309e-577">6.7 SecureConversation</span><span class="sxs-lookup"><span data-stu-id="d309e-577">6.7 SecureConversation</span></span>  
 <span data-ttu-id="d309e-578">A associação usada é uma associação simétrica com o token de proteção sendo um SCT por WS-SecureConversation (WS-SC).</span><span class="sxs-lookup"><span data-stu-id="d309e-578">The binding used is a symmetric binding with the protection token being a SCT per WS-SecureConversation (WS-SC).</span></span> <span data-ttu-id="d309e-579">O SCT é negociada com o WS-Trust (WS-Trust) ou WS-SecureConversation (WS-SC) acordo com uma associação aninhada, que também é uma associação simétrica que usa um protocolo de negociação.</span><span class="sxs-lookup"><span data-stu-id="d309e-579">The SCT is negotiated using WS-Trust (WS-Trust) or WS-SecureConversation (WS-SC) according to a nested binding, which is itself a symmetric binding that uses a negotiation protocol.</span></span> <span data-ttu-id="d309e-580">O protocolo de negociação usará o Kerberos para realizar a autenticação de cliente e servidor se possível.</span><span class="sxs-lookup"><span data-stu-id="d309e-580">The negotiation protocol will use Kerberos to perform client and server authentication if possible.</span></span> <span data-ttu-id="d309e-581">Se Kerberos não pode ser usado, ele retornará a NTLM.</span><span class="sxs-lookup"><span data-stu-id="d309e-581">If Kerberos cannot be used, it will fall back to NTLM.</span></span>  
  
 <span data-ttu-id="d309e-582">Política</span><span class="sxs-lookup"><span data-stu-id="d309e-582">Policy</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="d309e-583">Exemplos de cabeçalho de segurança: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="d309e-583">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="d309e-584">Solicitação</span><span class="sxs-lookup"><span data-stu-id="d309e-584">Request</span></span>  
  
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
  
 <span data-ttu-id="d309e-585">Resposta</span><span class="sxs-lookup"><span data-stu-id="d309e-585">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="d309e-586">Exemplos de cabeçalho de segurança: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="d309e-586">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="d309e-587">Solicitação</span><span class="sxs-lookup"><span data-stu-id="d309e-587">Request</span></span>  
  
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
  
 <span data-ttu-id="d309e-588">Resposta</span><span class="sxs-lookup"><span data-stu-id="d309e-588">Response</span></span>  
  
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
