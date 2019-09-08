---
title: Segurança estendida
ms.date: 03/30/2017
helpviewer_keywords:
- security [WCF], extending
ms.assetid: a015a040-9fdf-4147-9ea9-f83b570be1d4
ms.openlocfilehash: 45216493a3afa23f24a085964a2c43e19b197d4b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70797124"
---
# <a name="extending-security"></a><span data-ttu-id="2df1f-102">Segurança estendida</span><span class="sxs-lookup"><span data-stu-id="2df1f-102">Extending Security</span></span>
<span data-ttu-id="2df1f-103">Para acomodar novos tipos de declaração e tokens personalizados, você pode estender a infraestrutura de segurança do Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="2df1f-103">To accommodate new claim types and custom tokens, you can extend the security infrastructure of Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="2df1f-104">Os tópicos nesta seção mostram como isso é feito.</span><span class="sxs-lookup"><span data-stu-id="2df1f-104">The topics in this section show you how this is done.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2df1f-105">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="2df1f-105">In This Section</span></span>  
  
 [<span data-ttu-id="2df1f-106">Credencial personalizada e validação de credenciais</span><span class="sxs-lookup"><span data-stu-id="2df1f-106">Custom Credential and Credential Validation</span></span>](custom-credential-and-credential-validation.md)  
 <span data-ttu-id="2df1f-107">Explica como o modelo de identidade é usado ao validar credenciais personalizadas.</span><span class="sxs-lookup"><span data-stu-id="2df1f-107">Explains how the Identity Model is used when validating custom credentials.</span></span>  
  
 [<span data-ttu-id="2df1f-108">Tokens personalizados</span><span class="sxs-lookup"><span data-stu-id="2df1f-108">Custom Tokens</span></span>](custom-tokens.md)  
 <span data-ttu-id="2df1f-109">Os tokens emitidos de um serviço de token de segurança (STS) normalmente são tokens SAML.</span><span class="sxs-lookup"><span data-stu-id="2df1f-109">Issued tokens from a Security Token Service (STS) are typically SAML tokens.</span></span> <span data-ttu-id="2df1f-110">Este tópico explica como criar um tipo de token personalizado.</span><span class="sxs-lookup"><span data-stu-id="2df1f-110">This topic explains how to create a custom token type.</span></span>  
  
 [<span data-ttu-id="2df1f-111">Autorização personalizada</span><span class="sxs-lookup"><span data-stu-id="2df1f-111">Custom Authorization</span></span>](custom-authorization.md)  
 <span data-ttu-id="2df1f-112">Explica como implementar a autorização personalizada.</span><span class="sxs-lookup"><span data-stu-id="2df1f-112">Explains how to implement custom authorization.</span></span>  
  
 [<span data-ttu-id="2df1f-113">Substituindo a identidade de um serviço de autenticação</span><span class="sxs-lookup"><span data-stu-id="2df1f-113">Overriding the Identity of a Service for Authentication</span></span>](overriding-the-identity-of-a-service-for-authentication.md)  
 <span data-ttu-id="2df1f-114">Descreve como substituir a identidade de um serviço para autenticação.</span><span class="sxs-lookup"><span data-stu-id="2df1f-114">Describes how to override the identity of a service for authentication.</span></span>  
  
 [<span data-ttu-id="2df1f-115">Como: Criar um verificador de identidade de cliente personalizado</span><span class="sxs-lookup"><span data-stu-id="2df1f-115">How to: Create a Custom Client Identity Verifier</span></span>](how-to-create-a-custom-client-identity-verifier.md)  
 <span data-ttu-id="2df1f-116">Demonstra como validar uma identidade de ponto de extremidade personalizada.</span><span class="sxs-lookup"><span data-stu-id="2df1f-116">Demonstrates how to validate a custom endpoint identity.</span></span>  
  
 [<span data-ttu-id="2df1f-117">Como: Usar certificados X. 509 separados para assinatura e criptografia</span><span class="sxs-lookup"><span data-stu-id="2df1f-117">How to: Use Separate X.509 Certificates for Signing and Encryption</span></span>](how-to-use-separate-x-509-certificates-for-signing-and-encryption.md)  
 <span data-ttu-id="2df1f-118">Normalmente, as mensagens são assinadas e criptografadas com um único certificado.</span><span class="sxs-lookup"><span data-stu-id="2df1f-118">Messages are typically signed and encrypted with a single certificate.</span></span> <span data-ttu-id="2df1f-119">Este tópico explica como dois certificados podem ser usados, quando necessário.</span><span class="sxs-lookup"><span data-stu-id="2df1f-119">This topic explains how two certificates can be used, when required.</span></span>  
  
 [<span data-ttu-id="2df1f-120">Como: Alterar o provedor criptográfico para uma chave privada do certificado X. 509</span><span class="sxs-lookup"><span data-stu-id="2df1f-120">How to: Change the Cryptographic Provider for an X.509 Certificate's Private Key</span></span>](change-cryptographic-provider-x509-certificate-private-key.md)  
 <span data-ttu-id="2df1f-121">Explica como alterar o provedor criptográfico usado para fornecer uma chave privada do certificado X. 509 e como integrar o provedor à estrutura do Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="2df1f-121">Explains how to change the cryptographic provider used to provide an X.509 certificate's private key and how to integrate the provider into the Windows Communication Foundation (WCF) framework.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="2df1f-122">Referência</span><span class="sxs-lookup"><span data-stu-id="2df1f-122">Reference</span></span>  
 <xref:System.ServiceModel.ServiceAuthorizationManager>  
  
 <xref:System.ServiceModel.Security>  
  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.IdentityModel.Policy>  
  
 <xref:System.IdentityModel.Tokens>  
  
 <xref:System.IdentityModel.Selectors>  
  
## <a name="related-sections"></a><span data-ttu-id="2df1f-123">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="2df1f-123">Related Sections</span></span>  
 [<span data-ttu-id="2df1f-124">Segurança</span><span class="sxs-lookup"><span data-stu-id="2df1f-124">Security</span></span>](../feature-details/security.md)  
  
 [<span data-ttu-id="2df1f-125">Programação básica do WCF</span><span class="sxs-lookup"><span data-stu-id="2df1f-125">Basic WCF Programming</span></span>](../basic-wcf-programming.md)  
  
## <a name="see-also"></a><span data-ttu-id="2df1f-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2df1f-126">See also</span></span>

- [<span data-ttu-id="2df1f-127">Visão geral de segurança</span><span class="sxs-lookup"><span data-stu-id="2df1f-127">Security Overview</span></span>](../feature-details/security-overview.md)
