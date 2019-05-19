---
title: Autorização no WCF
ms.date: 03/30/2017
helpviewer_keywords:
- authorization [WCF]
- security [WCF], authorization
ms.assetid: 8ea0b552-af65-45b0-a157-c6c111b8ce5e
ms.openlocfilehash: 8c605b310f19a05f994296d8f4268b91b408fb18
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2019
ms.locfileid: "65881204"
---
# <a name="authorization-in-wcf"></a><span data-ttu-id="73c94-102">Autorização no WCF</span><span class="sxs-lookup"><span data-stu-id="73c94-102">Authorization in WCF</span></span>
<span data-ttu-id="73c94-103">A autorização é o processo de controle de acesso e os direitos aos recursos, como os serviços ou arquivos.</span><span class="sxs-lookup"><span data-stu-id="73c94-103">Authorization is the process of controlling access and rights to resources, such as services or files.</span></span> <span data-ttu-id="73c94-104">Os tópicos nesta seção mostram como executar essa tarefa básica no Windows Communication Foundation (WCF) em uma variedade de formas.</span><span class="sxs-lookup"><span data-stu-id="73c94-104">The topics in this section show you how to perform this basic task in Windows Communication Foundation (WCF) in a variety of ways.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="73c94-105">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="73c94-105">In This Section</span></span>  
 [<span data-ttu-id="73c94-106">Mecanismos de controle de acesso</span><span class="sxs-lookup"><span data-stu-id="73c94-106">Access Control Mechanisms</span></span>](../../../../docs/framework/wcf/feature-details/access-control-mechanisms.md)  
 <span data-ttu-id="73c94-107">Fornece uma breve descrição dos mecanismos de autorização no WCF e usa sugeridas.</span><span class="sxs-lookup"><span data-stu-id="73c94-107">Provides a brief outline of the authorization mechanisms in WCF, and suggested uses.</span></span>  
  
 [<span data-ttu-id="73c94-108">Como: Restringir o acesso com a PrincipalPermissionAttribute Class</span><span class="sxs-lookup"><span data-stu-id="73c94-108">How to: Restrict Access with the PrincipalPermissionAttribute Class</span></span>](../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)  
 <span data-ttu-id="73c94-109">Mostra o processo de restringir o acesso a um serviço com o <xref:System.Security.Permissions.PrincipalPermissionAttribute>.</span><span class="sxs-lookup"><span data-stu-id="73c94-109">Shows the process of restricting access to a service with the <xref:System.Security.Permissions.PrincipalPermissionAttribute>.</span></span>  
  
 [<span data-ttu-id="73c94-110">Como: Usar o provedor de função ASP.NET com um serviço</span><span class="sxs-lookup"><span data-stu-id="73c94-110">How to: Use the ASP.NET Role Provider with a Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)  
 <span data-ttu-id="73c94-111">Percorre a configuração de um serviço para habilitá-lo para usar o recurso de provedor de função do ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="73c94-111">Walks through the configuration of a service to enable it to use the role provider feature of ASP.NET.</span></span>  
  
 [<span data-ttu-id="73c94-112">Como: Usar o provedor de função do Gerenciador de autorização do ASP.NET com um serviço</span><span class="sxs-lookup"><span data-stu-id="73c94-112">How to: Use the ASP.NET Authorization Manager Role Provider with a Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service.md)  
 <span data-ttu-id="73c94-113">ASP.NET pode usar o Gerenciador de autorização para gerenciar a autorização para um site da Web.</span><span class="sxs-lookup"><span data-stu-id="73c94-113">ASP.NET can use the Authorization Manager to manage authorization for a Web site.</span></span> <span data-ttu-id="73c94-114">WCF da mesma forma pode aproveitar a combinação de ASP.NET/Authorization Gerenciador de autorização de clientes.</span><span class="sxs-lookup"><span data-stu-id="73c94-114">WCF can similarly leverage the ASP.NET/Authorization Manager combination for authorization of clients.</span></span>  
  
 [<span data-ttu-id="73c94-115">Gerenciando reivindicações e autorização com o modelo de identidade</span><span class="sxs-lookup"><span data-stu-id="73c94-115">Managing Claims and Authorization with the Identity Model</span></span>](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)  
 <span data-ttu-id="73c94-116">Explica as Noções básicas de como usar a infraestrutura do modelo de identidade para autorização baseada em declarações.</span><span class="sxs-lookup"><span data-stu-id="73c94-116">Explains the basics of using the Identity Model infrastructure for claims-based authorization.</span></span>  
  
 [<span data-ttu-id="73c94-117">Delegação e representação</span><span class="sxs-lookup"><span data-stu-id="73c94-117">Delegation and Impersonation</span></span>](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)  
 <span data-ttu-id="73c94-118">Explica a diferença entre a delegação e representação.</span><span class="sxs-lookup"><span data-stu-id="73c94-118">Explains the difference between delegation and impersonation.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="73c94-119">Referência</span><span class="sxs-lookup"><span data-stu-id="73c94-119">Reference</span></span>  
 <xref:System.ServiceModel.Security>  
  
 <xref:System.ServiceModel.Description.PrincipalPermissionMode>  
  
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>  
  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute>  
  
## <a name="related-sections"></a><span data-ttu-id="73c94-120">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="73c94-120">Related Sections</span></span>  
 [<span data-ttu-id="73c94-121">Autenticação</span><span class="sxs-lookup"><span data-stu-id="73c94-121">Authentication</span></span>](../../../../docs/framework/wcf/feature-details/authentication-in-wcf.md)  
  
## <a name="see-also"></a><span data-ttu-id="73c94-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="73c94-122">See also</span></span>

- [<span data-ttu-id="73c94-123">Visão geral de segurança</span><span class="sxs-lookup"><span data-stu-id="73c94-123">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [<span data-ttu-id="73c94-124">Modelo de segurança do Windows Server App Fabric</span><span class="sxs-lookup"><span data-stu-id="73c94-124">Security Model for Windows Server App Fabric</span></span>](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
