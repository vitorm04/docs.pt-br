---
title: ServiceAuthorizationBehavior
ms.date: 03/30/2017
ms.assetid: 77dad8e8-fea4-4d1c-b366-2f01a2a87f78
ms.openlocfilehash: 51555e3357b8c33a53261c4894d97798b0a05656
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61957049"
---
# <a name="serviceauthorizationbehavior"></a><span data-ttu-id="3ff4e-102">ServiceAuthorizationBehavior</span><span class="sxs-lookup"><span data-stu-id="3ff4e-102">ServiceAuthorizationBehavior</span></span>
<span data-ttu-id="3ff4e-103">ServiceAuthorizationBehavior</span><span class="sxs-lookup"><span data-stu-id="3ff4e-103">ServiceAuthorizationBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ff4e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3ff4e-104">Syntax</span></span>  
  
```csharp
class ServiceAuthorizationBehavior : Behavior  
{  
  boolean ImpersonateCallerForAllOperations;  
  string PrincipalPermissionMode;  
  string RoleProvider;  
  string ServiceAuthorizationManager;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="3ff4e-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="3ff4e-105">Methods</span></span>  
 <span data-ttu-id="3ff4e-106">A classe ServiceAuthorizationBehavior não define quaisquer métodos.</span><span class="sxs-lookup"><span data-stu-id="3ff4e-106">The ServiceAuthorizationBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="3ff4e-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="3ff4e-107">Properties</span></span>  
 <span data-ttu-id="3ff4e-108">A classe ServiceAuthorizationBehavior tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="3ff4e-108">The ServiceAuthorizationBehavior class has the following properties:</span></span>  
  
### <a name="impersonatecallerforalloperations"></a><span data-ttu-id="3ff4e-109">ImpersonateCallerForAllOperations</span><span class="sxs-lookup"><span data-stu-id="3ff4e-109">ImpersonateCallerForAllOperations</span></span>  
 <span data-ttu-id="3ff4e-110">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="3ff4e-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="3ff4e-111">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="3ff4e-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3ff4e-112">Um valor que controla se o serviço tentará representar usando as credenciais fornecidas pela mensagem de entrada.</span><span class="sxs-lookup"><span data-stu-id="3ff4e-112">A value that controls whether the service attempts to impersonate using the credentials provided by the incoming message.</span></span>  
  
### <a name="principalpermissionmode"></a><span data-ttu-id="3ff4e-113">PrincipalPermissionMode</span><span class="sxs-lookup"><span data-stu-id="3ff4e-113">PrincipalPermissionMode</span></span>  
 <span data-ttu-id="3ff4e-114">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="3ff4e-114">Data type: string</span></span>  
  
 <span data-ttu-id="3ff4e-115">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="3ff4e-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3ff4e-116">A entidade de segurança usada para executar operações no servidor.</span><span class="sxs-lookup"><span data-stu-id="3ff4e-116">The principal used to carry out operations on the server.</span></span>  
  
### <a name="roleprovider"></a><span data-ttu-id="3ff4e-117">RoleProvider</span><span class="sxs-lookup"><span data-stu-id="3ff4e-117">RoleProvider</span></span>  
 <span data-ttu-id="3ff4e-118">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="3ff4e-118">Data type: string</span></span>  
  
 <span data-ttu-id="3ff4e-119">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="3ff4e-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3ff4e-120">O nome do provedor de função ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="3ff4e-120">The name of the ASP.NET role provider.</span></span>  
  
### <a name="serviceauthorizationmanager"></a><span data-ttu-id="3ff4e-121">ServiceAuthorizationManager</span><span class="sxs-lookup"><span data-stu-id="3ff4e-121">ServiceAuthorizationManager</span></span>  
 <span data-ttu-id="3ff4e-122">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="3ff4e-122">Data type: string</span></span>  
  
 <span data-ttu-id="3ff4e-123">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="3ff4e-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3ff4e-124">O Gerenciador de autorização usado para autorização personalizada.</span><span class="sxs-lookup"><span data-stu-id="3ff4e-124">The authorization manager used for custom authorization.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3ff4e-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3ff4e-125">Requirements</span></span>  
  
|<span data-ttu-id="3ff4e-126">MOF</span><span class="sxs-lookup"><span data-stu-id="3ff4e-126">MOF</span></span>|<span data-ttu-id="3ff4e-127">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="3ff4e-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="3ff4e-128">Namespace</span><span class="sxs-lookup"><span data-stu-id="3ff4e-128">Namespace</span></span>|<span data-ttu-id="3ff4e-129">Definido no root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="3ff4e-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3ff4e-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3ff4e-130">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
