---
title: Autenticação no WCF
ms.date: 03/30/2017
helpviewer_keywords:
- authentication [WCF]
- security [WCF], authentication
ms.assetid: 9254d873-843d-4c6e-bea4-8184ac3e44f4
ms.openlocfilehash: ebff66e185bdca75a0150b22a16392bfd08892d3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59165448"
---
# <a name="authentication-in-wcf"></a><span data-ttu-id="4b4b9-102">Autenticação no WCF</span><span class="sxs-lookup"><span data-stu-id="4b4b9-102">Authentication in WCF</span></span>
<span data-ttu-id="4b4b9-103">Os tópicos a seguir mostram um número de mecanismos diferentes no Windows Communication Foundation (WCF) que fornecem autenticação, por exemplo, a autenticação do Windows, certificados X.509 e o nome de usuário e senhas.</span><span class="sxs-lookup"><span data-stu-id="4b4b9-103">The following topics show a number of different mechanisms in Windows Communication Foundation (WCF) that provide authentication, for example, Windows authentication, X.509 certificates, and user name and passwords.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4b4b9-104">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="4b4b9-104">In This Section</span></span>  
 [<span data-ttu-id="4b4b9-105">Como: usar o provedor de associação do ASP.NET</span><span class="sxs-lookup"><span data-stu-id="4b4b9-105">How to: Use the ASP.NET Membership Provider</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md)  
 <span data-ttu-id="4b4b9-106">Recursos do ASP.NET incluem uma associação e provedor de função, um banco de dados para armazenar pares de nome/senha de usuário para autenticação e funções de usuário para autorização.</span><span class="sxs-lookup"><span data-stu-id="4b4b9-106">ASP.NET features include a membership and role provider, a database to store user name/password pairs for authentication, and user roles for authorization.</span></span> <span data-ttu-id="4b4b9-107">Este tópico explica como os serviços do WCF podem usar o mesmo banco de dados para autenticar e autorizar usuários.</span><span class="sxs-lookup"><span data-stu-id="4b4b9-107">This topic explains how WCF services can use the same database to authenticate and authorize users.</span></span>  
  
 [<span data-ttu-id="4b4b9-108">Como: usar um validador personalizado de nome de usuário e senha</span><span class="sxs-lookup"><span data-stu-id="4b4b9-108">How to: Use a Custom User Name and Password Validator</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-a-custom-user-name-and-password-validator.md)  
 <span data-ttu-id="4b4b9-109">Demonstra como integrar um validador de nome/senha de usuário personalizada.</span><span class="sxs-lookup"><span data-stu-id="4b4b9-109">Demonstrates how to integrate a custom user name/password validator.</span></span>  
  
 [<span data-ttu-id="4b4b9-110">Identidade e autenticação de serviço</span><span class="sxs-lookup"><span data-stu-id="4b4b9-110">Service Identity and Authentication</span></span>](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 <span data-ttu-id="4b4b9-111">Como uma proteção extra, um cliente pode autenticar o serviço especificando o esperado *identidade* do serviço.</span><span class="sxs-lookup"><span data-stu-id="4b4b9-111">As an extra safeguard, a client can authenticate the service by specifying the expected *identity* of the service.</span></span> <span data-ttu-id="4b4b9-112">Se a identidade esperada e a identidade retornados pelo serviço não corresponderem, a autenticação falhará.</span><span class="sxs-lookup"><span data-stu-id="4b4b9-112">If the expected identity and the identity returned by the service do not match, authentication fails.</span></span>  
  
 [<span data-ttu-id="4b4b9-113">Negociação de segurança e tempo limite</span><span class="sxs-lookup"><span data-stu-id="4b4b9-113">Security Negotiation and Timeouts</span></span>](../../../../docs/framework/wcf/feature-details/security-negotiation-and-timeouts.md)  
 <span data-ttu-id="4b4b9-114">Descreve como usar o <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> propriedade no <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> classe.</span><span class="sxs-lookup"><span data-stu-id="4b4b9-114">Describes how to use the <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> property in the <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> class.</span></span>  
  
 [<span data-ttu-id="4b4b9-115">Depurando erros de autenticação do Windows</span><span class="sxs-lookup"><span data-stu-id="4b4b9-115">Debugging Windows Authentication Errors</span></span>](../../../../docs/framework/wcf/feature-details/debugging-windows-authentication-errors.md)  
 <span data-ttu-id="4b4b9-116">Se concentra em problemas comuns encontrados ao usar a autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="4b4b9-116">Focuses on common problems encountered when using Windows authentication.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="4b4b9-117">Referência</span><span class="sxs-lookup"><span data-stu-id="4b4b9-117">Reference</span></span>  
 <xref:System.ServiceModel>  
  
## <a name="related-sections"></a><span data-ttu-id="4b4b9-118">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="4b4b9-118">Related Sections</span></span>  
 [<span data-ttu-id="4b4b9-119">Cenários comuns de segurança</span><span class="sxs-lookup"><span data-stu-id="4b4b9-119">Common Security Scenarios</span></span>](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)  
  
## <a name="see-also"></a><span data-ttu-id="4b4b9-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4b4b9-120">See also</span></span>

- [<span data-ttu-id="4b4b9-121">Visão geral de segurança</span><span class="sxs-lookup"><span data-stu-id="4b4b9-121">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [<span data-ttu-id="4b4b9-122">Modelo de segurança do Windows Server App Fabric</span><span class="sxs-lookup"><span data-stu-id="4b4b9-122">Security Model for Windows Server App Fabric</span></span>](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
