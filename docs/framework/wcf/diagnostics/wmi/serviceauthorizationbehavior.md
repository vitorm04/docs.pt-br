---
title: ServiceAuthorizationBehavior
ms.date: 03/30/2017
ms.assetid: 77dad8e8-fea4-4d1c-b366-2f01a2a87f78
ms.openlocfilehash: 58eb2a9fd9017aaf9966644180936f5871e086d1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54613890"
---
# <a name="serviceauthorizationbehavior"></a><span data-ttu-id="7177b-102">ServiceAuthorizationBehavior</span><span class="sxs-lookup"><span data-stu-id="7177b-102">ServiceAuthorizationBehavior</span></span>
<span data-ttu-id="7177b-103">ServiceAuthorizationBehavior</span><span class="sxs-lookup"><span data-stu-id="7177b-103">ServiceAuthorizationBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7177b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7177b-104">Syntax</span></span>  
  
```csharp
class ServiceAuthorizationBehavior : Behavior  
{  
  boolean ImpersonateCallerForAllOperations;  
  string PrincipalPermissionMode;  
  string RoleProvider;  
  string ServiceAuthorizationManager;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="7177b-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="7177b-105">Methods</span></span>  
 <span data-ttu-id="7177b-106">A classe ServiceAuthorizationBehavior não define quaisquer métodos.</span><span class="sxs-lookup"><span data-stu-id="7177b-106">The ServiceAuthorizationBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="7177b-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="7177b-107">Properties</span></span>  
 <span data-ttu-id="7177b-108">A classe ServiceAuthorizationBehavior tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="7177b-108">The ServiceAuthorizationBehavior class has the following properties:</span></span>  
  
### <a name="impersonatecallerforalloperations"></a><span data-ttu-id="7177b-109">ImpersonateCallerForAllOperations</span><span class="sxs-lookup"><span data-stu-id="7177b-109">ImpersonateCallerForAllOperations</span></span>  
 <span data-ttu-id="7177b-110">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="7177b-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="7177b-111">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="7177b-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7177b-112">Um valor que controla se o serviço tentará representar usando as credenciais fornecidas pela mensagem de entrada.</span><span class="sxs-lookup"><span data-stu-id="7177b-112">A value that controls whether the service attempts to impersonate using the credentials provided by the incoming message.</span></span>  
  
### <a name="principalpermissionmode"></a><span data-ttu-id="7177b-113">PrincipalPermissionMode</span><span class="sxs-lookup"><span data-stu-id="7177b-113">PrincipalPermissionMode</span></span>  
 <span data-ttu-id="7177b-114">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="7177b-114">Data type: string</span></span>  
  
 <span data-ttu-id="7177b-115">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="7177b-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7177b-116">A entidade de segurança usada para executar operações no servidor.</span><span class="sxs-lookup"><span data-stu-id="7177b-116">The principal used to carry out operations on the server.</span></span>  
  
### <a name="roleprovider"></a><span data-ttu-id="7177b-117">RoleProvider</span><span class="sxs-lookup"><span data-stu-id="7177b-117">RoleProvider</span></span>  
 <span data-ttu-id="7177b-118">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="7177b-118">Data type: string</span></span>  
  
 <span data-ttu-id="7177b-119">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="7177b-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7177b-120">O nome do provedor de função ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="7177b-120">The name of the ASP.NET role provider.</span></span>  
  
### <a name="serviceauthorizationmanager"></a><span data-ttu-id="7177b-121">ServiceAuthorizationManager</span><span class="sxs-lookup"><span data-stu-id="7177b-121">ServiceAuthorizationManager</span></span>  
 <span data-ttu-id="7177b-122">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="7177b-122">Data type: string</span></span>  
  
 <span data-ttu-id="7177b-123">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="7177b-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7177b-124">O Gerenciador de autorização usado para autorização personalizada.</span><span class="sxs-lookup"><span data-stu-id="7177b-124">The authorization manager used for custom authorization.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7177b-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7177b-125">Requirements</span></span>  
  
|<span data-ttu-id="7177b-126">MOF</span><span class="sxs-lookup"><span data-stu-id="7177b-126">MOF</span></span>|<span data-ttu-id="7177b-127">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="7177b-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="7177b-128">Namespace</span><span class="sxs-lookup"><span data-stu-id="7177b-128">Namespace</span></span>|<span data-ttu-id="7177b-129">Definido no root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="7177b-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7177b-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7177b-130">See also</span></span>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
