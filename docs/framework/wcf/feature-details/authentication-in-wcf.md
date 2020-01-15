---
title: Autenticação no WCF
ms.date: 03/30/2017
helpviewer_keywords:
- authentication [WCF]
- security [WCF], authentication
ms.assetid: 9254d873-843d-4c6e-bea4-8184ac3e44f4
ms.openlocfilehash: abe7aff025207ad8bdf8657daba3584e6a1b2e7f
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/15/2020
ms.locfileid: "75964691"
---
# <a name="authentication-in-wcf"></a><span data-ttu-id="b416b-102">Autenticação no WCF</span><span class="sxs-lookup"><span data-stu-id="b416b-102">Authentication in WCF</span></span>
<span data-ttu-id="b416b-103">Os tópicos a seguir mostram vários mecanismos diferentes no Windows Communication Foundation (WCF) que fornecem autenticação, por exemplo, autenticação do Windows, certificados X. 509 e nome de usuário e senhas.</span><span class="sxs-lookup"><span data-stu-id="b416b-103">The following topics show a number of different mechanisms in Windows Communication Foundation (WCF) that provide authentication, for example, Windows authentication, X.509 certificates, and user name and passwords.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b416b-104">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="b416b-104">In This Section</span></span>  
 [<span data-ttu-id="b416b-105">Como usar o provedor de associação do ASP.NET</span><span class="sxs-lookup"><span data-stu-id="b416b-105">How to: Use the ASP.NET Membership Provider</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md)  
 <span data-ttu-id="b416b-106">Os recursos do ASP.NET incluem uma associação e um provedor de função, um banco de dados para armazenar pares de nome de usuário/senha para autenticação e funções de usuário para autorização.</span><span class="sxs-lookup"><span data-stu-id="b416b-106">ASP.NET features include a membership and role provider, a database to store user name/password pairs for authentication, and user roles for authorization.</span></span> <span data-ttu-id="b416b-107">Este tópico explica como os serviços WCF podem usar o mesmo banco de dados para autenticar e autorizar usuários.</span><span class="sxs-lookup"><span data-stu-id="b416b-107">This topic explains how WCF services can use the same database to authenticate and authorize users.</span></span>  
  
 [<span data-ttu-id="b416b-108">Como usar um nome de usuário e validador de senha personalizados</span><span class="sxs-lookup"><span data-stu-id="b416b-108">How to: Use a Custom User Name and Password Validator</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-a-custom-user-name-and-password-validator.md)  
 <span data-ttu-id="b416b-109">Demonstra como integrar um validador de nome de usuário/senha personalizado.</span><span class="sxs-lookup"><span data-stu-id="b416b-109">Demonstrates how to integrate a custom user name/password validator.</span></span>  
  
 [<span data-ttu-id="b416b-110">Autenticação e identidade de serviço</span><span class="sxs-lookup"><span data-stu-id="b416b-110">Service Identity and Authentication</span></span>](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 <span data-ttu-id="b416b-111">Como uma proteção extra, um cliente pode autenticar o serviço especificando a *identidade* esperada do serviço.</span><span class="sxs-lookup"><span data-stu-id="b416b-111">As an extra safeguard, a client can authenticate the service by specifying the expected *identity* of the service.</span></span> <span data-ttu-id="b416b-112">Se a identidade esperada e a identidade retornada pelo serviço não corresponderem, a autenticação falhará.</span><span class="sxs-lookup"><span data-stu-id="b416b-112">If the expected identity and the identity returned by the service do not match, authentication fails.</span></span>  
  
 [<span data-ttu-id="b416b-113">Negociação de segurança e tempos limite</span><span class="sxs-lookup"><span data-stu-id="b416b-113">Security Negotiation and Timeouts</span></span>](../../../../docs/framework/wcf/feature-details/security-negotiation-and-timeouts.md)  
 <span data-ttu-id="b416b-114">Descreve como usar a propriedade <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> na classe <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>.</span><span class="sxs-lookup"><span data-stu-id="b416b-114">Describes how to use the <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> property in the <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> class.</span></span>  
  
 [<span data-ttu-id="b416b-115">Depuração de erros de autenticação do Windows</span><span class="sxs-lookup"><span data-stu-id="b416b-115">Debugging Windows Authentication Errors</span></span>](../../../../docs/framework/wcf/feature-details/debugging-windows-authentication-errors.md)  
 <span data-ttu-id="b416b-116">Concentra-se em problemas comuns encontrados ao usar a autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="b416b-116">Focuses on common problems encountered when using Windows authentication.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="b416b-117">Referência</span><span class="sxs-lookup"><span data-stu-id="b416b-117">Reference</span></span>  
 <xref:System.ServiceModel>  
  
## <a name="related-sections"></a><span data-ttu-id="b416b-118">Seções Relacionadas</span><span class="sxs-lookup"><span data-stu-id="b416b-118">Related Sections</span></span>  
 [<span data-ttu-id="b416b-119">Cenários comuns de segurança</span><span class="sxs-lookup"><span data-stu-id="b416b-119">Common Security Scenarios</span></span>](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)  
  
## <a name="see-also"></a><span data-ttu-id="b416b-120">Veja também</span><span class="sxs-lookup"><span data-stu-id="b416b-120">See also</span></span>

- [<span data-ttu-id="b416b-121">Visão geral de segurança</span><span class="sxs-lookup"><span data-stu-id="b416b-121">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
- <span data-ttu-id="b416b-122">[Modelo de segurança para o Windows Server app Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="b416b-122">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
