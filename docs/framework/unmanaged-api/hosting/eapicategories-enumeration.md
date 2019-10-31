---
title: Enumeração EApiCategories
ms.date: 03/30/2017
api_name:
- EApiCategories
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EApiCategories
helpviewer_keywords:
- EApiCategories enumeration [.NET Framework hosting]
ms.assetid: 3c4a8a5a-8a46-4ac9-947f-4959bc9d6ac6
topic_type:
- apiref
ms.openlocfilehash: 0fd9409a5157e1013365c94f01631f130a76f54b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131208"
---
# <a name="eapicategories-enumeration"></a><span data-ttu-id="48324-102">Enumeração EApiCategories</span><span class="sxs-lookup"><span data-stu-id="48324-102">EApiCategories Enumeration</span></span>
<span data-ttu-id="48324-103">Descreve as categorias de recursos que o host pode bloquear de ser executado em código parcialmente confiável.</span><span class="sxs-lookup"><span data-stu-id="48324-103">Describes the categories of capabilities that the host can block from running in partially trusted code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48324-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="48324-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    eNoCategory               = 0,  
    eSynchronization          = 0x1,  
    eSharedState              = 0x2,  
    eExternalProcessMgmt      = 0x4,  
    eSelfAffectingProcessMgmt = 0x8,  
    eExternalThreading        = 0x10,  
    eSelfAffectingThreading   = 0x20,  
    eSecurityInfrastructure   = 0x40,  
    eUI                       = 0x80,  
    eMayLeakOnAbort           = 0x100,  
    eAll                      = 0x1ff  
} EHostProtectionCategories;  
```  
  
## <a name="members"></a><span data-ttu-id="48324-105">Membros</span><span class="sxs-lookup"><span data-stu-id="48324-105">Members</span></span>  
  
|<span data-ttu-id="48324-106">Membro</span><span class="sxs-lookup"><span data-stu-id="48324-106">Member</span></span>|<span data-ttu-id="48324-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="48324-107">Description</span></span>|  
|------------|-----------------|  
|`eAll`|<span data-ttu-id="48324-108">Especifica que todas as classes e membros gerenciados que são cobertos por outros `EApiCategories` campos sejam impedidos de serem executados em código parcialmente confiável.</span><span class="sxs-lookup"><span data-stu-id="48324-108">Specifies that all managed classes and members that are covered by other `EApiCategories` fields be blocked from running in partially trusted code.</span></span>|  
|`eExternalProcessMgmt`|<span data-ttu-id="48324-109">Especifica que classes e membros gerenciados que permitem a criação, manipulação e destruição de processos externos sejam impedidos de serem executados em código parcialmente confiável.</span><span class="sxs-lookup"><span data-stu-id="48324-109">Specifies that managed classes and members that allow the creation, manipulation, and destruction of external processes be blocked from running in partially trusted code.</span></span>|  
|`eExternalThreading`|<span data-ttu-id="48324-110">Especifica que classes e membros gerenciados que permitem a criação, manipulação e destruição de threads externos sejam impedidos de serem executados em código parcialmente confiável.</span><span class="sxs-lookup"><span data-stu-id="48324-110">Specifies that managed classes and members that allow the creation, manipulation, and destruction of external threads be blocked from running in partially trusted code.</span></span>|  
|`eMayLeakOnAbort`|<span data-ttu-id="48324-111">Especifica que os tipos gerenciados e membros que poderiam vazar memória em anulação sejam impedidos de serem executados em código parcialmente confiável.</span><span class="sxs-lookup"><span data-stu-id="48324-111">Specifies that managed types and members that could potentially leak memory on abort be blocked from running in partially trusted code.</span></span>|  
|`eNoCategory`|<span data-ttu-id="48324-112">Especifica que nenhuma categoria de código gerenciado será impedida de ser executada em código parcialmente confiável.</span><span class="sxs-lookup"><span data-stu-id="48324-112">Specifies that no managed code categories be blocked from running in partially trusted code.</span></span>|  
|`eSecurityInfrastructure`|<span data-ttu-id="48324-113">Especifica que a infraestrutura de segurança Common Language Runtime (CLR) seja impedida de ser usada pelo código parcialmente confiável.</span><span class="sxs-lookup"><span data-stu-id="48324-113">Specifies that the common language runtime (CLR) security infrastructure be blocked from being used by partially trusted code.</span></span>|  
|`eSelfAffectingProcessMgmt`|<span data-ttu-id="48324-114">Especifica que classes e membros gerenciados cujos recursos podem afetar o processo hospedado sejam impedidos de serem executados em código parcialmente confiável.</span><span class="sxs-lookup"><span data-stu-id="48324-114">Specifies that managed classes and members whose capabilities can affect the hosted process be blocked from running in partially trusted code.</span></span>|  
|`eSelfAffectingThreading`|<span data-ttu-id="48324-115">Especifica que classes e membros gerenciados cujos recursos podem afetar threads no processo hospedado serão impedidos de serem executados em código parcialmente confiável.</span><span class="sxs-lookup"><span data-stu-id="48324-115">Specifies that managed classes and members whose capabilities can affect threads in the hosted process be blocked from running in partially trusted code.</span></span>|  
|`eSharedState`|<span data-ttu-id="48324-116">Especifica que classes e membros gerenciados que expõem o estado compartilhado sejam impedidos de serem executados em código parcialmente confiável.</span><span class="sxs-lookup"><span data-stu-id="48324-116">Specifies that managed classes and members that expose shared state be blocked from running in partially trusted code.</span></span>|  
|`eSynchronization`|<span data-ttu-id="48324-117">Especifica que Common Language Runtime classes e membros que permitem que o código do usuário mantenha bloqueios sejam impedidos de serem executados em código parcialmente confiável.</span><span class="sxs-lookup"><span data-stu-id="48324-117">Specifies that common language runtime classes and members that allow user code to hold locks be blocked from running in partially trusted code.</span></span>|  
|`eUI`|<span data-ttu-id="48324-118">Especifica que classes e membros gerenciados que permitem ou exigem interação humana são impedidos de serem executados em código parcialmente confiável.</span><span class="sxs-lookup"><span data-stu-id="48324-118">Specifies that managed classes and members that allow or require human interaction be blocked from running in partially trusted code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="48324-119">Comentários</span><span class="sxs-lookup"><span data-stu-id="48324-119">Remarks</span></span>  
 <span data-ttu-id="48324-120">O método [ICLRHostProtectionManager:: SetProtectedCategories](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-setprotectedcategories-method.md) usa um parâmetro do tipo `EApiCategories`.</span><span class="sxs-lookup"><span data-stu-id="48324-120">The [ICLRHostProtectionManager::SetProtectedCategories](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-setprotectedcategories-method.md) method takes a parameter of type `EApiCategories`.</span></span>  
  
 <span data-ttu-id="48324-121">A enumeração `EApiCategories` e o método `SetProtectedCategories` estão diretamente relacionados à classe <xref:System.Security.Permissions.HostProtectionAttribute?displayProperty=nameWithType> gerenciada.</span><span class="sxs-lookup"><span data-stu-id="48324-121">The `EApiCategories` enumeration and the `SetProtectedCategories` method are directly related to the managed <xref:System.Security.Permissions.HostProtectionAttribute?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="48324-122">A classe gerenciada é usada com a enumeração <xref:System.Security.Permissions.HostProtectionResource?displayProperty=nameWithType>, cujos valores correspondem diretamente aos valores de `EApiCategories`, para marcar tipos gerenciados e membros que expõem recursos correspondentes às categorias descritas por `EApiCategories`.</span><span class="sxs-lookup"><span data-stu-id="48324-122">The managed class is used with the <xref:System.Security.Permissions.HostProtectionResource?displayProperty=nameWithType> enumeration, whose values correspond directly to the `EApiCategories` values, to mark managed types and members that expose capabilities corresponding to the categories described by `EApiCategories`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="48324-123">Requisitos</span><span class="sxs-lookup"><span data-stu-id="48324-123">Requirements</span></span>  
 <span data-ttu-id="48324-124">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="48324-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="48324-125">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="48324-125">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="48324-126">**Biblioteca:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="48324-126">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="48324-127">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="48324-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48324-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="48324-128">See also</span></span>

- [<span data-ttu-id="48324-129">Interface ICLRHostProtectionManager</span><span class="sxs-lookup"><span data-stu-id="48324-129">ICLRHostProtectionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)
- [<span data-ttu-id="48324-130">Enumerações de hospedagem</span><span class="sxs-lookup"><span data-stu-id="48324-130">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
