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
ms.openlocfilehash: 3debd3f13d78841188dd8c900f51c0110e1d4c67
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61906367"
---
# <a name="eapicategories-enumeration"></a><span data-ttu-id="13c20-102">Enumeração EApiCategories</span><span class="sxs-lookup"><span data-stu-id="13c20-102">EApiCategories Enumeration</span></span>
<span data-ttu-id="13c20-103">Descreve as categorias de recursos que o host pode bloquear seja executado no código parcialmente confiável.</span><span class="sxs-lookup"><span data-stu-id="13c20-103">Describes the categories of capabilities that the host can block from running in partially trusted code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13c20-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="13c20-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="13c20-105">Membros</span><span class="sxs-lookup"><span data-stu-id="13c20-105">Members</span></span>  
  
|<span data-ttu-id="13c20-106">Membro</span><span class="sxs-lookup"><span data-stu-id="13c20-106">Member</span></span>|<span data-ttu-id="13c20-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="13c20-107">Description</span></span>|  
|------------|-----------------|  
|`eAll`|<span data-ttu-id="13c20-108">Especifica que todos os gerenciados classes e membros que são cobertos por outros `EApiCategories` campos impedido de ser executado em código parcialmente confiável.</span><span class="sxs-lookup"><span data-stu-id="13c20-108">Specifies that all managed classes and members that are covered by other `EApiCategories` fields be blocked from running in partially trusted code.</span></span>|  
|`eExternalProcessMgmt`|<span data-ttu-id="13c20-109">Especifica que classes gerenciadas e membros que permitem a criação, a manipulação e a destruição de processos externos impedido de ser executado em código parcialmente confiável.</span><span class="sxs-lookup"><span data-stu-id="13c20-109">Specifies that managed classes and members that allow the creation, manipulation, and destruction of external processes be blocked from running in partially trusted code.</span></span>|  
|`eExternalThreading`|<span data-ttu-id="13c20-110">Especifica que classes gerenciadas e membros que permitem a criação, a manipulação e a destruição de threads externos impedido de ser executado em código parcialmente confiável.</span><span class="sxs-lookup"><span data-stu-id="13c20-110">Specifies that managed classes and members that allow the creation, manipulation, and destruction of external threads be blocked from running in partially trusted code.</span></span>|  
|`eMayLeakOnAbort`|<span data-ttu-id="13c20-111">Especifica que tipos gerenciados e membros que poderia potencialmente vazar memória no abortar a execução bloqueada em código parcialmente confiável.</span><span class="sxs-lookup"><span data-stu-id="13c20-111">Specifies that managed types and members that could potentially leak memory on abort be blocked from running in partially trusted code.</span></span>|  
|`eNoCategory`|<span data-ttu-id="13c20-112">Especifica que nenhuma categoria de código gerenciado impedido de ser executado em código parcialmente confiável.</span><span class="sxs-lookup"><span data-stu-id="13c20-112">Specifies that no managed code categories be blocked from running in partially trusted code.</span></span>|  
|`eSecurityInfrastructure`|<span data-ttu-id="13c20-113">Especifica que a infraestrutura de segurança do common language runtime (CLR) ser impedido de que está sendo usado pelo código parcialmente confiável.</span><span class="sxs-lookup"><span data-stu-id="13c20-113">Specifies that the common language runtime (CLR) security infrastructure be blocked from being used by partially trusted code.</span></span>|  
|`eSelfAffectingProcessMgmt`|<span data-ttu-id="13c20-114">Especifica que classes gerenciadas e membros cujos recursos podem afetar o processo hospedado impedido de ser executado em código parcialmente confiável.</span><span class="sxs-lookup"><span data-stu-id="13c20-114">Specifies that managed classes and members whose capabilities can affect the hosted process be blocked from running in partially trusted code.</span></span>|  
|`eSelfAffectingThreading`|<span data-ttu-id="13c20-115">Especifica que classes gerenciadas e membros cujos recursos podem afetar os threads no processo hospedado impedido de ser executado em código parcialmente confiável.</span><span class="sxs-lookup"><span data-stu-id="13c20-115">Specifies that managed classes and members whose capabilities can affect threads in the hosted process be blocked from running in partially trusted code.</span></span>|  
|`eSharedState`|<span data-ttu-id="13c20-116">Especifica que classes gerenciadas e membros que expõem o estado compartilhado impedido de ser executado em código parcialmente confiável.</span><span class="sxs-lookup"><span data-stu-id="13c20-116">Specifies that managed classes and members that expose shared state be blocked from running in partially trusted code.</span></span>|  
|`eSynchronization`|<span data-ttu-id="13c20-117">Especifica que as classes de tempo de execução de linguagem e membros que permitem que o código do usuário manter bloqueios comuns impedido de ser executado em código parcialmente confiável.</span><span class="sxs-lookup"><span data-stu-id="13c20-117">Specifies that common language runtime classes and members that allow user code to hold locks be blocked from running in partially trusted code.</span></span>|  
|`eUI`|<span data-ttu-id="13c20-118">Especifica que classes gerenciadas e membros que permitem ou exigem interação humana impedido de ser executado em código parcialmente confiável.</span><span class="sxs-lookup"><span data-stu-id="13c20-118">Specifies that managed classes and members that allow or require human interaction be blocked from running in partially trusted code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="13c20-119">Comentários</span><span class="sxs-lookup"><span data-stu-id="13c20-119">Remarks</span></span>  
 <span data-ttu-id="13c20-120">O [iclrhostprotectionmanager:: Setprotectedcategories](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-setprotectedcategories-method.md) método utiliza um parâmetro de tipo `EApiCategories`.</span><span class="sxs-lookup"><span data-stu-id="13c20-120">The [ICLRHostProtectionManager::SetProtectedCategories](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-setprotectedcategories-method.md) method takes a parameter of type `EApiCategories`.</span></span>  
  
 <span data-ttu-id="13c20-121">O `EApiCategories` enumeração e a `SetProtectedCategories` método estão diretamente relacionados para o gerenciado <xref:System.Security.Permissions.HostProtectionAttribute?displayProperty=nameWithType> classe.</span><span class="sxs-lookup"><span data-stu-id="13c20-121">The `EApiCategories` enumeration and the `SetProtectedCategories` method are directly related to the managed <xref:System.Security.Permissions.HostProtectionAttribute?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="13c20-122">A classe gerenciada é usada com o <xref:System.Security.Permissions.HostProtectionResource?displayProperty=nameWithType> enumeração, cujos valores correspondem diretamente para o `EApiCategories` valores, para marcar tipos gerenciados e membros que expõem funcionalidades correspondentes às categorias descritas pelo `EApiCategories`.</span><span class="sxs-lookup"><span data-stu-id="13c20-122">The managed class is used with the <xref:System.Security.Permissions.HostProtectionResource?displayProperty=nameWithType> enumeration, whose values correspond directly to the `EApiCategories` values, to mark managed types and members that expose capabilities corresponding to the categories described by `EApiCategories`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="13c20-123">Requisitos</span><span class="sxs-lookup"><span data-stu-id="13c20-123">Requirements</span></span>  
 <span data-ttu-id="13c20-124">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="13c20-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="13c20-125">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="13c20-125">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="13c20-126">**Biblioteca:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="13c20-126">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="13c20-127">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="13c20-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13c20-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="13c20-128">See also</span></span>

- [<span data-ttu-id="13c20-129">Interface ICLRHostProtectionManager</span><span class="sxs-lookup"><span data-stu-id="13c20-129">ICLRHostProtectionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)
- [<span data-ttu-id="13c20-130">Enumerações de hospedagem</span><span class="sxs-lookup"><span data-stu-id="13c20-130">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
