---
title: "Autenticação no WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- authentication [WCF]
- security [WCF], authentication
ms.assetid: 9254d873-843d-4c6e-bea4-8184ac3e44f4
caps.latest.revision: "15"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6fbd4a322153bd9f560b6c039f586100770a0216
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="authentication-in-wcf"></a><span data-ttu-id="a8609-102">Autenticação no WCF</span><span class="sxs-lookup"><span data-stu-id="a8609-102">Authentication in WCF</span></span>
<span data-ttu-id="a8609-103">Os tópicos a seguir mostram um número de mecanismos diferentes em [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] que fornecem autenticação, por exemplo, a autenticação do Windows, certificados x. 509 e o nome de usuário e senhas.</span><span class="sxs-lookup"><span data-stu-id="a8609-103">The following topics show a number of different mechanisms in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] that provide authentication, for example, Windows authentication, X.509 certificates, and user name and passwords.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a8609-104">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="a8609-104">In This Section</span></span>  
 [<span data-ttu-id="a8609-105">Como: usar o provedor de associação do ASP.NET</span><span class="sxs-lookup"><span data-stu-id="a8609-105">How to: Use the ASP.NET Membership Provider</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md)  
 <span data-ttu-id="a8609-106">Recursos do ASP.NET incluem uma associação e provedor de função, um banco de dados para armazenar pares de nome e senha de usuário para autenticação e as funções de usuário para autorização.</span><span class="sxs-lookup"><span data-stu-id="a8609-106">ASP.NET features include a membership and role provider, a database to store user name/password pairs for authentication, and user roles for authorization.</span></span> <span data-ttu-id="a8609-107">Este tópico explica como [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviços podem usar o mesmo banco de dados para autenticar e autorizar usuários.</span><span class="sxs-lookup"><span data-stu-id="a8609-107">This topic explains how [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services can use the same database to authenticate and authorize users.</span></span>  
  
 [<span data-ttu-id="a8609-108">Como: usar um nome de usuário personalizada e validação de senha</span><span class="sxs-lookup"><span data-stu-id="a8609-108">How to: Use a Custom User Name and Password Validator</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-a-custom-user-name-and-password-validator.md)  
 <span data-ttu-id="a8609-109">Demonstra como integrar um validador de nome e senha de usuário personalizada.</span><span class="sxs-lookup"><span data-stu-id="a8609-109">Demonstrates how to integrate a custom user name/password validator.</span></span>  
  
 [<span data-ttu-id="a8609-110">Autenticação e identidade de serviço</span><span class="sxs-lookup"><span data-stu-id="a8609-110">Service Identity and Authentication</span></span>](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 <span data-ttu-id="a8609-111">Como uma proteção extra, um cliente pode autenticar o serviço especificando o esperado *identidade* do serviço.</span><span class="sxs-lookup"><span data-stu-id="a8609-111">As an extra safeguard, a client can authenticate the service by specifying the expected *identity* of the service.</span></span> <span data-ttu-id="a8609-112">Se a identidade esperada e a identidade retornada pelo serviço não coincidirem, a autenticação falhará.</span><span class="sxs-lookup"><span data-stu-id="a8609-112">If the expected identity and the identity returned by the service do not match, authentication fails.</span></span>  
  
 [<span data-ttu-id="a8609-113">Negociação de segurança e tempos limite</span><span class="sxs-lookup"><span data-stu-id="a8609-113">Security Negotiation and Timeouts</span></span>](../../../../docs/framework/wcf/feature-details/security-negotiation-and-timeouts.md)  
 <span data-ttu-id="a8609-114">Descreve como usar o <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> propriedade o <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> classe.</span><span class="sxs-lookup"><span data-stu-id="a8609-114">Describes how to use the <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> property in the <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> class.</span></span>  
  
 [<span data-ttu-id="a8609-115">Depuração de erros de autenticação do Windows</span><span class="sxs-lookup"><span data-stu-id="a8609-115">Debugging Windows Authentication Errors</span></span>](../../../../docs/framework/wcf/feature-details/debugging-windows-authentication-errors.md)  
 <span data-ttu-id="a8609-116">Se concentra em problemas comuns encontrados ao usar a autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="a8609-116">Focuses on common problems encountered when using Windows authentication.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="a8609-117">Referência</span><span class="sxs-lookup"><span data-stu-id="a8609-117">Reference</span></span>  
 <xref:System.ServiceModel>  
  
## <a name="related-sections"></a><span data-ttu-id="a8609-118">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="a8609-118">Related Sections</span></span>  
 [<span data-ttu-id="a8609-119">Cenários comuns de segurança</span><span class="sxs-lookup"><span data-stu-id="a8609-119">Common Security Scenarios</span></span>](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)  
  
## <a name="see-also"></a><span data-ttu-id="a8609-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a8609-120">See Also</span></span>  
 [<span data-ttu-id="a8609-121">Visão geral de segurança</span><span class="sxs-lookup"><span data-stu-id="a8609-121">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [<span data-ttu-id="a8609-122">Modelo de segurança para o Windows Server App Fabric</span><span class="sxs-lookup"><span data-stu-id="a8609-122">Security Model for Windows Server App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
