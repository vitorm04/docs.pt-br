---
title: Credencial personalizada e validação de credencial
ms.date: 03/30/2017
helpviewer_keywords:
- credentials [WCF], custom
- credentials [WCF]
- custom credentials [WCF]
- credential validation [WCF]
- credentials [WCF], validation
ms.assetid: da831bec-e281-4d44-b343-437b5eef688e
ms.openlocfilehash: 1418d4155bc7f2fefc9f3e6caf4d3a264747a667
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795807"
---
# <a name="custom-credential-and-credential-validation"></a><span data-ttu-id="991cc-102">Credencial personalizada e validação de credencial</span><span class="sxs-lookup"><span data-stu-id="991cc-102">Custom Credential and Credential Validation</span></span>
<span data-ttu-id="991cc-103">A segurança no Windows Communication Foundation (WCF) é baseada na troca de credenciais entre serviços e clientes.</span><span class="sxs-lookup"><span data-stu-id="991cc-103">Security in Windows Communication Foundation (WCF) is based on the exchange of credentials between services and clients.</span></span> <span data-ttu-id="991cc-104">A maioria dos cenários de segurança pode ser satisfeita usando tipos de credenciais comuns, como Windows (Kerberos), nome de usuário e senhas e certificados.</span><span class="sxs-lookup"><span data-stu-id="991cc-104">Most security scenarios can be satisfied using common credential types, such as Windows (Kerberos), username and passwords, and certificates.</span></span> <span data-ttu-id="991cc-105">No entanto, se um novo tipo de credencial for necessário, os tópicos nesta seção explicam como tratar e validar novos tipos.</span><span class="sxs-lookup"><span data-stu-id="991cc-105">However, if a new type of credential is required, the topics in this section explain how to handle and validate new types.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="991cc-106">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="991cc-106">In This Section</span></span>  
 [<span data-ttu-id="991cc-107">Como: Criar um serviço que empregue um validador de certificado personalizado</span><span class="sxs-lookup"><span data-stu-id="991cc-107">How to: Create a Service that Employs a Custom Certificate Validator</span></span>](how-to-create-a-service-that-employs-a-custom-certificate-validator.md)  
 <span data-ttu-id="991cc-108">Explica como personalizar a <xref:System.IdentityModel.Selectors.X509CertificateValidator> validação do WCF herdando da classe.</span><span class="sxs-lookup"><span data-stu-id="991cc-108">Explains how to customize WCF validation by inheriting from the <xref:System.IdentityModel.Selectors.X509CertificateValidator> class.</span></span>  
  
 [<span data-ttu-id="991cc-109">Passo a passo: Criando credenciais de cliente e de serviço personalizadas</span><span class="sxs-lookup"><span data-stu-id="991cc-109">Walkthrough: Creating Custom Client and Service Credentials</span></span>](walkthrough-creating-custom-client-and-service-credentials.md)  
 <span data-ttu-id="991cc-110">Demonstra como estender as <xref:System.ServiceModel.Description.ClientCredentials> classes e <xref:System.ServiceModel.Description.ServiceCredentials> para acomodar novos tipos de credencial.</span><span class="sxs-lookup"><span data-stu-id="991cc-110">Demonstrates how to extend the <xref:System.ServiceModel.Description.ClientCredentials> and <xref:System.ServiceModel.Description.ServiceCredentials> classes to accommodate new credential types.</span></span> <span data-ttu-id="991cc-111">Isso é primeiro em uma série de tópicos que permitem a criação de tipos de credenciais personalizados.</span><span class="sxs-lookup"><span data-stu-id="991cc-111">This is first in a series of topics that enable creation of custom credential types.</span></span>  
  
 [<span data-ttu-id="991cc-112">Como: Criar um provedor de token de segurança personalizado</span><span class="sxs-lookup"><span data-stu-id="991cc-112">How to: Create a Custom Security Token Provider</span></span>](how-to-create-a-custom-security-token-provider.md)  
 <span data-ttu-id="991cc-113">Explica como criar um provedor de token de segurança para lidar com novos tipos de credenciais e retornar novos tokens para a credencial.</span><span class="sxs-lookup"><span data-stu-id="991cc-113">Explains how to create a security token provider to handle new credential types and return new tokens for the credential.</span></span> <span data-ttu-id="991cc-114">Este é o segundo tópico da série.</span><span class="sxs-lookup"><span data-stu-id="991cc-114">This is the second topic in the series.</span></span>  
  
 [<span data-ttu-id="991cc-115">Como: Criar um autenticador de token de segurança personalizado</span><span class="sxs-lookup"><span data-stu-id="991cc-115">How to: Create a Custom Security Token Authenticator</span></span>](how-to-create-a-custom-security-token-authenticator.md)  
 <span data-ttu-id="991cc-116">Explica como criar um autenticador personalizado para autenticar um novo tipo de credencial.</span><span class="sxs-lookup"><span data-stu-id="991cc-116">Explains how to create a custom authenticator to authenticate a new credential type.</span></span> <span data-ttu-id="991cc-117">Este é o terceiro tópico da série.</span><span class="sxs-lookup"><span data-stu-id="991cc-117">This is the third topic in the series.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="991cc-118">Referência</span><span class="sxs-lookup"><span data-stu-id="991cc-118">Reference</span></span>  
 <xref:System.ServiceModel.Security>  
  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.IdentityModel.Policy>  
  
 <xref:System.IdentityModel.Tokens>  
  
 <xref:System.IdentityModel.Selectors>  
  
 <xref:System.IdentityModel.Selectors.X509CertificateValidator>  
  
 <xref:System.ServiceModel.Description.ClientCredentials>  
  
 <xref:System.ServiceModel.Description.ServiceCredentials>  
  
## <a name="related-sections"></a><span data-ttu-id="991cc-119">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="991cc-119">Related Sections</span></span>  
 [<span data-ttu-id="991cc-120">Autenticação</span><span class="sxs-lookup"><span data-stu-id="991cc-120">Authentication</span></span>](../feature-details/authentication-in-wcf.md)  
  
 [<span data-ttu-id="991cc-121">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="991cc-121">Federation and Issued Tokens</span></span>](../feature-details/federation-and-issued-tokens.md)  
  
 [<span data-ttu-id="991cc-122">Autorização</span><span class="sxs-lookup"><span data-stu-id="991cc-122">Authorization</span></span>](../feature-details/authorization-in-wcf.md)  
  
## <a name="see-also"></a><span data-ttu-id="991cc-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="991cc-123">See also</span></span>

- [<span data-ttu-id="991cc-124">Segurança</span><span class="sxs-lookup"><span data-stu-id="991cc-124">Security</span></span>](../feature-details/security.md)
