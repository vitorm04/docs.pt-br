---
title: "Segurança estendida"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: security [WCF], extending
ms.assetid: a015a040-9fdf-4147-9ea9-f83b570be1d4
caps.latest.revision: "23"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: cdd9b91ba7ff9b1e431f7d9107e72df084ba8af3
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="extending-security"></a><span data-ttu-id="9f343-102">Segurança estendida</span><span class="sxs-lookup"><span data-stu-id="9f343-102">Extending Security</span></span>
<span data-ttu-id="9f343-103">Para acomodar novos tipos de declaração e tokens personalizados, você pode estender a infraestrutura de segurança de [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9f343-103">To accommodate new claim types and custom tokens, you can extend the security infrastructure of [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span></span> <span data-ttu-id="9f343-104">Os tópicos nesta seção mostram como fazer isso.</span><span class="sxs-lookup"><span data-stu-id="9f343-104">The topics in this section show you how this is done.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9f343-105">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="9f343-105">In This Section</span></span>  
 [<span data-ttu-id="9f343-106">Arquitetura de segurança</span><span class="sxs-lookup"><span data-stu-id="9f343-106">Security Architecture</span></span>](http://msdn.microsoft.com/library/16593476-d36a-408d-808c-ae6fd483e28f)  
 <span data-ttu-id="9f343-107">Explica a arquitetura do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sistema de segurança.</span><span class="sxs-lookup"><span data-stu-id="9f343-107">Walks through the architecture of the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] security system.</span></span>  
  
 [<span data-ttu-id="9f343-108">Credencial personalizada e validação de credenciais</span><span class="sxs-lookup"><span data-stu-id="9f343-108">Custom Credential and Credential Validation</span></span>](../../../../docs/framework/wcf/extending/custom-credential-and-credential-validation.md)  
 <span data-ttu-id="9f343-109">Explica como o modelo de identidade é usado ao validar credenciais personalizadas.</span><span class="sxs-lookup"><span data-stu-id="9f343-109">Explains how the Identity Model is used when validating custom credentials.</span></span>  
  
 [<span data-ttu-id="9f343-110">Tokens personalizados</span><span class="sxs-lookup"><span data-stu-id="9f343-110">Custom Tokens</span></span>](../../../../docs/framework/wcf/extending/custom-tokens.md)  
 <span data-ttu-id="9f343-111">Tokens emitidos de um Token de segurança Service (STS) normalmente são tokens SAML.</span><span class="sxs-lookup"><span data-stu-id="9f343-111">Issued tokens from a Security Token Service (STS) are typically SAML tokens.</span></span> <span data-ttu-id="9f343-112">Este tópico explica como criar um tipo de token personalizado.</span><span class="sxs-lookup"><span data-stu-id="9f343-112">This topic explains how to create a custom token type.</span></span>  
  
 [<span data-ttu-id="9f343-113">Autorização personalizada</span><span class="sxs-lookup"><span data-stu-id="9f343-113">Custom Authorization</span></span>](../../../../docs/framework/wcf/extending/custom-authorization.md)  
 <span data-ttu-id="9f343-114">Explica como implementar a autorização personalizada.</span><span class="sxs-lookup"><span data-stu-id="9f343-114">Explains how to implement custom authorization.</span></span>  
  
 [<span data-ttu-id="9f343-115">Substituindo a identidade de um serviço de autenticação</span><span class="sxs-lookup"><span data-stu-id="9f343-115">Overriding the Identity of a Service for Authentication</span></span>](../../../../docs/framework/wcf/extending/overriding-the-identity-of-a-service-for-authentication.md)  
 <span data-ttu-id="9f343-116">Descreve como substituir a identidade de um serviço para autenticação.</span><span class="sxs-lookup"><span data-stu-id="9f343-116">Describes how to override the identity of a service for authentication.</span></span>  
  
 [<span data-ttu-id="9f343-117">Como criar um verificador de identidade de cliente personalizado</span><span class="sxs-lookup"><span data-stu-id="9f343-117">How to: Create a Custom Client Identity Verifier</span></span>](../../../../docs/framework/wcf/extending/how-to-create-a-custom-client-identity-verifier.md)  
 <span data-ttu-id="9f343-118">Demonstra como validar uma identidade de ponto de extremidade personalizado.</span><span class="sxs-lookup"><span data-stu-id="9f343-118">Demonstrates how to validate a custom endpoint identity.</span></span>  
  
 [<span data-ttu-id="9f343-119">Como usar certificados X.509 separados para assinatura e criptografia</span><span class="sxs-lookup"><span data-stu-id="9f343-119">How to: Use Separate X.509 Certificates for Signing and Encryption</span></span>](../../../../docs/framework/wcf/extending/how-to-use-separate-x-509-certificates-for-signing-and-encryption.md)  
 <span data-ttu-id="9f343-120">As mensagens são normalmente assinadas e criptografadas com um único certificado.</span><span class="sxs-lookup"><span data-stu-id="9f343-120">Messages are typically signed and encrypted with a single certificate.</span></span> <span data-ttu-id="9f343-121">Este tópico explica como dois certificados podem ser usados, quando necessário.</span><span class="sxs-lookup"><span data-stu-id="9f343-121">This topic explains how two certificates can be used, when required.</span></span>  
  
 [<span data-ttu-id="9f343-122">Como alterar o provedor criptográfico para a chave privada de um certificado X.509</span><span class="sxs-lookup"><span data-stu-id="9f343-122">How to: Change the Cryptographic Provider for an X.509 Certificate's Private Key</span></span>](../../../../docs/framework/wcf/extending/change-cryptographic-provider-x509-certificate-private-key.md)  
 <span data-ttu-id="9f343-123">Explica como alterar o provedor de criptografia usado para fornecer a chave privada de um certificado x. 509 e como integrar o provedor para o [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] framework.</span><span class="sxs-lookup"><span data-stu-id="9f343-123">Explains how to change the cryptographic provider used to provide an X.509 certificate's private key and how to integrate the provider into the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] framework.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="9f343-124">Referência</span><span class="sxs-lookup"><span data-stu-id="9f343-124">Reference</span></span>  
 <xref:System.ServiceModel.ServiceAuthorizationManager>  
  
 <xref:System.ServiceModel.Security>  
  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.IdentityModel.Policy>  
  
 <xref:System.IdentityModel.Tokens>  
  
 <xref:System.IdentityModel.Selectors>  
  
## <a name="related-sections"></a><span data-ttu-id="9f343-125">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="9f343-125">Related Sections</span></span>  
 [<span data-ttu-id="9f343-126">Segurança</span><span class="sxs-lookup"><span data-stu-id="9f343-126">Security</span></span>](../../../../docs/framework/wcf/feature-details/security.md)  
  
 [<span data-ttu-id="9f343-127">Programação básica do WCF</span><span class="sxs-lookup"><span data-stu-id="9f343-127">Basic WCF Programming</span></span>](../../../../docs/framework/wcf/basic-wcf-programming.md)  
  
## <a name="see-also"></a><span data-ttu-id="9f343-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9f343-128">See Also</span></span>  
 [<span data-ttu-id="9f343-129">Visão geral de segurança</span><span class="sxs-lookup"><span data-stu-id="9f343-129">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
