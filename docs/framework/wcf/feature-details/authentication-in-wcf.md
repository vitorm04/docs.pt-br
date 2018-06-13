---
title: Autenticação no WCF
ms.date: 03/30/2017
helpviewer_keywords:
- authentication [WCF]
- security [WCF], authentication
ms.assetid: 9254d873-843d-4c6e-bea4-8184ac3e44f4
ms.openlocfilehash: a4f9b719024db1334b599f0f02fe01bc083bf3c8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33489103"
---
# <a name="authentication-in-wcf"></a><span data-ttu-id="dbe4a-102">Autenticação no WCF</span><span class="sxs-lookup"><span data-stu-id="dbe4a-102">Authentication in WCF</span></span>
<span data-ttu-id="dbe4a-103">Os tópicos a seguir mostram um número de mecanismos diferentes no Windows Communication Foundation (WCF) que fornecem autenticação, por exemplo, a autenticação do Windows, certificados x. 509 e o nome de usuário e senhas.</span><span class="sxs-lookup"><span data-stu-id="dbe4a-103">The following topics show a number of different mechanisms in Windows Communication Foundation (WCF) that provide authentication, for example, Windows authentication, X.509 certificates, and user name and passwords.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="dbe4a-104">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="dbe4a-104">In This Section</span></span>  
 [<span data-ttu-id="dbe4a-105">Como usar o provedor de associação do ASP.NET</span><span class="sxs-lookup"><span data-stu-id="dbe4a-105">How to: Use the ASP.NET Membership Provider</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md)  
 <span data-ttu-id="dbe4a-106">Recursos do ASP.NET incluem uma associação e provedor de função, um banco de dados para armazenar pares de nome e senha de usuário para autenticação e as funções de usuário para autorização.</span><span class="sxs-lookup"><span data-stu-id="dbe4a-106">ASP.NET features include a membership and role provider, a database to store user name/password pairs for authentication, and user roles for authorization.</span></span> <span data-ttu-id="dbe4a-107">Este tópico explica como os serviços WCF podem usar o mesmo banco de dados para autenticar e autorizar usuários.</span><span class="sxs-lookup"><span data-stu-id="dbe4a-107">This topic explains how WCF services can use the same database to authenticate and authorize users.</span></span>  
  
 [<span data-ttu-id="dbe4a-108">Como usar um nome de usuário e validador de senha personalizados</span><span class="sxs-lookup"><span data-stu-id="dbe4a-108">How to: Use a Custom User Name and Password Validator</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-a-custom-user-name-and-password-validator.md)  
 <span data-ttu-id="dbe4a-109">Demonstra como integrar um validador de nome e senha de usuário personalizada.</span><span class="sxs-lookup"><span data-stu-id="dbe4a-109">Demonstrates how to integrate a custom user name/password validator.</span></span>  
  
 [<span data-ttu-id="dbe4a-110">Autenticação e identidade de serviço</span><span class="sxs-lookup"><span data-stu-id="dbe4a-110">Service Identity and Authentication</span></span>](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 <span data-ttu-id="dbe4a-111">Como uma proteção extra, um cliente pode autenticar o serviço especificando o esperado *identidade* do serviço.</span><span class="sxs-lookup"><span data-stu-id="dbe4a-111">As an extra safeguard, a client can authenticate the service by specifying the expected *identity* of the service.</span></span> <span data-ttu-id="dbe4a-112">Se a identidade esperada e a identidade retornada pelo serviço não coincidirem, a autenticação falhará.</span><span class="sxs-lookup"><span data-stu-id="dbe4a-112">If the expected identity and the identity returned by the service do not match, authentication fails.</span></span>  
  
 [<span data-ttu-id="dbe4a-113">Negociação de segurança e tempos limite</span><span class="sxs-lookup"><span data-stu-id="dbe4a-113">Security Negotiation and Timeouts</span></span>](../../../../docs/framework/wcf/feature-details/security-negotiation-and-timeouts.md)  
 <span data-ttu-id="dbe4a-114">Descreve como usar o <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> propriedade o <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> classe.</span><span class="sxs-lookup"><span data-stu-id="dbe4a-114">Describes how to use the <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> property in the <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> class.</span></span>  
  
 [<span data-ttu-id="dbe4a-115">Depuração de erros de autenticação do Windows</span><span class="sxs-lookup"><span data-stu-id="dbe4a-115">Debugging Windows Authentication Errors</span></span>](../../../../docs/framework/wcf/feature-details/debugging-windows-authentication-errors.md)  
 <span data-ttu-id="dbe4a-116">Se concentra em problemas comuns encontrados ao usar a autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="dbe4a-116">Focuses on common problems encountered when using Windows authentication.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="dbe4a-117">Referência</span><span class="sxs-lookup"><span data-stu-id="dbe4a-117">Reference</span></span>  
 <xref:System.ServiceModel>  
  
## <a name="related-sections"></a><span data-ttu-id="dbe4a-118">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="dbe4a-118">Related Sections</span></span>  
 [<span data-ttu-id="dbe4a-119">Cenários comuns de segurança</span><span class="sxs-lookup"><span data-stu-id="dbe4a-119">Common Security Scenarios</span></span>](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)  
  
## <a name="see-also"></a><span data-ttu-id="dbe4a-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dbe4a-120">See Also</span></span>  
 [<span data-ttu-id="dbe4a-121">Visão geral de segurança</span><span class="sxs-lookup"><span data-stu-id="dbe4a-121">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [<span data-ttu-id="dbe4a-122">Modelo de segurança para o Windows Server App Fabric</span><span class="sxs-lookup"><span data-stu-id="dbe4a-122">Security Model for Windows Server App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
