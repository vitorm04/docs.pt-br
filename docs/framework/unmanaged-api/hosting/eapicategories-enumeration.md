---
title: "Enumeração EApiCategories"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: EApiCategories
api_location: mscoree.dll
api_type: COM
f1_keywords: EApiCategories
helpviewer_keywords: EApiCategories enumeration [.NET Framework hosting]
ms.assetid: 3c4a8a5a-8a46-4ac9-947f-4959bc9d6ac6
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: eaff0133020fe84e58f8a130bffc8ddc2a55a19d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="eapicategories-enumeration"></a><span data-ttu-id="8ef18-102">Enumeração EApiCategories</span><span class="sxs-lookup"><span data-stu-id="8ef18-102">EApiCategories Enumeration</span></span>
<span data-ttu-id="8ef18-103">Descreve as categorias de recursos que o host pode bloquear a execução de código parcialmente confiável.</span><span class="sxs-lookup"><span data-stu-id="8ef18-103">Describes the categories of capabilities that the host can block from running in partially trusted code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ef18-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8ef18-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="8ef18-105">Membros</span><span class="sxs-lookup"><span data-stu-id="8ef18-105">Members</span></span>  
  
|<span data-ttu-id="8ef18-106">Membro</span><span class="sxs-lookup"><span data-stu-id="8ef18-106">Member</span></span>|<span data-ttu-id="8ef18-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="8ef18-107">Description</span></span>|  
|------------|-----------------|  
|`eAll`|<span data-ttu-id="8ef18-108">Especifica que todos os gerenciados classes e membros que são cobertos por outros `EApiCategories` campos bloquear a execução de código parcialmente confiável.</span><span class="sxs-lookup"><span data-stu-id="8ef18-108">Specifies that all managed classes and members that are covered by other `EApiCategories` fields be blocked from running in partially trusted code.</span></span>|  
|`eExternalProcessMgmt`|<span data-ttu-id="8ef18-109">Especifica que classes gerenciadas e membros que permitem a criação, manipulação e destruição de processos externos bloquear a execução de código parcialmente confiável.</span><span class="sxs-lookup"><span data-stu-id="8ef18-109">Specifies that managed classes and members that allow the creation, manipulation, and destruction of external processes be blocked from running in partially trusted code.</span></span>|  
|`eExternalThreading`|<span data-ttu-id="8ef18-110">Especifica que classes gerenciadas e membros que permitem a criação, manipulação e destruição de segmentos externos bloquear a execução de código parcialmente confiável.</span><span class="sxs-lookup"><span data-stu-id="8ef18-110">Specifies that managed classes and members that allow the creation, manipulation, and destruction of external threads be blocked from running in partially trusted code.</span></span>|  
|`eMayLeakOnAbort`|<span data-ttu-id="8ef18-111">Especifica que tipos gerenciados e membros que potencialmente podem causar o vazamento de memória em Anular bloquear a execução de código parcialmente confiável.</span><span class="sxs-lookup"><span data-stu-id="8ef18-111">Specifies that managed types and members that could potentially leak memory on abort be blocked from running in partially trusted code.</span></span>|  
|`eNoCategory`|<span data-ttu-id="8ef18-112">Especifica que nenhuma categoria de código gerenciado bloquear a execução de código parcialmente confiável.</span><span class="sxs-lookup"><span data-stu-id="8ef18-112">Specifies that no managed code categories be blocked from running in partially trusted code.</span></span>|  
|`eSecurityInfrastructure`|<span data-ttu-id="8ef18-113">Especifica que a infraestrutura de segurança do common language runtime (CLR) impedido de ser usado por código parcialmente confiável.</span><span class="sxs-lookup"><span data-stu-id="8ef18-113">Specifies that the common language runtime (CLR) security infrastructure be blocked from being used by partially trusted code.</span></span>|  
|`eSelfAffectingProcessMgmt`|<span data-ttu-id="8ef18-114">Especifica que classes gerenciadas e membros cujos recursos podem afetar o processo hospedado bloquear a execução de código parcialmente confiável.</span><span class="sxs-lookup"><span data-stu-id="8ef18-114">Specifies that managed classes and members whose capabilities can affect the hosted process be blocked from running in partially trusted code.</span></span>|  
|`eSelfAffectingThreading`|<span data-ttu-id="8ef18-115">Especifica que classes gerenciadas e membros cujos recursos podem afetar os threads do processo hospedado bloquear a execução de código parcialmente confiável.</span><span class="sxs-lookup"><span data-stu-id="8ef18-115">Specifies that managed classes and members whose capabilities can affect threads in the hosted process be blocked from running in partially trusted code.</span></span>|  
|`eSharedState`|<span data-ttu-id="8ef18-116">Especifica que classes gerenciadas e membros que expõem o estado compartilhado bloquear a execução de código parcialmente confiável.</span><span class="sxs-lookup"><span data-stu-id="8ef18-116">Specifies that managed classes and members that expose shared state be blocked from running in partially trusted code.</span></span>|  
|`eSynchronization`|<span data-ttu-id="8ef18-117">Especifica que classes de tempo de execução de linguagem e membros que permitem que o código do usuário manter bloqueios comuns bloquear a execução de código parcialmente confiável.</span><span class="sxs-lookup"><span data-stu-id="8ef18-117">Specifies that common language runtime classes and members that allow user code to hold locks be blocked from running in partially trusted code.</span></span>|  
|`eUI`|<span data-ttu-id="8ef18-118">Especifica que classes gerenciadas e membros que permitem ou exigem interação humana bloquear a execução de código parcialmente confiável.</span><span class="sxs-lookup"><span data-stu-id="8ef18-118">Specifies that managed classes and members that allow or require human interaction be blocked from running in partially trusted code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8ef18-119">Comentários</span><span class="sxs-lookup"><span data-stu-id="8ef18-119">Remarks</span></span>  
 <span data-ttu-id="8ef18-120">O [Iclrhostprotectionmanager](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-setprotectedcategories-method.md) método usa um parâmetro do tipo `EApiCategories`.</span><span class="sxs-lookup"><span data-stu-id="8ef18-120">The [ICLRHostProtectionManager::SetProtectedCategories](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-setprotectedcategories-method.md) method takes a parameter of type `EApiCategories`.</span></span>  
  
 <span data-ttu-id="8ef18-121">O `EApiCategories` enumeração e `SetProtectedCategories` método estão diretamente relacionadas ao gerenciado <xref:System.Security.Permissions.HostProtectionAttribute?displayProperty=nameWithType> classe.</span><span class="sxs-lookup"><span data-stu-id="8ef18-121">The `EApiCategories` enumeration and the `SetProtectedCategories` method are directly related to the managed <xref:System.Security.Permissions.HostProtectionAttribute?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="8ef18-122">A classe gerenciada é usada com o <xref:System.Security.Permissions.HostProtectionResource?displayProperty=nameWithType> enumeração, cujos valores correspondem diretamente para o `EApiCategories` valores, para marcar tipos gerenciados e membros que expõem os recursos correspondentes às categorias descritas pelo `EApiCategories`.</span><span class="sxs-lookup"><span data-stu-id="8ef18-122">The managed class is used with the <xref:System.Security.Permissions.HostProtectionResource?displayProperty=nameWithType> enumeration, whose values correspond directly to the `EApiCategories` values, to mark managed types and members that expose capabilities corresponding to the categories described by `EApiCategories`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ef18-123">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8ef18-123">Requirements</span></span>  
 <span data-ttu-id="8ef18-124">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8ef18-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8ef18-125">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8ef18-125">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8ef18-126">**Biblioteca:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8ef18-126">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8ef18-127">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8ef18-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ef18-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8ef18-128">See Also</span></span>  
 [<span data-ttu-id="8ef18-129">Interface ICLRHostProtectionManager</span><span class="sxs-lookup"><span data-stu-id="8ef18-129">ICLRHostProtectionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)  
 [<span data-ttu-id="8ef18-130">Enumerações de hospedagem</span><span class="sxs-lookup"><span data-stu-id="8ef18-130">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
