---
title: Autorização no WCF
ms.date: 03/30/2017
helpviewer_keywords:
- authorization [WCF]
- security [WCF], authorization
ms.assetid: 8ea0b552-af65-45b0-a157-c6c111b8ce5e
ms.openlocfilehash: c6bf779c7baeea1f9a253ad0bde966cea67b57aa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33488566"
---
# <a name="authorization-in-wcf"></a><span data-ttu-id="612d1-102">Autorização no WCF</span><span class="sxs-lookup"><span data-stu-id="612d1-102">Authorization in WCF</span></span>
<span data-ttu-id="612d1-103">A autorização é o processo de controle de acesso e direitos a recursos, como arquivos ou serviços.</span><span class="sxs-lookup"><span data-stu-id="612d1-103">Authorization is the process of controlling access and rights to resources, such as services or files.</span></span> <span data-ttu-id="612d1-104">Os tópicos nesta seção mostram como executar essa tarefa básica no Windows Communication Foundation (WCF) em uma variedade de maneiras.</span><span class="sxs-lookup"><span data-stu-id="612d1-104">The topics in this section show you how to perform this basic task in Windows Communication Foundation (WCF) in a variety of ways.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="612d1-105">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="612d1-105">In This Section</span></span>  
 [<span data-ttu-id="612d1-106">Mecanismos de controle de acesso</span><span class="sxs-lookup"><span data-stu-id="612d1-106">Access Control Mechanisms</span></span>](../../../../docs/framework/wcf/feature-details/access-control-mechanisms.md)  
 <span data-ttu-id="612d1-107">Fornece uma breve descrição dos mecanismos de autorização do WCF e usa sugeridas.</span><span class="sxs-lookup"><span data-stu-id="612d1-107">Provides a brief outline of the authorization mechanisms in WCF, and suggested uses.</span></span>  
  
 [<span data-ttu-id="612d1-108">Como restringir o acesso com a classe PrincipalPermissionAttribute</span><span class="sxs-lookup"><span data-stu-id="612d1-108">How to: Restrict Access with the PrincipalPermissionAttribute Class</span></span>](../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)  
 <span data-ttu-id="612d1-109">Mostra o processo de restringir o acesso a um serviço com o <xref:System.Security.Permissions.PrincipalPermissionAttribute>.</span><span class="sxs-lookup"><span data-stu-id="612d1-109">Shows the process of restricting access to a service with the <xref:System.Security.Permissions.PrincipalPermissionAttribute>.</span></span>  
  
 [<span data-ttu-id="612d1-110">Como usar o provedor de função ASP.NET com um serviço</span><span class="sxs-lookup"><span data-stu-id="612d1-110">How to: Use the ASP.NET Role Provider with a Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)  
 <span data-ttu-id="612d1-111">Explica a configuração de um serviço para habilitá-lo para usar o recurso de provedor de função do [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)].</span><span class="sxs-lookup"><span data-stu-id="612d1-111">Walks through the configuration of a service to enable it to use the role provider feature of [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)].</span></span>  
  
 [<span data-ttu-id="612d1-112">Como usar o provedor de função do gerenciador de autorização do ASP.NET com um serviço</span><span class="sxs-lookup"><span data-stu-id="612d1-112">How to: Use the ASP.NET Authorization Manager Role Provider with a Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service.md)  
 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]<span data-ttu-id="612d1-113"> pode usar o Gerenciador de autorização para gerenciar a autorização para um site da Web.</span><span class="sxs-lookup"><span data-stu-id="612d1-113"> can use the Authorization Manager to manage authorization for a Web site.</span></span> <span data-ttu-id="612d1-114">WCF de maneira semelhante pode aproveitar o [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]combinação /Authorization Gerenciador de autorização de clientes.</span><span class="sxs-lookup"><span data-stu-id="612d1-114">WCF can similarly leverage the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]/Authorization Manager combination for authorization of clients.</span></span>  
  
 [<span data-ttu-id="612d1-115">Gerenciando reivindicações e autorização com o modelo de identidade</span><span class="sxs-lookup"><span data-stu-id="612d1-115">Managing Claims and Authorization with the Identity Model</span></span>](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)  
 <span data-ttu-id="612d1-116">Explica os conceitos básicos de como usar a infraestrutura do modelo de identidade para autorização baseada em declarações.</span><span class="sxs-lookup"><span data-stu-id="612d1-116">Explains the basics of using the Identity Model infrastructure for claims-based authorization.</span></span>  
  
 [<span data-ttu-id="612d1-117">Delegação e representação</span><span class="sxs-lookup"><span data-stu-id="612d1-117">Delegation and Impersonation</span></span>](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)  
 <span data-ttu-id="612d1-118">Explica a diferença entre a delegação e representação.</span><span class="sxs-lookup"><span data-stu-id="612d1-118">Explains the difference between delegation and impersonation.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="612d1-119">Referência</span><span class="sxs-lookup"><span data-stu-id="612d1-119">Reference</span></span>  
 <xref:System.ServiceModel.Security>  
  
 <xref:System.ServiceModel.Description.PrincipalPermissionMode>  
  
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>  
  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute>  
  
## <a name="related-sections"></a><span data-ttu-id="612d1-120">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="612d1-120">Related Sections</span></span>  
 [<span data-ttu-id="612d1-121">Autenticação</span><span class="sxs-lookup"><span data-stu-id="612d1-121">Authentication</span></span>](../../../../docs/framework/wcf/feature-details/authentication-in-wcf.md)  
  
## <a name="see-also"></a><span data-ttu-id="612d1-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="612d1-122">See Also</span></span>  
 [<span data-ttu-id="612d1-123">Visão geral de segurança</span><span class="sxs-lookup"><span data-stu-id="612d1-123">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [<span data-ttu-id="612d1-124">Modelo de segurança para o Windows Server App Fabric</span><span class="sxs-lookup"><span data-stu-id="612d1-124">Security Model for Windows Server App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
