---
title: Autenticação no WCF
ms.date: 03/30/2017
helpviewer_keywords:
- authentication [WCF]
- security [WCF], authentication
ms.assetid: 9254d873-843d-4c6e-bea4-8184ac3e44f4
ms.openlocfilehash: 401bd8901f4d8b9292e83d3e54d0afce30c9584f
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43785824"
---
# <a name="authentication-in-wcf"></a><span data-ttu-id="d37ce-102">Autenticação no WCF</span><span class="sxs-lookup"><span data-stu-id="d37ce-102">Authentication in WCF</span></span>
<span data-ttu-id="d37ce-103">Os tópicos a seguir mostram um número de mecanismos diferentes no Windows Communication Foundation (WCF) que fornecem autenticação, por exemplo, a autenticação do Windows, certificados X.509 e o nome de usuário e senhas.</span><span class="sxs-lookup"><span data-stu-id="d37ce-103">The following topics show a number of different mechanisms in Windows Communication Foundation (WCF) that provide authentication, for example, Windows authentication, X.509 certificates, and user name and passwords.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d37ce-104">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="d37ce-104">In This Section</span></span>  
 [<span data-ttu-id="d37ce-105">Como usar o provedor de associação do ASP.NET</span><span class="sxs-lookup"><span data-stu-id="d37ce-105">How to: Use the ASP.NET Membership Provider</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md)  
 <span data-ttu-id="d37ce-106">Recursos do ASP.NET incluem uma associação e provedor de função, um banco de dados para armazenar pares de nome/senha de usuário para autenticação e funções de usuário para autorização.</span><span class="sxs-lookup"><span data-stu-id="d37ce-106">ASP.NET features include a membership and role provider, a database to store user name/password pairs for authentication, and user roles for authorization.</span></span> <span data-ttu-id="d37ce-107">Este tópico explica como os serviços do WCF podem usar o mesmo banco de dados para autenticar e autorizar usuários.</span><span class="sxs-lookup"><span data-stu-id="d37ce-107">This topic explains how WCF services can use the same database to authenticate and authorize users.</span></span>  
  
 [<span data-ttu-id="d37ce-108">Como usar um nome de usuário e validador de senha personalizados</span><span class="sxs-lookup"><span data-stu-id="d37ce-108">How to: Use a Custom User Name and Password Validator</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-a-custom-user-name-and-password-validator.md)  
 <span data-ttu-id="d37ce-109">Demonstra como integrar um validador de nome/senha de usuário personalizada.</span><span class="sxs-lookup"><span data-stu-id="d37ce-109">Demonstrates how to integrate a custom user name/password validator.</span></span>  
  
 [<span data-ttu-id="d37ce-110">Autenticação e identidade de serviço</span><span class="sxs-lookup"><span data-stu-id="d37ce-110">Service Identity and Authentication</span></span>](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 <span data-ttu-id="d37ce-111">Como uma proteção extra, um cliente pode autenticar o serviço especificando o esperado *identidade* do serviço.</span><span class="sxs-lookup"><span data-stu-id="d37ce-111">As an extra safeguard, a client can authenticate the service by specifying the expected *identity* of the service.</span></span> <span data-ttu-id="d37ce-112">Se a identidade esperada e a identidade retornados pelo serviço não corresponderem, a autenticação falhará.</span><span class="sxs-lookup"><span data-stu-id="d37ce-112">If the expected identity and the identity returned by the service do not match, authentication fails.</span></span>  
  
 [<span data-ttu-id="d37ce-113">Negociação de segurança e tempos limite</span><span class="sxs-lookup"><span data-stu-id="d37ce-113">Security Negotiation and Timeouts</span></span>](../../../../docs/framework/wcf/feature-details/security-negotiation-and-timeouts.md)  
 <span data-ttu-id="d37ce-114">Descreve como usar o <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> propriedade no <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> classe.</span><span class="sxs-lookup"><span data-stu-id="d37ce-114">Describes how to use the <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> property in the <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> class.</span></span>  
  
 [<span data-ttu-id="d37ce-115">Depuração de erros de autenticação do Windows</span><span class="sxs-lookup"><span data-stu-id="d37ce-115">Debugging Windows Authentication Errors</span></span>](../../../../docs/framework/wcf/feature-details/debugging-windows-authentication-errors.md)  
 <span data-ttu-id="d37ce-116">Se concentra em problemas comuns encontrados ao usar a autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="d37ce-116">Focuses on common problems encountered when using Windows authentication.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="d37ce-117">Referência</span><span class="sxs-lookup"><span data-stu-id="d37ce-117">Reference</span></span>  
 <xref:System.ServiceModel>  
  
## <a name="related-sections"></a><span data-ttu-id="d37ce-118">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="d37ce-118">Related Sections</span></span>  
 [<span data-ttu-id="d37ce-119">Cenários comuns de segurança</span><span class="sxs-lookup"><span data-stu-id="d37ce-119">Common Security Scenarios</span></span>](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)  
  
## <a name="see-also"></a><span data-ttu-id="d37ce-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d37ce-120">See Also</span></span>  
 [<span data-ttu-id="d37ce-121">Visão geral de segurança</span><span class="sxs-lookup"><span data-stu-id="d37ce-121">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [<span data-ttu-id="d37ce-122">Modelo de segurança do Windows Server App Fabric</span><span class="sxs-lookup"><span data-stu-id="d37ce-122">Security Model for Windows Server App Fabric</span></span>](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
