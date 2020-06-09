---
title: Autorização no WCF
ms.date: 03/30/2017
helpviewer_keywords:
- authorization [WCF]
- security [WCF], authorization
ms.assetid: 8ea0b552-af65-45b0-a157-c6c111b8ce5e
ms.openlocfilehash: d67d64dcf0003de28775ac947f8b5f72d7c2ba2a
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597625"
---
# <a name="authorization-in-wcf"></a><span data-ttu-id="44ede-102">Autorização no WCF</span><span class="sxs-lookup"><span data-stu-id="44ede-102">Authorization in WCF</span></span>
<span data-ttu-id="44ede-103">A autorização é o processo de controle de acesso e direitos a recursos, como serviços ou arquivos.</span><span class="sxs-lookup"><span data-stu-id="44ede-103">Authorization is the process of controlling access and rights to resources, such as services or files.</span></span> <span data-ttu-id="44ede-104">Os tópicos nesta seção mostram como executar essa tarefa básica no Windows Communication Foundation (WCF) de várias maneiras.</span><span class="sxs-lookup"><span data-stu-id="44ede-104">The topics in this section show you how to perform this basic task in Windows Communication Foundation (WCF) in a variety of ways.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="44ede-105">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="44ede-105">In This Section</span></span>  
 [<span data-ttu-id="44ede-106">Mecanismos de controle de acesso</span><span class="sxs-lookup"><span data-stu-id="44ede-106">Access Control Mechanisms</span></span>](access-control-mechanisms.md)  
 <span data-ttu-id="44ede-107">Fornece uma breve descrição dos mecanismos de autorização no WCF e usos sugeridos.</span><span class="sxs-lookup"><span data-stu-id="44ede-107">Provides a brief outline of the authorization mechanisms in WCF, and suggested uses.</span></span>  
  
 [<span data-ttu-id="44ede-108">Como restringir o acesso com a classe PrincipalPermissionAttribute</span><span class="sxs-lookup"><span data-stu-id="44ede-108">How to: Restrict Access with the PrincipalPermissionAttribute Class</span></span>](../how-to-restrict-access-with-the-principalpermissionattribute-class.md)  
 <span data-ttu-id="44ede-109">Mostra o processo de restringir o acesso a um serviço com o <xref:System.Security.Permissions.PrincipalPermissionAttribute> .</span><span class="sxs-lookup"><span data-stu-id="44ede-109">Shows the process of restricting access to a service with the <xref:System.Security.Permissions.PrincipalPermissionAttribute>.</span></span>  
  
 [<span data-ttu-id="44ede-110">Como utilizar o provedor de função do ASP.NET com um serviço</span><span class="sxs-lookup"><span data-stu-id="44ede-110">How to: Use the ASP.NET Role Provider with a Service</span></span>](how-to-use-the-aspnet-role-provider-with-a-service.md)  
 <span data-ttu-id="44ede-111">Percorre a configuração de um serviço para habilitá-lo a usar o recurso de provedor de função do ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="44ede-111">Walks through the configuration of a service to enable it to use the role provider feature of ASP.NET.</span></span>  
  
 [<span data-ttu-id="44ede-112">Como usar o provedor de função do gerenciador de autorização do ASP.NET com um serviço</span><span class="sxs-lookup"><span data-stu-id="44ede-112">How to: Use the ASP.NET Authorization Manager Role Provider with a Service</span></span>](how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service.md)  
 <span data-ttu-id="44ede-113">O ASP.NET pode usar o Gerenciador de autorização para gerenciar a autorização de um site da Web.</span><span class="sxs-lookup"><span data-stu-id="44ede-113">ASP.NET can use the Authorization Manager to manage authorization for a Web site.</span></span> <span data-ttu-id="44ede-114">Da mesma forma, o WCF pode aproveitar a combinação do Gerenciador de ASP.NET/Authorization para autorização de clientes.</span><span class="sxs-lookup"><span data-stu-id="44ede-114">WCF can similarly leverage the ASP.NET/Authorization Manager combination for authorization of clients.</span></span>  
  
 [<span data-ttu-id="44ede-115">Gerenciamento de declarações e autorizações com o modelo de identidade</span><span class="sxs-lookup"><span data-stu-id="44ede-115">Managing Claims and Authorization with the Identity Model</span></span>](managing-claims-and-authorization-with-the-identity-model.md)  
 <span data-ttu-id="44ede-116">Explica as noções básicas do uso da infraestrutura do modelo de identidade para autorização baseada em declarações.</span><span class="sxs-lookup"><span data-stu-id="44ede-116">Explains the basics of using the Identity Model infrastructure for claims-based authorization.</span></span>  
  
 [<span data-ttu-id="44ede-117">Delegação e representação</span><span class="sxs-lookup"><span data-stu-id="44ede-117">Delegation and Impersonation</span></span>](delegation-and-impersonation-with-wcf.md)  
 <span data-ttu-id="44ede-118">Explica a diferença entre delegação e representação.</span><span class="sxs-lookup"><span data-stu-id="44ede-118">Explains the difference between delegation and impersonation.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="44ede-119">Referência</span><span class="sxs-lookup"><span data-stu-id="44ede-119">Reference</span></span>  
 <xref:System.ServiceModel.Security>  
  
 <xref:System.ServiceModel.Description.PrincipalPermissionMode>  
  
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>  
  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute>  
  
## <a name="related-sections"></a><span data-ttu-id="44ede-120">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="44ede-120">Related Sections</span></span>  
 [<span data-ttu-id="44ede-121">Autenticação</span><span class="sxs-lookup"><span data-stu-id="44ede-121">Authentication</span></span>](authentication-in-wcf.md)  
  
## <a name="see-also"></a><span data-ttu-id="44ede-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="44ede-122">See also</span></span>

- [<span data-ttu-id="44ede-123">Visão geral de segurança</span><span class="sxs-lookup"><span data-stu-id="44ede-123">Security Overview</span></span>](security-overview.md)
- <span data-ttu-id="44ede-124">[Modelo de segurança para o Windows Server app Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="44ede-124">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
