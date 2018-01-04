---
title: "Credencial personalizada e validação de credencial"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- credentials [WCF], custom
- credentials [WCF]
- custom credentials [WCF]
- credential validation [WCF]
- credentials [WCF], validation
ms.assetid: da831bec-e281-4d44-b343-437b5eef688e
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bdfd50253c71bfc9edd737964e771546cb797b9e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="custom-credential-and-credential-validation"></a><span data-ttu-id="05683-102">Credencial personalizada e validação de credencial</span><span class="sxs-lookup"><span data-stu-id="05683-102">Custom Credential and Credential Validation</span></span>
<span data-ttu-id="05683-103">Segurança em [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] baseia-se a troca de credenciais entre clientes e serviços.</span><span class="sxs-lookup"><span data-stu-id="05683-103">Security in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] is based on the exchange of credentials between services and clients.</span></span> <span data-ttu-id="05683-104">A maioria dos cenários de segurança podem ser satisfeitos usando tipos comuns de credenciais, como Windows (Kerberos), nome de usuário e senhas e certificados.</span><span class="sxs-lookup"><span data-stu-id="05683-104">Most security scenarios can be satisfied using common credential types, such as Windows (Kerberos), username and passwords, and certificates.</span></span> <span data-ttu-id="05683-105">No entanto, se um novo tipo de credencial for necessário, os tópicos nesta seção explicam como manipular e validar os novos tipos.</span><span class="sxs-lookup"><span data-stu-id="05683-105">However, if a new type of credential is required, the topics in this section explain how to handle and validate new types.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="05683-106">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="05683-106">In This Section</span></span>  
 [<span data-ttu-id="05683-107">Como criar um serviço que utiliza um validador de certificado personalizado</span><span class="sxs-lookup"><span data-stu-id="05683-107">How to: Create a Service that Employs a Custom Certificate Validator</span></span>](../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)  
 <span data-ttu-id="05683-108">Explica como personalizar [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] validação herdando do <xref:System.IdentityModel.Selectors.X509CertificateValidator> classe.</span><span class="sxs-lookup"><span data-stu-id="05683-108">Explains how to customize [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] validation by inheriting from the <xref:System.IdentityModel.Selectors.X509CertificateValidator> class.</span></span>  
  
 [<span data-ttu-id="05683-109">Passo a passo: criando credenciais de serviço e de cliente personalizados</span><span class="sxs-lookup"><span data-stu-id="05683-109">Walkthrough: Creating Custom Client and Service Credentials</span></span>](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md)  
 <span data-ttu-id="05683-110">Demonstra como estender o <xref:System.ServiceModel.Description.ClientCredentials> e <xref:System.ServiceModel.Description.ServiceCredentials> classes para acomodar novos tipos de credenciais.</span><span class="sxs-lookup"><span data-stu-id="05683-110">Demonstrates how to extend the <xref:System.ServiceModel.Description.ClientCredentials> and <xref:System.ServiceModel.Description.ServiceCredentials> classes to accommodate new credential types.</span></span> <span data-ttu-id="05683-111">Este é o primeiro em uma série de tópicos que permitem a criação de tipos de credencial personalizada.</span><span class="sxs-lookup"><span data-stu-id="05683-111">This is first in a series of topics that enable creation of custom credential types.</span></span>  
  
 [<span data-ttu-id="05683-112">Como criar um provedor de token de segurança personalizado</span><span class="sxs-lookup"><span data-stu-id="05683-112">How to: Create a Custom Security Token Provider</span></span>](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md)  
 <span data-ttu-id="05683-113">Explica como criar um provedor de token de segurança para lidar com novos tipos de credenciais e retornar novos tokens para a credencial.</span><span class="sxs-lookup"><span data-stu-id="05683-113">Explains how to create a security token provider to handle new credential types and return new tokens for the credential.</span></span> <span data-ttu-id="05683-114">Este é o segundo tópico na série.</span><span class="sxs-lookup"><span data-stu-id="05683-114">This is the second topic in the series.</span></span>  
  
 [<span data-ttu-id="05683-115">Como criar um autenticador de token de segurança personalizado</span><span class="sxs-lookup"><span data-stu-id="05683-115">How to: Create a Custom Security Token Authenticator</span></span>](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-authenticator.md)  
 <span data-ttu-id="05683-116">Explica como criar um autenticador personalizado para autenticar um novo tipo de credencial.</span><span class="sxs-lookup"><span data-stu-id="05683-116">Explains how to create a custom authenticator to authenticate a new credential type.</span></span> <span data-ttu-id="05683-117">Este é o terceiro tópico na série.</span><span class="sxs-lookup"><span data-stu-id="05683-117">This is the third topic in the series.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="05683-118">Referência</span><span class="sxs-lookup"><span data-stu-id="05683-118">Reference</span></span>  
 <xref:System.ServiceModel.Security>  
  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.IdentityModel.Policy>  
  
 <xref:System.IdentityModel.Tokens>  
  
 <xref:System.IdentityModel.Selectors>  
  
 <xref:System.IdentityModel.Selectors.X509CertificateValidator>  
  
 <xref:System.ServiceModel.Description.ClientCredentials>  
  
 <xref:System.ServiceModel.Description.ServiceCredentials>  
  
## <a name="related-sections"></a><span data-ttu-id="05683-119">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="05683-119">Related Sections</span></span>  
 [<span data-ttu-id="05683-120">Autenticação</span><span class="sxs-lookup"><span data-stu-id="05683-120">Authentication</span></span>](../../../../docs/framework/wcf/feature-details/authentication-in-wcf.md)  
  
 [<span data-ttu-id="05683-121">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="05683-121">Federation and Issued Tokens</span></span>](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
  
 [<span data-ttu-id="05683-122">Autorização</span><span class="sxs-lookup"><span data-stu-id="05683-122">Authorization</span></span>](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
  
## <a name="see-also"></a><span data-ttu-id="05683-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="05683-123">See Also</span></span>  
 [<span data-ttu-id="05683-124">Segurança</span><span class="sxs-lookup"><span data-stu-id="05683-124">Security</span></span>](../../../../docs/framework/wcf/feature-details/security.md)
