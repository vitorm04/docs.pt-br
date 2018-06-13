---
title: ServiceAuthorizationBehavior
ms.date: 03/30/2017
ms.assetid: 77dad8e8-fea4-4d1c-b366-2f01a2a87f78
ms.openlocfilehash: e03f83927ec5aef7f916b2262c9c8cff1db68ac9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33486467"
---
# <a name="serviceauthorizationbehavior"></a><span data-ttu-id="e04d8-102">ServiceAuthorizationBehavior</span><span class="sxs-lookup"><span data-stu-id="e04d8-102">ServiceAuthorizationBehavior</span></span>
<span data-ttu-id="e04d8-103">ServiceAuthorizationBehavior</span><span class="sxs-lookup"><span data-stu-id="e04d8-103">ServiceAuthorizationBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e04d8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e04d8-104">Syntax</span></span>  
  
```  
class ServiceAuthorizationBehavior : Behavior  
{  
  boolean ImpersonateCallerForAllOperations;  
  string PrincipalPermissionMode;  
  string RoleProvider;  
  string ServiceAuthorizationManager;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="e04d8-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="e04d8-105">Methods</span></span>  
 <span data-ttu-id="e04d8-106">A classe ServiceAuthorizationBehavior não define nenhum método.</span><span class="sxs-lookup"><span data-stu-id="e04d8-106">The ServiceAuthorizationBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="e04d8-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="e04d8-107">Properties</span></span>  
 <span data-ttu-id="e04d8-108">A classe ServiceAuthorizationBehavior tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="e04d8-108">The ServiceAuthorizationBehavior class has the following properties:</span></span>  
  
### <a name="impersonatecallerforalloperations"></a><span data-ttu-id="e04d8-109">ImpersonateCallerForAllOperations</span><span class="sxs-lookup"><span data-stu-id="e04d8-109">ImpersonateCallerForAllOperations</span></span>  
 <span data-ttu-id="e04d8-110">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="e04d8-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="e04d8-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="e04d8-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e04d8-112">Um valor que controla se o serviço tenta representar usando as credenciais fornecidas pela mensagem de entrada.</span><span class="sxs-lookup"><span data-stu-id="e04d8-112">A value that controls whether the service attempts to impersonate using the credentials provided by the incoming message.</span></span>  
  
### <a name="principalpermissionmode"></a><span data-ttu-id="e04d8-113">PrincipalPermissionMode</span><span class="sxs-lookup"><span data-stu-id="e04d8-113">PrincipalPermissionMode</span></span>  
 <span data-ttu-id="e04d8-114">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="e04d8-114">Data type: string</span></span>  
  
 <span data-ttu-id="e04d8-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="e04d8-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e04d8-116">O principal usado para realizar operações no servidor.</span><span class="sxs-lookup"><span data-stu-id="e04d8-116">The principal used to carry out operations on the server.</span></span>  
  
### <a name="roleprovider"></a><span data-ttu-id="e04d8-117">Propriedade RoleProvider</span><span class="sxs-lookup"><span data-stu-id="e04d8-117">RoleProvider</span></span>  
 <span data-ttu-id="e04d8-118">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="e04d8-118">Data type: string</span></span>  
  
 <span data-ttu-id="e04d8-119">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="e04d8-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e04d8-120">O nome do provedor de função ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="e04d8-120">The name of the ASP.NET role provider.</span></span>  
  
### <a name="serviceauthorizationmanager"></a><span data-ttu-id="e04d8-121">ServiceAuthorizationManager</span><span class="sxs-lookup"><span data-stu-id="e04d8-121">ServiceAuthorizationManager</span></span>  
 <span data-ttu-id="e04d8-122">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="e04d8-122">Data type: string</span></span>  
  
 <span data-ttu-id="e04d8-123">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="e04d8-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e04d8-124">O Gerenciador de autorização usado para autorização personalizada.</span><span class="sxs-lookup"><span data-stu-id="e04d8-124">The authorization manager used for custom authorization.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e04d8-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e04d8-125">Requirements</span></span>  
  
|<span data-ttu-id="e04d8-126">MOF</span><span class="sxs-lookup"><span data-stu-id="e04d8-126">MOF</span></span>|<span data-ttu-id="e04d8-127">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="e04d8-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="e04d8-128">Namespace</span><span class="sxs-lookup"><span data-stu-id="e04d8-128">Namespace</span></span>|<span data-ttu-id="e04d8-129">Definido em root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="e04d8-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e04d8-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e04d8-130">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
