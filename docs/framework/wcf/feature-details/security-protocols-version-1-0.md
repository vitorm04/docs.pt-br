---
title: "Protocolos de segurança versão 1.0"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ee3402d2-1076-410b-a3cb-fae0372bd7af
caps.latest.revision: "4"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: f40c79ad1a6eedc2b1de4dffa9de5b48aeb8e6f5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="security-protocols-version-10"></a><span data-ttu-id="70bfa-102">Protocolos de segurança versão 1.0</span><span class="sxs-lookup"><span data-stu-id="70bfa-102">Security Protocols version 1.0</span></span>
<span data-ttu-id="70bfa-103">Os protocolos de segurança de serviços Web fornecer mecanismos de segurança de serviços Web que abrangem todos os enterprise existente, requisitos de segurança de mensagens.</span><span class="sxs-lookup"><span data-stu-id="70bfa-103">The Web Services Security Protocols provide Web services security mechanisms that cover all existing enterprise messaging security requirements.</span></span> <span data-ttu-id="70bfa-104">Esta seção descreve o [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] detalhes de versão 1.0 (implementado no <xref:System.ServiceModel.Channels.SecurityBindingElement>) para protocolos de segurança de serviços Web a seguir.</span><span class="sxs-lookup"><span data-stu-id="70bfa-104">This section describes the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] version 1.0 details (implemented in the <xref:System.ServiceModel.Channels.SecurityBindingElement>) for the following Web services security protocols.</span></span>  
  
|<span data-ttu-id="70bfa-105">Documento de especificação /</span><span class="sxs-lookup"><span data-stu-id="70bfa-105">Specification/Document</span></span>|<span data-ttu-id="70bfa-106">Link</span><span class="sxs-lookup"><span data-stu-id="70bfa-106">Link</span></span>|  
|-|-|  
|<span data-ttu-id="70bfa-107">WSS: Segurança de mensagens SOAP 1.0</span><span class="sxs-lookup"><span data-stu-id="70bfa-107">WSS: SOAP Message Security 1.0</span></span>|<span data-ttu-id="70bfa-108">http://docs.oasis-open.org/WSS/2004/01/OASIS-200401-WSS-SOAP-Message-Security-1.0.PDF</span><span class="sxs-lookup"><span data-stu-id="70bfa-108">http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0.pdf</span></span>|  
|<span data-ttu-id="70bfa-109">WSS: Perfil de Token de nome de usuário 1.0</span><span class="sxs-lookup"><span data-stu-id="70bfa-109">WSS: Username Token Profile 1.0</span></span>|<span data-ttu-id="70bfa-110">http://docs.oasis-open.org/WSS/2004/01/OASIS-200401-WSS-username-token-Profile-1.0.PDF</span><span class="sxs-lookup"><span data-stu-id="70bfa-110">http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0.pdf</span></span>|  
|<span data-ttu-id="70bfa-111">WSS: X509 Token perfil 1.0</span><span class="sxs-lookup"><span data-stu-id="70bfa-111">WSS: X509 Token Profile 1.0</span></span>|<span data-ttu-id="70bfa-112">http://docs.oasis-open.org/WSS/2004/01/OASIS-200401-WSS-X509-token-Profile-1.0.PDF</span><span class="sxs-lookup"><span data-stu-id="70bfa-112">http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-x509-token-profile-1.0.pdf</span></span>|  
|<span data-ttu-id="70bfa-113">WSS: SAML 1.1 Profile 1.0 do Token</span><span class="sxs-lookup"><span data-stu-id="70bfa-113">WSS: SAML 1.1 Token Profile 1.0</span></span>|<span data-ttu-id="70bfa-114">http://docs.oasis-open.org/WSS/OASIS-WSS-SAML-token-Profile-1.0.PDF</span><span class="sxs-lookup"><span data-stu-id="70bfa-114">http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.0.pdf</span></span>|  
|<span data-ttu-id="70bfa-115">WSS: Segurança de mensagens SOAP 1.1</span><span class="sxs-lookup"><span data-stu-id="70bfa-115">WSS: SOAP Message Security 1.1</span></span>|<span data-ttu-id="70bfa-116">http://www.oasis-open.org/committees/download.PHP/16790/WSS-v1.1-spec-os-SOAPMessageSecurity.PDF</span><span class="sxs-lookup"><span data-stu-id="70bfa-116">http://www.oasis-open.org/committees/download.php/16790/wss-v1.1-spec-os-SOAPMessageSecurity.pdf</span></span>|  
|<span data-ttu-id="70bfa-117">Perfil de Token de nome de usuário 1.1 do WSS</span><span class="sxs-lookup"><span data-stu-id="70bfa-117">WSS Username Token Profile 1.1</span></span>|<span data-ttu-id="70bfa-118">http://docs.oasis-open.org/WSS/2004/01/OASIS-200401-WSS-username-token-Profile-1.0.PDF</span><span class="sxs-lookup"><span data-stu-id="70bfa-118">http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0.pdf</span></span>|  
|<span data-ttu-id="70bfa-119">WSS: Perfil de Token de x. 509 1.1</span><span class="sxs-lookup"><span data-stu-id="70bfa-119">WSS: X.509 Token Profile 1.1</span></span>|<span data-ttu-id="70bfa-120">http://www.oasis-open.org/committees/download.PHP/16785/WSS-v1.1-spec-os-x509TokenProfile.PDF</span><span class="sxs-lookup"><span data-stu-id="70bfa-120">http://www.oasis-open.org/committees/download.php/16785/wss-v1.1-spec-os-x509TokenProfile.pdf</span></span>|  
|<span data-ttu-id="70bfa-121">WSS: Perfil de Token Kerberos 1.1</span><span class="sxs-lookup"><span data-stu-id="70bfa-121">WSS: Kerberos Token Profile 1.1</span></span>|<span data-ttu-id="70bfa-122">http://www.oasis-open.org/committees/download.PHP/16788/WSS-v1.1-spec-os-KerberosTokenProfile.PDF</span><span class="sxs-lookup"><span data-stu-id="70bfa-122">http://www.oasis-open.org/committees/download.php/16788/wss-v1.1-spec-os-KerberosTokenProfile.pdf</span></span>|  
|<span data-ttu-id="70bfa-123">WSS: SAML 1.1 Profile 1.1 do Token</span><span class="sxs-lookup"><span data-stu-id="70bfa-123">WSS: SAML 1.1 Token Profile 1.1</span></span>|<span data-ttu-id="70bfa-124">http://www.oasis-open.org/committees/download.PHP/16768/WSS-v1.1-spec-os-SAMLTokenProfile.PDF</span><span class="sxs-lookup"><span data-stu-id="70bfa-124">http://www.oasis-open.org/committees/download.php/16768/wss-v1.1-spec-os-SAMLTokenProfile.pdf</span></span>|  
|<span data-ttu-id="70bfa-125">WS-Secure Conversation</span><span class="sxs-lookup"><span data-stu-id="70bfa-125">WS-Secure Conversation</span></span>|<span data-ttu-id="70bfa-126">http://msdn.microsoft.com/ws/2005/02/WS-Secure-Conversation/</span><span class="sxs-lookup"><span data-stu-id="70bfa-126">http://msdn.microsoft.com/ws/2005/02/ws-secure-conversation/</span></span>|  
|<span data-ttu-id="70bfa-127">WS-Trust</span><span class="sxs-lookup"><span data-stu-id="70bfa-127">WS-Trust</span></span>|<span data-ttu-id="70bfa-128">http://msdn.microsoft.com/ws/2005/02/WS-Trust/</span><span class="sxs-lookup"><span data-stu-id="70bfa-128">http://msdn.microsoft.com/ws/2005/02/ws-trust/</span></span>|  
|<span data-ttu-id="70bfa-129">Observação do aplicativo:</span><span class="sxs-lookup"><span data-stu-id="70bfa-129">Application Note:</span></span><br /><br /> <span data-ttu-id="70bfa-130">Usando o WS-Trust de Handshake TLS</span><span class="sxs-lookup"><span data-stu-id="70bfa-130">Using WS-Trust for TLS Handshake</span></span>|<span data-ttu-id="70bfa-131">A publicação</span><span class="sxs-lookup"><span data-stu-id="70bfa-131">To be published</span></span>|  
|<span data-ttu-id="70bfa-132">Observação do aplicativo:</span><span class="sxs-lookup"><span data-stu-id="70bfa-132">Application Note:</span></span><br /><br /> <span data-ttu-id="70bfa-133">Usando o WS-Trust para SPNEGO</span><span class="sxs-lookup"><span data-stu-id="70bfa-133">Using WS-Trust for SPNEGO</span></span>|<span data-ttu-id="70bfa-134">A publicação</span><span class="sxs-lookup"><span data-stu-id="70bfa-134">To be published</span></span>|  
|<span data-ttu-id="70bfa-135">Observação do aplicativo:</span><span class="sxs-lookup"><span data-stu-id="70bfa-135">Application Note:</span></span><br /><br /> <span data-ttu-id="70bfa-136">Identidade e referências de endereçamento de ponto de extremidade de serviços Web</span><span class="sxs-lookup"><span data-stu-id="70bfa-136">Web Services Addressing Endpoint References And Identity</span></span>|<span data-ttu-id="70bfa-137">A publicação</span><span class="sxs-lookup"><span data-stu-id="70bfa-137">To be published</span></span>|  
|<span data-ttu-id="70bfa-138">O WS-SecurityPolicy 1.1</span><span class="sxs-lookup"><span data-stu-id="70bfa-138">WS-SecurityPolicy 1.1</span></span><br /><br /> <span data-ttu-id="70bfa-139">(2005/07)</span><span class="sxs-lookup"><span data-stu-id="70bfa-139">(2005/07)</span></span>|<span data-ttu-id="70bfa-140">http://msdn.microsoft.com/ws/2005/07/WS-Security-Policy/</span><span class="sxs-lookup"><span data-stu-id="70bfa-140">http://msdn.microsoft.com/ws/2005/07/ws-security-policy/</span></span><br /><br /> <span data-ttu-id="70bfa-141">como corrigida por errata enviado ao OASIS WS-SX Technical Committee http://www.oasis-open.org/archives/ws-sx/200512/msg00017.html</span><span class="sxs-lookup"><span data-stu-id="70bfa-141">as amended by errata submitted to OASIS WS-SX Technical Committee http://www.oasis-open.org/archives/ws-sx/200512/msg00017.html</span></span>|  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="70bfa-142">, versão 1, fornece 17 modos de autenticação que podem ser usados como a base de configuração de segurança de serviços da Web.</span><span class="sxs-lookup"><span data-stu-id="70bfa-142">, version 1, provides 17 authentication modes that can be used as the basis for Web services security configuration.</span></span> <span data-ttu-id="70bfa-143">Cada modo é otimizado para um conjunto comum de requisitos de implantação, como:</span><span class="sxs-lookup"><span data-stu-id="70bfa-143">Each mode is optimized for a common set of deployment requirements, such as:</span></span>  
  
-   <span data-ttu-id="70bfa-144">Credenciais usadas para autenticar o cliente e o serviço.</span><span class="sxs-lookup"><span data-stu-id="70bfa-144">Credentials used to authenticate client and service.</span></span>  
  
-   <span data-ttu-id="70bfa-145">Mecanismos de proteção de segurança transporte ou mensagem.</span><span class="sxs-lookup"><span data-stu-id="70bfa-145">Message or transport security protection mechanisms.</span></span>  
  
-   <span data-ttu-id="70bfa-146">Padrões de troca de mensagem.</span><span class="sxs-lookup"><span data-stu-id="70bfa-146">Message exchange patterns.</span></span>  
  
|<span data-ttu-id="70bfa-147">Modo de autenticação</span><span class="sxs-lookup"><span data-stu-id="70bfa-147">Authentication Mode</span></span>|<span data-ttu-id="70bfa-148">Autenticação de cliente</span><span class="sxs-lookup"><span data-stu-id="70bfa-148">Client Authentication</span></span>|<span data-ttu-id="70bfa-149">Autenticação de servidor</span><span class="sxs-lookup"><span data-stu-id="70bfa-149">Server Authentication</span></span>|<span data-ttu-id="70bfa-150">Modo</span><span class="sxs-lookup"><span data-stu-id="70bfa-150">Mode</span></span>|  
|-------------------------|---------------------------|---------------------------|----------|  
|<span data-ttu-id="70bfa-151">UserNameOverTransport</span><span class="sxs-lookup"><span data-stu-id="70bfa-151">UserNameOverTransport</span></span>|<span data-ttu-id="70bfa-152">Nome de usuário/senha</span><span class="sxs-lookup"><span data-stu-id="70bfa-152">User name/password</span></span>|<span data-ttu-id="70bfa-153">X509</span><span class="sxs-lookup"><span data-stu-id="70bfa-153">X509</span></span>|<span data-ttu-id="70bfa-154">Transporte</span><span class="sxs-lookup"><span data-stu-id="70bfa-154">Transport</span></span>|  
|<span data-ttu-id="70bfa-155">CertificateOverTransport</span><span class="sxs-lookup"><span data-stu-id="70bfa-155">CertificateOverTransport</span></span>|<span data-ttu-id="70bfa-156">X509</span><span class="sxs-lookup"><span data-stu-id="70bfa-156">X509</span></span>|<span data-ttu-id="70bfa-157">X509</span><span class="sxs-lookup"><span data-stu-id="70bfa-157">X509</span></span>|<span data-ttu-id="70bfa-158">Transporte</span><span class="sxs-lookup"><span data-stu-id="70bfa-158">Transport</span></span>|  
|<span data-ttu-id="70bfa-159">KerberosOverTransport</span><span class="sxs-lookup"><span data-stu-id="70bfa-159">KerberosOverTransport</span></span>|<span data-ttu-id="70bfa-160">Windows</span><span class="sxs-lookup"><span data-stu-id="70bfa-160">Windows</span></span>|<span data-ttu-id="70bfa-161">X509</span><span class="sxs-lookup"><span data-stu-id="70bfa-161">X509</span></span>|<span data-ttu-id="70bfa-162">Transporte</span><span class="sxs-lookup"><span data-stu-id="70bfa-162">Transport</span></span>|  
|<span data-ttu-id="70bfa-163">IssuedTokenOverTransport</span><span class="sxs-lookup"><span data-stu-id="70bfa-163">IssuedTokenOverTransport</span></span>|<span data-ttu-id="70bfa-164">Federado</span><span class="sxs-lookup"><span data-stu-id="70bfa-164">Federated</span></span>|<span data-ttu-id="70bfa-165">X509</span><span class="sxs-lookup"><span data-stu-id="70bfa-165">X509</span></span>|<span data-ttu-id="70bfa-166">Transporte</span><span class="sxs-lookup"><span data-stu-id="70bfa-166">Transport</span></span>|  
|<span data-ttu-id="70bfa-167">SspiNegotiatedOverTransport</span><span class="sxs-lookup"><span data-stu-id="70bfa-167">SspiNegotiatedOverTransport</span></span>|<span data-ttu-id="70bfa-168">Negociada Sspi do Windows</span><span class="sxs-lookup"><span data-stu-id="70bfa-168">Windows Sspi Negotiated</span></span>|<span data-ttu-id="70bfa-169">Negociada Sspi do Windows</span><span class="sxs-lookup"><span data-stu-id="70bfa-169">Windows Sspi Negotiated</span></span>|<span data-ttu-id="70bfa-170">Transporte</span><span class="sxs-lookup"><span data-stu-id="70bfa-170">Transport</span></span>|  
|<span data-ttu-id="70bfa-171">AnonymousForCertificate</span><span class="sxs-lookup"><span data-stu-id="70bfa-171">AnonymousForCertificate</span></span>|<span data-ttu-id="70bfa-172">Nenhum</span><span class="sxs-lookup"><span data-stu-id="70bfa-172">None</span></span>|<span data-ttu-id="70bfa-173">X509</span><span class="sxs-lookup"><span data-stu-id="70bfa-173">X509</span></span>|<span data-ttu-id="70bfa-174">Mensagem</span><span class="sxs-lookup"><span data-stu-id="70bfa-174">Message</span></span>|  
|<span data-ttu-id="70bfa-175">UserNameForCertificate</span><span class="sxs-lookup"><span data-stu-id="70bfa-175">UserNameForCertificate</span></span>|<span data-ttu-id="70bfa-176">Nome de usuário/senha</span><span class="sxs-lookup"><span data-stu-id="70bfa-176">User name/password</span></span>|<span data-ttu-id="70bfa-177">X509</span><span class="sxs-lookup"><span data-stu-id="70bfa-177">X509</span></span>|<span data-ttu-id="70bfa-178">Mensagem</span><span class="sxs-lookup"><span data-stu-id="70bfa-178">Message</span></span>|  
|<span data-ttu-id="70bfa-179">MutualCertificate</span><span class="sxs-lookup"><span data-stu-id="70bfa-179">MutualCertificate</span></span>|<span data-ttu-id="70bfa-180">X509</span><span class="sxs-lookup"><span data-stu-id="70bfa-180">X509</span></span>|<span data-ttu-id="70bfa-181">X509</span><span class="sxs-lookup"><span data-stu-id="70bfa-181">X509</span></span>|<span data-ttu-id="70bfa-182">Mensagem</span><span class="sxs-lookup"><span data-stu-id="70bfa-182">Message</span></span>|  
|<span data-ttu-id="70bfa-183">MutualCertificateDuplex</span><span class="sxs-lookup"><span data-stu-id="70bfa-183">MutualCertificateDuplex</span></span>|<span data-ttu-id="70bfa-184">X509</span><span class="sxs-lookup"><span data-stu-id="70bfa-184">X509</span></span>|<span data-ttu-id="70bfa-185">X509</span><span class="sxs-lookup"><span data-stu-id="70bfa-185">X509</span></span>|<span data-ttu-id="70bfa-186">Mensagem</span><span class="sxs-lookup"><span data-stu-id="70bfa-186">Message</span></span>|  
|<span data-ttu-id="70bfa-187">IssuedTokenForCertificate</span><span class="sxs-lookup"><span data-stu-id="70bfa-187">IssuedTokenForCertificate</span></span>|<span data-ttu-id="70bfa-188">Federado</span><span class="sxs-lookup"><span data-stu-id="70bfa-188">Federated</span></span>|<span data-ttu-id="70bfa-189">X509</span><span class="sxs-lookup"><span data-stu-id="70bfa-189">X509</span></span>|<span data-ttu-id="70bfa-190">Mensagem</span><span class="sxs-lookup"><span data-stu-id="70bfa-190">Message</span></span>|  
|<span data-ttu-id="70bfa-191">Kerberos</span><span class="sxs-lookup"><span data-stu-id="70bfa-191">Kerberos</span></span>|<span data-ttu-id="70bfa-192">Windows</span><span class="sxs-lookup"><span data-stu-id="70bfa-192">Windows</span></span>|<span data-ttu-id="70bfa-193">Windows</span><span class="sxs-lookup"><span data-stu-id="70bfa-193">Windows</span></span>|<span data-ttu-id="70bfa-194">Mensagem</span><span class="sxs-lookup"><span data-stu-id="70bfa-194">Message</span></span>|  
|<span data-ttu-id="70bfa-195">IssuedToken</span><span class="sxs-lookup"><span data-stu-id="70bfa-195">IssuedToken</span></span>|<span data-ttu-id="70bfa-196">Federado</span><span class="sxs-lookup"><span data-stu-id="70bfa-196">Federated</span></span>|<span data-ttu-id="70bfa-197">Federado</span><span class="sxs-lookup"><span data-stu-id="70bfa-197">Federated</span></span>|<span data-ttu-id="70bfa-198">Mensagem</span><span class="sxs-lookup"><span data-stu-id="70bfa-198">Message</span></span>|  
|<span data-ttu-id="70bfa-199">SspiNegotiated</span><span class="sxs-lookup"><span data-stu-id="70bfa-199">SspiNegotiated</span></span>|<span data-ttu-id="70bfa-200">Negociada Sspi do Windows</span><span class="sxs-lookup"><span data-stu-id="70bfa-200">Windows Sspi Negotiated</span></span>|<span data-ttu-id="70bfa-201">Negociada Sspi do Windows</span><span class="sxs-lookup"><span data-stu-id="70bfa-201">Windows Sspi Negotiated</span></span>|<span data-ttu-id="70bfa-202">Mensagem</span><span class="sxs-lookup"><span data-stu-id="70bfa-202">Message</span></span>|  
|<span data-ttu-id="70bfa-203">AnonymousForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="70bfa-203">AnonymousForSslNegotiated</span></span>|<span data-ttu-id="70bfa-204">Nenhum</span><span class="sxs-lookup"><span data-stu-id="70bfa-204">None</span></span>|<span data-ttu-id="70bfa-205">X509, Nego TLS</span><span class="sxs-lookup"><span data-stu-id="70bfa-205">X509, TLS-Nego</span></span>|<span data-ttu-id="70bfa-206">Mensagem</span><span class="sxs-lookup"><span data-stu-id="70bfa-206">Message</span></span>|  
|<span data-ttu-id="70bfa-207">UserNameForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="70bfa-207">UserNameForSslNegotiated</span></span>|<span data-ttu-id="70bfa-208">Nome de usuário/senha</span><span class="sxs-lookup"><span data-stu-id="70bfa-208">User name/password</span></span>|<span data-ttu-id="70bfa-209">X509, Nego TLS</span><span class="sxs-lookup"><span data-stu-id="70bfa-209">X509, TLS-Nego</span></span>|<span data-ttu-id="70bfa-210">Mensagem</span><span class="sxs-lookup"><span data-stu-id="70bfa-210">Message</span></span>|  
|<span data-ttu-id="70bfa-211">MutualSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="70bfa-211">MutualSslNegotiated</span></span>|<span data-ttu-id="70bfa-212">X509</span><span class="sxs-lookup"><span data-stu-id="70bfa-212">X509</span></span>|<span data-ttu-id="70bfa-213">X509, Nego TLS</span><span class="sxs-lookup"><span data-stu-id="70bfa-213">X509, TLS-Nego</span></span>|<span data-ttu-id="70bfa-214">Mensagem</span><span class="sxs-lookup"><span data-stu-id="70bfa-214">Message</span></span>|  
|<span data-ttu-id="70bfa-215">IssuedTokenForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="70bfa-215">IssuedTokenForSslNegotiated</span></span>|<span data-ttu-id="70bfa-216">Federado</span><span class="sxs-lookup"><span data-stu-id="70bfa-216">Federated</span></span>|<span data-ttu-id="70bfa-217">X509, Nego TLS</span><span class="sxs-lookup"><span data-stu-id="70bfa-217">X509, TLS-Nego</span></span>|<span data-ttu-id="70bfa-218">Mensagem</span><span class="sxs-lookup"><span data-stu-id="70bfa-218">Message</span></span>|  
  
 <span data-ttu-id="70bfa-219">Pontos de extremidade usando esses modos de autenticação podem expressar seus requisitos de segurança usando o WS-SecurityPolicy (WS-SP).</span><span class="sxs-lookup"><span data-stu-id="70bfa-219">Endpoints using such authentication modes can express their security requirements using WS-SecurityPolicy (WS-SP).</span></span> <span data-ttu-id="70bfa-220">Este documento descreve a estrutura de cabeçalho de segurança e mensagens de infraestrutura para cada modo de autenticação e fornece exemplos de políticas e mensagens.</span><span class="sxs-lookup"><span data-stu-id="70bfa-220">This document describes the structure of security header and infrastructure messages for each authentication mode and provides examples of policies and messages.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="70bfa-221">aproveita o WS-SecureConversation para oferecer suportam a sessões seguras para proteger os intercâmbios de várias mensagens entre aplicativos.</span><span class="sxs-lookup"><span data-stu-id="70bfa-221"> leverages WS-SecureConversation to provide secure sessions support to protect multi-message exchanges between applications.</span></span>  <span data-ttu-id="70bfa-222">Consulte "Proteger sessões" abaixo para obter detalhes de implementação.</span><span class="sxs-lookup"><span data-stu-id="70bfa-222">See "Secure Sessions" below for implementation details.</span></span>  
  
 <span data-ttu-id="70bfa-223">Além dos modos de autenticação, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] fornece as configurações para controlar os mecanismos de proteção comuns que se aplicam à maioria dos modos de autenticação com base em segurança de mensagem, por exemplo: ordem de assinatura versus operações de criptografia, conjuntos de algoritmo derivação de chave e a confirmação de assinatura.</span><span class="sxs-lookup"><span data-stu-id="70bfa-223">In addition to authentication modes, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] provides settings to control common protection mechanisms that apply to most message security-based authentication modes, for example: order of signature versus encryption operations, algorithm suites, key derivation, and signature confirmation.</span></span>  
  
 <span data-ttu-id="70bfa-224">Os prefixos e os namespaces a seguir são usadas neste documento.</span><span class="sxs-lookup"><span data-stu-id="70bfa-224">The following prefixes and namespaces are used in this document.</span></span>  
  
|<span data-ttu-id="70bfa-225">Prefixo</span><span class="sxs-lookup"><span data-stu-id="70bfa-225">Prefix</span></span>|<span data-ttu-id="70bfa-226">Namespace</span><span class="sxs-lookup"><span data-stu-id="70bfa-226">Namespace</span></span>|  
|------------|---------------|  
|<span data-ttu-id="70bfa-227">s</span><span class="sxs-lookup"><span data-stu-id="70bfa-227">s</span></span>|<span data-ttu-id="70bfa-228">http://www.w3.org/2003/05/SOAP-envelope</span><span class="sxs-lookup"><span data-stu-id="70bfa-228">http://www.w3.org/2003/05/soap-envelope</span></span>|  
|<span data-ttu-id="70bfa-229">SP</span><span class="sxs-lookup"><span data-stu-id="70bfa-229">sp</span></span>|<span data-ttu-id="70bfa-230">http://schemas.xmlsoap.org/ws/2005/07/SecurityPolicy</span><span class="sxs-lookup"><span data-stu-id="70bfa-230">http://schemas.xmlsoap.org/ws/2005/07/securitypolicy</span></span>|  
|<span data-ttu-id="70bfa-231">a</span><span class="sxs-lookup"><span data-stu-id="70bfa-231">a</span></span>|<span data-ttu-id="70bfa-232">http://www.w3.org/2005/08/Addressing</span><span class="sxs-lookup"><span data-stu-id="70bfa-232">http://www.w3.org/2005/08/addressing</span></span>|  
|<span data-ttu-id="70bfa-233">wsse</span><span class="sxs-lookup"><span data-stu-id="70bfa-233">wsse</span></span>|<span data-ttu-id="70bfa-234">TBD-OASIS WSS 1.0 URI</span><span class="sxs-lookup"><span data-stu-id="70bfa-234">TBD – OASIS WSS 1.0 URI</span></span>|  
|<span data-ttu-id="70bfa-235">wsse11</span><span class="sxs-lookup"><span data-stu-id="70bfa-235">wsse11</span></span>|<span data-ttu-id="70bfa-236">TBD-OASIS WSS 1.1 URI</span><span class="sxs-lookup"><span data-stu-id="70bfa-236">TBD – OASIS WSS 1.1 URI</span></span>|  
|<span data-ttu-id="70bfa-237">wsu</span><span class="sxs-lookup"><span data-stu-id="70bfa-237">wsu</span></span>|<span data-ttu-id="70bfa-238">TBD-OASIS WSS 1.0 utilitário URI</span><span class="sxs-lookup"><span data-stu-id="70bfa-238">TBD – OASIS WSS 1.0 Utility URI</span></span>|  
|<span data-ttu-id="70bfa-239">DS</span><span class="sxs-lookup"><span data-stu-id="70bfa-239">ds</span></span>|<span data-ttu-id="70bfa-240">TBD-W3C XMLDSig URI</span><span class="sxs-lookup"><span data-stu-id="70bfa-240">TBD – W3C XMLDSig URI</span></span>|  
|<span data-ttu-id="70bfa-241">WST</span><span class="sxs-lookup"><span data-stu-id="70bfa-241">wst</span></span>|<span data-ttu-id="70bfa-242">TBD-02/2005 WS-Trust URI</span><span class="sxs-lookup"><span data-stu-id="70bfa-242">TBD – WS-Trust 2005/02 URI</span></span>|  
|<span data-ttu-id="70bfa-243">wssc</span><span class="sxs-lookup"><span data-stu-id="70bfa-243">wssc</span></span>|<span data-ttu-id="70bfa-244">TBD-02/2005 WS-SecureConversation URI</span><span class="sxs-lookup"><span data-stu-id="70bfa-244">TBD – WS-SecureConversation 2005/02 URI</span></span>|  
|<span data-ttu-id="70bfa-245">wsaw</span><span class="sxs-lookup"><span data-stu-id="70bfa-245">wsaw</span></span>|<span data-ttu-id="70bfa-246">TBD - WS-Addressing namespace de política</span><span class="sxs-lookup"><span data-stu-id="70bfa-246">TBD - WS-Addressing policy namespace</span></span>|  
|<span data-ttu-id="70bfa-247">wsp</span><span class="sxs-lookup"><span data-stu-id="70bfa-247">wsp</span></span>|<span data-ttu-id="70bfa-248">http://schemas.xmlsoap.org/ws/2004/09/Policy</span><span class="sxs-lookup"><span data-stu-id="70bfa-248">http://schemas.xmlsoap.org/ws/2004/09/policy</span></span>|  
|<span data-ttu-id="70bfa-249">mssp</span><span class="sxs-lookup"><span data-stu-id="70bfa-249">mssp</span></span>|<span data-ttu-id="70bfa-250">http://schemas.microsoft.com/ws/2005/07/SecurityPolicy</span><span class="sxs-lookup"><span data-stu-id="70bfa-250">http://schemas.microsoft.com/ws/2005/07/securitypolicy</span></span>|  
  
## <a name="1-token-profiles"></a><span data-ttu-id="70bfa-251">1. Perfis de token</span><span class="sxs-lookup"><span data-stu-id="70bfa-251">1. Token Profiles</span></span>  
 <span data-ttu-id="70bfa-252">Especificações de segurança dos serviços da Web representam credencial como tokens de segurança.</span><span class="sxs-lookup"><span data-stu-id="70bfa-252">Web Services Security specifications represent credential as security tokens.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="70bfa-253">suporta os seguintes tipos de token:</span><span class="sxs-lookup"><span data-stu-id="70bfa-253"> supports the following token types:</span></span>  
  
### <a name="11-usernametoken"></a><span data-ttu-id="70bfa-254">1.1 UsernameToken</span><span class="sxs-lookup"><span data-stu-id="70bfa-254">1.1 UsernameToken</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="70bfa-255">perfis de UsernameToken10 e UsernameToken11 com as seguintes restrições a seguir:</span><span class="sxs-lookup"><span data-stu-id="70bfa-255"> follows UsernameToken10 and UsernameToken11 profiles with the following constraints:</span></span>  
  
 <span data-ttu-id="70bfa-256">R1101 PasswordType atributo no elemento UsernameToken\Password deve ser omitido ou tem valor #PasswordText (padrão).</span><span class="sxs-lookup"><span data-stu-id="70bfa-256">R1101 PasswordType attribute on UsernameToken\Password element MUST be either omitted or have value #PasswordText (default).</span></span>  
  
 <span data-ttu-id="70bfa-257">O #PasswordDigest usando extensibilidade podem ser implementados.</span><span class="sxs-lookup"><span data-stu-id="70bfa-257">One can implement the #PasswordDigest using extensibility.</span></span> <span data-ttu-id="70bfa-258">Foi observado que #PasswordDigest foi enganado geralmente para ser um mecanismo de proteção de senha segura o suficiente.</span><span class="sxs-lookup"><span data-stu-id="70bfa-258">It has been observed that #PasswordDigest was often mistaken to be a secure enough password protection mechanism.</span></span> <span data-ttu-id="70bfa-259">Mas #PasswordDigest não pode servir como um substituto para criptografia de UsernameToken.</span><span class="sxs-lookup"><span data-stu-id="70bfa-259">But #PasswordDigest cannot serve as a substitute for encryption of the UsernameToken.</span></span> <span data-ttu-id="70bfa-260">O objetivo principal do #PasswordDigest é a proteção contra ataques de repetição.</span><span class="sxs-lookup"><span data-stu-id="70bfa-260">The primary goal of #PasswordDigest is protection against replay attacks.</span></span> <span data-ttu-id="70bfa-261">Em [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] modos de autenticação, as ameaças de ataques de reprodução são atenuados usando assinaturas de mensagem.</span><span class="sxs-lookup"><span data-stu-id="70bfa-261">In [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] authentication modes, replay attack threats are mitigated by using message signatures.</span></span>  
  
 <span data-ttu-id="70bfa-262">B1102 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] nunca emite Nonce e criado subelementos UsernameToken.</span><span class="sxs-lookup"><span data-stu-id="70bfa-262">B1102 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] never emits Nonce and Created sub-elements of the UsernameToken.</span></span>  
  
 <span data-ttu-id="70bfa-263">Estes subelementos destinam-se a ajudar na detecção de repetição.</span><span class="sxs-lookup"><span data-stu-id="70bfa-263">These sub-elements are intended to help replay detection.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="70bfa-264">usa assinaturas de mensagem.</span><span class="sxs-lookup"><span data-stu-id="70bfa-264"> uses message signatures instead.</span></span>  
  
 <span data-ttu-id="70bfa-265">OASIS WSS SOAP mensagem segurança UsernameToken Profile 1.1 (UsernameToken11) introduziu a derivação de chave de recurso de senha.</span><span class="sxs-lookup"><span data-stu-id="70bfa-265">OASIS WSS SOAP Message Security UsernameToken Profile 1.1 (UsernameToken11) introduced key derivation from password feature.</span></span>  
  
 <span data-ttu-id="70bfa-266">B1103 UsernameToken senha não deve ser usada para derivação de chaves e, portanto, para operações criptográficas.</span><span class="sxs-lookup"><span data-stu-id="70bfa-266">B1103 UsernameToken password MUST not be used for key derivation and therefore for cryptographic operations.</span></span>  
  
 <span data-ttu-id="70bfa-267">Motivo: senhas geralmente são consideradas muito fracas para ser usada para operações criptográficas.</span><span class="sxs-lookup"><span data-stu-id="70bfa-267">Rationale: passwords are generally considered too weak to be used for cryptographic operations.</span></span>  
  
### <a name="12-x509-token"></a><span data-ttu-id="70bfa-268">1.2 x 509 Token</span><span class="sxs-lookup"><span data-stu-id="70bfa-268">1.2 X509 Token</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="70bfa-269">oferece suporte a certificados de X509v3 como um tipo de credencial e segue X509TokenProfile1.0 e X509TokenProfile1.1 com as seguintes restrições:</span><span class="sxs-lookup"><span data-stu-id="70bfa-269"> supports X509v3 certificates as a credential type and follows X509TokenProfile1.0 and X509TokenProfile1.1 with the following constraints:</span></span>  
  
 <span data-ttu-id="70bfa-270">Atributo ValueType o R1201 no elemento BinarySecurityToken deve ter valor #X509v3 quando ele contém um certificado de X509v3.</span><span class="sxs-lookup"><span data-stu-id="70bfa-270">R1201 The ValueType attribute on the BinarySecurityToken element must have value #X509v3 when it contains an X509v3 certificate.</span></span>  
  
 <span data-ttu-id="70bfa-271">WSS X509 Token Profile 1.0 e 1.1 definem também X509PKIPathv&#1; e #PKCS7 como tipos de valor.</span><span class="sxs-lookup"><span data-stu-id="70bfa-271">WSS X509 Token Profile 1.0 and 1.1 define also #X509PKIPathv1 and #PKCS7 as value types.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="70bfa-272">não oferece suporte a esses tipos.</span><span class="sxs-lookup"><span data-stu-id="70bfa-272"> does not support these types.</span></span>  
  
 <span data-ttu-id="70bfa-273">R1202 se uma extensão de SubjectKeyIdentifier (SKI) está presente no X509 certificado, wsse:KeyIdentifier deve ser usado para referências externas para o token, com ValueType como #X509SubjectKeyIdentifier e seu conteúdo o codificada em base64 valor de atributo extensão SKI do certificado.</span><span class="sxs-lookup"><span data-stu-id="70bfa-273">R1202 If a SubjectKeyIdentifier (SKI) extension is present in an X509 certificate, wsse:KeyIdentifier should be used for external references to the token, with the ValueType attribute as #X509SubjectKeyIdentifier and its content the base64-encoded value of certificate's SKI extension.</span></span>  
  
 <span data-ttu-id="70bfa-274">Referências SKI são amplamente implementadas e mostrou para ser um tipo de referência externa altamente interoperável.</span><span class="sxs-lookup"><span data-stu-id="70bfa-274">SKI references are widely implemented and proven to be a highly interoperable external reference type.</span></span>  
  
 <span data-ttu-id="70bfa-275">R1203 Uma referência externa para X509 segurança Token não devem usar ds:X509IssuerSerial.</span><span class="sxs-lookup"><span data-stu-id="70bfa-275">R1203 An external Reference to X509 Security Token SHOULD NOT use ds:X509IssuerSerial.</span></span>  
  
 <span data-ttu-id="70bfa-276">X509TokenProfile1.1 de R1204 se estiver em uso, uma referência externa para X509 segurança Token deve usar a impressão digital introduzida por 1,1 WS-Security.</span><span class="sxs-lookup"><span data-stu-id="70bfa-276">R1204 If X509TokenProfile1.1 is in use, an external reference to X509 Security Token SHOULD use the thumbprint introduced by WS-Security 1.1.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="70bfa-277">dá suporte a X509IssuerSerial.</span><span class="sxs-lookup"><span data-stu-id="70bfa-277"> supports X509IssuerSerial.</span></span> <span data-ttu-id="70bfa-278">No entanto, há problemas de interoperabilidade com X509IssuerSerial: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usa uma cadeia de caracteres para comparar dois valores de X509IssuerSerial.</span><span class="sxs-lookup"><span data-stu-id="70bfa-278">However There are interoperability issues with X509IssuerSerial: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uses a string to compare two values of X509IssuerSerial.</span></span> <span data-ttu-id="70bfa-279">Portanto, se um reorganiza os componentes do nome da entidade e envia para uma [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uma referência a um certificado de serviço, ele não pode ser encontrado.</span><span class="sxs-lookup"><span data-stu-id="70bfa-279">Therefore if one reorders components of the Subject Name and sends to an [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service a reference to a certificate, it may not be found.</span></span>  
  
### <a name="13-kerberos-token"></a><span data-ttu-id="70bfa-280">1.3 Token Kerberos</span><span class="sxs-lookup"><span data-stu-id="70bfa-280">1.3 Kerberos Token</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="70bfa-281">dá suporte a KerberosTokenProfile1.1 para fins de autenticação do Windows com as seguintes restrições:</span><span class="sxs-lookup"><span data-stu-id="70bfa-281"> supports KerberosTokenProfile1.1 for the purpose of Windows authentication with the following constraints:</span></span>  
  
 <span data-ttu-id="70bfa-282">R1301 um Kerberos Token deve conter o valor de um GSS encapsulado Kerberos v4 AP_REQ conforme definido em GSS_API e a especificação de Kerberos e deve ter o atributo ValueType com o valor #GSS_Kerberosv5_AP_REQ.</span><span class="sxs-lookup"><span data-stu-id="70bfa-282">R1301 A Kerberos Token must carry the value of a GSS wrapped Kerberos v4 AP_REQ as defined in GSS_API and the Kerberos specification, and must have the ValueType attribute with the value #GSS_Kerberosv5_AP_REQ.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="70bfa-283">usa GSS encapsulado AP-REQ Kerberos, não um bare AP-REQ.</span><span class="sxs-lookup"><span data-stu-id="70bfa-283"> uses GSS wrapped Kerberos AP-REQ, not a bare AP-REQ.</span></span> <span data-ttu-id="70bfa-284">Isso é uma prática recomendada de segurança.</span><span class="sxs-lookup"><span data-stu-id="70bfa-284">This is a security best practice.</span></span>  
  
### <a name="14-saml-v11-token"></a><span data-ttu-id="70bfa-285">1.4 SAML 1.1 Token</span><span class="sxs-lookup"><span data-stu-id="70bfa-285">1.4 SAML v1.1 Token</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="70bfa-286">dá suporte a perfis de Token de SAML do WSS 1.0 e 1.1 para tokens do SAML 1.1.</span><span class="sxs-lookup"><span data-stu-id="70bfa-286"> supports WSS SAML Token profiles 1.0 and 1.1 for SAML v1.1 tokens.</span></span> <span data-ttu-id="70bfa-287">É possível implementar a outras versões de formatos de token SAML.</span><span class="sxs-lookup"><span data-stu-id="70bfa-287">It is possible to implement other versions of SAML token formats.</span></span>  
  
### <a name="15-security-context-token"></a><span data-ttu-id="70bfa-288">1.5 Token de contexto de segurança de</span><span class="sxs-lookup"><span data-stu-id="70bfa-288">1.5 Security Context Token</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="70bfa-289">oferece suporte a segurança contexto Token SCT () introduzido no WS-SecureCoversation.</span><span class="sxs-lookup"><span data-stu-id="70bfa-289"> supports the Security Context Token (SCT) introduced in WS-SecureCoversation.</span></span> <span data-ttu-id="70bfa-290">SCT é usada para representar o contexto de segurança estabelecido no SecureConversation, bem como a negociação binária protocolos TLS e SSPI, descrito abaixo.</span><span class="sxs-lookup"><span data-stu-id="70bfa-290">SCT is used to represent a security context established in SecureConversation as well as the binary negotiation protocols TLS and SSPI, described below.</span></span>  
  
## <a name="2-common-message-security-parameters"></a><span data-ttu-id="70bfa-291">2. Parâmetros comuns de segurança de mensagem</span><span class="sxs-lookup"><span data-stu-id="70bfa-291">2. Common Message Security Parameters</span></span>  
  
### <a name="21-timestamp"></a><span data-ttu-id="70bfa-292">2.1 TimeStamp</span><span class="sxs-lookup"><span data-stu-id="70bfa-292">2.1 TimeStamp</span></span>  
 <span data-ttu-id="70bfa-293">Presença de carimbo de hora é controlada usando o <xref:System.ServiceModel.Channels.SecurityBindingElement.IncludeTimestamp%2A> propriedade o <xref:System.ServiceModel.Channels.SecurityBindingElement> classe.</span><span class="sxs-lookup"><span data-stu-id="70bfa-293">Timestamp presence is controlled using the <xref:System.ServiceModel.Channels.SecurityBindingElement.IncludeTimestamp%2A> property of the <xref:System.ServiceModel.Channels.SecurityBindingElement> class.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="70bfa-294">Serializa sempre wsse:TimeStamp com wsse: criados e wsse: campos de expirar.</span><span class="sxs-lookup"><span data-stu-id="70bfa-294"> always serializes wsse:TimeStamp with wsse:Created and wsse:Expires fields.</span></span> <span data-ttu-id="70bfa-295">O wsse:TimeStamp sempre é assinado quando a assinatura é usada.</span><span class="sxs-lookup"><span data-stu-id="70bfa-295">The wsse:TimeStamp is always signed when signing is used.</span></span>  
  
### <a name="22-protection-order"></a><span data-ttu-id="70bfa-296">2.2 ordem de proteção</span><span class="sxs-lookup"><span data-stu-id="70bfa-296">2.2 Protection Order</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="70bfa-297">dá suporte a ordem de proteção de mensagem "Logon antes de criptografar" e "Criptografar antes de inscrever-se" (1.1 de política de segurança).</span><span class="sxs-lookup"><span data-stu-id="70bfa-297"> supports the message protection order "Sign Before Encrypt" and "Encrypt Before Sign" (Security Policy 1.1).</span></span> <span data-ttu-id="70bfa-298">"Entrar antes de criptografar" é recomendado por motivos como: mensagens protegidas com criptografar antes de sinal estão sujeitos a ataques de substituição de assinatura a menos que o mecanismo do WS-Security 1.1 SignatureConfirmation for usado, e faz com que uma assinatura sobre conteúdo criptografado auditoria mais difícil.</span><span class="sxs-lookup"><span data-stu-id="70bfa-298">"Sign Before Encrypt" is recommended for reasons including: messages protected with Encrypt Before Sign are open to signature substitution attacks unless the WS-Security 1.1 SignatureConfirmation mechanism is used, and a signature over encrypted content makes auditing harder.</span></span>  
  
### <a name="23-signature-protection"></a><span data-ttu-id="70bfa-299">2.3 proteção de assinatura</span><span class="sxs-lookup"><span data-stu-id="70bfa-299">2.3 Signature Protection</span></span>  
 <span data-ttu-id="70bfa-300">Quando criptografar antes de logon é usado, é recomendável para proteger a assinatura para evitar ataques de força bruta para adivinhar o conteúdo criptografado ou a chave de assinatura (especialmente quando um token personalizado é usado com material de chave fraca).</span><span class="sxs-lookup"><span data-stu-id="70bfa-300">When Encrypt Before Sign is used, it is recommended to protect the signature to prevent brute force attacks for guessing the encrypted content or the signing key (especially when a custom token is used with weak key material).</span></span>  
  
### <a name="24-algorithm-suite"></a><span data-ttu-id="70bfa-301">2.4 conjunto de algoritmos de</span><span class="sxs-lookup"><span data-stu-id="70bfa-301">2.4 Algorithm Suite</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="70bfa-302">oferece suporte a todos os conjuntos de algoritmo listados na 1.1 de política de segurança.</span><span class="sxs-lookup"><span data-stu-id="70bfa-302"> supports all algorithm suites listed in Security Policy 1.1.</span></span>  
  
### <a name="25-key-derivation"></a><span data-ttu-id="70bfa-303">2.5 derivação de chave</span><span class="sxs-lookup"><span data-stu-id="70bfa-303">2.5 Key Derivation</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="70bfa-304">usa "Derivação de chave para chaves simétricas", conforme descrito em WS-SecureConversation.</span><span class="sxs-lookup"><span data-stu-id="70bfa-304"> uses "Key Derivation for symmetric keys" as described in WS-SecureConversation.</span></span>  
  
### <a name="26-signature-confirmation"></a><span data-ttu-id="70bfa-305">2.6 confirmação de assinatura</span><span class="sxs-lookup"><span data-stu-id="70bfa-305">2.6 Signature Confirmation</span></span>  
 <span data-ttu-id="70bfa-306">Confirmação de assinatura pode ser como proteção contra ataques intermediária para proteger o conjunto de assinaturas.</span><span class="sxs-lookup"><span data-stu-id="70bfa-306">Signature confirmation can be as protection from middle man attacks to protect the set of signatures.</span></span>  
  
### <a name="27-security-header-layout"></a><span data-ttu-id="70bfa-307">2.7 Layout de cabeçalho de segurança</span><span class="sxs-lookup"><span data-stu-id="70bfa-307">2.7 Security Header Layout</span></span>  
 <span data-ttu-id="70bfa-308">Cada modo de autenticação descreve um determinado layout para o cabeçalho de segurança.</span><span class="sxs-lookup"><span data-stu-id="70bfa-308">Each authentication mode describes a certain layout for the security header.</span></span> <span data-ttu-id="70bfa-309">Elementos dentro do cabeçalho de segurança são ordenados semi-estruturados.</span><span class="sxs-lookup"><span data-stu-id="70bfa-309">Elements within the security header are semi-ordered.</span></span> <span data-ttu-id="70bfa-310">Para definir a ordem dos elementos de filhos do cabeçalho de segurança, WS-Security Policy define os seguintes modos de layout de cabeçalho de segurança:</span><span class="sxs-lookup"><span data-stu-id="70bfa-310">To define the order of security header child elements, WS-Security Policy defines the following security header layout modes:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="70bfa-311">Estrito</span><span class="sxs-lookup"><span data-stu-id="70bfa-311">Strict</span></span>|<span data-ttu-id="70bfa-312">Itens são adicionados para o seguinte cabeçalho de segurança, que as regras de layout numerados descrito na seção 7.7.1 de acordo com um geral de política de segurança princípio de "declarar antes do uso".</span><span class="sxs-lookup"><span data-stu-id="70bfa-312">Items are added to the security header following the numbered layout rules described in Security Policy section 7.7.1 according to a general principle of "declare before use".</span></span>|  
|<span data-ttu-id="70bfa-313">Incerta</span><span class="sxs-lookup"><span data-stu-id="70bfa-313">Lax</span></span>|<span data-ttu-id="70bfa-314">Itens são adicionados ao cabeçalho de segurança em qualquer ordem compatível com WSS: segurança de mensagens SOAP.</span><span class="sxs-lookup"><span data-stu-id="70bfa-314">Items are added to the security header in any order that conforms to WSS: SOAP Message Security.</span></span>|  
|<span data-ttu-id="70bfa-315">LaxTimestampFirst</span><span class="sxs-lookup"><span data-stu-id="70bfa-315">LaxTimestampFirst</span></span>|<span data-ttu-id="70bfa-316">Mesmo como Lax exceto que o primeiro item no cabeçalho de segurança deve ser um wsse:Timestamp</span><span class="sxs-lookup"><span data-stu-id="70bfa-316">Same as Lax except that the first item in the security header must be a wsse:Timestamp</span></span>|  
|<span data-ttu-id="70bfa-317">LaxTimestampLast</span><span class="sxs-lookup"><span data-stu-id="70bfa-317">LaxTimestampLast</span></span>|<span data-ttu-id="70bfa-318">Mesmo que incerta exceto que o último item no cabeçalho de segurança deve ser um wsse:Timestamp</span><span class="sxs-lookup"><span data-stu-id="70bfa-318">Same as lax except that the last item in the security header must be a wsse:Timestamp</span></span>|  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="70bfa-319">oferece suporte a todos os quatro modos de layout de cabeçalho de segurança.</span><span class="sxs-lookup"><span data-stu-id="70bfa-319"> supports all four modes for security header layout.</span></span> <span data-ttu-id="70bfa-320">Exemplos de estrutura e a mensagem de cabeçalho de segurança para os modos de autenticação abaixo siga o modo de "Strict".</span><span class="sxs-lookup"><span data-stu-id="70bfa-320">Security header structure and message examples for authentication modes below follow the "Strict" mode.</span></span>  
  
## <a name="2-common-message-security-parameters"></a><span data-ttu-id="70bfa-321">2. Parâmetros comuns de segurança de mensagem</span><span class="sxs-lookup"><span data-stu-id="70bfa-321">2. Common Message Security Parameters</span></span>  
 <span data-ttu-id="70bfa-322">Esta seção fornece as políticas de exemplo para cada modo de autenticação junto com exemplos mostrando a estrutura de cabeçalho de segurança em mensagens trocadas por cliente e de serviço.</span><span class="sxs-lookup"><span data-stu-id="70bfa-322">This section provides example policies for each authentication mode along with examples showing security header structure in messages exchanged by client and service.</span></span>  
  
### <a name="61-transport-protection"></a><span data-ttu-id="70bfa-323">6.1 proteção de transporte</span><span class="sxs-lookup"><span data-stu-id="70bfa-323">6.1 Transport Protection</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="70bfa-324">fornece cinco modos de autenticação que usam um transporte seguro para proteger as mensagens; UserNameOverTransport, CertificateOverTransport, KerberosOverTransport, IssuedTokenOverTransport e SspiNegotiatedOverTransport.</span><span class="sxs-lookup"><span data-stu-id="70bfa-324"> provides five authentication modes that use secure transport to protect messages; UserNameOverTransport, CertificateOverTransport, KerberosOverTransport, IssuedTokenOverTransport and SspiNegotiatedOverTransport.</span></span>  
  
 <span data-ttu-id="70bfa-325">Esses modos de autenticação são construídos usando a associação de transporte descrita em SecurityPolicy.</span><span class="sxs-lookup"><span data-stu-id="70bfa-325">These authentication modes are constructed using the transport binding described in SecurityPolicy.</span></span> <span data-ttu-id="70bfa-326">Para o UserNameOverTransport UsernameToken o modo de autenticação é um token de suporte assinado.</span><span class="sxs-lookup"><span data-stu-id="70bfa-326">For the UserNameOverTransport authentication mode the UsernameToken is a signed supporting token.</span></span> <span data-ttu-id="70bfa-327">Para outros modos de autenticação de token aparece como um token de endosso assinado.</span><span class="sxs-lookup"><span data-stu-id="70bfa-327">For the other authentication modes the token appears as a signed endorsing token.</span></span> <span data-ttu-id="70bfa-328">Apêndice C.1.2 e C.1.3 de SecurityPolicy descrevem o layout do cabeçalho de segurança em detalhes.</span><span class="sxs-lookup"><span data-stu-id="70bfa-328">Appendix C.1.2 and C.1.3 of SecurityPolicy describe the security header layout in detail.</span></span> <span data-ttu-id="70bfa-329">Os cabeçalhos de segurança de exemplo a seguir mostram o layout estrito para um modo de autenticação específico.</span><span class="sxs-lookup"><span data-stu-id="70bfa-329">The following example security headers show the Strict layout for a given authentication mode.</span></span>  
  
 <span data-ttu-id="70bfa-330">O valor da propriedade "Chaves derivadas" para os tokens em todos os casos é "false".</span><span class="sxs-lookup"><span data-stu-id="70bfa-330">The value of the "Derived Keys" property for the tokens in all cases is "false".</span></span>  
  
 <span data-ttu-id="70bfa-331">Os valores de várias propriedades da associação de transporte são da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="70bfa-331">The values of the various properties of the transport binding are as follows:</span></span>  
  
 <span data-ttu-id="70bfa-332">Carimbo de hora: true</span><span class="sxs-lookup"><span data-stu-id="70bfa-332">Timestamp: true</span></span>  
  
 <span data-ttu-id="70bfa-333">Layout de cabeçalho de segurança: estrito</span><span class="sxs-lookup"><span data-stu-id="70bfa-333">Security Header Layout: Strict</span></span>  
  
 <span data-ttu-id="70bfa-334">Conjunto de algoritmos: Basic256</span><span class="sxs-lookup"><span data-stu-id="70bfa-334">Algorithm Suite: Basic256</span></span>  
  
#### <a name="611-usernameovertransport"></a><span data-ttu-id="70bfa-335">6.1.1 UsernameOverTransport</span><span class="sxs-lookup"><span data-stu-id="70bfa-335">6.1.1 UsernameOverTransport</span></span>  
 <span data-ttu-id="70bfa-336">Com esse modo de autenticação, o cliente autentica com um Token de nome de usuário que aparece na camada de SOAP como um token de suporte assinado que é sempre enviado do iniciador para o destinatário.</span><span class="sxs-lookup"><span data-stu-id="70bfa-336">With this authentication mode, the client authenticates with a Username Token which appears at the SOAP layer as a signed supporting token that is always sent from the initiator to the recipient.</span></span> <span data-ttu-id="70bfa-337">O serviço é autenticado usando um certificado x. 509 na camada de transporte.</span><span class="sxs-lookup"><span data-stu-id="70bfa-337">The service is authenticated using an X.509 certificate at the transport layer.</span></span> <span data-ttu-id="70bfa-338">A associação usada é uma associação de transporte.</span><span class="sxs-lookup"><span data-stu-id="70bfa-338">The binding used is a transport binding.</span></span>  
  
 <span data-ttu-id="70bfa-339">Política</span><span class="sxs-lookup"><span data-stu-id="70bfa-339">Policy</span></span>  
  
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
  
 <span data-ttu-id="70bfa-340">Layout de cabeçalho de segurança</span><span class="sxs-lookup"><span data-stu-id="70bfa-340">Security Header Layout</span></span>  
  
 <span data-ttu-id="70bfa-341">Solicitação</span><span class="sxs-lookup"><span data-stu-id="70bfa-341">Request</span></span>  
  
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
  
 <span data-ttu-id="70bfa-342">Resposta</span><span class="sxs-lookup"><span data-stu-id="70bfa-342">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
#### <a name="612-certificateovertransport"></a><span data-ttu-id="70bfa-343">6.1.2 CertificateOverTransport</span><span class="sxs-lookup"><span data-stu-id="70bfa-343">6.1.2 CertificateOverTransport</span></span>  
 <span data-ttu-id="70bfa-344">Com esse modo de autenticação que o cliente autentica com um x. 509 do certificado que aparece na camada de SOAP como um token de suporte de endosso que é sempre enviado do iniciador para o destinatário.</span><span class="sxs-lookup"><span data-stu-id="70bfa-344">With this authentication mode the client authenticates using an X.509 certificate which appears at the SOAP layer as an endorsing supporting token that is always sent from the initiator to the recipient.</span></span> <span data-ttu-id="70bfa-345">O serviço é autenticado usando um certificado x. 509 na camada de transporte.</span><span class="sxs-lookup"><span data-stu-id="70bfa-345">The service is authenticated using an X.509 certificate at the transport layer.</span></span> <span data-ttu-id="70bfa-346">A associação usada é uma associação de transporte.</span><span class="sxs-lookup"><span data-stu-id="70bfa-346">The binding used is a transport binding.</span></span>  
  
 <span data-ttu-id="70bfa-347">Política</span><span class="sxs-lookup"><span data-stu-id="70bfa-347">Policy</span></span>  
  
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
  
 <span data-ttu-id="70bfa-348">Layout de cabeçalho de segurança</span><span class="sxs-lookup"><span data-stu-id="70bfa-348">Security Header Layout</span></span>  
  
 <span data-ttu-id="70bfa-349">Solicitação</span><span class="sxs-lookup"><span data-stu-id="70bfa-349">Request</span></span>  
  
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
  
 <span data-ttu-id="70bfa-350">Resposta</span><span class="sxs-lookup"><span data-stu-id="70bfa-350">Response</span></span>  
  
```xml  
<o:Security>  
  <u:Timestamp u:Id="_0">  
  ...  
  </u:Timestamp>  
</o:Security>  
```  
  
#### <a name="613-issuedtokenovertransport"></a><span data-ttu-id="70bfa-351">6.1.3 IssuedTokenOverTransport</span><span class="sxs-lookup"><span data-stu-id="70bfa-351">6.1.3 IssuedTokenOverTransport</span></span>  
 <span data-ttu-id="70bfa-352">Com esse modo de autenticação o cliente não autentica para o serviço, como tal, mas em vez disso, apresenta um token emitido por um Token de segurança Service (STS) e comprova conhecimento de uma chave compartilhada.</span><span class="sxs-lookup"><span data-stu-id="70bfa-352">With this authentication mode the client does not authenticate to the service, as such, but rather presents a token issued by a Security Token Service (STS) and proves knowledge of a shared key.</span></span> <span data-ttu-id="70bfa-353">O token emitido é exibido na camada de SOAP como um token de suporte de endosso que é sempre enviado do iniciador para o destinatário.</span><span class="sxs-lookup"><span data-stu-id="70bfa-353">The issued token appears at the SOAP layer as an endorsing supporting token that is always sent from the initiator to the recipient.</span></span> <span data-ttu-id="70bfa-354">O serviço é autenticado usando um certificado x. 509 na camada de transporte.</span><span class="sxs-lookup"><span data-stu-id="70bfa-354">The service is authenticated using an X.509 certificate at the transport layer.</span></span> <span data-ttu-id="70bfa-355">A associação é uma associação de transporte.</span><span class="sxs-lookup"><span data-stu-id="70bfa-355">The binding is a transport binding.</span></span>  
  
 <span data-ttu-id="70bfa-356">Política</span><span class="sxs-lookup"><span data-stu-id="70bfa-356">Policy</span></span>  
  
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
  
 <span data-ttu-id="70bfa-357">Layout de cabeçalho de segurança</span><span class="sxs-lookup"><span data-stu-id="70bfa-357">Security Header Layout</span></span>  
  
 <span data-ttu-id="70bfa-358">Solicitação</span><span class="sxs-lookup"><span data-stu-id="70bfa-358">Request</span></span>  
  
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
  
 <span data-ttu-id="70bfa-359">Resposta</span><span class="sxs-lookup"><span data-stu-id="70bfa-359">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
#### <a name="614-kerberosovertransport"></a><span data-ttu-id="70bfa-360">6.1.4 KerberosOverTransport</span><span class="sxs-lookup"><span data-stu-id="70bfa-360">6.1.4 KerberosOverTransport</span></span>  
 <span data-ttu-id="70bfa-361">Com esse modo de autenticação o cliente autentica para o serviço usando um tíquete Kerberos.</span><span class="sxs-lookup"><span data-stu-id="70bfa-361">With this authentication mode the client authenticates to the service using a Kerberos ticket.</span></span> <span data-ttu-id="70bfa-362">O token Kerberos aparece na camada de SOAP como um token de suporte de endosso.</span><span class="sxs-lookup"><span data-stu-id="70bfa-362">The Kerberos token appears at the SOAP layer as an endorsing supporting token.</span></span> <span data-ttu-id="70bfa-363">O serviço é autenticado usando um certificado x. 509 na camada de transporte.</span><span class="sxs-lookup"><span data-stu-id="70bfa-363">The service is authenticated using an X.509 certificate at the transport layer.</span></span> <span data-ttu-id="70bfa-364">A associação é uma associação de transporte.</span><span class="sxs-lookup"><span data-stu-id="70bfa-364">The binding is a transport binding.</span></span>  
  
 <span data-ttu-id="70bfa-365">Política</span><span class="sxs-lookup"><span data-stu-id="70bfa-365">Policy</span></span>  
  
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
  
 <span data-ttu-id="70bfa-366">Layout de cabeçalho de segurança</span><span class="sxs-lookup"><span data-stu-id="70bfa-366">Security Header Layout</span></span>  
  
 <span data-ttu-id="70bfa-367">Solicitação</span><span class="sxs-lookup"><span data-stu-id="70bfa-367">Request</span></span>  
  
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
  
 <span data-ttu-id="70bfa-368">Resposta</span><span class="sxs-lookup"><span data-stu-id="70bfa-368">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
#### <a name="615-sspinegotiatedovertransport"></a><span data-ttu-id="70bfa-369">6.1.5 SspiNegotiatedOverTransport</span><span class="sxs-lookup"><span data-stu-id="70bfa-369">6.1.5 SspiNegotiatedOverTransport</span></span>  
 <span data-ttu-id="70bfa-370">Com esse modo, um protocolo de negociação é usado para realizar a autenticação de cliente e servidor.</span><span class="sxs-lookup"><span data-stu-id="70bfa-370">With this mode a negotiation protocol is used to perform client and server authentication.</span></span> <span data-ttu-id="70bfa-371">Kerberos é usado, se possível, caso contrário NTLM.</span><span class="sxs-lookup"><span data-stu-id="70bfa-371">Kerberos is used if possible, otherwise NTLM.</span></span> <span data-ttu-id="70bfa-372">O SCT resultante aparece na camada de SOAP como um token de suporte de endosso que é sempre enviado do iniciador ao destinatário.</span><span class="sxs-lookup"><span data-stu-id="70bfa-372">The resulting SCT appears at the SOAP layer as an endorsing supporting token that is always sent from initiator to recipient.</span></span> <span data-ttu-id="70bfa-373">Além disso, o serviço é autenticado na camada de transporte por um certificado x. 509.</span><span class="sxs-lookup"><span data-stu-id="70bfa-373">The service is additionally authenticated at the transport layer by an X.509 certificate.</span></span> <span data-ttu-id="70bfa-374">A associação usada é uma associação de transporte.</span><span class="sxs-lookup"><span data-stu-id="70bfa-374">The binding used is a transport binding.</span></span> <span data-ttu-id="70bfa-375">"SPNEGO" (negociação) descreve como [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usa o protocolo de negociação binária SSPI com WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="70bfa-375">"SPNEGO" (negotiation) describes how [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uses SSPI binary negotiation protocol with WS-Trust.</span></span> <span data-ttu-id="70bfa-376">Exemplos de cabeçalho de segurança nesta seção são depois que o SCT foi estabelecida por meio de handshake SPNEGO.</span><span class="sxs-lookup"><span data-stu-id="70bfa-376">Security header examples in this section are after the SCT has been established through the SPNEGO handshake.</span></span>  
  
 <span data-ttu-id="70bfa-377">Política</span><span class="sxs-lookup"><span data-stu-id="70bfa-377">Policy</span></span>  
  
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
  
### <a name="security-header-examples"></a><span data-ttu-id="70bfa-378">Exemplos de cabeçalho de segurança</span><span class="sxs-lookup"><span data-stu-id="70bfa-378">Security Header Examples</span></span>  
 <span data-ttu-id="70bfa-379">Quando o Token de contexto de segurança é estabelecido por meio de handshake SPNEGO usando negociação binária do WS-Trust, as mensagens de aplicativo têm cabeçalhos de segurança com a seguinte estrutura.</span><span class="sxs-lookup"><span data-stu-id="70bfa-379">Once the Security Context Token is established through SPNEGO handshake using WS-Trust Binary Negotiation, the application messages have security headers with the following structure.</span></span>  
  
 <span data-ttu-id="70bfa-380">Solicitação</span><span class="sxs-lookup"><span data-stu-id="70bfa-380">Request</span></span>  
  
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
  
 <span data-ttu-id="70bfa-381">Resposta</span><span class="sxs-lookup"><span data-stu-id="70bfa-381">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
### <a name="62-using-x509-certificates-for-service-authentication"></a><span data-ttu-id="70bfa-382">6.2 usando certificados x. 509 para autenticação de serviço</span><span class="sxs-lookup"><span data-stu-id="70bfa-382">6.2 Using X.509 Certificates for Service Authentication</span></span>  
 <span data-ttu-id="70bfa-383">Esta seção descreve os seguintes modos de autenticação: MutualCertificate WSS1.0, CertificateDuplex mútua, MutualCertificate WSS1.1, AnonymousForCertificate, UserNameForCertificate e IssuedTokenForCertificate.</span><span class="sxs-lookup"><span data-stu-id="70bfa-383">This section describes the following authentication modes: MutualCertificate WSS1.0, Mutual CertificateDuplex, MutualCertificate WSS1.1, AnonymousForCertificate, UserNameForCertificate and IssuedTokenForCertificate.</span></span>  
  
#### <a name="621-mutualcertificate-wss10"></a><span data-ttu-id="70bfa-384">6.2.1 MutualCertificate WSS1.0</span><span class="sxs-lookup"><span data-stu-id="70bfa-384">6.2.1 MutualCertificate WSS1.0</span></span>  
 <span data-ttu-id="70bfa-385">Com esse modo de autenticação que o cliente autentica com um x. 509 do certificado que aparece na camada de SOAP que o token de iniciador.</span><span class="sxs-lookup"><span data-stu-id="70bfa-385">With this authentication mode the client authenticates using an X.509 certificate which appears at the SOAP layer as the initiator token.</span></span> <span data-ttu-id="70bfa-386">O serviço também é autenticado usando um certificado x. 509.</span><span class="sxs-lookup"><span data-stu-id="70bfa-386">The service is also authenticated using an X.509 certificate.</span></span>  
  
 <span data-ttu-id="70bfa-387">A associação usada é uma associação assimétrica com os seguintes valores de propriedade:</span><span class="sxs-lookup"><span data-stu-id="70bfa-387">The binding used is an asymmetric binding with the following property values:</span></span>  
  
 <span data-ttu-id="70bfa-388">Token de iniciador: o certificado do cliente x. 509, com o modo de inclusão definido como .../IncludeToken/AlwaysToRecipient</span><span class="sxs-lookup"><span data-stu-id="70bfa-388">Initiator Token: the client’s X.509 certificate, with inclusion mode set to …/IncludeToken/AlwaysToRecipient</span></span>  
  
 <span data-ttu-id="70bfa-389">Token de destinatário: Servidor do certificado x. 509, com o modo de inclusão é definido .../IncludeToken/Never</span><span class="sxs-lookup"><span data-stu-id="70bfa-389">Recipient Token: Server’s X.509 Certificate, with inclusion mode is set …/IncludeToken/Never</span></span>  
  
 <span data-ttu-id="70bfa-390">Proteção de token: False</span><span class="sxs-lookup"><span data-stu-id="70bfa-390">Token Protection: False</span></span>  
  
 <span data-ttu-id="70bfa-391">Todo cabeçalho e corpo assinaturas: True</span><span class="sxs-lookup"><span data-stu-id="70bfa-391">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="70bfa-392">Ordem de proteção: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="70bfa-392">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="70bfa-393">Criptografar assinatura: True</span><span class="sxs-lookup"><span data-stu-id="70bfa-393">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="70bfa-394">Política</span><span class="sxs-lookup"><span data-stu-id="70bfa-394">Policy</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="70bfa-395">Exemplos de cabeçalho de segurança: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="70bfa-395">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="70bfa-396">Solicitação</span><span class="sxs-lookup"><span data-stu-id="70bfa-396">Request</span></span>  
  
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
  
 <span data-ttu-id="70bfa-397">Resposta</span><span class="sxs-lookup"><span data-stu-id="70bfa-397">Response</span></span>  
  
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
  
 <span data-ttu-id="70bfa-398">Exemplos de cabeçalho de segurança: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="70bfa-398">Security Header Examples: EncryptBeforeSign</span></span>  
  
 <span data-ttu-id="70bfa-399">Solicitação</span><span class="sxs-lookup"><span data-stu-id="70bfa-399">Request</span></span>  
  
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
  
 <span data-ttu-id="70bfa-400">Resposta</span><span class="sxs-lookup"><span data-stu-id="70bfa-400">Response</span></span>  
  
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
  
#### <a name="622-mutualcertificateduplex"></a><span data-ttu-id="70bfa-401">6.2.2 MutualCertificateDuplex</span><span class="sxs-lookup"><span data-stu-id="70bfa-401">6.2.2 MutualCertificateDuplex</span></span>  
 <span data-ttu-id="70bfa-402">Com esse modo de autenticação que o cliente autentica com um x. 509 do certificado que aparece na camada de SOAP que o token de iniciador.</span><span class="sxs-lookup"><span data-stu-id="70bfa-402">With this authentication mode the client authenticates using an X.509 certificate which appears at the SOAP layer as the initiator token.</span></span> <span data-ttu-id="70bfa-403">O serviço também é autenticado usando um certificado x. 509.</span><span class="sxs-lookup"><span data-stu-id="70bfa-403">The service is also authenticated using an X.509 certificate.</span></span>  
  
 <span data-ttu-id="70bfa-404">A associação usada é uma associação assimétrica com os seguintes valores de propriedade:</span><span class="sxs-lookup"><span data-stu-id="70bfa-404">The binding used is an asymmetric binding with the following property values:</span></span>  
  
 <span data-ttu-id="70bfa-405">Token de iniciador: X509 do cliente certificado, o modo de inclusão estiver definido como .../IncludeToken/AlwaysToRecipient</span><span class="sxs-lookup"><span data-stu-id="70bfa-405">Initiator Token: Client’s X509 Certificate, inclusion mode is set to …/IncludeToken/AlwaysToRecipient</span></span>  
  
 <span data-ttu-id="70bfa-406">Token de destinatário: X509 do servidor certificado, o modo de inclusão estiver definido como .../IncludeToken/AlwaysToInitiator</span><span class="sxs-lookup"><span data-stu-id="70bfa-406">Recipient Token: Server’s X509 Certificate, inclusion mode is set to …/IncludeToken/AlwaysToInitiator</span></span>  
  
 <span data-ttu-id="70bfa-407">Proteção de token: False</span><span class="sxs-lookup"><span data-stu-id="70bfa-407">Token Protection: False</span></span>  
  
 <span data-ttu-id="70bfa-408">Todo cabeçalho e corpo assinaturas: True</span><span class="sxs-lookup"><span data-stu-id="70bfa-408">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="70bfa-409">Ordem de proteção: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="70bfa-409">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="70bfa-410">Criptografar assinatura: True</span><span class="sxs-lookup"><span data-stu-id="70bfa-410">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="70bfa-411">Política</span><span class="sxs-lookup"><span data-stu-id="70bfa-411">Policy</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="70bfa-412">Exemplos de cabeçalho de segurança: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="70bfa-412">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="70bfa-413">Solicitação e resposta</span><span class="sxs-lookup"><span data-stu-id="70bfa-413">Request and Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="70bfa-414">Exemplos de cabeçalho de segurança: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="70bfa-414">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="70bfa-415">Solicitação e resposta</span><span class="sxs-lookup"><span data-stu-id="70bfa-415">Request and Response</span></span>  
  
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
  
#### <a name="623-using-symmetricbinding-with-x509-service-authentication"></a><span data-ttu-id="70bfa-416">6.2.3 usando SymmetricBinding com a autenticação do serviço x. 509</span><span class="sxs-lookup"><span data-stu-id="70bfa-416">6.2.3 Using SymmetricBinding with X.509 Service Authentication</span></span>  
 <span data-ttu-id="70bfa-417">"WSS10" fornecido suporte limitado para cenários com X509 tokens.</span><span class="sxs-lookup"><span data-stu-id="70bfa-417">"WSS10" provided limited support for scenarios with X509 tokens.</span></span> <span data-ttu-id="70bfa-418">Por exemplo, não havia uma maneira para fornecer proteção de assinatura e criptografia de mensagens usando apenas o token de serviço X509.</span><span class="sxs-lookup"><span data-stu-id="70bfa-418">For example, there was no way to provide signature and encryption protection for messages using only service X509 token.</span></span> <span data-ttu-id="70bfa-419">"WSS11" introduziu o uso de EncryptedKey como um token simétrico.</span><span class="sxs-lookup"><span data-stu-id="70bfa-419">"WSS11" introduced the usage of EncryptedKey as a symmetric token.</span></span> <span data-ttu-id="70bfa-420">Agora, uma chave temporária criptografada para o certificado de x. 509 do serviço pode ser usada para proteção de mensagens de solicitação e resposta.</span><span class="sxs-lookup"><span data-stu-id="70bfa-420">Now a temporary key encrypted for the service's X.509 certificate could be used for both request and response messages protection.</span></span> <span data-ttu-id="70bfa-421">Os modos de autenticação descritos na seção 6.4 abaixo usam esse padrão.</span><span class="sxs-lookup"><span data-stu-id="70bfa-421">The authentication modes described in the section 6.4 below use this pattern.</span></span>  
  
 <span data-ttu-id="70bfa-422">O WS-SecurityPolicy descreve esse padrão usando SymmetricBinding com o serviço de token X509 como o token de proteção.</span><span class="sxs-lookup"><span data-stu-id="70bfa-422">WS-SecurityPolicy describes this pattern using SymmetricBinding with Service X509 token as the protection token.</span></span>  
  
 <span data-ttu-id="70bfa-423">Modos de autenticação AnonymousForCertificate, UsernameForCertificate, MutualCertificate WSS11 e IssuedTokenForCertificate todos usam uma instância semelhante de sp:SymmetricBinding com os seguintes valores de propriedade:</span><span class="sxs-lookup"><span data-stu-id="70bfa-423">Authentication modes AnonymousForCertificate, UsernameForCertificate, MutualCertificate WSS11 and IssuedTokenForCertificate all use a similar instance of sp:SymmetricBinding with the following property values:</span></span>  
  
 <span data-ttu-id="70bfa-424">Token de proteção: X509 do servidor certificado, o modo de inclusão estiver definido como .../IncludeToken/Never</span><span class="sxs-lookup"><span data-stu-id="70bfa-424">Protection Token: Server’s X509 Certificate, inclusion mode is set to .../IncludeToken/Never</span></span>  
<span data-ttu-id="70bfa-425">Proteção de token: False</span><span class="sxs-lookup"><span data-stu-id="70bfa-425">Token Protection: False</span></span>  
  
 <span data-ttu-id="70bfa-426">Todo cabeçalho e corpo assinaturas: True</span><span class="sxs-lookup"><span data-stu-id="70bfa-426">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="70bfa-427">Ordem de proteção: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="70bfa-427">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="70bfa-428">Criptografar assinatura: True</span><span class="sxs-lookup"><span data-stu-id="70bfa-428">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="70bfa-429">Os modos de autenticação acima diferem apenas por tokens de suporte que eles usam.</span><span class="sxs-lookup"><span data-stu-id="70bfa-429">The above authentication modes only differ by the supporting tokens they use.</span></span> <span data-ttu-id="70bfa-430">AnonymousForCertificate não tem todos os tokens de suporte, MutualCertificate WSS 1.1 tem o cliente do certificado X509 como um endossando dar suporte a tokens, UserNameForCertificate tem um Token de nome de usuário como um token de suporte assinado e IssuedTokenForCertificate tem o token emitido como um token de suporte de endosso.</span><span class="sxs-lookup"><span data-stu-id="70bfa-430">AnonymousForCertificate does not have any supporting tokens, MutualCertificate WSS 1.1 has the client’s X509 certificate as an endorsing supporting tokens, UserNameForCertificate has a UserName Token as a signed supporting token and IssuedTokenForCertificate has the issued token as an endorsing supporting token.</span></span>  
  
 <span data-ttu-id="70bfa-431">Política</span><span class="sxs-lookup"><span data-stu-id="70bfa-431">Policy</span></span>  
  
 <span data-ttu-id="70bfa-432">Vinculação simétrica</span><span class="sxs-lookup"><span data-stu-id="70bfa-432">Symmetric Binding</span></span>  
  
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
  
#### <a name="624-anonymousforcertificate"></a><span data-ttu-id="70bfa-433">6.2.4 AnonymousForCertificate</span><span class="sxs-lookup"><span data-stu-id="70bfa-433">6.2.4 AnonymousForCertificate</span></span>  
 <span data-ttu-id="70bfa-434">Com esse modo de autenticação o cliente é anônimo e o serviço é autenticado usando um certificado x. 509.</span><span class="sxs-lookup"><span data-stu-id="70bfa-434">With this authentication mode the client is anonymous and the service is authenticated using an X.509 certificate.</span></span> <span data-ttu-id="70bfa-435">A associação usada é uma instância de associação simétrica, conforme descrito em 6.4.2.</span><span class="sxs-lookup"><span data-stu-id="70bfa-435">The binding used is an instance of symmetric binding as described in 6.4.2.</span></span>  
  
 <span data-ttu-id="70bfa-436">Política</span><span class="sxs-lookup"><span data-stu-id="70bfa-436">Policy</span></span>  
  
 <span data-ttu-id="70bfa-437">Consulte "Política" 6.2.3 acima para obter detalhes de associação</span><span class="sxs-lookup"><span data-stu-id="70bfa-437">See "Policy" in 6.2.3 above for binding details</span></span>  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="70bfa-438">Exemplos de cabeçalho de segurança: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="70bfa-438">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="70bfa-439">Solicitação</span><span class="sxs-lookup"><span data-stu-id="70bfa-439">Request</span></span>  
  
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
  
 <span data-ttu-id="70bfa-440">Resposta</span><span class="sxs-lookup"><span data-stu-id="70bfa-440">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="70bfa-441">Exemplos de cabeçalho de segurança: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="70bfa-441">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="70bfa-442">Solicitação</span><span class="sxs-lookup"><span data-stu-id="70bfa-442">Request</span></span>  
  
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
  
 <span data-ttu-id="70bfa-443">Resposta</span><span class="sxs-lookup"><span data-stu-id="70bfa-443">Response</span></span>  
  
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
  
#### <a name="625-usernameforcertificate"></a><span data-ttu-id="70bfa-444">6.2.5 UserNameForCertificate</span><span class="sxs-lookup"><span data-stu-id="70bfa-444">6.2.5 UserNameForCertificate</span></span>  
 <span data-ttu-id="70bfa-445">Com esse modo de autenticação o cliente autentica para o serviço usando um Token de nome de usuário que aparece na camada de SOAP como um token de suporte assinado.</span><span class="sxs-lookup"><span data-stu-id="70bfa-445">With this authentication mode the client authenticates to the service using a Username Token which appears at the SOAP layer as a signed supporting token.</span></span> <span data-ttu-id="70bfa-446">O serviço autentica o cliente usando um certificado x. 509.</span><span class="sxs-lookup"><span data-stu-id="70bfa-446">The service authenticates to the client using an X.509 certificate.</span></span> <span data-ttu-id="70bfa-447">A associação usada é uma associação simétrica com o token de proteção sendo uma chave gerada pelo cliente, criptografado com a chave pública do serviço.</span><span class="sxs-lookup"><span data-stu-id="70bfa-447">The binding used is a symmetric binding with the protection token being a key generated by the client, encrypted with the public key of the service.</span></span>  
  
 <span data-ttu-id="70bfa-448">Política</span><span class="sxs-lookup"><span data-stu-id="70bfa-448">Policy</span></span>  
  
 <span data-ttu-id="70bfa-449">Consulte "Política" 6.2.3 acima para obter detalhes de associação</span><span class="sxs-lookup"><span data-stu-id="70bfa-449">See "Policy" in 6.2.3 above for binding details</span></span>  
  
 <span data-ttu-id="70bfa-450">Assinatura de Token de suporte</span><span class="sxs-lookup"><span data-stu-id="70bfa-450">Signed Supporting Token</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="70bfa-451">Exemplos de cabeçalho de segurança: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="70bfa-451">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="70bfa-452">Solicitação</span><span class="sxs-lookup"><span data-stu-id="70bfa-452">Request</span></span>  
  
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
  
 <span data-ttu-id="70bfa-453">Resposta</span><span class="sxs-lookup"><span data-stu-id="70bfa-453">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="70bfa-454">Exemplos de cabeçalho de segurança: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="70bfa-454">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="70bfa-455">Solicitação</span><span class="sxs-lookup"><span data-stu-id="70bfa-455">Request</span></span>  
  
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
  
 <span data-ttu-id="70bfa-456">Resposta</span><span class="sxs-lookup"><span data-stu-id="70bfa-456">Response</span></span>  
  
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
  
#### <a name="626-mutualcertificate-wss-11"></a><span data-ttu-id="70bfa-457">6.2.6 MutualCertificate (WSS 1.1)</span><span class="sxs-lookup"><span data-stu-id="70bfa-457">6.2.6 MutualCertificate (WSS 1.1)</span></span>  
 <span data-ttu-id="70bfa-458">Com esse modo de autenticação que o cliente autentica com um x. 509 do certificado que aparece na camada de SOAP como um token de suporte de endosso.</span><span class="sxs-lookup"><span data-stu-id="70bfa-458">With this authentication mode the client authenticates using an X.509 certificate which appears at the SOAP layer as an endorsing supporting token.</span></span> <span data-ttu-id="70bfa-459">O serviço também é autenticado usando um certificado x. 509.</span><span class="sxs-lookup"><span data-stu-id="70bfa-459">The service is also authenticated using an X.509 certificate.</span></span> <span data-ttu-id="70bfa-460">A associação usada é uma associação simétrica com o token de proteção sendo uma chave gerada pelo cliente, criptografado com a chave pública do serviço.</span><span class="sxs-lookup"><span data-stu-id="70bfa-460">The binding used is a symmetric binding with the protection token being a key generated by the client, encrypted with the public key of the service.</span></span>  
  
 <span data-ttu-id="70bfa-461">Política</span><span class="sxs-lookup"><span data-stu-id="70bfa-461">Policy</span></span>  
  
 <span data-ttu-id="70bfa-462">Consulte a política em 6.2.3 para os detalhes da associação</span><span class="sxs-lookup"><span data-stu-id="70bfa-462">See Policy in 6.2.3 for binding details</span></span>  
  
 <span data-ttu-id="70bfa-463">Endossando o Token de suporte</span><span class="sxs-lookup"><span data-stu-id="70bfa-463">Endorsing Supporting Token</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="70bfa-464">Exemplos de cabeçalho de segurança: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="70bfa-464">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="70bfa-465">Solicitação</span><span class="sxs-lookup"><span data-stu-id="70bfa-465">Request</span></span>  
  
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
  
 <span data-ttu-id="70bfa-466">Resposta</span><span class="sxs-lookup"><span data-stu-id="70bfa-466">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="70bfa-467">Exemplos de cabeçalho de segurança: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="70bfa-467">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="70bfa-468">Solicitação</span><span class="sxs-lookup"><span data-stu-id="70bfa-468">Request</span></span>  
  
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
  
 <span data-ttu-id="70bfa-469">Resposta</span><span class="sxs-lookup"><span data-stu-id="70bfa-469">Response</span></span>  
  
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
  
#### <a name="627-issuedtokenforcertificate"></a><span data-ttu-id="70bfa-470">6.2.7 IssuedTokenForCertificate</span><span class="sxs-lookup"><span data-stu-id="70bfa-470">6.2.7 IssuedTokenForCertificate</span></span>  
 <span data-ttu-id="70bfa-471">Com essa autenticação o cliente não autenticar para o serviço, como tal, mas em vez disso, o modo apresenta um token emitido por um STS e comprova conhecimento de uma chave compartilhada.</span><span class="sxs-lookup"><span data-stu-id="70bfa-471">With this authentication mode the client does not authenticate to the service, as such, but instead presents a token issued by a STS and proves knowledge of a shared key.</span></span> <span data-ttu-id="70bfa-472">O token emitido é exibido na camada de SOAP como um token de suporte de endosso.</span><span class="sxs-lookup"><span data-stu-id="70bfa-472">The issued token appears at the SOAP layer as an endorsing supporting token.</span></span> <span data-ttu-id="70bfa-473">O serviço autentica o cliente usando um certificado x. 509.</span><span class="sxs-lookup"><span data-stu-id="70bfa-473">The service authenticates to the client using an X.509 certificate.</span></span> <span data-ttu-id="70bfa-474">A associação usada é uma associação simétrica com o token de proteção sendo uma chave gerada pelo cliente, criptografado com a chave pública do serviço.</span><span class="sxs-lookup"><span data-stu-id="70bfa-474">The binding used is a symmetric binding with the protection token being a key generated by the client, encrypted with the public key of the service.</span></span>  
  
 <span data-ttu-id="70bfa-475">Política</span><span class="sxs-lookup"><span data-stu-id="70bfa-475">Policy</span></span>  
  
 <span data-ttu-id="70bfa-476">Consulte a política em 6.2.3 acima para obter detalhes de associação</span><span class="sxs-lookup"><span data-stu-id="70bfa-476">See Policy in 6.2.3 above for binding details</span></span>  
  
 <span data-ttu-id="70bfa-477">Endossando o Token de suporte</span><span class="sxs-lookup"><span data-stu-id="70bfa-477">Endorsing Supporting Token</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="70bfa-478">Exemplos de cabeçalho de segurança: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="70bfa-478">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="70bfa-479">Solicitação</span><span class="sxs-lookup"><span data-stu-id="70bfa-479">Request</span></span>  
  
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
  
 <span data-ttu-id="70bfa-480">Resposta</span><span class="sxs-lookup"><span data-stu-id="70bfa-480">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="70bfa-481">Exemplos de cabeçalho de segurança: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="70bfa-481">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="70bfa-482">Solicitação</span><span class="sxs-lookup"><span data-stu-id="70bfa-482">Request</span></span>  
  
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
  
 <span data-ttu-id="70bfa-483">Resposta</span><span class="sxs-lookup"><span data-stu-id="70bfa-483">Response</span></span>  
  
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
  
## <a name="63-kerberos"></a><span data-ttu-id="70bfa-484">6.3 Kerberos</span><span class="sxs-lookup"><span data-stu-id="70bfa-484">6.3 Kerberos</span></span>  
 <span data-ttu-id="70bfa-485">Com esse modo de autenticação o cliente autentica para o serviço usando um tíquete Kerberos.</span><span class="sxs-lookup"><span data-stu-id="70bfa-485">With this authentication mode the client authenticates to the service using a Kerberos ticket.</span></span> <span data-ttu-id="70bfa-486">Esse tíquete mesmo também fornece autenticação de servidor.</span><span class="sxs-lookup"><span data-stu-id="70bfa-486">That same ticket also provides server authentication.</span></span> <span data-ttu-id="70bfa-487">A associação usada é uma associação simétrica com as seguintes propriedades;</span><span class="sxs-lookup"><span data-stu-id="70bfa-487">The binding used is a symmetric binding with the following properties;</span></span>  
  
 <span data-ttu-id="70bfa-488">Token de proteção: Tíquete Kerberos, o modo de inclusão estiver definido como .../IncludeToken/Once</span><span class="sxs-lookup"><span data-stu-id="70bfa-488">Protection Token: Kerberos Ticket, inclusion mode is set to .../IncludeToken/Once</span></span>  
<span data-ttu-id="70bfa-489">Proteção de token: False</span><span class="sxs-lookup"><span data-stu-id="70bfa-489">Token Protection: False</span></span>  
  
 <span data-ttu-id="70bfa-490">Todo cabeçalho e corpo assinaturas: True</span><span class="sxs-lookup"><span data-stu-id="70bfa-490">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="70bfa-491">Ordem de proteção: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="70bfa-491">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="70bfa-492">Criptografar assinatura: True</span><span class="sxs-lookup"><span data-stu-id="70bfa-492">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="70bfa-493">Política</span><span class="sxs-lookup"><span data-stu-id="70bfa-493">Policy</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="70bfa-494">Exemplos de cabeçalho de segurança: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="70bfa-494">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="70bfa-495">Solicitação</span><span class="sxs-lookup"><span data-stu-id="70bfa-495">Request</span></span>  
  
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
  
 <span data-ttu-id="70bfa-496">Resposta</span><span class="sxs-lookup"><span data-stu-id="70bfa-496">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="70bfa-497">Exemplos de cabeçalho de segurança: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="70bfa-497">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="70bfa-498">Solicitação</span><span class="sxs-lookup"><span data-stu-id="70bfa-498">Request</span></span>  
  
```xml  
<wsse:Security>  
TBD  
</wsse:Security>  
```  
  
 <span data-ttu-id="70bfa-499">Resposta</span><span class="sxs-lookup"><span data-stu-id="70bfa-499">Response</span></span>  
  
```xml  
<wsse:Security>  
TBD  
</wsse:Security>  
```  
  
#### <a name="64-issuedtoken"></a><span data-ttu-id="70bfa-500">6.4 IssuedToken</span><span class="sxs-lookup"><span data-stu-id="70bfa-500">6.4 IssuedToken</span></span>  
 <span data-ttu-id="70bfa-501">Com esse modo de autenticação que o cliente não autenticar para o serviço, assim, em vez disso, o cliente apresenta um token emitido por um STS e comprova conhecimento de uma chave compartilhada.</span><span class="sxs-lookup"><span data-stu-id="70bfa-501">With this authentication mode the client does not authenticate to the service, as such, rather the client presents a token issued by an STS and proves knowledge of a shared key.</span></span> <span data-ttu-id="70bfa-502">O serviço não é autenticado para o cliente, como tal, em vez disso, o STS criptografa a chave compartilhada como parte do token emitido, de modo que apenas o serviço possa descriptografar a chave.</span><span class="sxs-lookup"><span data-stu-id="70bfa-502">The service is not authenticated to the client, as such, instead the STS encrypts the shared key as part of the issued token such that only the service can decrypt the key.</span></span> <span data-ttu-id="70bfa-503">A associação usada é simétrica associação com as seguintes propriedades;</span><span class="sxs-lookup"><span data-stu-id="70bfa-503">The binding used is as symmetric binding with the following properties;</span></span>  
  
 <span data-ttu-id="70bfa-504">Modo de inclusão de Token de proteção: O Token emitido, é definido como .../IncludeToken/AlwaysToRecipient</span><span class="sxs-lookup"><span data-stu-id="70bfa-504">Protection Token: Issued Token, inclusion mode is set to .../IncludeToken/AlwaysToRecipient</span></span>  
<span data-ttu-id="70bfa-505">Proteção de token: False</span><span class="sxs-lookup"><span data-stu-id="70bfa-505">Token Protection: False</span></span>  
  
 <span data-ttu-id="70bfa-506">Todo cabeçalho e corpo assinaturas: True</span><span class="sxs-lookup"><span data-stu-id="70bfa-506">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="70bfa-507">Ordem de proteção: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="70bfa-507">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="70bfa-508">Criptografar assinatura: True</span><span class="sxs-lookup"><span data-stu-id="70bfa-508">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="70bfa-509">Política</span><span class="sxs-lookup"><span data-stu-id="70bfa-509">Policy</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="70bfa-510">Exemplos de cabeçalho de segurança: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="70bfa-510">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="70bfa-511">Solicitação</span><span class="sxs-lookup"><span data-stu-id="70bfa-511">Request</span></span>  
  
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
  
 <span data-ttu-id="70bfa-512">Resposta</span><span class="sxs-lookup"><span data-stu-id="70bfa-512">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="70bfa-513">Exemplos de cabeçalho de segurança: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="70bfa-513">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="70bfa-514">Solicitação</span><span class="sxs-lookup"><span data-stu-id="70bfa-514">Request</span></span>  
  
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
  
 <span data-ttu-id="70bfa-515">Resposta</span><span class="sxs-lookup"><span data-stu-id="70bfa-515">Response</span></span>  
  
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
  
### <a name="65-using-sslnegotiated-for-service-authentication"></a><span data-ttu-id="70bfa-516">6.5 usando SslNegotiated para autenticação de serviço</span><span class="sxs-lookup"><span data-stu-id="70bfa-516">6.5 Using SslNegotiated for Service Authentication</span></span>  
 <span data-ttu-id="70bfa-517">Esta seção descreve um grupo de modos de autenticação que usa uma associação simétrica com o token de proteção sendo um Token de contexto de segurança por WS-SecureConversation (WS-SC) cujo valor da chave é negociado executando o protocolo TLS sobre WS-Trust (WS-F) primeira / Mensagens RSTR.</span><span class="sxs-lookup"><span data-stu-id="70bfa-517">This section describes a group of authentication modes that use a symmetric binding with the protection token being a Security Context Token per WS-SecureConversation (WS-SC) whose key value is negotiated by executing the TLS protocol over WS-Trust (WS-T) RST/RSTR messages.</span></span> <span data-ttu-id="70bfa-518">Detalhes da implementação de handshake TLS usando o WS-Trust são descritos em TLSNEGO.</span><span class="sxs-lookup"><span data-stu-id="70bfa-518">Details of the TLS handshake implementation using WS-Trust are described in TLSNEGO.</span></span> <span data-ttu-id="70bfa-519">Veja os exemplos de mensagem, vamos pressupor que SCT com um contexto de segurança associadas já está estabelecida por meio de um handshake.</span><span class="sxs-lookup"><span data-stu-id="70bfa-519">Here in the message examples we will assume that SCT with an associated security context is already established through a handshake.</span></span>  
  
 <span data-ttu-id="70bfa-520">A associação usada é uma associação simétrica com as seguintes propriedades;</span><span class="sxs-lookup"><span data-stu-id="70bfa-520">The binding used is a symmetric binding with the following properties;</span></span>  
  
 <span data-ttu-id="70bfa-521">Token de proteção: SslContextToken, modo de inclusão estiver definido como .../IncludeToken/Never</span><span class="sxs-lookup"><span data-stu-id="70bfa-521">Protection Token: SslContextToken, inclusion mode is set to .../IncludeToken/Never</span></span>  
<span data-ttu-id="70bfa-522">Proteção de token: False</span><span class="sxs-lookup"><span data-stu-id="70bfa-522">Token Protection: False</span></span>  
  
 <span data-ttu-id="70bfa-523">Todo cabeçalho e corpo assinaturas: True</span><span class="sxs-lookup"><span data-stu-id="70bfa-523">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="70bfa-524">Ordem de proteção: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="70bfa-524">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="70bfa-525">Criptografar assinatura: True</span><span class="sxs-lookup"><span data-stu-id="70bfa-525">Encrypt Signature: True</span></span>  
  
#### <a name="651-policy-for-sslnegotiated-service-authentication"></a><span data-ttu-id="70bfa-526">6.5.1 política de para autenticação do serviço SslNegotiated</span><span class="sxs-lookup"><span data-stu-id="70bfa-526">6.5.1 Policy for SslNegotiated service authentication</span></span>  
 <span data-ttu-id="70bfa-527">Política para todos os modos de autenticação nesta seção são semelhante e diferem apenas por específicas de suporte assinado ou endossando tokens usados.</span><span class="sxs-lookup"><span data-stu-id="70bfa-527">Policy for all authentication modes in this section are similar and differ only by specific signed supporting or endorsing tokens used.</span></span>  
  
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
  
#### <a name="652-anonymousforsslnegotiated"></a><span data-ttu-id="70bfa-528">6.5.2 AnonymousForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="70bfa-528">6.5.2 AnonymousForSslNegotiated</span></span>  
 <span data-ttu-id="70bfa-529">Com esse modo de autenticação o cliente é anônimo e o serviço é autenticado usando um certificado x. 509.</span><span class="sxs-lookup"><span data-stu-id="70bfa-529">With this authentication mode the client is anonymous and the service is authenticated using an X.509 certificate.</span></span> <span data-ttu-id="70bfa-530">A associação usada é uma instância de associação simétrica, conforme descrito em 6.5.1 acima.</span><span class="sxs-lookup"><span data-stu-id="70bfa-530">The binding used is an instance of symmetric binding as described in 6.5.1 above.</span></span>  
  
 <span data-ttu-id="70bfa-531">Política</span><span class="sxs-lookup"><span data-stu-id="70bfa-531">Policy</span></span>  
  
 <span data-ttu-id="70bfa-532">Consulte a política em 6.5.1 acima para obter detalhes de associação.</span><span class="sxs-lookup"><span data-stu-id="70bfa-532">See Policy in 6.5.1 above for binding details.</span></span>  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="70bfa-533">Exemplos de cabeçalho de segurança: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="70bfa-533">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="70bfa-534">Solicitação</span><span class="sxs-lookup"><span data-stu-id="70bfa-534">Request</span></span>  
  
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
  
 <span data-ttu-id="70bfa-535">Resposta</span><span class="sxs-lookup"><span data-stu-id="70bfa-535">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="70bfa-536">Exemplos de cabeçalho de segurança: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="70bfa-536">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="70bfa-537">Solicitação</span><span class="sxs-lookup"><span data-stu-id="70bfa-537">Request</span></span>  
  
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
  
 <span data-ttu-id="70bfa-538">Resposta</span><span class="sxs-lookup"><span data-stu-id="70bfa-538">Response</span></span>  
  
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
  
#### <a name="653-usernameforsslnegotiated"></a><span data-ttu-id="70bfa-539">6.5.3 UserNameForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="70bfa-539">6.5.3 UserNameForSslNegotiated</span></span>  
 <span data-ttu-id="70bfa-540">Com essa autenticação modo que é o cliente autentica usando um Token de nome de usuário que aparece na camada de SOAP como um token de suporte assinado.</span><span class="sxs-lookup"><span data-stu-id="70bfa-540">With this authentication mode the client is authenticates using a Username Token which appears at the SOAP layer as a signed supporting token.</span></span> <span data-ttu-id="70bfa-541">O serviço é autenticado usando um certificado x. 509.</span><span class="sxs-lookup"><span data-stu-id="70bfa-541">The service is authenticated using an X.509 certificate.</span></span> <span data-ttu-id="70bfa-542">A associação usada é uma instância de associação simétrica, conforme descrito em 6.5.1.</span><span class="sxs-lookup"><span data-stu-id="70bfa-542">The binding used is an instance of symmetric binding as described in 6.5.1.</span></span>  
  
 <span data-ttu-id="70bfa-543">Política</span><span class="sxs-lookup"><span data-stu-id="70bfa-543">Policy</span></span>  
  
 <span data-ttu-id="70bfa-544">Consulte a seção 6.5.1 acima para obter detalhes de associação</span><span class="sxs-lookup"><span data-stu-id="70bfa-544">See section 6.5.1 above for binding details</span></span>  
  
 <span data-ttu-id="70bfa-545">Assinatura de Token de suporte</span><span class="sxs-lookup"><span data-stu-id="70bfa-545">Signed Supporting Token</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="70bfa-546">Exemplos de cabeçalho de segurança: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="70bfa-546">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="70bfa-547">Solicitação</span><span class="sxs-lookup"><span data-stu-id="70bfa-547">Request</span></span>  
  
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
  
 <span data-ttu-id="70bfa-548">Resposta</span><span class="sxs-lookup"><span data-stu-id="70bfa-548">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="70bfa-549">Exemplos de cabeçalho de segurança: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="70bfa-549">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="70bfa-550">Solicitação</span><span class="sxs-lookup"><span data-stu-id="70bfa-550">Request</span></span>  
  
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
  
 <span data-ttu-id="70bfa-551">Resposta</span><span class="sxs-lookup"><span data-stu-id="70bfa-551">Response</span></span>  
  
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
  
#### <a name="654-issuedtokenforsslnegotiated"></a><span data-ttu-id="70bfa-552">6.5.4 IssuedTokenForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="70bfa-552">6.5.4 IssuedTokenForSslNegotiated</span></span>  
 <span data-ttu-id="70bfa-553">Com essa autenticação o cliente não autenticar para o serviço, como tal, mas em vez disso, o modo apresenta um token emitido por um STS e comprova conhecimento de uma chave compartilhada.</span><span class="sxs-lookup"><span data-stu-id="70bfa-553">With this authentication mode the client does not authenticate to the service, as such, but instead presents a token issued by an STS and proves knowledge of a shared key.</span></span> <span data-ttu-id="70bfa-554">O token emitido é exibido na camada de SOAP como um token de suporte de endosso.</span><span class="sxs-lookup"><span data-stu-id="70bfa-554">The issued token appears at the SOAP layer as an endorsing supporting token.</span></span> <span data-ttu-id="70bfa-555">O serviço é autenticado usando um certificado x. 509.</span><span class="sxs-lookup"><span data-stu-id="70bfa-555">The service is authenticated using an X.509 certificate.</span></span> <span data-ttu-id="70bfa-556">A associação usada é uma instância de associação simétrica, conforme descrito em 6.5.1 acima.</span><span class="sxs-lookup"><span data-stu-id="70bfa-556">The binding used is an instance of symmetric binding as described in 6.5.1 above.</span></span>  
  
 <span data-ttu-id="70bfa-557">Política</span><span class="sxs-lookup"><span data-stu-id="70bfa-557">Policy</span></span>  
  
 <span data-ttu-id="70bfa-558">Consulte a seção 6.5.1 acima para obter detalhes de associação</span><span class="sxs-lookup"><span data-stu-id="70bfa-558">See section 6.5.1 above for binding details</span></span>  
  
 <span data-ttu-id="70bfa-559">Endossando o Token de suporte</span><span class="sxs-lookup"><span data-stu-id="70bfa-559">Endorsing Supporting Token</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="70bfa-560">Exemplos de cabeçalho de segurança: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="70bfa-560">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="70bfa-561">Solicitação</span><span class="sxs-lookup"><span data-stu-id="70bfa-561">Request</span></span>  
  
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
  
 <span data-ttu-id="70bfa-562">Resposta</span><span class="sxs-lookup"><span data-stu-id="70bfa-562">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="70bfa-563">Exemplos de cabeçalho de segurança: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="70bfa-563">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="70bfa-564">Solicitação</span><span class="sxs-lookup"><span data-stu-id="70bfa-564">Request</span></span>  
  
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
  
 <span data-ttu-id="70bfa-565">Resposta</span><span class="sxs-lookup"><span data-stu-id="70bfa-565">Response</span></span>  
  
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
  
#### <a name="655-mutualsslnegotiated"></a><span data-ttu-id="70bfa-566">6.5.5 MutualSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="70bfa-566">6.5.5 MutualSslNegotiated</span></span>  
 <span data-ttu-id="70bfa-567">Com esse modo de autenticação o cliente e o serviço de autenticação usando certificados x. 509.</span><span class="sxs-lookup"><span data-stu-id="70bfa-567">With this authentication mode the client and the service authenticate using X.509 certificates.</span></span> <span data-ttu-id="70bfa-568">A associação usada é uma instância de associação simétrica, conforme descrito em 6.5.1 acima.</span><span class="sxs-lookup"><span data-stu-id="70bfa-568">The binding used is an instance of symmetric binding as described in 6.5.1 above.</span></span>  
  
 <span data-ttu-id="70bfa-569">Política</span><span class="sxs-lookup"><span data-stu-id="70bfa-569">Policy</span></span>  
  
 <span data-ttu-id="70bfa-570">Consulte a seção 6.5.1 acima para obter detalhes de associação</span><span class="sxs-lookup"><span data-stu-id="70bfa-570">See section 6.5.1 above for binding details</span></span>  
  
 <span data-ttu-id="70bfa-571">Endossando o Token de suporte</span><span class="sxs-lookup"><span data-stu-id="70bfa-571">Endorsing Supporting Token</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="70bfa-572">Exemplos de cabeçalho de segurança: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="70bfa-572">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="70bfa-573">Solicitação</span><span class="sxs-lookup"><span data-stu-id="70bfa-573">Request</span></span>  
  
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
  
 <span data-ttu-id="70bfa-574">Resposta</span><span class="sxs-lookup"><span data-stu-id="70bfa-574">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="70bfa-575">Exemplos de cabeçalho de segurança: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="70bfa-575">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="70bfa-576">Solicitação</span><span class="sxs-lookup"><span data-stu-id="70bfa-576">Request</span></span>  
  
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
  
 <span data-ttu-id="70bfa-577">Resposta</span><span class="sxs-lookup"><span data-stu-id="70bfa-577">Response</span></span>  
  
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
  
### <a name="66-sspinegotiated"></a><span data-ttu-id="70bfa-578">6.6 SspiNegotiated</span><span class="sxs-lookup"><span data-stu-id="70bfa-578">6.6 SspiNegotiated</span></span>  
 <span data-ttu-id="70bfa-579">Com esse modo de autenticação, um protocolo de negociação é usado para realizar a autenticação de cliente e servidor.</span><span class="sxs-lookup"><span data-stu-id="70bfa-579">With this authentication mode a negotiation protocol is used to perform client and server authentication.</span></span> <span data-ttu-id="70bfa-580">Kerberos é usado, se possível, caso contrário NTLM.</span><span class="sxs-lookup"><span data-stu-id="70bfa-580">Kerberos is used if possible, otherwise NTLM.</span></span> <span data-ttu-id="70bfa-581">A associação usada é uma associação simétrica com as seguintes propriedades;</span><span class="sxs-lookup"><span data-stu-id="70bfa-581">The binding used is a symmetric binding with the following properties;</span></span>  
  
 <span data-ttu-id="70bfa-582">Token de proteção: SpnegoContextToken, modo de inclusão estiver definido como .../IncludeToken/AlwaysToRecipient</span><span class="sxs-lookup"><span data-stu-id="70bfa-582">Protection Token: SpnegoContextToken, inclusion mode is set to .../IncludeToken/AlwaysToRecipient</span></span>  
<span data-ttu-id="70bfa-583">Proteção de token: False</span><span class="sxs-lookup"><span data-stu-id="70bfa-583">Token Protection: False</span></span>  
  
 <span data-ttu-id="70bfa-584">Todo cabeçalho e corpo assinaturas: True</span><span class="sxs-lookup"><span data-stu-id="70bfa-584">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="70bfa-585">Ordem de proteção: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="70bfa-585">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="70bfa-586">Criptografar assinatura: True</span><span class="sxs-lookup"><span data-stu-id="70bfa-586">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="70bfa-587">Política</span><span class="sxs-lookup"><span data-stu-id="70bfa-587">Policy</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="70bfa-588">Exemplos de cabeçalho de segurança: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="70bfa-588">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="70bfa-589">Solicitação</span><span class="sxs-lookup"><span data-stu-id="70bfa-589">Request</span></span>  
  
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
  
 <span data-ttu-id="70bfa-590">Resposta</span><span class="sxs-lookup"><span data-stu-id="70bfa-590">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="70bfa-591">Exemplos de cabeçalho de segurança: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="70bfa-591">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="70bfa-592">Solicitação</span><span class="sxs-lookup"><span data-stu-id="70bfa-592">Request</span></span>  
  
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
  
 <span data-ttu-id="70bfa-593">Resposta</span><span class="sxs-lookup"><span data-stu-id="70bfa-593">Response</span></span>  
  
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
  
### <a name="67-secureconversation"></a><span data-ttu-id="70bfa-594">6.7 SecureConversation</span><span class="sxs-lookup"><span data-stu-id="70bfa-594">6.7 SecureConversation</span></span>  
 <span data-ttu-id="70bfa-595">A associação usada é uma associação simétrica com o token de proteção sendo um SCT por WS-SecureConversation (WS-SC).</span><span class="sxs-lookup"><span data-stu-id="70bfa-595">The binding used is a symmetric binding with the protection token being a SCT per WS-SecureConversation (WS-SC).</span></span> <span data-ttu-id="70bfa-596">O SCT é negociada com o WS-Trust (WS-Trust) ou WS-SecureConversation (WS-SC) acordo com uma associação aninhada, que também é uma associação simétrica que usa um protocolo de negociação.</span><span class="sxs-lookup"><span data-stu-id="70bfa-596">The SCT is negotiated using WS-Trust (WS-Trust) or WS-SecureConversation (WS-SC) according to a nested binding, which is itself a symmetric binding that uses a negotiation protocol.</span></span> <span data-ttu-id="70bfa-597">O protocolo de negociação usará o Kerberos para realizar a autenticação de cliente e servidor se possível.</span><span class="sxs-lookup"><span data-stu-id="70bfa-597">The negotiation protocol will use Kerberos to perform client and server authentication if possible.</span></span> <span data-ttu-id="70bfa-598">Se Kerberos não pode ser usado, ele retornará a NTLM.</span><span class="sxs-lookup"><span data-stu-id="70bfa-598">If Kerberos cannot be used, it will fall back to NTLM.</span></span>  
  
 <span data-ttu-id="70bfa-599">Política</span><span class="sxs-lookup"><span data-stu-id="70bfa-599">Policy</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="70bfa-600">Exemplos de cabeçalho de segurança: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="70bfa-600">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="70bfa-601">Solicitação</span><span class="sxs-lookup"><span data-stu-id="70bfa-601">Request</span></span>  
  
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
  
 <span data-ttu-id="70bfa-602">Resposta</span><span class="sxs-lookup"><span data-stu-id="70bfa-602">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="70bfa-603">Exemplos de cabeçalho de segurança: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="70bfa-603">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="70bfa-604">Solicitação</span><span class="sxs-lookup"><span data-stu-id="70bfa-604">Request</span></span>  
  
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
  
 <span data-ttu-id="70bfa-605">Resposta</span><span class="sxs-lookup"><span data-stu-id="70bfa-605">Response</span></span>  
  
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
