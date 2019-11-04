---
title: Protocolos de segurança versão 1.0
ms.date: 03/30/2017
ms.assetid: ee3402d2-1076-410b-a3cb-fae0372bd7af
ms.openlocfilehash: e22150d21638cffdf804008c32285f900bb1e263
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459047"
---
# <a name="security-protocols-version-10"></a><span data-ttu-id="82f52-102">Protocolos de segurança versão 1.0</span><span class="sxs-lookup"><span data-stu-id="82f52-102">Security Protocols version 1.0</span></span>
<span data-ttu-id="82f52-103">Os protocolos especificação Web Services Security fornecem mecanismos de segurança de serviços da Web que abrangem todos os requisitos de segurança de mensagens empresariais existentes.</span><span class="sxs-lookup"><span data-stu-id="82f52-103">The Web Services Security Protocols provide Web services security mechanisms that cover all existing enterprise messaging security requirements.</span></span> <span data-ttu-id="82f52-104">Esta seção descreve os detalhes da versão 1,0 do Windows Communication Foundation (WCF) (implementados no <xref:System.ServiceModel.Channels.SecurityBindingElement>) para os seguintes protocolos de segurança de serviços da Web.</span><span class="sxs-lookup"><span data-stu-id="82f52-104">This section describes the Windows Communication Foundation (WCF) version 1.0 details (implemented in the <xref:System.ServiceModel.Channels.SecurityBindingElement>) for the following Web services security protocols.</span></span>  
  
|<span data-ttu-id="82f52-105">Especificação/documento</span><span class="sxs-lookup"><span data-stu-id="82f52-105">Specification/Document</span></span>|<span data-ttu-id="82f52-106">Link</span><span class="sxs-lookup"><span data-stu-id="82f52-106">Link</span></span>|  
|-|-|  
|<span data-ttu-id="82f52-107">WSS: segurança de mensagem SOAP 1,0</span><span class="sxs-lookup"><span data-stu-id="82f52-107">WSS: SOAP Message Security 1.0</span></span>|<https://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0.pdf>|
|<span data-ttu-id="82f52-108">WSS: nome do perfil do token 1,0</span><span class="sxs-lookup"><span data-stu-id="82f52-108">WSS: Username Token Profile 1.0</span></span>|<https://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0.pdf>|
|<span data-ttu-id="82f52-109">WSS: perfil de token X509 1,0</span><span class="sxs-lookup"><span data-stu-id="82f52-109">WSS: X509 Token Profile 1.0</span></span>|<https://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-x509-token-profile-1.0.pdf>|
|<span data-ttu-id="82f52-110">WSS: perfil de token 1,1 SAML 1,0</span><span class="sxs-lookup"><span data-stu-id="82f52-110">WSS: SAML 1.1 Token Profile 1.0</span></span>|<https://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.0.pdf>|
|<span data-ttu-id="82f52-111">WSS: segurança de mensagem SOAP 1,1</span><span class="sxs-lookup"><span data-stu-id="82f52-111">WSS: SOAP Message Security 1.1</span></span>|<https://www.oasis-open.org/committees/download.php/16790/wss-v1.1-spec-os-SOAPMessageSecurity.pdf>|
|<span data-ttu-id="82f52-112">Perfil de token de nome de usuário do WSS 1,1</span><span class="sxs-lookup"><span data-stu-id="82f52-112">WSS Username Token Profile 1.1</span></span>|<https://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0.pdf>|
|<span data-ttu-id="82f52-113">WSS: X. 509 o perfil de token 1,1</span><span class="sxs-lookup"><span data-stu-id="82f52-113">WSS: X.509 Token Profile 1.1</span></span>|<https://www.oasis-open.org/committees/download.php/16785/wss-v1.1-spec-os-x509TokenProfile.pdf>|
|<span data-ttu-id="82f52-114">WSS: perfil de token Kerberos 1,1</span><span class="sxs-lookup"><span data-stu-id="82f52-114">WSS: Kerberos Token Profile 1.1</span></span>|<https://www.oasis-open.org/committees/download.php/16788/wss-v1.1-spec-os-KerberosTokenProfile.pdf>|
|<span data-ttu-id="82f52-115">WSS: perfil de token 1,1 SAML 1,1</span><span class="sxs-lookup"><span data-stu-id="82f52-115">WSS: SAML 1.1 Token Profile 1.1</span></span>|<https://www.oasis-open.org/committees/download.php/16768/wss-v1.1-spec-os-SAMLTokenProfile.pdf>|
|<span data-ttu-id="82f52-116">Conversa WS-Secure</span><span class="sxs-lookup"><span data-stu-id="82f52-116">WS-Secure Conversation</span></span>|<https://specs.xmlsoap.org/ws/2005/02/sc/WS-SecureConversation.pdf>|
|<span data-ttu-id="82f52-117">WS-Trust</span><span class="sxs-lookup"><span data-stu-id="82f52-117">WS-Trust</span></span>|<https://specs.xmlsoap.org/ws/2005/02/trust/ws-trust.pdf>|
|<span data-ttu-id="82f52-118">Observação do aplicativo:</span><span class="sxs-lookup"><span data-stu-id="82f52-118">Application Note:</span></span><br /><br /> <span data-ttu-id="82f52-119">Usando WS-Trust para handshake de TLS</span><span class="sxs-lookup"><span data-stu-id="82f52-119">Using WS-Trust for TLS Handshake</span></span>|<span data-ttu-id="82f52-120">A ser publicado</span><span class="sxs-lookup"><span data-stu-id="82f52-120">To be published</span></span>|  
|<span data-ttu-id="82f52-121">Observação do aplicativo:</span><span class="sxs-lookup"><span data-stu-id="82f52-121">Application Note:</span></span><br /><br /> <span data-ttu-id="82f52-122">Usando WS-Trust para SPNEGO</span><span class="sxs-lookup"><span data-stu-id="82f52-122">Using WS-Trust for SPNEGO</span></span>|<span data-ttu-id="82f52-123">A ser publicado</span><span class="sxs-lookup"><span data-stu-id="82f52-123">To be published</span></span>|  
|<span data-ttu-id="82f52-124">Observação do aplicativo:</span><span class="sxs-lookup"><span data-stu-id="82f52-124">Application Note:</span></span><br /><br /> <span data-ttu-id="82f52-125">Serviços Web que endereçam referências e identidades de ponto de extremidade</span><span class="sxs-lookup"><span data-stu-id="82f52-125">Web Services Addressing Endpoint References And Identity</span></span>|<span data-ttu-id="82f52-126">A ser publicado</span><span class="sxs-lookup"><span data-stu-id="82f52-126">To be published</span></span>|  
|<span data-ttu-id="82f52-127">WS-SecurityPolicy 1,1</span><span class="sxs-lookup"><span data-stu-id="82f52-127">WS-SecurityPolicy 1.1</span></span><br /><br /> <span data-ttu-id="82f52-128">(2005/07)</span><span class="sxs-lookup"><span data-stu-id="82f52-128">(2005/07)</span></span>|<https://specs.xmlsoap.org/ws/2005/07/securitypolicy/ws-securitypolicy.pdf><br /><br /> <span data-ttu-id="82f52-129">conforme alterado por [errata](https://lists.oasis-open.org/archives/ws-sx/200512/msg00017.html) enviada para o comitê técnico WS-SX Oasis</span><span class="sxs-lookup"><span data-stu-id="82f52-129">as amended by [errata](https://lists.oasis-open.org/archives/ws-sx/200512/msg00017.html) submitted to OASIS WS-SX Technical Committee</span></span> |  
  
 <span data-ttu-id="82f52-130">O WCF, versão 1, fornece 17 modos de autenticação que podem ser usados como base para a configuração de segurança de serviços Web.</span><span class="sxs-lookup"><span data-stu-id="82f52-130">WCF, version 1, provides 17 authentication modes that can be used as the basis for Web services security configuration.</span></span> <span data-ttu-id="82f52-131">Cada modo é otimizado para um conjunto comum de requisitos de implantação, como:</span><span class="sxs-lookup"><span data-stu-id="82f52-131">Each mode is optimized for a common set of deployment requirements, such as:</span></span>  
  
- <span data-ttu-id="82f52-132">Credenciais usadas para autenticar o cliente e o serviço.</span><span class="sxs-lookup"><span data-stu-id="82f52-132">Credentials used to authenticate client and service.</span></span>  
  
- <span data-ttu-id="82f52-133">Mecanismos de proteção de segurança de mensagens ou transporte.</span><span class="sxs-lookup"><span data-stu-id="82f52-133">Message or transport security protection mechanisms.</span></span>  
  
- <span data-ttu-id="82f52-134">Padrões de troca de mensagens.</span><span class="sxs-lookup"><span data-stu-id="82f52-134">Message exchange patterns.</span></span>  
  
|<span data-ttu-id="82f52-135">Modo de autenticação</span><span class="sxs-lookup"><span data-stu-id="82f52-135">Authentication Mode</span></span>|<span data-ttu-id="82f52-136">Autenticação de cliente</span><span class="sxs-lookup"><span data-stu-id="82f52-136">Client Authentication</span></span>|<span data-ttu-id="82f52-137">Autenticação do servidor</span><span class="sxs-lookup"><span data-stu-id="82f52-137">Server Authentication</span></span>|<span data-ttu-id="82f52-138">Modo</span><span class="sxs-lookup"><span data-stu-id="82f52-138">Mode</span></span>|  
|-------------------------|---------------------------|---------------------------|----------|  
|<span data-ttu-id="82f52-139">UserNameOverTransport</span><span class="sxs-lookup"><span data-stu-id="82f52-139">UserNameOverTransport</span></span>|<span data-ttu-id="82f52-140">Nome de usuário/senha</span><span class="sxs-lookup"><span data-stu-id="82f52-140">User name/password</span></span>|<span data-ttu-id="82f52-141">X509</span><span class="sxs-lookup"><span data-stu-id="82f52-141">X509</span></span>|<span data-ttu-id="82f52-142">Porta</span><span class="sxs-lookup"><span data-stu-id="82f52-142">Transport</span></span>|  
|<span data-ttu-id="82f52-143">CertificateOverTransport</span><span class="sxs-lookup"><span data-stu-id="82f52-143">CertificateOverTransport</span></span>|<span data-ttu-id="82f52-144">X509</span><span class="sxs-lookup"><span data-stu-id="82f52-144">X509</span></span>|<span data-ttu-id="82f52-145">X509</span><span class="sxs-lookup"><span data-stu-id="82f52-145">X509</span></span>|<span data-ttu-id="82f52-146">Porta</span><span class="sxs-lookup"><span data-stu-id="82f52-146">Transport</span></span>|  
|<span data-ttu-id="82f52-147">KerberosOverTransport</span><span class="sxs-lookup"><span data-stu-id="82f52-147">KerberosOverTransport</span></span>|<span data-ttu-id="82f52-148">Windows</span><span class="sxs-lookup"><span data-stu-id="82f52-148">Windows</span></span>|<span data-ttu-id="82f52-149">X509</span><span class="sxs-lookup"><span data-stu-id="82f52-149">X509</span></span>|<span data-ttu-id="82f52-150">Porta</span><span class="sxs-lookup"><span data-stu-id="82f52-150">Transport</span></span>|  
|<span data-ttu-id="82f52-151">IssuedTokenOverTransport</span><span class="sxs-lookup"><span data-stu-id="82f52-151">IssuedTokenOverTransport</span></span>|<span data-ttu-id="82f52-152">Federado</span><span class="sxs-lookup"><span data-stu-id="82f52-152">Federated</span></span>|<span data-ttu-id="82f52-153">X509</span><span class="sxs-lookup"><span data-stu-id="82f52-153">X509</span></span>|<span data-ttu-id="82f52-154">Porta</span><span class="sxs-lookup"><span data-stu-id="82f52-154">Transport</span></span>|  
|<span data-ttu-id="82f52-155">SspiNegotiatedOverTransport</span><span class="sxs-lookup"><span data-stu-id="82f52-155">SspiNegotiatedOverTransport</span></span>|<span data-ttu-id="82f52-156">Windows SSPI negociado</span><span class="sxs-lookup"><span data-stu-id="82f52-156">Windows Sspi Negotiated</span></span>|<span data-ttu-id="82f52-157">Windows SSPI negociado</span><span class="sxs-lookup"><span data-stu-id="82f52-157">Windows Sspi Negotiated</span></span>|<span data-ttu-id="82f52-158">Porta</span><span class="sxs-lookup"><span data-stu-id="82f52-158">Transport</span></span>|  
|<span data-ttu-id="82f52-159">AnonymousForCertificate</span><span class="sxs-lookup"><span data-stu-id="82f52-159">AnonymousForCertificate</span></span>|<span data-ttu-id="82f52-160">Nenhum</span><span class="sxs-lookup"><span data-stu-id="82f52-160">None</span></span>|<span data-ttu-id="82f52-161">X509</span><span class="sxs-lookup"><span data-stu-id="82f52-161">X509</span></span>|<span data-ttu-id="82f52-162">Mensagem</span><span class="sxs-lookup"><span data-stu-id="82f52-162">Message</span></span>|  
|<span data-ttu-id="82f52-163">UserNameForCertificate</span><span class="sxs-lookup"><span data-stu-id="82f52-163">UserNameForCertificate</span></span>|<span data-ttu-id="82f52-164">Nome de usuário/senha</span><span class="sxs-lookup"><span data-stu-id="82f52-164">User name/password</span></span>|<span data-ttu-id="82f52-165">X509</span><span class="sxs-lookup"><span data-stu-id="82f52-165">X509</span></span>|<span data-ttu-id="82f52-166">Mensagem</span><span class="sxs-lookup"><span data-stu-id="82f52-166">Message</span></span>|  
|<span data-ttu-id="82f52-167">MutualCertificate</span><span class="sxs-lookup"><span data-stu-id="82f52-167">MutualCertificate</span></span>|<span data-ttu-id="82f52-168">X509</span><span class="sxs-lookup"><span data-stu-id="82f52-168">X509</span></span>|<span data-ttu-id="82f52-169">X509</span><span class="sxs-lookup"><span data-stu-id="82f52-169">X509</span></span>|<span data-ttu-id="82f52-170">Mensagem</span><span class="sxs-lookup"><span data-stu-id="82f52-170">Message</span></span>|  
|<span data-ttu-id="82f52-171">MutualCertificateDuplex</span><span class="sxs-lookup"><span data-stu-id="82f52-171">MutualCertificateDuplex</span></span>|<span data-ttu-id="82f52-172">X509</span><span class="sxs-lookup"><span data-stu-id="82f52-172">X509</span></span>|<span data-ttu-id="82f52-173">X509</span><span class="sxs-lookup"><span data-stu-id="82f52-173">X509</span></span>|<span data-ttu-id="82f52-174">Mensagem</span><span class="sxs-lookup"><span data-stu-id="82f52-174">Message</span></span>|  
|<span data-ttu-id="82f52-175">IssuedTokenForCertificate</span><span class="sxs-lookup"><span data-stu-id="82f52-175">IssuedTokenForCertificate</span></span>|<span data-ttu-id="82f52-176">Federado</span><span class="sxs-lookup"><span data-stu-id="82f52-176">Federated</span></span>|<span data-ttu-id="82f52-177">X509</span><span class="sxs-lookup"><span data-stu-id="82f52-177">X509</span></span>|<span data-ttu-id="82f52-178">Mensagem</span><span class="sxs-lookup"><span data-stu-id="82f52-178">Message</span></span>|  
|<span data-ttu-id="82f52-179">Kerberos</span><span class="sxs-lookup"><span data-stu-id="82f52-179">Kerberos</span></span>|<span data-ttu-id="82f52-180">Windows</span><span class="sxs-lookup"><span data-stu-id="82f52-180">Windows</span></span>|<span data-ttu-id="82f52-181">Windows</span><span class="sxs-lookup"><span data-stu-id="82f52-181">Windows</span></span>|<span data-ttu-id="82f52-182">Mensagem</span><span class="sxs-lookup"><span data-stu-id="82f52-182">Message</span></span>|  
|<span data-ttu-id="82f52-183">IssuedToken</span><span class="sxs-lookup"><span data-stu-id="82f52-183">IssuedToken</span></span>|<span data-ttu-id="82f52-184">Federado</span><span class="sxs-lookup"><span data-stu-id="82f52-184">Federated</span></span>|<span data-ttu-id="82f52-185">Federado</span><span class="sxs-lookup"><span data-stu-id="82f52-185">Federated</span></span>|<span data-ttu-id="82f52-186">Mensagem</span><span class="sxs-lookup"><span data-stu-id="82f52-186">Message</span></span>|  
|<span data-ttu-id="82f52-187">SspiNegotiated</span><span class="sxs-lookup"><span data-stu-id="82f52-187">SspiNegotiated</span></span>|<span data-ttu-id="82f52-188">Windows SSPI negociado</span><span class="sxs-lookup"><span data-stu-id="82f52-188">Windows Sspi Negotiated</span></span>|<span data-ttu-id="82f52-189">Windows SSPI negociado</span><span class="sxs-lookup"><span data-stu-id="82f52-189">Windows Sspi Negotiated</span></span>|<span data-ttu-id="82f52-190">Mensagem</span><span class="sxs-lookup"><span data-stu-id="82f52-190">Message</span></span>|  
|<span data-ttu-id="82f52-191">AnonymousForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="82f52-191">AnonymousForSslNegotiated</span></span>|<span data-ttu-id="82f52-192">Nenhum</span><span class="sxs-lookup"><span data-stu-id="82f52-192">None</span></span>|<span data-ttu-id="82f52-193">X509, TLS-nego</span><span class="sxs-lookup"><span data-stu-id="82f52-193">X509, TLS-Nego</span></span>|<span data-ttu-id="82f52-194">Mensagem</span><span class="sxs-lookup"><span data-stu-id="82f52-194">Message</span></span>|  
|<span data-ttu-id="82f52-195">UserNameForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="82f52-195">UserNameForSslNegotiated</span></span>|<span data-ttu-id="82f52-196">Nome de usuário/senha</span><span class="sxs-lookup"><span data-stu-id="82f52-196">User name/password</span></span>|<span data-ttu-id="82f52-197">X509, TLS-nego</span><span class="sxs-lookup"><span data-stu-id="82f52-197">X509, TLS-Nego</span></span>|<span data-ttu-id="82f52-198">Mensagem</span><span class="sxs-lookup"><span data-stu-id="82f52-198">Message</span></span>|  
|<span data-ttu-id="82f52-199">MutualSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="82f52-199">MutualSslNegotiated</span></span>|<span data-ttu-id="82f52-200">X509</span><span class="sxs-lookup"><span data-stu-id="82f52-200">X509</span></span>|<span data-ttu-id="82f52-201">X509, TLS-nego</span><span class="sxs-lookup"><span data-stu-id="82f52-201">X509, TLS-Nego</span></span>|<span data-ttu-id="82f52-202">Mensagem</span><span class="sxs-lookup"><span data-stu-id="82f52-202">Message</span></span>|  
|<span data-ttu-id="82f52-203">IssuedTokenForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="82f52-203">IssuedTokenForSslNegotiated</span></span>|<span data-ttu-id="82f52-204">Federado</span><span class="sxs-lookup"><span data-stu-id="82f52-204">Federated</span></span>|<span data-ttu-id="82f52-205">X509, TLS-nego</span><span class="sxs-lookup"><span data-stu-id="82f52-205">X509, TLS-Nego</span></span>|<span data-ttu-id="82f52-206">Mensagem</span><span class="sxs-lookup"><span data-stu-id="82f52-206">Message</span></span>|  
  
 <span data-ttu-id="82f52-207">Os pontos de extremidade que usam esses modos de autenticação podem expressar seus requisitos de segurança usando WS-SecurityPolicy (WS-SP).</span><span class="sxs-lookup"><span data-stu-id="82f52-207">Endpoints using such authentication modes can express their security requirements using WS-SecurityPolicy (WS-SP).</span></span> <span data-ttu-id="82f52-208">Este documento descreve a estrutura de mensagens de cabeçalho e de infraestrutura de segurança para cada modo de autenticação e fornece exemplos de políticas e mensagens.</span><span class="sxs-lookup"><span data-stu-id="82f52-208">This document describes the structure of security header and infrastructure messages for each authentication mode and provides examples of policies and messages.</span></span>  
  
 <span data-ttu-id="82f52-209">O WCF aproveita o WS-SecureConversation para fornecer suporte a sessões seguras para proteger as trocas de várias mensagens entre aplicativos.</span><span class="sxs-lookup"><span data-stu-id="82f52-209">WCF leverages WS-SecureConversation to provide secure sessions support to protect multi-message exchanges between applications.</span></span>  <span data-ttu-id="82f52-210">Consulte "sessões seguras" abaixo para obter detalhes de implementação.</span><span class="sxs-lookup"><span data-stu-id="82f52-210">See "Secure Sessions" below for implementation details.</span></span>  
  
 <span data-ttu-id="82f52-211">Além dos modos de autenticação, o WCF fornece configurações para controlar mecanismos de proteção comuns que se aplicam à maioria dos modos de autenticação baseados em segurança de mensagem, por exemplo: ordem de assinatura versus operações de criptografia, conjuntos de algoritmos, derivação de chave e confirmação de assinatura.</span><span class="sxs-lookup"><span data-stu-id="82f52-211">In addition to authentication modes, WCF provides settings to control common protection mechanisms that apply to most message security-based authentication modes, for example: order of signature versus encryption operations, algorithm suites, key derivation, and signature confirmation.</span></span>  
  
 <span data-ttu-id="82f52-212">Os seguintes prefixos e namespaces são usados neste documento.</span><span class="sxs-lookup"><span data-stu-id="82f52-212">The following prefixes and namespaces are used in this document.</span></span>  
  
|<span data-ttu-id="82f52-213">Prefixo</span><span class="sxs-lookup"><span data-stu-id="82f52-213">Prefix</span></span>|<span data-ttu-id="82f52-214">espaço de nome</span><span class="sxs-lookup"><span data-stu-id="82f52-214">Namespace</span></span>|  
|------------|---------------|  
|<span data-ttu-id="82f52-215">s</span><span class="sxs-lookup"><span data-stu-id="82f52-215">s</span></span>|<http://www.w3.org/2003/05/soap-envelope/>|
|<span data-ttu-id="82f52-216">SP3</span><span class="sxs-lookup"><span data-stu-id="82f52-216">sp</span></span>|<http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/>|
|<span data-ttu-id="82f52-217">a</span><span class="sxs-lookup"><span data-stu-id="82f52-217">a</span></span>|<http://www.w3.org/2005/08/addressing>|  
|<span data-ttu-id="82f52-218">wsse</span><span class="sxs-lookup"><span data-stu-id="82f52-218">wsse</span></span>|<span data-ttu-id="82f52-219">TBD – OASIS WSS 1,0 URI</span><span class="sxs-lookup"><span data-stu-id="82f52-219">TBD – OASIS WSS 1.0 URI</span></span>|  
|<span data-ttu-id="82f52-220">wsse11</span><span class="sxs-lookup"><span data-stu-id="82f52-220">wsse11</span></span>|<span data-ttu-id="82f52-221">TBD – OASIS WSS 1,1 URI</span><span class="sxs-lookup"><span data-stu-id="82f52-221">TBD – OASIS WSS 1.1 URI</span></span>|  
|<span data-ttu-id="82f52-222">wsu</span><span class="sxs-lookup"><span data-stu-id="82f52-222">wsu</span></span>|<span data-ttu-id="82f52-223">TBD – URI do utilitário do WSS 1,0 OASIS</span><span class="sxs-lookup"><span data-stu-id="82f52-223">TBD – OASIS WSS 1.0 Utility URI</span></span>|  
|<span data-ttu-id="82f52-224">AD</span><span class="sxs-lookup"><span data-stu-id="82f52-224">ds</span></span>|<span data-ttu-id="82f52-225">TBD – URI de XMLDSig do W3C</span><span class="sxs-lookup"><span data-stu-id="82f52-225">TBD – W3C XMLDSig URI</span></span>|  
|<span data-ttu-id="82f52-226">WST</span><span class="sxs-lookup"><span data-stu-id="82f52-226">wst</span></span>|<span data-ttu-id="82f52-227">TBD – URI do WS-Trust 2005/02</span><span class="sxs-lookup"><span data-stu-id="82f52-227">TBD – WS-Trust 2005/02 URI</span></span>|  
|<span data-ttu-id="82f52-228">wssc</span><span class="sxs-lookup"><span data-stu-id="82f52-228">wssc</span></span>|<span data-ttu-id="82f52-229">TBD – WS-SecureConversation 2005/02 URI</span><span class="sxs-lookup"><span data-stu-id="82f52-229">TBD – WS-SecureConversation 2005/02 URI</span></span>|  
|<span data-ttu-id="82f52-230">wsaw</span><span class="sxs-lookup"><span data-stu-id="82f52-230">wsaw</span></span>|<span data-ttu-id="82f52-231">TBD-namespace de política de WS-Addressing</span><span class="sxs-lookup"><span data-stu-id="82f52-231">TBD - WS-Addressing policy namespace</span></span>|  
|<span data-ttu-id="82f52-232">WSP</span><span class="sxs-lookup"><span data-stu-id="82f52-232">wsp</span></span>|<http://schemas.xmlsoap.org/ws/2004/09/policy>|  
|<span data-ttu-id="82f52-233">mssp</span><span class="sxs-lookup"><span data-stu-id="82f52-233">mssp</span></span>|<http://schemas.xmlsoap.org/ws/2005/07/securitypolicy>|
  
## <a name="1-token-profiles"></a><span data-ttu-id="82f52-234">1. perfis de token</span><span class="sxs-lookup"><span data-stu-id="82f52-234">1. Token Profiles</span></span>  
 <span data-ttu-id="82f52-235">As especificações de especificação Web Services Security representam credenciais como tokens de segurança.</span><span class="sxs-lookup"><span data-stu-id="82f52-235">Web Services Security specifications represent credential as security tokens.</span></span> <span data-ttu-id="82f52-236">O WCF dá suporte aos seguintes tipos de token:</span><span class="sxs-lookup"><span data-stu-id="82f52-236">WCF supports the following token types:</span></span>  
  
### <a name="11-usernametoken"></a><span data-ttu-id="82f52-237">UsernameToken 1,1</span><span class="sxs-lookup"><span data-stu-id="82f52-237">1.1 UsernameToken</span></span>  
 <span data-ttu-id="82f52-238">O WCF segue os perfis UsernameToken10 e UsernameToken11 com as seguintes restrições:</span><span class="sxs-lookup"><span data-stu-id="82f52-238">WCF follows UsernameToken10 and UsernameToken11 profiles with the following constraints:</span></span>  
  
 <span data-ttu-id="82f52-239">O atributo R1101 Passwordtype no elemento UsernameToken\Password deve ser omitido ou ter um valor #PasswordText (padrão).</span><span class="sxs-lookup"><span data-stu-id="82f52-239">R1101 PasswordType attribute on UsernameToken\Password element MUST be either omitted or have value #PasswordText (default).</span></span>  
  
 <span data-ttu-id="82f52-240">Uma delas pode implementar o #PasswordDigest usando a extensibilidade.</span><span class="sxs-lookup"><span data-stu-id="82f52-240">One can implement the #PasswordDigest using extensibility.</span></span> <span data-ttu-id="82f52-241">Foi observado que #PasswordDigest muitas vezes estava confundido como um mecanismo seguro de proteção de senha.</span><span class="sxs-lookup"><span data-stu-id="82f52-241">It has been observed that #PasswordDigest was often mistaken to be a secure enough password protection mechanism.</span></span> <span data-ttu-id="82f52-242">Mas #PasswordDigest não pode servir como um substituto para a criptografia do UsernameToken.</span><span class="sxs-lookup"><span data-stu-id="82f52-242">But #PasswordDigest cannot serve as a substitute for encryption of the UsernameToken.</span></span> <span data-ttu-id="82f52-243">O objetivo principal do #PasswordDigest é a proteção contra ataques de repetição.</span><span class="sxs-lookup"><span data-stu-id="82f52-243">The primary goal of #PasswordDigest is protection against replay attacks.</span></span> <span data-ttu-id="82f52-244">Nos modos de autenticação do WCF, a reprodução de ameaças de ataque é atenuada usando assinaturas de mensagens.</span><span class="sxs-lookup"><span data-stu-id="82f52-244">In WCF authentication modes, replay attack threats are mitigated by using message signatures.</span></span>  
  
 <span data-ttu-id="82f52-245">O WCF B1102 nunca emite um nonce e cria subelementos do UsernameToken.</span><span class="sxs-lookup"><span data-stu-id="82f52-245">B1102 WCF never emits Nonce and Created sub-elements of the UsernameToken.</span></span>  
  
 <span data-ttu-id="82f52-246">Esses subelementos destinam-se a ajudar a detecção de reprodução.</span><span class="sxs-lookup"><span data-stu-id="82f52-246">These sub-elements are intended to help replay detection.</span></span> <span data-ttu-id="82f52-247">Em vez disso, o WCF usa assinaturas de mensagens.</span><span class="sxs-lookup"><span data-stu-id="82f52-247">WCF uses message signatures instead.</span></span>  
  
 <span data-ttu-id="82f52-248">O perfil de UsernameToken de segurança de mensagem SOAP do WSS 1,1 (UsernameToken11) introduziu a derivação de chave do recurso de senha.</span><span class="sxs-lookup"><span data-stu-id="82f52-248">OASIS WSS SOAP Message Security UsernameToken Profile 1.1 (UsernameToken11) introduced key derivation from password feature.</span></span>  
  
 <span data-ttu-id="82f52-249">A senha do UsernameToken B1103 não deve ser usada para a derivação de chave e, portanto, para operações criptográficas.</span><span class="sxs-lookup"><span data-stu-id="82f52-249">B1103 UsernameToken password MUST not be used for key derivation and therefore for cryptographic operations.</span></span>  
  
 <span data-ttu-id="82f52-250">Lógica: as senhas geralmente são consideradas muito fracas para serem usadas para operações criptográficas.</span><span class="sxs-lookup"><span data-stu-id="82f52-250">Rationale: passwords are generally considered too weak to be used for cryptographic operations.</span></span>  
  
### <a name="12-x509-token"></a><span data-ttu-id="82f52-251">1,2 token X509</span><span class="sxs-lookup"><span data-stu-id="82f52-251">1.2 X509 Token</span></span>  
 <span data-ttu-id="82f52-252">O WCF dá suporte a certificados X509v3 como um tipo de credencial e segue o X509TokenProfile 1.0 e o X509TokenProfile 1.1 com as seguintes restrições:</span><span class="sxs-lookup"><span data-stu-id="82f52-252">WCF supports X509v3 certificates as a credential type and follows X509TokenProfile1.0 and X509TokenProfile1.1 with the following constraints:</span></span>  
  
 <span data-ttu-id="82f52-253">R1201 o atributo ValueType no elemento BinarySecurityToken deve ter valor #X509v3 quando ele contiver um certificado X509v3.</span><span class="sxs-lookup"><span data-stu-id="82f52-253">R1201 The ValueType attribute on the BinarySecurityToken element must have value #X509v3 when it contains an X509v3 certificate.</span></span>  
  
 <span data-ttu-id="82f52-254">O perfil de token X509 do WSS 1,0 e 1,1 definem também #X509PKIPathv1 e #PKCS7 como tipos de valor.</span><span class="sxs-lookup"><span data-stu-id="82f52-254">WSS X509 Token Profile 1.0 and 1.1 define also #X509PKIPathv1 and #PKCS7 as value types.</span></span> <span data-ttu-id="82f52-255">O WCF não oferece suporte a esses tipos.</span><span class="sxs-lookup"><span data-stu-id="82f52-255">WCF does not support these types.</span></span>  
  
 <span data-ttu-id="82f52-256">R1202 se uma extensão SubjectKeyIdentifier (esqui) estiver presente em um certificado X509, wsse: KeyIdentifier deve ser usado para referências externas ao token, com o atributo ValueType como #X509SubjectKeyIdentifier e seu conteúdo com o valor codificado em Base64 de extensão de esqui do certificado.</span><span class="sxs-lookup"><span data-stu-id="82f52-256">R1202 If a SubjectKeyIdentifier (SKI) extension is present in an X509 certificate, wsse:KeyIdentifier should be used for external references to the token, with the ValueType attribute as #X509SubjectKeyIdentifier and its content the base64-encoded value of certificate's SKI extension.</span></span>  
  
 <span data-ttu-id="82f52-257">As referências de esqui são amplamente implementadas e comprovadas como um tipo de referência externa altamente interoperável.</span><span class="sxs-lookup"><span data-stu-id="82f52-257">SKI references are widely implemented and proven to be a highly interoperable external reference type.</span></span>  
  
 <span data-ttu-id="82f52-258">R1203 uma referência externa ao token de segurança X509 não deve usar DS: X509IssuerSerial.</span><span class="sxs-lookup"><span data-stu-id="82f52-258">R1203 An external Reference to X509 Security Token SHOULD NOT use ds:X509IssuerSerial.</span></span>  
  
 <span data-ttu-id="82f52-259">R1204 se o X509TokenProfile 1.1 estiver em uso, uma referência externa ao token de segurança X509 deverá usar a impressão digital introduzida pelo WS-Security 1,1.</span><span class="sxs-lookup"><span data-stu-id="82f52-259">R1204 If X509TokenProfile1.1 is in use, an external reference to X509 Security Token SHOULD use the thumbprint introduced by WS-Security 1.1.</span></span>  
  
 <span data-ttu-id="82f52-260">O WCF dá suporte a X509IssuerSerial.</span><span class="sxs-lookup"><span data-stu-id="82f52-260">WCF supports X509IssuerSerial.</span></span> <span data-ttu-id="82f52-261">No entanto, há problemas de interoperabilidade com o X509IssuerSerial: o WCF usa uma cadeia de caracteres para comparar dois valores de X509IssuerSerial.</span><span class="sxs-lookup"><span data-stu-id="82f52-261">However There are interoperability issues with X509IssuerSerial: WCF uses a string to compare two values of X509IssuerSerial.</span></span> <span data-ttu-id="82f52-262">Portanto, se um reordenar componentes do nome da entidade e enviar a um serviço WCF uma referência a um certificado, ele poderá não ser encontrado.</span><span class="sxs-lookup"><span data-stu-id="82f52-262">Therefore if one reorders components of the Subject Name and sends to an WCF service a reference to a certificate, it may not be found.</span></span>  
  
### <a name="13-kerberos-token"></a><span data-ttu-id="82f52-263">Token Kerberos 1,3</span><span class="sxs-lookup"><span data-stu-id="82f52-263">1.3 Kerberos Token</span></span>  
 <span data-ttu-id="82f52-264">O WCF dá suporte ao KerberosTokenProfile 1.1 para fins de autenticação do Windows com as seguintes restrições:</span><span class="sxs-lookup"><span data-stu-id="82f52-264">WCF supports KerberosTokenProfile1.1 for the purpose of Windows authentication with the following constraints:</span></span>  
  
 <span data-ttu-id="82f52-265">R1301 um token Kerberos deve transportar o valor de um GSS AP_REQ do Kerberos v4 encapsulado, conforme definido em GSS_API e a especificação Kerberos, e deve ter o atributo ValueType com o valor #GSS_Kerberosv5_AP_REQ.</span><span class="sxs-lookup"><span data-stu-id="82f52-265">R1301 A Kerberos Token must carry the value of a GSS wrapped Kerberos v4 AP_REQ as defined in GSS_API and the Kerberos specification, and must have the ValueType attribute with the value #GSS_Kerberosv5_AP_REQ.</span></span>  
  
 <span data-ttu-id="82f52-266">O WCF usa a GSS-REQ do Kerberos encapsulado no protocolo de autenticação, e não um ponto de acesso simples.</span><span class="sxs-lookup"><span data-stu-id="82f52-266">WCF uses GSS wrapped Kerberos AP-REQ, not a bare AP-REQ.</span></span> <span data-ttu-id="82f52-267">Essa é uma prática recomendada de segurança.</span><span class="sxs-lookup"><span data-stu-id="82f52-267">This is a security best practice.</span></span>  
  
### <a name="14-saml-v11-token"></a><span data-ttu-id="82f52-268">Token do SAML v 1.1 1,4</span><span class="sxs-lookup"><span data-stu-id="82f52-268">1.4 SAML v1.1 Token</span></span>  
 <span data-ttu-id="82f52-269">O WCF dá suporte a perfis de token SAML 1,0 e 1,1 para tokens SAML v 1.1.</span><span class="sxs-lookup"><span data-stu-id="82f52-269">WCF supports WSS SAML Token profiles 1.0 and 1.1 for SAML v1.1 tokens.</span></span> <span data-ttu-id="82f52-270">É possível implementar outras versões de formatos de token SAML.</span><span class="sxs-lookup"><span data-stu-id="82f52-270">It is possible to implement other versions of SAML token formats.</span></span>  
  
### <a name="15-security-context-token"></a><span data-ttu-id="82f52-271">Token de contexto de segurança 1,5</span><span class="sxs-lookup"><span data-stu-id="82f52-271">1.5 Security Context Token</span></span>  
 <span data-ttu-id="82f52-272">O WCF dá suporte ao SCT (token de contexto de segurança) introduzido no WS-SecureConversation.</span><span class="sxs-lookup"><span data-stu-id="82f52-272">WCF supports the Security Context Token (SCT) introduced in WS-SecureConversation.</span></span> <span data-ttu-id="82f52-273">O SCT é usado para representar um contexto de segurança estabelecido no SecureConversation, bem como os protocolos de negociação binárias TLS e SSPI, descritos abaixo.</span><span class="sxs-lookup"><span data-stu-id="82f52-273">SCT is used to represent a security context established in SecureConversation as well as the binary negotiation protocols TLS and SSPI, described below.</span></span>  
  
## <a name="2-common-message-security-parameters"></a><span data-ttu-id="82f52-274">2. parâmetros de segurança de mensagem comum</span><span class="sxs-lookup"><span data-stu-id="82f52-274">2. Common Message Security Parameters</span></span>  
  
### <a name="21-timestamp"></a><span data-ttu-id="82f52-275">2,1 carimbo de data/hora</span><span class="sxs-lookup"><span data-stu-id="82f52-275">2.1 TimeStamp</span></span>  
 <span data-ttu-id="82f52-276">A presença do carimbo de data/hora é controlada usando a propriedade <xref:System.ServiceModel.Channels.SecurityBindingElement.IncludeTimestamp%2A> da classe <xref:System.ServiceModel.Channels.SecurityBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="82f52-276">Timestamp presence is controlled using the <xref:System.ServiceModel.Channels.SecurityBindingElement.IncludeTimestamp%2A> property of the <xref:System.ServiceModel.Channels.SecurityBindingElement> class.</span></span> <span data-ttu-id="82f52-277">O WCF sempre serializa wsse: TimeStamp com wsse: created e wsse: expira campos.</span><span class="sxs-lookup"><span data-stu-id="82f52-277">WCF always serializes wsse:TimeStamp with wsse:Created and wsse:Expires fields.</span></span> <span data-ttu-id="82f52-278">O carimbo de data/hora wsse: sempre é assinado quando a assinatura é usada.</span><span class="sxs-lookup"><span data-stu-id="82f52-278">The wsse:TimeStamp is always signed when signing is used.</span></span>  
  
### <a name="22-protection-order"></a><span data-ttu-id="82f52-279">2,2 ordem de proteção</span><span class="sxs-lookup"><span data-stu-id="82f52-279">2.2 Protection Order</span></span>  
 <span data-ttu-id="82f52-280">O WCF dá suporte à ordem de proteção de mensagem "assinar antes de criptografar" e "criptografar antes de assinar" (política de segurança 1,1).</span><span class="sxs-lookup"><span data-stu-id="82f52-280">WCF supports the message protection order "Sign Before Encrypt" and "Encrypt Before Sign" (Security Policy 1.1).</span></span> <span data-ttu-id="82f52-281">A opção "assinar antes de criptografar" é recomendada por motivos, incluindo: mensagens protegidas com criptografar antes de assinar os ataques de substituição de assinatura, a menos que o mecanismo de SignatureConfirmation do WS-Security 1,1 seja usado e uma assinatura sobre conteúdo criptografado faça a auditoria é mais difícil.</span><span class="sxs-lookup"><span data-stu-id="82f52-281">"Sign Before Encrypt" is recommended for reasons including: messages protected with Encrypt Before Sign are open to signature substitution attacks unless the WS-Security 1.1 SignatureConfirmation mechanism is used, and a signature over encrypted content makes auditing harder.</span></span>  
  
### <a name="23-signature-protection"></a><span data-ttu-id="82f52-282">Proteção de assinatura 2,3</span><span class="sxs-lookup"><span data-stu-id="82f52-282">2.3 Signature Protection</span></span>  
 <span data-ttu-id="82f52-283">Quando o sinal de criptografia antes é usado, é recomendável proteger a assinatura para evitar ataques de força bruta para adivinhar o conteúdo criptografado ou a chave de assinatura (especialmente quando um token personalizado é usado com o material de chave fraco).</span><span class="sxs-lookup"><span data-stu-id="82f52-283">When Encrypt Before Sign is used, it is recommended to protect the signature to prevent brute force attacks for guessing the encrypted content or the signing key (especially when a custom token is used with weak key material).</span></span>  
  
### <a name="24-algorithm-suite"></a><span data-ttu-id="82f52-284">Pacote de algoritmos 2,4</span><span class="sxs-lookup"><span data-stu-id="82f52-284">2.4 Algorithm Suite</span></span>  
 <span data-ttu-id="82f52-285">O WCF dá suporte a todos os conjuntos de algoritmos listados na política de segurança 1,1.</span><span class="sxs-lookup"><span data-stu-id="82f52-285">WCF supports all algorithm suites listed in Security Policy 1.1.</span></span>  
  
### <a name="25-key-derivation"></a><span data-ttu-id="82f52-286">Derivação de chave 2,5</span><span class="sxs-lookup"><span data-stu-id="82f52-286">2.5 Key Derivation</span></span>  
 <span data-ttu-id="82f52-287">O WCF usa "derivação de chave para chaves simétricas", conforme descrito em WS-SecureConversation.</span><span class="sxs-lookup"><span data-stu-id="82f52-287">WCF uses "Key Derivation for symmetric keys" as described in WS-SecureConversation.</span></span>  
  
### <a name="26-signature-confirmation"></a><span data-ttu-id="82f52-288">2,6 confirmação de assinatura</span><span class="sxs-lookup"><span data-stu-id="82f52-288">2.6 Signature Confirmation</span></span>  
 <span data-ttu-id="82f52-289">A confirmação da assinatura pode ser como proteção contra ataques do Man Middle para proteger o conjunto de assinaturas.</span><span class="sxs-lookup"><span data-stu-id="82f52-289">Signature confirmation can be as protection from middle man attacks to protect the set of signatures.</span></span>  
  
### <a name="27-security-header-layout"></a><span data-ttu-id="82f52-290">Layout do cabeçalho de segurança 2,7</span><span class="sxs-lookup"><span data-stu-id="82f52-290">2.7 Security Header Layout</span></span>  
 <span data-ttu-id="82f52-291">Cada modo de autenticação descreve um determinado layout para o cabeçalho de segurança.</span><span class="sxs-lookup"><span data-stu-id="82f52-291">Each authentication mode describes a certain layout for the security header.</span></span> <span data-ttu-id="82f52-292">Os elementos dentro do cabeçalho de segurança são semiordenados.</span><span class="sxs-lookup"><span data-stu-id="82f52-292">Elements within the security header are semi-ordered.</span></span> <span data-ttu-id="82f52-293">Para definir a ordem dos elementos filho do cabeçalho de segurança, a política do WS-Security define os seguintes modos de layout de cabeçalho de segurança:</span><span class="sxs-lookup"><span data-stu-id="82f52-293">To define the order of security header child elements, WS-Security Policy defines the following security header layout modes:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="82f52-294">Strict</span><span class="sxs-lookup"><span data-stu-id="82f52-294">Strict</span></span>|<span data-ttu-id="82f52-295">Os itens são adicionados ao cabeçalho de segurança seguindo as regras de layout numeradas descritas na seção política de segurança 7.7.1 de acordo com um princípio geral de "declarar antes de usar".</span><span class="sxs-lookup"><span data-stu-id="82f52-295">Items are added to the security header following the numbered layout rules described in Security Policy section 7.7.1 according to a general principle of "declare before use".</span></span>|  
|<span data-ttu-id="82f52-296">Incerto</span><span class="sxs-lookup"><span data-stu-id="82f52-296">Lax</span></span>|<span data-ttu-id="82f52-297">Os itens são adicionados ao cabeçalho de segurança em qualquer ordem que esteja de acordo com o WSS: segurança de mensagem SOAP.</span><span class="sxs-lookup"><span data-stu-id="82f52-297">Items are added to the security header in any order that conforms to WSS: SOAP Message Security.</span></span>|  
|<span data-ttu-id="82f52-298">LaxTimestampFirst</span><span class="sxs-lookup"><span data-stu-id="82f52-298">LaxTimestampFirst</span></span>|<span data-ttu-id="82f52-299">O mesmo que LAX, exceto que o primeiro item no cabeçalho de segurança deve ser um wsse: timestamp</span><span class="sxs-lookup"><span data-stu-id="82f52-299">Same as Lax except that the first item in the security header must be a wsse:Timestamp</span></span>|  
|<span data-ttu-id="82f52-300">LaxTimestampLast</span><span class="sxs-lookup"><span data-stu-id="82f52-300">LaxTimestampLast</span></span>|<span data-ttu-id="82f52-301">O mesmo que LAX, exceto que o último item no cabeçalho de segurança deve ser um wsse: timestamp</span><span class="sxs-lookup"><span data-stu-id="82f52-301">Same as lax except that the last item in the security header must be a wsse:Timestamp</span></span>|  
  
 <span data-ttu-id="82f52-302">O WCF dá suporte a todos os quatro modos de layout de cabeçalho de segurança.</span><span class="sxs-lookup"><span data-stu-id="82f52-302">WCF supports all four modes for security header layout.</span></span> <span data-ttu-id="82f52-303">A estrutura de cabeçalho de segurança e os exemplos de mensagem para os modos de autenticação abaixo seguem o modo "estrito".</span><span class="sxs-lookup"><span data-stu-id="82f52-303">Security header structure and message examples for authentication modes below follow the "Strict" mode.</span></span>  
  
## <a name="2-common-message-security-parameters"></a><span data-ttu-id="82f52-304">2. parâmetros de segurança de mensagem comum</span><span class="sxs-lookup"><span data-stu-id="82f52-304">2. Common Message Security Parameters</span></span>  
 <span data-ttu-id="82f52-305">Esta seção fornece as políticas de exemplo para cada modo de autenticação, juntamente com exemplos que mostram a estrutura de cabeçalho de segurança em mensagens trocadas por cliente e serviço.</span><span class="sxs-lookup"><span data-stu-id="82f52-305">This section provides example policies for each authentication mode along with examples showing security header structure in messages exchanged by client and service.</span></span>  
  
### <a name="61-transport-protection"></a><span data-ttu-id="82f52-306">Proteção de transporte 6,1</span><span class="sxs-lookup"><span data-stu-id="82f52-306">6.1 Transport Protection</span></span>  
 <span data-ttu-id="82f52-307">O WCF fornece cinco modos de autenticação que usam o transporte seguro para proteger mensagens; UserNameOverTransport, CertificateOverTransport, KerberosOverTransport, IssuedTokenOverTransport e SspiNegotiatedOverTransport.</span><span class="sxs-lookup"><span data-stu-id="82f52-307">WCF provides five authentication modes that use secure transport to protect messages; UserNameOverTransport, CertificateOverTransport, KerberosOverTransport, IssuedTokenOverTransport and SspiNegotiatedOverTransport.</span></span>  
  
 <span data-ttu-id="82f52-308">Esses modos de autenticação são construídos usando a associação de transporte descrita em SecurityPolicy.</span><span class="sxs-lookup"><span data-stu-id="82f52-308">These authentication modes are constructed using the transport binding described in SecurityPolicy.</span></span> <span data-ttu-id="82f52-309">Para o modo de autenticação UserNameOverTransport, o UsernameToken é um token de suporte assinado.</span><span class="sxs-lookup"><span data-stu-id="82f52-309">For the UserNameOverTransport authentication mode the UsernameToken is a signed supporting token.</span></span> <span data-ttu-id="82f52-310">Para os outros modos de autenticação, o token aparece como um token de endosso assinado.</span><span class="sxs-lookup"><span data-stu-id="82f52-310">For the other authentication modes the token appears as a signed endorsing token.</span></span> <span data-ttu-id="82f52-311">O Apêndice C. 1.2 e o C. 1.3 de SecurityPolicy descrevem o layout do cabeçalho de segurança em detalhes.</span><span class="sxs-lookup"><span data-stu-id="82f52-311">Appendix C.1.2 and C.1.3 of SecurityPolicy describe the security header layout in detail.</span></span> <span data-ttu-id="82f52-312">Os cabeçalhos de segurança de exemplo a seguir mostram o layout estrito para um determinado modo de autenticação.</span><span class="sxs-lookup"><span data-stu-id="82f52-312">The following example security headers show the Strict layout for a given authentication mode.</span></span>  
  
 <span data-ttu-id="82f52-313">O valor da propriedade "chaves derivadas" para os tokens em todos os casos é "false".</span><span class="sxs-lookup"><span data-stu-id="82f52-313">The value of the "Derived Keys" property for the tokens in all cases is "false".</span></span>  
  
 <span data-ttu-id="82f52-314">Os valores das várias propriedades da Associação de transporte são os seguintes:</span><span class="sxs-lookup"><span data-stu-id="82f52-314">The values of the various properties of the transport binding are as follows:</span></span>  
  
 <span data-ttu-id="82f52-315">Carimbo de data/hora: verdadeiro</span><span class="sxs-lookup"><span data-stu-id="82f52-315">Timestamp: true</span></span>  
  
 <span data-ttu-id="82f52-316">Layout do cabeçalho de segurança: estrito</span><span class="sxs-lookup"><span data-stu-id="82f52-316">Security Header Layout: Strict</span></span>  
  
 <span data-ttu-id="82f52-317">Conjunto de algoritmos: Basic256</span><span class="sxs-lookup"><span data-stu-id="82f52-317">Algorithm Suite: Basic256</span></span>  
  
#### <a name="611-usernameovertransport"></a><span data-ttu-id="82f52-318">UsernameOverTransport 6.1.1</span><span class="sxs-lookup"><span data-stu-id="82f52-318">6.1.1 UsernameOverTransport</span></span>  
 <span data-ttu-id="82f52-319">Com esse modo de autenticação, o cliente é autenticado com um token de nome de usuário que aparece na camada SOAP como um token de suporte assinado que é sempre enviado do iniciador para o destinatário.</span><span class="sxs-lookup"><span data-stu-id="82f52-319">With this authentication mode, the client authenticates with a Username Token which appears at the SOAP layer as a signed supporting token that is always sent from the initiator to the recipient.</span></span> <span data-ttu-id="82f52-320">O serviço é autenticado usando um certificado X. 509 na camada de transporte.</span><span class="sxs-lookup"><span data-stu-id="82f52-320">The service is authenticated using an X.509 certificate at the transport layer.</span></span> <span data-ttu-id="82f52-321">A associação usada é uma associação de transporte.</span><span class="sxs-lookup"><span data-stu-id="82f52-321">The binding used is a transport binding.</span></span>  
  
 <span data-ttu-id="82f52-322">Política</span><span class="sxs-lookup"><span data-stu-id="82f52-322">Policy</span></span>  
  
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
  
 <span data-ttu-id="82f52-323">Layout do cabeçalho de segurança</span><span class="sxs-lookup"><span data-stu-id="82f52-323">Security Header Layout</span></span>  
  
 <span data-ttu-id="82f52-324">Solicitação</span><span class="sxs-lookup"><span data-stu-id="82f52-324">Request</span></span>  
  
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
  
 <span data-ttu-id="82f52-325">Resposta</span><span class="sxs-lookup"><span data-stu-id="82f52-325">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
#### <a name="612-certificateovertransport"></a><span data-ttu-id="82f52-326">6.1.2 CertificateOverTransport</span><span class="sxs-lookup"><span data-stu-id="82f52-326">6.1.2 CertificateOverTransport</span></span>  
 <span data-ttu-id="82f52-327">Com esse modo de autenticação, o cliente é autenticado usando um certificado X. 509 que aparece na camada SOAP como um token de suporte de endosso que é sempre enviado do iniciador para o destinatário.</span><span class="sxs-lookup"><span data-stu-id="82f52-327">With this authentication mode the client authenticates using an X.509 certificate which appears at the SOAP layer as an endorsing supporting token that is always sent from the initiator to the recipient.</span></span> <span data-ttu-id="82f52-328">O serviço é autenticado usando um certificado X. 509 na camada de transporte.</span><span class="sxs-lookup"><span data-stu-id="82f52-328">The service is authenticated using an X.509 certificate at the transport layer.</span></span> <span data-ttu-id="82f52-329">A associação usada é uma associação de transporte.</span><span class="sxs-lookup"><span data-stu-id="82f52-329">The binding used is a transport binding.</span></span>  
  
 <span data-ttu-id="82f52-330">Política</span><span class="sxs-lookup"><span data-stu-id="82f52-330">Policy</span></span>  
  
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
  
 <span data-ttu-id="82f52-331">Layout do cabeçalho de segurança</span><span class="sxs-lookup"><span data-stu-id="82f52-331">Security Header Layout</span></span>  
  
 <span data-ttu-id="82f52-332">Solicitação</span><span class="sxs-lookup"><span data-stu-id="82f52-332">Request</span></span>  
  
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
  
 <span data-ttu-id="82f52-333">Resposta</span><span class="sxs-lookup"><span data-stu-id="82f52-333">Response</span></span>  
  
```xml  
<o:Security>  
  <u:Timestamp u:Id="_0">  
  ...  
  </u:Timestamp>  
</o:Security>  
```  
  
#### <a name="613-issuedtokenovertransport"></a><span data-ttu-id="82f52-334">6.1.3 IssuedTokenOverTransport</span><span class="sxs-lookup"><span data-stu-id="82f52-334">6.1.3 IssuedTokenOverTransport</span></span>  
 <span data-ttu-id="82f52-335">Com esse modo de autenticação, o cliente não se autentica no serviço, como tal, mas apresenta um token emitido por um STS (serviço de token de segurança) e comprova o conhecimento de uma chave compartilhada.</span><span class="sxs-lookup"><span data-stu-id="82f52-335">With this authentication mode the client does not authenticate to the service, as such, but rather presents a token issued by a Security Token Service (STS) and proves knowledge of a shared key.</span></span> <span data-ttu-id="82f52-336">O token emitido é exibido na camada SOAP como um token de suporte de endosso que é sempre enviado do iniciador para o destinatário.</span><span class="sxs-lookup"><span data-stu-id="82f52-336">The issued token appears at the SOAP layer as an endorsing supporting token that is always sent from the initiator to the recipient.</span></span> <span data-ttu-id="82f52-337">O serviço é autenticado usando um certificado X. 509 na camada de transporte.</span><span class="sxs-lookup"><span data-stu-id="82f52-337">The service is authenticated using an X.509 certificate at the transport layer.</span></span> <span data-ttu-id="82f52-338">A associação é uma associação de transporte.</span><span class="sxs-lookup"><span data-stu-id="82f52-338">The binding is a transport binding.</span></span>  
  
 <span data-ttu-id="82f52-339">Política</span><span class="sxs-lookup"><span data-stu-id="82f52-339">Policy</span></span>  
  
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
  
 <span data-ttu-id="82f52-340">Layout do cabeçalho de segurança</span><span class="sxs-lookup"><span data-stu-id="82f52-340">Security Header Layout</span></span>  
  
 <span data-ttu-id="82f52-341">Solicitação</span><span class="sxs-lookup"><span data-stu-id="82f52-341">Request</span></span>  
  
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
  
 <span data-ttu-id="82f52-342">Resposta</span><span class="sxs-lookup"><span data-stu-id="82f52-342">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
#### <a name="614-kerberosovertransport"></a><span data-ttu-id="82f52-343">6.1.4 KerberosOverTransport</span><span class="sxs-lookup"><span data-stu-id="82f52-343">6.1.4 KerberosOverTransport</span></span>  
 <span data-ttu-id="82f52-344">Com esse modo de autenticação, o cliente é autenticado para o serviço usando um tíquete Kerberos.</span><span class="sxs-lookup"><span data-stu-id="82f52-344">With this authentication mode the client authenticates to the service using a Kerberos ticket.</span></span> <span data-ttu-id="82f52-345">O token Kerberos é exibido na camada SOAP como um token de suporte de endosso.</span><span class="sxs-lookup"><span data-stu-id="82f52-345">The Kerberos token appears at the SOAP layer as an endorsing supporting token.</span></span> <span data-ttu-id="82f52-346">O serviço é autenticado usando um certificado X. 509 na camada de transporte.</span><span class="sxs-lookup"><span data-stu-id="82f52-346">The service is authenticated using an X.509 certificate at the transport layer.</span></span> <span data-ttu-id="82f52-347">A associação é uma associação de transporte.</span><span class="sxs-lookup"><span data-stu-id="82f52-347">The binding is a transport binding.</span></span>  
  
 <span data-ttu-id="82f52-348">Política</span><span class="sxs-lookup"><span data-stu-id="82f52-348">Policy</span></span>  
  
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
  
 <span data-ttu-id="82f52-349">Layout do cabeçalho de segurança</span><span class="sxs-lookup"><span data-stu-id="82f52-349">Security Header Layout</span></span>  
  
 <span data-ttu-id="82f52-350">Solicitação</span><span class="sxs-lookup"><span data-stu-id="82f52-350">Request</span></span>  
  
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
  
 <span data-ttu-id="82f52-351">Resposta</span><span class="sxs-lookup"><span data-stu-id="82f52-351">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
#### <a name="615-sspinegotiatedovertransport"></a><span data-ttu-id="82f52-352">6.1.5 SspiNegotiatedOverTransport</span><span class="sxs-lookup"><span data-stu-id="82f52-352">6.1.5 SspiNegotiatedOverTransport</span></span>  
 <span data-ttu-id="82f52-353">Com esse modo, um protocolo de negociação é usado para executar a autenticação de cliente e servidor.</span><span class="sxs-lookup"><span data-stu-id="82f52-353">With this mode a negotiation protocol is used to perform client and server authentication.</span></span> <span data-ttu-id="82f52-354">O Kerberos é usado se possível, caso contrário, NTLM.</span><span class="sxs-lookup"><span data-stu-id="82f52-354">Kerberos is used if possible, otherwise NTLM.</span></span> <span data-ttu-id="82f52-355">O SCT resultante aparece na camada SOAP como um token de suporte de endosso que sempre é enviado do iniciador para o destinatário.</span><span class="sxs-lookup"><span data-stu-id="82f52-355">The resulting SCT appears at the SOAP layer as an endorsing supporting token that is always sent from initiator to recipient.</span></span> <span data-ttu-id="82f52-356">O serviço também é autenticado na camada de transporte por um certificado X. 509.</span><span class="sxs-lookup"><span data-stu-id="82f52-356">The service is additionally authenticated at the transport layer by an X.509 certificate.</span></span> <span data-ttu-id="82f52-357">A associação usada é uma associação de transporte.</span><span class="sxs-lookup"><span data-stu-id="82f52-357">The binding used is a transport binding.</span></span> <span data-ttu-id="82f52-358">"SPNEGO" (negociação) descreve como o WCF usa o protocolo de negociação binária SSPI com WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="82f52-358">"SPNEGO" (negotiation) describes how WCF uses SSPI binary negotiation protocol with WS-Trust.</span></span> <span data-ttu-id="82f52-359">Os exemplos de cabeçalho de segurança nesta seção são após o SCT ter sido estabelecido por meio do handshake SPNEGO.</span><span class="sxs-lookup"><span data-stu-id="82f52-359">Security header examples in this section are after the SCT has been established through the SPNEGO handshake.</span></span>  
  
 <span data-ttu-id="82f52-360">Política</span><span class="sxs-lookup"><span data-stu-id="82f52-360">Policy</span></span>  
  
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
  
### <a name="security-header-examples"></a><span data-ttu-id="82f52-361">Exemplos de cabeçalho de segurança</span><span class="sxs-lookup"><span data-stu-id="82f52-361">Security Header Examples</span></span>  
 <span data-ttu-id="82f52-362">Depois que o token de contexto de segurança é estabelecido por meio de handshake SPNEGO usando a negociação binária de WS-Trust, as mensagens de aplicativo têm cabeçalhos de segurança com a seguinte estrutura.</span><span class="sxs-lookup"><span data-stu-id="82f52-362">Once the Security Context Token is established through SPNEGO handshake using WS-Trust Binary Negotiation, the application messages have security headers with the following structure.</span></span>  
  
 <span data-ttu-id="82f52-363">Solicitação</span><span class="sxs-lookup"><span data-stu-id="82f52-363">Request</span></span>  
  
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
  
 <span data-ttu-id="82f52-364">Resposta</span><span class="sxs-lookup"><span data-stu-id="82f52-364">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
### <a name="62-using-x509-certificates-for-service-authentication"></a><span data-ttu-id="82f52-365">6,2 usando certificados X. 509 para autenticação de serviço</span><span class="sxs-lookup"><span data-stu-id="82f52-365">6.2 Using X.509 Certificates for Service Authentication</span></span>  
 <span data-ttu-id="82f52-366">Esta seção descreve os seguintes modos de autenticação: MutualCertificate WSS 1.0, Mutual CertificateDuplex, MutualCertificate WSS 1.1, AnonymousForCertificate, UserNameForCertificate e IssuedTokenForCertificate.</span><span class="sxs-lookup"><span data-stu-id="82f52-366">This section describes the following authentication modes: MutualCertificate WSS1.0, Mutual CertificateDuplex, MutualCertificate WSS1.1, AnonymousForCertificate, UserNameForCertificate and IssuedTokenForCertificate.</span></span>  
  
#### <a name="621-mutualcertificate-wss10"></a><span data-ttu-id="82f52-367">6.2.1 MutualCertificate WSS 1.0</span><span class="sxs-lookup"><span data-stu-id="82f52-367">6.2.1 MutualCertificate WSS1.0</span></span>  
 <span data-ttu-id="82f52-368">Com esse modo de autenticação, o cliente é autenticado usando um certificado X. 509 que aparece na camada SOAP como o token do iniciador.</span><span class="sxs-lookup"><span data-stu-id="82f52-368">With this authentication mode the client authenticates using an X.509 certificate which appears at the SOAP layer as the initiator token.</span></span> <span data-ttu-id="82f52-369">O serviço também é autenticado usando um certificado X. 509.</span><span class="sxs-lookup"><span data-stu-id="82f52-369">The service is also authenticated using an X.509 certificate.</span></span>  
  
 <span data-ttu-id="82f52-370">A associação usada é uma associação assimétrica com os seguintes valores de propriedade:</span><span class="sxs-lookup"><span data-stu-id="82f52-370">The binding used is an asymmetric binding with the following property values:</span></span>  
  
 <span data-ttu-id="82f52-371">Token do iniciador: o certificado X. 509 do cliente, com o modo de inclusão definido como. ../IncludeToken/AlwaysToRecipient</span><span class="sxs-lookup"><span data-stu-id="82f52-371">Initiator Token: the client’s X.509 certificate, with inclusion mode set to …/IncludeToken/AlwaysToRecipient</span></span>  
  
 <span data-ttu-id="82f52-372">Token do destinatário: o certificado X. 509 do servidor, com o modo de inclusão, está definido. ../IncludeToken/Never</span><span class="sxs-lookup"><span data-stu-id="82f52-372">Recipient Token: Server’s X.509 Certificate, with inclusion mode is set …/IncludeToken/Never</span></span>  
  
 <span data-ttu-id="82f52-373">Proteção de token: false</span><span class="sxs-lookup"><span data-stu-id="82f52-373">Token Protection: False</span></span>  
  
 <span data-ttu-id="82f52-374">Assinaturas inteiras de cabeçalho e corpo: verdadeiro</span><span class="sxs-lookup"><span data-stu-id="82f52-374">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="82f52-375">Ordem de proteção: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="82f52-375">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="82f52-376">Criptografar assinatura: verdadeiro</span><span class="sxs-lookup"><span data-stu-id="82f52-376">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="82f52-377">Política</span><span class="sxs-lookup"><span data-stu-id="82f52-377">Policy</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="82f52-378">Exemplos de cabeçalho de segurança: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="82f52-378">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="82f52-379">Solicitação</span><span class="sxs-lookup"><span data-stu-id="82f52-379">Request</span></span>  
  
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
  
 <span data-ttu-id="82f52-380">Resposta</span><span class="sxs-lookup"><span data-stu-id="82f52-380">Response</span></span>  
  
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
  
 <span data-ttu-id="82f52-381">Exemplos de cabeçalho de segurança: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="82f52-381">Security Header Examples: EncryptBeforeSign</span></span>  
  
 <span data-ttu-id="82f52-382">Solicitação</span><span class="sxs-lookup"><span data-stu-id="82f52-382">Request</span></span>  
  
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
  
 <span data-ttu-id="82f52-383">Resposta</span><span class="sxs-lookup"><span data-stu-id="82f52-383">Response</span></span>  
  
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
  
#### <a name="622-mutualcertificateduplex"></a><span data-ttu-id="82f52-384">6.2.2 MutualCertificateDuplex</span><span class="sxs-lookup"><span data-stu-id="82f52-384">6.2.2 MutualCertificateDuplex</span></span>  
 <span data-ttu-id="82f52-385">Com esse modo de autenticação, o cliente é autenticado usando um certificado X. 509 que aparece na camada SOAP como o token do iniciador.</span><span class="sxs-lookup"><span data-stu-id="82f52-385">With this authentication mode the client authenticates using an X.509 certificate which appears at the SOAP layer as the initiator token.</span></span> <span data-ttu-id="82f52-386">O serviço também é autenticado usando um certificado X. 509.</span><span class="sxs-lookup"><span data-stu-id="82f52-386">The service is also authenticated using an X.509 certificate.</span></span>  
  
 <span data-ttu-id="82f52-387">A associação usada é uma associação assimétrica com os seguintes valores de propriedade:</span><span class="sxs-lookup"><span data-stu-id="82f52-387">The binding used is an asymmetric binding with the following property values:</span></span>  
  
 <span data-ttu-id="82f52-388">Token do iniciador: certificado X509 do cliente, modo de inclusão definido como. ../IncludeToken/AlwaysToRecipient</span><span class="sxs-lookup"><span data-stu-id="82f52-388">Initiator Token: Client’s X509 Certificate, inclusion mode is set to …/IncludeToken/AlwaysToRecipient</span></span>  
  
 <span data-ttu-id="82f52-389">Token do destinatário: certificado X509 do servidor, modo de inclusão definido como. ../IncludeToken/AlwaysToInitiator</span><span class="sxs-lookup"><span data-stu-id="82f52-389">Recipient Token: Server’s X509 Certificate, inclusion mode is set to …/IncludeToken/AlwaysToInitiator</span></span>  
  
 <span data-ttu-id="82f52-390">Proteção de token: false</span><span class="sxs-lookup"><span data-stu-id="82f52-390">Token Protection: False</span></span>  
  
 <span data-ttu-id="82f52-391">Assinaturas inteiras de cabeçalho e corpo: verdadeiro</span><span class="sxs-lookup"><span data-stu-id="82f52-391">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="82f52-392">Ordem de proteção: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="82f52-392">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="82f52-393">Criptografar assinatura: verdadeiro</span><span class="sxs-lookup"><span data-stu-id="82f52-393">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="82f52-394">Política</span><span class="sxs-lookup"><span data-stu-id="82f52-394">Policy</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="82f52-395">Exemplos de cabeçalho de segurança: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="82f52-395">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="82f52-396">Solicitação e resposta</span><span class="sxs-lookup"><span data-stu-id="82f52-396">Request and Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="82f52-397">Exemplos de cabeçalho de segurança: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="82f52-397">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="82f52-398">Solicitação e resposta</span><span class="sxs-lookup"><span data-stu-id="82f52-398">Request and Response</span></span>  
  
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
  
#### <a name="623-using-symmetricbinding-with-x509-service-authentication"></a><span data-ttu-id="82f52-399">6.2.3 usando Simétricobinding com autenticação de serviço X. 509</span><span class="sxs-lookup"><span data-stu-id="82f52-399">6.2.3 Using SymmetricBinding with X.509 Service Authentication</span></span>  
 <span data-ttu-id="82f52-400">"WSS10" forneceu suporte limitado para cenários com tokens X509.</span><span class="sxs-lookup"><span data-stu-id="82f52-400">"WSS10" provided limited support for scenarios with X509 tokens.</span></span> <span data-ttu-id="82f52-401">Por exemplo, não havia como fornecer proteção de assinatura e criptografia para mensagens usando apenas o token X509 do serviço.</span><span class="sxs-lookup"><span data-stu-id="82f52-401">For example, there was no way to provide signature and encryption protection for messages using only service X509 token.</span></span> <span data-ttu-id="82f52-402">"WSS11" introduziu o uso de EncryptedKey como um token simétrico.</span><span class="sxs-lookup"><span data-stu-id="82f52-402">"WSS11" introduced the usage of EncryptedKey as a symmetric token.</span></span> <span data-ttu-id="82f52-403">Agora, uma chave temporária criptografada para o certificado X. 509 do serviço pode ser usada para a proteção de mensagens de solicitação e resposta.</span><span class="sxs-lookup"><span data-stu-id="82f52-403">Now a temporary key encrypted for the service's X.509 certificate could be used for both request and response messages protection.</span></span> <span data-ttu-id="82f52-404">Os modos de autenticação descritos na seção 6,4 abaixo usam esse padrão.</span><span class="sxs-lookup"><span data-stu-id="82f52-404">The authentication modes described in the section 6.4 below use this pattern.</span></span>  
  
 <span data-ttu-id="82f52-405">O WS-SecurityPolicy descreve esse padrão usando o Simétricobinding com o token X509 do serviço como o token de proteção.</span><span class="sxs-lookup"><span data-stu-id="82f52-405">WS-SecurityPolicy describes this pattern using SymmetricBinding with Service X509 token as the protection token.</span></span>  
  
 <span data-ttu-id="82f52-406">Modos de autenticação AnonymousForCertificate, UsernameForCertificate, MutualCertificate WSS11 e IssuedTokenForCertificate usam uma instância semelhante de SP: Symmetricbinding com os seguintes valores de propriedade:</span><span class="sxs-lookup"><span data-stu-id="82f52-406">Authentication modes AnonymousForCertificate, UsernameForCertificate, MutualCertificate WSS11 and IssuedTokenForCertificate all use a similar instance of sp:SymmetricBinding with the following property values:</span></span>  
  
 <span data-ttu-id="82f52-407">Token de proteção: certificado X509 do servidor, modo de inclusão definido como. ../IncludeToken/Never</span><span class="sxs-lookup"><span data-stu-id="82f52-407">Protection Token: Server’s X509 Certificate, inclusion mode is set to .../IncludeToken/Never</span></span>  
<span data-ttu-id="82f52-408">Proteção de token: false</span><span class="sxs-lookup"><span data-stu-id="82f52-408">Token Protection: False</span></span>  
  
 <span data-ttu-id="82f52-409">Assinaturas inteiras de cabeçalho e corpo: verdadeiro</span><span class="sxs-lookup"><span data-stu-id="82f52-409">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="82f52-410">Ordem de proteção: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="82f52-410">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="82f52-411">Criptografar assinatura: verdadeiro</span><span class="sxs-lookup"><span data-stu-id="82f52-411">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="82f52-412">Os modos de autenticação acima diferem apenas pelos tokens de suporte que eles usam.</span><span class="sxs-lookup"><span data-stu-id="82f52-412">The above authentication modes only differ by the supporting tokens they use.</span></span> <span data-ttu-id="82f52-413">AnonymousForCertificate não tem nenhum token de suporte, o MutualCertificate WSS 1,1 tem o certificado X509 do cliente como um token de suporte de endosso, UserNameForCertificate tem um token de nome de usuário como um token de suporte assinado e IssuedTokenForCertificate tem o token emitido como um token de suporte de endosso.</span><span class="sxs-lookup"><span data-stu-id="82f52-413">AnonymousForCertificate does not have any supporting tokens, MutualCertificate WSS 1.1 has the client’s X509 certificate as an endorsing supporting tokens, UserNameForCertificate has a UserName Token as a signed supporting token and IssuedTokenForCertificate has the issued token as an endorsing supporting token.</span></span>  
  
 <span data-ttu-id="82f52-414">Política</span><span class="sxs-lookup"><span data-stu-id="82f52-414">Policy</span></span>  
  
 <span data-ttu-id="82f52-415">Associação simétrica</span><span class="sxs-lookup"><span data-stu-id="82f52-415">Symmetric Binding</span></span>  
  
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
  
#### <a name="624-anonymousforcertificate"></a><span data-ttu-id="82f52-416">6.2.4 AnonymousForCertificate</span><span class="sxs-lookup"><span data-stu-id="82f52-416">6.2.4 AnonymousForCertificate</span></span>  
 <span data-ttu-id="82f52-417">Com esse modo de autenticação, o cliente é anônimo e o serviço é autenticado usando um certificado X. 509.</span><span class="sxs-lookup"><span data-stu-id="82f52-417">With this authentication mode the client is anonymous and the service is authenticated using an X.509 certificate.</span></span> <span data-ttu-id="82f52-418">A associação usada é uma instância da Associação simétrica, conforme descrito em 6.4.2.</span><span class="sxs-lookup"><span data-stu-id="82f52-418">The binding used is an instance of symmetric binding as described in 6.4.2.</span></span>  
  
 <span data-ttu-id="82f52-419">Política</span><span class="sxs-lookup"><span data-stu-id="82f52-419">Policy</span></span>  
  
 <span data-ttu-id="82f52-420">Consulte "política" em 6.2.3 acima para obter detalhes de associação</span><span class="sxs-lookup"><span data-stu-id="82f52-420">See "Policy" in 6.2.3 above for binding details</span></span>  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="82f52-421">Exemplos de cabeçalho de segurança: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="82f52-421">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="82f52-422">Solicitação</span><span class="sxs-lookup"><span data-stu-id="82f52-422">Request</span></span>  
  
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
  
 <span data-ttu-id="82f52-423">Resposta</span><span class="sxs-lookup"><span data-stu-id="82f52-423">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="82f52-424">Exemplos de cabeçalho de segurança: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="82f52-424">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="82f52-425">Solicitação</span><span class="sxs-lookup"><span data-stu-id="82f52-425">Request</span></span>  
  
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
  
 <span data-ttu-id="82f52-426">Resposta</span><span class="sxs-lookup"><span data-stu-id="82f52-426">Response</span></span>  
  
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
  
#### <a name="625-usernameforcertificate"></a><span data-ttu-id="82f52-427">6.2.5 UserNameForCertificate</span><span class="sxs-lookup"><span data-stu-id="82f52-427">6.2.5 UserNameForCertificate</span></span>  
 <span data-ttu-id="82f52-428">Com esse modo de autenticação, o cliente é autenticado no serviço usando um token de nome de usuário que aparece na camada SOAP como um token de suporte assinado.</span><span class="sxs-lookup"><span data-stu-id="82f52-428">With this authentication mode the client authenticates to the service using a Username Token which appears at the SOAP layer as a signed supporting token.</span></span> <span data-ttu-id="82f52-429">O serviço é autenticado no cliente usando um certificado X. 509.</span><span class="sxs-lookup"><span data-stu-id="82f52-429">The service authenticates to the client using an X.509 certificate.</span></span> <span data-ttu-id="82f52-430">A associação usada é uma associação simétrica com o token de proteção sendo uma chave gerada pelo cliente, criptografada com a chave pública do serviço.</span><span class="sxs-lookup"><span data-stu-id="82f52-430">The binding used is a symmetric binding with the protection token being a key generated by the client, encrypted with the public key of the service.</span></span>  
  
 <span data-ttu-id="82f52-431">Política</span><span class="sxs-lookup"><span data-stu-id="82f52-431">Policy</span></span>  
  
 <span data-ttu-id="82f52-432">Consulte "política" em 6.2.3 acima para obter detalhes de associação</span><span class="sxs-lookup"><span data-stu-id="82f52-432">See "Policy" in 6.2.3 above for binding details</span></span>  
  
 <span data-ttu-id="82f52-433">Token de suporte assinado</span><span class="sxs-lookup"><span data-stu-id="82f52-433">Signed Supporting Token</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="82f52-434">Exemplos de cabeçalho de segurança: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="82f52-434">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="82f52-435">Solicitação</span><span class="sxs-lookup"><span data-stu-id="82f52-435">Request</span></span>  
  
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
  
 <span data-ttu-id="82f52-436">Resposta</span><span class="sxs-lookup"><span data-stu-id="82f52-436">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="82f52-437">Exemplos de cabeçalho de segurança: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="82f52-437">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="82f52-438">Solicitação</span><span class="sxs-lookup"><span data-stu-id="82f52-438">Request</span></span>  
  
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
  
 <span data-ttu-id="82f52-439">Resposta</span><span class="sxs-lookup"><span data-stu-id="82f52-439">Response</span></span>  
  
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
  
#### <a name="626-mutualcertificate-wss-11"></a><span data-ttu-id="82f52-440">6.2.6 MutualCertificate (WSS 1,1)</span><span class="sxs-lookup"><span data-stu-id="82f52-440">6.2.6 MutualCertificate (WSS 1.1)</span></span>  
 <span data-ttu-id="82f52-441">Com esse modo de autenticação, o cliente é autenticado usando um certificado X. 509 que aparece na camada SOAP como um token de suporte de endosso.</span><span class="sxs-lookup"><span data-stu-id="82f52-441">With this authentication mode the client authenticates using an X.509 certificate which appears at the SOAP layer as an endorsing supporting token.</span></span> <span data-ttu-id="82f52-442">O serviço também é autenticado usando um certificado X. 509.</span><span class="sxs-lookup"><span data-stu-id="82f52-442">The service is also authenticated using an X.509 certificate.</span></span> <span data-ttu-id="82f52-443">A associação usada é uma associação simétrica com o token de proteção sendo uma chave gerada pelo cliente, criptografada com a chave pública do serviço.</span><span class="sxs-lookup"><span data-stu-id="82f52-443">The binding used is a symmetric binding with the protection token being a key generated by the client, encrypted with the public key of the service.</span></span>  
  
 <span data-ttu-id="82f52-444">Política</span><span class="sxs-lookup"><span data-stu-id="82f52-444">Policy</span></span>  
  
 <span data-ttu-id="82f52-445">Consulte a política em 6.2.3 para obter detalhes de associação</span><span class="sxs-lookup"><span data-stu-id="82f52-445">See Policy in 6.2.3 for binding details</span></span>  
  
 <span data-ttu-id="82f52-446">Token de suporte de endosso</span><span class="sxs-lookup"><span data-stu-id="82f52-446">Endorsing Supporting Token</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="82f52-447">Exemplos de cabeçalho de segurança: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="82f52-447">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="82f52-448">Solicitação</span><span class="sxs-lookup"><span data-stu-id="82f52-448">Request</span></span>  
  
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
  
 <span data-ttu-id="82f52-449">Resposta</span><span class="sxs-lookup"><span data-stu-id="82f52-449">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="82f52-450">Exemplos de cabeçalho de segurança: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="82f52-450">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="82f52-451">Solicitação</span><span class="sxs-lookup"><span data-stu-id="82f52-451">Request</span></span>  
  
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
  
 <span data-ttu-id="82f52-452">Resposta</span><span class="sxs-lookup"><span data-stu-id="82f52-452">Response</span></span>  
  
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
  
#### <a name="627-issuedtokenforcertificate"></a><span data-ttu-id="82f52-453">6.2.7 IssuedTokenForCertificate</span><span class="sxs-lookup"><span data-stu-id="82f52-453">6.2.7 IssuedTokenForCertificate</span></span>  
 <span data-ttu-id="82f52-454">Com esse modo de autenticação, o cliente não se autentica no serviço, como tal, mas apresenta um token emitido por um STS e comprova o conhecimento de uma chave compartilhada.</span><span class="sxs-lookup"><span data-stu-id="82f52-454">With this authentication mode the client does not authenticate to the service, as such, but instead presents a token issued by a STS and proves knowledge of a shared key.</span></span> <span data-ttu-id="82f52-455">O token emitido é exibido na camada SOAP como um token de suporte de endosso.</span><span class="sxs-lookup"><span data-stu-id="82f52-455">The issued token appears at the SOAP layer as an endorsing supporting token.</span></span> <span data-ttu-id="82f52-456">O serviço é autenticado no cliente usando um certificado X. 509.</span><span class="sxs-lookup"><span data-stu-id="82f52-456">The service authenticates to the client using an X.509 certificate.</span></span> <span data-ttu-id="82f52-457">A associação usada é uma associação simétrica com o token de proteção sendo uma chave gerada pelo cliente, criptografada com a chave pública do serviço.</span><span class="sxs-lookup"><span data-stu-id="82f52-457">The binding used is a symmetric binding with the protection token being a key generated by the client, encrypted with the public key of the service.</span></span>  
  
 <span data-ttu-id="82f52-458">Política</span><span class="sxs-lookup"><span data-stu-id="82f52-458">Policy</span></span>  
  
 <span data-ttu-id="82f52-459">Consulte a política no 6.2.3 acima para obter detalhes de associação</span><span class="sxs-lookup"><span data-stu-id="82f52-459">See Policy in 6.2.3 above for binding details</span></span>  
  
 <span data-ttu-id="82f52-460">Token de suporte de endosso</span><span class="sxs-lookup"><span data-stu-id="82f52-460">Endorsing Supporting Token</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="82f52-461">Exemplos de cabeçalho de segurança: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="82f52-461">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="82f52-462">Solicitação</span><span class="sxs-lookup"><span data-stu-id="82f52-462">Request</span></span>  
  
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
  
 <span data-ttu-id="82f52-463">Resposta</span><span class="sxs-lookup"><span data-stu-id="82f52-463">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="82f52-464">Exemplos de cabeçalho de segurança: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="82f52-464">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="82f52-465">Solicitação</span><span class="sxs-lookup"><span data-stu-id="82f52-465">Request</span></span>  
  
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
  
 <span data-ttu-id="82f52-466">Resposta</span><span class="sxs-lookup"><span data-stu-id="82f52-466">Response</span></span>  
  
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
  
## <a name="63-kerberos"></a><span data-ttu-id="82f52-467">6,3 Kerberos</span><span class="sxs-lookup"><span data-stu-id="82f52-467">6.3 Kerberos</span></span>  
 <span data-ttu-id="82f52-468">Com esse modo de autenticação, o cliente é autenticado para o serviço usando um tíquete Kerberos.</span><span class="sxs-lookup"><span data-stu-id="82f52-468">With this authentication mode the client authenticates to the service using a Kerberos ticket.</span></span> <span data-ttu-id="82f52-469">Esse mesmo tíquete também fornece autenticação de servidor.</span><span class="sxs-lookup"><span data-stu-id="82f52-469">That same ticket also provides server authentication.</span></span> <span data-ttu-id="82f52-470">A associação usada é uma associação simétrica com as seguintes propriedades;</span><span class="sxs-lookup"><span data-stu-id="82f52-470">The binding used is a symmetric binding with the following properties;</span></span>  
  
 <span data-ttu-id="82f52-471">Token de proteção: tíquete Kerberos, modo de inclusão é definido como. ../IncludeToken/Once</span><span class="sxs-lookup"><span data-stu-id="82f52-471">Protection Token: Kerberos Ticket, inclusion mode is set to .../IncludeToken/Once</span></span>  
<span data-ttu-id="82f52-472">Proteção de token: false</span><span class="sxs-lookup"><span data-stu-id="82f52-472">Token Protection: False</span></span>  
  
 <span data-ttu-id="82f52-473">Assinaturas inteiras de cabeçalho e corpo: verdadeiro</span><span class="sxs-lookup"><span data-stu-id="82f52-473">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="82f52-474">Ordem de proteção: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="82f52-474">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="82f52-475">Criptografar assinatura: verdadeiro</span><span class="sxs-lookup"><span data-stu-id="82f52-475">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="82f52-476">Política</span><span class="sxs-lookup"><span data-stu-id="82f52-476">Policy</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="82f52-477">Exemplos de cabeçalho de segurança: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="82f52-477">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="82f52-478">Solicitação</span><span class="sxs-lookup"><span data-stu-id="82f52-478">Request</span></span>  
  
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
  
 <span data-ttu-id="82f52-479">Resposta</span><span class="sxs-lookup"><span data-stu-id="82f52-479">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="82f52-480">Exemplos de cabeçalho de segurança: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="82f52-480">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="82f52-481">Solicitação</span><span class="sxs-lookup"><span data-stu-id="82f52-481">Request</span></span>  
  
```xml  
<wsse:Security>  
TBD  
</wsse:Security>  
```  
  
 <span data-ttu-id="82f52-482">Resposta</span><span class="sxs-lookup"><span data-stu-id="82f52-482">Response</span></span>  
  
```xml  
<wsse:Security>  
TBD  
</wsse:Security>  
```  
  
#### <a name="64-issuedtoken"></a><span data-ttu-id="82f52-483">6,4 IssuedToken</span><span class="sxs-lookup"><span data-stu-id="82f52-483">6.4 IssuedToken</span></span>  
 <span data-ttu-id="82f52-484">Com esse modo de autenticação, o cliente não se autentica no serviço, como tal, em vez disso, o cliente apresenta um token emitido por um STS e comprova o conhecimento de uma chave compartilhada.</span><span class="sxs-lookup"><span data-stu-id="82f52-484">With this authentication mode the client does not authenticate to the service, as such, rather the client presents a token issued by an STS and proves knowledge of a shared key.</span></span> <span data-ttu-id="82f52-485">O serviço não é autenticado para o cliente, como tal, em vez disso, o STS criptografa a chave compartilhada como parte do token emitido, de modo que somente o serviço possa descriptografar a chave.</span><span class="sxs-lookup"><span data-stu-id="82f52-485">The service is not authenticated to the client, as such, instead the STS encrypts the shared key as part of the issued token such that only the service can decrypt the key.</span></span> <span data-ttu-id="82f52-486">A associação usada é como uma associação simétrica com as seguintes propriedades;</span><span class="sxs-lookup"><span data-stu-id="82f52-486">The binding used is as symmetric binding with the following properties;</span></span>  
  
 <span data-ttu-id="82f52-487">Token de proteção: token emitido, o modo de inclusão é definido como. ../IncludeToken/AlwaysToRecipient</span><span class="sxs-lookup"><span data-stu-id="82f52-487">Protection Token: Issued Token, inclusion mode is set to .../IncludeToken/AlwaysToRecipient</span></span>  
<span data-ttu-id="82f52-488">Proteção de token: false</span><span class="sxs-lookup"><span data-stu-id="82f52-488">Token Protection: False</span></span>  
  
 <span data-ttu-id="82f52-489">Assinaturas inteiras de cabeçalho e corpo: verdadeiro</span><span class="sxs-lookup"><span data-stu-id="82f52-489">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="82f52-490">Ordem de proteção: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="82f52-490">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="82f52-491">Criptografar assinatura: verdadeiro</span><span class="sxs-lookup"><span data-stu-id="82f52-491">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="82f52-492">Política</span><span class="sxs-lookup"><span data-stu-id="82f52-492">Policy</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="82f52-493">Exemplos de cabeçalho de segurança: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="82f52-493">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="82f52-494">Solicitação</span><span class="sxs-lookup"><span data-stu-id="82f52-494">Request</span></span>  
  
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
  
 <span data-ttu-id="82f52-495">Resposta</span><span class="sxs-lookup"><span data-stu-id="82f52-495">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="82f52-496">Exemplos de cabeçalho de segurança: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="82f52-496">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="82f52-497">Solicitação</span><span class="sxs-lookup"><span data-stu-id="82f52-497">Request</span></span>  
  
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
  
 <span data-ttu-id="82f52-498">Resposta</span><span class="sxs-lookup"><span data-stu-id="82f52-498">Response</span></span>  
  
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
  
### <a name="65-using-sslnegotiated-for-service-authentication"></a><span data-ttu-id="82f52-499">6,5 usando SslNegotiated para autenticação de serviço</span><span class="sxs-lookup"><span data-stu-id="82f52-499">6.5 Using SslNegotiated for Service Authentication</span></span>  
 <span data-ttu-id="82f52-500">Esta seção descreve um grupo de modos de autenticação que usam uma associação simétrica com o token de proteção sendo um token de contexto de segurança por WS-SecureConversation (WS-SC), cujo valor de chave é negociado pela execução do protocolo TLS por meio de WS-Trust (WS-T) RST/ Mensagens de RSTR.</span><span class="sxs-lookup"><span data-stu-id="82f52-500">This section describes a group of authentication modes that use a symmetric binding with the protection token being a Security Context Token per WS-SecureConversation (WS-SC) whose key value is negotiated by executing the TLS protocol over WS-Trust (WS-T) RST/RSTR messages.</span></span> <span data-ttu-id="82f52-501">Detalhes da implementação de handshake de TLS usando WS-Trust são descritos em TLSNEGO.</span><span class="sxs-lookup"><span data-stu-id="82f52-501">Details of the TLS handshake implementation using WS-Trust are described in TLSNEGO.</span></span> <span data-ttu-id="82f52-502">Aqui, nos exemplos de mensagem, vamos supor que o SCT com um contexto de segurança associado já foi estabelecido por meio de um handshake.</span><span class="sxs-lookup"><span data-stu-id="82f52-502">Here in the message examples we will assume that SCT with an associated security context is already established through a handshake.</span></span>  
  
 <span data-ttu-id="82f52-503">A associação usada é uma associação simétrica com as seguintes propriedades;</span><span class="sxs-lookup"><span data-stu-id="82f52-503">The binding used is a symmetric binding with the following properties;</span></span>  
  
 <span data-ttu-id="82f52-504">Token de proteção: SslContextToken, o modo de inclusão é definido como. ../IncludeToken/Never</span><span class="sxs-lookup"><span data-stu-id="82f52-504">Protection Token: SslContextToken, inclusion mode is set to .../IncludeToken/Never</span></span>  
<span data-ttu-id="82f52-505">Proteção de token: false</span><span class="sxs-lookup"><span data-stu-id="82f52-505">Token Protection: False</span></span>  
  
 <span data-ttu-id="82f52-506">Assinaturas inteiras de cabeçalho e corpo: verdadeiro</span><span class="sxs-lookup"><span data-stu-id="82f52-506">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="82f52-507">Ordem de proteção: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="82f52-507">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="82f52-508">Criptografar assinatura: verdadeiro</span><span class="sxs-lookup"><span data-stu-id="82f52-508">Encrypt Signature: True</span></span>  
  
#### <a name="651-policy-for-sslnegotiated-service-authentication"></a><span data-ttu-id="82f52-509">política de 6.5.1 para autenticação do serviço SslNegotiated</span><span class="sxs-lookup"><span data-stu-id="82f52-509">6.5.1 Policy for SslNegotiated service authentication</span></span>  
 <span data-ttu-id="82f52-510">A política para todos os modos de autenticação nesta seção é semelhante e difere somente por tokens de suporte ou de endosso específicos assinados usados.</span><span class="sxs-lookup"><span data-stu-id="82f52-510">Policy for all authentication modes in this section are similar and differ only by specific signed supporting or endorsing tokens used.</span></span>  
  
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
  
#### <a name="652-anonymousforsslnegotiated"></a><span data-ttu-id="82f52-511">6.5.2 AnonymousForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="82f52-511">6.5.2 AnonymousForSslNegotiated</span></span>  
 <span data-ttu-id="82f52-512">Com esse modo de autenticação, o cliente é anônimo e o serviço é autenticado usando um certificado X. 509.</span><span class="sxs-lookup"><span data-stu-id="82f52-512">With this authentication mode the client is anonymous and the service is authenticated using an X.509 certificate.</span></span> <span data-ttu-id="82f52-513">A associação usada é uma instância da Associação simétrica, conforme descrito em 6.5.1 acima.</span><span class="sxs-lookup"><span data-stu-id="82f52-513">The binding used is an instance of symmetric binding as described in 6.5.1 above.</span></span>  
  
 <span data-ttu-id="82f52-514">Política</span><span class="sxs-lookup"><span data-stu-id="82f52-514">Policy</span></span>  
  
 <span data-ttu-id="82f52-515">Consulte a política em 6.5.1 acima para obter detalhes de associação.</span><span class="sxs-lookup"><span data-stu-id="82f52-515">See Policy in 6.5.1 above for binding details.</span></span>  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="82f52-516">Exemplos de cabeçalho de segurança: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="82f52-516">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="82f52-517">Solicitação</span><span class="sxs-lookup"><span data-stu-id="82f52-517">Request</span></span>  
  
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
  
 <span data-ttu-id="82f52-518">Resposta</span><span class="sxs-lookup"><span data-stu-id="82f52-518">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="82f52-519">Exemplos de cabeçalho de segurança: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="82f52-519">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="82f52-520">Solicitação</span><span class="sxs-lookup"><span data-stu-id="82f52-520">Request</span></span>  
  
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
  
 <span data-ttu-id="82f52-521">Resposta</span><span class="sxs-lookup"><span data-stu-id="82f52-521">Response</span></span>  
  
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
  
#### <a name="653-usernameforsslnegotiated"></a><span data-ttu-id="82f52-522">6.5.3 UserNameForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="82f52-522">6.5.3 UserNameForSslNegotiated</span></span>  
 <span data-ttu-id="82f52-523">Com esse modo de autenticação, o cliente é autenticado usando um token de nome de usuário que aparece na camada SOAP como um token de suporte assinado.</span><span class="sxs-lookup"><span data-stu-id="82f52-523">With this authentication mode the client is authenticates using a Username Token which appears at the SOAP layer as a signed supporting token.</span></span> <span data-ttu-id="82f52-524">O serviço é autenticado usando um certificado X. 509.</span><span class="sxs-lookup"><span data-stu-id="82f52-524">The service is authenticated using an X.509 certificate.</span></span> <span data-ttu-id="82f52-525">A associação usada é uma instância da Associação simétrica, conforme descrito em 6.5.1.</span><span class="sxs-lookup"><span data-stu-id="82f52-525">The binding used is an instance of symmetric binding as described in 6.5.1.</span></span>  
  
 <span data-ttu-id="82f52-526">Política</span><span class="sxs-lookup"><span data-stu-id="82f52-526">Policy</span></span>  
  
 <span data-ttu-id="82f52-527">Consulte a seção 6.5.1 acima para obter detalhes de associação</span><span class="sxs-lookup"><span data-stu-id="82f52-527">See section 6.5.1 above for binding details</span></span>  
  
 <span data-ttu-id="82f52-528">Token de suporte assinado</span><span class="sxs-lookup"><span data-stu-id="82f52-528">Signed Supporting Token</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="82f52-529">Exemplos de cabeçalho de segurança: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="82f52-529">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="82f52-530">Solicitação</span><span class="sxs-lookup"><span data-stu-id="82f52-530">Request</span></span>  
  
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
  
 <span data-ttu-id="82f52-531">Resposta</span><span class="sxs-lookup"><span data-stu-id="82f52-531">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="82f52-532">Exemplos de cabeçalho de segurança: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="82f52-532">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="82f52-533">Solicitação</span><span class="sxs-lookup"><span data-stu-id="82f52-533">Request</span></span>  
  
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
  
 <span data-ttu-id="82f52-534">Resposta</span><span class="sxs-lookup"><span data-stu-id="82f52-534">Response</span></span>  
  
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
  
#### <a name="654-issuedtokenforsslnegotiated"></a><span data-ttu-id="82f52-535">6.5.4 IssuedTokenForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="82f52-535">6.5.4 IssuedTokenForSslNegotiated</span></span>  
 <span data-ttu-id="82f52-536">Com esse modo de autenticação, o cliente não se autentica no serviço, como tal, mas apresenta um token emitido por um STS e comprova o conhecimento de uma chave compartilhada.</span><span class="sxs-lookup"><span data-stu-id="82f52-536">With this authentication mode the client does not authenticate to the service, as such, but instead presents a token issued by an STS and proves knowledge of a shared key.</span></span> <span data-ttu-id="82f52-537">O token emitido é exibido na camada SOAP como um token de suporte de endosso.</span><span class="sxs-lookup"><span data-stu-id="82f52-537">The issued token appears at the SOAP layer as an endorsing supporting token.</span></span> <span data-ttu-id="82f52-538">O serviço é autenticado usando um certificado X. 509.</span><span class="sxs-lookup"><span data-stu-id="82f52-538">The service is authenticated using an X.509 certificate.</span></span> <span data-ttu-id="82f52-539">A associação usada é uma instância da Associação simétrica, conforme descrito em 6.5.1 acima.</span><span class="sxs-lookup"><span data-stu-id="82f52-539">The binding used is an instance of symmetric binding as described in 6.5.1 above.</span></span>  
  
 <span data-ttu-id="82f52-540">Política</span><span class="sxs-lookup"><span data-stu-id="82f52-540">Policy</span></span>  
  
 <span data-ttu-id="82f52-541">Consulte a seção 6.5.1 acima para obter detalhes de associação</span><span class="sxs-lookup"><span data-stu-id="82f52-541">See section 6.5.1 above for binding details</span></span>  
  
 <span data-ttu-id="82f52-542">Token de suporte de endosso</span><span class="sxs-lookup"><span data-stu-id="82f52-542">Endorsing Supporting Token</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="82f52-543">Exemplos de cabeçalho de segurança: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="82f52-543">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="82f52-544">Solicitação</span><span class="sxs-lookup"><span data-stu-id="82f52-544">Request</span></span>  
  
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
  
 <span data-ttu-id="82f52-545">Resposta</span><span class="sxs-lookup"><span data-stu-id="82f52-545">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="82f52-546">Exemplos de cabeçalho de segurança: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="82f52-546">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="82f52-547">Solicitação</span><span class="sxs-lookup"><span data-stu-id="82f52-547">Request</span></span>  
  
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
  
 <span data-ttu-id="82f52-548">Resposta</span><span class="sxs-lookup"><span data-stu-id="82f52-548">Response</span></span>  
  
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
  
#### <a name="655-mutualsslnegotiated"></a><span data-ttu-id="82f52-549">6.5.5 MutualSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="82f52-549">6.5.5 MutualSslNegotiated</span></span>  
 <span data-ttu-id="82f52-550">Com esse modo de autenticação, o cliente e o serviço se autenticam usando certificados X. 509.</span><span class="sxs-lookup"><span data-stu-id="82f52-550">With this authentication mode the client and the service authenticate using X.509 certificates.</span></span> <span data-ttu-id="82f52-551">A associação usada é uma instância da Associação simétrica, conforme descrito em 6.5.1 acima.</span><span class="sxs-lookup"><span data-stu-id="82f52-551">The binding used is an instance of symmetric binding as described in 6.5.1 above.</span></span>  
  
 <span data-ttu-id="82f52-552">Política</span><span class="sxs-lookup"><span data-stu-id="82f52-552">Policy</span></span>  
  
 <span data-ttu-id="82f52-553">Consulte a seção 6.5.1 acima para obter detalhes de associação</span><span class="sxs-lookup"><span data-stu-id="82f52-553">See section 6.5.1 above for binding details</span></span>  
  
 <span data-ttu-id="82f52-554">Token de suporte de endosso</span><span class="sxs-lookup"><span data-stu-id="82f52-554">Endorsing Supporting Token</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="82f52-555">Exemplos de cabeçalho de segurança: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="82f52-555">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="82f52-556">Solicitação</span><span class="sxs-lookup"><span data-stu-id="82f52-556">Request</span></span>  
  
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
  
 <span data-ttu-id="82f52-557">Resposta</span><span class="sxs-lookup"><span data-stu-id="82f52-557">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="82f52-558">Exemplos de cabeçalho de segurança: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="82f52-558">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="82f52-559">Solicitação</span><span class="sxs-lookup"><span data-stu-id="82f52-559">Request</span></span>  
  
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
  
 <span data-ttu-id="82f52-560">Resposta</span><span class="sxs-lookup"><span data-stu-id="82f52-560">Response</span></span>  
  
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
  
### <a name="66-sspinegotiated"></a><span data-ttu-id="82f52-561">6,6 SspiNegotiated</span><span class="sxs-lookup"><span data-stu-id="82f52-561">6.6 SspiNegotiated</span></span>  
 <span data-ttu-id="82f52-562">Com esse modo de autenticação, um protocolo de negociação é usado para executar a autenticação de cliente e servidor.</span><span class="sxs-lookup"><span data-stu-id="82f52-562">With this authentication mode a negotiation protocol is used to perform client and server authentication.</span></span> <span data-ttu-id="82f52-563">O Kerberos é usado se possível, caso contrário, NTLM.</span><span class="sxs-lookup"><span data-stu-id="82f52-563">Kerberos is used if possible, otherwise NTLM.</span></span> <span data-ttu-id="82f52-564">A associação usada é uma associação simétrica com as seguintes propriedades;</span><span class="sxs-lookup"><span data-stu-id="82f52-564">The binding used is a symmetric binding with the following properties;</span></span>  
  
 <span data-ttu-id="82f52-565">Token de proteção: SpnegoContextToken, o modo de inclusão é definido como. ../IncludeToken/AlwaysToRecipient</span><span class="sxs-lookup"><span data-stu-id="82f52-565">Protection Token: SpnegoContextToken, inclusion mode is set to .../IncludeToken/AlwaysToRecipient</span></span>  
<span data-ttu-id="82f52-566">Proteção de token: false</span><span class="sxs-lookup"><span data-stu-id="82f52-566">Token Protection: False</span></span>  
  
 <span data-ttu-id="82f52-567">Assinaturas inteiras de cabeçalho e corpo: verdadeiro</span><span class="sxs-lookup"><span data-stu-id="82f52-567">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="82f52-568">Ordem de proteção: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="82f52-568">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="82f52-569">Criptografar assinatura: verdadeiro</span><span class="sxs-lookup"><span data-stu-id="82f52-569">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="82f52-570">Política</span><span class="sxs-lookup"><span data-stu-id="82f52-570">Policy</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="82f52-571">Exemplos de cabeçalho de segurança: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="82f52-571">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="82f52-572">Solicitação</span><span class="sxs-lookup"><span data-stu-id="82f52-572">Request</span></span>  
  
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
  
 <span data-ttu-id="82f52-573">Resposta</span><span class="sxs-lookup"><span data-stu-id="82f52-573">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="82f52-574">Exemplos de cabeçalho de segurança: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="82f52-574">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="82f52-575">Solicitação</span><span class="sxs-lookup"><span data-stu-id="82f52-575">Request</span></span>  
  
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
  
 <span data-ttu-id="82f52-576">Resposta</span><span class="sxs-lookup"><span data-stu-id="82f52-576">Response</span></span>  
  
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
  
### <a name="67-secureconversation"></a><span data-ttu-id="82f52-577">6,7 SecureConversation</span><span class="sxs-lookup"><span data-stu-id="82f52-577">6.7 SecureConversation</span></span>  
 <span data-ttu-id="82f52-578">A associação usada é uma associação simétrica com o token de proteção sendo um SCT por WS-SecureConversation (WS-SC).</span><span class="sxs-lookup"><span data-stu-id="82f52-578">The binding used is a symmetric binding with the protection token being a SCT per WS-SecureConversation (WS-SC).</span></span> <span data-ttu-id="82f52-579">O SCT é negociado usando WS-Trust (WS-Trust) ou WS-SecureConversation (WS-SC) de acordo com uma associação aninhada, que, por sua vez, é uma ligação simétrica que usa um protocolo de negociação.</span><span class="sxs-lookup"><span data-stu-id="82f52-579">The SCT is negotiated using WS-Trust (WS-Trust) or WS-SecureConversation (WS-SC) according to a nested binding, which is itself a symmetric binding that uses a negotiation protocol.</span></span> <span data-ttu-id="82f52-580">O protocolo de negociação usará o Kerberos para executar a autenticação de cliente e servidor, se possível.</span><span class="sxs-lookup"><span data-stu-id="82f52-580">The negotiation protocol will use Kerberos to perform client and server authentication if possible.</span></span> <span data-ttu-id="82f52-581">Se o Kerberos não puder ser usado, ele retornará ao NTLM.</span><span class="sxs-lookup"><span data-stu-id="82f52-581">If Kerberos cannot be used, it will fall back to NTLM.</span></span>  
  
 <span data-ttu-id="82f52-582">Política</span><span class="sxs-lookup"><span data-stu-id="82f52-582">Policy</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="82f52-583">Exemplos de cabeçalho de segurança: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="82f52-583">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="82f52-584">Solicitação</span><span class="sxs-lookup"><span data-stu-id="82f52-584">Request</span></span>  
  
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
  
 <span data-ttu-id="82f52-585">Resposta</span><span class="sxs-lookup"><span data-stu-id="82f52-585">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="82f52-586">Exemplos de cabeçalho de segurança: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="82f52-586">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="82f52-587">Solicitação</span><span class="sxs-lookup"><span data-stu-id="82f52-587">Request</span></span>  
  
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
  
 <span data-ttu-id="82f52-588">Resposta</span><span class="sxs-lookup"><span data-stu-id="82f52-588">Response</span></span>  
  
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
