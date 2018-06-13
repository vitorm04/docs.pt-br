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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f25348410387a7b0e03ef897e8534336baeb126a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33432203"
---
# <a name="eapicategories-enumeration"></a><span data-ttu-id="daffc-102">Enumeração EApiCategories</span><span class="sxs-lookup"><span data-stu-id="daffc-102">EApiCategories Enumeration</span></span>
<span data-ttu-id="daffc-103">Descreve as categorias de recursos que o host pode bloquear a execução de código parcialmente confiável.</span><span class="sxs-lookup"><span data-stu-id="daffc-103">Describes the categories of capabilities that the host can block from running in partially trusted code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="daffc-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="daffc-104">Syntax</span></span>  
  
```  
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
  
## <a name="members"></a><span data-ttu-id="daffc-105">Membros</span><span class="sxs-lookup"><span data-stu-id="daffc-105">Members</span></span>  
  
|<span data-ttu-id="daffc-106">Membro</span><span class="sxs-lookup"><span data-stu-id="daffc-106">Member</span></span>|<span data-ttu-id="daffc-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="daffc-107">Description</span></span>|  
|------------|-----------------|  
|`eAll`|<span data-ttu-id="daffc-108">Especifica que todos os gerenciados classes e membros que são cobertos por outros `EApiCategories` campos bloquear a execução de código parcialmente confiável.</span><span class="sxs-lookup"><span data-stu-id="daffc-108">Specifies that all managed classes and members that are covered by other `EApiCategories` fields be blocked from running in partially trusted code.</span></span>|  
|`eExternalProcessMgmt`|<span data-ttu-id="daffc-109">Especifica que classes gerenciadas e membros que permitem a criação, manipulação e destruição de processos externos bloquear a execução de código parcialmente confiável.</span><span class="sxs-lookup"><span data-stu-id="daffc-109">Specifies that managed classes and members that allow the creation, manipulation, and destruction of external processes be blocked from running in partially trusted code.</span></span>|  
|`eExternalThreading`|<span data-ttu-id="daffc-110">Especifica que classes gerenciadas e membros que permitem a criação, manipulação e destruição de segmentos externos bloquear a execução de código parcialmente confiável.</span><span class="sxs-lookup"><span data-stu-id="daffc-110">Specifies that managed classes and members that allow the creation, manipulation, and destruction of external threads be blocked from running in partially trusted code.</span></span>|  
|`eMayLeakOnAbort`|<span data-ttu-id="daffc-111">Especifica que tipos gerenciados e membros que potencialmente podem causar o vazamento de memória em Anular bloquear a execução de código parcialmente confiável.</span><span class="sxs-lookup"><span data-stu-id="daffc-111">Specifies that managed types and members that could potentially leak memory on abort be blocked from running in partially trusted code.</span></span>|  
|`eNoCategory`|<span data-ttu-id="daffc-112">Especifica que nenhuma categoria de código gerenciado bloquear a execução de código parcialmente confiável.</span><span class="sxs-lookup"><span data-stu-id="daffc-112">Specifies that no managed code categories be blocked from running in partially trusted code.</span></span>|  
|`eSecurityInfrastructure`|<span data-ttu-id="daffc-113">Especifica que a infraestrutura de segurança do common language runtime (CLR) impedido de ser usado por código parcialmente confiável.</span><span class="sxs-lookup"><span data-stu-id="daffc-113">Specifies that the common language runtime (CLR) security infrastructure be blocked from being used by partially trusted code.</span></span>|  
|`eSelfAffectingProcessMgmt`|<span data-ttu-id="daffc-114">Especifica que classes gerenciadas e membros cujos recursos podem afetar o processo hospedado bloquear a execução de código parcialmente confiável.</span><span class="sxs-lookup"><span data-stu-id="daffc-114">Specifies that managed classes and members whose capabilities can affect the hosted process be blocked from running in partially trusted code.</span></span>|  
|`eSelfAffectingThreading`|<span data-ttu-id="daffc-115">Especifica que classes gerenciadas e membros cujos recursos podem afetar os threads do processo hospedado bloquear a execução de código parcialmente confiável.</span><span class="sxs-lookup"><span data-stu-id="daffc-115">Specifies that managed classes and members whose capabilities can affect threads in the hosted process be blocked from running in partially trusted code.</span></span>|  
|`eSharedState`|<span data-ttu-id="daffc-116">Especifica que classes gerenciadas e membros que expõem o estado compartilhado bloquear a execução de código parcialmente confiável.</span><span class="sxs-lookup"><span data-stu-id="daffc-116">Specifies that managed classes and members that expose shared state be blocked from running in partially trusted code.</span></span>|  
|`eSynchronization`|<span data-ttu-id="daffc-117">Especifica que classes de tempo de execução de linguagem e membros que permitem que o código do usuário manter bloqueios comuns bloquear a execução de código parcialmente confiável.</span><span class="sxs-lookup"><span data-stu-id="daffc-117">Specifies that common language runtime classes and members that allow user code to hold locks be blocked from running in partially trusted code.</span></span>|  
|`eUI`|<span data-ttu-id="daffc-118">Especifica que classes gerenciadas e membros que permitem ou exigem interação humana bloquear a execução de código parcialmente confiável.</span><span class="sxs-lookup"><span data-stu-id="daffc-118">Specifies that managed classes and members that allow or require human interaction be blocked from running in partially trusted code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="daffc-119">Comentários</span><span class="sxs-lookup"><span data-stu-id="daffc-119">Remarks</span></span>  
 <span data-ttu-id="daffc-120">O [Iclrhostprotectionmanager](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-setprotectedcategories-method.md) método usa um parâmetro do tipo `EApiCategories`.</span><span class="sxs-lookup"><span data-stu-id="daffc-120">The [ICLRHostProtectionManager::SetProtectedCategories](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-setprotectedcategories-method.md) method takes a parameter of type `EApiCategories`.</span></span>  
  
 <span data-ttu-id="daffc-121">O `EApiCategories` enumeração e `SetProtectedCategories` método estão diretamente relacionadas ao gerenciado <xref:System.Security.Permissions.HostProtectionAttribute?displayProperty=nameWithType> classe.</span><span class="sxs-lookup"><span data-stu-id="daffc-121">The `EApiCategories` enumeration and the `SetProtectedCategories` method are directly related to the managed <xref:System.Security.Permissions.HostProtectionAttribute?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="daffc-122">A classe gerenciada é usada com o <xref:System.Security.Permissions.HostProtectionResource?displayProperty=nameWithType> enumeração, cujos valores correspondem diretamente para o `EApiCategories` valores, para marcar tipos gerenciados e membros que expõem os recursos correspondentes às categorias descritas pelo `EApiCategories`.</span><span class="sxs-lookup"><span data-stu-id="daffc-122">The managed class is used with the <xref:System.Security.Permissions.HostProtectionResource?displayProperty=nameWithType> enumeration, whose values correspond directly to the `EApiCategories` values, to mark managed types and members that expose capabilities corresponding to the categories described by `EApiCategories`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="daffc-123">Requisitos</span><span class="sxs-lookup"><span data-stu-id="daffc-123">Requirements</span></span>  
 <span data-ttu-id="daffc-124">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="daffc-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="daffc-125">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="daffc-125">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="daffc-126">**Biblioteca:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="daffc-126">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="daffc-127">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="daffc-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="daffc-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="daffc-128">See Also</span></span>  
 [<span data-ttu-id="daffc-129">Interface ICLRHostProtectionManager</span><span class="sxs-lookup"><span data-stu-id="daffc-129">ICLRHostProtectionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)  
 [<span data-ttu-id="daffc-130">Enumerações de hospedagem</span><span class="sxs-lookup"><span data-stu-id="daffc-130">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
