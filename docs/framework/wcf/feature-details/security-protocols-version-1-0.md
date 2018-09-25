---
title: Protocolos de segurança versão 1.0
ms.date: 03/30/2017
ms.assetid: ee3402d2-1076-410b-a3cb-fae0372bd7af
author: BrucePerlerMS
ms.openlocfilehash: 043a092855b7f5827c03b1d247b03328ba561edf
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47083040"
---
# <a name="security-protocols-version-10"></a><span data-ttu-id="eaaa4-102">Protocolos de segurança versão 1.0</span><span class="sxs-lookup"><span data-stu-id="eaaa4-102">Security Protocols version 1.0</span></span>
<span data-ttu-id="eaaa4-103">Os protocolos de segurança de serviços Web fornecem mecanismos de segurança de serviços Web que abrangem todos os empresariais existentes, requisitos de segurança de mensagens.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-103">The Web Services Security Protocols provide Web services security mechanisms that cover all existing enterprise messaging security requirements.</span></span> <span data-ttu-id="eaaa4-104">Esta seção descreve os detalhes do Windows Communication Foundation (WCF) versão 1.0 (implementado de <xref:System.ServiceModel.Channels.SecurityBindingElement>) para protocolos de segurança de serviços da Web a seguir.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-104">This section describes the Windows Communication Foundation (WCF) version 1.0 details (implemented in the <xref:System.ServiceModel.Channels.SecurityBindingElement>) for the following Web services security protocols.</span></span>  
  
|<span data-ttu-id="eaaa4-105">Especificação/documento</span><span class="sxs-lookup"><span data-stu-id="eaaa4-105">Specification/Document</span></span>|<span data-ttu-id="eaaa4-106">Link</span><span class="sxs-lookup"><span data-stu-id="eaaa4-106">Link</span></span>|  
|-|-|  
|<span data-ttu-id="eaaa4-107">WSS: Segurança de mensagem SOAP 1.0</span><span class="sxs-lookup"><span data-stu-id="eaaa4-107">WSS: SOAP Message Security 1.0</span></span>|http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0.pdf|  
|<span data-ttu-id="eaaa4-108">WSS: Perfil de Token de nome de usuário 1.0</span><span class="sxs-lookup"><span data-stu-id="eaaa4-108">WSS: Username Token Profile 1.0</span></span>|http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0.pdf|  
|<span data-ttu-id="eaaa4-109">WSS: X509 Token Profile 1.0</span><span class="sxs-lookup"><span data-stu-id="eaaa4-109">WSS: X509 Token Profile 1.0</span></span>|http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-x509-token-profile-1.0.pdf|  
|<span data-ttu-id="eaaa4-110">WSS: SAML 1.1 Token Profile 1.0</span><span class="sxs-lookup"><span data-stu-id="eaaa4-110">WSS: SAML 1.1 Token Profile 1.0</span></span>|http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.0.pdf|  
|<span data-ttu-id="eaaa4-111">WSS: Segurança de mensagem SOAP 1.1</span><span class="sxs-lookup"><span data-stu-id="eaaa4-111">WSS: SOAP Message Security 1.1</span></span>|http://www.oasis-open.org/committees/download.php/16790/wss-v1.1-spec-os-SOAPMessageSecurity.pdf|  
|<span data-ttu-id="eaaa4-112">Perfil de Token de nome de usuário 1.1 do WSS</span><span class="sxs-lookup"><span data-stu-id="eaaa4-112">WSS Username Token Profile 1.1</span></span>|http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0.pdf|  
|<span data-ttu-id="eaaa4-113">WSS: Perfil de Token de x. 509 1.1</span><span class="sxs-lookup"><span data-stu-id="eaaa4-113">WSS: X.509 Token Profile 1.1</span></span>|http://www.oasis-open.org/committees/download.php/16785/wss-v1.1-spec-os-x509TokenProfile.pdf|  
|<span data-ttu-id="eaaa4-114">WSS: Perfil de Token Kerberos 1.1</span><span class="sxs-lookup"><span data-stu-id="eaaa4-114">WSS: Kerberos Token Profile 1.1</span></span>|http://www.oasis-open.org/committees/download.php/16788/wss-v1.1-spec-os-KerberosTokenProfile.pdf|  
|<span data-ttu-id="eaaa4-115">WSS: SAML 1.1 Profile 1.1 de Token</span><span class="sxs-lookup"><span data-stu-id="eaaa4-115">WSS: SAML 1.1 Token Profile 1.1</span></span>|http://www.oasis-open.org/committees/download.php/16768/wss-v1.1-spec-os-SAMLTokenProfile.pdf|  
|<span data-ttu-id="eaaa4-116">WS-Secure Conversation</span><span class="sxs-lookup"><span data-stu-id="eaaa4-116">WS-Secure Conversation</span></span>|http://msdn.microsoft.com/ws/2005/02/ws-secure-conversation/|  
|<span data-ttu-id="eaaa4-117">WS-Trust</span><span class="sxs-lookup"><span data-stu-id="eaaa4-117">WS-Trust</span></span>|http://msdn.microsoft.com/ws/2005/02/ws-trust/|  
|<span data-ttu-id="eaaa4-118">Observação de aplicativo:</span><span class="sxs-lookup"><span data-stu-id="eaaa4-118">Application Note:</span></span><br /><br /> <span data-ttu-id="eaaa4-119">Usando o WS-Trust para o Handshake TLS</span><span class="sxs-lookup"><span data-stu-id="eaaa4-119">Using WS-Trust for TLS Handshake</span></span>|<span data-ttu-id="eaaa4-120">Para serem publicados</span><span class="sxs-lookup"><span data-stu-id="eaaa4-120">To be published</span></span>|  
|<span data-ttu-id="eaaa4-121">Observação de aplicativo:</span><span class="sxs-lookup"><span data-stu-id="eaaa4-121">Application Note:</span></span><br /><br /> <span data-ttu-id="eaaa4-122">Usando o WS-Trust para SPNEGO</span><span class="sxs-lookup"><span data-stu-id="eaaa4-122">Using WS-Trust for SPNEGO</span></span>|<span data-ttu-id="eaaa4-123">Para serem publicados</span><span class="sxs-lookup"><span data-stu-id="eaaa4-123">To be published</span></span>|  
|<span data-ttu-id="eaaa4-124">Observação de aplicativo:</span><span class="sxs-lookup"><span data-stu-id="eaaa4-124">Application Note:</span></span><br /><br /> <span data-ttu-id="eaaa4-125">Identidade e referências de endereçamento de ponto de extremidade de serviços Web</span><span class="sxs-lookup"><span data-stu-id="eaaa4-125">Web Services Addressing Endpoint References And Identity</span></span>|<span data-ttu-id="eaaa4-126">Para serem publicados</span><span class="sxs-lookup"><span data-stu-id="eaaa4-126">To be published</span></span>|  
|<span data-ttu-id="eaaa4-127">O WS-SecurityPolicy 1.1</span><span class="sxs-lookup"><span data-stu-id="eaaa4-127">WS-SecurityPolicy 1.1</span></span><br /><br /> <span data-ttu-id="eaaa4-128">(2005/07)</span><span class="sxs-lookup"><span data-stu-id="eaaa4-128">(2005/07)</span></span>|http://msdn.microsoft.com/ws/2005/07/ws-security-policy/<br /><br /> <span data-ttu-id="eaaa4-129">como corrigida por errata enviado ao OASIS WS-SX Technical Committee http://www.oasis-open.org/archives/ws-sx/200512/msg00017.html</span><span class="sxs-lookup"><span data-stu-id="eaaa4-129">as amended by errata submitted to OASIS WS-SX Technical Committee http://www.oasis-open.org/archives/ws-sx/200512/msg00017.html</span></span>|  
  
 <span data-ttu-id="eaaa4-130">O WCF, versão 1, oferece 17 modos de autenticação que podem ser usados como a base de configuração de segurança de serviços da Web.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-130">WCF, version 1, provides 17 authentication modes that can be used as the basis for Web services security configuration.</span></span> <span data-ttu-id="eaaa4-131">Cada modo é otimizado para um conjunto comum de requisitos de implantação, tais como:</span><span class="sxs-lookup"><span data-stu-id="eaaa4-131">Each mode is optimized for a common set of deployment requirements, such as:</span></span>  
  
-   <span data-ttu-id="eaaa4-132">Credenciais usadas para autenticar o cliente e o serviço.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-132">Credentials used to authenticate client and service.</span></span>  
  
-   <span data-ttu-id="eaaa4-133">Mecanismos de proteção de segurança transporte ou de mensagem.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-133">Message or transport security protection mechanisms.</span></span>  
  
-   <span data-ttu-id="eaaa4-134">Padrões de troca de mensagem.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-134">Message exchange patterns.</span></span>  
  
|<span data-ttu-id="eaaa4-135">Modo de autenticação</span><span class="sxs-lookup"><span data-stu-id="eaaa4-135">Authentication Mode</span></span>|<span data-ttu-id="eaaa4-136">Autenticação de cliente</span><span class="sxs-lookup"><span data-stu-id="eaaa4-136">Client Authentication</span></span>|<span data-ttu-id="eaaa4-137">Autenticação de servidor</span><span class="sxs-lookup"><span data-stu-id="eaaa4-137">Server Authentication</span></span>|<span data-ttu-id="eaaa4-138">Modo</span><span class="sxs-lookup"><span data-stu-id="eaaa4-138">Mode</span></span>|  
|-------------------------|---------------------------|---------------------------|----------|  
|<span data-ttu-id="eaaa4-139">UserNameOverTransport</span><span class="sxs-lookup"><span data-stu-id="eaaa4-139">UserNameOverTransport</span></span>|<span data-ttu-id="eaaa4-140">Nome de usuário/senha</span><span class="sxs-lookup"><span data-stu-id="eaaa4-140">User name/password</span></span>|<span data-ttu-id="eaaa4-141">X509</span><span class="sxs-lookup"><span data-stu-id="eaaa4-141">X509</span></span>|<span data-ttu-id="eaaa4-142">Transporte</span><span class="sxs-lookup"><span data-stu-id="eaaa4-142">Transport</span></span>|  
|<span data-ttu-id="eaaa4-143">CertificateOverTransport</span><span class="sxs-lookup"><span data-stu-id="eaaa4-143">CertificateOverTransport</span></span>|<span data-ttu-id="eaaa4-144">X509</span><span class="sxs-lookup"><span data-stu-id="eaaa4-144">X509</span></span>|<span data-ttu-id="eaaa4-145">X509</span><span class="sxs-lookup"><span data-stu-id="eaaa4-145">X509</span></span>|<span data-ttu-id="eaaa4-146">Transporte</span><span class="sxs-lookup"><span data-stu-id="eaaa4-146">Transport</span></span>|  
|<span data-ttu-id="eaaa4-147">KerberosOverTransport</span><span class="sxs-lookup"><span data-stu-id="eaaa4-147">KerberosOverTransport</span></span>|<span data-ttu-id="eaaa4-148">Windows</span><span class="sxs-lookup"><span data-stu-id="eaaa4-148">Windows</span></span>|<span data-ttu-id="eaaa4-149">X509</span><span class="sxs-lookup"><span data-stu-id="eaaa4-149">X509</span></span>|<span data-ttu-id="eaaa4-150">Transporte</span><span class="sxs-lookup"><span data-stu-id="eaaa4-150">Transport</span></span>|  
|<span data-ttu-id="eaaa4-151">IssuedTokenOverTransport</span><span class="sxs-lookup"><span data-stu-id="eaaa4-151">IssuedTokenOverTransport</span></span>|<span data-ttu-id="eaaa4-152">Federado</span><span class="sxs-lookup"><span data-stu-id="eaaa4-152">Federated</span></span>|<span data-ttu-id="eaaa4-153">X509</span><span class="sxs-lookup"><span data-stu-id="eaaa4-153">X509</span></span>|<span data-ttu-id="eaaa4-154">Transporte</span><span class="sxs-lookup"><span data-stu-id="eaaa4-154">Transport</span></span>|  
|<span data-ttu-id="eaaa4-155">SspiNegotiatedOverTransport</span><span class="sxs-lookup"><span data-stu-id="eaaa4-155">SspiNegotiatedOverTransport</span></span>|<span data-ttu-id="eaaa4-156">Sspi Windows negociado</span><span class="sxs-lookup"><span data-stu-id="eaaa4-156">Windows Sspi Negotiated</span></span>|<span data-ttu-id="eaaa4-157">Sspi Windows negociado</span><span class="sxs-lookup"><span data-stu-id="eaaa4-157">Windows Sspi Negotiated</span></span>|<span data-ttu-id="eaaa4-158">Transporte</span><span class="sxs-lookup"><span data-stu-id="eaaa4-158">Transport</span></span>|  
|<span data-ttu-id="eaaa4-159">AnonymousForCertificate</span><span class="sxs-lookup"><span data-stu-id="eaaa4-159">AnonymousForCertificate</span></span>|<span data-ttu-id="eaaa4-160">Nenhum</span><span class="sxs-lookup"><span data-stu-id="eaaa4-160">None</span></span>|<span data-ttu-id="eaaa4-161">X509</span><span class="sxs-lookup"><span data-stu-id="eaaa4-161">X509</span></span>|<span data-ttu-id="eaaa4-162">Mensagem</span><span class="sxs-lookup"><span data-stu-id="eaaa4-162">Message</span></span>|  
|<span data-ttu-id="eaaa4-163">UserNameForCertificate</span><span class="sxs-lookup"><span data-stu-id="eaaa4-163">UserNameForCertificate</span></span>|<span data-ttu-id="eaaa4-164">Nome de usuário/senha</span><span class="sxs-lookup"><span data-stu-id="eaaa4-164">User name/password</span></span>|<span data-ttu-id="eaaa4-165">X509</span><span class="sxs-lookup"><span data-stu-id="eaaa4-165">X509</span></span>|<span data-ttu-id="eaaa4-166">Mensagem</span><span class="sxs-lookup"><span data-stu-id="eaaa4-166">Message</span></span>|  
|<span data-ttu-id="eaaa4-167">MutualCertificate</span><span class="sxs-lookup"><span data-stu-id="eaaa4-167">MutualCertificate</span></span>|<span data-ttu-id="eaaa4-168">X509</span><span class="sxs-lookup"><span data-stu-id="eaaa4-168">X509</span></span>|<span data-ttu-id="eaaa4-169">X509</span><span class="sxs-lookup"><span data-stu-id="eaaa4-169">X509</span></span>|<span data-ttu-id="eaaa4-170">Mensagem</span><span class="sxs-lookup"><span data-stu-id="eaaa4-170">Message</span></span>|  
|<span data-ttu-id="eaaa4-171">MutualCertificateDuplex</span><span class="sxs-lookup"><span data-stu-id="eaaa4-171">MutualCertificateDuplex</span></span>|<span data-ttu-id="eaaa4-172">X509</span><span class="sxs-lookup"><span data-stu-id="eaaa4-172">X509</span></span>|<span data-ttu-id="eaaa4-173">X509</span><span class="sxs-lookup"><span data-stu-id="eaaa4-173">X509</span></span>|<span data-ttu-id="eaaa4-174">Mensagem</span><span class="sxs-lookup"><span data-stu-id="eaaa4-174">Message</span></span>|  
|<span data-ttu-id="eaaa4-175">IssuedTokenForCertificate</span><span class="sxs-lookup"><span data-stu-id="eaaa4-175">IssuedTokenForCertificate</span></span>|<span data-ttu-id="eaaa4-176">Federado</span><span class="sxs-lookup"><span data-stu-id="eaaa4-176">Federated</span></span>|<span data-ttu-id="eaaa4-177">X509</span><span class="sxs-lookup"><span data-stu-id="eaaa4-177">X509</span></span>|<span data-ttu-id="eaaa4-178">Mensagem</span><span class="sxs-lookup"><span data-stu-id="eaaa4-178">Message</span></span>|  
|<span data-ttu-id="eaaa4-179">Kerberos</span><span class="sxs-lookup"><span data-stu-id="eaaa4-179">Kerberos</span></span>|<span data-ttu-id="eaaa4-180">Windows</span><span class="sxs-lookup"><span data-stu-id="eaaa4-180">Windows</span></span>|<span data-ttu-id="eaaa4-181">Windows</span><span class="sxs-lookup"><span data-stu-id="eaaa4-181">Windows</span></span>|<span data-ttu-id="eaaa4-182">Mensagem</span><span class="sxs-lookup"><span data-stu-id="eaaa4-182">Message</span></span>|  
|<span data-ttu-id="eaaa4-183">IssuedToken</span><span class="sxs-lookup"><span data-stu-id="eaaa4-183">IssuedToken</span></span>|<span data-ttu-id="eaaa4-184">Federado</span><span class="sxs-lookup"><span data-stu-id="eaaa4-184">Federated</span></span>|<span data-ttu-id="eaaa4-185">Federado</span><span class="sxs-lookup"><span data-stu-id="eaaa4-185">Federated</span></span>|<span data-ttu-id="eaaa4-186">Mensagem</span><span class="sxs-lookup"><span data-stu-id="eaaa4-186">Message</span></span>|  
|<span data-ttu-id="eaaa4-187">SspiNegotiated</span><span class="sxs-lookup"><span data-stu-id="eaaa4-187">SspiNegotiated</span></span>|<span data-ttu-id="eaaa4-188">Sspi Windows negociado</span><span class="sxs-lookup"><span data-stu-id="eaaa4-188">Windows Sspi Negotiated</span></span>|<span data-ttu-id="eaaa4-189">Sspi Windows negociado</span><span class="sxs-lookup"><span data-stu-id="eaaa4-189">Windows Sspi Negotiated</span></span>|<span data-ttu-id="eaaa4-190">Mensagem</span><span class="sxs-lookup"><span data-stu-id="eaaa4-190">Message</span></span>|  
|<span data-ttu-id="eaaa4-191">AnonymousForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="eaaa4-191">AnonymousForSslNegotiated</span></span>|<span data-ttu-id="eaaa4-192">Nenhum</span><span class="sxs-lookup"><span data-stu-id="eaaa4-192">None</span></span>|<span data-ttu-id="eaaa4-193">X509, Nego de TLS</span><span class="sxs-lookup"><span data-stu-id="eaaa4-193">X509, TLS-Nego</span></span>|<span data-ttu-id="eaaa4-194">Mensagem</span><span class="sxs-lookup"><span data-stu-id="eaaa4-194">Message</span></span>|  
|<span data-ttu-id="eaaa4-195">UserNameForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="eaaa4-195">UserNameForSslNegotiated</span></span>|<span data-ttu-id="eaaa4-196">Nome de usuário/senha</span><span class="sxs-lookup"><span data-stu-id="eaaa4-196">User name/password</span></span>|<span data-ttu-id="eaaa4-197">X509, Nego de TLS</span><span class="sxs-lookup"><span data-stu-id="eaaa4-197">X509, TLS-Nego</span></span>|<span data-ttu-id="eaaa4-198">Mensagem</span><span class="sxs-lookup"><span data-stu-id="eaaa4-198">Message</span></span>|  
|<span data-ttu-id="eaaa4-199">MutualSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="eaaa4-199">MutualSslNegotiated</span></span>|<span data-ttu-id="eaaa4-200">X509</span><span class="sxs-lookup"><span data-stu-id="eaaa4-200">X509</span></span>|<span data-ttu-id="eaaa4-201">X509, Nego de TLS</span><span class="sxs-lookup"><span data-stu-id="eaaa4-201">X509, TLS-Nego</span></span>|<span data-ttu-id="eaaa4-202">Mensagem</span><span class="sxs-lookup"><span data-stu-id="eaaa4-202">Message</span></span>|  
|<span data-ttu-id="eaaa4-203">IssuedTokenForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="eaaa4-203">IssuedTokenForSslNegotiated</span></span>|<span data-ttu-id="eaaa4-204">Federado</span><span class="sxs-lookup"><span data-stu-id="eaaa4-204">Federated</span></span>|<span data-ttu-id="eaaa4-205">X509, Nego de TLS</span><span class="sxs-lookup"><span data-stu-id="eaaa4-205">X509, TLS-Nego</span></span>|<span data-ttu-id="eaaa4-206">Mensagem</span><span class="sxs-lookup"><span data-stu-id="eaaa4-206">Message</span></span>|  
  
 <span data-ttu-id="eaaa4-207">Pontos de extremidade usando esses modos de autenticação podem expressar seus requisitos de segurança usando o WS-SecurityPolicy (WS-SP).</span><span class="sxs-lookup"><span data-stu-id="eaaa4-207">Endpoints using such authentication modes can express their security requirements using WS-SecurityPolicy (WS-SP).</span></span> <span data-ttu-id="eaaa4-208">Este documento descreve a estrutura de cabeçalho de segurança e as mensagens de infraestrutura para cada modo de autenticação e fornece exemplos de políticas e mensagens.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-208">This document describes the structure of security header and infrastructure messages for each authentication mode and provides examples of policies and messages.</span></span>  
  
 <span data-ttu-id="eaaa4-209">WCF aproveita o WS-SecureConversation para oferecer suportam a sessões seguras para proteger as trocas de várias mensagens entre aplicativos.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-209">WCF leverages WS-SecureConversation to provide secure sessions support to protect multi-message exchanges between applications.</span></span>  <span data-ttu-id="eaaa4-210">Consulte "Secure sessões" abaixo para obter detalhes de implementação.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-210">See "Secure Sessions" below for implementation details.</span></span>  
  
 <span data-ttu-id="eaaa4-211">Além dos modos de autenticação, o WCF fornece as configurações para controlar os mecanismos de proteção comuns que se aplicam à maioria dos modos de autenticação com base em segurança de mensagem, por exemplo: ordem de assinatura versus operações de criptografia, conjuntos de algoritmo, derivação de chave e a confirmação de assinatura.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-211">In addition to authentication modes, WCF provides settings to control common protection mechanisms that apply to most message security-based authentication modes, for example: order of signature versus encryption operations, algorithm suites, key derivation, and signature confirmation.</span></span>  
  
 <span data-ttu-id="eaaa4-212">Os prefixos e namespaces a seguir são usados neste documento.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-212">The following prefixes and namespaces are used in this document.</span></span>  
  
|<span data-ttu-id="eaaa4-213">Prefixo</span><span class="sxs-lookup"><span data-stu-id="eaaa4-213">Prefix</span></span>|<span data-ttu-id="eaaa4-214">Namespace</span><span class="sxs-lookup"><span data-stu-id="eaaa4-214">Namespace</span></span>|  
|------------|---------------|  
|<span data-ttu-id="eaaa4-215">s</span><span class="sxs-lookup"><span data-stu-id="eaaa4-215">s</span></span>|http://www.w3.org/2003/05/soap-envelope|  
|<span data-ttu-id="eaaa4-216">SP</span><span class="sxs-lookup"><span data-stu-id="eaaa4-216">sp</span></span>|http://schemas.xmlsoap.org/ws/2005/07/securitypolicy|  
|<span data-ttu-id="eaaa4-217">a</span><span class="sxs-lookup"><span data-stu-id="eaaa4-217">a</span></span>|http://www.w3.org/2005/08/addressing|  
|<span data-ttu-id="eaaa4-218">wsse</span><span class="sxs-lookup"><span data-stu-id="eaaa4-218">wsse</span></span>|<span data-ttu-id="eaaa4-219">TBD – URI DO OASIS WSS 1.0</span><span class="sxs-lookup"><span data-stu-id="eaaa4-219">TBD – OASIS WSS 1.0 URI</span></span>|  
|<span data-ttu-id="eaaa4-220">wsse11</span><span class="sxs-lookup"><span data-stu-id="eaaa4-220">wsse11</span></span>|<span data-ttu-id="eaaa4-221">TBD – OASIS WSS 1.1 URI</span><span class="sxs-lookup"><span data-stu-id="eaaa4-221">TBD – OASIS WSS 1.1 URI</span></span>|  
|<span data-ttu-id="eaaa4-222">wsu</span><span class="sxs-lookup"><span data-stu-id="eaaa4-222">wsu</span></span>|<span data-ttu-id="eaaa4-223">TBD – OASIS WSS 1.0 utilitário URI</span><span class="sxs-lookup"><span data-stu-id="eaaa4-223">TBD – OASIS WSS 1.0 Utility URI</span></span>|  
|<span data-ttu-id="eaaa4-224">DS</span><span class="sxs-lookup"><span data-stu-id="eaaa4-224">ds</span></span>|<span data-ttu-id="eaaa4-225">TBD – W3C XMLDSig URI</span><span class="sxs-lookup"><span data-stu-id="eaaa4-225">TBD – W3C XMLDSig URI</span></span>|  
|<span data-ttu-id="eaaa4-226">WST</span><span class="sxs-lookup"><span data-stu-id="eaaa4-226">wst</span></span>|<span data-ttu-id="eaaa4-227">TBD – URI de 2005 do WS-Trust/02</span><span class="sxs-lookup"><span data-stu-id="eaaa4-227">TBD – WS-Trust 2005/02 URI</span></span>|  
|<span data-ttu-id="eaaa4-228">wssc</span><span class="sxs-lookup"><span data-stu-id="eaaa4-228">wssc</span></span>|<span data-ttu-id="eaaa4-229">TBD – URI de 2005 do WS-SecureConversation/02</span><span class="sxs-lookup"><span data-stu-id="eaaa4-229">TBD – WS-SecureConversation 2005/02 URI</span></span>|  
|<span data-ttu-id="eaaa4-230">wsaw</span><span class="sxs-lookup"><span data-stu-id="eaaa4-230">wsaw</span></span>|<span data-ttu-id="eaaa4-231">TBD - namespace WS-Addressing de política</span><span class="sxs-lookup"><span data-stu-id="eaaa4-231">TBD - WS-Addressing policy namespace</span></span>|  
|<span data-ttu-id="eaaa4-232">wsp</span><span class="sxs-lookup"><span data-stu-id="eaaa4-232">wsp</span></span>|http://schemas.xmlsoap.org/ws/2004/09/policy|  
|<span data-ttu-id="eaaa4-233">mssp</span><span class="sxs-lookup"><span data-stu-id="eaaa4-233">mssp</span></span>|http://schemas.microsoft.com/ws/2005/07/securitypolicy|  
  
## <a name="1-token-profiles"></a><span data-ttu-id="eaaa4-234">1. Perfis de token</span><span class="sxs-lookup"><span data-stu-id="eaaa4-234">1. Token Profiles</span></span>  
 <span data-ttu-id="eaaa4-235">Especificações de segurança de serviços da Web representam credencial como tokens de segurança.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-235">Web Services Security specifications represent credential as security tokens.</span></span> <span data-ttu-id="eaaa4-236">O WCF suporta os seguintes tipos de token:</span><span class="sxs-lookup"><span data-stu-id="eaaa4-236">WCF supports the following token types:</span></span>  
  
### <a name="11-usernametoken"></a><span data-ttu-id="eaaa4-237">1.1 UsernameToken</span><span class="sxs-lookup"><span data-stu-id="eaaa4-237">1.1 UsernameToken</span></span>  
 <span data-ttu-id="eaaa4-238">WCF segue UsernameToken10 e UsernameToken11 perfis com as seguintes restrições:</span><span class="sxs-lookup"><span data-stu-id="eaaa4-238">WCF follows UsernameToken10 and UsernameToken11 profiles with the following constraints:</span></span>  
  
 <span data-ttu-id="eaaa4-239">R1101 PasswordType atributo no elemento UsernameToken\Password deve ser omitido ou tem valor #PasswordText (padrão).</span><span class="sxs-lookup"><span data-stu-id="eaaa4-239">R1101 PasswordType attribute on UsernameToken\Password element MUST be either omitted or have value #PasswordText (default).</span></span>  
  
 <span data-ttu-id="eaaa4-240">O #PasswordDigest usando a extensibilidade podem ser implementados.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-240">One can implement the #PasswordDigest using extensibility.</span></span> <span data-ttu-id="eaaa4-241">Foi observado que #PasswordDigest geralmente estava errada para ser um mecanismo de proteção de senha segura o suficiente.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-241">It has been observed that #PasswordDigest was often mistaken to be a secure enough password protection mechanism.</span></span> <span data-ttu-id="eaaa4-242">Mas #PasswordDigest não pode servir como um substituto para a criptografia de UsernameToken.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-242">But #PasswordDigest cannot serve as a substitute for encryption of the UsernameToken.</span></span> <span data-ttu-id="eaaa4-243">O objetivo principal do #PasswordDigest é a proteção contra ataques de repetição.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-243">The primary goal of #PasswordDigest is protection against replay attacks.</span></span> <span data-ttu-id="eaaa4-244">Nos modos de autenticação do WCF, ameaças de ataques de reprodução são atenuadas usando as assinaturas de mensagem.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-244">In WCF authentication modes, replay attack threats are mitigated by using message signatures.</span></span>  
  
 <span data-ttu-id="eaaa4-245">WCF B1102 nunca emite Nonce e criado subelementos UsernameToken.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-245">B1102 WCF never emits Nonce and Created sub-elements of the UsernameToken.</span></span>  
  
 <span data-ttu-id="eaaa4-246">Esses subelementos destinam-se a ajudar a detecção de reprodução.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-246">These sub-elements are intended to help replay detection.</span></span> <span data-ttu-id="eaaa4-247">Em vez disso, o WCF usa assinaturas de mensagem.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-247">WCF uses message signatures instead.</span></span>  
  
 <span data-ttu-id="eaaa4-248">OASIS WSS SOAP mensagem Security UsernameToken Profile 1.1 (UsernameToken11) introduziu a derivação de chave de recurso de senha.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-248">OASIS WSS SOAP Message Security UsernameToken Profile 1.1 (UsernameToken11) introduced key derivation from password feature.</span></span>  
  
 <span data-ttu-id="eaaa4-249">B1103 UsernameToken senha não deve ser usada para derivação de chave e, portanto, para operações criptográficas.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-249">B1103 UsernameToken password MUST not be used for key derivation and therefore for cryptographic operations.</span></span>  
  
 <span data-ttu-id="eaaa4-250">Lógica: as senhas são geralmente consideradas muito fracas para ser usado para operações de criptografia.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-250">Rationale: passwords are generally considered too weak to be used for cryptographic operations.</span></span>  
  
### <a name="12-x509-token"></a><span data-ttu-id="eaaa4-251">1.2 x 509 Token</span><span class="sxs-lookup"><span data-stu-id="eaaa4-251">1.2 X509 Token</span></span>  
 <span data-ttu-id="eaaa4-252">O WCF oferece suporte a certificados X509v3 como um tipo de credencial e segue X509TokenProfile1.0 e X509TokenProfile1.1 com as seguintes restrições:</span><span class="sxs-lookup"><span data-stu-id="eaaa4-252">WCF supports X509v3 certificates as a credential type and follows X509TokenProfile1.0 and X509TokenProfile1.1 with the following constraints:</span></span>  
  
 <span data-ttu-id="eaaa4-253">ValueType de R1201 o atributo no elemento BinarySecurityToken deve ter valor #X509v3 quando ela contém um certificado de X509v3.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-253">R1201 The ValueType attribute on the BinarySecurityToken element must have value #X509v3 when it contains an X509v3 certificate.</span></span>  
  
 <span data-ttu-id="eaaa4-254">O WSS X509 Token Profile 1.0 e 1.1 definem também X509PKIPathv1 # e #PKCS7 como tipos de valor.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-254">WSS X509 Token Profile 1.0 and 1.1 define also #X509PKIPathv1 and #PKCS7 as value types.</span></span> <span data-ttu-id="eaaa4-255">O WCF não oferece suporte a esses tipos.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-255">WCF does not support these types.</span></span>  
  
 <span data-ttu-id="eaaa4-256">R1202 se uma extensão SubjectKeyIdentifier SKI () está presente em um X509 certificado, wsse:KeyIdentifier deve ser usado para as referências externas ao token, com ValueType como #X509SubjectKeyIdentifier e seu conteúdo a codificada em base64 valor de atributo extensão de ESQUI do certificado.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-256">R1202 If a SubjectKeyIdentifier (SKI) extension is present in an X509 certificate, wsse:KeyIdentifier should be used for external references to the token, with the ValueType attribute as #X509SubjectKeyIdentifier and its content the base64-encoded value of certificate's SKI extension.</span></span>  
  
 <span data-ttu-id="eaaa4-257">Referências de ESQUI são amplamente implementadas e provou para ser um tipo de referência externa altamente interoperável.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-257">SKI references are widely implemented and proven to be a highly interoperable external reference type.</span></span>  
  
 <span data-ttu-id="eaaa4-258">R1203 Uma referência externa como X509 Security Token não deve usar ds:X509IssuerSerial.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-258">R1203 An external Reference to X509 Security Token SHOULD NOT use ds:X509IssuerSerial.</span></span>  
  
 <span data-ttu-id="eaaa4-259">R1204 X509TokenProfile1.1 de se está em uso, uma referência externa como X509 Security Token deve usar a impressão digital introduzida por WS-Security 1.1.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-259">R1204 If X509TokenProfile1.1 is in use, an external reference to X509 Security Token SHOULD use the thumbprint introduced by WS-Security 1.1.</span></span>  
  
 <span data-ttu-id="eaaa4-260">O WCF oferece suporte a X509IssuerSerial.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-260">WCF supports X509IssuerSerial.</span></span> <span data-ttu-id="eaaa4-261">No entanto, há problemas de interoperabilidade com X509IssuerSerial: WCF usa uma cadeia de caracteres para comparar dois valores de X509IssuerSerial.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-261">However There are interoperability issues with X509IssuerSerial: WCF uses a string to compare two values of X509IssuerSerial.</span></span> <span data-ttu-id="eaaa4-262">Portanto, se um reordena os componentes do nome da entidade e envia a um serviço WCF, uma referência a um certificado, ele não pode ser encontrado.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-262">Therefore if one reorders components of the Subject Name and sends to an WCF service a reference to a certificate, it may not be found.</span></span>  
  
### <a name="13-kerberos-token"></a><span data-ttu-id="eaaa4-263">1.3 Token Kerberos</span><span class="sxs-lookup"><span data-stu-id="eaaa4-263">1.3 Kerberos Token</span></span>  
 <span data-ttu-id="eaaa4-264">O WCF oferece suporte a KerberosTokenProfile1.1 para fins de autenticação do Windows com as seguintes restrições:</span><span class="sxs-lookup"><span data-stu-id="eaaa4-264">WCF supports KerberosTokenProfile1.1 for the purpose of Windows authentication with the following constraints:</span></span>  
  
 <span data-ttu-id="eaaa4-265">Token do Kerberos R1301 um necessário realizar o valor de um GSS encapsulado Kerberos v4 AP_REQ conforme definido em GSS_API e a especificação de Kerberos e deve ter o atributo com o valor #GSS_Kerberosv5_AP_REQ ValueType.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-265">R1301 A Kerberos Token must carry the value of a GSS wrapped Kerberos v4 AP_REQ as defined in GSS_API and the Kerberos specification, and must have the ValueType attribute with the value #GSS_Kerberosv5_AP_REQ.</span></span>  
  
 <span data-ttu-id="eaaa4-266">O WCF usa GSS encapsulado AP-REQ Kerberos, não um bare AP-REQ.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-266">WCF uses GSS wrapped Kerberos AP-REQ, not a bare AP-REQ.</span></span> <span data-ttu-id="eaaa4-267">Isso é uma prática recomendada de segurança.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-267">This is a security best practice.</span></span>  
  
### <a name="14-saml-v11-token"></a><span data-ttu-id="eaaa4-268">1.4 SAML v1.1 Token</span><span class="sxs-lookup"><span data-stu-id="eaaa4-268">1.4 SAML v1.1 Token</span></span>  
 <span data-ttu-id="eaaa4-269">O WCF dá suporte a perfis de Token de SAML do WSS 1.0 e 1.1 para os tokens SAML versão 1.1.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-269">WCF supports WSS SAML Token profiles 1.0 and 1.1 for SAML v1.1 tokens.</span></span> <span data-ttu-id="eaaa4-270">É possível implementar outras versões dos formatos de token SAML.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-270">It is possible to implement other versions of SAML token formats.</span></span>  
  
### <a name="15-security-context-token"></a><span data-ttu-id="eaaa4-271">1.5 Token de contexto de segurança de</span><span class="sxs-lookup"><span data-stu-id="eaaa4-271">1.5 Security Context Token</span></span>  
 <span data-ttu-id="eaaa4-272">O WCF oferece suporte a segurança contexto Token (SCT) introduzidos no WS-SecureCoversation.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-272">WCF supports the Security Context Token (SCT) introduced in WS-SecureCoversation.</span></span> <span data-ttu-id="eaaa4-273">SCT é usado para representar um contexto de segurança estabelecido em SecureConversation, bem como a negociação binária protocolos TLS e SSPI, descrito abaixo.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-273">SCT is used to represent a security context established in SecureConversation as well as the binary negotiation protocols TLS and SSPI, described below.</span></span>  
  
## <a name="2-common-message-security-parameters"></a><span data-ttu-id="eaaa4-274">2. Parâmetros comuns de segurança de mensagem</span><span class="sxs-lookup"><span data-stu-id="eaaa4-274">2. Common Message Security Parameters</span></span>  
  
### <a name="21-timestamp"></a><span data-ttu-id="eaaa4-275">2.1 carimbo de hora</span><span class="sxs-lookup"><span data-stu-id="eaaa4-275">2.1 TimeStamp</span></span>  
 <span data-ttu-id="eaaa4-276">Presença de carimbo de hora é controlada usando o <xref:System.ServiceModel.Channels.SecurityBindingElement.IncludeTimestamp%2A> propriedade do <xref:System.ServiceModel.Channels.SecurityBindingElement> classe.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-276">Timestamp presence is controlled using the <xref:System.ServiceModel.Channels.SecurityBindingElement.IncludeTimestamp%2A> property of the <xref:System.ServiceModel.Channels.SecurityBindingElement> class.</span></span> <span data-ttu-id="eaaa4-277">WCF sempre serializa wsse: timestamp com wsse: criado e wsse: campos de expirar.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-277">WCF always serializes wsse:TimeStamp with wsse:Created and wsse:Expires fields.</span></span> <span data-ttu-id="eaaa4-278">O wsse: timestamp sempre está conectado quando a assinatura é usada.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-278">The wsse:TimeStamp is always signed when signing is used.</span></span>  
  
### <a name="22-protection-order"></a><span data-ttu-id="eaaa4-279">2.2 ordem de proteção de</span><span class="sxs-lookup"><span data-stu-id="eaaa4-279">2.2 Protection Order</span></span>  
 <span data-ttu-id="eaaa4-280">O WCF oferece suporte a ordem de proteção de mensagem "Logon antes de criptografar" e "Criptografar antes de entrar" (1.1 de política de segurança).</span><span class="sxs-lookup"><span data-stu-id="eaaa4-280">WCF supports the message protection order "Sign Before Encrypt" and "Encrypt Before Sign" (Security Policy 1.1).</span></span> <span data-ttu-id="eaaa4-281">"Entrar antes de criptografar" é recomendada para motivos, incluindo: mensagens protegidas com criptografar antes de sinal são abertas a ataques de substituição de assinatura, a menos que o mecanismo de WS-Security 1.1 SignatureConfirmation é usado, e faz com que uma assinatura sobre o conteúdo criptografado a auditoria mais difícil.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-281">"Sign Before Encrypt" is recommended for reasons including: messages protected with Encrypt Before Sign are open to signature substitution attacks unless the WS-Security 1.1 SignatureConfirmation mechanism is used, and a signature over encrypted content makes auditing harder.</span></span>  
  
### <a name="23-signature-protection"></a><span data-ttu-id="eaaa4-282">2.3 proteção de assinatura</span><span class="sxs-lookup"><span data-stu-id="eaaa4-282">2.3 Signature Protection</span></span>  
 <span data-ttu-id="eaaa4-283">Ao criptografar antes de sinal é usado, é recomendável para proteger a assinatura para evitar ataques de força bruta para adivinhar o conteúdo criptografado ou a chave de assinatura (especialmente quando um token personalizado é usado com o material da chave fraca).</span><span class="sxs-lookup"><span data-stu-id="eaaa4-283">When Encrypt Before Sign is used, it is recommended to protect the signature to prevent brute force attacks for guessing the encrypted content or the signing key (especially when a custom token is used with weak key material).</span></span>  
  
### <a name="24-algorithm-suite"></a><span data-ttu-id="eaaa4-284">2.4 pacote de algoritmos</span><span class="sxs-lookup"><span data-stu-id="eaaa4-284">2.4 Algorithm Suite</span></span>  
 <span data-ttu-id="eaaa4-285">O WCF oferece suporte a todos os conjuntos de algoritmo listados na 1.1 de política de segurança.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-285">WCF supports all algorithm suites listed in Security Policy 1.1.</span></span>  
  
### <a name="25-key-derivation"></a><span data-ttu-id="eaaa4-286">2.5 derivação de chave</span><span class="sxs-lookup"><span data-stu-id="eaaa4-286">2.5 Key Derivation</span></span>  
 <span data-ttu-id="eaaa4-287">O WCF usa "Derivação de chave para chaves simétricas", conforme descrito em WS-SecureConversation.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-287">WCF uses "Key Derivation for symmetric keys" as described in WS-SecureConversation.</span></span>  
  
### <a name="26-signature-confirmation"></a><span data-ttu-id="eaaa4-288">2.6 confirmação de assinatura</span><span class="sxs-lookup"><span data-stu-id="eaaa4-288">2.6 Signature Confirmation</span></span>  
 <span data-ttu-id="eaaa4-289">Confirmação de assinatura pode ser como proteção contra ataques man intermediária para proteger o conjunto de assinaturas.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-289">Signature confirmation can be as protection from middle man attacks to protect the set of signatures.</span></span>  
  
### <a name="27-security-header-layout"></a><span data-ttu-id="eaaa4-290">2.7 Layout de cabeçalho de segurança</span><span class="sxs-lookup"><span data-stu-id="eaaa4-290">2.7 Security Header Layout</span></span>  
 <span data-ttu-id="eaaa4-291">Cada modo de autenticação descreve um determinado layout para o cabeçalho de segurança.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-291">Each authentication mode describes a certain layout for the security header.</span></span> <span data-ttu-id="eaaa4-292">Os elementos dentro do cabeçalho de segurança são semi-estruturados ordenados.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-292">Elements within the security header are semi-ordered.</span></span> <span data-ttu-id="eaaa4-293">Para definir a ordem dos elementos de filho de cabeçalho de segurança, WS-Security Policy define os seguintes modos de layout de cabeçalho de segurança:</span><span class="sxs-lookup"><span data-stu-id="eaaa4-293">To define the order of security header child elements, WS-Security Policy defines the following security header layout modes:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="eaaa4-294">Estrito</span><span class="sxs-lookup"><span data-stu-id="eaaa4-294">Strict</span></span>|<span data-ttu-id="eaaa4-295">Itens são adicionados para o seguinte cabeçalho de segurança, que as regras de layout numerada descrito na seção 7.7.1 acordo com um geral de política de segurança princípio de "declarar antes do uso".</span><span class="sxs-lookup"><span data-stu-id="eaaa4-295">Items are added to the security header following the numbered layout rules described in Security Policy section 7.7.1 according to a general principle of "declare before use".</span></span>|  
|<span data-ttu-id="eaaa4-296">Incerto</span><span class="sxs-lookup"><span data-stu-id="eaaa4-296">Lax</span></span>|<span data-ttu-id="eaaa4-297">Itens são adicionados ao cabeçalho de segurança em qualquer ordem que está de acordo com o WSS: segurança de mensagem SOAP.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-297">Items are added to the security header in any order that conforms to WSS: SOAP Message Security.</span></span>|  
|<span data-ttu-id="eaaa4-298">LaxTimestampFirst</span><span class="sxs-lookup"><span data-stu-id="eaaa4-298">LaxTimestampFirst</span></span>|<span data-ttu-id="eaaa4-299">Mesmo como Lax, exceto que o primeiro item no cabeçalho de segurança deve ser um wsse: timestamp</span><span class="sxs-lookup"><span data-stu-id="eaaa4-299">Same as Lax except that the first item in the security header must be a wsse:Timestamp</span></span>|  
|<span data-ttu-id="eaaa4-300">LaxTimestampLast</span><span class="sxs-lookup"><span data-stu-id="eaaa4-300">LaxTimestampLast</span></span>|<span data-ttu-id="eaaa4-301">Mesmo que incerto, exceto pelo fato de que o último item no cabeçalho de segurança deve ser um wsse: timestamp</span><span class="sxs-lookup"><span data-stu-id="eaaa4-301">Same as lax except that the last item in the security header must be a wsse:Timestamp</span></span>|  
  
 <span data-ttu-id="eaaa4-302">WCF dá suporte a todos os quatro modos de layout de cabeçalho de segurança.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-302">WCF supports all four modes for security header layout.</span></span> <span data-ttu-id="eaaa4-303">Exemplos de estrutura e a mensagem de cabeçalho de segurança para os modos de autenticação abaixo siga o modo "Estrito".</span><span class="sxs-lookup"><span data-stu-id="eaaa4-303">Security header structure and message examples for authentication modes below follow the "Strict" mode.</span></span>  
  
## <a name="2-common-message-security-parameters"></a><span data-ttu-id="eaaa4-304">2. Parâmetros comuns de segurança de mensagem</span><span class="sxs-lookup"><span data-stu-id="eaaa4-304">2. Common Message Security Parameters</span></span>  
 <span data-ttu-id="eaaa4-305">Esta seção fornece exemplos de políticas para cada modo de autenticação junto com exemplos que mostram a estrutura de cabeçalho de segurança em mensagens trocadas por cliente e o serviço.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-305">This section provides example policies for each authentication mode along with examples showing security header structure in messages exchanged by client and service.</span></span>  
  
### <a name="61-transport-protection"></a><span data-ttu-id="eaaa4-306">6.1 proteção de transporte</span><span class="sxs-lookup"><span data-stu-id="eaaa4-306">6.1 Transport Protection</span></span>  
 <span data-ttu-id="eaaa4-307">O WCF fornece cinco modos de autenticação que usam o transporte seguro para proteger as mensagens; UserNameOverTransport, CertificateOverTransport, KerberosOverTransport, IssuedTokenOverTransport e SspiNegotiatedOverTransport.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-307">WCF provides five authentication modes that use secure transport to protect messages; UserNameOverTransport, CertificateOverTransport, KerberosOverTransport, IssuedTokenOverTransport and SspiNegotiatedOverTransport.</span></span>  
  
 <span data-ttu-id="eaaa4-308">Esses modos de autenticação são construídos usando a associação de transporte descrita SecurityPolicy.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-308">These authentication modes are constructed using the transport binding described in SecurityPolicy.</span></span> <span data-ttu-id="eaaa4-309">Para o UserNameOverTransport UsernameToken do modo de autenticação é um token de suporte com sinal.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-309">For the UserNameOverTransport authentication mode the UsernameToken is a signed supporting token.</span></span> <span data-ttu-id="eaaa4-310">Para outros modos de autenticação o token será exibido como um token de endosso assinado.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-310">For the other authentication modes the token appears as a signed endorsing token.</span></span> <span data-ttu-id="eaaa4-311">Apêndice C.1.2 e C.1.3 de SecurityPolicy descrevem o layout do cabeçalho de segurança em detalhes.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-311">Appendix C.1.2 and C.1.3 of SecurityPolicy describe the security header layout in detail.</span></span> <span data-ttu-id="eaaa4-312">Os cabeçalhos de segurança de exemplo a seguir mostram o layout estrito para um modo de autenticação específico.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-312">The following example security headers show the Strict layout for a given authentication mode.</span></span>  
  
 <span data-ttu-id="eaaa4-313">O valor da propriedade "Chaves derivadas" para os tokens em todos os casos é "false".</span><span class="sxs-lookup"><span data-stu-id="eaaa4-313">The value of the "Derived Keys" property for the tokens in all cases is "false".</span></span>  
  
 <span data-ttu-id="eaaa4-314">Os valores de várias propriedades da associação de transporte são da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="eaaa4-314">The values of the various properties of the transport binding are as follows:</span></span>  
  
 <span data-ttu-id="eaaa4-315">Carimbo de hora: true</span><span class="sxs-lookup"><span data-stu-id="eaaa4-315">Timestamp: true</span></span>  
  
 <span data-ttu-id="eaaa4-316">Layout de cabeçalho de segurança: Strict</span><span class="sxs-lookup"><span data-stu-id="eaaa4-316">Security Header Layout: Strict</span></span>  
  
 <span data-ttu-id="eaaa4-317">Pacote de algoritmos: Basic256</span><span class="sxs-lookup"><span data-stu-id="eaaa4-317">Algorithm Suite: Basic256</span></span>  
  
#### <a name="611-usernameovertransport"></a><span data-ttu-id="eaaa4-318">6.1.1 UsernameOverTransport</span><span class="sxs-lookup"><span data-stu-id="eaaa4-318">6.1.1 UsernameOverTransport</span></span>  
 <span data-ttu-id="eaaa4-319">Com esse modo de autenticação, o cliente autentica com um Token de nome de usuário que aparece na camada de SOAP como um token de suporte com sinal que é sempre enviado do iniciador para o destinatário.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-319">With this authentication mode, the client authenticates with a Username Token which appears at the SOAP layer as a signed supporting token that is always sent from the initiator to the recipient.</span></span> <span data-ttu-id="eaaa4-320">O serviço é autenticado usando um certificado X.509 na camada de transporte.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-320">The service is authenticated using an X.509 certificate at the transport layer.</span></span> <span data-ttu-id="eaaa4-321">A associação usada é uma associação de transporte.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-321">The binding used is a transport binding.</span></span>  
  
 <span data-ttu-id="eaaa4-322">Política</span><span class="sxs-lookup"><span data-stu-id="eaaa4-322">Policy</span></span>  
  
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
  
 <span data-ttu-id="eaaa4-323">Layout de cabeçalho de segurança</span><span class="sxs-lookup"><span data-stu-id="eaaa4-323">Security Header Layout</span></span>  
  
 <span data-ttu-id="eaaa4-324">Solicitação</span><span class="sxs-lookup"><span data-stu-id="eaaa4-324">Request</span></span>  
  
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
  
 <span data-ttu-id="eaaa4-325">Resposta</span><span class="sxs-lookup"><span data-stu-id="eaaa4-325">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
#### <a name="612-certificateovertransport"></a><span data-ttu-id="eaaa4-326">6.1.2 CertificateOverTransport</span><span class="sxs-lookup"><span data-stu-id="eaaa4-326">6.1.2 CertificateOverTransport</span></span>  
 <span data-ttu-id="eaaa4-327">Com esse modo de autenticação que o cliente é autenticado usando um X.509 do certificado que aparece na camada de SOAP como um token de suporte de endosso que é sempre enviado do iniciador para o destinatário.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-327">With this authentication mode the client authenticates using an X.509 certificate which appears at the SOAP layer as an endorsing supporting token that is always sent from the initiator to the recipient.</span></span> <span data-ttu-id="eaaa4-328">O serviço é autenticado usando um certificado X.509 na camada de transporte.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-328">The service is authenticated using an X.509 certificate at the transport layer.</span></span> <span data-ttu-id="eaaa4-329">A associação usada é uma associação de transporte.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-329">The binding used is a transport binding.</span></span>  
  
 <span data-ttu-id="eaaa4-330">Política</span><span class="sxs-lookup"><span data-stu-id="eaaa4-330">Policy</span></span>  
  
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
  
 <span data-ttu-id="eaaa4-331">Layout de cabeçalho de segurança</span><span class="sxs-lookup"><span data-stu-id="eaaa4-331">Security Header Layout</span></span>  
  
 <span data-ttu-id="eaaa4-332">Solicitação</span><span class="sxs-lookup"><span data-stu-id="eaaa4-332">Request</span></span>  
  
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
  
 <span data-ttu-id="eaaa4-333">Resposta</span><span class="sxs-lookup"><span data-stu-id="eaaa4-333">Response</span></span>  
  
```xml  
<o:Security>  
  <u:Timestamp u:Id="_0">  
  ...  
  </u:Timestamp>  
</o:Security>  
```  
  
#### <a name="613-issuedtokenovertransport"></a><span data-ttu-id="eaaa4-334">6.1.3 IssuedTokenOverTransport</span><span class="sxs-lookup"><span data-stu-id="eaaa4-334">6.1.3 IssuedTokenOverTransport</span></span>  
 <span data-ttu-id="eaaa4-335">Com esse modo de autenticação o cliente não se autenticar no serviço, como tal, mas em vez disso, apresenta um token emitido por um Security Token Service (STS) e comprova o conhecimento de uma chave compartilhada.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-335">With this authentication mode the client does not authenticate to the service, as such, but rather presents a token issued by a Security Token Service (STS) and proves knowledge of a shared key.</span></span> <span data-ttu-id="eaaa4-336">O token emitido é exibido na camada de SOAP como um token de suporte de endosso que é sempre enviado do iniciador para o destinatário.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-336">The issued token appears at the SOAP layer as an endorsing supporting token that is always sent from the initiator to the recipient.</span></span> <span data-ttu-id="eaaa4-337">O serviço é autenticado usando um certificado X.509 na camada de transporte.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-337">The service is authenticated using an X.509 certificate at the transport layer.</span></span> <span data-ttu-id="eaaa4-338">A associação é uma associação de transporte.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-338">The binding is a transport binding.</span></span>  
  
 <span data-ttu-id="eaaa4-339">Política</span><span class="sxs-lookup"><span data-stu-id="eaaa4-339">Policy</span></span>  
  
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
  
 <span data-ttu-id="eaaa4-340">Layout de cabeçalho de segurança</span><span class="sxs-lookup"><span data-stu-id="eaaa4-340">Security Header Layout</span></span>  
  
 <span data-ttu-id="eaaa4-341">Solicitação</span><span class="sxs-lookup"><span data-stu-id="eaaa4-341">Request</span></span>  
  
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
  
 <span data-ttu-id="eaaa4-342">Resposta</span><span class="sxs-lookup"><span data-stu-id="eaaa4-342">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
#### <a name="614-kerberosovertransport"></a><span data-ttu-id="eaaa4-343">6.1.4 KerberosOverTransport</span><span class="sxs-lookup"><span data-stu-id="eaaa4-343">6.1.4 KerberosOverTransport</span></span>  
 <span data-ttu-id="eaaa4-344">Com esse modo de autenticação o cliente é autenticado para o serviço usando um tíquete Kerberos.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-344">With this authentication mode the client authenticates to the service using a Kerberos ticket.</span></span> <span data-ttu-id="eaaa4-345">O token Kerberos é exibido na camada de SOAP como um token de suporte de endosso.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-345">The Kerberos token appears at the SOAP layer as an endorsing supporting token.</span></span> <span data-ttu-id="eaaa4-346">O serviço é autenticado usando um certificado X.509 na camada de transporte.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-346">The service is authenticated using an X.509 certificate at the transport layer.</span></span> <span data-ttu-id="eaaa4-347">A associação é uma associação de transporte.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-347">The binding is a transport binding.</span></span>  
  
 <span data-ttu-id="eaaa4-348">Política</span><span class="sxs-lookup"><span data-stu-id="eaaa4-348">Policy</span></span>  
  
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
  
 <span data-ttu-id="eaaa4-349">Layout de cabeçalho de segurança</span><span class="sxs-lookup"><span data-stu-id="eaaa4-349">Security Header Layout</span></span>  
  
 <span data-ttu-id="eaaa4-350">Solicitação</span><span class="sxs-lookup"><span data-stu-id="eaaa4-350">Request</span></span>  
  
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
  
 <span data-ttu-id="eaaa4-351">Resposta</span><span class="sxs-lookup"><span data-stu-id="eaaa4-351">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
#### <a name="615-sspinegotiatedovertransport"></a><span data-ttu-id="eaaa4-352">6.1.5 SspiNegotiatedOverTransport</span><span class="sxs-lookup"><span data-stu-id="eaaa4-352">6.1.5 SspiNegotiatedOverTransport</span></span>  
 <span data-ttu-id="eaaa4-353">Com esse modo, um protocolo de negociação é usado para realizar a autenticação de cliente e servidor.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-353">With this mode a negotiation protocol is used to perform client and server authentication.</span></span> <span data-ttu-id="eaaa4-354">Kerberos é usado, se possível, caso contrário, NTLM.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-354">Kerberos is used if possible, otherwise NTLM.</span></span> <span data-ttu-id="eaaa4-355">O SCT resultante aparece na camada de SOAP como um token de suporte de endosso que é sempre enviado do iniciador ao destinatário.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-355">The resulting SCT appears at the SOAP layer as an endorsing supporting token that is always sent from initiator to recipient.</span></span> <span data-ttu-id="eaaa4-356">Além disso, o serviço é autenticado na camada de transporte por um certificado X.509.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-356">The service is additionally authenticated at the transport layer by an X.509 certificate.</span></span> <span data-ttu-id="eaaa4-357">A associação usada é uma associação de transporte.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-357">The binding used is a transport binding.</span></span> <span data-ttu-id="eaaa4-358">"SPNEGO" (negociação) descreve como o WCF usa o protocolo de negociação binária de SSPI com o WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-358">"SPNEGO" (negotiation) describes how WCF uses SSPI binary negotiation protocol with WS-Trust.</span></span> <span data-ttu-id="eaaa4-359">Exemplos de cabeçalho de segurança nesta seção são depois SCT tiver sido estabelecido por meio de handshake de SPNEGO.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-359">Security header examples in this section are after the SCT has been established through the SPNEGO handshake.</span></span>  
  
 <span data-ttu-id="eaaa4-360">Política</span><span class="sxs-lookup"><span data-stu-id="eaaa4-360">Policy</span></span>  
  
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
  
### <a name="security-header-examples"></a><span data-ttu-id="eaaa4-361">Exemplos de cabeçalho de segurança</span><span class="sxs-lookup"><span data-stu-id="eaaa4-361">Security Header Examples</span></span>  
 <span data-ttu-id="eaaa4-362">Quando o Token de contexto de segurança é estabelecido por meio do handshake SPNEGO usando WS-Trust a negociação binária, as mensagens de aplicativo têm cabeçalhos de segurança com a seguinte estrutura.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-362">Once the Security Context Token is established through SPNEGO handshake using WS-Trust Binary Negotiation, the application messages have security headers with the following structure.</span></span>  
  
 <span data-ttu-id="eaaa4-363">Solicitação</span><span class="sxs-lookup"><span data-stu-id="eaaa4-363">Request</span></span>  
  
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
  
 <span data-ttu-id="eaaa4-364">Resposta</span><span class="sxs-lookup"><span data-stu-id="eaaa4-364">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
### <a name="62-using-x509-certificates-for-service-authentication"></a><span data-ttu-id="eaaa4-365">6.2 usando certificados X.509 para autenticação de serviço</span><span class="sxs-lookup"><span data-stu-id="eaaa4-365">6.2 Using X.509 Certificates for Service Authentication</span></span>  
 <span data-ttu-id="eaaa4-366">Esta seção descreve os seguintes modos de autenticação: MutualCertificate WSS1.0, CertificateDuplex mútua, MutualCertificate WSS1.1, AnonymousForCertificate, UserNameForCertificate e IssuedTokenForCertificate.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-366">This section describes the following authentication modes: MutualCertificate WSS1.0, Mutual CertificateDuplex, MutualCertificate WSS1.1, AnonymousForCertificate, UserNameForCertificate and IssuedTokenForCertificate.</span></span>  
  
#### <a name="621-mutualcertificate-wss10"></a><span data-ttu-id="eaaa4-367">6.2.1 MutualCertificate WSS1.0</span><span class="sxs-lookup"><span data-stu-id="eaaa4-367">6.2.1 MutualCertificate WSS1.0</span></span>  
 <span data-ttu-id="eaaa4-368">Com esse modo de autenticação que o cliente é autenticado usando um X.509 do certificado que aparece na camada de SOAP que o token de iniciador.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-368">With this authentication mode the client authenticates using an X.509 certificate which appears at the SOAP layer as the initiator token.</span></span> <span data-ttu-id="eaaa4-369">O serviço também é autenticado usando um certificado X.509.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-369">The service is also authenticated using an X.509 certificate.</span></span>  
  
 <span data-ttu-id="eaaa4-370">A associação usada é uma associação assimétrica com os seguintes valores de propriedade:</span><span class="sxs-lookup"><span data-stu-id="eaaa4-370">The binding used is an asymmetric binding with the following property values:</span></span>  
  
 <span data-ttu-id="eaaa4-371">Token de iniciador: o certificado do cliente x. 509, com o modo de inclusão definido como .../IncludeToken/AlwaysToRecipient</span><span class="sxs-lookup"><span data-stu-id="eaaa4-371">Initiator Token: the client’s X.509 certificate, with inclusion mode set to …/IncludeToken/AlwaysToRecipient</span></span>  
  
 <span data-ttu-id="eaaa4-372">Token de destinatário: O servidor do certificado x. 509, com o modo de inclusão é definido .../IncludeToken/Never</span><span class="sxs-lookup"><span data-stu-id="eaaa4-372">Recipient Token: Server’s X.509 Certificate, with inclusion mode is set …/IncludeToken/Never</span></span>  
  
 <span data-ttu-id="eaaa4-373">Proteção de token: False</span><span class="sxs-lookup"><span data-stu-id="eaaa4-373">Token Protection: False</span></span>  
  
 <span data-ttu-id="eaaa4-374">Todo o cabeçalho e corpo assinaturas: True</span><span class="sxs-lookup"><span data-stu-id="eaaa4-374">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="eaaa4-375">Ordem de proteção: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="eaaa4-375">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="eaaa4-376">Criptografar assinatura: True</span><span class="sxs-lookup"><span data-stu-id="eaaa4-376">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="eaaa4-377">Política</span><span class="sxs-lookup"><span data-stu-id="eaaa4-377">Policy</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="eaaa4-378">Exemplos de cabeçalho de segurança: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="eaaa4-378">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="eaaa4-379">Solicitação</span><span class="sxs-lookup"><span data-stu-id="eaaa4-379">Request</span></span>  
  
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
  
 <span data-ttu-id="eaaa4-380">Resposta</span><span class="sxs-lookup"><span data-stu-id="eaaa4-380">Response</span></span>  
  
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
  
 <span data-ttu-id="eaaa4-381">Exemplos de cabeçalho de segurança: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="eaaa4-381">Security Header Examples: EncryptBeforeSign</span></span>  
  
 <span data-ttu-id="eaaa4-382">Solicitação</span><span class="sxs-lookup"><span data-stu-id="eaaa4-382">Request</span></span>  
  
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
  
 <span data-ttu-id="eaaa4-383">Resposta</span><span class="sxs-lookup"><span data-stu-id="eaaa4-383">Response</span></span>  
  
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
  
#### <a name="622-mutualcertificateduplex"></a><span data-ttu-id="eaaa4-384">6.2.2 MutualCertificateDuplex</span><span class="sxs-lookup"><span data-stu-id="eaaa4-384">6.2.2 MutualCertificateDuplex</span></span>  
 <span data-ttu-id="eaaa4-385">Com esse modo de autenticação que o cliente é autenticado usando um X.509 do certificado que aparece na camada de SOAP que o token de iniciador.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-385">With this authentication mode the client authenticates using an X.509 certificate which appears at the SOAP layer as the initiator token.</span></span> <span data-ttu-id="eaaa4-386">O serviço também é autenticado usando um certificado X.509.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-386">The service is also authenticated using an X.509 certificate.</span></span>  
  
 <span data-ttu-id="eaaa4-387">A associação usada é uma associação assimétrica com os seguintes valores de propriedade:</span><span class="sxs-lookup"><span data-stu-id="eaaa4-387">The binding used is an asymmetric binding with the following property values:</span></span>  
  
 <span data-ttu-id="eaaa4-388">Token de iniciador: X509 do cliente certificado, o modo de inclusão é definido como .../IncludeToken/AlwaysToRecipient</span><span class="sxs-lookup"><span data-stu-id="eaaa4-388">Initiator Token: Client’s X509 Certificate, inclusion mode is set to …/IncludeToken/AlwaysToRecipient</span></span>  
  
 <span data-ttu-id="eaaa4-389">Token de destinatário: X509 do servidor certificado, o modo de inclusão é definido como .../IncludeToken/AlwaysToInitiator</span><span class="sxs-lookup"><span data-stu-id="eaaa4-389">Recipient Token: Server’s X509 Certificate, inclusion mode is set to …/IncludeToken/AlwaysToInitiator</span></span>  
  
 <span data-ttu-id="eaaa4-390">Proteção de token: False</span><span class="sxs-lookup"><span data-stu-id="eaaa4-390">Token Protection: False</span></span>  
  
 <span data-ttu-id="eaaa4-391">Todo o cabeçalho e corpo assinaturas: True</span><span class="sxs-lookup"><span data-stu-id="eaaa4-391">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="eaaa4-392">Ordem de proteção: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="eaaa4-392">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="eaaa4-393">Criptografar assinatura: True</span><span class="sxs-lookup"><span data-stu-id="eaaa4-393">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="eaaa4-394">Política</span><span class="sxs-lookup"><span data-stu-id="eaaa4-394">Policy</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="eaaa4-395">Exemplos de cabeçalho de segurança: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="eaaa4-395">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="eaaa4-396">Solicitação e resposta</span><span class="sxs-lookup"><span data-stu-id="eaaa4-396">Request and Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="eaaa4-397">Exemplos de cabeçalho de segurança: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="eaaa4-397">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="eaaa4-398">Solicitação e resposta</span><span class="sxs-lookup"><span data-stu-id="eaaa4-398">Request and Response</span></span>  
  
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
  
#### <a name="623-using-symmetricbinding-with-x509-service-authentication"></a><span data-ttu-id="eaaa4-399">6.2.3 usando SymmetricBinding com autenticação do serviço de x. 509</span><span class="sxs-lookup"><span data-stu-id="eaaa4-399">6.2.3 Using SymmetricBinding with X.509 Service Authentication</span></span>  
 <span data-ttu-id="eaaa4-400">"WSS10" fornecido suporte limitado para cenários com X509 tokens.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-400">"WSS10" provided limited support for scenarios with X509 tokens.</span></span> <span data-ttu-id="eaaa4-401">Por exemplo, não houve nenhuma maneira de fornecer proteção de assinatura e criptografia de mensagens usando apenas o token de serviço X509.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-401">For example, there was no way to provide signature and encryption protection for messages using only service X509 token.</span></span> <span data-ttu-id="eaaa4-402">"WSS11" introduziu o uso de EncryptedKey como um token simétrico.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-402">"WSS11" introduced the usage of EncryptedKey as a symmetric token.</span></span> <span data-ttu-id="eaaa4-403">Agora, uma chave temporária criptografada para o certificado do serviço x. 509 poderia ser usada para a proteção de mensagens de solicitação e resposta.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-403">Now a temporary key encrypted for the service's X.509 certificate could be used for both request and response messages protection.</span></span> <span data-ttu-id="eaaa4-404">Os modos de autenticação descritos na seção 6.4 abaixo usam esse padrão.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-404">The authentication modes described in the section 6.4 below use this pattern.</span></span>  
  
 <span data-ttu-id="eaaa4-405">O WS-SecurityPolicy descreve esse padrão usando SymmetricBinding com o serviço de token X509 que o token de proteção.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-405">WS-SecurityPolicy describes this pattern using SymmetricBinding with Service X509 token as the protection token.</span></span>  
  
 <span data-ttu-id="eaaa4-406">Modos de autenticação AnonymousForCertificate, UsernameForCertificate, MutualCertificate WSS11 e IssuedTokenForCertificate todos usam uma instância similar do sp:SymmetricBinding com os seguintes valores de propriedade:</span><span class="sxs-lookup"><span data-stu-id="eaaa4-406">Authentication modes AnonymousForCertificate, UsernameForCertificate, MutualCertificate WSS11 and IssuedTokenForCertificate all use a similar instance of sp:SymmetricBinding with the following property values:</span></span>  
  
 <span data-ttu-id="eaaa4-407">Token de proteção: X509 do servidor certificado, o modo de inclusão é definido como .../IncludeToken/Never</span><span class="sxs-lookup"><span data-stu-id="eaaa4-407">Protection Token: Server’s X509 Certificate, inclusion mode is set to .../IncludeToken/Never</span></span>  
<span data-ttu-id="eaaa4-408">Proteção de token: False</span><span class="sxs-lookup"><span data-stu-id="eaaa4-408">Token Protection: False</span></span>  
  
 <span data-ttu-id="eaaa4-409">Todo o cabeçalho e corpo assinaturas: True</span><span class="sxs-lookup"><span data-stu-id="eaaa4-409">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="eaaa4-410">Ordem de proteção: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="eaaa4-410">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="eaaa4-411">Criptografar assinatura: True</span><span class="sxs-lookup"><span data-stu-id="eaaa4-411">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="eaaa4-412">Os modos de autenticação acima diferem somente por tokens de suporte que eles usam.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-412">The above authentication modes only differ by the supporting tokens they use.</span></span> <span data-ttu-id="eaaa4-413">AnonymousForCertificate não tem quaisquer tokens de suporte, MutualCertificate WSS 1.1 tem o cliente como um endosso que dão suporte a tokens de certificados X509, UserNameForCertificate tem um Token de nome de usuário como um token de suporte assinado e IssuedTokenForCertificate tem o token emitido como um token de suporte de endosso.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-413">AnonymousForCertificate does not have any supporting tokens, MutualCertificate WSS 1.1 has the client’s X509 certificate as an endorsing supporting tokens, UserNameForCertificate has a UserName Token as a signed supporting token and IssuedTokenForCertificate has the issued token as an endorsing supporting token.</span></span>  
  
 <span data-ttu-id="eaaa4-414">Política</span><span class="sxs-lookup"><span data-stu-id="eaaa4-414">Policy</span></span>  
  
 <span data-ttu-id="eaaa4-415">Associação simétrica</span><span class="sxs-lookup"><span data-stu-id="eaaa4-415">Symmetric Binding</span></span>  
  
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
  
#### <a name="624-anonymousforcertificate"></a><span data-ttu-id="eaaa4-416">6.2.4 AnonymousForCertificate</span><span class="sxs-lookup"><span data-stu-id="eaaa4-416">6.2.4 AnonymousForCertificate</span></span>  
 <span data-ttu-id="eaaa4-417">Com esse modo de autenticação, o cliente é anônimo e o serviço é autenticado usando um certificado X.509.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-417">With this authentication mode the client is anonymous and the service is authenticated using an X.509 certificate.</span></span> <span data-ttu-id="eaaa4-418">A associação usada é uma instância de associação simétrica, conforme descrito em 6.4.2.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-418">The binding used is an instance of symmetric binding as described in 6.4.2.</span></span>  
  
 <span data-ttu-id="eaaa4-419">Política</span><span class="sxs-lookup"><span data-stu-id="eaaa4-419">Policy</span></span>  
  
 <span data-ttu-id="eaaa4-420">Consulte "Política" 6.2.3 acima para obter detalhes de associação</span><span class="sxs-lookup"><span data-stu-id="eaaa4-420">See "Policy" in 6.2.3 above for binding details</span></span>  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="eaaa4-421">Exemplos de cabeçalho de segurança: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="eaaa4-421">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="eaaa4-422">Solicitação</span><span class="sxs-lookup"><span data-stu-id="eaaa4-422">Request</span></span>  
  
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
  
 <span data-ttu-id="eaaa4-423">Resposta</span><span class="sxs-lookup"><span data-stu-id="eaaa4-423">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="eaaa4-424">Exemplos de cabeçalho de segurança: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="eaaa4-424">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="eaaa4-425">Solicitação</span><span class="sxs-lookup"><span data-stu-id="eaaa4-425">Request</span></span>  
  
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
  
 <span data-ttu-id="eaaa4-426">Resposta</span><span class="sxs-lookup"><span data-stu-id="eaaa4-426">Response</span></span>  
  
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
  
#### <a name="625-usernameforcertificate"></a><span data-ttu-id="eaaa4-427">6.2.5 UserNameForCertificate</span><span class="sxs-lookup"><span data-stu-id="eaaa4-427">6.2.5 UserNameForCertificate</span></span>  
 <span data-ttu-id="eaaa4-428">Com esse modo de autenticação o cliente é autenticado para o serviço usando um Token de nome de usuário que aparece na camada de SOAP como um token de suporte com sinal.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-428">With this authentication mode the client authenticates to the service using a Username Token which appears at the SOAP layer as a signed supporting token.</span></span> <span data-ttu-id="eaaa4-429">O serviço autentica para o cliente usando um certificado X.509.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-429">The service authenticates to the client using an X.509 certificate.</span></span> <span data-ttu-id="eaaa4-430">A associação usada é uma associação simétrica com o token de proteção sendo uma chave gerada pelo cliente, criptografado com a chave pública do serviço.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-430">The binding used is a symmetric binding with the protection token being a key generated by the client, encrypted with the public key of the service.</span></span>  
  
 <span data-ttu-id="eaaa4-431">Política</span><span class="sxs-lookup"><span data-stu-id="eaaa4-431">Policy</span></span>  
  
 <span data-ttu-id="eaaa4-432">Consulte "Política" 6.2.3 acima para obter detalhes de associação</span><span class="sxs-lookup"><span data-stu-id="eaaa4-432">See "Policy" in 6.2.3 above for binding details</span></span>  
  
 <span data-ttu-id="eaaa4-433">Assinado um Token de suporte</span><span class="sxs-lookup"><span data-stu-id="eaaa4-433">Signed Supporting Token</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="eaaa4-434">Exemplos de cabeçalho de segurança: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="eaaa4-434">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="eaaa4-435">Solicitação</span><span class="sxs-lookup"><span data-stu-id="eaaa4-435">Request</span></span>  
  
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
  
 <span data-ttu-id="eaaa4-436">Resposta</span><span class="sxs-lookup"><span data-stu-id="eaaa4-436">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="eaaa4-437">Exemplos de cabeçalho de segurança: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="eaaa4-437">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="eaaa4-438">Solicitação</span><span class="sxs-lookup"><span data-stu-id="eaaa4-438">Request</span></span>  
  
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
  
 <span data-ttu-id="eaaa4-439">Resposta</span><span class="sxs-lookup"><span data-stu-id="eaaa4-439">Response</span></span>  
  
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
  
#### <a name="626-mutualcertificate-wss-11"></a><span data-ttu-id="eaaa4-440">6.2.6 MutualCertificate (WSS 1.1)</span><span class="sxs-lookup"><span data-stu-id="eaaa4-440">6.2.6 MutualCertificate (WSS 1.1)</span></span>  
 <span data-ttu-id="eaaa4-441">Com esse modo de autenticação que o cliente é autenticado usando um X.509 do certificado que aparece na camada de SOAP como um token de suporte de endosso.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-441">With this authentication mode the client authenticates using an X.509 certificate which appears at the SOAP layer as an endorsing supporting token.</span></span> <span data-ttu-id="eaaa4-442">O serviço também é autenticado usando um certificado X.509.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-442">The service is also authenticated using an X.509 certificate.</span></span> <span data-ttu-id="eaaa4-443">A associação usada é uma associação simétrica com o token de proteção sendo uma chave gerada pelo cliente, criptografado com a chave pública do serviço.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-443">The binding used is a symmetric binding with the protection token being a key generated by the client, encrypted with the public key of the service.</span></span>  
  
 <span data-ttu-id="eaaa4-444">Política</span><span class="sxs-lookup"><span data-stu-id="eaaa4-444">Policy</span></span>  
  
 <span data-ttu-id="eaaa4-445">Consulte a política em 6.2.3 para obter detalhes de associação</span><span class="sxs-lookup"><span data-stu-id="eaaa4-445">See Policy in 6.2.3 for binding details</span></span>  
  
 <span data-ttu-id="eaaa4-446">Token de suporte de endosso</span><span class="sxs-lookup"><span data-stu-id="eaaa4-446">Endorsing Supporting Token</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="eaaa4-447">Exemplos de cabeçalho de segurança: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="eaaa4-447">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="eaaa4-448">Solicitação</span><span class="sxs-lookup"><span data-stu-id="eaaa4-448">Request</span></span>  
  
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
  
 <span data-ttu-id="eaaa4-449">Resposta</span><span class="sxs-lookup"><span data-stu-id="eaaa4-449">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="eaaa4-450">Exemplos de cabeçalho de segurança: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="eaaa4-450">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="eaaa4-451">Solicitação</span><span class="sxs-lookup"><span data-stu-id="eaaa4-451">Request</span></span>  
  
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
  
 <span data-ttu-id="eaaa4-452">Resposta</span><span class="sxs-lookup"><span data-stu-id="eaaa4-452">Response</span></span>  
  
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
  
#### <a name="627-issuedtokenforcertificate"></a><span data-ttu-id="eaaa4-453">6.2.7 IssuedTokenForCertificate</span><span class="sxs-lookup"><span data-stu-id="eaaa4-453">6.2.7 IssuedTokenForCertificate</span></span>  
 <span data-ttu-id="eaaa4-454">Com essa autenticação modo que o cliente não se autenticar no serviço, como tal, mas em vez disso, apresenta um token emitido por um STS e comprova o conhecimento de uma chave compartilhada.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-454">With this authentication mode the client does not authenticate to the service, as such, but instead presents a token issued by a STS and proves knowledge of a shared key.</span></span> <span data-ttu-id="eaaa4-455">O token emitido é exibido na camada de SOAP como um token de suporte de endosso.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-455">The issued token appears at the SOAP layer as an endorsing supporting token.</span></span> <span data-ttu-id="eaaa4-456">O serviço autentica para o cliente usando um certificado X.509.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-456">The service authenticates to the client using an X.509 certificate.</span></span> <span data-ttu-id="eaaa4-457">A associação usada é uma associação simétrica com o token de proteção sendo uma chave gerada pelo cliente, criptografado com a chave pública do serviço.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-457">The binding used is a symmetric binding with the protection token being a key generated by the client, encrypted with the public key of the service.</span></span>  
  
 <span data-ttu-id="eaaa4-458">Política</span><span class="sxs-lookup"><span data-stu-id="eaaa4-458">Policy</span></span>  
  
 <span data-ttu-id="eaaa4-459">Consulte a política em 6.2.3 acima para obter detalhes de associação</span><span class="sxs-lookup"><span data-stu-id="eaaa4-459">See Policy in 6.2.3 above for binding details</span></span>  
  
 <span data-ttu-id="eaaa4-460">Token de suporte de endosso</span><span class="sxs-lookup"><span data-stu-id="eaaa4-460">Endorsing Supporting Token</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="eaaa4-461">Exemplos de cabeçalho de segurança: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="eaaa4-461">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="eaaa4-462">Solicitação</span><span class="sxs-lookup"><span data-stu-id="eaaa4-462">Request</span></span>  
  
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
  
 <span data-ttu-id="eaaa4-463">Resposta</span><span class="sxs-lookup"><span data-stu-id="eaaa4-463">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="eaaa4-464">Exemplos de cabeçalho de segurança: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="eaaa4-464">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="eaaa4-465">Solicitação</span><span class="sxs-lookup"><span data-stu-id="eaaa4-465">Request</span></span>  
  
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
  
 <span data-ttu-id="eaaa4-466">Resposta</span><span class="sxs-lookup"><span data-stu-id="eaaa4-466">Response</span></span>  
  
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
  
## <a name="63-kerberos"></a><span data-ttu-id="eaaa4-467">6.3 Kerberos</span><span class="sxs-lookup"><span data-stu-id="eaaa4-467">6.3 Kerberos</span></span>  
 <span data-ttu-id="eaaa4-468">Com esse modo de autenticação o cliente é autenticado para o serviço usando um tíquete Kerberos.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-468">With this authentication mode the client authenticates to the service using a Kerberos ticket.</span></span> <span data-ttu-id="eaaa4-469">Esse tíquete mesmo também fornece autenticação de servidor.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-469">That same ticket also provides server authentication.</span></span> <span data-ttu-id="eaaa4-470">A associação usada é uma associação simétrica com as seguintes propriedades;</span><span class="sxs-lookup"><span data-stu-id="eaaa4-470">The binding used is a symmetric binding with the following properties;</span></span>  
  
 <span data-ttu-id="eaaa4-471">Token de proteção: Tíquete Kerberos, o modo de inclusão é definido como .../IncludeToken/Once</span><span class="sxs-lookup"><span data-stu-id="eaaa4-471">Protection Token: Kerberos Ticket, inclusion mode is set to .../IncludeToken/Once</span></span>  
<span data-ttu-id="eaaa4-472">Proteção de token: False</span><span class="sxs-lookup"><span data-stu-id="eaaa4-472">Token Protection: False</span></span>  
  
 <span data-ttu-id="eaaa4-473">Todo o cabeçalho e corpo assinaturas: True</span><span class="sxs-lookup"><span data-stu-id="eaaa4-473">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="eaaa4-474">Ordem de proteção: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="eaaa4-474">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="eaaa4-475">Criptografar assinatura: True</span><span class="sxs-lookup"><span data-stu-id="eaaa4-475">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="eaaa4-476">Política</span><span class="sxs-lookup"><span data-stu-id="eaaa4-476">Policy</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="eaaa4-477">Exemplos de cabeçalho de segurança: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="eaaa4-477">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="eaaa4-478">Solicitação</span><span class="sxs-lookup"><span data-stu-id="eaaa4-478">Request</span></span>  
  
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
  
 <span data-ttu-id="eaaa4-479">Resposta</span><span class="sxs-lookup"><span data-stu-id="eaaa4-479">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="eaaa4-480">Exemplos de cabeçalho de segurança: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="eaaa4-480">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="eaaa4-481">Solicitação</span><span class="sxs-lookup"><span data-stu-id="eaaa4-481">Request</span></span>  
  
```xml  
<wsse:Security>  
TBD  
</wsse:Security>  
```  
  
 <span data-ttu-id="eaaa4-482">Resposta</span><span class="sxs-lookup"><span data-stu-id="eaaa4-482">Response</span></span>  
  
```xml  
<wsse:Security>  
TBD  
</wsse:Security>  
```  
  
#### <a name="64-issuedtoken"></a><span data-ttu-id="eaaa4-483">6.4 IssuedToken</span><span class="sxs-lookup"><span data-stu-id="eaaa4-483">6.4 IssuedToken</span></span>  
 <span data-ttu-id="eaaa4-484">Com esse modo de autenticação que o cliente não se autenticar no serviço, assim, em vez disso, o cliente apresenta um token emitido por um STS e comprova o conhecimento de uma chave compartilhada.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-484">With this authentication mode the client does not authenticate to the service, as such, rather the client presents a token issued by an STS and proves knowledge of a shared key.</span></span> <span data-ttu-id="eaaa4-485">O serviço não está autenticado para o cliente, como tal, em vez disso, o STS criptografa a chave compartilhada como parte do token emitido, de modo que apenas o serviço pode descriptografar a chave.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-485">The service is not authenticated to the client, as such, instead the STS encrypts the shared key as part of the issued token such that only the service can decrypt the key.</span></span> <span data-ttu-id="eaaa4-486">A associação usada é como simétrica associação com as seguintes propriedades;</span><span class="sxs-lookup"><span data-stu-id="eaaa4-486">The binding used is as symmetric binding with the following properties;</span></span>  
  
 <span data-ttu-id="eaaa4-487">Proteção de Token: Token emitido, o modo de inclusão é definido como .../IncludeToken/AlwaysToRecipient</span><span class="sxs-lookup"><span data-stu-id="eaaa4-487">Protection Token: Issued Token, inclusion mode is set to .../IncludeToken/AlwaysToRecipient</span></span>  
<span data-ttu-id="eaaa4-488">Proteção de token: False</span><span class="sxs-lookup"><span data-stu-id="eaaa4-488">Token Protection: False</span></span>  
  
 <span data-ttu-id="eaaa4-489">Todo o cabeçalho e corpo assinaturas: True</span><span class="sxs-lookup"><span data-stu-id="eaaa4-489">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="eaaa4-490">Ordem de proteção: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="eaaa4-490">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="eaaa4-491">Criptografar assinatura: True</span><span class="sxs-lookup"><span data-stu-id="eaaa4-491">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="eaaa4-492">Política</span><span class="sxs-lookup"><span data-stu-id="eaaa4-492">Policy</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="eaaa4-493">Exemplos de cabeçalho de segurança: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="eaaa4-493">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="eaaa4-494">Solicitação</span><span class="sxs-lookup"><span data-stu-id="eaaa4-494">Request</span></span>  
  
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
  
 <span data-ttu-id="eaaa4-495">Resposta</span><span class="sxs-lookup"><span data-stu-id="eaaa4-495">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="eaaa4-496">Exemplos de cabeçalho de segurança: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="eaaa4-496">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="eaaa4-497">Solicitação</span><span class="sxs-lookup"><span data-stu-id="eaaa4-497">Request</span></span>  
  
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
  
 <span data-ttu-id="eaaa4-498">Resposta</span><span class="sxs-lookup"><span data-stu-id="eaaa4-498">Response</span></span>  
  
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
  
### <a name="65-using-sslnegotiated-for-service-authentication"></a><span data-ttu-id="eaaa4-499">6.5 usando SslNegotiated para autenticação de serviço</span><span class="sxs-lookup"><span data-stu-id="eaaa4-499">6.5 Using SslNegotiated for Service Authentication</span></span>  
 <span data-ttu-id="eaaa4-500">Esta seção descreve um grupo de modos de autenticação que usam uma associação simétrica com o token de proteção sendo um Token de contexto de segurança por WS-SecureConversation (WS-SC) cujo valor da chave é negociado executando o protocolo TLS sobre WS-Trust (WS-T) RST / Mensagens RSTR.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-500">This section describes a group of authentication modes that use a symmetric binding with the protection token being a Security Context Token per WS-SecureConversation (WS-SC) whose key value is negotiated by executing the TLS protocol over WS-Trust (WS-T) RST/RSTR messages.</span></span> <span data-ttu-id="eaaa4-501">Detalhes da implementação de handshake TLS usando WS-Trust estão descritos no TLSNEGO.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-501">Details of the TLS handshake implementation using WS-Trust are described in TLSNEGO.</span></span> <span data-ttu-id="eaaa4-502">Aqui os exemplos de mensagem, vamos pressupor que SCT com um contexto de segurança associadas já foi estabelecida por meio de um handshake.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-502">Here in the message examples we will assume that SCT with an associated security context is already established through a handshake.</span></span>  
  
 <span data-ttu-id="eaaa4-503">A associação usada é uma associação simétrica com as seguintes propriedades;</span><span class="sxs-lookup"><span data-stu-id="eaaa4-503">The binding used is a symmetric binding with the following properties;</span></span>  
  
 <span data-ttu-id="eaaa4-504">Token de proteção: SslContextToken, modo de inclusão é definido como .../IncludeToken/Never</span><span class="sxs-lookup"><span data-stu-id="eaaa4-504">Protection Token: SslContextToken, inclusion mode is set to .../IncludeToken/Never</span></span>  
<span data-ttu-id="eaaa4-505">Proteção de token: False</span><span class="sxs-lookup"><span data-stu-id="eaaa4-505">Token Protection: False</span></span>  
  
 <span data-ttu-id="eaaa4-506">Todo o cabeçalho e corpo assinaturas: True</span><span class="sxs-lookup"><span data-stu-id="eaaa4-506">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="eaaa4-507">Ordem de proteção: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="eaaa4-507">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="eaaa4-508">Criptografar assinatura: True</span><span class="sxs-lookup"><span data-stu-id="eaaa4-508">Encrypt Signature: True</span></span>  
  
#### <a name="651-policy-for-sslnegotiated-service-authentication"></a><span data-ttu-id="eaaa4-509">6.5.1 diretiva SslNegotiated autenticação de serviço</span><span class="sxs-lookup"><span data-stu-id="eaaa4-509">6.5.1 Policy for SslNegotiated service authentication</span></span>  
 <span data-ttu-id="eaaa4-510">Política para todos os modos de autenticação nesta seção são semelhante e diferem apenas pelo suporte assinados específicos ou endossando tokens usados.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-510">Policy for all authentication modes in this section are similar and differ only by specific signed supporting or endorsing tokens used.</span></span>  
  
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
  
#### <a name="652-anonymousforsslnegotiated"></a><span data-ttu-id="eaaa4-511">6.5.2 AnonymousForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="eaaa4-511">6.5.2 AnonymousForSslNegotiated</span></span>  
 <span data-ttu-id="eaaa4-512">Com esse modo de autenticação, o cliente é anônimo e o serviço é autenticado usando um certificado X.509.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-512">With this authentication mode the client is anonymous and the service is authenticated using an X.509 certificate.</span></span> <span data-ttu-id="eaaa4-513">A associação usada é uma instância de associação simétrica, conforme descrito em 6.5.1 acima.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-513">The binding used is an instance of symmetric binding as described in 6.5.1 above.</span></span>  
  
 <span data-ttu-id="eaaa4-514">Política</span><span class="sxs-lookup"><span data-stu-id="eaaa4-514">Policy</span></span>  
  
 <span data-ttu-id="eaaa4-515">Consulte a política em 6.5.1 acima para obter detalhes de associação.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-515">See Policy in 6.5.1 above for binding details.</span></span>  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="eaaa4-516">Exemplos de cabeçalho de segurança: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="eaaa4-516">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="eaaa4-517">Solicitação</span><span class="sxs-lookup"><span data-stu-id="eaaa4-517">Request</span></span>  
  
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
  
 <span data-ttu-id="eaaa4-518">Resposta</span><span class="sxs-lookup"><span data-stu-id="eaaa4-518">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="eaaa4-519">Exemplos de cabeçalho de segurança: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="eaaa4-519">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="eaaa4-520">Solicitação</span><span class="sxs-lookup"><span data-stu-id="eaaa4-520">Request</span></span>  
  
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
  
 <span data-ttu-id="eaaa4-521">Resposta</span><span class="sxs-lookup"><span data-stu-id="eaaa4-521">Response</span></span>  
  
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
  
#### <a name="653-usernameforsslnegotiated"></a><span data-ttu-id="eaaa4-522">6.5.3 UserNameForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="eaaa4-522">6.5.3 UserNameForSslNegotiated</span></span>  
 <span data-ttu-id="eaaa4-523">Com essa autenticação modo que é o cliente autentica usando um Token de nome de usuário que aparece na camada de SOAP como um token de suporte com sinal.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-523">With this authentication mode the client is authenticates using a Username Token which appears at the SOAP layer as a signed supporting token.</span></span> <span data-ttu-id="eaaa4-524">O serviço é autenticado usando um certificado X.509.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-524">The service is authenticated using an X.509 certificate.</span></span> <span data-ttu-id="eaaa4-525">A associação usada é uma instância de associação simétrica, conforme descrito em 6.5.1.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-525">The binding used is an instance of symmetric binding as described in 6.5.1.</span></span>  
  
 <span data-ttu-id="eaaa4-526">Política</span><span class="sxs-lookup"><span data-stu-id="eaaa4-526">Policy</span></span>  
  
 <span data-ttu-id="eaaa4-527">Consulte a seção 6.5.1 acima para obter detalhes de associação</span><span class="sxs-lookup"><span data-stu-id="eaaa4-527">See section 6.5.1 above for binding details</span></span>  
  
 <span data-ttu-id="eaaa4-528">Assinado um Token de suporte</span><span class="sxs-lookup"><span data-stu-id="eaaa4-528">Signed Supporting Token</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="eaaa4-529">Exemplos de cabeçalho de segurança: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="eaaa4-529">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="eaaa4-530">Solicitação</span><span class="sxs-lookup"><span data-stu-id="eaaa4-530">Request</span></span>  
  
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
  
 <span data-ttu-id="eaaa4-531">Resposta</span><span class="sxs-lookup"><span data-stu-id="eaaa4-531">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="eaaa4-532">Exemplos de cabeçalho de segurança: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="eaaa4-532">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="eaaa4-533">Solicitação</span><span class="sxs-lookup"><span data-stu-id="eaaa4-533">Request</span></span>  
  
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
  
 <span data-ttu-id="eaaa4-534">Resposta</span><span class="sxs-lookup"><span data-stu-id="eaaa4-534">Response</span></span>  
  
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
  
#### <a name="654-issuedtokenforsslnegotiated"></a><span data-ttu-id="eaaa4-535">6.5.4 IssuedTokenForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="eaaa4-535">6.5.4 IssuedTokenForSslNegotiated</span></span>  
 <span data-ttu-id="eaaa4-536">Com essa autenticação modo que o cliente não se autenticar no serviço, como tal, mas em vez disso, apresenta um token emitido por um STS e comprova o conhecimento de uma chave compartilhada.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-536">With this authentication mode the client does not authenticate to the service, as such, but instead presents a token issued by an STS and proves knowledge of a shared key.</span></span> <span data-ttu-id="eaaa4-537">O token emitido é exibido na camada de SOAP como um token de suporte de endosso.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-537">The issued token appears at the SOAP layer as an endorsing supporting token.</span></span> <span data-ttu-id="eaaa4-538">O serviço é autenticado usando um certificado X.509.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-538">The service is authenticated using an X.509 certificate.</span></span> <span data-ttu-id="eaaa4-539">A associação usada é uma instância de associação simétrica, conforme descrito em 6.5.1 acima.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-539">The binding used is an instance of symmetric binding as described in 6.5.1 above.</span></span>  
  
 <span data-ttu-id="eaaa4-540">Política</span><span class="sxs-lookup"><span data-stu-id="eaaa4-540">Policy</span></span>  
  
 <span data-ttu-id="eaaa4-541">Consulte a seção 6.5.1 acima para obter detalhes de associação</span><span class="sxs-lookup"><span data-stu-id="eaaa4-541">See section 6.5.1 above for binding details</span></span>  
  
 <span data-ttu-id="eaaa4-542">Token de suporte de endosso</span><span class="sxs-lookup"><span data-stu-id="eaaa4-542">Endorsing Supporting Token</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="eaaa4-543">Exemplos de cabeçalho de segurança: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="eaaa4-543">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="eaaa4-544">Solicitação</span><span class="sxs-lookup"><span data-stu-id="eaaa4-544">Request</span></span>  
  
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
  
 <span data-ttu-id="eaaa4-545">Resposta</span><span class="sxs-lookup"><span data-stu-id="eaaa4-545">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="eaaa4-546">Exemplos de cabeçalho de segurança: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="eaaa4-546">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="eaaa4-547">Solicitação</span><span class="sxs-lookup"><span data-stu-id="eaaa4-547">Request</span></span>  
  
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
  
 <span data-ttu-id="eaaa4-548">Resposta</span><span class="sxs-lookup"><span data-stu-id="eaaa4-548">Response</span></span>  
  
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
  
#### <a name="655-mutualsslnegotiated"></a><span data-ttu-id="eaaa4-549">6.5.5 MutualSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="eaaa4-549">6.5.5 MutualSslNegotiated</span></span>  
 <span data-ttu-id="eaaa4-550">Com esse modo de autenticação de cliente e o serviço se autenticar usando certificados x. 509.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-550">With this authentication mode the client and the service authenticate using X.509 certificates.</span></span> <span data-ttu-id="eaaa4-551">A associação usada é uma instância de associação simétrica, conforme descrito em 6.5.1 acima.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-551">The binding used is an instance of symmetric binding as described in 6.5.1 above.</span></span>  
  
 <span data-ttu-id="eaaa4-552">Política</span><span class="sxs-lookup"><span data-stu-id="eaaa4-552">Policy</span></span>  
  
 <span data-ttu-id="eaaa4-553">Consulte a seção 6.5.1 acima para obter detalhes de associação</span><span class="sxs-lookup"><span data-stu-id="eaaa4-553">See section 6.5.1 above for binding details</span></span>  
  
 <span data-ttu-id="eaaa4-554">Token de suporte de endosso</span><span class="sxs-lookup"><span data-stu-id="eaaa4-554">Endorsing Supporting Token</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="eaaa4-555">Exemplos de cabeçalho de segurança: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="eaaa4-555">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="eaaa4-556">Solicitação</span><span class="sxs-lookup"><span data-stu-id="eaaa4-556">Request</span></span>  
  
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
  
 <span data-ttu-id="eaaa4-557">Resposta</span><span class="sxs-lookup"><span data-stu-id="eaaa4-557">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="eaaa4-558">Exemplos de cabeçalho de segurança: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="eaaa4-558">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="eaaa4-559">Solicitação</span><span class="sxs-lookup"><span data-stu-id="eaaa4-559">Request</span></span>  
  
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
  
 <span data-ttu-id="eaaa4-560">Resposta</span><span class="sxs-lookup"><span data-stu-id="eaaa4-560">Response</span></span>  
  
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
  
### <a name="66-sspinegotiated"></a><span data-ttu-id="eaaa4-561">6.6 SspiNegotiated</span><span class="sxs-lookup"><span data-stu-id="eaaa4-561">6.6 SspiNegotiated</span></span>  
 <span data-ttu-id="eaaa4-562">Com esse modo de autenticação, um protocolo de negociação é usado para realizar a autenticação de cliente e servidor.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-562">With this authentication mode a negotiation protocol is used to perform client and server authentication.</span></span> <span data-ttu-id="eaaa4-563">Kerberos é usado, se possível, caso contrário, NTLM.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-563">Kerberos is used if possible, otherwise NTLM.</span></span> <span data-ttu-id="eaaa4-564">A associação usada é uma associação simétrica com as seguintes propriedades;</span><span class="sxs-lookup"><span data-stu-id="eaaa4-564">The binding used is a symmetric binding with the following properties;</span></span>  
  
 <span data-ttu-id="eaaa4-565">Token de proteção: SpnegoContextToken, modo de inclusão é definido como .../IncludeToken/AlwaysToRecipient</span><span class="sxs-lookup"><span data-stu-id="eaaa4-565">Protection Token: SpnegoContextToken, inclusion mode is set to .../IncludeToken/AlwaysToRecipient</span></span>  
<span data-ttu-id="eaaa4-566">Proteção de token: False</span><span class="sxs-lookup"><span data-stu-id="eaaa4-566">Token Protection: False</span></span>  
  
 <span data-ttu-id="eaaa4-567">Todo o cabeçalho e corpo assinaturas: True</span><span class="sxs-lookup"><span data-stu-id="eaaa4-567">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="eaaa4-568">Ordem de proteção: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="eaaa4-568">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="eaaa4-569">Criptografar assinatura: True</span><span class="sxs-lookup"><span data-stu-id="eaaa4-569">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="eaaa4-570">Política</span><span class="sxs-lookup"><span data-stu-id="eaaa4-570">Policy</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="eaaa4-571">Exemplos de cabeçalho de segurança: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="eaaa4-571">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="eaaa4-572">Solicitação</span><span class="sxs-lookup"><span data-stu-id="eaaa4-572">Request</span></span>  
  
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
  
 <span data-ttu-id="eaaa4-573">Resposta</span><span class="sxs-lookup"><span data-stu-id="eaaa4-573">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="eaaa4-574">Exemplos de cabeçalho de segurança: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="eaaa4-574">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="eaaa4-575">Solicitação</span><span class="sxs-lookup"><span data-stu-id="eaaa4-575">Request</span></span>  
  
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
  
 <span data-ttu-id="eaaa4-576">Resposta</span><span class="sxs-lookup"><span data-stu-id="eaaa4-576">Response</span></span>  
  
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
  
### <a name="67-secureconversation"></a><span data-ttu-id="eaaa4-577">6.7 SecureConversation</span><span class="sxs-lookup"><span data-stu-id="eaaa4-577">6.7 SecureConversation</span></span>  
 <span data-ttu-id="eaaa4-578">A associação usada é uma associação simétrica com o token de proteção sendo um SCT por WS-SecureConversation (WS-SC).</span><span class="sxs-lookup"><span data-stu-id="eaaa4-578">The binding used is a symmetric binding with the protection token being a SCT per WS-SecureConversation (WS-SC).</span></span> <span data-ttu-id="eaaa4-579">O SCT é negociado usando WS-Trust (WS-Trust) ou WS-SecureConversation (WS-SC) acordo com uma associação aninhada, que também é uma associação simétrica que usa um protocolo de negociação.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-579">The SCT is negotiated using WS-Trust (WS-Trust) or WS-SecureConversation (WS-SC) according to a nested binding, which is itself a symmetric binding that uses a negotiation protocol.</span></span> <span data-ttu-id="eaaa4-580">O protocolo de negociação usam o Kerberos para realizar a autenticação de cliente e servidor se possível.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-580">The negotiation protocol will use Kerberos to perform client and server authentication if possible.</span></span> <span data-ttu-id="eaaa4-581">Se o Kerberos não pode ser usado, ele fará o fallback para NTLM.</span><span class="sxs-lookup"><span data-stu-id="eaaa4-581">If Kerberos cannot be used, it will fall back to NTLM.</span></span>  
  
 <span data-ttu-id="eaaa4-582">Política</span><span class="sxs-lookup"><span data-stu-id="eaaa4-582">Policy</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="eaaa4-583">Exemplos de cabeçalho de segurança: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="eaaa4-583">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="eaaa4-584">Solicitação</span><span class="sxs-lookup"><span data-stu-id="eaaa4-584">Request</span></span>  
  
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
  
 <span data-ttu-id="eaaa4-585">Resposta</span><span class="sxs-lookup"><span data-stu-id="eaaa4-585">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="eaaa4-586">Exemplos de cabeçalho de segurança: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="eaaa4-586">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="eaaa4-587">Solicitação</span><span class="sxs-lookup"><span data-stu-id="eaaa4-587">Request</span></span>  
  
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
  
 <span data-ttu-id="eaaa4-588">Resposta</span><span class="sxs-lookup"><span data-stu-id="eaaa4-588">Response</span></span>  
  
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
